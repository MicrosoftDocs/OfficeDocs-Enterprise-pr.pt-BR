---
title: Atribuir licenças a contas de usuários usando o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Como usar o Office 365 PowerShell para atribuir uma licença do Office 365 a usuários não licenciados.
ms.openlocfilehash: 9fbf81db3b942dab90ef214169f197a8fea3f7ed
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841678"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Atribuir licenças a contas de usuários usando o PowerShell do Office 365

Os usuários não podem usar os serviços do Office 365 até que a conta tenha sido atribuída a uma licença de um plano de licenciamento. Você pode usar o Office 365 PowerShell para atribuir licenças rapidamente a contas não licenciadas. 

>[!Note]
>As contas de usuário devem ser atribuídas a um local. Você pode fazer isso a partir das propriedades de uma conta de usuário no centro de administração do Microsoft 365 ou no PowerShell.
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Em seguida, liste os planos de licença para seu locatário com este comando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Em seguida, obtenha o nome de entrada da conta para a qual você deseja adicionar uma licença, também conhecido como o nome de usuário principal (UPN).

Em seguida, verifique se a conta de usuário tem um local de uso atribuído.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Se não houver nenhum local de uso atribuído, você poderá atribuir um com estes comandos:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Por fim, especifique o nome de entrada do usuário e o nome do plano de licença e execute esses comandos.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Execute o `Get-MsolAccountSku` comando para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano da sua organização. O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para obter mais informações sobre planos de licenciamento, licenças e serviços, consulte [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

>[!Note]
>O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome. Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.
>

Para localizar as contas não licenciadas em sua organização, execute este comando.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Você só pode atribuir licenças a contas de usuário que tenham a propriedade **UsageLocation** definida para um código de país 3166-1 do país de 2 Alpha válido. Por exemplo, US para os Estados Unidos e FR para a França. Alguns serviços do Office 365 não estão disponíveis em determinados países. Para obter mais informações, consulte [about License Restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Para localizar contas que não tenham um valor **UsageLocation** , execute este comando.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Para definir o valor **UsageLocation** em uma conta, execute este comando.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Por exemplo:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro **-All**, somente as primeiras 500 contas serão retornadas.

### <a name="assigning-licenses-to-user-accounts"></a>Atribuir licenças a contas de usuário
    
Para atribuir uma licença a um usuário, use o seguinte comando no Office 365 PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Este exemplo atribui uma licença do plano de licenciamento do **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ao usuário não licenciado **\@Pomaria litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Para atribuir uma licença a todos os usuários não licenciados, execute este comando.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Você não pode atribuir várias licenças a um usuário do mesmo plano de licenciamento. Se você não tiver licenças o suficiente disponíveis, as licenças serão atribuídas aos usuários na ordem em que eles forem retornados pelo cmdlet **Get-MsolUser** até que as licenças disponíveis esgotem.
>

Este exemplo atribui licenças do plano de licenciamento do **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a todos os usuários não licenciados:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Este exemplo atribui as mesmas licenças a usuários não licenciados no departamento de vendas nos Estados Unidos:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Mover um usuário para uma assinatura diferente (plano de licença) com o módulo PowerShell do Azure Active Directory para Graph

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Em seguida, obtenha o nome de entrada da conta de usuário para a qual você deseja assinaturas de troca, também conhecido como nome de usuário principal (UPN).

Em seguida, liste as assinaturas (planos de licença) para o seu locatário com este comando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Em seguida, liste as assinaturas que a conta de usuário tem atualmente com esses comandos.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identifique a assinatura que o usuário tem atualmente (a assinatura de) e a assinatura à qual o usuário está se movendo (a assinatura para).

Por fim, especifique os nomes de assinatura para e de (números de peça SKU) e execute esses comandos.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Você pode verificar a alteração na assinatura da conta de usuário com esses comandos.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Confira também

[Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
