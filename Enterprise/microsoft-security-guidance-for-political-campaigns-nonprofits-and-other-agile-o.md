---
title: Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: 'Resumo: Diretrizes de planejamento e implementação para organizações ágeis que têm um perfil de ameaça maior.'
ms.openlocfilehash: 9f8979a674dd61710268df5b67857a5a8d641609
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="97f85-103">Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile</span><span class="sxs-lookup"><span data-stu-id="97f85-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="97f85-104">**Resumo:** Diretrizes de planejamento e implementação para organizações ágeis que têm um perfil de ameaça maior.</span><span class="sxs-lookup"><span data-stu-id="97f85-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="97f85-p101">Se sua organização é ágil, você tem uma pequena equipe de TI e seu perfil de ameaça é maior do que a média, estas diretrizes foram projetadas para você. Esta solução demonstra como criar rapidamente um ambiente com serviços de nuvem essenciais que incluem controles seguros desde o início. Essas diretrizes incluem as recomendações de segurança prescritiva para proteger dados, identidades, email e acesso de dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="97f85-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="97f85-108">Diretrizes da solução de segurança</span><span class="sxs-lookup"><span data-stu-id="97f85-108">Security solution guidance</span></span>

<span data-ttu-id="97f85-p102">Estas diretrizes descrevem como implementar um ambiente de nuvem seguro. As diretrizes da solução podem ser usadas por qualquer organização. Isso inclui ajuda adicional para organizações ágeis com contas de convidado e acesso BYOD. Você pode usar essas diretrizes como o ponto inicial para a criação do seu ambiente. Apreciamos seus comentários em [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="97f85-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="97f85-114">**Item**</span><span class="sxs-lookup"><span data-stu-id="97f85-114">**Item**</span></span> <br/> |<span data-ttu-id="97f85-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="97f85-115">**Description**</span></span> <br/> |
|<span data-ttu-id="97f85-116">**Diretrizes de segurança da Microsoft para campanhas políticas**</span><span class="sxs-lookup"><span data-stu-id="97f85-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="97f85-117">[![Miniatura para conjunto de mini-pôsteres.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="97f85-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="97f85-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)</span><span class="sxs-lookup"><span data-stu-id="97f85-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf) \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)</span></span> <br/> |<span data-ttu-id="97f85-p103">Este guia usa uma organização de campanha política como exemplo. Use este guia como um ponto de partida para qualquer ambiente.</span><span class="sxs-lookup"><span data-stu-id="97f85-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="97f85-121">**Diretrizes de segurança da Microsoft para organizações sem fins lucrativos**</span><span class="sxs-lookup"><span data-stu-id="97f85-121">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="97f85-122">[![Imagem em miniatura para arquivos disponíveis para download](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="97f85-122">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="97f85-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)</span><span class="sxs-lookup"><span data-stu-id="97f85-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf) \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)</span></span> <br/> |<span data-ttu-id="97f85-p104">Este guia é ligeiramente revisado para organizações sem fins lucrativos. Por exemplo, ele faz referência aos planos do Office 365 para entidades sem fins lucrativos. As diretrizes técnicas são as mesmas do guia de solução de campanha política.</span><span class="sxs-lookup"><span data-stu-id="97f85-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="97f85-127">Guias de laboratório de teste</span><span class="sxs-lookup"><span data-stu-id="97f85-127">Test Lab Guides</span></span>

<span data-ttu-id="97f85-128">Para criar um ambiente de desenvolvimento/teste para esta solução, siga a orientação de laboratório de teste seguinte:</span><span class="sxs-lookup"><span data-stu-id="97f85-128">To create a dev/test environment for this solution, use the following:</span></span> 
  
- [<span data-ttu-id="97f85-129">Defina grupos e usuários para um ambiente de desenvolvimento/teste de uma campanha política</span><span class="sxs-lookup"><span data-stu-id="97f85-129">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="97f85-130">Crie assinaturas de avaliação do Office 365 e EMS e, em seguida crie grupos e usuários para uma campanha política representativa.</span><span class="sxs-lookup"><span data-stu-id="97f85-130">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="97f85-131">Criar sites de equipe em um ambiente de desenvolvimento/teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="97f85-131">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="97f85-132">Crie quatro sites de equipe do SharePoint Online com os níveis de segurança Interno, Particular, Confidencial e Altamente Confidencial.</span><span class="sxs-lookup"><span data-stu-id="97f85-132">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="97f85-133">Confira outros recursos de segurança para demonstração ou prova de conceito em [Guias de laboratório de teste do Office 365](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="97f85-133">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="97f85-134">Confira também
</span><span class="sxs-lookup"><span data-stu-id="97f85-134">See Also</span></span>

[<span data-ttu-id="97f85-135">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="97f85-135">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="97f85-136">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="97f85-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="97f85-137">Recursos de arquitetura de TI do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="97f85-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



