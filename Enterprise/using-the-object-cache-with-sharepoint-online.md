---
title: Usando o cache de objetos com o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: Este artigo explica a diferença entre usar o cache de objetos no SharePoint Server 2013 no local e o SharePoint Online.
ms.openlocfilehash: 59f3a69199893cb367d4d28c0c545ebd9dfd1236
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25769850"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="b0eb9-103">Usando o cache de objetos com o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b0eb9-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="b0eb9-104">Este artigo explica a diferença entre usar o cache de objetos no SharePoint Server 2013 no local e o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="b0eb9-p101">Há um impacto negativo significativo em depender do cache de objetos na implantação do SharePoint Online. Qualquer dependência do cache de objetos no SharePoint Online reduzirá a confiabilidade da sua página.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="b0eb9-107">Como o SharePoint Online e o SharePoint Server 2013 objeto cache funciona</span><span class="sxs-lookup"><span data-stu-id="b0eb9-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="b0eb9-p102">Quando o SharePoint Server 2013 estiver hospedado no local, o cliente tem servidores web front-end privada que hospedam o cache de objetos. Isso significa que o cache é dedicado a um cliente e é limitado apenas pela quantidade de memória está disponível e ser alocado para o cache de objetos. Porque apenas um cliente sejam atendido no cenário local nos servidores web front-end geralmente têm usuários fazendo solicitações para os mesmos sites repetidamente. Isso significa que o cache obtém completo rapidamente e permanece completo dos resultados de consulta de lista e objetos do SharePoint que seus usuários estão solicitando regularmente.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![Mostra o tráfego e a carga para servidores front-end da Web locais](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="b0eb9-p103">Como resultado, na segunda vez que um usuário visita uma página, o tempo de carregamento da página aumenta. Após um mínimo de quatro carregamentos da mesma página, ela é armazenada em cache em todos os servidores front-end da Web.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="b0eb9-p104">Por outro lado, no SharePoint Online, há muitos mais servidores, mas também muitos sites mais. Todos os usuários podem se conectar a um servidor web front-end diferente que não tem o cache preenchido. Ou então, talvez o cache obter preenchido para um servidor, mas o próximo usuário para que solicitações de servidor web front-end uma página de um site diferente. Ou, mesmo se o próximo usuário solicita a mesma página nos seus visita anterior, eles estarão com balanceamento de carga para um servidor web front-end diferente que não tem essa página em seu cache. Nesse último caso, o cache não ajuda os usuários em todas as.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="b0eb9-p105">Na figura a seguir, cada ponto representa uma página que um usuário está solicitando e onde ela é armazenada em cache. Cores diferentes representam diferentes clientes fazendo uso compartilhado da infraestrutura SaaS.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![Mostra os resultados do cache de objeto no SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="b0eb9-p106">Como você pode ver do diagrama, as chances de qualquer usuário determinado do visitando um servidor com a versão em cache da sua página são mínimas. Além disso, devido ao fato de que os servidores são compartilhados entre muitos sites e taxa de transferência grande, o cache não dura tempo, desde que apenas um pouco espaço para armazenar em cache está disponível.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="b0eb9-125">Por todos esses motivos, confiar que os usuários obtenham objetos em cache não é uma maneira eficaz de assegurar uma experiência de usuário e um carregamento de página de qualidade no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="b0eb9-126">Se não é possível confiar no cache de objetos para melhorar o desempenho no SharePoint Online, o que devemos usar?</span><span class="sxs-lookup"><span data-stu-id="b0eb9-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="b0eb9-p107">Já que não é possível confiar no cache no SharePoint Online, você deve avaliar as abordagens de design alternativo para personalizações do SharePoint que usam o cache de objetos. Isso significa usar abordagens para problemas de desempenho que não dependem do cache de objetos para produzir bons resultados para os usuários. Isso é descrito em alguns outros artigos desta série e inclui:</span><span class="sxs-lookup"><span data-stu-id="b0eb9-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="b0eb9-130">Opções de navegação para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b0eb9-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="b0eb9-131">Minificação e agrupamento no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b0eb9-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="b0eb9-132">Usando redes de distribuição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="b0eb9-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="b0eb9-133">Atraso no carregamento de imagens e JavaScript no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b0eb9-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

