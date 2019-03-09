---
title: Planejamento de capacidade e teste de carregamento do SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Este artigo descreve como você pode implantar o no SharePoint Online sem executar testes de carga tradicionais, pois ele não é permitido.
ms.openlocfilehash: ef5d6c043b4be2e8c5358a9c060459b4c6a92156
ms.sourcegitcommit: 468c8e8d2f951e08cf50301445ad650ef17328aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "30512716"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planejamento de capacidade e teste de carga do SharePoint Online.

Este artigo descreve como você pode implantar o no SharePoint Online sem testes de carga tradicionais, já que o teste de carga não é permitido no SharePoint Online. O SharePoint Online é um serviço de nuvem os recursos de carga, a integridade e o equilíbrio geral de carga no serviço são gerenciados pela Microsoft.
  
A melhor abordagem para garantir o sucesso da inicialização do seu site é seguir princípios básicos, práticas e recomendações realçadas abaixo.
  
Com ambientes locais, o teste de carga é usado para validar a suposição de escala e, finalmente, encontrar o ponto de ruptura de um farm; por saturating-lo com Load. Com o SharePoint Online, precisamos fazer coisas de forma diferente. Ser um ambiente de vários locatários, devemos proteger todos os locatários no mesmo farm, portanto, aceleraremos automaticamente qualquer teste de carga. Isso significa que você receberá resultados disappointing e potencialmente enganosos se tentar carregar testar seu ambiente.
  
Um dos principais benefícios do SharePoint Online sobre uma implantação local é a elasticidade da nuvem. Nosso ambiente de grande escala é configurado para atender milhões de usuários diariamente, portanto, é importante que possamos lidar com a capacidade de forma eficaz, balanceando e expandindo farms. O artigo também aborda abordagens para você usar que não envolvem testes de carga, mas envolvem as seguintes diretrizes que irão configurar um lançamento bem-sucedido. 
  
Embora o crescimento seja imprevisível para qualquer locatário em qualquer um dos farms, a soma agregada das solicitações é previsível ao longo do tempo. Identificando as tendências de crescimento no SharePoint Online, podemos planejar a expansão futura.
  
Para usar eficientemente a capacidade e lidar com o crescimento inesperado, em qualquer farm, temos automação que controla a carga de front-end e aumenta, quando necessário. Há várias métricas utilizadas com uma das principais carga de CPU que é usada como sinal para dimensionar servidores front-end. Além disso, e, como você notará mais no artigo, recomendamos uma abordagem em fases/ondas, pois os ambientes SQL serão dimensionados de acordo com a carga e a demanda e seguindo as fases e ondas permite a distribuição correta de carga e crescimento. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>Como planejar um lançamento de site?

### <a name="optimize-pages-by-following-recommended-guidelines"></a>Otimizar páginas seguindo as diretrizes recomendadas
As páginas de uma implantação local não devem ser simplesmente consideradas como estão no SharePoint Online sem analisá-las em relação às diretrizes recomendadas para o SharePoint Online.

Alguns fatores importantes devem ser considerados:
- As implantações locais podem aproveitar caches tradicionais do lado do servidor, como o cache de objetos, mas com as diferenças de topologia na nuvem, essas opções não estão disponíveis.
- Qualquer página/recurso/personalização usada para o consumo em nuvem deve ser otimizado para vários locais, de forma que os usuários em diferentes áreas ou regiões tenham uma experiência consistente. A nuvem oferece otimizações como redes de distribuição de conteúdo (CDN) para otimizar para uma base de usuários distribuídos.

Para páginas de publicação clássicas no SharePoint Online, você pode usar a extensão de Chrome da [ferramenta de diagnóstico de página](https://aka.ms/perftool) que auxiliará na análise das principais páginas de aterrissagem usadas pelos usuários.
As ferramentas de desenvolvedor F12 no navegador ou [Fiddler](https://www.telerik.com/download/fiddler) podem ser usadas para revisar o peso da página e o número de chamadas e elementos que afetam a carga de página Geral deve ser revisado e otimizado. Uma lista de recomendações incluindo o uso de redes de distribuição de conteúdo e outras otimizações pode ser analisada no artigo [ajustar desempenho do SharePoint Online](https://aka.ms/spoperformance) .

### <a name="wave--phase-approach"></a>Abordagem de onda/fase
A abordagem de Big Bang tradicional para os lançamentos de site não permite que a verificação de que personalizações, fontes externas, serviços ou processos tenha sido testada na escala correta. O SharePoint como um serviço também dimensiona sua capacidade com base no uso e no uso previsto e, embora não seja necessário notificar o lançamento do site, siga as diretrizes abaixo para garantir o sucesso.
  
Conforme mostrado na imagem a seguir, muitas vezes o número de usuários convidados é significativamente maior do que aqueles que realmente usam o site. Esta imagem mostra uma estratégia de implantação de uma versão. Este método ajuda a identificar maneiras de melhorar o site do SharePoint antes que a maioria dos usuários o veja. Também permite que um lançamento seja pausado se você encontrar problemas em qualquer uma das fases/ondas, limitando o potencial número de usuários afetados.
  
![Gráfico mostrando usuários convidados e ativos](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Na fase piloto, é bom obter comentários dos usuários que a organização confia e sabe que serão envolvidos. Dessa forma, é possível avaliar como o sistema está sendo usado, além de como ele está sendo executado.
  
Durante cada uma das ondas, reúna os comentários dos usuários em torno dos recursos, bem como o desempenho durante cada onda de implantação. Isso tem a vantagem de apresentar lentamente o sistema e fazer melhorias à medida que o sistema é mais usado. Isso também nos permite reagir à maior carga à medida que o site é implantado para mais e mais usuários.
