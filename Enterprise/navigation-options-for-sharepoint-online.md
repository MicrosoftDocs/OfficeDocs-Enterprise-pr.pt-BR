---
title: Opções de navegação para o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Este artigo descreve como melhorar os tempos de carregamento de página para o SharePoint Online usando navegação gerenciada ou navegação orientada por pesquisa na publicação clássico.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539404"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="e6442-103">Opções de navegação para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e6442-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="e6442-104">Este artigo descreve como melhorar os tempos de carregamento de página para o SharePoint Online usando navegação gerenciada ou navegação orientada por pesquisa na publicação clássico.</span><span class="sxs-lookup"><span data-stu-id="e6442-104">This article describes how to improve page load times for SharePoint Online by using managed navigation or search-driven navigation in Classic publishing.</span></span>
  
<span data-ttu-id="e6442-105">SharePoint Online com publicação clássica habilitada tem duas áreas de navegação; Navegação global e navegação atual.</span><span class="sxs-lookup"><span data-stu-id="e6442-105">SharePoint Online with classic publishing enabled has two navigation areas; Global Navigation and Current Navigation.</span></span>
  
<span data-ttu-id="e6442-106">Navegação global é o menu de navegação superior, enquanto navegação atual está o lado ou em contexto esquerda/direita navegação depende a configuração de idioma e a página mestra utilizada.</span><span class="sxs-lookup"><span data-stu-id="e6442-106">Global navigation is the top navigation menu while Current Navigation is the side or in-context left/right navigation dependent on the language configuration and master page utilized.</span></span>
  
<span data-ttu-id="e6442-107">Navegação pode afetar negativamente o desempenho para o Portal inteiro conforme ele é geralmente configurado para uso do portal para toda a empresa e como tal, é um elemento importante de qualquer site do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e6442-107">Navigation can negatively impact performance for the entire Portal as it is often configured for portal-wide use and as such is an important element of any SharePoint site.</span></span>
  
<span data-ttu-id="e6442-108">Navegação estrutural não é a opção recomendada de navegação no SharePoint Online, pois ele foi projetado para uma topologia de local diante com a filtragem de segurança e esse projeto faz com que as chamadas de cargas excessivas no servidor e afeta o desempenho quando ele é usado.</span><span class="sxs-lookup"><span data-stu-id="e6442-108">Structural navigation is not the recommended navigation option in SharePoint Online as it was designed for an On-premise topology with security trimming and this design causes excessive server calls and impacts performance when it is used.</span></span>
  
<span data-ttu-id="e6442-p101">Que o design foi alterado com a introdução dos sites do SharePoint moderno onde moderno tem uma hierarquia de site plana simplificada. Isso tem simplificado navegação com uma hierarquia simplificada que eliminou problemas de desempenho relacionados à navegação.</span><span class="sxs-lookup"><span data-stu-id="e6442-p101">That design has changed with the introduction of Modern SharePoint sites where Modern has a simplified flattened site hierarchy. This has simplified navigation with a simplified hierarchy that has eliminated performance issues related to navigation.</span></span>
  
<span data-ttu-id="e6442-p102">Há duas opções principais de navegação da caixa no SharePoint, bem como uma terceira, abordagem personalizada e orientado por pesquisa. Como alternativa, um quarto e opção bastante popular é criar um provedor de navegação personalizado. Analise [as soluções de navegação para portais SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) para obter orientações sobre um provedor de navegação personalizado.</span><span class="sxs-lookup"><span data-stu-id="e6442-p102">There are two main out-of-the-box navigation options in SharePoint as well as a third, custom, search-driven approach. Alternatively, a fourth and fairly popular option is to build a Custom Navigation Provider. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) for guidance on a Custom navigation provider.</span></span> 
  
<span data-ttu-id="e6442-114">Cada opção tem vantagens e desvantagens, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6442-114">Each option has pros and cons as outlined in the following table.</span></span>
  
