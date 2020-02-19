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
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="64f40-103">Avaliação de rede do Office 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="64f40-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="64f40-104">A avaliação de rede do Office 365 indica o impacto da experiência do usuário relativa da conectividade de rede do cliente.</span><span class="sxs-lookup"><span data-stu-id="64f40-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="64f40-105">O impacto de qualquer conectividade de rede de propriedade da Microsoft é excluído disso para permitir que os clientes otimizem os designs de rede para os quais são responsáveis.</span><span class="sxs-lookup"><span data-stu-id="64f40-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="64f40-106">Ela é calculada a partir de medições que afetam a experiência do usuário em cargas de trabalho principais do Office 365 e mostradas como uma porcentagem com um intervalo de 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="64f40-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="64f40-107">Uma pontuação de rede muito baixa sugere que os clientes do Office 365 terão problemas significativos de conexão ou de resposta restante do usuário.</span><span class="sxs-lookup"><span data-stu-id="64f40-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="64f40-108">Uma pontuação de 80% representa a conectividade de rede em que você não espera receber queixas de usuário sobre sua experiência de usuário do Office 365 devido ao seu desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="64f40-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="64f40-109">À medida que são feitas melhorias na conectividade de rede, essa Pontuação aumenta junto com a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="64f40-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="64f40-110">Recomendações de desempenho de rede, ideias e avaliações no centro de administração do Microsoft 365 estão atualmente no status de visualização e só estão disponíveis para locatários do Office 365 que foram registrados no programa de visualização de recurso.</span><span class="sxs-lookup"><span data-stu-id="64f40-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="64f40-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="64f40-111">Exchange Online</span></span>

<span data-ttu-id="64f40-112">Para o Exchange Online, a latência TCP da máquina cliente para o servidor front-end do Exchange é medida.</span><span class="sxs-lookup"><span data-stu-id="64f40-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="64f40-113">Isso pode ser afetado pela distância que a rede se movimenta na LAN e na WAN dos clientes.</span><span class="sxs-lookup"><span data-stu-id="64f40-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="64f40-114">Também pode ser afetado por dispositivos ou serviços intermediários de rede que atrasam a conectividade ou fazem com que os pacotes sejam reenviados.</span><span class="sxs-lookup"><span data-stu-id="64f40-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="64f40-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="64f40-115">SharePoint Online</span></span>

<span data-ttu-id="64f40-116">Para o SharePoint Online, a velocidade de download disponível para o usuário acessar um documento é medida.</span><span class="sxs-lookup"><span data-stu-id="64f40-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="64f40-117">Isso pode ser afetado pela largura de banda disponível em circuitos de rede entre a máquina cliente e a rede da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="64f40-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="64f40-118">Também é possível impactar com o congestionamento de rede que existe em gargalos em dispositivos de rede complexos ou em áreas de Wi-Fi de cobertura ruim.</span><span class="sxs-lookup"><span data-stu-id="64f40-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="64f40-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="64f40-119">Microsoft Teams</span></span>

<span data-ttu-id="64f40-120">Para o Microsoft Teams, a qualidade da rede é medida como latência de UDP, tremulação de UDP e perda de pacotes UDP.</span><span class="sxs-lookup"><span data-stu-id="64f40-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="64f40-121">O UDP é usado para a chamada e conferência de áudio e conectividade de mídia de vídeo para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="64f40-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="64f40-122">Isso pode ser afetado pelos mesmos fatores para a latência e velocidade de download, além de falhas de conectividade no suporte a UDP de uma rede, pois o UDP é configurado separadamente para o protocolo TCP mais comum.</span><span class="sxs-lookup"><span data-stu-id="64f40-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="64f40-123">Pontuação de rede de locatário e pontuação de rede de local do escritório</span><span class="sxs-lookup"><span data-stu-id="64f40-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="64f40-124">Uma pontuação de rede mede o design do perímetro de rede de um local do escritório para a rede da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="64f40-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="64f40-125">Aprimoramentos no perímetro da rede são mais bem executados em cada local do escritório ou onde a conectividade de rede é agregada pode haver melhorias que afetam vários locais.</span><span class="sxs-lookup"><span data-stu-id="64f40-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="64f40-126">Mostramos uma pontuação de rede para todo o locatário do Office 365 na página de visão geral do desempenho da rede e uma pontuação de rede específica para cada local do escritório detectado na página de resumo desse local.</span><span class="sxs-lookup"><span data-stu-id="64f40-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="64f40-127">Painel de Pontuação de rede</span><span class="sxs-lookup"><span data-stu-id="64f40-127">Network score panel</span></span>

<span data-ttu-id="64f40-128">Cada Pontuação de rede se para o locatário ou para um local específico do escritório mostra um painel com detalhes sobre a pontuação.</span><span class="sxs-lookup"><span data-stu-id="64f40-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="64f40-129">Este painel mostra um gráfico de barras da pontuação tanto como uma porcentagem quanto como o total de pontos para cada carga de trabalho do componente, incluindo apenas as cargas de trabalho onde os dados de medição foram recebidos.</span><span class="sxs-lookup"><span data-stu-id="64f40-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="64f40-130">Para uma pontuação de rede de local de escritório, também mostramos um benchmark que é a mediana de todos os clientes do Office 365 que relataram dados na mesma cidade que o seu local do Office.</span><span class="sxs-lookup"><span data-stu-id="64f40-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="64f40-131">A divisão de pontuação no painel mostra a pontuação de cada uma das cargas de trabalho do componente.</span><span class="sxs-lookup"><span data-stu-id="64f40-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="64f40-132">O histórico de Pontuação mostra os últimos 30 dias da pontuação e o benchmark.</span><span class="sxs-lookup"><span data-stu-id="64f40-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="64f40-133">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="64f40-133">Related topics</span></span>

[<span data-ttu-id="64f40-134">Recomendações de desempenho de rede no centro de administração do Microsoft 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="64f40-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="64f40-135">Informações de desempenho de rede do Office 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="64f40-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="64f40-136">Ferramenta de integração de rede do Office 365 no centro de administração do M365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="64f40-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
