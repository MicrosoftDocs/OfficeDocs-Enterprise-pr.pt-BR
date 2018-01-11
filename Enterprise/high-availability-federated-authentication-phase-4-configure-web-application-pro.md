---
title: "Alta disponibilidade federado proxies de aplicativo de web fase 4 configurar autenticação"
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: "Resumo: Configure os servidores de proxy de aplicativo web para sua autenticação federada de alta disponibilidade para o Office 365 in Microsoft Azure."
ms.openlocfilehash: 9e7c07a659993437776a7c26e5d02498b1680699
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="65dcc-103">Autenticação federada de alta disponibilidade Fase 4: Configurar proxies de aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="65dcc-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="65dcc-104">**Resumo:** Configure os servidores de proxy de aplicativo web para sua autenticação federada de alta disponibilidade para o Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="65dcc-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="65dcc-105">Nessa fase de implantação da alta disponibilidade para a autenticação federada do Office 365 nos serviços de infraestrutura do Azure, você cria um balanceador de carga interno e dois servidores AD FS.</span><span class="sxs-lookup"><span data-stu-id="65dcc-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="65dcc-p101">Você deve concluir esta fase antes de mover o logon em [alta disponibilidade federado autenticação fase 5: configurar a autenticação federada para o Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.</span><span class="sxs-lookup"><span data-stu-id="65dcc-p101">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="65dcc-108">Criar o balanceador de carga voltado para a Internet no Azure</span><span class="sxs-lookup"><span data-stu-id="65dcc-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="65dcc-109">Você deve criar um balanceador de carga voltado para a Internet para que o Azure distribua o tráfego de autenticação de cliente de entrada proveniente da Internet uniformemente entre os dois servidores proxy de aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="65dcc-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="65dcc-p102">O comando a seguir define usar a versão mais recente do Azure PowerShell. Consulte a [Introdução ao cmdlets do PowerShell do Windows Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="65dcc-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="65dcc-112">Quando tiver fornecido os valores de localização e grupo de recursos, execute o bloco resultante no prompt de comando do Azure PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65dcc-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="65dcc-113">Para um arquivo de texto que contém todos os comandos do PowerShell este artigo e uma pasta de trabalho de configuração Microsoft Excel que gera blocos de comando do PowerShell pronto para executar com base em suas configurações personalizadas, consulte o [autenticação federada para o Office 365 Kit de implantação do Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="65dcc-113">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzureRmPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzureRmLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="65dcc-114">Para exibir o endereço IP público atribuído ao seu balanceador de carga voltado para a Internet, execute estes comandos no prompt de comando do Azure PowerShell no computador local:</span><span class="sxs-lookup"><span data-stu-id="65dcc-114">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="65dcc-115">Determinar o FQDN do seu serviço de federação e criar registros DNS</span><span class="sxs-lookup"><span data-stu-id="65dcc-115">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="65dcc-p103">Você precisa determinar o nome DNS para identificar o nome do seu serviço de federação na Internet. O Azure AD Connect configurará o Office 365 com este nome na Fase 5, e ele se tornará parte da URL enviada pelo Office 365 aos clientes que se conectam para obter um token de segurança. Um exemplo é fs.contoso.com (fs representa serviço de federação).</span><span class="sxs-lookup"><span data-stu-id="65dcc-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="65dcc-119">Depois que você tiver o FQDN do serviço de federação, crie para ele um registro A de domínio DNS público que seja resolvido para o endereço IP público do balanceador de carga voltado para a Internet do Azure.</span><span class="sxs-lookup"><span data-stu-id="65dcc-119">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="65dcc-120">**Nome**</span><span class="sxs-lookup"><span data-stu-id="65dcc-120">**Name**</span></span>|<span data-ttu-id="65dcc-121">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="65dcc-121">**Type**</span></span>|<span data-ttu-id="65dcc-122">**TTL**</span><span class="sxs-lookup"><span data-stu-id="65dcc-122">**TTL**</span></span>|<span data-ttu-id="65dcc-123">**Valor**</span><span class="sxs-lookup"><span data-stu-id="65dcc-123">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="65dcc-124">FQDN do serviço de federação</span><span class="sxs-lookup"><span data-stu-id="65dcc-124">federation service FDQN</span></span>  <br/> |<span data-ttu-id="65dcc-125">A</span><span class="sxs-lookup"><span data-stu-id="65dcc-125">A</span></span>  <br/> |<span data-ttu-id="65dcc-126">3600</span><span class="sxs-lookup"><span data-stu-id="65dcc-126">3600</span></span>  <br/> |<span data-ttu-id="65dcc-127">endereço IP público do balanceador de carga voltados para a Internet do Windows Azure (exibido pelo comando **Write-Host** na seção anterior)</span><span class="sxs-lookup"><span data-stu-id="65dcc-127">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="65dcc-128">Este é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="65dcc-128">Here is an example:</span></span>
  
|<span data-ttu-id="65dcc-129">**Nome**</span><span class="sxs-lookup"><span data-stu-id="65dcc-129">**Name**</span></span>|<span data-ttu-id="65dcc-130">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="65dcc-130">**Type**</span></span>|<span data-ttu-id="65dcc-131">**TTL**</span><span class="sxs-lookup"><span data-stu-id="65dcc-131">**TTL**</span></span>|<span data-ttu-id="65dcc-132">**Valor**</span><span class="sxs-lookup"><span data-stu-id="65dcc-132">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="65dcc-133">FS.contoso.com</span><span class="sxs-lookup"><span data-stu-id="65dcc-133">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="65dcc-134">A</span><span class="sxs-lookup"><span data-stu-id="65dcc-134">A</span></span>  <br/> |<span data-ttu-id="65dcc-135">3600</span><span class="sxs-lookup"><span data-stu-id="65dcc-135">3600</span></span>  <br/> |<span data-ttu-id="65dcc-136">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="65dcc-136">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="65dcc-137">Em seguida, adicione um registro de endereço DNS ao namespace DNS particular da sua organização que resolva o FQDN do serviço de federação para o endereço IP privado atribuído ao balanceador de carga interno dos servidores do AD FS (Tabela I, item 4, coluna Valor).</span><span class="sxs-lookup"><span data-stu-id="65dcc-137">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="65dcc-138">Criar máquinas virtuais dos servidores proxy de aplicativos Web no Azure</span><span class="sxs-lookup"><span data-stu-id="65dcc-138">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="65dcc-139">Use o seguinte bloco de comandos do Azure PowerShell para criar as máquinas virtuais para os dois servidores proxy de aplicativos Web. </span><span class="sxs-lookup"><span data-stu-id="65dcc-139">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="65dcc-140">Observe que o seguinte comando do Azure PowerShell define valores de uso das tabelas a seguir:</span><span class="sxs-lookup"><span data-stu-id="65dcc-140">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="65dcc-141">Tabela M, para suas máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="65dcc-141">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="65dcc-142">Tabela R, para seus grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="65dcc-142">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="65dcc-143">Tabela V, para suas configurações de rede virtual</span><span class="sxs-lookup"><span data-stu-id="65dcc-143">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="65dcc-144">Tabela S, para suas sub-redes</span><span class="sxs-lookup"><span data-stu-id="65dcc-144">Table S, for your subnets</span></span>
    
- <span data-ttu-id="65dcc-145">Tabela I, para seu endereço IP estático</span><span class="sxs-lookup"><span data-stu-id="65dcc-145">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="65dcc-146">Tabela A, para seus conjuntos de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="65dcc-146">Table A, for your availability sets</span></span>
    
<span data-ttu-id="65dcc-147">Lembre-se de que você definiu milhões de tabela em [alta disponibilidade federado autenticação fase 2: Configure os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) e tabelas R, V, S, I e A na [alta disponibilidade federado autenticação fase 1: configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="65dcc-147">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="65dcc-148">Quando tiver fornecido todos os valores apropriados, execute o bloco resultante no prompt de comando do Azure PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65dcc-148">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="65dcc-p104">Como essas máquinas virtuais são para um aplicativo de intranet, não estão atribuídos a um endereço IP público ou um rótulo de nome de domínio DNS e expostos à Internet. No entanto, isso também significa que você não pode se conectar a eles do portal do Azure. A opção **Conectar** está disponível quando você exibe as propriedades da máquina virtual. Use o acessório de Conexão de área de trabalho remota ou outra ferramenta de área de trabalho remota para se conectar à máquina virtual usando seu privada endereço IP ou intranet DNS nome e as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="65dcc-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="65dcc-153">Veja a seguir a configuração resultante da conclusão bem-sucedida dessa fase, com nomes de computador de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="65dcc-153">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="65dcc-154">**Fase 4: O voltado à Internet carregar balanceador e servidores de proxy de aplicativo da web para a sua infraestrutura de autenticação federada de alta disponibilidade no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="65dcc-154">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 4 da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure com os servidores Proxy de aplicativo Web](images/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="65dcc-156">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="65dcc-156">Next step</span></span>

<span data-ttu-id="65dcc-157">Uso [alta disponibilidade federado autenticação fase 5: configurar a autenticação federada para o Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) para continuar a configurar essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65dcc-157">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="65dcc-158">Veja também</span><span class="sxs-lookup"><span data-stu-id="65dcc-158">See Also</span></span>

[<span data-ttu-id="65dcc-159">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="65dcc-159">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="65dcc-160">Identidade federada para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="65dcc-160">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="65dcc-161">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="65dcc-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="65dcc-162">Identidade federada para o Office 365</span><span class="sxs-lookup"><span data-stu-id="65dcc-162">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


