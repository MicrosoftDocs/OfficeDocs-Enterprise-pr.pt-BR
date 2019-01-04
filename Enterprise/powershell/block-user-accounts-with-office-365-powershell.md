---
title: Bloquear contas de usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Explica como usar o Office 365 PowerShell para bloquear e desbloquear o acesso às contas do Office 365.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546472"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquear contas de usuários com o Office 365 PowerShell

**Resumo:**  Explica como usar o Office 365 PowerShell para bloquear e desbloquear o acesso às contas do Office 365.
  
Bloqueando o acesso a uma conta do Office 365 impede que qualquer pessoa usando a conta para entrar e acessar os serviços e os dados em sua organização do Office 365. Você pode usar o Office 365 PowerShell para bloquear o acesso individuais e várias contas de usuário.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo de gráfico

Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Bloquear o acesso às contas de usuário individual

Use a seguinte sintaxe para bloquear uma conta de usuário individual:
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> O parâmetro - ObjectID no cmdlet Set-AzureAD aceita qualquer nome da conta entrar, também conhecido como o nome Principal de usuário ou a ID do objeto. da conta 
  
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
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Este exemplo exibe a conta de usuário para o usuário chamado Caleb Sills UPN.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para bloquear uma conta com base no nome de exibição do usuário, use os seguintes comandos:
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquear o acesso a várias contas de usuário

Para bloquear o acesso a várias contas de usuário, crie um arquivo de texto que contém uma entrada nome da conta em cada linha semelhante a esta:
    
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o módulo do Microsoft Azure Active Directory para o Windows PowerShell

Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

    
### <a name="block-access-to-individual-user-accounts"></a>Bloquear o acesso às contas de usuário individual

Use a seguinte sintaxe para bloquear o acesso a uma conta de usuário individual:
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Para desbloquear a conta do usuário, execute o seguinte comando:
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquear o acesso a várias contas de usuário

Primeiro, crie um arquivo de texto que contém uma conta em cada linha semelhante a esta:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
Nos comandos a seguir, o arquivo de texto de exemplo é C:\My Documents\Accounts.txt. Substitua pelo caminho e o nome do seu arquivo de texto.
    
Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Veja também

[Gerenciar contas de usuário e licenças usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
