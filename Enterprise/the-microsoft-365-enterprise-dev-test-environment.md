---
title: Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Resumo: use este Guia de laboratório de teste para criar um ambiente de desenvolvimento/teste que incluir o Office 365 E5, Enterprise Mobility + Security (EMS) E5 e um computador executando o Windows 10 Enterprise.'
ms.openlocfilehash: 03fa8e0a4e8d90fcb834eeb2491d3dd39b67ff05
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "19178643"
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="6744a-103">Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="6744a-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="6744a-104">**Resumo:** use este Guia de laboratório de teste para criar um ambiente de desenvolvimento/teste que incluir o Office 365 E5, Enterprise Mobility + Security (EMS) E5 e um computador executando o Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="6744a-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="6744a-105">Este artigo fornece instruções passo a passo para criar um ambiente de teste simplificado testar os recursos e funcionalidades do [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="6744a-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="6744a-106">Fase 1: Criar sua assinatura do Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="6744a-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="6744a-107">Siga as etapas das Fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md) para criar um ambiente de desenvolvimento/teste simples do Office 365, como mostrado na Figura 1.</span><span class="sxs-lookup"><span data-stu-id="6744a-107">Follow the steps in Phase 2 and Phase 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="6744a-108">**Figura 1: Sua assinatura do Office 365 E5 com as contas de usuário e do locatário do Azure Active Directory (AD)**</span><span class="sxs-lookup"><span data-stu-id="6744a-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Fase 1 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> <span data-ttu-id="6744a-p101">A assinatura de avaliação do Office 365 E5 é de 30 dias, que podem ser facilmente estendidos por até 60 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com algumas licenças.</span><span class="sxs-lookup"><span data-stu-id="6744a-p101">The Office 365 E5 trial subscription is 30 days, which can be easily extended to 60 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="6744a-112">Fase 2: Adicionar o EMS</span><span class="sxs-lookup"><span data-stu-id="6744a-112">Phase 2: Add EMS</span></span>

<span data-ttu-id="6744a-113">Nesta fase, inscreva-se para a assinatura de avaliação do EMS E5 e adicione-a à mesma organização de sua assinatura de avaliação do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="6744a-113">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="6744a-114">Primeiro adicione a assinatura de avaliação do EMS E5 e atribua uma licença EMS à sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="6744a-114">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="6744a-p102">Em uma instância particular do navegador da Internet, entre no Portal do Office 365 com as credenciais da conta de administrador global. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6744a-p102">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6744a-117">Clique no bloco de **Administração**.</span><span class="sxs-lookup"><span data-stu-id="6744a-117">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="6744a-118">Na guia **Centro de Administração do Office** no navegador, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.</span><span class="sxs-lookup"><span data-stu-id="6744a-118">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="6744a-p103">Na página **Comprar serviços**, encontre o item **Enterprise Mobility + Security E5**. Passe o ponteiro do mouse sobre ele e clique em **Iniciar avaliação gratuita**.</span><span class="sxs-lookup"><span data-stu-id="6744a-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="6744a-121">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="6744a-121">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="6744a-122">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="6744a-122">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="6744a-123">Na guia **Centro de administração do Office 365** do navegador, no painel de navegação esquerdo, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="6744a-123">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="6744a-124">Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **Licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="6744a-124">Click your global administrator account, and then click Edit for Product licenses.</span></span>
    
9. <span data-ttu-id="6744a-125">No painel **Licenças de produto**, mude a licença de produto de **Enterprise Mobility + Security E5** para **Ativada**, clique em **Salvar** e clique em **Fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="6744a-125">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="6744a-p104">A assinatura de avaliação do Enterprise Mobility + Security E5 dura 90 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com uma pequena quantidade de licenças.</span><span class="sxs-lookup"><span data-stu-id="6744a-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="6744a-128">***Se você tiver concluído a Fase 3 do*** [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md), repita as etapas 8 e 9 do procedimento anterior para todas as suas contas (Usuário 2, Usuário 3, Usuário 4 e Usuário 5).</span><span class="sxs-lookup"><span data-stu-id="6744a-128">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="6744a-129">Seu ambiente de desenvolvimento/teste agora tem:</span><span class="sxs-lookup"><span data-stu-id="6744a-129">Your Office 365 and EMS dev/test environment now has:</span></span>
  
