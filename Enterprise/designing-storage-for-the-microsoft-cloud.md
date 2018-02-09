---
title: Projetar o armazenamento para a nuvem da Microsoft
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
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "Resumo: Entenda por que você precisa de armazenamento na nuvem e examine a lista de opções de armazenamento de nuvem da Microsoft e os cenários de armazenamento de chave."
ms.openlocfilehash: ed816743e2d85a622a3fbfbb129bf90a7db93881
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="97200-103">Projetar o armazenamento para a nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="97200-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="97200-104">**Resumo:** Entender por que você precisa de armazenamento na nuvem e examine a lista de opções de armazenamento de nuvem da Microsoft e os cenários de armazenamento de chave.</span><span class="sxs-lookup"><span data-stu-id="97200-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="97200-105">Integrar o armazenamento com serviços de nuvem da Microsoft oferece acesso a uma ampla gama de opções de plataforma de serviços e a nuvem.</span><span class="sxs-lookup"><span data-stu-id="97200-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="97200-106">Por que armazenamento na nuvem?</span><span class="sxs-lookup"><span data-stu-id="97200-106">Why cloud storage?</span></span>

<span data-ttu-id="97200-107">Há dois motivos principais para usar o armazenamento em nuvem.</span><span class="sxs-lookup"><span data-stu-id="97200-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="97200-108">Velocidade do mercado:</span><span class="sxs-lookup"><span data-stu-id="97200-108">Speed to market:</span></span>
    
  - <span data-ttu-id="97200-109">Configuração mais rápida para alta disponibilidade e recuperação de desastres</span><span class="sxs-lookup"><span data-stu-id="97200-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="97200-110">Nenhum hardware de armazenamento adquirir</span><span class="sxs-lookup"><span data-stu-id="97200-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="97200-111">Direcionamento interno fornecido pelo ofertas de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="97200-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="97200-112">Disponível em qualquer lugar no mundo</span><span class="sxs-lookup"><span data-stu-id="97200-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="97200-113">Reduzir os custos para manter:</span><span class="sxs-lookup"><span data-stu-id="97200-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="97200-114">Elasticidade dimensionar acima e abaixo suas demandas de armazenamento</span><span class="sxs-lookup"><span data-stu-id="97200-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="97200-115">Nenhum hardware de armazenamento para manter ou migrar</span><span class="sxs-lookup"><span data-stu-id="97200-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="97200-116">A Microsoft tem o seu técnico interno para manter e aprimorar a infra-estrutura</span><span class="sxs-lookup"><span data-stu-id="97200-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="97200-117">Melhor segurança de armazenamento no mercado com melhorias em andamento</span><span class="sxs-lookup"><span data-stu-id="97200-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="97200-118">Opções de armazenamento do Microsoft cloud</span><span class="sxs-lookup"><span data-stu-id="97200-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="97200-119">Para ajudá-lo a entender a ampla variedade de opções de armazenamento de nuvem, usamos uma analogia de construção.</span><span class="sxs-lookup"><span data-stu-id="97200-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="97200-120">Move-in pronto</span><span class="sxs-lookup"><span data-stu-id="97200-120">Move-in ready</span></span>

<span data-ttu-id="97200-p101">Use essas soluções pré-empacotados que estão incluídas com serviços existentes. Use imediatamente e com a configuração mínima.</span><span class="sxs-lookup"><span data-stu-id="97200-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="97200-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="97200-123">Office 365</span></span>
    
- <span data-ttu-id="97200-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="97200-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="97200-125">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="97200-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="97200-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="97200-126">Dynamics 365</span></span>
    
- <span data-ttu-id="97200-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="97200-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="97200-128">Recuperação de sites do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="97200-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="97200-129">Compartilhamento de sites do Yammer</span><span class="sxs-lookup"><span data-stu-id="97200-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="97200-130">Backup do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="97200-130">Azure Backup</span></span>
    
