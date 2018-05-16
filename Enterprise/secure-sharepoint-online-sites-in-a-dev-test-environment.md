---
title: Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Resumo: Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento e teste.'
ms.openlocfilehash: 004a1614330f220b31be640cd822d9fdcbb49b99
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="e5c57-103">Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="e5c57-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="e5c57-104">**Resumo:** Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="e5c57-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="e5c57-105">Este artigo fornece instruções passo a passo para criar um ambiente de desenvolvimento e teste que inclui os quatro tipos diferentes de sites de equipe do SharePoint Online para a solução de [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md) .</span><span class="sxs-lookup"><span data-stu-id="e5c57-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![Todos os quatro sites de equipe no ambiente de desenvolvimento/teste do SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="e5c57-107">Use este ambiente de desenvolvimento/teste para experimentar com os comportamentos de proteção de informações e ajustar as configurações para suas necessidades específicas antes de implantar sites de equipe do SharePoint Online na produção.</span><span class="sxs-lookup"><span data-stu-id="e5c57-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="e5c57-108">Fase 1: Criar seu ambiente de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="e5c57-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="e5c57-109">Nesta fase, você deve obter assinaturas de avaliação do Office 365 e do Enterprise Mobility + Security para uma organização fictícia.</span><span class="sxs-lookup"><span data-stu-id="e5c57-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="e5c57-110">Primeiro, siga as instruções na **Fase 2** do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="e5c57-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e5c57-111">Em seguida, inscreva-se para a assinatura de avaliação do EMS e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e5c57-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="e5c57-p101">Se necessário, entre no portal do Office 365 com as credenciais da conta de administrador global de sua assinatura de avaliação. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e5c57-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e5c57-114">Clique no bloco de **Administração**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e5c57-115">Na guia **Centro de Administração do Office** no navegador, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="e5c57-p102">Na página **Serviços de compra** , localize o item de **mobilidade corporativos + E5 de segurança** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="e5c57-118">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="e5c57-119">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="e5c57-120">Em seguida, habilite a licença do Enterprise Mobility + Security E5 para sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="e5c57-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="e5c57-121">Na guia **Centro de Administração do Office 365** no navegador, no painel de navegação esquerdo, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="e5c57-122">Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="e5c57-123">No painel de **licenças do produto** , ativar a licença do produto para **mobilidade corporativos + E5 de segurança** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="e5c57-124">Fase 2: Criar e configurar seus grupos e usuários do Azure AD (Active Directory)</span><span class="sxs-lookup"><span data-stu-id="e5c57-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="e5c57-125">Nesta fase, você cria e configura os usuários e grupos do Azure AD para sua organização fictícia.</span><span class="sxs-lookup"><span data-stu-id="e5c57-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="e5c57-126">Primeiro, crie um conjunto de grupos para uma organização típica com o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="e5c57-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="e5c57-127">Criar uma guia separada no seu navegador e, em seguida, vá para o portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com). Se necessário, entre com as credenciais da conta de administrador global para a sua assinatura de avaliação do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="e5c57-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="e5c57-128">No portal do Azure, clique em **Azure Active Directory > grupos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-128">In the Azure portal, click **Azure Active Directory > Groups**.</span></span>
    
3. <span data-ttu-id="e5c57-129">No blade **grupos - todos os grupos** , clique em **+ novo grupo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-129">On the **Groups - All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="e5c57-130">Na folha **Grupo**:</span><span class="sxs-lookup"><span data-stu-id="e5c57-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="e5c57-131">Selecione **Office 365** no **tipo de grupo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-131">Select **Office 365** in **Group type**.</span></span>
    
  - <span data-ttu-id="e5c57-132">Digite **Pacote C** em **Nome**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-132">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="e5c57-133">Selecione **atribuído** no **tipo de associação**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-133">Select **Assigned** in **Membership type**.</span></span>
      
5. <span data-ttu-id="e5c57-134">Clique em **Criar**e, em seguida, feche a folha **Grupo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="e5c57-135">Repita as etapas 3 a 5 para os seguintes nomes de grupo:</span><span class="sxs-lookup"><span data-stu-id="e5c57-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="e5c57-136">Equipe de TI</span><span class="sxs-lookup"><span data-stu-id="e5c57-136">IT staff</span></span>
    
  - <span data-ttu-id="e5c57-137">Equipe de pesquisa</span><span class="sxs-lookup"><span data-stu-id="e5c57-137">Research staff</span></span>
    
  - <span data-ttu-id="e5c57-138">Equipe regular</span><span class="sxs-lookup"><span data-stu-id="e5c57-138">Regular staff</span></span>
    
  - <span data-ttu-id="e5c57-139">Equipe de marketing</span><span class="sxs-lookup"><span data-stu-id="e5c57-139">Marketing staff</span></span>
    
  - <span data-ttu-id="e5c57-140">Equipe de vendas</span><span class="sxs-lookup"><span data-stu-id="e5c57-140">Sales staff</span></span>
    
