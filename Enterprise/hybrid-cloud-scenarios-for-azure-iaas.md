---
title: Cenários de nuvem híbrida para a IaaS do Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 'Resumo: Entenda os cenários e arquitetura híbrida para a infra-estrutura da Microsoft como um serviço (IaaS)-based ofertas de nuvem no Windows Azure.'
ms.openlocfilehash: 441565adae46d50ad1b7139525ff3146c5f88ca3
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181032"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Cenários de nuvem híbrida para a IaaS do Azure

 **Resumo:** Entenda os cenários e arquitetura híbrida para a infra-estrutura da Microsoft como um serviço (IaaS)-based ofertas de nuvem no Windows Azure.
  
Estender sua computação no local e a infra-estrutura de identidades em nuvem hospedando cargas de trabalho do IT executando em locais cruzados redes virtuais do Azure (VNets). 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Arquitetura de cenário do Windows Azure IaaS híbrida

A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em IaaS Microsoft no Azure.
  
**Figura 1: Cenários de implantação híbrida baseada em IaaS Microsoft no Azure**

![Cenários híbridos da Microsoft baseados em IaaS no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
Para cada camada da arquitetura:
  
- Cenários e aplicativos
    
    Uma carga de trabalho de TI é geralmente uma de várias camadas, aplicativo altamente disponível composto de máquinas virtuais do Azure (VMs).
    
- Identidade
    
    Adicione servidores de identidade, como controladores de domínio do Windows Server AD, ao conjunto de servidores que executam em VNets do Windows Azure para a autenticação local.
    
- Rede
    
    Use uma conexão de VPN-to-site via Internet ou uma conexão ExpressRoute com correspondência privada para Azure IaaS.
    
- Local
    
    Contém os servidores de identidade que são sincronizados com os servidores de identidade em execução no Windows Azure. Também pode conter recursos que podem acessar VMs em execução no Azure, como a infraestrutura de gerenciamento de armazenamento e sistemas.
    
## <a name="directory-synchronization-server-for-office-365"></a>Servidor de sincronização de diretório para o Office 365

Executar o seu servidor de sincronização de diretório de um VNet do Azure, conforme mostrado na Figura 2, é um exemplo de estendendo sua infra-estrutura de computação e identidade para a nuvem.
  
**Figura 2: Servidor de sincronização de diretório para o Office 365 no Azure IaaS**

![Servidor de sincronização de diretório para o Office 365 no Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
Na Figura 2, uma rede local hospeda uma infraestrutura do Windows Server AD, com um servidor proxy e um roteador em sua borda. O roteador conecta-se para um gateway Azure na extremidade de uma VNet Azure com uma conexão de VPN ou ExpressRoute-to-site. Dentro do VNet, um servidor de sincronização de diretório executa Connect do Azure AD.
  
Um servidor de sincronização de diretório para o Office 365 sincroniza a lista de contas no Windows Server AD com o locatário do Azure AD de uma assinatura do Office 365.
  
Um servidor de sincronização de diretório é um servidor baseado no Windows que executa o Connect do Azure AD. Para provisionamento mais rápidos ou reduzir o número de servidores locais em sua organização, implante seu servidor de sincronização de diretório em uma rede virtual (VNet) no Windows Azure IaaS.
  
O servidor de sincronização de diretório sonda Windows Server AD para que as alterações e sincroniza-los com assinatura do Office 365.
  
Para obter mais informações, consulte [Implantar o Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).
  
## <a name="line-of-business-lob-application"></a>Linha do aplicativo de negócios (LOB)

A Figura 3 mostra a configuração de um aplicativo de LOB baseado em servidor está em execução no Azure IaaS.
  
**Figura 3: Aplicativos de LOB no Azure IaaS**

![Aplicativo LOB baseado em servidor na IaaS do Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
Na Figura 3, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão de VPN ou ExpressRoute-to-site. Azure IaaS hospeda uma rede virtual que contém os servidores do aplicativo LOB.
  
Você pode criar aplicativos de LOB executados em máquinas virtuais do Windows Azure, que residem em sub-redes de uma VNet do Windows Azure em um datacenter do Windows Azure (também conhecido como um local).
  
Porque você essencialmente estiver estendendo sua infraestrutura local no Azure, você deve atribuir o espaço de endereço privado exclusivo ao seu VNets e atualizar o seu local tabelas de roteamento para garantir o alcance a cada VNet.
  
Uma vez conectado, essas VMs podem ser gerenciadas com conexões de área de trabalho remota ou com o software de gerenciamento de sistemas, assim como os servidores no local.
  
Configurando portas expostas publicamente, essas VMs também podem ser acessados pela Internet por usuários remotos ou móveis.
  
Para uma configuração de prova de conceito, consulte [simuladas locais cruzados rede virtual no Windows Azure](simulated-cross-premises-virtual-network-in-azure.md).
  
Atributos de aplicativos de LOB hospedados em máquinas virtuais do Windows Azure são as seguintes:
  
- Vários níveis
    
    Os aplicativos de LOB típicos usam uma abordagem hierárquica. Conjuntos de servidores fornecem a identidade, processamento de banco de dados, aplicativo e processamento de lógica e servidores web front-end para acesso de funcionários ou clientes. 
    
- Alta disponibilidade
    
    Os aplicativos de LOB típicos fornecem alta disponibilidade por meio de vários servidores em cada camada. Azure IaaS fornece um SLA do tempo de atividade de 99,9% para servidores em conjuntos de disponibilidade do Azure. 
    
- Distribuição de carga
    
    Para distribuir a carga de tráfego de rede entre vários servidores em uma camada, você pode usar um balanceador de carga de Azure voltado à Internet ou interna. Ou então, você pode usar um aparelho de Balanceador de carga dedicado disponível no Azure marketplace.
    
- Segurança
    
    Para proteger os servidores de tráfego de entrada não solicitado da Internet, você pode usar grupos de segurança de rede do Windows Azure. Você pode definir permitido ou negado o tráfego de uma sub-rede ou a interface de rede de uma máquina virtual individual.
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Farm do SharePoint Server 2016 no Windows Azure

Um exemplo de um de várias camadas, os aplicativos LOB altamente disponível no Windows Azure é um farm do SharePoint Server 2016, conforme mostrado na Figura 4.
  
**Figura 4: Um farm de SharePoint Server 2016 de alta disponibilidade no Azure IaaS**

![Farm de alta disponibilidade do SharePoint Server 2016 no Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
Na Figura 4, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão de VPN ou ExpressRoute-to-site. VNet o Azure contém os servidores do farm do SharePoint Server 2016, que inclui as camadas separadas para os servidores front-end, servidores de aplicativos, o cluster do SQL Server e os controladores de domínio.
  
Esta configuração tem os seguintes atributos de aplicativos LOB no Windows Azure: 
  
- Camadas
    
    Servidores que executam funções diferentes dentro do farm criam as camadas, e cada camada tem sua própria sub-rede.
    
- Alta disponibilidade
    
    Obtida usando mais de um servidor em cada camada e colocar todos os servidores de uma camada no mesmo conjunto de disponibilidade.
    
- Distribuição de carga
    
    Balanceadores de carga Azure interno distribui o tráfego web cliente entrada para os servidores front-end (WEB1 e WEB2) e o endereço IP do ouvinte do cluster do SQL Server (SQL1, SQL2 e MN1).
    
- Segurança
    
    Grupos de segurança de rede para cada sub-rede permitem que você para configurar o tráfego de entrada e saído permitido.
    
Siga este caminho para a adoção bem-sucedida:
  
1. Avaliar e testar
    
    Consulte [2016 do SharePoint Server in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) compreender as vantagens de executar o SharePoint Server 2016 no Windows Azure.
    
    Consulte [Intranet do SharePoint Server 2016 no ambiente de desenvolvimento e teste do Windows Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) para criar um ambiente de desenvolvimento e teste simulados
    
2. Design
    
    Consulte [Projetando um farm do SharePoint Server 2016 no Windows Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) para passar por um processo para determinar o conjunto de rede do Azure IaaS, compute e elementos de armazenamento para hospedar seu farm e suas configurações.
    
3. Implantar
    
    Consulte [Implantando o SharePoint Server 2016 com grupos de disponibilidade do SQL Server AlwaysOn no Windows Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) para percorrer a configuração de ponta a ponta do farm de alta disponibilidade em cinco fases.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identidade federada para o Office 365 no Windows Azure

Outro exemplo de um aplicativo de LOB de várias camado, altamente disponível no Windows Azure é a identidade federada para o Office 365.
  
**Figura 5: Uma infraestrutura de identidade federada de alta disponibilidade para o Office 365 no Azure IaaS**

![Uma alta disponibilidade Office 365 federados a infraestrutura de autenticação no Windows Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
Na Figura 5, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão de VPN ou ExpressRoute-to-site. VNet o Azure contém servidores proxy da web, servidores de serviços de Federação do Active Directory (AD FS) e controladores de domínio do Windows Server AD (Active Directory).
  
Esta configuração tem os seguintes atributos de aplicativos LOB no Windows Azure:
  
- **Camadas:** Há camadas para servidores proxy da web, servidores do AD FS e controladores de domínio do Windows Server AD.
    
- **Distribuição de carga:** Um balanceador de carga Azure externo distribui as solicitações de autenticação de cliente recebidas para os proxies de web e um balanceador de carga Azure interno distribui solicitações de autenticação para os servidores do AD FS.
    
Siga este caminho para a adoção bem-sucedida:
  
1. Avaliar e testar
    
    Consulte a [identidade federada para seu ambiente de desenvolvimento e teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md) para criar um ambiente de desenvolvimento e teste simulado para autenticação federada com o Office 365.
    
2. Implantar
    
    Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para percorrer a configuração de ponta a ponta da infraestrutura AD FS alta disponibilidade em cinco fases.
    
    
## <a name="see-also"></a>Confira também

[Nuvem híbrida da Microsoft para Arquitetos Corporativos](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)


