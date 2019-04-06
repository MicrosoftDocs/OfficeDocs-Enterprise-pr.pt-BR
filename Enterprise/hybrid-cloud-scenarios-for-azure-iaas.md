---
title: Cenários de nuvem híbrida para a IaaS do Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 'Resumo: entenda a arquitetura híbrida e os cenários para ofertas de nuvem com base na infraestrutura do Microsoft de serviço (IaaS) no Azure.'
ms.openlocfilehash: 5d125780e8baf3dbbe71b0878f6bf57cbeb5740f
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037925"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="bb509-103">Cenários de nuvem híbrida para a IaaS do Azure</span><span class="sxs-lookup"><span data-stu-id="bb509-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="bb509-104">**Resumo:** Compreenda a arquitetura híbrida e os cenários para ofertas de nuvem baseadas na infraestrutura da Microsoft como um serviço (IaaS) no Azure.</span><span class="sxs-lookup"><span data-stu-id="bb509-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="bb509-105">Estenda a infraestrutura de computação e identidade local para a nuvem hospedando cargas de trabalho de ti em execução em redes virtuais do Azure entre locais (VNets).</span><span class="sxs-lookup"><span data-stu-id="bb509-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="bb509-106">Arquitetura de cenário híbrido do Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="bb509-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="bb509-107">A Figura 1 mostra a arquitetura dos cenários híbridos baseados no Microsoft IaaS no Azure.</span><span class="sxs-lookup"><span data-stu-id="bb509-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="bb509-108">**Figura 1: cenários híbridos baseados no Microsoft IaaS no Azure**</span><span class="sxs-lookup"><span data-stu-id="bb509-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Cenários híbridos baseados no Microsoft IaaS no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="bb509-110">Para cada camada da arquitetura:</span><span class="sxs-lookup"><span data-stu-id="bb509-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="bb509-111">Aplicativos e cenários</span><span class="sxs-lookup"><span data-stu-id="bb509-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="bb509-112">Uma carga de trabalho de ti normalmente é um aplicativo de várias camadas e altamente disponível composto de VMs (máquinas virtuais) do Azure.</span><span class="sxs-lookup"><span data-stu-id="bb509-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="bb509-113">Identidade</span><span class="sxs-lookup"><span data-stu-id="bb509-113">Identity</span></span>
    
    <span data-ttu-id="bb509-114">Adicione servidores de identidade, como controladores de domínio do Windows Server AD, ao conjunto de servidores que estão sendo executados no Azure VNets para autenticação local.</span><span class="sxs-lookup"><span data-stu-id="bb509-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="bb509-115">Rede</span><span class="sxs-lookup"><span data-stu-id="bb509-115">Network</span></span>
    
    <span data-ttu-id="bb509-116">Use uma conexão VPN de site para site pela Internet ou uma conexão ExpressRoute com emparelhamento privado para o Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="bb509-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="bb509-117">Local</span><span class="sxs-lookup"><span data-stu-id="bb509-117">On-premises</span></span>
    
    <span data-ttu-id="bb509-118">Contém servidores de identidade que são sincronizados com os servidores de identidade em execução no Azure.</span><span class="sxs-lookup"><span data-stu-id="bb509-118">Contains identity servers that are synchronized with the identity servers running in Azure.</span></span> <span data-ttu-id="bb509-119">Também pode conter recursos que as VMs em execução no Azure podem acessar, como a infraestrutura de gerenciamento de armazenamento e de sistemas.</span><span class="sxs-lookup"><span data-stu-id="bb509-119">Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="bb509-120">Servidor de sincronização de diretório para o Office 365</span><span class="sxs-lookup"><span data-stu-id="bb509-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="bb509-121">Executar seu servidor de sincronização de diretório a partir de uma VNet do Azure, conforme mostrado na Figura 2, é um exemplo de estender sua infraestrutura de computação e identidade para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="bb509-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="bb509-122">**Figura 2: servidor de sincronização de diretório para o Office 365 no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="bb509-122">**Figure 2: Directory synchronization server for Office 365 in Azure IaaS**</span></span>

