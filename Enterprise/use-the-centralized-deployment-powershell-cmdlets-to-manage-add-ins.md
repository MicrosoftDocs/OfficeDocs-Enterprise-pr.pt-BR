---
title: Usar os cmdlets do PowerShell de Implantação Centralizada para gerenciar suplementos
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Use os cmdlets do PowerShell de implantação centralizada para ajudá-lo a implantar e gerenciar suplementos do Office para sua organização do Office 365.
ms.openlocfilehash: c63a48d212bba4eda25fb6b8843f6321892dc54b
ms.sourcegitcommit: d53033c2d2d41d52047e3e2644d77373d4a5dd9a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35791246"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="76eb8-103">Usar os cmdlets do PowerShell de Implantação Centralizada para gerenciar suplementos</span><span class="sxs-lookup"><span data-stu-id="76eb8-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="76eb8-104">Como um administrador global da Microsoft 365 ou do Exchange, você pode implantar suplementos do Office para usuários por meio do recurso de implantação centralizada (Confira [implantar suplementos do Office no centro de administração](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span><span class="sxs-lookup"><span data-stu-id="76eb8-104">As a Microsoft 365 global, or Exchange admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="76eb8-105">Além de implantar os suplementos do Office por meio do centro de administração do Microsoft 365, você também pode usar o Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76eb8-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="76eb8-106">Instale o [módulo de implantação de suplemento centralizado do O365 para o Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span><span class="sxs-lookup"><span data-stu-id="76eb8-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="76eb8-107">Depois de baixar o módulo, abra uma janela do Windows PowerShell regular e execute o seguinte cmdlet:</span><span class="sxs-lookup"><span data-stu-id="76eb8-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="76eb8-108">Conectar-se usando suas credenciais de administrador</span><span class="sxs-lookup"><span data-stu-id="76eb8-108">Connect using your admin credentials</span></span>

<span data-ttu-id="76eb8-109">Antes de poder usar os cmdlets de implantação centralizada, você precisa entrar.</span><span class="sxs-lookup"><span data-stu-id="76eb8-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="76eb8-110">Inicie o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76eb8-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="76eb8-111">Conecte-se ao PowerShell usando as credenciais de administrador da sua empresa.</span><span class="sxs-lookup"><span data-stu-id="76eb8-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="76eb8-112">Execute o cmdlet a seguir.</span><span class="sxs-lookup"><span data-stu-id="76eb8-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="76eb8-113">Na página **Inserir credenciais** , digite suas credenciais de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="76eb8-113">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="76eb8-114">Como alternativa, você pode inserir suas credenciais diretamente no cmdlet.</span><span class="sxs-lookup"><span data-stu-id="76eb8-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="76eb8-115">Execute o cmdlet a seguir especificando suas credenciais de administrador de empresa como um objeto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="76eb8-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="76eb8-116">Para obter mais informações sobre como usar o PowerShell, confira [conectar-se ao Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="76eb8-116">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="76eb8-117">Carregar um manifesto de suplemento</span><span class="sxs-lookup"><span data-stu-id="76eb8-117">Upload an add-in manifest</span></span>

<span data-ttu-id="76eb8-118">Execute o cmdlet **New-OrganizationAdd-in** para carregar um manifesto de suplemento a partir de um caminho, que pode ser um local de arquivo ou uma URL.</span><span class="sxs-lookup"><span data-stu-id="76eb8-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="76eb8-119">O exemplo a seguir mostra um local de arquivo para o valor do parâmetro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="76eb8-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="76eb8-120">Você também pode executar o cmdlet **New-OrganizationAdd-in** para carregar um suplemento e atribuí-lo a usuários ou grupos diretamente usando o parâmetro _Members_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="76eb8-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="76eb8-121">Separe os endereços de email dos membros com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="76eb8-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="76eb8-122">Carregar um suplemento da Office Store</span><span class="sxs-lookup"><span data-stu-id="76eb8-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="76eb8-123">Execute o cmdlet **New-OrganizationAddIn** para carregar um manifesto da Office Store.</span><span class="sxs-lookup"><span data-stu-id="76eb8-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="76eb8-124">No exemplo a seguir, o cmdlet **New-OrganizationAddIn** especifica o AssetID de um suplemento para um local dos Estados Unidos e o mercado de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="76eb8-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="76eb8-125">Para determinar o valor para o __ parâmetro AssetID, você pode copiá-lo da URL da página da Web da Office Store para o suplemento.</span><span class="sxs-lookup"><span data-stu-id="76eb8-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="76eb8-126">AssetIds sempre começa com "WA" seguido por um número.</span><span class="sxs-lookup"><span data-stu-id="76eb8-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="76eb8-127">Por exemplo, no exemplo anterior, a origem para o valor AssetID de WA104099688 é a URL da página da Web da Office Store para o suplemento: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="76eb8-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="76eb8-128">Os valores para o parâmetro _locale_ e o parâmetro _ContentMarket_ são idênticos e indicam o país/região para o qual você está tentando instalar o suplemento.</span><span class="sxs-lookup"><span data-stu-id="76eb8-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="76eb8-129">O formato é en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="76eb8-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="76eb8-130">e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="76eb8-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="76eb8-131">Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store.</span><span class="sxs-lookup"><span data-stu-id="76eb8-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="76eb8-132">Obter detalhes de um suplemento</span><span class="sxs-lookup"><span data-stu-id="76eb8-132">Get details of an add-in</span></span>

<span data-ttu-id="76eb8-133">Execute o cmdlet **Get-OrganizationAddIn** conforme mostrado abaixo para obter detalhes de todos os suplementos carregados no locatário, incluindo a ID de produto de um suplemento.</span><span class="sxs-lookup"><span data-stu-id="76eb8-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="76eb8-134">Execute o cmdlet **Get-OrganizationAddIn** com um valor para o parâmetro _ProductID_ para especificar o suplemento para o qual você deseja recuperar detalhes.</span><span class="sxs-lookup"><span data-stu-id="76eb8-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="76eb8-135">Para obter detalhes completos de todos os suplementos, além dos usuários e grupos atribuídos, canalize a saída do cmdlet **Get-OrganizationAddIn** para o cmdlet Format-List, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="76eb8-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="76eb8-136">Ativar ou desativar um suplemento</span><span class="sxs-lookup"><span data-stu-id="76eb8-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="76eb8-137">Para desativar um suplemento para que os usuários e grupos atribuídos a ele não tenham mais acesso, execute o cmdlet **set-OrganizationAddIn** com o parâmetro _ProductID_ e o parâmetro _Enabled_ definido como `$false`, conforme mostrado no exemplo a seguir .</span><span class="sxs-lookup"><span data-stu-id="76eb8-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="76eb8-138">Para ativar um suplemento novamente, execute o mesmo cmdlet com o parâmetro _Enabled_ definido como `$true`.</span><span class="sxs-lookup"><span data-stu-id="76eb8-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="76eb8-139">Adicionar ou remover usuários de um suplemento</span><span class="sxs-lookup"><span data-stu-id="76eb8-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="76eb8-140">Para adicionar usuários e grupos a um suplemento específico, execute o cmdlet **set-OrganizationAddInAssignments** com os parâmetros _ProductID_, _Add_e Members __ .</span><span class="sxs-lookup"><span data-stu-id="76eb8-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="76eb8-141">Separe os endereços de email dos membros com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="76eb8-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="76eb8-142">Para remover usuários e grupos, execute o mesmo cmdlet usando o parâmetro _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="76eb8-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="76eb8-143">Para atribuir um suplemento a todos os usuários no locatário, execute o mesmo cmdlet usando o parâmetro _AssignToEveryone_ com o valor definido como `$true`.</span><span class="sxs-lookup"><span data-stu-id="76eb8-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="76eb8-144">Para não atribuir um suplemento a todos e reverter para os usuários e grupos atribuídos anteriormente, você pode executar o mesmo cmdlet e desativar o parâmetro _AssignToEveryone_ definindo seu valor como `$false`.</span><span class="sxs-lookup"><span data-stu-id="76eb8-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="76eb8-145">Atualizar um suplemento</span><span class="sxs-lookup"><span data-stu-id="76eb8-145">Update an add-in</span></span>

<span data-ttu-id="76eb8-146">Para atualizar um suplemento de um manifesto, execute o cmdlet **set-OrganizationAddIn** com os parâmetros _ProductID_, _ManifestPath_e _locale_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="76eb8-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="76eb8-147">Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store.</span><span class="sxs-lookup"><span data-stu-id="76eb8-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="76eb8-148">Excluir um suplemento</span><span class="sxs-lookup"><span data-stu-id="76eb8-148">Delete an add-in</span></span>

<span data-ttu-id="76eb8-149">Para excluir um suplemento, execute o cmdlet **Remove-OrganizationAddIn** com o parâmetro _ProductID_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="76eb8-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a><span data-ttu-id="76eb8-150">Personalizar suplementos da Microsoft Store para sua organização</span><span class="sxs-lookup"><span data-stu-id="76eb8-150">Customize Microsoft Store add-ins for your organization</span></span>

<span data-ttu-id="76eb8-151">Você deve personalizar o suplemento antes de implantá-lo em sua organização.</span><span class="sxs-lookup"><span data-stu-id="76eb8-151">You must customize the add-in before you deploy it to your organization.</span></span> <span data-ttu-id="76eb8-152">Os suplementos mais antigos do que a versão 1,1 não são suportados por este recurso.</span><span class="sxs-lookup"><span data-stu-id="76eb8-152">Add-ins older than version 1.1 are not supported by this feature.</span></span> 

<span data-ttu-id="76eb8-153">Observe também as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="76eb8-153">Note also the following restrictions:</span></span>
- <span data-ttu-id="76eb8-154">Todas as URLs devem ser absolutas (incluir http ou HTTPS) e válidas.</span><span class="sxs-lookup"><span data-stu-id="76eb8-154">All URLs must be absolute (include http or https) and valid.</span></span>
- <span data-ttu-id="76eb8-155">*DisplayName* não deve exceder 125 caracteres</span><span class="sxs-lookup"><span data-stu-id="76eb8-155">*DisplayName* must not exceed 125 characters</span></span> 
- <span data-ttu-id="76eb8-156">*DisplayName*, \*\* Resources e *AppDomains* não devem incluir os seguintes caracteres:</span><span class="sxs-lookup"><span data-stu-id="76eb8-156">*DisplayName*, *Resources* and *AppDomains* must not include the following characters:</span></span> 
 
    - \<
    -  \>
    -  <span data-ttu-id="76eb8-157">;</span><span class="sxs-lookup"><span data-stu-id="76eb8-157"></span></span>
    -  =   

<span data-ttu-id="76eb8-158">Se você quiser personalizar um suplemento implantado, será necessário desinstalá-lo no centro de administração e, em seguida, consulte [remover um suplemento do cache local](#remove-an-add-in-from-local-cache) para obter etapas para removê-lo de cada computador no qual foi implantado.</span><span class="sxs-lookup"><span data-stu-id="76eb8-158">If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.</span></span>

<span data-ttu-id="76eb8-159">Para personalizar um suplemento, execute o cmdlet **set – OrganizationAddInOverrides** com o *ProductID* como um parâmetro, seguido da marca que você deseja substituir e o novo valor.</span><span class="sxs-lookup"><span data-stu-id="76eb8-159">To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value.</span></span> <span data-ttu-id="76eb8-160">Para saber como obter o *ProductID* , confira [obter detalhes de um suplemento](#get-details-of-an-add-in) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="76eb8-160">To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article.</span></span> <span data-ttu-id="76eb8-161">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="76eb8-161">For example:</span></span>

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
<span data-ttu-id="76eb8-162">Para personalizar várias marcas de um suplemento, adicione essas marcas à linha de comando:</span><span class="sxs-lookup"><span data-stu-id="76eb8-162">To customize multiple tags for an add-in, add those tags to the commandline:</span></span>

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> <span data-ttu-id="76eb8-163">Você deve aplicar várias marcas personalizadas a um suplemento como um comando.</span><span class="sxs-lookup"><span data-stu-id="76eb8-163">You must apply multiple customized tags to one add-in as one command.</span></span> <span data-ttu-id="76eb8-164">Se você personalizar as marcas um por um, somente a última personalização será aplicada.</span><span class="sxs-lookup"><span data-stu-id="76eb8-164">If you customize tags one by one, only the last customization will be applied.</span></span> <span data-ttu-id="76eb8-165">Além disso, se você personalizar uma marca por engano, você deve remover todas as personalizações e começar novamente.</span><span class="sxs-lookup"><span data-stu-id="76eb8-165">Additionally, if you customize a tag by mistake, you must remove all customizations and start over.</span></span>

### <a name="tags-you-can-customize"></a><span data-ttu-id="76eb8-166">Marcas que você pode personalizar</span><span class="sxs-lookup"><span data-stu-id="76eb8-166">Tags you can customize</span></span>

| <span data-ttu-id="76eb8-167">Tag</span><span class="sxs-lookup"><span data-stu-id="76eb8-167">Tag</span></span>                  | <span data-ttu-id="76eb8-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="76eb8-168">Description</span></span>          |
| :------------------- | :------------------- |
| <span data-ttu-id="76eb8-169">\<> IconURL</span><span class="sxs-lookup"><span data-stu-id="76eb8-169">\<IconURL></span></span>   </br>| <span data-ttu-id="76eb8-170">A URL da imagem usada como o ícone do suplemento (no centro de administração).</span><span class="sxs-lookup"><span data-stu-id="76eb8-170">The URL of the image used as the add-in’s icon (in admin center).</span></span> </br> |
| <span data-ttu-id="76eb8-171">\<> DisplayName</span><span class="sxs-lookup"><span data-stu-id="76eb8-171">\<DisplayName></span></span>| <span data-ttu-id="76eb8-172">O título do suplemento (no centro de administração).</span><span class="sxs-lookup"><span data-stu-id="76eb8-172">The title of the add-in  (in admin center).</span></span>|
| <span data-ttu-id="76eb8-173">\<Hospeda></span><span class="sxs-lookup"><span data-stu-id="76eb8-173">\<Hosts></span></span>| <span data-ttu-id="76eb8-174">Lista de aplicativos que oferecerão suporte ao suplemento.</span><span class="sxs-lookup"><span data-stu-id="76eb8-174">List of apps that will support the add-in.</span></span>|
| <span data-ttu-id="76eb8-175">\<> SourceLocation</span><span class="sxs-lookup"><span data-stu-id="76eb8-175">\<SourceLocation></span></span> | <span data-ttu-id="76eb8-176">A URL de origem à qual o suplemento será conectado.</span><span class="sxs-lookup"><span data-stu-id="76eb8-176">The source URL that the add-in will connect to.</span></span>| 
| <span data-ttu-id="76eb8-177">\<> AppDomains</span><span class="sxs-lookup"><span data-stu-id="76eb8-177">\<AppDomains></span></span> | <span data-ttu-id="76eb8-178">Uma lista de domínios com os quais o suplemento pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="76eb8-178">A list of domains that the add-in can connect with.</span></span> | 
| <span data-ttu-id="76eb8-179">\<> SupportURL</span><span class="sxs-lookup"><span data-stu-id="76eb8-179">\<SupportURL></span></span>| <span data-ttu-id="76eb8-180">A URL que os usuários podem usar para acessar a ajuda e suporte.</span><span class="sxs-lookup"><span data-stu-id="76eb8-180">The URL users can use to access help and support.</span></span> | 
| <span data-ttu-id="76eb8-181">\<Recursos></span><span class="sxs-lookup"><span data-stu-id="76eb8-181">\<Resources></span></span>  | <span data-ttu-id="76eb8-182">Essa marca contém vários elementos, incluindo títulos, dicas de ferramentas e ícones de tamanhos diferentes.</span><span class="sxs-lookup"><span data-stu-id="76eb8-182">This tag contains a number of elements including titles, tooltips, and icons of different sizes.</span></span>| 
|
### <a name="customize-resources-tag"></a><span data-ttu-id="76eb8-183">Marca personalizar recursos</span><span class="sxs-lookup"><span data-stu-id="76eb8-183">Customize Resources tag</span></span>

<span data-ttu-id="76eb8-184">Qualquer elemento na <Resources> marca do manifesto pode ser personalizado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="76eb8-184">Any element in the <Resources> tag of the manifest can be customized dynamically.</span></span> <span data-ttu-id="76eb8-185">Primeiro, você precisa verificar o manifesto para localizar a ID do elemento ao qual você deseja atribuir um novo valor.</span><span class="sxs-lookup"><span data-stu-id="76eb8-185">You first need to check the manifest to find the element id to which you want to assign a new value.</span></span> <span data-ttu-id="76eb8-186">A <Resources> marca tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="76eb8-186">The <Resources> tag looks like this:</span></span>

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
<span data-ttu-id="76eb8-187">Nesse caso, a ID do elemento para a imagem é "img16icon" e o valor associado a ela é "http:<i></i>//site. <i> </i>com/img. jpg. "</span><span class="sxs-lookup"><span data-stu-id="76eb8-187">In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”</span></span>

<span data-ttu-id="76eb8-188">Depois de identificar os elementos que você deseja personalizar, use o seguinte comando no PowerShell para atribuir novos valores aos elementos:</span><span class="sxs-lookup"><span data-stu-id="76eb8-188">Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:</span></span>

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

<span data-ttu-id="76eb8-189">Você pode personalizar tantos elementos com o comando quanto necessário.</span><span class="sxs-lookup"><span data-stu-id="76eb8-189">You can customize as many elements with the command as you need to.</span></span>

### <a name="remove-customization-from-an-add-in"></a><span data-ttu-id="76eb8-190">Remover a personalização de um suplemento</span><span class="sxs-lookup"><span data-stu-id="76eb8-190">Remove customization from an add-in</span></span>

<span data-ttu-id="76eb8-191">A única opção disponível atualmente para excluir personalizações é excluir todas elas de uma só vez:</span><span class="sxs-lookup"><span data-stu-id="76eb8-191">The only option currently available for deleting customizations is to delete all of them at once:</span></span>

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a><span data-ttu-id="76eb8-192">Exibir personalizações de suplementos</span><span class="sxs-lookup"><span data-stu-id="76eb8-192">View add-in customizations</span></span>

<span data-ttu-id="76eb8-193">Para exibir uma lista de personalizações aplicadas, execute o cmdlet **Get-OrganizationAddInOverrides** .</span><span class="sxs-lookup"><span data-stu-id="76eb8-193">To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet.</span></span> <span data-ttu-id="76eb8-194">Se **Get-OrganizationAddInOverrides** for executado sem um *ProductID* , uma lista de todos os suplementos com substituições aplicadas será retornada.</span><span class="sxs-lookup"><span data-stu-id="76eb8-194">If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.</span></span>  

```powershell
Get-OrganizationAddInOverrides 
```
<span data-ttu-id="76eb8-195">Se ProductId for especificado, uma lista de substituições aplicada a esse suplemento será retornada.</span><span class="sxs-lookup"><span data-stu-id="76eb8-195">If ProductId is specified, then a list of overrides applied to that add-in is returned.</span></span> 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a><span data-ttu-id="76eb8-196">Remover um suplemento do cache local</span><span class="sxs-lookup"><span data-stu-id="76eb8-196">Remove an add-in from local cache</span></span>

<span data-ttu-id="76eb8-197">Se um suplemento tiver sido implantado, ele deve ser removido do cache em cada computador antes que ele possa ser personalizado.</span><span class="sxs-lookup"><span data-stu-id="76eb8-197">If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized.</span></span> <span data-ttu-id="76eb8-198">Para remive um suplemento do cache:</span><span class="sxs-lookup"><span data-stu-id="76eb8-198">To remive an add-in from cache:</span></span>

1. <span data-ttu-id="76eb8-199">Navegue até a pasta "usuários" em C:</span><span class="sxs-lookup"><span data-stu-id="76eb8-199">Navigate to the “Users” folder in C:</span></span>\ 
1. <span data-ttu-id="76eb8-200">Vá para a pasta do usuário</span><span class="sxs-lookup"><span data-stu-id="76eb8-200">Go to your user folder</span></span>
1. <span data-ttu-id="76eb8-201">Navegue até AppData\Local\Microsoft\Office e selecione a pasta associada à sua versão do Office</span><span class="sxs-lookup"><span data-stu-id="76eb8-201">Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office</span></span>
1. <span data-ttu-id="76eb8-202">Na pasta *WEF* , exclua \*\* a pasta manifestos.</span><span class="sxs-lookup"><span data-stu-id="76eb8-202">In the *Wef* folder delete the *Manifests* folder.</span></span>

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="76eb8-203">Obter ajuda detalhada para cada cmdlet</span><span class="sxs-lookup"><span data-stu-id="76eb8-203">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="76eb8-204">Você pode examinar a ajuda detalhada para cada cmdlet usando o cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="76eb8-204">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="76eb8-205">Por exemplo, o cmdlet a seguir fornece informações detalhadas sobre o cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="76eb8-205">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


