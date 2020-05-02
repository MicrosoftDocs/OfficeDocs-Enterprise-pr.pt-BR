---
title: Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumo: Use o Office 365 PowerShell para gerenciar usuários, grupos e sites do SharePoint Online.'
ms.openlocfilehash: c820fd009635a8a9b27f28d858d345794bea6334
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004114"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="bbfef-103">Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbfef-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

<span data-ttu-id="bbfef-104">Se você for um administrador do SharePoint Online que trabalha com grandes listas de contas de usuário ou grupos e deseja uma maneira mais fácil de gerenciá-los, você pode usar o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bbfef-104">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

<span data-ttu-id="bbfef-105">Antes de começar, os procedimentos neste tópico exigem que você se conecte ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bbfef-105">Before you begin, the procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="bbfef-106">Para obter instruções, consulte [conectar-se ao PowerShell do SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="bbfef-106">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="bbfef-107">Obter uma lista de sites, grupos e usuários</span><span class="sxs-lookup"><span data-stu-id="bbfef-107">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="bbfef-p102">Antes de começarmos a gerenciar usuários e grupos, você precisa obter listas de seus sites, grupos e usuários. Você pode usar essas informações para resolver o exemplo neste artigo.</span><span class="sxs-lookup"><span data-stu-id="bbfef-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

<span data-ttu-id="bbfef-110">Obtenha uma lista dos sites em seu locatário com este comando:</span><span class="sxs-lookup"><span data-stu-id="bbfef-110">Get a list of the sites in your tenant with this command:</span></span>

```powershell
Get-SPOSite
```

<span data-ttu-id="bbfef-111">Obtenha uma lista dos grupos em seu locatário com este comando:</span><span class="sxs-lookup"><span data-stu-id="bbfef-111">Get a list of the groups in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

<span data-ttu-id="bbfef-112">Obtenha uma lista dos usuários em seu locatário com este comando:</span><span class="sxs-lookup"><span data-stu-id="bbfef-112">Get a list of the users in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="bbfef-113">Adicionar um usuário ao grupo de administradores ao site</span><span class="sxs-lookup"><span data-stu-id="bbfef-113">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="bbfef-114">Você usa o `Set-SPOUser` cmdlet para adicionar um usuário à lista de administradores de conjunto de sites em um conjunto de sites.</span><span class="sxs-lookup"><span data-stu-id="bbfef-114">You use the `Set-SPOUser` cmdlet to add a user to the list of Site Collection Administrators on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="bbfef-115">Para usar esses comandos, substitua substituir tudo dentro das aspas, incluindo os caracteres < e >, com os nomes corretos.</span><span class="sxs-lookup"><span data-stu-id="bbfef-115">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="bbfef-116">Por exemplo, este conjunto de comandos adiciona o Opal Martins (nome de usuário opalc) a lista de administradores de conjunto de sites no conjunto de sites do ContosoTest no locatário da Contoso:</span><span class="sxs-lookup"><span data-stu-id="bbfef-116">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="bbfef-117">Você pode copiar e colar esses comandos no bloco de notas, alterar os valores de variáveis para $tenant, $site e $user para valores reais do seu ambiente e, em seguida, colá-los na janela do Shell de gerenciamento do SharePoint Online para executá-los.</span><span class="sxs-lookup"><span data-stu-id="bbfef-117">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-groups"></a><span data-ttu-id="bbfef-118">Adicionar um usuário a outros grupos de conjuntos de sites</span><span class="sxs-lookup"><span data-stu-id="bbfef-118">Add a user to other site collection groups</span></span>

<span data-ttu-id="bbfef-119">Nesta tarefa, usaremos o `Add-SPOUser` cmdlet para adicionar um usuário a um grupo do SharePoint em um conjunto de sites.</span><span class="sxs-lookup"><span data-stu-id="bbfef-119">In this task, we'll use the `Add-SPOUser` cmdlet to add a user to a SharePoint group on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="bbfef-120">Por exemplo, vamos adicionar Glen Rife (nome de usuário glenr) ao grupo auditores no conjunto de sites ContosoTest no aluguel da Contoso:</span><span class="sxs-lookup"><span data-stu-id="bbfef-120">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="bbfef-121">Criar um grupo de conjunto de sites</span><span class="sxs-lookup"><span data-stu-id="bbfef-121">Create a site collection group</span></span>

<span data-ttu-id="bbfef-122">Você usa o `New-SPOSiteGroup` cmdlet para criar um novo grupo do SharePoint e adicioná-lo a um conjunto de sites.</span><span class="sxs-lookup"><span data-stu-id="bbfef-122">You use the `New-SPOSiteGroup` cmdlet to create a new SharePoint group and add it to a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="bbfef-123">Propriedades de grupo, como níveis de permissão, podem ser atualizadas posteriormente usando `Set-SPOSiteGroup` o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbfef-123">Group properties, such as permission levels, can be updated later by using the `Set-SPOSiteGroup` cmdlet.</span></span>

