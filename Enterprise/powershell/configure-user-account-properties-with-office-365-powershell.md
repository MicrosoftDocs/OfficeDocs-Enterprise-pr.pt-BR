---
title: Configurar propriedades da conta de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumo: Usar o PowerShell do Office 365 para configurar propriedades de um indivíduo ou várias contas de usuário no seu locatário do Office 365.'
ms.openlocfilehash: 4db63482fdcc1d6cb186e663fd55c13186b33813
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546482"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="3373a-103">Configurar propriedades da conta de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3373a-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="3373a-104">**Resumo:** Use o Office 365 PowerShell para configurar propriedades de um indivíduo ou várias contas de usuário no seu locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="3373a-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="3373a-105">Embora você possa usar o Centro de administração do Office 365 para configurar propriedades para as contas de usuário do seu locatário do Office 365, você também pode usar o PowerShell do Office 365 e fazer algumas coisas que não é possível o Centro de administração do Office 365.</span><span class="sxs-lookup"><span data-stu-id="3373a-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="3373a-106">Use o PowerShell do Azure Active Directory para o módulo de gráfico</span><span class="sxs-lookup"><span data-stu-id="3373a-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="3373a-107">Para configurar propriedades de contas de usuário com o Azure Active Directory PowerShell para o módulo de gráfico, você use o cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e especifique as propriedades para definir ou alterar.</span><span class="sxs-lookup"><span data-stu-id="3373a-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="3373a-108">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="3373a-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="3373a-109">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="3373a-109">Change properties for a specific user account</span></span>

