---
title: ExpressRoute para conectividade de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/12/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Resumo: entenda como o ExpressRoute pode ajudá-lo com conexões mais rápidas e mais confiáveis para plataformas e serviços em nuvem da Microsoft.'
ms.openlocfilehash: a3b36e98c946bc3ae7281bd38cd4b98820ee8afb
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574005"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="25200-103">ExpressRoute para conectividade de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="25200-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="25200-104">**Resumo:** Entenda como o ExpressRoute pode ajudá-lo com conexões mais rápidas e mais confiáveis para plataformas e serviços em nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="25200-105">O ExpressRoute oferece uma conexão de rede privada, dedicada e de alta taxa de transferência para a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="25200-106">ExpressRoute para a nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="25200-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="25200-107">Este é o caminho de rede para a nuvem da Microsoft sem uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="25200-108">**Figura 1: o caminho de rede sem o ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="25200-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Figura 1: o caminho de rede sem o ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="25200-110">A Figura 1 mostra o caminho típico entre uma rede local e a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-110">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud.</span></span> <span data-ttu-id="25200-111">A borda de rede local conecta-se à Internet por meio de um link de WAN para um provedor.</span><span class="sxs-lookup"><span data-stu-id="25200-111">The on-premises network edge connects to the Internet through a WAN link to an ISP.</span></span> <span data-ttu-id="25200-112">O tráfego passa pela Internet para a borda da Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="25200-112">The traffic then travels across the Internet to the edge of the Microsoft cloud.</span></span> <span data-ttu-id="25200-113">As ofertas de nuvem no Microsoft Cloud incluem o Office 365, o Microsoft Azure, o Microsoft Intune e o Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="25200-113">Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365.</span></span> <span data-ttu-id="25200-114">Os usuários de uma organização podem estar localizados na rede local ou na Internet.</span><span class="sxs-lookup"><span data-stu-id="25200-114">Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="25200-115">Sem uma conexão ExpressRoute, a única parte do caminho de tráfego para a nuvem da Microsoft que você pode controlar (e ter uma relação com o provedor de serviços) é o link entre sua borda de rede local e seu ISP.</span><span class="sxs-lookup"><span data-stu-id="25200-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="25200-116">O caminho entre o seu ISP e o Microsoft Cloud Edge é um sistema de entrega de melhor esforço na Internet sujeito a interrupções, congestionamento de tráfego e monitoramento por usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="25200-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="25200-117">Os usuários na Internet, como usuários móveis ou remotos, enviam o tráfego para a nuvem da Microsoft pela Internet.</span><span class="sxs-lookup"><span data-stu-id="25200-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="25200-118">Estes são os caminhos de rede para a nuvem da Microsoft com uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="25200-119">**Figura 2: caminhos de rede com ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="25200-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Figura 2: caminhos de rede com ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="25200-121">A Figura 2 mostra dois caminhos de rede.</span><span class="sxs-lookup"><span data-stu-id="25200-121">Figure 2 shows two networking paths.</span></span> <span data-ttu-id="25200-122">O tráfego para o Microsoft Intune viaja para o mesmo caminho que o tráfego de Internet normal.</span><span class="sxs-lookup"><span data-stu-id="25200-122">Traffic to Microsoft Intune travels the same path as normal Internet traffic.</span></span> <span data-ttu-id="25200-123">O tráfego para o Office 365, Microsoft Azure e Dynamics 365 passa pela conexão ExpressRoute, um caminho dedicado entre a borda da rede local e a borda da Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="25200-123">Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="25200-124">Com uma conexão ExpressRoute, agora você tem controle, por meio de uma relação com seu provedor de serviços, sobre todo o caminho de tráfego da sua borda para a borda da Microsoft em nuvem.</span><span class="sxs-lookup"><span data-stu-id="25200-124">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge.</span></span> <span data-ttu-id="25200-125">Essa conexão pode oferecer desempenho previsível e um [SLA de tempo de atividade de 99,95%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span><span class="sxs-lookup"><span data-stu-id="25200-125">This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="25200-126">Agora, você pode contar com a taxa de transferência e a latência previsíveis, com base na conexão do provedor de serviços, para os serviços do Office 365, Azure e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="25200-126">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services.</span></span> <span data-ttu-id="25200-127">As conexões ExpressRoute com o Microsoft Intune não são suportadas no momento.</span><span class="sxs-lookup"><span data-stu-id="25200-127">ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="25200-128">O tráfego enviado pela conexão ExpressRoute não está mais sujeito a interrupções de Internet, congestionamento de tráfego e monitoramento.</span><span class="sxs-lookup"><span data-stu-id="25200-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="25200-129">Os usuários na Internet, como usuários móveis ou remotos, ainda enviam o tráfego para a nuvem da Microsoft pela Internet.</span><span class="sxs-lookup"><span data-stu-id="25200-129">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet.</span></span> <span data-ttu-id="25200-130">Uma exceção é o tráfego para um aplicativo de linha de negócios de intranet hospedado no Azure IaaS, que é enviado pela conexão ExpressRoute por meio de uma conexão de acesso remoto à rede local.</span><span class="sxs-lookup"><span data-stu-id="25200-130">One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="25200-131">Mesmo com uma conexão ExpressRoute, algum tráfego ainda é enviado pela Internet, como consultas de DNS, verificação de lista de certificados revogados e solicitações de rede de distribuição de conteúdo (CDN).</span><span class="sxs-lookup"><span data-stu-id="25200-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="25200-132">ConFira estes recursos adicionais para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="25200-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="25200-133">Rota Expressa para Office 365</span><span class="sxs-lookup"><span data-stu-id="25200-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="25200-134">ExpressRoute para Azure</span><span class="sxs-lookup"><span data-stu-id="25200-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="25200-135">Vantagens do ExpressRoute para o Azure</span><span class="sxs-lookup"><span data-stu-id="25200-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="25200-136">Veja algumas vantagens de usar o ExpressRoute para serviços de nuvem baseados no Azure:</span><span class="sxs-lookup"><span data-stu-id="25200-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="25200-137">**Desempenho previsível:** Com um caminho dedicado para a borda da nuvem da Microsoft, seu desempenho não está sujeito às interrupções e aos picos do provedor de Internet no tráfego da Internet.</span><span class="sxs-lookup"><span data-stu-id="25200-137">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic.</span></span> <span data-ttu-id="25200-138">Você pode determinar e manter seus provedores em sua conta em um SLA de taxa de transferência e latência para a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-138">You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="25200-139">**Privacidade dos dados de seu tráfego:** O tráfego enviado por sua conexão expressa dedicada não está sujeito à monitoração da Internet ou captura de pacotes e análise por usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="25200-139">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users.</span></span> <span data-ttu-id="25200-140">É tão seguro quanto usar links WAN baseados em comutação de rótulo de multiProtocolo (MPLS).</span><span class="sxs-lookup"><span data-stu-id="25200-140">It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="25200-141">**Conexões de alto desempenho:** Com amplo suporte para conexões ExpressRoute por provedores do Exchange e provedores de serviços de rede, você pode obter até um link de 10 Gbps para a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="25200-142">**Custo mais baixo para algumas configurações:** Embora as conexões de ExpressRoute sejam um custo adicional, em alguns casos, uma única conexão ExpressRoute pode custar menos do que aumentar sua capacidade de Internet em vários locais de sua organização para fornecer uma taxa de transferência adequada para os serviços de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="25200-143">Uma conexão ExpressRoute não é uma garantia de melhor desempenho em todas as configurações.</span><span class="sxs-lookup"><span data-stu-id="25200-143">An ExpressRoute connection is not a guarantee of higher performance in every configuration.</span></span> <span data-ttu-id="25200-144">É possível ter um desempenho menor em relação a uma conexão ExpressRoute de baixa largura de banda do que uma conexão com a Internet de alta largura de banda que seja apenas alguns saltos de um datacenter regional da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-144">It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="25200-145">Para obter as recomendações mais recentes para usar o ExpressRoute com o Office 365, consulte [ExpressRoute para office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="25200-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="25200-146">Modelos de conectividade ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="25200-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="25200-147">A tabela 1 mostra os três modelos de conectividade principais para conexões ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="25200-148">**Localizado em um Exchange na nuvem**</span><span class="sxs-lookup"><span data-stu-id="25200-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="25200-149">**Ethernet ponto a ponto**</span><span class="sxs-lookup"><span data-stu-id="25200-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="25200-150">**Conexão de qualquer um (IP VPN)**</span><span class="sxs-lookup"><span data-stu-id="25200-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![Modelo de conectividade ExpressRoute: localizado em um Exchange na nuvem](media/Network-Poster/ER-Conn1.png)|![Modelo de conectividade ExpressRoute: Ethernet ponto a ponto](media/Network-Poster/ER-Conn2.png)|![Modelo de conectividade ExpressRoute: conexão de qualquer um (IP VPN)](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="25200-154">Se o seu datacenter estiver localizado em um recurso com uma troca de nuvem, você poderá solicitar uma conexão cruzada virtual para a nuvem da Microsoft por meio do Exchange Ethernet do provedor de colocalização.</span><span class="sxs-lookup"><span data-stu-id="25200-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="25200-155">Se o seu datacenter estiver localizado em seu local, você poderá usar um link Ethernet ponto a ponto para se conectar à nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="25200-156">Se você já estiver usando um provedor de IP VPN (MPLS) para conectar os sites da sua organização, uma conexão ExpressRoute ao Microsoft Cloud funcionará como outro local na sua WAN privada.</span><span class="sxs-lookup"><span data-stu-id="25200-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="25200-157">**Tabela 1: modelos de conectividade do ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="25200-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="25200-158">Relações de emparelhamento de rota para os serviços de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="25200-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="25200-159">Uma única conexão ExpressRoute oferece suporte a até dois relacionamentos de emparelhamento do protocolo BGP (Border Gateway Protocol) diferentes para partes diferentes da nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-159">A single ExpressRoute connection supports up to two different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud.</span></span> <span data-ttu-id="25200-160">O BPG usa relações de emparelhamento para estabelecer informações de roteamento de confiança e Exchange.</span><span class="sxs-lookup"><span data-stu-id="25200-160">BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="25200-161">**Figura 3: as duas relações de BGP diferentes em uma única conexão ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="25200-161">**Figure 3: The two different BGP relationships in a single ExpressRoute connection**</span></span>

![Figura 3: as duas relações de BGP diferentes em uma única conexão ExpressRoute](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="25200-163">A Figura 3 mostra uma conexão ExpressRoute de uma rede local.</span><span class="sxs-lookup"><span data-stu-id="25200-163">Figure 3 shows an ExpressRoute connection from an on-premises network.</span></span> <span data-ttu-id="25200-164">A conexão ExpressRoute tem duas relações lógicas de emparelhamento.</span><span class="sxs-lookup"><span data-stu-id="25200-164">The ExpressRoute connection has two logical peering relationships.</span></span> <span data-ttu-id="25200-165">Uma relação de emparelhamento da Microsoft vai para os serviços Microsoft SaaS, incluindo o Office 365, o Dynamcs 365 e os serviços do Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="25200-165">A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365, Dynamcs 365, and Azure PaaS services.</span></span> <span data-ttu-id="25200-166">Uma relação de emparelhamento privado passa para o Azure IaaS e para um gateway de rede virtual que hospeda máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="25200-166">A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="25200-167">A relação BGP de emparelhamento da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="25200-167">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="25200-168">É de um roteador em sua DMZ para os endereços públicos do Office 365, do Dynamics 365 e dos serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="25200-168">Is from a router in your DMZ to the public addresses of Office 365, Dynamics 365, and Azure services.</span></span> 
    
- <span data-ttu-id="25200-169">Oferece suporte à comunicação iniciada bidirecional.</span><span class="sxs-lookup"><span data-stu-id="25200-169">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="25200-170">A relação BGP de emparelhamento privado:</span><span class="sxs-lookup"><span data-stu-id="25200-170">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="25200-171">É de um roteador na borda da rede da sua organização para os endereços IP privados atribuídos ao seu VNets do Azure.</span><span class="sxs-lookup"><span data-stu-id="25200-171">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="25200-172">Oferece suporte à comunicação iniciada bidirecional.</span><span class="sxs-lookup"><span data-stu-id="25200-172">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="25200-173">É uma extensão da rede da sua organização para a nuvem da Microsoft, completa com endereçamento e roteamento consistentes internamente.</span><span class="sxs-lookup"><span data-stu-id="25200-173">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>

>[!Note]
><span data-ttu-id="25200-174">A relação de BGP de emparelhamento público descrita em versões anteriores deste artigo foi preterida.</span><span class="sxs-lookup"><span data-stu-id="25200-174">The public peering BGP relationship described in previous versions of this article has been deprecated.</span></span>
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="25200-175">Exemplo de implantação de aplicativo e fluxo de tráfego com ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="25200-175">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="25200-176">O modo como o tráfego percorre as conexões ExpressRoute e dentro da nuvem da Microsoft é uma função das rotas nos saltos do caminho entre a origem e o comportamento de aplicativo e de destino.</span><span class="sxs-lookup"><span data-stu-id="25200-176">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior.</span></span> <span data-ttu-id="25200-177">Veja a seguir um exemplo de um aplicativo em execução em uma máquina virtual do Azure que acessa um farm do SharePoint local em uma conexão VPN de site a site.</span><span class="sxs-lookup"><span data-stu-id="25200-177">Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="25200-178">**Figura 4: um aplicativo em uma máquina virtual do Azure que acessa um farm local do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="25200-178">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Figura 4: um aplicativo em uma máquina virtual do Azure que acessa um farm local do SharePoint](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="25200-180">A Figura 4 mostra um farm do SharePoint local, uma conexão VPN de site a site entre a rede local e uma rede virtual no Azure IaaS, um servidor de aplicativos executando como uma máquina virtual do Azure IaaS e o fluxo de tráfego entre o servidor de aplicativos e farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="25200-180">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="25200-181">O aplicativo localiza o endereço IP do farm do SharePoint usando o DNS local e todo o tráfego passa pela conexão VPN site a site.</span><span class="sxs-lookup"><span data-stu-id="25200-181">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="25200-182">Esta organização migrou o farm local do SharePoint para o SharePoint Online no Office 365 e implantou uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-182">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="25200-183">**Figura 5: movendo o farm do SharePoint local para o SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="25200-183">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Figura 5: movendo o farm do SharePoint local para o SharePoint Online](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="25200-185">A Figura 5 mostra a adição de uma conexão ExpressRoute com relações de emparelhamento com o Microsoft SaaS e o Office 365 e para o Azure IaaS contendo o servidor de aplicativos em uma rede virtual.</span><span class="sxs-lookup"><span data-stu-id="25200-185">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network.</span></span> <span data-ttu-id="25200-186">O farm local do SharePoint foi migrado para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="25200-186">The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="25200-187">Com as relações de emparelhamento privado e da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="25200-187">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="25200-188">No gateway de rede virtual do Azure, locais no local estão disponíveis na conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-188">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="25200-189">Na assinatura do Office 365, os endereços IP públicos de dispositivos de borda, como servidores proxy, estão disponíveis na conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-189">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="25200-190">Na borda da rede local, os endereços IP privados da VNet do Azure e os endereços IP públicos do Office 365 estão disponíveis na conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-190">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="25200-191">Quando o aplicativo acessa as URLs do SharePoint Online, ele encaminha seu tráfego pela conexão ExpressRoute para um servidor proxy na borda.</span><span class="sxs-lookup"><span data-stu-id="25200-191">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="25200-192">Quando o servidor proxy localizar o endereço IP do SharePoint Online, ele encaminhará o tráfego de volta pela conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-192">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection.</span></span> <span data-ttu-id="25200-193">O tráfego de resposta Percorra o caminho reverso.</span><span class="sxs-lookup"><span data-stu-id="25200-193">Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="25200-194">**Figura 6: fluxo de tráfego quando o farm do SharePoint foi migrado para o SharePoint Online no Office 365**</span><span class="sxs-lookup"><span data-stu-id="25200-194">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Figura 6: fluxo de tráfego quando o farm do SharePoint foi migrado para o SharePoint Online no Office 365](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="25200-196">A Figura 6 mostra como o tráfego entre o servidor de aplicativos e o SharePoint Online no Office 365 flui sobre a relação de emparelhamento privado do servidor de aplicativos para a borda de rede local e, em seguida, da borda sobre a relação de emparelhamento da Microsoft para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="25200-196">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="25200-197">O resultado é a fixação de cabelo, uma conseqüência do comportamento de roteamento e aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25200-197">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="25200-198">Rota expressa e rede de nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="25200-198">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="25200-199">As conexões ExpressRoute estão disponíveis em duas versões diferentes: ExpressRoute e ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="25200-199">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="25200-200">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="25200-200">ExpressRoute</span></span>

<span data-ttu-id="25200-201">O modo como o tráfego transita entre a rede da sua organização e um datacenter da Microsoft é uma combinação de:</span><span class="sxs-lookup"><span data-stu-id="25200-201">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="25200-202">Seus locais.</span><span class="sxs-lookup"><span data-stu-id="25200-202">Your locations.</span></span>
    
- <span data-ttu-id="25200-203">Locais de emparelhamento de nuvem da Microsoft (os locais físicos para se conectar ao Microsoft Edge).</span><span class="sxs-lookup"><span data-stu-id="25200-203">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="25200-204">Locais de datacenter da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-204">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="25200-205">O Microsoft datacenter e locais de emparelhamento na nuvem estão conectados à rede de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-205">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="25200-206">Ao criar uma conexão ExpressRoute com um local de emparelhamento de nuvem da Microsoft, você está conectado à rede do Microsoft Cloud e a todos os locais de datacenter da Microsoft no mesmo continente.</span><span class="sxs-lookup"><span data-stu-id="25200-206">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent.</span></span> <span data-ttu-id="25200-207">O tráfego entre o local de emparelhamento da nuvem e o datacenter da Microsoft de destino é transportado pela rede da Microsoft em nuvem.</span><span class="sxs-lookup"><span data-stu-id="25200-207">The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="25200-208">Isso pode resultar em uma entrega não ideal para data centers da Microsoft locais para o modelo de conectividade qualquer-para-qualquer.</span><span class="sxs-lookup"><span data-stu-id="25200-208">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="25200-209">**Figura 7: exemplo de uma organização geograficamente distribuída que usa uma única conexão ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="25200-209">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Figura 7: exemplo de uma organização geograficamente distribuída que usa uma única conexão ExpressRoute](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="25200-211">A Figura 7 mostra uma organização com dois locais, local 1 no noroeste dos Estados Unidos e local 2 no nordeste.</span><span class="sxs-lookup"><span data-stu-id="25200-211">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast.</span></span> <span data-ttu-id="25200-212">Eles estão conectados por um provedor de WAN de qualquer um.</span><span class="sxs-lookup"><span data-stu-id="25200-212">They are connected by an any-to-any WAN provider.</span></span> <span data-ttu-id="25200-213">Essa organização também tem uma conexão ExpressRoute com um local de emparelhamento da Microsoft na costa oeste.</span><span class="sxs-lookup"><span data-stu-id="25200-213">This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast.</span></span> <span data-ttu-id="25200-214">O tráfego de local 2 no nordeste destinado a um datacenter de costa leste deve viajar completamente pela WAN da organização para a costa oeste, para o local de emparelhamento da Microsoft e, em seguida, de volta em todo o país da rede de nuvem da Microsoft para a costa leste datacenter.</span><span class="sxs-lookup"><span data-stu-id="25200-214">Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="25200-215">Para a entrega ideal, use várias conexões ExpressRoute para locais regionais de emparelhamento da nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-215">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="25200-216">**Figura 8: o uso de várias conexões ExpressRoute para a entrega ideal para datacenters regionais**</span><span class="sxs-lookup"><span data-stu-id="25200-216">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Figura 8: o uso de várias conexões ExpressRoute para a entrega ideal para datacenters regionais](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="25200-218">A Figura 8 mostra a mesma organização com duas conexões ExpressRoute, uma para cada local, para locais de emparelhamento da Microsoft locais de região.</span><span class="sxs-lookup"><span data-stu-id="25200-218">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations.</span></span> <span data-ttu-id="25200-219">Nessa configuração, o tráfego do local 2 no nordeste destinado a um datacenter de costa leste vai diretamente para um local de emparelhamento da costa leste, para a rede de nuvem da Microsoft e, em seguida, para o datacenter da costa leste.</span><span class="sxs-lookup"><span data-stu-id="25200-219">In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="25200-220">Várias conexões ExpressRoute podem fornecer:</span><span class="sxs-lookup"><span data-stu-id="25200-220">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="25200-221">Melhor desempenho para os locais de datacenters da Microsoft em região local.</span><span class="sxs-lookup"><span data-stu-id="25200-221">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="25200-222">Maior disponibilidade para a nuvem da Microsoft quando uma conexão expressa local fica indisponível.</span><span class="sxs-lookup"><span data-stu-id="25200-222">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="25200-223">Isso funciona bem para organizações no mesmo continente.</span><span class="sxs-lookup"><span data-stu-id="25200-223">This works well for organizations in the same continent.</span></span> <span data-ttu-id="25200-224">No enTanto, o tráfego para os data centers da Microsoft fora do continente da organização passa pela Internet.</span><span class="sxs-lookup"><span data-stu-id="25200-224">However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="25200-225">Para o tráfego Intercontinental na rede do Microsoft Cloud, você deve usar conexões Premium do ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-225">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="25200-226">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="25200-226">ExpressRoute Premium</span></span>

<span data-ttu-id="25200-227">Para organizações distribuídas globalmente entre continentes, você pode usar o ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="25200-227">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="25200-228">Com o ExpressRoute Premium, você pode alcançar qualquer Datacenter da Microsoft em qualquer continente de qualquer local de emparelhamento da Microsoft em qualquer continente.</span><span class="sxs-lookup"><span data-stu-id="25200-228">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent.</span></span> <span data-ttu-id="25200-229">O tráfego entre os continentes é transportado pela rede da Microsoft em nuvem.</span><span class="sxs-lookup"><span data-stu-id="25200-229">The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="25200-230">Com várias conexões Premium do ExpressRoute, você pode ter:</span><span class="sxs-lookup"><span data-stu-id="25200-230">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="25200-231">Melhor desempenho para data centers da Microsoft localmente.</span><span class="sxs-lookup"><span data-stu-id="25200-231">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="25200-232">Maior disponibilidade para a nuvem global da Microsoft quando uma conexão expressa local fica indisponível.</span><span class="sxs-lookup"><span data-stu-id="25200-232">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="25200-233">O ExpressRoute Premium é necessário para conexões ExpressRoute baseadas no Office 365.</span><span class="sxs-lookup"><span data-stu-id="25200-233">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="25200-234">**Figura 9: a rede de nuvem da Microsoft em todo o mundo**</span><span class="sxs-lookup"><span data-stu-id="25200-234">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Figura 9: a rede de nuvem da Microsoft em todo o mundo](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="25200-236">A Figura 9 mostra um diagrama lógico da rede em nuvem da Microsoft em todo o mundo, com redes que abrangem os continentes e regiões do mundo e suas interconexões.</span><span class="sxs-lookup"><span data-stu-id="25200-236">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections.</span></span> <span data-ttu-id="25200-237">Com uma parte da rede de nuvem da Microsoft em cada continente, uma empresa global cria conexões de ExpressRoute Premium a partir de seus escritórios de Hub regionais para locais de emparelhamento da Microsoft locais.</span><span class="sxs-lookup"><span data-stu-id="25200-237">With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="25200-238">Para um escritório regional, o tráfego apropriado do Office 365 para:</span><span class="sxs-lookup"><span data-stu-id="25200-238">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="25200-239">Os datacenters do Office 365 são transferidos pela rede de nuvem da Microsoft dentro do continente.</span><span class="sxs-lookup"><span data-stu-id="25200-239">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="25200-240">Os datacenters do Office 365 em outro continente trafegam pela rede de nuvem do Intercontinental da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-240">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="25200-241">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="25200-241">For more information, see:</span></span>
  
- [<span data-ttu-id="25200-242">Treinamento do Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="25200-242">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="25200-243">Planejamento de rede e ajuste de desempenho para o Office 365</span><span class="sxs-lookup"><span data-stu-id="25200-243">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="expressroute-options"></a><span data-ttu-id="25200-244">Opções do ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="25200-244">ExpressRoute options</span></span>

<span data-ttu-id="25200-245">Você também pode incorporar as seguintes opções à sua implantação do ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="25200-245">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="25200-246">**Segurança na sua borda:** Para fornecer segurança avançada para o tráfego enviado e recebido pela conexão ExpressRoute, como inspeção de tráfego ou detecção de invasão/malware, coloque seus dispositivos de segurança no caminho de tráfego dentro do DMZ ou na borda da sua intranet.</span><span class="sxs-lookup"><span data-stu-id="25200-246">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
- <span data-ttu-id="25200-247">**Tráfego da Internet para VMs:** Para impedir que as VMs do Azure iniciem o tráfego diretamente com locais da Internet, anuncie a rota padrão à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25200-247">**Internet traffic for VMs:** To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft.</span></span> <span data-ttu-id="25200-248">O tráfego para a Internet é roteado pela conexão ExpressRoute e por meio de seus servidores proxy no local.</span><span class="sxs-lookup"><span data-stu-id="25200-248">Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers.</span></span> <span data-ttu-id="25200-249">O tráfego de VMs do Azure para os serviços do Azure PaaS ou Office 365 é roteado de volta pela conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="25200-249">Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="25200-250">**Otimizadores de WAN:** Você pode implantar otimizadores de WAN em ambos os lados de uma conexão de emparelhamento privado para uma rede virtual do Azure entre locais (VNet).</span><span class="sxs-lookup"><span data-stu-id="25200-250">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet).</span></span> <span data-ttu-id="25200-251">Dentro da VNet do Azure, use um dispositivo de rede de otimizador de WAN do Azure Marketplace e o roteamento definido pelo usuário para encaminhar o tráfego pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="25200-251">Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="25200-252">**Qualidade do serviço:** Use valores de ponto de código de serviços diferenciados (DSCP) no cabeçalho IPv4 do seu tráfego para marcá-lo para voz, vídeo/interativo ou entrega de melhor esforço.</span><span class="sxs-lookup"><span data-stu-id="25200-252">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery.</span></span> <span data-ttu-id="25200-253">Isso é especialmente importante para o relacionamento de emparelhamento da Microsoft e o tráfego do Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="25200-253">This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="25200-254">ConFira estes recursos adicionais para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="25200-254">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="25200-255">Rota Expressa para Office 365</span><span class="sxs-lookup"><span data-stu-id="25200-255">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="25200-256">Treinamento do Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="25200-256">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="25200-257">ExpressRoute para Azure</span><span class="sxs-lookup"><span data-stu-id="25200-257">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="25200-258">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="25200-258">Next step</span></span>

[<span data-ttu-id="25200-259">Criação de rede para o Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="25200-259">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="25200-260">Confira também</span><span class="sxs-lookup"><span data-stu-id="25200-260">See also</span></span>

[<span data-ttu-id="25200-261">Rede do Microsoft Cloud para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="25200-261">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="25200-262">Recursos de arquitetura de TI do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="25200-262">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

