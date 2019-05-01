---
title: Diagrama acessível-recuperação de desastre do SharePoint para o Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Este artigo é uma versão de texto acessível do diagrama chamado recuperação de desastre do SharePoint para o Microsoft Azure.
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487717"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="8ae1f-103">Diagrama acessível-recuperação de desastre do SharePoint para o Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="8ae1f-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="8ae1f-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado recuperação de desastre do SharePoint para o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="8ae1f-105">Este cartaz fornece exemplos de arquiteturas para a criação de um ambiente de recuperação no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="8ae1f-106">Ambiente local com um ambiente de recuperação do Azure</span><span class="sxs-lookup"><span data-stu-id="8ae1f-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="8ae1f-107">O diagrama mostra um exemplo de arquitetura usada para o ambiente de produção de um ambiente local que usa o Azure para recuperação.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="8ae1f-108">Ambiente de produção local</span><span class="sxs-lookup"><span data-stu-id="8ae1f-108">On-premises production environment</span></span>

<span data-ttu-id="8ae1f-109">O diagrama a seguir mostra um ambiente de produção ativo com quatro camadas de servidores em um farm de servidores.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="8ae1f-110">Camada 1</span><span class="sxs-lookup"><span data-stu-id="8ae1f-110">Tier 1</span></span>

<span data-ttu-id="8ae1f-111">Há dois servidores para o processamento de consultas e serviços de front-end.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-111">There are two servers for front-end services and query processing.</span></span> <span data-ttu-id="8ae1f-112">Há uma partição de índice que fornece uma réplica dos dois servidores.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-112">There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="8ae1f-113">Camada 2</span><span class="sxs-lookup"><span data-stu-id="8ae1f-113">Tier 2</span></span>

<span data-ttu-id="8ae1f-114">Há dois servidores para o cache distribuído nessa camada.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="8ae1f-115">Camada 3</span><span class="sxs-lookup"><span data-stu-id="8ae1f-115">Tier 3</span></span>

<span data-ttu-id="8ae1f-116">Há três servidores nessa camada.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-116">There are three servers in this tier.</span></span> <span data-ttu-id="8ae1f-117">Cada servidor fornece os seguintes serviços:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-117">Each server provides the following services:</span></span> 
  
- <span data-ttu-id="8ae1f-118">Serviços de backend</span><span class="sxs-lookup"><span data-stu-id="8ae1f-118">Backend services</span></span> 
    
- <span data-ttu-id="8ae1f-119">Admin</span><span class="sxs-lookup"><span data-stu-id="8ae1f-119">Admin</span></span> 
    
- <span data-ttu-id="8ae1f-120">Gerenciador de fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="8ae1f-120">Workflow manager</span></span> 
    
- <span data-ttu-id="8ae1f-121">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="8ae1f-121">Crawl</span></span> 
    
- <span data-ttu-id="8ae1f-122">Processamento de conteúdo</span><span class="sxs-lookup"><span data-stu-id="8ae1f-122">Content processing</span></span> 
    
- <span data-ttu-id="8ae1f-123">Análise</span><span class="sxs-lookup"><span data-stu-id="8ae1f-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="8ae1f-124">Camada 4</span><span class="sxs-lookup"><span data-stu-id="8ae1f-124">Tier 4</span></span>

