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
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minificação e agrupamento no SharePoint Online

Este artigo descreve como usar minimização e agrupando técnicas com Web Essentials para reduzir o número de solicitações HTTP e reduzir o tempo que leva para carregar páginas no SharePoint Online.
  
Ao personalizar seu site, você pode acabar adicionando um grande número de arquivos extras ao servidor para dar suporte à personalização. Adicionar mais imagens, CSS e JavaScript aumenta o número de solicitações HTTP para o servidor, o que aumenta o tempo necessário para exibir uma página da Web. Se tiver vários arquivos do mesmo tipo, você pode agrupá-los para tornar o download mais rápido.
  
Para arquivos JavaScript e CSS, você também pode usar uma abordagem chamada minimização, onde você reduzir o tamanho total dos arquivos, removendo o espaço em branco e outros caracteres que não são necessários.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minificação e agrupamento de arquivos JavaScript e CSS com Web Essentials

Você pode usar softwares de terceiros, como o Web Essentials, para agrupar arquivos CSS e JavaScript.
  
> [!IMPORTANT]
> Web Essentials é um projeto de terceiros, código-fonte aberto, baseadas na comunidade. O software é uma extensão do Visual Studio 2012 e o Visual Studio 2013 e não é suportado pela Microsoft. Para baixar o Web Essentials, visite o site em [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629). 
  
O Web Essentials oferece duas formas de agrupamento:
  
- .bundle: para arquivos CSS e JavaScript
    
- .sprite: para imagens (disponível apenas no Visual Studio 2013)
    
Você pode usar o Web Essentials se tiver um recurso existente com alguns elementos de identidade visual que são referenciados dentro de uma página mestra personalizada, como:
  
![Captura de tela do elemento de marca na página mestra personalizada](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Para criar um pacote TE000127218 e CSS na Web Essentials**
  
1. No Visual Studio, no Gerenciador de Soluções, selecione os arquivos que você deseja incluir no grupo.
    
2. Os arquivos selecionados do mouse em e selecione **Web Essentials** \> o **arquivo de pacote de criar JavaScript** no menu de contexto. Por exemplo: 
    
    ![Captura de tela mostrando as opções do menu Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Exibindo os resultados de agrupamento de arquivos JavaScript e CSS

Quando você cria um grupo de JavaScript e CSS, o Web Essentials cria um arquivo XML chamado arquivo de receita que identifica os arquivos JavaScript e CSS, bem como algumas outras informações de configuração: 
  
![Captura de tela de arquivo de receita JavaScript e CSS](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Além disso, se o sinalizador de minificação for definido como true na receita de agrupamento, os arquivos serão reduzidos em tamanho, bem como agrupados. Isso significa que novas versões minificadas dos arquivos JavaScript foram criadas e podem ser referenciadas na sua página mestra.
  
![Captura de tela do sinalizador minify definido como verdadeiro](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Ao carregar uma página do seu site, você pode usar as ferramentas de desenvolvedor do navegador da Web, como o Internet Explorer 11, para ver o número de solicitações enviadas para o servidor e o tempo de carregamento de cada arquivo.
  
A figura a seguir é o resultado do carregamento dos arquivos JavaScript e CSS antes da minificação.
  
![Captura de tela mostrando 80 itens sendo baixados](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Depois de agrupar os arquivos CSS e JavaScript, o número de solicitações caiu para 74 e cada arquivo demorou apenas um pouco mais do que os arquivos originais para ser baixado individualmente:
  
![Captura de tela mostrando 74 itens sendo baixados](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Depois do agrupamento, o arquivo de grupo do JavaScript foi reduzido significativamente de 815 KB para 365 KB:
  
![Captura de tela mostrando tamanho do download reduzido](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Agrupando imagens criando uma imagem sprite

Semelhante ao como você agrupam os arquivos JavaScript e CSS, você pode combinar muitos ícones pequenos e outras imagens comuns em uma folha de entidade gráfica maior e, em seguida, usar CSS para revelar as imagens individuais. Em vez de fazer o download de cada imagem individual, o navegador da web do usuário baixa a planilha de entidade gráfica uma vez e, em seguida, armazena-os no computador local. Isso melhora o desempenho do carregamento de página, corte para baixo no número de downloads e viagens de ida e para o servidor web.
  
 **Para criar uma imagem sprite no Web Essentials**
  
1. No Visual Studio, no Gerenciador de Soluções, selecione os arquivos que você deseja incluir no grupo.
    
2. Os arquivos selecionados do mouse em e selecione **Web Essentials** \> **entidade gráfica de imagem de criar** , no menu de contexto. Por exemplo: 
    
    ![Captura de tela mostrando como criar uma entidade gráfica de imagem](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Escolha um local para salvar o arquivo sprite. O arquivo .sprite é um arquivo XML que descreve as configurações e os arquivos no sprite. As figuras a seguir mostram um exemplo de um arquivo PNG sprite e seu arquivo XML .sprite correspondente.
    
    ![Captura de tela de um arquivo de entidade gráfica](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Captura de tela de arquivo XML de entidade gráfica](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