<span data-ttu-id="bbfef-124">Por exemplo, vamos adicionar o grupo auditores com permissões somente para exibição no conjunto de sites do ContosoTest no locatário da Contoso:</span><span class="sxs-lookup"><span data-stu-id="bbfef-124">For example, let’s add the Auditors group with View Only permissions to the contosotest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="bbfef-125">Remover usuários de um grupo</span><span class="sxs-lookup"><span data-stu-id="bbfef-125">Remove users from a group</span></span>

<span data-ttu-id="bbfef-p103">Às vezes é preciso remover um usuário de um site ou até mesmo de todos os sites. Talvez o funcionário tenha sido transferido de uma divisão para outra ou tenha saído da empresa. Você pode facilmente fazer isso para um funcionário na interface do usuário. Mas isso não é tão fácil de fazer se você tiver que deslocar uma divisão inteira de um local para outro.</span><span class="sxs-lookup"><span data-stu-id="bbfef-p103">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="bbfef-129">No entanto, usando os arquivos do Shell de gerenciamento do SharePoint Online e CSV, isso é rápido e fácil.</span><span class="sxs-lookup"><span data-stu-id="bbfef-129">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="bbfef-130">Nesta tarefa, você usará o Windows PowerShell para remover um usuário de um grupo de segurança de um conjunto de sites.</span><span class="sxs-lookup"><span data-stu-id="bbfef-130">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="bbfef-131">Neste caso, você usará um arquivo CSV e removerá muitos usuários de sites diferentes.</span><span class="sxs-lookup"><span data-stu-id="bbfef-131">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="bbfef-132">Vamos usar o cmdlet "Remove-marido" para remover um único usuário do Office 365 de um grupo de conjuntos de sites para que possamos ver a sintaxe do comando.</span><span class="sxs-lookup"><span data-stu-id="bbfef-132">We'll be using the 'Remove-SPOUser' cmdlet to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="bbfef-133">A sintaxe é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="bbfef-133">Here is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="bbfef-134">Por exemplo, vamos remover Bobby dias do grupo de auditores do conjunto de sites no conjunto de sites do ContosoTest no locatário da Contoso:</span><span class="sxs-lookup"><span data-stu-id="bbfef-134">For example, let’s remove Bobby Overby from the site collection Auditors group in the contosotest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="bbfef-135">Vamos supor que queremos remover o Bobby de todos os grupos nos quais ele está.</span><span class="sxs-lookup"><span data-stu-id="bbfef-135">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="bbfef-136">Procederemos do seguinte modo:</span><span class="sxs-lookup"><span data-stu-id="bbfef-136">Here is how we would do that:</span></span>

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="bbfef-137">Este é apenas um exemplo.</span><span class="sxs-lookup"><span data-stu-id="bbfef-137">This is just an example.</span></span> <span data-ttu-id="bbfef-138">Você não deve executar esse comando, a menos que você realmente deseja remover um usuário de cada grupo, por exemplo, se o usuário deixar a empresa.</span><span class="sxs-lookup"><span data-stu-id="bbfef-138">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="bbfef-139">Automatizar o gerenciamento de grandes listas de usuários e grupos</span><span class="sxs-lookup"><span data-stu-id="bbfef-139">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="bbfef-140">Para adicionar um grande número de contas a sites do SharePoint e conceder permissões, você pode usar o centro de administração do 365, comandos individuais do PowerShell ou o PowerShell um arquivo CSV.</span><span class="sxs-lookup"><span data-stu-id="bbfef-140">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="bbfef-141">Dessas escolhas, o arquivo CSV é a maneira mais rápida de automatizar esta tarefa.</span><span class="sxs-lookup"><span data-stu-id="bbfef-141">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="bbfef-142">O processo básico é a criação de um arquivo CSV com cabeçalhos (colunas) que correspondem aos parâmetros que requerem um script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bbfef-142">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="bbfef-143">Você pode facilmente criar uma lista no Excel e, em seguida, exportá-lo como um arquivo CSV.</span><span class="sxs-lookup"><span data-stu-id="bbfef-143">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="bbfef-144">Em seguida, você pode usar um script do Windows PowerShell para pesquisar nos registros (linhas) no arquivo CSV, adicionar usuários a grupos e os grupos para os sites.</span><span class="sxs-lookup"><span data-stu-id="bbfef-144">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="bbfef-p110">Por exemplo, vamos criar um arquivo CSV para a definição de um grupo de conjuntos de sites, grupos e permissões. Em seguida, vamos criar um arquivo CSV para popular os grupos com os usuários. Finalmente, vamos criar e executar um script simples do Windows PowerShell que cria e preenche os grupos.</span><span class="sxs-lookup"><span data-stu-id="bbfef-p110">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="bbfef-148">O primeiro arquivo CSV adicionará um ou mais grupos para um ou mais conjuntos de sites e terá essa estrutura:</span><span class="sxs-lookup"><span data-stu-id="bbfef-148">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

