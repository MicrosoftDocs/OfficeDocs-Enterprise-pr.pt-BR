---
title: 'Visão geral: túnel dividido de VPN com o Office 365'
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/27/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Diretrizes para o uso de túnel dividido de VPN com o Office 365 para otimizar a conectividade do Office 365 para usuários remotos.
ms.openlocfilehash: 3ba52ecdb6e22c234cc0f208ae3ca40b3cb06b6d
ms.sourcegitcommit: c081928170e2a56bc0627e5ec8174c1152fcc151
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2020
ms.locfileid: "43034816"
---
# <a name="optimize-office-365-connectivity-for-remote-users-using-vpn-split-tunnelling"></a><span data-ttu-id="8b0a2-103">Otimizar a conectividade do Office 365 para usuários remotos usando o túnel dividido de VPN</span><span class="sxs-lookup"><span data-stu-id="8b0a2-103">Optimize Office 365 connectivity for remote users using VPN split tunnelling</span></span>
<!---
>[!NOTE]
>This topic is part of a set of topics that address Office 365 optimization for remote users.
>- For VPN split tunnel implementation guidance, see [Implementing VPN split tunnelling for Office 365](office-365-vpn-implement-split-tunnel.md).
>- For information about optimizing Office 365 worldwide tenant performance for users in China, see [Office 365 performance optimization for China users](office-365-networking-china.md).
-->

<span data-ttu-id="8b0a2-104">Para os clientes que conectam os dispositivos de funcionários remotos à rede corporativa ou à infraestrutura de nuvem através de VPN, a Microsoft recomenda que os principais cenários do Office 365, **Microsoft Teams**, **SharePoint Online** e **Exchange Online** sejam roteados através de uma configuração de _túnel dividido de VPN_.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-104">For customers who connect their remote worker devices to the corporate network or cloud infrastructure over VPN, Microsoft recommends that the key Office 365 scenarios **Microsoft Teams**, **SharePoint Online** and **Exchange Online** are routed over a _VPN split tunnel_ configuration.</span></span> <span data-ttu-id="8b0a2-105">Isso se torna especialmente importante como estratégia de primeira linha para facilitar a produtividade contínua dos funcionários durante eventos em larga escala de trabalho em casa, como a pandemia de COVID-19.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-105">This becomes especially important as the first line strategy to facilitate continued employee productivity during large scale work-from-home events such as the COVID-19 pandemic.</span></span>

![Configuração de VPN de túnel dividido](media/vpn-split-tunnelling/vpn-model-2.png)

<span data-ttu-id="8b0a2-107">_Figura 1: uma solução VPN de túnel dividido com exceções definidas do Office 365, enviada diretamente para o serviço. Todo o tráfego restante atravessa o túnel VPN, independentemente do destino._</span><span class="sxs-lookup"><span data-stu-id="8b0a2-107">_Figure 1: A VPN split tunnel solution with defined Office 365 exceptions sent directly to the service. All other traffic traverses the VPN tunnel regardless of destination._</span></span>

<span data-ttu-id="8b0a2-108">A essência dessa abordagem é fornecer um método simples para as empresas diminuírem o risco de saturação da infraestrutura VPN e melhorar drasticamente o desempenho do Office 365 no menor espaço de tempo possível.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-108">The essence of this approach is to provide a simple method for enterprises to mitigate the risk of VPN infrastructure saturation and dramatically improve Office 365 performance in the shortest timeframe possible.</span></span> <span data-ttu-id="8b0a2-109">Para permitir que o tráfego de alto volume e mais crítico do Office 365 contorne o túnel VPN, a configuração de clientes VPN tem os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="8b0a2-109">Configuring VPN clients to allow the most critical, high volume Office 365 traffic to bypass the VPN tunnel achieves the following benefits:</span></span>

