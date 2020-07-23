---
title: Manter a associação de grupo do Microsoft 365 com o PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Saiba como usar o PowerShell para manter a associação nos grupos do Microsoft 365.
ms.openlocfilehash: f75587c9c50a1fce3a5abfb00ddba2845318e9c4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230647"
---
# <a name="maintain-microsoft-365-group-membership-with-powershell"></a><span data-ttu-id="aa097-103">Manter a associação de grupo do Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa097-103">Maintain Microsoft 365 group membership with PowerShell</span></span>

<span data-ttu-id="aa097-104">*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="aa097-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="aa097-105">Você pode usar o PowerShell para o Microsoft 365 como uma alternativa para o centro de administração do Microsoft 365 para manter a associação de grupo no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="aa097-105">You can use PowerShell for Microsoft 365 as an alternative to the Microsoft 365 admin center to maintain group membership in Microsoft 365.</span></span> 

> [!TIP]
> <span data-ttu-id="aa097-106">Para gerar comandos do PowerShell prontos para execução especificando os nomes de conta e de grupo do usuário, use esta [pasta de trabalho de manutenção de grupo do Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span><span class="sxs-lookup"><span data-stu-id="aa097-106">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="aa097-107">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="aa097-107">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="aa097-108">Primeiro, [Conecte-se ao seu locatário do Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="aa097-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="aa097-109">Adicionar ou remover contas de usuário como membros de um grupo</span><span class="sxs-lookup"><span data-stu-id="aa097-109">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="aa097-110">**Para adicionar uma conta de usuário por seu UPN**, preencha o nome principal do usuário (UPN) da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo, removendo os caracteres "<" e ">" e execute esses comandos na janela do PowerShell ou no ISE (ambiente de script integrado) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-110">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="aa097-111">**Para adicionar uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-111">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="aa097-112">**Para remover uma conta de usuário por seu UPN**, preencha o UPN da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-112">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="aa097-113">**Para remover uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-113">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="aa097-114">Adicionar ou remover grupos como membros de um grupo</span><span class="sxs-lookup"><span data-stu-id="aa097-114">Add or remove groups as members of a group</span></span>

<span data-ttu-id="aa097-115">Os grupos de segurança podem conter outros grupos como membros.</span><span class="sxs-lookup"><span data-stu-id="aa097-115">Security groups can contain other groups as members.</span></span> <span data-ttu-id="aa097-116">Os grupos do Microsoft 365, no entanto, não podem.</span><span class="sxs-lookup"><span data-stu-id="aa097-116">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="aa097-117">Esta seção contém comandos do PowerShell para adicionar ou remover grupos apenas de um grupo de segurança.</span><span class="sxs-lookup"><span data-stu-id="aa097-117">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="aa097-118">**Para adicionar um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você adicionará e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-118">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="aa097-119">**Para remover um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você vai remover e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-119">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="aa097-120">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-120">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="aa097-121">Primeiro, [Conecte-se ao seu locatário do Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="aa097-121">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="aa097-122">Adicionar ou remover contas de usuário como membros de um grupo</span><span class="sxs-lookup"><span data-stu-id="aa097-122">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="aa097-123">**Para adicionar uma conta de usuário por seu UPN**, preencha o nome principal do usuário (UPN) da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo, removendo os caracteres "<" e ">" e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-123">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="aa097-124">**Para adicionar uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-124">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="aa097-125">**Para remover uma conta de usuário por seu UPN**, preencha o UPN da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-125">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="aa097-126">**Para remover uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-126">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="aa097-127">Adicionar ou remover grupos como membros de um grupo</span><span class="sxs-lookup"><span data-stu-id="aa097-127">Add or remove groups as members of a group</span></span>

<span data-ttu-id="aa097-128">Os grupos de segurança podem conter outros grupos como membros.</span><span class="sxs-lookup"><span data-stu-id="aa097-128">Security groups can contain other groups as members.</span></span> <span data-ttu-id="aa097-129">Os grupos do Microsoft 365, no entanto, não podem.</span><span class="sxs-lookup"><span data-stu-id="aa097-129">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="aa097-130">Esta seção contém comandos do PowerShell para adicionar ou remover grupos apenas de um grupo de segurança.</span><span class="sxs-lookup"><span data-stu-id="aa097-130">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="aa097-131">**Para adicionar um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você adicionará e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-131">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="aa097-132">**Para remover um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você vai remover e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa097-132">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="aa097-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa097-133">See also</span></span>

[<span data-ttu-id="aa097-134">Gerenciar contas de usuário, licenças e grupos do Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa097-134">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="aa097-135">Gerenciar o Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa097-135">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="aa097-136">Introdução ao PowerShell para o Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="aa097-136">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