|<span data-ttu-id="e6442-115">**Navegação estrutural**</span><span class="sxs-lookup"><span data-stu-id="e6442-115">**Structural navigation**</span></span>|<span data-ttu-id="e6442-116">**Navegação gerenciada**</span><span class="sxs-lookup"><span data-stu-id="e6442-116">**Managed navigation**</span></span>|<span data-ttu-id="e6442-117">**Navegação orientada por pesquisa**</span><span class="sxs-lookup"><span data-stu-id="e6442-117">**Search-driven navigation**</span></span>||<span data-ttu-id="e6442-118">**Provedor de navegação personalizada**</span><span class="sxs-lookup"><span data-stu-id="e6442-118">**Custom Navigation Provider**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="e6442-119">Vantagens:</span><span class="sxs-lookup"><span data-stu-id="e6442-119">Pros:</span></span>  <br/>  <span data-ttu-id="e6442-120">Fácil de configurar</span><span class="sxs-lookup"><span data-stu-id="e6442-120">Easy to configure</span></span>  <br/>  <span data-ttu-id="e6442-121">Remoção de segurança</span><span class="sxs-lookup"><span data-stu-id="e6442-121">Security-trimmed</span></span>  <br/>  <span data-ttu-id="e6442-122">Atualização automática quando os sites são adicionados</span><span class="sxs-lookup"><span data-stu-id="e6442-122">Automatically updates as sites are added</span></span>  <br/> | <span data-ttu-id="e6442-123">Vantagens:</span><span class="sxs-lookup"><span data-stu-id="e6442-123">Pros:</span></span>  <br/>  <span data-ttu-id="e6442-124">Fácil de manter</span><span class="sxs-lookup"><span data-stu-id="e6442-124">Easy to maintain</span></span>  <br/>  <span data-ttu-id="e6442-125">Opção recomendada</span><span class="sxs-lookup"><span data-stu-id="e6442-125">Recommended option</span></span>  <br/> | <span data-ttu-id="e6442-126">Vantagens:</span><span class="sxs-lookup"><span data-stu-id="e6442-126">Pros:</span></span>  <br/>  <span data-ttu-id="e6442-127">Remoção de segurança</span><span class="sxs-lookup"><span data-stu-id="e6442-127">Security-trimmed</span></span>  <br/>  <span data-ttu-id="e6442-128">Atualização automática quando os sites são adicionados</span><span class="sxs-lookup"><span data-stu-id="e6442-128">Automatically updates as sites are added</span></span>  <br/>  <span data-ttu-id="e6442-129">Tempo de carregamento rápido e estrutura de navegação armazenada em cache localmente</span><span class="sxs-lookup"><span data-stu-id="e6442-129">Fast loading time and locally cached navigation structure</span></span>  <br/> || <span data-ttu-id="e6442-130">Prós:</span><span class="sxs-lookup"><span data-stu-id="e6442-130">Pros:</span></span>  <br/>    <br/>  <span data-ttu-id="e6442-131">Escolha mais larga / opções disponíveis</span><span class="sxs-lookup"><span data-stu-id="e6442-131">Wider choice / options available</span></span>  <br/>  <span data-ttu-id="e6442-132">Carregando Fast quando o cache é usada corretamente</span><span class="sxs-lookup"><span data-stu-id="e6442-132">Fast loading when caching is used correctly</span></span>  <br/> |
| <span data-ttu-id="e6442-133">Desvantagens:</span><span class="sxs-lookup"><span data-stu-id="e6442-133">Cons:</span></span>  <br/> <span data-ttu-id="e6442-134">**Não recomendado**</span><span class="sxs-lookup"><span data-stu-id="e6442-134">**Not recommended**</span></span> <br/> <span data-ttu-id="e6442-135">**Impacto sobre o desempenho**</span><span class="sxs-lookup"><span data-stu-id="e6442-135">**Impacts performance**</span></span> <br/> | <span data-ttu-id="e6442-136">Desvantagens:</span><span class="sxs-lookup"><span data-stu-id="e6442-136">Cons:</span></span>  <br/>  <span data-ttu-id="e6442-137">Não é atualizado automaticamente para refletir a estrutura do site</span><span class="sxs-lookup"><span data-stu-id="e6442-137">Not automatically updated to reflect site structure</span></span>  <br/>  <span data-ttu-id="e6442-138">Impacto sobre o desempenho se a filtragem de segurança está habilitada</span><span class="sxs-lookup"><span data-stu-id="e6442-138">Impacts performance if security trimming is enabled</span></span>  <br/> | <span data-ttu-id="e6442-139">Desvantagens:</span><span class="sxs-lookup"><span data-stu-id="e6442-139">Cons:</span></span>  <br/>  <span data-ttu-id="e6442-140">Não possui capacidade de ordenar facilmente os sites</span><span class="sxs-lookup"><span data-stu-id="e6442-140">No ability to easily order sites</span></span>  <br/>  <span data-ttu-id="e6442-141">Requer a personalização da página mestra (habilidades técnicas necessárias)</span><span class="sxs-lookup"><span data-stu-id="e6442-141">Requires customization of the master page (technical skills required)</span></span>  <br/> || <span data-ttu-id="e6442-142">Desvantagens:</span><span class="sxs-lookup"><span data-stu-id="e6442-142">Cons:</span></span>  <br/>  <span data-ttu-id="e6442-143">Desenvolvimento personalizado é necessário</span><span class="sxs-lookup"><span data-stu-id="e6442-143">Custom development is required</span></span>  <br/>  <span data-ttu-id="e6442-144">Fonte de dados externa / cache armazenados é necessária Azure ex.:</span><span class="sxs-lookup"><span data-stu-id="e6442-144">External data source / cache stored is needed e.g. Azure</span></span>  <br/> |
   
