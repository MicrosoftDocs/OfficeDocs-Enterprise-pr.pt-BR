---
title: "Ambiente de desenvolvimento e teste de configuração de base"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Resumo: Crie uma intranet simplificada como um ambiente de desenvolvimento e teste in Microsoft Azure.'
ms.openlocfilehash: f61490ea9ee9ee23df2b2fd13df1097d183a8de7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="0eb98-103">Ambiente de desenvolvimento e teste de configuração de base</span><span class="sxs-lookup"><span data-stu-id="0eb98-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="0eb98-104">**Resumo:** Crie uma intranet simplificada como um ambiente de desenvolvimento e teste in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="0eb98-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="0eb98-105">Este artigo fornece instruções passo a passo para criar o ambiente de desenvolvimento e teste de configuração básica seguinte no Windows Azure:</span><span class="sxs-lookup"><span data-stu-id="0eb98-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
<span data-ttu-id="0eb98-106">**Figura 1: Ambiente de desenvolvimento e teste a configuração básica**</span><span class="sxs-lookup"><span data-stu-id="0eb98-106">**Figure 1: The Base Configuration dev/test environment**</span></span>

![Fase 4 da Configuração Básica no Azure com a máquina virtual CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="0eb98-p101">O ambiente de desenvolvimento e teste de configuração básica na Figura 1 consiste de subnet Corpnet uma somente em nuvem rede virtual do Azure chamada de laboratório de teste que simule uma intranet simplificada, privada conectada à Internet. Ele contém três máquinas virtuais do Azure executando o Windows Server 2016:</span><span class="sxs-lookup"><span data-stu-id="0eb98-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="0eb98-110">DC1 está configurado como um controlador de domínio da intranet e o servidor de sistema de nome de domínio (DNS)</span><span class="sxs-lookup"><span data-stu-id="0eb98-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="0eb98-111">App1 esteja configurado como um servidor de aplicativos e web geral</span><span class="sxs-lookup"><span data-stu-id="0eb98-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="0eb98-112">CLIENT1 atua como um cliente de intranet</span><span class="sxs-lookup"><span data-stu-id="0eb98-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="0eb98-113">Essa configuração permite DC1, APP1, CLIENT1 e outros computadores da sub-rede Corpnet ser:</span><span class="sxs-lookup"><span data-stu-id="0eb98-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="0eb98-114">Conectado à Internet para instalar as atualizações, acessar os recursos da Internet em tempo real e participar de tecnologias de nuvem pública, como o Microsoft Office 365 e outros serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="0eb98-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="0eb98-115">Gerenciar remotamente usando conexões de área de trabalho remota do seu computador que está conectado à Internet ou à rede da organização.</span><span class="sxs-lookup"><span data-stu-id="0eb98-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="0eb98-116">Você pode usar o ambiente de teste resultante:</span><span class="sxs-lookup"><span data-stu-id="0eb98-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="0eb98-117">Para o desenvolvimento de aplicativos e testes.</span><span class="sxs-lookup"><span data-stu-id="0eb98-117">For application development and testing.</span></span>
    
- <span data-ttu-id="0eb98-118">Como a configuração inicial de um ambiente de teste estendido de seu próprio design que inclui outras máquinas virtuais, serviços do Azure ou outras ofertas de nuvem da Microsoft, como o Office 365 + mobilidade e segurança da empresa.</span><span class="sxs-lookup"><span data-stu-id="0eb98-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility.</span></span>
    
<span data-ttu-id="0eb98-119">Há quatro fases para configurar o ambiente de teste de configuração básica no Windows Azure:</span><span class="sxs-lookup"><span data-stu-id="0eb98-119">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="0eb98-120">Crie a rede virtual.</span><span class="sxs-lookup"><span data-stu-id="0eb98-120">Create the virtual network.</span></span>
    
2. <span data-ttu-id="0eb98-121">Configure o DC1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-121">Configure DC1.</span></span>
    
3. <span data-ttu-id="0eb98-122">Configure APP1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-122">Configure APP1.</span></span>
    
4. <span data-ttu-id="0eb98-123">Definir CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-123">Configure CLIENT1.</span></span>
    
<span data-ttu-id="0eb98-p102">Se você ainda não tiver uma assinatura do Windows Azure, você pode se inscrever para uma avaliação gratuita no [Azure tente](https://azure.microsoft.com/pricing/free-trial/). Se você tiver uma assinatura do MSDN ou o Visual Studio, consulte [crédito Azure mensal para assinantes do Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="0eb98-p102">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0eb98-p103">Máquinas virtuais do Azure incorrer em um custo monetário em andamento quando eles estão em execução. Esse custo é cobrado em relação a sua assinatura do MSDN de avaliação, livre ou assinatura paga. Para obter mais informações sobre os custos da execução de máquinas virtuais do Azure, consulte [Detalhes de preços de máquinas virtuais](https://azure.microsoft.com/pricing/details/virtual-machines/) e [Calculadora de preços do Azure](https://azure.microsoft.com/pricing/calculator/). Para reduzir os custos, consulte [minimizar os custos de máquinas virtuais do teste ambiente no Windows Azure](base-configuration-dev-test-environment.md#mincost).</span><span class="sxs-lookup"><span data-stu-id="0eb98-p103">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Guias do Laboratório de Teste da Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="0eb98-131">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="0eb98-131">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-virtual-network"></a><span data-ttu-id="0eb98-132">Fase 1: Criar a rede virtual</span><span class="sxs-lookup"><span data-stu-id="0eb98-132">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="0eb98-133">Em primeiro lugar, inicie um prompt do Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0eb98-133">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0eb98-p104">O comando a seguir define usar a versão mais recente do Azure PowerShell. Consulte a [Introdução ao cmdlets do PowerShell do Windows Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="0eb98-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="0eb98-136">Inscreva-se à sua conta do Windows Azure com o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="0eb98-136">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="0eb98-137">Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) para obter um arquivo de texto que contém todos os comandos do PowerShell neste artigo.</span><span class="sxs-lookup"><span data-stu-id="0eb98-137">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="0eb98-138">Para obter o nome de sua assinatura, use este comando.</span><span class="sxs-lookup"><span data-stu-id="0eb98-138">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="0eb98-p105">Defina sua assinatura do Azure. Substitua tudo o que está entre aspas, incluindo os caracteres < e >, pelo nome correto.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p105">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="0eb98-p106">Em seguida, crie um novo grupo de recursos para o seu laboratório de teste de configuração básica. Para determinar o nome de um grupo de recursos exclusivos, use este comando para listar os grupos de recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p106">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="0eb98-p107">Crie seu novo grupo de recursos com esses comandos. Substituir tudo entre aspas, incluindo o < e > caracteres, com os nomes corretos.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p107">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="0eb98-145">Em seguida, crie a rede virtual do laboratório de teste que hospedará a sub-rede Corpnet da configuração básica e protegê-lo com um grupo de segurança de rede.</span><span class="sxs-lookup"><span data-stu-id="0eb98-145">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="0eb98-146">Esta é a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="0eb98-146">This is your current configuration.</span></span>
  
![Fase 1 da Configuração Básica no Azure com sub-rede e rede virtuais](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a><span data-ttu-id="0eb98-148">Fase 2: Configurar DC1</span><span class="sxs-lookup"><span data-stu-id="0eb98-148">Phase 2: Configure DC1</span></span>

<span data-ttu-id="0eb98-149">Nesta fase, criamos máquina virtual DC1 e configurá-lo como um controlador de domínio para o domínio do Windows Server Active Directory (AD) corp.contoso.com e um servidor DNS para as máquinas virtuais da rede virtual laboratório de teste.</span><span class="sxs-lookup"><span data-stu-id="0eb98-149">In this phase, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>
  
<span data-ttu-id="0eb98-150">Para criar uma máquina virtual do Azure para DC1, no nome de seu grupo de recursos de preenchimento e executar esses comandos no prompt de comando do PowerShell do Azure no computador local.</span><span class="sxs-lookup"><span data-stu-id="0eb98-150">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="0eb98-p108">Você será solicitado para um nome de usuário e senha para a conta de administrador local no DC1. Use uma senha forte e registre o nome e a senha em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p108">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="0eb98-153">Em seguida, conecte-se à máquina virtual DC1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-153">Next, connect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a><span data-ttu-id="0eb98-154">Conectar-se ao DC1 usando credenciais de conta de administrador local</span><span class="sxs-lookup"><span data-stu-id="0eb98-154">Connect to DC1 using local administrator account credentials</span></span>

1. <span data-ttu-id="0eb98-155">No [portal do Azure](https://portal.azure.com), clique em **grupos de recursos >** <the name of your new resource group> **> DC1 > conectar**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-155">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** <the name of your new resource group> **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="0eb98-156">Abra o arquivo de DC1.rdp que é baixado e, em seguida, clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-156">Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="0eb98-157">Especifique o nome de conta de administrador local DC1:</span><span class="sxs-lookup"><span data-stu-id="0eb98-157">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="0eb98-158">Para Windows 7:</span><span class="sxs-lookup"><span data-stu-id="0eb98-158">For Windows 7:</span></span>
    
    <span data-ttu-id="0eb98-p109">Na caixa de diálogo **Segurança do Windows** , clique em **usar outra conta**. Em **nome de usuário**, digite **DC1\\**[nome de conta de Administrador Local].</span><span class="sxs-lookup"><span data-stu-id="0eb98-p109">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="0eb98-161">Para o Windows 8 ou Windows 10:</span><span class="sxs-lookup"><span data-stu-id="0eb98-161">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="0eb98-p110">Na caixa de diálogo **Segurança do Windows** , clique em **mais opções**e, em seguida, clique em **usar uma conta diferente**. Em **nome de usuário**, digite **DC1\\**[nome de conta de Administrador Local].</span><span class="sxs-lookup"><span data-stu-id="0eb98-p110">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="0eb98-164">Em **senha**, digite a senha da conta de administrador local e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-164">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="0eb98-165">Quando solicitado, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-165">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="0eb98-166">Em seguida, adicione um disco de dados extras como um novo volume com a letra da unidade f: com este comando em um prompt de comando do Windows PowerShell de nível de administrador no DC1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-166">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="0eb98-p111">Em seguida, configure DC1 como um controlador de domínio e o servidor DNS para o domínio corp.contoso.com. Execute estes comandos em um prompt de comando do Windows PowerShell de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p111">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs"
```

<span data-ttu-id="0eb98-p112">Você precisará especificar uma senha de administrador do modo de segurança. Armazene esta senha em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p112">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="0eb98-171">Esses comandos podem levar alguns minutos para serem concluídos.</span><span class="sxs-lookup"><span data-stu-id="0eb98-171">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="0eb98-172">Após a reinicialização do DC1, reconecte à máquina virtual DC1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-172">After DC1 restarts, reconnect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-domain-credentials"></a><span data-ttu-id="0eb98-173">Conectar-se ao DC1 usando credenciais de domínio</span><span class="sxs-lookup"><span data-stu-id="0eb98-173">Connect to DC1 using domain credentials</span></span>

1. <span data-ttu-id="0eb98-174">No [portal do Azure](https://portal.azure.com), clique em **grupos de recursos >** <your resource group name> **> DC1 > conectar**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-174">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** <your resource group name> **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="0eb98-175">Execute o arquivo DC1.rdp que é baixado e, em seguida, clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-175">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="0eb98-p113">Na **Segurança do Windows**, clique em **usar outra conta**. Em **nome de usuário**, digite **CORP\\**[nome de conta de Administrador Local].</span><span class="sxs-lookup"><span data-stu-id="0eb98-p113">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="0eb98-178">Em **senha**, digite a senha da conta de administrador local e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-178">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="0eb98-179">Quando solicitado, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-179">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="0eb98-p114">Em seguida, crie uma conta de usuário no Active Directory que será usada ao fazer logon no computador de membro de domínio CORP. Execute este comando em um prompt de comando do Windows PowerShell de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p114">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="0eb98-p115">Observe que este comando solicitará que você forneça a senha da conta User1. Como essa conta será usada para conexões de área de trabalho remotas para todos os computadores de membro de domínio CORP, escolha uma senha forte. Registre a senha da conta User1 e armazená-lo em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p115">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="0eb98-p116">Em seguida, configure a nova conta User1 como um administrador da empresa. Execute este comando no prompt de comando do Windows PowerShell nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p116">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="0eb98-187">Fechar a sessão de área de trabalho remota com DC1 e depois reconectar usando CORP\\conta User1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-187">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="0eb98-188">Em seguida, para permitir o tráfego para a ferramenta de Ping, execute este comando em um prompt de comando do Windows PowerShell de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="0eb98-188">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="0eb98-189">Esta é a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="0eb98-189">This is your current configuration.</span></span>
  
![Fase 2 da Configuração Básica no Azure com a máquina virtual DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a><span data-ttu-id="0eb98-191">Fase 3: Configurar APP1</span><span class="sxs-lookup"><span data-stu-id="0eb98-191">Phase 3: Configure APP1</span></span>

<span data-ttu-id="0eb98-192">App1 fornece web e serviços de compartilhamento de arquivo.</span><span class="sxs-lookup"><span data-stu-id="0eb98-192">APP1 provides web and file sharing services.</span></span>
  
<span data-ttu-id="0eb98-193">Para criar uma máquina Virtual de Windows Azure para APP1, preencher no nome de seu grupo de recursos, Azure local e nome da conta de armazenamento e executar esses comandos no prompt de comando do PowerShell do Azure no computador local.</span><span class="sxs-lookup"><span data-stu-id="0eb98-193">To create an Azure Virtual Machine for APP1, fill in the name of your resource group, Azure location, and storage account name and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="0eb98-194">Em seguida, conecte-se à máquina virtual APP1 usando a APP1 nome da conta de administrador local e a senha e, em seguida, abra um prompt de comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0eb98-194">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="0eb98-195">Para verificar a comunicação de rede e resolução de nome entre APP1 e DC1, execute o comando **ping dc1.corp.contoso.com** e verifique se há quatro respostas.</span><span class="sxs-lookup"><span data-stu-id="0eb98-195">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="0eb98-196">Em seguida, ingresse máquina virtual APP1 no domínio CORP com esses comandos no prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0eb98-196">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="0eb98-197">Observe que você deve fornecer o CORP\\User1 credenciais de conta de domínio após executar o comando **Add-Computer** .</span><span class="sxs-lookup"><span data-stu-id="0eb98-197">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="0eb98-198">Após a reinicialização do APP1, conectá-lo usando o CORP\\conta User1 e, então, abra um nível de administrador Windows PowerShell prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0eb98-198">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="0eb98-199">Em seguida, verifique APP1 um servidor da web com este comando no prompt de comando do Windows PowerShell no APP1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-199">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="0eb98-200">Em seguida, crie uma pasta compartilhada e um arquivo de texto dentro da pasta no APP1 com esses comandos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0eb98-200">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\\files -type directory
Write-Output "This is a shared file." | out-file c:\\files\\example.txt
New-SmbShare -name files -path c:\\files -changeaccess CORP\\User1
```

<span data-ttu-id="0eb98-201">Esta é a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="0eb98-201">This is your current configuration.</span></span>
  
![Fase 3 da Configuração Básica no Azure com a máquina virtual APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a><span data-ttu-id="0eb98-203">Fase 4: Configurar CLIENT1</span><span class="sxs-lookup"><span data-stu-id="0eb98-203">Phase 4: Configure CLIENT1</span></span>

<span data-ttu-id="0eb98-204">CLIENT1 atua como um laptop típica, tablet ou computador desktop na intranet da Contoso.</span><span class="sxs-lookup"><span data-stu-id="0eb98-204">CLIENT1 acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0eb98-p117">O conjunto de comandos a seguir cria CLIENT1 executando o Windows Server 2016 Datacenter, que pode ser feito para todos os tipos de inscrições do Azure. Se você tiver uma assinatura do Windows Azure baseados no Visual Studio, você pode criar CLIENT1 executando Windows 10, Windows 8 ou Windows 7 com o [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="0eb98-p117">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10, Windows 8, or Windows 7 with the [Azure portal](https://portal.azure.com).</span></span> 
  
<span data-ttu-id="0eb98-207">Para criar uma máquina Virtual de Windows Azure para CLIENT1, preencher no nome de seu grupo de recursos, Azure local e nome da conta de armazenamento e executar esses comandos no prompt de comando do PowerShell do Azure no computador local.</span><span class="sxs-lookup"><span data-stu-id="0eb98-207">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group, Azure location, and storage account name and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="0eb98-208">Em seguida, conecte-se à máquina virtual CLIENT1 usando a CLIENT1 nome da conta de administrador local e a senha e, em seguida, abra um prompt de comando do Windows PowerShell de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="0eb98-208">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="0eb98-209">Para verificar a comunicação de rede e resolução de nome entre CLIENT1 e DC1, execute o comando **ping dc1.corp.contoso.com** em um prompt de comando do Windows PowerShell e verifique se há quatro respostas.</span><span class="sxs-lookup"><span data-stu-id="0eb98-209">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="0eb98-210">Em seguida, ingresse a máquina virtual CLIENT1 no domínio CORP com esses comandos no prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0eb98-210">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="0eb98-211">Observe que você deve fornecer sua CORP\\User1 credenciais de conta de domínio após executar o comando **Add-Computer** .</span><span class="sxs-lookup"><span data-stu-id="0eb98-211">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="0eb98-212">Após a reinicialização do CLIENT1, conecte-se a ela usando o CORP\\Usuário1 nome e a senha da conta e, em seguida, abra um prompt de comando do Windows PowerShell de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="0eb98-212">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="0eb98-213">Em seguida, verifique se que você pode acessar os recursos de compartilhamento de arquivo e web no APP1 do CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-213">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
### <a name="verify-client-access-to-app1"></a><span data-ttu-id="0eb98-214">Verificar o acesso de cliente App1</span><span class="sxs-lookup"><span data-stu-id="0eb98-214">Verify CLIENT access to APP1</span></span>

1. <span data-ttu-id="0eb98-215">No Gerenciador de servidores, no painel de árvore, clique em **Servidor Local**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-215">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="0eb98-216">Em **Propriedades para CLIENT1**, clique **em** ao lado de **Configuração de segurança reforçada do Internet Explorer**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-216">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="0eb98-217">**A configuração de segurança reforçada do Internet Explorer**, clique em **Desativar** para **administradores** e **usuários**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-217">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="0eb98-218">Na tela Iniciar, clique em **Internet Explorer**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0eb98-218">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="0eb98-p118">Na barra endereço, digite **http://app1.corp.contoso.com/**e pressione ENTER. Você deverá ver uma página da web padrão do Internet Information Services para APP1.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p118">In the Address bar, type **http://app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="0eb98-221">Na barra de tarefas da área de trabalho, clique no ícone do Gerenciador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="0eb98-221">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="0eb98-p119">Na barra de endereços, digite ** \\ \\app1\\arquivos**, e pressione ENTER. Você deverá ver uma janela de pasta com o conteúdo da pasta compartilhada de arquivos.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p119">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="0eb98-p120">Na janela de pasta compartilhada de **arquivos** , clique duas vezes no arquivo **txt** . Você deverá ver o conteúdo do arquivo txt.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p120">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="0eb98-226">Feche o **txt - o bloco de notas** e as janelas da pasta de **arquivos** compartilhados.</span><span class="sxs-lookup"><span data-stu-id="0eb98-226">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="0eb98-227">Esta é a configuração final.</span><span class="sxs-lookup"><span data-stu-id="0eb98-227">This is your final configuration.</span></span>
  
![Fase 4 da Configuração Básica no Azure com a máquina virtual CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="0eb98-229">A configuração de Base no Windows Azure agora está pronta para teste e desenvolvimento de aplicativos ou para a criação de ambientes de teste adicionais.</span><span class="sxs-lookup"><span data-stu-id="0eb98-229">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="0eb98-230">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="0eb98-230">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="0eb98-231">Minimizar os custos de máquinas virtuais do teste ambiente no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="0eb98-231">Minimizing the costs of test environment virtual machines in Azure</span></span>
<span data-ttu-id="0eb98-232"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="0eb98-232"></span></span>

<span data-ttu-id="0eb98-233">Para minimizar o custo de execução máquinas virtuais do ambiente de teste, siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="0eb98-233">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="0eb98-p121">Criar o ambiente de teste e execute seus testes necessários e demonstração mais depressa possível. Quando concluir, exclua o grupo de recursos para o ambiente de teste.</span><span class="sxs-lookup"><span data-stu-id="0eb98-p121">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="0eb98-236">Desligue suas máquinas de virtuais do ambiente de teste em um estado de liberada.</span><span class="sxs-lookup"><span data-stu-id="0eb98-236">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="0eb98-237">Para encerrar as máquinas virtuais com o Azure PowerShell, preencha o nome do grupo de recursos e executar esses comandos.</span><span class="sxs-lookup"><span data-stu-id="0eb98-237">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="0eb98-238">Para garantir que suas máquinas virtuais funcionam corretamente ao iniciar todos eles do estado de parado (Deallocated), você deve iniciá-los na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="0eb98-238">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="0eb98-239">DC1</span><span class="sxs-lookup"><span data-stu-id="0eb98-239">DC1</span></span>
    
2. <span data-ttu-id="0eb98-240">APP1</span><span class="sxs-lookup"><span data-stu-id="0eb98-240">APP1</span></span>
    
3. <span data-ttu-id="0eb98-241">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="0eb98-241">CLIENT1</span></span>
    
<span data-ttu-id="0eb98-242">Para iniciar as máquinas virtuais em ordem com o Azure PowerShell, preencha o nome do grupo de recursos e executar esses comandos.</span><span class="sxs-lookup"><span data-stu-id="0eb98-242">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="0eb98-243">Veja também</span><span class="sxs-lookup"><span data-stu-id="0eb98-243">See Also</span></span>

<span data-ttu-id="0eb98-244"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="0eb98-244"></span></span>

[<span data-ttu-id="0eb98-245">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb98-245">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="0eb98-246">DirSync para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb98-246">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="0eb98-247">Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb98-247">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="0eb98-248">Proteção de ameaça avançada para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb98-248">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="0eb98-249">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="0eb98-249">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


