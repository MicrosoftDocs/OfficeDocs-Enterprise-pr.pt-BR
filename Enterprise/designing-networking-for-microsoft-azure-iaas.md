---
title: Criação de rede para o Microsoft Azure IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Resumo: entenda como projetar redes otimizadas para cargas de trabalho no Microsoft Azure IaaS.'
ms.openlocfilehash: c41e92445dd01a94b7d305b521bbd4330311fcb4
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490966"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a>Criação de rede para o Microsoft Azure IaaS

 **Resumo:** Entenda como projetar a rede otimizada para cargas de trabalho no Microsoft Azure IaaS.
  
Otimizar a rede para cargas de trabalho de ti hospedadas no Azure IaaS requer uma compreensão das redes virtuais do Azure (VNets), espaços de endereço, roteamento, DNS e balanceamento de carga.
  
## <a name="planning-steps-for-any-vnet"></a>Planejamento de etapas para qualquer VNet

Siga estas etapas para qualquer tipo de VNet.
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>Etapa 1: preparar sua intranet para os serviços de nuvem da Microsoft.

Siga as **etapas para preparar sua rede para o serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>Etapa 2: otimizar a largura de banda da Internet.

Otimize a largura de banda da Internet usando as etapas 2-4 das **etapas para preparar sua rede para os serviços Microsoft SaaS** no [projeto de rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md).
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>Etapa 3: determinar o tipo de VNet (somente na nuvem ou entre locais).

Uma VNet somente na nuvem não tem conexão com uma rede local. Veja um exemplo.
  
**Figura 1: uma VNet somente na nuvem**

