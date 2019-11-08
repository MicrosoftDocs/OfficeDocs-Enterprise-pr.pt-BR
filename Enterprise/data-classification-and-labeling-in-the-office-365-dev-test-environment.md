---
title: Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Resumo: Configure e demonstre a classificação de dados e rotular usando o cliente de proteção de informações do Azure (AIP) no seu ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: f16fd41aaa454a3f038fd23c890bbf48be2c3e66
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028895"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365

 **Resumo:** Configurar e demonstrar a classificação de dados e rotular usando o cliente de proteção de informações do Azure (AIP) em seu ambiente de desenvolvimento/teste do Office 365.
  
O cliente de proteção de informações do Azure permite que você classifique um documento antes de carregá-lo em uma pasta do SharePoint Online no Office 365. Com as instruções deste artigo, você instala o cliente de proteção de informações do Azure e demonstra a classificação de dados. Confira mais informações em [proteção de informações do Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Clique [aqui](https://aka.ms/catlgstack) para exibir um mapa visual de todos os artigos da pilha da Guia do Laboratório de Teste do Office 365.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: criar seu ambiente de desenvolvimento/teste do Office 365

Siga as instruções em [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Fase 2: adicionar a assinatura de avaliação do Azure Information Protection

Nesta fase, adicione a proteção de informações do Azure ao seu ambiente de desenvolvimento/teste do Office 365 e habilite-a para suas contas de usuário. Se você tiver configurado o [ambiente de desenvolvimento/teste do Office 365 e EMS](https://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), pule esta fase. A assinatura de avaliação do Enterprise Mobility Suite inclui licenças de proteção de informações do Azure.
  
Primeiro, Inscreva-se em uma assinatura de avaliação do Azure Information Protection.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Inscreva-se para obter uma assinatura de avaliação do Azure Information Protection

1. No Internet Explorer ou no navegador, acesse [https://admin.microsoft.com](https://admin.microsoft.com) e entre com sua conta de administrador global do Office 365.
    
2. Na guia **Microsoft Office Home** , clique no bloco **administrador** .
    
3. Na guia Administração do Office 365, na navegação à esquerda, clique em **cobrança > comprar serviços**.
    
4. Na página **comprar serviços** , encontre o item do **Azure Information Protection Premium P2** . Passe o mouse sobre ele e clique em **Iniciar avaliação gratuita**.
    
5. Na página **Confirmar seu pedido**, clique em **Experimentar agora**.
    
6. Na página **Recibo do pedido**, clique em **Continuar**.
    
Em seguida, habilite a licença de proteção de informações do Azure para todas as contas de usuário.
  
1. Na guia centro de administração do Microsoft 365, clique em **usuários**.
    
2.  Na lista de contas de usuário, selecione sua conta de administrador global e clique em **Editar** para **licenças de produto**.
    
3. Ative a licença de produto do **Azure Information Protection Premium P2** para **ativado**, clique em **salvar** e clique em **fechar** duas vezes.
    
4. Repita as etapas 2 e 3 para suas outras contas de usuário (usuário 1 até usuário 5).
    
Seu ambiente de desenvolvimento/teste do Office 365 agora tem:
  
- Assinaturas de avaliação do Office 365 E5 Enterprise e Azure Information Protection.
    
- Todas as suas contas de usuário habilitadas para usar a proteção de informações do Office 365 E5 Enterprise e do Azure.
    
## <a name="phase-3-demonstrate-data-classification"></a>Fase 3: demonstrar a classificação dos dados

Nesta fase, você demonstra a classificação de dados usando o cliente de proteção de informações do Azure e a política de proteção de informações padrão do Azure.
  
Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, primeiro deverá instalar o Office 2016 em CLIENT1.
  
1. Use seu navegador e vá para o [portal do Azure](https://portal.azure.com).
    
2. Clique em **grupos de recursos >** [nome do grupo de recursos] **> CLIENT1 > se conectar**.
    
3. Em CLIENT1, execute o Internet Explorer, vá para o portal do [https://admin.microsoft.com](https://admin.microsoft.com)Office em e entre com o nome da conta e senha do User5.
    
4. Na guia **Microsoft Office Home**, clique em **Instalar o Office 2016**.
    
5. Execute o download quando solicitado e clique em **Sim** quando solicitado pelo controle de conta de usuário. Aguarde a instalação do Office. Ao concluir, clique em **fechar** duas vezes.
    
Em seguida, instale o cliente de proteção de informações do Azure.
  
1. No navegador ou no Internet Explorer, vá para a [página de download da proteção de informações do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Se você estiver usando a versão leve do ambiente de desenvolvimento/teste do Office 365, use o navegador no computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, execute o Internet Explorer a partir de CLIENT1.
    
2. Na página Download da **proteção de informações do Microsoft Azure** , clique em **baixar**, clique em **AzInfoProtection. exe**e clique em **Avançar**.
    
3. Quando solicitado, execute AzInfoProtection. exe.
    
4. Na caixa **instalar o cliente de proteção de informações do Azure** , clique em **concordo**e, em seguida, clique em **Sim** quando solicitado pelo controle de conta de usuário.
    
5. Na caixa **concluído com êxito** , clique em **fechar.**
    
Em seguida, demonstre a classificação de documentos.
  
1. Clique no ícone do **Word** na barra de tarefas.
    
2. Quando solicitado, entre com o nome da conta e senha do User5.
    
3. Se você acabou de instalar o Office 2016 em CLIENT1, na primeira caixa de **informações** , clique em **aceitar**.
    
4. Clique em **documento em branco**. 
    
    Observe a seção **proteção** da faixa de opções na guia **página inicial** e a linha de classificações de documento.
    
5. No documento em branco, digite algum texto.
    
6. Clique em **arquivo > salvar**, digite o nome **BeforeAIP**e clique em **OK**. 
    
7. Na linha de classes de documento, clique na seta para baixo para **segredo**e, em seguida, clique em **toda a empresa**.
    
8. Clique em **arquivo > salvar como**, digite o nome **AfterAIP**e clique em **OK**.
    
9. Clique em **Explorador de arquivos** na barra de tarefas e, em seguida, abra a pasta **documentos** .
    
    Observe os diferentes tamanhos de arquivo dos documentos **BeforeAIP** e **AfterAIP** . O documento AfterAIP é maior porque tem as informações de classificação.
    
Em seguida, permita que todos acessem o conjunto de sites de suporte.
  
1. Na guia **Microsoft Office Home** , clique em **SharePoint**.
    
2. Na guia **SharePoint** , clique em **conjunto de sites de suporte**.
    
3. No canto superior direito, clique no ícone **configurações** e, em seguida, clique em **compartilhado com**.
    
4. Em **compartilhar ' conjunto de sites de suporte '**, clique em **avançado**.
    
5. Na lista de grupos do SharePoint, clique em **suporte para membros do conjunto de sites**.
    
6. Na página **Pessoas e Grupos**, clique em **Novo**.
    
7. Em **compartilhar ' conjunto de sites de suporte '**, digite **todos**, clique em **todos exceto usuários externos**e, em seguida, clique em **compartilhar.**
    
8. Feche a guia **pessoas e grupos** .
    
Em seguida, entre com sua conta do User5 e carregue o documento protegido por AIP na pasta documentos do conjunto de sites de suporte.
  
1. Na guia **página inicial do Microsoft Office** , no canto superior direito, clique no ícone usuário e **, em seguida**, clique em sair.
    
2. Acesse [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Na página de **entrada do Office 365** , clique no nome da conta do User5 e entre.
    
4. Na guia **Microsoft Office Home** , clique em **conjunto de sites de suporte do SharePoint >**.
    
5. Clique em **documentos**, clique em **carregar**, clique no documento **AfterAIP** e, em seguida, clique em **abrir**.
    
    Você verá AfterAIP. docx na pasta documentos no conjunto de sites de suporte.
    
## <a name="see-also"></a>Confira também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 e o ambiente de desenvolvimento/teste do EMS](https://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Proteção de Informações do Azure](https://www.microsoft.com/cloud-platform/azure-information-protection)


