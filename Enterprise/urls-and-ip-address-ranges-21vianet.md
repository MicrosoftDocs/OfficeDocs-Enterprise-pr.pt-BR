---
title: Intervalos de URLs e endereços IP do Office 365 operados pela 21Vianet
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/29/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
f1.keywords:
- NOCSH
description: This article applies to Office 365 operated by 21Vianet in China. This article lists the URLs and IP address ranges used by Office 365 operated by 21Vianet.
hideEdit: true
ms.openlocfilehash: 9d43049211afbac3c13d013be54a8a944e3acb91
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998134"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>Intervalos de URLs e endereços IP do Office 365 operados pela 21Vianet

 *Aplica-se a: Office 365 operado pela 21Vianet - Administrador de Pequenas Empresas, Office 365 operado pela 21Vianet - Administrador*

**Resumo**: os pontos de extremidade a seguir (FQDNs, portas, URLs, prefixos IPv4 e IPv6) se aplicam ao Office 365 operado pela 21 Vianet e são projetados para entregar serviços de produtividade às organizações que usam somente esses planos.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Pontos de extremidade do Office 365:** [global (incluindo GCC)](urls-and-ip-address-ranges.md)  | *Office 365 operado pela 21 Vianet* | [Office 365 Alemanha](office-365-germany-endpoints.md)  |  [Office 365 Governo dos E.U.A. Departamento de Defesa](office-365-u-s-government-dod-endpoints.md) | [GCC High do Office 365 Governo dos E.U.A. ](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Última atualização:** 06/29/2020- ![ ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [assinatura de log de alteração](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS|**Baixar:** todos os destinos obrigatórios e opcionais em uma lista [no formato em JSON](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> |

Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

As colunas de dados exibidas são:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](./includes/office-365-operated-by-21vianet-endpoints.md)]


