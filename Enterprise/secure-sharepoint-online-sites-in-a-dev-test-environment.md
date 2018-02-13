---
title: Proteger sites do SharePoint Online em um ambiente de desenvolvimento e teste
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "Resumo: Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento e teste."
ms.openlocfilehash: a0448cdbce570db748f8fcae784fd6f1beefc218
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="04dcd-103">Proteger sites do SharePoint Online em um ambiente de desenvolvimento e teste</span><span class="sxs-lookup"><span data-stu-id="04dcd-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="04dcd-104">**Resumo:** Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="04dcd-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="04dcd-105">Este artigo fornece instruções passo a passo para criar um ambiente de desenvolvimento e teste que inclui os quatro tipos diferentes de sites de equipe do SharePoint Online para a solução de [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md) .</span><span class="sxs-lookup"><span data-stu-id="04dcd-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![Todos os quatro sites de equipe no ambiente de desenvolvimento/teste do SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="04dcd-107">Use esse ambiente de desenvolvimento e teste para experimentar os comportamentos de proteção de informações e ajustar as configurações para suas necessidades específicas antes de implantar o SharePoint Online sites de equipe em produção.</span><span class="sxs-lookup"><span data-stu-id="04dcd-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="04dcd-108">Fase 1: Crie seu ambiente de desenvolvimento e teste</span><span class="sxs-lookup"><span data-stu-id="04dcd-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="04dcd-109">Nesta fase, você deve obter assinaturas de avaliação do Office 365 e mobilidade corporativos + segurança para uma organização a empresa fictícia.</span><span class="sxs-lookup"><span data-stu-id="04dcd-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="04dcd-110">Primeiro, siga as instruções na **fase 2** do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="04dcd-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="04dcd-111">Em seguida, inscreva-se para a assinatura de avaliação do EMS e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="04dcd-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="04dcd-p101">Se necessário, entre no portal do Office 365 com as credenciais da conta de administrador global de sua assinatura de avaliação. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="04dcd-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="04dcd-114">Clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="04dcd-115">Na guia do **Centro de administração do Office** em seu navegador, no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="04dcd-p102">Na página **Serviços de compra** , localize o item de **mobilidade corporativos + E5 de segurança** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="04dcd-118">Na página **confirmar seu pedido** , clique em **tente agora**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="04dcd-119">Na página **confirmação de ordem** , clique em **continuar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="04dcd-120">Em seguida, habilite a mobilidade corporativos + licença E5 de segurança para sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="04dcd-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="04dcd-121">Na guia do **Centro de administração do Office 365** em seu navegador, no painel de navegação esquerdo, clique em **usuários > usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="04dcd-122">Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="04dcd-123">No painel de **licenças do produto** , ativar a licença do produto para **mobilidade corporativos + E5 de segurança** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="04dcd-124">Fase 2: Criar e configurar seus usuários e grupos do Windows Azure AD (Active Directory)</span><span class="sxs-lookup"><span data-stu-id="04dcd-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="04dcd-125">Nesta fase, criar e configurar o Azure AD grupos e usuários para a sua organização a empresa fictícia.</span><span class="sxs-lookup"><span data-stu-id="04dcd-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="04dcd-126">Primeiro, crie um conjunto de grupos de uma organização comum com o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="04dcd-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="04dcd-127">Criar uma guia separada no seu navegador e, em seguida, vá para o portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com). Se necessário, entre com as credenciais da conta de administrador global para a sua assinatura de avaliação do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="04dcd-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="04dcd-128">No portal do Azure, clique em **Azure Active Directory > usuários e grupos > todos os grupos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="04dcd-129">No blade **todos os grupos** , clique em **+ novo grupo**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="04dcd-130">No **grupo** blade:</span><span class="sxs-lookup"><span data-stu-id="04dcd-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="04dcd-131">Tipo **C-Suite** em **nome**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="04dcd-132">Selecione **atribuído** na **associação**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="04dcd-133">Clique em **Sim** para **Habilitar o Office recursos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="04dcd-134">Clique em **criar**e feche o blade de **grupo** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="04dcd-135">Repita as etapas 3 a 5 para os nomes de grupo a seguir:</span><span class="sxs-lookup"><span data-stu-id="04dcd-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="04dcd-136">Equipe de TI</span><span class="sxs-lookup"><span data-stu-id="04dcd-136">IT staff</span></span>
    
  - <span data-ttu-id="04dcd-137">Equipe de pesquisa</span><span class="sxs-lookup"><span data-stu-id="04dcd-137">Research staff</span></span>
    
  - <span data-ttu-id="04dcd-138">Equipe regular</span><span class="sxs-lookup"><span data-stu-id="04dcd-138">Regular staff</span></span>
    
  - <span data-ttu-id="04dcd-139">Equipe de marketing</span><span class="sxs-lookup"><span data-stu-id="04dcd-139">Marketing staff</span></span>
    
  - <span data-ttu-id="04dcd-140">Equipe de vendas</span><span class="sxs-lookup"><span data-stu-id="04dcd-140">Sales staff</span></span>
    
