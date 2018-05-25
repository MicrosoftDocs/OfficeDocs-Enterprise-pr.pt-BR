---
title: Configurar a pesquisa para o OneDrive for Business com a funcionalidade multigeográfica
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba mais sobre como configurar a pesquisa em um ambiente multigeográfico.
ms.openlocfilehash: d7e9109eaa7afcf36ea047d00c0bba8f16dd0fde
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="2c0bc-103">Configurar a pesquisa para o OneDrive for Business com a funcionalidade multigeográfica</span><span class="sxs-lookup"><span data-stu-id="2c0bc-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="2c0bc-104">Em um ambiente multigeográfico do SharePoint Online (SPO), uma organização pode ter um locatário do Office 365, mas armazenar o conteúdo do SharePoint em várias localizações geográficas – um local central e uma ou mais localizações geográficas satélites.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="2c0bc-p101">Cada localização geográfica tem o seu próprio índice de pesquisa e Centro de pesquisa. Quando um usuário pesquisa, realiza-se fan-out da consulta para todos os índices, e os resultados retornados são mesclados.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="2c0bc-p102">Por exemplo, um usuário em uma localização geográfica pode pesquisar conteúdo armazenado em outra localização geográfica ou por conteúdo em um site do SharePoint restrito a uma localização geográfica diferente. Se o usuário tiver acesso a esse conteúdo, a pesquisa mostrará o resultado.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="2c0bc-109">Quais clientes de pesquisa funcionam em um ambiente multigeográfico?</span><span class="sxs-lookup"><span data-stu-id="2c0bc-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="2c0bc-110">Esses clientes podem retornar resultados de todas as localizações geográficas:</span><span class="sxs-lookup"><span data-stu-id="2c0bc-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="2c0bc-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="2c0bc-111">OneDrive for Business</span></span>

-   <span data-ttu-id="2c0bc-112">Delve</span><span class="sxs-lookup"><span data-stu-id="2c0bc-112">Delve</span></span>

-   <span data-ttu-id="2c0bc-113">A home page do SharePoint</span><span class="sxs-lookup"><span data-stu-id="2c0bc-113">The SharePoint Central Administration Web site home page opens.</span></span>

-   <span data-ttu-id="2c0bc-114">O Centro de Pesquisa</span><span class="sxs-lookup"><span data-stu-id="2c0bc-114">The Search Center</span></span>

-   <span data-ttu-id="2c0bc-115">Aplicativos de pesquisa personalizada que usam a API de pesquisa do SharePoint</span><span class="sxs-lookup"><span data-stu-id="2c0bc-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="2c0bc-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="2c0bc-116">OneDrive for Business</span></span>

<span data-ttu-id="2c0bc-117">Assim que o ambiente multigeográfico for configurado, os usuários que pesquisam no OneDrive obtêm resultados de todas as localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="2c0bc-118">Delve</span><span class="sxs-lookup"><span data-stu-id="2c0bc-118">Delve</span></span>

<span data-ttu-id="2c0bc-119">Assim que o ambiente multigeográfico for configurado, os usuários que pesquisam no Delve obtêm resultados de todas as localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="2c0bc-p103">O feed do Delve e o cartão de perfil mostram apenas as visualizações de arquivos armazenados no local **central**. Para os arquivos armazenados em localizações geográficas satélites, é mostrado o ícone para o tipo de arquivo.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="2c0bc-122">A home page do SharePoint</span><span class="sxs-lookup"><span data-stu-id="2c0bc-122">The SharePoint Central Administration Web site home page opens.</span></span>

<span data-ttu-id="2c0bc-p104">Assim que o ambiente multigeográfico for configurado, os usuários verão notícias, sites recentes e seguidos a partir de várias localizações geográficas na home page do SharePoint. Se eles usarem a caixa de pesquisa na home page do SharePoint, receberão resultados mesclados de várias localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="2c0bc-125">O Centro de Pesquisa</span><span class="sxs-lookup"><span data-stu-id="2c0bc-125">The Search Center</span></span>

