---
title: Diagrama acessível-integração de rede de produtos do Microsoft Office Server
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: Este artigo é uma versão de texto acessível do diagrama chamado integração de rede dos produtos do Microsoft Office Server.
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487759"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="467d0-103">Diagrama acessível-integração de rede de produtos do Microsoft Office Server</span><span class="sxs-lookup"><span data-stu-id="467d0-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="467d0-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado integração de rede dos produtos do Microsoft Office Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="467d0-105">Este cartaz fornece uma ilustração geral de um ambiente de rede que inclui o Lync Server 2013, o SharePoint 2013 e o Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="467d0-105">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013.</span></span> <span data-ttu-id="467d0-106">Ele também ilustra os seguintes elementos de rede que são comuns em todos os produtos: acesso remoto e interno, autenticação, tráfego de cliente e tráfego de roteamento por meio de dispositivos compartilhados.</span><span class="sxs-lookup"><span data-stu-id="467d0-106">It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="467d0-107">Conceitos de alto nível para Lync, Exchange, SharePoint Server e Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="467d0-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="467d0-108">Sobre o design</span><span class="sxs-lookup"><span data-stu-id="467d0-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="467d0-109">Design de rede simplificado</span><span class="sxs-lookup"><span data-stu-id="467d0-109">Streamlined network design</span></span>

<span data-ttu-id="467d0-110">Esta topologia ilustra uma implantação de rede local do SharePoint 2013, do Exchange Server 2013 e do Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="467d0-110">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013.</span></span> <span data-ttu-id="467d0-111">Ele também mostra o uso do serviço baseado em nuvem da Microsoft, o Exchange Online Protection, que fornece proteção contra spam e malware para tráfego SMTP de entrada da Internet.</span><span class="sxs-lookup"><span data-stu-id="467d0-111">It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="467d0-112">Esse design de rede é simplificado para um conjunto mínimo de recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="467d0-112">This network design is streamlined to a minimum set of network features.</span></span> <span data-ttu-id="467d0-113">O design não leva em conta os recursos de segurança ou de infraestrutura adicionais que algumas organizações podem exigir.</span><span class="sxs-lookup"><span data-stu-id="467d0-113">The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="467d0-114">Este diagrama:</span><span class="sxs-lookup"><span data-stu-id="467d0-114">This diagram:</span></span> 
  
- <span data-ttu-id="467d0-115">Fornece um exemplo de topologia de rede que ilustra o tráfego de entrada e saída por meio de um roteador de gateway e balanceamento de carga do tráfego de sessão de cliente (externo e interno) para as camadas apropriadas do SharePoint, do Exchange e do Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="467d0-116">Mostra o uso de servidores de acesso remoto opcionais, como um gateway VPN de terceiros ou servidor DirectAccess, para fornecer comunicação segura para funcionários móveis ou remotos.</span><span class="sxs-lookup"><span data-stu-id="467d0-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="467d0-117">Detalha o fluxo de tráfego do SharePoint, do Exchange e do Lync do cliente para cada camada de servidor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="467d0-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="467d0-118">Identifica o tipo de conexão de acesso remoto ou interno com base no cliente (como parceiro ou funcionário) e o método de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="467d0-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="467d0-119">Divide as plataformas do SharePoint, do Exchange e do Lync por funções de servidor necessárias, identificando o front-end, o aplicativo, o banco de dados e outros níveis.</span><span class="sxs-lookup"><span data-stu-id="467d0-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="467d0-120">A arquitetura usada aqui para SharePoint, Lync e Exchange não sugere uma forma preferida de implementar essas plataformas.</span><span class="sxs-lookup"><span data-stu-id="467d0-120">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms.</span></span> <span data-ttu-id="467d0-121">Ele simplesmente fornece um exemplo de topologias diferentes com base em requisitos de rede exclusivos e considerações de segurança.</span><span class="sxs-lookup"><span data-stu-id="467d0-121">It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="467d0-122">Roteador de gateway</span><span class="sxs-lookup"><span data-stu-id="467d0-122">Gateway router</span></span>

