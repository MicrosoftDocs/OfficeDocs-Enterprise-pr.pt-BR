---
title: Plano para dispositivos de rede que se conectam aos serviços do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Resumo: Descreve as considerações para a capacidade da rede, aceleradores de WAN e balanceamento de dispositivos que são usados para conectar para o Office 365.'
ms.openlocfilehash: c384ba043e64ec83eda74b234937efaf72f29815
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223063"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="d43d8-103">Plano para dispositivos de rede que se conectam aos serviços do Office 365</span><span class="sxs-lookup"><span data-stu-id="d43d8-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="d43d8-104">**Resumo**: Descreve as considerações para a capacidade da rede, aceleradores de WAN e balanceamento de dispositivos que são usados para conectar para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="d43d8-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="d43d8-p101">Alguns dispositivos de hardware de rede podem ter limitações no número de sessões simultâneas que são suportados. Para ter mais de 2.000 usuários de empresas, recomendamos que eles monitoram seus dispositivos de rede para garantir que eles sejam capazes de lidar com o tráfego de serviço adicional do Office 365. Simple Network Management Protocol (SNMP) software de monitoramento pode ajudá-lo a fazer isso.</span><span class="sxs-lookup"><span data-stu-id="d43d8-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="d43d8-108">Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="d43d8-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="d43d8-p102">Local saídas configurações de proxy de Internet também afetam a conectividade com os serviços do Office 365 para seus aplicativos de cliente. Você também deve configurar os dispositivos de proxy de rede para permitir conexões para aplicativos e URLs de serviços de nuvem do Microsoft. Cada organização é diferente. Para obter uma ideia de como o Microsoft gerencia esse processo e a largura de banda, vamos provisionar, [Leia o estudo de caso](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span><span class="sxs-lookup"><span data-stu-id="d43d8-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="d43d8-113">A seguir Skype para artigos de Ajuda do Business ter mais informações sobre Skype para configurações de negócios:</span><span class="sxs-lookup"><span data-stu-id="d43d8-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="d43d8-114">Skype de solução de problemas para erros de entrada do corporativos (administradores)</span><span class="sxs-lookup"><span data-stu-id="d43d8-114">Troubleshooting Skype for Business Sign-in Errors (Administrators)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243624)

- [<span data-ttu-id="d43d8-115">Você não pode se conectar ao Skype para negócios ou determinados recursos não funcionam porque um firewall local bloqueia a conexão</span><span class="sxs-lookup"><span data-stu-id="d43d8-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="d43d8-116">Embora muitas dessas configurações sejam Skype para negócios específicos, a orientação geral sobre configuração de rede é útil para todos os serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d43d8-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="d43d8-117">Determinando a capacidade da rede</span><span class="sxs-lookup"><span data-stu-id="d43d8-117">Determining Network Capacity</span></span>

<span data-ttu-id="d43d8-p103">Cada dispositivo de rede que existe em uma conexão tem seu limite de capacidade. Esses dispositivos incluem os adaptadores de rede do cliente e do servidor, roteadores, chaves e hubs que se interconectam. Capacidade de rede adequada significa que nenhum deles está saturado. O monitoramento da atividade da rede é essencial para ajudar a assegurar que os carregamentos reais em todos os dispositivos de rede estejam abaixo de sua capacidade máxima. A capacidade da rede afeta o desempenho do dispositivo proxy.</span><span class="sxs-lookup"><span data-stu-id="d43d8-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="d43d8-p104">Na maioria das situações, a largura de banda de conexão de Internet define o limite para a quantidade de tráfego. Desempenho fraco durante as horas de pico tráfego provavelmente é causado por uso excessivo do link da Internet. Essa situação também se aplica a um cenário de filiais, onde os computadores de servidores de proxy de escritório de filial estão conectados ao dispositivo proxy nas matrizes da ramificação em um link de rede de longa distância (WAN) lento.</span><span class="sxs-lookup"><span data-stu-id="d43d8-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="d43d8-p105">Para testar a capacidade da rede, monitore a atividade de rede na interface da rede de proxy. Se for mais de 75% da largura de banda máxima de qualquer interface de rede, considere a aumentar a largura de banda da infraestrutura de rede que for inadequada. Ou então, considere o uso de recursos avançados, como compactação HTTP.</span><span class="sxs-lookup"><span data-stu-id="d43d8-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="d43d8-129">Aceleradores de WAN</span><span class="sxs-lookup"><span data-stu-id="d43d8-129">WAN Accelerators</span></span>

<span data-ttu-id="d43d8-p106">Se sua organização usa os dispositivos de proxy de aceleração de rede (WAN) de longa distância, você poderá encontrar problemas ao acessar os serviços do Office 365. Você pode precisar otimizar seu dispositivo de rede ou dispositivos para garantir que os usuários tenham uma experiência consistente ao acessar o Office 365. Por exemplo, serviços do Office 365 criptografar algum conteúdo do Office 365 e o cabeçalho TCP. O dispositivo não estejam aptos a lidar com esse tipo de tráfego.</span><span class="sxs-lookup"><span data-stu-id="d43d8-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="d43d8-134">Leia nossa declaração de suporte sobre [usando o controlador de otimização de WAN ou dispositivos de inspeção do tráfego com o Office 365](https://support.microsoft.com/kb/2690045).</span><span class="sxs-lookup"><span data-stu-id="d43d8-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="d43d8-135">Dispositivos de balanceamento de carga de hardware e software</span><span class="sxs-lookup"><span data-stu-id="d43d8-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="d43d8-p107">Sua organização precisa usar um balanceador de carga de hardware (HLB) ou uma solução de balanceamento de carga da rede (NLB) para distribuir as solicitações para seus servidores Active Directory Federation Services (AD FS) e/ou servidores híbridos do Exchange. Os dispositivos de balanceamento de carga controlam o tráfego da rede para os servidores locais. Esses servidores são cruciais para ajudar a assegurar a disponibilidade do logon único e da implantação híbrida do Exchange.</span><span class="sxs-lookup"><span data-stu-id="d43d8-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="d43d8-p108">Fornecemos uma solução NLB baseada em software integrada ao Windows Server. Office 365 oferece suporte a essa solução para atingir o balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="d43d8-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="d43d8-141">Firewalls e proxies</span><span class="sxs-lookup"><span data-stu-id="d43d8-141">Firewalls and proxies</span></span>

<span data-ttu-id="d43d8-142">Para obter mais detalhes sobre como configurar firewalls e proxies para se conectar ao Office 365, leia os [pontos de extremidade de gerenciar o Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [conectividade de rede para o Office 365](network-connectivity.md)e [pontos de extremidade do Office 365 perguntas Frequentes](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) para saber mais sobre os dispositivos e seleção de circuito.</span><span class="sxs-lookup"><span data-stu-id="d43d8-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d43d8-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="d43d8-143">See also</span></span>

[<span data-ttu-id="d43d8-144">Supervisores de implantação para serviços do Office 365</span><span class="sxs-lookup"><span data-stu-id="d43d8-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
