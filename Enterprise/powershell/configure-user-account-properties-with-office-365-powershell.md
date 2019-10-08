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
ms.openlocfilehash: 3d81a7e5860b086fd411e8e6fcaab44568e890d5
ms.sourcegitcommit: 4d29b00a57c22225f2cdd592064ee8b6e575fceb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "37411510"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="206e4-103">Configurar propriedades da conta de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="206e4-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="206e4-104">**Resumo:** Use o Office 365 PowerShell para configurar propriedades de várias contas de usuário ou individuais em seu locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="206e4-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="206e4-105">Embora você possa usar o centro de administração do Microsoft 365 para configurar as propriedades das contas de usuário do seu locatário do Office 365, você também pode usar o Office 365 PowerShell e realizar algumas coisas que o centro de administração não pode.</span><span class="sxs-lookup"><span data-stu-id="206e4-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="206e4-106">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="206e4-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="206e4-107">Para configurar propriedades de contas de usuário com o módulo PowerShell do Azure Active Directory para Graph, use o cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="206e4-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="206e4-108">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="206e4-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="206e4-109">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="206e4-109">Change properties for a specific user account</span></span>

<span data-ttu-id="206e4-110">Você identifica a conta com o parâmetro **-ObjectID** e define ou altera propriedades específicas com parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="206e4-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="206e4-111">Veja a seguir uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="206e4-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="206e4-112">-Department "\<nome do departamento>"</span><span class="sxs-lookup"><span data-stu-id="206e4-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="206e4-113">-DisplayName "\<nome de usuário completo>"</span><span class="sxs-lookup"><span data-stu-id="206e4-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="206e4-114">-FacsimilieTelephoneNumber "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="206e4-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="206e4-115">-Exnamename\<"nome de usuário>"</span><span class="sxs-lookup"><span data-stu-id="206e4-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="206e4-116">-Sobrenome "\<último nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="206e4-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="206e4-117">– "\<Número de telefone celular>" móvel</span><span class="sxs-lookup"><span data-stu-id="206e4-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="206e4-118">-JobTitle "\<título do trabalho>"</span><span class="sxs-lookup"><span data-stu-id="206e4-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="206e4-119">-PreferredLanguage "\<idioma>"</span><span class="sxs-lookup"><span data-stu-id="206e4-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="206e4-120">-StreetAddress "\<endereço>"</span><span class="sxs-lookup"><span data-stu-id="206e4-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="206e4-121">-City "\<nome da cidade>"</span><span class="sxs-lookup"><span data-stu-id="206e4-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="206e4-122">-State "\<nome do estado>"</span><span class="sxs-lookup"><span data-stu-id="206e4-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="206e4-123">-PostalCode "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="206e4-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="206e4-124">-País "\<nome do país>"</span><span class="sxs-lookup"><span data-stu-id="206e4-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="206e4-125">-TelephoneNumber "\<número de telefone do Office>"</span><span class="sxs-lookup"><span data-stu-id="206e4-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="206e4-126">-UsageLocation "\<código de país ou região de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="206e4-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="206e4-127">Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.</span><span class="sxs-lookup"><span data-stu-id="206e4-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="206e4-128">Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="206e4-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>

>[!Note]
> <span data-ttu-id="206e4-129">Você define a propriedade de **email** com o parâmetro **-OtherMails** .</span><span class="sxs-lookup"><span data-stu-id="206e4-129">You set the **Mail** property with the **-OtherMails** parameter.</span></span>
>
 
