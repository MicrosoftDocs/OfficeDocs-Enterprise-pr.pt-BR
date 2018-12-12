---
title: Diagrama acessível - rede integração dos produtos Microsoft Office Server
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
description: Este artigo é uma versão de texto acessível do diagrama denominado rede integração dos produtos Microsoft Office Server.
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504424"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="b4879-103">Diagrama acessível - rede integração dos produtos Microsoft Office Server</span><span class="sxs-lookup"><span data-stu-id="b4879-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="b4879-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama denominado rede integração dos produtos Microsoft Office Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="b4879-p101">Este cartaz fornece uma ilustração geral de um ambiente de rede que inclua o Lync Server 2013, SharePoint 2013 e Exchange Server 2013. Ele também ilustra os seguintes elementos de redes que são comuns entre esses produtos: acesso remoto e interno, autenticação, o tráfego do cliente e rotear o tráfego por meio de dispositivos compartilhados.</span><span class="sxs-lookup"><span data-stu-id="b4879-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="b4879-107">Conceitos de alto nível do Lync, Exchange, SharePoint Server e Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="b4879-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="b4879-108">Sobre o design</span><span class="sxs-lookup"><span data-stu-id="b4879-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="b4879-109">Design de rede simplificadas</span><span class="sxs-lookup"><span data-stu-id="b4879-109">Streamlined network design</span></span>

<span data-ttu-id="b4879-p102">Essa topologia ilustra uma implantação de rede local do SharePoint 2013, Exchange Server 2013 e Lync Server 2013. Ele também mostra o uso do serviço de nuvem do Microsoft, Exchange Online Protection, que oferece proteção contra spam e malware Simple Mail Transfer Protocol (SMTP) para tráfego de entrada da Internet.</span><span class="sxs-lookup"><span data-stu-id="b4879-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="b4879-p103">Esse projeto de rede é simplificado a fim de um conjunto mínimo de recursos de rede. O design não leva em conta infraestrutura ou segurança recursos adicionais que algumas organizações podem exigir.</span><span class="sxs-lookup"><span data-stu-id="b4879-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="b4879-114">Este diagrama:</span><span class="sxs-lookup"><span data-stu-id="b4879-114">This diagram:</span></span> 
  
- <span data-ttu-id="b4879-115">Fornece uma topologia de rede de exemplo que ilustram o tráfego de entrada e saído por meio de um roteador de gateway e o balanceamento de carga de sessão tráfego do cliente (interno e externo) para as camadas de servidor do SharePoint, Exchange e Lync apropriados.</span><span class="sxs-lookup"><span data-stu-id="b4879-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="b4879-116">Mostra o uso de servidores de acesso remoto opcional, um gateway VPN de terceiros ou o servidor DirectAccess, para fornecer comunicações seguras para os funcionários móveis ou remotos.</span><span class="sxs-lookup"><span data-stu-id="b4879-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="b4879-117">Fornece detalhes sobre o SharePoint, Exchange e Lync fluxo de tráfego do cliente para cada camada do servidor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="b4879-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="b4879-118">Identifica o tipo de conexão de acesso remoto ou interno com base no cliente (por exemplo, parceiros ou funcionários) e o método de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="b4879-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="b4879-119">Rompe as plataformas do SharePoint, Exchange e Lync pelas funções de servidor necessárias, que identifica o front-end, aplicativo, banco de dados e outros níveis.</span><span class="sxs-lookup"><span data-stu-id="b4879-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="b4879-p104">A arquitetura aqui usado para o SharePoint, Lync e Exchange não sugere uma maneira preferencial de implementar essas plataformas. Ele fornece um exemplo meramente conforme topologias diferem com base nos requisitos de rede exclusivo e considerações de segurança.</span><span class="sxs-lookup"><span data-stu-id="b4879-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="b4879-122">Roteador de gateway</span><span class="sxs-lookup"><span data-stu-id="b4879-122">Gateway router</span></span>

