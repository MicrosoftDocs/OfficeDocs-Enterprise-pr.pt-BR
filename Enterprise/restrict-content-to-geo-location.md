---
title: Restringir o conteúdo do site do SharePoint a um local geográfico
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: Neste artigo, saiba como restringir sites do SharePoint a um local geográfico especificado em um ambiente multigeográfico.
ms.openlocfilehash: 7f0147d803fe4dbc6aa444a5e5014884c0f00beb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606147"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a><span data-ttu-id="51260-103">Restringir o conteúdo do site do SharePoint a um local geográfico</span><span class="sxs-lookup"><span data-stu-id="51260-103">Restrict SharePoint site content to a geo location</span></span>

<span data-ttu-id="51260-104">Em algumas circunstâncias você pode optar por impor que um site e o conteúdo do arquivo permaneça na localização geográfica onde o site foi criado, impedindo que o site movido ou impedindo o cache de conteúdo do arquivo do site em outro local geográfico.</span><span class="sxs-lookup"><span data-stu-id="51260-104">Under some circumstances you may choose to enforce a site and its file content to remain in the geo location where the site was created, either by preventing the site from being moved or by preventing the caching of the site's file content in another geo location.</span></span>

<span data-ttu-id="51260-105">Você pode fazer isso usando o cmdlet [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) com o parâmetro **RestrictedToGeo**.</span><span class="sxs-lookup"><span data-stu-id="51260-105">You can do this by using the [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet with the **RestrictedToGeo** parameter.</span></span> <span data-ttu-id="51260-106">Esse parâmetro possui um valor padrão de NULO, mas você pode alterá-lo para um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="51260-106">This parameter has a default value of NULL, but you can change it to one of the following:</span></span>

|<span data-ttu-id="51260-107">Restrição</span><span class="sxs-lookup"><span data-stu-id="51260-107">Restriction</span></span>|<span data-ttu-id="51260-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="51260-108">Description</span></span>|
|:----------|:----------|
|<span data-ttu-id="51260-109">NoRestriction</span><span class="sxs-lookup"><span data-stu-id="51260-109">NoRestriction</span></span>|<span data-ttu-id="51260-110">O site pode ser movido para outro local geográfico.</span><span class="sxs-lookup"><span data-stu-id="51260-110">The site can be moved to another geo location.</span></span>|
|<span data-ttu-id="51260-111">BlockMoveOnly</span><span class="sxs-lookup"><span data-stu-id="51260-111">BlockMoveOnly</span></span>|<span data-ttu-id="51260-112">O site não pode ser movido para outro local geográfico, mas o conteúdo do site pode ser armazenada em cache em outros locais geográficos.</span><span class="sxs-lookup"><span data-stu-id="51260-112">Site cannot be moved to another geo location, but site content can be cached in other geo locations.</span></span>|
|<span data-ttu-id="51260-113">BlockFull</span><span class="sxs-lookup"><span data-stu-id="51260-113">BlockFull</span></span>|<span data-ttu-id="51260-114">Site não pode ser movido para outro local geográfico e o conteúdo do arquivo completo não está armazenado em cache em outros locais geográficos.</span><span class="sxs-lookup"><span data-stu-id="51260-114">Site cannot be moved to another geo location, and full file content is not cached in other geo locations.</span></span> <span data-ttu-id="51260-115">O título dos arquivos (colhidos do conteúdo), o nome do arquivo e outras propriedades do arquivo ainda podem ser armazenados em cache em outras localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="51260-115">Files' title (harvested from the content), file name, and other properties of the file can still be cached in other geo-locations.</span></span><br><span data-ttu-id="51260-116">O conteúdo armazenado no site antes de ser configurado para o BlockFull, pode continuar a ser armazenado em cache em outras localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="51260-116">Content stored in the site before it was configured to BlockFull, may continue to be cached in other geo locations.</span></span>|

<span data-ttu-id="51260-117">Use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="51260-117">Use the following syntax:</span></span>

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

<span data-ttu-id="51260-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="51260-118">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
