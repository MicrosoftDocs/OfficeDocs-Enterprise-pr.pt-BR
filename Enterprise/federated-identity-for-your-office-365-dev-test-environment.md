---
title: Identidade federada para seu ambiente de desenvolvimento e teste do Office 365
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
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: "Resumo: Configure a autenticação federada para seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: e37b57d5497f3151885682f7c4d8abca7120b99e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a><span data-ttu-id="e644d-103">Identidade federada para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e644d-103">Federated identity for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="e644d-104">**Resumo:** Configure autenticação federada para seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e644d-104">**Summary:** Configure federated authentication for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e644d-p101">Office 365 oferece suporte a identidade federada. Isso significa que em vez de executar a validação de credenciais em si, Office 365 se refere ao usuário se conectando a um servidor de autenticação federada relações de confiança do Office 365. Se as credenciais do usuário estão corretas, o servidor de autenticação federada emite um token de segurança que envia o cliente para o Office 365 como prova de autenticação. Identidade federada permite o descarregamento e expansão de autenticação para uma assinatura do Office 365 e cenários de autenticação e segurança avançada.</span><span class="sxs-lookup"><span data-stu-id="e644d-p101">Office 365 supports federated identity. This means that instead of performing the validation of credentials itself, Office 365 refers the connecting user to a federated authentication server that Office 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Office 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for an Office 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="e644d-109">Este artigo descreve como você pode configurar a autenticação federada para o ambiente de desenvolvimento e teste do Office 365, resultando no seguinte:</span><span class="sxs-lookup"><span data-stu-id="e644d-109">This article describes how you can configure federated authentication for the Office 365 dev/test environment, resulting in the following:</span></span>
  
<span data-ttu-id="e644d-110">**Figura 1: A autenticação federada para o ambiente de desenvolvimento e teste do Office 365**</span><span class="sxs-lookup"><span data-stu-id="e644d-110">**Figure 1: The federated authentication for Office 365 dev/test environment**</span></span>

![O servidor proxy do aplicativo Web adicionado ao DirSync para o ambiente de desenvolvimento/teste do Office 365](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="e644d-112">A configuração mostrada na Figura 1 consiste em:</span><span class="sxs-lookup"><span data-stu-id="e644d-112">The configuration shown in Figure 1 consists of:</span></span> 
  
- <span data-ttu-id="e644d-113">Um Office 365 E5 avaliação assinatura, que expira 30 dias a partir de quando você criá-lo.</span><span class="sxs-lookup"><span data-stu-id="e644d-113">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="e644d-p102">Uma intranet da organização simplificado conectado à Internet, consistindo em cinco máquinas virtuais em uma sub-rede de uma rede virtual do Azure (DC1, APP1, CLIENT1, ADFS1 e PROXY1). Conectar do Azure AD executa no APP1 para sincronizar a lista de contas no domínio AD do Windows Server para o Office 365. PROXY1 recebe as solicitações de autenticação de entrada. ADFS1 valida credenciais com DC1 e emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="e644d-p102">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1). Azure AD Connect runs on APP1 to synchronize the list of accounts in the Windows Server AD domain to Office 365. PROXY1 receives the incoming authentication requests. ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="e644d-118">Há cinco fases para configurar esse ambiente de desenvolvimento e teste:</span><span class="sxs-lookup"><span data-stu-id="e644d-118">There are five phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="e644d-119">Crie o ambiente de desenvolvimento e teste simulado enterprise Office 365 com o DirSync.</span><span class="sxs-lookup"><span data-stu-id="e644d-119">Create the simulated enterprise Office 365 dev/test environment with DirSync.</span></span>
    
2. <span data-ttu-id="e644d-120">Crie um servidor AD FS (ADFS1).</span><span class="sxs-lookup"><span data-stu-id="e644d-120">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="e644d-121">Crie o servidor de proxy da web (PROXY1).</span><span class="sxs-lookup"><span data-stu-id="e644d-121">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="e644d-122">Criar um certificado autoassinado e configure ADFS1 e PROXY1.</span><span class="sxs-lookup"><span data-stu-id="e644d-122">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="e644d-123">Configure o Office 365 para identidade federada.</span><span class="sxs-lookup"><span data-stu-id="e644d-123">Configure Office 365 for federated identity.</span></span>
    
