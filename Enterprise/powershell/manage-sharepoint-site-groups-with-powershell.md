---
title: Manage SharePoint Online site groups with Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumo: Usar o PowerShell do Office 365 para gerenciar grupos de sites do SharePoint Online.'
ms.openlocfilehash: a9fddf33b2f29e7b4e8ed6b86c2433c7ca19a9fc
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915346"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="bbd0c-103">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbd0c-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="bbd0c-104">**Resumo:** Use o Office 365 PowerShell para gerenciar grupos de sites do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="bbd0c-105">Embora você possa usar o Centro de administração do Office 365, você também pode usar o Office 365 PowerShell para gerenciar os grupos de sites do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="bbd0c-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="bbd0c-106">Before you begin</span></span>

<span data-ttu-id="bbd0c-p101">Os procedimentos neste artigo exigem que você se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="bbd0c-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="bbd0c-109">Modo de exibição SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbd0c-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="bbd0c-p102">Centro de administração do SharePoint Online tem alguns métodos fácil de usar para gerenciar grupos de sites. Por exemplo, suponha que você deseja examinar os grupos e os membros do grupo, o `https://litwareinc.sharepoint.com/sites/finance` site. Aqui está o que você deve fazer para:</span><span class="sxs-lookup"><span data-stu-id="bbd0c-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="bbd0c-113">No Centro de administração do Office 365, clique em **recursos** > **Sites**e, em seguida, clique na URL do site.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="bbd0c-114">Na caixa de diálogo do conjunto de sites, clique em **Ir para este site**.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="bbd0c-115">Na página do site, clique no ícone **configurações** (localizado no canto superior direito da página) e clique em **configurações do Site**:</span><span class="sxs-lookup"><span data-stu-id="bbd0c-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="bbd0c-116">![Configurações de site do SharePoint Online](media/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="bbd0c-116">![SharePoint Online site settings](media/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="bbd0c-117">Na página Configurações do Site, clique em **permissões de Sites** em **usuários e permissões**.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="bbd0c-118">E, em seguida, repita o processo para o próximo site que você deseja examinar.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="bbd0c-119">Para obter uma lista dos grupos com o Office 365 PowerShell, você usaria o seguinte conjunto de comando:</span><span class="sxs-lookup"><span data-stu-id="bbd0c-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="bbd0c-120">Há duas maneiras de executar este comando definir no prompt de comando do Shell de gerenciamento do SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="bbd0c-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="bbd0c-p103">Copie os comandos no bloco de notas (ou outro editor de texto), modifique o valor da variável **$siteURL** , selecione os comandos e cole-os no prompt de comando do Shell de gerenciamento do SharePoint Online. Quando você fizer isso, o PowerShell será interrompida a um **>>** prompt. Pressione Enter para executar o comando **foreach** .</span><span class="sxs-lookup"><span data-stu-id="bbd0c-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a **>>** prompt. Press Enter to execute the **foreach** command.</span></span></br>
- <span data-ttu-id="bbd0c-p104">Copie os comandos no bloco de notas (ou outro editor de texto), modifique o valor da variável **$siteURL** e, em seguida, salve o arquivo de texto com um nome e a extensão. ps1 em uma pasta adequada. Em seguida, execute o script no prompt de comando do Shell de gerenciamento do SharePoint Online especificando seu nome de arquivo e caminho. Aqui está um exemplo de comando:</span><span class="sxs-lookup"><span data-stu-id="bbd0c-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="bbd0c-127">Em ambos os casos, você verá algo semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="bbd0c-127">In both cases, you should see something similar to this:</span></span>

![Grupos de sites do SharePoint Online](media/SPO-site-groups.png)

<span data-ttu-id="bbd0c-p105">Esses são todos os grupos que foram criados para o site `https://litwareinc.sharepoint.com/sites/finance`, assim como todos os usuários atribuídos a esses grupos. Os nomes de grupo são em amarelo para ajudá-lo nomes de grupo separado de seus membros.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-p105">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="bbd0c-131">Como outro exemplo, aqui está um conjunto de comandos que lista os grupos e todas as associações de grupo, para todos os sites do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```
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
    
## <a name="see-also"></a><span data-ttu-id="bbd0c-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="bbd0c-132">See also</span></span>

[<span data-ttu-id="bbd0c-133">Conectar ao PowerShell do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bbd0c-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="bbd0c-134">Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbd0c-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="bbd0c-135">Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbd0c-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="bbd0c-136">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbd0c-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="bbd0c-137">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbd0c-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

