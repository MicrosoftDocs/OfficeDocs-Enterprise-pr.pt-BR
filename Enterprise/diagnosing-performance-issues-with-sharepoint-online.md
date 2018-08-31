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
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="52a66-103">Diagnosticando problemas de desempenho no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52a66-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="52a66-104">Este artigo mostra como você pode diagnosticar problemas comuns com o seu site do SharePoint Online usando as ferramentas de desenvolvedor do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="52a66-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="52a66-105">Há três maneiras diferentes de identificar que uma página em um site do SharePoint Online tem um problema de desempenho com as personalizações.</span><span class="sxs-lookup"><span data-stu-id="52a66-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="52a66-106">O monitor de rede da barra de ferramentas F12</span><span class="sxs-lookup"><span data-stu-id="52a66-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="52a66-107">Comparação com uma linha de base não personalizada</span><span class="sxs-lookup"><span data-stu-id="52a66-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="52a66-108">Métricas de cabeçalho de resposta do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52a66-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="52a66-p101">Este tópico descreve como usar cada um desses métodos para diagnosticar problemas de desempenho. Depois que você calculou a causa do problema, você pode trabalhar em direção de uma solução usando os artigos sobre como melhorar o desempenho do SharePoint que podem ser encontradas em http://aka.ms/tune.</span><span class="sxs-lookup"><span data-stu-id="52a66-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="52a66-111">Usando a barra de ferramentas F12 para diagnosticar o desempenho no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52a66-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="52a66-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="52a66-112"></span></span>