<span data-ttu-id="b4879-p105">Essa topologia, o roteador de gateway estiver disposta da borda da rede e roteia todo o tráfego de entrada e saído para e da intranet. Como alternativa, também pode haver outros componentes que fechar a lacuna entre o roteador de gateway e o balanceador de carga mostrado, como várias camadas de firewalls. Essa topologia representa apenas uma maneira de implantar sua rede entre vários. Nesta configuração, o gateway é configurado com listas de controle de acesso (ACLs) para permitir muito entrada e saída com base em IP tráfego específico nas interfaces do roteador. ACLs, inspeção avançada ou conversão de endereço de rede (NAT) também pode ser executada em outros dispositivos, como firewalls, em toda a sua rede.</span><span class="sxs-lookup"><span data-stu-id="b4879-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="b4879-128">Dispositivos de proxy reverso e o balanceador de carga</span><span class="sxs-lookup"><span data-stu-id="b4879-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="b4879-p106">Você pode usar soluções de balanceamento de carga de hardware ou software para redirecionar o tráfego para segmentos, incluindo servidores web front-end do SharePoint e servidores de acesso para cliente do Exchange (classes). Em alguns casos, é melhor usar um balanceador de carga baseado no hardware de camada 7 para requisitos de persistência conforme ele pode executar melhor usando informações na solicitação, cookies ou cabeçalhos. No entanto, a fatores como custo e aumento da utilização e carga de trabalho de tal solução não pode ser desejável para suas necessidades específicas. Considere os seguintes pontos balanceamento de carga em SharePoint, Exchange e Lync:</span><span class="sxs-lookup"><span data-stu-id="b4879-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="b4879-p107">SharePoint - para o SharePoint 2013, você não precisará habilitar afinidade para os servidores web front-end. Normalmente, isso seria usado para criar sessões auto-adesivas e evitar a várias solicitações de autenticação de clientes para cada servidor web front-end. O novo serviço de Cache distribuído no SharePoint 2013 armazena e distribui tokens de logon entre os servidores web do farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b4879-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="b4879-p108">Exchange - In Exchange 2013, a função CAS foi projetado para usar o balanceamento de carga de camada 4, distribuir solicitações na camada de transporte. Isso pode diminuir significativamente a utilização do balanceador de carga e a carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b4879-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="b4879-p109">Lync - balanceamento de carga de sistema de nome de domínio (DNS) é recomendada para tráfego de protocolo de iniciação de sessão (SIP) para os pools do Lync. (HLB) de balanceamento de carga de hardware é necessária para o tráfego da Web do Lync (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="b4879-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="b4879-140">Opções de acesso remoto</span><span class="sxs-lookup"><span data-stu-id="b4879-140">Remote access options</span></span>