<span data-ttu-id="467d0-123">Para essa topologia, o roteador de gateway fica na borda da rede e roteia todo o tráfego de entrada e saída para e da intranet.</span><span class="sxs-lookup"><span data-stu-id="467d0-123">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> <span data-ttu-id="467d0-124">Como alternativa, também pode haver outros componentes que desligam a lacuna entre o roteador de gateway e o balanceador de carga mostrado, como várias camadas de firewalls.</span><span class="sxs-lookup"><span data-stu-id="467d0-124">Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls.</span></span> <span data-ttu-id="467d0-125">Essa topologia representa apenas uma maneira de implantar sua rede de várias.</span><span class="sxs-lookup"><span data-stu-id="467d0-125">This topology represents just one way to deploy your network out of many.</span></span> <span data-ttu-id="467d0-126">Nessa configuração, o gateway é configurado com ACLs (listas de controle de acesso) para permitir tráfego muito específico de entrada e saída baseado em IP nas interfaces do roteador.</span><span class="sxs-lookup"><span data-stu-id="467d0-126">In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces.</span></span> <span data-ttu-id="467d0-127">ACLs, inspeção avançada ou NAT (conversão de endereço de rede) também podem ser realizadas em outros dispositivos, como firewalls, por toda a rede.</span><span class="sxs-lookup"><span data-stu-id="467d0-127">ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="467d0-128">Balanceador de carga e dispositivos de proxy reverso</span><span class="sxs-lookup"><span data-stu-id="467d0-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="467d0-129">Você pode usar soluções de balanceamento de carga de software ou hardware para redirecionar o tráfego de segmentos, incluindo servidores Web front-end do SharePoint e servidores de acesso para cliente do Exchange (CASs).</span><span class="sxs-lookup"><span data-stu-id="467d0-129">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="467d0-130">Em alguns casos, é ideal usar um balanceador de carga baseado em hardware de camada 7 para obter os requisitos de persistência, pois ele pode funcionar melhor usando informações na solicitação, como cookies ou cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="467d0-130">In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers.</span></span> <span data-ttu-id="467d0-131">No enTanto, fatores como custo e maior utilização e carga de trabalho de tal solução podem não ser desejáveis para suas necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="467d0-131">However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs.</span></span> <span data-ttu-id="467d0-132">Considere os seguintes pontos para balanceamento de carga no SharePoint, no Exchange e no Lync:</span><span class="sxs-lookup"><span data-stu-id="467d0-132">Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="467d0-133">SharePoint – para o SharePoint 2013, não é necessário habilitar a afinidade para seus servidores Web front-end.</span><span class="sxs-lookup"><span data-stu-id="467d0-133">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers.</span></span> <span data-ttu-id="467d0-134">Normalmente, isso seria usado para criar sessões adesivas e evitar várias solicitações de autenticação de clientes para cada servidor Web front-end.</span><span class="sxs-lookup"><span data-stu-id="467d0-134">Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server.</span></span> <span data-ttu-id="467d0-135">O novo serviço de cache distribuído no SharePoint 2013 armazena e distribui tokens de logon nos servidores Web do farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="467d0-135">The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="467d0-136">Exchange-no Exchange 2013, a função CAS é projetada para usar o balanceamento de carga de camada 4, distribuindo solicitações na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="467d0-136">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer.</span></span> <span data-ttu-id="467d0-137">Isso pode diminuir significativamente a utilização e a carga de um balanceador de carga.</span><span class="sxs-lookup"><span data-stu-id="467d0-137">This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="467d0-138">Lync-o balanceamento de carga do DNS (sistema de nomes de domínio) é recomendado para o tráfego do protocolo SIP para pools do Lync.</span><span class="sxs-lookup"><span data-stu-id="467d0-138">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools.</span></span> <span data-ttu-id="467d0-139">O balanceamento de carga de hardware (HLB) é necessário para o tráfego do Lync Web (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="467d0-139">Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="467d0-140">Opções de acesso remoto</span><span class="sxs-lookup"><span data-stu-id="467d0-140">Remote access options</span></span>

