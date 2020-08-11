---
title: Bloquear contas de usuário do Microsoft 365 com o PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- seo-marvel-apr2020
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Este artigo explica como usar o PowerShell para bloquear e desbloquear o acesso às contas do Microsoft 365.
ms.openlocfilehash: 1d32554642f29b4548e2525135d20967ba6b0f16
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606427"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="a24d7-103">Bloquear contas de usuário do Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="a24d7-103">Block Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="a24d7-104">*Este artigo se aplica tanto ao Microsoft 365 Enterprise quanto ao Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="a24d7-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="a24d7-105">Bloquear o acesso a uma conta do Microsoft 365 impede que qualquer pessoa use a conta para entrar e acessar os serviços e dados na sua organização do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a24d7-105">Blocking access to a Microsoft 365 account prevents anyone from using the account to sign in and access the services and data in your Microsoft 365 organization.</span></span> <span data-ttu-id="a24d7-106">Você pode usar o PowerShell para bloquear o acesso a contas de usuário individuais e múltiplas.</span><span class="sxs-lookup"><span data-stu-id="a24d7-106">You can use PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a24d7-107">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="a24d7-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a24d7-108">Primeiro, [Conecte-se ao seu locatário do Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="a24d7-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="a24d7-109">Bloquear o acesso a contas de usuário individuais</span><span class="sxs-lookup"><span data-stu-id="a24d7-109">Block access to individual user accounts</span></span>

<span data-ttu-id="a24d7-110">Use a seguinte sintaxe para bloquear uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="a24d7-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="a24d7-111">O parâmetro-ObjectID no cmdlet Set-AzureAD aceita o nome de entrada da conta, também conhecido como o nome principal do usuário ou a ID de objeto da conta.</span><span class="sxs-lookup"><span data-stu-id="a24d7-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="a24d7-112">Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="a24d7-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="a24d7-113">Para desbloquear essa conta de usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a24d7-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="a24d7-114">Para exibir o UPN da conta de usuário com base no nome de exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="a24d7-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="a24d7-115">Este exemplo exibe o UPN da conta de usuário para o usuário chamado Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="a24d7-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a24d7-116">Para bloquear uma conta com base no nome de exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="a24d7-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="a24d7-117">A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a24d7-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="a24d7-118">Bloquear o acesso a várias contas de usuário</span><span class="sxs-lookup"><span data-stu-id="a24d7-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="a24d7-119">Para bloquear o acesso a várias contas de usuário, crie um arquivo de texto que contenha um nome de logon de conta em cada linha como esta:</span><span class="sxs-lookup"><span data-stu-id="a24d7-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="a24d7-120">Nos seguintes comandos, o arquivo de texto de exemplo é C:\Meus Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="a24d7-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="a24d7-121">Substitua isso pelo caminho e nome de arquivo do arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="a24d7-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="a24d7-122">Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a24d7-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="a24d7-123">Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a24d7-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a24d7-124">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a24d7-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a24d7-125">Primeiro, [Conecte-se ao seu locatário do Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="a24d7-125">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="a24d7-126">Bloquear o acesso a contas de usuário individuais</span><span class="sxs-lookup"><span data-stu-id="a24d7-126">Block access to individual user accounts</span></span>

<span data-ttu-id="a24d7-127">Use a seguinte sintaxe para bloquear o acesso a uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="a24d7-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="a24d7-128">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="a24d7-128">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="a24d7-129">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a24d7-129">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="a24d7-130">Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="a24d7-130">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="a24d7-131">Para desbloquear a conta do usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a24d7-131">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="a24d7-132">A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a24d7-132">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="a24d7-133">Bloquear o acesso a várias contas de usuário</span><span class="sxs-lookup"><span data-stu-id="a24d7-133">Block access to multiple user accounts</span></span>

<span data-ttu-id="a24d7-134">Primeiro, crie um arquivo de texto que contenha uma conta em cada linha como esta:</span><span class="sxs-lookup"><span data-stu-id="a24d7-134">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="a24d7-135">Nos seguintes comandos, o arquivo de texto de exemplo é C:\Meus Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="a24d7-135">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="a24d7-136">Substitua isso pelo caminho e nome de arquivo do arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="a24d7-136">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="a24d7-137">Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a24d7-137">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="a24d7-138">Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a24d7-138">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="a24d7-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="a24d7-139">See also</span></span>

[<span data-ttu-id="a24d7-140">Gerenciar contas de usuário, licenças e grupos do Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="a24d7-140">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a24d7-141">Gerenciar o Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="a24d7-141">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a24d7-142">Introdução ao PowerShell para o Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a24d7-142">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
