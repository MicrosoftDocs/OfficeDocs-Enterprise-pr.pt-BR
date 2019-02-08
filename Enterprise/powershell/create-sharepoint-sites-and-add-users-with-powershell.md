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
ms.openlocfilehash: 61b9338469ed8d01abc76edbf14ed448c3ca00d3
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897164"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="36b97-103">Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36b97-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="36b97-104">**Resumo:** Use o Office 365 PowerShell para criar novos sites do SharePoint Online e, em seguida, adicionar usuários e grupos para esses sites.</span><span class="sxs-lookup"><span data-stu-id="36b97-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="36b97-p101">Quando você usa o Office 365 PowerShell para criar sites do SharePoint Online e adicionar usuários, você pode rapidamente e repetidamente executar tarefas muito mais rápidas do que você pode fazer no Centro de administração do Office 356. Você também pode executar as tarefas que não serão possíveis executar no Centro de administração do Office 356.</span><span class="sxs-lookup"><span data-stu-id="36b97-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="36b97-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="36b97-107">Before you begin</span></span>

<span data-ttu-id="36b97-p102">Os procedimentos neste tópico exigem que você se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="36b97-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="36b97-110">Etapa 1: Criar novos conjuntos de sites usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="36b97-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="36b97-p103">Crie vários sites usando o Office 365 PowerShell e um arquivo. csv que você criar usando o código de exemplo fornecido e o bloco de notas. Esse procedimento, você substituirá as informações de espaço reservado mostradas na colchetes com suas próprias informações específicas do site e do inquilino. Esse processo permite criar um único arquivo e execute um comando do Office 365 PowerShell único que usa esse arquivo. Isso faz com que as ações realizadas repetível e portátil e elimina muitos, se não todos os erros que podem ser provenientes de comandos longos digitados no SharePoint Online Management Shell. Há duas partes para esse procedimento. Primeiro, você vai criar um arquivo. csv e, em seguida, você vai fazer referência a esse arquivo. csv usando o Office 365 PowerShell, que usará o seu conteúdo para criar os sites.</span><span class="sxs-lookup"><span data-stu-id="36b97-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process lets you create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="36b97-p104">O cmdlet do PowerShell do Office 365 importa o arquivo. csv e canaliza para um loop dentro de chaves que lê a primeira linha do arquivo como cabeçalhos de coluna. Em seguida, o cmdlet do PowerShell do Office 365 percorre os registros restantes, cria um novo conjunto de sites para cada registro e atribui propriedades do conjunto de sites de acordo com os cabeçalhos de coluna.</span><span class="sxs-lookup"><span data-stu-id="36b97-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="36b97-119">Criando um arquivo .csv</span><span class="sxs-lookup"><span data-stu-id="36b97-119">Create a .csv file</span></span>