<span data-ttu-id="467d0-141">Há várias opções que podem publicar recursos de intranet para parceiros na Internet ou fornecer acesso remoto seguro para funcionários remotos ou móveis.</span><span class="sxs-lookup"><span data-stu-id="467d0-141">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees.</span></span> <span data-ttu-id="467d0-142">Esses exemplos incluem proxies reversos, DirectAccess e gateways VPN de terceiros.</span><span class="sxs-lookup"><span data-stu-id="467d0-142">Such examples include reverse proxies, DirectAccess, and third-party VPN gateways.</span></span> <span data-ttu-id="467d0-143">As soluções de acesso remoto discutidas mais adiante nesta seção são possibilidades para o SharePoint, Lync e Exchange, ou qualquer combinação desses servidores em uma implantação local.</span><span class="sxs-lookup"><span data-stu-id="467d0-143">The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment.</span></span> <span data-ttu-id="467d0-144">No enTanto, algumas opções remotas podem não funcionar com uma solução específica.</span><span class="sxs-lookup"><span data-stu-id="467d0-144">However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="467d0-145">Proxy reverso-um proxy reverso oferece suporte à criptografia de tráfego, como SSL (Secure Sockets Layer) e com ele você pode publicar aplicativos de intranet e recursos da Web para usuários e parceiros autenticados na Internet.</span><span class="sxs-lookup"><span data-stu-id="467d0-145">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet.</span></span> <span data-ttu-id="467d0-146">Um exemplo é o Microsoft Forefront Unified Access Gateway (UAG).</span><span class="sxs-lookup"><span data-stu-id="467d0-146">An example is Microsoft Forefront Unified Access Gateway (UAG).</span></span> <span data-ttu-id="467d0-147">Muitos balanceadores de carga de hardware também oferecem suporte à funcionalidade de proxy reverso.</span><span class="sxs-lookup"><span data-stu-id="467d0-147">Many hardware load balancers also support reverse proxy functionality.</span></span> <span data-ttu-id="467d0-148">No enTanto, ainda há cenários válidos para usar uma solução autônoma com base em suas necessidades e requisitos, como isolamento de tráfego, compartimentalização de segurança e otimização de desempenho.</span><span class="sxs-lookup"><span data-stu-id="467d0-148">However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="467d0-149">Considerações e benefícios do proxy reverso:</span><span class="sxs-lookup"><span data-stu-id="467d0-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="467d0-150">Fornece acesso autenticado e protegido para parceiros ou usuários que acessam recursos de intranet (usa SSL (TCP 443) entre o cliente e o servidor de proxy reverso).</span><span class="sxs-lookup"><span data-stu-id="467d0-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="467d0-151">Para o Exchange, um benefício de usar um proxy reverso como o Forefront UAG é a pré-autenticação antes de acessar o servidor de acesso para cliente do Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-151">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server.</span></span> <span data-ttu-id="467d0-152">Os usuários de acesso remoto que usam aplicativos publicados como o Outlook Web Access (OWA) podem autenticar com os métodos Basic, NTLM ou Kerberos antes que eles cheguem à rede interna.</span><span class="sxs-lookup"><span data-stu-id="467d0-152">Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="467d0-153">Para o Exchange e o SharePoint, soluções como o Forefront UAG podem encerrar conexões SSL e diminuir a carga do servidor de recursos de intranet enquanto fornecem um único ponto de gerenciamento para certificados.</span><span class="sxs-lookup"><span data-stu-id="467d0-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="467d0-154">Para o tráfego do Lync, Web (HTTPS) passa pelo proxy reverso (TCP 443) para comunicação de cliente.</span><span class="sxs-lookup"><span data-stu-id="467d0-154">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication.</span></span> <span data-ttu-id="467d0-155">Os proxies de proxy reverso da conexão HTTPS para os serviços Web do Lync, Exchange CAS e Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="467d0-155">The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps.</span></span> <span data-ttu-id="467d0-156">O Lync Server 2013 não dá suporte a UAG.</span><span class="sxs-lookup"><span data-stu-id="467d0-156">Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="467d0-157">DirectAccess-uma tecnologia de acesso remoto que se baseia no protocolo IPsec (Internet Protocol Security) para autenticação e criptografia de tráfego entre o cliente e o servidor do DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="467d0-157">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server.</span></span> <span data-ttu-id="467d0-158">O DirectAccess fornece acesso simultâneo à Internet e recursos de intranet para funcionários móveis e remotos sem ter que iniciar uma conexão.</span><span class="sxs-lookup"><span data-stu-id="467d0-158">DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="467d0-159">Pontos do DirectAccess a considerar:</span><span class="sxs-lookup"><span data-stu-id="467d0-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="467d0-160">O DirectAccess usa o tráfego protegido IPsec (protocolo 50 e 51 e UDP 500) entre o cliente e o servidor do DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="467d0-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="467d0-161">O DirectAccess para Windows Server 2012 e Windows 8 não precisa de uma implantação de infraestrutura de chave pública (PKI) para autenticação de servidor e cliente.</span><span class="sxs-lookup"><span data-stu-id="467d0-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="467d0-162">Recomendamos o uso do DirectAccess com o Lync Server 2013 devido a problemas de latência de áudio e vídeo associados à criptografia e descriptografia IPsec.</span><span class="sxs-lookup"><span data-stu-id="467d0-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="467d0-163">Gateway VPN-gateways VPN típicos fornecem uma conexão de acesso remoto na qual um computador cliente de acesso remoto é projetado logicamente para a intranet por meio de uma conexão encapsulada e iniciada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="467d0-163">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection.</span></span> <span data-ttu-id="467d0-164">Você pode usar o acesso remoto uniFicado no Windows Server 2012 ou várias soluções de terceiros para fornecer acesso seguro à intranet para funcionários móveis ou remotos.</span><span class="sxs-lookup"><span data-stu-id="467d0-164">You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees.</span></span> <span data-ttu-id="467d0-165">A VPN não é recomendada para o Lync.</span><span class="sxs-lookup"><span data-stu-id="467d0-165">VPN is not recommended for Lync.</span></span> <span data-ttu-id="467d0-166">O tráfego do Lync remoto deve usar os servidores de borda e o túnel de divisão.</span><span class="sxs-lookup"><span data-stu-id="467d0-166">Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="467d0-167">Considerações sobre DNS (sistema de nomes de domínio)</span><span class="sxs-lookup"><span data-stu-id="467d0-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="467d0-168">Você precisa planejar o conjunto de registros DNS que permitem que os usuários de Internet e intranet resolvam nomes DNS para os endereços IP apropriados.</span><span class="sxs-lookup"><span data-stu-id="467d0-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="467d0-169">Para parceiros baseados na Internet e para funcionários remotos ou móveis, os registros DNS registrados com servidores DNS da Internet fornecem resolução para o conjunto de endereços IP públicos correspondentes ao roteador de gateway, o servidor de borda do Lync, o conjunto de endereços IP virtuais (VIPs) no o balanceador de carga e o DirectAccess ou o gateway VPN, conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="467d0-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="467d0-170">Para usuários baseados na intranet, os registros DNS registrados em servidores DNS da intranet fornecem resolução para o conjunto de VIPs (endereços IP virtuais) no balanceador de carga para acesso aos recursos do SharePoint, Lync e Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="467d0-171">Os clientes do DirectAccess usam servidores DNS da intranet para nomes que correspondem ao espaço de nome DNS da intranet e servidores DNS da Internet para nomes que não.</span><span class="sxs-lookup"><span data-stu-id="467d0-171">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not.</span></span> <span data-ttu-id="467d0-172">Para simplificar a operação do DirectAccess, considere o uso de uma implementação de DNS dividido que usa namespaces DNS diferentes para nomes baseados na intranet e na Internet.</span><span class="sxs-lookup"><span data-stu-id="467d0-172">To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names.</span></span> <span data-ttu-id="467d0-173">Por exemplo, use contoso.com para namespace da Internet e corp.contoso.com para o namespace da intranet.</span><span class="sxs-lookup"><span data-stu-id="467d0-173">For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="467d0-174">O Exchange usa um modelo de DNS dividido em que a resolução de host para IP difere no tráfego roteado publicamente do na rede corporativa.</span><span class="sxs-lookup"><span data-stu-id="467d0-174">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network.</span></span> <span data-ttu-id="467d0-175">No mínimo, você precisa ter registros DNS para OWA, descoberta automática, URLs do ActiveSync para tráfego do cliente e um registro MX para email de entrada.</span><span class="sxs-lookup"><span data-stu-id="467d0-175">At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="467d0-176">Se você estiver usando o Exchange Online Protection (EOP), seu registro MX apontará para esse serviço em vez do farm do Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="467d0-177">Para o Exchange, você precisa de um registro TXT de verificação de propriedade no seu DNS público e uma ID da organização de Federação para configurar o compartilhamento federado.</span><span class="sxs-lookup"><span data-stu-id="467d0-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="467d0-178">Os clientes VPN de acesso remoto podem ser configurados para usar apenas os servidores DNS da intranet quando a conexão VPN de acesso remoto estiver ativa.</span><span class="sxs-lookup"><span data-stu-id="467d0-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="467d0-179">Descrição do diagrama</span><span class="sxs-lookup"><span data-stu-id="467d0-179">Diagram Description</span></span>

