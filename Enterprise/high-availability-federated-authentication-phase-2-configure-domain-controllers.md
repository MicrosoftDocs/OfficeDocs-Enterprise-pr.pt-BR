---
title: Autenticação federada de alta disponibilidade fase 2 configure os controladores de domínio
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Resumo: Configure os controladores de domínio e o servidor de sincronização de diretório para a autenticação federada de alta disponibilidade para o Microsoft 365 no Microsoft Azure.'
ms.openlocfilehash: 14939691e8dc114a6234bfee1ade7212762eae04
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102519"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="98ee4-103">Autenticação federada de alta disponibilidade Fase 2: configurar controladores de domínio</span><span class="sxs-lookup"><span data-stu-id="98ee4-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

<span data-ttu-id="98ee4-104">Nesta fase de implantação de alta disponibilidade para a autenticação federada do Microsoft 365 nos serviços de infraestrutura do Azure, configure dois controladores de domínio e o servidor de sincronização de diretório na rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="98ee4-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the directory synchronization server in the Azure virtual network.</span></span> <span data-ttu-id="98ee4-105">Solicitações da Web de clientes para autenticação podem então ser autenticadas na rede virtual do Azure, em vez de o tráfego de autenticação ser enviado na conexão de VPN site a site à sua rede local.</span><span class="sxs-lookup"><span data-stu-id="98ee4-105">Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="98ee4-106">Os serviços de Federação do Active Directory (AD FS) não podem usar o Azure Active Directory (Azure AD) como um substituto para os controladores de domínio dos serviços de domínio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="98ee4-106">Active Directory Federation Services (AD FS) cannot use Azure Active Directory (Azure AD) as a substitute for Active Directory Domain Services (AD DS) domain controllers.</span></span> 
  
