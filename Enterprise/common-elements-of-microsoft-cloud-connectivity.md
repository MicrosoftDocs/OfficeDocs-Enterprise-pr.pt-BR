---
title: Elementos comuns da conectividade de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 'Resumo: Entenda os elementos comuns da infraestrutura de rede e como preparar sua rede.'
ms.openlocfilehash: 27a83217e94d6a0f882825c57346b58ea1834443
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="e8bf8-103">Elementos comuns da conectividade de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="e8bf8-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="e8bf8-104">**Resumo:** Compreenda os elementos comuns da infraestrutura de rede e como preparar sua rede.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="e8bf8-105">A integração da sua rede com a nuvem da Microsoft oferece um acesso excelente a uma ampla gama de serviços.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="e8bf8-106">Etapas para preparar sua rede para serviços de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="e8bf8-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="e8bf8-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="e8bf8-107"></span></span>

<span data-ttu-id="e8bf8-108">Para a sua rede local:</span><span class="sxs-lookup"><span data-stu-id="e8bf8-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="e8bf8-109">Analisar os computadores cliente e otimizar para drivers de software, hardware de rede, as configurações de protocolo e navegadores da Internet.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="e8bf8-110">Analise sua rede local para latência de tráfego e roteamento ideal para o dispositivo de borda de Internet.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="e8bf8-111">Analisar a capacidade e o desempenho do seu dispositivo de borda de Internet e otimizar para níveis mais altos de tráfego.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="e8bf8-112">Para sua conexão de Internet:</span><span class="sxs-lookup"><span data-stu-id="e8bf8-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="e8bf8-113">Analise a latência entre seu dispositivo de borda da Internet (por exemplo, seu firewall externo) e os locais regionais do serviço de nuvem da Microsoft para o qual você está se conectando.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="e8bf8-p101">Analisar a capacidade e a utilização de sua conexão de Internet atual e adicionar capacidade, se necessário. Como alternativa, adicione uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="e8bf8-116">Opções de conectividade do Microsoft cloud</span><span class="sxs-lookup"><span data-stu-id="e8bf8-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="e8bf8-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="e8bf8-117"></span></span>

<span data-ttu-id="e8bf8-118">Use seu pipe Internet existente ou uma conexão ExpressRoute ao Office 365, Windows Azure e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="e8bf8-119">**Figura 1: Opções para conectividade de nuvem da Microsoft**</span><span class="sxs-lookup"><span data-stu-id="e8bf8-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Figura 1:  Opções para a conectividade de nuvem da Microsoft](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="e8bf8-p102">A Figura 1 mostra como uma rede local pode ser conectada para ofertas de nuvem da Microsoft usando seus pipe de Internet existente ou ExpressRoute. O pipe Internet representa uma DMZ e pode ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="e8bf8-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="e8bf8-p103">**Firewall interno:** Uma barreira entre sua rede confiável e um não confiável. Realiza a filtragem de tráfego (com base nas regras) e monitoramento.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="e8bf8-125">**a carga de trabalho externa:** Sites da Web ou outras cargas de trabalho disponibilizado para usuários externos na Internet.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="e8bf8-p104">**Servidor proxy:** Serviços de solicitações de conteúdo da web em nome de usuários da intranet. Um proxy reverso permite que as solicitações de entrada não solicitadas.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="e8bf8-p105">**Firewall externo:** Permite que o tráfego de saída e o tráfego de entrada especificado. Pode executar a conversão de endereço.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="e8bf8-130">**Conexão WAN para ISP:** Uma conexão para um ISP, quem peers com a Internet para conectividade e roteamento baseado em operadora.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="e8bf8-131">Áreas de rede comuns a todos os serviços de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="e8bf8-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="e8bf8-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="e8bf8-132"></span></span>

<span data-ttu-id="e8bf8-133">Você precisa considerar nessas áreas de rede quando a adoção de qualquer um dos serviços de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="e8bf8-134">**Desempenho intranet:** Desempenho aos recursos baseados em Internet sofrerá se sua intranet, incluindo os computadores clientes, não está otimizado.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="e8bf8-135">**Dispositivos de borda:** Dispositivos na extremidade de sua rede são os pontos de saída e podem incluir conversores de endereço de rede (NATs), servidores de proxy (incluindo proxies reversos), firewalls, dispositivos de detecção de invasão ou uma combinação.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="e8bf8-p106">**Conexão de Internet:** Sua conexão WAN para seu ISP e a Internet deve ter capacidade suficiente para lidar com cargas de pico. Você também pode usar uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="e8bf8-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR e outros registros para localizar nuvem da Microsoft ou seus serviços hospedados na nuvem. Por exemplo, talvez seja necessário um registro CNAME para seu aplicativo hospedado no Windows Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="e8bf8-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e8bf8-140">See Also</span><span class="sxs-lookup"><span data-stu-id="e8bf8-140">See Also</span></span>

<span data-ttu-id="e8bf8-141"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="e8bf8-141"></span></span>

[<span data-ttu-id="e8bf8-142">Microsoft Cloud Networking para arquitetos da empresa</span><span class="sxs-lookup"><span data-stu-id="e8bf8-142">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="e8bf8-143">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="e8bf8-143">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="e8bf8-144">Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="e8bf8-144">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


