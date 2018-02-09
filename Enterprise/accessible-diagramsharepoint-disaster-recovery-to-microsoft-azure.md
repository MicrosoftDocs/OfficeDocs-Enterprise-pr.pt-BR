---
title: "Diagrama acessível - recuperação de desastres do SharePoint para o Microsoft Azure"
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
description: "Este artigo é uma versão de texto acessível do diagrama chamado de recuperação de desastres do SharePoint para o Microsoft Azure."
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="92090-103">Diagrama acessível - recuperação de desastres do SharePoint para o Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="92090-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="92090-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado de recuperação de desastres do SharePoint para o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="92090-105">Este cartaz fornece exemplos de arquiteturas para a criação de um ambiente de recuperação no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="92090-106">Ambiente de local com um ambiente de recuperação do Azure</span><span class="sxs-lookup"><span data-stu-id="92090-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="92090-107">O diagrama mostra um exemplo de arquitetura usado para o ambiente de produção de um ambiente de local que usa o Windows Azure para recuperação.</span><span class="sxs-lookup"><span data-stu-id="92090-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="92090-108">Ambiente de produção do local</span><span class="sxs-lookup"><span data-stu-id="92090-108">On-premises production environment</span></span>

<span data-ttu-id="92090-109">O diagrama acompanha mostra um ambiente de produção ao vivo com quatro níveis de servidores em um farm de servidores.</span><span class="sxs-lookup"><span data-stu-id="92090-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="92090-110">Nível 1</span><span class="sxs-lookup"><span data-stu-id="92090-110">Tier 1</span></span>

<span data-ttu-id="92090-p101">Há dois servidores de serviços de front-end e processamento de consultas. Não há uma partição do índice que fornece uma réplica de ambos os servidores.</span><span class="sxs-lookup"><span data-stu-id="92090-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="92090-113">Camada 2</span><span class="sxs-lookup"><span data-stu-id="92090-113">Tier 2</span></span>

<span data-ttu-id="92090-114">Há dois servidores de cache distribuído nesse nível.</span><span class="sxs-lookup"><span data-stu-id="92090-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="92090-115">Camada 3</span><span class="sxs-lookup"><span data-stu-id="92090-115">Tier 3</span></span>

<span data-ttu-id="92090-p102">Há três servidores nesse nível. Cada servidor fornece os seguintes serviços:</span><span class="sxs-lookup"><span data-stu-id="92090-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="92090-118">Serviços de back-end</span><span class="sxs-lookup"><span data-stu-id="92090-118">Backend services</span></span> 
    
- <span data-ttu-id="92090-119">Administrador</span><span class="sxs-lookup"><span data-stu-id="92090-119">Admin</span></span> 
    
- <span data-ttu-id="92090-120">Gerenciador de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="92090-120">Workflow manager</span></span> 
    
- <span data-ttu-id="92090-121">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="92090-121">Crawl</span></span> 
    
- <span data-ttu-id="92090-122">Processamento de conteúdo</span><span class="sxs-lookup"><span data-stu-id="92090-122">Content processing</span></span> 
    
- <span data-ttu-id="92090-123">Análise</span><span class="sxs-lookup"><span data-stu-id="92090-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="92090-124">Nível 4</span><span class="sxs-lookup"><span data-stu-id="92090-124">Tier 4</span></span>

