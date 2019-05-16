---
title: Cenários de nuvem híbrida para Microsoft SaaS (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Resumo: entenda a arquitetura híbrida e os cenários de ofertas de nuvem baseadas em SaaS da Microsoft (Office 365).'
ms.openlocfilehash: 84092fe419ab31fca7763f434e328eb855d46835
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067217"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="8c6ca-103">Cenários de nuvem híbrida para Microsoft SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8c6ca-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="8c6ca-104">**Resumo:** Compreenda a arquitetura híbrida e os cenários de ofertas de nuvem baseadas em SaaS da Microsoft (Office 365).</span><span class="sxs-lookup"><span data-stu-id="8c6ca-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="8c6ca-105">Combine implantações locais do Exchange, SharePoint ou Skype for Business com seus correspondentes no Office 365 como parte de uma migração em nuvem ou uma estratégia de integração de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="8c6ca-106">Arquitetura de cenário híbrido Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="8c6ca-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="8c6ca-107">A Figura 1 mostra a arquitetura dos cenários híbridos baseados em SaaS da Microsoft para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="8c6ca-108">**Figura 1: cenários híbridos baseados em SaaS da Microsoft para o Office 365**</span><span class="sxs-lookup"><span data-stu-id="8c6ca-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Cenários híbridos baseados em SaaS da Microsoft para o Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="8c6ca-110">Para cada camada da arquitetura:</span><span class="sxs-lookup"><span data-stu-id="8c6ca-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="8c6ca-111">Aplicativos e cenários</span><span class="sxs-lookup"><span data-stu-id="8c6ca-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="8c6ca-112">Há uma variedade de cenários híbridos baseados em SaaS, que se alinha ao redor dos produtos do Office Server e seus correspondentes no Office 365:</span><span class="sxs-lookup"><span data-stu-id="8c6ca-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="8c6ca-113">Exchange Server combinado com o Exchange Online (Exchange Server híbrido)</span><span class="sxs-lookup"><span data-stu-id="8c6ca-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="8c6ca-114">Skype for Business Server combinado com o Skype for Business Online e os novos cenários de Cloud PBX e Cloud Connector Edition</span><span class="sxs-lookup"><span data-stu-id="8c6ca-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="8c6ca-115">SharePoint Server 2019, SharePoint Server 2016 ou SharePoint Server 2013 combinado com o SharePoint Online (vários cenários)</span><span class="sxs-lookup"><span data-stu-id="8c6ca-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="8c6ca-116">Há também o Exchange Online com o Skype for Business Server no local, um cenário híbrido entre produtos.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="8c6ca-117">Identidade</span><span class="sxs-lookup"><span data-stu-id="8c6ca-117">Identity</span></span>
    
    <span data-ttu-id="8c6ca-118">Pode incluir a sincronização de diretórios com os serviços de domínio do Active Directory (AD DS) local.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-118">Can include directory synchronization with your on-premises Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="8c6ca-119">Como alternativa, é possível configurar o Azure AD para federação com um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-119">Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="8c6ca-120">Rede</span><span class="sxs-lookup"><span data-stu-id="8c6ca-120">Network</span></span>
    
    <span data-ttu-id="8c6ca-121">O consiste no seu pipe existente na Internet ou em uma conexão ExpressRoute com o emparelhamento da Microsoft para o Office 365 ou Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="8c6ca-122">No local</span><span class="sxs-lookup"><span data-stu-id="8c6ca-122">On-premises</span></span>
    
    <span data-ttu-id="8c6ca-123">Pode consistir em servidores existentes para o Exchange, o SharePoint e o Skype for Business, que devem ser atualizados para suas versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-123">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions.</span></span> <span data-ttu-id="8c6ca-124">Em seguida, você pode combiná-los com seus correspondentes do Office 365 para cenários híbridos.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-124">You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="8c6ca-125">Configure seu próprio ambiente de desenvolvimento/teste do Office 365, confira [guias de laboratório de teste do office 365](cloud-adoption-test-lab-guides-tlgs.md).</span><span class="sxs-lookup"><span data-stu-id="8c6ca-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="8c6ca-126">Skype for Business híbrido</span><span class="sxs-lookup"><span data-stu-id="8c6ca-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="8c6ca-127">O Skype for Business híbrido permite combinar uma implantação local existente com o Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-127">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online.</span></span> <span data-ttu-id="8c6ca-128">Alguns usuários estão hospedados no local e alguns usuários estão hospedados online, mas os usuários compartilham o mesmo domínio SIP (Session Initiation Protocol), como contoso.com.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-128">Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com.</span></span> <span data-ttu-id="8c6ca-129">Você pode usar essa configuração híbrida para migrar do local para o Office 365 com o tempo, no seu cronograma.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-129">You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule.</span></span> <span data-ttu-id="8c6ca-130">O Skype for Business também pode ser integrado ao [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span><span class="sxs-lookup"><span data-stu-id="8c6ca-130">Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="8c6ca-131">**Figura 2: a configuração híbrida do Skype for Business**</span><span class="sxs-lookup"><span data-stu-id="8c6ca-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![A configuração híbrida do Skype for Business](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="8c6ca-133">A Figura 2 mostra a configuração híbrida do Skype for Business, que consiste em um pool de front-ends do Skype for Business local e um servidor de borda se comunicando com o Skype for Business online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="8c6ca-134">Para obter mais informações, consulte [Plan Hybrid Connectivity between Skype for Business Server e Skype for Business online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="8c6ca-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="8c6ca-135">Cloud PBX com o Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="8c6ca-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="8c6ca-136">O Cloud PBX com o Skype for Business Server permite que você migre uma implantação local existente do Skype for Business Server para uma topologia com conectividade PSTN (rede telefônica pública comutada) local.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="8c6ca-137">**Figura 3: Cloud PBX com o Skype for Business Server**</span><span class="sxs-lookup"><span data-stu-id="8c6ca-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Cloud PBX com o Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="8c6ca-139">A Figura 3 mostra o Cloud PBX com a configuração do Skype for Business Server, consistindo em um PBX existente local ou gateway Telco, um Skype for Business Server e o PSTN conectado ao Cloud PBX da Microsoft no Office 365, que inclui o Skype for Business Modo.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="8c6ca-140">Os usuários da organização que estão hospedados na nuvem podem receber serviços de PBX (central privada de comutação telefônica) da nuvem da Microsoft que incluem sinalização e caixa postal, mas a conectividade PSTN (sinal de discagem) é fornecida pelo Enterprise Voice de seu local Implantação do Skype for Business Server.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="8c6ca-141">Este é um ótimo exemplo de uma configuração híbrida que permite migrar gradualmente para um serviço baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-141">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service.</span></span> <span data-ttu-id="8c6ca-142">Você pode manter os recursos de voz de seus usuários ao começar a movê-los para o Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-142">You can retain your users' voice capabilities as you begin to move them to Skype for Business Online.</span></span> <span data-ttu-id="8c6ca-143">Você pode mover seus usuários em seu próprio ritmo, sabendo que seus recursos de voz continuarão independentemente de onde estejam hospedados.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-143">You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="8c6ca-144">Para obter mais informações, consulte [Plan Hybrid Connectivity between Skype for Business Server e Skype for Business online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="8c6ca-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="8c6ca-145">Se você ainda não tiver uma implantação existente do Lync Server ou do Skype for Business Server, poderá usar o Skype for Business Cloud Connector Edition, um conjunto de VMs (máquinas virtuais) empacotadas que implementam a conectividade PSTN local com o Cloud PBX.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="8c6ca-146">Para obter mais informações, consulte [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span><span class="sxs-lookup"><span data-stu-id="8c6ca-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="8c6ca-147">Implantação Híbrida do SharePoint</span><span class="sxs-lookup"><span data-stu-id="8c6ca-147">SharePoint Hybrid</span></span>

<span data-ttu-id="8c6ca-148">O SharePoint híbrido combina o SharePoint Online no Office 365 com seu farm local do SharePoint para obter o melhor de ambas as duas opções, a experiência conectada.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="8c6ca-149">**Figura 4: a configuração híbrida do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="8c6ca-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![A configuração híbrida do SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="8c6ca-151">A Figura 4 mostra a configuração híbrida do SharePoint, que consiste em um farm local do SharePoint que se comunica com o SharePoint Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="8c6ca-152">Cenários híbridos do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="8c6ca-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="8c6ca-153">OneDrive for Business híbrido</span><span class="sxs-lookup"><span data-stu-id="8c6ca-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="8c6ca-154">B2B de extranet híbrida</span><span class="sxs-lookup"><span data-stu-id="8c6ca-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="8c6ca-155">Pesquisa híbrida</span><span class="sxs-lookup"><span data-stu-id="8c6ca-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="8c6ca-156">Perfis híbridos</span><span class="sxs-lookup"><span data-stu-id="8c6ca-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="8c6ca-157">Seletor híbrido</span><span class="sxs-lookup"><span data-stu-id="8c6ca-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="8c6ca-158">É fácil habilitar cenários híbridos usando os assistentes que automatizam a configuração híbrida, disponível no centro de administração do SharePoint Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="8c6ca-159">Inicializador de aplicativos híbrido extensível</span><span class="sxs-lookup"><span data-stu-id="8c6ca-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="8c6ca-160">Permite que os usuários exibam e usem o vídeo do Office 365 e os aplicativos e experiências do Delve nas páginas de seu farm local do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="8c6ca-161">Todos esses cenários híbridos do SharePoint, exceto o inicializador de aplicativos híbridos extensíveis, estão disponíveis para os usuários do SharePoint 2016 e do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="8c6ca-162">Exchange Server 2016 híbrido</span><span class="sxs-lookup"><span data-stu-id="8c6ca-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="8c6ca-163">Com o Exchange Server 2016 híbrido, você pode obter os benefícios do Exchange Online no Office 365 para usuários online enquanto os usuários locais continuam a usar a infraestrutura existente do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="8c6ca-164">**Figura 5: a configuração híbrida do Exchange 2016**</span><span class="sxs-lookup"><span data-stu-id="8c6ca-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![A configuração híbrida do Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="8c6ca-166">A Figura 5 mostra a configuração híbrida do Exchange 2016, que consiste em servidores locais de caixa de correio do Exchange que se comunicam com proteção e caixas de correio do Exchange Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="8c6ca-167">Alguns usuários têm um servidor de email local e alguns usuários usam o Exchange Online, mas todos os usuários compartilham o mesmo espaço de endereço de email.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="8c6ca-168">Esta configuração híbrida:</span><span class="sxs-lookup"><span data-stu-id="8c6ca-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="8c6ca-169">Aproveita a infraestrutura existente do Exchange Server enquanto você migra para o Exchange Online ao longo do tempo, no seu cronograma.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="8c6ca-170">Permite que você dê suporte a sites remotos sem investir na infraestrutura de filial do escritório.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="8c6ca-171">Permite rotear emails de entrada da Internet por meio do Exchange Online Protection no Office 365.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="8c6ca-172">O atende às necessidades de organizações multinacionais com subsidiárias que exigem dados para residir no local.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="8c6ca-173">Você também pode integrar essa configuração híbrida com outros aplicativos do Microsoft Office 365, incluindo o Skype for Business Online e o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8c6ca-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="8c6ca-174">Para obter mais informações, consulte implantações híbridas do [Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).</span><span class="sxs-lookup"><span data-stu-id="8c6ca-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8c6ca-175">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c6ca-175">See Also</span></span>

[<span data-ttu-id="8c6ca-176">Nuvem híbrida da Microsoft para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="8c6ca-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="8c6ca-177">Recursos de arquitetura de TI da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="8c6ca-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

