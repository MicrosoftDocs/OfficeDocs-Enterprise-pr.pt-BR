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
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Atribuir funções a contas de usuário com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell e o cmdlet **Add-MsolRoleMember** para atribuir funções a contas de usuário.
  
Você pode atribuir rapidez e facilidade funções a contas de usuário usando o Office 365 PowerShell identificando o nome para exibição da conta do usuário e o nome da função.
  
## <a name="before-you-begin"></a>Antes de começar

Os procedimentos neste tópico exigem que você para se conectar ao Office 365 PowerShell usando uma conta de administrador global. Para obter instruções, consulte [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="for-a-single-role-change"></a>Para alterar uma única função

Determine o seguinte:
  
- A conta de usuário que você deseja configurar.
    
    Para especificar a conta de usuário, você deve determinar seu nome para exibição. Para obter uma lista completa de contas, use este comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Este comando lista o nome de exibição de suas contas de usuário, classificadas por nome de exibição, uma tela por vez. Você pode filtrar a lista para um conjunto menor usando o cmdlet **onde** . Aqui está um exemplo:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Este comando lista apenas as contas de usuário para o qual o nome de exibição começa com "João".
    
- A função que você deseja atribuir.
    
    Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Depois de ter determinado o nome para exibição da conta e o nome da função, use estes comandos para atribuir a função para a conta:
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Copie os comandos e colá-las no bloco de notas. Para as variáveis **$dispName** e **$roleName** , substitua o texto de descrição com seus valores, remova o \< e > caracteres e deixe as aspas. Copie as linhas modificadas e colá-los em sua janela do Windows Azure Active Directory módulo para Windows PowerShell para executá-los. Como alternativa, você pode usar o Windows PowerShell integrada Script Environment (ISE).
  
Aqui está um exemplo de um conjunto de comandos concluído:
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>Para várias alterações de função

Determine o seguinte:
  
- Quais contas de usuário que você deseja configurar.
    
    Para especificar a conta de usuário, você deve determinar seu nome para exibição. Para obter uma lista de contas, use este comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Este comando lista o nome de exibição de todas as suas contas de usuário, classificadas por nome de exibição, uma tela por vez. Você pode filtrar a lista para um conjunto menor usando o cmdlet **onde** . Aqui está um exemplo:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Este comando lista apenas as contas de usuário para o qual o nome de exibição começa com "João".
    
- Quais funções que você deseja atribuir a cada conta de usuário.
    
    Para exibir a lista de funções disponíveis que você pode atribuir às contas de usuário, use este comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Em seguida, crie um arquivo de texto delimitado por vírgula (CSV) que contém o DisplayName e função nomear campos. Aqui está um exemplo:
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

Em seguida, preencha o local do arquivo CSV e execute os comandos resultantes no prompt de comando do PowerShell.
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Veja também

#### 

[Gerenciar contas de usuário e licenças usando o PowerShell do Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
#### 

[Adicionar-MsolRoleMember](https://msdn.microsoft.com/library/dn194120.aspx)

