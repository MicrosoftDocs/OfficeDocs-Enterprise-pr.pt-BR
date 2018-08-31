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
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Atraso no carregamento de imagens e JavaScript no SharePoint Online

Este artigo descreve como você pode reduzir o tempo de carregamento de páginas do SharePoint Online usando o JavaScript atrasar o carregamento de imagens e também aguardando carregar JavaScript não essenciais até após a página for carregada. 
  
As imagens podem afetar negativamente as velocidades de carregamento de página no SharePoint Online. Por padrão, os navegadores mais modernos da Internet buscam previamente as imagens ao carregar uma página HTML. Isso pode fazer com que a página fique desnecessariamente lenta ao carregar, se as imagens não estiverem visíveis até que o usuário role a tela para baixo. As imagens podem bloquear o navegador no carregamento da parte visível da página. Para contornar esse problema, você pode usar o JavaScript para ignorar o carregamento de imagens primeiro. Além disso, carregar JavaScript dispensáveis pode retardar os tempos de carregamento nas suas páginas do SharePoint também. Este tópico descreve alguns métodos que podem ser usados para melhorar os tempos de carregamento de página com o JavaScript no SharePoint Online. 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Melhore os tempos de carregamento de página atrasando o carregamento de imagens nas páginas do SharePoint Online usando o JavaScript

Você pode usar o JavaScript para impedir que um navegador da web de imagens previamente ao buscar. Isso acelera o processamento de documentos geral. Para fazer isso, você remover o valor do atributo src do \<img\> marcar e substituí-lo com o caminho para um arquivo em um atributo de dados, como: src de dados. Por exemplo:
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Ao usar esse método, o navegador não baixar as imagens imediatamente. Se a imagem já estiver no visor, JavaScript informa ao navegador para recuperar a URL no atributo de dados e inseri-lo como o valor para o atributo src. A imagem carrega apenas como o usuário rolar e ele entra em modo de exibição.
  
Para fazer tudo isso acontecer, você precisará usar o JavaScript.
  
Em um arquivo de texto, defina a função **isElementInViewport()** para verificar se um elemento é ou não parte do navegador que é visível para o usuário. 
  
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

Em seguida, use **isElementInViewport()** na função **loadItemsInView()**. A função **loadItemsInView()** carregará todas as imagens que tenham um valor para o atributo de data-src, se elas estiverem na parte do navegador que é visível para o usuário. Adicione a seguinte função no arquivo de texto: 
  
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

Finalmente, chame **loadItemsInView()** de **window.onscroll()**, conforme mostrado no exemplo a seguir. Isso garante que as imagens que estão no visor sejam carregadas quando o usuário precisar delas, mas não antes. Adicione o seguinte no arquivo de texto: 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Para o SharePoint Online, você precisa anexar a função a seguir para o evento scroll em #s4-espaço de trabalho \<div\> marca. Isso ocorre porque os eventos de janela são substituídos para garantir que a faixa de opções continua conectada para o topo da página.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Salve o arquivo de texto como um arquivo JavaScript com a extensão .js, por exemplo, atrasarCarregamentoDeImagens.js.
  
Depois que você tiver terminado de escrever delayLoadImages.js, você pode adicionar o conteúdo do arquivo a uma página mestra no SharePoint Online. Para fazer isso, adicionando um link de script para o cabeçalho da página mestra. Quando ele estiver em uma página mestra, o JavaScript será aplicado a todas as páginas no site do SharePoint Online que usam o layout da página mestra. Como alternativa, se você pretende usar isso somente em uma página do seu site, use o Web Part do editor de scripts integrar o JavaScript na página. Consulte estes tópicos para obter mais informações:
  
- [Como: aplicar uma página mestra a um site no SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Como: criar um layout de página no SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Exemplo: fazendo referência ao arquivo JavaScript atrasarCarregamentoDeImagens.js de uma página mestra no SharePoint Online**
  
Para isso funcionar, é também necessário fazer referência à jQuery na página mestra. No exemplo a seguir, é possível ver que no carregamento de página inicial apenas uma imagem é carregada, mas há várias outras na página.
  
![Captura de tela mostrando uma imagem carregada na página](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
A seguinte captura de tela mostra o restante das imagens que são baixadas depois de rolar até o campo de visão.
  
![Captura de tela mostrando várias imagens carregadas na página](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Atrasar o carregamento de imagens usando o JavaScript pode ser uma técnica eficaz para aumentar o desempenho. No entanto, se a técnica for aplicada em um site público, os mecanismos de pesquisa não serão capazes de rastrear as imagens da mesma forma que rastreariam uma imagem formada regularmente. Isso pode afetar as classificações nos mecanismos de pesquisa, porque os metadados da imagem em si não estão realmente lá até que a página seja carregada. Os rastreadores de mecanismos de pesquisa leem apenas o HTML e, portanto, não verão as imagens como conteúdo na página. As imagens são um dos fatores usados para classificar páginas nos resultados da pesquisa. Uma maneira de contornar isso é usar um texto introdutório para suas imagens.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>Exemplo de código do GitHub: Injetando JavaScript para aprimorar o desempenho

Não perca o artigo e exemplo de código em [JavaScript injeção](https://go.microsoft.com/fwlink/p/?LinkId=524759) fornecido no GitHub. 
  
## <a name="see-also"></a>Confira também

[Navegadores com suporte no Office 2013 e Office 365 ProPlus](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Como: aplicar uma página mestra a um site no SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Como: criar um layout de página no SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