<span data-ttu-id="e6442-p103">A opção mais adequada ao seu site dependerá em seus requisitos de site e em sua capacidade técnica. Se você estiver familiarizado com o uso de uma página mestra personalizada e alguns recursos da organização para manter as alterações que podem ocorrer na página mestra padrão para o SharePoint Online, a opção orientado por pesquisa produzirá a melhor experiência de usuário. Se desejar que um simple intermediário entre a navegação estrutural de-de-imediata e pesquisa, o painel de navegação gerenciada é uma boa opção. A opção de navegação gerenciada pode ser mantida por meio de configuração, não envolvem arquivos de personalização de código e é consideravelmente menor do que a navegação estrutural da caixa.</span><span class="sxs-lookup"><span data-stu-id="e6442-p103">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the search-driven option will produce the best user experience. If you want a simple middle ground between the out-of-the-box structural navigation and search, then the managed navigation is a very good option. The managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than the out-of-the-box structural navigation.</span></span>
  
<span data-ttu-id="e6442-p104">Simplificando a estrutura geral do seu Portal clássico muito semelhante moderno, ajuda com desempenho e escala também gerais. O que isso significa é que, em vez de um único conjunto de sites com centenas / milhares de sites (subwebs), uma abordagem melhor é terá muitos conjuntos de sites com subsites pouquíssimas (subwebs).</span><span class="sxs-lookup"><span data-stu-id="e6442-p104">Simplifying the overall structure of your Classic Portal much like Modern, helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds / thousands of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>
  
<span data-ttu-id="e6442-151">Isso fornece opções adicionais de dimensionamento no serviço, evita colocar todo o conteúdo em um banco de dados grande e basicamente permite maior flexibilidade para a navegação e mais importante de segurança.</span><span class="sxs-lookup"><span data-stu-id="e6442-151">This provides additional scaling options in the service, avoids putting all content into one big database and ultimately allows greater flexibility for navigation and more importantly security.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="e6442-152">Usando a navegação estrutural no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e6442-152">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="e6442-p105">Esta é a navegação da caixa usada por padrão e é a solução mais simples, mas como tal, tem uma compensação de desempenho caro. Ele não requer qualquer personalização e um usuário não técnico também facilmente pode adicionar itens, ocultar itens e gerenciar o painel de navegação da página Configurações. Isso é, no entanto, também true para a navegação gerenciada então, é recomendável usar a navegação gerenciada como que pode também ser facilmente gerenciados e controlados também.</span><span class="sxs-lookup"><span data-stu-id="e6442-p105">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well.</span></span>
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="e6442-156">Ativando a navegação estrutural no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e6442-156">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="e6442-p106">Para ilustrar como o desempenho em uma solução do SharePoint Online standard com navegação estrutural e show subsites opção ativada. A seguir é uma captura de tela configurações encontradas na página **Configurações do Site** \> **navegação**.</span><span class="sxs-lookup"><span data-stu-id="e6442-p106">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screen shot settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Captura de tela mostrando subsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="e6442-160">Analisando o desempenho da navegação estrutural no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e6442-160">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="e6442-161">Para analisar o desempenho de uma página do SharePoint use a guia **Rede** das ferramentas do desenvolvedor F12 no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e6442-161">To analyze the performance of a SharePoint page use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Captura de tela mostrando a guia Rede das ferramentas de desenvolvimento F12](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
<span data-ttu-id="e6442-163">Na guia **Rede**, clique na página .aspx que está sendo carregada e, em seguida, clique na guia **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="e6442-163">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span> 
  
