---
title: "Proteção de arquivos confidenciais no ambiente de desenvolvimento e teste Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Resumo: Configurar e demonstrar como o Office 365 Information Rights Management protege arquivos confidenciais, mesmo quando eles são lançados ao conjunto de sites do SharePoint Online errado."
ms.openlocfilehash: 22f12143dc7cb50c19a135f51c08cb4b9bf02f38
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Proteção de arquivos confidenciais no ambiente de desenvolvimento e teste Office 365

 **Resumo:** Configurar e demonstrar como o Office 365 Information Rights Management protege arquivos confidenciais, mesmo quando eles são lançados ao conjunto de sites do SharePoint Online errado.
  
Gerenciamento de direitos de informação (IRM) no Office 365 é um conjunto de recursos para proteger os documentos que são baixados listas e bibliotecas do SharePoint Online. Arquivos baixados são criptografados e contenham cópia aberta, salvar e imprimir permissões que refletem a biblioteca do SharePoint Online na qual eles foram armazenados.
  
Com as instruções deste artigo, você pode habilitar e testar o IRM no Office 365 para arquivos que contenham informações confidenciais possíveis em sua assinatura de avaliação do Office 365.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: Criar o seu ambiente de desenvolvimento e teste do Office 365

Se você deseja testar a proteção de arquivo confidenciais de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você deseja testar a proteção de arquivos confidenciais em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testando a proteção de arquivos confidenciais não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa testar a proteção de arquivos confidenciais e experimentar em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Fase 2: Demonstre como documentos de sites permissões protegido podem ser vazados

Nesta fase, você demonstrar que alguém pode fazer o download de um documento de um site protegido por permissões e carregá-la a um site que tenha permissões totalmente abertas.
  
Primeiro, você adiciona três novas contas de usuário que representam executivos e atribuir-lhes licenças do Office 365 E5.
  
