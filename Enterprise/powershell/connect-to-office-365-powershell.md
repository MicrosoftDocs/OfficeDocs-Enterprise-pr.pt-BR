---
title: Conectar-se ao PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumo: Conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para executar tarefas da central de administração a partir da linha de comando.'
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639772"
---
# <a name="connect-to-office-365-powershell"></a>Conectar-se ao PowerShell do Office 365

 **Resumo:** Conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para executar tarefas de administração a partir da linha de comando.
  
O Office 365 PowerShell permite que você gerencie suas configurações do Office 365 a partir da linha de comando. Conectar-se ao Office 365 PowerShell é um processo simples onde você instala o software necessário e, em seguida, conecta-se à sua organização do Office 365. 

Há duas versões do módulo do PowerShell que você usa para se conectar ao Office 365 e administrar contas de usuário, grupos e licenças:

- PowerShell do Azure Active Directory para Graph (os cmdlets incluem **AzureAD** em seu nome) 
- Módulo do Microsoft Azure Active Directory para Windows PowerShell (os cmdlets incluem **MSol** em seu nome) 

A partir da data deste artigo, o módulo PowerShell do Azure Active Directory para Graph não substitui completamente a funcionalidade nos cmdlets do módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell para administração de usuários, grupos e licenças . Em muitos casos, você precisa usar ambas as versões. Você pode instalar com segurança ambas as versões no mesmo computador.

> [!TIP]
> **Novo no PowerShell? ** Veja um [vídeo de visão geral do PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), apresentado pelo LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

- Tempo estimado para conclusão: 5 minutos
    
- Você pode usar as seguintes versões do Windows:
    
  - Windows 10, Windows 8,1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Use uma versão de 64 bits do Windows, pois o suporte para a versão de 32 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell foi descontinuada em outubro de 2014.
    
-  Esses procedimentos se destinam a usuários que são membros de uma função de administrador do Office 365. Para saber mais, veja [Sobre as funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Conectar-se ao Azure Active Directory PowerShell para o módulo do Graph

Os comandos no módulo do [PowerShell do Azure Active Directory para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) têm **AzureAD** em seu nome de cmdlet.

Para procedimentos que exigem os novos cmdlets no módulo PowerShell do Azure Active Directory para Graph, use estas etapas para instalar o módulo e se conectar à sua assinatura do Office 365.

>[!Note]
>Confira [Azure Active Directory PowerShell for Graph Module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obter informações sobre o suporte para diferentes versões do Microsoft Windows.
>

### <a name="step-1-install-required-software"></a>Etapa 1: Instalar o software necessário

Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.
  
1. Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).
    
2. Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:
    
  ```
  Install-Module -Name AzureAD
  ```

Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione ENTER.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Etapa 2: conectar-se ao Azure AD para sua assinatura do Office 365

Para se conectar ao Azure AD para sua assinatura do Office 365 com um nome de conta e senha ou com a *autenticação multifator (MFA)*, execute um destes comandos a partir de um prompt de comando do Windows PowerShell (ele não precisa ser elevado).

|||
|:-------|:-----|
| **Nuvem do Office 365** | **Command** |
| Office 365 em todo o mundo (+ GCC) | `Connect-AzureAD` |
| Office 365 operado por 21 vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 governo dos EUA DoD e Office 365 governo dos EUA | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Na caixa de diálogo **entrar em sua conta** , digite o nome de usuário e a senha da conta corporativa ou de estudante do Office 365 e clique em **OK**.

Se você estiver usando a MFA, siga as instruções nas caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.


Após a conexão, você pode usar os novos cmdlets para o [módulo do PowerShell do Azure Active Directory para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

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
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Etapa 2: conectar-se ao Azure AD para sua assinatura do Office 365

Para se conectar ao Azure AD para sua assinatura do Office 365 com um nome de conta e senha ou com a *autenticação multifator (MFA)*, execute um destes comandos a partir de um prompt de comando do Windows PowerShell (ele não precisa ser elevado).

|||
|:-------|:-----|
| **Nuvem do Office 365** | **Command** |
| Office 365 em todo o mundo (+ GCC) | `Connect-MsolService` |
| Office 365 operado por 21 vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 governo dos EUA DoD e Office 365 governo dos EUA | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

Na caixa de diálogo **entrar em sua conta** , digite o nome de usuário e a senha da conta corporativa ou de estudante do Office 365 e clique em **OK**.

Se você estiver usando a MFA, siga as instruções nas caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.

### <a name="how-do-you-know-this-worked"></a>Como saber se funcionou?

Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.
  
Caso você receba erros, verifique os seguintes requisitos:
  
- **Um problema comum é uma senha incorreta**. Execute a etapa 2 novamente. e preste atenção ao nome de usuário e à senha que você digitou.
    
- * *O módulo Microsoft Azure Active Directory para Windows PowerShell exige que o Microsoft .net Framework 3,5.* o recurso x * está habilitado no computador * *. É provável que seu computador tenha uma versão mais recente instalada (por exemplo, 4 ou 4,5.* x *), mas a compatibilidade com versões anteriores do .NET Framework pode ser habilitada ou desabilitada. Para mais informações, confira os seguintes tópicos:
    
  - Para Windows Server 2012 ou Windows Server 2012 R2, confira [Habilitar o .NET Framework 3.5 usando o Assistente de Adição de Funções e Recursos](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Para Windows 7 ou Windows Server 2008 R2, confira [Não é possível abrir o módulo Microsoft Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - Para Windows 10, Windows 8,1 e Windows 8, consulte [instalar o .NET Framework 3,5 no Windows 10, Windows 8,1 e Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
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

