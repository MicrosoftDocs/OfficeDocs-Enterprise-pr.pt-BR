---
title: Minificação e agrupamento no SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: Este artigo descreve como usar minimização e agrupando técnicas com Web Essentials para reduzir o número de solicitações HTTP e reduzir o tempo que leva para carregar páginas no SharePoint Online.
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539123"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="66d5f-103">Minificação e agrupamento no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="66d5f-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="66d5f-104">Este artigo descreve como usar minimização e agrupando técnicas com Web Essentials para reduzir o número de solicitações HTTP e reduzir o tempo que leva para carregar páginas no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="66d5f-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="66d5f-p101">Ao personalizar seu site, você pode acabar adicionando um grande número de arquivos extras ao servidor para dar suporte à personalização. Adicionar mais imagens, CSS e JavaScript aumenta o número de solicitações HTTP para o servidor, o que aumenta o tempo necessário para exibir uma página da Web. Se tiver vários arquivos do mesmo tipo, você pode agrupá-los para tornar o download mais rápido.</span><span class="sxs-lookup"><span data-stu-id="66d5f-p101">When you customize your website you can end up adding a large number of extra files to the server to support the customization. Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page. If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="66d5f-108">Para arquivos JavaScript e CSS, você também pode usar uma abordagem chamada minimização, onde você reduzir o tamanho total dos arquivos, removendo o espaço em branco e outros caracteres que não são necessários.</span><span class="sxs-lookup"><span data-stu-id="66d5f-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="66d5f-109">Minificação e agrupamento de arquivos JavaScript e CSS com Web Essentials</span><span class="sxs-lookup"><span data-stu-id="66d5f-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="66d5f-110">Você pode usar softwares de terceiros, como o Web Essentials, para agrupar arquivos CSS e JavaScript.</span><span class="sxs-lookup"><span data-stu-id="66d5f-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="66d5f-p102">Web Essentials é um projeto de terceiros, código-fonte aberto, baseadas na comunidade. O software é uma extensão do Visual Studio 2012 e o Visual Studio 2013 e não é suportado pela Microsoft. Para baixar o Web Essentials, visite o site em [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span><span class="sxs-lookup"><span data-stu-id="66d5f-p102">Web Essentials is a third-party, open-source, community-based project. The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft. To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="66d5f-114">O Web Essentials oferece duas formas de agrupamento:</span><span class="sxs-lookup"><span data-stu-id="66d5f-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="66d5f-115">.bundle: para arquivos CSS e JavaScript</span><span class="sxs-lookup"><span data-stu-id="66d5f-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="66d5f-116">.sprite: para imagens (disponível apenas no Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="66d5f-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="66d5f-117">Você pode usar o Web Essentials se tiver um recurso existente com alguns elementos de identidade visual que são referenciados dentro de uma página mestra personalizada, como:</span><span class="sxs-lookup"><span data-stu-id="66d5f-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![Captura de tela do elemento de marca na página mestra personalizada](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="66d5f-119">**Para criar um pacote TE000127218 e CSS na Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="66d5f-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="66d5f-120">No Visual Studio, no Gerenciador de Soluções, selecione os arquivos que você deseja incluir no grupo.</span><span class="sxs-lookup"><span data-stu-id="66d5f-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="66d5f-p103">Os arquivos selecionados do mouse em e selecione **Web Essentials** \> o **arquivo de pacote de criar JavaScript** no menu de contexto. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="66d5f-p103">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu. For example:</span></span> 
    
    ![Captura de tela mostrando as opções do menu Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="66d5f-124">Exibindo os resultados de agrupamento de arquivos JavaScript e CSS</span><span class="sxs-lookup"><span data-stu-id="66d5f-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="66d5f-125">Quando você cria um grupo de JavaScript e CSS, o Web Essentials cria um arquivo XML chamado arquivo de receita que identifica os arquivos JavaScript e CSS, bem como algumas outras informações de configuração:</span><span class="sxs-lookup"><span data-stu-id="66d5f-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![Captura de tela de arquivo de receita JavaScript e CSS](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="66d5f-p104">Além disso, se o sinalizador de minificação for definido como true na receita de agrupamento, os arquivos serão reduzidos em tamanho, bem como agrupados. Isso significa que novas versões minificadas dos arquivos JavaScript foram criadas e podem ser referenciadas na sua página mestra.</span><span class="sxs-lookup"><span data-stu-id="66d5f-p104">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together. This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Captura de tela do sinalizador minify definido como verdadeiro](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="66d5f-130">Ao carregar uma página do seu site, você pode usar as ferramentas de desenvolvedor do navegador da Web, como o Internet Explorer 11, para ver o número de solicitações enviadas para o servidor e o tempo de carregamento de cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="66d5f-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="66d5f-131">A figura a seguir é o resultado do carregamento dos arquivos JavaScript e CSS antes da minificação.</span><span class="sxs-lookup"><span data-stu-id="66d5f-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![Captura de tela mostrando 80 itens sendo baixados](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="66d5f-133">Depois de agrupar os arquivos CSS e JavaScript, o número de solicitações caiu para 74 e cada arquivo demorou apenas um pouco mais do que os arquivos originais para ser baixado individualmente:</span><span class="sxs-lookup"><span data-stu-id="66d5f-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![Captura de tela mostrando 74 itens sendo baixados](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="66d5f-135">Depois do agrupamento, o arquivo de grupo do JavaScript foi reduzido significativamente de 815 KB para 365 KB:</span><span class="sxs-lookup"><span data-stu-id="66d5f-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![Captura de tela mostrando tamanho do download reduzido](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="66d5f-137">Agrupando imagens criando uma imagem sprite</span><span class="sxs-lookup"><span data-stu-id="66d5f-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="66d5f-p105">Semelhante ao como você agrupam os arquivos JavaScript e CSS, você pode combinar muitos ícones pequenos e outras imagens comuns em uma folha de entidade gráfica maior e, em seguida, usar CSS para revelar as imagens individuais. Em vez de fazer o download de cada imagem individual, o navegador da web do usuário baixa a planilha de entidade gráfica uma vez e, em seguida, armazena-os no computador local. Isso melhora o desempenho do carregamento de página, corte para baixo no número de downloads e viagens de ida e para o servidor web.</span><span class="sxs-lookup"><span data-stu-id="66d5f-p105">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images. Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer. This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="66d5f-141">**Para criar uma imagem sprite no Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="66d5f-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="66d5f-142">No Visual Studio, no Gerenciador de Soluções, selecione os arquivos que você deseja incluir no grupo.</span><span class="sxs-lookup"><span data-stu-id="66d5f-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="66d5f-p106">Os arquivos selecionados do mouse em e selecione **Web Essentials** \> **entidade gráfica de imagem de criar** , no menu de contexto. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="66d5f-p106">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu. For example:</span></span> 
    
    ![Captura de tela mostrando como criar uma entidade gráfica de imagem](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="66d5f-p107">Escolha um local para salvar o arquivo sprite. O arquivo .sprite é um arquivo XML que descreve as configurações e os arquivos no sprite. As figuras a seguir mostram um exemplo de um arquivo PNG sprite e seu arquivo XML .sprite correspondente.</span><span class="sxs-lookup"><span data-stu-id="66d5f-p107">Choose a location to save the sprite file. The .sprite file is an XML file that describes the settings and files in the sprite. The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![Captura de tela de um arquivo de entidade gráfica](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Captura de tela de arquivo XML de entidade gráfica](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

