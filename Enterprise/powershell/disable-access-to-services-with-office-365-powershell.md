---
title: "Desabilitar o acesso aos serviços com o PowerShell do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Explica como usar o Office 365 PowerShell para adicionar ou remover o acesso aos serviços do Office 365 para usuários na sua organização."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="167b1-103">Desabilitar o acesso aos serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="167b1-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="167b1-104">**Resumo:** Explica como usar o Office 365 PowerShell para adicionar ou remover o acesso aos serviços do Office 365 para usuários na sua organização.</span><span class="sxs-lookup"><span data-stu-id="167b1-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="167b1-p101">Quando uma conta do Office 365 é atribuída a uma licença de um plano de licenciamento, serviços do Office 365 são disponibilizados para o usuário dessa licença. No entanto, você pode controlar os serviços do Office 365 que o usuário pode acessar. Por exemplo, mesmo que a licença permite o acesso ao SharePoint Online, você pode desabilitar o acesso a ele. Na verdade, você pode usar o Office 365 PowerShell para desabilitar o acesso a qualquer número de serviços para:</span><span class="sxs-lookup"><span data-stu-id="167b1-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="167b1-109">Uma conta individual</span><span class="sxs-lookup"><span data-stu-id="167b1-109">An individual account.</span></span>
    
- <span data-ttu-id="167b1-110">Um grupo de contas.</span><span class="sxs-lookup"><span data-stu-id="167b1-110">A group of accounts.</span></span>
    
- <span data-ttu-id="167b1-111">Todas as contas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="167b1-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="167b1-112">**Conteúdo:** [A versão curta (instruções sem explicações)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [A versão longa (instruções com explicações detalhadas sobre)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Consulte também](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="167b1-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="167b1-113">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="167b1-113">Before you begin</span></span>
<span data-ttu-id="167b1-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="167b1-114"></span></span>

