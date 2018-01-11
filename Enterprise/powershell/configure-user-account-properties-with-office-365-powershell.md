---
title: "Configurar propriedades da conta de usuário com o Office 365 PowerShell"
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Resumo: Usar o PowerShell do Office 365 para configurar propriedades de um indivíduo ou várias contas de usuário no seu locatário do Office 365."
ms.openlocfilehash: eac568d20d1b33e06c37e920f9fd31582c8bb648
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="d0371-103">Configurar propriedades da conta de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0371-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="d0371-104">**Resumo:** Use o Office 365 PowerShell para configurar propriedades de um indivíduo ou várias contas de usuário no seu locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d0371-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="d0371-105">Embora você possa usar o Centro de administração do Office 365 para configurar propriedades para as contas de usuário do seu locatário do Office 365, você também pode usar o PowerShell do Office 365 e fazer algumas coisas que não é possível o Centro de administração do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d0371-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d0371-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="d0371-106">Before you begin</span></span>

<span data-ttu-id="d0371-p101">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d0371-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d0371-109">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="d0371-109">Change properties for a specific user account</span></span>

<span data-ttu-id="d0371-p102">Para configurar as propriedades de uma conta de usuário específico, você use o cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e especifique as propriedades para definir ou alterar. Este exemplo de comando altera o local de uso de Belinda Newman para França:</span><span class="sxs-lookup"><span data-stu-id="d0371-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="d0371-p103">Identificar a conta com o parâmetro **- UserPrincipalName** e definir ou alterar propriedades específicas com parâmetros adicionais. Aqui está uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="d0371-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d0371-114">-Cidade "\<nome da cidade >"</span><span class="sxs-lookup"><span data-stu-id="d0371-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d0371-115">-País "\<nome do país >"</span><span class="sxs-lookup"><span data-stu-id="d0371-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d0371-116">-Departamento "\<nome de departamento >"</span><span class="sxs-lookup"><span data-stu-id="d0371-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d0371-117">-DisplayName "\<nome completos do usuário >"</span><span class="sxs-lookup"><span data-stu-id="d0371-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d0371-118">-Fax "\<número de fax >"</span><span class="sxs-lookup"><span data-stu-id="d0371-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="d0371-119">-FirstName "\<nome usuário >"</span><span class="sxs-lookup"><span data-stu-id="d0371-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="d0371-120">-LastName "\<sobrenome do usuário >"</span><span class="sxs-lookup"><span data-stu-id="d0371-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="d0371-121">-MobilePhone "\<o número de telefone celular >"</span><span class="sxs-lookup"><span data-stu-id="d0371-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d0371-122">-Office "\<local do escritório >"</span><span class="sxs-lookup"><span data-stu-id="d0371-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="d0371-123">-PhoneNumber "\<o número de telefone do escritório >"</span><span class="sxs-lookup"><span data-stu-id="d0371-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d0371-124">-PostalCode "\<CEP >"</span><span class="sxs-lookup"><span data-stu-id="d0371-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d0371-125">-PreferredLanguage "\<idioma >"</span><span class="sxs-lookup"><span data-stu-id="d0371-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d0371-126">-State "\<estado nome >"</span><span class="sxs-lookup"><span data-stu-id="d0371-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d0371-127">-StreetAddress "\<endereço >"</span><span class="sxs-lookup"><span data-stu-id="d0371-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d0371-128">-Title "\<nome título >"</span><span class="sxs-lookup"><span data-stu-id="d0371-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="d0371-129">-UsageLocation "\<código de país ou região 2 caracteres >"</span><span class="sxs-lookup"><span data-stu-id="d0371-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d0371-130">Este é o código de região ou país com duas letras ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="d0371-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d0371-131">Consulte [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d0371-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="d0371-132">Para ver os nomes de entidade de usuário de todos os seus usuários, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="d0371-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="d0371-133">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="d0371-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d0371-134">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-135">Classifique a lista de nomes de entidade de usuário em ordem alfabética ( **Objeto Sort UserPrincipalName** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-136">Exiba apenas a propriedade de nome Principal de usuário para cada conta ( **UserPrincipalName Select-Object** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="d0371-137">Exibi-las uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d0371-p104">Esse comando listará todas as suas contas. Se você quiser exibir o nome Principal de usuário para uma conta com base em sua exibição nome (nome e sobrenome), preencha a variável **$userName** abaixo (removendo o \< e > caracteres), e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d0371-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d0371-140">Este exemplo exibe o nome Principal de usuário para o usuário chamado Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="d0371-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d0371-p105">Usando uma variável de **$upn** , você pode fazer alterações para contas individuais com base em seu nome para exibição. Aqui está um exemplo de definição de local de uso de Belinda Newman como França, mas especificando seu nome para exibição em vez de seu nome Principal de usuário:</span><span class="sxs-lookup"><span data-stu-id="d0371-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d0371-143">Alterar propriedades para todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="d0371-143">Change properties for all user accounts</span></span>

<span data-ttu-id="d0371-p106">Para alterar propriedades para todos os usuários, você pode usar a combinação dos cmdlets **Get-MsolUser** e **Set-MsolUser** . O exemplo a seguir altera o local de uso para todos os usuários para França:</span><span class="sxs-lookup"><span data-stu-id="d0371-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d0371-146">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="d0371-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d0371-147">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-148">Defina o local do usuário para França ( **Set-MsolUser-UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d0371-149">Alterar as propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="d0371-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d0371-p107">Para alterar propriedades para um conjunto específico de conta de usuário, você pode usar a combinação dos cmdlets **Get-MsolUser**, **Where-Object**e **Set-MsolUser** . O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para França:</span><span class="sxs-lookup"><span data-stu-id="d0371-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d0371-152">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="d0371-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d0371-153">Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-154">Localizar todas as contas de usuário que tenham sua propriedade departamento definido como "Accounting" ( **Where-Object {$_. Departamento - eq "Accounting"}** ) e enviar as informações resultantes para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-155">Defina o local do usuário para França ( **Set-MsolUser-UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="d0371-156">Exibi-las uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="d0371-157">Use o módulo do Azure Active Directory V2 PowerShell para configurar propriedades da conta de usuário</span><span class="sxs-lookup"><span data-stu-id="d0371-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="d0371-p108">Para configurar as propriedades de contas de usuário com o módulo do Azure Active Directory PowerShell V2, você use o cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e especifique as propriedades para definir ou alterar. Mas, primeiro, você deve se conectar à sua assinatura. Para ver as instruções, consulte [Connect com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="d0371-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d0371-161">Alterar as propriedades de uma conta de usuário específica</span><span class="sxs-lookup"><span data-stu-id="d0371-161">Change properties for a specific user account</span></span>

<span data-ttu-id="d0371-162">Este exemplo de comando altera o local de uso de Belinda Newman para França:</span><span class="sxs-lookup"><span data-stu-id="d0371-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="d0371-p109">Identificar a conta com o parâmetro **- ObjectID** e definir ou alterar propriedades específicas com parâmetros adicionais. Aqui está uma lista dos parâmetros mais comuns.</span><span class="sxs-lookup"><span data-stu-id="d0371-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d0371-165">-Departamento "\<nome de departamento >"</span><span class="sxs-lookup"><span data-stu-id="d0371-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d0371-166">-DisplayName "\<nome completos do usuário >"</span><span class="sxs-lookup"><span data-stu-id="d0371-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d0371-167">-FacsimilieTelephoneNumber "\<número de fax >"</span><span class="sxs-lookup"><span data-stu-id="d0371-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="d0371-168">-GivenName "\<nome usuário >"</span><span class="sxs-lookup"><span data-stu-id="d0371-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="d0371-169">-Sobrenome "\<sobrenome do usuário >"</span><span class="sxs-lookup"><span data-stu-id="d0371-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="d0371-170">-Móvel "\<o número de telefone celular >"</span><span class="sxs-lookup"><span data-stu-id="d0371-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d0371-171">-JobTitle "\<cargo >"</span><span class="sxs-lookup"><span data-stu-id="d0371-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="d0371-172">-PreferredLanguage "\<idioma >"</span><span class="sxs-lookup"><span data-stu-id="d0371-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d0371-173">-StreetAddress "\<endereço >"</span><span class="sxs-lookup"><span data-stu-id="d0371-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d0371-174">-Cidade "\<nome da cidade >"</span><span class="sxs-lookup"><span data-stu-id="d0371-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d0371-175">-State "\<estado nome >"</span><span class="sxs-lookup"><span data-stu-id="d0371-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d0371-176">-PostalCode "\<CEP >"</span><span class="sxs-lookup"><span data-stu-id="d0371-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d0371-177">-País "\<nome do país >"</span><span class="sxs-lookup"><span data-stu-id="d0371-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d0371-178">-TelephoneNumber "\<o número de telefone do escritório >"</span><span class="sxs-lookup"><span data-stu-id="d0371-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d0371-179">-UsageLocation "\<código de país ou região 2 caracteres >"</span><span class="sxs-lookup"><span data-stu-id="d0371-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d0371-180">Este é o código de região ou país com duas letras ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="d0371-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d0371-181">Consulte [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d0371-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="d0371-182">Para exibir o nome Principal de usuário para suas contas de usuário, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="d0371-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="d0371-183">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="d0371-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d0371-184">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-185">Classifique a lista de nomes de entidade de usuário em ordem alfabética ( **Objeto Sort UserPrincipalName** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-186">Exiba apenas a propriedade de nome Principal de usuário para cada conta ( **UserPrincipalName Select-Object** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="d0371-187">Exibi-las uma tela por vez ( **mais** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d0371-p110">Esse comando listará todas as suas contas. Se você quiser exibir o nome Principal de usuário para uma conta com base em sua exibição nome (nome e sobrenome), preencha a variável **$userName** abaixo (removendo o \< e > caracteres), e, em seguida, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d0371-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d0371-190">Este exemplo exibe o nome Principal de usuário para o usuário chamado Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="d0371-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d0371-p111">Usando uma variável de **$upn** , você pode fazer alterações para contas individuais com base em seu nome para exibição. Aqui está um exemplo de definição de local de uso de Belinda Newman como França, mas especificando seu nome para exibição em vez de seu nome Principal de usuário:</span><span class="sxs-lookup"><span data-stu-id="d0371-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d0371-193">Alterar propriedades para todas as contas de usuário</span><span class="sxs-lookup"><span data-stu-id="d0371-193">Change properties for all user accounts</span></span>

<span data-ttu-id="d0371-p112">Para alterar propriedades para todos os usuários, você pode usar a combinação dos cmdlets **Get-AzureADUser** e **Set-AzureADUser** . O exemplo a seguir altera o local de uso para todos os usuários para França:</span><span class="sxs-lookup"><span data-stu-id="d0371-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d0371-196">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="d0371-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d0371-197">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-198">Defina o local do usuário para França ( **Set-AzureADUser-UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d0371-199">Alterar as propriedades de um conjunto específico de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="d0371-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d0371-p113">Para alterar propriedades para um conjunto específico de conta de usuário, você pode usar a combinação dos cmdlets **Get-AzureADUser**, **onde**e **Set-AzureADUser** . O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para França:</span><span class="sxs-lookup"><span data-stu-id="d0371-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d0371-202">Este comando instrui o Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="d0371-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d0371-203">Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-204">Localizar todas as contas de usuário que tenham sua propriedade departamento definida como "Accounting" ( **onde {$_. Departamento - eq "Accounting"}** ) e enviar as informações resultantes para o próximo comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d0371-205">Defina o local do usuário para França ( **Set-AzureADUser-UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="d0371-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d0371-206">Veja também</span><span class="sxs-lookup"><span data-stu-id="d0371-206">See also</span></span>

#### 

[<span data-ttu-id="d0371-207">Gerenciar contas de usuário e licenças usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="d0371-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d0371-208">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0371-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d0371-209">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0371-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