<span data-ttu-id="e644d-124">Para depurar uma implantação de produção da autenticação federada para o Office 365 no Windows Azure, consulte [Deploy autenticação federada do alta disponibilidade para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="e644d-124">To step through a production deployment of federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e644d-125">Você não pode configurar esse ambiente de desenvolvimento e teste com uma assinatura de avaliação do Azure.</span><span class="sxs-lookup"><span data-stu-id="e644d-125">You cannot configure this dev/test environment with an Azure Trial subscription.</span></span> 
  
> [!TIP]
> <span data-ttu-id="e644d-126">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="e644d-126">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a><span data-ttu-id="e644d-127">Fase 1: Criar o ambiente de desenvolvimento e teste simulado enterprise Office 365 com DirSync</span><span class="sxs-lookup"><span data-stu-id="e644d-127">Phase 1: Create the simulated enterprise Office 365 dev/test environment with DirSync</span></span>

<span data-ttu-id="e644d-128">Siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md) para criar o ambiente de desenvolvimento e teste simulado enterprise Office 365 com APP1 como o servidor de DirSync e a identidade sincronizada entre o Office 365 e o Windows Server AD contas no DC1.</span><span class="sxs-lookup"><span data-stu-id="e644d-128">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to create the simulated enterprise Office 365 dev/test environment with APP1 as the DirSync server and synchronized identity between Office 365 and the Windows Server AD accounts on DC1.</span></span>
  
<span data-ttu-id="e644d-p103">Em seguida, crie um novo nome de domínio público DNS com base em seu nome de domínio atual e adicioná-lo à sua assinatura do Office 365. É recomendável usar o nome **laboratório de teste.** \<seu domínio público >. Por exemplo, se seu nome de domínio público for contoso.com, adicione o testlab.contoso.com de nome de domínio público.</span><span class="sxs-lookup"><span data-stu-id="e644d-p103">Next, create a new public DNS domain name based on your current domain name and add it to your Office 365 subscription. We recommend using the name **testlab.**\<your public domain>. For example, if your public domain name is contoso.com, add the public domain name testlab.contoso.com.</span></span>
  
