---
title: Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
description: 'Resumo: Use o Office 365 PowerShell para criar novos sites do SharePoint Online e, em seguida, adicione usuários e grupos a esses sites.'
ms.openlocfilehash: 1fc9192ed27bfd097ac770b53837fb8ba2eb062d
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004694"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="26155-103">Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="26155-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

<span data-ttu-id="26155-104">Ao usar o Office 365 PowerShell para criar sites do SharePoint Online e adicionar usuários, você pode executar tarefas com rapidez e repetidamente do que no centro de administração do Microsoft 356.</span><span class="sxs-lookup"><span data-stu-id="26155-104">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Microsoft 356 admin center.</span></span> <span data-ttu-id="26155-105">Você também pode executar tarefas que não são possíveis de realizar no centro de administração do Office 356.</span><span class="sxs-lookup"><span data-stu-id="26155-105">You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="26155-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="26155-106">Before you begin</span></span>

<span data-ttu-id="26155-107">Os procedimentos neste tópico exigem que você se conecte ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="26155-107">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="26155-108">Para obter instruções, consulte [conectar-se ao PowerShell do SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="26155-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="26155-109">Etapa 1: criar novos conjuntos de sites usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="26155-109">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="26155-110">Crie vários sites usando o Office 365 PowerShell e um arquivo. csv que você cria usando o código de exemplo fornecido e o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="26155-110">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="26155-111">Para este procedimento, você substituirá as informações do espaço reservado mostradas entre colchetes com suas próprias informações específicas do site e do locatário.</span><span class="sxs-lookup"><span data-stu-id="26155-111">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="26155-112">Esse processo permite que você crie um único arquivo e execute um único comando do Office 365 PowerShell que usa esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="26155-112">This process lets you create a single file and run a single Office 365 PowerShell command that uses that file.</span></span> <span data-ttu-id="26155-113">Isso faz com que as ações sejam refeitas e portáveis e elimina muitas, se não todos os, erros que podem vir da digitação de comandos Long no Shell de gerenciamento do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="26155-113">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="26155-114">Há duas partes nesse procedimento.</span><span class="sxs-lookup"><span data-stu-id="26155-114">There are two parts to this procedure.</span></span> <span data-ttu-id="26155-115">Primeiro, você criará um arquivo. csv e, em seguida, fará referência a esse arquivo. CSV usando o Office 365 PowerShell, que usará seu conteúdo para criar os sites.</span><span class="sxs-lookup"><span data-stu-id="26155-115">First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="26155-116">O cmdlet do Office 365 PowerShell importa o arquivo. csv e o canaliza para um loop dentro das chaves que lê a primeira linha do arquivo como cabeçalhos de coluna.</span><span class="sxs-lookup"><span data-stu-id="26155-116">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers.</span></span> <span data-ttu-id="26155-117">O cmdlet do PowerShell do Office 365, em seguida, itera por meio dos registros restantes, cria um novo conjunto de sites para cada registro e atribui Propriedades do conjunto de sites de acordo com os cabeçalhos da coluna.</span><span class="sxs-lookup"><span data-stu-id="26155-117">The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="26155-118">Criando um arquivo .csv</span><span class="sxs-lookup"><span data-stu-id="26155-118">Create a .csv file</span></span>

1. <span data-ttu-id="26155-119">Abra o bloco de notas e cole o seguinte bloco de texto:</span><span class="sxs-lookup"><span data-stu-id="26155-119">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="26155-120">Onde *locatário* é o nome do seu locatário e *proprietário* é o nome de usuário do usuário em seu locatário para o qual você deseja conceder a função de administrador do conjunto de sites principal.</span><span class="sxs-lookup"><span data-stu-id="26155-120">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="26155-121">(Você pode pressionar CTRL + H ao usar o bloco de notas para substituir em massa mais rápido.)</span><span class="sxs-lookup"><span data-stu-id="26155-121">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="26155-122">Salve o arquivo na área de trabalho como **SiteCollections. csv**.</span><span class="sxs-lookup"><span data-stu-id="26155-122">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="26155-123">Antes de usar este ou qualquer outro arquivo de script. csv ou do Windows PowerShell, é uma boa prática garantir que não haja caracteres estranhos ou não imprimíveis.</span><span class="sxs-lookup"><span data-stu-id="26155-123">Before you use this or any other .csv or Windows PowerShell script file, it's a good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="26155-124">Abra o arquivo no Word, e na faixa de opções, clique no ícone do parágrafo  para mostrar caracteres não imprimíveis.</span><span class="sxs-lookup"><span data-stu-id="26155-124">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="26155-125">Não deve haver caracteres estranhos não imprimíveis.</span><span class="sxs-lookup"><span data-stu-id="26155-125">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="26155-126">Por exemplo, não deve haver marcas do parágrafo no final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="26155-126">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="26155-127">Execute o comando do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="26155-127">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="26155-128">No prompt do Windows PowerShell, digite ou copie e cole o seguinte comando e pressione ENTER:</span><span class="sxs-lookup"><span data-stu-id="26155-128">At the Windows PowerShell prompt, type or copy and paste the following command, and press Enter:</span></span><br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="26155-129">Em que *myalias* é igual ao seu alias de usuário.</span><span class="sxs-lookup"><span data-stu-id="26155-129">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="26155-130">Aguarde até que o prompt do Windows PowerShell reapareça.</span><span class="sxs-lookup"><span data-stu-id="26155-130">Wait for the Windows PowerShell prompt to reappear.</span></span> <span data-ttu-id="26155-131">Pode demorar um minuto ou dois.</span><span class="sxs-lookup"><span data-stu-id="26155-131">It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="26155-132">No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione ENTER:</span><span class="sxs-lookup"><span data-stu-id="26155-132">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="26155-133">Observe os novos conjuntos de sites na lista.</span><span class="sxs-lookup"><span data-stu-id="26155-133">Note the new site collections in the list.</span></span> <span data-ttu-id="26155-134">Usando nosso arquivo CSV de exemplo, você verá os seguintes conjuntos de sites: **TeamSite01**, **Blog01**, **Project01**e **Community01**</span><span class="sxs-lookup"><span data-stu-id="26155-134">Using our example CSV file, you would see the following site collections: **TeamSite01**, **Blog01**, **Project01**, and **Community01**</span></span>

<span data-ttu-id="26155-135">É isso.</span><span class="sxs-lookup"><span data-stu-id="26155-135">That’s it.</span></span> <span data-ttu-id="26155-136">Você criou vários conjuntos de sites usando o arquivo. csv criado e um único comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26155-136">You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell command.</span></span> <span data-ttu-id="26155-137">Agora você está pronto para criar e alocar usuários nestes sites.</span><span class="sxs-lookup"><span data-stu-id="26155-137">You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="26155-138">Etapa 2: Adicionar usuários ou grupos</span><span class="sxs-lookup"><span data-stu-id="26155-138">Step 2: Add users and groups</span></span>

<span data-ttu-id="26155-p109">Agora você criará usuários e irá adicioná-los ao grupo do site. Então você usará um arquivo csv. para fazer o carregamento em massa de novos grupos e usuários.</span><span class="sxs-lookup"><span data-stu-id="26155-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="26155-141">Os seguintes procedimentos continuam a usar os sites de exemplo TeamSite01, Blog01, Project01 e Community01.</span><span class="sxs-lookup"><span data-stu-id="26155-141">The following procedures continue using the example sites TeamSite01, Blog01, Project01, and Community01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="26155-142">Criando arquivos .csv e .ps1</span><span class="sxs-lookup"><span data-stu-id="26155-142">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="26155-143">Abra o bloco de notas e cole o seguinte bloco de texto:</span><span class="sxs-lookup"><span data-stu-id="26155-143">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/><span data-ttu-id="26155-144">Onde *locatário* é igual ao nome do locatário.</span><span class="sxs-lookup"><span data-stu-id="26155-144">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="26155-145">Salve o arquivo em sua área de trabalho como **GroupsAndPermissions. csv**.</span><span class="sxs-lookup"><span data-stu-id="26155-145">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="26155-146">Abra uma nova instância do bloco de notas e cole o seguinte bloco de texto:</span><span class="sxs-lookup"><span data-stu-id="26155-146">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/><span data-ttu-id="26155-147">Onde *locatário* é igual ao nome do locatário e *username* é igual ao nome de usuário de um usuário existente.</span><span class="sxs-lookup"><span data-stu-id="26155-147">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="26155-148">Salve o arquivo na sua área de trabalho como **users. csv**.</span><span class="sxs-lookup"><span data-stu-id="26155-148">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="26155-149">Abra uma nova instância do bloco de notas e cole o seguinte bloco de texto:</span><span class="sxs-lookup"><span data-stu-id="26155-149">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="26155-150">Em que myalias é igual ao nome de usuário do usuário que está conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="26155-150">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="26155-151">Salve o arquivo em sua área de trabalho como **UsersAndGroups. ps1**.</span><span class="sxs-lookup"><span data-stu-id="26155-151">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="26155-152">Este é um script simples do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26155-152">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="26155-153">Agora você está pronto para executar o script UsersAndGroup.ps1 para adicionar usuários e grupos a vários conjuntos de sites.</span><span class="sxs-lookup"><span data-stu-id="26155-153">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="26155-154">Execute o script UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="26155-154">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="26155-155">Retorne ao shell de gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="26155-155">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="26155-156">No prompt do Windows PowerShell, digite ou copie e cole a seguinte linha e pressione ENTER:</span><span class="sxs-lookup"><span data-stu-id="26155-156">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="26155-157">No prompt de confirmação, pressione **s**.</span><span class="sxs-lookup"><span data-stu-id="26155-157">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="26155-158">No prompt do Windows PowerShell, digite ou copie e cole o seguinte e pressione ENTER:</span><span class="sxs-lookup"><span data-stu-id="26155-158">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="26155-159">Em que *myalias* é igual ao nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="26155-159">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="26155-p111">Aguarde a solicitação de retorno do prompt antes de prosseguir. Os grupos aparecerão de acordo com a criação dos mesmos. Então você verá a repetição da lista do grupo de acordo com os usuários que são agregados.</span><span class="sxs-lookup"><span data-stu-id="26155-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="26155-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="26155-163">See also</span></span>

[<span data-ttu-id="26155-164">Conectar ao PowerShell do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="26155-164">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="26155-165">Gerenciar grupos de sites do SharePoint Online Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="26155-165">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="26155-166">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="26155-166">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="26155-167">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="26155-167">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

