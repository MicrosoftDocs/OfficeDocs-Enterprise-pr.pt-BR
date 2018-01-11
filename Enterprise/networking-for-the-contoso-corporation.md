---
title: Sistema de rede para a Contoso Corporation
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
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: "Resumo: Entenda a definição e elementos de nuvem da Microsoft híbrida."
ms.openlocfilehash: 0943864c8a9982eba00a139617ebe17d39cdde4e
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="56a78-103">Sistema de rede para a Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="56a78-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="56a78-104">**Resumo:** Compreenda a definição e elementos de nuvem da Microsoft híbrida.</span><span class="sxs-lookup"><span data-stu-id="56a78-104">**Summary:** Understand the definition and elements of Microsoft hybrid cloud.</span></span>
  
<span data-ttu-id="56a78-p101">Para adotar uma infra-estrutura inclusive de nuvem, engenheiros de rede da Contoso concretizados do turno fundamental da maneira que o tráfego de rede para viagens de serviços em nuvem. Em vez de apenas otimizar o tráfego para os servidores locais e data centers, igual atenção à otimização de tráfego até a borda da Internet e pela Internet.</span><span class="sxs-lookup"><span data-stu-id="56a78-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="56a78-107">Infraestrutura de rede da Contoso</span><span class="sxs-lookup"><span data-stu-id="56a78-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="56a78-108">A Contoso tem a infra-estrutura de rede mostrada na Figura 1.</span><span class="sxs-lookup"><span data-stu-id="56a78-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="56a78-109">**Figura 1: WAN de infra-estrutura da Contoso**</span><span class="sxs-lookup"><span data-stu-id="56a78-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![Infraestrutura WAN da Contoso conectando a sede, os centros regionais e as filiais](images/Contoso_Poster/Contoso_WW_Net.png)
  
<span data-ttu-id="56a78-111">A Figura 1 mostra os escritórios da Contoso em todo o mundo e o conjunto de regionais e links de WAN office satélite entre elas.</span><span class="sxs-lookup"><span data-stu-id="56a78-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="56a78-112">Elementos adicionais de sua rede são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="56a78-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="56a78-113">Rede local</span><span class="sxs-lookup"><span data-stu-id="56a78-113">On-premises network</span></span>
    
    <span data-ttu-id="56a78-p102">Links de WAN conectam as matrizes Paris para escritórios regionais e escritórios regionais em escritórios satélites em uma configuração de hub e spoke. Dentro de cada escritório, roteadores entregar o tráfego para hosts ou pontos de acesso sem fio em sub-redes, que usa o espaço de endereço IP particular.</span><span class="sxs-lookup"><span data-stu-id="56a78-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="56a78-116">Conectividade com a Internet</span><span class="sxs-lookup"><span data-stu-id="56a78-116">Internet connectivity</span></span>
    
    <span data-ttu-id="56a78-p103">Cada escritório tem seu próprio conectividade de Internet por meio de um servidor proxy. Isso geralmente é implementado como uma WAN link para um provedor de local que também fornece endereços IP públicos para o servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="56a78-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="56a78-119">Presença na Internet</span><span class="sxs-lookup"><span data-stu-id="56a78-119">Internet presence</span></span>
    
    <span data-ttu-id="56a78-p104">A Contoso possui o nome de domínio público de contoso.com. O site web público de Contoso para encomendar produtos é um conjunto de servidores em um datacenter conectados à Internet no campus Paris. A Contoso usa um /24 intervalo de endereços IP público na Internet.</span><span class="sxs-lookup"><span data-stu-id="56a78-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="56a78-123">Infraestrutura de app da Contoso</span><span class="sxs-lookup"><span data-stu-id="56a78-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="56a78-124">Arquitetura do Contoso criada sua infraestrutura de aplicativo e servidor para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="56a78-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="56a78-125">**Figura 2: Infra-estrutura da Contoso para aplicativos internos**</span><span class="sxs-lookup"><span data-stu-id="56a78-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Infraestrutura da Contoso para aplicativos internos](images/Contoso_Poster/App_Infra.png)
  
