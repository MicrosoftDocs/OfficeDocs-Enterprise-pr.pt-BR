---
title: Configurar sua rede para o Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Resumo: consulte estes artigos para entender a rede para o Microsoft 365.'
ms.openlocfilehash: 4c414d8cbf597af9165e991a71e5d6a6a330e33a
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735650"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Configurar sua rede para o Microsoft 365

*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*

An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection. 

Use estes artigos para entender as principais diferenças e modificar seus dispositivos de borda, computadores clientes e rede local para obter o melhor desempenho para seus usuários locais.

## <a name="how-microsoft-365-networking-works"></a>Como funciona a rede Microsoft 365

Consulte estes artigos para obter uma visão geral da conectividade do Microsoft 365:

- [Visão geral da conectividade de rede do Microsoft 365](office-365-networking-overview.md)
- [Princípios de conectividade de rede do Microsoft 365](office-365-network-connectivity-principles.md)
- [Avaliando a conectividade de rede do Microsoft 365](assessing-network-connectivity.md)

Para obter conselhos sobre como melhorar o desempenho, consulte [planejamento de rede e ajuste de desempenho para o Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Suporte para redes Microsoft 365 como um fornecedor de equipamento de rede

If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions. 

## <a name="office-365-endpoints"></a>Pontos de extremidade do Office 365

Pontos de extremidade são o conjunto de endereços IP de destino, nomes de domínio do DNS e URLs do tráfego do Office 365 na Internet. 

To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.

Confira [Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md) para saber mais.

There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.

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


## <a name="additional-topics-for-microsoft-365-networking"></a>Tópicos adicionais para a rede 365 da Microsoft

Consulte estes artigos sobre tópicos especializados na rede Microsoft 365:

- [Redes de distribuição de conteúdo](content-delivery-networks.md)
- [Suporte a IPv6 nos serviços do Office 365](ipv6-support.md)
- [Suporte a NAT com o Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute para o Microsoft 365

Confira estes artigos para obter informações sobre o uso do ExpressRoute para tráfego do Office 365:

- [Microsoft Azure ExpressRoute para Office 365](azure-expressroute.md)
- [Como implementar o ExpressRoute para Office 365](implementing-expressroute.md)
- [Planejamento de rede com o ExpressRoute para Office 365](network-planning-with-expressroute.md)
- [Como rotear com o ExpressRoute para Office 365](routing-with-expressroute.md)
