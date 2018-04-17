---
title: Proteger os arquivos do SharePoint Online com o Office 365 rótulos e DLP
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
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 'Resumo: Aplica Office 365 rótulos e dados perda prevention (DLP) políticas para sites de equipe do SharePoint Online com vários níveis de proteção das informações.'
ms.openlocfilehash: a6413ac556cf63cbe7491180d65b4425cd0dba3d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Proteger os arquivos do SharePoint Online com o Office 365 rótulos e DLP

 **Resumo:** Aplica Office 365 rótulos e dados perda prevention (DLP) políticas para sites de equipe do SharePoint Online com vários níveis de proteção das informações.
  
Use as etapas neste artigo para projetar e implantar o Office 365 rótulos e políticas DLP da linha de base, confidenciais e altamente confidenciais SharePoint Online para sites de equipe. Para obter mais informações sobre esses três camadas de proteção, consulte [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md).
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>Rótulos do Office 365 para seus sites do SharePoint Online

Existem três fases à criação e, em seguida, atribuir o Office 365 etiquetas aos sites de equipe do SharePoint Online.
  
### <a name="phase-1-determine-the-office-365-label-names"></a>Etapa 1: Determinar os nomes de rótulo do Office 365

Nesta fase, você determina os nomes dos rótulos do Office 365 para os quatro níveis de proteção de informações aplicados a sites de equipe do SharePoint Online. A tabela a seguir lista os nomes recomendados para cada nível.
  
|**Nível de proteção do site de equipe do SharePoint Online**|**Nome do rótulo**|
|:-----|:-----|
|Linha de base público  <br/> |Público interno  <br/> |
|Linha de base privado  <br/> |Private  <br/> |
|Confidencial  <br/> |Confidencial  <br/> |
|Altamente Confidencial  <br/> |Altamente Confidencial  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a>Fase 2: Criar os rótulos do Office 365

Nesta fase, você cria e publica seus determinados rótulos para os diferentes níveis de proteção de informações.
  
Para criar os rótulos, você pode usar o Centro de administração do Office 365 ou o Microsoft PowerShell.
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>Crie rótulos do Office 365 com o Centro de administração do Office 365

1. Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na guia **Microsoft Office Home**, clique no bloco **Administração**.
    
3. Na guia novo **Centro de administração do Office** do seu navegador, clique em **centrais de Admin > segurança &amp; conformidade**.
    
4. Do novo **Home - segurança &amp; conformidade** guia do navegador, clique em **classificações > rótulos**.
    
5. No painel **Início > Rótulos**, clique em **Criar um rótulo**.
    
6. No painel de **nome de seu rótulo** , digite o nome do rótulo e clique em **Avançar**.
    
7. No painel **Configurações do Rótulo**, clique em **Avançar**.
    
8. No painel **Revise suas configurações** , clique em **criar este rótulo**e, em seguida, clique em **Fechar**.
    
9. Repita as etapas de 5 a 8 para os rótulos adicionais.
    
### <a name="create-office-365-labels-with-powershell"></a>Crie rótulos do Office 365 com o PowerShell

1. [Conectar para a segurança do Office 365 &amp; usando o PowerShell remoto do Centro de conformidade](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) e especifique as credenciais de uma conta que tenha a função de administrador de segurança ou administrador da empresa.
    
2. Preencha a lista de nomes de rótulo e execute esses comandos no prompt de comando do PowerShell:
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

Em seguida, use estas etapas para publicar os novos rótulos do Office 365.
  
1. Da **Home > rótulos** a segurança do painel &amp; Centro de conformidade, clique em **Publicar rótulos**.
    
2. No painel **Escolher rótulos para publicar**, clique em **Escolher rótulos para publicar**.
    
3. No painel **Escolher rótulos**, clique em **Adicionar** e selecione todos os quatro rótulos.
    
4. Clique em **Concluído**.
    
5. No painel **Escolher rótulos para publicar**, clique em **Avançar**.
    
