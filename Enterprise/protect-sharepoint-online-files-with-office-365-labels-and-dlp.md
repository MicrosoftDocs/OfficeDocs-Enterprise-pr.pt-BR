---
title: Proteger arquivos do SharePoint Online com DLP e rótulos do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 'Resumo: Aplique rótulos do Office 365 e políticas de DLP (prevenção de perda de dados) aos sites de equipe do SharePoint Online com vários níveis de proteção de informações.'
ms.openlocfilehash: 439f59f683090d39ea98730854aa1ca5dc8db482
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319262"
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Proteger arquivos do SharePoint Online com DLP e rótulos do Office 365

 **Resumo:** Aplique rótulos do Office 365 e políticas de DLP (prevenção de perda de dados) aos sites de equipe do SharePoint Online com vários níveis de proteção de informações.
  
Use as etapas neste artigo para projetar e implantar políticas de DLP e rótulos do Office 365 para sites de equipe do SharePoint Online de linha de base, confidenciais e altamente confidenciais. Para obter mais informações sobre essas três camadas de proteção, consulte [Arquivos e sites do SharePoint Online seguros](secure-sharepoint-online-sites-and-files.md).
  
## <a name="how-this-works"></a>Como isso funciona
1. Crie os rótulos desejados e publique-os. Pode levar até 12 horas para que eles sejam publicados.
2. Para os sites do SharePoint desejados, edite as configurações de biblioteca de documentos para aplicar um rótulo a itens na biblioteca.
3. Crie políticas DLP para agir com base nas etiquetas.

Quando os usuários adicionam um documento à biblioteca, o documento recebe o rótulo atribuído por padrão. Os usuários podem alterar o rótulo, se necessário. Quando um usuário compartilha um documento para fora da organização, a DLP verifica se um rótulo está atribuído e toma medidas caso uma política DLP corresponda ao rótulo. A DLP também procura por outras correspondências de política, como a proteção de arquivos com números de cartão de crédito, se esse tipo de política estiver configurado. 

## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>Rótulos do Office 365 para seus sites do SharePoint Online

Há três etapas para criar e atribuir rótulos do Office 365 a sites de equipe do SharePoint Online.
  
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
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>Criar rótulos do Office 365 com o Centro de administração do Office 365

1. Entre no Portal do Office 365 com uma conta que tenha a função de Administrador de Segurança ou Administrador da Empresa. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na guia **Microsoft Office Home**, clique no bloco **Administração**.
    
3. Na nova guia **Centro de Administração do Office** do navegador, clique em **Centros de Administração > Segurança&amp; e Conformidade**.
    
4. Na nova guia **Início – Segurança &amp;e Conformidade** do navegador, clique em **Classificações > Rótulos**.
    
5. No painel **Início > Rótulos**, clique em **Criar um rótulo**.
    
6. No painel **Atribuir nome ao seu rótulo**, digite o nome do rótulo e clique em **Avançar**.
    
7. No painel **Configurações do rótulo**, clique em **Avançar**.
    
8. No painel **Examine as configurações**, clique em **Criar este rótulo** e clique em **Fechar**.
    
9. Repita as etapas de 5 a 8 para os rótulos adicionais.
    
### <a name="create-office-365-labels-with-powershell"></a>Criar rótulos do Office 365 com o PowerShell

1. [Conecte-se ao Centro de Segurança e Conformidade do Office 365 &amp;usando o PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) remoto e especifique as credenciais da conta que têm a função de Administrador de Segurança ou Administrador da Empresa.
    
2. Preencha a lista de nomes de rótulo e execute esses comandos no prompt de comando do PowerShell:
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

Em seguida, use estas etapas para publicar os novos rótulos do Office 365.
  
1. No painel **Início > Rótulos** no Centro de Segurança&amp; e Conformidade, clique em** Publicar rótulos**.
    
2. No painel **Escolher rótulos para publicar**, clique em **Escolher rótulos para publicar**.
    
3. No painel **Escolher rótulos**, clique em **Adicionar** e selecione todos os quatro rótulos.
    
4. Clique em **Concluído**.
    
5. No painel **Escolher rótulos para publicar**, clique em **Avançar**.
    
6. No painel **Escolher locais**, clique em **Avançar**.
    
7. No painel **Atribuir um nome à política**, digite um nome para o conjunto de rótulos em **Nome** e clique em **Avançar**.
    
8. No painel **Examine as configurações**, clique em **Publicar rótulos** e clique em **Fechar**.
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>Etapa 3: Aplicar os rótulos do Office 365 aos sites do SharePoint Online

Use estas etapas para aplicar os rótulos do Office 365 às pastas de documentos de seus sites de equipe do SharePoint Online.
  
1. Na guia **Microsoft Office Home** do navegador, clique no bloco **SharePoint**.
    
2. Na nova guia **SharePoint** no navegador, clique em um site que precisa de um rótulo do Office 365 atribuído.
    
3. Na nova guia de site do SharePoint do navegador, clique em **Documentos**.
    
4. Clique no ícone de configurações e clique em **Configurações de biblioteca**.
    
5. Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.
    
6. Em **Configurações – Aplicar Rótulo**, selecione o rótulo adequado e clique em **Salvar**.
    
7. Feche a guia para o site do SharePoint Online.
    
