---
title: Identidade híbrida e sincronização de diretório para o Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
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
ms.openlocfilehash: 31fcd8baaccabf5d3f4f0cf47c7573c43f7cd40b
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102480"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="4d989-103">Identidade híbrida e sincronização de diretório para o Office 365</span><span class="sxs-lookup"><span data-stu-id="4d989-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="4d989-104">Dependendo das necessidades de negócios e dos requisitos técnicos, o modelo de identidade híbrida e a sincronização de diretórios é a opção mais comum para clientes corporativos que estão adotando o Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d989-104">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="4d989-105">A sincronização de diretórios permite gerenciar identidades em seus serviços de domínio do Active Directory (AD DS) e todas as atualizações de contas de usuário, grupos e contatos são sincronizadas com o locatário do Azure Active Directory (Azure AD) da sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d989-105">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>


>[!Note]
><span data-ttu-id="4d989-106">Quando as contas de usuário do AD DS são sincronizadas pela primeira vez, elas não recebem automaticamente uma licença do Office 365 e não podem acessar os serviços do Office 365, como email.</span><span class="sxs-lookup"><span data-stu-id="4d989-106">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="4d989-107">Você deve atribuir uma licença a essas contas de usuário, individualmente ou dinamicamente por meio da Associação de grupo.</span><span class="sxs-lookup"><span data-stu-id="4d989-107">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="4d989-108">Autenticação para identidade híbrida</span><span class="sxs-lookup"><span data-stu-id="4d989-108">Authentication for hybrid identity</span></span>

<span data-ttu-id="4d989-109">Há dois tipos de autenticação ao usar o modelo de identidade híbrida:</span><span class="sxs-lookup"><span data-stu-id="4d989-109">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="4d989-110">Autenticação gerenciada</span><span class="sxs-lookup"><span data-stu-id="4d989-110">Managed authentication</span></span>

  <span data-ttu-id="4d989-111">O Azure AD lida com o processo de autenticação usando uma versão de hash armazenada localmente ou envia as credenciais para um agente de software local para ser autenticado pelo AD DS local.</span><span class="sxs-lookup"><span data-stu-id="4d989-111">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="4d989-112">Autenticação federada</span><span class="sxs-lookup"><span data-stu-id="4d989-112">Federated authentication</span></span>

  <span data-ttu-id="4d989-113">O Azure AD redireciona o computador cliente solicitando a autenticação para entrar em contato com outro provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="4d989-113">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="4d989-114">Autenticação gerenciada</span><span class="sxs-lookup"><span data-stu-id="4d989-114">Managed authentication</span></span>

<span data-ttu-id="4d989-115">Há dois tipos de autenticação gerenciada:</span><span class="sxs-lookup"><span data-stu-id="4d989-115">There are two types of managed authentication:</span></span>

- <span data-ttu-id="4d989-116">Sincronização de hash de senha (PHS)</span><span class="sxs-lookup"><span data-stu-id="4d989-116">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="4d989-117">O Azure AD executa a própria autenticação.</span><span class="sxs-lookup"><span data-stu-id="4d989-117">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="4d989-118">Autenticação de passagem (PTA)</span><span class="sxs-lookup"><span data-stu-id="4d989-118">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="4d989-119">O Azure AD tem o AD DS executando a autenticação.</span><span class="sxs-lookup"><span data-stu-id="4d989-119">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="4d989-120">Sincronização de hash de senha</span><span class="sxs-lookup"><span data-stu-id="4d989-120">Password hash synchronization</span></span>

<span data-ttu-id="4d989-121">Com a sincronização de hash de senha (PHS), você sincroniza suas contas de usuário do AD DS com o Office 365 e gerencia seus usuários no local.</span><span class="sxs-lookup"><span data-stu-id="4d989-121">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="4d989-122">Hashes de senhas de usuário são sincronizados do AD DS para o Azure AD para que os usuários tenham a mesma senha no local e na nuvem.</span><span class="sxs-lookup"><span data-stu-id="4d989-122">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="4d989-123">Essa é a maneira mais simples de habilitar a autenticação para identidades do AD DS no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4d989-123">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="4d989-124">Quando as senhas são alteradas ou redefinidas no local, os novos hashes de senha são sincronizados com o Azure AD para que os usuários sempre possam usar a mesma senha para recursos de nuvem e recursos locais.</span><span class="sxs-lookup"><span data-stu-id="4d989-124">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="4d989-125">As senhas do usuário nunca são enviadas para o Azure AD ou armazenadas no Azure AD em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="4d989-125">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="4d989-126">Alguns recursos premium do Azure AD, como proteção de identidade, exigem PHS independentemente do método de autenticação selecionado.</span><span class="sxs-lookup"><span data-stu-id="4d989-126">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="4d989-127">Consulte [escolher PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="4d989-127">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="4d989-128">Autenticação de passagem</span><span class="sxs-lookup"><span data-stu-id="4d989-128">Pass-through authentication</span></span>

