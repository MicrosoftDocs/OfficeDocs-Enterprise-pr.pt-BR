---
title: Gerenciar um site de equipe do SharePoint Online isolado
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: 'Resumo: Gerencie seu site de equipe do SharePoint Online isolado com esses procedimentos.'
ms.openlocfilehash: bc6a3487f8e7dd6d6c3c0c8a38d2ac85e3565091
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a>Gerenciar um site de equipe do SharePoint Online isolado

 **Resumo:** Gerencie seu site de equipe do SharePoint Online isolado com esses procedimentos.
  
Este artigo descreve as operações de gerenciamento comuns para um site de equipe do SharePoint Online isolado.
  
## <a name="add-a-new-user"></a>Adicionar um novo usuário

Quando uma nova pessoa ingressa o site, você deve decidir o seu nível de participação no site:
  
- Administração: Adicionar nova conta de usuário ao site admins acessar grupo
    
- Colaboração ativa: adicionar a conta de usuário ao site membros do grupo de acesso
    
- Visualização: Adicionar a conta de usuário ao site visualizadores acessar grupo
    
Se você estiver gerenciando contas de usuários e grupos pelo Windows Server Active Directory (AD), adicione os usuários apropriados aos grupos de acesso apropriado usando seus Windows Server AD usuário e grupo gerenciamento procedimentos normais e aguarde a sincronização com o seu Assinatura do Office 365.
  
Se você estiver gerenciando contas de usuários e grupos por meio do Office 365, você pode usar o Centro de administração do Office ou o Microsoft PowerShell:
  
- Para o Centro de administração do Office, entrar com uma conta de usuário que tenha sido atribuída a função de administrador da conta de usuário ou administrador da empresa e usar grupos para adicionar usuários apropriados para os grupos de acesso apropriado.
    
- Para o PowerShell, primeiro [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218). Para adicionar uma conta de usuário a um grupo de acesso com seu nome de usuário principal (UPN), use o seguinte bloco de comando do PowerShell:
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> Para um arquivo de texto que contém todos os comandos do PowerShell e um Excel planilha de configuração que gera os comandos do PowerShell com base no seu grupo e usuário nomes de conta, baixe o [Isolado SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907). 

Para adicionar uma conta de usuário a um grupo de acesso com seu nome para exibição, use o seguinte bloco de comando do PowerShell:

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a>Adicionar um novo grupo

Para adicionar o acesso a um grupo inteiro, você deve decidir o nível de participação de todos os membros do grupo no site:
  
- Administração: Adicionar o grupo ao site do grupo de administradores acesso
    
- Colaboração ativa: adicionar o grupo ao site de membros do grupo de acesso
    
- Visualização: Adicionar o grupo ao site visualizadores acessar grupo
    
Se você estiver gerenciando contas de usuários e grupos por meio do Windows Server AD, adicione os grupos apropriados aos grupos apropriados usando seu usuário normal do Windows Server AD e procedimentos de gerenciamento de grupo e aguarde a sincronização com sua assinatura do Office 365.
  
Se você estiver gerenciando contas de usuários e grupos por meio do Office 365, você pode usar o Centro de administração do Office ou PowerShell:
  
- Para o Centro de administração do Office, entrar com uma conta de usuário que tenha sido atribuída a função de administrador da conta de usuário ou administrador da empresa e usar grupos para adicionar os grupos apropriados para os grupos de acesso apropriado.
    
- Para o PowerShell, primeiro [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218). Em seguida, use os seguintes comandos do PowerShell:
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a>Remover um usuário

Quando alguém acesso deve ser removido do site, removê-los a partir do grupo de acesso para o qual eles estão atualmente com base em sua participação no site do membro:
  
- Administração: Remover a conta de usuário do grupo de acesso de administradores de site
    
- Colaboração ativa: remover a conta de usuário a partir do grupo de acesso de membros do site
    
- Visualização: Remove a conta de usuário a partir do grupo de acesso do site visualizadores
    
Se você estiver gerenciando contas de usuários e grupos por meio do Windows Server AD, remova os usuários apropriados os grupos de acesso apropriado usando seu usuário normal do Windows Server AD e procedimentos de gerenciamento de grupo e aguarde a sincronização com o Office 365 assinatura.
  
Se você estiver gerenciando contas de usuários e grupos por meio do Office 365, você pode usar o Centro de administração do Office ou PowerShell:
  
