---
title: Atribuir licenças a contas de usuários usando o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
ms.audience: Admin
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
description: Explica como usar o Office 365 PowerShell para atribuir uma licença do Office 365 para usuários não licenciados.
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651175"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="59230-103">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="59230-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="59230-104">**Resumo:** explica como usar o Office 365 PowerShell para atribuir uma licença do Office 365 para usuários não licenciados.</span><span class="sxs-lookup"><span data-stu-id="59230-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="59230-p101">Usuários não podem usar qualquer serviços do Office 365, até que sua conta tenha sido atribuída uma licença de um plano de licenciamento. Você pode usar o Office 365 PowerShell rapidamente atribuir licenças às contas não licenciadas.</span><span class="sxs-lookup"><span data-stu-id="59230-p101">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan. You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="59230-107">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="59230-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="59230-108">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="59230-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="59230-109">Em seguida, liste os planos de licença para o seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="59230-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="59230-110">Em seguida, obtenha o nome de logon da conta para o qual você deseja adicionar uma licença, também conhecido como o usuário nome principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="59230-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="59230-111">Finalmente, especifique o nome de entrada do usuário e o nome do plano de licença e executar esses comandos.</span><span class="sxs-lookup"><span data-stu-id="59230-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="59230-112">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59230-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="59230-113">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="59230-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="59230-p102">Execute o comando **Get-MsolAccountSku** para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano em sua organização. O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para obter mais informações sobre o licenciamento planos, licenças e serviços, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="59230-p102">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="59230-117">Para localizar as contas não licenciadas em sua organização, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="59230-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="59230-p103">Você só pode atribuir licenças às contas de usuário que têm a propriedade **UsageLocation** definida como um código de país do 3166-1 alpha-2 ISO válido. Por exemplo, nos Estados Unidos e FR para França de tempo. Alguns serviços do Office 365 não estão disponíveis em determinados países. Para obter mais informações, consulte [sobre as restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="59230-p103">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="59230-122">Para localizar as contas que não têm um valor de **UsageLocation** , execute este comando.</span><span class="sxs-lookup"><span data-stu-id="59230-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="59230-123">Para definir o valor de **UsageLocation** em uma conta, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="59230-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="59230-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="59230-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="59230-125">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro **-All**, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="59230-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="59230-126">Atribuir licenças às contas de usuário</span><span class="sxs-lookup"><span data-stu-id="59230-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="59230-127">Para atribuir uma licença a um usuário, use o seguinte comando no Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59230-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="59230-128">Este exemplo atribui uma licença a partir do **litwareinc: enterprisepack** (Office 365 Enterprise E3) plano para o usuário não licenciado **belindan@litwareinc.com**de licenciamento:</span><span class="sxs-lookup"><span data-stu-id="59230-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="59230-129">Para atribuir uma licença a muitos usuários não licenciados, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="59230-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="59230-p104">Você não pode atribuir várias licenças a um usuário do plano de licenciamento do mesmo. Se você não possui licenças suficientes disponíveis, as licenças são atribuídas a usuários na ordem em que estiver retornadas pelo cmdlet **Get-MsolUser** até que as licenças disponíveis se esgotar.</span><span class="sxs-lookup"><span data-stu-id="59230-p104">You can't assign multiple licenses to a user from the same licensing plan. If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="59230-132">Este exemplo atribui as licenças do plano de licenciamento do **litwareinc: enterprisepack** (Office 365 Enterprise E3) para todos os usuários não licenciados:</span><span class="sxs-lookup"><span data-stu-id="59230-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="59230-133">Este exemplo atribui as mesmas licenças aos usuários não licenciados no departamento de vendas nos Estados Unidos:</span><span class="sxs-lookup"><span data-stu-id="59230-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="59230-134">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="59230-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="59230-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="59230-135">See also</span></span>

[<span data-ttu-id="59230-136">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59230-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="59230-137">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59230-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="59230-138">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59230-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
