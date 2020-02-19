---
title: Recomendações de desempenho de rede no centro de administração do Microsoft 365 (versão prévia)
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
description: Visão geral das recomendações de desempenho de rede no centro de administração do Microsoft 365 (versão prévia)
ms.openlocfilehash: d944814effc62956d5047bad1f3088d0919793ee
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106236"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Recomendações de desempenho de rede no centro de administração do Microsoft 365 (versão prévia)

A página desempenho da rede no centro de administração do Microsoft 365 mostra as insights de rede e uma pontuação de rede para clientes corporativos. O Network insights é uma alteração de design de arquitetura de rede recomendada específica para melhorar a experiência do usuário relacionada à conectividade de rede com o Office 365 e a pontuação de rede mostra como a conectividade de rede impacta a experiência do usuário que permite a comparação de diferentes conexões de rede de local de usuário. As empresas que usam o Office 365 com vários locais do Office e arquiteturas de perímetro de rede não triviais podem se beneficiar, durante a integração inicial com o Office 365, ou para corrigir problemas de desempenho de rede descobertos com o uso dos. Em geral, isso não é necessário para pequenas empresas que usam o Office 365 ou qualquer empresa que já tenha conectividade de rede simples e direta. Empresas com mais de 500 usuários e vários locais do Office são mais beneficiadas.

>[!IMPORTANT]
>Recomendações de desempenho de rede, ideias e avaliações no centro de administração do Microsoft 365 estão atualmente no status de visualização e só estão disponíveis para locatários do Office 365 que foram registrados no programa de visualização de recurso.

## <a name="enterprise-network-connectivity-challenges"></a>Desafios de conectividade de rede corporativa

