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
description: 'Resumo: Entenda os cenários e arquitetura de híbrido para Microsoft baseada em SaaS ofertas (Office 365) na nuvem.'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123408"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Cenários de nuvem híbrida para Microsoft SaaS (Office 365)

 **Resumo:** Entenda os cenários e arquitetura de híbrido para Microsoft baseada em SaaS ofertas (Office 365) na nuvem.
  
Combine as implantações de local do Exchange, SharePoint ou Skype for Business com seus correspondentes no Office 365, como parte de uma migração em nuvem ou uma estratégia de integração de longo prazo.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Arquitetura de cenário do Microsoft SaaS híbrida

A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em SaaS da Microsoft para o Office 365.
  
**Figura 1: Cenários de implantação híbrida baseada em SaaS Microsoft para o Office 365**

![Cenários híbridos da Microsoft baseados em SaaS para o Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
Para cada camada da arquitetura:
  
- Cenários e aplicativos
    
    Há uma variedade de cenários de implantação híbrida baseada em SaaS, alinhando ao redor dos produtos do Office Server e seus equivalentes do Office 365:
    
  - Exchange Server combinados com o Exchange Online (Exchange Server híbrido)
    
  - Skype para Business Server combinado com Skype para Business Online e os novos cenários de nuvem PBX e edição do conector de nuvem
    
  - SharePoint Server 2019, 2016 do SharePoint Server ou SharePoint Server 2013 combinado com o SharePoint Online (vários cenários)
    
    Há também Exchange Online com Skype para Business Server local, um cenário híbrido entre produtos.
    
- Identidade
    
    Pode incluir a sincronização de diretórios com seu local Windows Server AD. Como alternativa, você pode configurar o Azure AD para estabelecer uma federação com um provedor de identidade de terceiros.
    
- Rede
    
    Consiste em seu pipe Internet existente ou uma conexão ExpressRoute com a Microsoft correspondência para Office 365 ou Dynamics 365.
    
- Local
    
    Pode consistir em servidores existentes para o Exchange, SharePoint e Skype para os negócios, que devem ser atualizados para suas versões mais recentes. Você pode combiná-los com os representantes do Office 365 para cenários híbridos.
    
Configurar seu próprio ambiente de desenvolvimento e teste do Office 365, consulte [Guias de laboratório de teste do Office 365](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Skype para o híbrido de negócios

Skype para negócios híbrido permite combinar uma implantação local existente com Skype para negócios Online. Alguns usuários estão hospedados no local e alguns usuários hospedados online, mas os usuários compartilhem o mesmo domínio do protocolo de iniciação de sessão (SIP), por exemplo, contoso.com. Você pode usar essa configuração híbrida para migrar do local para o Office 365 ao longo do tempo, no seu calendário. Skype para negócios também pode ser integrado com o [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).
  
**Figura 2: O Skype para configuração híbrida de negócios**

![O Skype para configuração híbrida de negócios](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
A Figura 2 mostra o Skype para configuração híbrida de negócios, consistindo em um Skype local para o pool de front-end de negócios e borda servidor se comunicando com Skype para negócios Online no Office 365.
  
Para obter mais informações, consulte [Planejar a conectividade híbrida entre Skype para Business Server e do Skype para negócios Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Cloud PBX com Skype for Business Server

Nuvem PBX com Skype para Business Server lhe permite fazer a transição de um existente Skype para implantação do Business Server local para uma topologia com conectividade de rede de telefônica pública comutada (PSTN) local. 
  
**Figura 3: Nuvem PBX com Skype para Business Server**

![Cloud PBX com Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
A Figura 3 mostra o PBX nuvem com Skype para configuração do servidor de negócios, consistindo em um gateway PBX existente ou telecomunicações, um Skype para Business Server e o PSTN conectado ao PBX Microsoft Cloud no Office 365, que inclui Skype for Business no local Online.
  
Os usuários na organização hospedados na nuvem podem receber os serviços privada de comutação telefônica (PBX) de nuvem da Microsoft que incluem a sinalização e a caixa postal, mas conectividade PSTN (tom de discagem) é fornecida por meio do Enterprise Voice, a partir de seu local Skype para implantação de servidor de negócios.
  
Este é um ótimo exemplo de uma configuração híbrida que permite que você migrar gradualmente para um serviço baseado em nuvem. Você pode manter os recursos de voz dos usuários conforme você começa a movê-los para Skype para negócios Online. Você pode mover os usuários em seu próprio ritmo, sabendo que seus recursos de voz continuará não importa onde eles estão hospedados. 
  
Para obter mais informações, consulte [Planejar a conectividade híbrida entre Skype para Business Server e do Skype para negócios Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Se você ainda não tiver um servidor existente do Lync ou Skype para implantação de servidor de negócios, você pode usar o Skype para Business Edition de conector de nuvem, um conjunto de Industrializados máquinas virtuais (VMs) implementar a conectividade PSTN locais com PBX de nuvem.
  
Para obter mais informações, consulte [Planejar Skype para o conector de nuvem Business Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>Implantação Híbrida do SharePoint

SharePoint híbrido combina SharePoint Online no Office 365 com o seu farm do SharePoint no local para uma melhor dos dois mundos, experiência conectada.
  
**Figura 4: Configuração do SharePoint híbrido**

![A configuração híbrida do SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
Figura 4 mostra a configuração híbrida do SharePoint, consistindo em um farm do SharePoint local se comunicam com o SharePoint Online no Office 365.
  
Cenários de híbridos do SharePoint:
  
- [OneDrive for Business híbrido](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [Híbrido B2B de Extranet](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Pesquisa híbrida](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Perfis híbridos](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Seletor de híbrido](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    É fácil habilitar cenários híbridos usando os assistentes que automatizam configuração híbrida, disponível no Centro de administração do SharePoint Online no Office 365.
    
- [Inicializador de aplicativos híbrido extensível](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Permite que os usuários exibam e usem o vídeo do Office 365 e Delve aplicativos e experiências dentro de páginas do seu farm do SharePoint local.
    
Todos esses cenários de híbrido do SharePoint, exceto o iniciador de app híbrida extensível, estão disponíveis para os usuários do SharePoint 2016 e o SharePoint 2013.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 híbrido

Com o Exchange Server 2016 híbrido, você pode aproveitar as vantagens do Exchange Online no Office 365 para usuários online enquanto usuários locais continuam a usar a infra-estrutura existente do Exchange Server. 
  
**Figura 5: Configuração 2016 Exchange híbrida**

![A configuração híbrida do Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
Figura 5 mostra a configuração híbrida do Exchange 2016, consistindo em servidores de caixa de correio do Exchange local se comunicam com Exchange Online Protection e caixas de correio no Office 365.
  
Alguns usuários têm um servidor de email local e alguns usuários usarem o Exchange Online, mas todos os usuários compartilham o mesmo espaço de endereço de email. 
  
Essa configuração híbrida:
  
- Aproveita a infra-estrutura existente do Exchange Server enquanto você migrar para o Exchange Online ao longo do tempo, no seu calendário.
    
- Permite que você ofereça suporte a sites remotos sem investir em infraestrutura de escritório de filial.
    
- Permite que você rotear emails de entrada da Internet no Exchange Online Protection no Office 365.
    
- Atende às necessidades de organizações multinacionais com subsidiárias que exigem dados devem residir no local.
    
Você também pode integrar esta configuração híbrida com outros aplicativos do Microsoft Office 365, incluindo Skype para negócios Online e SharePoint Online.
  
Para obter mais informações, consulte [Implantações híbridas do Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>Confira também

[Nuvem híbrida da Microsoft para Arquitetos Corporativos](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

