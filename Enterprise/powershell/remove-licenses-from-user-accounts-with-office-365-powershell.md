---
title: Remover licenças de contas de usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explica como usar o Office 365 PowerShell para remover as licenças do Office 365 que foram previamente atribuídas aos usuários.
ms.openlocfilehash: ce529221c18e5f094b9d45037e95b859eeaea5a0
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844182"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="6c64f-103">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c64f-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="6c64f-104">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="6c64f-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="6c64f-105">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="6c64f-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="6c64f-106">Em seguida, liste os planos de licença para seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="6c64f-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="6c64f-107">Em seguida, obtenha o nome de entrada da conta para a qual você deseja remover uma licença, também conhecido como o nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="6c64f-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="6c64f-108">Por fim, especifique os nomes de entrada e de plano de licença do usuário, remova os caracteres "<" e ">" e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="6c64f-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="6c64f-109">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c64f-109">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="6c64f-110">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="6c64f-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="6c64f-111">Para exibir as informações do plano de licenciamento (**AccountSkuID** ) em sua organização, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="6c64f-111">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="6c64f-112">Exibir licenças e serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="6c64f-112">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="6c64f-113">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c64f-113">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="6c64f-114">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="6c64f-114">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="6c64f-115">Removendo licenças de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="6c64f-115">Removing licenses from user accounts</span></span>

<span data-ttu-id="6c64f-116">Para remover licenças de uma conta de usuário existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="6c64f-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="6c64f-117">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="6c64f-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="6c64f-118">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c64f-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="6c64f-119">Este exemplo remove a licença **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) da conta de usuário BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="6c64f-119">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="6c64f-120">Você não pode usar `Set-MsolUserLicense` o cmdlet para cancelar a atribuição de usuários de licenças *canceladas* .</span><span class="sxs-lookup"><span data-stu-id="6c64f-120">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="6c64f-121">Você deve fazer isso individualmente para cada conta de usuário no centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="6c64f-121">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="6c64f-122">Para remover licenças de um grupo de usuários licenciados existentes, use um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="6c64f-122">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="6c64f-123">**Filtrar as contas com base em um atributo de conta existente** Para fazer isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="6c64f-123">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="6c64f-124">Este exemplo remove as licenças **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de todas as contas de usuários no departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="6c64f-124">This example removes the  **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="6c64f-125">**Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="6c64f-125">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="6c64f-126">Crie e salve um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="6c64f-126">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="6c64f-127">Use a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="6c64f-127">Use the following syntax:</span></span>
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

<span data-ttu-id="6c64f-128">Este exemplo remove a licença **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) das contas de usuário definidas no arquivo de texto c:\Meus Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="6c64f-128">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="6c64f-129">Para remover licenças de todas as contas de usuário existentes, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="6c64f-129">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="6c64f-130">Este exemplo remove a licença **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de todas as contas de usuário licenciado existentes.</span><span class="sxs-lookup"><span data-stu-id="6c64f-130">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="6c64f-131">Outra maneira de liberar uma licença é excluir a conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="6c64f-131">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="6c64f-132">Para obter mais informações, consulte [excluir e restaurar contas de usuário com o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6c64f-132">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6c64f-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c64f-133">See also</span></span>

[<span data-ttu-id="6c64f-134">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c64f-134">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="6c64f-135">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c64f-135">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6c64f-136">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c64f-136">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

