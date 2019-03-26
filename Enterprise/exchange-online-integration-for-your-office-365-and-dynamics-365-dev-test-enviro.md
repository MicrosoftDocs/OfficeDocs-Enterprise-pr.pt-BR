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
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Integração com o Exchange Online para seu ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365

 **Resumo:** Use este guia de laboratório de teste para habilitar a integração do Dynamics 365 para o Exchange Online em sua assinatura de avaliação do Office 365.
  
Um uso valioso do Microsoft Dynamics 365 é armazenar todas as comunicações do cliente em um único local, para que qualquer pessoa com as permissões apropriadas possa ver todos os registros de cliente relevantes. Por exemplo, exibir todos os emails associados a um contato, conta, oportunidade ou caso específico.
  
Para armazenar emails e outros registros de mensagens no Dynamics 365, você precisa sincronizar o sistema de email com o Dynamics 365. Sincronização no servidor é o método de escolha para a sincronização de email.
  
Use este guia de laboratório de teste para configurar e demonstrar como o cliente do Exchange Online e do Outlook online pode aproveitar as informações armazenadas no Dynamics 365. 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>Fase 1: compilar o ambiente de desenvolvimento/teste do Office 365 e Dynamics 365

Use as instruções no [ambiente de desenvolvimento/teste do office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md) para criar uma versão de empresa leve ou simulada de um ambiente de desenvolvimento/teste do Office 365 e Dynamics 365.
  
> [!NOTE]
> A configuração deste artigo não requer o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do Active Directory (AD) do Windows Server. É fornecido aqui como uma opção para que você possa experimentar o Office 365 e o Dynamics 365 em um ambiente que represente uma organização típica 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>Fase 2: configurar e demonstrar a integração do Dynamics 365 no Exchange Online

Use estas etapas para configurar a caixa de correio do administrador global para a integração do Dynamics 365 e do Exchange Online:
  
1. Usando uma sessão privada do navegador, acesse [http://admin.microsoft.com](http://admin.microsoft.com) e entre usando sua conta de administrador global do Office 365.
    
2. Na home page do **Microsoft Office** , clique no bloco **email** .
    
3. Na guia novo **email** no navegador, clique em **novo** e observe como o canto inferior do painel abaixo da caixa para digitar uma mensagem tem um ícone para meus modelos.
    
     ![Uma nova mensagem de email em branco sem a integração com o Dynamics 365.](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. Clique **** em descartar e deixe a guia **email** aberta.
    
5. Clique na guia **Microsoft Office Home** no navegador e, em seguida, clique no bloco **administrador** .
    
6. Na navegação à esquerda da guia **centro de administração do Office** , clique em **centros de administração > Dynamics 365**.
    
7. Na nova guia do **dynamics 365** no navegador, na lista de instâncias do Dynamics 365, clique em **abrir**.
    
8. Na nova guia **Administração** no navegador, na barra de navegação, clique na seta para baixo ao lado de **configurações**e clique em **configuração de email** em **sistema**.
    
9.  Na página **configuração de email** , clique em **definições de configuração de email**.
    
10. Na guia **email** da caixa de diálogo **configurações do sistema** , altere **compromissos, contatos e tarefas** para a **sincronização do lado do servidor**e clique em **OK**.
    
11. Na página **configuração de email** , clique em **caixas de correio**.
    
12. Selecione o nome do administrador global do Office 365 na coluna marca de seleção à esquerda, clique em **aplicar configurações de email padrão** na barra de ferramentas e, em seguida, clique em **OK**.
    
13. Clique em **aprovar email** na barra de ferramentas e clique em **OK**.
    
14. Selecione o nome do administrador global do Office 365 na coluna marca de seleção à esquerda, clique em **testar &amp; habilitar caixas de correio** na barra de ferramentas e, em seguida, clique em **OK**.
    
15. Clique na guia abrir **email** e confirme se o administrador global recebeu uma mensagem de teste.
    
16. ReTorne à guia caixas de correio ativas em **minhas caixas de correio** em seu navegador e atualize a página. As colunas **status do email de entrada** e status do email de **saída** devem ser definidas como **êxito** para o nome da conta de administrador global. Observe que pode levar até 15 minutos para concluir os dois testes.
    
Use estas etapas para instalar o aplicativo Dynamics 365 para Outlook e demonstrar os recursos do Dynamics 365 dentro da caixa de correio do administrador global:
  
1. Na guia caixas de correio de **minhas caixas** de correio ativas no navegador, clique na seta para baixo ao lado de **configurações**e, em seguida, clique em **aplicativo Dynamics 365 para Outlook** em **sistema**.
    
2. Na página **introdução ao aplicativo Microsoft Dynamics 365 para Outlook** , clique no nome do administrador global e, em seguida, clique em **Adicionar aplicativo ao Outlook**. A coluna **status** é alterada para **pendente**.
    
3. Atualize a página até que o status mude para **adicionado ao Outlook**. Observe que pode levar até 15 minutos para concluir essa configuração.
    
4. Clique na guia **email** do navegador e feche-o.
    
5. Clique na guia **Microsoft Office Home** no navegador e, em seguida, clique no bloco **email** .
    
6. Na guia novo **email** no navegador, clique em **novo**. Observe que o canto inferior do painel abaixo da caixa para digitar uma mensagem agora tem um ícone para o Dynamics 365.
    
     ![Uma nova mensagem de email em branco com a integração com o Dynamics 365, mostrando o novo ícone.](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. Clique no ícone do Dynamics 365. Você verá um painel do **Dynamics 365** , no qual você pode acompanhar este email ou acessar modelos, especificações ou artigos de vendas.
    
8. No campo **para** da mensagem de email, digite **Alex.y.Wu@outlook.com**e clique em **repetir** no painel do **Dynamics 365** . Você verá uma seção de **destinatários** no painel do **Dynamics 365** com informações sobre Alex Wu, um contato do aplicativo de vendas fornecido com os dados de exemplo para sua assinatura de avaliação.
    
     ![O painel de informações do Dynamics 365 para um contato de vendas armazenado no Dynamics 365.](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. Clique **** em descartar.

> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
    
## <a name="see-also"></a>Confira também


[Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para o ambiente de desenvolvimento/ teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)

[Gerenciamento de assinaturas do Dynamics 365 (online)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Administração do Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


