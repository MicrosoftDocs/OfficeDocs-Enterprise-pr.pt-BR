---
title: Identidade híbrida e sincronização de diretório para o Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Descreve a sincronização de diretório com o Office 365, limpeza de serviços de domínio do Active Directory e a ferramenta Azure Active Directory Connect.
ms.openlocfilehash: fda9750ae6038f062938f3c8ad92fe1859c2d7e1
ms.sourcegitcommit: 2e6fadb5b2b16619ad141b6293d3466460720cb4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "37428108"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="45c91-103">Identidade híbrida e sincronização de diretório para o Office 365</span><span class="sxs-lookup"><span data-stu-id="45c91-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="45c91-104">*Este artigo aplica-se ao Office 365 Enterprise e ao Microsoft 365 Enterprise*</span><span class="sxs-lookup"><span data-stu-id="45c91-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise*</span></span>

<span data-ttu-id="45c91-105">Dependendo das necessidades de negócios e dos requisitos técnicos, o modelo de identidade híbrida e a sincronização de diretórios é a opção mais comum para clientes corporativos que estão adotando o Office 365.</span><span class="sxs-lookup"><span data-stu-id="45c91-105">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="45c91-106">A sincronização de diretórios permite gerenciar identidades em seus serviços de domínio do Active Directory (AD DS) e todas as atualizações de contas de usuário, grupos e contatos são sincronizadas com o locatário do Azure Active Directory (Azure AD) da sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="45c91-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="45c91-107">Quando as contas de usuário do AD DS são sincronizadas pela primeira vez, elas não recebem automaticamente uma licença do Office 365 e não podem acessar os serviços do Office 365, como email.</span><span class="sxs-lookup"><span data-stu-id="45c91-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="45c91-108">Você deve atribuir uma licença a essas contas de usuário, individualmente ou dinamicamente por meio da Associação de grupo.</span><span class="sxs-lookup"><span data-stu-id="45c91-108">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="45c91-109">Autenticação para identidade híbrida</span><span class="sxs-lookup"><span data-stu-id="45c91-109">Authentication for hybrid identity</span></span>

<span data-ttu-id="45c91-110">Há dois tipos de autenticação ao usar o modelo de identidade híbrida:</span><span class="sxs-lookup"><span data-stu-id="45c91-110">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="45c91-111">Autenticação gerenciada</span><span class="sxs-lookup"><span data-stu-id="45c91-111">Managed authentication</span></span>

  <span data-ttu-id="45c91-112">O Azure AD lida com o processo de autenticação usando uma versão de hash armazenada localmente ou envia as credenciais para um agente de software local para ser autenticado pelo AD DS local.</span><span class="sxs-lookup"><span data-stu-id="45c91-112">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="45c91-113">Autenticação federada</span><span class="sxs-lookup"><span data-stu-id="45c91-113">Federated authentication</span></span>

  <span data-ttu-id="45c91-114">O Azure AD redireciona o computador cliente solicitando a autenticação para entrar em contato com outro provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="45c91-114">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="45c91-115">Autenticação gerenciada</span><span class="sxs-lookup"><span data-stu-id="45c91-115">Managed authentication</span></span>

<span data-ttu-id="45c91-116">Há dois tipos de autenticação gerenciada:</span><span class="sxs-lookup"><span data-stu-id="45c91-116">There are two types of managed authentication:</span></span>

- <span data-ttu-id="45c91-117">Sincronização de hash de senha (PHS)</span><span class="sxs-lookup"><span data-stu-id="45c91-117">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="45c91-118">O Azure AD executa a própria autenticação.</span><span class="sxs-lookup"><span data-stu-id="45c91-118">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="45c91-119">Autenticação de passagem (PTA)</span><span class="sxs-lookup"><span data-stu-id="45c91-119">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="45c91-120">O Azure AD tem o AD DS executando a autenticação.</span><span class="sxs-lookup"><span data-stu-id="45c91-120">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="45c91-121">Sincronização de hash de senha</span><span class="sxs-lookup"><span data-stu-id="45c91-121">Password hash synchronization</span></span>

