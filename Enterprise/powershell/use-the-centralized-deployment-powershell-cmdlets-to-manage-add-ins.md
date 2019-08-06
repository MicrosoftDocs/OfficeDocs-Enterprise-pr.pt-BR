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
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Use os cmdlets do PowerShell de implantação centralizada para ajudá-lo a implantar e gerenciar suplementos do Office para sua organização do Office 365.
ms.openlocfilehash: 3d6495646c6ce0a1d15f2d911f1fa8af92e3c2c6
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782581"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="680b1-103">Usar os cmdlets do PowerShell de Implantação Centralizada para gerenciar suplementos</span><span class="sxs-lookup"><span data-stu-id="680b1-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="680b1-104">Como um administrador do Office 365, você pode implantar suplementos do Office para usuários por meio do recurso de implantação centralizada (consulte [Manage Deployment of Office 365 Add-ins no centro de administração](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span><span class="sxs-lookup"><span data-stu-id="680b1-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="680b1-105">Além de implantar os suplementos do Office por meio do centro de administração, você também pode usar o Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="680b1-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="680b1-106">[Baixe](https://go.microsoft.com/fwlink/p/?linkid=850850) os cmdlets do PowerShell de implantação centralizada no centro de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="680b1-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="680b1-107">O que você deseja fazer?</span><span class="sxs-lookup"><span data-stu-id="680b1-107">What do you want to do?</span></span>

[<span data-ttu-id="680b1-108">Conectar-se usando suas credenciais de administrador</span><span class="sxs-lookup"><span data-stu-id="680b1-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="680b1-109">Carregar um manifesto de suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="680b1-110">Carregar um suplemento da Office Store</span><span class="sxs-lookup"><span data-stu-id="680b1-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="680b1-111">Obter detalhes de um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="680b1-112">Ativar ou desativar um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="680b1-113">Adicionar ou remover usuários de um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="680b1-114">Atualizar um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="680b1-115">Excluir um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="680b1-116">Obter ajuda detalhada para cada cmdlet</span><span class="sxs-lookup"><span data-stu-id="680b1-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="680b1-117">Conectar-se usando suas credenciais de administrador</span><span class="sxs-lookup"><span data-stu-id="680b1-117">Connect using your admin credentials</span></span>
<span data-ttu-id="680b1-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-118"></span></span>

<span data-ttu-id="680b1-119">Antes de poder usar os cmdlets de implantação centralizada, você precisa entrar.</span><span class="sxs-lookup"><span data-stu-id="680b1-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="680b1-120">Inicie o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="680b1-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="680b1-121">Conecte-se ao PowerShell usando as credenciais de administrador da sua empresa.</span><span class="sxs-lookup"><span data-stu-id="680b1-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="680b1-122">Execute o cmdlet a seguir.</span><span class="sxs-lookup"><span data-stu-id="680b1-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="680b1-123">Na página **Inserir credenciais** , digite suas credenciais de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="680b1-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="680b1-124">Como alternativa, você pode inserir suas credenciais diretamente no cmdlet.</span><span class="sxs-lookup"><span data-stu-id="680b1-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="680b1-125">Execute o cmdlet a seguir especificando suas credenciais de administrador de empresa como um objeto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="680b1-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="680b1-126">Para obter mais informações sobre como usar o PowerShell, confira [conectar-se ao Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="680b1-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="680b1-127">Carregar um manifesto de suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-127">Upload an add-in manifest</span></span>
<span data-ttu-id="680b1-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-128"></span></span>

<span data-ttu-id="680b1-129">Execute o cmdlet New-OrganizationAdd-in para carregar um manifesto de suplemento a partir de um caminho, que pode ser um local de arquivo ou uma URL.</span><span class="sxs-lookup"><span data-stu-id="680b1-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="680b1-130">O exemplo a seguir mostra um local de arquivo para o valor do parâmetro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="680b1-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="680b1-131">Você também pode executar o cmdlet New-OrganizationAdd-in para carregar um suplemento e atribuí-lo a usuários ou grupos diretamente usando o parâmetro _Members_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="680b1-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="680b1-132">Separe os endereços de email dos membros com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="680b1-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="680b1-133">Carregar um suplemento da Office Store</span><span class="sxs-lookup"><span data-stu-id="680b1-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="680b1-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-134"></span></span>

<span data-ttu-id="680b1-135">Execute o cmdlet New-OrganizationAddIn para carregar um manifesto da Office Store.</span><span class="sxs-lookup"><span data-stu-id="680b1-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="680b1-136">No exemplo a seguir, o cmdlet New-OrganizationAddIn especifica o AssetID de um suplemento para um local dos Estados Unidos e o mercado de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="680b1-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="680b1-137">Para determinar o valor para o __ parâmetro AssetID, você pode copiá-lo da URL da página da Web da Office Store para o suplemento.</span><span class="sxs-lookup"><span data-stu-id="680b1-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="680b1-138">AssetIds sempre começa com "WA" seguido por um número.</span><span class="sxs-lookup"><span data-stu-id="680b1-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="680b1-139">Por exemplo, no exemplo anterior, a origem para o valor AssetID de WA104099688 é a URL da página da Web da Office Store para o suplemento: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="680b1-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="680b1-140">Os valores para o parâmetro _locale_ e o parâmetro _ContentMarket_ são idênticos e indicam o país/região para o qual você está tentando instalar o suplemento.</span><span class="sxs-lookup"><span data-stu-id="680b1-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="680b1-141">O formato é en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="680b1-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="680b1-142">e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="680b1-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="680b1-143">Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store.</span><span class="sxs-lookup"><span data-stu-id="680b1-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="680b1-144">Obter detalhes de um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-144">Get details of an add-in</span></span>
<span data-ttu-id="680b1-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-145"></span></span>

<span data-ttu-id="680b1-146">Execute o cmdlet Get-OrganizationAddIn conforme mostrado abaixo para obter detalhes de todos os suplementos carregados no locatário, incluindo a ID de produto de um suplemento.</span><span class="sxs-lookup"><span data-stu-id="680b1-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="680b1-147">Execute o cmdlet Get-OrganizationAddIn com um valor para o parâmetro _ProductID_ para especificar o suplemento para o qual você deseja recuperar detalhes.</span><span class="sxs-lookup"><span data-stu-id="680b1-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="680b1-148">Para obter detalhes completos de todos os suplementos, além dos usuários e grupos atribuídos, canalize a saída do cmdlet Get-OrganizationAddIn para o cmdlet Format-List, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="680b1-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="680b1-149">Ativar ou desativar um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="680b1-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-150"></span></span>

<span data-ttu-id="680b1-151">Para desativar um suplemento para que os usuários e grupos atribuídos a ele não tenham mais acesso, execute o cmdlet Set-OrganizationAddIn com o parâmetro _ProductID_ e o parâmetro _Enabled_ definido como `$false`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="680b1-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="680b1-152">Para ativar um suplemento novamente, execute o mesmo cmdlet com o parâmetro _Enabled_ definido como `$true`.</span><span class="sxs-lookup"><span data-stu-id="680b1-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="680b1-153">Adicionar ou remover usuários de um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="680b1-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-154"></span></span>

<span data-ttu-id="680b1-155">Para adicionar usuários e grupos a um suplemento específico, execute o cmdlet Set-OrganizationAddInAssignments com os parâmetros _ProductID_, _Add_e Members __ .</span><span class="sxs-lookup"><span data-stu-id="680b1-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="680b1-156">Separe os endereços de email dos membros com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="680b1-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="680b1-157">Para remover usuários e grupos, execute o mesmo cmdlet usando o parâmetro _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="680b1-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="680b1-158">Para atribuir um suplemento a todos os usuários no locatário, execute o mesmo cmdlet usando o parâmetro _AssignToEveryone_ com o valor definido como `$true`.</span><span class="sxs-lookup"><span data-stu-id="680b1-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="680b1-159">Para não atribuir um suplemento a todos e reverter para os usuários e grupos atribuídos anteriormente, você pode executar o mesmo cmdlet e desativar o parâmetro _AssignToEveryone_ definindo seu valor como `$false`.</span><span class="sxs-lookup"><span data-stu-id="680b1-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="680b1-160">Atualizar um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-160">Update an add-in</span></span>
<span data-ttu-id="680b1-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-161"></span></span>

<span data-ttu-id="680b1-162">Para atualizar um suplemento de um manifesto, execute o cmdlet Set-OrganizationAddIn com os parâmetros _ProductID_, _ManifestPath_e _locale_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="680b1-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="680b1-163">Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store.</span><span class="sxs-lookup"><span data-stu-id="680b1-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="680b1-164">Excluir um suplemento</span><span class="sxs-lookup"><span data-stu-id="680b1-164">Delete an add-in</span></span>
<span data-ttu-id="680b1-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-165"></span></span>

<span data-ttu-id="680b1-166">Para excluir um suplemento, execute o cmdlet Remove-OrganizationAddIn com o parâmetro _ProductID_ , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="680b1-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="680b1-167">Obter ajuda detalhada para cada cmdlet</span><span class="sxs-lookup"><span data-stu-id="680b1-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="680b1-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="680b1-168"></span></span>

<span data-ttu-id="680b1-169">Você pode examinar a ajuda detalhada para cada cmdlet usando o cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="680b1-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="680b1-170">Por exemplo, o cmdlet a seguir fornece informações detalhadas sobre o cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="680b1-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


