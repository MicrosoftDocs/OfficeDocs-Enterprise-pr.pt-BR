---
title: Sites de equipe isolados do SharePoint Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: 'Resumo: conheça as utilizações dos sites de equipe do SharePoint Online isolados.'
ms.openlocfilehash: 86aa5fb9fa4d4eb2f76e1e32a6fcd8bda7b29b76
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="a5a37-103">Sites de equipe isolados do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a5a37-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="a5a37-104">**Resumo:** conheça as utilizações dos sites de equipe do SharePoint Online isolados.</span><span class="sxs-lookup"><span data-stu-id="a5a37-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="a5a37-p101">Os sites de equipe do SharePoint Online são uma maneira fácil de criar rapidamente um espaço para colaboração em anotações, documentos, artigos, um calendário e outros recursos do Microsoft Office 365. Os sites de equipe do SharePoint Online são baseados em um grupo do Office 365 e possuem um modelo de administração simplificado para permitir a colaboração aberta entre um determinado conjunto de membros do grupo ou toda a organização. Um site de equipe padrão do SharePoint Online permite que os membros do grupo do Office 365 convidem outros usuários e controlem as configurações de permissões.</span><span class="sxs-lookup"><span data-stu-id="a5a37-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="a5a37-p102">No entanto, em alguns casos, você quer criar um site de equipe do SharePoint Online para colaboração em locais onde as permissões desse site sejam controladas com maior rigidez por meio da associação ao grupo e níveis de permissão do SharePoint Online, que são gerenciados apenas por administradores do SharePoint. Chamamos isso de um site isolado, que é isolado do conjunto de usuários que estão colaborando, visualizando seu conteúdo ou administrando o site. Um site isolado pode ser necessário para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a5a37-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="a5a37-111">Um projeto secreto em sua organização.</span><span class="sxs-lookup"><span data-stu-id="a5a37-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="a5a37-112">O local da propriedade intelectual altamente confidencial ou valiosa para sua organização.</span><span class="sxs-lookup"><span data-stu-id="a5a37-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="a5a37-113">Os recursos de uma ação judicial iniciada por sua organização ou à qual a empresa está sendo submetida.</span><span class="sxs-lookup"><span data-stu-id="a5a37-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="a5a37-114">Para compartilhar uma assinatura do Office 365 entre várias organizações que possuem alguma sobreposição, mas, na maioria das vezes, existem como entidades comerciais separadas.</span><span class="sxs-lookup"><span data-stu-id="a5a37-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="a5a37-115">Veja os requisitos de um site isolado:</span><span class="sxs-lookup"><span data-stu-id="a5a37-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="a5a37-116">Apenas os administradores do SharePoint Online podem realizar a administração de sites, o que inclui a associação ao grupo para acessar o site e a configuração de permissões personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a5a37-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="a5a37-117">Os membros do site não podem convidar outros membros para o site de equipe.</span><span class="sxs-lookup"><span data-stu-id="a5a37-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="a5a37-p103">Os usuários que não são membros do site isolado não podem solicitar acesso ao site e verão uma página da Web de acesso negado ao tentar acessar qualquer URL associada ao site.</span><span class="sxs-lookup"><span data-stu-id="a5a37-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="a5a37-p104">A desvantagem de exigir controle de acesso centralizado e permissões personalizadas pelos administradores do SharePoint Online é que o site manterá-se isolado ao longo do tempo. Por exemplo, os membros atuais não poderão, intencionalmente ou acidentalmente, convidar ou configurar permissões personalizadas para outros usuários na assinatura do Office 365 que não sejam membros do site.</span><span class="sxs-lookup"><span data-stu-id="a5a37-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="a5a37-122">Um site isolado pode ser usado com outros recursos, como:</span><span class="sxs-lookup"><span data-stu-id="a5a37-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="a5a37-123">Gerenciamento de Direitos de Informação para garantir que os recursos do site permaneçam criptografados, mesmo que eles sejam baixados localmente e carregados em outro site que esteja disponível para toda a organização.</span><span class="sxs-lookup"><span data-stu-id="a5a37-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="a5a37-124">Prevenção contra a perda de dados para evitar que os usuários enviem os recursos do site, como arquivos, por email.</span><span class="sxs-lookup"><span data-stu-id="a5a37-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="a5a37-125">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a5a37-125">Next steps</span></span>

<span data-ttu-id="a5a37-126">Para experimentar um site de equipe do SharePoint Online isolado em uma assinatura de avaliação, confira as instruções passo a passo no [Site de equipe do SharePoint Online isolado no seu ambiente de desenvolvimento/teste](isolated-sharepoint-online-team-site-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a5a37-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a5a37-127">Quando estiver pronto para implantar um site de equipe do SharePoint Online isolado na produção, confira as considerações de design passo a passo no [Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="a5a37-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5a37-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="a5a37-128">See Also</span></span>

<span data-ttu-id="a5a37-129">[Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md)</span><span class="sxs-lookup"><span data-stu-id="a5a37-129">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
[<span data-ttu-id="a5a37-130">Gerenciar um site de equipe do SharePoint Online isolado</span><span class="sxs-lookup"><span data-stu-id="a5a37-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="a5a37-131">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="a5a37-131">Security solutions</span></span>](security-solutions.md)

<span data-ttu-id="a5a37-132">[Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md)</span><span class="sxs-lookup"><span data-stu-id="a5a37-132">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>