<span data-ttu-id="467d0-180">Este diagrama fornece um exemplo de topologia de rede que ilustra o tráfego de entrada e saída por meio de um roteador de gateway e balanceamento de carga do tráfego de sessão de cliente (externo e interno) para as camadas apropriadas do SharePoint, do Exchange e do Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-180">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> <span data-ttu-id="467d0-181">A descrição deste diagrama é dividida em duas partes:</span><span class="sxs-lookup"><span data-stu-id="467d0-181">The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="467d0-182">Descrição dos componentes mostrados no diagrama</span><span class="sxs-lookup"><span data-stu-id="467d0-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="467d0-183">Descrição de como o tráfego se move pelos componentes para as camadas do servidor do SharePoint, do Exchange, do Lync e do Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="467d0-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="467d0-184">Descrição dos componentes mostrados no diagrama</span><span class="sxs-lookup"><span data-stu-id="467d0-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="467d0-185">Tipos de usuários</span><span class="sxs-lookup"><span data-stu-id="467d0-185">User types</span></span>

<span data-ttu-id="467d0-186">Há quatro tipos diferentes de usuários, três fora dos serviços de rede e nuvem e um interno, que incluem:</span><span class="sxs-lookup"><span data-stu-id="467d0-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="467d0-187">Empresas parceiras (Business-to-Business)-externa</span><span class="sxs-lookup"><span data-stu-id="467d0-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="467d0-188">Parceiros individuais (SharePoint e anônimo (Lync))-externo</span><span class="sxs-lookup"><span data-stu-id="467d0-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="467d0-189">Funcionários remotos e móveis-externos</span><span class="sxs-lookup"><span data-stu-id="467d0-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="467d0-190">Funcionários internos</span><span class="sxs-lookup"><span data-stu-id="467d0-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="467d0-191">Tráfego de email baseado na nuvem</span><span class="sxs-lookup"><span data-stu-id="467d0-191">Cloud-based email traffic</span></span>

<span data-ttu-id="467d0-192">Há um componente baseado em nuvem para tráfego de email baseado em SMTP, hosts de email da Internet ou proteção do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="467d0-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="467d0-193">Autenticação para acesso externo</span><span class="sxs-lookup"><span data-stu-id="467d0-193">Authentication for external access</span></span>

