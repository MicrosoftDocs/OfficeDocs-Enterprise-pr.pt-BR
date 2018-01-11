---
title: Projetando a rede para o Microsoft SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Resumo: Entenda como otimizar sua rede para o acesso aos serviços de SaaS da Microsoft, incluindo o Office 365 e Microsoft Intune Dynamics 365."
ms.openlocfilehash: 970d27e50e06f4d872de67589295c490aaa6e0e7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="d2a83-103">Projetando a rede para o Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="d2a83-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="d2a83-104">**Resumo:** Compreenda como otimizar sua rede para o acesso aos serviços de SaaS da Microsoft, incluindo o Office 365 e Microsoft Intune Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="d2a83-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="d2a83-105">Otimizar sua rede para os serviços SaaS da Microsoft requer uma análise cuidadosa da borda de Internet, dos dispositivos do cliente e das operações típicas de TI.</span><span class="sxs-lookup"><span data-stu-id="d2a83-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="d2a83-106">Etapas para preparar sua rede para serviços SaaS da Microsoft</span><span class="sxs-lookup"><span data-stu-id="d2a83-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="d2a83-107">Siga estas etapas para otimizar a sua rede de serviços SaaS da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="d2a83-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="d2a83-108">Percorra a seção de **etapas para preparar sua rede para serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="d2a83-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="d2a83-109">Otimize sua saída da Internet para os serviços do Microsoft SaaS usando as recomendações do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="d2a83-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="d2a83-110">Otimize sua taxa de transferência da Internet usando as recomendações de proximidade e local.</span><span class="sxs-lookup"><span data-stu-id="d2a83-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="d2a83-111">Otimize o desempenho de seus computadores clientes e intranet em que eles estão localizados usando as considerações de uso do cliente.</span><span class="sxs-lookup"><span data-stu-id="d2a83-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="d2a83-112">Conforme necessário, otimize o desempenho de sincronização usando as considerações de operações de IT e migrações de dados.</span><span class="sxs-lookup"><span data-stu-id="d2a83-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="d2a83-113">Considerações sobre a borda da Internet</span><span class="sxs-lookup"><span data-stu-id="d2a83-113">Internet edge considerations</span></span>

