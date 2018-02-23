---
title: "Excluir e restaurar contas de usuários usando o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: PowerShell, Ent_Office_Other, O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Saiba como usar o Office 365 PowerShell para excluir e restaurar contas de usuários do Office 365."
ms.openlocfilehash: 1f1212de342894f6ca9f478a0830c45458d27511
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>Excluir e restaurar contas de usuários usando o Office 365 PowerShell

**Resumo:** saiba como usar o Office 365 PowerShell para excluir e restaurar contas de usuários do Office 365.
  
Quando você usa o Office 365 PowerShell para excluir uma conta de usuário, ela não é excluída permanentemente. Você pode restaurar a conta excluída do usuário no prazo de 30 dias.
  
## <a name="before-you-begin"></a>Antes de começar

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Confira como fazer isso em [Conectar-se ao Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Usar o Office 365 PowerShell para bloquear o acesso a contas de usuário individuais
<a name="ShortVersion"> </a>

Para excluir uma conta de usuário, use a seguinte sintaxe:
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

Este exemplo exclui a conta de usuário BrendaF@litwareinc.com.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Para restaurar uma conta de usuário excluída no período de tolerância de 30 dias, use a seguinte sintaxe:
  
```
Restore-MsolUser -UserPrincipalName <Account>
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

- Se o nome UPN (nome principal do usuário) original da conta de usuário for usado por outra conta, use o parâmetro  _NewUserPrincipalName_ no lugar de _UserPrincipalName_ para especificar um UPN diferente ao restaurar a conta de usuário.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Usar o módulo PowerShell do Azure Active Directory V2 para remover uma conta de usuário
<a name="ShortVersion"> </a>

Para usar o cmdlet **Remove-AzureADUser** no módulo PowerShell do Azure Active Directory V2, conecte-se primeiro à sua assinatura. Confira as instruções em [Conectar-se com o módulo PowerShell do Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Após a conexão, use a seguinte sintaxe para remover uma conta de usuário individual:
  
```
Remove-AzureADUser -ObjectID <Account>
```

Este exemplo remove a conta de usuário ricardoc@litwareinc.com.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> O parâmetro **-ObjectID** no cmdlet **Remove-AzureAD** aceita o nome da conta, também conhecido como o nome UPN, ou a ID de objeto da conta.
  
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

Para remover uma conta com base no nome do usuário, use os seguintes comandos:
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>Veja também
<a name="SeeAlso"> </a>

Confira estes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Criar contas de usuários usando o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Bloquear contas de usuários com o Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Atribuir licenças a contas de usuários usando o Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Remover licenças de contas de usuários com o Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