<span data-ttu-id="4d989-129">A autenticação de passagem (PTA) fornece uma validação de senha simples para os serviços de autenticação do Azure AD usando um agente de software executado em um ou mais servidores locais para validar os usuários diretamente com o AD DS.</span><span class="sxs-lookup"><span data-stu-id="4d989-129">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="4d989-130">Com a autenticação de passagem (PTA), você sincroniza contas de usuário do AD DS com o Office 365 e gerencia seus usuários no local.</span><span class="sxs-lookup"><span data-stu-id="4d989-130">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="4d989-131">O PTA permite que os usuários entrem em recursos e aplicativos locais e do Office 365 usando sua conta e senha local.</span><span class="sxs-lookup"><span data-stu-id="4d989-131">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="4d989-132">Essa configuração valida senhas de usuários diretamente em seu AD DS local sem armazenar hashes de senha no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4d989-132">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="4d989-133">PTA também é para organizações com um requisito de segurança para impor imediatamente os Estados de conta de usuário local, as diretivas de senha e o horário de logon.</span><span class="sxs-lookup"><span data-stu-id="4d989-133">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="4d989-134">Consulte [escolher PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="4d989-134">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="4d989-135">Autenticação federada</span><span class="sxs-lookup"><span data-stu-id="4d989-135">Federated authentication</span></span>

