---
title: Intervalos de URLs e endereços IP do Office 365 operados pela 21Vianet
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
description: Este artigo se aplica ao Office 365 operado pela 21Vianet na China. Este artigo lista as URLs e intervalos de endereços IP usados pelo Office 365 operado pela 21Vianet.
hideEdit: true
ms.openlocfilehash: 9767b231a815ef08a97feaa412aee8c5e43c556e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539133"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>Intervalos de URLs e endereços IP do Office 365 operados pela 21Vianet

 *Aplica-se a: Office 365 operado pela 21Vianet - Administrador de Pequenas Empresas, Office 365 operado pela 21Vianet - Administrador*

**Resumo**: os pontos de extremidade a seguir (FQDNs, portas, URLs, prefixos IPv4 e IPv6) se aplicam ao Office 365 operado pela 21 Vianet e são projetados para entregar serviços de produtividade às organizações que usam somente esses planos.
  
> [!NOTE]
> A Microsoft está desenvolvendo um serviço web baseado em REST para o endereço IP e entradas FQDN desta página. Este novo serviço ajudará você a configurar e atualizar dispositivos de perímetro de rede como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista ou alterações específicas. Este serviço substituirá o documento XML desta página. Para experimentar o novo serviço, acesse [serviço Web](managing-office-365-endpoints.md#webservice). 
  
 **Pontos de extremidade do Office 365:** [global (incluindo GCC)](urls-and-ip-address-ranges.md)  | *Office 365 operado pela 21 Vianet* | [Office 365 Alemanha](office-365-germany-endpoints.md)  |  [Office 365 Governo dos E.U.A. Departamento de Defesa](office-365-u-s-government-dod-endpoints.md) | [GCC High do Office 365 Governo dos E.U.A. ](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Última atualização:** 1/8/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Assinatura do registro de alterações](http://go.microsoft.com/fwlink/?LinkId=536386)||

Comece com [Gerenciar os pontos de extremidade do Office 365](managing-office-365-endpoints.md) para entender nossas recomendações para gerenciar a conectividade de rede usando estes dados. Os dados dos pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicadas 30 dias antes de se tornarem ativas. Isso permite que os clientes que ainda não têm atualizações automáticas completem seus processos antes de precisarem de nova conectividade. Os pontos de extremidade também podem ser atualizados durante o mês, se necessário, para tratar de escalações de suporte, incidentes de segurança ou outros requisitos operacionais imediatos. Todos os dados exibidos abaixo nesta página são gerados a partir dos serviços web baseados em REST. Se estiver usando um script ou dispositivo de rede para acessar esses dados, vá diretamente para o [serviço Web](managing-office-365-endpoints.md#webservice).

Os dados dos pontos de extremidade abaixo listam requisitos de conectividade do computador de um usuário para o Office 365. Eles não incluem conexões de rede da Microsoft com uma rede de clientes, que são algumas vezes chamadas conexões de rede híbridas ou de entrada.

Os pontos de extremidade são agrupados em quatro áreas de serviço. As primeiras três áreas de serviço podem ser selecionadas independentemente de conectividade. A quarta área de serviço é uma dependência comum (chamada de Microsoft 365 Comum e Office Online) e deve ter sempre conectividade de rede.

As colunas de dados exibidas são:

- **ID**: O número de ID da linha, também conhecido como um conjunto de pontos de extremidade. Esse ID é o mesmo que é retornado pelo serviço web ao conjunto de pontos de extremidade.

- **Categoria**: mostra se o conjunto de pontos de extremidade é categorizado como "Otimizar", "Permitir" ou "Padrão". Leia sobre essas categorias e diretrizes para gerenciamento de todos eles em [ http://aka.ms/pnc ](http://aka.ms/pnc). Esta coluna também lista quais conjuntos de ponto de extremidade são necessários para que haja conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para que haja conectividade de rede, fornecemos notas nesse campo para indicar qual funcionalidade estaria ausente se o conjunto de pontos de extremidade estiver bloqueado. Se você estiver excluindo uma área de serviço inteira, os conjuntos de pontos de extremidade listados como necessários não vão precisar de conectividade.

- **ER**: Aqui, você verá um **Sim** se o conjunto de pontos de extremidade tem suporte no Azure ExpressRoute com prefixos de rota do Office 365. A comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área do serviço listada. Quando o ER estiver marcado como**Não**, isso significa que o ExpressRoute não é suportado para esse conjunto de pontos de extremidade. No entanto, não devemos presumir que não existem rotas anunciadas para um conjunto de ponto de extremidade onde ER está marcado como **Não**.

- **Endereços**: lista os FQDNs ou nomes de domínio curinga e intervalos de endereços IP para o conjunto de pontos de extremidade. Observe que o intervalo de endereços IP está no formato CIDR e pode incluir vários endereços IP individuais na rede especificada.
 
- **Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você poderá notar algumas duplicações nos intervalos de endereços IP em que há diferentes portas listadas.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](./includes/office-365-operated-by-21vianet-endpoints.md)]

