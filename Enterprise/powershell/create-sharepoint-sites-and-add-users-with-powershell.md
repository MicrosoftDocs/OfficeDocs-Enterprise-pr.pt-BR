---
title: Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumo: Use o Office 365 PowerShell para criar novos sites do SharePoint Online e, em seguida, adicione usuários e grupos a esses sites.'
ms.openlocfilehash: c2ed2afd7915fa5fc3aa936b5aa09cf90679ff97
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069097"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para criar novos sites do SharePoint Online e, em seguida, adicione usuários e grupos a esses sites.

Ao usar o Office 365 PowerShell para criar sites do SharePoint Online e adicionar usuários, você pode executar as tarefas com rapidez e repetidamente do que você pode no centro de administração do Office 356. Você também pode executar tarefas que não são possíveis de realizar no centro de administração do Office 356. 

## <a name="before-you-begin"></a>Antes de começar

Os procedimentos neste tópico exigem que você se conecte ao SharePoint Online. Para obter instruções, consulte [conectar-se ao PowerShell do SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Etapa 1: criar novos conjuntos de sites usando o Office 365 PowerShell

Crie vários sites usando o Office 365 PowerShell e um arquivo. csv que você cria usando o código de exemplo fornecido e o bloco de notas. Para este procedimento, você substituirá as informações do espaço reservado mostradas entre colchetes com suas próprias informações específicas do site e do locatário. Esse processo permite que você crie um único arquivo e execute um único comando do Office 365 PowerShell que usa esse arquivo. Isso faz com que as ações sejam refeitas e portáveis e elimina muitas, se não todos os, erros que podem vir da digitação de comandos Long no Shell de gerenciamento do SharePoint Online. Há duas partes nesse procedimento. Primeiro, você criará um arquivo. csv e, em seguida, fará referência a esse arquivo. CSV usando o Office 365 PowerShell, que usará seu conteúdo para criar os sites.

O cmdlet do Office 365 PowerShell importa o arquivo. csv e o canaliza para um loop dentro das chaves que lê a primeira linha do arquivo como cabeçalhos de coluna. O cmdlet do PowerShell do Office 365, em seguida, itera por meio dos registros restantes, cria um novo conjunto de sites para cada registro e atribui Propriedades do conjunto de sites de acordo com os cabeçalhos da coluna.

### <a name="create-a-csv-file"></a>Criando um arquivo .csv

1. Abra o bloco de notas e cole o seguinte bloco de texto:<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>Onde *locatário* é o nome do seu locatário e *proprietário* é o nome de usuário do usuário em seu locatário para o qual você deseja conceder a função de administrador do conjunto de sites principal.<br/>(Você pode pressionar CTRL + H ao usar o bloco de notas para substituir em massa mais rápido.)<br/>

2. Salve o arquivo na área de trabalho como **SiteCollections. csv**.<br/>

> [!TIP]
> Antes de usar este ou qualquer outro arquivo de script. csv ou do Windows PowerShell, é recomendável garantir que não haja caracteres estranhos ou não imprimíveis. Abra o arquivo no Word, e na faixa de opções, clique no ícone do parágrafo  para mostrar caracteres não imprimíveis. Não deve haver caracteres estranhos não imprimíveis. Por exemplo, não deve haver marcas do parágrafo no final do arquivo.

### <a name="run-the-windows-powershell-command"></a>Execute o comando do Windows PowerShell:

1. No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione ENTER:<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>Em ** que myalias é igual ao seu alias de usuário.<br/>

2. Aguarde até que o prompt do Windows PowerShell reapareça. Pode demorar um minuto ou dois.<br/>

3. No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione ENTER:<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. Observe os novos conjuntos de sites na lista. Você deve ver os seguintes conjuntos de sites: **ContosoTest**, **TeamSite01**, **Blog01**e **Project01**

É isso. Você criou vários conjuntos de sites usando o arquivo. csv criado e um único cmdlet do Windows PowerShell. Agora você está pronto para criar e alocar usuários nestes sites.

## <a name="step-2-add-users-and-groups"></a>Etapa 2: Adicionar usuários ou grupos

Agora você criará usuários e irá adicioná-los ao grupo do site. Então você usará um arquivo csv. para fazer o carregamento em massa de novos grupos e usuários.

Os procedimentos a seguir indicam que você criou com sucesso os conjuntos de sites contosotest, TeamSite01, Blog01, e Project01.

### <a name="create-csv-and-ps1-files"></a>Criando arquivos .csv e .ps1

1. Abra o bloco de notas e cole o seguinte bloco de texto:<br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>Onde *locatário* é igual ao nome do locatário.<br/>

2. Salve o arquivo em sua área de trabalho como **GroupsAndPermissions. csv**.<br/>

3. Abra uma nova instância do bloco de notas e cole o seguinte bloco de texto:<br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>Onde *locatário* é igual ao nome do locatário e *username* é igual ao nome de usuário de um usuário existente.<br/>

4. Salve o arquivo na sua área de trabalho como **users. csv**.<br/>

5. Abra uma nova instância do bloco de notas e cole o seguinte bloco de texto:<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>Em que myalias é igual ao nome de usuário do usuário que está conectado no momento.<br/>

6. Salve o arquivo em sua área de trabalho como **UsersAndGroups. ps1**. Este é um script simples do Windows PowerShell.

Agora você está pronto para executar o script UsersAndGroup.ps1 para adicionar usuários e grupos a vários conjuntos de sites.

### <a name="run-usersandgroupsps1-script"></a>Execute o script UsersAndGroups.ps1

1. Retorne ao shell de gerenciamento do SharePoint Online<br/>
2. No prompt do Windows PowerShell, digite ou copie e cole a seguinte linha e pressione ENTER:<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. No prompt de confirmação, pressione **s**.<br/>

4. No prompt do Windows PowerShell, digite ou copie e cole o seguinte e pressione ENTER:<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>Em ** que myalias é igual ao nome de usuário.<br/>

5. Aguarde a solicitação de retorno do prompt antes de prosseguir. Os grupos aparecerão de acordo com a criação dos mesmos. Então você verá a repetição da lista do grupo de acordo com os usuários que são agregados.

## <a name="see-also"></a>Confira também

[Conectar ao PowerShell do SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Gerenciar grupos de sites do SharePoint Online Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

