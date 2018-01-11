---
title: "Implantar sites do SharePoint Online para três camadas de proteção"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "Resumo: Criar e configurar sites de equipe do SharePoint Online para diversos níveis de proteção de informações."
ms.openlocfilehash: 7aa0107222454383abe0c1284b66ec0c4b808595
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a>Implantar sites do SharePoint Online para três camadas de proteção

 **Resumo:** Criar e configurar sites de equipe do SharePoint Online para diversos níveis de proteção de informações.
  
Use as etapas neste artigo para projetar e implantar a linha de base, confidenciais e altamente confidenciais team sites do SharePoint Online. Para obter mais informações sobre esses três camadas de proteção, consulte [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md).
  
## <a name="baseline-sharepoint-online-team-sites"></a>Sites de equipe do SharePoint Online da linha de base

Proteção de linha de base inclui os dois sites de equipe públicos e particulares. Sites de equipe públicas podem ser descobertos e acessados por qualquer pessoa na organização. Sites privadas só podem ser descobertos e acessados pelos membros do grupo do Office 365 associadas ao site de equipe. Ambos os tipos de sites de equipe permitem que os membros compartilhe o site com outras pessoas.
  
### <a name="public"></a>Público

Para criar um site de equipe do SharePoint Online da linha de base com e permissões de acesso público, faça o seguinte:
  
1. Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do Site**, digite um nome para o site de equipe pública. 
    
6. Em **Descrição do site de equipe**, digite uma descrição do objetivo do site.
    
7. Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
Esta é a configuração resultante.
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online público.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a>Particular

Para criar um site de equipe do SharePoint Online da linha de base com permissões e acesso privado, faça o seguinte:
  
1. Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do Site**, digite um nome para o site de equipe particular. 
    
6. Em **Descrição do site de equipe,** digite uma descrição do objetivo do site.
    
7. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, em **Adicionar membros**, digite os nomes das contas de usuário que têm acesso a este site de equipe particular.
    
9. Quando você terminar adicionando o conjunto inicial de membros para o site, clique em **Concluir**
    
Esta é a configuração resultante.
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online privado.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a>Sites de equipe do SharePoint Online confidenciais

Um site de equipe do SharePoint Online confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio de associação nos grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.
  
Para criar um site de equipe isolado, há duas etapas principais.
  
### <a name="step-1-design-your-isolated-site"></a>Etapa 1: Criar o seu site isolado

Para criar o seu site de equipe isolado, você precisa determinar:
  
- Seus grupos do SharePoint e níveis de permissão.
    
- O conjunto de grupos de acesso que serão membros de seus grupos do SharePoint.
    
     O conjunto recomendado de grupos de acesso é um para membros do site, um para os visualizadores de site e outra para os administradores de sites.
    
- Se você usará grupos aninhados dentro dos seus grupos de acesso.
    
Por exemplo, os níveis de permissão e estrutura de grupo recomendada semelhante a esta:
  
|**Grupo do SharePoint**|**Nível de permissão**|**Grupo de acesso (exemplos)**|
|:-----|:-----|:-----|
|[nome do site] Membros  <br/> |Editar  <br/> |[nome do site] Membros  <br/> |
|[nome do site] Visitantes  <br/> |Leitura  <br/> |[nome do site] Visualizadores  <br/> |
|[nome do site] Proprietários  <br/> |Controle total  <br/> |[nome do site] Administradores  <br/> |
   
Os grupos do SharePoint e níveis de permissão são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.
  
Para obter detalhes sobre o processo de design, consulte [Design um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).
  
### <a name="step-2-deploy-your-isolated-site"></a>Etapa 2: Implantar seu site isolado

Para implantar seu site isolado, você precisa primeiro:
  
- Determine as contas de usuário e grupos a serem adicionados a cada um dos seus grupos de acesso.
    
- Criar os grupos de acesso e adicione os membros de grupo e usuário.
    
Para obter etapas detalhadas, consulte **Phase 1** de [implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).
  
Em seguida, você cria o site da equipe do SharePoint Online com estas etapas.
  
1. Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** novo do seu navegador, clique em **+ Criar site**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do Site**, digite um nome para o site de equipe particular.
    
6. Na **Descrição do site de equipe**, digite uma descrição opcional.
    
7. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
Em seguida, do novo site de equipe do SharePoint Online, configure permissões com estas etapas.
  
1. Determinar o nome Principal de usuário (UPN) do administrador de TI ou outra pessoa de quem será responsável para responder e lidando com as solicitações de acesso ao site (belindan@contoso.com é um exemplo de um UPN). Gravar esse UPN aqui: _.
    
2. Na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
3. No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.
    
4. Na guia **permissões** novo do navegador, clique em **Configurações de solicitação de acesso**.
    
5. Na caixa de diálogo **Configurações de solicitações de acesso** :
    
  - Desmarque as caixas de seleção **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** .
    
  - Digite o UPN do seu administrador de TI da etapa 1 na **Enviar todas as solicitações de acesso**.
    
  - Clique em **OK**.
    
