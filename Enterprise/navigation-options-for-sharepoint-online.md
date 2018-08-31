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
# <a name="navigation-options-for-sharepoint-online"></a>Opções de navegação para o SharePoint Online

Este artigo descreve como melhorar os tempos de carregamento de página para o SharePoint Online usando navegação gerenciada ou navegação orientada por pesquisa na publicação clássico.
  
SharePoint Online com publicação clássica habilitada tem duas áreas de navegação; Navegação global e navegação atual.
  
Navegação global é o menu de navegação superior, enquanto navegação atual está o lado ou em contexto esquerda/direita navegação depende a configuração de idioma e a página mestra utilizada.
  
Navegação pode afetar negativamente o desempenho para o Portal inteiro conforme ele é geralmente configurado para uso do portal para toda a empresa e como tal, é um elemento importante de qualquer site do SharePoint.
  
Navegação estrutural não é a opção recomendada de navegação no SharePoint Online, pois ele foi projetado para uma topologia de local diante com a filtragem de segurança e esse projeto faz com que as chamadas de cargas excessivas no servidor e afeta o desempenho quando ele é usado.
  
Que o design foi alterado com a introdução dos sites do SharePoint moderno onde moderno tem uma hierarquia de site plana simplificada. Isso tem simplificado navegação com uma hierarquia simplificada que eliminou problemas de desempenho relacionados à navegação.
  
Há duas opções principais de navegação da caixa no SharePoint, bem como uma terceira, abordagem personalizada e orientado por pesquisa. Como alternativa, um quarto e opção bastante popular é criar um provedor de navegação personalizado. Analise [as soluções de navegação para portais SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) para obter orientações sobre um provedor de navegação personalizado. 
  
Cada opção tem vantagens e desvantagens, conforme descrito na tabela a seguir.
  
|**Navegação estrutural**|**Navegação gerenciada**|**Navegação orientada por pesquisa**||**Provedor de navegação personalizada**|
|:-----|:-----|:-----|:-----|:-----|
| Vantagens:  <br/>  Fácil de configurar  <br/>  Remoção de segurança  <br/>  Atualização automática quando os sites são adicionados  <br/> | Vantagens:  <br/>  Fácil de manter  <br/>  Opção recomendada  <br/> | Vantagens:  <br/>  Remoção de segurança  <br/>  Atualização automática quando os sites são adicionados  <br/>  Tempo de carregamento rápido e estrutura de navegação armazenada em cache localmente  <br/> || Prós:  <br/>    <br/>  Escolha mais larga / opções disponíveis  <br/>  Carregando Fast quando o cache é usada corretamente  <br/> |
| Desvantagens:  <br/> **Não recomendado** <br/> **Impacto sobre o desempenho** <br/> | Desvantagens:  <br/>  Não é atualizado automaticamente para refletir a estrutura do site  <br/>  Impacto sobre o desempenho se a filtragem de segurança está habilitada  <br/> | Desvantagens:  <br/>  Não possui capacidade de ordenar facilmente os sites  <br/>  Requer a personalização da página mestra (habilidades técnicas necessárias)  <br/> || Desvantagens:  <br/>  Desenvolvimento personalizado é necessário  <br/>  Fonte de dados externa / cache armazenados é necessária Azure ex.:  <br/> |
   
A opção mais adequada ao seu site dependerá em seus requisitos de site e em sua capacidade técnica. Se você estiver familiarizado com o uso de uma página mestra personalizada e alguns recursos da organização para manter as alterações que podem ocorrer na página mestra padrão para o SharePoint Online, a opção orientado por pesquisa produzirá a melhor experiência de usuário. Se desejar que um simple intermediário entre a navegação estrutural de-de-imediata e pesquisa, o painel de navegação gerenciada é uma boa opção. A opção de navegação gerenciada pode ser mantida por meio de configuração, não envolvem arquivos de personalização de código e é consideravelmente menor do que a navegação estrutural da caixa.
  
Simplificando a estrutura geral do seu Portal clássico muito semelhante moderno, ajuda com desempenho e escala também gerais. O que isso significa é que, em vez de um único conjunto de sites com centenas / milhares de sites (subwebs), uma abordagem melhor é terá muitos conjuntos de sites com subsites pouquíssimas (subwebs).
  
Isso fornece opções adicionais de dimensionamento no serviço, evita colocar todo o conteúdo em um banco de dados grande e basicamente permite maior flexibilidade para a navegação e mais importante de segurança.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Usando a navegação estrutural no SharePoint Online