7. <span data-ttu-id="e5c57-141">Feche a guia do portal do Azure no navegador.</span><span class="sxs-lookup"><span data-stu-id="e5c57-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="e5c57-142">Em seguida, você configurar o licenciamento automático para que os membros dos grupos são automaticamente atribuídos licenças para suas assinaturas do Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="e5c57-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="e5c57-143">No Portal do Azure, clique em **Azure Active Directory > Licenças > Todos os produtos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="e5c57-144">Na lista, selecione **Enterprise mobilidade + E5 de segurança** e o **Office 365 Enterprise E5**e, em seguida, clique em **atribuir**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="e5c57-145">Na folha **Atribuir licença**, clique em **Usuários e grupos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="e5c57-146">Na lista de grupos, selecione o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5c57-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="e5c57-147">Pacote C</span><span class="sxs-lookup"><span data-stu-id="e5c57-147">C-Suite</span></span>
    
  - <span data-ttu-id="e5c57-148">Equipe de TI</span><span class="sxs-lookup"><span data-stu-id="e5c57-148">IT staff</span></span>
    
  - <span data-ttu-id="e5c57-149">Equipe de pesquisa</span><span class="sxs-lookup"><span data-stu-id="e5c57-149">Research staff</span></span>
    
  - <span data-ttu-id="e5c57-150">Equipe regular</span><span class="sxs-lookup"><span data-stu-id="e5c57-150">Regular staff</span></span>
    
  - <span data-ttu-id="e5c57-151">Equipe de marketing</span><span class="sxs-lookup"><span data-stu-id="e5c57-151">Marketing staff</span></span>
    
  - <span data-ttu-id="e5c57-152">Equipe de vendas</span><span class="sxs-lookup"><span data-stu-id="e5c57-152">Sales staff</span></span>
    