<span data-ttu-id="8ae1f-125">Há dois servidores nessa camada.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-125">There are two servers in this tier.</span></span> <span data-ttu-id="8ae1f-126">Ambos os servidores têm três grupos de disponibilidade, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-126">Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="8ae1f-127">O grupo de disponibilidade #1 fornece recursos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="8ae1f-128">O grupo de disponibilidade #2 fornece aplicativos de conteúdo, configuração e serviço.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="8ae1f-129">O grupo de disponibilidade #3 fornece conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="8ae1f-130">Há também um servidor de compartilhamento de arquivos nessa camada.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-130">There is also a file sharing server in this tier.</span></span> <span data-ttu-id="8ae1f-131">Os servidores de camada 4 usam o envio de logs para se comunicar com este servidor.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-131">The tier 4 servers use log shipping to communicate with this server.</span></span> <span data-ttu-id="8ae1f-132">Este servidor, por sua vez, se comunica através da replicação do sistema de arquivos distribuídos (DFSR) para um servidor de compartilhamento de arquivos no ambiente de recuperação de espera passiva do Azure, conforme descrito na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-132">This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="8ae1f-133">Ambiente de recuperação do Azure</span><span class="sxs-lookup"><span data-stu-id="8ae1f-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="8ae1f-134">Ambiente de espera passiva executando máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="8ae1f-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="8ae1f-135">O diagrama a seguir mostra o ambiente local replicado exatamente no ambiente de recuperação do Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-135">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment.</span></span> <span data-ttu-id="8ae1f-136">O servidor de compartilhamento de arquivos desse ambiente está vinculado ao ambiente local por meio do DFSR.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-136">The file share server in this environment is linked to the on-premises environment through DFSR.</span></span> <span data-ttu-id="8ae1f-137">O DFSR transfere logs do ambiente de produção para o ambiente de recuperação por meio do servidor de compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-137">DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="8ae1f-138">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="8ae1f-138">Overview</span></span>

<span data-ttu-id="8ae1f-139">O ambiente de recuperação de desastres para um farm local do SharePoint 2013 pode ser hospedado no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="8ae1f-140">Os serviços de infraestrutura do Azure fornecem um data center secundário.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="8ae1f-141">Pague apenas os recursos que você usa.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="8ae1f-142">Pequenos farms de recuperação podem ser dimensionados após um desastre para atender às metas de escala e capacidade.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="8ae1f-143">O farm de recuperação no Azure é configurado da forma mais idêntica possível para o farm local de produção.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="8ae1f-144">Mesma representação de funções de servidor.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="8ae1f-145">Mesma configuração de personalizações.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="8ae1f-146">Mesma configuração dos recursos de pesquisa (eles podem estar em uma versão menor do farm de produção).</span><span class="sxs-lookup"><span data-stu-id="8ae1f-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="8ae1f-147">O envio de logs e o DFSR são usados para copiar backups de banco de dados e logs de transações para o farm do Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="8ae1f-148">O DFSR é usado para transferir logs do ambiente de produção para o ambiente de recuperação.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-148">DFSR is used to transfer logs from the production environment to the recovery environment.</span></span> <span data-ttu-id="8ae1f-149">Em um cenário WAN, a DFSR é mais eficiente do que enviar os logs diretamente para o servidor secundário no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-149">In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="8ae1f-150">Os logs são repetidos nos computadores do SQL Server baseados no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="8ae1f-151">Os bancos de dados enviados por log não são anexados ao farm até que um exercício de recuperação seja realizado.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="8ae1f-152">Procedimentos de failover:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="8ae1f-153">Parar o envio de logs.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="8ae1f-154">Pare de aceitar o tráfego para o farm principal.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="8ae1f-155">Reproduza os logs de transação finais.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="8ae1f-156">Anexe os bancos de dados de conteúdo ao farm.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="8ae1f-157">Inicie um rastreamento completo.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="8ae1f-158">Restaure os aplicativos de serviço dos bancos de dados de serviços replicados.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="8ae1f-159">Os objetivos de recuperação fornecidos por esta solução incluem:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="8ae1f-160">Sites e conteúdo</span><span class="sxs-lookup"><span data-stu-id="8ae1f-160">Sites and content</span></span> 
    
- <span data-ttu-id="8ae1f-161">Pesquisar (rastreado novamente, sem histórico de pesquisa)</span><span class="sxs-lookup"><span data-stu-id="8ae1f-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="8ae1f-162">Serviços</span><span class="sxs-lookup"><span data-stu-id="8ae1f-162">Services</span></span>
    