<span data-ttu-id="b4879-p110">Há várias opções que podem publicar recursos da intranet para parceiros na Internet ou fornecer acesso remoto seguro para funcionários remotos ou móveis. Esses exemplos incluem proxies reversos, DirectAccess e gateways VPN de terceiros. As soluções de acesso remoto discutidas posteriormente nesta seção são possibilidades para SharePoint, Exchange e o Lync, ou qualquer combinação desses servidores em uma implantação no local. No entanto, algumas opções remotas podem não funcionar com uma solução específica.</span><span class="sxs-lookup"><span data-stu-id="b4879-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="b4879-p111">Proxy reverso - um proxy reverso oferece suporte à criptografia de tráfego, como o Secure Sockets Layer (SSL) e com ele, para que você pode publicar aplicativos de intranet e os recursos da web autenticados usuários e parceiros na Internet. Um exemplo é o Microsoft Forefront Unified Access Gateway (UAG). Muitos balanceadores de carga de hardware também suportam a funcionalidade de proxy reverso. No entanto, há ainda válidos cenários para uso de uma solução de autônomo com base em suas necessidades e requisitos, como isolamento de tráfego, compartimentalização de segurança e a otimização do desempenho.</span><span class="sxs-lookup"><span data-stu-id="b4879-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="b4879-149">Benefícios de proxy reverso e considerações:</span><span class="sxs-lookup"><span data-stu-id="b4879-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="b4879-150">Fornece acesso autenticado e protegido para parceiros ou usuários que acessam recursos da intranet (usa SSL (TCP 443) entre o cliente e o servidor proxy reverso).</span><span class="sxs-lookup"><span data-stu-id="b4879-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="b4879-p112">Para o Exchange, uma vantagem do uso de um proxy reverso como o Forefront UAG é pré-autenticação antes de acessar o servidor acesso para cliente do Exchange. Os usuários de acesso remoto que usam aplicativos publicados, como o Outlook Web Access (OWA) pode autenticar com o básico, NTLM ou Kerberos métodos antes que eles cheguem a rede interna.</span><span class="sxs-lookup"><span data-stu-id="b4879-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="b4879-153">Para o Exchange e SharePoint, soluções, como o Forefront UAG podem encerrar conexões SSL e diminuir a carga do servidor de recursos de intranet fornecendo um único ponto de gerenciamento de certificados.</span><span class="sxs-lookup"><span data-stu-id="b4879-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="b4879-p113">Para o Lync, o tráfego de Web (HTTPS) passa pelo proxy reverso (TCP 443) para comunicação do cliente. Os proxies de proxy reverso o HTTPS conexão a serviços Web do Lync, CAS do Exchange e Office Web Apps. Lync Server 2013 não suporta UAG.</span><span class="sxs-lookup"><span data-stu-id="b4879-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="b4879-p114">DirectAccess - uma tecnologia de acesso remoto que depende do protocolo IPSec (IPsec) para autenticação e para criptografar o tráfego entre o cliente DirectAccess e o servidor. DirectAccess fornece acesso simultâneo aos recursos de Internet e intranet para funcionários móveis e remotos, sem precisar iniciar uma conexão.</span><span class="sxs-lookup"><span data-stu-id="b4879-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="b4879-159">DirectAccess pontos a considerar:</span><span class="sxs-lookup"><span data-stu-id="b4879-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="b4879-160">DirectAccess usa tráfego IPsec protegido (protocolo UDP 500 e 50 e 51) entre o cliente DirectAccess e o servidor.</span><span class="sxs-lookup"><span data-stu-id="b4879-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="b4879-161">DirectAccess para o Windows Server 2012 e Windows 8 não precisa de uma implantação da infraestrutura de chave pública (PKI) para autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="b4879-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="b4879-162">Não é recomendável usar o DirectAccess com o Lync Server 2013 devido a problemas de latência de áudio e vídeo associados IPsec criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="b4879-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="b4879-p115">Gateway VPN - gateways VPN típica fornecem uma conexão de acesso remoto no qual um computador cliente de acesso remoto é logicamente projetado intranet através de uma conexão encapsulada e iniciadas pelo usuário. Você pode usar a Unificação de acesso remoto no Windows Server 2012 ou várias soluções de terceiros para fornecer acesso seguro à intranet para funcionários móveis ou remotos. VPN não é recomendado para o Lync. O tráfego remoto do Lync deve usar os servidores de borda e dividida encapsulamento.</span><span class="sxs-lookup"><span data-stu-id="b4879-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="b4879-167">Considerações de nome DNS (sistema) do domínio</span><span class="sxs-lookup"><span data-stu-id="b4879-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="b4879-168">Você precisa planejar para o conjunto de registros DNS que permitem que os usuários de Internet e intranet resolver nomes DNS para os endereços IP apropriados.</span><span class="sxs-lookup"><span data-stu-id="b4879-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="b4879-169">Para parceiros baseado na Internet e os funcionários móveis ou remotos, registros DNS registrados com servidores DNS da Internet fornecem resolução ao conjunto de endereços IP públicos, correspondente para o roteador de gateway, o servidor de borda do Lync, o conjunto de endereços IP virtuais (VIPs) em o balanceador de carga e o gateway DirectAccess ou VPN, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b4879-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="b4879-170">Para usuários baseados na intranet, registros DNS registrados com servidores DNS da intranet fornecem resolução ao conjunto de endereços IP virtuais (VIPs) no balanceador de carga para acessar recursos do SharePoint, Lync e Exchange.</span><span class="sxs-lookup"><span data-stu-id="b4879-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="b4879-p116">Os clientes DirectAccess usam servidores DNS da intranet para nomes correspondente para o espaço para nome DNS da intranet e os servidores DNS da Internet para nomes que não. Para simplificar a operação do DirectAccess, considere o uso de uma implementação de DNS dividido que usa diferentes namespaces DNS para nomes baseado na Internet e intranet. Por exemplo, use contoso.com para o namespace de Internet e corp.contoso.com para o namespace da intranet.</span><span class="sxs-lookup"><span data-stu-id="b4879-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="b4879-p117">O Exchange usa um modelo DNS dividido onde o host de resolução de IP difere no tráfego roteado publicamente do que na rede corporativa. No mínimo, você precisa ter um registro MX para emails de entrada e registros DNS para o OWA, descoberta automática, ActiveSync URLs para o tráfego do cliente.</span><span class="sxs-lookup"><span data-stu-id="b4879-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="b4879-176">Se você estiver usando o Exchange Online Protection (EOP), o seu registro MX aponta para esse serviço em vez de seu farm do Exchange.</span><span class="sxs-lookup"><span data-stu-id="b4879-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="b4879-177">Para o Exchange, você precisa de uma prova de propriedade registro TXT em seu DNS público e uma ID da organização de federação para configurar o compartilhamento federado.</span><span class="sxs-lookup"><span data-stu-id="b4879-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="b4879-178">Clientes de VPN de acesso remoto podem ser configurados para usar apenas os servidores DNS da intranet quando a conexão VPN de acesso remoto está ativo.</span><span class="sxs-lookup"><span data-stu-id="b4879-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="b4879-179">Descrição do diagrama</span><span class="sxs-lookup"><span data-stu-id="b4879-179">Diagram Description</span></span>

