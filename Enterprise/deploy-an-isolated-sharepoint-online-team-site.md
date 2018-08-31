---
title: Implantar um site de equipe do SharePoint Online isolado
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: 'Resumo: Implante um novo isolado SharePoint Online site de equipe com estas instruções passo a passo.'
ms.openlocfilehash: e71564248716523a53fcdda48f3a9fdc6349a2c5
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914946"
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>Implantar um site de equipe do SharePoint Online isolado

 **Resumo:** Implante um novo isolado SharePoint Online site de equipe com estas instruções passo a passo.
  
Este artigo é um guia passo a passo de implantação para criar e configurar um site de equipe do SharePoint Online isolado em Microsoft Office 365. Essas etapas pressupõem o uso dos três grupos padrão do SharePoint e níveis de permissão correspondente, com um grupo único de acesso baseado no AD do Windows Azure Active Directory para cada nível de acesso.
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>Fase 1: Crie e preencha os grupos de acesso do site de equipe

Nesta fase, você cria os três grupos Azure acesso baseado em AD para os grupos padrão de três do SharePoint e preenchê-los com as contas de usuário apropriada.
  
> [!NOTE]
> As etapas a seguir pressupõem que todas as contas de usuário necessários já existirem e recebem as licenças apropriadas. Caso contrário, adicione-os e atribuir licenças antes de prosseguir para a etapa 1. 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>Etapa 1: Listar os administradores do SharePoint Online para o site

Determine que o conjunto de usuário contas correspondente ao grupo de administradores do SharePoint Online para o site de equipe isolado.
  
Se você está gerenciando contas de usuários e grupos por meio do Office 365 e deseja usar o Windows PowerShell, faça uma lista dos seus usuários nomes principais (UPNs) (exemplo UPN: belindan@contoso.com).
  
### <a name="step-2-list-the-members-for-the-site"></a>Etapa 2: Listam os membros do site

Determine o conjunto de contas de usuário correspondente aos membros para o site de equipe isolado, aqueles que vai ser colaborando em recursos armazenados dentro do site.
  
Se você está gerenciando contas de usuários e grupos por meio do Office 365 e deseja usar o PowerShell, faça uma lista de seus UPNs. Se houver muitos membros do site, você pode armazenar a lista de UPNs em um arquivo de texto e adicioná-los a todos com um único comando do PowerShell.
  
### <a name="step-3-list-the-viewers-for-the-site"></a>Etapa 3: Listar os visualizadores para o site

Determine o conjunto de contas de usuário correspondente para os visualizadores do site da equipe isolado, aqueles que pode exibir os recursos armazenados no site, mas não modificá-los ou colaborar diretamente em seu conteúdo.
  
Se você está gerenciando contas de usuários e grupos por meio do Office 365 e deseja usar o PowerShell, faça uma lista de seus UPNs. Se houver muitos membros do site, você pode armazenar a lista de UPNs em um arquivo de texto e adicioná-los a todos com um único comando do PowerShell.
  
Visualizadores para o site podem incluir a gerência executiva, assessores jurídicos ou inter-departmental participantes.
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>Etapa 4: Criar os grupos de três do access para o site no Windows Azure AD

Você precisa criar os seguintes grupos de acesso no Azure AD:
  
- Administradores de site (que conterão a lista da etapa 1)
    
- Membros do site (que conterão a lista da etapa 2)
    
- Visitantes do site (que conterão a lista da etapa 3)
    
1. No seu navegador, vá para o portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com) e entre com as credenciais de uma conta que tenha sido atribuída com função de administrador de gerenciamento de usuários ou administrador da empresa.
    
2. No Portal do Azure, clique em **Azure Active Directory > Grupos**.
    
3. Na folha **Grupos – Todos os grupos**, clique em **+ Novo grupo**.
    
4. Na folha **Grupo**:
    
  - Escolha **Office 365** em **Tipo de Grupo**.
    
  - Digite o nome do grupo no **nome**.
    
  - Digite uma descrição do grupo na **Descrição do grupo**.
    
  - Escolha **Atribuído** em **Tipo de Associação**.
    
