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
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>Configurar a pesquisa do OneDrive para Business Multi-Geo

Em um ambiente de Multi-Geo SharePoint Online (SPO), uma organização pode ter um locatário do Office 365, mas armazene seu conteúdo do SharePoint em várias localizações geográficas - um local central e um ou mais locais geo de satélite.

Cada localização geográfica tem seus próprios índice de pesquisa e o Centro de pesquisa. Quando um usuário procura, a consulta é leque exibindo para todos os índices e resultados retornados são mesclados.

Por exemplo, um usuário em um único local geo pode pesquisar para conteúdo armazenado em outro local geo ou conteúdo em um site do SharePoint que é restrita a um local diferente geo. Se o usuário tem acesso a esse conteúdo, a pesquisa mostrará o resultado.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Qual a pesquisa funciona de clientes em um ambiente Multi-Geo?

Esses clientes podem retornar resultados de todos os locais de geo:

-   OneDrive for Business

-   Delve

-   Na home page do SharePoint

-   Centro de pesquisa

-   Aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint

### <a name="onedrive-for-business"></a>OneDrive for Business

Assim que o ambiente de Multi-Geo tiver sido configurado, os usuários de pesquisa no OneDrive obter resultados de todos os locais de geo.

### <a name="delve"></a>Delve

Assim que o ambiente de Multi-Geo tiver sido configurado, os usuários de pesquisa no Delve obter resultados de todos os locais de geo.

O feed Delve e o cartão de perfil mostram apenas as visualizações dos arquivos que são armazenados no local **central** . Para arquivos que são armazenados nos locais de geo satélite, o ícone do tipo de arquivo é mostrado em vez disso.

### <a name="the-sharepoint-home-page"></a>Na home page do SharePoint

Assim que o ambiente de Multi-Geo tiver sido configurado, os usuários verão notícias, sites recentes e visitados vários locais geo na sua home page do SharePoint. Se eles usarem a caixa de pesquisa na home page do SharePoint, eles obterá resultados mesclados de vários locais geo.

### <a name="the-search-center"></a>Centro de pesquisa

