---
title: Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
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
ms.openlocfilehash: 0a0438917f6e7010b56703ce0bf73e89e1db0533
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para criar novos sites do SharePoint Online e, em seguida, adicionar usuários e grupos para esses sites.

Quando você usa o Office 365 PowerShell para criar sites do SharePoint Online e adicionar usuários, você pode rapidamente e repetidamente executar tarefas muito mais rápidas do que você pode fazer no Centro de administração do Office 356. Você também pode executar as tarefas que não serão possíveis executar no Centro de administração do Office 356. 

## <a name="before-you-begin"></a>Antes de começar

Os procedimentos neste tópico exigem que você se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Etapa 1: Criar novos conjuntos de sites usando o PowerShell do Office 365

Crie vários sites usando o Office 365 PowerShell e um arquivo. csv que você criar usando o código de exemplo fornecido e o bloco de notas. Esse procedimento, você substituirá as informações de espaço reservado mostradas na colchetes com suas próprias informações específicas do site e do inquilino. Esse processo permite que você crie um único arquivo e execute um comando do Office 365 PowerShell único que usa esse arquivo. Isso faz com que as ações realizadas repetível e portátil e elimina muitos, se não todos os erros que podem ser provenientes de comandos longos digitados no SharePoint Online Management Shell. Há duas partes para esse procedimento. Primeiro, você vai criar um arquivo. csv e, em seguida, você vai fazer referência a esse arquivo. csv usando o Office 365 PowerShell, que usará o seu conteúdo para criar os sites.

O cmdlet do PowerShell do Office 365 importa o arquivo. csv e canaliza para um loop dentro de chaves que lê a primeira linha do arquivo como cabeçalhos de coluna. Em seguida, o cmdlet do PowerShell do Office 365 percorre os registros restantes, cria um novo conjunto de sites para cada registro e atribui propriedades do conjunto de sites de acordo com os cabeçalhos de coluna.

###<a name="create-a-csv-file"></a>Criando um arquivo .csv

1. Abra o bloco de notas e cole o seguinte bloco de texto:</br>
```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```</br>Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</br>(You can press Ctrl+H when you use Notepad to bulk replace faster.)</br>
2. Save the file on your desktop as **SiteCollections.csv**.

 > [!TIP]
> Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.

### Run the Windows PowerShell command

1. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite-proprietário $_. Proprietário - StorageQuota $_. StorageQuota-Url $_. URL - NoWait - ResourceQuota $_. ResourceQuota-modelo $_. Modelo - TimeZoneID $_. TimeZoneID-Title $_. Nome}
```
</br>Where *MyAlias* equals your user alias.</br>
2. Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</br>
3. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
Get-SPOSite-detalhadas | Format-Table - AutoSize
```</br>
4. Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**.

That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.

## Step 2: Add users and groups

Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.

The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.

### Create .csv and .ps1 files

1. Open Notepad, and paste the following text block into it:</br>
```
Site, grupo, PermissionLevels https://tenant.sharepoint.com/sites/contosotest, Contoso Project Leads, controle total https://tenant.sharepoint.com/sites/contosotest, auditores da Contoso, somente exibição https://tenant.sharepoint.com/sites/contosotest, Designers Contoso, Design https://tenant.sharepoint.com/sites/TeamSite01, líderes de equipe de XT1000, controle total https://tenant.sharepoint.com/sites/TeamSite01, consultores XT1000, editar https://tenant.sharepoint.com/sites/Blog01, Contoso Blog Os designers, Design https://tenant.sharepoint.com/sites/Blog01, editores de Blog da Contoso, editar https://tenant.sharepoint.com/sites/Project01, Project alfa aprovadores, controle total
```
</br>Where *tenant* equals your tenant name.</br>
2. Save the file to your desktop as **GroupsAndPermissions.csv**.</br>
3. Open a new instance of Notepad, and paste the following text block into it:</br>
```
Grupo, LoginName, Site Contoso Project Leads, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest Contoso auditores, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest Contoso Designers, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest XT1000 líderes de equipe, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01 XT1000 consultores, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01 Designers de Blog da Contoso, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01 editores de Blog da Contoso, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01 Projeto de aprovadores alfa, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
</br>Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</br>
4. Save the file to your desktop as **Users.csv**.</br>
5. Open a new instance of Notepad, and paste the following text block into it:</br>
```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup-$_de grupo. Agrupar - PermissionLevels $_. PermissionLevels-$_de sites. Site} Import-Csv C:\users\MyAlias\desktop\Users.csv | onde {adicionar-SPOUser-grupo $_. Agrupe – LoginName $_. LoginName-Site $_. Site}
```
</br>Where MyAlias equals the user name of the user that is currently logged on.</br>
6. Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.

You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.

### Run UsersAndGroups.ps1 script

1. Return to the SharePoint Online Management Shell.</br>
2. At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</br>
```
Set-ExecutionPolicy Bypass
```</br>
3. At the confirmation prompt, press **Y**.</br>
4. At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</br>
```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
</br>Where *MyAlias* equals your user name.</br>
5. Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.

## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Manage SharePoint Online site groups Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

