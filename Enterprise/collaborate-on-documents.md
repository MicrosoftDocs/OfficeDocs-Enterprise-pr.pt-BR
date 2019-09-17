---
title: Colaborar com convidados em um documento
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Saiba como colaborar com convidados em um documento no SharePoint e no OneDrive.
ms.openlocfilehash: c0c74f2457e9b25b37355c58ed18f120261e3364
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992400"
---
# <a name="collaborate-with-guests-on-a-document"></a><span data-ttu-id="e18cc-103">Colaborar com convidados em um documento</span><span class="sxs-lookup"><span data-stu-id="e18cc-103">Collaborate with guests on a document</span></span>

<span data-ttu-id="e18cc-104">Se você precisar colaborar com convidados em documentos do SharePoint ou do OneDrive, você pode enviar um link de compartilhamento para o documento.</span><span class="sxs-lookup"><span data-stu-id="e18cc-104">If you need to collaborate with guests on documents in SharePoint or OneDrive, you can send them a sharing link to the document.</span></span> <span data-ttu-id="e18cc-105">Neste artigo, veremos as etapas de configuração do Microsoft 365 necessárias para configurar links de compartilhamento para o SharePoint e o OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e18cc-105">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up sharing links for SharePoint and OneDrive.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="e18cc-106">Configurações de relações organizacionais do Azure</span><span class="sxs-lookup"><span data-stu-id="e18cc-106">Azure Organizational relationships settings</span></span>

