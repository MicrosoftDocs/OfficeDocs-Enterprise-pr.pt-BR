---
title: "Criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Resumo: Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em seu ambiente de desenvolvimento e teste de campanha política."
ms.openlocfilehash: 3a2e507d17a558452fe0c2f0a062098e7c9c6407
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a>Criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política

 **Resumo:** Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em seu ambiente de desenvolvimento e teste de campanha política. 
  
Use as instruções deste artigo para criar um ambiente de desenvolvimento e teste que inclui os quatro tipos diferentes de sites de equipe do SharePoint Online para as [Diretrizes de segurança da Microsoft para campanhas político, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solução. Esses sites são descritos em detalhes no tópico 10, intitulado **SharePoint e o OneDrive for Business**.
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a>Fase 1: Crie seu ambiente de desenvolvimento e teste de campanha política

Primeiro, siga as instruções em [Configure grupos e usuários para um ambiente de desenvolvimento e teste de campanha político](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) para criar suas assinaturas, usuários e grupos.
  
## <a name="phase-2-create-office-365-labels"></a>Fase 2: Criar rótulos do Office 365

Nesta fase, você deve criar os rótulos para os diferentes níveis de segurança para pastas de documentos do site de equipe do SharePoint Online.
  
1. Se necessário, entre no portal do Office 365 com as credenciais da conta de administrador global de sua assinatura de avaliação. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .
    
3. Na guia novo **Centro de administração do Office** do seu navegador, clique em **centrais de Admin > segurança &amp; conformidade**.
    
4. Do novo **Home - segurança &amp; conformidade** guia do navegador, clique em **classificações > rótulos**.
    
5. Da **Home > rótulos** painel, clique em **criar um rótulo**.
    
6. No painel de **nome de seu rótulo** , digite **interno**e clique em **Avançar**.
    
7. No painel de **configurações de rótulo** , clique em **Avançar**.
    
8. No painel **Revise suas configurações** , clique em **criar este rótulo**e, em seguida, clique em **Fechar**.
    
9. Repita as etapas 5 a 8 para esses rótulos adicionais:
    
  - Particular
    
  - Confidenciais
    
  - Altamente confidenciais
    
10. Da **Home > rótulos** painel, clique em **Publicar rótulos**.
    
11. No painel **Choose rótulos para publicar** , clique em **rótulos de escolher para publicar**.
    
12. No painel **Choose rótulos** , clique em **Adicionar** e selecione todas as quatro rótulos.
    
13. Clique em **concluído**.
    
14. No painel **Choose rótulos para publicar** , clique em **Avançar**.
    
15. No painel **Choose locais** , clique em **Avançar**.
    
16. No painel de **sua política de nome** , digite **campanha** em **nome**e, em seguida, clique em **Avançar**.
    
17. No painel **Revise suas configurações** , clique em **rótulos de publicar**e, em seguida, clique em **Fechar**.
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a>Fase 3: Criar seus sites de equipe do SharePoint Online

Nesta fase, criar e configurar sites de equipe do SharePoint Online para a sua campanha política correspondente aos quatro tipos de sites de equipe do SharePoint Online.
  
### <a name="campaign-wide-team-site"></a>Site da equipe ampla campanha

Para criar um site de equipe ' baseline público do SharePoint Online, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do Site**, digite **campanha ampla**. 
    
6. Na **Descrição do site de equipe**, digite o **site do SharePoint para toda a campanha**.
    
7. Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
Em seguida, configure a pasta de documentos do site campanha ampla de equipe para o rótulo interno.
  
1. Na guia **wide-Home de campanhas** de seu navegador, clique em **documentos**.
    
2. Clique no ícone configurações e clique em **definições da biblioteca**.
    
3. Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **interno**e, em seguida, clique em **Salvar**.
    
### <a name="campaign-project-1-team-site"></a>Site da campanha 1 equipe de projeto

Para criar um site de equipe baseline privado SharePoint Online para um projeto dentro da campanha, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do Site**, digite **Projeto1 campanha**. 
    
6. Na **Descrição do site de equipe,** digite o **site do SharePoint para o projeto de campanha 1**.
    
7. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
Em seguida, configure a pasta de documentos do site campanha projeto 1 de equipe para o rótulo de privada.
  
1. Na guia **projeto 1-Home de campanhas** de seu navegador, clique em **documentos**.
    
2. Clique no ícone configurações e clique em **definições da biblioteca**.
    
3. Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **privada**e clique em **Salvar**.
    
### <a name="campaign-marketing-team-site"></a>Site da campanha de marketing da equipe

Para criar um nível confidenciais isolado SharePoint Online site de equipe para campanha de marketing recursos, faça o seguinte:
  
1. Usando um navegador no computador local, entre no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do site de equipe**, digite **marketing campanha**.
    
6. Na **Descrição do site de equipe**, digite o **site do SharePoint para campanha de marketing (confidenciais)**.
    
7.  Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
9. Na guia novo **marketing campanha** no seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
10. No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.
    
11. Na guia **permissões** nova no seu navegador, clique em **Configurações de solicitação de acesso**.
    
12. Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque as caixas de seleção **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** , digite **ITAdmin1 @** <your organization name> **. onmicrosoft.com** em **Enviar todas as solicitações de acesso**e clique em **Okey**.
    
13. Clique em **campanhas de marketing membros** na lista.
    
14. Na página **pessoas e grupos** , clique em **novo**.
    
15. Na caixa de diálogo **compartilhar** , digite **sênior e à equipe estratégico**, selecioná-la e, em seguida, clique em **compartilhar**.
    
16. Repita as etapas 14 e 15 para o grupo de **equipe de análise** e a conta de usuário **Regular1** .
    
17. Clique no botão voltar de seu navegador.
    
18. Na lista, clique em **campanhas de marketing proprietários** .
    
19. Na página **pessoas e grupos** , clique em **novo**.
    
20. Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.
    
21. Clique no botão voltar de seu navegador.
    
22. Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Home campanha de marketing** no seu navegador e, em seguida, feche o painel de **permissões do Site** .
    
Estes são os resultados da configuração das permissões:
  
- Grupo do SharePoint de **Campanhas de marketing-membros** contém somente o **sênior e à equipe estratégica** grupo (que contém as contas de usuário do candidato, ChiefOfStaff e Strategic1), grupo **campanhas marketing** (que contém o conta de usuário de administrador global), o grupo de **equipe de análise** (que contém a conta de usuário DataScientist1) e a conta de usuário **Regular1** .
    
- O grupo do SharePoint de **Campanhas de marketing-proprietários** contém apenas o grupo de **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).
    
