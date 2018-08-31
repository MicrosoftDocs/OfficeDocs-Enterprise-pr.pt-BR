---
title: Alta disponibilidade federado controladores de domínio de fase 2 Configurar autenticação
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Resumo: Configure os controladores de domínio e o servidor DirSync para a sua autenticação federada de alta disponibilidade para o Office 365 no Microsoft Azure.'
ms.openlocfilehash: 1e66403348bc2cd9a6dfab56f32735d62c986035
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915146"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="e87e9-103">Autenticação federada de alta disponibilidade Fase 2: Configurar controladores de domínio</span><span class="sxs-lookup"><span data-stu-id="e87e9-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="e87e9-104">**Resumo:** Configure os controladores de domínio e o servidor DirSync para a sua autenticação federada de alta disponibilidade para o Office 365 no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e87e9-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="e87e9-p101">Nessa fase de implantação da alta disponibilidade para a autenticação federada do Office 365 nos serviços de infraestrutura do Azure, você configurará dois controladores de domínio e o servidor DirSync na rede virtual do Azure. Solicitações da Web de clientes para autenticação podem então ser autenticadas na rede virtual do Azure, em vez de o tráfego de autenticação ser enviado na conexão de VPN site a site à sua rede local.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e87e9-107">Os Serviços de Federação do Active Directory (AD FS) não podem usar o Azure Active Directory Domain Services como substituto para controladores de domínio do Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="e87e9-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Windows Server AD domain controllers.</span></span> 
  
