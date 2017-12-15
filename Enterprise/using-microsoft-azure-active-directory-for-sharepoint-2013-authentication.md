---
title: "Usando o Microsoft Azure Active Directory para autenticação do SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "Resumo: Saiba como usar o serviço de controle de acesso do Windows Azure para autenticar os usuários do SharePoint Server 2013 com o Windows Azure Active Directory."
ms.openlocfilehash: 85db8376aeb06ef6f291b563410c991ea24351d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a><span data-ttu-id="2a618-103">Usando o Microsoft Azure Active Directory para autenticação do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="2a618-103">Using Microsoft Azure Active Directory for SharePoint 2013 authentication</span></span>

 <span data-ttu-id="2a618-104">**Resumo:** Saiba como usar o serviço de controle de acesso do Windows Azure para autenticar os usuários do SharePoint Server 2013 com o Windows Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2a618-104">**Summary:** Learn how to use the Azure Access Control Service to authenticate your SharePoint Server 2013 users with Azure Active Directory.</span></span>
  
<span data-ttu-id="2a618-p101">Pode ser mais fácil gerenciar seus usuários, autenticando-los com provedores de identidade diferente. Considere como pode ser prático para usar um provedor de identidade que você confia, mas gerencia a outra pessoa. Por exemplo, você poderia ter um tipo de autenticação para usuários que acessam o SharePoint Server 2013 na nuvem e outro para usuários do SharePoint 2013 no seu ambiente local. O serviço de controle de acesso do Windows Azure possibilita a essas escolhas.</span><span class="sxs-lookup"><span data-stu-id="2a618-p101">It can be easier to manage your users by authenticating them with different identity providers. Consider how convenient it can be to use an identity provider that you trust, but someone else manages. For example, you could have one type of authentication for users who access SharePoint Server 2013 in the cloud and another for SharePoint 2013 users in your on-premises environment. The Azure Access Control Service makes these choices possible.</span></span> 
  
