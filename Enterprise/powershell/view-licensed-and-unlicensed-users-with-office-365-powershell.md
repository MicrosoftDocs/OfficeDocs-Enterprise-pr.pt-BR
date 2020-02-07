---
title: Exibir usuários licenciados e não licenciados com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/18/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Explica como usar o Office 365 PowerShell para exibir as contas de usuários licenciados e não licenciados.
ms.openlocfilehash: 4b2f2b5b3898b9f800cc3fb9416c5b666472d907
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844142"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="62213-103">Exibir usuários licenciados e não licenciados com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="62213-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="62213-p101">As contas de usuário em sua organização do Office 365 podem ter algumas, todas ou nenhuma das licenças disponíveis atribuídas a elas em planos de licenciamento que estão disponíveis em sua organização. Você pode usar o Office 365 PowerShell para localizar rapidamente os usuários licenciados e não licenciados em sua organização.</span><span class="sxs-lookup"><span data-stu-id="62213-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="62213-106">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="62213-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="62213-107">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="62213-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="62213-108">Para exibir a lista de todas as contas de usuário em sua organização que não tenham sido atribuídos a nenhum dos seus planos de licenciamento (usuários não licenciados), execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="62213-108">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="62213-109">Para exibir a lista de todas as contas de usuário em sua organização que foram atribuídas a qualquer um dos seus planos de licenciamento (usuários licenciados), execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="62213-109">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
><span data-ttu-id="62213-110">Para listar todos os usuários em sua assinatura, use o `Get-AzureAdUser -All $true` comando.</span><span class="sxs-lookup"><span data-stu-id="62213-110">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="62213-111">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62213-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="62213-112">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="62213-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="62213-113">Para exibir a lista de todas as contas de usuário e seu status de licenciamento em sua organização, execute o seguinte comando no Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="62213-113">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

>[!Note]
><span data-ttu-id="62213-114">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="62213-114">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="62213-115">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62213-115">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="62213-116">Para visualizar a lista de todas as contas de usuários não licenciados em sua organização, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="62213-116">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="62213-117">Para visualizar a lista de todas as contas de usuários licenciados em sua organização, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="62213-117">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="62213-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="62213-118">See also</span></span>

[<span data-ttu-id="62213-119">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="62213-119">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="62213-120">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="62213-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="62213-121">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="62213-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
