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
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "Explica como usar o Office 365 PowerShell para atribuir uma licença do Office 365 para usuários não licenciados."
ms.openlocfilehash: 88628a78179605c734cd1d3f114a8a1dcb712376
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="b9c87-103">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="b9c87-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="b9c87-104">**Resumo:** explica como usar o Office 365 PowerShell para atribuir uma licença do Office 365 para usuários não licenciados.</span><span class="sxs-lookup"><span data-stu-id="b9c87-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="b9c87-p101">O licenciamento de contas de usuário no Office 365 é importante, porque os usuários não poderão usar nenhum serviço do Office 365 até que suas contas sejam licenciadas. Você pode usar o Office 365 PowerShell para atribuir licenças de forma eficiente para contas não licenciadas, especialmente para várias contas.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="b9c87-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="b9c87-107">Before you begin</span></span>
<span data-ttu-id="b9c87-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="b9c87-108"><a name="RTT"> </a></span></span>

- <span data-ttu-id="b9c87-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b9c87-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="b9c87-p103">Use o cmdlet **Get-MsolAccountSku** para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano na sua organização. O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para mais informações sobre planos de licenciamento, licenças e serviços, confira [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b9c87-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="b9c87-114">Para localizar as contas não licenciadas em sua organização, execute o comando  `Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="b9c87-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="b9c87-p104">Você só pode atribuir licenças para contas de usuário que tenham o conjunto de propriedades **UsageLocation** definido como um código de país ISO 3166-1 alpha-2 válido. Por exemplo, US para os Estados Unidos e FR para a França. Alguns serviços do Office 365 não estão disponíveis em certos países. Para mais informações, confira [Sobre restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="b9c87-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="b9c87-p105">Para localizar contas que não tenham um valor **UsageLocation**, execute o comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Para definir o valor **UsageLocation** em uma conta, use a sintaxe `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Por exemplo,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="b9c87-122">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro `-All`, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="b9c87-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="b9c87-123">A versão curta (instruções sem explicações)</span><span class="sxs-lookup"><span data-stu-id="b9c87-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="b9c87-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="b9c87-124"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="b9c87-p106">Esta seção apresenta os procedimentos sem explicação detalhada. Se você tiver dúvidas ou se quiser obter mais informações, leia o restante do tópico.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="b9c87-127">Para atribuir uma licença a um usuário, use a seguinte sintaxe no Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b9c87-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="b9c87-128">Este exemplo atribui uma licença do plano de licenciamento do `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ao usuário não licenciado `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="b9c87-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="b9c87-129">Para atribuir uma licença a vários usuários sem licença, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="b9c87-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="b9c87-130">**Anotações**</span><span class="sxs-lookup"><span data-stu-id="b9c87-130">**Notes**</span></span>
  
- <span data-ttu-id="b9c87-131">Você não pode atribuir várias licenças a um usuário do mesmo plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="b9c87-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="b9c87-132">Se você não tiver licenças o suficiente disponíveis, as licenças serão atribuídas aos usuários na ordem em que eles forem retornados pelo cmdlet **Get-MsolUser** até que as licenças disponíveis esgotem.</span><span class="sxs-lookup"><span data-stu-id="b9c87-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="b9c87-133">Este exemplo atribui licenças do plano de licenciamento do `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) a todos os usuários não licenciados.</span><span class="sxs-lookup"><span data-stu-id="b9c87-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="b9c87-134">Este exemplo atribui essas mesmas licenças a usuários não licenciados no Departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="b9c87-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="b9c87-135">A versão longa (instruções com explicações detalhadas)</span><span class="sxs-lookup"><span data-stu-id="b9c87-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="b9c87-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="b9c87-136"><a name="LongVersion"> </a></span></span>

<span data-ttu-id="b9c87-p107">Como observado no artigo [Exibir usuários licenciados e não licenciados com o PowerShell do Office 365](view-licensed-and-unlicensed-users-with-office-365-powershell.md), é possível ter usuários com contas de usuário do Office 365 válidas mas que não tenham obtido uma licença do Office 365. Isso significa que, com conta válida ou não, esses usuários não poderão fazer logon no Office 365. E se você não pode fazer logon, não pode aproveitar nenhum dos serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="b9c87-140">O artigo supracitado também observou que podemos retornar uma lista de contas de usuário não licenciadas executando este comando:</span><span class="sxs-lookup"><span data-stu-id="b9c87-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="b9c87-141">Esse comando retorna informações sobre todos os usuários que não estejam licenciados para o Office 365 no momento:</span><span class="sxs-lookup"><span data-stu-id="b9c87-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="b9c87-p108">Como você pode ver, temos um usuário não licenciado: Brenda Fernandes. Como podemos atribuir uma licença do Office 365 a Brenda?</span><span class="sxs-lookup"><span data-stu-id="b9c87-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="b9c87-144">Para começar, vamos executar o cmdlet **Get-MsolAccountSku** discutido no artigo [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span><span class="sxs-lookup"><span data-stu-id="b9c87-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="b9c87-145">Esse comando retorna dados semelhantes a estes:</span><span class="sxs-lookup"><span data-stu-id="b9c87-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="b9c87-p109">Por que executamos o **Get-MsolAccountSku** ? "Sku", caso você queira saber, é a abreviação de "stock-keeping unit" (unidade de manutenção de estoque). Para os fins deste guia, é só um jargão comercial para "produto". Existem dois motivos para a execução de **Get-MsolAccountSku**. Primeiro, precisamos garantir que realmente temos uma licença para atribuirmos a Brenda. Temos alguma licença para atribuir a ela? Para determinar isso, pegamos o valor da propriedade **ActiveUnits** (25) e subtraímos os valores das propriedades **WarningUnits** (0) e **ConsumedUnits** (24):</span><span class="sxs-lookup"><span data-stu-id="b9c87-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="b9c87-p110">A propriedade **ActiveUnits** nos diz quantas licenças nós compramos, e o valor combinado de **WarningUnits** e de **ConsumedUnits** nos diz quantas licenças estão em uso no momento. Se subtrairmos o número de licenças já dito do número de licenças que compramos, saberemos quantas licenças ainda estão disponíveis. Por sorte, temos uma licença disponível para distribuição:</span><span class="sxs-lookup"><span data-stu-id="b9c87-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="b9c87-p111">Segundo, para atribuirmos uma nova licença a Brenda, precisamos saber o nome de nosso plano de licenciamento, isto é, precisamos conhecer a **AccountSkuId**. Neste caso, isso é fácil: temos somente uma plano de licenciamento ( `litwareinc:ENTERPRISEPACK`). Observe, no entanto, que uma organização pode ter vários planos de licenciamento. Nesse cenário, **Get-MsolAccountSku** retornaria duas **AccountSkuIds** diferentes e seria necessário escolher o plano de licenciamento apropriado ao atribuir as licenças. Por enquanto continuaremos com o caso mais simples e assumiremos que temos apenas um plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="b9c87-p112">Então,  *como*  atribuímos uma nova licença para a Brenda Fernandes? Assim:</span><span class="sxs-lookup"><span data-stu-id="b9c87-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="b9c87-162">Você terá que fazer o seguinte: chame o cmdlet **Set-MsolUserLicense**, especificando o parâmetro _UserPrincipalName_ para o usuário e o plano de licenciamento apropriado.</span><span class="sxs-lookup"><span data-stu-id="b9c87-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="b9c87-163">Quando **Set-MsolUserLicense** terminar de ser executado, você verá algo similar a isto na tela:</span><span class="sxs-lookup"><span data-stu-id="b9c87-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\\windows\\system32>`
  
<span data-ttu-id="b9c87-p113">Em outras palavras, não parecerá que algo mudou. Para verificar se a licença foi atribuída ao usuário, execute um comando como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b9c87-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="b9c87-166">Se tudo tiver ocorrido conforme esperado, você verá a propriedade isLicensed de Brenda definida como True:</span><span class="sxs-lookup"><span data-stu-id="b9c87-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!SECURITY NOTE]<span data-ttu-id="b9c87-p114"> Boa pergunta: e se você errar e tentar atribuir a licença a um usuário que já tenha uma licença? Um único usuário ficará com duas licenças? > A resposta rápida é não. O Office 365 não permite que você atribua mais de uma licença ao mesmo usuário. (Para falar a verdade, mais de uma licença do mesmo plano de licença, que fique bem claro). Se tentar fazer isso, seu comando falhará e você verá a seguinte mensagem de erro: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> É verdade que essa mensagem de erro é um pouco confusa: a licença não é inválida, só está sendo atribuída a um usuário que  *já possui*  uma licença. Mas, independente disso, o importante é observar que um usuário não ficará com várias licenças.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="b9c87-p115">Como vimos, é muito fácil usar o Office 365 PowerShell para atribuir uma única licença a um único usuário. E isso nos leva a uma pergunta óbvia: não seria tão ou mais fácil usar o Centro de administração do Office 365 para atribuir uma única licença a um único usuário? Bem, talvez. Isso dependerá, em parte, se você se sente mais confortável usando o Windows PowerShell ou usando o Centro de administração do Office 365. O Windows PowerShell realmente se destaca quando você precisa atribuir várias licenças a vários usuários. Por exemplo, este comando atribui uma licença do Office 365 a qualquer de seus usuários que ainda não tenha licença:</span><span class="sxs-lookup"><span data-stu-id="b9c87-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="b9c87-p116">No comando anterior, usamos **Get-MsolUser** e o parâmetro _UnlicensedUsersOnly_ para obtermos um conjunto de todas as contas de usuário não licenciadas. Então, passamos esse conjunto para o cmdlet **Set-MsolUserLicense**. Por sua vez, **Set-MsolUserLicense** atribui uma licença (retirada do plano de licenciamento `litwareinc:ENTERPRISEPACK`) a cada usuário no conjunto.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="b9c87-p117">Mas e se você tiver cinco usuários não licenciados e apenas uma licença disponível? Nesse caso, **Set-MsolUserLicense** dará a licença disponível ao primeiro usuário retornado por **Get-MsolUser**. Então, **Set-MsolUserLicense** tentará atribuir diligentemente uma licença aos outros quatro usuários, mas todas as quatro tentativas falharão, gerando a seguinte mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="b9c87-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="b9c87-p118">Em outras palavras, MsolUserLicense não falhará simplesmente. Em vez disso, ele atribuirá todas as licenças possíveis. Só então falhará.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="b9c87-p119">Vamos tentar outro exemplo. Talvez você queira atribuir uma licença a todos os usuários no departamento de vendas. Sem problema:</span><span class="sxs-lookup"><span data-stu-id="b9c87-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="b9c87-189">Ou, se quiser fazer algo mais elaborado (e quiser manter um mínimo de mensagens de erro e de processamento de computação), apenas atribua uma licença a usuários não licenciados do departamento de vendas:</span><span class="sxs-lookup"><span data-stu-id="b9c87-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="b9c87-p120">Afinal, de nada serve tentar licenciar usuários que já têm uma licença. Já vimos que isso não funciona.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="b9c87-p121">Eis outro exemplo. Talvez você queira licenciar todos os usuários no Brasil que atualmente não têm uma licença do Office 365. Nesse caso:</span><span class="sxs-lookup"><span data-stu-id="b9c87-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="b9c87-195">E assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b9c87-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b9c87-p122">Quanto tempo demora para executar um comando que, digamos, emite licenças a todos os usuários não licenciados? É difícil dizer. Depende de várias coisas, desde a quantidade de usuários até a velocidade da sua conexão de rede. Se tiver algumas centenas de usuários para licenciar, será razoavelmente rápido (isto é, não deve levar mais do que um minuto ou dois). Se tiver 10 mil usuários, obviamente demorará mais. Mas não chega nem perto do tempo que demoraria para atribuir licenças a 10 mil usuários usando o Centro de administração do Office 365.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="b9c87-p123">Já que falamos nisso, tome cuidado com o seguinte ao atribuir licenças: se um usuário não tiver um valor configurado para a propriedade **UsageLocation** mencionada anteriormente, não será possível atribuir uma licença do Office 365 a ele. Em vez disso, você receberá uma mensagem de erro similar a esta:</span><span class="sxs-lookup"><span data-stu-id="b9c87-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="b9c87-p124">De uma forma redundante, essa mensagem de erro nos informa que o usuário em questão não tem um **UsageLocation** atribuído. Como você já deve ter adivinhado, a propriedade **UsageLocation** (que indica a região ou o país em que o usuário geralmente utiliza o Office 365) é extremamente importante. Por quê? Isso acontece porque os serviços disponíveis dependem do pacote de licenciamento adquirido e do local em que o usuário reside: devido a normas e regulamentações locais, alguns serviços podem não estar disponíveis a alguns usuários. Se um usuário não tem um **UsageLocation**, o Office 365 não tem como saber quais serviços podem ser legalmente expostos a ele. Portanto, o Office 365 não pode oferecer serviços ao usuário, pelo menos não até que o **UsageLocation** tenha sido especificado.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b9c87-p125">Ao configurar uma conta de usuário, você saberá imediatamente se há restrições de licença associadas a uma parte específica do mundo. Por exemplo, se você alterar o **UsageLocation** de um usuário licenciado para o Irã (`IR`), o comando falhará, gerando a seguinte mensagem de erro: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> Isso ocorre porque o Office 365 não está disponível atualmente para usuários do Irã. Para mais informações, confira [Sobre restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730). A propósito, o Office 365 usa o código de país com duas letras gerado pela ISO (International Organization for Standardization, Organização Internacional para Padronização). Você encontra esses códigos no [Site da ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span><span class="sxs-lookup"><span data-stu-id="b9c87-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="b9c87-214">Se você quiser verificar se determinado usuário tem um **UsageLocation**, use um comando similar a este:</span><span class="sxs-lookup"><span data-stu-id="b9c87-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="b9c87-215">Ou você pode obter uma lista de todos os usuários que não têm um **UsageLocation** com este comando:</span><span class="sxs-lookup"><span data-stu-id="b9c87-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="b9c87-p126">Quando você atribui uma licença a um usuário, ele terá acesso, por padrão, a todos os serviços do Office 365 aos quais sua organização tem acesso. Por exemplo, se você comprou licenças para o Office 365 Enterprise E3, seu usuário licenciado recentemente terá acesso automático a serviços como o Exchange Online, o Skype for Business online e o SharePoint Online. Se você preferir limitar o acesso de um usuário a esses serviços (por exemplo, talvez você queira que um usuário tenha acesso ao SharePoint Online, mas  *não*  ao Exchange Online e ao Skype for Business online), confira o artigo [Desabilitar o acesso a serviços com o PowerShell do Office 365](disable-access-to-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b9c87-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="b9c87-219">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="b9c87-219">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="b9c87-p127">![O ícone pequeno do LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Começando a usar o Office 365?**         Descubra cursos em vídeo gratuitos para [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), oferecidos pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="b9c87-p127">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="b9c87-222">Veja também</span><span class="sxs-lookup"><span data-stu-id="b9c87-222">See Also</span></span>
<span data-ttu-id="b9c87-223"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="b9c87-223"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="b9c87-224">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b9c87-224">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="b9c87-225">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9c87-225">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b9c87-226">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9c87-226">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b9c87-227">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9c87-227">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b9c87-228">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9c87-228">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="b9c87-229">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="b9c87-229">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="b9c87-230">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="b9c87-230">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="b9c87-231">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="b9c87-231">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="b9c87-232">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="b9c87-232">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="b9c87-233">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="b9c87-233">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="b9c87-234">Select-Object</span><span class="sxs-lookup"><span data-stu-id="b9c87-234">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="b9c87-235">Where-Object</span><span class="sxs-lookup"><span data-stu-id="b9c87-235">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