<span data-ttu-id="e18cc-107">O compartilhamento no Microsoft 365 é regido no seu nível mais alto pelas configurações de relações organizacionais no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e18cc-107">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="e18cc-108">Se o compartilhamento de convidados estiver desabilitado ou restrito no Azure AD, isso substituirá as configurações de compartilhamento que você configurar no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e18cc-108">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="e18cc-109">Verifique as configurações de relações organizacionais para garantir que o compartilhamento com convidados não seja bloqueado.</span><span class="sxs-lookup"><span data-stu-id="e18cc-109">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Captura de tela da página de configurações de relações organizacionais do Active Directory do Azure](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="e18cc-111">Para definir as configurações de relação organizacional</span><span class="sxs-lookup"><span data-stu-id="e18cc-111">To set organizational relationship settings</span></span>

1. <span data-ttu-id="e18cc-112">Faça logon no Microsoft Azure em [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="e18cc-112">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="e18cc-113">Na navegação à esquerda, clique em **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-113">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="e18cc-114">No painel **visão geral** , clique em **relações organizacionais**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-114">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="e18cc-115">No painel **relações organizacionais** , clique em **configurações**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-115">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="e18cc-116">Certifique-se de que **Administradores e usuários na função de convite de convidado podem convidar** e **os membros podem convidar** estão definidos como **Sim**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-116">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="e18cc-117">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-117">If you made changes, click **Save**.</span></span>

<span data-ttu-id="e18cc-118">Observe as configurações na seção **restrições de colaboração** .</span><span class="sxs-lookup"><span data-stu-id="e18cc-118">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="e18cc-119">Certifique-se de que os domínios dos convidados com os quais você deseja colaborar não estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="e18cc-119">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="e18cc-120">Configurações de compartilhamento de nível da organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="e18cc-120">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="e18cc-121">Para que os convidados tenham acesso a um documento no SharePoint ou no OneDrive, as configurações de compartilhamento no nível da organização do SharePoint e do OneDrive devem permitir o compartilhamento com convidados.</span><span class="sxs-lookup"><span data-stu-id="e18cc-121">In order for guests to have access to a document in SharePoint or OneDrive, the SharePoint and OneDrive organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="e18cc-122">As configurações de nível de organização para o SharePoint determinam as configurações disponíveis para sites individuais do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e18cc-122">The organization-level settings for SharePoint determine what settings are available for individual SharePoint sites.</span></span> <span data-ttu-id="e18cc-123">As configurações do site não podem ser mais permissivas do que as configurações no nível da organização.</span><span class="sxs-lookup"><span data-stu-id="e18cc-123">Site settings cannot be more permissive than the organization-level settings.</span></span> <span data-ttu-id="e18cc-124">A configuração de nível de organização para o OneDrive determina o nível de compartilhamento disponível nas bibliotecas do OneDrive dos usuários.</span><span class="sxs-lookup"><span data-stu-id="e18cc-124">The organization-level setting for OneDrive determines what level of sharing is available in users' OneDrive libraries.</span></span>

<span data-ttu-id="e18cc-125">Para o SharePiont e o OneDrive, se você quiser permitir o compartilhamento de arquivos e pastas com usuários anônimos, escolha **qualquer pessoa**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-125">For SharePiont and OneDrive, if you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="e18cc-126">Se você quiser garantir que todos os convidados devem se autenticar, escolha **novos e existentes convidados**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-126">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> 

<span data-ttu-id="e18cc-127">Para o SharePoint, escolha a configuração mais permissiva que será necessária para qualquer site em sua organização.</span><span class="sxs-lookup"><span data-stu-id="e18cc-127">For SharePoint, choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Captura de tela das configurações de compartilhamento no nível da organização do SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="e18cc-129">Para definir as configurações de compartilhamento de nível da organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="e18cc-129">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="e18cc-130">No centro de administração do Microsoft 365, na navegação à esquerda, em **centros de administração**, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-130">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="e18cc-131">No centro de administração do SharePoint, na navegação à esquerda, clique em **compartilhamento**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-131">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="e18cc-132">Certifique-se de que o compartilhamento externo do SharePoint ou do OneDrive está definido como **qualquer pessoa** ou **convidado novo e existente**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-132">Ensure that external sharing for SharePoint or OneDrive is set to **Anyone** or **New and existing guests**.</span></span> <span data-ttu-id="e18cc-133">(Observe que a configuração do OneDrive não pode ser mais permissiva do que a configuração do SharePoint.)</span><span class="sxs-lookup"><span data-stu-id="e18cc-133">(Note that the OneDrive setting cannot be more permissive than the SharePoint setting.)</span></span>
4. <span data-ttu-id="e18cc-134">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-134">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="e18cc-135">Configurações de link padrão de nível de organização do SharePoint</span><span class="sxs-lookup"><span data-stu-id="e18cc-135">SharePoint organization level default link settings</span></span>

<span data-ttu-id="e18cc-136">As configurações padrão de link de arquivo e pasta determinam qual opção de link é mostrada para o usuário por padrão ao compartilhar um arquivo ou uma pasta.</span><span class="sxs-lookup"><span data-stu-id="e18cc-136">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="e18cc-137">Os usuários podem alterar o tipo de link para uma das outras opções antes de compartilhar, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e18cc-137">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="e18cc-138">Tenha em mente que essa configuração afeta os sites do SharePoint em sua organização, bem como o OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e18cc-138">Keep in mind that this setting affects SharePoint sites in your organization, as well as OneDrive.</span></span>

<span data-ttu-id="e18cc-139">Escolha o tipo de link selecionado por padrão quando os usuários compartilham arquivos e pastas:</span><span class="sxs-lookup"><span data-stu-id="e18cc-139">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="e18cc-140">**Qualquer pessoa com o link** -escolha essa opção se você espera compartilhar muitos arquivos e pastas com usuários anônimos.</span><span class="sxs-lookup"><span data-stu-id="e18cc-140">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="e18cc-141">Se você quiser permitir links de *qualquer pessoa* , mas estiver preocupado com o compartilhamento anônimo acidental, considere uma das outras opções como padrão.</span><span class="sxs-lookup"><span data-stu-id="e18cc-141">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="e18cc-142">Esse tipo de link só estará disponível se você tiver habilitado o compartilhamento de **qualquer pessoa** .</span><span class="sxs-lookup"><span data-stu-id="e18cc-142">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="e18cc-143">**Somente as pessoas da sua organização** -escolha esta opção se você espera que a maioria dos compartilhamento de arquivos e pastas seja com pessoas dentro da sua organização.</span><span class="sxs-lookup"><span data-stu-id="e18cc-143">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="e18cc-144">**Pessoas específicas** -considere essa opção se você espera que um grande volume de compartilhamento de arquivos e pastas com convidados.</span><span class="sxs-lookup"><span data-stu-id="e18cc-144">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="e18cc-145">Esse tipo de link funciona com convidados e exige a autenticação.</span><span class="sxs-lookup"><span data-stu-id="e18cc-145">This type of link works with guests and requires them to authenticate.</span></span>
 
![Captura de tela das configurações de compartilhamento de arquivos e pastas da organização do SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="e18cc-147">Para definir as configurações de link padrão de nível de organização do OneDrive e SharePoint</span><span class="sxs-lookup"><span data-stu-id="e18cc-147">To set the SharePoint and OneDrive organization level default link settings</span></span>

1. <span data-ttu-id="e18cc-148">Navegue até a página de compartilhamento no centro de administração do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e18cc-148">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="e18cc-149">Em **links de arquivo e pasta**, selecione o link de compartilhamento padrão que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="e18cc-149">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="e18cc-150">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-150">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="e18cc-151">Configurações de compartilhamento no nível do site do SharePoint</span><span class="sxs-lookup"><span data-stu-id="e18cc-151">SharePoint site level sharing settings</span></span>

<span data-ttu-id="e18cc-152">Se você estiver compartilhando arquivos e fodlers que estão em um site do SharePoint, também precisará verificar as configurações de compartilhamento no nível do site para esse site.</span><span class="sxs-lookup"><span data-stu-id="e18cc-152">If you're sharing files and fodlers that are in a SharePoint site, you also need to check the site-level sharing settings for that site.</span></span>

![Captura de tela das configurações de compartilhamento externo do site do SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="e18cc-154">Para definir configurações de compartilhamento no nível do site</span><span class="sxs-lookup"><span data-stu-id="e18cc-154">To set site-level sharing settings</span></span>
1. <span data-ttu-id="e18cc-155">No centro de administração do SharePoint, na navegação à esquerda, expanda **sites** e clique em **sites ativos**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-155">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="e18cc-156">Selecione o site que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="e18cc-156">Select the site that you just created.</span></span>
3. <span data-ttu-id="e18cc-157">Na faixa de opções, clique em **compartilhamento**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-157">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="e18cc-158">Verifique se o compartilhamento está definido como **qualquer pessoa** ou **convidado novo e existente**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-158">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="e18cc-159">Se você tiver feito alterações, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="e18cc-159">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="e18cc-160">Convidar usuários</span><span class="sxs-lookup"><span data-stu-id="e18cc-160">Invite users</span></span>

<span data-ttu-id="e18cc-161">As configurações de compartilhamento de convidados agora estão configuradas, portanto, os usuários agora podem compartilhar arquivos e pastas com convidados.</span><span class="sxs-lookup"><span data-stu-id="e18cc-161">Guest sharing settings are now configured, so users can now share files and folders with guests.</span></span> <span data-ttu-id="e18cc-162">Consulte [compartilhar arquivos e pastas do onedrive](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) e [compartilhar arquivos ou pastas do SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e18cc-162">See [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) and [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="e18cc-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="e18cc-163">See Also</span></span>
