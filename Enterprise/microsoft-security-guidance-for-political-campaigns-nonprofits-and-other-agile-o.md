---
title: "Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil"
ms.author: bcarter
author: bcarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "Resumo: Orientação de planejamento e implementação para velozes organizações com um perfil de ameaça maior."
ms.openlocfilehash: 632cb63877e159f18707dbf68eb7733082319654
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="d9625-103">Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil</span><span class="sxs-lookup"><span data-stu-id="d9625-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="d9625-104">**Resumo:** Orientação de planejamento e implementação para velozes organizações com um perfil de ameaça maior.</span><span class="sxs-lookup"><span data-stu-id="d9625-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="d9625-p101">Se sua organização estiver ágil, você tem uma pequena equipe de TI e seu perfil de ameaça é maior que a média, este guia foi criado para você. Esta solução demonstra como criar rapidamente um ambiente com os serviços de nuvem essencial que incluam controles seguros desde o início. Este guia inclui as recomendações de segurança prescritiva para proteger os dados, as identidades, email e acesso de dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="d9625-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="d9625-108">Diretrizes de solução de segurança</span><span class="sxs-lookup"><span data-stu-id="d9625-108">Security solution guidance</span></span>

<span data-ttu-id="d9625-p102">Este guia descreve como implementar um ambiente de nuvem seguro. A orientação da solução pode ser usada por qualquer organização. Ela inclui ajuda extra para organizações ágil e com contas de acesso e convidado BYOD. Você pode usar este guia como um ponto de partida para projetar seu próprio ambiente. Seus comentários são bem-vindos no [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="d9625-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="d9625-114">**Item**</span><span class="sxs-lookup"><span data-stu-id="d9625-114">**Item**</span></span> <br/> |<span data-ttu-id="d9625-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d9625-115">**Description**</span></span> <br/> |
|<span data-ttu-id="d9625-116">**Diretrizes de segurança da Microsoft para campanhas políticas**</span><span class="sxs-lookup"><span data-stu-id="d9625-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="d9625-117">[![Prego Thumb para pôster Minibarra definido.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="d9625-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="d9625-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="d9625-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span></span>| [<span data-ttu-id="d9625-119">Visio</span><span class="sxs-lookup"><span data-stu-id="d9625-119">Visio</span></span>](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx) <br/> |<span data-ttu-id="d9625-p103">Esta orientação usa uma organização campanha política como um exemplo. Use este guia como ponto de partida para qualquer ambiente.</span><span class="sxs-lookup"><span data-stu-id="d9625-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="d9625-122">**Orientação de segurança da Microsoft para organizações sem fins lucrativos**</span><span class="sxs-lookup"><span data-stu-id="d9625-122">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="d9625-123">[![Imagem em miniatura do arquivo baixável](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="d9625-123">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="d9625-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="d9625-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span></span>| [<span data-ttu-id="d9625-125">Visio</span><span class="sxs-lookup"><span data-stu-id="d9625-125">Visio</span></span>](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx) <br/> |<span data-ttu-id="d9625-p104">Este guia é ligeiramente revisado para organizações sem fins lucrativos. Por exemplo, ele referencia planos sem fins lucrativos do Office 365. A orientação técnica é o mesmo que o guia de solução de campanha política.</span><span class="sxs-lookup"><span data-stu-id="d9625-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="d9625-129">Guias do Laboratório de Teste</span><span class="sxs-lookup"><span data-stu-id="d9625-129">Test Lab Guides</span></span>

<span data-ttu-id="d9625-130">Para criar um ambiente de desenvolvimento e teste para essa solução, use os seguintes guias de laboratório de teste:</span><span class="sxs-lookup"><span data-stu-id="d9625-130">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="d9625-131">Configurar grupos e usuários para um ambiente de desenvolvimento e teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="d9625-131">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="d9625-132">Crie assinaturas de avaliação do Office 365 e EMS e, em seguida, criar grupos e usuários para uma campanha político representativo.</span><span class="sxs-lookup"><span data-stu-id="d9625-132">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="d9625-133">Criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="d9625-133">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="d9625-134">Crie quatro sites de equipe do SharePoint Online com interno, privadas, confidenciais e altamente confidenciais níveis de segurança.</span><span class="sxs-lookup"><span data-stu-id="d9625-134">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="d9625-135">Para recursos de segurança adicionais para demonstração ou prova de conceito, consulte [Guias de laboratório de teste do Office 365](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="d9625-135">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d9625-136">See Also</span><span class="sxs-lookup"><span data-stu-id="d9625-136">See Also</span></span>

[<span data-ttu-id="d9625-137">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="d9625-137">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="d9625-138">Adoção de nuvem Test Lab Guides (TLGs)</span><span class="sxs-lookup"><span data-stu-id="d9625-138">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d9625-139">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="d9625-139">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



