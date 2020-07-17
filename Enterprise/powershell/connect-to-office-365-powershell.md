---
title: Conectar-se ao PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/30/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Conecte-se à sua organização do Office 365 usando o PowerShell do Office 365 para realizar tarefas do centro de administração a partir da linha de comando.
ms.openlocfilehash: 0906da2b8773973236bc8cb6ef273d1a14528bfd
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997417"
---
# <a name="connect-to-office-365-powershell"></a>Conectar-se ao PowerShell do Office 365

O Office 365 PowerShell permite gerenciar as configurações do Office 365 da linha de comando. Conectar-se ao Office 365 PowerShell é um processo simples em que você instala o software necessário e se conecta à sua organização do Office 365. 

Existem duas versões do módulo do PowerShell usadas para se conectar ao Office 365 e administrar contas de usuários, grupos e licenças:

- O Azure Active Directory PowerShell para Graph (inclui **AzureAD** no nome dos cmdlets)
- O Módulo Microsoft Azure Active Directory para Windows PowerShell (inclui **MSol** no nome dos cmdlets) 

A partir da data deste artigo, o Azure Active Directory PowerShell para o módulo do Graph não substituiu completamente a funcionalidade dos cmdlets do Módulo Microsoft Azure Active Directory para o módulo do Windows PowerShell para a administração de usuários, grupos e licenças. Em muitos casos, é necessário usar as duas versões. As duas versões podem ser instaladas com segurança no mesmo computador.

## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

Você pode usar as seguintes versões do Windows:
    
  - Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1

    > [!NOTE]
    > Para o módulo do PowerShell do Azure Active Directory para Graph, você deve usar o PowerShell versão 5.1 ou posterior. Para o módulo do PowerShell do Azure Active Directory para módulo do Windows PowerShell, você deve usar o PowerShell versão 5.1 ou posterior até o PowerShell versão 6. Você não pode usar o PowerShell versão 7. Para Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, e Windows Server 2008 R2 SP1, baixe e instale o [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616). 
    
    > [!NOTE]
    > Use uma versão de 64 bits do Windows, pois o suporte para a versão de 32 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell foi descontinuada em outubro de 2014.
    
