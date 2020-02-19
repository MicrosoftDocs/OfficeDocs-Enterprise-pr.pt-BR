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
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="51d3c-103">Informações de desempenho de rede do Office 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="51d3c-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="51d3c-104">As páginas de desempenho da rede do centro de administração do Microsoft 365 mostram as insights de rede do Office 365 que podem ajudar na criação de perímetros de rede para seus locais do Office.</span><span class="sxs-lookup"><span data-stu-id="51d3c-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="51d3c-105">Há cinco insights de rede específicos que podem ser mostradas para cada local do escritório.</span><span class="sxs-lookup"><span data-stu-id="51d3c-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="51d3c-106">Recomendações de desempenho de rede, ideias e avaliações no centro de administração do Microsoft 365 estão atualmente no status de visualização e só estão disponíveis para locatários do Office 365 que foram registrados no programa de visualização de recurso.</span><span class="sxs-lookup"><span data-stu-id="51d3c-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="51d3c-107">Saída de rede de rebocada</span><span class="sxs-lookup"><span data-stu-id="51d3c-107">Backhauled network egress</span></span>

<span data-ttu-id="51d3c-108">A distância entre o local do usuário e a saída da rede é maior que 500 milhas (800 quilômetros) e espera-se que isso afete o desempenho.</span><span class="sxs-lookup"><span data-stu-id="51d3c-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="51d3c-109">É recomendada a saída local mais próxima do usuário.</span><span class="sxs-lookup"><span data-stu-id="51d3c-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="51d3c-110">Isso identifica que a distância entre o local do escritório e a egresso da rede é maior que 500 milhas.</span><span class="sxs-lookup"><span data-stu-id="51d3c-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="51d3c-111">O local do Office é identificado por um local de máquina cliente ofuscado e o local de egresso de rede é identificado usando o endereço IP reverso para os bancos de dados de local.</span><span class="sxs-lookup"><span data-stu-id="51d3c-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="51d3c-112">O local do escritório pode ser impreciso se os serviços de localização do Windows estiverem desabilitados nos computadores.</span><span class="sxs-lookup"><span data-stu-id="51d3c-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="51d3c-113">O local de egresso de rede pode ser impreciso se as informações do banco de dados de endereço IP reverso não forem precisas.</span><span class="sxs-lookup"><span data-stu-id="51d3c-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="51d3c-114">Os detalhes dessa informação incluem o local do escritório, o local de egresso da rede e a distância entre eles.</span><span class="sxs-lookup"><span data-stu-id="51d3c-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="51d3c-115">Para esta percepção, recomendamos que a saída da rede fique mais próxima do local do escritório, para que a conectividade possa ser roteada de maneira ideal para a rede da Microsoft na Internet e para as portas frontais do serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="51d3c-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="51d3c-116">Após o fechamento de egresso da rede para usuários, os locais do Office também podem melhorar o desempenho no futuro, já que a Microsoft expande tanto os pontos de presença de rede quanto as portas de serviço do Office 365 no futuro.</span><span class="sxs-lookup"><span data-stu-id="51d3c-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="51d3c-117">Esta percepção é abreviada como "egresso" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="51d3c-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="51d3c-118">Melhor desempenho detectado para clientes próximos de você</span><span class="sxs-lookup"><span data-stu-id="51d3c-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="51d3c-119">Como um número significativo de clientes em sua área de metrô têm melhor desempenho do que os usuários em sua organização neste local do escritório.</span><span class="sxs-lookup"><span data-stu-id="51d3c-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="51d3c-120">Isso examina o desempenho agregado dos clientes do Office 365 na mesma cidade que este local do escritório.</span><span class="sxs-lookup"><span data-stu-id="51d3c-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![Desempenho de rede relativo](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="51d3c-122">Calculamos a porcentagem dos clientes do Office 365 na mesma cidade em buckets de desempenho melhores.</span><span class="sxs-lookup"><span data-stu-id="51d3c-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="51d3c-123">Se esse número for 10% de mais, mostraremos a visão da rede.</span><span class="sxs-lookup"><span data-stu-id="51d3c-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="51d3c-124">Esta percepção é abreviada como "pares" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="51d3c-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="51d3c-125">Uso de uma porta frontal de serviço do Exchange Online não ideal</span><span class="sxs-lookup"><span data-stu-id="51d3c-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="51d3c-126">O usuário não está se conectando a uma das melhores portas de serviço do Office 365 e isso deve afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="51d3c-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="51d3c-127">Listamos as portas frontais do serviço do Exchange Online que são adequadas para uso da cidade de local do escritório com bom desempenho.</span><span class="sxs-lookup"><span data-stu-id="51d3c-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="51d3c-128">Se o teste atual mostrar o uso de uma porta frontal do serviço do Exchange Online que não está nessa lista, chamamos essa recomendação.</span><span class="sxs-lookup"><span data-stu-id="51d3c-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="51d3c-129">O uso de uma porta de entrada de serviço do Exchange Online não ideal pode ser causado pelo backhaul de rede antes da saída da rede corporativa, caso recomendamos a saída de rede local e direta.</span><span class="sxs-lookup"><span data-stu-id="51d3c-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="51d3c-130">Também pode ser causado pelo uso de um servidor de resolvedor de DNS recursivo remoto, caso recomendamos alinhar o servidor do resolvedor de DNS recursivo com a saída da rede.</span><span class="sxs-lookup"><span data-stu-id="51d3c-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="51d3c-131">Esta percepção é abreviada como "roteamento" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="51d3c-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="51d3c-132">Uso da porta frontal do serviço do SharePoint Online não ideal</span><span class="sxs-lookup"><span data-stu-id="51d3c-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="51d3c-133">O usuário não está se conectando à porta frontal mais próxima do serviço do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="51d3c-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="51d3c-134">Espera-se que isso esteja afetando o desempenho.</span><span class="sxs-lookup"><span data-stu-id="51d3c-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="51d3c-135">Identificamos a porta frontal do serviço do SharePoint Online à qual o cliente de teste está se conectando.</span><span class="sxs-lookup"><span data-stu-id="51d3c-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="51d3c-136">Em seguida, para a cidade do local do escritório, comparamos isso à porta frontal do serviço do SharePoint Online esperado para essa cidade.</span><span class="sxs-lookup"><span data-stu-id="51d3c-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="51d3c-137">Se não coincidir, fazemos essa recomendação.</span><span class="sxs-lookup"><span data-stu-id="51d3c-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="51d3c-138">Esta percepção é abreviada como "AFD" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="51d3c-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="51d3c-139">Baixa velocidade de download da porta frontal do SharePoint</span><span class="sxs-lookup"><span data-stu-id="51d3c-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="51d3c-140">Sub-rede ideal a velocidade de download detectou que impacta quanto tempo leva para carregar documentos do OneDrive for Business.</span><span class="sxs-lookup"><span data-stu-id="51d3c-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="51d3c-141">A velocidade de download que um usuário pode obter do SharePoint Online e do OneDrive for Business Service Doors é medida em megabytes por segundo (MBps).</span><span class="sxs-lookup"><span data-stu-id="51d3c-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="51d3c-142">Se esse valor for menor que 1 MBps, forneceremos esta percepção.</span><span class="sxs-lookup"><span data-stu-id="51d3c-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="51d3c-143">Para melhorar a velocidade de download que um usuário pode obter largura de banda pode precisar ser aumentada.</span><span class="sxs-lookup"><span data-stu-id="51d3c-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="51d3c-144">Como alternativa, pode haver congestionamento de rede entre máquinas de usuário no local do escritório e na porta frontal do serviço do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="51d3c-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="51d3c-145">Isso às vezes é chamado de perda congestionada e restringe a velocidade de download disponível para os usuários, mesmo se houver largura de banda suficiente disponível.</span><span class="sxs-lookup"><span data-stu-id="51d3c-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="51d3c-146">Esta percepção é abreviada como "throughput" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="51d3c-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="51d3c-147">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="51d3c-147">Related topics</span></span>

[<span data-ttu-id="51d3c-148">Recomendações de desempenho de rede no centro de administração do Microsoft 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="51d3c-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="51d3c-149">Avaliação de rede do Office 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="51d3c-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="51d3c-150">Ferramenta de integração de rede do Office 365 no centro de administração do M365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="51d3c-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