- Para o Centro de administração do Office, entrar com uma conta de usuário que tenha sido atribuída a função de administrador da conta de usuário ou administrador da empresa e usar grupos para remover os usuários apropriados dos grupos acesso apropriado.
    
- Para o PowerShell, primeiro [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218). Para remover uma conta de usuário de um grupo de acesso com seu UPN, use o seguinte bloco de comando do PowerShell:
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

Para remover uma conta de usuário de um grupo de acesso com seu nome para exibição, use o seguinte bloco de comando do PowerShell:
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a>Remover um grupo

Para remover o acesso a um grupo inteiro, você pode remover o grupo a partir do grupo de acesso para o qual eles estão atualmente com base em sua participação no site do membro:
  
- Administração: Remover o grupo do grupo de acesso de administradores de site
    
- Colaboração ativa: remover o grupo a partir do grupo de acesso de membros do site
    
- Visualização: Remover o grupo do grupo de acesso ao site visualizadores
    
Se você estiver gerenciando contas de usuários e grupos por meio do Windows Server Active Directory, remova os grupos apropriados os grupos de acesso apropriado usando seus Windows Server AD usuário e grupo gerenciamento procedimentos normais e aguarde a sincronização com o seu Assinatura do Office 365.
  
Se você estiver gerenciando contas de usuários e grupos por meio do Office 365, você pode usar o Centro de administração do Office ou PowerShell:
  
- Para o Centro de administração do Office, entrar com uma conta de usuário que tenha sido atribuída a função de administrador da conta de usuário ou administrador da empresa e usar grupos para remover os grupos apropriados dos grupos acesso apropriado.
    
- Para o PowerShell, primeiro [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).    
Para remover um grupo de um grupo de acesso usando seus nomes de exibição, use o seguinte bloco de comando do PowerShell:
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a>Crie uma subpasta de documentos com permissões personalizadas

Em alguns casos, um subconjunto das pessoas trabalhando dentro do site isolado precisa de um lugar mais privado para colaborar. Para sites do SharePoint Online, você pode criar uma subpasta na pasta de documentos do site e atribuir permissões personalizadas. Aqueles sem permissões não verá a subpasta.
  
Para criar uma subpasta de documentos com permissões personalizadas, faça o seguinte:
  
1. Faça logon no Office 365 com uma conta que seja membro do grupo Administradores de acesso para o site. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Vá para o site de equipe isolado e clique em **documentos**.
    
3. Navegue até a pasta na pasta de documentos que conterá a subpasta com permissões personalizadas, crie a pasta e abra-o.
    
4. Clique em **compartilhar**.
    
5. Clique em **compartilhadas com > avançadas**.
    
6. Clique em **Parar herança de permissões**e clique em **Okey**.
    
7. Clique em **compartilhar**.
    
8. Clique em **compartilhadas com > avançadas**.
    
9. Clique em **conceder permissões > compartilhadas com > avançadas**.
    
10. Na página permissões, clique em ** \<nome do site > membros na lista**.
    
11. Sobre o ** \<nome do site > membros** de página, selecione a marca de seleção ao lado do grupo de acesso de membros do site, clique em **ações**, clique em **remover usuários do grupo**e clique em **Okey**.
    
12. Para adicionar membros específicos a essa subpasta, clique em **New > Adicionar usuários**.
    
13. Na caixa de diálogo **compartilhar** , digite os nomes das contas de usuário que podem colaborar nos arquivos na subpasta e, em seguida, clique em **compartilhar**.
    
14. Atualize a página da web para ver os novos resultados.
    
15. Em **grupos** , no painel de navegação esquerdo, clique no ** \<nome do site > visitantes** agrupar e use as etapas 11 a 14 para especificar o conjunto de contas de usuário que pode exibir os arquivos na subpasta (conforme necessário).
    
16. Em **grupos** , no painel de navegação esquerdo, clique no ** \<nome do site > proprietários** agrupar e use as etapas 11 a 14 para especificar o conjunto de contas de usuário que pode administrar as permissões na subpasta (conforme necessário).
    
17. Feche a guia **pessoas e grupos** no seu navegador.
    
## <a name="see-also"></a>Veja também

[Isolado sites de equipe do SharePoint Online](isolated-sharepoint-online-team-sites.md)
  
[Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md)
  
[Soluções de segurança](security-solutions.md)

[Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md)



