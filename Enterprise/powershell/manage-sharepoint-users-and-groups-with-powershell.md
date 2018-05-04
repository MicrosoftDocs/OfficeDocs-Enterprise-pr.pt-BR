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
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="d985f-103">Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d985f-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="d985f-104">**Resumo:** Use o Office 365 PowerShell para gerenciar usuários, grupos e sites do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d985f-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="d985f-105">Se você for um SharePoint Online que funciona com listas grandes de contas de usuário ou grupos e quiser uma maneira fácil de gerenciá-los, você pode usar o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d985f-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="d985f-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="d985f-106">Before you begin</span></span>

<span data-ttu-id="d985f-p101">Os procedimentos neste tópico exigem que você se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="d985f-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="d985f-109">Obter uma lista de sites, grupos e usuários</span><span class="sxs-lookup"><span data-stu-id="d985f-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="d985f-p102">Antes de começarmos a gerenciar usuários e grupos, você precisa obter listas de seus sites, grupos e usuários. Você pode usar essas informações para resolver o exemplo neste artigo.</span><span class="sxs-lookup"><span data-stu-id="d985f-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="d985f-112">Obter uma lista de sites</span><span class="sxs-lookup"><span data-stu-id="d985f-112">Get a list of sites</span></span>

<span data-ttu-id="d985f-113">Obtenha uma lista dos sites em seu locatário com este comando:</span><span class="sxs-lookup"><span data-stu-id="d985f-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="d985f-114">Obter uma lista de grupos</span><span class="sxs-lookup"><span data-stu-id="d985f-114">Get a list of groups</span></span>

<span data-ttu-id="d985f-115">Obtenha uma lista dos grupos em seu locatário com este comando:</span><span class="sxs-lookup"><span data-stu-id="d985f-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="d985f-116">Obter uma lista de usuários</span><span class="sxs-lookup"><span data-stu-id="d985f-116">Get a list of users</span></span>

<span data-ttu-id="d985f-117">Obtenha uma lista dos usuários em seu locatário com este comando:</span><span class="sxs-lookup"><span data-stu-id="d985f-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="d985f-118">Adicionar um usuário ao grupo de administradores ao site</span><span class="sxs-lookup"><span data-stu-id="d985f-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="d985f-p103">Você pode usar o comando **Set-SPOUser** para adicionar um usuário à lista de administradores do conjunto de sites em um conjunto de sites. Esta é a aparência da sintaxe:</span><span class="sxs-lookup"><span data-stu-id="d985f-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="d985f-121">Este exemplo usa variáveis para armazenar valores e tiver notas no script (por exemplo "<!--This is the Tenant Name…-->") para ajudá-lo a entender o que esses valores devem ser.</span><span class="sxs-lookup"><span data-stu-id="d985f-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="d985f-122">Por exemplo, este conjunto de comandos adiciona opala Castillo (opalc de nome de usuário) a lista de administradores do conjunto de sites no conjunto de sites ContosoTest no aluguel contoso1:</span><span class="sxs-lookup"><span data-stu-id="d985f-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="d985f-123">Na realidade, você poderá cortar e colar estes comandos no Bloco de Notas, alterar os valores das variáveis $tenant, $site e $user para valores reais do seu ambiente e depois colá-los na sua janela do Shell de Gerenciamento do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d985f-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="d985f-124">Adicionar um usuário a outros grupos de Administradores de Conjunto de Sites</span><span class="sxs-lookup"><span data-stu-id="d985f-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="d985f-p104">Essa tarefa, usaremos o comando **Add-SPOUser** para adicionar um usuário a um grupo do SharePoint em um conjunto de sites. Esta é a aparência da sintaxe:</span><span class="sxs-lookup"><span data-stu-id="d985f-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

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

<span data-ttu-id="d985f-127">Por exemplo, vamos adicionar Glen apresenta (glenr de nome de usuário) ao grupo Auditores no conjunto de sites ContosoTest no aluguel contoso1:</span><span class="sxs-lookup"><span data-stu-id="d985f-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="d985f-128">Criar um grupo de conjunto de sites</span><span class="sxs-lookup"><span data-stu-id="d985f-128">Create a site collection group</span></span>