<span data-ttu-id="e87e9-p102">Você deve concluir esta fase antes de mover o logon em [alta disponibilidade federado autenticação fase 3: configurar os servidores AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p102">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="e87e9-110">Criar máquinas virtuais de controlador de domínio no Azure</span><span class="sxs-lookup"><span data-stu-id="e87e9-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="e87e9-111">Em primeiro lugar, você precisa preencher a coluna **Nome da máquina virtual** da Tabela M e modificar tamanhos de máquina virtual, conforme necessário, na coluna **Tamanho mínimo**.</span><span class="sxs-lookup"><span data-stu-id="e87e9-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="e87e9-112">**Item**</span><span class="sxs-lookup"><span data-stu-id="e87e9-112">**Item**</span></span>|<span data-ttu-id="e87e9-113">**Nome da máquina virtual**</span><span class="sxs-lookup"><span data-stu-id="e87e9-113">**Virtual machine name**</span></span>|<span data-ttu-id="e87e9-114">**Imagem da galeria**</span><span class="sxs-lookup"><span data-stu-id="e87e9-114">**Gallery image**</span></span>|<span data-ttu-id="e87e9-115">**Tipo de armazenamento**</span><span class="sxs-lookup"><span data-stu-id="e87e9-115">**Storage type**</span></span>|<span data-ttu-id="e87e9-116">**Tamanho mínimo**</span><span class="sxs-lookup"><span data-stu-id="e87e9-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="e87e9-117">1.</span><span class="sxs-lookup"><span data-stu-id="e87e9-117">1.</span></span>  <br/> |<span data-ttu-id="e87e9-118">![](./media/Common-Images/TableLine.png) (primeiro controlador de domínio, DC1 de exemplo)</span><span class="sxs-lookup"><span data-stu-id="e87e9-118">![](./media/Common-Images/TableLine.png) (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="e87e9-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e87e9-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e87e9-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e87e9-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e87e9-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e87e9-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e87e9-122">2.</span><span class="sxs-lookup"><span data-stu-id="e87e9-122">2.</span></span>  <br/> |<span data-ttu-id="e87e9-123">![](./media/Common-Images/TableLine.png) (segundo controlador de domínio, DC2 de exemplo)</span><span class="sxs-lookup"><span data-stu-id="e87e9-123">![](./media/Common-Images/TableLine.png) (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="e87e9-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e87e9-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e87e9-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e87e9-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e87e9-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e87e9-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e87e9-127">3.</span><span class="sxs-lookup"><span data-stu-id="e87e9-127">3.</span></span>  <br/> |<span data-ttu-id="e87e9-128">![](./media/Common-Images/TableLine.png)(Servidor DirSync, exemplo DS1)</span><span class="sxs-lookup"><span data-stu-id="e87e9-128">![](./media/Common-Images/TableLine.png) (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="e87e9-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e87e9-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e87e9-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e87e9-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e87e9-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e87e9-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e87e9-132">4.</span><span class="sxs-lookup"><span data-stu-id="e87e9-132">4.</span></span>  <br/> |<span data-ttu-id="e87e9-133">![](./media/Common-Images/TableLine.png)(servidor do AD FS primeiro, o exemplo ADFS1)</span><span class="sxs-lookup"><span data-stu-id="e87e9-133">![](./media/Common-Images/TableLine.png) (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="e87e9-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e87e9-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e87e9-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e87e9-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e87e9-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e87e9-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e87e9-137">5.</span><span class="sxs-lookup"><span data-stu-id="e87e9-137">5.</span></span>  <br/> |<span data-ttu-id="e87e9-138">![](./media/Common-Images/TableLine.png)(servidor do AD FS segundo, exemplo ADFS2)</span><span class="sxs-lookup"><span data-stu-id="e87e9-138">![](./media/Common-Images/TableLine.png) (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="e87e9-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e87e9-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e87e9-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e87e9-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e87e9-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e87e9-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e87e9-142">6.</span><span class="sxs-lookup"><span data-stu-id="e87e9-142">6.</span></span>  <br/> |<span data-ttu-id="e87e9-143">![](./media/Common-Images/TableLine.png)(primeiro web application proxy server, exemplo WEB1)</span><span class="sxs-lookup"><span data-stu-id="e87e9-143">![](./media/Common-Images/TableLine.png) (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="e87e9-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e87e9-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e87e9-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e87e9-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e87e9-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e87e9-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e87e9-147">7.</span><span class="sxs-lookup"><span data-stu-id="e87e9-147">7.</span></span>  <br/> |<span data-ttu-id="e87e9-148">![](./media/Common-Images/TableLine.png)(segunda web application proxy server, exemplo WEB2)</span><span class="sxs-lookup"><span data-stu-id="e87e9-148">![](./media/Common-Images/TableLine.png) (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="e87e9-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e87e9-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e87e9-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e87e9-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e87e9-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e87e9-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="e87e9-152">**Tabela M - máquinas virtuais para a autenticação federada de alta disponibilidade para o Office 365 no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="e87e9-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="e87e9-153">Para obter a lista completa de tamanhos de máquinas virtuais, confira [Tamanhos das máquinas virtuais](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="e87e9-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="e87e9-p103">O seguinte bloco de comando do Windows Azure PowerShell cria as máquinas virtuais para os controladores de dois domínio. Especifique os valores para as variáveis, removendo a \< e > caracteres. Observe que este bloco de comando do Windows Azure PowerShell usa valores das tabelas a seguir:</span><span class="sxs-lookup"><span data-stu-id="e87e9-p103">The following Azure PowerShell command block creates the virtual machines for the two domain controllers. Specify the values for the variables, removing the \< and > characters. Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="e87e9-157">Tabela M, para suas máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="e87e9-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="e87e9-158">Tabela R, para seus grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="e87e9-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="e87e9-159">Tabela V, para suas configurações de rede virtual</span><span class="sxs-lookup"><span data-stu-id="e87e9-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="e87e9-160">Tabela S, para suas sub-redes</span><span class="sxs-lookup"><span data-stu-id="e87e9-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="e87e9-161">Tabela I, para seu endereço IP estático</span><span class="sxs-lookup"><span data-stu-id="e87e9-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="e87e9-162">Tabela A, para seus conjuntos de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="e87e9-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="e87e9-163">Lembre-se de que você definiu tabelas R, V, S, I e A na [alta disponibilidade federado autenticação fase 1: configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="e87e9-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e87e9-p104">O comando a seguir define o uso da versão mais recente do Azure PowerShell. Confira [Introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="e87e9-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="e87e9-166">Quando tiver fornecido todos os valores corretos, execute o bloco resultante no prompt do Azure PowerShell ou no Ambiente de Script Integrado (ISE) do PowerShell no computador local.</span><span class="sxs-lookup"><span data-stu-id="e87e9-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="e87e9-167">Para um arquivo de texto que contém todos os comandos do PowerShell este artigo e uma pasta de trabalho de configuração Microsoft Excel que gera blocos de comando do PowerShell pronto para executar com base em suas configurações personalizadas, consulte o [autenticação federada para o Office 365 Kit de implantação do Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="e87e9-167">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="e87e9-p105">Como essas máquinas virtuais são para um aplicativo de intranet, não estão atribuídos a um endereço IP público ou um rótulo de nome de domínio DNS e expostos à Internet. No entanto, isso também significa que você não pode se conectar a eles do portal do Azure. A opção **Conectar** está disponível quando você exibe as propriedades da máquina virtual. Use o acessório de Conexão de área de trabalho remota ou outra ferramenta de área de trabalho remota para se conectar à máquina virtual usando o privada IP endereço ou intranet nome DNS.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="e87e9-172">Configurar o primeiro controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="e87e9-172">Configure the first domain controller</span></span>

<span data-ttu-id="e87e9-p106">Use o cliente de área de trabalho remota de sua preferência e crie uma conexão de área de trabalho remota com a primeira máquina virtual de controlador de domínio. Use seu nome de computador ou DNS de intranet e as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="e87e9-175">Em seguida, adicione o disco de dados extras para o primeiro controlador de domínio com este comando do Windows PowerShell prompt de comando **na máquina de virtual do primeira controlador de domínio**:</span><span class="sxs-lookup"><span data-stu-id="e87e9-175">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="e87e9-176">Em seguida, teste a conectividade do primeiro controlador de domínio com os locais na rede da sua organização usando o comando **ping** para executar ping em nomes e endereços IP de recursos nessa rede.</span><span class="sxs-lookup"><span data-stu-id="e87e9-176">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="e87e9-p107">Esse procedimento assegura que a resolução de nomes DNS esteja funcionando corretamente (que a máquina virtual esteja corretamente configurada com os servidores DNS locais) e que pacotes possam ser enviados de e para a rede virtual entre locais. Se esse teste básico falhar, entre em contato com seu departamento de TI para solucionar problemas de entrega de pacotes e resolução de nomes DNS.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="e87e9-179">Em seguida, no prompt de comandos do Windows PowerShell no primeiro controlador de domínio, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e87e9-179">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="e87e9-p108">Você será solicitado a fornecer as credenciais de uma conta de administrador de domínio. O computador será reiniciado.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="e87e9-182">Configurar o segundo controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="e87e9-182">Configure the second domain controller</span></span>

<span data-ttu-id="e87e9-p109">Use o cliente de área de trabalho remota de sua preferência e crie uma conexão de área de trabalho remota com a segunda máquina virtual de controlador de domínio. Use seu nome de computador ou DNS de intranet e as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="e87e9-185">Em seguida, você precisa adicionar o disco de dados adicionais para o segundo controlador de domínio com este comando de um Windows PowerShell prompt de comando **na máquina de virtual do segunda controlador de domínio**:</span><span class="sxs-lookup"><span data-stu-id="e87e9-185">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="e87e9-186">Em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e87e9-186">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="e87e9-p110">Você será solicitado a fornecer as credenciais de uma conta de administrador de domínio. O computador será reiniciado.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="e87e9-p111">Em seguida, você precisará atualizar os servidores DNS para sua rede virtual para que o Azure atribui máquinas virtuais os endereços IP dos dois novos controladores de domínio a ser usado como seus servidores DNS. Preencha as variáveis e, em seguida, executar esses comandos em um prompt de comando do Windows PowerShell no computador local:</span><span class="sxs-lookup"><span data-stu-id="e87e9-p111">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers. Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```
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

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="e87e9-p112">Observe que reiniciamos os dois controladores de domínio para que eles não sejam configurados com os servidores DNS locais como servidores DNS. Como ambos são servidores DNS, eles foram configurados automaticamente com os servidores DNS locais como encaminhadores de DNS quando foram promovidos para controladores de domínio.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="e87e9-p113">Em seguida, precisamos criar um site de replicação do Active Directory para garantir que os servidores na rede virtual do Azure usem os controladores de domínio locais. Conecte a um dos controlador de domínio com uma conta de administrador de domínio e execute os seguintes comandos em um prompt do Windows PowerShell em nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="e87e9-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="e87e9-195">Configurar o servidor DirSync</span><span class="sxs-lookup"><span data-stu-id="e87e9-195">Configure the DirSync server</span></span>

<span data-ttu-id="e87e9-p114">Use o cliente de desktop remoto de sua escolha e criar uma conexão da área de trabalho remota para a máquina do DirSync servidor virtual. Use seu nome de computador ou de DNS da intranet e as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="e87e9-p114">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="e87e9-198">Em seguida, associe-o ao domínio do AD apropriado do Windows Server com esses comandos no prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e87e9-198">Next, join it to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="e87e9-199">Veja a seguir a configuração resultante da conclusão bem-sucedida dessa fase, com nomes de computador de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="e87e9-199">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="e87e9-200">**Fase 2: Os controladores de domínio e o servidor DirSync para a sua infraestrutura de autenticação federada de alta disponibilidade no Azure**</span><span class="sxs-lookup"><span data-stu-id="e87e9-200">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 2 da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure com controladores de domínio](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="e87e9-202">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="e87e9-202">Next step</span></span>

<span data-ttu-id="e87e9-203">Use o [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) para continuar configurando essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e87e9-203">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e87e9-204">Confira também</span><span class="sxs-lookup"><span data-stu-id="e87e9-204">See Also</span></span>

[<span data-ttu-id="e87e9-205">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="e87e9-205">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="e87e9-206">Identidade federada para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e87e9-206">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e87e9-207">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="e87e9-207">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="e87e9-208">Opções de autenticação federada</span><span class="sxs-lookup"><span data-stu-id="e87e9-208">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