<span data-ttu-id="467d0-194">Há um conjunto específico de procedimentos de autenticação para Lync, SharePoint e Exchange para cada um dos tipos de usuário.</span><span class="sxs-lookup"><span data-stu-id="467d0-194">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types.</span></span> <span data-ttu-id="467d0-195">Eles são descritos mais detalhadamente mais adiante neste documento.</span><span class="sxs-lookup"><span data-stu-id="467d0-195">They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="467d0-196">Roteador de gateway com ACLs</span><span class="sxs-lookup"><span data-stu-id="467d0-196">Gateway router with ACLs</span></span>

<span data-ttu-id="467d0-197">O roteador de gateway fica na borda da rede e roteia todo o tráfego de entrada e saída para e da intranet.</span><span class="sxs-lookup"><span data-stu-id="467d0-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="467d0-198">Servidores de acesso remoto para Lync e SharePoint</span><span class="sxs-lookup"><span data-stu-id="467d0-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="467d0-199">Essa topologia inclui um servidor de borda do Lync e um gateway VPN do SharePoint ou um servidor DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="467d0-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="467d0-200">Balanceador de carga e dispositivo de proxy reverso</span><span class="sxs-lookup"><span data-stu-id="467d0-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="467d0-201">Você pode usar soluções de balanceamento de carga de software ou hardware para redirecionar o tráfego de segmentos, incluindo servidores Web front-end do SharePoint e servidores de acesso para cliente do Exchange (CASs).</span><span class="sxs-lookup"><span data-stu-id="467d0-201">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="467d0-202">Essa topologia mostra os componentes do Lync VIP, do SharePoint VIP e do Exchange VIP no balanceador de carga.</span><span class="sxs-lookup"><span data-stu-id="467d0-202">This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="467d0-203">Servidores</span><span class="sxs-lookup"><span data-stu-id="467d0-203">Servers</span></span>

<span data-ttu-id="467d0-204">Há quatro servidores: Lync, SharePoint, Exchange e Office Web Apps Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-204">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server.</span></span> <span data-ttu-id="467d0-205">Cada servidor pode ter três camadas: um front-end, uma camada de acesso para cliente, uma camada de aplicativo e uma camada de banco de dados/armazenamento.</span><span class="sxs-lookup"><span data-stu-id="467d0-205">Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="467d0-206">Front-end, camada de acesso para cliente</span><span class="sxs-lookup"><span data-stu-id="467d0-206">Front-end, client-access tier</span></span>

<span data-ttu-id="467d0-207">Esta camada tem componentes em todos os quatro servidores:</span><span class="sxs-lookup"><span data-stu-id="467d0-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="467d0-208">Pool do Lync (front-end).</span><span class="sxs-lookup"><span data-stu-id="467d0-208">Lync pool (front end).</span></span> <span data-ttu-id="467d0-209">O diagrama mostra dois bancos de dados do Lync.</span><span class="sxs-lookup"><span data-stu-id="467d0-209">The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="467d0-210">Front-end do SharePoint e cache distribuído.</span><span class="sxs-lookup"><span data-stu-id="467d0-210">SharePoint front end and distributed cache.</span></span> <span data-ttu-id="467d0-211">O diagrama mostra três bancos de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="467d0-211">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="467d0-212">CAS do Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-212">Exchange CAS.</span></span> <span data-ttu-id="467d0-213">O diagrama mostra dois bancos de dados do Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-213">The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="467d0-214">Servidor do Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="467d0-214">Office Web Apps Server.</span></span> <span data-ttu-id="467d0-215">O diagrama mostra dois bancos de dados do Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="467d0-215">The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="467d0-216">Camada de aplicativo</span><span class="sxs-lookup"><span data-stu-id="467d0-216">Application tier</span></span>

<span data-ttu-id="467d0-217">Esta camada tem componentes somente no servidor do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="467d0-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="467d0-218">Pesquisa (consulta, índice, administrador).</span><span class="sxs-lookup"><span data-stu-id="467d0-218">Search (query, index, admin).</span></span> <span data-ttu-id="467d0-219">O diagrama mostra três bancos de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="467d0-219">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="467d0-220">Processamento em lotes.</span><span class="sxs-lookup"><span data-stu-id="467d0-220">Batch processing.</span></span> <span data-ttu-id="467d0-221">O diagrama mostra três bancos de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="467d0-221">The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="467d0-222">Banco de dados/camada de armazenamento</span><span class="sxs-lookup"><span data-stu-id="467d0-222">Database/storage tier</span></span>