Esta é a navegação da caixa usada por padrão e é a solução mais simples, mas como tal, tem uma compensação de desempenho caro. Ele não requer qualquer personalização e um usuário não técnico também facilmente pode adicionar itens, ocultar itens e gerenciar o painel de navegação da página Configurações. Isso é, no entanto, também true para a navegação gerenciada então, é recomendável usar a navegação gerenciada como que pode também ser facilmente gerenciados e controlados também.
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Ativando a navegação estrutural no SharePoint Online

Para ilustrar como o desempenho em uma solução do SharePoint Online standard com navegação estrutural e show subsites opção ativada. A seguir é uma captura de tela configurações encontradas na página **Configurações do Site** \> **navegação**.
  
![Captura de tela mostrando subsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analisando o desempenho da navegação estrutural no SharePoint Online

Para analisar o desempenho de uma página do SharePoint use a guia **Rede** das ferramentas do desenvolvedor F12 no Internet Explorer. 
  
![Captura de tela mostrando a guia Rede das ferramentas de desenvolvimento F12](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
Na guia **Rede**, clique na página .aspx que está sendo carregada e, em seguida, clique na guia **Detalhes**. 
  
![Captura de tela mostrando a guia de detalhes](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
Clique em **Cabeçalhos de resposta**.
  
![Captura de tela da guia Detalhes](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
O SharePoint retorna algumas informações de diagnóstico úteis em seus cabeçalhos de resposta. Uma das mais úteis é **SPRequestDuration** que é o valor, em milissegundos, do tempo que uma solicitação levou para ser processada no servidor. 
  
**Mostrar subsites** de captura de tela a seguir está desmarcada para navegação estrutural. Isso significa que há somente o link de conjunto de sites, no painel de navegação global: 
  
![Captura de tela mostrando tempos de carga como duração da solicitação](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
A chave **SPRequestDuration** tem um valor de 245 milissegundos. Isso representa o tempo necessário para retornar a solicitação. Como há somente um item de navegação no site, este é um parâmetro de comparação bom para como o SharePoint Online executa sem navegação pesada. A próxima captura de tela mostra como a adição de subsites afeta essa chave. 
  
![Captura de tela mostrando uma duração de solicitação de 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
Adicionar os subsites aumentou significativamente o tempo necessário para retornar a solicitação de página.
  
As vantagens de usar a navegação estruturada regular é que você pode facilmente organizar a ordem, ocultar sites, adicione páginas, os resultados são aparada de segurança e tenha de páginas mestras com suporte usadas no SharePoint Online não se desviado.
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>Usando a navegação gerenciada e metadados gerenciados no SharePoint Online

A navegação gerenciada é outra opção integrada que você pode usar para recriar o mesmo tipo de funcionalidade que a navegação estrutural.
  
A vantagem de usar metadados gerenciados é o que é muito mais rápido para recuperar os dados é diferente usando o conteúdo por consulta para criar a navegação do site. Embora seja que muito mais rapidez não há segurança trim os resultados por isso se um usuário não tem acesso a um site específico, o link ainda mostrará mas levará a uma mensagem de erro.
  
 **Como implementar a navegação gerenciada e os resultados**
  
Há vários artigos no TechNet sobre os detalhes da navegação gerenciada, por exemplo, consulte [Visão geral da navegação gerenciada no SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).
  
Para implementar a navegação gerenciada são necessárias permissões do administrador do repositório de termos. Ao configurar termos com URLs que coincidem com a estrutura de um conjunto de sites, a navegação gerenciada pode ser usada para substituir a navegação estrutural. Por exemplo:
  
![Captura de tela do exemplo de Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
O exemplo a seguir mostra o desempenho da navegação complexa usando a navegação gerenciada.
  
![Captura de tela do exemplo de SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
Usar a navegação gerenciada consistentemente melhora o desempenho em comparação com a abordagem de navegação estrutural de consulta por conteúdo.
  
## <a name="using-search-driven-client-side-scripting"></a>Usando o script do lado do cliente orientado por pesquisa

Utilizando a pesquisa, você pode aproveitar os índices que são criados na tela de fundo usando o rastreamento contínuo. Isso significa que não existem consultas de conteúdo pesadas. Os resultados da pesquisa são retirados do índice de pesquisa e passam pela remoção de segurança. Isso é mais rápido do que usar consultas de conteúdo normais. Usar a pesquisa para a navegação estrutural, especialmente se tiver uma estrutura de site complexa, irá acelerar consideravelmente o tempo de carregamento de página. A principal vantagem desta navegação sobre a gerenciada é que você se beneficia da filtragem de segurança.
  
Essa abordagem envolve a criação de uma página mestra personalizada e a substituição do código de navegação integrado com HTML personalizado. Siga este procedimento para substituir o código de navegação no arquivo seattle.html.
  
Neste exemplo, você abrir o arquivo seattle.html e substitua o elemento todo **id = "DeltaTopNavigation"** com o código HTML personalizado. 
  
 **Exemplo: Para substituir o código de navegação integrado em uma página mestra**
  
1. Navegue até a página **Configurações do Site**. 
    
2. Abra a galeria de páginas mestras clicando em **Páginas Mestras**.
    
3. Aqui você pode navegar pela biblioteca e baixar o arquivo **seattle.master**.
    
4. Edite o código usando um editor de texto e exclua o bloco de código na captura de tela a seguir.
    
    ![Captura de tela do código DeltaTopNavigation para exclusão](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. Remover o código entre o \<SharePoint:AjaxDelta id = "DeltaTopNavigation"\> e \<\SharePoint:AjaxDelta\> tags e substituí-lo com o trecho a seguir:
    
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

6. Substituir a URL no carregamento da imagem marca âncora no início, com um link para uma imagem de carregamento em seu conjunto de sites. Depois de fazer as alterações, renomeie o arquivo e, em seguida, carregue-o para a Galeria de páginas mestras. Isso gerará um novo arquivo. master.
    
7. Este HTML é a marcação básica que será preenchida pelos resultados de pesquisa retornados pelo código JavaScript. Você precisará editar o código a seguir para alterar o valor para o `var root = "site collection URL"` conforme demonstrado no seguinte trecho: 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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

     $("li.level1").mouseover (função () { 
  
posição de var = $(this).position();
  
$(this).find("ul.level2").css ({largura: 100, esquerda: position.left + 10, top: 50});
    
     }) 
  
.Mouseout (função () {
  
$(this).find("ul.level2").css ({esquerdo:-99999, superior: 0});
  
});
  
$("li.level2").mouseover (função () {
  
posição de var = $(this).position();
  
console.log(JSON.stringify(Position));
  
$(this).find("ul.level3").css ({largura: 100, esquerda: position.left + 95, top: position.top});
    
     }) 
  
.Mouseout (função () {
  
$(this).find("ul.level3").css ({esquerdo:-99999, superior: 0});
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. Em seguida, os resultados são atribuídos à matriz **[self.nodes]** e uma hierarquia é compilada sem os objetos usando linq.js atribuindo a saída para uma matriz **[self.heirarchy]**. Esta matriz é o objeto que é vinculado ao HTML. Isso é feito na função **[toggleView()]** , passando o objeto self para a função **[ko.applyBinding()]** . Em seguida, isso faz a matriz de hierarquia deve ser vinculado a seguinte HTML: 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    Finalmente, os manipuladores de eventos para **[mouseenter]** e **[mouseexit]** são adicionados para a navegação de nível superior para lidar com os menus suspensos subsite que é feita na função **[addEventsToElements()]** . 
    
    Os resultados do painel de navegação podem ser vistos na captura de tela abaixo:
    
    ![Captura de tela de resultados de navegação](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    No nosso exemplo de navegação complexa, uma página em branco carregada sem o cache local mostra que o tempo gasto no servidor foi reduzido do parâmetro de comparação da navegação estrutural para obter um resultado semelhante, como a abordagem de navegação gerenciada.
    
    ![Captura de tela de SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    Uma grande vantagem dessa abordagem é que ao usar o armazenamento local HTML5, a navegação é armazenada localmente para os usuários na próxima vez em que carregarem a página.
    
Recebemos importantes melhorias de desempenho usando a API de pesquisa para a navegação estrutural. No entanto, são necessários alguns recursos técnicos para executar e personalizar essa funcionalidade. No exemplo de implementação, os sites são ordenados da mesma forma que a navegação estrutural integrada; em ordem alfabética. Será mais complicado de desenvolver e manter se você quiser evitar essa ordem. Além disso, esta abordagem exige que você se desvie das páginas mestras suportadas. Se a página mestra personalizada não for mantida, seu site perderá as atualizações e as melhorias que a Microsoft faz nas páginas mestras.
  
O código acima tem as seguintes dependências:
  
- jQuery-[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), ou [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
A versão atual do LinqJS não contém o método ByHierarchy usado no código acima e interromperá o código de navegação. Para corrigir esse problema, adicione o seguinte método ao arquivo Linq.js antes da linha "nivelamento: funcionar ()".
  
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


