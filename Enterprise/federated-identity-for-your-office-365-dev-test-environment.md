---
title: Identidade federada para seu ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
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
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 'Resumo: configure a autenticação federada do ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: f028acb99d0687bb3fcfbc1c66bdd8885850565b
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915236"
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a><span data-ttu-id="fe6e4-103">Identidade federada para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="fe6e4-103">Federated identity for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="fe6e4-104">**Resumo:** configure a autenticação federada do ambiente de desenvolvimento/teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-104">**Summary:** Configure federated authentication for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="fe6e4-p101">O Office 365 dá suporte à identidade federada, ou seja, em vez de executar a validação de credenciais em si, o Office 365 refere-se a conectar o usuário a um servidor de autenticação federada em que o Office 365 confia. Se as credenciais do usuário estiverem corretas, o servidor de autenticação federada emite um token de segurança que o cliente envia ao Office 365 como prova de autenticação. A identidade federada permite a liberação e a ampliação da autenticação para uma assinatura do Office 365 e cenários avançados de autenticação e segurança.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p101">Office 365 supports federated identity. This means that instead of performing the validation of credentials itself, Office 365 refers the connecting user to a federated authentication server that Office 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Office 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for an Office 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="fe6e4-109">Este artigo descreve como você pode configurar a autenticação federada para o ambiente de desenvolvimento/teste do Office 365, resultando no seguinte:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-109">This article describes how you can configure federated authentication for the Office 365 dev/test environment, resulting in the following:</span></span>
  
<span data-ttu-id="fe6e4-110">**Figura 1: A autenticação federada para o ambiente de desenvolvimento/teste do Office 365.**</span><span class="sxs-lookup"><span data-stu-id="fe6e4-110">**Figure 1: The federated authentication for Office 365 dev/test environment**</span></span>

![A autenticação federada para o ambiente de desenvolvimento/teste do Office 365](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="fe6e4-112">A configuração mostrada na Figura 1 consiste em:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-112">The configuration shown in Figure 1 consists of:</span></span> 
  
- <span data-ttu-id="fe6e4-113">Uma assinatura de avaliação do Office 365 E5, que expira 30 dias depois de você criá-la.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-113">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="fe6e4-p102">Uma intranet simplificada da organização, conectada à Internet, consistindo em cinco máquinas virtuais na sub-rede de uma rede virtual Azure (DC1, APP1, CLIENT1, ADFS1 e PROXY1). O Azure AD Connect é executado no APP1 para sincronizar a lista de contas no domínio do AD do Windows Server ao Office 365. O PROXY1 recebe as solicitações de autenticação de entrada. O ADFS1 valida as credenciais com o DC1 e emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p102">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1). Azure AD Connect runs on APP1 to synchronize the list of accounts in the Windows Server AD domain to Office 365. PROXY1 receives the incoming authentication requests. ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="fe6e4-118">Há cinco fases para configurar esse ambiente de desenvolvimento/teste:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-118">There are five phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="fe6e4-119">Crie o ambiente de desenvolvimento/teste corporativo simulado do Office 365 com o DirSync.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-119">Create the simulated enterprise Office 365 dev/test environment with DirSync.</span></span>
    
2. <span data-ttu-id="fe6e4-120">Crie o servidor AD FS (ADFS1).</span><span class="sxs-lookup"><span data-stu-id="fe6e4-120">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="fe6e4-121">Crie o servidor de proxy da web (PROXY1).</span><span class="sxs-lookup"><span data-stu-id="fe6e4-121">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="fe6e4-122">Crie um certificado autoassinado e configure o ADFS1 e o PROXY1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-122">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="fe6e4-123">Configure o Office 365 com a identidade federada.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-123">Configure Office 365 for federated identity.</span></span>
    