<span data-ttu-id="92090-p103">Há dois servidores nesse nível. Ambos os servidores têm três grupos de disponibilidade, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="92090-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="92090-127">Grupo de disponibilidade #1 fornece recursos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="92090-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="92090-128">Grupo de disponibilidade #2 fornece conteúdo, configuração e aplicativos de serviço.</span><span class="sxs-lookup"><span data-stu-id="92090-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="92090-129">Grupo de disponibilidade #3 fornece conteúdo.</span><span class="sxs-lookup"><span data-stu-id="92090-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="92090-p104">Também é um servidor nesse nível de compartilhamento de arquivo. Os servidores de camada 4 usam o envio de logs para se comunicar com este servidor. Este servidor, por sua vez, comunica-se via distribuído arquivo sistema replicação (DFSR) para um servidor de compartilhamento de arquivos no ambiente de recuperação de espera passiva Azure, conforme descrito na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="92090-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="92090-133">Ambiente de recuperação do Azure</span><span class="sxs-lookup"><span data-stu-id="92090-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="92090-134">Ambiente de em espera passiva máquinas virtuais em execução</span><span class="sxs-lookup"><span data-stu-id="92090-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="92090-p105">O diagrama acompanha mostra o ambiente local replicado exatamente no ambiente de recuperação do Azure. O servidor de compartilhamento de arquivos nesse ambiente está vinculado DFSR do ambiente local. DFSR transfere logs do ambiente de produção para o ambiente de recuperação por meio do servidor de compartilhamento de arquivo.</span><span class="sxs-lookup"><span data-stu-id="92090-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="92090-138">Visão geral</span><span class="sxs-lookup"><span data-stu-id="92090-138">Overview</span></span>

<span data-ttu-id="92090-139">O ambiente de recuperação de desastres para um farm do SharePoint 2013 no local pode ser hospedado no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="92090-140">Serviços de infraestrutura Azure fornece um datacenter secundário.</span><span class="sxs-lookup"><span data-stu-id="92090-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="92090-141">Preste apenas para os recursos usados.</span><span class="sxs-lookup"><span data-stu-id="92090-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="92090-142">Farms de recuperação pequenas podem ser dimensionados após um desastre para cumprir as metas de dimensionamento e capacidade.</span><span class="sxs-lookup"><span data-stu-id="92090-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="92090-143">O farm de recuperação no Windows Azure é configurado como identicamente possível ao farm do local de produção.</span><span class="sxs-lookup"><span data-stu-id="92090-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="92090-144">Mesma representação das funções de servidor.</span><span class="sxs-lookup"><span data-stu-id="92090-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="92090-145">Mesma configuração das personalizações.</span><span class="sxs-lookup"><span data-stu-id="92090-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="92090-146">Mesma configuração de recursos de pesquisa (essas podem estar em uma versão menor do que o farm de produção).</span><span class="sxs-lookup"><span data-stu-id="92090-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="92090-147">Envio de logs e DFSR são usados para copiar backups de banco de dados e logs de transação para o farm do Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="92090-p106">DFSR é usado para transferir os logs do ambiente de produção para o ambiente de recuperação. Em um cenário WAN, DFSR é mais eficiente do que os logs diretamente para o servidor secundário de envio no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="92090-150">Logs são reproduzidos nos computadores com base no Windows Azure SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92090-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="92090-151">Bancos de dados enviados com logs não são anexados ao farm até que um exercício de recuperação é executado.</span><span class="sxs-lookup"><span data-stu-id="92090-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="92090-152">Procedimentos de failover:</span><span class="sxs-lookup"><span data-stu-id="92090-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="92090-153">Pare o envio de log.</span><span class="sxs-lookup"><span data-stu-id="92090-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="92090-154">Pare de aceitar o tráfego para o farm principal.</span><span class="sxs-lookup"><span data-stu-id="92090-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="92090-155">Repetição durante os logs de transações final.</span><span class="sxs-lookup"><span data-stu-id="92090-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="92090-156">Anexe os bancos de dados de conteúdo ao farm.</span><span class="sxs-lookup"><span data-stu-id="92090-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="92090-157">Inicie um rastreamento completo.</span><span class="sxs-lookup"><span data-stu-id="92090-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="92090-158">Restaure aplicativos de serviço dos bancos de dados replicados.</span><span class="sxs-lookup"><span data-stu-id="92090-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="92090-159">Objetivos de recuperação fornecidos por essa solução incluem:</span><span class="sxs-lookup"><span data-stu-id="92090-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="92090-160">Sites e conteúdo</span><span class="sxs-lookup"><span data-stu-id="92090-160">Sites and content</span></span> 
    
