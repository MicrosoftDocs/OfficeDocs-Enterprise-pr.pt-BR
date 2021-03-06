---
title: "Conectar uma rede local a uma rede virtual do Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/13/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: "Resumo: Aprenda a configurar uma rede virtual Azure entre locais para cargas de trabalho de servidor do Office."
---

# Conectar uma rede local a uma rede virtual do Microsoft Azure

 **Resumo:** Aprenda a configurar uma rede virtual Azure entre locais para cargas de trabalho de servidor do Office.
  
Uma rede virtual entre locais do Azure está conectada à sua rede local, ampliando sua rede para incluir sub-redes e máquinas virtuais hospedadas em serviços na infraestrutura do Azure. Esta conexão permite que os computadores na sua rede local acessem diretamente máquinas virtuais no Azure e vice-versa. Por exemplo, um servidor DirSync que está sendo executado em uma máquina virtual Azure precisa consultar controladores de domínio locais procurando por alterações nas contas e sincronizar essas alterações com a sua assinatura do Office 365. Este artigo mostra como configurar uma rede virtual entre locais do Azure que esteja pronta para hospedar máquinas virtuais do Azure.
  
Neste artigo:
  
- [Visão geral](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Overview)
    
- [Planejar sua rede virtual do Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)
    
- [Roteiro de implantação](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#DeploymentRoadmap)
    
## Visão geral
<a name="Overview"> </a>

Suas máquinas virtuais no Azure não precisam ser isoladas do seu ambiente local. Para conectar as máquinas virtuais do Azure aos recursos da sua rede local, é preciso configurar uma rede virtual do Azure entre locais. O diagrama a seguir mostra os componentes necessários para implantar uma rede virtual do Azure entre locais com uma máquina virtual no Azure.
  
![Rede local conectada ao Microsoft Azure por meio de uma conexão VPN site a site](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
No diagrama existem duas redes conectadas por uma conexão VPN (rede privada virtual) site a site: a rede local e a rede virtual do Azure. A rede local possui um dispositivo VPN que termina o túnel VPN da rede virtual do Azure. A conexão VPN site a site é encerrada por um dispositivo VPN na rede local e um gateway VPN Azure na rede virtual do Azure. A rede virtual do Azure tem máquinas virtuais. O tráfego originado das máquinas virtuais na rede virtual do Azure é encaminhado ao gateway VPN que, então, encaminha o tráfego pela conexão VPN de site a site para o dispositivo VPN na rede local. A infraestrutura de roteamento da rede local encaminha então o tráfego ao seu destino.
  
Para configurar a conexão VPN entre a rede local e sua rede virtual do Azure, siga estas etapas: 
  
1. **Local** Defina e crie um roteamento de rede local para o espaço de endereço da rede virtual do Azure que aponte para o seu dispositivo VPN local.
    
2. **Microsoft Azure:** Crie uma rede virtual do Azure com uma conexão VPN site a site. Este artigo não descreve o uso da[ExpressRoute](https://azure.microsoft.com/services/expressroute/).
    
3. **Local** Configure seu hardware ou software local de seu dispositivo VPN para encerrar a conexão VPN, que usa o protocolo IPsec (segurança).
    
Depois de estabelecer a conexão VPN de site a site, você pode adicionar máquinas virtuais do Azure às sub-redes da rede virtual.
  
## Planejar sua rede virtual do Azure
<a name="PlanningVirtual"> </a>

### Pré-requisitos
<a name="Prerequisites"> </a>

- Uma assinatura do Azure. Para saber mais sobre assinaturas do Azure, vá para a [página de assinaturas do Microsoft Azure](https://azure.microsoft.com/pricing/purchase-options/).
    
- Um espaço de endereço IPv4 privado disponível para atribuir à rede virtual e às suas sub-redes, com espaço suficiente para ampliação a fim de acomodar a quantidade de máquinas virtuais necessárias agora e no futuro.
    
- Um dispositivo VPN disponível em sua rede local para encerrar a conexão VPN site a site compatível com os requisitos para IPsec. Para saber mais, confira [VPN para conexões de rede virtual de site a site](https://go.microsoft.com/fwlink/p/?LinkId=393093).
    
- As alterações realizadas à sua infraestrutura de roteamento para que o tráfego direcionado ao espaço de endereço da rede virtual do Azure seja encaminhado para o dispositivo VPN que hospeda a conexão VPN site a site.
    
- Um proxy da Web que dê aos computadores conectados à rede local e à rede virtual do Azure acesso à Internet.
    
### Suposições de design de arquitetura da solução
<a name="DesignAssumptions"> </a>

A lista a seguir representa as opções de design que foram feitas para a arquitetura dessa solução. 
  
- Essa solução usa uma única rede virtual do Azure com uma conexão VPN de site a site. A rede virtual do Azure hospeda uma única sub-rede que pode conter várias máquinas virtuais. 
    
- Você pode usar o RRAS (Serviço de Roteamento e Acesso Remoto) no Windows Server 2016 ou Windows Server 2012 para estabelecer uma conexão VPN IPsec de site a site entre a rede local e a rede virtual do Azure. Você também pode usar outras opções, como dispositivos VPN Cisco ou Juniper Networks.
    
- A rede local pode ainda ter serviços de rede como o AD (Active Directory) do Windows Server, o DNS (Sistema de Nomes de Domínio) e servidores proxy. Dependendo dos requisitos, pode ser vantajoso colocar alguns desses recursos de rede na rede virtual no Azure.
    
Para uma rede virtual do Azure existente com uma ou mais sub-redes, determine se há um espaço de endereço remanescente para uma sub-rede adicional a fim de hospedar as máquinas virtual necessárias, com base em seus requisitos. Se você não tem um espaço de endereço remanescente para uma sub-rede adicional, crie outra rede virtual que tenha sua própria conexão VPN site a site.
  
### Planejar as alterações da infraestrutura de roteamento para a rede virtual do Azure
<a name="routing"> </a>

Você deve configurar sua infraestrutura de roteamento local para encaminhar o tráfego destinado ao espaço de endereço da rede virtual do Azure no dispositivo VPN local que hospeda a conexão VPN site a site.
  
O método exato de atualização da infraestrutura de roteamento depende de como você gerencia suas informações de roteamento, que pode ser:
  
- Atualizações da tabela de roteamento com base em configuração manual.
    
- Atualizações da tabela de roteamento com base em protocolos de roteamento, como protocolo RIP (Routing Information Protocol) ou protocolo OSPF (Open Shortest Path First).
    
Consulte seu especialista em roteamento para garantir que o tráfego destinado à rede virtual do Azure seja encaminhado ao dispositivo VPN local.
  
### Planejar regras de firewall para tráfego que entra e sai do dispositivo VPN local
<a name="firewall"> </a>

Se seu dispositivo VPN está em uma rede de perímetro que tem um firewall entre a rede de perímetro e a Internet, pode ser necessário configurar o firewall com as seguintes regras para possibilitar a conexão VPN de site a site.
  
- Tráfego para o dispositivo VPN (vindo da Internet):
    
  - Endereço IP de destino do dispositivo VPN e protocolo IP 50
    
  - Endereço IP de destino do dispositivo VPN e porta de destino UDP 500
    
  - Endereço IP de destino do dispositivo VPN e porta de destino UDP 4500
    
- Tráfego do dispositivo VPN (indo para a Internet):
    
  - Endereço IP de origem do dispositivo VPN e protocolo IP 50
    
  - Endereço IP de origem do dispositivo VPN e porta de origem UDP 500
    
  - Endereço IP de origem do dispositivo VPN e porta de origem UDP 4500
    
### Planejar para um espaço de endereço IP privado da rede virtual do Azure
<a name="IPAddresses"> </a>

O espaço de endereço IP privado da rede virtual do Azure deve pode acomodar endereços usados pelo Azure para hospedar a rede virtual e ao menos uma sub-rede que tenha endereços suficientes para suas máquinas virtuais do Azure.
  
Para determinar a quantidade de endereços necessários para a sub-rede, conte o número de máquinas virtuais necessárias agora, estime o crescimento futuro e use a tabela a seguir para determinar o tamanho da sub-rede.
  
|**Número de máquinas virtuais necessárias**|**Número de bits de host necessário**|**Tamanho da sub-rede**|
|:-----|:-----|:-----|
|1 a 3  <br/> |3  <br/> |/29  <br/> |
|4 a 11  <br/> |4  <br/> |/28  <br/> |
|12 a 27  <br/> |5  <br/> |/27  <br/> |
|28 a 59  <br/> |6  <br/> |/26  <br/> |
|60 a 123  <br/> |7  <br/> |/25  <br/> |
   
### Planilha de planejamento para configurar sua rede virtual do Azure
<a name="worksheet"> </a>

Antes de criar uma rede virtual do Azure para hospedar máquinas virtuais, você deve determinar as configurações necessárias nas tabelas a seguir.
  
Para as configurações da rede virtual, preencha a Tabela V.
  
 **Tabela V: Configuração de rede virtual entre locais**
  
|**Item**|**Elemento Configuration**|**Descrição**|**Valor**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nome da rede virtual  <br/> |Um nome a atribuir à rede virtual do Azure (por exemplo, DirSyncNet).  <br/> |__________________  <br/> |
|2.  <br/> |Local da rede virtual  <br/> |O datacenter do Azure que conterá a rede virtual (como Oeste dos EUA).  <br/> |__________________  <br/> |
|3.  <br/> |Endereço IP do dispositivo VPN  <br/> |O endereço IPv4 público da interface de seu dispositivo VPN na Internet. Trabalhe com seu departamento de TI para determinar este endereço.  <br/> |__________________  <br/> |
|4.  <br/> |Espaço de endereço da rede virtual  <br/> |O espaço de endereço (definido em um único prefixo de endereço privado) para a rede virtual. Trabalhe com seu departamento de TI para determinar este espaço de endereço. O espaço de endereço deve estar no formato Roteamento entre Domínios sem Classificação (CIDR), também conhecido como formato de prefixo de rede. 10.24.64.0/20 é um exemplo.  <br/> |__________________  <br/> |
|5.  <br/> |Chave compartilhada IPsec  <br/> |Uma cadeia alfanumérica aleatória com 32 caracteres, que será usada para autenticar ambos os lados da conexão VPN site a site. Trabalhe com seu departamento de TI ou de segurança para determinar este valor de chave e armazená-lo em um local seguro. Como alternativa, confira [Criar uma cadeia de caracteres aleatória para uma chave pré-compartilhada IPsec](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |__________________  <br/> |
   
Preencha a Tabela S para as sub-redes desta solução.
  
- Para a primeira sub-rede, determine um espaço de endereço de 28 bits (com um comprimento de prefixo /28) para a sub-rede do gateway do Azure. Confira [Calcular o espaço de endereço da sub-rede do gateway para as redes virtuais do Azure](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/) para instruções sobre como determinar este espaço de endereço.
    
- Para a segunda sub-rede, especifique um nome amigável, um único espaço de endereço IP com base no espaço de endereço da rede virtual e um propósito descritivo.
    
Trabalhe com seu departamento de TI para determinar esses espaços de endereço a partir do espaço de endereço da rede virtual. Ambos os espaços de endereço devem estar no formato CIDR.
  
 **Tabela S: Sub-redes na rede virtual**
  
|**Item**|**Nome da sub-rede**|**Espaço de endereço da sub-rede**|**Finalidade**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |_____________________________  <br/> |A sub-rede usada pelo gateway do Azure.  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Para servidores de DNS locais que você deseja que sejam usados pelas máquinas virtuais da rede virtual, preencha a Tabela D. Dê a cada servidor DNS um nome amigável e um único endereço IP. Esse nome amigável não precisa corresponder ao nome do host ou ao nome do computador do servidor DNS. Observe que duas entradas em branco estão listadas, mas você pode adicionar mais. Trabalhe com seu departamento de TI para determinar esta lista.
  
 **Tabela D: servidores DNS locais**
  
|**Item**|**Nome amigável do servidor DNS**|**Endereço IP do servidor DNS**|
|:-----|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Para direcionar os pacotes da rede virtual do Azure para a rede de sua organização por uma conexão VPN de site a site, é preciso configurar a rede virtual com uma rede local. Essa rede local contém uma lista de espaços de endereço (no formato CIDR) para todos os locais da rede local de sua organização que as máquinas virtuais da rede virtual devem acessar. Essa lista pode conter todos os locais na rede ou em uma sub-rede locais. A lista de espaços de endereço que define sua rede local deve ser exclusiva e não deve coincidir com os espaços de endereço usados para essa rede virtual ou suas outras redes virtuais entre locais.
  
Para o conjunto de espaços de endereço da rede local, preencha a Tabela L. Observe que há três entradas em branco listadas, mas geralmente você precisará de mais. Trabalhe com seu departamento de TI para determinar esta lista.
  
 **Tabela L: Prefixos de endereço para a rede local**
  
|**Item**|**Espaço de endereço da rede local**|
|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |
|3.  <br/> |_____________________________  <br/> |
   
## Roteiro de implantação
<a name="DeploymentRoadmap"> </a>

A criação da rede virtual entre locais e a adição de máquinas virtuais no Azure tem três fases:
  
- Fase 1: Preparar sua rede local.
    
- Fase 2: Criar a rede virtual entre locais no Azure.
    
- Fase 3 (Opcional): Adicionar máquinas virtuais.
    
### Fase 1: Preparar sua rede local
<a name="Phase1"> </a>

Você deve configurar sua rede local com uma rota que aponte e, por fim, gere tráfego destinado para o espaço de endereço da rede virtual ao roteador na borda da rede local. Confira o administrador da rede para determinar como adicionar a rota à infraestrutura de roteamento da rede local.
  
Esta é a configuração resultante.
  
![A rede local deve ter uma rota para o espaço de endereço da rede virtual que aponte para o dispositivo VPN.](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### Fase 2: Criar a rede virtual entre locais no Azure
<a name="Phase2"> </a>

Primeiro, abra um prompt do Azure PowerShell. Se você não instalou o Azure PowerShell, confira [Introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).
  
> [!NOTE]
> Esses comandos são destinados ao Azure PowerShell 1.0 e versões superiores. Para obter um arquivo de texto contendo todos os comandos do PowerShell neste artigo, clique [aqui](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19). 
  
Em seguida, entre com sua conta do Azure usando este comando.
  
```
Login-AzureRMAccount
```

Para obter o nome de sua assinatura, use este comando.
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

Defina sua assinatura do Azure com esses comandos. Substitua tudo o que está entre aspas, incluindo os caracteres < e >, pelo nome de assinatura correto.
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

Depois, crie um novo grupo de recursos para sua rede virtual. Para determinar um nome de grupo de recursos exclusivo, use este comando para listar os grupos de recurso existentes.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Crie o novo grupo de recursos com estes comandos.
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

As máquinas virtuais baseadas no Gerenciador de Recursos exigem uma conta de armazenamento baseada no Gerenciador de Recursos. Você deve escolher um nome globalmente exclusivo para sua conta de armazenamento, e ele deve conter apenas letras minúsculas e números. Você pode usar este comando para listar as contas de armazenamento existentes.
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

Use este comando para testar se o nome proposto para a conta de armazenamento é exclusivo.
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

Para criar uma nova conta de armazenamento, execute estes comandos.
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

Crie a rede virtual do Azure.
  
```
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )

# Get the shortened version of the location
$rg=Get-AzureRmResourceGroup -Name $rgName
$locShortName=$rg.Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzureRmVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
```

Esta é a configuração resultante.
  
![A rede virtual ainda não está conectada à rede local.](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Em seguida, use estes comandos para criar os gateways para a conexão VPN site a site.
  
```
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

Esta é a configuração resultante.
  
![Agora a rede virtual tem um gateway.](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Em seguida, configure seu dispositivo VPN local para se conectar ao gateway de VPN do Azure. Para saber mais, confira [Sobre dispositivos VPN para conexões de rede virtual do Azure de site a site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Para configurar seu dispositivo VPN, você precisará do seguinte:
  
- O endereço IPv4 público do gateway VPN do Azure para sua rede virtual. Use o comando **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** para exibir esse endereço.
    
- A chave IPsec pré-compartilhada para a conexão VPN site a site (Tabela V - Item 5 - coluna Valor).
    
Esta é a configuração resultante.
  
![A rede virtual ainda já está conectada à rede local.](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### Fase 3 (Opcional): Adicionar máquinas virtuais
<a name="Phase2"> </a>

Crie as máquinas virtuais de que você precisa no Azure. Para saber mais, confira [Criar sua primeira máquina virtual do Windows no portal do Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Use as seguintes configurações:
  
- No painel **Básico**, selecione a mesma assinatura e grupo de recursos que sua rede virtual. Armazene o nome de usuário e a senha em um local seguro. Você precisará dessas informações posteriormente para entrar na máquina virtual.
    
- No painel **Tamanho**, escolha o tamanho apropriado.
    
- No painel **Configurações**, na seção **Armazenamento**, escolha o tipo de armazenamento **Padrão** e configure a conta de armazenamento com sua rede virtual. Na seção **Rede**, escolha o nome de suas rede e sub-rede virtuais para hospedar máquinas virtuais (não a GatewaySubnet). Deixe todas as outras configurações com os valores padrão.
    
Verifique se a máquina virtual está usando o DNS corretamente (examine o DNS interno) para garantir que os registros de Endereço (A) foram adicionados à sua nova máquina virtual. Para acessar a Internet, suas máquinas virtuais do Azure devem estar configuradas para usar o servidor proxy da sua rede local. Entre em contato com o administrador da rede para etapas de configuração adicionais a executar no servidor.
  
Esta é a configuração resultante.
  
![Agora a rede virtual hospeda máquinas virtuais que são acessíveis pela rede local.](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## See Also
<a name="DeploymentRoadmap"> </a>

#### 

[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Implantar a DirSync (sincronização de diretórios) do Office 365 no Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)
#### 

[Como criar a máquina virtual](https://go.microsoft.com/fwlink/p/?LinkId=393098)
  
[Sobre dispositivos VPN para conexões de rede virtual do Azure de site a site](https://azure.microsoft.com/documentation/articles/vpn-gateway-about-vpn-devices/)
  
[Como instalar e configurar o Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/#how-to-install-azure-powershell)

