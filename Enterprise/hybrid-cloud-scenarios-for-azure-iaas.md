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
description: 'Resumo: entenda a arquitetura híbrida e os cenários para ofertas de nuvem com base na infraestrutura do Microsoft de serviço (IaaS) no Azure.'
ms.openlocfilehash: d3f4b4ccbc9dbfa54e6f1d0988624aeb71f27106
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741357"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Cenários de nuvem híbrida para a IaaS do Azure

 **Resumo:** Compreenda a arquitetura híbrida e os cenários para ofertas de nuvem baseadas na infraestrutura da Microsoft como um serviço (IaaS) no Azure.
  
Estenda a infraestrutura de computação e identidade local para a nuvem hospedando cargas de trabalho de ti em execução em redes virtuais do Azure entre locais (VNets). 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Arquitetura de cenário híbrido do Azure IaaS

A Figura 1 mostra a arquitetura dos cenários híbridos baseados no Microsoft IaaS no Azure.
  
**Figura 1: cenários híbridos baseados no Microsoft IaaS no Azure**

![Cenários híbridos baseados no Microsoft IaaS no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
Para cada camada da arquitetura:
  
- Aplicativos e cenários
    
    Uma carga de trabalho de ti normalmente é um aplicativo de várias camadas e altamente disponível composto de VMs (máquinas virtuais) do Azure.
    
- Identidade
    
    Adicione servidores de identidade, como controladores de domínio dos serviços de domínio do Active Directory (AD DS), ao conjunto de servidores em execução no Azure VNets para autenticação local.
    
- Rede
    
    Use uma conexão VPN de site para site pela Internet ou uma conexão ExpressRoute com emparelhamento privado para o Azure IaaS.
    
- Local
    
    Contém servidores de identidade que são sincronizados com os servidores de identidade em execução no Azure. Também pode conter recursos que as VMs em execução no Azure podem acessar, como a infraestrutura de gerenciamento de armazenamento e de sistemas.
    
## <a name="directory-synchronization-server-for-office-365"></a>Servidor de sincronização de diretório para o Office 365

Executar seu servidor de sincronização de diretório a partir de uma VNet do Azure, conforme mostrado na Figura 2, é um exemplo de estender sua infraestrutura de computação e identidade para a nuvem.
  
**Figura 2: servidor de sincronização de diretório para o Office 365 no Azure IaaS**

![Servidor de sincronização de diretório para o Office 365 no Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
Na Figura 2, uma rede local hospeda uma infraestrutura do AD DS, com um servidor proxy e um roteador em sua borda. O roteador conecta-se a um gateway do Azure na borda de uma VNet do Azure com uma conexão VPN de site a site ou ExpressRoute. Dentro da VNet, um servidor de sincronização de diretório executa o Azure AD Connect.
  
Um servidor de sincronização de diretório para o Office 365 sincroniza a lista de contas no AD DS com o locatário do Azure AD de uma assinatura do Office 365.
  
Um servidor de sincronização de diretório é um servidor baseado em Windows que executa o Azure AD Connect. Para o provisionamento mais rápido ou para reduzir o número de servidores locais em sua organização, implante seu servidor de sincronização de diretório em uma rede virtual (VNet) no Azure IaaS.
  
O servidor de sincronização de diretório sonda alterações no AD DS e, em seguida, sincroniza-as com a assinatura do Office 365.
  
Para obter mais informações, consulte [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).
  
## <a name="line-of-business-lob-application"></a>Aplicativo de linha de negócios (LOB)

A Figura 3 mostra a configuração de um aplicativo LOB baseado em servidor executado no Azure IaaS.
  
**Figura 3: aplicativo LOB no Azure IaaS**

![Aplicativo LOB baseado em servidor no Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
Na Figura 3, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão VPN de site a site ou ExpressRoute. O Azure IaaS hospeda uma rede virtual contendo os servidores do aplicativo LOB.
  
Você pode criar aplicativos LOB executados em VMs do Azure, que residem em sub-redes de uma VNet do Azure em um datacenter do Azure (também conhecido como local).
  
Como você está essencialmente estendindo sua infraestrutura local para o Azure, você deve atribuir um espaço de endereçamento privado exclusivo ao seu VNets e atualizar suas tabelas de roteamento local para garantir a acessibilidade a cada VNet.
  
Depois de conectado, essas VMs podem ser gerenciadas com as conexões da área de trabalho remota ou com seu software de gerenciamento de sistema, assim como os servidores locais.
  
Configurando portas expostas publicamente, essas VMs também podem ser acessadas pela Internet por usuários móveis ou remotos.
  
Para obter uma configuração de prova de conceito, confira a [rede virtual de interlocalização entre locais no Azure](simulated-cross-premises-virtual-network-in-azure.md).
  
Os atributos de aplicativos LOB hospedados nas VMs do Azure são os seguintes:
  
- Várias camadas
    
    Aplicativos LOB típicos usam uma abordagem em camadas. Os conjuntos de servidores fornecem identidade, processamento de banco de dados, processamento de aplicativo e lógica e servidores Web front-end para acesso de funcionário ou de cliente. 
    
- Alta disponibilidade
    
    Aplicativos LOB típicos fornecem alta disponibilidade usando vários servidores em cada camada. O Azure IaaS fornece um SLA de tempo de atividade de 99,9% para servidores nos conjuntos de disponibilidade do Azure. 
    
- Distribuição de carga
    
    Para distribuir a carga do tráfego de rede entre vários servidores em uma camada, você pode usar um balanceador de carga interno ou voltado para a Internet. Ou você pode usar um dispositivo balanceador de carga dedicado disponível no Azure Marketplace.
    
- Segurança
    
    Para proteger os servidores de tráfego de entrada não solicitado da Internet, você pode usar os grupos de segurança de rede do Azure. Você pode definir o tráfego permitido ou negado para uma sub-rede ou interface de rede de uma máquina virtual individual.
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Farm do SharePoint Server 2016 no Azure

Um exemplo de um aplicativo LOB de várias camadas e altamente disponível no Azure é um farm do SharePoint Server 2016, conforme mostrado na Figura 4.
  
**Figura 4: um farm do SharePoint Server 2016 de alta disponibilidade no Azure IaaS**

![Um farm do SharePoint Server 2016 de alta disponibilidade no Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
Na Figura 4, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão VPN de site a site ou ExpressRoute. A VNet do Azure contém os servidores do farm do SharePoint Server 2016, que inclui camadas separadas para os servidores front-end, os servidores de aplicativos, o cluster do SQL Server e os controladores de domínio.
  
Essa configuração tem os seguintes atributos de aplicativos LOB no Azure: 
  
- Camadas
    
    Servidores executando diferentes funções dentro do farm criam as camadas e cada camada tem sua própria sub-rede.
    
- Alta disponibilidade
    
    Alcançado usando mais de um servidor em cada camada e colocando todos os servidores de uma camada no mesmo conjunto de disponibilidade.
    
- Distribuição de carga
    
    Balanceadores de carga internos do Azure distribuem o tráfego da Web do cliente de entrada para os servidores front-end (WEB1 e WEB2) e para o endereço IP do ouvinte do cluster do SQL Server (SQL1, SQL2 e MN1).
    
- Segurança
    
    Os grupos de segurança de rede de cada sub-rede permitem configurar o tráfego de entrada e de saída permitido.
    
Siga este caminho para adoção bem-sucedida:
  
1. Avaliar e testar
    
    Consulte [SharePoint server 2016 no Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) para compreender os benefícios da execução do sharepoint Server 2016 no Azure.
    
    Consulte [intranet do SharePoint Server 2016 no ambiente de desenvolvimento/teste do Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) para criar um ambiente simulado de desenvolvimento/teste
    
2. Design
    
    Consulte [Designing a SharePoint Server 2016 Farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) para percorrer um processo para determinar o conjunto de elementos de rede, computação e armazenamento do Azure IaaS para hospedar seu farm e suas configurações.
    
3. Implantar
    
    Consulte [deployIng SharePoint server 2016 with SQL Server AlwaysOn Availability groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) para percorrer a configuração de ponta a ponta do farm de alta disponibilidade em cinco fases.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identidade federada para o Office 365 no Azure

Outro exemplo de um aplicativo LOB de várias camadas e altamente disponível no Azure é a identidade federada para o Office 365.
  
**Figura 5: uma infraestrutura de identidade federada de alta disponibilidade para o Office 365 no Azure IaaS**

![Uma infraestrutura de autenticação federada de alta disponibilidade do Office 365 no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
Na Figura 5, uma rede local hospeda uma infraestrutura de identidade e usuários. Ele está conectado a um gateway do Azure IaaS com uma conexão VPN de site a site ou ExpressRoute. A VNet do Azure contém servidores de proxy da Web, servidores de serviços de Federação do Active Directory (AD FS) e controladores de domínio do AD DS (serviços de domínio Active Directory).
  
Essa configuração tem os seguintes atributos de aplicativos LOB no Azure:
  
- **Camadas:** Há camadas para servidores de proxy da Web, servidores do AD FS e controladores de domínio do AD DS.
    
- **Distribuição de carga:** Um balanceador de carga externo do Azure distribui as solicitações de autenticação de cliente de entrada para os proxies web e um balanceador de carga interno do Azure distribui solicitações de autenticação para os servidores do AD FS.
    
Siga este caminho para adoção bem-sucedida:
  
1. Avaliar e testar
    
    Consulte [identidade federada para seu ambiente de desenvolvimento/teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md) para criar um ambiente simulado de desenvolvimento/teste para autenticação federada com o Office 365.
    
2. Implantar
    
    Consulte [implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para percorrer a configuração de ponta a ponta da infraestrutura do AD FS de alta disponibilidade em cinco fases.
    
    
## <a name="see-also"></a>Confira também


[Nuvem híbrida da Microsoft para arquitetos corporativos](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)


