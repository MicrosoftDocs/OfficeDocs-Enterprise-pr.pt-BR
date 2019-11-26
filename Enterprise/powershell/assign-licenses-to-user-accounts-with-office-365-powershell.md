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
ms.openlocfilehash: 8db03eb919547fd0664f8e71cf5f8eddd0f41e2e
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257450"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="fd81e-103">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="fd81e-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="fd81e-104">**Resumo:**  Como usar o Office 365 PowerShell para atribuir uma licença do Office 365 a usuários não licenciados.</span><span class="sxs-lookup"><span data-stu-id="fd81e-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="fd81e-105">Os usuários não podem usar os serviços do Office 365 até que a conta tenha sido atribuída a uma licença de um plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="fd81e-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="fd81e-106">Você pode usar o Office 365 PowerShell para atribuir licenças rapidamente a contas não licenciadas.</span><span class="sxs-lookup"><span data-stu-id="fd81e-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="fd81e-107">As contas de usuário devem ser atribuídas a um local.</span><span class="sxs-lookup"><span data-stu-id="fd81e-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="fd81e-108">Você pode fazer isso a partir das propriedades de uma conta de usuário no centro de administração do Microsoft 365 ou no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd81e-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fd81e-109">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="fd81e-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="fd81e-110">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="fd81e-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="fd81e-111">Em seguida, liste os planos de licença para seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="fd81e-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="fd81e-112">Em seguida, obtenha o nome de entrada da conta para a qual você deseja adicionar uma licença, também conhecido como o nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="fd81e-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="fd81e-113">Em seguida, verifique se a conta de usuário tem um local de uso atribuído.</span><span class="sxs-lookup"><span data-stu-id="fd81e-113">Next, ensure that the user account has a usage location assigned.</span></span>

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="fd81e-114">Se não houver nenhum local de uso atribuído, você poderá atribuir um com estes comandos:</span><span class="sxs-lookup"><span data-stu-id="fd81e-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="fd81e-115">Por fim, especifique o nome de entrada do usuário e o nome do plano de licença e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="fd81e-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fd81e-116">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd81e-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fd81e-117">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="fd81e-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="fd81e-118">Execute o comando **Get-MsolAccountSku** para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano da sua organização.</span><span class="sxs-lookup"><span data-stu-id="fd81e-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="fd81e-119">O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="fd81e-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="fd81e-120">Para obter mais informações sobre planos de licenciamento, licenças e serviços, consulte [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fd81e-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

>[!Note]
><span data-ttu-id="fd81e-121">O PowerShell Core não é compatível com o módulo Microsoft Azure Active Directory para o módulo e cmdlets do Windows PowerShell com o **MSol** em seu nome.</span><span class="sxs-lookup"><span data-stu-id="fd81e-121">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="fd81e-122">Para continuar usando esses cmdlets, você deve executá-los do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd81e-122">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="fd81e-123">Para localizar as contas não licenciadas em sua organização, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="fd81e-123">To find the unlicensed accounts in your organization, run this command.</span></span>

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="fd81e-124">Você só pode atribuir licenças a contas de usuário que tenham a propriedade **UsageLocation** definida para um código de país 3166-1 do país de 2 Alpha válido.</span><span class="sxs-lookup"><span data-stu-id="fd81e-124">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="fd81e-125">Por exemplo, US para os Estados Unidos e FR para a França.</span><span class="sxs-lookup"><span data-stu-id="fd81e-125">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="fd81e-126">Alguns serviços do Office 365 não estão disponíveis em determinados países.</span><span class="sxs-lookup"><span data-stu-id="fd81e-126">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="fd81e-127">Para obter mais informações, consulte [about License Restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="fd81e-127">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="fd81e-128">Para localizar contas que não tenham um valor **UsageLocation** , execute este comando.</span><span class="sxs-lookup"><span data-stu-id="fd81e-128">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="fd81e-129">Para definir o valor **UsageLocation** em uma conta, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="fd81e-129">To set the **UsageLocation** value on an account, run this command.</span></span>

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="fd81e-130">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fd81e-130">For example:</span></span>

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="fd81e-131">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro **-All**, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="fd81e-131">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="fd81e-132">Atribuir licenças a contas de usuário</span><span class="sxs-lookup"><span data-stu-id="fd81e-132">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="fd81e-133">Para atribuir uma licença a um usuário, use o seguinte comando no Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd81e-133">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="fd81e-134">Este exemplo atribui uma licença do plano de licenciamento do **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ao usuário não licenciado **\@Pomaria litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="fd81e-134">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="fd81e-135">Para atribuir uma licença a vários usuários não licenciados, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="fd81e-135">To assign a license to many unlicensed users, run this command.</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="fd81e-136">Você não pode atribuir várias licenças a um usuário do mesmo plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="fd81e-136">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="fd81e-137">Se você não tiver licenças o suficiente disponíveis, as licenças serão atribuídas aos usuários na ordem em que eles forem retornados pelo cmdlet **Get-MsolUser** até que as licenças disponíveis esgotem.</span><span class="sxs-lookup"><span data-stu-id="fd81e-137">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="fd81e-138">Este exemplo atribui licenças do plano de licenciamento do **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a todos os usuários não licenciados:</span><span class="sxs-lookup"><span data-stu-id="fd81e-138">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="fd81e-139">Este exemplo atribui as mesmas licenças a usuários não licenciados no departamento de vendas nos Estados Unidos:</span><span class="sxs-lookup"><span data-stu-id="fd81e-139">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fd81e-140">Mover um usuário para uma assinatura diferente (plano de licença) com o módulo PowerShell do Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="fd81e-140">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="fd81e-141">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="fd81e-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="fd81e-142">Em seguida, obtenha o nome de entrada da conta de usuário para a qual você deseja assinaturas de troca, também conhecido como nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="fd81e-142">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="fd81e-143">Em seguida, liste as assinaturas (planos de licença) para o seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="fd81e-143">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="fd81e-144">Em seguida, liste as assinaturas que a conta de usuário tem atualmente com esses comandos.</span><span class="sxs-lookup"><span data-stu-id="fd81e-144">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="fd81e-145">Identifique a assinatura que o usuário tem atualmente (a assinatura de) e a assinatura à qual o usuário está se movendo (a assinatura para).</span><span class="sxs-lookup"><span data-stu-id="fd81e-145">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="fd81e-146">Por fim, especifique os nomes de assinatura para e de (números de peça SKU) e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="fd81e-146">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

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

<span data-ttu-id="fd81e-147">Você pode verificar a alteração na assinatura da conta de usuário com esses comandos.</span><span class="sxs-lookup"><span data-stu-id="fd81e-147">You can verify the change in subscription for the user account with these commands.</span></span>

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="new-to-office-365"></a><span data-ttu-id="fd81e-148">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="fd81e-148">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="fd81e-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd81e-149">See also</span></span>

[<span data-ttu-id="fd81e-150">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd81e-150">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="fd81e-151">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd81e-151">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fd81e-152">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd81e-152">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
