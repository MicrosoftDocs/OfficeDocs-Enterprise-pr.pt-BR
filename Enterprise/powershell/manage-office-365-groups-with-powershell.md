---
title: Gerenciar Grupos do Office 365 com o PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Saiba como realizar tarefas comuns de gerenciamento para grupos do Office 365 no Microsoft PowerShell.
ms.openlocfilehash: bab98ac641b03bd30ea8acbc8d4dacd55073f62f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841438"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="2ee52-103">Gerenciar Grupos do Office 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ee52-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="2ee52-104">*Última atualização 18 de abril de 2018*</span><span class="sxs-lookup"><span data-stu-id="2ee52-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="2ee52-105">Este artigo fornece as etapas para realizar tarefas comuns de gerenciamento para grupos no Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ee52-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="2ee52-106">Ele também lista os cmdlets do PowerShell para grupos.</span><span class="sxs-lookup"><span data-stu-id="2ee52-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="2ee52-107">Para obter informações sobre como gerenciar sites do SharePoint, confira [gerenciar sites do SharePoint online usando o PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="2ee52-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="2ee52-108">Link para suas diretrizes de uso de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="2ee52-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="2ee52-109"><a name="BK_LinkToGuideLines"> </a></span></span>

<span data-ttu-id="2ee52-110">Quando os usuários [criarem ou editarem um grupo no Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), você poderá mostrar um link para as diretrizes de uso da sua organização.</span><span class="sxs-lookup"><span data-stu-id="2ee52-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="2ee52-111">Por exemplo, se você precisar adicionar um prefixo ou sufixo específico a um nome de grupo.</span><span class="sxs-lookup"><span data-stu-id="2ee52-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="2ee52-112">Use o PowerShell do Azure Active Directory para apontar seus usuários para as diretrizes de uso da sua organização para grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-112">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span> <span data-ttu-id="2ee52-113">Confira os [cmdlets do Azure Active Directory para definir as configurações de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) e siga as etapas em **criar configurações no nível do diretório** para definir o hiperlink de diretriz de uso.</span><span class="sxs-lookup"><span data-stu-id="2ee52-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="2ee52-114">Depois de executar o cmdlet AAD, o usuário verá o link para suas diretrizes ao criar ou editar um grupo no Outlook.</span><span class="sxs-lookup"><span data-stu-id="2ee52-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Criar um novo grupo com o link de diretrizes de uso](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Clique em diretrizes de uso de grupo para ver as diretrizes de grupos do Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="2ee52-117">Permitir que os usuários enviem como o grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="2ee52-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="2ee52-118"><a name="BK_LinkToGuideLines"> </a></span></span>
  