<span data-ttu-id="fe6e4-124">Para passar pela implementação da produção da autenticação federada para o Office 365 no Azure, confira [Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="fe6e4-124">To step through a production deployment of federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="fe6e4-125">Você não pode configurar o ambiente de desenvolvimento/teste com uma assinatura de avaliação do Azure.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-125">You cannot configure this dev/test environment with an Azure Trial subscription.</span></span> 
  
> [!TIP]
> <span data-ttu-id="fe6e4-126">Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-126">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a><span data-ttu-id="fe6e4-127">Fase 1: Crie o ambiente de desenvolvimento/teste corporativo simulado do Office 365 com o DirSync.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-127">Phase 1: Create the simulated enterprise Office 365 dev/test environment with DirSync</span></span>

<span data-ttu-id="fe6e4-128">Siga as instruções em [Sincronização de diretório do ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md) para criar o ambiente de desenvolvimento/teste corporativo simulado do Office 365 com APP1 como o servidor do DirSync e identidade sincronizada entre o Office 365 e as contas do AD do Windows Server no DC1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-128">Follow the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to create the simulated enterprise Office 365 dev/test environment with APP1 as the DirSync server and synchronized identity between Office 365 and the Windows Server AD accounts on DC1.</span></span>
  
<span data-ttu-id="fe6e4-p103">Em seguida, crie um novo nome de domínio público DNS com base no nome de domínio atual e adicione-o à sua assinatura do Office 365. É recomendável usar o nome **testlab.**\<seu domínio público >. Por exemplo, se o nome de domínio público for contoso.com, adicione testlab.contoso.com como o nome de domínio público.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p103">Next, create a new public DNS domain name based on your current domain name and add it to your Office 365 subscription. We recommend using the name **testlab.**\<your public domain>. For example, if your public domain name is contoso.com, add the public domain name testlab.contoso.com.</span></span>
  
<span data-ttu-id="fe6e4-132">Para obter instruções sobre como criar os registros DNS corretos no seu provedor de DNS e adicionar o domínio à sua assinatura de avaliação do Office 365, confira [Adicionar usuários e domínios ao Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span><span class="sxs-lookup"><span data-stu-id="fe6e4-132">For instructions on how to create the correct DNS records in your DNS provider and add the domain to your Office 365 trial subscription, see [Add users and domain to Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span></span> 
  
<span data-ttu-id="fe6e4-133">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-133">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="fe6e4-134">**Figura 2: Sincronização de diretório do ambiente de desenvolvimento/teste do Office 365**</span><span class="sxs-lookup"><span data-stu-id="fe6e4-134">**Figure 2: Directory synchronization for the Office 365 dev/test environment**</span></span>

![Ambiente de desenvolvimento/de teste do Office 365 com a sincronização de diretório](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="fe6e4-136">A Figura 2 mostra a sincronização de diretório do ambiente de desenvolvimento/teste do Office 365 que inclui máquinas virtuais do Office 365 e CLIENT1, APP1, e DC1 em uma rede virtual Azure.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-136">Figure 2 shows the directory synchronizationc for Office 365 dev/test environment, which includes Office 365 and CLIENT1, APP1, and DC1 virtual machines in an Azure virtual network.</span></span>
  
## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="fe6e4-137">Fase 2: Criar o servidor AD FS</span><span class="sxs-lookup"><span data-stu-id="fe6e4-137">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="fe6e4-138">Um servidor do AD FS fornece autenticação federada entre o Office 365 e contas do domínio corp.contoso.com hospedado no DC1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-138">An AD FS server provides federated authentication between Office 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="fe6e4-139">Para criar uma máquina virtual do Azure para ADFS1, preencha o nome da assinatura e do grupo de recursos, o local do Azure para a Configuração da base e execute estes comandos no prompt de comando do Azure PowerShell no computador local.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-139">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$subscr="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Login-AzureRMAccount
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
$staticIP="10.0.0.100"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzureRMNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> <span data-ttu-id="fe6e4-140">Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) para obter um arquivo de texto contendo todos os comandos do Windows PowerShell neste artigo.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) for a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="fe6e4-141">Em seguida, use o [portal do Azure](http://portal.azure.com) para se conectar à máquina virtual do ADFS1 usando o nome da conta e a senha do administrador local do ADFS1, depois abra um prompt de comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-141">Next, use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="fe6e4-142">Para verificar a comunicação da rede e a resolução de nome entre ADFS1 e DC1, execute o comando **ping dc1.corp.contoso.com** e verifique se há quatro respostas.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-142">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="fe6e4-143">Em seguida, associe a máquina virtual do ADFS1 ao domínio CORP com estes comandos no prompt do Windows PowerShell no ADFS1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-143">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="fe6e4-144">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-144">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="fe6e4-145">**Figura 3: Adicionar o servidor AD FS**</span><span class="sxs-lookup"><span data-stu-id="fe6e4-145">**Figure 3: Adding the AD FS server**</span></span>

![O servidor AD FS adicionado ao DirSync para o ambiente de desenvolvimento/teste do Office 365](media/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
<span data-ttu-id="fe6e4-147">A Figura 3 mostra a adição do servidor ADFS1 ao DirSync para o ambiente de desenvolvimento/teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-147">Figure 3 shows the addition of the ADFS1 server to the DirSync for Office 365 dev/test environment.</span></span>
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="fe6e4-148">Fase 3: crie o servidor de proxy da web</span><span class="sxs-lookup"><span data-stu-id="fe6e4-148">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="fe6e4-149">O PROXY1 fornece proxy de mensagens de autenticação entre ADFS1 e os usuários que tentarem se autenticar.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-149">PROXY1 provides proxying of authentication messages between users attempting to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="fe6e4-150">Para criar uma máquina virtual do Azure para o PROXY1, preencha o nome do grupo de recursos e execute estes comandos no prompt de comando do Azure PowerShell no computador local.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-150">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzureRMNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="fe6e4-151">Um endereço IP estático público é atribuído ao PROXY1 porque você cria um registro DNS público que aponta para ele e não deverá ser alterado ao reiniciar a máquina virtual do PROXY1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-151">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="fe6e4-p104">Em seguida, adicione uma regra ao grupo de segurança de rede para a sub-rede da CorpNet para permitir o tráfego de entrada não solicitada da Internet para o endereço IP particular do PROXY1 e da porta 443 de TCP. Execute esses comandos no prompt de comando do Azure PowerShell no computador local.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p104">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

<span data-ttu-id="fe6e4-154">Em seguida, use o [portal do Azure](http://portal.azure.com) para se conectar à máquina virtual do PROXY1 usando o nome e a senha da conta do administrador local do PROXY1, depois abra um prompt de comando do Windows PowerShell no PROXY1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-154">Next, use the [Azure portal](http://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="fe6e4-155">Para verificar a comunicação da rede e a resolução de nome entre PROXY1 e DC1, execute o comando **ping dc1.corp.contoso.com** e verifique se há quatro respostas.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-155">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="fe6e4-156">Em seguida, associe a máquina virtual do PROXY1 ao domínio CORP com estes comandos no prompt do Windows PowerShell no PROXY1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-156">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="fe6e4-157">Exiba o endereço IP público do PROXY1 com estes comandos do Azure PowerShell no computador local:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-157">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="fe6e4-p105">Em seguida, trabalhe com seu provedor de DNS público e crie um novo registro público de DNS A para **fs.testlab.** \<seu nome de domínio DNS > que resolve o endereço IP exibido pelo comando **Write-Host**. De agora em diante, **fs.testlab.** \<seu nome de domínio DNS > é conhecido como o *FQDN do serviço de federação*.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p105">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*  .</span></span>
  
<span data-ttu-id="fe6e4-160">Em seguida, use o [portal do Azure](http://portal.azure.com) para se conectar à máquina virtual DC1 usando as credenciais CORP\\Usuário1 e execute este comando em um prompt de comando do Windows PowerShell de nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-160">Next, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

<span data-ttu-id="fe6e4-161">Esses comandos criam um registro DNS A para o seu FQDN do serviço de federação que as máquinas virtuais da rede virtual do Azure podem resolver o endereço IP privado do ADFS1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-161">These commands create a DNS A record for your federation service FQDN that virtual machines on the Azure virtual network can resolve to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="fe6e4-162">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-162">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="fe6e4-163">**Figura 4: Adicionar o servidor proxy de aplicativo web**</span><span class="sxs-lookup"><span data-stu-id="fe6e4-163">**Figure 4: Adding the web application proxy server**</span></span>

![O servidor proxy do aplicativo Web adicionado ao DirSync para o ambiente de desenvolvimento/teste do Office 365](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="fe6e4-165">A Figura 4 mostra a adição do servidor PROXY1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-165">Figure 4 shows the addition of the PROXY1 server.</span></span>
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="fe6e4-166">Fase 4: crie um certificado autoassinado e configure o ADFS1 e o PROXY1</span><span class="sxs-lookup"><span data-stu-id="fe6e4-166">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="fe6e4-167">Nesta fase, crie um certificado digital autoassinado para o seu FQDN de serviço de federação e configure o ADFS1 e o PROXY1 como um farm do AD FS.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-167">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="fe6e4-168">Em seguida, use o [portal do Azure](http://portal.azure.com) para se conectar à máquina virtual DC1 usando as credenciais CORP\\Usuário1 e abra um prompt de comando de nível de administrador do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-168">First, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="fe6e4-169">Depois crie a conta de serviço do AD FS usando esse comando no prompt de comando do Windows PowerShell em DC1:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-169">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="fe6e4-p106">Observe que esse comando solicita que você forneça a senha da conta. Escolha uma senha forte e anote-a em um local seguro. Você precisará dela neste fase e na fase 5.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p106">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="fe6e4-p107">Use o [portal do Azure](http://portal.azure.com) para se conectar à máquina virtual ADFS1 usando as credenciais CORP\\Usuário1. Abra um prompt de comando do Windows PowerShell de nível de administrador no ADFS1, preencha o FQDN de serviço de Federação e execute estes comandos para criar um certificado autoassinado:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p107">Use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

<span data-ttu-id="fe6e4-175">Em seguida, use estas etapas para salvar o novo certificado autoassinado como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-175">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="fe6e4-176">Clique em **Iniciar**, digite **mmc.exe** e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-176">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="fe6e4-177">Clique em **Arquivo > Adicionar/Remover Snap-in**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-177">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="fe6e4-178">Em **Adicionar/Remover Snap-in**, clique duas vezes em **Certificados** na lista de snap-ins disponíveis, clique em **Conta do computador** e em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-178">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="fe6e4-179">Em **Selecionar Computador**, clique em **Concluir** e em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-179">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="fe6e4-180">No painel da árvore, abra **Certificados (Computador Local) > Pessoal > Certificados**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-180">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="fe6e4-181">Clique com o botão direito do mouse no certificado com FQDN de serviço de federação, clique em **Todas as Tarefas** e em **Exportar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-181">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="fe6e4-182">Na página **Bem-vindo**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-182">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="fe6e4-183">Na página **Exportar Chave Privada**, clique em **Sim** e em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-183">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="fe6e4-184">Na página **Formato de Arquivo de Exportação**, clique em **Exportar Todas as Propriedades Estendidas** e em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-184">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="fe6e4-185">Na pagina **Segurança**, clique em **Senha**, digite uma senha em **Senha** e clique em **Confirmar Senha.**</span><span class="sxs-lookup"><span data-stu-id="fe6e4-185">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="fe6e4-186">Na página **Arquivo a Ser Exportado**, clique em **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-186">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="fe6e4-187">Navegue até a pasta **C:\\Certs**, digite **SSL** em **Nome do Arquivo** e clique em **Salvar.**</span><span class="sxs-lookup"><span data-stu-id="fe6e4-187">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="fe6e4-188">Na página **Arquivo a Ser Exportado**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-188">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="fe6e4-p108">Na página **Concluindo o Assistente para Exportação de Certificados**, clique em **Concluir** e, quando solicitado, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p108">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="fe6e4-191">Depois instale o serviço do AD FS usando esse comando no prompt de comando do Windows PowerShell em ADFS1:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-191">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="fe6e4-192">Aguarde a instalação ser concluída.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-192">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="fe6e4-193">Em seguida, configure o serviço do AD FS com estas etapas:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-193">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="fe6e4-194">Clique em **Iniciar** e no ícone **Gerenciador do Servidor**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-194">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="fe6e4-195">No painel da árvore do Gerenciador de Servidores, clique em **AD FS**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-195">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="fe6e4-196">Na barra de ferramentas, na parte superior, clique no símbolo de cuidado laranja e, em seguida, clique em **Configurar o Serviço de Federação neste Servidor**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-196">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="fe6e4-197">Na página **Bem-vindo** do Assistente de Configuração de Serviços de Federação do Active Directory (AD FS), clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-197">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="fe6e4-198">Na página **Conectar aos AD DS**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-198">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="fe6e4-199">Na página **Especificar Propriedades do Serviço**:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-199">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="fe6e4-200">Para o **Certificado SSL**, clique na seta para baixo e, em seguida, clique no certificado com o nome do seu FQDN de serviço de federação.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-200">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="fe6e4-201">No **Nome de Exibição de Serviços de Federação**, digite o nome da sua organização fictícia.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-201">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="fe6e4-202">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-202">Click **Next**.</span></span>
    
7. <span data-ttu-id="fe6e4-203">Na página **Especificar Conta de Serviço**, clique em **Selecionar** para **Nome da Conta**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-203">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="fe6e4-204">Em **Selecionar Usuário ou Conta de Serviço**, digite **Serviço ADFS**, clique em **Verificar Nomes** e em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-204">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="fe6e4-205">Em **Senha da Conta**, digite a senha da conta de serviço do ADFS e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-205">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="fe6e4-206">Na página **Especificar Banco de Dados de Configurações**, clique em **Avançar**:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-206">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="fe6e4-207">Na página **Opções de Revisão**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-207">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="fe6e4-208">Na página **Verificações de Pré-requisitos**, clique em **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-208">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="fe6e4-209">Na página **Resultados**, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-209">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="fe6e4-210">Clique em **Iniciar**, clique no ícone de Energia, clique em **Reiniciar** e, em seguida, em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-210">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="fe6e4-211">No [portal do Azure](http://portal.azure.com), conecte-se ao PROXY1 com as credenciais da conta CORP\\Usuário1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-211">From the [Azure portal](http://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="fe6e4-212">Em seguida, use estas etapas para instalar o certificado autoassinado e configurar o PROXY1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-212">Next, use these steps to install the self-signed certificate and configure PROXY1.</span></span>
  
1. <span data-ttu-id="fe6e4-213">Clique em **Iniciar**, digite **mmc.exe** e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-213">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="fe6e4-214">Clique em **Arquivo > Adicionar/Remover Snap-in**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-214">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="fe6e4-215">Em **Adicionar/Remover Snap-in**, clique duas vezes em **Certificados** na lista de snap-ins disponíveis, clique em **Conta do computador** e em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-215">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="fe6e4-216">Em **Selecionar Computador**, clique em **Concluir** e em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-216">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="fe6e4-217">No painel da árvore, abra **Certificados (Computador Local) > Pessoal > Certificados**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-217">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="fe6e4-218">Clique com o botão direito do mouse em **Pessoal**, selecione **Todas as Tarefas** e clique em **Importar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-218">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="fe6e4-219">Na página **Bem-vindo**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-219">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="fe6e4-220">Na página **Arquivo a Ser Importado**, digite**\\\\adfs1\\certs\\ssl.pfx** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-220">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="fe6e4-221">Na página **Proteção de Chave Privada**, digite a senha de certificado na **Senha** e, em seguida, clique em **Avançar.**</span><span class="sxs-lookup"><span data-stu-id="fe6e4-221">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="fe6e4-222">Na página **Repositório de certificados**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-222">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="fe6e4-223">Na página **Concluindo**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-223">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="fe6e4-224">Na página **Repositório de Certificados**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-224">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="fe6e4-225">Quando solicitado, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-225">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="fe6e4-226">Clique em **Certificados** no painel de árvore.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-226">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="fe6e4-227">Clique com o botão direito do mouse no certificado e depois em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-227">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="fe6e4-228">No painel de árvore, abra **Autoridades de Certificação Raiz Confiáveis > Certificados**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-228">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="fe6e4-229">Passe o ponteiro do cursor abaixo da lista de certificados instalados, clique com o botão direito do mouse e clique em **Colar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-229">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="fe6e4-230">Abra um prompt de comando do Windows PowerShell de nível de administrador e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-230">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="fe6e4-231">Aguarde a instalação ser concluída.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-231">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="fe6e4-232">Use estas etapas para configurar o serviço de proxy de aplicativo web para usar o ADFS1 como seu servidor de federação:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-232">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="fe6e4-233">Clique em **Iniciar** e em **Gerenciador do Servidor**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-233">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="fe6e4-234">No painel de árvore, clique em **Acesso Remoto**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-234">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="fe6e4-235">Na barra de ferramentas, na parte superior, clique no símbolo de cuidado laranja e, em seguida, clique em **Abrir o Assistente de Proxy de Aplicativo Web**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-235">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="fe6e4-236">Na página **Bem-vindo** do Assistente de Configuração do Proxy de Aplicativo Web, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-236">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="fe6e4-237">Na página **Servidor de Federação**:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-237">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="fe6e4-238">Digite o FQDN do serviço de federação em **Nome do Serviço de Federação**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-238">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="fe6e4-239">Digite **CORP\\Usuário1** no **Nome de Usuário**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-239">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="fe6e4-240">Digite a senha da conta do Usuário1 em **Senha**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-240">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="fe6e4-241">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-241">Click **Next**.</span></span>
    
6. <span data-ttu-id="fe6e4-242">Na página **Certificado Proxy AD FS**, clique na seta para baixo, clique no certificado com o nome do seu FQDN de serviço de federação e depois em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-242">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="fe6e4-243">Na página **Confirmação**, clique em **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-243">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="fe6e4-244">Na página **Resultados**, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-244">On the **Results** page, click **Close**.</span></span>
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a><span data-ttu-id="fe6e4-245">Fase 5: Configurar o Office 365 para a identidade federada</span><span class="sxs-lookup"><span data-stu-id="fe6e4-245">Phase 5: Configure Office 365 for federated identity</span></span>

<span data-ttu-id="fe6e4-246">Use o [portal do Azure](http://portal.azure.com) para conectar a máquina virtual APP1 com as credenciais da conta CORP\\Usuário1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-246">Use the [Azure portal](http://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="fe6e4-247">Use estas etapas para configurar o Azure AD Connect e sua assinatura do Office 365 para autenticação federada:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-247">Use these steps to configure Azure AD Connect and your Office 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="fe6e4-248">Na área de trabalho, clique duas vezes em **Azure AD Connect**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-248">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="fe6e4-249">Na página **Bem-vindo ao Azure AD Connect**, clique em **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-249">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="fe6e4-250">Na página **Tarefas Adicionais**, clique em **Alterar entrada do usuário** e em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-250">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="fe6e4-251">Na página **Conectar ao Azure AD**, digite o nome de sua conta e a senha de administrador global do Office 365 e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-251">On the **Connect to Azure AD** page, type your Office 365 global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="fe6e4-252">Na página **Entrada do usuário**, clique em **Federação com AD FS** e em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-252">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="fe6e4-253">Na página **Farm do AD FS**, clique em **Usar um farm do AD FS existente**, digite **ADFS1** no **Nome do servidor** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-253">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="fe6e4-254">Nas credenciais do servidor, insira as credenciais da conta CORP\\Usuário1 e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-254">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="fe6e4-255">Na página de credenciais **Administrador de domínio**, digite **CORP\\Usuário1** no **Nome de usuário** e a senha da conta em **Senha** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-255">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="fe6e4-256">Na página **Conta de Serviço do AD FS**, digite **CORP\\ADFS serviço** no **Nome de Usuário de Domínio** e a senha da conta em **Senha de Usuário de Domínio** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-256">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="fe6e4-257">Na página **Domínio do Azure AD**, em **Domínio**, selecione o nome do domínio que você criou anteriormente e adicionou à sua assinatura do Office 365 na fase 1 e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-257">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your Office 365 subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="fe6e4-258">Na página **Pronto para configurar**, clique em **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-258">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="fe6e4-259">Na página **Instalação Completa**, clique em **Verificar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-259">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="fe6e4-260">Você verá mensagens indicando que as configurações da intranet e da Internet foram verificadas.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-260">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="fe6e4-261">Na página **Instalação Completa**, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-261">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="fe6e4-262">Para demonstrar que a autenticação federada está funcionando, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-262">To demonstrate that federated authentication is working, do the following:</span></span>
  
1. <span data-ttu-id="fe6e4-263">Abra uma nova instância privada no navegador do computador local e acesse [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="fe6e4-263">Open a new private instance of your browser on your local computer and go to [https://portal.office.com](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="fe6e4-264">Como credenciais de entrada, digite **usuário1@**\<domínio criado na Fase 1 >.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-264">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="fe6e4-p109">Por exemplo, se o domínio de teste for **testlab.contoso.com**, digite **usuário1@testlab.contoso.com**. Pressione a tecla TAB ou deixe que o Office 365 o redirecione automaticamente.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p109">For example, if your test domain is **testlab.contoso.com**, you would type **user1@testlab.contoso.com**. Press TAB or allow Office 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="fe6e4-p110">Agora você deverá ver a página **Sua conexão não é particular** porque você instalou o certificado autoassinado em ADFS1 que seu computador desktop não consegue validar. Em uma implantação de produção com autenticação federada, será necessário usar um certificado de autoridade de certificação confiável e os usuários não verão esta página.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p110">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="fe6e4-270">Na página **Sua conexão não é particular**, clique em **Avançado** e em **Vá para \<FQDN do seu serviço de federação>**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-270">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="fe6e4-271">Na página com o nome da sua organização fictícia, entre com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-271">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="fe6e4-272">**CORP\\Usuário1** como o nome</span><span class="sxs-lookup"><span data-stu-id="fe6e4-272">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="fe6e4-273">A senha da conta Usuário1</span><span class="sxs-lookup"><span data-stu-id="fe6e4-273">The password for the User1 account</span></span>
    
    <span data-ttu-id="fe6e4-274">Você verá a página **Microsoft Office Home**.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-274">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="fe6e4-p111">Esse procedimento demonstra que sua assinatura de avaliação do Office 365 está federada com o domínio corp.contoso.com do AD do Windows Server hospedado no DC1. Veja abaixo as noções básicas do processo de autenticação:</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p111">This procedure demonstrates that your Office 365 trial subscription is federated with the Windows Server AD corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="fe6e4-277">Ao usar o domínio federado criado na Fase 1 como o nome da conta de entrada, o Office 365 redireciona o navegador para o PROXY1 e FQDN do serviço da federação.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-277">When you use the federated domain that you created in Phase 1 within the sign-in account name, Office 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="fe6e4-278">PROXY1 envia a página de entrada da empresa fictícia para o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-278">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="fe6e4-279">Quando você envia CORP\\Usuário1 e a senha PROXY1, ele o encaminha para o ADFS1.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-279">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="fe6e4-280">O ADFS1 valida CORP\\Usuário1 e a senha com o DC1 e envia um token de segurança para o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-280">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="fe6e4-281">O computador local envia o token de segurança ao Office 365.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-281">Your local computer sends the security token to Office 365.</span></span>
    
6. <span data-ttu-id="fe6e4-282">O Office 365 valida o token de segurança criado por ADFS1 e permite o acesso.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-282">Office 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="fe6e4-p112">Agora a assinatura de avaliação do Office 365 está configurada com a autenticação federada. Você pode usar esse ambiente de desenvolvimento/teste em cenários avançados de autenticação.</span><span class="sxs-lookup"><span data-stu-id="fe6e4-p112">Your Office 365 trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="fe6e4-285">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="fe6e4-285">Next Step</span></span>

<span data-ttu-id="fe6e4-286">Quando estiver pronto para a implementação da autenticação federada pronta para a produção e de alta disponibilidade para o Office 365 no Azure, confira [Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="fe6e4-286">When you are ready to deploy production-ready, high availability federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fe6e4-287">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe6e4-287">See Also</span></span>

[<span data-ttu-id="fe6e4-288">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="fe6e4-288">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
<span data-ttu-id="fe6e4-289">[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="fe6e4-289">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="fe6e4-290">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="fe6e4-290">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="fe6e4-291">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="fe6e4-291">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="fe6e4-292">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="fe6e4-292">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


