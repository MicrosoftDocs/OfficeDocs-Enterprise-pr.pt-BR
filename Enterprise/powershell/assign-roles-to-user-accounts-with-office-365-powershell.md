---
title: Atribuir funções a contas de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/30/2019
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
ms.openlocfilehash: d06b305c348d014ce526448d7f8401c26f4d1c47
ms.sourcegitcommit: 3100813cd7dff8b27b1a30a6d6ed5a7c4765c60f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "34586977"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="80713-103">Atribuir funções a contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80713-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="80713-104">Você pode atribuir funções de forma rápida e fácil às contas de usuário usando o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80713-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="80713-105">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="80713-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="80713-106">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) usando uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="80713-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="80713-107">Em seguida, determine o nome de entrada da conta de usuário que você deseja adicionar a uma função (exemplo: fredsm@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="80713-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="80713-108">Isso também é conhecido como nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="80713-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="80713-109">Em seguida, determine o nome da função.</span><span class="sxs-lookup"><span data-stu-id="80713-109">Next, determine the name of the role.</span></span> <span data-ttu-id="80713-110">Use essa [lista de permissões de função de administrador no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="80713-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="80713-111">Preste atenção nas anotações deste artigo.</span><span class="sxs-lookup"><span data-stu-id="80713-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="80713-112">Alguns nomes de função são diferentes para o Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80713-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="80713-113">Por exemplo, a função "administrador do SharePoint" no centro de administração do Microsoft 365 é chamada de "administrador de serviços do SharePoint" para o Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80713-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="80713-114">Em seguida, preencha os nomes de entrada e de função e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="80713-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
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

<span data-ttu-id="80713-115">Veja um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="80713-115">Here is an example of a completed command set:</span></span>
  
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

<span data-ttu-id="80713-116">Para exibir a lista de nomes de usuário para uma função específica, use estes comandos.</span><span class="sxs-lookup"><span data-stu-id="80713-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="80713-117">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80713-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="80713-118">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) usando uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="80713-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="80713-119">Para uma alteração de função única</span><span class="sxs-lookup"><span data-stu-id="80713-119">For a single role change</span></span>

<span data-ttu-id="80713-120">As formas mais comuns de uma conta de usuário específica são com seu nome de exibição ou seu nome de email, também conhecido como nome principal de usuário (UPN) do nome de entrada.</span><span class="sxs-lookup"><span data-stu-id="80713-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="80713-121">Exibir nomes de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="80713-121">Display names of user accounts</span></span>

<span data-ttu-id="80713-122">Se você estiver acostumado a trabalhar com os nomes de exibição das contas de usuário, determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="80713-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="80713-123">A conta de usuário que você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="80713-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="80713-124">Para especificar a conta de usuário, você deve determinar seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="80713-124">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="80713-125">Para obter uma lista completa de contas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="80713-125">To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="80713-126">Este comando lista o nome de exibição de suas contas de usuário, classificados pelo nome de exibição, uma tela por vez.</span><span class="sxs-lookup"><span data-stu-id="80713-126">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="80713-127">Você pode filtrar a lista em um conjunto menor usando o cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="80713-127">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="80713-128">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="80713-128">Here is an example:</span></span>
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="80713-129">Este comando lista apenas as contas de usuário para as quais o nome de exibição começa com "John".</span><span class="sxs-lookup"><span data-stu-id="80713-129">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="80713-130">A função que você deseja atribuir.</span><span class="sxs-lookup"><span data-stu-id="80713-130">The role you want to assign.</span></span>
    
    <span data-ttu-id="80713-131">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="80713-131">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="80713-132">Depois de determinar o nome de exibição da conta e o nome da função, use estes comandos para atribuir a função à conta:</span><span class="sxs-lookup"><span data-stu-id="80713-132">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="80713-133">Copie os comandos e cole-os no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="80713-133">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="80713-134">Para as variáveis **$dispName** e **$roleName** , substitua o texto da descrição por seus valores, remova \< os caracteres e > e deixe as aspas.</span><span class="sxs-lookup"><span data-stu-id="80713-134">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="80713-135">Copie as linhas modificadas e cole-as em sua janela do módulo do Microsoft Azure Active Directory para Windows PowerShell para executá-las.</span><span class="sxs-lookup"><span data-stu-id="80713-135">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="80713-136">Como alternativa, você pode usar o ambiente de script integrado (ISE) do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80713-136">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="80713-137">Veja um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="80713-137">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="80713-138">Nomes de entrada de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="80713-138">Sign-in names of user accounts</span></span>

<span data-ttu-id="80713-139">Se você estiver acostumado a trabalhar com os nomes de entrada ou UPNs de contas de usuário, determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="80713-139">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="80713-140">O UPN da conta do usuário.</span><span class="sxs-lookup"><span data-stu-id="80713-140">The user account's UPN.</span></span>
    
    <span data-ttu-id="80713-141">Se você ainda não souber o UPN, use este comando:</span><span class="sxs-lookup"><span data-stu-id="80713-141">If you don't already know the UPN, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="80713-142">Este comando lista o UPN de suas contas de usuário, classificados pelo UPN, uma tela por vez.</span><span class="sxs-lookup"><span data-stu-id="80713-142">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="80713-143">Você pode filtrar a lista em um conjunto menor usando o cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="80713-143">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="80713-144">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="80713-144">Here is an example:</span></span>
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="80713-145">Este comando lista apenas as contas de usuário para as quais o nome de exibição começa com "John".</span><span class="sxs-lookup"><span data-stu-id="80713-145">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="80713-146">A função que você deseja atribuir.</span><span class="sxs-lookup"><span data-stu-id="80713-146">The role you want to assign.</span></span>
    
    <span data-ttu-id="80713-147">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="80713-147">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="80713-148">Depois de ter o UPN da conta e o nome da função, use estes comandos para atribuir a função à conta:</span><span class="sxs-lookup"><span data-stu-id="80713-148">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="80713-149">Copie os comandos e cole-os no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="80713-149">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="80713-150">Para as variáveis **$upnName** e **$roleName** , substitua o texto da descrição por seus valores, remova \< os caracteres e > e deixe as aspas.</span><span class="sxs-lookup"><span data-stu-id="80713-150">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="80713-151">Copie as linhas modificadas e cole-as em sua janela do módulo do Microsoft Azure Active Directory para Windows PowerShell para executá-las.</span><span class="sxs-lookup"><span data-stu-id="80713-151">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="80713-152">Como alternativa, você pode usar o Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="80713-152">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="80713-153">Veja um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="80713-153">Here is an example of a completed command set:</span></span>
  
```
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="80713-154">Para várias alterações de função</span><span class="sxs-lookup"><span data-stu-id="80713-154">For multiple role changes</span></span>

<span data-ttu-id="80713-155">Determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="80713-155">Determine the following:</span></span>
  
- <span data-ttu-id="80713-156">Quais contas de usuário você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="80713-156">Which user accounts that you want to configure.</span></span> <span data-ttu-id="80713-157">Você pode usar os métodos da seção anterior para coletar o conjunto de nomes de exibição ou UPNs.</span><span class="sxs-lookup"><span data-stu-id="80713-157">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="80713-158">Quais funções você deseja atribuir a cada conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="80713-158">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="80713-159">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="80713-159">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="80713-160">Em seguida, crie um arquivo de texto de valor separado por vírgula (CSV) que tenha os campos nome de exibição ou UPN e nome da função.</span><span class="sxs-lookup"><span data-stu-id="80713-160">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="80713-161">Você pode fazer isso facilmente com o Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="80713-161">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="80713-162">Veja um exemplo de nomes de exibição:</span><span class="sxs-lookup"><span data-stu-id="80713-162">Here is an example for display names:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="80713-163">Em seguida, preencha o local do arquivo CSV e execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80713-163">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="80713-164">Veja um exemplo de UPNs:</span><span class="sxs-lookup"><span data-stu-id="80713-164">Here is an example for UPNs:</span></span>
  
```
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="80713-165">Em seguida, preencha o local do arquivo CSV e execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80713-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a><span data-ttu-id="80713-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="80713-166">See also</span></span>

- [<span data-ttu-id="80713-167">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80713-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="80713-168">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80713-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="80713-169">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80713-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
