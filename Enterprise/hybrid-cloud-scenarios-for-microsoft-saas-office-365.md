---
title: "Cenários de nuvem híbrida para a Microsoft SaaS (Office 365)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Resumo: Entenda os cenários e arquitetura de híbrido para Microsoft baseada em SaaS ofertas (Office 365) na nuvem."
ms.openlocfilehash: 63126d694817f8323494e584f1f497a1a732c678
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Cenários de nuvem híbrida para a Microsoft SaaS (Office 365)

 **Resumo:** Entenda os cenários e arquitetura de híbrido para Microsoft baseada em SaaS ofertas (Office 365) na nuvem.
  
Combine as implantações de local do Exchange, SharePoint ou Skype for Business com seus correspondentes no Office 365, como parte de uma migração em nuvem ou uma estratégia de integração de longo prazo.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Arquitetura de cenário do Microsoft SaaS híbrida

A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em SaaS da Microsoft para o Office 365.
  
**Figura 1: Cenários de implantação híbrida baseada em SaaS Microsoft para o Office 365**

![Cenários híbridos da Microsoft baseados em SaaS para o Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
Para cada camada da arquitetura:
  
- Cenários e aplicativos
    
    Há uma variedade de cenários de implantação híbrida baseada em SaaS, alinhando ao redor dos produtos do Office Server e seus equivalentes do Office 365:
    
  - Exchange Server combinados com o Exchange Online (Exchange Server híbrido)
    
  - Skype para Business Server combinado com Skype para Business Online e os novos cenários de nuvem PBX e edição do conector de nuvem
    
  - SharePoint Server 2016 ou SharePoint Server 2013 combinada com o SharePoint Online (vários cenários)
    
    Há também Exchange Online com Skype para Business Server local, um cenário híbrido entre produtos.
    
- Identidade
    
    Pode incluir a sincronização de diretórios com seu local Windows Server AD. Como alternativa, você pode configurar o Azure AD para estabelecer uma federação com um provedor de identidade de terceiros.
    
- Rede
    
    Consiste em seu pipe Internet existente ou uma conexão ExpressRoute com a Microsoft correspondência para Office 365 ou Dynamics 365.
    
- Local
    
    Pode consistir em servidores existentes para o Exchange, SharePoint e Skype para os negócios, que devem ser atualizados para suas versões mais recentes. Você pode combiná-los com os representantes do Office 365 para cenários híbridos.
    
Configure seu próprio [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
## <a name="skype-for-business-2015-hybrid"></a>Skype para negócios 2015 híbrido

Skype para negócios 2015 híbrido permite combinar uma implantação local existente com Skype para negócios Online. Alguns usuários estão hospedados no local e alguns usuários hospedados online, mas os usuários compartilhem o mesmo domínio do protocolo de iniciação de sessão (SIP), por exemplo, contoso.com. Você pode usar essa configuração híbrida para migrar do local para o Office 365 ao longo do tempo, no seu calendário. Skype para negócios 2015 também pode ser integrado com o Exchange Online.
  
**Figura 2: O Skype para configuração híbrida de negócios 2015**

![A configuração híbrida do Skype for Business 2015](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
A Figura 2 mostra o Skype para configuração híbrida de negócios 2015, consistindo em um Skype local para o pool de front-end de negócios 2015 e borda servidor se comunicando com Skype para negócios Online no Office 365.
  
Para obter mais informações, consulte:
  
- [Planejar a conectividade híbrida entre Skype para Business Server e do Skype para negócios Online](https://technet.microsoft.com/library/jj205403.aspx)
    
- [Configurações de híbridas com suporte para o Skype para Business Server 2015](https://technet.microsoft.com/library/jj945633.aspx)
    
- [Skype para o híbrido de negócios](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Cloud PBX com Skype for Business Server

Nuvem PBX com Skype para Business Server permite fazer a transição de um existente Skype para implantação do Business Server local para uma topologia com conectividade de rede de telefônica pública comutada (PSTN) local. 
  
**Figura 3: Nuvem PBX com Skype para Business Server**

![Cloud PBX com Skype for Business Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
A Figura 3 mostra o PBX nuvem com Skype para configuração do servidor de negócios, consistindo em um gateway PBX existente ou telecomunicações, um Skype para Business Server e o PSTN conectado ao PBX Microsoft Cloud no Office 365, que inclui Skype for Business no local Online.
  
Os usuários na organização hospedados na nuvem podem receber os serviços privada de comutação telefônica (PBX) de nuvem da Microsoft que incluem a sinalização e a caixa postal, mas conectividade PSTN (tom de discagem) é fornecida por meio do Enterprise Voice, a partir de seu local Skype para implantação de servidor de negócios.
  
Este é um ótimo exemplo de uma configuração híbrida que permite que você migrar gradualmente para um serviço baseado em nuvem. Você pode manter os recursos de voz dos usuários conforme você começa a movê-los para Skype para negócios Online. Você pode mover os usuários em seu próprio ritmo, sabendo que seus recursos de voz continuará não importa onde eles estão hospedados. 
  
Para obter mais informações, consulte [Planejar a conectividade híbrida entre Skype para Business Server e do Skype para Business Online ou Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).
  
Se você ainda não tiver um servidor existente do Lync ou Skype para implantação de servidor de negócios, você pode usar o Skype para Business Edition de conector de nuvem, um conjunto de Industrializados máquinas virtuais (VMs) implementar a conectividade PSTN locais com PBX de nuvem.
  
Para obter mais informações, consulte [Planejar Skype para o conector de nuvem Business Edition](https://technet.microsoft.com/library/mt605227.aspx).
  
## <a name="sharepoint-hybrid"></a>Implantação Híbrida do SharePoint

SharePoint híbrido combina SharePoint Online no Office 365 com o seu farm do SharePoint no local para uma melhor dos dois mundos, experiência conectada.
  
**Figura 4: Configuração do SharePoint híbrido**

![A configuração híbrida do SharePoint](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
Figura 4 mostra a configuração híbrida do SharePoint, consistindo em um farm do SharePoint local se comunicam com o SharePoint Online no Office 365.
  
Cenários de híbridos do SharePoint:
  
- [Híbrido OneDrive for Business](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [Sites de equipe híbrida](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [Híbrido B2B de Extranet](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [Pesquisa híbrida](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [Perfis de híbrido](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [Seletor de híbrido](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    É fácil habilitar cenários híbridos usando os assistentes que automatizam configuração híbrida, disponível no Centro de administração do SharePoint Online no Office 365.
    
- [Iniciador de app híbrida extensível](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    Permite que os usuários exibam e usem o vídeo do Office 365 e Delve aplicativos e experiências dentro de páginas do seu farm do SharePoint local.
    
Todos esses cenários de híbrido do SharePoint, exceto o iniciador de app híbrida extensível, estão disponíveis para os usuários do SharePoint 2016 e o SharePoint 2013.
  
Para obter mais informações, consulte [SharePoint híbrido](http://hybrid.office.com/sharepoint/).
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 híbrido

Com o Exchange Server 2016 híbrido, você pode aproveitar as vantagens do Exchange Online no Office 365 para usuários online enquanto usuários locais continuam a usar a infra-estrutura existente do Exchange Server. 
  
**Figura 5: Configuração 2016 Exchange híbrida**

![A configuração híbrida do Exchange 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
Figura 5 mostra a configuração híbrida do Exchange 2016, consistindo em servidores de caixa de correio do Exchange local se comunicam com Exchange Online Protection e caixas de correio no Office 365.
  
Alguns usuários têm um servidor de email local e alguns usuários usarem o Exchange Online, mas todos os usuários compartilham o mesmo espaço de endereço de email. 
  
Essa configuração híbrida:
  
- Aproveita a infra-estrutura existente do Exchange Server enquanto você migrar para o Exchange Online ao longo do tempo, no seu calendário.
    
- Permite que você ofereça suporte a sites remotos sem investir em infraestrutura de escritório de filial.
    
- Permite que você rotear emails de entrada da Internet no Exchange Online Protection no Office 365.
    
- Atende às necessidades de organizações multinacionais com subsidiárias que exigem dados devem residir no local.
    
Você também pode integrar esta configuração híbrida com outros aplicativos do Microsoft Office 365, incluindo Skype para negócios Online e SharePoint Online.
  
Para obter mais informações, consulte [Implantações híbridas do Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) e o [Exchange híbrido](http://hybrid.office.com/exchange/).
  
## <a name="see-also"></a>Veja também

[Nuvem híbrida da Microsoft para arquitetos corporativos](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