![Captura de tela mostrando a guia de detalhes](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
<span data-ttu-id="e6442-165">Clique em **Cabeçalhos de resposta**.</span><span class="sxs-lookup"><span data-stu-id="e6442-165">Click **Response headers**.</span></span>
  
![Captura de tela da guia Detalhes](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
<span data-ttu-id="e6442-p107">O SharePoint retorna algumas informações de diagnóstico úteis em seus cabeçalhos de resposta. Uma das mais úteis é **SPRequestDuration** que é o valor, em milissegundos, do tempo que uma solicitação levou para ser processada no servidor.</span><span class="sxs-lookup"><span data-stu-id="e6442-p107">SharePoint returns some useful diagnostic information in its response headers. One of the most useful is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> 
  
<span data-ttu-id="e6442-p108">**Mostrar subsites** de captura de tela a seguir está desmarcada para navegação estrutural. Isso significa que há somente o link de conjunto de sites, no painel de navegação global:</span><span class="sxs-lookup"><span data-stu-id="e6442-p108">In the following screen shot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span> 
  
![Captura de tela mostrando tempos de carga como duração da solicitação](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
<span data-ttu-id="e6442-p109">A chave **SPRequestDuration** tem um valor de 245 milissegundos. Isso representa o tempo necessário para retornar a solicitação. Como há somente um item de navegação no site, este é um parâmetro de comparação bom para como o SharePoint Online executa sem navegação pesada. A próxima captura de tela mostra como a adição de subsites afeta essa chave.</span><span class="sxs-lookup"><span data-stu-id="e6442-p109">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span> 
  
![Captura de tela mostrando uma duração de solicitação de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
<span data-ttu-id="e6442-177">Adicionar os subsites aumentou significativamente o tempo necessário para retornar a solicitação de página.</span><span class="sxs-lookup"><span data-stu-id="e6442-177">Adding the subsites has significantly increased the time it takes to return the page request.</span></span>
  
<span data-ttu-id="e6442-178">As vantagens de usar a navegação estruturada regular é que você pode facilmente organizar a ordem, ocultar sites, adicione páginas, os resultados são aparada de segurança e tenha de páginas mestras com suporte usadas no SharePoint Online não se desviado.</span><span class="sxs-lookup"><span data-stu-id="e6442-178">The advantages of using the regular structured navigation is that you can easily organize the order, hide sites, add pages, the results are security-trimmed, and you are not deviating from the supported master pages used in SharePoint Online.</span></span>
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a><span data-ttu-id="e6442-179">Usando a navegação gerenciada e metadados gerenciados no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e6442-179">Using managed navigation and managed metadata in SharePoint Online</span></span>

<span data-ttu-id="e6442-180">A navegação gerenciada é outra opção integrada que você pode usar para recriar o mesmo tipo de funcionalidade que a navegação estrutural.</span><span class="sxs-lookup"><span data-stu-id="e6442-180">Managed navigation is another out-of-the-box option that you can use to recreate the same sort of functionality as structural navigation.</span></span>
  
<span data-ttu-id="e6442-p110">A vantagem de usar metadados gerenciados é o que é muito mais rápido para recuperar os dados é diferente usando o conteúdo por consulta para criar a navegação do site. Embora seja que muito mais rapidez não há segurança trim os resultados por isso se um usuário não tem acesso a um site específico, o link ainda mostrará mas levará a uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="e6442-p110">The advantage of using managed metadata is that it is much faster to retrieve the data than using content by query to build the site navigation. Although it is much faster there is no way to security trim the results so if a user doesn't have access to a given site, the link will still show but will lead to an error message.</span></span>
  
 <span data-ttu-id="e6442-183">**Como implementar a navegação gerenciada e os resultados**</span><span class="sxs-lookup"><span data-stu-id="e6442-183">**How to implement managed navigation and the results**</span></span>
  
<span data-ttu-id="e6442-184">Há vários artigos no TechNet sobre os detalhes da navegação gerenciada, por exemplo, consulte [Visão geral da navegação gerenciada no SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span><span class="sxs-lookup"><span data-stu-id="e6442-184">There are several articles on TechNet about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span></span>
  
<span data-ttu-id="e6442-p111">Para implementar a navegação gerenciada são necessárias permissões do administrador do repositório de termos. Ao configurar termos com URLs que coincidem com a estrutura de um conjunto de sites, a navegação gerenciada pode ser usada para substituir a navegação estrutural. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e6442-p111">In order to implement managed navigation, you need to have term store administrator permissions. By setting up terms with URLs that match the structure of a site collection, managed navigation can be used to replace structural navigation. For example:</span></span>
  
![Captura de tela do exemplo de Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
<span data-ttu-id="e6442-189">O exemplo a seguir mostra o desempenho da navegação complexa usando a navegação gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e6442-189">The following example shows the performance of the complex navigation using managed navigation.</span></span>
  
![Captura de tela do exemplo de SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
<span data-ttu-id="e6442-191">Usar a navegação gerenciada consistentemente melhora o desempenho em comparação com a abordagem de navegação estrutural de consulta por conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e6442-191">Using managed navigation consistently improves performance compared to the content by query structural navigation approach.</span></span>
  
## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="e6442-192">Usando o script do lado do cliente orientado por pesquisa</span><span class="sxs-lookup"><span data-stu-id="e6442-192">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="e6442-p112">Utilizando a pesquisa, você pode aproveitar os índices que são criados na tela de fundo usando o rastreamento contínuo. Isso significa que não existem consultas de conteúdo pesadas. Os resultados da pesquisa são retirados do índice de pesquisa e passam pela remoção de segurança. Isso é mais rápido do que usar consultas de conteúdo normais. Usar a pesquisa para a navegação estrutural, especialmente se tiver uma estrutura de site complexa, irá acelerar consideravelmente o tempo de carregamento de página. A principal vantagem desta navegação sobre a gerenciada é que você se beneficia da filtragem de segurança.</span><span class="sxs-lookup"><span data-stu-id="e6442-p112">Using search you can leverage the indexes that are built up in the background using continuous crawl. This means there are no heavy content queries. The search results are pulled from the search index and the results are security-trimmed. This is faster than using regular content queries. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>
  
<span data-ttu-id="e6442-p113">Essa abordagem envolve a criação de uma página mestra personalizada e a substituição do código de navegação integrado com HTML personalizado. Siga este procedimento para substituir o código de navegação no arquivo seattle.html.</span><span class="sxs-lookup"><span data-stu-id="e6442-p113">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure to replace the navigation code in the file seattle.html.</span></span>
  
<span data-ttu-id="e6442-201">Neste exemplo, você abrir o arquivo seattle.html e substitua o elemento todo **id = "DeltaTopNavigation"** com o código HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="e6442-201">In this example, you will open the seattle.html file and replace the whole element **id="DeltaTopNavigation"** with the custom HTML code.</span></span> 
  
 <span data-ttu-id="e6442-202">**Exemplo: Para substituir o código de navegação integrado em uma página mestra**</span><span class="sxs-lookup"><span data-stu-id="e6442-202">**Example: To replace the out-of-the-box navigation code in a master page**</span></span>
  
1. <span data-ttu-id="e6442-203">Navegue até a página **Configurações do Site**.</span><span class="sxs-lookup"><span data-stu-id="e6442-203">Navigate to the **Site Settings** page.</span></span> 
    
2. <span data-ttu-id="e6442-204">Abra a galeria de páginas mestras clicando em **Páginas Mestras**.</span><span class="sxs-lookup"><span data-stu-id="e6442-204">Open the master page gallery by clicking **Master Pages**.</span></span>
    
3. <span data-ttu-id="e6442-205">Aqui você pode navegar pela biblioteca e baixar o arquivo **seattle.master**.</span><span class="sxs-lookup"><span data-stu-id="e6442-205">From here you can navigate through the library and download the file **seattle.master**.</span></span>
    
4. <span data-ttu-id="e6442-206">Edite o código usando um editor de texto e exclua o bloco de código na captura de tela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6442-206">Edit the code using a text editor and delete the code block in the following screen shot.</span></span>
    
    ![Captura de tela do código DeltaTopNavigation para exclusão](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. <span data-ttu-id="e6442-208">Remover o código entre o \<SharePoint:AjaxDelta id = "DeltaTopNavigation"\> e \<\SharePoint:AjaxDelta\> tags e substituí-lo com o trecho a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6442-208">Remove the code between the \<SharePoint:AjaxDelta id="DeltaTopNavigation"\> and \<\SharePoint:AjaxDelta\> tags and replace it with the following snippet:</span></span>
    
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

6. <span data-ttu-id="e6442-p114">Substituir a URL no carregamento da imagem marca âncora no início, com um link para uma imagem de carregamento em seu conjunto de sites. Depois de fazer as alterações, renomeie o arquivo e, em seguida, carregue-o para a Galeria de páginas mestras. Isso gerará um novo arquivo. master.</span><span class="sxs-lookup"><span data-stu-id="e6442-p114">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span>
    
7. <span data-ttu-id="e6442-p115">Este HTML é a marcação básica que será preenchida pelos resultados de pesquisa retornados pelo código JavaScript. Você precisará editar o código a seguir para alterar o valor para o `var root = "site collection URL"` conforme demonstrado no seguinte trecho:</span><span class="sxs-lookup"><span data-stu-id="e6442-p115">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the following code to change the value for the  `var root = "site collection URL"` as demonstrated in the following snippet:</span></span> 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

    <span data-ttu-id="e6442-214">O arquivo JavaScript inteiro é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e6442-214">The entire JavaScript file is as follows:</span></span>
    
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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     <span data-ttu-id="e6442-215">$("li.level1").mouseover (função () {</span><span class="sxs-lookup"><span data-stu-id="e6442-215">$("li.level1").mouseover(function () {</span></span> 
  
<span data-ttu-id="e6442-216">posição de var = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="e6442-216">var position = $(this).position();</span></span>
  
<span data-ttu-id="e6442-217">$(this).find("ul.level2").css ({largura: 100, esquerda: position.left + 10, top: 50});</span><span class="sxs-lookup"><span data-stu-id="e6442-217">$(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });</span></span>
    
     }) 
  
<span data-ttu-id="e6442-218">.Mouseout (função () {</span><span class="sxs-lookup"><span data-stu-id="e6442-218">.mouseout(function () {</span></span>
  
<span data-ttu-id="e6442-219">$(this).find("ul.level2").css ({esquerdo:-99999, superior: 0});</span><span class="sxs-lookup"><span data-stu-id="e6442-219">$(this).find("ul.level2").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="e6442-220">});</span><span class="sxs-lookup"><span data-stu-id="e6442-220"></span></span>
  
<span data-ttu-id="e6442-221">$("li.level2").mouseover (função () {</span><span class="sxs-lookup"><span data-stu-id="e6442-221">$("li.level2").mouseover(function () {</span></span>
  
<span data-ttu-id="e6442-222">posição de var = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="e6442-222">var position = $(this).position();</span></span>
  
<span data-ttu-id="e6442-223">console.log(JSON.stringify(Position));</span><span class="sxs-lookup"><span data-stu-id="e6442-223">console.log(JSON.stringify(position));</span></span>
  
<span data-ttu-id="e6442-224">$(this).find("ul.level3").css ({largura: 100, esquerda: position.left + 95, top: position.top});</span><span class="sxs-lookup"><span data-stu-id="e6442-224">$(this).find("ul.level3").css({ width: 100, left: position.left + 95, top: position.top});</span></span>
    
     }) 
  
<span data-ttu-id="e6442-225">.Mouseout (função () {</span><span class="sxs-lookup"><span data-stu-id="e6442-225">.mouseout(function () {</span></span>
  
<span data-ttu-id="e6442-226">$(this).find("ul.level3").css ({esquerdo:-99999, superior: 0});</span><span class="sxs-lookup"><span data-stu-id="e6442-226">$(this).find("ul.level3").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="e6442-227">});</span><span class="sxs-lookup"><span data-stu-id="e6442-227"></span></span>
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. <span data-ttu-id="e6442-p116">Em seguida, os resultados são atribuídos à matriz **[self.nodes]** e uma hierarquia é compilada sem os objetos usando linq.js atribuindo a saída para uma matriz **[self.heirarchy]**. Esta matriz é o objeto que é vinculado ao HTML. Isso é feito na função **[toggleView()]** , passando o objeto self para a função **[ko.applyBinding()]** . Em seguida, isso faz a matriz de hierarquia deve ser vinculado a seguinte HTML:</span><span class="sxs-lookup"><span data-stu-id="e6442-p116">Next, the results are assigned to the **[self.nodes]** array and a hierarchy is built out of the objects using linq.js assigning the output to an array **[self.heirarchy]**. This array is the object that is bound to the HTML. This is done in the **[toggleView()]** function by passing the self object to the **[ko.applyBinding()]** function. This then causes the hierarchy array to be bound to the following HTML:</span></span> 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    <span data-ttu-id="e6442-232">Finalmente, os manipuladores de eventos para **[mouseenter]** e **[mouseexit]** são adicionados para a navegação de nível superior para lidar com os menus suspensos subsite que é feita na função **[addEventsToElements()]** .</span><span class="sxs-lookup"><span data-stu-id="e6442-232">Finally, the event handlers for **[mouseenter]** and **[mouseexit]** are added to the top-level navigation to handle the subsite drop-down menus which is done in the **[addEventsToElements()]** function.</span></span> 
    
    <span data-ttu-id="e6442-233">Os resultados do painel de navegação podem ser vistos na captura de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="e6442-233">The results of the navigation can be seen in the screen shot below:</span></span>
    
    ![Captura de tela de resultados de navegação](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    <span data-ttu-id="e6442-235">No nosso exemplo de navegação complexa, uma página em branco carregada sem o cache local mostra que o tempo gasto no servidor foi reduzido do parâmetro de comparação da navegação estrutural para obter um resultado semelhante, como a abordagem de navegação gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e6442-235">In our complex navigation example a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>
    
    ![Captura de tela de SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    <span data-ttu-id="e6442-237">Uma grande vantagem dessa abordagem é que ao usar o armazenamento local HTML5, a navegação é armazenada localmente para os usuários na próxima vez em que carregarem a página.</span><span class="sxs-lookup"><span data-stu-id="e6442-237">One major benefit of this approach is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span>
    
<span data-ttu-id="e6442-p117">Recebemos importantes melhorias de desempenho usando a API de pesquisa para a navegação estrutural. No entanto, são necessários alguns recursos técnicos para executar e personalizar essa funcionalidade. No exemplo de implementação, os sites são ordenados da mesma forma que a navegação estrutural integrada; em ordem alfabética. Será mais complicado de desenvolver e manter se você quiser evitar essa ordem. Além disso, esta abordagem exige que você se desvie das páginas mestras suportadas. Se a página mestra personalizada não for mantida, seu site perderá as atualizações e as melhorias que a Microsoft faz nas páginas mestras.</span><span class="sxs-lookup"><span data-stu-id="e6442-p117">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality. In the example implementation, the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>
  
<span data-ttu-id="e6442-243">O código acima tem as seguintes dependências:</span><span class="sxs-lookup"><span data-stu-id="e6442-243">The above code has the following dependencies:</span></span>
  
- <span data-ttu-id="e6442-244">jQuery-[http://jquery.com/](http://jquery.com/)</span><span class="sxs-lookup"><span data-stu-id="e6442-244">jQuery - [http://jquery.com/](http://jquery.com/)</span></span>
    
- <span data-ttu-id="e6442-245">KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)</span><span class="sxs-lookup"><span data-stu-id="e6442-245">KnockoutJS - [http://knockoutjs.com/](http://knockoutjs.com/)</span></span>
    
- <span data-ttu-id="e6442-246">LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), ou [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span><span class="sxs-lookup"><span data-stu-id="e6442-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), or [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span></span>
    
<span data-ttu-id="e6442-p118">A versão atual do LinqJS não contém o método ByHierarchy usado no código acima e interromperá o código de navegação. Para corrigir esse problema, adicione o seguinte método ao arquivo Linq.js antes da linha "nivelamento: funcionar ()".</span><span class="sxs-lookup"><span data-stu-id="e6442-p118">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line "Flatten: function ()".</span></span>
  
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


