---
title: Atribuir funções a contas de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
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
ms.openlocfilehash: 999b44f56e2652c0d6d2d746a3ed204be9d1f69c
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072523"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="94cfa-103">Atribuir funções a contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94cfa-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="94cfa-104">Você pode atribuir funções de forma rápida e fácil às contas de usuário usando o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94cfa-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="94cfa-105">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="94cfa-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="94cfa-106">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) usando uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="94cfa-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="94cfa-107">Em seguida, determine o nome de entrada da conta de usuário que você deseja adicionar a uma função (exemplo: fredsm@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="94cfa-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="94cfa-108">Isso também é conhecido como nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="94cfa-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="94cfa-109">Em seguida, determine o nome da função.</span><span class="sxs-lookup"><span data-stu-id="94cfa-109">Next, determine the name of the role.</span></span> <span data-ttu-id="94cfa-110">Use essa [lista de permissões de função de administrador no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="94cfa-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="94cfa-111">Preste atenção nas anotações deste artigo.</span><span class="sxs-lookup"><span data-stu-id="94cfa-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="94cfa-112">Alguns nomes de função são diferentes para o Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94cfa-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="94cfa-113">Por exemplo, a função "administrador do SharePoint" no centro de administração do Microsoft 365 é chamada de "administrador de serviços do SharePoint" para o Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94cfa-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="94cfa-114">Em seguida, preencha os nomes de entrada e de função e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="94cfa-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
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

