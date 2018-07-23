---
title: Conectar-se ao PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
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
description: 'Resumo: Conecte à sua organização do Office 365 usando o Office 365 PowerShell para realizar tarefas de centro de administração da linha de comando.'
ms.openlocfilehash: 96406fbc23adadbf77a3cd02f8c167081f908977
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720397"
---
# <a name="connect-to-office-365-powershell"></a>Conectar-se ao PowerShell do Office 365

 **Resumo:** Conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para executar tarefas de administração da linha de comando.
  
O Office 365 PowerShell permite gerenciar as configurações do Office 365 na linha de comando. Conectar-se ao Office 365 PowerShell é um processo simples de três etapas em que você instala e executa o software necessário e depois se conecta à sua organização do Office 365. 

  
> [!TIP]
> **Novo no PowerShell? ** Veja um [vídeo de visão geral do PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), apresentado pelo LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

- Tempo estimado para conclusão: 5 minutos
    
- Você pode usar as seguintes versões do Windows:
    
  - Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Use uma versão de 64 bits do Windows, pois o suporte para a versão de 32 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell foi descontinuada em outubro de 2014.
    
-  Estes procedimentos destinam-se para os usuários que são membros de uma função de administrador do Office 365. Para obter mais informações, consulte [funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).

## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Conecte-se com o Azure Active Directory PowerShell para o módulo de gráfico

Comandos no módulo do [Azure Active Directory PowerShell para gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) têm **AzureAD** em seu nome do cmdlet.

Para obter os procedimentos que exigem os cmdlets novos no Azure Active Directory PowerShell para o módulo de gráfico, execute estas etapas para instalar o módulo e conecte-se à sua assinatura do Office 365.

>[!Note]
>Consulte o [Azure Active Directory PowerShell para o módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obter informações sobre o suporte para diferentes versões do Microsoft Windows.
>

### <a name="step-1-install-required-software"></a>Etapa 1: instalar o software necessário

Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.
  
1. Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).
    
2. Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:
    
  ```
  Install-Module -Name AzureAD
  ```

Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione Enter.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Etapa 2: Conectar ao Azure AD para sua assinatura do Office 365

Para se conectar ao AD do Windows Azure para o Office 365 assinatura com um nome de conta e senha ou com *a autenticação multifator (MFA)* execute este comando em um prompt de comando do Windows PowerShell (ele não tem de ser elevado):
    
```
Connect-AzureAD
```

Na caixa de diálogo **logon em sua conta** , digite o seu trabalho do Office 365 ou o nome de usuário da conta de escola e a senha e clique em **Okey**.

Se você estiver usando MFA, siga as instruções nas caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.
    
Depois de se conectar, você pode usar os novos cmdlets para o [Windows Azure Active Directory PowerShell para o módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Conecte com o Módulo Microsoft Azure Active Directory para Windows PowerShell

Os comandos no Módulo Microsoft Azure Active Directory para Windows PowerShell têm **Msol** no nome do cmdlet.
    
### <a name="step-1-install-required-software"></a>Etapa 1: instalar o software necessário

Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.
  
1.  Instale a versão de 64 bits do Assistente de Conexão do Microsoft Online Services: [Assistente de Conexão do Microsoft Online Services para profissionais de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Instale o Módulo Microsoft Azure Active Directory para Windows PowerShell seguindo estas etapas:
    
  - Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).
  - Execute o comando **Install-Module MSOnline**.
  - Se solicitado a instalar o provedor de NuGet, digite **Y** e pressione Enter.
  - Se solicitado a instalar o módulo de PSGallery, digite **Y** e pressione Enter.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Etapa 2: Conectar ao Azure AD para sua assinatura do Office 365

Para conectar ao Azure AD para sua assinatura do Office 365 com um nome de conta e senha ou com *a autenticação multifator (MFA)*, execute este comando em um prompt de comando do Windows PowerShell (ele não tem de ser elevado):
    
```
Connect-MsolService
```

Na caixa de diálogo **logon em sua conta** , digite o seu trabalho do Office 365 ou o nome de usuário da conta de escola e a senha e clique em **Okey**.

Se você estiver usando MFA, siga as instruções nas caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.

    
### <a name="how-do-you-know-this-worked"></a>Como saber se funcionou?

Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.
  
Caso você receba erros, verifique os seguintes requisitos:
  
- **Senhas incorretas são problemas comuns**. Execute as Etapa 3 novamente e preste muita atenção ao nome de usuário e à senha inseridos.
    
- * *O Microsoft Azure Active Directory módulo para Windows PowerShell requer que o Microsoft .NET Framework 3.5.* x * recurso está ativado em seu computador * *. É provável que o seu computador tiver uma versão mais recente instalada (por exemplo, 4 ou 4.5.* x *), mas com versões anteriores a compatibilidade com versões mais antigas do .NET Framework pode ser habilitada ou desabilitada. Para obter mais informações, consulte os tópicos a seguir:
    
  - Para Windows Server 2012 ou Windows Server 2012 R2, confira [Habilitar o .NET Framework 3.5 usando o Assistente de Adição de Funções e Recursos](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Para Windows 8 ou Windows 8.1, confira [Instalando o .NET Framework 3.5 no Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - Para Windows 7 ou Windows Server 2008 R2, confira [Não é possível abrir o módulo Microsoft Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - Para 10 do Windows, Windows 8.1 e Windows 8, consulte [instalar o .NET Framework 3.5 no Windows 10, Windows 8.1 e Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
- **Sua versão do Módulo Microsoft Azure Active Directory para Windows PowerShell deve estar desatualizada.** Para verificar, execute o seguinte comando no Office 365 PowerShell ou no Módulo Microsoft Azure Active Directory para Windows PowerShell:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Se o número da versão retornado for menor que o valor 1.0.8070.2, desinstale o Módulo Microsoft Azure Active Directory para Windows PowerShell e instale a versão mais recente usando o link da Etapa 1.
    
- **Se você receber um erro de conexão, confira este tópico:** ["Connect-MsolService: ocorreu exceção do tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    

## <a name="see-also"></a>Confira também

- [Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
- [Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

