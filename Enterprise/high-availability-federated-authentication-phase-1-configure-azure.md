---
title: "Autenticação federada de alta disponibilidade fase 1 configurar o Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "Resumo: Configure a infraestrutura do Microsoft Azure para alta disponibilidade do host autenticação federada para o Office 365."
ms.openlocfilehash: f74e91930f5aef8f10986dcf51db6066c953014d
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="7fcb2-103">Autenticação federada de alta disponibilidade Fase 1: Configurar o Azure</span><span class="sxs-lookup"><span data-stu-id="7fcb2-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="7fcb2-104">**Resumo:** Configure a infraestrutura do Microsoft Azure para a autenticação de alta disponibilidade federada host para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="7fcb2-p101">Nesta fase, você pode criar os grupos de recursos, contas de armazenamento, conjuntos de rede (VNet) e disponibilidade virtuais no Azure que irá hospedar as máquinas virtuais em fases 2, 3 e 4. Você deve concluir esta fase antes de mover o logon em [alta disponibilidade federado autenticação fase 2: Configure os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p101">In this phase, you create the resource groups, storage accounts, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="7fcb2-108">Deve ser provisionados do Azure com esses componentes básicos:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="7fcb2-109">Grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="7fcb2-109">Resource groups</span></span>
    
- <span data-ttu-id="7fcb2-110">Uma rede virtual do Azure (VNet) entre locais com sub-redes para a hospedagem das máquinas virtuais do Azure</span><span class="sxs-lookup"><span data-stu-id="7fcb2-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="7fcb2-111">Grupos de segurança de rede para a realização do isolamento de sub-redes</span><span class="sxs-lookup"><span data-stu-id="7fcb2-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="7fcb2-112">Conjuntos de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="7fcb2-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="7fcb2-113">Configurar componentes do Azure</span><span class="sxs-lookup"><span data-stu-id="7fcb2-113">Configure Azure components</span></span>

