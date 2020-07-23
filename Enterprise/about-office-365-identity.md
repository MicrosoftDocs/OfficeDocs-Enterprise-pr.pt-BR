---
title: Modelos de identidade do Microsoft 365 e Active Directory do Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 06/09/2020
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Saiba como a identidade do usuário é gerenciada no Microsoft 365.
ms.openlocfilehash: e473a6397cb0b2fc7a2b81ab7a959a4ccdda400b
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230057"
---
# <a name="microsoft-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="2347e-103">Modelos de identidade do Microsoft 365 e Active Directory do Azure</span><span class="sxs-lookup"><span data-stu-id="2347e-103">Microsoft 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="2347e-104">*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="2347e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="2347e-105">O Microsoft 365 usa o Azure Active Directory (Azure AD), um serviço de autenticação e identidade do usuário baseado na nuvem que está incluído na assinatura do Microsoft 365, para gerenciar identidades e autenticação para o Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-105">Microsoft 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Microsoft 365 subscription, to manage identities and authentication for Microsoft 365.</span></span> <span data-ttu-id="2347e-106">Obter sua infraestrutura de identidade configurada corretamente é vital para gerenciar o acesso de usuário e permissões do Microsoft 365 para sua organização.</span><span class="sxs-lookup"><span data-stu-id="2347e-106">Getting your identity infrastructure configured correctly is vital to managing Microsoft 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="2347e-107">Antes de começar, assista a este vídeo para ter uma visão geral dos modelos de identidade e autenticação do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-107">Before you begin, watch this video for an overview of identity models and authentication for Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="2347e-108">Sua primeira opção de planejamento é o modelo de identidade do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-108">Your first planning choice is the Microsoft 365 identity model.</span></span>

## <a name="microsoft-365-identity-models"></a><span data-ttu-id="2347e-109">Modelos de identidade do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="2347e-109">Microsoft 365 identity models</span></span>

<span data-ttu-id="2347e-110">Para planejar contas de usuário, primeiro você precisa entender os dois modelos de identidade no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-110">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="2347e-111">Você pode manter as identidades da sua organização apenas na nuvem ou pode manter suas identidades do AD DS (serviços de domínio Active Directory) locais e usá-las para autenticação quando os usuários acessarem os serviços de nuvem do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-111">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="2347e-112">Estes são os dois tipos de identidade e seus benefícios e melhores necessidades.</span><span class="sxs-lookup"><span data-stu-id="2347e-112">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="2347e-113">**Identidade somente na nuvem**</span><span class="sxs-lookup"><span data-stu-id="2347e-113">**Cloud-only identity**</span></span> | <span data-ttu-id="2347e-114">**Identidade híbrida**</span><span class="sxs-lookup"><span data-stu-id="2347e-114">**Hybrid identity**</span></span> |
| <span data-ttu-id="2347e-115">**Definição**</span><span class="sxs-lookup"><span data-stu-id="2347e-115">**Definition**</span></span> | <span data-ttu-id="2347e-116">A conta de usuário existe somente no locatário do Azure AD para sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-116">User account only exists in the Azure AD tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="2347e-117">A conta de usuário existe no AD DS e uma cópia também está no locatário do Azure AD para sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-117">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="2347e-118">A conta de usuário no Azure AD também pode incluir uma versão de hash da senha da conta de usuário do AD DS já codificada.</span><span class="sxs-lookup"><span data-stu-id="2347e-118">The user account in Azure AD might also include a hashed version of the already hashed AD DS user account password.</span></span> |
| <span data-ttu-id="2347e-119">**Como o Microsoft 365 autentica as credenciais do usuário**</span><span class="sxs-lookup"><span data-stu-id="2347e-119">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="2347e-120">O locatário do Azure AD para sua assinatura do Microsoft 365 realiza a autenticação com a conta de identidade de nuvem.</span><span class="sxs-lookup"><span data-stu-id="2347e-120">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="2347e-121">O locatário do Azure AD para sua assinatura do Microsoft 365 manipula o processo de autenticação ou redireciona o usuário para outro provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="2347e-121">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="2347e-122">**Melhor para**</span><span class="sxs-lookup"><span data-stu-id="2347e-122">**Best for**</span></span> | <span data-ttu-id="2347e-123">Organizações que não têm ou precisam de um AD DS local.</span><span class="sxs-lookup"><span data-stu-id="2347e-123">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="2347e-124">Organizações que usam o AD DS ou outro provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="2347e-124">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="2347e-125">**Melhor benefício**</span><span class="sxs-lookup"><span data-stu-id="2347e-125">**Greatest benefit**</span></span> | <span data-ttu-id="2347e-126">Simples de usar.</span><span class="sxs-lookup"><span data-stu-id="2347e-126">Simple to use.</span></span> <span data-ttu-id="2347e-127">Não é necessária nenhuma ferramenta ou servidor de diretório extra.</span><span class="sxs-lookup"><span data-stu-id="2347e-127">No extra directory tools or servers required.</span></span> | <span data-ttu-id="2347e-128">Os usuários podem usar as mesmas credenciais ao acessar recursos locais ou baseados em nuvem.</span><span class="sxs-lookup"><span data-stu-id="2347e-128">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="2347e-129">Identidade somente na nuvem</span><span class="sxs-lookup"><span data-stu-id="2347e-129">Cloud-only identity</span></span>

