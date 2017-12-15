---
title: "Desabilitar o acesso aos serviços com o PowerShell do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Explica como usar o Office 365 PowerShell para adicionar ou remover o acesso aos serviços do Office 365 para usuários na sua organização."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Desabilitar o acesso aos serviços com o PowerShell do Office 365

**Resumo:** Explica como usar o Office 365 PowerShell para adicionar ou remover o acesso aos serviços do Office 365 para usuários na sua organização.
  
Quando uma conta do Office 365 é atribuída a uma licença de um plano de licenciamento, serviços do Office 365 são disponibilizados para o usuário dessa licença. No entanto, você pode controlar os serviços do Office 365 que o usuário pode acessar. Por exemplo, mesmo que a licença permite o acesso ao SharePoint Online, você pode desabilitar o acesso a ele. Na verdade, você pode usar o Office 365 PowerShell para desabilitar o acesso a qualquer número de serviços para:
- Uma conta individual
    
- Um grupo de contas.
    
- Todas as contas em sua organização.
    
 **Conteúdo:** [A versão curta (instruções sem explicações)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [A versão longa (instruções com explicações detalhadas sobre)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Consulte também](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>Antes de começar
<a name="RTT"> </a>

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Você pode usar o cmdlet **Get-MsolAccountSku** para exibir seus planos de licenciamento disponíveis e que estão disponíveis nesses planos de serviços do Office 365. Para obter mais informações, consulte[Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Para ver o antes e depois os resultados dos procedimentos neste tópico, consulte [Exibir detalhes de licença e serviço de conta com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico. Especificamente, o script permite exibir e desabilitar serviços em sua organização do Office 365, incluindo o Sway. Para saber mais, confira [Desabilitar o acesso ao Sway com o PowerShell do Office 365](disable-access-to-sway-with-office-365-powershell.md).
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.
    
## <a name="the-short-version-instructions-without-explanations"></a>A versão curta (instruções sem explicações)
<a name="ShortVersion"> </a>

Esta seção apresenta os procedimentos sem divulgação ou explicação supérflua. Se você tiver dúvidas ou se quiser obter mais informações, leia o restante do tópico.
  
Para desabilitar os serviços do Office 365 para usuários de um único plano de licenciamento, execute as seguintes etapas:
  
1. Identificar os serviços indesejáveis no plano de licenciamento usando a seguinte sintaxe:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    Este exemplo cria um objeto **LicenseOptions** que desabilita os Serviços Online do Office e SharePoint Online no plano de licenciamento denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Use o objeto **LicenseOptions** da etapa 1 em um ou mais usuários.
    
  - Para criar uma nova conta que tem serviços desabilitados, use a seguinte sintaxe:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    Este exemplo cria uma nova conta para Leonor Marques que atribui a licença e desabilita os serviços descritos na Etapa 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    Para obter mais informações sobre a criação de contas de usuário no Office 365 PowerShell, consulte [criar contas de usuário com o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Para desabilitar os serviços de um usuário licenciado existente, use a seguinte sintaxe:
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    Este exemplo desabilita os serviços do usuário BrendaF@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Para desabilitar os serviços descritos na etapa 1 para todos os usuários licenciados existentes, especifique o nome do seu plano do Office 365 da exibição do cmdlet **Get-MsolAccountSku** (por exemplo, **litwareinc: enterprisepack** ) e, em seguida, execute os seguintes comandos:
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - Para desabilitar os serviços para um grupo de usuários existentes, use um dos seguintes métodos para identificar os usuários:
    
  - **Filtrar as contas com base em um atributo existente da conta** Para fazer isso, use a seguinte sintaxe:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    Este exemplo desabilita os serviços para os usuários no departamento de Vendas nos Estados Unidos.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:
    
1. Crie um arquivo de texto que contenha uma conta em cada linha da seguinte forma:
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    Neste exemplo, o arquivo de texto é c:\\Meus documentos\\Accounts.txt.
    
2. Execute o comando a seguir:
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Para desabilitar os serviços do Office 365 para usuários enquanto eles atribuídas a um plano de licenciamento, consulte [Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário](disable-access-to-services-while-assigning-user-licenses.md).
  
Para desabilitar os serviços do Office 365 para usuários em todos os planos de licenciamento disponíveis, execute as seguintes etapas:
  
1. Copie e cole este script no Bloco de Notas.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. Personalize os seguintes valores para seu ambiente:
    
  -  _<UndesirableService>_Neste exemplo, usaremos Online do Office e SharePoint Online.
    
  -  _<Account>_Neste exemplo, usaremos belindan@litwareinc.com.
    
    O script personalizado tem esta aparência:
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. Salve o script como `RemoveO365Services.ps1` em um local fácil de encontrar. Neste exemplo, podemos vai salvar o arquivo em " `C:\\O365 Scripts`".
    
4. Execute o script no PowerShell do Office 365 usando o comando a seguir.
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Para reverter os efeitos de qualquer um desses procedimentos (ou seja, para reabilitar os serviços desabilitados), execute o procedimento novamente, mas use o valor `$null` para o parâmetro _DisabledPlans_ .
  
[Voltar ao início](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>A versão longa (instruções com explicações detalhadas)
<a name="LongVersion"> </a>

Por padrão, todos os serviços estão habilitados quando você emite uma licença usando o PowerShell do Office 365. E geralmente é uma boa coisa: isso significa que você pode rapidez e facilidade atribuir licenças aos usuários sem ter de especificar o que cada serviço será habilitada ao longo do percurso.
  
Dito isso, no entanto, também é verdade que você deseja restringir os serviços disponíveis em alguns dos usuários; Por exemplo, talvez alguns usuários devem ter acesso ao Office Professional Plus, Skype para Business Online e Exchange Online, mas esses mesmos usuários não devem ter acesso ao SharePoint Online ou no Office Online. Você pode restringir contas dessa maneira? Na verdade, você pode. Para ajudar a explicam como isso funciona, vamos uma abordagem em duas etapas para lidar com esse problema:
  
1. Atribua ao usuário uma licença do Office 365 que automaticamente habilita todos os serviços.
    
2. Execute um par de comandos do PowerShell do Office 365 que desabilitam serviços para esse usuário.
    
Podemos já atentar da etapa 1: nosso (Belinda Newman) do usuário tem uma licença do Office 365 que lhe oferece acesso a todos os serviços do Office 365. No entanto, queremos modificar a conta de Belinda para que ela não tem acesso ao SharePoint Online ( `SHAREPOINTENTERPRISE`) ou no Office Online ( `SHAREPOINTWAC`). Mas como podemos devem fazer isso?
  
Aqui está como. Em primeiro lugar, vamos usar o cmdlet **New-MsolLicenseOptions** para criar um objeto de **LicenseOption** que contém os serviços que queremos desabilitados. No caso de Belinda, queremos desabilitar `SHAREPOINTENTERPRISE` e `SHAREPOINTWAC`, portanto, usamos este comando:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

Entendeu como funciona? Você especifica o plano de licenciamento ( `litwareinc:ENTERPRISEPACK`) e indica cada um dos serviços que você deseja desabilitados, separando-os por vírgulas.
  
> [!NOTE]
> Certificar-se de que você armazene seu novo objeto **LicenseOption** em uma variável. No exemplo anterior, usamos `$x`, embora você possa usar qualquer nome de variável válido do Windows PowerShell. 
  
Agora podemos usar o seguinte comando para desabilitar o acesso de Belinda aos dois serviços:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Nada muito elaborado aqui, ambos: basta chamar o cmdlet **Set-MsolUserLicense** e incluir o parâmetro _LicenseOptions_ , juntamente com a variável ( `$x`) que contém os planos queremos desabilitar. E o que vemos agora se podemos dê uma olhada no informações de licença de Belinda executando o comando: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Vemos isto:
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

Muito legal, hein? E, obviamente, poderíamos fazer essa mesma coisa a vários usuários se quisermos. Por exemplo, esses comandos desabilitar os mesmos dois serviços para todos os nossos usuários licenciados. Especifique o nome do seu plano do Office 365 da exibição do cmdlet **Get-MsolAccountSku** (por exemplo, **litwareinc: enterprisepack** ) e, em seguida, executá-los.
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

Tenha em mente que Belinda ainda tem uma licença válida do Office 365; é exatamente isso agora ela tem acesso aos serviços de menos. Antes de desabilitamos os dois serviços, Belinda tinha acesso a news feeds, OneDrive e SharePoint Online sites:
  
![Usuário com acesso ao SharePoint](images/o365_powershell_with_sharepoint.png)
  
Agora essas opções já não estão mais disponíveis:
  
![Usuário sem acesso ao SharePoint](images/o365_powershell_without_sharepoint.png)
  
Que é exatamente o que queríamos que acontecesse.
  
E se podemos alterar nossa mente posterior em: é possível reabilitar esses serviços? Você aposto é. Para reabilitar a todos os serviços para um usuário, use este comando para criar o objeto de **LicenseOption** a seguir:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

O que esse comando fazer? Para começar, com a constante do Windows PowerShell `$null` significa "nada". (Ou, no idioma do pouco mais técnico, isso significa que um "valor nulo".) Como você se lembra, quando usamos o cmdlet **New-MsolLicenseOptions** temos que indicar os serviços que queremos desabilitado. Nesse caso, não queremos qualquer um dos serviços a ser desabilitado. Que podem levar você acredita que poderíamos usar um comando semelhante ao seguinte, um comando onde podemos não especificar um valor para o parâmetro _DisabledPlans_ :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

No entanto, isso não funcionará. Em vez disso, ela gerará uma mensagem de erro:
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
Felizmente para nós, definindo o valor de parâmetro para `$null` funciona:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Isso simplesmente significa que, quando executamos o cmdlet **Set-MsolUserLicense** , estamos dizendo para **Set-MsolUserLicense** que não queremos que Belinda tenha quaisquer serviços desabilitados:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

E, logicamente, se nenhum dos serviços está desabilitado, deve significar que todos estão habilitados.
  
Agora que você entende como isso funciona, vamos mostram como você pode emitir uma licença e desabilitar os serviços especificados e todos com o mesmo comando. Sinceramente, não há realmente nada a ele, mas, isso parece muito impressionante: apenas incluir os _AddLicenses_ e _LicenseOptions_ parâmetros no mesmo comando. Em outras palavras, primeiro crie seu objeto **LicenseOption** :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

E, em seguida, conforme observado anteriormente, você usa o _AddLicenses_ e os parâmetros de _LicenseOptions_ em seu comando:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

Que comando emitirá Belinda Newman uma nova licença, mas uma licença nos qual Skype para Business Online ( `SHAREPOINTWAC`) e o SharePoint Online ( `SHAREPOINTENTERPRISE`) estarão desabilitados.
  
[Voltar ao início](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>Começando a usar o Office 365?
<a name="LongVersion"> </a>

||
|:-----|
|![O ícone pequeno do LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Começando a usar o Office 365?**         Descubra cursos em vídeo gratuitos para **Office 365 admins and IT pros**, oferecidos pelo LinkedIn Learning. |
   
## <a name="see-also"></a>See also
<a name="SeeAlso"> </a>

Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear contas de usuários com o Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Atribuir licenças a contas de usuários usando o PowerShell do Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Criar contas de usuários usando o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [New-MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [MsolUser-nova](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object.](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[Voltar ao início](disable-access-to-services-with-office-365-powershell.md#RTT)
  

