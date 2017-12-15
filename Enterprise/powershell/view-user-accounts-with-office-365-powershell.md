---
title: "Exibir as contas de usuário com o Office 365 PowerShell"
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "Resumo: Assista, listar ou exibir suas contas de usuário de diversas maneiras com o Office 365 PowerShell."
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="0e126-103">Exibir as contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e126-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="0e126-104">**Resumo:** Exibir, listar ou exibir suas contas de usuário de diversas maneiras com o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e126-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="0e126-105">Embora você possa usar o Centro de administração do Office 365 para exibir as contas para seu locatário do Office 365, você também pode usar o Office 365 PowerShell e fazer algumas coisas que não é possível o Centro de administração do Office 365.</span><span class="sxs-lookup"><span data-stu-id="0e126-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="0e126-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="0e126-106">Before you begin</span></span>

<span data-ttu-id="0e126-p101">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="0e126-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="0e126-109">Exibir informações da conta de usuário do Office 365</span><span class="sxs-lookup"><span data-stu-id="0e126-109">Display Office 365 user account information</span></span>

<span data-ttu-id="0e126-110">Para exibir a lista completa das contas de usuário, execute este comando no prompt de comando seu Office 365 PowerShell ou o ambiente de Script integrado PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="0e126-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="0e126-111">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="0e126-111">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="0e126-p102">O cmdlet **Get-MsolUser** também tem um conjunto de parâmetros para filtrar o conjunto de contas de usuário exibida. Por exemplo, para a lista de usuários não licenciados (usuários que foram adicionados ao Office 365, mas ainda não foram licenciados para usar qualquer um dos serviços), execute este comando.</span><span class="sxs-lookup"><span data-stu-id="0e126-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="0e126-114">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="0e126-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="0e126-115">Para obter mais informações sobre parâmetros adicionais para filtrar a exibição o conjunto de contas de usuário exibida, consulte [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span><span class="sxs-lookup"><span data-stu-id="0e126-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="0e126-p103">Para ser mais seletiva sobre a lista de contas para exibir, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-MsolUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Office 365 PowerShell para obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="0e126-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="0e126-119">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="0e126-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0e126-120">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0e126-p104">Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="0e126-123">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="0e126-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="0e126-p105">A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="0e126-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="0e126-p106">Por exemplo, nessa lista, **Cidade** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários mora em Londres:</span><span class="sxs-lookup"><span data-stu-id="0e126-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="0e126-p107">A sintaxe para o cmdlet **Where-Object** mostrada neste exemplo é **Where-Object {$\_.** [nome de propriedade de conta do usuário] [operador de comparação] [valor] **}**. > [operador de comparação] é **-eq** for igual a, **-ne** para não é igual a, **-lt** for menor que, **-gt** para maior e outros > [valor] normalmente é uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$Null** para não for especificado > consulte [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0e126-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="0e126-131">Você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0e126-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="0e126-132">Selecionar as propriedades da conta de usuário a serem exibidas</span><span class="sxs-lookup"><span data-stu-id="0e126-132">Select the user account properties to display</span></span>

<span data-ttu-id="0e126-133">O cmdlet [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) por padrão exibe três propriedades de contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="0e126-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="0e126-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="0e126-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="0e126-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0e126-135">DisplayName</span></span>
    
- <span data-ttu-id="0e126-136">isLicensed</span><span class="sxs-lookup"><span data-stu-id="0e126-136">isLicensed</span></span>
    
<span data-ttu-id="0e126-p108">Se você precisar propriedades adicionais, como o departamento que o usuário trabalha e o país/região onde o usuário usa os serviços do Office 365, você pode executar o **Get-MsolUser** em combinação com o cmdlet **Select-Object** para especificar a lista de conta de usuário Propriedades. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="0e126-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="0e126-139">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="0e126-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0e126-140">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0e126-141">Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="0e126-142">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="0e126-142">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

