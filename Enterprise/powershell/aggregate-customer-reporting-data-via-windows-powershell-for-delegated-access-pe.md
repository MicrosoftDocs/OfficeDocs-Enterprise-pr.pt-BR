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
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>Agregar dados de relatório do cliente por meio do Windows PowerShell para parceiros com permissão de acesso delegado (DAP)

 **Resumo:** use o Windows PowerShell para Office 365 para recuperar relatórios de todos os locatários do cliente e agregar os dados em um único local.
  
Por padrão, o Windows PowerShell para Office 365 não tem uma agregação interna de dados de relatório de várias locações do cliente. No entanto, você pode usar este script de exemplo do Windows PowerShell para Office 365 para repetir todas as locações do cliente, de modo a recuperar um único relatório para seus clientes individuais e, em seguida, agregar os dados de relatórios em um único local. Como resultado, você terá um único relatório para todos os locatários do cliente. 
  
Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas do Office 365 em suas ofertas de serviço aos seus clientes. Quando eles vendem uma assinatura do Office 365, recebem automaticamente permissões de Administrar Em Nome de (AOBO) para aslocações de cliente para que possam administrar e relatar todas as suas locações de cliente.
## <a name="before-you-begin"></a>Antes de começar

Para usar esse script, substitua seus valores específicos nas seguintes variáveis:
  
- **$UserName** - Este é o nome de usuário do administrador do seu parceiro. Essas credenciais serão usadas para se conectar a todas as locações do cliente.
    
- **$OutputFile** - Este é o arquivo de valores separados por vírgula aos quais os dados de relatórios serão agregados.
    
- **$ErrorFile** - Este é o arquivo de log de texto para obter detalhes dos erros.
    
- **$ScriptBlock** - Este script de exemplo usa **Get-MailboxActivityReport** e parâmetros (como as datas de início e término) para que você tenha uma forma de começar. Se desejar obter outros relatórios, substitua o nome do relatório desejado e os parâmetros necessários de **Get-MailboxActivityReport**.
    
- Abrir uma sessão do Windows PowerShell remota para Exchange Online usando as etapas em [Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>Usar o Windows PowerShell para agregar relatórios de locatários do cliente em um único local

1. Copie e cole este script no Bloco de Notas.
    
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

2. Salve o script como GetMailboxActivityReport.ps1 em um local fácil de localizar. Por exemplo, o arquivo foi salvo em C:\\O365 Scripts. 
    
3. Execute o script no Windows PowerShell remoto executando a seguinte sintaxe.
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

Este script de exemplo coloca o relatório agregado no arquivo ReportOutput.csv.
  
## <a name="see-also"></a>Veja também

#### 

[Ajuda para parceiros](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Serviço Web de Relatório do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlets de criação de relatórios no Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)

