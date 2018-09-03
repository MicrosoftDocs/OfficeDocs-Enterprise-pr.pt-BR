---
title: 'URLs e intervalos de endereço IP do Office 365 '
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Resumo: o Office 365 requer conectividade com a Internet. Os pontos de extremidade abaixo devem estar acessíveis para os clientes que usam os planos do Office 365, incluindo a Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: 2e6f5afd097aa85c09847b58fd3166961116b773
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539444"
---
# <a name="office-365-urls-and-ip-address-ranges"></a><span data-ttu-id="2cb1d-104">URLs e intervalos de endereço IP do Office 365 </span><span class="sxs-lookup"><span data-stu-id="2cb1d-104">Office 365 URLs and IP address ranges</span></span>

 <span data-ttu-id="2cb1d-p102">**Resumo:** o Office 365 requer conectividade com a Internet. Os pontos de extremidade abaixo devem estar acessíveis para os clientes que usam os planos do Office 365, incluindo a Government Community Cloud (GCC).</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p102">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2cb1d-p103">A Microsoft está desenvolvendo um serviço web baseado em REST para o endereço IP e entradas FQDN desta página. Este novo serviço ajudará você a configurar e atualizar dispositivos de perímetro de rede como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista ou alterações específicas. Este serviço substituirá o documento XML desta página. Para experimentar o novo serviço, acesse [serviço Web](managing-office-365-endpoints.md#webservice).</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p103">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document linked from this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
<span data-ttu-id="2cb1d-112">*Office 365 Worldwide (+GCC)* | [Office 365 operado pela 21 Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Alemanha](office-365-germany-endpoints.md) | [Office 365 Departamento de Defesa do Governo dos E.U.A.](office-365-u-s-government-dod-endpoints.md)  | [Office 365 GCC Alta do Governo dos E.U.A.](office-365-u-s-government-gcc-high-endpoints.md) |</span><span class="sxs-lookup"><span data-stu-id="2cb1d-112">*Office 365 Worldwide (+GCC)* | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="2cb1d-113">**Última atualização:** 1/8/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Assinatura do registro de alterações](https://go.microsoft.com/fwlink/p/?linkid=236301)</span><span class="sxs-lookup"><span data-stu-id="2cb1d-113">**Last updated:** 8/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://go.microsoft.com/fwlink/p/?linkid=236301)</span></span> <br/> |<span data-ttu-id="2cb1d-114">**Baixar:** todos os destinos obrigatórios e opcionais em uma lista [no formato em XML ](https://go.microsoft.com/fwlink/?LinkId=533185).</span><span class="sxs-lookup"><span data-stu-id="2cb1d-114">**Download:** all required and optional destinations in one [XML formatted](https://go.microsoft.com/fwlink/?LinkId=533185) list.</span></span>  <br/> | <span data-ttu-id="2cb1d-115">**Use:** nossos arquivos proxy [PAC](managing-office-365-endpoints.md#pacfiles)</span><span class="sxs-lookup"><span data-stu-id="2cb1d-115">**Use:** our proxy [PAC files](managing-office-365-endpoints.md#pacfiles)</span></span> <br/> |
   
 <span data-ttu-id="2cb1d-p104">Comece com [Gerenciar os pontos de extremidade do Office 365](managing-office-365-endpoints.md) para entender nossas recomendações para gerenciar a conectividade de rede usando estes dados. Os dados dos pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicadas 30 dias antes de se tornarem ativas. Isso permite que os clientes que ainda não têm atualizações automáticas completem seus processos antes de precisarem de nova conectividade. Os pontos de extremidade também podem ser atualizados durante o mês, se necessário, para tratar de escalações de suporte, incidentes de segurança ou outros requisitos operacionais imediatos. Todos os dados exibidos abaixo nesta página são gerados a partir dos serviços web baseados em REST. Se estiver usando um script ou dispositivo de rede para acessar esses dados, vá diretamente para o [serviço Web](managing-office-365-endpoints.md#webservice).</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p104">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="2cb1d-p105">Os dados dos pontos de extremidade abaixo listam requisitos de conectividade do computador de um usuário para o Office 365. Eles não incluem conexões de rede da Microsoft com uma rede de clientes, que são algumas vezes chamadas conexões de rede híbridas ou de entrada.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="2cb1d-p106">Os pontos de extremidade são agrupados em quatro áreas de serviço. As primeiras três áreas de serviço podem ser selecionadas independentemente de conectividade. A quarta área de serviço é uma dependência comum (chamada de Microsoft 365 Comum e Office Online) e deve ter sempre conectividade de rede.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="2cb1d-127">As colunas de dados exibidas são:</span><span class="sxs-lookup"><span data-stu-id="2cb1d-127">Data columns shown are:</span></span>

- <span data-ttu-id="2cb1d-p107">**ID**: O número de ID da linha, também conhecido como um conjunto de pontos de extremidade. Esse ID é o mesmo que é retornado pelo serviço web ao conjunto de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="2cb1d-p108">**Categoria**: mostra se o conjunto de pontos de extremidade é categorizado como "Otimizar", "Permitir" ou "Padrão". Leia sobre essas categorias e diretrizes para gerenciamento de todos eles em [ http://aka.ms/pnc ](http://aka.ms/pnc). Esta coluna também lista quais conjuntos de ponto de extremidade são necessários para que haja conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para que haja conectividade de rede, fornecemos notas nesse campo para indicar qual funcionalidade estaria ausente se o conjunto de pontos de extremidade estiver bloqueado. Se você estiver excluindo uma área de serviço inteira, os conjuntos de pontos de extremidade listados como necessários não vão precisar de conectividade.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="2cb1d-p109">**ER**: Aqui, você verá um **Sim** se o conjunto de pontos de extremidade tem suporte no Azure ExpressRoute com prefixos de rota do Office 365. A comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área do serviço listada. Quando o ER estiver marcado como**Não**, isso significa que o ExpressRoute não é suportado para esse conjunto de pontos de extremidade. No entanto, não devemos presumir que não existem rotas anunciadas para um conjunto de ponto de extremidade onde ER está marcado como **Não**.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="2cb1d-p110">**Endereços**: lista os FQDNs ou nomes de domínio curinga e intervalos de endereços IP para o conjunto de pontos de extremidade. Observe que o intervalo de endereços IP está no formato CIDR e pode incluir vários endereços IP individuais na rede especificada.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="2cb1d-p111">**Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você poderá notar algumas duplicações nos intervalos de endereços IP em que há diferentes portas listadas.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

## <a name="related-topics"></a><span data-ttu-id="2cb1d-143">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="2cb1d-143">Related Topics</span></span>

[<span data-ttu-id="2cb1d-144">Gerenciar pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="2cb1d-144">Office 365 Germany endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="2cb1d-145">Solucionar problemas de conectividade do Office 365</span><span class="sxs-lookup"><span data-stu-id="2cb1d-145">Office 365 connectivity limits</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[<span data-ttu-id="2cb1d-146">Conectividade de cliente</span><span class="sxs-lookup"><span data-stu-id="2cb1d-146">Client connectivity</span></span>](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[<span data-ttu-id="2cb1d-147">Redes de distribuição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2cb1d-147">Content delivery networks</span></span>](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[<span data-ttu-id="2cb1d-148">Intervalos de IP do Datacenter do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2cb1d-148">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="2cb1d-149">Grupos de notícias públicos da Microsoft</span><span class="sxs-lookup"><span data-stu-id="2cb1d-149">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)

