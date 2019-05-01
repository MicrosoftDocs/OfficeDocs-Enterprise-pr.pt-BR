---
title: Atribuir funções a contas de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Resumo: Use o Office 365 PowerShell para atribuir funções a contas de usuário.'
ms.openlocfilehash: 78f2e08df6d46588b93dc217d0e16b7c3a350a88
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491987"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="05fe8-103">Atribuir funções a contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05fe8-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="05fe8-104">Você pode atribuir funções de forma rápida e fácil às contas de usuário usando o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05fe8-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="05fe8-105">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="05fe8-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="05fe8-106">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) usando uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="05fe8-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="05fe8-107">Em seguida, determine o nome de entrada da conta de usuário que você deseja adicionar a uma função (exemplo: fredsm@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="05fe8-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="05fe8-108">Isso também é conhecido como nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="05fe8-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="05fe8-109">Em seguida, determine o nome da função.</span><span class="sxs-lookup"><span data-stu-id="05fe8-109">Next, determine the name of the role.</span></span> <span data-ttu-id="05fe8-110">Use essa [lista de permissões de função de administrador no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="05fe8-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="05fe8-111">Preste atenção nas anotações deste artigo.</span><span class="sxs-lookup"><span data-stu-id="05fe8-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="05fe8-112">Alguns nomes de função são diferentes para o Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05fe8-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="05fe8-113">Por exemplo, a função "administrador do SharePoint" no centro de administração do Microsoft 365 é chamada de "administrador de serviços do SharePoint" para o Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05fe8-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="05fe8-114">Em seguida, preencha os nomes de entrada e de função e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="05fe8-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="05fe8-115">Veja um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="05fe8-115">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="05fe8-116">Para exibir a lista de nomes de usuário para uma função específica, use estes comandos.</span><span class="sxs-lookup"><span data-stu-id="05fe8-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="05fe8-117">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05fe8-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="05fe8-118">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) usando uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="05fe8-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="05fe8-119">Para uma alteração de função única</span><span class="sxs-lookup"><span data-stu-id="05fe8-119">For a single role change</span></span>

<span data-ttu-id="05fe8-120">Determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="05fe8-120">Determine the following:</span></span>
  
- <span data-ttu-id="05fe8-121">A conta de usuário que você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="05fe8-121">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="05fe8-122">Para especificar a conta de usuário, você deve determinar seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="05fe8-122">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="05fe8-123">Para obter uma lista completa de contas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="05fe8-123">To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="05fe8-124">Este comando lista o nome de exibição de suas contas de usuário, classificados pelo nome de exibição, uma tela por vez.</span><span class="sxs-lookup"><span data-stu-id="05fe8-124">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="05fe8-125">Você pode filtrar a lista em um conjunto menor usando o cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="05fe8-125">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="05fe8-126">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="05fe8-126">Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="05fe8-127">Este comando lista apenas as contas de usuário para as quais o nome de exibição começa com "John".</span><span class="sxs-lookup"><span data-stu-id="05fe8-127">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="05fe8-128">A função que você deseja atribuir.</span><span class="sxs-lookup"><span data-stu-id="05fe8-128">The role you want to assign.</span></span>
    
    <span data-ttu-id="05fe8-129">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="05fe8-129">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="05fe8-130">Depois de determinar o nome de exibição da conta e o nome da função, use estes comandos para atribuir a função à conta:</span><span class="sxs-lookup"><span data-stu-id="05fe8-130">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="05fe8-131">Copie os comandos e cole-os no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="05fe8-131">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="05fe8-132">Para as variáveis **$dispName** e **$roleName** , substitua o texto da descrição por seus valores, remova \< os caracteres e > e deixe as aspas.</span><span class="sxs-lookup"><span data-stu-id="05fe8-132">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="05fe8-133">Copie as linhas modificadas e cole-as em sua janela do módulo do Microsoft Azure Active Directory para Windows PowerShell para executá-las.</span><span class="sxs-lookup"><span data-stu-id="05fe8-133">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="05fe8-134">Como alternativa, você pode usar o ambiente de script integrado (ISE) do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05fe8-134">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="05fe8-135">Veja um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="05fe8-135">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="05fe8-136">Para várias alterações de função</span><span class="sxs-lookup"><span data-stu-id="05fe8-136">For multiple role changes</span></span>

<span data-ttu-id="05fe8-137">Determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="05fe8-137">Determine the following:</span></span>
  
- <span data-ttu-id="05fe8-138">Quais contas de usuário você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="05fe8-138">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="05fe8-139">Para especificar a conta de usuário, você deve determinar seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="05fe8-139">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="05fe8-140">Para obter uma lista de contas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="05fe8-140">To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="05fe8-141">Este comando lista o nome de exibição de todas as suas contas de usuário, classificados pelo nome de exibição, uma tela por vez.</span><span class="sxs-lookup"><span data-stu-id="05fe8-141">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="05fe8-142">Você pode filtrar a lista em um conjunto menor usando o cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="05fe8-142">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="05fe8-143">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="05fe8-143">Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="05fe8-144">Este comando lista apenas as contas de usuário para as quais o nome de exibição começa com "John".</span><span class="sxs-lookup"><span data-stu-id="05fe8-144">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="05fe8-145">Quais funções você deseja atribuir a cada conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="05fe8-145">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="05fe8-146">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="05fe8-146">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="05fe8-147">Em seguida, crie um arquivo de texto de valor separado por vírgula (CSV) que tenha os campos DisplayName e nome da função.</span><span class="sxs-lookup"><span data-stu-id="05fe8-147">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields.</span></span> <span data-ttu-id="05fe8-148">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="05fe8-148">Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="05fe8-149">Em seguida, preencha o local do arquivo CSV e execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05fe8-149">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="05fe8-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="05fe8-150">See also</span></span>

- [<span data-ttu-id="05fe8-151">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05fe8-151">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="05fe8-152">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05fe8-152">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="05fe8-153">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05fe8-153">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
