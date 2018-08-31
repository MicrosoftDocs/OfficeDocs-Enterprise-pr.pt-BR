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
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="34c8a-103">Usando as redes de fornecimento de conteúdo com o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="34c8a-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="34c8a-104">**Resumo:** Este artigo descreve as redes de fornecimento de conteúdo (CDNs) e como você pode usá-los para aumentar o desempenho do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="34c8a-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="34c8a-p101">Comunidades de desenvolvimento de web de hoje, há muitas bibliotecas comuns (por exemplo, arquivos JavaScript e CSS) que você pode incluir em sua solução do SharePoint. Muitos deles são hospedados pela Microsoft em seus CDN do ASP. Isso significa que você pode fazer referência a essas bibliotecas desses servidores distribuídos e permitir internas roteamento sistemas DNS da internet localizar o servidor mais próximo ao usuário. Os exemplos neste artigo demonstram como a diferença de horário entre baixando o jQuery populares biblioteca do servidor do SharePoint Online versus a CDN ASP é significativa. O usuário também já pode ter a versão CDN armazenados em cache no computador local para que não têm que baixar o arquivo. Isso pode ser importante se você tiver usuários distribuídos em todo o mundo e longe do data center que hospeda o site do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="34c8a-p102">Ao criar páginas para o SharePoint Online, a latência pode ser afetada pela distância física entre os usuários e o local da instância do SharePoint Online. Isso é particularmente importante para organizações que possuem presença global, elas podem ter um site hospedado em um continente e usuários do outro lado do mundo acessando seu conteúdo. As CDNs ajudam a atenuar essa situação hospedando determinados ativos populares da Web em diferentes locais próximos aos usuários finais.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="34c8a-p103">Como uma CDN é uma rede mundial de servidores que hospeda os mesmos arquivos, as URLs de Internet para arquivos armazenados nas CDNs são interpretadas pelo computador do cliente para que o servidor mais próximo do usuário forneça o arquivo. Isso reduz significativamente os atrasos causados pelas viagens de ida e volta da rede.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="34c8a-116">O desafio de hospedar sites do SharePoint Online para um público global</span><span class="sxs-lookup"><span data-stu-id="34c8a-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="34c8a-p104">Os sites do SharePoint Online são hospedados em datacenters de acordo com o local (especificado pelo usuário) selecionado quando você se inscreveu com o Office 365. Por exemplo, se seu site estiver em servidores nos Estados Unidos e seus usuários o acessarem do Leste Asiático, podem surgir problemas de latência devido a distância que os dados têm de percorrer no cabo de fibra ótica.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="34c8a-p105">Muitos arquivos estáticos usados pela interface do usuário padrão do SharePoint já estiverem hospedados em rede mundial da Microsoft de CDNs. Isso melhora o desempenho ao longo do tempo. No entanto, se você usar qualquer ativos JavaScript e CSS populares (por exemplo; JQuery, Modernizr, Bootstrap ou ASP.NET Ajax), você poderá melhorar os tempos de carregamento desses arquivos usando CDNs disponíveis gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="34c8a-122">Vantagens de usar as CDNs para melhorar a velocidade de download</span><span class="sxs-lookup"><span data-stu-id="34c8a-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="34c8a-p106">Usar as CDNs pode melhorar os tempos de carregamento de página para uma variedade de motivos. Um motivo é que a distância entre a CDN e o usuário pode ser menor do que a distância para a instância do SharePoint Online. Essas redes são altamente distribuídas e também se adequam tenham tempos de resposta e disponibilidade muito altos. Outro motivo é que, se você estiver usando uma biblioteca popular dos arquivos CSS, juntamente com uma CDN, o usuário já disponham de biblioteca do cache e eles ainda não precisam baixá-lo em todos os.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="34c8a-p107">As capturas de tela a seguir ilustram as vantagens de usar as CDNs. Essas capturas de tela são a partir da guia **rede** nas ferramentas de desenvolvedor do Internet Explorer 11. Essas capturas de tela mostram a latência no jQuery a biblioteca populares. Para exibir essa tela, no Internet Explorer, pressione a **tecla F12** e selecione a guia de **rede** que é indicada com um ícone de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![Captura de tela da Rede F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="34c8a-p108">Esta captura de tela mostra a Biblioteca carregada para a Galeria de páginas mestras no site do SharePoint Online em si. O tempo gasto para carregar a biblioteca é 1.51 segundos.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![Captura de tela do tempo de carregamento 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="34c8a-p109">A segunda captura de tela mostra o mesmo arquivo viabilizado da Microsoft CDN. Neste momento, a latência é cerca 496 milissegundos. Esta é uma grande melhoria e mostra que um segundo todo é eliminou desativa o tempo total para baixar o conteúdo da página.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![Captura de tela dos tempos de carregamento em 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="34c8a-139">Usando as CDNs com o SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="34c8a-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="34c8a-p110">Usar as CDNs somente faz sentido em um contexto do SharePoint Online e deve ser evitado with SharePoint Server 2013. Isso acontece porque todas as vantagens em torno de localização geográfica não espera true se o servidor está localizado no local ou geograficamente fechar mesmo assim. Além disso, se houver uma conexão de rede para os servidores onde ele está hospedado, em seguida, o site pode ser usado sem uma conexão de Internet e, portanto, não é possível recuperar os arquivos CDN. Caso contrário, você deve usar uma CDN se houver uma disponível e estável para os arquivos e a biblioteca que você precisa para seu site.</span><span class="sxs-lookup"><span data-stu-id="34c8a-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="34c8a-144">CDNs populares e como usá-las</span><span class="sxs-lookup"><span data-stu-id="34c8a-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="34c8a-145">Ajax CDN da Microsoft oferece a maioria das bibliotecas de populares, incluindo jQuery (e todos os seus outras bibliotecas), ASP.NET Ajax, Bootstrap, Knockout. js e muitos outros.</span><span class="sxs-lookup"><span data-stu-id="34c8a-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="34c8a-p111">Para incluir esses scripts no seu projeto, basta substituir todas as referências a essas bibliotecas disponíveis publicamente por referências ao endereço CDN, em vez de incluí-la no projeto. Por exemplo, use o código a seguir para vincular à jQuery:</span><span class="sxs-lookup"><span data-stu-id="34c8a-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="34c8a-148">Para obter mais informações sobre as CDNs, consulte [redes de fornecimento de conteúdo](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="34c8a-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="34c8a-149">Mais tópicos sobre como usar as CDNs com o SharePoint</span><span class="sxs-lookup"><span data-stu-id="34c8a-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="34c8a-150">Parte da web do lado do cliente do Office 365 CDN de hospedagem</span><span class="sxs-lookup"><span data-stu-id="34c8a-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

