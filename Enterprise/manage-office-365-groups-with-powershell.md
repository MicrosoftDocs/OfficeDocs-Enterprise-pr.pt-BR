---
title: Gerenciar grupos do Office 365 com o PowerShell
ms.author: dianef
author: dianef77
manager: scotv
ms.date: 6/29/2018
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
description: Este artigo fornece as etapas para realizar tarefas comuns de gerenciamento para grupos no Microsoft PowerShell.
ms.openlocfilehash: 23dfb7f871496b33bf9c34937977b98dc13cea6d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539377"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="e6679-103">Gerenciar grupos do Office 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="e6679-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="e6679-104">*Última atualizados 18 de abril de 2018*</span><span class="sxs-lookup"><span data-stu-id="e6679-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="e6679-p101">Este artigo fornece as etapas para realizar tarefas comuns de gerenciamento para grupos no Microsoft PowerShell. Ela também lista os cmdlets do PowerShell para grupos. Para informações sobre como gerenciar sites do SharePoint, consulte [Gerenciar o SharePoint Online sites usando o PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).</span><span class="sxs-lookup"><span data-stu-id="e6679-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="e6679-108">Tarefas comuns de gerenciamento de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="e6679-109">Listas de distribuição de atualização para o Office 365 grupos</span><span class="sxs-lookup"><span data-stu-id="e6679-109">Upgrade distribution lists to Office 365 Groups</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f.aspx)
    
- [<span data-ttu-id="e6679-110">Gerenciar quem pode criar grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618.aspx)
    
- [<span data-ttu-id="e6679-111">Gerenciar o acesso de convidado aos grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96.aspx)
    
