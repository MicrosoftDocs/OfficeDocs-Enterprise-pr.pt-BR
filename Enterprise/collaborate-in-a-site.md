---
title: Colaborar com convidados em um site
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Saiba como colaborar com convidados em um site do SharePoint.
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017309"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="dc080-103">Colaborar com convidados em um site</span><span class="sxs-lookup"><span data-stu-id="dc080-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="dc080-104">Se você precisar colaborar com convidados entre documentos, dados e listas, poderá usar um site do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dc080-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="dc080-105">Os sites modernos do SharePoint estão conectados a grupos do Office 365 que podem gerenciar a associação do site e fornecer ferramentas de colaboração adicionais, como uma caixa de correio e um calendário compartilhados.</span><span class="sxs-lookup"><span data-stu-id="dc080-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="dc080-106">Neste artigo, veremos as etapas de configuração do Microsoft 365 necessárias para configurar um site do SharePoint para colaboração com convidados.</span><span class="sxs-lookup"><span data-stu-id="dc080-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="dc080-107">Configurações de relações organizacionais do Azure</span><span class="sxs-lookup"><span data-stu-id="dc080-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="dc080-108">O compartilhamento no Microsoft 365 é regido no seu nível mais alto pelas configurações de relações organizacionais no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="dc080-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="dc080-109">Se o compartilhamento de convidados estiver desabilitado ou restrito no Azure AD, isso substituirá as configurações de compartilhamento que você configurar no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="dc080-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="dc080-110">Verifique as configurações de relações organizacionais para garantir que o compartilhamento com convidados não seja bloqueado.</span><span class="sxs-lookup"><span data-stu-id="dc080-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Captura de tela da página de configurações de relações organizacionais do Active Directory do Azure](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="dc080-112">Para definir as configurações de relação organizacional</span><span class="sxs-lookup"><span data-stu-id="dc080-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="dc080-113">Faça logon no Microsoft Azure em [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="dc080-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="dc080-114">Na navegação à esquerda, clique em **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="dc080-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="dc080-115">No painel **visão geral** , clique em **relações organizacionais**.</span><span class="sxs-lookup"><span data-stu-id="dc080-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="dc080-116">No painel **relações organizacionais** , clique em **configurações**.</span><span class="sxs-lookup"><span data-stu-id="dc080-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="dc080-117">Certifique-se de que **Administradores e usuários na função de convite de convidado podem convidar** e **os membros podem convidar** estão definidos como **Sim**.</span><span class="sxs-lookup"><span data-stu-id="dc080-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="dc080-118">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="dc080-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="dc080-119">Observe as configurações na seção **restrições de colaboração** .</span><span class="sxs-lookup"><span data-stu-id="dc080-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="dc080-120">Certifique-se de que os domínios dos convidados com os quais você deseja colaborar não estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="dc080-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="dc080-121">Configurações de convidado de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="dc080-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="dc080-122">Os sites modernos do SharePoint usam grupos do Office 365 para controlar o acesso ao site.</span><span class="sxs-lookup"><span data-stu-id="dc080-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="dc080-123">As configurações de convidado de grupos do Office 365 devem ser ativadas para que o acesso de convidados nos sites do SharePoint funcione.</span><span class="sxs-lookup"><span data-stu-id="dc080-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Captura de tela das configurações de convidado do Office 365 groups no centro de administração do Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="dc080-125">Para definir as configurações de convidado de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="dc080-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="dc080-126">No centro de administração do Microsoft 365, no painel de navegação à esquerda, expanda **configurações**.</span><span class="sxs-lookup"><span data-stu-id="dc080-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="dc080-127">Clique em **serviços & suplementos**.</span><span class="sxs-lookup"><span data-stu-id="dc080-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="dc080-128">Na lista, clique em **grupos do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="dc080-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="dc080-129">Certifique-se de que o **grupo permitir Membros fora do seu conteúdo de grupo de acesso à organização** e **que os proprietários do grupo adicionem pessoas fora da sua organização a grupos de** seleção.</span><span class="sxs-lookup"><span data-stu-id="dc080-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="dc080-130">Se você tiver feito alterações, clique em **salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="dc080-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="dc080-131">Configurações de compartilhamento de nível da organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="dc080-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="dc080-132">Para que os convidados tenham acesso aos sites do SharePoint, as configurações de compartilhamento no nível da organização do SharePoint devem permitir o compartilhamento com convidados.</span><span class="sxs-lookup"><span data-stu-id="dc080-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="dc080-133">As configurações de nível de organização determinam quais configurações estão disponíveis para sites individuais.</span><span class="sxs-lookup"><span data-stu-id="dc080-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="dc080-134">As configurações do site não podem ser mais permissivas do que as configurações no nível da organização.</span><span class="sxs-lookup"><span data-stu-id="dc080-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="dc080-135">Se você quiser permitir o compartilhamento de arquivos e pastas com usuários anônimos, escolha **qualquer pessoa**.</span><span class="sxs-lookup"><span data-stu-id="dc080-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="dc080-136">Se você quiser garantir que todos os convidados devem se autenticar, escolha **novos e existentes convidados**.</span><span class="sxs-lookup"><span data-stu-id="dc080-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="dc080-137">Escolha a configuração mais permissiva que será necessária para qualquer site em sua organização.</span><span class="sxs-lookup"><span data-stu-id="dc080-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Captura de tela das configurações de compartilhamento no nível da organização do SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="dc080-139">Para definir as configurações de compartilhamento de nível da organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="dc080-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="dc080-140">No centro de administração do Microsoft 365, na navegação à esquerda, em **centros de administração**, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="dc080-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="dc080-141">No centro de administração do SharePoint, na navegação à esquerda, clique em **compartilhamento**.</span><span class="sxs-lookup"><span data-stu-id="dc080-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="dc080-142">Verifique se o compartilhamento externo do SharePoint está definido como **qualquer pessoa** ou **novo convidado existente**.</span><span class="sxs-lookup"><span data-stu-id="dc080-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="dc080-143">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="dc080-143">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="dc080-144">Criar um site</span><span class="sxs-lookup"><span data-stu-id="dc080-144">Create a site</span></span>

<span data-ttu-id="dc080-145">A próxima etapa é criar o site que você planeja usar para colaborar com convidados.</span><span class="sxs-lookup"><span data-stu-id="dc080-145">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="dc080-146">Para criar um site</span><span class="sxs-lookup"><span data-stu-id="dc080-146">To create a site</span></span>
1. <span data-ttu-id="dc080-147">No centro de administração do SharePoint, em **sites**, clique em **sites ativos**.</span><span class="sxs-lookup"><span data-stu-id="dc080-147">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="dc080-148">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="dc080-148">Click **Create**.</span></span>
3. <span data-ttu-id="dc080-149">Clique em **site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="dc080-149">Click **Team site**.</span></span>
4. <span data-ttu-id="dc080-150">Digite um nome de site e insira um nome para o proprietário do grupo (proprietário do site).</span><span class="sxs-lookup"><span data-stu-id="dc080-150">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="dc080-151">Em **Configurações avançadas**, escolha se você deseja que este seja um site público ou privado.</span><span class="sxs-lookup"><span data-stu-id="dc080-151">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="dc080-152">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dc080-152">Click **Next**.</span></span>
7. <span data-ttu-id="dc080-153">Clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="dc080-153">Click **Finish**.</span></span>

<span data-ttu-id="dc080-154">Vamos convidar os usuários mais tarde.</span><span class="sxs-lookup"><span data-stu-id="dc080-154">We'll invite users later.</span></span> <span data-ttu-id="dc080-155">Em seguida, é importante verificar as configurações de compartilhamento no nível do site para este site.</span><span class="sxs-lookup"><span data-stu-id="dc080-155">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="dc080-156">Configurações de compartilhamento no nível do site do SharePoint</span><span class="sxs-lookup"><span data-stu-id="dc080-156">SharePoint site level sharing settings</span></span>

<span data-ttu-id="dc080-157">Verifique as configurações de compartilhamento no nível do site para garantir que elas permitam o tipo de acesso que você deseja para este site.</span><span class="sxs-lookup"><span data-stu-id="dc080-157">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="dc080-158">Por exemplo, se você definir as configurações de nível de organização como **qualquer pessoa**, mas quiser que todos os convidados autentiquem esse site, verifique se as configurações de compartilhamento no nível do site estão definidas para **convidados novos e existentes**.</span><span class="sxs-lookup"><span data-stu-id="dc080-158">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="dc080-159">Observe que o site não pode ser compartilhado com usuários anônimos (configuração de**qualquer pessoa** ), mas arquivos e pastas individuais podem.</span><span class="sxs-lookup"><span data-stu-id="dc080-159">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Captura de tela das configurações de compartilhamento externo do site do SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="dc080-161">Para definir configurações de compartilhamento no nível do site</span><span class="sxs-lookup"><span data-stu-id="dc080-161">To set site-level sharing settings</span></span>
1. <span data-ttu-id="dc080-162">No centro de administração do SharePoint, na navegação à esquerda, expanda **sites** e clique em **sites ativos**.</span><span class="sxs-lookup"><span data-stu-id="dc080-162">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="dc080-163">Selecione o site que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="dc080-163">Select the site that you just created.</span></span>
3. <span data-ttu-id="dc080-164">Na faixa de opções, clique em **compartilhamento**.</span><span class="sxs-lookup"><span data-stu-id="dc080-164">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="dc080-165">Verifique se o compartilhamento está definido como **qualquer pessoa** ou **convidado novo e existente**.</span><span class="sxs-lookup"><span data-stu-id="dc080-165">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="dc080-166">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="dc080-166">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="dc080-167">Convidar usuários</span><span class="sxs-lookup"><span data-stu-id="dc080-167">Invite users</span></span>

<span data-ttu-id="dc080-168">As configurações de compartilhamento de convidados agora estão configuradas para que você possa começar a adicionar usuários internos e convidados ao seu site.</span><span class="sxs-lookup"><span data-stu-id="dc080-168">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="dc080-169">O acesso ao site é controlado pelo grupo associado do Office 365, portanto, vamos adicionar usuários lá.</span><span class="sxs-lookup"><span data-stu-id="dc080-169">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="dc080-170">Para convidar usuários internos para um grupo</span><span class="sxs-lookup"><span data-stu-id="dc080-170">To invite internal users to a group</span></span>
1. <span data-ttu-id="dc080-171">Navegue até o site em que você deseja adicionar usuários.</span><span class="sxs-lookup"><span data-stu-id="dc080-171">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="dc080-172">Clique em **Membros** no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="dc080-172">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="dc080-173">Clique em **Adicionar membros**.</span><span class="sxs-lookup"><span data-stu-id="dc080-173">Click **Add members**.</span></span>
4. <span data-ttu-id="dc080-174">Digite os nomes ou endereços de email dos usuários que você deseja convidar para o site e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="dc080-174">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="dc080-175">Os usuários convidados não podem ser adicionados do site.</span><span class="sxs-lookup"><span data-stu-id="dc080-175">Guest users can't be added from the site.</span></span> <span data-ttu-id="dc080-176">Você precisa adicioná-los usando o Outlook na Web.</span><span class="sxs-lookup"><span data-stu-id="dc080-176">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="dc080-177">Para convidar convidados para um site</span><span class="sxs-lookup"><span data-stu-id="dc080-177">To invite guests to a site</span></span>
1. <span data-ttu-id="dc080-178">No Outlook na Web, em **grupos**, clique no grupo em que você deseja adicionar membros.</span><span class="sxs-lookup"><span data-stu-id="dc080-178">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="dc080-179">Abra o cartão de visita do grupo e, em **mais opções** (...), clique em **adicionar membros**.</span><span class="sxs-lookup"><span data-stu-id="dc080-179">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="dc080-180">Digite os endereços de email dos convidados que você deseja convidar e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="dc080-180">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="dc080-181">Clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="dc080-181">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc080-182">Confira também</span><span class="sxs-lookup"><span data-stu-id="dc080-182">See Also</span></span>
