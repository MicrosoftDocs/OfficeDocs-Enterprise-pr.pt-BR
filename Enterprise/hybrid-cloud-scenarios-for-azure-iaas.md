---
title: "Cenários de nuvem híbrida para o Windows Azure IaaS"
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
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "Resumo: Entenda os cenários e arquitetura híbrida para a infra-estrutura da Microsoft como um serviço (IaaS)-based ofertas de nuvem no Windows Azure."
ms.openlocfilehash: 5ec74058174724b6497a5cb41e67896818ef4d05
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="68f9a-103">Cenários de nuvem híbrida para o Windows Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="68f9a-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="68f9a-104">**Resumo:** Entenda os cenários e arquitetura híbrida para a infra-estrutura da Microsoft como um serviço (IaaS)-based ofertas de nuvem no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="68f9a-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="68f9a-105">Estender sua computação no local e a infra-estrutura de identidades em nuvem hospedando cargas de trabalho do IT executando em locais cruzados redes virtuais do Azure (VNets).</span><span class="sxs-lookup"><span data-stu-id="68f9a-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="68f9a-106">Arquitetura de cenário do Windows Azure IaaS híbrida</span><span class="sxs-lookup"><span data-stu-id="68f9a-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="68f9a-107">A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em IaaS Microsoft no Azure.</span><span class="sxs-lookup"><span data-stu-id="68f9a-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="68f9a-108">**Figura 1: Cenários de implantação híbrida baseada em IaaS Microsoft no Azure**</span><span class="sxs-lookup"><span data-stu-id="68f9a-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Cenários híbridos da Microsoft baseados em IaaS no Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS.png)
  
<span data-ttu-id="68f9a-110">Para cada camada da arquitetura:</span><span class="sxs-lookup"><span data-stu-id="68f9a-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="68f9a-111">Cenários e aplicativos</span><span class="sxs-lookup"><span data-stu-id="68f9a-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="68f9a-112">Uma carga de trabalho de TI é geralmente uma de várias camadas, aplicativo altamente disponível composto de máquinas virtuais do Azure (VMs).</span><span class="sxs-lookup"><span data-stu-id="68f9a-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="68f9a-113">Identidade</span><span class="sxs-lookup"><span data-stu-id="68f9a-113">Identity</span></span>
    
    <span data-ttu-id="68f9a-114">Adicione servidores de identidade, como controladores de domínio do Windows Server AD, ao conjunto de servidores que executam em VNets do Windows Azure para a autenticação local.</span><span class="sxs-lookup"><span data-stu-id="68f9a-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="68f9a-115">Rede</span><span class="sxs-lookup"><span data-stu-id="68f9a-115">Network</span></span>
    
    <span data-ttu-id="68f9a-116">Use uma conexão de VPN-to-site via Internet ou uma conexão ExpressRoute com correspondência privada para Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="68f9a-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="68f9a-117">Local</span><span class="sxs-lookup"><span data-stu-id="68f9a-117">On-premises</span></span>
    
    <span data-ttu-id="68f9a-p101">Contém os servidores de identidade que são sincronizados com os servidores de identidade em execução no Windows Azure. Também pode conter recursos que podem acessar VMs em execução no Azure, como a infraestrutura de gerenciamento de armazenamento e sistemas.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="dirsync-server-for-office-365"></a><span data-ttu-id="68f9a-120">Servidor DirSync para o Office 365</span><span class="sxs-lookup"><span data-stu-id="68f9a-120">DirSync server for Office 365</span></span>

<span data-ttu-id="68f9a-121">Executar o seu servidor de sincronização (DirSync) do diretório de um VNet do Azure, conforme mostrado na Figura 2, é um exemplo de estendendo sua infra-estrutura de computação e identidade para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="68f9a-121">Running your directory synchronization (DirSync) server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="68f9a-122">**Figura 2: Servidor de DirSync para o Office 365 no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="68f9a-122">**Figure 2: DirSync server for Office 365 in Azure IaaS**</span></span>

![Servidor DirSync para Office 365 no Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_DirSync.png)
  