<span data-ttu-id="7fcb2-p102">Antes de começar a configuração de componentes do Windows Azure, preencha as tabelas a seguir. Para ajudá-lo nos procedimentos para configurar o Azure, imprimir nesta seção e anote as informações necessárias ou copie nesta seção para um documento e preencha-lo. Para obter as configurações do VNet, preencha V da tabela.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="7fcb2-117">**Item**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-117">**Item**</span></span>|<span data-ttu-id="7fcb2-118">**Definição de configuração**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-118">**Configuration setting**</span></span>|<span data-ttu-id="7fcb2-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-119">**Description**</span></span>|<span data-ttu-id="7fcb2-120">**Valor**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="7fcb2-121">1.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-121">1.</span></span>  <br/> |<span data-ttu-id="7fcb2-122">Nome da VNet</span><span class="sxs-lookup"><span data-stu-id="7fcb2-122">VNet name</span></span>  <br/> |<span data-ttu-id="7fcb2-123">Um nome a ser atribuído à VNet (exemplo FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |<span data-ttu-id="7fcb2-124">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-124"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-125">2.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-125">2.</span></span>  <br/> |<span data-ttu-id="7fcb2-126">Local de VNet</span><span class="sxs-lookup"><span data-stu-id="7fcb2-126">VNet location</span></span>  <br/> |<span data-ttu-id="7fcb2-127">O datacenter do Azure regional que conterá a rede virtual.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-127">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |<span data-ttu-id="7fcb2-128">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-128"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-129">3.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-129">3.</span></span>  <br/> |<span data-ttu-id="7fcb2-130">Endereço IP do dispositivo VPN</span><span class="sxs-lookup"><span data-stu-id="7fcb2-130">VPN device IP address</span></span>  <br/> |<span data-ttu-id="7fcb2-131">O endereço IPv4 público da interface de seu dispositivo VPN na Internet. </span><span class="sxs-lookup"><span data-stu-id="7fcb2-131">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |<span data-ttu-id="7fcb2-132">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-132"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-133">4.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-133">4.</span></span>  <br/> |<span data-ttu-id="7fcb2-134">Espaço de endereço da VNet</span><span class="sxs-lookup"><span data-stu-id="7fcb2-134">VNet address space</span></span>  <br/> |<span data-ttu-id="7fcb2-p103">O espaço de endereço da rede virtual. Trabalhe com seu departamento de TI para determinar esse espaço de endereço.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |<span data-ttu-id="7fcb2-137">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-137"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-138">5.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-138">5.</span></span>  <br/> |<span data-ttu-id="7fcb2-139">Chave compartilhada IPsec</span><span class="sxs-lookup"><span data-stu-id="7fcb2-139">IPsec shared key</span></span>  <br/> |<span data-ttu-id="7fcb2-p104">Uma 32 aleatória, alfanumérica cadeia de caracteres que será usada para autenticar a ambos os lados da conexão de VPN-to-site. Trabalhar com sua equipe de TI ou o departamento de segurança para determinar o valor da chave. Como alternativa, consulte [criar uma cadeia de caracteres aleatória para uma chave pré compartilhada do IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="7fcb2-143">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-143"></span></span>  <br/> |
   
 <span data-ttu-id="7fcb2-144">**Tabela V: Configuração de rede virtual entre locais**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-144">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="7fcb2-p105">Em seguida, preencha a Tabela S para as sub-redes desta solução. Todos os espaços de endereço devem estar no formato de Roteamento entre Domínios sem Classificação (CIDR), também conhecido como formato de prefixo de rede. Um exemplo é 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="7fcb2-p106">Para as três primeiras sub-redes, especifique um nome e um único espaço de endereços IP com base no espaço de endereço da rede virtual. Para a sub-rede de gateway, determine um espaço de endereço de 27 bits (com um comprimento de prefixo /27) para a sub-rede do gateway do Azure. Use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="7fcb2-150">Defina os bits variáveis no espaço de endereço da VNet como 1, até os bits que estão sendo usados pela sub-rede do gateway, e depois defina os bits restantes como 0.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-150">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="7fcb2-151">Converta os bits resultantes em decimais e expresse-os como um espaço de endereço com o comprimento de prefixo definido como o tamanho da sub-rede do gateway.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-151">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="7fcb2-152">Consulte [Calculadora de espaço de endereço para sub-redes do Azure gateway](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for um bloco de comando do PowerShell e o aplicativo de console c# ou Python que realiza esse cálculo para você.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-152">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="7fcb2-153">Trabalhe com seu departamento de TI para determinar esses espaços de endereço a partir do espaço de endereço da rede virtual.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-153">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="7fcb2-154">**Item**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-154">**Item**</span></span>|<span data-ttu-id="7fcb2-155">**Nome da sub-rede**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-155">**Subnet name**</span></span>|<span data-ttu-id="7fcb2-156">**Espaço de endereço da sub-rede**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-156">**Subnet address space**</span></span>|<span data-ttu-id="7fcb2-157">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-157">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="7fcb2-158">1.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-158">1.</span></span>  <br/> |<span data-ttu-id="7fcb2-159">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-159"></span></span>  <br/> |<span data-ttu-id="7fcb2-160">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-160"></span></span>  <br/> |<span data-ttu-id="7fcb2-161">A sub-rede usada pelo controlador de domínio e as máquinas virtuais (VMs) DirSync do Windows Server Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-161">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="7fcb2-162">2.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-162">2.</span></span>  <br/> |<span data-ttu-id="7fcb2-163">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-163"></span></span>  <br/> |<span data-ttu-id="7fcb2-164">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-164"></span></span>  <br/> |<span data-ttu-id="7fcb2-165">A sub-rede usada pelos VMs do AD FS.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-165">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="7fcb2-166">3.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-166">3.</span></span>  <br/> |<span data-ttu-id="7fcb2-167">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-167"></span></span>  <br/> |<span data-ttu-id="7fcb2-168">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-168"></span></span>  <br/> |<span data-ttu-id="7fcb2-169">A sub-rede usada pelas VMs de proxy do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-169">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="7fcb2-170">4.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-170">4.</span></span>  <br/> |<span data-ttu-id="7fcb2-171">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="7fcb2-171">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="7fcb2-172">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-172"></span></span>  <br/> |<span data-ttu-id="7fcb2-173">A sub-rede usada pelas VMs do gateway do Azure.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-173">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="7fcb2-174">**Tabela S: Sub-redes na rede virtual**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-174">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="7fcb2-175">Em seguida, preencha a Tabela I para os endereços IP estáticos atribuídos a máquinas virtuais e instâncias de balanceador de carga.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-175">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="7fcb2-176">**Item**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-176">**Item**</span></span>|<span data-ttu-id="7fcb2-177">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-177">**Purpose**</span></span>|<span data-ttu-id="7fcb2-178">**Endereço IP da sub-rede**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-178">**IP address on the subnet**</span></span>|<span data-ttu-id="7fcb2-179">**Valor**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-179">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="7fcb2-180">1.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-180">1.</span></span>  <br/> |<span data-ttu-id="7fcb2-181">Endereço IP estático do primeiro controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="7fcb2-181">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="7fcb2-182">O quarto endereço IP possível para o espaço de endereço da sub-rede definido no Item 1 da Tabela S.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-182">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="7fcb2-183">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-183"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-184">2.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-184">2.</span></span>  <br/> |<span data-ttu-id="7fcb2-185">Endereço IP estático do segundo controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="7fcb2-185">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="7fcb2-186">O quinto endereço IP possível para o espaço de endereço da sub-rede definido no Item 1 da Tabela S.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-186">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="7fcb2-187">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-187"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-188">3.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-188">3.</span></span>  <br/> |<span data-ttu-id="7fcb2-189">Endereço IP estático do servidor DirSync</span><span class="sxs-lookup"><span data-stu-id="7fcb2-189">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="7fcb2-190">O sexto endereço IP possível para o espaço de endereço da sub-rede definido no Item 1 da Tabela S. </span><span class="sxs-lookup"><span data-stu-id="7fcb2-190">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="7fcb2-191">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-191"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-192">4.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-192">4.</span></span>  <br/> |<span data-ttu-id="7fcb2-193">Endereço IP estático do balanceador de carga internos para os servidores do AD FS</span><span class="sxs-lookup"><span data-stu-id="7fcb2-193">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="7fcb2-194">O quarto endereço IP possível para o espaço de endereço da sub-rede definido no Item 2 da Tabela S. </span><span class="sxs-lookup"><span data-stu-id="7fcb2-194">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="7fcb2-195">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-195"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-196">5.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-196">5.</span></span>  <br/> |<span data-ttu-id="7fcb2-197">Endereço IP estático do primeiro servidor do AD FS</span><span class="sxs-lookup"><span data-stu-id="7fcb2-197">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="7fcb2-198">O quinto endereço IP possível para o espaço de endereço da sub-rede definido no Item 2 da Tabela S.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-198">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="7fcb2-199">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-199"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-200">6.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-200">6.</span></span>  <br/> |<span data-ttu-id="7fcb2-201">Endereço IP estático do segundo servidor do AD FS</span><span class="sxs-lookup"><span data-stu-id="7fcb2-201">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="7fcb2-202">O sexto endereço IP possível para o espaço de endereço da sub-rede definido no Item 2 da Tabela S.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-202">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="7fcb2-203">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-203"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-204">7.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-204">7.</span></span>  <br/> |<span data-ttu-id="7fcb2-205">Endereço IP estático do primeiro servidor proxy de aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="7fcb2-205">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="7fcb2-206">O quarto endereço IP possível para o espaço de endereço da sub-rede definido no Item 3 da Tabela S.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-206">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="7fcb2-207">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-207"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-208">8.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-208">8.</span></span>  <br/> |<span data-ttu-id="7fcb2-209">Endereço IP estático do segundo servidor proxy de aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="7fcb2-209">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="7fcb2-210">O quinto endereço IP possível para o espaço de endereço da sub-rede definido no Item 3 da Tabela S.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-210">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="7fcb2-211">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-211"></span></span>  <br/> |
   
 <span data-ttu-id="7fcb2-212">**Endereços de IP estático de i: tabela na rede virtual**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-212">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="7fcb2-213">Para dois servidores de Sistema de Nomes de Domínio (DNS) na sua rede local que você deseja usar ao configurar controladores de domínio inicialmente na sua rede virtual, preencha a Tabela D. Trabalhe com o departamento de TI para determinar essa lista.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-213">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="7fcb2-214">**Item**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-214">**Item**</span></span>|<span data-ttu-id="7fcb2-215">**Nome amigável do servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-215">**DNS server friendly name**</span></span>|<span data-ttu-id="7fcb2-216">**Endereço IP do servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-216">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7fcb2-217">1.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-217">1.</span></span>  <br/> |<span data-ttu-id="7fcb2-218">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-218"></span></span>  <br/> |<span data-ttu-id="7fcb2-219">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-219"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-220">2.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-220">2.</span></span>  <br/> |<span data-ttu-id="7fcb2-221">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-221"></span></span>  <br/> |<span data-ttu-id="7fcb2-222">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-222"></span></span>  <br/> |
   
 <span data-ttu-id="7fcb2-223">**Tabela D: servidores DNS locais**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-223">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="7fcb2-p107">Para rotear pacotes da rede entre locais para a rede da organização entre a conexão de VPN site a site, você deve configurar a rede virtual com uma rede local que contenha uma lista dos espaços de endereço (em notação CIDR) para todos os locais acessíveis na rede local da sua organização. A lista de espaços de endereço que definem a sua rede local deve ser exclusiva e não deve ser ficar sobreposta ao espaço de endereço usado para outras redes virtuais ou locais.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="7fcb2-p108">Para o conjunto de espaços de endereço da rede local, preencha a Tabela L. Observe que há três entradas em branco listadas, mas geralmente você precisará de mais. Trabalhe com seu departamento de TI para determinar esta lista de espaços de endereço.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="7fcb2-228">**Item**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-228">**Item**</span></span>|<span data-ttu-id="7fcb2-229">**Espaço de endereço da rede local**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-229">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7fcb2-230">1.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-230">1.</span></span>  <br/> |<span data-ttu-id="7fcb2-231">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-231"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-232">2.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-232">2.</span></span>  <br/> |<span data-ttu-id="7fcb2-233">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-233"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-234">3.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-234">3.</span></span>  <br/> |<span data-ttu-id="7fcb2-235">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-235"></span></span>  <br/> |
   
 <span data-ttu-id="7fcb2-236">**Tabela L: Prefixos de endereço para a rede local**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-236">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="7fcb2-237">Agora, vamos começar a criar a infraestrutura do Azure para hospedar sua autenticação federada para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-237">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7fcb2-p109">O comando a seguir define usar a versão mais recente do Azure PowerShell. Consulte a [Introdução ao cmdlets do PowerShell do Windows Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="7fcb2-240">Primeiro, inicie um prompt do Azure PowerShell e faça logon na sua conta.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-240">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="7fcb2-241">Para um arquivo de texto que contém todos os comandos do PowerShell este artigo e uma pasta de trabalho de configuração Microsoft Excel que gera blocos de comando do PowerShell pronto para executar com base em suas configurações personalizadas, consulte o [autenticação federada para o Office 365 Kit de implantação do Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-241">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="7fcb2-242">Para obter o nome de sua assinatura, use este comando.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-242">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="7fcb2-243">Para versões mais antigas do Azure PowerShell, use este comando.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-243">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="7fcb2-p110">Defina sua assinatura do Windows Azure. Substituir tudo entre aspas, incluindo o \< e > caracteres, com o nome correto.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="7fcb2-p111">Em seguida, crie os novos grupos de recursos. Para determinar um conjunto exclusivo de nomes de grupo de recursos, use este comando para listar os grupos de recurso existentes.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="7fcb2-248">Preencha a tabela a seguir para o conjunto de nomes de grupos de recursos exclusivos.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-248">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="7fcb2-249">**Item**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-249">**Item**</span></span>|<span data-ttu-id="7fcb2-250">**Nome do grupo de recursos**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-250">**Resource group name**</span></span>|<span data-ttu-id="7fcb2-251">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-251">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7fcb2-252">1.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-252">1.</span></span>  <br/> |<span data-ttu-id="7fcb2-253">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-253"></span></span>  <br/> |<span data-ttu-id="7fcb2-254">Controladores de domínio:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-254">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="7fcb2-255">2.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-255">2.</span></span>  <br/> |<span data-ttu-id="7fcb2-256">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-256"></span></span>  <br/> |<span data-ttu-id="7fcb2-257">Servidores do AD FS</span><span class="sxs-lookup"><span data-stu-id="7fcb2-257">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="7fcb2-258">3.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-258">3.</span></span>  <br/> |<span data-ttu-id="7fcb2-259">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-259"></span></span>  <br/> |<span data-ttu-id="7fcb2-260">Servidores proxy de aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="7fcb2-260">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="7fcb2-261">4.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-261">4.</span></span>  <br/> |<span data-ttu-id="7fcb2-262">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-262"></span></span>  <br/> |<span data-ttu-id="7fcb2-263">Elementos de infraestrutura</span><span class="sxs-lookup"><span data-stu-id="7fcb2-263">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="7fcb2-264">**Tabela r: grupos de recursos**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-264">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="7fcb2-265">Crie os novos grupos de recursos com estes comandos.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-265">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="7fcb2-266">Em seguida, você criará a rede virtual do Azure e suas sub-redes.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-266">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="7fcb2-p112">Em seguida, crie rede grupos de segurança para cada sub-rede que contém as máquinas virtuais. Para executar o isolamento de sub-rede, você pode adicionar regras para os tipos específicos de tráfego permitido ou negado ao grupo de segurança de rede de uma sub-rede.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="7fcb2-269">Em seguida, use estes comandos para criar os gateways para a conexão VPN site a site.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-269">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="7fcb2-p113">Autenticação federada de usuários individuais não depende do quaisquer recursos locais. No entanto, se essa conexão de VPN-to-site ficar indisponível, os controladores de domínio em que o VNet não receberá as atualizações feitos no servidor local Windows AD de grupos e contas de usuário. Para garantir que isso não acontecer, você pode configurar a alta disponibilidade para sua conexão de VPN-to-site. Para obter mais informações, consulte [altamente disponível entre locais e conectividade de VNet para VNet](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="7fcb2-274">Em seguida, registre o endereço IPv4 público do gateway de VPN do Azure para a sua rede virtual na exibição deste comando:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-274">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="7fcb2-p114">Em seguida, configure seu dispositivo VPN de local para se conectar ao gateway VPN do Windows Azure. Para obter mais informações, consulte [Configure seu dispositivo VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="7fcb2-277">Para configurar seu dispositivo VPN local, você precisará do seguinte:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-277">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="7fcb2-278">O endereço IPv4 público do gateway de VPN do Azure.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-278">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="7fcb2-279">A chave pré-compartilhada IPsec para a conexão de VPN-to-site (coluna de tabela V - Item 5 - valor).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-279">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="7fcb2-p115">Em seguida, certifique-se de que o espaço de endereço da rede virtual seja acessível a partir da sua rede local. Isso é feito geralmente com a inclusão de uma rota correspondente ao espaço de endereço da rede virtual para o seu dispositivo VPN e, em seguida, publicando essa rota ao restante da infraestrutura de roteamento da rede da sua organização. Trabalhe com seu departamento de TI para determinar como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="7fcb2-p116">Em seguida, defina os nomes de três conjuntos de disponibilidade. Preencha a Tabela A. </span><span class="sxs-lookup"><span data-stu-id="7fcb2-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="7fcb2-285">**Item**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-285">**Item**</span></span>|<span data-ttu-id="7fcb2-286">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-286">**Purpose**</span></span>|<span data-ttu-id="7fcb2-287">**Nome do conjunto de disponibilidade**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-287">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7fcb2-288">1.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-288">1.</span></span>  <br/> |<span data-ttu-id="7fcb2-289">Controladores de domínio:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-289">Domain controllers</span></span>  <br/> |<span data-ttu-id="7fcb2-290">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-290"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-291">2.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-291">2.</span></span>  <br/> |<span data-ttu-id="7fcb2-292">Servidores do AD FS</span><span class="sxs-lookup"><span data-stu-id="7fcb2-292">AD FS servers</span></span>  <br/> |<span data-ttu-id="7fcb2-293">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-293"></span></span>  <br/> |
|<span data-ttu-id="7fcb2-294">3.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-294">3.</span></span>  <br/> |<span data-ttu-id="7fcb2-295">Servidores proxy de aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="7fcb2-295">Web application proxy servers</span></span>  <br/> |<span data-ttu-id="7fcb2-296">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7fcb2-296"></span></span>  <br/> |
   
 <span data-ttu-id="7fcb2-297">**Conjuntos de disponibilidade de r: tabela**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-297">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="7fcb2-298">Você precisará desses nomes quando criar as máquinas virtuais nas fases 2, 3 e 4.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-298">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="7fcb2-299">Crie os novos conjuntos de disponibilidade com estes comandos do Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-299">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

<span data-ttu-id="7fcb2-300">Esta é a configuração resultante da conclusão bem-sucedida dessa fase.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-300">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="7fcb2-301">**Fase 1: A infraestrutura Azure para autenticação federada de alta disponibilidade para o Office 365**</span><span class="sxs-lookup"><span data-stu-id="7fcb2-301">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Fase 1 da autenticação federada de alta disponibilidade para o Office 365 no Azure com a infraestrutura do Azure](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="7fcb2-303">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="7fcb2-303">Next step</span></span>

<span data-ttu-id="7fcb2-304">Uso [alta disponibilidade federado autenticação fase 2: Configure os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) para continuar com a configuração dessa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-304">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7fcb2-305">Veja também</span><span class="sxs-lookup"><span data-stu-id="7fcb2-305">See Also</span></span>

[<span data-ttu-id="7fcb2-306">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="7fcb2-306">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="7fcb2-307">Identidade federada para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="7fcb2-307">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="7fcb2-308">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="7fcb2-308">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="7fcb2-309">Identidade federada para o Office 365</span><span class="sxs-lookup"><span data-stu-id="7fcb2-309">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