<span data-ttu-id="d985f-p105">Você pode usar o comando **Set-SPOSiteGroup** para criar um novo grupo do SharePoint e adicioná-lo ao conjunto de sites ContosoTest. Esta é a aparência da sintaxe:</span><span class="sxs-lookup"><span data-stu-id="d985f-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

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
> <span data-ttu-id="d985f-p106">Você deve colocar qualquer cadeia de caracteres com espaços entre aspas. Propriedades de grupo, como os níveis de permissão, podem ser atualizadas posteriormente usando o cmdlet **Set-SPOSiteGroup** .</span><span class="sxs-lookup"><span data-stu-id="d985f-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="d985f-133">Por exemplo, vamos adicionar o grupo Auditores com permissões exibir apenas ao conjunto de sites de teste de Contoso no aluguel contoso1:</span><span class="sxs-lookup"><span data-stu-id="d985f-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="d985f-134">Remover usuários de um grupo</span><span class="sxs-lookup"><span data-stu-id="d985f-134">Remove users from a group</span></span>

<span data-ttu-id="d985f-p107">Às vezes é preciso remover um usuário de um site ou até mesmo de todos os sites. Talvez o funcionário tenha sido transferido de uma divisão para outra ou tenha saído da empresa. Você pode facilmente fazer isso para um funcionário na interface do usuário. Mas isso não é tão fácil de fazer se você tiver que deslocar uma divisão inteira de um local para outro.</span><span class="sxs-lookup"><span data-stu-id="d985f-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="d985f-p108">No entanto, usando os arquivos CSV e do Shell de gerenciamento do SharePoint Online, isso é rápido e fácil. Essa tarefa, você usará o Windows PowerShell para remover um usuário de um grupo de segurança do conjunto de sites. Em seguida, você usar um arquivo CSV e remover muitos usuários de sites diferentes.</span><span class="sxs-lookup"><span data-stu-id="d985f-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="d985f-p109">Usaremos o comando **Remove-SPOUser** para remover um único usuário do Office 365 de um grupo de conjunto de sites, apenas para que possamos consultar a sintaxe do comando. Aqui está como a sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="d985f-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

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

<span data-ttu-id="d985f-143">Por exemplo, vamos remover Bobby Overby de grupo Auditores de conjunto de sites no conjunto de sites de teste de Contoso no aluguel contoso1:</span><span class="sxs-lookup"><span data-stu-id="d985f-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="d985f-p110">Vamos supor que queremos remover o Bobby de todos os grupos nos quais ele está. Procederemos do seguinte modo:</span><span class="sxs-lookup"><span data-stu-id="d985f-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="d985f-p111">Isto é somente um exemplo. Você não deve executar esse comando, a menos que você realmente deseja remover um usuário de cada grupo, por exemplo, se o usuário deixar a empresa.</span><span class="sxs-lookup"><span data-stu-id="d985f-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="d985f-148">Automatizar o gerenciamento de grandes listas de usuários e grupos</span><span class="sxs-lookup"><span data-stu-id="d985f-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="d985f-p112">Para adicionar um grande número de contas aos sites do SharePoint e conceda permissões, você pode usar o Centro de administração do Office 365, comandos do PowerShell individuais ou PowerShell um um arquivo CSV. Dessas opções, o arquivo CSV é a maneira mais rápida para automatizar essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="d985f-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="d985f-p113">O processo básico é criar um arquivo CSV que tem cabeçalhos (colunas) que correspondem aos parâmetros que precisa de script do Windows PowerShell. Você pode criar facilmente uma lista no Excel e, em seguida, exportá-lo como um arquivo CSV. Em seguida, você deve usar um script do Windows PowerShell para percorrer registros (linhas) no arquivo CSV, adicionando os usuários a grupos e os grupos aos sites.</span><span class="sxs-lookup"><span data-stu-id="d985f-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="d985f-p114">Por exemplo, vamos criar um arquivo CSV para a definição de um grupo de conjuntos de sites, grupos e permissões. Em seguida, vamos criar um arquivo CSV para popular os grupos com os usuários. Finalmente, vamos criar e executar um script simples do Windows PowerShell que cria e preenche os grupos.</span><span class="sxs-lookup"><span data-stu-id="d985f-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="d985f-157">O primeiro arquivo CSV adicionará um ou mais grupos para um ou mais conjuntos de sites e terá essa estrutura:</span><span class="sxs-lookup"><span data-stu-id="d985f-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="d985f-158">Cabeçalho:</span><span class="sxs-lookup"><span data-stu-id="d985f-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="d985f-159">Item:</span><span class="sxs-lookup"><span data-stu-id="d985f-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="d985f-160">Aqui está o segundo arquivo:</span><span class="sxs-lookup"><span data-stu-id="d985f-160">Here is an example file:</span></span>

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