5. <span data-ttu-id="e5c57-153">Clique em **Selecionar**e, em seguida, clique em **atribuir**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="e5c57-154">Feche a guia do Portal do Azure no navegador.</span><span class="sxs-lookup"><span data-stu-id="e5c57-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="e5c57-155">Em seguida, você deve se [Conectar ao módulo PowerShell do Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="e5c57-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="e5c57-156">Preencha o nome da sua organização, seu local e uma senha comum e, em seguida, execute estes comandos no prompt de comando do PowerShell ou ambiente de Script integrado (ISE) para criar contas de usuário e adicioná-los em seus grupos:</span><span class="sxs-lookup"><span data-stu-id="e5c57-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> <span data-ttu-id="e5c57-p103">O uso de uma senha comum aqui é para a automação e facilidade de configuração para um ambiente de desenvolvimento/teste. Isso nunca é recomendado assinaturas de produção.</span><span class="sxs-lookup"><span data-stu-id="e5c57-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="e5c57-159">Use estas etapas para verificar se o licenciamento do grupo está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="e5c57-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="e5c57-160">Na guia **Microsoft Office Home** do navegador, clique no bloco **Administração**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="e5c57-161">Na nova guia **Centro de Administração do Office** do navegador, clique em **Usuários**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="e5c57-162">Na lista de usuários, clique em **CEO**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="e5c57-163">No painel que lista as propriedades da conta de usuário **CEO**, verifique se ele recebeu a atribuição das licenças **Enterprise Mobility + Security E5** e **Office 365 Enterprise E5** (em **Licenças de produto**).</span><span class="sxs-lookup"><span data-stu-id="e5c57-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="e5c57-164">Fase 3: Criar rótulos do Office 365</span><span class="sxs-lookup"><span data-stu-id="e5c57-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="e5c57-165">Nesta fase, você deve criar os rótulos para os diferentes níveis de segurança para as pastas e documentos do site da equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e5c57-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="e5c57-p104">Se necessário, use uma instância particular do seu navegador da Internet e entrar no portal do Office 365 com a conta de administrador global de sua assinatura de avaliação do Office 365 E5. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e5c57-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e5c57-168">Na guia **Microsoft Office Home**, clique no bloco **Administração**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e5c57-169">Na guia novo **Centro de administração do Office** do seu navegador, clique em **centrais de Admin > segurança &amp; conformidade**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="e5c57-170">Do novo **Home - segurança &amp; conformidade** guia do navegador, clique em **classificações > rótulos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="e5c57-171">No painel **Início > Rótulos**, clique em **Criar um rótulo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="e5c57-172">No painel de **nome de seu rótulo** , digite **Internos de públicos**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="e5c57-173">No painel **Configurações do Rótulo**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="e5c57-174">No painel **Revise suas configurações** , clique em **criar este rótulo**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="e5c57-175">Repita as etapas de 5 a 8 para os rótulos adicionais:</span><span class="sxs-lookup"><span data-stu-id="e5c57-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="e5c57-176">Private</span><span class="sxs-lookup"><span data-stu-id="e5c57-176">Private</span></span>
    
  - <span data-ttu-id="e5c57-177">Confidencial</span><span class="sxs-lookup"><span data-stu-id="e5c57-177">Sensitive</span></span>
    
  - <span data-ttu-id="e5c57-178">Altamente Confidencial</span><span class="sxs-lookup"><span data-stu-id="e5c57-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="e5c57-179">No painel **Início > Rótulos**, clique em **Publicar rótulos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="e5c57-180">No painel **Escolher rótulos para publicar**, clique em **Escolher rótulos para publicar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="e5c57-181">No painel **Escolher rótulos**, clique em **Adicionar** e selecione todos os quatro rótulos.</span><span class="sxs-lookup"><span data-stu-id="e5c57-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="e5c57-182">Clique em **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="e5c57-183">No painel **Escolher rótulos para publicar**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="e5c57-184">No painel **Escolher locais**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="e5c57-185">No painel de **sua política de nome** , digite o **exemplo de organização** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="e5c57-186">No painel **Revise suas configurações** , clique em **rótulos de publicar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="e5c57-187">Fase 4: Criar seus sites de equipe do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e5c57-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="e5c57-188">Nesta fase, você cria e configura os quatro tipos de sites de equipe do SharePoint Online para sua organização de exemplo.</span><span class="sxs-lookup"><span data-stu-id="e5c57-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="e5c57-189">Site de equipe de toda a organização</span><span class="sxs-lookup"><span data-stu-id="e5c57-189">Organization wide team site</span></span>

<span data-ttu-id="e5c57-190">Para criar um site de equipe do SharePoint Online público de linha de base, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5c57-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="e5c57-p105">Se necessário, use um navegador no computador local e entre no Portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e5c57-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e5c57-193">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="e5c57-194">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="e5c57-195">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="e5c57-196">Em **Nome do site**, digite **Toda a organização**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="e5c57-197">Na **Descrição do site de equipe**, digite **Site do SharePoint para toda a organização**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="e5c57-198">Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e5c57-199">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="e5c57-200">Em seguida, configure a pasta de documentos do site de equipe Toda a organização para o rótulo Público Interno.</span><span class="sxs-lookup"><span data-stu-id="e5c57-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="e5c57-201">Na guia **Home toda a organização** do seu navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="e5c57-202">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="e5c57-203">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="e5c57-204">Em **Configurações se aplicam rótulo**, selecione **Interno pública**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="e5c57-205">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="e5c57-205">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para site de equipe do SharePoint Online público para toda a Organização.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="e5c57-207">Site de equipe do projeto 1</span><span class="sxs-lookup"><span data-stu-id="e5c57-207">Project 1 team site</span></span>

<span data-ttu-id="e5c57-208">Para criar um site de equipe do SharePoint Online privado de linha de base para um projeto dentro da organização, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5c57-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="e5c57-p106">Se necessário, use um navegador no computador local e entre no Portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e5c57-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e5c57-211">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="e5c57-212">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="e5c57-213">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="e5c57-214">Em **Nome do site**, digite **Projeto 1**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="e5c57-215">Na **Descrição do site de equipe,** digite o **site do SharePoint para o Project 1**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="e5c57-216">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e5c57-217">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="e5c57-218">Em seguida, configure a pasta de documentos do site de equipe Projeto 1 para o rótulo Privado.</span><span class="sxs-lookup"><span data-stu-id="e5c57-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="e5c57-219">Na guia **Projeto 1 – Início** do navegador, clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="e5c57-220">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="e5c57-221">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="e5c57-222">Em **Configurações se aplicam rótulo**, selecione **privada**e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="e5c57-223">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="e5c57-223">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para o site de equipe do SharePoint Online privado do Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="e5c57-225">Site de equipe de campanhas de marketing</span><span class="sxs-lookup"><span data-stu-id="e5c57-225">Marketing campaigns team site</span></span>

