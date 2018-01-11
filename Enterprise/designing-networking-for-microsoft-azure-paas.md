---
title: Projetando a rede para o Microsoft Azure PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Resumo: Entenda como otimizar sua rede para o acesso ao Microsoft Azure PaaS.'
ms.openlocfilehash: 8ea344b5c18f9224b1a939a05c6e5a4eda2eeec5
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="7931d-103">Projetando a rede para o Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="7931d-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="7931d-104">**Resumo:** Compreenda como otimizar sua rede para o acesso ao Microsoft Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="7931d-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="7931d-105">Otimizar a rede para os aplicativos PaaS do Azure exige uma largura de banda de Internet adequada e pode ainda exigir a distribuição de tráfego de rede em diversos sites ou aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7931d-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="7931d-106">Etapas de planejamento para hospedar aplicativos PaaS de organização no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="7931d-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

<span data-ttu-id="7931d-107">Insira o corpo da seção aqui.</span><span class="sxs-lookup"><span data-stu-id="7931d-107">Insert section body here.</span></span>
  
1. <span data-ttu-id="7931d-108">Percorra a seção de **etapas para preparar sua rede para serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="7931d-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="7931d-109">Otimize sua largura de banda da Internet usando as etapas 2 a 4 da seção **etapas para preparar a sua rede de serviços Microsoft SaaS** em [projetar a rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="7931d-109">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="7931d-110">Determine se você precisa de uma conexão ExpressRoute no Azure.</span><span class="sxs-lookup"><span data-stu-id="7931d-110">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="7931d-111">Para cargas de trabalho baseados na web, determine se é necessário que o Gateway de aplicativo do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="7931d-111">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="7931d-112">Para distribuição de tráfego para os pontos de extremidade diferentes em datacenters diferentes, determine se é necessário que o Gerenciador de tráfego do Azure.</span><span class="sxs-lookup"><span data-stu-id="7931d-112">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="7931d-113">Largura de banda de Internet para aplicativos de PaaS da organização</span><span class="sxs-lookup"><span data-stu-id="7931d-113">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="7931d-p101">Aplicativos de organização hospedados no Azure PaaS exigem largura de banda da Internet para os usuários da intranet. Há duas opções:</span><span class="sxs-lookup"><span data-stu-id="7931d-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="7931d-p102">**Opção 1:** Use seu pipe existente, otimizado para o tráfego da Internet com a capacidade de lidar com cargas de pico. Consulte[Projetando a rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md) para borda de Internet, uso do cliente e considerações de operações de IT.</span><span class="sxs-lookup"><span data-stu-id="7931d-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="7931d-118">**Opção 2:** Para alta largura de banda ou baixa latência necessidades, use uma conexão ExpressRoute no Azure.</span><span class="sxs-lookup"><span data-stu-id="7931d-118">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="7931d-119">**Figura 1: Opções de Conexão para conectar-se os serviços do Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="7931d-119">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![Figura 1: Opções de conexão para os serviços de PaaS do Azure](images/Network_Poster/PaaS1.png)
  
<span data-ttu-id="7931d-121">A Figura 1 mostra uma rede local conectando-se aos serviços do Azure PaaS através de uma conexão de Internet ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="7931d-121">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="7931d-122">Gateway de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="7931d-122">Azure Application Gateway</span></span>

<span data-ttu-id="7931d-123">Roteamento de nível de aplicativo e balanceamento de serviços que permitem que você construir um escalonável e altamente disponível web front-end no Windows Azure para aplicativos web, serviços em nuvem e máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="7931d-123">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="7931d-124">**Figura 2: Gateway de aplicativo do Azure**</span><span class="sxs-lookup"><span data-stu-id="7931d-124">**Figure 2: Azure Application Gateway**</span></span>

![Figura 2: Serviço de gateway do aplicativo do Azure](images/Network_Poster/PaaS2.png)
  
