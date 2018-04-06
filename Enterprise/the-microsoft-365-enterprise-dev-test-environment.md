---
title: O ambiente de desenvolvimento e teste da Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Resumo: Use este guia de laboratório de teste para criar um ambiente de desenvolvimento e teste que inclui o Office 365 E5, Enterprise mobilidade + E5 de segurança (EMS) e um computador que executa o Windows 10 Enterprise.'
ms.openlocfilehash: f4100a870191f03f82e7af5e79e710ee1403e8c7
ms.sourcegitcommit: 1db536d09343bdf6b4eb695ab07890164c047bd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="2afee-103">O ambiente de desenvolvimento e teste da Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="2afee-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="2afee-104">**Resumo:** Use este guia de laboratório de teste para criar um ambiente de desenvolvimento e teste que inclui o Office 365 E5, Enterprise mobilidade + E5 de segurança (EMS) e um computador que executa o Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="2afee-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="2afee-105">Este artigo fornece instruções passo a passo para criar um ambiente simplificado para testar os recursos e funcionalidades do [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="2afee-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="2afee-106">Fase 1: Crie sua assinatura do Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="2afee-106">Phase 1: Create your Office 365 E5 subscription</span></span>

<span data-ttu-id="2afee-107">Siga as etapas em fase 2 e a fase 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md) para criar um ambiente de desenvolvimento e teste de lightweight Office 365, conforme mostrado na Figura 1.</span><span class="sxs-lookup"><span data-stu-id="2afee-107">Follow the steps in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="2afee-108">**Figura 1: Sua assinatura do Office 365 E5 com suas contas de usuário e de locatário do Azure Active Directory (AD)**</span><span class="sxs-lookup"><span data-stu-id="2afee-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Fase 1 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="2afee-110">Fase 2: Adicionar EMS</span><span class="sxs-lookup"><span data-stu-id="2afee-110">Phase 2: Add EMS</span></span>

<span data-ttu-id="2afee-111">Nesta fase, inscreva-se para a assinatura de avaliação do EMS E5 e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="2afee-111">In this phase, you sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 E5 trial subscription.</span></span>
  
<span data-ttu-id="2afee-112">Primeiro, adicione a assinatura de avaliação do EMS E5 e atribuir uma licença do EMS à sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="2afee-112">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="2afee-p101">Com uma instância particular de um navegador da Internet, entre no portal do Office 365 com suas credenciais de conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="2afee-p101">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="2afee-115">Clique no bloco de **Administração**.</span><span class="sxs-lookup"><span data-stu-id="2afee-115">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="2afee-116">Na guia **Centro de Administração do Office** no navegador, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.</span><span class="sxs-lookup"><span data-stu-id="2afee-116">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="2afee-p102">Na página **Serviços de compra** , localize o item de **mobilidade corporativos + E5 de segurança** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="2afee-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="2afee-119">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="2afee-119">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="2afee-120">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="2afee-120">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="2afee-121">Na guia **Centro de Administração do Office 365** no navegador, no painel de navegação esquerdo, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="2afee-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="2afee-122">Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="2afee-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="2afee-123">No painel de **licenças do produto** , ativar a licença do produto para **mobilidade corporativos + E5 de segurança** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="2afee-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="2afee-p103">A assinatura de avaliação do Enterprise Mobility + Security E5 dura 90 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com uma pequena quantidade de licenças.</span><span class="sxs-lookup"><span data-stu-id="2afee-p103">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="2afee-126">***Se você concluiu a fase 3 do*** [Ambiente de desenvolvimento e teste do office 365](office-365-dev-test-environment.md), repita as etapas 8 e 9 do procedimento anterior para todas as suas contas (usuário 2, 3 do usuário, usuário 4 e 5 do usuário).</span><span class="sxs-lookup"><span data-stu-id="2afee-126">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="2afee-127">Seu ambiente de desenvolvimento e teste agora tem:</span><span class="sxs-lookup"><span data-stu-id="2afee-127">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="2afee-128">Assinaturas de avaliação do Office 365 Enterprise E5 e do EMS que compartilham a mesma organização e o mesmo locatário do Azure AD com sua lista de contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="2afee-128">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="2afee-129">Todas as suas contas de usuário apropriada (administrador global ou todas as contas de usuário de cinco) estão habilitadas para usar o Office 365 E5 e EMS E5.</span><span class="sxs-lookup"><span data-stu-id="2afee-129">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="2afee-130">A Figura 2 mostra a configuração resultante, que adiciona EMS.</span><span class="sxs-lookup"><span data-stu-id="2afee-130">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="2afee-131">**Figura 2: Adicionar a assinatura de avaliação do EMS**</span><span class="sxs-lookup"><span data-stu-id="2afee-131">**Figure 2: Adding the EMS trial subscription**</span></span>

