---
title: Avaliação de rede do Office 365 (versão prévia)
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
description: Avaliação de rede do Office 365 (versão prévia)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106235"
---
# <a name="office-365-network-assessment-preview"></a>Avaliação de rede do Office 365 (versão prévia)

A avaliação de rede do Office 365 indica o impacto da experiência do usuário relativa da conectividade de rede do cliente. O impacto de qualquer conectividade de rede de propriedade da Microsoft é excluído disso para permitir que os clientes otimizem os designs de rede para os quais são responsáveis.

Ela é calculada a partir de medições que afetam a experiência do usuário em cargas de trabalho principais do Office 365 e mostradas como uma porcentagem com um intervalo de 0 a 100.

Uma pontuação de rede muito baixa sugere que os clientes do Office 365 terão problemas significativos de conexão ou de resposta restante do usuário. Uma pontuação de 80% representa a conectividade de rede em que você não espera receber queixas de usuário sobre sua experiência de usuário do Office 365 devido ao seu desempenho de rede. À medida que são feitas melhorias na conectividade de rede, essa Pontuação aumenta junto com a experiência do usuário.

>[!IMPORTANT]
>Recomendações de desempenho de rede, ideias e avaliações no centro de administração do Microsoft 365 estão atualmente no status de visualização e só estão disponíveis para locatários do Office 365 que foram registrados no programa de visualização de recurso.

## <a name="exchange-online"></a>Exchange Online

Para o Exchange Online, a latência TCP da máquina cliente para o servidor front-end do Exchange é medida. Isso pode ser afetado pela distância que a rede se movimenta na LAN e na WAN dos clientes. Também pode ser afetado por dispositivos ou serviços intermediários de rede que atrasam a conectividade ou fazem com que os pacotes sejam reenviados.

## <a name="sharepoint-online"></a>SharePoint Online

Para o SharePoint Online, a velocidade de download disponível para o usuário acessar um documento é medida. Isso pode ser afetado pela largura de banda disponível em circuitos de rede entre a máquina cliente e a rede da Microsoft. Também é possível impactar com o congestionamento de rede que existe em gargalos em dispositivos de rede complexos ou em áreas de Wi-Fi de cobertura ruim.

## <a name="microsoft-teams"></a>Microsoft Teams

Para o Microsoft Teams, a qualidade da rede é medida como latência de UDP, tremulação de UDP e perda de pacotes UDP. O UDP é usado para a chamada e conferência de áudio e conectividade de mídia de vídeo para o Microsoft Teams. Isso pode ser afetado pelos mesmos fatores para a latência e velocidade de download, além de falhas de conectividade no suporte a UDP de uma rede, pois o UDP é configurado separadamente para o protocolo TCP mais comum.

## <a name="tenant-network-score-and-office-location-network-score"></a>Pontuação de rede de locatário e pontuação de rede de local do escritório

Uma pontuação de rede mede o design do perímetro de rede de um local do escritório para a rede da Microsoft. Aprimoramentos no perímetro da rede são mais bem executados em cada local do escritório ou onde a conectividade de rede é agregada pode haver melhorias que afetam vários locais.
Mostramos uma pontuação de rede para todo o locatário do Office 365 na página de visão geral do desempenho da rede e uma pontuação de rede específica para cada local do escritório detectado na página de resumo desse local.

## <a name="network-score-panel"></a>Painel de Pontuação de rede

Cada Pontuação de rede se para o locatário ou para um local específico do escritório mostra um painel com detalhes sobre a pontuação. Este painel mostra um gráfico de barras da pontuação tanto como uma porcentagem quanto como o total de pontos para cada carga de trabalho do componente, incluindo apenas as cargas de trabalho onde os dados de medição foram recebidos. Para uma pontuação de rede de local de escritório, também mostramos um benchmark que é a mediana de todos os clientes do Office 365 que relataram dados na mesma cidade que o seu local do Office.

A divisão de pontuação no painel mostra a pontuação de cada uma das cargas de trabalho do componente.

O histórico de Pontuação mostra os últimos 30 dias da pontuação e o benchmark.

## <a name="related-topics"></a>Tópicos relacionados

[Recomendações de desempenho de rede no centro de administração do Microsoft 365 (versão prévia)](office-365-network-mac-perf-overview.md)

[Informações de desempenho de rede do Office 365 (versão prévia)](office-365-network-mac-perf-insights.md)

[Ferramenta de integração de rede do Office 365 no centro de administração do M365 (versão prévia)](office-365-network-mac-perf-onboarding-tool.md)
