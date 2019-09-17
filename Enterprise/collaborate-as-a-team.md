---
title: Colaborar com convidados em uma equipe
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Saiba como colaborar com convidados no Microsoft Teams.
ms.openlocfilehash: 9a169e33a9cbd8f079966443bd3d830aa79f4971
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992410"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="3fa60-103">Colaborar com convidados em uma equipe</span><span class="sxs-lookup"><span data-stu-id="3fa60-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="3fa60-104">Se você precisar colaborar com convidados entre documentos, tarefas e conversas, recomendamos o uso do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3fa60-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="3fa60-105">O Microsoft Teams fornece todos os recursos de colaboração disponíveis no Office e no SharePoint com chat persistente e um conjunto personalizável e extensível de ferramentas de colaboração em uma experiência de usuário unificada.</span><span class="sxs-lookup"><span data-stu-id="3fa60-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="3fa60-106">Neste artigo, veremos as etapas de configuração do 365 da Microsoft necessárias para configurar uma equipe para colaboração com convidados.</span><span class="sxs-lookup"><span data-stu-id="3fa60-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="3fa60-107">Configurações de relações organizacionais do Azure</span><span class="sxs-lookup"><span data-stu-id="3fa60-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="3fa60-108">O compartilhamento no Microsoft 365 é regido no seu nível mais alto pelas configurações de relações organizacionais no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3fa60-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="3fa60-109">Se o compartilhamento de convidados estiver desabilitado ou restrito no Azure AD, isso substituirá as configurações de compartilhamento que você configurar no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3fa60-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="3fa60-110">Verifique as configurações de relações organizacionais para garantir que o compartilhamento com convidados não seja bloqueado.</span><span class="sxs-lookup"><span data-stu-id="3fa60-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Captura de tela da página de configurações de relações organizacionais do Active Directory do Azure](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="3fa60-112">Para definir as configurações de relação organizacional</span><span class="sxs-lookup"><span data-stu-id="3fa60-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="3fa60-113">Faça logon no Microsoft Azure em [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="3fa60-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="3fa60-114">Na navegação à esquerda, clique em **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="3fa60-115">No painel **visão geral** , clique em **relações organizacionais**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="3fa60-116">No painel **relações organizacionais** , clique em **configurações**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="3fa60-117">Certifique-se de que **Administradores e usuários na função de convite de convidado podem convidar** e **os membros podem convidar** estão definidos como **Sim**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="3fa60-118">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="3fa60-119">Observe as configurações na seção **restrições de colaboração** .</span><span class="sxs-lookup"><span data-stu-id="3fa60-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="3fa60-120">Certifique-se de que os domínios dos convidados com os quais você deseja colaborar não estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="3fa60-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="3fa60-121">Configurações de acesso de convidados do teams</span><span class="sxs-lookup"><span data-stu-id="3fa60-121">Teams guest access settings</span></span>

<span data-ttu-id="3fa60-122">O Microsoft Teams tem uma opção de ativar/desativar mestre para acesso de convidados e uma variedade de configurações disponíveis para controlar o que os convidados podem fazer em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="3fa60-122">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="3fa60-123">A opção mestre **permite que o acesso de convidados no Microsoft Teams** seja **ativado** para que o acesso de convidados funcione no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3fa60-123">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="3fa60-124">Verifique se o acesso de convidados está habilitado no Teams e faça qualquer ajuste nas configurações de convidado com base nas suas necessidades de negócios.</span><span class="sxs-lookup"><span data-stu-id="3fa60-124">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="3fa60-125">Tenha em mente que essas configurações afetam todas as equipes.</span><span class="sxs-lookup"><span data-stu-id="3fa60-125">Keep in mind that these settings affect all teams.</span></span>

![Captura de tela do teams Guest Access toggle](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="3fa60-127">Para definir as configurações de acesso de convidados do teams</span><span class="sxs-lookup"><span data-stu-id="3fa60-127">To set Teams guest access settings</span></span>

1. <span data-ttu-id="3fa60-128">Faça logon no centro de administração do Microsoft 365 [https://admin.microsoft.com](https://admin.microsoft.com)em.</span><span class="sxs-lookup"><span data-stu-id="3fa60-128">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="3fa60-129">No painel de navegação à esquerda, clique em **Mostrar tudo**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-129">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="3fa60-130">Em **centros de administração**, clique em **equipes**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-130">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="3fa60-131">No centro de administração do Microsoft Teams, no painel de navegação à esquerda, expanda **configurações de toda a organização** e clique em **acesso de convidado**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-131">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="3fa60-132">Verifique se **permitir acesso de convidados no Teams** está definido como **ativado**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-132">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="3fa60-133">Faça as alterações desejadas nas configurações de convidado adicionais e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-133">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="3fa60-134">Pode levar até vinte e quatro horas para que a configuração de convidado do Microsoft Teams fique ativa após você ativá-la.</span><span class="sxs-lookup"><span data-stu-id="3fa60-134">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="3fa60-135">Configurações de convidado de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="3fa60-135">Office 365 Groups guest settings</span></span>

<span data-ttu-id="3fa60-136">O Microsoft Teams usa grupos do Office 365 para associação da equipe.</span><span class="sxs-lookup"><span data-stu-id="3fa60-136">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="3fa60-137">As configurações de convidado de grupos do Office 365 devem ser ativadas para que o acesso de convidados no Teams funcione.</span><span class="sxs-lookup"><span data-stu-id="3fa60-137">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Captura de tela das configurações de convidado do Office 365 groups no centro de administração do Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="3fa60-139">Para definir as configurações de convidado de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="3fa60-139">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="3fa60-140">No centro de administração do Microsoft 365, no painel de navegação à esquerda, expanda **configurações**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-140">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="3fa60-141">Clique em **serviços & suplementos**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-141">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="3fa60-142">Na lista, clique em **grupos do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-142">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="3fa60-143">Certifique-se de que o **grupo permitir Membros fora do seu conteúdo de grupo de acesso à organização** e **que os proprietários do grupo adicionem pessoas fora da sua organização a grupos de** seleção.</span><span class="sxs-lookup"><span data-stu-id="3fa60-143">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="3fa60-144">Se você tiver feito alterações, clique em **salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-144">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="3fa60-145">Configurações de compartilhamento de nível da organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="3fa60-145">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="3fa60-146">Para que os convidados tenham acesso aos arquivos no Teams, as configurações de compartilhamento no nível da organização do SharePoint devem permitir o compartilhamento com convidados.</span><span class="sxs-lookup"><span data-stu-id="3fa60-146">In order for guests to have access to files in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="3fa60-147">As configurações de nível de organização determinam quais configurações estão disponíveis para sites individuais, incluindo sites associados ao Teams.</span><span class="sxs-lookup"><span data-stu-id="3fa60-147">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="3fa60-148">As configurações do site não podem ser mais permissivas do que as configurações no nível da organização.</span><span class="sxs-lookup"><span data-stu-id="3fa60-148">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="3fa60-149">Se você quiser permitir o compartilhamento de arquivos e pastas com usuários anônimos, escolha **qualquer pessoa**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-149">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="3fa60-150">Se você quiser garantir que todos os convidados devem se autenticar, escolha **novos e existentes convidados**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-150">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="3fa60-151">Escolha a configuração mais permissiva que será necessária para qualquer site em sua organização.</span><span class="sxs-lookup"><span data-stu-id="3fa60-151">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Captura de tela das configurações de compartilhamento no nível da organização do SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="3fa60-153">Para definir as configurações de compartilhamento de nível da organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="3fa60-153">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="3fa60-154">No centro de administração do Microsoft 365, na navegação à esquerda, em **centros de administração**, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-154">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="3fa60-155">No centro de administração do SharePoint, na navegação à esquerda, clique em **compartilhamento**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-155">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="3fa60-156">Verifique se o compartilhamento externo do SharePoint está definido como **qualquer pessoa** ou **novo convidado existente**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-156">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="3fa60-157">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-157">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="3fa60-158">Configurações de link padrão de nível de organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="3fa60-158">SharePoint organization level default link settings</span></span>

<span data-ttu-id="3fa60-159">As configurações padrão de link de arquivo e pasta determinam qual opção de link é mostrada para o usuário por padrão ao compartilhar um arquivo ou uma pasta.</span><span class="sxs-lookup"><span data-stu-id="3fa60-159">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="3fa60-160">Os usuários podem alterar o tipo de link para uma das outras opções antes de compartilhar, se desejado.</span><span class="sxs-lookup"><span data-stu-id="3fa60-160">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="3fa60-161">Tenha em mente que essa configuração afeta todas as equipes e sites do SharePoint em sua organização.</span><span class="sxs-lookup"><span data-stu-id="3fa60-161">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="3fa60-162">Escolha o tipo de link selecionado por padrão quando os usuários compartilham arquivos e pastas:</span><span class="sxs-lookup"><span data-stu-id="3fa60-162">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="3fa60-163">**Qualquer pessoa com o link** -escolha essa opção se você espera compartilhar muitos arquivos e pastas com usuários anônimos.</span><span class="sxs-lookup"><span data-stu-id="3fa60-163">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="3fa60-164">Se você quiser permitir links de *qualquer pessoa* , mas estiver preocupado com o compartilhamento anônimo acidental, considere uma das outras opções como padrão.</span><span class="sxs-lookup"><span data-stu-id="3fa60-164">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="3fa60-165">Esse tipo de link só estará disponível se você tiver habilitado o compartilhamento de **qualquer pessoa** .</span><span class="sxs-lookup"><span data-stu-id="3fa60-165">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="3fa60-166">**Somente as pessoas da sua organização** -escolha esta opção se você espera que a maioria dos compartilhamento de arquivos e pastas seja com pessoas dentro da sua organização.</span><span class="sxs-lookup"><span data-stu-id="3fa60-166">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="3fa60-167">**Pessoas específicas** -considere essa opção se você espera que um grande volume de compartilhamento de arquivos e pastas com convidados.</span><span class="sxs-lookup"><span data-stu-id="3fa60-167">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="3fa60-168">Esse tipo de link funciona com convidados e exige a autenticação.</span><span class="sxs-lookup"><span data-stu-id="3fa60-168">This type of link works with guests and requires them to authenticate.</span></span>
 
![Captura de tela das configurações de compartilhamento de arquivos e pastas da organização do SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="3fa60-170">Para definir as configurações de link padrão de nível de organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="3fa60-170">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="3fa60-171">Navegue até a página de compartilhamento no centro de administração do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3fa60-171">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="3fa60-172">Em **links de arquivo e pasta**, selecione o link de compartilhamento padrão que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="3fa60-172">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="3fa60-173">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-173">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="3fa60-174">Criar uma equipe</span><span class="sxs-lookup"><span data-stu-id="3fa60-174">Create a team</span></span>

<span data-ttu-id="3fa60-175">A próxima etapa é criar a equipe que você planeja usar para colaborar com convidados.</span><span class="sxs-lookup"><span data-stu-id="3fa60-175">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="3fa60-176">Para criar uma equipe</span><span class="sxs-lookup"><span data-stu-id="3fa60-176">To create a team</span></span>
1. <span data-ttu-id="3fa60-177">No Teams, na guia **Teams** , clique em **ingressar ou criar uma equipe** na parte inferior do painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="3fa60-177">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="3fa60-178">Clique em **criar uma equipe**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-178">Click **Create a team**.</span></span>
3. <span data-ttu-id="3fa60-179">Clique em **criar uma equipe do zero**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-179">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="3fa60-180">Escolha **privado** ou **público**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-180">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="3fa60-181">Digite um nome e uma descrição para a equipe e, em seguida, clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-181">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="3fa60-182">Clique em **ignorar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-182">Click **Skip**.</span></span>

<span data-ttu-id="3fa60-183">Vamos convidar os usuários mais tarde.</span><span class="sxs-lookup"><span data-stu-id="3fa60-183">We'll invite users later.</span></span> <span data-ttu-id="3fa60-184">Em seguida, é importante verificar as configurações de compartilhamento no nível do site do SharePoint associado à equipe.</span><span class="sxs-lookup"><span data-stu-id="3fa60-184">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="3fa60-185">Configurações de compartilhamento no nível do site do SharePoint</span><span class="sxs-lookup"><span data-stu-id="3fa60-185">SharePoint site level sharing settings</span></span>

<span data-ttu-id="3fa60-186">Verifique as configurações de compartilhamento no nível do site para garantir que elas permitam o tipo de acesso que você deseja para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="3fa60-186">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="3fa60-187">Por exemplo, se você definir as configurações de nível de organização como **qualquer pessoa**, mas quiser que todos os convidados autentiquem essa equipe, verifique se as configurações de compartilhamento no nível do site estão definidas para **convidados novos e existentes**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-187">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![Captura de tela das configurações de compartilhamento externo do site do SharePoint](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="3fa60-189">Para definir configurações de compartilhamento no nível do site</span><span class="sxs-lookup"><span data-stu-id="3fa60-189">To set site-level sharing settings</span></span>
1. <span data-ttu-id="3fa60-190">No centro de administração do SharePoint, na navegação à esquerda, expanda **sites** e clique em **sites ativos**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-190">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="3fa60-191">Selecione o site para a equipe que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="3fa60-191">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="3fa60-192">Na faixa de opções, clique em **compartilhamento**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-192">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="3fa60-193">Verifique se o compartilhamento está definido como **qualquer pessoa** ou **convidado novo e existente**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-193">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="3fa60-194">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-194">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="3fa60-195">Convidar usuários</span><span class="sxs-lookup"><span data-stu-id="3fa60-195">Invite users</span></span>

<span data-ttu-id="3fa60-196">As configurações de compartilhamento de convidados agora estão configuradas para que você possa começar a adicionar usuários internos e convidados à sua equipe.</span><span class="sxs-lookup"><span data-stu-id="3fa60-196">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="3fa60-197">Para convidar usuários internos para uma equipe</span><span class="sxs-lookup"><span data-stu-id="3fa60-197">To invite internal users to a team</span></span>
1. <span data-ttu-id="3fa60-198">Na equipe, clique em **mais opções** (**\*\***) e, em seguida, clique em **Adicionar membro**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-198">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="3fa60-199">Digite o nome da pessoa que você deseja convidar.</span><span class="sxs-lookup"><span data-stu-id="3fa60-199">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="3fa60-200">Clique em **Adicionar**e, em seguida, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-200">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="3fa60-201">Para convidar convidados para uma equipe</span><span class="sxs-lookup"><span data-stu-id="3fa60-201">To invite guests to a team</span></span>
1. <span data-ttu-id="3fa60-202">Na equipe, clique em **mais opções** (**\*\***) e, em seguida, clique em **Adicionar membro**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-202">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="3fa60-203">Digite o endereço de email do convidado que você deseja convidar.</span><span class="sxs-lookup"><span data-stu-id="3fa60-203">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="3fa60-204">Clique em **Editar informações de convidado**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-204">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="3fa60-205">Digite o nome completo do convidado e clique na marca de seleção.</span><span class="sxs-lookup"><span data-stu-id="3fa60-205">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="3fa60-206">Clique em **Adicionar**e, em seguida, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="3fa60-206">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fa60-207">Confira também</span><span class="sxs-lookup"><span data-stu-id="3fa60-207">See Also</span></span>