<span data-ttu-id="b4879-p118">Este diagrama fornece uma topologia de rede de exemplo que ilustram o tráfego de entrada e saído por meio de um roteador de gateway e o balanceamento de carga de sessão tráfego do cliente (interno e externo) para as camadas de servidor do SharePoint, Exchange e Lync apropriados. A descrição deste diagrama é dividida em duas partes:</span><span class="sxs-lookup"><span data-stu-id="b4879-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="b4879-182">Descrição dos componentes mostrados no diagrama</span><span class="sxs-lookup"><span data-stu-id="b4879-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="b4879-183">Descrição de como o tráfego é movido por todos os componentes para as camadas de servidor do SharePoint, Exchange, Lync e Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="b4879-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="b4879-184">Descrição dos componentes mostrados no diagrama</span><span class="sxs-lookup"><span data-stu-id="b4879-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="b4879-185">Tipos de usuário</span><span class="sxs-lookup"><span data-stu-id="b4879-185">User types</span></span>

<span data-ttu-id="b4879-186">Há quatro tipos diferentes de usuários, três fora os serviços de rede e em nuvem e outro interna, que incluem:</span><span class="sxs-lookup"><span data-stu-id="b4879-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="b4879-187">Empresas parceiras (business-to-business)-externo</span><span class="sxs-lookup"><span data-stu-id="b4879-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="b4879-188">Parceiros individuais (SharePoint e anônimo (Lync))-externo</span><span class="sxs-lookup"><span data-stu-id="b4879-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="b4879-189">Externo funcionários móvel e remoto</span><span class="sxs-lookup"><span data-stu-id="b4879-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="b4879-190">Funcionários internos</span><span class="sxs-lookup"><span data-stu-id="b4879-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="b4879-191">Tráfego de email baseada em nuvem</span><span class="sxs-lookup"><span data-stu-id="b4879-191">Cloud-based email traffic</span></span>

