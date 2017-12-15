---
title: Proteger sites do SharePoint Online em um ambiente de desenvolvimento e teste
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "Resumo: Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento e teste."
ms.openlocfilehash: 17abee7a293996194a097693607b4b4d9c117046
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Proteger sites do SharePoint Online em um ambiente de desenvolvimento e teste

 **Resumo:** Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento e teste.
  
Este artigo fornece instruções passo a passo para criar um ambiente de desenvolvimento e teste que inclui os quatro tipos diferentes de sites de equipe do SharePoint Online para a solução de [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md) .
  
![Todos os quatro sites de equipe no ambiente de desenvolvimento/teste do SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Use esse ambiente de desenvolvimento e teste para experimentar os comportamentos de proteção de informações e ajustar as configurações para suas necessidades específicas antes de implantar o SharePoint Online sites de equipe em produção.
  
## <a name="phase-1-create-your-devtest-environment"></a>Fase 1: Crie seu ambiente de desenvolvimento e teste

Nesta fase, você deve obter assinaturas de avaliação do Office 365 e mobilidade corporativos + segurança para uma organização a empresa fictícia.
  
Primeiro, siga as instruções na **fase 2** do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Em seguida, inscreva-se para a assinatura de avaliação do EMS e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365.
  
1. Se necessário, entre no portal do Office 365 com as credenciais da conta de administrador global de sua assinatura de avaliação. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Clique no lado do **Admin** .
    
3. Na guia do **Centro de administração do Office** em seu navegador, no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.
    
4. Na página **Serviços de compra** , localize o item de **mobilidade corporativos + E5 de segurança** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.
    
5. Na página **confirmar seu pedido** , clique em **tente agora**.
    
6. Na página **confirmação de ordem** , clique em **continuar**.
    
Em seguida, habilite a mobilidade corporativos + licença E5 de segurança para sua conta de administrador global.
  
1. Na guia do **Centro de administração do Office 365** em seu navegador, no painel de navegação esquerdo, clique em **usuários > usuários ativos**.
    
2. Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.
    
3. No painel de **licenças do produto** , ativar a licença do produto para **mobilidade corporativos + E5 de segurança** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Fase 2: Criar e configurar seus usuários e grupos do Windows Azure AD (Active Directory)

Nesta fase, criar e configurar o Azure AD grupos e usuários para a sua organização a empresa fictícia.
  
Primeiro, crie um conjunto de grupos de uma organização comum com o portal do Azure.
  
1. Criar uma guia separada no seu navegador e, em seguida, vá para o portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com). Se necessário, entre com as credenciais da conta de administrador global para a sua assinatura de avaliação do Office 365 E5.
    
2. No portal do Azure, clique em **Azure Active Directory > usuários e grupos > todos os grupos**.
    
3. No blade **todos os grupos** , clique em **+ novo grupo**.
    
4. No **grupo** blade:
    
  - Tipo **C-Suite** em **nome**.
    
  - Selecione **atribuído** na **associação**.
    
  - Clique em **Sim** para **Habilitar o Office recursos**.
    
5. Clique em **criar**e feche o blade de **grupo** .
    
6. Repita as etapas 3 a 5 para os nomes de grupo a seguir:
    
  - Equipe de TI
    
  - Equipe de pesquisa
    
  - Equipe regular
    
  - Equipe de marketing
    
  - Equipe de vendas
    
7. Lembre na guia portal Azure abrir seu navegador.
    
Em seguida, você configurar o licenciamento automático para que os membros dos grupos são automaticamente atribuídos licenças para suas assinaturas do Office 365 e EMS.
  
1. No portal do Azure, clique em **Azure Active Directory > licenças > todos os produtos**.
    
2. Na lista, selecione **Enterprise mobilidade + E5 de segurança** e o **Office 365 Enterprise E5**e, em seguida, clique em **atribuir**.
    
3. Na blade **atribuir licença** , clique em **usuários e grupos**.
    
4. Na lista de grupos, selecione o seguinte:
    
  - C-Suite
    
  - Equipe de TI
    
  - Equipe de pesquisa
    
  - Equipe regular
    
  - Equipe de marketing
    
  - Equipe de vendas
    
5. Clique em **Selecionar**e, em seguida, clique em **atribuir**.
    
6. Feche a Azure guia portal no seu navegador.
    