<span data-ttu-id="2ee52-119">Se você deseja habilitar seus grupos do Office 365 para "enviar como", use os cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) e [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) para configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="2ee52-119">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="2ee52-120">Após habilitar essa configuração, os usuários do grupo do Office 365 podem usar o Outlook ou o Outlook na Web para enviar e responder a email como o grupo do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-120">Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group.</span></span> <span data-ttu-id="2ee52-121">Os usuários podem ir para o grupo, criar um novo email e alterar o campo "enviar como" para o endereço de email do grupo.</span><span class="sxs-lookup"><span data-stu-id="2ee52-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="2ee52-122">([Você também pode fazer isso no centro de administração do Exchange](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span><span class="sxs-lookup"><span data-stu-id="2ee52-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="2ee52-123">Use o script a seguir, substituindo \* \<\> GroupAlias\* com o alias do grupo que você deseja atualizar e \* \<useralias\> \* com o alias do usuário a quem você deseja conceder permssions.</span><span class="sxs-lookup"><span data-stu-id="2ee52-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions.</span></span> <span data-ttu-id="2ee52-124">[Conectar-se ao PowerShell do Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para executar esse script.</span><span class="sxs-lookup"><span data-stu-id="2ee52-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="2ee52-125">Depois que o cmdlet é executado, os usuários podem acessar o Outlook ou o Outlook na Web para enviar como o grupo, adicionando o endereço de email do grupo ao campo **de** .</span><span class="sxs-lookup"><span data-stu-id="2ee52-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="2ee52-126">Criar classificações para grupos do Office em sua organização</span><span class="sxs-lookup"><span data-stu-id="2ee52-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="2ee52-127">Você pode criar classificações que os usuários em sua organização podem definir quando criarem um grupo do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-127">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="2ee52-128">Por exemplo, você pode permitir que os usuários definam "Standard", "Secret" e "Top Secret" em grupos criados.</span><span class="sxs-lookup"><span data-stu-id="2ee52-128">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="2ee52-129">As classificações de grupo não são definidas por padrão e você precisa criá-las para que os usuários a definam.</span><span class="sxs-lookup"><span data-stu-id="2ee52-129">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="2ee52-130">Use o PowerShell do Azure Active Directory para apontar seus usuários para as diretrizes de uso da sua organização para grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-130">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="2ee52-131">Confira os [cmdlets do Azure Active Directory para definir as configurações de grupo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) e siga as etapas em **criar configurações no nível do diretório** para definir a classificação dos grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="2ee52-132">Para associar uma descrição a cada classificação, você pode usar o atributo de configurações *ClassificationDescriptions* para definir.</span><span class="sxs-lookup"><span data-stu-id="2ee52-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="2ee52-133">em que a classificação corresponde às cadeias de caracteres na classificação.</span><span class="sxs-lookup"><span data-stu-id="2ee52-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="2ee52-134">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2ee52-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="2ee52-135">Depois de executar o cmdlet acima do Active Directory do Azure para definir sua classificação, execute o cmdlet [set-unificado](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) , se quiser definir a classificação de um grupo específico.</span><span class="sxs-lookup"><span data-stu-id="2ee52-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="2ee52-136">Ou criar um novo grupo com uma classificação.</span><span class="sxs-lookup"><span data-stu-id="2ee52-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="2ee52-137">Confira [usando o PowerShell com o Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) e [Conecte-se ao PowerShell do Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para obter mais detalhes sobre como usar o PowerShell do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="2ee52-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="2ee52-138">Depois que essas configurações forem habilitadas, o proprietário do grupo poderá escolher uma classificação no menu suspenso no Outlook na Web e no Outlook e salvá-la na página **Editar** grupo.</span><span class="sxs-lookup"><span data-stu-id="2ee52-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Escolha a classificação de grupo do Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="2ee52-140">Ocultar grupos do Office 365 da GAL</span><span class="sxs-lookup"><span data-stu-id="2ee52-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="2ee52-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2ee52-141"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="2ee52-142">Você pode especificar se um grupo do Office 365 aparece na lista de endereços global (GAL) e em outras listas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="2ee52-142">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="2ee52-143">Por exemplo, se você tiver um grupo de departamento jurídico que não deseja exibir na lista de endereços, você pode impedir que esse grupo apareça na GAL.</span><span class="sxs-lookup"><span data-stu-id="2ee52-143">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="2ee52-144">Execute o cmdlet Set-Unified Group para ocultar o grupo da lista de endereços da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2ee52-144">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="2ee52-145">Permitir que somente usuários internos enviem mensagens para o grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="2ee52-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2ee52-146"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="2ee52-147">Se não quiser que os usuários de outra organização enviem emails para um grupo do Office 365, você poderá alterar as configurações desse grupo.</span><span class="sxs-lookup"><span data-stu-id="2ee52-147">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="2ee52-148">Ele permitirá que apenas usuários internos enviem um email para o seu grupo.</span><span class="sxs-lookup"><span data-stu-id="2ee52-148">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="2ee52-149">Se o usuário externo tentar enviar uma mensagem para esse grupo, ele será rejeitado.</span><span class="sxs-lookup"><span data-stu-id="2ee52-149">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="2ee52-150">Execute o cmdlet Set-unificado para atualizar essa configuração, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2ee52-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="2ee52-151">Adicionar dicas de correio aos grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="2ee52-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2ee52-152"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="2ee52-153">Sempre que um remetente tenta enviar um email a um grupo do Office 365, uma dica de email pode ser exibida para eles.</span><span class="sxs-lookup"><span data-stu-id="2ee52-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="2ee52-154">Execute o cmdlet Set-Unified Group para adicionar uma dica de tela ao grupo:</span><span class="sxs-lookup"><span data-stu-id="2ee52-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="2ee52-155">Juntamente com as dicas de dicas, você também pode definir MailTipTranslations, que especifica idiomas adicionais para a dica de a.</span><span class="sxs-lookup"><span data-stu-id="2ee52-155">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="2ee52-156">Suponha que você deseja ter a tradução para espanhol e, em seguida, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2ee52-156">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="2ee52-157">Alterar o nome de exibição do grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="2ee52-158">Nome para exibição especifica o nome do grupo do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-158">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="2ee52-159">Você pode ver esse nome no seu centro de administração do Exchange ou no portal de administração do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-159">You can see this name in your exchange admin center or Office 365 admin portal.</span></span> <span data-ttu-id="2ee52-160">Você pode editar o nome de exibição do grupo ou atribuir um nome para exibição a um grupo existente do Office 365 executando o comando Set-Unified Group:</span><span class="sxs-lookup"><span data-stu-id="2ee52-160">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="2ee52-161">Alterar a configuração padrão dos grupos do Office 365 para o Outlook para público ou privado</span><span class="sxs-lookup"><span data-stu-id="2ee52-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="2ee52-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2ee52-162"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="2ee52-163">Os grupos do Office 365 no Outlook são criados como particulares por padrão.</span><span class="sxs-lookup"><span data-stu-id="2ee52-163">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="2ee52-164">Se sua organização deseja que os grupos do Office 365 sejam criados como públicos por padrão (ou de volta para privado), use esta sintaxe de cmdlet do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="2ee52-164">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="2ee52-165">Para definir como particular:</span><span class="sxs-lookup"><span data-stu-id="2ee52-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="2ee52-166">Para verificar a configuração:</span><span class="sxs-lookup"><span data-stu-id="2ee52-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="2ee52-167">Para saber mais, confira [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) e [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="2ee52-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="2ee52-168">Cmdlets de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="2ee52-169">Os cmdlets a seguir podem ser usados com grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="2ee52-170">**Nome do cmdlet**</span><span class="sxs-lookup"><span data-stu-id="2ee52-170">**Cmdlet name**</span></span>|<span data-ttu-id="2ee52-171">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ee52-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="2ee52-172">Obter-Unificação de um</span><span class="sxs-lookup"><span data-stu-id="2ee52-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="2ee52-173">Use este cmdlet para pesquisar grupos existentes do Office 365 e para exibir as propriedades do objeto Group</span><span class="sxs-lookup"><span data-stu-id="2ee52-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="2ee52-174">Conjunto-unificado</span><span class="sxs-lookup"><span data-stu-id="2ee52-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="2ee52-175">Atualizar as propriedades de um grupo específico do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2ee52-176">Novo-unificado</span><span class="sxs-lookup"><span data-stu-id="2ee52-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="2ee52-177">Criar um novo grupo do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2ee52-177">Create a new Office 365 group.</span></span> <span data-ttu-id="2ee52-178">Este cmdlet fornece um conjunto mínimo de parâmetros, para definir valores para propriedades estendidas use set-Unified Group depois de criar o novo grupo</span><span class="sxs-lookup"><span data-stu-id="2ee52-178">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="2ee52-179">Remover-unificado</span><span class="sxs-lookup"><span data-stu-id="2ee52-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="2ee52-180">Excluir um grupo existente do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2ee52-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="2ee52-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="2ee52-182">Recuperar informações de associação e de proprietário de um grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2ee52-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="2ee52-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="2ee52-184">Adicionar centenas ou milhares de usuários, ou novos proprietários, a um grupo existente do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2ee52-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="2ee52-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="2ee52-186">Remover proprietários e membros de um grupo existente do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2ee52-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="2ee52-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="2ee52-188">Usado para exibir informações sobre a foto do usuário associada a uma conta.</span><span class="sxs-lookup"><span data-stu-id="2ee52-188">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="2ee52-189">As fotos do usuário são armazenadas no Active Directory</span><span class="sxs-lookup"><span data-stu-id="2ee52-189">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="2ee52-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="2ee52-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="2ee52-191">Usado para associar uma foto de usuário a uma conta.</span><span class="sxs-lookup"><span data-stu-id="2ee52-191">Used to associate a user photo with an account.</span></span> <span data-ttu-id="2ee52-192">As fotos do usuário são armazenadas no Active Directory</span><span class="sxs-lookup"><span data-stu-id="2ee52-192">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="2ee52-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="2ee52-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="2ee52-194">Remover a foto de um grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="2ee52-195">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="2ee52-195">Related topics</span></span>

[<span data-ttu-id="2ee52-196">Atualizar listas de distribuição para grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="2ee52-197">Gerenciar quem pode criar grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="2ee52-198">Gerenciar o acesso de convidados aos Grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="2ee52-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="2ee52-199">Alterar a associação de grupo estático para dinâmico no</span><span class="sxs-lookup"><span data-stu-id="2ee52-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
