---
title: Site de equipe do SharePoint Online isolado no seu ambiente de desenvolvimento/teste
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
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: 'Resumo: Configure um site de equipe do SharePoint Online que é isolado do resto da organização em seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: d2a75f3a3a410116c454892c9ecf3747fb3da53d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915046"
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>Site de equipe do SharePoint Online isolado no seu ambiente de desenvolvimento/teste

 **Resumo:** Configure um site de equipe do SharePoint Online que é isolado do resto da organização em seu ambiente de desenvolvimento e teste do Office 365.
  
Sites de equipe do SharePoint Online no Office 365 são locais para colaboração usando uma biblioteca de documentos comuns, um bloco de anotações do OneNote e outros serviços. Em muitos casos, você deseja acesso ampla e a colaboração entre departamentos ou empresas. No entanto, em alguns casos, você deseja controlar rigorosamente o acesso e permissões para a colaboração entre um pequeno grupo de pessoas.
  
Acesso a sites de equipe do SharePoint Online e os usuários podem fazer é controlado por níveis de permissão e grupos do SharePoint. Por padrão, os sites do SharePoint Online tem três níveis de acesso:
  
- **Membros**, que podem exibir, criar e modificar recursos no site.
    
- **Proprietários**, que têm controle total do site, incluindo a capacidade de alterar permissões.
    
- **Visitantes**, que só podem exibir recursos no site.
    
Etapas neste artigo, você pela configuração de um site de equipe do SharePoint Online isolado para um projeto de pesquisa secreta denominado ProjectX. Os requisitos de acesso são:
  
- Somente os membros do projeto podem acessar o site e seu conteúdo (documentos, Bloco de Anotações do OneNote, Páginas), com níveis de permissão de edição e exibição do SharePoint controlados por meio de associação de grupo.
    
- Somente o criador do site e os membros de um grupo de Administradores do site podem executar a administração do site, a qual inclui modificação de permissões no nível do site.
    
Há três fases para configurar um site de equipe do SharePoint Online isolado em seu ambiente de desenvolvimento e teste do Office 365:
  
1. Criação do ambiente de desenvolvimento/teste do Office 365.

    
2. Criação de usuários e grupos para o Projeto X.
    
3. Isolar e criar um novo site de equipe ProjectX SharePoint Online.
    
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada

Se você deseja criar um site de equipe do SharePoint Online isolado de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você deseja criar um site de equipe do SharePoint Online isolado em uma configuração de enterprise simulado, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> A criação de um site isolado do SharePoint Online não exige o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do AD no Windows Server. Ele é fornecido aqui como uma opção para que você possa testar um site do SharePoint Online isolado e fazer testes com ele em um ambiente que representa uma organização comum. 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>Fase 2: Criar contas de usuário e grupos de acesso

Use as instruções em [conectar-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para se conectar à sua assinatura de trilha do Office 365 com sua conta de administrador global do:
  
- Seu computador (para o ambiente leve de desenvolvimento/teste do Office 365).
    
- A máquina virtual CLIENT1 (para o ambiente de desenvolvimento/teste corporativo simulado do Office 365).
    
Para criar os novos grupos de acesso para o site de equipe ProjectX SharePoint Online, execute estes comandos a partir do prompt do Windows Azure Active Directory módulo para Windows PowerShell:
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) para um arquivo de texto que contém todos os comandos do PowerShell neste artigo.
  
Preencha o nome de sua organização (exemplo: contosotoycompany), o código de país com dois caracteres de seu local e execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

Na exibição do comando **New-MsolUser**, anote a senha gerada para a conta de Designer Chefe e grave-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

Na exibição do comando **New-MsolUser**, anote a senha gerada para a conta de Pesquisador Chefe e grave-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

Na exibição do comando **New-MsolUser**, anote a senha gerada para a conta de VP de Desenvolvimento e grave-a em um local seguro.
  
Em seguida, para adicionar as novas contas para os novos grupos de acesso, execute estes comandos do PowerShell do prompt do Windows Azure Active Directory módulo para Windows PowerShell:
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

Resultados:
  
- O grupo de acesso de membros de ProjectX contém as contas de usuário liderança Designer e o Pesquisador de liderança
    
- O grupo de acesso ProjectX-Admins contém a conta de administrador global para a sua assinatura de avaliação
    
