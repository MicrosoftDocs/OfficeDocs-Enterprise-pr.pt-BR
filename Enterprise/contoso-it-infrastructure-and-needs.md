---
title: Infraestrutura e necessidades de TI da Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Resumo: Compreenda a estrutura básica da Contoso local como seus negócios precisa podem ser atendidos por ofertas de nuvem da Microsoft e a infraestrutura de TI."
ms.openlocfilehash: b8282c4bd04448266bc68e65f95aaaff0a7a5db8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="bc98a-103">Infraestrutura e necessidades de TI da Contoso</span><span class="sxs-lookup"><span data-stu-id="bc98a-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="bc98a-104">**Resumo:** Compreenda a estrutura básica da Contoso local como seus negócios precisa podem ser atendidos por ofertas de nuvem da Microsoft e a infraestrutura de TI.</span><span class="sxs-lookup"><span data-stu-id="bc98a-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="bc98a-105">A Contoso está em processo de transição de um local, a infraestrutura de TI centralizado para um outro inclusive de nuvem que incorpora as cargas de trabalho de produtividade pessoal baseado em nuvem, aplicativos e cenários híbridos.</span><span class="sxs-lookup"><span data-stu-id="bc98a-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="bc98a-106">Infraestrutura de TI da Contoso</span><span class="sxs-lookup"><span data-stu-id="bc98a-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="bc98a-107">A Contoso usa principalmente centralizado infraestrutura de TI, com centros de dados de aplicativo na sede Paris local.</span><span class="sxs-lookup"><span data-stu-id="bc98a-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="bc98a-108">**Figura 1: Infra-estrutura de TI da Contoso**</span><span class="sxs-lookup"><span data-stu-id="bc98a-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Infraestrutura de TI da Contoso](images/Contoso_Poster/Existing_IT.png)
  
<span data-ttu-id="bc98a-110">A Figura 1 mostra um escritório matriz com a Internet, DMZ e centros de dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bc98a-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="bc98a-111">Em DMZ da Contoso, fornecem os diferentes conjuntos de servidores:</span><span class="sxs-lookup"><span data-stu-id="bc98a-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="bc98a-112">Acesso remoto para o proxy de intranet e web Contoso para trabalhadores na sede Paris.</span><span class="sxs-lookup"><span data-stu-id="bc98a-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="bc98a-113">Hospedagem para o site público Contoso, do qual os clientes podem solicitar produtos, partes ou fontes.</span><span class="sxs-lookup"><span data-stu-id="bc98a-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="bc98a-114">Hospedando o parceiro Contoso extranet para colaboração e comunicação parceiros.</span><span class="sxs-lookup"><span data-stu-id="bc98a-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="bc98a-115">Necessidades de negócios da Contoso</span><span class="sxs-lookup"><span data-stu-id="bc98a-115">Contoso's business needs</span></span>

