---
title: Suporte NAT com o Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Resumo: fornece detalhes sobre como se aproximar do número de clientes correto que você pode usar por endereço IP na sua organização, usando a Conversão de Endereços de Rede (NAT).'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539120"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="fcced-103">Suporte NAT com o Office 365</span><span class="sxs-lookup"><span data-stu-id="fcced-103">NAT support with Office 365</span></span>

 <span data-ttu-id="fcced-104">**Resumo:** fornece detalhes sobre como se aproximar do número de clientes correto que você pode usar por endereço IP na sua organização, usando a Conversão de Endereços de Rede (NAT).</span><span class="sxs-lookup"><span data-stu-id="fcced-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="fcced-105">Anteriormente, a orientação sugerido que o número máximo de clientes do Exchange que você deve usar para se conectar ao Office 365 por endereço IP era de cerca de 2.000 clientes por porta de rede.</span><span class="sxs-lookup"><span data-stu-id="fcced-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="fcced-106">Por que usar a NAT?</span><span class="sxs-lookup"><span data-stu-id="fcced-106">Why use NAT?</span></span>

<span data-ttu-id="fcced-107">Usando NAT, milhares de pessoas em uma rede corporativa podem "compartilhar" poucos endereços IP roteáveis publicamente.</span><span class="sxs-lookup"><span data-stu-id="fcced-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="fcced-p101">A maioria das redes corporativas usa o espaço de endereço IP (RFC1918) privado. O espaço de endereço privado é alocado pela IANA (Internet Assigned Numbers Authority) e destinado unicamente para as redes que não roteiam diretamente para e a partir da Internet global.</span><span class="sxs-lookup"><span data-stu-id="fcced-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="fcced-p102">Para fornecer acesso à Internet para dispositivos em um espaço de endereço IP particular, as organizações usam tecnologias de gateway, como firewalls e proxies que fornecem conversão de endereço de rede (NAT) ou serviços (PAT) de conversão de endereço de porta. Esses gateways tornar tráfego internamente dispositivos com a Internet (incluindo o Office 365) parecem ser provenientes de um ou mais endereços IP roteáveis publicamente. Cada conexão de saída de um dispositivo interno é convertido em uma porta TCP de origem diferentes no endereço IP público.</span><span class="sxs-lookup"><span data-stu-id="fcced-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="fcced-113">Por que você precisa ter tantas conexões aberta para o Office 365 ao mesmo tempo?</span><span class="sxs-lookup"><span data-stu-id="fcced-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="fcced-p103">O Outlook  pode abrir oito ou mais conexões (nas situações em que há suplementos, calendários compartilhados, caixas de correio, etc.). Como existe um máximo de 64.000 portas disponíveis em um dispositivo NAT baseado no Windows, pode haver um máximo de 8.000 usuários por trás de um endereço IP antes das portas se esgotarem. Note que se os clientes estiverem usando dispositivos baseados no SO diferente do Windows para NAT, o total de portas disponíveis dependerá de qual dispositivo NAT ou software está sendo usado. Neste caso, o número máximo de portas poderia ser inferior a 64.000. A disponibilidade das portas também é afetada por outros fatores, como o limite do Windows de 4.000 portas para uso próprio, o que reduz o número total de portas disponíveis para 60.000. Pode haver outros aplicativos, como o Internet Explorer, que podem se conectar ao mesmo tempo, requerendo portas adicionais.</span><span class="sxs-lookup"><span data-stu-id="fcced-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="fcced-119">Máximo de cálculo de dispositivos suportados em um único endereço IP público com o Office 365</span><span class="sxs-lookup"><span data-stu-id="fcced-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="fcced-p104">Para determinar o número máximo de dispositivos por trás de um único endereço IP público, você deve monitorar o tráfego de rede para determinar o consumo da porta de pico por cliente. Além disso, um fator de pico deve ser usado para o uso da porta (mínimo de 4).</span><span class="sxs-lookup"><span data-stu-id="fcced-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="fcced-122">**Use a seguinte fórmula para calcular o número de dispositivos suportados por endereço IP:**</span><span class="sxs-lookup"><span data-stu-id="fcced-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="fcced-123">Dispositivos máximos suportados em um único endereço IP público = (64.000 - portas restritas) / (consumo da porta + fator de pico de pico)</span><span class="sxs-lookup"><span data-stu-id="fcced-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="fcced-124">**Por exemplo, se o seguinte for verdadeiro:**</span><span class="sxs-lookup"><span data-stu-id="fcced-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="fcced-125">**Portas restritas:** 4.000 para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="fcced-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="fcced-126">**Consumo da porta de pico:** 6 por dispositivo</span><span class="sxs-lookup"><span data-stu-id="fcced-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="fcced-127">**Fator de pico:** 4</span><span class="sxs-lookup"><span data-stu-id="fcced-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="fcced-128">Em seguida, os dispositivos máximos suportados por trás de um único endereço IP público = (64.000 4.000) / (6 + 4) = 6.000</span><span class="sxs-lookup"><span data-stu-id="fcced-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="fcced-p105">Com a versão do pacote, incluído nas atualizações de setembro de 2011 do Microsoft Office Outlook 2007 ou de novembro de 2011 do Microsoft Outlook 2010 ou uma atualização posterior, o número de conexões do Outlook (ambas Office Outlook 2007 com o serviço de hospedagem do Office 365 Pack 2 e o Outlook 2010) para Exchange pode ser, no mínimo, 2. Você precisará fator nos sistemas operacionais diferentes, comportamentos do usuário, e assim por diante para determinar o número mínimo e máximo de portas que sua rede precisarão de no máximo.</span><span class="sxs-lookup"><span data-stu-id="fcced-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="fcced-131">Se você quiser dar suporte a dispositivos mais atrás de um único endereço IP público, siga as etapas descritas para avaliar o número máximo de dispositivos que podem ser suportados:</span><span class="sxs-lookup"><span data-stu-id="fcced-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="fcced-p106">Monitorar o tráfego de rede para determinar o consumo da porta de pico por cliente. Você deve coletar esses dados:</span><span class="sxs-lookup"><span data-stu-id="fcced-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="fcced-134">A partir de vários locais</span><span class="sxs-lookup"><span data-stu-id="fcced-134">From multiple locations</span></span>
    
- <span data-ttu-id="fcced-135">A partir de vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="fcced-135">From multiple devices</span></span>
    
- <span data-ttu-id="fcced-136">Em vários momentos</span><span class="sxs-lookup"><span data-stu-id="fcced-136">At multiple times</span></span>
    
<span data-ttu-id="fcced-137">Use a fórmula anterior para calcular os usuários máximos por endereço IP que podem ser suportados em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="fcced-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="fcced-p107">Há vários métodos para distribuindo a carga de cliente em outros endereços IP públicos. Estratégias disponíveis dependem os recursos da solução corporativa gateway. A solução mais simples é segmentar seu espaço de endereço do usuário e "atribuir" estaticamente um número de endereços IP para cada gateway. Outra alternativa que oferecem vários dispositivos de gateway é a capacidade de usar um pool de endereços IP. A vantagem do pool de endereços é que ele é muito mais dinâmico e menos suscetíveis a requerem ajustes à medida que cresce sua base de usuários.</span><span class="sxs-lookup"><span data-stu-id="fcced-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fcced-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="fcced-143">See also</span></span>

[<span data-ttu-id="fcced-144">Gerenciando pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="fcced-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="fcced-145">Pontos de extremidade perguntas Frequentes do Office 365</span><span class="sxs-lookup"><span data-stu-id="fcced-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

