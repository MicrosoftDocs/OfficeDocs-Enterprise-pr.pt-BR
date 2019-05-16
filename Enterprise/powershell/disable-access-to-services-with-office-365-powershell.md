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
ms.openlocfilehash: bd6961f0de52d95026bae3a743613b33a4af918b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069027"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="80653-103">Desabilitar o acesso aos serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="80653-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="80653-104">**Resumo:** Explica como usar o Office 365 PowerShell para desabilitar o acesso aos serviços do Office 365 para usuários em sua organização.</span><span class="sxs-lookup"><span data-stu-id="80653-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="80653-105">Quando uma conta do Office 365 recebe uma licença de um plano de licenciamento, os serviços do Office 365 são disponibilizados para o usuário dessa licença.</span><span class="sxs-lookup"><span data-stu-id="80653-105">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="80653-106">No entanto, você pode controlar os serviços do Office 365 que o usuário pode acessar.</span><span class="sxs-lookup"><span data-stu-id="80653-106">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="80653-107">Por exemplo, mesmo que a licença permita acesso ao serviço do SharePoint Online, você pode desabilitar o acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="80653-107">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="80653-108">Você pode usar o PowerShell para desabilitar o acesso a qualquer número de serviços para um plano de licenciamento específico para:</span><span class="sxs-lookup"><span data-stu-id="80653-108">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="80653-109">Uma conta individual</span><span class="sxs-lookup"><span data-stu-id="80653-109">An individual account.</span></span>
    
- <span data-ttu-id="80653-110">Um grupo de contas.</span><span class="sxs-lookup"><span data-stu-id="80653-110">A group of accounts.</span></span>
    
- <span data-ttu-id="80653-111">Todas as contas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="80653-111">All accounts in your organization.</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="80653-112">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80653-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="80653-113">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="80653-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="80653-114">Em seguida, use este comando para exibir seus planos de licenciamento disponíveis, também conhecidos como AccountSkuIds:</span><span class="sxs-lookup"><span data-stu-id="80653-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

<span data-ttu-id="80653-115">Para obter mais informações, consulte [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="80653-115">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="80653-116">Para ver os resultados anteriores e posteriores dos procedimentos neste tópico, consulte [Exibir licença de conta e detalhes do serviço com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="80653-116">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="80653-117">Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="80653-117">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="80653-118">Especificamente, o script permite que você exiba e desabilite serviços na sua organização do Office 365, incluindo Sway.</span><span class="sxs-lookup"><span data-stu-id="80653-118">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="80653-119">Para saber mais, confira [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="80653-119">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="80653-120">Desabilitar serviços específicos do Office 365 para usuários específicos para um plano de licenciamento específico</span><span class="sxs-lookup"><span data-stu-id="80653-120">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="80653-121">Para desabilitar um conjunto específico de serviços do Office 365 para os usuários para um plano de licenciamento específico, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="80653-121">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="80653-122">Identifique os serviços indesejáveis no plano de licenciamento usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="80653-122">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="80653-123">O exemplo a seguir cria \*\*\*\* um objeto licenseoptions que desabilita o Office Online e o SharePoint Online Services no plano de licenciamento `litwareinc:ENTERPRISEPACK` chamado (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="80653-123">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="80653-124">Use o objeto **LicenseOptions** da Etapa 1 em um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="80653-124">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="80653-125">Para criar uma nova conta que tem serviços desabilitados, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="80653-125">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="80653-126">O exemplo a seguir cria uma nova conta para o Leonor Marques que atribui a licença e desabilita os serviços descritos na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="80653-126">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="80653-127">Para obter mais informações sobre a criação de contas de usuário no Office 365 PowerShell, consulte [Create User Accounts with office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="80653-127">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="80653-128">Para desabilitar os serviços de um usuário licenciado existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="80653-128">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="80653-129">Este exemplo desabilita os serviços do usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="80653-129">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="80653-130">Para desabilitar os serviços descritos na etapa 1 para todos os usuários licenciados existentes, especifique o nome do seu plano do Office 365 na exibição do cmdlet **Get-MsolAccountSku** (como **litwareinc: ENTERPRISEPACK**) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="80653-130">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="80653-131">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_ , somente as primeiras 500 contas de usuário serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="80653-131">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>


  - <span data-ttu-id="80653-132">Para desabilitar os serviços para um grupo de usuários existentes, use um dos seguintes métodos para identificar os usuários:</span><span class="sxs-lookup"><span data-stu-id="80653-132">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="80653-133">**Filtrar as contas com base em um atributo de conta existente** Para fazer isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="80653-133">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="80653-134">O exemplo a seguir desabilita os serviços para usuários no departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="80653-134">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="80653-135">**Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="80653-135">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="80653-136">Crie um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="80653-136">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="80653-137">Neste exemplo, o arquivo de texto é C:\\meus documentos\\accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="80653-137">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="80653-138">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="80653-138">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="80653-139">Se você quiser desabilitar o acesso aos serviços para vários planos de licenciamento, repita as instruções acima para cada plano de licenciamento, assegurando que:</span><span class="sxs-lookup"><span data-stu-id="80653-139">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="80653-140">O plano de licenciamento foi atribuído às contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="80653-140">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="80653-141">Os serviços a serem desabilitados estão disponíveis no plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="80653-141">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="80653-142">Para desabilitar os serviços do Office 365 para usuários enquanto você estiver atribuindo-os a um plano de licenciamento, confira [desabilitar o acesso aos serviços ao atribuir licenças de usuário](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="80653-142">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="80653-143">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="80653-143">New to Office 365?</span></span>
<span data-ttu-id="80653-144"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="80653-144"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="80653-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="80653-145">See also</span></span>
<span data-ttu-id="80653-146"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="80653-146"></span></span>

<span data-ttu-id="80653-147">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="80653-147">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="80653-148">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80653-148">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="80653-149">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80653-149">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="80653-150">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80653-150">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="80653-151">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="80653-151">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="80653-152">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80653-152">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