<span data-ttu-id="97200-131">Para obter os detalhes de cada uma dessas opções de armazenamento em nuvem, consulte [Move-in pronto](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="97200-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="97200-132">Alguns assembly necessário</span><span class="sxs-lookup"><span data-stu-id="97200-132">Some assembly required</span></span>

<span data-ttu-id="97200-133">Use esses serviços existentes como um ponto de partida para sua solução de armazenamento com uma configuração adicional ou codificação para um ajuste personalizado.</span><span class="sxs-lookup"><span data-stu-id="97200-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="97200-134">Rede de fornecimento de conteúdo do Azure</span><span class="sxs-lookup"><span data-stu-id="97200-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="97200-135">Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="97200-135">Azure Media Services</span></span>
    
- <span data-ttu-id="97200-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="97200-136">HdInsight</span></span>
    
- <span data-ttu-id="97200-137">Cache do Azure relacionada</span><span class="sxs-lookup"><span data-stu-id="97200-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="97200-138">Banco de Dados SQL Azure</span><span class="sxs-lookup"><span data-stu-id="97200-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="97200-139">SQL Server em uma VM Azure</span><span class="sxs-lookup"><span data-stu-id="97200-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="97200-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="97200-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="97200-141">Desempenho do StorSimple</span><span class="sxs-lookup"><span data-stu-id="97200-141">StorSimple</span></span>
    
- <span data-ttu-id="97200-142">Armazém de dados do SQL Azure</span><span class="sxs-lookup"><span data-stu-id="97200-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="97200-143">Repositório de Lake de dados do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="97200-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="97200-144">Para obter os detalhes de cada uma dessas opções de armazenamento de nuvem, consulte [alguns assembly necessários](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="97200-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="97200-145">Criação de ponta a ponta para cima</span><span class="sxs-lookup"><span data-stu-id="97200-145">Build from the ground up</span></span>

<span data-ttu-id="97200-146">Use esses blocos de construção de armazenamento, juntamente com a codificação, para criar sua própria solução de armazenamento ou aplicativos a partir do zero.</span><span class="sxs-lookup"><span data-stu-id="97200-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="97200-147">Armazenamento do Azure (arquivos)</span><span class="sxs-lookup"><span data-stu-id="97200-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="97200-148">Armazenamento (blobs) do Azure</span><span class="sxs-lookup"><span data-stu-id="97200-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="97200-149">Armazenamento do Azure (filas)</span><span class="sxs-lookup"><span data-stu-id="97200-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="97200-150">Armazenamento do Azure (tabelas)</span><span class="sxs-lookup"><span data-stu-id="97200-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="97200-151">Para obter os detalhes de cada uma dessas opções de armazenamento de nuvem, consulte [construir a partir do zero](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="97200-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="97200-152">Cenários de armazenamento de chave</span><span class="sxs-lookup"><span data-stu-id="97200-152">Key storage scenarios</span></span>

<span data-ttu-id="97200-153">Aqui estão os principais cenários que exigem o armazenamento baseado em nuvem:</span><span class="sxs-lookup"><span data-stu-id="97200-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="97200-154">Cache de dados</span><span class="sxs-lookup"><span data-stu-id="97200-154">Cache data</span></span>
    
    <span data-ttu-id="97200-155">Acelere o acesso aos dados comumente usados, armazenando-o em um cache de alta velocidade.</span><span class="sxs-lookup"><span data-stu-id="97200-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="97200-156">Colaborar com membros da equipe</span><span class="sxs-lookup"><span data-stu-id="97200-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="97200-157">Conceder permissão a vários usuários para permitir o acesso aos dados no armazenamento na nuvem.</span><span class="sxs-lookup"><span data-stu-id="97200-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="97200-158">Gerenciar dados</span><span class="sxs-lookup"><span data-stu-id="97200-158">Manage data</span></span>
    
    <span data-ttu-id="97200-159">Armazenar, mover ou excluir dados em massa internos ou externos.</span><span class="sxs-lookup"><span data-stu-id="97200-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="97200-160">Gerenciar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="97200-160">Manage source code</span></span>
    
    <span data-ttu-id="97200-161">Carregar, colaborar e executar arquivos de código do aplicativo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="97200-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="97200-162">Arquivos de backup</span><span class="sxs-lookup"><span data-stu-id="97200-162">Backup files</span></span>
    
    <span data-ttu-id="97200-163">Armazene cópias de dados internos ou externos externos em vários locais em nuvem.</span><span class="sxs-lookup"><span data-stu-id="97200-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="97200-164">Publicar comunicações da empresa</span><span class="sxs-lookup"><span data-stu-id="97200-164">Publish company communications</span></span>
    
    <span data-ttu-id="97200-165">Crie um ponto único de publicação para mensagens internas ou externas.</span><span class="sxs-lookup"><span data-stu-id="97200-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="97200-166">Distribuir milhões de eventos</span><span class="sxs-lookup"><span data-stu-id="97200-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="97200-167">Crie o armazenamento para inclusão de telemetria em sites, aplicativos e dispositivos.</span><span class="sxs-lookup"><span data-stu-id="97200-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="97200-168">Gerenciar/servem vídeos</span><span class="sxs-lookup"><span data-stu-id="97200-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="97200-169">Armazenar e forneça conteúdo de vídeo aos clientes ou usuários da organização.</span><span class="sxs-lookup"><span data-stu-id="97200-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="97200-170">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="97200-170">Next step</span></span>

<span data-ttu-id="97200-171">Examine as opções de armazenamento [pronto Move na](move-in-ready.md) nuvem.</span><span class="sxs-lookup"><span data-stu-id="97200-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="97200-172">Veja também</span><span class="sxs-lookup"><span data-stu-id="97200-172">See Also</span></span>

[<span data-ttu-id="97200-173">Armazenamento do Microsoft Cloud para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="97200-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="97200-174">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="97200-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="97200-175">Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="97200-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


