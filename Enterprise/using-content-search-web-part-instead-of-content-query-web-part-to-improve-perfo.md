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
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Usando o Web Part de pesquisa de conteúdo, em vez de Web Part de consulta de conteúdo para melhorar o desempenho no SharePoint Online

Este artigo descreve como aumentar o desempenho, substituindo o Web Part de consulta de conteúdo com a Web Part conteúdo de pesquisa no SharePoint Server 2013 e SharePoint Online.
  
Um dos novos recursos do SharePoint Server 2013 e SharePoint Online mais poderosos é a parte de Web de pesquisa conteúdo (CSWP). Esta Web Part usa o índice de pesquisa para recuperar rapidamente os resultados que são mostrados ao usuário. Use a Web Part de pesquisa conteúdo em vez do conteúdo consulta CQWP (Web Part) em suas páginas para melhorar o desempenho de seus usuários.
  
Usando uma Web Part de pesquisa conteúdo sobre uma Web Part de consulta de conteúdo quase sempre resultará em significativamente melhor desempenho de carga de página no SharePoint Online. Não há uma pouca configuração adicional para obter a consulta à direita, mas as recompensas são obter melhor desempenho e mais satisfeitos usuários.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Comparando o ganho de desempenho obtido usando o Web Part de pesquisa de conteúdo, em vez de Web Part de consulta de conteúdo

Os exemplos a seguir mostram os ganhos de desempenho relativo que poderá receber quando você usar uma Web Part de pesquisa conteúdo em vez de uma Web Part de consulta de conteúdo. Os efeitos são mais óbvios com uma estrutura de site complexo e consultas de conteúdo muito amplas.
  
Este site de exemplo tem as seguintes características:
  
- 8 níveis de subsites.
    
- Lista usando um tipo de conteúdo personalizado "fruta".
    
- Na Web Part, a consulta de conteúdo é ampla, retornando todos os itens com o tipo de conteúdo de "frutas".
    
- O exemplo usa apenas 50 itens entre os sites de 8. Os efeitos vai ser ainda mais pronuncia-se para sites com mais de conteúdo.
    
Aqui está uma captura de tela dos resultados da consulta Web Part de conteúdo.
  
![Gráfico que mostra a consulta de conteúdo da web part](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
No Internet Explorer, use a guia de **rede** das ferramentas de desenvolvedor do F12 para ver os detalhes para o cabeçalho de resposta. Na seguinte captura de tela, o valor para o **SPRequestDuration** essa carga de página é 924 milissegundos. 
  
![Captura de tela mostrando a duração da solicitação de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** indica a quantidade de trabalho que é feito no servidor para preparar a página. Alternar o conteúdo por Web Parts de consulta com conteúdo por Web Parts de pesquisa drasticamente reduz o tempo que leva para renderizar a página. Por outro lado, uma página com uma Web Part equivalentes de pesquisa conteúdo, retornar o mesmo número de resultados possui um valor de **SPRequestDuration** de 106 milissegundos, conforme mostrado na captura de tela a este: 
  
![Captura de tela mostrando a Duração da Solicitação de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Adicionar uma Web Part de pesquisa de conteúdo no SharePoint Online

Adicionar uma Web Part de pesquisa conteúdo é muito semelhante a uma Web Part regular do consulta de conteúdo. Consulte a seção *"adicionar um conteúdo Web Part de pesquisa"* em [Configure um Web Part conteúdo de pesquisa no SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Criando a consulta de pesquisa correta para o seu conteúdo Web Part de pesquisa

Depois de adicionar uma Web Part de pesquisa conteúdo, você pode refinar a pesquisa e retornar os itens que você deseja. Para obter instruções detalhadas sobre como fazer isso, consulte a seção, *"Content de exibição, definindo uma consulta avançada em uma Web Part de pesquisa conteúdo"* em [Configure uma Web Part de pesquisa de conteúdo no SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Criar e testar a ferramenta de consulta

Para uma ferramenta criar e testar consultas complexas, consulte a [Ferramenta de consulta de pesquisa](https://sp2013searchtool.codeplex.com/) no Codeplex. 
  

