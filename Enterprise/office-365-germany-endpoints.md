---
title: Pontos de extremidade do Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
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
ms.openlocfilehash: 016fc3073ece232a0e12e298d745cd18d8e5cb9d
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872292"
---
# <a name="office-365-germany-endpoints"></a>Pontos de extremidade do Office 365 Germany

 *Aplicável à: Administração do Office 365*

**Resumo:** O Office 365 requer conectividade à Internet. Os pontos de extremidade abaixo devem ser alcançados para clientes usando apenas planos do **Office 365 Alemanha** .
  
> [!NOTE]
> A Microsoft lançou um serviço web baseado em REST para as entradas de endereço IP e FQDN desta página. Esse novo serviço ajudará você a configurar e atualizar dispositivos de perímetro de rede como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista ou alterações específicas. Este serviço substitui o documento XML desta página, que foi preterido em 2 de outubro de 2018. Para experimentar o novo serviço, acesse [serviço Web](office-365-ip-web-service.md).
  
 **Pontos de extremidade do Office 365:** [global (incluindo GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operado pela 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Alemanha*  |  [Office 365 Governo dos E.U.A. Departamento de Defesa](office-365-u-s-government-dod-endpoints.md) | [GCC High do Office 365 Governo dos E.U.A. ](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Última atualização:** 11/28/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [assinatura do Log de alterações](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**Baixar:** todos os destinos obrigatórios e opcionais em uma lista [no formato em JSON](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> |

Comece com [pontos de extremidade de gerenciamento do Office 365](managing-office-365-endpoints.md) entender as nossas recomendações para o gerenciamento de conectividade de rede usando esses dados. Dados de pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicadas 30 dias antes de começar a sendo ativo. Isso permite que os clientes que ainda não tenham automatizada atualizações para concluir seus processos antes que é necessária a conectividade do nova. Pontos de extremidade também podem ser atualizados durante o mês, se necessário para questões de suporte de endereço, incidentes de segurança ou outros requisitos operacionais imediatos. Você sempre pode consultar a [alterar a assinatura de log](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Os dados mostrados nesta página abaixo são gerados a partir de serviços da web baseado em REST. Se você estiver usando um script ou um dispositivo de rede para acessar esses dados, você deve ir diretamente para o [serviço Web](office-365-ip-web-service.md) .

Os dados dos pontos de extremidade abaixo listam requisitos de conectividade do computador de um usuário para o Office 365. Eles não incluem conexões de rede da Microsoft com uma rede de clientes, que são algumas vezes chamadas conexões de rede híbridas ou de entrada.

Os pontos de extremidade são agrupados em quatro áreas de serviço. As primeiras três áreas de serviço podem ser selecionadas independentemente de conectividade. A quarta área de serviço é uma dependência comum (chamada de Microsoft 365 Comum e Office Online) e deve ter sempre conectividade de rede.

As colunas de dados exibidas são:

- **ID**: O número de ID da linha, também conhecido como um conjunto de pontos de extremidade. Esse ID é o mesmo que é retornado pelo serviço web ao conjunto de pontos de extremidade.

- **Categoria**: mostra se o conjunto de pontos de extremidade é categorizado como "Otimizar", "Permitir" ou "Padrão". Leia sobre essas categorias e diretrizes para gerenciamento de todos eles em [ http://aka.ms/pnc ](http://aka.ms/pnc). Esta coluna também lista quais conjuntos de ponto de extremidade são necessários para que haja conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para que haja conectividade de rede, fornecemos notas nesse campo para indicar qual funcionalidade estaria ausente se o conjunto de pontos de extremidade estiver bloqueado. Se você estiver excluindo uma área de serviço inteira, os conjuntos de pontos de extremidade listados como necessários não vão precisar de conectividade.

- **ER**: Aqui, você verá um **Sim** se o conjunto de pontos de extremidade tem suporte no Azure ExpressRoute com prefixos de rota do Office 365. A comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área do serviço listada. Quando o ER estiver marcado como**Não**, isso significa que o ExpressRoute não é suportado para esse conjunto de pontos de extremidade. No entanto, não devemos presumir que não existem rotas anunciadas para um conjunto de ponto de extremidade onde ER está marcado como **Não**.

- **Endereços**: lista os FQDNs ou nomes de domínio curinga e intervalos de endereços IP para o conjunto de pontos de extremidade. Observe que o intervalo de endereços IP está no formato CIDR e pode incluir vários endereços IP individuais na rede especificada.
 
- **Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você poderá notar algumas duplicações nos intervalos de endereços IP em que há diferentes portas listadas.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