5. Clique em **Criar** e, em seguida, feche a folha **Grupo**.
    
6. Repita as etapas 3 a 5 para os grupos adicionais.
    
> [!NOTE]
> Você precisará usar o portal do Windows Azure para criar os grupos para que eles tenham os recursos do Office habilitados. Se um site do SharePoint Online isolado posteriormente é configurado como um site altamente confidenciais com um rótulo de proteção de informações do Windows Azure (AIP) para criptografar arquivos e atribuir permissões a grupos específicos, os grupos permitidos devem ter sido criados com os recursos do Office habilitado. Você não pode alterar a configuração de recursos do Office de um grupo do Windows Azure AD após ele ter sido criado. 
  
Aqui está a configuração resultante com os grupos de acesso de três do site.
  
![Os três grupos de acesso para sua implantação de um site isolado do SharePoint Online.](media/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>Etapa 5. Adicione as contas de usuário para os grupos de acesso

Nesta etapa, faça o seguinte:
  
1. Adicionar a lista de usuários da etapa 1 ao grupo de acesso de administradores de site
    
2. Adicionar a lista de usuários da etapa 2 para o grupo de acesso de membros do site
    
3. Adicionar a lista de usuários da etapa 3, ao grupo de acesso do site visualizadores
    
Se você está gerenciando contas de usuários e grupos por meio do Windows Server AD, adicione usuários aos grupos de acesso apropriado usando seu usuário normal do Windows Server AD e procedimentos de gerenciamento de grupo e aguarde a sincronização com sua assinatura do Office 365.
  
Se você estiver gerenciando contas de usuários e grupos por meio do Office 365, você pode usar o Centro de administração do Office ou do PowerShell. Se você tiver os nomes de grupo duplicado para qualquer um dos grupos de acesso, você deve usar o Centro de administração do Office.
  
Para o Centro de administração do Office, entrar com uma conta de usuário que tenha sido atribuída a função de administrador da conta de usuário ou administrador da empresa e use grupos para adicionar as contas de usuário apropriados e para os grupos de acesso apropriado.
  
Para o PowerShell, primeiro [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Em seguida, use o seguinte bloco de comando para adicionar uma conta de usuário individual para um grupo de acesso:
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> Para um arquivo de texto que contém todos os comandos do PowerShell e um Excel planilha de configuração que gera os comandos do PowerShell com base no seu grupo e usuário nomes de conta, baixe o [Isolado SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907). 
  
Se você armazenou os UPNs das contas de usuário para qualquer um dos grupos de acesso em um arquivo de texto, você pode usar o seguinte bloco de comando do PowerShell para adicioná-los todos ao mesmo tempo:
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

Para PowerShell, use o seguinte bloco de comando para adicionar um grupo individual para um grupo de acesso:
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

Os resultados devem ser o seguinte:
  
- Grupo do Azure AD de administradores de site contém as contas de usuário do administrador de site ou grupos
    
- Grupo do Azure AD de membros do site contém as contas de usuário do site membro ou grupos
    
- Grupo de visualizadores Azure AD de site contém as contas de usuário ou grupos que só podem visualizar o conteúdo do site
    
Valide a lista de membros de grupo para cada grupo de acesso com o Centro de administração do Office ou com o seguinte bloco de comando do PowerShell:
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

Aqui está a configuração resultante com os grupos de acesso do três site preenchida com as contas de usuário ou grupos.
  
![Os três grupos de acesso preenchidos com contas de usuário.](media/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>Fase 2: Criar e configurar o site de equipe isolado

Nesta fase, você cria o site do SharePoint Online isolado e configurar as permissões para os níveis de permissão padrão do SharePoint Online usar os novos grupos do Azure acesso baseado em AD.
  
Primeiro, crie o site da equipe do SharePoint Online com estas etapas.
  
1. Entre no Portal do Office 365 com uma conta que também será usada para administrar o site de equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na nova guia **SharePoint** do navegador, clique em **+ Criar site**.
    
4. Na página **Criar um site**, clique em **Site de equipe**.
    
5. Em **nome do Site**, digite um nome para o site de equipe. 
    
6. Na **Descrição do site de equipe,** digite uma descrição opcional da finalidade do site.
    
7. Em **Configurações de privacidade**, selecione **Privado – somente membros podem acessar esse site** e clique em **Avançar**.
    
8. No painel **Quem você deseja adicionar?**, clique em **Concluir**.
    
Em seguida, do novo site de equipe do SharePoint Online, configure permissões.
  
1. Na barra de ferramentas, clique no ícone Configurações e, em seguida, clique em **Permissões do site**.
    
2. No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.
    
3. Na nova guia **Permissões** do navegador, clique em **Configurações de Solicitação de Acesso**.
    
4. Na caixa de diálogo **Configurações de solicitações de acesso** , desmarque **Permitir membro para compartilhar o site e arquivos e pastas individuais** e **solicitações de acesso permitir** (de forma que todas as três caixas de seleção estiver desmarcadas) e clique em **Okey**.
    
5. Na guia **permissões** do seu navegador, clique em ** \<nome do site > membros** na lista.
    
6. Em **Pessoas e Grupos**, clique em **Novo**.
    
7. Na caixa de diálogo **compartilhar** , digite o nome do grupo de acesso de membros do site, selecione-o e, em seguida, clique em **compartilhar**.
    
8. Clique no botão Voltar de seu navegador.
    
9. Clique em ** \<nome do site > proprietários** na lista.
    
10. Em **Pessoas e Grupos**, clique em **Novo**.
    
11. Na caixa de diálogo **compartilhamento** , digite o nome do grupo de acesso de administradores do site, selecioná-la e, em seguida, clique em **compartilhar**.
    
12. Clique no botão Voltar de seu navegador.
    
13. Clique em ** \<nome do site > visitantes** na lista.
    
14. Em **Pessoas e Grupos**, clique em **Novo**.
    
15. Na caixa de diálogo **compartilhamento** , digite o nome do grupo de acesso ao site visualizadores, selecioná-la e, em seguida, clique em **compartilhar**.
    
16. Feche a guia **Permissões** do navegador.
    
Os resultados dessas configurações de permissão são:
  
- O ** \<nome do site > proprietários** grupo do SharePoint contém o grupo de acesso de administradores de site, no quais todos os membros têm o nível de permissão **controle total** .
    
- O ** \<nome do site > membros** grupo do SharePoint contém o grupo de acesso de membros do site, em que todos os membros têm o nível de permissão **Editar** .
    
- O ** \<nome do site > visitantes** grupo do SharePoint contém o site grupo visualizadores de acesso, no quais todos os membros têm o nível de permissão de **leitura** .
    
- A capacidade de membros convidar outros membros ou de membros solicitar acesso está desabilitada.
    
Aqui está a configuração resultante com os três grupos do SharePoint para o site configurado para usar os três grupos de acesso, que são preenchidos com contas de usuário ou grupos do Azure AD.
  
![A configuração final do seu site isolado do SharePoint Online com contas de usuário e grupos de acesso.](media/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
Você e os membros do site, por meio de associação de grupo em um dos grupos de acesso, agora podem colaborar usando os recursos do site.
  
## <a name="next-step"></a>Próxima etapa

Quando você precisar alterar a associação de grupo de acesso do site ou criar uma pasta de documentos com permissões personalizadas, consulte [Gerenciar um site de equipe do SharePoint Online isolado](manage-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Confira também

[Sites de equipe do SharePoint Online isolados](isolated-sharepoint-online-team-sites.md)
  
[Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md)
  
[Gerenciar um site de equipe do SharePoint Online isolado](manage-an-isolated-sharepoint-online-team-site.md)
  
[Soluções de segurança](security-solutions.md)



