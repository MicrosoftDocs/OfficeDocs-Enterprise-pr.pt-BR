---
title: Configurar propriedades da conta de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumo: Use o Office 365 PowerShell para configurar propriedades de várias contas de usuário ou individuais em seu locatário do Office 365.'
ms.openlocfilehash: 3fdf5c4c5dbb4c44a3c91d343bd77810a1411a20
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069231"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="d770b-103">Configurar propriedades da conta de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d770b-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="d770b-104">**Resumo:** Use o Office 365 PowerShell para configurar propriedades de várias contas de usuário ou individuais em seu locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d770b-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="d770b-105">Embora você possa usar o centro de administração do Office 365 para configurar as propriedades das contas de usuário do seu locatário do Office 365, você também pode usar o Office 365 PowerShell e fazer algumas coisas que o centro de administração do Office 365 não pode.</span><span class="sxs-lookup"><span data-stu-id="d770b-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d770b-106">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="d770b-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d770b-107">Para configurar propriedades de contas de usuário com o módulo PowerShell do Azure Active Directory para Graph, use o cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="d770b-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d770b-108">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d770b-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d770b-109">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="d770b-109">Change properties for a specific user account</span></span>

<span data-ttu-id="d770b-110">Você identifica a conta com o parâmetro **-ObjectID** e define ou altera propriedades específicas com parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d770b-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="d770b-111">Veja a seguir uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="d770b-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d770b-112">-Department "\<Department name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d770b-113">-DisplayName "\<name> de usuário completo"</span><span class="sxs-lookup"><span data-stu-id="d770b-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d770b-114">-FacsimilieTelephoneNumber "\<fax number>"</span><span class="sxs-lookup"><span data-stu-id="d770b-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="d770b-115">-Exname>va\<"usuário primeiro"</span><span class="sxs-lookup"><span data-stu-id="d770b-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="d770b-116">-Sobrenome "\<último usuário name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="d770b-117">– "\<Telefone celular number>"</span><span class="sxs-lookup"><span data-stu-id="d770b-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d770b-118">-JobTitle "\<trabalho title>"</span><span class="sxs-lookup"><span data-stu-id="d770b-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="d770b-119">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="d770b-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d770b-120">-StreetAddress "\<rua address>"</span><span class="sxs-lookup"><span data-stu-id="d770b-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d770b-121">-City "\<City name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d770b-122">-State "\<estado name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d770b-123">-PostalCode "\<code> postal"</span><span class="sxs-lookup"><span data-stu-id="d770b-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d770b-124">-País "\<país name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d770b-125">-TelephoneNumber "\<number> de telefone do Office"</span><span class="sxs-lookup"><span data-stu-id="d770b-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d770b-126">-UsageLocation "\<2 caracteres de país ou região code>"</span><span class="sxs-lookup"><span data-stu-id="d770b-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d770b-127">Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.</span><span class="sxs-lookup"><span data-stu-id="d770b-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d770b-128">Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d770b-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="d770b-129">Para exibir o nome principal do usuário para suas contas de usuário, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="d770b-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="d770b-130">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="d770b-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d770b-131">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="d770b-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-132">Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **objeto Sort userPrincipalName** ) e envie-o para **|** o próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="d770b-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-133">Exibe apenas a propriedade nome principal do usuário para cada conta ( **Select-Object userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="d770b-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="d770b-134">Exibir uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="d770b-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d770b-135">Este comando listará todas as suas contas.</span><span class="sxs-lookup"><span data-stu-id="d770b-135">This command will list all of your accounts.</span></span> <span data-ttu-id="d770b-136">Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d770b-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d770b-137">Este exemplo exibe o nome principal do usuário para a conta de usuário com o nome de exibição de Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="d770b-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d770b-138">Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="d770b-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="d770b-139">Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:</span><span class="sxs-lookup"><span data-stu-id="d770b-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d770b-140">Alterar propriedades de todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="d770b-140">Change properties for all user accounts</span></span>

