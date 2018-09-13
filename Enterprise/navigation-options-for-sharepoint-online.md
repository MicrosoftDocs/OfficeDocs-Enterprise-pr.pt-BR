---
title: Opções de navegação para o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Este artigo descreve os sites de opções de navegação com a publicação do SharePoint habilitado no SharePoint Online. As opções e a configuração da navegação afeta significativamente o desempenho e escalabilidade de sites no SharePoint Online.
ms.openlocfilehash: 08790dcee343e9e69bbaab149cce8a390470e7d6
ms.sourcegitcommit: 5731dce2440e5a7a261f6360e8e2e9639d339d4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "23957446"
---
# <a name="navigation-options-for-sharepoint-online"></a>Opções de navegação para o SharePoint Online

Este artigo descreve os sites de opções de navegação com a publicação do SharePoint habilitado no SharePoint Online. As opções e a configuração da navegação afeta significativamente o desempenho e escalabilidade de sites no SharePoint Online.

## <a name="overview"></a>Visão geral

Configuração de provedor de navegação pode afetar significativamente o desempenho para todo o site e cuidadosa consideração deve ser seguida para selecionar um provedor de navegação e a configuração que pode ser dimensionado com eficiência para os requisitos de um site do SharePoint. Existem dois provedores de navegação da caixa, bem como implementações de navegação personalizado.

