---
title: Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/10/2018
ms.audience: ITPro
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
description: 'Resumo: Conecte o Windows PowerShell para todos os serviços do Office 365 em uma única janela do Windows PowerShell.'
ms.openlocfilehash: ffa603ec50c95f5800315eee07b4d01e058852f3
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell

 **Resumo:** Em vez de gerenciar diferentes serviços do Office 365 em janelas separadas de console do PowerShell, é possível conectar-se a todos os serviços do Office 365 e gerenciá-los da janela do console único.
  
Quando você usar o PowerShell para gerenciar o Office 365, é possível ter até cinco sessões diferentes do Windows PowerShell abrir ao mesmo tempo correspondente ao centro de administração do Office 365, SharePoint Online, Exchange Online, Skype para Business Online e a segurança &amp;Centro de conformidade. Com cinco métodos diferentes de conexão em sessões separados do Windows PowerShell, sua área de trabalho pode ser assim:
  
![Cinco consoles do Windows PowerShell em execução ao mesmo tempo](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Isso não é ideal para gerenciar o Office 365 porque você não pode trocar dados entre esses cinco windows para o gerenciamento de cross-service. Este tópico descreve como usar uma única instância do Windows PowerShell a partir do qual você pode gerenciar o Office 365, Skype Business Online, Exchange Online, SharePoint Online e a segurança &amp; Centro de conformidade.

## <a name="before-you-begin"></a>Antes de começar
<a name="BeforeYouBegin"> </a>

Antes de você pode gerenciar tudo do Office 365 de uma única instância do Windows PowerShell, considere os seguintes pré-requisitos:
  
- O Office 365 funcionam ou escola a conta que você usa para esses procedimentos necessidades para ser um membro de uma função de administrador do Office 365. Para obter mais informações, consulte [funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este um requisito para o Office 365 PowerShell, mas não necessariamente para todos os outros serviços do Office 365.
    
- Você pode usar as seguintes versões de 64 bits do Windows:
    
  - Windows 10
    
  - Windows 8.1 ou Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 ou Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Você precisa instalar o Microsoft .NET Framework 4.5. *x* e, em seguida, ambos o Windows Management Framework 3.0 ou o Windows Management Framework 4.0. Para obter mais informações, consulte [Instalando o .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) e [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Você precisa usar uma versão de 64 bits do Windows devido aos requisitos para o Skype para módulo Business Online e outra os módulos do Office 365.
    
- Você precisa instalar os módulos necessários para o Office 365, SharePoint Online e Skype para Business Online:
    
   - [Microsoft Online Service Assistente de conexão para profissionais de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - Windows Azure Active Directory módulo para Windows PowerShell (versão de 64 bits) com o comando **Install-módulo MSOnline** em um prompt de comando elevado do PowerShell.
   - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype para negócios on-line, o módulo do Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell deve ser configurado para executar scripts assinados Skype para Business Online, o Exchange Online e a segurança &amp; Centro de conformidade. Para fazer isso, execute o seguinte comando em uma sessão do Windows PowerShell com privilégios elevados (uma janela do Windows PowerShell para abrir, selecione **Executar como administrador**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Etapas de Conexão ao usar uma senha
<a name="ConnStepsPassword"> </a>

Aqui estão as etapas para se conectar a todos os serviços em uma única janela do PowerShell.
  
1. Abra o Windows PowerShell como um administrador (use **Executar como administrador**).
    
2. Execute este comando e insira seu trabalho do Office 365 ou escola credenciais da conta.
    
  ```
  $credential = Get-Credential
  ```

3. Execute estes comandos para se conectar ao Office 365.
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. Execute estes comandos para se conectar ao SharePoint Online. Substituir _ \<domainhost >_ com o valor real para seu domínio. Por exemplo, para `litwareinc.onmicrosoft.com`, o _ \<domainhost >_ valor é `litwareinc`.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Execute estes comandos para se conectar ao Skype para negócios Online. Um aviso sobre o aumento do `WSMan NetworkDelayms` valor esperado na primeira vez que você se conectar e devem ser ignorados.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Execute estes comandos para se conectar ao Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. Execute estes comandos para se conectar à segurança &amp; Centro de conformidade.
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
  Import-PSSession $SccSession
  ```

Aqui estão todos os comandos em um único bloco. Especifique o nome do seu host do domínio e execute todas elas ao mesmo tempo.
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $SccSession
```
Quando você estiver pronto para fechar a janela do Windows PowerShell para baixo, execute este comando para remover as sessões ativas para Skype para Business Online, Exchange Online, SharePoint Online e a segurança &amp; Centro de conformidade:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Etapas de Conexão ao usar a autenticação multifator
<a name="ConnStepsMFA"> </a>

Aqui estão todos os comandos em um único bloco para se conectar ao AD do Windows Azure, SharePoint Online e Skype para negócios usando a autenticação multifator em uma única janela. Especifique o nome de nome principal (UPN) do usuário de uma conta de administrador global e seu nome de host do domínio e execute todas elas ao mesmo tempo.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
#If you are running Office 365 commands that contain "AzureAd" in their name, use this command:
Connect-AzureAD
#If you are running Office 365 commands that contain "Msol" in their name, comment the preceding command and un-comment the following command:
#Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Para o Exchange Online e a segurança &amp; Centro de conformidade, consulte os tópicos a seguir para se conectar usando a autenticação multifator:

- [Connect to Exchange Online PowerShell usando a autenticação multifator](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell).
- [Conectar-se ao PowerShell do Centro de conformidade usando a autenticação multifator & de segurança do Office 365](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
Observe que, em ambos os casos, você deve se conectar usando sessões separadas do Exchange Online Remote PowerShell módulo.


## <a name="new-to-office-365"></a>Começando a usar o Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Veja também

- [Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
- [Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Gerenciar o SharePoint Online com o Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Gerenciar contas de usuário e licenças usando o PowerShell do Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Use o Windows PowerShell para criar relatórios no Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
