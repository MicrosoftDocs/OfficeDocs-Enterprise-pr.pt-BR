---
title: Autenticação federada de alta disponibilidade fase 3 configurar servidores do AD FS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: 'Resumo: Crie e configure os servidores dos Serviços de Federação do Active Directory (AD FS) para a sua autenticação federada de alta disponibilidade para o Office 365 no Microsoft Azure.'
ms.openlocfilehash: b2ea785aa5bb2237df5509a2a4d4401cd149f36d
ms.sourcegitcommit: b85d3db24385d7e0bdbfb0d4499174ccd7f573bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "30650134"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="0776d-103">Autenticação federada de alta disponibilidade Fase 3: Configurar servidores do AD FS</span><span class="sxs-lookup"><span data-stu-id="0776d-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

 <span data-ttu-id="0776d-104">**Resumo:** Crie e configure os servidores dos Serviços de Federação do Active Directory (AD FS) para a sua autenticação federada de alta disponibilidade para o Office 365 no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="0776d-104">**Summary:** Create and configure the Active Directory Federation Services (AD FS) servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="0776d-105">Nessa fase de implantação da alta disponibilidade para a autenticação federada do Office 365 nos serviços de infraestrutura do Azure, você cria um balanceador de carga interno e dois servidores AD FS.</span><span class="sxs-lookup"><span data-stu-id="0776d-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="0776d-106">Você deve concluir essa fase antes de passar para [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span><span class="sxs-lookup"><span data-stu-id="0776d-106">You must complete this phase before moving on to [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="0776d-107">Consulte [implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.</span><span class="sxs-lookup"><span data-stu-id="0776d-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="0776d-108">Criar máquinas virtuais dos servidores do AD FS no Azure</span><span class="sxs-lookup"><span data-stu-id="0776d-108">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="0776d-p102">Use o seguinte bloco de comandos do PowerShell para criar as máquinas virtuais para os dois servidores do AD FS. Este conjunto de comandos do PowerShell usa valores das seguintes tabelas:</span><span class="sxs-lookup"><span data-stu-id="0776d-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="0776d-111">Tabela M, para suas máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="0776d-111">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="0776d-112">Tabela R, para seus grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="0776d-112">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="0776d-113">Tabela V, para suas configurações de rede virtual</span><span class="sxs-lookup"><span data-stu-id="0776d-113">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="0776d-114">Tabela S, para suas sub-redes</span><span class="sxs-lookup"><span data-stu-id="0776d-114">Table S, for your subnets</span></span>
    
- <span data-ttu-id="0776d-115">Tabela I, para seu endereço IP estático</span><span class="sxs-lookup"><span data-stu-id="0776d-115">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="0776d-116">Tabela A, para seus conjuntos de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="0776d-116">Table A, for your availability sets</span></span>
    
<span data-ttu-id="0776d-117">Lembre-se de que você definiu a tabela M na [autenticação federada de alta disponibilidade fase 2: configurar os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) e as tabelas R, V, S, I e A na [autenticação federada de alta disponibilidade fase 1: configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="0776d-117">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0776d-118">[!OBSERVAçãO] O comando a seguir define o uso da versão mais recente do Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0776d-118">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="0776d-119">Confira [Introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="0776d-119">See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="0776d-120">Em primeiro lugar, crie um balanceador de carga interno do Azure para os dois servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="0776d-120">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="0776d-121">Especifique os valores para as variáveis, removendo \< os caracteres e >.</span><span class="sxs-lookup"><span data-stu-id="0776d-121">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="0776d-122">Quando tiver fornecido todos os valores apropriados, execute o bloco resultante no prompt de comando do Azure PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0776d-122">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="0776d-123">Em seguida, crie máquinas virtuais dos servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="0776d-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="0776d-124">Quando tiver fornecido todos os valores apropriados, execute o bloco resultante no prompt de comando do Azure PowerShell ou no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0776d-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="0776d-p105">Como essas máquinas virtuais são para um aplicativo de intranet, elas não recebem um endereço IP público ou um rótulo de nome de domínio DNS, nem estão expostas à Internet. No entanto, isso também significa que você não pode se conectar a eles no portal do Azure. A opção **Conectar** não está disponível quando você visualiza as propriedades da máquina virtual. Use o acessório Conexão de Área de Trabalho Remota ou outra ferramenta de Área de Trabalho Remota para se conectar à máquina virtual usando seu endereço IP privado ou o nome DNS da intranet.</span><span class="sxs-lookup"><span data-stu-id="0776d-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="0776d-p106">Para cada máquina virtual, use o cliente de área de trabalho remota de sua preferência e crie uma conexão de área de trabalho remota. Use seu nome de computador ou DNS de intranet e as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="0776d-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="0776d-131">Para cada máquina virtual, associe-os ao domínio do AD apropriado do Windows Server com esses comandos no prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0776d-131">For each virtual machine, join them to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="0776d-132">Veja a seguir a configuração resultante da conclusão bem-sucedida dessa fase, com nomes de computador de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="0776d-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="0776d-133">**Fase 3: Os servidores do AD FS e o balanceador de carga interno para a sua infraestrutura de autenticação federada de alta disponibilidade no Azure**</span><span class="sxs-lookup"><span data-stu-id="0776d-133">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 3 da infraestrutura de autenticação federada de alta disponibilidade do Office 365 no Azure com os servidores AD FS](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="0776d-135">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="0776d-135">Next step</span></span>

<span data-ttu-id="0776d-136">Use o [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) para continuar configurando essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0776d-136">Use [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0776d-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="0776d-137">See Also</span></span>

[<span data-ttu-id="0776d-138">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="0776d-138">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="0776d-139">Identidade federada para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0776d-139">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


