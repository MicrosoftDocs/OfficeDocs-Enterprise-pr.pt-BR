---
title: "Configurar grupos e usuários para um ambiente de desenvolvimento e teste de campanha política"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Resumo: Crie assinaturas de avaliação de segurança (EMS) + Office 365 e mobilidade da empresa com usuários e grupos para um ambiente de desenvolvimento e teste de campanha política."
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="7a2c0-103">Configurar grupos e usuários para um ambiente de desenvolvimento e teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="7a2c0-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="7a2c0-104">**Resumo:** Crie assinaturas de avaliação de segurança (EMS) + Office 365 e mobilidade da empresa com usuários e grupos para um ambiente de desenvolvimento e teste de campanha política.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="7a2c0-105">Use as instruções deste artigo para criar um ambiente de desenvolvimento e teste que inclui contas de usuário simplificada e grupos para a solução de [Diretrizes de segurança da Microsoft para campanhas político, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) .</span><span class="sxs-lookup"><span data-stu-id="7a2c0-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="7a2c0-106">Fase 1: Criar seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="7a2c0-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="7a2c0-107">Nesta fase, você deve obter assinaturas de avaliação do Office 365 E5 e mobilidade corporativos + E5 de segurança (EMS) para uma empresa fictícia que representa uma campanha de política.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="7a2c0-108">Primeiro, siga as instruções na **fase 2** do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="7a2c0-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="7a2c0-109">Em seguida, inscreva-se para a assinatura de avaliação do EMS E5 e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="7a2c0-p101">Se necessário, entre no portal do Office 365 com as credenciais da conta de administrador global de sua assinatura de avaliação. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="7a2c0-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="7a2c0-112">Clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="7a2c0-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="7a2c0-113">Na guia do **Centro de administração do Office** em seu navegador, no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="7a2c0-p102">Na página **Serviços de compra** , localize o item de **mobilidade corporativos + E5 de segurança** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="7a2c0-116">Na página **confirmar seu pedido** , clique em **tente agora**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="7a2c0-117">Na página **confirmação de ordem** , clique em **continuar**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="7a2c0-118">Em seguida, habilite a licença do EMS E5 para sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="7a2c0-119">Na guia do **Centro de administração do Office 365** em seu navegador, no painel de navegação esquerdo, clique em **usuários > usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="7a2c0-120">Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="7a2c0-121">No painel de **licenças do produto** , ativar a licença do produto para **mobilidade corporativos + E5 de segurança** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="7a2c0-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="7a2c0-122">Fase 2: Criar e configurar seus grupos do Windows Azure AD (Active Directory)</span><span class="sxs-lookup"><span data-stu-id="7a2c0-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="7a2c0-123">Nesta fase, criar e configurar os grupos do Azure AD para sua campanha.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="7a2c0-124">Primeiro, crie um conjunto de grupos para uma campanha político típica com o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="7a2c0-125">Em uma guia separada no seu navegador, vá para o portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com). Se necessário, entre com as credenciais da conta de administrador global para a sua assinatura de avaliação do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="7a2c0-126">No portal do Azure, clique em **Azure Active Directory > usuários e grupos > todos os grupos**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="7a2c0-127">Execute as seguintes etapas para cada nome de grupo nesta lista:</span><span class="sxs-lookup"><span data-stu-id="7a2c0-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="7a2c0-128">Sênior e à equipe estratégica</span><span class="sxs-lookup"><span data-stu-id="7a2c0-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="7a2c0-129">Equipe de TI</span><span class="sxs-lookup"><span data-stu-id="7a2c0-129">IT staff</span></span>
    
  - <span data-ttu-id="7a2c0-130">Equipe de análise</span><span class="sxs-lookup"><span data-stu-id="7a2c0-130">Analytics staff</span></span>
    
  - <span data-ttu-id="7a2c0-131">Equipe de núcleo regular</span><span class="sxs-lookup"><span data-stu-id="7a2c0-131">Regular core staff</span></span>
    
  - <span data-ttu-id="7a2c0-132">Equipe de operações</span><span class="sxs-lookup"><span data-stu-id="7a2c0-132">Operations staff</span></span>
    
  - <span data-ttu-id="7a2c0-133">Equipe de campo</span><span class="sxs-lookup"><span data-stu-id="7a2c0-133">Field staff</span></span>
    
