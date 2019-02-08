---
title: Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento e teste do Office 365
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
description: 'Resumo: Configure e demonstre a Descoberta Eletrônica Avançada do Office 365 com dados de amostra no seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897504"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento e teste do Office 365

 **Resumo:** Configure e demonstre a Descoberta Eletrônica Avançada do Office 365 com dados de amostra no seu ambiente de desenvolvimento e teste do Office 365.
  
Descoberta eletrônica avançada do Office 365 permite localizar rapidamente e analisar informações relevantes entre os dados armazenados no Office 365, incluindo email e documentos. Isso pode salvar uma enorme quantidades de tempo e despesas, especialmente nas situações de litígio. Para obter mais informações, consulte [eDiscovery avançadas do Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Com as instruções neste artigo, você cria um pequeno conjunto de dados para uma disputa de contrato fictícia e o analisa com a Descoberta Eletrônica Avançada.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: Criar seu ambiente de desenvolvimento/teste do Office 365

Se você quiser testar eDiscovery avançado de forma leve com os requisitos mínimos, siga as instruções na fase 2 e a fase 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar eDiscovery avançada em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testar eDiscovery avançada não exige o ambiente simulado enterprise, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa realizar testes e experimentação em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Fase 2: Criar dados de exemplo para a Descoberta Eletrônica Avançada

Neste procedimento, você criará mensagens de email que, mais tarde, serão analisadas em um caso de Descoberta Eletrônica Avançada.
  
1. Abra o Internet Explorer e entrar no [https://outlook.com](https://outlook.com) a conta do Outlook que você criou na fase 2 do[ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
    
  - Se estiver usando o ambiente de desenvolvimento e teste leve, abra uma sessão particular do Internet Explorer e entre com o seu computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento e teste de enterprise simulado, usar o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)) para se conectar à máquina virtual CLIENT1 e entrar em CLIENT1.
    
2. Na guia **Email do Outlook**, clique em **Novo**.
    
3. Em **para**, digite o endereço de email da conta User6 de sua assinatura de avaliação ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
4. Para o assunto, digite **Email de teste 1**.
    
5. No corpo, digite **Rascunho do contrato com a Tailspin** e clique em **Enviar**.
    
6. Na guia **Email do Outlook**, clique em **Novo**.
    
7. Em **Para**, digite o endereço de email da conta Usuário:6 da sua assinatura de teste.
    
8. Para o assunto, digite **Email de teste 2**.
    
9. No corpo, digite **Reunião de almoço com a Tailspin** e clique em **Enviar**.
    
10. Na guia **Email do Outlook**, clique em **Novo**.
    
11. Em **Para**, digite o endereço de email da conta Usuário:6 da sua assinatura de teste.
    
12. Para o assunto, digite **Email de teste 3**.
    
13. No corpo, digite **Desacordo no contrato com a Tailspin** e clique em **Enviar**.
    
14. Clique no ícone de usuário no canto superior direito e clique em **Sair**.
    
15. Abra uma nova guia e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) com o nome da conta e a senha da conta de User6 de sua assinatura de avaliação.
    
16. Na guia do **portal do Office 365**, clique em **Email**.
    
17. Na guia **email - User6 - Outlook** , verifique que User6 recebeu todos os três emails da conta de email do Outlook.
    
18. Volte para a **guia do portal do Office 365** de Usuário6.
    
19. Clique no ícone de usuário no canto superior direito e depois clique em **Sair.**
    
Neste procedimento, você criará dois documentos do Word que, mais tarde, serão analisados em um caso de Descoberta Eletrônica Avançada.
  
1. Na página do **Office**, clique em **Entrar** e entre com as credenciais da sua conta de administrador global.
    
2. Em uma nova guia, acessar a URL do seu site do SharePoint de produção: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. Na guia **Conjunto de sites de produção**, em **Documentos**, clique em **Novo > Documento do Word**.
    
4. Na página do **Word Online**, digite **Contrato de rascunho com a Tailspin**, aguarde até que **Salvo** apareça no título e feche a guia da página do **Word Online**.
    
5. Na guia **Conjunto de sites de produção**, em **Documentos**, clique em **Novo > Documento do Word**.
    
6. 	Na guia do **Word Online**, digite **Notas da disputa contratual com a Tailspin**, aguarde até que **Salvo** apareça no título e feche a guia do **Word Online**.
    
7. Na guia **Conjunto de sites de produção**, você verá **Documento** e **Documento1** na lista de documentos.
    
8. Feche a guia **Coleção do site de produção**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: Uso eDiscovery avançadas para uma disputa legal

Infelizmente, uma contestação contrato entre sua organização e Tailspin Toys atingiu o ponto de ações legais. Neste procedimento, você cria e configurar um caso de eDiscovery avançadas para procurar e analisar o email e documentos que contêm o texto "Contrato Tailspin".
  
