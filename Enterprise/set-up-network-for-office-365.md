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
ms.openlocfilehash: 6fb1d4d441719f61886b9263b30cdf27cbe7eaf4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070817"
---
# <a name="set-up-your-network-for-office-365"></a><span data-ttu-id="c1ee6-103">Configure sua rede para o Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-103">Set up your network for Office 365</span></span>

<span data-ttu-id="c1ee6-104">\*\*Resumo: \*\*Confira estes artigos para entender a rede do Office 365.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-104">**Summary:** See these articles to understand networking for Office 365.</span></span>
  
<span data-ttu-id="c1ee6-p101">Uma parte importante da sua integração do Office 365 é garantir que suas conexões de rede e Internet sejam configuradas para o melhor acesso. Configurar sua rede local para acessar uma nuvem globalmente distribuída tipo Software Como Serviço (SaaS) é diferente de uma rede tradicional que é otimizada para o tráfego para centros de dados locais.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-p101">An important part of your Office 365 onboarding is to first ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters.</span></span> 

<span data-ttu-id="c1ee6-107">Use estes artigos para entender as diferenças importantes e para modificar os dispositivos de borda, computadores clientes e a rede local para oferecer o melhor desempenho ao usuário.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-107">Use these articles to understand the key differences and to modify your  edge devices, client computers, and on-premises network to get the best user performance.</span></span>

## <a name="how-office-365-networking-works"></a><span data-ttu-id="c1ee6-108">Como funciona a rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-108">How Office 365 networking works</span></span>

<span data-ttu-id="c1ee6-109">Confira estes artigos para obter uma visão geral de conectividade do Office 365:</span><span class="sxs-lookup"><span data-stu-id="c1ee6-109">See these articles for an overview of connectivity for Office 365:</span></span>

- [<span data-ttu-id="c1ee6-110">Visão geral da conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-110">Office 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="c1ee6-111">Princípios de conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-111">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="c1ee6-112">Conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-112">Network connectivity to Office 365</span></span>](network-connectivity.md)

<span data-ttu-id="c1ee6-113">Para conselhos sobre como aprimorar o desempenho, confira [Planejamento de rede e ajuste de desempenho do Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="c1ee6-113">For advice on enhancing performance, see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="c1ee6-114">Suporte de rede do Office 365 como fornecedor de equipamentos de rede</span><span class="sxs-lookup"><span data-stu-id="c1ee6-114">Support Office 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="c1ee6-p102">Se você é um fornecedor de equipamentos de rede, junte-se ao [Programa de Parceiros de Rede do Office 365](office-365-networking-partner-program.md). Inscreva-se no programa para integrar princípios de conectividade de rede do Office 365 aos seus produtos e soluções.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="c1ee6-117">Pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-117">Office 365 endpoints</span></span>

<span data-ttu-id="c1ee6-118">Pontos de extremidade são o conjunto de endereços IP de destino, nomes de domínio do DNS e URLs do tráfego do Office 365 na Internet.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="c1ee6-p103">Para otimizar o desempenho dos serviços do Office 365 baseados em nuvem, estes pontos de extremidade precisam de um tratamento especial por parte de seus navegadores clientes e dos dispositivos em sua rede de borda. Estes dispositivos incluem firewalls, dispositivos SSL Break and Inspect e de inspeção de pacotes e sistemas de prevenção de perda de dados.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-p103">To optimize performance to Office 365 cloud-based services, these endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="c1ee6-121">Confira [Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="c1ee6-p104">Atualmente, há cinco nuvens diferentes do Office 365. Esta tabela leva você à lista de pontos de extremidade de cada um deles.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="c1ee6-124">Pontos de extremidade mundiais</span><span class="sxs-lookup"><span data-stu-id="c1ee6-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="c1ee6-125">Os pontos de extremidade das assinaturas do Office 365 em todo o mundo, que incluem a United States Government Community Cloud (GCC).</span><span class="sxs-lookup"><span data-stu-id="c1ee6-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="c1ee6-126">Pontos de extremidade do US Government DoD</span><span class="sxs-lookup"><span data-stu-id="c1ee6-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="c1ee6-127">Os pontos de extremidade das assinaturas do Departamento de Defesa dos Estados Unidos (DoD).</span><span class="sxs-lookup"><span data-stu-id="c1ee6-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="c1ee6-128">Pontos de extremidade do US Government GCC High</span><span class="sxs-lookup"><span data-stu-id="c1ee6-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="c1ee6-129">Os pontos de extremidade das assinaturas da United States Government Community Cloud High (GCC alto).</span><span class="sxs-lookup"><span data-stu-id="c1ee6-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="c1ee6-130">Pontos de extremidade do Office 365 operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="c1ee6-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="c1ee6-131">Os pontos de extremidade do Office 365 operado pela 21Vianet, que são projetados para atender às necessidades do Office 365 na China.</span><span class="sxs-lookup"><span data-stu-id="c1ee6-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="c1ee6-132">Pontos de extremidade do Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="c1ee6-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="c1ee6-133">Os pontos de extremidade uma nuvem separada na Europa para a maioria dos clientes regulamentados na Alemanha, União Europeia (UE) e Associação Europeia de Livre Comércio (EFTA).</span><span class="sxs-lookup"><span data-stu-id="c1ee6-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="c1ee6-134">Para obter automaticamente a lista mais recente de pontos de extremidade de sua nuvem do Office 365, confira o [Serviços de Endereços IP e URLs da Web do Office 365](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="c1ee6-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="c1ee6-135">Para pontos de extremidade adicionais, confira estes artigos:</span><span class="sxs-lookup"><span data-stu-id="c1ee6-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="c1ee6-136">Pontos de extremidade adicionais não incluídos nos serviços Web</span><span class="sxs-lookup"><span data-stu-id="c1ee6-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="c1ee6-137">Solicitações de rede do Office 2016 para Mac</span><span class="sxs-lookup"><span data-stu-id="c1ee6-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a><span data-ttu-id="c1ee6-138">Outros tópicos de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-138">Additional topics for Office 365 networking</span></span>

<span data-ttu-id="c1ee6-139">Confira estes artigos para tópicos especializados na rede do Office 365:</span><span class="sxs-lookup"><span data-stu-id="c1ee6-139">See these articles for specialized topics in Office 365 networking:</span></span>

- [<span data-ttu-id="c1ee6-140">Redes de distribuição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="c1ee6-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="c1ee6-141">Suporte a IPv6 nos serviços do Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="c1ee6-142">Suporte a NAT com o Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a><span data-ttu-id="c1ee6-143">ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-143">ExpressRoute for Office 365</span></span>

<span data-ttu-id="c1ee6-144">Confira estes artigos para obter informações sobre o uso do ExpressRoute para tráfego do Office 365:</span><span class="sxs-lookup"><span data-stu-id="c1ee6-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="c1ee6-145">Microsoft Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="c1ee6-146">Como implementar o ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="c1ee6-147">Planejamento de rede com o ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="c1ee6-148">Como rotear com o ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="c1ee6-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
