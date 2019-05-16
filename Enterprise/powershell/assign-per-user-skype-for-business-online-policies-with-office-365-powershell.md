---
title: Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Resumo: Use o Office 365 PowerShell para atribuir configurações de comunicação por usuário com as políticas do Skype for Business online.'
ms.openlocfilehash: 3c6c869874329d7efb6d8c417c797c9f81df6bf8
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069287"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para atribuir configurações de comunicação por usuário com as políticas do Skype for Business online.
  
O uso do Office 365 PowerShell é uma maneira eficiente de atribuir configurações de comunicação por usuário com as políticas do Skype for Business online.
  
## <a name="before-you-begin"></a>Antes de começar

Use estas instruções para configurar a execução dos comandos (pule as etapas que você já concluiu):
  
1. Baixe e instale o [módulo do conector do Skype for Business online](https://www.microsoft.com/en-us/download/details.aspx?id=39366).
    
2. Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos: 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
Quando solicitado, insira o nome da conta e a senha do administrador do Skype for Business online.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Atualizando configurações de comunicação externa para uma conta de usuário

Suponha que você queira alterar as configurações de comunicação externa em uma conta de usuário. Por exemplo, você deseja permitir que Alex se comunique com usuários federados (EnableFederationAccess é igual a true), mas não com usuários do Windows Live (EnablePublicCloudAccess é igual a false). Para fazer isso, você precisa fazer duas coisas:
  
1. Localizar uma política de acesso externo que atenda aos nossos critérios.
    
2. Atribuir essa política de acesso externo a Antônio.
    
> [!NOTE]
>  Você não pode criar uma política personalizada todos nossos. Isso ocorre porque o Skype for Business online não permite que você crie políticas personalizadas. Em vez disso, você deve atribuir uma das políticas que foram criadas especificamente para o Office 365. Essas políticas previamente criadas incluem: 4 diferentes políticas de cliente, 224 diferentes políticas de conferência, cinco planos de discagem diferentes, cinco políticas de acesso externo diferentes, 1 política de caixa postal hospedada e 4 políticas de voz diferentes.
  
Então, como determinar qual política de acesso externo atribuirá a Alex? O comando a seguir retorna todas as políticas de acesso externo em que EnableFederationAccess é definido como True e EnablePublicCloudAccess como False:
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

O que o comando faz é retornar todas as políticas que atendem a dois critérios: a propriedade EnableFederationAccess é definida como true e a política EnablePublicCloudAccess é definida como false. Por sua vez, esse comando retorna uma política que atende aos nossos critérios (FederationOnly). Veja um exemplo:
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> A identidade da política diz a marca: FederationOnly. Na verdade, o prefixo Tag: é um carryover de um trabalho pré-lançamento anterior do Microsoft Lync 2013. No que diz respeito à atribuição de políticas a usuários, você deve excluir o prefixo Tag: e usar apenas o nome da política: FederationOnly. 
  
Agora que você sabe qual política será atribuída a Alex, podemos atribuir essa política usando o cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) . Veja um exemplo:
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Atribuir uma política é muito simples: basta especificar a identidade do usuário e o nome da política a ser atribuída. 
  
E quando se trata de políticas e atribuições de política, você não está limitado a trabalhar com as contas de usuário uma vez. Por exemplo, suponha que você precise de uma lista de todos os usuários que têm permissão para se comunicar com parceiros federados e com usuários do Windows Live. Já sabemos que esses usuários foram atribuídos à política de acesso de usuário externo FederationAndPICDefault. Como sabemos que, você pode exibir uma lista de todos os usuários executando um comando simples. Este é o comando:
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Em outras palavras, isso nos mostra todos os usuários cuja propriedade ExternalAccessPolicy está definida como FederationAndPICDefault. (E, para limitar a quantidade de informações que aparece na tela, use o cmdlet Select-Object para exibir apenas mostrar o nome de exibição de cada usuário.) 
  
Para configurar todas as contas de usuário para usar essa mesma política, use este comando:
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Este comando usa Get-CsOnlineUser para retornar uma coleção de todos os usuários que tenham sido habilitados para o Lync e, em seguida, envia todas as informações para Grant-CsExternalAccessPolicy, que atribui a política de FederationAndPICDefault a cada e a todos os usuários da coleção.
  
Como um exemplo adicional, suponha que você tenha anteriormente atribuído a Alex a política FederationAndPICDefault e agora já alterou sua mente e gostaria que ele fosse gerenciado pela política de acesso externo global. Você não pode atribuir explicitamente a política global a qualquer pessoa. Ela só será usada se nenhuma política por usuário for atribuída. Portanto, se quisermos que Alex seja gerenciado pela política global, você precisará *cancelar a atribuição* de qualquer política por usuário atribuída anteriormente a ele. Este é um exemplo de comando:
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Este comando define o nome da política de acesso externo atribuída a Alex como um valor nulo ($Null). NULL significa "Nothing". Em outras palavras, nenhuma política de acesso externo é atribuída a Alex. Quando nenhuma política de acesso externo é atribuída a um usuário, esse usuário é gerenciado pela política global.
  
Para desabilitar uma conta de usuário usando o Windows PowerShell, use os cmdlets do Azure Active Directory para remover a licença do Skype for Business online de Alex. Para obter mais informações, consulte [desabilitar o acesso aos serviços com o Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Confira também

#### 

[Gerenciar o Skype for Business Online com o Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