<span data-ttu-id="52a66-p102">Neste artigo, usamos o Internet Explorer 11. As versões das ferramentas de desenvolvedor F12 em outros navegadores possuem recursos semelhantes, embora possam parecer um pouco diferentes. Para saber mais sobre as ferramentas de desenvolvedor F12, consulte:</span><span class="sxs-lookup"><span data-stu-id="52a66-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="52a66-116">O que há de novo nas ferramentas F12</span><span class="sxs-lookup"><span data-stu-id="52a66-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="52a66-117">Usando as ferramentas de desenvolvedor F12</span><span class="sxs-lookup"><span data-stu-id="52a66-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="52a66-118">Para exibir as ferramentas de desenvolvedor, pressione **F12** e, em seguida, clique no ícone de Wi-Fi: 
</span><span class="sxs-lookup"><span data-stu-id="52a66-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![Captura de tela de ícone de Wi-Fi de ferramentas de desenvolvedor F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="52a66-p103">Na guia **Rede**, pressione o botão Reproduzir verde para carregar uma página. A ferramenta retorna todos os arquivos que o navegador solicita para obter a página que você requisitou. A captura de tela a seguir mostra uma dessas listas.</span><span class="sxs-lookup"><span data-stu-id="52a66-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![Captura de tela da lista de arquivos retornados com uma solicitação de página.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="52a66-124">Você também pode ver os tempos de download de arquivos no lado direito, como mostra a captura de tela.</span><span class="sxs-lookup"><span data-stu-id="52a66-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![Diagrama mostrando o tempo de carregamento das páginas solicitadas do SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="52a66-p104">Isso oferece uma representação visual de quanto tempo o arquivo levou para ser carregado. A linha verde representa quando a página está pronta para ser processada pelo navegador. Isso pode fornecer uma visualização rápida dos diferentes arquivos que podem estar causando carregamentos de página lentos no seu site.

</span><span class="sxs-lookup"><span data-stu-id="52a66-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="52a66-129">Configurando uma linha de base não personalizada para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52a66-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="52a66-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="52a66-130"></span></span>

<span data-ttu-id="52a66-p105">Configurar um conjunto de sites de completamente-de-imediata no SharePoint Online é a melhor maneira de determinar os pontos fracos do desempenho do seu site. Dessa forma você pode comparar todos os vários aspectos do seu site com obtido sem personalização na página. O OneDrive for Business home page é um bom exemplo de um conjunto de sites separado é improvável que tenha todas as personalizações.</span><span class="sxs-lookup"><span data-stu-id="52a66-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="52a66-134">Exibindo informações de cabeçalho de resposta do SharePoint</span><span class="sxs-lookup"><span data-stu-id="52a66-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="52a66-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="52a66-135"></span></span>

<span data-ttu-id="52a66-p106">No SharePoint Online e no SharePoint Server 2013, é possível acessar as informações enviadas ao navegador no cabeçalho de resposta de cada arquivo. Os dois valores mais úteis para diagnosticar problemas de desempenho são SPRequestDuration e X-SharePointHealthScore:</span><span class="sxs-lookup"><span data-stu-id="52a66-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="52a66-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="52a66-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="52a66-p107">Esse é o período de tempo que a solicitação demorou para ser processada no servidor. Isso pode ajudar a determinar se a solicitação é muito pesada e se faz uso intensivo de recursos. É a sua melhor percepção sobre a quantidade de trabalho que o servidor tem para atender a página.</span><span class="sxs-lookup"><span data-stu-id="52a66-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="52a66-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="52a66-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="52a66-p108">Isso indica que a utilização do servidor, ou CPU, no qual sua instância do SharePoint é executado. Este intervalos de números de 0 a 10, onde 0 indica que o servidor está ocioso e 10 indica que o servidor está muito ocupado. Uma pontuação de integridade é consistentemente 9 ou 10 pode indicar um problema de desempenho em andamento com o servidor. Qualquer outro número indica que o servidor está funcionando no intervalo esperado.</span><span class="sxs-lookup"><span data-stu-id="52a66-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="52a66-147">**Para exibir informações de cabeçalho de resposta do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="52a66-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="52a66-p109">Certifique-se de que você tenha as ferramentas F12 instaladas. Para obter mais informações sobre como baixar e instalar essas ferramentas, consulte [o que há de novo nas ferramentas de F12](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span><span class="sxs-lookup"><span data-stu-id="52a66-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="52a66-150">Em ferramentas F12, na guia **Rede**, pressione o botão Reproduzir verde para carregar uma página.</span><span class="sxs-lookup"><span data-stu-id="52a66-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="52a66-151">Clique em um dos arquivos .aspx retornados pela ferramenta e, em seguida, clique em **DETALHES**.</span><span class="sxs-lookup"><span data-stu-id="52a66-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![Mostra detalhes do cabeçalho de resposta](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="52a66-153">Clique em **Cabeçalhos de resposta**.</span><span class="sxs-lookup"><span data-stu-id="52a66-153">Click **Response headers**.</span></span> 
    
    ![Diagrama mostrando a URL do cabeçalho de resposta](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="52a66-155">O que está causando problemas de desempenho no SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="52a66-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="52a66-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="52a66-156"></span></span>

<span data-ttu-id="52a66-p110">O artigo [Opções de navegação para o SharePoint Online](navigation-options-for-sharepoint-online.md) mostra um exemplo de usando o valor de SPRequestDuration para determinar a navegação estrutural complicada estava fazendo com que a página para levar muito tempo para processar no servidor. De acordo com um valor para um site de linha de base (sem personalização), é possível determinar se qualquer tipo de arquivo está demorando muito tempo para carregar. O exemplo usado em [Opções de navegação para o SharePoint Online](navigation-options-for-sharepoint-online.md) é o arquivo. aspx principal. Esse arquivo contém a maioria do código ASP.NET que executa sua carga de página. Dependendo do modelo de site que você use, isso poderia ser start.aspx, aspx, default. aspx ou outro nome se você personalizar a home page. Se esse número for consideravelmente maior do que o seu site de linha de base, é uma boa indicação de que há algo complexo acontecendo na sua página que está causando problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="52a66-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="52a66-p111">Depois de ter identificado que é um problema específico do seu site, a maneira recomendada para descobrir o que está causando o baixo desempenho é eliminar todas as possíveis causas, como personalizações de página, e adicioná-las uma por uma novamente ao local. Depois de remover personalizações suficientes e a página apresentar bom desempenho, você pode então adicionar personalizações específicas uma por uma novamente.</span><span class="sxs-lookup"><span data-stu-id="52a66-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="52a66-p112">Por exemplo, se você tiver uma navegação muito complexa tente alterar a navegação para não mostrar subsites e verifique as ferramentas de desenvolvedor para ver se isso faz diferença. Ou se você tiver uma grande quantidade de conteúdos acumulados, tente removê-los da página e veja se isso melhora as coisas. Ao eliminar todas as possíveis causas e adicioná-las uma por uma novamente, você pode identificar facilmente quais recursos são o maior problema e procurar uma solução. 
</span><span class="sxs-lookup"><span data-stu-id="52a66-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

