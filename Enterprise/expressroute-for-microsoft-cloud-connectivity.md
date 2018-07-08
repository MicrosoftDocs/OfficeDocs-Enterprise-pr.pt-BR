---
title: ExpressRoute para conectividade de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/03/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Resumo: Entenda como ExpressRoute pode ajudá-lo com mais rápidas e confiáveis de conexões para os serviços de nuvem da Microsoft e plataformas.'
ms.openlocfilehash: 55ac09e3c3cf65649d24d67ea79e185808d83cdb
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188109"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="f4ae1-103">ExpressRoute para conectividade de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="f4ae1-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="f4ae1-104">**Resumo:** Compreenda como ExpressRoute pode ajudá-lo com mais rápidas e confiáveis de conexões para os serviços de nuvem da Microsoft e plataformas.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="f4ae1-105">O ExpressRoute oferece uma conexão de rede privada, dedicada e de alta taxa de transferência para a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="f4ae1-106">ExpressRoute para a nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="f4ae1-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="f4ae1-107">Aqui é o caminho de rede para a nuvem da Microsoft sem uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="f4ae1-108">**Figura 1: O caminho de rede sem o ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Figura 1: O caminho de rede sem o ExpressRoute](images/Network_Poster/ExpressRoute.png)
  
<span data-ttu-id="f4ae1-p101">A Figura 1 mostra o caminho típico entre uma rede local e a nuvem da Microsoft. A borda da rede local conecta-se à Internet por meio de uma WAN link para um provedor. O tráfego viaja pela Internet e o limite da nuvem da Microsoft. Ofertas de nuvem em nuvem da Microsoft incluem o Office 365, Microsoft Azure, Microsoft Intune e Dynamics 365. Os usuários de uma organização podem ser localizados na rede local ou na Internet.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="f4ae1-115">Sem uma conexão de ExpressRoute, a única parte do caminho do tráfego para a nuvem da Microsoft que podem controlar (e ter uma relação com o provedor de serviço) é o vínculo entre sua borda da rede local e seu ISP.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="f4ae1-116">O caminho entre seu ISP e a borda de nuvem da Microsoft é um sistema de entrega de melhor esforço na Internet sujeito interrupções, congestionamento de tráfego e monitoramento por usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="f4ae1-117">Os usuários da Internet, como usuários móveis ou remotos, enviam o tráfego para a nuvem da Microsoft pela Internet.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="f4ae1-118">Aqui estão os caminhos de redes para a nuvem da Microsoft com uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="f4ae1-119">**Figura 2: Os caminhos de rede sem o ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Figura 2: Os caminhos de rede sem o ExpressRoute](images/Network_Poster/ExpressRoute_post.png)
  