<span data-ttu-id="d985f-161">O segundo arquivo CSV adicionará um ou mais usuários a um ou mais grupos e terá essa estrutura:</span><span class="sxs-lookup"><span data-stu-id="d985f-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="d985f-162">Cabeçalho:</span><span class="sxs-lookup"><span data-stu-id="d985f-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="d985f-163">Item:</span><span class="sxs-lookup"><span data-stu-id="d985f-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="d985f-164">Aqui está o segundo arquivo:</span><span class="sxs-lookup"><span data-stu-id="d985f-164">Here is an example file:</span></span>

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

<span data-ttu-id="d985f-p115">Para a próxima etapa, você deverá salvar os dois arquivos CSV na sua unidade. Aqui estão os comandos que usam ambos os arquivos CSV para adicionar permissões e associações de grupo:</span><span class="sxs-lookup"><span data-stu-id="d985f-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="d985f-p116">O script importa o conteúdo do arquivo CSV e usa os valores nas colunas (em negrito) para popular os parâmetros dos comandos **New-SPOSiteGroup** e **Add-SPOUser** . No nosso exemplo, estamos economizando isso na unidade C, mas você poderá salvá-lo, onde você desejar.</span><span class="sxs-lookup"><span data-stu-id="d985f-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="d985f-p117">Agora, vamos remover várias pessoas de vários grupos em diferentes sites usando o mesmo arquivo CSV. Aqui está o comando:</span><span class="sxs-lookup"><span data-stu-id="d985f-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="d985f-171">Gerar relatórios de usuário</span><span class="sxs-lookup"><span data-stu-id="d985f-171">Generate user reports</span></span>

<span data-ttu-id="d985f-p118">Você pode querer obter um relatório simples para alguns sites e exibir os usuários destes sites, o seu nível de permissão e outras propriedades. A sintaxe é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="d985f-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="d985f-p119">Isso irá capturar os dados para esses três sites e gravá-los em um arquivo de texto em sua unidade local. Observe que o parâmetro – Append irá adicionar o novo conteúdo para um arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="d985f-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="d985f-176">Por exemplo, vamos executar um relatório nos sites ContosoTest, TeamSite01 e Project01 do locatário Contoso1:</span><span class="sxs-lookup"><span data-stu-id="d985f-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="d985f-p120">Observe que precisamos alterar apenas a variável **$site** . A variável **$tenant** mantém seu valor por meio de todas as execuções de três do comando.</span><span class="sxs-lookup"><span data-stu-id="d985f-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="d985f-p121">Mas e se você quiser fazer isso em todos os sites? Você poderá fazer isso sem ter que digitar todos os sites usando este comando:</span><span class="sxs-lookup"><span data-stu-id="d985f-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="d985f-p122">Este relatório é razoavelmente simple e você pode adicionar mais código para criar relatórios ou relatórios que incluem informações mais detalhadas mais específica. Mas isso deve dar uma ideia de como usar o Shell de gerenciamento do SharePoint Online para gerenciar usuários no ambiente do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d985f-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="d985f-183">Confira também</span><span class="sxs-lookup"><span data-stu-id="d985f-183">See also</span></span>

[<span data-ttu-id="d985f-184">Conectar-se ao PowerShell do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d985f-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="d985f-185">Gerenciar o SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d985f-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="d985f-186">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d985f-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d985f-187">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d985f-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