- <span data-ttu-id="56a78-127">Filiais usam servidores locais de armazenamento em cache para armazenar documentos acessados frequentemente e sites internos.</span><span class="sxs-lookup"><span data-stu-id="56a78-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="56a78-p105">Hubs regionais usam servidores de aplicativos regionais para regionais e de filiais. Esses servidores sincronizam com servidores na matriz da Paris.</span><span class="sxs-lookup"><span data-stu-id="56a78-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="56a78-130">O campus Paris tem os datacenters que contêm os servidores de aplicativos centralizado que atendem a toda a organização.</span><span class="sxs-lookup"><span data-stu-id="56a78-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="56a78-p106">Para usuários de satélite ou escritórios regionais de hub, 60% dos recursos necessários pelos funcionários podem ser atendidas por servidores do office hub regionais e de satélite. Vincular a 40% adicionais de recurso solicitações devem passar pela WAN campus da Paris.</span><span class="sxs-lookup"><span data-stu-id="56a78-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="56a78-133">Análise de rede da Contoso</span><span class="sxs-lookup"><span data-stu-id="56a78-133">Contoso's network analysis</span></span>

<span data-ttu-id="56a78-134">Aqui estão os resultados da análise da Contoso das alterações necessárias em sua rede para acomodar as diferentes categorias de ofertas de nuvem da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="56a78-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="56a78-135">**SaaS ofertas de nuvem: Office 365, EMS e Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="56a78-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="56a78-136">**Azure PaaS: Aplicativos móveis**</span><span class="sxs-lookup"><span data-stu-id="56a78-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="56a78-137">**Windows Azure IaaS: Cargas de trabalho baseado em servidor**</span><span class="sxs-lookup"><span data-stu-id="56a78-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="56a78-138">Adoção bem-sucedida dos serviços de SaaS pelos usuários depende altamente disponível e de alto desempenho conectividade à Internet ou diretamente aos serviços de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="56a78-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="56a78-139">Para usuários móveis, seu acesso à Internet atual é assumido para ser adequado.</span><span class="sxs-lookup"><span data-stu-id="56a78-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="56a78-140">Para os usuários na intranet da Contoso, cada escritório deve ser analisado e otimizado para taxa de transferência para a Internet e tempos de ida e volta para os locatários do Office 365, EMS e Dynamics 365 de hospedagem do datacenter de Europa da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="56a78-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="56a78-p107">Os funcionários móveis da melhor suporte, aplicativos herdados e alguns sites de compartilhamento de arquivo estão sendo refeitas e implantados como aplicativos do Windows Azure PaaS. Para obter o desempenho ideal, Contoso planeja implantar aplicativos novos a partir de vários centros de dados Azure no mundo inteiro. Gerenciador de tráfego do Azure para enviar o cliente solicitações de aplicativos, se elas se originam de um usuário móvel ou em um computador no escritório, para o datacenter do Windows Azure mais próximo do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="56a78-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="56a78-144">O departamento de TI precisará adicionar PaaS o desempenho de aplicativos e distribuição de tráfego à sua solução de monitoramento de integridade de rede.</span><span class="sxs-lookup"><span data-stu-id="56a78-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="56a78-145">Para mover alguns servidores herdados e arquivamento sem os datacenters de campus Paris e adicionar servidores conforme necessário para o processamento de ponta trimestre, Contoso planeja usar máquinas virtuais executando nos serviços de infraestrutura do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="56a78-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="56a78-146">As redes virtuais do Azure que contêm esses servidores devem ser projetadas para espaços de endereçamento não sobrepostos, DNS roteamento e integrada.</span><span class="sxs-lookup"><span data-stu-id="56a78-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="56a78-147">O departamento de TI deve incluir esses novos servidores em seus gerenciamento de rede e o sistema de monitoramento.</span><span class="sxs-lookup"><span data-stu-id="56a78-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="56a78-148">Uso da Contoso do ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="56a78-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="56a78-p108">ExpressRoute é uma conexão WAN dedicada de seu local para um local de correspondência do Microsoft que se conecta a sua rede a rede de nuvem da Microsoft. As conexões de ExpressRoute oferecem desempenho previsível e um SLA do tempo de atividade de 99,9%. .</span><span class="sxs-lookup"><span data-stu-id="56a78-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="56a78-p109">Com uma conexão ExpressRoute, você está conectado à rede de nuvem da Microsoft e todos os locais de datacenter Microsoft no mesmo continente. O tráfego entre o local de correspondência da nuvem e o datacenter da Microsoft de destino é transmitido a rede de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="56a78-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="56a78-154">**Figura 3: A Microsoft cloud rede mundial**</span><span class="sxs-lookup"><span data-stu-id="56a78-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![A rede de nuvem da Microsoft em todo o mundo](images/Contoso_Poster/MS_WW_Cloud.png)
  
