---
title: Configurar a pesquisa do OneDrive para Business Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba mais sobre como configurar a pesquisa em um ambiente multi-geo.
ms.openlocfilehash: 5aa1e9eb189e00dbed8f575e88046b661341bf52
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="e0eff-103">Configurar a pesquisa do OneDrive para Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="e0eff-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="e0eff-104">Em um ambiente de Multi-Geo SharePoint Online (SPO), uma organização pode ter um locatário do Office 365, mas armazene seu conteúdo do SharePoint em várias localizações geográficas - um local central e um ou mais locais geo de satélite.</span><span class="sxs-lookup"><span data-stu-id="e0eff-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="e0eff-p101">Cada localização geográfica tem seus próprios índice de pesquisa e o Centro de pesquisa. Quando um usuário procura, a consulta é leque exibindo para todos os índices e resultados retornados são mesclados.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="e0eff-p102">Por exemplo, um usuário em um único local geo pode pesquisar para conteúdo armazenado em outro local geo ou conteúdo em um site do SharePoint que é restrita a um local diferente geo. Se o usuário tem acesso a esse conteúdo, a pesquisa mostrará o resultado.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="e0eff-109">Qual a pesquisa funciona de clientes em um ambiente Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="e0eff-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="e0eff-110">Esses clientes podem retornar resultados de todos os locais de geo:</span><span class="sxs-lookup"><span data-stu-id="e0eff-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="e0eff-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="e0eff-111">OneDrive for Business</span></span>

-   <span data-ttu-id="e0eff-112">Delve</span><span class="sxs-lookup"><span data-stu-id="e0eff-112">Delve</span></span>

-   <span data-ttu-id="e0eff-113">Na home page do SharePoint</span><span class="sxs-lookup"><span data-stu-id="e0eff-113">The SharePoint home page</span></span>

-   <span data-ttu-id="e0eff-114">Centro de pesquisa</span><span class="sxs-lookup"><span data-stu-id="e0eff-114">The Search Center</span></span>

-   <span data-ttu-id="e0eff-115">Aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint</span><span class="sxs-lookup"><span data-stu-id="e0eff-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="e0eff-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="e0eff-116">OneDrive for Business</span></span>

<span data-ttu-id="e0eff-117">Assim que o ambiente de Multi-Geo tiver sido configurado, os usuários de pesquisa no OneDrive obter resultados de todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="e0eff-118">Delve</span><span class="sxs-lookup"><span data-stu-id="e0eff-118">Delve</span></span>

<span data-ttu-id="e0eff-119">Assim que o ambiente de Multi-Geo tiver sido configurado, os usuários de pesquisa no Delve obter resultados de todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="e0eff-p103">O feed Delve e o cartão de perfil mostram apenas as visualizações dos arquivos que são armazenados no local **central** . Para arquivos que são armazenados nos locais de geo satélite, o ícone do tipo de arquivo é mostrado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="e0eff-122">Na home page do SharePoint</span><span class="sxs-lookup"><span data-stu-id="e0eff-122">The SharePoint home page</span></span>

<span data-ttu-id="e0eff-p104">Assim que o ambiente de Multi-Geo tiver sido configurado, os usuários verão notícias, sites recentes e visitados vários locais geo na sua home page do SharePoint. Se eles usarem a caixa de pesquisa na home page do SharePoint, eles obterá resultados mesclados de vários locais geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="e0eff-125">Centro de pesquisa</span><span class="sxs-lookup"><span data-stu-id="e0eff-125">The Search Center</span></span>

