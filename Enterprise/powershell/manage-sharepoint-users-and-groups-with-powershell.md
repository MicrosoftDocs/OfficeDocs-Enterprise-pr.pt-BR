---
title: Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell
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
description: 'Resumo: Usar o PowerShell do Office 365 para gerenciar usuários, grupos e sites do SharePoint Online.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para gerenciar usuários, grupos e sites do SharePoint Online.

Se você for um SharePoint Online que funciona com listas grandes de contas de usuário ou grupos e quiser uma maneira fácil de gerenciá-los, você pode usar o Office 365 PowerShell. 

## <a name="before-you-begin"></a>Antes de começar

Os procedimentos neste tópico exigem que você se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>Obter uma lista de sites, grupos e usuários

Antes de começarmos a gerenciar usuários e grupos, você precisa obter listas de seus sites, grupos e usuários. Você pode usar essas informações para resolver o exemplo neste artigo.

### <a name="get-a-list-of-sites"></a>Obter uma lista de sites

Obtenha uma lista dos sites em seu locatário com este comando:

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>Obter uma lista de grupos

Obtenha uma lista dos grupos em seu locatário com este comando:

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a>Obter uma lista de usuários

Obtenha uma lista dos usuários em seu locatário com este comando:

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Adicionar um usuário ao grupo de administradores ao site

Você pode usar o comando **Set-SPOUser** para adicionar um usuário à lista de administradores do conjunto de sites em um conjunto de sites. Esta é a aparência da sintaxe:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

Este exemplo usa variáveis para armazenar valores e tiver notas no script (por exemplo "<!--This is the Tenant Name…-->") para ajudá-lo a entender o que esses valores devem ser.

Por exemplo, este conjunto de comandos adiciona opala Castillo (opalc de nome de usuário) a lista de administradores do conjunto de sites no conjunto de sites ContosoTest no aluguel contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

Na realidade, você poderá cortar e colar estes comandos no Bloco de Notas, alterar os valores das variáveis $tenant, $site e $user para valores reais do seu ambiente e depois colá-los na sua janela do Shell de Gerenciamento do SharePoint Online.

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>Adicionar um usuário a outros grupos de Administradores de Conjunto de Sites

Essa tarefa, usaremos o comando **Add-SPOUser** para adicionar um usuário a um grupo do SharePoint em um conjunto de sites. Esta é a aparência da sintaxe:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

Por exemplo, vamos adicionar Glen apresenta (glenr de nome de usuário) ao grupo Auditores no conjunto de sites ContosoTest no aluguel contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Criar um grupo de conjunto de sites

Você pode usar o comando **Set-SPOSiteGroup** para criar um novo grupo do SharePoint e adicioná-lo ao conjunto de sites ContosoTest. Esta é a aparência da sintaxe:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> Você deve colocar qualquer cadeia de caracteres com espaços entre aspas. Propriedades de grupo, como os níveis de permissão, podem ser atualizadas posteriormente usando o cmdlet **Set-SPOSiteGroup** .

Por exemplo, vamos adicionar o grupo Auditores com permissões exibir apenas ao conjunto de sites de teste de Contoso no aluguel contoso1:

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Remover usuários de um grupo

Às vezes é preciso remover um usuário de um site ou até mesmo de todos os sites. Talvez o funcionário tenha sido transferido de uma divisão para outra ou tenha saído da empresa. Você pode facilmente fazer isso para um funcionário na interface do usuário. Mas isso não é tão fácil de fazer se você tiver que deslocar uma divisão inteira de um local para outro.

No entanto, usando os arquivos CSV e do Shell de gerenciamento do SharePoint Online, isso é rápido e fácil. Essa tarefa, você usará o Windows PowerShell para remover um usuário de um grupo de segurança do conjunto de sites. Em seguida, você usar um arquivo CSV e remover muitos usuários de sites diferentes. 

Usaremos o comando **Remove-SPOUser** para remover um único usuário do Office 365 de um grupo de conjunto de sites, apenas para que possamos consultar a sintaxe do comando. Aqui está como a sintaxe é:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

