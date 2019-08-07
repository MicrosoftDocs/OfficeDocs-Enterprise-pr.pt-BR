---
title: Configure sua rede para o Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Resumo: Confira estes artigos para entender a rede do Office 365.'
ms.openlocfilehash: 958841733259bd01cd16a908cfac65998a3f3127
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722680"
---
# <a name="set-up-your-network-for-office-365"></a>Configure sua rede para o Office 365

**Resumo: **Confira estes artigos para entender a rede do Office 365.
  
Uma parte importante da sua integração do Office 365 é garantir que suas conexões de rede e Internet sejam configuradas para o melhor acesso. Configurar sua rede local para acessar uma nuvem globalmente distribuída tipo Software Como Serviço (SaaS) é diferente de uma rede tradicional que é otimizada para o tráfego para centros de dados locais. 

Use estes artigos para entender as diferenças importantes e para modificar os dispositivos de borda, computadores clientes e a rede local para oferecer o melhor desempenho ao usuário.

## <a name="how-office-365-networking-works"></a>Como funciona a rede do Office 365

Confira estes artigos para obter uma visão geral de conectividade do Office 365:

- [Visão geral da conectividade de rede do Office 365](office-365-networking-overview.md)
- [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md)
- [Avaliando a conectividade de rede do Office 365](assessing-network-connectivity.md)

Para conselhos sobre como aprimorar o desempenho, confira [Planejamento de rede e ajuste de desempenho do Office 365](network-planning-and-performance.md).

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>Suporte de rede do Office 365 como fornecedor de equipamentos de rede

Se você é um fornecedor de equipamentos de rede, junte-se ao [Programa de Parceiros de Rede do Office 365](office-365-networking-partner-program.md). Inscreva-se no programa para integrar princípios de conectividade de rede do Office 365 aos seus produtos e soluções. 

## <a name="office-365-endpoints"></a>Pontos de extremidade do Office 365

Pontos de extremidade são o conjunto de endereços IP de destino, nomes de domínio do DNS e URLs do tráfego do Office 365 na Internet. 

Para otimizar o desempenho dos serviços do Office 365 baseados em nuvem, estes pontos de extremidade precisam de um tratamento especial por parte de seus navegadores clientes e dos dispositivos em sua rede de borda. Estes dispositivos incluem firewalls, dispositivos SSL Break and Inspect e de inspeção de pacotes e sistemas de prevenção de perda de dados.

Confira [Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md) para saber mais.

Atualmente, há cinco nuvens diferentes do Office 365. Esta tabela leva você à lista de pontos de extremidade de cada um deles.

|||
|:-------|:-----|
| [Pontos de extremidade mundiais](urls-and-ip-address-ranges.md) | Os pontos de extremidade das assinaturas do Office 365 em todo o mundo, que incluem a United States Government Community Cloud (GCC). |
| [Pontos de extremidade do US Government DoD](office-365-u-s-government-dod-endpoints.md) | Os pontos de extremidade das assinaturas do Departamento de Defesa dos Estados Unidos (DoD). |
| [Pontos de extremidade do US Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) | Os pontos de extremidade das assinaturas da United States Government Community Cloud High (GCC alto). |
| [Pontos de extremidade do Office 365 operado pela 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Os pontos de extremidade do Office 365 operado pela 21Vianet, que são projetados para atender às necessidades do Office 365 na China. |
| [Pontos de extremidade do Office 365 Germany](office-365-germany-endpoints.md) | Os pontos de extremidade uma nuvem separada na Europa para a maioria dos clientes regulamentados na Alemanha, União Europeia (UE) e Associação Europeia de Livre Comércio (EFTA). |
|||

Para obter automaticamente a lista mais recente de pontos de extremidade de sua nuvem do Office 365, confira o [Serviços de Endereços IP e URLs da Web do Office 365](office-365-ip-web-service.md).

Para pontos de extremidade adicionais, confira estes artigos:

- [Pontos de extremidade adicionais não incluídos nos serviços Web](additional-office365-ip-addresses-and-urls.md)
- [Solicitações de rede do Office 2016 para Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a>Outros tópicos de rede do Office 365

Confira estes artigos para tópicos especializados na rede do Office 365:

- [Redes de distribuição de conteúdo](content-delivery-networks.md)
- [Suporte a IPv6 nos serviços do Office 365](ipv6-support.md)
- [Suporte a NAT com o Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>ExpressRoute para Office 365

Confira estes artigos para obter informações sobre o uso do ExpressRoute para tráfego do Office 365:

- [Microsoft Azure ExpressRoute para Office 365](azure-expressroute.md)
- [Como implementar o ExpressRoute para Office 365](implementing-expressroute.md)
- [Planejamento de rede com o ExpressRoute para Office 365](network-planning-with-expressroute.md)
- [Como rotear com o ExpressRoute para Office 365](routing-with-expressroute.md)
