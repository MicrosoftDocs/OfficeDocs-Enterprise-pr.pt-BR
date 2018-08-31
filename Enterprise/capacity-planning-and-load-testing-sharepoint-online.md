---
title: SharePoint Online de teste de carga e planejamento de capacidade
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
description: Este artigo descreve como você pode implantar no SharePoint Online, sem realizando o teste de carga tradicional, desde que ela não é permitida.
ms.openlocfilehash: 06649942f20dc18abfcae0e56df7e3ea56ed9165
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539409"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="352b4-103">SharePoint Online de teste de carga e planejamento de capacidade</span><span class="sxs-lookup"><span data-stu-id="352b4-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="352b4-104">Este artigo descreve como você pode implantar no SharePoint Online, sem realizando o teste de carga tradicional, desde que ela não é permitida.</span><span class="sxs-lookup"><span data-stu-id="352b4-104">This article describes how you can deploy to SharePoint Online without performing traditional load testing since it is not permitted.</span></span>
  
<span data-ttu-id="352b4-105">Embora a carga ativa testes no SharePoint Online é recomendada, existem outras maneiras que você pode assegurar um site não produzirá uma experiência de usuário ruim quando você inicia o site.</span><span class="sxs-lookup"><span data-stu-id="352b4-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="352b4-p101">Com o SharePoint Online você não precisa fazer planejamento de capacidade, como isso é feito para você, como parte de nossa oferta de serviço. Com ambientes locais, o teste de carga é usado para validar a pressuposição de escala e, por fim, encontre o ponto de interrupção de um farm; pela saturação-lo com carga. Com o SharePoint Online, precisamos fazer coisas de forma diferente. Sendo um ambiente de multilocação, temos proteger inquilinos todos no mesmo farm, portanto, podemos será automaticamente acelerar quaisquer testes de carga. Isso significa que você receberá decepcionantes e potencialmente incorreta são resultados se você tentar carregar o seu ambiente de teste.</span><span class="sxs-lookup"><span data-stu-id="352b4-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="352b4-p102">Um dos principais benefícios do SharePoint Online em uma implantação local é a elasticidade da nuvem. Nosso ambiente de grande escala estiver configurado para o serviço milhões de usuários em uma base diária, portanto, é importante que podemos manipular capacidade efetivamente expandindo automaticamente farms, como e quando necessário. Este artigo explica como podemos planejar o crescimento de capacidade e dimensionamento out no lugar. O artigo também aborda abordagens para uso que não envolvem o teste de carga.</span><span class="sxs-lookup"><span data-stu-id="352b4-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="352b4-115">Como o Office 365 prevê carga e expande a capacidade</span><span class="sxs-lookup"><span data-stu-id="352b4-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="352b4-116">Trabalho de gerenciamento de capacidade de servidor SharePoint Online é feito usando dois métodos:</span><span class="sxs-lookup"><span data-stu-id="352b4-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="352b4-117">Previsão de capacidade</span><span class="sxs-lookup"><span data-stu-id="352b4-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="352b4-118">Balanceamento de carga nos farms de servidor único</span><span class="sxs-lookup"><span data-stu-id="352b4-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="352b4-p103">Ao contrário de planejamento para um ambiente local, para previsão de capacidade no SharePoint Online, estamos capazes de compilar estatísticas e requisitos possíveis em qualquer grupo de determinado servidor do gráfico. A demanda agregada algo parecido com as solicitações na zona (onde uma zona é um grupo de farms do SharePoint) linha de crescimento na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="352b4-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![Gráfico mostrando a capacidade preditiva: previsão](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="352b4-p104">Embora o crescimento imprevisível em qualquer um farm, a soma agregada de solicitações em uma zona é previsível. Identificando as tendências de crescimento no SharePoint Online, podemos planejar expansão futura.</span><span class="sxs-lookup"><span data-stu-id="352b4-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="352b4-p105">Para usar a capacidade de forma eficiente e lidar com o crescimento inesperado, qualquer farm, temos automação que rastreia a carga de front-end e dimensiona in-loco, quando necessário. A principal métrica que usamos como um sinal para dimensionar com antecedência termina é a carga da CPU. Nosso objetivo é manter a carga da CPU de pico em 40%. Isso é para que o buffer suficiente absorver picos inesperados. Como carga abordagens 40% no estado estável, adicionamos front-ends para farms.</span><span class="sxs-lookup"><span data-stu-id="352b4-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![Gráfico que mostra a capacidade de previsão: gerenciando farms](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="352b4-130">Servidores adicionais podem ser adicionados rapidamente para um farm, usando aqueles que foram adicionados anteriormente à região através do uso de previsão.</span><span class="sxs-lookup"><span data-stu-id="352b4-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="352b4-131">Como planejar para o lançamento de um site?</span><span class="sxs-lookup"><span data-stu-id="352b4-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="352b4-p106">Você deve esperar que o farm em que seu novo site inicia serão automaticamente monitorado para que sejam adicionados novos servidores front-end, conforme descrito acima. Por esse motivo, não precisamos qualquer notificação para o seu novo lançamento de site.</span><span class="sxs-lookup"><span data-stu-id="352b4-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="352b4-134">Após outras práticas recomendadas para uma única página no SharePoint Online é improvável que um novo lançamento de site para até 100.000 usuários terá impacto no farm.</span><span class="sxs-lookup"><span data-stu-id="352b4-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="352b4-p107">Há algumas estratégias para planejar uma versão de um novo site do SharePoint Online. Conforme mostrado na seguinte imagem, muitas vezes a quantidade de usuários que são convidados é consideravelmente maior do que aqueles que realmente os utilizam o site. Esta imagem mostra uma estratégia sobre como distribuir uma versão. Esse método não apenas ajuda com o carregamento de desempenho, mas também pode ajudar a identificar as maneiras de melhorar o site do SharePoint antes da grande maioria dos usuários vê-lo.</span><span class="sxs-lookup"><span data-stu-id="352b4-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![Gráfico mostrando usuários convidados e ativos](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="352b4-p108">Na fase piloto, é bom Obtenha comentários de usuários que a organização de confiança e sabe que vão ser envolvido. Dessa forma, é possível medir como o sistema está sendo usado, bem como seu desempenho.</span><span class="sxs-lookup"><span data-stu-id="352b4-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="352b4-p109">Depois disso, começa uma distribuição a todos os usuários em ondas; Obtendo feedback e analisando o desempenho regularmente. Isso tem a vantagem de lentamente apresentando o sistema e fazer melhorias, como o sistema obtém uso mais. Isso também permite reagir à carga maior como o site é distribuiu para cada vez mais usuários.</span><span class="sxs-lookup"><span data-stu-id="352b4-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="352b4-p110">Finalmente, enquanto os testes de carga são proibidas, os clientes talvez queira configurar o ping periódico o serviço de latência e disponibilidade de medida. Isso identificará uma linha de base para os sites. No entanto, estas devem ser mantidas para baixa frequência para evitar a limitação problemas descritos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="352b4-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

