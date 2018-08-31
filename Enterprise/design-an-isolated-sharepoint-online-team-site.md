---
title: Projetar um site de equipe do SharePoint Online isolado
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: 'Resumo: Etapa durante o processo de design para sites de equipe do SharePoint Online isolados.'
ms.openlocfilehash: 4807b7cef0a401901eb5abec3d683ca67b2193db
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914836"
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="344ac-103">Projetar um site de equipe do SharePoint Online isolado</span><span class="sxs-lookup"><span data-stu-id="344ac-103">Design an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="344ac-104">**Resumo:** Percorrer o processo de design para sites de equipe do SharePoint Online isolados.</span><span class="sxs-lookup"><span data-stu-id="344ac-104">**Summary:** Step through the design process for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="344ac-105">Este artigo apresenta as decisões de design principal, que você deve fazer antes de criar um site de equipe do SharePoint Online isolado.</span><span class="sxs-lookup"><span data-stu-id="344ac-105">This article takes you through the key design decisions you must make before creating an isolated SharePoint Online team site.</span></span>
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="344ac-106">Fase 1: Determinar seus grupos do SharePoint e níveis de permissão</span><span class="sxs-lookup"><span data-stu-id="344ac-106">Phase 1: Determine your SharePoint groups and permission levels</span></span>

<span data-ttu-id="344ac-107">Cada site de equipe do SharePoint Online, por padrão é criado com os seguintes grupos do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="344ac-107">Every SharePoint Online team site by default is created with the following SharePoint groups:</span></span>
  
- <span data-ttu-id="344ac-108">\<nome do site > membros</span><span class="sxs-lookup"><span data-stu-id="344ac-108">\<site name> Members</span></span>
    
- <span data-ttu-id="344ac-109">\<nome do site > visitantes</span><span class="sxs-lookup"><span data-stu-id="344ac-109">\<site name> Visitors</span></span>
    
- <span data-ttu-id="344ac-110">\<nome do site > proprietários</span><span class="sxs-lookup"><span data-stu-id="344ac-110">\<site name> Owners</span></span>
    
<span data-ttu-id="344ac-111">Esses grupos são separados dos grupos do Office 365 e Windows Azure AD (Active Directory) e são a base para atribuir permissões para os recursos do site.</span><span class="sxs-lookup"><span data-stu-id="344ac-111">These groups are separate from Office 365 and Azure Active Directory (AD) groups and are the basis for assigning permissions for the resources of the site.</span></span>
  
<span data-ttu-id="344ac-p101">O conjunto de permissões específicas que determina o que um membro de um grupo do SharePoint pode fazer em um site é um nível de permissão. Existem três níveis de permissão por padrão para um site de equipe do SharePoint Online: controle total, leitura e editar. A tabela a seguir mostra a correlação de padrão de grupos do SharePoint e níveis de permissão atribuídos:</span><span class="sxs-lookup"><span data-stu-id="344ac-p101">The set of specific permissions that determines what a member of a SharePoint group can do in a site is a permission level. There are three permission levels by default for a SharePoint Online team site: Edit, Read, and Full control. The following table shows the default correlation of SharePoint groups and assigned permission levels:</span></span>
  
|<span data-ttu-id="344ac-115">**Grupo do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="344ac-115">**SharePoint group**</span></span>|<span data-ttu-id="344ac-116">**Nível de permissão**</span><span class="sxs-lookup"><span data-stu-id="344ac-116">**Permission level**</span></span>|
|:-----|:-----|
|<span data-ttu-id="344ac-117">\<nome do site > membros</span><span class="sxs-lookup"><span data-stu-id="344ac-117">\<site name> Members</span></span>  <br/> |<span data-ttu-id="344ac-118">Editar</span><span class="sxs-lookup"><span data-stu-id="344ac-118">Edit</span></span>  <br/> |
|<span data-ttu-id="344ac-119">\<nome do site > visitantes</span><span class="sxs-lookup"><span data-stu-id="344ac-119">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="344ac-120">Ler</span><span class="sxs-lookup"><span data-stu-id="344ac-120">Read</span></span>  <br/> |
|<span data-ttu-id="344ac-121">\<nome do site > proprietários</span><span class="sxs-lookup"><span data-stu-id="344ac-121">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="344ac-122">Controle total</span><span class="sxs-lookup"><span data-stu-id="344ac-122">Full control</span></span>  <br/> |
   
 <span data-ttu-id="344ac-p102">**Práticas recomendadas:** Você pode criar grupos adicionais do SharePoint e níveis de permissão. No entanto, é recomendável usar os grupos padrão do SharePoint e níveis de permissão para o seu site do SharePoint Online isolado.</span><span class="sxs-lookup"><span data-stu-id="344ac-p102">**Best practice:** You can create additional SharePoint groups and permission levels. However, we recommend using the default SharePoint groups and permission levels for your isolated SharePoint Online site.</span></span>
  