<span data-ttu-id="8ae1f-163">Itens adicionais que podem ser tratados pelos serviços de consultoria da Microsoft ou por um parceiro:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="8ae1f-164">Sincronizando soluções de farm personalizadas</span><span class="sxs-lookup"><span data-stu-id="8ae1f-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="8ae1f-165">Conexões com fontes de dados locais (BDC (conectividade de dados corporativos) e fontes de conteúdo de pesquisa)</span><span class="sxs-lookup"><span data-stu-id="8ae1f-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="8ae1f-166">Cenários de restauração de pesquisa</span><span class="sxs-lookup"><span data-stu-id="8ae1f-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="8ae1f-167">Objetivos de tempo de recuperação (RTO) e objetivos de ponto de recuperação (RPO)</span><span class="sxs-lookup"><span data-stu-id="8ae1f-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="8ae1f-168">Ambiente de espera Cold executando máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="8ae1f-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="8ae1f-169">Os ambientes de espera Cold levam mais tempo para começar, mas são menos caros.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="8ae1f-170">O farm está totalmente construído, mas as máquinas virtuais são interrompidas após a criação do farm.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-170">The farm is fully built, but the virtual machines are stopped after the farm is created.</span></span> <span data-ttu-id="8ae1f-171">Você paga apenas os custos de processamento quando as máquinas virtuais estão em execução, mas os custos de transferência de dados de rede e armazenamento são aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-171">You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="8ae1f-172">No caso de um desastre, todas as máquinas virtuais no farm são iniciadas e corrigidas.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="8ae1f-173">Os backups e logs de transações são aplicados aos bancos de dados do farm.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="8ae1f-174">A lista a seguir descreve procedimentos adicionais para ambientes de espera Cold:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="8ae1f-175">Ative as máquinas virtuais regularmente para corrigir, atualizar e verificar o ambiente.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="8ae1f-176">Execute procedimentos para atualizar DNS e endereços IP.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="8ae1f-177">Configure o AlwaysOn do SQL após um failover.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="8ae1f-178">O diagrama a seguir mostra um ambiente de recuperação replicado em máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-178">The accompanying diagram shows a replicated recovery environment on virtual machines.</span></span> <span data-ttu-id="8ae1f-179">Após o failover para um ambiente de espera Cold, todas as máquinas virtuais são iniciadas e os grupos de disponibilidade são configurados usando logs de repetição para disponibilizar os servidores de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-179">After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="8ae1f-180">Ambiente de recuperação do SharePoint no Azure</span><span class="sxs-lookup"><span data-stu-id="8ae1f-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="8ae1f-181">Projete e construa o ambiente de failover no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="8ae1f-182">Criar uma rede virtual no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="8ae1f-183">Conecte a rede local com a rede virtual no Azure com uma conexão VPN de site a site.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-183">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection.</span></span> <span data-ttu-id="8ae1f-184">Esta conexão usa um gateway dinâmico no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-184">This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="8ae1f-185">Implante um ou mais controladores de domínio na rede virtual do Azure e configure-os para que funcionem com seu domínio local.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-185">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain.</span></span> <span data-ttu-id="8ae1f-186">Esses controladores de domínio são servidores de catálogo.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-186">These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="8ae1f-187">Adaptar o farm do SharePoint para os serviços de nuvem e conjuntos de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="8ae1f-188">Implante o farm do SharePoint, além de um servidor de arquivos para hospedar compartilhamentos de arquivos.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="8ae1f-189">Configurar o envio de logs e o DFSR entre o ambiente local e o ambiente de recuperação baseado no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="8ae1f-190">O diagrama a seguir mostra o ambiente local e a rede virtual do Azure com os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="8ae1f-191">Ambiente no local</span><span class="sxs-lookup"><span data-stu-id="8ae1f-191">On-premises environment</span></span>

- <span data-ttu-id="8ae1f-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="8ae1f-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="8ae1f-193">Servidor do Active Directory</span><span class="sxs-lookup"><span data-stu-id="8ae1f-193">Active Directory server</span></span> 
    
