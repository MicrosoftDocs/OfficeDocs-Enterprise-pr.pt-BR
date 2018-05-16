---
title: Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Resumo: Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento e teste.'
ms.openlocfilehash: 004a1614330f220b31be640cd822d9fdcbb49b99
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste

 **Resumo:** Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento e teste.
  
Este artigo fornece instruções passo a passo para criar um ambiente de desenvolvimento e teste que inclui os quatro tipos diferentes de sites de equipe do SharePoint Online para a solução de [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md) .
  
![Todos os quatro sites de equipe no ambiente de desenvolvimento/teste do SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Use este ambiente de desenvolvimento/teste para experimentar com os comportamentos de proteção de informações e ajustar as configurações para suas necessidades específicas antes de implantar sites de equipe do SharePoint Online na produção.
  
## <a name="phase-1-create-your-devtest-environment"></a>Fase 1: Criar seu ambiente de desenvolvimento/teste

Nesta fase, você deve obter assinaturas de avaliação do Office 365 e do Enterprise Mobility + Security para uma organização fictícia.
  
Primeiro, siga as instruções na **Fase 2** do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).
  
Em seguida, inscreva-se para a assinatura de avaliação do EMS e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365.
  
1. Se necessário, entre no portal do Office 365 com as credenciais da conta de administrador global de sua assinatura de avaliação. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Clique no bloco de **Administração**.
    
3. Na guia **Centro de Administração do Office** no navegador, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.
    
4. Na página **Serviços de compra** , localize o item de **mobilidade corporativos + E5 de segurança** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.
    
5. Na página **Confirmar seu pedido**, clique em **Experimentar agora**.
    
6. Na página **Recibo do pedido**, clique em **Continuar**.
    
Em seguida, habilite a licença do Enterprise Mobility + Security E5 para sua conta de administrador global.
  
1. Na guia **Centro de Administração do Office 365** no navegador, no painel de navegação esquerdo, clique em **Usuários > Usuários ativos**.
    
2. Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.
    
3. No painel de **licenças do produto** , ativar a licença do produto para **mobilidade corporativos + E5 de segurança** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Fase 2: Criar e configurar seus grupos e usuários do Azure AD (Active Directory)

Nesta fase, você cria e configura os usuários e grupos do Azure AD para sua organização fictícia.
  
Primeiro, crie um conjunto de grupos para uma organização típica com o portal do Azure.
  
1. Criar uma guia separada no seu navegador e, em seguida, vá para o portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com). Se necessário, entre com as credenciais da conta de administrador global para a sua assinatura de avaliação do Office 365 E5.
    
2. No portal do Azure, clique em **Azure Active Directory > grupos**.
    
3. No blade **grupos - todos os grupos** , clique em **+ novo grupo**.
    
4. Na folha **Grupo**:
    
  - Selecione **Office 365** no **tipo de grupo**.
    
  - Digite **Pacote C** em **Nome**.
    
  - Selecione **atribuído** no **tipo de associação**.
      
5. Clique em **Criar**e, em seguida, feche a folha **Grupo**.
    
6. Repita as etapas 3 a 5 para os seguintes nomes de grupo:
    
  - Equipe de TI
    
  - Equipe de pesquisa
    
  - Equipe regular
    
  - Equipe de marketing
    
  - Equipe de vendas
    
7. Feche a guia do portal do Azure no navegador.
    
Em seguida, você configurar o licenciamento automático para que os membros dos grupos são automaticamente atribuídos licenças para suas assinaturas do Office 365 e EMS.
  
1. No Portal do Azure, clique em **Azure Active Directory > Licenças > Todos os produtos**.
    
2. Na lista, selecione **Enterprise mobilidade + E5 de segurança** e o **Office 365 Enterprise E5**e, em seguida, clique em **atribuir**.
    
3. Na folha **Atribuir licença**, clique em **Usuários e grupos**.
    
4. Na lista de grupos, selecione o seguinte:
    
  - Pacote C
    
  - Equipe de TI
    
  - Equipe de pesquisa
    
  - Equipe regular
    
  - Equipe de marketing
    
  - Equipe de vendas
    
