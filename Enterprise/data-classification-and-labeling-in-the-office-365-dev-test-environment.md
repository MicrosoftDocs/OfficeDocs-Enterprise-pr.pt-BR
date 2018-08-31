---
title: Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365
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
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Resumo: Configurar e demonstrar a classificação de dados e rótulos usando o cliente de proteção de informações do Windows Azure (AIP) em seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: 91d3b40f43eed750bd33065faa1c57d74179cf58
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914846"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365

 **Resumo:** Configurar e demonstrar a classificação de dados e rótulos usando o cliente de proteção de informações do Windows Azure (AIP) em seu ambiente de desenvolvimento e teste do Office 365.
  
O cliente de proteção de informações do Windows Azure permite classificar um documento antes de carregá-la para uma pasta do SharePoint Online no Office 365. Com as instruções deste artigo, você pode instala o cliente de proteção de informações do Windows Azure e demonstrar a classificação de dados. Para obter mais informações, consulte [Proteção de informações do Windows Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: Criar o seu ambiente de desenvolvimento e teste do Office 365

Siga as instruções no [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Fase 2: Adicionar uma assinatura de avaliação de proteção de informações do Windows Azure

Nesta fase, você adiciona a proteção de informações do Windows Azure para seu ambiente de desenvolvimento e teste do Office 365 e habilitá-lo para suas contas de usuário. Se você tiver configurado o [Office 365 e o ambiente de desenvolvimento e teste do EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignore esta fase. A assinatura de avaliação Enterprise mobilidade Suite inclui licenças da proteção de informações do Windows Azure.
  
Em primeiro lugar, inscreva-se para uma assinatura de avaliação de proteção de informações do Windows Azure.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Inscreva-se para uma assinatura de avaliação de proteção de informações do Windows Azure

1. No Internet Explorer ou seu navegador, vá para [http://portal.office.com](http://portal.office.com) e entre com sua conta de administrador global do Office 365.
    
2. Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .
    
3. Na guia de administração do Office 365, no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.
    
4. Na página **Serviços de compra** , localize o item de **P2 de Premium de proteção de informações do Azure** . Passe o mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.
    
5. Na página **Confirmar seu pedido**, clique em **Experimentar agora**.
    
6. Na página **Recibo do pedido**, clique em **Continuar**.
    
Em seguida, você pode habilitar a licença de proteção de informações do Windows Azure para todas as contas de usuário.
  
1. Na guia Office 365 admin center, clique em **usuários**.
    
2.  Na lista de contas de usuário, selecione sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.
    
3. Ativar a licença do produto para o **Windows Azure informações proteção Premium P2** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .
    
4. Repita as etapas 2 e 3 para suas outras contas de usuário (usuário 1 a 5 do usuário).
    
Agora tem seu ambiente de desenvolvimento e teste do Office 365:
  
- Assinaturas de avaliação do Office 365 E5 Enterprise e proteção de informações do Windows Azure.
    
- Todas as suas contas de usuário habilitado para usar o Office 365 E5 Enterprise e proteção de informações do Windows Azure.
    
## <a name="phase-3-demonstrate-data-classification"></a>Fase 3: Demonstrar a classificação de dados

Nesta fase, você demonstrar a classificação de dados usando o cliente de proteção de informações do Windows Azure e a diretiva de proteção de informações do Azure padrão.
  
Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, você deve instalar primeiro 2016 do Office no CLIENT1.
  
1. Use o seu navegador e vá para o [portal do Azure](http://portal.azure.com).
    
2. Clique em **grupos de recursos >** [seu nome de grupo de recurso] **> CLIENT1 > conectar**.
    
3. No CLIENT1, execute o Internet Explorer, vá para o portal do Office em [http://portal.office.com](http://portal.office.com)e, em seguida, entre com o nome da conta de User5 e a senha.
    
4. Na guia **Microsoft Office Home**, clique em **Instalar o Office 2016**.
    
5. Execute o download quando solicitado e clique em **Sim** quando solicitado pelo controle de conta de usuário. Aguarde do Office instalar. Quando concluir, clique em **Fechar** duas vezes.
    
Em seguida, você pode instalar o cliente de proteção de informações do Windows Azure.
  
1. No seu navegador ou o Internet Explorer, vá para a [página de download de proteção de informações do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Se você estiver usando a versão leve do ambiente de desenvolvimento e teste do Office 365, use o navegador no computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, execute o Internet Explorer do CLIENT1.
    
2. Na página de download de **Proteção de informações do Microsoft Azure** , clique em **Download**, clique em **AzInfoProtection.exe**e, em seguida, clique em **Avançar**.
    
3. Quando solicitado, execute AzInfoProtection.exe.
    
4. Na caixa de cliente **instalar a proteção de informações do Windows Azure** , clique em **Concordo**e clique em **Sim** quando solicitado pelo controle de conta de usuário.
    
5. Na caixa **concluída com êxito** , clique em **Close.**
    
Em seguida, você demonstrar a classificação de documento.
  
1. Clique no ícone do **Word** na barra de tarefas.
    
2. Quando solicitado, inscreva-se com o nome da conta de User5 e a senha.
    
3. Se você acabou de instalar Office 2016 no CLIENT1, no **primeiras coisas primeiro** , clique em **Aceitar**.
    
4. Clique em **documento em branco**. 
    
    Observe que a seção de **proteção** da faixa de opções, na guia **página inicial** e a linha de classificações de documento.
    
5. No documento em branco, digite algum texto.
    
6. Clique em **arquivo > Salvar**, digite o nome **BeforeAIP**e, em seguida, clique em **Okey**. 
    
7. Na linha de classes de documento, clique na seta para **segredo**e, em seguida, clique em **Tudo empresa**.
    
8. Clique em **arquivo > Salvar como**, digite o nome **AfterAIP**e, em seguida, clique em **Okey**.
    
9. Clique em **Gerenciador de arquivos** , na barra de tarefas e, em seguida, abra a pasta de **documentos** .
    
    Observe os tamanhos de arquivo diferente dos documentos **BeforeAIP** e **AfterAIP** . O documento de AfterAIP for maior, pois ele contém as informações de classificação.
    
Em seguida, você permitir que todos acessar a coleção de site de suporte.
  
1. Na guia **Página inicial do Microsoft Office** , clique em **SharePoint**.
    
2. Na guia **SharePoint** , clique em **conjunto de sites de suporte**.
    
3. No canto superior direito, clique no ícone **configurações** e, em seguida, clique em **compartilhado com**.
    
4. Em **compartilhamento 'Conjunto de sites de suporte'**, clique em **Avançado**.
    
5. Na lista de grupos do SharePoint, clique em **conjunto de sites de suporte membros**.
    
6. Na página **Pessoas e Grupos**, clique em **Novo**.
    
7. Em **compartilhamento 'Conjunto de sites de suporte'**, digite **todos**, clique em **todos exceto os usuários externos**e, em seguida, clique em **Share.**
    
8. Feche a guia **pessoas e grupos** .
    
Em seguida, você pode entrar com sua conta User5 e carregar um documento protegido por AIP para a pasta de documentos do conjunto de sites de suporte.
  
1. Na guia **Página inicial do Microsoft Office** , no canto superior direito, clique no ícone de usuário e, em seguida, clique em **Sair**.
    
2. Vá para [http://portal.office.com](http://portal.office.com).
    
3. Na página do **Office 365 entrar** , clique no nome da conta de User5 e entrar.
    
4. Na guia **Página inicial do Microsoft Office** , clique em **SharePoint > suportam o conjunto de sites**.
    
5. Clique em **documentos**, clique em **carregar**, clique no documento **AfterAIP** e clique em **Abrir**.
    
    Você deverá ver AfterAIP.docx na pasta documentos no conjunto de sites de suporte.
    
## <a name="see-also"></a>Confira também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 e o ambiente de desenvolvimento/teste do EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Proteção de Informações do Azure](https://www.microsoft.com/cloud-platform/azure-information-protection)


