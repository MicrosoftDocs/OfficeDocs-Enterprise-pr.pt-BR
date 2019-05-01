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
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491387"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="102b9-103">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="102b9-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="102b9-104">**Resumo:**  Explica como usar o Office 365 PowerShell para bloquear e desbloquear o acesso às contas do Office 365.</span><span class="sxs-lookup"><span data-stu-id="102b9-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="102b9-105">Bloquear o acesso a uma conta do Office 365 impede que qualquer pessoa use a conta para entrar e acessar os serviços e dados na sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="102b9-105">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="102b9-106">Você pode usar o Office 365 PowerShell para bloquear o acesso a contas de usuário individuais e múltiplas.</span><span class="sxs-lookup"><span data-stu-id="102b9-106">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="102b9-107">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="102b9-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="102b9-108">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="102b9-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="102b9-109">Bloquear o acesso a contas de usuário individuais</span><span class="sxs-lookup"><span data-stu-id="102b9-109">Block access to individual user accounts</span></span>

<span data-ttu-id="102b9-110">Use a seguinte sintaxe para bloquear uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="102b9-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="102b9-111">O parâmetro-ObjectID no cmdlet Set-AzureAD aceita o nome de entrada da conta, também conhecido como o nome principal do usuário ou a ID de objeto da conta.</span><span class="sxs-lookup"><span data-stu-id="102b9-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="102b9-112">Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="102b9-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="102b9-113">Para desbloquear essa conta de usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="102b9-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="102b9-114">Para exibir o UPN da conta de usuário com base no nome de exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="102b9-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="102b9-115">Este exemplo exibe o UPN da conta de usuário para o usuário chamado Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="102b9-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="102b9-116">Para bloquear uma conta com base no nome de exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="102b9-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="102b9-117">A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="102b9-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="102b9-118">Bloquear o acesso a várias contas de usuário</span><span class="sxs-lookup"><span data-stu-id="102b9-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="102b9-119">Para bloquear o acesso a várias contas de usuário, crie um arquivo de texto que contenha um nome de logon de conta em cada linha como esta:</span><span class="sxs-lookup"><span data-stu-id="102b9-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="102b9-120">Nos seguintes comandos, o arquivo de texto de exemplo é C:\Meus Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="102b9-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="102b9-121">Substitua isso pelo caminho e nome de arquivo do arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="102b9-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="102b9-122">Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="102b9-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="102b9-123">Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="102b9-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="102b9-124">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="102b9-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="102b9-125">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="102b9-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="102b9-126">Bloquear o acesso a contas de usuário individuais</span><span class="sxs-lookup"><span data-stu-id="102b9-126">Block access to individual user accounts</span></span>

<span data-ttu-id="102b9-127">Use a seguinte sintaxe para bloquear o acesso a uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="102b9-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="102b9-128">Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="102b9-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="102b9-129">Para desbloquear a conta do usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="102b9-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="102b9-130">A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="102b9-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="102b9-131">Bloquear o acesso a várias contas de usuário</span><span class="sxs-lookup"><span data-stu-id="102b9-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="102b9-132">Primeiro, crie um arquivo de texto que contenha uma conta em cada linha como esta:</span><span class="sxs-lookup"><span data-stu-id="102b9-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="102b9-133">Nos seguintes comandos, o arquivo de texto de exemplo é C:\Meus Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="102b9-133">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="102b9-134">Substitua isso pelo caminho e nome de arquivo do arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="102b9-134">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="102b9-135">Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="102b9-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="102b9-136">Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="102b9-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="102b9-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="102b9-137">See also</span></span>

[<span data-ttu-id="102b9-138">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="102b9-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="102b9-139">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="102b9-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="102b9-140">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="102b9-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
