---
title: "Atribuir funções a contas de usuário com o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: O365ITProTrain, PowerShell, Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "Resumo: Use o Office 365 PowerShell e o cmdlet Add-MsolRoleMember para atribuir funções a contas de usuário."
ms.openlocfilehash: 68e8be24f1581aa3430bca95206ecc1b2512f09a
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="dad83-103">Atribuir funções a contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dad83-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="dad83-104">**Resumo:** Use o Office 365 PowerShell e o cmdlet **Add-MsolRoleMember** para atribuir funções a contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="dad83-104">**Summary:** Use Office 365 PowerShell and the **Add-MsolRoleMember** cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="dad83-105">Você pode atribuir rapidez e facilidade funções a contas de usuário usando o Office 365 PowerShell identificando o nome para exibição da conta do usuário e o nome da função.</span><span class="sxs-lookup"><span data-stu-id="dad83-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="dad83-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="dad83-106">Before you begin</span></span>

<span data-ttu-id="dad83-p101">Os procedimentos neste tópico exigem que você para se conectar ao Office 365 PowerShell usando uma conta de administrador global. Para obter instruções, consulte [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="dad83-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="dad83-109">Para alterar uma única função</span><span class="sxs-lookup"><span data-stu-id="dad83-109">For a single role change</span></span>

<span data-ttu-id="dad83-110">Determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dad83-110">Determine the following:</span></span>
  
- <span data-ttu-id="dad83-111">A conta de usuário que você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="dad83-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="dad83-p102">Para especificar a conta de usuário, você deve determinar seu nome para exibição. Para obter uma lista completa de contas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="dad83-p102">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="dad83-p103">Este comando lista o nome de exibição de suas contas de usuário, classificadas por nome de exibição, uma tela por vez. Você pode filtrar a lista para um conjunto menor usando o cmdlet **onde** . Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="dad83-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="dad83-117">Este comando lista apenas as contas de usuário para o qual o nome de exibição começa com "João".</span><span class="sxs-lookup"><span data-stu-id="dad83-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="dad83-118">A função que você deseja atribuir.</span><span class="sxs-lookup"><span data-stu-id="dad83-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="dad83-119">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="dad83-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="dad83-120">Depois de ter determinado o nome para exibição da conta e o nome da função, use estes comandos para atribuir a função para a conta:</span><span class="sxs-lookup"><span data-stu-id="dad83-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="dad83-p104">Copie os comandos e colá-las no bloco de notas. Para as variáveis **$dispName** e **$roleName** , substitua o texto de descrição com seus valores, remova o \< e > caracteres e deixe as aspas. Copie as linhas modificadas e colá-los em sua janela do Windows Azure Active Directory módulo para Windows PowerShell para executá-los. Como alternativa, você pode usar o Windows PowerShell integrada Script Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="dad83-p104">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="dad83-125">Aqui está um exemplo de um conjunto de comandos concluído:</span><span class="sxs-lookup"><span data-stu-id="dad83-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="dad83-126">Para várias alterações de função</span><span class="sxs-lookup"><span data-stu-id="dad83-126">For multiple role changes</span></span>

<span data-ttu-id="dad83-127">Determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dad83-127">Determine the following:</span></span>
  
- <span data-ttu-id="dad83-128">Quais contas de usuário que você deseja configurar.</span><span class="sxs-lookup"><span data-stu-id="dad83-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="dad83-p105">Para especificar a conta de usuário, você deve determinar seu nome para exibição. Para obter uma lista de contas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="dad83-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="dad83-p106">Este comando lista o nome de exibição de todas as suas contas de usuário, classificadas por nome de exibição, uma tela por vez. Você pode filtrar a lista para um conjunto menor usando o cmdlet **onde** . Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="dad83-p106">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="dad83-134">Este comando lista apenas as contas de usuário para o qual o nome de exibição começa com "João".</span><span class="sxs-lookup"><span data-stu-id="dad83-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="dad83-135">Quais funções que você deseja atribuir a cada conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="dad83-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="dad83-136">Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:</span><span class="sxs-lookup"><span data-stu-id="dad83-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="dad83-p107">Em seguida, crie um arquivo de texto delimitado por vírgula (CSV) que contém o DisplayName e função nomear campos. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="dad83-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="dad83-139">Em seguida, preencha o local do arquivo CSV e execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dad83-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="dad83-140">Veja também</span><span class="sxs-lookup"><span data-stu-id="dad83-140">See also</span></span>

#### 

[<span data-ttu-id="dad83-141">Gerenciar contas de usuário e licenças usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="dad83-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="dad83-142">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dad83-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="dad83-143">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dad83-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

[<span data-ttu-id="dad83-144">Adicionar-MsolRoleMember</span><span class="sxs-lookup"><span data-stu-id="dad83-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)