7. <span data-ttu-id="04dcd-141">Lembre na guia portal Azure abrir seu navegador.</span><span class="sxs-lookup"><span data-stu-id="04dcd-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="04dcd-142">Em seguida, você configurar o licenciamento automático para que os membros dos grupos são automaticamente atribuídos licenças para suas assinaturas do Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="04dcd-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="04dcd-143">No portal do Azure, clique em **Azure Active Directory > licenças > todos os produtos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="04dcd-144">Na lista, selecione **Enterprise mobilidade + E5 de segurança** e o **Office 365 Enterprise E5**e, em seguida, clique em **atribuir**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="04dcd-145">Na blade **atribuir licença** , clique em **usuários e grupos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="04dcd-146">Na lista de grupos, selecione o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04dcd-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="04dcd-147">C-Suite</span><span class="sxs-lookup"><span data-stu-id="04dcd-147">C-Suite</span></span>
    
  - <span data-ttu-id="04dcd-148">Equipe de TI</span><span class="sxs-lookup"><span data-stu-id="04dcd-148">IT staff</span></span>
    
  - <span data-ttu-id="04dcd-149">Equipe de pesquisa</span><span class="sxs-lookup"><span data-stu-id="04dcd-149">Research staff</span></span>
    
  - <span data-ttu-id="04dcd-150">Equipe regular</span><span class="sxs-lookup"><span data-stu-id="04dcd-150">Regular staff</span></span>
    
  - <span data-ttu-id="04dcd-151">Equipe de marketing</span><span class="sxs-lookup"><span data-stu-id="04dcd-151">Marketing staff</span></span>
    
  - <span data-ttu-id="04dcd-152">Equipe de vendas</span><span class="sxs-lookup"><span data-stu-id="04dcd-152">Sales staff</span></span>
    