<span data-ttu-id="206e4-130">Para exibir o nome principal do usuário para suas contas de usuário, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="206e4-130">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="206e4-131">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="206e4-131">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="206e4-132">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="206e4-132">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-133">Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **objeto Sort userPrincipalName** ) e envie-o para **|** o próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="206e4-133">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-134">Exibe apenas a propriedade nome principal do usuário para cada conta ( **Select-Object userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="206e4-134">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="206e4-135">Exibir uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="206e4-135">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="206e4-136">Este comando listará todas as suas contas.</span><span class="sxs-lookup"><span data-stu-id="206e4-136">This command will list all of your accounts.</span></span> <span data-ttu-id="206e4-137">Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="206e4-137">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="206e4-138">Este exemplo exibe o nome principal do usuário para a conta de usuário com o nome de exibição de Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="206e4-138">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="206e4-139">Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="206e4-139">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="206e4-140">Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:</span><span class="sxs-lookup"><span data-stu-id="206e4-140">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="206e4-141">Alterar propriedades de todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="206e4-141">Change properties for all user accounts</span></span>

<span data-ttu-id="206e4-142">Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-AzureADUser** e **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="206e4-142">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="206e4-143">O exemplo a seguir altera o local de uso de todos os usuários para a França:</span><span class="sxs-lookup"><span data-stu-id="206e4-143">The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="206e4-144">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="206e4-144">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="206e4-145">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="206e4-145">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-146">Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="206e4-146">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="206e4-147">Alterar propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="206e4-147">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="206e4-148">Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-AzureADUser**, **Where**e **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="206e4-148">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="206e4-149">O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:</span><span class="sxs-lookup"><span data-stu-id="206e4-149">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="206e4-150">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="206e4-150">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="206e4-151">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="206e4-151">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-152">Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="206e4-152">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-153">Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="206e4-153">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="206e4-154">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="206e4-154">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="206e4-155">Para configurar propriedades de contas de usuário com o módulo Microsoft Azure Active Directory para Windows PowerShell, use o cmdlet Set-MsolUser e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="206e4-155">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="206e4-156">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="206e4-156">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="206e4-157">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="206e4-157">Change properties for a specific user account</span></span>

<span data-ttu-id="206e4-158">Para configurar as propriedades de uma conta de usuário específica, use o cmdlet [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e especifique as propriedades a serem definidas ou alteradas.</span><span class="sxs-lookup"><span data-stu-id="206e4-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="206e4-159">Você identifica a conta com o parâmetro **-userPrincipalName** e define ou altera propriedades específicas com parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="206e4-159">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="206e4-160">Veja a seguir uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="206e4-160">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="206e4-161">-City "\<nome da cidade>"</span><span class="sxs-lookup"><span data-stu-id="206e4-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="206e4-162">-País "\<nome do país>"</span><span class="sxs-lookup"><span data-stu-id="206e4-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="206e4-163">-Department "\<nome do departamento>"</span><span class="sxs-lookup"><span data-stu-id="206e4-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="206e4-164">-DisplayName "\<nome de usuário completo>"</span><span class="sxs-lookup"><span data-stu-id="206e4-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="206e4-165">– Fax "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="206e4-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="206e4-166">-FirstName "\<nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="206e4-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="206e4-167">-LastName "\<último nome do usuário>"</span><span class="sxs-lookup"><span data-stu-id="206e4-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="206e4-168">-MobilePhone "\<número de telefone celular>"</span><span class="sxs-lookup"><span data-stu-id="206e4-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="206e4-169">-Office "\<local do Office>"</span><span class="sxs-lookup"><span data-stu-id="206e4-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="206e4-170">-PhoneNumber "\<número de telefone do Office>"</span><span class="sxs-lookup"><span data-stu-id="206e4-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="206e4-171">-PostalCode "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="206e4-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="206e4-172">-PreferredLanguage "\<idioma>"</span><span class="sxs-lookup"><span data-stu-id="206e4-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="206e4-173">-State "\<nome do estado>"</span><span class="sxs-lookup"><span data-stu-id="206e4-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="206e4-174">-StreetAddress "\<endereço>"</span><span class="sxs-lookup"><span data-stu-id="206e4-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="206e4-175">-Title "\<nome do título>"</span><span class="sxs-lookup"><span data-stu-id="206e4-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="206e4-176">-UsageLocation "\<código de país ou região de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="206e4-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="206e4-177">Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.</span><span class="sxs-lookup"><span data-stu-id="206e4-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="206e4-178">Consulte [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="206e4-178">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

>[!Note]
> <span data-ttu-id="206e4-179">Você define a propriedade de **email** com o parâmetro **-AlternateEmailAddresses** .</span><span class="sxs-lookup"><span data-stu-id="206e4-179">You set the **Mail** property with the **-AlternateEmailAddresses** parameter.</span></span>
>
 
<span data-ttu-id="206e4-180">Para ver os nomes principais de usuário de todos os seus usuários, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="206e4-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="206e4-181">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="206e4-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="206e4-182">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="206e4-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-183">Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **objeto Sort userPrincipalName** ) e envie-o para **|** o próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="206e4-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-184">Exibe apenas a propriedade nome principal do usuário para cada conta ( **Select-Object userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="206e4-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="206e4-185">Exibir uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="206e4-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="206e4-186">Este comando listará todas as suas contas.</span><span class="sxs-lookup"><span data-stu-id="206e4-186">This command will list all of your accounts.</span></span> <span data-ttu-id="206e4-187">Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="206e4-187">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="206e4-188">Este exemplo exibe o nome principal do usuário chamado Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="206e4-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="206e4-189">Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="206e4-189">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="206e4-190">Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:</span><span class="sxs-lookup"><span data-stu-id="206e4-190">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="206e4-191">Alterar propriedades de todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="206e4-191">Change properties for all user accounts</span></span>

<span data-ttu-id="206e4-192">Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-MsolUser** e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="206e4-192">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="206e4-193">O exemplo a seguir altera o local de uso de todos os usuários para a França:</span><span class="sxs-lookup"><span data-stu-id="206e4-193">The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="206e4-194">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="206e4-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="206e4-195">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="206e4-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-196">Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="206e4-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="206e4-197">Alterar propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="206e4-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="206e4-198">Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-MsolUser**, **Where-Object**e **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="206e4-198">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="206e4-199">O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:</span><span class="sxs-lookup"><span data-stu-id="206e4-199">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="206e4-200">Este comando instrui o Office 365 PowerShell a:</span><span class="sxs-lookup"><span data-stu-id="206e4-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="206e4-201">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().</span><span class="sxs-lookup"><span data-stu-id="206e4-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-202">Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde-Object {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().</span><span class="sxs-lookup"><span data-stu-id="206e4-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="206e4-203">Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="206e4-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="206e4-204">Confira também</span><span class="sxs-lookup"><span data-stu-id="206e4-204">See also</span></span>

[<span data-ttu-id="206e4-205">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="206e4-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="206e4-206">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="206e4-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="206e4-207">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="206e4-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
