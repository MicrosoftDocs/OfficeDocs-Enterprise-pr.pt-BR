---
title: Otimização de imagem para o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Saiba como usar representações e sprites para melhorar o desempenho de imagem em seus sites do SharePoint Online.
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539158"
---
# <a name="image-optimization-for-sharepoint-online"></a>Otimização de imagem para o SharePoint Online

A velocidade de carregamento de uma página da Web depende do tamanho combinado de todos os componentes necessários para processar a página, incluindo CSS, HTML, JavaScript e imagens. Imagens são uma ótima maneira para tornar seu site mais atraente, mas seu tamanho pode afetar o desempenho. Otimizando suas imagens com a compactação de redimensionamento e uso de sprites, você pode compensar os efeitos das imagens muito grandes. Usando a reprodução de imagens do SharePoint, você pode carregar uma única imagem grande e exibir seções da imagem permitindo que ele ser reutilizados em vez de ser recarregado.
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>Usando sprites para acelerar o carregamento da imagem no SharePoint Online

|||
|:-----|:-----|
| Uma entidade gráfica de imagem contém várias imagens menores. Usando CSS que você selecionar uma parte da imagem composta para exibir uma determinada parte da página com posicionamento absoluto. Basicamente, você mova uma única imagem ao redor da página em vez de carregar várias imagens e tornar uma pequena parte da imagem visíveis por meio de uma pequena janela em que a parte necessária da imagem entidade gráfica é mostrado ao usuário final. SharePoint Online usa sprites para exibir seus vários ícones em spcommon.png a entidade gráfica.  <br/>  O que é abordado aqui:  <br/>  Compactação de imagem  <br/>  Otimização da imagem  <br/>  Reprodução de imagens do SharePoint  <br/> |![Captura de tela de spcommon](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
Isso pode aumentar o desempenho porque você baixe apenas uma imagem em vez de várias e, em seguida, armazenar em cache e reutilizar aquela imagem. Mesmo que a imagem não permanece em cache, estabelecendo uma única imagem, em vez de várias imagens, esse método reduz o número total de solicitações HTTP para o servidor que reduzirá os tempos de carregamento de página. Isso é realmente uma forma de agrupamento de imagem. Essa é uma técnica muito útil se as imagens não estiver alterando com frequência, por exemplo, ícones, conforme mostrado no exemplo SharePoint fornecido acima. Você pode como usar o [Web Essentials](http://vswebessentials.com/), um projeto de terceiros, código-fonte aberto, baseado em comunidades para fazer isto facilmente no Microsoft Visual Studio. Para obter mais informações, consulte [minimização e agrupando no SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>Usando a compactação de imagem e a otimização para acelerar o carregamento de página no SharePoint

A compactação e a otimização de imagem reduzem o tamanho do arquivo das imagens que você usa no seu site. Geralmente, a melhor técnica para reduzir o tamanho de uma imagem é redimensioná-la para as dimensões máximas que serão exibidas no site. Não faz sentido ter uma imagem maior do que o tamanho que ela será exibida. Usar um editor de imagens para garantir que as imagens possuem as dimensões corretas é uma maneira rápida e fácil de reduzir o tamanho da página.
  
Depois que as imagens são no tamanho correto, a próxima etapa é otimizar a compactação dessas imagens. Existem diversas ferramentas disponíveis para serem usados para compactação e otimização, incluindo a Galeria de fotos e ferramentas de terceiros. A tecla a compactação é reduzir o tamanho de arquivo tanto quanto possível sem perder qualquer qualidade perceptível para usuários finais. Certifique-se de que testar seus arquivos compactados em uma exibição de alta definição para garantir que eles ainda parecem bons.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Acelere os downloads da página usando a representação de imagens do SharePoint

Reprodução de imagens é um recurso no SharePoint Online que permite que você atender a diferentes versões de imagens com base nas dimensões de imagem pré-definidos. Isso é especialmente importante quando houver conteúdo da imagem gerados pelo usuário ou as dimensões da imagem, como width e height são corrigidas pelo CSS no site. Mesmo se uma imagem é fixo por CSS, a imagem de uma solução completa é ainda carregada. Nesse caso, o tamanho do arquivo pode ser reduzido usando renderizações de imagem.
  
> [!NOTE]
> Representações só estarão disponíveis para o SharePoint quando a publicação é habilitada. Você pode habilitar a publicação em configurações \> configurações do Site \> gerenciar recursos do site \> publicação do SharePoint Server. A opção não será exibida caso contrário. 
  
O redimensionamento de representações de imagem funciona usando a menor medida que você definiu de largura ou altura e, em seguida, redimensionando a imagem para que a outra medida seja automaticamente redimensionada com base na taxa de proporção bloqueada. Por padrão, ele cortará a imagem a partir do centro pelas dimensões restantes. Por exemplo, se você definir uma representação de 100 px de largura e 50 px de altura e a imagem original tiver 1000 px de largura e 800 px de altura, ela será redimensionada para que a dimensão de 800 px seja agora de 50 px e a dimensão de 1000 px (agora 62,5 px) seja cortada a partir do centro da imagem.
  
As etapas são relativamente simples, mas no caso das imagens a serem usadas para representações, é necessário que as representações estejam no site do SharePoint antes de adicionar as imagens. Além disso, você também precisa ter os recursos de Infraestrutura de Publicação do SharePoint Server (nível de Conjunto de Sites) e recursos de Publicação do SharePoint Server (nível de Site) ativados.
  
 **Adicionar uma representação de imagem para acelerar o carregamento da página**
  
1. Verifique se a conta de usuário que está executando esse procedimento tem, no mínimo, permissões de Design ao site de nível superior do conjunto de sites, e que o site está sendo publicado para uma página da Web.
    
2. Em um navegador da Web, vá para o site de nível superior do conjunto de sites de publicação.
    
3. Escolha o ícone **Configurações**. 
    
4. Na página **Configurações do Site**, na seção **Aparência**, você verá as representações de imagem internas. 
    
    Você pode usar as representações integradas ou escolher **Representações de Imagem** para criar uma nova. 
    
    ![Captura de tela de representação de imagem](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Na página **Representações de Imagem**, escolha **Adicionar novo item**.
    
    ![Captura de tela de Adicionar Novo Item](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Na página **Nova Representação de Imagem**, na caixa **Nome**, digite um nome para a representação. 
    
7. Nas caixas de texto **Largura** e **Altura**, digite a largura e a altura, em pixels, da representação e escolha a opção **Salvar**.
    
    ![Captura de tela do Nome da Representação de Imagem](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>Corte personalizado com representações de imagem no SharePoint

Por padrão, uma representação de imagem é gerada a partir do centro da imagem. Você pode ajustar a representação de imagem para imagens individuais, cortando a parte da imagem que você deseja usar. É possível cortar as imagens individualmente, por representação. Corte as imagens acelera o carregamento usando o cache de blob do SharePoint para criar uma versão da imagem para cada representação da página. Dessa forma, a carga do servidor é reduzida porque a imagem somente é redimensionada uma vez e, em seguida, está pronta para atender aos usuários finais várias vezes. Para obter mais informações sobre como cortar uma representação de imagem, consulte [Cortar uma representação de imagem](https://go.microsoft.com/fwlink/p/?LinkId=525626).
  

