---
title: Isolado sites de equipe do SharePoint Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: 'Resumo: Saiba mais sobre os usos para sites de equipe do SharePoint Online isolados.'
ms.openlocfilehash: 0ce446860becb7a9dced91e26b6da55ed5fab1c9
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="2d3b7-103">Isolado sites de equipe do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2d3b7-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="2d3b7-104">**Resumo:** Saiba mais sobre os usos para sites de equipe do SharePoint Online isolados.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="2d3b7-p101">Sites de equipe do SharePoint Online são uma maneira fácil para criar rapidamente um espaço para colaboração de notas, documentos, artigos, um calendário e outros recursos no Microsoft Office 365. Sites de equipe do SharePoint Online baseiam-se em um grupo do Office 365 e tem um modelo de administração simplificada para permitir a colaboração aberta com um conjunto particular de membros de grupo ou de toda a organização. Um site de equipe do SharePoint Online padrão permite que os membros do grupo do Office 365 convidar outros usuários e controlar as configurações de permissões.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="2d3b7-p102">No entanto, em alguns casos, você deseja criar um site de equipe do SharePoint Online para colaboração onde as permissões do site são mais controladas por meio de associação de grupo e níveis de permissão do SharePoint Online, que só são gerenciados pelo SharePoint Administradores. Chamamos isso um site isolado, o que é isolado para o conjunto de usuários que estão colaborando, exibindo seu conteúdo ou administrando o site. Talvez você precise um site isolado para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2d3b7-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="2d3b7-111">Um projeto secreto dentro da sua organização.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="2d3b7-112">O local para a propriedade intelectual de altamente confidenciais ou valioso para sua organização.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="2d3b7-113">Os recursos de uma ação judicial tomadas por sua organização ou que ao qual ele está sujeito.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="2d3b7-114">Para compartilhar uma assinatura do Office 365 entre várias organizações que têm algumas overlap, mas existir na maioria das vezes como entidades empresariais separadas.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="2d3b7-115">Aqui estão os requisitos de um site isolado:</span><span class="sxs-lookup"><span data-stu-id="2d3b7-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="2d3b7-116">Somente os administradores do SharePoint Online podem executar a administração do site, que inclui a associação de grupo para acessar o site e como configurar permissões personalizadas.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="2d3b7-117">Membros do site não podem convidar outros membros para o site de equipe.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="2d3b7-p103">Usuários que não são membros do site isolado não podem solicitar acesso ao site. Eles receberão um acesso negado a página da web quando eles tentam acessar qualquer URL associada ao site.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="2d3b7-p104">A desvantagem da exigência de controle de acesso centralizado e permissões personalizadas pelos administradores do SharePoint Online é que o site permanece isolado ao longo do tempo. Por exemplo, atuais membros não é possível, intencionalmente ou acidentalmente, convidar ou configurar permissões personalizadas para outros usuários dentro da assinatura do Office 365, que não devem ser membros do site.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="2d3b7-122">Um site isolado pode ser usado com outros recursos, tais como:</span><span class="sxs-lookup"><span data-stu-id="2d3b7-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="2d3b7-123">Information Rights Management para garantir que os recursos no site permaneçam criptografados, mesmo se eles são baixados localmente e carregado para outro site que está disponível para toda a organização.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="2d3b7-124">Prevenção de perda de dados para impedir que os usuários enviem os recursos do site, como arquivos, em email.</span><span class="sxs-lookup"><span data-stu-id="2d3b7-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="2d3b7-125">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2d3b7-125">Next steps</span></span>

<span data-ttu-id="2d3b7-126">Para testar um site de equipe do SharePoint Online isolado em uma assinatura de avaliação, consulte as instruções passo a passo no [ambiente de desenvolvimento e teste de site de equipe isolado SharePoint Online](isolated-sharepoint-online-team-site-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2d3b7-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="2d3b7-127">Quando estiver pronto para implantar um site de equipe do SharePoint Online isolado em produção, consulte as considerações de design passo a passo em [um site de equipe do SharePoint Online isolado de Design](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="2d3b7-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2d3b7-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="2d3b7-128">See Also</span></span>

[<span data-ttu-id="2d3b7-129">Projetar um site de equipe do SharePoint Online isolado</span><span class="sxs-lookup"><span data-stu-id="2d3b7-129">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="2d3b7-130">Gerenciar um site de equipe do SharePoint Online isolado</span><span class="sxs-lookup"><span data-stu-id="2d3b7-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="2d3b7-131">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="2d3b7-131">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="2d3b7-132">Implantar um site de equipe do SharePoint Online isolado</span><span class="sxs-lookup"><span data-stu-id="2d3b7-132">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)


