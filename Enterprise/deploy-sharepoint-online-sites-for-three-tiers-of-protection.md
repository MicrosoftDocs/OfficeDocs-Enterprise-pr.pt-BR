---
title: Implantar sites do SharePoint Online para três camadas de proteção
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
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: 'Resumo: Criar e configurar sites de equipe do SharePoint Online para diversos níveis de proteção de informações.'
ms.openlocfilehash: ddeb1885cbc74be6e7098660eb1d9906d43739fd
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a>Implantar sites do SharePoint Online para três camadas de proteção

 **Resumo:** Criar e configurar sites de equipe do SharePoint Online para diversos níveis de proteção de informações.
  
Use as etapas neste artigo para projetar e implantar sites de equipe do SharePoint Online de linha de base, confidenciais e altamente confidenciais. Para obter mais informações sobre essas três camadas de proteção, consulte [Arquivos e sites do SharePoint Online seguros](secure-sharepoint-online-sites-and-files.md).
  
## <a name="baseline-sharepoint-online-team-sites"></a>Sites de equipe do SharePoint Online de linha de base

A proteção de linha de base inclui os sites de equipe públicos e privados. Os sites de equipe públicos podem ser descobertos e acessados por qualquer pessoa na organização. Os sites privados podem ser descobertos e acessados somente por membros do grupo do Office 365 associado ao site de equipe. Esses dois tipos de sites de equipe permitem que os membros compartilhem o site com outras pessoas.
  
### <a name="public"></a>Público

Para criar um site de equipe do SharePoint Online de linha de base com permissões e acesso público, faça o seguinte:
  
1. Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.
    
4. Na página **Criar um site**, clique em **Site de equipe**.
    
5. Em **Nome do site**, digite um nome para o site de equipe público. 
    
6. Em **Descrição do site de equipe**, digite uma descrição do objetivo do site.
    
7. Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.
    
8. No painel **Quem você deseja adicionar?**, clique em **Concluir**.
    
Esta é a configuração resultante.
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online público.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a>Private

Para criar um site de equipe do SharePoint Online de linha de base com permissões e acesso privado, faça o seguinte:
  
1. Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.
    
4. Na página **Criar um site**, clique em **Site de equipe**.
    
5. Em **Nome do site**, digite um nome para o site de equipe privado. 
    
6. Em **Descrição do site de equipe,** digite uma descrição do objetivo do site.
    
7. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. No painel **Quem você deseja adicionar?**, em **Adicionar membros**, digite os nomes das contas de usuário que têm acesso a esse site de equipe privado.
    
9. Quando você terminar adicionando o conjunto inicial de membros para o site, clique em **Concluir**
    
Esta é a configuração resultante.
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online privado.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a>Sites de equipe do SharePoint Online confidenciais

Um site de equipe do SharePoint Online confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio da associação em grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.
  
Para criar um site de equipe isolado, há duas etapas principais.
  
### <a name="step-1-design-your-isolated-site"></a>Etapa 1: Projetar o site isolado

Para projetar o site de equipe isolado, você precisa determinar:
  
- Seus níveis de permissão e grupos do SharePoint.
    
- O conjunto de grupos de acesso que serão membros de seus grupos do SharePoint.
    
     O conjunto recomendado de grupos de acesso é um para membros do site, um para os visualizadores de site e outra para os administradores de sites.
    
- Se você usará grupos aninhados dentro de seus grupos de acesso.
    
Por exemplo, os níveis de permissão e estrutura de grupo recomendados têm essa aparência:
  
|**Grupo do SharePoint**|**Nível de permissão**|**Grupo de acesso (exemplos)**|
|:-----|:-----|:-----|
|Membros do [nome do site]  <br/> |Editar  <br/> |Membros do [nome do site]  <br/> |
|Visitantes do [nome do site]  <br/> |Ler  <br/> |Visualizadores do [nome do site]  <br/> |
|Proprietários do [nome do site]  <br/> |Controle total  <br/> |Administradores do [nome do site]  <br/> |
   
Os níveis de permissão e grupos do SharePoint são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.
  
Para obter os detalhes do processo de design, consulte [Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).
  
### <a name="step-2-deploy-your-isolated-site"></a>Etapa 2: Implantar o site isolado

Para implantar seu site isolado, primeiro você precisa:
  
- Determinar as contas de usuário e os grupos a serem adicionados a cada um dos seus grupos de acesso.
    
- Criar os grupos de acesso e adicionar os membros de usuário e grupo.
    
Para obter as etapas detalhadas, consulte a **Fase 1** de [Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).
  
Em seguida, você cria o site da equipe do SharePoint Online com estas etapas.
  
1. Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** novo do seu navegador, clique em **+ Criar site**.
    
4. Na página **Criar um site**, clique em **Site de equipe**.
    
5. Em **Nome do site**, digite um nome para o site de equipe privado.
    
6. Na **Descrição do site de equipe**, digite uma descrição opcional.
    
7. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. No painel **Quem você deseja adicionar?**, clique em **Concluir**.
    
