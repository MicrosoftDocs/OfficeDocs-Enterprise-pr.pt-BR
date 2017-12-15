---
title: "Atribuir licenças a contas de usuários usando o PowerShell do Office 365"
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
- LIL_Placement
- DecEntMigration
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "Explica como usar o Office 365 PowerShell atribuir uma licença do Office 365 para usuários sem licença."
ms.openlocfilehash: 7120b5d61b98f401f9ec1830598f20fbcbecdb66
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Atribuir licenças a contas de usuários usando o PowerShell do Office 365

**Resumo:**  Explica como usar o Office 365 PowerShell atribuir uma licença do Office 365 para usuários sem licença.
  
Licenciar contas de usuário no Office 365 é importante, porque os usuários não podem usar qualquer serviços do Office 365, até que a sua conta foi licenciada. Você pode usar o Office 365 PowerShell com eficiência atribuir licenças às contas não licenciadas, especialmente várias contas. 

## <a name="before-you-begin"></a>Antes de começar
<a name="RTT"> </a>

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Use o cmdlet **Get-MsolAccountSku** para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano em sua organização. O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para obter mais informações sobre o licenciamento planos, licenças e serviços, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Para localizar as contas não licenciadas em sua organização, execute o comando  `Get-MsolUser -All -UnlicensedUsersOnly`
    
- Você pode atribuir licenças apenas às contas de usuário que têm a propriedade **UsageLocation** definida como um código de país do 3166-1 alpha-2 ISO válido. Por exemplo, nos Estados Unidos e FR para França de tempo. Alguns serviços do Office 365 não estão disponíveis em determinados países. Para obter mais informações, consulte [sobre as restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Para localizar contas que não tenham um valor **UsageLocation**, execute o comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Para definir o valor **UsageLocation** em uma conta, use a sintaxe `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Por exemplo,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o `-All` parâmetro, apenas as primeiro 500 contas são retornadas.
    
## <a name="the-short-version-instructions-without-explanations"></a>A versão curta (instruções sem explicações)
<a name="ShortVersion"> </a>

Esta seção apresenta os procedimentos sem explicação detalhada. Se você tiver dúvidas ou para obter mais informações, você pode ler o restante do tópico.
  
Para atribuir uma licença a um usuário, use a seguinte sintaxe no Office 365 PowerShell:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Este exemplo atribui uma licença do `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) plano de licenciamento para o usuário não licenciado `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Para atribuir uma licença a vários usuários sem licença, use a seguinte sintaxe:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Notas**
  
- Você não pode atribuir várias licenças a um usuário do mesmo plano de licenciamento.
    
- Se você não tiver licenças o suficiente disponíveis, as licenças serão atribuídas aos usuários na ordem em que eles forem retornados pelo cmdlet **Get-MsolUser** até que as licenças disponíveis esgotem.
    
Este exemplo atribui as licenças do `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) plano de licenciamento para todos os usuários sem licença.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

Este exemplo atribui essas mesmas licenças a usuários não licenciados no Departamento de vendas nos Estados Unidos.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>A versão longa (instruções com explicações detalhadas)
<a name="LongVersion"> </a>

Como observado no artigo [Exibir usuários licenciados e não licenciados com o PowerShell do Office 365](view-licensed-and-unlicensed-users-with-office-365-powershell.md), é possível ter usuários com contas de usuário do Office 365 válidas mas que não tenham obtido uma licença do Office 365. Isso significa que, com conta válida ou não, esses usuários não poderão fazer logon no Office 365. E se você não pode fazer logon, não pode aproveitar nenhum dos serviços do Office 365.
  
O artigo supracitado também observou que podemos retornar uma lista de contas de usuário não licenciadas executando este comando:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Esse comando retorna informações sobre todos os usuários que não estejam licenciados para o Office 365 no momento:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

Como você pode ver, temos um usuário não licenciado. Brenda Fernandes. E como podemos atribuir uma licença do Office 365 a Brenda?
  
Para começar, vamos executar o cmdlet **Get-MsolAccountSku** discutido no artigo [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):
  
```
Get-MsolAccountSku
```

Esse comando retorna dados semelhantes a estes:
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