<span data-ttu-id="f4ae1-p102">A Figura 2 mostra dois caminhos de redes. Tráfego para o Microsoft Intune viaja mesmo caminho de tráfego de Internet normal. Tráfego para o Office 365 e Microsoft Azure Dynamics 365 viaja entre a conexão ExpressRoute, um caminho dedicado entre a borda da rede local e a borda da nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="f4ae1-p103">Com uma conexão ExpressRoute, agora você tem um controle, por meio de uma relação com seu provedor de serviços, no caminho de todo tráfego da sua borda para a Microsoft cloud borda. Essa conexão pode oferecer desempenho previsível e um [tempo de atividade 99,95% SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="f4ae1-p104">Agora, você pode contar com previsível taxa de transferência e latência, com base na conexão do seu provedor de serviços, aos serviços do Office 365, Windows Azure e Dynamics 365. Conexões de ExpressRoute com Microsoft Intune não são suportados no momento.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="f4ae1-128">Tráfego enviado pela conexão a ExpressRoute não são mais está sujeito a Internet interrupções, congestionamento de tráfego e monitoramento.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="f4ae1-p105">Os usuários da Internet, como usuários móveis ou remotos, ainda enviam o tráfego para a nuvem da Microsoft pela Internet. Uma exceção é o tráfego para uma linha de intranet do aplicativo de negócios hospedada no Azure IaaS, que são enviados pela conexão a ExpressRoute por meio de uma conexão de acesso remoto à rede local.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="f4ae1-131">Mesmo com uma conexão ExpressRoute, alguns tráfego ainda é enviado pela Internet, como as consultas DNS, verificação, lista de certificados revogados e solicitações de rede de fornecimento de conteúdo (CDN).</span><span class="sxs-lookup"><span data-stu-id="f4ae1-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="f4ae1-132">Consulte estes recursos adicionais para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="f4ae1-133">Rota Expressa para Office 365</span><span class="sxs-lookup"><span data-stu-id="f4ae1-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="f4ae1-134">ExpressRoute para o Windows Azure</span><span class="sxs-lookup"><span data-stu-id="f4ae1-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="f4ae1-135">Vantagens da ExpressRoute para o Windows Azure</span><span class="sxs-lookup"><span data-stu-id="f4ae1-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="f4ae1-136">Aqui estão algumas vantagens de usar ExpressRoute para serviços de nuvem baseada no Windows Azure:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="f4ae1-p106">**Desempenho previsível:** Com um caminho dedicado até a borda da nuvem da Microsoft, seu desempenho não está sujeito interrupções do provedor de Internet e picos de tráfego da Internet. Você pode determinar e responsabilizar seus provedores a uma taxa de transferência e latência SLA para a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="f4ae1-p107">**Privacidade de dados para seu tráfego:** Tráfego enviado pela sua conexão de ExpressRoute dedicado não está sujeito a captura de pacote ou de monitoramento de Internet e análise por usuários mal-intencionados. É mais seguro usando links de WAN com base em Multiprotocol Label alternando MPLS.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="f4ae1-141">**Conexões de alta taxa de transferência:** Com suporte ampla ExpressRoute conexões por provedores do exchange e provedores de serviços de rede, você pode obter até um link Gbps 10 para a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="f4ae1-142">**Menor custo para algumas configurações:** Embora ExpressRoute conexões sejam um custo adicional, em alguns casos uma conexão de ExpressRoute único pode custo menor do que aumentando sua capacidade de Internet em vários locais da sua organização para fornecer a taxa de transferência adequada aos serviços de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="f4ae1-p108">Uma conexão ExpressRoute não é uma garantia de um melhor desempenho em cada configuração. É possível ter desempenho inferior sobre uma conexão de ExpressRoute pouca largura de banda que uma conexão de Internet de alta largura de banda é apenas alguns saltos para longe de um datacenter regional da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="f4ae1-145">Para obter as recomendações mais recentes para usar ExpressRoute com o Office 365, consulte [ExpressRoute para o Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="f4ae1-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="f4ae1-146">Modelos de conectividade de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="f4ae1-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="f4ae1-147">A tabela 1 mostra os três modelos de conectividade principal para conexões de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="f4ae1-148">**Co localizado em uma troca de nuvem**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="f4ae1-149">**Ethernet de ponto a ponto**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="f4ae1-150">**Para qualquer conexão de (VPN IP)**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![Modelo de conectividade ExpressRoute: Localizado em um Exchange na nuvem](images/Network_Poster/ER_Conn1.png)|![Modelo de conectividade ExpressRoute: Ethernet de ponto a ponto](images/Network_Poster/ER_Conn2.png)|![Modelo de conectividade ExpressRoute: Conexão tipo any-to-any (IP VPN)](images/Network_Poster/ER_Conn3.png)|
|<span data-ttu-id="f4ae1-154">Se seu datacenter co estiver localizado em um recurso com uma troca de nuvem, você pode solicitar uma conexão entre virtual para a nuvem da Microsoft através de intercâmbio de Ethernet do provedor a localização conjunta.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="f4ae1-155">Se seu datacenter estiver localizado em seu local, você pode usar um link de Ethernet de ponto a ponto para conectar-se para a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="f4ae1-156">Se você já estiver usando um provedor de VPN IP (MPLS) para conectar os sites da sua organização, uma conexão ExpressRoute para a nuvem da Microsoft atua como outro local na sua WAN privada.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="f4ae1-157">**Tabela 1: Modelos de conectividade de ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="f4ae1-158">Relacionamentos de correspondência ExpressRoute aos serviços de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="f4ae1-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="f4ae1-p109">Uma conexão de ExpressRoute único oferece suporte a até três Border Gateway Protocol (BGP) aos relacionamentos diferentes para diferentes partes de nuvem da Microsoft. BPG usa relações de correspondência para estabelecer a confiança e trocar informações de roteamento.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p109">A single ExpressRoute connection supports up to three different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="f4ae1-161">**Figura 3: As três diferentes relações BGP em uma única conexão ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-161">**Figure 3: The three different BGP relationships in a single ExpressRoute connection**</span></span>

![Figura 3: As três diferentes relações BGP em uma única conexão ExpressRoute](images/Network_Poster/ERPeering.png)
  
<span data-ttu-id="f4ae1-p110">A Figura 3 mostra uma conexão ExpressRoute de uma rede local. A conexão ExpressRoute contém três relacionamentos lógicos de correspondência. Uma relação de correspondência da Microsoft vai para serviços de SaaS Microsoft, incluindo o Office 365 e Dynamcs CRM Online. Uma relação de correspondência pública vai aos serviços do Azure PaaS. Uma relação de correspondência privada vai para o Windows Azure IaaS e um gateway de rede virtual que hospeda máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection contains three logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365 and Dynamcs CRM Online. A public peering relationship goes to Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="f4ae1-168">O relacionamento BGP aos Microsoft:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-168">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="f4ae1-169">É a partir de um roteador em sua DMZ e os endereços públicos de serviços do Office 365 e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-169">Is from a router in your DMZ to the public addresses of Office 365 and Dynamics 365 services.</span></span> 
    
- <span data-ttu-id="f4ae1-170">Oferece suporte a comunicação iniciada pelo bidirecional.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-170">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="f4ae1-171">O relacionamento BGP correspondência público:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-171">The public peering BGP relationship:</span></span>
  
- <span data-ttu-id="f4ae1-172">É a partir de um roteador em sua DMZ e os endereços IP públicos de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-172">Is from a router in your DMZ to the public IP addresses of Azure services.</span></span>
    
- <span data-ttu-id="f4ae1-p111">Suporta comunicação unidirecional iniciadas dos sistemas locais somente. O relacionamento de correspondência não oferece suporte a comunicação iniciada dos serviços do Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p111">Supports unidirectional-initiated communication from on-premises systems only. The peering relationship does not support communication initiated from Azure PaaS services.</span></span>
    
<span data-ttu-id="f4ae1-175">O relacionamento BGP correspondência privado:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-175">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="f4ae1-176">É de um roteador na borda da rede da organização para os endereços IP privados atribuídos ao seu VNets do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-176">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="f4ae1-177">Oferece suporte a comunicação iniciada pelo bidirecional.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-177">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="f4ae1-178">É uma extensão da rede da organização para a nuvem da Microsoft, completa com endereçamento e roteamento internamente consistente.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-178">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="f4ae1-179">Exemplo de fluxo de tráfego e implantação de aplicativo com ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="f4ae1-179">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="f4ae1-p112">Como o tráfego viaja através de conexões de ExpressRoute e em nuvem da Microsoft é uma função das rotas em de saltos do caminho entre a origem e o comportamento de destino e o aplicativo. Aqui está um exemplo de um aplicativo executado em uma máquina virtual do Azure que acessa um farm do SharePoint no local através de uma conexão de VPN-to-site.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p112">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="f4ae1-182">**Figure 4: Um aplicativo em uma máquina virtual Azure acessando um farm local do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-182">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Figure 4: Um aplicativo em uma máquina virtual Azure acessando um farm local do SharePoint](images/Network_Poster/ER_App_Flow1.png)

  
<span data-ttu-id="f4ae1-184">Mostra a Figura 4 fluxo de um farm do SharePoint local, uma conexão VPN de site a site entre a rede local e uma rede virtual no Azure IaaS, um servidor de aplicativos executando como uma máquina virtual de Azure IaaS e o tráfego entre o servidor de aplicativos e o farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-184">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="f4ae1-185">O aplicativo localiza o endereço IP do farm do SharePoint usando o DNS local e todo o tráfego vai sobre a conexão de VPN-to-site.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-185">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="f4ae1-186">Esta organização migrados seu farm do SharePoint no local para o SharePoint Online no Office 365 e implantado uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-186">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="f4ae1-187">**Figura 5: Movendo o farm local do SharePoint para o SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-187">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Figura 5: Movendo o farm local do SharePoint para o SharePoint Online](images/Network_Poster/Hairpin1.png)
  