5. <span data-ttu-id="04dcd-153">Clique em **Selecionar**e, em seguida, clique em **atribuir**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="04dcd-154">Feche a Azure guia portal no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="04dcd-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="04dcd-155">Em seguida, você [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="04dcd-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="04dcd-156">Preencha o nome da sua organização, seu local e uma senha comum e, em seguida, execute estes comandos no prompt de comando do PowerShell ou ambiente de Script integrado (ISE) para criar contas de usuário e adicioná-los em seus grupos:</span><span class="sxs-lookup"><span data-stu-id="04dcd-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
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
> <span data-ttu-id="04dcd-p103">O uso de uma senha comum aqui é para automação e facilidade de configuração para um ambiente de desenvolvimento e teste. Isso não é recomendado para assinaturas de produção.</span><span class="sxs-lookup"><span data-stu-id="04dcd-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="04dcd-159">Use estas etapas para verificar se o licenciamento do grupo está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="04dcd-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="04dcd-160">Na guia **Página inicial do Microsoft Office** do seu navegador, clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="04dcd-161">Na guia novo **Centro de administração do Office** do seu navegador, clique em **usuários**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="04dcd-162">Na lista de usuários, clique em **CEO**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="04dcd-163">No painel que lista as propriedades da conta de usuário do **CEO** , verifique se que ele foi atribuído as licenças de **mobilidade corporativos + E5 de segurança** e o **Office 365 Enterprise E5** (em **licenças do produto**).</span><span class="sxs-lookup"><span data-stu-id="04dcd-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="04dcd-164">Fase 3: Criar rótulos do Office 365</span><span class="sxs-lookup"><span data-stu-id="04dcd-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="04dcd-165">Nesta fase, você deve criar os rótulos para os diferentes níveis de segurança para pastas de documentos do site de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="04dcd-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="04dcd-p104">Se necessário, use uma instância particular do seu navegador da Internet e entrar no portal do Office 365 com a conta de administrador global de sua assinatura de avaliação do Office 365 E5. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="04dcd-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="04dcd-168">Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="04dcd-169">Na guia novo **Centro de administração do Office** do seu navegador, clique em **centrais de Admin > segurança &amp; conformidade**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="04dcd-170">Do novo **Home - segurança &amp; conformidade** guia do navegador, clique em **classificações > rótulos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="04dcd-171">Da **Home > rótulos** painel, clique em **criar um rótulo**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="04dcd-172">No painel de **nome de seu rótulo** , digite **Internos de públicos**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="04dcd-173">No painel de **configurações de rótulo** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="04dcd-174">No painel **Revise suas configurações** , clique em **criar este rótulo**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="04dcd-175">Repita as etapas 5 a 8 para esses rótulos adicionais:</span><span class="sxs-lookup"><span data-stu-id="04dcd-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="04dcd-176">Particular</span><span class="sxs-lookup"><span data-stu-id="04dcd-176">Private</span></span>
    
  - <span data-ttu-id="04dcd-177">Confidenciais</span><span class="sxs-lookup"><span data-stu-id="04dcd-177">Sensitive</span></span>
    
  - <span data-ttu-id="04dcd-178">Altamente confidenciais</span><span class="sxs-lookup"><span data-stu-id="04dcd-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="04dcd-179">Da **Home > rótulos** painel, clique em **Publicar rótulos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="04dcd-180">No painel **Choose rótulos para publicar** , clique em **rótulos de escolher para publicar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="04dcd-181">No painel **Choose rótulos** , clique em **Adicionar** e selecione todas as quatro rótulos.</span><span class="sxs-lookup"><span data-stu-id="04dcd-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="04dcd-182">Clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="04dcd-183">No painel **Choose rótulos para publicar** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="04dcd-184">No painel **Choose locais** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="04dcd-185">No painel de **sua política de nome** , digite o **exemplo de organização** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="04dcd-186">No painel **Revise suas configurações** , clique em **rótulos de publicar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="04dcd-187">Fase 4: Criar seus sites de equipe do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="04dcd-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="04dcd-188">Nesta fase, criar e configurar os quatro tipos de sites de equipe do SharePoint Online para a sua organização de exemplo.</span><span class="sxs-lookup"><span data-stu-id="04dcd-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="04dcd-189">Site de equipe ampla de organização</span><span class="sxs-lookup"><span data-stu-id="04dcd-189">Organization wide team site</span></span>