<span data-ttu-id="d2a83-114">Aqui estão algumas coisas a considerar otimizam sua borda da Internet e a taxa de transferência aos serviços do Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="d2a83-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="d2a83-115">**Figura 1: Opções de Conexão para serviços SaaS da Microsoft**</span><span class="sxs-lookup"><span data-stu-id="d2a83-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![Figura 1: Opções de conexão para serviços SaaS da Microsoft](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="d2a83-117">A Figura 1 mostra uma rede local conectando-se aos serviços do Microsoft SaaS através de um pipe de Internet ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="d2a83-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="d2a83-118">Aqui estão algumas recomendações para otimizar o seu servidor proxy:</span><span class="sxs-lookup"><span data-stu-id="d2a83-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="d2a83-119">Configurar clientes web usando WPAD, PAC ou GPO</span><span class="sxs-lookup"><span data-stu-id="d2a83-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="d2a83-120">Não use a interceptação de SSL</span><span class="sxs-lookup"><span data-stu-id="d2a83-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="d2a83-121">Usar um arquivo PAC para ignorar o proxy para nomes DNS do serviço Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="d2a83-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="d2a83-122">Permitir o tráfego de verificação de CRL/OCSP</span><span class="sxs-lookup"><span data-stu-id="d2a83-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="d2a83-123">Aqui estão alguns afunilamentos de servidor proxy para verificar:</span><span class="sxs-lookup"><span data-stu-id="d2a83-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="d2a83-124">Conexões persistentes insuficientes (Outlook)</span><span class="sxs-lookup"><span data-stu-id="d2a83-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="d2a83-125">Capacidade suficiente</span><span class="sxs-lookup"><span data-stu-id="d2a83-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="d2a83-126">Fazendo a avaliação de fora da rede</span><span class="sxs-lookup"><span data-stu-id="d2a83-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="d2a83-127">Exigir autenticação</span><span class="sxs-lookup"><span data-stu-id="d2a83-127">Requiring authentication</span></span>
    
- <span data-ttu-id="d2a83-128">Não há suporte para o tráfego UDP (Skype para negócios)</span><span class="sxs-lookup"><span data-stu-id="d2a83-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="d2a83-129">Aqui estão algumas recomendações de proximidade e local:</span><span class="sxs-lookup"><span data-stu-id="d2a83-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="d2a83-130">Não rotear o tráfego da Internet pela WAN privada</span><span class="sxs-lookup"><span data-stu-id="d2a83-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="d2a83-131">Usar o fluxo de tráfego DNS e a Internet na região para usuários de fora da região</span><span class="sxs-lookup"><span data-stu-id="d2a83-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="d2a83-132">Use ExpressRoute para alta largura de banda para o Office 365 e conectividade simultânea com os serviços do Azure</span><span class="sxs-lookup"><span data-stu-id="d2a83-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="d2a83-133">Aqui estão as portas de saída necessárias para o tráfego do Office 365:</span><span class="sxs-lookup"><span data-stu-id="d2a83-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="d2a83-134">TCP 80 (para verificações CRL/OCSP)</span><span class="sxs-lookup"><span data-stu-id="d2a83-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="d2a83-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="d2a83-135">TCP 443</span></span>
    
- <span data-ttu-id="d2a83-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="d2a83-136">UDP 3478</span></span>
    
- <span data-ttu-id="d2a83-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="d2a83-137">TCP 5223</span></span>
    
- <span data-ttu-id="d2a83-138">TCP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="d2a83-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="d2a83-139">UDP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="d2a83-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="d2a83-140">Considerações de uso do cliente</span><span class="sxs-lookup"><span data-stu-id="d2a83-140">Client usage considerations</span></span>

<span data-ttu-id="d2a83-141">Primeiro, configure o conjunto de serviços que os clientes usarão, tais como:</span><span class="sxs-lookup"><span data-stu-id="d2a83-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="d2a83-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="d2a83-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="d2a83-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="d2a83-143">Office 365</span></span>
    
  - <span data-ttu-id="d2a83-144">Aplicativos de cliente do Office</span><span class="sxs-lookup"><span data-stu-id="d2a83-144">Office client apps</span></span>
    
  - <span data-ttu-id="d2a83-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d2a83-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="d2a83-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d2a83-146">Exchange Online</span></span>
    
  - <span data-ttu-id="d2a83-147">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="d2a83-147">Skype for Business</span></span>
    
- <span data-ttu-id="d2a83-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="d2a83-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="d2a83-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="d2a83-149">Dynamics 365</span></span>
    
<span data-ttu-id="d2a83-150">Para os computadores cliente, determine o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d2a83-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="d2a83-151">Número máximo de cada vez (hora do dia, sazonais, picos e os vales em uso)</span><span class="sxs-lookup"><span data-stu-id="d2a83-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="d2a83-152">Largura de banda total necessária para picos</span><span class="sxs-lookup"><span data-stu-id="d2a83-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="d2a83-153">Latência para o dispositivo de saída de Internet</span><span class="sxs-lookup"><span data-stu-id="d2a83-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="d2a83-154">País de origem versus país de localização conjunta do datacenter</span><span class="sxs-lookup"><span data-stu-id="d2a83-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="d2a83-155">Para cada tipo de cliente (PC, smartphone, tablet), verifique se o atual:</span><span class="sxs-lookup"><span data-stu-id="d2a83-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="d2a83-156">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="d2a83-156">Operating system</span></span>
    
- <span data-ttu-id="d2a83-157">Navegador da Internet</span><span class="sxs-lookup"><span data-stu-id="d2a83-157">Internet browser</span></span>
    
- <span data-ttu-id="d2a83-158">Pilha TCP/IP</span><span class="sxs-lookup"><span data-stu-id="d2a83-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="d2a83-159">Hardware de rede</span><span class="sxs-lookup"><span data-stu-id="d2a83-159">Network hardware</span></span>
    
- <span data-ttu-id="d2a83-160">Drivers de sistema operacional para o hardware de rede</span><span class="sxs-lookup"><span data-stu-id="d2a83-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="d2a83-161">Atualizações e patches estão instalados</span><span class="sxs-lookup"><span data-stu-id="d2a83-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="d2a83-162">Além disso, otimizar a taxa de transferência de conexão de intranet (com fio, sem fio ou VPN).</span><span class="sxs-lookup"><span data-stu-id="d2a83-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="d2a83-163">Para obter mais informações, consulte [suporte a NAT com o Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span><span class="sxs-lookup"><span data-stu-id="d2a83-163">For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span></span>
  
<span data-ttu-id="d2a83-164">Para obter as recomendações mais recentes para usar ExpressRoute com o Office 365, consulte [ExpressRoute para o Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="d2a83-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
<span data-ttu-id="d2a83-165">Para otimizar o desempenho da sua intranet, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d2a83-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="d2a83-166">Usar ferramentas para medir viagem de ida e tempo (RTTs) para seus dispositivos de borda da Internet (PsPing, Ping, Tracert, TraceTCP, Monitor de rede)</span><span class="sxs-lookup"><span data-stu-id="d2a83-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="d2a83-167">Executar a análise de caminho de saída usando os protocolos de fluxo</span><span class="sxs-lookup"><span data-stu-id="d2a83-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="d2a83-168">Executar a análise de dispositivos intermediários (idade, integridade, etc.)</span><span class="sxs-lookup"><span data-stu-id="d2a83-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="d2a83-169">Para obter mais informações, consulte a [ferramenta PsPing](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span><span class="sxs-lookup"><span data-stu-id="d2a83-169">For more information, see the [PsPing tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="d2a83-170">Considerações de operações de IT</span><span class="sxs-lookup"><span data-stu-id="d2a83-170">IT operations considerations</span></span>

<span data-ttu-id="d2a83-171">Aqui estão algumas coisas a considerar quando operando uma carga de trabalho de TI em um serviço do Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="d2a83-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="d2a83-172">Migrações de ocorrência únicas</span><span class="sxs-lookup"><span data-stu-id="d2a83-172">One-time migrations</span></span>

<span data-ttu-id="d2a83-173">Exemplos de migrações ocasionais são a transferência de dados em massa para aplicativos baseados em nuvem ou armazenamento de arquivamento.</span><span class="sxs-lookup"><span data-stu-id="d2a83-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="d2a83-174">Para otimizar sua rede para migrações em tempo:</span><span class="sxs-lookup"><span data-stu-id="d2a83-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="d2a83-175">Evite pico de uso de rede e tempos de aplicação de patch do computador</span><span class="sxs-lookup"><span data-stu-id="d2a83-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="d2a83-176">Deve ser a linha e testados, avaliar a integridade de rede e resolver problemas antes de tentar migração real</span><span class="sxs-lookup"><span data-stu-id="d2a83-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="d2a83-177">Execute o post-mortem para migrações futuras</span><span class="sxs-lookup"><span data-stu-id="d2a83-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="d2a83-178">Sincronizações em andamento</span><span class="sxs-lookup"><span data-stu-id="d2a83-178">Ongoing synchronizations</span></span>

<span data-ttu-id="d2a83-179">Exemplos de sincronizações em andamento são informações de diretório, configurações ou arquivos.</span><span class="sxs-lookup"><span data-stu-id="d2a83-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="d2a83-180">Para otimizar sua rede para sincronizações em andamento:</span><span class="sxs-lookup"><span data-stu-id="d2a83-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="d2a83-181">Certifique-se de que um sistema de monitoramento de largura de banda está no lugar, resolver ou descartar erros coletados</span><span class="sxs-lookup"><span data-stu-id="d2a83-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="d2a83-182">Use monitoramento resultados de largura de banda para determinar a necessidade de alterações na rede (up/dimensionamento, circuitos novos ou adicionar dispositivos)</span><span class="sxs-lookup"><span data-stu-id="d2a83-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="d2a83-183">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="d2a83-183">For more information, see:</span></span>
  
- [<span data-ttu-id="d2a83-184">Rede e planejamento de migração para o Office 365</span><span class="sxs-lookup"><span data-stu-id="d2a83-184">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="d2a83-185">Curso de gerenciamento de desempenho Microsoft Academy Virtual do Office 365</span><span class="sxs-lookup"><span data-stu-id="d2a83-185">Office 365 Performance Management Microsoft Virtual Academy course</span></span>](https://aka.ms/o365perf)
    
- [<span data-ttu-id="d2a83-186">ExpressRoute para o Office 365</span><span class="sxs-lookup"><span data-stu-id="d2a83-186">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
## <a name="see-also"></a><span data-ttu-id="d2a83-187">Veja também</span><span class="sxs-lookup"><span data-stu-id="d2a83-187">See Also</span></span>

[<span data-ttu-id="d2a83-188">Microsoft Cloud Networking para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="d2a83-188">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="d2a83-189">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="d2a83-189">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="d2a83-190">Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="d2a83-190">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



