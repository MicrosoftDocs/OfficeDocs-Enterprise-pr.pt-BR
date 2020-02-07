---
title: Manter Associação de grupo com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Saiba como usar o Office 365 PowerShell para manter a associação em grupos do Office 365.
ms.openlocfilehash: 397f8d93df5e9abef0779e4eb56df7bab9ef2344
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841478"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="b17a9-103">Manter Associação de grupo com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b17a9-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="b17a9-104">Você pode usar o Office 365 PowerShell como uma alternativa para o centro de administração do Microsoft 365 para manter a associação de grupo no Office 365.</span><span class="sxs-lookup"><span data-stu-id="b17a9-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="b17a9-105">Para gerar comandos do PowerShell prontos para execução especificando os nomes de conta e de grupo do usuário, use esta [pasta de trabalho de manutenção de grupo do Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span><span class="sxs-lookup"><span data-stu-id="b17a9-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b17a9-106">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="b17a9-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="b17a9-107">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="b17a9-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="b17a9-108">Adicionar ou remover contas de usuário como membros de um grupo</span><span class="sxs-lookup"><span data-stu-id="b17a9-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="b17a9-109">**Para adicionar uma conta de usuário por seu UPN**, preencha o nome principal do usuário (UPN) da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo, removendo os caracteres "<" e ">" e execute esses comandos na janela do PowerShell ou no ISE (ambiente de script integrado) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="b17a9-110">**Para adicionar uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="b17a9-111">**Para remover uma conta de usuário por seu UPN**, preencha o UPN da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="b17a9-112">**Para remover uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="b17a9-113">Adicionar ou remover grupos como membros de um grupo</span><span class="sxs-lookup"><span data-stu-id="b17a9-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="b17a9-114">Os grupos de segurança podem conter outros grupos como membros.</span><span class="sxs-lookup"><span data-stu-id="b17a9-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="b17a9-115">No entanto, os grupos do Office 365 não podem.</span><span class="sxs-lookup"><span data-stu-id="b17a9-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="b17a9-116">Esta seção contém comandos do PowerShell para adicionar ou remover grupos apenas de um grupo de segurança.</span><span class="sxs-lookup"><span data-stu-id="b17a9-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="b17a9-117">**Para adicionar um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você adicionará e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="b17a9-118">**Para remover um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você vai remover e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b17a9-119">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b17a9-120">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b17a9-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="b17a9-121">Adicionar ou remover contas de usuário como membros de um grupo</span><span class="sxs-lookup"><span data-stu-id="b17a9-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="b17a9-122">**Para adicionar uma conta de usuário por seu UPN**, preencha o nome principal do usuário (UPN) da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo, removendo os caracteres "<" e ">" e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="b17a9-123">**Para adicionar uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="b17a9-124">**Para remover uma conta de usuário por seu UPN**, preencha o UPN da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="b17a9-125">**Para remover uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="b17a9-126">Adicionar ou remover grupos como membros de um grupo</span><span class="sxs-lookup"><span data-stu-id="b17a9-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="b17a9-127">Os grupos de segurança podem conter outros grupos como membros.</span><span class="sxs-lookup"><span data-stu-id="b17a9-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="b17a9-128">No entanto, os grupos do Office 365 não podem.</span><span class="sxs-lookup"><span data-stu-id="b17a9-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="b17a9-129">Esta seção contém comandos do PowerShell para adicionar ou remover grupos apenas de um grupo de segurança.</span><span class="sxs-lookup"><span data-stu-id="b17a9-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="b17a9-130">**Para adicionar um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você adicionará e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="b17a9-131">**Para remover um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você vai remover e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b17a9-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="b17a9-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="b17a9-132">See also</span></span>

[<span data-ttu-id="b17a9-133">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b17a9-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b17a9-134">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b17a9-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b17a9-135">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b17a9-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

