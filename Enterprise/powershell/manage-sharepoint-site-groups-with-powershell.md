---
title: Manage SharePoint Online site groups with Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
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
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumo: Use o Office 365 PowerShell para gerenciar grupos de sites do SharePoint Online.'
ms.openlocfilehash: 3a1b999470746cbe02ec52fe888ea26b59cd423b
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004194"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="36f2e-103">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f2e-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="36f2e-104">Embora você possa usar o centro de administração do Microsoft 365, você também pode usar o Office 365 PowerShell para gerenciar seus grupos de sites do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="36f2e-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="36f2e-105">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="36f2e-105">Before you begin</span></span>

<span data-ttu-id="36f2e-106">Os procedimentos deste artigo exigem que você se conecte ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="36f2e-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="36f2e-107">Para obter instruções, consulte [conectar-se ao PowerShell do SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="36f2e-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="36f2e-108">Exibir o SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f2e-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="36f2e-109">O centro de administração do SharePoint Online tem alguns métodos fáceis de usar para gerenciar grupos de sites.</span><span class="sxs-lookup"><span data-stu-id="36f2e-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="36f2e-110">Por exemplo, suponha que você queira examinar os grupos e os membros do grupo para o `https://litwareinc.sharepoint.com/sites/finance` site.</span><span class="sxs-lookup"><span data-stu-id="36f2e-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="36f2e-111">Veja o que você precisa fazer para:</span><span class="sxs-lookup"><span data-stu-id="36f2e-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="36f2e-112">No centro de administração do SharePoint, clique em **sites ativos**e, em seguida, clique na URL do site.</span><span class="sxs-lookup"><span data-stu-id="36f2e-112">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="36f2e-113">Na página do site, clique no ícone **configurações** (localizado no canto superior direito da página) e clique em **permissões do site**.</span><span class="sxs-lookup"><span data-stu-id="36f2e-113">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="36f2e-114">E, em seguida, repita o processo para o próximo site que você deseja examinar.</span><span class="sxs-lookup"><span data-stu-id="36f2e-114">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="36f2e-115">Para obter uma lista dos grupos com o Office 365 PowerShell, você pode usar os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="36f2e-115">To get a list of the groups with Office 365 PowerShell, you can use the following commands:</span></span>

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="36f2e-116">Há duas maneiras de executar este conjunto de comandos no prompt de comando do Shell de gerenciamento do SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="36f2e-116">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="36f2e-117">Copie os comandos para o bloco de notas (ou outro editor de texto), modifique o valor da variável **$SiteUrl** , selecione os comandos e cole-os no prompt de comando do Shell de gerenciamento do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="36f2e-117">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="36f2e-118">Quando você fizer isso, o PowerShell será interrompido **>>** em um prompt.</span><span class="sxs-lookup"><span data-stu-id="36f2e-118">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="36f2e-119">Pressione Enter para executar o `foreach` comando.</span><span class="sxs-lookup"><span data-stu-id="36f2e-119">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="36f2e-120">Copie os comandos para o bloco de notas (ou outro editor de texto), modifique o valor da variável **$SiteUrl** e salve esse arquivo de texto com um nome e a extensão. ps1 em uma pasta adequada.</span><span class="sxs-lookup"><span data-stu-id="36f2e-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="36f2e-121">Em seguida, execute o script a partir do prompt de comando do Shell de gerenciamento do SharePoint Online especificando o caminho e o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="36f2e-121">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="36f2e-122">Este é um exemplo de comando:</span><span class="sxs-lookup"><span data-stu-id="36f2e-122">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="36f2e-123">Em ambos os casos, você deve ver algo semelhante a:</span><span class="sxs-lookup"><span data-stu-id="36f2e-123">In both cases, you should see something similar to this:</span></span>

![Grupos de sites do SharePoint Online](media/SPO-site-groups.png)

<span data-ttu-id="36f2e-125">Estes são todos os grupos que foram criados para o site `https://litwareinc.sharepoint.com/sites/finance`e todos os usuários atribuídos a esses grupos.</span><span class="sxs-lookup"><span data-stu-id="36f2e-125">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="36f2e-126">Os nomes de grupo estão em amarelo para ajudá-lo a separar os nomes de grupo de seus membros.</span><span class="sxs-lookup"><span data-stu-id="36f2e-126">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="36f2e-127">Como outro exemplo, aqui está um conjunto de comandos que lista os grupos e todos os membros do grupo, para todos os seus sites do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="36f2e-127">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a><span data-ttu-id="36f2e-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="36f2e-128">See also</span></span>

[<span data-ttu-id="36f2e-129">Conectar ao PowerShell do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="36f2e-129">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="36f2e-130">Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f2e-130">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="36f2e-131">Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f2e-131">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="36f2e-132">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f2e-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="36f2e-133">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f2e-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