Por que executamos o **Get-MsolAccountSku** ? "Sku", caso você queira saber, é a abreviação de "stock-keeping unit" (unidade de manutenção de estoque). Para os fins deste guia, é só um jargão comercial para "produto". Existem dois motivos para a execução de **Get-MsolAccountSku**. Primeiro, precisamos garantir que realmente temos uma licença para atribuirmos a Brenda. Temos alguma licença para atribuir a ela? Para determinar isso, pegamos o valor da propriedade **ActiveUnits** (25) e subtraímos os valores das propriedades **WarningUnits** (0) e **ConsumedUnits** (24):
  
 `25 - 0 - 24 = 1`
  
A propriedade **ActiveUnits** nos diz quantas licenças nós compramos, e o valor combinado de **WarningUnits** e de **ConsumedUnits** nos diz quantas licenças estão em uso no momento. Se subtrairmos o número de licenças já dito do número de licenças que compramos, saberemos quantas licenças ainda estão disponíveis. Por sorte, temos uma licença disponível para distribuição:
  
 `25 - 0 - 24 = 1`
  
Segundo, para atribuirmos uma nova licença a Brenda, precisamos saber o nome de nosso plano de licenciamento, isto é, precisamos conhecer a **AccountSkuId**. Neste caso, isso é fácil: temos somente uma plano de licenciamento ( `litwareinc:ENTERPRISEPACK`). Observe, no entanto, que uma organização pode ter vários planos de licenciamento. Nesse cenário, **Get-MsolAccountSku** retornaria duas **AccountSkuIds** diferentes e seria necessário escolher o plano de licenciamento apropriado ao atribuir as licenças. Por enquanto continuaremos com o caso mais simples e assumiremos que temos apenas um plano de licenciamento.
  
Então,  *como*  atribuímos uma nova licença para a Brenda Fernandes? Assim:
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Você terá que fazer o seguinte: chame o cmdlet **Set-MsolUserLicense**, especificando o parâmetro _UserPrincipalName_ para o usuário e o plano de licenciamento apropriado.
  
Quando **Set-MsolUserLicense** terminar de ser executado, você verá algo similar a isto na tela:
  
 `PS C:\\windows\\system32>`
  
Em outras palavras, não parecerá que algo mudou. Para verificar se a licença foi atribuída ao usuário, execute um comando como o seguinte:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

Se tudo tiver ocorrido conforme esperado, você verá a propriedade isLicensed de Brenda definida como True:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!SECURITY NOTE] Boa pergunta: e se você errar e tentar atribuir a licença a um usuário que já tenha uma licença? Um único usuário ficará com duas licenças? > A resposta rápida é não. O Office 365 não permite que você atribua mais de uma licença ao mesmo usuário. (Para falar a verdade, mais de uma licença do mesmo plano de licença, que fique bem claro). Se tentar fazer isso, seu comando falhará e você verá a seguinte mensagem de erro: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> É verdade que essa mensagem de erro é um pouco confusa: a licença não é inválida, só está sendo atribuída a um usuário que  *já possui*  uma licença. Mas, independente disso, o importante é observar que um usuário não ficará com várias licenças.
  
Como vimos, é muito fácil usar o Office 365 PowerShell para atribuir uma única licença a um único usuário. E isso nos leva a uma pergunta óbvia: não seria tão ou mais fácil usar o Centro de administração do Office 365 para atribuir uma única licença a um único usuário? Bem, talvez. Isso dependerá, em parte, se você se sente mais confortável usando o Windows PowerShell ou usando o Centro de administração do Office 365. O Windows PowerShell realmente se destaca quando você precisa atribuir várias licenças a vários usuários. Por exemplo, este comando atribui uma licença do Office 365 a qualquer de seus usuários que ainda não tenha licença:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

No comando anterior, usamos **Get-MsolUser** e o parâmetro _UnlicensedUsersOnly_ para obtermos um conjunto de todas as contas de usuário não licenciadas. Então, passamos esse conjunto para o cmdlet **Set-MsolUserLicense**. Por sua vez, **Set-MsolUserLicense** atribui uma licença (retirada do plano de licenciamento `litwareinc:ENTERPRISEPACK`) a cada usuário no conjunto.
  
Mas e se você tiver cinco usuários não licenciados e apenas uma licença disponível? Nesse caso, **Set-MsolUserLicense** dará a licença disponível ao primeiro usuário retornado por **Get-MsolUser**. Então, **Set-MsolUserLicense** tentará atribuir diligentemente uma licença aos outros quatro usuários, mas todas as quatro tentativas falharão, gerando a seguinte mensagem de erro:
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
Em outras palavras, MsolUserLicense não falhará simplesmente. Em vez disso, ele atribuirá todas as licenças possíveis. Só então falhará.
  
