---
title: Proteção de arquivos confidenciais no ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Resumo: Configure e demonstre como o gerenciamento de direitos de informação do Office 365 protege seus arquivos confidenciais, mesmo quando eles são publicados no conjunto de sites do SharePoint Online errado.'
ms.openlocfilehash: 59d4cf56113f8b787f0caeaefddae135ad8e6249
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574065"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Proteção de arquivos confidenciais no ambiente de desenvolvimento/teste do Office 365

 **Resumo:** Configure e demonstre como o gerenciamento de direitos de informação do Office 365 protege seus arquivos confidenciais, mesmo quando eles são publicados no conjunto de sites do SharePoint Online errado.
  
O gerenciamento de direitos de informação (IRM) no Office 365 é um conjunto de recursos para proteger documentos baixados de bibliotecas e listas do SharePoint Online. Os arquivos baixados são criptografados e contêm as permissões abrir, copiar, salvar e imprimir que refletem a biblioteca do SharePoint Online na qual foram armazenadas.
  
Com as instruções deste artigo, você habilita e testa o IRM no Office 365 para arquivos que contêm possíveis informações confidenciais em sua assinatura de avaliação do Office 365.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: criar seu ambiente de desenvolvimento/teste do Office 365

Se você só quiser testar a proteção de arquivos confidenciais de forma leve com os requisitos mínimos, siga as instruções nas fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar a proteção de arquivos confidenciais em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> O teste de proteção de arquivos confidenciais não exige o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa testar a proteção de arquivos confidenciais e experimentá-lo em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Fase 2: demonstrar como os documentos de sites protegidos por permissões podem ser vazados

Nesta fase, você demonstra que alguém pode baixar um documento de um site protegido por permissões e carregá-lo em um site que tenha permissões de abertura ampla.
  
Primeiro, você adiciona três novas contas de usuário que representam executivos e atribui as licenças do Office 365 e5.
  