<span data-ttu-id="04dcd-190">Para criar um site de equipe ' baseline público do SharePoint Online, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04dcd-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="04dcd-p105">Se necessário, use um navegador no computador local e entrar no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="04dcd-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="04dcd-193">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="04dcd-194">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="04dcd-195">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="04dcd-196">Em **nome do Site**, digite **toda a organização**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="04dcd-197">Na **Descrição do site de equipe**, digite o **site do SharePoint para toda a organização**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="04dcd-198">Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="04dcd-199">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="04dcd-200">Em seguida, configure a pasta de documentos do site organização ampla de equipe para o rótulo de público interno.</span><span class="sxs-lookup"><span data-stu-id="04dcd-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="04dcd-201">Na guia **Home toda a organização** do seu navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="04dcd-202">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="04dcd-203">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="04dcd-204">Em **Configurações se aplicam rótulo**, selecione **Interno pública**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="04dcd-205">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="04dcd-205">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para site de equipe do SharePoint Online público para toda a Organização.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="04dcd-207">Site de equipe do projeto 1</span><span class="sxs-lookup"><span data-stu-id="04dcd-207">Project 1 team site</span></span>

<span data-ttu-id="04dcd-208">Para criar um site de equipe baseline privado SharePoint Online para um projeto dentro da organização, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04dcd-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="04dcd-p106">Se necessário, use um navegador no computador local e entrar no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="04dcd-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="04dcd-211">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="04dcd-212">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="04dcd-213">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="04dcd-214">Em **nome do Site**, digite **1 do Project**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="04dcd-215">Na **Descrição do site de equipe,** digite o **site do SharePoint para o Project 1**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="04dcd-216">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="04dcd-217">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="04dcd-218">Em seguida, configure a pasta de documentos do site da equipe de projeto 1 para o rótulo de privada.</span><span class="sxs-lookup"><span data-stu-id="04dcd-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="04dcd-219">Na guia **Project 1-Home** do seu navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="04dcd-220">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="04dcd-221">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="04dcd-222">Em **Configurações se aplicam rótulo**, selecione **privada**e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="04dcd-223">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="04dcd-223">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para o site de equipe do SharePoint Online privado do Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="04dcd-225">Site da equipe de campanhas de marketing</span><span class="sxs-lookup"><span data-stu-id="04dcd-225">Marketing campaigns team site</span></span>