- Grupo de **Campanhas de marketing-visitantes** do SharePoint não contém grupos ou contas de usuário.
    
- Membros não podem modificar permissões de nível de site (isso só pode ser feito por membros do grupo de **Campanhas de marketing-proprietários** ).
    
- Outras contas de usuário não podem acessar o site ou seus recursos, mas podem solicitar acesso ao site, qual enviará um email para a caixa de correio de conta de usuário ITAdmin1.
    
Em seguida, configure a pasta de documentos do site de equipe marketing a campanha para o rótulo de confidencial.
  
1. Na guia **Home campanha de marketing** do navegador, clique em **documentos**.
    
2. Clique no ícone configurações e clique em **definições da biblioteca**.
    
3. Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **confidenciais**e, em seguida, clique em **Salvar**.
    
Em seguida, configure uma política de prevenção (DLP) de perda de dados que notifica os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo confidencial fora da organização. Essa política DLP serão aplicadas aos recursos em que o site da campanha de marketing.
  
1. Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.
    
2. No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.
    
3. No painel de **prevenção de perda de dados** , clique em **+ para criar uma política**.
    
4. No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.
    
5. No painel de **sua política de nome** , digite os **sites de equipe do SharePoint Online rótulo confidenciais** em **nome**e, em seguida, clique em **Avançar**.
    
