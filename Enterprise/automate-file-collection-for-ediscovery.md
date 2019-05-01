---
title: Automatizar a coleta de arquivos para descoberta eletrônica
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Resumo: saiba como automatizar a coleta de arquivos dos computadores dos usuários para descoberta eletrônica.'
ms.openlocfilehash: bfbe3b9218ed81727f2cc6ad9fabcb02e76d486b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490759"
---
# <a name="automate-file-collection-for-ediscovery"></a>Automatizar a coleta de arquivos para descoberta eletrônica

 **Resumo:** Saiba como automatizar a coleta de arquivos dos computadores dos usuários para descoberta eletrônica.
  
Todas as empresas enfrentam o potencial de processos judiciais ou outros tipos de ações legais. Embora os departamentos jurídicos trabalhem para reduzir essa exposição, o litígio é um fato da vida útil da empresa. Quando uma empresa enfrenta ações legais, elas são necessárias, por meio do processo de descoberta legal, para fornecer todo o material documentário relevante para o tribunal e para o advogado oposto. 
  
a descoberta eletrônica é o processo pelo qual as empresas fazem inventário, pesquisa, identificar, preservar, filtrar e disponibilizar os materiais documentários relevantes que existem em formato eletrônico. O SharePoint 2013, o Exchange Server 2013, o Lync Server 2013, o SharePoint Online e o Exchange Online podem armazenar grandes quantidades de conteúdo documentário. Dependendo da versão, esses produtos podem oferecer suporte a descoberta eletrônica e bloqueios no local (Lync através do Exchange Server), tornando mais fácil para as equipes legais indexar, identificar, reter e filtrar o conteúdo mais relevante para um determinado caso.
  
Muitos documentos são armazenados nos computadores locais dos usuários (responsáveis), e não em um local centralizado. Isso torna praticamente impossível que o SharePoint 2013 pesquise e, se não puder ser pesquisado, não possa ser incluído no eDiscovery. Esta solução mostra como usar scripts de logon, System Center Orchestrator 2012 R2 e Windows PowerShell para Exchange Server para automatizar a identificação e coleção de materiais documentários de computadores dos usuários.
  
## <a name="what-this-solution-does"></a>O que esta solução faz

Esta solução usa um grupo de segurança global, uma diretiva de grupo e um script do Windows PowerShell para localizar, inventariar e coletar conteúdo e arquivos de repositório pessoal do Outlook de computadores locais de usuários para um compartilhamento de arquivo oculto. A partir daí, os arquivos PST podem ser importados para o Exchange Server 2013 ou o Exchange Online. Todos os arquivos são movidos usando um runbook do System Center Orchestrator 2012 R2 para outro compartilhamento de arquivos no Microsoft Azure para armazenamento de longo prazo e indexação pelo SharePoint 2013. Em seguida, você usa centros de descoberta eletrônica em sua implantação local do SharePoint 2013 ou no SharePoint Online, como faria regularmente para executar a descoberta eletrônica. 
  
> [!IMPORTANT]
> Esta solução usa o Robocopy para copiar arquivos dos computadores dos responsáveis para um compartilhamento de arquivos centralizado. Como o Robocopy não copia arquivos que estão abertos ou bloqueados, qualquer arquivo, incluindo arquivos PST, que os responsáveis por abrir não serão coletados. Você terá que coletar manualmente. Esta solução fornece uma lista que identifica explicitamente os arquivos que não podem ser copiados e o caminho completo para cada arquivo. 
  
O diagrama a seguir orienta você por todas as etapas e elementos da solução.
  
