---
title: Atribuir licenças a contas de usuários usando o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/26/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Como usar o Office 365 PowerShell para atribuir uma licença do Office 365 a usuários não licenciados.
ms.openlocfilehash: e963b9a0f24ae5b573dfe9612d9d09419809defe
ms.sourcegitcommit: 6b4fca7ccdbb7aeadc705d82f1007ac285f27357
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "37282926"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="ed14c-103">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="ed14c-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="ed14c-104">**Resumo:**  Como usar o Office 365 PowerShell para atribuir uma licença do Office 365 a usuários não licenciados.</span><span class="sxs-lookup"><span data-stu-id="ed14c-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="ed14c-105">Os usuários não podem usar os serviços do Office 365 até que a conta tenha sido atribuída a uma licença de um plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="ed14c-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="ed14c-106">Você pode usar o Office 365 PowerShell para atribuir licenças rapidamente a contas não licenciadas.</span><span class="sxs-lookup"><span data-stu-id="ed14c-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="ed14c-107">As contas de usuário devem ser atribuídas a um local.</span><span class="sxs-lookup"><span data-stu-id="ed14c-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="ed14c-108">Você pode fazer isso a partir das propriedades de uma conta de usuário no centro de administração do Microsoft 365 ou no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed14c-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ed14c-109">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="ed14c-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ed14c-110">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ed14c-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="ed14c-111">Em seguida, liste os planos de licença para seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="ed14c-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="ed14c-112">Em seguida, obtenha o nome de entrada da conta para a qual você deseja adicionar uma licença, também conhecido como o nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="ed14c-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="ed14c-113">Em seguida, verifique se a conta de usuário tem um local de uso atribuído.</span><span class="sxs-lookup"><span data-stu-id="ed14c-113">Next, ensure that the user account has a usage location assigned.</span></span>

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="ed14c-114">Se não houver nenhum local de uso atribuído, você poderá atribuir um com estes comandos:</span><span class="sxs-lookup"><span data-stu-id="ed14c-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="ed14c-115">Por fim, especifique o nome de entrada do usuário e o nome do plano de licença e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="ed14c-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ed14c-116">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed14c-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ed14c-117">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ed14c-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="ed14c-118">Execute o comando **Get-MsolAccountSku** para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano da sua organização.</span><span class="sxs-lookup"><span data-stu-id="ed14c-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="ed14c-119">O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="ed14c-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="ed14c-120">Para obter mais informações sobre planos de licenciamento, licenças e serviços, consulte [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ed14c-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="ed14c-121">Para localizar as contas não licenciadas em sua organização, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="ed14c-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="ed14c-122">Você só pode atribuir licenças a contas de usuário que tenham a propriedade **UsageLocation** definida para um código de país 3166-1 do país de 2 Alpha válido.</span><span class="sxs-lookup"><span data-stu-id="ed14c-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="ed14c-123">Por exemplo, US para os Estados Unidos e FR para a França.</span><span class="sxs-lookup"><span data-stu-id="ed14c-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="ed14c-124">Alguns serviços do Office 365 não estão disponíveis em determinados países.</span><span class="sxs-lookup"><span data-stu-id="ed14c-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="ed14c-125">Para obter mais informações, consulte [about License Restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="ed14c-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="ed14c-126">Para localizar contas que não tenham um valor **UsageLocation** , execute este comando.</span><span class="sxs-lookup"><span data-stu-id="ed14c-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="ed14c-127">Para definir o valor **UsageLocation** em uma conta, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="ed14c-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="ed14c-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ed14c-128">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="ed14c-129">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro **-All**, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="ed14c-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="ed14c-130">Atribuir licenças a contas de usuário</span><span class="sxs-lookup"><span data-stu-id="ed14c-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="ed14c-131">Para atribuir uma licença a um usuário, use o seguinte comando no Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed14c-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="ed14c-132">Este exemplo atribui uma licença do plano de licenciamento do **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ao usuário não licenciado **\@Pomaria litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="ed14c-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ed14c-133">Para atribuir uma licença a vários usuários não licenciados, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="ed14c-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="ed14c-134">Você não pode atribuir várias licenças a um usuário do mesmo plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="ed14c-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="ed14c-135">Se você não tiver licenças o suficiente disponíveis, as licenças serão atribuídas aos usuários na ordem em que eles forem retornados pelo cmdlet **Get-MsolUser** até que as licenças disponíveis esgotem.</span><span class="sxs-lookup"><span data-stu-id="ed14c-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="ed14c-136">Este exemplo atribui licenças do plano de licenciamento do **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a todos os usuários não licenciados:</span><span class="sxs-lookup"><span data-stu-id="ed14c-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ed14c-137">Este exemplo atribui as mesmas licenças a usuários não licenciados no departamento de vendas nos Estados Unidos:</span><span class="sxs-lookup"><span data-stu-id="ed14c-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ed14c-138">Mover um usuário para uma assinatura diferente (plano de licença) com o módulo PowerShell do Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="ed14c-138">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ed14c-139">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ed14c-139">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="ed14c-140">Em seguida, obtenha o nome de entrada da conta de usuário para a qual você deseja assinaturas de troca, também conhecido como nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="ed14c-140">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="ed14c-141">Em seguida, liste as assinaturas (planos de licença) para o seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="ed14c-141">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="ed14c-142">Em seguida, liste as assinaturas que a conta de usuário tem atualmente com esses comandos.</span><span class="sxs-lookup"><span data-stu-id="ed14c-142">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="ed14c-143">Identifique a assinatura que o usuário tem atualmente (a assinatura de) e a assinatura à qual o usuário está se movendo (a assinatura para).</span><span class="sxs-lookup"><span data-stu-id="ed14c-143">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="ed14c-144">Por fim, especifique os nomes de assinatura para e de (números de peça SKU) e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="ed14c-144">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```
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

<span data-ttu-id="ed14c-145">Você pode verificar a alteração na assinatura da conta de usuário com esses comandos.</span><span class="sxs-lookup"><span data-stu-id="ed14c-145">You can verify the change in subscription for the user account with these commands.</span></span>

```
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="new-to-office-365"></a><span data-ttu-id="ed14c-146">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="ed14c-146">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="ed14c-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="ed14c-147">See also</span></span>

[<span data-ttu-id="ed14c-148">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed14c-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ed14c-149">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed14c-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ed14c-150">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed14c-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