<span data-ttu-id="8ae1f-194">A interface de rede local com a rede virtual do Azure por meio de um gateway VPN (rede virtual privada).</span><span class="sxs-lookup"><span data-stu-id="8ae1f-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="8ae1f-195">Rede virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="8ae1f-195">Azure virtual network</span></span>

<span data-ttu-id="8ae1f-196">As interfaces de gateway VPN com uma sub-rede ativa de gateway VPN.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="8ae1f-197">Há três serviços de nuvem na rede virtual do Azure:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="8ae1f-198">O primeiro serviço de nuvem tem dois servidores Active Directory e DNS com um conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="8ae1f-199">O segundo serviço de nuvem tem três conjuntos de servidores: dois servidores de cache distribuído com um conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-199">The second cloud service has three sets of servers: Two distributed cache servers with an availability set.</span></span> <span data-ttu-id="8ae1f-200">Dois servidores front-end com um conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-200">Two front-end servers with an availability set.</span></span> <span data-ttu-id="8ae1f-201">Três servidores de back-end com um conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-201">Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="8ae1f-202">O terceiro serviço de nuvem tem três servidores de banco de dados com um conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-202">The third cloud service has three database servers with an availability set.</span></span> <span data-ttu-id="8ae1f-203">Um desses servidores de banco de dados é um compartilhamento de arquivos para o envio de logs e um terceiro nó de uma maioria de nós para o SQL Server AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-203">One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="8ae1f-204">Criar o ambiente híbrido do AD DS</span><span class="sxs-lookup"><span data-stu-id="8ae1f-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="8ae1f-205">A configuração do AD DS para esta solução constitui um cenário de implantação híbrida no qual o AD DS é implantado parcialmente no local e implantado parcialmente nas máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="8ae1f-206">Importante — antes de implantar o AD DS no Azure, leia as diretrizes para implantar o Windows Server Active Directory nas máquinas virtuais dohttp://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)Microsoft Azure (.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="8ae1f-207">Para obter uma orientação completa sobre como projetar e implantar ambientes do Active http://TechNet.microsoft.comDirectory, consulte.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="8ae1f-208">Essa arquitetura de referência inclui duas máquinas virtuais configuradas como controladores de domínio.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-208">This reference architecture includes two virtual machines configured as domain controllers.</span></span> <span data-ttu-id="8ae1f-209">Cada uma é configurada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8ae1f-209">Each is configured as follows:</span></span> 
  
- <span data-ttu-id="8ae1f-210">Tamanho – pequeno.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-210">Size — Small.</span></span> 
    
- <span data-ttu-id="8ae1f-211">Sistema operacional — Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="8ae1f-212">Função — controlador de domínio AD DS designado como um servidor de catálogo global.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-212">Role — AD DS domain controller designated as a global catalog server.</span></span> <span data-ttu-id="8ae1f-213">Essa configuração reduz o tráfego de egresso na conexão VPN.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-213">This configuration reduces egress traffic across the VPN connection.</span></span> <span data-ttu-id="8ae1f-214">Em um ambiente de vários domínios com altas taxas de alteração, configure os controladores de domínio no local para não sincronizar com os servidores de catálogo global no Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-214">In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="8ae1f-215">Discos de dados — Coloque o banco de dados do AD DS, os logs e o SYSVOL nos discos de dados do Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-215">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks.</span></span> <span data-ttu-id="8ae1f-216">Não coloque esses no disco do sistema operacional ou nos discos temporários fornecidos pelo Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-216">Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span> <span data-ttu-id="8ae1f-217">Isso é importante.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-217">This is important.</span></span> 
    
- <span data-ttu-id="8ae1f-218">Função — instale e configure o DNS do Windows nos controladores de domínio.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="8ae1f-219">Endereços IP — use endereços IP dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-219">IP addresses — Use dynamic IP addresses.</span></span> <span data-ttu-id="8ae1f-220">Isso exige que você crie uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="8ae1f-220">This requires you to create an Azure Virtual Network.</span></span> 
    

