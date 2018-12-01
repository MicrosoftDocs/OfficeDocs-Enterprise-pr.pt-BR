---
title: Exibir as contas de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Resumo: Assista, listar ou exibir suas contas de usuário de diversas maneiras com o Office 365 PowerShell.'
ms.openlocfilehash: f2743197456cc56f654e99e682108230420384c9
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123248"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="72fd2-103">Exibir as contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="72fd2-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="72fd2-104">**Resumo:** Exiba suas contas de usuário de diversas maneiras com o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72fd2-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="72fd2-105">Embora você possa usar o Centro de administração do Office 365 para exibir as contas para seu locatário do Office 365, você também pode usar o Office 365 PowerShell e fazer algumas coisas que não é possível o Centro de administração do Office 365.</span><span class="sxs-lookup"><span data-stu-id="72fd2-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="72fd2-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="72fd2-106">Before you begin</span></span>

<span data-ttu-id="72fd2-p101">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="72fd2-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information-with-azure-active-directory-powershell-for-graph"></a><span data-ttu-id="72fd2-109">Exibir informações de conta de usuário do Office 365 com o Windows Azure Active Directory PowerShell para gráfico</span><span class="sxs-lookup"><span data-stu-id="72fd2-109">Display Office 365 user account information with Azure Active Directory PowerShell for Graph</span></span> 

<span data-ttu-id="72fd2-110">As seções a seguir descrevem como exibir informações da conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="72fd2-110">The following sections describe how to display user account information.</span></span>

### <a name="all-accounts"></a><span data-ttu-id="72fd2-111">Todas as contas</span><span class="sxs-lookup"><span data-stu-id="72fd2-111">All accounts</span></span>

<span data-ttu-id="72fd2-112">Para exibir a lista completa das contas de usuário, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="72fd2-112">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="72fd2-113">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="72fd2-113">You should see information similar to this:</span></span>
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="a-specific-account"></a><span data-ttu-id="72fd2-114">Uma conta específica</span><span class="sxs-lookup"><span data-stu-id="72fd2-114">A specific account</span></span>

<span data-ttu-id="72fd2-115">Para exibir uma conta de usuário específica, preencha o nome principal do usuário (UPN) da conta de usuário, remova o "<" e ">" caracteres e execute este comando:</span><span class="sxs-lookup"><span data-stu-id="72fd2-115">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="additional-property-values-for-a-specific-account"></a><span data-ttu-id="72fd2-116">Valores de propriedades adicionais para uma conta específica</span><span class="sxs-lookup"><span data-stu-id="72fd2-116">Additional property values for a specific account</span></span>

<span data-ttu-id="72fd2-117">Por padrão, o cmdlet **Get-AzureADUser** exibe apenas as propriedades ObjectID, DisplayName e UserPrincipalName das contas.</span><span class="sxs-lookup"><span data-stu-id="72fd2-117">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="72fd2-p102">Para ser mais seletiva sobre a lista de propriedades para exibir, você pode usar o cmdlet **Select-Object** em combinação com o cmdlet **Get-AzureADUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa o Azure Active Directory PowerShell para o gráfico obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe o DisplayName, departamento e UsageLocation para cada conta de usuário:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p102">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="72fd2-121">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="72fd2-121">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="72fd2-122">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-122">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="72fd2-123">Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-123">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="72fd2-p103">Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (\*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p103">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="72fd2-126">Como outro exemplo, é possível verificar o status ativado de uma conta de usuário específico com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="72fd2-126">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="some-accounts-based-on-a-common-property"></a><span data-ttu-id="72fd2-127">Algumas contas com base em uma propriedade comum</span><span class="sxs-lookup"><span data-stu-id="72fd2-127">Some accounts based on a common property</span></span>

<span data-ttu-id="72fd2-p104">Para ser mais seletiva sobre a lista de contas para exibir, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-AzureADUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa o Azure Active Directory PowerShell para o gráfico obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p104">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="72fd2-131">Este comando instrui o Azure Active Directory PowerShell para o gráfico para:</span><span class="sxs-lookup"><span data-stu-id="72fd2-131">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="72fd2-132">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-132">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="72fd2-p105">Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( \*\* $ \_. UsageLocation\*\* ) não é especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-p105">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="72fd2-p106">A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (\*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p106">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="72fd2-p107">Por exemplo, nessa lista, **Cidade** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários mora em Londres:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p107">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="72fd2-p108">A sintaxe para o cmdlet **Where-Object** mostrada neste exemplo é **Where-Object {$\_.** [nome de propriedade de conta do usuário] [operador de comparação] [valor] **}**. > [operador de comparação] é **-eq** for igual a, **-ne** para não é igual a, **-lt** for menor que, **-gt** para maior e outros.  [valor] é geralmente uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$Null** para não for especificado > consulte [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="72fd2-p108">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="display-office-365-user-account-information-with-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="72fd2-143">Exibir informações de conta de usuário do Office 365 com o Microsoft Azure Active Directory módulo para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="72fd2-143">Display Office 365 user account information with Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="72fd2-144">As seções a seguir descrevem como exibir informações da conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="72fd2-144">The following sections describe how to display user account information.</span></span>

### <a name="all-accounts"></a><span data-ttu-id="72fd2-145">Todas as contas</span><span class="sxs-lookup"><span data-stu-id="72fd2-145">All accounts</span></span>

