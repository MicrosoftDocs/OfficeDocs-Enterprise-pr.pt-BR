---
title: Planejamento de capacidade e teste de carregamento do SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Este artigo descreve como você pode implantar o no SharePoint Online sem executar testes de carga tradicionais, pois ele não é permitido.
ms.openlocfilehash: d62b15be38b3f62c64c2943313b94aa99cbd14ab
ms.sourcegitcommit: 739024fe2862ab646b36e218b57c5cc16ebe7892
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2019
ms.locfileid: "37422138"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planejamento de capacidade e teste de carregamento do SharePoint Online
Este artigo descreve como você pode implantar o no SharePoint Online sem testes de carga tradicionais, já que o teste de carga não é permitido no SharePoint Online. O SharePoint Online é um serviço de nuvem e os recursos de carga, a integridade e o equilíbrio geral de carga no serviço são gerenciados pela Microsoft.
  
A melhor abordagem para garantir o sucesso da inicialização do seu site é seguir princípios básicos, práticas e recomendações que estão realçadas no [plano de implantação do seu portal de lançamento](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Visão geral de como o SharePoint Online realiza o planejamento de capacidade 
Um dos principais benefícios do SharePoint Online sobre uma implantação local é a elasticidade da nuvem, bem como otimizações para usuários em regiões distribuídas. Nosso ambiente de grande escala é configurado para atender milhões de usuários diariamente, portanto, é importante que possamos lidar com a capacidade de forma eficaz, balanceando e expandindo farms.
  
Embora o crescimento seja geralmente imprevisível para qualquer locatário em qualquer farm, a soma de solicitações agregada é previsível ao longo do tempo. Identificando as tendências de crescimento no SharePoint Online, podemos planejar a expansão futura.
  
Para usar eficientemente a capacidade e lidar com o crescimento inesperado, em qualquer farm, temos automação que controla e monitora vários elementos do serviço. Várias métricas são utilizadas, com uma das principais que estão sendo carga de CPU, que é usada como um sinal para dimensionar servidores front-end. Além disso, recomendamos uma [abordagem em fases/ondas](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out), pois os ambientes SQL serão dimensionados de acordo com a carga e o crescimento ao longo do tempo e, seguindo as fases e ondas, o permitirá a distribuição correta da carga e do crescimento. 

A capacidade é mais do que simplesmente adicionar mais hardware de forma contínua, mas também se refere ao gerenciamento e ao controle dessa capacidade para garantir que ela esteja atendendo solicitações de carregamento válidas. Recomendamos que os clientes sigam as diretrizes recomendadas para garantir que tenham a melhor experiência. Isso também significa limitar padrões e controles no local para garantir que não permitimos o comportamento "abusivo" no serviço. Embora nem todo o comportamento "ruim" seja intencional, temos de garantir que limitamos o efeito desse comportamento. Para obter mais informações sobre a limitação e como evitá-la, consulte o artigo sobre [como evitar ser limitado](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) .

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Por que você não pode carregar testar o SharePoint Online
Com ambientes locais, o teste de carga é usado para validar a suposição de escala e, finalmente, encontrar o ponto de ruptura de um farm; por saturating-lo com Load. 

Com o SharePoint Online, precisamos fazer coisas de forma diferente porque a escala é relativamente fluida e ajusta, acelera e controla a carga, com base em determinadas heurísticas. Sendo um ambiente de vários locatários de grande escala, devemos proteger todos os locatários no mesmo farm, portanto, aceleraremos automaticamente qualquer teste de carga. No entanto, se você tentar carregar o teste, além de ser limitado, receberá resultados disappointing e potencialmente enganosos, pois o farm que você testou hoje provavelmente terá sofrido alterações de escala durante a janela de teste ou em horas após o teste, como as ações de escala e de balanceamento de farm são executadas em uma base contínua.

Em vez de tentar carregar o SharePoint de teste como um serviço, em vez de se concentrar em seguir as práticas recomendadas e siga as orientações de [criação, inicialização e manutenção de um portal saudável](https://go.microsoft.com/fwlink/?linkid=2105838) .