<span data-ttu-id="e644d-132">Para obter instruções sobre como criar os registros DNS corretos no seu provedor de DNS e adicionar o domínio à sua assinatura de avaliação do Office 365, consulte [Adicionar usuários e o domínio ao Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span><span class="sxs-lookup"><span data-stu-id="e644d-132">For instructions on how to create the correct DNS records in your DNS provider and add the domain to your Office 365 trial subscription, see [Add users and domain to Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span></span> 
  
<span data-ttu-id="e644d-133">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="e644d-133">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="e644d-134">**Figura 2: DirSync para o ambiente de desenvolvimento e teste do Office 365**</span><span class="sxs-lookup"><span data-stu-id="e644d-134">**Figure 2: DirSync for Office 365 dev/test environment**</span></span>

![O ambiente de desenvolvimento e teste do Office 365 com o DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="e644d-136">A Figura 2 mostra o DirSync para ambiente de desenvolvimento e teste do Office 365, que inclui máquinas virtuais do Office 365 e CLIENT1, APP1 e DC1 em uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="e644d-136">Figure 2 shows the DirSync for Office 365 dev/test environment, which includes Office 365 and CLIENT1, APP1, and DC1 virtual machines in an Azure virtual network.</span></span>
  
## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="e644d-137">Fase 2: Criar um servidor AD FS</span><span class="sxs-lookup"><span data-stu-id="e644d-137">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="e644d-138">Um servidor AD FS fornece autenticação federada entre o Office 365 e as contas no domínio corp.contoso.com hospedado em DC1.</span><span class="sxs-lookup"><span data-stu-id="e644d-138">An AD FS server provides federated authentication between Office 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="e644d-139">Para criar uma máquina virtual do Azure para ADFS1, preencher no nome de sua assinatura e o grupo de recursos e o Azure local para sua configuração básica e, em seguida, execute estes comandos no prompt de comando do PowerShell do Azure no computador local.</span><span class="sxs-lookup"><span data-stu-id="e644d-139">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> <span data-ttu-id="e644d-140">Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) para obter um arquivo de texto que contém todos os comandos do PowerShell neste artigo.</span><span class="sxs-lookup"><span data-stu-id="e644d-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="e644d-141">Em seguida, usar o [portal do Windows Azure](http://portal.azure.com) para conectar-se à máquina virtual ADFS1 usando o nome de conta de administrador local ADFS1 e a senha e, em seguida, abra um prompt de comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e644d-141">Next, use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e644d-142">Para verificar a comunicação de rede e resolução de nome entre ADFS1 e DC1, execute o comando **ping dc1.corp.contoso.com** e verifique se há quatro respostas.</span><span class="sxs-lookup"><span data-stu-id="e644d-142">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="e644d-143">Em seguida, ingresse ADFS1 máquina virtual ao domínio CORP com esses comandos no prompt do Windows PowerShell no ADFS1.</span><span class="sxs-lookup"><span data-stu-id="e644d-143">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="e644d-144">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="e644d-144">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="e644d-145">**Figura 3: Adicionar o servidor do AD FS**</span><span class="sxs-lookup"><span data-stu-id="e644d-145">**Figure 3: Adding the AD FS server**</span></span>

![O servidor AD FS adicionado ao DirSync para o ambiente de desenvolvimento/teste do Office 365](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
<span data-ttu-id="e644d-147">A Figura 3 mostra a adição do servidor ADFS1 para DirSync para o ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e644d-147">Figure 3 shows the addition of the ADFS1 server to the DirSync for Office 365 dev/test environment.</span></span>
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="e644d-148">Fase 3: Criar o servidor de proxy da web</span><span class="sxs-lookup"><span data-stu-id="e644d-148">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="e644d-149">PROXY1 fornece um proxy de mensagens de autenticação entre usuários tentando autenticar e ADFS1.</span><span class="sxs-lookup"><span data-stu-id="e644d-149">PROXY1 provides proxying of authentication messages between users attempting to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="e644d-150">Para criar uma máquina virtual do Azure para PROXY1, preencher no nome de seu grupo de recursos e o Azure local e, em seguida, execute estes comandos no prompt de comando do PowerShell do Azure no computador local.</span><span class="sxs-lookup"><span data-stu-id="e644d-150">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="e644d-151">PROXY1 é atribuída a um endereço IP estático e público porque você criará um registro DNS público que aponta para ele e ele não deve alterar quando você reiniciar a máquina virtual PROXY1.</span><span class="sxs-lookup"><span data-stu-id="e644d-151">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="e644d-p104">Em seguida, adicione uma regra para o grupo de segurança de rede para a sub-rede da rede corporativa para permitir o tráfego de entrada não solicitado da Internet para o endereço IP particular do PROXY1 e a porta TCP 443. Execute estes comandos no prompt de comando do PowerShell do Azure no computador local.</span><span class="sxs-lookup"><span data-stu-id="e644d-p104">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

<span data-ttu-id="e644d-154">Em seguida, usar o [portal do Windows Azure](http://portal.azure.com) para conectar-se à máquina virtual PROXY1 usando o nome de conta de administrador local PROXY1 e a senha e, em seguida, abra um prompt de comando do Windows PowerShell em PROXY1.</span><span class="sxs-lookup"><span data-stu-id="e644d-154">Next, use the [Azure portal](http://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="e644d-155">Para verificar a comunicação de rede e resolução de nome entre PROXY1 e DC1, execute o comando **ping dc1.corp.contoso.com** e verifique se há quatro respostas.</span><span class="sxs-lookup"><span data-stu-id="e644d-155">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="e644d-156">Em seguida, ingresse PROXY1 máquina virtual ao domínio CORP com esses comandos no prompt do Windows PowerShell no PROXY1.</span><span class="sxs-lookup"><span data-stu-id="e644d-156">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="e644d-157">Exiba o endereço IP público do PROXY1 com estes comandos do PowerShell do Windows Azure no computador local:</span><span class="sxs-lookup"><span data-stu-id="e644d-157">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="e644d-p105">Em seguida, trabalhar com seu provedor de DNS público e criar um novo registro DNS A pública para **fs.testlab.** \<seu nome de domínio DNS > que se resolva como o endereço IP exibido pelo comando **Write-Host** . O **fs.testlab.** \<seu nome de domínio DNS > é citado como o *FQDN do serviço de Federação* .</span><span class="sxs-lookup"><span data-stu-id="e644d-p105">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*  .</span></span>
  
<span data-ttu-id="e644d-160">Em seguida, usar o [portal do Azure](http://portal.azure.com) para conectar-se à máquina virtual DC1 usando a CORP\\User1 credenciais e execute os seguintes comandos em um prompt de comando do Windows PowerShell de nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="e644d-160">Next, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

<span data-ttu-id="e644d-161">Esses comandos criam um registro DNS A para seu serviço de Federação FQDN máquinas virtuais em uma rede virtual Azure pode resolver para o endereço IP particular do ADFS1.</span><span class="sxs-lookup"><span data-stu-id="e644d-161">These commands create a DNS A record for your federation service FQDN that virtual machines on the Azure virtual network can resolve to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="e644d-162">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="e644d-162">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="e644d-163">**Figura 4: Adicionar o servidor de proxy de aplicativo web**</span><span class="sxs-lookup"><span data-stu-id="e644d-163">**Figure 4: Adding the web application proxy server**</span></span>

![O servidor proxy do aplicativo Web adicionado ao DirSync para o ambiente de desenvolvimento/teste do Office 365](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="e644d-165">Figura 4 mostra a adição do servidor PROXY1.</span><span class="sxs-lookup"><span data-stu-id="e644d-165">Figure 4 shows the addition of the PROXY1 server.</span></span>
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="e644d-166">Fase 4: Criar um certificado autoassinado e configurar ADFS1 e PROXY1</span><span class="sxs-lookup"><span data-stu-id="e644d-166">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="e644d-167">Nesta fase, você cria um certificado digital autoassinado para seu serviço de Federação FQDN e configure ADFS1 e PROXY1 como um farm do AD FS.</span><span class="sxs-lookup"><span data-stu-id="e644d-167">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="e644d-168">Primeiro, use o [portal do Windows Azure](http://portal.azure.com) para conectar-se a máquina virtual DC1 usando a CORP\\User1 credenciais e, então, abra um nível de administrador Windows PowerShell prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e644d-168">First, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e644d-169">Em seguida, crie a conta de serviço do AD FS com este comando no prompt de comando do Windows PowerShell no DC1:</span><span class="sxs-lookup"><span data-stu-id="e644d-169">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="e644d-p106">Observe que este comando solicitará que você forneça a senha da conta. Escolha uma senha forte e registre-a em um local seguro. Você precisará dele para esta fase e a fase 5.</span><span class="sxs-lookup"><span data-stu-id="e644d-p106">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="e644d-p107">Usar o [portal do Windows Azure](http://portal.azure.com) para conectar-se à máquina virtual ADFS1 usando CORP\\User1 credenciais. Abra um prompt de comando do Windows PowerShell de nível de administrador em ADFS1, preencha o FQDN do serviço de Federação e, em seguida, execute estes comandos para criar um certificado autoassinado:</span><span class="sxs-lookup"><span data-stu-id="e644d-p107">Use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\\LocalMachine\\My"
New-Item -path c:\\Certs -type directory
New-SmbShare -name Certs -path c:\\Certs -changeaccess CORP\\User1
```

<span data-ttu-id="e644d-175">Em seguida, execute estas etapas para salvar o novo certificado autoassinado como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e644d-175">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="e644d-176">Clique em **Iniciar**, digite **mmc.exe**e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="e644d-176">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="e644d-177">Clique em **arquivo > Adicionar/Remover Snap-in**.</span><span class="sxs-lookup"><span data-stu-id="e644d-177">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="e644d-178">Em **Adicionar ou Remover Snap-ins**, clique duas vezes em **certificados** na lista de snap-ins disponíveis, clique em **conta de computador**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-178">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="e644d-179">Em **Selecionar computador**, clique em **Concluir**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e644d-179">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e644d-180">No painel de árvore, abra **certificados (computador Local) > pessoal > certificados**.</span><span class="sxs-lookup"><span data-stu-id="e644d-180">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="e644d-181">Com o botão direito o certificado com seu FQDN do serviço de federação, clique em **All tasks**e clique em **Exportar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-181">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="e644d-182">Na página de **boas-vindas** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-182">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="e644d-183">Na página **Exportar chave particular** , clique em **Sim**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-183">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e644d-184">Na página **Exportar formato de arquivo** , clique em **Exportar todas as propriedades estendidas**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-184">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="e644d-185">Na página **segurança** , clique em **senha** e digite uma senha na **senha** e **Confirmar senha.**</span><span class="sxs-lookup"><span data-stu-id="e644d-185">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="e644d-186">Na página **arquivo a ser exportado** , clique em **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-186">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="e644d-187">Navegue até o **c:\\certificados** pasta, digite **SSL** em **nome do arquivo**e, em seguida, clique em **Salvar.**</span><span class="sxs-lookup"><span data-stu-id="e644d-187">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="e644d-188">Na página **arquivo a ser exportado** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-188">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="e644d-p108">Na página **Concluindo o Assistente para exportação de certificados** , clique em **Concluir**. Quando solicitado, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e644d-p108">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="e644d-191">Em seguida, instale o serviço AD FS com este comando no prompt de comando do Windows PowerShell em ADFS1:</span><span class="sxs-lookup"><span data-stu-id="e644d-191">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="e644d-192">Aguarde a conclusão da instalação.</span><span class="sxs-lookup"><span data-stu-id="e644d-192">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="e644d-193">Em seguida, configure o serviço AD FS com estas etapas:</span><span class="sxs-lookup"><span data-stu-id="e644d-193">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="e644d-194">Clique em **Iniciar**e, em seguida, clique no ícone do **Gerenciador de servidores** .</span><span class="sxs-lookup"><span data-stu-id="e644d-194">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="e644d-195">No painel da árvore do Gerenciador de servidores, clique em **AD FS**.</span><span class="sxs-lookup"><span data-stu-id="e644d-195">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="e644d-196">Na barra de ferramentas na parte superior, clique no símbolo de cuidado laranja e, em seguida, clique em **Configurar o serviço de Federação nesse servidor**.</span><span class="sxs-lookup"><span data-stu-id="e644d-196">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="e644d-197">Na página de **boas-vindas** do Assistente de configuração de serviços de Federação Active Directory, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-197">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="e644d-198">Na página **conectar ao AD DS** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-198">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="e644d-199">Na página **Especificar propriedades do serviço** :</span><span class="sxs-lookup"><span data-stu-id="e644d-199">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="e644d-200">Para o **Certificado SSL**, clique na seta para baixo e, em seguida, clique no certificado com o nome do seu serviço de Federação FQDN.</span><span class="sxs-lookup"><span data-stu-id="e644d-200">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="e644d-201">Em **Nome de exibição do serviço de Federação**, digite o nome da sua organização a empresa fictícia.</span><span class="sxs-lookup"><span data-stu-id="e644d-201">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="e644d-202">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-202">Click **Next**.</span></span>
    
7. <span data-ttu-id="e644d-203">Na página **Especificar a conta de serviço** , clique em **Selecionar** para o **nome da conta**.</span><span class="sxs-lookup"><span data-stu-id="e644d-203">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="e644d-204">Em **Selecionar usuário ou conta de serviço**, digite **Serviço ADFS**, clique em **Verificar nomes**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e644d-204">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="e644d-205">Em **Senha da conta**, digite a senha da conta de serviço do ADFS e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-205">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="e644d-206">Na página **Especificar banco de dados de configuração** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-206">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="e644d-207">Na página **Opções de revisão** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-207">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="e644d-208">Na página **Verificações de pré-requisito** , clique em **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-208">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="e644d-209">Na página de **resultados** , clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-209">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="e644d-210">Clique em **Iniciar**, clique no ícone de energia, clique em **Reiniciar**e, em seguida, clique em **continuar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-210">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="e644d-211">No [portal do Azure](http://portal.azure.com), se conectar ao PROXY1 com CORP\\credenciais de conta User1.</span><span class="sxs-lookup"><span data-stu-id="e644d-211">From the [Azure portal](http://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="e644d-212">Em seguida, execute estas etapas para instalar o certificado autoassinado e configurar PROXY1.</span><span class="sxs-lookup"><span data-stu-id="e644d-212">Next, use these steps to install the self-signed certificate and configure PROXY1.</span></span>
  
1. <span data-ttu-id="e644d-213">Clique em **Iniciar**, digite **mmc.exe**e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="e644d-213">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="e644d-214">Clique em **arquivo > Adicionar/Remover Snap-in**.</span><span class="sxs-lookup"><span data-stu-id="e644d-214">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="e644d-215">Em **Adicionar ou Remover Snap-ins**, clique duas vezes em **certificados** na lista de snap-ins disponíveis, clique em **conta de computador**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-215">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="e644d-216">Em **Selecionar computador**, clique em **Concluir**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e644d-216">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e644d-217">No painel de árvore, abra **certificados (computador Local) > pessoal > certificados**.</span><span class="sxs-lookup"><span data-stu-id="e644d-217">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="e644d-218">Clique com o botão **pessoais**, clique em **All tasks**e, em seguida, clique em **Importar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-218">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="e644d-219">Na página de **boas-vindas** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-219">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="e644d-220">Na página **arquivo a ser importado** , digite ** \\ \\adfs1\\certificados\\ssl.pfx**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-220">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e644d-221">Na página de **proteção de chave privada** , digite a senha do certificado na **senha**e, em seguida, clique em **próxima.**</span><span class="sxs-lookup"><span data-stu-id="e644d-221">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="e644d-222">Na página **repositório de certificado** , clique em **próxima.**</span><span class="sxs-lookup"><span data-stu-id="e644d-222">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="e644d-223">Na página **Concluindo** , clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="e644d-223">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="e644d-224">Na página **Repositório de certificados** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-224">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="e644d-225">Quando solicitado, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e644d-225">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="e644d-226">No painel de árvore, clique em **certificados** .</span><span class="sxs-lookup"><span data-stu-id="e644d-226">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="e644d-227">Com o botão direito no certificado e, em seguida, clique em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-227">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="e644d-228">No painel de árvore, abra **autoridades de certificação raiz confiáveis > certificados**.</span><span class="sxs-lookup"><span data-stu-id="e644d-228">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="e644d-229">Mover o ponteiro do mouse abaixo da lista de certificados instalados, com o botão direito e depois clique em **Colar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-229">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="e644d-230">Abra um prompt de comando do PowerShell de nível de administrador e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e644d-230">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="e644d-231">Aguarde a conclusão da instalação.</span><span class="sxs-lookup"><span data-stu-id="e644d-231">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="e644d-232">Use estas etapas para configurar o serviço de proxy de aplicativo web para usar ADFS1 como seu servidor de Federação:</span><span class="sxs-lookup"><span data-stu-id="e644d-232">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="e644d-233">Clique em **Iniciar**e, em seguida, clique em **Gerenciador de servidores**.</span><span class="sxs-lookup"><span data-stu-id="e644d-233">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="e644d-234">No painel de árvore, clique em **Acesso remoto**.</span><span class="sxs-lookup"><span data-stu-id="e644d-234">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="e644d-235">Na barra de ferramentas na parte superior, clique no símbolo de cuidado laranja e clique em **Abrir o Assistente de Proxy de aplicativo Web**.</span><span class="sxs-lookup"><span data-stu-id="e644d-235">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="e644d-236">Na página de **boas-vindas** do Assistente de configuração de Proxy de aplicativo Web, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-236">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="e644d-237">Na página **Servidor de Federação** :</span><span class="sxs-lookup"><span data-stu-id="e644d-237">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="e644d-238">Digite o FQDN do serviço de federação no **nome do serviço de Federação**.</span><span class="sxs-lookup"><span data-stu-id="e644d-238">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="e644d-239">Tipo **CORP\\User1** em **nome de usuário**.</span><span class="sxs-lookup"><span data-stu-id="e644d-239">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="e644d-240">Digite a senha para a conta User1 na **senha**.</span><span class="sxs-lookup"><span data-stu-id="e644d-240">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="e644d-241">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-241">Click **Next**.</span></span>
    
6. <span data-ttu-id="e644d-242">Na página **Certificado de Proxy do AD FS** , clique na seta para baixo, clique no certificado com o FQDN do serviço de Federação e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-242">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="e644d-243">Na página de **confirmação** , clique em **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-243">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="e644d-244">Na página de **resultados** , clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-244">On the **Results** page, click **Close**.</span></span>
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a><span data-ttu-id="e644d-245">Fase 5: Configurar o Office 365 para identidades federadas</span><span class="sxs-lookup"><span data-stu-id="e644d-245">Phase 5: Configure Office 365 for federated identity</span></span>

<span data-ttu-id="e644d-246">Usar o [portal do Azure](http://portal.azure.com) para conectar-se a máquina virtual APP1 com CORP\\credenciais de conta User1.</span><span class="sxs-lookup"><span data-stu-id="e644d-246">Use the [Azure portal](http://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="e644d-247">Use estas etapas para configurar Connect do Azure AD e sua assinatura do Office 365 para autenticação federada:</span><span class="sxs-lookup"><span data-stu-id="e644d-247">Use these steps to configure Azure AD Connect and your Office 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="e644d-248">Na área de trabalho, clique duas vezes em **Connect do Azure AD**.</span><span class="sxs-lookup"><span data-stu-id="e644d-248">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="e644d-249">Na página **Bem-vindo ao conectar do Azure AD** , clique em **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-249">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="e644d-250">Na página **tarefas adicionais** , clique em **Alterar usuário entrar**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-250">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="e644d-251">Na página **conectar ao AD do Windows Azure** , digite seu nome de conta de administrador global do Office 365 e a senha e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-251">On the **Connect to Azure AD** page, type your Office 365 global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="e644d-252">Na página de **logon do usuário** , clique em **federação com o AD FS**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-252">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="e644d-253">Na página **farm AD FS** , clique em **usar um farm existente do AD FS**, digite **ADFS1** em **Nome do servidor**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-253">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="e644d-254">Quando solicitado a fornecer credenciais do servidor, insira as credenciais de CORP\\User1 da conta e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e644d-254">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="e644d-255">Na página credenciais de **Administrador de domínio** , digite **CORP\\User1** no **nome de usuário** e a senha da conta em **senha**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-255">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e644d-256">Na página **conta de serviço do AD FS** , digite **CORP\\serviço ADFS** no **Nome de usuário de domínio** e a senha da conta em **Senha de usuário de domínio**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-256">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="e644d-257">Na página **Domínio do Windows Azure AD** , no **domínio**, selecione o nome do domínio que você criou anteriormente e adicionado à sua assinatura do Office 365 na fase 1 e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-257">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your Office 365 subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="e644d-258">Na página **pronto para configurar** , clique em **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-258">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="e644d-259">Na página **instalação concluída** , clique em **Verificar**.</span><span class="sxs-lookup"><span data-stu-id="e644d-259">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="e644d-260">Você deverá ver mensagens indicando que a intranet e a Internet configuração foi verificada.</span><span class="sxs-lookup"><span data-stu-id="e644d-260">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="e644d-261">Na página **instalação concluída** , clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="e644d-261">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="e644d-262">Para demonstrar que a autenticação federada está funcionando, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e644d-262">To demonstrate that federated authentication is working, do the following:</span></span>
  
1. <span data-ttu-id="e644d-263">Abra uma nova instância particular do navegador no computador local e vá para [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="e644d-263">Open a new private instance of your browser on your local computer and go to [https://portal.office.com](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="e644d-264">Para as credenciais de login, digite **Usuário1 @**\<o domínio criado na fase 1 >.</span><span class="sxs-lookup"><span data-stu-id="e644d-264">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="e644d-265">Por exemplo, se o seu domínio de teste for **testlab.contoso.com**, você digitaria **user1@testlab.contoso.com**. Pressione a tecla TAB ou permitir que o Office 365 para redirecioná-lo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e644d-265">For example, if your test domain is **testlab.contoso.com**, you would type **user1@testlab.contoso.com**. Press TAB or allow Office 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="e644d-p109">Agora, você deverá ver uma página de **sua conexão é não particular** . Você está vendo isso porque você instalou um certificado autoassinado em ADFS1 computador desktop não foi possível validar. Em uma implantação de produção da autenticação federada, você usaria um certificado de uma autoridade de certificação confiável e seus usuários não veria nesta página.</span><span class="sxs-lookup"><span data-stu-id="e644d-p109">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="e644d-269">Na página **sua conexão é não particular** , clique em **Avançado**e, em seguida, clique em **prossiga para \<seu serviço de Federação FQDN >**.</span><span class="sxs-lookup"><span data-stu-id="e644d-269">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="e644d-270">Na página com o nome da sua organização a empresa fictícia, entrar com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e644d-270">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="e644d-271">**CORP\\User1** para o nome</span><span class="sxs-lookup"><span data-stu-id="e644d-271">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="e644d-272">A senha para a conta User1</span><span class="sxs-lookup"><span data-stu-id="e644d-272">The password for the User1 account</span></span>
    
    <span data-ttu-id="e644d-273">Você deverá ver a página do **Microsoft Office Home** .</span><span class="sxs-lookup"><span data-stu-id="e644d-273">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="e644d-p110">Esse procedimento demonstra que sua assinatura de avaliação do Office 365 é federada com o domínio corp.contoso.com do AD do Windows Server hospedado no DC1. Aqui estão os fundamentos do processo de autenticação:</span><span class="sxs-lookup"><span data-stu-id="e644d-p110">This procedure demonstrates that your Office 365 trial subscription is federated with the Windows Server AD corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="e644d-276">Quando você usa o domínio federado que você criou na fase 1 do nome de conta de entrada, o Office 365 redireciona o navegador para sua federação FQDN e PROXY1 de serviço.</span><span class="sxs-lookup"><span data-stu-id="e644d-276">When you use the federated domain that you created in Phase 1 within the sign-in account name, Office 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="e644d-277">PROXY1 envia a página de entrada de empresa fictícia de seu computador local.</span><span class="sxs-lookup"><span data-stu-id="e644d-277">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="e644d-278">Quando você envia CORP\\User1 e a senha para PROXY1, ele encaminha para ADFS1.</span><span class="sxs-lookup"><span data-stu-id="e644d-278">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="e644d-279">ADFS1 valida CORP\\User1 e a senha com DC1 e envia um token de segurança de computador local.</span><span class="sxs-lookup"><span data-stu-id="e644d-279">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="e644d-280">Computador local envia o token de segurança para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="e644d-280">Your local computer sends the security token to Office 365.</span></span>
    
6. <span data-ttu-id="e644d-281">O Office 365 valida que o token de segurança foi criado por ADFS1 e permite o acesso.</span><span class="sxs-lookup"><span data-stu-id="e644d-281">Office 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="e644d-p111">Agora, a sua assinatura de avaliação do Office 365 é configurada com autenticação federada. Você pode usar esse ambiente de desenvolvimento e teste para cenários de autenticação avançada.</span><span class="sxs-lookup"><span data-stu-id="e644d-p111">Your Office 365 trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="e644d-284">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="e644d-284">Next Step</span></span>

<span data-ttu-id="e644d-285">Quando estiver pronto para implantar pronto para produção, autenticação federada de alta disponibilidade para o Office 365 no Windows Azure, consulte [Deploy autenticação federada do alta disponibilidade para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="e644d-285">When you are ready to deploy production-ready, high availability federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e644d-286">Veja também</span><span class="sxs-lookup"><span data-stu-id="e644d-286">See Also</span></span>

[<span data-ttu-id="e644d-287">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="e644d-287">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="e644d-288">Ambiente de desenvolvimento e teste de configuração de base</span><span class="sxs-lookup"><span data-stu-id="e644d-288">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="e644d-289">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e644d-289">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="e644d-290">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="e644d-290">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="e644d-291">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="e644d-291">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