<span data-ttu-id="b4879-192">Não há um componente baseado em nuvem para o tráfego de email baseados em SMTP, Hosts de email da Internet ou Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="b4879-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="b4879-193">Autenticação para acesso externo</span><span class="sxs-lookup"><span data-stu-id="b4879-193">Authentication for external access</span></span>

<span data-ttu-id="b4879-p119">Há um conjunto específico de procedimentos de autenticação para o Lync, SharePoint e Exchange para cada um dos tipos de usuário. Eles são descritos em mais detalhes posteriormente neste documento.</span><span class="sxs-lookup"><span data-stu-id="b4879-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="b4879-196">Roteador de gateway com ACLs</span><span class="sxs-lookup"><span data-stu-id="b4879-196">Gateway router with ACLs</span></span>

<span data-ttu-id="b4879-197">O roteador de gateway fica na borda da rede e encaminha o todo o tráfego de entrada e saído para e da intranet.</span><span class="sxs-lookup"><span data-stu-id="b4879-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="b4879-198">Servidores de acesso remoto do Lync e SharePoint</span><span class="sxs-lookup"><span data-stu-id="b4879-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="b4879-199">Essa topologia inclui um servidor de borda do Lync e um gateway de SharePoint VPN ou servidor DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="b4879-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="b4879-200">Balanceador de carga e o dispositivo de proxy reverso</span><span class="sxs-lookup"><span data-stu-id="b4879-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="b4879-p120">Você pode usar soluções de balanceamento de carga de hardware ou software para redirecionar o tráfego para segmentos, incluindo servidores web front-end do SharePoint e servidores de acesso para cliente do Exchange (classes). Essa topologia mostra componentes Lync VIP, VIP do SharePoint e Exchange VIP no balanceador de carga.</span><span class="sxs-lookup"><span data-stu-id="b4879-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="b4879-203">Servidores</span><span class="sxs-lookup"><span data-stu-id="b4879-203">Servers</span></span>

<span data-ttu-id="b4879-p121">Há quatro servidores: Office Web Apps Server, SharePoint, Exchange e Lync. Cada servidor pode ter três camadas: um front-end, o nível de acesso para cliente, uma camada de aplicativo e uma camada de armazenamento/banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b4879-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="b4879-206">Front-end, camada de acesso para cliente</span><span class="sxs-lookup"><span data-stu-id="b4879-206">Front-end, client-access tier</span></span>

<span data-ttu-id="b4879-207">Essa camada tem componentes em todos os quatro servidores:</span><span class="sxs-lookup"><span data-stu-id="b4879-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="b4879-p122">Pool do Lync (front-end). O diagrama mostra os dois bancos de dados do Lync.</span><span class="sxs-lookup"><span data-stu-id="b4879-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="b4879-p123">Front-end do SharePoint e o cache distribuído. O diagrama mostra três bancos de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b4879-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="b4879-p124">CAS do Exchange. O diagrama mostra os dois bancos de dados do Exchange.</span><span class="sxs-lookup"><span data-stu-id="b4879-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="b4879-p125">Office Web Apps Server. O diagrama mostra os dois bancos de dados do Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="b4879-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="b4879-216">Camada de aplicativo</span><span class="sxs-lookup"><span data-stu-id="b4879-216">Application tier</span></span>

<span data-ttu-id="b4879-217">Essa camada tem componentes somente no servidor do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="b4879-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="b4879-p126">Pesquisa (consulta, index, admin). O diagrama mostra três bancos de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b4879-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="b4879-p127">Processamento em lotes. O diagrama mostra três bancos de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b4879-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="b4879-222">Camada de armazenamento/banco de dados</span><span class="sxs-lookup"><span data-stu-id="b4879-222">Database/storage tier</span></span>