6. No painel **Escolher locais**, clique em **Avançar**.
    
7. No painel de **sua política de nome** , digite um nome para seu conjunto de etiquetas em **nome**e, em seguida, clique em **Avançar**.
    
8. No painel **Revise suas configurações** , clique em **rótulos de publicar**e, em seguida, clique em **Fechar**.
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>Etapa 3: Aplicar os rótulos do Office 365 aos sites do SharePoint Online

Use estas etapas para aplicar os rótulos do Office 365 às pastas de documentos de seus sites de equipe do SharePoint Online.
  
1. Na guia **Microsoft Office Home** do navegador, clique no bloco **SharePoint**.
    
2. Na nova guia **SharePoint** no navegador, clique em um site que precisa de um rótulo do Office 365 atribuído.
    
3. Na nova guia de site do SharePoint do navegador, clique em **Documentos**.
    
4. Clique no ícone de configurações e clique em **Configurações de biblioteca**.
    
5. Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.
    
6. Em **Configurações se aplicam rótulo**, selecione o rótulo apropriado e, em seguida, clique em **Salvar**.
    
7. Feche a guia para o site do SharePoint Online.
    
8. Repita as etapas 3 a 8 acima para atribuir rótulos do Office 365 aos sites adicionais do SharePoint Online.
    
Aqui está a configuração resultante.
  
![Rótulos do Office 365 para os quatro tipos de sites de equipe do SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>Políticas DLP para seus sites do SharePoint Online

Use estas etapas para configurar uma política DLP que notifica os usuários quando eles compartilham um documento em um site de equipe confidencial do SharePoint Online fora da organização.
  
1. Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.
    
2. No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.
    
3. No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.
    
4. No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.
    
5. No painel de **sua política de nome** , digite o nome para a política de DLP nível confidencial em **nome**e, em seguida, clique em **Avançar**.
    
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
    
    Como alternativa, digite ou cole em seu próprio dica de política que instrua os usuários sobre como compartilhar um arquivo de fora da sua organização.
    
16. Clique em **OK**.
    
17. No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, desmarque a caixa de seleção **bloquear pessoas de compartilhamento e restringir o acesso ao conteúdo compartilhado** e, em seguida, clique em **Avançar**.
    
18. No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.
    
19. No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.
    
Aqui está a configuração resultante dos sites confidenciais da equipe do SharePoint Online.
  
![A política DLP para um site de equipe isolado do SharePoint Online usando o rótulo Confidencial do Office 365.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
Em seguida, use estas etapas para configurar uma política DLP que bloqueia os usuários quando eles compartilham um documento em um site de equipe altamente confidencial do SharePoint Online fora da organização.
  
1. Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.
    
2. No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.
    
3. No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.
    
4. No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.
    
5. No painel de **sua política de nome** , digite o nome para a política de DLP nível altamente confidencial em **nome**e, em seguida, clique em **Avançar**.
    
6. No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.
    
7. Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.
    
8. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.
    
9. No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.
    
10. No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **Altamente confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.
    
11. No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.
    
12. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.
    
13. No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.
    
14. No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.
    
15. Na caixa de texto, digite ou cole o seguinte:
    
  - Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.
    
    Como alternativa, digite ou cole em seu próprio dica de política que instrua os usuários sobre como compartilhar um arquivo de fora da sua organização.
    
16. Clique em **OK**.
    
17. No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, selecione **exigir uma justificativa comercial para substituir**e, em seguida, clique em **Avançar**.
    
18. No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.
    
19. No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.
    
Aqui está a configuração resultante para sites de equipe do SharePoint Online de alta confidencialidade.
  
![A política DLP para um site de equipe isolado do SharePoint Online usando o rótulo Altamente Confidencial do Office 365.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>Próxima etapa

[Proteger arquivos do SharePoint Online com a Proteção de Informações do Azure](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>Confira também

[Proteger sites e arquivos do SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)


