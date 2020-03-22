---
title: Office 365 Network insights (visualização)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/20/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 Network insights (visualização)
ms.openlocfilehash: 9b9ef28fa22b68f7860864aa6ce706531c0d8e00
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890591"
---
# <a name="office-365-network-insights-preview"></a><span data-ttu-id="4787f-103">Office 365 Network insights (visualização)</span><span class="sxs-lookup"><span data-stu-id="4787f-103">Office 365 Network Insights (preview)</span></span>

<span data-ttu-id="4787f-104">O **insights de rede** é uma métrica de desempenho ao vivo coletada do seu locatário do Office 365 e está disponível para visualização apenas por usuários administrativos em seu locatário.</span><span class="sxs-lookup"><span data-stu-id="4787f-104">**Network insights** are live performance metrics collected from your Office 365 tenant, and available to view only by administrative users in your tenant.</span></span> <span data-ttu-id="4787f-105">As ideias são exibidas no centro de administração do Microsoft 365 em <https://portal.microsoft.com/adminportal/home#/networkperformance>.</span><span class="sxs-lookup"><span data-stu-id="4787f-105">Insights are displayed in the Microsoft 365 Admin Center at <https://portal.microsoft.com/adminportal/home#/networkperformance>.</span></span>

<span data-ttu-id="4787f-106">As ideias destinam-se a ajudar na criação de perímetros de rede para seus locais do Office.</span><span class="sxs-lookup"><span data-stu-id="4787f-106">Insights are intended to help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="4787f-107">Cada informação fornece detalhes ao vivo sobre as características de desempenho para um problema comum específico para cada localização geográfica onde os usuários acessam seu locatário.</span><span class="sxs-lookup"><span data-stu-id="4787f-107">Each insight provides live details about the performance characteristics for a specific common issue for each geographic location where users are accessing your tenant.</span></span>

<span data-ttu-id="4787f-108">Há cinco insights de rede específicos que podem ser mostradas para cada local do escritório:</span><span class="sxs-lookup"><span data-stu-id="4787f-108">There are five specific network insights that may be shown for each office location:</span></span>