1. <span data-ttu-id="7a2c0-134">No blade **todos os grupos** , clique em **+ novo grupo**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="7a2c0-135">Digite o nome de grupo da lista em **nome**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="7a2c0-136">Selecione o **usuário dinâmico** na **associação**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="7a2c0-137">Clique em **Sim** para **Habilitar o Office recursos**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="7a2c0-138">Clique em **Add query de dinâmico**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="7a2c0-139">No **Adicionar usuários onde**, selecione o **departamento**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="7a2c0-140">No próximo campo, selecione **é igual a**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="7a2c0-141">No campo próximo, digite o nome de grupo da lista.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="7a2c0-142">Clique em **Add query**e, em seguida, clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="7a2c0-143">Clique em **usuários e grupos - todos os grupos**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="7a2c0-144">Em seguida, configure os grupos para que os membros são automaticamente atribuídos licenças do Office 365 E5 e EMS E5.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="7a2c0-145">No portal do Azure, clique em **Azure Active Directory > licenças > todos os produtos**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="7a2c0-146">Na lista, selecione **Enterprise mobilidade + E5 de segurança** e o **Office 365 Enterprise E5**e, em seguida, clique em **+ atribuir**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="7a2c0-147">Na blade **atribuir licença** , clique em **usuários e grupos**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="7a2c0-148">Na lista de grupos, selecione o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7a2c0-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="7a2c0-149">Equipe de análise</span><span class="sxs-lookup"><span data-stu-id="7a2c0-149">Analytics staff</span></span>
    
  - <span data-ttu-id="7a2c0-150">Equipe de campo</span><span class="sxs-lookup"><span data-stu-id="7a2c0-150">Field staff</span></span>
    
  - <span data-ttu-id="7a2c0-151">Equipe de TI</span><span class="sxs-lookup"><span data-stu-id="7a2c0-151">IT staff</span></span>
    
  - <span data-ttu-id="7a2c0-152">Equipe de operações</span><span class="sxs-lookup"><span data-stu-id="7a2c0-152">Operations staff</span></span>
    
  - <span data-ttu-id="7a2c0-153">Equipe de núcleo regular</span><span class="sxs-lookup"><span data-stu-id="7a2c0-153">Regular core staff</span></span>
    
  - <span data-ttu-id="7a2c0-154">Sênior e à equipe estratégica</span><span class="sxs-lookup"><span data-stu-id="7a2c0-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="7a2c0-155">Clique em **Selecionar**e, em seguida, clique em **atribuir**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="7a2c0-156">Feche a Azure guia portal no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="7a2c0-157">Fase 3: Adicionar suas contas de usuário</span><span class="sxs-lookup"><span data-stu-id="7a2c0-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="7a2c0-158">Nesta fase, você pode adicionar as contas de usuário de exemplo para sua campanha política.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="7a2c0-159">Primeiro, você [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="7a2c0-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="7a2c0-160">Em seguida, preencha o nome da sua organização, seu local e uma senha comum e, em seguida, execute estes comandos no prompt de comando do PowerShell ou ambiente de Script integrado (ISE):</span><span class="sxs-lookup"><span data-stu-id="7a2c0-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="7a2c0-p103">O uso de uma senha comum aqui é para automação e facilidade de configuração para um ambiente de desenvolvimento e teste. Isso não é recomendado para assinaturas de produção. Conforme você entrar com cada um dessas novas contas de usuário, você será solicitado para alterar a senha.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="7a2c0-164">Use estas etapas para verificar se a associação ao grupo dinâmico e licenciamento baseado no grupo estão funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="7a2c0-165">Na guia **Página inicial do Microsoft Office** do seu navegador, clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="7a2c0-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="7a2c0-166">Na guia novo **Centro de administração do Office** do seu navegador, clique em **usuários**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="7a2c0-167">Na lista de usuários, clique em **candidato**.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="7a2c0-168">No painel que lista as propriedades da conta de usuário de **candidato** , verifique se:</span><span class="sxs-lookup"><span data-stu-id="7a2c0-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="7a2c0-169">Ele é um membro do grupo **sênior e à equipe estratégico** (em **associações de grupo**).</span><span class="sxs-lookup"><span data-stu-id="7a2c0-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="7a2c0-170">Ela recebeu as licenças de **mobilidade corporativos + E5 de segurança** e o **Office 365 Enterprise E5** (em **licenças do produto**).</span><span class="sxs-lookup"><span data-stu-id="7a2c0-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="7a2c0-171">Feche o painel de conta de usuário do **candidato** .</span><span class="sxs-lookup"><span data-stu-id="7a2c0-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="7a2c0-172">Valores do registro para referência futura</span><span class="sxs-lookup"><span data-stu-id="7a2c0-172">Record values for future reference</span></span>

<span data-ttu-id="7a2c0-173">Esses valores para trabalhar com o Office 365 e EMS assinaturas de avaliação para este ambiente de desenvolvimento e teste de registro:</span><span class="sxs-lookup"><span data-stu-id="7a2c0-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="7a2c0-174">O nome da sua organização de assinatura de avaliação: _</span><span class="sxs-lookup"><span data-stu-id="7a2c0-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="7a2c0-175">Por exemplo, o nome de domínio de assinatura de avaliação de contoso.onmicrosoft.com, o nome da organização é "contoso".</span><span class="sxs-lookup"><span data-stu-id="7a2c0-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="7a2c0-176">O nome de administrador global do Office 365: ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="7a2c0-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="7a2c0-177">Registre a senha dessa conta e a senha inicial comuns para as outras contas de usuário em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="7a2c0-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="7a2c0-178">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="7a2c0-178">Next step</span></span>

<span data-ttu-id="7a2c0-179">Construa os quatro tipos diferentes de sites de equipe do SharePoint Online neste ambiente de desenvolvimento e teste com [criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="7a2c0-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a2c0-180">See Also</span><span class="sxs-lookup"><span data-stu-id="7a2c0-180">See Also</span></span>

[<span data-ttu-id="7a2c0-181">Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil</span><span class="sxs-lookup"><span data-stu-id="7a2c0-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="7a2c0-182">Criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="7a2c0-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="7a2c0-183">Adoção de nuvem Test Lab Guides (TLGs)</span><span class="sxs-lookup"><span data-stu-id="7a2c0-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="7a2c0-184">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="7a2c0-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




