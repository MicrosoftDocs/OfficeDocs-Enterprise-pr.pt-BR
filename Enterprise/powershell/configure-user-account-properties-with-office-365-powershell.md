---
title: Configurar propriedades da conta de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
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
ms.openlocfilehash: 67ce7d3c57f286f0b2365aa2503fdf1c8bc13429
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257652"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="8483d-103">Configurar propriedades da conta de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8483d-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="8483d-104">**Resumo:** Use o Office 365 PowerShell para configurar propriedades de várias contas de usuário ou individuais em seu locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8483d-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="8483d-105">Embora você possa usar o centro de administração do Microsoft 365 para configurar as propriedades das contas de usuário do seu locatário do Office 365, você também pode usar o Office 365 PowerShell e realizar algumas coisas que o centro de administração não pode.</span><span class="sxs-lookup"><span data-stu-id="8483d-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8483d-106">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="8483d-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8483d-107">Para configurar propriedades de contas de usuário com o módulo PowerShell do Azure Active Directory para Graph, use o cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="8483d-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="8483d-108">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="8483d-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="8483d-109">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="8483d-109">Change properties for a specific user account</span></span>

<span data-ttu-id="8483d-110">Você identifica a conta com o parâmetro **-ObjectID** e define ou altera propriedades específicas com parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8483d-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="8483d-111">Veja a seguir uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="8483d-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="8483d-112">-Department "\<nome do departamento>"</span><span class="sxs-lookup"><span data-stu-id="8483d-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="8483d-113">-DisplayName "\<nome de usuário completo>"</span><span class="sxs-lookup"><span data-stu-id="8483d-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="8483d-114">-FacsimilieTelephoneNumber "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="8483d-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="8483d-115">-Exnamename\<"nome de usuário>"</span><span class="sxs-lookup"><span data-stu-id="8483d-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="8483d-116">-Sobrenome "\<último nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="8483d-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="8483d-117">– "\<Número de telefone celular>" móvel</span><span class="sxs-lookup"><span data-stu-id="8483d-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="8483d-118">-JobTitle "\<título do trabalho>"</span><span class="sxs-lookup"><span data-stu-id="8483d-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="8483d-119">-PreferredLanguage "\<idioma>"</span><span class="sxs-lookup"><span data-stu-id="8483d-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="8483d-120">-StreetAddress "\<endereço>"</span><span class="sxs-lookup"><span data-stu-id="8483d-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="8483d-121">-City "\<nome da cidade>"</span><span class="sxs-lookup"><span data-stu-id="8483d-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="8483d-122">-State "\<nome do estado>"</span><span class="sxs-lookup"><span data-stu-id="8483d-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="8483d-123">-PostalCode "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="8483d-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="8483d-124">-País "\<nome do país>"</span><span class="sxs-lookup"><span data-stu-id="8483d-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="8483d-125">-TelephoneNumber "\<número de telefone do Office>"</span><span class="sxs-lookup"><span data-stu-id="8483d-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="8483d-126">-UsageLocation "\<código de país ou região de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="8483d-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="8483d-127">Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.</span><span class="sxs-lookup"><span data-stu-id="8483d-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="8483d-128">Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8483d-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="8483d-129">Para exibir o nome principal do usuário para suas contas de usuário, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="8483d-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="8483d-130">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="8483d-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8483d-131">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="8483d-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-132">Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **objeto Sort userPrincipalName** ) e envie-o para **|** o próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="8483d-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-133">Exibe apenas a propriedade nome principal do usuário para cada conta ( **Select-Object userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="8483d-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="8483d-134">Exibir uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="8483d-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="8483d-135">Este comando listará todas as suas contas.</span><span class="sxs-lookup"><span data-stu-id="8483d-135">This command will list all of your accounts.</span></span> <span data-ttu-id="8483d-136">Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="8483d-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="8483d-137">Este exemplo exibe o nome principal do usuário para a conta de usuário com o nome de exibição de Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="8483d-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="8483d-138">Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="8483d-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="8483d-139">Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:</span><span class="sxs-lookup"><span data-stu-id="8483d-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="8483d-140">Alterar propriedades de todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="8483d-140">Change properties for all user accounts</span></span>

<span data-ttu-id="8483d-141">Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-AzureADUser** e **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="8483d-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="8483d-142">O exemplo a seguir altera o local de uso de todos os usuários para a França:</span><span class="sxs-lookup"><span data-stu-id="8483d-142">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="8483d-143">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="8483d-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8483d-144">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="8483d-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-145">Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="8483d-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="8483d-146">Alterar propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="8483d-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="8483d-147">Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-AzureADUser**, **Where**e **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="8483d-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="8483d-148">O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:</span><span class="sxs-lookup"><span data-stu-id="8483d-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="8483d-149">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="8483d-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8483d-150">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="8483d-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-151">Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="8483d-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-152">Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="8483d-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8483d-153">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8483d-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8483d-154">Para configurar propriedades de contas de usuário com o módulo Microsoft Azure Active Directory para Windows PowerShell, use o cmdlet Set-MsolUser e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="8483d-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="8483d-155">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8483d-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="8483d-156">O PowerShell Core não é compatível com o módulo Microsoft Azure Active Directory para o módulo e cmdlets do Windows PowerShell com o **MSol** em seu nome.</span><span class="sxs-lookup"><span data-stu-id="8483d-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8483d-157">Para continuar usando esses cmdlets, você deve executá-los do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8483d-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="8483d-158">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="8483d-158">Change properties for a specific user account</span></span>

<span data-ttu-id="8483d-159">Para configurar as propriedades de uma conta de usuário específica, use o cmdlet [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="8483d-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="8483d-160">Você identifica a conta com o parâmetro **-userPrincipalName** e define ou altera propriedades específicas com parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8483d-160">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="8483d-161">Veja a seguir uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="8483d-161">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="8483d-162">-City "\<nome da cidade>"</span><span class="sxs-lookup"><span data-stu-id="8483d-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="8483d-163">-País "\<nome do país>"</span><span class="sxs-lookup"><span data-stu-id="8483d-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="8483d-164">-Department "\<nome do departamento>"</span><span class="sxs-lookup"><span data-stu-id="8483d-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="8483d-165">-DisplayName "\<nome de usuário completo>"</span><span class="sxs-lookup"><span data-stu-id="8483d-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="8483d-166">– Fax "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="8483d-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="8483d-167">-FirstName "\<nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="8483d-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="8483d-168">-LastName "\<último nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="8483d-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="8483d-169">-MobilePhone "\<número de telefone celular>"</span><span class="sxs-lookup"><span data-stu-id="8483d-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="8483d-170">-Office "\<local do Office>"</span><span class="sxs-lookup"><span data-stu-id="8483d-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="8483d-171">-PhoneNumber "\<número de telefone do Office>"</span><span class="sxs-lookup"><span data-stu-id="8483d-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="8483d-172">-PostalCode "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="8483d-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="8483d-173">-PreferredLanguage "\<idioma>"</span><span class="sxs-lookup"><span data-stu-id="8483d-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="8483d-174">-State "\<nome do estado>"</span><span class="sxs-lookup"><span data-stu-id="8483d-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="8483d-175">-StreetAddress "\<endereço>"</span><span class="sxs-lookup"><span data-stu-id="8483d-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="8483d-176">-Title "\<nome do título>"</span><span class="sxs-lookup"><span data-stu-id="8483d-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="8483d-177">-UsageLocation "\<código de país ou região de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="8483d-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="8483d-178">Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.</span><span class="sxs-lookup"><span data-stu-id="8483d-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="8483d-179">Consulte [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8483d-179">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="8483d-180">Para ver os nomes principais de usuário de todos os seus usuários, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="8483d-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="8483d-181">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="8483d-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8483d-182">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="8483d-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-183">Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **objeto Sort userPrincipalName** ) e envie-o para **|** o próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="8483d-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-184">Exibe apenas a propriedade nome principal do usuário para cada conta ( **Select-Object userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="8483d-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="8483d-185">Exibir uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="8483d-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="8483d-186">Este comando listará todas as suas contas.</span><span class="sxs-lookup"><span data-stu-id="8483d-186">This command will list all of your accounts.</span></span> <span data-ttu-id="8483d-187">Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="8483d-187">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="8483d-188">Este exemplo exibe o nome principal do usuário chamado Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="8483d-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="8483d-189">Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="8483d-189">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="8483d-190">Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:</span><span class="sxs-lookup"><span data-stu-id="8483d-190">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="8483d-191">Alterar propriedades de todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="8483d-191">Change properties for all user accounts</span></span>

<span data-ttu-id="8483d-192">Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-MsolUser** e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="8483d-192">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="8483d-193">O exemplo a seguir altera o local de uso de todos os usuários para a França:</span><span class="sxs-lookup"><span data-stu-id="8483d-193">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="8483d-194">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="8483d-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8483d-195">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="8483d-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-196">Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="8483d-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="8483d-197">Alterar propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="8483d-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="8483d-198">Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-MsolUser**, **Where-Object**e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="8483d-198">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="8483d-199">O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:</span><span class="sxs-lookup"><span data-stu-id="8483d-199">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="8483d-200">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="8483d-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8483d-201">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="8483d-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-202">Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde-Object {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="8483d-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8483d-203">Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="8483d-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="8483d-204">Confira também</span><span class="sxs-lookup"><span data-stu-id="8483d-204">See also</span></span>

[<span data-ttu-id="8483d-205">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8483d-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8483d-206">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8483d-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8483d-207">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8483d-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
