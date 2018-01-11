---
title: Ambiente de desenvolvimento/teste do Office 365
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
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: "Resumo: Use este guia de laboratório de teste para criar uma assinatura de avaliação do Office 365 para avaliação ou desenvolvimento e teste."
ms.openlocfilehash: 60ac59f8b6af81ff18a4c41c0ce5d2376bc161e7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="office-365-devtest-environment"></a>Ambiente de desenvolvimento/teste do Office 365

 **Resumo:** Use este guia de laboratório de teste para criar uma assinatura de avaliação do Office 365 para avaliação ou desenvolvimento e teste.
  
Você pode usar uma assinatura de avaliação do Office 365 e criar um ambiente de desenvolvimento e teste do Office 365 para aplicativos ou para demonstrar os recursos e capacidades do Office 365. Existem duas versões:
  
- O ambiente de desenvolvimento e teste do Office 365 lightweight consiste em uma assinatura de avaliação do Office 365 que você pode acessar do computador principal.
    
    Use esse ambiente quando quiser demonstrar rapidamente um recurso. Para o ambiente de desenvolvimento e teste do Office 365 leve, conclua as etapas 2 e 3 deste artigo.
    
- Ambiente de desenvolvimento e teste do Office 365 enterprise simulado consiste em uma assinatura de avaliação do Office 365 e uma intranet da organização simplificado conectado à Internet, que é hospedada no serviços de infraestrutura do Microsoft Azure. Você pode construir essa configuração completamente na nuvem da Microsoft.
    
    Use esse ambiente quando quiser demonstrar um recurso ou um aplicativo em um ambiente que se parece com uma rede de organização típica conectada à Internet ou para recursos que exigem esse tipo de ambiente. Para o ambiente de desenvolvimento e teste de enterprise simulado Office 365, conclua as fases 1, 2 e 3 deste artigo.
    
> [!NOTE]
> Convém imprimir este artigo para registrar os valores específicos que você precisará desse ambiente nos 30 dias da assinatura de avaliação do Office 365. Você pode estender facilmente a assinatura de trilha para outro 30 dias. Para um ambiente de desenvolvimento e teste permanente, crie uma nova assinatura com um pequeno número de licenças paga. 
  