6. Na guia **permissões** do seu navegador, clique em **membros do [nome do site]** na lista.
    
7. Em **pessoas e grupos**, clique em **novo**.
    
8. Na caixa de diálogo **compartilhamento** , digite o nome do seu grupo de acesso de membros do site para este site, selecioná-la e, em seguida, clique em **compartilhar**.
    
9. Clique no botão voltar de seu navegador.
    
10. Na lista, clique em **[nome do site] proprietários** .
    
11. Em **pessoas e grupos**, clique em **novo**.
    
12. Na caixa de diálogo **compartilhamento** , digite o nome do grupo de acesso de administradores de site para este site, selecioná-la e, em seguida, clique em **compartilhar**.
    
13. Clique no botão voltar de seu navegador.
    
14. Clique em **visitantes do [nome do site]** na lista.
    
15. Em **pessoas e grupos**, clique em **novo**.
    
16. Na caixa de diálogo **compartilhamento** , digite o nome do grupo de acesso ao site visualizadores para esse site, selecioná-la e, em seguida, clique em **compartilhar**.
    
17. Feche a guia **permissões** do navegador.
    
Os resultados dessas configurações de permissão são:
  
- Os **proprietários do [nome do site]** grupo do SharePoint contém o grupo de acesso de administradores de site, no quais todos os membros têm o nível de permissão **controle total** .
    
- Os **membros do [nome do site]** grupo do SharePoint contém o grupo de acesso de membros do site, no quais todos os membros têm o nível de permissão **Editar** .
    
- **Visitantes do [nome do site]** grupo do SharePoint contém site grupo visualizadores de acesso, no quais todos os membros têm o nível de permissão de **leitura** .
    
- A capacidade de membros convidar outros membros está desabilitada.
    
- A capacidade de membros solicitar acesso está habilitada.
    
Esta é a configuração resultante.
  
![Proteção de nível confidencial para um site de equipe isolado do SharePoint Online.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
Os membros do site, por meio de associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança com os recursos do site.
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a>Altamente confidenciais sites de equipe do SharePoint Online

Um site de equipe do SharePoint Online altamente confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio de associação nos grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.
  
Para criar um site de equipe isolado informações altamente confidenciais e colaboração, há duas etapas principais.
  
### <a name="step-1-design-your-isolated-site"></a>Etapa 1: Criar o seu site isolado

Para criar o seu site de equipe isolado, você precisa determinar:
  
- Seus grupos do SharePoint e níveis de permissão.
    
- O conjunto de grupos de acesso que serão membros de seus grupos do SharePoint.
    
     O conjunto recomendado de grupos de acesso é um para membros do site, um para os visualizadores de site e outra para os administradores de sites.
    
- Se você usará grupos aninhados dentro dos seus grupos de acesso.
    
Por exemplo, os níveis de permissão e estrutura de grupo recomendada semelhante a esta:
  
|**Grupo do SharePoint**|**Nível de permissão**|**Grupo de acesso (exemplos)**|
|:-----|:-----|:-----|
|[nome do site] Membros  <br/> |Editar  <br/> |[nome do site] Membros  <br/> |
|[nome do site] Visitantes  <br/> |Leitura  <br/> |[nome do site] Visualizadores  <br/> |
|[nome do site] Proprietários  <br/> |Controle total  <br/> |[nome do site] Administradores  <br/> |
   
Os grupos do SharePoint e níveis de permissão são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.
  
Para obter detalhes sobre o processo de design, consulte [Design um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).
  
### <a name="step-2-deploy-your-isolated-site"></a>Etapa 2: Implantar seu site isolado

Para implantar seu site isolado, você precisa primeiro:
  
- Determinar os membros de grupo e usuário de cada um dos seus grupos de acesso
    
- Criar os grupos de acesso e adicionar os membros de grupo e usuário
    
- Criar um site de equipe isolado que usa os grupos de acesso
    
Para obter etapas detalhadas, consulte [Deploy um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).
  
Os resultados das configurações de permissão são:
  
- Os **proprietários do [nome do site]** grupo do SharePoint contém o grupo de acesso de administradores de site, no quais todos os membros têm o nível de permissão **controle total** .
    
- Os **membros do [nome do site]** grupo do SharePoint contém o grupo de acesso de membros do site, no quais todos os membros têm o nível de permissão **Editar** .
    
- **Visitantes do [nome do site]** grupo do SharePoint contém site grupo visualizadores de acesso, no quais todos os membros têm o nível de permissão de **leitura** .
    
- A capacidade de membros convidar outros membros está desabilitada.
    
- A capacidade de membros solicitar acesso está desabilitada.
    
Esta é a configuração resultante.
  
![Proteção com alto nível de confidencialidade para um site de equipe isolado do SharePoint Online.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
Os membros do site, por meio de associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança com os recursos do site.
  
## <a name="next-step"></a>Próxima etapa

[Proteger os arquivos do SharePoint Online com o Office 365 rótulos e DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a>Veja também

[Proteja arquivos e sites do SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteger sites do SharePoint Online em um ambiente de desenvolvimento e teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




