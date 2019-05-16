---
title: Criação de rede para o Microsoft Azure PaaS
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
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Resumo: entenda como otimizar sua rede para acesso à PaaS do Microsoft Azure.'
ms.openlocfilehash: fafc3de1c5f755e891da6c07ae8993fb869bc5e1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067817"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="1e2cf-103">Criação de rede para o Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="1e2cf-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="1e2cf-104">**Resumo:** Entenda como otimizar sua rede para acessar o Microsoft Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="1e2cf-105">Otimizar a rede para os aplicativos PaaS do Azure exige uma largura de banda de Internet adequada e pode ainda exigir a distribuição de tráfego de rede em diversos sites ou aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="1e2cf-106">Planejamento de etapas de Hospedagem de aplicativos de PaaS da organização no Azure</span><span class="sxs-lookup"><span data-stu-id="1e2cf-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

1. <span data-ttu-id="1e2cf-107">Siga as **etapas para preparar sua rede para o serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="1e2cf-107">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="1e2cf-108">Otimize a largura de banda da Internet usando as etapas 2-4 das **etapas para preparar sua rede para os serviços Microsoft SaaS** no [projeto de rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="1e2cf-108">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="1e2cf-109">Determine se você precisa de uma conexão expressa para o Azure.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-109">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="1e2cf-110">Para cargas de trabalho baseadas na Web, determine se você precisa do gateway de aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-110">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="1e2cf-111">Para distribuição de tráfego para diferentes pontos de extremidade em diferentes data centers, determine se você precisa do Azure Traffic Manager.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-111">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="1e2cf-112">Largura de banda da Internet para aplicativos de PaaS da organização</span><span class="sxs-lookup"><span data-stu-id="1e2cf-112">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="1e2cf-113">Os aplicativos de organização hospedados na PaaS do Azure exigem largura de banda de Internet para usuários de intranet.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-113">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users.</span></span> <span data-ttu-id="1e2cf-114">Há duas opções:</span><span class="sxs-lookup"><span data-stu-id="1e2cf-114">There are two options:</span></span>
  
- <span data-ttu-id="1e2cf-115">**Opção 1:** Use seu pipe existente, otimizado para o tráfego de Internet com a capacidade de lidar com as cargas de pico.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-115">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads.</span></span> <span data-ttu-id="1e2cf-116">Consulte[projetando a rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md) para borda da Internet, uso do cliente e considerações sobre operações de ti.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-116">See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="1e2cf-117">**Opção 2:** Para necessidades de alta largura de banda ou baixa latência, use uma conexão ExpressRoute para o Azure.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-117">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="1e2cf-118">**Figura 1: opções de conexão para conectar os serviços do Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="1e2cf-118">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![Figura 1: opções de conexão para os serviços do Azure PaaS](media/Network-Poster/PaaS1.png)
  
<span data-ttu-id="1e2cf-120">A Figura 1 mostra uma rede local conectando-se aos serviços de PaaS do Azure em um pipe da Internet ou no ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-120">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="1e2cf-121">Gateway de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="1e2cf-121">Azure Application Gateway</span></span>

<span data-ttu-id="1e2cf-122">Roteamento de nível de aplicativo e serviços de balanceamento de carga que permitem criar um front-end da Web escalonável e altamente disponível no Azure para aplicativos Web, serviços em nuvem e máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-122">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="1e2cf-123">**Figura 2: gateway de aplicativo do Azure**</span><span class="sxs-lookup"><span data-stu-id="1e2cf-123">**Figure 2: Azure Application Gateway**</span></span>

![Figura 2: serviço do Azure Application Gateway](media/Network-Poster/PaaS2.png)
  
<span data-ttu-id="1e2cf-125">A Figura 2 mostra o gateway de aplicativo do Azure e como as solicitações de usuário da Internet podem ser roteadas para aplicativos Web do Azure, serviços em nuvem ou máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-125">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="1e2cf-126">O Application Gateway atualmente oferece suporte à entrega de aplicativos Layer 7 para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1e2cf-126">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="1e2cf-127">Balanceamento de carga HTTP</span><span class="sxs-lookup"><span data-stu-id="1e2cf-127">HTTP load balancing</span></span>
    
- <span data-ttu-id="1e2cf-128">Afinidade de sessão baseada em cookies</span><span class="sxs-lookup"><span data-stu-id="1e2cf-128">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="1e2cf-129">Descarregamento SSL</span><span class="sxs-lookup"><span data-stu-id="1e2cf-129">SSL offload</span></span>
    
<span data-ttu-id="1e2cf-130">Para obter mais informações, consulte [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span><span class="sxs-lookup"><span data-stu-id="1e2cf-130">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="1e2cf-131">Gerenciador de tráfego do Azure</span><span class="sxs-lookup"><span data-stu-id="1e2cf-131">Azure Traffic Manager</span></span>

<span data-ttu-id="1e2cf-132">Distribuição de tráfego para diferentes pontos de extremidade, que podem incluir serviços em nuvem ou aplicativos Web do Azure localizados em diferentes centros de dados ou pontos de extremidade externos.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-132">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="1e2cf-133">O Gerenciador de tráfego usa os seguintes métodos de roteamento:</span><span class="sxs-lookup"><span data-stu-id="1e2cf-133">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="1e2cf-134">**Failover:** Os pontos de extremidade estão no mesmo ou em diferentes data centers do Azure e você deseja usar um ponto de extremidade principal para todo o tráfego, mas fornecer backups caso os pontos de extremidade principal ou de backup não estejam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-134">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="1e2cf-135">**Round Robin:** Você deseja distribuir o carregamento em um conjunto de pontos de extremidade no mesmo datacenter ou em diferentes data centers.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-135">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="1e2cf-136">**Desempenho:** Você tem pontos de extremidade em diferentes locais geográficos e deseja solicitar que os clientes usem o ponto de extremidade "mais próximo" em termos da menor latência.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-136">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="1e2cf-137">Veja a seguir um exemplo de três aplicativos Web distribuídos geograficamente.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-137">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="1e2cf-138">**Figura 3: Gerenciador de tráfego do Azure**</span><span class="sxs-lookup"><span data-stu-id="1e2cf-138">**Figure 3: Azure Traffic Manager**</span></span>

![Figura 3: Gerenciador de tráfego do Azure](media/Network-Poster/PaaS3.png)
  
<span data-ttu-id="1e2cf-140">A Figura 3 mostra o processo básico que o Gerenciador de tráfego usa para encaminhar solicitações para três aplicativos Web do Azure diferentes nos Estados Unidos, na Europa e na Ásia.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-140">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia.</span></span> <span data-ttu-id="1e2cf-141">No exemplo:</span><span class="sxs-lookup"><span data-stu-id="1e2cf-141">In the example:</span></span>
  
1. <span data-ttu-id="1e2cf-142">Uma consulta DNS de usuário para uma URL de site é direcionada para o Azure Traffic Manager, que retorna o nome de um aplicativo Web regional, com base no método de roteamento de desempenho.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-142">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="1e2cf-143">O usuário inicia o tráfego com o aplicativo Web regional na Europa.</span><span class="sxs-lookup"><span data-stu-id="1e2cf-143">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="1e2cf-144">Para obter mais informações, consulte [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="1e2cf-144">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="1e2cf-145">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="1e2cf-145">Next step</span></span>

[<span data-ttu-id="1e2cf-146">Criação de rede para o Microsoft Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="1e2cf-146">Designing networking for Microsoft Azure IaaS</span></span>](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a><span data-ttu-id="1e2cf-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="1e2cf-147">See also</span></span>

[<span data-ttu-id="1e2cf-148">Rede do Microsoft Cloud para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="1e2cf-148">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="1e2cf-149">Recursos de arquitetura de TI da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="1e2cf-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

