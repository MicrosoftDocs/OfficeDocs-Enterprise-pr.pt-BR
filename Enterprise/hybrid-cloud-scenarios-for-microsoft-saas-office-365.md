---
title: Cenários de nuvem híbrida para Microsoft SaaS (Office 365)
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
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Resumo: entenda a arquitetura híbrida e os cenários de ofertas de nuvem baseadas em SaaS da Microsoft (Office 365).'
ms.openlocfilehash: 90b751e4bbea42d723961eb2ac339d23faf8c259
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741387"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Cenários de nuvem híbrida para Microsoft SaaS (Office 365)

 **Resumo:** Compreenda a arquitetura híbrida e os cenários de ofertas de nuvem baseadas em SaaS da Microsoft (Office 365).
  
Combine implantações locais do Exchange, SharePoint ou Skype for Business com seus correspondentes no Office 365 como parte de uma migração em nuvem ou uma estratégia de integração de longo prazo.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Arquitetura de cenário híbrido Microsoft SaaS

A Figura 1 mostra a arquitetura dos cenários híbridos baseados em SaaS da Microsoft para o Office 365.
  
**Figura 1: cenários híbridos baseados em SaaS da Microsoft para o Office 365**

![Cenários híbridos baseados em SaaS da Microsoft para o Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
Para cada camada da arquitetura:
  
- Aplicativos e cenários
    
    Há uma variedade de cenários híbridos baseados em SaaS, que se alinha ao redor dos produtos do Office Server e seus correspondentes no Office 365:
    
  - Exchange Server combinado com o Exchange Online (Exchange Server híbrido)
    
  - Skype for Business Server combinado com o Skype for Business Online e os novos cenários de Cloud PBX e Cloud Connector Edition
    
  - SharePoint Server 2019, SharePoint Server 2016 ou SharePoint Server 2013 combinado com o SharePoint Online (vários cenários)
    
    Há também o Exchange Online com o Skype for Business Server no local, um cenário híbrido entre produtos.
    
- Identidade
    
    Pode incluir a sincronização de diretórios com os serviços de domínio do Active Directory (AD DS) local. Como alternativa, é possível configurar o Azure AD para federação com um provedor de identidade de terceiros.
    
- Rede
    
    O consiste no seu pipe existente na Internet ou em uma conexão ExpressRoute com o emparelhamento da Microsoft para o Office 365 ou Dynamics 365.
    
- Local
    
    Pode consistir em servidores existentes para o Exchange, o SharePoint e o Skype for Business, que devem ser atualizados para suas versões mais recentes. Em seguida, você pode combiná-los com seus correspondentes do Office 365 para cenários híbridos.
    
Configure seu próprio ambiente de desenvolvimento/teste do Office 365, confira [guias de laboratório de teste do office 365](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Skype for Business híbrido

O Skype for Business híbrido permite combinar uma implantação local existente com o Skype for Business online. Alguns usuários estão hospedados no local e alguns usuários estão hospedados online, mas os usuários compartilham o mesmo domínio SIP (Session Initiation Protocol), como contoso.com. Você pode usar essa configuração híbrida para migrar do local para o Office 365 com o tempo, no seu cronograma. O Skype for Business também pode ser integrado ao [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).
  
**Figura 2: a configuração híbrida do Skype for Business**

![A configuração híbrida do Skype for Business](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
A Figura 2 mostra a configuração híbrida do Skype for Business, que consiste em um pool de front-ends do Skype for Business local e um servidor de borda se comunicando com o Skype for Business online no Office 365.
  
Para obter mais informações, consulte [Plan Hybrid Connectivity between Skype for Business Server e Skype for Business online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Cloud PBX com o Skype for Business Server

O Cloud PBX com o Skype for Business Server permite que você migre uma implantação local existente do Skype for Business Server para uma topologia com conectividade PSTN (rede telefônica pública comutada) local. 
  
**Figura 3: Cloud PBX com o Skype for Business Server**

![Cloud PBX com o Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
A Figura 3 mostra o Cloud PBX com a configuração do Skype for Business Server, consistindo em um PBX existente local ou gateway Telco, um Skype for Business Server e o PSTN conectado ao Cloud PBX da Microsoft no Office 365, que inclui o Skype for Business Modo.
  
Os usuários da organização que estão hospedados na nuvem podem receber serviços de PBX (central privada de comutação telefônica) da nuvem da Microsoft que incluem sinalização e caixa postal, mas a conectividade PSTN (sinal de discagem) é fornecida pelo Enterprise Voice de seu local Implantação do Skype for Business Server.
  
Este é um ótimo exemplo de uma configuração híbrida que permite migrar gradualmente para um serviço baseado em nuvem. Você pode manter os recursos de voz de seus usuários ao começar a movê-los para o Skype for Business online. Você pode mover seus usuários em seu próprio ritmo, sabendo que seus recursos de voz continuarão independentemente de onde estejam hospedados. 
  
Para obter mais informações, consulte [Plan Hybrid Connectivity between Skype for Business Server e Skype for Business online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Se você ainda não tiver uma implantação existente do Lync Server ou do Skype for Business Server, poderá usar o Skype for Business Cloud Connector Edition, um conjunto de VMs (máquinas virtuais) empacotadas que implementam a conectividade PSTN local com o Cloud PBX.
  
Para obter mais informações, consulte [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>Implantação Híbrida do SharePoint

O SharePoint híbrido combina o SharePoint Online no Office 365 com seu farm local do SharePoint para obter o melhor de ambas as duas opções, a experiência conectada.
  
**Figura 4: a configuração híbrida do SharePoint**

![A configuração híbrida do SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
A Figura 4 mostra a configuração híbrida do SharePoint, que consiste em um farm local do SharePoint que se comunica com o SharePoint Online no Office 365.
  
Cenários híbridos do SharePoint:
  
- [OneDrive for Business híbrido](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [B2B de extranet híbrida](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Pesquisa híbrida](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Perfis híbridos](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Seletor híbrido](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    É fácil habilitar cenários híbridos usando os assistentes que automatizam a configuração híbrida, disponível no centro de administração do SharePoint Online no Office 365.
    
- [Inicializador de aplicativos híbrido extensível](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Permite que os usuários exibam e usem o vídeo do Office 365 e os aplicativos e experiências do Delve nas páginas de seu farm local do SharePoint.
    
Todos esses cenários híbridos do SharePoint, exceto o inicializador de aplicativos híbridos extensíveis, estão disponíveis para os usuários do SharePoint 2016 e do SharePoint 2013.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 híbrido

Com o Exchange Server 2016 híbrido, você pode obter os benefícios do Exchange Online no Office 365 para usuários online enquanto os usuários locais continuam a usar a infraestrutura existente do Exchange Server. 
  
**Figura 5: a configuração híbrida do Exchange 2016**

![A configuração híbrida do Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
A Figura 5 mostra a configuração híbrida do Exchange 2016, que consiste em servidores locais de caixa de correio do Exchange que se comunicam com proteção e caixas de correio do Exchange Online no Office 365.
  
Alguns usuários têm um servidor de email local e alguns usuários usam o Exchange Online, mas todos os usuários compartilham o mesmo espaço de endereço de email. 
  
Esta configuração híbrida:
  
- Aproveita a infraestrutura existente do Exchange Server enquanto você migra para o Exchange Online ao longo do tempo, no seu cronograma.
    
- Permite que você dê suporte a sites remotos sem investir na infraestrutura de filial do escritório.
    
- Permite rotear emails de entrada da Internet por meio do Exchange Online Protection no Office 365.
    
- O atende às necessidades de organizações multinacionais com subsidiárias que exigem dados para residir no local.
    
Você também pode integrar essa configuração híbrida com outros aplicativos do Microsoft Office 365, incluindo o Skype for Business Online e o SharePoint Online.
  
Para obter mais informações, consulte imPlantações híbridas do [Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>Confira também


[Nuvem híbrida da Microsoft para arquitetos corporativos](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

