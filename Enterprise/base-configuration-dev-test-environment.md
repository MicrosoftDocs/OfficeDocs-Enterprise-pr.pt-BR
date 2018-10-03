---
title: Ambiente de desenvolvimento/teste para a Configuração Base
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/01/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Resumo: Criar uma intranet simplificada como um ambiente de desenvolvimento/teste no Microsoft Azure.'
ms.openlocfilehash: 9ffa35a6318d83d489ec51051547ce22c16b5b5f
ms.sourcegitcommit: 9ce1da973b8c91b0926142a28c5b90f95f0422d8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "25353307"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="d5acb-103">Ambiente de desenvolvimento/teste para a Configuração Base</span><span class="sxs-lookup"><span data-stu-id="d5acb-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="d5acb-104">**Resumo:** Criar uma intranet simplificada como um ambiente de desenvolvimento/teste no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="d5acb-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="d5acb-105">Este artigo fornece instruções para criar o seguinte ambiente de desenvolvimento/teste para a Configuração Básica no Azure:</span><span class="sxs-lookup"><span data-stu-id="d5acb-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
![A configuração padrão no Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="d5acb-107">**Figura 1: Ambiente de desenvolvimento/teste da Configuração Base**</span><span class="sxs-lookup"><span data-stu-id="d5acb-107">**Figure 1: The Base Configuration dev/test environment**</span></span>

<span data-ttu-id="d5acb-p101">O ambiente de desenvolvimento/teste da Configuração Base na Figura 1 inclui a sub-rede Corpnet em uma rede virtual do Azure, somente na nuvem, chamada TestLab que simula uma intranet simplificada e privada conectada à Internet. Ele contém três máquinas virtuais do Azure em que o Windows Server 2016 é executado:</span><span class="sxs-lookup"><span data-stu-id="d5acb-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines running WIndows Server 2016:</span></span>
  
- <span data-ttu-id="d5acb-110">O DC1 está configurado como um controlador de domínio de intranet e servidor de Sistema de Nomes de Domínio (DNS).</span><span class="sxs-lookup"><span data-stu-id="d5acb-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="d5acb-111">O APP1 está configurado como um servidor Web e aplicativo geral.</span><span class="sxs-lookup"><span data-stu-id="d5acb-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="d5acb-112">O CLIENT1 atua como um cliente de intranet.</span><span class="sxs-lookup"><span data-stu-id="d5acb-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="d5acb-113">Essa configuração permite que o DC1, APP1, CLIENT1 e outros computadores na sub-rede Corpnet:</span><span class="sxs-lookup"><span data-stu-id="d5acb-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="d5acb-114">Fiquem conectados à Internet para instalar atualizações, acessar os recursos da Internet em tempo real e participar de tecnologias públicas de nuvem como o Microsoft Office 365 e outros serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="d5acb-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="d5acb-115">Sejam gerenciados remotamente usando conexões da de Área de Trabalho Remota do seu computador que está conectado à Internet ou à rede da sua organização.</span><span class="sxs-lookup"><span data-stu-id="d5acb-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="d5acb-116">É possível usar o ambiente teste resultante:</span><span class="sxs-lookup"><span data-stu-id="d5acb-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="d5acb-117">Para testes e desenvolvimento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d5acb-117">For application development and testing.</span></span>
    
- <span data-ttu-id="d5acb-118">Como a configuração inicial de um ambiente de teste estendido dos seu próprios designs, que inclui máquinas virtuais adicionais, serviços do Azure ou outras ofertas de nuvem da Microsoft como o Office 365 e Enterprise Mobility + Security (EMS).</span><span class="sxs-lookup"><span data-stu-id="d5acb-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility (EMS).</span></span>
    
<span data-ttu-id="d5acb-119">Há dois métodos para criar esse ambiente:</span><span class="sxs-lookup"><span data-stu-id="d5acb-119">There are two methods to creating this environment:</span></span>

1. <span data-ttu-id="d5acb-120">Um modelo do Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="d5acb-120">An Azure Resource Manager template</span></span>
2. <span data-ttu-id="d5acb-121">Usar o Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5acb-121">Azure Powershell</span></span>

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a><span data-ttu-id="d5acb-122">Método 1: criar sua intranet simulada com um modelo do Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="d5acb-122">Method 1: Build your simulated intranet with an Azure Resource Manager template</span></span>

<span data-ttu-id="d5acb-p102">Nesse método, você usa um modelo do Azure Resource Manager (ARM) para criar uma intranet simulada. Os modelos do ARM contêm todas as instruções para criar e configurar a infraestrutura de rede do Azure e as máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p102">In this method, you use an Azure Resource Manager (ARM) template to build out the simulated intranet. ARM templates contain all of the instructions to create the Azure networking infrastructure, the virtual machines, and their configuration.</span></span>

<span data-ttu-id="d5acb-125">Antes de implantar o modelo, leia toda a [página LEIAME do modelo](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) e tenha as seguintes informações em mãos:</span><span class="sxs-lookup"><span data-stu-id="d5acb-125">Prior to deploying the template, read through the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) and have the following information ready:</span></span>