<span data-ttu-id="0e126-p109">O cmdlet **Select-Object** permite que você escolher as propriedades que você deseja exibir um comando. Para ver todas as propriedades para contas de usuário, use o caractere curinga (*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="0e126-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="0e126-p110">Para ser mais seletiva sobre a lista de contas para exibir, você também pode usar o cmdlet **Where-Object** . Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="0e126-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="0e126-148">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="0e126-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0e126-149">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0e126-p111">Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e enviar as informações resultantes para o próximo comando ( **|** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="0e126-152">Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="0e126-153">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="0e126-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="0e126-154">Use o módulo do Azure Active Directory PowerShell V2 para exibir as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="0e126-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="0e126-p112">Para exibir propriedades de contas de usuário com o módulo do Azure Active Directory PowerShell V2, você deve usar o cmdlet [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Mas, primeiro, você deve se conectar à sua assinatura. Para ver as instruções, consulte[Connect com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="0e126-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="0e126-158">Exibir informações da conta de usuário do Office 365</span><span class="sxs-lookup"><span data-stu-id="0e126-158">Display Office 365 user account information</span></span>

<span data-ttu-id="0e126-159">Para exibir a lista completa das contas de usuário, execute este comando no prompt de comando seu Office 365 PowerShell ou o ambiente de Script integrado PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="0e126-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="0e126-160">O cmdlet **Get-AzureADUser** por padrão exibe três propriedades de contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="0e126-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="0e126-161">ObjectID</span><span class="sxs-lookup"><span data-stu-id="0e126-161">ObjectID</span></span>
    
- <span data-ttu-id="0e126-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0e126-162">DisplayName</span></span>
    
- <span data-ttu-id="0e126-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="0e126-163">UserPrincipalName</span></span>
    
<span data-ttu-id="0e126-p113">Para ser mais seletiva sobre a lista de contas para exibir, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-AzureADUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Office 365 PowerShell para obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="0e126-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="0e126-167">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="0e126-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0e126-168">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0e126-p114">Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="0e126-p115">A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibir todos eles para uma conta de usuário específico, uma página de cada vez ( **mais** ). Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="0e126-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="0e126-p116">Por exemplo, **Cidade** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários mora em Londres:</span><span class="sxs-lookup"><span data-stu-id="0e126-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="0e126-p117">A sintaxe para o cmdlet **Where-Object** mostrada neste exemplo é **Where-Object {$\_.** [nome de propriedade de conta do usuário] [operador de comparação] [valor] **}**. > [operador de comparação] é **-eq** for igual a, **-ne** para não é igual a, **-lt** for menor que, **-gt** para maior e outros > [valor] normalmente é uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$Null** para não for especificado > consulte[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0e126-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="0e126-178">Selecionar as propriedades da conta de usuário a serem exibidas</span><span class="sxs-lookup"><span data-stu-id="0e126-178">Select the user account properties to display</span></span>

<span data-ttu-id="0e126-p118">O cmdlet **Get-AzureADUser** por padrão exibe as propriedades ObjectID, DisplayName e UserPrincipalName das contas de usuário. Se você precisar propriedades adicionais, como o departamento que o usuário trabalha e o país/região onde o usuário usa os serviços do Office 365, é possível executar **Get-AzureADUser** em combinação com o cmdlet **Select-Object** para especificar a lista de usuário Propriedades da conta. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="0e126-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="0e126-182">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="0e126-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0e126-183">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0e126-184">Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="0e126-p119">Para ser mais seletiva sobre a lista de contas para exibir, você também pode usar o cmdlet **Where-Object** . Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="0e126-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="0e126-187">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="0e126-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0e126-188">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0e126-p120">Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e enviar as informações resultantes para o próximo comando ( **|** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="0e126-191">Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="0e126-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="0e126-192">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="0e126-192">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="0e126-p121">![O ícone pequeno do LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Começando a usar o Office 365?**         Descubra cursos em vídeo gratuitos para [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), oferecidos pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="0e126-p121">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="0e126-195">See also</span><span class="sxs-lookup"><span data-stu-id="0e126-195">See also</span></span>

#### 

[<span data-ttu-id="0e126-196">Gerenciar contas de usuário e licenças usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="0e126-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="0e126-197">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e126-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0e126-198">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e126-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

