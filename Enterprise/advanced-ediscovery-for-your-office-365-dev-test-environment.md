---
title: "Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento e teste do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: "Resumo: Configurar e demonstrar o eDiscovery avançadas do Office 365 com dados de exemplo no seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: c55a466f05eba4e9f06ce2930dfc7c762d7fceae
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento e teste do Office 365

 **Resumo:** Configurar e demonstrar o eDiscovery avançadas do Office 365 com dados de exemplo no seu ambiente de desenvolvimento e teste do Office 365.
  
Descoberta eletrônica avançada do Office 365 permite que você rapidamente encontrar e analisar informações relevantes entre os dados armazenados no Office 365, incluindo email e documentos. Isso pode salvar uma enorme quantidades de tempo e despesas, especialmente nas situações de litígio. Para obter mais informações, consulte [eDiscovery avançadas do Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Com as instruções neste artigo, você cria um pequeno conjunto de dados para uma disputa de contrato fictícia e o analisa com a Descoberta Eletrônica Avançada.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: Criar seu ambiente de desenvolvimento e teste do Office 365

Se você quiser testar eDiscovery avançado de forma leve com os requisitos mínimos, siga as instruções na fase 2 e a fase 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar eDiscovery avançada em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testar eDiscovery avançada não exige o ambiente simulado enterprise, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa realizar testes e experimentação em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Fase 2: Criar dados de exemplo para a Descoberta Eletrônica Avançada

Neste procedimento, você criará mensagens de email que, mais tarde, serão analisadas em um caso de Descoberta Eletrônica Avançada.
  
1. Abra o Internet Explorer e entrar no [https://outlook.com](https://outlook.com) para a conta do Outlook que você criou na fase 2 do[ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
    
  - Se estiver usando o ambiente de desenvolvimento e teste leve, abra uma sessão particular do Internet Explorer e entre com o seu computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento e teste de enterprise simulado, use o portal Azure ([https://portal.azure.com](https://portal.azure.com)) para se conectar à máquina virtual CLIENT1 e entrar em CLIENT1.
    
2. Na guia **Email do Outlook** , clique em **novo**.
    
3. Em **para**, digite o endereço de email da conta User6 de sua assinatura de avaliação ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
4. Para o assunto, digite **o email de teste 1**.
    
5. No corpo, digite **Tailspin rascunho de contrato**e clique em **Enviar**.
    
6. Na guia **Email do Outlook** , clique em **novo**.
    
7. Na caixa **para**, digite o endereço de email da conta User6 de sua assinatura de avaliação.
    
8. Para o assunto, digite **o email de teste 2**.
    
9. No corpo, digite **Tailspin almoço reunião**e, em seguida, clique em **Enviar**.
    
10. Na guia **Email do Outlook** , clique em **novo**.
    
11. Na caixa **para**, digite o endereço de email da conta User6 de sua assinatura de avaliação.
    
12. Para o assunto, digite **o email de teste 3**.
    
13. No corpo, digite **divergência de contrato Tailspin**e, em seguida, clique em **Enviar**.
    
14. Clique no ícone de usuário no canto superior direito e clique em **Sair**.
    
15. Abra uma nova guia e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) com o nome da conta e a senha da conta de User6 de sua assinatura de avaliação.
    
16. Na guia **portal do Office 365** , clique em **email**.
    
17. Na guia **email - User6 - Outlook** , verifique se que o User6 recebidas todos os três e-mails de conta de email do Outlook.
    
18. Alterne para a **guia portal do Office 365** para User6.
    
19. Clique no ícone de usuário no canto superior direito e, em seguida, clique em **desconectá-.**
    
Neste procedimento, você criará dois documentos do Word que, mais tarde, serão analisados em um caso de Descoberta Eletrônica Avançada.
  
1. Na página do **Office** , clique em **entrar,** logon com as credenciais da sua conta de administrador global.
    
2. Em uma nova guia, acessar a URL do seu site do SharePoint de produção: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. Na guia **conjunto de sites de produção** , em **documentos**, clique em **New > documento do Word**.
    
4. Na página **Online do Word** , digite **contrato de rascunho Tailspin**, aguarde até que ele exibe **Saved** no título e feche a guia de página **Online do Word** .
    
5. Na guia **conjunto de sites de produção** , em **documentos**, clique em **New > documento do Word**.
    
6. Na guia **On-line do Word** , digite **Tailspin contrato contestação observações**, aguarde até que ele exibe **Saved** no título e feche a guia **Word Online** .
    
7. Na guia **conjunto de sites de produção** , você deverá ver o **documento** e **Document1** na lista de documentos.
    
8. Feche a guia de **conjunto de sites de produção** .
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: Uso eDiscovery avançadas para uma disputa legal

Infelizmente, uma contestação contrato entre sua organização e Tailspin Toys atingiu o ponto de ações legais. Neste procedimento, você cria e configurar um caso de eDiscovery avançadas para procurar e analisar o email e documentos que contêm o texto "Contrato Tailspin".
  
O processo de uso da Descoberta Eletrônica Avançada é o seguinte:
  
- Criar uma pesquisa na segurança &amp; Centro de conformidade, analisar seus resultados e prepare os resultados para eDiscovery avançado.
    
- Criar e configurar um caso de Descoberta Eletrônica Avançada e analisar os resultados da pesquisa.
    
Neste procedimento, você cria uma pesquisa na segurança &amp; conformidade center para o "Contrato Tailspin", procure os resultados e, em seguida, preparar os resultados eDiscovery avançado.
  
1. Na guia **portal do Office 365** , clique em **Admin**.
    
2. No painel de navegação à esquerda da guia Administração Central, clique em **centrais de Admin > conformidade**.
    
3. Sobre o **segurança &amp; conformidade** guia, clique em **permissões**.
    
4. Na lista de **permissões** , clique duas vezes em **Gerenciamento da organização**.
    
5. Na janela do **Grupo de função** , em **membros**, clique no sinal de adição.
    
6. Na janela **Selecionar membros** , duas vezes no nome da sua conta de administrador e clique em **Okey**.
    
7. Na janela do **Grupo de função** , clique em **Salvar**.
    
8. Na lista de **permissões** , clique duas vezes em **Gerenciador de descoberta eletrônica**.
    
9. Na janela do **Grupo de função** , **eDiscovery administrador**, clique no ícone mais.
    
10. Na janela **Selecionar membros** , duas vezes no nome da sua conta de administrador e clique em **Okey**.
    
11. Na janela do **Grupo de função** , clique em **Salvar**.
    
12. No painel de navegação esquerdo, clique em **pesquisa &amp; investigação > pesquisa de conteúdo**.
    
13. Clique no ícone de adição para adicionar uma pesquisa.
    
14. Na janela **nova pesquisa** , digite a **pesquisa de contrato Tailspin** no **nome**.
    
15. No **onde você deseja com a aparência?**, clique em **Pesquisar em todos os lugares,** selecione **Exchange**, **SharePoint**e **As pastas públicas**e, em seguida, clique em **próxima.**
    
16. Em **que você deseja fazer conosco para procurar?**, digite **contrato Tailspin**e clique em **Pesquisar**.
    
17. Na lista de pesquisas, clique no nome de **pesquisa de contrato Tailspin** .
    
18. No painel de **pesquisa de contrato Tailspin** , clique em **resultados da pesquisa de visualização** em **resultados**. Você deverá ver uma janela listando os dois documentos sobre o site do SharePoint de produção ( **documento** e **Document1**) e os emails de **e-mail de teste 1** e **3 de e-mail de teste** para User6. Feche a janela.
    
19. No painel de **pesquisa de conteúdo** , **Analisar resultados com eDiscovery avançada**, clique em **resultados de visualização para análise**.
    
20. Na janela de **resultados para pesquisa de contrato Tailspin mais Prepare a pesquisa** , clique em **Preparar** e aguarde a conclusão.
    
Neste procedimento, você criará um novo caso de Descoberta Eletrônica Avançada e analisará os resultados da pesquisa de contrato com a Tailspin.
  
1. No painel de navegação esquerdo, clique em **Descoberta eletrônica** em **pesquisa &amp; investigação**.
    
2. No painel de **Descoberta eletrônica** , clique em **Ir para descoberta eletrônica avançada**.
    
3. Na guia **Avançado de descoberta eletrônica** , clique no ícone mais para adicionar um novo caso.
    
4. No painel de **caso de adicionar** , digite **disputa do contrato Tailspin** em **nome**e clique em **Okey**. Aguarde o caso a ser criado.
    
5. Clique duas vezes o caso de **disputa do contrato Tailspin** na lista.
    
6. Na lista do **contêiner** , clique no contêiner de **pesquisa de contrato Tailspin** e, em seguida, clique em **processar**. Aguarde o processamento ser concluída.
    
7. Quando **processo: concluído** aparece na parte inferior da janela, clique em **processo de resumo** no painel de navegação à esquerda para ver um resumo.
    
8. No painel de navegação superior, clique em **Analisar**.
    
9. Na página **instalação** , em **temas**, digite **3** no **número máximo de temas**.
    
10. Clique em **Analisar** e aguarde concluir a análise. Você deverá ver uma série de gráficos de pizza com a análise da população de destino, documentos, emails e anexos. Para obter mais informações, consulte [Exibindo analisar resultados](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Agora, você pode usar esse ambiente para criar novo conteúdo, novas pesquisas e casos e também para continuar os testes com a Descoberta Eletrônica Avançada no Office 365.
  
## <a name="see-also"></a>Veja também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento e teste de configuração de base](base-configuration-dev-test-environment.md)
  
[Ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Descoberta eletrônica avançada do Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