<span data-ttu-id="2347e-130">Uma identidade somente na nuvem usa contas de usuário que existem somente no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2347e-130">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="2347e-131">A identidade em nuvem é normalmente usada por pequenas organizações que não têm servidores locais ou não usam o AD DS para gerenciar identidades locais.</span><span class="sxs-lookup"><span data-stu-id="2347e-131">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="2347e-132">Estes são os componentes básicos da identidade somente na nuvem.</span><span class="sxs-lookup"><span data-stu-id="2347e-132">Here are the basic components of cloud-only identity.</span></span>
 
![Componentes básicos da identidade somente na nuvem](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="2347e-134">Os usuários locais e remotos (online) usam suas contas de usuário e senhas do Azure AD para acessar os serviços de nuvem da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-134">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Microsoft 365 cloud services.</span></span> <span data-ttu-id="2347e-135">O Azure AD autentica as credenciais do usuário com base em suas contas de usuário e senhas armazenadas.</span><span class="sxs-lookup"><span data-stu-id="2347e-135">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="2347e-136">Administração</span><span class="sxs-lookup"><span data-stu-id="2347e-136">Administration</span></span>
<span data-ttu-id="2347e-137">Como as contas de usuário são armazenadas apenas no Azure AD, você gerencia identidades de nuvem com ferramentas como o [centro de administração do Microsoft 365](https://admin.microsoft.com) e o [Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-user-accounts-and-licenses-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="2347e-137">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and [Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-user-accounts-and-licenses-with-office-365-powershell).</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="2347e-138">Identidade híbrida</span><span class="sxs-lookup"><span data-stu-id="2347e-138">Hybrid identity</span></span>

<span data-ttu-id="2347e-139">A identidade híbrida usa contas originadas em um AD DS local e ter uma cópia no locatário do Azure AD de uma assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2347e-139">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="2347e-140">No entanto, a maioria das alterações só flui de uma forma.</span><span class="sxs-lookup"><span data-stu-id="2347e-140">However, most changes only flow one way.</span></span> <span data-ttu-id="2347e-141">As alterações feitas nas contas de usuário do AD DS são sincronizadas com sua cópia no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2347e-141">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="2347e-142">Mas as alterações feitas nas contas baseadas em nuvem no Azure AD, como novas contas de usuário, não são sincronizadas com o AD DS.</span><span class="sxs-lookup"><span data-stu-id="2347e-142">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="2347e-143">O Azure AD Connect fornece a sincronização de contas contínuas.</span><span class="sxs-lookup"><span data-stu-id="2347e-143">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="2347e-144">Ele é executado em um servidor local, verifica as alterações no AD DS e encaminha essas alterações para o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2347e-144">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="2347e-145">O Azure AD Connect oferece a capacidade de filtrar quais contas estão sincronizadas e se deve sincronizar uma versão de hash de senhas de usuário, conhecida como sincronização de hash de senha (PHS).</span><span class="sxs-lookup"><span data-stu-id="2347e-145">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="2347e-146">Ao implementar a identidade híbrida, seu AD DS local é a fonte autoritativa de informações da conta.</span><span class="sxs-lookup"><span data-stu-id="2347e-146">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="2347e-147">Isso significa que você realiza tarefas de administração principalmente no local, que são então sincronizadas com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2347e-147">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="2347e-148">Estes são os componentes da identidade híbrida.</span><span class="sxs-lookup"><span data-stu-id="2347e-148">Here are the components of hybrid identity.</span></span>

![Componentes da identidade híbrida](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="2347e-150">O locatário do Azure AD tem uma cópia das contas do AD DS.</span><span class="sxs-lookup"><span data-stu-id="2347e-150">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="2347e-151">Nessa configuração, os usuários locais e remotos que acessam o Microsoft 365 Cloud Services são autenticados no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2347e-151">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="2347e-152">Você sempre precisa usar o Azure AD Connect para sincronizar contas de usuário para identidade híbrida.</span><span class="sxs-lookup"><span data-stu-id="2347e-152">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="2347e-153">Você precisa das contas de usuário sincronizadas no Azure AD para realizar a atribuição de licença e o gerenciamento de grupo, configurar permissões e outras tarefas administrativas que envolvem contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="2347e-153">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="2347e-154">Administração</span><span class="sxs-lookup"><span data-stu-id="2347e-154">Administration</span></span>

<span data-ttu-id="2347e-155">Como as contas de usuário originais e autoritativas são armazenadas no AD DS local, você gerencia suas identidades com as mesmas ferramentas que o AD DS, como a ferramenta usuários e computadores do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2347e-155">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="2347e-156">Você não usa o centro de administração do Microsoft 365 ou o PowerShell para a Microsoft 365 para gerenciar contas de usuário sincronizadas no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2347e-156">You don’t use the Microsoft 365 admin center or PowerShell for Microsoft 365 to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="2347e-157">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="2347e-157">Next step</span></span>

<span data-ttu-id="2347e-158">Se você precisar do modelo de identidade somente na nuvem, confira [identidade somente na nuvem](cloud-only-identities.md).</span><span class="sxs-lookup"><span data-stu-id="2347e-158">If you need the cloud-only identity model, see [Cloud-only identity](cloud-only-identities.md).</span></span>

<span data-ttu-id="2347e-159">Se você precisar do modelo de identidade híbrida, consulte [identidade híbrida](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="2347e-159">If you need the hybrid identity model, see [Hybrid identity](plan-for-directory-synchronization.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="2347e-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="2347e-160">See also</span></span>

[<span data-ttu-id="2347e-161">Visão geral do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="2347e-161">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
