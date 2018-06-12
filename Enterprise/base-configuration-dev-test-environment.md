---
title: Ambiente de desenvolvimento/teste para a Configuração Base
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Resumo: Criar uma intranet simplificada como um ambiente de desenvolvimento/teste no Microsoft Azure.'
ms.openlocfilehash: 86f2f6ec907639c9aa513c6868f6ce5ed021f3d4
ms.sourcegitcommit: b2058b34196022668eac15e723962fefd82d6774
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "19631402"
---
# <a name="base-configuration-devtest-environment"></a>Ambiente de desenvolvimento/teste para a Configuração Base

 **Resumo:** Criar uma intranet simplificada como um ambiente de desenvolvimento/teste no Microsoft Azure.
  
Este artigo fornece instruções passo a passo para criar o seguinte ambiente de desenvolvimento/teste para a Configuração Básica no Azure:
  
**Figura 1: Ambiente de desenvolvimento/teste da Configuração Base**

![Fase 4 da Configuração Base no Azure com a máquina virtual CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
O ambiente de desenvolvimento/teste da Configuração Base na Figura 1 inclui a sub-rede Corpnet em uma rede virtual do Azure, somente na nuvem, chamada TestLab que simula uma intranet simplificada e privada conectada à Internet. Ele contém três máquinas virtuais do Azure em que o Windows Server 2016 é executado:
  
- O DC1 está configurado como um controlador de domínio de intranet e servidor de Sistema de Nomes de Domínio (DNS).
    
- O APP1 está configurado como um servidor Web e aplicativo geral.
    
- O CLIENT1 atua como um cliente de intranet.
    
Essa configuração permite que o DC1, APP1, CLIENT1 e outros computadores na sub-rede Corpnet: 
  
- Fiquem conectados à Internet para instalar atualizações, acessar os recursos da Internet em tempo real e participar de tecnologias públicas de nuvem como o Microsoft Office 365 e outros serviços do Azure.
    
- Sejam gerenciados remotamente usando conexões da de Área de Trabalho Remota do seu computador que está conectado à Internet ou à rede da sua organização.
    
É possível usar o ambiente teste resultante:
  
- Para testes e desenvolvimento de aplicativos.
    
- Como a configuração inicial de um ambiente de teste estendido dos seu próprios designs, que inclui máquinas virtuais adicionais, serviços do Azure ou outras ofertas de nuvem da Microsoft como o Office 365 e Enterprise Mobility + Security (EMS).
    
Há quatro etapas para configurar o ambiente de teste da Configuração Base no Azure:
  
1. Criar uma rede virtual.
    
2. Configurar o DC1.
    
3. Configurar o APP1.
    
4. Configurar o CLIENT1.
    
Se você ainda não tem a assinatura do Azure, inscreva-se para uma avaliação gratuita em [Experimentar o Azure](https://azure.microsoft.com/pricing/free-trial/). Se você já tem a assinatura do MSDN ou Visual Studio, consulte o [crédito mensal do Azure para assinantes do Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
> [!NOTE]
> As máquinas virtuais no Azure implicam um custo monetário contínuo quando estão em execução. Esse custo é cobrado em relação à avaliação gratuita, assinatura do MSDN ou assinatura paga. Para saber mais sobre os custos de execução de máquinas virtuais do Azure, consulte os [detalhes de preços de máquinas virtuais](https://azure.microsoft.com/pricing/details/virtual-machines/) e a [calculadora de preços do Azure](https://azure.microsoft.com/pricing/calculator/). Para reduzir custos, consulte também mais informações sobre como [minimizar os custos de máquinas virtuais do ambiente de teste no Azure](base-configuration-dev-test-environment.md#mincost). 
  
![Guias do Laboratório de Teste da Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-create-the-virtual-network"></a>Fase 1: Criar uma rede virtual

Primeiro, abra um prompt no Azure PowerShell.
  
> [!NOTE]
> O comando a seguir define o uso da versão mais recente do Azure PowerShell. Consulte a [introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/pt-BR/powershell/azureps-cmdlets-docs/). 
  
Entre na sua conta do Azure usando o comando a seguir.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) para obter um arquivo de texto que contém todos os comandos do PowerShell deste artigo.
  
Para obter o nome de sua assinatura, use este comando.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Configure a assinatura do Azure. Substitua tudo o que está entre aspas, incluindo os caracteres < e >, pelo nome correto.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Depois, crie um novo grupo de recursos para seu laboratório de teste da Configuração Base. Para determinar um nome de grupo de recursos exclusivo, use este comando para listar seus grupos de recurso existentes.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Crie seu novo grupo de recursos com estes comandos. Substitua tudo o que está entre aspas, incluindo os caracteres < e >, pelos nomes corretos.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Em seguida, crie a rede virtual TestLab, que hospedará a sub-rede Corpnet da configuração base e a protegerá com um grupo de segurança de rede.
  
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

Esta é sua configuração atual:
  
![Fase 1 da Configuração Base no Azure com sub-rede e rede virtuais](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a>Fase 2: Configurar o DC1.

Nesta fase, você vai criar a máquina virtual DC1 e configurá-la como o controle de domínio para o domínio corp.contoso.com do AD (Active Directory) do Windows Server e um servidor DNS para as máquinas virtuais da rede virtual TestLab.
  
Para criar uma máquina virtual para o DC1, preencha o nome do grupo de recursos e execute estes comandos no prompt de comando do Azure PowerShell no computador local.
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
$diskConfig=New-AzureRmDiskConfig -AccountType StandardLRS -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Será solicitado que você insira um nome de usuário e uma senha para a conta de administrador local no DC1. Use uma senha forte e armazene ambos, a senha e o nome, em um local seguro.
  
Em seguida, conecte-se à máquina virtual DC1.
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a>Conectar-se ao DC1 usando as credenciais de conta de administrador local

1. No [Portal do Azure](https://portal.azure.com), clique em **Grupos de recursos >** [nome do novo grupo de recursos] **> DC1 > Conectar**.
    
2. No painel aberto, clique em **Baixar o arquivo RDP**. Abra o arquivo DC1.rdp que foi baixado e clique em **Conectar**.
    
3. Especifique o nome da conta de administrador local no DC1:
    
  - No Windows 7:
    
    Na caixa de diálogo **Segurança do Windows**, clique em **Usar outra conta**. Em **Nome de usuário**, digite **DC1\\**[nome da conta de administrador local].
    
  - No Windows 8 ou Windows 10:
    
    Na caixa de diálogo **Segurança do Windows**, clique em **Mais opções** e, então, clique em **Usar uma conta diferente**. Em **Nome de usuário**, digite **DC1\\**[nome da conta de administrador local].
    
4. Em **Senha**, digite a senha da conta de administrador local e clique em **OK**.
    
5. Quando solicitado, clique em **Sim**.
    
Em seguida, adicione um disco de dados extra como um novo volume com a letra de unidade F:, com este comando, em um prompt de comando do Windows PowerShell de nível de administrador no DC1.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Depois, configure o DC1 como controlador de domínio e servidor DNS para o domínio corp.contoso.com. Execute estes comandos em um prompt de comando do Windows PowerShell de nível de administrador.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
Será preciso especificar uma senha de administrador no modo de segurança. Armazene essa senha em um local seguro.
  
Esses comandos podem levar alguns minutos para serem concluídos.
  
Após a reinicialização do DC1, reconecte-se à máquina virtual do DC1.
  
### <a name="connect-to-dc1-using-domain-credentials"></a>Conectar-se ao DC1 usando credenciais de domínio

1. No [Portal do Azure](https://portal.azure.com), clique em **Grupos de recursos >** [nome do seu grupo de recursos] **> DC1 > Conectar**.
    
2. Execute o arquivo DC1.rdp que foi baixado e clique em **Conectar**.
    
3. Em **Segurança do Windows**, clique em **Usar outra conta**. Em **Nome de usuário**, digite **CORP\\**[nome da conta de administrador local].
    
4. Em **Senha**, digite a senha da conta de administrador local e clique em **OK**.
    
5. Quando solicitado, clique em **Sim**.
    
Em seguida, crie uma conta de usuário no Active Directory que será usada quando entrar nos computadores dos membros do domínio CORP. Execute este comando no prompt de comando nível de administrador do Windows PowerShell.
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Esse comando solicitará que você forneça a senha da conta User1. Como essa conta será usada para conexões remotas da área de trabalho para todos os computadores que são membros do domínio CORP, escolha uma senha forte. Registre a senha da conta User1 e armazene-a em um local seguro.
  
Em seguida, configure a nova conta User1 como administrador corporativo. Execute este comando no prompt de comando do Windows PowerShell no nível de administrador.
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

Feche a sessão de Área de Trabalho Remota com o DC1 e se reconecte usando a conta CORP\\User1.
  
Em seguida, para permitir o tráfego da ferramenta Ping, execute este comando no prompt de comando de nível de administrador do Windows PowerShell.
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Esta é sua configuração atual:
  
![Fase 2 da Configuração Base no Azure com a máquina virtual DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a>Fase 3: Configurar o APP1.

O APP1 fornece serviços de web e de compartilhamento de arquivos.

Para criar uma Máquina Virtual para o APP1, preencha o nome do grupo de recursos e execute estes comandos no prompt de comando do Azure PowerShell no computador local.
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Em seguida, conecte-se à máquina virtual do APP1 usando o nome da conta e a senha do administrador local do APP1 e depois abra um prompt de comando do Windows PowerShell.
  
Para verificar a comunicação da rede e a resolução de nome entre o APP1 e o DC1, execute o comando **ping dc1.corp.contoso.com** e verifique se há quatro respostas.
  
Em seguida, adicione a máquina virtual do APP1 ao domínio CORP com estes comandos no prompt do Windows PowerShell.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

Você deve fornecer as credenciais de conta do domínio CORP\\User1 depois de executar o comando **Add-Computer**.
  
Depois de reiniciar o APP1, conecte-se a ele usando a conta CORP\\User1 e, em seguida, abra um prompt de comando de nível de administrador do Windows PowerShell.
  
Depois, transforme o APP1 em um servidor web usando este comando no prompt de comando do Windows PowerShell no APP1:
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Em seguida, crie uma pasta compartilhada e um arquivo de texto dentro da pasta do APP1 com estes comandos no PowerShell.
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

Esta é sua configuração atual:
  
![Fase 3 da Configuração Base no Azure com a máquina virtual do APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a>Fase 4: Configurar o CLIENT1.

O CLIENT1 atua como um típico notebook, tablet ou computador, na intranet da Contoso.

> [!NOTE]  
> O seguinte conjunto de comandos cria o CLIENT1 executando o Windows Server 2016 Datacenter, o que pode ser feito em todos os tipos de assinaturas do Azure. Se você tiver a assinatura do Azure baseada em Visual Studio, será possível criar o CLIENT1 executando o Windows 10 no [Portal do Azure](https://portal.azure.com). 
  
Para criar uma Máquina Virtual no Azure para o CLIENT1, preencha o nome do grupo de recursos e execute estes comandos no prompt de comando do Azure PowerShell no computador local.
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Em seguida, conecte-se à máquina virtual do CLIENT1 usando o nome da conta e a senha do administrador local do CLIENT1 e depois abra um prompt de comando de nível de administrador no Windows PowerShell.
  
Para verificar a comunicação da rede e a resolução de nome entre o CLIENT1 e o DC1, execute o comando **ping dc1.corp.contoso.com** no prompt de comando do Windows PowerShell e verifique se há quatro respostas.
  
Em seguida, adicione a máquina virtual do CLIENT1 ao domínio CORP com estes comandos no prompt do Windows PowerShell.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

Observe que você deve fornecer as credenciais de conta do domínio CORP\\User1 depois de executar o comando **Add-Computer**.
  
Depois de reiniciar o CLIENT1, conecte-se a ele usando o nome e a senha da conta CORP\\User1 e, em seguida, abra um prompt de comando de nível de administrador no Windows PowerShell.
  
Após esse procedimento, verifique se que você pode acessar os recursos de compartilhamento de arquivo e da web no APP1 a partir do CLIENT1.
  
### <a name="verify-client-access-to-app1"></a>Verificar o acesso do cliente ao APP1

1. No Gerenciador do Servidor, na árvore do painel, clique em **Servidor Local**.
    
2. Em **Propriedades do CLIENT1**, clique em **Ativar** ao lado da **Configuração de Segurança Aprimorada do IE**.
    
3. Na **Configuração de Segurança Aprimorada do Internet Explorer**, clique em **Desativar** para **Administradores** e **Usurários** e, então, clique em **OK**.
    
4. Na tela Inicial, clique em **Internet Explorer** e, então, em**OK**.
    
5. Na barra de endereços, digite **http:\//app1.corp.contoso.com/** e pressione Enter. Você verá uma página padrão da Web sobre Serviços de Informações da Internet para APP1.
    
6. Na barra de tarefas da área de trabalho, clique no ícone do Explorador de Arquivos.
    
7. Na barra de endereços, digite **\\\\app1\\Files** e pressione Enter. Você verá uma janela de pasta com o conteúdo da pasta compartilhada de arquivos.
    
8. Na janela da pasta compartilhada **Arquivos**, clique duas vezes no arquivo **Example.txt**. Você verá o conteúdo do arquivo Example.txt.
    
9. Feche o **Bloco de notas do Example.txt ** e a janela da pasta compartilhada **Arquivos**.
    
Esta é sua configuração final:
  
![Fase 4 da Configuração Base no Azure com a máquina virtual CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
A Configuração Base no Azure agora está pronta para o desenvolvimento e os teste do aplicativo ou para criar ambientes de teste adicionais. 
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
<a name="mincost"> </a>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>Minimizar os custos de máquinas virtuais do teste ambiente no Azure

Para reduzir os custos com a execução de máquinas virtuais em ambiente de teste, siga um destes procedimentos:
  
- Crie um ambiente de teste e realize a demonstração e os testes necessários com a maior brevidade possível. Ao concluir, exclua o grupo de recursos do ambiente de teste.
    
- Desligue as máquinas virtuais do ambiente de teste para o estado desalocado.
    
Para desligar as máquinas virtuais com o Azure PowerShell, preencha o nome do grupo de recursos e execute estes comandos.
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

Para garantir que as máquinas virtuais funcionem corretamente ao iniciar todas elas do estado Parado (Desalocado), inicie-as na seguinte ordem:
  
1. DC1
2. APP1
3. CLIENT1
    
Para ligar as máquinas virtuais em ordem com o Azure PowerShell, preencha o nome do grupo de recursos e execute estes comandos.
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>Confira também

- [Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
- [DirSync para o ambiente de desenvolvimento/ teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
- [Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento/teste do Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