<span data-ttu-id="f4ae1-p113">Figura 5 mostra a adição de uma conexão ExpressRoute com relações de correspondência para Microsoft SaaS e o Office 365 e Windows Azure IaaS que contém o servidor de aplicativos em uma rede virtual. O farm do SharePoint local foi migrado para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p113">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="f4ae1-191">Com as relações de correspondência privadas e da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-191">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="f4ae1-192">Do gateway rede virtual do Azure, os locais de local estão disponíveis na conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-192">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="f4ae1-193">De assinatura do Office 365, os endereços IP públicos dispositivos de borda, como servidores proxy, estão disponíveis na conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-193">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="f4ae1-194">Da rede local borda, os endereços IP privados de VNet o Azure e os endereços IP públicos do Office 365 estão disponíveis na conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-194">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="f4ae1-195">Quando o aplicativo acessa as URLs do SharePoint Online, ele encaminha seu tráfego entre a conexão ExpressRoute em um servidor de proxy em da borda.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-195">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="f4ae1-p114">Quando o servidor proxy localiza o endereço IP do SharePoint Online, ele encaminha o tráfego novamente sobre a conexão ExpressRoute. Tráfego de resposta passa o caminho reverso.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p114">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="f4ae1-198">**Figura 6: Fluxo de tráfego quando o farm do SharePoint foi migrado para o SharePoint Online no Office 365**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-198">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Figura 6: Fluxo de tráfego quando o farm do SharePoint foi migrado para o SharePoint Online no Office 365](images/Network_Poster/Hairpin2.png)

  
<span data-ttu-id="f4ae1-200">A Figura 6 mostra como o tráfego entre o servidor de aplicativo e o SharePoint Online no Office 365 sobre a relação de correspondência particular do servidor de aplicativos até a borda da rede local e, em seguida, da borda ao redor a relação de correspondência da Microsoft para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-200">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="f4ae1-201">O resultado é uma forma de fixação, uma consequência do comportamento de roteamento e de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-201">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="f4ae1-202">Rede de nuvem da Microsoft e de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="f4ae1-202">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="f4ae1-203">Conexões ExpressRoute estão disponíveis nas duas versões diferentes: ExpressRoute e ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-203">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="f4ae1-204">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="f4ae1-204">ExpressRoute</span></span>