<span data-ttu-id="4d989-136">A autenticação federada é principalmente para grandes organizações corporativas com requisitos de autenticação mais complexos.</span><span class="sxs-lookup"><span data-stu-id="4d989-136">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="4d989-137">As identidades do AD DS são sincronizadas com o Office 365 e as contas de usuários são gerenciadas no local.</span><span class="sxs-lookup"><span data-stu-id="4d989-137">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="4d989-138">Com a autenticação federada, os usuários têm a mesma senha no local e na nuvem, e não precisam entrar novamente para usar o Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d989-138">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="4d989-139">A autenticação federada pode dar suporte a requisitos de autenticação adicionais, como a autenticação com base em Smartcard ou uma autenticação multifator de terceiros, e normalmente é necessária quando as organizações têm um requisito de autenticação não com suporte nativo pelo Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4d989-139">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="4d989-140">Consulte [escolhendo autenticação federada](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="4d989-140">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="4d989-141">Provedores de autenticação e identidade de terceiros</span><span class="sxs-lookup"><span data-stu-id="4d989-141">Third-party authentication and identity providers</span></span>

<span data-ttu-id="4d989-142">Os objetos de diretório no local podem ser sincronizados com o Office 365 e o acesso a recursos em nuvem é basicamente gerenciado por um provedor de identidade de terceiros (IdP).</span><span class="sxs-lookup"><span data-stu-id="4d989-142">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="4d989-143">Se sua organização usa uma solução de Federação de terceiros, você pode configurar o logon com essa solução para o Office 365 desde que a solução de Federação de terceiros seja compatível com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4d989-143">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="4d989-144">Confira [compatibilidade de Federação do Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="4d989-144">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="4d989-145">Limpeza do AD DS</span><span class="sxs-lookup"><span data-stu-id="4d989-145">AD DS Cleanup</span></span>

<span data-ttu-id="4d989-146">Para ajudar a garantir uma transição contínua para o Office 365 usando a sincronização, você deve preparar sua floresta do AD DS antes de começar sua implantação de sincronização de diretório do Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d989-146">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="4d989-147">Ao [Configurar a sincronização de diretórios no Office 365](set-up-directory-synchronization.md), uma das etapas é [baixar e executar a ferramenta IdFix](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="4d989-147">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="4d989-148">Você pode usar a ferramenta IdFix para ajudar com a [limpeza de diretório](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="4d989-148">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="4d989-149">Sua limpeza de diretório deve se concentrar nas seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="4d989-149">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="4d989-150">Remover os atributos **ProxyAddress** e **userPrincipalName** duplicados.</span><span class="sxs-lookup"><span data-stu-id="4d989-150">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="4d989-151">Atualizar atributos **userPrincipalName** em branco e inválidos com atributos **userPrincipalName** válidos.</span><span class="sxs-lookup"><span data-stu-id="4d989-151">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="4d989-152">Remover caracteres inválidos e questionáveis em \*\*\*\* excertoname, sobrenome ( **SN** ) **, sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailNickname**e **userPrincipalName** atributos.</span><span class="sxs-lookup"><span data-stu-id="4d989-152">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="4d989-153">Para obter detalhes sobre como preparar atributos, consulte [lista de atributos que são sincronizados pela ferramenta de sincronização do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="4d989-153">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="4d989-154">Estes são os mesmos atributos que o Azure AD Connect sincroniza.</span><span class="sxs-lookup"><span data-stu-id="4d989-154">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="4d989-155">Considerações de implantação de várias florestas</span><span class="sxs-lookup"><span data-stu-id="4d989-155">Multi-forest deployment considerations</span></span>

<span data-ttu-id="4d989-156">Para várias florestas e opções de SSO, use a [instalação personalizada do Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="4d989-156">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="4d989-157">Se sua organização tiver várias florestas para autenticação (florestas de logon), recomendamos enfaticamente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4d989-157">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="4d989-158">**Considere a consolidação de suas florestas.**</span><span class="sxs-lookup"><span data-stu-id="4d989-158">**Consider consolidating your forests.**</span></span> <span data-ttu-id="4d989-159">Em geral, há mais sobrecarga necessária para manter várias florestas.</span><span class="sxs-lookup"><span data-stu-id="4d989-159">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="4d989-160">A menos que sua organização tenha restrições de segurança que ditem a necessidade de florestas separadas, considere simplificar o ambiente local.</span><span class="sxs-lookup"><span data-stu-id="4d989-160">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="4d989-161">**Use somente na floresta de logon principal.**</span><span class="sxs-lookup"><span data-stu-id="4d989-161">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="4d989-162">Considere a implantação do Office 365 somente em sua floresta de logon principal para a sua distribuição inicial do Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d989-162">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="4d989-163">Se você não puder consolidar sua implantação do AD DS de várias florestas ou se estiver usando outros serviços de diretório para gerenciar identidades, talvez seja possível sincronizá-las com a ajuda da Microsoft ou de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="4d989-163">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="4d989-164">Confira [sincronização de diretórios de várias florestas com um cenário de logon único](https://go.microsoft.com/fwlink/p/?LinkId=525321) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="4d989-164">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="4d989-165">Recursos que dependem da sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="4d989-165">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="4d989-166">A sincronização de diretórios é necessária para os seguintes recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="4d989-166">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="4d989-167">Logon único (SSO) contínuo do Azure AD</span><span class="sxs-lookup"><span data-stu-id="4d989-167">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="4d989-168">Coexistência do Skype</span><span class="sxs-lookup"><span data-stu-id="4d989-168">Skype coexistence</span></span>
- <span data-ttu-id="4d989-169">Implantação híbrida do Exchange, incluindo:</span><span class="sxs-lookup"><span data-stu-id="4d989-169">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="4d989-170">GAL (lista de endereços global) totalmente compartilhada entre seu ambiente do Exchange local e o Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d989-170">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="4d989-171">Sincronizar informação de GAL de sistemas de email diferentes.</span><span class="sxs-lookup"><span data-stu-id="4d989-171">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="4d989-172">A capacidade de adicionar usuários e remover usuários das ofertas de serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d989-172">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="4d989-173">Isto exige o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4d989-173">This requires the following:</span></span>
  - <span data-ttu-id="4d989-174">A sincronização bidirecional deve ser configurada durante a configuração de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="4d989-174">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="4d989-175">Por padrão, as ferramentas de sincronização de diretório gravam informações de diretório somente na nuvem.</span><span class="sxs-lookup"><span data-stu-id="4d989-175">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="4d989-176">Ao configurar a sincronização bidirecional, você habilita a funcionalidade de write-back para que um número limitado de atributos de objeto seja copiado da nuvem e, em seguida, os escreveu novamente no AD DS local.</span><span class="sxs-lookup"><span data-stu-id="4d989-176">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="4d989-177">O Write-back também é conhecido como modo híbrido do Exchange.</span><span class="sxs-lookup"><span data-stu-id="4d989-177">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="4d989-178">Uma implantação híbrida local do Exchange</span><span class="sxs-lookup"><span data-stu-id="4d989-178">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="4d989-179">A capacidade de mover algumas caixas de correio do usuário para o Office 365 enquanto mantém outras caixas de correio do usuário no local.</span><span class="sxs-lookup"><span data-stu-id="4d989-179">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="4d989-180">Remetentes confiáveis e remetentes bloqueados no local são replicados para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d989-180">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="4d989-181">Delegação básica e funcionalidade de email enviar em nome de.</span><span class="sxs-lookup"><span data-stu-id="4d989-181">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="4d989-182">Você tem uma solução integrada de cartão inteligente ou de autenticação multifator no local.</span><span class="sxs-lookup"><span data-stu-id="4d989-182">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="4d989-183">Sincronização de fotos, miniaturas, salas de conferência e grupos de segurança</span><span class="sxs-lookup"><span data-stu-id="4d989-183">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="4d989-184">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="4d989-184">Next step</span></span>

<span data-ttu-id="4d989-185">Quando estiver pronto para implantar a identidade híbrida, confira [preparar para provisionar usuários](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="4d989-185">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  