Esses procedimentos são destinados aos usuários membros de uma função de administrador do Office 365. Para saber mais, confira [Sobre as funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Conecte-se ao Azure Active Directory PowerShell para o módulo do Graph.

Os comandos no módulo do PowerShell do Azure Active Directory para Graph têm o **AzureAD** no nome do cmdlet. Você pode instalar o módulo do [PowerShell do Azure Active Directory para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) ou o [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).

Para os procedimentos que exigem os novos cmdlets no Azure Active Directory PowerShell para o módulo do Graph, use estas etapas para instalar o módulo e se conectar à sua assinatura do Office 365.

>[!Note]
>Confira o [Azure Active Directory PowerShell para o módulo do Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obter mais informações sobre o suporte a diferentes versões do Microsoft Windows.
>

### <a name="step-1-install-required-software"></a>Etapa 1: instalar o software necessário

Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.
  
1. Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).
    
2. Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:
    
  ```powershell
  Install-Module -Name AzureAD
  ```

Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione Enter.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Etapa 2: conectar-se ao Azure AD da sua assinatura do Office 365

Para se conectar ao Azure AD da sua assinatura do Office 365 com um nome de conta e senha, ou com autenticação multifator (MFA), execute um destes comandos de um prompt de comando do Windows PowerShell (não é necessário ser privilegiado).

|||
|:-------|:-----|
| **Nuvem do Office 365** | **Comando** |
| Office 365 no Mundo (+GCC) | `Connect-AzureAD` |
| Office 365 operado pela 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 U.S. Government DoD e Office 365 U.S. Government GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Na caixa de diálogo **Entrar na sua conta**, digite seu nome de usuário e senha para uma conta corporativa ou de estudante do Office 365, e clique em **OK**.

Se você estiver usando uma MFA, siga as instruções das caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.

Depois de se conectar, você pode usar os cmdlets do [módulo do Azure Active Directory PowerShell para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Conecte com o Módulo Microsoft Azure Active Directory para Windows PowerShell

Os comandos no Módulo Microsoft Azure Active Directory para Windows PowerShell têm **Msol** no nome do cmdlet.

O PowerShell versão 7 e posterior não oferece suporte ao Módulo do Microsoft Azure Active Directory para módulo do Windows PowerShell e cmdlets com **Msol** no nome. Para o PowerShell versão 7 e posterior, você deve usar o módulo do PowerShell do Azure Active Directory para Graph ou o Azure PowerShell.

O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome. Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell. 
    
### <a name="step-1-install-required-software"></a>Etapa 1: instalar o software necessário

Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.
  
1.  Se você não estiver executando o Windows 10, instale a versão de 64 bits do assistente de conexão do Microsoft Online Services: [Assistente de conexão do Microsoft Online Services para profissionais de ti RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Instale o Módulo Microsoft Azure Active Directory para Windows PowerShell seguindo estas etapas:
    
  - Abra um prompt de comando privilegiado do Windows PowerShell (execute o Windows PowerShell como administrador).
  - Execute o comando **Install-Module MSOnline**.
  - Se solicitado a instalar o provedor de NuGet, digite **Y** e pressione Enter.
  - Se solicitado a instalar o módulo de PSGallery, digite **Y** e pressione Enter.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Etapa 2: conectar-se ao Azure AD da sua assinatura do Office 365

Para se conectar ao Azure AD da sua assinatura do Office 365 com um nome de conta e senha, ou com autenticação multifator (MFA), execute um destes comandos de um prompt de comando do Windows PowerShell (não é necessário ser privilegiado).

|||
|:-------|:-----|
| **Nuvem do Office 365** | **Comando** |
| Office 365 no Mundo (+GCC) | `Connect-MsolService` |
| Office 365 operado pela 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 U.S. Government DoD e Office 365 U.S. Government GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

Na caixa de diálogo **Entrar na sua conta**, digite seu nome de usuário e senha para uma conta corporativa ou de estudante do Office 365, e clique em **OK**.

Se você estiver usando uma MFA, siga as instruções das caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.

### <a name="how-do-you-know-this-worked"></a>Como saber se funcionou?

Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.
  
Caso você receba erros, verifique os seguintes requisitos:
  
- **Senha incorreta é um problema comum**. Execute a Etapa 2 novamente. e preste muita atenção ao nome de usuário e à senha inseridos.
    
- **O Módulo Microsoft Azure Active Directory para Windows PowerShell requer que o recurso do Microsoft .NET Framework 3.5.* x* esteja habilitado em seu computador**. É provável que seu computador tenha uma versão mais recente instalada (por exemplo, 4 ou 4.5.* x*), mas a compatibilidade com versões anteriores do .NET Framework pode ser habilitada ou desabilitada. Para mais informações, confira os seguintes tópicos:
    
  - Para Windows Server 2012 ou Windows Server 2012 R2, confira [Habilitar o .NET Framework 3.5 usando o Assistente de Adição de Funções e Recursos](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Para Windows 7 ou Windows Server 2008 R2, confira [Não é possível abrir o Módulo Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - Para Windows 10, Windows 8.1 e Windows 8, confira [Instalar o .NET Framework 3.5 no Windows 10, Windows 8.1 e Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)

  
- **Sua versão do Módulo Microsoft Azure Active Directory para Windows PowerShell deve estar desatualizada.** Para verificar, execute o seguinte comando no Office 365 PowerShell ou no Módulo Microsoft Azure Active Directory para Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Se o número da versão retornado for menor do que o valor 1.0.8070.2, desinstale o módulo Microsoft Azure Active Directory para Windows PowerShell e instale da etapa 1 acima.

- **Se você receber um erro de conexão, confira este tópico:** ["Connect-MsolService: ocorreu exceção do tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
- **Se você receber a mensagem de erro "Get-Item : Não é possível encontrar o caminho", use este comando:** 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a>Confira também

- [Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
- [Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
