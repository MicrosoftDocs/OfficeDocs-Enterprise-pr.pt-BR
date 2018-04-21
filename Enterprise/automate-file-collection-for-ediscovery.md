---
title: Automatizar o conjunto de arquivos para eDiscovery
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
description: 'Resumo: Saiba como automatizar o conjunto de arquivos dos computadores do usuário para a descoberta eletrônica.'
ms.openlocfilehash: 0a09eb8ec997f62e0f8c3149d35422b0ee0e4a98
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="automate-file-collection-for-ediscovery"></a>Automatizar o conjunto de arquivos para eDiscovery

 **Resumo:** Saiba como automatizar o conjunto de arquivos dos computadores do usuário para a descoberta eletrônica.
  
Todas as empresas enfrentam o potencial de ações legais ou outros tipos de ações legais. Enquanto departamentos legais trabalham para reduzir a essa exposição, litígio é um fato da vida útil de negócios. Quando uma empresa faces ação judicial, eles são necessários, pelo processo de descoberta legal, para fornecer a todos os materiais de documentos relevantes para o tribunal e advogado oposto. 
  
descoberta eletrônica é o processo pelo qual as empresas de estoque, pesquisa, identificam, preservar, filtrar e disponibilizar os materiais de documentos relevantes que existem em formulário eletrônico. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online e Exchange Online podem armazenar grandes quantidades de conteúdo de documentos. Dependendo da versão, esses produtos podem suportar a descoberta eletrônica e in-loco retém (Lync através do servidor do Exchange), tornando mais fácil para que as equipes legais indexar, identificam, mantenha e filtrar o conteúdo mais relevante para uma determinada ocorrência.
  
Muitos documentos são armazenados em dos usuários (responsáveis) computadores locais, não em um local centralizado. Isso torna impossível essencialmente para o SharePoint 2013 pesquisar e se ele não pode ser pesquisado, ele não pode ser incluído no eDiscovery. Essa solução mostra como usar scripts de logon, o System Center Orchestrator 2012 R2 e o Windows PowerShell para o Exchange Server para automatizar a identificação e o conjunto de documentos materiais dos computadores dos usuários.
  
## <a name="what-this-solution-does"></a>Esta solução não

Esta solução usa um grupo de segurança global, diretiva de grupo e um script do Windows PowerShell para localizar, de estoque e coletar conteúdo e os arquivos de armazenamento pessoal (. PST) do Outlook dos computadores de usuários locais para um compartilhamento de arquivo oculto. A partir daí, os arquivos PST podem ser importados para o Exchange Server 2013 ou Exchange Online. Todos os arquivos são movidos usando um runbook do System Center Orchestrator 2012 R2 para outro compartilhamento de arquivo no Microsoft Azure para armazenamento de longo prazo e indexação pelo SharePoint 2013. Você então usar centros de eDiscovery em sua implantação do SharePoint 2013 no local ou no SharePoint Online como faria regularmente para executar a descoberta eletrônica. 
  
> [!IMPORTANT]
> Esta solução usa o robocopy para copiar os arquivos dos computadores dos responsáveis para um compartilhamento de arquivo centralizado. Porque o robocopy não copia os arquivos que são aberto ou bloqueado, quaisquer arquivos, incluindo arquivos PST, que dos responsáveis abriu não será coletado. Você precisará coletá-los manualmente. Essa solução fornecem uma lista que identifica explicitamente os arquivos que ele não é possível copiar e o caminho completo para cada arquivo. 
  
O diagrama a seguir percorre todas as etapas e os elementos da solução.
  
