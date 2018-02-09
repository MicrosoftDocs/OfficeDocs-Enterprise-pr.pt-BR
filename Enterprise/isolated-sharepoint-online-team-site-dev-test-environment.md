---
title: Isolado ambiente de desenvolvimento e teste de site equipe do SharePoint Online
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
description: "Resumo: Configure um site de equipe do SharePoint Online que é isolado do resto da organização em seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: 997c5cf236a795f4846718cc8864997799a1d966
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>Isolado ambiente de desenvolvimento e teste de site equipe do SharePoint Online

 **Resumo:** Configure um site de equipe do SharePoint Online que é isolado do resto da organização em seu ambiente de desenvolvimento e teste do Office 365.
  
Sites de equipe do SharePoint Online no Office 365 são locais para colaboração usando uma biblioteca de documentos comuns, um bloco de anotações do OneNote e outros serviços. Em muitos casos, você deseja acesso ampla e a colaboração entre departamentos ou empresas. No entanto, em alguns casos, você deseja controlar rigorosamente o acesso e permissões para a colaboração entre um pequeno grupo de pessoas.
  
Acesso a sites de equipe do SharePoint Online e os usuários podem fazer é controlado por níveis de permissão e grupos do SharePoint. Por padrão, os sites do SharePoint Online tem três níveis de acesso:
  
- **Membros**, que pode exibir, criar e modificar os recursos no site.
    
- **Proprietários**, que têm controle completo do site, incluindo a capacidade de alterar permissões.
    
- **Visitantes**, que só podem exibir recursos no site.
    
Etapas neste artigo, você pela configuração de um site de equipe do SharePoint Online isolado para um projeto de pesquisa secreta denominado ProjectX. Os requisitos de acesso são:
  
- Somente os membros do projeto podem acessar o site e seu conteúdo (documentos, Bloco de Anotações do OneNote, Páginas), com níveis de permissão de edição e exibição do SharePoint controlados por meio de associação de grupo.
    
- Somente o criador do site e os membros de um grupo de Administradores do site podem executar a administração do site, a qual inclui modificação de permissões no nível do site.
    
Há três fases para configurar um site de equipe do SharePoint Online isolado em seu ambiente de desenvolvimento e teste do Office 365:
  
1. Crie o ambiente de desenvolvimento e teste do Office 365.
    
2. Criação de usuários e grupos para o Projeto X.
    
3. Isolar e criar um novo site de equipe ProjectX SharePoint Online.
    
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada

Se você deseja criar um site de equipe do SharePoint Online isolado de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você deseja criar um site de equipe do SharePoint Online isolado em uma configuração de enterprise simulado, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> A criação de um site isolado do SharePoint Online não exige o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do AD no Windows Server. Ele é fornecido aqui como uma opção para que você possa testar um site do SharePoint Online isolado e fazer testes com ele em um ambiente que representa uma organização comum. 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>Fase 2: Criar contas de usuário e grupos de acesso

