---
title: Gerenciar Grupos do Office 365 com o PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760053"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="790a7-103">Gerenciar Grupos do Office 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="790a7-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="790a7-104">*Última atualizados 18 de abril de 2018*</span><span class="sxs-lookup"><span data-stu-id="790a7-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="790a7-p101">Este artigo fornece as etapas para realizar tarefas comuns de gerenciamento para grupos no Microsoft PowerShell. Ela também lista os cmdlets do PowerShell para grupos. Para informações sobre como gerenciar sites do SharePoint, consulte [Gerenciar o SharePoint Online sites usando o PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="790a7-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="790a7-108">Link para a suas diretrizes de uso de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="790a7-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="790a7-109"></span></span>

<span data-ttu-id="790a7-p102">Quando os usuários [criar ou editar um grupo no Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), você poderá mostrar um link para as diretrizes de uso da sua organização. Por exemplo, se você exige um prefixo específico ou sufixo a ser adicionado a um nome de grupo.</span><span class="sxs-lookup"><span data-stu-id="790a7-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="790a7-p103">Use o Azure Active Directory PowerShell para direcionar seus usuários às diretrizes de uso da sua organização para grupos do Office 365. Check-out de [cmdlets do Windows Azure Active Directory para definir as configurações de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) e siga as etapas na **criar configurações no nível do diretório** para definir o hiperlink de diretriz de uso. Uma vez você executar o cmdlet AAD, usuário verá o link para a suas diretrizes quando eles cria ou edita um grupo no Outlook.</span><span class="sxs-lookup"><span data-stu-id="790a7-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Criar um novo grupo com o link de diretrizes de uso](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Clique em diretrizes de uso de grupo para ver suas organizações diretrizes de grupos do Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="790a7-117">Permitir que os usuários enviar como o grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="790a7-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="790a7-118"></span></span>
  
<span data-ttu-id="790a7-p104">Se você deseja habilitar os grupos do Office 365 para "Enviar como", use o [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) e os cmdlets [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) essa configuração. Depois que você habilitar essa configuração, os usuários de grupo do Office 365 podem usar o Outlook ou o Outlook na web para enviar e responder para emails como o grupo do Office 365. Os usuários podem ir ao grupo, crie um novo email e altere o campo "Enviar como" para o endereço de email do grupo.</span><span class="sxs-lookup"><span data-stu-id="790a7-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="790a7-122">([Você também pode fazer isso no Centro de administração do Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="790a7-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="790a7-p105">Use o seguinte script, substituindo \* \<GroupAlias\> \* com o alias do grupo que você deseja atualizar, e \* \<UserAlias\> \* com o alias do usuário a quem você deseja conceder permissões. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) executar esse script.</span><span class="sxs-lookup"><span data-stu-id="790a7-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="790a7-125">Depois que o cmdlet é executado, os usuários podem ir para o Outlook ou do Outlook na web para ser enviada como o grupo, adicionando o endereço de email do grupo no campo **de** .</span><span class="sxs-lookup"><span data-stu-id="790a7-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="790a7-126">Criar classificações para grupos do Office em sua organização</span><span class="sxs-lookup"><span data-stu-id="790a7-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="790a7-p106">Você pode criar classificações que os usuários em sua organização podem ser definidas quando eles criam um grupo do Office 365. Por exemplo, você pode permitir que os usuários definam "Standard", "Secret" e "Altamente secretos" nos grupos que eles criam. Classificações de grupo não são definidas por padrão, e você precisa criá-lo na ordem para seus usuários para defini-la. Use o Azure Active Directory PowerShell para direcionar seus usuários às diretrizes de uso da sua organização para grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="790a7-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="790a7-131">Check-out de [cmdlets do Windows Azure Active Directory para definir as configurações de grupo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) e siga as etapas na **criar configurações no nível do diretório** para definir a classificação de para grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="790a7-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="790a7-132">Para associar uma descrição de cada tabela de classificação que você pode usar as configurações *ClassificationDescriptions* para definir o atributo.</span><span class="sxs-lookup"><span data-stu-id="790a7-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="790a7-133">onde classificação corresponde a ClassificationList as sequências de caracteres.</span><span class="sxs-lookup"><span data-stu-id="790a7-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="790a7-134">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="790a7-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="790a7-135">Após executar o cmdlet acima do Azure Active Directory para definir sua classificação, execute o cmdlet [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) se você deseja definir a classificação de um grupo específico.</span><span class="sxs-lookup"><span data-stu-id="790a7-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="790a7-136">Ou crie um novo grupo com uma classificação.</span><span class="sxs-lookup"><span data-stu-id="790a7-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="790a7-137">Confira [Usando o PowerShell com o Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) e [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para obter mais detalhes sobre como usar o PowerShell do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="790a7-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="790a7-138">Depois que essas configurações estão habilitadas, o proprietário do grupo será capaz de escolher uma classificação na lista suspensa menu no Outlook na Web e Outlook e salvá-lo da página **Editar** grupo.</span><span class="sxs-lookup"><span data-stu-id="790a7-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Escolha a classificação de grupo do Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="790a7-140">Ocultar grupos do Office 365 da GAL</span><span class="sxs-lookup"><span data-stu-id="790a7-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="790a7-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="790a7-141"></span></span>

<span data-ttu-id="790a7-p107">Você pode especificar se um grupo do Office 365 é exibida na lista de endereços global (GAL) e outras listas em sua organização. Por exemplo, se você tiver um grupo de departamento jurídico que você não deseja que seja mostrada na lista de endereços, você poderá interromper esse grupo apareçam na GAL. Execute o cmdlet Set-Unified grupo para ocultar o grupo da lista de endereços semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="790a7-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="790a7-145">Permitir que somente usuários internos enviar a mensagem ao grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="790a7-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="790a7-146"></span></span>

<span data-ttu-id="790a7-p108">Se você não desejar que os usuários de outra organização para enviar email a um grupo do Office 365, você poderá alterar as configurações para esse grupo. Ele permitirá que apenas usuários internos enviar um email para seu grupo. Se o usuário externo tente enviar a mensagem a esse grupo que serão rejeitadas.</span><span class="sxs-lookup"><span data-stu-id="790a7-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="790a7-150">Execute o cmdlet Set-UnifiedGroup para atualizar esta configuração, semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="790a7-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="790a7-151">Adicionar dicas de email aos grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="790a7-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="790a7-152"></span></span>

<span data-ttu-id="790a7-153">Sempre que um remetente tenta enviar um email a um grupo do Office 365, uma dica de email pode ser mostrada para acessá-los.</span><span class="sxs-lookup"><span data-stu-id="790a7-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="790a7-154">Execute o cmdlet grupo Set-Unified para adicionar uma dica de email para o grupo:</span><span class="sxs-lookup"><span data-stu-id="790a7-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="790a7-p109">Junto com a dica de email, também é possível definir MailTipTranslations, que especifica os idiomas adicionais para a dica de email. Suponha que você deseja que têm a tradução em espanhol e, em seguida, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="790a7-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="790a7-157">Alterar o nome de exibição do grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="790a7-p110">Nome para exibição Especifica o nome do grupo do Office 365. Você pode ver esse nome no seu centro de administração do exchange ou o portal de administração do Office 365. Você pode editar o nome para exibição do grupo ou atribuir um nome de exibição para um grupo existente do Office 365, executando o comando Set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="790a7-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="790a7-161">Altere a configuração padrão dos grupos do Office 365 para o Outlook para pública ou privada</span><span class="sxs-lookup"><span data-stu-id="790a7-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="790a7-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="790a7-162"></span></span>

<span data-ttu-id="790a7-p111">O Office 365 grupos no Outlook são criados como particular por padrão. Se sua organização deseja grupos do Office 365 deve ser criado como público por padrão (ou para Private), use esta sintaxe de cmdlet do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="790a7-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="790a7-165">Para definir como privada:</span><span class="sxs-lookup"><span data-stu-id="790a7-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="790a7-166">Para verificar a configuração:</span><span class="sxs-lookup"><span data-stu-id="790a7-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="790a7-167">Para saber mais, consulte [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) e [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="790a7-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="790a7-168">Cmdlets de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="790a7-169">Os cmdlets a seguir pode ser usados com grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="790a7-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="790a7-170">**Nome do cmdlet**</span><span class="sxs-lookup"><span data-stu-id="790a7-170">**Cmdlet name**</span></span>|<span data-ttu-id="790a7-171">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="790a7-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="790a7-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="790a7-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="790a7-173">Use este cmdlet para procurar grupos de 365 existentes do Office e para visualizar as propriedades do objeto de grupo</span><span class="sxs-lookup"><span data-stu-id="790a7-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="790a7-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="790a7-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="790a7-175">Atualizar as propriedades de um grupo específico de 365 do Office</span><span class="sxs-lookup"><span data-stu-id="790a7-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="790a7-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="790a7-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="790a7-p112">Crie um novo grupo do Office 365. Esse cmdlet fornece um conjunto mínimo de parâmetros, para configuração valores para propriedades estendidas usam Set-UnifiedGroup após a criação do novo grupo</span><span class="sxs-lookup"><span data-stu-id="790a7-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="790a7-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="790a7-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="790a7-180">Excluir um grupo de 365 existente do Office</span><span class="sxs-lookup"><span data-stu-id="790a7-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="790a7-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="790a7-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="790a7-182">Recuperar informações de associação e o proprietário de um grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="790a7-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="790a7-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="790a7-184">Adicionar centenas ou milhares de usuários ou proprietários novos, a um grupo de 365 existente do Office</span><span class="sxs-lookup"><span data-stu-id="790a7-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="790a7-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="790a7-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="790a7-186">Remover membros e proprietários de um grupo de 365 existente do Office</span><span class="sxs-lookup"><span data-stu-id="790a7-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="790a7-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="790a7-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="790a7-p113">Usado para exibir informações sobre a foto do usuário associada a uma conta. Fotos dos usuários são armazenadas no Active Directory</span><span class="sxs-lookup"><span data-stu-id="790a7-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="790a7-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="790a7-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="790a7-p114">Usado para associar uma foto do usuário com uma conta. Fotos dos usuários são armazenadas no Active Directory</span><span class="sxs-lookup"><span data-stu-id="790a7-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="790a7-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="790a7-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="790a7-194">Remover a foto de um grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="790a7-195">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="790a7-195">Related topics</span></span>

[<span data-ttu-id="790a7-196">Listas de distribuição de atualização para o Office 365 grupos</span><span class="sxs-lookup"><span data-stu-id="790a7-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="790a7-197">Gerenciar quem pode criar Grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="790a7-198">Gerenciar o acesso de convidados aos Grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="790a7-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="790a7-199">Alterar a associação ao grupo estático para dinâmico em</span><span class="sxs-lookup"><span data-stu-id="790a7-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