<span data-ttu-id="bc98a-116">Aqui estão as necessidades de negócios da Contoso em ordem de prioridade:</span><span class="sxs-lookup"><span data-stu-id="bc98a-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="bc98a-117">Cumprir os requisitos normativos regionais</span><span class="sxs-lookup"><span data-stu-id="bc98a-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="bc98a-118">Para evitar multas e manter boas relações com governos locais, a Contoso deve assegurar a conformidade com normas de armazenamento e a criptografia de dados.</span><span class="sxs-lookup"><span data-stu-id="bc98a-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="bc98a-119">Melhorar o gerenciamento de fornecedores e parceiros</span><span class="sxs-lookup"><span data-stu-id="bc98a-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="bc98a-p101">O parceiro extranet é a duração e caras de manter. A Contoso deseja substituí-la por uma solução baseada na nuvem que usa autenticação federada.</span><span class="sxs-lookup"><span data-stu-id="bc98a-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="bc98a-122">Melhorar a produtividade da força de trabalho móvel, gerenciamento de dispositivo e acesso</span><span class="sxs-lookup"><span data-stu-id="bc98a-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="bc98a-123">Força de trabalho somente mobile da Contoso está expandindo e necessidades de gerenciamento de dispositivos para garantir acesso mais eficiente aos recursos e a proteção à propriedade intelectual.</span><span class="sxs-lookup"><span data-stu-id="bc98a-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="bc98a-124">Reduzir a infra-estrutura de acesso remoto</span><span class="sxs-lookup"><span data-stu-id="bc98a-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="bc98a-125">Movendo recursos comumente acessados pelos funcionários remotos para a nuvem, Contoso economizarão, reduzindo os custos de manutenção e suporte para sua solução de acesso remoto.</span><span class="sxs-lookup"><span data-stu-id="bc98a-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="bc98a-126">Dimensionar para baixo de centros de dados no local</span><span class="sxs-lookup"><span data-stu-id="bc98a-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="bc98a-127">Os datacenters Contoso contêm centenas de servidores, alguns dos quais estão executando funções herdadas ou de arquivamento que distraem a equipe de TI de manutenção de cargas de trabalho de valor comercial alto.</span><span class="sxs-lookup"><span data-stu-id="bc98a-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="bc98a-128">Recursos de computação e armazenamento de dimensione para processamento de final de trimestre</span><span class="sxs-lookup"><span data-stu-id="bc98a-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="bc98a-129">Fim do trimestre contabilidade financeira e processamento, juntamente com o gerenciamento do inventário de projeção requer curto prazo aumenta em servidores e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="bc98a-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="bc98a-130">Mapeamento de negócios da Contoso precisa ofertas de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="bc98a-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="bc98a-131">Com base em uma análise das ofertas de nuvem da Microsoft, a Contoso do departamento de TI determinou que o mapeamento a seguir:</span><span class="sxs-lookup"><span data-stu-id="bc98a-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="bc98a-132">**Software como serviço (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="bc98a-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="bc98a-133">**Plataforma como um serviço (PaaS Azure)**</span><span class="sxs-lookup"><span data-stu-id="bc98a-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="bc98a-134">**Infraestrutura como um serviço (Azure IaaS)**</span><span class="sxs-lookup"><span data-stu-id="bc98a-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bc98a-135">**Office 365:** Aplicativos de produtividade de pessoal e de grupo principal na nuvem.</span><span class="sxs-lookup"><span data-stu-id="bc98a-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="bc98a-136">Necessidades de negócios: 1 3 5</span><span class="sxs-lookup"><span data-stu-id="bc98a-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="bc98a-137">Hospedar vendas e suporte a documentos e sistemas de informação usando aplicativos baseados em nuvem.</span><span class="sxs-lookup"><span data-stu-id="bc98a-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="bc98a-138">Necessidade comercial: 3</span><span class="sxs-lookup"><span data-stu-id="bc98a-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="bc98a-139">Mova os sistemas de arquivamento e herdados para servidores baseados em nuvem.</span><span class="sxs-lookup"><span data-stu-id="bc98a-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="bc98a-140">Necessidade comercial: 5</span><span class="sxs-lookup"><span data-stu-id="bc98a-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="bc98a-p102">**Dynamics 365:** Use o gerenciamento de fornecedores e clientes baseados em nuvem. Remova o parceiro extranet no DMZ.</span><span class="sxs-lookup"><span data-stu-id="bc98a-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="bc98a-143">Necessidade comercial: 2</span><span class="sxs-lookup"><span data-stu-id="bc98a-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="bc98a-144">Aplicativos móveis são baseadas em nuvem, em vez de Paris com base no datacenter.</span><span class="sxs-lookup"><span data-stu-id="bc98a-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="bc98a-145">Necessidades de negócios: 3 de 4</span><span class="sxs-lookup"><span data-stu-id="bc98a-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="bc98a-146">Migre dados fora do local de centros de dados e aplicativos pouco usado.</span><span class="sxs-lookup"><span data-stu-id="bc98a-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="bc98a-147">Necessidade comercial: 5</span><span class="sxs-lookup"><span data-stu-id="bc98a-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="bc98a-148">**Intune/EMS:** Gerencie dispositivos com Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="bc98a-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="bc98a-149">Necessidade comercial: 3</span><span class="sxs-lookup"><span data-stu-id="bc98a-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="bc98a-150">Adicione servidores temporários e armazenamento para necessidades de processamento de final de trimestre.</span><span class="sxs-lookup"><span data-stu-id="bc98a-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="bc98a-151">Necessidade comercial: 6</span><span class="sxs-lookup"><span data-stu-id="bc98a-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="bc98a-152">Veja também</span><span class="sxs-lookup"><span data-stu-id="bc98a-152">See Also</span></span>

[<span data-ttu-id="bc98a-153">Contoso na Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="bc98a-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="bc98a-154">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="bc98a-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="bc98a-155">Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="bc98a-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