- [<span data-ttu-id="4787f-109">Saída de rede de rebocada</span><span class="sxs-lookup"><span data-stu-id="4787f-109">Backhauled network egress</span></span>](#backhauled-network-egress)
- [<span data-ttu-id="4787f-110">Melhor desempenho detectado para clientes próximos de você</span><span class="sxs-lookup"><span data-stu-id="4787f-110">Better performance detected for customers near you</span></span>](#better-performance-detected-for-customers-near-you)
- [<span data-ttu-id="4787f-111">Uso de uma porta frontal de serviço do Exchange Online não ideal</span><span class="sxs-lookup"><span data-stu-id="4787f-111">Use of a non-optimal Exchange Online service front door</span></span>](#use-of-a-non-optimal-exchange-online-service-front-door)
- [<span data-ttu-id="4787f-112">Uso de uma porta frontal não ideal do SharePoint Online Service</span><span class="sxs-lookup"><span data-stu-id="4787f-112">Use of a non-optimal SharePoint Online service front door</span></span>](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [<span data-ttu-id="4787f-113">Baixa velocidade de download da porta frontal do SharePoint</span><span class="sxs-lookup"><span data-stu-id="4787f-113">Low download speed from SharePoint front door</span></span>](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
><span data-ttu-id="4787f-114">Os insights de rede, as recomendações de desempenho e as avaliações no centro de administração do Microsoft 365 estão atualmente no status de visualização e só estão disponíveis para os locatários do Office 365 que foram registrados no programa de visualização de recurso.</span><span class="sxs-lookup"><span data-stu-id="4787f-114">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="4787f-115">Saída de rede de rebocada</span><span class="sxs-lookup"><span data-stu-id="4787f-115">Backhauled network egress</span></span>

<span data-ttu-id="4787f-116">Esta percepção será exibida se o serviço de insights de rede detectar que a distância de um determinado local de usuário para a saída da rede é maior que 500 milhas (800 quilômetros), indicando que o tráfego do Office 365 está sendo repassado para uma borda de Internet comum dispositivo ou proxy.</span><span class="sxs-lookup"><span data-stu-id="4787f-116">This insight will be displayed if the network insights service detects that the distance from a given user location to the network egress is greater than 500 miles (800 kilometers), indicating that Office 365 traffic is being backhauled to a common Internet edge device or proxy.</span></span>

<span data-ttu-id="4787f-117">Esta percepção é abreviada como "egresso" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="4787f-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

![Saída de rede de rebocada](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="4787f-119">Cenário</span><span class="sxs-lookup"><span data-stu-id="4787f-119">What does this mean?</span></span>

<span data-ttu-id="4787f-120">Isso identifica que a distância entre o local do escritório e a egresso da rede é maior que 500 milhas (800 quilômetros).</span><span class="sxs-lookup"><span data-stu-id="4787f-120">This identifies that the distance between the office location and the network egress is more than 500 miles (800 kilometers).</span></span> <span data-ttu-id="4787f-121">O local do Office é identificado por um local de máquina cliente ofuscado e o local de egresso de rede é identificado usando o endereço IP reverso para os bancos de dados de local.</span><span class="sxs-lookup"><span data-stu-id="4787f-121">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="4787f-122">O local do escritório pode ser impreciso se os serviços de localização do Windows estiverem desabilitados nos computadores.</span><span class="sxs-lookup"><span data-stu-id="4787f-122">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="4787f-123">O local de egresso de rede pode ser impreciso se as informações do banco de dados de endereço IP reverso não forem precisas.</span><span class="sxs-lookup"><span data-stu-id="4787f-123">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="4787f-124">Os detalhes desta percepção incluem o local do escritório, porcentagem estimada do usuário do locatário total no local, o local de egresso da rede atual, relevância do local de egresso, a distância entre o local e o ponto de saída atual, a data em que o a condição foi detectada pela primeira vez e a data em que a condição foi resolvida.</span><span class="sxs-lookup"><span data-stu-id="4787f-124">Details for this insight include the office location, estimated percentage of total tenant user at the location, the current network egress location, relevance of the egress location, the distance between the location and the current egress point, the date the condition was first detected, and the date the condition was resolved.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4787f-125">O que devo fazer?</span><span class="sxs-lookup"><span data-stu-id="4787f-125">What should I do?</span></span>

<span data-ttu-id="4787f-126">Para esta percepção, recomendamos que a saída da rede fique mais próxima do local do escritório, de forma que a conectividade possa ser roteada de maneira ideal para a rede global da Microsoft e para a porta frontal de serviço mais próxima do Office 365.</span><span class="sxs-lookup"><span data-stu-id="4787f-126">For this insight, we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's global network and to the nearest Office 365 service front door.</span></span> <span data-ttu-id="4787f-127">Após o fechamento de egresso da rede para usuários, os locais do Office também podem melhorar o desempenho no futuro, já que a Microsoft expande tanto os pontos de presença de rede quanto as portas de serviço do Office 365 no futuro.</span><span class="sxs-lookup"><span data-stu-id="4787f-127">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="4787f-128">Para obter mais informações sobre como resolver esse problema, confira [conexões de rede de saída localmente](office-365-network-connectivity-principles.md#egress-network-connections-locally) nos [princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md).</span><span class="sxs-lookup"><span data-stu-id="4787f-128">For more information about how to resolve this issue, see [Egress network connections locally](office-365-network-connectivity-principles.md#egress-network-connections-locally) in [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="4787f-129">Melhor desempenho detectado para clientes próximos de você</span><span class="sxs-lookup"><span data-stu-id="4787f-129">Better performance detected for customers near you</span></span>

<span data-ttu-id="4787f-130">Esta percepção será exibida se o serviço de insights de rede detectar que um número significativo de clientes em sua área de metrô tem melhor desempenho do que os usuários em sua organização nesse local do escritório.</span><span class="sxs-lookup"><span data-stu-id="4787f-130">This insight will be displayed if the network insights service detects that a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="4787f-131">Esta percepção é abreviada como "pares" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="4787f-131">This insight is abbreviated as "Peers" in some summary views.</span></span>

![Desempenho de rede relativo](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="4787f-133">Cenário</span><span class="sxs-lookup"><span data-stu-id="4787f-133">What does this mean?</span></span>

<span data-ttu-id="4787f-134">Essa percepção examina o desempenho agregado dos clientes do Office 365 na mesma cidade que este local do escritório.</span><span class="sxs-lookup"><span data-stu-id="4787f-134">This insight examines the aggregate performance of Office 365 customers in the same city as this office location.</span></span> <span data-ttu-id="4787f-135">Esta percepção será exibida se a latência média de seus usuários for 10% maior do que a latência média dos locatários vizinhos.</span><span class="sxs-lookup"><span data-stu-id="4787f-135">This insight is displayed if the average latency of your users is 10% greater than the average latency of neighboring tenants.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4787f-136">O que devo fazer?</span><span class="sxs-lookup"><span data-stu-id="4787f-136">What should I do?</span></span>

<span data-ttu-id="4787f-137">Pode haver vários motivos para esta condição, incluindo latência na rede corporativa ou no provedor de Internet, afunilamentos ou problemas de design de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="4787f-137">There could be many reasons for this condition, including latency in your corporate network or ISP, bottlenecks, or architecture design issues.</span></span> <span data-ttu-id="4787f-138">Examine a latência entre cada salto na rota entre a rede do Office e a porta frontal atual do Office 365.</span><span class="sxs-lookup"><span data-stu-id="4787f-138">Examine the latency between each hop in the route between your office network and the current Office 365 front door.</span></span> <span data-ttu-id="4787f-139">Para obter mais informações, consulte [princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md).</span><span class="sxs-lookup"><span data-stu-id="4787f-139">For more information, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="4787f-140">Uso de uma porta frontal de serviço do Exchange Online não ideal</span><span class="sxs-lookup"><span data-stu-id="4787f-140">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="4787f-141">Esta percepção será exibida se o serviço de insights de rede detectar que os usuários em um local específico não estão se conectando a uma porta de entrada ideal do Exchange Online Service.</span><span class="sxs-lookup"><span data-stu-id="4787f-141">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to an optimal Exchange Online service front door.</span></span>

<span data-ttu-id="4787f-142">Esta percepção é abreviada como "roteamento" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="4787f-142">This insight is abbreviated as "Routing" in some summary views.</span></span>

![Porta frontal não ideal](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="4787f-144">Cenário</span><span class="sxs-lookup"><span data-stu-id="4787f-144">What does this mean?</span></span>

<span data-ttu-id="4787f-145">Listamos as portas frontais do serviço do Exchange Online que são adequadas para uso da cidade de local do escritório com bom desempenho.</span><span class="sxs-lookup"><span data-stu-id="4787f-145">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="4787f-146">Se o teste atual mostrar o uso de uma porta frontal do serviço do Exchange Online que não está nessa lista, chamamos essa recomendação.</span><span class="sxs-lookup"><span data-stu-id="4787f-146">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4787f-147">O que devo fazer?</span><span class="sxs-lookup"><span data-stu-id="4787f-147">What should I do?</span></span>

<span data-ttu-id="4787f-148">O uso de uma porta de entrada de serviço do Exchange Online não ideal pode ser causado pelo backhaul de rede antes da saída da rede corporativa, caso recomendamos a saída de rede local e direta.</span><span class="sxs-lookup"><span data-stu-id="4787f-148">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="4787f-149">Também pode ser causado pelo uso de um servidor de resolvedor de DNS recursivo remoto, caso recomendamos alinhar o servidor do resolvedor de DNS recursivo com a saída da rede.</span><span class="sxs-lookup"><span data-stu-id="4787f-149">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="4787f-150">Uso de uma porta frontal não ideal do SharePoint Online Service</span><span class="sxs-lookup"><span data-stu-id="4787f-150">Use of a non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="4787f-151">Esta percepção será exibida se o serviço de insights de rede detectar que os usuários em um local específico não estão se conectando à porta frontal mais próxima do SharePoint Online Service.</span><span class="sxs-lookup"><span data-stu-id="4787f-151">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to the closest SharePoint Online service front door.</span></span>

<span data-ttu-id="4787f-152">Esta percepção é abreviada como "AFD" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="4787f-152">This insight is abbreviated as "Afd" in some summary views.</span></span>

![Porta frontal não ideal](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="4787f-154">Cenário</span><span class="sxs-lookup"><span data-stu-id="4787f-154">What does this mean?</span></span>

<span data-ttu-id="4787f-155">Identificamos a porta frontal do serviço do SharePoint Online à qual o cliente de teste está se conectando.</span><span class="sxs-lookup"><span data-stu-id="4787f-155">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="4787f-156">Em seguida, para a cidade do local do escritório, comparamos isso à porta frontal do serviço do SharePoint Online esperado para essa cidade.</span><span class="sxs-lookup"><span data-stu-id="4787f-156">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="4787f-157">Se não coincidir, fazemos essa recomendação.</span><span class="sxs-lookup"><span data-stu-id="4787f-157">If it doesn't match, then we make this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4787f-158">O que devo fazer?</span><span class="sxs-lookup"><span data-stu-id="4787f-158">What should I do?</span></span>

<span data-ttu-id="4787f-159">O uso de uma porta de entrada de serviço do SharePoint Online não ideal pode ser causado pelo backhaul de rede antes da saída da rede corporativa, caso recomendamos a saída de rede local e direta.</span><span class="sxs-lookup"><span data-stu-id="4787f-159">Use of a non-optimal SharePoint Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="4787f-160">Também pode ser causado pelo uso de um servidor de resolvedor de DNS recursivo remoto, caso recomendamos alinhar o servidor do resolvedor de DNS recursivo com a saída da rede.</span><span class="sxs-lookup"><span data-stu-id="4787f-160">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="4787f-161">Baixa velocidade de download da porta frontal do SharePoint</span><span class="sxs-lookup"><span data-stu-id="4787f-161">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="4787f-162">Esta percepção será exibida se o serviço de insights de rede detectar essa largura de banda entre o local específico do Office e o SharePoint Online for menor que 1 MBps.</span><span class="sxs-lookup"><span data-stu-id="4787f-162">This insight will be displayed if the network insights service detects that bandwidth between the specific office location and SharePoint Online is less than 1 MBps.</span></span>

<span data-ttu-id="4787f-163">Esta percepção é abreviada como "throughput" em alguns modos de exibição de resumo.</span><span class="sxs-lookup"><span data-stu-id="4787f-163">This insight is abbreviated as "Throughput" in some summary views.</span></span>

### <a name="what-does-this-mean"></a><span data-ttu-id="4787f-164">Cenário</span><span class="sxs-lookup"><span data-stu-id="4787f-164">What does this mean?</span></span>

<span data-ttu-id="4787f-165">A velocidade de download que um usuário pode obter do SharePoint Online e do OneDrive for Business Service Doors é medida em megabytes por segundo (MBps).</span><span class="sxs-lookup"><span data-stu-id="4787f-165">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="4787f-166">Se esse valor for menor que 1 MBps, forneceremos esta percepção.</span><span class="sxs-lookup"><span data-stu-id="4787f-166">If this value is less than 1 MBps then we provide this insight.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4787f-167">O que devo fazer?</span><span class="sxs-lookup"><span data-stu-id="4787f-167">What should I do?</span></span>

<span data-ttu-id="4787f-168">Para melhorar as velocidades de download, a largura de banda pode precisar ser aumentada.</span><span class="sxs-lookup"><span data-stu-id="4787f-168">To improve download speeds, bandwidth may need to be increased.</span></span> <span data-ttu-id="4787f-169">Como alternativa, pode haver congestionamento de rede entre máquinas de usuário no local do escritório e na porta frontal do serviço do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4787f-169">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="4787f-170">Isso às vezes é chamado de perda congestionada e restringe a velocidade de download disponível para os usuários, mesmo se houver largura de banda suficiente disponível.</span><span class="sxs-lookup"><span data-stu-id="4787f-170">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

## <a name="china-user-optimal-network-egress"></a><span data-ttu-id="4787f-171">Saída de rede ideal para o usuário da China</span><span class="sxs-lookup"><span data-stu-id="4787f-171">China user optimal network egress</span></span>

<span data-ttu-id="4787f-172">Esta percepção será exibida se sua organização tiver usuários na China se conectarem ao seu locatário do Office 365 em outros locais geográficos.</span><span class="sxs-lookup"><span data-stu-id="4787f-172">This insight will be displayed if your organization has users in China connecting to your Office 365 tenant in other geographic locations.</span></span> 

### <a name="what-does-this-mean"></a><span data-ttu-id="4787f-173">Cenário</span><span class="sxs-lookup"><span data-stu-id="4787f-173">What does this mean?</span></span>

<span data-ttu-id="4787f-174">Se sua organização tem conectividade de WAN privada, recomendamos configurar um circuito de WAN de rede de seus locais do Office na China que têm a saída da rede para a Internet em qualquer um dos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="4787f-174">If your organization has private WAN connectivity, we recommend configuring a network WAN circuit from your office locations in China that has network egress to the Internet in any of the following locations:</span></span>

- <span data-ttu-id="4787f-175">Hong-Kong</span><span class="sxs-lookup"><span data-stu-id="4787f-175">Hong Kong</span></span>
- <span data-ttu-id="4787f-176">Japão</span><span class="sxs-lookup"><span data-stu-id="4787f-176">Japan</span></span>
- <span data-ttu-id="4787f-177">Taiwan</span><span class="sxs-lookup"><span data-stu-id="4787f-177">Taiwan</span></span>
- <span data-ttu-id="4787f-178">Coreia do Sul</span><span class="sxs-lookup"><span data-stu-id="4787f-178">South Korea</span></span>
- <span data-ttu-id="4787f-179">Cingapura</span><span class="sxs-lookup"><span data-stu-id="4787f-179">Singapore</span></span>
- <span data-ttu-id="4787f-180">Malásia</span><span class="sxs-lookup"><span data-stu-id="4787f-180">Malaysia</span></span>

<span data-ttu-id="4787f-181">O egresso de Internet mais distante dos usuários do que esses locais reduzirá o desempenho e o egresso na China pode causar problemas de alta latência e conectividade devido a um congestionamento entre bordas.</span><span class="sxs-lookup"><span data-stu-id="4787f-181">Internet egress further away from users than these locations will reduce performance, and egress in China may cause high latency and connectivity issues due to cross-border congestion.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4787f-182">O que devo fazer?</span><span class="sxs-lookup"><span data-stu-id="4787f-182">What should I do?</span></span>

<span data-ttu-id="4787f-183">Para obter mais informações sobre como reduzir problemas de desempenho relacionados a essa percepção, consulte [Office 365 global locatário Performance Optimization for China Users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).</span><span class="sxs-lookup"><span data-stu-id="4787f-183">For more information about how to mitigate performance issues related to this insight, see [Office 365 global tenant performance optimization for China users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).</span></span>

## <a name="related-topics"></a><span data-ttu-id="4787f-184">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="4787f-184">Related topics</span></span>

[<span data-ttu-id="4787f-185">Recomendações de desempenho de rede no centro de administração do Microsoft 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="4787f-185">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="4787f-186">Avaliação de rede do Office 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="4787f-186">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="4787f-187">Ferramenta de integração de rede do Office 365 no centro de administração do M365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="4787f-187">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
