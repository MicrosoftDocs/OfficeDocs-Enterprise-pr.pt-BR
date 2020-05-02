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
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="4b7ee-103">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b7ee-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="4b7ee-104">Bloquear o acesso a uma conta do Office 365 impede que qualquer pessoa use a conta para entrar e acessar os serviços e dados na sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-104">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="4b7ee-105">Você pode usar o Office 365 PowerShell para bloquear o acesso a contas de usuário individuais e múltiplas.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-105">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="4b7ee-106">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="4b7ee-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="4b7ee-107">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="4b7ee-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="4b7ee-108">Bloquear o acesso a contas de usuário individuais</span><span class="sxs-lookup"><span data-stu-id="4b7ee-108">Block access to individual user accounts</span></span>

<span data-ttu-id="4b7ee-109">Use a seguinte sintaxe para bloquear uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-109">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="4b7ee-110">O parâmetro-ObjectID no cmdlet Set-AzureAD aceita o nome de entrada da conta, também conhecido como o nome principal do usuário ou a ID de objeto da conta.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-110">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="4b7ee-111">Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-111">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="4b7ee-112">Para desbloquear essa conta de usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-112">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="4b7ee-113">Para exibir o UPN da conta de usuário com base no nome de exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-113">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="4b7ee-114">Este exemplo exibe o UPN da conta de usuário para o usuário chamado Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-114">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="4b7ee-115">Para bloquear uma conta com base no nome de exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-115">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="4b7ee-116">A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-116">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="4b7ee-117">Bloquear o acesso a várias contas de usuário</span><span class="sxs-lookup"><span data-stu-id="4b7ee-117">Block access to multiple user accounts</span></span>

<span data-ttu-id="4b7ee-118">Para bloquear o acesso a várias contas de usuário, crie um arquivo de texto que contenha um nome de logon de conta em cada linha como esta:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-118">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="4b7ee-119">Nos seguintes comandos, o arquivo de texto de exemplo é C:\Meus Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-119">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="4b7ee-120">Substitua isso pelo caminho e nome de arquivo do arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-120">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="4b7ee-121">Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-121">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="4b7ee-122">Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-122">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="4b7ee-123">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-123">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="4b7ee-124">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="4b7ee-124">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="4b7ee-125">Bloquear o acesso a contas de usuário individuais</span><span class="sxs-lookup"><span data-stu-id="4b7ee-125">Block access to individual user accounts</span></span>

<span data-ttu-id="4b7ee-126">Use a seguinte sintaxe para bloquear o acesso a uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-126">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="4b7ee-127">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-127">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="4b7ee-128">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-128">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="4b7ee-129">Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="4b7ee-130">Para desbloquear a conta do usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-130">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="4b7ee-131">A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-131">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="4b7ee-132">Bloquear o acesso a várias contas de usuário</span><span class="sxs-lookup"><span data-stu-id="4b7ee-132">Block access to multiple user accounts</span></span>

<span data-ttu-id="4b7ee-133">Primeiro, crie um arquivo de texto que contenha uma conta em cada linha como esta:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-133">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="4b7ee-134">Nos seguintes comandos, o arquivo de texto de exemplo é C:\Meus Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-134">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="4b7ee-135">Substitua isso pelo caminho e nome de arquivo do arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="4b7ee-135">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="4b7ee-136">Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-136">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="4b7ee-137">Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4b7ee-137">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="4b7ee-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="4b7ee-138">See also</span></span>

[<span data-ttu-id="4b7ee-139">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b7ee-139">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="4b7ee-140">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b7ee-140">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4b7ee-141">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b7ee-141">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