<span data-ttu-id="68f9a-p102">Na Figura 2, uma rede local hospeda uma infraestrutura do Windows Server AD, com um servidor proxy e um roteador em sua borda. O roteador conecta-se para um gateway Azure na extremidade de uma VNet Azure com uma conexão de VPN ou ExpressRoute-to-site. Dentro do VNet, um servidor DirSync executa Connect do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a DirSync server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="68f9a-127">Um servidor DirSync para o Office 365 sincroniza a lista de contas no Windows Server AD com o locatário do Azure AD de uma assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="68f9a-127">A DirSync server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="68f9a-p103">Um servidor de DirSync é um servidor baseado no Windows que executa o Connect do Azure AD. Para provisionamento mais rápidos ou reduzir o número de servidores locais em sua organização, implante seu servidor DirSync em uma rede virtual (VNet) no Windows Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p103">A DirSync server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your DirSync server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="68f9a-130">O servidor DirSync sonda Windows Server AD para que as alterações e sincroniza-los com assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="68f9a-130">The DirSync server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="68f9a-131">Para obter mais informações, consulte [Implantar o Office 365 DirSync no Windows Azure](https://technet.microsoft.com/library/dn635310.aspx).</span><span class="sxs-lookup"><span data-stu-id="68f9a-131">For more information, see [Deploy Office 365 DirSync in Azure](https://technet.microsoft.com/library/dn635310.aspx).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="68f9a-132">Linha do aplicativo de negócios (LOB)</span><span class="sxs-lookup"><span data-stu-id="68f9a-132">Line of business (LOB) application</span></span>

<span data-ttu-id="68f9a-133">A Figura 3 mostra a configuração de um aplicativo de LOB baseado em servidor está em execução no Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="68f9a-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="68f9a-134">**Figura 3: Aplicativos de LOB no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="68f9a-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Aplicativo LOB baseado em servidor na IaaS do Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_Ex.png)
  