<span data-ttu-id="f4ae1-205">Como o tráfego viaja entre a rede de organização e o Microsoft Data Center é uma combinação de:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-205">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="f4ae1-206">Seus locais.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-206">Your locations.</span></span>
    
- <span data-ttu-id="f4ae1-207">Microsoft aos locais em nuvem (locais físicos para conectar até a borda da Microsoft).</span><span class="sxs-lookup"><span data-stu-id="f4ae1-207">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="f4ae1-208">Locais de datacenter da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-208">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="f4ae1-209">Datacenter da Microsoft e locais de correspondência de nuvem são conectados à rede de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-209">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="f4ae1-p115">Quando você cria uma conexão ExpressRoute para um local de correspondência de nuvem do Microsoft, você está conectado à rede de nuvem da Microsoft e todos os locais de datacenter Microsoft no mesmo continente. O tráfego entre o local de correspondência da nuvem e o datacenter da Microsoft de destino é realizado através da rede de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p115">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="f4ae1-212">Isso pode resultar em entrega não ideal em centros de dados Microsoft locais para o modelo de conectividade para qualquer.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-212">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="f4ae1-213">**Figura 7: Exemplo de uma organização distribuída geograficamente que usa uma conexão ExpressRoute única**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-213">**Figure 7: Example of an geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Figura 7: Exemplo de uma organização distribuída geograficamente que usa uma conexão ExpressRoute única](images/Network_Poster/MSNet1.png)
  
