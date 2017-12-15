---
title: Projetando a rede para o Microsoft Azure IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Resumo: Entenda como projetar rede otimizada para cargas de trabalho no Microsoft Azure IaaS.'
ms.openlocfilehash: e4861de51f386af6e142debdafc64f655f010880
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="23ceb-103">Projetando a rede para o Microsoft Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="23ceb-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="23ceb-104">**Resumo:** Compreenda como projetar rede otimizada para cargas de trabalho no Microsoft Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="23ceb-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="23ceb-105">Otimização de rede para cargas de trabalho do IT hospedado no Windows Azure IaaS requer uma compreensão de redes virtuais do Azure (VNets), espaços de endereçamento, roteamento, DNS e balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="23ceb-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="23ceb-106">Etapas de planejamento para qualquer VNet</span><span class="sxs-lookup"><span data-stu-id="23ceb-106">Planning steps for any VNet</span></span>

<span data-ttu-id="23ceb-107">Siga estas etapas para qualquer tipo de VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="23ceb-108">Etapa 1: Prepare sua intranet para serviços de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="23ceb-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="23ceb-109">Percorra a seção de **etapas para preparar sua rede para serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="23ceb-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="23ceb-110">Etapa 2: Otimize sua largura de banda da Internet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="23ceb-111">Otimize sua largura de banda da Internet usando as etapas 2 a 4 da seção **etapas para preparar a sua rede de serviços Microsoft SaaS** em [projetar a rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="23ceb-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="23ceb-112">Etapa 3: Determinar o tipo de VNet (somente em nuvem ou entre instalações).</span><span class="sxs-lookup"><span data-stu-id="23ceb-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="23ceb-p101">Um VNet somente em nuvem não tem nenhuma conexão a uma rede local. Aqui está um exemplo.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="23ceb-115">**Figura 1: Um somente em nuvem VNet**</span><span class="sxs-lookup"><span data-stu-id="23ceb-115">**Figure 1: A cloud-only VNet**</span></span>

![Figura 1: Uma rede virtual somente na nuvem no Azure](images/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="23ceb-117">A Figura 1 mostra um conjunto de máquinas virtuais em um VNet somente em nuvem.</span><span class="sxs-lookup"><span data-stu-id="23ceb-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="23ceb-p102">Uma locais cruzados VNet tem uma site a site (S2S) conexão VPN ou ExpressRoute a uma rede local através de um gateway Azure. Aqui está um exemplo.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="23ceb-120">**Figura 2: Uma VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="23ceb-120">**Figure 2: A cross-premises VNet**</span></span>

![Figura 2: Uma rede virtual entre locais no Azure](images/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="23ceb-122">Figura 2 mostra um conjunto de máquinas virtuais em um VNet entre locais, que é conectado a uma rede local.</span><span class="sxs-lookup"><span data-stu-id="23ceb-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="23ceb-123">Consulte o adicionais seção [etapas de planejamento para uma VNet locais cruzados](designing-networking-for-microsoft-azure-iaas.md#cross_prem) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="23ceb-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="23ceb-124">Etapa 4: Determine o espaço de endereçamento do VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="23ceb-125">A tabela 1 mostra os espaços de endereço para os diferentes tipos de VNets.</span><span class="sxs-lookup"><span data-stu-id="23ceb-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="23ceb-126">**Tipo de VNet**</span><span class="sxs-lookup"><span data-stu-id="23ceb-126">**Type of VNet**</span></span>|<span data-ttu-id="23ceb-127">**Espaço de endereço de rede virtual**</span><span class="sxs-lookup"><span data-stu-id="23ceb-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="23ceb-128">Apenas Nuvem</span><span class="sxs-lookup"><span data-stu-id="23ceb-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="23ceb-129">Espaço de endereço privado arbitrário</span><span class="sxs-lookup"><span data-stu-id="23ceb-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="23ceb-130">Interconectados somente em nuvem</span><span class="sxs-lookup"><span data-stu-id="23ceb-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="23ceb-131">Privado arbitrário, mas não sobrepostas com os outros conectados VNets</span><span class="sxs-lookup"><span data-stu-id="23ceb-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="23ceb-132">Entre locais</span><span class="sxs-lookup"><span data-stu-id="23ceb-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="23ceb-133">Privadas, mas não sobrepostas com o local</span><span class="sxs-lookup"><span data-stu-id="23ceb-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="23ceb-134">Interconexão entre locais</span><span class="sxs-lookup"><span data-stu-id="23ceb-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="23ceb-135">Privadas, mas não sobrepostas com local e outros conectados VNets</span><span class="sxs-lookup"><span data-stu-id="23ceb-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="23ceb-136">**Tabela 1: Espaço de endereçamento de tipos de VNets e seus correspondente**</span><span class="sxs-lookup"><span data-stu-id="23ceb-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="23ceb-137">Máquinas virtuais são atribuídas a uma configuração de endereço a partir do espaço de endereço da sub-rede por DHCP:</span><span class="sxs-lookup"><span data-stu-id="23ceb-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="23ceb-138">Endereço/máscara de sub-rede</span><span class="sxs-lookup"><span data-stu-id="23ceb-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="23ceb-139">Gateway padrão</span><span class="sxs-lookup"><span data-stu-id="23ceb-139">Default gateway</span></span>
    
- <span data-ttu-id="23ceb-140">Endereços IP do servidor DNS</span><span class="sxs-lookup"><span data-stu-id="23ceb-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="23ceb-141">Você também pode reservar um endereço IP estático.</span><span class="sxs-lookup"><span data-stu-id="23ceb-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="23ceb-142">Máquinas virtuais pode também ser atribuídas um endereço IP público, individualmente ou do serviço de nuvem que contêm (para máquinas de implantação clássico somente).</span><span class="sxs-lookup"><span data-stu-id="23ceb-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="23ceb-143">Etapa 5: Determine as sub-redes dentro do VNet e os espaços de endereço atribuídos a cada uma.</span><span class="sxs-lookup"><span data-stu-id="23ceb-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="23ceb-144">Existem dois tipos de sub-redes em uma VNet, uma sub-rede de gateway e uma sub-rede de hospedagem de máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="23ceb-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="23ceb-145">**Figura 3: Os dois tipos de sub-redes no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="23ceb-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Figura 3: Os dois tipos de sub-redes no Azure](images/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="23ceb-147">A Figura 3 mostra uma VNet contendo uma sub-rede de gateway que contenha um gateway Azure e um conjunto de sub-redes de hospedagem de máquinas virtuais contendo as máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="23ceb-147">Figure 3 shows a VNet containing a gateway subnet that contains an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="23ceb-p103">A sub-rede do Azure gateway é necessário pelo Windows Azure para hospedar as duas máquinas virtuais do Azure gateway de. Especificar um espaço de endereçamento com pelo menos um comprimento de prefixo 29 bits (exemplo: 192.168.15.248/29). É recomendável um comprimento de prefixo 28 bits ou menor, especialmente se você estiver planejando usar ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="23ceb-151">Uma prática recomendada para determinar o espaço de endereço da sub-rede Azure gateway é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="23ceb-151">A best practice for determining the address space of the Azure gateway subnet is the following:</span></span>
  
1. <span data-ttu-id="23ceb-152">Decida sobre o tamanho da sub-rede gateway.</span><span class="sxs-lookup"><span data-stu-id="23ceb-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="23ceb-153">Nos bits variáveis no espaço de endereço do VNet, defina os bits usados para a sub-rede do gateway como 0 e defina os bits restantes como 1.</span><span class="sxs-lookup"><span data-stu-id="23ceb-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="23ceb-154">Converter em decimal e express como um espaço de endereçamento com o comprimento de prefixo definido como o tamanho da sub-rede gateway.</span><span class="sxs-lookup"><span data-stu-id="23ceb-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="23ceb-155">Com este método, o espaço de endereço para a sub-rede do gateway é sempre o final mais distante do espaço de endereço VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="23ceb-p104">Aqui está um exemplo de como definir o prefixo de endereço para a sub-rede do gateway: espaço de endereço do VNet é 10.119.0.0/16. A organização usará inicialmente uma conexão VPN de site a site, mas receberá eventualmente ExpressRoute. Tabela 2 mostra as etapas e os resultados de determinar o prefixo de endereço de sub-rede de gateway em notação de prefixo de rede (também conhecido como CIDR).</span><span class="sxs-lookup"><span data-stu-id="23ceb-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="23ceb-159">Aqui estão as etapas e exemplo de determinar o prefixo de endereço de sub-rede de gateway:</span><span class="sxs-lookup"><span data-stu-id="23ceb-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="23ceb-p105">Decida sobre o tamanho da sub-rede gateway. Para nosso exemplo, podemos escolheu /28.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="23ceb-p106">Defina os bits na variável parte do espaço de endereço VNet (b) como 0 para o gateway de bits de sub-rede (G), caso contrário 1 (V). Para nosso exemplo, estamos usando o espaço de endereçamento 10.119.0.0/16 para o VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="23ceb-p107">10.119. bbbbbbbb. bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="23ceb-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="23ceb-p108">10.119. VVVVVVVV. VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="23ceb-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="23ceb-p109">10.119. 11111111. 11110000</span><span class="sxs-lookup"><span data-stu-id="23ceb-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="23ceb-p110">Converta o resultado da etapa 2 para decimal e expressa como um espaço de endereçamento. Para nosso exemplo, 10.119. 11111111. 11110000 é 10.119.255.240 e com o comprimento de prefixo da etapa 1, (28 em nosso exemplo), o prefixo de endereço de sub-rede de gateway resultante é 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="23ceb-177">Para obter mais informações, consulte o [Calculadora de espaço de endereço para sub-redes de gateway do Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="23ceb-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="23ceb-178">Hospedagem de máquinas virtuais sub-redes são onde você colocar máquinas virtuais do Azure, que pode ser feito de acordo com as diretrizes de local típico, uma função comuns ou a camada de um aplicativo ou para o isolamento de sub-rede.</span><span class="sxs-lookup"><span data-stu-id="23ceb-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="23ceb-p111">Azure usa os 3 primeiros endereços em cada sub-rede. Portanto, o número de endereços possíveis em uma sub-rede Azure é 2<sup>n</sup> -5, onde n é o número de bits de host. Mostra a tabela 3 hospeda o intervalo de máquinas virtuais necessárias, o número de bits necessários e o tamanho de sub-rede correspondente.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="23ceb-182">**Máquinas virtuais necessárias**</span><span class="sxs-lookup"><span data-stu-id="23ceb-182">**Virtual machines required**</span></span>|<span data-ttu-id="23ceb-183">**Bits de host**</span><span class="sxs-lookup"><span data-stu-id="23ceb-183">**Host bits**</span></span>|<span data-ttu-id="23ceb-184">**Tamanho de sub-rede**</span><span class="sxs-lookup"><span data-stu-id="23ceb-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="23ceb-185">1 a 3</span><span class="sxs-lookup"><span data-stu-id="23ceb-185">1-3</span></span>  <br/> |<span data-ttu-id="23ceb-186">3</span><span class="sxs-lookup"><span data-stu-id="23ceb-186">3</span></span>  <br/> |<span data-ttu-id="23ceb-187">/29</span><span class="sxs-lookup"><span data-stu-id="23ceb-187">/29</span></span>  <br/> |
|<span data-ttu-id="23ceb-188">4 a 11</span><span class="sxs-lookup"><span data-stu-id="23ceb-188">4-11</span></span>  <br/> |<span data-ttu-id="23ceb-189">4</span><span class="sxs-lookup"><span data-stu-id="23ceb-189">4</span></span>  <br/> |<span data-ttu-id="23ceb-190">/28</span><span class="sxs-lookup"><span data-stu-id="23ceb-190">/28</span></span>  <br/> |
|<span data-ttu-id="23ceb-191">12 a 27</span><span class="sxs-lookup"><span data-stu-id="23ceb-191">12-27</span></span>  <br/> |<span data-ttu-id="23ceb-192">5</span><span class="sxs-lookup"><span data-stu-id="23ceb-192">5</span></span>  <br/> |<span data-ttu-id="23ceb-193">/27</span><span class="sxs-lookup"><span data-stu-id="23ceb-193">/27</span></span>  <br/> |
|<span data-ttu-id="23ceb-194">28 a 59</span><span class="sxs-lookup"><span data-stu-id="23ceb-194">28-59</span></span>  <br/> |<span data-ttu-id="23ceb-195">6</span><span class="sxs-lookup"><span data-stu-id="23ceb-195">6</span></span>  <br/> |<span data-ttu-id="23ceb-196">/26</span><span class="sxs-lookup"><span data-stu-id="23ceb-196">/26</span></span>  <br/> |
|<span data-ttu-id="23ceb-197">60 a 123</span><span class="sxs-lookup"><span data-stu-id="23ceb-197">60-123</span></span>  <br/> |<span data-ttu-id="23ceb-198">7</span><span class="sxs-lookup"><span data-stu-id="23ceb-198">7</span></span>  <br/> |<span data-ttu-id="23ceb-199">/25</span><span class="sxs-lookup"><span data-stu-id="23ceb-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="23ceb-200">**Tabela 3: requisitos de máquina Virtual e seus tamanhos de sub-rede**</span><span class="sxs-lookup"><span data-stu-id="23ceb-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="23ceb-201">Para obter mais informações sobre a quantidade máxima de máquinas virtuais em uma sub-rede ou VNet, consulte [Limites do serviço de rede](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="23ceb-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="23ceb-202">Para obter mais informações, consulte [Plan and design redes virtuais do Azure](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="23ceb-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="23ceb-203">Etapa 6: Determine a configuração do servidor DNS e os endereços dos servidores DNS para atribuir a VMs no VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="23ceb-p112">Azure atribui os endereços dos servidores DNS por DHCP de máquinas virtuais. Os servidores DNS podem ser:</span><span class="sxs-lookup"><span data-stu-id="23ceb-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="23ceb-206">Fornecidos pelo Windows Azure: fornece o registro de nome local e o local e a resolução de nomes de Internet</span><span class="sxs-lookup"><span data-stu-id="23ceb-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="23ceb-207">Fornecido por você: fornece o registro de nome local ou intranet e intranet ou resolução de nomes de Internet</span><span class="sxs-lookup"><span data-stu-id="23ceb-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="23ceb-208">A tabela 4 mostra as diferentes configurações de servidores DNS para cada tipo de VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="23ceb-209">**Tipo de VNet**</span><span class="sxs-lookup"><span data-stu-id="23ceb-209">**Type of VNet**</span></span>|<span data-ttu-id="23ceb-210">**Servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="23ceb-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="23ceb-211">Apenas Nuvem</span><span class="sxs-lookup"><span data-stu-id="23ceb-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="23ceb-212">Fornecidos pelo Windows Azure para o local e a resolução de nomes de Internet</span><span class="sxs-lookup"><span data-stu-id="23ceb-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="23ceb-213">Máquina virtual do Azure para o local e a resolução de nomes de Internet (encaminhamento de DNS)</span><span class="sxs-lookup"><span data-stu-id="23ceb-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="23ceb-214">Entre locais</span><span class="sxs-lookup"><span data-stu-id="23ceb-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="23ceb-215">No local para resolução de nomes de local e intranet</span><span class="sxs-lookup"><span data-stu-id="23ceb-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="23ceb-216">Máquina virtual do Azure para resolução de nomes de local e intranet (replicação DNS e encaminhamento)</span><span class="sxs-lookup"><span data-stu-id="23ceb-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="23ceb-217">**Tabela 4: Opções de servidor DNS para os dois tipos diferentes de VNets**</span><span class="sxs-lookup"><span data-stu-id="23ceb-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="23ceb-218">Para obter mais informações, consulte [Resolução de nomes de máquinas virtuais e instâncias de função](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="23ceb-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="23ceb-219">Etapa 7: Determinar a configuração de balanceamento de carga (voltados para a Internet ou interno).</span><span class="sxs-lookup"><span data-stu-id="23ceb-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="23ceb-p113">Em alguns casos, você deseja distribuir o tráfego de entrada para um conjunto de servidores que possuem a mesma função. Azure IaaS tem um recurso interno para fazer isso para voltados para a Internet e cargas de tráfego interno.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="23ceb-222">Azure voltado à Internet balanceamento aleatoriamente distribui o tráfego de entrada não solicitado da Internet para os membros de um conjunto com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="23ceb-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="23ceb-223">**Figura 4: Um balanceador de carga externo no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="23ceb-223">**Figure 4: An external load balancer in Azure**</span></span>

![Figure 4: Um balanceador de carga externo no Azure](images/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="23ceb-225">Figura 4 mostra um balanceador de carga externo no Azure que distribui o tráfego de entrada em uma regra de entrada NAT ou ponto de extremidade para um conjunto de máquinas virtuais em um conjunto com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="23ceb-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="23ceb-226">Aleatoriamente de balanceamento de carga de interna Azure distribui o tráfego de entrada não solicitado a partir de outras VMs Azure ou computadores da intranet para os membros de um conjunto com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="23ceb-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="23ceb-227">**Figura 5: Um balanceador de carga interno no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="23ceb-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Figura 5: Um balanceador de carga interno no Azure](images/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="23ceb-229">Figura 5 mostra um balanceador de carga interno no Azure que distribui o tráfego de entrada em uma regra de entrada NAT ou ponto de extremidade para um conjunto de máquinas virtuais em um conjunto com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="23ceb-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="23ceb-230">Para obter mais informações, consulte o [Balanceador de carga do Windows Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="23ceb-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="23ceb-231">Etapa 8: Determine o uso de dispositivos virtuais e rotas definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="23ceb-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="23ceb-232">Se você precisar encaminhar o tráfego de aparelhos virtuais na sua VNet, você pode precisar adicionar uma ou mais rotas definidas pelo usuário a uma sub-rede.</span><span class="sxs-lookup"><span data-stu-id="23ceb-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="23ceb-233">**Figura 6: Dispositivos virtuais e rotas definidas pelo usuário no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="23ceb-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Figura 6: Dispositivos virtuais e rotas definidas pelo usuário no Azure](images/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="23ceb-235">Figura 6 mostra uma VNet entre locais e uma rota definida pelo usuário atribuído a uma sub-rede de hospedagem de máquina virtual que aponta para um dispositivo virtual.</span><span class="sxs-lookup"><span data-stu-id="23ceb-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="23ceb-236">Para obter mais informações, consulte [as rotas definidas pelo usuário e o encaminhamento de IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="23ceb-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="23ceb-237">Etapa 9: Determine como computadores da Internet se conectará para máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="23ceb-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="23ceb-238">Há várias maneiras de fornecer acesso à Internet para as máquinas virtuais em um VNet, que inclui o acesso a partir da rede da organização por meio de seu servidor proxy ou outro dispositivo de borda.</span><span class="sxs-lookup"><span data-stu-id="23ceb-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="23ceb-239">Tabela 5 lista os métodos de filtragem ou inspecionando o tráfego de entrada não solicitado.</span><span class="sxs-lookup"><span data-stu-id="23ceb-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="23ceb-240">**Método**</span><span class="sxs-lookup"><span data-stu-id="23ceb-240">**Method**</span></span>|<span data-ttu-id="23ceb-241">**Modelo de implantação**</span><span class="sxs-lookup"><span data-stu-id="23ceb-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="23ceb-242">1. ACLs configuradas em serviços em nuvem e pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="23ceb-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="23ceb-243">Clássico</span><span class="sxs-lookup"><span data-stu-id="23ceb-243">Classic</span></span>  <br/> |
|<span data-ttu-id="23ceb-244">2. grupos de segurança de rede de</span><span class="sxs-lookup"><span data-stu-id="23ceb-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="23ceb-245">Gerenciador de recursos e clássico</span><span class="sxs-lookup"><span data-stu-id="23ceb-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="23ceb-246">3. balanceador de carga de voltado à Internet com as regras de entrada NAT</span><span class="sxs-lookup"><span data-stu-id="23ceb-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="23ceb-247">Gerente de Recursos</span><span class="sxs-lookup"><span data-stu-id="23ceb-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="23ceb-248">4. rede security appliances o Azure</span><span class="sxs-lookup"><span data-stu-id="23ceb-248">4. Network security appliances in the Azure</span></span> 
 <span data-ttu-id="23ceb-249">Marketplace (não mostrada)</span><span class="sxs-lookup"><span data-stu-id="23ceb-249">Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="23ceb-250">Gerenciador de recursos e clássico</span><span class="sxs-lookup"><span data-stu-id="23ceb-250">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="23ceb-251">**Tabela 5: Métodos para máquinas virtuais e seus modelos de implantação Azure correspondentes conectar**</span><span class="sxs-lookup"><span data-stu-id="23ceb-251">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="23ceb-252">**Figura 7: Conectar-se a máquinas virtuais do Azure pela Internet**</span><span class="sxs-lookup"><span data-stu-id="23ceb-252">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Figura 7: Conexão com as máquinas virtuais do Azure pela Internet](images/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="23ceb-254">Figura 7 mostra um computador conectado à Internet, conectando-se a uma máquina virtual em um serviço de nuvem usando um ponto de extremidade, uma máquina virtual em uma sub-rede usando um grupo de segurança de rede e uma máquina virtual em uma sub-rede usando um balanceador de carga externo e as regras de entrada NAT.</span><span class="sxs-lookup"><span data-stu-id="23ceb-254">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="23ceb-255">Segurança adicional é fornecida por:</span><span class="sxs-lookup"><span data-stu-id="23ceb-255">Additional security is provided by:</span></span>
  
- <span data-ttu-id="23ceb-256">Conexões da área de trabalho remota e SSH, que são autenticadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="23ceb-256">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="23ceb-257">PowerShell sessões remotas, que são autenticadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="23ceb-257">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="23ceb-258">Modo de transporte IPsec, que pode ser usada para a criptografia de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="23ceb-258">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="23ceb-259">Proteção de DDOS Azure, que ajuda a impedir ataques de internas e externas</span><span class="sxs-lookup"><span data-stu-id="23ceb-259">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="23ceb-260">Para obter mais informações, consulte [Microsoft Security de nuvem para arquitetos da empresa](https://aka.ms/cloudarchsecurity) e [Segurança de rede do Windows Azure](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="23ceb-260">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="23ceb-261">Etapa 10: Para vários VNets, determine a topologia de conexão VNet para VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-261">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="23ceb-262">VNets pode ser conectado uns aos outros usando topologias similares às utilizada para conectar os sites de uma organização.</span><span class="sxs-lookup"><span data-stu-id="23ceb-262">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="23ceb-263">Uma configuração de corrente margarida conecta-se a VNets em uma série.</span><span class="sxs-lookup"><span data-stu-id="23ceb-263">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="23ceb-264">**Figura 8: Uma conectados configuração para VNets**</span><span class="sxs-lookup"><span data-stu-id="23ceb-264">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Figura 8: Uma configuração encadeada para redes virtuais do Azure](images/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="23ceb-266">Figura 8 mostra cinco VNets conectados na série usando uma configuração conectados.</span><span class="sxs-lookup"><span data-stu-id="23ceb-266">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="23ceb-267">Uma configuração de hub e spoke conecta vários VNets para um conjunto de VNets central, que são sozinhos conectados entre si.</span><span class="sxs-lookup"><span data-stu-id="23ceb-267">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="23ceb-268">**Figura 9: Uma configuração hub e spoke para VNets**</span><span class="sxs-lookup"><span data-stu-id="23ceb-268">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![Figura 9: Uma configuração do tipo spoke and hub para redes virtuais do Azure](images/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="23ceb-270">Figura 9 mostra seis VNets, que dois VNets são hubs que estão conectados a umas às outras e também dois outro spoke VNets.</span><span class="sxs-lookup"><span data-stu-id="23ceb-270">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="23ceb-271">Uma configuração de malha completa se conecta a cada VNet uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="23ceb-271">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="23ceb-272">**Figura 10: Configuração para VNets de malha completa**</span><span class="sxs-lookup"><span data-stu-id="23ceb-272">**Figure 10: A full mesh configuration for VNets**</span></span>

![Figura 10: Uma configuração em malha para redes virtuais do Azure](images/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="23ceb-274">Figura 10 mostra quatro VNets que estão conectados entre si, usando um total de conexões de seis VNet para VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-274">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="23ceb-275">Etapas de planejamento para uma VNet entre locais</span><span class="sxs-lookup"><span data-stu-id="23ceb-275">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="23ceb-276"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="23ceb-276"></span></span>

<span data-ttu-id="23ceb-277">Siga estas etapas para uma VNet entre locais.</span><span class="sxs-lookup"><span data-stu-id="23ceb-277">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="23ceb-278">Para criar um ambiente de desenvolvimento e teste simulado entre locais, consulte [simuladas locais cruzados rede virtual no Windows Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="23ceb-278">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="23ceb-279">Etapa 1: Determine a conexão entre locais para o VNet (S2S VPN ou ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="23ceb-279">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="23ceb-280">Tabela 6 lista os diferentes tipos de conexões.</span><span class="sxs-lookup"><span data-stu-id="23ceb-280">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="23ceb-281">**Tipo de conexão**</span><span class="sxs-lookup"><span data-stu-id="23ceb-281">**Type of connection**</span></span>|<span data-ttu-id="23ceb-282">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="23ceb-282">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="23ceb-283">VPN to-Site (S2S)</span><span class="sxs-lookup"><span data-stu-id="23ceb-283">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="23ceb-284">Conecte sites de 1 a 10 (incluindo outros VNets) para um único VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-284">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="23ceb-285">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="23ceb-285">ExpressRoute</span></span>  <br/> |<span data-ttu-id="23ceb-286">Um link particular e seguro no Azure por meio de um provedor de Exchange da Internet (IXP) ou um provedor de serviço de rede (NSP).</span><span class="sxs-lookup"><span data-stu-id="23ceb-286">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="23ceb-287">VPN ponto-a-Site (P2S)</span><span class="sxs-lookup"><span data-stu-id="23ceb-287">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="23ceb-288">Conecta-se um único computador para um VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-288">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="23ceb-289">Correspondência de VNet ou VNet para VNet (V2V) VPN</span><span class="sxs-lookup"><span data-stu-id="23ceb-289">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="23ceb-290">Conecta-se um VNet para outra VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-290">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="23ceb-291">**Tabela 6: Os tipos de conexões para locais cruzados VNets**</span><span class="sxs-lookup"><span data-stu-id="23ceb-291">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="23ceb-292">Para obter mais informações sobre o número máximo de conexões, consulte [Limites do serviço de rede](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="23ceb-292">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="23ceb-293">Para obter mais informações sobre dispositivos VPN, consulte [dispositivos VPN para conexões de rede virtual do site a site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="23ceb-293">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="23ceb-294">Para obter mais informações sobre VNet correspondência, consulte [VNet correspondência](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span><span class="sxs-lookup"><span data-stu-id="23ceb-294">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="23ceb-295">**Figura 11: As quatro maneiras para se conectar a um VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="23ceb-295">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![Figura 11: As três maneiras de se conectar a uma rede virtual do Azure entre locais](images/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="23ceb-297">A Figura 11 mostra um VNet com os quatro tipos de conexões: uma conexão P2S de um computador, uma conexão VPN S2S de uma rede local, uma conexão ExpressRoute de uma rede local e uma conexão de VNet para VNet a partir de outra VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-297">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="23ceb-298">Você pode conectar VMs em um VNet das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="23ceb-298">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="23ceb-299">Administração de VMs VNet da sua rede local ou da Internet</span><span class="sxs-lookup"><span data-stu-id="23ceb-299">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="23ceb-300">Acesso de carga de trabalho do IT da sua rede local</span><span class="sxs-lookup"><span data-stu-id="23ceb-300">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="23ceb-301">Extensão da sua rede por meio de VNets adicionais</span><span class="sxs-lookup"><span data-stu-id="23ceb-301">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="23ceb-302">Segurança para conexões é fornecida pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="23ceb-302">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="23ceb-303">P2S usa o Secure Socket encapsulamento SSTP (Protocol)</span><span class="sxs-lookup"><span data-stu-id="23ceb-303">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="23ceb-304">Conexões S2S e VNet para VNet VPN usam o modo de túnel IPsec AES256</span><span class="sxs-lookup"><span data-stu-id="23ceb-304">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="23ceb-305">ExpressRoute é uma conexão WAN privada</span><span class="sxs-lookup"><span data-stu-id="23ceb-305">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="23ceb-306">Para obter mais informações, consulte [Microsoft Security de nuvem para arquitetos da empresa](https://aka.ms/cloudarchsecurity) e [Segurança de rede do Windows Azure](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="23ceb-306">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="23ceb-307">Etapa 2: Determine o dispositivo VPN no local ou roteador.</span><span class="sxs-lookup"><span data-stu-id="23ceb-307">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="23ceb-308">Seu dispositivo VPN no local ou roteador atua como:</span><span class="sxs-lookup"><span data-stu-id="23ceb-308">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="23ceb-309">Um ponto IPsec, abortar a conexão VPN S2S do Azure gateway.</span><span class="sxs-lookup"><span data-stu-id="23ceb-309">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="23ceb-310">O ponto BPG e rescisão apontam para a conexão privada de ExpressRoute de correspondência.</span><span class="sxs-lookup"><span data-stu-id="23ceb-310">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="23ceb-311">**Figura 12: O roteador VPN local ou dispositivo**</span><span class="sxs-lookup"><span data-stu-id="23ceb-311">**Figure 12: The on-premises VPN router or device**</span></span>

![Figura 12: O roteador ou dispositivo VPN local](images/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="23ceb-313">Figura 12 mostra que um VNet locais cruzados conectado a um roteador VPN local ou dispositivo.</span><span class="sxs-lookup"><span data-stu-id="23ceb-313">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="23ceb-314">Para obter mais informações, consulte [gateway sobre VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="23ceb-314">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="23ceb-315">Etapa 3: Adicione rotas à sua intranet para tornar o espaço de endereço do VNet pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="23ceb-315">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="23ceb-316">O roteamento para VNets no local consiste das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="23ceb-316">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="23ceb-317">Uma rota para o espaço de endereçamento de VNet direcionará seu dispositivo VPN.</span><span class="sxs-lookup"><span data-stu-id="23ceb-317">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="23ceb-318">Uma rota para o espaço de endereçamento VNet no seu dispositivo VPN que aponta entre a conexão VPN S2S ou ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="23ceb-318">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="23ceb-319">**Figura 13: As rotas de local necessário para fazer um VNet pode ser acessado**</span><span class="sxs-lookup"><span data-stu-id="23ceb-319">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Figura 13: As rotas locais necessárias para tornar um Azure VNet acessível](images/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="23ceb-321">Figura 13 mostra as informações de roteamento exigidas pelos roteadores no local e o roteador VPN ou dispositivo que representa o espaço de endereço do VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-321">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="23ceb-322">Etapa 4: Para ExpressRoute, planeje a nova conexão com seu provedor.</span><span class="sxs-lookup"><span data-stu-id="23ceb-322">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="23ceb-323">Você pode criar uma conexão ExpressRoute com correspondência privada entre sua rede local e a nuvem da Microsoft de três maneiras diferentes:</span><span class="sxs-lookup"><span data-stu-id="23ceb-323">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="23ceb-324">Co localizado em uma troca de nuvem</span><span class="sxs-lookup"><span data-stu-id="23ceb-324">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="23ceb-325">Conexões Ethernet de ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="23ceb-325">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="23ceb-326">Para qualquer redes de (VPN IP)</span><span class="sxs-lookup"><span data-stu-id="23ceb-326">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="23ceb-327">**Figura 14: Usando ExpressRoute para se conectar a um VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="23ceb-327">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Figura 14: Usando ExpressRoute para se conectar a uma rede virtual do Azure entre locais](images/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="23ceb-329">Figura 14 mostra uma VNet entre locais e uma conexão de ExpressRoute de um roteador no local para o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="23ceb-329">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="23ceb-330">Para obter mais informações, consulte [ExpressRoute para conectividade de nuvem da Microsoft](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="23ceb-330">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="23ceb-331">Etapa 5: Determine o espaço de endereço de rede Local para o gateway do Azure.</span><span class="sxs-lookup"><span data-stu-id="23ceb-331">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="23ceb-332">Para o roteamento para outros VNets ou local de um VNet, o Azure encaminha o tráfego entre um gateway Azure que coincida com o espaço de endereço de rede Local atribuído ao gateway.</span><span class="sxs-lookup"><span data-stu-id="23ceb-332">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="23ceb-333">**Figura 15: O espaço de endereço de rede Local para uma VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="23ceb-333">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Figura 15: O espaço de endereço de rede local para uma rede virtual Azure rede virtual](images/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="23ceb-335">Figura 15 mostra uma VNet entre locais e o espaço de endereço de rede Local no gateway do Azure, que representa o espaço de endereçamento pode ser acessado na rede local.</span><span class="sxs-lookup"><span data-stu-id="23ceb-335">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="23ceb-336">Você pode definir o espaço de endereço de rede Local das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="23ceb-336">You can define the Local Network address space in the following ways:</span></span>
  
- <span data-ttu-id="23ceb-337">Opção 1: Lista de prefixos para o espaço de endereçamento necessitado no momento ou em uso (atualizações podem ser necessários quando você adiciona novas sub-redes).</span><span class="sxs-lookup"><span data-stu-id="23ceb-337">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="23ceb-338">Opção 2: O seu local em toda a (necessários apenas quando você adiciona o novo espaço de endereçamento de atualizações) de espaço de endereçamento.</span><span class="sxs-lookup"><span data-stu-id="23ceb-338">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="23ceb-339">Porque o Azure gateway não permite rotas resumidas, você deve definir o espaço de endereço de rede Local para a opção 2 para que ele não inclui o espaço de endereçamento VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-339">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="23ceb-340">**Figura 16: O endereço espaço orifício criado pelo espaço de endereçamento VNet**</span><span class="sxs-lookup"><span data-stu-id="23ceb-340">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Figura 16: A abertura de espaço de endereço criada pelo espaço de endereço de rede virtual](images/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="23ceb-342">Figura 16 mostra uma representação de um espaço de endereçamento, com o espaço de raiz e o espaço de endereçamento VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-342">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="23ceb-343">Aqui está um exemplo de como definir os prefixos para o espaço de endereço de rede Local ao redor do espaço de endereço "brecha" criado pelo VNet:</span><span class="sxs-lookup"><span data-stu-id="23ceb-343">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="23ceb-p114">Uma organização utiliza partes do espaço de endereço privado (10.0.0.0/8, 172.16.0.0/12 e 192.168.0.0/16) toda a sua rede local. Que escolheram a opção 2 e 10.100.100.0/24 como seu espaço de endereço VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="23ceb-346">A tabela 7 mostra as etapas e os prefixos resultantes que definem o espaço de endereço de rede Local para que esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="23ceb-346">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="23ceb-347">**Etapa**</span><span class="sxs-lookup"><span data-stu-id="23ceb-347">**Step**</span></span>|<span data-ttu-id="23ceb-348">**Resultados**</span><span class="sxs-lookup"><span data-stu-id="23ceb-348">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="23ceb-349">1. listam os prefixos que não sejam o espaço de raiz para o espaço de endereçamento VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-349">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="23ceb-350">172.16.0.0/12 e 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="23ceb-350">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="23ceb-351">2. listar os prefixos não sobrepostos para octetos variáveis até, mas não incluindo o último usado</span><span class="sxs-lookup"><span data-stu-id="23ceb-351">2. List the non-overlapping prefixes for variable octets up to but not including the last used</span></span> 
 <span data-ttu-id="23ceb-352">octeto no espaço de endereçamento VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-352">octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="23ceb-353">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 prefixos, ignorando 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="23ceb-353">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="23ceb-354">3. lista o não sobrepostos prefixos dentro do</span><span class="sxs-lookup"><span data-stu-id="23ceb-354">3. List the non-overlapping prefixes within the</span></span> 
 <span data-ttu-id="23ceb-355">usado pela última octeto do espaço de endereço VNet.</span><span class="sxs-lookup"><span data-stu-id="23ceb-355">last used octet of the VNet address space.</span></span>  <br/> <span data-ttu-id="23ceb-356">| 10.100.0.0/24, 10.100.1.0/24 … 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 prefixos, ignorando 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="23ceb-356">|10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="23ceb-357">**Tabela 7: Espaço de endereço do Local de exemplo de rede**</span><span class="sxs-lookup"><span data-stu-id="23ceb-357">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="23ceb-358">Etapa 6: Configure os servidores DNS locais para replicação de DNS com servidores DNS hospedados no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="23ceb-358">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="23ceb-359">Para garantir que os computadores no local podem resolver os nomes dos servidores baseados no Windows Azure e servidores baseados no Windows Azure podem resolver os nomes dos computadores no local, configure:</span><span class="sxs-lookup"><span data-stu-id="23ceb-359">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="23ceb-360">Os servidores DNS na sua VNet para encaminhar para os servidores DNS locais</span><span class="sxs-lookup"><span data-stu-id="23ceb-360">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="23ceb-361">Replicação de DNS das zonas adequadas entre servidores DNS no local e o VNet</span><span class="sxs-lookup"><span data-stu-id="23ceb-361">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="23ceb-362">**Figura 17: Replicação de DNS e o encaminhamento para um servidor DNS em uma VNet locais cruzados**</span><span class="sxs-lookup"><span data-stu-id="23ceb-362">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Figura 17: A replicação de DNS e o encaminhamento para um servidor DNS em uma rede virtual do Azure entre locais](images/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="23ceb-p115">Figura 17 mostra uma VNet entre locais com os servidores DNS na rede local e em uma sub-rede em que o VNet. Encaminhamento e replicação de DNS foi configurado entre os dois servidores DNS.</span><span class="sxs-lookup"><span data-stu-id="23ceb-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="23ceb-366">Etapa 7: Determine o uso de encapsulamento forçado.</span><span class="sxs-lookup"><span data-stu-id="23ceb-366">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="23ceb-p116">A rota de sistema padrão para sub-redes Azure aponta para a Internet. Para garantir que todo o tráfego de máquinas virtuais percorrem a conexão entre locais, crie uma tabela de roteamento com a rota padrão que usa o gateway Azure como seu endereço de próximo salto. Você, em seguida, associe a tabela de rota da sub-rede. Esse procedimento é conhecido como forçado encapsulamento. Para obter mais informações, consulte [Configure forçado encapsulamento](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span><span class="sxs-lookup"><span data-stu-id="23ceb-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="23ceb-372">**Figura 18: Rotas definidas pelo usuário e encapsulamento forçado para um VNet entre locais**</span><span class="sxs-lookup"><span data-stu-id="23ceb-372">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Figura 18: Rotas definidas pelo usuário e túnel forçado para uma rede virtual do Azure entre locais](images/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="23ceb-374">Figura 18 mostra uma VNet entre locais com uma rota definida pelo usuário para uma sub-rede apontando para o gateway do Azure.</span><span class="sxs-lookup"><span data-stu-id="23ceb-374">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="23ceb-375">Farm do SharePoint Server 2016 no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="23ceb-375">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="23ceb-376"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="23ceb-376"></span></span>

<span data-ttu-id="23ceb-377">Um exemplo de uma carga de trabalho de TI hospedado no Windows Azure IaaS intranet é a um farm do SharePoint Server 2016 altamente disponível e de várias camado, conforme mostrado na Figura 19.</span><span class="sxs-lookup"><span data-stu-id="23ceb-377">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm, as shown in Figure 19.</span></span>
  
<span data-ttu-id="23ceb-378">**Figura 19: Um farm de SharePoint Server 2016 de intranet altamente disponível no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="23ceb-378">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Farm de alta disponibilidade do SharePoint Server 2016 no Azure IaaS](images/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="23ceb-p117">Figura 19 mostra os nove servidores de um farm do SharePoint Server 2016 implantado em um VNet entre locais que usa balanceadores de carga interno para as camadas de front-end e de dados. Para obter mais informações, incluindo design passo a passo e instruções de implantação, consulte [2016 do SharePoint Server in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="23ceb-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span></span>
  
> [!TIP]
> <span data-ttu-id="23ceb-382">Para criar um farm do SharePoint Server 2016 de servidor único em um VNet simulado entre locais, consulte [Intranet do SharePoint Server 2016 no ambiente de desenvolvimento e teste do Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="23ceb-382">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span> 
  
<span data-ttu-id="23ceb-383">Para obter exemplos adicionais de cargas de trabalho do IT implantados nas máquinas virtuais em um virtual de Azure entre locais de rede, consulte [os cenários de nuvem híbrida para o Windows Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span><span class="sxs-lookup"><span data-stu-id="23ceb-383">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="23ceb-384">See Also</span><span class="sxs-lookup"><span data-stu-id="23ceb-384">See Also</span></span>

<span data-ttu-id="23ceb-385"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="23ceb-385"></span></span>

[<span data-ttu-id="23ceb-386">Microsoft Cloud Networking para arquitetos da empresa</span><span class="sxs-lookup"><span data-stu-id="23ceb-386">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="23ceb-387">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="23ceb-387">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="23ceb-388">Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="23ceb-388">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