Use as instruções em [conectar-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar os módulos do PowerShell (se necessário) e se conectar à sua nova assinatura do Office 365 de:
  
- Seu computador (para o ambiente leve de desenvolvimento/teste do Office 365).
    
- A máquina virtual CLIENT1 (para o ambiente de desenvolvimento/teste corporativo simulado do Office 365).
    
Na caixa de diálogo solicitação de credencial do **Windows PowerShell** , digite o nome do administrador global do Office 365 (exemplo: jdoe@contosotoycompany.onmicrosoft.com) e a senha da sua assinatura de avaliação do Office 365.
  
Preencha o nome da sua organização (exemplo: contosotoycompany) e o código de país de dois caracteres para seu local e, em seguida, execute os seguintes comandos do prompt do módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Na exibição do comando **New-MsolUser** , anote a senha gerada para a conta do CEO e grave-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Na exibição do comando **New-MsolUser** , anote a senha gerada para a conta CFO e grave-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Na exibição do comando **New-MsolUser** , anote a senha gerada para a conta COO e grave-a em um local seguro.
  
Em seguida, crie um grupo de executivos privados e adicione as novas contas executivas a ele.
  
1. No navegador, vá para o portal do Office em [http://admin.microsoft.com](http://admin.microsoft.com) e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
  - Se você estiver usando o ambiente leve de desenvolvimento/teste do Office 365, abra uma sessão particular do Internet Explorer ou seu navegador e entre no computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, use o portal do Azure para se conectar à máquina virtual do CLIENT1 e, em seguida, entre no CLIENT1.
    
2. Na guia **Microsoft Office Home** , clique em **administrador do > grupos de >** e clique em **Adicionar um grupo**.
    
3. Em **Adicionar um grupo**, selecione **grupo do Office 365** para o tipo de grupo, digite **executivos** em **nome** e **ID do grupo**, selecione **privado** para **privacidade**e clique em **selecionar proprietário**.
    
4. Na lista, clique no nome da conta de administrador global.
    
5. Clique em **Adicionar**e, em seguida, clique em **fechar**.
    
6. Na lista de grupos, clique em **executivos**.
    
7. Clique em **Editar para membros**.
    
8. Clique em **Adicionar membros**. Na lista de membros, selecione as seguintes contas de usuário:
    
  - Diretor executivo
    
  - Diretor financeiro
    
  - Diretor de operações
    
9. Clique em **salvar**e, em seguida, clique em **fechar**.
    
10. Feche a guia **centro de administração do Office** .
    
Em seguida, você cria um conjunto de sites executivos e permite que apenas os membros do grupo executivos o acessem.
  
1. Na guia **Microsoft Office Home** , clique no bloco **administrador** .
    
2. Na guia **centro de administração do Office** , clique em **centros de administração > SharePoint**.
    
3. Na guia **centro de administração do SharePoint** , clique em **novo conjunto de sites privados >**.
    
4. No painel novo conjunto de sites, digite **executivos** em **título**, executivos na caixa URL, especifique o nome da conta de administrador global no **administrador**e clique em **OK**.
    
5. Aguarde até que o novo conjunto de sites tenha sido criado. Ao concluir, copie a URL do novo conjunto de sites executivos e cole-a em uma nova guia do navegador.
    
6. No canto superior direito do conjunto de sites **executivos** , clique no ícone configurações e, em seguida, clique em **compartilhado com**.
    
7. Em **compartilhar ' executivos '**, clique em **avançado**.
    
8. Na lista de grupos do SharePoint, clique em **membros de executivos**.
    
9. Na página **Pessoas e Grupos**, clique em **Novo**.
    
10. Em **compartilhar ' executivos '**, digite **executivos**, clique no grupo **executivos** e, em seguida, clique em **compartilhar**.
    
11. Feche a guia **pessoas e grupos** .
    
Em seguida, permita que todos acessem o conjunto de sites de vendas.
  
1. Na guia **centro de administração do SharePoint** , copie a URL do conjunto de sites vendas e cole-a em uma nova guia do navegador.
    
2. No canto superior direito, clique no ícone configurações e, em seguida, clique em **compartilhado com**.
    
3. Em **compartilhar "conjunto de sites de vendas"**, clique em **avançado**.
    
4. Na lista de grupos do SharePoint, clique em **membros do conjunto de sites de vendas**.
    
5. Na página **Pessoas e Grupos**, clique em **Novo**.
    
6. Em **compartilhar ' conjunto de sites de vendas '**, digite **todos**, clique em **todos exceto usuários externos**e, em seguida, clique em **compartilhar**.
    
7. Feche as guias **conjunto de sites de vendas** e **do SharePoint** .
    
Em seguida, você entra com uma conta executiva e cria um documento no conjunto de sites executivos.
  
1. Na guia **Microsoft Office Home** , clique no ícone de usuário no canto superior direito e, em seguida, **** clique em sair.
    
2. Acesse [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Na página de **entrada do Office 365** , clique em **usar outra conta**.
    
4. Digite o nome da conta do **CEO** e sua senha e clique em **entrar**.
    
5. em uma nova guia do navegador, digite a URL do conjunto de sites executivos ( **https://**\<organization name>**. sharepoint.com/sites/executives**).
    
6. Clique em **documentos**, clique em **novo** e em **documento do Word**.
    
7. Clique na barra de título e digite **SensitiveData-BeforeIRM**.
    
8. Clique no corpo do documento e digite **minutos na reunião mais recente da placa**e, em seguida, clique em **executivos**.
    
     Você verá **SensitiveData-BeforeIRM. docx** na pasta **documentos** .
    
Em seguida, Baixe uma cópia local do documento SensitiveData-BeforeIRM. docx e, em seguida, poste-a acidentalmente para o conjunto de sites Sales.
  
1. No computador local, crie uma nova pasta (por exemplo, C:\\TLGs\\SensitiveDataTestFiles).
    
2. Na guia **documentos** do navegador, selecione o documento **SensitiveData-BeforeIRM. docx** , clique nas reticências e, em seguida, clique em **baixar**.
    
3. Armazene o documento **SensitiveData-BeforeIRM. docx** na pasta criada na etapa 1.
    
4. em uma nova guia do navegador, digite a URL do conjunto de sites de vendas ( **https://**\<organization name>**. sharepoint.com/sites/sales**).
    
5. Clique na pasta **documentos** do **conjunto de sites de vendas**.
    
6. Clique em **carregar**e especifique o documento **SensitiveData-BeforeIRM. docx** na pasta criada na etapa 1 e clique em **OK**.
    
7. Verifique se o documento **SensitiveData-BeforeIRM. docx** está na pasta **documentos** .
    
8. Feche as guias **vendas** e **do SharePoint** .
    
Em seguida, você entra como User5 e tenta abrir o documento SensitiveData-BeforeIRM. docx no conjunto de sites de vendas.
  
1. Na guia **Microsoft Office Home** , clique no ícone de usuário no canto superior direito e, em seguida, **** clique em sair.
    
2. Acesse [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Na página de **entrada do Office 365** , clique em **usar outra conta**.
    
4. Digite o nome da conta do User5 e sua senha e clique em **entrar**.
    
5. Em uma nova guia do navegador, digite a URL do conjunto de sites de vendas.
    
6. Na pasta **documentos** do conjunto de **sites vendas**, clique no documento **SensitiveData-BeforeIRM. docx** .
    
    Você deve ver seu conteúdo.
    
7. Feche as guias **documentos** e **conjunto de sites de vendas** .
    
Ao postar o documento SensitiveData-BeforeIRM. docx acidentalmente no conjunto de sites de vendas, o CEO ignorou a segurança de permissões do conjunto de sites executivos.
  
Para preparar o Office 365 para as fases 3 e 4, habilite o IRM para o SharePoint Online.
  
1. Na guia **Microsoft Office Home** , clique no ícone de usuário no canto superior direito e, em seguida, **** clique em sair.
    
2. Acesse [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Na página de **entrada do Office 365** , clique no nome da conta de administrador global, digite sua senha e clique em **entrar**.
    
4. Na guia **Microsoft Office Home** , clique em **administrador do _GT_ de administração do SharePoint >**.
    
5. Na guia **centro de administração do SharePoint** , clique em **configurações**.
    
6. Na página **configurações** , na seção **Gerenciamento de direitos de informação (IRM)** , selecione **usar o serviço IRM especificado em sua configuração**e, em seguida, selecione **Atualizar configurações de IRM**.
    
7. Feche a guia **centro de administração do SharePoint** .
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Fase 3: usar o gerenciamento de direitos de informação do SharePoint com um grupo privado do Office 365

Nesta fase, você usa o gerenciamento de direitos de informação do SharePoint com um grupo privado do Office 365 para proteger o acesso a um documento com informações confidenciais, mesmo quando ele é publicado em um site com permissões abertas.
  
Primeiro, habilite e configure o IRM para a biblioteca de documentos do conjunto de sites executivos. 
  
1. Em uma nova guia do navegador, digite a URL para o conjunto de sites executivos.
    
2. Clique em **Documentos**.
    
3. No canto superior direito, clique no ícone configurações e, em seguida, clique em **configurações da biblioteca**.
    
4. Na página **configurações** , em **permissões e gerenciamento**, clique em **Gerenciamento de direitos de informação**.
    
5. Na página **configurações de gerenciamento de direitos de informação** :
    
  - Selecione **restringir permissão para documentos nesta biblioteca durante o download**.
    
  - Para **criar um título de política de permissão**, digite **executivos**.
    
  - Para **Adicionar uma descrição de política de permissão**, digite **IRM para executivos**.
    
6. Clique em **Mostrar Opções**.
    
7. Em **definir configurações de biblioteca de IRM adicionais**, selecione não **permitir que os usuários carreguem documentos que não dão suporte ao IRM**.
    
8. Em **Configurar direitos de acesso ao documento**, selecione **permitir que** os visualizadores imprimam e **permitir que os visualizadores escrevam em uma cópia do documento baixado**.
    
9. Em **definir intervalo de credenciais e proteção de grupo**, selecione **permitir proteção de grupo** e para **grupo padrão**, digite **executivos**.
    
10. Clique em **OK**.
    
Em seguida, agindo como CEO, você carrega um novo documento na pasta de documentos executivos, baixa-o e, em seguida, o carrega acidentalmente para a pasta de documentos de vendas.
  
1. Abra a pasta local onde você armazenou o documento **SensitiveData-BeforeIRM. docx** .
    
2. Clique com o botão direito do mouse em **SensitiveData-BeforeIRM. docx**e clique em **copiar**.
    
3. Clique com o botão direito do mouse na pasta e clique em **colar**.
    
4. ReNomeie o novo arquivo **SensitiveData-BeforeIRM-Copy. docx** para **SensitiveData-AfterIRM. docx**.
    
5. Na guia **Microsoft Office Home** no navegador, clique no ícone de usuário no canto superior direito e, em seguida, clique **** em sair.
    
6. Acesse [http://admin.microsoft.com](http://admin.microsoft.com).
    
7. Na página de **entrada do Office 365** , clique no nome da conta do CEO, digite sua senha e clique em **entrar**.
    
8. Em uma nova guia do navegador, digite a URL para o conjunto de sites executivos.
    
9. Na página **documentos** , clique em **carregar**, especifique o documento **SensitiveData-AfterIRM. docx** na pasta local e clique em **abrir**.
    
10. Selecione o novo documento **SensitiveData-AfterIRM. docx** na página **documentos** , clique nas reticências (...) na barra de menus e, em seguida, clique em **baixar**.
    
11. Quando solicitado, salve o documento **SensitiveData-AfterIRM. docx** na pasta local, substituindo a versão original.
    
12. Feche a guia da página de **documentos** .
    
13. Em uma nova guia do navegador, digite a URL do conjunto de sites de vendas.
    
14. Clique em **Documentos**.
    
15. Na página **documentos** , clique em **carregar**, especifique o documento **SensitiveData-AfterIRM. docx** na pasta local e clique em **abrir**.
    
16. Feche as guias **conjunto de sites de vendas** e **do SharePoint** .
    
Em seguida, agindo como um usuário normal, você tenta acessar o documento **SensitiveData-AfterIRM. docx** na pasta de documentos Sales.
  
1. Na guia **Microsoft Office Home** no navegador, clique no ícone de usuário no canto superior direito e, em seguida, clique **** em sair.
    
2. Acesse [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Na página de **entrada do Office 365** , clique no nome da conta User5, digite sua senha e clique em **entrar**.
    
4. Em uma nova guia do navegador, digite a URL do conjunto de sites de vendas.
    
5. Clique em **Documentos**.
    
6. Na página **documentos** , abra o documento **SensitiveData-AfterIRM. docx** .
    
    Você deve ver uma mensagem que diz "o Word online não pode abrir este documento porque ele está protegido pelo gerenciamento de direitos de informação (IRM)". 
    
7. Clique em **Editar no Word**. Você será solicitado a confirmar se deseja abrir o arquivo. Clique em **Sim**.
    
8. Você será solicitado a entrar. Digite o nome da conta do User5 e clique em **Avançar**.
    
9. Você será solicitado a fornecer a senha. Digite a senha para a conta User5 e clique em **entrar**. 
    
    Você deve ver a mensagem que diz: "você não tem as credenciais que permitem abrir este documento."
    
10. Clique em **não**.
    
Outra maneira de ver a proteção de IRM é examinar os arquivos na sua pasta local. O **SensitiveData-AfterIRM. docx** deve ser muito maior do que o arquivo **SensitiveData-BeforeIRM. docx** . O arquivo **SensitiveData-AfterIRM. docx** é criptografado e tem as informações de proteção do IRM adicionadas a ele.
  
## <a name="see-also"></a>Confira também


[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md)


