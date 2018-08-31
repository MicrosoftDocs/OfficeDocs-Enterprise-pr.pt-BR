---
title: Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários.
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223103"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell

**Resumo:** Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários.
  
No Office 365, licencia para planos de licenciamento (também chamado de SKUs ou do Office 365 estiver planejando) conceder aos usuários acesso aos serviços do Office 365 que são definidos para esses planos. No entanto, um usuário pode não ter acesso a todos os serviços que estão disponíveis em uma licença atualmente atribuído a eles. Você pode usar o PowerShell do Office 365 para exibir o status dos serviços em contas de usuário. 

## <a name="before-you-begin"></a>Antes de começar

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Use os comandos `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` para encontrar as seguintes informações:
    
  - Os planos de licenciamento que estão disponíveis na sua organização.
    
  - Os serviços que estão disponíveis em cada plano de licenciamento e a ordem em que eles estão listados (o número do índice).
    
     Para obter mais informações sobre o licenciamento planos, licenças e serviços, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Use o comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` para encontrar as licenças atribuídas a um usuário e a ordem na qual eles estão listados (o número de índice).
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.
    

## <a name="to-view-services-for-a-user-account"></a>Para exibir serviços para uma conta de usuário

Para exibir todos os serviços do Office 365 que um usuário tem acesso ao, use a seguinte sintaxe:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Este exemplo mostra os serviços aos quais o usuário BelindaN@litwareinc.com tem acesso. Mostra os serviços que estão associados a todas as licenças são atribuídas à sua conta.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Este exemplo mostra os serviços aos quais a usuária BrendaF@litwareinc.com tem acesso a partir da primeira licença atribuída à conta dela (o número de índice é 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Para localizar todos os usuários licenciados que foram habilitados ou não habilitados para serviços específicos, use a seguinte sintaxe:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

Esses exemplos utilizam as seguintes informações:
  
- A licença que fornece acesso aos serviços do Office 365 que estamos interessados em é a primeira licença atribuída a todos os usuários (o número de índice é 0).
    
- Os serviços do Office 365 que estamos interessados em são Skype para Business Online e o Exchange Online. As licenças que estão associados com o plano de licenciamento, Skype para Business Online é o serviço 6º listado (o número de índice é de 5), e o Exchange Online é o serviço de 9 listados (o número de índice é 8).
    
Este exemplo retorna todas licenciados usuários habilitados para o Skype para Business Online e o Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Este exemplo retorna todos os usuários licenciados que não estão habilitados para o Skype para Business Online ou Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Para exibir todos os serviços para um usuário que tenha sido atribuído a *várias licenças*, use a seguinte sintaxe:

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a>Veja também

Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Criar contas de usuários usando o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear contas de usuários com o Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Atribuir licenças a contas de usuários usando o Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Remover licenças de contas de usuários com o Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Começando a usar o Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]