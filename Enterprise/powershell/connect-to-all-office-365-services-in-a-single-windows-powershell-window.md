---
title: Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Resumo: Conecte o Windows PowerShell a todos os serviços do Office 365 em uma única janela do Windows PowerShell.'
ms.openlocfilehash: f64a29bb0594694c5a6b6e2dff8d0f7611fdf11e
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707058"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell

 **Resumo:** Em vez de gerenciar diferentes serviços do Office 365 em janelas de console do PowerShell separadas, você pode se conectar a todos os serviços do Office 365 e gerenciá-los em uma única janela do console.
  
Quando você usa o PowerShell para gerenciar o Office 365, é possível ter até cinco sessões do Windows PowerShell diferentes abertas ao mesmo tempo que corresponde ao centro de administração do Microsoft 365, ao SharePoint Online, ao Exchange Online, ao Skype for Business &amp; online e ao centro de conformidade de segurança. Com cinco métodos de conexão diferentes em sessões separadas do Windows PowerShell, sua área de trabalho pode ter a seguinte aparência:
  
![Cinco consoles do Windows PowerShell em execução ao mesmo tempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Isso não é ideal para gerenciar o Office 365 porque não é possível trocar dados entre essas cinco janelas para gerenciamento entre serviços. Este tópico descreve como usar uma única instância do Windows PowerShell a partir da qual você pode gerenciar o Office 365, o Skype for Business Online, o Exchange Online, o SharePoint &amp; online e o centro de conformidade de segurança.

>[!Note]
>Este artigo atualmente contém apenas os comandos para se conectar à nuvem do Office 365 Worldwide (+ GCC). As observações adicionais fornecem links para artigos com informações sobre como se conectar às outras nuvens do Office 365.
>

## <a name="before-you-begin"></a>Antes de começar

Antes de poder gerenciar todo o Office 365 de uma única instância do Windows PowerShell, considere os seguintes pré-requisitos:
  
- O Office 365conta comercial ou escolar que você usa para esses procedimentos precisa ser um membro de uma função de administrador do Office 365. Para saber mais, veja [Sobre as funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Isso é um requisito para o Office 365 PowerShell, não necessariamente para todos os outros serviços do Office 365.
    
- Você pode usar as seguintes versões de 64 bits do Windows:
    
  - Windows 10
    
  - Windows 8.1 ou Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 ou Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Você precisa instalar o Microsoft .NET Framework 4,5. *x* e, em seguida, o Windows management Framework 3,0 ou o Windows management Framework 4,0. Para obter mais informações, consulte [instalando o .NET Framework e o](https://go.microsoft.com/fwlink/p/?LinkId=257868) [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Você precisa usar uma versão de 64 bits do Windows devido aos requisitos para o módulo do Skype for Business Online e um dos módulos do Office 365.
    
- Você precisa instalar os módulos necessários para o Azure AD, o SharePoint Online e o Skype for Business Online:
    
   - [Azure Active Directory v2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [Shell de gerenciamento do SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype for Business Online, módulo do Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  O Windows PowerShell precisa ser configurado para executar scripts assinados para o Skype for Business Online, o Exchange Online e &amp; o centro de conformidade de segurança. Para fazer isso, execute o seguinte comando em uma sessão elevada do Windows PowerShell (uma janela do Windows PowerShell que você abre selecionando **Executar como administrador**).
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Etapas de conexão ao usar uma senha

Aqui estão as etapas para se conectar a todos os serviços em uma única janela do PowerShell.
  
1. Abra o Windows PowerShell como administrador (use **Executar como administrador**).
    
2. Execute este comando e insira suas credenciais de conta corporativa ou de estudante do Office 365.
    
  ```powershell
  $credential = Get-Credential
  ```

3. Execute este comando para se conectar ao AD (Active Directory) do Azure usando o módulo do PowerShell do Azure Active Directory para Graph.
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  Como alternativa, se você estiver usando o módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell, execute este comando.
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

4. Execute estes comandos para se conectar ao SharePoint Online. Substitua _ \<domainhost>_ pelo valor real do seu domínio. Por exemplo, para "litwareinc.onmicrosoft.com", o valor de _ \<>domainhost_ é "litwareinc".
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Execute estes comandos para se conectar ao Skype for Business online. Um aviso sobre o aumento `WSMan NetworkDelayms` do valor é esperado na primeira vez que você se conecta e deve ser ignorado.
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Execute estes comandos para se conectar ao Exchange Online.
    
  ```powershell
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
>Para conectar-se ao Exchange Online para nuvens do Office 365 diferentes do mundo inteiro, confira [conectar-se ao PowerShell do Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
>

7. Execute estes comandos para se conectar ao centro &amp; de conformidade de segurança.
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>Para se conectar ao centro &amp; de conformidade de segurança para nuvens do Office 365 diferentes do mundo, confira [conectar-se ao office 365 segurança & centro de conformidade do PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
>

Aqui estão todos os comandos em um único bloco ao usar o módulo PowerShell do Azure Active Directory para Graph. Especifique o nome do seu host de domínio e, em seguida, execute todos ao mesmo tempo.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Como alternativa, aqui estão todos os comandos em um único bloco ao usar o módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell. Especifique o nome do seu host de domínio e, em seguida, execute todos ao mesmo tempo.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Quando estiver pronto para fechar a janela do Windows PowerShell, execute este comando para remover as sessões ativas para o Skype for Business Online, o Exchange Online, o SharePoint Online e &amp; o centro de conformidade de segurança:
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Etapas de conexão ao usar a autenticação multifator

Aqui estão todos os comandos em um único bloco para se conectar ao Azure AD, SharePoint Online e Skype para buiness usando a autenticação multifator em uma única janela usando o módulo do PowerShell do Azure Active Directory para Graph. Especifique o nome UPN (nome principal de usuário) de uma conta de usuário e o nome de host do domínio e, em seguida, execute todos os itens de uma só vez.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
```

Como alternativa, aqui estão todos os comandos ao usar o módulo Microsoft Azure Active Directory para Windows PowerShell.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
```

Para o Exchange Online e o &amp; centro de conformidade de segurança, consulte os seguintes tópicos para se conectarem usando a autenticação multifator:

- [Conectar-se ao PowerShell do Exchange Online usando a autenticação multifator](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Conectar-se ao centro de conformidade do Office 365 Security & o PowerShell usando a autenticação multifator](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
Observe que, em ambos os casos, você deve se conectar usando sessões separadas do módulo do PowerShell remoto do Exchange Online.


## <a name="see-also"></a>Confira também

- [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md)
- [Gerenciar o SharePoint Online com o Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Gerenciar contas de usuário e licenças usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Use o Windows PowerShell para criar relatórios no Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