<span data-ttu-id="467d0-223">Esta camada tem componentes nos servidores Lync, SharePoint e Exchange:</span><span class="sxs-lookup"><span data-stu-id="467d0-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="467d0-224">Banco de dados do Lync (backend).</span><span class="sxs-lookup"><span data-stu-id="467d0-224">Lync Database (backend).</span></span> <span data-ttu-id="467d0-225">O diagrama mostra três bancos de dados do Lync.</span><span class="sxs-lookup"><span data-stu-id="467d0-225">The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="467d0-226">Banco de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="467d0-226">SharePoint Database.</span></span> <span data-ttu-id="467d0-227">O diagrama mostra três bancos de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="467d0-227">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="467d0-228">Servidor de caixa de correio do Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-228">Exchange Mailbox server.</span></span> <span data-ttu-id="467d0-229">O diagrama mostra dois servidores de caixa de correio do Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-229">The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="467d0-230">Para obter mais informações sobre os componentes instalados em cada uma das funções do SharePoint Server, consulte [topologias otimizadas para o SharePoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="467d0-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="467d0-231">Descrição de como o tráfego se move pelos componentes para diferentes níveis de servidor</span><span class="sxs-lookup"><span data-stu-id="467d0-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="467d0-232">Esta seção descreve como as solicitações de usuário são movidas pela topologia de rede.</span><span class="sxs-lookup"><span data-stu-id="467d0-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="467d0-233">Autenticação e roteamento para acesso externo</span><span class="sxs-lookup"><span data-stu-id="467d0-233">Authentication and routing for external access</span></span>

