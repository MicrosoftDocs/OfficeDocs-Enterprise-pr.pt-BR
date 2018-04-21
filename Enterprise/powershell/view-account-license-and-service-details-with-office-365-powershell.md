---
title: Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários.
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell

**Resumo:** Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários.
  
No Office 365, licencia para planos de licenciamento (também chamado de SKUs ou do Office 365 estiver planejando) conceder aos usuários acesso aos serviços do Office 365 que são definidos para esses planos. No entanto, um usuário pode não ter acesso a todos os serviços que estão disponíveis em uma licença atualmente atribuído a eles. Você pode usar o PowerShell do Office 365 para exibir o status dos serviços em contas de usuário. 

## <a name="before-you-begin"></a>Antes de começar
<a name="RTT"> </a>

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Use os comandos `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` para encontrar as seguintes informações:
    
  - Os planos de licenciamento que estão disponíveis na sua organização.
    
  - Os serviços que estão disponíveis em cada plano de licenciamento e a ordem em que eles estão listados (o número do índice).
    
     Para obter mais informações sobre o licenciamento planos, licenças e serviços, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Use o comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` para encontrar as licenças atribuídas a um usuário e a ordem na qual eles estão listados (o número de índice).
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.
    
<a name="ShortVersion"> </a>
## <a name="the-short-version-instructions-without-explanations"></a>A versão curta (instruções sem explicações)

Para exibir todos os serviços do Office 365 PowerShell que um usuário tem acesso ao, use a seguinte sintaxe:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Este exemplo mostra os serviços aos quais o usuário BelindaN@litwareinc.com tem acesso. Mostra os serviços que estão associados a todas as licenças são atribuídas à sua conta.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Este exemplo mostra os serviços aos quais a usuária BrendaF@litwareinc.com tem acesso a partir da primeira licença atribuída à conta dela (o número de índice é 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Para localizar todos os usuários licenciados que foram habilitados ou não habilitados para serviços específicos, use a seguinte sintaxe:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

Esses exemplos utilizam as seguintes informações:
  
- A licença que fornece acesso aos serviços do Office 365 que estamos interessados em é a primeira licença atribuída a todos os usuários (o número de índice é 0).
    
- Os serviços do Office 365 que estamos interessados em são Skype para Business Online e o Exchange Online. As licenças que estão associados com o plano de licenciamento, Skype para Business Online é o serviço 6º listado (o número de índice é de 5), e o Exchange Online é o serviço de 9 listados (o número de índice é 8).
    
Este exemplo retorna todas licenciados usuários habilitados para o Skype para Business Online e o Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Este exemplo retorna todos os usuários licenciados que não estão habilitados para o Skype para Business Online ou Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<a name="LongVersion"> </a>
## <a name="the-long-version-instructions-with-detailed-explanations"></a>A versão longa (instruções com explicações detalhadas)

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>Encontre os serviços do Office 365 PowerShell que um usuário tem acesso ao

É importante, obviamente, para que você sabe quais usuários tiverem sido emitidos licenças do Office 365 e os usuários que ainda não. (Consulte o artigo [Exibir usuários licenciados e não licenciados com o Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) para obter mais informações). No entanto, simplesmente ter uma licença do Office 365 não informa nada sobre o que esse usuário pode realmente fazer com o Office 365. Pode ele usar Exchange Online ou Skype para Business Online? Esse usuário pode acessar o SharePoint Online? Ele tem acesso ao Office Professional Plus? Ter uma licença simplesmente significa que o usuário tem o potencial para acessar esses serviços. No entanto, os recursos disponíveis para um usuário dependem os serviços que foram habilitados em sua licença.
  
Como podemos determinar a quais recursos do Office 365 um usuário tem acesso? Para fazer isso precisamos executar um comando semelhante a esta:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

Neste comando, estamos usando o cmdlet **Get-MsolUser** para retornar informações sobre a conta BelindaN@litwareinc.com. Depois que podemos tiver retornado essa informação, podemos, em seguida, canalize os dados da conta para o cmdlet **Select-Object** e solicite **Select-Object** para "expandir" o valor da propriedade **licenças** :
  
 `Select-Object -ExpandProperty Licenses`
  
Por que fazemos isso? Bem, por padrão, as **licenças** de propriedade nos informa apenas o nome do pacote de licenciamento onde originou a licença de Belinda de:
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

"Expandir" **essa propriedade** nos dá um pouco mais informações:
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

E, em seguida, expandindo a propriedade **ServiceStatus** podemos obter ainda mais informações:
  
|****Plano de serviço****|****Descrição****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plano 2 do Exchange Online  <br/> |
   
> [!NOTE]
> Acha que está digitando muito? Bem, se você conseguir aguentar uma pouco as chatices do Windows PowerShell, você poderá executar a versão compacta do comando em vez disso: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
Caso você esteja se perguntando, podemos podem "expandir" **essa propriedade** como **licenças** é uma propriedade de valores múltiplos: é uma única propriedade que pode armazenar vários valores. Quando há que expandimos podemos simplesmente fazer drill down em um valor de propriedade recebe esses valores adicionais que, por padrão, não são exibidos na tela.
  
> [!NOTE]
> Então como podemos saber que um valor é uma propriedade de vários valores? Bem, para descobrir isso, tente executar um comando similar a esta: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> o cmdlet **Get-member** retorna informações sobre o objeto em si; Nesse caso, as informações sobre a propriedade valores que formam um objeto de conta de usuário. Aqui está o que **Get-Member** tem a dizer sobre a propriedade **licenças** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> se a definição da propriedade nos diz algo sobre conjuntos (neste caso, `System.Collections.Generic.List`), então você sabe que você está lidando com uma propriedade de vários valores. 
  
Então o que isso significa? Para responder a isso, vamos primeiro dar uma olhada nas informações retornadas pelo cmdlet **Get-MsolUser** :
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

E vamos também dar uma olhada em uma tabela que explica o que esses planos de serviço estranhos representam:
  
|****Plano de serviço****|****Descrição****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plano 2 do Exchange Online  <br/> |
   
Entendeu tudo?  `MCOSTANDARD` destina-se apenas um nome interno programação para Skype Online de negócios, enquanto `OFFICESUSBCRIPTION` é apenas o nome interno programação para Office Professional Plus. Não é a coisa mais intuitiva no mundo, mas desde que você mantenha esta tabela úteis não terá muitos problemas quando se trata de trabalhar com os serviços do Office 365.
  
Mas espere: há mais. Como podemos aprendeu no artigo [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), se o **ProvisioningStatus** estiver definida como `Success` , isso significa que o serviço foi habilitado totalmente; Por exemplo se `MCOSTANDARD` estiver definida como `Success` , isso significa que o usuário pode acessar o Skype para Business Online. Se o **ProvisioningStatus** estiver definida como `PendingInput` , isso significa que o Office 365 ainda está processando a solicitação de serviço; No entanto, o usuário pode fazer logon e acessar o serviço enquanto a solicitação termina o processamento normalmente. ( `YAMMER_ENTERPRISE` sempre serão exibidos como `PendingInput`, mas isso é Okey: não para de que um usuário faça logon no Yammer).
  
> [!IMPORTANT]
> Os usuários podem instalar e ativar uma nova instalação do Office Professional Plus enquanto `OFFICESUBSCRIPTION` que se situa a `PendingInput` estado.
  
E, obviamente, é um serviço é definido como `Disabled` isso significa que o serviço em questão não está disponível para o usuário.
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>Localizar usuários que têm acesso a serviços específicos do Office 365 PowerShell

Um artigo separados, vimos como você pode usar o Office 365 PowerShell para desabilitar o acesso do usuário aos serviços. (Se você tiver perdido desse artigo, consulte [Desabilitar o acesso aos serviços do Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Isso leva a uma pergunta óbvia: há alguma maneira para determinar quais *usuários* (ou seja, mais de um usuário) têm quais serviços habilitados ou desabilitados?
  
Esperávamos que alguém fizesse que. Para responder à pergunta, vamos revisar a tabela de serviços que primeiro examinamos no artigo [serviços com o Office 365 PowerShell e exibir as licenças](view-licenses-and-services-with-office-365-powershell.md) para nosso plano de licenciamento disponível apenas `litwareinc:ENTERPRISEPACK`:
  
|****Plano de serviço****|****Descrição****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plano 2 do Exchange Online  <br/> |
   
Como você pode lembrar, o plano de serviço é nada mais que o nome interno de programação para um produto. Por exemplo, `OFFICESUBSCRIPTION`, para o nome de um, é o nome interno de programação para Office Professional Plus. Se `OFFICESUBSCRIPTION` aparece como `SUCCESS` no plano de serviço de um usuário, em seguida, isso significa que o usuário tem permissão para acessar o Office Professional Plus. Se `EXCHANGE_S_ENTERPRISE` está listado como `DISABLED` isso significa que o usuário não é possível usar o Exchange Online.
  
> [!IMPORTANT]
> Os usuários podem instalar e ativar uma nova instalação do Office Professional Plus enquanto `OFFICESUBSCRIPTION` que se situa a `PendingInput` estado.
  
Este é o momento em que a ordem na qual os serviços são exibidos é extremamente importante. Windows PowerShell atribui um número de índice para cada entrada na lista. A primeira entrada é 0, a próxima entrada é 1 e assim por diante. Os resultados são explicados na tabela a seguir:
  
|Número de índice * * *|****Plano de serviço****|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
Como você pode ver, `SWAY` é o primeiro serviço listado, portanto, ela recebe o número de índice 0.
  
> [!CAUTION]
> Por que 0 e não 1? Isso é um ponto de programação. Em linguagens de programação índices informam quanto um item é "deslocar" desde o início da matriz. O primeiro item *é* o início da matriz, portanto, seu deslocamento é 0. O segundo item é 1 item desde o início da matriz, portanto, seu deslocamento é 1.
  
Vamos tentar um exemplo. Suponha que gostaríamos de uma lista de todos os usuários licenciados que não tiverem sido habilitados para o Exchange Online. Para fazer isso, podemos usar o seguinte comando:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Sem dúvida, que é um comando de pouca secreto procurando, vamos levar um minuto para explicar como ele funciona. Isso é realmente um comando de duas partes e a primeira parte é muito simple: usamos o cmdlet **Get-MsolUser** para retornar uma coleção de todos os nossos usuários do Office 365 (licenciado e não licenciado):
  
```
Get-MsolUser
```

Essa informação é então canalizada para o cmdlet **Where-Object** . **Where-Object** percorre todas as contas de usuário e procura por essas contas que atenderem aos seguintes critérios:
  
- A propriedade **isLicensed** é igual a ( `-eq`) `True` ( `$true`). Que permite que os usuários não licenciados eliminar.
    
- O valor das licenças **[0]. ServiceStatus [8]. ProvisioningStatus** propriedade for igual a ( `-eq`) `Disabled`. Para fins de nossos imediatas, a parte importante desse nome de propriedade complicado é o seguinte:
    
     `ServiceStatus[8]`
    
    O `[8]` representa o número de índice para o Exchange Online. (Nós sabemos que observando a tabela há alguns minutos). O que ocorre se queríamos localizar todos os usuários habilitados para Skype para Business Online? Bem, o número de índice para Skype para Business Online é 5, portanto, usaríamos esta sintaxe:
    
     `ServiceStatus[5]`
    
    Etc., etc.
    
    A propósito, `Licenses[0]` indica o plano de licenciamento que queremos a ser analisado. Como o domínio de nosso teste tem apenas um plano de licenciamento isso não importa muito. Mas, suponhamos que tivéssemos que um usuário que tenha sido atribuído licenças de dois diferentes planos de licenciamento. Nesse caso, `Licenses[0]` seria representam o primeiro plano de licenciamento e `Licenses[1]` seria representam o segundo plano de licenciamento.
    
    Para encontrar as licenças atribuídas a um usuário e a ordem na qual elas estão listadas, execute o seguinte comando:
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

Você consegue ver como isso funciona? O número de índice para o Office Professional Plus é 4; Portanto, este comando retorna uma lista de todos os usuários que não tiverem sido habilitados para o Office Professional Plus:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

E se queríamos que uma lista de usuários que tiverem sido *habilitados* para o Office Professional Plus? Bem, se você tiver sido habilitado sua **ServiceStatus** será `PendingInput` ou `Success`; em outras palavras, sua **ServiceStatus** será igual *não* ( `-ne`) `Disabled`. Isso significa que tudo o que temos a fazer é levar nosso comando anterior e trocar o `-eq` operador para o `-ne` operador:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

Como dizem der, que código provavelmente não win concursos de maravilha muitos. E, verdade seja dita, o código pode obter ainda mais tangled. Por exemplo, suponha que queremos procurar usuários que tiverem sido habilitados para ambos os Skype para Business Online e o Exchange Online:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Mas não se preocupe muito sobre como gnarly que pode parecer: o mais importante é que, com relativamente pouco esforço, é possível recuperar essas informações. Não é possível obter essa mesma informação usando o Centro de administração do Office 365? Teoricamente, Sim mas, em termos práticos, não. Para obter essa mesma informação usando o Centro de administração do Office 365, você precisaria examinar as informações de licenciamento para cada usuário, um usuário por vez e, em seguida, manualmente ficar atento que tinham sido habilitados para *X* e quem não tivesse. Que seria funcionar, mas vamos sinceramente: se você tiver mais de 10 ou 11 usuários, você não vai fazer isso. É muito tediosas e demoradas.
  
É claro que, é por isso que temos o Windows PowerShell: Windows PowerShell ajuda você a se livrar de tarefas tediosas e demoradas, como que.
  
Aqui está um exemplo de um comando para exibir informações de serviço para um conjunto específico de serviços, conforme identificado por seus índices de licenças e ServiceStatus para uma assinatura do Office 365 E5:
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

Este comando cria um arquivo CSV mostrando todos os usuários e seus status de serviço para um conjunto específico de serviços (equipes, Yammer, AD RMS, OfficePro, Skype, SharePoint e Exchange).

>[!Note]
>Você pode obter a lista de serviços em uma assinatura do `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` comando. A saída, você inicia a numeração os índices de serviço com 0. O comando anterior é apenas um exemplo. Números de índice para serviços pode alterar ao longo do tempo.
>

  
<a name="SeeAlso"> </a>
## <a name="see-also"></a>Confira também

Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Criar contas de usuários usando o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear contas de usuários com o Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Atribuir licenças a contas de usuários usando o Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Remover licenças de contas de usuários com o Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Começando a usar o Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]