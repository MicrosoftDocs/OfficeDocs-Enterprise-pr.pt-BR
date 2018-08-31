---
title: Usando as redes de fornecimento de conteúdo com o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Resumo: Este artigo descreve redes de fornecimento de conteúdo (CDNs) e como você pode usá-los para aumentar o desempenho do SharePoint Online.'
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539248"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Usando as redes de fornecimento de conteúdo com o SharePoint Online

 **Resumo:** Este artigo descreve as redes de fornecimento de conteúdo (CDNs) e como você pode usá-los para aumentar o desempenho do SharePoint Online. 
  
Comunidades de desenvolvimento de web de hoje, há muitas bibliotecas comuns (por exemplo, arquivos JavaScript e CSS) que você pode incluir em sua solução do SharePoint. Muitos deles são hospedados pela Microsoft em seus CDN do ASP. Isso significa que você pode fazer referência a essas bibliotecas desses servidores distribuídos e permitir internas roteamento sistemas DNS da internet localizar o servidor mais próximo ao usuário. Os exemplos neste artigo demonstram como a diferença de horário entre baixando o jQuery populares biblioteca do servidor do SharePoint Online versus a CDN ASP é significativa. O usuário também já pode ter a versão CDN armazenados em cache no computador local para que não têm que baixar o arquivo. Isso pode ser importante se você tiver usuários distribuídos em todo o mundo e longe do data center que hospeda o site do SharePoint Online.
  
Ao criar páginas para o SharePoint Online, a latência pode ser afetada pela distância física entre os usuários e o local da instância do SharePoint Online. Isso é particularmente importante para organizações que possuem presença global, elas podem ter um site hospedado em um continente e usuários do outro lado do mundo acessando seu conteúdo. As CDNs ajudam a atenuar essa situação hospedando determinados ativos populares da Web em diferentes locais próximos aos usuários finais.
  
Como uma CDN é uma rede mundial de servidores que hospeda os mesmos arquivos, as URLs de Internet para arquivos armazenados nas CDNs são interpretadas pelo computador do cliente para que o servidor mais próximo do usuário forneça o arquivo. Isso reduz significativamente os atrasos causados pelas viagens de ida e volta da rede.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>O desafio de hospedar sites do SharePoint Online para um público global

Os sites do SharePoint Online são hospedados em datacenters de acordo com o local (especificado pelo usuário) selecionado quando você se inscreveu com o Office 365. Por exemplo, se seu site estiver em servidores nos Estados Unidos e seus usuários o acessarem do Leste Asiático, podem surgir problemas de latência devido a distância que os dados têm de percorrer no cabo de fibra ótica.
  
Muitos arquivos estáticos usados pela interface do usuário padrão do SharePoint já estiverem hospedados em rede mundial da Microsoft de CDNs. Isso melhora o desempenho ao longo do tempo. No entanto, se você usar qualquer ativos JavaScript e CSS populares (por exemplo; JQuery, Modernizr, Bootstrap ou ASP.NET Ajax), você poderá melhorar os tempos de carregamento desses arquivos usando CDNs disponíveis gratuitamente.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Vantagens de usar as CDNs para melhorar a velocidade de download

Usar as CDNs pode melhorar os tempos de carregamento de página para uma variedade de motivos. Um motivo é que a distância entre a CDN e o usuário pode ser menor do que a distância para a instância do SharePoint Online. Essas redes são altamente distribuídas e também se adequam tenham tempos de resposta e disponibilidade muito altos. Outro motivo é que, se você estiver usando uma biblioteca popular dos arquivos CSS, juntamente com uma CDN, o usuário já disponham de biblioteca do cache e eles ainda não precisam baixá-lo em todos os.
  
As capturas de tela a seguir ilustram as vantagens de usar as CDNs. Essas capturas de tela são a partir da guia **rede** nas ferramentas de desenvolvedor do Internet Explorer 11. Essas capturas de tela mostram a latência no jQuery a biblioteca populares. Para exibir essa tela, no Internet Explorer, pressione a **tecla F12** e selecione a guia de **rede** que é indicada com um ícone de Wi-Fi. 
  
![Captura de tela da Rede F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Esta captura de tela mostra a Biblioteca carregada para a Galeria de páginas mestras no site do SharePoint Online em si. O tempo gasto para carregar a biblioteca é 1.51 segundos.
  
![Captura de tela do tempo de carregamento 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
A segunda captura de tela mostra o mesmo arquivo viabilizado da Microsoft CDN. Neste momento, a latência é cerca 496 milissegundos. Esta é uma grande melhoria e mostra que um segundo todo é eliminou desativa o tempo total para baixar o conteúdo da página.
  
![Captura de tela dos tempos de carregamento em 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Usando as CDNs com o SharePoint Server 2013

Usar as CDNs somente faz sentido em um contexto do SharePoint Online e deve ser evitado with SharePoint Server 2013. Isso acontece porque todas as vantagens em torno de localização geográfica não espera true se o servidor está localizado no local ou geograficamente fechar mesmo assim. Além disso, se houver uma conexão de rede para os servidores onde ele está hospedado, em seguida, o site pode ser usado sem uma conexão de Internet e, portanto, não é possível recuperar os arquivos CDN. Caso contrário, você deve usar uma CDN se houver uma disponível e estável para os arquivos e a biblioteca que você precisa para seu site.
  
## <a name="popular-cdns-and-how-to-use-them"></a>CDNs populares e como usá-las

Ajax CDN da Microsoft oferece a maioria das bibliotecas de populares, incluindo jQuery (e todos os seus outras bibliotecas), ASP.NET Ajax, Bootstrap, Knockout. js e muitos outros.
  
Para incluir esses scripts no seu projeto, basta substituir todas as referências a essas bibliotecas disponíveis publicamente por referências ao endereço CDN, em vez de incluí-la no projeto. Por exemplo, use o código a seguir para vincular à jQuery:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Para obter mais informações sobre as CDNs, consulte [redes de fornecimento de conteúdo](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Mais tópicos sobre como usar as CDNs com o SharePoint

[Parte da web do lado do cliente do Office 365 CDN de hospedagem](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