![Rede de cliente para nuvem](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Muitas empresas têm configurações de perímetro de rede que cresceram com o passar do tempo e foram basicamente projetadas para acomodar o acesso ao site da Internet para funcionários, onde a maioria dos sites não é conhecida e não é confiável. O foco predominante e necessário é evitar ataques de malware e pesca desses sites desconhecidos. Essa estratégia de configuração de rede, embora útil para fins de segurança, pode levar à degradação do desempenho do usuário do Office 365 e da experiência do usuário. As empresas podem melhorar a experiência do usuário, mas também continuar a proteger seu ambiente, seguindo os [princípios de conectividade do Office 365](https://aka.ms/pnc) e, em breve, usando o novo recurso de desempenho de rede do centro de administração do Microsoft 365. Este recurso ajuda com o design de arquitetura de rede que se alinha com os princípios de conectividade do Office 365 e deve levar a um desempenho otimizado de rede para a conectividade com o Office 365.

## <a name="how-we-can-solve-these-challenges"></a>Como podemos resolver esses desafios

Às vezes, a Microsoft é solicitada a investigar problemas de desempenho da rede com o Office 365 para clientes de grandes empresas, e essas muitas vezes têm uma causa raiz relacionada à infraestrutura de egresso da rede do cliente. Quando uma causa raiz comum de um problema de perímetro de rede do cliente for encontrada, procuraremos a identificação de medidas de teste simples que a identificam. Um teste com um limite de medida que identifica um problema específico é importante porque podemos testar a mesma medição em qualquer local, diga se essa causa raiz está presente e compartilhe-a como uma percepção de rede com o administrador. Alguns insights de rede simplesmente indicarão um problema que precisa de investigação adicional. Uma percepção de rede onde temos testes suficientes para mostrar uma ação de correção específica para corrigir a causa raiz é listada como uma ação recomendada. Essas insights de rede com base em medidas após um limite pré-determinado são muito mais valiosos do que o Conselho geral de práticas recomendadas, já que você não precisa perguntar se a prática recomendada se aplica e resultará em uma melhoria significativa da experiência do usuário ou não .

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Visão geral do desempenho da rede no centro de administração do Microsoft 365

A Microsoft tem medições de rede existentes de vários clientes da Web e da área de trabalho do Office que dão suporte à operação do Office 365. Essas medidas estão sendo usadas agora para fornecer insights de design de arquitetura de rede e uma pontuação de desempenho de rede que é mostrada na página desempenho da rede no centro de administração do Microsoft 365.

As informações de local aproximadas associadas às medições de rede podem identificar a cidade onde os dispositivos cliente estão localizados. Isso é usado para mostrar os locais do escritório e as medições de rede dos clientes são agrupadas para fornecer informações de rede para esse local do escritório. A pontuação de rede em cada local é mostrada com cores e o número relativo de usuários em cada local é representado pelo tamanho do círculo. A página Visão geral também mostra a pontuação de rede para o cliente como uma média ponderada em todos os locais do Office.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Resumo de desempenho da rede de local específico do Office e insights

Selecionar um local do Office abre uma página de resumo específica do local. Mostramos detalhes da saída de rede que foi identificado de medidas para esse local do escritório.

A página de Resumo de localização do Office também mostra os locais de Pontuação de rede, o histórico de Pontuação de rede, uma comparação dessa pontuação de locais com outros clientes na mesma cidade e uma lista de ideias e recomendações específicas que o cliente pode realizar melhorar a conectividade de rede. As comparações entre os clientes na mesma cidade têm como base a expectativa de que todos os clientes tenham acesso igual aos provedores de serviços de rede, à infraestrutura de telecomunicações e aos pontos de presença da rede Microsoft próximos.

A guia detalhes na página local do escritório mostra os resultados da medição específica que foram usados para surgir com qualquer insights, recomendações e a pontuação de rede. Isso é fornecido para que os engenheiros de rede possam validar as recomendações e o fator em qualquer restrição ou especificações em seu ambiente.
Para clientes que desejam melhorar a precisão de locais e recomendações do Office, permitimos que sejam inseridas informações mais específicas. Isso é feito editando as informações de local descobertas e pode reduzir as aproximações inerentes às informações de local disponíveis para medições de rede.

## <a name="faq"></a>Perguntas frequentes

### <a name="what-is-office-365-service-front-door"></a>O que é a porta frontal de serviço do Office 365?

A porta frontal do serviço do Office 365 é um ponto de entrada na rede global da Microsoft, onde os clientes e serviços do Office terminam suas conexões de rede. Para obter uma conexão de rede ideal com o Office 365, é recomendável que sua conexão de rede seja encerrada na porta frontal mais próxima do Office 365 na sua cidade ou metro.
Observação: a porta frontal do serviço do Office 365 não tem relação direta com o produto "serviço de porta frontal do Azure" disponível no Azure Marketplace.

### <a name="what-is-an-optimal-office-365-service-front-door"></a>Qual é a melhor porta de serviço do Office 365?

Uma das melhores portas de serviço do Office 365 é uma das mais próximas à saída da sua rede, geralmente na cidade ou na área de metrô. Use a ferramenta de desempenho de rede do Office 365 para determinar o local da sua porta de entrada de serviço do Office 365 e da porta frontal de serviço ideal. Se a ferramenta determina que sua porta frontal de uso é ideal, então, você está se conectando de forma ideal à rede global da Microsoft.

### <a name="what-is-an-internet-egress-location"></a>O que é um local de egresso na Internet?

O local de egresso de Internet é o local onde o tráfego de rede sai da rede corporativa e se conecta à Internet. Isso também é identificado como o local onde você tem um dispositivo NAT (conversão de endereço de rede) e, em geral, onde você se conecta com um provedor de serviços de Internet (ISP). Se você vir uma longa distância entre o local e o local de saída da Internet, isso poderá identificar um backhaul WAN significativo.

## <a name="related-topics"></a>Tópicos relacionados

[Informações de desempenho de rede do Office 365 (versão prévia)](office-365-network-mac-perf-insights.md)

[Avaliação de rede do Office 365 (versão prévia)](office-365-network-mac-perf-score.md)

[Ferramenta de integração de rede do Office 365 no centro de administração do M365 (versão prévia)](office-365-network-mac-perf-onboarding-tool.md)
