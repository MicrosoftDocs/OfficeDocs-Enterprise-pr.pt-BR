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
ms.openlocfilehash: 53668a69d72cdcbe912d550be2b9e571b7f6c0e0
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747470"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="e180a-103">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e180a-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="e180a-104">No Office 365, as licenças de planos de licenciamento (também chamados de SKUs ou planos do Office 365) dão aos usuários acesso aos serviços do Office 365 definidos para esses planos.</span><span class="sxs-lookup"><span data-stu-id="e180a-104">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="e180a-105">No entanto, um usuário pode não ter acesso a todos os serviços disponíveis em uma licença que está atribuída atualmente a ele.</span><span class="sxs-lookup"><span data-stu-id="e180a-105">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="e180a-106">Você pode usar o Office 365 PowerShell para exibir o status dos serviços em contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="e180a-106">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="e180a-107">Para obter mais informações sobre planos de licenciamento, licença e serviços, consulte [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e180a-107">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e180a-108">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="e180a-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e180a-109">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e180a-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="e180a-110">Em seguida, liste os planos de licença para seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="e180a-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="e180a-111">Use estes comandos para listar os serviços disponíveis em cada plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="e180a-111">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="e180a-112">Use estes comandos para listar as licenças atribuídas a uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="e180a-112">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e180a-113">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e180a-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e180a-114">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e180a-114">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="e180a-115">Em seguida, execute este comando para listar os planos de licenciamento que estão disponíveis em sua organização.</span><span class="sxs-lookup"><span data-stu-id="e180a-115">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```

<span data-ttu-id="e180a-116">Em seguida, execute este comando para listar os serviços que estão disponíveis em cada plano de licenciamento e a ordem em que eles estão listados (o número de índice).</span><span class="sxs-lookup"><span data-stu-id="e180a-116">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
```
  
<span data-ttu-id="e180a-117">Use este comando para listar as licenças atribuídas a um usuário e a ordem em que elas estão listadas (o número de índice).</span><span class="sxs-lookup"><span data-stu-id="e180a-117">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

>[!Note]
><span data-ttu-id="e180a-118">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="e180a-118">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="e180a-119">Para exibir os serviços de uma conta de usuário</span><span class="sxs-lookup"><span data-stu-id="e180a-119">To view services for a user account</span></span>

<span data-ttu-id="e180a-120">Para exibir todos os serviços do Office 365 aos quais um usuário tem acesso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e180a-120">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="e180a-121">Este exemplo mostra os serviços aos quais o usuário BelindaN@litwareinc.com tem acesso.</span><span class="sxs-lookup"><span data-stu-id="e180a-121">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="e180a-122">Isso mostra os serviços associados a todas as licenças atribuídas à conta dela.</span><span class="sxs-lookup"><span data-stu-id="e180a-122">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="e180a-123">Este exemplo mostra os serviços aos quais a usuária BrendaF@litwareinc.com tem acesso a partir da primeira licença atribuída à conta dela (o número de índice é 0).</span><span class="sxs-lookup"><span data-stu-id="e180a-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="e180a-124">Para exibir todos os serviços de um usuário que tenha *várias licenças*atribuídas, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e180a-124">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
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

  
## <a name="new-to-office-365"></a><span data-ttu-id="e180a-125">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="e180a-125">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="e180a-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="e180a-126">See also</span></span>

[<span data-ttu-id="e180a-127">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e180a-127">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e180a-128">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e180a-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e180a-129">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e180a-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
