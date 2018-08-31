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
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>SharePoint Online de teste de carga e planejamento de capacidade

Este artigo descreve como você pode implantar no SharePoint Online, sem realizando o teste de carga tradicional, desde que ela não é permitida.
  
Embora a carga ativa testes no SharePoint Online é recomendada, existem outras maneiras que você pode assegurar um site não produzirá uma experiência de usuário ruim quando você inicia o site. 
  
Com o SharePoint Online você não precisa fazer planejamento de capacidade, como isso é feito para você, como parte de nossa oferta de serviço. Com ambientes locais, o teste de carga é usado para validar a pressuposição de escala e, por fim, encontre o ponto de interrupção de um farm; pela saturação-lo com carga. Com o SharePoint Online, precisamos fazer coisas de forma diferente. Sendo um ambiente de multilocação, temos proteger inquilinos todos no mesmo farm, portanto, podemos será automaticamente acelerar quaisquer testes de carga. Isso significa que você receberá decepcionantes e potencialmente incorreta são resultados se você tentar carregar o seu ambiente de teste.
  
Um dos principais benefícios do SharePoint Online em uma implantação local é a elasticidade da nuvem. Nosso ambiente de grande escala estiver configurado para o serviço milhões de usuários em uma base diária, portanto, é importante que podemos manipular capacidade efetivamente expandindo automaticamente farms, como e quando necessário. Este artigo explica como podemos planejar o crescimento de capacidade e dimensionamento out no lugar. O artigo também aborda abordagens para uso que não envolvem o teste de carga.
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a>Como o Office 365 prevê carga e expande a capacidade

Trabalho de gerenciamento de capacidade de servidor SharePoint Online é feito usando dois métodos:
  
- Previsão de capacidade
    
- Balanceamento de carga nos farms de servidor único
    
Ao contrário de planejamento para um ambiente local, para previsão de capacidade no SharePoint Online, estamos capazes de compilar estatísticas e requisitos possíveis em qualquer grupo de determinado servidor do gráfico. A demanda agregada algo parecido com as solicitações na zona (onde uma zona é um grupo de farms do SharePoint) linha de crescimento na imagem abaixo:
  
![Gráfico mostrando a capacidade preditiva: previsão](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
Embora o crescimento imprevisível em qualquer um farm, a soma agregada de solicitações em uma zona é previsível. Identificando as tendências de crescimento no SharePoint Online, podemos planejar expansão futura.
  
Para usar a capacidade de forma eficiente e lidar com o crescimento inesperado, qualquer farm, temos automação que rastreia a carga de front-end e dimensiona in-loco, quando necessário. A principal métrica que usamos como um sinal para dimensionar com antecedência termina é a carga da CPU. Nosso objetivo é manter a carga da CPU de pico em 40%. Isso é para que o buffer suficiente absorver picos inesperados. Como carga abordagens 40% no estado estável, adicionamos front-ends para farms.
  
![Gráfico que mostra a capacidade de previsão: gerenciando farms](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
Servidores adicionais podem ser adicionados rapidamente para um farm, usando aqueles que foram adicionados anteriormente à região através do uso de previsão. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>Como planejar para o lançamento de um site?

Você deve esperar que o farm em que seu novo site inicia serão automaticamente monitorado para que sejam adicionados novos servidores front-end, conforme descrito acima. Por esse motivo, não precisamos qualquer notificação para o seu novo lançamento de site.
  
Após outras práticas recomendadas para uma única página no SharePoint Online é improvável que um novo lançamento de site para até 100.000 usuários terá impacto no farm.
  
Há algumas estratégias para planejar uma versão de um novo site do SharePoint Online. Conforme mostrado na seguinte imagem, muitas vezes a quantidade de usuários que são convidados é consideravelmente maior do que aqueles que realmente os utilizam o site. Esta imagem mostra uma estratégia sobre como distribuir uma versão. Esse método não apenas ajuda com o carregamento de desempenho, mas também pode ajudar a identificar as maneiras de melhorar o site do SharePoint antes da grande maioria dos usuários vê-lo.
  
![Gráfico mostrando usuários convidados e ativos](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Na fase piloto, é bom Obtenha comentários de usuários que a organização de confiança e sabe que vão ser envolvido. Dessa forma, é possível medir como o sistema está sendo usado, bem como seu desempenho.
  
Depois disso, começa uma distribuição a todos os usuários em ondas; Obtendo feedback e analisando o desempenho regularmente. Isso tem a vantagem de lentamente apresentando o sistema e fazer melhorias, como o sistema obtém uso mais. Isso também permite reagir à carga maior como o site é distribuiu para cada vez mais usuários.
  
Finalmente, enquanto os testes de carga são proibidas, os clientes talvez queira configurar o ping periódico o serviço de latência e disponibilidade de medida. Isso identificará uma linha de base para os sites. No entanto, estas devem ser mantidas para baixa frequência para evitar a limitação problemas descritos anteriormente.
  

