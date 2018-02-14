---
title: "Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell"
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
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "Resumo: Conecte o Windows PowerShell para todos os serviços do Office 365 em uma única janela do Windows PowerShell."
ms.openlocfilehash: d11487ae1c95cb0d36221e7ce572ed55052d98eb
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
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
    
    * Você precisa instalar o Microsoft .NET Framework 4.5. _x_ e, em seguida, ambos o Windows Management Framework 3.0 ou o Windows Management Framework 4.0. Para obter mais informações, consulte [Instalando o .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) e [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Você precisa usar uma versão de 64 bits do Windows devido aos requisitos para o Skype para módulo Business Online e outra os módulos do Office 365.
    
- Você precisa instalar os módulos necessários para o Office 365, SharePoint Online e Skype para Business Online:
    
  - [Microsoft Online Service Assistente de conexão para profissionais de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [Windows Azure Active Directory módulo para Windows PowerShell (versão de 64 bits)](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [Skype para negócios on-line, o módulo do Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell deve ser configurado para executar scripts assinados Skype para Business Online, o Exchange Online e a segurança &amp; Centro de conformidade. Para fazer isso, execute o seguinte comando em uma sessão do Windows PowerShell com privilégios elevados (uma janela do Windows PowerShell para abrir, selecione **Executar como administrador**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a>A versão curta (instruções sem explicações)
<a name="ShortVersion"> </a>

Esta seção apresenta as etapas de conexão sem explicações detalhadas. Se você tiver dúvidas ou se quiser obter mais informações, leia o restante do tópico. Os números de etapa aqui correspondem às seções de etapas numeradas no restante do tópico:
  
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
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. Execute estes comandos para se conectar à segurança &amp; Centro de conformidade.
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> O prefixo de texto "cc" é adicionado a *todas as* segurança &amp; nomes de cmdlet do Centro de conformidade para que você possa executar cmdlets que existem no Exchange Online e a segurança &amp; Centro de conformidade na mesma sessão do Windows PowerShell. Por exemplo, **Get-RoleGroup** torna-se **Get-ccRoleGroup** na segurança &amp; Centro de conformidade.
  
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
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

Quando você estiver pronto para fechar a janela do Windows PowerShell para baixo, execute este comando para remover as sessões ativas para Skype para Business Online, Exchange Online, SharePoint Online e a segurança &amp; Centro de conformidade:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>A versão longa (instruções com explicações detalhadas)
<a name="LongVersion"> </a>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a>Etapa 1: abrir o Windows PowerShell como administrador
<a name="Step1"> </a>

Se você estiver executando o Windows 10, Windows 8, Windows 8.1, 2016 do Windows Server, Windows Server 2012 R2 ou Windows Server 2012 R2, faça o seguinte:
  
1. Use qualquer um desses métodos para localizar o atalho do **Windows PowerShell**:
    
  - Na tela Iniciar, clique em uma área vazia e digite o Windows PowerShell.
    
  - Na área de trabalho ou tela Iniciar, pressione o Windows chave + Q. No botão Pesquisar, digite o Windows PowerShell.
    
  - Na área de trabalho ou tela Iniciar, mova o cursor ao canto superior direito ou passe o dedo da borda direita da tela para mostrar os botões da esquerda. Selecione o botão Pesquisar e insira o Windows PowerShell.
    
2. Nos resultados, clique com botão direito **Do Windows PowerShell**e selecione **Executar como administrador**.
    
3. Se a caixa de diálogo **Controle de conta de usuário** for exibida, selecione **Sim** para verificar que você deseja executar o Windows PowerShell sob as credenciais de administrador.
    
Se você estiver executando o Windows 7 SP1 (ou Windows Server 2008 R2 SP1), faça o seguinte:
  
1. No menu **Iniciar** , selecione **Todos os programas** > **Acessórios** > **Do Windows PowerShell**. Com o botão direito **Do Windows PowerShell**e, em seguida, selecione **Executar como administrador**.
    
2. Se a caixa de diálogo **Controle de conta de usuário** for exibida, selecione **Sim** para verificar que você deseja executar o Windows PowerShell sob as credenciais de administrador.
    
Você deve executar o Windows PowerShell como administrador. Se não fizer isso, você vai receber uma mensagem de erro semelhante a esta quando você tenta importar um dos módulos necessários.
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

A única maneira de remediar a situação é fechar o Windows PowerShell e reiniciá-lo como um administrador. Aqui está uma maneira rápida e fácil saber se você estiver executando o Windows PowerShell como um administrador: prompt é `PS C:\Windows\System32>`, e não `PS C:\Users\YourUserName>`.

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a>Etapa 2: Criar um objeto de credenciais do Windows PowerShell
<a name="Step2"> </a>

O objeto de credenciais oferece uma maneira criptografada para passar o seu nome de usuário e senha para o Windows PowerShell. Para criar um objeto de credenciais, execute o seguinte comando no Windows PowerShell.
  
```
$credential = Get-Credential
```

> [!NOTE]
>  `$credential`é uma variável que armazenará o objeto de credenciais. Você não precisa nomeie a variável `$credential`, mas fazer isso torna mais fácil de lembrar qual variável contém o objeto de credenciais. (E que é importante, porque vai reutilizar a essa variável várias vezes). Que também facilitará a seguir nossos exemplos, pois este artigo sempre usarão `$credential` para representar o objeto de credenciais.
  
Em seguida, o Windows PowerShell exibirá uma caixa de diálogo parecida com esta.
  
![Caixa de diálogo de solicitação de credenciais em branco.](images/o365_powershell_empty_credentials_box.png)
  
Digite seu trabalho ou nome de usuário de conta na caixa **nome de usuário** , usando o formato _username@domainname_ (por exemplo, kenmyer@litwareinc.onmicrosoft.com); da escola Digite sua senha na caixa **senha** ; e, em seguida, clique em **Okey**:
  
![Conclusão da caixa de diálogo de solicitação de credenciais.](images/o365_powershell_completed_credentials_box.png)
  
Observe que, como normalmente é o caso, você não verá qualquer tipo de confirmação de que o objeto de credenciais foi criado. (Windows PowerShell geralmente informa quando as coisas dão erradas, mas não sempre diz quando coisas ir para a direita.) Se você quiser verificar se o objeto de credenciais foi criado, digite o seguinte no Windows PowerShell e pressione Enter.
  
```
$credential
```

Depois você deve ver algo como o seguinte na tela:
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

Uma coisa deve ter em mente aqui é que o cmdlet [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) apenas cria o objeto de credenciais; ele não autenticar você ou caso contrário, verifique se o nome de usuário e a senha que você forneceu estão corretas. Por exemplo, suponha que você digitado incorretamente o nome de usuário como kenmyer@litwareinc.onmicrosoft.com. Se você fizer isso, **Get-Credential** criará um objeto de credenciais usando esse nome de usuário e sem verificar ver se esse é realmente um nome de usuário válido. Você não sabe se você tiver criado um objeto de credenciais válidas realmente até que você realmente os utilizam esse objeto para tentar se conectar aos serviços do Office 365.
  
### <a name="step-3-connect-to-office-365"></a>Etapa 3: Conectar-se ao Office 365
<a name="Step3"> </a>

Começaremos conectando-se ao Office 365 em si. 
  
A primeira coisa que precisamos fazer aqui é importar o módulo do Office 365 (o Microsoft Azure Active Directory módulo para Windows PowerShell). Para fazer isso, execute este comando no Windows PowerShell.
  
```
Import-Module MsOnline
```

No entanto, execute o comando a seguir para verificar se o módulo foi importado.
  
```
Get-Module
```

Em algum lugar na lista de módulos retornados por esse comando você verá algo semelhante isso: `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.
  
Se você vir `MSOnline` listado, isso significa que tudo correu.
  
Com o objeto de credenciais criado (consulte [etapa 2: criar um objeto de credenciais do Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) e com o `MsOnline` módulo carregado, podemos agora pode se conectar ao Office 365 usando o cmdlet [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) e o comando a seguir.
  
```
Connect-MsolService -Credential $credential
```

Observe que tudo o que você precisa fornecer é o objeto de credenciais ( `$credential`). Com base nessas credenciais, Office 365 irá automaticamente conectá-lo ao domínio correto. Você não precisará especificar o nome do seu domínio ao se executar o **Connect-MsolService**.
  
Para verificar que você realmente *estiver* conectado ao Office 365, execute este comando.
  
```
Get-MsolDomain
```

Como resposta, você deve receber alguma coisa parecida com:
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a>Etapa 4: Conectar ao SharePoint Online
<a name="Step4"> </a>

Importe o módulo do SharePoint Online com o seguinte comando:
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

A opção _DisableNameChecking_ suprime esse aviso.
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

Para se conectar ao SharePoint Online, você precisa fornecer duas partes de informações: suas credenciais e a URL do site de administração do SharePoint Online. A parte de credenciais é fácil: já armazenamos que na variável `$credential` (consulte [etapa 2: criar um objeto de credenciais do Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). Para a URL do seu site de administração, que é fácil de determinar, também. Suponha que o seu nome de domínio do Office 365 é `litwareinc.onmicrosoft.com`.
  
Para determinar a URL do site de administração, faça o seguinte:
  
1. Iniciar usando o prefixo `https://`.
    
2. Adicione a parte de host de domínio do seu nome de domínio. Por exemplo, para `litwareinc.onmicrosoft.com`, o nome de host do domínio é `litwareinc`. Para `contoso.onmicrosoft.com`, o nome de host do domínio é `contoso`.
    
3. Adicione um hífen (-) seguido `admin.sharepoint.com`.
    
Em outras palavras:
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
Após ter construído a URL, em seguida, você pode usar essa URL e seu objeto de credenciais para se conectar ao SharePoint Online. Chame o cmdlet [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) , usando um comando semelhante a este.
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

Para verificar que a conexão foi feita, execute o seguinte comando no Windows PowerShell.
  
```
Get-SPOSite
```

Você deve obter uma lista de todos os sites do SharePoint Online. Aqui está um exemplo:
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

Comandos do seu Office 365 (aqueles descrito em [etapa 3: conectar ao Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) será trabalho ainda. (Tente executar **Get-MsolUser**e veja por si mesmo). Isso significa que agora você pode gerenciar Office 365 e o SharePoint Online da mesma instância do Windows PowerShell.
  
### <a name="step-5-connect-to-skype-for-business-online"></a>Etapa 5: Conectar-se ao Skype for Business Online
<a name="Step5"> </a>

Conectando a Skype para Business Online (e para o Exchange Online ou a segurança &amp; Centro de conformidade) é diferente de conectar-se ao Office 365 ou no SharePoint Online. Isso acontece porque o Skype para cmdlets Business Online e o Exchange Online não obter instalado no computador, semelhante a como o Office 365 e os cmdlets do SharePoint Online. Em vez disso, cada vez que entrar, os cmdlets apropriados são temporariamente copiados para seu computador. Quando você aprovar, esses cmdlets, em seguida, são removidos do seu computador.
  
Para se conectar ao Skype para Business Online, você precisa importar o Skype para módulo Business Online. Para fazer isso, execute este comando.
  
```
Import-Module SkypeOnlineConnector
```

Na primeira vez que fizer isso, você visualizará a seguinte mensagem de aviso, que pode ignorar com segurança.
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

Depois que o módulo foi importado, execute este comando.
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

Criamos uma sessão PowerShell remota. Nesse caso, isso significa que podemos se conectou a uma instância do Windows PowerShell em execução em um dos servidores do Office 365. 
  
Embora que fizemos uma conexão para o Office 365, podemos ainda não baixou os scripts, cmdlets e outros itens necessários para gerenciar Skype para Business Online. Para fazer isso, temos que executar este comando.
  
```
Import-PSSession $sfboSession
```

Quando você importa a sessão do Windows PowerShell, você deverá ver uma barra de progresso semelhante ao seguinte, uma barra de progresso que emite um relatório sobre todos o Skype para Business Online cmdlets sendo importados para o seu computador.
  
![Barra de progresso do Lync Online.](images/o365_powershell_lync_progress_bar.png)
  
Quando a barra de progresso desaparece, você deve então ver saída semelhante à seguinte:
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a>Etapa 6: Conectar-se ao Exchange Online
<a name="Step6"> </a>

Execute este comando, que cria uma sessão remota do Windows PowerShell com o Exchange Online.
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> Por que é o comando para conectar-se ao Exchange Online mais complicados do que o comando para conectar Skype para Business Online? Tecnicamente, não é: os dois comandos façam exatamente a mesma coisa. No entanto, o Skype para equipe Business Online criado seu próprio cmdlet — **New-CsOnlineSession** — que oculta alguns dos parâmetros (como _a autenticação_ e _AllowRedirection_) que são usados durante a conexão com o Exchange Online. Em vez de exigir que você digitar essa informação sozinho, os parâmetros de _autenticação_ e _AllowRedirection_ efetivamente são internos para o cmdlet **New-CsOnlineSession** . Você precisa digitar esses parâmetros durante a conexão com o Exchange Online, como o Exchange Online usa o cmdlet [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) padrão para se conectar ao Office 365. A desvantagem é que você tenha um pouco mais de digitação para fazer. A vantagem é que você não precisa baixar e instalar um módulo do Exchange Online.
  
Agora, tudo o que você deve fazer é importar nesta sessão remota, exatamente como fizemos com Skype para negócios Online.
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

Você deve ver algo como o seguinte na tela.
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

Agora tente executar este comando:
  
```
Get-AcceptedDomain
```

Em troca, você deverá ver informações sobre seus domínios do Office 365 que estiverem configurados para endereços de email no Exchange Online.
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a>Etapa 7: Conectar à segurança &amp; Centro de conformidade
<a name="Step7"> </a>

A segurança &amp; Centro de conformidade é um serviço no Office 365 que permite que você para gerenciar recursos de conformidade de um local. Para obter mais informações, consulte o [Centro de conformidade do Office 365](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).
  
As instruções de conexão para a segurança &amp; Centro de conformidade são muito semelhantes aos para Exchange Online, mas com um pouco, que você verá em breve.
  
Execute este comando, que cria uma sessão PowerShell remota com a segurança &amp; Centro de conformidade.
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

Agora execute este comando:
  
```
Import-PSSession $ccSession -Prefix cc
```

Novamente, esse comando é muito semelhante ao comando para o Exchange Online. A opção _DisableNameChecking_ não é necessária porque não há nenhum verbo não aprovado na segurança &amp; Centro de conformidade. Mas e quanto adicionais ou `-Prefix cc` parâmetro e valor? É o pouco que nós dissemos sobre.
  
O Exchange Online e a segurança &amp; Centro de conformidade compartilhar alguns cmdlets que possuem exatamente os mesmos nomes e fornecer a mesma funcionalidade. **Get-RoleGroup** é um exemplo.
  
O que acontece se você tentar importar duas sessões que contêm cmdlets com o mesmo nome? Eles entrarem em conflito. Você receberá uma mensagem de aviso amarelo ganhar que diz, `WARNING: Proxy creation has been skipped for the following command:` seguido pela lista de cmdlets conflitantes que não puderam ser importados. O resultado final? É possível executar **Get-RoleGroup** no Exchange Online porque você lá conectado pela primeira vez, mas não é possível executar **Get-RoleGroup** na segurança &amp; conformidade centraliza porque você lá conectado última e os cmdlets conflitantes recusou a ser importado.
  
A maneira mais fácil para lidar com esse problema é adicionar um prefixo de texto arbitrário à segurança importada &amp; cmdlets do Centro de conformidade. Fizemos essa usando o parâmetro _Prefix_ com o valor "cc" no cmdlet **Import-PSSession** . O que que fazer para nós? Eliminava os conflitos alterando (ligeiramente) a segurança &amp; nomes de cmdlet do Centro de conformidade para esta sessão. Todas a segurança importada &amp; cmdlets do Centro de conformidade agora começar com "cc" no substantivo do nome do cmdlet (à direita do "-"). Por exemplo, o cmdlet **Get-RoleGroup** contenciosos torna-se **Get-ccRoleGroup** para a segurança &amp; Centro de conformidade para que ele não fique em conflito com **Get-RoleGroup** para Exchange Online.
  
A desvantagem?  *Todos os*  Segurança &amp; nomes de cmdlet do Centro de conformidade recebem o prefixo "cc" — mesmo exclusivos cmdlets que ele não é necessário. Por exemplo, **Get-ComplianceSearch** torna-se **Get-ccComplianceSearch** , mesmo que não haja nenhuma dessas cmdlet no Exchange Online. É um pouco de um problema, mas não é tão ruim ao considerar os benefícios do gerenciamento de todos os serviços do Office 365 em uma única sessão do Windows PowerShell. Lembre-se adicionar "cc" para os nomes de cmdlet para todos os procedimentos na segurança &amp; Centro de conformidade.
  
Se tudo correr bem, você verá algo semelhante a isso:
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

Agora você tem liberdade para gerenciar todos os serviços do Office 365 em uma única sessão do Windows PowerShell.
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a>Etapa 8: Encerrar normalmente suas sessões do PowerShell
<a name="Step8"> </a>

Se você apenas fechar a janela do Windows PowerShell, sua Skype para conexão remota Business Online permanece ativa para os próximas 15 minutos ou mais. Porque Skype para Business Online limita o número de conexões simultâneas que qualquer pessoa ou qualquer um domínio pode ter aberto, que poderia ser um problema. Com Skype para Business Online, um administrador individual pode ter, no máximo, três conexões abertas de uma só vez, e um domínio pode ter um máximo de nove conexões abertas. Se você entrar no Skype para Business Online e saia sem fechar corretamente a sessão, essa sessão permanece aberta para os próximas 15 minutos ou mais. Como resultado, que é uma conexão menos disponível para você ou outros administradores em seu domínio.
  
Em vez disso, vamos fechar as sessões remotas para Skype para Business Online, o Exchange Online e a segurança &amp; conformidade centraliza normalmente. Antes de fazer isso, execute este comando.
  
```
Get-PSSession
```

O cmdlet [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) deve mostrar a você possui pelo menos três sessões remotas abrir, um para Skype para Business Online, um para o Exchange Online e outro para a segurança &amp; Centro de conformidade (é possível você poderia ter mais de três remota sessões em execução, dependendo se você usou esta instância do Windows PowerShell para se conectar ao algo diferente, além de serviços do Office 365). Você verá algo semelhante ao seguinte.
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

Para fechar a essas três sessões, execute estes comandos um de cada vez. O primeiro comando fecha o Skype para sessão Business Online, o segundo fecha a sessão do Exchange Online, e a terceira fecha a segurança &amp; sessão do Centro de conformidade.
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

Se você executar o cmdlet **Get-PSSession** agora, você deverá ver nada nisso (a menos que você tenha outras conexões remotas ativas em funcionamento).
  
![Console do Windows PowerShell com nenhuma sessão remota.](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> Se você preferir fechar todas as suas sessões remotas ao mesmo tempo, você pode usar este comando: >`Get-PSSession | Remove-PSSession`
  
Caso você tente executar um cmdlet de qualquer uma dessas fechado sessões (por exemplo, **Get-CsMeetingConfiguration** no Skype para Business Online), você receberá uma mensagem de erro semelhante a este.
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

Recebemos essa mensagem de erro porque os cmdlets do Skype para Business Online, o Exchange Online e a segurança &amp; Centro de conformidade foram excluídos quando fechamos as sessões remotas.
  
Para fechar a sessão do SharePoint Online, digite este comando.
  
```
Disconnect-SPOService
```

Se você tentar executar o cmdlet **Get-SPOSite** agora, você receberá uma mensagem de erro semelhante a esta.
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

Você não é possível recuperar as informações do site porque você não está conectado ao SharePoint Online.
  
Às propriedades de sua conexão com o Office 365, embora não haja um cmdlet do **Connect-MsolService** , não há nenhum cmdlet de **Disconnect-MsolService** correspondente. Portanto para o Office 365, basta feche a janela do Windows PowerShell. No entanto, ainda é uma boa ideia fazer isso últimos, portanto você pode adequadamente desconectar do SharePoint Online, Skype para Business Online, o Exchange Online e a segurança &amp; Centro de conformidade.
  
## <a name="new-to-office-365"></a>Começando a usar o Office 365?
<a name="LongVersion"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Veja também

#### 

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Gerenciar o SharePoint Online com o Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
  
[Gerenciar contas de usuário e licenças usando o PowerShell do Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Use o Windows PowerShell para criar relatórios no Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

