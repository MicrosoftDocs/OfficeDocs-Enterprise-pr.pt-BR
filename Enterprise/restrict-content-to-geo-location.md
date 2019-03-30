---
title: Restringir o conteúdo para uma localização geográfica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba como restringir os sites do SharePoint em um local geográfico especificado em um ambiente de multigeográfico.
ms.openlocfilehash: 59301a591e5465bdcda4aa84a18880961c0b615b
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933925"
---
# <a name="restrict-content-to-a-geo-location"></a><span data-ttu-id="ca82a-103">Restringir o conteúdo para uma localização geográfica</span><span class="sxs-lookup"><span data-stu-id="ca82a-103">Restrict content to a geo location</span></span>

<span data-ttu-id="ca82a-104">Em algumas circunstâncias você pode optar por impor que um site e o conteúdo do arquivo permaneça na localização geográfica onde o site foi criado, impedindo que o site movido ou impedindo o cache de conteúdo do arquivo do site em outro local geográfico.</span><span class="sxs-lookup"><span data-stu-id="ca82a-104">Under some circumstances you may choose to enforce a site and its file content to remain in the geo location where the site was created, either by preventing the site from being moved or by preventing the caching of the site's file content in another geo location.</span></span>

<span data-ttu-id="ca82a-105">Você pode fazer isso usando o cmdlet [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) com o parâmetro **RestrictedToGeo**.</span><span class="sxs-lookup"><span data-stu-id="ca82a-105">You can do this by using the [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet with the **RestrictedToGeo** parameter.</span></span> <span data-ttu-id="ca82a-106">Esse parâmetro possui um valor padrão de NULO, mas você pode alterá-lo para um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="ca82a-106">This parameter has a default value of NULL, but you can change it to one of the following:</span></span>

|<span data-ttu-id="ca82a-107">Restrição</span><span class="sxs-lookup"><span data-stu-id="ca82a-107">Restriction</span></span>|<span data-ttu-id="ca82a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca82a-108">Description</span></span>|
|:----------|:----------|
|<span data-ttu-id="ca82a-109">NoRestriction</span><span class="sxs-lookup"><span data-stu-id="ca82a-109">NoRestriction</span></span>|<span data-ttu-id="ca82a-110">O site pode ser movido para outro local geográfico.</span><span class="sxs-lookup"><span data-stu-id="ca82a-110">The site can be moved to another geo location.</span></span>|
|<span data-ttu-id="ca82a-111">BlockMoveOnly</span><span class="sxs-lookup"><span data-stu-id="ca82a-111">BlockMoveOnly</span></span>|<span data-ttu-id="ca82a-112">O site não pode ser movido para outro local geográfico, mas o conteúdo do site pode ser armazenada em cache em outros locais geográficos.</span><span class="sxs-lookup"><span data-stu-id="ca82a-112">Site cannot be moved to another geo location, but site content can be cached in other geo locations.</span></span>|
|<span data-ttu-id="ca82a-113">BlockFull</span><span class="sxs-lookup"><span data-stu-id="ca82a-113">BlockFull</span></span>|<span data-ttu-id="ca82a-114">Site não pode ser movido para outro local geográfico e o conteúdo do arquivo completo não está armazenado em cache em outros locais geográficos.</span><span class="sxs-lookup"><span data-stu-id="ca82a-114">Site cannot be moved to another geo location, and full file content is not cached in other geo locations.</span></span> <span data-ttu-id="ca82a-115">O título dos arquivos (colhidos do conteúdo), o nome do arquivo e outras propriedades do arquivo ainda podem ser armazenados em cache em outras localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="ca82a-115">Files' title (harvested from the content), file name, and other properties of the file can still be cached in other geo-locations.</span></span><br><span data-ttu-id="ca82a-116">O conteúdo armazenado no site antes de ser configurado para o BlockFull, pode continuar a ser armazenado em cache em outras localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="ca82a-116">Content stored in the site before it was configured to BlockFull, may continue to be cached in other geo locations.</span></span>|

<span data-ttu-id="ca82a-117">Use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="ca82a-117">Use the following syntax:</span></span>

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

<span data-ttu-id="ca82a-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ca82a-118">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