- <span data-ttu-id="6744a-130">As assinaturas de avaliação do Office 365 Enterprise E5 e do EMS E5 compartilham o mesmo locatário do Azure AD com sua lista de contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="6744a-130">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="6744a-131">Todas as suas contas de usuário apropriadas (a conta do administrador global ou todas as cinco contas de usuário) estão habilitadas para usar o Office 365 E5 e o EMS E5.</span><span class="sxs-lookup"><span data-stu-id="6744a-131">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="6744a-132">A Figura 2 mostra a configuração resultante, que adiciona o EMS.</span><span class="sxs-lookup"><span data-stu-id="6744a-132">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="6744a-133">**Figura 2: Adicionar a assinatura de avaliação do EMS**</span><span class="sxs-lookup"><span data-stu-id="6744a-133">**Figure 2: Adding the EMS trial subscription**</span></span>

![Fase 2 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="6744a-135">Fase 3: Criar um computador com o Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="6744a-135">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="6744a-136">Nesta fase, crie um computador autônomo executando o Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="6744a-136">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="6744a-137">Computador físico</span><span class="sxs-lookup"><span data-stu-id="6744a-137">Physical computer</span></span>

<span data-ttu-id="6744a-p105">Obtenha um computador pessoal e instale o Windows 10 Enterprise. Você pode baixar a versão de avaliação do Windows 10 Enterprise [aqui](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="6744a-p105">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="6744a-140">Máquina virtual</span><span class="sxs-lookup"><span data-stu-id="6744a-140">Virtual machine</span></span>

<span data-ttu-id="6744a-p106">Crie uma máquina virtual usando o hipervisor de sua escolha e instale o Windows 10 Enterprise. Você pode baixar a versão de avaliação do Windows 10 Enterprise [aqui](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="6744a-p106">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="6744a-143">Máquina virtual no Azure</span><span class="sxs-lookup"><span data-stu-id="6744a-143">Virtual machine in Azure</span></span>

<span data-ttu-id="6744a-p107">Para criar uma máquina virtual do Windows 10 no Microsoft Azure, ***você deve ter uma assinatura baseada no Visual Studio***, que tem acesso à imagem do Windows 10 Enterprise. Outros tipos de assinatura do Azure, como assinaturas de avaliação e pagas, não têm acesso a esta imagem. Confira as informações mais recentes em [Usar o cliente do Windows no Azure para cenários de desenvolvimento/teste](https://docs.microsoft.com/azure/virtual-machines/windows/client-images).</span><span class="sxs-lookup"><span data-stu-id="6744a-p107">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image. For the latest information, see [Use Windows client in Azure for dev/test scenarios](https://docs.microsoft.com/azure/virtual-machines/windows/client-images).</span></span>
  
> [!NOTE]
> <span data-ttu-id="6744a-p108">Os conjuntos de comandos a seguir usam a versão mais recente do Azure PowerShell. Confira [Introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Esses conjuntos de comandos montam uma máquina virtual do Windows 10 Enterprise chamada WIN10 e toda a infraestrutura necessária, incluindo um grupo de recursos, uma conta de armazenamento e uma rede virtual. Se você já estiver familiarizado com os serviços de infraestrutura Azure, adapte estas instruções para se ajustar à sua infraestrutura implantada no momento.</span><span class="sxs-lookup"><span data-stu-id="6744a-p108">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="6744a-151">Inicie um prompt do Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6744a-151">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="6744a-152">Entre na sua conta do Azure usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="6744a-152">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="6744a-153">Para obter o nome de sua assinatura, use este comando.</span><span class="sxs-lookup"><span data-stu-id="6744a-153">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="6744a-p109">Defina sua assinatura do Azure. Substitua tudo o que está entre aspas, incluindo os caracteres \< e >, pelo nome correto.</span><span class="sxs-lookup"><span data-stu-id="6744a-p109">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="6744a-p110">Depois, crie um novo grupo de recursos. Para determinar um nome exclusivo para o grupo de recursos, use este comando para listar os grupos de recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="6744a-p110">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="6744a-p111">Crie seu novo grupo de recursos com estes comandos. Substitua tudo o que está entre aspas, incluindo os caracteres \< e >, pelos nomes corretos.</span><span class="sxs-lookup"><span data-stu-id="6744a-p111">Create your new resource group with these commands. Set the variables by replacing everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="6744a-p112">Em seguida, crie uma nova rede virtual e uma máquina virtual WIN10 com estes comandos. Quando solicitado, forneça o nome e a senha da conta de administrador local para WIN10 e armazene-os em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="6744a-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="6744a-162">Fase 4: Adicionar o computador com Windows 10 no Azure AD</span><span class="sxs-lookup"><span data-stu-id="6744a-162">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="6744a-163">Depois de criar a máquina física ou virtual com Windows 10 Enterprise, entre com uma conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="6744a-163">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6744a-p113">Conecte uma máquina virtual no Azure usando [estas instruções](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Entre com as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="6744a-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="6744a-166">Em seguida, adicione o computador WIN10 no locatário do Azure AD das suas assinaturas do Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="6744a-166">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="6744a-167">Na área de trabalho do computador WIN10, clique em **Iniciar > Configurações > Contas > Acessar trabalho ou escola > Conectar**.</span><span class="sxs-lookup"><span data-stu-id="6744a-167">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="6744a-168">Na caixa de diálogo **Configurar uma conta corporativa ou de estudante**, clique em **Adicionar este dispositivo ao Azure AD**.</span><span class="sxs-lookup"><span data-stu-id="6744a-168">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="6744a-169">Em **Conta corporativa ou de estudante**, digite o nome da conta do administrador global da sua assinatura do Office 365 e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="6744a-169">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="6744a-170">Em **Digitar Senha**, digite a senha da conta de administrador global e clique em **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="6744a-170">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="6744a-171">Quando solicitado para garantir que esta é sua organização, clique em **Ingressar** e em **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="6744a-171">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="6744a-172">Feche a janela de configurações.</span><span class="sxs-lookup"><span data-stu-id="6744a-172">Close the settings window.</span></span>
    
<span data-ttu-id="6744a-173">Em seguida, instale o Office 365 ProPlus no computador WIN10.</span><span class="sxs-lookup"><span data-stu-id="6744a-173">Next, install Office 365 ProPlus on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="6744a-p114">Abra o navegador do Microsoft Edge e entre no Portal do Office 365 com as credenciais da conta de administrador global. Para obter ajuda, confira [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6744a-p114">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6744a-176">Na guia **Microsoft Office Home**, clique em **Instalar o Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="6744a-176">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="6744a-177">Quando solicitado sobre o que fazer, clique em **Executar** e em **Sim** para **Controle de Conta de Usuário**.</span><span class="sxs-lookup"><span data-stu-id="6744a-177">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="6744a-p115">Aguarde até concluir a instalação do Office. Quando você vir **Tudo pronto!**, clique duas vezes em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="6744a-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="6744a-180">A Figura 3 mostra o ambiente resultante, que inclui o computador do WIN10 que:</span><span class="sxs-lookup"><span data-stu-id="6744a-180">Figure 3 shows your resulting environment, which includes the WIN10 computer that has:</span></span>

- <span data-ttu-id="6744a-181">Ingressou no locatário do Azure AD das suas assinaturas do Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="6744a-181">Joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
- <span data-ttu-id="6744a-182">Registrou um dispositivo do Azure AD no Intune (EMS).</span><span class="sxs-lookup"><span data-stu-id="6744a-182">Enrolled as an Azure AD device in Intune (EMS).</span></span>
- <span data-ttu-id="6744a-183">Instalou o Office 365 ProPlus.</span><span class="sxs-lookup"><span data-stu-id="6744a-183">Has Office 365 ProPlus installed.</span></span>
  
<span data-ttu-id="6744a-184">**Figura 3: a configuração de final de um ambiente de desenvolvimento/teste do Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="6744a-184">**Figure 3: The final configuration of the Microsoft 365 dev/test environment**</span></span>

![Fase 4 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="6744a-186">Agora você está pronto para experimentar os recursos adicionais do [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="6744a-186">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="6744a-187">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6744a-187">Next steps</span></span>

<span data-ttu-id="6744a-188">Confira estes artigos adicionais para explorar os recursos do Microsoft 365 Enterprise:</span><span class="sxs-lookup"><span data-stu-id="6744a-188">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="6744a-189">Adicionar políticas do gerenciamento de aplicativos móveis (MAM)</span><span class="sxs-lookup"><span data-stu-id="6744a-189">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="6744a-190">Registrar dispositivos iOS e Android</span><span class="sxs-lookup"><span data-stu-id="6744a-190">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="6744a-191">Configurar e testar o Gerenciamento de Segurança Avançada</span><span class="sxs-lookup"><span data-stu-id="6744a-191">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="6744a-192">Configurar e testar a Proteção Avançada contra Ameaças</span><span class="sxs-lookup"><span data-stu-id="6744a-192">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="6744a-193">Confira também</span><span class="sxs-lookup"><span data-stu-id="6744a-193">See also</span></span>

- [<span data-ttu-id="6744a-194">Documentação do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="6744a-194">Microsoft 365 Enterprise documentation and resources</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- <span data-ttu-id="6744a-195">[Implantar o Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)</span><span class="sxs-lookup"><span data-stu-id="6744a-195">Microsoft 365 Enterprise[](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)</span></span>
- [<span data-ttu-id="6744a-196">Ambiente de desenvolvimento/teste do One Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="6744a-196">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
- [<span data-ttu-id="6744a-197">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="6744a-197">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