<span data-ttu-id="04dcd-226">Para criar um nível confidenciais isolado team site do SharePoint Online para recursos de campanhas de marketing, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04dcd-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="04dcd-p107">Usando um navegador no computador local, entre no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="04dcd-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="04dcd-229">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="04dcd-230">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="04dcd-231">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="04dcd-232">Em **nome do site de equipe**, digite **campanhas de Marketing**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="04dcd-233">Na **Descrição do site de equipe**, digite o **site do SharePoint para recursos de campanha de marketing (confidenciais)**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="04dcd-234">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="04dcd-235">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="04dcd-236">Na guia **campanhas de Marketing** novo em seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="04dcd-237">No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="04dcd-238">Na guia **permissões** nova no seu navegador, clique em **Configurações de solicitação de acesso**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="04dcd-239">Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque as caixas de seleção **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** , digite **ITAdmin1 @**\<sua nome da organização >**. onmicrosoft.com** em **Enviar todas as solicitações de acesso**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="04dcd-240">Na lista, clique em **membros de campanhas de Marketing** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="04dcd-241">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="04dcd-242">Na caixa de diálogo **compartilhar** , digite **a equipe de Marketing**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="04dcd-243">Repita as etapas 14 e 15 para a conta de usuário **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="04dcd-244">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="04dcd-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="04dcd-245">Na lista, clique em **campanhas de Marketing proprietários** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="04dcd-246">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="04dcd-247">Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="04dcd-248">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="04dcd-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="04dcd-249">Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Home de campanhas de Marketing** no seu navegador e, em seguida, feche o painel de **permissões do Site** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="04dcd-250">Estes são os resultados da configuração das permissões:</span><span class="sxs-lookup"><span data-stu-id="04dcd-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="04dcd-251">O grupo do SharePoint **Membros de campanhas de Marketing** contém apenas o grupo de **campanhas de Marketing** (que contém a conta de usuário do administrador global), o grupo de **equipe de Marketing** (que contém o usuário Marketing1 e Marketing2 contas) e a conta de usuário **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="04dcd-252">O grupo de **Proprietários de campanhas de Marketing** SharePoint contém apenas o grupo de **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="04dcd-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="04dcd-253">Grupo de **Campanhas de Marketing - visitantes** do SharePoint não contém grupos ou contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="04dcd-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="04dcd-254">Membros não podem modificar permissões de nível de site (isso só pode ser feito por membros do grupo **Proprietários de campanhas de Marketing** ).</span><span class="sxs-lookup"><span data-stu-id="04dcd-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="04dcd-255">Outras contas de usuário não podem acessar o site ou seus recursos, mas podem solicitar acesso ao site, qual enviará um email para a caixa de correio de conta de usuário ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="04dcd-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="04dcd-256">Em seguida, configure a pasta de documentos do site da equipe de campanhas de Marketing, rótulo confidencial de.</span><span class="sxs-lookup"><span data-stu-id="04dcd-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="04dcd-257">Na guia **Home de campanhas de Marketing** do seu navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="04dcd-258">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="04dcd-259">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="04dcd-260">Em **Configurações se aplicam rótulo**, selecione **confidenciais**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="04dcd-261">Em seguida, configure uma política de prevenção (DLP) de perda de dados que notifica os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo confidencial, que inclui o site de campanhas de Marketing, fora da organização.</span><span class="sxs-lookup"><span data-stu-id="04dcd-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="04dcd-262">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="04dcd-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="04dcd-263">No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="04dcd-264">No painel de **prevenção de perda de dados** , clique em **+ para criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="04dcd-265">No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="04dcd-266">No painel de **sua política de nome** , digite os **sites de equipe do SharePoint Online rótulo confidenciais** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="04dcd-267">No painel **Choose locais** , clique em **Deixe-me escolher locais específicos**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="04dcd-268">Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="04dcd-269">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="04dcd-270">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="04dcd-271">No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="04dcd-272">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="04dcd-273">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="04dcd-274">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, clique em **Personalizar a dica e email**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="04dcd-275">No painel de **dicas de política personalizar e notificações por email** , clique em **Personalizar o texto da dica de política**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="04dcd-276">Na caixa de texto, digite ou cole o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="04dcd-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="04dcd-p108">Para compartilhar com um usuário fora da organização, baixe o arquivo e, em seguida, abri-lo. Clique em arquivo, em seguida, proteger documento e, em seguida, criptografar com senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="04dcd-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="04dcd-280">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="04dcd-281">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, desmarque a caixa de seleção **bloquear pessoas de compartilhamento e restringir o acesso ao conteúdo compartilhado** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="04dcd-282">No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="04dcd-283">No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="04dcd-284">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="04dcd-284">Here is your resulting configuration.</span></span>
  