<span data-ttu-id="bbfef-149">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="bbfef-149">Header:</span></span>

```powershell
Site,Group,PermissionLevels
```

<span data-ttu-id="bbfef-150">Discrimina</span><span class="sxs-lookup"><span data-stu-id="bbfef-150">Item:</span></span>

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="bbfef-151">Aqui está o segundo arquivo:</span><span class="sxs-lookup"><span data-stu-id="bbfef-151">Here is an example file:</span></span>

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="bbfef-152">O segundo arquivo CSV adicionará um ou mais usuários a um ou mais grupos e terá essa estrutura:</span><span class="sxs-lookup"><span data-stu-id="bbfef-152">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

<span data-ttu-id="bbfef-153">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="bbfef-153">Header:</span></span>

```powershell
Group,LoginName,Site
```

<span data-ttu-id="bbfef-154">Discrimina</span><span class="sxs-lookup"><span data-stu-id="bbfef-154">Item:</span></span>

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="bbfef-155">Aqui está o segundo arquivo:</span><span class="sxs-lookup"><span data-stu-id="bbfef-155">Here is an example file:</span></span>

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

<span data-ttu-id="bbfef-156">Para a próxima etapa, você deverá salvar os dois arquivos CSV na sua unidade.</span><span class="sxs-lookup"><span data-stu-id="bbfef-156">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="bbfef-157">Aqui estão exemplos de comandos que usam arquivos CSV e adicionam permissões e membros de Grupo:</span><span class="sxs-lookup"><span data-stu-id="bbfef-157">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="bbfef-158">O script importa o conteúdo do arquivo CSV e usa os valores nas colunas para preencher os parâmetros dos comandos **New-SPOSiteGroup** e **Add-marido** .</span><span class="sxs-lookup"><span data-stu-id="bbfef-158">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="bbfef-159">No nosso exemplo, estamos salvando isso na pasta theO365Admin na unidade C, mas você pode salvá-lo onde quiser.</span><span class="sxs-lookup"><span data-stu-id="bbfef-159">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="bbfef-160">Agora, vamos remover várias pessoas de vários grupos em diferentes sites usando o mesmo arquivo CSV.</span><span class="sxs-lookup"><span data-stu-id="bbfef-160">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="bbfef-161">Este é um exemplo de comando:</span><span class="sxs-lookup"><span data-stu-id="bbfef-161">Here is an example command:</span></span>

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="bbfef-162">Gerar relatórios de usuário</span><span class="sxs-lookup"><span data-stu-id="bbfef-162">Generate user reports</span></span>

<span data-ttu-id="bbfef-p114">Você pode querer obter um relatório simples para alguns sites e exibir os usuários destes sites, o seu nível de permissão e outras propriedades. A sintaxe é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="bbfef-p114">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="bbfef-165">Você poderá usar os dados destes três sites e registrá-los em um arquivo de texto na sua unidade local.</span><span class="sxs-lookup"><span data-stu-id="bbfef-165">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="bbfef-166">Observe que o parâmetro –Append agregará novo conteúdo a um arquivo já existente.</span><span class="sxs-lookup"><span data-stu-id="bbfef-166">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="bbfef-167">Por exemplo, vamos executar um relatório nos sites ContosoTest, TeamSite01 e Project01 do locatário Contoso1:</span><span class="sxs-lookup"><span data-stu-id="bbfef-167">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="bbfef-168">Observe que tivemos que alterar apenas a variável **$site** .</span><span class="sxs-lookup"><span data-stu-id="bbfef-168">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="bbfef-169">A variável **$Tenant** mantém seu valor por meio de todas as três execuções do comando.</span><span class="sxs-lookup"><span data-stu-id="bbfef-169">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="bbfef-p117">Mas e se você quiser fazer isso em todos os sites? Você poderá fazer isso sem ter que digitar todos os sites usando este comando:</span><span class="sxs-lookup"><span data-stu-id="bbfef-p117">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="bbfef-172">Este relatório é muito simples, e você pode adicionar mais códigos para criar relatórios ou relatórios que incluem informações mais detalhadas e mais precisas.</span><span class="sxs-lookup"><span data-stu-id="bbfef-172">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="bbfef-173">Mas isso deve dar uma ideia de como usar o Shell de gerenciamento do SharePoint Online para gerenciar usuários no ambiente do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bbfef-173">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="bbfef-174">Confira também</span><span class="sxs-lookup"><span data-stu-id="bbfef-174">See also</span></span>

[<span data-ttu-id="bbfef-175">Conectar ao PowerShell do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bbfef-175">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="bbfef-176">Gerenciar o SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbfef-176">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="bbfef-177">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbfef-177">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="bbfef-178">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbfef-178">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

