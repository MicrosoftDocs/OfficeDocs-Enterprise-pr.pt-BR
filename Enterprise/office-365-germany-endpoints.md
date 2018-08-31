---
title: Pontos de extremidade do Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Se sua organização usa o Office 365 e restringe os computadores em sua rede de se conectar à Internet, abaixo você encontrará os pontos de extremidade (FQDNs, portas, URLs e IPv4 e IPv6 intervalos de endereços) que você deve incluir em seu saída permite listas garantir que sua computadores com êxito podem usar o Office 365.
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539130"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="58b40-103">Pontos de extremidade do Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="58b40-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="58b40-104">*Aplicável à: Administração do Office 365*</span><span class="sxs-lookup"><span data-stu-id="58b40-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="58b40-p101">**Resumo:** O Office 365 requer conectividade à Internet. Os pontos de extremidade abaixo devem ser alcançados para clientes usando apenas planos do **Office 365 Alemanha** .</span><span class="sxs-lookup"><span data-stu-id="58b40-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="58b40-p102">A Microsoft está desenvolvendo um serviço web baseado em REST para o endereço IP e as entradas de FQDN nesta página. Esse novo serviço ajudará você a configurar e atualizar os dispositivos de perímetro de rede, como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista, ou alterações específicas. Esse serviço eventualmente substituirão o documento XML, RSS feed e o endereço IP e as entradas de FQDN nesta página. Para testar esse novo serviço, vá para o [serviço Web](managing-office-365-endpoints.md#webservice).</span><span class="sxs-lookup"><span data-stu-id="58b40-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
 <span data-ttu-id="58b40-112">**Pontos de extremidade do office 365:** [Worldwide (incluindo GCC)](urls-and-ip-address-ranges.md)   |  [Office 365 operado pela Vianet 21](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Alemanha* | [Office 365 US governamentais DoD](office-365-u-s-government-dod-endpoints.md) | [Alta de GCC do governo dos EUA Office 365](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="58b40-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="58b40-113">**Última atualização:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [lista de alterações para os pontos de extremidade do Office 365 Alemanha](office-365-germany-endpoints-change-log.md)</span><span class="sxs-lookup"><span data-stu-id="58b40-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [List of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md)</span></span>||

<span data-ttu-id="58b40-p103">Comece com [pontos de extremidade de gerenciamento do Office 365](managing-office-365-endpoints.md) entender as nossas recomendações para o gerenciamento de conectividade de rede usando esses dados. Dados de pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicadas 30 dias antes de começar a sendo ativo. Isso permite que os clientes que ainda não tenham automatizada atualizações para concluir seus processos antes que é necessária a conectividade do nova. Pontos de extremidade também podem ser atualizados durante o mês, se necessário para questões de suporte de endereço, incidentes de segurança ou outros requisitos operacionais imediatos. Você sempre pode consultar a [lista de alterações para os pontos de extremidade do Office 365 Alemanha](office-365-germany-endpoints-change-log.md).</span><span class="sxs-lookup"><span data-stu-id="58b40-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. You can always refer to the [list of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md).</span></span>

<span data-ttu-id="58b40-p104">Os dados mostrados nesta página abaixo são gerados a partir de serviços da web baseado em REST. Se você estiver usando um script ou um dispositivo de rede para acessar esses dados, você deve ir diretamente para o [serviço Web](managing-office-365-endpoints.md#webservice) .</span><span class="sxs-lookup"><span data-stu-id="58b40-p104">The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="58b40-p105">Dados de ponto de extremidade abaixo lista os requisitos para a conectividade da máquina de um usuário para o Office 365. Ele não inclui as conexões de rede da Microsoft em uma rede de cliente, às vezes chamado de híbrido ou conexões de rede de entrada.</span><span class="sxs-lookup"><span data-stu-id="58b40-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="58b40-p106">Os pontos de extremidade são agrupados em quatro áreas de serviço. As áreas de serviço de três primeira independentemente podem ser selecionadas para conectividade. Área de serviço quarta é uma dependência comuns (chamada Microsoft 365 comuns e Online do Office) e sempre deve ter conectividade de rede.</span><span class="sxs-lookup"><span data-stu-id="58b40-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="58b40-126">Colunas de dados mostradas são:</span><span class="sxs-lookup"><span data-stu-id="58b40-126">Data columns shown are:</span></span>

- <span data-ttu-id="58b40-p107">**ID**: número de identificação da linha, também conhecida como um conjunto de pontos de extremidade. Este ID é a mesma que é retornado pelo serviço da web para o conjunto de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="58b40-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="58b40-p108">**Categoria**: mostra se o conjunto de ponto de extremidade é classificado como "Otimizar", "Permitir" ou "Padrão". Você pode ler sobre essas categorias e orientação para o gerenciamento deles em [http://aka.ms/pnc](http://aka.ms/pnc). Essa coluna também lista quais conjuntos de ponto de extremidade são necessários para a conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para ter conectividade de rede, nós fornecemos anotações neste campo para indicar qual funcionalidade seria ausente se o conjunto de ponto de extremidade está bloqueado. Se você estiver excluindo uma área de todo o serviço, os conjuntos de ponto de extremidade listados conforme exigido não exigem conectividade.</span><span class="sxs-lookup"><span data-stu-id="58b40-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="58b40-p109">**ER**: esse é **Sim** , se o conjunto de ponto de extremidade é suportado pela ExpressRoute Azure com prefixos de rota do Office 365. Comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área de serviço listada. Quando ER for **não**, isso significa que ExpressRoute não é suportado para este conjunto de ponto de extremidade. No entanto, ele não deve ser presumido que não há rotas são anunciadas para um conjunto de pontos de extremidade onde ER é **não**.</span><span class="sxs-lookup"><span data-stu-id="58b40-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="58b40-p110">**Endereços**: lista os FQDNs ou nomes de domínio de curinga e intervalos de endereço IP para o conjunto de pontos de extremidade. Observe que um intervalo de endereços IP está no formato CIDR e pode incluir muitos endereços IP individuais na rede especificada.</span><span class="sxs-lookup"><span data-stu-id="58b40-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="58b40-p111">**Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você pode observar algumas duplicação em intervalos de endereço IP onde há portas diferentes listadas.</span><span class="sxs-lookup"><span data-stu-id="58b40-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

