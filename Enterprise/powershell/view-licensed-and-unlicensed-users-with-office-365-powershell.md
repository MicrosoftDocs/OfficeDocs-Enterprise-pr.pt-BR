---
title: Exibir usuários licenciados e não licenciados com o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Explica como usar o Office 365 PowerShell para exibir as contas de usuários licenciados e não licenciados.
ms.openlocfilehash: 8b0456b468f4e0f912491f4a138d5868feb5abbc
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071127"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="2432f-103">Exibir usuários licenciados e não licenciados com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2432f-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="2432f-104">**Resumo:** explica como usar o Office 365 PowerShell para exibir as contas de usuários licenciados e não licenciados.</span><span class="sxs-lookup"><span data-stu-id="2432f-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="2432f-p101">As contas de usuário em sua organização do Office 365 podem ter algumas, todas ou nenhuma das licenças disponíveis atribuídas a elas em planos de licenciamento que estão disponíveis em sua organização. Você pode usar o Office 365 PowerShell para localizar rapidamente os usuários licenciados e não licenciados em sua organização.</span><span class="sxs-lookup"><span data-stu-id="2432f-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="2432f-107">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="2432f-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="2432f-108">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="2432f-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="2432f-109">Para exibir a lista de todas as contas de usuário em sua organização que não tenham sido atribuídos a nenhum dos seus planos de licenciamento (usuários não licenciados), execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2432f-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="2432f-110">Para exibir a lista de todas as contas de usuário em sua organização que foram atribuídas a qualquer um dos seus planos de licenciamento (usuários licenciados), execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2432f-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="2432f-111">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2432f-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="2432f-112">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2432f-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="2432f-113">Para exibir a lista de todas as contas de usuário e seu status de licenciamento em sua organização, execute o seguinte comando no Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="2432f-113">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="2432f-114">Para visualizar a lista de todas as contas de usuários não licenciados em sua organização, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2432f-114">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="2432f-115">Para visualizar a lista de todas as contas de usuários licenciados em sua organização, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2432f-115">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="2432f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="2432f-116">See also</span></span>

[<span data-ttu-id="2432f-117">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2432f-117">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="2432f-118">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2432f-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2432f-119">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2432f-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
