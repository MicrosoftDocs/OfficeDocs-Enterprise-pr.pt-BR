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
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="ea5c5-103">Cenários de nuvem híbrida para Microsoft SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="ea5c5-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="ea5c5-104">**Resumo:** Entenda os cenários e arquitetura de híbrido para Microsoft baseada em SaaS ofertas (Office 365) na nuvem.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="ea5c5-105">Combine as implantações de local do Exchange, SharePoint ou Skype for Business com seus correspondentes no Office 365, como parte de uma migração em nuvem ou uma estratégia de integração de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="ea5c5-106">Arquitetura de cenário do Microsoft SaaS híbrida</span><span class="sxs-lookup"><span data-stu-id="ea5c5-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="ea5c5-107">A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em SaaS da Microsoft para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="ea5c5-108">**Figura 1: Cenários de implantação híbrida baseada em SaaS Microsoft para o Office 365**</span><span class="sxs-lookup"><span data-stu-id="ea5c5-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Cenários híbridos da Microsoft baseados em SaaS para o Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="ea5c5-110">Para cada camada da arquitetura:</span><span class="sxs-lookup"><span data-stu-id="ea5c5-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="ea5c5-111">Cenários e aplicativos</span><span class="sxs-lookup"><span data-stu-id="ea5c5-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="ea5c5-112">Há uma variedade de cenários de implantação híbrida baseada em SaaS, alinhando ao redor dos produtos do Office Server e seus equivalentes do Office 365:</span><span class="sxs-lookup"><span data-stu-id="ea5c5-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="ea5c5-113">Exchange Server combinados com o Exchange Online (Exchange Server híbrido)</span><span class="sxs-lookup"><span data-stu-id="ea5c5-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="ea5c5-114">Skype para Business Server combinado com Skype para Business Online e os novos cenários de nuvem PBX e edição do conector de nuvem</span><span class="sxs-lookup"><span data-stu-id="ea5c5-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="ea5c5-115">SharePoint Server 2019, 2016 do SharePoint Server ou SharePoint Server 2013 combinado com o SharePoint Online (vários cenários)</span><span class="sxs-lookup"><span data-stu-id="ea5c5-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="ea5c5-116">Há também Exchange Online com Skype para Business Server local, um cenário híbrido entre produtos.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="ea5c5-117">Identidade</span><span class="sxs-lookup"><span data-stu-id="ea5c5-117">Identity</span></span>
    
    <span data-ttu-id="ea5c5-p101">Pode incluir a sincronização de diretórios com seu local Windows Server AD. Como alternativa, você pode configurar o Azure AD para estabelecer uma federação com um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="ea5c5-120">Rede</span><span class="sxs-lookup"><span data-stu-id="ea5c5-120">Network</span></span>
    
    <span data-ttu-id="ea5c5-121">Consiste em seu pipe Internet existente ou uma conexão ExpressRoute com a Microsoft correspondência para Office 365 ou Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="ea5c5-122">Local</span><span class="sxs-lookup"><span data-stu-id="ea5c5-122">On-premises</span></span>
    
    <span data-ttu-id="ea5c5-p102">Pode consistir em servidores existentes para o Exchange, SharePoint e Skype para os negócios, que devem ser atualizados para suas versões mais recentes. Você pode combiná-los com os representantes do Office 365 para cenários híbridos.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="ea5c5-125">Configurar seu próprio ambiente de desenvolvimento e teste do Office 365, consulte [Guias de laboratório de teste do Office 365](cloud-adoption-test-lab-guides-tlgs.md).</span><span class="sxs-lookup"><span data-stu-id="ea5c5-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="ea5c5-126">Skype para o híbrido de negócios</span><span class="sxs-lookup"><span data-stu-id="ea5c5-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="ea5c5-p103">Skype para negócios híbrido permite combinar uma implantação local existente com Skype para negócios Online. Alguns usuários estão hospedados no local e alguns usuários hospedados online, mas os usuários compartilhem o mesmo domínio do protocolo de iniciação de sessão (SIP), por exemplo, contoso.com. Você pode usar essa configuração híbrida para migrar do local para o Office 365 ao longo do tempo, no seu calendário. Skype para negócios também pode ser integrado com o [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span><span class="sxs-lookup"><span data-stu-id="ea5c5-p103">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="ea5c5-131">**Figura 2: O Skype para configuração híbrida de negócios**</span><span class="sxs-lookup"><span data-stu-id="ea5c5-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![O Skype para configuração híbrida de negócios](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="ea5c5-133">A Figura 2 mostra o Skype para configuração híbrida de negócios, consistindo em um Skype local para o pool de front-end de negócios e borda servidor se comunicando com Skype para negócios Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="ea5c5-134">Para obter mais informações, consulte [Planejar a conectividade híbrida entre Skype para Business Server e do Skype para negócios Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="ea5c5-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="ea5c5-135">Cloud PBX com Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="ea5c5-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="ea5c5-136">Nuvem PBX com Skype para Business Server lhe permite fazer a transição de um existente Skype para implantação do Business Server local para uma topologia com conectividade de rede de telefônica pública comutada (PSTN) local.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="ea5c5-137">**Figura 3: Nuvem PBX com Skype para Business Server**</span><span class="sxs-lookup"><span data-stu-id="ea5c5-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Cloud PBX com Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="ea5c5-139">A Figura 3 mostra o PBX nuvem com Skype para configuração do servidor de negócios, consistindo em um gateway PBX existente ou telecomunicações, um Skype para Business Server e o PSTN conectado ao PBX Microsoft Cloud no Office 365, que inclui Skype for Business no local Online.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="ea5c5-140">Os usuários na organização hospedados na nuvem podem receber os serviços privada de comutação telefônica (PBX) de nuvem da Microsoft que incluem a sinalização e a caixa postal, mas conectividade PSTN (tom de discagem) é fornecida por meio do Enterprise Voice, a partir de seu local Skype para implantação de servidor de negócios.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="ea5c5-p104">Este é um ótimo exemplo de uma configuração híbrida que permite que você migrar gradualmente para um serviço baseado em nuvem. Você pode manter os recursos de voz dos usuários conforme você começa a movê-los para Skype para negócios Online. Você pode mover os usuários em seu próprio ritmo, sabendo que seus recursos de voz continuará não importa onde eles estão hospedados.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-p104">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="ea5c5-144">Para obter mais informações, consulte [Planejar a conectividade híbrida entre Skype para Business Server e do Skype para negócios Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="ea5c5-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="ea5c5-145">Se você ainda não tiver um servidor existente do Lync ou Skype para implantação de servidor de negócios, você pode usar o Skype para Business Edition de conector de nuvem, um conjunto de Industrializados máquinas virtuais (VMs) implementar a conectividade PSTN locais com PBX de nuvem.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="ea5c5-146">Para obter mais informações, consulte [Planejar Skype para o conector de nuvem Business Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span><span class="sxs-lookup"><span data-stu-id="ea5c5-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="ea5c5-147">Implantação Híbrida do SharePoint</span><span class="sxs-lookup"><span data-stu-id="ea5c5-147">SharePoint Hybrid</span></span>

<span data-ttu-id="ea5c5-148">SharePoint híbrido combina SharePoint Online no Office 365 com o seu farm do SharePoint no local para uma melhor dos dois mundos, experiência conectada.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="ea5c5-149">**Figura 4: Configuração do SharePoint híbrido**</span><span class="sxs-lookup"><span data-stu-id="ea5c5-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![A configuração híbrida do SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="ea5c5-151">Figura 4 mostra a configuração híbrida do SharePoint, consistindo em um farm do SharePoint local se comunicam com o SharePoint Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="ea5c5-152">Cenários de híbridos do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="ea5c5-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="ea5c5-153">OneDrive for Business híbrido</span><span class="sxs-lookup"><span data-stu-id="ea5c5-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="ea5c5-154">Híbrido B2B de Extranet</span><span class="sxs-lookup"><span data-stu-id="ea5c5-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="ea5c5-155">Pesquisa híbrida</span><span class="sxs-lookup"><span data-stu-id="ea5c5-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="ea5c5-156">Perfis híbridos</span><span class="sxs-lookup"><span data-stu-id="ea5c5-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="ea5c5-157">Seletor de híbrido</span><span class="sxs-lookup"><span data-stu-id="ea5c5-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="ea5c5-158">É fácil habilitar cenários híbridos usando os assistentes que automatizam configuração híbrida, disponível no Centro de administração do SharePoint Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="ea5c5-159">Inicializador de aplicativos híbrido extensível</span><span class="sxs-lookup"><span data-stu-id="ea5c5-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="ea5c5-160">Permite que os usuários exibam e usem o vídeo do Office 365 e Delve aplicativos e experiências dentro de páginas do seu farm do SharePoint local.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="ea5c5-161">Todos esses cenários de híbrido do SharePoint, exceto o iniciador de app híbrida extensível, estão disponíveis para os usuários do SharePoint 2016 e o SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="ea5c5-162">Exchange Server 2016 híbrido</span><span class="sxs-lookup"><span data-stu-id="ea5c5-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="ea5c5-163">Com o Exchange Server 2016 híbrido, você pode aproveitar as vantagens do Exchange Online no Office 365 para usuários online enquanto usuários locais continuam a usar a infra-estrutura existente do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="ea5c5-164">**Figura 5: Configuração 2016 Exchange híbrida**</span><span class="sxs-lookup"><span data-stu-id="ea5c5-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![A configuração híbrida do Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="ea5c5-166">Figura 5 mostra a configuração híbrida do Exchange 2016, consistindo em servidores de caixa de correio do Exchange local se comunicam com Exchange Online Protection e caixas de correio no Office 365.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="ea5c5-167">Alguns usuários têm um servidor de email local e alguns usuários usarem o Exchange Online, mas todos os usuários compartilham o mesmo espaço de endereço de email.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="ea5c5-168">Essa configuração híbrida:</span><span class="sxs-lookup"><span data-stu-id="ea5c5-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="ea5c5-169">Aproveita a infra-estrutura existente do Exchange Server enquanto você migrar para o Exchange Online ao longo do tempo, no seu calendário.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="ea5c5-170">Permite que você ofereça suporte a sites remotos sem investir em infraestrutura de escritório de filial.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="ea5c5-171">Permite que você rotear emails de entrada da Internet no Exchange Online Protection no Office 365.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="ea5c5-172">Atende às necessidades de organizações multinacionais com subsidiárias que exigem dados devem residir no local.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="ea5c5-173">Você também pode integrar esta configuração híbrida com outros aplicativos do Microsoft Office 365, incluindo Skype para negócios Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ea5c5-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="ea5c5-174">Para obter mais informações, consulte [Implantações híbridas do Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).</span><span class="sxs-lookup"><span data-stu-id="ea5c5-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ea5c5-175">Confira também</span><span class="sxs-lookup"><span data-stu-id="ea5c5-175">See Also</span></span>

[<span data-ttu-id="ea5c5-176">Nuvem híbrida da Microsoft para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="ea5c5-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="ea5c5-177">Recursos de arquitetura de TI do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="ea5c5-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