<span data-ttu-id="d770b-141">Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-AzureADUser** e **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="d770b-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="d770b-142">O exemplo a seguir altera o local de uso de todos os usuários para a França:</span><span class="sxs-lookup"><span data-stu-id="d770b-142">The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d770b-143">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="d770b-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d770b-144">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="d770b-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-145">Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="d770b-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d770b-146">Alterar propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="d770b-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d770b-147">Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-AzureADUser**, **Where**e **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="d770b-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="d770b-148">O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:</span><span class="sxs-lookup"><span data-stu-id="d770b-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d770b-149">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="d770b-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d770b-150">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="d770b-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-151">Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="d770b-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-152">Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="d770b-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d770b-153">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d770b-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d770b-154">Para configurar propriedades de contas de usuário com o módulo Microsoft Azure Active Directory para Windows PowerShell, use o cmdlet Set-MsolUser e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="d770b-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d770b-155">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d770b-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d770b-156">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="d770b-156">Change properties for a specific user account</span></span>

<span data-ttu-id="d770b-157">Para configurar as propriedades de uma conta de usuário específica, use o cmdlet [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="d770b-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d770b-158">Você identifica a conta com o parâmetro **-userPrincipalName** e define ou altera propriedades específicas com parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d770b-158">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="d770b-159">Veja a seguir uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="d770b-159">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d770b-160">-City "\<City name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d770b-161">-País "\<país name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d770b-162">-Department "\<Department name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d770b-163">-DisplayName "\<name> de usuário completo"</span><span class="sxs-lookup"><span data-stu-id="d770b-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d770b-164">– Fax "\<fax number>"</span><span class="sxs-lookup"><span data-stu-id="d770b-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="d770b-165">-FirstName "\<User First name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="d770b-166">-LastName "\<última name> do usuário"</span><span class="sxs-lookup"><span data-stu-id="d770b-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="d770b-167">-MobilePhone "\<telefone celular number>"</span><span class="sxs-lookup"><span data-stu-id="d770b-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d770b-168">– Office "\<Office location>"</span><span class="sxs-lookup"><span data-stu-id="d770b-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="d770b-169">-PhoneNumber "\<number> de telefone do Office"</span><span class="sxs-lookup"><span data-stu-id="d770b-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d770b-170">-PostalCode "\<code> postal"</span><span class="sxs-lookup"><span data-stu-id="d770b-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d770b-171">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="d770b-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d770b-172">-State "\<estado name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d770b-173">-StreetAddress "\<rua address>"</span><span class="sxs-lookup"><span data-stu-id="d770b-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d770b-174">-Title "\<título name>"</span><span class="sxs-lookup"><span data-stu-id="d770b-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="d770b-175">-UsageLocation "\<2 caracteres de país ou região code>"</span><span class="sxs-lookup"><span data-stu-id="d770b-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d770b-176">Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.</span><span class="sxs-lookup"><span data-stu-id="d770b-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d770b-177">Consulte [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d770b-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="d770b-178">Para ver os nomes principais de usuário de todos os seus usuários, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="d770b-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="d770b-179">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="d770b-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d770b-180">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="d770b-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-181">Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **objeto Sort userPrincipalName** ) e envie-o para **|** o próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="d770b-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-182">Exibe apenas a propriedade nome principal do usuário para cada conta ( **Select-Object userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="d770b-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="d770b-183">Exibir uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="d770b-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d770b-184">Este comando listará todas as suas contas.</span><span class="sxs-lookup"><span data-stu-id="d770b-184">This command will list all of your accounts.</span></span> <span data-ttu-id="d770b-185">Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d770b-185">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d770b-186">Este exemplo exibe o nome principal do usuário chamado Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="d770b-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d770b-187">Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="d770b-187">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="d770b-188">Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:</span><span class="sxs-lookup"><span data-stu-id="d770b-188">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d770b-189">Alterar propriedades de todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="d770b-189">Change properties for all user accounts</span></span>

<span data-ttu-id="d770b-190">Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-MsolUser** e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="d770b-190">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="d770b-191">O exemplo a seguir altera o local de uso de todos os usuários para a França:</span><span class="sxs-lookup"><span data-stu-id="d770b-191">The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d770b-192">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="d770b-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d770b-193">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="d770b-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-194">Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="d770b-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d770b-195">Alterar propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="d770b-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d770b-196">Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-MsolUser**, **Where-Object**e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="d770b-196">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="d770b-197">O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:</span><span class="sxs-lookup"><span data-stu-id="d770b-197">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d770b-198">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="d770b-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d770b-199">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="d770b-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-200">Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde-Object {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="d770b-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d770b-201">Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="d770b-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="d770b-202">Confira também</span><span class="sxs-lookup"><span data-stu-id="d770b-202">See also</span></span>

[<span data-ttu-id="d770b-203">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d770b-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d770b-204">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d770b-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d770b-205">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d770b-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
