---
title: Bloquear contas de usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Explica como usar o Office 365 PowerShell para bloquear e desbloquear o acesso às contas do Office 365.
ms.openlocfilehash: 5633c35feee67ede65c4fffa8bc55276c3b979b8
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004724"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquear contas de usuários com o Office 365 PowerShell

Bloquear o acesso a uma conta do Office 365 impede que qualquer pessoa use a conta para entrar e acessar os serviços e dados na sua organização do Office 365. Você pode usar o Office 365 PowerShell para bloquear o acesso a contas de usuário individuais e múltiplas.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Bloquear o acesso a contas de usuário individuais

Use a seguinte sintaxe para bloquear uma conta de usuário individual:
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> O parâmetro-ObjectID no cmdlet Set-AzureAD aceita o nome de entrada da conta, também conhecido como o nome principal do usuário ou a ID de objeto da conta. 
  
Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Para desbloquear essa conta de usuário, execute o seguinte comando:
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Para exibir o UPN da conta de usuário com base no nome de exibição do usuário, use os seguintes comandos:
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Este exemplo exibe o UPN da conta de usuário para o usuário chamado Carlos Lima.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para bloquear uma conta com base no nome de exibição do usuário, use os seguintes comandos:
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquear o acesso a várias contas de usuário

Para bloquear o acesso a várias contas de usuário, crie um arquivo de texto que contenha um nome de logon de conta em cada linha como esta:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Nos seguintes comandos, o arquivo de texto de exemplo é C:\Meus Documents\Accounts.txt. Substitua isso pelo caminho e nome de arquivo do arquivo de texto.
  
Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
### <a name="block-access-to-individual-user-accounts"></a>Bloquear o acesso a contas de usuário individuais

Use a seguinte sintaxe para bloquear o acesso a uma conta de usuário individual:
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome. Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.
>

Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Para desbloquear a conta do usuário, execute o seguinte comando:
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquear o acesso a várias contas de usuário

Primeiro, crie um arquivo de texto que contenha uma conta em cada linha como esta:
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

Nos seguintes comandos, o arquivo de texto de exemplo é C:\Meus Documents\Accounts.txt. Substitua isso pelo caminho e nome de arquivo do arquivo de texto.
    
Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Veja também

[Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
