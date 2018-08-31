---
title: Usando o Web Part de pesquisa de conteúdo, em vez de Web Part de consulta de conteúdo para melhorar o desempenho no SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: Este artigo descreve como aumentar o desempenho, substituindo o Web Part de consulta de conteúdo com a Web Part conteúdo de pesquisa no SharePoint Server 2013 e SharePoint Online.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539455"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="bdecc-103">Usando o Web Part de pesquisa de conteúdo, em vez de Web Part de consulta de conteúdo para melhorar o desempenho no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bdecc-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="bdecc-104">Este artigo descreve como aumentar o desempenho, substituindo o Web Part de consulta de conteúdo com a Web Part conteúdo de pesquisa no SharePoint Server 2013 e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bdecc-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="bdecc-p101">Um dos novos recursos do SharePoint Server 2013 e SharePoint Online mais poderosos é a parte de Web de pesquisa conteúdo (CSWP). Esta Web Part usa o índice de pesquisa para recuperar rapidamente os resultados que são mostrados ao usuário. Use a Web Part de pesquisa conteúdo em vez do conteúdo consulta CQWP (Web Part) em suas páginas para melhorar o desempenho de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="bdecc-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="bdecc-p102">Usando uma Web Part de pesquisa conteúdo sobre uma Web Part de consulta de conteúdo quase sempre resultará em significativamente melhor desempenho de carga de página no SharePoint Online. Não há uma pouca configuração adicional para obter a consulta à direita, mas as recompensas são obter melhor desempenho e mais satisfeitos usuários.</span><span class="sxs-lookup"><span data-stu-id="bdecc-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="bdecc-110">Comparando o ganho de desempenho obtido usando o Web Part de pesquisa de conteúdo, em vez de Web Part de consulta de conteúdo</span><span class="sxs-lookup"><span data-stu-id="bdecc-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="bdecc-p103">Os exemplos a seguir mostram os ganhos de desempenho relativo que poderá receber quando você usar uma Web Part de pesquisa conteúdo em vez de uma Web Part de consulta de conteúdo. Os efeitos são mais óbvios com uma estrutura de site complexo e consultas de conteúdo muito amplas.</span><span class="sxs-lookup"><span data-stu-id="bdecc-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="bdecc-113">Este site de exemplo tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="bdecc-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="bdecc-114">8 níveis de subsites.</span><span class="sxs-lookup"><span data-stu-id="bdecc-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="bdecc-115">Lista usando um tipo de conteúdo personalizado "fruta".</span><span class="sxs-lookup"><span data-stu-id="bdecc-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="bdecc-116">Na Web Part, a consulta de conteúdo é ampla, retornando todos os itens com o tipo de conteúdo de "frutas".</span><span class="sxs-lookup"><span data-stu-id="bdecc-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="bdecc-p104">O exemplo usa apenas 50 itens entre os sites de 8. Os efeitos vai ser ainda mais pronuncia-se para sites com mais de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bdecc-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="bdecc-119">Aqui está uma captura de tela dos resultados da consulta Web Part de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bdecc-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Gráfico que mostra a consulta de conteúdo da web part](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="bdecc-p105">No Internet Explorer, use a guia de **rede** das ferramentas de desenvolvedor do F12 para ver os detalhes para o cabeçalho de resposta. Na seguinte captura de tela, o valor para o **SPRequestDuration** essa carga de página é 924 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="bdecc-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Captura de tela mostrando a duração da solicitação de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="bdecc-p106">**SPRequestDuration** indica a quantidade de trabalho que é feito no servidor para preparar a página. Alternar o conteúdo por Web Parts de consulta com conteúdo por Web Parts de pesquisa drasticamente reduz o tempo que leva para renderizar a página. Por outro lado, uma página com uma Web Part equivalentes de pesquisa conteúdo, retornar o mesmo número de resultados possui um valor de **SPRequestDuration** de 106 milissegundos, conforme mostrado na captura de tela a este:</span><span class="sxs-lookup"><span data-stu-id="bdecc-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Captura de tela mostrando a Duração da Solicitação de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="bdecc-128">Adicionar uma Web Part de pesquisa de conteúdo no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bdecc-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="bdecc-p107">Adicionar uma Web Part de pesquisa conteúdo é muito semelhante a uma Web Part regular do consulta de conteúdo. Consulte a seção *"adicionar um conteúdo Web Part de pesquisa"* em [Configure um Web Part conteúdo de pesquisa no SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="bdecc-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="bdecc-131">Criando a consulta de pesquisa correta para o seu conteúdo Web Part de pesquisa</span><span class="sxs-lookup"><span data-stu-id="bdecc-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="bdecc-p108">Depois de adicionar uma Web Part de pesquisa conteúdo, você pode refinar a pesquisa e retornar os itens que você deseja. Para obter instruções detalhadas sobre como fazer isso, consulte a seção, *"Content de exibição, definindo uma consulta avançada em uma Web Part de pesquisa conteúdo"* em [Configure uma Web Part de pesquisa de conteúdo no SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="bdecc-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="bdecc-134">Criar e testar a ferramenta de consulta</span><span class="sxs-lookup"><span data-stu-id="bdecc-134">Query building and testing tool</span></span>

<span data-ttu-id="bdecc-135">Para uma ferramenta criar e testar consultas complexas, consulte a [Ferramenta de consulta de pesquisa](https://sp2013searchtool.codeplex.com/) no Codeplex.</span><span class="sxs-lookup"><span data-stu-id="bdecc-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