Use as instruções em [conectar-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar os módulos do PowerShell (se necessário) e se conectar à sua nova assinatura do Office 365 de:
  
- Seu computador (para o ambiente leve de desenvolvimento/teste do Office 365).
    
- A máquina virtual CLIENT1 (para o ambiente de desenvolvimento e teste de enterprise simulado Office 365).
    
Na caixa de diálogo **Solicitação de credencial do Windows PowerShell** , digite o nome de administrador global do Office 365 (exemplo: jdoe@contosotoycompany.onmicrosoft.com) e a senha da sua assinatura de avaliação do Office 365.
  
Preencha o nome da sua organização (exemplo: contosotoycompany) e o país de dois caracteres de código para o seu local e, em seguida, execute os seguintes comandos no prompt Windows Azure Active Directory módulo para Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Na exibição do comando **New-MsolUser** , observe a gerado senha da conta do CEO e registre-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Na exibição do comando **New-MsolUser** , observe a gerado senha da conta do diretor financeiro e registre-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Na exibição do comando **New-MsolUser** , observe a gerado senha da conta de COO e registre-a em um local seguro.
  
Em seguida, você pode cria um grupo de executivos privado e adicione as novas contas de executivas a ela.
  
1. No seu navegador, vá para o portal do Office em [http://portal.office.com](http://portal.office.com) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
  - Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 lightweight, abra uma sessão particular do Internet Explorer ou seu navegador e acesse do computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, use o portal Azure para conectar a máquina virtual CLIENT1 e entrar em CLIENT1.
    
2. Na guia **Página inicial do Microsoft Office** , clique em **Admin > grupos > grupos**e, em seguida, clique em **Adicionar um grupo**.
    
3. Em **Adicionar um grupo**, selecione o **grupo do Office 365** para o tipo de grupo, digite **executivos** em **nome** e **Id de grupo**, selecione **privada** para **privacidade**e, em seguida, clique em **Selecionar proprietário**.
    
4. Na lista, clique em seu nome de conta de administrador global.
    
5. Clique em **Adicionar**e, em seguida, clique em **Fechar**.
    
6. Na lista de grupos, clique em **executivos**.
    
7. Clique em **Editar para membros**.
    
8. Clique em **Adicionar membros**. Na lista de membros, selecione as seguintes contas de usuário:
    
  - Diretor executivo
    
  - Diretor financeiro
    
  - Diretor de operações
    
9. Clique em **Salvar**e, em seguida, clique em **Fechar**.
    
10. Feche a guia do **Centro de administração do Office** .
    
Em seguida, você pode cria um conjunto de sites de executivos e permitir que apenas os membros do grupo executivos para acessá-lo.
  
1. Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .
    
2. Na guia do **Centro de administração do Office** , clique em **centrais de Admin > SharePoint**.
    
3. Na guia do **Centro de administração do SharePoint** , clique em **Novo > conjunto de sites particulares**.
    
4. No painel de novo conjunto de sites, digite **executivos** em **título**, executivos na caixa URL, especifique o nome da sua conta de administrador global no **administrador**e clique em **Okey**.
    
5. Aguarde até que o novo conjunto de sites foi criado. Quando concluir, copie a URL do novo conjunto de sites executivos e colá-lo em uma nova guia do navegador.
    
6. No canto direito superior do conjunto de sites **executivos** , clique no ícone configurações e, em seguida, clique em **compartilhado com**.
    
7. Em **compartilhamento 'Executivos'**, clique em **Avançado**.
    
8. Na lista de grupos do SharePoint, clique em **Membros de executivos**.
    
9. Na página **pessoas e grupos** , clique em **novo**.
    
10. Em **compartilhamento 'Executivos'**, digite **executivos**, clique no grupo **executivos** e, em seguida, clique em **compartilhar**.
    
11. Feche a guia **pessoas e grupos** .
    
Em seguida, você permitir que todos acessar o conjunto de sites de vendas.
  
1. A partir da guia do **Centro de administração do SharePoint** , copie a URL do conjunto de sites de vendas e colá-lo em uma nova guia do navegador..
    
2. No canto superior direito, clique no ícone configurações e, em seguida, clique em **compartilhado com**.
    
3. Em **compartilhamento 'Conjunto de sites de vendas'**, clique em **Avançado**.
    
4. Na lista de grupos do SharePoint, clique em **membros do conjunto de sites de vendas**.
    
5. Na página **pessoas e grupos** , clique em **novo**.
    
6. Em **compartilhamento 'Conjunto de sites de vendas'**, digite **todos**, clique em **todos exceto os usuários externos**e, em seguida, clique em **compartilhar**.
    
7. Feche as guias de **conjunto de sites de vendas** e **do SharePoint** .
    
Em seguida, você pode entrar com uma conta executiva e cria um documento no conjunto de sites executivos.
  
1. Na guia **Página inicial do Microsoft Office** , clique no ícone de usuário no canto superior direito e clique em **Sair**.
    
2. Vá para [http://portal.office.com](http://portal.office.com).
    
3. Na página do **Office 365 entrar** , clique em **usar outra conta**.
    
4. Digite o nome da conta **CEO** e sua senha e clique em **entrar**.
    
5. Em uma nova guia do navegador, digite a URL para o conjunto de sites de executivos ( **https://**\<nome da organização >**.sharepoint.com/sites/executives**).
    
6. Clique em **documentos**, clique em **novo** e clique em **Documento do Word**.
    
7. Clique na barra de título e digite **SensitiveData-BeforeIRM**.
    
8. Clique no corpo do documento e digite **minutos da reunião placa mais recente**e clique em **executivos**.
    
     Você deverá ver **SensitiveData-BeforeIRM.docx** na pasta **Documents** .
    
Em seguida, você pode baixar uma cópia local do documento SensitiveData-BeforeIRM.docx e depois enviá-lo acidentalmente ao conjunto de sites de vendas.
  
1. No computador local, crie uma nova pasta (por exemplo, c\\TLGs\\SensitiveDataTestFiles).
    
2. Na guia **documentos** do seu navegador, selecione o documento **SensitiveData-BeforeIRM.docx** , clique nas reticências e, em seguida, clique em **Baixar**.
    
3. Armazene um documento **SensitiveData-BeforeIRM.docx** na pasta criada na etapa 1.
    
4. Em uma nova guia do navegador, digite a URL para o conjunto de sites de vendas ( **https://**\<nome da organização >**.sharepoint.com/sites/sales**).
    
5. Clique na pasta de **documentos** do que o **conjunto de sites de vendas**.
    
6. Clique em **carregar**e, em seguida, especifique **SensitiveData-BeforeIRM.docx** documento na pasta criada na etapa 1 e clique em **Okey**.
    
7. Verifique se o documento **SensitiveData-BeforeIRM.docx** na pasta **Documents** .
    
8. Feche as guias de **vendas** e **do SharePoint** .
    
Em seguida, você pode entrar como User5 e tenta abrir o documento SensitiveData-BeforeIRM.docx no conjunto de sites de vendas.
  
1. Na guia **Página inicial do Microsoft Office** , clique no ícone de usuário no canto superior direito e clique em **Sair**.
    
2. Vá para [http://portal.office.com](http://portal.office.com).
    
3. Na página do **Office 365 entrar** , clique em **usar outra conta**.
    
4. Digite o nome da conta User5 e sua senha e clique em **entrar**.
    
5. Em uma nova guia do navegador, digite a URL para o conjunto de sites de vendas.
    
6. Na pasta **documentos** do que o **conjunto de sites de vendas**, clique no documento de **SensitiveData-BeforeIRM.docx** .
    
    Você deve ver seu conteúdo.
    
7. Feche as guias de **documentos** e o **conjunto de sites de vendas** .
    
Ao postar acidentalmente o documento SensitiveData-BeforeIRM.docx no conjunto de sites de vendas, CEO ignorada a segurança de permissões do conjunto de sites executivos.
  
Para preparar o Office 365 para fases 3 e 4, habilite o IRM para o SharePoint Online.
  
1. Na guia **Página inicial do Microsoft Office** , clique no ícone de usuário no canto superior direito e clique em **Sair**.
    
2. Vá para [http://portal.office.com](http://portal.office.com).
    
3. Na página do **Office 365 entrar** , clique no nome da conta de administrador global, digite sua senha e, em seguida, clique em **entrar**.
    
4. Na guia **Página inicial do Microsoft Office** , clique em **Admin > centrais de Admin > SharePoint**.
    
5. Na guia do **Centro de administração do SharePoint** , clique em **configurações**.
    
6. Na página **configurações** , na seção **Gerenciamento de direitos de informação (IRM)** , selecione **usar o serviço IRM especificado na sua configuração**e, em seguida, selecione **Atualizar configurações de IRM**.
    
7. Feche a guia do **Centro de administração do SharePoint** .
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Fase 3: Usar SharePoint Information Rights Management com um grupo particular do Office 365

Nesta fase, você usa SharePoint Information Rights Management com um grupo particular do Office 365 para proteger o acesso a um documento com informações confidenciais, mesmo quando ela é postada em um site com permissões open.
  
Primeiro, você pode habilitar e configurar o IRM para a biblioteca de documentos do conjunto de sites executivos. 
  
1. Em uma nova guia do navegador, digite a URL para o conjunto de sites de executivos.
    
2. Clique em **documentos**.
    
3. No canto superior direito, clique no ícone configurações e clique em **definições da biblioteca**.
    
4. Na página **configurações** , em **permissões e gerenciamento**, clique em **Gerenciamento de direitos de informação**.
    
5. Na página **Configurações de gerenciamento de direitos de informações** :
    
  - Selecione **Restringir permissão aos documentos essa biblioteca no download**.
    
  - Para **criar um título de política de permissão**, digite **executivos**.
    
  - Para **Adicionar uma descrição da política de permissão**, digite o **IRM para executivos**.
    
6. Clique em **Mostrar opções**.
    
7. Em **definir configurações adicionais do IRM biblioteca**, selecione **não permitir que os usuários carreguem documentos que não têm suporte para IRM**.
    
8. Em **Configurar direitos de acesso de documento**, selecione **Permitir visualizadores para imprimir** e **visualizadores de permissões para gravar em uma cópia do documento baixado**.
    
9. Em **definir proteção de grupo e o intervalo de credenciais**, selecione **Permitir proteção de grupo** e para o **grupo padrão**, digite **executivos**.
    
10. Clique em **OK**.
    
Em seguida, atuando como CEO, você carregar um novo documento na pasta de documentos de executivos, baixá-lo e acidentalmente carregá-la para a pasta de documentos de vendas.
  
1. Abra a pasta local onde você armazenou o documento **SensitiveData-BeforeIRM.docx** .
    
2. Clique com o botão **SensitiveData-BeforeIRM.docx**e clique em **Copiar**.
    
3. Com o botão direito na pasta e, em seguida, clique em **Colar**.
    
4. Renomeie o novo arquivo **SensitiveData-BeforeIRM - Copy.docx** para **SensitiveData-AfterIRM.docx**.
    
5. Na guia **Página inicial do Microsoft Office** no seu navegador, clique no ícone de usuário no canto superior direito e clique em **Sair**.
    
6. Vá para [http://portal.office.com](http://portal.office.com).
    
7. Na página do **Office 365 entrar** , clique no nome de conta do CEO, digite sua senha e, em seguida, clique em **entrar**.
    
8. Em uma nova guia do navegador, digite a URL para o conjunto de sites de executivos.
    
9. Na página de **documentos** , clique em **carregar**, especifique o documento **SensitiveData-AfterIRM.docx** em sua pasta local e clique em **Abrir**.
    
10. Selecione o novo documento **SensitiveData-AfterIRM.docx** na página de **documentos** , clique nas reticências (…) na barra de menus e, em seguida, clique em **Baixar**.
    
11. Quando solicitado, salve o documento de **SensitiveData-AfterIRM.docx** na sua pasta local, substituindo a versão original.
    
12. Feche a guia para a página de **documentos** .
    
13. Em uma nova guia do navegador, digite a URL para o conjunto de sites de vendas.
    
14. Clique em **documentos**.
    
15. Na página de **documentos** , clique em **carregar**, especifique o documento **SensitiveData-AfterIRM.docx** em sua pasta local e clique em **Abrir**.
    
16. Feche as guias de **conjunto de sites de vendas** e **do SharePoint** .
    
Em seguida, atuando como um usuário normal, você tenta acessar o documento **SensitiveData-AfterIRM.docx** da pasta de documentos de vendas.
  
1. Na guia **Página inicial do Microsoft Office** no seu navegador, clique no ícone de usuário no canto superior direito e clique em **Sair**.
    
2. Vá para [http://portal.office.com](http://portal.office.com).
    
3. Na página do **Office 365 entrar** , clique no nome da conta de User5, digite sua senha e, em seguida, clique em **entrar**.
    
4. Em uma nova guia do navegador, digite a URL para o conjunto de sites de vendas.
    
5. Clique em **documentos**.
    
6. Na página de **documentos** , abra o documento de **SensitiveData-AfterIRM.docx** .
    
    Você deverá ver uma mensagem que declara "Desculpe, Word Online não é possível abrir este documento porque ele está protegido por gerenciamento de direitos de informação (IRM)." 
    
7. Clique em **Editar no Word**. Você será solicitado a se desejar abrir o arquivo. Clique em **Sim**.
    
8. Você será solicitado a sign-in. Digite o nome da conta da conta User5 e clique em **Avançar**.
    
9. Você será solicitado a fornecer a senha. Digite a senha para a conta de User5 e clique em **entrar**. 
    
    Você deverá ver a uma mensagem que declara: "Você não tem as credenciais que permitam abrir este documento".
    
10. Clique em **não**.
    
Outra maneira para ver a proteção de IRM é examinar os arquivos em sua pasta local. O **SensitiveData-AfterIRM.docx** deve ser muito maior do que o arquivo **SensitiveData-BeforeIRM.docx** . O arquivo **SensitiveData-AfterIRM.docx** é criptografado e as informações de proteção de IRM adicionou a ele.
  
## <a name="see-also"></a>Veja também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento e teste de configuração de base](base-configuration-dev-test-environment.md)
  
[Ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)