<span data-ttu-id="3373a-p101">Identificar a conta com o parâmetro **- ObjectID** e definir ou alterar propriedades específicas com parâmetros adicionais. Aqui está uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="3373a-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="3373a-112">-Departamento "\<nome de departamento >"</span><span class="sxs-lookup"><span data-stu-id="3373a-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="3373a-113">-DisplayName "\<nome completos do usuário >"</span><span class="sxs-lookup"><span data-stu-id="3373a-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="3373a-114">-FacsimilieTelephoneNumber "\<número de fax >"</span><span class="sxs-lookup"><span data-stu-id="3373a-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="3373a-115">-GivenName "\<nome usuário >"</span><span class="sxs-lookup"><span data-stu-id="3373a-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="3373a-116">-Sobrenome "\<sobrenome do usuário >"</span><span class="sxs-lookup"><span data-stu-id="3373a-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="3373a-117">-Móvel "\<o número de telefone celular >"</span><span class="sxs-lookup"><span data-stu-id="3373a-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="3373a-118">-JobTitle "\<cargo >"</span><span class="sxs-lookup"><span data-stu-id="3373a-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="3373a-119">-PreferredLanguage "\<idioma >"</span><span class="sxs-lookup"><span data-stu-id="3373a-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="3373a-120">-StreetAddress "\<endereço >"</span><span class="sxs-lookup"><span data-stu-id="3373a-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="3373a-121">-Cidade "\<nome da cidade >"</span><span class="sxs-lookup"><span data-stu-id="3373a-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="3373a-122">-State "\<estado nome >"</span><span class="sxs-lookup"><span data-stu-id="3373a-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="3373a-123">-PostalCode "\<CEP >"</span><span class="sxs-lookup"><span data-stu-id="3373a-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="3373a-124">-País "\<nome do país >"</span><span class="sxs-lookup"><span data-stu-id="3373a-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="3373a-125">-TelephoneNumber "\<o número de telefone do escritório >"</span><span class="sxs-lookup"><span data-stu-id="3373a-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="3373a-126">-UsageLocation "\<código de país ou região 2 caracteres >"</span><span class="sxs-lookup"><span data-stu-id="3373a-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="3373a-127">Este é o código de região ou país com duas letras ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="3373a-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="3373a-128">Consulte [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="3373a-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="3373a-129">Para exibir o nome Principal de usuário para suas contas de usuário, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="3373a-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="3373a-130">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="3373a-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3373a-131">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-132">Classifique a lista de nomes de entidade de usuário em ordem alfabética ( **Objeto Sort UserPrincipalName** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-133">Exiba apenas a propriedade de nome Principal de usuário para cada conta ( **UserPrincipalName Select-Object** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="3373a-134">Exibi-las uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="3373a-p102">Esse comando listará todas as suas contas. Se você quiser exibir o nome Principal de usuário para uma conta com base em sua exibição nome (nome e sobrenome), preencha a variável **$userName** abaixo (removendo o \< e > caracteres), e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="3373a-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="3373a-137">Este exemplo exibe o nome Principal de usuário para a conta de usuário com o nome de exibição do Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="3373a-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="3373a-p103">Usando uma variável de **$upn** , você pode fazer alterações para contas individuais com base em seu nome para exibição. Aqui está um exemplo de definição de local de uso de Belinda Newman como França, mas especificando seu nome para exibição em vez de seu nome Principal de usuário:</span><span class="sxs-lookup"><span data-stu-id="3373a-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="3373a-140">Alterar propriedades para todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="3373a-140">Change properties for all user accounts</span></span>

<span data-ttu-id="3373a-p104">Para alterar propriedades para todos os usuários, você pode usar a combinação dos cmdlets **Get-AzureADUser** e **Set-AzureADUser** . O exemplo a seguir altera o local de uso para todos os usuários para França:</span><span class="sxs-lookup"><span data-stu-id="3373a-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="3373a-143">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="3373a-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3373a-144">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-145">Defina o local do usuário para França ( **Set-AzureADUser-UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="3373a-146">Alterar as propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="3373a-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="3373a-p105">Para alterar propriedades para um conjunto específico de conta de usuário, você pode usar a combinação dos cmdlets **Get-AzureADUser**, **onde**e **Set-AzureADUser** . O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para França:</span><span class="sxs-lookup"><span data-stu-id="3373a-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="3373a-149">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="3373a-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3373a-150">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-151">Localizar todas as contas de usuário que tenham sua propriedade departamento definida como "Accounting" ( **onde {$_. Departamento - eq "Accounting"}** ) e enviar as informações resultantes para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-152">Defina o local do usuário para França ( **Set-AzureADUser-UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="3373a-153">Use o módulo do Microsoft Azure Active Directory para o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3373a-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="3373a-154">Para configurar propriedades de contas de usuário com o Microsoft Azure Active Directory módulo para Windows PowerShell, você use o cmdlet Set-MsolUser e especifique as propriedades para definir ou alterar.</span><span class="sxs-lookup"><span data-stu-id="3373a-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="3373a-155">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3373a-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="3373a-156">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="3373a-156">Change properties for a specific user account</span></span>

<span data-ttu-id="3373a-157">Para configurar as propriedades de uma conta de usuário específico, você use o cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e especifique as propriedades para definir ou alterar.</span><span class="sxs-lookup"><span data-stu-id="3373a-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="3373a-p106">Identificar a conta com o parâmetro **- UserPrincipalName** e definir ou alterar propriedades específicas com parâmetros adicionais. Aqui está uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="3373a-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="3373a-160">-Cidade "\<nome da cidade >"</span><span class="sxs-lookup"><span data-stu-id="3373a-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="3373a-161">-País "\<nome do país >"</span><span class="sxs-lookup"><span data-stu-id="3373a-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="3373a-162">-Departamento "\<nome de departamento >"</span><span class="sxs-lookup"><span data-stu-id="3373a-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="3373a-163">-DisplayName "\<nome completos do usuário >"</span><span class="sxs-lookup"><span data-stu-id="3373a-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="3373a-164">-Fax "\<número de fax >"</span><span class="sxs-lookup"><span data-stu-id="3373a-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="3373a-165">-FirstName "\<nome usuário >"</span><span class="sxs-lookup"><span data-stu-id="3373a-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="3373a-166">-LastName "\<sobrenome do usuário >"</span><span class="sxs-lookup"><span data-stu-id="3373a-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="3373a-167">-MobilePhone "\<o número de telefone celular >"</span><span class="sxs-lookup"><span data-stu-id="3373a-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="3373a-168">-Office "\<local do escritório >"</span><span class="sxs-lookup"><span data-stu-id="3373a-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="3373a-169">-PhoneNumber "\<o número de telefone do escritório >"</span><span class="sxs-lookup"><span data-stu-id="3373a-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="3373a-170">-PostalCode "\<CEP >"</span><span class="sxs-lookup"><span data-stu-id="3373a-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="3373a-171">-PreferredLanguage "\<idioma >"</span><span class="sxs-lookup"><span data-stu-id="3373a-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="3373a-172">-State "\<estado nome >"</span><span class="sxs-lookup"><span data-stu-id="3373a-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="3373a-173">-StreetAddress "\<endereço >"</span><span class="sxs-lookup"><span data-stu-id="3373a-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="3373a-174">-Title "\<nome título >"</span><span class="sxs-lookup"><span data-stu-id="3373a-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="3373a-175">-UsageLocation "\<código de país ou região 2 caracteres >"</span><span class="sxs-lookup"><span data-stu-id="3373a-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="3373a-176">Este é o código de região ou país com duas letras ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="3373a-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="3373a-177">Consulte [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="3373a-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="3373a-178">Para ver os nomes de entidade de usuário de todos os seus usuários, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="3373a-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="3373a-179">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="3373a-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3373a-180">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-181">Classifique a lista de nomes de entidade de usuário em ordem alfabética ( **Objeto Sort UserPrincipalName** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-182">Exiba apenas a propriedade de nome Principal de usuário para cada conta ( **UserPrincipalName Select-Object** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="3373a-183">Exibi-las uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="3373a-p107">Esse comando listará todas as suas contas. Se você quiser exibir o nome Principal de usuário para uma conta com base em sua exibição nome (nome e sobrenome), preencha a variável **$userName** abaixo (removendo o \< e > caracteres), e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="3373a-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="3373a-186">Este exemplo exibe o nome Principal de usuário para o usuário chamado Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="3373a-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="3373a-p108">Usando uma variável de **$upn** , você pode fazer alterações para contas individuais com base em seu nome para exibição. Aqui está um exemplo de definição de local de uso de Belinda Newman como França, mas especificando seu nome para exibição em vez de seu nome Principal de usuário:</span><span class="sxs-lookup"><span data-stu-id="3373a-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="3373a-189">Alterar propriedades para todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="3373a-189">Change properties for all user accounts</span></span>

<span data-ttu-id="3373a-p109">Para alterar propriedades para todos os usuários, você pode usar a combinação dos cmdlets **Get-MsolUser** e **Set-MsolUser**. O exemplo a seguir altera o local de uso de todos os usuários para França:</span><span class="sxs-lookup"><span data-stu-id="3373a-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="3373a-192">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="3373a-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3373a-193">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-194">Defina o local do usuário para França ( **Set-MsolUser-UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="3373a-195">Alterar as propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="3373a-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="3373a-p110">Para alterar propriedades para um conjunto específico de conta de usuário, você pode usar a combinação dos cmdlets **Get-MsolUser**, **Where-Object**e **Set-MsolUser** . O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para França:</span><span class="sxs-lookup"><span data-stu-id="3373a-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="3373a-198">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="3373a-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="3373a-199">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-200">Localizar todas as contas de usuário que tenham sua propriedade departamento definido como "Accounting" ( **Where-Object {$_. Departamento - eq "Accounting"}** ) e enviar as informações resultantes para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="3373a-201">Defina o local do usuário para França ( **Set-MsolUser-UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="3373a-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="3373a-202">Confira também</span><span class="sxs-lookup"><span data-stu-id="3373a-202">See also</span></span>

[<span data-ttu-id="3373a-203">Gerenciar contas de usuário e licenças usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3373a-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3373a-204">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3373a-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3373a-205">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3373a-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