<span data-ttu-id="45c91-122">Com a sincronização de hash de senha (PHS), você sincroniza suas contas de usuário do AD DS com o Office 365 e gerencia seus usuários no local.</span><span class="sxs-lookup"><span data-stu-id="45c91-122">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="45c91-123">Hashes de senhas de usuário são sincronizados do AD DS para o Azure AD para que os usuários tenham a mesma senha no local e na nuvem.</span><span class="sxs-lookup"><span data-stu-id="45c91-123">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="45c91-124">Essa é a maneira mais simples de habilitar a autenticação para identidades do AD DS no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="45c91-124">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="45c91-125">Quando as senhas são alteradas ou redefinidas no local, os novos hashes de senha são sincronizados com o Azure AD para que os usuários sempre possam usar a mesma senha para recursos de nuvem e recursos locais.</span><span class="sxs-lookup"><span data-stu-id="45c91-125">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="45c91-126">As senhas do usuário nunca são enviadas para o Azure AD ou armazenadas no Azure AD em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="45c91-126">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="45c91-127">Alguns recursos premium do Azure AD, como proteção de identidade, exigem PHS independentemente do método de autenticação selecionado.</span><span class="sxs-lookup"><span data-stu-id="45c91-127">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="45c91-128">Consulte [escolher PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="45c91-128">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="45c91-129">Autenticação de passagem</span><span class="sxs-lookup"><span data-stu-id="45c91-129">Pass-through authentication</span></span>

<span data-ttu-id="45c91-130">A autenticação de passagem (PTA) fornece uma validação de senha simples para os serviços de autenticação do Azure AD usando um agente de software executado em um ou mais servidores locais para validar os usuários diretamente com o AD DS.</span><span class="sxs-lookup"><span data-stu-id="45c91-130">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="45c91-131">Com a autenticação de passagem (PTA), você sincroniza contas de usuário do AD DS com o Office 365 e gerencia seus usuários no local.</span><span class="sxs-lookup"><span data-stu-id="45c91-131">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="45c91-132">O PTA permite que os usuários entrem em recursos e aplicativos locais e do Office 365 usando sua conta e senha local.</span><span class="sxs-lookup"><span data-stu-id="45c91-132">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="45c91-133">Essa configuração valida senhas de usuários diretamente em seu AD DS local sem armazenar hashes de senha no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="45c91-133">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="45c91-134">PTA também é para organizações com um requisito de segurança para impor imediatamente os Estados de conta de usuário local, as diretivas de senha e o horário de logon.</span><span class="sxs-lookup"><span data-stu-id="45c91-134">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="45c91-135">Consulte [escolher PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="45c91-135">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="45c91-136">Autenticação federada</span><span class="sxs-lookup"><span data-stu-id="45c91-136">Federated authentication</span></span>

<span data-ttu-id="45c91-137">A autenticação federada é principalmente para grandes organizações corporativas com requisitos de autenticação mais complexos.</span><span class="sxs-lookup"><span data-stu-id="45c91-137">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="45c91-138">As identidades do AD DS são sincronizadas com o Office 365 e as contas de usuários são gerenciadas no local.</span><span class="sxs-lookup"><span data-stu-id="45c91-138">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="45c91-139">Com a autenticação federada, os usuários têm a mesma senha no local e na nuvem, e não precisam entrar novamente para usar o Office 365.</span><span class="sxs-lookup"><span data-stu-id="45c91-139">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="45c91-140">A autenticação federada pode dar suporte a requisitos de autenticação adicionais, como a autenticação com base em Smartcard ou uma autenticação multifator de terceiros, e normalmente é necessária quando as organizações têm um requisito de autenticação não com suporte nativo pelo Azure AD.</span><span class="sxs-lookup"><span data-stu-id="45c91-140">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="45c91-141">Consulte [escolhendo autenticação federada](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="45c91-141">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="45c91-142">Provedores de autenticação e identidade de terceiros</span><span class="sxs-lookup"><span data-stu-id="45c91-142">Third-party authentication and identity providers</span></span>

<span data-ttu-id="45c91-143">Os objetos de diretório no local podem ser sincronizados com o Office 365 e o acesso a recursos em nuvem é basicamente gerenciado por um provedor de identidade de terceiros (IdP).</span><span class="sxs-lookup"><span data-stu-id="45c91-143">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="45c91-144">Se sua organização usa uma solução de Federação de terceiros, você pode configurar o logon com essa solução para o Office 365 desde que a solução de Federação de terceiros seja compatível com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="45c91-144">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="45c91-145">Confira [compatibilidade de Federação do Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="45c91-145">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="45c91-146">Limpeza do AD DS</span><span class="sxs-lookup"><span data-stu-id="45c91-146">AD DS Cleanup</span></span>

<span data-ttu-id="45c91-147">Para ajudar a garantir uma transição contínua para o Office 365 usando a sincronização, você deve preparar sua floresta do AD DS antes de começar sua implantação de sincronização de diretório do Office 365.</span><span class="sxs-lookup"><span data-stu-id="45c91-147">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="45c91-148">Ao [Configurar a sincronização de diretórios no Office 365](set-up-directory-synchronization.md), uma das etapas é [baixar e executar a ferramenta IdFix](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="45c91-148">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="45c91-149">Você pode usar a ferramenta IdFix para ajudar com a [limpeza de diretório](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="45c91-149">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="45c91-150">Sua limpeza de diretório deve se concentrar nas seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="45c91-150">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="45c91-151">Remover os atributos **ProxyAddress** e **userPrincipalName** duplicados.</span><span class="sxs-lookup"><span data-stu-id="45c91-151">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="45c91-152">Atualizar atributos **userPrincipalName** em branco e inválidos com atributos **userPrincipalName** válidos.</span><span class="sxs-lookup"><span data-stu-id="45c91-152">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="45c91-153">Remover caracteres inválidos e questionáveis em **excertoname**, sobrenome ( **SN** ) **, sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailNickname**e **userPrincipalName** atributos.</span><span class="sxs-lookup"><span data-stu-id="45c91-153">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="45c91-154">Para obter detalhes sobre como preparar atributos, consulte [lista de atributos que são sincronizados pela ferramenta de sincronização do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="45c91-154">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="45c91-155">Estes são os mesmos atributos que o Azure AD Connect sincroniza.</span><span class="sxs-lookup"><span data-stu-id="45c91-155">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="45c91-156">Considerações de implantação de várias florestas</span><span class="sxs-lookup"><span data-stu-id="45c91-156">Multi-forest deployment considerations</span></span>

<span data-ttu-id="45c91-157">Para várias florestas e opções de SSO, use a [instalação personalizada do Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="45c91-157">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="45c91-158">Se sua organização tiver várias florestas para autenticação (florestas de logon), recomendamos enfaticamente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="45c91-158">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="45c91-159">**Considere a consolidação de suas florestas.**</span><span class="sxs-lookup"><span data-stu-id="45c91-159">**Consider consolidating your forests.**</span></span> <span data-ttu-id="45c91-160">Em geral, há mais sobrecarga necessária para manter várias florestas.</span><span class="sxs-lookup"><span data-stu-id="45c91-160">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="45c91-161">A menos que sua organização tenha restrições de segurança que ditem a necessidade de florestas separadas, considere simplificar o ambiente local.</span><span class="sxs-lookup"><span data-stu-id="45c91-161">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="45c91-162">**Use somente na floresta de logon principal.**</span><span class="sxs-lookup"><span data-stu-id="45c91-162">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="45c91-163">Considere a implantação do Office 365 somente em sua floresta de logon principal para a sua distribuição inicial do Office 365.</span><span class="sxs-lookup"><span data-stu-id="45c91-163">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="45c91-164">Se você não puder consolidar sua implantação do AD DS de várias florestas ou se estiver usando outros serviços de diretório para gerenciar identidades, talvez seja possível sincronizá-las com a ajuda da Microsoft ou de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="45c91-164">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="45c91-165">Confira [sincronização de diretórios de várias florestas com um cenário de logon único](https://go.microsoft.com/fwlink/p/?LinkId=525321) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="45c91-165">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="45c91-166">Recursos que dependem da sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="45c91-166">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="45c91-167">A sincronização de diretórios é necessária para os seguintes recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="45c91-167">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="45c91-168">Logon único (SSO) contínuo do Azure AD</span><span class="sxs-lookup"><span data-stu-id="45c91-168">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="45c91-169">Coexistência do Skype</span><span class="sxs-lookup"><span data-stu-id="45c91-169">Skype coexistence</span></span>
- <span data-ttu-id="45c91-170">Implantação híbrida do Exchange, incluindo:</span><span class="sxs-lookup"><span data-stu-id="45c91-170">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="45c91-171">GAL (lista de endereços global) totalmente compartilhada entre seu ambiente do Exchange local e o Office 365.</span><span class="sxs-lookup"><span data-stu-id="45c91-171">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="45c91-172">Sincronizar informação de GAL de sistemas de email diferentes.</span><span class="sxs-lookup"><span data-stu-id="45c91-172">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="45c91-173">A capacidade de adicionar usuários e remover usuários das ofertas de serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="45c91-173">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="45c91-174">Isto exige o seguinte:</span><span class="sxs-lookup"><span data-stu-id="45c91-174">This requires the following:</span></span>
  - <span data-ttu-id="45c91-175">A sincronização bidirecional deve ser configurada durante a configuração de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="45c91-175">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="45c91-176">Por padrão, as ferramentas de sincronização de diretório gravam informações de diretório somente na nuvem.</span><span class="sxs-lookup"><span data-stu-id="45c91-176">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="45c91-177">Ao configurar a sincronização bidirecional, você habilita a funcionalidade de write-back para que um número limitado de atributos de objeto seja copiado da nuvem e, em seguida, os escreveu novamente no AD DS local.</span><span class="sxs-lookup"><span data-stu-id="45c91-177">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="45c91-178">O Write-back também é conhecido como modo híbrido do Exchange.</span><span class="sxs-lookup"><span data-stu-id="45c91-178">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="45c91-179">Uma implantação híbrida local do Exchange</span><span class="sxs-lookup"><span data-stu-id="45c91-179">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="45c91-180">A capacidade de mover algumas caixas de correio do usuário para o Office 365 enquanto mantém outras caixas de correio do usuário no local.</span><span class="sxs-lookup"><span data-stu-id="45c91-180">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="45c91-181">Remetentes confiáveis e remetentes bloqueados no local são replicados para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="45c91-181">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="45c91-182">Delegação básica e funcionalidade de email enviar em nome de.</span><span class="sxs-lookup"><span data-stu-id="45c91-182">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="45c91-183">Você tem uma solução integrada de cartão inteligente ou de autenticação multifator no local.</span><span class="sxs-lookup"><span data-stu-id="45c91-183">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="45c91-184">Sincronização de fotos, miniaturas, salas de conferência e grupos de segurança</span><span class="sxs-lookup"><span data-stu-id="45c91-184">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="45c91-185">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="45c91-185">Next step</span></span>

<span data-ttu-id="45c91-186">Quando estiver pronto para implantar a identidade híbrida, confira [preparar para provisionar usuários](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="45c91-186">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="45c91-187">Confira também</span><span class="sxs-lookup"><span data-stu-id="45c91-187">See also</span></span>

[<span data-ttu-id="45c91-188">Visão geral do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="45c91-188">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