<span data-ttu-id="68f9a-p104">Na Figura 3, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão de VPN ou ExpressRoute-to-site. Azure IaaS hospeda uma rede virtual que contém os servidores do aplicativo LOB.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="68f9a-139">Você pode criar aplicativos de LOB executados em máquinas virtuais do Windows Azure, que residem em sub-redes de uma VNet do Windows Azure em um datacenter do Windows Azure (também conhecido como um local).</span><span class="sxs-lookup"><span data-stu-id="68f9a-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="68f9a-140">Porque você essencialmente estiver estendendo sua infraestrutura local no Azure, você deve atribuir o espaço de endereço privado exclusivo ao seu VNets e atualizar o seu local tabelas de roteamento para garantir o alcance a cada VNet.</span><span class="sxs-lookup"><span data-stu-id="68f9a-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="68f9a-141">Uma vez conectado, essas VMs podem ser gerenciadas com conexões de área de trabalho remota ou com o software de gerenciamento de sistemas, assim como os servidores no local.</span><span class="sxs-lookup"><span data-stu-id="68f9a-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="68f9a-142">Configurando portas expostas publicamente, essas VMs também podem ser acessados pela Internet por usuários remotos ou móveis.</span><span class="sxs-lookup"><span data-stu-id="68f9a-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="68f9a-143">Para uma configuração de prova de conceito, consulte [simuladas locais cruzados rede virtual no Windows Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="68f9a-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="68f9a-144">Atributos de aplicativos de LOB hospedados em máquinas virtuais do Windows Azure são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="68f9a-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="68f9a-145">Vários níveis</span><span class="sxs-lookup"><span data-stu-id="68f9a-145">Multiple tiers</span></span>
    
    <span data-ttu-id="68f9a-p105">Os aplicativos de LOB típicos usam uma abordagem hierárquica. Conjuntos de servidores fornecem a identidade, processamento de banco de dados, aplicativo e processamento de lógica e servidores web front-end para acesso de funcionários ou clientes.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="68f9a-148">Alta disponibilidade</span><span class="sxs-lookup"><span data-stu-id="68f9a-148">High availability</span></span>
    
    <span data-ttu-id="68f9a-p106">Os aplicativos de LOB típicos fornecem alta disponibilidade por meio de vários servidores em cada camada. Azure IaaS fornece um SLA do tempo de atividade de 99,9% para servidores em conjuntos de disponibilidade do Azure.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="68f9a-151">Distribuição de carga</span><span class="sxs-lookup"><span data-stu-id="68f9a-151">Load distribution</span></span>
    
    <span data-ttu-id="68f9a-p107">Para distribuir a carga de tráfego de rede entre vários servidores em uma camada, você pode usar um balanceador de carga de Azure voltado à Internet ou interna. Ou então, você pode usar um aparelho de Balanceador de carga dedicado disponível no Azure marketplace.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="68f9a-154">Segurança</span><span class="sxs-lookup"><span data-stu-id="68f9a-154">Security</span></span>
    
    <span data-ttu-id="68f9a-p108">Para proteger os servidores de tráfego de entrada não solicitado da Internet, você pode usar grupos de segurança de rede do Windows Azure. Você pode definir permitido ou negado o tráfego de uma sub-rede ou a interface de rede de uma máquina virtual individual.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="68f9a-157">Farm do SharePoint Server 2016 no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="68f9a-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="68f9a-158">Um exemplo de um de várias camadas, os aplicativos LOB altamente disponível no Windows Azure é um farm do SharePoint Server 2016, conforme mostrado na Figura 4.</span><span class="sxs-lookup"><span data-stu-id="68f9a-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="68f9a-159">**Figura 4: Um farm de SharePoint Server 2016 de alta disponibilidade no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="68f9a-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Farm de alta disponibilidade do SharePoint Server 2016 no Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_SP2016.png)
  
<span data-ttu-id="68f9a-p109">Na Figura 4, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão de VPN ou ExpressRoute-to-site. VNet o Azure contém os servidores do farm do SharePoint Server 2016, que inclui as camadas separadas para os servidores front-end, servidores de aplicativos, o cluster do SQL Server e os controladores de domínio.</span><span class="sxs-lookup"><span data-stu-id="68f9a-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="68f9a-164">Esta configuração tem os seguintes atributos de aplicativos LOB no Windows Azure:</span><span class="sxs-lookup"><span data-stu-id="68f9a-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="68f9a-165">Camadas</span><span class="sxs-lookup"><span data-stu-id="68f9a-165">Tiers</span></span>
    
    <span data-ttu-id="68f9a-166">Servidores que executam funções diferentes dentro do farm criam as camadas, e cada camada tem sua própria sub-rede.</span><span class="sxs-lookup"><span data-stu-id="68f9a-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="68f9a-167">Alta disponibilidade</span><span class="sxs-lookup"><span data-stu-id="68f9a-167">High-availability</span></span>
    
    <span data-ttu-id="68f9a-168">Obtida usando mais de um servidor em cada camada e colocar todos os servidores de uma camada no mesmo conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="68f9a-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="68f9a-169">Distribuição de carga</span><span class="sxs-lookup"><span data-stu-id="68f9a-169">Load distribution</span></span>
    
    <span data-ttu-id="68f9a-170">Balanceadores de carga Azure interno distribui o tráfego web cliente entrada para os servidores front-end (WEB1 e WEB2) e o endereço IP do ouvinte do cluster do SQL Server (SQL1, SQL2 e MN1).</span><span class="sxs-lookup"><span data-stu-id="68f9a-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="68f9a-171">Segurança</span><span class="sxs-lookup"><span data-stu-id="68f9a-171">Security</span></span>
    
    <span data-ttu-id="68f9a-172">Grupos de segurança de rede para cada sub-rede permitem que você para configurar o tráfego de entrada e saído permitido.</span><span class="sxs-lookup"><span data-stu-id="68f9a-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="68f9a-173">Siga este caminho para a adoção bem-sucedida:</span><span class="sxs-lookup"><span data-stu-id="68f9a-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="68f9a-174">Avaliar e testar</span><span class="sxs-lookup"><span data-stu-id="68f9a-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="68f9a-175">Consulte [2016 do SharePoint Server in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) compreender as vantagens de executar o SharePoint Server 2016 no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="68f9a-175">See [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="68f9a-176">Consulte [Intranet do SharePoint Server 2016 no ambiente de desenvolvimento e teste do Windows Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) para criar um ambiente de desenvolvimento e teste simulados</span><span class="sxs-lookup"><span data-stu-id="68f9a-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="68f9a-177">Design</span><span class="sxs-lookup"><span data-stu-id="68f9a-177">Design</span></span>
    
    <span data-ttu-id="68f9a-178">Consulte [Projetando um farm do SharePoint Server 2016 no Windows Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) para passar por um processo para determinar o conjunto de rede do Azure IaaS, compute e elementos de armazenamento para hospedar seu farm e suas configurações.</span><span class="sxs-lookup"><span data-stu-id="68f9a-178">See [Designing a SharePoint Server 2016 farm in Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="68f9a-179">Implantar</span><span class="sxs-lookup"><span data-stu-id="68f9a-179">Deploy</span></span>
    
    <span data-ttu-id="68f9a-180">Consulte [Implantando o SharePoint Server 2016 com grupos de disponibilidade do SQL Server AlwaysOn no Windows Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) para percorrer a configuração de ponta a ponta do farm de alta disponibilidade em cinco fases.</span><span class="sxs-lookup"><span data-stu-id="68f9a-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="68f9a-181">Identidade federada para o Office 365 no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="68f9a-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="68f9a-182">Outro exemplo de um aplicativo de LOB de várias camado, altamente disponível no Windows Azure é a identidade federada para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="68f9a-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="68f9a-183">**Figura 5: Uma infraestrutura de identidade federada de alta disponibilidade para o Office 365 no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="68f9a-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![A configuração final da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_ADFS.png)
  
<span data-ttu-id="68f9a-p110">Na Figura 5, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão de VPN ou ExpressRoute-to-site. VNet o Azure contém servidores proxy da web, servidores de serviços de Federação do Active Directory (AD FS) e controladores de domínio do Windows Server AD (Active Directory).</span><span class="sxs-lookup"><span data-stu-id="68f9a-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="68f9a-188">Esta configuração tem os seguintes atributos de aplicativos LOB no Windows Azure:</span><span class="sxs-lookup"><span data-stu-id="68f9a-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="68f9a-189">**Camadas:** Há camadas para servidores proxy da web, servidores do AD FS e controladores de domínio do Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="68f9a-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="68f9a-190">**Distribuição de carga:** Um balanceador de carga Azure externo distribui as solicitações de autenticação de cliente recebidas para os proxies de web e um balanceador de carga Azure interno distribui solicitações de autenticação para os servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="68f9a-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="68f9a-191">Siga este caminho para a adoção bem-sucedida:</span><span class="sxs-lookup"><span data-stu-id="68f9a-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="68f9a-192">Avaliar e testar</span><span class="sxs-lookup"><span data-stu-id="68f9a-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="68f9a-193">Consulte a [identidade federada para seu ambiente de desenvolvimento e teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md) para criar um ambiente de desenvolvimento e teste simulado para autenticação federada com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="68f9a-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="68f9a-194">Implantar</span><span class="sxs-lookup"><span data-stu-id="68f9a-194">Deploy</span></span>
    
    <span data-ttu-id="68f9a-195">Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para percorrer a configuração de ponta a ponta da infraestrutura AD FS alta disponibilidade em cinco fases.</span><span class="sxs-lookup"><span data-stu-id="68f9a-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
<span data-ttu-id="68f9a-196">Consulte estes recursos adicionais:</span><span class="sxs-lookup"><span data-stu-id="68f9a-196">See these additional resources:</span></span>
  
- [<span data-ttu-id="68f9a-197">Arquitetura de ambientes híbridos do nuvem</span><span class="sxs-lookup"><span data-stu-id="68f9a-197">Architecting Hybrid Cloud Environments</span></span>](https://gallery.technet.microsoft.com/Architecting-Hybrid-Cloud-a7dc9f24/file/147475/1/Architecting%20Hybrid%20Cloud%20Environments%20V1.docx)
    
- [<span data-ttu-id="68f9a-198">Estender seu Datacenter para o curso de nuvem Microsoft Virtual Academy</span><span class="sxs-lookup"><span data-stu-id="68f9a-198">Extend Your Datacenter to the Cloud Microsoft Virtual Academy course</span></span>](https://mva.microsoft.com/en-US/training-courses/extend-your-datacenter-to-the-cloud-13908?l=7fG3tAouB_7100115881)
    
- [<span data-ttu-id="68f9a-199">Projetar e criar um aplicativo LOB no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="68f9a-199">Design and Build an LOB application in Azure </span></span>](https://techcommunity.microsoft.com/t5/CAAB-Cloud-Adoption-Advisory/EXTRA-November-2016-Webinar/m-p/30058#M41)
    
## <a name="see-also"></a><span data-ttu-id="68f9a-200">Veja também</span><span class="sxs-lookup"><span data-stu-id="68f9a-200">See Also</span></span>

[<span data-ttu-id="68f9a-201">Nuvem híbrida da Microsoft para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="68f9a-201">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="68f9a-202">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="68f9a-202">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="68f9a-203">Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="68f9a-203">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



