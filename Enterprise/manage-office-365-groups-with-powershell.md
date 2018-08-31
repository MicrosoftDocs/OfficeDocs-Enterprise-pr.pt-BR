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
# <a name="manage-office-365-groups-with-powershell"></a>Gerenciar grupos do Office 365 com o PowerShell

 *Última atualizados 18 de abril de 2018* 
  
Este artigo fornece as etapas para realizar tarefas comuns de gerenciamento para grupos no Microsoft PowerShell. Ela também lista os cmdlets do PowerShell para grupos. Para informações sobre como gerenciar sites do SharePoint, consulte [Gerenciar o SharePoint Online sites usando o PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).
  
## <a name="common-tasks-for-managing-office-365-groups"></a>Tarefas comuns de gerenciamento de grupos do Office 365

- [Listas de distribuição de atualização para o Office 365 grupos](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f.aspx)
    
- [Gerenciar quem pode criar grupos do Office 365](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618.aspx)
    
- [Gerenciar o acesso de convidado aos grupos do Office 365](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96.aspx)
    
- [Gerenciar grupos dinamicamente no Windows Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=847632)
    
- Adicionar centenas ou milhares de usuários aos grupos do Office 365, use o [cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a>Link para a suas diretrizes de uso de grupos do Office 365
<a name="BK_LinkToGuideLines"> </a>

Quando os usuários [criar ou editar um grupo no Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), você poderá mostrar um link para as diretrizes de uso da sua organização. Por exemplo, se você exige um prefixo específico ou sufixo a ser adicionado a um nome de grupo.
  
Use o Azure Active Directory PowerShell para direcionar seus usuários às diretrizes de uso da sua organização para grupos do Office 365. Check-out de [cmdlets do Windows Azure Active Directory para definir as configurações de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) e siga as etapas na **criar configurações no nível do diretório** para definir o hiperlink de diretriz de uso. Uma vez você executar o cmdlet AAD, usuário verá o link para a suas diretrizes quando eles cria ou edita um grupo no Outlook. 
  
![Criar um novo grupo com o link de diretrizes de uso](media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Clique em diretrizes de uso de grupo para ver suas organizações diretrizes de grupos do Office 365](media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a>Permitir que os usuários enviar como o grupo do Office 365
<a name="BK_LinkToGuideLines"> </a>

Você também pode fazer isso no Centro de administração do Exchange. Consulte [Permitir que os membros "Enviar como" ou "Enviar em nome de" um grupo do Office 365](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).
  
Se você deseja habilitar os grupos do Office 365 para "Enviar como", use o [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) e os cmdlets [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) essa configuração. Depois que você habilitar essa configuração, os usuários de grupo do Office 365 podem usar o Outlook ou o Outlook na web para enviar e responder para emails como o grupo do Office 365. Os usuários podem ir ao grupo, crie um novo email e altere o campo "Enviar como" para o endereço de email do grupo. 
  
> [!NOTE]
> Você precisará adicionar o endereço de email do grupo no campo **Cc** ao redigir email "Enviar como", para que a mensagem é enviada ao grupo e aparece em conversas de grupo. 
  
Neste momento, a única maneira para atualizar a política de caixa de correio é por meio do [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).
  
- Use este comando para definir o alias do grupo.
    
  ```
  $groupAlias = "TestSendAs"
  ```

- Use este comando para definir o alias do usuário.
    
  ```
  $userAlias = "User"
  ```

- Use este comando para passar o groupalias para o cmdlet Get-Recipient para obter os detalhes do destinatário.
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- Em seguida, o nome do destinatário de destino (nome de grupo) precisa ser passado para o cmdlet Add-RecipientPermission. Useralias para quem a permissão sendas receberá será atribuído ao parâmetro - objeto de confiança.
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- Depois que o cmdlet é executado, os usuários podem ir para o Outlook ou do Outlook na web para ser enviada como o grupo, adicionando o endereço de email do grupo no campo **de** . 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a>Criar classificações para grupos do Office em sua organização

Você pode criar classificações que os usuários em sua organização podem ser definidas quando eles criam um grupo do Office 365. Por exemplo, você pode permitir que os usuários definam "Standard", "Secret" e "Altamente secretos" nos grupos que eles criam. Classificações de grupo não são definidas por padrão, e você precisa criá-lo na ordem para seus usuários para defini-la. Use o Azure Active Directory PowerShell para direcionar seus usuários às diretrizes de uso da sua organização para grupos do Office 365.
  
Check-out de [cmdlets do Windows Azure Active Directory para definir as configurações de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) e siga as etapas na **criar configurações no nível do diretório** para definir a classificação de para grupos do Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Para associar uma descrição de cada tabela de classificação que você pode usar as configurações *ClassificationDescriptions* para definir o atributo. 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

Exemplo:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Após executar o cmdlet acima do Azure Active Directory para definir sua classificação, execute o cmdlet [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) se você deseja definir a classificação de um grupo específico. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Ou crie um novo grupo com uma classificação.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Confira [Usando o PowerShell com o Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) e [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) para obter mais detalhes sobre como usar o PowerShell do Exchange Online. 
  
Depois que essas configurações estão habilitadas, o proprietário do grupo será capaz de escolher uma classificação na lista suspensa menu no Outlook na Web e Outlook e salvá-lo da página **Editar** grupo. 
  
![Escolha a classificação de grupo do Office 365](media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a>Ocultar grupos do Office 365 da GAL
<a name="BKMK_CreateClassification"> </a>

Você pode especificar se um grupo do Office 365 é exibida na lista de endereços global (GAL) e outras listas em sua organização. Por exemplo, se você tiver um grupo de departamento jurídico que você não deseja que seja mostrada na lista de endereços, você poderá interromper esse grupo apareçam na GAL. Execute o commandlet Set-Unified grupo para ocultar o grupo da lista de endereços semelhante a esta:
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Permitir que somente usuários internos enviar a mensagem ao grupo do Office 365
<a name="BKMK_CreateClassification"> </a>

Se você não desejar que os usuários de outra organização para enviar email a um grupo do Office 365, você poderá alterar as configurações para esse grupo. Ele permitirá que apenas usuários internos enviar um email para seu grupo. Se o usuário externo tente enviar a mensagem a esse grupo que serão rejeitadas.
  
Execute o commandlet Set-UnifiedGroup para atualizar esta configuração, semelhante a esta:
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a>Adicionar dicas de email aos grupos do Office 365
<a name="BKMK_CreateClassification"> </a>

Sempre que um remetente tenta enviar um email a um grupo do Office 365, uma dica de email pode ser mostrada a ele.
  
Execute o commandlet grupo Set-Unified para adicionar uma dica de email para o grupo:
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Junto com a dica de email, você pode também definir MailTipTranslations, que especifica os idiomas adicionais para a dica de email. Suponha que você deseja que têm a tradução em espanhol e, em seguida, execute o seguinte comando:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a>Alterar o nome de exibição do grupo do Office 365

Nome para exibição Especifica o nome do grupo do Office 365. Você pode ver esse nome no portal de administração seu exchange admin center ou o365. Você pode editar o nome para exibição do grupo ou atribuir um nome de exibição para um grupo do Office 365 existentes executando o comando Set-UnifiedGroup:
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a>Gerenciar as fotos de usuários em grupos do Office 365

|**Nome do cmdlet**|**Descrição**|
|:-----|:-----|
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Usado para exibir informações sobre a foto do usuário associada a uma conta. Fotos dos usuários são armazenadas no Active Directory  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Usado para associar uma foto do usuário com uma conta. Fotos dos usuários são armazenadas no Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Remover a foto de um grupo do Office 365  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Altere a configuração padrão dos grupos do Office 365 para o Outlook para pública ou privada
<a name="BKMK_CreateClassification"> </a>

O Office 365 grupos no Outlook são criados como particular por padrão. Se sua organização deseja grupos do Office 365 para o Outlook deve ser criado como público por padrão (ou para Private), use esta sintaxe de cmdlet do PowerShell:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Para definir como privada:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Para verificar a configuração: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Para saber mais, consulte [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) e [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).
  
## <a name="office-365-groups-cmdlets"></a>Cmdlets de grupos do Office 365

Os cmdlets a seguir foram feitos recentemente disponíveis aos grupos do Office 365. Se você não poderá usá-los, sua assinatura do Office 365 não foi atualizada com essa funcionalidade ainda. Verifique seu centro de mensagens e o [mapa do Office 365](http://roadmap.office.com/en-us).
  
|**Nome do cmdlet**|**Descrição**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Use este cmdlet para procurar grupos de 365 existentes do Office e para visualizar as propriedades do objeto de grupo  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Atualizar as propriedades de um grupo específico de 365 do Office  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Crie um novo grupo do Office 365. Esse cmdlet fornece um conjunto mínimo de parâmetros, para configuração valores para propriedades estendidas usam Set-UnifiedGroup após a criação do novo grupo  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Excluir um grupo de 365 existente do Office  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Recuperar informações de associação e o proprietário de um grupo do Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Adicionar centenas ou milhares de usuários ou proprietários novos, a um grupo de 365 existente do Office  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Remover membros e proprietários de um grupo de 365 existente do Office  <br/> |
   
## <a name="for-more-information"></a>Para saber mais

[Gerenciar o Office 365 com o Office 365 PowerShell](powershell/manage-office-365-with-office-365-powershell.md)
