---
title: Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que foram atribuídos aos usuários.
ms.openlocfilehash: 608d26dfc4aa1be782f94aa3b1ba5f66a0378f1e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071117"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell

**Resumo:** Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que foram atribuídos aos usuários.
  
No Office 365, as licenças de planos de licenciamento (também chamados de SKUs ou planos do Office 365) dão aos usuários acesso aos serviços do Office 365 definidos para esses planos. No entanto, um usuário pode não ter acesso a todos os serviços disponíveis em uma licença que está atribuída atualmente a ele. Você pode usar o Office 365 PowerShell para exibir o status dos serviços em contas de usuário. 

Para obter mais informações sobre planos de licenciamento, licença e serviços, consulte [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Em seguida, liste os planos de licença para seu locatário com este comando.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Use estes comandos para listar os serviços disponíveis em cada plano de licenciamento.

```
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
````

Use estes comandos para listar as licenças atribuídas a uma conta de usuário.

````
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
````

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Em seguida, execute este comando para listar os planos de licenciamento que estão disponíveis em sua organização. 

```
Get-MsolAccountSku
```

Em seguida, execute este comando para listar os serviços que estão disponíveis em cada plano de licenciamento e a ordem em que eles estão listados (o número de índice).

````
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
````
  
Use este comando para listar as licenças atribuídas a um usuário e a ordem em que elas estão listadas (o número de índice).

````
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
````

>[!Note]
>Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.
>
   

### <a name="to-view-services-for-a-user-account"></a>Para exibir os serviços de uma conta de usuário

Para exibir todos os serviços do Office 365 aos quais um usuário tem acesso, use a seguinte sintaxe:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Este exemplo mostra os serviços aos quais o usuário BelindaN@litwareinc.com tem acesso. Isso mostra os serviços associados a todas as licenças atribuídas à conta dela.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Este exemplo mostra os serviços aos quais a usuária BrendaF@litwareinc.com tem acesso a partir da primeira licença atribuída à conta dela (o número de índice é 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Para exibir todos os serviços de um usuário que tenha *várias licenças*atribuídas, use a seguinte sintaxe:

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

  
## <a name="new-to-office-365"></a>Começando a usar o Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Confira também

[Gerenciar licenças e contas de usuário usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
