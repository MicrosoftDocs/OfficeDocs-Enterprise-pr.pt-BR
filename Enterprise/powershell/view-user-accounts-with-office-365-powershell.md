---
title: Exibir as contas de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
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
description: 'Resumo: exiba, liste ou exiba suas contas de usuário de várias maneiras com o Office 365 PowerShell.'
ms.openlocfilehash: 10b6d209e76f94b8b001718abd35368f9d1bc29c
ms.sourcegitcommit: ae4b3c1e2859991f3b94690f2eb3b2838d7db2d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "30539009"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="b88e2-103">Exibir as contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b88e2-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="b88e2-104">**Resumo:** Exiba suas contas de usuário de várias maneiras com o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88e2-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="b88e2-105">Embora você possa usar o centro de administração do Office 365 para exibir as contas do seu locatário do Office 365, você também pode usar o Office 365 PowerShell e fazer algumas coisas que o centro de administração do Office 365 não pode.</span><span class="sxs-lookup"><span data-stu-id="b88e2-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b88e2-106">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="b88e2-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="b88e2-107">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="b88e2-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="b88e2-108">Exibir todas as contas</span><span class="sxs-lookup"><span data-stu-id="b88e2-108">View all accounts</span></span>

<span data-ttu-id="b88e2-109">Para exibir a lista completa de contas de usuário, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="b88e2-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="b88e2-110">Você deve ver informações semelhantes a estas:</span><span class="sxs-lookup"><span data-stu-id="b88e2-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="b88e2-111">Exibir uma conta específica</span><span class="sxs-lookup"><span data-stu-id="b88e2-111">View a specific account</span></span>

<span data-ttu-id="b88e2-112">Para exibir uma conta de usuário específica, preencha o nome da conta de logon da conta de usuário, também conhecida como nome UPN, remova os caracteres "<" e ">" e execute este comando:</span><span class="sxs-lookup"><span data-stu-id="b88e2-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="b88e2-113">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="b88e2-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="b88e2-114">Exibir valores de propriedade adicionais para uma conta específica</span><span class="sxs-lookup"><span data-stu-id="b88e2-114">View additional property values for a specific account</span></span>

<span data-ttu-id="b88e2-115">Por padrão, o cmdlet **Get-AzureADUser** exibe apenas as propriedades ObjectID, DisplayName e userPrincipalName de accounts.</span><span class="sxs-lookup"><span data-stu-id="b88e2-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="b88e2-116">Para ser mais seletivo sobre a lista de propriedades a serem exibidas, você pode usar o cmdlet **Select-Object** em combinação com o cmdlet **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="b88e2-116">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="b88e2-117">Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Azure Active Directory PowerShell para Graph para obter os resultados de um comando e enviá-lo para o próximo comando.</span><span class="sxs-lookup"><span data-stu-id="b88e2-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b88e2-118">Veja a seguir um exemplo de comando que exibe o DisplayName, o departamento e o UsageLocation para cada conta de usuário:</span><span class="sxs-lookup"><span data-stu-id="b88e2-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="b88e2-119">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="b88e2-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b88e2-120">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="b88e2-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b88e2-121">Exibir apenas o nome da conta de usuário, o departamento e o local de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b88e2-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="b88e2-122">Para ver todas as propriedades de contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (\*) para exibi-los para uma conta de usuário específica.</span><span class="sxs-lookup"><span data-stu-id="b88e2-122">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b88e2-123">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="b88e2-123">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="b88e2-124">Como outro exemplo, você pode verificar o status habilitado de uma conta de usuário específica com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b88e2-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="b88e2-125">Exibir algumas contas com base em uma propriedade comum</span><span class="sxs-lookup"><span data-stu-id="b88e2-125">View some accounts based on a common property</span></span>

