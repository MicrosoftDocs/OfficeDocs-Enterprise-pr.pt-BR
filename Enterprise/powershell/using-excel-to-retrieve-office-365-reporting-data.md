---
title: "Usar o Excel para Recuperar Dados de Relatório do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 510d5528-ac00-4f54-9d38-75fa043d0a06
description: "Resumo: Use o recurso oData no Microsoft Excel para recuperar informações detalhadas de relatórios para sua implantação do Office 365"
ms.openlocfilehash: 0749160e1d9bf5e8e0b6ee73aa1baa5ae826ba49
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="using-excel-to-retrieve-office-365-reporting-data"></a>Usar o Excel para Recuperar Dados de Relatório do Office 365

 **Resumo:** use o recurso oData no Microsoft Excel para recuperar informações detalhadas de relatórios para sua implantação do Office 365
  
Os relatórios são uma parte importante da administração do sistema. O Centro de administração do Office 365 inclui vários relatórios predefinidos, que você pode acessar na seção **Relatórios** da navegação à esquerda. Há relatórios de uso e segurança e de conformidade.
  
Os relatórios disponíveis para você dependem da versão do Office 365 que está sendo usada e de quais serviços do Office 365 foram habilitados. Para obter mais informações, consulte a [Página de relatórios](https://technet.microsoft.com/pt-BR/library/office-365-reports.aspx).
  
Os relatórios predefinidos do Centro de administração são um excelente recurso. Eles facilitam a verificação de alguns itens, como o uso de caixa de correio ou o número de minutos que os usuários estão gastando em conferências online. Entretanto, quando se trata de análises detalhadas do seu domínio do Office 365, os relatórios têm suas limitações.
  
Uma forma de contornar estas limitações é usar o Windows PowerShell ou outra linguagem de desenvolvimento para acessar o serviço de relatório do Office 365 e criar relatórios personalizados. Os relatórios personalizados oferecem a você a capacidade de ditar quais dados (e quantos) são retornados do serviço de relatório do Office 365. Ao escrever relatórios personalizados, você também pode especificar como os dados devem ser classificados e agrupados e, se necessário, como eles devem ser salvos. Por exemplo, é possível salvar dados no formato XML ou no formato de valores separados por vírgula, que podem ser facilmente importados no Excel. 
  
Além disso, os scripts/aplicativos personalizados permitem que você acesse relatórios que não estão disponíveis no Centro de Administração do Office 365. Por exemplo, o Centro de Administração pode informar quantas caixas de correio obsoletas você tem, mas não quantas caixas de correio foram acessadas nos últimos 30 dias. Isso é algo que um script do PowerShell personalizado pode informar. Estas opções em conjunto representam uma enorme flexibilidade como retorno por escrever um breve e relativamente simples script do Windows PowerShell.
  
> [!VISUAL BASIC NOTE] Para obter mais informações, consulte a [home page](https://msdn.microsoft.com/pt-BR/library/office/jj984325%28v=office.15%29.aspx) do serviço de relatório do Office 365.
  
Para recuperar esses dados você tem que escrever um código. Essa opção é válida se você fizer parte de uma grande organização que precisa limitar a quantidade e o tipo de informações que são retornadas. Mas se você fizer parte de uma organização menor, que não precisa limitar a quantidade e o tipo de informações que são retornadas, convém considerar abrir os relatórios do Office 365 pelo Excel.
  
No entanto, há algumas limitações, a primeira delas é: você não pode filtrar, classificar, selecionar ou manipular de forma alguma os dados antes de serem retornados. Em vez disso, você simplesmente obtém o conjunto de dados padrão retornado pelo relatório. Em alguns casos podem não ser dados suficientes. Por exemplo, o relatório pode retornar dados apenas para o mês anterior e não para o ano inteiro. Em outros casos podem ser dados em excesso: você pode obter dados para o ano inteiro mesmo que só quisesse os dados do mês anterior.
  
Para abrir um relatório do Office 365 diretamente de dentro do Excel, realize o procedimento a seguir:
  
1. Comece abrindo uma nova planilha no Excel. Nesta planilha, clique em **Dados**, depois em **A Partir de Outras Fontes** e, por fim, clique em **A Partir do Feed de Dados OData**. Isso faz com que a caixa de diálogo do **Assistente para Conexão de Dados** seja aberta:
    
     ![Exemplo de uma caixa de diálogo Conectar a um Feed de Dados no Assistente de Conexão de Dados.](images/o365_reporting_connect_data_feed.png)
  
2. Na página **Conectar a um Feed de Dados**, insira **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** como o local do feed de dados. Observe que você só pode digitar a URL base conforme mostrado. Não é possível adicionar qualquer instrução para Selecionar, Filtrar ou Formatar. Se você digitar qualquer informação que não seja a URL base, não recuperará nenhum dado. Em vez disso, você simplesmente verá a seguinte mensagem de erro:
    
     ![Exemplo da mensagem de erro quando você adiciona instruções para Selecionar, Filtrar ou Formatar.](images/o365_reporting_incorrect_data_feed.png)
  
3. Após inserir a URL do serviço de relatório, selecione **Usar este nome e senha** sob **Credenciais de logon**. Na caixa **Nome de Usuário**, digite seu nome de logon do Office 365 (por exemplo, admin@litwareinc.onmicrosoft.com). Na caixa **Senha**, digite sua senha de logon do Office 365 e clique em **Avançar**. Em seguida, o Excel tentará conectar-se ao serviço de relatórios usando as credenciais fornecidas.
    
4. Após ser autenticado, você verá a página **Selecionar Tabelas**. Selecione o relatório que gostaria de ver (por exemplo, **MailTrafficTop** ) e clique em **Avançar**:
    
     ![Exemplo da página Selecionar Tabelas do Assistente de Conexão de Dados.](images/o365_reporting_select_tables.png)
  
    > [!NOTE]
    > É possível selecionar vários relatórios. Isso resulta em várias tabelas/gráficos adicionados à sua planilha do Excel. Também é possível criar uma tabela/gráfico único que combina dados de vários relatórios. No entanto, não discutiremos esta opção neste artigo introdutório. 
  
5. Após clicar em **Avançar** você será direcionado para a página **Salvar Arquivo de Conexão de Dados e Concluir**:
    
     ![Exemplo da página Salvar Arquivo de Conexão de Dados e Concluir do Assistente de Conexão de Dados.](images/o365_reporting_odata_finish.png)
  
    Não é preciso inserir informações aqui. Para recuperar seus dados, basta clicar em **Concluir**. No entanto, vale observar que, por padrão, o Excel salva informações sobre cada conexão de dados realizada. Esses dados são armazenados em sua pasta **Minhas Fontes de Dados**:
    
     ![Exemplo de caixa de diálogo para salvar arquivo para a pasta Minhas Fontes de Dados.](images/o365_reporting_save_data_source.png)
  
    É por isso que as caixas de diálogo incluem caixas de texto com rótulos como **Nome Amigável** e **Palavras-chave de Pesquisa**, estas opções lhe conferem a oportunidade de personalizar estas conexões de dados. Dessa forma você não fica com várias fontes de dados parecidas com estas:
    
  ```
  DataFeed_1_reports-office365-com ClientSoftwareBrowserDetail.odc
DataFeed_1_reports-office365-com MailTrafficTop.odc
DataFeed_1_reports-office365-com Multiple Tables.odc
DataFeed_2_reports-office365-com MailboxActivityWeekly.odc
DataFeed_2_reports-office365-com MailTrafficTop.odc
DataFeed_3_reports-office365-com ClientSoftwareBrowserDetail.odc
  ```

Se você marcar a caixa de seleção **Salvar senha em arquivo**, é possível reutilizar estes feeds de dados. Por exemplo, supondo que você salve uma conexão de dados como **Relatório do Navegador do Cliente**. Da próxima vez que precisar de informações sobre os navegadores Web que estão sendo usados para acessar o seu domínio do Office 365, você não terá que usar o assistente para conexão de dados. Em vez disso, tudo o que precisa fazer é abrir o Excel, clicar em **Dados** e em **Fontes Existentes**. Selecione a conexão de dados desejada na caixa de diálogo **Conexões Existentes** e clique em **OK**:
    
![Exemplo de como selecionar a conexão de dados desejada na caixa de diálogo Conexões Existentes.](images/o365_reporting_select_connection.png)
  
Nesse momento, o Excel faz a conexão para você e recupera os dados.
    
Observe que esses arquivos .ODC são arquivos XML de texto sem formatação. Incluídos neles estão seu nome de usuário e senha do Office 365:
    
\<odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=*;Max Received Message Size=4398046511104;Integrated Security=Basic; **User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!**;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/\</odc:ConnectionString>
    
Se você não gosta da ideia de salvar seu nome de usuário e senha em um arquivo de texto sem formatação, não marque a caixa rotulada **Salvar senha em arquivo**. Entretanto, lembre-se que se fizer isso não poderá reutilizar estas conexões de dados. Isso acontece porque, sem o nome de usuário e a senha, o Office 365 não pode autenticar a sua tentativa de logon no serviço.
    
6. Clique em **Concluir** na página **Salvar Arquivo de Conexão de Dados e Concluir** e a caixa de diálogo **Importar Dados** aparecerá:
    
     ![Exemplo da caixa de diálogo Importar Dados.](images/o365_reporting_import_data.png)
  
7. Selecione as opções de exibição (por exemplo, **Relatório de Tabela Dinâmica** ) e clique em **OK**. Se tudo der certo, os seus dados serão importados e apresentados em qualquer opção de exibição que você tenha escolhido:
    
     ![Exemplo de dados importados com êxito para uma planilha do Excel.](images/o365_reporting_sample_spreadsheet.png)
  
O que fazer com esses dados é escolha sua. Para obter sugestões, confira [Crie um painel nos Serviços do Excel usando o feed de dados oData](https://technet.microsoft.com/pt-BR/library/jj873965%28v=office.15%29.aspx). Ainda que este artigo não use o serviço de relatório do Office 365, ele fornece algumas dicas úteis de como realizar ações como adicionar filtros e segmentações ao seu novo painel.
  
## <a name="see-also"></a>Veja também

#### 

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Use o Windows PowerShell para criar relatórios no Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