<span data-ttu-id="344ac-125">Aqui estão os níveis de permissão e grupos padrão do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="344ac-125">Here are the default SharePoint groups and permission levels.</span></span>
  
![Os grupos do SharePoint e níveis de permissão padrão de um site do SharePoint Online.](media/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a><span data-ttu-id="344ac-127">Fase 2: Atribuir permissões aos usuários com grupos de acesso</span><span class="sxs-lookup"><span data-stu-id="344ac-127">Phase 2: Assign permissions to users with access groups</span></span>

<span data-ttu-id="344ac-p103">Você pode atribuir permissões aos usuários adicionando sua conta de usuário ou um grupo do Office 365 ou no Windows Azure AD do qual a conta de usuário é um membro, aos grupos do SharePoint. Uma vez adicionados, as contas de usuário do Office 365, seja diretamente ou indiretamente por meio de associação em um grupo do Office 365 ou no Windows Azure AD, recebem o nível de permissão associado ao grupo do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="344ac-p103">You can assign permissions to users by adding their user account, or an Office 365 or Azure AD group of which the user account is a member, to the SharePoint groups. Once added, the Office 365 user accounts, either directly or indirectly via membership in an Office 365 or Azure AD group, are assigned the permission level associated with the SharePoint group.</span></span>
  
<span data-ttu-id="344ac-130">Usando os grupos padrão do SharePoint como exemplo:</span><span class="sxs-lookup"><span data-stu-id="344ac-130">Using the default SharePoint groups as an example:</span></span>
  
- <span data-ttu-id="344ac-131">Membros do ** \<nome do site > membros** grupo do SharePoint, que pode incluir contas de usuário e grupos, recebem o nível de permissão **Editar**</span><span class="sxs-lookup"><span data-stu-id="344ac-131">Members of the **\<site name> Members** SharePoint group, which can include both user accounts and groups, are assigned the **Edit** permission level</span></span>
    
- <span data-ttu-id="344ac-132">Membros do ** \<nome do site > visitantes** grupo do SharePoint, que pode incluir contas de usuário e grupos, recebem o nível de permissão de **leitura**</span><span class="sxs-lookup"><span data-stu-id="344ac-132">Members of the **\<site name> Visitors** SharePoint group, which can include both user accounts and groups, are assigned the **Read** permission level</span></span>
    
- <span data-ttu-id="344ac-133">Membros do ** \<nome do site > proprietários** grupo do SharePoint, que pode incluir contas de usuário e grupos, recebem o nível de permissão **controle total**</span><span class="sxs-lookup"><span data-stu-id="344ac-133">Members of the **\<site name> Owners** SharePoint group, which can include both user accounts and groups, are assigned the **Full control** permission level</span></span>
    
 <span data-ttu-id="344ac-p104">**Práticas recomendadas:** Embora seja possível gerenciar permissões por meio de contas de usuário individuais, recomendamos que você use um único grupo Azure AD, conhecido como um grupo de acesso, em vez disso. Isso simplifica o gerenciamento de permissões por meio da participação no grupo de acesso, em vez de contas de gerenciamento da lista de usuário para cada grupo do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="344ac-p104">**Best practice:** Although you can manage permissions through individual user accounts, we recommend that you use a single Azure AD group, known as an access group, instead. This simplifies the management of permissions through membership in the access group, rather than managing the list of user accounts for each SharePoint group.</span></span>
  
<span data-ttu-id="344ac-p105">Grupos do Azure AD para o Office 365 são diferentes grupos do Office 365. Grupos do Azure AD aparecem no Centro de administração do Office com seu conjunto de **tipo** para **segurança** e não têm um endereço de email. Grupos do Azure AD podem ser gerenciados em:</span><span class="sxs-lookup"><span data-stu-id="344ac-p105">Azure AD groups for Office 365 are different than Office 365 groups. Azure AD groups appear in the Office Admin center with their **Type** set to **Security** and do not have an email address. Azure AD groups can be managed within:</span></span>
  
- <span data-ttu-id="344ac-139">Windows Server Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="344ac-139">Windows Server Active Directory (AD)</span></span>
    
    <span data-ttu-id="344ac-p106">Esses são grupos que foram criados na infraestrutura do Windows Server AD local e sincronizados à sua assinatura do Office 365. No Centro de administração do Office, esses grupos têm um **Status** de **Synched com o active directory**.</span><span class="sxs-lookup"><span data-stu-id="344ac-p106">These are groups that have been created in your on-premises Windows Server AD infrastructure and synchronized to your Office 365 subscription. In the Office Admin center, these groups have a **Status** of **Synched with active directory**.</span></span>
    
- <span data-ttu-id="344ac-142">Office 365</span><span class="sxs-lookup"><span data-stu-id="344ac-142">Office 365</span></span>
    
    <span data-ttu-id="344ac-p107">Estes são os grupos que foram criados usando o Centro de administração do Office, o portal do Azure ou Microsoft PowerShell. No Centro de administração do Office, esses grupos têm um **Status** de **nuvem**.</span><span class="sxs-lookup"><span data-stu-id="344ac-p107">These are groups that have been created using either the Office Admin center, the Azure portal, or Microsoft PowerShell. In the Office Admin center, these groups have a **Status** of **Cloud**.</span></span>
    
 <span data-ttu-id="344ac-145">**Práticas recomendadas:** Se você estiver usando o Windows Server AD local e sincronizar com sua assinatura do Office 365, execute o usuário e o gerenciamento de grupo com o Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="344ac-145">**Best practice:** If you are using Windows Server AD on-premises and synchronizing with your Office 365 subscription, perform your user and group management with Windows Server AD.</span></span>
  
<span data-ttu-id="344ac-146">Para sites de equipe do SharePoint Online isolados, a estrutura do grupo recomendado tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="344ac-146">For isolated SharePoint Online team sites, the recommended group structure looks like this:</span></span>
  
|<span data-ttu-id="344ac-147">**Grupo do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="344ac-147">**SharePoint group**</span></span>|<span data-ttu-id="344ac-148">**Grupo Azure de acesso baseada em AD**</span><span class="sxs-lookup"><span data-stu-id="344ac-148">**Azure AD-based access group**</span></span>|<span data-ttu-id="344ac-149">**Nível de permissão**</span><span class="sxs-lookup"><span data-stu-id="344ac-149">**Permission level**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="344ac-150">\<nome do site > membros</span><span class="sxs-lookup"><span data-stu-id="344ac-150">\<site name> Members</span></span>  <br/> |<span data-ttu-id="344ac-151">\<nome do site > membros</span><span class="sxs-lookup"><span data-stu-id="344ac-151">\<site name> Members</span></span>  <br/> |<span data-ttu-id="344ac-152">Editar</span><span class="sxs-lookup"><span data-stu-id="344ac-152">Edit</span></span>  <br/> |
|<span data-ttu-id="344ac-153">\<nome do site > visitantes</span><span class="sxs-lookup"><span data-stu-id="344ac-153">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="344ac-154">\<nome do site > visualizadores</span><span class="sxs-lookup"><span data-stu-id="344ac-154">\<site name> Viewers</span></span>  <br/> |<span data-ttu-id="344ac-155">Ler</span><span class="sxs-lookup"><span data-stu-id="344ac-155">Read</span></span>  <br/> |
|<span data-ttu-id="344ac-156">\<nome do site > proprietários</span><span class="sxs-lookup"><span data-stu-id="344ac-156">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="344ac-157">\<nome do site > Admins</span><span class="sxs-lookup"><span data-stu-id="344ac-157">\<site name> Admins</span></span>  <br/> |<span data-ttu-id="344ac-158">Controle total</span><span class="sxs-lookup"><span data-stu-id="344ac-158">Full control</span></span>  <br/> |
   
 <span data-ttu-id="344ac-p108">**Práticas recomendadas:** Embora você possa usar o Office 365 ou Azure AD grupos como membros de grupos do SharePoint, é recomendável que você use grupos do Azure AD. Grupos do AD Azure, gerenciados através do Windows Server AD ou Office 365, proporcionam mais flexibilidade para usar grupos aninhados para atribuir permissões.</span><span class="sxs-lookup"><span data-stu-id="344ac-p108">**Best practice:** Although you can use either Office 365 or Azure AD groups as members of SharePoint groups, we recommend that you use Azure AD groups. Azure AD groups, managed either through Windows Server AD or Office 365, give you more flexibility to use nested groups to assign permissions.</span></span>
  
<span data-ttu-id="344ac-161">Aqui está configurados para usar grupos do Azure acesso baseado em AD de grupos do SharePoint padrão.</span><span class="sxs-lookup"><span data-stu-id="344ac-161">Here are the default SharePoint groups configured to use Azure AD-based access groups.</span></span>
  
![Usando os grupos de acesso como membros de grupos de sites do SharePoint Online padrão.](media/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
<span data-ttu-id="344ac-163">Quando estiver criando os grupos de três do access, lembre-se do seguinte:</span><span class="sxs-lookup"><span data-stu-id="344ac-163">When designing the three access groups, keep the following in mind:</span></span>
  
- <span data-ttu-id="344ac-164">Deve haver apenas alguns membros no ** \<nome do site > Admins** grupo de acesso, correspondente a um pequeno número de administradores do SharePoint Online, que estão gerenciando o site de equipe.</span><span class="sxs-lookup"><span data-stu-id="344ac-164">There should be only a few members in the **\<site name> Admins** access group, corresponding to a small number of SharePoint Online administrators who are managing the team site.</span></span>
    
- <span data-ttu-id="344ac-p109">A maioria dos seus membros do site está no ** \<nome do site > membros** ou ** \<nome do site > visualizadores** acessar grupos. Porque sites membros no ** \<nome do site > membros** grupo acesso têm a capacidade de excluir ou modificar os recursos do site, considere cuidadosamente sua associação. Quando estiver em dúvida, adicione o membro de site para o ** \<nome do site > visualizadores** grupo de acesso.</span><span class="sxs-lookup"><span data-stu-id="344ac-p109">Most of your site members are in the **\<site name> Members** or **\<site name> Viewers** access groups. Because site members in the **\<site name> Members** access group have the ability to delete or modify resources in the site, carefully consider its membership. When in doubt, add the site member to the **\<site name> Viewers** access group.</span></span>
    
<span data-ttu-id="344ac-168">Aqui está um exemplo dos grupos do SharePoint e grupos de acesso para um site isolado chamado ProjectX.</span><span class="sxs-lookup"><span data-stu-id="344ac-168">Here is an example of the SharePoint groups and access groups for an isolated site named ProjectX.</span></span>
  
![Um exemplo de como usar os grupos de acesso em um site do SharePoint Online chamado ProjectX.](media/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a><span data-ttu-id="344ac-170">Fase 3: Usar aninhadas grupos do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="344ac-170">Phase 3: Use nested Azure AD groups</span></span>

<span data-ttu-id="344ac-p110">Para um projeto confinado a um pequeno número de pessoas, um único nível de grupos de Azure acesso baseado em AD adicionados aos grupos do SharePoint do site mais adequado para a maioria dos cenários. No entanto, se você tiver um grande número de pessoas e as pessoas já estejam membros de estabelecidos grupos do AD do Windows Azure, você pode mais facilmente atribuir permissões do SharePoint usando grupos aninhados ou grupos que contêm outros grupos como membros.</span><span class="sxs-lookup"><span data-stu-id="344ac-p110">For a project confined to a small number of people, a single level of Azure AD-based access groups added to the SharePoint groups of the site will fit most scenarios. However, if you have a large number of people and those people are already members of established Azure AD groups, you can more easily assign SharePoint permissions by using nested groups, or groups that contain other groups as members.</span></span>
  
<span data-ttu-id="344ac-p111">Por exemplo, você deseja criar um site de equipe online isolado do SharePoint para colaboração entre os executivos de vendas, marketing, engenharia, legais e suporte departamentos e os departamentos já seus próprios grupos com a conta de usuário executivo associação. Em vez de criar um novo grupo para os novos membros do site e colocar todas as contas de usuário individual de executivos nela, coloque os grupos de executivos existentes para cada departamento no novo grupo.</span><span class="sxs-lookup"><span data-stu-id="344ac-p111">For example, you want to create an isolated SharePoint online team site for collaboration among the executives of the sales, marketing, engineering, legal, and support departments and those departments already their own groups with executive user account membership. Rather than creating a new group for the new site members and placing all the individual executive user accounts in it, put the existing executive groups for each department in the new group.</span></span>
  
 <span data-ttu-id="344ac-p112">Se você estiver compartilhando uma assinatura do Office 365 entre várias organizações, um único nível de associação de grupo para um site isolada para uma organização pode se tornar difícil de gerenciar devido ao grande número de contas de usuário. Nesse caso, você pode usar grupos do Azure AD para cada organização que contenham os grupos em suas organizações para gerenciar as permissões aninhados.</span><span class="sxs-lookup"><span data-stu-id="344ac-p112">If you are sharing an Office 365 subscription between multiple organizations, a single level of group membership for an isolated site for an organization might become difficult to manage due to the sheer number of user accounts. In this case, you can use nested Azure AD groups for each organization that contain the groups within their organizations to manage the permissions.</span></span>
  
<span data-ttu-id="344ac-177">Para usar grupos de Azure AD aninhados:</span><span class="sxs-lookup"><span data-stu-id="344ac-177">To use nested Azure AD groups:</span></span>
  
1. <span data-ttu-id="344ac-178">Identificar ou criar os grupos do Azure AD que conterá a contas de usuário e adicione as contas de usuário apropriados como membros.</span><span class="sxs-lookup"><span data-stu-id="344ac-178">Identify or create the Azure AD groups that will contain user accounts and add the appropriate user accounts as members.</span></span>
    
2. <span data-ttu-id="344ac-179">Crie o grupo do Azure acesso baseado em AD contêiner que conterá os outros grupos do Azure AD e adicionar esses grupos como membros.</span><span class="sxs-lookup"><span data-stu-id="344ac-179">Create the container Azure AD-based access group that will contain the other Azure AD groups and add those groups as members.</span></span>
    
3.  <span data-ttu-id="344ac-180">Para o nível apropriado de acesso para o grupo de acesso do contêiner, identifique o grupo do SharePoint e o nível de permissão correspondente.</span><span class="sxs-lookup"><span data-stu-id="344ac-180">For the appropriate level of access for the container access group, identify the SharePoint group and corresponding permission level.</span></span>
    
> [!NOTE]
> <span data-ttu-id="344ac-181">É possível usar grupos aninhados do Office 365.</span><span class="sxs-lookup"><span data-stu-id="344ac-181">You cannot use nested Office 365 groups.</span></span> 
  
<span data-ttu-id="344ac-182">Aqui está um exemplo do Azure AD aninhado grupos para o grupo de acesso do membro ProjectX.</span><span class="sxs-lookup"><span data-stu-id="344ac-182">Here is an example of nested Azure AD groups for the ProjectX member access group.</span></span>
  
![Um exemplo de como usar grupos de acesso aninhados para o grupo de acesso de membros do site do ProjectX.](media/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
<span data-ttu-id="344ac-184">Como todas as contas de usuário na Research, engenharia e Project leads equipes destinam-se a ser membros do site, é mais fácil adicionar seus grupos do Azure AD ao grupo acesso ProjectX membros.</span><span class="sxs-lookup"><span data-stu-id="344ac-184">Because all of the user accounts in the Research, Engineering, and Project leads teams are intended to be site members, it is easier to add their Azure AD groups to the ProjectX Members access group.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="344ac-185">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="344ac-185">Next step</span></span>

<span data-ttu-id="344ac-186">Quando você estiver pronto para criar e configurar um site isolado em produção, consulte [Deploy um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="344ac-186">When you are ready to create and configure an isolated site in production, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="344ac-187">Confira também</span><span class="sxs-lookup"><span data-stu-id="344ac-187">See Also</span></span>

[<span data-ttu-id="344ac-188">Sites de equipe do SharePoint Online isolados</span><span class="sxs-lookup"><span data-stu-id="344ac-188">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="344ac-189">Gerenciar um site de equipe do SharePoint Online isolado</span><span class="sxs-lookup"><span data-stu-id="344ac-189">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="344ac-190">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="344ac-190">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="344ac-191">Implantar um site de equipe do SharePoint Online isolado</span><span class="sxs-lookup"><span data-stu-id="344ac-191">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