<span data-ttu-id="b88e2-126">Para ser mais seletivo sobre a lista de contas a serem exibidas, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="b88e2-126">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="b88e2-127">Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Azure Active Directory PowerShell para Graph para obter os resultados de um comando e enviá-lo para o próximo comando.</span><span class="sxs-lookup"><span data-stu-id="b88e2-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b88e2-128">Veja a seguir um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="b88e2-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b88e2-129">Este comando instrui o Azure Active Directory PowerShell para Graph para:</span><span class="sxs-lookup"><span data-stu-id="b88e2-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="b88e2-130">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="b88e2-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b88e2-131">Encontre todas as contas de usuário que têm um local de uso não especificado ( **onde-objeto {\_$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="b88e2-131">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="b88e2-132">Dentro das chaves, o comando instrui o Office 365 PowerShell a localizar apenas o conjunto de contas no qual a propriedade da conta de usuário do UsageLocation ( \*\* $ \_. UsageLocation\*\* ) não é especificado ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="b88e2-132">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b88e2-133">A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="b88e2-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="b88e2-134">Para ver todas as propriedades de contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (\*) para exibi-los para uma conta de usuário específica.</span><span class="sxs-lookup"><span data-stu-id="b88e2-134">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b88e2-135">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="b88e2-135">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="b88e2-136">Por exemplo, na lista, **City** é o nome de uma propriedade de conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="b88e2-136">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="b88e2-137">Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários em Londres:</span><span class="sxs-lookup"><span data-stu-id="b88e2-137">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b88e2-138">A sintaxe do cmdlet **Where-Object** mostrado nesses exemplos é **onde-Object {$\_.**</span><span class="sxs-lookup"><span data-stu-id="b88e2-138">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="b88e2-139">[nome da propriedade da conta de usuário] [operador de comparação] valor **}**. > [operador de comparação] é **-EQ** para igual a, **-ne** para não igual a, **-lt** para menor que, **-gT** para maior que e outros.</span><span class="sxs-lookup"><span data-stu-id="b88e2-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="b88e2-140">[value] normalmente é uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$NULL** para Unspecified> ver [onde-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b88e2-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b88e2-141">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88e2-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b88e2-142">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b88e2-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="b88e2-143">Exibir todas as contas</span><span class="sxs-lookup"><span data-stu-id="b88e2-143">View all accounts</span></span>

<span data-ttu-id="b88e2-144">Para exibir a lista completa de contas de usuário, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="b88e2-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="b88e2-145">Você deve ver informações semelhantes a estas:</span><span class="sxs-lookup"><span data-stu-id="b88e2-145">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b88e2-146">O cmdlet **Get-MsolUser** também tem um conjunto de parâmetros para filtrar o conjunto de contas de usuário exibidas.</span><span class="sxs-lookup"><span data-stu-id="b88e2-146">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="b88e2-147">Por exemplo, para a lista de usuários não licenciados (usuários que foram adicionados ao Office 365, mas que ainda não foram licenciados para usar qualquer um dos serviços), execute este comando.</span><span class="sxs-lookup"><span data-stu-id="b88e2-147">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="b88e2-148">Você deve ver informações semelhantes a estas:</span><span class="sxs-lookup"><span data-stu-id="b88e2-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b88e2-149">Para obter mais informações sobre parâmetros adicionais para filtrar a exibição do conjunto de contas de usuário exibidas, consulte [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="b88e2-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="b88e2-150">Exibir uma conta específica</span><span class="sxs-lookup"><span data-stu-id="b88e2-150">View a specific account</span></span>

<span data-ttu-id="b88e2-151">Para exibir uma conta de usuário específica, preencha o nome de entrada da conta de usuário da conta de usuário, também conhecida como nome de usuário principal (UPN), remova os caracteres "<" e ">" e execute este comando:</span><span class="sxs-lookup"><span data-stu-id="b88e2-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="b88e2-152">Exibir algumas contas com base em uma propriedade comum</span><span class="sxs-lookup"><span data-stu-id="b88e2-152">View some accounts based on a common property</span></span>

<span data-ttu-id="b88e2-153">Para ser mais seletivo sobre a lista de contas a serem exibidas, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="b88e2-153">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="b88e2-154">Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que diz ao Office 365 PowerShell para obter os resultados de um comando e enviá-lo para o próximo comando.</span><span class="sxs-lookup"><span data-stu-id="b88e2-154">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b88e2-155">Veja a seguir um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="b88e2-155">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b88e2-156">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="b88e2-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b88e2-157">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="b88e2-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b88e2-158">Encontre todas as contas de usuário que têm um local de uso não especificado ( **onde-objeto {\_$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="b88e2-158">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="b88e2-159">Dentro das chaves, o comando instrui o Office 365 PowerShell a localizar apenas o conjunto de contas no qual a propriedade da conta de usuário do UsageLocation ( \*\* $ \_. UsageLocation\*\* ) não é especificado ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="b88e2-159">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b88e2-160">Você deve ver informações semelhantes a estas:</span><span class="sxs-lookup"><span data-stu-id="b88e2-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="b88e2-161">A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="b88e2-161">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="b88e2-162">Para ver todas as propriedades de contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (\*) para exibi-los para uma conta de usuário específica.</span><span class="sxs-lookup"><span data-stu-id="b88e2-162">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b88e2-163">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="b88e2-163">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="b88e2-164">Por exemplo, na lista, **City** é o nome de uma propriedade de conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="b88e2-164">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="b88e2-165">Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários em Londres:</span><span class="sxs-lookup"><span data-stu-id="b88e2-165">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b88e2-166">A sintaxe do cmdlet **Where-Object** mostrado nesses exemplos é **onde-Object {$\_.**</span><span class="sxs-lookup"><span data-stu-id="b88e2-166">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="b88e2-167">[nome da propriedade da conta de usuário] [operador de comparação] valor **}**.</span><span class="sxs-lookup"><span data-stu-id="b88e2-167">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="b88e2-168">[operador de comparação] é **-EQ** para igual a, **-ne** para não é igual a, **-lt** para menor que, **-gt** para maior que e outros.</span><span class="sxs-lookup"><span data-stu-id="b88e2-168">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="b88e2-169">[value] normalmente é uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$NULL** para não especificado.</span><span class="sxs-lookup"><span data-stu-id="b88e2-169">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="b88e2-170">ConFira [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b88e2-170">See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="b88e2-171">Você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b88e2-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="b88e2-172">Exibir valores de propriedade adicionais para contas</span><span class="sxs-lookup"><span data-stu-id="b88e2-172">View additional property values for accounts</span></span>

<span data-ttu-id="b88e2-173">Por padrão, o cmdlet **Get-MsolUser** exibe três propriedades de contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="b88e2-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="b88e2-174">Principal</span><span class="sxs-lookup"><span data-stu-id="b88e2-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="b88e2-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b88e2-175">DisplayName</span></span>
    
- <span data-ttu-id="b88e2-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="b88e2-176">isLicensed</span></span>
    
<span data-ttu-id="b88e2-177">Se você precisar de propriedades adicionais, como o departamento para o qual o usuário trabalha e o país/região em que o usuário usa os serviços do Office 365, você pode executar **Get-MsolUser** em combinação com o cmdlet **Select-Object** para especificar a lista de contas de usuário Propriedades.</span><span class="sxs-lookup"><span data-stu-id="b88e2-177">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="b88e2-178">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="b88e2-178">Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="b88e2-179">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="b88e2-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b88e2-180">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="b88e2-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b88e2-181">Exibir apenas o nome da conta de usuário, o departamento e o local de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b88e2-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b88e2-182">Você deve ver informações semelhantes a estas:</span><span class="sxs-lookup"><span data-stu-id="b88e2-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="b88e2-183">O cmdlet **Select-Object** permite que você escolha e escolha as propriedades que você deseja que um comando exiba.</span><span class="sxs-lookup"><span data-stu-id="b88e2-183">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="b88e2-184">Para ver todas as propriedades de contas de usuário, use o caractere curinga (\*) para exibi-las para uma conta de usuário específica.</span><span class="sxs-lookup"><span data-stu-id="b88e2-184">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b88e2-185">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="b88e2-185">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="b88e2-186">Para ser mais seletivo sobre a lista de contas a serem exibidas, você também pode usar o cmdlet **Where-Object** .</span><span class="sxs-lookup"><span data-stu-id="b88e2-186">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet.</span></span> <span data-ttu-id="b88e2-187">Veja a seguir um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:</span><span class="sxs-lookup"><span data-stu-id="b88e2-187">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="b88e2-188">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="b88e2-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b88e2-189">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="b88e2-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b88e2-190">Encontre todas as contas de usuário que têm um local de uso não especificado ( **onde-objeto {\_$. UsageLocation-EQ $Null}** ) e envie as informações resultantes para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="b88e2-190">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="b88e2-191">Dentro das chaves, o comando está instruindo o Office 365 PowerShell a localizar apenas o conjunto de contas no qual a propriedade da conta de usuário do UsageLocation ( \*\* $ \_. UsageLocation\*\* ) não é especificado ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="b88e2-191">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="b88e2-192">Exibir apenas o nome da conta de usuário, o departamento e o local de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b88e2-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b88e2-193">Você deve ver informações semelhantes a estas:</span><span class="sxs-lookup"><span data-stu-id="b88e2-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="b88e2-194">Se você estiver usando a sincronização de diretórios para criar e gerenciar seus usuários do Office 365, poderá exibir a conta local em que um usuário do Office 365 foi projetado.</span><span class="sxs-lookup"><span data-stu-id="b88e2-194">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="b88e2-195">O seguinte pressupõe que o Azure AD Connect tenha sido configurado para usar a âncora de origem padrão de objectGUID (para saber mais sobre como configurar uma âncora de origem, confira [Azure ad Connect: design Concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) e pressupõe que o módulo do Active Directory para o PowerShell tenha foi instalado (consulte [ferramentas de RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="b88e2-195">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="b88e2-196">Confira também</span><span class="sxs-lookup"><span data-stu-id="b88e2-196">See also</span></span>

[<span data-ttu-id="b88e2-197">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b88e2-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b88e2-198">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b88e2-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b88e2-199">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b88e2-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