![Visão geral da solução de coleção de arquivos automatizada](images/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|Legenda * * *||
|:-----|:-----|
|![balão magenta 1](images/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|Criar um objeto de diretiva de grupo (GPO) e associá-lo com o script de logon da coleção.  <br/> |
|![balão magenta 2](images/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| Configure o filtro de segurança do GPO para aplicar o GPO somente ao grupo responsáveis. <br/> |
|![balão magenta 3](images/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Dos responsáveis faz logon e executa o GPO, chamar o script de logon da coleção.  <br/> |
|![balão magenta 4](images/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|O script de logon da coleção faz o inventário todas as unidades conectadas localmente no computador responsáveis, pesquisar os arquivos que deseja e seu local de gravação.  <br/> |
|![balão magenta 5](images/4bf8898c-44ad-4524-b983-70175804eb85.png)|O script de logon da coleção copia os arquivos inventariados para um compartilhamento de arquivo oculto no servidor intermediário.  <br/> |
|![balão magenta 6](images/99589726-0c7e-406b-a276-44301a135768.png)| (Uma opção) Manualmente, execute o script de importação de PST para importar os arquivos PST coletados para Exchange Server 2013. <br/> |
|![balão magenta 7](images/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Opção B) Usando a ferramenta de importação do Office 365 e o processo, importe os arquivos PST coletados para Exchange Online.  <br/> |
|![balão magenta 8](images/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Mova coletados todos os arquivos para um compartilhamento de arquivo Azure para armazenamento de longo prazo com o runbook MoveToColdStorage System Center Orchestrator 2012 R2. <br/> |
|![balão magenta 9](images/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Indexe os arquivos em compartilhamento de arquivos o armazenamento frio com o SharePoint 2013.  <br/> |
|![balão magenta 10](images/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Execute a descoberta eletrônica no conteúdo em armazenamento de frio e do local Exchange Server 2013.  <br/> |
|![balão magenta 11](images/e59ab403-2f19-497a-92a5-549846dded66.png)|Execute a descoberta eletrônica no conteúdo no Office 365.  <br/> |
   
## <a name="prerequisites"></a>Pré-requisitos

A configuração dessa solução requer muitos elementos, mais dos quais você provavelmente in-loco e configurou se você estiver pensando sobre a descoberta eletrônica. Para os elementos que você pode não ter ou aquelas que exigem uma configuração específica, forneceremos você com os links que você precisa criar sua configuração de base. Você deve ter a configuração básica in-loco antes de configurar a solução em si.
  
### <a name="base-configuration"></a>Configuração base

|**Elemento**|**Link**|
|:-----|:-----|
|Domínio do Active Directory Domain Services (AD DS)  <br/> ||
|Conectividade de Internet da sua rede local  <br/> ||
|SQL Server 2012 para dar suporte ao SharePoint 2013 e o System Center Orchestrator 2012 R2  <br/> |[Implantando o System Center Orchestrator - 2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| Local ou Azure com base em SharePoint 2013 para descoberta eletrônica (necessária para a opção uma) <br/> ||
|Servidor de compartilhamento de arquivos local para preparação  <br/> ||
|Local do Exchange Server 2013 para importação de PST de uma opção  <br/> |CU5 (15.913.22) está disponível em [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[Implantando o System Center Orchestrator - 2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Office 365 (plano E3) com o Exchange Online e SharePoint Online (necessário para a opção B)  <br/> |Para se inscrever para uma assinatura do Office 365 E3, consulte [assinatura do Office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).  <br/> |
|Assinatura do Windows Azure com uma máquina virtual  <br/> |Para se inscrever para um Azure, consulte [inscrever-se no Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|Uma conexão VPN entre sua rede local e a sua assinatura do Windows Azure  <br/> |Para configurar um túnel VPN entre sua assinatura do Windows Azure e sua rede local, consulte [Connect uma local da rede para uma rede virtual do Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|EDiscovery do SharePoint 2013 configurado para pesquisar por meio do SharePoint e Exchange Server 2013 e, opcionalmente, Lync Server 2013  <br/> |Para configurar o eDiscovery dessa maneira, consulte [Configurar o eDiscovery no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) e[Test Lab Guide: configurar a descoberta eletrônica para um Exchange, Lync, SharePoint e do laboratório de teste de compartilhamentos de arquivo Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).  <br/> |
|descoberta eletrônica no Office 365 para o SharePoint Online e o Exchange Online  <br/> |Para configurar o eDiscovery no Office 365, consulte [Configurar uma central de descoberta eletrônica no SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).  <br/> |
   
## <a name="configure-the-environment"></a>Configurar o ambiente

Agora que você tem a configuração básica in-loco, você pode mover com antecedência para configurar a solução em si. 
  
### <a name="staging-file-share"></a>Compartilhamento de arquivo do teste

1. No domínio local, crie um grupo de segurança global chamado responsáveis.
    
2. Crie um compartilhamento de arquivo oculto para os arquivos que são coletadas de computadores responsáveis. Este deve ser em um servidor local. Por exemplo, em um servidor chamado preparo, crie um compartilhamento de arquivo chamado $ casos. O **$** é necessário para fazer isso em um compartilhamento oculto.
    
3. Defina as permissões de compartilhamento a seguir:
    
  - Responsáveis: Alteração e leitura
    
  - Administradores: Controle Total
    
  - Subsistema confiável do Exchange: Leitura, alteração
    
4. Abra a guia **segurança** , adicione o grupo responsáveis e clique em **Avançado**. Defina as seguintes permissões para o grupo responsáveis:
    
  - **Tipo: Negar**
    
  - **Aplica-se a: esta pasta, subpastas e arquivos**
    
5. Clique em **Permissões avançadas** e selecione o seguinte:
    
  - **Atributos de leitura**
    
  - **Ler atributos estendidos**
    
  - **Permissões de leitura**
    
6. Teste o acesso ao compartilhamento de arquivos de $ casos fazendo o seguinte:
    
1. Adicione um usuário ao grupo responsáveis.
    
2. Coloca um arquivo na pasta de $ casos.
    
3. Como o usuário, vá para o servidor de teste, por exemplo, navegue até o \\ \\preparo compartilhar para ver quais compartilhamentos estão disponíveis. Você não deve ver o compartilhamento de **casos$** listado.
    
4. Manualmente, digite o caminho completo para o compartilhamento de $ casos no Explorer. Isso deve abrir o compartilhamento de $ casos.
    
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

2. Salve o script acima como CollectionScript.ps1 em um local fácil de encontrar, por exemplo, c:\\AFCScripts.
    
3. Use o recurso ir para no bloco de notas. Faça as seguintes alterações, conforme necessário:
    
|**N º de linha**|**Você precisa alterar**|**Obrigatório/opcional**|
|:-----|:-----|:-----|
|71  <br/> |Variável de **$FileTypes** . Inclua todas as extensões de tipo de arquivo que você deseja que o script de estoque e coletar na variável de matriz.<br/> |Opcional  <br/> |
|76 e 77  <br/> |Alterar a maneira como a variável **$CaseNo** é criado para atender às suas necessidades. O script captura a data atual e a hora e o acrescenta o nome de usuário a ela.<br/> |Opcional  <br/> |
|80  <br/> |Compartilha **$CaseRootLocation** variável precisa ser definida como seu arquivo preparo de conjunto de servidores, por exemplo ** \\ \\preparo\\casos$**. <br/> |Obrigatório  <br/> |
   
4. Coloque o arquivo de CollectionScript.ps1 no compartilhamento de arquivo de logon de rede em um controlador de domínio. 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>Configurar o GPO para o script de logon e o grupo de responsáveis

1. Configure um script de logon para o grupo responsáveis seguindo a seção "Como atribuir scripts de logon do usuário" no tópico, [usando inicialização, desligamento, Logon e os Scripts de Logoff na diretiva de grupo](https://go.microsoft.com/fwlink/p/?LinkId=614844).
    
2. Remover usuários autenticados do **Filtro de segurança**e adicione o grupo responsáveis.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>PST importar opção A, o script do Exchange Server 2013

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

2. Salve o script como PSTImportScript.ps1 em um local fácil de encontrar. Por exemplo e facilidade de uso, crie uma pasta no seu servidor intermediário chamado \\ \\preparo\\AFCScripts e salvá-lo nesse local.
    
3. Use o recurso ir para no bloco de notas e faça as seguintes alterações, conforme necessário:
    
|**N º de linha**|**Você precisa alterar**|**Obrigatório/opcional**|
|:-----|:-----|:-----|
|12  <br/> |As pastas de caixa de correio que PSTs são importados para marcas de **$FolderIdentifier** . Altere essa opção se necessário.<br/> |Opcional  <br/> |
|17  <br/> |**$ConnectionUri** deve ser definida para seu próprio servidor. <br/> > [!IMPORTANT]> Verifique se sua **$ConnectionUri** aponta para um local de http, https não. Ele não funcionará com https:.          |Obrigatório  <br/> |
   
4. Verifique se a conta de subsistema confiável do Exchange tem permissões de leitura, gravação e execução para o \\ \\preparo\\compartilhamento de $ casos.
    
5. O script de importação de PST requer os dois parâmetros de entrada a seguintes:
    
  - **$SourcePath** O local dos arquivos PST a ser importado, por exemplo \\ \\preparo\\casos$.
    
  - **$MailboxAlias** O alias da caixa de correio de destino que receberá os itens de e-mail importadas.
    
6. Por exemplo, se você deseja importar todos os arquivos PST do caminho da \\Staging\Cases$ em uma caixa de correio com o eDiscoveryMailbox alias, você pode executar o script semelhante a esta `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opção de importação de PST B, para o Exchange Online

-  Crie a estrutura da caixa de correio para colocar os arquivos PST importados em. Para obter mais informações sobre como criar uma caixa de correio do usuário no Exchange Online, consulte[Criar caixas de correio de usuário no Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Armazenamento frio

1. Criar um compartilhamento de arquivo no Windows Azure Máquina Virtual, onde todos os arquivos coletados serão colocados, por exemplo, \\ \\AZFile1\\ContentColdStorage.
    
2. Conceder a conta de acesso a conteúdo padrão pelo menos permissões de leitura para o compartilhamento e todas as subpastas e arquivos. Para obter mais informações sobre como configurar a pesquisa do SharePoint 2013, consulte [criar e configurar um aplicativo de serviço de pesquisa no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. Se você prevê a importação de arquivos PST do \\ \\AZFile1\\ContentColdStorage, conceder leia subsistema confiável do Exchange, gravação e execução de permissões para o compartilhamento.
    
### <a name="orchestrator"></a>Orchestrator

1. Baixe o[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) do Microsoft Download Center.
    
2. Abrir o **Runbook Designer**, no painel **conexões** , clique na pasta que você deseja importar o runbook em. Clique no menu **ações** e clique em **Importar**. Será exibida a caixa de diálogo de **importação** .
    
3. Na caixa **Local do arquivo** , digite o nome de arquivo e caminho do runbook que você deseja importar ou clique nas reticências ( **…**) para navegar até o arquivo que você deseja importar. 
    
4. Selecione **Importar runbooks** e **Orchestrator importar os dados criptografados**. Desmarque **contadores**, **agendas**, **variáveis**, **Grupos de computadores**, **configurações globais de importação**e **Substituir as configurações globais existentes**.
    
5. Clique em **Concluir**.
    
6. Edite o runbook **MoveFilesToColdStorage** da seguinte maneira:
    
1. Atividade de **Mover arquivos** - definir o caminho do **Arquivo de origem** para o compartilhamento de arquivos da coleção, por exemplo \\ \\preparo\\casos$. Conjunto de compartilhar a **Pasta de destino** para o arquivo frio armazenamento no Windows Azure, por exemplo \\ \\AZFile1\\ContentColdStorage. Selecione **criar um arquivo com um nome exclusivo**.
    
2. **Excluir pasta** atividade - definir o **caminho:** à coleção de compartilhamento de arquivo, por exemplo \\ \\preparo\\casos$\\* e selecione **Excluir todos os arquivos e subpastas**. 
    
7. Implante o runbook **MoveToColdStorage** usando os procedimentos em[Implantando Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Pesquisa do SharePoint local para armazenamento frio

1. Criar uma nova fonte de conteúdo em seu farm do SharePoint 2013 para o compartilhamento de armazenamento frio no Windows Azure, por exemplo \\ \\AZFile1\\ContentColdStorage. Para obter mais informações sobre como gerenciar fontes de conteúdo, consulte [Adicionar, editar ou excluir uma fonte de conteúdo no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. Inicie um rastreamento completo. Para mais informações, consulte [Iniciar, pausar, retomar ou parar um rastreamento no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Usando a solução

Há cinco etapas principais usando essa solução, supondo que você não quiser importar os arquivos PST para o Exchange Server 2013 e Exchange Online. Esta seção fornece os procedimentos para todos eles. Sua principal interação com a solução será ao fazer o seguinte:
  
1. Gerencie a associação do usuário no grupo responsáveis.
    
2. Revise os arquivos de log gerados pelo script de logon. O FileCopyErrors.log lista todos os arquivos que não foram copiados com êxito. É necessário decidir o que você deseja fazer com eles
    
3. Gerenciando o processo de importação de PST.
    
4. Mover os arquivos da coleção para armazenamento frio.
    
Todas as outras etapas não são específicas para essa solução. Eles são tarefas administrativas padrão que podem ser executadas no SharePoint 2013 e o Office 365 e o Windows Azure. Existem itens que essa solução não oferece quaisquer diretrizes que você precisará trabalhar check-out com base nas necessidades da sua empresa, como:
  
1. Controlando seus casos de eDiscovery e quais responsáveis estão associados a qual caso.
    
2. Controlando quais conjuntos de conjuntos de arquivo são associe com qual caso de descoberta eletrônica.
    
3. Coordenar o tempo de importação e mover para armazenamento frio etapas.
    
4. Gerenciando o espaço de arquivo usado no Windows Azure.
    
5. Gerenciando as caixas de correio que PSTs são importados para.
    
6. Backup e restauração de todos os dados de local.
    
### <a name="custodian-management"></a>Gerenciamento dos responsáveis

- Para iniciar o processo de coleta automatizada de arquivos para um usuário individual, adicioná-los ao grupo responsáveis. Na próxima vez que o usuário fizer logon, o script de logon atribuído ao grupo responsáveis pela diretiva de grupo será executado. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Monitore arquivos coletados e revisar os arquivos de log

1. Assista o arquivo da coleção compartilhar, por exemplo \\ \\preparo\\casos$\\*, para a pasta da coleção do usuário. O nome da pasta será formatado como esta: *yyyyMMddHHmm_UserName* .
    
2. Quando a coleção for concluída, abra a pasta da coleção e navegue até a pasta _Log. Na pasta _Log, você verá o seguinte:
    
  - Um arquivo XML para cada unidade local no computador do usuário, por exemplo **A.xml**, **C.xml**. Esses arquivos contêm as unidades de estoque que são nomeados após, e elas são usadas para a operação robocopy.
    
    > [!NOTE]
    > O script de coleção somente criará uma entrada no arquivo inventário para os tipos de arquivo que você definiu no próprio script. Além disso, ele não criará uma entrada de inventário para todos os arquivos no computador do usuário. 
  
  - Um arquivo de log denominado FileCopyErrors.log para cada conjunto de executar. Esse arquivo contém uma lista dos arquivos que robocopy poderia não uma cópia para o conjunto de arquivos compartilhar, por exemplo, \\ \\preparo\\casos$\\*. Você precisará revisar isso e decidir quais ações tomar para esses arquivos perdidos. Normalmente, você tanto precisa coletá-los manualmente, se desejado, ou você pode decidir que eles não são necessários e, portanto, podem ser omitidos da coleção.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Opção de importação de PST uma para o Exchange Server 2013

1. Faça logon servidor que hospeda o compartilhamento de arquivos da coleção, por exemplo **preparo**e abra o Windows PowerShell. Para obter mais informações sobre como iniciar o Windows PowerShell, consulte[Iniciando o Windows PowerShell no Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Defina a diretiva de execução como irrestrito. Tipo `Set-ExecutionPolicy Unrestricted -Scope Process` em Windows PowerShell e pressione Enter.
    
3. Execute o arquivo PSTImportScript.ps1 e fornecem os parâmetros **$SourcePath** e **$MailboxAlias** . Para obter mais informações sobre a execução de scripts do Windows PowerShell, consulte[Executando Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Analise a saída se há erros.
    
5. Antes de tentar importar um arquivo PST de nome idêntico para a mesma caixa de correio, você precisa remover a solicitação de importação da caixa de correio. Execute o seguinte comando para fazer isso: `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Você será solicitado para remover a cada solicitação individual da fila. Responda conforme necessário.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opção de importação de PST B, para o Exchange Online

- Para colocar os arquivos PST coletados em Exchange Online, siga os procedimentos nos arquivos de importação para o Office 365 por meio da seção de carregamento de rede do [Serviço de importação do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=614938).
    
### <a name="move-to-cold-storage"></a>Migrar para o armazenamento frio

1. Execute o runbook **MoveToColdStorage** usando os procedimentos em[Execução Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).
    
2. Observação o compartilhamento de arquivo Azure que você está usando para armazenamento de longo prazo, por exemplo \\ \\AZFile1\\ContentColdStorage e o arquivo da coleção local compartilharem, por exemplo \\ \\preparo\\casos$. Você deve ver os arquivos e pastas aparecem no compartilhamento de arquivo frio armazenamento e desaparecem do compartilhamento de arquivos da coleção.
    
### <a name="ediscovery"></a>eDiscovery

1. Permitir o rastreamento completo do compartilhamento de arquivo frio armazenamento para executar como agendas, ou inicia um rastreamento. Para obter mais informações sobre como iniciar rastreamentos completos ou incrementais, consulte [Iniciar, pausar, retomar ou parar um rastreamento no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Criar um caso de descoberta eletrônica no SharePoint 2013, se você usou a opção uma para uma importação de arquivos PST ou criar um caso de descoberta eletrônica no SharePoint Online, se você tiver usado a opção B.
    

