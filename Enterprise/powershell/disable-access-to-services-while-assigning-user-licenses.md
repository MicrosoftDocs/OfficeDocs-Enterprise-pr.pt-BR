---
title: Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Saiba como atribuir licenças às contas de usuário e desativar os planos de serviço específico ao mesmo tempo usando o PowerShell do Office 365.
ms.openlocfilehash: 7567d84490cdb3db7c149a51c4f2f04d39cad9ce
ms.sourcegitcommit: def3e311db9322e469753bac59ff03624349b140
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="253a0-103">Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário</span><span class="sxs-lookup"><span data-stu-id="253a0-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="253a0-104">**Resumo:**  Saiba como atribuir licenças às contas de usuário e desativar os planos de serviço específico ao mesmo tempo usando o PowerShell do Office 365.</span><span class="sxs-lookup"><span data-stu-id="253a0-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="253a0-p101">Assinaturas do Office 365 vêm com planos de serviço para serviços individuais. Administradores do Office 365 geralmente precisam desativar os planos de determinados ao atribuir licenças aos usuários. Com as instruções deste artigo, você pode atribuir uma licença do Office 365 ao desativar os planos de serviço específico usando o PowerShell para uma conta de usuário individual ou várias contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="253a0-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="253a0-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="253a0-108">Before you begin</span></span>

<span data-ttu-id="253a0-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="253a0-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="253a0-111">Coletar informações sobre assinaturas e planos de serviço</span><span class="sxs-lookup"><span data-stu-id="253a0-111">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="253a0-112">Execute este comando para ver suas inscrições atuais:</span><span class="sxs-lookup"><span data-stu-id="253a0-112">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="253a0-113">Na exibição do `Get-MsolAccountSku` comando:</span><span class="sxs-lookup"><span data-stu-id="253a0-113">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="253a0-p103">**AccountSkuId** é uma assinatura para sua organização no \<OrganizationName >:\<assinatura > formato. O \<OrganizationName > é o valor que você forneceu ao registrado no Office 365 e é exclusivo para a sua organização. O \<assinatura > valor é para uma inscrição específica. Por exemplo, para litwareinc: enterprisepack, o nome da organização é litwareinc e o nome da inscrição é ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="253a0-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="253a0-118">**ActiveUnits** é o número de licenças que você comprou para a assinatura.</span><span class="sxs-lookup"><span data-stu-id="253a0-118">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="253a0-119">**WarningUnits** é o número de licenças em uma assinatura que você ainda não renovado e que irá expirar após o período de carência de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="253a0-119">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="253a0-120">**ConsumedUnits** é o número de licenças que você atribuiu aos usuários para a assinatura.</span><span class="sxs-lookup"><span data-stu-id="253a0-120">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="253a0-p104">Observe o AccountSkuId para sua assinatura do Office 365 que contém os usuários que você deseja da licença. Além disso, certifique-se de que não há licenças suficientes para atribuir (subtrair **ConsumedUnits** da **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="253a0-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="253a0-123">Em seguida, execute este comando para ver os detalhes sobre os planos de serviço do Office 365 estão disponíveis em todas as suas assinaturas:</span><span class="sxs-lookup"><span data-stu-id="253a0-123">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="253a0-124">Na janela deste comando, determine quais planos de serviço que você gostaria de desabilitar ao atribuir licenças aos usuários.</span><span class="sxs-lookup"><span data-stu-id="253a0-124">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="253a0-125">Aqui está uma lista parcial de planos de serviço e seus serviços do Office 365 correspondentes.</span><span class="sxs-lookup"><span data-stu-id="253a0-125">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="253a0-126">**Plano de serviço**</span><span class="sxs-lookup"><span data-stu-id="253a0-126">**Service plan**</span></span>|<span data-ttu-id="253a0-127">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="253a0-127">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="253a0-128">SWAY</span><span class="sxs-lookup"><span data-stu-id="253a0-128">SWAY</span></span>  <br/> |<span data-ttu-id="253a0-129">Sway</span><span class="sxs-lookup"><span data-stu-id="253a0-129">Sway</span></span>  <br/> |
|<span data-ttu-id="253a0-130">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="253a0-130">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="253a0-131">Gerenciamento de Dispositivos Móveis para o Office 365</span><span class="sxs-lookup"><span data-stu-id="253a0-131">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="253a0-132">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="253a0-132">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="253a0-133">Yammer</span><span class="sxs-lookup"><span data-stu-id="253a0-133">Yammer</span></span>  <br/> |
|<span data-ttu-id="253a0-134">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="253a0-134">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="253a0-135">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="253a0-135">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="253a0-136">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="253a0-136">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="253a0-137">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="253a0-137">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="253a0-138">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="253a0-138">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="253a0-139">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="253a0-139">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="253a0-140">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="253a0-140">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="253a0-141">Office Online</span><span class="sxs-lookup"><span data-stu-id="253a0-141">Office Online</span></span>  <br/> |
|<span data-ttu-id="253a0-142">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="253a0-142">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="253a0-143">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="253a0-143">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="253a0-144">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="253a0-144">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="253a0-145">Plano 2 do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="253a0-145">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="253a0-146">Agora que você tiver o AccountSkuId e os planos de serviço para desabilitar, você pode atribuir licenças para um usuário individual ou para vários usuários.</span><span class="sxs-lookup"><span data-stu-id="253a0-146">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="253a0-147">Para um único usuário</span><span class="sxs-lookup"><span data-stu-id="253a0-147">For a single user</span></span>

<span data-ttu-id="253a0-p105">Para um único usuário, preencha o nome principal de usuário de conta de usuário, o AccountSkuId e a lista de planos de serviço desativar e remover o texto explicativo e o \< e > caracteres. Em seguida, execute os comandos resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="253a0-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="253a0-150">Aqui está um bloco de comando de exemplo para a conta denominada belindan@contoso.com, para a licença de contoso:ENTERPRISEPACK, e os planos de serviço para desabilitar são RMS_S_ENTERPRISE, SWAY, INTUNE_O365 e YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="253a0-150">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
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

## <a name="for-multiple-users"></a><span data-ttu-id="253a0-151">Para vários usuários</span><span class="sxs-lookup"><span data-stu-id="253a0-151">For multiple users</span></span>

<span data-ttu-id="253a0-p106">Para realizar essa tarefa de administração para vários usuários, crie um arquivo de texto delimitado por vírgula (CSV) que contém os campos UserPrincipalName e UsageLocation. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="253a0-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="253a0-154">Em seguida, preencha o local dos arquivos CSV de saída e a entrada, a conta de ID de SKU e a lista de planos de serviço para desabilitar e, em seguida, execute os comandos de resultantes no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="253a0-154">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="253a0-155">Este bloco de comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="253a0-155">This PowerShell command block:</span></span>
  
- <span data-ttu-id="253a0-156">Exibe o nome principal de usuário de cada usuário.</span><span class="sxs-lookup"><span data-stu-id="253a0-156">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="253a0-157">Atribui personalizados licenças para cada usuário.</span><span class="sxs-lookup"><span data-stu-id="253a0-157">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="253a0-158">Cria um arquivo CSV com todos os usuários que foram processados e mostra seus status de licença.</span><span class="sxs-lookup"><span data-stu-id="253a0-158">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="253a0-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="253a0-159">See also</span></span>

[<span data-ttu-id="253a0-160">Desabilitar o acesso aos serviços com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="253a0-160">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="253a0-161">Desabilitar o acesso aos Sway com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="253a0-161">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="253a0-162">Gerenciar contas de usuário e licenças usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="253a0-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="253a0-163">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="253a0-163">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