A primeira opção, [**navegação gerenciado (metadados)**](#using-managed-navigation-and-metadata-in-sharepoint-online), é recomendável e é uma das opções padrão no SharePoint Online; No entanto, é recomendável que a filtragem de segurança seja desativado, a menos que o necessário. Filtragem de segurança está habilitada como uma configuração de seguro por padrão para esse provedor de navegação; No entanto, muitos sites não exigem a sobrecarga de filtragem de segurança desde que elementos de navegação normalmente são consistentes para todos os usuários do site. Com a configuração recomendada para desabilitar a filtragem de segurança, esse provedor de navegação não exige enumerando a estrutura do site e é altamente escalonável com impacto no desempenho aceitável.

A segunda opção, [**navegação estrutural**](#using-structural-navigation-in-sharepoint-online), **não uma opção de navegação recomendada no SharePoint Online**. Esse provedor de navegação foi projetado para uma topologia de local tem suporte limitado no SharePoint Online. Enquanto ele fornece alguns adicional conjunto de recursos em comparação com outras opções de navegação, esses recursos, incluindo a filtragem de segurança e enumeração de estrutura do site, tem um custo de desempenho e escalabilidade impactos e chamadas de cargas excessivas no servidor quando ele é usado. Sites usando navegação structed que consomem recursos excessivos podem estar sujeitos de limitação.

Os provedores de navegação de-de-imediata, além de muitos clientes implementou com êxito implementações alternativas de navegação personalizado. Uma classe comum das implementações de navegação personalizado engloba os padrões de design renderizados pelo cliente que armazenam um cache local de nós de navegação. (Consulte **[scripts do lado do cliente orientado por pesquisa](#using-search-driven-client-side-scripting)** neste artigo.)

Esses provedores de navegação tem algumas das principais vantagens: 
- Eles geralmente funcionam bem com designs de página responsivos.
- Eles são escaláveis extremamente alto desempenho porque eles podem renderizar sem custo do recurso (e a atualização em segundo plano após um tempo limite). 
- Esses provedores de navegação podem recuperar dados de navegação usando diversas estratégias, que varia de configurações estáticas simples a vários provedores de intercâmbio dinâmico de dados. 

Um exemplo de um provedor de dados é usar uma **navegação orientada por pesquisa**, que permite a flexibilidade para enumerar nós de navegação e lidar com eficiência de filtragem de segurança. 

Existem outras opções populares para criar **provedores de navegação personalizado**. Analise [as soluções de navegação para portais SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) para obter mais orientações sobre a criação de um provedor de navegação personalizado.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Opções de navegação prós e contras do SharePoint Online

A tabela a seguir resume as vantagens e desvantagens de cada opção. 


|Navegação gerenciada  |Navegação estrutural  |Navegação orientada por pesquisa  |Provedor de navegação personalizada  |
|---------|---------|---------|---------|
|Vantagens:<br/><br/>Fácil de manter<br/>Opção recomendada<br/>     |Vantagens:<br/><br/>Fácil de configurar<br/>Filtragem de segurança<br/>Atualiza automaticamente conforme o conteúdo é adicionado<br/>|Prós:<br/><br/>Filtragem de segurança<br/>Atualização automática quando os sites são adicionados<br/>Tempo de carregamento rápido e estrutura de navegação armazenada em cache localmente<br/>|Prós:<br/><br/>Ampla gama de opções disponíveis<br/>Carregando Fast quando o cache é usada corretamente<br/>Muitas opções funcionam bem com o design da página responsivos<br/>|
|Desvantagens:<br/><br/>Não é atualizado automaticamente para refletir a estrutura do site<br/>Impacto sobre o desempenho se a filtragem de segurança está habilitada<br/>|Desvantagens:<br/><br/>**Não recomendado**<br/>**Impacto sobre o desempenho e escalabilidade**<br/>**Sujeito a limitação**<br/>|Desvantagens:<br/><br/>Não possui capacidade de ordenar facilmente os sites<br/>Requer a personalização da página mestra (habilidades técnicas necessárias)<br/>|Desvantagens:<br/><br/>Desenvolvimento personalizado é necessário<br/>Fonte de dados externa / cache armazenados é necessária Azure ex.:<br/>|

A opção mais adequada ao seu site dependerá em seus requisitos de site e em sua capacidade técnica. Se desejar que um provedor de navegação de-de-imediata escalonável, navegação gerenciada com a filtragem de segurança desabilitada é uma boa opção. 

A opção de navegação gerenciado pode ser mantida por meio de configuração, não envolvem arquivos de personalização de código e é consideravelmente menor do que a navegação estrutural. Se você exige a filtragem de segurança e estiver familiarizado com o uso de uma página mestra personalizada e alguns recursos na organização para manter as alterações que podem ocorrer na página mestra padrão para o SharePoint Online, a opção orientado por pesquisa pode produzir um melhor experiência do usuário. Se você tiver requisitos mais complexos, um provedor de navegação personalizado pode ser a melhor opção. Navegação estrutural não é recomendada.

Finalmente, é importante observar que o SharePoint está adicionando provedores de navegação adicionais e funcionalidades para modernas arquiteturas de site do SharePoint aproveitamento uma hierarquia de site mais plana e um modelo de hub e spoke com sites de hub do SharePoint. Isso permite que vários cenários que não exigem o uso do recurso de publicação do SharePoint a ser alcançada, e essas configurações de navegação otimizadas para escalabilidade e a latência no SharePoint Online. Observe que geralmente aplicando o mesmo princípio - simplificando a estrutura geral do seu site de publicação do SharePoint para uma estrutura mais simples, ajuda com o desempenho geral e dimensionar também. Isso significa que, em vez de informarem um único conjunto de sites com centenas de sites (subwebs), uma abordagem melhor é terá muitos conjuntos de sites com subsites pouquíssimas (subwebs).


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Usando navegação gerenciada e metadados no SharePoint Online

Navegação gerenciada é outra opção de-de-imediata que você pode usar para recriar a maioria da mesma funcionalidade da navegação estrutural. Metadados gerenciados podem ser configurado para que a filtragem de segurança habilitados ou desabilitados. Quando configurado com a filtragem de segurança desabilitada, navegação gerenciada é bastante eficiente, conforme ele carrega todos os links de navegação com um número constante de chamadas do servidor. Habilitar a filtragem de segurança, no entanto, dispensa algumas das vantagens da navegação gerenciada e os clientes podem escolher explorar uma das soluções de navegação personalizada para obter o melhor desempenho e escalabilidade.

Muitos sites não exigem a filtragem de segurança, como a estrutura de navegação normalmente é consistente para todos os usuários do site. Se a filtragem de segurança está desabilitada e um link é adicionado à navegação que nem todos os usuários têm acesso a, o link ainda mostrará mas levará a uma mensagem acesso negado. Não há nenhum risco de acesso inadvertidas ao conteúdo.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Como implementar a navegação gerenciada e os resultados

Há vários artigos sobre Docs.Microsoft.com sobre os detalhes da navegação gerenciada, por exemplo, consulte [Visão geral da navegação gerenciada no SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Para implementar a navegação gerenciada, você configurar termos com URLs correspondente à estrutura de navegação do site. Navegação gerenciada ainda pode ser curated manualmente para substituir a navegação estrutural em muitos casos. Por exemplo:

![Estrutura de site do SharePoint Online](media/SPONavOptionsListOfSites.png)

O exemplo a seguir mostra o desempenho da navegação complexa usando a navegação gerenciada.

![Desempenho da navegação complexo usando navegação gerenciada](media/SPONavOptionsComplexNavPerf.png)

Usar a navegação gerenciada consistentemente melhora o desempenho em comparação com a abordagem de navegação estrutural.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Usando a navegação estrutural no SharePoint Online

Esta é a navegação da caixa usada por padrão e é a solução mais simples, mas como tal, tem uma compensação de desempenho caro. Ele não requer qualquer personalização e um usuário não técnico também facilmente pode adicionar itens, ocultar itens e gerenciar o painel de navegação da página Configurações. Isso é Entretanto também true para a navegação gerenciada então, é recomendável usar a navegação gerenciada como que pode também ser facilmente gerenciado e controlado também com melhor desempenho.

![Navegação estrutural com Subsites Mostrar selecionada](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Ativando a navegação estrutural no SharePoint Online

Para ilustrar como o desempenho em uma solução do SharePoint Online standard com navegação estrutural e show subsites opção ativada. A seguir é uma captura de tela das configurações encontradas na página **Configurações do Site** \> **navegação**.
  
![Captura de tela mostrando subsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analisando o desempenho da navegação estrutural no SharePoint Online

Para analisar o desempenho de uma página do SharePoint, use a guia de **rede** das ferramentas de desenvolvedor do F12 no Internet Explorer. 
  
![Captura de tela mostrando a guia Rede das ferramentas de desenvolvimento F12](media/SPONavOptionsNetworks.png)
  
1. Na guia **Rede**, clique na página .aspx que está sendo carregada e, em seguida, clique na guia **Detalhes**.<br/> ![Captura de tela mostrando a guia de detalhes](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Clique em **Cabeçalhos de resposta**. <br/>![Captura de tela da guia Detalhes](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint retorna algumas informações de diagnósticos úteis em seus cabeçalhos de resposta. 
3. Uma das partes de informações mais útil é **SPRequestDuration** , que é o valor, em milissegundos, dos quanto tempo levou de uma solicitação para ser processada no servidor. **Mostrar subsites** é desmarcada para navegação estrutural na seguinte imagem. Isso significa que há somente o link de conjunto de sites, no painel de navegação global:<br/>![Captura de tela mostrando tempos de carga como duração da solicitação](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. A chave **SPRequestDuration** tem um valor de 245 milissegundos. Isso representa o tempo necessário para retornar a solicitação. Como há somente um item de navegação no site, este é um parâmetro de comparação bom para como o SharePoint Online executa sem navegação pesada. A próxima captura de tela mostra como a adição de subsites afeta essa chave.<br/>![Captura de tela mostrando uma duração de solicitação de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
Adicionar os subsites aumentou significativamente o tempo que leva para retornar a solicitação de página para este site de amostra relativamente simples. Hierarquias de sites complexos, incluindo páginas na navegação e outras configuração e as opções de topologia drasticamente podem aumentar ainda mais esse impacto.

## <a name="using-search-driven-client-side-scripting"></a>Usando o script do lado do cliente orientado por pesquisa

Usando a pesquisa, você pode aproveitar os índices que são criados no plano de fundo usando o rastreamento contínuo. Os resultados da pesquisa são extraídos do índice de pesquisa e os resultados são aparada de segurança. Isso é geralmente menor do que os provedores de navegação da caixa quando a filtragem de segurança é necessária. Usando a pesquisa para a navegação estrutural, especialmente se você tiver uma estrutura de site complexa, agilizará consideravelmente o tempo de carregamento de página. A principal vantagem disso sobre navegação gerenciada é que você se beneficia de filtragem de segurança.

Essa abordagem envolve a criação de uma página mestra personalizada e substituindo o código de navegação da caixa com HTML personalizadas. Siga este procedimento descrito no exemplo a seguir para substituir o código de navegação no arquivo `seattle.html`. Neste exemplo, você abrirá o `seattle.html` de arquivo e substitua o elemento todo `id=”DeltaTopNavigation”` com código personalizado de HTML.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Exemplo: Substitua o código de navegação da caixa em uma página mestra

1.  Navegue até a página Configurações do Site.
2.  Abra a galeria de páginas mestras clicando em **Páginas Mestras**.
3.  A partir daqui, você pode navegar por meio da biblioteca e baixe o arquivo `seattle.master`.
4.  Edite o código usando um editor de texto e exclua o bloco de código na captura de tela a seguir.<br/>![Excluir o bloco de código mostrado](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Remover o código entre o `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` e `<\SharePoint:AjaxDelta>` tags e substituí-lo com o trecho a seguir:<br/>

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
6. Substituir a URL no carregamento da imagem marca âncora no início, com um link para uma imagem de carregamento em seu conjunto de sites. Depois de fazer as alterações, renomeie o arquivo e, em seguida, carregue-o para a Galeria de páginas mestras. Isso gerará um novo arquivo. master.<br/>
7. Este HTML é a marcação básica que será preenchida pelos resultados de pesquisa retornados pelo código JavaScript. Você precisará editar o código para alterar o valor para a raiz de var = "URL do conjunto de sites" conforme demonstrado no seguinte trecho:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. Os resultados são atribuídos à matriz self.nodes e uma hierarquia é compilada sem os objetos usando linq.js atribuindo a saída para um self.heirarchy de matriz. Esta matriz é o objeto que é vinculado ao HTML. Isso é feito na função toggleView() passando o objeto self para a função ko.applyBinding().<br/>Em seguida, isso faz a matriz de hierarquia deve ser vinculado a seguinte HTML:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

Os manipuladores de eventos para `mouseenter` e `mouseexit` são adicionados para a navegação de nível superior para lidar com os menus de lista suspensa de subsite que é feita no `addEventsToElements()` função.

No nosso exemplo complexas de navegação, uma página nova carga sem mostra o cache local o tempo gasto no servidor foi reduzido para baixo de navegação estrutural parâmetro de comparação para obter um resultado semelhante como a abordagem da navegação gerenciada.

### <a name="about-the-javascript-file"></a>Sobre o arquivo JavaScript …

O arquivo JavaScript inteiro é o seguinte:

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

Para resumir o código mostrado acima no `jQuery $(document).ready` função existe um `viewModel object` criado e depois o `loadNavigationNodes()` função em tal objeto é chamada. Essa função ou carrega a hierarquia de navegação previamente compilado armazenada no armazenamento local HTML5 do navegador do cliente ou ele chama a função `queryRemoteInterface()`.

`QueryRemoteInterface()`cria uma solicitação usando o `getRequest()` função com o parâmetro de consulta definidos anteriormente no script e, em seguida, retorna dados do servidor. Esses dados são essencialmente uma matriz de todos os sites no conjunto de sites, representado como objetos de transferência de dados com várias propriedades. 

Esses dados são analisados, em seguida, em previamente definido `SPO.Models.NavigationNode` objetos que utilizam `Knockout.js` para criar propriedades observáveis para uso por dados, os valores de vinculação para o HTML que podemos definidos anteriormente. 

Os objetos são colocados em uma matriz de resultados. Essa matriz é analisada em JSON usando vazado e armazenado no armazenamento local do navegador para melhorar o desempenho no futuro página for carregada.

### <a name="benefits-of-this-approach"></a>Benefícios dessa abordagem

Uma grande vantagem [dessa](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) abordagem é que usando-se HTML5 de armazenamento local, painel de navegação é armazenado localmente para o usuário na próxima vez em que eles carregam a página. Recebemos melhorias de desempenho principais que usa a API de pesquisa para a navegação estrutural; No entanto, levará alguns recursos técnicos para executar e personalizar essa funcionalidade. 

Na [implementação de exemplo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), os sites são ordenados da mesma maneira como a navegação estrutural-de-imediata; ordem alfabética. Se você quisesse desviar nesta ordem, seria mais complicado para desenvolver e manter. Além disso, essa abordagem exige que você desviar das páginas mestras com suporte. Se a página mestra não é mantida, seu site será perder abrindo diante atualizações e aperfeiçoamentos que a Microsoft faz as páginas mestras.

O [acima código](#about-the-javascript-file) tem as seguintes dependências:

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- LINQ.js - http://linqjs.codeplex.com/, ou github.com/neuecc/linq.js

A versão atual do LinqJS não contém o método ByHierarchy usado no código acima e interromperá o código de navegação. Para corrigir esse problema, adicione o seguinte método ao arquivo Linq.js antes da linha `Flatten: function ()`.

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
  
## <a name="related-topics"></a>Tópicos relacionados

[Visão geral da navegação gerenciada no SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

