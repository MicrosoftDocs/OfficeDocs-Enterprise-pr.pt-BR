---
title: Opções de navegação para o SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Este artigo descreve os sites de opções de navegação com a publicação do SharePoint habilitada no SharePoint Online. A escolha e a configuração de navegação impactam significativamente o desempenho e a escalabilidade de sites no SharePoint Online. Este artigo não se aplica a sites de equipe clássicos.
ms.openlocfilehash: d86b0462e8ddb93c39eab0d42a24f3a94f785ecd
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078306"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="025c6-105">Opções de navegação para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="025c6-105">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="025c6-106">Este artigo descreve os sites de opções de navegação com a publicação do SharePoint habilitada no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="025c6-106">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="025c6-107">A escolha e a configuração de navegação impactam significativamente o desempenho e a escalabilidade de sites no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="025c6-107">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="025c6-108">Visão geral</span><span class="sxs-lookup"><span data-stu-id="025c6-108">Overview</span></span>

<span data-ttu-id="025c6-109">A configuração do provedor de navegação pode impactar significativamente o desempenho de todo o site e é necessário fazer uma consideração cuidadosa para escolher um provedor de navegação e uma configuração que sejam dimensionados de forma eficaz para os requisitos de um site do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="025c6-109">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="025c6-110">Há dois provedores de navegação prontos para uso, bem como implementações de navegação personalizadas.</span><span class="sxs-lookup"><span data-stu-id="025c6-110">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="025c6-111">A primeira opção, [**navegação gerenciada (metadados)**](#using-managed-navigation-and-metadata-in-sharepoint-online), é recomendada e é uma das opções padrão no SharePoint Online; no entanto, recomendamos que o aparamento de segurança seja desabilitado, a menos que seja necessário</span><span class="sxs-lookup"><span data-stu-id="025c6-111">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="025c6-112">O aparamento de segurança está habilitado como uma configuração segura por padrão para este provedor de navegação; no entanto, muitos sites não exigem a sobrecarga da filtragem de segurança, já que os elementos de navegação freqüentemente são consistentes para todos os usuários do site.</span><span class="sxs-lookup"><span data-stu-id="025c6-112">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="025c6-113">Com a configuração recomendada para desabilitar a filtragem de segurança, esse provedor de navegação não requer a enumeração da estrutura do site e é altamente escalável com impacto de desempenho aceitável.</span><span class="sxs-lookup"><span data-stu-id="025c6-113">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="025c6-114">A segunda opção, [**navegação estrutural**](#using-structural-navigation-in-sharepoint-online), **não é uma opção de navegação recomendada no SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="025c6-114">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="025c6-115">Este provedor de navegação foi projetado para uma topologia local com suporte limitado no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="025c6-115">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="025c6-116">Enquanto fornece um conjunto adicional de recursos em relação a outras opções de navegação, esses recursos, incluindo filtragem de segurança e enumeração de estrutura de site, vêm com um custo de chamadas excessivas no servidor e impactam a escalabilidade e o desempenho quando são usados.</span><span class="sxs-lookup"><span data-stu-id="025c6-116">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="025c6-117">Sites usando navegação estruturada que consumam recursos excessivos podem estar sujeitos à limitação.</span><span class="sxs-lookup"><span data-stu-id="025c6-117">Sites using structured navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="025c6-118">Além dos provedores de navegação prontos para uso, muitos clientes implementaram com êxito implementações de navegação personalizada alternativas.</span><span class="sxs-lookup"><span data-stu-id="025c6-118">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="025c6-119">Uma classe comum de implementações de navegação personalizadas engloba padrões de design renderizados pelo cliente que armazenam um cache local de nós de navegação.</span><span class="sxs-lookup"><span data-stu-id="025c6-119">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="025c6-120">(Confira **[scripts do lado do cliente orientados por pesquisa](#using-search-driven-client-side-scripting)** neste artigo.)</span><span class="sxs-lookup"><span data-stu-id="025c6-120">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="025c6-121">Esses provedores de navegação têm algumas vantagens importantes:</span><span class="sxs-lookup"><span data-stu-id="025c6-121">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="025c6-122">Em geral, eles funcionam bem com designs de página responsivos.</span><span class="sxs-lookup"><span data-stu-id="025c6-122">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="025c6-123">Eles são extremamente escalonáveis e de desempenho porque podem renderizar sem custo de recurso (e atualizar em segundo plano após um tempo limite).</span><span class="sxs-lookup"><span data-stu-id="025c6-123">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="025c6-124">Esses provedores de navegação podem recuperar dados de navegação usando várias estratégias, variando de configurações estáticas simples para vários provedores de dados dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="025c6-124">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="025c6-125">Um exemplo de um provedor de dados é usar uma **navegação orientada por pesquisa**, o que permite flexibilidade para enumerar nós de navegação e manipular a filtragem de segurança com eficiência.</span><span class="sxs-lookup"><span data-stu-id="025c6-125">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="025c6-126">Há outras opções populares para criar **provedores de navegação personalizados**.</span><span class="sxs-lookup"><span data-stu-id="025c6-126">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="025c6-127">Revise as [soluções de navegação para portais do SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) para obter mais orientações sobre a criação de um provedor de navegação personalizado.</span><span class="sxs-lookup"><span data-stu-id="025c6-127">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="025c6-128">Prós e contras das opções de navegação do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="025c6-128">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="025c6-129">A tabela a seguir resume os prós e contras de cada opção.</span><span class="sxs-lookup"><span data-stu-id="025c6-129">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="025c6-130">Navegação gerenciada</span><span class="sxs-lookup"><span data-stu-id="025c6-130">Managed navigation</span></span>  |<span data-ttu-id="025c6-131">Navegação estrutural</span><span class="sxs-lookup"><span data-stu-id="025c6-131">Structural navigation</span></span>  |<span data-ttu-id="025c6-132">Navegação orientada por pesquisa</span><span class="sxs-lookup"><span data-stu-id="025c6-132">Search-driven navigation</span></span>  |<span data-ttu-id="025c6-133">Provedor de navegação personalizada</span><span class="sxs-lookup"><span data-stu-id="025c6-133">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="025c6-134">Prós</span><span class="sxs-lookup"><span data-stu-id="025c6-134">Pros:</span></span><br/><br/><span data-ttu-id="025c6-135">Fácil de manter</span><span class="sxs-lookup"><span data-stu-id="025c6-135">Easy to maintain</span></span><br/><span data-ttu-id="025c6-136">Opção recomendada</span><span class="sxs-lookup"><span data-stu-id="025c6-136">Recommended option</span></span><br/>     |<span data-ttu-id="025c6-137">Prós</span><span class="sxs-lookup"><span data-stu-id="025c6-137">Pros:</span></span><br/><br/><span data-ttu-id="025c6-138">Fácil de configurar</span><span class="sxs-lookup"><span data-stu-id="025c6-138">Easy to configure</span></span><br/><span data-ttu-id="025c6-139">Segurança cortada</span><span class="sxs-lookup"><span data-stu-id="025c6-139">Security trimmed</span></span><br/><span data-ttu-id="025c6-140">Atualiza automaticamente à medida que o conteúdo é adicionado</span><span class="sxs-lookup"><span data-stu-id="025c6-140">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="025c6-141">Prós</span><span class="sxs-lookup"><span data-stu-id="025c6-141">Pros:</span></span><br/><br/><span data-ttu-id="025c6-142">Segurança cortada</span><span class="sxs-lookup"><span data-stu-id="025c6-142">Security trimmed</span></span><br/><span data-ttu-id="025c6-143">Atualiza automaticamente à medida que os sites são adicionados</span><span class="sxs-lookup"><span data-stu-id="025c6-143">Automatically updates as sites are added</span></span><br/><span data-ttu-id="025c6-144">Tempo de carregamento rápido e estrutura de navegação em cache local</span><span class="sxs-lookup"><span data-stu-id="025c6-144">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="025c6-145">Prós</span><span class="sxs-lookup"><span data-stu-id="025c6-145">Pros:</span></span><br/><br/><span data-ttu-id="025c6-146">Escolha mais ampla de opções disponíveis</span><span class="sxs-lookup"><span data-stu-id="025c6-146">Wider choice of options available</span></span><br/><span data-ttu-id="025c6-147">Carregamento rápido quando o cache é usado corretamente</span><span class="sxs-lookup"><span data-stu-id="025c6-147">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="025c6-148">Muitas opções funcionam bem com o design de página responsivo</span><span class="sxs-lookup"><span data-stu-id="025c6-148">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="025c6-149">Contras</span><span class="sxs-lookup"><span data-stu-id="025c6-149">Cons:</span></span><br/><br/><span data-ttu-id="025c6-150">Não atualizado automaticamente para refletir a estrutura do site</span><span class="sxs-lookup"><span data-stu-id="025c6-150">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="025c6-151">Impacta o desempenho se a filtragem de segurança estiver habilitada</span><span class="sxs-lookup"><span data-stu-id="025c6-151">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="025c6-152">Contras</span><span class="sxs-lookup"><span data-stu-id="025c6-152">Cons:</span></span><br/><br/><span data-ttu-id="025c6-153">**Não recomendado**</span><span class="sxs-lookup"><span data-stu-id="025c6-153">**Not recommended**</span></span><br/><span data-ttu-id="025c6-154">**Impacta o desempenho e a escalabilidade**</span><span class="sxs-lookup"><span data-stu-id="025c6-154">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="025c6-155">**Sujeito à limitação**</span><span class="sxs-lookup"><span data-stu-id="025c6-155">**Subject to throttling**</span></span><br/>|<span data-ttu-id="025c6-156">Contras</span><span class="sxs-lookup"><span data-stu-id="025c6-156">Cons:</span></span><br/><br/><span data-ttu-id="025c6-157">Sem capacidade para encomendar facilmente sites</span><span class="sxs-lookup"><span data-stu-id="025c6-157">No ability to easily order sites</span></span><br/><span data-ttu-id="025c6-158">Requer a personalização da página mestra (habilidades técnicas obrigatórias)</span><span class="sxs-lookup"><span data-stu-id="025c6-158">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="025c6-159">Contras</span><span class="sxs-lookup"><span data-stu-id="025c6-159">Cons:</span></span><br/><br/><span data-ttu-id="025c6-160">O desenvolvimento personalizado é necessário</span><span class="sxs-lookup"><span data-stu-id="025c6-160">Custom development is required</span></span><br/><span data-ttu-id="025c6-161">A fonte de dados externa/cache armazenado é necessária, por exemplo, o Azure</span><span class="sxs-lookup"><span data-stu-id="025c6-161">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="025c6-162">A opção mais apropriada para seu site dependerá dos requisitos do seu site e do seu recurso técnico.</span><span class="sxs-lookup"><span data-stu-id="025c6-162">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="025c6-163">Se você quiser um provedor de navegação de caixa de saída escalável, a navegação gerenciada com a remoção de segurança desabilitada é uma boa opção.</span><span class="sxs-lookup"><span data-stu-id="025c6-163">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span>

<span data-ttu-id="025c6-164">A opção de navegação gerenciada pode ser mantida através da configuração, não envolve arquivos de personalização de código e é significativamente mais rápida do que a navegação estrutural.</span><span class="sxs-lookup"><span data-stu-id="025c6-164">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="025c6-165">Se você precisar de filtragem de segurança e estiver seguro usando uma página mestra personalizada e tiver algum recurso na organização para manter as alterações que podem ocorrer na página mestra padrão do SharePoint Online, a opção orientada por pesquisa poderá produzir um melhor experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="025c6-165">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="025c6-166">Se você tiver requisitos mais complexos, um provedor de navegação personalizado pode ser a escolha certa.</span><span class="sxs-lookup"><span data-stu-id="025c6-166">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="025c6-167">A navegação estrutural não é recomendada.</span><span class="sxs-lookup"><span data-stu-id="025c6-167">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="025c6-168">Por fim, é importante observar que o SharePoint está adicionando outros provedores de navegação e funcionalidade para arquiteturas de site do SharePoint modernas, aproveitando uma hierarquia de sites mais nivelada e um modelo de Hub e spoke com sites de Hub do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="025c6-168">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="025c6-169">Isso permite que muitos cenários sejam alcançados e não exijam o uso do recurso de publicação do SharePoint, e essas configurações de navegação são otimizadas para escalabilidade e latência no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="025c6-169">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="025c6-170">Observe que aplicar o mesmo princípio – simplificando a estrutura geral do seu site de publicação do SharePoint para uma estrutura Flatter, geralmente ajuda no desempenho e na escala gerais.</span><span class="sxs-lookup"><span data-stu-id="025c6-170">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="025c6-171">Isso significa que, em vez de ter um único conjunto de sites com centenas de sites (subwebs), uma abordagem melhor é ter muitos conjuntos de sites com muito poucos subsites (subwebs).</span><span class="sxs-lookup"><span data-stu-id="025c6-171">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="025c6-172">Usando a navegação gerenciada e metadados no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="025c6-172">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="025c6-173">A navegação gerenciada é outra opção pronta para uso, que você pode usar para recriar a maior parte da mesma funcionalidade que a navegação estrutural.</span><span class="sxs-lookup"><span data-stu-id="025c6-173">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="025c6-174">Os metadados gerenciados podem ser configurados para que o aparamento de segurança seja habilitado ou desabilitado.</span><span class="sxs-lookup"><span data-stu-id="025c6-174">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="025c6-175">Quando configurado com o aparamento de segurança desabilitado, a navegação gerenciada é bastante eficiente, pois carrega todos os links de navegação com um número constante de chamadas do servidor.</span><span class="sxs-lookup"><span data-stu-id="025c6-175">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="025c6-176">Habilitar a filtragem de segurança, no entanto, elimina algumas das vantagens da navegação gerenciada e os clientes podem optar por explorar uma das soluções de navegação personalizadas para obter desempenho e escalabilidade ideais.</span><span class="sxs-lookup"><span data-stu-id="025c6-176">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="025c6-177">Muitos sites não exigem filtragem de segurança, já que a estrutura de navegação é geralmente consistente para todos os usuários do site.</span><span class="sxs-lookup"><span data-stu-id="025c6-177">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="025c6-178">Se a filtragem de segurança estiver desabilitada e um link for adicionado à navegação à qual nem todos os usuários tenham acesso, o link ainda será mostrado, mas levará a uma mensagem de acesso negado.</span><span class="sxs-lookup"><span data-stu-id="025c6-178">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="025c6-179">Não há risco de acesso inadvertido ao conteúdo.</span><span class="sxs-lookup"><span data-stu-id="025c6-179">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="025c6-180">Como implementar a navegação gerenciada e os resultados</span><span class="sxs-lookup"><span data-stu-id="025c6-180">How to implement managed navigation and the results</span></span>

<span data-ttu-id="025c6-181">Há vários artigos no Docs.Microsoft.com sobre os detalhes da navegação gerenciada, por exemplo, confira [visão geral da navegação gerenciada no SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="025c6-181">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="025c6-182">Para implementar a navegação gerenciada, você configura termos com URLs correspondentes à estrutura de navegação do site.</span><span class="sxs-lookup"><span data-stu-id="025c6-182">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="025c6-183">A navegação gerenciada pode até ser organizada manualmente para substituir a navegação estrutural em muitos casos.</span><span class="sxs-lookup"><span data-stu-id="025c6-183">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="025c6-184">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="025c6-184">For example:</span></span>

![Estrutura do site do SharePoint Online](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="025c6-186">O exemplo a seguir mostra o desempenho da navegação complexa usando a navegação gerenciada.</span><span class="sxs-lookup"><span data-stu-id="025c6-186">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Desempenho da navegação complexa usando a navegação gerenciada](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="025c6-188">Usar a navegação gerenciada aumenta consistentemente o desempenho em comparação com a abordagem de navegação estrutural.</span><span class="sxs-lookup"><span data-stu-id="025c6-188">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="025c6-189">Usando a navegação estrutural no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="025c6-189">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="025c6-190">Esta é a navegação pronta para uso, usada por padrão e é a solução mais direta, mas, como tal, tem uma compensação de desempenho dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="025c6-190">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="025c6-191">Não requer personalização e um usuário não técnico também pode facilmente adicionar itens, ocultar itens e gerenciar a navegação na página Configurações.</span><span class="sxs-lookup"><span data-stu-id="025c6-191">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="025c6-192">No entanto, isso também é verdadeiro para a navegação gerenciada, de modo que seja recomendado usar a navegação gerenciada, também pode ser facilmente gerenciada e controlada, bem como um desempenho aprimorado.</span><span class="sxs-lookup"><span data-stu-id="025c6-192">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Navegação estrutural com mostrar subsites selecionados](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="025c6-194">Ativando a navegação estrutural no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="025c6-194">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="025c6-195">Ilustrar como o desempenho em uma solução do SharePoint Online padrão com navegação estrutural e a opção Mostrar subsites ativadas.</span><span class="sxs-lookup"><span data-stu-id="025c6-195">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="025c6-196">Veja a seguir uma captura de tela das configurações encontradas na **navegação** **configurações** \> do site da página.</span><span class="sxs-lookup"><span data-stu-id="025c6-196">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Captura de tela mostrando subsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="025c6-198">Analisar o desempenho da navegação estrutural no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="025c6-198">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="025c6-199">Para analisar o desempenho de uma página do SharePoint, use a guia **rede** das ferramentas de desenvolvedor F12 no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="025c6-199">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Captura de tela mostrando a guia Rede das ferramentas de desenvolvimento F12](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="025c6-201">Na guia **rede** , clique na página. aspx que está sendo carregada e, em seguida, clique na guia **detalhes** .</span><span class="sxs-lookup"><span data-stu-id="025c6-201">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="025c6-202">![Captura de tela mostrando a guia de detalhes](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="025c6-202">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="025c6-203">Clique em **cabeçalhos de resposta**.</span><span class="sxs-lookup"><span data-stu-id="025c6-203">Click **Response headers**.</span></span> <br/><span data-ttu-id="025c6-204">![Captura de tela da guia Detalhes](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="025c6-204">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="025c6-205">O SharePoint retorna algumas informações úteis de diagnóstico em seus cabeçalhos de resposta.</span><span class="sxs-lookup"><span data-stu-id="025c6-205">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="025c6-206">Uma das informações mais úteis é o **SPRequestDuration** , que é o valor, em milissegundos, quanto tempo uma solicitação levou para ser processada no servidor.</span><span class="sxs-lookup"><span data-stu-id="025c6-206">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="025c6-207">A captura de tela a seguir **mostra subsites** está desmarcada para a navegação estrutural.</span><span class="sxs-lookup"><span data-stu-id="025c6-207">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="025c6-208">Isso significa que há apenas o link do conjunto de sites na navegação global:</span><span class="sxs-lookup"><span data-stu-id="025c6-208">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="025c6-209">![Captura de tela mostrando tempos de carga como duração da solicitação](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="025c6-209">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="025c6-210">A chave **SPRequestDuration** tem um valor de 245 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="025c6-210">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="025c6-211">Isso representa o tempo necessário para retornar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="025c6-211">This represents the time it took to return the request.</span></span> <span data-ttu-id="025c6-212">Como há apenas um item de navegação no site, este é um bom benchmark para como o SharePoint Online é executado sem uma navegação intensa.</span><span class="sxs-lookup"><span data-stu-id="025c6-212">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="025c6-213">A captura de tela a seguir mostra como a adição nos subsites afeta essa chave.</span><span class="sxs-lookup"><span data-stu-id="025c6-213">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="025c6-214">![Captura de tela mostrando uma duração de solicitação de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="025c6-214">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="025c6-215">A adição dos subsites aumentou significativamente o tempo necessário para retornar a solicitação de página para este site de exemplo relativamente simples.</span><span class="sxs-lookup"><span data-stu-id="025c6-215">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="025c6-216">Hierarquias de sites complexas, incluindo páginas em navegação, e outras opções de configuração e topologia, podem aumentar consideravelmente esse impacto ainda mais.</span><span class="sxs-lookup"><span data-stu-id="025c6-216">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="025c6-217">Usando scripts do lado do cliente orientados por pesquisa</span><span class="sxs-lookup"><span data-stu-id="025c6-217">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="025c6-218">Usando a pesquisa você pode aproveitar os índices criados em segundo plano usando o rastreamento contínuo.</span><span class="sxs-lookup"><span data-stu-id="025c6-218">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="025c6-219">Os resultados da pesquisa são extraídos do índice de pesquisa e os resultados são cortados de segurança.</span><span class="sxs-lookup"><span data-stu-id="025c6-219">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="025c6-220">Isso é geralmente mais rápido do que os provedores de navegação prontos quando o aparamento de segurança é necessário.</span><span class="sxs-lookup"><span data-stu-id="025c6-220">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="025c6-221">Usando a pesquisa para navegação estrutural, especialmente se você tiver uma estrutura de site complexa, acelerará consideravelmente o tempo de carregamento da página.</span><span class="sxs-lookup"><span data-stu-id="025c6-221">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="025c6-222">A principal vantagem disso sobre a navegação gerenciada é que você se beneficia da filtragem de segurança.</span><span class="sxs-lookup"><span data-stu-id="025c6-222">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="025c6-223">Essa abordagem envolve a criação de uma página mestra personalizada e a substituição do código de navegação pronto com HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="025c6-223">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="025c6-224">Siga este procedimento descrito no exemplo a seguir para substituir o código de navegação no arquivo `seattle.html`.</span><span class="sxs-lookup"><span data-stu-id="025c6-224">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="025c6-225">Neste exemplo, você abrirá o `seattle.html` arquivo e substituirá o elemento `id=”DeltaTopNavigation”` inteiro pelo código HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="025c6-225">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="025c6-226">Exemplo: substituir o código de navegação pronto em uma página mestra</span><span class="sxs-lookup"><span data-stu-id="025c6-226">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="025c6-227">Navegue até a página Configurações do site.</span><span class="sxs-lookup"><span data-stu-id="025c6-227">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="025c6-228">Abra a Galeria de páginas mestras clicando em **páginas mestras**.</span><span class="sxs-lookup"><span data-stu-id="025c6-228">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="025c6-229">Aqui você pode navegar pela biblioteca e baixar o arquivo `seattle.master`.</span><span class="sxs-lookup"><span data-stu-id="025c6-229">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="025c6-230">Edite o código usando um editor de texto e exclua o bloco de código na captura de tela a seguir.</span><span class="sxs-lookup"><span data-stu-id="025c6-230">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Excluir o bloco de código mostrado](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="025c6-232">Remova o código entre as `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` marcas `<\SharePoint:AjaxDelta>` e e substitua-o pelo seguinte trecho:</span><span class="sxs-lookup"><span data-stu-id="025c6-232">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. <span data-ttu-id="025c6-233">Substitua a URL na marca de âncora carregar imagem no início, com um link para uma imagem de carregamento no seu conjunto de sites.</span><span class="sxs-lookup"><span data-stu-id="025c6-233">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="025c6-234">Depois de fazer as alterações, renomeie o arquivo e carregue-o na Galeria de páginas mestras.</span><span class="sxs-lookup"><span data-stu-id="025c6-234">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="025c6-235">Isso gera um novo arquivo. master.</span><span class="sxs-lookup"><span data-stu-id="025c6-235">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="025c6-236">Este HTML é a marcação básica que será preenchida pelos resultados da pesquisa retornados do código JavaScript.</span><span class="sxs-lookup"><span data-stu-id="025c6-236">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="025c6-237">Você precisará editar o código para alterar o valor de var root = "URL do conjunto de sites", conforme demonstrado no seguinte trecho de código:</span><span class="sxs-lookup"><span data-stu-id="025c6-237">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="025c6-238">Os resultados são atribuídos à matriz Self. Nodes e uma hierarquia é criada a partir dos objetos usando LINQ. js, atribuindo a saída a uma hierarquia de matriz própria.</span><span class="sxs-lookup"><span data-stu-id="025c6-238">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="025c6-239">Esta matriz é o objeto que está vinculado ao HTML.</span><span class="sxs-lookup"><span data-stu-id="025c6-239">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="025c6-240">Isso é feito na função toggleView (), passando o autoobjeto para a função ko. applybinding ().</span><span class="sxs-lookup"><span data-stu-id="025c6-240">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="025c6-241">Isso faz com que a matriz de hierarquia seja vinculada ao seguinte HTML:</span><span class="sxs-lookup"><span data-stu-id="025c6-241">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="025c6-242">Os manipuladores de eventos `mouseenter` para `mouseexit` e são adicionados à navegação de nível superior para lidar com os menus suspensos de subsites que é feito `addEventsToElements()` na função.</span><span class="sxs-lookup"><span data-stu-id="025c6-242">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="025c6-243">No nosso exemplo de navegação complexa, uma nova carga de página sem o cache local mostra que o tempo gasto no servidor foi reduzido da navegação estrutural de benchmark para obter um resultado semelhante à abordagem de navegação gerenciada.</span><span class="sxs-lookup"><span data-stu-id="025c6-243">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="025c6-244">Sobre o arquivo JavaScript...</span><span class="sxs-lookup"><span data-stu-id="025c6-244">About the JavaScript file...</span></span>

<span data-ttu-id="025c6-245">O arquivo JavaScript inteiro é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="025c6-245">The entire JavaScript file is as follows:</span></span>

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

<span data-ttu-id="025c6-246">Para resumir o código mostrado acima na `jQuery $(document).ready` função, há uma `viewModel object` criada e, em `loadNavigationNodes()` seguida, a função desse objeto é chamada.</span><span class="sxs-lookup"><span data-stu-id="025c6-246">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="025c6-247">Essa função carrega a hierarquia de navegação criada anteriormente armazenada no armazenamento local do HTML5 do navegador cliente ou chama a função `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="025c6-247">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="025c6-248">`QueryRemoteInterface()`Cria uma solicitação usando a `getRequest()` função com o parâmetro de consulta definido anteriormente no script e, em seguida, retorna dados do servidor.</span><span class="sxs-lookup"><span data-stu-id="025c6-248">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="025c6-249">Esses dados são essencialmente uma matriz de todos os sites no conjunto de sites representados como objetos de transferência de dados com várias propriedades.</span><span class="sxs-lookup"><span data-stu-id="025c6-249">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="025c6-250">Esses dados são analisados nos objetos previamente definidos `SPO.Models.NavigationNode` que usam `Knockout.js` para criar propriedades observáveis para uso por dados associando os valores no HTML que definimos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="025c6-250">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="025c6-251">Os objetos são então colocados em uma matriz de resultados.</span><span class="sxs-lookup"><span data-stu-id="025c6-251">The objects are then put into a results array.</span></span> <span data-ttu-id="025c6-252">Essa matriz é analisada no JSON usando vazar e armazenada no armazenamento de navegador local para melhorar o desempenho em cargas de página futuras.</span><span class="sxs-lookup"><span data-stu-id="025c6-252">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="025c6-253">Benefícios dessa abordagem</span><span class="sxs-lookup"><span data-stu-id="025c6-253">Benefits of this approach</span></span>

<span data-ttu-id="025c6-254">Uma das principais vantagens dessa [abordagem](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) é que, usando o armazenamento local do HTML5, a navegação é armazenada localmente para o usuário na próxima vez que ele carregar a página.</span><span class="sxs-lookup"><span data-stu-id="025c6-254">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="025c6-255">Obtemos grandes aprimoramentos de desempenho ao usar a API de pesquisa para navegação estrutural; no entanto, ele leva algum recurso técnico para executar e personalizar essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="025c6-255">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="025c6-256">Na [implementação de exemplo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), os sites são classificados da mesma maneira que a navegação estrutural pronta para uso; ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="025c6-256">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="025c6-257">Se você quisesse se desviar dessa ordem, seria mais complicado desenvolver e manter.</span><span class="sxs-lookup"><span data-stu-id="025c6-257">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="025c6-258">Além disso, essa abordagem exige que você se desvie das páginas mestras com suporte.</span><span class="sxs-lookup"><span data-stu-id="025c6-258">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="025c6-259">Se a página mestra personalizada não for mantida, seu site perderá as atualizações e melhorias que a Microsoft faz nas páginas mestras.</span><span class="sxs-lookup"><span data-stu-id="025c6-259">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="025c6-260">O [código acima](#about-the-javascript-file) tem as seguintes dependências:</span><span class="sxs-lookup"><span data-stu-id="025c6-260">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="025c6-261">jQueryhttps://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="025c6-261">jQuery - https://jquery.com/</span></span>
- <span data-ttu-id="025c6-262">KnockoutJS -https://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="025c6-262">KnockoutJS - https://knockoutjs.com/</span></span>
- <span data-ttu-id="025c6-263">LINQ. js- https://linqjs.codeplex.com/ou github.com/neuecc/LINQ.js</span><span class="sxs-lookup"><span data-stu-id="025c6-263">Linq.js - https://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="025c6-264">A versão atual do LinqJS não contém o método ByHierarchy usado no código acima e quebrará o código de navegação.</span><span class="sxs-lookup"><span data-stu-id="025c6-264">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="025c6-265">Para corrigir isso, adicione o seguinte método ao arquivo LINQ. js antes da linha `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="025c6-265">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a><span data-ttu-id="025c6-266">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="025c6-266">Related topics</span></span>

[<span data-ttu-id="025c6-267">Visão geral da navegação gerenciada no SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="025c6-267">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

