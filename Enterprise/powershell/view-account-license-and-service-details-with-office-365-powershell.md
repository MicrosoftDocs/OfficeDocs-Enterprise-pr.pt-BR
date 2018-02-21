---
title: "Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell"
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: "Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários."
ms.openlocfilehash: 69784b43e6e2b24f776d07a937877e5ae0c74888
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="60aae-103">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="60aae-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="60aae-104">**Resumo:** Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários.</span><span class="sxs-lookup"><span data-stu-id="60aae-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="60aae-p101">No Office 365, licencia para planos de licenciamento (também chamado de SKUs ou do Office 365 estiver planejando) conceder aos usuários acesso aos serviços do Office 365 que são definidos para esses planos. No entanto, um usuário pode não ter acesso a todos os serviços que estão disponíveis em uma licença atualmente atribuído a eles. Você pode usar o PowerShell do Office 365 para exibir o status dos serviços em contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="60aae-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="60aae-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="60aae-108">Before you begin</span></span>
<span data-ttu-id="60aae-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="60aae-109"></span></span>

- <span data-ttu-id="60aae-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="60aae-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="60aae-112">Use os comandos `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` para encontrar as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="60aae-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="60aae-113">Os planos de licenciamento que estão disponíveis na sua organização.</span><span class="sxs-lookup"><span data-stu-id="60aae-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="60aae-114">Os serviços que estão disponíveis em cada plano de licenciamento e a ordem em que eles estão listados (o número do índice).</span><span class="sxs-lookup"><span data-stu-id="60aae-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="60aae-115">Para obter mais informações sobre o licenciamento planos, licenças e serviços, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="60aae-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="60aae-116">Use o comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` para encontrar as licenças atribuídas a um usuário e a ordem na qual eles estão listados (o número de índice).</span><span class="sxs-lookup"><span data-stu-id="60aae-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="60aae-117">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="60aae-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="60aae-118">A versão curta (instruções sem explicações)</span><span class="sxs-lookup"><span data-stu-id="60aae-118">The short version (instructions without explanations)</span></span>
<span data-ttu-id="60aae-119"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="60aae-119"></span></span>

<span data-ttu-id="60aae-120">Para exibir todos os serviços do Office 365 PowerShell que um usuário tem acesso ao, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="60aae-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="60aae-p103">Este exemplo mostra os serviços aos quais o usuário BelindaN@litwareinc.com tem acesso. Mostra os serviços que estão associados a todas as licenças são atribuídas à sua conta.</span><span class="sxs-lookup"><span data-stu-id="60aae-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="60aae-123">Este exemplo mostra os serviços aos quais a usuária BrendaF@litwareinc.com tem acesso a partir da primeira licença atribuída à conta dela (o número de índice é 0).</span><span class="sxs-lookup"><span data-stu-id="60aae-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="60aae-124">Para localizar todos os usuários licenciados que foram habilitados ou não habilitados para serviços específicos, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="60aae-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="60aae-125">Esses exemplos utilizam as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="60aae-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="60aae-126">A licença que fornece acesso aos serviços do Office 365 que estamos interessados em é a primeira licença atribuída a todos os usuários (o número de índice é 0).</span><span class="sxs-lookup"><span data-stu-id="60aae-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="60aae-p104">Os serviços do Office 365 que estamos interessados em são Skype para Business Online e o Exchange Online. As licenças que estão associados com o plano de licenciamento, Skype para Business Online é o serviço 6º listado (o número de índice é de 5), e o Exchange Online é o serviço de 9 listados (o número de índice é 8).</span><span class="sxs-lookup"><span data-stu-id="60aae-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="60aae-129">Este exemplo retorna todas licenciados usuários habilitados para o Skype para Business Online e o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="60aae-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="60aae-130">Este exemplo retorna todos os usuários licenciados que não estão habilitados para o Skype para Business Online ou Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="60aae-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="60aae-131">A versão longa (instruções com explicações detalhadas)</span><span class="sxs-lookup"><span data-stu-id="60aae-131">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="60aae-132"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="60aae-132"></span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="60aae-133">Encontre os serviços do Office 365 PowerShell que um usuário tem acesso ao</span><span class="sxs-lookup"><span data-stu-id="60aae-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="60aae-p105">É importante, obviamente, para que você sabe quais usuários tiverem sido emitidos licenças do Office 365 e os usuários que ainda não. (Consulte o artigo [Exibir usuários licenciados e não licenciados com o Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) para obter mais informações). No entanto, simplesmente ter uma licença do Office 365 não informa nada sobre o que esse usuário pode realmente fazer com o Office 365. Pode ele usar Exchange Online ou Skype para Business Online? Esse usuário pode acessar o SharePoint Online? Ele tem acesso ao Office Professional Plus? Ter uma licença simplesmente significa que o usuário tem o potencial para acessar esses serviços. No entanto, os recursos disponíveis para um usuário dependem os serviços que foram habilitados em sua licença.</span><span class="sxs-lookup"><span data-stu-id="60aae-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="60aae-p106">Como podemos determinar a quais recursos do Office 365 um usuário tem acesso? Para fazer isso precisamos executar um comando semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="60aae-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="60aae-144">Neste comando, estamos usando o cmdlet **Get-MsolUser** para retornar informações sobre a conta BelindaN@litwareinc.com. Depois que podemos tiver retornado essa informação, podemos, em seguida, canalize os dados da conta para o cmdlet **Select-Object** e solicite **Select-Object** para "expandir" o valor da propriedade **licenças** :</span><span class="sxs-lookup"><span data-stu-id="60aae-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="60aae-p107">Por que fazemos isso? Bem, por padrão, as **licenças** de propriedade nos informa apenas o nome do pacote de licenciamento onde originou a licença de Belinda de:</span><span class="sxs-lookup"><span data-stu-id="60aae-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="60aae-147">"Expandir" **essa propriedade** nos dá um pouco mais informações:</span><span class="sxs-lookup"><span data-stu-id="60aae-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="60aae-148">E, em seguida, expandindo a propriedade **ServiceStatus** podemos obter ainda mais informações:</span><span class="sxs-lookup"><span data-stu-id="60aae-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="60aae-149">****Plano de serviço****</span><span class="sxs-lookup"><span data-stu-id="60aae-149">****Service plan****</span></span>|<span data-ttu-id="60aae-150">****Descrição****</span><span class="sxs-lookup"><span data-stu-id="60aae-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="60aae-151">Sway</span><span class="sxs-lookup"><span data-stu-id="60aae-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="60aae-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="60aae-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="60aae-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="60aae-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="60aae-154">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="60aae-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="60aae-155">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="60aae-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="60aae-156">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="60aae-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="60aae-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="60aae-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="60aae-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="60aae-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="60aae-159">Plano 2 do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="60aae-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="60aae-p108">Acha que está digitando muito? Bem, se você conseguir aguentar uma pouco as chatices do Windows PowerShell, você poderá executar a versão compacta do comando em vez disso: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="60aae-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="60aae-p109">Caso você esteja se perguntando, podemos podem "expandir" **essa propriedade** como **licenças** é uma propriedade de valores múltiplos: é uma única propriedade que pode armazenar vários valores. Quando há que expandimos podemos simplesmente fazer drill down em um valor de propriedade recebe esses valores adicionais que, por padrão, não são exibidos na tela.</span><span class="sxs-lookup"><span data-stu-id="60aae-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="60aae-p110">Então como podemos saber que um valor é uma propriedade de vários valores? Bem, para descobrir isso, tente executar um comando similar a esta: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> o cmdlet **Get-member** retorna informações sobre o objeto em si; Nesse caso, as informações sobre a propriedade valores que formam um objeto de conta de usuário. Aqui está o que **Get-Member** tem a dizer sobre a propriedade **licenças** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> se a definição da propriedade nos diz algo sobre conjuntos (neste caso, `System.Collections.Generic.List`), então você sabe que você está lidando com uma propriedade de vários valores.</span><span class="sxs-lookup"><span data-stu-id="60aae-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="60aae-p111">Então o que isso significa? Para responder a isso, vamos primeiro dar uma olhada nas informações retornadas pelo cmdlet **Get-MsolUser** :</span><span class="sxs-lookup"><span data-stu-id="60aae-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
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

<span data-ttu-id="60aae-169">E vamos também dar uma olhada em uma tabela que explica o que esses planos de serviço estranhos representam:</span><span class="sxs-lookup"><span data-stu-id="60aae-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="60aae-170">****Plano de serviço****</span><span class="sxs-lookup"><span data-stu-id="60aae-170">****Service plan****</span></span>|<span data-ttu-id="60aae-171">****Descrição****</span><span class="sxs-lookup"><span data-stu-id="60aae-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="60aae-172">Sway</span><span class="sxs-lookup"><span data-stu-id="60aae-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="60aae-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="60aae-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="60aae-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="60aae-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="60aae-175">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="60aae-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="60aae-176">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="60aae-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="60aae-177">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="60aae-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="60aae-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="60aae-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="60aae-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="60aae-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="60aae-180">Plano 2 do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="60aae-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="60aae-p112">Entendeu tudo?  `MCOSTANDARD` destina-se apenas um nome interno programação para Skype Online de negócios, enquanto `OFFICESUSBCRIPTION` é apenas o nome interno programação para Office Professional Plus. Não é a coisa mais intuitiva no mundo, mas desde que você mantenha esta tabela úteis não terá muitos problemas quando se trata de trabalhar com os serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="60aae-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="60aae-p113">Mas espere: há mais. Como podemos aprendeu no artigo [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), se o **ProvisioningStatus** estiver definida como `Success` , isso significa que o serviço foi habilitado totalmente; Por exemplo se `MCOSTANDARD` estiver definida como `Success` , isso significa que o usuário pode acessar o Skype para Business Online. Se o **ProvisioningStatus** estiver definida como `PendingInput` , isso significa que o Office 365 ainda está processando a solicitação de serviço; No entanto, o usuário pode fazer logon e acessar o serviço enquanto a solicitação termina o processamento normalmente. ( `YAMMER_ENTERPRISE` sempre serão exibidos como `PendingInput`, mas isso é Okey: não para de que um usuário faça logon no Yammer).</span><span class="sxs-lookup"><span data-stu-id="60aae-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="60aae-188">Os usuários podem instalar e ativar uma nova instalação do Office Professional Plus enquanto `OFFICESUBSCRIPTION` que se situa a `PendingInput` estado.</span><span class="sxs-lookup"><span data-stu-id="60aae-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="60aae-189">E, obviamente, é um serviço é definido como `Disabled` isso significa que o serviço em questão não está disponível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="60aae-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="60aae-190">Localizar usuários que têm acesso a serviços específicos do Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="60aae-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="60aae-p114">Um artigo separados, vimos como você pode usar o Office 365 PowerShell para desabilitar o acesso do usuário aos serviços. (Se você tiver perdido desse artigo, consulte [Desabilitar o acesso aos serviços do Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Isso leva a uma pergunta óbvia: há alguma maneira para determinar quais *usuários* (ou seja, mais de um usuário) têm quais serviços habilitados ou desabilitados?</span><span class="sxs-lookup"><span data-stu-id="60aae-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="60aae-p115">Esperávamos que alguém fizesse que. Para responder à pergunta, vamos revisar a tabela de serviços que primeiro examinamos no artigo [serviços com o Office 365 PowerShell e exibir as licenças](view-licenses-and-services-with-office-365-powershell.md) para nosso plano de licenciamento disponível apenas `litwareinc:ENTERPRISEPACK`:</span><span class="sxs-lookup"><span data-stu-id="60aae-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="60aae-196">****Plano de serviço****</span><span class="sxs-lookup"><span data-stu-id="60aae-196">****Service plan****</span></span>|<span data-ttu-id="60aae-197">****Descrição****</span><span class="sxs-lookup"><span data-stu-id="60aae-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="60aae-198">Sway</span><span class="sxs-lookup"><span data-stu-id="60aae-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="60aae-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="60aae-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="60aae-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="60aae-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="60aae-201">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="60aae-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="60aae-202">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="60aae-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="60aae-203">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="60aae-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="60aae-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="60aae-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="60aae-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="60aae-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="60aae-206">Plano 2 do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="60aae-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="60aae-p116">Como você pode lembrar, o plano de serviço é nada mais que o nome interno de programação para um produto. Por exemplo, `OFFICESUBSCRIPTION`, para o nome de um, é o nome interno de programação para Office Professional Plus. Se `OFFICESUBSCRIPTION` aparece como `SUCCESS` no plano de serviço de um usuário, em seguida, isso significa que o usuário tem permissão para acessar o Office Professional Plus. Se `EXCHANGE_S_ENTERPRISE` está listado como `DISABLED` isso significa que o usuário não é possível usar o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="60aae-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="60aae-210">Os usuários podem instalar e ativar uma nova instalação do Office Professional Plus enquanto `OFFICESUBSCRIPTION` que se situa a `PendingInput` estado.</span><span class="sxs-lookup"><span data-stu-id="60aae-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="60aae-p117">Este é o momento em que a ordem na qual os serviços são exibidos é extremamente importante. Windows PowerShell atribui um número de índice para cada entrada na lista. A primeira entrada é 0, a próxima entrada é 1 e assim por diante. Os resultados são explicados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="60aae-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="60aae-215">Número de índice \* \* \*</span><span class="sxs-lookup"><span data-stu-id="60aae-215">****Index number****</span></span>|<span data-ttu-id="60aae-216">****Plano de serviço****</span><span class="sxs-lookup"><span data-stu-id="60aae-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="60aae-217">0</span><span class="sxs-lookup"><span data-stu-id="60aae-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="60aae-218">1</span><span class="sxs-lookup"><span data-stu-id="60aae-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="60aae-219">2</span><span class="sxs-lookup"><span data-stu-id="60aae-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="60aae-220">3</span><span class="sxs-lookup"><span data-stu-id="60aae-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="60aae-221">4</span><span class="sxs-lookup"><span data-stu-id="60aae-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="60aae-222">5</span><span class="sxs-lookup"><span data-stu-id="60aae-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="60aae-223">6</span><span class="sxs-lookup"><span data-stu-id="60aae-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="60aae-224">7</span><span class="sxs-lookup"><span data-stu-id="60aae-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="60aae-225">8</span><span class="sxs-lookup"><span data-stu-id="60aae-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="60aae-226">Como você pode ver, `SWAY` é o primeiro serviço listado, portanto, ela recebe o número de índice 0.</span><span class="sxs-lookup"><span data-stu-id="60aae-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="60aae-p118">Por que 0 e não 1? Isso é um ponto de programação. Em linguagens de programação índices informam quanto um item é "deslocar" desde o início da matriz. O primeiro item *é* o início da matriz, portanto, seu deslocamento é 0. O segundo item é 1 item desde o início da matriz, portanto, seu deslocamento é 1.</span><span class="sxs-lookup"><span data-stu-id="60aae-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="60aae-p119">Vamos tentar um exemplo. Suponha que gostaríamos de uma lista de todos os usuários licenciados que não tiverem sido habilitados para o Exchange Online. Para fazer isso, podemos usar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="60aae-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="60aae-p120">Sem dúvida, que é um comando de pouca secreto procurando, vamos levar um minuto para explicar como ele funciona. Isso é realmente um comando de duas partes e a primeira parte é muito simple: usamos o cmdlet **Get-MsolUser** para retornar uma coleção de todos os nossos usuários do Office 365 (licenciado e não licenciado):</span><span class="sxs-lookup"><span data-stu-id="60aae-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="60aae-p121">Essa informação é então canalizada para o cmdlet **Where-Object** . **Where-Object** percorre todas as contas de usuário e procura por essas contas que atenderem aos seguintes critérios:</span><span class="sxs-lookup"><span data-stu-id="60aae-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="60aae-p122">A propriedade **isLicensed** é igual a ( `-eq`) `True` ( `$true`). Que permite que os usuários não licenciados eliminar.</span><span class="sxs-lookup"><span data-stu-id="60aae-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="60aae-p123">O valor das licenças **[0]. ServiceStatus [8]. ProvisioningStatus** propriedade for igual a ( `-eq`) `Disabled`. Para fins de nossos imediatas, a parte importante desse nome de propriedade complicado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="60aae-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="60aae-p124">O `[8]` representa o número de índice para o Exchange Online. (Nós sabemos que observando a tabela há alguns minutos). O que ocorre se queríamos localizar todos os usuários habilitados para Skype para Business Online? Bem, o número de índice para Skype para Business Online é 5, portanto, usaríamos esta sintaxe:</span><span class="sxs-lookup"><span data-stu-id="60aae-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="60aae-247">Etc., etc.</span><span class="sxs-lookup"><span data-stu-id="60aae-247">Etc., etc.</span></span>
    
    <span data-ttu-id="60aae-p125">A propósito, `Licenses[0]` indica o plano de licenciamento que queremos a ser analisado. Como o domínio de nosso teste tem apenas um plano de licenciamento isso não importa muito. Mas, suponhamos que tivéssemos que um usuário que tenha sido atribuído licenças de dois diferentes planos de licenciamento. Nesse caso, `Licenses[0]` seria representam o primeiro plano de licenciamento e `Licenses[1]` seria representam o segundo plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="60aae-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="60aae-252">Para encontrar as licenças atribuídas a um usuário e a ordem na qual elas estão listadas, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="60aae-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="60aae-p126">Você consegue ver como isso funciona? O número de índice para o Office Professional Plus é 4; Portanto, este comando retorna uma lista de todos os usuários que não tiverem sido habilitados para o Office Professional Plus:</span><span class="sxs-lookup"><span data-stu-id="60aae-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="60aae-p127">E se queríamos que uma lista de usuários que tiverem sido *habilitados* para o Office Professional Plus? Bem, se você tiver sido habilitado sua **ServiceStatus** será `PendingInput` ou `Success`; em outras palavras, sua **ServiceStatus** será igual *não* ( `-ne`) `Disabled`. Isso significa que tudo o que temos a fazer é levar nosso comando anterior e trocar o `-eq` operador para o `-ne` operador:</span><span class="sxs-lookup"><span data-stu-id="60aae-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="60aae-p128">Como dizem der, que código provavelmente não win concursos de maravilha muitos. E, verdade seja dita, o código pode obter ainda mais tangled. Por exemplo, suponha que queremos procurar usuários que tiverem sido habilitados para ambos os Skype para Business Online e o Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="60aae-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="60aae-p129">Mas não se preocupe muito sobre como gnarly que pode parecer: o mais importante é que, com relativamente pouco esforço, é possível recuperar essas informações. Não é possível obter essa mesma informação usando o Centro de administração do Office 365? Teoricamente, Sim mas, em termos práticos, não. Para obter essa mesma informação usando o Centro de administração do Office 365, você precisaria examinar as informações de licenciamento para cada usuário, um usuário por vez e, em seguida, manualmente ficar atento que tinham sido habilitados para *X* e quem não tivesse. Que seria funcionar, mas vamos sinceramente: se você tiver mais de 10 ou 11 usuários, você não vai fazer isso. É muito tediosas e demoradas.</span><span class="sxs-lookup"><span data-stu-id="60aae-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="60aae-267">É claro que, é por isso que temos o Windows PowerShell: Windows PowerShell ajuda você a se livrar de tarefas tediosas e demoradas, como que.</span><span class="sxs-lookup"><span data-stu-id="60aae-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="60aae-268">Já que estamos falando nisso, aqui está um comando excelente para exibir informações de serviço:</span><span class="sxs-lookup"><span data-stu-id="60aae-268">While we're at it, here's the ultimate command for viewing service information:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

<span data-ttu-id="60aae-p130">E Sim, que é um comando caracter estranho muito. Mas, ele cria um arquivo CSV mostrando todos os usuários e todos seus status de serviço.</span><span class="sxs-lookup"><span data-stu-id="60aae-p130">And yes, that's a very crazy-looking command. But it creates a CSV file showing all of your users and all of their service statuses.</span></span>

  
## <a name="see-also"></a><span data-ttu-id="60aae-271">Confira também</span><span class="sxs-lookup"><span data-stu-id="60aae-271">See also</span></span>
<span data-ttu-id="60aae-272"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="60aae-272"></span></span>

<span data-ttu-id="60aae-273">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="60aae-273">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="60aae-274">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="60aae-274">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="60aae-275">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="60aae-275">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="60aae-276">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="60aae-276">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="60aae-277">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="60aae-277">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="60aae-278">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="60aae-278">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="60aae-279">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="60aae-279">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="60aae-280">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="60aae-280">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="60aae-281">Format-List</span><span class="sxs-lookup"><span data-stu-id="60aae-281">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="60aae-282">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="60aae-282">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="60aae-283">Select-Object</span><span class="sxs-lookup"><span data-stu-id="60aae-283">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="60aae-284">Where-Object</span><span class="sxs-lookup"><span data-stu-id="60aae-284">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="60aae-285">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="60aae-285">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]