O processo de uso da Descoberta Eletrônica Avançada é o seguinte:
  
- Criar uma pesquisa na segurança &amp; Centro de conformidade, analisar seus resultados e prepare os resultados para eDiscovery avançado.
    
- Criar e configurar um caso de Descoberta Eletrônica Avançada e analisar os resultados da pesquisa.
    
Neste procedimento, você cria uma pesquisa na segurança &amp; conformidade center para o "Contrato Tailspin", procure os resultados e, em seguida, preparar os resultados eDiscovery avançado.
  
1. Na guia do **portal do Office 365**, clique em **Admin**.
    
2. Na navegação à esquerda da guia Centro de administração, clique em **Centros de administração > Conformidade**.
    
3. Sobre o **segurança &amp; conformidade** guia, clique em **permissões**.
    
4. Na lista **Permissões**, clique duas vezes em **Gerenciamento da Organização**.
    
5. Na janela **Grupo de Função**, em **Membros**, clique no sinal de adição.
    
6. Na janela **Selecionar Membros**, clique duas vezes o nome da sua conta de administrador e depois clique em **OK**.
    
7. Na janela **Grupo de Funções**, clique em **Salvar**.
    
8. Na lista **Permissões**, clique duas vezes em **Gerente de Descoberta Eletrônica**.
    
9. Na janela **Grupo de Função**, em **Administrador de Descoberta Eletrônica**, clique no ícone de adição.
    
10. Na janela **Selecionar Membros**, clique duas vezes o nome da sua conta de administrador e depois clique em **OK**.
    
11. Na janela **Grupo de Funções**, clique em **Salvar**.
    
12. No painel de navegação esquerdo, clique em **pesquisa &amp; pesquisa de conteúdo investigação gt _**.
    
13. Clique no ícone de adição para adicionar uma pesquisa.
    
14. Na janela **Nova pesquisa**, digite **Pesquisa de contrato com a Tailspin** em **Nome**.
    
15. Em **Onde deseja procurar?**, clique em **Pesquisar em todos os lugares**, selecione **Exchange**, **SharePoint** e **Pastas Públicas** e depois clique em **Avançar**.
    
16. Em **O que você deseja que procuremos?**, digite **Contrato com a Tailspin** e clique em **Pesquisar**.
    
17. Na lista de pesquisas, clique no nome **Pesquisa de contrato com a Tailspin**.
    
18. No painel de **pesquisa de contrato Tailspin** , clique em **resultados da pesquisa de visualização** em **resultados**. Você deverá ver uma janela listando os dois documentos sobre o site do SharePoint de produção ( **documento** e **Document1**) e os emails de **e-mail de teste 1** e **3 de e-mail de teste** para User6. Feche a janela.
    
19. No painel **Pesquisa de conteúdo**, em **Analisar os resultados com a Descoberta Eletrônica Avançada**, clique em **Visualizar resultados para análise**.
    
20. Na janela **Preparar os resultados da pesquisa para a pesquisa de contrato com a Tailspin**, clique em **Preparar** e aguarde a sua conclusão.
    
Neste procedimento, você criará um novo caso de Descoberta Eletrônica Avançada e analisará os resultados da pesquisa de contrato com a Tailspin.
  
1. No painel de navegação esquerdo, clique em **Descoberta eletrônica** em **pesquisa &amp; investigação**.
    
2. No painel **Descoberta Eletrônica**, clique em **Ir para Descoberta Eletrônica Avançada**.
    
3. Na guia **Descoberta Eletrônica Avançada**, clique no ícone de adição para adicionar um novo caso.
    
4. 	No painel **Adicionar caso**, digite **Disputa contratual com a Tailspin** em **Nome** e depois clique em **OK**. Aguarde até que o caso seja criado.
    
5. Clique duas vezes no caso **Disputa contratual com a Tailspin** na lista. 
    
6. Na lista do **contêiner** , clique no contêiner de **pesquisa de contrato Tailspin** e, em seguida, clique em **processar**. Aguarde o processamento ser concluída.
    
7. Quando a mensagem **Processo: concluído** aparecer na parte inferior da janela, clique em **Resumo do processo** na navegação à esquerda para ver um resumo.
    
8. Na navegação superior, clique em **Analisar**.
    
9. Na página **Configuração**, em **Temas**, digite **3** em **Número máximo de temas**.
    
10. Clique em **Analisar** e aguarde concluir a análise. Você deverá ver uma série de gráficos de pizza com a análise da população de destino, documentos, emails e anexos. Para obter mais informações, consulte [Exibindo analisar resultados](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Agora, você pode usar esse ambiente para criar novo conteúdo, novas pesquisas e casos e também para continuar os testes com a Descoberta Eletrônica Avançada no Office 365.
  
## <a name="see-also"></a>Confira também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para o ambiente de desenvolvimento/ teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Descoberta Eletrônica Avançada do Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