<span data-ttu-id="e0eff-p105">Após o Multi-Geo ambiente tiver sido definida para cima, cada centro de pesquisa continua para mostrar somente os resultados de sua próprias local geo. Os administradores devem [alterar as configurações de cada centro de pesquisa](#_Set_up_a_1) para obter resultados de todos os locais de geo. Depois disso, os usuários que pesquise no Centro de pesquisa obtém resultados de todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="e0eff-129">Aplicativos de pesquisa personalizados</span><span class="sxs-lookup"><span data-stu-id="e0eff-129">Custom search applications</span></span>

<span data-ttu-id="e0eff-p106">Normalmente, aplicativos de pesquisa personalizados interagem com os índices de pesquisa usando as APIs do REST de pesquisa do SharePoint existente. Para obter resultados de locais de geo todas ou algumas, o aplicativo deve [chamar a API e incluir os novos parâmetros de consulta Multi-Geo](#_Get_custom_search) na solicitação. Isso dispara um ventilador de consulta para todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="e0eff-133">O que é diferente sobre a pesquisa em um ambiente Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="e0eff-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="e0eff-134">Alguns recursos de pesquisa que você pode estar familiarizado com, funcionam de modo diferente em um ambiente Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e0eff-135"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="e0eff-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="e0eff-136"><strong>Como funciona</strong></span><span class="sxs-lookup"><span data-stu-id="e0eff-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="e0eff-137"><strong>Solução alternativa</strong></span><span class="sxs-lookup"><span data-stu-id="e0eff-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e0eff-138">Resultados promovidos</span><span class="sxs-lookup"><span data-stu-id="e0eff-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="e0eff-p107">Você pode criar regras de consulta com resultados promovidos em diferentes níveis: para o locatário todo, para um conjunto de sites ou para um site. Em um ambiente de Multi-Geo, defina resultados promovidos no nível de <strong>locatário</strong> , se você deseja promover os resultados para os centros de pesquisa em <strong>todos os</strong> locais de geo. Se você <strong>só</strong> deseja promover resultados no Centro de pesquisa que está no local do conjunto de sites ou site geo, defina os resultados no nível do <strong>conjunto de sites</strong> ou <strong>site</strong> .</span><span class="sxs-lookup"><span data-stu-id="e0eff-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="e0eff-142">Se você não precisa diferentes resultados promovidos por geo local, por exemplo diferentes regras para viajando, é recomendável definindo promovidos resultados a nível de locatário.</span><span class="sxs-lookup"><span data-stu-id="e0eff-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e0eff-143">Refinadores de pesquisa</span><span class="sxs-lookup"><span data-stu-id="e0eff-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="e0eff-p108">Pesquisa retorna refinadores de todos os locais de um inquilino geo e, em seguida, agrega-los. A agregação de lista segura é um melhor esforço, que significa que as contagens de refinador podem não ser 100% preciso. Para a maioria dos cenários orientado por pesquisa, essa precisão é suficiente.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="e0eff-147">Para aplicativos orientado por pesquisa que dependam completude refinador, consulta cada local geo independentemente sem usar fan-out de Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="e0eff-148">Pesquisa de multi-Geo não oferece suporte a bucketing dinâmico para refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="e0eff-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="e0eff-149">Use o <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">parâmetro "Discretize"</a> para refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="e0eff-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e0eff-150">IDs de documento</span><span class="sxs-lookup"><span data-stu-id="e0eff-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="e0eff-151">Se você estiver desenvolvendo um aplicativo orientado por pesquisa que depende de IDs de documento, observe que as IDs de documento em um ambiente Multi-Geo não são exclusivas entre localidades geo, eles são exclusivos em cada local geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="e0eff-p109">Adicionamos uma coluna que identifica a localização geográfica. Use essa coluna para atingir exclusividade. Essa coluna é denominada "GeoLocationSource".</span><span class="sxs-lookup"><span data-stu-id="e0eff-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e0eff-155">Número de resultados</span><span class="sxs-lookup"><span data-stu-id="e0eff-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="e0eff-156">A página de resultados de pesquisa mostra os resultados combinados nos locais geo, mas não é possível em uma página acima de 500 resultados.</span><span class="sxs-lookup"><span data-stu-id="e0eff-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="e0eff-157">O que não é suportado para pesquisa em um ambiente Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="e0eff-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="e0eff-158">Alguns dos recursos de pesquisa que você pode estar familiarizado com, não são suportados em um ambiente Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e0eff-159"><strong>Recurso de pesquisa</strong></span><span class="sxs-lookup"><span data-stu-id="e0eff-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="e0eff-160"><strong>Observação</strong></span><span class="sxs-lookup"><span data-stu-id="e0eff-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e0eff-161">Autenticação de aplicativo</span><span class="sxs-lookup"><span data-stu-id="e0eff-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="e0eff-162">Autenticação somente App (acesso privilegiado dos serviços) não é compatível com Multi-Geo pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e0eff-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e0eff-163">Usuários convidados</span><span class="sxs-lookup"><span data-stu-id="e0eff-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="e0eff-164">Usuários convidados somente obtém resultados do local geo que eles estiver pesquisando de.</span><span class="sxs-lookup"><span data-stu-id="e0eff-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="e0eff-165">Como a pesquisa faz trabalhar em um ambiente de Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="e0eff-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="e0eff-166">**Todos** os clientes de pesquisa usam as APIs do REST de pesquisa do SharePoint existentes para interagir com os índices de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e0eff-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="e0eff-167">Um cliente de pesquisa chama o ponto de extremidade do REST de pesquisa com a propriedade de consulta EnableMultiGeoSearch = true.</span><span class="sxs-lookup"><span data-stu-id="e0eff-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="e0eff-168">A consulta é enviada para todos os locais de geo no inquilino.</span><span class="sxs-lookup"><span data-stu-id="e0eff-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="e0eff-169">Resultados de pesquisa de cada local geo são mesclados e classificados.</span><span class="sxs-lookup"><span data-stu-id="e0eff-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="e0eff-170">O cliente obtém os resultados de pesquisa unificada.</span><span class="sxs-lookup"><span data-stu-id="e0eff-170">The client gets unified search results.</span></span>



<span data-ttu-id="e0eff-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Observe que não podemos mesclar os resultados da pesquisa até que recebemos os resultados de todos os locais de geo. Isso significa que as pesquisas de Multi-Geo tem latência adicional em comparação com pesquisas em um ambiente com apenas um geo local.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="e0eff-173">Obtenha um centro de pesquisa para mostrar os resultados de todos os locais de geo</span><span class="sxs-lookup"><span data-stu-id="e0eff-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="e0eff-174">Cada centro de pesquisa tem várias verticais e você precisará configurar cada vertical individualmente.</span><span class="sxs-lookup"><span data-stu-id="e0eff-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="e0eff-175">Certifique-se de que você execute essas etapas com uma conta que tenha permissão para editar a página de resultados de pesquisa e a Web Part de resultados de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e0eff-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="e0eff-176">Navegue até a página de resultados de pesquisa (consulte a [lista](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de pesquisa de páginas de resultados)</span><span class="sxs-lookup"><span data-stu-id="e0eff-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="e0eff-p111">Selecione a vertical para configurar, clique em **configurações do** ícone de engrenagem no canto superior direito e, em seguida, clique em **Editar página**. A página de resultados de pesquisa é aberta no modo de edição.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="e0eff-p112">Na Web Part de resultados da pesquisa, mova o ponteiro para o superior, no canto direito da Web Part, clique na seta e, em seguida, clique em **Editar Web Part** no menu. O painel de ferramentas da Web Part de resultados de pesquisa será aberto sob a faixa de opções na parte superior direita da página.![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="e0eff-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="e0eff-181">No painel de ferramentas da Web Part, na seção **configurações** , em **configurações de controle de resultados**, selecione **Mostrar Multi-Geo resultados** para obter a Web Part de resultados de pesquisa para mostrar os resultados de todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="e0eff-182">Clique em **Okey** para salvar suas alterações e fechar o painel de ferramentas da Web Part.</span><span class="sxs-lookup"><span data-stu-id="e0eff-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="e0eff-183">Verifique suas alterações para a Web Part de resultados de pesquisa clicando em **Check-In** na guia página do menu principal.</span><span class="sxs-lookup"><span data-stu-id="e0eff-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="e0eff-184">Publique as alterações usando o link fornecido na nota na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="e0eff-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="e0eff-185">Obtenha os aplicativos de pesquisa personalizados para mostrar os resultados de alguns ou todos os locais de geo</span><span class="sxs-lookup"><span data-stu-id="e0eff-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="e0eff-p113">Aplicativos de pesquisa personalizados obtém resultados de locais de geo todas ou algumas, especificando-se os parâmetros de consulta com a solicitação para a API do REST de pesquisa do SharePoint. Dependendo dos parâmetros de consulta, a consulta é leque exibindo para todos os locais de geo ou para alguns locais geo. Por exemplo, se você precisar apenas consultar um subconjunto dos locais geo encontrar informações relevantes, você pode controlar o ventilador check-out para apenas elas. Se a solicitação tiver êxito, a API do REST de pesquisa do SharePoint retorna dados de resposta.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="e0eff-190">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="e0eff-190">Query parameters</span></span>

<span data-ttu-id="e0eff-p114">EnableMultiGeoSearch - este é um valor Boolean que especifica se a consulta deverá ser leque exibindo para os índices de outros locais geo do inquilino Multi-Geo. Defini-la como **true** para espalham consulta; **false** para não espalham a consulta. O valor padrão é **false**. Se esse parâmetro não for incluído, a consulta é **não** leque exibindo a outros locais geo. Se você usar o parâmetro em um ambiente que não seja Multi-Geo, o parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="e0eff-p115">Tipo_de_cliente - isso é uma cadeia de caracteres. Insira um nome exclusivo do cliente para cada aplicativo de pesquisa. Se esse parâmetro não for incluído, a consulta é **não** leque exibindo a outros locais geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="e0eff-p116">MultiGeoSearchConfiguration - esta é uma lista opcional de qual geo locais in a Multi-Geo locatários para espalham a consulta para quando **EnableMultiGeoSearch** for **verdadeira**. Se você não incluir esse parâmetro ou deixe em branco, a consulta é leque exibindo a todos os locais de geo. Para cada local geo, insira os itens a seguir, no formato JSON:</span><span class="sxs-lookup"><span data-stu-id="e0eff-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e0eff-202">Item</span><span class="sxs-lookup"><span data-stu-id="e0eff-202">Item</span></span></th>
<th align="left"><span data-ttu-id="e0eff-203">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0eff-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e0eff-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="e0eff-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="e0eff-205">O local de geo, por exemplo, nome.</span><span class="sxs-lookup"><span data-stu-id="e0eff-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e0eff-206">Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="e0eff-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="e0eff-207">O ponto de extremidade para se conectar, por exemplohttps://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="e0eff-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e0eff-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="e0eff-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="e0eff-209">O GUID da fonte de resultados, por exemplo B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="e0eff-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="e0eff-p117">Se você omitir DataLocation ou ponto de extremidade, ou se um DataLocation é duplicado, a solicitação falhará. [Você pode obter informações sobre o ponto de extremidade de locais de geo de um locatário usando o Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="e0eff-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="e0eff-212">Dados de resposta</span><span class="sxs-lookup"><span data-stu-id="e0eff-212">Response data</span></span>

<span data-ttu-id="e0eff-p118">MultiGeoSearchStatus – isso é uma propriedade que a API de pesquisa do SharePoint retorna em resposta a uma solicitação. O valor da propriedade será uma sequência de caracteres e fornece as seguintes informações sobre a API de pesquisa do SharePoint retorna os resultados:</span><span class="sxs-lookup"><span data-stu-id="e0eff-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e0eff-215">Valor</span><span class="sxs-lookup"><span data-stu-id="e0eff-215">Value</span></span></th>
<th align="left"><span data-ttu-id="e0eff-216">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0eff-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e0eff-217">Completo</span><span class="sxs-lookup"><span data-stu-id="e0eff-217">Full</span></span></td>
<td align="left"><span data-ttu-id="e0eff-218">Total resultados de <strong>todos</strong> os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="e0eff-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e0eff-219">Parcial</span><span class="sxs-lookup"><span data-stu-id="e0eff-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="e0eff-p119">Resultados de parciais de um ou mais locais de geo. Os resultados são incompletos devido a um erro transitório.</span><span class="sxs-lookup"><span data-stu-id="e0eff-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="e0eff-222">Consulta usando o serviço REST</span><span class="sxs-lookup"><span data-stu-id="e0eff-222">Query using the REST service</span></span>

<span data-ttu-id="e0eff-p120">Com uma solicitação GET, você pode especificar os parâmetros de consulta na URL. Com uma solicitação POST, você pode passar os parâmetros de consulta no corpo no formato JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="e0eff-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="e0eff-225">Cabeçalhos de solicitação</span><span class="sxs-lookup"><span data-stu-id="e0eff-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e0eff-226">Nome</span><span class="sxs-lookup"><span data-stu-id="e0eff-226">Name</span></span></th>
<th align="left"><span data-ttu-id="e0eff-227">Valor</span><span class="sxs-lookup"><span data-stu-id="e0eff-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e0eff-228">Tipo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="e0eff-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="e0eff-229">aplicativo/json; odata = verbose</span><span class="sxs-lookup"><span data-stu-id="e0eff-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="e0eff-230">Amostra da solicitação GET que leque está exibindo a **todos os** locais de geo</span><span class="sxs-lookup"><span data-stu-id="e0eff-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="e0eff-231">https:// \<locatário\>/\_api/pesquisa/query?querytext = 'sharepoint' & Propriedades = 'EnableMultiGeoSearch:true' & Tipo_de_cliente =' Meu\_cliente\_id'</span><span class="sxs-lookup"><span data-stu-id="e0eff-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="e0eff-232">Amostra da solicitação GET para espalham para **alguns** locais geo</span><span class="sxs-lookup"><span data-stu-id="e0eff-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="e0eff-233">https:// <tenant>/_api/search/query?querytext = 'site' & Tipo_de_cliente = 'my_client_id' & Propriedades ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{DataLocation\:"Nome"\,ponto de extremidade\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"Pode"\,ponto de extremidade\:" https\://contosoCAN.sharepoint-df.com "}]'</span><span class="sxs-lookup"><span data-stu-id="e0eff-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="e0eff-234">Amostra da solicitação POST que leque está exibindo a **todos os** locais de geo</span><span class="sxs-lookup"><span data-stu-id="e0eff-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="e0eff-235">Amostra da solicitação POST que leque está exibindo a **alguns** locais geo</span><span class="sxs-lookup"><span data-stu-id="e0eff-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="e0eff-236">Consulta usando CSOM</span><span class="sxs-lookup"><span data-stu-id="e0eff-236">Query using CSOM</span></span>

<span data-ttu-id="e0eff-237">Aqui está um exemplo de consulta CSOM leque está exibindo a **todos os** locais de geo:</span><span class="sxs-lookup"><span data-stu-id="e0eff-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