![Visão geral da solução de conjunto de arquivos automatizado](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|Legenda * * * *||
|:-----|:-----|
|![texto explicativo magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|Crie um objeto de política de grupo (GPO) e associe-o ao script de logon da coleção.  <br/> |
|![balão magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| Configure o filtro de segurança do GPO para aplicar o GPO somente ao grupo responsáveis. <br/> |
|![texto explicativo 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Os responsáveis fizer o logon e o GPO ser executado, chamando o script de logon da coleção.  <br/> |
|![texto explicativo magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|O script de logon da coleção faz o inventário de todas as unidades conectadas localmente no computador responsáveis, pesquisando os arquivos que você deseja e gravando sua localização.  <br/> |
|![balão magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|O script de logon da coleção copia os arquivos inventariados para um compartilhamento de arquivo oculto no servidor de teste.  <br/> |
|![chamada magenta 6](media/99589726-0c7e-406b-a276-44301a135768.png)| (Opção A) Execute manualmente o script de importação PST para importar os arquivos PST coletados para o Exchange Server 2013. <br/> |
|![texto explicativo de magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Opção B) Usando a ferramenta e o processo de importação do Office 365, importe os arquivos PST coletados para o Exchange Online.  <br/> |
|![balão de magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Mova todos os arquivos coletados para um compartilhamento de arquivos do Azure para armazenamento de longo prazo com o runbook do MoveToColdStorage System Center Orchestrator 2012 R2. <br/> |
|![texto explicativo magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Indexe os arquivos no compartilhamento de arquivos de armazenamento Cold com o SharePoint 2013.  <br/> |
|![texto explicativo Magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Realize o conteúdo de descoberta eletrônica no armazenamento Cold e no Exchange Server 2013 local.  <br/> |
|![texto explicativo 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Realize o conteúdo de descoberta eletrônica no Office 365.  <br/> |
   
## <a name="prerequisites"></a>Pré-requisitos

A configuração dessa solução requer muitos elementos, a maioria dos quais você provavelmente já fez e configurou se você está pensando no eDiscovery. Para os elementos que você não pode ter ou que exijam uma configuração específica, forneceremos os links necessários para desenvolver sua configuração básica. Você deve ter a configuração básica in-loco antes de configurar a própria solução.
  
### <a name="base-configuration"></a>Configuração base

|**Elemento**|**Link**|
|:-----|:-----|
|Domínio dos serviços de domínio do Active Directory (AD DS)  <br/> ||
|Conectividade com a Internet da sua rede local  <br/> ||
|SQL Server 2012 para oferecer suporte ao SharePoint 2013 e ao System Center Orchestrator 2012 R2  <br/> |[ImPlantando o System Center Orchestrator-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| SharePoint 2013 local ou baseado no Azure para descoberta eletrônica (necessário para A opção A) <br/> ||
|Servidor de compartilhamento de arquivos no local para preparação  <br/> ||
|Exchange Server 2013 local para A opção uma importação de PST  <br/> |CU5 (15.913.22) está disponível em [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[ImPlantando o System Center Orchestrator-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Office 365 (E3 Plan) com Exchange Online e SharePoint Online (necessário para a opção B)  <br/> |Para se inscrever em uma assinatura do Office 365 E3, confira [assinatura do office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).  <br/> |
|Assinatura do Azure com uma máquina virtual  <br/> |Para se inscrever no Azure, confira [inscrever-se no Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|Uma conexão VPN entre a rede local e sua assinatura do Azure  <br/> |Para configurar um túnel VPN entre sua assinatura do Azure e sua rede local, consulte [conectar uma rede local a uma rede virtual do Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|Descoberta eletrônica do SharePoint 2013 configurada para pesquisar no SharePoint e no Exchange Server 2013 e, opcionalmente, Lync Server 2013  <br/> |Para configurar a descoberta eletrônica dessa maneira, confira [Configurar a descoberta eletrônica no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) e[testar o guia de laboratório: configurar a descoberta eletrônica para um laboratório de teste de compartilhamentos de arquivos do Exchange, Lync, SharePoint e Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).  <br/> |
|Descoberta eletrônica no Office 365 para SharePoint Online e Exchange Online  <br/> |Para configurar a descoberta eletrônica no Office 365, consulte [configurar um centro de descoberta eletrônica no SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).  <br/> |
   
## <a name="configure-the-environment"></a>Configurar o ambiente

Agora que você tem a configuração base in-loco, você pode prosseguir para configurar a própria solução. 
  
### <a name="staging-file-share"></a>Compartilhamento de arquivo de preparação

1. No domínio local, crie um grupo de segurança global chamado responsáveis.
    
2. Criar um compartilhamento de arquivo oculto para os arquivos coletados de computadores. Ele deve estar em um servidor local. Por exemplo, em um servidor chamado preparação, crie um compartilhamento de arquivos chamado casos $. O **$** é necessário para tornar este um compartilhamento oculto.
    
3. Defina as seguintes permissões de compartilhamento:
    
  - Responsáveis: alterar, ler
    
  - Administradores: Controle Total
    
  - Subsistema confiável do Exchange: alterar, ler
    
4. Abra a guia **segurança** , adicione o grupo responsáveis e clique em **avançado**. Defina as seguintes permissões para o grupo responsáveis:
    
  - **Tipo: negar**
    
  - **Aplica-se a: esta pasta, subpastas e arquivos**
    
5. Clique em **permissões avançadas** e selecione o seguinte:
    
  - **Atributos de leitura**
    
  - **Ler atributos estendidos**
    
  - **Permissões de leitura**
    
6. Teste o acesso ao compartilhamento de arquivos de casos $, fazendo o seguinte:
    
1. Adicionar um usuário ao grupo responsáveis.
    
2. Coloque um arquivo na pasta casos $.
    
3. Como usuário, navegue até o servidor de teste, por exemplo, navegue até o \\ \\compartilhamento de preparo para ver quais compartilhamentos estão disponíveis. Você não verá os **casos $** share listados.
    
4. Digite manualmente o caminho completo para os casos $ share no Explorer. Isso deve abrir os casos $ share.
    
5. Tente abrir o arquivo que você colocou anteriormente no compartilhamento. Isso deve falhar.
    
### <a name="logon-script"></a>Script de logon

1. Copie e cole este script do Windows PowerShell no bloco de notas:
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. Salve o script acima como CollectionScript. ps1 em um local que seja fácil de localizar, por exemplo, C:\\AFCScripts.
    
3. Use o recurso ir para no bloco de notas. Faça as seguintes alterações, conforme necessário:
    
|**Número da linha**|**O que você precisa alterar**|**Obrigatório/opcional**|
|:-----|:-----|:-----|
|71  <br/> |**$Filetypes** variável. Inclua todas as extensões de tipo de arquivo que você deseja que o script faça inventário e colete na variável de matriz. <br/> |Opcional  <br/> |
|76 e 77  <br/> |Alterar a maneira como a variável de **$CaseNo** é criada para atender às suas necessidades. O script captura a data atual e a hora e acrescenta o nome de usuário a ela. <br/> |Opcional  <br/> |
|80  <br/> |**$CaseRootLocation** variável precisa ser definida para o compartilhamento de arquivos do conjunto de servidores de preparo, por exemplo ** \\ \\, exemplos de preparação\\$**. <br/> |Obrigatório  <br/> |
   
4. Coloque o arquivo CollectionScript. ps1 no compartilhamento de arquivos Netlogon em um controlador de domínio. 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>Configurar o GPO para o script de logon e o grupo de responsáveis

1. Configure um script de logon para o grupo responsáveis seguindo a seção "como atribuir scripts de logon do usuário" no tópico, [usando scripts de inicialização, desligamento, logon e logoff na política de grupo](https://go.microsoft.com/fwlink/p/?LinkId=614844).
    
2. Remova os usuários autenticados da **filtragem de segurança**e adicione o grupo responsáveis.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>Opção de importação de PST A, script para O Exchange Server 2013

1.  Copie e cole o seguinte script do Windows PowerShell no bloco de notas:
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. Salve o script como PSTImportScript. ps1 em um local que seja fácil de encontrar. Por exemplo e facilidade de uso, crie uma pasta no seu servidor de teste, \\ \\chamada preparação\\de AFCScripts, e salve-a.
    
3. Use o recurso ir para no bloco de notas e faça as seguintes alterações, conforme necessário:
    
|**Número da linha**|**O que você precisa alterar**|**Obrigatório/opcional**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** marca as pastas de caixa de correio nas quais os PSTs são importados. Altere isso se necessário. <br/> |Opcional  <br/> |
|17   <br/> |**$ConnectionURI** precisa ser definido para seu próprio servidor. <br/> > [!IMPORTANT]> Verifique se o **$ConnectionURI** aponta para um local http, não para https. Ele não funcionará com https:.          |Obrigatório  <br/> |
   
4. Verifique se a conta de subsistema confiável do Exchange tem permissões de leitura, gravação e execução \\ \\para o\\compartilhamento de casos de preparação $.
    
5. O script de importação de PST requer os dois parâmetros de entrada a seguir:
    
  - **$SourcePath** O local dos arquivos PST a serem importados, por \\ \\exemplo,\\exemplos de preparação $.
    
  - **$MailboxAlias** O alias da caixa de correio de destino que receberá os itens de email importados.
    
6. Por exemplo, se você deseja importar todos os arquivos PST do caminho \\Staging\Cases $ para uma caixa de correio com o alias eDiscoveryMailbox, você deve executar o script como este `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opção de importação de PST B, para o Exchange Online

-  Crie a estrutura da caixa de correio para colocar os arquivos PST importados no. Para saber mais sobre como criar uma caixa de correio de usuário no Exchange Online, confira[criar caixas de correio de usuário no Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Armazenamento Cold

1. Crie um compartilhamento de arquivos na máquina virtual do Azure, onde todos os arquivos coletados serão colocados, por exemplo \\ \\,\\AZFile1 ContentColdStorage.
    
2. Conceda à conta de acesso ao conteúdo padrão pelo menos permissões de leitura para o compartilhamento e todas as subpastas e arquivos. Para obter mais informações sobre como configurar a pesquisa do SharePoint 2013, consulte [Create and configure a Search Service Application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. Se você previr a importação de arquivos \\ \\PST\\do AZFile1 ContentColdStorage, conceda permissões de leitura, gravação e execução do subsistema confiável do Exchange para o compartilhamento.
    
### <a name="orchestrator"></a>Orquestrador

1. Baixe o[ runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) do centro de download da Microsoft.
    
2. Abra o **runbook designer**, no painel **conexões** , clique na pasta para a qual você deseja importar o runbook. Clique no menu **ações** e clique em **importar**. A caixa de diálogo **importar** é exibida.
    
3. Na caixa **local do arquivo** , digite o caminho e o nome de arquivo do runbook que você deseja importar ou clique nas reticências ( **...**) para navegar até o arquivo que você deseja importar. 
    
4. Selecione **importar runbooks** e **importar dados criptografados**do Orchestrator. Limpe **contadores**, **agendas**, **variáveis**, **grupos de computadores**, **importe configurações globais**e **substitua as configurações globais existentes**.
    
5. Clique em **Concluir**.
    
6. Edite o runbook **MoveFilesToColdStorage** da seguinte maneira:
    
1. **Mover arquivo** atividade-define o caminho do **arquivo de origem** para o compartilhamento de arquivo de \\ \\conjunto,\\por exemplo, exemplos de preparação $. Defina a **pasta de destino** para o compartilhamento de arquivo de armazenamento Cold no Azure \\ \\,\\por exemplo, AZFile1 ContentColdStorage. Selecione **criar um arquivo com um nome exclusivo**.
    
2. **Excluir** atividade da pasta-defina **o caminho:** para o compartilhamento de arquivo da coleção \\ \\, por\\exemplo,\\casos de preparação $ *, e selecione **excluir todos os arquivos e**subpastas. 
    
7. Implante o runbook **MoveToColdStorage** usando os procedimentos de[implantação de Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Pesquisa do SharePoint no local para armazenamento Cold

1. crie uma nova fonte de conteúdo no seu farm do SharePoint 2013 para o compartilhamento de armazenamento cold no Azure \\ \\,\\por exemplo, AZFile1 ContentColdStorage. Para obter mais informações sobre como gerenciar fontes de conteúdo, consulte [Adicionar, editar ou excluir uma fonte de conteúdo no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. Inicie um rastreamento completo. Para obter mais informações, consulte, [Iniciar, pausar, continuar ou parar um rastreamento no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Usando a solução

Há cinco etapas principais para usar essa solução, supondo que você não queira importar os arquivos PST para o Exchange Server 2013 e o Exchange Online. Esta seção fornece os procedimentos para todos eles. Sua interação principal com a solução será fazer o seguinte:
  
1. Gerenciar a associação do usuário no grupo responsáveis.
    
2. Revise os arquivos de log gerados pelo script de logon. O FileCopyErrors. log lista todos os arquivos que não foram copiados com êxito. Você precisa decidir o que deseja fazer com eles
    
3. Gerenciar o processo de importação de PST.
    
4. Mover os arquivos da coleção para o armazenamento Cold.
    
Todas as outras etapas não são específicas desta solução. São tarefas administrativas padrão realizadas no SharePoint 2013 e no Office 365 e no Azure. Há itens que esta solução não fornece orientações que você precisará para trabalhar com base nas necessidades da sua empresa, como:
  
1. Controle de casos de descoberta eletrônica e quais responsáveis estão associados a esse caso.
    
2. Controlar quais conjuntos de coleções de arquivos são associados ao caso de descoberta eletrônica.
    
3. Coordenar o tempo das etapas de importação e migração para o armazenamento Cold.
    
4. Gerenciar o espaço de arquivo usado no Azure.
    
5. Gerenciar as caixas de correio nas quais os PSTs são importados.
    
6. Backup e restauração de todos os dados locais.
    
### <a name="custodian-management"></a>Gerenciamento de responsáveis

- Para iniciar o processo de coleta automatizada de arquivos para um usuário individual, adicione-os ao grupo responsáveis. Na próxima vez que o usuário fizer logon, o script de logon atribuído ao grupo responsáveis por meio da política de grupo será executado. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Monitorar arquivos coletados e examinar arquivos de log

1. Assista ao compartilhamento de arquivo de coleção, \\ \\por exemplo\\, casos\\de preparação $ *, para a pasta de coleção do usuário. O nome da pasta será formatado da seguinte maneira: *yyyyMMddHHmm_UserName* .
    
2. Quando a coleção estiver concluída, abra a pasta de coleção e navegue até a pasta _Log Na pasta _Log, você verá o seguinte:
    
  - Um arquivo XML para cada unidade local no computador do usuário, por exemplo, **um. xml**, **C. xml**. Esses arquivos contêm as unidades de estoque que são nomeadas após e são usadas para a operação do Robocopy.
    
    > [!NOTE]
    > O script de coleção só criará uma entrada no arquivo de inventário para os tipos de arquivo que você definiu no próprio script. Ele não criará uma entrada de inventário para cada arquivo no computador do usuário. 
  
  - Um arquivo de log chamado FileCopyErrors. log para cada execução de coleção. Este arquivo contém uma lista dos arquivos que o Robocopy não pôde copiar para o compartilhamento de coleção de arquivos, por \\ \\exemplo,\\casos de\\preparação $ *. Você precisará revisar esta ação e decidir quais ações tomar para esses arquivos perdidos. Normalmente, você precisará coletar manualmente, se quiser, ou pode decidir que elas não são necessárias e, portanto, podem ser omitidas da coleção.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Opção de importação de PST A para O Exchange Server 2013

1. Faça logon no servidor que hospeda o compartilhamento de arquivo de conjunto, por exemplo, **preparação**e abra o Windows PowerShell. Para obter mais informações sobre como iniciar o Windows PowerShell, consulte[iniciando o Windows PowerShell no Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Defina a política de execução como irrestrita. Digite `Set-ExecutionPolicy Unrestricted -Scope Process` no Windows PowerShell e pressione Enter.
    
3. Execute o arquivo PSTImportScript. ps1 e forneça os parâmetros **$SourcePath** e **$MailboxAlias** . Para obter mais informações sobre a execução de scripts do Windows PowerShell, consulte[running scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Revise a saída para ver se há erros.
    
5. Antes de tentar importar um arquivo PST com nome idêntico para a mesma caixa de correio, você precisa remover a solicitação de importação de caixa de correio. Execute o seguinte comando para fazer isso: `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Você será solicitado a remover cada solicitação individual da fila. Responder conforme necessário.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opção de importação de PST B, para o Exchange Online

- Para colocar os arquivos PST coletados no Exchange Online, siga os procedimentos na seção importar arquivos para o Office 365 através da seção carregamento de rede do [serviço de importação do office 365](https://go.microsoft.com/fwlink/p/?LinkId=614938).
    
### <a name="move-to-cold-storage"></a>Mover para o armazenamento Cold

1. Execute o runbook **MoveToColdStorage** usando os procedimentos em[executando Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).
    
2. Assista ao compartilhamento de arquivos do Azure que você está usando para armazenamento de longo \\ \\prazo\\, por exemplo, AZFile1 ContentColdStorage e o compartilhamento de arquivo da \\ \\coleção local\\, por exemplo, exemplos de preparação $. Você deve ver os arquivos e pastas que aparecem no compartilhamento de arquivos de armazenamento Cold e desaparecem do conjunto de arquivos de coleção.
    
### <a name="ediscovery"></a>Descoberta eletrônica

1. Permitir que o rastreamento completo do compartilhamento de arquivos de armazenamento Cold seja executado como agendamentos ou iniciar um rastreamento. Para obter mais informações sobre como iniciar rastreamentos completos ou incrementais, consulte [Iniciar, pausar, continuar ou parar um rastreamento no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Criar um caso de descoberta eletrônica no SharePoint 2013 se você usou A opção A para um arquivo PST, importe ou crie um caso de descoberta eletrônica no SharePoint Online se você usou a opção B.
    

