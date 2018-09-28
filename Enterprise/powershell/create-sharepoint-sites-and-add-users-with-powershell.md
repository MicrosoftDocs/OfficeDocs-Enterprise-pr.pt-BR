---
title: Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumo: Usar o PowerShell do Office 365 para criar novos sites do SharePoint Online e, em seguida, adicionar usuários e grupos para esses sites.'
ms.openlocfilehash: 41ca26249bd494d5603a425689e47f9fe6809f1a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975199"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para criar novos sites do SharePoint Online e, em seguida, adicionar usuários e grupos para esses sites.

Quando você usa o Office 365 PowerShell para criar sites do SharePoint Online e adicionar usuários, você pode rapidamente e repetidamente executar tarefas muito mais rápidas do que você pode fazer no Centro de administração do Office 356. Você também pode executar as tarefas que não serão possíveis executar no Centro de administração do Office 356. 

## <a name="before-you-begin"></a>Antes de começar

Os procedimentos neste tópico exigem que você se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Etapa 1: Criar novos conjuntos de sites usando o PowerShell do Office 365

Crie vários sites usando o Office 365 PowerShell e um arquivo. csv que você criar usando o código de exemplo fornecido e o bloco de notas. Esse procedimento, você substituirá as informações de espaço reservado mostradas na colchetes com suas próprias informações específicas do site e do inquilino. Esse processo permite que você crie um único arquivo e execute um comando do Office 365 PowerShell único que usa esse arquivo. Isso faz com que as ações realizadas repetível e portátil e elimina muitos, se não todos os erros que podem ser provenientes de comandos longos digitados no SharePoint Online Management Shell. Há duas partes para esse procedimento. Primeiro, você vai criar um arquivo. csv e, em seguida, você vai fazer referência a esse arquivo. csv usando o Office 365 PowerShell, que usará o seu conteúdo para criar os sites.

O cmdlet do PowerShell do Office 365 importa o arquivo. csv e canaliza para um loop dentro de chaves que lê a primeira linha do arquivo como cabeçalhos de coluna. Em seguida, o cmdlet do PowerShell do Office 365 percorre os registros restantes, cria um novo conjunto de sites para cada registro e atribui propriedades do conjunto de sites de acordo com os cabeçalhos de coluna.

### <a name="create-a-csv-file"></a>Criando um arquivo .csv

1. Abra o bloco de notas e cole o seguinte bloco de texto:<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>Onde o *locatário* é o nome do seu locatário e *proprietário* é o nome de usuário do usuário do seu locatário aos quais você deseja conceder o papel de administrador do conjunto de sites primário.<br/>(Você pode pressionar Ctrl + H ao usar o bloco de notas para em massa substituir mais rápido).<br/>

2. Salve o arquivo no seu desktop como **Sitecollections**.<br/>

> [!TIP]
> Antes de usar esta ou qualquer outro. csv ou arquivo de script do Windows PowerShell, é uma boa prática para certificar-se de que não há nenhum caractere incorretas ou não-imprimível. Abra o arquivo no Word e, na faixa de opções, clique no ícone de parágrafo para mostrar os caracteres não imprimíveis. Não deve haver nenhum caracteres não-imprimíveis não essenciais. Por exemplo, deve haver sem marcas de parágrafo além daquela final no final do arquivo.

### <a name="run-the-windows-powershell-command"></a>Execute o comando do Windows PowerShell:

1. No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione Enter:<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>Onde *MyAlias* é igual ao seu nome de usuário.<br/>

2. Aguarde o prompt do Windows PowerShell reaparecem. Ela pode levar um minuto ou dois.<br/>

3. No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione Enter:<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. Observe os novos conjuntos de sites na lista. Você deverá ver os seguintes conjuntos de sites: **contosotest**, **TeamSite01**, **Blog01**e **Project01**

É isso. Você criou vários conjuntos de sites usando o arquivo. csv que você criou e um único cmdlet do Windows PowerShell. Agora você está pronto para criar e atribuir usuários a esses sites.

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
<br/>Onde *inquilino* é igual ao nome do seu locatário.<br/>

2. Salve o arquivo seu desktop como **GroupsandPermissions**.<br/>

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
<br/>Onde *inquilino* é igual ao nome do seu locatário e *username* é igual ao nome de usuário de um usuário existente.<br/>

4. Salve o arquivo seu desktop como **Users**.<br/>

5. Abra uma nova instância do bloco de notas e cole o seguinte bloco de texto:<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>Onde o MyAlias é igual ao nome de usuário do usuário que está conectado no momento.<br/>

6. Salve o arquivo em sua área de trabalho como **UsersAndGroups.ps1**. Este é um simple script do Windows PowerShell.

Agora você está pronto para executar o script UsersAndGroup.ps1 para adicionar usuários e grupos a vários conjuntos de sites.

### <a name="run-usersandgroupsps1-script"></a>Execute o script UsersAndGroups.ps1

1. Retorne ao shell de gerenciamento do SharePoint Online<br/>
2. No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione Enter:<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. No prompt de confirmação, clique em **Y**.<br/>

4. No prompt do Windows PowerShell, tipo ou copiar e colar o seguinte cmdlet e pressione insira:<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>Onde *MyAlias* é igual a seu nome de usuário.<br/>

5. Aguarde a solicitação de retorno do prompt antes de prosseguir. Os grupos aparecerão de acordo com a criação dos mesmos. Então você verá a repetição da lista do grupo de acordo com os usuários que são agregados.

## <a name="see-also"></a>Confira também

[Conectar ao PowerShell do SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Gerenciar grupos de sites do SharePoint Online do Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