<span data-ttu-id="e5c57-226">Para criar um site de equipe do SharePoint Online isolado de nível confidencial para recursos de campanha de marketing, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5c57-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="e5c57-p107">Usando um navegador no computador local, entre no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e5c57-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e5c57-229">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="e5c57-230">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="e5c57-231">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="e5c57-232">Em **Nome do site de equipe**, digite **Campanhas de marketing**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="e5c57-233">Em **Descrição do site de equipe**, digite **Site do SharePoint para recursos de campanha de marketing (confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="e5c57-234">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e5c57-235">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="e5c57-236">Na guia **campanhas de Marketing** novo em seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="e5c57-237">No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="e5c57-238">Na nova guia **Permissões** no navegador, clique em **Configurações de Solicitação de Acesso**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="e5c57-239">Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque as caixas de seleção **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** , digite **ITAdmin1 @**\<sua nome da organização >**. onmicrosoft.com** em **Enviar todas as solicitações de acesso**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="e5c57-240">Clique em **Membros de campanhas de marketing** na lista.</span><span class="sxs-lookup"><span data-stu-id="e5c57-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="e5c57-241">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="e5c57-242">Na caixa de diálogo **compartilhar** , digite **a equipe de Marketing**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="e5c57-243">Repita as etapas 14 e 15 para a conta de usuário **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="e5c57-244">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="e5c57-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="e5c57-245">Na lista, clique em **campanhas de Marketing proprietários** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="e5c57-246">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="e5c57-247">Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="e5c57-248">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="e5c57-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="e5c57-249">Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Home de campanhas de Marketing** no seu navegador e, em seguida, feche o painel de **permissões do Site** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="e5c57-250">Aqui estão os resultados da configuração de permissões:</span><span class="sxs-lookup"><span data-stu-id="e5c57-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="e5c57-251">O grupo do SharePoint **Campanhas de marketing – membros** contém apenas o grupo **Campanhas de marketing** (que contém a conta de usuário de administrador global), o grupo **Equipe de marketing** (que contém as conas de usuário Marketing1 e Marketing2) e a conta de usuário **Researcher1**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="e5c57-252">O grupo do SharePoint **Campanhas de marketing – Proprietários** contém apenas o grupo **Equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="e5c57-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="e5c57-253">O grupo do SharePoint **Campanhas de marketing – Visitantes** não contém grupos ou contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="e5c57-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="e5c57-254">Os membros não podem modificar permissões de nível de site (isso pode ser feito apenas por membros do grupo **Campanhas de marketing – Proprietários**).</span><span class="sxs-lookup"><span data-stu-id="e5c57-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="e5c57-255">Outras contas de usuário não podem acessar o site ou seus recursos, mas podem solicitar acesso ao site, qual enviará um email para a caixa de correio de conta de usuário ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="e5c57-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="e5c57-256">Em seguida, configure a pasta de documentos do site de equipe Campanhas de marketing para o rótulo Confidencial.</span><span class="sxs-lookup"><span data-stu-id="e5c57-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="e5c57-257">Na guia **Campanhas de marketing – Início** do navegador, clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="e5c57-258">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="e5c57-259">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="e5c57-260">Em **Configurações se aplicam rótulo**, selecione **confidenciais**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="e5c57-261">Em seguida, configure uma política de DLP (prevenção de perda de dados) que notifica os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo Confidencial, que inclui o site de Campanhas de marketing, fora da organização.</span><span class="sxs-lookup"><span data-stu-id="e5c57-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="e5c57-262">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="e5c57-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="e5c57-263">No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="e5c57-264">No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="e5c57-265">No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="e5c57-266">No painel de **sua política de nome** , digite os **sites de equipe do SharePoint Online rótulo confidenciais** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="e5c57-267">No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="e5c57-268">Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e5c57-269">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="e5c57-270">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="e5c57-271">No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="e5c57-272">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="e5c57-273">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="e5c57-274">No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="e5c57-275">No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="e5c57-276">Na caixa de texto, digite ou cole o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5c57-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="e5c57-p108">Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="e5c57-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="e5c57-280">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="e5c57-281">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, desmarque a caixa de seleção **bloquear pessoas de compartilhamento e restringir o acesso ao conteúdo compartilhado** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="e5c57-282">No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="e5c57-283">No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="e5c57-284">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="e5c57-284">Here is your resulting configuration.</span></span>
  