- [<span data-ttu-id="e6679-112">Gerenciar grupos dinamicamente no Windows Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e6679-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="e6679-113">Adicionar centenas ou milhares de usuários aos grupos do Office 365, use o [cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span><span class="sxs-lookup"><span data-stu-id="e6679-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="e6679-114">Link para a suas diretrizes de uso de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="e6679-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="e6679-115"></span></span>

<span data-ttu-id="e6679-p102">Quando os usuários [criar ou editar um grupo no Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), você poderá mostrar um link para as diretrizes de uso da sua organização. Por exemplo, se você exige um prefixo específico ou sufixo a ser adicionado a um nome de grupo.</span><span class="sxs-lookup"><span data-stu-id="e6679-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="e6679-p103">Use o Azure Active Directory PowerShell para direcionar seus usuários às diretrizes de uso da sua organização para grupos do Office 365. Check-out de [cmdlets do Windows Azure Active Directory para definir as configurações de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) e siga as etapas na **criar configurações no nível do diretório** para definir o hiperlink de diretriz de uso. Uma vez você executar o cmdlet AAD, usuário verá o link para a suas diretrizes quando eles cria ou edita um grupo no Outlook.</span><span class="sxs-lookup"><span data-stu-id="e6679-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Criar um novo grupo com o link de diretrizes de uso](media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Clique em diretrizes de uso de grupo para ver suas organizações diretrizes de grupos do Office 365](media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="e6679-123">Permitir que os usuários enviar como o grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="e6679-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="e6679-124"></span></span>

<span data-ttu-id="e6679-p104">Você também pode fazer isso no Centro de administração do Exchange. Consulte [Permitir que os membros "Enviar como" ou "Enviar em nome de" um grupo do Office 365](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).</span><span class="sxs-lookup"><span data-stu-id="e6679-p104">You can also do this in the Exchange Admin Center. See [Allow members to "Send as" or "Send on behalf of" an Office 365 Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).</span></span>
  
<span data-ttu-id="e6679-p105">Se você deseja habilitar os grupos do Office 365 para "Enviar como", use o [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) e os cmdlets [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) essa configuração. Depois que você habilitar essa configuração, os usuários de grupo do Office 365 podem usar o Outlook ou o Outlook na web para enviar e responder para emails como o grupo do Office 365. Os usuários podem ir ao grupo, crie um novo email e altere o campo "Enviar como" para o endereço de email do grupo.</span><span class="sxs-lookup"><span data-stu-id="e6679-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e6679-130">Você precisará adicionar o endereço de email do grupo no campo **Cc** ao redigir email "Enviar como", para que a mensagem é enviada ao grupo e aparece em conversas de grupo.</span><span class="sxs-lookup"><span data-stu-id="e6679-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="e6679-131">Neste momento, a única maneira para atualizar a política de caixa de correio é por meio do [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span><span class="sxs-lookup"><span data-stu-id="e6679-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="e6679-132">Use este comando para definir o alias do grupo.</span><span class="sxs-lookup"><span data-stu-id="e6679-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="e6679-133">Use este comando para definir o alias do usuário.</span><span class="sxs-lookup"><span data-stu-id="e6679-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="e6679-134">Use este comando para passar o groupalias para o cmdlet Get-Recipient para obter os detalhes do destinatário.</span><span class="sxs-lookup"><span data-stu-id="e6679-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="e6679-p106">Em seguida, o nome do destinatário de destino (nome de grupo) precisa ser passado para o cmdlet Add-RecipientPermission. Useralias para quem a permissão sendas receberá será atribuído ao parâmetro - objeto de confiança.</span><span class="sxs-lookup"><span data-stu-id="e6679-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="e6679-137">Depois que o cmdlet é executado, os usuários podem ir para o Outlook ou do Outlook na web para ser enviada como o grupo, adicionando o endereço de email do grupo no campo **de** .</span><span class="sxs-lookup"><span data-stu-id="e6679-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="e6679-138">Criar classificações para grupos do Office em sua organização</span><span class="sxs-lookup"><span data-stu-id="e6679-138">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="e6679-p107">Você pode criar classificações que os usuários em sua organização podem ser definidas quando eles criam um grupo do Office 365. Por exemplo, você pode permitir que os usuários definam "Standard", "Secret" e "Altamente secretos" nos grupos que eles criam. Classificações de grupo não são definidas por padrão, e você precisa criá-lo na ordem para seus usuários para defini-la. Use o Azure Active Directory PowerShell para direcionar seus usuários às diretrizes de uso da sua organização para grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e6679-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="e6679-143">Check-out de [cmdlets do Windows Azure Active Directory para definir as configurações de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) e siga as etapas na **criar configurações no nível do diretório** para definir a classificação de para grupos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e6679-143">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="e6679-144">Para associar uma descrição de cada tabela de classificação que você pode usar as configurações *ClassificationDescriptions* para definir o atributo.</span><span class="sxs-lookup"><span data-stu-id="e6679-144">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="e6679-145">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e6679-145">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="e6679-146">Após executar o cmdlet acima do Azure Active Directory para definir sua classificação, execute o cmdlet [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) se você deseja definir a classificação de um grupo específico.</span><span class="sxs-lookup"><span data-stu-id="e6679-146">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="e6679-147">Ou crie um novo grupo com uma classificação.</span><span class="sxs-lookup"><span data-stu-id="e6679-147">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="e6679-148">Confira [Usando o PowerShell com o Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) e [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) para obter mais detalhes sobre como usar o PowerShell do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="e6679-148">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="e6679-149">Depois que essas configurações estão habilitadas, o proprietário do grupo será capaz de escolher uma classificação na lista suspensa menu no Outlook na Web e Outlook e salvá-lo da página **Editar** grupo.</span><span class="sxs-lookup"><span data-stu-id="e6679-149">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Escolha a classificação de grupo do Office 365](media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="e6679-151">Ocultar grupos do Office 365 da GAL</span><span class="sxs-lookup"><span data-stu-id="e6679-151">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="e6679-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e6679-152"></span></span>

<span data-ttu-id="e6679-p108">Você pode especificar se um grupo do Office 365 é exibida na lista de endereços global (GAL) e outras listas em sua organização. Por exemplo, se você tiver um grupo de departamento jurídico que você não deseja que seja mostrada na lista de endereços, você poderá interromper esse grupo apareçam na GAL. Execute o commandlet Set-Unified grupo para ocultar o grupo da lista de endereços semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="e6679-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="e6679-156">Permitir que somente usuários internos enviar a mensagem ao grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-156">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="e6679-157"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e6679-157"></span></span>

<span data-ttu-id="e6679-p109">Se você não desejar que os usuários de outra organização para enviar email a um grupo do Office 365, você poderá alterar as configurações para esse grupo. Ele permitirá que apenas usuários internos enviar um email para seu grupo. Se o usuário externo tente enviar a mensagem a esse grupo que serão rejeitadas.</span><span class="sxs-lookup"><span data-stu-id="e6679-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="e6679-161">Execute o commandlet Set-UnifiedGroup para atualizar esta configuração, semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="e6679-161">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="e6679-162">Adicionar dicas de email aos grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-162">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="e6679-163"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e6679-163"></span></span>

<span data-ttu-id="e6679-164">Sempre que um remetente tenta enviar um email a um grupo do Office 365, uma dica de email pode ser mostrada a ele.</span><span class="sxs-lookup"><span data-stu-id="e6679-164">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="e6679-165">Execute o commandlet grupo Set-Unified para adicionar uma dica de email para o grupo:</span><span class="sxs-lookup"><span data-stu-id="e6679-165">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="e6679-p110">Junto com a dica de email, você pode também definir MailTipTranslations, que especifica os idiomas adicionais para a dica de email. Suponha que você deseja que têm a tradução em espanhol e, em seguida, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e6679-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="e6679-168">Alterar o nome de exibição do grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-168">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="e6679-p111">Nome para exibição Especifica o nome do grupo do Office 365. Você pode ver esse nome no portal de administração seu exchange admin center ou o365. Você pode editar o nome para exibição do grupo ou atribuir um nome de exibição para um grupo do Office 365 existentes executando o comando Set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="e6679-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="e6679-172">Gerenciar as fotos de usuários em grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-172">Manage user photos in Office 365 Groups</span></span>

|<span data-ttu-id="e6679-173">**Nome do cmdlet**</span><span class="sxs-lookup"><span data-stu-id="e6679-173">**Cmdlet name**</span></span>|<span data-ttu-id="e6679-174">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e6679-174">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="e6679-175">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e6679-175">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="e6679-p112">Usado para exibir informações sobre a foto do usuário associada a uma conta. Fotos dos usuários são armazenadas no Active Directory</span><span class="sxs-lookup"><span data-stu-id="e6679-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="e6679-178">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e6679-178">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="e6679-p113">Usado para associar uma foto do usuário com uma conta. Fotos dos usuários são armazenadas no Active Directory</span><span class="sxs-lookup"><span data-stu-id="e6679-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="e6679-181">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e6679-181">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="e6679-182">Remover a foto de um grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-182">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="e6679-183">Altere a configuração padrão dos grupos do Office 365 para o Outlook para pública ou privada</span><span class="sxs-lookup"><span data-stu-id="e6679-183">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="e6679-184"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e6679-184"></span></span>

<span data-ttu-id="e6679-p114">O Office 365 grupos no Outlook são criados como particular por padrão. Se sua organização deseja grupos do Office 365 para o Outlook deve ser criado como público por padrão (ou para Private), use esta sintaxe de cmdlet do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e6679-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="e6679-187">Para definir como privada:</span><span class="sxs-lookup"><span data-stu-id="e6679-187">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="e6679-188">Para verificar a configuração:</span><span class="sxs-lookup"><span data-stu-id="e6679-188">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="e6679-189">Para saber mais, consulte [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) e [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span><span class="sxs-lookup"><span data-stu-id="e6679-189">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="e6679-190">Cmdlets de grupos do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-190">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="e6679-p115">Os cmdlets a seguir foram feitos recentemente disponíveis aos grupos do Office 365. Se você não poderá usá-los, sua assinatura do Office 365 não foi atualizada com essa funcionalidade ainda. Verifique seu centro de mensagens e o [mapa do Office 365](http://roadmap.office.com/en-us).</span><span class="sxs-lookup"><span data-stu-id="e6679-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Office 365 Roadmap](http://roadmap.office.com/en-us).</span></span>
  
|<span data-ttu-id="e6679-194">**Nome do cmdlet**</span><span class="sxs-lookup"><span data-stu-id="e6679-194">**Cmdlet name**</span></span>|<span data-ttu-id="e6679-195">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e6679-195">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="e6679-196">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="e6679-196">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="e6679-197">Use este cmdlet para procurar grupos de 365 existentes do Office e para visualizar as propriedades do objeto de grupo</span><span class="sxs-lookup"><span data-stu-id="e6679-197">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="e6679-198">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="e6679-198">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="e6679-199">Atualizar as propriedades de um grupo específico de 365 do Office</span><span class="sxs-lookup"><span data-stu-id="e6679-199">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e6679-200">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="e6679-200">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="e6679-p116">Crie um novo grupo do Office 365. Esse cmdlet fornece um conjunto mínimo de parâmetros, para configuração valores para propriedades estendidas usam Set-UnifiedGroup após a criação do novo grupo</span><span class="sxs-lookup"><span data-stu-id="e6679-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="e6679-203">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="e6679-203">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="e6679-204">Excluir um grupo de 365 existente do Office</span><span class="sxs-lookup"><span data-stu-id="e6679-204">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e6679-205">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e6679-205">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="e6679-206">Recuperar informações de associação e o proprietário de um grupo do Office 365</span><span class="sxs-lookup"><span data-stu-id="e6679-206">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e6679-207">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e6679-207">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="e6679-208">Adicionar centenas ou milhares de usuários ou proprietários novos, a um grupo de 365 existente do Office</span><span class="sxs-lookup"><span data-stu-id="e6679-208">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e6679-209">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e6679-209">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="e6679-210">Remover membros e proprietários de um grupo de 365 existente do Office</span><span class="sxs-lookup"><span data-stu-id="e6679-210">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="e6679-211">Para saber mais</span><span class="sxs-lookup"><span data-stu-id="e6679-211">For more information</span></span>

[<span data-ttu-id="e6679-212">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e6679-212">Manage Office 365 with Office 365 PowerShell</span></span>](powershell/manage-office-365-with-office-365-powershell.md)
