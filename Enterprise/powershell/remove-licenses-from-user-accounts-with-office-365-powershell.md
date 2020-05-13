---
title: Remover licenças de contas de usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explica como usar o Office 365 PowerShell para remover as licenças do Office 365 que foram previamente atribuídas aos usuários.
ms.openlocfilehash: 4a99fb115b7c3241beb2cb3b0dd83666622747d5
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208752"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e5aa6-103">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5aa6-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e5aa6-104">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="e5aa6-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e5aa6-105">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e5aa6-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="e5aa6-106">Em seguida, liste os planos de licença para seu locatário com este comando.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="e5aa6-107">Em seguida, obtenha o nome de entrada da conta para a qual você deseja remover uma licença, também conhecido como o nome de usuário principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="e5aa6-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="e5aa6-108">Por fim, especifique os nomes de entrada e de plano de licença do usuário, remova os caracteres "<" e ">" e execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e5aa6-109">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-109">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e5aa6-110">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e5aa6-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="e5aa6-111">Para exibir as informações do plano de licenciamento (**AccountSkuID**) em sua organização, confira os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="e5aa6-111">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="e5aa6-112">Exibir licenças e serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="e5aa6-112">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="e5aa6-113">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5aa6-113">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="e5aa6-114">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-114">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="e5aa6-115">Removendo licenças de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="e5aa6-115">Removing licenses from user accounts</span></span>

<span data-ttu-id="e5aa6-116">Para remover licenças de uma conta de usuário existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e5aa6-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="e5aa6-117">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e5aa6-118">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="e5aa6-119">Este exemplo remove a licença **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) da conta de usuário BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-119">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="e5aa6-120">Você não pode usar o `Set-MsolUserLicense` cmdlet para cancelar a atribuição de usuários de licenças *canceladas* .</span><span class="sxs-lookup"><span data-stu-id="e5aa6-120">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="e5aa6-121">Você deve fazer isso individualmente para cada conta de usuário no centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-121">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="e5aa6-122">Para remover todas as licenças de um grupo de usuários licenciados existentes, use um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="e5aa6-122">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="e5aa6-123">**Filtrar as contas com base em um atributo de conta existente** Para fazer isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e5aa6-123">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="e5aa6-124">Este exemplo remove todas as licenças de todas as contas de usuário no departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-124">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="e5aa6-125">**Usar uma lista de contas específicas para uma licença específica** Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="e5aa6-125">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="e5aa6-126">Crie e salve um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="e5aa6-126">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="e5aa6-127">Use a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="e5aa6-127">Use the following syntax:</span></span>
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId>" }
  ```

<span data-ttu-id="e5aa6-128">Este exemplo remove a licença **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) das contas de usuário definidas no arquivo de texto c:\Meus Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-128">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="e5aa6-129">Para remover todas as licenças de todas as contas de usuário existentes, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e5aa6-129">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="e5aa6-130">Outra maneira de liberar uma licença é excluir a conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="e5aa6-130">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="e5aa6-131">Para obter mais informações, consulte [excluir e restaurar contas de usuário com o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e5aa6-131">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e5aa6-132">Também consulte</span><span class="sxs-lookup"><span data-stu-id="e5aa6-132">See also</span></span>

[<span data-ttu-id="e5aa6-133">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5aa6-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e5aa6-134">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5aa6-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e5aa6-135">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5aa6-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

