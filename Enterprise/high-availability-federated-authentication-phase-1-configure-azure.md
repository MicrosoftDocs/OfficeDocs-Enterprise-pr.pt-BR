---
title: "Autenticação federada de alta disponibilidade fase 1 configurar o Azure"
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
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "Resumo: Configure a infraestrutura do Microsoft Azure para alta disponibilidade do host autenticação federada para o Office 365."
ms.openlocfilehash: fed6b24af2ba54bef95be22641fd140f7c1be717
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Autenticação federada de alta disponibilidade Fase 1: Configurar o Azure

 **Resumo:** Configure a infraestrutura do Microsoft Azure para a autenticação de alta disponibilidade federada host para o Office 365.
  
Nesta fase, você pode criar os grupos de recursos, contas de armazenamento, conjuntos de rede (VNet) e disponibilidade virtuais no Azure que irá hospedar as máquinas virtuais em fases 2, 3 e 4. Você deve concluir esta fase antes de mover o logon em [alta disponibilidade federado autenticação fase 2: Configure os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.
  
Deve ser provisionados do Azure com esses componentes básicos:
  
- Grupo de recursos
    
- Uma rede virtual do Azure (VNet) entre locais com sub-redes para a hospedagem das máquinas virtuais do Azure
    
- Grupos de segurança de rede para a realização do isolamento de sub-redes
    
- Conjuntos de disponibilidade
    
## <a name="configure-azure-components"></a>Configurar componentes do Azure

Antes de começar a configuração de componentes do Windows Azure, preencha as tabelas a seguir. Para ajudá-lo nos procedimentos para configurar o Azure, imprimir nesta seção e anote as informações necessárias ou copie nesta seção para um documento e preencha-lo. Para obter as configurações do VNet, preencha V da tabela.
  
|**Item**|**Definição de configuração**|**Descrição**|**Valor**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nome da VNet  <br/> |Um nome a ser atribuído à VNet (exemplo FedAuthNet).  <br/> |_______________________________  <br/> |
|2.  <br/> |Local de VNet  <br/> |O datacenter do Azure regional que conterá a rede virtual.  <br/> |_______________________________  <br/> |
|3.  <br/> |Endereço IP do dispositivo VPN  <br/> |O endereço IPv4 público da interface de seu dispositivo VPN na Internet.   <br/> |_______________________________  <br/> |
|4.  <br/> |Espaço de endereço da VNet  <br/> |O espaço de endereço da rede virtual. Trabalhe com seu departamento de TI para determinar esse espaço de endereço.  <br/> |_______________________________  <br/> |
|5.  <br/> |Chave compartilhada IPsec  <br/> |Uma 32 aleatória, alfanumérica cadeia de caracteres que será usada para autenticar a ambos os lados da conexão de VPN-to-site. Trabalhar com sua equipe de TI ou o departamento de segurança para determinar o valor da chave. Como alternativa, consulte [criar uma cadeia de caracteres aleatória para uma chave pré compartilhada do IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).<br/> |_______________________________  <br/> |
   
 **Tabela V: Configuração de rede virtual entre locais**
  
Em seguida, preencha a Tabela S para as sub-redes desta solução. Todos os espaços de endereço devem estar no formato de Roteamento entre Domínios sem Classificação (CIDR), também conhecido como formato de prefixo de rede. Um exemplo é 10.24.64.0/20.
  
Para as três primeiras sub-redes, especifique um nome e um único espaço de endereços IP com base no espaço de endereço da rede virtual. Para a sub-rede de gateway, determine um espaço de endereço de 27 bits (com um comprimento de prefixo /27) para a sub-rede do gateway do Azure. Use o seguinte:
  
1. Defina os bits variáveis no espaço de endereço da VNet como 1, até os bits que estão sendo usados pela sub-rede do gateway, e depois defina os bits restantes como 0.
    
2. Converta os bits resultantes em decimais e expresse-os como um espaço de endereço com o comprimento de prefixo definido como o tamanho da sub-rede do gateway.
    
Consulte [Calculadora de espaço de endereço para sub-redes do Azure gateway](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for um bloco de comando do PowerShell e o aplicativo de console c# ou Python que realiza esse cálculo para você.
  
Trabalhe com seu departamento de TI para determinar esses espaços de endereço a partir do espaço de endereço da rede virtual.
  
|**Item**|**Nome da sub-rede**|**Espaço de endereço da sub-rede**|**Finalidade**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |_______________________________  <br/> |A sub-rede usada pelo controlador de domínio e as máquinas virtuais (VMs) DirSync do Windows Server Active Directory (AD).  <br/> |
|2.  <br/> |_______________________________  <br/> |_______________________________  <br/> |A sub-rede usada pelos VMs do AD FS.  <br/> |
|3.  <br/> |_______________________________  <br/> |_______________________________  <br/> |A sub-rede usada pelas VMs de proxy do aplicativo Web.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |_______________________________  <br/> |A sub-rede usada pelas VMs do gateway do Azure.  <br/> |
   
 **Tabela S: Sub-redes na rede virtual**
  
Em seguida, preencha a Tabela I para os endereços IP estáticos atribuídos a máquinas virtuais e instâncias de balanceador de carga.
  
|**Item**|**Objetivo**|**Endereço IP da sub-rede**|**Valor**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Endereço IP estático do primeiro controlador de domínio  <br/> |O quarto endereço IP possível para o espaço de endereço da sub-rede definido no Item 1 da Tabela S.  <br/> |_______________________________  <br/> |
|2.  <br/> |Endereço IP estático do segundo controlador de domínio  <br/> |O quinto endereço IP possível para o espaço de endereço da sub-rede definido no Item 1 da Tabela S.  <br/> |_______________________________  <br/> |
|3.  <br/> |Endereço IP estático do servidor DirSync  <br/> |O sexto endereço IP possível para o espaço de endereço da sub-rede definido no Item 1 da Tabela S.   <br/> |_______________________________  <br/> |
|4.  <br/> |Endereço IP estático do balanceador de carga internos para os servidores do AD FS  <br/> |O quarto endereço IP possível para o espaço de endereço da sub-rede definido no Item 2 da Tabela S.   <br/> |_______________________________  <br/> |
|5.  <br/> |Endereço IP estático do primeiro servidor do AD FS  <br/> |O quinto endereço IP possível para o espaço de endereço da sub-rede definido no Item 2 da Tabela S.  <br/> |_______________________________  <br/> |
|6.  <br/> |Endereço IP estático do segundo servidor do AD FS  <br/> |O sexto endereço IP possível para o espaço de endereço da sub-rede definido no Item 2 da Tabela S.  <br/> |_______________________________  <br/> |
|7.  <br/> |Endereço IP estático do primeiro servidor proxy de aplicativos Web  <br/> |O quarto endereço IP possível para o espaço de endereço da sub-rede definido no Item 3 da Tabela S.  <br/> |_______________________________  <br/> |
|8.  <br/> |Endereço IP estático do segundo servidor proxy de aplicativos Web  <br/> |O quinto endereço IP possível para o espaço de endereço da sub-rede definido no Item 3 da Tabela S.  <br/> |_______________________________  <br/> |
   
 **Endereços de IP estático de i: tabela na rede virtual**
  
Para dois servidores de Sistema de Nomes de Domínio (DNS) na sua rede local que você deseja usar ao configurar controladores de domínio inicialmente na sua rede virtual, preencha a Tabela D. Trabalhe com o departamento de TI para determinar essa lista.
  
|**Item**|**Nome amigável do servidor DNS**|**Endereço IP do servidor DNS**|
|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |_______________________________  <br/> |
|2.  <br/> |_______________________________  <br/> |_______________________________  <br/> |
   
 **Tabela D: servidores DNS locais**
  
Para rotear pacotes da rede entre locais para a rede da organização entre a conexão de VPN site a site, você deve configurar a rede virtual com uma rede local que contenha uma lista dos espaços de endereço (em notação CIDR) para todos os locais acessíveis na rede local da sua organização. A lista de espaços de endereço que definem a sua rede local deve ser exclusiva e não deve ser ficar sobreposta ao espaço de endereço usado para outras redes virtuais ou locais.
  
Para o conjunto de espaços de endereço da rede local, preencha a Tabela L. Observe que há três entradas em branco listadas, mas geralmente você precisará de mais. Trabalhe com seu departamento de TI para determinar esta lista de espaços de endereço.
  
|**Item**|**Espaço de endereço da rede local**|
|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |
|2.  <br/> |_______________________________  <br/> |
|3.  <br/> |_______________________________  <br/> |
   
 **Tabela L: Prefixos de endereço para a rede local**
  
Agora, vamos começar a criar a infraestrutura do Azure para hospedar sua autenticação federada para o Office 365.
  
> [!NOTE]
> O comando a seguir define usar a versão mais recente do Azure PowerShell. Consulte a [Introdução ao cmdlets do PowerShell do Windows Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Primeiro, inicie um prompt do Azure PowerShell e faça logon na sua conta.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Para um arquivo de texto que contém todos os comandos do PowerShell este artigo e uma pasta de trabalho de configuração Microsoft Excel que gera blocos de comando do PowerShell pronto para executar com base em suas configurações personalizadas, consulte o [autenticação federada para o Office 365 Kit de implantação do Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
Para obter o nome de sua assinatura, use este comando.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Para versões mais antigas do Azure PowerShell, use este comando.
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

Defina sua assinatura do Windows Azure. Substituir tudo entre aspas, incluindo o \< e > caracteres, com o nome correto.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Em seguida, crie os novos grupos de recursos. Para determinar um conjunto exclusivo de nomes de grupo de recursos, use este comando para listar os grupos de recurso existentes.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Preencha a tabela a seguir para o conjunto de nomes de grupos de recursos exclusivos.
  
|**Item**|**Nome do grupo de recursos**|**Finalidade**|
|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |Controladores de domínio:  <br/> |
|2.  <br/> |_______________________________  <br/> |Servidores do AD FS  <br/> |
|3.  <br/> |_______________________________  <br/> |Servidores proxy de aplicativos Web  <br/> |
|4.  <br/> |_______________________________  <br/> |Elementos de infraestrutura  <br/> |
   
 **Tabela r: grupos de recursos**
  
Crie os novos grupos de recursos com estes comandos.
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Em seguida, você criará a rede virtual do Azure e suas sub-redes.
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

Em seguida, crie rede grupos de segurança para cada sub-rede que contém as máquinas virtuais. Para executar o isolamento de sub-rede, você pode adicionar regras para os tipos específicos de tráfego permitido ou negado ao grupo de segurança de rede de uma sub-rede.
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

Em seguida, use estes comandos para criar os gateways para a conexão VPN site a site.
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> Autenticação federada de usuários individuais não depende do quaisquer recursos locais. No entanto, se essa conexão de VPN-to-site ficar indisponível, os controladores de domínio em que o VNet não receberá as atualizações feitos no servidor local Windows AD de grupos e contas de usuário. Para garantir que isso não acontecer, você pode configurar a alta disponibilidade para sua conexão de VPN-to-site. Para obter mais informações, consulte [altamente disponível entre locais e conectividade de VNet para VNet](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Em seguida, registre o endereço IPv4 público do gateway de VPN do Azure para a sua rede virtual na exibição deste comando:
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Em seguida, configure seu dispositivo VPN de local para se conectar ao gateway VPN do Windows Azure. Para obter mais informações, consulte [Configure seu dispositivo VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Para configurar seu dispositivo VPN local, você precisará do seguinte:
  
- O endereço IPv4 público do gateway de VPN do Azure.
    
- A chave pré-compartilhada IPsec para a conexão de VPN-to-site (coluna de tabela V - Item 5 - valor).
    
Em seguida, certifique-se de que o espaço de endereço da rede virtual seja acessível a partir da sua rede local. Isso é feito geralmente com a inclusão de uma rota correspondente ao espaço de endereço da rede virtual para o seu dispositivo VPN e, em seguida, publicando essa rota ao restante da infraestrutura de roteamento da rede da sua organização. Trabalhe com seu departamento de TI para determinar como fazer isso.
  
Em seguida, defina os nomes de três conjuntos de disponibilidade. Preencha a Tabela A.  
  
|**Item**|**Objetivo**|**Nome do conjunto de disponibilidade**|
|:-----|:-----|:-----|
|1.  <br/> |Controladores de domínio:  <br/> |_______________________________  <br/> |
|2.  <br/> |Servidores do AD FS  <br/> |_______________________________  <br/> |
|3.  <br/> |Servidores proxy de aplicativos Web  <br/> |_______________________________  <br/> |
   
 **Conjuntos de disponibilidade de r: tabela**
  
Você precisará desses nomes quando criar as máquinas virtuais nas fases 2, 3 e 4.
  
Crie os novos conjuntos de disponibilidade com estes comandos do Azure PowerShell.
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

Esta é a configuração resultante da conclusão bem-sucedida dessa fase.
  
**Fase 1: A infraestrutura Azure para autenticação federada de alta disponibilidade para o Office 365**

![Fase 1 da autenticação federada de alta disponibilidade para o Office 365 no Azure com a infraestrutura do Azure](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Próxima etapa

Uso [alta disponibilidade federado autenticação fase 2: Configure os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) para continuar com a configuração dessa carga de trabalho.
  
## <a name="see-also"></a>See Also

[Implantar a autenticação federada de alta disponibilidade para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Identidade federada para seu ambiente de desenvolvimento e teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Identidade federada para o Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


