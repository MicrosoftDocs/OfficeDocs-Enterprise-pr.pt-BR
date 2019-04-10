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
ms.openlocfilehash: b1cf2714f79d38e5a3349b331cee0862cd6aac52
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741448"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento e teste do Office 365

 **Resumo:** Configure e demonstre a Descoberta Eletrônica Avançada do Office 365 com dados de amostra no seu ambiente de desenvolvimento e teste do Office 365.
  
A descoberta eletrônica avançada do Office 365 permite que você encontre e analise rapidamente informações relevantes nos dados armazenados no Office 365, incluindo emails e documentos. Isso pode poupar enormes quantidades de tempo e despesas, especialmente em situações de litígio. Para saber mais, consulte [Descoberta Eletrônica Avançada do Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Com as instruções neste artigo, você cria um pequeno conjunto de dados para uma disputa de contrato fictícia e o analisa com a Descoberta Eletrônica Avançada.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa Visual para todos os artigos da pilha do guia do laboratório de teste do Office 365.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: Criar seu ambiente de desenvolvimento/teste do Office 365

Se você só quiser testar a descoberta eletrônica avançada de forma leve com os requisitos mínimos, siga as instruções na fase 2 e na fase 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar a descoberta eletrônica avançada em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> O teste de descoberta eletrônica avançada não requer o ambiente de empresa simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta dos serviços de domínio Active Directory (AD DS). Ele é fornecido aqui como uma opção para que você possa executar testes e experimentos em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Fase 2: Criar dados de exemplo para a Descoberta Eletrônica Avançada

Neste procedimento, você criará mensagens de email que, mais tarde, serão analisadas em um caso de Descoberta Eletrônica Avançada.
  
1. Abra o Internet Explorer e entre [https://outlook.com](https://outlook.com) na conta do Outlook que você criou na fase 2 do[ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
    
  - Se estiver usando o ambiente de desenvolvimento e teste leve, abra uma sessão particular do Internet Explorer e entre com o seu computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento/teste corporativo simulado, use o portal do[https://portal.azure.com](https://portal.azure.com)Azure () para se conectar à máquina virtual CLIENT1 e, em seguida, entre no CLIENT1.
    
2. Na guia **Email do Outlook**, clique em **Novo**.
    
3. Em **para**, digite o endereço de email da conta usuário6 da sua assinatura de avaliação ( ** user6@.**<organization name> **. onmicrosoft.com**).
    
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
    
14. Clique no ícone de usuário no canto superior direito e depois clique em **Sair**.
    
15. Abra uma nova guia e entre no portal do Office 365 ([https://www.office.com](https://www.office.com)) com o nome da conta e a senha da conta usuário6 da sua assinatura de avaliação.
    
16. Na guia do **portal do Office 365**, clique em **Email**.
    
17. Na guia **mail-usuário6-Outlook** , verifique se usuário6 recebeu todos os três emails da conta de email do Outlook.
    
18. Volte para a **guia do portal do Office 365** de Usuário6.
    
19. Clique no ícone de usuário no canto superior direito e depois clique em **Sair.**
    
Neste procedimento, você criará dois documentos do Word que, mais tarde, serão analisados em um caso de Descoberta Eletrônica Avançada.
  
1. Na página do **Office**, clique em **Entrar** e entre com as credenciais da sua conta de administrador global.
    
2. em uma nova guia, acesse a URL do site de produção do SharePoint: **https://** <fictional organization name> **. sharepoint.com/sites/production**
    
3. Na guia **Conjunto de sites de produção**, em **Documentos**, clique em **Novo > Documento do Word**.
    
4. Na página do **Word Online**, digite **Contrato de rascunho com a Tailspin**, aguarde até que **Salvo** apareça no título e feche a guia da página do **Word Online**.
    
5. Na guia **Conjunto de sites de produção**, em **Documentos**, clique em **Novo > Documento do Word**.
    
6. 	Na guia do **Word Online**, digite **Notas da disputa contratual com a Tailspin**, aguarde até que **Salvo** apareça no título e feche a guia do **Word Online**.
    
7. Na guia **Conjunto de sites de produção**, você verá **Documento** e **Documento1** na lista de documentos.
    
8. Feche a guia **Coleção do site de produção**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Fase 3: usar a descoberta eletrônica avançada para uma disputa legal

Infelizmente, uma disputa de contrato entre a organização e a Tailspin Toys chegou ao ponto de desencadear uma ação legal. Neste procedimento, você criará e configurará uma ocorrência de descoberta eletrônica avançada para pesquisar e analisar emails e documentos que contenham o texto "Tailspin Contract".
  
O processo de uso da Descoberta Eletrônica Avançada é o seguinte:
  
- Criar uma pesquisa no centro de &amp; conformidade de segurança, analisar seus resultados e, em seguida, preparar os resultados para descoberta eletrônica avançada.
    
- Criar e configurar um caso de Descoberta Eletrônica Avançada e analisar os resultados da pesquisa.
    
Neste procedimento, você cria uma pesquisa no centro de conformidade &amp; de segurança para "contrato da Tailspin", examina os resultados e, em seguida, prepara os resultados para descoberta eletrônica avançada.
  
1. Na guia do **portal do Office 365**, clique em **Admin**.
    
2. Na navegação à esquerda da guia Centro de administração, clique em **Centros de administração > Conformidade**.
    
3. Na guia **conformidade &amp; de segurança** , clique em **permissões**.
    
4. Na lista **Permissões**, clique duas vezes em **Gerenciamento da Organização**.
    
5. Na janela **Grupo de Função**, em **Membros**, clique no sinal de adição.
    
6. Na janela **Selecionar Membros**, clique duas vezes o nome da sua conta de administrador e depois clique em **OK**.
    
7. Na janela **Grupo de Funções**, clique em **Salvar**.
    
8. Na lista **Permissões**, clique duas vezes em **Gerente de Descoberta Eletrônica**.
    
9. Na janela **Grupo de Função**, em **Administrador de Descoberta Eletrônica**, clique no ícone de adição.
    
10. Na janela **Selecionar Membros**, clique duas vezes o nome da sua conta de administrador e depois clique em **OK**.
    
11. Na janela **Grupo de Funções**, clique em **Salvar**.
    
12. No painel de navegação à esquerda, clique em **investigação de pesquisa &amp; > conteúdo pesquisa**.
    
13. Clique no ícone de adição para adicionar uma pesquisa.
    
14. Na janela **Nova pesquisa**, digite **Pesquisa de contrato com a Tailspin** em **Nome**.
    
15. Em **Onde deseja procurar?**, clique em **Pesquisar em todos os lugares**, selecione **Exchange**, **SharePoint** e **Pastas Públicas** e depois clique em **Avançar**.
    
16. Em **O que você deseja que procuremos?**, digite **Contrato com a Tailspin** e clique em **Pesquisar**.
    
17. Na lista de pesquisas, clique no nome **Pesquisa de contrato com a Tailspin**.
    
18. No painel **Pesquisa de contrato com a Tailspin**, clique em **Visualizar resultados de pesquisa** em **Resultados**. Você verá uma janela listando os dois documentos no site de produção do SharePoint ( **Document** e **Documento1**) e os emails de **teste email 1** e **testar email 3** para o usuário6. Feche a janela.
    
19. No painel **Pesquisa de conteúdo**, em **Analisar os resultados com a Descoberta Eletrônica Avançada**, clique em **Visualizar resultados para análise**.
    
20. Na janela **Preparar os resultados da pesquisa para a pesquisa de contrato com a Tailspin**, clique em **Preparar** e aguarde a sua conclusão.
    
Neste procedimento, você criará um novo caso de Descoberta Eletrônica Avançada e analisará os resultados da pesquisa de contrato com a Tailspin.
  
1. Na navegação à esquerda, clique em **descoberta eletrônica** em **investigação de pesquisa &amp; **.
    
2. No painel **Descoberta Eletrônica**, clique em **Ir para Descoberta Eletrônica Avançada**.
    
3. Na guia **Descoberta Eletrônica Avançada**, clique no ícone de adição para adicionar um novo caso.
    
4. 	No painel **Adicionar caso**, digite **Disputa contratual com a Tailspin** em **Nome** e depois clique em **OK**. Aguarde até que o caso seja criado.
    
5. Clique duas vezes no caso **Disputa contratual com a Tailspin** na lista. 
    
6. Na lista **contêiner** , clique no contêiner de **pesquisa de contrato** com a Tailspin e, em seguida, clique em **processar**. Aguarde até que o processamento seja concluído.
    
7. Quando a mensagem **Processo: concluído** aparecer na parte inferior da janela, clique em **Resumo do processo** na navegação à esquerda para ver um resumo.
    
8. Na navegação superior, clique em **Analisar**.
    
9. Na página **Configuração**, em **Temas**, digite **3** em **Número máximo de temas**.
    
10. Clique em **Analisar** e aguarde a conclusão da análise. Você verá uma série de gráficos de pizza com a análise da população-alvo, documentos, emails e anexos. Para obter mais informações, consulte [exibir resultados de análise](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Agora, você pode usar esse ambiente para criar novo conteúdo, novas pesquisas e casos e também para continuar os testes com a Descoberta Eletrônica Avançada no Office 365.
  
## <a name="see-also"></a>Confira também


[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento/teste para a Configuração Base](base-configuration-dev-test-environment.md)
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para o ambiente de desenvolvimento/ teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Descoberta Eletrônica Avançada do Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