<span data-ttu-id="98ee4-107">Você deve concluir essa fase antes de passar para a [fase 3: configurar servidores do AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span><span class="sxs-lookup"><span data-stu-id="98ee4-107">You must complete this phase before moving on to [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="98ee4-108">Consulte [implantar a autenticação federada de alta disponibilidade para o Microsoft 365 no Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.</span><span class="sxs-lookup"><span data-stu-id="98ee4-108">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="98ee4-109">Criar máquinas virtuais de controlador de domínio no Azure</span><span class="sxs-lookup"><span data-stu-id="98ee4-109">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="98ee4-110">Em primeiro lugar, você precisa preencher a coluna **Nome da máquina virtual** da Tabela M e modificar tamanhos de máquina virtual, conforme necessário, na coluna **Tamanho mínimo**.</span><span class="sxs-lookup"><span data-stu-id="98ee4-110">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="98ee4-111">**Item**</span><span class="sxs-lookup"><span data-stu-id="98ee4-111">**Item**</span></span>|<span data-ttu-id="98ee4-112">**Nome da máquina virtual**</span><span class="sxs-lookup"><span data-stu-id="98ee4-112">**Virtual machine name**</span></span>|<span data-ttu-id="98ee4-113">**Imagem da galeria**</span><span class="sxs-lookup"><span data-stu-id="98ee4-113">**Gallery image**</span></span>|<span data-ttu-id="98ee4-114">**Tipo de armazenamento**</span><span class="sxs-lookup"><span data-stu-id="98ee4-114">**Storage type**</span></span>|<span data-ttu-id="98ee4-115">**Tamanho mínimo**</span><span class="sxs-lookup"><span data-stu-id="98ee4-115">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="98ee4-116">1.</span><span class="sxs-lookup"><span data-stu-id="98ee4-116">1.</span></span>  <br/> |![linha](./media/Common-Images/TableLine.png) <span data-ttu-id="98ee4-118"> (primeiro controlador de domínio, DC1 de exemplo)</span><span class="sxs-lookup"><span data-stu-id="98ee4-118">(first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="98ee4-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="98ee4-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="98ee4-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="98ee4-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="98ee4-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="98ee4-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="98ee4-122">2.</span><span class="sxs-lookup"><span data-stu-id="98ee4-122">2.</span></span>  <br/> |![linha](./media/Common-Images/TableLine.png) <span data-ttu-id="98ee4-124"> (segundo controlador de domínio, DC2 de exemplo)</span><span class="sxs-lookup"><span data-stu-id="98ee4-124">(second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="98ee4-125">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="98ee4-125">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="98ee4-126">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="98ee4-126">Standard_LRS</span></span>  <br/> |<span data-ttu-id="98ee4-127">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="98ee4-127">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="98ee4-128">3.</span><span class="sxs-lookup"><span data-stu-id="98ee4-128">3.</span></span>  <br/> |![linha](./media/Common-Images/TableLine.png) <span data-ttu-id="98ee4-130">(servidor de sincronização de diretório, exemplo DS1)</span><span class="sxs-lookup"><span data-stu-id="98ee4-130">(directory synchronization server, example DS1)</span></span>  <br/> |<span data-ttu-id="98ee4-131">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="98ee4-131">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="98ee4-132">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="98ee4-132">Standard_LRS</span></span>  <br/> |<span data-ttu-id="98ee4-133">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="98ee4-133">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="98ee4-134">4.</span><span class="sxs-lookup"><span data-stu-id="98ee4-134">4.</span></span>  <br/> |![linha](./media/Common-Images/TableLine.png) <span data-ttu-id="98ee4-136">(primeiro servidor AD FS, exemplo ADFS1)</span><span class="sxs-lookup"><span data-stu-id="98ee4-136">(first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="98ee4-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="98ee4-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="98ee4-138">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="98ee4-138">Standard_LRS</span></span>  <br/> |<span data-ttu-id="98ee4-139">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="98ee4-139">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="98ee4-140">5.</span><span class="sxs-lookup"><span data-stu-id="98ee4-140">5.</span></span>  <br/> |![linha](./media/Common-Images/TableLine.png) <span data-ttu-id="98ee4-142">(segundo servidor AD FS, exemplo ADFS2)</span><span class="sxs-lookup"><span data-stu-id="98ee4-142">(second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="98ee4-143">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="98ee4-143">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="98ee4-144">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="98ee4-144">Standard_LRS</span></span>  <br/> |<span data-ttu-id="98ee4-145">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="98ee4-145">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="98ee4-146">6.</span><span class="sxs-lookup"><span data-stu-id="98ee4-146">6.</span></span>  <br/> |![linha](./media/Common-Images/TableLine.png) <span data-ttu-id="98ee4-148">(primeiro servidor de proxy de aplicativo Web, exemplo WEB1)</span><span class="sxs-lookup"><span data-stu-id="98ee4-148">(first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="98ee4-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="98ee4-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="98ee4-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="98ee4-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="98ee4-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="98ee4-151">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="98ee4-152">7.</span><span class="sxs-lookup"><span data-stu-id="98ee4-152">7.</span></span>  <br/> |![linha](./media/Common-Images/TableLine.png) <span data-ttu-id="98ee4-154">(segundo servidor de proxy de aplicativo Web, exemplo WEB2)</span><span class="sxs-lookup"><span data-stu-id="98ee4-154">(second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="98ee4-155">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="98ee4-155">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="98ee4-156">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="98ee4-156">Standard_LRS</span></span>  <br/> |<span data-ttu-id="98ee4-157">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="98ee4-157">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="98ee4-158">**Tabela M-máquinas virtuais para a autenticação federada de alta disponibilidade para o Microsoft 365 no Azure**</span><span class="sxs-lookup"><span data-stu-id="98ee4-158">**Table M - Virtual machines for the high availability federated authentication for Microsoft 365 in Azure**</span></span>
  
<span data-ttu-id="98ee4-159">Para obter a lista completa de tamanhos de máquinas virtuais, confira [Tamanhos das máquinas virtuais](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="98ee4-159">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="98ee4-160">O seguinte bloco de comandos do Azure PowerShell cria as máquinas virtuais para os dois controladores de domínio.</span><span class="sxs-lookup"><span data-stu-id="98ee4-160">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="98ee4-161">Especifique os valores para as variáveis, removendo os \< and > caracteres.</span><span class="sxs-lookup"><span data-stu-id="98ee4-161">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="98ee4-162">Observe que este bloco de comandos do Azure PowerShell usa valores para as tabelas a seguir:</span><span class="sxs-lookup"><span data-stu-id="98ee4-162">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="98ee4-163">Tabela M, para suas máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="98ee4-163">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="98ee4-164">Tabela R, para seus grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="98ee4-164">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="98ee4-165">Tabela V, para suas configurações de rede virtual</span><span class="sxs-lookup"><span data-stu-id="98ee4-165">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="98ee4-166">Tabela S, para suas sub-redes</span><span class="sxs-lookup"><span data-stu-id="98ee4-166">Table S, for your subnets</span></span>
    
- <span data-ttu-id="98ee4-167">Tabela I, para seu endereço IP estático</span><span class="sxs-lookup"><span data-stu-id="98ee4-167">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="98ee4-168">Tabela A, para seus conjuntos de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="98ee4-168">Table A, for your availability sets</span></span>
    
<span data-ttu-id="98ee4-169">Lembre-se de que você definiu as tabelas R, V, S, I e A na [fase 1: configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="98ee4-169">Recall that you defined Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="98ee4-170">[!OBSERVAçãO] O comando a seguir define o uso da versão mais recente do Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98ee4-170">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="98ee4-171">Confira [introdução ao PowerShell do Azure](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span><span class="sxs-lookup"><span data-stu-id="98ee4-171">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="98ee4-172">Quando tiver fornecido todos os valores corretos, execute o bloco resultante no prompt do Azure PowerShell ou no Ambiente de Script Integrado (ISE) do PowerShell no computador local.</span><span class="sxs-lookup"><span data-stu-id="98ee4-172">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="98ee4-173">Para gerar blocos de comando prontos para executar do PowerShell com base em suas configurações personalizadas, use esta [pasta de trabalho de configuração do Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span><span class="sxs-lookup"><span data-stu-id="98ee4-173">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="98ee4-174">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span><span class="sxs-lookup"><span data-stu-id="98ee4-174">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span></span> <span data-ttu-id="98ee4-175">However, this also means that you cannot connect to them from the Azure portal.</span><span class="sxs-lookup"><span data-stu-id="98ee4-175">However, this also means that you cannot connect to them from the Azure portal.</span></span> <span data-ttu-id="98ee4-176">The **Connect** option is unavailable when you view the properties of the virtual machine.</span><span class="sxs-lookup"><span data-stu-id="98ee4-176">The **Connect** option is unavailable when you view the properties of the virtual machine.</span></span> <span data-ttu-id="98ee4-177">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span><span class="sxs-lookup"><span data-stu-id="98ee4-177">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="98ee4-178">Configurar o primeiro controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="98ee4-178">Configure the first domain controller</span></span>

<span data-ttu-id="98ee4-179">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine.</span><span class="sxs-lookup"><span data-stu-id="98ee4-179">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine.</span></span> <span data-ttu-id="98ee4-180">Use its intranet DNS or computer name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="98ee4-180">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="98ee4-181">Em seguida, adicione o disco de dados extra ao primeiro controlador de domínio com esse comando a partir de um prompt de comando do Windows PowerShell **na primeira máquina virtual do controlador de domínio**:</span><span class="sxs-lookup"><span data-stu-id="98ee4-181">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="98ee4-182">Em seguida, teste a conectividade do primeiro controlador de domínio com os locais na rede da sua organização usando o comando **ping** para executar ping em nomes e endereços IP de recursos nessa rede.</span><span class="sxs-lookup"><span data-stu-id="98ee4-182">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="98ee4-183">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network.</span><span class="sxs-lookup"><span data-stu-id="98ee4-183">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network.</span></span> <span data-ttu-id="98ee4-184">If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span><span class="sxs-lookup"><span data-stu-id="98ee4-184">If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="98ee4-185">Em seguida, no prompt de comandos do Windows PowerShell no primeiro controlador de domínio, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="98ee4-185">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="98ee4-186">You will be prompted to supply the credentials of a domain administrator account.</span><span class="sxs-lookup"><span data-stu-id="98ee4-186">You will be prompted to supply the credentials of a domain administrator account.</span></span> <span data-ttu-id="98ee4-187">The computer will restart.</span><span class="sxs-lookup"><span data-stu-id="98ee4-187">The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="98ee4-188">Configurar o segundo controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="98ee4-188">Configure the second domain controller</span></span>

<span data-ttu-id="98ee4-189">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine.</span><span class="sxs-lookup"><span data-stu-id="98ee4-189">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine.</span></span> <span data-ttu-id="98ee4-190">Use its intranet DNS or computer name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="98ee4-190">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="98ee4-191">Em seguida, você precisa adicionar o disco de dados extra ao segundo controlador de domínio com esse comando a partir de um prompt de comando do Windows PowerShell **na segunda máquina virtual de controlador de domínio**:</span><span class="sxs-lookup"><span data-stu-id="98ee4-191">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="98ee4-192">Em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="98ee4-192">Next, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="98ee4-193">You will be prompted to supply the credentials of a domain administrator account.</span><span class="sxs-lookup"><span data-stu-id="98ee4-193">You will be prompted to supply the credentials of a domain administrator account.</span></span> <span data-ttu-id="98ee4-194">The computer will restart.</span><span class="sxs-lookup"><span data-stu-id="98ee4-194">The computer will restart.</span></span>
  
<span data-ttu-id="98ee4-195">Em seguida, você precisará atualizar os servidores DNS da sua rede virtual, para que o Azure atribua máquinas virtuais aos endereços IP dos dois novos controladores de domínio para uso como seus servidores DNS.</span><span class="sxs-lookup"><span data-stu-id="98ee4-195">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="98ee4-196">Preencha as variáveis e, em seguida, execute esses comandos em um prompt de comando do Windows PowerShell no computador local:</span><span class="sxs-lookup"><span data-stu-id="98ee4-196">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="98ee4-197">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers.</span><span class="sxs-lookup"><span data-stu-id="98ee4-197">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers.</span></span> <span data-ttu-id="98ee4-198">Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span><span class="sxs-lookup"><span data-stu-id="98ee4-198">Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="98ee4-199">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers.</span><span class="sxs-lookup"><span data-stu-id="98ee4-199">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers.</span></span> <span data-ttu-id="98ee4-200">Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span><span class="sxs-lookup"><span data-stu-id="98ee4-200">Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a><span data-ttu-id="98ee4-201">Configurar o servidor de sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="98ee4-201">Configure the directory synchronization server</span></span>

<span data-ttu-id="98ee4-202">Use o cliente de área de trabalho remota de sua preferência e crie uma conexão de área de trabalho remota com a máquina virtual do servidor de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="98ee4-202">Use the remote desktop client of your choice and create a remote desktop connection to the directory synchronization server virtual machine.</span></span> <span data-ttu-id="98ee4-203">Use seu nome de computador ou DNS de intranet e as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="98ee4-203">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="98ee4-204">Em seguida, ingresse-o no domínio do AD DS apropriado com estes comandos no prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98ee4-204">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="98ee4-205">Veja a seguir a configuração resultante da conclusão bem-sucedida dessa fase, com nomes de computador de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="98ee4-205">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="98ee4-206">**Fase 2: os controladores de domínio e o servidor de sincronização de diretório para a infraestrutura de autenticação federada de alta disponibilidade no Azure**</span><span class="sxs-lookup"><span data-stu-id="98ee4-206">**Phase 2: The domain controllers and directory synchronization server for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 2 da infraestrutura de autenticação federada de alta disponibilidade da Microsoft 365 no Azure com controladores de domínio](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="98ee4-208">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="98ee4-208">Next step</span></span>

<span data-ttu-id="98ee4-209">Use a [fase 3: configurar servidores do AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) para continuar Configurando essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="98ee4-209">Use [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98ee4-210">Confira também</span><span class="sxs-lookup"><span data-stu-id="98ee4-210">See Also</span></span>

[<span data-ttu-id="98ee4-211">Implantar a autenticação federada de alta disponibilidade para o Microsoft 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="98ee4-211">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="98ee4-212">Identidade federada para seu ambiente de desenvolvimento/teste do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="98ee4-212">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="98ee4-213">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="98ee4-213">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)