1. <span data-ttu-id="36b97-120">Abra o bloco de notas e cole o seguinte bloco de texto:</span><span class="sxs-lookup"><span data-stu-id="36b97-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="36b97-121">Onde o *locatário* é o nome do seu locatário e *proprietário* é o nome de usuário do usuário do seu locatário aos quais você deseja conceder o papel de administrador do conjunto de sites primário.</span><span class="sxs-lookup"><span data-stu-id="36b97-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="36b97-122">(Você pode pressionar Ctrl + H ao usar o bloco de notas para em massa substituir mais rápido).</span><span class="sxs-lookup"><span data-stu-id="36b97-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="36b97-123">Salve o arquivo no seu desktop como **Sitecollections**.</span><span class="sxs-lookup"><span data-stu-id="36b97-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="36b97-p105">Antes de usar esta ou qualquer outro. csv ou arquivo de script do Windows PowerShell, é uma boa prática para certificar-se de que não há nenhum caractere incorretas ou não-imprimível. Abra o arquivo no Word e, na faixa de opções, clique no ícone de parágrafo para mostrar os caracteres não imprimíveis. Não deve haver nenhum caracteres não-imprimíveis não essenciais. Por exemplo, deve haver sem marcas de parágrafo além daquela final no final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="36b97-p105">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="36b97-128">Execute o comando do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="36b97-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="36b97-129">No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione Enter:</span><span class="sxs-lookup"><span data-stu-id="36b97-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="36b97-130">Onde *MyAlias* é igual ao seu nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="36b97-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="36b97-p106">Aguarde o prompt do Windows PowerShell reaparecem. Ela pode levar um minuto ou dois.</span><span class="sxs-lookup"><span data-stu-id="36b97-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="36b97-133">No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione Enter:</span><span class="sxs-lookup"><span data-stu-id="36b97-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="36b97-p107">Observe os novos conjuntos de sites na lista. Você deverá ver os seguintes conjuntos de sites: **contosotest**, **TeamSite01**, **Blog01**e **Project01**</span><span class="sxs-lookup"><span data-stu-id="36b97-p107">Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="36b97-p108">É isso. Você criou vários conjuntos de sites usando o arquivo. csv que você criou e um único cmdlet do Windows PowerShell. Agora você está pronto para criar e atribuir usuários a esses sites.</span><span class="sxs-lookup"><span data-stu-id="36b97-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="36b97-139">Etapa 2: Adicionar usuários ou grupos</span><span class="sxs-lookup"><span data-stu-id="36b97-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="36b97-p109">Agora você criará usuários e irá adicioná-los ao grupo do site. Então você usará um arquivo csv. para fazer o carregamento em massa de novos grupos e usuários.</span><span class="sxs-lookup"><span data-stu-id="36b97-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="36b97-142">Os procedimentos a seguir indicam que você criou com sucesso os conjuntos de sites contosotest, TeamSite01, Blog01, e Project01.</span><span class="sxs-lookup"><span data-stu-id="36b97-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="36b97-143">Criando arquivos .csv e .ps1</span><span class="sxs-lookup"><span data-stu-id="36b97-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="36b97-144">Abra o bloco de notas e cole o seguinte bloco de texto:</span><span class="sxs-lookup"><span data-stu-id="36b97-144">Open Notepad, and paste the following text block into it:</span></span><br/>
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
<br/><span data-ttu-id="36b97-145">Onde *inquilino* é igual ao nome do seu locatário.</span><span class="sxs-lookup"><span data-stu-id="36b97-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="36b97-146">Salve o arquivo seu desktop como **GroupsandPermissions**.</span><span class="sxs-lookup"><span data-stu-id="36b97-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="36b97-147">Abra uma nova instância do bloco de notas e cole o seguinte bloco de texto:</span><span class="sxs-lookup"><span data-stu-id="36b97-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="36b97-148">Onde *inquilino* é igual ao nome do seu locatário e *username* é igual ao nome de usuário de um usuário existente.</span><span class="sxs-lookup"><span data-stu-id="36b97-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="36b97-149">Salve o arquivo seu desktop como **Users**.</span><span class="sxs-lookup"><span data-stu-id="36b97-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="36b97-150">Abra uma nova instância do bloco de notas e cole o seguinte bloco de texto:</span><span class="sxs-lookup"><span data-stu-id="36b97-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="36b97-151">Onde o MyAlias é igual ao nome de usuário do usuário que está conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="36b97-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="36b97-p110">Salve o arquivo em sua área de trabalho como **UsersAndGroups.ps1**. Este é um simple script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36b97-p110">Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="36b97-154">Agora você está pronto para executar o script UsersAndGroup.ps1 para adicionar usuários e grupos a vários conjuntos de sites.</span><span class="sxs-lookup"><span data-stu-id="36b97-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="36b97-155">Execute o script UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="36b97-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="36b97-156">Retorne ao shell de gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="36b97-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="36b97-157">No prompt do Windows PowerShell, digite ou copie e cole o seguinte cmdlet e pressione Enter:</span><span class="sxs-lookup"><span data-stu-id="36b97-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="36b97-158">No prompt de confirmação, clique em **Y**.</span><span class="sxs-lookup"><span data-stu-id="36b97-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="36b97-159">No prompt do Windows PowerShell, tipo ou copiar e colar o seguinte cmdlet e pressione insira:</span><span class="sxs-lookup"><span data-stu-id="36b97-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="36b97-160">Onde *MyAlias* é igual a seu nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="36b97-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="36b97-p111">Aguarde a solicitação de retorno do prompt antes de prosseguir. Os grupos aparecerão de acordo com a criação dos mesmos. Então você verá a repetição da lista do grupo de acordo com os usuários que são agregados.</span><span class="sxs-lookup"><span data-stu-id="36b97-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="36b97-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="36b97-164">See also</span></span>

[<span data-ttu-id="36b97-165">Conectar ao PowerShell do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="36b97-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="36b97-166">Gerenciar grupos de sites do SharePoint Online do Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36b97-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="36b97-167">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36b97-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="36b97-168">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36b97-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