Após o Multi-Geo ambiente tiver sido definida para cima, cada centro de pesquisa continua para mostrar somente os resultados de sua próprias local geo. Os administradores devem [alterar as configurações de cada centro de pesquisa](#_Set_up_a_1) para obter resultados de todos os locais de geo. Depois disso, os usuários que pesquise no Centro de pesquisa obtém resultados de todos os locais de geo.

### <a name="custom-search-applications"></a>Aplicativos de pesquisa personalizados

Normalmente, aplicativos de pesquisa personalizados interagem com os índices de pesquisa usando as APIs do REST de pesquisa do SharePoint existente. Para obter resultados de locais de geo todas ou algumas, o aplicativo deve [chamar a API e incluir os novos parâmetros de consulta Multi-Geo](#_Get_custom_search) na solicitação. Isso dispara um ventilador de consulta para todos os locais de geo.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>O que é diferente sobre a pesquisa em um ambiente Multi-Geo?

Alguns recursos de pesquisa que você pode estar familiarizado com, funcionam de modo diferente em um ambiente Multi-Geo.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Recurso</strong></th>
<th align="left"><strong>Como funciona</strong></th>
<th align="left"><strong>Solução alternativa</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Resultados promovidos</td>
<td align="left">Você pode criar regras de consulta com resultados promovidos em diferentes níveis: para o locatário todo, para um conjunto de sites ou para um site. Em um ambiente de Multi-Geo, defina resultados promovidos no nível de <strong>locatário</strong> , se você deseja promover os resultados para os centros de pesquisa em <strong>todos os</strong> locais de geo. Se você <strong>só</strong> deseja promover resultados no Centro de pesquisa que está no local do conjunto de sites ou site geo, defina os resultados no nível do <strong>conjunto de sites</strong> ou <strong>site</strong> .</td>
<td align="left">Se você não precisa diferentes resultados promovidos por geo local, por exemplo diferentes regras para viajando, é recomendável definindo promovidos resultados a nível de locatário.</td>
</tr>
<tr class="even">
<td align="left">Refinadores de pesquisa</td>
<td align="left">Pesquisa retorna refinadores de todos os locais de um inquilino geo e, em seguida, agrega-los. A agregação de lista segura é um melhor esforço, que significa que as contagens de refinador podem não ser 100% preciso. Para a maioria dos cenários orientado por pesquisa, essa precisão é suficiente.</td>
<td align="left">Para aplicativos orientado por pesquisa que dependam completude refinador, consulta cada local geo independentemente sem usar fan-out de Multi-Geo.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Pesquisa de multi-Geo não oferece suporte a bucketing dinâmico para refinadores numéricos.</td>
<td align="left">Use o <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">parâmetro "Discretize"</a> para refinadores numéricos.</td>
</tr>
<tr class="even">
<td align="left">IDs de documento</td>
<td align="left">Se você estiver desenvolvendo um aplicativo orientado por pesquisa que depende de IDs de documento, observe que as IDs de documento em um ambiente Multi-Geo não são exclusivas entre localidades geo, eles são exclusivos em cada local geo.</td>
<td align="left">Adicionamos uma coluna que identifica a localização geográfica. Use essa coluna para atingir exclusividade. Essa coluna é denominada "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Número de resultados</td>
<td align="left">A página de resultados de pesquisa mostra os resultados combinados nos locais geo, mas não é possível em uma página acima de 500 resultados.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>O que não é suportado para pesquisa em um ambiente Multi-Geo?

Alguns dos recursos de pesquisa que você pode estar familiarizado com, não são suportados em um ambiente Multi-Geo.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Recurso de pesquisa</strong></th>
<th align="left"><strong>Observação</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Autenticação de aplicativo</td>
<td align="left">Autenticação somente App (acesso privilegiado dos serviços) não é compatível com Multi-Geo pesquisa.</td>
</tr>
<tr class="even">
<td align="left">Usuários convidados</td>
<td align="left">Usuários convidados somente obtém resultados do local geo que eles estiver pesquisando de.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Como a pesquisa faz trabalhar em um ambiente de Multi-Geo?

**Todos** os clientes de pesquisa usam as APIs do REST de pesquisa do SharePoint existentes para interagir com os índices de pesquisa.
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. Um cliente de pesquisa chama o ponto de extremidade do REST de pesquisa com a propriedade de consulta EnableMultiGeoSearch = true.
2. A consulta é enviada para todos os locais de geo no inquilino.
3. Resultados de pesquisa de cada local geo são mesclados e classificados.
4. O cliente obtém os resultados de pesquisa unificada.



<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Observe que não podemos mesclar os resultados da pesquisa até que recebemos os resultados de todos os locais de geo. Isso significa que as pesquisas de Multi-Geo tem latência adicional em comparação com pesquisas em um ambiente com apenas um geo local.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Obtenha um centro de pesquisa para mostrar os resultados de todos os locais de geo

Cada centro de pesquisa tem várias verticais e você precisará configurar cada vertical individualmente.

1.  Certifique-se de que você execute essas etapas com uma conta que tenha permissão para editar a página de resultados de pesquisa e a Web Part de resultados de pesquisa.

2.  Navegue até a página de resultados de pesquisa (consulte a [lista](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de pesquisa de páginas de resultados)

3.  Selecione a vertical para configurar, clique em **configurações do** ícone de engrenagem no canto superior direito e, em seguida, clique em **Editar página**. A página de resultados de pesquisa é aberta no modo de edição.

     ![](media/configure-search-for-multi-geo_image2.png)
1.  Na Web Part de resultados da pesquisa, mova o ponteiro para o superior, no canto direito da Web Part, clique na seta e, em seguida, clique em **Editar Web Part** no menu. O painel de ferramentas da Web Part de resultados de pesquisa será aberto sob a faixa de opções na parte superior direita da página.![](media/configure-search-for-multi-geo_image3.png)

1.  No painel de ferramentas da Web Part, na seção **configurações** , em **configurações de controle de resultados**, selecione **Mostrar Multi-Geo resultados** para obter a Web Part de resultados de pesquisa para mostrar os resultados de todos os locais de geo.

2.  Clique em **Okey** para salvar suas alterações e fechar o painel de ferramentas da Web Part.

3.  Verifique suas alterações para a Web Part de resultados de pesquisa clicando em **Check-In** na guia página do menu principal.

4.  Publique as alterações usando o link fornecido na nota na parte superior da página.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Obtenha os aplicativos de pesquisa personalizados para mostrar os resultados de alguns ou todos os locais de geo

Aplicativos de pesquisa personalizados obtém resultados de locais de geo todas ou algumas, especificando-se os parâmetros de consulta com a solicitação para a API do REST de pesquisa do SharePoint. Dependendo dos parâmetros de consulta, a consulta é leque exibindo para todos os locais de geo ou para alguns locais geo. Por exemplo, se você precisar apenas consultar um subconjunto dos locais geo encontrar informações relevantes, você pode controlar o ventilador check-out para apenas elas. Se a solicitação tiver êxito, a API do REST de pesquisa do SharePoint retorna dados de resposta.

### <a name="query-parameters"></a>Parâmetros de consulta

EnableMultiGeoSearch - este é um valor Boolean que especifica se a consulta deverá ser leque exibindo para os índices de outros locais geo do inquilino Multi-Geo. Defini-la como **true** para espalham consulta; **false** para não espalham a consulta. O valor padrão é **false**. Se esse parâmetro não for incluído, a consulta é **não** leque exibindo a outros locais geo. Se você usar o parâmetro em um ambiente que não seja Multi-Geo, o parâmetro será ignorado.

Tipo_de_cliente - isso é uma cadeia de caracteres. Insira um nome exclusivo do cliente para cada aplicativo de pesquisa. Se esse parâmetro não for incluído, a consulta é **não** leque exibindo a outros locais geo.

MultiGeoSearchConfiguration - esta é uma lista opcional de qual geo locais in a Multi-Geo locatários para espalham a consulta para quando **EnableMultiGeoSearch** for **verdadeira**. Se você não incluir esse parâmetro ou deixe em branco, a consulta é leque exibindo a todos os locais de geo. Para cada local geo, insira os itens a seguir, no formato JSON:

<table>
<thead>
<tr class="header">
<th align="left">Item</th>
<th align="left">Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">O local de geo, por exemplo, nome.</td>
</tr>
<tr class="even">
<td align="left">Ponto de extremidade</td>
<td align="left">O ponto de extremidade para se conectar, por exemplohttps://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">O GUID da fonte de resultados, por exemplo B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Se você omitir DataLocation ou ponto de extremidade, ou se um DataLocation é duplicado, a solicitação falhará. [Você pode obter informações sobre o ponto de extremidade de locais de geo de um locatário usando o Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Dados de resposta

MultiGeoSearchStatus – isso é uma propriedade que a API de pesquisa do SharePoint retorna em resposta a uma solicitação. O valor da propriedade será uma sequência de caracteres e fornece as seguintes informações sobre a API de pesquisa do SharePoint retorna os resultados:

<table>
<thead>
<tr class="header">
<th align="left">Valor</th>
<th align="left">Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Completo</td>
<td align="left">Total resultados de <strong>todos</strong> os locais de geo.</td>
</tr>
<tr class="even">
<td align="left">Parcial</td>
<td align="left">Resultados de parciais de um ou mais locais de geo. Os resultados são incompletos devido a um erro transitório.</td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Consulta usando o serviço REST

Com uma solicitação GET, você pode especificar os parâmetros de consulta na URL. Com uma solicitação POST, você pode passar os parâmetros de consulta no corpo no formato JavaScript Object Notation (JSON).

#### <a name="request-headers"></a>Cabeçalhos de solicitação

<table>
<thead>
<tr class="header">
<th align="left">Nome</th>
<th align="left">Valor</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Tipo de conteúdo</td>
<td align="left">aplicativo/json; odata = verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Amostra da solicitação GET que leque está exibindo a **todos os** locais de geo

https:// \<locatário\>/\_api/pesquisa/query?querytext = 'sharepoint' & Propriedades = 'EnableMultiGeoSearch:true' & Tipo_de_cliente =' Meu\_cliente\_id'

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Amostra da solicitação GET para espalham para **alguns** locais geo

https:// <tenant>/_api/search/query?querytext = 'site' & Tipo_de_cliente = 'my_client_id' & Propriedades ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{DataLocation\:"Nome"\,ponto de extremidade\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"Pode"\,ponto de extremidade\:" https\://contosoCAN.sharepoint-df.com "}]'

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Amostra da solicitação POST que leque está exibindo a **todos os** locais de geo

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Amostra da solicitação POST que leque está exibindo a **alguns** locais geo


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

### <a name="query-using-csom"></a>Consulta usando CSOM

Aqui está um exemplo de consulta CSOM leque está exibindo a **todos os** locais de geo:

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

