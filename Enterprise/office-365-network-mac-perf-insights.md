---
title: Informações de desempenho de rede do Office 365 (versão prévia)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Informações de desempenho de rede do Office 365 (versão prévia)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106242"
---
# <a name="office-365-network-performance-insights-preview"></a>Informações de desempenho de rede do Office 365 (versão prévia)

As páginas de desempenho da rede do centro de administração do Microsoft 365 mostram as insights de rede do Office 365 que podem ajudar na criação de perímetros de rede para seus locais do Office. Há cinco insights de rede específicos que podem ser mostradas para cada local do escritório.

>[!IMPORTANT]
>Recomendações de desempenho de rede, ideias e avaliações no centro de administração do Microsoft 365 estão atualmente no status de visualização e só estão disponíveis para locatários do Office 365 que foram registrados no programa de visualização de recurso.

## <a name="backhauled-network-egress"></a>Saída de rede de rebocada

A distância entre o local do usuário e a saída da rede é maior que 500 milhas (800 quilômetros) e espera-se que isso afete o desempenho. É recomendada a saída local mais próxima do usuário.

Isso identifica que a distância entre o local do escritório e a egresso da rede é maior que 500 milhas. O local do Office é identificado por um local de máquina cliente ofuscado e o local de egresso de rede é identificado usando o endereço IP reverso para os bancos de dados de local. O local do escritório pode ser impreciso se os serviços de localização do Windows estiverem desabilitados nos computadores. O local de egresso de rede pode ser impreciso se as informações do banco de dados de endereço IP reverso não forem precisas.

Os detalhes dessa informação incluem o local do escritório, o local de egresso da rede e a distância entre eles.

Para esta percepção, recomendamos que a saída da rede fique mais próxima do local do escritório, para que a conectividade possa ser roteada de maneira ideal para a rede da Microsoft na Internet e para as portas frontais do serviço do Office 365. Após o fechamento de egresso da rede para usuários, os locais do Office também podem melhorar o desempenho no futuro, já que a Microsoft expande tanto os pontos de presença de rede quanto as portas de serviço do Office 365 no futuro.

Esta percepção é abreviada como "egresso" em alguns modos de exibição de resumo.

## <a name="better-performance-detected-for-customers-near-you"></a>Melhor desempenho detectado para clientes próximos de você

Como um número significativo de clientes em sua área de metrô têm melhor desempenho do que os usuários em sua organização neste local do escritório.

Isso examina o desempenho agregado dos clientes do Office 365 na mesma cidade que este local do escritório.

![Desempenho de rede relativo](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

Calculamos a porcentagem dos clientes do Office 365 na mesma cidade em buckets de desempenho melhores. Se esse número for 10% de mais, mostraremos a visão da rede.

Esta percepção é abreviada como "pares" em alguns modos de exibição de resumo.

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Uso de uma porta frontal de serviço do Exchange Online não ideal

O usuário não está se conectando a uma das melhores portas de serviço do Office 365 e isso deve afetar o desempenho.

Listamos as portas frontais do serviço do Exchange Online que são adequadas para uso da cidade de local do escritório com bom desempenho. Se o teste atual mostrar o uso de uma porta frontal do serviço do Exchange Online que não está nessa lista, chamamos essa recomendação.

O uso de uma porta de entrada de serviço do Exchange Online não ideal pode ser causado pelo backhaul de rede antes da saída da rede corporativa, caso recomendamos a saída de rede local e direta. Também pode ser causado pelo uso de um servidor de resolvedor de DNS recursivo remoto, caso recomendamos alinhar o servidor do resolvedor de DNS recursivo com a saída da rede.

Esta percepção é abreviada como "roteamento" em alguns modos de exibição de resumo.

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a>Uso da porta frontal do serviço do SharePoint Online não ideal

O usuário não está se conectando à porta frontal mais próxima do serviço do SharePoint Online. Espera-se que isso esteja afetando o desempenho.

Identificamos a porta frontal do serviço do SharePoint Online à qual o cliente de teste está se conectando. Em seguida, para a cidade do local do escritório, comparamos isso à porta frontal do serviço do SharePoint Online esperado para essa cidade. Se não coincidir, fazemos essa recomendação.

Esta percepção é abreviada como "AFD" em alguns modos de exibição de resumo.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Baixa velocidade de download da porta frontal do SharePoint

Sub-rede ideal a velocidade de download detectou que impacta quanto tempo leva para carregar documentos do OneDrive for Business.

A velocidade de download que um usuário pode obter do SharePoint Online e do OneDrive for Business Service Doors é medida em megabytes por segundo (MBps). Se esse valor for menor que 1 MBps, forneceremos esta percepção.

Para melhorar a velocidade de download que um usuário pode obter largura de banda pode precisar ser aumentada. Como alternativa, pode haver congestionamento de rede entre máquinas de usuário no local do escritório e na porta frontal do serviço do SharePoint Online. Isso às vezes é chamado de perda congestionada e restringe a velocidade de download disponível para os usuários, mesmo se houver largura de banda suficiente disponível.

Esta percepção é abreviada como "throughput" em alguns modos de exibição de resumo.

## <a name="related-topics"></a>Tópicos relacionados

[Recomendações de desempenho de rede no centro de administração do Microsoft 365 (versão prévia)](office-365-network-mac-perf-overview.md)

[Avaliação de rede do Office 365 (versão prévia)](office-365-network-mac-perf-score.md)

[Ferramenta de integração de rede do Office 365 no centro de administração do M365 (versão prévia)](office-365-network-mac-perf-onboarding-tool.md)
