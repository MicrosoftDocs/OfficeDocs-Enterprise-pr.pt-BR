---
title: Introdução ao ajuste de desempenho para o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: Este artigo explica quais aspectos específicos que você precisa considerar durante a criação de páginas para obter o melhor desempenho no SharePoint Online.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219871"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introdução ao ajuste de desempenho para o SharePoint Online

Este artigo explica quais aspectos específicos que você precisa considerar durante a criação de páginas para obter o melhor desempenho no SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>Métricas do SharePoint Online

As seguintes métricas amplas para o SharePoint Online fornecem dados reais sobre o desempenho:
  
- Velocidade de carregamento das páginas
    
- Quantas viagens de ida e volta são exigidas por página
    
- Problemas com o serviço
    
- Outras questões que causam perda de desempenho
    
### <a name="conclusions-reached-because-of-the-data"></a>Conclusões obtidas com base nos dados

Os dados nos informam que:
  
- a maioria das páginas apresenta um bom desempenho no SharePoint Online.
    
- Páginas não personalizadas carregam rapidamente.
    
- O OneDrive for Business, os sites de equipe e as páginas de sistema, como _layouts, etc., carregam rapidamente.
    
- O 1% mais lento das páginas do SharePoint Online demora mais de 5.000 milissegundos para carregar.
    
Um simples teste de benchmark pode ser usado para medir o desempenho comparando o tempo de carregamento do seu próprio portal ao tempo de carregamento da home page do OneDrive for Business, que usa alguns recursos personalizados. Essa geralmente será a primeira etapa que o Suporte solicitará que você conclua ao solucionar problemas de desempenho de rede.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Usar uma conta de usuário padrão ao verificar o desempenho

Um administrador de conjunto de sites, proprietário do Site, Editor ou colaborador pertencem a grupos de segurança adicional, ter permissões adicionais e, portanto, têm elementos adicionais que carrega do SharePoint em uma página.
  
Isso é aplicável para SharePoint local e o SharePoint Online, mas em um cenário local as diferenças não seja tão facilmente percebidas como no SharePoint Online.
  
Para avaliar corretamente o como uma página executará para usuários, você deve usar uma conta de usuário padrão para evitar o carregamento de criação de controles e tráfego adicional relacionados aos grupos de segurança.
  
## <a name="connection-categories-for-performance-tuning"></a>Categorias de conexão para ajuste de desempenho

Você pode categorizar as conexões entre o servidor e o usuário em três componentes principais. Considere-os durante a criação de páginas do SharePoint Online para obter informações sobre o tempo de carregamento.
  
- **Servidor** Os servidores que a Microsoft hospeda em datacenters.
    
- **Rede** Microsoft network, Internet e sua rede local entre o datacenter e seus usuários.
    
- **Navegador** Onde a página for carregada.
    
Entre essas três conexões normalmente existem cinco motivos que causam 95% das páginas lentas. Cada um destes motivos é discutido neste artigo:
  
- Problemas de navegação
    
- Acúmulo de conteúdo
    
- Arquivos grandes
    
- Muitas solicitações ao servidor
    
- Processamento de Web Part
    
### <a name="server-connection"></a>Conexão do servidor

Muitos dos problemas que afetam o desempenho do SharePoint local também se aplicam ao SharePoint Online.
  
Como esperado, você tem mais controle sobre o desempenho dos servidores com o SharePoint local. Com o SharePoint Online, as coisas são um pouco diferentes. Quanto mais trabalho um servidor recebe, mais tempo ele leva para renderizar uma página. Com o SharePoint, as principais responsáveis nesse sentido são as páginas complexas com várias web parts.
  
SharePoint Server no local
  
![Captura de tela do servidor local](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Captura de tela do servidor online](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Com o SharePoint Online, determinadas solicitações de página podem realmente acabar chamando vários servidores. Você pode acabar com uma matriz de solicitações entre servidores para uma solicitação individual. Estas interações são caras da perspectiva de carregamento da página e tornam o processo mais lento.
  
Exemplos dessas interações de servidor para servidor são:
  
- Web para SQL Servers
    
- Web para servidores de aplicativos
    
Outro aspecto que pode reduzir a velocidade das interações do servidor são os erros de cache. Ao contrário do SharePoint local, há uma chance muito pequena de você atingir o mesmo servidor de uma página visitada anteriormente; isso torna o cache de objeto obsoleto.
  
### <a name="network-connection"></a>Conexão de rede

Com o SharePoint local que não faz uso de uma WAN, você poderá usar uma conexão de alta velocidade entre datacenter e usuários finais. Geralmente, as coisas são fáceis de gerenciar a partir de uma perspectiva de rede.
  
Com o SharePoint Online, há alguns outros fatores a considerar; por exemplo:
  
- A rede da Microsoft
    
- A Internet
    
- O ISP
    
Seja qual for a versão do SharePoint (e da rede) que estiver sendo usada, os motivos que geralmente fazem com que a rede esteja ocupada incluem:
  
- Grande carga
    
- Muitos arquivos
    
- Grande distância física até o servidor
    
Um recurso que você pode aproveitar no SharePoint Online é a Microsoft CDN (rede de fornecimento de conteúdo). Uma CDN é basicamente uma coleção distribuída de servidores implantados em vários datacenters. Com uma CDN, o conteúdo em páginas pode ser hospedado em um servidor e o cliente está perto do mesmo se o cliente está longe do servidor do SharePoint de origem. Microsoft usarão isso em mais detalhes no futuro para armazenar instâncias locais das páginas que não podem ser personalizadas, por exemplo o SharePoint admin home page Online. Para obter mais informações sobre as CDNs, consulte [redes de fornecimento de conteúdo](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).
  
Algo que de que você deve estar ciente, mas que não pode fazer muito para mudar, é a velocidade de conexão do seu ISP. Uma simples ferramenta de teste de velocidade indicará a velocidade de conexão.
  
### <a name="browser-connection"></a>Conexão do navegador

Existem alguns fatores que devem ser considerados com relação aos navegadores da Web de uma perspectiva de desempenho.
  
Visitar páginas complexas afetará o desempenho. A maioria dos navegadores têm apenas um cache pequeno (aproximadamente 90MB), enquanto a média página da web é geralmente cerca de 1.6 MB. Isso não leva muito tempo para ser usado para cima.
  
Largura de banda também pode ser um problema. Por exemplo, se um usuário está assistindo a vídeos em outra sessão, isso afetará o desempenho da sua página do SharePoint. Enquanto você não pode impedir usuários de fluxo de mídia, você pode controlar a maneira como uma página carregará para usuários.
  
Confira os seguintes artigos para diferentes técnicas de personalização de página do SharePoint Online e outras práticas recomendadas para ajudá-lo a obter o desempenho ideal.
  
- [Opções de navegação para o SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Use a ferramenta de diagnóstico de página para o SharePoint Online](page-diagnostics-for-spo.md)
    
- [Otimização de imagem para o SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Atraso no carregamento de imagens e JavaScript no SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minificação e agrupamento no SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Usando redes de distribuição de conteúdo](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Usando o Web Part de pesquisa de conteúdo, em vez de Web Part de consulta de conteúdo para melhorar o desempenho no SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [SharePoint Online de teste de carga e planejamento de capacidade](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnóstico de problemas de desempenho no SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Usando o cache de objetos com o SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Como evitar ficar limitado ou bloqueado no SharePoint Online](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