- <span data-ttu-id="d5acb-p103">O nome da assinatura do Azure. Você precisará inserir esse rótulo nas **assinatura** campo dos **implantação personalizada** página.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p103">The Azure subscription name. You’ll need to enter this label in the **Subscription** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="d5acb-p104">O nome do grupo de recursos do Azure. Você precisará inserir esse rótulo nas **grupo de recursos** campo dos **implantação personalizada** página.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p104">The Azure resource group name. You’ll need to enter this label in the **Resource group** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="d5acb-p105">Um prefixo de rótulo DNS para as URLs dos endereços IP públicos de suas máquinas virtuais. Você precisará inserir esse rótulo no campo **Prefixo do rótulo DNS** da página **Implantação personalizada**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p105">A DNS label prefix for the URLs of the public IP addresses of your virtual machines. You’ll need to enter this label in the **Dns Label Prefix** field of the **Custom deployment** page.</span></span>

<span data-ttu-id="d5acb-132">Depois de ler todas as instruções, clique em **Implantar no Azure** na [página LEIAME do modelo](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) para começar.</span><span class="sxs-lookup"><span data-stu-id="d5acb-132">After reading through the instructions, click **Deploy to Azure** on the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) to get started.</span></span>

>[!Note]
><span data-ttu-id="d5acb-133">A intranet simulada criada pelo modelo do ARM requer uma assinatura paga do Azure.</span><span class="sxs-lookup"><span data-stu-id="d5acb-133">The simulated intranet built by the ARM template requires a paid Azure subscription.</span></span>
>

<span data-ttu-id="d5acb-134">Esta é sua configuração após a conclusão do modelo.</span><span class="sxs-lookup"><span data-stu-id="d5acb-134">Here is your configuration after the template is complete.</span></span>