- O grupo de acesso ProjectX-visualizadores contém a conta de usuário vice-Presidente de desenvolvimento
    
A Figura 1 mostra os grupos de acesso e seus membros.
  
**Figura 1**

![Os grupos do Office 365 e seus membros para um site de Grupo do SharePoint Online isolado](media/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>Fase 3: Isolar e criar um novo site de equipe ProjectX SharePoint Online

Para criar um site de equipe do SharePoint Online para ProjectX, faça o seguinte:
  
1. Usando um navegador em um computador local (configuração leve) ou no CLIENT1 (configuração enterprise simulados), entre no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na nova guia SharePoint no navegador, clique em **+ Criar site**.
    
4. Em **nome do site de equipe**, digite **ProjectX**. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**.
    
5. Em **Descrição do site de equipe**, digite **Site do SharePoint para o Projeto X** e clique em **Avançar**.
    
6. No **que você deseja adicionar**? painel, clique em **Concluir**.
    
7. Na nova guia **Projeto X-Página Inicial** em seu navegador, na barra de ferramentas, clique no ícone de configurações e depois clique em **Permissões do site**.
    
8. No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.
    
9. Na nova guia **Permissões: Projeto X** em seu navegador, clique em **Configurações de Solicitação de Acesso**.
    
10. Na caixa de diálogo **Configurações de Solicitações de Acesso**, desmarque **Permitir que os membros compartilhem o site e arquivos e pastas individuais** e **Permitir solicitações de acesso** (para que todas as três caixas de seleção sejam desmarcadas) e, depois, clique em **OK**.
    
11. Clique em **Membros do Projeto X** na lista.
    
12. Na página **Pessoas e Grupos**, clique em **Novo**.
    
13. Na caixa de diálogo **Compartilhar**, digite **Projeto X-Membros**, selecione-o e clique em **Compartilhar**.
    
14. Clique no botão Voltar de seu navegador.
    
15. Clique em **Proprietários do Projeto X** na lista.
    
16. Na página **Pessoas e Grupos**, clique em **Novo**.
    
17. Na caixa de diálogo **Compartilhar**, digite **Projeto X-Administradores**, selecione-o e clique em **Compartilhar**.
    
18. Clique no botão Voltar de seu navegador.
    
19. Clique em **Visitantes do Projeto X** na lista.
    
20. Na página **Pessoas e Grupos**, clique em **Novo**.
    
21. Na caixa de diálogo **Compartilhar**, digite **Projeto X-Visualizadores**, selecione-o e clique em **Compartilhar**.
    
22. Feche a guia **Pessoas e Grupos** em seu navegador, clique na guia **Projeto X-Página Inicial** em seu navegador e feche o painel **Permissões do site**.

    
Aqui estão os resultados da configuração de permissões:
  
- ProjectX grupo membros do SharePoint contém apenas o grupo de acesso de membros de ProjectX (que contém apenas as contas de usuário liderança Designer e o Pesquisador de liderança) e o grupo ProjectX (que contém a conta de usuário administrador global).
    
- O grupo de proprietários do SharePoint ProjectX contém apenas o grupo de acesso ProjectX-Admins (que contém a conta de usuário administrador global).
    
- O grupo do SharePoint de visitantes ProjectX contém apenas ProjectX-grupo visualizadores de acesso (que contém a conta de usuário vice-Presidente de desenvolvimento).
    
- Os membros não podem modificar as permissões no nível do site (isso só pode ser feito por membros do grupo Projeto X-Administradores).
    
- Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar acesso ao site.
    
A Figura 2 mostra os grupos do SharePoint e suas associações.
  
**Figure 2**

![Os grupos do SharePoint Online e seus membros para um site de Grupo do SharePoint Online isolado](media/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
Agora vamos demonstrar usando a conta de usuário do Designer de liderança de acesso:
  
1. Feche a guia **Projeto X-Página Inicial** em seu navegador e clique na guia **Microsoft Office Home** em seu navegador.
    
2. Clique no nome do administrador global e clique em **Sair**.
    
3. Entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando o nome da conta de liderança de Designer e sua senha.
    
4. Na lista de blocos, clique em **SharePoint**.
    
5. Na guia **SharePoint** nova no seu navegador, digite **ProjectX** na caixa Pesquisar, ativar a pesquisa e, em seguida, clique no site de equipe do **ProjectX** . Você deverá ver uma nova guia no seu navegador para o site de equipe ProjectX.
    
6. Clique no ícone de configurações. Observe que não há opção para **Permissões de Site**. Isso está correto, pois somente os membros do grupo Projeto X-Administradores podem modificar as permissões no site
    
7. Abra o bloco de notas ou um editor de texto de sua escolha.
    
8. Copie a URL do site da equipe ProjectX e colá-lo em uma nova linha no bloco de notas ou o editor de texto.
    
9. Na nova guia **Projeto X-Página Inicial** em seu navegador, clique em **Documentos**.
    
10. Copie a URL da pasta de documentos do Projeto X e cole-a em uma nova linha no Bloco de Notas ou em seu editor de texto.
    
11. Na nova guia **Projeto X-Documentos** em seu navegador, clique em **Novo > Documento do Word**.
    
12. Digite algum texto na página **Word Online**, aguarde até o status indicar **Salvo**, clique no botão Voltar de seu navegador e atualize a página. Você deverá ver um novo **Document.docx** na pasta **Documentos**.
    
13. Clique nas reticências do documento **Document.docx** e clique em **Obter um link**.
    
14. Copie a URL na caixa de diálogo **Compartilhar 'Document.docx'** e colá-lo em uma nova linha no bloco de notas ou o editor de texto e, em seguida, feche a caixa de diálogo **Compartilhar 'Document.docx'** .
    
15. Feche as guias **Projeto X-Documentos** e **SharePoint** em seu navegador e clique na guia **Microsoft Office Home**.
    
16. Clique no nome **Designer Chefe** e clique em **Sair**.

    
Agora vamos demonstrar access usando a conta de usuário vice-Presidente de desenvolvimento:
  
1. Entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando o nome da conta vice-Presidente de desenvolvimento e sua senha.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, digite **ProjectX** na caixa Pesquisar, ativar a pesquisa e, em seguida, clique no site de equipe do **ProjectX** . Você deverá ver uma nova guia no seu navegador para o site de equipe ProjectX.
    
4. Clique em **Documentos** e clique no arquivo **Document.docx**.
    
5. Na guia **Document.docx** em seu navegador, tente modificar o texto. Você deve ver uma mensagem informando que **Este documento é somente leitura.** Isso é esperado, pois a conta de usuário de VP de Desenvolvimento só tem permissões de exibição no site.
    
6. Feche as guias **Document.docx**, **Projeto X-Documentos** e **SharePoint** em seu navegador.
    
7. Clique na guia **Microsoft Office Home**, clique no nome **VP de Desenvolvimento** e clique em **Sair**.

    
Agora vamos demonstrar acesso com uma conta de usuário que não possui permissões:
  
1. Entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando o nome da conta de usuário 3 e sua senha.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. 	Na nova guia **SharePoint** em seu navegador, digite **Projeto X** na caixa de pesquisa e ative a pesquisa. Você deverá ver a mensagem **Não houve resultados para sua pesquisa.**
    
4. Na instância aberta do Bloco de Notas ou de seu editor de texto, copie a URL do site do Projeto X na barra de endereços de seu navegador e pressione **Enter**. Você deverá ver uma página **Acesso Negado**.
    
5. No Bloco de Notas ou seu editor de texto, copie a URL da pasta Documentos do Projeto X e cole-a na barra de endereços de seu navegador e pressione **Enter**. Você deverá ver uma página **Acesso Negado**.
    
6. No Bloco de Notas ou seu editor de texto, copie a URL do arquivo Documents.docx na barra de endereços de seu navegador e pressione **Enter**. Você deverá ver uma página **Acesso Negado**.
    
7. Feche a guia **SharePoint** em seu navegador, clique na guia **Microsoft Office Home**, clique no nome **Usuário 3** e clique em **Sair**.

    
Site do SharePoint Online isolado agora está pronto para sua experimentação adicional.
  
## <a name="next-step"></a>Próxima etapa

Quando estiver pronto para implantar um site de equipe do SharePoint Online isolado na produção, confira as considerações de design passo a passo no [Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Veja também

[Sites de equipe do SharePoint Online isolados](isolated-sharepoint-online-team-sites.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




