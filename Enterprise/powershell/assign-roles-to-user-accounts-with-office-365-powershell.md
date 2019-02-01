---
title: Atribuir funções a contas de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
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
description: 'Resumo: Usar o PowerShell do Office 365 para atribuir funções a contas de usuário.'
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690432"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c8472-103">Atribuir funções a contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8472-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c8472-104">Você pode atribuir rapidez e facilidade funções às contas de usuário usando o PowerShell do Office 365.</span><span class="sxs-lookup"><span data-stu-id="c8472-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c8472-105">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="c8472-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c8472-106">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) usando uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c8472-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="c8472-p101">Em seguida, determine o nome de entrada da conta de usuário que você deseja adicionar a uma função (exemplo: fredsm@contoso.com). Isso também é conhecido como o nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="c8472-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="c8472-p102">Em seguida, determine o nome da função. Use este comando para listar as funções que podem ser atribuídos com o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8472-p102">Next, determine the name of the role. Use this command to list the roles that you can assign with PowerShell.</span></span>

````
Get-AzureADDirectoryRole
````

<span data-ttu-id="c8472-111">Em seguida, preencha os nomes de entrada e de função e executar esses comandos.</span><span class="sxs-lookup"><span data-stu-id="c8472-111">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="c8472-112">Aqui está um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="c8472-112">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="c8472-113">Para exibir a lista de nomes de usuário para uma função específica, use esses comandos.</span><span class="sxs-lookup"><span data-stu-id="c8472-113">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c8472-114">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8472-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c8472-115">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) usando uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c8472-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="c8472-116">Para alterar uma única função</span><span class="sxs-lookup"><span data-stu-id="c8472-116">For a single role change</span></span>

<span data-ttu-id="c8472-117">Determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c8472-117">Determine the following:</span></span>
  
- <span data-ttu-id="c8472-118">A conta de usuário que você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="c8472-118">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="c8472-p103">Para especificar a conta de usuário, você deve determinar seu nome para exibição. Para obter uma lista completa de contas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="c8472-p103">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c8472-p104">Este comando lista o nome de exibição de suas contas de usuário, classificadas por nome de exibição, uma tela por vez. Você pode filtrar a lista para um conjunto menor usando o cmdlet **onde** . Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8472-p104">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c8472-124">Este comando lista apenas as contas de usuário para o qual o nome de exibição começa com "João".</span><span class="sxs-lookup"><span data-stu-id="c8472-124">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="c8472-125">A função que você deseja atribuir.</span><span class="sxs-lookup"><span data-stu-id="c8472-125">The role you want to assign.</span></span>
    
    <span data-ttu-id="c8472-126">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="c8472-126">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c8472-127">Depois de ter determinado o nome para exibição da conta e o nome da função, use estes comandos para atribuir a função para a conta:</span><span class="sxs-lookup"><span data-stu-id="c8472-127">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="c8472-p105">Copie os comandos e colá-las no bloco de notas. Para as variáveis **$dispName** e **$roleName** , substitua o texto de descrição com seus valores, remova o \< e caracteres gt _ e deixe as aspas. Copie as linhas modificadas e colá-los em sua janela do Windows Azure Active Directory módulo para Windows PowerShell para executá-los. Como alternativa, você pode usar o Windows PowerShell integrada Script Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="c8472-p105">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="c8472-132">Aqui está um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="c8472-132">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="c8472-133">Para várias alterações de função</span><span class="sxs-lookup"><span data-stu-id="c8472-133">For multiple role changes</span></span>

<span data-ttu-id="c8472-134">Determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c8472-134">Determine the following:</span></span>
  
- <span data-ttu-id="c8472-135">Quais contas de usuário que você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="c8472-135">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="c8472-p106">Para especificar a conta de usuário, você deve determinar seu nome para exibição. Para obter uma lista de contas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="c8472-p106">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c8472-p107">Este comando lista o nome de exibição de todas as suas contas de usuário, classificadas por nome de exibição, uma tela por vez. Você pode filtrar a lista para um conjunto menor usando o cmdlet **onde** . Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8472-p107">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c8472-141">Este comando lista apenas as contas de usuário para o qual o nome de exibição começa com "João".</span><span class="sxs-lookup"><span data-stu-id="c8472-141">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="c8472-142">Quais funções que você deseja atribuir a cada conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="c8472-142">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="c8472-143">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="c8472-143">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c8472-p108">Em seguida, crie um arquivo de texto delimitado por vírgula (CSV) que possui o DisplayName e role nomear campos. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8472-p108">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="c8472-146">Em seguida, preencha o local do arquivo CSV e execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8472-146">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="c8472-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8472-147">See also</span></span>

- [<span data-ttu-id="c8472-148">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8472-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="c8472-149">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8472-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="c8472-150">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8472-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