<span data-ttu-id="f4ae1-p116">Figura 7 mostra uma organização com dois locais, 1 do local em que o Noroeste dos Estados Unidos e local 2 nordeste do Estados Unidos. Eles são conectados por um provedor WAN para qualquer. Esta organização também tem uma conexão ExpressRoute para um local de correspondência da Microsoft na Costa Oeste. Tráfego de local 2 da região nordeste destinado a um datacenter Costa Leste deve viagens por toda WAN a organização da Costa Oeste, para o local de correspondência do Microsoft e, em seguida, volta em todo o país através da rede de nuvem da Microsoft para da Costa Leste Datacenter.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p116">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="f4ae1-219">Para entrega ideal, use várias conexões de ExpressRoute para regionais locais de correspondência nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-219">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="f4ae1-220">**Figura 8: O uso de várias conexões ExpressRoute para entrega ideal para data centers regionais**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-220">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Figura 8: O uso de várias conexões ExpressRoute para entrega ideal para data centers regionais](images/Network_Poster/MSNet2.png)
  
<span data-ttu-id="f4ae1-p117">Figura 8 mostra a mesma organização com duas conexões ExpressRoute, um para cada local, para um local regional Microsoft aos locais. Nesta configuração, o tráfego do local 2 da região nordeste destinado a um datacenter Costa Leste passa diretamente para um local de correspondência da Costa Leste, para a rede de nuvem da Microsoft e, em seguida, para o datacenter Costa Leste.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p117">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="f4ae1-224">Várias conexões de ExpressRoute podem fornecer:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-224">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="f4ae1-225">Melhor desempenho para locais de datacenter Microsoft locais regional.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-225">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="f4ae1-226">Maior disponibilidade para a nuvem da Microsoft quando uma conexão de ExpressRoute local fica indisponível.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-226">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="f4ae1-p118">Isso funciona bem para organizações do mesmo continente. No entanto, o tráfego para centros de dados do Microsoft fora continente da organização viaja pela Internet.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p118">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="f4ae1-229">Para tráfego intercontinentais através da rede de nuvem da Microsoft, você deve usar conexões ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-229">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="f4ae1-230">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="f4ae1-230">ExpressRoute Premium</span></span>

<span data-ttu-id="f4ae1-231">Para organizações que sejam distribuídas globalmente em continentes diferentes, você pode usar ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-231">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="f4ae1-p119">Com o ExpressRoute Premium, você poderá encontrá-qualquer datacenter da Microsoft em qualquer continente de qualquer local de correspondência da Microsoft em qualquer continente. O tráfego entre continentes é realizado através da rede de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p119">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="f4ae1-234">Com várias conexões de ExpressRoute Premium, você pode ter:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-234">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="f4ae1-235">Melhor desempenho em locais continentally centros de dados do Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-235">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="f4ae1-236">Maior disponibilidade para o Microsoft cloud global quando uma conexão de ExpressRoute local fica indisponível.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-236">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="f4ae1-p120">ExpressRoute Premium é necessário para conexões de ExpressRoute baseadas no Office 365. No entanto, não há nenhum custo adicional para empresas com usuários de 500 ou mais licenciados.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p120">ExpressRoute Premium is required for Office 365-based ExpressRoute connections. However, there is no additional cost for enterprises with 500 or more licensed users.</span></span>
  
<span data-ttu-id="f4ae1-239">**Figura 9: Mundial Microsoft cloud network**</span><span class="sxs-lookup"><span data-stu-id="f4ae1-239">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Figura 9: A rede de nuvem da Microsoft em todo o mundo](images/Network_Poster/MSNet3.png)
  
