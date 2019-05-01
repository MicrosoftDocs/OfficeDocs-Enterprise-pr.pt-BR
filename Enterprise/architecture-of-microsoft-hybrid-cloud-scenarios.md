---
title: Arquitetura de cenários de nuvem híbrida da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: 'Resumo: entenda a arquitetura das ofertas de nuvem híbrida da Microsoft.'
ms.openlocfilehash: f5493c0f008b22af412ee95ccb8b7581eee71476
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490258"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="e0ba9-103">Arquitetura de cenários de nuvem híbrida da Microsoft</span><span class="sxs-lookup"><span data-stu-id="e0ba9-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="e0ba9-104">**Resumo:** Entenda a arquitetura das ofertas de nuvem híbrida da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="e0ba9-105">Use uma abordagem arquitetônica para planejar e implementar cenários de nuvem híbrida com plataformas e serviços em nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="e0ba9-106">**Figura 1: a pilha de nuvem híbrida da Microsoft**</span><span class="sxs-lookup"><span data-stu-id="e0ba9-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![A pilha de nuvem híbrida da Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="e0ba9-108">A Figura 1 mostra a pilha de nuvem híbrida da Microsoft e sua camada, que incluem local, rede, identidade, aplicativos e cenários e a categoria de serviço de nuvem (Microsoft SaaS, Azure PaaS e Azure PaaS).</span><span class="sxs-lookup"><span data-stu-id="e0ba9-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="e0ba9-109">A camada aplicativos e cenários tem os cenários de nuvem híbrida específicos que são detalhados nos artigos adicionais desse modelo.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-109">The Apps and scenarios layer has the specific hybrid cloud scenarios that are detailed in the additional articles of this model.</span></span> <span data-ttu-id="e0ba9-110">A identidade, a rede e as camadas locais podem ser comuns às categorias de serviço de nuvem (SaaS, PaaS ou PaaS).</span><span class="sxs-lookup"><span data-stu-id="e0ba9-110">The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="e0ba9-111">No local</span><span class="sxs-lookup"><span data-stu-id="e0ba9-111">On-premises</span></span>
    
    <span data-ttu-id="e0ba9-112">A infraestrutura local para cenários híbridos pode incluir servidores para o SharePoint, o Exchange, o Skype for Business e aplicativos de linha de negócios.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-112">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications.</span></span> <span data-ttu-id="e0ba9-113">Também pode incluir repositórios de dados (bancos de dados, listas, arquivos).</span><span class="sxs-lookup"><span data-stu-id="e0ba9-113">It can also include data stores (databases, lists, files).</span></span> <span data-ttu-id="e0ba9-114">Sem conexões ExpressRoute, o acesso aos armazenamentos de dados locais deve ser permitido por meio de um proxy reverso ou ao tornar o servidor ou os dados acessíveis em sua DMZ ou Extranet.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-114">Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="e0ba9-115">Rede</span><span class="sxs-lookup"><span data-stu-id="e0ba9-115">Network</span></span>
    
    <span data-ttu-id="e0ba9-116">Há duas opções de conectividade para plataformas e serviços da nuvem da Microsoft: seu pipe da Internet existente e o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-116">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute.</span></span> <span data-ttu-id="e0ba9-117">Use uma conexão ExpressRoute se o desempenho previsível for importante.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-117">Use an ExpressRoute connection if predictable performance is important.</span></span> <span data-ttu-id="e0ba9-118">Você pode usar uma conexão ExpressRoute para se conectar diretamente aos serviços Microsoft SaaS (Office 365 e Dynamics 365), serviços de PaaS do Azure e serviços do Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-118">You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="e0ba9-119">Identidade</span><span class="sxs-lookup"><span data-stu-id="e0ba9-119">Identity</span></span>
    
    <span data-ttu-id="e0ba9-120">Para a infraestrutura de identidade em nuvem, há duas maneiras de ir, dependendo da plataforma de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-120">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform.</span></span> <span data-ttu-id="e0ba9-121">Para o SaaS e o PaaS do Azure, integre sua infraestrutura de identidade local com o Azure AD ou Federação com sua infraestrutura de identidade local ou provedores de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-121">For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers.</span></span> <span data-ttu-id="e0ba9-122">Para VMs em execução no Azure, você pode estender sua infraestrutura de identidade local, como os serviços de domínio do Active Directory (AD DS), para as redes virtuais (VNets) onde suas VMs residem.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-122">For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Active Directory Domain Services (AD DS), to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="e0ba9-123">Cenários de nuvem híbrida para o processo de adoção em nuvem de três fases</span><span class="sxs-lookup"><span data-stu-id="e0ba9-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="e0ba9-124">Muitas empresas, incluindo a Microsoft, usam uma abordagem de três fases para adotar a nuvem.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-124">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud.</span></span> <span data-ttu-id="e0ba9-125">Cenários de nuvem híbrida podem desempenhar uma função em cada fase.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-125">Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="e0ba9-126">Mover cargas de trabalho de produtividade para o SaaS</span><span class="sxs-lookup"><span data-stu-id="e0ba9-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="e0ba9-127">Para cargas de trabalho de produtividade que atualmente estão ou devem permanecer no local, os cenários híbridos permitem que eles sejam integrados às suas contrapartes da nuvem.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="e0ba9-128">Desenvolver aplicativos novos e modernos na PaaS do Azure</span><span class="sxs-lookup"><span data-stu-id="e0ba9-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="e0ba9-129">Os aplicativos híbridos da PaaS do Azure podem aproveitar com segurança os recursos de servidor ou armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="e0ba9-130">Mover aplicativos existentes para o Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="e0ba9-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="e0ba9-131">Para cenários de aumento e de fim e de compilação em nuvem, os aplicativos baseados em servidor executados nas VMs do Azure oferecem provisionamento e dimensionamento simples.</span><span class="sxs-lookup"><span data-stu-id="e0ba9-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e0ba9-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="e0ba9-132">See Also</span></span>

[<span data-ttu-id="e0ba9-133">Nuvem híbrida da Microsoft para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="e0ba9-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="e0ba9-134">Recursos de arquitetura de TI do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="e0ba9-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

