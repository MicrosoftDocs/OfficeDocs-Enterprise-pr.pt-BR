---
title: Desabilitar o acesso aos serviços com o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/20/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Explica como usar o Office 365 PowerShell para desabilitar o acesso aos serviços do Office 365 para usuários em sua organização.
ms.openlocfilehash: d65308746ac5c2b60f4749588455fa66471069e3
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914986"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="93b1f-103">Desabilitar o acesso aos serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="93b1f-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="93b1f-104">**Resumo:** Explica como usar o Office 365 PowerShell para desabilitar o acesso aos serviços do Office 365 para usuários em sua organização.</span><span class="sxs-lookup"><span data-stu-id="93b1f-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="93b1f-p101">Quando uma conta do Office 365 é atribuída a uma licença de um plano de licenciamento, serviços do Office 365 são disponibilizados para o usuário dessa licença. No entanto, você pode controlar os serviços do Office 365 que o usuário pode acessar. Por exemplo, mesmo que a licença permite acesso ao serviço do SharePoint Online, você pode desabilitar o acesso a ele. Você pode usar o Office 365 PowerShell para desabilitar o acesso a qualquer número de serviços para um plano de licenciamento específico para:</span><span class="sxs-lookup"><span data-stu-id="93b1f-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to the SharePoint Online service, you can disable access to it. You can use Office 365 PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="93b1f-109">Uma conta individual</span><span class="sxs-lookup"><span data-stu-id="93b1f-109">An individual account.</span></span>
    
- <span data-ttu-id="93b1f-110">Um grupo de contas.</span><span class="sxs-lookup"><span data-stu-id="93b1f-110">A group of accounts.</span></span>
    
- <span data-ttu-id="93b1f-111">Todas as contas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="93b1f-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="93b1f-112">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="93b1f-112">Before you begin</span></span>
<span data-ttu-id="93b1f-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="93b1f-113"></span></span>

- <span data-ttu-id="93b1f-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="93b1f-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93b1f-p103">Você pode usar o cmdlet **Get-MsolAccountSku** para exibir seus planos de licenciamento disponíveis e que estão disponíveis nesses planos de serviços do Office 365. Para obter mais informações, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="93b1f-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93b1f-118">Para ver o antes e depois os resultados dos procedimentos neste tópico, consulte [Exibir detalhes de licença e serviço de conta com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="93b1f-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93b1f-p104">Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico. Especificamente, o script permite exibir e desabilitar serviços em sua organização do Office 365, incluindo o Sway. Para saber mais, confira [Desabilitar o acesso ao Sway com o PowerShell do Office 365](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="93b1f-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93b1f-122">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_ , somente as contas de 500 usuário primeira são retornadas.</span><span class="sxs-lookup"><span data-stu-id="93b1f-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="93b1f-123">Desabilitar serviços específicos do Office 365 para usuários específicos para um plano de licenciamento específico</span><span class="sxs-lookup"><span data-stu-id="93b1f-123">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="93b1f-124">Para desabilitar um conjunto específico de serviços do Office 365 para usuários de um plano de licenciamento específico, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="93b1f-124">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="93b1f-125">Identificar os serviços indesejáveis no plano de licenciamento usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="93b1f-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="93b1f-126">O exemplo a seguir cria um objeto de **LicenseOptions** que desabilita os Serviços Online do Office e SharePoint Online no plano de licenciamento denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="93b1f-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="93b1f-127">Use o objeto **LicenseOptions** da Etapa 1 em um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="93b1f-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="93b1f-128">Para criar uma nova conta que tem serviços desabilitados, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="93b1f-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="93b1f-129">O exemplo a seguir cria uma nova conta para Allie Bellew que atribui a licença e desabilita os serviços descritos na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="93b1f-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="93b1f-130">Para obter mais informações sobre a criação de contas de usuário no Office 365 PowerShell, consulte [criar contas de usuário com o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="93b1f-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="93b1f-131">Para desabilitar os serviços de um usuário licenciado existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="93b1f-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="93b1f-132">Este exemplo desabilita os serviços do usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="93b1f-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="93b1f-133">Para desabilitar os serviços descritos na etapa 1 para todos os usuários licenciados existentes, especifique o nome do seu plano do Office 365 da exibição do cmdlet **Get-MsolAccountSku** (por exemplo, **litwareinc: enterprisepack**) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="93b1f-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="93b1f-134">Para desabilitar os serviços para um grupo de usuários existentes, use um dos seguintes métodos para identificar os usuários:</span><span class="sxs-lookup"><span data-stu-id="93b1f-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="93b1f-135">**Filtrar as contas com base em um atributo existente da conta** Para fazer isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="93b1f-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="93b1f-136">O exemplo a seguir desabilita os serviços para os usuários no departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="93b1f-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="93b1f-137">**Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="93b1f-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="93b1f-138">Crie um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="93b1f-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="93b1f-139">Neste exemplo, o arquivo de texto é c:\\Meus documentos\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="93b1f-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="93b1f-140">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="93b1f-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="93b1f-141">Se desejar desabilitar o acesso aos serviços para vários planos de licenciamento, repita as instruções acima para cada plano de licenciamento, garantindo que:</span><span class="sxs-lookup"><span data-stu-id="93b1f-141">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="93b1f-142">As contas de usuário atribuiu o plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="93b1f-142">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="93b1f-143">Para desabilitar os serviços estão disponíveis no plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="93b1f-143">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="93b1f-144">Para desabilitar os serviços do Office 365 para usuários enquanto eles atribuídas a um plano de licenciamento, consulte [Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="93b1f-144">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="93b1f-145">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="93b1f-145">New to Office 365?</span></span>
<span data-ttu-id="93b1f-146"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="93b1f-146"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="93b1f-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="93b1f-147">See also</span></span>
<span data-ttu-id="93b1f-148"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="93b1f-148"></span></span>

<span data-ttu-id="93b1f-149">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="93b1f-149">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="93b1f-150">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="93b1f-150">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93b1f-151">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="93b1f-151">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93b1f-152">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="93b1f-152">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93b1f-153">Atribuir licenças a contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="93b1f-153">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93b1f-154">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="93b1f-154">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="93b1f-155">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="93b1f-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="93b1f-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="93b1f-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="93b1f-157">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="93b1f-157">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="93b1f-158">New-MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="93b1f-158">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="93b1f-159">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="93b1f-159">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="93b1f-160">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="93b1f-160">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="93b1f-161">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="93b1f-161">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="93b1f-162">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="93b1f-162">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="93b1f-163">Where-Object</span><span class="sxs-lookup"><span data-stu-id="93b1f-163">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