![Servidor de sincronização de diretório para o Office 365 no Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="bb509-124">Na Figura 2, uma rede local hospeda uma infraestrutura do AD do Windows Server, com um servidor proxy e um roteador em sua borda.</span><span class="sxs-lookup"><span data-stu-id="bb509-124">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge.</span></span> <span data-ttu-id="bb509-125">O roteador conecta-se a um gateway do Azure na borda de uma VNet do Azure com uma conexão VPN de site a site ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bb509-125">The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="bb509-126">Dentro da VNet, um servidor de sincronização de diretório executa o Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="bb509-126">Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="bb509-127">Um servidor de sincronização de diretório para O Office 365 sincroniza a lista de contas no Windows Server AD com o locatário do Azure AD de uma assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb509-127">A directory synchronization server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="bb509-128">Um servidor de sincronização de diretório é um servidor baseado em Windows que executa o Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="bb509-128">A directory synchronization server is a Windows-based server that runs Azure AD Connect.</span></span> <span data-ttu-id="bb509-129">Para o provisionamento mais rápido ou para reduzir o número de servidores locais em sua organização, implante seu servidor de sincronização de diretório em uma rede virtual (VNet) no Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="bb509-129">For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="bb509-130">O servidor de sincronização de diretório sonda as alterações no AD do Windows Server e as sincroniza com a assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb509-130">The directory synchronization server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="bb509-131">Para obter mais informações, consulte [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="bb509-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="bb509-132">Aplicativo de linha de negócios (LOB)</span><span class="sxs-lookup"><span data-stu-id="bb509-132">Line of business (LOB) application</span></span>

<span data-ttu-id="bb509-133">A Figura 3 mostra a configuração de um aplicativo LOB baseado em servidor executado no Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="bb509-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="bb509-134">**Figura 3: aplicativo LOB no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="bb509-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Aplicativo LOB baseado em servidor no Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="bb509-136">Na Figura 3, uma rede local hospeda uma infraestrutura de identidade e usuários.</span><span class="sxs-lookup"><span data-stu-id="bb509-136">In Figure 3, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="bb509-137">Ele está conectado a um gateway do Azure IaaS com uma conexão VPN de site a site ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bb509-137">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="bb509-138">O Azure IaaS hospeda uma rede virtual contendo os servidores do aplicativo LOB.</span><span class="sxs-lookup"><span data-stu-id="bb509-138">Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="bb509-139">Você pode criar aplicativos LOB executados em VMs do Azure, que residem em sub-redes de uma VNet do Azure em um datacenter do Azure (também conhecido como local).</span><span class="sxs-lookup"><span data-stu-id="bb509-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="bb509-140">Como você está essencialmente estendindo sua infraestrutura local para o Azure, você deve atribuir um espaço de endereçamento privado exclusivo ao seu VNets e atualizar suas tabelas de roteamento local para garantir a acessibilidade a cada VNet.</span><span class="sxs-lookup"><span data-stu-id="bb509-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="bb509-141">Depois de conectado, essas VMs podem ser gerenciadas com as conexões da área de trabalho remota ou com seu software de gerenciamento de sistema, assim como os servidores locais.</span><span class="sxs-lookup"><span data-stu-id="bb509-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="bb509-142">Configurando portas expostas publicamente, essas VMs também podem ser acessadas pela Internet por usuários móveis ou remotos.</span><span class="sxs-lookup"><span data-stu-id="bb509-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="bb509-143">Para obter uma configuração de prova de conceito, confira a [rede virtual de interlocalização entre locais no Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="bb509-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="bb509-144">Os atributos de aplicativos LOB hospedados nas VMs do Azure são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="bb509-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="bb509-145">Várias camadas</span><span class="sxs-lookup"><span data-stu-id="bb509-145">Multiple tiers</span></span>
    
    <span data-ttu-id="bb509-146">Aplicativos LOB típicos usam uma abordagem em camadas.</span><span class="sxs-lookup"><span data-stu-id="bb509-146">Typical LOB applications use a tiered approach.</span></span> <span data-ttu-id="bb509-147">Os conjuntos de servidores fornecem identidade, processamento de banco de dados, processamento de aplicativo e lógica e servidores Web front-end para acesso de funcionário ou de cliente.</span><span class="sxs-lookup"><span data-stu-id="bb509-147">Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="bb509-148">Alta disponibilidade</span><span class="sxs-lookup"><span data-stu-id="bb509-148">High availability</span></span>
    
    <span data-ttu-id="bb509-149">Aplicativos LOB típicos fornecem alta disponibilidade usando vários servidores em cada camada.</span><span class="sxs-lookup"><span data-stu-id="bb509-149">Typical LOB applications provide high availability by using multiple servers in each tier.</span></span> <span data-ttu-id="bb509-150">O Azure IaaS fornece um SLA de tempo de atividade de 99,9% para servidores nos conjuntos de disponibilidade do Azure.</span><span class="sxs-lookup"><span data-stu-id="bb509-150">Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="bb509-151">Distribuição de carga</span><span class="sxs-lookup"><span data-stu-id="bb509-151">Load distribution</span></span>
    
    <span data-ttu-id="bb509-152">Para distribuir a carga do tráfego de rede entre vários servidores em uma camada, você pode usar um balanceador de carga interno ou voltado para a Internet.</span><span class="sxs-lookup"><span data-stu-id="bb509-152">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer.</span></span> <span data-ttu-id="bb509-153">Ou você pode usar um dispositivo balanceador de carga dedicado disponível no Azure Marketplace.</span><span class="sxs-lookup"><span data-stu-id="bb509-153">Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="bb509-154">Segurança</span><span class="sxs-lookup"><span data-stu-id="bb509-154">Security</span></span>
    
    <span data-ttu-id="bb509-155">Para proteger os servidores de tráfego de entrada não solicitado da Internet, você pode usar os grupos de segurança de rede do Azure.</span><span class="sxs-lookup"><span data-stu-id="bb509-155">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups.</span></span> <span data-ttu-id="bb509-156">Você pode definir o tráfego permitido ou negado para uma sub-rede ou interface de rede de uma máquina virtual individual.</span><span class="sxs-lookup"><span data-stu-id="bb509-156">You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="bb509-157">Farm do SharePoint Server 2016 no Azure</span><span class="sxs-lookup"><span data-stu-id="bb509-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="bb509-158">Um exemplo de um aplicativo LOB de várias camadas e altamente disponível no Azure é um farm do SharePoint Server 2016, conforme mostrado na Figura 4.</span><span class="sxs-lookup"><span data-stu-id="bb509-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="bb509-159">**Figura 4: um farm do SharePoint Server 2016 de alta disponibilidade no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="bb509-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Um farm do SharePoint Server 2016 de alta disponibilidade no Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="bb509-161">Na Figura 4, uma rede local hospeda uma infraestrutura de identidade e usuários.</span><span class="sxs-lookup"><span data-stu-id="bb509-161">In Figure 4, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="bb509-162">Ele está conectado a um gateway do Azure IaaS com uma conexão VPN de site a site ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bb509-162">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="bb509-163">A VNet do Azure contém os servidores do farm do SharePoint Server 2016, que inclui camadas separadas para os servidores front-end, os servidores de aplicativos, o cluster do SQL Server e os controladores de domínio.</span><span class="sxs-lookup"><span data-stu-id="bb509-163">The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="bb509-164">Essa configuração tem os seguintes atributos de aplicativos LOB no Azure:</span><span class="sxs-lookup"><span data-stu-id="bb509-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="bb509-165">Camadas</span><span class="sxs-lookup"><span data-stu-id="bb509-165">Tiers</span></span>
    
    <span data-ttu-id="bb509-166">Servidores executando diferentes funções dentro do farm criam as camadas e cada camada tem sua própria sub-rede.</span><span class="sxs-lookup"><span data-stu-id="bb509-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="bb509-167">Alta disponibilidade</span><span class="sxs-lookup"><span data-stu-id="bb509-167">High-availability</span></span>
    
    <span data-ttu-id="bb509-168">Alcançado usando mais de um servidor em cada camada e colocando todos os servidores de uma camada no mesmo conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="bb509-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="bb509-169">Distribuição de carga</span><span class="sxs-lookup"><span data-stu-id="bb509-169">Load distribution</span></span>
    
    <span data-ttu-id="bb509-170">Balanceadores de carga internos do Azure distribuem o tráfego da Web do cliente de entrada para os servidores front-end (WEB1 e WEB2) e para o endereço IP do ouvinte do cluster do SQL Server (SQL1, SQL2 e MN1).</span><span class="sxs-lookup"><span data-stu-id="bb509-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="bb509-171">Segurança</span><span class="sxs-lookup"><span data-stu-id="bb509-171">Security</span></span>
    
    <span data-ttu-id="bb509-172">Os grupos de segurança de rede de cada sub-rede permitem configurar o tráfego de entrada e de saída permitido.</span><span class="sxs-lookup"><span data-stu-id="bb509-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="bb509-173">Siga este caminho para adoção bem-sucedida:</span><span class="sxs-lookup"><span data-stu-id="bb509-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="bb509-174">Avaliar e testar</span><span class="sxs-lookup"><span data-stu-id="bb509-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="bb509-175">Consulte [SharePoint server 2016 no Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) para compreender os benefícios da execução do sharepoint Server 2016 no Azure.</span><span class="sxs-lookup"><span data-stu-id="bb509-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="bb509-176">Consulte [intranet do SharePoint Server 2016 no ambiente de desenvolvimento/teste do Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) para criar um ambiente simulado de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="bb509-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="bb509-177">Design</span><span class="sxs-lookup"><span data-stu-id="bb509-177">Design</span></span>
    
    <span data-ttu-id="bb509-178">Consulte [Designing a SharePoint Server 2016 Farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) para percorrer um processo para determinar o conjunto de elementos de rede, computação e armazenamento do Azure IaaS para hospedar seu farm e suas configurações.</span><span class="sxs-lookup"><span data-stu-id="bb509-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="bb509-179">Implantar</span><span class="sxs-lookup"><span data-stu-id="bb509-179">Deploy</span></span>
    
    <span data-ttu-id="bb509-180">Consulte [deployIng SharePoint server 2016 with SQL Server AlwaysOn Availability groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) para percorrer a configuração de ponta a ponta do farm de alta disponibilidade em cinco fases.</span><span class="sxs-lookup"><span data-stu-id="bb509-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="bb509-181">Identidade federada para o Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="bb509-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="bb509-182">Outro exemplo de um aplicativo LOB de várias camadas e altamente disponível no Azure é a identidade federada para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb509-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="bb509-183">**Figura 5: uma infraestrutura de identidade federada de alta disponibilidade para o Office 365 no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="bb509-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Uma infraestrutura de autenticação federada de alta disponibilidade do Office 365 no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="bb509-185">Na Figura 5, uma rede local hospeda uma infraestrutura de identidade e usuários.</span><span class="sxs-lookup"><span data-stu-id="bb509-185">In Figure 5, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="bb509-186">Ele está conectado a um gateway do Azure IaaS com uma conexão VPN de site a site ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="bb509-186">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="bb509-187">A VNet do Azure contém servidores de proxy da Web, servidores de serviços de Federação do Active Directory (AD FS) e controladores de domínio do AD DS (serviços de domínio Active Directory).</span><span class="sxs-lookup"><span data-stu-id="bb509-187">The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Active Directory Domain Services (AD DS) domain controllers.</span></span>
  
<span data-ttu-id="bb509-188">Essa configuração tem os seguintes atributos de aplicativos LOB no Azure:</span><span class="sxs-lookup"><span data-stu-id="bb509-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="bb509-189">**Camadas:** Há camadas para servidores de proxy da Web, servidores do AD FS e controladores de domínio do Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="bb509-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="bb509-190">**Distribuição de carga:** Um balanceador de carga externo do Azure distribui as solicitações de autenticação de cliente de entrada para os proxies web e um balanceador de carga interno do Azure distribui solicitações de autenticação para os servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="bb509-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="bb509-191">Siga este caminho para adoção bem-sucedida:</span><span class="sxs-lookup"><span data-stu-id="bb509-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="bb509-192">Avaliar e testar</span><span class="sxs-lookup"><span data-stu-id="bb509-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="bb509-193">Consulte [identidade federada para seu ambiente de desenvolvimento/teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md) para criar um ambiente simulado de desenvolvimento/teste para autenticação federada com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb509-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="bb509-194">Implantar</span><span class="sxs-lookup"><span data-stu-id="bb509-194">Deploy</span></span>
    
    <span data-ttu-id="bb509-195">Consulte [implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para percorrer a configuração de ponta a ponta da infraestrutura do AD FS de alta disponibilidade em cinco fases.</span><span class="sxs-lookup"><span data-stu-id="bb509-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="bb509-196">Confira também</span><span class="sxs-lookup"><span data-stu-id="bb509-196">See Also</span></span>

[<span data-ttu-id="bb509-197">Nuvem híbrida da Microsoft para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="bb509-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="bb509-198">Recursos de arquitetura de TI da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="bb509-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