8. Repita as etapas 3 a 8 acima para atribuir rótulos do Office 365 aos sites adicionais do SharePoint Online.
    
Esta é a configuração resultante.
  
![Rótulos do Office 365 para os quatro tipos de sites de equipe do SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>Políticas DLP para seus sites do SharePoint Online

Use estas etapas para configurar uma política DLP que notifica os usuários quando eles compartilham um documento em um site de equipe confidencial do SharePoint Online fora da organização.
  
1. Na guia **Microsoft Office Home** no navegador, clique no bloco **Segurança&amp; Conformidade**.
    
2. Na nova guia **Segurança e&amp; Conformidade** no navegador, clique em **Prevenção de perda de dados > Política**.
    
3. No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.
    
4. No painel **Iniciar com um modelo ou criar uma política personalizada**, clique em **Personalizado** e clique em **Avançar**.
    
5. No painel **Atribuir um nome à política**, digite o nome da política DLP de nível confidencial em **Nome** e clique em **Avançar**.
    
6. No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.
    
7. Na lista de locais, desabilite os locais **Email do Exchange** e **Contas do OneDrive** e clique em **Avançar**.
    
8. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.
    
9. No painel **Escolher os tipos de conteúdo para proteger**, clique em **Adicionar** na caixa suspensa e clique em **Rótulos**.
    
10. No painel **Rótulos**, clique em **+ Adicionar**, selecione o rótulo **Confidencial**, clique em **Adicionar** e clique em **Concluído**.
    
11. No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.
    
12. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.
    
13. No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.
    
14. No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.
    
15. Na caixa de texto, digite ou cole uma das dicas a seguir, dependendo de se você implementou a Proteção de Informações do Azure para proteger arquivos altamente confidenciais:
    
  - Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.
  - Arquivos altamente confidenciais são protegidos com criptografia. Somente usuários externos que recebam permissões do seu departamento de TI para esses arquivos poderão lê-los.
    
    Como alternativa, digite ou cole uma dica de política que informe os usuários sobre como compartilhar um arquivo para fora da sua organização. Para saber mais sobre como fornecer permissões a usuários externos para arquivos protegidos com a Proteção de Informações do Azure, confira Adicionar permissões para usuários externos.
    
16. Clique em **OK**.
    
17. No painel **O que deseja fazer se detectarmos informações confidenciais?**, desmarque a caixa de seleção **Impedir que as pessoas compartilhem e restringir o acesso ao conteúdo compartilhado** e clique em **Avançar**.
    
18. No painel **Deseja ativar a política ou testar primeiro?**, clique em **Sim** para ativá-la imediatamente e clique em **Avançar**.
    
19. No painel **Examine as configurações**, clique em **Criar** e em **Fechar**.
    
Aqui está a configuração resultante dos sites confidenciais da equipe do SharePoint Online.
  
![A política DLP para um site de equipe isolado do SharePoint Online usando o rótulo Confidencial do Office 365.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
Em seguida, use estas etapas para configurar uma política DLP que bloqueia os usuários quando eles compartilham um documento em um site de equipe altamente confidencial do SharePoint Online fora da organização.
  
1. Na guia **Microsoft Office Home** no navegador, clique no bloco **Segurança&amp; Conformidade**.
    
2. Na nova guia **Segurança e&amp; Conformidade** no navegador, clique em **Prevenção de perda de dados > Política**.
    
3. No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.
    
4. No painel **Iniciar com um modelo ou criar uma política personalizada**, clique em **Personalizado** e clique em **Avançar**.
    
5. No painel **Atribuir um nome à política**, digite o nome da política DLP de nível altamente confidencial em **Nome** e clique em **Avançar**.
    
6. No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.
    
7. Na lista de locais, desabilite os locais **Email do Exchange** e **Contas do OneDrive** e clique em **Avançar**.
    
8. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.
    
9. No painel **Escolher os tipos de conteúdo para proteger**, clique em **Adicionar** na caixa suspensa e clique em **Rótulos**.
    
10. No painel **Rótulos**, clique em **+ Adicionar**, selecione o **rótulo Altamente Confidencial**, clique em **Adicionar** e clique em **Concluído**.
    
11. No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.
    
12. No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.
    
13. No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.
    
14. No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.
    
15. Na caixa de texto, digite ou cole o seguinte:
    
  - Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.
    
    Como alternativa, digite ou cole em sua própria dica de política que instrui os usuários sobre como compartilhar um arquivo fora da organização.
    
16. Clique em **OK**.
    
17. No painel **O que deseja fazer se detectarmos informações confidenciais?**, selecione **Exigir uma justificativa de negócios para substituir** e clique em **Avançar**.
    
18. No painel **Deseja ativar a política ou testar primeiro?**, clique em **Sim** para ativá-la imediatamente e clique em **Avançar**.
    
19. No painel **Examine as configurações**, clique em **Criar** e em **Fechar**.
    
Aqui está a configuração resultante para sites de equipe do SharePoint Online de alta confidencialidade.
  
![A política DLP para um site de equipe isolado do SharePoint Online usando o rótulo Altamente Confidencial do Office 365.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>Próxima etapa

[Proteger arquivos do SharePoint Online com a Proteção de Informações do Azure](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>Confira também

[Proteger sites e arquivos do SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md)