Use as instruções em [conectar-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para se conectar à sua assinatura de trilha do Office 365 com sua conta de administrador global do:
  
- Seu computador (para o ambiente leve de desenvolvimento/teste do Office 365).
    
- A máquina virtual CLIENT1 (para o ambiente de desenvolvimento e teste de enterprise simulado Office 365).
    
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

Na exibição do comando **New-MsolUser** , observe a gerado senha da conta de liderança de Designer e registre-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

Na exibição do comando **New-MsolUser** , observe a senha gerada para a conta do Pesquisador liderança e registre-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

Na exibição do comando **New-MsolUser** , observe a gerado senha da conta de vice-Presidente de desenvolvimento e registre-a em um local seguro.
  
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

![Os grupos do Office 365 e seus membros para um site de Grupo do SharePoint Online isolado](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>Fase 3: Isolar e criar um novo site de equipe ProjectX SharePoint Online

Para criar um site de equipe do SharePoint Online para ProjectX, faça o seguinte:
  
1. Usando um navegador em um computador local (configuração leve) ou no CLIENT1 (configuração enterprise simulados), entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia SharePoint nova no seu navegador, clique em **Criar site +**.
    
4. Em **nome do site de equipe**, digite **ProjectX**. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**.
    
5. Em **Descrição do site de equipe**, digite o **site do SharePoint para ProjectX**e clique em **Avançar**.
    
6. No **que você deseja adicionar**? painel, clique em **Concluir**.
    
7. Na guia **Home ProjectX** novo em seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
8. No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.
    
9. Na nova **permissões: Project X** no seu navegador, clique em **Configurações de solicitação de acesso**.
    
10. Na caixa de diálogo **Configurações de solicitações de acesso** , desmarque **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **solicitações de acesso permitir** (de forma que todas as três caixas de seleção estiver desmarcadas) e clique em **Okey**.
    
11. Clique em **ProjectX membros** na lista.
    
12. Na página **pessoas e grupos** , clique em **novo**.
    
13. Na caixa de diálogo **compartilhar** , digite **ProjectX-membros**, selecioná-la e, em seguida, clique em **compartilhar**.
    
14. Clique no botão voltar de seu navegador.
    
15. Na lista, clique em **ProjectX proprietários** .
    
16. Na página **pessoas e grupos** , clique em **novo**.
    
17. Na caixa de diálogo **compartilhar** , digite **ProjectX-Admins**, selecioná-la e, em seguida, clique em **compartilhar**.
    
18. Clique no botão voltar de seu navegador.
    
19. Clique em **Visitantes ProjectX** na lista.
    
20. Na página **pessoas e grupos** , clique em **novo**.
    
21. Na caixa de diálogo **compartilhar** , digite **ProjectX-visualizadores**, selecioná-la e, em seguida, clique em **compartilhar**.
    
22. Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Página inicial do ProjectX** no seu navegador e, em seguida, feche o painel de **permissões do Site** .
    
Estes são os resultados da configuração das permissões:
  
- ProjectX grupo membros do SharePoint contém apenas o grupo de acesso de membros de ProjectX (que contém apenas as contas de usuário liderança Designer e o Pesquisador de liderança) e o grupo ProjectX (que contém a conta de usuário administrador global).
    
- O grupo de proprietários do SharePoint ProjectX contém apenas o grupo de acesso ProjectX-Admins (que contém a conta de usuário administrador global).
    
- O grupo do SharePoint de visitantes ProjectX contém apenas ProjectX-grupo visualizadores de acesso (que contém a conta de usuário vice-Presidente de desenvolvimento).
    
- Os membros não podem modificar as permissões no nível do site (isso só pode ser feito por membros do grupo Projeto X-Administradores).
    
- Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar acesso ao site.
    
A Figura 2 mostra os grupos do SharePoint e suas associações.
  
**Figura 2**

![Os grupos do SharePoint Online e seus membros para um site de Grupo do SharePoint Online isolado](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
Agora vamos demonstrar usando a conta de usuário do Designer de liderança de acesso:
  
1. Fechar a guia **Página inicial do ProjectX** no seu navegador e, em seguida, clique na guia **Página inicial do Microsoft Office** no seu navegador.
    
2. Clique no nome do administrador global e clique em **Sair**.
    
3. Entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando o nome da conta de liderança de Designer e sua senha.
    
4. Na lista de blocos, clique em **SharePoint**.
    
5. Na guia **SharePoint** nova no seu navegador, digite **ProjectX** na caixa Pesquisar, ativar a pesquisa e, em seguida, clique no site de equipe do **ProjectX** . Você deverá ver uma nova guia no seu navegador para o site de equipe ProjectX.
    
6. Clique no ícone configurações. Observe que não há nenhuma opção **As permissões**do Site. Isso é correto porque apenas os membros do grupo Administradores de ProjectX podem modificar permissões no site
    
7. Abra o bloco de notas ou um editor de texto de sua escolha.
    
8. Copie a URL do site da equipe ProjectX e colá-lo em uma nova linha no bloco de notas ou o editor de texto.
    
9. Na guia **Home ProjectX** nova no seu navegador, clique em **documentos**.
    
10. Copie a URL da pasta de documentos do Projeto X e cole-a em uma nova linha no Bloco de Notas ou em seu editor de texto.
    
11. Na guia **ProjectX-documentos** nova no seu navegador, clique em **New > documento do Word**.
    
12. Digite algum texto na página do **Word Online** , aguarde o status para indicar **salvo**, clique no botão Voltar do navegador e, em seguida, atualize a página. Você deverá ver uma nova **Document.docx** na pasta **Documents** .
    
13. Clique nas reticências para o documento **Document.docx** e clique em **obter um link**.
    
14. Copie a URL na caixa de diálogo **Compartilhar 'Document.docx'** e colá-lo em uma nova linha no bloco de notas ou o editor de texto e, em seguida, feche a caixa de diálogo **Compartilhar 'Document.docx'** .
    
15. Fechar as guias **SharePoint** e **ProjectX-documentos** no seu navegador e, em seguida, clique na guia **Página inicial do Microsoft Office** .
    
16. Clique no nome do **Designer de liderança** e clique em **Sair**.
    
Agora vamos demonstrar access usando a conta de usuário vice-Presidente de desenvolvimento:
  
1. Entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando o nome da conta vice-Presidente de desenvolvimento e sua senha.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, digite **ProjectX** na caixa Pesquisar, ativar a pesquisa e, em seguida, clique no site de equipe do **ProjectX** . Você deverá ver uma nova guia no seu navegador para o site de equipe ProjectX.
    
4. Clique em **documentos**e, em seguida, clique no arquivo de **Document.docx** .
    
5. Na guia **Document.docx** no seu navegador, tente modificar o texto. Você verá uma mensagem informando **esse documento é somente leitura.** Isso é esperado porque a conta de usuário vice-Presidente de desenvolvimento só tem permissões de exibição para o site.
    
6. Feche as guias **Document.docx**, **ProjectX-documentos**e **SharePoint** no seu navegador.
    
7. Clique na guia **Página inicial do Microsoft Office** , clique no nome de **Vice -Presidente de desenvolvimento** e, em seguida, clique em **Sair**.
    
Agora vamos demonstrar acesso com uma conta de usuário que não possui permissões:
  
1. Entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando o nome da conta de usuário 3 e sua senha.
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, digite **ProjectX** na caixa Pesquisar e, em seguida, ativar a pesquisa. Você verá a mensagem **nada aqui se compara à sua pesquisa.**
    
4. Da instância aberta do bloco de notas ou o editor de texto, copie o URL para o site ProjectX na barra de endereços do navegador e pressione **Enter**. Você deverá ver uma página de **Acesso negado** .
    
5. No bloco de notas ou o editor de texto, copie a URL para a pasta de documentos ProjectX na barra de endereços do navegador e pressione **Enter**. Você deverá ver uma página de **Acesso negado** .
    
6. No bloco de notas ou o editor de texto, copie o URL para o arquivo Documents.docx na barra de endereços do navegador e pressione **Enter**. Você deverá ver uma página de **Acesso negado** .
    
7. Fechar a guia do **SharePoint** no seu navegador, clique na guia **Página inicial do Microsoft Office** , clique no nome de **usuário 3** e clique em **Sair**.
    
Site do SharePoint Online isolado agora está pronto para sua experimentação adicional.
  
## <a name="next-step"></a>Próxima etapa

Quando estiver pronto para implantar um site de equipe do SharePoint Online isolado em produção, consulte as considerações de design passo a passo em [um site de equipe do SharePoint Online isolado de Design](design-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Veja também

[Isolado sites de equipe do SharePoint Online](isolated-sharepoint-online-team-sites.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento e teste de configuração de base](base-configuration-dev-test-environment.md)
  
[Ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




