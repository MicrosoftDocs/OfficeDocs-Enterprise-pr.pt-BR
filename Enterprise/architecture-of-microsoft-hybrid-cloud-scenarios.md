---
title: "Arquitetura dos cenários de nuvem Microsoft híbridos"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Resumo: Entenda a arquitetura das ofertas de nuvem da Microsoft híbrida."
ms.openlocfilehash: f1c234026324b2c507dd4369cb98306e7e83a775
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="8e18b-103">Arquitetura dos cenários de nuvem Microsoft híbridos</span><span class="sxs-lookup"><span data-stu-id="8e18b-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="8e18b-104">**Resumo:** Entenda a arquitetura de ofertas de nuvem da Microsoft híbrida.</span><span class="sxs-lookup"><span data-stu-id="8e18b-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="8e18b-105">Use uma abordagem de arquitetura para planejar e implementar os cenários de nuvem híbrida com os serviços de nuvem da Microsoft e plataformas.</span><span class="sxs-lookup"><span data-stu-id="8e18b-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="8e18b-106">**Figura 1: Microsoft híbrida pilha da nuvem**</span><span class="sxs-lookup"><span data-stu-id="8e18b-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![A pilha de nuvem híbrida da Microsoft](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
<span data-ttu-id="8e18b-108">A Figura 1 mostra a pilha de nuvem híbrida Microsoft e sua camada, que incluem o local, rede, identidade, aplicativos e cenários e categoria do serviço na nuvem (SaaS Microsoft Azure PaaS e Azure PaaS).</span><span class="sxs-lookup"><span data-stu-id="8e18b-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="8e18b-p101">A camada de aplicativos e cenários contém os cenários de nuvem híbrida específica que são detalhados nos artigos adicionais desse modelo. A identidade, rede e locais camadas podem ser comuns para as categorias de serviço na nuvem (SaaS, PaaS ou PaaS).</span><span class="sxs-lookup"><span data-stu-id="8e18b-p101">The Apps and scenarios layer contains the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="8e18b-111">Local</span><span class="sxs-lookup"><span data-stu-id="8e18b-111">On-premises</span></span>
    
    <span data-ttu-id="8e18b-p102">Infraestrutura do local para cenários híbridos pode incluir servidores para SharePoint, Exchange, Skype para aplicativos linha de negócios e de negócios. Ele também pode incluir os repositórios de dados (bancos de dados, listas, arquivos). Sem conexões ExpressRoute, acesso para os repositórios de dados de locais deve ser permitido por meio de um proxy reverso ou tornando o servidor ou os dados acessíveis em sua DMZ ou extranet.</span><span class="sxs-lookup"><span data-stu-id="8e18b-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="8e18b-115">Rede</span><span class="sxs-lookup"><span data-stu-id="8e18b-115">Network</span></span>
    
    <span data-ttu-id="8e18b-p103">Há duas opções para conectividade com plataformas de nuvem da Microsoft e serviços: seu pipe existente da Internet e ExpressRoute. Use uma conexão ExpressRoute se desempenho previsível é importante. Você pode usar uma conexão de ExpressRoute para conectar-se diretamente para os serviços Microsoft SaaS (Office 365 e Dynamics 365), serviços do Azure PaaS e serviços do Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="8e18b-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure PaaS services.</span></span>
    
- <span data-ttu-id="8e18b-119">Identidade</span><span class="sxs-lookup"><span data-stu-id="8e18b-119">Identity</span></span>
    
    <span data-ttu-id="8e18b-p104">Para infraestrutura de identidade de nuvem, há duas maneiras de ir, dependendo da plataforma de nuvem da Microsoft. Para SaaS e PaaS do Azure, integrar sua infraestrutura de identidade no local com o Azure AD ou estabelecer uma federação com provedores de identidade seu local identidade infraestrutura ou de terceiros. Para VMs em execução no Windows Azure, você pode estender sua infraestrutura de identidade de local, como o Windows Server AD, para as redes virtuais (VNets) onde residem os suas VMs.</span><span class="sxs-lookup"><span data-stu-id="8e18b-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="8e18b-123">Cenários de nuvem híbrida para o processo de adoção de nuvem de três fases</span><span class="sxs-lookup"><span data-stu-id="8e18b-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="8e18b-p105">Muitas empresas, incluindo Microsoft, usam uma abordagem de três fases para adotar a nuvem. Cenários de nuvem híbrida podem reproduzir uma função em cada fase.</span><span class="sxs-lookup"><span data-stu-id="8e18b-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="8e18b-126">Mover cargas de trabalho de produtividade para SaaS</span><span class="sxs-lookup"><span data-stu-id="8e18b-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="8e18b-127">Para produtividade cargas de trabalho que atualmente estão ou devem permanecer no local, cenários híbridos permitir que eles sejam integrados com os representantes de nuvem.</span><span class="sxs-lookup"><span data-stu-id="8e18b-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="8e18b-128">Desenvolva aplicativos novos e modernos no Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="8e18b-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="8e18b-129">Aplicativos do Azure PaaS híbrida com segurança podem aproveitar os recursos de servidor ou armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="8e18b-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="8e18b-130">Mover aplicativos existentes para o Windows Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="8e18b-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="8e18b-131">Para cenários de shift e levantar e compilação na nuvem, aplicativos de servidor em execução no Azure VMs fornecem fácil provisionamento e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="8e18b-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="8e18b-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="8e18b-132">See Also</span></span>

[<span data-ttu-id="8e18b-133">Nuvem híbrida da Microsoft para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="8e18b-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="8e18b-134">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="8e18b-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="8e18b-135">Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="8e18b-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



