---
title: Usando redes de distribuição de conteúdo com o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Resumo: Este artigo descreve o CDNs (redes de distribuição de conteúdo) e como você pode usá-los para aumentar o desempenho do SharePoint Online.'
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070577"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Usando redes de distribuição de conteúdo com o SharePoint Online

 **Resumo:** Este artigo descreve o CDNs (redes de distribuição de conteúdo) e como você pode usá-los para aumentar o desempenho do SharePoint Online. 
  
Nas comunidades de desenvolvimento da Web de hoje, há muitas bibliotecas comuns (como arquivos JavaScript e CSS) que você pode incluir em sua solução do SharePoint. Muitos deles são hospedados pela Microsoft na CDN do ASP. Isso significa que você pode fazer referência a essas bibliotecas desses servidores distribuídos e permitir que os sistemas de roteamento DNS internos da Internet encontrem o servidor mais próximo ao usuário. Os exemplos neste artigo demonstram como a diferença de horário entre baixar o jQuery de biblioteca comum do servidor do SharePoint Online versus a CDN do ASP é muito importante. O usuário também pode já ter a versão de CDN armazenada em cache no computador local, para que não seja necessário baixar o arquivo. Isso pode ser importante se você tiver usuários distribuídos em todo o mundo e distante do datacenter que hospeda seu site do SharePoint Online.
  
Ao criar páginas para o SharePoint Online, a latência pode ser afetada pela distância física entre seus usuários e o local da instância do SharePoint Online. Isso é particularmente importante para as organizações que têm uma presença global onde um site pode ser hospedado em um continente, enquanto os usuários no outro lado do mundo estão acessando seu conteúdo. CDNs ajudam a reduzir essa situação, hospedando certos ativos da Web populares em locais diferentes mais próximos dos usuários finais.
  
Como uma CDN é uma rede mundial de servidores que hospedam os mesmos arquivos, as URLs da Internet para arquivos armazenados no CDNs são interpretadas pela máquina cliente para que o servidor mais próximo ao usuário sirva o arquivo. Isso reduz significativamente os atrasos causados por viagens de ida e segundo.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>O desafio de hospedar sites do SharePoint Online para um público global

Os sites do SharePoint Online são hospedados em data centers em relação ao local (especificado pelo usuário) selecionado quando você se inscreveu no Office 365. Por exemplo, se o seu site estiver nos servidores dos Estados Unidos e você tiver usuários que acessam o site do leste da Ásia, podem surgir problemas de latência devido à distância que os dados têm para viajar pelo cabo de fibra ótica.
  
Muitos arquivos estáticos usados pela interface do usuário padrão do SharePoint já estão hospedados na rede mundial de CDNs da Microsoft. Isso irá melhorar o desempenho ao longo do tempo. No entanto, se você usar quaisquer ativos populares de JavaScript e CSS (por exemplo; JQuery, Modernizr, Bootstrap ou ASP.NET AJAX) você pode melhorar os tempos de carregamento desses arquivos usando o CDNs disponível gratuitamente.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Vantagens de usar o CDNs para melhorar a velocidade de download

O uso do CDNs pode melhorar o tempo de carregamento da página por vários motivos. Um motivo é que a distância entre a CDN e o usuário pode ser menor do que a distância para a instância do SharePoint Online. Essas redes são altamente distribuídas e também são projetadas para ter tempos de resposta e disponibilidade muito altos. Outro motivo é que, se você estiver usando uma biblioteca popular de arquivos CSS, em conjunto com uma CDN, talvez o usuário já tenha a biblioteca armazenada em cache e nem precisará baixá-la.
  
As seguintes capturas de tela ilustram as vantagens de usar o CDNs. Essas capturas de tela são da guia **rede** nas ferramentas de desenvolvedor do Internet Explorer 11. Essas capturas de tela mostram a latência na biblioteca popular jQuery. Para exibir essa tela, no Internet Explorer, pressione **F12** e selecione a guia **rede** que é simbolizada com um ícone de Wi-Fi. 
  
![Captura de tela da Rede F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Esta captura de tela mostra a biblioteca carregada para a Galeria de páginas mestras no próprio site do SharePoint Online. O tempo necessário para carregar a biblioteca é de 1,51 segundos.
  
![Captura de tela do tempo de carregamento 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
A segunda captura de tela mostra o mesmo arquivo entregue pela CDN da Microsoft. Desta vez, a latência é de cerca de 496 milissegundos. Este é um grande aperfeiçoamento e mostra que todo um segundo é Shaved do tempo total para baixar o conteúdo da página.
  
![Captura de tela dos tempos de carregamento em 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Usando o CDNs com o SharePoint Server 2013

O uso do CDNs faz sentido em um contexto do SharePoint Online e deve ser evitado com o SharePoint Server 2013. Isso ocorre porque todas as vantagens em torno do local geográfico não são verdadeiras se o servidor está localizado no local ou geographicly Close, mesmo assim. Além disso, se houver uma conexão de rede com os servidores em que ele está hospedado, o site poderá ser usado sem uma conexão com a Internet e, portanto, não poderá recuperar os arquivos CDN. Caso contrário, você deverá usar uma CDN se houver uma disponível e estável para a biblioteca e os arquivos necessários para o site.
  
## <a name="popular-cdns-and-how-to-use-them"></a>CDNs populares e como usá-los

A CDN Ajax da Microsoft oferece a maioria das bibliotecas populares, incluindo jQuery (e todas as outras bibliotecas), ASP.NET AJAX, Bootstrap, Knockout. js e muito mais.
  
Para incluir esses scripts em seu projeto, basta substituir qualquer referência a essas bibliotecas disponíveis publicamente com referências ao endereço da CDN, em vez de incluí-lo em seu próprio projeto. Por exemplo, use o seguinte código para vincular ao jQuery:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Para obter mais informações sobre o CDNs, consulte [redes de distribuição de conteúdo](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Mais tópicos sobre como usar o CDNs com o SharePoint

[Hospedando Web Part do lado do cliente da CDN do Office 365](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

