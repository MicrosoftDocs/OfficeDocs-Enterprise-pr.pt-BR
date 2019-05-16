---
title: Atribuir licenças a contas de usuários usando o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
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
description: Explica como usar o Office 365 PowerShell atribuir uma licença do Office 365 a usuários não licenciados.
ms.openlocfilehash: 91fe9f3a14663ebb9adb61700de3004edd236e0c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069277"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="1fc99-103">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="1fc99-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="1fc99-104">**Resumo:**  Explica como usar o Office 365 PowerShell atribuir uma licença do Office 365 a usuários não licenciados.</span><span class="sxs-lookup"><span data-stu-id="1fc99-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="1fc99-105">Os usuários não podem usar os serviços do Office 365 até que a conta tenha sido atribuída a uma licença de um plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="1fc99-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="1fc99-106">Você pode usar o Office 365 PowerShell para atribuir licenças rapidamente a contas não licenciadas.</span><span class="sxs-lookup"><span data-stu-id="1fc99-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1fc99-107">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="1fc99-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1fc99-108">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="1fc99-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="1fc99-109">Em seguida, liste os planos de licença para seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="1fc99-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="1fc99-110">Em seguida, obtenha o nome de entrada da conta para a qual você deseja adicionar uma licença, também conhecido como o nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="1fc99-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="1fc99-111">Por fim, especifique o nome de entrada do usuário e o nome do plano de licença e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="1fc99-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1fc99-112">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fc99-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1fc99-113">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1fc99-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="1fc99-114">Execute o comando **Get-MsolAccountSku** para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano da sua organização.</span><span class="sxs-lookup"><span data-stu-id="1fc99-114">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="1fc99-115">O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="1fc99-115">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="1fc99-116">Para obter mais informações sobre planos de licenciamento, licenças e serviços, consulte [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1fc99-116">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="1fc99-117">Para localizar as contas não licenciadas em sua organização, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="1fc99-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="1fc99-118">Você só pode atribuir licenças a contas de usuário que tenham a propriedade **UsageLocation** definida para um código de país 3166-1 do país de 2 Alpha válido.</span><span class="sxs-lookup"><span data-stu-id="1fc99-118">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="1fc99-119">Por exemplo, US para os Estados Unidos e FR para a França.</span><span class="sxs-lookup"><span data-stu-id="1fc99-119">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="1fc99-120">Alguns serviços do Office 365 não estão disponíveis em determinados países.</span><span class="sxs-lookup"><span data-stu-id="1fc99-120">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="1fc99-121">Para obter mais informações, consulte [about License Restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="1fc99-121">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="1fc99-122">Para localizar contas que não tenham um valor **UsageLocation** , execute este comando.</span><span class="sxs-lookup"><span data-stu-id="1fc99-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="1fc99-123">Para definir o valor **UsageLocation** em uma conta, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="1fc99-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="1fc99-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1fc99-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="1fc99-125">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro **-All**, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="1fc99-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="1fc99-126">Atribuir licenças a contas de usuário</span><span class="sxs-lookup"><span data-stu-id="1fc99-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="1fc99-127">Para atribuir uma licença a um usuário, use o seguinte comando no Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fc99-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="1fc99-128">Este exemplo atribui uma licença do plano de licenciamento do **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ao usuário não licenciado **belindan@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="1fc99-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="1fc99-129">Para atribuir uma licença a vários usuários não licenciados, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="1fc99-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="1fc99-130">Você não pode atribuir várias licenças a um usuário do mesmo plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="1fc99-130">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="1fc99-131">Se você não tiver licenças o suficiente disponíveis, as licenças serão atribuídas aos usuários na ordem em que eles forem retornados pelo cmdlet **Get-MsolUser** até que as licenças disponíveis esgotem.</span><span class="sxs-lookup"><span data-stu-id="1fc99-131">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="1fc99-132">Este exemplo atribui licenças do plano de licenciamento do **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a todos os usuários não licenciados:</span><span class="sxs-lookup"><span data-stu-id="1fc99-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="1fc99-133">Este exemplo atribui as mesmas licenças a usuários não licenciados no departamento de vendas nos Estados Unidos:</span><span class="sxs-lookup"><span data-stu-id="1fc99-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="1fc99-134">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="1fc99-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="1fc99-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="1fc99-135">See also</span></span>

[<span data-ttu-id="1fc99-136">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fc99-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1fc99-137">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fc99-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1fc99-138">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fc99-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
