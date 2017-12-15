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
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Resumo: Entenda os cenários e arquitetura de híbrido para Microsoft baseada em SaaS ofertas (Office 365) na nuvem."
ms.openlocfilehash: 5f50573376b70ad94b3b1cd4b86ce3ef1fdc67dd
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="43ad2-103">Cenários de nuvem híbrida para a Microsoft SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="43ad2-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="43ad2-104">**Resumo:** Entenda os cenários e arquitetura de híbrido para Microsoft baseada em SaaS ofertas (Office 365) na nuvem.</span><span class="sxs-lookup"><span data-stu-id="43ad2-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="43ad2-105">Combine as implantações de local do Exchange, SharePoint ou Skype for Business com seus correspondentes no Office 365, como parte de uma migração em nuvem ou uma estratégia de integração de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="43ad2-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="43ad2-106">Arquitetura de cenário do Microsoft SaaS híbrida</span><span class="sxs-lookup"><span data-stu-id="43ad2-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="43ad2-107">A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em SaaS da Microsoft para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="43ad2-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="43ad2-108">**Figura 1: Cenários de implantação híbrida baseada em SaaS Microsoft para o Office 365**</span><span class="sxs-lookup"><span data-stu-id="43ad2-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Cenários híbridos da Microsoft baseados em SaaS para o Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="43ad2-110">Para cada camada da arquitetura:</span><span class="sxs-lookup"><span data-stu-id="43ad2-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="43ad2-111">Cenários e aplicativos</span><span class="sxs-lookup"><span data-stu-id="43ad2-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="43ad2-112">Há uma variedade de cenários de implantação híbrida baseada em SaaS, alinhando ao redor dos produtos do Office Server e seus equivalentes do Office 365:</span><span class="sxs-lookup"><span data-stu-id="43ad2-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="43ad2-113">Exchange Server combinados com o Exchange Online (Exchange Server híbrido)</span><span class="sxs-lookup"><span data-stu-id="43ad2-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="43ad2-114">Skype para Business Server combinado com Skype para Business Online e os novos cenários de nuvem PBX e edição do conector de nuvem</span><span class="sxs-lookup"><span data-stu-id="43ad2-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="43ad2-115">SharePoint Server 2016 ou SharePoint Server 2013 combinada com o SharePoint Online (vários cenários)</span><span class="sxs-lookup"><span data-stu-id="43ad2-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="43ad2-116">Há também Exchange Online com Skype para Business Server local, um cenário híbrido entre produtos.</span><span class="sxs-lookup"><span data-stu-id="43ad2-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="43ad2-117">Identidade</span><span class="sxs-lookup"><span data-stu-id="43ad2-117">Identity</span></span>
    
    <span data-ttu-id="43ad2-p101">Pode incluir a sincronização de diretórios com seu local Windows Server AD. Como alternativa, você pode configurar o Azure AD para estabelecer uma federação com um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="43ad2-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="43ad2-120">Rede</span><span class="sxs-lookup"><span data-stu-id="43ad2-120">Network</span></span>
    
    <span data-ttu-id="43ad2-121">Consiste em seu pipe Internet existente ou uma conexão ExpressRoute com a Microsoft correspondência para Office 365 ou Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="43ad2-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="43ad2-122">Local</span><span class="sxs-lookup"><span data-stu-id="43ad2-122">On-premises</span></span>
    
    <span data-ttu-id="43ad2-p102">Pode consistir em servidores existentes para o Exchange, SharePoint e Skype para os negócios, que devem ser atualizados para suas versões mais recentes. Você pode combiná-los com os representantes do Office 365 para cenários híbridos.</span><span class="sxs-lookup"><span data-stu-id="43ad2-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="43ad2-125">Configure seu próprio [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="43ad2-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="43ad2-126">Skype para negócios 2015 híbrido</span><span class="sxs-lookup"><span data-stu-id="43ad2-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="43ad2-p103">Skype para negócios 2015 híbrido permite combinar uma implantação local existente com Skype para negócios Online. Alguns usuários estão hospedados no local e alguns usuários hospedados online, mas os usuários compartilhem o mesmo domínio do protocolo de iniciação de sessão (SIP), por exemplo, contoso.com. Você pode usar essa configuração híbrida para migrar do local para o Office 365 ao longo do tempo, no seu calendário. Skype para negócios 2015 também pode ser integrado com o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="43ad2-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="43ad2-130">**Figura 2: O Skype para configuração híbrida de negócios 2015**</span><span class="sxs-lookup"><span data-stu-id="43ad2-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![A configuração híbrida do Skype for Business 2015](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="43ad2-132">A Figura 2 mostra o Skype para configuração híbrida de negócios 2015, consistindo em um Skype local para o pool de front-end de negócios 2015 e borda servidor se comunicando com Skype para negócios Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="43ad2-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="43ad2-133">Saiba mais em:</span><span class="sxs-lookup"><span data-stu-id="43ad2-133">For more information, see:</span></span>
  