6. No painel **Choose locais** , clique em **Deixe-me escolher locais específicos**e clique em **Avançar**.
    
7. Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.
    
8. No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Editar**.
    
9. No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.
    
10. No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.
    
11. No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Salvar**.
    
12. No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Avançar**.
    
13. No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, clique em **Personalizar a dica e email**.
    
14. No painel de **dicas de política personalizar e notificações por email** , clique em **Personalizar o texto da dica de política**.
    
15. Na caixa de texto, digite ou cole o código a seguir:
    
  - Para compartilhar com um usuário fora da organização, baixe o arquivo e, em seguida, abri-lo. Clique em arquivo, em seguida, proteger documento e, em seguida, criptografar com senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.
    
16. Clique em **OK**.
    
17. No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, desmarque a caixa de seleção **bloquear pessoas de compartilhamento e restringir o acesso ao conteúdo compartilhado** e, em seguida, clique em **Avançar**.
    
18. No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.
    
19. No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.
    
### <a name="campaign-strategy-team-site"></a>Site de equipe da estratégia de campanha

Para criar um site de equipe do SharePoint Online isolado no nível altamente confidencial para recursos de estratégia de campanha, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do site de equipe**, digite a **estratégia de campanha**.
    
6. Na **Descrição do site de equipe**, digite o **site do SharePoint para a estratégia de campanha (altamente confidencial)**.
    
7.  Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
9. Na guia **estratégia da campanha de** novo no seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
10. No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.
    
11. Na guia **permissões** nova no seu navegador, clique em **Configurações de solicitação de acesso**.
    
12. Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** (de forma que todas as três caixas de seleção estiver desmarcadas) e clique em ** Okey**.
    
13. Clique em **estratégia da campanha de membros** na lista.
    
14. Na página **pessoas e grupos** , clique em **novo**.
    
15. Na caixa de diálogo **compartilhar** , digite **sênior e à equipe estratégico**, selecioná-la e, em seguida, clique em **compartilhar**.
    
16. Na lista, clique em **estratégia da campanha de proprietários** .
    
17. Na página **pessoas e grupos** , clique em **novo**.
    
18. Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.
    
19. Clique no botão voltar de seu navegador.
    
20. Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Home a estratégia de campanhas** no seu navegador e, em seguida, feche o painel de **permissões do Site** .
    
Estes são os resultados da configuração das permissões:
  
- Grupo do SharePoint **Campanha estratégia-membros** contém apenas o grupo de **sênior e à equipe estratégico** (que contém apenas as contas de usuário de candidato, ChiefOfStaff e Strategic1) e o grupo de **estratégia de campanha** (que contém somente a administrador global conta de usuário).
    
- Grupo do SharePoint de **Proprietários de estratégia de campanha** contém apenas o grupo de **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).
    
- Grupo do SharePoint **Campanha estratégia-visitantes** não contém grupos ou contas de usuário.
    
- Membros não podem modificar permissões de nível de site (isso só pode ser feito por membros do grupo **Proprietários de estratégia de campanha** ).
    
- Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar acesso ao site. Permissões adicionais para o site devem ser realizadas pelo administrador global ou por um membro do grupo **Proprietários campanha estratégia** .
    
Em seguida, configure a pasta de documentos do site da equipe de estratégia campanha para o rótulo de altamente confidenciais.
  
1. Na guia **Home a estratégia de campanhas** de seu navegador, clique em **documentos**.
    
2. Clique no ícone configurações e clique em **definições da biblioteca**.
    
3. Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **Altamente confidenciais**e, em seguida, clique em **Salvar**.
    
Em seguida, configure uma política de DLP que bloqueia usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo altamente confidenciais fora da organização. Essa política DLP serão aplicadas aos recursos no site da campanha de estratégia.
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) com uma conta que tenha a função de administrador de segurança ou administrador da empresa.
    
2. Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.
    
3. No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.
    
4. No painel de **prevenção de perda de dados** , clique em **+ para criar uma política**.
    