- <span data-ttu-id="167b1-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="167b1-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="167b1-p103">Você pode usar o cmdlet **Get-MsolAccountSku** para exibir seus planos de licenciamento disponíveis e que estão disponíveis nesses planos de serviços do Office 365. Para obter mais informações, consulte[Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="167b1-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="167b1-119">Para ver o antes e depois os resultados dos procedimentos neste tópico, consulte [Exibir detalhes de licença e serviço de conta com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="167b1-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="167b1-p104">Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico. Especificamente, o script permite exibir e desabilitar serviços em sua organização do Office 365, incluindo o Sway. Para saber mais, confira [Desabilitar o acesso ao Sway com o PowerShell do Office 365](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="167b1-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="167b1-123">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="167b1-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="167b1-124">A versão curta (instruções sem explicações)</span><span class="sxs-lookup"><span data-stu-id="167b1-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="167b1-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="167b1-125"></span></span>

<span data-ttu-id="167b1-p105">Esta seção apresenta os procedimentos sem divulgação ou explicação supérflua. Se você tiver dúvidas ou se quiser obter mais informações, leia o restante do tópico.</span><span class="sxs-lookup"><span data-stu-id="167b1-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="167b1-128">Para desabilitar os serviços do Office 365 para usuários de um único plano de licenciamento, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="167b1-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="167b1-129">Identificar os serviços indesejáveis no plano de licenciamento usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="167b1-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="167b1-130">Este exemplo cria um objeto **LicenseOptions** que desabilita os Serviços Online do Office e SharePoint Online no plano de licenciamento denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="167b1-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="167b1-131">Use o objeto **LicenseOptions** da etapa 1 em um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="167b1-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="167b1-132">Para criar uma nova conta que tem serviços desabilitados, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="167b1-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="167b1-133">Este exemplo cria uma nova conta para Leonor Marques que atribui a licença e desabilita os serviços descritos na Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="167b1-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="167b1-134">Para obter mais informações sobre a criação de contas de usuário no Office 365 PowerShell, consulte [criar contas de usuário com o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="167b1-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="167b1-135">Para desabilitar os serviços de um usuário licenciado existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="167b1-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="167b1-136">Este exemplo desabilita os serviços do usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="167b1-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="167b1-137">Para desabilitar os serviços descritos na etapa 1 para todos os usuários licenciados existentes, especifique o nome do seu plano do Office 365 da exibição do cmdlet **Get-MsolAccountSku** (por exemplo, **litwareinc: enterprisepack** ) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="167b1-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="167b1-138">Para desabilitar os serviços para um grupo de usuários existentes, use um dos seguintes métodos para identificar os usuários:</span><span class="sxs-lookup"><span data-stu-id="167b1-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="167b1-139">**Filtrar as contas com base em um atributo existente da conta** Para fazer isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="167b1-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="167b1-140">Este exemplo desabilita os serviços para os usuários no departamento de Vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="167b1-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="167b1-141">**Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="167b1-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="167b1-142">Crie um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="167b1-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="167b1-143">Neste exemplo, o arquivo de texto é c:\\Meus documentos\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="167b1-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="167b1-144">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="167b1-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="167b1-145">Para desabilitar os serviços do Office 365 para usuários enquanto eles atribuídas a um plano de licenciamento, consulte [Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="167b1-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="167b1-146">Para desabilitar os serviços do Office 365 para usuários em todos os planos de licenciamento disponíveis, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="167b1-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="167b1-147">Copie e cole este script no Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="167b1-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="167b1-148">Personalize os seguintes valores para seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="167b1-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="167b1-149">_<UndesirableService>_Neste exemplo, usaremos Online do Office e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="167b1-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="167b1-150">_<Account>_Neste exemplo, usaremos belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="167b1-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="167b1-151">O script personalizado tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="167b1-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="167b1-p106">Salve o script como `RemoveO365Services.ps1` em um local fácil de encontrar. Neste exemplo, podemos vai salvar o arquivo em " `C:\\O365 Scripts`".</span><span class="sxs-lookup"><span data-stu-id="167b1-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="167b1-154">Execute o script no PowerShell do Office 365 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="167b1-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="167b1-155">Para reverter os efeitos de qualquer um desses procedimentos (ou seja, para reabilitar os serviços desabilitados), execute o procedimento novamente, mas use o valor `$null` para o parâmetro _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="167b1-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="167b1-156">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="167b1-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="167b1-157">A versão longa (instruções com explicações detalhadas)</span><span class="sxs-lookup"><span data-stu-id="167b1-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="167b1-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="167b1-158"></span></span>

<span data-ttu-id="167b1-p107">Por padrão, todos os serviços estão habilitados quando você emite uma licença usando o PowerShell do Office 365. E geralmente é uma boa coisa: isso significa que você pode rapidez e facilidade atribuir licenças aos usuários sem ter de especificar o que cada serviço será habilitada ao longo do percurso.</span><span class="sxs-lookup"><span data-stu-id="167b1-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="167b1-p108">Dito isso, no entanto, também é verdade que você deseja restringir os serviços disponíveis em alguns dos usuários; Por exemplo, talvez alguns usuários devem ter acesso ao Office Professional Plus, Skype para Business Online e Exchange Online, mas esses mesmos usuários não devem ter acesso ao SharePoint Online ou no Office Online. Você pode restringir contas dessa maneira? Na verdade, você pode. Para ajudar a explicam como isso funciona, vamos uma abordagem em duas etapas para lidar com esse problema:</span><span class="sxs-lookup"><span data-stu-id="167b1-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="167b1-165">Atribua ao usuário uma licença do Office 365 que automaticamente habilita todos os serviços.</span><span class="sxs-lookup"><span data-stu-id="167b1-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="167b1-166">Execute um par de comandos do PowerShell do Office 365 que desabilitam serviços para esse usuário.</span><span class="sxs-lookup"><span data-stu-id="167b1-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="167b1-p109">Podemos já atentar da etapa 1: nosso (Belinda Newman) do usuário tem uma licença do Office 365 que lhe oferece acesso a todos os serviços do Office 365. No entanto, queremos modificar a conta de Belinda para que ela não tem acesso ao SharePoint Online ( `SHAREPOINTENTERPRISE`) ou no Office Online ( `SHAREPOINTWAC`). Mas como podemos devem fazer isso?</span><span class="sxs-lookup"><span data-stu-id="167b1-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="167b1-p110">Aqui está como. Em primeiro lugar, vamos usar o cmdlet **New-MsolLicenseOptions** para criar um objeto de **LicenseOption** que contém os serviços que queremos desabilitados. No caso de Belinda, queremos desabilitar `SHAREPOINTENTERPRISE` e `SHAREPOINTWAC`, portanto, usamos este comando:</span><span class="sxs-lookup"><span data-stu-id="167b1-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="167b1-p111">Entendeu como funciona? Você especifica o plano de licenciamento ( `litwareinc:ENTERPRISEPACK`) e indica cada um dos serviços que você deseja desabilitados, separando-os por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="167b1-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="167b1-p112">Certificar-se de que você armazene seu novo objeto **LicenseOption** em uma variável. No exemplo anterior, usamos `$x`, embora você possa usar qualquer nome de variável válido do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="167b1-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="167b1-177">Agora podemos usar o seguinte comando para desabilitar o acesso de Belinda aos dois serviços:</span><span class="sxs-lookup"><span data-stu-id="167b1-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="167b1-p113">Nada muito elaborado aqui, ambos: basta chamar o cmdlet **Set-MsolUserLicense** e incluir o parâmetro _LicenseOptions_ , juntamente com a variável ( `$x`) que contém os planos queremos desabilitar. E o que vemos agora se podemos dê uma olhada no informações de licença de Belinda executando o comando: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Vemos isto:</span><span class="sxs-lookup"><span data-stu-id="167b1-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="167b1-p114">Muito legal, hein? E, obviamente, poderíamos fazer essa mesma coisa a vários usuários se quisermos. Por exemplo, esses comandos desabilitar os mesmos dois serviços para todos os nossos usuários licenciados. Especifique o nome do seu plano do Office 365 da exibição do cmdlet **Get-MsolAccountSku** (por exemplo, **litwareinc: enterprisepack** ) e, em seguida, executá-los.</span><span class="sxs-lookup"><span data-stu-id="167b1-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="167b1-p115">Tenha em mente que Belinda ainda tem uma licença válida do Office 365; é exatamente isso agora ela tem acesso aos serviços de menos. Antes de desabilitamos os dois serviços, Belinda tinha acesso a news feeds, OneDrive e SharePoint Online sites:</span><span class="sxs-lookup"><span data-stu-id="167b1-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![Usuário com acesso ao SharePoint](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="167b1-188">Agora essas opções já não estão mais disponíveis:</span><span class="sxs-lookup"><span data-stu-id="167b1-188">Now those options are no longer available to her:</span></span>
  
![Usuário sem acesso ao SharePoint](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="167b1-190">Que é exatamente o que queríamos que acontecesse.</span><span class="sxs-lookup"><span data-stu-id="167b1-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="167b1-p116">E se podemos alterar nossa mente posterior em: é possível reabilitar esses serviços? Você aposto é. Para reabilitar a todos os serviços para um usuário, use este comando para criar o objeto de **LicenseOption** a seguir:</span><span class="sxs-lookup"><span data-stu-id="167b1-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="167b1-p117">O que esse comando fazer? Para começar, com a constante do Windows PowerShell `$null` significa "nada". (Ou, no idioma do pouco mais técnico, isso significa que um "valor nulo".) Como você se lembra, quando usamos o cmdlet **New-MsolLicenseOptions** temos que indicar os serviços que queremos desabilitado. Nesse caso, não queremos qualquer um dos serviços a ser desabilitado. Que podem levar você acredita que poderíamos usar um comando semelhante ao seguinte, um comando onde podemos não especificar um valor para o parâmetro _DisabledPlans_ :</span><span class="sxs-lookup"><span data-stu-id="167b1-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="167b1-p118">No entanto, isso não funcionará. Em vez disso, ela gerará uma mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="167b1-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="167b1-201">Felizmente para nós, definindo o valor de parâmetro para `$null` funciona:</span><span class="sxs-lookup"><span data-stu-id="167b1-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="167b1-202">Isso simplesmente significa que, quando executamos o cmdlet **Set-MsolUserLicense** , estamos dizendo para **Set-MsolUserLicense** que não queremos que Belinda tenha quaisquer serviços desabilitados:</span><span class="sxs-lookup"><span data-stu-id="167b1-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="167b1-203">E, logicamente, se nenhum dos serviços está desabilitado, deve significar que todos estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="167b1-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="167b1-p119">Agora que você entende como isso funciona, vamos mostram como você pode emitir uma licença e desabilitar os serviços especificados e todos com o mesmo comando. Sinceramente, não há realmente nada a ele, mas, isso parece muito impressionante: apenas incluir os _AddLicenses_ e _LicenseOptions_ parâmetros no mesmo comando. Em outras palavras, primeiro crie seu objeto **LicenseOption** :</span><span class="sxs-lookup"><span data-stu-id="167b1-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="167b1-207">E, em seguida, conforme observado anteriormente, você usa o _AddLicenses_ e os parâmetros de _LicenseOptions_ em seu comando:</span><span class="sxs-lookup"><span data-stu-id="167b1-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="167b1-208">Que comando emitirá Belinda Newman uma nova licença, mas uma licença nos qual Skype para Business Online ( `SHAREPOINTWAC`) e o SharePoint Online ( `SHAREPOINTENTERPRISE`) estarão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="167b1-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="167b1-209">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="167b1-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="167b1-210">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="167b1-210">New to Office 365?</span></span>
<span data-ttu-id="167b1-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="167b1-211"></span></span>

||
|:-----|
|<span data-ttu-id="167b1-p120">![O ícone pequeno do LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Começando a usar o Office 365?**         Descubra cursos em vídeo gratuitos para **Office 365 admins and IT pros**, oferecidos pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="167b1-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="167b1-214">See also</span><span class="sxs-lookup"><span data-stu-id="167b1-214">See also</span></span>
<span data-ttu-id="167b1-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="167b1-215"></span></span>

<span data-ttu-id="167b1-216">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="167b1-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="167b1-217">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="167b1-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="167b1-218">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="167b1-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="167b1-219">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="167b1-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="167b1-220">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="167b1-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="167b1-221">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="167b1-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="167b1-222">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="167b1-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="167b1-223">Get-Content</span><span class="sxs-lookup"><span data-stu-id="167b1-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="167b1-224">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="167b1-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="167b1-225">New-MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="167b1-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="167b1-226">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="167b1-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="167b1-227">MsolUser-nova</span><span class="sxs-lookup"><span data-stu-id="167b1-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="167b1-228">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="167b1-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="167b1-229">ForEach-Object.</span><span class="sxs-lookup"><span data-stu-id="167b1-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="167b1-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="167b1-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="167b1-231">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="167b1-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

