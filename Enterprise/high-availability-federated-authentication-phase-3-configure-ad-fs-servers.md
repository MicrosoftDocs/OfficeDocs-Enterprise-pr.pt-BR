---
title: "Alta disponibilidade federado servidores de autenticação fase 3 configurar o AD FS"
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
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: "Resumo: Criar e configurar os servidores de serviços de Federação do Active Directory (AD FS) para sua autenticação federada de alta disponibilidade para o Office 365 in Microsoft Azure."
ms.openlocfilehash: a9daecddb572bf2432d68ae76ed8d81571ef4b79
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="529cf-103">Autenticação federada de alta disponibilidade Fase 3: Configurar servidores do AD FS</span><span class="sxs-lookup"><span data-stu-id="529cf-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

 <span data-ttu-id="529cf-104">**Resumo:** Criar e configurar os servidores de serviços de Federação do Active Directory (AD FS) para sua autenticação federada de alta disponibilidade para o Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="529cf-104">**Summary:** Create and configure the Active Directory Federation Services (AD FS) servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="529cf-105">Nessa fase de implantação da alta disponibilidade para a autenticação federada do Office 365 nos serviços de infraestrutura do Azure, você cria um balanceador de carga interno e dois servidores AD FS.</span><span class="sxs-lookup"><span data-stu-id="529cf-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="529cf-p101">Você deve concluir esta fase antes de mover o logon em [alta disponibilidade federado autenticação fase 4: configurar proxies de aplicativo da web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.</span><span class="sxs-lookup"><span data-stu-id="529cf-p101">You must complete this phase before moving on to [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="529cf-108">Criar máquinas virtuais dos servidores do AD FS no Azure</span><span class="sxs-lookup"><span data-stu-id="529cf-108">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="529cf-p102">Use o seguinte bloco de comandos do PowerShell para criar as máquinas virtuais para os dois servidores do AD FS. Este conjunto de comandos do PowerShell usa valores das seguintes tabelas:</span><span class="sxs-lookup"><span data-stu-id="529cf-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="529cf-111">Tabela M, para suas máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="529cf-111">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="529cf-112">Tabela R, para seus grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="529cf-112">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="529cf-113">Tabela V, para suas configurações de rede virtual</span><span class="sxs-lookup"><span data-stu-id="529cf-113">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="529cf-114">Tabela S, para suas sub-redes</span><span class="sxs-lookup"><span data-stu-id="529cf-114">Table S, for your subnets</span></span>
    
- <span data-ttu-id="529cf-115">Tabela I, para seu endereço IP estático</span><span class="sxs-lookup"><span data-stu-id="529cf-115">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="529cf-116">Tabela A, para seus conjuntos de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="529cf-116">Table A, for your availability sets</span></span>
    
<span data-ttu-id="529cf-117">Lembre-se de que você definiu milhões de tabela em [alta disponibilidade federado autenticação fase 2: Configure os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) e tabelas R, V, S, I e A na [alta disponibilidade federado autenticação fase 1: configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="529cf-117">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="529cf-p103">O comando a seguir define usar a versão mais recente do Azure PowerShell. Consulte a [Introdução ao cmdlets do PowerShell do Windows Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="529cf-p103">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="529cf-p104">Primeiro, crie um balanceador de carga interno Azure para o AD dois servidores FS. Especifique os valores para as variáveis, removendo a \< e > caracteres. Quando você tiver fornecido todos os valores adequados, execute o bloco de resultante no prompt de comando do PowerShell do Azure ou com o PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="529cf-p104">First, you create an Azure internal load balancer for the two AD FS servers. Specify the values for the variables, removing the \< and > characters. When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="529cf-123">Para um arquivo de texto que contém todos os comandos do PowerShell este artigo e uma pasta de trabalho de configuração Microsoft Excel que gera blocos de comando do PowerShell pronto para executar com base em suas configurações personalizadas, consulte o [autenticação federada para o Office 365 Kit de implantação do Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="529cf-123">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzureRMLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="529cf-124">Em seguida, crie máquinas virtuais dos servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="529cf-124">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="529cf-125">Quando tiver fornecido todos os valores apropriados, execute o bloco resultante no prompt de comando do Azure PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="529cf-125">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="529cf-p105">Como essas máquinas virtuais são para um aplicativo de intranet, não estão atribuídos a um endereço IP público ou um rótulo de nome de domínio DNS e expostos à Internet. No entanto, isso também significa que você não pode se conectar a eles do portal do Azure. A opção **Conectar** está disponível quando você exibe as propriedades da máquina virtual. Use o acessório de Conexão de área de trabalho remota ou outra ferramenta de área de trabalho remota para se conectar à máquina virtual usando o privada IP endereço ou intranet nome DNS.</span><span class="sxs-lookup"><span data-stu-id="529cf-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="529cf-p106">Para cada máquina virtual, use o cliente de área de trabalho remota de sua preferência e crie uma conexão de área de trabalho remota. Use seu nome de computador ou DNS de intranet e as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="529cf-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="529cf-132">Para cada máquina virtual, associe-os ao domínio do AD apropriado do Windows Server com esses comandos no prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="529cf-132">For each virtual machine, join them to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="529cf-133">Veja a seguir a configuração resultante da conclusão bem-sucedida dessa fase, com nomes de computador de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="529cf-133">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="529cf-134">**Fase 3: Servidores AD FS e balanceador de carga interno para a sua infraestrutura de autenticação federada de alta disponibilidade no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="529cf-134">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 3 da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure com os servidores AD FS](images/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="529cf-136">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="529cf-136">Next step</span></span>

<span data-ttu-id="529cf-137">Uso [alta disponibilidade federado autenticação fase 4: configurar proxies de aplicativo da web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) para continuar a configurar essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="529cf-137">Use [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="529cf-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="529cf-138">See Also</span></span>

[<span data-ttu-id="529cf-139">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="529cf-139">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="529cf-140">Identidade federada para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="529cf-140">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


