---
title: Introdução ao ajuste de desempenho para o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: Este artigo explica quais aspectos específicos que você precisa considerar durante a criação de páginas para obter o melhor desempenho no SharePoint Online.
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539145"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="faca2-103">Introdução ao ajuste de desempenho para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="faca2-104">Este artigo explica quais aspectos específicos que você precisa considerar durante a criação de páginas para obter o melhor desempenho no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="faca2-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="faca2-105">Neste artigo</span><span class="sxs-lookup"><span data-stu-id="faca2-105">In this article</span></span>

- <span data-ttu-id="faca2-106">[Métricas do SharePoint Online](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) e [conclusões atingido por causa dos dados](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="faca2-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="faca2-107">Usar uma conta de usuário padrão ao verificar o desempenho</span><span class="sxs-lookup"><span data-stu-id="faca2-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="faca2-108">[Categorias de Conexão para ajuste de desempenho](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [conexão do servidor](introduction-to-performance-tuning-for-sharepoint-online.md#server), [conexão de rede](introduction-to-performance-tuning-for-sharepoint-online.md#network)e [conexão do navegador](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="faca2-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="faca2-109">Métricas do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-109">SharePoint Online metrics</span></span>
<span data-ttu-id="faca2-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="faca2-110"></span></span>

<span data-ttu-id="faca2-111">As seguintes métricas amplas para o SharePoint Online fornecem dados reais sobre o desempenho:</span><span class="sxs-lookup"><span data-stu-id="faca2-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="faca2-112">Velocidade de carregamento das páginas</span><span class="sxs-lookup"><span data-stu-id="faca2-112">How fast pages load</span></span>
    
- <span data-ttu-id="faca2-113">Quantas viagens de ida e volta são exigidas por página</span><span class="sxs-lookup"><span data-stu-id="faca2-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="faca2-114">Problemas com o serviço</span><span class="sxs-lookup"><span data-stu-id="faca2-114">Issues with the service</span></span>
    
- <span data-ttu-id="faca2-115">Outras questões que causam perda de desempenho</span><span class="sxs-lookup"><span data-stu-id="faca2-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="faca2-116">Conclusões obtidas com base nos dados</span><span class="sxs-lookup"><span data-stu-id="faca2-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="faca2-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="faca2-117"></span></span>

<span data-ttu-id="faca2-118">Os dados nos informam que:</span><span class="sxs-lookup"><span data-stu-id="faca2-118">The data tells us:</span></span>
  
- <span data-ttu-id="faca2-119">a maioria das páginas apresenta um bom desempenho no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="faca2-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="faca2-120">Páginas não personalizadas carregam rapidamente.</span><span class="sxs-lookup"><span data-stu-id="faca2-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="faca2-121">O OneDrive for Business, os sites de equipe e as páginas de sistema, como _layouts, etc., carregam rapidamente.</span><span class="sxs-lookup"><span data-stu-id="faca2-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="faca2-122">O 1% mais lento das páginas do SharePoint Online demora mais de 5.000 milissegundos para carregar.</span><span class="sxs-lookup"><span data-stu-id="faca2-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="faca2-p101">Um simples teste de benchmark pode ser usado para medir o desempenho comparando o tempo de carregamento do seu próprio portal ao tempo de carregamento da home page do OneDrive for Business, que usa alguns recursos personalizados. Essa geralmente será a primeira etapa que o Suporte solicitará que você conclua ao solucionar problemas de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="faca2-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="faca2-125">Usar uma conta de usuário padrão ao verificar o desempenho</span><span class="sxs-lookup"><span data-stu-id="faca2-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="faca2-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="faca2-126"></span></span>

<span data-ttu-id="faca2-127">Um administrador de conjunto de sites, proprietário do Site, Editor ou colaborador pertencem a grupos de segurança adicional, ter permissões adicionais e, portanto, têm elementos adicionais que carrega do SharePoint em uma página.</span><span class="sxs-lookup"><span data-stu-id="faca2-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="faca2-128">Isso é aplicável para SharePoint local e o SharePoint Online, mas em um cenário local as diferenças não seja tão facilmente percebidas como no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="faca2-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="faca2-129">Para avaliar corretamente o como uma página executará para usuários, você deve usar uma conta de usuário padrão para evitar o carregamento de criação de controles e tráfego adicional relacionados aos grupos de segurança.</span><span class="sxs-lookup"><span data-stu-id="faca2-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="faca2-130">Categorias de conexão para ajuste de desempenho</span><span class="sxs-lookup"><span data-stu-id="faca2-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="faca2-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="faca2-131"></span></span>

<span data-ttu-id="faca2-p102">Você pode categorizar as conexões entre o servidor e o usuário em três componentes principais. Considere-os durante a criação de páginas do SharePoint Online para obter informações sobre o tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="faca2-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="faca2-134">**Server.** Os servidores que a Microsoft hospeda em datacenters.</span><span class="sxs-lookup"><span data-stu-id="faca2-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="faca2-135">**Rede.** Microsoft network, Internet e sua rede local entre o datacenter e seus usuários.</span><span class="sxs-lookup"><span data-stu-id="faca2-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="faca2-136">**Navegador.** Onde a página for carregada.</span><span class="sxs-lookup"><span data-stu-id="faca2-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="faca2-p103">Entre essas três conexões normalmente existem cinco motivos que causam 95% das páginas lentas. Cada um destes motivos é discutido neste artigo:</span><span class="sxs-lookup"><span data-stu-id="faca2-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="faca2-139">Problemas de navegação</span><span class="sxs-lookup"><span data-stu-id="faca2-139">Navigation issues</span></span>
    
- <span data-ttu-id="faca2-140">Acúmulo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="faca2-140">Content roll up</span></span>
    
- <span data-ttu-id="faca2-141">Arquivos grandes</span><span class="sxs-lookup"><span data-stu-id="faca2-141">Large files</span></span>
    
- <span data-ttu-id="faca2-142">Muitas solicitações ao servidor</span><span class="sxs-lookup"><span data-stu-id="faca2-142">Many requests to the server</span></span>
    
- <span data-ttu-id="faca2-143">Processamento de Web Part</span><span class="sxs-lookup"><span data-stu-id="faca2-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="faca2-144">Conexão do servidor</span><span class="sxs-lookup"><span data-stu-id="faca2-144">Server connection</span></span>
<span data-ttu-id="faca2-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="faca2-145"></span></span>

<span data-ttu-id="faca2-146">Muitos dos problemas que afetam o desempenho do SharePoint local também se aplicam ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="faca2-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="faca2-p104">Como esperado, você tem mais controle sobre o desempenho dos servidores com o SharePoint local. Com o SharePoint Online, as coisas são um pouco diferentes. Quanto mais trabalho um servidor recebe, mais tempo ele leva para renderizar uma página. Com o SharePoint, as principais responsáveis nesse sentido são as páginas complexas com várias web parts.</span><span class="sxs-lookup"><span data-stu-id="faca2-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="faca2-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-151">SharePoint Online</span></span>
  
![Captura de tela do servidor online](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="faca2-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="faca2-153">SharePoint</span></span>
  
![Captura de tela do servidor local](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="faca2-p105">Com o SharePoint Online, determinadas solicitações de página podem realmente acabar chamando vários servidores. Você pode acabar com uma matriz de solicitações entre servidores para uma solicitação individual. Estas interações são caras da perspectiva de carregamento da página e tornam o processo mais lento.</span><span class="sxs-lookup"><span data-stu-id="faca2-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="faca2-158">Exemplos dessas interações de servidor para servidor são:</span><span class="sxs-lookup"><span data-stu-id="faca2-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="faca2-159">Web para SQL Servers</span><span class="sxs-lookup"><span data-stu-id="faca2-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="faca2-160">Web para servidores de aplicativos</span><span class="sxs-lookup"><span data-stu-id="faca2-160">Web to application servers</span></span>
    
<span data-ttu-id="faca2-p106">Outro aspecto que pode reduzir a velocidade das interações do servidor são os erros de cache. Ao contrário do SharePoint local, há uma chance muito pequena de você atingir o mesmo servidor de uma página visitada anteriormente; isso torna o cache de objeto obsoleto.</span><span class="sxs-lookup"><span data-stu-id="faca2-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="faca2-163">Conexão de rede</span><span class="sxs-lookup"><span data-stu-id="faca2-163">Network connection</span></span>
<span data-ttu-id="faca2-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="faca2-164"></span></span>

<span data-ttu-id="faca2-p107">Com o SharePoint local que não faz uso de uma WAN, você poderá usar uma conexão de alta velocidade entre datacenter e usuários finais. Geralmente, as coisas são fáceis de gerenciar a partir de uma perspectiva de rede.</span><span class="sxs-lookup"><span data-stu-id="faca2-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="faca2-167">Com o SharePoint Online, há alguns outros fatores a considerar; por exemplo:</span><span class="sxs-lookup"><span data-stu-id="faca2-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="faca2-168">A rede da Microsoft</span><span class="sxs-lookup"><span data-stu-id="faca2-168">The Microsoft network</span></span>
    
- <span data-ttu-id="faca2-169">A Internet</span><span class="sxs-lookup"><span data-stu-id="faca2-169">The Internet</span></span>
    
- <span data-ttu-id="faca2-170">O ISP</span><span class="sxs-lookup"><span data-stu-id="faca2-170">The ISP</span></span>
    
<span data-ttu-id="faca2-171">Seja qual for a versão do SharePoint (e da rede) que estiver sendo usada, os motivos que geralmente fazem com que a rede esteja ocupada incluem:</span><span class="sxs-lookup"><span data-stu-id="faca2-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="faca2-172">Grande carga</span><span class="sxs-lookup"><span data-stu-id="faca2-172">Large payload</span></span>
    
- <span data-ttu-id="faca2-173">Muitos arquivos</span><span class="sxs-lookup"><span data-stu-id="faca2-173">Many files</span></span>
    
- <span data-ttu-id="faca2-174">Grande distância física até o servidor</span><span class="sxs-lookup"><span data-stu-id="faca2-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="faca2-p108">Um recurso que você pode aproveitar no SharePoint Online é a Microsoft CDN (rede de fornecimento de conteúdo). Uma CDN é basicamente uma coleção distribuída de servidores implantados em vários datacenters. Com uma CDN, o conteúdo em páginas pode ser hospedado em um servidor e o cliente está perto do mesmo se o cliente está longe do servidor do SharePoint de origem. Microsoft usarão isso em mais detalhes no futuro para armazenar instâncias locais das páginas que não podem ser personalizadas, por exemplo o SharePoint admin home page Online. Para obter mais informações sobre as CDNs, consulte [redes de fornecimento de conteúdo](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span><span class="sxs-lookup"><span data-stu-id="faca2-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="faca2-p109">Algo que de que você deve estar ciente, mas que não pode fazer muito para mudar, é a velocidade de conexão do seu ISP. Uma simples ferramenta de teste de velocidade indicará a velocidade de conexão.</span><span class="sxs-lookup"><span data-stu-id="faca2-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="faca2-182">Conexão do navegador</span><span class="sxs-lookup"><span data-stu-id="faca2-182">Browser connection</span></span>
<span data-ttu-id="faca2-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="faca2-183"></span></span>

<span data-ttu-id="faca2-184">Existem alguns fatores que devem ser considerados com relação aos navegadores da Web de uma perspectiva de desempenho.</span><span class="sxs-lookup"><span data-stu-id="faca2-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="faca2-p110">Visitar páginas complexas afetará o desempenho. A maioria dos navegadores têm apenas um cache pequeno (aproximadamente 90MB), enquanto a média página da web é geralmente cerca de 1.6 MB. Isso não leva muito tempo para ser usado para cima.</span><span class="sxs-lookup"><span data-stu-id="faca2-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="faca2-p111">Largura de banda também pode ser um problema. Por exemplo, se um usuário está assistindo a vídeos em outra sessão, isso afetará o desempenho da sua página do SharePoint. Enquanto você não pode impedir usuários de fluxo de mídia, você pode controlar a maneira como uma página carregará para usuários.</span><span class="sxs-lookup"><span data-stu-id="faca2-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="faca2-191">Confira os seguintes artigos para diferentes técnicas de personalização de página do SharePoint Online e outras práticas recomendadas para ajudá-lo a obter o desempenho ideal.</span><span class="sxs-lookup"><span data-stu-id="faca2-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="faca2-192">Opções de navegação para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="faca2-193">Use a ferramenta de diagnóstico de página para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="faca2-194">Otimização de imagem para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="faca2-195">Atraso no carregamento de imagens e JavaScript no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="faca2-196">Minificação e agrupamento no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="faca2-197">Usando redes de distribuição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="faca2-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="faca2-198">Usando o Web Part de pesquisa de conteúdo, em vez de Web Part de consulta de conteúdo para melhorar o desempenho no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="faca2-199">SharePoint Online de teste de carga e planejamento de capacidade</span><span class="sxs-lookup"><span data-stu-id="faca2-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="faca2-200">Diagnosticando problemas de desempenho no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="faca2-201">Usando o cache de objetos com o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="faca2-202">Como evitar ficar limitado ou bloqueado no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="faca2-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