<span data-ttu-id="b4879-223">Essa camada tem componentes nos servidores do SharePoint, Lync e Exchange:</span><span class="sxs-lookup"><span data-stu-id="b4879-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="b4879-p128">Banco de dados do Lync (back-end). O diagrama mostra três bancos de dados do Lync.</span><span class="sxs-lookup"><span data-stu-id="b4879-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="b4879-p129">Banco de dados do SharePoint. O diagrama mostra três bancos de dados do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b4879-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="b4879-p130">Servidor de caixa de correio do Exchange. O diagrama mostra dois servidores de caixa de correio do Exchange.</span><span class="sxs-lookup"><span data-stu-id="b4879-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="b4879-230">Para obter mais informações sobre componentes instalados em cada uma das funções de servidor do SharePoint, consulte [Topologias otimizadas do SharePoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="b4879-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="b4879-231">Descrição de como o tráfego é movido por todos os componentes para as camadas de servidor diferente</span><span class="sxs-lookup"><span data-stu-id="b4879-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="b4879-232">Esta seção descreve como as solicitações de usuário para percorrer a topologia de rede.</span><span class="sxs-lookup"><span data-stu-id="b4879-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="b4879-233">Autenticação e o roteamento para acesso externo</span><span class="sxs-lookup"><span data-stu-id="b4879-233">Authentication and routing for external access</span></span>

