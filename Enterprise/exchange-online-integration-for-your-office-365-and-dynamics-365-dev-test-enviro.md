---
title: Integração com o Exchange Online para seu ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: 'Resumo: Use este guia de laboratório de teste para habilitar a integração do Dynamics 365 para o Exchange Online em sua assinatura de avaliação do Office 365.'
ms.openlocfilehash: be79f58f448799bba9c4a9ee51350f198d721e0d
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574015"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="9bd8a-103">Integração com o Exchange Online para seu ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9bd8a-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="9bd8a-104">**Resumo:** Use este guia de laboratório de teste para habilitar a integração do Dynamics 365 para o Exchange Online em sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="9bd8a-105">Um uso valioso do Microsoft Dynamics 365 é armazenar todas as comunicações do cliente em um único local, para que qualquer pessoa com as permissões apropriadas possa ver todos os registros de cliente relevantes.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-105">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records.</span></span> <span data-ttu-id="9bd8a-106">Por exemplo, exibir todos os emails associados a um contato, conta, oportunidade ou caso específico.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-106">For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="9bd8a-107">Para armazenar emails e outros registros de mensagens no Dynamics 365, você precisa sincronizar o sistema de email com o Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-107">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365.</span></span> <span data-ttu-id="9bd8a-108">Sincronização no servidor é o método de escolha para a sincronização de email.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-108">Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="9bd8a-109">Use este guia de laboratório de teste para configurar e demonstrar como o cliente do Exchange Online e do Outlook online pode aproveitar as informações armazenadas no Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="9bd8a-110">Fase 1: compilar o ambiente de desenvolvimento/teste do Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9bd8a-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="9bd8a-111">Use as instruções no [ambiente de desenvolvimento/teste do office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md) para criar uma versão de empresa leve ou simulada de um ambiente de desenvolvimento/teste do Office 365 e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9bd8a-112">A configuração deste artigo não requer o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do Active Directory (AD) do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-112">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest.</span></span> <span data-ttu-id="9bd8a-113">É fornecido aqui como uma opção para que você possa experimentar o Office 365 e o Dynamics 365 em um ambiente que represente uma organização típica</span><span class="sxs-lookup"><span data-stu-id="9bd8a-113">It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="9bd8a-114">Fase 2: configurar e demonstrar a integração do Dynamics 365 no Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9bd8a-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="9bd8a-115">Use estas etapas para configurar a caixa de correio do administrador global para a integração do Dynamics 365 e do Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="9bd8a-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="9bd8a-116">Usando uma sessão privada do navegador, acesse [http://admin.microsoft.com](http://admin.microsoft.com) e entre usando sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-116">Using a private session of your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="9bd8a-117">Na home page do **Microsoft Office** , clique no bloco **email** .</span><span class="sxs-lookup"><span data-stu-id="9bd8a-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="9bd8a-118">Na guia novo **email** no navegador, clique em **novo** e observe como o canto inferior do painel abaixo da caixa para digitar uma mensagem tem um ícone para meus modelos.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message has an icon for My Templates.</span></span>
    
     ![Uma nova mensagem de email em branco sem a integração com o Dynamics 365.](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="9bd8a-120">Clique \*\*\*\* em descartar e deixe a guia **email** aberta.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="9bd8a-121">Clique na guia **Microsoft Office Home** no navegador e, em seguida, clique no bloco **administrador** .</span><span class="sxs-lookup"><span data-stu-id="9bd8a-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="9bd8a-122">Na navegação à esquerda da guia **centro de administração do Office** , clique em **centros de administração > Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="9bd8a-123">Na nova guia do **dynamics 365** no navegador, na lista de instâncias do Dynamics 365, clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="9bd8a-124">Na nova guia **Administração** no navegador, na barra de navegação, clique na seta para baixo ao lado de **configurações**e clique em **configuração de email** em **sistema**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="9bd8a-125">Na página **configuração de email** , clique em **definições de configuração de email**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="9bd8a-126">Na guia **email** da caixa de diálogo **configurações do sistema** , altere **compromissos, contatos e tarefas** para a **sincronização do lado do servidor**e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="9bd8a-127">Na página **configuração de email** , clique em **caixas de correio**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="9bd8a-128">Selecione o nome do administrador global do Office 365 na coluna marca de seleção à esquerda, clique em **aplicar configurações de email padrão** na barra de ferramentas e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="9bd8a-129">Clique em **aprovar email** na barra de ferramentas e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="9bd8a-130">Selecione o nome do administrador global do Office 365 na coluna marca de seleção à esquerda, clique em **testar &amp; habilitar caixas de correio** na barra de ferramentas e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="9bd8a-131">Clique na guia abrir **email** e confirme se o administrador global recebeu uma mensagem de teste.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="9bd8a-132">ReTorne à guia caixas de correio ativas em **minhas caixas de correio** em seu navegador e atualize a página.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-132">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page.</span></span> <span data-ttu-id="9bd8a-133">As colunas **status do email de entrada** e status do email de **saída** devem ser definidas como **êxito** para o nome da conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-133">The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name.</span></span> <span data-ttu-id="9bd8a-134">Observe que pode levar até 15 minutos para concluir os dois testes.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-134">Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="9bd8a-135">Use estas etapas para instalar o aplicativo Dynamics 365 para Outlook e demonstrar os recursos do Dynamics 365 dentro da caixa de correio do administrador global:</span><span class="sxs-lookup"><span data-stu-id="9bd8a-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="9bd8a-136">Na guia caixas de correio de **minhas caixas** de correio ativas no navegador, clique na seta para baixo ao lado de **configurações**e, em seguida, clique em **aplicativo Dynamics 365 para Outlook** em **sistema**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="9bd8a-137">Na página **introdução ao aplicativo Microsoft Dynamics 365 para Outlook** , clique no nome do administrador global e, em seguida, clique em **Adicionar aplicativo ao Outlook**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-137">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**.</span></span> <span data-ttu-id="9bd8a-138">A coluna **status** é alterada para **pendente**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-138">The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="9bd8a-139">Atualize a página até que o status mude para **adicionado ao Outlook**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-139">Refresh the page until the status changes to **Added to Outlook**.</span></span> <span data-ttu-id="9bd8a-140">Observe que pode levar até 15 minutos para concluir essa configuração.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-140">Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="9bd8a-141">Clique na guia **email** do navegador e feche-o.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="9bd8a-142">Clique na guia **Microsoft Office Home** no navegador e, em seguida, clique no bloco **email** .</span><span class="sxs-lookup"><span data-stu-id="9bd8a-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="9bd8a-143">Na guia novo **email** no navegador, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-143">On the new **Mail** tab in your browser, click **New**.</span></span> <span data-ttu-id="9bd8a-144">Observe que o canto inferior do painel abaixo da caixa para digitar uma mensagem agora tem um ícone para o Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-144">Notice that the bottom corner of the pane below the box for typing a message now has an icon for Dynamics 365.</span></span>
    
     ![Uma nova mensagem de email em branco com a integração com o Dynamics 365, mostrando o novo ícone.](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="9bd8a-146">Clique no ícone do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-146">Click the Dynamics 365 icon.</span></span> <span data-ttu-id="9bd8a-147">Você verá um painel do **Dynamics 365** , no qual você pode acompanhar este email ou acessar modelos, especificações ou artigos de vendas.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-147">You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="9bd8a-148">No campo **para** da mensagem de email, digite **Alex.y.Wu@outlook.com**e clique em **repetir** no painel do **Dynamics 365** .</span><span class="sxs-lookup"><span data-stu-id="9bd8a-148">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane.</span></span> <span data-ttu-id="9bd8a-149">Você verá uma seção de **destinatários** no painel do **Dynamics 365** com informações sobre Alex Wu, um contato do aplicativo de vendas fornecido com os dados de exemplo para sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-149">You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![O painel de informações do Dynamics 365 para um contato de vendas armazenado no Dynamics 365.](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="9bd8a-151">Clique \*\*\*\* em descartar.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="9bd8a-152">Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="9bd8a-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9bd8a-153">Confira também
</span><span class="sxs-lookup"><span data-stu-id="9bd8a-153">See Also</span></span>

[<span data-ttu-id="9bd8a-154">Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9bd8a-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="9bd8a-155">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="9bd8a-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
<span data-ttu-id="9bd8a-156">[Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="9bd8a-156">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="9bd8a-157">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="9bd8a-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="9bd8a-158">DirSync para o ambiente de desenvolvimento/ teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="9bd8a-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="9bd8a-159">Gerenciamento de assinaturas do Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="9bd8a-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="9bd8a-160">Administração do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9bd8a-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