- [<span data-ttu-id="43ad2-134">Planejar a conectividade híbrida entre Skype para Business Server e do Skype para negócios Online</span><span class="sxs-lookup"><span data-stu-id="43ad2-134">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="43ad2-135">Configurações de híbridas com suporte para o Skype para Business Server 2015</span><span class="sxs-lookup"><span data-stu-id="43ad2-135">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="43ad2-136">Skype para o híbrido de negócios</span><span class="sxs-lookup"><span data-stu-id="43ad2-136">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="43ad2-137">Cloud PBX com Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="43ad2-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="43ad2-138">Nuvem PBX com Skype para Business Server permite fazer a transição de um existente Skype para implantação do Business Server local para uma topologia com conectividade de rede de telefônica pública comutada (PSTN) local.</span><span class="sxs-lookup"><span data-stu-id="43ad2-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="43ad2-139">**Figura 3: Nuvem PBX com Skype para Business Server**</span><span class="sxs-lookup"><span data-stu-id="43ad2-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Cloud PBX com Skype for Business Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="43ad2-141">A Figura 3 mostra o PBX nuvem com Skype para configuração do servidor de negócios, consistindo em um gateway PBX existente ou telecomunicações, um Skype para Business Server e o PSTN conectado ao PBX Microsoft Cloud no Office 365, que inclui Skype for Business no local Online.</span><span class="sxs-lookup"><span data-stu-id="43ad2-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="43ad2-142">Os usuários na organização hospedados na nuvem podem receber os serviços privada de comutação telefônica (PBX) de nuvem da Microsoft que incluem a sinalização e a caixa postal, mas conectividade PSTN (tom de discagem) é fornecida por meio do Enterprise Voice, a partir de seu local Skype para implantação de servidor de negócios.</span><span class="sxs-lookup"><span data-stu-id="43ad2-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="43ad2-p104">Este é um ótimo exemplo de uma configuração híbrida que permite que você migrar gradualmente para um serviço baseado em nuvem. Você pode manter os recursos de voz dos usuários conforme você começa a movê-los para Skype para negócios Online. Você pode mover os usuários em seu próprio ritmo, sabendo que seus recursos de voz continuará não importa onde eles estão hospedados.</span><span class="sxs-lookup"><span data-stu-id="43ad2-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="43ad2-146">Para obter mais informações, consulte [Planejar a conectividade híbrida entre Skype para Business Server e do Skype para Business Online ou Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span><span class="sxs-lookup"><span data-stu-id="43ad2-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="43ad2-147">Se você ainda não tiver um servidor existente do Lync ou Skype para implantação de servidor de negócios, você pode usar o Skype para Business Edition de conector de nuvem, um conjunto de Industrializados máquinas virtuais (VMs) implementar a conectividade PSTN locais com PBX de nuvem.</span><span class="sxs-lookup"><span data-stu-id="43ad2-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="43ad2-148">Para obter mais informações, consulte [Planejar Skype para o conector de nuvem Business Edition](https://technet.microsoft.com/library/mt605227.aspx).</span><span class="sxs-lookup"><span data-stu-id="43ad2-148">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="43ad2-149">Implantação Híbrida do SharePoint</span><span class="sxs-lookup"><span data-stu-id="43ad2-149">SharePoint Hybrid</span></span>

<span data-ttu-id="43ad2-150">SharePoint híbrido combina SharePoint Online no Office 365 com o seu farm do SharePoint no local para uma melhor dos dois mundos, experiência conectada.</span><span class="sxs-lookup"><span data-stu-id="43ad2-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="43ad2-151">**Figura 4: Configuração do SharePoint híbrido**</span><span class="sxs-lookup"><span data-stu-id="43ad2-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![A configuração híbrida do SharePoint](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="43ad2-153">Figura 4 mostra a configuração híbrida do SharePoint, consistindo em um farm do SharePoint local se comunicam com o SharePoint Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="43ad2-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="43ad2-154">Cenários de híbridos do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="43ad2-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="43ad2-155">Híbrido OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="43ad2-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="43ad2-156">Sites de equipe híbrida</span><span class="sxs-lookup"><span data-stu-id="43ad2-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="43ad2-157">Híbrido B2B de Extranet</span><span class="sxs-lookup"><span data-stu-id="43ad2-157">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="43ad2-158">Pesquisa híbrida</span><span class="sxs-lookup"><span data-stu-id="43ad2-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="43ad2-159">Perfis de híbrido</span><span class="sxs-lookup"><span data-stu-id="43ad2-159">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="43ad2-160">Seletor de híbrido</span><span class="sxs-lookup"><span data-stu-id="43ad2-160">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="43ad2-161">É fácil habilitar cenários híbridos usando os assistentes que automatizam configuração híbrida, disponível no Centro de administração do SharePoint Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="43ad2-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="43ad2-162">Iniciador de app híbrida extensível</span><span class="sxs-lookup"><span data-stu-id="43ad2-162">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="43ad2-163">Permite que os usuários exibam e usem o vídeo do Office 365 e Delve aplicativos e experiências dentro de páginas do seu farm do SharePoint local.</span><span class="sxs-lookup"><span data-stu-id="43ad2-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="43ad2-164">Todos esses cenários de híbrido do SharePoint, exceto o iniciador de app híbrida extensível, estão disponíveis para os usuários do SharePoint 2016 e o SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="43ad2-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="43ad2-165">Para obter mais informações, consulte [SharePoint híbrido](http://hybrid.office.com/sharepoint/).</span><span class="sxs-lookup"><span data-stu-id="43ad2-165">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="43ad2-166">Exchange Server 2016 híbrido</span><span class="sxs-lookup"><span data-stu-id="43ad2-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="43ad2-167">Com o Exchange Server 2016 híbrido, você pode aproveitar as vantagens do Exchange Online no Office 365 para usuários online enquanto usuários locais continuam a usar a infra-estrutura existente do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="43ad2-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="43ad2-168">**Figura 5: Configuração 2016 Exchange híbrida**</span><span class="sxs-lookup"><span data-stu-id="43ad2-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![A configuração híbrida do Exchange 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="43ad2-170">Figura 5 mostra a configuração híbrida do Exchange 2016, consistindo em servidores de caixa de correio do Exchange local se comunicam com Exchange Online Protection e caixas de correio no Office 365.</span><span class="sxs-lookup"><span data-stu-id="43ad2-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="43ad2-171">Alguns usuários têm um servidor de email local e alguns usuários usarem o Exchange Online, mas todos os usuários compartilham o mesmo espaço de endereço de email.</span><span class="sxs-lookup"><span data-stu-id="43ad2-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="43ad2-172">Essa configuração híbrida:</span><span class="sxs-lookup"><span data-stu-id="43ad2-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="43ad2-173">Aproveita a infra-estrutura existente do Exchange Server enquanto você migrar para o Exchange Online ao longo do tempo, no seu calendário.</span><span class="sxs-lookup"><span data-stu-id="43ad2-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="43ad2-174">Permite que você ofereça suporte a sites remotos sem investir em infraestrutura de escritório de filial.</span><span class="sxs-lookup"><span data-stu-id="43ad2-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="43ad2-175">Permite que você rotear emails de entrada da Internet no Exchange Online Protection no Office 365.</span><span class="sxs-lookup"><span data-stu-id="43ad2-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="43ad2-176">Atende às necessidades de organizações multinacionais com subsidiárias que exigem dados devem residir no local.</span><span class="sxs-lookup"><span data-stu-id="43ad2-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="43ad2-177">Você também pode integrar esta configuração híbrida com outros aplicativos do Microsoft Office 365, incluindo Skype para negócios Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="43ad2-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="43ad2-178">Para obter mais informações, consulte [Implantações híbridas do Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) e o [Exchange híbrido](http://hybrid.office.com/exchange/).</span><span class="sxs-lookup"><span data-stu-id="43ad2-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="43ad2-179">See Also</span><span class="sxs-lookup"><span data-stu-id="43ad2-179">See Also</span></span>

[<span data-ttu-id="43ad2-180">Nuvem híbrida da Microsoft para arquitetos da empresa</span><span class="sxs-lookup"><span data-stu-id="43ad2-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="43ad2-181">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="43ad2-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="43ad2-182">Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="43ad2-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



