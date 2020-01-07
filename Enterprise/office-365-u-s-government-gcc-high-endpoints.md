---
title: Pontos de extremidade altos do Office 365 governo dos EUA
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 01/02/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Se sua organização usa o Office 365 e impede que os computadores na sua rede se conectem à Internet, abaixo você encontrará os pontos de extremidade (FQDNs, portas, URLs, IPv4 e intervalos de endereços IPv6) que devem ser incluídos nas listas de permissão de saída para garantir que seu os computadores podem usar o Office 365 com êxito.
hideEdit: true
ms.openlocfilehash: 9d4b0538256a2c65d299572f665c908f678b4538
ms.sourcegitcommit: f9888d1c27e38d3c489a0cbed7684a2e67c3afbd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "40951540"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Pontos de extremidade altos do Office 365 governo dos EUA

 *Aplica-se a: administrador do Office 365*

**Resumo:** O Office 365 requer conectividade com a Internet. Os pontos de extremidade abaixo devem ser acessíveis para os clientes que usam o Office 365 governo dos EUA e High Plan GCC apenas.
  
> [!NOTE]
> A Microsoft lançou um serviço web baseado em REST para as entradas de endereço IP e FQDN desta página. Esse novo serviço ajudará você a configurar e atualizar dispositivos de perímetro de rede como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista ou alterações específicas. Este serviço substitui o documento XML desta página, que foi preterido em 2 de outubro de 2018. Para experimentar o novo serviço, acesse [serviço Web](office-365-ip-web-service.md).
  
 **Pontos de extremidade do Office 365:** [global (incluindo GCC)](urls-and-ip-address-ranges.md) | [Office 365 operado pela 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Alemanha](office-365-germany-endpoints.md)   |  [Office 365 Governo dos E.U.A. Departamento de Defesa](office-365-u-s-government-dod-endpoints.md) | *GCC High do Office 365 Governo dos E.U.A. * |
  
|||
|:-----|:-----|
|**Última atualização:** 01/02/2020- ![](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [assinatura de log de alteração](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS <br/> |**Baixar:** a lista completa no [formato JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Comece com o [Gerenciamento de pontos de extremidade do Office 365](managing-office-365-endpoints.md) para entender nossas recomendações de gerenciamento de conectividade de rede usando esses dados. Os dados de pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicados 30 dias antes de estarem ativos. Isso permite que os clientes que ainda não tenham atualizações automatizadas concluam seus processos antes que uma nova conectividade seja necessária. Os pontos de extremidade também podem ser atualizados durante o mês, se necessário para lidar com escalonamentos de suporte, incidentes de segurança ou outros requisitos operacionais imediatos. Os dados mostrados nesta página abaixo são todos gerados a partir dos serviços Web baseados em REST. Se você estiver usando um script ou um dispositivo de rede para acessar esses dados, vá diretamente para o [serviço Web](office-365-ip-web-service.md) .

Os dados dos pontos de extremidade abaixo listam requisitos de conectividade do computador de um usuário para o Office 365. Eles não incluem conexões de rede da Microsoft com uma rede de clientes, que são algumas vezes chamadas conexões de rede híbridas ou de entrada.

Os pontos de extremidade são agrupados em quatro áreas de serviço. As primeiras três áreas de serviço podem ser selecionadas independentemente de conectividade. A quarta área de serviço é uma dependência comum (chamada de Microsoft 365 Common and Office) e deve ter sempre conectividade de rede.

As colunas de dados exibidas são:

- **ID**: O número de ID da linha, também conhecido como um conjunto de pontos de extremidade. Esse ID é o mesmo que é retornado pelo serviço web ao conjunto de pontos de extremidade.

- **Categoria**: mostra se o conjunto de pontos de extremidade é categorizado como "Otimizar", "Permitir" ou "Padrão". Leia sobre essas categorias e diretrizes para gerenciamento de todos eles em [ https://aka.ms/pnc ](https://aka.ms/pnc). Esta coluna também lista quais conjuntos de ponto de extremidade são necessários para que haja conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para que haja conectividade de rede, fornecemos notas nesse campo para indicar qual funcionalidade estaria ausente se o conjunto de pontos de extremidade estiver bloqueado. Se você estiver excluindo uma área de serviço inteira, os conjuntos de pontos de extremidade listados como necessários não vão precisar de conectividade.

- **Er**: **Sim** se o conjunto de pontos de extremidade for compatível com o Azure ExpressRoute com prefixos de rota do Office 365. A Comunidade BGP que inclui os prefixos de rota mostrada é alinhada com a área de serviço listada. Quando ER é **não**, isso significa que o ExpressRoute não é suportado para este conjunto de pontos de extremidade. No entanto, não deve ser considerado que nenhuma rota é anunciada para um conjunto de pontos de extremidade em que a ER é **não**. Se você planeja usar o Azure AD Connect, leia a [seção considerações especiais](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) para garantir que você tenha a configuração apropriada do Azure ad Connect.

- **Endereços**: lista os FQDNs ou nomes de domínio curinga e intervalos de endereços IP para o conjunto de pontos de extremidade. Observe que o intervalo de endereços IP está no formato CIDR e pode incluir vários endereços IP individuais na rede especificada.
 
- **Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você poderá notar algumas duplicações nos intervalos de endereços IP em que há diferentes portas listadas.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Observações da tabela:

- O centro de segurança e conformidade (SCC) oferece suporte para o Azure ExpressRoute para Office 365. O mesmo se aplica a vários recursos expostos por meio de SCC, como relatórios, auditoria, descoberta eletrônica avançada, DLP unificada e governança de dados. Dois recursos específicos, importação de PST e exportação de descoberta eletrônica, atualmente não suportam o Azure ExpressRoute com apenas filtros de rota do Office 365 devido à sua dependência no armazenamento de blob do Azure. Para consumir esses recursos, você precisa de conectividade separada para o armazenamento de blob do Azure usando as opções de conectividade do Azure compatíveis, que incluem a conectividade com a Internet ou o Azure ExpressRoute com filtros de rotas públicas do Azure. Você precisa avaliar o estabelecimento dessa conectividade para ambos os recursos. A equipe de proteção de informações do Office 365 está ciente dessa limitação e está trabalhando ativamente para trazer suporte para o Azure ExpressRoute para Office 365 como limitado aos filtros de rotas do Office 365 para ambos os recursos.

- Há pontos de extremidade opcionais adicionais para o Office 365 ProPlus que não estão listados e não são necessários para que os usuários iniciem aplicativos do Office 365 ProPlus e editem documentos. Os pontos de extremidade opcionais são hospedados em datacenters da Microsoft e não processam, transmitem ou armazenam dados do cliente. Recomendamos que as conexões de usuário para esses pontos de extremidade sejam direcionadas para o perímetro de saída da Internet padrão.

