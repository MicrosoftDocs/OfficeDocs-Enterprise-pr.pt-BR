---
title: Criar contas de usuários usando o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Saiba como usar o Office 365 PowerShell para criar contas de usuários no Office 365.
ms.openlocfilehash: 3247f9d047ca7e7e99c3c0b0900c356854ce3d75
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844242"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="4aafa-103">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4aafa-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="4aafa-p101">Você pode usar o Office 365 PowerShell para criar contas de usuários de forma eficiente, especialmente para várias contas de usuários. Quando você cria contas de usuários no Office 365 PowerShell, determinadas propriedades de conta são sempre obrigatórias. Outras propriedades, embora sejam importantes, não são obrigatórias para a criação de contas. Essas propriedades estão descritas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="4aafa-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="4aafa-108">**Nome da propriedade**</span><span class="sxs-lookup"><span data-stu-id="4aafa-108">**Property name**</span></span>|<span data-ttu-id="4aafa-109">**Obrigatório?**</span><span class="sxs-lookup"><span data-stu-id="4aafa-109">**Required?**</span></span>|<span data-ttu-id="4aafa-110">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4aafa-110">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4aafa-111">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="4aafa-111">**DisplayName**</span></span> <br/> |<span data-ttu-id="4aafa-112">Sim</span><span class="sxs-lookup"><span data-stu-id="4aafa-112">Yes</span></span>  <br/> |<span data-ttu-id="4aafa-p102">Esse é o nome para exibição usado nos serviços do Office 365. Por exemplo, Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="4aafa-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="4aafa-115">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="4aafa-115">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="4aafa-116">Sim</span><span class="sxs-lookup"><span data-stu-id="4aafa-116">Yes</span></span>  <br/> |<span data-ttu-id="4aafa-p103">Esse é o nome da conta usado para entrar nos serviços do Office 365. Por exemplo, carlosl@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="4aafa-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="4aafa-119">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="4aafa-119">**FirstName**</span></span> <br/> |<span data-ttu-id="4aafa-120">Não</span><span class="sxs-lookup"><span data-stu-id="4aafa-120">No</span></span>  <br/> ||
|<span data-ttu-id="4aafa-121">**LastName**</span><span class="sxs-lookup"><span data-stu-id="4aafa-121">**LastName**</span></span> <br/> |<span data-ttu-id="4aafa-122">Não</span><span class="sxs-lookup"><span data-stu-id="4aafa-122">No</span></span>  <br/> ||
|<span data-ttu-id="4aafa-123">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="4aafa-123">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="4aafa-124">Não</span><span class="sxs-lookup"><span data-stu-id="4aafa-124">No</span></span>  <br/> |<span data-ttu-id="4aafa-p104">Esse é o plano de licenciamento (também conhecido como plano de licença, plano do Office 365 ou SKU) do qual uma licença disponível será atribuída à conta do usuário. A licença determina os serviços do Office 365 disponíveis para a conta. Não é necessário atribuir uma licença a um usuário ao criar a conta, mas a conta requer uma licença para acessar os serviços do Office 365. Você tem 30 dias para licenciar a conta de usuário depois de criá-la.</span><span class="sxs-lookup"><span data-stu-id="4aafa-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="4aafa-129">**Password**</span><span class="sxs-lookup"><span data-stu-id="4aafa-129">**Password**</span></span> <br/> |<span data-ttu-id="4aafa-130">Não</span><span class="sxs-lookup"><span data-stu-id="4aafa-130">No</span></span>  <br/> | <span data-ttu-id="4aafa-p105">Caso não especifique uma senha, nosso sistema atribuirá uma senha aleatória para a conta do usuário e a senha ficará visível nos resultados do comando. Se você especificar uma senha, ela deverá Se você especificar uma senha, ela precisará ter de 8 a 16 caracteres de texto ASCII de qualquer um dos três tipos a seguir: letras minúsculas, letras maiúsculas, números e símbolos.</span><span class="sxs-lookup"><span data-stu-id="4aafa-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="4aafa-133">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="4aafa-133">**UsageLocation**</span></span> <br/> |<span data-ttu-id="4aafa-134">Não</span><span class="sxs-lookup"><span data-stu-id="4aafa-134">No</span></span>  <br/> |<span data-ttu-id="4aafa-p106">Esse é um código de país ISO 3166-1 alpha 2 válido. Por exemplo, FR para França e BR para Brasil. É importante fornecer esse valor, pois alguns serviços do Office 365 não estão disponíveis em certos países/regiões. Portanto, só será possível atribuir uma licença a uma conta de usuário após configurar esse valor na conta. Confira mais informações no artigo [Sobre restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="4aafa-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="4aafa-139">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="4aafa-139">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="4aafa-140">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="4aafa-140">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="4aafa-141">Depois de se conectar, use a seguinte sintaxe para criar uma conta individual:</span><span class="sxs-lookup"><span data-stu-id="4aafa-141">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="4aafa-142">Neste exemplo, criamos uma conta para o usuário chamado Carlos Lima do Brasil:</span><span class="sxs-lookup"><span data-stu-id="4aafa-142">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="4aafa-143">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4aafa-143">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="4aafa-144">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="4aafa-144">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="4aafa-145">Criar uma conta de usuário individual</span><span class="sxs-lookup"><span data-stu-id="4aafa-145">Create an individual user account</span></span>

<span data-ttu-id="4aafa-146">Para criar uma conta individual, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="4aafa-146">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="4aafa-147">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="4aafa-147">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="4aafa-148">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4aafa-148">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="4aafa-149">Para listar os nomes do plano de licenciamento disponível, use este comando:</span><span class="sxs-lookup"><span data-stu-id="4aafa-149">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="4aafa-150">Nesse exemplo, criamos uma conta para o usuário chamado Carlos Lima do Brasil e atribuímos uma licença do plano de licenciamento `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="4aafa-150">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="4aafa-151">Criar várias contas de usuários</span><span class="sxs-lookup"><span data-stu-id="4aafa-151">Create multiple user accounts</span></span>

1. <span data-ttu-id="4aafa-p108">Crie um arquivo CSV (arquivo de valores separados por vírgula) que inclua as informações necessárias da conta do usuário. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4aafa-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="4aafa-154">Os nomes de coluna e a respectiva ordem na primeira linha do arquivo CSV são arbitrários, mas você pode verificar se os dados no restante do arquivo correspondem à ordem dos nomes e usar esses nomes para os valores de parâmetro, no comando do Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4aafa-154">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="4aafa-155">Use a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="4aafa-155">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="4aafa-156">Nesse exemplo, criamos as contas de usuários do arquivo C:\Meus Documentos\NewAccounts.csv e registramos os resultados no arquivo C:\Meus Documentos\NewAccountResults.csv</span><span class="sxs-lookup"><span data-stu-id="4aafa-156">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="4aafa-p109">Examine o arquivo de saída para conferir os resultados. Não especificamos senhas, de modo que as senhas aleatórias que o Office 365 gerou ficam visíveis no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="4aafa-p109">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="4aafa-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="4aafa-159">See also</span></span>

[<span data-ttu-id="4aafa-160">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4aafa-160">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="4aafa-161">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4aafa-161">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4aafa-162">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4aafa-162">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