<span data-ttu-id="7931d-126">A Figura 2 mostra o Gateway de aplicativo do Windows Azure e como o usuário solicita da Internet pode ser roteada para os aplicativos web do Azure, serviços de nuvem ou máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="7931d-126">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="7931d-127">Application Gateway suporta atualmente o fornecimento de 7 de aplicativos de camada para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7931d-127">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="7931d-128">Balanceamento de carga HTTP</span><span class="sxs-lookup"><span data-stu-id="7931d-128">HTTP load balancing</span></span>
    
- <span data-ttu-id="7931d-129">Afinidade baseada em cookie de sessão</span><span class="sxs-lookup"><span data-stu-id="7931d-129">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="7931d-130">Descarregamento SSL</span><span class="sxs-lookup"><span data-stu-id="7931d-130">SSL offload</span></span>
    
<span data-ttu-id="7931d-131">Para obter mais informações, consulte [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span><span class="sxs-lookup"><span data-stu-id="7931d-131">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="7931d-132">Gerenciador de tráfego do Azure</span><span class="sxs-lookup"><span data-stu-id="7931d-132">Azure Traffic Manager</span></span>

<span data-ttu-id="7931d-133">Distribuição de tráfego para os pontos de extremidade diferentes, que podem incluir serviços em nuvem ou aplicativos web Azure localizados em datacenters diferentes ou pontos de extremidade externos.</span><span class="sxs-lookup"><span data-stu-id="7931d-133">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="7931d-134">Gerenciador de tráfego usa os seguintes métodos de roteamento:</span><span class="sxs-lookup"><span data-stu-id="7931d-134">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="7931d-135">**Failover:** Os pontos de extremidade estão em data centers Azure o mesmo ou diferente e você deseja usar um ponto de extremidade principal para todo o tráfego, mas fornecer backups em caso do principal ou os pontos de extremidade de backup não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7931d-135">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="7931d-136">**Rodízio:** Você deseja distribuir a carga em um conjunto de pontos de extremidade no mesmo datacenter ou em datacenters diferentes.</span><span class="sxs-lookup"><span data-stu-id="7931d-136">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="7931d-137">**Desempenho:** Você tem pontos de extremidade em diferentes locais geográficos e quiser que o solicitante aos clientes utilizarem o ponto de extremidade "mais próximo" em termos a mais baixa latência.</span><span class="sxs-lookup"><span data-stu-id="7931d-137">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="7931d-138">Aqui está um exemplo para três aplicativos da web distribuídos geograficamente.</span><span class="sxs-lookup"><span data-stu-id="7931d-138">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="7931d-139">**Figura 3: Gerenciador de tráfego do Azure**</span><span class="sxs-lookup"><span data-stu-id="7931d-139">**Figure 3: Azure Traffic Manager**</span></span>

![Figura 3: Gerenciador de tráfego do Azure](images/Network_Poster/PaaS3.png)
  
<span data-ttu-id="7931d-p103">A Figura 3 mostra o processo básico que o Gerenciador de tráfego usa para rotear solicitações para três aplicativos web Azure diferente nos Estados Unidos, Europa e Ásia. No exemplo:</span><span class="sxs-lookup"><span data-stu-id="7931d-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="7931d-143">Uma consulta DNS do usuário para um site da web que URL obtém direcionados para Azure Gerenciador de tráfego, que retorna o nome de um aplicativo web regionais, com base no método de roteamento de desempenho.</span><span class="sxs-lookup"><span data-stu-id="7931d-143">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="7931d-144">O usuário inicia o tráfego com o aplicativo web regionais na Europa.</span><span class="sxs-lookup"><span data-stu-id="7931d-144">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="7931d-145">Para obter mais informações, consulte [Gerenciador de tráfego](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="7931d-145">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7931d-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="7931d-146">See Also</span></span>

[<span data-ttu-id="7931d-147">Microsoft Cloud Networking para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="7931d-147">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="7931d-148">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="7931d-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="7931d-149">Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="7931d-149">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



