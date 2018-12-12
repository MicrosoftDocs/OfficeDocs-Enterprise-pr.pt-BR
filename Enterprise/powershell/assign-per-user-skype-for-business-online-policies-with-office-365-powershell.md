---
title: Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Resumo: Usar o PowerShell do Office 365 para atribuir configurações de comunicação com Skype para políticas de negócios Online de por usuário.'
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
ms.locfileid: "17114802"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para atribuir por usuário configurações de comunicação com Skype para políticas de negócios Online.
  
Usar o Office 365 PowerShell é uma maneira eficiente para atribuir configurações de comunicação com Skype para políticas de negócios Online de por usuário.
  
## <a name="before-you-begin"></a>Antes de começar

Use essas instruções para obter configurado para executar os comandos (ignore as etapas que você já tenha concluído):
  
1. Baixe e instale o [Skype para módulo Business Connector Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366).
    
2. Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos: 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
Quando solicitado, insira seu Skype para Business Online nome da conta de administrador e senha.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Atualizar as configurações de comunicação externa para uma conta de usuário

Suponha que você deseja alterar as configurações de comunicação externa em uma conta de usuário. Por exemplo, você deseja permitir Alex para se comunicar com usuários federados (EnableFederationAccess é igual a True), mas não com usuários do Windows Live (EnablePublicCloudAccess for igual a False). Para fazer isso, você precisa fazer duas coisas:
  
1. Localizar uma política de acesso externo que atenda aos nossos critérios.
    
2. Atribuir essa política de acesso externo a Antônio.
    
> [!NOTE]
>  Não é possível criar uma política personalizada para todos os nossos próprios. Isso acontece porque o Skype para Business Online não permite que você crie diretivas personalizadas. Em vez disso, você deve atribuir uma das políticas que foram criadas especificamente para o Office 365. Aqueles criados anteriormente políticas incluem: 4 políticas de cliente diferente, 224 políticas de conferência diferentes, 5 planos de discagem diferentes, 5 políticas de acesso externo diferentes, política de correio de voz hospedada 1 e 4 políticas de voz diferentes.
  
Então, como determinar qual política de acesso externo para atribuir a Antônio? O comando a seguir retorna todas as políticas de acesso externo em que EnableFederationAccess for definido como True e EnablePublicCloudAccess for definida como False:
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

O que significa o comando é retornar todas as políticas que atenderem a dois critérios: a propriedade EnableFederationAccess for definida como True e a política EnablePublicCloudAccess for definida como False. Por sua vez, esse comando retorna uma política que atenda aos nossos critérios (FederationOnly). Aqui está um exemplo:
  
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
> A identidade da política diz Tag: FederationOnly. Na verdade, a marca: prefixo é uma consequência do trabalho de pré-lançamento antecipado feito no Microsoft Lync 2013. Quando se trata de atribuir políticas aos usuários, você deve excluir a marca: prefix e use apenas o nome de política: FederationOnly. 
  
Agora que você sabe quais políticas atribuir a Antônio, podemos atribuir essa política usando o cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) . Aqui está um exemplo:
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Atribuindo uma política é muito simple: basta especificar a identidade do usuário e o nome da política a ser atribuído. 
  
E quando se trata de políticas e atribuições de políticas, você não está limitado a trabalhar com uma conta de usuário uma vez. Por exemplo, suponha que você precisa de uma lista de todos os usuários que têm permissão para se comunicar com parceiros federados e usuários do Windows Live. Já sabemos que esses usuários tiverem sido atribuídos a política de acesso de usuário externo FederationAndPICDefault. Porque sabemos que, você pode exibir uma lista de todos os usuários executando um comando simple. Aqui está o comando:
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Em outras palavras, nos mostrará todos os usuários cuja propriedade ExternalAccessPolicy é definida para FederationAndPICDefault. (E, para limitar a quantidade de informações que aparece na tela, use o cmdlet Select-Object para exibir nos mostrará apenas o nome de exibição de cada usuário.) 
  
Para configurar todas as nossas contas de usuário para usar a mesma política, use este comando:
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Esse comando usa Get-CsOnlineUser para retornar uma coleção de todos os usuários que tiverem sido habilitados para o Lync e, em seguida, envia todas essas informações para Grant-CsExternalAccessPolicy, que atribuirá a política de FederationAndPICDefault para cada usuário na coleção.
  
Como um exemplo adicional, suponha que você atribuiu Alex anteriormente a política FederationAndPICDefault e agora você mudou de ideia e gostaria que ele seja gerenciado pela política de acesso externo global. Você não pode atribuir explicitamente a política global para qualquer pessoa. Ele é usado apenas se nenhuma outra diretiva por usuário é atribuída. Portanto, se quisermos Alex a ser gerenciado pela política global, você precisará *retirar a atribuição de* qualquer política por usuário previamente atribuída a ele. Aqui está um exemplo de comando:
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Esse comando define o nome da política de acesso externo atribuída à Alex para um nulo ($ $Null). NULL significa "nothing". Em outras palavras, nenhuma política de acesso externo é atribuída a Antônio. Quando nenhuma política de acesso externo é atribuída a um usuário, o que o usuário, obtém gerenciado pela diretiva global.
  
Para desabilitar uma conta de usuário usando o Windows PowerShell, use os cmdlets do Windows Azure Active Directory para remover Skype de Alex licença Business Online. Para obter mais informações, consulte [Desabilitar o acesso aos serviços do Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Veja também

#### 

[Gerenciar o Skype for Business Online com o Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

