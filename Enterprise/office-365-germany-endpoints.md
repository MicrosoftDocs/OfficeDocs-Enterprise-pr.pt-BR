---
title: Pontos de extremidade do Office 365 Alemanha
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/28/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Se sua organização usa o Office 365 e impede que os computadores na sua rede se conectem à Internet, abaixo você encontrará os pontos de extremidade (FQDNs, portas, URLs e intervalos de endereços IPv4 e IPv6) que devem ser incluídos nas listas de permissão de saída para garantir que o seu os computadores podem usar o Office 365 com êxito.
hideEdit: true
ms.openlocfilehash: 5b87403f0173567d249e3350ef1913378bf1c358
ms.sourcegitcommit: 653bd752db6be18f2f0d31e5abeb8ad734704772
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "37765742"
---
# <a name="office-365-germany-endpoints"></a>Pontos de extremidade do Office 365 Alemanha

 *Aplica-se a: administrador do Office 365*

**Resumo:** O Office 365 requer conectividade com a Internet. Os pontos de extremidade abaixo devem ser acessíveis para os clientes que usam apenas planos da **Alemanha do Office 365** .
  
> [!NOTE]
> A Microsoft lançou um serviço web baseado em REST para as entradas de endereço IP e FQDN desta página. Esse novo serviço ajudará você a configurar e atualizar dispositivos de perímetro de rede como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista ou alterações específicas. Este serviço substitui o documento XML desta página, que foi preterido em 2 de outubro de 2018. Para experimentar o novo serviço, acesse [serviço Web](office-365-ip-web-service.md).
 
 **Pontos de extremidade do Office 365:** [global (incluindo GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operado pela 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Alemanha*  |  [Office 365 Governo dos E.U.A. Departamento de Defesa](office-365-u-s-government-dod-endpoints.md) | [GCC High do Office 365 Governo dos E.U.A. ](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Última atualização:** 10/28/2019- ![](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [assinatura de log de alteração](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS |**Baixar:** todos os destinos obrigatórios e opcionais em uma lista [no formato em JSON](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> |

Comece com o [Gerenciamento de pontos de extremidade do Office 365](managing-office-365-endpoints.md) para entender nossas recomendações de gerenciamento de conectividade de rede usando esses dados. Os dados de pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicados 30 dias antes de estarem ativos. Isso permite que os clientes que ainda não tenham atualizações automatizadas concluam seus processos antes que uma nova conectividade seja necessária. Os pontos de extremidade também podem ser atualizados durante o mês, se necessário para lidar com escalonamentos de suporte, incidentes de segurança ou outros requisitos operacionais imediatos. Você sempre pode consultar a [assinatura do log de alterações](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Os dados mostrados nesta página abaixo são todos gerados a partir dos serviços Web baseados em REST. Se você estiver usando um script ou um dispositivo de rede para acessar esses dados, vá diretamente para o [serviço Web](office-365-ip-web-service.md) .

Os dados dos pontos de extremidade abaixo listam requisitos de conectividade do computador de um usuário para o Office 365. Eles não incluem conexões de rede da Microsoft com uma rede de clientes, que são algumas vezes chamadas conexões de rede híbridas ou de entrada.

Os pontos de extremidade são agrupados em quatro áreas de serviço. As primeiras três áreas de serviço podem ser selecionadas independentemente de conectividade. A quarta área de serviço é uma dependência comum (chamada de Microsoft 365 Common and Office) e deve ter sempre conectividade de rede.

As colunas de dados exibidas são:

- **ID**: O número de ID da linha, também conhecido como um conjunto de pontos de extremidade. Esse ID é o mesmo que é retornado pelo serviço web ao conjunto de pontos de extremidade.

- **Categoria**: mostra se o conjunto de pontos de extremidade é categorizado como "Otimizar", "Permitir" ou "Padrão". Leia sobre essas categorias e diretrizes para gerenciamento de todos eles em [ http://aka.ms/pnc ](http://aka.ms/pnc). Esta coluna também lista quais conjuntos de ponto de extremidade são necessários para que haja conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para que haja conectividade de rede, fornecemos notas nesse campo para indicar qual funcionalidade estaria ausente se o conjunto de pontos de extremidade estiver bloqueado. Se você estiver excluindo uma área de serviço inteira, os conjuntos de pontos de extremidade listados como necessários não vão precisar de conectividade.

- **ER**: Aqui, você verá um **Sim** se o conjunto de pontos de extremidade tem suporte no Azure ExpressRoute com prefixos de rota do Office 365. A comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área do serviço listada. Quando o ER estiver marcado como**Não**, isso significa que o ExpressRoute não é suportado para esse conjunto de pontos de extremidade. No entanto, não devemos presumir que não existem rotas anunciadas para um conjunto de ponto de extremidade onde ER está marcado como **Não**.

- **Endereços**: lista os FQDNs ou nomes de domínio curinga e intervalos de endereços IP para o conjunto de pontos de extremidade. Observe que o intervalo de endereços IP está no formato CIDR e pode incluir vários endereços IP individuais na rede especificada.
 
- **Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você poderá notar algumas duplicações nos intervalos de endereços IP em que há diferentes portas listadas.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

