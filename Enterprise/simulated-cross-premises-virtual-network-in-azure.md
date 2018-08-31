---
title: Rede virtual simulada entre locais no Azure
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
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: 'Resumo: crie uma rede virtual simulada entre locais no Microsoft Azure como um ambiente de desenvolvimento/teste.'
ms.openlocfilehash: 0aee14af136e0874c259faac26d83d85b188a7c7
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915336"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a>Rede virtual simulada entre locais no Azure

 **Resumo:** crie uma rede virtual simulada entre locais no Microsoft Azure como um ambiente de desenvolvimento/teste.
  
Este artigo ajuda você a criar um ambiente simulado de nuvem híbrida com o Microsoft Azure usando duas redes virtuais do Azure. Veja a configuração resultante. 
  
![Fase 3 do ambiente de desenvolvimento/teste da rede virtual simulada entre locais, com a máquina virtual DC2 na VNet XPrem](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Isso simula um ambiente de produção de nuvem híbrida para o IaaS do Azure e consiste em:
  
- Uma rede local simulada e simplificada hospedada na rede virtual do Azure (a rede virtual TestLab). 
    
- Uma rede virtual simulada entre locais hospedada no Azure (XPrem).
    
- Uma relação de emparelhamento de VNets entre as duas redes virtuais.
    
- Um controlador de domínio secundário na rede virtual XPrem.
    
Isso fornece uma base e um ponto de partida comuns a partir dos quais você pode: 
  
- Desenvolver e testar aplicativos em um ambiente simulado de nuvem híbrida para o IaaS do Azure.
    
- Criar configurações de teste para computadores, algumas na rede virtual TestLab e outras na rede virtual XPrem, para simular cargas de trabalho de TI baseadas na nuvem híbrida.
    
Há três fases principais para configurar esse ambiente de desenvolvimento/teste:
  
1. Configurar a rede virtual TestLab.
    
2. Criar a rede virtual entre locais.
    
3. Configurar o DC2.
    
> [!NOTE]
> Essa configuração requer uma assinatura paga do Azure. 
  
![Guias do Laboratório de Teste da Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a>Fase 1: configurar a rede virtual TestLab

Use as instruções em [Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) para configurar os computadores DC1, APP1 e CLIENT1 na rede virtual Azure chamada TestLab.
  
Esta é sua configuração atual. 
  
![Fase 4 da Configuração básica no Azure com a máquina virtual CLIENT1](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Fase 2: criar uma rede virtual XPrem

Nesta fase, crie e configure a nova rede virtual XPrem e conecte-se à rede virtual TestLab com emparelhamento de VNets.
  
Primeiro, inicie um prompt do Azure PowerShell em seu computador local.
  
> [!NOTE]
> O comando a seguir define o uso da versão mais recente do Azure PowerShell. Confira [Introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/pt-BR/powershell/azureps-cmdlets-docs/). 
  
Entre na sua conta do Azure usando o comando a seguir.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) para obter um arquivo de texto que contém todos os comandos do PowerShell usados neste artigo.
  
Para obter o nome de sua assinatura, use este comando.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Defina sua assinatura do Azure. Substitua tudo o que está entre aspas, incluindo os caracteres \< e >, pelos nomes corretos.
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

Em seguida, crie a rede virtual XPrem e proteja-a usando um grupo de segurança de rede com estes comandos.
  
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

Depois, crie a relação de emparelhamento de VNets entre as VNets TestLab e XPrem com estes comandos.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Esta é sua configuração atual. 
  
![Fase 2 do ambiente de desenvolvimento/teste da rede virtual simulada entre locais, com a relação de emparelhamento de VNet e VNet XPrem](media/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Fase 3: configurar o DC2

Nesta fase, crie a máquina virtual DC2 na rede virtual XPrem e configure-a como um controlador de domínio de réplica.
  
Primeiro, crie uma máquina virtual para o DC2. Execute esses comandos no prompt de comando do Azure PowerShell em seu computador local.
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Em seguida, conecte-se à nova máquina virtual DC2 a partir do [portal do Azure](https://portal.azure.com) usando o nome e a senha da conta de administrador local.
  
Em seguida, configure uma regra de Firewall do Windows para permitir o tráfego para testes básicos de conectividade. No DC2, em um prompt de comando de nível de administrador do Windows PowerShell, execute esses comandos. 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

O comando ping deve resultar em quatro respostas bem-sucedidas do endereço IP 10.0.0.4. Este é um teste de tráfego entre a relação de emparelhamento de VNets. 
  
Em seguida, adicione o disco de dados extra como um novo volume com a letra de unidade F:, com este comando em um prompt de comando do Windows PowerShell no DC2.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Depois, configure o DC2 como controlador de domínio de réplica para o domínio corp.contoso.com. Execute estes comandos em um prompt de comando do Windows PowerShell no DC2.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Observe que você será solicitado a fornecer a senha de CORP\\Usuário1 e uma senha do Modo de Restauração dos Serviços de Diretório (DSRM) e a reiniciar o DC2. 
  
Agora que a rede virtual XPrem tem seu próprio servidor DNS (DC2), você deve configurá-la para usar esse servidor DNS. Execute esses comandos no prompt de comando do Azure PowerShell em seu computador local.
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

No portal do Azure no computador local, conecte-se ao DC1 com as credenciais CORP\\Usuário1. Para configurar o domínio CORP de modo que os computadores e usuários usem seu controlador de domínio local para autenticação, execute esses comandos em um prompt de comando do Windows PowerShell como administrador no DC1.
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Esta é sua configuração atual. 
  
![Fase 3 do ambiente de desenvolvimento/teste da rede virtual simulada entre locais, com a máquina virtual DC2 na VNet XPrem](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Seu ambiente simulado de nuvem híbrida do Azure já está pronto para testes.
  
## <a name="next-step"></a>Próxima etapa

Use este ambiente de desenvolvimento/teste para simular um [farm de Intranet do SharePoint Server 2016 hospedado no Azure ](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).
  
## <a name="see-also"></a>Confira também

[Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para o ambiente de desenvolvimento/ teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento/teste do Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md)


