---
title: Deletar contas de usuários usando o Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Saiba como usar o Office 365 PowerShell para excluir contas de usuários do Office 365.
ms.openlocfilehash: dd7e5052f8933955267302a5d03870017702a7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069037"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a>Deletar contas de usuários usando o Office 365 PowerShell

**Resumo:** Saiba como usar o Office 365 PowerShell para excluir e restaurar contas de usuários do Office 365.
  
Você pode usar o PowerShell do Office 365 para excluir uma conta de usuário.

   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Após a conexão, use a seguinte sintaxe para remover uma conta de usuário individual:
  
```
Remove-AzureADUser -ObjectID <sign-in name>
```

Este exemplo remove a conta de usuário ricardoc@litwareinc.com.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> O parâmetro **-ObjectID** no cmdlet **Remove-AzureAD** aceita o nome de usuário da conta, também conhecido como o nome UPN, ou a ID de objeto da conta.
  
Para exibir o nome da conta com base no nome do usuário, use os seguintes comandos:
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este exemplo exibe o nome da conta do usuário Carlos Lima.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para remover uma conta com base no nome de exibição do usuário, use os seguintes comandos:
  
```
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Quando você exclui uma conta de usuário com o Módulo Microsoft Azure Active Directory para Windows PowerShell, ela não é excluída permanentemente. Você pode restaurar a conta de usuário excluída no prazo de 30 dias.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


Para excluir uma conta de usuário, use a seguinte sintaxe:
  
```
Remove-MsolUser -UserPrincipalName <sign-in name>
```

Este exemplo exclui a conta de usuário BrendaF@litwareinc.com.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Para restaurar uma conta de usuário excluída no período de tolerância de 30 dias, use a seguinte sintaxe:
  
```
Restore-MsolUser -UserPrincipalName <sign-in name>
```

Este exemplo restaura a conta excluída BrendaF@litwareinc.com.
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Observações:**
  
- Para ver a lista de usuários excluídos que pode ser restaurados, execute o seguinte comando:
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Se o nome UPN (nome principal do usuário) original da conta de usuário for usado por outra conta, use o parâmetro _NewUserPrincipalName_ no lugar de _UserPrincipalName_ para especificar um UPN diferente ao restaurar a conta de usuário.


## <a name="see-also"></a>Confira também

[Gerenciar licenças e contas de usuário usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