<span data-ttu-id="72fd2-146">Para exibir a lista completa das contas de usuário, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="72fd2-146">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="72fd2-147">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="72fd2-147">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="72fd2-p109">O cmdlet **Get-MsolUser** também tem um conjunto de parâmetros para filtrar o conjunto de contas de usuário exibida. Por exemplo, para a lista de usuários não licenciados (usuários que foram adicionados ao Office 365, mas ainda não foram licenciados para usar qualquer um dos serviços), execute este comando.</span><span class="sxs-lookup"><span data-stu-id="72fd2-p109">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="72fd2-150">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="72fd2-150">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="72fd2-151">Para obter mais informações sobre parâmetros adicionais para filtrar a exibição o conjunto de contas de usuário exibida, consulte [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="72fd2-151">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="a-specific-account"></a><span data-ttu-id="72fd2-152">Uma conta específica</span><span class="sxs-lookup"><span data-stu-id="72fd2-152">A specific account</span></span>

<span data-ttu-id="72fd2-153">Para exibir uma conta de usuário específica, preencha o nome principal do usuário (UPN) da conta de usuário, remova o "<" e ">" caracteres e execute este comando:</span><span class="sxs-lookup"><span data-stu-id="72fd2-153">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="some-accounts-based-on-a-common-property"></a><span data-ttu-id="72fd2-154">Algumas contas com base em uma propriedade comum</span><span class="sxs-lookup"><span data-stu-id="72fd2-154">Some accounts based on a common property</span></span>

<span data-ttu-id="72fd2-p110">Para ser mais seletiva sobre a lista de contas para exibir, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-MsolUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Office 365 PowerShell para obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p110">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="72fd2-158">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="72fd2-158">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="72fd2-159">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-159">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="72fd2-p111">Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( \*\* $ \_. UsageLocation\*\* ) não é especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="72fd2-162">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="72fd2-162">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="72fd2-p112">A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (\*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p112">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="72fd2-p113">Por exemplo, nessa lista, **Cidade** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários mora em Londres:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p113">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="72fd2-p114">A sintaxe para o cmdlet **Where-Object** mostrada neste exemplo é **Where-Object {$\_.** [nome de propriedade de conta do usuário] [operador de comparação] [valor] **}**.  [operador de comparação] é **-eq** for igual a, **-ne** para não é igual a, **-lt** for menor que, **-gt** para maior e outros.  [valor] é geralmente uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$Null** para não for especificado. Para obter mais informações, consulte o [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="72fd2-p114">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="72fd2-173">Você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="72fd2-173">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="additional-property-values-for-accounts"></a><span data-ttu-id="72fd2-174">Valores de propriedades adicionais para contas</span><span class="sxs-lookup"><span data-stu-id="72fd2-174">Additional property values for accounts</span></span>

<span data-ttu-id="72fd2-175">O cmdlet **Get-MsolUser** por padrão exibe três propriedades de contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="72fd2-175">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="72fd2-176">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="72fd2-176">UserPrincipalName</span></span>
    
- <span data-ttu-id="72fd2-177">DisplayName</span><span class="sxs-lookup"><span data-stu-id="72fd2-177">DisplayName</span></span>
    
- <span data-ttu-id="72fd2-178">isLicensed</span><span class="sxs-lookup"><span data-stu-id="72fd2-178">isLicensed</span></span>
    
<span data-ttu-id="72fd2-p115">Se você precisar propriedades adicionais, como o departamento que o usuário trabalha e o país/região onde o usuário usa os serviços do Office 365, você pode executar o **Get-MsolUser** em combinação com o cmdlet **Select-Object** para especificar a lista de conta de usuário Propriedades. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p115">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="72fd2-181">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="72fd2-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="72fd2-182">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="72fd2-183">Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-183">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="72fd2-184">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="72fd2-184">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="72fd2-p116">O cmdlet **Select-Object** permite que você escolher as propriedades que você deseja exibir um comando. Para ver todas as propriedades para contas de usuário, use o caractere curinga (\*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p116">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="72fd2-p117">Para ser mais seletiva sobre a lista de contas para exibir, você também pode usar o cmdlet **Where-Object** . Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="72fd2-p117">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="72fd2-190">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="72fd2-190">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="72fd2-191">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-191">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="72fd2-p118">Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e enviar as informações resultantes para o próximo comando ( **|** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( \*\* $ \_. UsageLocation\*\* ) não é especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-p118">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="72fd2-194">Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="72fd2-194">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="72fd2-195">Você deverá ver informações parecidas com estas:</span><span class="sxs-lookup"><span data-stu-id="72fd2-195">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="72fd2-p119">Se você estiver usando a sincronização de diretórios para criar e gerenciar os usuários do Office 365, você pode exibir qual um usuário do Office 365 tenha sido projetado de conta local. A seguir pressupõe que se conectar do Azure AD foi configurada para usar a âncora de fonte padrão do ObjectGUID (para obter mais informações sobre como configurar uma âncora de origem, consulte [Connect do Azure AD: conceitos de projeto](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) e pressupõe que o módulo do Active Directory para o powershell tem foi instalado (consulte [Ferramentas RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="72fd2-p119">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="new-to-office-365"></a><span data-ttu-id="72fd2-198">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="72fd2-198">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a><span data-ttu-id="72fd2-199">Confira também</span><span class="sxs-lookup"><span data-stu-id="72fd2-199">See also</span></span>

[<span data-ttu-id="72fd2-200">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="72fd2-200">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="72fd2-201">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="72fd2-201">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="72fd2-202">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="72fd2-202">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

