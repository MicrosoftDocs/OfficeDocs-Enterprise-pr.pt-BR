---
title: Rede virtual simulada entre locais no Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: 'Resumo: crie uma rede virtual simulada entre locais no Microsoft Azure como um ambiente de desenvolvimento/teste.'
ms.openlocfilehash: 42ef04a92794c8df53d3de32970db78d4dcf3119
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193661"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="2e534-103">Rede virtual simulada entre locais no Azure</span><span class="sxs-lookup"><span data-stu-id="2e534-103">Simulated cross-premises virtual network in Azure</span></span>

 <span data-ttu-id="2e534-104">**Resumo:** crie uma rede virtual simulada entre locais no Microsoft Azure como um ambiente de desenvolvimento/teste.</span><span class="sxs-lookup"><span data-stu-id="2e534-104">**Summary:** Create a simulated cross-premises virtual network in Microsoft Azure as a dev/test environment.</span></span>
  
<span data-ttu-id="2e534-p101">Este artigo ajuda você a criar um ambiente simulado de nuvem híbrida com o Microsoft Azure usando duas redes virtuais do Azure. Veja a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="2e534-p101">This article steps you through creating a simulated hybrid cloud environment with Microsoft Azure using two Azure virtual networks. Here is the resulting configuration.</span></span> 
  
