---
title: Conectividade de cliente
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Resumo: Explica como os computadores clientes se conectam a locatários do Office 365, dependendo da localização do computador cliente e do datacenter do locatário do Office 365.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223033"
---
# <a name="client-connectivity"></a><span data-ttu-id="34a43-103">Conectividade de cliente</span><span class="sxs-lookup"><span data-stu-id="34a43-103">Client connectivity</span></span>

 <span data-ttu-id="34a43-104">**Resumo:** Explica como os computadores clientes se conectam a locatários do Office 365, dependendo da localização do computador cliente e do datacenter do locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="34a43-p101">O Office 365 reside em datacenters da Microsoft em todo o mundo que ajudam a manter o serviço de backup e executando o mesmo quando há um grande problema em uma região, como um terremoto ou uma interrupção de energia. Quando você se conectar ao seu locatário do Office 365, a conexão do cliente será direcionado para o datacenter apropriado onde seu locatário está sendo hospedado. As regras que determinam onde seu locatário pode ser hospedado são definidas por seu contrato com a Microsoft. As regras que determinam como seu cliente adquire os dados a partir desta localização de datacenter dependem a arquitetura do serviço que você está usando.</span><span class="sxs-lookup"><span data-stu-id="34a43-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="34a43-p102">Por exemplo, quando você fizer logon no portal do Office 365, você está geralmente conectado com o datacenter mais próximo ao cliente e direcionado dependendo do serviço que você use Avançar. Se você abrir o email, a conexão inicial para exibir a interface do usuário pode ainda ser provenientes do datacenter mais próximo, mas uma segunda conexão pode ser aberto entre o datacenter mais próximo e o datacenter onde seu locatário está localizado para mostrar que você está em emails ler. Microsoft opera uma das dez redes principais do mundo, resultando em um datacenter para datacenter extremamente fast conexões rápidas.</span><span class="sxs-lookup"><span data-stu-id="34a43-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="34a43-112">Após ler o artigo, você provavelmente compreenderá por que não fornecemos [intervalos de endereços IP e URLs do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) por datacenter, eles são simplesmente muito interconexão e dependentes de uns aos outros fazer com que viável.</span><span class="sxs-lookup"><span data-stu-id="34a43-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="34a43-p103">Se você estiver usando o Windows Azure ExpressRoute para o Office 365, na maioria dos casos seu conectividade irão sobre uma conexão privada para Office 365 em vez da conexão pública descrito aqui. Os princípios sobre como os clientes se conectam ainda estão exatos. Saiba mais sobre [ExpressRoute do Windows Azure para o Office 365](azure-expressroute.md).</span><span class="sxs-lookup"><span data-stu-id="34a43-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="34a43-116">Para mais detalhes no Skype para solicitações de rede de negócios, leia o artigo de [qualidade de mídia e o desempenho da conectividade de rede em Skype para negócios Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span><span class="sxs-lookup"><span data-stu-id="34a43-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="34a43-117">Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="34a43-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="34a43-p104">Podemos tomar muito cuidado para gerenciar dados de cliente, por isso é seguro e privadas em nossos centros de dados. Detalhes sobre as etapas tomada para gerenciar a privacidade estão incluídos na [Central de confiabilidade](https://go.microsoft.com/fwlink/?LinkID=397383).</span><span class="sxs-lookup"><span data-stu-id="34a43-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="34a43-120">Conexão com o datacenter mais próximo</span><span class="sxs-lookup"><span data-stu-id="34a43-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="34a43-p105">Este é o tipo de conexão mais comum, e é usado pelo portal do Office 365 e Exchange Online. Nessa situação, quando os clientes tentam se conectar ao Office 365, consulta DNS do seu computador determina as regiões do mundo que vem de seu computador e Office 365 redireciona a solicitação para o datacenter mais próximo.</span><span class="sxs-lookup"><span data-stu-id="34a43-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="34a43-123">Conexões ao portal interrompida ao datacenter mais próximo, e o computador cliente é apresentado com informações sobre o locatário do cliente do mesmo local.</span><span class="sxs-lookup"><span data-stu-id="34a43-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="34a43-p106">O Exchange Online vai uma etapa adicional. Depois que o computador cliente estiver conectado com o datacenter mais próximo, um servidor do Exchange em que datacenter se conecta com o datacenter onde o inquilino é realmente localizado, conforme ilustrado no *como faz isso trabalhar seção* abaixo. Os servidores do Exchange Online no datacenter mais próximo e proxy as solicitações do computador cliente para o servidor de caixa de correio. Isso acelera a experiência para o computador cliente, movendo o trabalho pesado de recuperação de emails e itens de calendário para Microsoft network.</span><span class="sxs-lookup"><span data-stu-id="34a43-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="34a43-128">Como isso funciona para ofertas de nuvem padrão?</span><span class="sxs-lookup"><span data-stu-id="34a43-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="34a43-p107">Esse processo de conexão é o padrão para tráfego intenso, aplicativos da web de alto valor, como o Office 365. Nesta seção, nós de estrutura de tópicos e ilustram as etapas no processo. Quando o computador cliente não estiver na mesma região como o locatário, a conexão se parece muito diferente, dependendo do serviço que o cliente está se conectando.</span><span class="sxs-lookup"><span data-stu-id="34a43-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="34a43-p108">Este diagrama ilustra um cliente usando uma oferta padrão do Office 365 com um locatário na América do Norte. Neste cenário, a pessoa que está fazendo a solicitação tiver percorrida para Europa e está usando o Office 365 desse local.</span><span class="sxs-lookup"><span data-stu-id="34a43-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="34a43-134">O computador cliente solicita aos servidores DNS locais o endereço IP associado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="34a43-135">Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="34a43-136">Os servidores DNS da Microsoft retornam o nome de servidor regional (com base na localização dos servidores DNS do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter regional do Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="34a43-137">O computador cliente se conecta ao endereço IP do datacenter regional.</span><span class="sxs-lookup"><span data-stu-id="34a43-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="34a43-138">Os servidores do Exchange Online estabelecem uma conexão com o datacenter ativo onde o locatário do cliente reside.</span><span class="sxs-lookup"><span data-stu-id="34a43-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Datacenter regional mais próximo](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="34a43-140">Como esse trabalho para sovereign nuvem ofertas?</span><span class="sxs-lookup"><span data-stu-id="34a43-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="34a43-p109">Essa conexão é ligeiramente diferente para ofertas de nuvem soberana como o Office 365 operado pela Vianet 21. Com o locatário em uma instância de soberana do Office 365, os servidores do Office 365 mais próximo que aceitarão conexões de portal são os servidores com a região soberana cujo locatário reside. Da mesma forma, os clientes acessando SharePoint Online em nosso soberana nuvem ou ofertas padrão serão direcionados para servidores front-end cujo locatário reside. Consulte a conexão com o datacenter ativo abaixo.</span><span class="sxs-lookup"><span data-stu-id="34a43-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="34a43-145">O computador cliente solicita aos servidores DNS locais o endereço IP associado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="34a43-146">Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="34a43-147">Os servidores DNS da Microsoft retornam o nome de servidor regional (com base na localização dos servidores DNS do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter regional do Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="34a43-148">O computador cliente se conecta ao endereço IP do datacenter regional.</span><span class="sxs-lookup"><span data-stu-id="34a43-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="34a43-149">Os servidores do Exchange Online estabelecem uma conexão com o datacenter ativo onde o locatário do cliente reside.</span><span class="sxs-lookup"><span data-stu-id="34a43-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Datacenter regional dos EUA mais próximo](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="34a43-151">Conexão com o datacenter ativo</span><span class="sxs-lookup"><span data-stu-id="34a43-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="34a43-p110">Conexão com o datacenter ativo foi projetado para cargas de trabalho de transferência de dados mais pesadas e está sendo usado pelo SharePoint Online. Nessa situação, quando os clientes que tentam se conectar ao Office 365, seu navegador é redirecionado para o datacenter ativo para seu locatário do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="34a43-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="34a43-154">Como isso funciona?</span><span class="sxs-lookup"><span data-stu-id="34a43-154">How does this work?</span></span>

<span data-ttu-id="34a43-p111">Quando o computador cliente está se conectando ao SharePoint Online a partir de uma região diferente, a conexão é redirecionada para o datacenter ativo de SharePoint Online. Neste cenário, o cliente está usando um padrão que oferece, resultando nas conexões de portal remanescente local e as conexões do SharePoint Online, sendo direcionadas para o datacenter ativo.</span><span class="sxs-lookup"><span data-stu-id="34a43-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="34a43-157">O computador cliente solicita aos servidores DNS locais o endereço IP associado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="34a43-158">Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="34a43-159">Os servidores DNS da Microsoft retornam o nome do servidor do SharePoint Online datacenter ativo (com base na localização do locatário do Office 365 do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter ativo do Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="34a43-160">O computador cliente se conecta ao endereço IP do datacenter ativo.</span><span class="sxs-lookup"><span data-stu-id="34a43-160">The client computer connects to the active datacenter IP address.</span></span>

![Datacenter dos EUA ativo](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="34a43-162">Conexão em Redes Virtuais Privadas (VPN)</span><span class="sxs-lookup"><span data-stu-id="34a43-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="34a43-p112">Esse tipo de conexão se aplica somente quando uma rede virtual privada (VPN) é usada pelos computadores cliente. Na realidade, comportamento do Office 365 não será alterado simplesmente como uma VPN é usada, mas VPNs são comumente usadas para controlar como os computadores cliente estabelecem conexões com o Office 365 e, normalmente, os resultados em uma experiência de degradação, portanto é importante cobrir.</span><span class="sxs-lookup"><span data-stu-id="34a43-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="34a43-165">Como isso funciona?</span><span class="sxs-lookup"><span data-stu-id="34a43-165">How does this work?</span></span>

<span data-ttu-id="34a43-p113">Quando o computador cliente estabelece uma conexão VPN para um escritório corporativo em uma região diferente, os servidores DNS no que office são usados no lugar de servidores DNS do local do computador cliente. Na maioria dos casos, essa conexão extra através da VPN prejudicará a experiência do Office 365. Os serviços do Office 365 otimizados para conexões de cliente do serviço como e está perto do usuário final possível. Muitos serviços aproveitam a rede de borda do Azure, redes de fornecimento de conteúdo e a capacidade de rede confiável na rede Microsoft para oferecer a melhor experiência de usuário possíveis quando são feitas solicitações de rede para serviços do Office 365 mais próximo do computador cliente possível.</span><span class="sxs-lookup"><span data-stu-id="34a43-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="34a43-170">O computador cliente solicita o DNS VPN servidores para o endereço IP associado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="34a43-171">Servidores de DNS VPN do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="34a43-172">Os servidores DNS da Microsoft retornam o nome de servidor regional (com base na localização dos servidores DNS da VPN) e o computador cliente repete as etapas 1 e 2 para obter as informações de endereço IP do datacenter regional do Office 365.</span><span class="sxs-lookup"><span data-stu-id="34a43-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="34a43-173">O computador cliente se conecta com o datacenter endereço IP que mais se aproxima ao escritório corporativo com que eles estabelecerem uma conexão VPN.</span><span class="sxs-lookup"><span data-stu-id="34a43-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![Conectividade do datacenter de VPN](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="34a43-175">Aqui está um link curto que você pode usar para voltar:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="34a43-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="34a43-176">Confira também</span><span class="sxs-lookup"><span data-stu-id="34a43-176">See also</span></span>

[<span data-ttu-id="34a43-177">Gerenciando pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="34a43-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="34a43-178">Conectividade de rede para Office 365</span><span class="sxs-lookup"><span data-stu-id="34a43-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
