---
title: Rede virtual simulado entre locais no Windows Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: 'Resumo: Crie uma rede virtual de locais cruzados simulado in Microsoft Azure como um ambiente de desenvolvimento e teste.'
ms.openlocfilehash: 4a34126bba4561da621dc3faf37dd30d4dcc9ff3
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a>Rede virtual simulado entre locais no Windows Azure

 **Resumo:** Crie uma rede virtual de locais cruzados simulado in Microsoft Azure como um ambiente de desenvolvimento e teste.
  
Este artigo o orienta a criação de um ambiente de nuvem híbrida simulado com o Microsoft Azure using duas redes virtuais do Azure. Aqui está a configuração resultante. 
  
![Fase 3 do ambiente simulado de desenvolvimento e teste da rede virtual entre locais, com a máquina virtual DC2 na VNet XPrem](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Isso simula um ambiente de produção de nuvem do Windows Azure IaaS híbrida e consiste em:
  
- Uma rede de simulado e simplificado local hospedada em uma rede virtual do Azure (a rede virtual do laboratório de teste).
    
- Uma rede virtual de locais cruzados simulado hospedada no Windows Azure (XPrem).
    
- Um relacionamento de VNet a correspondência entre as duas redes virtuais.
    
- Um controlador de domínio secundário na rede virtual XPrem.
    
Isso oferece que uma base e iniciando comuns apontar a partir do qual você pode: 
  
- Desenvolver e testar aplicativos em um ambiente de nuvem simulado Azure IaaS híbrido.
    
- Crie configurações de teste de computadores, alguns dentro da rede virtual do laboratório de teste e alguns dentro da rede virtual XPrem, para simular híbrido baseado em nuvem IT as cargas de trabalho.
    
Há três fases principais para configurar esse ambiente de desenvolvimento/teste:
  
1. Configure a rede virtual do laboratório de teste.
    
2. Crie a rede virtual entre locais.
    
3. Configure DC2.
    
> [!NOTE]
> [!OBSERVAçãO] Essa configuração requer uma assinatura paga do Azure. 
  
![Guias do Laboratório de Teste da Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a>Fase 1: Configurar a rede virtual do laboratório de teste

Use as instruções no [ambiente de desenvolvimento e teste de configuração básica](base-configuration-dev-test-environment.md) para configurar os computadores DC1, APP1 e CLIENT1 na rede virtual Azure chamada de laboratório de teste.
  
Esta é a configuração atual. 
  
![Fase 4 da Configuração Básica no Azure com a máquina virtual CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Fase 2: Criar a rede virtual à XPrem

Nesta fase, você cria e configurar a rede virtual à nova XPrem e se conectar à rede virtual laboratório de teste com VNet correspondência.
  
Em primeiro lugar, inicie um prompt do Azure PowerShell no computador local.
  
> [!NOTE]
> [!OBSERVAçãO] O comando a seguir define o uso da versão mais recente do Azure PowerShell. Confira [Introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Inscreva-se à sua conta do Windows Azure com o seguinte comando.
  
```
Login-AzureRMAccount
```

> [!TIP]
> [!DICA] Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) para obter um arquivo de texto que contém todos os comandos do PowerShell deste artigo.
  
Para obter o nome de sua assinatura, use este comando.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Defina sua assinatura do Windows Azure. Substituir tudo entre aspas, incluindo o \< e > caracteres, com os nomes corretos.
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

Em seguida, crie a rede virtual à XPrem e protegê-lo com um grupo de segurança de rede com esses comandos.
  
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

Em seguida, você cria o relacionamento de correspondência VNet entre o laboratório de teste e XPrem VNets com esses comandos.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Esta é a configuração atual. 
  
![Fase 2 do ambiente simulado de desenvolvimento e teste da rede virtual entre locais, com a relação de emparelhamento do VNet e VNet XPrem](images/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Fase 3: Configurar DC2

Nesta fase, você cria a máquina virtual do DC2 na rede virtual XPrem e, em seguida, configure-o como um controlador de domínio de réplica.
  
Primeiro, crie uma máquina virtual para DC2. Execute estes comandos no prompt de comando do PowerShell do Azure no computador local.
  
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

Em seguida, conecte-se para a nova máquina virtual DC2 a partir do [portal do Windows Azure](https://portal.azure.com) usando seu nome de conta de administrador local e a senha.
  
Em seguida, configure uma regra de Firewall do Windows para permitir o tráfego para testar a conectividade básica. A partir de um prompt de comando do Windows PowerShell de nível de administrador no DC2, execute estes comandos. 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

O comando ping deve resultar em quatro respostas bem-sucedidas 10.0.0.4 de endereço IP. Este é um teste de tráfego entre o relacionamento de correspondência VNet. 
  
Em seguida, adicione o disco de dados extras como um novo volume com a letra da unidade f: com este comando no prompt de comando do Windows PowerShell no DC2.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Em seguida, configure DC2 como um controlador de domínio de réplica para o domínio corp.contoso.com. Execute estes comandos no prompt de comando do Windows PowerShell no DC2.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Observe que você será solicitado a fornecer os dois CORP\\User1 senha e uma senha de modo de restauração de serviços de diretório (DSRM) e reiniciar DC2. 
  
Agora que a rede virtual à XPrem tem seu próprio servidor DNS (DC2), você deve configurar a rede virtual à XPrem para usar este servidor DNS. Execute esses comandos no prompt de comando do PowerShell do Windows Azure no computador local.
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

Do portal do Windows Azure no computador local, se conecte ao DC1 com CORP\\User1 credenciais. Para configurar o domínio CORP para que os usuários e computadores usam seu controlador de domínio local para autenticação, execute estes comandos em um prompt de comando do Windows PowerShell de nível de administrador no DC1.
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Esta é a configuração atual. 
  
![Fase 3 do ambiente simulado de desenvolvimento e teste da rede virtual entre locais, com a máquina virtual DC2 na VNet XPrem](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Seu ambiente de nuvem híbrida Azure simulado agora está pronta para teste.
  
## <a name="next-step"></a>Próxima etapa

Use esse ambiente de desenvolvimento e teste para simular a um [farm do SharePoint Server 2016 intranet hospedado no Windows Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).
  
## <a name="see-also"></a>Confira também

[O ambiente de desenvolvimento e teste de configuração base](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[ Segurança no Aplicativo na Nuvem para seu ambiente de desenvolvimento e teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)