<span data-ttu-id="b4879-234">Há três tipos diferentes de clientes fora do serviços de rede e em nuvem, que incluem:</span><span class="sxs-lookup"><span data-stu-id="b4879-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="b4879-235">Empresas parceiras (business-to-business)-externo</span><span class="sxs-lookup"><span data-stu-id="b4879-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="b4879-236">Parceiros individuais (SharePoint e anônimo (Lync))-externo</span><span class="sxs-lookup"><span data-stu-id="b4879-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="b4879-237">Externo funcionários móvel e remoto</span><span class="sxs-lookup"><span data-stu-id="b4879-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="b4879-238">A autenticação e o processo de roteamento para cada tipo de usuário externo é descrito individualmente.</span><span class="sxs-lookup"><span data-stu-id="b4879-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="b4879-239">Empresas parceiras (business-to-business) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="b4879-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="b4879-p131">Lync: a confiança de federação com outras organizações, Skype e conectividade de IM pública (PIC) com o AOL. O tráfego de Federação do Lync passa pelo roteador gateway para o servidor de borda do Lync, como o VIP do Lync (servidor de proxy / reverso do balanceador de carga) e, em seguida, o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="b4879-p132">SharePoint: Confiáveis provedor de identidade de parceiro com autenticação SAML. O tráfego de cliente do SharePoint passa pelo roteador Gateway para o VIP do SharePoint (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="b4879-p133">Exchange: TLS Auth mútuo para tráfego de email, a autenticação SAML para Federated Sharing. O tráfego do cliente Exchange passa pelo roteador Gateway para o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) e depois para o Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="b4879-246">O tráfego de SMTP passa por meio do roteador de Gateway e o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) para o Exchange server.</span><span class="sxs-lookup"><span data-stu-id="b4879-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="b4879-247">Parceiros individuais (SharePoint) e anônimo (Lync) (https://partnerweb.contoso.com e https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="b4879-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="b4879-p134">Lync: usuários anônimos só podem ingressar em reuniões do Lync organizados pelos funcionários. O tráfego de Federação do Lync passa pelo roteador Gateway para o servidor de borda do Lync, como o VIP do Lync (servidor de proxy / reverso do balanceador de carga) e, em seguida, o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="b4879-p135">Do SharePoint: Provedor de identidade parceiro confiável com autenticação SAML ou a autenticação baseada em formulários. O tráfego de cliente do SharePoint passa pelo roteador Gateway para o VIP do SharePoint (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="b4879-252">Exchange: Não se aplica.</span><span class="sxs-lookup"><span data-stu-id="b4879-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="b4879-253">Tráfego da Web do Lync passa pelo roteador Gateway para o servidor de borda do Lync, como o VIP do Lync (servidor de proxy / reverso do balanceador de carga,) para um balanceador de carga de hardware, que é necessário para tráfego HTTPS, e depois para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="b4879-254">Funcionários móveis e remotos</span><span class="sxs-lookup"><span data-stu-id="b4879-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="b4879-255">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="b4879-256">https://Teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="b4879-257">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="b4879-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="b4879-259">https://mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="b4879-259">https://mail.contoso.com\*</span></span> 
    
6. <span data-ttu-id="b4879-260">https://dial.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="b4879-260">https://dial.contoso.com\*</span></span>
    
7. <span data-ttu-id="b4879-261">https://meet.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="b4879-261">https://meet.contoso.com\*</span></span>
    
* <span data-ttu-id="b4879-262">A URL do Exchange tem os seguintes diretórios virtuais: descoberta automática, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4879-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="b4879-p136">Lync: Autenticação TLS-DSK ou NTLM. O tráfego do cliente Lync passa pelo roteador Gateway para o servidor de borda do Lync, como o VIP do Lync (servidor de proxy / reverso do balanceador de carga) e, em seguida, o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="b4879-p137">SharePoint: Os serviços de domínio Active Directory (AD DS), a autenticação baseada em formulários ou autenticação SAML. O tráfego de cliente do SharePoint passa pelo gateway VPN ou o servidor DirectAccess para o VIP do SharePoint (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o SharePoint server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="b4879-p138">Exchange: A autenticação básica sobre SSL (ActiveSync, descoberta automática), a autenticação baseada em formulários (OWA). O tráfego do cliente Exchange passa pelo roteador Gateway para o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) e depois para o Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="b4879-269">O tráfego de cliente do Lync passa pelo roteador Gateway para o VIP Lync (servidor de proxy / reverso do balanceador de carga) para um balanceador de carga de hardware, que é necessário para tráfego HTTPS, e depois para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="b4879-270">Autenticação para acesso interno</span><span class="sxs-lookup"><span data-stu-id="b4879-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="b4879-271">Funcionários internos</span><span class="sxs-lookup"><span data-stu-id="b4879-271">Internal employees</span></span>

> <span data-ttu-id="b4879-272">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="b4879-273">https://Teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="b4879-274">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="b4879-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="b4879-276">https://mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="b4879-276">https://mail.contoso.com\*</span></span> 
    
> <span data-ttu-id="b4879-277">https://dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="b4879-278">https://meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="b4879-279">https://Admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b4879-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="b4879-p139">Lync: Autenticação Kerberos, NTLM ou DSK de TLS. O tráfego do cliente Lync vai para o VIP do Lync (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="b4879-p140">SharePoint: Os serviços de domínio Active Directory (AD DS), a autenticação baseada em formulários ou autenticação SAML. O tráfego de cliente do SharePoint vai para o VIP do SharePoint (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="b4879-p141">Exchange: AD DS, a autenticação baseada em formulários. O tráfego do cliente Exchange vai para o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) e depois para o Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="b4879-286">O tráfego de cliente do Lync vai para o VIP do Lync (servidor de proxy / reverso do balanceador de carga) para um balanceador de carga de hardware, que é necessário para tráfego HTTPS, e depois para o Lync Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="b4879-287">Tráfego de email baseada em nuvem</span><span class="sxs-lookup"><span data-stu-id="b4879-287">Cloud-based email traffic</span></span>

<span data-ttu-id="b4879-288">O componente baseado em nuvem para o tráfego de email baseados em SMTP consiste em Hosts de email da Internet ou Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="b4879-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="b4879-p142">Esses componentes movem o tráfego de email através da rede usando o SMTP. O tráfego passa pelo roteador Gateway para o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) e depois para o Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="b4879-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="b4879-291">Legenda de tráfego de rede</span><span class="sxs-lookup"><span data-stu-id="b4879-291">Network traffic legend</span></span>

<span data-ttu-id="b4879-292">Na caixa legenda graficamente mostra os diferentes tipos de tráfego ilustrado no gráfico nas linhas coloridos diferentes da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b4879-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="b4879-293">Verde linha: Lync SIP tráfego</span><span class="sxs-lookup"><span data-stu-id="b4879-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="b4879-294">Azul linha: tráfego da Web do Lync</span><span class="sxs-lookup"><span data-stu-id="b4879-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="b4879-295">Roxo linha: o tráfego de cliente do SharePoint</span><span class="sxs-lookup"><span data-stu-id="b4879-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="b4879-296">Linha laranja: tráfego do cliente do Exchange</span><span class="sxs-lookup"><span data-stu-id="b4879-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="b4879-297">Linha de cinza: tráfego do servidor de email do Exchange entre o Exchange local e o Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="b4879-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="b4879-298">Os diferentes tipos de tráfego e as portas que eles usam também são descritos na caixa legenda.</span><span class="sxs-lookup"><span data-stu-id="b4879-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="b4879-299">Tráfego SIP do Lync e o tráfego de web do Lync</span><span class="sxs-lookup"><span data-stu-id="b4879-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="b4879-300">O servidor de borda do Lync usa as seguintes portas para comunicação de usuário externo:</span><span class="sxs-lookup"><span data-stu-id="b4879-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="b4879-301">Tráfego de sinalização/IM (SIP/simples): porta TCP 443 (abertas para tráfego de entrada)</span><span class="sxs-lookup"><span data-stu-id="b4879-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="b4879-302">Tráfego de webconferência (PSOM) da Web: TCP 443 (aberta para o tráfego de entrada)</span><span class="sxs-lookup"><span data-stu-id="b4879-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="b4879-303">A / V (SRTP) do tráfego: TCP 443, UDP 3478 e TCP 50000-59999 (opcional) (aberta para o tráfego de entrada e saída)</span><span class="sxs-lookup"><span data-stu-id="b4879-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="b4879-304">Servidor de borda do Lync usa as seguintes portas para comunicação de Federação:</span><span class="sxs-lookup"><span data-stu-id="b4879-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="b4879-305">Portas TCP 5061 (SIP), 5269 (XMPP), 443 e UDP 3478 (SRTP) (aberta para o tráfego de entrada e saída)</span><span class="sxs-lookup"><span data-stu-id="b4879-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="b4879-306">Tráfego de cliente do SharePoint</span><span class="sxs-lookup"><span data-stu-id="b4879-306">SharePoint client traffic</span></span>

<span data-ttu-id="b4879-p143">SharePoint pode usar a porta TCP 443 (SSL) para comunicação criptografada entre o cliente e o balanceador de carga. Para obter acesso externo da Internet, essa porta precisa ser aberto para o tráfego de entrada e saído no roteador de gateway (ou firewall externo).</span><span class="sxs-lookup"><span data-stu-id="b4879-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="b4879-309">Tráfego de cliente do Exchange e o tráfego do servidor de email do Exchange</span><span class="sxs-lookup"><span data-stu-id="b4879-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="b4879-p144">Para comunicações de servidor-para-servidor, o Exchange usa a porta TCP 25 (SMTP). A maioria dos tráfego de cliente (OWA, ActiveSync, descoberta automática, Outlook Anywhere) é tratado na porta 443 (HTTPS). Se você tiver clientes POP ou IMAP, portas 110 (POP3), 995 (criptografadas POP3), 143 (IMAP4), 993 (criptografadas IMAP4) e 587 (SMTP) também são usadas para oferecer suporte a esses clientes.</span><span class="sxs-lookup"><span data-stu-id="b4879-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="b4879-313">Mais tráfego diante de rede do Lync?</span><span class="sxs-lookup"><span data-stu-id="b4879-313">More on Lync network traffic?</span></span>

<span data-ttu-id="b4879-p145">Saiba como o Lync Server pode ajudar sua organização a fornecer mensagens instantâneas, Webconferência, compartilhamento de aplicativos e comunicação por voz. Para obter mais informações, consulte o [Cartaz de cargas de trabalho de protocolo do Microsoft Lync Server 2013](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="b4879-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="b4879-316">O cartaz também inclui um código QR para acessar essa informação.</span><span class="sxs-lookup"><span data-stu-id="b4879-316">The poster also includes a QR code to access this information.</span></span> 
  