- <span data-ttu-id="92090-161">Pesquisa (novamente não rastreado, nenhum histórico de pesquisa)</span><span class="sxs-lookup"><span data-stu-id="92090-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="92090-162">Serviços</span><span class="sxs-lookup"><span data-stu-id="92090-162">Services</span></span>
    
<span data-ttu-id="92090-163">Itens adicionais que podem ser abordados por um parceiro ou de serviços de consultoria da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="92090-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="92090-164">Sincronizando soluções personalizadas do farm</span><span class="sxs-lookup"><span data-stu-id="92090-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="92090-165">Conexões com fontes de dados no local (conectividade de dados corporativos (BDC) e pesquisar fontes de conteúdo)</span><span class="sxs-lookup"><span data-stu-id="92090-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="92090-166">Cenários de restauração de pesquisa</span><span class="sxs-lookup"><span data-stu-id="92090-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="92090-167">Objetivos de tempo de recuperação (RTO) e objetivos de ponto de recuperação (RPO)</span><span class="sxs-lookup"><span data-stu-id="92090-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="92090-168">Ambiente de em espera a frio máquinas virtuais em execução</span><span class="sxs-lookup"><span data-stu-id="92090-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="92090-169">Ambientes de espera a frio demoram mais para iniciar, mas são baratos.</span><span class="sxs-lookup"><span data-stu-id="92090-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="92090-p107">O farm totalmente é criado, mas as máquinas virtuais são interrompidas depois que o farm é criado. Você paga apenas os custos de processamento quando as máquinas virtuais estão funcionando, mas aplicam custos de transferência de dados de armazenamento e de rede.</span><span class="sxs-lookup"><span data-stu-id="92090-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="92090-172">Em caso de desastre, todas as máquinas virtuais do farm foram iniciadas e corrigidas.</span><span class="sxs-lookup"><span data-stu-id="92090-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="92090-173">Backups e logs de transações são aplicados nos bancos de dados do farm.</span><span class="sxs-lookup"><span data-stu-id="92090-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="92090-174">A lista a seguir descreve os procedimentos adicionais para ambientes de espera a frio:</span><span class="sxs-lookup"><span data-stu-id="92090-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="92090-175">Ative máquinas virtuais regularmente para o patch, atualizar e verificar o ambiente.</span><span class="sxs-lookup"><span data-stu-id="92090-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="92090-176">Execute os procedimentos para atualizar o DNS e endereços IP.</span><span class="sxs-lookup"><span data-stu-id="92090-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="92090-177">Configure SQL AlwaysOn após um failover.</span><span class="sxs-lookup"><span data-stu-id="92090-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="92090-p108">O diagrama acompanha mostra um ambiente de recuperação replicado nas máquinas virtuais. Após o failover para um ambiente em espera a frio, todas as máquinas virtuais são iniciadas e os grupos de disponibilidade são configurados usando logs de repetição para disponibilizar os servidores de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="92090-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="92090-180">Ambiente de recuperação do SharePoint no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="92090-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="92090-181">Projetar e criar o ambiente de failover no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="92090-182">Crie uma rede virtual no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="92090-p109">Conecte a rede local com a rede virtual no Windows Azure com uma conexão de VPN-to-site. Esta conexão utiliza um gateway dinâmico no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="92090-p110">Implantar um ou mais controladores de domínio para a rede virtual do Azure e configurá-los para trabalhar com seu domínio local. Esses controladores de domínio são servidores de catálogo.</span><span class="sxs-lookup"><span data-stu-id="92090-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="92090-187">Adaptar-se o farm do SharePoint para conjuntos de disponibilidade e de serviços de nuvem.</span><span class="sxs-lookup"><span data-stu-id="92090-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="92090-188">Implante o farm do SharePoint mais de um servidor de arquivos em compartilhamentos de arquivos de host.</span><span class="sxs-lookup"><span data-stu-id="92090-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="92090-189">Configure o envio de log e DFSR entre o ambiente local e o ambiente de recuperação baseada no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="92090-190">O diagrama acompanha mostra o ambiente local e a rede virtual do Azure com os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="92090-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="92090-191">Ambiente no local</span><span class="sxs-lookup"><span data-stu-id="92090-191">On-premises environment</span></span>

