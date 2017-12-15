---
title: "Agregar dados de relatório do cliente por meio do Windows PowerShell para parceiros com permissão de acesso delegado (DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "Resumo: Use o Windows PowerShell para Office 365 para recuperar relatórios de todas as locações do cliente e agregar os dados em um único local."
ms.openlocfilehash: 89651971424d1b9a494335572d2654d8402ec146
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="966ee-103">Agregar dados de relatório do cliente por meio do Windows PowerShell para parceiros com permissão de acesso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="966ee-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="966ee-104">**Resumo:** Use o Windows PowerShell para Office 365 para recuperar relatórios em todos os aluguéis são de cliente e agregar os dados em um único local.</span><span class="sxs-lookup"><span data-stu-id="966ee-104">**Summary:** Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="966ee-p101">Por padrão, o Windows PowerShell para Office 365 não tem uma agregação interna de dados de relatório de várias locações do cliente. No entanto, você pode usar este script de exemplo do Windows PowerShell para Office 365 para repetir todas as locações do cliente, de modo a recuperar um único relatório para seus clientes individuais e, em seguida, agregar os dados de relatórios em um único local. Como resultado, você terá um único relatório para todos os locatários do cliente.</span><span class="sxs-lookup"><span data-stu-id="966ee-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="966ee-p102">Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas do Office 365 em suas ofertas de serviço aos seus clientes. Quando eles vendem uma assinatura do Office 365, recebem automaticamente permissões de Administrar Em Nome de (AOBO) para aslocações de cliente para que possam administrar e relatar todas as suas locações de cliente.</span><span class="sxs-lookup"><span data-stu-id="966ee-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="966ee-112">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="966ee-112">Before you begin</span></span>

<span data-ttu-id="966ee-113">Para usar esse script, substitua seus valores específicos nas seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="966ee-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="966ee-p103">**$UserName** - Este é o nome de usuário do administrador do seu parceiro. Essas credenciais serão usadas para se conectar a todas as locações do cliente.</span><span class="sxs-lookup"><span data-stu-id="966ee-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="966ee-116">**$OutputFile** - Este é o arquivo de valores separados por vírgula aos quais os dados de relatórios serão agregados.</span><span class="sxs-lookup"><span data-stu-id="966ee-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="966ee-117">**$ErrorFile** - Este é o arquivo de log de texto para obter detalhes dos erros.</span><span class="sxs-lookup"><span data-stu-id="966ee-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="966ee-p104">**$ScriptBlock** - Este script de exemplo usa **Get-MailboxActivityReport** e parâmetros (como as datas de início e término) para que você tenha uma forma de começar. Se desejar obter outros relatórios, substitua o nome do relatório desejado e os parâmetros necessários de **Get-MailboxActivityReport**.</span><span class="sxs-lookup"><span data-stu-id="966ee-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="966ee-120">Abrir uma sessão do Windows PowerShell remota para Exchange Online usando as etapas em [Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="966ee-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="966ee-121">Usar o Windows PowerShell para agregar relatórios de locatários do cliente em um único local</span><span class="sxs-lookup"><span data-stu-id="966ee-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="966ee-122">Copie e cole este script no Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="966ee-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. <span data-ttu-id="966ee-p105">Salve o script como GetMailboxActivityReport.ps1 em um local fácil de localizar. Por exemplo, o arquivo foi salvo em C:\\O365 Scripts.</span><span class="sxs-lookup"><span data-stu-id="966ee-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="966ee-125">Execute o script no Windows PowerShell remoto executando a seguinte sintaxe.</span><span class="sxs-lookup"><span data-stu-id="966ee-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="966ee-126">Este script de exemplo coloca o relatório agregado no arquivo ReportOutput.csv.</span><span class="sxs-lookup"><span data-stu-id="966ee-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="966ee-127">See also</span><span class="sxs-lookup"><span data-stu-id="966ee-127">See also</span></span>

#### 

[<span data-ttu-id="966ee-128">Ajuda para parceiros</span><span class="sxs-lookup"><span data-stu-id="966ee-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="966ee-129">Serviço Web de Relatório do Office 365</span><span class="sxs-lookup"><span data-stu-id="966ee-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="966ee-130">Cmdlets de criação de relatórios no Exchange Online</span><span class="sxs-lookup"><span data-stu-id="966ee-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

