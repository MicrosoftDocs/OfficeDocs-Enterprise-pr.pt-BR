---
title: Pontos de extremidade altos do Office 365 governo dos EUA
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/29/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Se sua organização usa o Office 365 e impede que os computadores na sua rede se conectem à Internet, abaixo você encontrará os pontos de extremidade (FQDNs, portas, URLs, IPv4 e intervalos de endereços IPv6) que devem ser incluídos nas listas de permissão de saída para garantir que os computadores possam usar o Office 365 com êxito.
hideEdit: true
ms.openlocfilehash: 995fb0265b3e2854b85291a8152469c3034e75a2
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997542"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Pontos de extremidade altos do Office 365 governo dos EUA

 *Aplica-se a: administrador do Office 365*

O Office 365 requer conectividade com a Internet. Os pontos de extremidade abaixo devem ser acessíveis para os clientes que usam o Office 365 governo dos EUA e High Plan GCC apenas.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Pontos de extremidade do Office 365:** [global (incluindo GCC)](urls-and-ip-address-ranges.md) | [Office 365 operado pela 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Alemanha](office-365-germany-endpoints.md)   |  [Office 365 Governo dos E.U.A. Departamento de Defesa](office-365-u-s-government-dod-endpoints.md) | *GCC High do Office 365 Governo dos E.U.A. * |
  
|||
|:-----|:-----|
|**Última atualização:** 06/29/2020- ![ ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [assinatura de log de alteração](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS <br/> |**Baixar:** a lista completa no [formato JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |

 Comece com o [Gerenciamento de pontos de extremidade do Office 365](managing-office-365-endpoints.md) para entender nossas recomendações de gerenciamento de conectividade de rede usando esses dados. Os dados de pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicados 30 dias antes de estarem ativos. Isso permite que os clientes que ainda não tenham atualizações automatizadas concluam seus processos antes que uma nova conectividade seja necessária. Os pontos de extremidade também podem ser atualizados durante o mês, se necessário para lidar com escalonamentos de suporte, incidentes de segurança ou outros requisitos operacionais imediatos. Os dados mostrados nesta página abaixo são todos gerados a partir dos serviços Web baseados em REST. Se você estiver usando um script ou um dispositivo de rede para acessar esses dados, vá diretamente para o [serviço Web](office-365-ip-web-service.md) .

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

As colunas de dados exibidas são:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **Er**: **Sim** se o conjunto de pontos de extremidade for compatível com o Azure ExpressRoute com prefixos de rota do Office 365. A Comunidade BGP que inclui os prefixos de rota mostrada é alinhada com a área de serviço listada. Quando ER é **não**, isso significa que o ExpressRoute não é suportado para este conjunto de pontos de extremidade. No entanto, não deve ser considerado que nenhuma rota é anunciada para um conjunto de pontos de extremidade em que a ER é **não**. Se você planeja usar o Azure AD Connect, leia a [seção considerações especiais](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) para garantir que você tenha a configuração apropriada do Azure ad Connect.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Observações da tabela:

- O centro de segurança e conformidade (SCC) oferece suporte para o Azure ExpressRoute para Office 365. O mesmo se aplica a vários recursos expostos por meio de SCC, como relatórios, auditoria, descoberta eletrônica avançada, DLP unificada e governança de dados. Dois recursos específicos, importação de PST e exportação de descoberta eletrônica, atualmente não suportam o Azure ExpressRoute com apenas filtros de rota do Office 365 devido à sua dependência no armazenamento de blob do Azure. Para consumir esses recursos, você precisa de conectividade separada para o armazenamento de blob do Azure usando as opções de conectividade do Azure compatíveis, que incluem a conectividade com a Internet ou o Azure ExpressRoute com filtros de rotas públicas do Azure. Você precisa avaliar o estabelecimento dessa conectividade para ambos os recursos. A equipe de proteção de informações do Office 365 está ciente dessa limitação e está trabalhando ativamente para trazer suporte para o Azure ExpressRoute para Office 365 como limitado aos filtros de rotas do Office 365 para ambos os recursos.

- Há pontos de extremidade opcionais adicionais para os aplicativos do Microsoft 365 para empresas que não estão listados e não são necessários para que os usuários iniciem aplicativos da Microsoft 365 para aplicativos corporativos e editem documentos. Os pontos de extremidade opcionais são hospedados em datacenters da Microsoft e não processam, transmitem ou armazenam dados do cliente. Recomendamos que as conexões de usuário para esses pontos de extremidade sejam direcionadas para o perímetro de saída da Internet padrão.

