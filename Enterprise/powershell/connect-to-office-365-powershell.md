---
title: Conectar-se ao PowerShell do Office 365
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
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Resumo: conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para realizar tarefas do Centro de administração do Office 365 a partir da linha de comando."
ms.openlocfilehash: 942c128d8cfbcf4e78f054a0ab3a51b05173073f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-office-365-powershell"></a>Conectar-se ao PowerShell do Office 365

 **Resumo:** conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para realizar tarefas de administração do Office 365 a partir da linha de comando.
  
O Office 365 PowerShell permite gerenciar as configurações do Office 365 na linha de comando. Conectar-se ao Office 365 PowerShell é um processo simples de três etapas em que você instala e executa o software necessário e depois se conecta à sua organização do Office 365. 

Essas instruções de conexão são as mesmas do tópico [Azure Active Directory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).
  
> [!TIP]
> **Novo no PowerShell? ** Veja um [vídeo de visão geral do PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), apresentado pelo LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

- Tempo estimado para conclusão: 5 minutos
    
- Você pode usar as seguintes versões do Windows:
    
  - Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Use uma versão de 64 bits do Windows, pois o suporte para a versão de 32 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell foi descontinuada em outubro de 2014.
    
-  A conta corporativa ou de estudante do Office 365 que você usa para esses procedimentos precisa ser membro de uma função de administrador do Office 365. Para mais informações, confira [Sobre as funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).
    
## <a name="step-1-install-required-software"></a>Etapa 1: Instalar o software necessário

Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.
  
1.  Instale a versão de 64 bits do Assistente de Conexão do Microsoft Online Services: [Assistente de Conexão do Microsoft Online Services para profissionais de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Instale a versão de 64 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell seguindo estas etapas:
    
  - Abra a página da Web do [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185)
    
  - Em **Arquivos em Download** na parte inferior da página, clique em **Download** para o arquivo **AdministrationConfig-V1.1.166.0-GA.msi** e instale-o.
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a>Etapa 2: Abrir o Módulo do Microsoft Azure Active Directory

1. Localizar e abrir o Módulo Microsoft Azure Active Directory para Windows PowerShell usando um dos seguintes métodos com base na sua versão do Windows:
    
  - **Menu Iniciar** A partir da área de trabalho, clique em **Iniciar** e, em seguida, digiteAzure.
    
  - **Sem menu Iniciar** ProcurarAzure usando qualquer um destes métodos:
    
  - Na tela Inicial, clique em uma área vazia e digite Azure.
    
  - Na área de trabalho ou na tela Inicial, pressione a tecla Windows + Q. No botão Pesquisar, digite Azure.
    
  - Na área de trabalho ou na tela Inicial, mova o cursor para o canto superior direito ou passe o dedo da borda direita da tela para a esquerda para mostrar os botões. Escolha o botão Pesquisar e digite **Azure**.
    
2. Nos resultados, clique em **Módulo Microsoft Azure Active Directory para Windows PowerShell**.
    
## <a name="step-3-connect-to-your-office-365-subscription"></a>Etapa 3: Conectar-se à assinatura do Office 365
<a name="step3"> </a>

Para conectar-se apenas com o  *nome e senha de conta*  :
  
1. Na janela de comando **Módulo Microsoft Azure Active Directory para Windows PowerShell**, execute os comandos a seguir.
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. Na caixa de diálogo **Solicitação de Credencial do Windows PowerShell**, digite o nome de usuário e a senha do Office 365conta comercial ou escolar e clique em **OK**.
    
Para conectar-se com a  *MFA (autenticação multifator)*  :
  
1. Na janela de comando **Módulo Microsoft Azure Active Directory para Windows PowerShell**, execute o comando a seguir.
    
  ```
  Connect-MsolService
  ```

2. Na caixa de diálogo **PowerShell do Azure Active Directory**, digite seu Office 365conta comercial ou escolarnome de usuário e senha e clique em **Entrar**.
    
3. Siga as instruções na caixa de diálogo **PowerShell do Azure Active Directory** para fornecer informações de autenticação adicionais, como o código de verificação, e clique **Entrar**.
    
## <a name="how-do-you-know-this-worked"></a>Como saber se funcionou?
<a name="step3"> </a>

Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.
  
Caso você receba erros, verifique os seguintes requisitos:
  
- **Senhas incorretas são problemas comuns**. Execute as Etapa 3 novamente e preste muita atenção ao nome de usuário e à senha inseridos.
    
- **O Módulo Microsoft Azure Active Directory para Windows PowerShell requer que o recurso do Microsoft .NET Framework 3.5. _x_ esteja habilitado em seu computador**. É provável que seu computador tenha uma versão mais recente instalada (por exemplo, 4 ou 4.5. _x_), mas a compatibilidade com versões anteriores do .NET Framework pode ser habilitada ou desabilitada. Para saber mais, confira os seguintes tópicos:
    
  - Para Windows Server 2012 ou Windows Server 2012 R2, confira [Habilitar o .NET Framework 3.5 usando o Assistente de Adição de Funções e Recursos](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Para Windows 8 ou Windows 8.1, confira [Instalando o .NET Framework 3.5 no Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - Para Windows 7 ou Windows Server 2008 R2, confira [Não é possível abrir o módulo Microsoft Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **Sua versão do Módulo Microsoft Azure Active Directory para Windows PowerShell deve estar desatualizada.** Para verificar, execute o seguinte comando no Office 365 PowerShell ou no Módulo Microsoft Azure Active Directory para Windows PowerShell:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Se o número da versão retornado for menor que o valor 1.0.8070.2, desinstale o Módulo Microsoft Azure Active Directory para Windows PowerShell e instale a versão mais recente usando o link da Etapa 1.
    
- **Se você receber um erro de conexão, confira este tópico:** ["Connect-MsolService: ocorreu exceção do tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>Conectar-se ao módulo do PowerShell V2 do Azure Active Directory
<a name="ConnectV2"> </a>

Para os procedimentos que exigem os novos cmdlets no [módulo PowerShell do Azure Active Directory V2]((https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)), use estas etapas para instalar o módulo e se conectar à sua assinatura do Office 365:
  
1. Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).
    
2. Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:
    
  ```
  Install-Module -Name AzureAD 
  ```

Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione ENTER.
    
3. Quando a instalação do novo módulo estiver concluída, use estes comandos para se conectar à sua assinatura do Office 365:
    
  -  Com um  *nome e senha da conta*  :
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 Na caixa de diálogo **Solicitação de Credencial do Windows PowerShell**, digite o nome de usuário e a senha do Office 365conta comercial ou escolar e clique em **OK**.
    
  - Com  *MFA (Autenticação Multifator)*  :
    
  ```
  Connect-AzureAD
  ```

Na caixa de diálogo **PowerShell do Azure Active Directory**, digite seu Office 365conta comercial ou escolarnome de usuário e senha e clique em **Entrar**.
    
Siga as instruções na caixa de diálogo **PowerShell do Azure Active Directory** para fornecer informações de autenticação adicionais, como o código de verificação, e clique **Entrar**.
    
Depois de se conectar, você poderá usar os novos cmdlets do [módulo do PowerShell V2 do Azure Active Directory]((https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)).
  
## <a name="see-also"></a>Veja também

#### 

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

