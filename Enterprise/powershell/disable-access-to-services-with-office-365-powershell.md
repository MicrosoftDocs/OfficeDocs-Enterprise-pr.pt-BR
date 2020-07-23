---
title: Desabilitar o acesso aos serviços do Microsoft 365 com o PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Use o PowerShell para desabilitar o acesso aos serviços do Microsoft 365 para usuários.
ms.openlocfilehash: 4e7c59447dae027dffa7fd5ea24d1818d5d64a9a
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230676"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a><span data-ttu-id="1e816-103">Desabilitar o acesso aos serviços do Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e816-103">Disable access to Microsoft 365 services with PowerShell</span></span>

<span data-ttu-id="1e816-104">*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="1e816-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1e816-105">Quando uma conta da Microsoft 365 é atribuída a uma licença de um plano de licenciamento, os serviços de 365 da Microsoft são disponibilizados para o usuário por essa licença.</span><span class="sxs-lookup"><span data-stu-id="1e816-105">When a Microsoft 365 account is assigned a license from a licensing plan, Microsoft 365 services are made available to the user from that license.</span></span> <span data-ttu-id="1e816-106">No entanto, você pode controlar os serviços do Microsoft 365 que o usuário pode acessar.</span><span class="sxs-lookup"><span data-stu-id="1e816-106">However, you can control the Microsoft 365 services that the user can access.</span></span> <span data-ttu-id="1e816-107">Por exemplo, mesmo que a licença permita acesso ao serviço do SharePoint Online, você pode desabilitar o acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="1e816-107">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="1e816-108">Você pode usar o PowerShell para desabilitar o acesso a qualquer número de serviços para um plano de licenciamento específico para:</span><span class="sxs-lookup"><span data-stu-id="1e816-108">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="1e816-109">Uma conta individual</span><span class="sxs-lookup"><span data-stu-id="1e816-109">An individual account.</span></span>
- <span data-ttu-id="1e816-110">Um grupo de contas.</span><span class="sxs-lookup"><span data-stu-id="1e816-110">A group of accounts.</span></span>
- <span data-ttu-id="1e816-111">Todas as contas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="1e816-111">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="1e816-112">Há dependências de serviço do Microsoft 365 que podem impedir você de desabilitar um serviço especificado quando outros serviços dependem dele.</span><span class="sxs-lookup"><span data-stu-id="1e816-112">There are Microsoft 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1e816-113">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e816-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1e816-114">Primeiro, [Conecte-se ao seu locatário do Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1e816-114">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="1e816-115">Em seguida, use este comando para exibir seus planos de licenciamento disponíveis, também conhecidos como AccountSkuIds:</span><span class="sxs-lookup"><span data-stu-id="1e816-115">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="1e816-116">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="1e816-116">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="1e816-117">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e816-117">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="1e816-118">Para obter mais informações, consulte [Exibir licenças e serviços com o PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1e816-118">For more information, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="1e816-119">Para ver os resultados anteriores e posteriores dos procedimentos neste tópico, consulte [Exibir licença de conta e detalhes do serviço com o PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1e816-119">To see the before and after results of the procedures in this topic, see [View account license and service details with PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="1e816-120">Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="1e816-120">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="1e816-121">Especificamente, o script permite que você exiba e desabilite serviços na sua organização do Microsoft 365, incluindo Sway.</span><span class="sxs-lookup"><span data-stu-id="1e816-121">Specifically, the script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="1e816-122">Confira mais informações em [desabilitar o acesso ao Sway com o PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1e816-122">For more information, see [Disable access to Sway with PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="1e816-123">Desabilitar serviços específicos da Microsoft 365 para usuários específicos para um plano de licenciamento específico</span><span class="sxs-lookup"><span data-stu-id="1e816-123">Disable specific Microsoft 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="1e816-124">Para desabilitar um conjunto específico de serviços do Microsoft 365 para os usuários para um plano de licenciamento específico, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="1e816-124">To disable a specific set of Microsoft 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="1e816-125">Etapa 1: identificar os serviços indesejáveis no plano de licenciamento usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="1e816-125">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="1e816-126">O exemplo a seguir cria um objeto **licenseoptions** que desabilita os serviços do Office e do SharePoint Online no plano de licenciamento chamado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="1e816-126">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="1e816-127">Etapa 2: usar o objeto **licenseoptions** da etapa 1 em um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="1e816-127">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="1e816-128">Para criar uma nova conta que tem serviços desabilitados, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="1e816-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="1e816-129">O exemplo a seguir cria uma nova conta para o Leonor Marques que atribui a licença e desabilita os serviços descritos na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="1e816-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="1e816-130">Para obter mais informações sobre a criação de contas de usuário no PowerShell para o Microsoft 365, consulte [Create User Accounts with PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1e816-130">For more information about creating user accounts in PowerShell for Microsoft 365, see [Create user accounts with PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="1e816-131">Para desabilitar os serviços de um usuário licenciado existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="1e816-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="1e816-132">Este exemplo desabilita os serviços do usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="1e816-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="1e816-133">Para desabilitar os serviços descritos na etapa 1 para todos os usuários licenciados existentes, especifique o nome do seu plano do Microsoft 365 na exibição do cmdlet **Get-MsolAccountSku** (como **litwareinc: ENTERPRISEPACK**) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="1e816-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Microsoft 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="1e816-134">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_ , somente as primeiras 500 contas de usuário serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="1e816-134">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="1e816-135">Para desabilitar os serviços para um grupo de usuários existentes, use um dos seguintes métodos para identificar os usuários:</span><span class="sxs-lookup"><span data-stu-id="1e816-135">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="1e816-136">**Método 1. Filtrar as contas com base em um atributo de conta existente**</span><span class="sxs-lookup"><span data-stu-id="1e816-136">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="1e816-137">Para isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="1e816-137">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="1e816-138">O exemplo a seguir desabilita os serviços para usuários no departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="1e816-138">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="1e816-139">**Método 2: usar uma lista de contas específicas**</span><span class="sxs-lookup"><span data-stu-id="1e816-139">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="1e816-140">Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="1e816-140">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="1e816-141">Crie um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1e816-141">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="1e816-142">Neste exemplo, o arquivo de texto é C: \\ meus documentos \\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="1e816-142">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="1e816-143">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="1e816-143">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="1e816-144">Se você quiser desabilitar o acesso aos serviços para vários planos de licenciamento, repita as instruções acima para cada plano de licenciamento, assegurando que:</span><span class="sxs-lookup"><span data-stu-id="1e816-144">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="1e816-145">O plano de licenciamento foi atribuído às contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="1e816-145">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="1e816-146">Os serviços a serem desabilitados estão disponíveis no plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="1e816-146">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="1e816-147">Para desabilitar os serviços do Microsoft 365 para os usuários enquanto você os atribui a um plano de licenciamento, confira [desabilitar o acesso aos serviços ao atribuir licenças de usuário](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="1e816-147">To disable Microsoft 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="1e816-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="1e816-148">See also</span></span>

[<span data-ttu-id="1e816-149">Gerenciar contas de usuário, licenças e grupos do Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e816-149">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1e816-150">Gerenciar o Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e816-150">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1e816-151">Introdução ao PowerShell para o Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1e816-151">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