![A configuração padrão no Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a><span data-ttu-id="d5acb-136">Método 2: criar sua intranet simulada com o Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5acb-136">Method 2: Build your simulated intranet with PowerShell</span></span>

<span data-ttu-id="d5acb-137">Nesse método, use o módulo do Windows PowerShell e do Azure PowerShell para criar a infraestrutura de rede, as máquinas virtuais e suas configurações.</span><span class="sxs-lookup"><span data-stu-id="d5acb-137">In this method, you use Windows PowerShell and the Azure PowerShell module to build out the networking infrastructure, the virtual machines, and their configuration.</span></span>

<span data-ttu-id="d5acb-p106">Use esse método caso deseje obter a experiência de criação de elementos de infraestrutura do Azure um bloco de comando por vez com o PowerShell. Assim, é possível personalizar os blocos de comando do PowerShell para sua própria implantação de outras máquinas virtuais no Azure.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p106">Use this method with an Azure trial subscription or if you want to get experience creating elements of Azure infrastructure one step at a time with PowerShell. You can then customize the PowerShell command blocks for your own deployment of other virtual machines in Azure.</span></span>

<span data-ttu-id="d5acb-140">Há quatro etapas para configurar o ambiente de teste de configuração básica usando o Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d5acb-140">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="d5acb-141">Criar uma rede virtual.</span><span class="sxs-lookup"><span data-stu-id="d5acb-141">Create the virtual network.</span></span>
    
2. <span data-ttu-id="d5acb-142">Configurar o DC1.</span><span class="sxs-lookup"><span data-stu-id="d5acb-142">Configure DC1.</span></span>
    
3. <span data-ttu-id="d5acb-143">Configurar o APP1.</span><span class="sxs-lookup"><span data-stu-id="d5acb-143">Configure APP1.</span></span>
    
4. <span data-ttu-id="d5acb-144">Configurar o CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="d5acb-144">Configure CLIENT1.</span></span>
    
<span data-ttu-id="d5acb-p107">Se você ainda não tem a assinatura do Azure, inscreva-se para uma avaliação gratuita em [Experimentar o Azure](https://azure.microsoft.com/pricing/free-trial/). Se você já tem a assinatura do MSDN ou Visual Studio, consulte o [crédito mensal do Azure para assinantes do Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="d5acb-p107">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d5acb-p108">As máquinas virtuais no Azure implicam um custo monetário contínuo quando estão em execução. Esse custo é cobrado em relação à avaliação gratuita, assinatura do MSDN ou assinatura paga. Para saber mais sobre os custos de execução de máquinas virtuais do Azure, consulte os [detalhes de preços de máquinas virtuais](https://azure.microsoft.com/pricing/details/virtual-machines/) e a [calculadora de preços do Azure](https://azure.microsoft.com/pricing/calculator/). Para reduzir custos, consulte também mais informações sobre como [minimizar os custos de máquinas virtuais do ambiente de teste no Azure](base-configuration-dev-test-environment.md#mincost).</span><span class="sxs-lookup"><span data-stu-id="d5acb-p108">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Guias do Laboratório de Teste da Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="d5acb-152">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="d5acb-152">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
### <a name="step-1-create-the-virtual-network"></a><span data-ttu-id="d5acb-153">Etapa 1: Criar rede virtual</span><span class="sxs-lookup"><span data-stu-id="d5acb-153">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="d5acb-154">Nesta etapa, você a rede virtual TestLab no Azure.</span><span class="sxs-lookup"><span data-stu-id="d5acb-154">In this step, you the TestLab virtual network in Azure.</span></span>

<span data-ttu-id="d5acb-155">Primeiro, abra um prompt no Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-155">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d5acb-p109">O comando a seguir define o uso da versão mais recente do Azure PowerShell. Consulte a [introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/pt-BR/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="d5acb-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/pt-BR/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="d5acb-158">Entre na sua conta do Azure usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="d5acb-158">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="d5acb-159">Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) para obter um arquivo de texto que contém todos os comandos do PowerShell deste artigo.</span><span class="sxs-lookup"><span data-stu-id="d5acb-159">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="d5acb-160">Para obter o nome de sua assinatura, use este comando.</span><span class="sxs-lookup"><span data-stu-id="d5acb-160">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="d5acb-p110">Configure a assinatura do Azure. Substitua tudo o que está entre aspas, incluindo os caracteres < e >, pelo nome correto.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p110">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="d5acb-p111">Depois, crie um novo grupo de recursos para seu laboratório de teste da Configuração Base. Para determinar um nome de grupo de recursos exclusivo, use este comando para listar seus grupos de recurso existentes.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p111">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="d5acb-p112">Crie seu novo grupo de recursos com estes comandos. Substitua tudo o que está entre aspas, incluindo os caracteres < e >, pelos nomes corretos.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p112">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="d5acb-167">Em seguida, crie a rede virtual TestLab, que hospedará a sub-rede Corpnet da configuração base e a protegerá com um grupo de segurança de rede.</span><span class="sxs-lookup"><span data-stu-id="d5acb-167">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
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

<span data-ttu-id="d5acb-168">Essa é sua configuração atual.</span><span class="sxs-lookup"><span data-stu-id="d5acb-168">This is your current configuration.</span></span>
  
![Etapa 1 da Configuração Base no Azure com sub-rede e rede virtuais](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a><span data-ttu-id="d5acb-170">Etapa 2: configurar o DC1</span><span class="sxs-lookup"><span data-stu-id="d5acb-170">Step 2: Configure APP1</span></span>

<span data-ttu-id="d5acb-171">Nesta fase, você vai criar a máquina virtual DC1 e configurá-la como o controle de domínio para o domínio corp.contoso.com do AD (Active Directory) do Windows Server e um servidor DNS para as máquinas virtuais da rede virtual TestLab.</span><span class="sxs-lookup"><span data-stu-id="d5acb-171">In this phase, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>

> [!NOTE]
> <span data-ttu-id="d5acb-p113">Antes de executar o bloco de comando a seguir, certifique-se do região do Azure (local) que você escolheu seja compatível com o tamanho de máquina virtual Azure, que é definido como Standard_A1 por padrão. Clique em [veja](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) para ver as informações mais recentes em tamanhos de máquina virtual Azure e locais.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p113">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="d5acb-174">Para criar uma máquina virtual para o DC1, preencha o nome do grupo de recursos e execute estes comandos no prompt de comando do Azure PowerShell no computador local.</span><span class="sxs-lookup"><span data-stu-id="d5acb-174">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="d5acb-p114">Será solicitado que você insira um nome de usuário e uma senha para a conta de administrador local no DC1. Use uma senha forte e armazene ambos, a senha e o nome, em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p114">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="d5acb-177">Em seguida, conecte-se à máquina virtual DC1.</span><span class="sxs-lookup"><span data-stu-id="d5acb-177">Next, connect to the DC1 virtual machine.</span></span>
  
1. <span data-ttu-id="d5acb-178">No [portal do Azure](https://portal.azure.com), clique em **Grupos de Recursos >** [nome do novo grupo de recursos] **> DC1 > Conectar**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-178">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="d5acb-p115">No painel aberto, clique em **Baixar o arquivo RDP**. Abra o arquivo DC1.rdp que foi baixado e clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p115">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="d5acb-181">Especifique o nome da conta de administrador local na DC1:</span><span class="sxs-lookup"><span data-stu-id="d5acb-181">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="d5acb-182">No Windows 7:</span><span class="sxs-lookup"><span data-stu-id="d5acb-182">For Windows 7:</span></span>
    
    <span data-ttu-id="d5acb-p116">Na caixa de diálogo **Segurança do Windows**, clique em **Usar outra conta**. Em **Nome de usuário**, digite **DC1\\**[nome da conta de administrador local].</span><span class="sxs-lookup"><span data-stu-id="d5acb-p116">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="d5acb-185">No Windows 8 ou Windows 10:</span><span class="sxs-lookup"><span data-stu-id="d5acb-185">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="d5acb-p117">Na caixa de diálogo **Segurança do Windows**, clique em **Mais opções** e, então, clique em **Usar uma conta diferente**. Em **Nome de usuário**, digite **DC1\\**[nome da conta de administrador local].</span><span class="sxs-lookup"><span data-stu-id="d5acb-p117">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="d5acb-188">Em **Senha**, digite a senha da conta de administrador local e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-188">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="d5acb-189">Quando solicitado, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-189">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="d5acb-190">Em seguida, adicione um disco de dados extra como um novo volume com a letra de unidade F:, com este comando, em um prompt de comando do Windows PowerShell de nível de administrador no DC1.</span><span class="sxs-lookup"><span data-stu-id="d5acb-190">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="d5acb-p118">Depois, configure o DC1 como controlador de domínio e servidor DNS para o domínio corp.contoso.com. Execute estes comandos em um prompt de comando do Windows PowerShell de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p118">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="d5acb-p119">Será preciso especificar uma senha de administrador no modo de segurança. Armazene essa senha em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p119">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="d5acb-195">Esses comandos podem levar alguns minutos para serem concluídos.</span><span class="sxs-lookup"><span data-stu-id="d5acb-195">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="d5acb-196">Após a reinicialização da DC1, reconecte a máquina virtual de DC1 usando credenciais de domínio.</span><span class="sxs-lookup"><span data-stu-id="d5acb-196">After DC1 restarts, reconnect to the DC1 virtual machine.</span></span>
  
1. <span data-ttu-id="d5acb-197">No [portal do Azure](https://portal.azure.com), clique em **Grupos de Recursos >** [nome do seu grupo de recursos] **> DC1 > Conectar**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-197">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="d5acb-198">Execute o arquivo DC1.rdp que foi baixado e clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-198">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="d5acb-p120">Em **Segurança do Windows**, clique em **Usar outra conta**. Em **Nome de usuário**, digite **CORP\\**[nome da conta de administrador local].</span><span class="sxs-lookup"><span data-stu-id="d5acb-p120">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="d5acb-201">Em **Senha**, digite a senha da conta de administrador local e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-201">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="d5acb-202">Quando solicitado, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-202">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="d5acb-p121">Em seguida, crie uma conta de usuário no Active Directory que será usada quando entrar nos computadores dos membros do domínio CORP. Execute este comando no prompt de comando nível de administrador do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p121">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="d5acb-p122">Esse comando solicitará que você forneça a senha da conta User1. Como essa conta será usada para conexões remotas da área de trabalho para todos os computadores que são membros do domínio CORP, escolha uma senha forte. Registre a senha da conta User1 e armazene-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p122">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="d5acb-p123">Em seguida, configure a nova conta User1 como administrador corporativo. Execute este comando no prompt de comando do Windows PowerShell no nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p123">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="d5acb-210">Feche a sessão de Área de Trabalho Remota com o DC1 e se reconecte usando a conta CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="d5acb-210">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="d5acb-211">Em seguida, para permitir o tráfego da ferramenta Ping, execute este comando no prompt de comando de nível de administrador do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-211">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="d5acb-212">Essa é sua configuração atual.</span><span class="sxs-lookup"><span data-stu-id="d5acb-212">This is your current configuration.</span></span>
  
![Fase 2 da Configuração Base no Azure com a máquina virtual DC1](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a><span data-ttu-id="d5acb-214">Etapa 3: configurar o APP1</span><span class="sxs-lookup"><span data-stu-id="d5acb-214">Step 2: Configure APP1</span></span>

<span data-ttu-id="d5acb-215">Nesta etapa, criar e configurar APP1 que fornece serviços de compartilhamento de arquivos e da web.</span><span class="sxs-lookup"><span data-stu-id="d5acb-215">In this step, you create and configure APP1, which is an application server that initially provides web and file sharing services.</span></span>

> [!NOTE]
> <span data-ttu-id="d5acb-p124">Antes de executar o bloco de comando a seguir, certifique-se do região do Azure (local) que você escolheu seja compatível com o tamanho de máquina virtual Azure, que é definido como Standard_A1 por padrão. Clique em [veja](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) para ver as informações mais recentes em tamanhos de máquina virtual Azure e locais.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p124">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="d5acb-218">Para criar uma Máquina Virtual para o APP1, preencha o nome do grupo de recursos e execute estes comandos no prompt de comando do Azure PowerShell no computador local.</span><span class="sxs-lookup"><span data-stu-id="d5acb-218">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="d5acb-219">Em seguida, conecte-se à máquina virtual do APP1 usando o nome da conta e a senha do administrador local do APP1 e depois abra um prompt de comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-219">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="d5acb-220">Para verificar a comunicação da rede e a resolução de nome entre o APP1 e o DC1, execute o comando **ping dc1.corp.contoso.com** e verifique se há quatro respostas.</span><span class="sxs-lookup"><span data-stu-id="d5acb-220">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="d5acb-221">Em seguida, adicione a máquina virtual do APP1 ao domínio CORP com estes comandos no prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-221">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="d5acb-222">Você deve fornecer as credenciais de conta do domínio CORP\\User1 depois de executar o comando **Add-Computer**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-222">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="d5acb-223">Depois de reiniciar o APP1, conecte-se a ele usando a conta CORP\\User1 e, em seguida, abra um prompt de comando de nível de administrador do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-223">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="d5acb-224">Depois, transforme o APP1 em um servidor web usando este comando no prompt de comando do Windows PowerShell no APP1:</span><span class="sxs-lookup"><span data-stu-id="d5acb-224">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="d5acb-225">Em seguida, crie uma pasta compartilhada e um arquivo de texto dentro da pasta do APP1 com estes comandos no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-225">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="d5acb-226">Essa é sua configuração atual.</span><span class="sxs-lookup"><span data-stu-id="d5acb-226">This is your current configuration.</span></span>
  
![Fase 3 da Configuração Base no Azure com a máquina virtual do APP1](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a><span data-ttu-id="d5acb-228">Etapa 4: configurar o CLIENT1</span><span class="sxs-lookup"><span data-stu-id="d5acb-228">Step 3: Configure CLIENT1</span></span>

<span data-ttu-id="d5acb-229">Nessa etapa, você cria e configura o CLIENT1, que atua como um laptop, tablet ou computador na Contoso intranet.</span><span class="sxs-lookup"><span data-stu-id="d5acb-229">In this step, you create and configure CLIENT1, which acts as a typical laptop, tablet, or desktop computer on the intranet.</span></span>

> [!NOTE]  
> <span data-ttu-id="d5acb-p125">O seguinte conjunto de comandos cria a CLIENT1 executando o Windows Server 2016 Datacenter, o que pode ser feito em todos os tipos de assinaturas do Azure. Se você tiver a assinatura do Azure baseada em Visual Studio, será possível criar a CLIENT1 executando o Windows 10 no [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="d5acb-p125">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 
  

> [!NOTE]
> <span data-ttu-id="d5acb-p126">Antes de executar o bloco de comando a seguir, certifique-se do região do Azure (local) que você escolheu seja compatível com o tamanho de máquina virtual Azure, que é definido como Standard_A1 por padrão. Clique em [veja](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) para ver as informações mais recentes em tamanhos de máquina virtual Azure e locais.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p126">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="d5acb-234">Para criar uma Máquina Virtual no Azure para o CLIENT1, preencha o nome do grupo de recursos e execute estes comandos no prompt de comando do Azure PowerShell no computador local.</span><span class="sxs-lookup"><span data-stu-id="d5acb-234">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="d5acb-235">Em seguida, conecte-se à máquina virtual do CLIENT1 usando o nome da conta e a senha do administrador local do CLIENT1 e depois abra um prompt de comando de nível de administrador no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-235">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="d5acb-236">Para verificar a comunicação da rede e a resolução de nome entre o CLIENT1 e o DC1, execute o comando **ping dc1.corp.contoso.com** no prompt de comando do Windows PowerShell e verifique se há quatro respostas.</span><span class="sxs-lookup"><span data-stu-id="d5acb-236">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="d5acb-237">Em seguida, adicione a máquina virtual do CLIENT1 ao domínio CORP com estes comandos no prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-237">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="d5acb-238">Observe que você deve fornecer as credenciais de conta do domínio CORP\\User1 depois de executar o comando **Add-Computer**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-238">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="d5acb-239">Depois de reiniciar o CLIENT1, conecte-se a ele usando o nome e a senha da conta CORP\\User1 e, em seguida, abra um prompt de comando de nível de administrador no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5acb-239">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="d5acb-240">Após esse procedimento, verifique se você consegue acessar os recursos de compartilhamento de arquivo e da Web no APP1 a partir do CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="d5acb-240">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
1. <span data-ttu-id="d5acb-241">No Gerenciador do servidor, na árvore do painel, clique em **Servidor Local**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-241">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="d5acb-242">Em **Propriedades do CLIENT1**, clique em **Ativar** ao lado da **Configuração de Segurança Aprimorada do IE**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-242">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="d5acb-243">Na **Configuração de Segurança Aprimorada do Internet Explorer**, clique em **Desativar** para **Administradores** e **Usurários** e, então, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-243">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="d5acb-244">Na tela Inicial, clique em **Internet Explorer** e, então, em**OK**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-244">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="d5acb-p127">Na barra de endereços, digite **http:\//app1.corp.contoso.com/** e pressione Enter. Você verá uma página padrão da Web sobre Serviços de Informações da Internet para APP1.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p127">In the Address bar, type **http:\//app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="d5acb-247">Na barra de tarefas da área de trabalho, clique no ícone do Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="d5acb-247">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="d5acb-p128">Na barra de endereços, digite **\\\\app1\\Files** e pressione Enter. Você verá uma janela de pasta com o conteúdo da pasta compartilhada de arquivos.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p128">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="d5acb-p129">Na janela da pasta compartilhada **Arquivos**, clique duas vezes no arquivo **Example.txt**. Você verá o conteúdo do arquivo Example.txt.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p129">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="d5acb-252">Feche o \*\*Bloco de notas do Example.txt \*\* e a janela da pasta compartilhada **Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="d5acb-252">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="d5acb-253">Esta é sua configuração final.</span><span class="sxs-lookup"><span data-stu-id="d5acb-253">This is your final configuration.</span></span>
  
![Fase 4 da Configuração Base no Azure com a máquina virtual CLIENT1](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="d5acb-255">A Configuração Base no Azure agora está pronta para o desenvolvimento e os teste do aplicativo ou para criar ambientes de teste adicionais.</span><span class="sxs-lookup"><span data-stu-id="d5acb-255">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="d5acb-256">Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="d5acb-256">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
<span data-ttu-id="d5acb-257"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="d5acb-257"></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="d5acb-258">Minimizar os custos de máquinas virtuais do teste ambiente no Azure</span><span class="sxs-lookup"><span data-stu-id="d5acb-258">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="d5acb-259">Para reduzir os custos com a execução de máquinas virtuais em ambiente de teste, siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="d5acb-259">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="d5acb-p130">Crie um ambiente de teste e realize a demonstração e os testes necessários com a maior brevidade possível. Ao concluir, exclua o grupo de recursos do ambiente de teste.</span><span class="sxs-lookup"><span data-stu-id="d5acb-p130">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="d5acb-262">Desligue as máquinas virtuais do ambiente de teste para o estado desalocado.</span><span class="sxs-lookup"><span data-stu-id="d5acb-262">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="d5acb-263">Para desligar as máquinas virtuais com o Azure PowerShell, preencha o nome do grupo de recursos e execute estes comandos.</span><span class="sxs-lookup"><span data-stu-id="d5acb-263">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="d5acb-264">Para garantir que as máquinas virtuais funcionem corretamente ao iniciar todas elas do estado Parado (Desalocado), inicie-as na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="d5acb-264">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="d5acb-265">DC1</span><span class="sxs-lookup"><span data-stu-id="d5acb-265">DC1</span></span>
2. <span data-ttu-id="d5acb-266">APP1</span><span class="sxs-lookup"><span data-stu-id="d5acb-266">APP1</span></span>
3. <span data-ttu-id="d5acb-267">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="d5acb-267">CLIENT1</span></span>
    
<span data-ttu-id="d5acb-268">Para ligar as máquinas virtuais em ordem com o Azure PowerShell, preencha o nome do grupo de recursos e execute estes comandos.</span><span class="sxs-lookup"><span data-stu-id="d5acb-268">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="d5acb-269">Confira também</span><span class="sxs-lookup"><span data-stu-id="d5acb-269">See Also</span></span>

- [<span data-ttu-id="d5acb-270">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="d5acb-270">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="d5acb-271">DirSync para o ambiente de desenvolvimento/ teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="d5acb-271">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="d5acb-272">Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="d5acb-272">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="d5acb-273">Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="d5acb-273">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="d5acb-274">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="d5acb-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
