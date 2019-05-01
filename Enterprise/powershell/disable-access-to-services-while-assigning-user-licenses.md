---
title: Desabilitar o acesso aos serviços na atribuição de licenças de usuário
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Saiba como atribuir licenças a contas de usuário e desabilitar planos de serviço específicos ao mesmo tempo usando o Office 365 PowerShell.
ms.openlocfilehash: c93f54fcd5716a0ea53290c24a2594b8bc63cecf
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491307"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="e3294-103">Desabilitar o acesso aos serviços na atribuição de licenças de usuário</span><span class="sxs-lookup"><span data-stu-id="e3294-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="e3294-104">**Resumo:**  Saiba como atribuir licenças a contas de usuário e desabilitar planos de serviço específicos ao mesmo tempo usando o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3294-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="e3294-105">As assinaturas do Office 365 vêm com planos de serviço para serviços individuais.</span><span class="sxs-lookup"><span data-stu-id="e3294-105">Office 365 subscriptions come with service plans for individual services.</span></span> <span data-ttu-id="e3294-106">Os administradores do Office 365 geralmente precisam desabilitar determinados planos ao atribuir licenças aos usuários.</span><span class="sxs-lookup"><span data-stu-id="e3294-106">Office 365 administrators often need to disable certain plans when assigning licenses to users.</span></span> <span data-ttu-id="e3294-107">Com as instruções deste artigo, você pode atribuir uma licença do Office 365 enquanto desabilita os planos de serviço específicos usando o PowerShell para uma conta de usuário individual ou várias contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="e3294-107">With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>


## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e3294-108">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3294-108">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e3294-109">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e3294-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="e3294-110">Em seguida, execute este comando para ver suas assinaturas atuais:</span><span class="sxs-lookup"><span data-stu-id="e3294-110">Next, run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="e3294-111">Na exibição do `Get-MsolAccountSku` comando:</span><span class="sxs-lookup"><span data-stu-id="e3294-111">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="e3294-112">**AccountSkuId** é uma assinatura da sua organização no \<formato OrganizationName>\<: Subscription>.</span><span class="sxs-lookup"><span data-stu-id="e3294-112">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format.</span></span> <span data-ttu-id="e3294-113">O \<OrganizationName> é o valor que você forneceu quando você registrou no Office 365 e é exclusivo para sua organização.</span><span class="sxs-lookup"><span data-stu-id="e3294-113">The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="e3294-114">O \<valor Subscription> é para uma assinatura específica.</span><span class="sxs-lookup"><span data-stu-id="e3294-114">The \<Subscription> value is for a specific subscription.</span></span> <span data-ttu-id="e3294-115">Por exemplo, para litwareinc: ENTERPRISEPACK, o nome da organização é litwareinc e o nome da assinatura é ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="e3294-115">For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="e3294-116">**ActiveUnits** é o número de licenças que você comprou para a assinatura.</span><span class="sxs-lookup"><span data-stu-id="e3294-116">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="e3294-117">**WarningUnits** é o número de licenças em uma assinatura que você não renovou e que expirarão após o período de cortesia de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="e3294-117">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="e3294-118">**ConsumedUnits** é o número de licenças que você atribuiu aos usuários para a assinatura.</span><span class="sxs-lookup"><span data-stu-id="e3294-118">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="e3294-119">Observe o AccountSkuId para sua assinatura do Office 365 que contém os usuários que você deseja licenciar.</span><span class="sxs-lookup"><span data-stu-id="e3294-119">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license.</span></span> <span data-ttu-id="e3294-120">Além disso, verifique se há licenças suficientes para atribuir (subtrair **ConsumedUnits** de **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="e3294-120">Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="e3294-121">Em seguida, execute este comando para ver os detalhes sobre os planos de serviço do Office 365 que estão disponíveis em todas as suas assinaturas:</span><span class="sxs-lookup"><span data-stu-id="e3294-121">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="e3294-122">Na exibição desse comando, determine quais planos de serviço você deseja desabilitar ao atribuir licenças aos usuários.</span><span class="sxs-lookup"><span data-stu-id="e3294-122">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="e3294-123">Veja a seguir uma lista parcial de planos de serviço e seus serviços do Office 365 correspondentes.</span><span class="sxs-lookup"><span data-stu-id="e3294-123">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="e3294-124">A tabela a seguir mostra os planos de serviço do Office 365 e seus nomes amigáveis para os serviços mais comuns.</span><span class="sxs-lookup"><span data-stu-id="e3294-124">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="e3294-125">Sua lista de planos de serviço pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="e3294-125">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="e3294-126">**Plano de serviço**</span><span class="sxs-lookup"><span data-stu-id="e3294-126">**Service plan**</span></span>|<span data-ttu-id="e3294-127">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e3294-127">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="e3294-128">Sway</span><span class="sxs-lookup"><span data-stu-id="e3294-128">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="e3294-129">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e3294-129">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="e3294-130">Yammer</span><span class="sxs-lookup"><span data-stu-id="e3294-130">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="e3294-131">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="e3294-131">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="e3294-132">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="e3294-132">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="e3294-133">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="e3294-133">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="e3294-134">Office Online</span><span class="sxs-lookup"><span data-stu-id="e3294-134">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="e3294-135">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e3294-135">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="e3294-136">Plano 2 do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="e3294-136">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="e3294-137">Para obter uma lista completa de planos de licença (também conhecidos como nomes de produtos), seus planos de serviço incluídos e seus nomes amigáveis correspondentes, confira [nomes de produtos e identificadores de planos de serviço para licenciamento](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="e3294-137">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="e3294-138">Agora que você tem o AccountSkuId e os planos de serviço para desabilitar, é possível atribuir licenças para um usuário individual ou para vários usuários.</span><span class="sxs-lookup"><span data-stu-id="e3294-138">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="e3294-139">Para um único usuário</span><span class="sxs-lookup"><span data-stu-id="e3294-139">For a single user</span></span>

