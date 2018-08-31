---
title: Recuperar itens excluídos na caixa de correio do usuário – Ajuda para Administradores
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: 'Este artigo destina-se a administradores. Um usuário excluir de permanentemente a itens de suas caixas de correio do Outlook? O usuário deseja-los novamente, mas não é possível recuperá-los. Você pode conseguir recuperar os itens removidos se ainda não tiver sido removidos permanentemente da caixa de correio do usuário. '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539200"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="b22d9-106">Recuperar itens excluídos na caixa de correio do usuário – Ajuda para Administradores</span><span class="sxs-lookup"><span data-stu-id="b22d9-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="b22d9-p102">**Neste artigo destina-se a administradores. Você está tentando recuperar itens excluídos em sua própria caixa de correio?** Tente um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="b22d9-p102">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?** Try one of the following:</span></span>
- [<span data-ttu-id="b22d9-109">Recuperar itens excluídos no Outlook para Windows</span><span class="sxs-lookup"><span data-stu-id="b22d9-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="b22d9-110">Recuperar itens ou emails excluídos no Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="b22d9-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="b22d9-111">Restaurar as mensagens de email excluídas no Outlook na web</span><span class="sxs-lookup"><span data-stu-id="b22d9-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="b22d9-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="b22d9-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="b22d9-p103">Um usuário excluir de permanentemente a itens de suas caixas de correio do Outlook? O usuário deseja-los novamente, mas não é possível recuperá-los. Você pode conseguir recuperar os itens removidos se ainda não tiver sido removidos permanentemente da caixa de correio do usuário. Você pode fazer isso usando a ferramenta de descoberta eletrônica In-loco no Exchange Online para pesquisar por email excluído e outros itens — e como contatos, compromissos do calendário e tarefas — na caixa de correio do usuário. Se você encontrar os itens excluídos, você poderá exportá-los para um arquivo PST (também chamado de um arquivo de dados do Outlook), que o usuário pode usar para restaurar os itens de volta para suas caixas de correio.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p103">Did a user permanently delete items from their Outlook mailbox? The user wants them back but can't recover them. You may be able recover the purged items if they haven't been permanently removed from the user's mailbox. You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox. If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="b22d9-p104">Aqui estão as etapas para recuperar itens excluídos na caixa de correio do usuário. Quanto tempo isso levará? Na primeira vez pode levar 20 ou 30 minutos para ser concluído todas as etapas, dependendo de quantos itens que você está tentando recuperar.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p104">Here are the steps for recovering deleted items in a user's mailbox. How long will this take? The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b22d9-p105">Você precisa ser um **Administrador Global** no Office 365 ou um **administrador do Exchange** ou ser membro do grupo de funções de gerenciamento da organização no Exchange Online para executar as etapas neste artigo. Para obter mais informações, consulte [funções de administrador do Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="b22d9-p105">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article. For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="b22d9-123">Etapa 1: Atribuir permissões de descoberta eletrônica para si mesmo</span><span class="sxs-lookup"><span data-stu-id="b22d9-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="b22d9-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="b22d9-124"></span></span>

<span data-ttu-id="b22d9-p106">A primeira etapa é atribuir si mesmo as permissões necessárias no Exchange Online para que você pode usar a ferramenta de descoberta eletrônica In-loco para pesquisar caixa de correio do usuário. Você só precisa fazer isso vez. Se você tiver outra caixa de correio de pesquisa no futuro, você pode ignorar esta etapa.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p106">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox. You only have to do this once. If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="b22d9-128">[Onde fazer o login Office 365 para empresas](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) com sua conta do trabalho ou da escola.</span><span class="sxs-lookup"><span data-stu-id="b22d9-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="b22d9-129">Selecione o ícone do aplicativo iniciador ![ícone do iniciador de aplicativo no Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) no canto esquerdo superior e clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="b22d9-130">No painel de navegação à esquerda no Centro de administração do Office 365, expanda **centrais de administração**e clique em **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![Lista do Centro de administração](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="b22d9-132">No Centro de administração do Exchange, clique em **permissões**e clique em **funções de administrador**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="b22d9-133">Na exibição de lista, selecione **Gerenciamento de descoberta**e clique em **Editar**![ícone Editar](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span><span class="sxs-lookup"><span data-stu-id="b22d9-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![Adicione si mesmo ao grupo de funções de gerenciamento de descoberta no EAC](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="b22d9-135">No **Grupo de função**, em **membros**, clique em **Adicionar**![ícone Adicionar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="b22d9-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="b22d9-136">Em **Selecionar membros**, selecione sozinho na lista de nomes, clique em **Adicionar**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="b22d9-p107">Você também pode adicionar um grupo que você é um membro de, como o gerenciamento da organização ou TenantAdmins. Se você adicionar um grupo, outros membros do grupo serão atribuídos as permissões necessárias para executar a ferramenta de descoberta eletrônica In-loco.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p107">You can also add a group that you are a member of, such as Organization Management or TenantAdmins. If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="b22d9-139">No **Grupo de função**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="b22d9-140">Sair do Office 365.</span><span class="sxs-lookup"><span data-stu-id="b22d9-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="b22d9-141">Você precisará sair antes de iniciar a próxima etapa para que as novas permissões entrarão em vigor.</span><span class="sxs-lookup"><span data-stu-id="b22d9-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="b22d9-p108">Membros do grupo de função de gerenciamento de descoberta podem acessar o conteúdo da mensagem confidenciais. Isso inclui a pesquisa de todas as caixas de correio em sua organização, visualizar os resultados da pesquisa (e outros itens de caixa de correio), copiando os resultados para uma caixa de correio de descoberta e exporte os resultados de pesquisa para um arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p108">Members of the Discovery Management role group can access sensitive message content. This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="b22d9-144">Return to top</span><span class="sxs-lookup"><span data-stu-id="b22d9-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="b22d9-145">Etapa 2: Pesquisa de caixa de correio do usuário para itens excluídos</span><span class="sxs-lookup"><span data-stu-id="b22d9-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="b22d9-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="b22d9-146"></span></span>

<span data-ttu-id="b22d9-p109">Quando você executa uma pesquisa de descoberta eletrônica In-loco, a pasta itens recuperáveis na caixa de correio que você pesquise automaticamente está incluída na pesquisa. A pasta itens recuperáveis é onde os itens excluídos permanentemente são armazenados até eles estão limpo (removida permanentemente) da caixa de correio. Portanto, se um item ainda não foram removido, você poderá encontrá-lo usando a ferramenta de descoberta eletrônica In-loco.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p109">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search. The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox. So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="b22d9-150">[Onde fazer o login Office 365 para empresas](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) com sua conta do trabalho ou da escola.</span><span class="sxs-lookup"><span data-stu-id="b22d9-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="b22d9-151">Selecione o ícone do aplicativo iniciador ![ícone do iniciador de aplicativo no Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) no canto esquerdo superior e clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="b22d9-152">No painel de navegação à esquerda no Centro de administração do Office 365, expanda **Admin**e, em seguida, clique em **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="b22d9-153">No Centro de administração do Exchange, clique em **gerenciamento de conformidade**, clique em **Descoberta eletrônica In-loco &amp; mantenha**e, em seguida, clique em **novo**![ícone Adicionar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="b22d9-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![No EAC, na página Gerenciamento de conformidade, clique em descoberta eletrônica In-loco e retenção](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="b22d9-155">Na página **nome e descrição** , digite um nome para a pesquisa (por exemplo, o nome do usuário que você estiver recuperando o email para), uma descrição opcional e depois clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="b22d9-156">Na página **caixas de correio** , clique em **especificar caixas de correio para pesquisar**e clique em **Adicionar**![ícone Adicionar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="b22d9-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![Clique em especificar caixas de correio para pesquisar para pesquisar uma caixa de correio specifc](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="b22d9-158">Encontre e selecione o nome do usuário que você estiver recuperando o email excluído para, clique em **Adicionar**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="b22d9-159">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-159">Click **Next**.</span></span>
    
    <span data-ttu-id="b22d9-p110">A página de **consulta de pesquisa** é exibida. Isso é onde você define os critérios de pesquisa que ajudarão você a localizar os itens ausentes na caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p110">The **Search query** page is displayed. This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="b22d9-162">Na página **Consulta de pesquisa**, preencha os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="b22d9-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="b22d9-p111">**Incluir todo o conteúdo** Selecione essa opção para incluir todo o conteúdo na caixa de correio do usuário nos resultados da pesquisa. Se você selecionar essa opção, você não pode especificar critérios de pesquisa adicionais.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p111">**Include all content** Select this option to include all content in the user's mailbox in the search results. If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="b22d9-165">**Filtro com base nos critérios** Selecione essa opção para especificar os critérios de pesquisa, incluindo palavras-chave, iniciar e encerrar datas, remetente e endereços de destinatário e tipos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b22d9-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![Criar uma pesquisa com base nos critérios como palavras-chave, intervalo de datas, tipos de mensagens e destinatários](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="b22d9-167">**Campo**</span><span class="sxs-lookup"><span data-stu-id="b22d9-167">**Field**</span></span>|<span data-ttu-id="b22d9-168">**Use essa opção para...**</span><span class="sxs-lookup"><span data-stu-id="b22d9-168">**Use this to...**</span></span>|
|:-----|:-----|
|![Um número em um círculo rosa](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="b22d9-170">Especifique o intervalo de datas, palavras-chave, os destinatários e tipos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b22d9-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![Número dois em um círculo rosa.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="b22d9-172">Buscar mensagens com palavras-chave ou frases e use operadores lógicos, como **AND** ou **OR**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![Número três em um círculo rosa.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="b22d9-174">Procurar mensagens enviadas ou recebidas em um intervalo de datas.</span><span class="sxs-lookup"><span data-stu-id="b22d9-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![Número 4 de um círculo rosa.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="b22d9-176">Pesquisar mensagens recebidas de ou enviados a pessoas específicas.</span><span class="sxs-lookup"><span data-stu-id="b22d9-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![Número cinco em um círculo rosa.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="b22d9-178">Procurar todos os tipos de mensagem ou selecione aqueles específicos.</span><span class="sxs-lookup"><span data-stu-id="b22d9-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="b22d9-p112">Na página **configurações de bloqueio In-loco** , clique em **Concluir** para iniciar a pesquisa. Para recuperar o email excluído, não há motivo para colocar a caixa de correio do usuário em espera.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p112">On the **In-Place Hold settings** page, click **Finish** to start the search. To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="b22d9-181">Depois de iniciar a pesquisa, o Exchange exibirá uma estimativa do tamanho total e o número de itens que retornarão na pesquisa com base nos critérios especificados por você.</span><span class="sxs-lookup"><span data-stu-id="b22d9-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="b22d9-p113">Selecione a pesquisa que você acabou de criar e clique em **Atualizar**![atualizar](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) para atualizar as informações exibidas no painel de detalhes. O status **Estimativa Succeeded** indica que a pesquisa foi finalizada. Exchange também exibe uma estimativa do número total de itens (e seu tamanho) encontrados na pesquisa com base nos critérios de pesquisa que você especificou na etapa 9.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p113">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane. The status of **Estimate Succeeded** indicates that the search has finished. Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="b22d9-p114">No painel de detalhes, clique em **resultados da pesquisa de visualização** para exibir os itens encontrados. Isso pode ajudá-lo a identificar os itens que você está procurando. Se você encontrar os itens que você está tentando recuperar, vá para a etapa 4 para exportar os resultados da pesquisa para um arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p114">In the details pane, click **Preview search results** to view the items that were found. This might help you identify the item(s) that you're looking for. If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![Clique em visualizar resultados de pesquisa para exibir o item que você está tentando recuperar](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="b22d9-p115">Se você não encontrar o que você está procurando, você pode revisar os critérios de pesquisa, selecionando a pesquisa, clicar em **Editar**![ícone Editar](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)e clicando em **consulta de pesquisa**. Alterar os critérios de pesquisa e, em seguida, execute novamente a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p115">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**. Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="b22d9-191">Return to top</span><span class="sxs-lookup"><span data-stu-id="b22d9-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="b22d9-192">(Opcional) Etapa 3: Copiar os resultados de pesquisa para uma caixa de correio de descoberta</span><span class="sxs-lookup"><span data-stu-id="b22d9-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="b22d9-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="b22d9-193"></span></span>

<span data-ttu-id="b22d9-p116">Se você não puder encontrar uma itens visualizando os resultados da pesquisa, ou se você quiser ver quais itens estão na pasta de itens recuperáveis do usuário, em seguida, você pode copiar os resultados de pesquisa para uma caixa de correio especial (chamada de uma caixa de correio de descoberta) e abra essa caixa de correio do Outlook na web t o visualizar os itens reais. O melhor motivo para copiar os resultados de pesquisa é para que possa visualizar os itens na pasta de itens recuperáveis do usuário. Mais do que provável o item que você está tentando recuperar está localizado na subpasta limpezas.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p116">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items. The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder. More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="b22d9-197">No Centro de administração do Exchange, vá até **gerenciamento de conformidade** \> **Descoberta eletrônica In-loco &amp; mantenha**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="b22d9-198">Na lista de pesquisas, selecione a pesquisa que você criou na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="b22d9-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="b22d9-199">Clique em **Pesquisar**![pesquisa](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)e clique em **resultados da pesquisa de cópia** da lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="b22d9-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![Clique em Pesquisar e clique em resultados da pesquisa de cópia](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="b22d9-201">Na página **Resultados da pesquisa de cópia** , clique em **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![Deixe as caixas de seleção desmarcadas ao recuperar itens excluídos](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="b22d9-203">Em **Nome para exibição**, clique em **Caixa de correio de pesquisa de descoberta**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![Copiar os resultados de pesquisa para a caixa de correio de pesquisa de descoberta padrão](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="b22d9-205">A caixa de correio de pesquisa de descoberta é uma caixa de correio de descoberta padrão que é criada automaticamente na sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="b22d9-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="b22d9-206">Volta na página **Resultados da pesquisa de cópia** , clique em **Copiar** para iniciar o processo para copiar os resultados da pesquisa para a caixa de correio de pesquisa de descoberta.</span><span class="sxs-lookup"><span data-stu-id="b22d9-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![Clique em Copiar para copiar os resultados da pesquisa para a caixa de correio de pesquisa de descoberta](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="b22d9-208">Clique em **Atualizar**![atualizar](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) para atualizar as informações sobre o status de cópia que é exibido no painel de detalhes.</span><span class="sxs-lookup"><span data-stu-id="b22d9-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="b22d9-209">Quando a cópia for concluída, clique em **Abrir** para abrir a caixa de correio de pesquisa de descoberta para exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b22d9-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![Clique em Abrir para ir para a caixa de correio de pesquisa de descoberta para exibir os resultados de pesquisa](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="b22d9-p117">Os resultados da pesquisa copiados para a caixa de correio de pesquisa de descoberta são colocados em uma pasta que tem o mesmo nome que a pesquisa de descoberta eletrônica In-loco. Você pode clicar em uma pasta para exibir os itens nessa pasta.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p117">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search. You can click a folder to display the items in that folder.</span></span>
    
    ![Resultados da pesquisa, na caixa de correio de pesquisa descoberta; itens na pasta limpezas só podem ser recuperadas por um administrador](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="b22d9-p118">Quando você executa uma pesquisa, a pasta de itens recuperáveis do usuário também é pesquisada. Isso significa que se itens na pasta itens recuperáveis atendam aos critérios de pesquisa, eles são incluídos nos resultados da pesquisa. Os itens na pasta exclusões são itens que o usuário é excluído permanentemente (excluindo um item da pasta Itens excluídos ou selecionando-o e pressionando **Shift + Delete**. Um usuário pode usar a ferramenta de recuperar itens excluídos no Outlook ou no Outlook na web para recuperar itens na pasta exclusões. Na pasta limpezas são itens que o usuário removido usando a ferramenta de recuperar itens excluídos ou itens que eles foram removidos automaticamente por uma política aplicada à caixa de correio. Em ambos os casos, apenas um administrador pode recuperar itens na pasta limpezas.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p118">When you run a search, the user's Recoverable Items folder is also searched. That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results. Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**. A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder. Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox. In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="b22d9-p119">Se um usuário não puder encontrar um item excluído, usando a ferramenta de itens recuperáveis, mas que o item ainda é recuperável (o que significa que ele não tenha sido removido permanentemente da caixa de correio), ele é mais do que provável localizado na pasta limpezas. Assim, certifique-se de examinar na pasta limpezas para o item excluído que você está tentando recuperar de um usuário.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p119">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder. So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="b22d9-222">Return to top</span><span class="sxs-lookup"><span data-stu-id="b22d9-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="b22d9-223">Etapa 4: Exportar os resultados da pesquisa para um arquivo PST</span><span class="sxs-lookup"><span data-stu-id="b22d9-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="b22d9-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="b22d9-224"></span></span>

<span data-ttu-id="b22d9-p120">Após localizar o item que você está tentando recuperar para um usuário, a próxima etapa é exportar os resultados de pesquisa que você executou na etapa 2 para um arquivo PST. O usuário usará esse arquivo PST na próxima etapa para restaurar o item excluído para suas caixas de correio.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p120">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file. The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="b22d9-227">No Centro de administração do Exchange, vá até **gerenciamento de conformidade** \> **Descoberta eletrônica In-loco &amp; mantenha**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="b22d9-228">Na lista de pesquisas, selecione a pesquisa que você criou na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="b22d9-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="b22d9-229">Clique em **Exportar para um arquivo PST**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-229">Click **Export to a PST file**.</span></span>
    
    ![Clique em Exportar para um arquivo PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="b22d9-231">Se você for solicitado a instalar a ferramenta de exportação de descoberta eletrônica, clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="b22d9-232">Na ferramenta de exportação de PST descoberta eletrônica, clique em **Procurar** para especificar o local onde você deseja baixar o arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="b22d9-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![A ferramenta de exportação de PST de eDiscovery](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="b22d9-234">Você pode ignorar as opções para habilitar a eliminação da duplicação e incluir itens não pesquisáveis.</span><span class="sxs-lookup"><span data-stu-id="b22d9-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="b22d9-235">Clique em **Iniciar** para baixar o arquivo PST em seu computador.</span><span class="sxs-lookup"><span data-stu-id="b22d9-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="b22d9-p121">A **ferramenta de exportação de PST de descoberta eletrônica** exibe informações de status sobre o processo de exportação. Quando a exportação estiver concluída, você pode acessar o arquivo no local onde ele foi baixado.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p121">The **eDiscovery PST Export Tool** displays status information about the export process. When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="b22d9-238">Return to top</span><span class="sxs-lookup"><span data-stu-id="b22d9-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="b22d9-239">Etapa 5: Restaurar os itens recuperados à caixa de correio do usuário</span><span class="sxs-lookup"><span data-stu-id="b22d9-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="b22d9-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="b22d9-240"></span></span>

<span data-ttu-id="b22d9-p122">A etapa final é usar o arquivo PST que foi exportado na etapa 4 para restaurar os itens recuperados à caixa de correio do usuário. Após enviar o arquivo PST para o usuário, o restante desta etapa é executado pelo usuário para abrir o arquivo PST e, em seguida, mover os itens recuperados para outra pasta em suas caixas de correio. Para obter instruções passo a passo, você também pode enviar ao usuário um link para este tópico: [Abrir e fechar arquivos de dados do Outlook (. pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Ou você pode enviar ao usuário um link para a seção [restaurar itens excluídos para uma caixa de correio usando um arquivo PST](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) abaixo e pedir-lhe que executar estas etapas.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p122">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox. After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox. For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="b22d9-245">**Enviar um arquivo PST para o usuário**</span><span class="sxs-lookup"><span data-stu-id="b22d9-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="b22d9-p123">A etapa final que você precisa executar está enviando o arquivo PST que foi exportado na etapa 4 para o usuário. Existem algumas maneiras de se fazer isso:</span><span class="sxs-lookup"><span data-stu-id="b22d9-p123">The final step that you need to perform is sending the PST file that was exported in step 4 to the user. There are a few ways to do this:</span></span>
  
- <span data-ttu-id="b22d9-p124">Anexe o arquivo PST a uma mensagem de email. Se o Outlook é configurado para bloquear PST arquivos, você terá o arquivo zip e, em seguida, anexá-lo à mensagem. Veja como:</span><span class="sxs-lookup"><span data-stu-id="b22d9-p124">Attach the PST file to an email message. If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message. Here's how:</span></span>
    
1. <span data-ttu-id="b22d9-251">No Windows Explorer ou o Gerenciador de arquivos, navegue até o arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="b22d9-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="b22d9-p125">O arquivo do mouse em e selecione **Enviar para** \> **Compressed folder (compactado)**. O Windows cria um novo arquivo zip e lhe atribui um nome idêntico como o arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p125">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**. Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="b22d9-254">Anexe o arquivo PST compactado a uma mensagem de email e enviá-la ao usuário, que então pode descompactar o arquivo apenas clicando nele.</span><span class="sxs-lookup"><span data-stu-id="b22d9-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="b22d9-255">Copie o arquivo PST para uma pasta compartilhada que o usuário pode acessar e recuperá-la.</span><span class="sxs-lookup"><span data-stu-id="b22d9-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="b22d9-256">As etapas na próxima seção são realizadas pelo usuário para restaurar os itens excluídos para suas caixas de correio.</span><span class="sxs-lookup"><span data-stu-id="b22d9-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="b22d9-257">**Restaurar itens excluídos para uma caixa de correio usando um arquivo PST**</span><span class="sxs-lookup"><span data-stu-id="b22d9-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="b22d9-p126">Você precisa usar o aplicativo de área de trabalho do Outlook para restaurar um item excluído, usando um arquivo PST. Você não pode usar o Outlook Web App ou Outlook na web para abrir um arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p126">You have to use the Outlook desktop app to restore a deleted item by using a PST file. You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="b22d9-260">No Outlook 2013 ou 2016 do Outlook, clique na guia **arquivo** .</span><span class="sxs-lookup"><span data-stu-id="b22d9-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="b22d9-261">Clique em **Open &amp; exportar**e clique em **Abrir arquivo de dados do Outlook**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="b22d9-262">Navegue até o local onde você salvou o arquivo PST enviada pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="b22d9-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="b22d9-263">Selecione o arquivo PST e, em seguida, clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="b22d9-264">O arquivo PST aparece na barra de navegação da esquerda no Outlook.</span><span class="sxs-lookup"><span data-stu-id="b22d9-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![O arquivo PST aparece na barra de navegação da esquerda no Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="b22d9-266">Clique nas setas para expandir o arquivo PST e as pastas nela para localizar o item que você deseja recuperar.</span><span class="sxs-lookup"><span data-stu-id="b22d9-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![Procure na pasta limpezas para o item que você deseja recuperar](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="b22d9-p127">Procure na pasta limpezas para o item que você deseja recuperar. Esta é uma pasta oculta que removidos para os itens serão movidos. Provavelmente é o item que o administrador recuperado é nesta pasta.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p127">Look in the Purges folder for the item you want to recover. This is a hidden folder that purged items are moved to. It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="b22d9-271">Com o botão direito do item que você deseja recuperar e, em seguida, clique em **Mover** \> **Outra pasta**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![Clique em mover e selecione outra pasta](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="b22d9-273">Para mover o item para sua caixa de entrada, clique em **caixa de entrada**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="b22d9-274">**Dica:** Para recuperar outros tipos de itens, siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="b22d9-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="b22d9-275">Para recuperar um item do calendário, clique sobre ela e, em seguida, clique em **Mover** \> **Outra pasta** \> **calendário**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="b22d9-276">Para recuperar um contato, clique sobre ela e, em seguida, clique em **Mover** \> **Outra pasta** \> **Contatos**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="b22d9-277">Para recuperar uma tarefa, clique sobre ela e, em seguida, clique em **Mover** \> **Outra pasta** \> **tarefas**.</span><span class="sxs-lookup"><span data-stu-id="b22d9-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![Selecione uma pasta para mover de outros tipos de itens](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="b22d9-279">Quando tiver terminado de recuperar itens excluídos, com o botão direito na barra de navegação da esquerda e selecione **Fechar "nome do arquivo PST"** arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="b22d9-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="b22d9-280">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="b22d9-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="b22d9-281">Mais informações</span><span class="sxs-lookup"><span data-stu-id="b22d9-281">More information</span></span>
<span data-ttu-id="b22d9-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="b22d9-282"></span></span>

- <span data-ttu-id="b22d9-p128">Talvez seja possível que um usuário recuperar um item excluído permanentemente, se o período de retenção de itens excluídos para o item não tiver expirado. Como um administrador, que talvez você tenha especificados quanto tempo os itens na pasta itens recuperáveis estão disponíveis para recuperação. Por exemplo, pode haver uma política que exclui qualquer coisa que está na pasta Itens excluídos de um usuário por 30 dias e outra política que permite aos usuários recuperar itens na pasta itens recuperáveis para até outro 14 dias. No entanto, após este 14 dias, você ainda poderá recuperar um item na caixa de correio de um usuário usando os procedimentos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="b22d9-p128">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired. As an admin you may have specified how long items in the Recoverable Items folder are available for recovery. For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days. However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="b22d9-p129">Os usuários podem recuperar um item excluído, se ele ainda não foram removido e se o período de retenção de itens excluídos para que o item não tiver expirado. Para ajudar os usuários a recuperar itens excluídos em suas caixas de correio, apontá-los para um dos seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="b22d9-p129">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="b22d9-289">Recuperar itens excluídos no Outlook para Windows</span><span class="sxs-lookup"><span data-stu-id="b22d9-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="b22d9-290">Recuperar itens excluídos no Outlook 2010</span><span class="sxs-lookup"><span data-stu-id="b22d9-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="b22d9-291">Recuperar itens ou emails excluídos no Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="b22d9-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="b22d9-292">Restaurar as mensagens de email excluídas no Outlook na web</span><span class="sxs-lookup"><span data-stu-id="b22d9-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="b22d9-293">Recuperar um contato excluído no Outlook</span><span class="sxs-lookup"><span data-stu-id="b22d9-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="b22d9-294">Restaurar as mensagens de email excluídas no Outlook.com</span><span class="sxs-lookup"><span data-stu-id="b22d9-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="b22d9-295">Return to top</span><span class="sxs-lookup"><span data-stu-id="b22d9-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

