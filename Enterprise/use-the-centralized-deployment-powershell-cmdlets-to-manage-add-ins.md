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
ms.openlocfilehash: 34040d11a1ef4d5da2d7a0e980b28e7ef0eba7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070497"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="b6e2d-103">Usar os cmdlets do PowerShell de Implantação Centralizada para gerenciar suplementos</span><span class="sxs-lookup"><span data-stu-id="b6e2d-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="b6e2d-104">Como um administrador do Office 365, você pode implantar suplementos do Office para usuários por meio do recurso de implantação centralizada (Confira [implantar suplementos do Office no centro de administração do office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span><span class="sxs-lookup"><span data-stu-id="b6e2d-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="b6e2d-105">Além de implantar os suplementos do Office por meio do centro de administração do Office 365, você também pode usar o Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-105">In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="b6e2d-106">Instale o [módulo de implantação de suplemento centralizado do O365 para o Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span><span class="sxs-lookup"><span data-stu-id="b6e2d-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="b6e2d-107">Conectar-se usando suas credenciais de administrador</span><span class="sxs-lookup"><span data-stu-id="b6e2d-107">Connect using your admin credentials</span></span>

<span data-ttu-id="b6e2d-108">Antes de poder usar os cmdlets de implantação centralizada, você precisa entrar.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-108">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="b6e2d-109">Inicie o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-109">Start PowerShell.</span></span>
    
2. <span data-ttu-id="b6e2d-110">Conecte-se ao PowerShell usando as credenciais de administrador da sua empresa.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-110">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="b6e2d-111">Execute o cmdlet a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-111">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="b6e2d-112">Na página **Inserir credenciais** , digite suas credenciais de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-112">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="b6e2d-113">Como alternativa, você pode inserir suas credenciais diretamente no cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-113">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="b6e2d-114">Execute o cmdlet a seguir especificando suas credenciais de administrador de empresa como um objeto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-114">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="b6e2d-115">Para obter mais informações sobre como usar o PowerShell, confira [conectar-se ao Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="b6e2d-115">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="b6e2d-116">Carregar um manifesto de suplemento</span><span class="sxs-lookup"><span data-stu-id="b6e2d-116">Upload an add-in manifest</span></span>

<span data-ttu-id="b6e2d-117">Execute o cmdlet New-OrganizationAdd-in para carregar um manifesto de suplemento a partir de um caminho, que pode ser um local de arquivo ou uma URL.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-117">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="b6e2d-118">O exemplo a seguir mostra um local de arquivo para o valor do parâmetro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="b6e2d-118">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="b6e2d-119">Você também pode executar o cmdlet New-OrganizationAdd-in para carregar um suplemento e atribuí-lo a usuários ou grupos diretamente usando o parâmetro _Members_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-119">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="b6e2d-120">Separe os endereços de email dos membros com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-120">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="b6e2d-121">Carregar um suplemento da Office Store</span><span class="sxs-lookup"><span data-stu-id="b6e2d-121">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="b6e2d-122">Execute o cmdlet New-OrganizationAddIn para carregar um manifesto da Office Store.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-122">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="b6e2d-123">No exemplo a seguir, o cmdlet New-OrganizationAddIn especifica o AssetID de um suplemento para um local dos Estados Unidos e o mercado de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-123">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="b6e2d-124">Para determinar o valor para o __ parâmetro AssetID, você pode copiá-lo da URL da página da Web da Office Store para o suplemento.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-124">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="b6e2d-125">AssetIds sempre começa com "WA" seguido por um número.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-125">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="b6e2d-126">Por exemplo, no exemplo anterior, a origem para o valor AssetID de WA104099688 é a URL da página da Web da Office Store para o suplemento: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="b6e2d-126">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="b6e2d-127">Os valores para o parâmetro _locale_ e o parâmetro _ContentMarket_ são idênticos e indicam o país/região para o qual você está tentando instalar o suplemento.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-127">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="b6e2d-128">O formato é en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-128">The format is en-US, fr-FR.</span></span> <span data-ttu-id="b6e2d-129">e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-129">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="b6e2d-130">Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-130">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="b6e2d-131">Obter detalhes de um suplemento</span><span class="sxs-lookup"><span data-stu-id="b6e2d-131">Get details of an add-in</span></span>

<span data-ttu-id="b6e2d-132">Execute o cmdlet Get-OrganizationAddIn conforme mostrado abaixo para obter detalhes de todos os suplementos carregados no locatário, incluindo a ID de produto de um suplemento.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-132">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="b6e2d-133">Execute o cmdlet Get-OrganizationAddIn com um valor para o parâmetro _ProductID_ para especificar o suplemento para o qual você deseja recuperar detalhes.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-133">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="b6e2d-134">Para obter detalhes completos de todos os suplementos, além dos usuários e grupos atribuídos, canalize a saída do cmdlet Get-OrganizationAddIn para o cmdlet Format-List, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-134">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="b6e2d-135">Ativar ou desativar um suplemento</span><span class="sxs-lookup"><span data-stu-id="b6e2d-135">Turn on or turn off an add-in</span></span>

<span data-ttu-id="b6e2d-136">Para desativar um suplemento para que os usuários e grupos atribuídos a ele não tenham mais acesso, execute o cmdlet Set-OrganizationAddIn com o parâmetro _ProductID_ e o parâmetro _Enabled_ definido como `$false`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-136">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="b6e2d-137">Para ativar um suplemento novamente, execute o mesmo cmdlet com o parâmetro _Enabled_ definido como `$true`.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-137">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="b6e2d-138">Adicionar ou remover usuários de um suplemento</span><span class="sxs-lookup"><span data-stu-id="b6e2d-138">Add or remove users from an add-in</span></span>

<span data-ttu-id="b6e2d-139">Para adicionar usuários e grupos a um suplemento específico, execute o cmdlet Set-OrganizationAddInAssignments com os parâmetros _ProductID_, _Add_e Members __ .</span><span class="sxs-lookup"><span data-stu-id="b6e2d-139">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="b6e2d-140">Separe os endereços de email dos membros com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-140">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="b6e2d-141">Para remover usuários e grupos, execute o mesmo cmdlet usando o parâmetro _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="b6e2d-141">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="b6e2d-142">Para atribuir um suplemento a todos os usuários no locatário, execute o mesmo cmdlet usando o parâmetro _AssignToEveryone_ com o valor definido como `$true`.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-142">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="b6e2d-143">Para não atribuir um suplemento a todos e reverter para os usuários e grupos atribuídos anteriormente, você pode executar o mesmo cmdlet e desativar o parâmetro _AssignToEveryone_ definindo seu valor como `$false`.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-143">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="b6e2d-144">Atualizar um suplemento</span><span class="sxs-lookup"><span data-stu-id="b6e2d-144">Update an add-in</span></span>

<span data-ttu-id="b6e2d-145">Para atualizar um suplemento de um manifesto, execute o cmdlet Set-OrganizationAddIn com os parâmetros _ProductID_, _ManifestPath_e _locale_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-145">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="b6e2d-146">Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-146">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="b6e2d-147">Excluir um suplemento</span><span class="sxs-lookup"><span data-stu-id="b6e2d-147">Delete an add-in</span></span>

<span data-ttu-id="b6e2d-148">Para excluir um suplemento, execute o cmdlet Remove-OrganizationAddIn com o parâmetro _ProductID_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-148">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="b6e2d-149">Obter ajuda detalhada para cada cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6e2d-149">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="b6e2d-150">Você pode examinar a ajuda detalhada para cada cmdlet usando o cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-150">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="b6e2d-151">Por exemplo, o cmdlet a seguir fornece informações detalhadas sobre o cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="b6e2d-151">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


