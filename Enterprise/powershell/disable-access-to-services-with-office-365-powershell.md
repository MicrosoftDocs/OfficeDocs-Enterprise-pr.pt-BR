---
title: Desabilitar o acesso aos serviços com o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Use o Office 365 PowerShell para desabilitar o acesso aos serviços do Office 365 para os usuários.
ms.openlocfilehash: 711f48dd2caad6fc2b438010405b126be203bd54
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257596"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="8fc0b-103">Desabilitar o acesso aos serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc0b-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="8fc0b-104">Quando uma conta do Office 365 recebe uma licença de um plano de licenciamento, os serviços do Office 365 são disponibilizados para o usuário dessa licença.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="8fc0b-105">No entanto, você pode controlar os serviços do Office 365 que o usuário pode acessar.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="8fc0b-106">Por exemplo, mesmo que a licença permita acesso ao serviço do SharePoint Online, você pode desabilitar o acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="8fc0b-107">Você pode usar o PowerShell para desabilitar o acesso a qualquer número de serviços para um plano de licenciamento específico para:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="8fc0b-108">Uma conta individual</span><span class="sxs-lookup"><span data-stu-id="8fc0b-108">An individual account.</span></span>
    
- <span data-ttu-id="8fc0b-109">Um grupo de contas.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-109">A group of accounts.</span></span>
    
- <span data-ttu-id="8fc0b-110">Todas as contas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-110">All accounts in your organization.</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8fc0b-111">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8fc0b-112">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8fc0b-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="8fc0b-113">Em seguida, use este comando para exibir seus planos de licenciamento disponíveis, também conhecidos como AccountSkuIds:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-113">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="8fc0b-114">O PowerShell Core não é compatível com o módulo Microsoft Azure Active Directory para o módulo e cmdlets do Windows PowerShell com o **MSol** em seu nome.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-114">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8fc0b-115">Para continuar usando esses cmdlets, você deve executá-los do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-115">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="8fc0b-116">Para obter mais informações, consulte [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8fc0b-116">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="8fc0b-117">Para ver os resultados anteriores e posteriores dos procedimentos neste tópico, consulte [Exibir licença de conta e detalhes do serviço com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8fc0b-117">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="8fc0b-118">Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-118">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="8fc0b-119">Especificamente, o script permite que você exiba e desabilite serviços na sua organização do Office 365, incluindo Sway.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-119">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="8fc0b-120">Para saber mais, confira [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8fc0b-120">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="8fc0b-121">Desabilitar serviços específicos do Office 365 para usuários específicos para um plano de licenciamento específico</span><span class="sxs-lookup"><span data-stu-id="8fc0b-121">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="8fc0b-122">Para desabilitar um conjunto específico de serviços do Office 365 para os usuários para um plano de licenciamento específico, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-122">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="8fc0b-123">Identifique os serviços indesejáveis no plano de licenciamento usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-123">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="8fc0b-124">O exemplo a seguir cria um objeto **licenseoptions** que desabilita os serviços do Office e do SharePoint Online no plano de licenciamento chamado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="8fc0b-124">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="8fc0b-125">Use o objeto **LicenseOptions** da Etapa 1 em um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-125">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="8fc0b-126">Para criar uma nova conta que tem serviços desabilitados, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-126">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```powershell
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="8fc0b-127">O exemplo a seguir cria uma nova conta para o Leonor Marques que atribui a licença e desabilita os serviços descritos na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-127">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```powershell
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="8fc0b-128">Para obter mais informações sobre a criação de contas de usuário no Office 365 PowerShell, consulte [Create User Accounts with office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8fc0b-128">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="8fc0b-129">Para desabilitar os serviços de um usuário licenciado existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-129">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="8fc0b-130">Este exemplo desabilita os serviços do usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-130">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="8fc0b-131">Para desabilitar os serviços descritos na etapa 1 para todos os usuários licenciados existentes, especifique o nome do seu plano do Office 365 na exibição do cmdlet **Get-MsolAccountSku** (como **litwareinc: ENTERPRISEPACK**) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-131">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```powershell
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="8fc0b-132">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_ , somente as primeiras 500 contas de usuário serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-132">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>


  - <span data-ttu-id="8fc0b-133">Para desabilitar os serviços para um grupo de usuários existentes, use um dos seguintes métodos para identificar os usuários:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-133">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="8fc0b-134">**Filtrar as contas com base em um atributo de conta existente** Para fazer isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-134">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```powershell
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="8fc0b-135">O exemplo a seguir desabilita os serviços para usuários no departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-135">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```powershell
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="8fc0b-136">**Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-136">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="8fc0b-137">Crie um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-137">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="8fc0b-138">Neste exemplo, o arquivo de texto é C:\\meus documentos\\accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-138">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="8fc0b-139">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-139">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="8fc0b-140">Se você quiser desabilitar o acesso aos serviços para vários planos de licenciamento, repita as instruções acima para cada plano de licenciamento, assegurando que:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-140">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="8fc0b-141">O plano de licenciamento foi atribuído às contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-141">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="8fc0b-142">Os serviços a serem desabilitados estão disponíveis no plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="8fc0b-142">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="8fc0b-143">Para desabilitar os serviços do Office 365 para usuários enquanto você estiver atribuindo-os a um plano de licenciamento, confira [desabilitar o acesso aos serviços ao atribuir licenças de usuário](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="8fc0b-143">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="8fc0b-144">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="8fc0b-144">New to Office 365?</span></span>
<span data-ttu-id="8fc0b-145"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="8fc0b-145"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="8fc0b-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="8fc0b-146">See also</span></span>
<span data-ttu-id="8fc0b-147"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="8fc0b-147"></span></span>

<span data-ttu-id="8fc0b-148">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8fc0b-148">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="8fc0b-149">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fc0b-149">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8fc0b-150">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fc0b-150">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8fc0b-151">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fc0b-151">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8fc0b-152">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc0b-152">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8fc0b-153">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fc0b-153">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
