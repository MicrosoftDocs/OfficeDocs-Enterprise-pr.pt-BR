---
title: Restringir o conteúdo do site do SharePoint a um local geográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba como restringir os sites do SharePoint em um local geográfico especificado em um ambiente de multigeográfico.
ms.openlocfilehash: 9319ed6229acc7cda48cc52b3a27681c53f1359c
ms.sourcegitcommit: 7bb48195079ce14aabfa0384771b17db0e4908b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "36828475"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Restringir o conteúdo do site do SharePoint a um local geográfico

Em algumas circunstâncias você pode optar por impor que um site e o conteúdo do arquivo permaneça na localização geográfica onde o site foi criado, impedindo que o site movido ou impedindo o cache de conteúdo do arquivo do site em outro local geográfico.

Você pode fazer isso usando o cmdlet [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) com o parâmetro **RestrictedToGeo**. Esse parâmetro possui um valor padrão de NULO, mas você pode alterá-lo para um destes procedimentos:

|Restrição|Descrição|
|:----------|:----------|
|NoRestriction|O site pode ser movido para outro local geográfico.|
|BlockMoveOnly|O site não pode ser movido para outro local geográfico, mas o conteúdo do site pode ser armazenada em cache em outros locais geográficos.|
|BlockFull|Site não pode ser movido para outro local geográfico e o conteúdo do arquivo completo não está armazenado em cache em outros locais geográficos. O título dos arquivos (colhidos do conteúdo), o nome do arquivo e outras propriedades do arquivo ainda podem ser armazenados em cache em outras localizações geográficas.<br>O conteúdo armazenado no site antes de ser configurado para o BlockFull, pode continuar a ser armazenado em cache em outras localizações geográficas.|

Use a seguinte sintaxe:

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Por exemplo:

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