<span data-ttu-id="56a78-156">A Figura 3 mostra a rede de nuvem Microsoft interconexão para as diversas regiões do mundo.</span><span class="sxs-lookup"><span data-stu-id="56a78-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="56a78-p110">Com o ExpressRoute Premium, você poderá encontrá-qualquer datacenter da Microsoft em qualquer continente de qualquer local de correspondência da Microsoft em qualquer continente. O tráfego entre continentes é realizado através da rede de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="56a78-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="56a78-159">Com base na análise de tráfego atual e futuro para as ofertas de nuvem da Microsoft, a Contoso tem realizou uma avaliação de rede e implementado uma conexão ExpressRoute (baseado em MPLS) para qualquer para acesso aos recursos do Windows Azure, com correspondência pública e privada relações de confiança, das matrizes Paris até o local de correspondência da Microsoft na Europa.</span><span class="sxs-lookup"><span data-stu-id="56a78-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="56a78-160">Esta conexão fornecerá a Contoso departamento de TI:</span><span class="sxs-lookup"><span data-stu-id="56a78-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="56a78-161">Desempenho consistente para a administração dos aplicativos do Windows Azure PaaS distribuídas</span><span class="sxs-lookup"><span data-stu-id="56a78-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="56a78-p111">Todos de desenvolvedores de aplicativos e a infraestrutura principal IT da Contoso, os administradores são no campus Paris. Com aplicativos do Azure PaaS distribuídos para diferentes datacenters Azure em todo o mundo, a Contoso precisa desempenho consistente do campus da Paris para administrar os aplicativos e seus recursos de armazenamento, que consistem em TB de documentos.</span><span class="sxs-lookup"><span data-stu-id="56a78-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="56a78-164">Desempenho consistente para a administração de servidores no Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="56a78-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="56a78-p112">Administradores de datacenter da Contoso estão em campus da Paris e os servidores a serem implantados no Azure são uma extensão do datacenter Paris. A Contoso precisa desempenho consistente para esses novos servidores para acessar aplicativos herdados e armazenamento de arquivamento e para o processamento de final de trimestre.</span><span class="sxs-lookup"><span data-stu-id="56a78-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="56a78-167">Caminho da Contoso para preparação de rede em nuvem</span><span class="sxs-lookup"><span data-stu-id="56a78-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="56a78-168">A Contoso usa as seguintes etapas para preparar sua rede para a nuvem da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="56a78-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="56a78-169">Otimizar os computadores dos funcionários para acesso à Internet</span><span class="sxs-lookup"><span data-stu-id="56a78-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="56a78-170">Computadores individuais serão verificados para garantir que a pilha de TCP/IP mais recente, navegador, os drivers de placa de rede e atualizações de segurança e o sistema operacional estão instaladas.</span><span class="sxs-lookup"><span data-stu-id="56a78-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="56a78-171">Analisar a utilização de conexão de Internet em cada escritório e aumentar conforme necessário</span><span class="sxs-lookup"><span data-stu-id="56a78-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="56a78-172">Cada escritório será analisado para o uso de Internet atual e a largura de banda do link WAN será aumentada se operando 70% ou acima de utilização.</span><span class="sxs-lookup"><span data-stu-id="56a78-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="56a78-173">Analisar sistemas DMZ em cada escritório para um desempenho ideal</span><span class="sxs-lookup"><span data-stu-id="56a78-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="56a78-p113">Firewalls, IDSs e outros sistemas no caminho da Internet serão analisados para um desempenho ideal. Servidores proxy serão atualizados ou atualizados conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="56a78-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="56a78-176">Adicionar ExpressRoute do campus da Paris</span><span class="sxs-lookup"><span data-stu-id="56a78-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="56a78-177">Fornece acesso uniforme aos recursos do Windows Azure para a administração de cargas de trabalho Azure PaaS e IaaS.</span><span class="sxs-lookup"><span data-stu-id="56a78-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="56a78-178">Criar e testar um perfil do Gerenciador de tráfego do Windows Azure para aplicativos do Windows Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="56a78-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="56a78-179">Teste um perfil do Gerenciador de tráfego do Azure que usa o método de roteamento de desempenho adquira experiência nos distribuir o tráfego da Internet para escritórios regionais.</span><span class="sxs-lookup"><span data-stu-id="56a78-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="56a78-180">Reservar espaço de endereço privado para VNets do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="56a78-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="56a78-181">Com base nos números dos servidores projetados de curtos e longo prazo no Azure IaaS, reserve espaço de endereço privado para VNets do Windows Azure e suas sub-redes.</span><span class="sxs-lookup"><span data-stu-id="56a78-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="56a78-182">Veja também</span><span class="sxs-lookup"><span data-stu-id="56a78-182">See Also</span></span>

[<span data-ttu-id="56a78-183">Contoso na Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="56a78-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="56a78-184">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="56a78-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="56a78-185">Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="56a78-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