- <span data-ttu-id="8b0a2-110">Ameniza imediatamente a causa raiz da maioria dos problemas de capacidade de rede e de desempenho relatados pelos clientes nas arquiteturas VPN corporativas que impactam a experiência do usuário do Office 365</span><span class="sxs-lookup"><span data-stu-id="8b0a2-110">Immediately mitigates the root cause of a majority of customer-reported performance and network capacity issues in enterprise VPN architectures impacting Office 365 user experience</span></span>
  
  <span data-ttu-id="8b0a2-111">A solução recomendada visa especificamente os pontos de extremidade de serviço do Office 365 categorizados como **Otimizar** no tópico [URLs e intervalos de endereço IP do Office 365](https://aka.ms/o365ips).</span><span class="sxs-lookup"><span data-stu-id="8b0a2-111">The recommended solution specifically targets Office 365 service endpoints categorized as **Optimize** in the topic [Office 365 URLs and IP address ranges](https://aka.ms/o365ips).</span></span> <span data-ttu-id="8b0a2-112">O tráfego para esses pontos de extremidade é altamente sensível à latência e limitação da largura de banda, e permitir que ele contorne o túnel VPN pode melhorar significativamente a experiência do usuário final, bem como reduzir a carga da rede corporativa.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-112">Traffic to these endpoints is highly sensitive to latency and bandwidth throttling, and enabling it to bypass the VPN tunnel can dramatically improve the end user experience as well as reduce the corporate network load.</span></span> <span data-ttu-id="8b0a2-113">As conexões do Office 365 que não constituem a maior parte da largura de banda ou da área de cobertura da experiência do usuário podem continuar a ser roteadas através do túnel VPN juntamente com o resto do tráfego de Internet.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-113">Office 365 connections that do not constitute the majority of bandwidth or user experience footprint can continue to be routed through the VPN tunnel along with the rest of the Internet-bound traffic.</span></span> <span data-ttu-id="8b0a2-114">Para obter mais informações, confira [A estratégia de túnel dividido de VPN](#the-vpn-split-tunnel-strategy).</span><span class="sxs-lookup"><span data-stu-id="8b0a2-114">For more information, see [The VPN split tunnel strategy](#the-vpn-split-tunnel-strategy).</span></span>

- <span data-ttu-id="8b0a2-115">Pode ser configurado, testado e implementado rapidamente pelos clientes, sem requisitos adicionais de infraestrutura ou aplicativos</span><span class="sxs-lookup"><span data-stu-id="8b0a2-115">Can be configured, tested and implemented rapidly by customers and with no additional infrastructure or application requirements</span></span>

  <span data-ttu-id="8b0a2-116">Dependendo da plataforma VPN e da arquitetura de rede, a implementação pode levar apenas algumas horas.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-116">Depending on the VPN platform and network architecture, implementation can take as little as a few hours.</span></span> <span data-ttu-id="8b0a2-117">Para obter mais informações, confira [Implementar o túnel divido de VPN](office-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunnelling).</span><span class="sxs-lookup"><span data-stu-id="8b0a2-117">For more information, see [Implement VPN split tunnelling](office-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunnelling).</span></span>

- <span data-ttu-id="8b0a2-118">Preserva a postura de segurança das implementações de VPN do cliente, não alterando a forma como outras conexões são roteadas, incluindo o tráfego da Internet</span><span class="sxs-lookup"><span data-stu-id="8b0a2-118">Preserves the security posture of customer VPN implementations by not changing how other connections are routed, including traffic to the Internet</span></span>

  <span data-ttu-id="8b0a2-119">A configuração recomendada segue o princípio de **privilégios mínimos** para exceções de tráfego VPN, e permite aos clientes implementar o túnel dividido de VPN sem expor os usuários ou a infraestrutura a riscos de segurança adicionais.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-119">The recommended configuration follows the **least privilege** principle for VPN traffic exceptions and allows customers to implement split tunnel VPN without exposing users or infrastructure to additional security risks.</span></span> <span data-ttu-id="8b0a2-120">O tráfego de rede roteado diretamente aos pontos de extremidade do Office 365 é criptografado, validado para integridade pelas pilhas de aplicativos do cliente Office e escopo de endereços IP dedicados aos serviços do Office 365, que são reforçados no nível do aplicativo e da rede.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-120">Network traffic routed directly to Office 365 endpoints is encrypted, validated for integrity by Office client application stacks and scoped to IP addresses dedicated to Office 365 services which are hardened at both the application and network level.</span></span> <span data-ttu-id="8b0a2-121">Para obter mais informações, confira [Maneiras alternativas para profissionais de segurança e TI alcançarem controles de segurança modernos nos cenários atuais de trabalho remoto (blog da equipe de segurança da Microsoft) ](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)</span><span class="sxs-lookup"><span data-stu-id="8b0a2-121">For more information, see [Alternative ways for security professionals and IT to achieve modern security controls in today's unique remote work scenarios (Microsoft Security Team blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).</span></span>

- <span data-ttu-id="8b0a2-122">Tem suporte nativo pela maioria das plataformas de VPN corporativas</span><span class="sxs-lookup"><span data-stu-id="8b0a2-122">Is natively supported by most enterprise VPN platforms</span></span>

  <span data-ttu-id="8b0a2-123">A Microsoft continua colaborando com parceiros industriais que produzem soluções de VPN comerciais para ajudar os parceiros a desenvolver modelos de configuração e diretrizes direcionadas para as suas soluções, em alinhamento com as recomendações acima.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-123">Microsoft continues to collaborate with industry partners producing commercial VPN solutions to help partners develop targeted guidance and configuration templates for their solutions in alignment with the above recommendations.</span></span> <span data-ttu-id="8b0a2-124">Para obter mais informações, confira [Guias HOWTO para plataformas VPN comuns](office-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).</span><span class="sxs-lookup"><span data-stu-id="8b0a2-124">For more information, see [HOWTO guides for common VPN platforms](office-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).</span></span>

>[!TIP]
><span data-ttu-id="8b0a2-125">A Microsoft recomenda a configuração de VPN de túnel dividido em intervalos de IP dedicados e documentados para serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-125">Microsoft recommends focusing split tunnel VPN configuration on documented dedicated IP ranges for Office 365 services.</span></span> <span data-ttu-id="8b0a2-126">As configurações de túnel dividido de FQDN ou baseadas no AppID, embora possível em determinadas plataformas de cliente VPN, podem não abranger todos os cenários essenciais do Office 365 e podem entrar em conflito com regras de roteamento VPN baseadas em IP.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-126">FQDN or AppID-based split tunnel configurations, while possible on certain VPN client platforms, may not fully cover key Office 365 scenarios and may conflict with IP based VPN routing rules.</span></span> <span data-ttu-id="8b0a2-127">Por esse motivo, a Microsoft não recomenda usar os FQDNs do Office 365 para configurar a VPN de túnel dividido.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-127">For this reason, Microsoft does not recommend using Office 365 FQDNs to configure split tunnel VPN.</span></span> <span data-ttu-id="8b0a2-128">O uso da configuração de FQDN pode ser útil em outros cenários relacionados, como personalizações de arquivos .pac ou para implementar um proxy ignorável.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-128">The use of FQDN configuration may be useful in other related scenarios, such as .pac file customizations or to implement proxy bypass.</span></span>

<span data-ttu-id="8b0a2-129">Para obter diretrizes completas de implementação, confira [Implementando o túnel dividido de VPN para Office 365](office-365-vpn-implement-split-tunnel.md).</span><span class="sxs-lookup"><span data-stu-id="8b0a2-129">For full implementation guidance, see [Implementing VPN split tunnelling for Office 365](office-365-vpn-implement-split-tunnel.md).</span></span>

## <a name="the-vpn-split-tunnel-strategy"></a><span data-ttu-id="8b0a2-130">A estratégia de túnel dividido VPN</span><span class="sxs-lookup"><span data-stu-id="8b0a2-130">The VPN split tunnel strategy</span></span>

<span data-ttu-id="8b0a2-131">Geralmente, as redes corporativas tradicionais são projetadas para trabalhar de forma segura no mundo da nuvem, em que os dados, os serviços e os aplicativos mais importantes estão hospedados no local e podem ser conectados diretamente à rede corporativa interna, como a maioria dos usuários.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-131">Traditional corporate networks are often designed to work securely for a pre-cloud world where most important data, services, applications are hosted on premises and are directly connected to the internal corporate network, as are the majority of users.</span></span> <span data-ttu-id="8b0a2-132">Assim, a infraestrutura de rede é construída em torno desses elementos, em que as filiais estão conectadas à sede através de redes _MPLS (Multiprotocol Label Switching)_, e os usuários remotos se conectam à rede corporativa através de uma VPN para acessar os pontos de extremidade locais e a Internet.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-132">Thus network infrastructure is built around these elements in that branch offices are connected to the head office via _Multiprotocol Label Switching (MPLS)_ networks, and remote users must connect to the corporate network over a VPN to access both on premises endpoints and the Internet.</span></span> <span data-ttu-id="8b0a2-133">Nesse modelo, todo o tráfego de usuários remotos passa pela rede corporativa e é direcionado para o serviço de nuvem por meio de um ponto de saída comum.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-133">In this model, all traffic from remote users traverses the corporate network and is routed to the cloud service through a common egress point.</span></span>

![Configuração de VPN forçada](media/vpn-split-tunnelling/vpn-model-1.png)

<span data-ttu-id="8b0a2-135">_Figura 2: uma solução de VPN comum para usuários remotos onde todo o tráfego é forçado de volta para a rede corporativa, independentemente do destino_</span><span class="sxs-lookup"><span data-stu-id="8b0a2-135">_Figure 2: A common VPN solution for remote users where all traffic is forced back into the corporate network regardless of destination_</span></span>

<span data-ttu-id="8b0a2-136">À medida que as organizações movem dados e aplicativos para a nuvem, esse modelo começou a se tornar menos eficaz, pois rapidamente se torna incômodo, caro e instável, afetando significativamente o desempenho da rede e a eficiência dos usuários, bem com restringindo a capacidade da organização de se adaptar às necessidades de mudança.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-136">As organizations move data and applications to the cloud, this model has begun to become less effective as it quickly becomes cumbersome, expensive and unscalable, significantly impacting network performance and efficiency of users and restricting the ability of the organization to adapt to changing needs.</span></span> <span data-ttu-id="8b0a2-137">Muitos clientes da Microsoft relataram que há alguns anos atrás, 80% do tráfego da rede era para um destino interno, mas em 2020, mais de 80% do tráfego se conecta a um recurso externo baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-137">Numerous Microsoft customers have reported that a few years ago 80% of network traffic was to an internal destination, but in 2020 80% plus of traffic connects to an external cloud based resource.</span></span>

<span data-ttu-id="8b0a2-138">A crise da COVID-19 agravou esse problema, exigindo soluções imediatas pela maioria das organizações.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-138">The COVID-19 crisis has aggravated this problem to require immediate solutions for the vast majority of organizations.</span></span> <span data-ttu-id="8b0a2-139">Muitos clientes descobriram que o modelo de VPN forçado não é escalável ou suficientemente eficaz para cenários de trabalho 100% remotos, como o que essa crise tem exigido.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-139">Many customers have found that the forced VPN model is not scalable or performant enough for 100% remote work scenarios such as that which this crisis has necessitated.</span></span> <span data-ttu-id="8b0a2-140">Soluções rápidas são necessárias para que essas organizações continuem a funcionar eficientemente.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-140">Rapid solutions are required for these organization to continue to operate efficiently.</span></span>

<span data-ttu-id="8b0a2-141">Para o serviço do Office 365, a Microsoft desenvolveu os requisitos de conectividade para esse serviço tendo esse problema em mente, onde um focado conjunto de pontos de extremidade, fortemente controlado e relativamente estático pode ser otimizado de forma muito simples e rápida. De modo que ofereça alto desempenho aos usuários que acessam o serviço e reduzir a carga sobre a infraestrutura de VPN, para que ela possa ser usada pelo tráfego que ainda o requer.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-141">For the Office 365 service, Microsoft has designed the connectivity requirements for the service with this problem squarely in mind, where a focused, tightly controlled and relatively static set of service endpoints can be optimized very simply and quickly so as to deliver high performance for users accessing the service, and reducing the burden on the VPN infrastructure so it can be used by traffic which still requires it.</span></span>

<span data-ttu-id="8b0a2-142">O Office 365 categoriza os pontos de extremidade necessários para o Office 365 em três categorias: **Optimizar**, **Permitir** e **Padrão**.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-142">Office 365 categorizes the required endpoints for Office 365 into three categories: **Optimize**, **Allow** and **Default**.</span></span> <span data-ttu-id="8b0a2-143">**Otimizar** os pontos de extremidade é o nosso foco aqui e têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="8b0a2-143">**Optimize** endpoints are our focus here and have the following characteristics:</span></span>

- <span data-ttu-id="8b0a2-144">São pontos de extremidade de propriedade e gerenciados peça Microsoft, hospedados na infraestrutura da Microsoft</span><span class="sxs-lookup"><span data-stu-id="8b0a2-144">Are Microsoft owned and managed endpoints, hosted on Microsoft infrastructure</span></span>
- <span data-ttu-id="8b0a2-145">Tem IPs fornecidos</span><span class="sxs-lookup"><span data-stu-id="8b0a2-145">Have IPs provided</span></span>
- <span data-ttu-id="8b0a2-146">Baixa taxa de alteração e espera-se que permaneça menor em número (atualmente 20 sub-redes de IP)</span><span class="sxs-lookup"><span data-stu-id="8b0a2-146">Low rate of change and are expected to remain small in number(currently 20 IP subnets)</span></span>
- <span data-ttu-id="8b0a2-147">São sensíveis a alto volume e/ou latência</span><span class="sxs-lookup"><span data-stu-id="8b0a2-147">Are high volume and/or latency sensitive</span></span>
- <span data-ttu-id="8b0a2-148">É possível ter os elementos de segurança necessários no serviço, em vez de embutido na rede</span><span class="sxs-lookup"><span data-stu-id="8b0a2-148">Are able to have required security elements provided in the service rather than inline on the network</span></span>
- <span data-ttu-id="8b0a2-149">Representam aproximadamente 70-80% do volume de tráfego para o serviço do Office 365</span><span class="sxs-lookup"><span data-stu-id="8b0a2-149">Account for around 70-80% of the volume of traffic to the Office 365 service</span></span>

<span data-ttu-id="8b0a2-150">Este conjunto de pontos de extremidade com um escopo apertado pode ser dividido do túnel de VPN forçado e enviado com segurança e diretamente para o serviço do Office 365 pela interface local do usuário.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-150">This tightly scoped set of endpoints can be split out of the forced VPN tunnel and sent securely and directly to the Office 365 service via the user's local interface.</span></span> <span data-ttu-id="8b0a2-151">Isso é conhecido como **túnel dividido**.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-151">This is known as **split tunnelling**.</span></span>

<span data-ttu-id="8b0a2-152">Elementos de segurança como DLP, proteção antivírus, autenticação e controle de acesso podem ser entregues de forma muito mais eficiente em relação a esses pontos de extremidades em diferentes camadas dentro do serviço.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-152">Security elements such as DLP, AV protection, authentication and access control can all be delivered much more efficiently against these endpoints at different layers within the service.</span></span> <span data-ttu-id="8b0a2-153">Como também desviamos a maior parte do volume de tráfego da solução VPN, isto libera a capacidade do VPN para o tráfego crítico do negócio que ainda depende dele.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-153">As we also divert the bulk of the traffic volume away from the VPN solution, this frees the VPN capacity up for business critical traffic which still relies on it.</span></span> <span data-ttu-id="8b0a2-154">Isso também deve eliminar a necessidade, em muitos casos, de passar por um longo e dispendioso programa de atualização para lidar com essa nova maneira de operar.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-154">It also should remove the need in many cases to go through a lengthy and costly upgrade program to deal with this new way of operating.</span></span>

![Configuração de VPN de túnel dividido](media/vpn-split-tunnelling/vpn-model-2.png)

<span data-ttu-id="8b0a2-156">_Figura 3: uma solução VPN de túnel dividido com exceções definidas do Office 365, enviada diretamente para o serviço. Todo o restante tráfego é forçado a voltar para a rede corporativa, independentemente do destino._</span><span class="sxs-lookup"><span data-stu-id="8b0a2-156">_Figure 3: A VPN split tunnel solution with defined Office 365 exceptions sent direct to the service. All other traffic is forced back into the corporate network regardless of destination._</span></span>

<span data-ttu-id="8b0a2-157">Do ponto de vista da segurança, a Microsoft tem uma série de recursos de segurança que podem ser usados para fornecer segurança semelhante, ou mesmo melhor do que aquela entregue pela inspeção inline por pilhas de segurança locais.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-157">From a security perspective, Microsoft has an array of security features which can be used to provide similar, or even enhanced security than that delivered by inline inspection by on premises security stacks.</span></span> <span data-ttu-id="8b0a2-158">A postagem do blog da equipe de segurança da Microsoft [Maneiras alternativas para profissionais de segurança e TI alcançarem controles de segurança modernos nos cenários atuais de trabalho remoto](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/), tem um resumo claro dos recursos disponíveis e você encontrará uma orientação mais detalhada neste artigo.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-158">The Microsoft Security team's blog post [Alternative ways for security professionals and IT to achieve modern security controls in today's unique remote work scenarios](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) has a clear summary of features available and you'll find more detailed guidance within this article.</span></span> <span data-ttu-id="8b0a2-159">Você também pode ler sobre a implementação da Microsoft de túneis divididos de VPN em [Trabalhando no VPN: como a Microsoft mantém sua força de trabalho remota conectada](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).</span><span class="sxs-lookup"><span data-stu-id="8b0a2-159">You can also read about Microsoft's implementation of VPN split tunnelling at [Running on VPN: How Microsoft is keeping its remote workforce connected](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).</span></span>

<span data-ttu-id="8b0a2-160">Em muitos casos, esta implementação pode ser alcançada em questão de horas, permitindo uma solução rápida de um dos problemas mais urgentes que as organizações enfrentam à medida que mudam rapidamente para o trabalho remoto em escala real.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-160">In many cases, this implementation can be achieved in a matter of hours, allowing rapid resolution to one of the most pressing problems facing organizations as they rapidly shift to full scale remote working.</span></span> <span data-ttu-id="8b0a2-161">Para obter orientações sobre a implementação de túneis divididos de VPN, confira [Implementando o túnel dividido de VPN para Office 365](office-365-vpn-implement-split-tunnel.md).</span><span class="sxs-lookup"><span data-stu-id="8b0a2-161">For VPN split tunnel implementation guidance, see [Implementing VPN split tunnelling for Office 365](office-365-vpn-implement-split-tunnel.md).</span></span>

>[!NOTE]
><span data-ttu-id="8b0a2-162">A Microsoft tem o compromisso de suspender as alterações feitas para **Otimizar** os pontos de extremidade do Office 365 até pelo menos **30 de junho de 2020**, permitindo que os clientes se concentrem em outros desafios, em vez de manter a lista de permissões dos pontos de extremidade, uma vez implementada inicialmente.</span><span class="sxs-lookup"><span data-stu-id="8b0a2-162">Microsoft has committed to suspending changes to **Optimize** endpoints for Office 365 until at least **June 30 2020**, allowing customers to focus on other challenges rather than maintaining the endpoint whitelist once initially implemented.</span></span>

## <a name="related-topics"></a><span data-ttu-id="8b0a2-163">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="8b0a2-163">Related topics</span></span>

[<span data-ttu-id="8b0a2-164">Implementando o tunelamento dividido de VPN para Office 365</span><span class="sxs-lookup"><span data-stu-id="8b0a2-164">Implementing VPN split tunnelling for Office 365</span></span>](office-365-vpn-implement-split-tunnel.md)

[<span data-ttu-id="8b0a2-165">Otimização de desempenho do Office 365 para usuários da China</span><span class="sxs-lookup"><span data-stu-id="8b0a2-165">Office 365 performance optimization for China users</span></span>](office-365-networking-china.md)

[<span data-ttu-id="8b0a2-166">Maneiras alternativas para profissionais de segurança e TI alcançarem controles de segurança modernos nos cenários atuais de trabalho remoto (blog da equipe de segurança da Microsoft)</span><span class="sxs-lookup"><span data-stu-id="8b0a2-166">Alternative ways for security professionals and IT to achieve modern security controls in today's unique remote work scenarios (Microsoft Security Team blog)</span></span>](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[<span data-ttu-id="8b0a2-167">Trabalhando no VPN: Como a Microsoft mantém sua força de trabalho remota conectada</span><span class="sxs-lookup"><span data-stu-id="8b0a2-167">Running on VPN: How Microsoft is keeping its remote workforce connected</span></span>](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[<span data-ttu-id="8b0a2-168">Princípios de conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="8b0a2-168">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="8b0a2-169">Avaliando a conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="8b0a2-169">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="8b0a2-170">Ferramenta de integração de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="8b0a2-170">Office 365 Network Onboarding tool</span></span>](https://aka.ms/netonboard)