Em seguida, no novo site de equipe do SharePoint Online, configure as permissões com estas etapas.
  
1. Determinar o nome Principal de usuário (UPN) do administrador de TI ou outra pessoa de quem será responsável para responder e lidando com as solicitações de acesso ao site (belindan@contoso.com é um exemplo de um UPN). Gravar esse UPN aqui: _.
    
2. Na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
3. No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.
    
4. Na nova guia **Permissões** do navegador, clique em **Configurações de Solicitação de Acesso**.
    
5. Na caixa de diálogo **Configurações de Solicitações de Acesso**:
    
  - Desmarque as caixas de seleção **Permitir que os membros compartilhem o site e arquivos e pastas individuais** e **Permitir que os membros convidem outras pessoas para o grupo de membros do site**.
    
  - Digite o UPN do seu administrador de TI da etapa 1 em **Enviar todas as solicitações de acesso**.
    
  - Clique em **OK**.
    
6. Na guia **Permissões** do navegador, clique em **Membros do [nome do site]** na lista.
    
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
    
17. Feche a guia **Permissões** do navegador.
    
Os resultados dessas configurações de permissão são:
  
- O grupo do SharePoint **Proprietários do [nome do site]** contém o grupo de acesso de administradores de site, em que todos os membros têm o nível de permissão **Controle total**.
    
- O grupo do SharePoint **Membros do [nome do site]** contém o grupo de acesso de membros de site, em que todos os membros têm o nível de permissão **Editar**.
    
- O grupo do SharePoint **Visitantes do [nome do site]** contém o grupo de acesso de visualizadores de site, em que todos os membros têm o nível de permissão **Ler**.
    
- A capacidade de os membros convidarem outros membros está desabilitada.
    
- A capacidade de não membros solicitarem o acesso está habilitada.
    
Esta é a configuração resultante.
  
![Proteção de nível confidencial para um site de equipe isolado do SharePoint Online.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
Os membros do site, por meio da associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança nos recursos do site.
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a>Sites de equipe do SharePoint Online altamente confidenciais

Um site de equipe do SharePoint Online altamente confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio da associação em grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.
  
Para criar um site de equipe isolado para colaboração e informações altamente confidenciais, há duas etapas principais.
  
### <a name="step-1-design-your-isolated-site"></a>Etapa 1: Projetar o site isolado

Para projetar o site de equipe isolado, você precisa determinar:
  
- Seus níveis de permissão e grupos do SharePoint.
    
- O conjunto de grupos de acesso que serão membros de seus grupos do SharePoint.
    
     O conjunto recomendado de grupos de acesso é um para membros do site, um para os visualizadores de site e outra para os administradores de sites.
    
- Se você usará grupos aninhados dentro de seus grupos de acesso.
    
Por exemplo, os níveis de permissão e estrutura de grupo recomendados têm essa aparência:
  
|**Grupo do SharePoint**|**Nível de permissão**|**Grupo de acesso (exemplos)**|
|:-----|:-----|:-----|
|Membros do [nome do site]  <br/> |Editar  <br/> |Membros do [nome do site]  <br/> |
|Visitantes do [nome do site]  <br/> |Ler  <br/> |Visualizadores do [nome do site]  <br/> |
|Proprietários do [nome do site]  <br/> |Controle total  <br/> |Administradores do [nome do site]  <br/> |
   
Os níveis de permissão e grupos do SharePoint são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.
  
Para obter os detalhes do processo de design, consulte [Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).
  
### <a name="step-2-deploy-your-isolated-site"></a>Etapa 2: Implantar o site isolado

Para implantar seu site isolado, primeiro você precisa:
  
- Determinar os membros de grupo e usuário de cada um dos seus grupos de acesso
    
- Criar os grupos de acesso e adicionar os membros de grupo e usuário
    
- Criar um site de equipe isolado que usa os grupos de acesso
    
Para obter as etapas detalhadas, consulte [Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).
  
Os resultados das configurações de permissão são:
  
- O grupo do SharePoint **Proprietários do [nome do site]** contém o grupo de acesso de administradores de site, em que todos os membros têm o nível de permissão **Controle total**.
    
- O grupo do SharePoint **Membros do [nome do site]** contém o grupo de acesso de membros de site, em que todos os membros têm o nível de permissão **Editar**.
    
- O grupo do SharePoint **Visitantes do [nome do site]** contém o grupo de acesso de visualizadores de site, em que todos os membros têm o nível de permissão **Ler**.
    
- A capacidade de os membros convidarem outros membros está desabilitada.
    
- A capacidade de não membros solicitarem o acesso está desabilitada.
    
Aqui está a configuração resultante.
  
![Proteção com alto nível de confidencialidade para um site de equipe isolado do SharePoint Online.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
Os membros do site, por meio da associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança nos recursos do site.
  
## <a name="next-step"></a>Próxima etapa

[Proteger os arquivos do SharePoint Online com o Office 365 rótulos e DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a>Confira também

[Proteger sites e arquivos do SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