![Figura 1: uma rede virtual somente na nuvem no Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
A Figura 1 mostra um conjunto de máquinas virtuais em uma VNet somente na nuvem.
  
Uma VNet entre locais tem uma conexão VPN ou ExpressRoute de site a site (S2S) para uma rede local por meio de um gateway do Azure. Veja um exemplo.
  
**Figura 2: uma VNet entre instalações**

![Figura 2: uma rede virtual entre locais no Azure](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
A Figura 2 mostra um conjunto de máquinas virtuais em uma VNet entre locais, que é conectada a uma rede local.
  
Consulte as [etapas adicionais de planejamento para uma seção de VNet entre locais](designing-networking-for-microsoft-azure-iaas.md#cross_prem) neste artigo.
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>Etapa 4: determinar o espaço de endereço da VNet.

A tabela 1 mostra os espaços de endereço para os diferentes tipos de VNets.
  
|**Tipo de VNet**|**Espaço de endereço da rede virtual**|
|:-----|:-----|
|Apenas Nuvem  <br/> |Espaço de endereçamento privado arbitrário  <br/> |
|Somente na nuvem interconectada  <br/> |Privado arbitrário, mas não sobrepondo com outros VNets conectados  <br/> |
|Entre locais  <br/> |Particular, mas não se sobrepõe ao local  <br/> |
|Interconexão entre locais  <br/> |Privado, mas não sobrepondo com o local e outros VNets conectados  <br/> |
   
 **Tabela 1: tipos de VNets e seus espaços de endereço correspondentes**
  
As máquinas virtuais recebem uma configuração de endereço do espaço de endereço da sub-rede por DHCP:
  
- Máscara de sub-rede/endereço
    
- Gateway padrão
    
- Endereços IP do servidor DNS
    
Você também pode reservar um endereço IP estático.
  
As máquinas virtuais também podem ser atribuídas a um endereço IP público, individualmente ou a partir do serviço de nuvem contendo (apenas para máquinas de implantação clássicas).
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>Etapa 5: determinar as sub-redes dentro do VNet e os espaços de endereço atribuídos a cada um.

Há dois tipos de sub-redes em uma rede virtual, uma sub-rede de gateway e uma sub-rede de Hospedagem de máquina virtual.
  
**Figura 3: os dois tipos de sub-redes no Azure**

![Figura 3: os dois tipos de sub-redes no Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
A Figura 3 mostra um VNet contendo uma sub-rede de gateway que tem um gateway do Azure e um conjunto de sub-redes de Hospedagem de máquina virtual contendo máquinas virtuais.
  
A sub-rede do portal do Azure é necessária para o Azure hospedar as duas máquinas virtuais do seu gateway do Azure. Especifique um espaço de endereçamento com pelo menos um comprimento de prefixo de 29 bits (exemplo: 192.168.15.248/29). Um comprimento de prefixo de 27 bits ou menor é recomendado, especialmente se você estiver planejando usar o ExpressRoute.
  
Uma prática recomendada para determinar o espaço de endereço da sub-rede do gateway do Azure é:
  
1. Escolha o tamanho da sub-rede do gateway.
    
2. Nos bits variáveis no espaço de endereço da VNet, defina os bits usados para a sub-rede de gateway como 0 e defina os bits restantes como 1.
    
3. Converta como Decimal e Express como um espaço de endereço com o comprimento do prefixo definido para o tamanho da sub-rede do gateway.
    
Com esse método, o espaço de endereço para a sub-rede do gateway está sempre no final mais distante do espaço de endereço da rede virtual.
  
Veja um exemplo de como definir o prefixo de endereço da sub-rede de gateway: o espaço de endereço da VNet é 10.119.0.0/16. Inicialmente, a organização usará uma conexão VPN site a site, mas, eventualmente, receberá o ExpressRoute. A tabela 2 mostra as etapas e os resultados da determinação do prefixo de endereço de sub-rede de gateway na notação de prefixo de rede (também conhecido como CIDR).

Veja a seguir as etapas e o exemplo de determinação do prefixo do endereço da sub-rede do gateway:

1. Escolha o tamanho da sub-rede do gateway. No nosso exemplo, escolhemos/28.
2. Defina os bits na parte variável do espaço de endereço da VNet (b) como 0 para os bits de sub-rede de gateway (G), caso contrário, 1 (V). No nosso exemplo, estamos usando o espaço de endereço 10.119.0.0/16 para a VNet.
<br/>
<br/>10,119. bbbbbbbb. bbbbbbbb
<br/>10,119. VVVVVVVV. VVVVGGGG
<br/>10,119. 11111111. 11110000
<br/><br/>
3. Converta o resultado da etapa 2 para decimal e Express como um espaço de endereço. Para o nosso exemplo, 10,119. 11111111. 11110000 é 10.119.255.240 e com o comprimento do prefixo da etapa 1, (28 no nosso exemplo), o prefixo do endereço da sub-rede do gateway resultante é 10.119.255.240/28.
  
Consulte a [calculadora de espaço de endereçamento para as sub-redes de gateway do Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) para obter mais informações.
  
As sub-redes de Hospedagem de máquina virtual são onde você coloca as máquinas virtuais do Azure, que podem ser feitas de acordo com as diretrizes locais típicas, como uma função ou camada comum de um aplicativo ou de um isolamento de sub-rede.
  
O Azure usa os primeiros 3 endereços em cada sub-rede. Portanto, o número de endereços possíveis em uma sub-rede do Azure é 2<sup>n</sup> -5, onde n é o número de bits do host. A tabela 3 mostra o intervalo de máquinas virtuais necessárias, o número de bits de hosts necessários e o tamanho da sub-rede correspondente.
  
|**Máquinas virtuais necessárias**|**Bits de host**|**Tamanho da sub-rede**|
|:-----|:-----|:-----|
|1 a 3  <br/> |3D  <br/> |/29  <br/> |
|4 a 11  <br/> |4   <br/> |/28  <br/> |
|12 a 27  <br/> |5   <br/> |/27  <br/> |
|28 a 59  <br/> |6   <br/> |/26  <br/> |
|60 a 123  <br/> |7   <br/> |/25  <br/> |
   
 **Tabela 3: requisitos de máquina virtual e seus tamanhos de sub-rede**
  
Para obter mais informações sobre a quantidade máxima de máquinas virtuais em uma sub-rede ou VNet, consulte [limites de rede](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).
  
Para obter mais informações, consulte [Plan and Design Azure virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>Etapa 6: determinar a configuração do servidor DNS e os endereços dos servidores DNS a serem atribuídos às VMs na VNet.

O Azure atribui máquinas virtuais aos endereços de servidores DNS por DHCP. Os servidores DNS podem ser:
  
- Fornecido pelo Azure: fornece registro de nome local e resolução local e de nomes de Internet
    
- Fornecido por você: fornece registro de nome local ou de intranet e resolução de nomes de intranet ou Internet
    
A tabela 4 mostra as diferentes configurações de servidores DNS para cada tipo de VNet.
    
|**Tipo de VNet**|**Servidor DNS**|
|:-----|:-----|
|Apenas Nuvem  <br/> |Fornecido pelo Azure para resolução de nomes locais e de Internet  <br/> Máquina virtual do Azure para resolução de nomes locais e de Internet (encaminhamento DNS)  <br/> |
|Entre locais  <br/> |Local para resolução de nomes locais e de intranet  <br/> Máquina virtual do Azure para resolução de nomes locais e de intranet (replicação e encaminhamento de DNS)  <br/> |
   
 **Tabela 4: opções de servidor DNS para os dois tipos diferentes de VNets**
  
Para obter mais informações, consulte [resolução de nomes para VMs e instâncias de função](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>Etapa 7: determinar a configuração de balanceamento de carga (voltada para a Internet ou interna).

Em alguns casos, você deseja distribuir o tráfego de entrada para um conjunto de servidores que têm a mesma função. O Azure IaaS tem um recurso interno para fazer isso para cargas de tráfego internas e voltadas para a Internet.
  
O balanceamento de carga voltado para a Internet do Azure distribui aleatoriamente o tráfego de entrada não solicitado da Internet para os membros de um conjunto de balanceamento de carga.
  
**Figura 4: um balanceador de carga externo no Azure**

![Figura 4: um balanceador de carga externo no Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
A Figura 4 mostra um balanceador de carga externo no Azure que distribui o tráfego de entrada em uma regra NAT de entrada ou ponto de extremidade para um conjunto de máquinas virtuais em um conjunto de balanceamento de carga.
  
O balanceamento de carga interno do Azure distribui aleatoriamente o tráfego de entrada não solicitado de outras VMs do Azure ou de computadores de intranet para os membros de um conjunto de balanceamento de carga. 
  
**Figura 5: um balanceador de carga interno no Azure**

![Figura 5: um balanceador de carga interno no Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
A Figura 5 mostra um balanceador de carga interno no Azure que distribui o tráfego de entrada em uma regra NAT de entrada ou ponto de extremidade para um conjunto de máquinas virtuais em um conjunto de balanceamento de carga.
  
Para saber mais, confira balanceador de [carga do Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>Etapa 8: determinar o uso de dispositivos virtuais e rotas definidas pelo usuário.

Se você precisar encaminhar o tráfego para dispositivos virtuais em sua VNet, talvez seja necessário adicionar uma ou mais rotas definidas pelo usuário a uma sub-rede.
  
**Figura 6: dispositivos virtuais e rotas definidas pelo usuário no Azure**

![Figura 6: dispositivos virtuais e rotas definidas pelo usuário no Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
A Figura 6 mostra uma VNet entre locais e uma rota definida pelo usuário atribuída a uma sub-rede de Hospedagem de máquina virtual que aponta para um dispositivo virtual.
  
Para obter mais informações, consulte [rotas definidas pelo usuário e encaminhamento de IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>Etapa 9: determinar como os computadores da Internet se conectarão às máquinas virtuais.

Há várias maneiras de fornecer acesso à Internet para as máquinas virtuais em uma VNet, que inclui o acesso da rede da sua organização através do servidor proxy ou de outro dispositivo de borda.
  
A tabela 5 lista os métodos para filtrar ou inspecionar tráfego de entrada não solicitado.
  
|**Method**|**Modelo de implantação**|
|:-----|:-----|
|1. pontos de extremidade e ACLs configurados nos serviços de nuvem  <br/> |Clássico  <br/> |
|2. grupos de segurança de rede  <br/> |Gerenciador de recursos e clássico  <br/> |
|3. balanceador de carga voltado para a Internet com regras de NAT de entrada  <br/> |Gerente de Recursos  <br/> |
|4. dispositivos de segurança de rede no Azure Marketplace (não mostrado)  <br/> |Gerenciador de recursos e clássico  <br/> |
   
 **Tabela 5: métodos de conexão com máquinas virtuais e seus modelos de implantação do Azure correspondentes**
  
**Figura 7: conectando-se às máquinas virtuais do Azure pela Internet**

![Figura 7: conectando-se às máquinas virtuais do Azure pela Internet](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
A Figura 7 mostra um computador conectado à Internet que se conecta a uma máquina virtual em um serviço de nuvem usando um ponto de extremidade, uma máquina virtual em uma sub-rede usando um grupo de segurança de rede e uma máquina virtual em uma sub-rede usando um balanceador de carga externo e regras de NAT de entrada.
  
A segurança adicional é fornecida por:
  
- Conexões SSH e de área de trabalho remota, que são autenticadas e criptografadas.
    
- Sessões remotas do PowerShell, que são autenticadas e criptografadas.
    
- Modo de transporte IPsec, que você pode usar para a criptografia de ponta a ponta.
    
- Proteção contra DDOS do Azure, que ajuda a evitar ataques externos e internos
    
Para obter mais informações, consulte [segurança de nuvem da Microsoft para arquitetos corporativos](https://aka.ms/cloudarchsecurity) e [segurança de rede do Azure](https://azure.microsoft.com/blog/azure-network-security/).
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>Etapa 10: para vários VNets, determine a topologia de conexão VNet para VNet.

O VNets pode ser conectado entre si usando topologias semelhantes àquelas usadas para conectar os sites de uma organização.
  
Uma configuração de correntes de Margarida conecta o VNets em uma série.
  
**Figura 8: uma configuração de correntes para VNets**

![Figura 8: uma configuração de correntes para redes virtuais do Azure](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
A Figura 8 mostra cinco VNets conectados à série usando uma configuração de correntes.
  
Uma configuração de Hub e spoke conecta vários VNets a um conjunto de VNets central, que são conectados uns aos outros.
  
**Figura 9: uma configuração de Hub e spoke para VNets**

![Figura 9: uma configuração de Hub e spoke para redes virtuais do Azure](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
A Figura 9 mostra seis VNets, dois VNets são hubs conectados uns aos outros e também dois outros VNets de spoke.
  
Uma configuração de malha completa conecta cada VNet entre si.
  
**Figura 10: uma configuração de malha completa para O VNets**

![Figura 10: uma configuração de malha para redes virtuais do Azure](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
A Figura 10 mostra quatro VNets que estão conectadas entre si, usando um total de seis conexões de VNet para VNet.
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>Planejamento de etapas para uma VNet entre locais
<a name="cross_prem"> </a>

Siga estas etapas para uma VNet entre locais.
  
> [!TIP]
> Para criar um ambiente simulado de desenvolvimento/teste entre instalações, confira a [rede virtual simulada entre locais no Azure](simulated-cross-premises-virtual-network-in-azure.md). 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>Etapa 1: determinar a conexão entre locais com a VNet (VPN S2S ou ExpressRoute).

A tabela 6 lista os diferentes tipos de conexões.
  
|**Tipo de conexão**|**Objetivo**|
|:-----|:-----|
|VPN de site a site (S2S)  <br/> |Conecte 1-10 sites (incluindo outros VNets) a uma única VNet.  <br/> |
|ExpressRoute  <br/> |Um link privado e seguro para o Azure por meio de um provedor de Internet (IXP) ou de um provedor de serviços de rede (NSP).  <br/> |
|VPN ponto a site (P2S)  <br/> |Conecta um único computador a uma VNet.  <br/> |
|Emparelhamento de VNet ou VPN de rede virtual (V2V)  <br/> |Conecta uma VNet a outra VNet.  <br/> |
   
 **Tabela 6: os tipos de conexões para o VNets entre locais**
  
Para obter mais informações sobre o número máximo de conexões, consulte [limites de rede](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).
  
Para obter mais informações sobre dispositivos VPN, consulte [dispositivos VPN para conexões de rede virtual de site a site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Para obter mais informações sobre emparelhamento de rede virtual, consulte [emparelhamento de vnet](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).
  
**Figura 11: as quatro maneiras de se conectar a uma VNet entre locais**

![Figura 11: as três maneiras de se conectar a uma rede virtual do Azure entre locais](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
A Figura 11 mostra uma VNet com os quatro tipos de conexões: uma conexão do P2S de um computador, uma conexão VPN S2S de uma rede local, uma conexão ExpressRoute de uma rede local e uma conexão de VNet para VNet de outra VNet. 
  
Você pode se conectar a VMs em uma VNet das seguintes maneiras:
  
- Administração de VMs de VNet de sua rede local ou da Internet
    
- Acesso de carga de trabalho da sua rede local
    
- Extensão de sua rede por meio de VNets adicionais
    
A segurança para conexões é fornecida pelo seguinte:
  
- O P2S usa o SSTP (Secure Socket Tunneling Protocol) 
    
- Conexões VPN S2S e VNet para VNet usam o modo de encapsulamento IPsec com AES256
    
- O ExpressRoute é uma conexão WAN privada
    
Para obter mais informações, consulte [segurança de nuvem da Microsoft para arquitetos corporativos](https://aka.ms/cloudarchsecurity) e [segurança de rede do Azure](https://azure.microsoft.com/blog/azure-network-security/).
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>Etapa 2: determinar o roteador ou dispositivo VPN local.

Seu roteador ou dispositivo VPN local atua como:
  
- Um ponto IPsec, terminando a conexão VPN S2S do gateway do Azure.
    
- O par de BPG e o ponto de terminação para a conexão rota de emparelhamento privado.
    
**Figura 12: o roteador ou dispositivo VPN local**

![Figura 12: o roteador ou dispositivo VPN local](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
A Figura 12 mostra uma VNet entre locais conectada a um roteador ou dispositivo VPN local.
  
Para obter mais informações, consulte [sobre o gateway VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>Etapa 3: adicionar rotas à sua intranet para tornar o espaço de endereço da VNet alcançável.

O roteamento para o VNets no local consiste no seguinte:
  
1. Uma rota para o espaço de endereço da VNet que aponta para o seu dispositivo VPN.
    
2. Uma rota para o espaço de endereço da VNet no seu dispositivo VPN que aponta entre a conexão VPN S2S ou ExpressRoute
    
**Figura 13: rotas locais necessárias para tornar uma VNet alcançável**

![Figura 13: rotas locais necessárias para tornar uma VNet do Azure alcançável](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
A Figura 13 mostra as informações de roteamento necessárias para os roteadores locais e o roteador ou dispositivo VPN que representa o espaço de endereço da VNet.
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>Etapa 4: para o ExpressRoute, planeje a nova conexão com seu provedor.

Você pode criar uma conexão ExpressRoute com emparelhamento privado entre sua rede local e a nuvem da Microsoft de três maneiras diferentes:
  
- Localizado em um Exchange na nuvem
    
- Conexões Ethernet ponto a ponto
    
- Redes IP de qualquer um (VPN)
    
**Figura 14: usando o ExpressRoute para se conectar a uma VNet entre locais**

![Figura 14: usando o ExpressRoute para se conectar a uma rede virtual do Azure entre locais](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
A Figura 14 mostra um VNet entre locais e uma conexão ExpressRoute de um roteador local para o Microsoft Azure.
  
Para obter mais informações, consulte [ExpressRoute for Microsoft Cloud Connectivity](expressroute-for-microsoft-cloud-connectivity.md).
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>Etapa 5: determinar o espaço de endereço de rede local para o gateway do Azure.

Para o roteamento para o local ou outro VNets de uma VNet, o Azure encaminha o tráfego em um gateway do Azure que corresponde ao espaço de endereço de rede local atribuído ao gateway.
  
**Figura 15: o espaço de endereço de rede local para uma VNet entre locais**

![Figura 15: o espaço de endereço de rede local para uma rede virtual do Azure entre locais](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
A Figura 15 mostra uma VNet entre locais e o espaço de endereço de rede local no gateway do Azure, que representa o espaço de endereço alcançável na rede local. 
  
Você pode definir o espaço de endereço de rede local das seguintes maneiras:
  
- Opção 1: a lista de prefixos para o espaço de endereço atualmente necessário ou em uso (as atualizações podem ser necessárias ao adicionar novas sub-redes).
    
- Opção 2: seu espaço de endereço local completo (atualizações necessárias apenas quando você adiciona novo espaço de endereçamento).
    
Como o portal do Azure não permite rotas resumidas, você deve definir o espaço de endereço da rede local para a opção 2 para que ele não inclua o espaço de endereço da VNet.
  
**Figura 16: o orifício do espaço de endereçamento criado pelo espaço de endereço da rede virtual**

![Figura 16: o orifício do espaço de endereçamento criado pelo espaço de endereço da rede virtual](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
A Figura 16 mostra uma representação de um espaço de endereçamento, com o espaço raiz e o espaço de endereço da VNet.
  
Veja um exemplo de como definir os prefixos para o espaço de endereço de rede local em torno do espaço de endereçamento "buraco" criado pela VNet:
  
- Uma organização usa partes do espaço de endereçamento privado (10.0.0.0/8, 172.16.0.0/12 e 192.168.0.0/16) em toda a sua rede local. Eles escolheram a opção 2 e 10.100.100.0/24 como seu espaço de endereço de rede virtual.
    
A tabela 7 mostra as etapas e prefixos resultantes que definem o espaço de endereço de rede local para este exemplo.
  
|**Etapa**|**Resultados**|
|:-----|:-----|
|1. liste os prefixos que não são o espaço raiz do espaço de endereço da VNet.  <br/> |172.16.0.0/12 e 192.168.0.0/16  <br/> |
|2. listar os prefixos não sobrepostos de octetos variáveis até mas não incluindo o último octeto usado no espaço de endereço da rede virtual.  <br/> |10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 prefixos, ignorando o 10.100.0.0/16)  <br/> |
|3. listar os prefixos não sobrepostos no último octeto usado do espaço de endereço da VNet.  <br/> |10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 prefixos, ignorando 10.100.100.0/24)  <br/> |
   
 **Tabela 7: exemplo de espaço de rede de endereços locais**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>Etapa 6: configurar os servidores DNS locais para replicação de DNS com servidores DNS hospedados no Azure.

Para garantir que os computadores locais possam resolver os nomes de servidores baseados no Azure e servidores baseados no Azure podem resolver os nomes de computadores locais, configure:
  
- Os servidores DNS de sua VNet para encaminhar para servidores DNS locais
    
- Replicação de DNS das zonas apropriadas entre os servidores DNS no local e na VNet
    
**Figura 17: replicação e encaminhamento de DNS para um servidor DNS em uma VNet entre locais**

![Figura 17: replicação e encaminhamento de DNS para um servidor DNS em uma rede virtual do Azure entre locais](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
A figura 17 mostra uma VNet entre locais com servidores DNS na rede local e em uma sub-rede na VNet. A replicação e o encaminhamento de DNS foram configurados entre os dois servidores DNS.
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>Etapa 7: determinar o uso de encapsulamento forçado.

A rota padrão do sistema para sub-redes do Azure aponta para a Internet. Para garantir que todo o tráfego de máquinas virtuais percorra a conexão entre locais, crie uma tabela de roteamento com a rota padrão que usa o gateway do Azure como seu endereço de próximo salto. Você associa a tabela de rotas à sub-rede. Isso é conhecido como encapsulamento forçado. Para obter mais informações, consulte [Configure FORCED Tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).
  
**Figura 18: rotas definidas pelo usuário e encapsulamento forçado para uma VNet entre locais**

![Figura 18: rotas definidas pelo usuário e encapsulamento forçado para uma rede virtual do Azure entre locais](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
A Figura 18 mostra uma VNet entre locais com uma rota definida pelo usuário para uma sub-rede apontando para o gateway do Azure.
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>Farm do SharePoint Server 2016 no Azure
<a name="cross_prem"> </a>

Um exemplo de uma carga de trabalho de ti de intranet hospedada no Azure IaaS é um farm do SharePoint Server 2016 de várias camadas altamente disponível.
  
**Figura 19: um farm do SharePoint Server 2016 de intranet altamente disponível no Azure IaaS**

![Um farm do SharePoint Server 2016 de alta disponibilidade no Azure IaaS](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
A Figura 19 mostra os nove servidores de um farm do SharePoint Server 2016 implantado em uma VNet entre locais que usa balanceadores de carga internos para as camadas de front-end e de dados. Para obter mais informações, incluindo instruções passo a passo de design e implantação, consulte [SharePoint Server 2016 no Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).
  
> [!TIP]
> Para criar um farm de servidor único do SharePoint Server 2016 em uma VNet de várias instalações simulada, confira [intranet SharePoint server 2016 in Azure dev/Test Environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment). 
  
Para obter exemplos adicionais de cargas de trabalho de ti implantadas em máquinas virtuais em uma rede virtual do Azure entre locais, consulte [cenários de nuvem híbrida para o Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).
  
## <a name="see-also"></a>Confira também

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)


