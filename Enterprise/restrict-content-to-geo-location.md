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
# <a name="restrict-content-to-a-geo-location"></a>Restringir o conteúdo para uma localização geográfica

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