<span data-ttu-id="e3294-140">Para um único usuário, preencha o nome principal do usuário da conta de usuário, o AccountSkuId e a lista de planos de serviço para desabilitar e remover o texto explicativo e \< os caracteres e >.</span><span class="sxs-lookup"><span data-stu-id="e3294-140">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="e3294-141">Em seguida, execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3294-141">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="e3294-142">Aqui está um exemplo de bloco de comando para a conta chamada belindan@contoso.com, para a licença contoso: ENTERPRISEPACK e os planos de serviço a serem desabilitados são RMS_S_ENTERPRISE, SWAY, INTUNE_O365 e YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="e3294-142">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

### <a name="for-multiple-users"></a><span data-ttu-id="e3294-143">Para vários usuários</span><span class="sxs-lookup"><span data-stu-id="e3294-143">For multiple users</span></span>

<span data-ttu-id="e3294-144">Para executar essa tarefa de administração para vários usuários, crie um arquivo de texto de valor separado por vírgula (CSV) que contenha os campos UserPrincipalName e UsageLocation.</span><span class="sxs-lookup"><span data-stu-id="e3294-144">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields.</span></span> <span data-ttu-id="e3294-145">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="e3294-145">Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="e3294-146">Em seguida, preencha o local dos arquivos CSV de entrada e saída, a ID SKU da conta e a lista de planos de serviço a serem desabilitados e, em seguida, execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3294-146">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="e3294-147">Este bloco de comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e3294-147">This PowerShell command block:</span></span>
  
- <span data-ttu-id="e3294-148">Exibe o nome principal do usuário de cada usuário.</span><span class="sxs-lookup"><span data-stu-id="e3294-148">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="e3294-149">Atribui licenças personalizadas a cada usuário.</span><span class="sxs-lookup"><span data-stu-id="e3294-149">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="e3294-150">Cria um arquivo CSV com todos os usuários que foram processados e mostra o status da licença.</span><span class="sxs-lookup"><span data-stu-id="e3294-150">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e3294-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="e3294-151">See also</span></span>

[<span data-ttu-id="e3294-152">Desabilitar o acesso aos serviços com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3294-152">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="e3294-153">Desabilitar o acesso ao Sway com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3294-153">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="e3294-154">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3294-154">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e3294-155">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3294-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