![Fase 3 do ambiente de desenvolvimento/teste da rede virtual simulada entre locais, com a máquina virtual DC2 na VNet XPrem](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="2e534-108">Isso simula um ambiente de produção de nuvem híbrida para o IaaS do Azure e consiste em:</span><span class="sxs-lookup"><span data-stu-id="2e534-108">This simulates an Azure IaaS hybrid cloud production environment and consists of:</span></span>
  
- <span data-ttu-id="2e534-109">Uma rede local simulada e simplificada hospedada na rede virtual do Azure (a rede virtual TestLab). </span><span class="sxs-lookup"><span data-stu-id="2e534-109">A simulated and simplified on-premises network hosted in an Azure virtual network (the TestLab virtual network).</span></span>
    
- <span data-ttu-id="2e534-110">Uma rede virtual simulada entre locais hospedada no Azure (XPrem).</span><span class="sxs-lookup"><span data-stu-id="2e534-110">A simulated cross-premises virtual network hosted in Azure (XPrem).</span></span>
    
- <span data-ttu-id="2e534-111">Uma relação de emparelhamento de VNets entre as duas redes virtuais.</span><span class="sxs-lookup"><span data-stu-id="2e534-111">A VNet peering relationship between the two virtual networks.</span></span>
    
- <span data-ttu-id="2e534-112">Um controlador de domínio secundário na rede virtual XPrem.</span><span class="sxs-lookup"><span data-stu-id="2e534-112">A single-server SharePoint farm (SP1 and SQL1) and secondary domain controller (DC2) in the XPrem virtual network.</span></span>
    
<span data-ttu-id="2e534-113">Isso fornece uma base e um ponto de partida comuns a partir dos quais você pode:</span><span class="sxs-lookup"><span data-stu-id="2e534-113">This configuration provides a basis and common starting point from which you can:</span></span> 
  
- <span data-ttu-id="2e534-114">Desenvolver e testar aplicativos em um ambiente simulado de nuvem híbrida para o IaaS do Azure.</span><span class="sxs-lookup"><span data-stu-id="2e534-114">Develop and test applications in a simulated Azure IaaS hybrid cloud environment.</span></span>
    
- <span data-ttu-id="2e534-115">Criar configurações de teste para computadores, algumas na rede virtual TestLab e outras na rede virtual XPrem, para simular cargas de trabalho de TI baseadas na nuvem híbrida.</span><span class="sxs-lookup"><span data-stu-id="2e534-115">Create test configurations of computers, some within the TestLab virtual network and some within the XPrem virtual network, to simulate hybrid cloud-based IT workloads.</span></span>
    
<span data-ttu-id="2e534-116">Há três fases principais para configurar esse ambiente de desenvolvimento/teste:</span><span class="sxs-lookup"><span data-stu-id="2e534-116">There are three major phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="2e534-117">Configurar a rede virtual TestLab.</span><span class="sxs-lookup"><span data-stu-id="2e534-117">Configure the TestLab virtual network.</span></span>
    
2. <span data-ttu-id="2e534-118">Criar a rede virtual entre locais.</span><span class="sxs-lookup"><span data-stu-id="2e534-118">Create the cross-premises virtual network in Azure.</span></span>
    
3. <span data-ttu-id="2e534-119">Configurar o DC2.</span><span class="sxs-lookup"><span data-stu-id="2e534-119">Configure DC2.</span></span>
    
> [!NOTE]
> <span data-ttu-id="2e534-120">Essa configuração requer uma assinatura paga do Azure.</span><span class="sxs-lookup"><span data-stu-id="2e534-120">This configuration requires a paid Azure subscription.</span></span> 
  
![Guias do Laboratório de Teste da Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="2e534-122">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="2e534-122">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a><span data-ttu-id="2e534-123">Fase 1: configurar a rede virtual TestLab</span><span class="sxs-lookup"><span data-stu-id="2e534-123">Phase 1: Configure the TestLab virtual network</span></span>

<span data-ttu-id="2e534-124">Use as instruções em [Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) para configurar os computadores DC1, APP1 e CLIENT1 na rede virtual Azure chamada TestLab.</span><span class="sxs-lookup"><span data-stu-id="2e534-124">Use the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md) to configure the DC1, APP1, and CLIENT1 computers in the Azure virtual network named TestLab.</span></span>
  
<span data-ttu-id="2e534-125">Esta é sua configuração atual.</span><span class="sxs-lookup"><span data-stu-id="2e534-125">This is your resulting configuration.</span></span> 
  
![Fase 4 da Configuração básica no Azure com a máquina virtual CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a><span data-ttu-id="2e534-127">Fase 2: criar uma rede virtual XPrem</span><span class="sxs-lookup"><span data-stu-id="2e534-127">Phase 2: Create the cross-premises virtual network in Azure</span></span>

<span data-ttu-id="2e534-128">Nesta fase, crie e configure a nova rede virtual XPrem e conecte-se à rede virtual TestLab com emparelhamento de VNets.</span><span class="sxs-lookup"><span data-stu-id="2e534-128">In this phase, you create and configure the new XPrem virtual network and then connect it to the TestLab virtual network with VNet peering.</span></span>
  
<span data-ttu-id="2e534-129">Primeiro, inicie um prompt do Azure PowerShell em seu computador local.</span><span class="sxs-lookup"><span data-stu-id="2e534-129">First, start an Azure PowerShell prompt on your local computer.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2e534-p102">O comando a seguir define o uso da versão mais recente do Azure PowerShell. Confira [Introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/pt-BR/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="2e534-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/pt-BR/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="2e534-132">Entre na sua conta do Azure usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e534-132">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="2e534-133">Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) para obter um arquivo de texto que contém todos os comandos do PowerShell usados neste artigo.</span><span class="sxs-lookup"><span data-stu-id="2e534-133">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) to get a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="2e534-134">Para obter o nome de sua assinatura, use este comando.</span><span class="sxs-lookup"><span data-stu-id="2e534-134">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="2e534-p103">Defina sua assinatura do Azure. Substitua tudo o que está entre aspas, incluindo os caracteres \< e >, pelos nomes corretos.</span><span class="sxs-lookup"><span data-stu-id="2e534-p103">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

<span data-ttu-id="2e534-137">Em seguida, crie a rede virtual XPrem e proteja-a usando um grupo de segurança de rede com estes comandos.</span><span class="sxs-lookup"><span data-stu-id="2e534-137">Next, create the XPrem virtual network and protect it with a network security group with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$Testnet=New-AzureRMVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzureRMVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
```

<span data-ttu-id="2e534-138">Depois, crie a relação de emparelhamento de VNets entre as VNets TestLab e XPrem com estes comandos.</span><span class="sxs-lookup"><span data-stu-id="2e534-138">Next, you create the VNet peering relationship between the TestLab and XPrem VNets with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

<span data-ttu-id="2e534-139">Esta é sua configuração atual.</span><span class="sxs-lookup"><span data-stu-id="2e534-139">This is your resulting configuration.</span></span> 
  
![Fase 2 do ambiente de desenvolvimento/teste da rede virtual simulada entre locais, com a relação de emparelhamento de VNet e VNet XPrem](images/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a><span data-ttu-id="2e534-141">Fase 3: configurar o DC2</span><span class="sxs-lookup"><span data-stu-id="2e534-141">Phase 3: Configure DC2</span></span>

<span data-ttu-id="2e534-142">Nesta fase, crie a máquina virtual DC2 na rede virtual XPrem e configure-a como um controlador de domínio de réplica.</span><span class="sxs-lookup"><span data-stu-id="2e534-142">In this phase, you create the DC2 virtual machine in the XPrem virtual network and then configure it as a replica domain controller.</span></span>
  
<span data-ttu-id="2e534-p104">Primeiro, crie uma máquina virtual para o DC2. Execute esses comandos no prompt de comando do Azure PowerShell em seu computador local.</span><span class="sxs-lookup"><span data-stu-id="2e534-p104">First, create a virtual machine for DC2. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<your resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzureRMVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="2e534-145">Em seguida, conecte-se à nova máquina virtual DC2 a partir do [portal do Azure](https://portal.azure.com) usando o nome e a senha da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="2e534-145">Next, connect to the new DC2 virtual machine from the [Azure portal](https://portal.azure.com) using its local administrator account name and password.</span></span>
  
<span data-ttu-id="2e534-p105">Em seguida, configure uma regra de Firewall do Windows para permitir o tráfego para testes básicos de conectividade. No DC2, em um prompt de comando de nível de administrador do Windows PowerShell, execute esses comandos.</span><span class="sxs-lookup"><span data-stu-id="2e534-p105">Next, configure a Windows Firewall rule to allow traffic for basic connectivity testing. From an administrator-level Windows PowerShell command prompt on DC2, run these commands.</span></span> 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

<span data-ttu-id="2e534-p106">O comando ping deve resultar em quatro respostas bem-sucedidas do endereço IP 10.0.0.4. Este é um teste de tráfego entre a relação de emparelhamento de VNets.</span><span class="sxs-lookup"><span data-stu-id="2e534-p106">The ping command should result in four successful replies from IP address 10.0.0.4. This is a test of traffic across the VNet peering relationship.</span></span> 
  
<span data-ttu-id="2e534-150">Em seguida, adicione o disco de dados extra como um novo volume com a letra de unidade F:, com este comando em um prompt de comando do Windows PowerShell no DC2.</span><span class="sxs-lookup"><span data-stu-id="2e534-150">
        Next, add an extra data disk as a new volume with the drive letter F: and create folders with these commands at an administrator-level Windows PowerShell command prompt on sqlVM.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="2e534-p107">Depois, configure o DC2 como controlador de domínio de réplica para o domínio corp.contoso.com. Execute estes comandos em um prompt de comando do Windows PowerShell no DC2.</span><span class="sxs-lookup"><span data-stu-id="2e534-p107">Next, configure adVM as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt on adVM.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

<span data-ttu-id="2e534-153">Observe que você será solicitado a fornecer a senha de CORP\\Usuário1 e uma senha do Modo de Restauração dos Serviços de Diretório (DSRM) e a reiniciar o DC2.</span><span class="sxs-lookup"><span data-stu-id="2e534-153">Note that you are prompted to supply both the CORP\\User1 password and a Directory Services Restore Mode (DSRM) password, and to restart DC2.</span></span> 
  
<span data-ttu-id="2e534-p108">Agora que a rede virtual XPrem tem seu próprio servidor DNS (DC2), você deve configurá-la para usar esse servidor DNS. Execute esses comandos no prompt de comando do Azure PowerShell em seu computador local.</span><span class="sxs-lookup"><span data-stu-id="2e534-p108">Now that the XPrem virtual network has its own DNS server (DC2), you must configure the XPrem virtual network to use this DNS server. Run these commands from the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

<span data-ttu-id="2e534-p109">No portal do Azure no computador local, conecte-se ao DC1 com as credenciais CORP\\Usuário1. Para configurar o domínio CORP de modo que os computadores e usuários usem seu controlador de domínio local para autenticação, execute esses comandos em um prompt de comando do Windows PowerShell como administrador no DC1.</span><span class="sxs-lookup"><span data-stu-id="2e534-p109">From the Azure portal on your local computer, connect to DC1 with the CORP\\User1 credentials. To configure the CORP domain so that computers and users use their local domain controller for authentication, run these commands from an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

<span data-ttu-id="2e534-158">Esta é sua configuração atual.</span><span class="sxs-lookup"><span data-stu-id="2e534-158">This is your resulting configuration.</span></span> 
  
![Fase 3 do ambiente de desenvolvimento/teste da rede virtual simulada entre locais, com a máquina virtual DC2 na VNet XPrem](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="2e534-160">Seu ambiente simulado de nuvem híbrida do Azure já está pronto para testes.</span><span class="sxs-lookup"><span data-stu-id="2e534-160">Your simulated Azure hybrid cloud environment is now ready for testing.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="2e534-161">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="2e534-161">Next step</span></span>

<span data-ttu-id="2e534-162">Use este ambiente de desenvolvimento/teste para simular um [farm de Intranet do SharePoint Server 2016 hospedado no Azure ](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="2e534-162">Use this dev/test environment to simulate a [SharePoint Server 2016 intranet farm hosted in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2e534-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e534-163">See Also</span></span>

<span data-ttu-id="2e534-164">[Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="2e534-164">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="2e534-165">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="2e534-165">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="2e534-166">DirSync para o ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="2e534-166">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="2e534-167">Cloud App Security para o ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="2e534-167">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="2e534-168">Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="2e534-168">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="2e534-169">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="2e534-169">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