5. No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.
    
6. No painel de **sua política de nome** , digite **altamente confidenciais sites de equipe do SharePoint Online do rótulo** em **nome**e, em seguida, clique em **Avançar**.
    
7. No painel **Choose locais** , clique em **Deixe-me escolher locais específicos**e clique em **Avançar**.
    
8. Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.
    
9. No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Editar**.
    
10. No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.
    
11. No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **Altamente confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.
    
12. No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Salvar**.
    
13. No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Avançar**.
    
14. No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, clique em **Personalizar a dica e email**.
    
15. No painel de **dicas de política personalizar e notificações por email** , clique em **Personalizar o texto da dica de política**.
    
16. Na caixa de texto, digite ou cole o código a seguir:
    
  - Para compartilhar com um usuário fora da organização, baixe o arquivo e, em seguida, abri-lo. Clique em arquivo, em seguida, proteger documento e, em seguida, criptografar com senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.
    
17. Clique em **OK**.
    
18. No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, selecione **exigir uma justificativa comercial para substituir**e, em seguida, clique em **Avançar**.
    
19. No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.
    
20. No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.
    
Use as instruções em [Ativar o Azure RMS com o Centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Em seguida, configure a proteção de informações do Windows Azure com uma nova política de escopo e sub-recurso rótulo para proteção e permissões com as seguintes etapas:
  
1. Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Em uma guia separada do navegador, vá para o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se essa for a primeira vez que você está configurando a proteção de informações do Windows Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. No painel de lista, clique em **mais de serviços**, digite as **informações**e clique em **Proteção de informações do Windows Azure**.
    
5. No blade **proteção das informações do Azure** , clique em **escopo políticas > + Adicionar uma nova diretiva**.
    
6. Digite **CampaignStrategy** no **nome da diretiva** e **rótulo para documentos no site da equipe de estratégia campanha** em **Descrição**.
    
7. Clique em **Selecione quais usuários ou grupos fazer essa política > grupos de usuários/**e selecione **sênior e equipe estratégica**.
    
8. Clique em **Selecione > Okey**.
    
9. Para o rótulo de **Altamente confidenciais** , clique nas reticências (…) e, em seguida, clique em **Adicionar um rótulo de subsites**.
    
10. Digite um nome para o rótulo de subsites em **nome** e uma descrição do rótulo em **Descrição**.
    
11. Em **definir permissões para documentos e emails contendo esse rótulo**, clique em **proteger**.
    
12. Na seção **proteção** , clique em **Windows Azure (chave de nuvem)**.
    
13. No blade **proteção** , em **configurações de proteção**, clique em **+ Adicionar permissões**.
    
14. No blade **Adicionar permissões** , em **especificar usuários e grupos**, clique em **+ Procurar no diretório**.
    
15. No painel **AAD usuários e grupos** , selecione **sênior e à equipe estratégico**e clique em **Selecionar**.
    
16. Em **Escolha as permissões a predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo**e **Encaminhar** .
    
17. Clique duas vezes em **Okey** .
    
18. No **rótulo sub-recurso** blade, clique em **Salvar**.
    
19. Fechar o novo escopo blade de política.
    
20. No blade **proteção de informações do Windows Azure - políticas com escopo** , clique em **Publicar**e, em seguida, clique em **Sim**.
    
Agora você está pronto para começar a criar documentos em sites essas quatro e testar acessá-los com várias contas de usuário em sua assinatura de avaliação. 
  
Para proteger um documento com esse novo rótulo e de proteção de informações do Windows Azure, você deve [instalar o cliente de proteção de informações do Windows Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em uma máquina de teste, instalar o Office do portal do Office 365 e entrar do Microsoft Word com uma conta no ** Sênior e à equipe estratégica** grupo de sua assinatura de avaliação.
  
## <a name="see-also"></a>Veja também

[Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Configurar grupos e usuários para um ambiente de desenvolvimento e teste de campanha política](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




