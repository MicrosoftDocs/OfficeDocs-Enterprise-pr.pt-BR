---
title: "Integração do Exchange Online para seu ambiente de desenvolvimento e teste do Office 365 e Dynamics 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- mar17entnews
- Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "Resumo: Use este guia de laboratório de teste para habilitar a integração de Dynamics 365 para Exchange Online em sua assinatura de avaliação do Office 365."
ms.openlocfilehash: 9cecd13f0ffc3c2822ac6c66a3bde9c9e6a3c798
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="17c31-103">Integração do Exchange Online para seu ambiente de desenvolvimento e teste do Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="17c31-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="17c31-104">**Resumo:** Use este guia de laboratório de teste para habilitar a integração de Dynamics 365 para Exchange Online em sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="17c31-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="17c31-p101">Um uso valioso do Microsoft Dynamics 365 é armazenar todas as comunicações de cliente em um único local, para que qualquer pessoa com as permissões apropriadas pode ver todos os registros do cliente relevante. Por exemplo, exiba todos os emails associados a um determinado contato, conta, oportunidade ou caso.</span><span class="sxs-lookup"><span data-stu-id="17c31-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="17c31-p102">Para armazenar o email e outros registros de mensagens no Dynamics 365, você precisa sincronizar seu sistema de email com Dynamics 365. Sincronização do servidor é o método de escolha para sincronização de email.</span><span class="sxs-lookup"><span data-stu-id="17c31-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="17c31-109">Use este guia de laboratório de teste para configurar e demonstrar como Exchange Online e o cliente Outlook Online podem aproveitar as informações armazenadas no Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="17c31-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="17c31-110">Fase 1: Criar o ambiente de desenvolvimento e teste do Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="17c31-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="17c31-111">Use as instruções no [Office 365 e o ambiente de desenvolvimento e teste do Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md) para criar uma versão de empresa leve ou simulado de um ambiente de desenvolvimento e teste do Office 365 e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="17c31-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="17c31-p103">A configuração neste artigo não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD (Active Directory). Ele é fornecido aqui como uma opção para que você pode experimentar com o Office 365 e Dynamics 365 em um ambiente que representa uma organização típica</span><span class="sxs-lookup"><span data-stu-id="17c31-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="17c31-114">Fase 2: Configurar e demonstrar a integração do Dynamics 365 no Exchange Online</span><span class="sxs-lookup"><span data-stu-id="17c31-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="17c31-115">Use estas etapas para configurar a caixa de correio do administrador global para a integração do Dynamics 365 e o Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="17c31-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="17c31-116">Usando uma sessão particular do seu navegador, vá para [http://portal.office.com](http://portal.office.com) e entrar usando sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="17c31-116">Using a private session of your browser, go to [http://portal.office.com](http://portal.office.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="17c31-117">Na página **Inicial do Microsoft Office** , clique no lado do **email** .</span><span class="sxs-lookup"><span data-stu-id="17c31-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="17c31-118">Na guia **email** nova no seu navegador, clique em **novo** e observe como o canto inferior do painel abaixo da caixa para digitar uma mensagem contém um ícone para Meus modelos.</span><span class="sxs-lookup"><span data-stu-id="17c31-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message contains an icon for My Templates.</span></span>
    
     ![Nova mensagem de email em branco sem a integração com o Dynamics 365.](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="17c31-120">Clique em **Descartar** e deixe a guia **email** aberto.</span><span class="sxs-lookup"><span data-stu-id="17c31-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="17c31-121">Clique na guia **Página inicial do Microsoft Office** no seu navegador e, em seguida, clique no lado de **Administração** .</span><span class="sxs-lookup"><span data-stu-id="17c31-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="17c31-122">No painel de navegação à esquerda da guia **Centro de administração do Office** , clique em **centrais de Admin > Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="17c31-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="17c31-123">Na guia **Dynamics 365** nova em seu navegador, na lista de instâncias de Dynamics 365, clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="17c31-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="17c31-124">Na guia **Administração** nova em seu navegador, na barra de navegação, clique na seta ao lado de **configurações**e clique em **Configuração de Email** em **sistema**.</span><span class="sxs-lookup"><span data-stu-id="17c31-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="17c31-125">Na página **Configuração de Email** , clique em **Definições de configuração de Email**.</span><span class="sxs-lookup"><span data-stu-id="17c31-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="17c31-126">Na guia **Email** na caixa de diálogo **Configurações do sistema** , altere **compromissos, contatos e tarefas** para **Sincronização do lado do servidor**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="17c31-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="17c31-127">Na página **Configuração de Email** , clique em **caixas de correio**.</span><span class="sxs-lookup"><span data-stu-id="17c31-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="17c31-128">Selecione o nome de administrador global do Office 365 na coluna a marca de seleção à esquerda, clique em **Aplicar configurações de Email padrão** , na barra de ferramentas e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="17c31-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="17c31-129">Clique em **Aprovar Email** na barra de ferramentas e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="17c31-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="17c31-130">Selecione o nome de administrador global do Office 365 na coluna a marca de seleção à esquerda, clique em **teste &amp; habilitar caixas de correio** na ferramenta de barra e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="17c31-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="17c31-131">Clique na guia open **Mail** e confirme que o administrador global recebeu uma mensagem de teste.</span><span class="sxs-lookup"><span data-stu-id="17c31-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="17c31-p104">Volte à guia **Caixas de correio meu ativa as caixas de correio** no seu navegador e atualize a página. As colunas de **Status de Email de entrada** e o **Status de Email de saída** devem ser definidas com **sucesso** para o nome da conta de administrador global. Observe que pode demorar até 15 minutos para concluir os dois testes.</span><span class="sxs-lookup"><span data-stu-id="17c31-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="17c31-135">Use estas etapas para instalar o aplicativo do Dynamics 365 para o Outlook e demonstrar os recursos do Dynamics 365 dentro da caixa de correio do administrador global:</span><span class="sxs-lookup"><span data-stu-id="17c31-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="17c31-136">Na guia **Caixas de correio meu ativa as caixas de correio** no seu navegador, clique na seta ao lado de **configurações**e clique em **Aplicativo do Dynamics 365 para o Outlook** em **sistema**.</span><span class="sxs-lookup"><span data-stu-id="17c31-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="17c31-p105">Na página **Introdução ao Microsoft Dynamics 365 App para o Outlook** , clique no nome do administrador global e, em seguida, clique em **Adicionar aplicativo para Outlook**. A coluna **Status** muda para **pendente**.</span><span class="sxs-lookup"><span data-stu-id="17c31-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="17c31-p106">Atualize a página até que o status muda para **foram adicionados ao Outlook**. Observe que pode demorar até 15 minutos para completar esta configuração.</span><span class="sxs-lookup"><span data-stu-id="17c31-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="17c31-141">Clique na guia **email** no seu navegador e fechá-lo.</span><span class="sxs-lookup"><span data-stu-id="17c31-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="17c31-142">Clique na guia **Página inicial do Microsoft Office** no seu navegador e, em seguida, clique no lado de **email** .</span><span class="sxs-lookup"><span data-stu-id="17c31-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="17c31-p107">Na guia **email** nova no seu navegador, clique em **novo**. Observe que o canto inferior do painel abaixo da caixa para digitar uma mensagem agora contém um ícone para Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="17c31-p107">On the new **Mail** tab in your browser, click **New**. Notice that the bottom corner of the pane below the box for typing a message now contains an icon for Dynamics 365.</span></span>
    
     ![Nova mensagem de email em branco com a integração com o Dynamics 365, mostrando o novo ícone.](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="17c31-p108">Clique no ícone do Dynamics 365. Você verá um painel **Dynamics 365** , do qual você pode controlar esse modelos de email ou de acesso, especificações ou artigos.</span><span class="sxs-lookup"><span data-stu-id="17c31-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="17c31-p109">No campo **para** da mensagem de email, digite **alex.y.wu@outlook.com**e, em seguida, clique em **Repetir** no painel **Dynamics 365** . Você deverá ver uma seção de **destinatários** no painel **Dynamics 365** com informações sobre Alex Wu, um contato do aplicativo de venda que foi fornecido com os dados de amostra para sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="17c31-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![Painel de informações do Dynamics 365 de um contato de vendas armazenado nesse serviço.](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="17c31-151">Clique em **Descartar**.</span><span class="sxs-lookup"><span data-stu-id="17c31-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="17c31-152">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="17c31-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="17c31-153">See Also</span><span class="sxs-lookup"><span data-stu-id="17c31-153">See Also</span></span>

[<span data-ttu-id="17c31-154">Office 365 e o ambiente de desenvolvimento e teste do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="17c31-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="17c31-155">Adoção de nuvem Test Lab Guides (TLGs)</span><span class="sxs-lookup"><span data-stu-id="17c31-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="17c31-156">Ambiente de desenvolvimento e teste de configuração de base</span><span class="sxs-lookup"><span data-stu-id="17c31-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="17c31-157">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="17c31-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="17c31-158">DirSync para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="17c31-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="17c31-159">Gerenciamento de assinatura do Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="17c31-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="17c31-160">Administrando o Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="17c31-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


