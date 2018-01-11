---
title: "Gerenciar Skype para políticas Business Online com o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "Resumo: Usar o PowerShell do Office 365 para gerenciar sua Skype para Business Online propriedades de conta de usuário com políticas."
ms.openlocfilehash: 6698bd43b2a55e1c98fbe8e536a46e2de604b4d2
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>Gerenciar Skype para políticas Business Online com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para gerenciar sua Skype para Business Online propriedades de conta de usuário com políticas.
  
Para gerenciar várias propriedades da conta de usuário para Skype para Business Online, você deve especificá-las como propriedades das políticas com o Office 365 PowerShell.
  
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
    
## <a name="manage-user-account-policies"></a>Gerenciar políticas de conta de usuário

Muitos Skype para Business Online propriedades da conta de usuário são definidas por meio de políticas. Políticas são simplesmente coleções de configurações que podem ser aplicadas a um ou mais usuários. Dê uma olhada em como a uma diretiva tiver sido configurada, você pode executar esse comando de exemplo para a política de FederationAndPICDefault:
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Por sua vez, você deve obter algo semelhante a esta:
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

Neste exemplo, os valores nessa diretiva determinam o que um uso pode ou não podem fazer quando se trata de se comunicar com usuários federados. Por exemplo, a propriedade EnableOutsideAccess deve ser definida como True para um usuário sejam capazes de se comunicar com pessoas fora da organização. Observe que essa propriedade não aparecem no Centro de administração do Office 365. Em vez disso, a propriedade é definida automaticamente como True ou False com base em outras seleções feitas. As duas outras propriedades de interesse são:
  
- **EnableFederationAccess** indica se o usuário pode se comunicar com pessoas de domínios federados.
    
- **EnablePublicCloudAccess** indica se o usuário pode se comunicar com usuários do Windows Live.
    
Portanto, você não alterar diretamente as propriedades relacionadas à Federação em contas de usuário (por exemplo, **Set-CsUser-EnableFederationAccess $True**). Em vez disso, você atribuir uma conta uma política de acesso externo que tem os valores de propriedade desejada pré-configurados. Se quisermos que um usuário seja capaz de se comunicar com usuários federados e usuários do Windows Live, essa conta de usuário deve ser atribuída a uma política que permite esses tipos de comunicação.
  
Se você deseja saber se ou não alguém pode se comunicar com usuários de fora da organização, você precisa:
  
- Determinar qual política de acesso externo foi atribuída a esse usuário.
    
- Determinar quais recursos são ou não permitidos por essa política.
    
Por exemplo, você pode fazer isso usando este comando:
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Esse comando localiza a política atribuída ao usuário, em seguida, localiza os recursos habilitados ou desabilitados dentro dessa política.
  
Observe que não há nenhuma cmdlets para criando ou modificando diretivas. Você deve usar as políticas previamente fornecidas pelo Office 365. Se você quiser dar uma olhada as políticas diferentes disponíveis, você pode usar estes comandos:
  
- Get-CsClientPolicy       
- Get-CsConferencingPolicy        
- Get-CsDialPlan            
- Get-CsExternalAccessPolicy                         
- Get-CsHostedVoicemailPolicy                        
- Get-CsPresencePolicy                               
- Get-CsVoicePolicy                                  

> [!NOTE]
> Um Skype para Business Online plano de discagem é uma diretiva em todos os aspectos, exceto o nome. O nome "plano de discagem" foi escolhido em vez, por exemplo, "diretiva de discagem" para fornecer compatibilidade com versões anteriores ao Office Communications Server e o Exchange. 
  
Por exemplo, para considerar todas as políticas de voz disponíveis para uso, execute este comando:
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> Isso retorna uma lista de todas as políticas de voz disponíveis para você. Tenha em mente, entretanto, que nem todas as políticas podem ser atribuídas a todos os usuários. Isso acontece devido à várias restrições envolvendo a localização geográfica e de licenciamento. (Os chamados "[local de uso](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") Se desejar saber as políticas de acesso externo e as diretivas de conferência que podem ser atribuídas a um usuário específico, use comandos semelhantes a estas: 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

O parâmetro ApplicableTo limita os dados retornados para políticas que podem ser atribuídas ao usuário especificado (por exemplo, Antônio Teixeira). Dependendo das restrições de licenciamento e local de uso, isso pode representar um subconjunto de todas as políticas disponíveis. 
  
Em alguns casos, propriedades das diretivas não são usadas com o Office 365, enquanto outros só podem ser gerenciados pela equipe de suporte da Microsoft. 
  
Com Skype para Business Online, os usuários devem ser gerenciados por uma política de algum tipo. Se uma propriedade válida de relacionada à política estiver vazia, isso significa que o usuário em questão está sendo gerenciado por uma política global, o que é uma política que será automaticamente aplicada a um usuário, a menos que ele ou ela especificamente atribuída uma política por usuário. Porque não vemos uma diretiva de cliente listada para uma conta de usuário, ele é gerenciado pela política global. Você pode determinar a diretiva de cliente global com este comando:
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Veja também

#### 

[Gerenciar o Skype for Business Online com o Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

