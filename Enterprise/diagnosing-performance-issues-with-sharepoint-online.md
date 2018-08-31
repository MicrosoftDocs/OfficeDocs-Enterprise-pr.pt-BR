---
title: Diagnosticando problemas de desempenho no SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: Este artigo mostra como você pode diagnosticar problemas comuns com o seu site do SharePoint Online usando as ferramentas de desenvolvedor do Internet Explorer.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539292"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnosticando problemas de desempenho no SharePoint Online

Este artigo mostra como você pode diagnosticar problemas comuns com o seu site do SharePoint Online usando as ferramentas de desenvolvedor do Internet Explorer.
  
Há três maneiras diferentes de identificar que uma página em um site do SharePoint Online tem um problema de desempenho com as personalizações.
  
- O monitor de rede da barra de ferramentas F12
    
- Comparação com uma linha de base não personalizada
    
- Métricas de cabeçalho de resposta do SharePoint Online
    
Este tópico descreve como usar cada um desses métodos para diagnosticar problemas de desempenho. Depois que você calculou a causa do problema, você pode trabalhar em direção de uma solução usando os artigos sobre como melhorar o desempenho do SharePoint que podem ser encontradas em http://aka.ms/tune.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Usando a barra de ferramentas F12 para diagnosticar o desempenho no SharePoint Online
<a name="F12ToolInfo"> </a>

Neste artigo, usamos o Internet Explorer 11. As versões das ferramentas de desenvolvedor F12 em outros navegadores possuem recursos semelhantes, embora possam parecer um pouco diferentes. Para saber mais sobre as ferramentas de desenvolvedor F12, consulte:
  
- [O que há de novo nas ferramentas F12](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [Usando as ferramentas de desenvolvedor F12](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
Para exibir as ferramentas de desenvolvedor, pressione **F12** e, em seguida, clique no ícone de Wi-Fi: 
 
  
![Captura de tela de ícone de Wi-Fi de ferramentas de desenvolvedor F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
Na guia **Rede**, pressione o botão Reproduzir verde para carregar uma página. A ferramenta retorna todos os arquivos que o navegador solicita para obter a página que você requisitou. A captura de tela a seguir mostra uma dessas listas. 
  
![Captura de tela da lista de arquivos retornados com uma solicitação de página.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Você também pode ver os tempos de download de arquivos no lado direito, como mostra a captura de tela.
  
![Diagrama mostrando o tempo de carregamento das páginas solicitadas do SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Isso oferece uma representação visual de quanto tempo o arquivo levou para ser carregado. A linha verde representa quando a página está pronta para ser processada pelo navegador. Isso pode fornecer uma visualização rápida dos diferentes arquivos que podem estar causando carregamentos de página lentos no seu site.


  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Configurando uma linha de base não personalizada para o SharePoint Online
<a name="F12ToolInfo"> </a>

Configurar um conjunto de sites de completamente-de-imediata no SharePoint Online é a melhor maneira de determinar os pontos fracos do desempenho do seu site. Dessa forma você pode comparar todos os vários aspectos do seu site com obtido sem personalização na página. O OneDrive for Business home page é um bom exemplo de um conjunto de sites separado é improvável que tenha todas as personalizações.
  
## <a name="viewing-sharepoint-response-header-information"></a>Exibindo informações de cabeçalho de resposta do SharePoint
<a name="F12ToolInfo"> </a>

No SharePoint Online e no SharePoint Server 2013, é possível acessar as informações enviadas ao navegador no cabeçalho de resposta de cada arquivo. Os dois valores mais úteis para diagnosticar problemas de desempenho são SPRequestDuration e X-SharePointHealthScore:
  
- **SPRequestDuration**
    
    Esse é o período de tempo que a solicitação demorou para ser processada no servidor. Isso pode ajudar a determinar se a solicitação é muito pesada e se faz uso intensivo de recursos. É a sua melhor percepção sobre a quantidade de trabalho que o servidor tem para atender a página.
    
- **X-SharePointHealthScore**
    
    Isso indica que a utilização do servidor, ou CPU, no qual sua instância do SharePoint é executado. Este intervalos de números de 0 a 10, onde 0 indica que o servidor está ocioso e 10 indica que o servidor está muito ocupado. Uma pontuação de integridade é consistentemente 9 ou 10 pode indicar um problema de desempenho em andamento com o servidor. Qualquer outro número indica que o servidor está funcionando no intervalo esperado.
    
 **Para exibir informações de cabeçalho de resposta do SharePoint**
  
1. Certifique-se de que você tenha as ferramentas F12 instaladas. Para obter mais informações sobre como baixar e instalar essas ferramentas, consulte [o que há de novo nas ferramentas de F12](https://go.microsoft.com/fwlink/p/?LinkId=522545).
    
2. Em ferramentas F12, na guia **Rede**, pressione o botão Reproduzir verde para carregar uma página. 
    
3. Clique em um dos arquivos .aspx retornados pela ferramenta e, em seguida, clique em **DETALHES**. 
    
    ![Mostra detalhes do cabeçalho de resposta](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Clique em **Cabeçalhos de resposta**. 
    
    ![Diagrama mostrando a URL do cabeçalho de resposta](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>O que está causando problemas de desempenho no SharePoint Online?
<a name="F12ToolInfo"> </a>

O artigo [Opções de navegação para o SharePoint Online](navigation-options-for-sharepoint-online.md) mostra um exemplo de usando o valor de SPRequestDuration para determinar a navegação estrutural complicada estava fazendo com que a página para levar muito tempo para processar no servidor. De acordo com um valor para um site de linha de base (sem personalização), é possível determinar se qualquer tipo de arquivo está demorando muito tempo para carregar. O exemplo usado em [Opções de navegação para o SharePoint Online](navigation-options-for-sharepoint-online.md) é o arquivo. aspx principal. Esse arquivo contém a maioria do código ASP.NET que executa sua carga de página. Dependendo do modelo de site que você use, isso poderia ser start.aspx, aspx, default. aspx ou outro nome se você personalizar a home page. Se esse número for consideravelmente maior do que o seu site de linha de base, é uma boa indicação de que há algo complexo acontecendo na sua página que está causando problemas de desempenho. 
  
Depois de ter identificado que é um problema específico do seu site, a maneira recomendada para descobrir o que está causando o baixo desempenho é eliminar todas as possíveis causas, como personalizações de página, e adicioná-las uma por uma novamente ao local. Depois de remover personalizações suficientes e a página apresentar bom desempenho, você pode então adicionar personalizações específicas uma por uma novamente.
  
Por exemplo, se você tiver uma navegação muito complexa tente alterar a navegação para não mostrar subsites e verifique as ferramentas de desenvolvedor para ver se isso faz diferença. Ou se você tiver uma grande quantidade de conteúdos acumulados, tente removê-los da página e veja se isso melhora as coisas. Ao eliminar todas as possíveis causas e adicioná-las uma por uma novamente, você pode identificar facilmente quais recursos são o maior problema e procurar uma solução. 

  