<span data-ttu-id="f4ae1-p121">Figura 9 mostra um diagrama lógico da rede da nuvem Microsoft no mundo todo, com redes que ultrapassam o continentes e regiões do mundo e suas interconexões. Com uma parte da rede de nuvem da Microsoft em cada continente, uma empresa global cria ExpressRoute Premium conexões de seus escritórios regionais hub para local Microsoft aos locais.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p121">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="f4ae1-243">De um escritório regional, apropriadas tráfego do Office 365 para:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-243">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="f4ae1-244">Continental centros de dados do Office 365 são transferidas pela rede Microsoft cloud dentro do continente.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-244">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="f4ae1-245">Centros de dados do Office 365 em outro continente viajam através da rede de nuvem Microsoft intercontinentais.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-245">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="f4ae1-246">Para obter mais informações, confira:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-246">For more information, see:</span></span>
  
- [<span data-ttu-id="f4ae1-247">Azure ExpressRoute treinamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="f4ae1-247">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="f4ae1-248">Planejamento de rede e ajuste de desempenho para o Office 365</span><span class="sxs-lookup"><span data-stu-id="f4ae1-248">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="f4ae1-249">Gerenciamento de desempenho do Office 365</span><span class="sxs-lookup"><span data-stu-id="f4ae1-249">Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="f4ae1-250">Opções de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="f4ae1-250">ExpressRoute options</span></span>

<span data-ttu-id="f4ae1-251">As opções a seguir também podem ser incorporadas em sua implantação ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-251">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="f4ae1-252">**Segurança na sua borda:** Para fornecer segurança avançada para o tráfego enviado e recebido através de conexão de ExpressRoute, como inspeção do tráfego ou detecção de intrusão/malware, coloque seus aparelhos de segurança no caminho do tráfego em sua DMZ ou na borda de sua intranet.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-252">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
    <span data-ttu-id="f4ae1-p122">Tráfego da Internet para máquinas virtuais para impedir que o Azure VMs iniciando tráfego diretamente com locais da Internet, anunciar a rota padrão para a Microsoft. O tráfego para a Internet será roteado entre a conexão ExpressRoute e através de seus servidores de proxy local. Tráfego de máquinas virtuais do Windows Azure para serviços do Azure PaaS ou do Office 365 é encaminhado volta entre a conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p122">Internet traffic for VMs To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="f4ae1-p123">**Otimizadores WAN:** Você pode implantar otimizadores WAN em ambos os lados de uma conexão privada de correspondência para um Azure locais cruzados rede virtual (VNet). Dentro do Azure VNet, use um aparelho de rede WAN otimizador do Azure marketplace e definida pelo usuário de roteamento para rotear o tráfego através do aparelho.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p123">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="f4ae1-p124">**Qualidade de serviço:** Use valores de ponto de código de serviços diferenciados (DSCP) no cabeçalho IPv4 do tráfego para marcá-la para voz, vídeo/interativa ou entrega de melhor esforço. Isso é especialmente importante para a relação de correspondência da Microsoft e Skype para tráfego Business Online.</span><span class="sxs-lookup"><span data-stu-id="f4ae1-p124">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="f4ae1-260">Consulte estes recursos adicionais para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="f4ae1-260">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="f4ae1-261">Rota Expressa para Office 365</span><span class="sxs-lookup"><span data-stu-id="f4ae1-261">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="f4ae1-262">Azure ExpressRoute treinamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="f4ae1-262">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="f4ae1-263">ExpressRoute para o Windows Azure</span><span class="sxs-lookup"><span data-stu-id="f4ae1-263">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="f4ae1-264">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="f4ae1-264">Next step</span></span>

[<span data-ttu-id="f4ae1-265">Projetando a rede para o Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="f4ae1-265">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="f4ae1-266">Confira também</span><span class="sxs-lookup"><span data-stu-id="f4ae1-266">See also</span></span>

[<span data-ttu-id="f4ae1-267">Rede do Microsoft Cloud para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="f4ae1-267">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="f4ae1-268">Recursos de arquitetura de TI do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f4ae1-268">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f4ae1-269">Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="f4ae1-269">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