5. Clique em **Selecionar**e, em seguida, clique em **atribuir**.
    
6. Feche a guia do Portal do Azure no navegador.
    
Em seguida, você deve se [Conectar ao módulo PowerShell do Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
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
> O uso de uma senha comum aqui é para a automação e facilidade de configuração para um ambiente de desenvolvimento/teste. Isso nunca é recomendado assinaturas de produção. 
  
Use estas etapas para verificar se o licenciamento do grupo está funcionando corretamente.
  
1. Na guia **Microsoft Office Home** do navegador, clique no bloco **Administração**.
    
2. Na nova guia **Centro de Administração do Office** do navegador, clique em **Usuários**.
    
3. Na lista de usuários, clique em **CEO**.
    
4. No painel que lista as propriedades da conta de usuário **CEO**, verifique se ele recebeu a atribuição das licenças **Enterprise Mobility + Security E5** e **Office 365 Enterprise E5** (em **Licenças de produto**).
    
## <a name="phase-3-create-office-365-labels"></a>Fase 3: Criar rótulos do Office 365

Nesta fase, você deve criar os rótulos para os diferentes níveis de segurança para as pastas e documentos do site da equipe do SharePoint Online.
  
1. Se necessário, use uma instância particular do seu navegador da Internet e entrar no portal do Office 365 com a conta de administrador global de sua assinatura de avaliação do Office 365 E5. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na guia **Microsoft Office Home**, clique no bloco **Administração**.
    
3. Na guia novo **Centro de administração do Office** do seu navegador, clique em **centrais de Admin > segurança &amp; conformidade**.
    
4. Do novo **Home - segurança &amp; conformidade** guia do navegador, clique em **classificações > rótulos**.
    
5. No painel **Início > Rótulos**, clique em **Criar um rótulo**.
    
6. No painel de **nome de seu rótulo** , digite **Internos de públicos**e clique em **Avançar**.
    
7. No painel **Configurações do Rótulo**, clique em **Avançar**.
    
8. No painel **Revise suas configurações** , clique em **criar este rótulo**e, em seguida, clique em **Fechar**.
    
9. Repita as etapas de 5 a 8 para os rótulos adicionais:
    
  - Private
    
  - Confidencial
    
  - Altamente Confidencial
    
10. No painel **Início > Rótulos**, clique em **Publicar rótulos**.
    
11. No painel **Escolher rótulos para publicar**, clique em **Escolher rótulos para publicar**.
    
12. No painel **Escolher rótulos**, clique em **Adicionar** e selecione todos os quatro rótulos.
    
13. Clique em **Concluído**.
    
14. No painel **Escolher rótulos para publicar**, clique em **Avançar**.
    
15. No painel **Escolher locais**, clique em **Avançar**.
    
16. No painel de **sua política de nome** , digite o **exemplo de organização** em **nome**e, em seguida, clique em **Avançar**.
    
17. No painel **Revise suas configurações** , clique em **rótulos de publicar**e, em seguida, clique em **Fechar**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Fase 4: Criar seus sites de equipe do SharePoint Online

Nesta fase, você cria e configura os quatro tipos de sites de equipe do SharePoint Online para sua organização de exemplo.
  
### <a name="organization-wide-team-site"></a>Site de equipe de toda a organização

Para criar um site de equipe do SharePoint Online público de linha de base, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entre no Portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.
    
4. Na página **Criar um site**, clique em **Site de equipe**.
    
5. Em **Nome do site**, digite **Toda a organização**. 
    
6. Na **Descrição do site de equipe**, digite **Site do SharePoint para toda a organização**.
    
7. Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.
    
8. No painel **Quem você deseja adicionar?**, clique em **Concluir**.
    
Em seguida, configure a pasta de documentos do site de equipe Toda a organização para o rótulo Público Interno.
  
1. Na guia **Home toda a organização** do seu navegador, clique em **documentos**.
    
2. Clique no ícone de configurações e clique em **Configurações de biblioteca**.
    
3. Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **Interno pública**e, em seguida, clique em **Salvar**.
    
Esta é a configuração resultante.
  
![Proteção de nível de linha de base para site de equipe do SharePoint Online público para toda a Organização.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Site de equipe do projeto 1

Para criar um site de equipe do SharePoint Online privado de linha de base para um projeto dentro da organização, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entre no Portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.
    
4. Na página **Criar um site**, clique em **Site de equipe**.
    
5. Em **Nome do site**, digite **Projeto 1**. 
    
6. Na **Descrição do site de equipe,** digite o **site do SharePoint para o Project 1**.
    
7. Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. No painel **Quem você deseja adicionar?**, clique em **Concluir**.
    
Em seguida, configure a pasta de documentos do site de equipe Projeto 1 para o rótulo Privado.
  
1. Na guia **Projeto 1 – Início** do navegador, clique em **Documentos**.
    
2. Clique no ícone de configurações e clique em **Configurações de biblioteca**.
    
3. Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **privada**e clique em **Salvar**.
    
Esta é a configuração resultante.
  
![Proteção de nível de linha de base para o site de equipe do SharePoint Online privado do Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Site de equipe de campanhas de marketing

Para criar um site de equipe do SharePoint Online isolado de nível confidencial para recursos de campanha de marketing, faça o seguinte:
  
1. Usando um navegador no computador local, entre no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.
    
4. Na página **Criar um site**, clique em **Site de equipe**.
    
5. Em **Nome do site de equipe**, digite **Campanhas de marketing**.
    
6. Em **Descrição do site de equipe**, digite **Site do SharePoint para recursos de campanha de marketing (confidencial)**.
    
7.  Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. No painel **Quem você deseja adicionar?**, clique em **Concluir**.
    
9. Na guia **campanhas de Marketing** novo em seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
10. No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.
    
11. Na nova guia **Permissões** no navegador, clique em **Configurações de Solicitação de Acesso**.
    
12. Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque as caixas de seleção **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** , digite **ITAdmin1 @**\<sua nome da organização >**. onmicrosoft.com** em **Enviar todas as solicitações de acesso**e clique em **Okey**.
    
13. Clique em **Membros de campanhas de marketing** na lista.
    
14. Na página **Pessoas e Grupos**, clique em **Novo**.
    
15. Na caixa de diálogo **compartilhar** , digite **a equipe de Marketing**, selecioná-la e, em seguida, clique em **compartilhar**.
    
16. Repita as etapas 14 e 15 para a conta de usuário **Researcher1** .
    
17. Clique no botão voltar de seu navegador.
    
18. Na lista, clique em **campanhas de Marketing proprietários** .
    
19. Na página **Pessoas e Grupos**, clique em **Novo**.
    
20. Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.
    
21. Clique no botão voltar de seu navegador.
    
22. Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Home de campanhas de Marketing** no seu navegador e, em seguida, feche o painel de **permissões do Site** .
    
Aqui estão os resultados da configuração de permissões:
  
- O grupo do SharePoint **Campanhas de marketing – membros** contém apenas o grupo **Campanhas de marketing** (que contém a conta de usuário de administrador global), o grupo **Equipe de marketing** (que contém as conas de usuário Marketing1 e Marketing2) e a conta de usuário **Researcher1**.
    
- O grupo do SharePoint **Campanhas de marketing – Proprietários** contém apenas o grupo **Equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).
    
- O grupo do SharePoint **Campanhas de marketing – Visitantes** não contém grupos ou contas de usuário.
    
- Os membros não podem modificar permissões de nível de site (isso pode ser feito apenas por membros do grupo **Campanhas de marketing – Proprietários**).
    
- Outras contas de usuário não podem acessar o site ou seus recursos, mas podem solicitar acesso ao site, qual enviará um email para a caixa de correio de conta de usuário ITAdmin1.
    
Em seguida, configure a pasta de documentos do site de equipe Campanhas de marketing para o rótulo Confidencial.
  
1. Na guia **Campanhas de marketing – Início** do navegador, clique em **Documentos**.
    
2. Clique no ícone de configurações e clique em **Configurações de biblioteca**.
    
3. Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **confidenciais**e, em seguida, clique em **Salvar**.
    
Em seguida, configure uma política de DLP (prevenção de perda de dados) que notifica os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo Confidencial, que inclui o site de Campanhas de marketing, fora da organização.
  
1. Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.
    
2. No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.
    
3. No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.
    
4. No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.
    
5. No painel de **sua política de nome** , digite os **sites de equipe do SharePoint Online rótulo confidenciais** em **nome**e, em seguida, clique em **Avançar**.
    
6. No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.
    
7. Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.
    
8. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.
    
9. No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.
    
10. No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.
    
11. No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.
    
12. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.
    
13. No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.
    
14. No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.
    
15. Na caixa de texto, digite ou cole o seguinte:
    
  - Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.
    
16. Clique em **OK**.
    
17. No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, desmarque a caixa de seleção **bloquear pessoas de compartilhamento e restringir o acesso ao conteúdo compartilhado** e, em seguida, clique em **Avançar**.
    
18. No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.
    
19. No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.
    
Esta é a configuração resultante.
  
![Proteção de nível confidencial para campanhas de Marketing isoladas do site de equipe do SharePoint Online.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Site de equipe de estratégia de empresa

Para criar um site de equipe do SharePoint Online isolado no nível altamente confidencial para recursos corporativos estratégicos dos diretores da organização, faça o seguinte:
  
1. Se necessário, use um navegador no computador local e entre no Portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na lista de blocos, clique em **SharePoint**.
    
3. Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.
    
4. Na página **Criar um site**, clique em **Site de equipe**.
    
5. Em **Nome do site da equipe**, digite **Estratégia da empresa**.
    
6. Em **Descrição do site da equipe**, digite **Site do SharePoint para estratégia da empresa (altamente confidencial)**.
    
7.  Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.
    
8. No painel **Quem você deseja adicionar?**, clique em **Concluir**.
    
9. Na guia nova **estratégia de empresa** no seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.
    
10. No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.
    
11. Na nova guia **Permissões** no navegador, clique em **Configurações de Solicitação de Acesso**.
    
12. Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** (de forma que todas as três caixas de seleção estiver desmarcadas) e clique em ** Okey**.
    
13. Na lista, clique em **membros de estratégia de empresa** .
    
14. Na página **Pessoas e Grupos**, clique em **Novo**.
    
15. Na caixa de diálogo **compartilhar** , digite **C-Suite**, selecioná-la e, em seguida, clique em **compartilhar**.
    
16. Na lista, clique em **estratégia de empresa proprietários** .
    
17. Na página **Pessoas e Grupos**, clique em **Novo**.
    
18. Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.
    
19. Clique no botão voltar de seu navegador.
    
20. Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Empresa estratégia-Home** no seu navegador e, em seguida, feche o painel de **permissões do Site** .
    
Aqui estão os resultados da configuração de permissões:
  
- O grupo do SharePoint **Estratégia da empresa – Membros** contém apenas o grupo **Pacote C** (que contém apenas as contas de usuário do CEO, do CFO e do CIO) e o grupo **Estratégia da empresa** (que contém apenas a conta de usuário de administrador global).
    
- O grupo do SharePoint de **Proprietários de estratégia de empresa** contém somente o grupo da **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).
    
- O grupo do SharePoint **Estratégia da empresa – Visitantes** não contém grupos ou contas de usuário.
    
- Os membros não podem modificar permissões de nível de site (isso pode ser feito apenas por membros do grupo **Estratégia da empresa – Proprietários**).
    
- Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar o acesso ao site. As permissões adicionais para o site devem ser feias pelo administrador global ou por um membro do grupo **Estratégia da empresa – Proprietários**.
    
Em seguida, configure a pasta de documentos do site da equipe de estratégia da empresa para o rótulo Altamente Confidencial.
  
1. Na guia **Estratégia da empresa – Início** do navegador, clique em **Documentos**.
    
2. Clique no ícone de configurações e clique em **Configurações de biblioteca**.
    
3. Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.
    
4. Em **Configurações se aplicam rótulo**, selecione **Altamente confidenciais**e, em seguida, clique em **Salvar**.
    
Em seguida, configure uma política de DLP que bloqueia os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo Altamente Confidencial, que inclui o site de Estratégia da empresa, fora da organização.
  
1. Se necessário, use um navegador no computador local e entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.
    
3. No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.
    
4. No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.
    
5. No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.
    
6. No painel de **sua política de nome** , digite **altamente confidenciais sites de equipe do SharePoint Online do rótulo** em **nome**e, em seguida, clique em **Avançar**.
    
7. No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.
    
8. Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.
    
9. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.
    
10. No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.
    
11. No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **Altamente confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.
    
12. No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.
    
13. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.
    
14. No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.
    
15. No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.
    
16. Na caixa de texto, digite ou cole o seguinte:
    
  - Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.
    
17. Clique em **OK**.
    
18. No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, selecione **exigir uma justificativa comercial para substituir**e, em seguida, clique em **Avançar**.
    
19. No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.
    
20. No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.
    
Em seguida, siga as instruções em [Ativar o Azure RMS com o centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Depois, configure a Proteção de Informações do Azure com uma nova política e sub-rótulo em escopo para proteção e permissões com as seguintes etapas:
  
1. Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Em uma guia separada do navegador, vá para o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se essa for a primeira vez que você está configurando a proteção de informações do Windows Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. No painel de lista, clique em **todos os serviços**, digite as **informações**e, clique em **Proteção de informações do Windows Azure**.
    
5. No blade **proteção das informações do Azure** , clique em **escopo políticas > + Adicionar uma nova diretiva**.
    
6. Digite **CompanyStrategy** em **Nome da política** e **Rótulo para documentos no site da equipe de estratégia da Empresa** em **Descrição**.
    
7. Clique em **Selecionar usuários ou grupos que obtêm essa política > Usuário/Grupos**e, em seguida, selecione **Pacote C**.
    
8. Clique em **Selecionar > OK**.
    
9. Para o rótulo **Altamente Confidencial**, clique nas reticências (...) e, em seguida, clique em **Adicionar um sub-rótulo**.
    
10. Digite um nome para o subrótulo em **Nome** e uma descrição do rótulo em **Descrição**.
    
11. Em **Definir permissões para documentos e emails que contenham este rótulo**, clique em **Proteger**.
    
12. Na seção **Proteção**, clique em **Azure (chave de nuvem)**.
    
13. Na folha **Proteção**, em **Configurações de proteção**, clique em **+ Adicionar permissões**.
    
14. Na folha **Adicionar permissões**, em **Especificar usuários e grupos**, clique em **+ Procurar no diretório**.
    
15. No painel **AAD usuários e grupos** , selecione o **Pacote de C**e, em seguida, clique em **Selecionar**.
    
16. Em **Escolha as permissões a predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo**e **Encaminhar** .
    
17. Clique duas vezes em **Okey** .
    
18. Na folha **Rótulo**, clique em **Salvar**.
    
19. Feche a nova folha de política em escopo.
    
20. No blade **proteção de informações do Windows Azure - políticas com escopo** , clique em **Publicar**e, em seguida, clique em **Sim**.
    
Para proteger um documento com esse novo rótulo e de proteção de informações do Windows Azure, você deve [instalar o cliente de proteção de informações do Windows Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em uma máquina de teste, instalar o Office do portal do Office 365 e entrar do Microsoft Word com uma conta no ** C-Suite** grupo de sua assinatura de avaliação.
  
Esta é a configuração resultante.
  
![Proteção com alto nível de confidencialidade para o site de equipe isolado do SharePoint Online de estratégia da Empresa.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Agora você está pronto para criar documentos nestes quatro sites e testar o acesso a eles com várias contas de usuário em sua assinatura de avaliação.
  
Aqui está a configuração geral para todos os quatro sites de equipe do SharePoint Online.
  
![Todos os quatro sites de equipe no ambiente de desenvolvimento/teste do SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Próxima etapa

Quando você estiver pronto para a implantação dos sites do SharePoint Online seguros na produção, consulte [Arquivos e sites do SharePoint Online seguros](secure-sharepoint-online-sites-and-files.md) para obter informações detalhadas e links para os artigos de implantação passo a passo.
  
## <a name="see-also"></a>Confira também

[Proteger sites e arquivos do SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Soluções de segurança](security-solutions.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