![Fase 2 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="2afee-133">Fase 3: Criar um computador Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="2afee-133">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="2afee-134">Nesta fase, você deve criar um computador autônomo que executa o Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="2afee-134">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="2afee-135">Computador físico</span><span class="sxs-lookup"><span data-stu-id="2afee-135">Physical computer</span></span>

<span data-ttu-id="2afee-p104">Obtenha um computador pessoal e instale o Windows 10 Enterprise contidas nela. Você pode baixar o Windows 10 Enterprise avaliação [aqui](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="2afee-p104">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="2afee-138">Máquina virtual</span><span class="sxs-lookup"><span data-stu-id="2afee-138">Virtual machine</span></span>

<span data-ttu-id="2afee-p105">Crie uma máquina virtual usando o hipervisor de sua escolha e instale o Windows 10 Enterprise contidas nela. Você pode baixar o Windows 10 Enterprise avaliação [aqui](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="2afee-p105">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="2afee-141">Máquina virtual no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="2afee-141">Virtual machine in Azure</span></span>

<span data-ttu-id="2afee-142">Crie uma máquina virtual de Windows 10 in Microsoft Azure usando a imagem da Galeria do Azure.</span><span class="sxs-lookup"><span data-stu-id="2afee-142">Create a Windows 10 virtual machine in Microsoft Azure using the Azure gallery image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2afee-p106">O comando a seguir define use a versão mais recente de te do Azure PowerShell. Consulte a [Introdução ao cmdlets do PowerShell do Windows Azure](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Esses conjuntos de comando compilação uma máquina virtual de Windows 10 Enterprise denominado WIN10 e todas as sua infra-estrutura necessária, incluindo um grupo de recursos, uma conta de armazenamento e uma rede virtual. Se você já estiver familiarizado com os serviços de infraestrutura do Windows Azure, se adapte essas instruções de acordo com sua infraestrutura implantada no momento.</span><span class="sxs-lookup"><span data-stu-id="2afee-p106">The following command sets use te latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="2afee-147">Em primeiro lugar, inicie um prompt de Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2afee-147">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="2afee-148">Inscreva-se à sua conta do Windows Azure com o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="2afee-148">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="2afee-149">Para obter o nome de sua assinatura, use este comando.</span><span class="sxs-lookup"><span data-stu-id="2afee-149">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="2afee-p107">Defina sua assinatura do Windows Azure. Substituir tudo entre aspas, incluindo o \< e > caracteres, com o nome correto.</span><span class="sxs-lookup"><span data-stu-id="2afee-p107">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="2afee-p108">Depois, crie um novo grupo de recursos. Para determinar um nome exclusivo para o grupo de recursos, use este comando para listar os grupos de recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="2afee-p108">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="2afee-p109">Crie seu novo grupo de recursos com esses comandos. Substituir tudo entre aspas, incluindo o \< e > caracteres, com os nomes corretos.</span><span class="sxs-lookup"><span data-stu-id="2afee-p109">Create your new resource group with these commands. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="2afee-p110">Em seguida, você cria uma nova rede virtual e a máquina virtual WIN10 com esses comandos. Quando solicitado, forneça o nome e a senha da conta de administrador local para WIN10 e armazená-los em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="2afee-p110">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
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

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="2afee-158">Fase 4: Ingressar seu computador 10 do Windows Azure AD</span><span class="sxs-lookup"><span data-stu-id="2afee-158">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="2afee-159">Depois que o física ou máquina virtual com Windows 10 Enterprise é criada, entre com uma conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="2afee-159">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2afee-p111">Para uma máquina virtual no Windows Azure, conecte-se a ela usando [estas instruções](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Entrar com as credenciais da conta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="2afee-p111">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="2afee-162">Em seguida, ingresse o computador WIN10 locatário do Azure AD de suas assinaturas do Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="2afee-162">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="2afee-163">Na área de trabalho do computador WIN10, clique em **Iniciar > Configurações > contas > acesso trabalho ou escola > conectar**.</span><span class="sxs-lookup"><span data-stu-id="2afee-163">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="2afee-164">Na caixa de diálogo **Configurar uma conta de trabalho ou da escola** , clique em **ingressar este dispositivo para o Windows Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="2afee-164">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="2afee-165">Em **trabalho ou escola conta**, digite o nome da conta de administrador global de sua assinatura do Office 365 e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="2afee-165">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="2afee-166">Em **Digite a senha**, digite a senha da sua conta de administrador global e, em seguida, clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="2afee-166">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="2afee-167">Quando solicitado a certificar-se de que esta é a sua organização, clique em **ingressar**e clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="2afee-167">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="2afee-168">Feche a janela configurações.</span><span class="sxs-lookup"><span data-stu-id="2afee-168">Close the settings window.</span></span>
    
<span data-ttu-id="2afee-169">Em seguida, instale o Office 2016 no computador WIN10.</span><span class="sxs-lookup"><span data-stu-id="2afee-169">Next, install Office 2016 on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="2afee-p112">Abra o navegador Microsoft Edge e entrar no portal do Office 365 com suas credenciais de conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="2afee-p112">Open the Microsoft Edge browser and sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="2afee-172">Na guia **Página inicial do Microsoft Office** , clique em **instalar Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="2afee-172">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="2afee-173">Quando solicitado com o que fazer, clique em **Executar**e, em seguida, clique em **Sim** para **Controle de conta de usuário**.</span><span class="sxs-lookup"><span data-stu-id="2afee-173">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="2afee-p113">Aguarde do Office completar sua instalação. Quando você vir **você estará pronto!**, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="2afee-p113">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="2afee-176">A Figura 3 mostra seu ambiente resultante, que inclui o computador WIN10 que foi Unido locatário do Azure AD de suas assinaturas do Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="2afee-176">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="2afee-177">**Figura 3: Adicionando a conta de computador do WIN10 ao locatário do Azure AD.**</span><span class="sxs-lookup"><span data-stu-id="2afee-177">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Fase 4 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="2afee-179">Agora você está pronto para experimentar os recursos adicionais do [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="2afee-179">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="2afee-180">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2afee-180">Next steps</span></span>

<span data-ttu-id="2afee-181">Use estes artigos adicionais para explorar os recursos do Microsoft 365 Enterprise:</span><span class="sxs-lookup"><span data-stu-id="2afee-181">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="2afee-182">Adicionar políticas de gerenciamento (MAM) do aplicativo móvel</span><span class="sxs-lookup"><span data-stu-id="2afee-182">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="2afee-183">Inscrever-se de dispositivos com Android e iOS</span><span class="sxs-lookup"><span data-stu-id="2afee-183">Enroll iOS and Android devices</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="2afee-184">Configurar e testar o gerenciamento de segurança avançada</span><span class="sxs-lookup"><span data-stu-id="2afee-184">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="2afee-185">Configurar e testar a proteção de ameaça avançadas</span><span class="sxs-lookup"><span data-stu-id="2afee-185">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="2afee-186">Confira também</span><span class="sxs-lookup"><span data-stu-id="2afee-186">See Also</span></span>

- [<span data-ttu-id="2afee-187">Documentação do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="2afee-187">Microsoft 365 Enterprise documentation</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)

 - [<span data-ttu-id="2afee-188">Implantar o Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="2afee-188">Deploy Microsoft 365 Enterprise</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)

- [<span data-ttu-id="2afee-189">O ambiente de desenvolvimento e teste de um Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="2afee-189">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
