---
title: "Bloquear contas de usuários com o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Explica como usar o Office 365 PowerShell para bloquear e desbloquear o acesso às contas do Office 365."
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquear contas de usuários com o Office 365 PowerShell

**Resumo:**  Explica como usar o Office 365 PowerShell para bloquear e desbloquear o acesso às contas do Office 365.
  
Bloqueando o acesso a uma conta do Office 365 impede que qualquer pessoa usando a conta para entrar e acessar os serviços e os dados em sua organização do Office 365. Quando você bloqueia o acesso à conta, o usuário recebe a seguinte mensagem de erro quando tentarem entrar:
  
![Conta bloqueada do Office 365.](images/o365_powershell_account_blocked.png)
  
Você pode usar o Office 365 PowerShell para bloquear o acesso individuais e várias contas de usuário.
  
## <a name="before-you-begin"></a>Antes de começar

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Quando você bloquear uma conta de usuário, ela pode levar desde que 24 horas, entre em vigor em clientes e dispositivos de todos os usuários.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Usar o Office 365 PowerShell para bloquear o acesso a contas de usuário individuais

Use a seguinte sintaxe para bloquear o acesso a uma conta de usuário individual:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Para desbloquear a conta do usuário, execute o seguinte comando:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>Use o Office 365 PowerShell para bloquear o acesso a várias contas de usuário

Primeiro, crie um arquivo de texto que contém uma conta em cada linha semelhante a esta:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
Nos comandos a seguir, o arquivo de texto de exemplo é C:\My Documents\Accounts.txt. Substitua pelo caminho e o nome do seu arquivo de texto.
    
Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>Usar o módulo PowerShell do Azure Active Directory V2 para bloquear o acesso a contas de usuário

Para usar o cmdlet **New-AzureADUser** no módulo PowerShell do Azure Active Directory V2, você deve primeiro conectar-se à sua assinatura. Para conhecer as instruções, confira[Conectar-se com o módulo PowerShell do Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Após a conexão, use a seguinte sintaxe para bloquear uma conta de usuário individual:
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> O parâmetro -ObjectID no cmdlet Set-AzureAD aceita o nome da conta, também conhecido como o nome UPN, ou a ID de objeto da conta. 
  
Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Para desbloquear essa conta de usuário, execute o seguinte comando:
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Para exibir a conta de usuário que UPN com base no nome para exibição do usuário, use os seguintes comandos:
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Este exemplo exibe a conta de usuário para o usuário chamado Caleb Sills UPN.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para bloquear uma conta com base no nome do usuário, use os seguintes comandos:
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

Para bloquear o acesso a várias contas de usuário, crie um arquivo de texto que contém um nome de conta em cada linha semelhante a esta:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Nos comandos a seguir, o arquivo de texto de exemplo é C:\My Documents\Accounts.txt. Substitua pelo caminho e o nome do seu arquivo de texto.
    
Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a>Veja também
<a name="SeeAlso"> </a>

Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Criar contas de usuários usando o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Atribuir licenças a contas de usuários usando o PowerShell do Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Remover licenças de contas de usuários com o Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [Set-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

