---
title: Criação de rede para o Microsoft Azure IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Resumo: entenda como projetar redes otimizadas para cargas de trabalho no Microsoft Azure IaaS.'
ms.openlocfilehash: b06564c8a86c59dac4ac9a5380cd88cf9d045974
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068127"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="667c0-103">Criação de rede para o Microsoft Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="667c0-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="667c0-104">**Resumo:** Entenda como projetar a rede otimizada para cargas de trabalho no Microsoft Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="667c0-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="667c0-105">Otimizar a rede para cargas de trabalho de ti hospedadas no Azure IaaS requer uma compreensão das redes virtuais do Azure (VNets), espaços de endereço, roteamento, DNS e balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="667c0-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="667c0-106">Planejamento de etapas para qualquer VNet</span><span class="sxs-lookup"><span data-stu-id="667c0-106">Planning steps for any VNet</span></span>

<span data-ttu-id="667c0-107">Siga estas etapas para qualquer tipo de VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="667c0-108">Etapa 1: preparar sua intranet para os serviços de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="667c0-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="667c0-109">Siga as **etapas para preparar sua rede para o serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="667c0-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="667c0-110">Etapa 2: otimizar a largura de banda da Internet.</span><span class="sxs-lookup"><span data-stu-id="667c0-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="667c0-111">Otimize a largura de banda da Internet usando as etapas 2-4 das **etapas para preparar sua rede para os serviços Microsoft SaaS** no [projeto de rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="667c0-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="667c0-112">Etapa 3: determinar o tipo de VNet (somente na nuvem ou entre locais).</span><span class="sxs-lookup"><span data-stu-id="667c0-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="667c0-113">Uma VNet somente na nuvem não tem conexão com uma rede local.</span><span class="sxs-lookup"><span data-stu-id="667c0-113">A cloud-only VNet has no connection to an on-premises network.</span></span> <span data-ttu-id="667c0-114">Veja um exemplo.</span><span class="sxs-lookup"><span data-stu-id="667c0-114">Here is an example.</span></span>
  
<span data-ttu-id="667c0-115">**Figura 1: uma VNet somente na nuvem**</span><span class="sxs-lookup"><span data-stu-id="667c0-115">**Figure 1: A cloud-only VNet**</span></span>

