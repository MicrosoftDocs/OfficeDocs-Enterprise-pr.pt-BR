---
title: Atraso no carregamento de imagens e JavaScript no SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: Este artigo descreve como você pode reduzir o tempo de carregamento de páginas do SharePoint Online usando o JavaScript atrasar o carregamento de imagens e também aguardando carregar JavaScript não essenciais até após a página for carregada.
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539373"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="c28f5-103">Atraso no carregamento de imagens e JavaScript no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c28f5-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="c28f5-104">Este artigo descreve como você pode reduzir o tempo de carregamento de páginas do SharePoint Online usando o JavaScript atrasar o carregamento de imagens e também aguardando carregar JavaScript não essenciais até após a página for carregada.</span><span class="sxs-lookup"><span data-stu-id="c28f5-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="c28f5-p101">As imagens podem afetar negativamente as velocidades de carregamento de página no SharePoint Online. Por padrão, os navegadores mais modernos da Internet buscam previamente as imagens ao carregar uma página HTML. Isso pode fazer com que a página fique desnecessariamente lenta ao carregar, se as imagens não estiverem visíveis até que o usuário role a tela para baixo. As imagens podem bloquear o navegador no carregamento da parte visível da página. Para contornar esse problema, você pode usar o JavaScript para ignorar o carregamento de imagens primeiro. Além disso, carregar JavaScript dispensáveis pode retardar os tempos de carregamento nas suas páginas do SharePoint também. Este tópico descreve alguns métodos que podem ser usados para melhorar os tempos de carregamento de página com o JavaScript no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c28f5-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="c28f5-112">Melhore os tempos de carregamento de página atrasando o carregamento de imagens nas páginas do SharePoint Online usando o JavaScript</span><span class="sxs-lookup"><span data-stu-id="c28f5-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="c28f5-p102">Você pode usar o JavaScript para impedir que um navegador da web de imagens previamente ao buscar. Isso acelera o processamento de documentos geral. Para fazer isso, você remover o valor do atributo src do \<img\> marcar e substituí-lo com o caminho para um arquivo em um atributo de dados, como: src de dados. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c28f5-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="c28f5-p103">Ao usar esse método, o navegador não baixar as imagens imediatamente. Se a imagem já estiver no visor, JavaScript informa ao navegador para recuperar a URL no atributo de dados e inseri-lo como o valor para o atributo src. A imagem carrega apenas como o usuário rolar e ele entra em modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c28f5-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="c28f5-119">Para fazer tudo isso acontecer, você precisará usar o JavaScript.</span><span class="sxs-lookup"><span data-stu-id="c28f5-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="c28f5-120">Em um arquivo de texto, defina a função **isElementInViewport()** para verificar se um elemento é ou não parte do navegador que é visível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="c28f5-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
```
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth) 
  );
}

```

<span data-ttu-id="c28f5-p104">Em seguida, use **isElementInViewport()** na função **loadItemsInView()**. A função **loadItemsInView()** carregará todas as imagens que tenham um valor para o atributo de data-src, se elas estiverem na parte do navegador que é visível para o usuário. Adicione a seguinte função no arquivo de texto:</span><span class="sxs-lookup"><span data-stu-id="c28f5-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
```
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

<span data-ttu-id="c28f5-p105">Finalmente, chame **loadItemsInView()** de **window.onscroll()**, conforme mostrado no exemplo a seguir. Isso garante que as imagens que estão no visor sejam carregadas quando o usuário precisar delas, mas não antes. Adicione o seguinte no arquivo de texto:</span><span class="sxs-lookup"><span data-stu-id="c28f5-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="c28f5-p106">Para o SharePoint Online, você precisa anexar a função a seguir para o evento scroll em #s4-espaço de trabalho \<div\> marca. Isso ocorre porque os eventos de janela são substituídos para garantir que a faixa de opções continua conectada para o topo da página.</span><span class="sxs-lookup"><span data-stu-id="c28f5-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="c28f5-129">Salve o arquivo de texto como um arquivo JavaScript com a extensão .js, por exemplo, atrasarCarregamentoDeImagens.js.</span><span class="sxs-lookup"><span data-stu-id="c28f5-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="c28f5-p107">Depois que você tiver terminado de escrever delayLoadImages.js, você pode adicionar o conteúdo do arquivo a uma página mestra no SharePoint Online. Para fazer isso, adicionando um link de script para o cabeçalho da página mestra. Quando ele estiver em uma página mestra, o JavaScript será aplicado a todas as páginas no site do SharePoint Online que usam o layout da página mestra. Como alternativa, se você pretende usar isso somente em uma página do seu site, use o Web Part do editor de scripts integrar o JavaScript na página. Consulte estes tópicos para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="c28f5-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="c28f5-135">Como: aplicar uma página mestra a um site no SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c28f5-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="c28f5-136">Como: criar um layout de página no SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c28f5-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="c28f5-137">**Exemplo: fazendo referência ao arquivo JavaScript atrasarCarregamentoDeImagens.js de uma página mestra no SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="c28f5-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="c28f5-p108">Para isso funcionar, é também necessário fazer referência à jQuery na página mestra. No exemplo a seguir, é possível ver que no carregamento de página inicial apenas uma imagem é carregada, mas há várias outras na página.</span><span class="sxs-lookup"><span data-stu-id="c28f5-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![Captura de tela mostrando uma imagem carregada na página](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="c28f5-141">A seguinte captura de tela mostra o restante das imagens que são baixadas depois de rolar até o campo de visão.</span><span class="sxs-lookup"><span data-stu-id="c28f5-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![Captura de tela mostrando várias imagens carregadas na página](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="c28f5-p109">Atrasar o carregamento de imagens usando o JavaScript pode ser uma técnica eficaz para aumentar o desempenho. No entanto, se a técnica for aplicada em um site público, os mecanismos de pesquisa não serão capazes de rastrear as imagens da mesma forma que rastreariam uma imagem formada regularmente. Isso pode afetar as classificações nos mecanismos de pesquisa, porque os metadados da imagem em si não estão realmente lá até que a página seja carregada. Os rastreadores de mecanismos de pesquisa leem apenas o HTML e, portanto, não verão as imagens como conteúdo na página. As imagens são um dos fatores usados para classificar páginas nos resultados da pesquisa. Uma maneira de contornar isso é usar um texto introdutório para suas imagens.</span><span class="sxs-lookup"><span data-stu-id="c28f5-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="c28f5-148">Exemplo de código do GitHub: Injetando JavaScript para aprimorar o desempenho</span><span class="sxs-lookup"><span data-stu-id="c28f5-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="c28f5-149">Não perca o artigo e exemplo de código em [JavaScript injeção](https://go.microsoft.com/fwlink/p/?LinkId=524759) fornecido no GitHub.</span><span class="sxs-lookup"><span data-stu-id="c28f5-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c28f5-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="c28f5-150">See also</span></span>

[<span data-ttu-id="c28f5-151">Navegadores com suporte no Office 2013 e Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="c28f5-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="c28f5-152">Como: aplicar uma página mestra a um site no SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c28f5-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="c28f5-153">Como: criar um layout de página no SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c28f5-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

