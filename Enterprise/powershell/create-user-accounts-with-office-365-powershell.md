---
title: Criar contas de usuários usando o Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Saiba como usar o Office 365 PowerShell para criar contas de usuários no Office 365.
ms.openlocfilehash: e5fed572d0b835a42071e77b4aeaf8714f2178bd
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
ms.locfileid: "17553254"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="fd9dc-103">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd9dc-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="fd9dc-104">**Resumo:** saiba como usar o Office 365 PowerShell para criar contas de usuários no Office 365.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="fd9dc-p101">Você pode usar o Office 365 PowerShell para criar contas de usuários de forma eficiente, especialmente para várias contas de usuários. Quando você cria contas de usuários no Office 365 PowerShell, determinadas propriedades de conta são sempre obrigatórias. Outras propriedades, embora sejam importantes, não são obrigatórias para a criação de contas. Essas propriedades estão descritas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="fd9dc-109">**Nome da propriedade**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-109">**Property name**</span></span>|<span data-ttu-id="fd9dc-110">**Obrigatório?**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-110">**Required?**</span></span>|<span data-ttu-id="fd9dc-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="fd9dc-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="fd9dc-113">Sim</span><span class="sxs-lookup"><span data-stu-id="fd9dc-113">Yes</span></span>  <br/> |<span data-ttu-id="fd9dc-p102">Esse é o nome para exibição usado nos serviços do Office 365. Por exemplo, Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="fd9dc-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="fd9dc-117">Sim</span><span class="sxs-lookup"><span data-stu-id="fd9dc-117">Yes</span></span>  <br/> |<span data-ttu-id="fd9dc-p103">Esse é o nome da conta usado para entrar nos serviços do Office 365. Por exemplo, carlosl@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="fd9dc-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-120">**FirstName**</span></span> <br/> |<span data-ttu-id="fd9dc-121">Não</span><span class="sxs-lookup"><span data-stu-id="fd9dc-121">No</span></span>  <br/> ||
|<span data-ttu-id="fd9dc-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-122">**LastName**</span></span> <br/> |<span data-ttu-id="fd9dc-123">Não</span><span class="sxs-lookup"><span data-stu-id="fd9dc-123">No</span></span>  <br/> ||
|<span data-ttu-id="fd9dc-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="fd9dc-125">Não</span><span class="sxs-lookup"><span data-stu-id="fd9dc-125">No</span></span>  <br/> |<span data-ttu-id="fd9dc-p104">Esse é o plano de licenciamento (também conhecido como plano de licença, plano do Office 365 ou SKU) do qual uma licença disponível será atribuída à conta do usuário. A licença determina os serviços do Office 365 que estão disponíveis para a conta. Não é necessário atribuir uma licença a um usuário ao criar a conta, mas a conta requer uma licença para acessar os serviços do Office 365. Você tem 30 dias para licenciar a conta de usuário depois de criá-la.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="fd9dc-p105">Use o cmdlet **Get-MsolAccountSku** para exibir os planos de licenciamento ( **AccountSkuId** ) e as licenças disponíveis na organização. Para saber mais, confira o artigo [Exibir licenças e serviços com o PowerShell do Office 365](view-licenses-and-services-with-office-365-powershell.md).  </span><span class="sxs-lookup"><span data-stu-id="fd9dc-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span></span><br/> |
|<span data-ttu-id="fd9dc-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-132">**Password**</span></span> <br/> |<span data-ttu-id="fd9dc-133">Não</span><span class="sxs-lookup"><span data-stu-id="fd9dc-133">No</span></span>  <br/> | <span data-ttu-id="fd9dc-p106">Caso não especifique uma senha, nosso sistema atribuirá uma senha aleatória para a conta do usuário e a senha ficará visível nos resultados do comando. Se você especificar uma senha, ela deverá atender aos seguintes requisitos de complexidade:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="fd9dc-136">Ter de 8 a 16 caracteres de texto ASCII.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="fd9dc-137">Incluir caracteres dos três tipos a seguir: letras maiúsculas, letras minúsculas, números e símbolos.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="fd9dc-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="fd9dc-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="fd9dc-139">Não</span><span class="sxs-lookup"><span data-stu-id="fd9dc-139">No</span></span>  <br/> |<span data-ttu-id="fd9dc-p107">Esse é um código de país ISO 3166-1 alpha 2 válido. Por exemplo, FR para França e BR para Brasil. É importante fornecer esse valor, pois alguns serviços do Office 365 não estão disponíveis em certos países/regiões. Portanto, apenas será possível atribuir uma licença a uma conta de usuário depois de configurar esse valor na conta. Para saber mais, confira o artigo [Sobre restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="fd9dc-144">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="fd9dc-144">Before you begin</span></span>

<span data-ttu-id="fd9dc-p108">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="fd9dc-147">Use o Office 365 PowerShell para criar contas de usuários individuais</span><span class="sxs-lookup"><span data-stu-id="fd9dc-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="fd9dc-148">Para criar uma conta individual, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="fd9dc-149">Nesse exemplo, criamos uma conta para o usuário chamado Carlos Lima do Brasil e atribuímos uma licença do plano de licenciamento  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="fd9dc-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="fd9dc-150">Use o Office 365 PowerShell para criar várias contas de usuários</span><span class="sxs-lookup"><span data-stu-id="fd9dc-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="fd9dc-p109">Crie um arquivo CSV (arquivo de valores separados por vírgula ) que inclua as informações necessárias da conta do usuário. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="fd9dc-153">Os nomes de coluna e a respectiva ordem na primeira linha do arquivo CSV são arbitrários, mas você pode verificar se os dados no restante do arquivo correspondem à ordem dos nomes e usar esses nomes para os valores de parâmetro, no comando do Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="fd9dc-154">Use a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="fd9dc-155">Nesse exemplo, criamos as contas de usuários do arquivo C:\Meus Documentos\NewAccounts.csv e registramos os resultados no arquivo C:\Meus Documentos\NewAccountResults.csv</span><span class="sxs-lookup"><span data-stu-id="fd9dc-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="fd9dc-p110">Examine o arquivo de saída para conferir os resultados. Não especificamos senhas, de modo que as senhas aleatórias geradas ficam visíveis no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="fd9dc-158">Use o módulo PowerShell do Azure Active Directory V2 para criar contas de usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="fd9dc-p111">Para usar o cmdlet **New-AzureADUser** no módulo do PowerShell Azure Active Directory V2, conecte-se primeiro à sua assinatura. Para conhecer as instruções, confira [Conectar-se com o módulo do PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="fd9dc-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="fd9dc-161">Depois de se conectar, use a seguinte sintaxe para criar uma conta de individual:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="fd9dc-162">Neste exemplo, criamos uma conta para o usuário chamado Carlos Lima do Brasil:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="fd9dc-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd9dc-163">See also</span></span>

<span data-ttu-id="fd9dc-164">Confira estes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-164">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="fd9dc-165">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd9dc-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fd9dc-166">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd9dc-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fd9dc-167">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="fd9dc-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fd9dc-168">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd9dc-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="fd9dc-169">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="fd9dc-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="fd9dc-170">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="fd9dc-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [<span data-ttu-id="fd9dc-171">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="fd9dc-171">Import-Csv</span></span>](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [<span data-ttu-id="fd9dc-172">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="fd9dc-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="fd9dc-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="fd9dc-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="fd9dc-174">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="fd9dc-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