Em seguida, você [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Preencha o nome da sua organização, seu local e uma senha comum e, em seguida, execute estes comandos no prompt de comando do PowerShell ou ambiente de Script integrado (ISE) para criar contas de usuário e adicioná-los em seus grupos:
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> O uso de uma senha comum aqui é para automação e facilidade de configuração para um ambiente de desenvolvimento e teste. Isso não é recomendado para assinaturas de produção. 
  
Use estas etapas para verificar se o licenciamento do grupo está funcionando corretamente.
  
1. Na guia **Página inicial do Microsoft Office** do seu navegador, clique no lado do **Admin** .
    
2. Na guia novo **Centro de administração do Office** do seu navegador, clique em **usuários**.
    
3. Na lista de usuários, clique em **CEO**.
    
4. No painel que lista as propriedades da conta de usuário do **CEO** , verifique se que ele foi atribuído as licenças de **mobilidade corporativos + E5 de segurança** e o **Office 365 Enterprise E5** (em **licenças do produto**).
    
## <a name="phase-3-create-office-365-labels"></a>Fase 3: Criar rótulos do Office 365

Nesta fase, você deve criar os rótulos para os diferentes níveis de segurança para pastas de documentos do site de equipe do SharePoint Online.
  
1. Se necessário, use uma instância particular do seu navegador da Internet e entrar no portal do Office 365 com a conta de administrador global de sua assinatura de avaliação do Office 365 E5. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .
    
3. Na guia novo **Centro de administração do Office** do seu navegador, clique em **centrais de Admin > segurança &amp; conformidade**.
    
4. Do novo **Home - segurança &amp; conformidade** guia do navegador, clique em **classificações > rótulos**.
    
5. Da **Home > rótulos** painel, clique em **criar um rótulo**.
    
6. No painel de **nome de seu rótulo** , digite **Internos de públicos**e clique em **Avançar**.
    
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
    
16. No painel de **sua política de nome** , digite o **exemplo de organização** em **nome**e, em seguida, clique em **Avançar**.
    
17. No painel **Revise suas configurações** , clique em **rótulos de publicar**e, em seguida, clique em **Fechar**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Fase 4: Criar seus sites de equipe do SharePoint Online

Nesta fase, criar e configurar os quatro tipos de sites de equipe do SharePoint Online para a sua organização de exemplo.
  
### <a name="organization-wide-team-site"></a>Site de equipe ampla de organização

Para criar um site de equipe ' baseline público do SharePoint Online, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do Site**, digite **toda a organização**. 
    
6. Na **Descrição do site de equipe**, digite o **site do SharePoint para toda a organização**.
    
7. Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
Em seguida, configure a pasta de documentos do site organização ampla de equipe para o rótulo de público interno.
  
1. Na guia **Home toda a organização** do seu navegador, clique em **documentos**.
    
2. Clique no ícone configurações e clique em **definições da biblioteca**.
    
3. Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **Interno pública**e, em seguida, clique em **Salvar**.
    
Esta é a configuração resultante.
  
![Proteção de nível de linha de base para site de equipe do SharePoint Online público para toda a Organização.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Site de equipe do projeto 1

Para criar um site de equipe baseline privado SharePoint Online para um projeto dentro da organização, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do Site**, digite **1 do Project**. 
    
6. Na **Descrição do site de equipe,** digite o **site do SharePoint para o Project 1**.
    
7. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
Em seguida, configure a pasta de documentos do site da equipe de projeto 1 para o rótulo de privada.
  
1. Na guia **Project 1-Home** do seu navegador, clique em **documentos**.
    
2. Clique no ícone configurações e clique em **definições da biblioteca**.
    
3. Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **privada**e clique em **Salvar**.
    
Esta é a configuração resultante.
  
![Proteção de nível de linha de base para o site de equipe do SharePoint Online privado do Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Site da equipe de campanhas de marketing

Para criar um nível confidenciais isolado team site do SharePoint Online para recursos de campanhas de marketing, faça o seguinte:
  
1. Usando um navegador no computador local, entre no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do site de equipe**, digite **campanhas de Marketing**.
    
6. Na **Descrição do site de equipe**, digite o **site do SharePoint para recursos de campanha de marketing (confidenciais)**.
    
7.  Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
9. Na guia **campanhas de Marketing** novo em seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
10. No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.
    
11. Na guia **permissões** nova no seu navegador, clique em **Configurações de solicitação de acesso**.
    
12. Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque as caixas de seleção **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** , digite **ITAdmin1 @**\<sua nome da organização >**. onmicrosoft.com** em **Enviar todas as solicitações de acesso**e clique em **Okey**.
    
13. Na lista, clique em **membros de campanhas de Marketing** .
    
14. Na página **pessoas e grupos** , clique em **novo**.
    
15. Na caixa de diálogo **compartilhar** , digite **a equipe de Marketing**, selecioná-la e, em seguida, clique em **compartilhar**.
    
16. Repita as etapas 14 e 15 para a conta de usuário **Researcher1** .
    
17. Clique no botão voltar de seu navegador.
    
18. Na lista, clique em **campanhas de Marketing proprietários** .
    
19. Na página **pessoas e grupos** , clique em **novo**.
    
20. Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.
    
21. Clique no botão voltar de seu navegador.
    
22. Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Home de campanhas de Marketing** no seu navegador e, em seguida, feche o painel de **permissões do Site** .
    
Estes são os resultados da configuração das permissões:
  
- O grupo do SharePoint **Membros de campanhas de Marketing** contém apenas o grupo de **campanhas de Marketing** (que contém a conta de usuário do administrador global), o grupo de **equipe de Marketing** (que contém o usuário Marketing1 e Marketing2 contas) e a conta de usuário **Researcher1** .
    
- O grupo de **Proprietários de campanhas de Marketing** SharePoint contém apenas o grupo de **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).
    
- Grupo de **Campanhas de Marketing - visitantes** do SharePoint não contém grupos ou contas de usuário.
    
- Membros não podem modificar permissões de nível de site (isso só pode ser feito por membros do grupo **Proprietários de campanhas de Marketing** ).
    
- Outras contas de usuário não podem acessar o site ou seus recursos, mas podem solicitar acesso ao site, qual enviará um email para a caixa de correio de conta de usuário ITAdmin1.
    
Em seguida, configure a pasta de documentos do site da equipe de campanhas de Marketing, rótulo confidencial de.
  
1. Na guia **Home de campanhas de Marketing** do seu navegador, clique em **documentos**.
    
2. Clique no ícone configurações e clique em **definições da biblioteca**.
    
3. Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **confidenciais**e, em seguida, clique em **Salvar**.
    
Em seguida, configure uma política de prevenção (DLP) de perda de dados que notifica os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo confidencial, que inclui o site de campanhas de Marketing, fora da organização.
  
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
    
Esta é a configuração resultante.
  
![Proteção de nível confidencial para campanhas de Marketing isoladas do site de equipe do SharePoint Online.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Site de equipe de estratégia de empresa

Para criar um site de equipe do SharePoint Online isolado no nível altamente confidencial para recursos da empresa estratégica dos principais executivos da organização, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.
    
4. Na página **criar um site** , clique em **sites de equipe**.
    
5. Em **nome do site de equipe**, digite a **estratégia de empresa**.
    
6. Na **Descrição do site de equipe**, digite o **site do SharePoint para a estratégia da empresa (altamente confidencial)**.
    
7.  Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.
    
9. Na guia nova **estratégia de empresa** no seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
10. No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.
    
11. Na guia **permissões** nova no seu navegador, clique em **Configurações de solicitação de acesso**.
    
12. Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** (de forma que todas as três caixas de seleção estiver desmarcadas) e clique em ** Okey**.
    
13. Na lista, clique em **membros de estratégia de empresa** .
    
14. Na página **pessoas e grupos** , clique em **novo**.
    
15. Na caixa de diálogo **compartilhar** , digite **C-Suite**, selecioná-la e, em seguida, clique em **compartilhar**.
    
16. Na lista, clique em **estratégia de empresa proprietários** .
    
17. Na página **pessoas e grupos** , clique em **novo**.
    
18. Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.
    
19. Clique no botão voltar de seu navegador.
    
20. Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Empresa estratégia-Home** no seu navegador e, em seguida, feche o painel de **permissões do Site** .
    
Estes são os resultados da configuração das permissões:
  
- O grupo do SharePoint de **Estratégia-membros da empresa** contém apenas o grupo de **Pacote do C** (que contém apenas as contas de usuário CEO, CIO e diretor financeiro) e do grupo de **estratégia da empresa** (que contém a conta de usuário administrador global).
    
- O grupo do SharePoint de **Proprietários de estratégia de empresa** contém somente o grupo da **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).
    
- Grupo do SharePoint **Empresa estratégia-visitantes** não contém grupos ou contas de usuário.
    
- Membros não podem modificar permissões de nível de site (isso só pode ser feito por membros do grupo **Proprietários de estratégia de empresa** ).
    
- Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar acesso ao site. Permissões adicionais para o site devem ser feitas pelo administrador global ou por um membro do grupo **Proprietários de estratégia de empresa** .
    
Em seguida, configure a pasta de documentos do site de equipe de estratégia da empresa para o rótulo de altamente confidenciais.
  
1. Na guia **Empresa estratégia-página inicial** do navegador, clique em **documentos**.
    
2. Clique no ícone configurações e clique em **definições da biblioteca**.
    
3. Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **Altamente confidenciais**e, em seguida, clique em **Salvar**.
    
Em seguida, configure uma política de DLP que bloqueia usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo altamente confidenciais, que inclui o site da estratégia de empresa, fora da organização.
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
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
    
Em seguida, siga as instruções em [Ativar o Azure RMS com o Centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Em seguida, configure a proteção de informações do Windows Azure com uma nova política de escopo e sub-recurso rótulo para proteção e permissões com as seguintes etapas:
  
1. Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Em uma guia separada do navegador, vá para o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se essa for a primeira vez que você está configurando a proteção de informações do Windows Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. No painel de lista, clique em **mais de serviços**, digite as **informações**e clique em **Proteção de informações do Windows Azure**.
    
5. No blade **proteção das informações do Azure** , clique em **escopo políticas > + Adicionar uma nova diretiva**.
    
6. Digite **CompanyStrategy** no **nome de política** e **rótulo para documentos no site da equipe de estratégia de empresa** em **Descrição**.
    
7. Clique em **Selecione quais usuários ou grupos fazer essa política > grupos de usuários/**e selecione **C-Suite**.
    
8. Clique em **Selecione > Okey**.
    
9. Para o rótulo de **Altamente confidenciais** , clique nas reticências (…) e, em seguida, clique em **Adicionar um rótulo de subsites**.
    
10. Digite um nome para o rótulo de subsites em **nome** e uma descrição do rótulo em **Descrição**.
    
11. Em **definir permissões para documentos e emails contendo esse rótulo**, clique em **proteger**.
    
12. Na seção **proteção** , clique em **Windows Azure (chave de nuvem)**.
    
13. No blade **proteção** , em **configurações de proteção**, clique em **+ Adicionar permissões**.
    
14. No blade **Adicionar permissões** , em **especificar usuários e grupos**, clique em **+ Procurar no diretório**.
    
15. No painel **AAD usuários e grupos** , selecione o **Pacote de C**e, em seguida, clique em **Selecionar**.
    
16. Em **Escolha as permissões a predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo**e **Encaminhar** .
    
17. Clique duas vezes em **Okey** .
    
18. No **rótulo sub-recurso** blade, clique em **Salvar**.
    
19. Fechar o novo escopo blade de política.
    
20. No blade **proteção de informações do Windows Azure - políticas com escopo** , clique em **Publicar**e, em seguida, clique em **Sim**.
    
Para proteger um documento com esse novo rótulo e de proteção de informações do Windows Azure, você deve [instalar o cliente de proteção de informações do Windows Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em uma máquina de teste, instalar o Office do portal do Office 365 e entrar do Microsoft Word com uma conta no ** C-Suite** grupo de sua assinatura de avaliação.
  
Esta é a configuração resultante.
  
![Proteção com alto nível de confidencialidade para o site de equipe isolado do SharePoint Online de estratégia da Empresa.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Agora você está pronto para criar documentos em sites essas quatro e testar acessá-los com várias contas de usuário em sua assinatura de avaliação.
  
Aqui está a configuração geral para todos os quatro sites de equipe do SharePoint Online.
  
![Todos os quatro sites de equipe no ambiente de desenvolvimento/teste do SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Próxima etapa

Quando estiver pronto para a implantação de produção de sites do SharePoint Online seguros, consulte [arquivos e sites do SharePoint Online segura](secure-sharepoint-online-sites-and-files.md) para obter informações detalhadas e links para artigos passo a passo de implantação.
  
## <a name="see-also"></a>See Also

[Proteja arquivos e sites do SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Soluções de segurança](security-solutions.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