![Proteção de nível confidencial para campanhas de Marketing isoladas do site de equipe do SharePoint Online.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="04dcd-286">Site de equipe de estratégia de empresa</span><span class="sxs-lookup"><span data-stu-id="04dcd-286">Company strategy team site</span></span>

<span data-ttu-id="04dcd-287">Para criar um site de equipe do SharePoint Online isolado no nível altamente confidencial para recursos da empresa estratégica dos principais executivos da organização, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04dcd-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="04dcd-p109">Se necessário, use um navegador no computador local e entrar no portal do Office 365 usando sua conta de administrador global. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="04dcd-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="04dcd-290">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="04dcd-291">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="04dcd-292">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="04dcd-293">Em **nome do site de equipe**, digite a **estratégia de empresa**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="04dcd-294">Na **Descrição do site de equipe**, digite o **site do SharePoint para a estratégia da empresa (altamente confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="04dcd-295">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="04dcd-296">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="04dcd-297">Na guia nova **estratégia de empresa** no seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="04dcd-298">No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="04dcd-299">Na guia **permissões** nova no seu navegador, clique em **Configurações de solicitação de acesso**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="04dcd-300">Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** (de forma que todas as três caixas de seleção estiver desmarcadas) e clique em ** Okey**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="04dcd-301">Na lista, clique em **membros de estratégia de empresa** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="04dcd-302">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="04dcd-303">Na caixa de diálogo **compartilhar** , digite **C-Suite**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="04dcd-304">Na lista, clique em **estratégia de empresa proprietários** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="04dcd-305">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="04dcd-306">Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="04dcd-307">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="04dcd-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="04dcd-308">Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Empresa estratégia-Home** no seu navegador e, em seguida, feche o painel de **permissões do Site** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="04dcd-309">Estes são os resultados da configuração das permissões:</span><span class="sxs-lookup"><span data-stu-id="04dcd-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="04dcd-310">O grupo do SharePoint de **Estratégia-membros da empresa** contém apenas o grupo de **Pacote do C** (que contém apenas as contas de usuário CEO, CIO e diretor financeiro) e do grupo de **estratégia da empresa** (que contém a conta de usuário administrador global).</span><span class="sxs-lookup"><span data-stu-id="04dcd-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="04dcd-311">O grupo do SharePoint de **Proprietários de estratégia de empresa** contém somente o grupo da **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="04dcd-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="04dcd-312">Grupo do SharePoint **Empresa estratégia-visitantes** não contém grupos ou contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="04dcd-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="04dcd-313">Membros não podem modificar permissões de nível de site (isso só pode ser feito por membros do grupo **Proprietários de estratégia de empresa** ).</span><span class="sxs-lookup"><span data-stu-id="04dcd-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="04dcd-p110">Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar acesso ao site. Permissões adicionais para o site devem ser feitas pelo administrador global ou por um membro do grupo **Proprietários de estratégia de empresa** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="04dcd-316">Em seguida, configure a pasta de documentos do site de equipe de estratégia da empresa para o rótulo de altamente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="04dcd-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="04dcd-317">Na guia **Empresa estratégia-página inicial** do navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="04dcd-318">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="04dcd-319">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="04dcd-320">Em **Configurações se aplicam rótulo**, selecione **Altamente confidenciais**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="04dcd-321">Em seguida, configure uma política de DLP que bloqueia usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo altamente confidenciais, que inclui o site da estratégia de empresa, fora da organização.</span><span class="sxs-lookup"><span data-stu-id="04dcd-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="04dcd-p111">Se necessário, use um navegador no computador local e entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="04dcd-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="04dcd-324">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="04dcd-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="04dcd-325">No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="04dcd-326">No painel de **prevenção de perda de dados** , clique em **+ para criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="04dcd-327">No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="04dcd-328">No painel de **sua política de nome** , digite **altamente confidenciais sites de equipe do SharePoint Online do rótulo** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="04dcd-329">No painel **Choose locais** , clique em **Deixe-me escolher locais específicos**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="04dcd-330">Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="04dcd-331">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="04dcd-332">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="04dcd-333">No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **Altamente confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="04dcd-334">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="04dcd-335">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="04dcd-336">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, clique em **Personalizar a dica e email**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="04dcd-337">No painel de **dicas de política personalizar e notificações por email** , clique em **Personalizar o texto da dica de política**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="04dcd-338">Na caixa de texto, digite ou cole o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="04dcd-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="04dcd-p112">Para compartilhar com um usuário fora da organização, baixe o arquivo e, em seguida, abri-lo. Clique em arquivo, em seguida, proteger documento e, em seguida, criptografar com senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="04dcd-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="04dcd-342">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="04dcd-343">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, selecione **exigir uma justificativa comercial para substituir**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="04dcd-344">No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="04dcd-345">No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="04dcd-346">Em seguida, siga as instruções em [Ativar o Azure RMS com o Centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="04dcd-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="04dcd-347">Em seguida, configure a proteção de informações do Windows Azure com uma nova política de escopo e sub-recurso rótulo para proteção e permissões com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="04dcd-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="04dcd-p113">Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="04dcd-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="04dcd-350">Em uma guia separada do navegador, vá para o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="04dcd-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="04dcd-351">Se essa for a primeira vez que você está configurando a proteção de informações do Windows Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="04dcd-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="04dcd-352">No painel de lista, clique em **mais de serviços**, digite as **informações**e clique em **Proteção de informações do Windows Azure**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="04dcd-353">No blade **proteção das informações do Azure** , clique em **escopo políticas > + Adicionar uma nova diretiva**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="04dcd-354">Digite **CompanyStrategy** no **nome de política** e **rótulo para documentos no site da equipe de estratégia de empresa** em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="04dcd-355">Clique em **Selecione quais usuários ou grupos fazer essa política > grupos de usuários/**e selecione **C-Suite**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="04dcd-356">Clique em **Selecione > Okey**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="04dcd-357">Para o rótulo de **Altamente confidenciais** , clique nas reticências (…) e, em seguida, clique em **Adicionar um rótulo de subsites**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="04dcd-358">Digite um nome para o rótulo de subsites em **nome** e uma descrição do rótulo em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="04dcd-359">Em **definir permissões para documentos e emails contendo esse rótulo**, clique em **proteger**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="04dcd-360">Na seção **proteção** , clique em **Windows Azure (chave de nuvem)**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="04dcd-361">No blade **proteção** , em **configurações de proteção**, clique em **+ Adicionar permissões**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="04dcd-362">No blade **Adicionar permissões** , em **especificar usuários e grupos**, clique em **+ Procurar no diretório**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="04dcd-363">No painel **AAD usuários e grupos** , selecione o **Pacote de C**e, em seguida, clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="04dcd-364">Em **Escolha as permissões a predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo**e **Encaminhar** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="04dcd-365">Clique duas vezes em **Okey** .</span><span class="sxs-lookup"><span data-stu-id="04dcd-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="04dcd-366">No **rótulo sub-recurso** blade, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="04dcd-367">Fechar o novo escopo blade de política.</span><span class="sxs-lookup"><span data-stu-id="04dcd-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="04dcd-368">No blade **proteção de informações do Windows Azure - políticas com escopo** , clique em **Publicar**e, em seguida, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="04dcd-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="04dcd-369">Para proteger um documento com esse novo rótulo e de proteção de informações do Windows Azure, você deve [instalar o cliente de proteção de informações do Windows Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em uma máquina de teste, instalar o Office do portal do Office 365 e entrar do Microsoft Word com uma conta no ** C-Suite** grupo de sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="04dcd-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="04dcd-370">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="04dcd-370">Here is your resulting configuration.</span></span>
  
![Proteção com alto nível de confidencialidade para o site de equipe isolado do SharePoint Online de estratégia da Empresa.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="04dcd-372">Agora você está pronto para criar documentos em sites essas quatro e testar acessá-los com várias contas de usuário em sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="04dcd-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="04dcd-373">Aqui está a configuração geral para todos os quatro sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="04dcd-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Todos os quatro sites de equipe no ambiente de desenvolvimento/teste do SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="04dcd-375">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="04dcd-375">Next step</span></span>

<span data-ttu-id="04dcd-376">Quando estiver pronto para a implantação de produção de sites do SharePoint Online seguros, consulte [arquivos e sites do SharePoint Online segura](secure-sharepoint-online-sites-and-files.md) para obter informações detalhadas e links para artigos passo a passo de implantação.</span><span class="sxs-lookup"><span data-stu-id="04dcd-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="04dcd-377">Veja também</span><span class="sxs-lookup"><span data-stu-id="04dcd-377">See Also</span></span>

[<span data-ttu-id="04dcd-378">Proteja arquivos e sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="04dcd-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="04dcd-379">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="04dcd-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="04dcd-380">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="04dcd-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="04dcd-381">Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil</span><span class="sxs-lookup"><span data-stu-id="04dcd-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




