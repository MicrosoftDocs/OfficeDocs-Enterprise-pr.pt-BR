---
title: "Desabilitar o acesso aos serviços com o PowerShell do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
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
description: "Explica como usar o Office 365 PowerShell para desabilitar o acesso aos serviços do Office 365 para usuários em sua organização."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="28129-103">Desabilitar o acesso aos serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="28129-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="28129-104">**Resumo:** Explica como usar o Office 365 PowerShell para desabilitar o acesso aos serviços do Office 365 para usuários em sua organização.</span><span class="sxs-lookup"><span data-stu-id="28129-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="28129-p101">Quando uma conta do Office 365 é atribuída a uma licença de um plano de licenciamento, serviços do Office 365 são disponibilizados para o usuário dessa licença. No entanto, você pode controlar os serviços do Office 365 que o usuário pode acessar. Por exemplo, mesmo que a licença permite o acesso ao SharePoint Online, você pode desabilitar o acesso a ele. Na verdade, você pode usar o Office 365 PowerShell para desabilitar o acesso a qualquer número de serviços para:</span><span class="sxs-lookup"><span data-stu-id="28129-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="28129-109">Uma conta individual</span><span class="sxs-lookup"><span data-stu-id="28129-109">An individual account.</span></span>
    
- <span data-ttu-id="28129-110">Um grupo de contas.</span><span class="sxs-lookup"><span data-stu-id="28129-110">A group of accounts.</span></span>
    
- <span data-ttu-id="28129-111">Todas as contas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="28129-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="28129-112">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="28129-112">Before you begin</span></span>
<span data-ttu-id="28129-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="28129-113"></span></span>

- <span data-ttu-id="28129-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="28129-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="28129-p103">Você pode usar o cmdlet **Get-MsolAccountSku** para exibir seus planos de licenciamento disponíveis e que estão disponíveis nesses planos de serviços do Office 365. Para obter mais informações, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="28129-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="28129-118">Para ver o antes e depois os resultados dos procedimentos neste tópico, consulte [Exibir detalhes de licença e serviço de conta com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="28129-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="28129-p104">Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico. Especificamente, o script permite exibir e desabilitar serviços em sua organização do Office 365, incluindo o Sway. Para saber mais, confira [Desabilitar o acesso ao Sway com o PowerShell do Office 365](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="28129-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="28129-122">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_ , somente as contas de 500 usuário primeira são retornadas.</span><span class="sxs-lookup"><span data-stu-id="28129-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="28129-123">Serviços específicos do Office 365 para usuários específicos para um único plano de licenciamento</span><span class="sxs-lookup"><span data-stu-id="28129-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="28129-124">Para desabilitar um conjunto específico de serviços do Office 365 para usuários de um único plano de licenciamento, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="28129-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="28129-125">Identificar os serviços indesejáveis no plano de licenciamento usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="28129-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="28129-126">O exemplo a seguir cria um objeto de **LicenseOptions** que desabilita os Serviços Online do Office e SharePoint Online no plano de licenciamento denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="28129-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="28129-127">Use o objeto **LicenseOptions** da etapa 1 em um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="28129-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="28129-128">Para criar uma nova conta que tem serviços desabilitados, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="28129-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="28129-129">O exemplo a seguir cria uma nova conta para Allie Bellew que atribui a licença e desabilita os serviços descritos na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="28129-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="28129-130">Para obter mais informações sobre a criação de contas de usuário no Office 365 PowerShell, consulte [criar contas de usuário com o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="28129-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="28129-131">Para desabilitar os serviços de um usuário licenciado existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="28129-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="28129-132">Este exemplo desabilita os serviços do usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="28129-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="28129-133">Para desabilitar os serviços descritos na etapa 1 para todos os usuários licenciados existentes, especifique o nome do seu plano do Office 365 da exibição do cmdlet **Get-MsolAccountSku** (por exemplo, **litwareinc: enterprisepack**) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="28129-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="28129-134">Para desabilitar os serviços para um grupo de usuários existentes, use um dos seguintes métodos para identificar os usuários:</span><span class="sxs-lookup"><span data-stu-id="28129-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="28129-135">**Filtrar as contas com base em um atributo existente da conta** Para fazer isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="28129-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="28129-136">O exemplo a seguir desabilita os serviços para os usuários no departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="28129-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="28129-137">**Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="28129-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="28129-138">Crie um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="28129-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="28129-139">Neste exemplo, o arquivo de texto é c:\\Meus documentos\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="28129-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="28129-140">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="28129-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="28129-141">Para desabilitar os serviços do Office 365 para usuários enquanto eles atribuídas a um plano de licenciamento, consulte [Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="28129-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="28129-142">Serviços específicos do Office 365 para usuários de todos os planos de licenciamento</span><span class="sxs-lookup"><span data-stu-id="28129-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="28129-143">Para desabilitar os serviços do Office 365 para usuários em todos os planos de licenciamento disponíveis, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="28129-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="28129-144">Copie e cole este script no Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="28129-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="28129-145">Personalize os seguintes valores para seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="28129-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="28129-146">_<UndesirableService>_Neste exemplo, usaremos Online do Office e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="28129-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="28129-147">_<Account>_Neste exemplo, usaremos belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="28129-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="28129-148">O script personalizado tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="28129-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="28129-p105">Salve o script como `RemoveO365Services.ps1` em um local fácil de encontrar. Neste exemplo, podemos vai salvar o arquivo em `C:\\O365 Scripts`.</span><span class="sxs-lookup"><span data-stu-id="28129-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="28129-151">Execute o script no PowerShell do Office 365 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="28129-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="28129-152">Para reverter os efeitos de qualquer um desses procedimentos (ou seja, para reabilitar os serviços desabilitados), execute o procedimento novamente, mas use o valor `$null` para o parâmetro _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="28129-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="28129-153">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="28129-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a><span data-ttu-id="28129-154">Todos os serviços do Office 365 para todos os usuários de um único plano de licenciamento</span><span class="sxs-lookup"><span data-stu-id="28129-154">All Office 365 services for all users for a single licensing plan</span></span>
 
<span data-ttu-id="28129-155">Para desabilitar todos os serviços do Office 365 para todos os usuários em um plano de licenciamento específico, especifique o nome do plano de licenciamento para $acctSKU (por exemplo, **litwareinc: enterprisepack**) e, em seguida, execute estes comandos na janela de comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="28129-155">To disable all Office 365 services for all users in a specific licensing plan, specify the licensing plan name for $acctSKU (such as **litwareinc:ENTERPRISEPACK**), and then run these commands in the PowerShell command window:</span></span>

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a><span data-ttu-id="28129-156">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="28129-156">New to Office 365?</span></span>
<span data-ttu-id="28129-157"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="28129-157"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="28129-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="28129-158">See also</span></span>
<span data-ttu-id="28129-159"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="28129-159"></span></span>

<span data-ttu-id="28129-160">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="28129-160">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="28129-161">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="28129-161">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="28129-162">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="28129-162">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="28129-163">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="28129-163">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="28129-164">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="28129-164">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="28129-165">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="28129-165">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="28129-166">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="28129-166">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="28129-167">Get-Content</span><span class="sxs-lookup"><span data-stu-id="28129-167">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="28129-168">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="28129-168">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="28129-169">New-MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="28129-169">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="28129-170">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="28129-170">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="28129-171">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="28129-171">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="28129-172">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="28129-172">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="28129-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="28129-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="28129-174">Where-Object</span><span class="sxs-lookup"><span data-stu-id="28129-174">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