![Proteção de nível confidencial para campanhas de Marketing isoladas do site de equipe do SharePoint Online.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="e5c57-286">Site de equipe de estratégia de empresa</span><span class="sxs-lookup"><span data-stu-id="e5c57-286">Company strategy team site</span></span>

<span data-ttu-id="e5c57-287">Para criar um site de equipe do SharePoint Online isolado no nível altamente confidencial para recursos corporativos estratégicos dos diretores da organização, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5c57-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="e5c57-p109">Se necessário, use um navegador no computador local e entre no Portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e5c57-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e5c57-290">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="e5c57-291">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="e5c57-292">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="e5c57-293">Em **Nome do site da equipe**, digite **Estratégia da empresa**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="e5c57-294">Em **Descrição do site da equipe**, digite **Site do SharePoint para estratégia da empresa (altamente confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="e5c57-295">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e5c57-296">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="e5c57-297">Na guia nova **estratégia de empresa** no seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="e5c57-298">No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="e5c57-299">Na nova guia **Permissões** no navegador, clique em **Configurações de Solicitação de Acesso**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="e5c57-300">Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** (de forma que todas as três caixas de seleção estiver desmarcadas) e clique em ** Okey**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="e5c57-301">Na lista, clique em **membros de estratégia de empresa** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="e5c57-302">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="e5c57-303">Na caixa de diálogo **compartilhar** , digite **C-Suite**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="e5c57-304">Na lista, clique em **estratégia de empresa proprietários** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="e5c57-305">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="e5c57-306">Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="e5c57-307">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="e5c57-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="e5c57-308">Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Empresa estratégia-Home** no seu navegador e, em seguida, feche o painel de **permissões do Site** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="e5c57-309">Aqui estão os resultados da configuração de permissões:</span><span class="sxs-lookup"><span data-stu-id="e5c57-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="e5c57-310">O grupo do SharePoint **Estratégia da empresa – Membros** contém apenas o grupo **Pacote C** (que contém apenas as contas de usuário do CEO, do CFO e do CIO) e o grupo **Estratégia da empresa** (que contém apenas a conta de usuário de administrador global).</span><span class="sxs-lookup"><span data-stu-id="e5c57-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="e5c57-311">O grupo do SharePoint de **Proprietários de estratégia de empresa** contém somente o grupo da **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="e5c57-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="e5c57-312">O grupo do SharePoint **Estratégia da empresa – Visitantes** não contém grupos ou contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="e5c57-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="e5c57-313">Os membros não podem modificar permissões de nível de site (isso pode ser feito apenas por membros do grupo **Estratégia da empresa – Proprietários**).</span><span class="sxs-lookup"><span data-stu-id="e5c57-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="e5c57-p110">Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar o acesso ao site. As permissões adicionais para o site devem ser feias pelo administrador global ou por um membro do grupo **Estratégia da empresa – Proprietários**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="e5c57-316">Em seguida, configure a pasta de documentos do site da equipe de estratégia da empresa para o rótulo Altamente Confidencial.</span><span class="sxs-lookup"><span data-stu-id="e5c57-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="e5c57-317">Na guia **Estratégia da empresa – Início** do navegador, clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="e5c57-318">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="e5c57-319">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="e5c57-320">Em **Configurações se aplicam rótulo**, selecione **Altamente confidenciais**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="e5c57-321">Em seguida, configure uma política de DLP que bloqueia os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo Altamente Confidencial, que inclui o site de Estratégia da empresa, fora da organização.</span><span class="sxs-lookup"><span data-stu-id="e5c57-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="e5c57-p111">Se necessário, use um navegador no computador local e entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e5c57-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e5c57-324">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="e5c57-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="e5c57-325">No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="e5c57-326">No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="e5c57-327">No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="e5c57-328">No painel de **sua política de nome** , digite **altamente confidenciais sites de equipe do SharePoint Online do rótulo** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="e5c57-329">No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e5c57-330">Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e5c57-331">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="e5c57-332">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="e5c57-333">No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **Altamente confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="e5c57-334">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="e5c57-335">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="e5c57-336">No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="e5c57-337">No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="e5c57-338">Na caixa de texto, digite ou cole o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5c57-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="e5c57-p112">Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="e5c57-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="e5c57-342">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="e5c57-343">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, selecione **exigir uma justificativa comercial para substituir**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="e5c57-344">No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="e5c57-345">No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="e5c57-346">Em seguida, siga as instruções em [Ativar o Azure RMS com o centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="e5c57-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="e5c57-347">Depois, configure a Proteção de Informações do Azure com uma nova política e sub-rótulo em escopo para proteção e permissões com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="e5c57-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="e5c57-p113">Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e5c57-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e5c57-350">Em uma guia separada do navegador, vá para o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="e5c57-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="e5c57-351">Se essa for a primeira vez que você está configurando a proteção de informações do Windows Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="e5c57-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="e5c57-352">No painel de lista, clique em **todos os serviços**, digite as **informações**e, clique em **Proteção de informações do Windows Azure**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-352">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="e5c57-353">No blade **proteção das informações do Azure** , clique em **escopo políticas > + Adicionar uma nova diretiva**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="e5c57-354">Digite **CompanyStrategy** em **Nome da política** e **Rótulo para documentos no site da equipe de estratégia da Empresa** em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="e5c57-355">Clique em **Selecionar usuários ou grupos que obtêm essa política > Usuário/Grupos**e, em seguida, selecione **Pacote C**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="e5c57-356">Clique em **Selecionar > OK**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="e5c57-357">Para o rótulo **Altamente Confidencial**, clique nas reticências (...) e, em seguida, clique em **Adicionar um sub-rótulo**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="e5c57-358">Digite um nome para o subrótulo em **Nome** e uma descrição do rótulo em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="e5c57-359">Em **Definir permissões para documentos e emails que contenham este rótulo**, clique em **Proteger**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="e5c57-360">Na seção **Proteção**, clique em **Azure (chave de nuvem)**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="e5c57-361">Na folha **Proteção**, em **Configurações de proteção**, clique em **+ Adicionar permissões**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="e5c57-362">Na folha **Adicionar permissões**, em **Especificar usuários e grupos**, clique em **+ Procurar no diretório**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="e5c57-363">No painel **AAD usuários e grupos** , selecione o **Pacote de C**e, em seguida, clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="e5c57-364">Em **Escolha as permissões a predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo**e **Encaminhar** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="e5c57-365">Clique duas vezes em **Okey** .</span><span class="sxs-lookup"><span data-stu-id="e5c57-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="e5c57-366">Na folha **Rótulo**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="e5c57-367">Feche a nova folha de política em escopo.</span><span class="sxs-lookup"><span data-stu-id="e5c57-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="e5c57-368">No blade **proteção de informações do Windows Azure - políticas com escopo** , clique em **Publicar**e, em seguida, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="e5c57-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="e5c57-369">Para proteger um documento com esse novo rótulo e de proteção de informações do Windows Azure, você deve [instalar o cliente de proteção de informações do Windows Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em uma máquina de teste, instalar o Office do portal do Office 365 e entrar do Microsoft Word com uma conta no ** C-Suite** grupo de sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="e5c57-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="e5c57-370">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="e5c57-370">Here is your resulting configuration.</span></span>
  
![Proteção com alto nível de confidencialidade para o site de equipe isolado do SharePoint Online de estratégia da Empresa.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="e5c57-372">Agora você está pronto para criar documentos nestes quatro sites e testar o acesso a eles com várias contas de usuário em sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="e5c57-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="e5c57-373">Aqui está a configuração geral para todos os quatro sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e5c57-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Todos os quatro sites de equipe no ambiente de desenvolvimento/teste do SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="e5c57-375">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="e5c57-375">Next step</span></span>

<span data-ttu-id="e5c57-376">Quando você estiver pronto para a implantação dos sites do SharePoint Online seguros na produção, consulte [Arquivos e sites do SharePoint Online seguros](secure-sharepoint-online-sites-and-files.md) para obter informações detalhadas e links para os artigos de implantação passo a passo.</span><span class="sxs-lookup"><span data-stu-id="e5c57-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e5c57-377">Confira também</span><span class="sxs-lookup"><span data-stu-id="e5c57-377">See Also</span></span>

[<span data-ttu-id="e5c57-378">Proteger sites e arquivos do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e5c57-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="e5c57-379">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="e5c57-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="e5c57-380">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="e5c57-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="e5c57-381">Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile</span><span class="sxs-lookup"><span data-stu-id="e5c57-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




