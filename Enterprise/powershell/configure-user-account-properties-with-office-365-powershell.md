---
title: Configurar propriedades da conta de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumo: Use o Office 365 PowerShell para configurar propriedades de várias contas de usuário ou individuais em seu locatário do Office 365.'
ms.openlocfilehash: 5748bd382357168e4184754fb49fb7304e2d2474
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004714"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="301e6-103">Configurar propriedades da conta de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="301e6-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="301e6-104">Embora você possa usar o centro de administração do Microsoft 365 para configurar as propriedades das contas de usuário do seu locatário do Office 365, você também pode usar o Office 365 PowerShell e realizar algumas coisas que o centro de administração não pode.</span><span class="sxs-lookup"><span data-stu-id="301e6-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="301e6-105">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="301e6-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="301e6-106">Para configurar propriedades de contas de usuário com o módulo PowerShell do Azure Active Directory para Graph, use o cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="301e6-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="301e6-107">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="301e6-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="301e6-108">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="301e6-108">Change properties for a specific user account</span></span>

<span data-ttu-id="301e6-109">Você identifica a conta com o parâmetro **-ObjectID** e define ou altera propriedades específicas com parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="301e6-109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="301e6-110">Veja a seguir uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="301e6-110">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="301e6-111">-Department "\<nome do departamento>"</span><span class="sxs-lookup"><span data-stu-id="301e6-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="301e6-112">-DisplayName "\<nome de usuário completo>"</span><span class="sxs-lookup"><span data-stu-id="301e6-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="301e6-113">-FacsimilieTelephoneNumber "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="301e6-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="301e6-114">-Exnamename\<"nome de usuário>"</span><span class="sxs-lookup"><span data-stu-id="301e6-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="301e6-115">-Sobrenome "\<último nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="301e6-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="301e6-116">– "\<Número de telefone celular>" móvel</span><span class="sxs-lookup"><span data-stu-id="301e6-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="301e6-117">-JobTitle "\<título do trabalho>"</span><span class="sxs-lookup"><span data-stu-id="301e6-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="301e6-118">-PreferredLanguage "\<idioma>"</span><span class="sxs-lookup"><span data-stu-id="301e6-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="301e6-119">-StreetAddress "\<endereço>"</span><span class="sxs-lookup"><span data-stu-id="301e6-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="301e6-120">-City "\<nome da cidade>"</span><span class="sxs-lookup"><span data-stu-id="301e6-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="301e6-121">-State "\<nome do estado>"</span><span class="sxs-lookup"><span data-stu-id="301e6-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="301e6-122">-PostalCode "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="301e6-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="301e6-123">-País "\<nome do país>"</span><span class="sxs-lookup"><span data-stu-id="301e6-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="301e6-124">-TelephoneNumber "\<número de telefone do Office>"</span><span class="sxs-lookup"><span data-stu-id="301e6-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="301e6-125">-UsageLocation "\<código de país ou região de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="301e6-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="301e6-126">Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.</span><span class="sxs-lookup"><span data-stu-id="301e6-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="301e6-127">Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="301e6-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="301e6-128">Para exibir o nome principal do usuário para suas contas de usuário, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="301e6-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="301e6-129">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="301e6-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="301e6-130">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="301e6-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-131">Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **classificar userPrincipalName** ) e enviá-lo **|** para o próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="301e6-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-132">Exibe apenas a propriedade nome principal do usuário para cada conta ( **selecione userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="301e6-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="301e6-133">Exibir uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="301e6-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="301e6-134">Este comando listará todas as suas contas.</span><span class="sxs-lookup"><span data-stu-id="301e6-134">This command will list all of your accounts.</span></span> <span data-ttu-id="301e6-135">Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="301e6-135">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="301e6-136">Este exemplo exibe o nome principal do usuário para a conta de usuário com o nome de exibição de Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="301e6-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="301e6-137">Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="301e6-137">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="301e6-138">Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:</span><span class="sxs-lookup"><span data-stu-id="301e6-138">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="301e6-139">Alterar propriedades de todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="301e6-139">Change properties for all user accounts</span></span>

<span data-ttu-id="301e6-140">Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-AzureADUser** e **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="301e6-140">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="301e6-141">O exemplo a seguir altera o local de uso de todos os usuários para a França:</span><span class="sxs-lookup"><span data-stu-id="301e6-141">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="301e6-142">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="301e6-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="301e6-143">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="301e6-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-144">Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="301e6-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="301e6-145">Alterar propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="301e6-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="301e6-146">Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-AzureADUser**, **Where**e **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="301e6-146">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="301e6-147">O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:</span><span class="sxs-lookup"><span data-stu-id="301e6-147">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="301e6-148">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="301e6-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="301e6-149">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="301e6-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-150">Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="301e6-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-151">Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="301e6-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="301e6-152">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="301e6-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="301e6-153">Para configurar propriedades de contas de usuário com o módulo Microsoft Azure Active Directory para Windows PowerShell, use o cmdlet **set-MsolUser** e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="301e6-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="301e6-154">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="301e6-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="301e6-155">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="301e6-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="301e6-156">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="301e6-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="301e6-157">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="301e6-157">Change properties for a specific user account</span></span>

<span data-ttu-id="301e6-158">Para configurar as propriedades de uma conta de usuário específica, use o cmdlet [set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="301e6-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="301e6-159">Você identifica a conta com o parâmetro **-userPrincipalName** e define ou altera propriedades específicas com parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="301e6-159">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="301e6-160">Veja a seguir uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="301e6-160">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="301e6-161">-City "\<nome da cidade>"</span><span class="sxs-lookup"><span data-stu-id="301e6-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="301e6-162">-País "\<nome do país>"</span><span class="sxs-lookup"><span data-stu-id="301e6-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="301e6-163">-Department "\<nome do departamento>"</span><span class="sxs-lookup"><span data-stu-id="301e6-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="301e6-164">-DisplayName "\<nome de usuário completo>"</span><span class="sxs-lookup"><span data-stu-id="301e6-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="301e6-165">– Fax "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="301e6-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="301e6-166">-FirstName "\<nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="301e6-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="301e6-167">-LastName "\<último nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="301e6-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="301e6-168">-MobilePhone "\<número de telefone celular>"</span><span class="sxs-lookup"><span data-stu-id="301e6-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="301e6-169">-Office "\<local do Office>"</span><span class="sxs-lookup"><span data-stu-id="301e6-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="301e6-170">-PhoneNumber "\<número de telefone do Office>"</span><span class="sxs-lookup"><span data-stu-id="301e6-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="301e6-171">-PostalCode "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="301e6-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="301e6-172">-PreferredLanguage "\<idioma>"</span><span class="sxs-lookup"><span data-stu-id="301e6-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="301e6-173">-State "\<nome do estado>"</span><span class="sxs-lookup"><span data-stu-id="301e6-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="301e6-174">-StreetAddress "\<endereço>"</span><span class="sxs-lookup"><span data-stu-id="301e6-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="301e6-175">-Title "\<nome do título>"</span><span class="sxs-lookup"><span data-stu-id="301e6-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="301e6-176">-UsageLocation "\<código de país ou região de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="301e6-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="301e6-177">Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.</span><span class="sxs-lookup"><span data-stu-id="301e6-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="301e6-178">Consulte [set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="301e6-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="301e6-179">Para ver os nomes principais de usuário de todos os seus usuários, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="301e6-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="301e6-180">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="301e6-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="301e6-181">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="301e6-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-182">Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **classificar userPrincipalName** ) e enviá-lo **|** para o próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="301e6-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-183">Exibe apenas a propriedade nome principal do usuário para cada conta ( **selecione userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="301e6-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="301e6-184">Exibir uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="301e6-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="301e6-185">Este comando listará todas as suas contas.</span><span class="sxs-lookup"><span data-stu-id="301e6-185">This command will list all of your accounts.</span></span> <span data-ttu-id="301e6-186">Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="301e6-186">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="301e6-187">Este exemplo exibe o nome principal do usuário chamado Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="301e6-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="301e6-188">Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="301e6-188">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="301e6-189">Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:</span><span class="sxs-lookup"><span data-stu-id="301e6-189">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="301e6-190">Alterar propriedades de todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="301e6-190">Change properties for all user accounts</span></span>

<span data-ttu-id="301e6-191">Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-MsolUser** e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="301e6-191">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="301e6-192">O exemplo a seguir altera o local de uso de todos os usuários para a França:</span><span class="sxs-lookup"><span data-stu-id="301e6-192">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="301e6-193">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="301e6-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="301e6-194">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="301e6-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-195">Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="301e6-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="301e6-196">Alterar propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="301e6-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="301e6-197">Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-MsolUser**, **Where**e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="301e6-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="301e6-198">O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:</span><span class="sxs-lookup"><span data-stu-id="301e6-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="301e6-199">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="301e6-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="301e6-200">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="301e6-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-201">Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="301e6-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="301e6-202">Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="301e6-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="301e6-203">Confira também</span><span class="sxs-lookup"><span data-stu-id="301e6-203">See also</span></span>

[<span data-ttu-id="301e6-204">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="301e6-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="301e6-205">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="301e6-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="301e6-206">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="301e6-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