<span data-ttu-id="467d0-234">Há três tipos diferentes de clientes fora da rede e dos serviços de nuvem, que incluem:</span><span class="sxs-lookup"><span data-stu-id="467d0-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="467d0-235">Empresas parceiras (Business-to-Business)-externa</span><span class="sxs-lookup"><span data-stu-id="467d0-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="467d0-236">Parceiros individuais (SharePoint e anônimo (Lync))-externo</span><span class="sxs-lookup"><span data-stu-id="467d0-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="467d0-237">Funcionários remotos e móveis-externos</span><span class="sxs-lookup"><span data-stu-id="467d0-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="467d0-238">O processo de autenticação e roteamento para cada tipo de usuário externo é descrito individualmente.</span><span class="sxs-lookup"><span data-stu-id="467d0-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="467d0-239">Empresas parceiras (Business-to-Business) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="467d0-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="467d0-240">Lync: confiança de Federação com outras organizações, Skype e conectividade pública de IM (PIC) com AOL.</span><span class="sxs-lookup"><span data-stu-id="467d0-240">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL.</span></span> <span data-ttu-id="467d0-241">O tráfego de Federação do Lync passa pelo roteador de gateway para o servidor de borda do Lync, para o VIP do Lync (balanceador de carga/servidor de proxy reverso) e, em seguida, para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-241">The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="467d0-242">SharePoint: provedor de identidade de parceiro confiável com autenticação SAML.</span><span class="sxs-lookup"><span data-stu-id="467d0-242">SharePoint: Trusted partner identity provider with SAML authentication.</span></span> <span data-ttu-id="467d0-243">O tráfego do cliente do SharePoint passa pelo roteador de gateway para o VIP do SharePoint (balanceador de carga/servidor de proxy reverso) e, em seguida, para o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-243">The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="467d0-244">Exchange: TLS de autenticação mútua para tráfego de email, autenticação SAML para compartilhamento federado.</span><span class="sxs-lookup"><span data-stu-id="467d0-244">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing.</span></span> <span data-ttu-id="467d0-245">O tráfego de cliente do Exchange passa pelo roteador de gateway para o VIP do Exchange (balanceador de carga/servidor de proxy reverso) e, em seguida, para o servidor Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-245">The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="467d0-246">O tráfego SMTP passa pelo roteador de gateway e por meio do VIP do Exchange (balanceador de carga/servidor de proxy reverso) para o Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="467d0-247">Parceiros individuais (SharePoint) e anônimo (Lync) (https://partnerweb.contoso.com ehttps://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="467d0-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="467d0-248">Lync: usuários anônimos podem apenas ingressar em reuniões do Lync organizadas por funcionários.</span><span class="sxs-lookup"><span data-stu-id="467d0-248">Lync: anonymous users can only join Lync meetings organized by employees.</span></span> <span data-ttu-id="467d0-249">O tráfego de Federação do Lync passa pelo roteador de gateway para o servidor de borda do Lync, para o VIP do Lync (balanceador de carga/servidor de proxy reverso) e, em seguida, para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-249">The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="467d0-250">SharePoint: provedor de identidade de parceiro confiável com autenticação SAML ou autenticação baseada em formulários.</span><span class="sxs-lookup"><span data-stu-id="467d0-250">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication.</span></span> <span data-ttu-id="467d0-251">O tráfego do cliente do SharePoint passa pelo roteador de gateway para o VIP do SharePoint (balanceador de carga/servidor de proxy reverso) e, em seguida, para o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-251">The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="467d0-252">Exchange: não se aplica.</span><span class="sxs-lookup"><span data-stu-id="467d0-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="467d0-253">O tráfego da Web do Lync passa pelo roteador de gateway para o servidor de borda do Lync, para o VIP do Lync (balanceador de carga/servidor de proxy reverso) para um balanceador de carga de hardware, que é necessário para o tráfego HTTPS e, em seguida, para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="467d0-254">Funcionários remotos e móveis</span><span class="sxs-lookup"><span data-stu-id="467d0-254">Roaming and remote employees</span></span>

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* <span data-ttu-id="467d0-255">A URL do Exchange tem os seguintes diretórios virtuais: descoberta automática, ECP, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span><span class="sxs-lookup"><span data-stu-id="467d0-255">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="467d0-256">Lync: TLS-DSK ou autenticação NTLM.</span><span class="sxs-lookup"><span data-stu-id="467d0-256">Lync: TLS-DSK or NTLM authentication.</span></span> <span data-ttu-id="467d0-257">O tráfego de cliente do Lync passa pelo roteador de gateway para o servidor de borda do Lync, para o VIP do Lync (balanceador de carga/servidor de proxy reverso) e, em seguida, para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-257">The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="467d0-258">SharePoint: AD DS (serviços de domínio Active Directory), autenticação baseada em formulários ou autenticação SAML.</span><span class="sxs-lookup"><span data-stu-id="467d0-258">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication.</span></span> <span data-ttu-id="467d0-259">O tráfego do cliente do SharePoint passa pelo gateway VPN ou pelo servidor DirectAccess para o VIP do SharePoint (balanceador de carga/servidor de proxy reverso) e, em seguida, para o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-259">The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="467d0-260">Exchange: autenticação básica sobre SSL (ActiveSync, descoberta automática), autenticação baseada em formulários (OWA).</span><span class="sxs-lookup"><span data-stu-id="467d0-260">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA).</span></span> <span data-ttu-id="467d0-261">O tráfego de cliente do Exchange passa pelo roteador de gateway para o VIP do Exchange (balanceador de carga/servidor de proxy reverso) e, em seguida, para o servidor Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-261">The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="467d0-262">O tráfego de cliente do Lync passa pelo roteador de gateway para o servidor VIP do Lync (balanceador de carga/servidor de proxy reverso) para um balanceador de carga de hardware, que é necessário para o tráfego HTTPS e, em seguida, para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-262">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="467d0-263">Autenticação para acesso interno</span><span class="sxs-lookup"><span data-stu-id="467d0-263">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="467d0-264">Funcionários internos</span><span class="sxs-lookup"><span data-stu-id="467d0-264">Internal employees</span></span>

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- <span data-ttu-id="467d0-265">Lync: Kerberos, TLS-DSK ou autenticação NTLM.</span><span class="sxs-lookup"><span data-stu-id="467d0-265">Lync: Kerberos, TLS-DSK, or NTLM authentication.</span></span> <span data-ttu-id="467d0-266">O tráfego de cliente do Lync vai para o servidor VIP do Lync (balanceador de carga/servidor de proxy reverso) e, em seguida, para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-266">The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="467d0-267">SharePoint: AD DS (serviços de domínio Active Directory), autenticação baseada em formulários ou autenticação SAML.</span><span class="sxs-lookup"><span data-stu-id="467d0-267">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication.</span></span> <span data-ttu-id="467d0-268">O tráfego do cliente do SharePoint vai para o VIP do SharePoint (balanceador de carga/servidor de proxy reverso) e, em seguida, para o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-268">The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="467d0-269">Exchange: AD DS, autenticação baseada em formulários.</span><span class="sxs-lookup"><span data-stu-id="467d0-269">Exchange: AD DS, forms-based authentication.</span></span> <span data-ttu-id="467d0-270">O tráfego de cliente do Exchange vai para o VIP do Exchange (servidor de balanceador de carga/servidor de proxy reverso) e, em seguida, para o servidor do Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-270">The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="467d0-271">O tráfego de cliente do Lync vai para o VIP do Lync (balanceador de carga/servidor de proxy reverso) para um balanceador de carga de hardware, que é necessário para o tráfego HTTPS e, em seguida, para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="467d0-271">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="467d0-272">Tráfego de email baseado na nuvem</span><span class="sxs-lookup"><span data-stu-id="467d0-272">Cloud-based email traffic</span></span>

<span data-ttu-id="467d0-273">O componente baseado em nuvem para tráfego de email com base em SMTP consiste em hosts de email da Internet ou proteção do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="467d0-273">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="467d0-274">Esses componentes movem o tráfego de email pela rede usando SMTP.</span><span class="sxs-lookup"><span data-stu-id="467d0-274">These components move email traffic over the network using SMTP.</span></span> <span data-ttu-id="467d0-275">O tráfego passa pelo roteador de gateway para o VIP do Exchange (balanceador de carga/servidor de proxy reverso) e, em seguida, para o servidor do Exchange.</span><span class="sxs-lookup"><span data-stu-id="467d0-275">The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="467d0-276">Legenda de tráfego de rede</span><span class="sxs-lookup"><span data-stu-id="467d0-276">Network traffic legend</span></span>