- <span data-ttu-id="92090-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="92090-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="92090-193">Servidor do Active Directory</span><span class="sxs-lookup"><span data-stu-id="92090-193">Active Directory server</span></span> 
    
<span data-ttu-id="92090-194">As interfaces de rede local com a rede virtual do Azure através de um gateway de rede virtual privada (VPN).</span><span class="sxs-lookup"><span data-stu-id="92090-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="92090-195">Rede virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="92090-195">Azure virtual network</span></span>

<span data-ttu-id="92090-196">As interfaces de gateway VPN com uma sub-rede de gateway VPN ativa.</span><span class="sxs-lookup"><span data-stu-id="92090-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="92090-197">Há três serviços de nuvem a rede virtual do Azure:</span><span class="sxs-lookup"><span data-stu-id="92090-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="92090-198">O primeiro serviço de nuvem tem dois Active Directory e servidores DNS com uma disponibilidade definida.</span><span class="sxs-lookup"><span data-stu-id="92090-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="92090-p111">O serviço de nuvem segundo tem três conjuntos de servidores: dois servidores de cache com um conjunto de disponibilidade de distribuídos. Dois servidores front-end com um conjunto de disponibilidade. Três servidores back-end com um conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="92090-p111">The second cloud service has three sets of servers: Two distributed cache servers with an availability set. Two front-end servers with an availability set. Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="92090-p112">O serviço de nuvem terceiro tem três servidores de banco de dados com um conjunto de disponibilidade. Um desses servidores de banco de dados é um compartilhamento de arquivo para o nó de uma terceira e de envio de log da maioria nó para SQL Server AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="92090-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="92090-204">Criar o ambiente híbrido do AD DS</span><span class="sxs-lookup"><span data-stu-id="92090-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="92090-205">A configuração do AD DS para essa solução constitui um cenário de implantação híbrido no qual o AD DS é parcialmente implantados no local e parcialmente implantadas em máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="92090-206">Importante — Antes de implantar o AD DS no Windows Azure, leia as diretrizes para implantar o Windows Server Active Directory no Microsoft máquinas virtuais do Azure (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span><span class="sxs-lookup"><span data-stu-id="92090-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="92090-207">Para obter orientação completa sobre como projetar e implantar ambientes do Active Directory, consulte http://TechNet.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="92090-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="92090-p113">Essa arquitetura de referência inclui duas máquinas virtuais configuradas como controladores de domínio. Cada uma é configurada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="92090-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="92090-210">Tamanho — pequeno.</span><span class="sxs-lookup"><span data-stu-id="92090-210">Size — Small.</span></span> 
    
- <span data-ttu-id="92090-211">Sistema operacional — Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="92090-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="92090-p114">Função — Controlador de domínio de AD DS designado como um servidor de catálogo global. Essa configuração reduz o tráfego de saída entre a conexão VPN. Em um ambiente de vários domínio com altas taxas de alteração, configure o domínio controladores local não sincronizar com os servidores de catálogo global no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="92090-p115">Discos de dados — colocar o banco de dados do AD DS, logs e SYSVOL em discos de dados do Azure. Não coloque essas do disco de sistema operacional ou os discos temporários fornecidos pelo Windows Azure. Isso é importante.</span><span class="sxs-lookup"><span data-stu-id="92090-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="92090-218">Função — Instalar e configurar o DNS do Windows nos controladores de domínio.</span><span class="sxs-lookup"><span data-stu-id="92090-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="92090-p116">Endereços IP — usar endereços IP dinâmicos. Isso exige a criação de uma rede Virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="92090-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