<span data-ttu-id="2c0bc-p105">Após a configuração do ambiente multigeográfico, cada Centro de Pesquisa continua mostrando apenas os resultados da própria localização geográfica. Os administradores devem [alterar as configurações de cada centro de pesquisa](#_Set_up_a_1) para obter resultados de todas as localizações geográfica. Posteriormente, os usuários que pesquisarem no Centro de Pesquisa obterão resultados de todas as localizações geográfica.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="2c0bc-129">Aplicativos de pesquisa personalizada</span><span class="sxs-lookup"><span data-stu-id="2c0bc-129">Custom search applications</span></span>

<span data-ttu-id="2c0bc-p106">Como de costume, os aplicativos de pesquisa personalizada interagem com os índices de pesquisa usando as APIs REST existentes da Pesquisa do SharePoint. Para obter resultados de todas ou de algumas localizações geográficas, o aplicativo deve [ligar para a API e incluir os novos parâmetros de consulta multigeográfica](#_Get_custom_search) na solicitação. Isso dispara um fan-out da consulta para todas as localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="2c0bc-133">O que a pesquisa em um ambiente multigeográfico tem de diferente?</span><span class="sxs-lookup"><span data-stu-id="2c0bc-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="2c0bc-134">Alguns recursos de pesquisa que talvez você conheça funcionam diferente em um ambiente multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2c0bc-135"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="2c0bc-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="2c0bc-136"><strong>Como funciona</strong></span><span class="sxs-lookup"><span data-stu-id="2c0bc-136"><strong>How does it work?</strong></span></span></th>
<th align="left"><span data-ttu-id="2c0bc-137"><strong>Solução alternativa</strong></span><span class="sxs-lookup"><span data-stu-id="2c0bc-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2c0bc-138">Resultados promovidos</span><span class="sxs-lookup"><span data-stu-id="2c0bc-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-p107">Você pode criar regras de consulta com resultados promovidos em diferentes níveis: para o locatário inteiro, para um conjunto de sites ou para um site. Em um ambiente multigeográfico, defina os resultados promovidos no nível de <strong>locatário</strong> se quiser promover os resultados para os Centros de Pesquisa em <strong>todas</strong> as localizações geográficas. Se você <strong>apenas</strong> deseja promover resultados no Centro de Pesquisa que está na localização geográfica do conjunto de sites ou do site, defina os resultados no nível do <strong>conjunto de sites</strong> ou do <strong>site</strong>.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-142">Se você não precisar de diferentes resultados promovidos por localização geográfica, como diferentes regras de viagens, recomendamos definir resultados promovidos no nível do locatário.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2c0bc-143">Refinadores de pesquisa</span><span class="sxs-lookup"><span data-stu-id="2c0bc-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-p108">A pesquisa retorna refinadores de todas as localizações geográficas de um locatário e os agrega. A agregação é um esforço dentro do melhor possível, quer dizer, as contagens de refinador podem não estar 100% corretas. Para a maioria dos cenários orientados por pesquisa, esse nível e precisão é suficiente.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-147">Para os aplicativos orientados por pesquisa que dependem da integridade de refinador, consulte cada localização geográfica individualmente sem usar o fan-out multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="2c0bc-148">A pesquisa multigeográfica não dá suporte a bucketing dinâmico para refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-149">Use o <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">parâmetro "Discretizar"</a> para refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2c0bc-150">IDs do documento</span><span class="sxs-lookup"><span data-stu-id="2c0bc-150">Unique Document IDs</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-151">Se você estiver desenvolvendo um aplicativo orientado por pesquisa que depende de IDs do documento, observe que as IDs de documento em um ambiente multigeográfico não são exclusivas entre localizações geográficas, elas são exclusivas por localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-p109">Adicionamos uma coluna que identifica a localização geográfica. Use essa coluna para obter exclusividade. Essa coluna é denominada "GeoLocationSource".</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2c0bc-155">Número de resultados</span><span class="sxs-lookup"><span data-stu-id="2c0bc-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-156">A página de resultados de pesquisa mostra resultados combinados das localizações geográficas, mas não é possível paginar mais de 500 resultados.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="2c0bc-157">O que a pesquisa em um ambiente multigeográfico não suporta?</span><span class="sxs-lookup"><span data-stu-id="2c0bc-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="2c0bc-158">Alguns dos recursos de pesquisa que talvez você conheça não são suportados em um ambiente multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2c0bc-159"><strong>Recurso de pesquisa</strong></span><span class="sxs-lookup"><span data-stu-id="2c0bc-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="2c0bc-160"><strong>Observação</strong></span><span class="sxs-lookup"><span data-stu-id="2c0bc-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2c0bc-161">Autenticação somente aplicativo</span><span class="sxs-lookup"><span data-stu-id="2c0bc-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-162">A autenticação somente de aplicativos (acesso privilegiado dos serviços) não tem suporte na pesquisa multigeográfica.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2c0bc-163">Usuários convidados</span><span class="sxs-lookup"><span data-stu-id="2c0bc-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-164">Os usuários convidados só obtêm resultados da localização geográfica da qual estão pesquisando.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="2c0bc-165">Como a pesquisa funciona em um ambiente multigeográfico?</span><span class="sxs-lookup"><span data-stu-id="2c0bc-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="2c0bc-166">**Todos os** clientes de pesquisa usam as existentes APIs REST de Pesquisa do SharePoint para interagir com os índices de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="2c0bc-167">Um cliente pesquisa chama o ponto de extremidade da API REST com a propriedade de consulta EnableMultiGeoSearch= true.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="2c0bc-168">A consulta é enviada a todas as localizações geográficas no locatário.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="2c0bc-169">Os resultados de pesquisa de cada localização geográfica são mesclados e classificados.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="2c0bc-170">O cliente obtém resultados de pesquisa unificados.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-170">The client gets unified search results.</span></span>



<span data-ttu-id="2c0bc-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Observe que não mesclamos os resultados de pesquisa até recebermos resultados de todas as localizações geográficas. Isso significa que as pesquisas multigeográficas têm latência adicional comparadas às pesquisas em um ambiente com apenas uma localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="2c0bc-173">Obter um centro de pesquisa para mostrar resultados de todas as localizações geográficas</span><span class="sxs-lookup"><span data-stu-id="2c0bc-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="2c0bc-174">Cada centro de pesquisa tem vários verticais e você precisará configurar cada vertical individualmente.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="2c0bc-175">Certifique-se de executar essas etapas com uma conta que tenha permissão para editar a página de resultados de pesquisa e a Web Part de resultados de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="2c0bc-176">Navegue até a página de resultados de pesquisa (confira a [lista](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) das páginas de resultados de pesquisa)</span><span class="sxs-lookup"><span data-stu-id="2c0bc-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="2c0bc-p111">Selecione o eixo vertical a configurar, clique no ícone de engrenagem **Configurações** no canto superior direito e, em seguida, clique em **Editar página**. A página de resultados de pesquisa abre no modo de edição.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="2c0bc-p112">Na Web Part de resultados da pesquisa, mova o ponteiro para o canto superior direito da Web Part, clique na seta e, em seguida, clique em **Editar Web Part** no menu. O painel de ferramentas da Web Part de resultados de pesquisa abre na faixa de opções no canto superior direito da página. ![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="2c0bc-181">No painel de ferramentas da Web Part, na seção **Configurações**, em **Configurações de controle de resultados**, marque **Mostrar resultados multigeográficos** para obter a Web Part de resultados de pesquisa para mostrar resultados de todas as localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="2c0bc-182">Clique em **OK** para salvar as alterações e fechar o painel de ferramentas da Web Part.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="2c0bc-183">Verifique as suas alterações na Web Part de resultados da pesquisa clicando em **Check-In** na guia Página do menu principal.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="2c0bc-184">Publique as alterações usando o link fornecido na observação na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="2c0bc-185">Obter aplicativos de pesquisa personalizada para mostrar resultados de todas ou algumas localizações geográficas</span><span class="sxs-lookup"><span data-stu-id="2c0bc-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="2c0bc-p113">Os aplicativos de pesquisa personalizada obtêm resultados de todas ou algumas localizações geográficas, especificando-se os parâmetros de consulta com a solicitação para a API REST de pesquisa do SharePoint. Dependendo dos parâmetros de consulta, realiza-se fan-out da consulta para todas ou algumas localizações geográficas. Por exemplo, se você apenas precisar consultar um subconjunto de localizações geográficas para encontrar informações relevantes, você pode controlar o fan-out apenas de acordo com elas. Se a solicitação for concluída, a API REST de pesquisa do SharePoint retorna dados de resposta.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="2c0bc-190">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="2c0bc-190">Query parameters</span></span>

<span data-ttu-id="2c0bc-p114">EnableMultiGeoSearch — É um valor booliano que especifica se se realiza fan-out da consulta para os índices de outras localizações geográficas do locatário multigeográfico. Definia-o como **verdadeiro** para fazer fan-out da consulta; **falso** para não fazer fan-out da consulta. O valor padrão é **falso**. Se esse parâmetro não for incluído, **não** será realizado fan-out da consulta para outras localizações geográficas. Se você usar o parâmetro em um ambiente que não seja multigeográfico, o parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="2c0bc-p115">ClientType — Isso é uma cadeia de caracteres. Insira um nome de cliente exclusivo para cada aplicativo de pesquisa. Se você não incluir esse parâmetro, **não** será realizado fan-out da consulta para outras localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="2c0bc-p116">MultiGeoSearchConfiguration — Isso é uma lista opcional de quais localizações geográficas no locatário multigeográfico realizará fan-out da consulta para quando **EnableMultiGeoSearch** for **verdadeiro**. Se você não incluir esse parâmetro ou deixá-lo em branco, será realizado fan-out da consulta para todas as localizações geográficas. Para cada localização, insira os seguintes itens, no formato JSON:</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2c0bc-202">Item</span><span class="sxs-lookup"><span data-stu-id="2c0bc-202">Item</span></span></th>
<th align="left"><span data-ttu-id="2c0bc-203">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c0bc-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2c0bc-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="2c0bc-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-205">Localização geográfica, por exemplo, NAM.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2c0bc-206">EndPoint</span><span class="sxs-lookup"><span data-stu-id="2c0bc-206">endpoint</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-207">O ponto de extremidade ao qual se conectar, por exemplo, https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="2c0bc-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2c0bc-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="2c0bc-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-209">O GUID da fonte de resultados, por exemplo, B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="2c0bc-p117">Se você omitir DataLocation ou EndPoint ou se um DataLocation estiver duplicado, a solicitação falhará. [Você pode obter informações sobre o ponto de extremidade das localizações geográficas de um locatário usando o Microsoft Graph](https://docs.microsoft.com/pt-BR/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/pt-BR/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="2c0bc-212">Dado de resposta</span><span class="sxs-lookup"><span data-stu-id="2c0bc-212">Response data</span></span>

<span data-ttu-id="2c0bc-p118">MultiGeoSearchStatus – Isso é uma propriedade que a API de pesquisa do SharePoint retorna em resposta a uma solicitação. O valor da propriedade é uma cadeia de caracteres e fornece as seguintes informações sobre os resultados que a API de pesquisa do SharePoint retorna:</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2c0bc-215">Valor</span><span class="sxs-lookup"><span data-stu-id="2c0bc-215">Value</span></span></th>
<th align="left"><span data-ttu-id="2c0bc-216">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c0bc-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2c0bc-217">Completo</span><span class="sxs-lookup"><span data-stu-id="2c0bc-217">Full</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-218">Total de resultados de <strong>todas</strong> as localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2c0bc-219">Parcial</span><span class="sxs-lookup"><span data-stu-id="2c0bc-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-p119">Os resultados parciais de uma ou mais localizações geográficas. Os resultados são incompletos devido a um erro transitório.</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="2c0bc-222">Consulta usando o serviço REST</span><span class="sxs-lookup"><span data-stu-id="2c0bc-222">Query using the REST service</span></span>

<span data-ttu-id="2c0bc-p120">Com uma solicitação GET, você especifica os parâmetros da consulta na URL. Com uma solicitação POST, você passa os parâmetros de consulta no corpo no formato JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="2c0bc-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="2c0bc-225">Cabeçalhos de solicitação</span><span class="sxs-lookup"><span data-stu-id="2c0bc-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2c0bc-226">Nome</span><span class="sxs-lookup"><span data-stu-id="2c0bc-226">Name</span></span></th>
<th align="left"><span data-ttu-id="2c0bc-227">Valor</span><span class="sxs-lookup"><span data-stu-id="2c0bc-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2c0bc-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="2c0bc-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="2c0bc-229">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="2c0bc-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="2c0bc-230">Exemplo de solicitação GET da qual se realiza fan-out para **todas** as localizações geográficas</span><span class="sxs-lookup"><span data-stu-id="2c0bc-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="2c0bc-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="2c0bc-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="2c0bc-232">Exemplo de solicitação GET da qual realizar fan-out para **algumas** localizações geográficas</span><span class="sxs-lookup"><span data-stu-id="2c0bc-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="2c0bc-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="2c0bc-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="2c0bc-234">Exemplo de solicitação POST da qual se realiza fan-out para **todas** as localizações geográficas</span><span class="sxs-lookup"><span data-stu-id="2c0bc-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="2c0bc-235">Exemplo de solicitação POST da qual se realiza fan-out para **algumas** localizações geográficas</span><span class="sxs-lookup"><span data-stu-id="2c0bc-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="2c0bc-236">Consulta usando o CSOM</span><span class="sxs-lookup"><span data-stu-id="2c0bc-236">Query using CSOM</span></span>

<span data-ttu-id="2c0bc-237">Vejamos um exemplo de consulta CSOM da qual se faz fan-out para **todas** as localizações geográficas:</span><span class="sxs-lookup"><span data-stu-id="2c0bc-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

