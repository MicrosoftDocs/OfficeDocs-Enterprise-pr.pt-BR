---
title: Elementos comuns de conectividade de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 'Resumo: entenda os elementos comuns da infraestrutura de rede e como preparar sua rede.'
ms.openlocfilehash: f092e3fb0a2f009aa7c6bbb14229fe98b35700ea
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068107"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="05b36-103">Elementos comuns de conectividade de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="05b36-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="05b36-104">**Resumo:** Compreenda os elementos comuns da infraestrutura de rede e como preparar sua rede.</span><span class="sxs-lookup"><span data-stu-id="05b36-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="05b36-105">A integração da sua rede com a nuvem da Microsoft oferece um acesso excelente a uma ampla gama de serviços.</span><span class="sxs-lookup"><span data-stu-id="05b36-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="05b36-106">Etapas para preparar sua rede para os serviços do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="05b36-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="05b36-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="05b36-107"></span></span>

<span data-ttu-id="05b36-108">Para sua rede local:</span><span class="sxs-lookup"><span data-stu-id="05b36-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="05b36-109">Analise seus computadores clientes e otimize para hardware de rede, drivers de software, configurações de protocolo e navegadores da Internet.</span><span class="sxs-lookup"><span data-stu-id="05b36-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="05b36-110">Analise sua rede local quanto à latência de tráfego e o roteamento ideal para o dispositivo de borda da Internet.</span><span class="sxs-lookup"><span data-stu-id="05b36-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="05b36-111">Analise a capacidade e o desempenho do seu dispositivo de borda da Internet e otimize para níveis mais altos de tráfego.</span><span class="sxs-lookup"><span data-stu-id="05b36-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="05b36-112">Para sua conexão com a Internet:</span><span class="sxs-lookup"><span data-stu-id="05b36-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="05b36-113">Analise a latência entre o dispositivo de borda da Internet (como o firewall externo) e os locais regionais do serviço de nuvem da Microsoft para os quais você está se conectando.</span><span class="sxs-lookup"><span data-stu-id="05b36-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="05b36-114">Analise a capacidade e a utilização da sua conexão atual com a Internet e adicione a capacidade, se necessário.</span><span class="sxs-lookup"><span data-stu-id="05b36-114">Analyze the capacity and utilization of your current Internet connection and add capacity if needed.</span></span> <span data-ttu-id="05b36-115">Como alternativa, adicione uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="05b36-115">Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="05b36-116">Opções de conectividade do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="05b36-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="05b36-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="05b36-117"></span></span>

<span data-ttu-id="05b36-118">Use seu pipe de Internet existente ou uma conexão ExpressRoute para o Office 365, Azure e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="05b36-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="05b36-119">**Figura 1: opções para a conectividade de nuvem da Microsoft**</span><span class="sxs-lookup"><span data-stu-id="05b36-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Figura 1: opções para a conectividade de nuvem da Microsoft](media/Network-Poster/CommonElements.png)

  
<span data-ttu-id="05b36-121">A Figura 1 mostra como uma rede local pode ser conectada às ofertas de nuvem da Microsoft usando seu pipe existente na Internet ou o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="05b36-121">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute.</span></span> <span data-ttu-id="05b36-122">O pipe da Internet representa uma DMZ e pode ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="05b36-122">The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="05b36-123">**Firewall interno:** Uma barreira entre sua rede confiável e outra não confiável.</span><span class="sxs-lookup"><span data-stu-id="05b36-123">**Internal firewall:** A barrier between your trusted network and an untrusted one.</span></span> <span data-ttu-id="05b36-124">Realiza filtragem de tráfego (com base em regras) e monitoramento.</span><span class="sxs-lookup"><span data-stu-id="05b36-124">Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="05b36-125">**Carga de trabalho externa:** Sites da Web ou outras cargas de trabalho disponibilizadas para usuários externos na Internet.</span><span class="sxs-lookup"><span data-stu-id="05b36-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="05b36-126">**Servidor proxy:** Serviços solicitações de conteúdo da Web em nome de usuários da intranet.</span><span class="sxs-lookup"><span data-stu-id="05b36-126">**Proxy server:** Services requests for web content on behalf of intranet users.</span></span> <span data-ttu-id="05b36-127">Um proxy reverso permite solicitações de entrada não solicitadas.</span><span class="sxs-lookup"><span data-stu-id="05b36-127">A reverse proxy permits unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="05b36-128">**Firewall externo:** Permite o tráfego de saída e o tráfego de entrada especificado.</span><span class="sxs-lookup"><span data-stu-id="05b36-128">**External firewall:** Allows outbound traffic and specified inbound traffic.</span></span> <span data-ttu-id="05b36-129">Pode executar a conversão de endereços, a inspeção de pacotes, a interrupção e a inspeção de SSL ou a prevenção contra perda de dados.</span><span class="sxs-lookup"><span data-stu-id="05b36-129">Can perform address translation, packet inspection, SSL Break and Inspect, or data loss prevention.</span></span>
    
- <span data-ttu-id="05b36-130">**Conexão WAN com o ISP:** Uma conexão baseada em uma operadora a um ISP, que os colegas com a Internet para conectividade e roteamento.</span><span class="sxs-lookup"><span data-stu-id="05b36-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="05b36-131">Áreas de rede comuns a todos os serviços de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="05b36-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="05b36-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="05b36-132"></span></span>

<span data-ttu-id="05b36-133">Você precisa considerar essas áreas de rede ao adotar qualquer um dos serviços de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="05b36-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="05b36-134">**Desempenho da intranet:** O desempenho para os recursos baseados na Internet será afetado se sua intranet, incluindo computadores cliente, não estiver otimizada.</span><span class="sxs-lookup"><span data-stu-id="05b36-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="05b36-135">**Dispositivos de borda:** Os dispositivos na borda da sua rede são pontos de saída e podem incluir conversores de endereço de rede (NATs), servidores proxy (incluindo proxies inversos), firewalls, dispositivos de detecção de invasão ou uma combinação.</span><span class="sxs-lookup"><span data-stu-id="05b36-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="05b36-136">**Conexão com a Internet:** Sua conexão WAN com seu ISP e com a Internet deve ter capacidade suficiente para lidar com as cargas de pico.</span><span class="sxs-lookup"><span data-stu-id="05b36-136">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads.</span></span> <span data-ttu-id="05b36-137">Você também pode usar uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="05b36-137">You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="05b36-138">**DNS da Internet:** A, AAAA, CNAME, MX, PTR e outros registros para localizar a nuvem da Microsoft ou seus serviços hospedados na nuvem.</span><span class="sxs-lookup"><span data-stu-id="05b36-138">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud.</span></span> <span data-ttu-id="05b36-139">Por exemplo, você pode precisar de um registro CNAME para seu aplicativo hospedado na PaaS do Azure.</span><span class="sxs-lookup"><span data-stu-id="05b36-139">For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="05b36-140">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="05b36-140">Next step</span></span>

[<span data-ttu-id="05b36-141">ExpressRoute para conectividade de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="05b36-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="05b36-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="05b36-142">See also</span></span>

<span data-ttu-id="05b36-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="05b36-143"></span></span>

[<span data-ttu-id="05b36-144">Rede do Microsoft Cloud para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="05b36-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="05b36-145">Recursos de arquitetura de TI da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="05b36-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


