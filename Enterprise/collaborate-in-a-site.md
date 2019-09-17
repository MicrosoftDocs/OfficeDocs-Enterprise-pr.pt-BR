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
ms.openlocfilehash: 23f55e22d4c85dcd168c403f50b35f574be9ac07
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992380"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="9173c-103">Colaborar com convidados em um site</span><span class="sxs-lookup"><span data-stu-id="9173c-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="9173c-104">Se você precisar colaborar com convidados entre documentos, dados e listas, poderá usar um site do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9173c-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="9173c-105">Os sites modernos do SharePoint estão conectados a grupos do Office 365 que podem gerenciar a associação do site e fornecer ferramentas de colaboração adicionais, como uma caixa de correio e um calendário compartilhados.</span><span class="sxs-lookup"><span data-stu-id="9173c-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="9173c-106">Neste artigo, veremos as etapas de configuração do Microsoft 365 necessárias para configurar um site do SharePoint para colaboração com convidados.</span><span class="sxs-lookup"><span data-stu-id="9173c-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="9173c-107">Configurações de relações organizacionais do Azure</span><span class="sxs-lookup"><span data-stu-id="9173c-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="9173c-108">O compartilhamento no Microsoft 365 é regido no seu nível mais alto pelas configurações de relações organizacionais no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9173c-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="9173c-109">Se o compartilhamento de convidados estiver desabilitado ou restrito no Azure AD, isso substituirá as configurações de compartilhamento que você configurar no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="9173c-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="9173c-110">Verifique as configurações de relações organizacionais para garantir que o compartilhamento com convidados não seja bloqueado.</span><span class="sxs-lookup"><span data-stu-id="9173c-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Captura de tela da página de configurações de relações organizacionais do Active Directory do Azure](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="9173c-112">Para definir as configurações de relação organizacional</span><span class="sxs-lookup"><span data-stu-id="9173c-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="9173c-113">Faça logon no Microsoft Azure em [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9173c-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="9173c-114">Na navegação à esquerda, clique em **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="9173c-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="9173c-115">No painel **visão geral** , clique em **relações organizacionais**.</span><span class="sxs-lookup"><span data-stu-id="9173c-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="9173c-116">No painel **relações organizacionais** , clique em **configurações**.</span><span class="sxs-lookup"><span data-stu-id="9173c-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="9173c-117">Certifique-se de que **Administradores e usuários na função de convite de convidado podem convidar** e **os membros podem convidar** estão definidos como **Sim**.</span><span class="sxs-lookup"><span data-stu-id="9173c-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="9173c-118">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="9173c-119">Observe as configurações na seção **restrições de colaboração** .</span><span class="sxs-lookup"><span data-stu-id="9173c-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="9173c-120">Certifique-se de que os domínios dos convidados com os quais você deseja colaborar não estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="9173c-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="9173c-121">Configurações de convidado de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="9173c-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="9173c-122">Os sites modernos do SharePoint usam grupos do Office 365 para controlar o acesso ao site.</span><span class="sxs-lookup"><span data-stu-id="9173c-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="9173c-123">As configurações de convidado de grupos do Office 365 devem ser ativadas para que o acesso de convidados nos sites do SharePoint funcione.</span><span class="sxs-lookup"><span data-stu-id="9173c-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Captura de tela das configurações de convidado do Office 365 groups no centro de administração do Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="9173c-125">Para definir as configurações de convidado de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="9173c-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="9173c-126">No centro de administração do Microsoft 365, no painel de navegação à esquerda, expanda **configurações**.</span><span class="sxs-lookup"><span data-stu-id="9173c-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="9173c-127">Clique em **serviços & suplementos**.</span><span class="sxs-lookup"><span data-stu-id="9173c-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="9173c-128">Na lista, clique em **grupos do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="9173c-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="9173c-129">Certifique-se de que o **grupo permitir Membros fora do seu conteúdo de grupo de acesso à organização** e **que os proprietários do grupo adicionem pessoas fora da sua organização a grupos de** seleção.</span><span class="sxs-lookup"><span data-stu-id="9173c-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="9173c-130">Se você tiver feito alterações, clique em **salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="9173c-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="9173c-131">Configurações de compartilhamento de nível da organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="9173c-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="9173c-132">Para que os convidados tenham acesso aos sites do SharePoint, as configurações de compartilhamento no nível da organização do SharePoint devem permitir o compartilhamento com convidados.</span><span class="sxs-lookup"><span data-stu-id="9173c-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="9173c-133">As configurações de nível de organização determinam quais configurações estão disponíveis para sites individuais.</span><span class="sxs-lookup"><span data-stu-id="9173c-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="9173c-134">As configurações do site não podem ser mais permissivas do que as configurações no nível da organização.</span><span class="sxs-lookup"><span data-stu-id="9173c-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="9173c-135">Se você quiser permitir o compartilhamento de arquivos e pastas com usuários anônimos, escolha **qualquer pessoa**.</span><span class="sxs-lookup"><span data-stu-id="9173c-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="9173c-136">Se você quiser garantir que todos os convidados devem se autenticar, escolha **novos e existentes convidados**.</span><span class="sxs-lookup"><span data-stu-id="9173c-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="9173c-137">Escolha a configuração mais permissiva que será necessária para qualquer site em sua organização.</span><span class="sxs-lookup"><span data-stu-id="9173c-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Captura de tela das configurações de compartilhamento no nível da organização do SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="9173c-139">Para definir as configurações de compartilhamento de nível da organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="9173c-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="9173c-140">No centro de administração do Microsoft 365, na navegação à esquerda, em **centros de administração**, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="9173c-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="9173c-141">No centro de administração do SharePoint, na navegação à esquerda, clique em **compartilhamento**.</span><span class="sxs-lookup"><span data-stu-id="9173c-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="9173c-142">Verifique se o compartilhamento externo do SharePoint está definido como **qualquer pessoa** ou **novo convidado existente**.</span><span class="sxs-lookup"><span data-stu-id="9173c-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="9173c-143">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-143">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="9173c-144">Configurações de link padrão de nível de organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="9173c-144">SharePoint organization level default link settings</span></span>

<span data-ttu-id="9173c-145">As configurações padrão de link de arquivo e pasta determinam qual opção de link é mostrada para o usuário por padrão ao compartilhar um arquivo ou uma pasta.</span><span class="sxs-lookup"><span data-stu-id="9173c-145">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="9173c-146">Os usuários podem alterar o tipo de link para uma das outras opções antes de compartilhar, se desejado.</span><span class="sxs-lookup"><span data-stu-id="9173c-146">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="9173c-147">Tenha em mente que essa configuração afeta todas as equipes e sites do SharePoint em sua organização.</span><span class="sxs-lookup"><span data-stu-id="9173c-147">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="9173c-148">Escolha o tipo de link selecionado por padrão quando os usuários compartilham arquivos e pastas:</span><span class="sxs-lookup"><span data-stu-id="9173c-148">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="9173c-149">**Qualquer pessoa com o link** -escolha essa opção se você espera compartilhar muitos arquivos e pastas com usuários anônimos.</span><span class="sxs-lookup"><span data-stu-id="9173c-149">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="9173c-150">Se você quiser permitir links de *qualquer pessoa* , mas estiver preocupado com o compartilhamento anônimo acidental, considere uma das outras opções como padrão.</span><span class="sxs-lookup"><span data-stu-id="9173c-150">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="9173c-151">Esse tipo de link só estará disponível se você tiver habilitado o compartilhamento de **qualquer pessoa** .</span><span class="sxs-lookup"><span data-stu-id="9173c-151">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="9173c-152">**Somente as pessoas da sua organização** -escolha esta opção se você espera que a maioria dos compartilhamento de arquivos e pastas seja com pessoas dentro da sua organização.</span><span class="sxs-lookup"><span data-stu-id="9173c-152">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="9173c-153">**Pessoas específicas** -considere essa opção se você espera que um grande volume de compartilhamento de arquivos e pastas com convidados.</span><span class="sxs-lookup"><span data-stu-id="9173c-153">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="9173c-154">Esse tipo de link funciona com convidados e exige a autenticação.</span><span class="sxs-lookup"><span data-stu-id="9173c-154">This type of link works with guests and requires them to authenticate.</span></span>
 
![Captura de tela das configurações de compartilhamento de arquivos e pastas da organização do SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="9173c-156">Para definir as configurações de link padrão de nível de organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="9173c-156">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="9173c-157">Navegue até a página de compartilhamento no centro de administração do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9173c-157">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="9173c-158">Em **links de arquivo e pasta**, selecione o link de compartilhamento padrão que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="9173c-158">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="9173c-159">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-159">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="9173c-160">Criar um site</span><span class="sxs-lookup"><span data-stu-id="9173c-160">Create a site</span></span>

<span data-ttu-id="9173c-161">A próxima etapa é criar o site que você planeja usar para colaborar com convidados.</span><span class="sxs-lookup"><span data-stu-id="9173c-161">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="9173c-162">Para criar um site</span><span class="sxs-lookup"><span data-stu-id="9173c-162">To create a site</span></span>
1. <span data-ttu-id="9173c-163">No centro de administração do SharePoint, em **sites**, clique em **sites ativos**.</span><span class="sxs-lookup"><span data-stu-id="9173c-163">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="9173c-164">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-164">Click **Create**.</span></span>
3. <span data-ttu-id="9173c-165">Clique em **site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="9173c-165">Click **Team site**.</span></span>
4. <span data-ttu-id="9173c-166">Digite um nome de site e insira um nome para o proprietário do grupo (proprietário do site).</span><span class="sxs-lookup"><span data-stu-id="9173c-166">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="9173c-167">Em **Configurações avançadas**, escolha se você deseja que este seja um site público ou privado.</span><span class="sxs-lookup"><span data-stu-id="9173c-167">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="9173c-168">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-168">Click **Next**.</span></span>
7. <span data-ttu-id="9173c-169">Clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="9173c-169">Click **Finish**.</span></span>

<span data-ttu-id="9173c-170">Vamos convidar os usuários mais tarde.</span><span class="sxs-lookup"><span data-stu-id="9173c-170">We'll invite users later.</span></span> <span data-ttu-id="9173c-171">Em seguida, é importante verificar as configurações de compartilhamento no nível do site para este site.</span><span class="sxs-lookup"><span data-stu-id="9173c-171">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="9173c-172">Configurações de compartilhamento no nível do site do SharePoint</span><span class="sxs-lookup"><span data-stu-id="9173c-172">SharePoint site level sharing settings</span></span>

<span data-ttu-id="9173c-173">Verifique as configurações de compartilhamento no nível do site para garantir que elas permitam o tipo de acesso que você deseja para este site.</span><span class="sxs-lookup"><span data-stu-id="9173c-173">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="9173c-174">Por exemplo, se você definir as configurações de nível de organização como **qualquer pessoa**, mas quiser que todos os convidados autentiquem esse site, verifique se as configurações de compartilhamento no nível do site estão definidas para **convidados novos e existentes**.</span><span class="sxs-lookup"><span data-stu-id="9173c-174">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="9173c-175">Observe que o site não pode ser compartilhado com usuários anônimos (configuração de**qualquer pessoa** ), mas arquivos e pastas individuais podem.</span><span class="sxs-lookup"><span data-stu-id="9173c-175">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Captura de tela das configurações de compartilhamento externo do site do SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="9173c-177">Para definir configurações de compartilhamento no nível do site</span><span class="sxs-lookup"><span data-stu-id="9173c-177">To set site-level sharing settings</span></span>
1. <span data-ttu-id="9173c-178">No centro de administração do SharePoint, na navegação à esquerda, expanda **sites** e clique em **sites ativos**.</span><span class="sxs-lookup"><span data-stu-id="9173c-178">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="9173c-179">Selecione o site que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="9173c-179">Select the site that you just created.</span></span>
3. <span data-ttu-id="9173c-180">Na faixa de opções, clique em **compartilhamento**.</span><span class="sxs-lookup"><span data-stu-id="9173c-180">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="9173c-181">Verifique se o compartilhamento está definido como **qualquer pessoa** ou **convidado novo e existente**.</span><span class="sxs-lookup"><span data-stu-id="9173c-181">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="9173c-182">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-182">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="9173c-183">Convidar usuários</span><span class="sxs-lookup"><span data-stu-id="9173c-183">Invite users</span></span>

<span data-ttu-id="9173c-184">As configurações de compartilhamento de convidados agora estão configuradas para que você possa começar a adicionar usuários internos e convidados ao seu site.</span><span class="sxs-lookup"><span data-stu-id="9173c-184">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="9173c-185">O acesso ao site é controlado pelo grupo associado do Office 365, portanto, vamos adicionar usuários lá.</span><span class="sxs-lookup"><span data-stu-id="9173c-185">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="9173c-186">Para convidar usuários internos para um grupo</span><span class="sxs-lookup"><span data-stu-id="9173c-186">To invite internal users to a group</span></span>
1. <span data-ttu-id="9173c-187">Navegue até o site em que você deseja adicionar usuários.</span><span class="sxs-lookup"><span data-stu-id="9173c-187">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="9173c-188">Clique em **Membros** no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="9173c-188">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="9173c-189">Clique em **Adicionar membros**.</span><span class="sxs-lookup"><span data-stu-id="9173c-189">Click **Add members**.</span></span>
4. <span data-ttu-id="9173c-190">Digite os nomes ou endereços de email dos usuários que você deseja convidar para o site e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-190">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="9173c-191">Os usuários convidados não podem ser adicionados do site.</span><span class="sxs-lookup"><span data-stu-id="9173c-191">Guest users can't be added from the site.</span></span> <span data-ttu-id="9173c-192">Você precisa adicioná-los usando o Outlook na Web.</span><span class="sxs-lookup"><span data-stu-id="9173c-192">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="9173c-193">Para convidar convidados para um site</span><span class="sxs-lookup"><span data-stu-id="9173c-193">To invite guests to a site</span></span>
1. <span data-ttu-id="9173c-194">No Outlook na Web, em **grupos**, clique no grupo em que você deseja adicionar membros.</span><span class="sxs-lookup"><span data-stu-id="9173c-194">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="9173c-195">Abra o cartão de visita do grupo e, em **mais opções** (...), clique em **adicionar membros**.</span><span class="sxs-lookup"><span data-stu-id="9173c-195">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="9173c-196">Digite os endereços de email dos convidados que você deseja convidar e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-196">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="9173c-197">Clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="9173c-197">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="9173c-198">Confira também</span><span class="sxs-lookup"><span data-stu-id="9173c-198">See Also</span></span>