![Figura 1: uma rede virtual somente na nuvem no Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="667c0-117">A Figura 1 mostra um conjunto de máquinas virtuais em uma VNet somente na nuvem.</span><span class="sxs-lookup"><span data-stu-id="667c0-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="667c0-118">Uma VNet entre locais tem uma conexão VPN ou ExpressRoute de site a site (S2S) para uma rede local por meio de um gateway do Azure.</span><span class="sxs-lookup"><span data-stu-id="667c0-118">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway.</span></span> <span data-ttu-id="667c0-119">Veja um exemplo.</span><span class="sxs-lookup"><span data-stu-id="667c0-119">Here is an example.</span></span>
  
<span data-ttu-id="667c0-120">**Figura 2: uma VNet entre instalações**</span><span class="sxs-lookup"><span data-stu-id="667c0-120">**Figure 2: A cross-premises VNet**</span></span>

![Figura 2: uma rede virtual entre locais no Azure](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="667c0-122">A Figura 2 mostra um conjunto de máquinas virtuais em uma VNet entre locais, que é conectada a uma rede local.</span><span class="sxs-lookup"><span data-stu-id="667c0-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="667c0-123">Consulte as [etapas adicionais de planejamento para uma seção de VNet entre locais](designing-networking-for-microsoft-azure-iaas.md#cross_prem) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="667c0-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="667c0-124">Etapa 4: determinar o espaço de endereço da VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="667c0-125">A tabela 1 mostra os espaços de endereço para os diferentes tipos de VNets.</span><span class="sxs-lookup"><span data-stu-id="667c0-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="667c0-126">**Tipo de VNet**</span><span class="sxs-lookup"><span data-stu-id="667c0-126">**Type of VNet**</span></span>|<span data-ttu-id="667c0-127">**Espaço de endereço da rede virtual**</span><span class="sxs-lookup"><span data-stu-id="667c0-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="667c0-128">Apenas Nuvem</span><span class="sxs-lookup"><span data-stu-id="667c0-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="667c0-129">Espaço de endereçamento privado arbitrário</span><span class="sxs-lookup"><span data-stu-id="667c0-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="667c0-130">Somente na nuvem interconectada</span><span class="sxs-lookup"><span data-stu-id="667c0-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="667c0-131">Privado arbitrário, mas não sobrepondo com outros VNets conectados</span><span class="sxs-lookup"><span data-stu-id="667c0-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="667c0-132">Entre locais</span><span class="sxs-lookup"><span data-stu-id="667c0-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="667c0-133">Particular, mas não se sobrepõe ao local</span><span class="sxs-lookup"><span data-stu-id="667c0-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="667c0-134">Interconexão entre locais</span><span class="sxs-lookup"><span data-stu-id="667c0-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="667c0-135">Privado, mas não sobrepondo com o local e outros VNets conectados</span><span class="sxs-lookup"><span data-stu-id="667c0-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="667c0-136">**Tabela 1: tipos de VNets e seus espaços de endereço correspondentes**</span><span class="sxs-lookup"><span data-stu-id="667c0-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="667c0-137">As máquinas virtuais recebem uma configuração de endereço do espaço de endereço da sub-rede por DHCP:</span><span class="sxs-lookup"><span data-stu-id="667c0-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="667c0-138">Máscara de sub-rede/endereço</span><span class="sxs-lookup"><span data-stu-id="667c0-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="667c0-139">Gateway padrão</span><span class="sxs-lookup"><span data-stu-id="667c0-139">Default gateway</span></span>
    
- <span data-ttu-id="667c0-140">Endereços IP do servidor DNS</span><span class="sxs-lookup"><span data-stu-id="667c0-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="667c0-141">Você também pode reservar um endereço IP estático.</span><span class="sxs-lookup"><span data-stu-id="667c0-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="667c0-142">As máquinas virtuais também podem ser atribuídas a um endereço IP público, individualmente ou a partir do serviço de nuvem contendo (apenas para máquinas de implantação clássicas).</span><span class="sxs-lookup"><span data-stu-id="667c0-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="667c0-143">Etapa 5: determinar as sub-redes dentro do VNet e os espaços de endereço atribuídos a cada um.</span><span class="sxs-lookup"><span data-stu-id="667c0-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="667c0-144">Há dois tipos de sub-redes em uma rede virtual, uma sub-rede de gateway e uma sub-rede de Hospedagem de máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="667c0-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="667c0-145">**Figura 3: os dois tipos de sub-redes no Azure**</span><span class="sxs-lookup"><span data-stu-id="667c0-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Figura 3: os dois tipos de sub-redes no Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="667c0-147">A Figura 3 mostra um VNet contendo uma sub-rede de gateway que tem um gateway do Azure e um conjunto de sub-redes de Hospedagem de máquina virtual contendo máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="667c0-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="667c0-148">A sub-rede do portal do Azure é necessária para o Azure hospedar as duas máquinas virtuais do seu gateway do Azure.</span><span class="sxs-lookup"><span data-stu-id="667c0-148">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway.</span></span> <span data-ttu-id="667c0-149">Especifique um espaço de endereçamento com pelo menos um comprimento de prefixo de 29 bits (exemplo: 192.168.15.248/29).</span><span class="sxs-lookup"><span data-stu-id="667c0-149">Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29).</span></span> <span data-ttu-id="667c0-150">Um comprimento de prefixo de 27 bits ou menor é recomendado, especialmente se você estiver planejando usar o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="667c0-150">A 27-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="667c0-151">Uma prática recomendada para determinar o espaço de endereço da sub-rede do gateway do Azure é:</span><span class="sxs-lookup"><span data-stu-id="667c0-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="667c0-152">Escolha o tamanho da sub-rede do gateway.</span><span class="sxs-lookup"><span data-stu-id="667c0-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="667c0-153">Nos bits variáveis no espaço de endereço da VNet, defina os bits usados para a sub-rede de gateway como 0 e defina os bits restantes como 1.</span><span class="sxs-lookup"><span data-stu-id="667c0-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="667c0-154">Converta como Decimal e Express como um espaço de endereço com o comprimento do prefixo definido para o tamanho da sub-rede do gateway.</span><span class="sxs-lookup"><span data-stu-id="667c0-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="667c0-155">Com esse método, o espaço de endereço para a sub-rede do gateway está sempre no final mais distante do espaço de endereço da rede virtual.</span><span class="sxs-lookup"><span data-stu-id="667c0-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="667c0-156">Veja um exemplo de como definir o prefixo de endereço da sub-rede de gateway: o espaço de endereço da VNet é 10.119.0.0/16.</span><span class="sxs-lookup"><span data-stu-id="667c0-156">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16.</span></span> <span data-ttu-id="667c0-157">Inicialmente, a organização usará uma conexão VPN site a site, mas, eventualmente, receberá o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="667c0-157">The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute.</span></span> <span data-ttu-id="667c0-158">A tabela 2 mostra as etapas e os resultados da determinação do prefixo de endereço de sub-rede de gateway na notação de prefixo de rede (também conhecido como CIDR).</span><span class="sxs-lookup"><span data-stu-id="667c0-158">Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="667c0-159">Veja a seguir as etapas e o exemplo de determinação do prefixo do endereço da sub-rede do gateway:</span><span class="sxs-lookup"><span data-stu-id="667c0-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="667c0-160">Escolha o tamanho da sub-rede do gateway.</span><span class="sxs-lookup"><span data-stu-id="667c0-160">Decide on the size of the gateway subnet.</span></span> <span data-ttu-id="667c0-161">No nosso exemplo, escolhemos/28.</span><span class="sxs-lookup"><span data-stu-id="667c0-161">For our example, we chose /28.</span></span>
2. <span data-ttu-id="667c0-162">Defina os bits na parte variável do espaço de endereço da VNet (b) como 0 para os bits de sub-rede de gateway (G), caso contrário, 1 (V).</span><span class="sxs-lookup"><span data-stu-id="667c0-162">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V).</span></span> <span data-ttu-id="667c0-163">No nosso exemplo, estamos usando o espaço de endereço 10.119.0.0/16 para a VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-163">For our example, we are using the 10.119.0.0/16 address space for the VNet.</span></span>
<br/>
<br/><span data-ttu-id="667c0-164">10,119.</span><span class="sxs-lookup"><span data-stu-id="667c0-164">10.119.</span></span> <span data-ttu-id="667c0-165">bbbbbbbb .</span><span class="sxs-lookup"><span data-stu-id="667c0-165">bbbbbbbb .</span></span> <span data-ttu-id="667c0-166">bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="667c0-166">bbbbbbbb</span></span>
<br/><span data-ttu-id="667c0-167">10,119.</span><span class="sxs-lookup"><span data-stu-id="667c0-167">10.119.</span></span> <span data-ttu-id="667c0-168">VVVVVVVV .</span><span class="sxs-lookup"><span data-stu-id="667c0-168">VVVVVVVV .</span></span> <span data-ttu-id="667c0-169">VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="667c0-169">VVVVGGGG</span></span>
<br/><span data-ttu-id="667c0-170">10,119.</span><span class="sxs-lookup"><span data-stu-id="667c0-170">10.119.</span></span> <span data-ttu-id="667c0-171">11111111.</span><span class="sxs-lookup"><span data-stu-id="667c0-171">11111111 .</span></span> <span data-ttu-id="667c0-172">11110000</span><span class="sxs-lookup"><span data-stu-id="667c0-172">11110000</span></span>
<br/><br/>
3. <span data-ttu-id="667c0-173">Converta o resultado da etapa 2 para decimal e Express como um espaço de endereço.</span><span class="sxs-lookup"><span data-stu-id="667c0-173">Convert the result from step 2 to decimal and express as an address space.</span></span> <span data-ttu-id="667c0-174">Para o nosso exemplo, 10,119.</span><span class="sxs-lookup"><span data-stu-id="667c0-174">For our example, 10.119.</span></span> <span data-ttu-id="667c0-175">11111111.</span><span class="sxs-lookup"><span data-stu-id="667c0-175">11111111 .</span></span> <span data-ttu-id="667c0-176">11110000 é 10.119.255.240 e com o comprimento do prefixo da etapa 1, (28 no nosso exemplo), o prefixo do endereço da sub-rede do gateway resultante é 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="667c0-176">11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="667c0-177">Consulte a [calculadora de espaço de endereçamento para as sub-redes de gateway do Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="667c0-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="667c0-178">As sub-redes de Hospedagem de máquina virtual são onde você coloca as máquinas virtuais do Azure, que podem ser feitas de acordo com as diretrizes locais típicas, como uma função ou camada comum de um aplicativo ou de um isolamento de sub-rede.</span><span class="sxs-lookup"><span data-stu-id="667c0-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="667c0-179">O Azure usa os primeiros 3 endereços em cada sub-rede.</span><span class="sxs-lookup"><span data-stu-id="667c0-179">Azure uses the first 3 addresses on each subnet.</span></span> <span data-ttu-id="667c0-180">Portanto, o número de endereços possíveis em uma sub-rede do Azure é 2<sup>n</sup> -5, onde n é o número de bits do host.</span><span class="sxs-lookup"><span data-stu-id="667c0-180">Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits.</span></span> <span data-ttu-id="667c0-181">A tabela 3 mostra o intervalo de máquinas virtuais necessárias, o número de bits de hosts necessários e o tamanho da sub-rede correspondente.</span><span class="sxs-lookup"><span data-stu-id="667c0-181">Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="667c0-182">**Máquinas virtuais necessárias**</span><span class="sxs-lookup"><span data-stu-id="667c0-182">**Virtual machines required**</span></span>|<span data-ttu-id="667c0-183">**Bits de host**</span><span class="sxs-lookup"><span data-stu-id="667c0-183">**Host bits**</span></span>|<span data-ttu-id="667c0-184">**Tamanho da sub-rede**</span><span class="sxs-lookup"><span data-stu-id="667c0-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="667c0-185">1 a 3</span><span class="sxs-lookup"><span data-stu-id="667c0-185">1-3</span></span>  <br/> |<span data-ttu-id="667c0-186">3D</span><span class="sxs-lookup"><span data-stu-id="667c0-186">3</span></span>  <br/> |<span data-ttu-id="667c0-187">/29</span><span class="sxs-lookup"><span data-stu-id="667c0-187">/29</span></span>  <br/> |
|<span data-ttu-id="667c0-188">4 a 11</span><span class="sxs-lookup"><span data-stu-id="667c0-188">4-11</span></span>  <br/> |<span data-ttu-id="667c0-189">quatro</span><span class="sxs-lookup"><span data-stu-id="667c0-189">4</span></span>  <br/> |<span data-ttu-id="667c0-190">/28</span><span class="sxs-lookup"><span data-stu-id="667c0-190">/28</span></span>  <br/> |
|<span data-ttu-id="667c0-191">12 a 27</span><span class="sxs-lookup"><span data-stu-id="667c0-191">12-27</span></span>  <br/> |<span data-ttu-id="667c0-192">0,5</span><span class="sxs-lookup"><span data-stu-id="667c0-192">5</span></span>  <br/> |<span data-ttu-id="667c0-193">/27</span><span class="sxs-lookup"><span data-stu-id="667c0-193">/27</span></span>  <br/> |
|<span data-ttu-id="667c0-194">28 a 59</span><span class="sxs-lookup"><span data-stu-id="667c0-194">28-59</span></span>  <br/> |<span data-ttu-id="667c0-195">6</span><span class="sxs-lookup"><span data-stu-id="667c0-195">6</span></span>  <br/> |<span data-ttu-id="667c0-196">/26</span><span class="sxs-lookup"><span data-stu-id="667c0-196">/26</span></span>  <br/> |
|<span data-ttu-id="667c0-197">60 a 123</span><span class="sxs-lookup"><span data-stu-id="667c0-197">60-123</span></span>  <br/> |<span data-ttu-id="667c0-198">178</span><span class="sxs-lookup"><span data-stu-id="667c0-198">7</span></span>  <br/> |<span data-ttu-id="667c0-199">/25</span><span class="sxs-lookup"><span data-stu-id="667c0-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="667c0-200">**Tabela 3: requisitos de máquina virtual e seus tamanhos de sub-rede**</span><span class="sxs-lookup"><span data-stu-id="667c0-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="667c0-201">Para obter mais informações sobre a quantidade máxima de máquinas virtuais em uma sub-rede ou VNet, consulte [limites de rede](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="667c0-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="667c0-202">Para obter mais informações, consulte [Plan and Design Azure virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="667c0-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="667c0-203">Etapa 6: determinar a configuração do servidor DNS e os endereços dos servidores DNS a serem atribuídos às VMs na VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="667c0-204">O Azure atribui máquinas virtuais aos endereços de servidores DNS por DHCP.</span><span class="sxs-lookup"><span data-stu-id="667c0-204">Azure assigns virtual machines the addresses of DNS servers by DHCP.</span></span> <span data-ttu-id="667c0-205">Os servidores DNS podem ser:</span><span class="sxs-lookup"><span data-stu-id="667c0-205">DNS servers can be:</span></span>
  
- <span data-ttu-id="667c0-206">Fornecido pelo Azure: fornece registro de nome local e resolução local e de nomes de Internet</span><span class="sxs-lookup"><span data-stu-id="667c0-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="667c0-207">Fornecido por você: fornece registro de nome local ou de intranet e resolução de nomes de intranet ou Internet</span><span class="sxs-lookup"><span data-stu-id="667c0-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="667c0-208">A tabela 4 mostra as diferentes configurações de servidores DNS para cada tipo de VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="667c0-209">**Tipo de VNet**</span><span class="sxs-lookup"><span data-stu-id="667c0-209">**Type of VNet**</span></span>|<span data-ttu-id="667c0-210">**Servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="667c0-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="667c0-211">Apenas Nuvem</span><span class="sxs-lookup"><span data-stu-id="667c0-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="667c0-212">Fornecido pelo Azure para resolução de nomes locais e de Internet</span><span class="sxs-lookup"><span data-stu-id="667c0-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="667c0-213">Máquina virtual do Azure para resolução de nomes locais e de Internet (encaminhamento DNS)</span><span class="sxs-lookup"><span data-stu-id="667c0-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="667c0-214">Entre locais</span><span class="sxs-lookup"><span data-stu-id="667c0-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="667c0-215">Local para resolução de nomes locais e de intranet</span><span class="sxs-lookup"><span data-stu-id="667c0-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="667c0-216">Máquina virtual do Azure para resolução de nomes locais e de intranet (replicação e encaminhamento de DNS)</span><span class="sxs-lookup"><span data-stu-id="667c0-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="667c0-217">**Tabela 4: opções de servidor DNS para os dois tipos diferentes de VNets**</span><span class="sxs-lookup"><span data-stu-id="667c0-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="667c0-218">Para obter mais informações, consulte [resolução de nomes para VMs e instâncias de função](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="667c0-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="667c0-219">Etapa 7: determinar a configuração de balanceamento de carga (voltada para a Internet ou interna).</span><span class="sxs-lookup"><span data-stu-id="667c0-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="667c0-220">Em alguns casos, você deseja distribuir o tráfego de entrada para um conjunto de servidores que têm a mesma função.</span><span class="sxs-lookup"><span data-stu-id="667c0-220">In some cases, you want to distribute incoming traffic to a set of servers that have the same role.</span></span> <span data-ttu-id="667c0-221">O Azure IaaS tem um recurso interno para fazer isso para cargas de tráfego internas e voltadas para a Internet.</span><span class="sxs-lookup"><span data-stu-id="667c0-221">Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="667c0-222">O balanceamento de carga voltado para a Internet do Azure distribui aleatoriamente o tráfego de entrada não solicitado da Internet para os membros de um conjunto de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="667c0-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="667c0-223">**Figura 4: um balanceador de carga externo no Azure**</span><span class="sxs-lookup"><span data-stu-id="667c0-223">**Figure 4: An external load balancer in Azure**</span></span>

![Figura 4: um balanceador de carga externo no Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="667c0-225">A Figura 4 mostra um balanceador de carga externo no Azure que distribui o tráfego de entrada em uma regra NAT de entrada ou ponto de extremidade para um conjunto de máquinas virtuais em um conjunto de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="667c0-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="667c0-226">O balanceamento de carga interno do Azure distribui aleatoriamente o tráfego de entrada não solicitado de outras VMs do Azure ou de computadores de intranet para os membros de um conjunto de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="667c0-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="667c0-227">**Figura 5: um balanceador de carga interno no Azure**</span><span class="sxs-lookup"><span data-stu-id="667c0-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Figura 5: um balanceador de carga interno no Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="667c0-229">A Figura 5 mostra um balanceador de carga interno no Azure que distribui o tráfego de entrada em uma regra NAT de entrada ou ponto de extremidade para um conjunto de máquinas virtuais em um conjunto de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="667c0-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="667c0-230">Para saber mais, confira balanceador de [carga do Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="667c0-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="667c0-231">Etapa 8: determinar o uso de dispositivos virtuais e rotas definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="667c0-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="667c0-232">Se você precisar encaminhar o tráfego para dispositivos virtuais em sua VNet, talvez seja necessário adicionar uma ou mais rotas definidas pelo usuário a uma sub-rede.</span><span class="sxs-lookup"><span data-stu-id="667c0-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="667c0-233">**Figura 6: dispositivos virtuais e rotas definidas pelo usuário no Azure**</span><span class="sxs-lookup"><span data-stu-id="667c0-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Figura 6: dispositivos virtuais e rotas definidas pelo usuário no Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="667c0-235">A Figura 6 mostra uma VNet entre locais e uma rota definida pelo usuário atribuída a uma sub-rede de Hospedagem de máquina virtual que aponta para um dispositivo virtual.</span><span class="sxs-lookup"><span data-stu-id="667c0-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="667c0-236">Para obter mais informações, consulte [rotas definidas pelo usuário e encaminhamento de IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="667c0-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="667c0-237">Etapa 9: determinar como os computadores da Internet se conectarão às máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="667c0-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="667c0-238">Há várias maneiras de fornecer acesso à Internet para as máquinas virtuais em uma VNet, que inclui o acesso da rede da sua organização através do servidor proxy ou de outro dispositivo de borda.</span><span class="sxs-lookup"><span data-stu-id="667c0-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="667c0-239">A tabela 5 lista os métodos para filtrar ou inspecionar tráfego de entrada não solicitado.</span><span class="sxs-lookup"><span data-stu-id="667c0-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="667c0-240">**Method**</span><span class="sxs-lookup"><span data-stu-id="667c0-240">**Method**</span></span>|<span data-ttu-id="667c0-241">**Modelo de implantação**</span><span class="sxs-lookup"><span data-stu-id="667c0-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="667c0-242">1. pontos de extremidade e ACLs configurados nos serviços de nuvem</span><span class="sxs-lookup"><span data-stu-id="667c0-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="667c0-243">Clássico</span><span class="sxs-lookup"><span data-stu-id="667c0-243">Classic</span></span>  <br/> |
|<span data-ttu-id="667c0-244">2. grupos de segurança de rede</span><span class="sxs-lookup"><span data-stu-id="667c0-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="667c0-245">Gerenciador de recursos e clássico</span><span class="sxs-lookup"><span data-stu-id="667c0-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="667c0-246">3. balanceador de carga voltado para a Internet com regras de NAT de entrada</span><span class="sxs-lookup"><span data-stu-id="667c0-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="667c0-247">Gerente de Recursos</span><span class="sxs-lookup"><span data-stu-id="667c0-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="667c0-248">4. dispositivos de segurança de rede no Azure Marketplace (não mostrado)</span><span class="sxs-lookup"><span data-stu-id="667c0-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="667c0-249">Gerenciador de recursos e clássico</span><span class="sxs-lookup"><span data-stu-id="667c0-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="667c0-250">**Tabela 5: métodos de conexão com máquinas virtuais e seus modelos de implantação do Azure correspondentes**</span><span class="sxs-lookup"><span data-stu-id="667c0-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="667c0-251">**Figura 7: conectando-se às máquinas virtuais do Azure pela Internet**</span><span class="sxs-lookup"><span data-stu-id="667c0-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Figura 7: conectando-se às máquinas virtuais do Azure pela Internet](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="667c0-253">A Figura 7 mostra um computador conectado à Internet que se conecta a uma máquina virtual em um serviço de nuvem usando um ponto de extremidade, uma máquina virtual em uma sub-rede usando um grupo de segurança de rede e uma máquina virtual em uma sub-rede usando um balanceador de carga externo e regras de NAT de entrada.</span><span class="sxs-lookup"><span data-stu-id="667c0-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="667c0-254">A segurança adicional é fornecida por:</span><span class="sxs-lookup"><span data-stu-id="667c0-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="667c0-255">Conexões SSH e de área de trabalho remota, que são autenticadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="667c0-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="667c0-256">Sessões remotas do PowerShell, que são autenticadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="667c0-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="667c0-257">Modo de transporte IPsec, que você pode usar para a criptografia de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="667c0-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="667c0-258">Proteção contra DDOS do Azure, que ajuda a evitar ataques externos e internos</span><span class="sxs-lookup"><span data-stu-id="667c0-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="667c0-259">Para obter mais informações, consulte [segurança de nuvem da Microsoft para arquitetos corporativos](https://aka.ms/cloudarchsecurity) e [segurança de rede do Azure](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="667c0-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="667c0-260">Etapa 10: para vários VNets, determine a topologia de conexão VNet para VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="667c0-261">O VNets pode ser conectado entre si usando topologias semelhantes àquelas usadas para conectar os sites de uma organização.</span><span class="sxs-lookup"><span data-stu-id="667c0-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="667c0-262">Uma configuração de correntes de Margarida conecta o VNets em uma série.</span><span class="sxs-lookup"><span data-stu-id="667c0-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="667c0-263">**Figura 8: uma configuração de correntes para VNets**</span><span class="sxs-lookup"><span data-stu-id="667c0-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Figura 8: uma configuração de correntes para redes virtuais do Azure](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="667c0-265">A Figura 8 mostra cinco VNets conectados à série usando uma configuração de correntes.</span><span class="sxs-lookup"><span data-stu-id="667c0-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="667c0-266">Uma configuração de Hub e spoke conecta vários VNets a um conjunto de VNets central, que são conectados uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="667c0-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="667c0-267">**Figura 9: uma configuração de Hub e spoke para VNets**</span><span class="sxs-lookup"><span data-stu-id="667c0-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![Figura 9: uma configuração de Hub e spoke para redes virtuais do Azure](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="667c0-269">A Figura 9 mostra seis VNets, dois VNets são hubs conectados uns aos outros e também dois outros VNets de spoke.</span><span class="sxs-lookup"><span data-stu-id="667c0-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="667c0-270">Uma configuração de malha completa conecta cada VNet entre si.</span><span class="sxs-lookup"><span data-stu-id="667c0-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="667c0-271">**Figura 10: uma configuração de malha completa para O VNets**</span><span class="sxs-lookup"><span data-stu-id="667c0-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![Figura 10: uma configuração de malha para redes virtuais do Azure](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="667c0-273">A Figura 10 mostra quatro VNets que estão conectadas entre si, usando um total de seis conexões de VNet para VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="667c0-274">Planejamento de etapas para uma VNet entre locais</span><span class="sxs-lookup"><span data-stu-id="667c0-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="667c0-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="667c0-275"></span></span>

<span data-ttu-id="667c0-276">Siga estas etapas para uma VNet entre locais.</span><span class="sxs-lookup"><span data-stu-id="667c0-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="667c0-277">Para criar um ambiente simulado de desenvolvimento/teste entre instalações, confira a [rede virtual simulada entre locais no Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="667c0-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="667c0-278">Etapa 1: determinar a conexão entre locais com a VNet (VPN S2S ou ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="667c0-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="667c0-279">A tabela 6 lista os diferentes tipos de conexões.</span><span class="sxs-lookup"><span data-stu-id="667c0-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="667c0-280">**Tipo de conexão**</span><span class="sxs-lookup"><span data-stu-id="667c0-280">**Type of connection**</span></span>|<span data-ttu-id="667c0-281">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="667c0-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="667c0-282">VPN de site a site (S2S)</span><span class="sxs-lookup"><span data-stu-id="667c0-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="667c0-283">Conecte 1-10 sites (incluindo outros VNets) a uma única VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="667c0-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="667c0-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="667c0-285">Um link privado e seguro para o Azure por meio de um provedor de Internet (IXP) ou de um provedor de serviços de rede (NSP).</span><span class="sxs-lookup"><span data-stu-id="667c0-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="667c0-286">VPN ponto a site (P2S)</span><span class="sxs-lookup"><span data-stu-id="667c0-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="667c0-287">Conecta um único computador a uma VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="667c0-288">Emparelhamento de VNet ou VPN de rede virtual (V2V)</span><span class="sxs-lookup"><span data-stu-id="667c0-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="667c0-289">Conecta uma VNet a outra VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="667c0-290">**Tabela 6: os tipos de conexões para o VNets entre locais**</span><span class="sxs-lookup"><span data-stu-id="667c0-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="667c0-291">Para obter mais informações sobre o número máximo de conexões, consulte [limites de rede](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="667c0-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="667c0-292">Para obter mais informações sobre dispositivos VPN, consulte [dispositivos VPN para conexões de rede virtual de site a site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="667c0-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="667c0-293">Para obter mais informações sobre emparelhamento de rede virtual, consulte [emparelhamento de vnet](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span><span class="sxs-lookup"><span data-stu-id="667c0-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="667c0-294">**Figura 11: as quatro maneiras de se conectar a uma VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="667c0-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![Figura 11: as três maneiras de se conectar a uma rede virtual do Azure entre locais](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="667c0-296">A Figura 11 mostra uma VNet com os quatro tipos de conexões: uma conexão do P2S de um computador, uma conexão VPN S2S de uma rede local, uma conexão ExpressRoute de uma rede local e uma conexão de VNet para VNet de outra VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="667c0-297">Você pode se conectar a VMs em uma VNet das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="667c0-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="667c0-298">Administração de VMs de VNet de sua rede local ou da Internet</span><span class="sxs-lookup"><span data-stu-id="667c0-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="667c0-299">Acesso de carga de trabalho da sua rede local</span><span class="sxs-lookup"><span data-stu-id="667c0-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="667c0-300">Extensão de sua rede por meio de VNets adicionais</span><span class="sxs-lookup"><span data-stu-id="667c0-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="667c0-301">A segurança para conexões é fornecida pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="667c0-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="667c0-302">O P2S usa o SSTP (Secure Socket Tunneling Protocol)</span><span class="sxs-lookup"><span data-stu-id="667c0-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="667c0-303">Conexões VPN S2S e VNet para VNet usam o modo de encapsulamento IPsec com AES256</span><span class="sxs-lookup"><span data-stu-id="667c0-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="667c0-304">O ExpressRoute é uma conexão WAN privada</span><span class="sxs-lookup"><span data-stu-id="667c0-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="667c0-305">Para obter mais informações, consulte [segurança de nuvem da Microsoft para arquitetos corporativos](https://aka.ms/cloudarchsecurity) e [segurança de rede do Azure](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="667c0-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="667c0-306">Etapa 2: determinar o roteador ou dispositivo VPN local.</span><span class="sxs-lookup"><span data-stu-id="667c0-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="667c0-307">Seu roteador ou dispositivo VPN local atua como:</span><span class="sxs-lookup"><span data-stu-id="667c0-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="667c0-308">Um ponto IPsec, terminando a conexão VPN S2S do gateway do Azure.</span><span class="sxs-lookup"><span data-stu-id="667c0-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="667c0-309">O par de BPG e o ponto de terminação para a conexão rota de emparelhamento privado.</span><span class="sxs-lookup"><span data-stu-id="667c0-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="667c0-310">**Figura 12: o roteador ou dispositivo VPN local**</span><span class="sxs-lookup"><span data-stu-id="667c0-310">**Figure 12: The on-premises VPN router or device**</span></span>

![Figura 12: o roteador ou dispositivo VPN local](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="667c0-312">A Figura 12 mostra uma VNet entre locais conectada a um roteador ou dispositivo VPN local.</span><span class="sxs-lookup"><span data-stu-id="667c0-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="667c0-313">Para obter mais informações, consulte [sobre o gateway VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="667c0-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="667c0-314">Etapa 3: adicionar rotas à sua intranet para tornar o espaço de endereço da VNet alcançável.</span><span class="sxs-lookup"><span data-stu-id="667c0-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="667c0-315">O roteamento para o VNets no local consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="667c0-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="667c0-316">Uma rota para o espaço de endereço da VNet que aponta para o seu dispositivo VPN.</span><span class="sxs-lookup"><span data-stu-id="667c0-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="667c0-317">Uma rota para o espaço de endereço da VNet no seu dispositivo VPN que aponta entre a conexão VPN S2S ou ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="667c0-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="667c0-318">**Figura 13: rotas locais necessárias para tornar uma VNet alcançável**</span><span class="sxs-lookup"><span data-stu-id="667c0-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Figura 13: rotas locais necessárias para tornar uma VNet do Azure alcançável](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="667c0-320">A Figura 13 mostra as informações de roteamento necessárias para os roteadores locais e o roteador ou dispositivo VPN que representa o espaço de endereço da VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="667c0-321">Etapa 4: para o ExpressRoute, planeje a nova conexão com seu provedor.</span><span class="sxs-lookup"><span data-stu-id="667c0-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="667c0-322">Você pode criar uma conexão ExpressRoute com emparelhamento privado entre sua rede local e a nuvem da Microsoft de três maneiras diferentes:</span><span class="sxs-lookup"><span data-stu-id="667c0-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="667c0-323">Localizado em um Exchange na nuvem</span><span class="sxs-lookup"><span data-stu-id="667c0-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="667c0-324">Conexões Ethernet ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="667c0-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="667c0-325">Redes IP de qualquer um (VPN)</span><span class="sxs-lookup"><span data-stu-id="667c0-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="667c0-326">**Figura 14: usando o ExpressRoute para se conectar a uma VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="667c0-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Figura 14: usando o ExpressRoute para se conectar a uma rede virtual do Azure entre locais](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="667c0-328">A Figura 14 mostra um VNet entre locais e uma conexão ExpressRoute de um roteador local para o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="667c0-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="667c0-329">Para obter mais informações, consulte [ExpressRoute for Microsoft Cloud Connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="667c0-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="667c0-330">Etapa 5: determinar o espaço de endereço de rede local para o gateway do Azure.</span><span class="sxs-lookup"><span data-stu-id="667c0-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="667c0-331">Para o roteamento para o local ou outro VNets de uma VNet, o Azure encaminha o tráfego em um gateway do Azure que corresponde ao espaço de endereço de rede local atribuído ao gateway.</span><span class="sxs-lookup"><span data-stu-id="667c0-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="667c0-332">**Figura 15: o espaço de endereço de rede local para uma VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="667c0-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Figura 15: o espaço de endereço de rede local para uma rede virtual do Azure entre locais](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="667c0-334">A Figura 15 mostra uma VNet entre locais e o espaço de endereço de rede local no gateway do Azure, que representa o espaço de endereço alcançável na rede local.</span><span class="sxs-lookup"><span data-stu-id="667c0-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="667c0-335">Você pode definir o espaço de endereço de rede local das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="667c0-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="667c0-336">Opção 1: a lista de prefixos para o espaço de endereço atualmente necessário ou em uso (as atualizações podem ser necessárias ao adicionar novas sub-redes).</span><span class="sxs-lookup"><span data-stu-id="667c0-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="667c0-337">Opção 2: seu espaço de endereço local completo (atualizações necessárias apenas quando você adiciona novo espaço de endereçamento).</span><span class="sxs-lookup"><span data-stu-id="667c0-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="667c0-338">Como o portal do Azure não permite rotas resumidas, você deve definir o espaço de endereço da rede local para a opção 2 para que ele não inclua o espaço de endereço da VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="667c0-339">**Figura 16: o orifício do espaço de endereçamento criado pelo espaço de endereço da rede virtual**</span><span class="sxs-lookup"><span data-stu-id="667c0-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Figura 16: o orifício do espaço de endereçamento criado pelo espaço de endereço da rede virtual](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="667c0-341">A Figura 16 mostra uma representação de um espaço de endereçamento, com o espaço raiz e o espaço de endereço da VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="667c0-342">Veja um exemplo de como definir os prefixos para o espaço de endereço de rede local em torno do espaço de endereçamento "buraco" criado pela VNet:</span><span class="sxs-lookup"><span data-stu-id="667c0-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="667c0-343">Uma organização usa partes do espaço de endereçamento privado (10.0.0.0/8, 172.16.0.0/12 e 192.168.0.0/16) em toda a sua rede local.</span><span class="sxs-lookup"><span data-stu-id="667c0-343">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network.</span></span> <span data-ttu-id="667c0-344">Eles escolheram a opção 2 e 10.100.100.0/24 como seu espaço de endereço de rede virtual.</span><span class="sxs-lookup"><span data-stu-id="667c0-344">They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="667c0-345">A tabela 7 mostra as etapas e prefixos resultantes que definem o espaço de endereço de rede local para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="667c0-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="667c0-346">**Etapa**</span><span class="sxs-lookup"><span data-stu-id="667c0-346">**Step**</span></span>|<span data-ttu-id="667c0-347">**Resultados**</span><span class="sxs-lookup"><span data-stu-id="667c0-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="667c0-348">1. liste os prefixos que não são o espaço raiz do espaço de endereço da VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="667c0-349">172.16.0.0/12 e 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="667c0-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="667c0-350">2. listar os prefixos não sobrepostos de octetos variáveis até mas não incluindo o último octeto usado no espaço de endereço da rede virtual.</span><span class="sxs-lookup"><span data-stu-id="667c0-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="667c0-351">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 prefixos, ignorando o 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="667c0-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="667c0-352">3. listar os prefixos não sobrepostos no último octeto usado do espaço de endereço da VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="667c0-353">10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 prefixos, ignorando 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="667c0-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="667c0-354">**Tabela 7: exemplo de espaço de rede de endereços locais**</span><span class="sxs-lookup"><span data-stu-id="667c0-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="667c0-355">Etapa 6: configurar os servidores DNS locais para replicação de DNS com servidores DNS hospedados no Azure.</span><span class="sxs-lookup"><span data-stu-id="667c0-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="667c0-356">Para garantir que os computadores locais possam resolver os nomes de servidores baseados no Azure e servidores baseados no Azure podem resolver os nomes de computadores locais, configure:</span><span class="sxs-lookup"><span data-stu-id="667c0-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="667c0-357">Os servidores DNS de sua VNet para encaminhar para servidores DNS locais</span><span class="sxs-lookup"><span data-stu-id="667c0-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="667c0-358">Replicação de DNS das zonas apropriadas entre os servidores DNS no local e na VNet</span><span class="sxs-lookup"><span data-stu-id="667c0-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="667c0-359">**Figura 17: replicação e encaminhamento de DNS para um servidor DNS em uma VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="667c0-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Figura 17: replicação e encaminhamento de DNS para um servidor DNS em uma rede virtual do Azure entre locais](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="667c0-361">A figura 17 mostra uma VNet entre locais com servidores DNS na rede local e em uma sub-rede na VNet.</span><span class="sxs-lookup"><span data-stu-id="667c0-361">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet.</span></span> <span data-ttu-id="667c0-362">A replicação e o encaminhamento de DNS foram configurados entre os dois servidores DNS.</span><span class="sxs-lookup"><span data-stu-id="667c0-362">DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="667c0-363">Etapa 7: determinar o uso de encapsulamento forçado.</span><span class="sxs-lookup"><span data-stu-id="667c0-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="667c0-364">A rota padrão do sistema para sub-redes do Azure aponta para a Internet.</span><span class="sxs-lookup"><span data-stu-id="667c0-364">The default system route for Azure subnets points to the Internet.</span></span> <span data-ttu-id="667c0-365">Para garantir que todo o tráfego de máquinas virtuais percorra a conexão entre locais, crie uma tabela de roteamento com a rota padrão que usa o gateway do Azure como seu endereço de próximo salto.</span><span class="sxs-lookup"><span data-stu-id="667c0-365">To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address.</span></span> <span data-ttu-id="667c0-366">Você associa a tabela de rotas à sub-rede.</span><span class="sxs-lookup"><span data-stu-id="667c0-366">You then associate the route table with the subnet.</span></span> <span data-ttu-id="667c0-367">Isso é conhecido como encapsulamento forçado.</span><span class="sxs-lookup"><span data-stu-id="667c0-367">This is known as forced tunneling.</span></span> <span data-ttu-id="667c0-368">Para obter mais informações, consulte [Configure FORCED Tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span><span class="sxs-lookup"><span data-stu-id="667c0-368">For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="667c0-369">**Figura 18: rotas definidas pelo usuário e encapsulamento forçado para uma VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="667c0-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Figura 18: rotas definidas pelo usuário e encapsulamento forçado para uma rede virtual do Azure entre locais](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="667c0-371">A Figura 18 mostra uma VNet entre locais com uma rota definida pelo usuário para uma sub-rede apontando para o gateway do Azure.</span><span class="sxs-lookup"><span data-stu-id="667c0-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="667c0-372">Farm do SharePoint Server 2016 no Azure</span><span class="sxs-lookup"><span data-stu-id="667c0-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="667c0-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="667c0-373"></span></span>

<span data-ttu-id="667c0-374">Um exemplo de uma carga de trabalho de ti de intranet hospedada no Azure IaaS é um farm do SharePoint Server 2016 de várias camadas altamente disponível.</span><span class="sxs-lookup"><span data-stu-id="667c0-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="667c0-375">**Figura 19: um farm do SharePoint Server 2016 de intranet altamente disponível no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="667c0-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Um farm do SharePoint Server 2016 de alta disponibilidade no Azure IaaS](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="667c0-377">A Figura 19 mostra os nove servidores de um farm do SharePoint Server 2016 implantado em uma VNet entre locais que usa balanceadores de carga internos para as camadas de front-end e de dados.</span><span class="sxs-lookup"><span data-stu-id="667c0-377">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers.</span></span> <span data-ttu-id="667c0-378">Para obter mais informações, incluindo instruções passo a passo de design e implantação, consulte [SharePoint Server 2016 no Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span><span class="sxs-lookup"><span data-stu-id="667c0-378">For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="667c0-379">Para criar um farm de servidor único do SharePoint Server 2016 em uma VNet de várias instalações simulada, confira [intranet SharePoint server 2016 in Azure dev/Test Environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span><span class="sxs-lookup"><span data-stu-id="667c0-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="667c0-380">Para obter exemplos adicionais de cargas de trabalho de ti implantadas em máquinas virtuais em uma rede virtual do Azure entre locais, consulte [cenários de nuvem híbrida para o Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span><span class="sxs-lookup"><span data-stu-id="667c0-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="667c0-381">Confira também</span><span class="sxs-lookup"><span data-stu-id="667c0-381">See also</span></span>

[<span data-ttu-id="667c0-382">Rede do Microsoft Cloud para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="667c0-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="667c0-383">Recursos de arquitetura de TI da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="667c0-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