<span data-ttu-id="2a618-p102">Este artigo explica como você pode usar o serviço de controle de acesso do Windows Azure para autenticar os usuários do SharePoint 2013 com o Azure AD, em vez de seu local no Active Directory. Nesta configuração, o Azure AD se torna um provedor de identidade confiável para o SharePoint 2013. Essa configuração adiciona um método de autenticação de usuário que é separado da autenticação do Active Directory usada pela instalação do SharePoint 2013 em si. Para se beneficiar deste artigo, você deve estar familiarizado com WS-Federation. Para obter mais informações, consulte [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span><span class="sxs-lookup"><span data-stu-id="2a618-p102">This article explains how you can use the Azure Access Control Service to authenticate your SharePoint 2013 users with Azure AD, instead of your on-premises Active Directory. In this configuration, Azure AD becomes a trusted identity provider for SharePoint 2013. This configuration adds a user authentication method that is separate from Active Directory authentication used by the SharePoint 2013 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>
  
<span data-ttu-id="2a618-114">A figura a seguir mostra como funciona a autenticação para usuários do SharePoint 2013 nessa configuração.</span><span class="sxs-lookup"><span data-stu-id="2a618-114">The following figure shows how authentication works for SharePoint 2013 users in this configuration.</span></span>
  
![Usuários autenticados com o Azure Active Directory](images/SP_AzureAD.png)
  
<span data-ttu-id="2a618-116">O exemplo usado neste artigo é fornecido pelo Pedro Evans, Microsoft Architect para o Centro de excelência do Azure.</span><span class="sxs-lookup"><span data-stu-id="2a618-116">The example used in this article is provided by Kirk Evans, Microsoft Architect for the Azure Center of Excellence.</span></span> 
  
<span data-ttu-id="2a618-117">Para obter informações sobre a acessibilidade do SharePoint 2013, consulte [acessibilidade do SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span><span class="sxs-lookup"><span data-stu-id="2a618-117">For information about SharePoint 2013 accessibility, see [Accessibility for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>
  
## <a name="configuration-overview"></a><span data-ttu-id="2a618-118">Visão geral da configuração</span><span class="sxs-lookup"><span data-stu-id="2a618-118">Configuration overview</span></span>

<span data-ttu-id="2a618-119">Siga estas etapas gerais para configurar seu ambiente para usar o Windows Azure AD como um provedor de identidade do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="2a618-119">Follow these general steps to set up your environment to use Azure AD as a SharePoint 2013 identity provider.</span></span>
  
1. <span data-ttu-id="2a618-120">Criar um novo inquilino do Azure AD e o namespace.</span><span class="sxs-lookup"><span data-stu-id="2a618-120">Create a new Azure AD tenant and namespace.</span></span>
    
2. <span data-ttu-id="2a618-121">Adicione um provedor de identidade do WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="2a618-121">Add a WS-Federation identity provider.</span></span>
    
3. <span data-ttu-id="2a618-122">Adicione o SharePoint como um aplicativo confiável de terceiros.</span><span class="sxs-lookup"><span data-stu-id="2a618-122">Add SharePoint as a relying party application.</span></span>
    
4. <span data-ttu-id="2a618-123">Crie um certificado autoassinado a ser usada para SSL.</span><span class="sxs-lookup"><span data-stu-id="2a618-123">Create a self-signed certificate to use for SSL.</span></span>
    
5. <span data-ttu-id="2a618-124">Crie um grupo de regra para autenticação baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="2a618-124">Create a rule group for claims-based authentication.</span></span>
    
6. <span data-ttu-id="2a618-125">Configure o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="2a618-125">Configure the X.509 certificate.</span></span>
    
7. <span data-ttu-id="2a618-126">Crie um mapeamento de declaração.</span><span class="sxs-lookup"><span data-stu-id="2a618-126">Create a claim mapping.</span></span>
    
8. <span data-ttu-id="2a618-127">Configure o SharePoint para o novo provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="2a618-127">Configure SharePoint for the new identity provider.</span></span>
    
9. <span data-ttu-id="2a618-128">Defina as permissões.</span><span class="sxs-lookup"><span data-stu-id="2a618-128">Set the permissions.</span></span>
    
10. <span data-ttu-id="2a618-129">Verifique se o novo provedor.</span><span class="sxs-lookup"><span data-stu-id="2a618-129">Verify the new provider.</span></span>
    
## <a name="create-azure-ad-tenant-and-namespace"></a><span data-ttu-id="2a618-130">Crie o namespace e locatário do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2a618-130">Create Azure AD tenant and namespace</span></span>

<span data-ttu-id="2a618-p103">Use as etapas a seguir para criar um novo inquilino do Azure AD e um namespace associado. Neste exemplo, usamos o namespace "blueskyabove".</span><span class="sxs-lookup"><span data-stu-id="2a618-p103">Use the following steps to create a new Azure AD tenant and an associated namespace. In this example, we use the namespace "blueskyabove."</span></span> 
  
1. <span data-ttu-id="2a618-133">No Portal de gerenciamento do Windows Azure, clique em **Active Directory**e, em seguida, crie um novo inquilino do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2a618-133">In the Azure Management Portal, click **Active Directory**, and then create a new Azure AD tenant.</span></span>
    
2. <span data-ttu-id="2a618-134">Clique em **Namespaces de controle de acesso**e criar um novo namespace.</span><span class="sxs-lookup"><span data-stu-id="2a618-134">Click **Access Control Namespaces**, and create a new namespace.</span></span> 
    
3. <span data-ttu-id="2a618-p104">Na barra de ferramentas inferior, clique em **Gerenciar** . Isso deve abrir este local, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span><span class="sxs-lookup"><span data-stu-id="2a618-p104">Click **Manage** on the bottom bar. This should open this location, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span></span>
    
4. <span data-ttu-id="2a618-p105">Abra o Windows PowerShell. Use o Microsoft Online Services Module for Windows PowerShell, que é um pré-requisito para instalar os cmdlets do Windows Azure para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a618-p105">Open Windows PowerShell. Use the Microsoft Online Services Module for Windows PowerShell, which is a prerequisite for installing the Azure for Windows PowerShell cmdlets.</span></span>
    
5. <span data-ttu-id="2a618-139">No prompt de comando do Windows PowerShell, digite o comando: `Connect-Msolservice`e digite suas credenciais.</span><span class="sxs-lookup"><span data-stu-id="2a618-139">From the Windows PowerShell command prompt, type the command:  `Connect-Msolservice`, and then type your credentials.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="2a618-140">Para obter informações adicionais sobre como usar os cmdlets do Windows Azure para o Windows PowerShell, consulte [Gerenciar o Azure AD usando o Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span><span class="sxs-lookup"><span data-stu-id="2a618-140">For additional information about how to use Azure for Windows PowerShell cmdlets, see [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span></span> 
  
6. <span data-ttu-id="2a618-141">Em um prompt de comando do Windows PowerShell, digite os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="2a618-141">From a Windows PowerShell command prompt, type the following commands:</span></span>
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    <span data-ttu-id="2a618-142">A figura a seguir ilustra o resultado de saída.</span><span class="sxs-lookup"><span data-stu-id="2a618-142">The following figure illustrates the output result.</span></span>
    
     ![Criando Nomes de Entidade de Serviço](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a><span data-ttu-id="2a618-144">Adicionar um provedor de identidade do WS-Federation ao namespace</span><span class="sxs-lookup"><span data-stu-id="2a618-144">Add a WS-Federation identity provider to the namespace</span></span>

<span data-ttu-id="2a618-145">Use as etapas a seguir para adicionar um novo provedor de identidade do WS-Federation ao namespace blueskyabove.</span><span class="sxs-lookup"><span data-stu-id="2a618-145">Use the following steps to add a new WS-Federation identity provider to the blueskyabove namespace.</span></span>
  
1. <span data-ttu-id="2a618-146">Do portal de gerenciamento do Azure, vá para o **Active Directory** > **Namespaces de controle de acesso**, clique em **criar uma nova instância**e, em seguida, clique em **Gerenciar**.</span><span class="sxs-lookup"><span data-stu-id="2a618-146">From the Azure management portal, go to **Active Directory** > **Access Control Namespaces**, click **Create a new instance**, and then click **Manage**.</span></span>
    
2. <span data-ttu-id="2a618-147">No portal do controle de acesso do Windows Azure, clique em **Provedores de identidade** > **Add**, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-147">From the Azure Access Control portal, click **Identity Providers** > **Add**, as illustrated in the following figure.</span></span>
    
     ![Caixa de diálogo Provedores de Identidade no Azure](images/Identity.jpg)
  
3. <span data-ttu-id="2a618-149">Clique em **provedor de identidade do WS-Federation**, conforme ilustrado na figura a seguir e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="2a618-149">Click **WS-Federation identity provider**, as illustrated in the following figure, and then click **Next**.</span></span>
    
     ![As configurações em Adicionar Provedor de Identidade](images/AddIdentity.jpg)
  
4. <span data-ttu-id="2a618-p106">Preencher o texto do link logon e o nome de exibição e, em seguida, clique em **Salvar**. Para a URL de metadados do WS-Federation, digite https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. A figura a seguir ilustra a configuração.</span><span class="sxs-lookup"><span data-stu-id="2a618-p106">Fill out the display name and logon link text, and then click **Save**. For the WS-Federation metadata URL, type https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. The following figure illustrates the setting.</span></span>
    
     ![O provedor de identidade de federação](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a><span data-ttu-id="2a618-155">Adicionar SharePoint como um aplicativo confiável de terceiros</span><span class="sxs-lookup"><span data-stu-id="2a618-155">Add SharePoint as a relying party application</span></span>

<span data-ttu-id="2a618-156">Use as etapas a seguir para adicionar o SharePoint como um aplicativo confiável de terceiros.</span><span class="sxs-lookup"><span data-stu-id="2a618-156">Use the following steps to add SharePoint as a relying party application.</span></span>
  
<span data-ttu-id="2a618-157">Para obter informações adicionais sobre as configurações do aplicativo de terceira parte confiável, consulte [Terceira aplicativos de terceiros](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span><span class="sxs-lookup"><span data-stu-id="2a618-157">For additional information about relying party application settings, see [Relying Party Applications](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span></span>
  
1. <span data-ttu-id="2a618-158">Do portal do controle de acesso do Windows Azure, clique em **aplicativos de terceiros de confiança**e clique em **Adicionar**, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-158">From the Azure Access Control portal, click **Relying party applications**, and then click **Add**, as illustrated in the following figure.</span></span>
    
     ![As configurações de terceira parte confiável aplicativo](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a><span data-ttu-id="2a618-160">Criar um certificado autoassinado a ser usada para SSL</span><span class="sxs-lookup"><span data-stu-id="2a618-160">Create a self-signed certificate to use for SSL</span></span>

<span data-ttu-id="2a618-161">Use as etapas a seguir para criar um certificado autoassinado, de novo a ser usado para comunicações seguras via SSL.</span><span class="sxs-lookup"><span data-stu-id="2a618-161">Use the following steps to create a new, self-signed certificate to use for secure communications over SSL.</span></span>
  
1. <span data-ttu-id="2a618-162">Estenda o aplicativo web para usar a mesma URL como PublishingSite, mas usar SSL com a porta 443, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-162">Extend the web application to use the same URL as PublishingSite, but use SSL with port 443, as illustrated in the following figure.</span></span>
    
     ![As configurações para estender o aplicativo](images/ExtendWebApp.jpg)
  
2. <span data-ttu-id="2a618-164">No Gerenciador do IIS, clique duas vezes em **Certificados de servidor**.</span><span class="sxs-lookup"><span data-stu-id="2a618-164">In IIS Manager, double-click **Server Certificates**.</span></span>
    
3. <span data-ttu-id="2a618-p107">No painel **ações** , clique em **Criar certificado autoassinado**. Digite um nome amigável do certificado na caixa **especificar um nome amigável do certificado** e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="2a618-p107">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the **Specify a friendly name for the certificate** box, and then click **OK**.</span></span>
    
4. <span data-ttu-id="2a618-167">Na caixa de diálogo **Editar associação de Site** , verifique se que o nome do host é o mesmo que o nome amigável, conforme ilustrado nas figuras a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-167">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following figures.</span></span>
    
     ![O assistente de Certificado Autoassinado](images/SelfSignedCert.jpg)
  
     ![O nome de host na caixa Editar Ligações](images/SelfSignedCert1.jpg)
  
5. <span data-ttu-id="2a618-170">Do portal de gerenciamento do Azure, clique na máquina virtual que você deseja configurar e clique em **pontos de extremidade**.</span><span class="sxs-lookup"><span data-stu-id="2a618-170">From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.</span></span>
    
6. <span data-ttu-id="2a618-171">Clique em **Adicionar**e, em seguida, clique em **-->** (para Avançar).</span><span class="sxs-lookup"><span data-stu-id="2a618-171">Click **Add**, and then click **-->** (for Next).</span></span>
    
7. <span data-ttu-id="2a618-172">Em **nome**, digite um nome para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2a618-172">In **Name**, type a name for the endpoint.</span></span>
    
8. <span data-ttu-id="2a618-p108">Em **Porta pública** e **Privada porta**, digite os números de porta que você deseja usar e clique para concluir a marca de seleção. Esses números podem ser diferentes. Para os fins deste artigo, estamos usando 443, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-p108">In **Public Port** and **Private Port**, type the port numbers that you want to use, and then click the check mark to complete. These numbers can be different. For the purposes of this article, we are using 443, as illustrated in the following figure.</span></span>
    
     ![As configurações de Ponto de Extremidade no Azure](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="2a618-177">Para obter informações adicionais sobre como adicionar um ponto de extremidade para uma máquina virtual no Windows Azure, consulte [como definir backup pontos de extremidade para uma máquina Virtual](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span><span class="sxs-lookup"><span data-stu-id="2a618-177">For additional information about how to add an endpoint to a virtual machine in Azure, see [How to Set Up Endpoints to a Virtual Machine](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span></span> 
  
9. <span data-ttu-id="2a618-178">Do portal de serviços do controle de acesso, adicione uma terceira parte confiável, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-178">From the Access Control services portal, add a relying party, as illustrated in the following figure.</span></span>
    
     ![As configurações de aplicativo em Adicionar Parte Confiável](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a><span data-ttu-id="2a618-180">Criar um grupo de regra para a autenticação baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="2a618-180">Create a rule group for claims-based authentication</span></span>

<span data-ttu-id="2a618-181">Use as etapas a seguir para criar um novo grupo de regra para controlar a autenticação baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="2a618-181">Use the following steps to create a new rule group to control claims-based authentication.</span></span>
  
1. <span data-ttu-id="2a618-182">No painel esquerdo, clique em **grupos de regra**e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2a618-182">In the left pane, click **Rule groups**, and then click **Add**.</span></span>
    
2. <span data-ttu-id="2a618-p109">Digite um nome para o grupo de regras, clique em **Salvar**e, em seguida, clique em **Gerar**. Para os fins deste artigo, estamos usando o **grupo de regra padrão loop for spvms.cloudapp.net**, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-p109">Type a name for the rule group, click **Save**, and then click **Generate**. For the purposes of this article, we are using **Default Rule Group for. spvms.cloudapp.net**, as illustrated in the following figure.</span></span>
    
     ![As configurações de Grupo de Regras no Azure](images/RuleGroup.jpg)
  
     ![As regras depois de escolher Gerar](images/GenerateRules.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="2a618-187">Para obter informações adicionais sobre como criar grupos de regras, consulte [grupos de regras e regras](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span><span class="sxs-lookup"><span data-stu-id="2a618-187">For additional information about how to create rule groups, see [Rule Groups and Rules](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span></span> 
  
3. <span data-ttu-id="2a618-p110">Clique no grupo de regra que você deseja alterar e, em seguida, clique na regra de declaração que você deseja alterar. Para os fins deste artigo, adicionamos uma regra de declaração no grupo para passar o **nome** como **upn**, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-p110">Click the rule group that you want to change, and then click the claim rule that you want to change. For the purposes of this article, we add a claim rule to the group to pass **name** as **upn**, as illustrated by the following figure.</span></span>
    
     ![As regras de declaração no Controle de Acesso do Azure](images/ClaimRules.jpg)
  
4. <span data-ttu-id="2a618-191">Excluir a regra de declaração existente chamada **upn**e deixar a regra de **Declaração nome UPN** , conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-191">Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.</span></span>
    
     ![As configurações de regras de declaração no Controle de Acesso do Azure](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a><span data-ttu-id="2a618-193">Configurar o certificado x. 509</span><span class="sxs-lookup"><span data-stu-id="2a618-193">Configure the X.509 certificate</span></span>

<span data-ttu-id="2a618-194">Use as seguintes etapas para configurar o certificado x. 509 a ser usado para autenticação de token.</span><span class="sxs-lookup"><span data-stu-id="2a618-194">Use the following steps to configure the X.509 certificate to use for token signing.</span></span>
  
1. <span data-ttu-id="2a618-195">No painel de serviço de controle de acesso, **desenvolvimento**, clique em **integração de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="2a618-195">In the Access Control Service pane, under **Development**, click **Application integration**.</span></span>
    
2. <span data-ttu-id="2a618-196">Na **Referência de ponto de extremidade**, localize o **Federation** que está associado ao seu locatário do Azure e copie o local na barra de endereços de um navegador.</span><span class="sxs-lookup"><span data-stu-id="2a618-196">In **Endpoint Reference**, locate the **Federation.xml** that is associated with your Azure tenant, and then copy the location in the address bar of a browser.</span></span>
    
3. <span data-ttu-id="2a618-197">No arquivo **Federation** , localize a seção **RoleDescriptor** e copie as informações a partir do _<X509Certificate>_ elemento, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-197">In the **Federation.xml** file, locate the **RoleDescriptor** section, and copy the information from the _<X509Certificate>_ element, as illustrated in the following figure.</span></span>
    
     ![Elemento de certificado X509 do arquivo Federation.xml](images/X509Cert.jpg)
  
4. <span data-ttu-id="2a618-199">Partindo da raiz da unidade c:\\, crie uma pasta chamada **certificados**.</span><span class="sxs-lookup"><span data-stu-id="2a618-199">From the root of drive C:\\, create a folder named **Certificates**.</span></span>
    
5. <span data-ttu-id="2a618-200">Salvar a informação de X509Certificate até a pasta c:\\certificados com o nome de arquivo, **AcsTokenSigning.cer**.</span><span class="sxs-lookup"><span data-stu-id="2a618-200">Save the X509Certificate information to the folder C:\\Certificates with the file name, **AcsTokenSigning.cer**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="2a618-201">O nome de arquivo deve ser salvo com uma extensão. cer.</span><span class="sxs-lookup"><span data-stu-id="2a618-201">The file name must be saved with a .cer extension.</span></span> 
  
     ![Salvando o elemento X509Certificate como um arquivo](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a><span data-ttu-id="2a618-203">Criar um mapeamento de declarações usando o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a618-203">Create a claim mapping by using Windows PowerShell</span></span>

<span data-ttu-id="2a618-204">Use as etapas a seguir para criar um mapeamento de declarações usando o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a618-204">Use the following steps to create a claim mapping by using Windows PowerShell.</span></span>
  
<span data-ttu-id="2a618-205">Verifique se você possui as seguintes associações:</span><span class="sxs-lookup"><span data-stu-id="2a618-205">Verify that you have the following memberships:</span></span>
  
1. <span data-ttu-id="2a618-206">função de servidor fixa **securityadmin** na instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2a618-206">**securityadmin** fixed server role on the SQL Server instance.</span></span>
    
2. <span data-ttu-id="2a618-207">função de banco de dados fixa **db_owner** em todos os bancos de dados que serão atualizados.</span><span class="sxs-lookup"><span data-stu-id="2a618-207">**db_owner** fixed database role on all databases that will be updated.</span></span>
    
3. <span data-ttu-id="2a618-208">Grupo de administradores no servidor no qual você está executando os cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a618-208">Administrators group on the server on which you are running the Windows PowerShell cmdlets.</span></span>
    
<span data-ttu-id="2a618-209">Um administrador pode usar o cmdlet **Add-SPShellAdmin** para conceder permissões para usar cmdlets do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="2a618-209">An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2a618-p111">Se você não tiver permissões, contate o administrador da instalação ou o administrador do SQL Server para solicitar permissões. Para obter informações adicionais sobre as permissões do Windows PowerShell, consulte [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span><span class="sxs-lookup"><span data-stu-id="2a618-p111">If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about Windows PowerShell permissions, see [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span></span> 
  
1. <span data-ttu-id="2a618-212">No menu **Iniciar** , clique em **Todos os programas**.</span><span class="sxs-lookup"><span data-stu-id="2a618-212">From the **Start** menu, click **All Programs**.</span></span>
    
2. <span data-ttu-id="2a618-213">Clique em **Produtos Microsoft SharePoint 2013**.</span><span class="sxs-lookup"><span data-stu-id="2a618-213">Click **Microsoft SharePoint 2013 Products**.</span></span>
    
3. <span data-ttu-id="2a618-214">Clique em **Shell de gerenciamento do SharePoint 2013**.</span><span class="sxs-lookup"><span data-stu-id="2a618-214">Click **SharePoint 2013 Management Shell**.</span></span>
    
4. <span data-ttu-id="2a618-215">No prompt de comando do Windows PowerShell, digite os comandos a seguir para criar um mapeamento de declaração:</span><span class="sxs-lookup"><span data-stu-id="2a618-215">At the Windows PowerShell command prompt, type the following commands to create a claim mapping:</span></span>
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a><span data-ttu-id="2a618-216">Configurar o SharePoint para o novo provedor de identidade</span><span class="sxs-lookup"><span data-stu-id="2a618-216">Configure SharePoint for the new identity provider</span></span>

<span data-ttu-id="2a618-217">Use as etapas a seguir para configurar sua instalação do SharePoint para o novo provedor de identidade para o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2a618-217">Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.</span></span>
  
1. <span data-ttu-id="2a618-218">Verifique se a conta de usuário que está executando esse procedimento é membro do grupo Administradores de Farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="2a618-218">Verify that the user account that is performing this procedure is a member of the Farm Administrators SharePoint group.</span></span>
    
2. <span data-ttu-id="2a618-219">Na Administração Central, na home page, clique em **Gerenciamento de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="2a618-219">In Central Administration, on the home page, click **Application Management**.</span></span>
    
3. <span data-ttu-id="2a618-220">Na página **Gerenciamento de aplicativos** , na seção **Aplicativos Web** , clique em **Gerenciar aplicativos da web**.</span><span class="sxs-lookup"><span data-stu-id="2a618-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
4. <span data-ttu-id="2a618-221">Clique no aplicativo Web apropriado.</span><span class="sxs-lookup"><span data-stu-id="2a618-221">Click the appropriate web application.</span></span>
    
5. <span data-ttu-id="2a618-222">Na faixa de opções, clique em **Provedores de autenticação**.</span><span class="sxs-lookup"><span data-stu-id="2a618-222">From the ribbon, click **Authentication Providers**.</span></span>
    
6. <span data-ttu-id="2a618-p112">Em **zona**, clique no nome da zona. Por exemplo, **Default**.</span><span class="sxs-lookup"><span data-stu-id="2a618-p112">Under **Zone**, click the name of the zone. For example, **Default**.</span></span>
    
7. <span data-ttu-id="2a618-p113">Na página **Editar autenticação** , na seção **Tipos de autenticação de declarações** , selecione o **provedor de identidade confiável**e, em seguida, clique no nome do seu provedor, que é **Um provedor ACS**para fins deste artigo. Clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="2a618-p113">On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.</span></span>
    
8. <span data-ttu-id="2a618-227">A figura a seguir ilustra a configuração de **Provedor confiável** .</span><span class="sxs-lookup"><span data-stu-id="2a618-227">The following figure illustrates the **Trusted Provider** setting.</span></span>
    
![A configuração de Provedor Confiável em um aplicativo Web](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a><span data-ttu-id="2a618-229">Definir as permissões</span><span class="sxs-lookup"><span data-stu-id="2a618-229">Set the permissions</span></span>

<span data-ttu-id="2a618-230">Use as etapas a seguir para definir as permissões para acessar o aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="2a618-230">Use the following steps to set the permissions to access the web application.</span></span>
  
1. <span data-ttu-id="2a618-231">Na Administração Central, na home page, clique em **Gerenciamento de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="2a618-231">In Central Administration, on the home page, click **Application Management**.</span></span>
    
2. <span data-ttu-id="2a618-232">Na página **Gerenciamento de aplicativos** , na seção **Aplicativos Web** , clique em **Gerenciar aplicativos da web**.</span><span class="sxs-lookup"><span data-stu-id="2a618-232">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
3. <span data-ttu-id="2a618-233">Clique no aplicativo web apropriado e clique em **Política de usuário**.</span><span class="sxs-lookup"><span data-stu-id="2a618-233">Click the appropriate web application, and then click **User Policy**.</span></span>
    
4. <span data-ttu-id="2a618-234">Em **política para aplicativo Web**, clique em **Adicionar usuários**.</span><span class="sxs-lookup"><span data-stu-id="2a618-234">In **Policy for Web Application**, click **Add Users**.</span></span>
    
5. <span data-ttu-id="2a618-235">Na caixa de diálogo **Adicionar usuários** , clique na zona apropriada em **zonas**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="2a618-235">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="2a618-236">Na caixa de diálogo **Adicionar usuários** , typeuser2@blueskyabove.onmicrosoft.com (ACS provedor).</span><span class="sxs-lookup"><span data-stu-id="2a618-236">In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span></span>
    
7. <span data-ttu-id="2a618-237">Em **permissões**, clique em **Controle total**.</span><span class="sxs-lookup"><span data-stu-id="2a618-237">In **Permissions**, click **Full Control**.</span></span>
    
8. <span data-ttu-id="2a618-238">Clique em **Concluir** e então clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a618-238">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="2a618-239">A figura a seguir ilustra a seção **Adicionar usuários** de um aplicativo web existente.</span><span class="sxs-lookup"><span data-stu-id="2a618-239">The following figure illustrates the **Add Users** section of an existing web application.</span></span>
  
![Adicionando usuários a um aplicativo Web existente](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a><span data-ttu-id="2a618-241">Verifique se o novo provedor</span><span class="sxs-lookup"><span data-stu-id="2a618-241">Verify the new provider</span></span>

<span data-ttu-id="2a618-242">Use as etapas a seguir para verificar se o novo provedor de identidade está funcionando, garantindo que o novo provedor de autenticação é exibida no prompt de entrada.</span><span class="sxs-lookup"><span data-stu-id="2a618-242">Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.</span></span>
  
1. <span data-ttu-id="2a618-243">Entrar usando o novo provedor chamado **Azul celeste acima**, conforme ilustrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a618-243">Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.</span></span>
    
     ![Caixa de diálogo de entrada mostrando o novo provedor confiável](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a><span data-ttu-id="2a618-245">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2a618-245">Additional resources</span></span>

[<span data-ttu-id="2a618-246">Noções básicas sobre WS-Federation</span><span class="sxs-lookup"><span data-stu-id="2a618-246">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="2a618-247">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="2a618-247">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="2a618-248">Ingressar na discussão</span><span class="sxs-lookup"><span data-stu-id="2a618-248">Join the discussion</span></span>

|<span data-ttu-id="2a618-249">**Entre em contato conosco**</span><span class="sxs-lookup"><span data-stu-id="2a618-249">**Contact us**</span></span>|<span data-ttu-id="2a618-250">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2a618-250">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2a618-251">**Qual conteúdo de adoção de nuvem faça você precisa?**</span><span class="sxs-lookup"><span data-stu-id="2a618-251">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="2a618-p114">Estamos criando conteúdo para a adoção de nuvem que abrange várias plataformas de nuvem da Microsoft e serviços. Fale conosco pensar em nosso conteúdo de adoção de nuvem ou pedir enviando e-mails para [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)conteúdo específico.</span><span class="sxs-lookup"><span data-stu-id="2a618-p114">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="2a618-254">**Participe da discussão de adoção de nuvem**</span><span class="sxs-lookup"><span data-stu-id="2a618-254">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="2a618-p115">Se você estiver entusiasmados pela sobre soluções baseadas em nuvem, considere ingressando a nuvem adoção consultoria placa (CAAB) para se conectar com uma comunidade amplos, vibrante de desenvolvedores de conteúdo Microsoft, profissionais do setor e clientes de todo o mundo. Para ingressar, adicione si mesmo como um membro do [espaço CAAB (placa de consultoria da adoção nuvem)](https://aka.ms/caab) da Microsoft Tech comunidade e envie-em um email rápido em [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Qualquer pessoa pode ler o conteúdo relacionado à comunidade no [blog CAAB](https://blogs.technet.com/b/solutions_advisory_board/). No entanto, os membros CAAB obtém convites para seminários na Web privados que descrevem os novos recursos de adoção de nuvem e soluções.</span><span class="sxs-lookup"><span data-stu-id="2a618-p115">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="2a618-258">**Obtenha a arte que aparece aqui**</span><span class="sxs-lookup"><span data-stu-id="2a618-258">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="2a618-p116">Se você quiser uma cópia editável da arte que você vê neste artigo, voltaremos felizes em enviá-lo. Envie sua solicitação, incluindo a URL e o título da arte, como [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).</span><span class="sxs-lookup"><span data-stu-id="2a618-p116">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