Por exemplo, vamos remover Bobby Overby de grupo Auditores de conjunto de sites no conjunto de sites de teste de Contoso no aluguel contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Vamos supor que queremos remover o Bobby de todos os grupos nos quais ele está. Procederemos do seguinte modo:

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> Isto é somente um exemplo. Você não deve executar esse comando, a menos que você realmente deseja remover um usuário de cada grupo, por exemplo, se o usuário deixar a empresa.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatizar o gerenciamento de grandes listas de usuários e grupos

Para adicionar um grande número de contas aos sites do SharePoint e conceda permissões, você pode usar o Centro de administração do Office 365, comandos do PowerShell individuais ou PowerShell um um arquivo CSV. Dessas opções, o arquivo CSV é a maneira mais rápida para automatizar essa tarefa.

O processo básico é criar um arquivo CSV que tem cabeçalhos (colunas) que correspondem aos parâmetros que precisa de script do Windows PowerShell. Você pode criar facilmente uma lista no Excel e, em seguida, exportá-lo como um arquivo CSV. Em seguida, você deve usar um script do Windows PowerShell para percorrer registros (linhas) no arquivo CSV, adicionando os usuários a grupos e os grupos aos sites. 

Por exemplo, vamos criar um arquivo CSV para a definição de um grupo de conjuntos de sites, grupos e permissões. Em seguida, vamos criar um arquivo CSV para popular os grupos com os usuários. Finalmente, vamos criar e executar um script simples do Windows PowerShell que cria e preenche os grupos.

O primeiro arquivo CSV adicionará um ou mais grupos para um ou mais conjuntos de sites e terá essa estrutura:

### <a name="header"></a>Cabeçalho:

```
Site,Group,PermissionLevels
```

### <a name="item"></a>Item:

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

Aqui está o segundo arquivo:

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

O segundo arquivo CSV adicionará um ou mais usuários a um ou mais grupos e terá essa estrutura:

### <a name="header"></a>Cabeçalho:

```
Group,LoginName,Site
```

### <a name="item"></a>Item:

```
group,login,https://tenant.sharepoint.com/sites/site
```

Aqui está o segundo arquivo:

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

Para a próxima etapa, você deverá salvar os dois arquivos CSV na sua unidade. Aqui estão os comandos que usam ambos os arquivos CSV para adicionar permissões e associações de grupo:

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

O script importa o conteúdo do arquivo CSV e usa os valores nas colunas (em negrito) para popular os parâmetros dos comandos **New-SPOSiteGroup** e **Add-SPOUser** . No nosso exemplo, estamos economizando isso na unidade C, mas você poderá salvá-lo, onde você desejar.

Agora, vamos remover várias pessoas de vários grupos em diferentes sites usando o mesmo arquivo CSV. Aqui está o comando:

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Gerar relatórios de usuário

Você pode querer obter um relatório simples para alguns sites e exibir os usuários destes sites, o seu nível de permissão e outras propriedades. A sintaxe é a seguinte:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Isso irá capturar os dados para esses três sites e gravá-los em um arquivo de texto em sua unidade local. Observe que o parâmetro – Append irá adicionar o novo conteúdo para um arquivo existente.

Por exemplo, vamos executar um relatório nos sites ContosoTest, TeamSite01 e Project01 do locatário Contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Observe que precisamos alterar apenas a variável **$site** . A variável **$tenant** mantém seu valor por meio de todas as execuções de três do comando.

Mas e se você quiser fazer isso em todos os sites? Você poderá fazer isso sem ter que digitar todos os sites usando este comando:

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Este relatório é razoavelmente simple e você pode adicionar mais código para criar relatórios ou relatórios que incluem informações mais detalhadas mais específica. Mas isso deve dar uma ideia de como usar o Shell de gerenciamento do SharePoint Online para gerenciar usuários no ambiente do SharePoint Online.
   
## <a name="see-also"></a>Confira também

[Conectar-se ao PowerShell do SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Gerenciar o SharePoint Online com o Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

