---
title: Identidade no Microsoft Cloud para arquitetos corporativos
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: O365ITProTrain, Strat_O365_Enterprise, Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "Resumo: Criar sua solução de identidade para plataformas e serviços em nuvem da Microsoft."
ms.openlocfilehash: 08dfb843128839fc6f8b70373335f64b44133ff1
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="85de7-103">Identidade no Microsoft Cloud para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="85de7-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="85de7-104">**Resumo:** Criar sua solução de identidade para plataformas e serviços em nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="85de7-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="85de7-p101">Este artigo descreve o que os arquitetos de TI precisam saber sobre a criação de identidade para organizações que usam plataformas e serviços da nuvem da Microsoft. Você também pode visualizar este artigo como um cartaz de 5 páginas e imprimi-lo em formato tabloide (também conhecido por ledger, 11x17 ou A3).</span><span class="sxs-lookup"><span data-stu-id="85de7-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="85de7-107">[![Imagem em miniatura do modelo de identidade de nuvem da Microsoft](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="85de7-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="85de7-108">![Arquivo PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Arquivo do Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![Ver uma página com as versões em outros idiomas](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Mais idiomas](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="85de7-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="85de7-109">Também é possível ver todos os modelos nos [Recursos de arquitetura de TI da Microsoft Cloud](microsoft-cloud-it-architecture-resources.md) e deslizar o dedo pelo [Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI](https://aka.ms/cloudarchitecture).</span><span class="sxs-lookup"><span data-stu-id="85de7-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="85de7-p102">Este artigo reflete a versão de janeiro de 2016 do cartaz **Identidade de nuvem da Microsoft para arquitetos corporativos**. Ele não contém as alterações da versão de abril de 2016 ou posteriores do cartaz.</span><span class="sxs-lookup"><span data-stu-id="85de7-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="85de7-112">Criação de identidade para a nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="85de7-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="85de7-p103">A integração das suas identidades com a nuvem da Microsoft oferece acesso a uma ampla gama de opções de serviços e plataformas da nuvem. Há duas opções principais:</span><span class="sxs-lookup"><span data-stu-id="85de7-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="85de7-p104">Você pode integrar ao Microsoft Azure AD (Active Directory). Isso envolve a sincronização das suas contas no local com o Azure AD, o provedor de identidade para a nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="85de7-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="85de7-117">Você pode estender seu ambiente do Active Directory Domain Services (AD DS) local para máquinas virtuais em execução nos serviços de infraestrutura do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="85de7-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![Opções para a criação de suas identidades na nuvem](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="85de7-119">**Figura 1: Opções para a criação das suas identidades na nuvem**</span><span class="sxs-lookup"><span data-stu-id="85de7-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="85de7-120">A Figura 1 mostra como o Azure AD é o provedor de identidade dos serviços de Software como serviço (SaaS) da Microsoft e de aplicativos do de Plataforma como serviço (PaaS) do Azure e como os aplicativos de linhas de negócios podem usar o AD DS local.</span><span class="sxs-lookup"><span data-stu-id="85de7-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="85de7-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="85de7-121">Azure Active Directory</span></span>

<span data-ttu-id="85de7-p105">O Microsoft Azure AD é o serviço de gerenciamento de acesso e identidade hospedado em nuvem da Microsoft. Ele está no centro dos serviços e das plataformas da nuvem da Microsoft. A integração com o Azure AD oferece acesso a todos os serviços de SaaS da Microsoft que usam seu conjunto atual de contas e senhas. Essa integração também oferece identidade baseada em nuvem para aplicativos de PaaS do Azure.</span><span class="sxs-lookup"><span data-stu-id="85de7-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="85de7-126">O Azure AD não substitui a necessidade do AD DS local para organizações empresariais ou de máquinas virtuais com base em Windows em execução no Azure Infraestrutura como serviço (IaaS).</span><span class="sxs-lookup"><span data-stu-id="85de7-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="85de7-127">Há três edições do Azure AD: Grátis, Básico e Premium.</span><span class="sxs-lookup"><span data-stu-id="85de7-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="85de7-128">**Grátis**</span><span class="sxs-lookup"><span data-stu-id="85de7-128">**Free**</span></span> <br/> |<span data-ttu-id="85de7-129">**Básica**</span><span class="sxs-lookup"><span data-stu-id="85de7-129">**Basic**</span></span> <br/> |<span data-ttu-id="85de7-130">**Premium**</span><span class="sxs-lookup"><span data-stu-id="85de7-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="85de7-131">	Gerenciar contas de usuário</span><span class="sxs-lookup"><span data-stu-id="85de7-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="85de7-132">Sincronizar com diretórios locais</span><span class="sxs-lookup"><span data-stu-id="85de7-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="85de7-133">Logon único entre Azure, Office 365 e milhares de outros aplicativos de SaaS populares, como Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox e mais</span><span class="sxs-lookup"><span data-stu-id="85de7-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="85de7-134">Inclui todas as capacidades na edição livre, além de:</span><span class="sxs-lookup"><span data-stu-id="85de7-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="85de7-135">Marca da empresa</span><span class="sxs-lookup"><span data-stu-id="85de7-135">Company branding</span></span> <br/>  <span data-ttu-id="85de7-136">Acesso a aplicativos baseados em grupo</span><span class="sxs-lookup"><span data-stu-id="85de7-136">Group-based application access</span></span> <br/>  <span data-ttu-id="85de7-137">Redefinição de senha de autoatendimento</span><span class="sxs-lookup"><span data-stu-id="85de7-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="85de7-138">SLA corporativo de 99,9%</span><span class="sxs-lookup"><span data-stu-id="85de7-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="85de7-139">Inclui todos os recursos das edições Free e Basic, além de:</span><span class="sxs-lookup"><span data-stu-id="85de7-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="85de7-140">Gerenciamento de grupo de autoatendimento</span><span class="sxs-lookup"><span data-stu-id="85de7-140">Self-service group management</span></span> <br/>  <span data-ttu-id="85de7-141">Relatórios e alertas avançados de segurança</span><span class="sxs-lookup"><span data-stu-id="85de7-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="85de7-142">Multi-factor Authentication</span><span class="sxs-lookup"><span data-stu-id="85de7-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="85de7-143">Redefinição de senha com write-back para AD DS local</span><span class="sxs-lookup"><span data-stu-id="85de7-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="85de7-144">Sincronização bidirecional da ferramenta Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="85de7-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="85de7-145">Proxy do Aplicativo Azure AD</span><span class="sxs-lookup"><span data-stu-id="85de7-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="85de7-146">	Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="85de7-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="85de7-147">Para mais informações sobre versões, confira [Edições do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span><span class="sxs-lookup"><span data-stu-id="85de7-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="85de7-148">Opção 1: Integração com o Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="85de7-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="85de7-p106">A maioria das organizações sincroniza um conjunto de objetos e atributos padrão para seu locatário do Azure AD. A ferramenta Azure AD Connect sincroniza suas contas entre o AD DS local e o locatário Azure AD.</span><span class="sxs-lookup"><span data-stu-id="85de7-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![Integração com o Azure AD](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="85de7-152">**Figura 2: Integração com o Azure AD**</span><span class="sxs-lookup"><span data-stu-id="85de7-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="85de7-p107">A Figura 2 mostra como a ferramenta Azure AD Connect obtém as alterações do AD DS e as envia ao seu locatário do Azure AD. Nesse caso, seu locatário do Azure AD é uma duplicata hospedada na nuvem de conteúdo do diretório local essencial.</span><span class="sxs-lookup"><span data-stu-id="85de7-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="85de7-p108">Muitas organizações usam o AD DS como provedor de identidade local. Você pode usar um tipo diferente de provedor de identidade local (como um que use LDAP) e sincronizá-lo no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="85de7-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="85de7-157">Opção 2: Estender o AD DS ao Azure</span><span class="sxs-lookup"><span data-stu-id="85de7-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="85de7-p109">Estender o AD DS para máquinas virtuais em execução nos serviços de infraestrutura do Azure oferece suporte a um conjunto diferente de soluções e aplicativos em comparação à sincronização com o Azure AD. Aqui estão duas:</span><span class="sxs-lookup"><span data-stu-id="85de7-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="85de7-160">Oferece suporte a soluções baseadas em nuvem que requerem autenticação NTLM ou Kerberos ou máquinas virtuais associadas a um domínio do AD DS.</span><span class="sxs-lookup"><span data-stu-id="85de7-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="85de7-161">Adiciona mais potencial de integração para aplicativos e serviços em nuvem em plataformas e serviços em nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="85de7-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![Estender o AD DS ao Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="85de7-163">**Figura 3: Estender o AD DS ao Azure**</span><span class="sxs-lookup"><span data-stu-id="85de7-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="85de7-p110">A Figura 3 mostra um controlador de domínios do AD DS conectado a uma rede virtual do Azure por um dispositivo VPN no local e um gateway de VPN do Azure. A rede virtual do Azure contém servidores para um aplicativo de linha de negócios e seu próprio conjunto de controladores de domínios do AD DS.</span><span class="sxs-lookup"><span data-stu-id="85de7-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="85de7-166">Mais informações</span><span class="sxs-lookup"><span data-stu-id="85de7-166">More Information</span></span>

- [<span data-ttu-id="85de7-167">A sincronização do seu diretório com o Office 365 é fácil</span><span class="sxs-lookup"><span data-stu-id="85de7-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="85de7-168">Infográfico: Gerenciamento de identidade e acesso de nuvem</span><span class="sxs-lookup"><span data-stu-id="85de7-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="85de7-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="85de7-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="85de7-170">Integrar suas contas do AD DS no local com o Microsoft Azure AD</span><span class="sxs-lookup"><span data-stu-id="85de7-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="85de7-171">Ao sincronizar suas contas AD DS no local com o Azure AD, seus usuários podem usar suas contas AD DS locais para acessar:</span><span class="sxs-lookup"><span data-stu-id="85de7-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="85de7-172">Todos os serviços de SaaS da Microsoft (Office 365, Microsoft Intune e Dynamics CRM Online)</span><span class="sxs-lookup"><span data-stu-id="85de7-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="85de7-173">Os aplicativos em execução na PaaS do Azure</span><span class="sxs-lookup"><span data-stu-id="85de7-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="85de7-174">Há duas maneiras de configurar essa integração:</span><span class="sxs-lookup"><span data-stu-id="85de7-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="85de7-175">Sincronização de diretório e senha</span><span class="sxs-lookup"><span data-stu-id="85de7-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="85de7-176">Federação e logon único</span><span class="sxs-lookup"><span data-stu-id="85de7-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="85de7-p111">Comece com a opção mais simples que atenda às suas necessidades. Você pode alternar entre essas opções, se necessário.</span><span class="sxs-lookup"><span data-stu-id="85de7-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="85de7-179">Usando contas somente na nuvem (não integração com seu AD DS local) não é recomendado para organizações de grande porte.</span><span class="sxs-lookup"><span data-stu-id="85de7-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="85de7-180">Sincronização de diretório e senha</span><span class="sxs-lookup"><span data-stu-id="85de7-180">Directory and password synchronization</span></span>

<span data-ttu-id="85de7-181">Essa é a opção mais simples e requer apenas um servidor que execute a ferramenta Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="85de7-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![Configuração de sincronização de diretório e senha](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="85de7-183">**Figura 4: Configuração de sincronização de diretório e senha**</span><span class="sxs-lookup"><span data-stu-id="85de7-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="85de7-p112">A Figura 4 mostra um datacenter local ou de nuvem privada com um controlador de domínio AD DS. Um servidor que executa a ferramenta Azure AD Connect sincroniza a lista de nomes de conta com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="85de7-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="85de7-186">Com essa opção:</span><span class="sxs-lookup"><span data-stu-id="85de7-186">With this option:</span></span>
  
- <span data-ttu-id="85de7-p113">As contas de usuário são sincronizadas do seu AD DS local (ou de outro provedor de identidade) para o seu locatário do AD Azure. O diretório local continua sendo a origem autoritativa das contas, e você gerencia todas as alterações nas contas nele.</span><span class="sxs-lookup"><span data-stu-id="85de7-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="85de7-189">O Azure AD executa toda a autenticação dos serviços baseados em SaaS da Microsoft e aplicativos de PaaS do Azure.</span><span class="sxs-lookup"><span data-stu-id="85de7-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="85de7-190">Você também pode configurar a sincronização para várias florestas do AD DS.</span><span class="sxs-lookup"><span data-stu-id="85de7-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="85de7-191">Com sincronização de senha:</span><span class="sxs-lookup"><span data-stu-id="85de7-191">With password synchronization:</span></span>
  
- <span data-ttu-id="85de7-192">Os usuários são solicitados a inserir uma senha ao acessar serviços na nuvem, que é a mesma senha que eles usam para recursos locais.</span><span class="sxs-lookup"><span data-stu-id="85de7-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="85de7-p114">As senhas de usuário nunca são enviadas como texto não criptografado para o Azure AD. Em vez disso, um hash da senha é usado. É impossível criptograficamente descriptografar ou fazer engenharia reversa do hash da senha e obter a senha em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="85de7-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="85de7-196">Com MFA (Autenticação Multifator):</span><span class="sxs-lookup"><span data-stu-id="85de7-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="85de7-197">Você pode aproveitar os recursos básicos de MFA oferecidos com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="85de7-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="85de7-198">Os desenvolvedores de aplicativos de PaaS do Azure podem aproveitar o Serviço de Autenticação Multifator do Azure.</span><span class="sxs-lookup"><span data-stu-id="85de7-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="85de7-199"> A sincronização de diretórios não oferece integração com as soluções de MFA locais.</span><span class="sxs-lookup"><span data-stu-id="85de7-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="85de7-200">Federação e logon único</span><span class="sxs-lookup"><span data-stu-id="85de7-200">Federation and single sign-on</span></span>

<span data-ttu-id="85de7-201">Essa opção exige infraestrutura e servidores adicionais.</span><span class="sxs-lookup"><span data-stu-id="85de7-201">This option requires additional servers and infrastructure.</span></span> 
  
![Servidores necessários para a autenticação federada](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="85de7-203">**Figura 5: Servidores necessários para a autenticação federada**</span><span class="sxs-lookup"><span data-stu-id="85de7-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="85de7-p115">A Figura 5 mostra o conjunto de componentes de autenticação federada. O Azure AD entra em contato com um proxy de aplicativo Web que encaminha a solicitação de autenticação para um servidor de serviços de Federação do Active Directory (AD FS), que encaminha a solicitação para um controlador de domínios do AD DS para avaliação e resposta. Um servidor que executa a ferramenta Azure AD Connect sincroniza a lista de nomes de conta do AD DS com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="85de7-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="85de7-207">A federação fornece esses recursos corporativos adicionais:</span><span class="sxs-lookup"><span data-stu-id="85de7-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="85de7-208">Todas as solicitações de autenticação enviadas ao Azure AD são encaminhadas para e executadas no provedor de identidade local pelo AD FS.</span><span class="sxs-lookup"><span data-stu-id="85de7-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="85de7-209">Funciona com provedores de identidade não Microsoft.</span><span class="sxs-lookup"><span data-stu-id="85de7-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="85de7-210">A sincronização de hash de senha pode atuar como um backup de entrada para entrada federada (por exemplo, se houver falha na autenticação federada).</span><span class="sxs-lookup"><span data-stu-id="85de7-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="85de7-211">Use federação se:</span><span class="sxs-lookup"><span data-stu-id="85de7-211">Use federation if:</span></span>
  
- <span data-ttu-id="85de7-p116">Logon único for necessário. Com o logon único, os usuários não serão solicitados a inserir credenciais (nome de usuário ou senha) ao acessar um serviço na nuvem.</span><span class="sxs-lookup"><span data-stu-id="85de7-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="85de7-214">O AD FS já estiver implantado.</span><span class="sxs-lookup"><span data-stu-id="85de7-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="85de7-215">Você usar um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="85de7-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="85de7-216">Você usa o Forefront Identity Manager 2010 R2 (não oferece suporte a sincronização de hash de senha).</span><span class="sxs-lookup"><span data-stu-id="85de7-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="85de7-217">Você tiver um cartão inteligente integrado local ou outra solução de MFA.</span><span class="sxs-lookup"><span data-stu-id="85de7-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="85de7-218">Você precisar de auditoria de credenciais e/ou desativação de contas.</span><span class="sxs-lookup"><span data-stu-id="85de7-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="85de7-219">Sua organização exige restrições de entrada do cliente pela rede local ou horas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="85de7-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="85de7-220">É preciso estar em conformidade com FIPS (Padrões Federais de Processamento de Informações).</span><span class="sxs-lookup"><span data-stu-id="85de7-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="85de7-221">A autenticação federada requer um maior investimento na infraestrutura local.</span><span class="sxs-lookup"><span data-stu-id="85de7-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="85de7-p117">Os servidores no local devem estar acessíveis pela Internet por meio de um firewall corporativo. A Microsoft recomenda o uso de servidores Proxy de aplicativo da Web implantados na sua rede de perímetro.</span><span class="sxs-lookup"><span data-stu-id="85de7-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="85de7-224">Requer hardware, licenças e operações para servidores do AD FS, proxy do AD FS ou servidores Proxy de Aplicativo Web, firewalls e balanceadores de carga.</span><span class="sxs-lookup"><span data-stu-id="85de7-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="85de7-225">Disponibilidade e desempenho são importantes para garantir que os usuários possam acessar o Office 365 e outros aplicativos em nuvem.</span><span class="sxs-lookup"><span data-stu-id="85de7-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="85de7-226">Mais informações</span><span class="sxs-lookup"><span data-stu-id="85de7-226">More Information</span></span>

- [<span data-ttu-id="85de7-227">A sincronização do seu diretório com o Office 365 é fácil</span><span class="sxs-lookup"><span data-stu-id="85de7-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="85de7-228">Prepare-se para provisionar usuários pela sincronização de diretório com o Office 365</span><span class="sxs-lookup"><span data-stu-id="85de7-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="85de7-229">Autenticação de vários fatores para o Office 365</span><span class="sxs-lookup"><span data-stu-id="85de7-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="85de7-230">Autenticação de vários fatores do Azure</span><span class="sxs-lookup"><span data-stu-id="85de7-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="85de7-231">TechEd 2014: Integração de Diretórios: Criação de um diretório com o Active Directory e o Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="85de7-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="85de7-232">Estender o AD DS ao Azure</span><span class="sxs-lookup"><span data-stu-id="85de7-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="85de7-233">Estender o AD DS ao Azure é a primeira etapa para oferecer suporte a aplicativos de linha de negócios em execução em máquinas virtuais nos serviços de infraestrutura do Azure, que fornece:</span><span class="sxs-lookup"><span data-stu-id="85de7-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="85de7-234">Suporte para soluções baseadas em nuvem que exigem autenticação NTLM ou Kerberos ou máquinas virtuais associadas a um domínio do AD DS.</span><span class="sxs-lookup"><span data-stu-id="85de7-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="85de7-235">Potencial de integração adicional para aplicativos e serviços em nuvem e pode ser adicionado a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="85de7-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![Estender o AD DS para uma rede virtual do Azure](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="85de7-237">**Figura 6: Estender o AD DS para uma rede virtual do Azure**</span><span class="sxs-lookup"><span data-stu-id="85de7-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="85de7-p118">A Figura 6 mostra um datacenter local ou de nuvem privada com o AD DS conectado a uma rede virtual Azure com uma conexão VPN ou ExpressRoute de site para site. A rede virtual do Azure contém servidores para um aplicativo de linha de negócios e seu próprio conjunto de controladores de domínios do AD DS. Essa configuração é uma implantação híbrida do AD DS local e nos serviços de infraestrutura do Azure. Exige:</span><span class="sxs-lookup"><span data-stu-id="85de7-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="85de7-242">Uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="85de7-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="85de7-243">Uma conexão entre um dispositivo ou roteador de rede virtual privada (VPN) local ou um gateway VPN Azure.</span><span class="sxs-lookup"><span data-stu-id="85de7-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="85de7-244">Usando uma parte do seu espaço de endereço IP local para máquinas virtuais da rede virtual.</span><span class="sxs-lookup"><span data-stu-id="85de7-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="85de7-245">Implantando um ou mais controladores de domínio na rede virtual designada como servidores de catálogo global (reduz o tráfego de saída pela conexão VPN).</span><span class="sxs-lookup"><span data-stu-id="85de7-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="85de7-246">Essa arquitetura de identidade oferece suporte a um conjunto diferente de soluções e aplicativos em comparação à sincronização com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="85de7-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="85de7-247">Opções de conexão local para o Azure</span><span class="sxs-lookup"><span data-stu-id="85de7-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="85de7-248">Para se conectar à sua rede local com uma rede virtual do Azure, você pode usar:</span><span class="sxs-lookup"><span data-stu-id="85de7-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="85de7-249">Uma conexão VPN de site para site, que pode se conectar a 1 a 10 sites (inclusive outras redes virtuais do Azure) a uma única rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="85de7-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="85de7-p119">ExpressRoute, um link WAN particular e seguro ao Azure por um provedor de serviços de rede e datacenter parceiro. As conexões ExpressRoute podem oferecer maior confiabilidade, largura de banda superior e latências inferiores.</span><span class="sxs-lookup"><span data-stu-id="85de7-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="85de7-252">Mais informações</span><span class="sxs-lookup"><span data-stu-id="85de7-252">More Information</span></span>

- [<span data-ttu-id="85de7-253">Conectividade entre locais para redes virtuais</span><span class="sxs-lookup"><span data-stu-id="85de7-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="85de7-254">Visão geral técnica do ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="85de7-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="85de7-255">Diretrizes para implantação do Active Directory do Windows Server em Máquinas Virtuais do Azure</span><span class="sxs-lookup"><span data-stu-id="85de7-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="85de7-256">Integrar os aplicativos com identidades de nuvem</span><span class="sxs-lookup"><span data-stu-id="85de7-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="85de7-p120">Ao criar e desenvolver aplicativos que são executados na nuvem, você deve ter em mente a homogeneidade da experiência do usuário no processo de autenticação, incluindo o conjunto de credenciais necessárias. Por exemplo, ao usar credenciais do Windows, seja no Azure AD ou em um AD DS estendido, certifique-se de que os usuários possam autenticar rapidamente e se concentrar em suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="85de7-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![Integrar os aplicativos com identidades de nuvem](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="85de7-260">**Figura 7: Integrar os aplicativos com identidades de nuvem**</span><span class="sxs-lookup"><span data-stu-id="85de7-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="85de7-261">A Figura 7 mostra três opções para integrar seu aplicativo com identidades de nuvem.</span><span class="sxs-lookup"><span data-stu-id="85de7-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="85de7-262">Registre seus aplicativos hospedados na nuvem com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="85de7-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="85de7-p121">Confira o artigo da MSDN [Integração de aplicativos com o Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). Isso permite que você use o Azure AD para autenticar o acesso ao seu aplicativo de PaaS, bem como permite que usuários ou administradores concedam direitos ao seu aplicativo para acessar o conteúdo em seu nome de outros serviços da nuvem, como o Office 365. Mais detalhes e amostras de código podem ser encontrados no artigo da MSDN [Cenários de autenticação do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span><span class="sxs-lookup"><span data-stu-id="85de7-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="85de7-266">Aplicativos que exigem autenticação programática para obter acesso a um aplicativo protegido por AD SD, AD FS no Windows Server 2012 R2 ou Azure AD podem usar:</span><span class="sxs-lookup"><span data-stu-id="85de7-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="85de7-267">A [API do Microsoft Azure AD Graph](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="85de7-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="85de7-268">Biblioteca de autenticação do Active Directory (ADAL)</span><span class="sxs-lookup"><span data-stu-id="85de7-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="85de7-p122">A API do Microsoft Azure AD Graph oferece suporte a OAuth e OpenID Connect. Ela também funciona com aplicativos de PaaS.</span><span class="sxs-lookup"><span data-stu-id="85de7-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="85de7-p123">Configure aplicativos no local ou de linha de negócios em execução em máquinas virtuais em uma rede virtual do Azure para usar a autenticação do Windows (NTLM ou Kerberos) diretamente. Essa é a melhor experiência para usuários e requer menos configuração para desenvolvedores de aplicativos de servidor.</span><span class="sxs-lookup"><span data-stu-id="85de7-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="85de7-273">Exemplo de integração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="85de7-273">Application integration example</span></span>

<span data-ttu-id="85de7-p124">Uma organização cria um aplicativo ASP.NET que expõe um ponto de extremidade REST no qual outros aplicativos podem obter os dados de vendas mais recentes. O acesso ao ponto de extremidade REST é protegido com o Azure AD. Aplicativos devem fornecer as credenciais que podem ser autenticadas pelo Azure AD antes que o aplicativo ASP.NET envie os dados solicitados. Outros desenvolvedores na organização poderão então escrever seus próprios aplicativos que usam os dados de vendas do ponto de extremidade REST.</span><span class="sxs-lookup"><span data-stu-id="85de7-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="85de7-p125">Para autenticar no Azure AD e recuperar dados, o ADAL gerencia o processo de autenticação de usuário e transmite o token de acesso para o aplicativo para que ele possa ser usado para obter acesso aos dados de vendas. O ADAL reduz muito da complexidade da obtenção de tokens de análise, fluxos OAuth e outros elementos. O ADAL é outra solução de tecnologia que está mudando rapidamente, então os desenvolvedores devem buscar a versão mais recente no NuGet.</span><span class="sxs-lookup"><span data-stu-id="85de7-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="85de7-281">Implantar componentes de diretório no Azure</span><span class="sxs-lookup"><span data-stu-id="85de7-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="85de7-p126">Você pode implantar componentes de diretório, como servidores, para sincronização de senha ou autenticação federada em uma rede virtual do Azure em vez de em um datacenter no local. Considere os benefícios, especialmente se você planeja estender o AD DS ao Azure.</span><span class="sxs-lookup"><span data-stu-id="85de7-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="85de7-284">Aqui estão os componentes de diretório que podem ser colocados em uma rede virtual do Azure:</span><span class="sxs-lookup"><span data-stu-id="85de7-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="85de7-285">	Ferramenta Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="85de7-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="85de7-286">Componentes de autenticação federada</span><span class="sxs-lookup"><span data-stu-id="85de7-286">Federated authentication components</span></span>
    
- <span data-ttu-id="85de7-287">Um ambiente autônomo do AD DS</span><span class="sxs-lookup"><span data-stu-id="85de7-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="85de7-288">Ferramenta AD Connect</span><span class="sxs-lookup"><span data-stu-id="85de7-288">AD Connect tool</span></span>

<span data-ttu-id="85de7-p127">A ferramenta Azure AD Connect pode ser hospedada na nuvem em uma rede virtual do Azure. Considere estes benefícios da implantação dessa carga de trabalho no Azure:</span><span class="sxs-lookup"><span data-stu-id="85de7-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="85de7-291">Operações de provisionamento potencialmente mais rápidas e menor custo de operações</span><span class="sxs-lookup"><span data-stu-id="85de7-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="85de7-292">Maior disponibilidade</span><span class="sxs-lookup"><span data-stu-id="85de7-292">Increased availability</span></span>
    
![A ferramenta AD Connect em execução nos serviços de infraestrutura do Azure](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="85de7-294">**Figura 8: A ferramenta AD Connect em execução no Azure**</span><span class="sxs-lookup"><span data-stu-id="85de7-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="85de7-p128">A Figura 8 mostra a ferramenta AD Connect em execução em uma máquina virtual em uma rede virtual do Azure, que consulta um controlador de domínios do AD DS local a respeito de alterações de conta e envia essas alterações para o Office 365. Essa solução funciona com:</span><span class="sxs-lookup"><span data-stu-id="85de7-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="85de7-297">Serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="85de7-297">Office 365 services.</span></span>
    
- <span data-ttu-id="85de7-298">Aplicativos de PaaS do Azure disponíveis pela Internet.</span><span class="sxs-lookup"><span data-stu-id="85de7-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="85de7-299">Aplicativos de linha de negócios no Azure que estão disponíveis em ambientes no local por meio da conexão VPN de site a site ou ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="85de7-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="85de7-300">Para mais informações, confira [Integrar suas identidades locais ao Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="85de7-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="85de7-301">Infraestrutura de autenticação federada</span><span class="sxs-lookup"><span data-stu-id="85de7-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="85de7-302">Se você ainda não tiver implantado o AD FS no local, considere esses benefícios da implantação dessa carga de trabalho no Azure:</span><span class="sxs-lookup"><span data-stu-id="85de7-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="85de7-303">Fornece autonomia para autenticação em serviços de nuvem (sem dependências locais)</span><span class="sxs-lookup"><span data-stu-id="85de7-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="85de7-304">Reduz servidores e ferramentas hospedados localmente</span><span class="sxs-lookup"><span data-stu-id="85de7-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="85de7-305">Usa um gateway de VPN site a site em um cluster de failover de dois nós para conectar-se ao Azure (novo)</span><span class="sxs-lookup"><span data-stu-id="85de7-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="85de7-306">Usa ACLs para garantir que os servidores Proxy de Aplicativo Web possam comunicar-se apenas com o AD FS, não com controladores de domínio ou outros servidores diretamente</span><span class="sxs-lookup"><span data-stu-id="85de7-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![Implantar sua infraestrutura de autenticação federada no Azure](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="85de7-308">**Figura 9: Implantar sua infraestrutura de autenticação federada no Azure**</span><span class="sxs-lookup"><span data-stu-id="85de7-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="85de7-p129">A Figura 9 mostra um conjunto controladores de domínio locais que replicam informações do AD DS com um conjunto de controladores de domínio em uma rede virtual do Azure. A ferramenta Azure AD Connect em execução em um servidor na rede virtual do Azure consulta controladores de domínio local a respeito de alterações e, em seguida, envia essas alterações para o Azure AD. As solicitações de autenticação de entrada para o Azure AD de serviços de SaaS da Microsoft, aplicativos de PaaS do Azure e outros aplicativos em nuvem são encaminhadas para um balanceador de carga externo que encaminha a solicitação para um conjunto de servidores Proxy de aplicativo da Web. Os servidores Proxy de aplicativo da Web encaminham a solicitação um balanceador de carga interno, que encaminha a solicitação para um conjunto de servidores do AD FS. Os servidores do AD FS encaminham a solicitação para um controlador de domínios para validar as credenciais de envio.</span><span class="sxs-lookup"><span data-stu-id="85de7-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="85de7-314">Essa solução funciona com:</span><span class="sxs-lookup"><span data-stu-id="85de7-314">This solution works with:</span></span>
  
- <span data-ttu-id="85de7-315">Aplicativos que exigem Kerberos</span><span class="sxs-lookup"><span data-stu-id="85de7-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="85de7-316">Todos os serviços de SaaS da Microsoft</span><span class="sxs-lookup"><span data-stu-id="85de7-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="85de7-317">Aplicativos no Azure voltados para a Internet</span><span class="sxs-lookup"><span data-stu-id="85de7-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="85de7-318">Aplicativos na IaaS ou na PaaS do Azure que exigem autenticação com o conjunto de contas no AD DS da sua organização</span><span class="sxs-lookup"><span data-stu-id="85de7-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="85de7-319">Para mais informações, confira [Integrar suas identidades locais ao Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="85de7-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="85de7-320">Ambiente autônomo do AD DS em uma rede virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="85de7-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="85de7-p130">Não é necessário sempre integrar um aplicativo em nuvem com o seu ambiente local. Por exemplo, um domínio autônomo do AD DS em uma rede virtual do Azure oferece suporte a aplicativos que são públicos, como sites da Internet.</span><span class="sxs-lookup"><span data-stu-id="85de7-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![Um ambiente de autônomo do AD DS de um aplicativo baseado em servidor](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="85de7-324">**Figura 10: Um ambiente de autônomo do AD DS de um aplicativo baseado em servidor**</span><span class="sxs-lookup"><span data-stu-id="85de7-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="85de7-p131">A Figura 10 mostra uma rede virtual do Azure que hospeda um conjunto de servidores do AD DS, oferecendo serviços de DNS e AD DS, com um conjunto de servidores que hospedam um aplicativo. Essa solução funciona com:</span><span class="sxs-lookup"><span data-stu-id="85de7-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="85de7-327">Sites e aplicativos conectados à Internet</span><span class="sxs-lookup"><span data-stu-id="85de7-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="85de7-328">Aplicativos que exigem autenticação NTLM ou Kerberos</span><span class="sxs-lookup"><span data-stu-id="85de7-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="85de7-329">Aplicativos executados em servidores com Windows que requerem AD DS</span><span class="sxs-lookup"><span data-stu-id="85de7-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="85de7-330">Para mais informações, confira [Integrar suas identidades locais ao Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="85de7-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="85de7-331">Veja também</span><span class="sxs-lookup"><span data-stu-id="85de7-331">See Also</span></span>

[<span data-ttu-id="85de7-332">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="85de7-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="85de7-333">Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="85de7-333">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



