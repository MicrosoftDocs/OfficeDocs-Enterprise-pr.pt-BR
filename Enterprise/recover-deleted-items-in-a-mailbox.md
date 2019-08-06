---
title: Recuperar itens excluídos na caixa de correio do usuário – Ajuda para Administradores
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: Admin
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
description: 'Este artigo é para administradores. Um usuário excluiu permanentemente itens da caixa de correio do Outlook? O usuário deseja refazê-los, mas não pode recuperá-los. Você pode ser capaz de recuperar os itens removidos se eles não foram removidos permanentemente da caixa de correio do usuário. '
ms.openlocfilehash: 12e07a88136d0dee0f186857aa71c3de6736a798
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782611"
---
<a name="__top"></a>
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="c6798-106">Recuperar itens excluídos na caixa de correio do usuário – Ajuda para Administradores</span><span class="sxs-lookup"><span data-stu-id="c6798-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="c6798-107">**Este artigo é para administradores. Você está tentando recuperar itens excluídos em sua própria caixa de correio?**</span><span class="sxs-lookup"><span data-stu-id="c6798-107">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?**</span></span> <span data-ttu-id="c6798-108">Tente uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="c6798-108">Try one of the following:</span></span>
- [<span data-ttu-id="c6798-109">Recuperar itens excluídos no Outlook para Windows</span><span class="sxs-lookup"><span data-stu-id="c6798-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="c6798-110">Recuperar itens ou emails excluídos no Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="c6798-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="c6798-111">Restaurar mensagens de email excluídas no Outlook na Web</span><span class="sxs-lookup"><span data-stu-id="c6798-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="c6798-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="c6798-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="c6798-113">Um usuário excluiu permanentemente itens da caixa de correio do Outlook?</span><span class="sxs-lookup"><span data-stu-id="c6798-113">Did a user permanently delete items from their Outlook mailbox?</span></span> <span data-ttu-id="c6798-114">O usuário deseja refazê-los, mas não pode recuperá-los.</span><span class="sxs-lookup"><span data-stu-id="c6798-114">The user wants them back but can't recover them.</span></span> <span data-ttu-id="c6798-115">Você pode ser capaz de recuperar os itens removidos se eles não foram removidos permanentemente da caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-115">You may be able recover the purged items if they haven't been permanently removed from the user's mailbox.</span></span> <span data-ttu-id="c6798-116">Para fazer isso, use a ferramenta de descoberta eletrônica in-loco no Exchange Online para pesquisar emails excluídos e outros itens, como contatos, compromissos de calendário e tarefas — na caixa de correio de um usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-116">You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox.</span></span> <span data-ttu-id="c6798-117">Se encontrar os itens excluídos, você poderá exportá-los para um arquivo PST (também chamado de arquivo de dados do Outlook), que o usuário pode usar para restaurar os itens de volta à caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="c6798-117">If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="c6798-118">Aqui estão as etapas para recuperar itens excluídos na caixa de correio de um usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-118">Here are the steps for recovering deleted items in a user's mailbox.</span></span> <span data-ttu-id="c6798-119">Quanto tempo isso levará?</span><span class="sxs-lookup"><span data-stu-id="c6798-119">How long will this take?</span></span> <span data-ttu-id="c6798-120">A primeira vez pode levar 20 ou 30 minutos para concluir todas as etapas, dependendo de quantos itens você está tentando recuperar.</span><span class="sxs-lookup"><span data-stu-id="c6798-120">The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c6798-121">Você precisa ser um **administrador do Exchange** ou um **Administrador Global** no Office 365 ou ser membro do grupo de função gerenciamento da organização no Exchange Online para executar as etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="c6798-121">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article.</span></span> <span data-ttu-id="c6798-122">Para saber mais, veja [Sobre as funções de administrador do Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="c6798-122">For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="c6798-123">Etapa 1: atribuir permissões de descoberta eletrônica por conta própria</span><span class="sxs-lookup"><span data-stu-id="c6798-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="c6798-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="c6798-124"></span></span>

<span data-ttu-id="c6798-125">A primeira etapa é atribuir as permissões necessárias no Exchange Online para que você possa usar a ferramenta de descoberta eletrônica in-loco para pesquisar a caixa de correio de um usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-125">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox.</span></span> <span data-ttu-id="c6798-126">Você só precisa fazer isso uma vez.</span><span class="sxs-lookup"><span data-stu-id="c6798-126">You only have to do this once.</span></span> <span data-ttu-id="c6798-127">Se você precisar pesquisar outra caixa de correio no futuro, ignore esta etapa.</span><span class="sxs-lookup"><span data-stu-id="c6798-127">If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="c6798-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) com sua conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="c6798-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="c6798-129">Selecione o ícone ![do inicializador de aplicativos o ícone do inicializador de aplicativos no Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) no canto superior esquerdo e clique em **administrador**.</span><span class="sxs-lookup"><span data-stu-id="c6798-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="c6798-130">Na navegação à esquerda no centro de administração do Microsoft 365, expanda **centros de administração**e clique em **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="c6798-130">In the left navigation in the Microsoft 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![Lista do centro de administração](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="c6798-132">No centro de administração do Exchange, clique em **permissões**e, em seguida, clique em **funções de administrador**.</span><span class="sxs-lookup"><span data-stu-id="c6798-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="c6798-133">No modo de exibição de lista, selecione **Gerenciamento de descoberta**e \*\*\*\*![clique em Editar](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)ícone de edição.</span><span class="sxs-lookup"><span data-stu-id="c6798-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![Adicione a si mesmo ao grupo de função gerenciamento de descoberta no Eat](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="c6798-135">Em **grupo de função**, **em Membros**, clique em **Adicionar**![ícone](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)de adição.</span><span class="sxs-lookup"><span data-stu-id="c6798-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="c6798-136">Em **selecionar Membros**, selecione-se na lista de nomes, clique em **Adicionar**e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6798-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c6798-137">Você também pode adicionar um grupo do qual você é membro, como gerenciamento da organização ou TenantAdmins.</span><span class="sxs-lookup"><span data-stu-id="c6798-137">You can also add a group that you are a member of, such as Organization Management or TenantAdmins.</span></span> <span data-ttu-id="c6798-138">Se você adicionar um grupo, as permissões necessárias para executar a ferramenta de descoberta eletrônica in-loco serão atribuídas a outros membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="c6798-138">If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="c6798-139">Em **grupo de funções**, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="c6798-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="c6798-140">Saia do Office 365.</span><span class="sxs-lookup"><span data-stu-id="c6798-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="c6798-141">Você deve sair antes de iniciar a próxima etapa para que as novas permissões entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="c6798-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="c6798-142">Os membros do grupo de função gerenciamento de descoberta podem acessar o conteúdo de mensagens confidenciais.</span><span class="sxs-lookup"><span data-stu-id="c6798-142">Members of the Discovery Management role group can access sensitive message content.</span></span> <span data-ttu-id="c6798-143">Isso inclui pesquisar todas as caixas de correio em sua organização, Visualizar os resultados da pesquisa (e outros itens de caixa de correio), copiar os resultados para uma caixa de correio de descoberta e exportar os resultados da pesquisa para um arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="c6798-143">This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="c6798-144">Return to top</span><span class="sxs-lookup"><span data-stu-id="c6798-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="c6798-145">Etapa 2: Pesquisar itens excluídos na caixa de correio do usuário</span><span class="sxs-lookup"><span data-stu-id="c6798-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="c6798-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="c6798-146"></span></span>

<span data-ttu-id="c6798-147">Quando você executa uma pesquisa de descoberta eletrônica in-loco, a pasta itens recuperáveis na caixa de correio que você pesquisa é automaticamente incluída na pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c6798-147">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search.</span></span> <span data-ttu-id="c6798-148">A pasta itens recuperáveis é onde os itens excluídos permanentemente são armazenados até serem limpos (permanentemente removidos) da caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="c6798-148">The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox.</span></span> <span data-ttu-id="c6798-149">Portanto, se um item não tiver sido removido, você deverá ser capaz de encontrá-lo usando a ferramenta de descoberta eletrônica in-loco.</span><span class="sxs-lookup"><span data-stu-id="c6798-149">So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="c6798-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) com sua conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="c6798-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="c6798-151">Selecione o ícone ![do inicializador de aplicativos o ícone do inicializador de aplicativos no Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) no canto superior esquerdo e clique em **administrador**.</span><span class="sxs-lookup"><span data-stu-id="c6798-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="c6798-152">Na navegação à esquerda no centro de administração do Microsoft 365, expanda **administrador**e clique em **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="c6798-152">In the left navigation in the Microsoft 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="c6798-153">No centro de administração do Exchange, clique em **Gerenciamento de conformidade**, clique **em &amp; bloqueio de descoberta eletrônica in-loco**e](media/8ee52980-254b-440b-99a2-18d068de62d3.gif), em seguida, clique em **novo**![ícone de adição.</span><span class="sxs-lookup"><span data-stu-id="c6798-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![No Eat, na página Gerenciamento de conformidade, clique em descoberta eletrônica in-loco e bloqueio](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="c6798-155">Na página **nome e descrição** , digite um nome para a pesquisa (como o nome do usuário para o qual você está recuperando o email), uma descrição opcional e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c6798-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c6798-156">Na página **caixas de correio** , clique **em especificar caixas de correio a serem pesquisadas**e, em seguida, clique em **Adicionar**![ícone](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)de adição.</span><span class="sxs-lookup"><span data-stu-id="c6798-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![Clique em especificar caixas de correio para pesquisar na pesquisa de uma caixa de correio do especialmente](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="c6798-158">Localize e selecione o nome do usuário para o qual você está recuperando o email excluído, clique em **Adicionar**e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6798-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="c6798-159">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c6798-159">Click **Next**.</span></span>
    
    <span data-ttu-id="c6798-160">A página de **consulta de pesquisa** é exibida.</span><span class="sxs-lookup"><span data-stu-id="c6798-160">The **Search query** page is displayed.</span></span> <span data-ttu-id="c6798-161">É aqui que você define os critérios de pesquisa que o ajudarão a encontrar os itens ausentes na caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-161">This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="c6798-162">Na página **Consulta de pesquisa**, preencha os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="c6798-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="c6798-163">**Incluir todo o conteúdo** Selecione essa opção para incluir todo o conteúdo na caixa de correio do usuário nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c6798-163">**Include all content** Select this option to include all content in the user's mailbox in the search results.</span></span> <span data-ttu-id="c6798-164">Se você selecionar essa opção, não poderá especificar critérios de pesquisa adicionais.</span><span class="sxs-lookup"><span data-stu-id="c6798-164">If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="c6798-165">**Filtro com base nos critérios** Selecione essa opção para especificar os critérios de pesquisa, incluindo palavras-chave, datas de início e término, endereços do remetente e do destinatário e tipos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c6798-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![Criar um Pesquisar com base em critérios como palavras-chave, intervalo de datas, destinatários e tipos de mensagem](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="c6798-167">**Field**</span><span class="sxs-lookup"><span data-stu-id="c6798-167">**Field**</span></span>|<span data-ttu-id="c6798-168">**Use para...**</span><span class="sxs-lookup"><span data-stu-id="c6798-168">**Use this to...**</span></span>|
|:-----|:-----|
|![Number one in a pink circle](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="c6798-170">Especifique palavras-chave, intervalo de datas, destinatários e tipos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c6798-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![Number two in a pink circle.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="c6798-172">Pesquise mensagens com palavras-chave ou frases e use operadores lógicos, como **e** ou **ou**.</span><span class="sxs-lookup"><span data-stu-id="c6798-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![Number three in a pink circle.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="c6798-174">Pesquisar mensagens enviadas ou recebidas em um intervalo de datas.</span><span class="sxs-lookup"><span data-stu-id="c6798-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![Number 4 in a pink circle.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="c6798-176">Pesquisar mensagens recebidas ou enviadas para pessoas específicas.</span><span class="sxs-lookup"><span data-stu-id="c6798-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![Número cinco em um círculo rosa.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="c6798-178">Procure todos os tipos de mensagem ou selecione os específicos.</span><span class="sxs-lookup"><span data-stu-id="c6798-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="c6798-179">Na página **configurações de bloqueio in-loco** , clique em **concluir** para iniciar a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c6798-179">On the **In-Place Hold settings** page, click **Finish** to start the search.</span></span> <span data-ttu-id="c6798-180">Para recuperar emails excluídos, não há motivo para colocar a caixa de correio do usuário em espera.</span><span class="sxs-lookup"><span data-stu-id="c6798-180">To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="c6798-181">Depois que você iniciar a pesquisa, o Exchange exibirá uma estimativa do tamanho total e do número de itens que será retornado pela pesquisa com base nos critérios que você especificou.</span><span class="sxs-lookup"><span data-stu-id="c6798-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="c6798-182">Selecione a pesquisa que você acabou de criar \*\*\*\*![e clique](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) em atualizar atualização para atualizar as informações exibidas no painel de detalhes.</span><span class="sxs-lookup"><span data-stu-id="c6798-182">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane.</span></span> <span data-ttu-id="c6798-183">O status da **estimativa com êxito** indica que a pesquisa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="c6798-183">The status of **Estimate Succeeded** indicates that the search has finished.</span></span> <span data-ttu-id="c6798-184">O Exchange também exibe uma estimativa do número total de itens (e seu tamanho) encontrado pela pesquisa com base nos critérios de pesquisa que você especificou na etapa 9.</span><span class="sxs-lookup"><span data-stu-id="c6798-184">Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="c6798-185">No painel de detalhes, clique em **Visualizar resultados da pesquisa** para exibir os itens que foram encontrados.</span><span class="sxs-lookup"><span data-stu-id="c6798-185">In the details pane, click **Preview search results** to view the items that were found.</span></span> <span data-ttu-id="c6798-186">Isso pode ajudar a identificar o (s) item (ns) que você está procurando.</span><span class="sxs-lookup"><span data-stu-id="c6798-186">This might help you identify the item(s) that you're looking for.</span></span> <span data-ttu-id="c6798-187">Se encontrar o (s) item (ns) que você está tentando recuperar, vá para a etapa 4 para exportar os resultados da pesquisa para um arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="c6798-187">If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![Clique em Visualizar resultados da pesquisa para exibir o item que você está tentando recuperar](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="c6798-189">Se não encontrar o que você está procurando, você poderá revisar seus critérios de pesquisa selecionando a pesquisa, \*\*\*\*![clicando em Editar](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)editar ícone e, em seguida, clicando em **consulta de pesquisa**.</span><span class="sxs-lookup"><span data-stu-id="c6798-189">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**.</span></span> <span data-ttu-id="c6798-190">Altere o critério de pesquisa e execute a pesquisa novamente.</span><span class="sxs-lookup"><span data-stu-id="c6798-190">Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="c6798-191">Return to top</span><span class="sxs-lookup"><span data-stu-id="c6798-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="c6798-192">Opcion Etapa 3: copiar os resultados da pesquisa para uma caixa de correio de descoberta</span><span class="sxs-lookup"><span data-stu-id="c6798-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="c6798-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="c6798-193"></span></span>

<span data-ttu-id="c6798-194">Se não for possível localizar itens visualizando os resultados da pesquisa ou se quiser ver quais itens estão na pasta itens recuperáveis do usuário, você pode copiar os resultados da pesquisa para uma caixa de correio especial (chamada de caixa de correio de descoberta) e abrir essa caixa de correio no Outlook na Web t o exibir os itens reais.</span><span class="sxs-lookup"><span data-stu-id="c6798-194">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items.</span></span> <span data-ttu-id="c6798-195">O melhor motivo para copiar os resultados da pesquisa é que você possa exibir os itens na pasta itens recuperáveis do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-195">The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder.</span></span> <span data-ttu-id="c6798-196">Mais do que provavelmente, o item que você está tentando recuperar está localizado na subpasta limpezas.</span><span class="sxs-lookup"><span data-stu-id="c6798-196">More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="c6798-197">No centro de administração do Exchange, vá para **Gerenciamento** \> **de conformidade e descoberta &amp; eletrônica in-loco**.</span><span class="sxs-lookup"><span data-stu-id="c6798-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="c6798-198">Na lista de pesquisas, selecione a pesquisa que você criou na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="c6798-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="c6798-199">Clique \*\*\*\*![em pesquisa](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)de pesquisa e, em seguida, clique em **copiar resultados da pesquisa** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="c6798-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![Clique em Pesquisar e, em seguida, clique em copiar resultados da pesquisa](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="c6798-201">Na página **copiar resultados da pesquisa** , clique em **procurar**.</span><span class="sxs-lookup"><span data-stu-id="c6798-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![Deixar caixas de seleção desmarcadas ao recuperar itens excluídos](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="c6798-203">Em **nome para exibição**, clique em **caixa de correio de pesquisa de descoberta**e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6798-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![Copiar os resultados da pesquisa para a caixa de correio de pesquisa de descoberta padrão](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="c6798-205">A caixa de correio de pesquisa de descoberta é uma caixa de correio de descoberta padrão criada automaticamente na sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="c6798-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="c6798-206">De volta à página **copiar resultados da pesquisa** , clique em **copiar** para iniciar o processo para copiar os resultados da pesquisa para a caixa de correio de pesquisa de descoberta.</span><span class="sxs-lookup"><span data-stu-id="c6798-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![Clique em copiar para copiar os resultados da pesquisa para a caixa de correio de pesquisa de descoberta](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="c6798-208">Clique \*\*\*\*![em atualizar](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) atualização para atualizar as informações sobre o status de cópia exibido no painel de detalhes.</span><span class="sxs-lookup"><span data-stu-id="c6798-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="c6798-209">Quando a cópia estiver concluída, clique em **abrir** para abrir a caixa de correio de pesquisa de descoberta para exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c6798-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![Clique em abrir para ir para a caixa de correio de pesquisa de descoberta para exibir os resultados da pesquisa](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="c6798-211">Os resultados da pesquisa copiados para a caixa de correio de pesquisa de descoberta são colocados em uma pasta com o mesmo nome da pesquisa de descoberta eletrônica in-loco.</span><span class="sxs-lookup"><span data-stu-id="c6798-211">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search.</span></span> <span data-ttu-id="c6798-212">Você pode clicar em uma pasta para exibir os itens dessa pasta.</span><span class="sxs-lookup"><span data-stu-id="c6798-212">You can click a folder to display the items in that folder.</span></span>
    
    ![Resultados da pesquisa na caixa de correio de pesquisa de descoberta; os itens na pasta expurgações só podem ser recuperados por um administrador](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="c6798-214">Quando você executa uma pesquisa, a pasta itens recuperáveis do usuário também é pesquisada.</span><span class="sxs-lookup"><span data-stu-id="c6798-214">When you run a search, the user's Recoverable Items folder is also searched.</span></span> <span data-ttu-id="c6798-215">Isso significa que se os itens na pasta itens recuperáveis atenderem aos critérios de pesquisa, eles serão incluídos nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c6798-215">That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results.</span></span> <span data-ttu-id="c6798-216">Itens na pasta exclusões são itens que o usuário excluiu permanentemente (excluindo um item da pasta itens excluídos ou selecionando-o e pressionando **Shift + Delete**.</span><span class="sxs-lookup"><span data-stu-id="c6798-216">Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**.</span></span> <span data-ttu-id="c6798-217">Um usuário pode usar a ferramenta recuperar itens excluídos no Outlook ou no Outlook na Web para recuperar itens na pasta exclusões.</span><span class="sxs-lookup"><span data-stu-id="c6798-217">A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder.</span></span> <span data-ttu-id="c6798-218">Itens na pasta expurgações são itens que o usuário limpou usando a ferramenta recuperar itens excluídos ou itens que eles foram automaticamente limpos por uma política aplicada à caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="c6798-218">Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox.</span></span> <span data-ttu-id="c6798-219">Em ambos os casos, somente um administrador pode recuperar itens na pasta expurgações.</span><span class="sxs-lookup"><span data-stu-id="c6798-219">In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="c6798-220">Se um usuário não conseguir localizar um item excluído usando a ferramenta itens recuperáveis, mas esse item ainda for recuperável (o que significa que ele não foi removido permanentemente da caixa de correio), é mais do que provavelmente localizado na pasta limpezas.</span><span class="sxs-lookup"><span data-stu-id="c6798-220">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder.</span></span> <span data-ttu-id="c6798-221">Portanto, certifique-se de examinar a pasta limpezas do item excluído que você está tentando recuperar para um usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-221">So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="c6798-222">Return to top</span><span class="sxs-lookup"><span data-stu-id="c6798-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="c6798-223">Etapa 4: exportar os resultados da pesquisa para um arquivo PST</span><span class="sxs-lookup"><span data-stu-id="c6798-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="c6798-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="c6798-224"></span></span>

<span data-ttu-id="c6798-225">Após localizar o item que você está tentando recuperar para um usuário, a próxima etapa é exportar os resultados da pesquisa executada na etapa 2 para um arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="c6798-225">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file.</span></span> <span data-ttu-id="c6798-226">O usuário usará esse arquivo PST na próxima etapa para restaurar o item excluído à caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="c6798-226">The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="c6798-227">No centro de administração do Exchange, vá para **Gerenciamento** \> **de conformidade e descoberta &amp; eletrônica in-loco**.</span><span class="sxs-lookup"><span data-stu-id="c6798-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="c6798-228">Na lista de pesquisas, selecione a pesquisa que você criou na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="c6798-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="c6798-229">Clique em **exportar para um arquivo PST**.</span><span class="sxs-lookup"><span data-stu-id="c6798-229">Click **Export to a PST file**.</span></span>
    
    ![Clique em exportar para um arquivo PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="c6798-231">Se você for solicitado a instalar a ferramenta de exportação de descoberta eletrônica, clique em **executar**.</span><span class="sxs-lookup"><span data-stu-id="c6798-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="c6798-232">Na ferramenta de exportação de PST de descoberta eletrônica, clique em **procurar** para especificar o local onde você deseja baixar o arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="c6798-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![A ferramenta de exportação de PST de descoberta eletrônica](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="c6798-234">Você pode ignorar as opções para habilitar a eliminação de duplicação e incluir itens não pesquisáveis.</span><span class="sxs-lookup"><span data-stu-id="c6798-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="c6798-235">Clique em **Iniciar** para baixar o arquivo pst em seu computador.</span><span class="sxs-lookup"><span data-stu-id="c6798-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="c6798-236">A **ferramenta de exportação de PST de descoberta eletrônica** exibe informações de status sobre o processo de exportação.</span><span class="sxs-lookup"><span data-stu-id="c6798-236">The **eDiscovery PST Export Tool** displays status information about the export process.</span></span> <span data-ttu-id="c6798-237">Quando a exportação estiver concluída, você poderá acessar o arquivo no local onde foi baixado.</span><span class="sxs-lookup"><span data-stu-id="c6798-237">When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="c6798-238">Return to top</span><span class="sxs-lookup"><span data-stu-id="c6798-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="c6798-239">Etapa 5: restaurar os itens recuperados para a caixa de correio do usuário</span><span class="sxs-lookup"><span data-stu-id="c6798-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="c6798-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="c6798-240"></span></span>

<span data-ttu-id="c6798-241">A etapa final é usar o arquivo PST que foi exportado na etapa 4 para restaurar os itens recuperados para a caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-241">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox.</span></span> <span data-ttu-id="c6798-242">Depois de enviar o arquivo PST ao usuário, o restante desta etapa é executado pelo usuário para abrir o arquivo PST e, em seguida, mover os itens recuperados para outra pasta na caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="c6798-242">After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox.</span></span> <span data-ttu-id="c6798-243">Para obter instruções passo a passo, você também pode enviar ao usuário um link para este tópico: [abrir e fechar arquivos de dados do Outlook (. pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2).</span><span class="sxs-lookup"><span data-stu-id="c6798-243">For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2).</span></span> <span data-ttu-id="c6798-244">Ou você pode enviar ao usuário um link para a seção [restaurar itens excluídos para uma caixa de correio usando um arquivo PST](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) abaixo e pedir que eles executem essas etapas.</span><span class="sxs-lookup"><span data-stu-id="c6798-244">Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="c6798-245">**Enviar o arquivo PST ao usuário**</span><span class="sxs-lookup"><span data-stu-id="c6798-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="c6798-246">A etapa final que você precisa realizar é enviar o arquivo PST que foi exportado na etapa 4 para o usuário.</span><span class="sxs-lookup"><span data-stu-id="c6798-246">The final step that you need to perform is sending the PST file that was exported in step 4 to the user.</span></span> <span data-ttu-id="c6798-247">Há algumas maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="c6798-247">There are a few ways to do this:</span></span>
  
- <span data-ttu-id="c6798-248">Anexe o arquivo PST a uma mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="c6798-248">Attach the PST file to an email message.</span></span> <span data-ttu-id="c6798-249">Se o Outlook estiver configurado para bloquear arquivos PST, você terá que compactar o arquivo e anexá-lo à mensagem.</span><span class="sxs-lookup"><span data-stu-id="c6798-249">If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message.</span></span> <span data-ttu-id="c6798-250">Veja como:</span><span class="sxs-lookup"><span data-stu-id="c6798-250">Here's how:</span></span>
    
1. <span data-ttu-id="c6798-251">No Windows Explorer ou no explorador de arquivos, navegue até o arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="c6798-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="c6798-252">Clique com o botão direito do mouse no arquivo e selecione **Enviar para** \> **pasta compactada (zipada)**.</span><span class="sxs-lookup"><span data-stu-id="c6798-252">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**.</span></span> <span data-ttu-id="c6798-253">O Windows cria um novo arquivo zip e fornece um nome idêntico ao arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="c6798-253">Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="c6798-254">Anexe o arquivo PST compactado a uma mensagem de email e envie-o ao usuário, que pode descompactar o arquivo simplesmente clicando nele.</span><span class="sxs-lookup"><span data-stu-id="c6798-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="c6798-255">Copie o arquivo PST para uma pasta compartilhada que o usuário possa acessar e recuperá-lo.</span><span class="sxs-lookup"><span data-stu-id="c6798-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="c6798-256">As etapas da próxima seção são executadas pelo usuário para restaurar os itens excluídos para a caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="c6798-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <a name="restoredeleteditems"></a>
<span data-ttu-id="c6798-257">**Restaurar itens excluídos para uma caixa de correio usando um arquivo PST**</span><span class="sxs-lookup"><span data-stu-id="c6798-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="c6798-258">Você precisa usar o aplicativo da área de trabalho do Outlook para restaurar um item excluído usando um arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="c6798-258">You have to use the Outlook desktop app to restore a deleted item by using a PST file.</span></span> <span data-ttu-id="c6798-259">Você não pode usar o Outlook Web App ou o Outlook na Web para abrir um arquivo PST.</span><span class="sxs-lookup"><span data-stu-id="c6798-259">You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="c6798-260">No Outlook 2013 ou no Outlook 2016, clique na guia **arquivo** .</span><span class="sxs-lookup"><span data-stu-id="c6798-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="c6798-261">Clique **em &amp; abrir exportação**e, em seguida, clique em **Abrir arquivo de dados do Outlook**.</span><span class="sxs-lookup"><span data-stu-id="c6798-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="c6798-262">Navegue até o local onde você salvou o arquivo PST enviado pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="c6798-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="c6798-263">Selecione o PST e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="c6798-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="c6798-264">O arquivo PST aparece na barra de navegação à esquerda no Outlook.</span><span class="sxs-lookup"><span data-stu-id="c6798-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![O arquivo PST aparece na barra de navegação à esquerda no Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="c6798-266">Clique nas setas para expandir o arquivo PST e as pastas abaixo dele para localizar o item que você deseja recuperar.</span><span class="sxs-lookup"><span data-stu-id="c6798-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![Procure na pasta limpezas do item que você deseja recuperar](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="c6798-268">Procure na pasta limpezas do item que você deseja recuperar.</span><span class="sxs-lookup"><span data-stu-id="c6798-268">Look in the Purges folder for the item you want to recover.</span></span> <span data-ttu-id="c6798-269">Esta é uma pasta oculta à qual os itens excluídos são movidos.</span><span class="sxs-lookup"><span data-stu-id="c6798-269">This is a hidden folder that purged items are moved to.</span></span> <span data-ttu-id="c6798-270">É provável que o item que o administrador tenha recuperado esteja nessa pasta.</span><span class="sxs-lookup"><span data-stu-id="c6798-270">It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="c6798-271">Clique com o botão direito do mouse no item que você deseja recuperar e clique em **mover** \> **outra pasta**.</span><span class="sxs-lookup"><span data-stu-id="c6798-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![Clique em mover e selecione outra pasta](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="c6798-273">Para mover o item para a caixa de entrada, clique em **caixa de entrada**e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6798-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="c6798-274">**Dica:** Para recuperar outros tipos de itens, siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="c6798-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="c6798-275">Para recuperar um item de calendário, clique nele com o botão direito do mouse e, em seguida, clique em **mover** \> **outro** \> **calendário**de pasta.</span><span class="sxs-lookup"><span data-stu-id="c6798-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="c6798-276">Para recuperar um contato, clique nele com o botão direito do mouse e, em seguida, clique em **mover** \> **outros** \> **contatos**da pasta.</span><span class="sxs-lookup"><span data-stu-id="c6798-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="c6798-277">Para recuperar uma tarefa, clique com o botão direito do mouse e clique em **mover** \> **outras** \> **tarefas**da pasta.</span><span class="sxs-lookup"><span data-stu-id="c6798-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![Selecionar uma pasta para mover outros tipos de itens](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="c6798-279">Quando tiver terminado a recuperação de itens excluídos, clique com o botão direito do mouse no arquivo PST na barra de navegação à esquerda e selecione **fechar "nome do arquivo pst"**.</span><span class="sxs-lookup"><span data-stu-id="c6798-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="c6798-280">Return to top</span><span class="sxs-lookup"><span data-stu-id="c6798-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="c6798-281">Mais informações</span><span class="sxs-lookup"><span data-stu-id="c6798-281">More information</span></span>
<span data-ttu-id="c6798-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="c6798-282"></span></span>

- <span data-ttu-id="c6798-283">Pode ser possível para um usuário recuperar um item permanentemente excluído se o período de retenção do item excluído para o item não tiver expirado.</span><span class="sxs-lookup"><span data-stu-id="c6798-283">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired.</span></span> <span data-ttu-id="c6798-284">Como administrador, você pode ter especificado por quanto tempo os itens na pasta itens recuperáveis estão disponíveis para recuperação.</span><span class="sxs-lookup"><span data-stu-id="c6798-284">As an admin you may have specified how long items in the Recoverable Items folder are available for recovery.</span></span> <span data-ttu-id="c6798-285">Por exemplo, pode haver uma política que exclua tudo o que está na pasta itens excluídos de um usuário por 30 dias e outra política que permite aos usuários recuperar itens na pasta itens recuperáveis por até mais 14 dias.</span><span class="sxs-lookup"><span data-stu-id="c6798-285">For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days.</span></span> <span data-ttu-id="c6798-286">No entanto, depois de 14 dias, você ainda poderá recuperar um item na caixa de correio de um usuário usando os procedimentos deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c6798-286">However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="c6798-287">Os usuários podem recuperar um item excluído se ele não tiver sido eliminado e se seu período de retenção não estiver expirado.</span><span class="sxs-lookup"><span data-stu-id="c6798-287">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired.</span></span> <span data-ttu-id="c6798-288">Para ajudar os usuários a recuperar itens excluídos em suas caixas de correio, aponte-os para um dos seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="c6798-288">To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="c6798-289">Recuperar itens excluídos no Outlook para Windows</span><span class="sxs-lookup"><span data-stu-id="c6798-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="c6798-290">Recuperar itens excluídos no Outlook 2010</span><span class="sxs-lookup"><span data-stu-id="c6798-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="c6798-291">Recuperar itens ou emails excluídos no Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="c6798-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="c6798-292">Restaurar mensagens de email excluídas no Outlook na Web</span><span class="sxs-lookup"><span data-stu-id="c6798-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="c6798-293">Recuperar um contato excluído no Outlook</span><span class="sxs-lookup"><span data-stu-id="c6798-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="c6798-294">Restaurar mensagens de email excluídas no Outlook.com</span><span class="sxs-lookup"><span data-stu-id="c6798-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="c6798-295">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="c6798-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