![Guias do Laboratório de Teste da Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>Fase 1: Criar a configuração base no Windows Azure

Siga as instruções no [ambiente de desenvolvimento e teste de configuração básica](base-configuration-dev-test-environment.md).
  
Você precisará de uma assinatura do Windows Azure. Você pode usar a [Versão de avaliação gratuita do Windows Azure](https://azure.microsoft.com/pricing/free-trial/) para esta configuração. Se você tiver uma assinatura do MSDN ou o Visual Studio, consulte [crédito Azure mensal para assinantes do Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
Aqui está a configuração resultante.
  
![O ambiente de desenvolvimento e teste de Configuração de Base no Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
Essa configuração consiste das máquinas virtuais DC1, APP1 e CLIENT1 em uma sub-rede de uma rede virtual do Azure.
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>Fase 2: Criar uma assinatura de avaliação do Office 365

Para iniciar a sua assinatura de avaliação do Office 365 E5, primeiro é necessário um nome de empresa fictícia e uma nova conta da Microsoft.
  
1. É recomendável que você usar uma variant do nome da empresa Contoso para o nome da sua empresa, que é uma empresa fictícia usada no conteúdo de exemplo da Microsoft, mas isso não é obrigatório. Registrar seu nome de empresa fictícia aqui: _
    
2. Para se inscrever para uma nova conta da Microsoft, vá para [https://outlook.com](https://outlook.com) e crie uma conta com uma nova conta de email e o endereço. Você usará essa conta para inscrever-se no Office 365.
    
  - Registre o nome e sobrenome de sua nova conta: _
    
  - Registrar o nova conta endereço de email aqui: ___@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Inscreva-se para uma assinatura de avaliação do Office 365 E5

1. Para o ambiente de desenvolvimento e teste do Office 365 leve, abra o navegador de Internet no seu computador e vá para [https://aka.ms/e5trial](https://aka.ms/e5trial). 
    
    Para o ambiente de desenvolvimento e teste de enterprise simulado Office 365:
    
  - Do [portal do Azure](https://portal.azure.com), conecte-se ao CLIENT1 com CORP\\conta User1.
    
  - Abra um prompt de comando do Windows PowerShell de nível de administrador e, em seguida, execute estes comandos:
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) para obter um arquivo de texto que contém todos os comandos do PowerShell neste artigo.
  
  - Na tela Iniciar, clique em **Internet Explorer** e vá para [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. Na página de **boas-vindas, vamos fazer conhecê-lo** , especifique:
    
  - Seu local físico
    
  - O nome e sobrenome de sua nova conta da Microsoft
    
  - Seu novo endereço de conta de email
    
  - Um número de telefone comercial
    
  - Nome da sua empresa fictícia
    
  - Um tamanho de organização de 250-999 pessoas
    
3. Clique em **apenas um deles mais etapa**.
    
4. Na página **criar sua ID de usuário** , digite um nome de usuário com base em seu novo endereço de email, sua empresa fictícia após o sinal (remover todos os espaços no nome de usuário), @ e uma senha (duas vezes) para este novo Office 365 da conta.
    
    Registre a senha que você digitou em um local seguro.
    
    Registrar seu nome de empresa fictícia, para ser referida como o **nome da organização**, aqui: _
    
5. Clique em **Criar minha conta**.
    
6. Sobre o **Prove. Você está. Não. R. robô.** página, digite o número de telefone do seu telefone capaz de texto e, em seguida, clique em **texto-me**.
    
7. Digite o código de verificação da mensagem de texto recebido e clique em **Avançar**.
    
8. Registre a URL de página de entrada aqui (select e cópia): _
    
9. Registre a ID de usuário aqui (select e cópia): ___.onmicrosoft.com
    
    Esse valor será chamado como o **nome de administrador global do Office 365**.
    
10. Quando você vê que **você está pronto para ir**, clique nele.
    
11. Na próxima página, aguarde até que o Office 365 for concluído a configuração de backup e todos os blocos estão disponíveis.
    
Você deverá ver a página portal principal do Office 365 no qual você pode acessar os Serviços Online do Office e o Centro de administração do Office 365.
  
Para o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, aqui está a configuração resultante.
  
![O ambiente de desenvolvimento e teste do Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Esta configuração consiste em: 
  
- Os virtual DC1, APP1 e CLIENT1 máquinas em uma sub-rede de uma rede virtual do Azure.
    
- Uma assinatura de avaliação do E5 do Office 365.
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>Fase 3: Configurar sua assinatura de avaliação do Office 365

Nesta fase, você pode configurar sua assinatura do Office 365 com outros usuários e sites de equipe do SharePoint Online.
  
Primeiro, você pode adicionar quatro novos usuários e atribuir-lhes licenças E5.
  
Use as instruções em [conectar-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar os módulos do PowerShell e se conectar à sua nova assinatura do Office 365 de:
  
- Seu computador (para o ambiente leve de desenvolvimento/teste do Office 365).
    
- A máquina virtual CLIENT1 (para o ambiente de desenvolvimento e teste de enterprise simulado Office 365).
    
 Na caixa de diálogo solicitação de credencial do Windows PowerShell, digite o nome de administrador global do Office 365 (exemplo: jdoe@contosotoycompany.onmicrosoft.com) e a senha.
  
Preencha o nome de sua organização (exemplo: contosotoycompany), o código de país com dois caracteres de seu local e execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

Na exibição do comando **New-MsolUser** , observe a gerado senha para a conta de usuário 2 e registre-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

Na exibição do comando **New-MsolUser** , observe a gerado senha para a conta de usuário 3 e registre-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

Na exibição do comando **New-MsolUser** , observe a gerado senha para a conta de usuário 4 e registre-a em um local seguro.
  
Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

Na exibição do comando **New-MsolUser** , observe a gerado senha para a conta de usuário 5 e registre-a em um local seguro.
  
Em seguida, você pode cria três novos sites de equipe do SharePoint Online para as vendas, produção e departamentos de suporte.
  
### <a name="create-three-new-sharepoint-online-team-sites"></a>Crie três novos sites de equipe do SharePoint Online

1. Instalar o [Shell de gerenciamento do SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251) (o x64 versão).
    
2. Clique em **Iniciar**, digite **sharepoint**e clique em **Shell de gerenciamento do SharePoint Online**.
    
3. Preencha o nome da sua organização (exemplo: contosotoycompany), e, em seguida, execute os seguintes comandos no prompt de Shell de gerenciamento do SharePoint Online para se conectar ao serviço do SharePoint Online
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. Na caixa de diálogo do **Microsoft SharePoint Online Management Shell** , digite o nome de administrador global do Office 365 (exemplo: jdoe@contosotoycompany.onmicrosoft.com) e uma senha e clique em **entrar**.
    
5. Para criar três novos sites de equipe (vendas, produção e suporte), preencham o nome de administrador global do Office 365 em, em seguida, execute os seguintes comandos no prompt de Shell de gerenciamento do SharePoint Online:
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. Execute este comando para listar as URLs desses sites novos:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. No Internet Explorer, digite a URL do site de produção para ver o site de equipe do SharePoint Online padrão para o departamento de produção.
    
## <a name="record-values-for-future-reference"></a>Valores do registro para referência futura

Registre esses valores para trabalhar com ou implantando guias de laboratório de teste adicionais neste ambiente de teste:
  
- Nome de administrador global do Office 365: ___.onmicrosoft.com (da etapa 9 da fase 2)
    
    Além disso, registre a senha dessa conta em um local seguro.
    
- O nome da sua organização de assinatura de avaliação: _ (da etapa 4 da fase 2)
    
- Para listar as contas de usuário 2, 3 do usuário, usuário 4 e 5 do usuário, execute o seguinte comando a partir do prompt do Windows Azure Active Directory módulo para Windows PowerShell:
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Registre os nomes de conta:
    
  - Nome da conta de usuário 2: user2@___.onmicrosoft.com
    
  - Nome da conta de usuário 3: user3@___.onmicrosoft.com
    
  - Nome da conta de usuário 4: user4@___.onmicrosoft.com
    
  - Nome da conta de usuário 5: user5@___.onmicrosoft.com
    
    Registre também as senhas para essas contas em um local seguro.
    
- Para listar as URLs de vendas, produção e oferecer suporte aos sites de equipe, execute o seguinte comando no prompt de Shell de gerenciamento do SharePoint Online:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - URL do site de produção: https://___.sharepoint.com/sites/production
    
  - URL do site de vendas: https://___.sharepoint.com/sites/sales
    
  - URL do site de suporte: https://___.sharepoint.com/sites/support
    
## <a name="next-steps"></a>Próximas etapas

Use estes artigos adicionais em seu ambiente de desenvolvimento e teste do Office 365:
  
- [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
- [A autenticação multifator para seu ambiente de desenvolvimento e teste do Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Identidade federada para seu ambiente de desenvolvimento e teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Proteção de ameaça avançada para seu ambiente de desenvolvimento e teste do Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [EDiscovery avançada para seu ambiente de desenvolvimento e teste do Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Proteção de arquivos confidenciais no ambiente de desenvolvimento e teste Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [Isolado ambiente de desenvolvimento e teste de site equipe do SharePoint Online](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Classificação de dados e rótulos no ambiente de desenvolvimento e teste Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
Estenda seu ambiente de desenvolvimento e teste do Office 365 para incluir adicionais ofertas de nuvem da Microsoft:
  
- [O ambiente de desenvolvimento e teste da Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [Office 365 e o ambiente de desenvolvimento e teste do Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a>Veja também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 e o ambiente de desenvolvimento e teste do Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)


