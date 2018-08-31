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
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539290"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Usando o cache de objetos com o SharePoint Online

Este artigo explica a diferença entre usar o cache de objetos no SharePoint Server 2013 no local e o SharePoint Online.
  
Há um impacto negativo significativo em depender do cache de objetos na implantação do SharePoint Online. Qualquer dependência do cache de objetos no SharePoint Online reduzirá a confiabilidade da sua página. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Como o SharePoint Online e o SharePoint Server 2013 objeto cache funciona

Quando o SharePoint Server 2013 estiver hospedado no local, o cliente tem servidores web front-end privada que hospedam o cache de objetos. Isso significa que o cache é dedicado a um cliente e é limitado apenas pela quantidade de memória está disponível e ser alocado para o cache de objetos. Porque apenas um cliente sejam atendido no cenário local nos servidores web front-end geralmente têm usuários fazendo solicitações para os mesmos sites repetidamente. Isso significa que o cache obtém completo rapidamente e permanece completo dos resultados de consulta de lista e objetos do SharePoint que seus usuários estão solicitando regularmente.
  
![Mostra o tráfego e a carga para servidores front-end da Web locais](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Como resultado, na segunda vez que um usuário visita uma página, o tempo de carregamento da página aumenta. Após um mínimo de quatro carregamentos da mesma página, ela é armazenada em cache em todos os servidores front-end da Web.
  
Por outro lado, no SharePoint Online, há muitos mais servidores, mas também muitos sites mais. Todos os usuários podem se conectar a um servidor web front-end diferente que não tem o cache preenchido. Ou, talvez o cache obter preenchido para um servidor, mas o usuário próximo a esse servidor web front-end solicita uma página de um site diferente. Ou, mesmo se o próximo usuário solicita a mesma página nos seus visita anterior, eles estarão com balanceamento de carga para um servidor web front-end diferente que não tem essa página em seu cache. Nesse último caso, o cache não ajuda os usuários em todas as.
  
Na figura a seguir, cada ponto representa uma página que um usuário está solicitando e onde ela é armazenada em cache. Cores diferentes representam diferentes clientes fazendo uso compartilhado da infraestrutura SaaS.
  
![Mostra os resultados do cache de objeto no SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Como você pode ver do diagrama, as chances de qualquer usuário determinado do visitando um servidor com a versão em cache da sua página são mínimas. Além disso, devido ao fato de que os servidores são compartilhados entre muitos sites e taxa de transferência grande, o cache não dura tempo, desde que apenas um pouco espaço para armazenar em cache está disponível.
  
Por todos esses motivos, confiar que os usuários obtenham objetos em cache não é uma maneira eficaz de assegurar uma experiência de usuário e um carregamento de página de qualidade no SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Se não é possível confiar no cache de objetos para melhorar o desempenho no SharePoint Online, o que devemos usar?

Já que não é possível confiar no cache no SharePoint Online, você deve avaliar as abordagens de design alternativo para personalizações do SharePoint que usam o cache de objetos. Isso significa usar abordagens para problemas de desempenho que não dependem do cache de objetos para produzir bons resultados para os usuários. Isso é descrito em alguns outros artigos desta série e inclui:
  
- [Opções de navegação para o SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minificação e agrupamento no SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Usando redes de distribuição de conteúdo](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Atraso no carregamento de imagens e JavaScript no SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