<span data-ttu-id="467d0-277">A caixa de legenda mostra graficamente os diferentes tipos de tráfego descritos no gráfico em diferentes linhas coloridas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="467d0-277">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="467d0-278">Linha verde: tráfego SIP do Lync</span><span class="sxs-lookup"><span data-stu-id="467d0-278">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="467d0-279">Linha azul: tráfego da Web do Lync</span><span class="sxs-lookup"><span data-stu-id="467d0-279">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="467d0-280">Linha roxa: tráfego de cliente do SharePoint</span><span class="sxs-lookup"><span data-stu-id="467d0-280">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="467d0-281">Linha laranja: tráfego de cliente do Exchange</span><span class="sxs-lookup"><span data-stu-id="467d0-281">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="467d0-282">Linha cinza: tráfego de servidor de email do Exchange entre o Exchange local e o Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="467d0-282">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="467d0-283">Os diferentes tipos de tráfego e as portas que eles usam também são descritos na caixa legenda.</span><span class="sxs-lookup"><span data-stu-id="467d0-283">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="467d0-284">Tráfego SIP do Lync e tráfego da Web do Lync</span><span class="sxs-lookup"><span data-stu-id="467d0-284">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="467d0-285">O servidor de borda do Lync usa as seguintes portas para comunicação externa do usuário:</span><span class="sxs-lookup"><span data-stu-id="467d0-285">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="467d0-286">Tráfego de mensagens INSTANTÂNEAs/sinalização (SIP/simples): porta TCP 443 (aberta para tráfego de entrada)</span><span class="sxs-lookup"><span data-stu-id="467d0-286">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="467d0-287">Tráfego de Webconferência (PSOM): TCP 443 (abrir para tráfego de entrada)</span><span class="sxs-lookup"><span data-stu-id="467d0-287">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="467d0-288">Tráfego A/V (SRTP): TCP 443, UDP 3478 e TCP 50000-59999 (opcional) (abrir para tráfego de entrada e saída)</span><span class="sxs-lookup"><span data-stu-id="467d0-288">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="467d0-289">O Lync Edge Server usa as seguintes portas para comunicação de Federação:</span><span class="sxs-lookup"><span data-stu-id="467d0-289">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="467d0-290">TCP portas 5061 (SIP), 5269 (XMPP), 443 e UDP 3478 (SRTP) (abrir para tráfego de entrada e saída)</span><span class="sxs-lookup"><span data-stu-id="467d0-290">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="467d0-291">Tráfego de cliente do SharePoint</span><span class="sxs-lookup"><span data-stu-id="467d0-291">SharePoint client traffic</span></span>

<span data-ttu-id="467d0-292">O SharePoint pode usar a porta TCP 443 (SSL) para comunicação criptografada entre o cliente e o balanceador de carga.</span><span class="sxs-lookup"><span data-stu-id="467d0-292">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer.</span></span> <span data-ttu-id="467d0-293">Para acesso externo a partir da Internet, esta porta precisa ser aberta para tráfego de entrada e saída no roteador do gateway (ou firewall externo).</span><span class="sxs-lookup"><span data-stu-id="467d0-293">For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="467d0-294">Tráfego de cliente do Exchange e de servidor de email do Exchange</span><span class="sxs-lookup"><span data-stu-id="467d0-294">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="467d0-295">O Exchange usa a porta TCP 25 (SMTP) para comunicações de servidor para servidor.</span><span class="sxs-lookup"><span data-stu-id="467d0-295">Exchange uses TCP port 25 (SMTP) for server-to-server communications.</span></span> <span data-ttu-id="467d0-296">A maior parte do tráfego de cliente (OWA, ActiveSync, autodiscover, Outlook Anywhere) é manipulada pela porta 443 (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="467d0-296">Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS).</span></span> <span data-ttu-id="467d0-297">Se você tiver clientes POP ou IMAP, as portas 110 (POP3), 995 (POP3 criptografado), 143 (IMAP4), 993 (Encrypted IMAP4) e 587 (SMTP) também serão usados para dar suporte a esses clientes.</span><span class="sxs-lookup"><span data-stu-id="467d0-297">If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="467d0-298">Mais sobre o tráfego de rede do Lync?</span><span class="sxs-lookup"><span data-stu-id="467d0-298">More on Lync network traffic?</span></span>

<span data-ttu-id="467d0-299">Saiba como o Lync Server pode ajudar sua organização a fornecer mensagens instantâneas, webconferência, compartilhamento de aplicativos e comunicação de voz.</span><span class="sxs-lookup"><span data-stu-id="467d0-299">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication.</span></span> <span data-ttu-id="467d0-300">Para obter mais informações, consulte [pôster de cargas de trabalho de protocolo do Microsoft Lync Server 2013](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="467d0-300">For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="467d0-301">O cartaz também inclui um código QR para acessar essas informações.</span><span class="sxs-lookup"><span data-stu-id="467d0-301">The poster also includes a QR code to access this information.</span></span> 
  