Vamos tentar outro exemplo. Talvez você queira atribuir uma licença a todos os usuários no departamento de vendas. Sem problema:
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Ou, se quiser fazer algo mais elaborado (e quiser manter um mínimo de mensagens de erro e de processamento de computação), apenas atribua uma licença a usuários não licenciados do departamento de vendas:
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Afinal, de nada serve tentar licenciar usuários que já têm uma licença. Já vimos que isso não funciona.
  
Eis outro exemplo. Talvez você queira licenciar todos os usuários no Brasil que atualmente não têm uma licença do Office 365. Nesse caso:
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

E assim por diante.
  
> [!NOTE]
> Quanto tempo demora para executar um comando que, digamos, emite licenças a todos os usuários não licenciados? É difícil dizer. Depende de várias coisas, desde a quantidade de usuários até a velocidade da sua conexão de rede. Se tiver algumas centenas de usuários para licenciar, será razoavelmente rápido (isto é, não deve levar mais do que um minuto ou dois). Se tiver 10 mil usuários, obviamente demorará mais. Mas não chega nem perto do tempo que demoraria para atribuir licenças a 10 mil usuários usando o Centro de administração do Office 365. 
  
Já que falamos nisso, tome cuidado com o seguinte ao atribuir licenças: se um usuário não tiver um valor configurado para a propriedade **UsageLocation** mencionada anteriormente, não será possível atribuir uma licença do Office 365 a ele. Em vez disso, você receberá uma mensagem de erro similar a esta:
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
De uma forma redundante, essa mensagem de erro nos informa que o usuário em questão não tem um **UsageLocation** atribuído. Como você já deve ter adivinhado, a propriedade **UsageLocation** (que indica a região ou o país em que o usuário geralmente utiliza o Office 365) é extremamente importante. Por quê? Isso acontece porque os serviços disponíveis dependem do pacote de licenciamento adquirido e do local em que o usuário reside: devido a normas e regulamentações locais, alguns serviços podem não estar disponíveis a alguns usuários. Se um usuário não tem um **UsageLocation**, o Office 365 não tem como saber quais serviços podem ser legalmente expostos a ele. Portanto, o Office 365 não pode oferecer serviços ao usuário, pelo menos não até que o **UsageLocation** tenha sido especificado.
  
> [!NOTE]
> Quando você configura uma conta de usuário você saberá imediatamente se há alguma restrição de licença associada à parte especificada do mundo. Por exemplo, se você alterar o **UsageLocation** para um usuário licenciado para Irã ( `IR`), o comando falhará com essa mensagem de erro: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> Isso ocorre porque o Office 365 não está disponível atualmente para usuários do Irã. Para obter mais informações, consulte [sobre as restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730). A propósito, o Office 365 utiliza os códigos de país com duas letras produzidos pela International Organization for Standardization (ISO). Você pode encontrar esses códigos no [site da web ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073). 
  
Se quiser verificar se determinado usuário tem um **UsageLocation**, é possível usar um comando similar a este:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

Ou você pode obter uma lista de todos os usuários que não têm um **UsageLocation** com este comando:
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> Quando você atribuir uma licença a um usuário que o usuário, por padrão, receberá acesso a todos os serviços do Office 365 que sua organização tem acesso. Por exemplo, se você adquiriu licenças para o Office 365 Enterprise E3, seu usuário recentemente licenciadas automaticamente terão acesso a serviços como o Exchange Online, Skype para Business Online e SharePoint Online. Se você preferir limitar o acesso do usuário para esses serviços (por exemplo, convém que um usuário tenha acesso ao SharePoint Online, mas *não* para Exchange Online e Skype para Business Online), em seguida, consulte o artigo [Desabilitar o acesso aos serviços com o Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md). 
  
## <a name="new-to-office-365"></a>Começando a usar o Office 365?

||
|:-----|
|![O ícone pequeno do LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Começando a usar o Office 365?**         Descubra cursos em vídeo gratuitos para [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), oferecidos pelo LinkedIn Learning. |
   
## <a name="see-also"></a>See Also
<a name="SeeAlso"> </a>

Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Criar contas de usuários usando o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear contas de usuários com o Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Remover licenças de contas de usuários com o Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object.](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