<span data-ttu-id="94cfa-115">Veja um exemplo de um conjunto de comandos concluído que atribui a função de administrador de serviços do SharePoint à conta belindan@contoso.com:</span><span class="sxs-lookup"><span data-stu-id="94cfa-115">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
```powershell
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

<span data-ttu-id="94cfa-116">Para exibir a lista de nomes de usuário para uma função específica, use estes comandos.</span><span class="sxs-lookup"><span data-stu-id="94cfa-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="94cfa-117">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94cfa-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="94cfa-118">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) usando uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="94cfa-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="94cfa-119">Para uma alteração de função única</span><span class="sxs-lookup"><span data-stu-id="94cfa-119">For a single role change</span></span>

<span data-ttu-id="94cfa-120">As formas mais comuns de uma conta de usuário específica são com seu nome de exibição ou seu nome de email, também conhecido como nome de logon ou nome UPN.</span><span class="sxs-lookup"><span data-stu-id="94cfa-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="94cfa-121">Exibir nomes de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="94cfa-121">Display names of user accounts</span></span>

<span data-ttu-id="94cfa-122">Se você estiver acostumado a trabalhar com os nomes de exibição das contas de usuário, determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="94cfa-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="94cfa-123">A conta de usuário que você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="94cfa-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="94cfa-124">Para especificar a conta de usuário, você deve determinar seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="94cfa-124">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="94cfa-125">Para obter uma lista completa de contas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="94cfa-125">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="94cfa-126">Este comando lista o nome de exibição de suas contas de usuário, classificados pelo nome de exibição, uma tela por vez.</span><span class="sxs-lookup"><span data-stu-id="94cfa-126">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="94cfa-127">Você pode filtrar a lista em um conjunto menor usando o cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="94cfa-127">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="94cfa-128">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="94cfa-128">Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="94cfa-129">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="94cfa-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="94cfa-130">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94cfa-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="94cfa-131">Este comando lista apenas as contas de usuário para as quais o nome de exibição começa com "John".</span><span class="sxs-lookup"><span data-stu-id="94cfa-131">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="94cfa-132">A função que você deseja atribuir.</span><span class="sxs-lookup"><span data-stu-id="94cfa-132">The role you want to assign.</span></span>
    
    <span data-ttu-id="94cfa-133">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="94cfa-133">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="94cfa-134">Depois de determinar o nome de exibição da conta e o nome da função, use estes comandos para atribuir a função à conta:</span><span class="sxs-lookup"><span data-stu-id="94cfa-134">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="94cfa-135">Copie os comandos e cole-os no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="94cfa-135">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="94cfa-136">Para as variáveis **$dispName** e **$roleName** , substitua o texto da descrição por seus valores, remova \< os caracteres e > e deixe as aspas.</span><span class="sxs-lookup"><span data-stu-id="94cfa-136">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="94cfa-137">Copie as linhas modificadas e cole-as em sua janela do módulo do Microsoft Azure Active Directory para Windows PowerShell para executá-las.</span><span class="sxs-lookup"><span data-stu-id="94cfa-137">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="94cfa-138">Como alternativa, você pode usar o ambiente de script integrado (ISE) do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94cfa-138">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="94cfa-139">Veja um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="94cfa-139">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="94cfa-140">Nomes de entrada de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="94cfa-140">Sign-in names of user accounts</span></span>

<span data-ttu-id="94cfa-141">Se você estiver acostumado a trabalhar com os nomes de entrada ou UPNs de contas de usuário, determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="94cfa-141">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="94cfa-142">O UPN da conta do usuário.</span><span class="sxs-lookup"><span data-stu-id="94cfa-142">The user account's UPN.</span></span>
    
    <span data-ttu-id="94cfa-143">Se você ainda não souber o UPN, use este comando:</span><span class="sxs-lookup"><span data-stu-id="94cfa-143">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="94cfa-144">Este comando lista o UPN de suas contas de usuário, classificados pelo UPN, uma tela por vez.</span><span class="sxs-lookup"><span data-stu-id="94cfa-144">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="94cfa-145">Você pode filtrar a lista em um conjunto menor usando o cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="94cfa-145">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="94cfa-146">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="94cfa-146">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="94cfa-147">Este comando lista apenas as contas de usuário para as quais o nome de exibição começa com "John".</span><span class="sxs-lookup"><span data-stu-id="94cfa-147">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="94cfa-148">A função que você deseja atribuir.</span><span class="sxs-lookup"><span data-stu-id="94cfa-148">The role you want to assign.</span></span>
    
    <span data-ttu-id="94cfa-149">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="94cfa-149">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="94cfa-150">Depois de ter o UPN da conta e o nome da função, use estes comandos para atribuir a função à conta:</span><span class="sxs-lookup"><span data-stu-id="94cfa-150">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="94cfa-151">Copie os comandos e cole-os no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="94cfa-151">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="94cfa-152">Para as variáveis **$upnName** e **$roleName** , substitua o texto da descrição por seus valores, remova \< os caracteres e > e deixe as aspas.</span><span class="sxs-lookup"><span data-stu-id="94cfa-152">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="94cfa-153">Copie as linhas modificadas e cole-as em sua janela do módulo do Microsoft Azure Active Directory para Windows PowerShell para executá-las.</span><span class="sxs-lookup"><span data-stu-id="94cfa-153">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="94cfa-154">Como alternativa, você pode usar o Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="94cfa-154">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="94cfa-155">Veja um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="94cfa-155">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="94cfa-156">Várias alterações de função</span><span class="sxs-lookup"><span data-stu-id="94cfa-156">Multiple role changes</span></span>

<span data-ttu-id="94cfa-157">Para várias alterações de função, determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="94cfa-157">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="94cfa-158">Quais contas de usuário você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="94cfa-158">Which user accounts that you want to configure.</span></span> <span data-ttu-id="94cfa-159">Você pode usar os métodos da seção anterior para coletar o conjunto de nomes de exibição ou UPNs.</span><span class="sxs-lookup"><span data-stu-id="94cfa-159">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="94cfa-160">Quais funções você deseja atribuir a cada conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="94cfa-160">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="94cfa-161">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="94cfa-161">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="94cfa-162">Em seguida, crie um arquivo de texto de valor separado por vírgula (CSV) que tenha os campos nome de exibição ou UPN e nome da função.</span><span class="sxs-lookup"><span data-stu-id="94cfa-162">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="94cfa-163">Você pode fazer isso facilmente com o Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="94cfa-163">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="94cfa-164">Veja um exemplo de nomes de exibição:</span><span class="sxs-lookup"><span data-stu-id="94cfa-164">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="94cfa-165">Em seguida, preencha o local do arquivo CSV e execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94cfa-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="94cfa-166">Veja um exemplo de UPNs:</span><span class="sxs-lookup"><span data-stu-id="94cfa-166">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="94cfa-167">Em seguida, preencha o local do arquivo CSV e execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94cfa-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="94cfa-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="94cfa-168">See also</span></span>

- [<span data-ttu-id="94cfa-169">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94cfa-169">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="94cfa-170">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94cfa-170">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="94cfa-171">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94cfa-171">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
