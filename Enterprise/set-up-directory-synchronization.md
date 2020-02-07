---
title: Configurar a sincronização de diretório no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Saiba como configurar a sincronização de diretório entre o Office 365 e o seu Active Directory local.
ms.openlocfilehash: d549d2b56ef1d642e5dfc16b747e6eb909dd7337
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844042"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="9e38f-103">Configurar a sincronização de diretório no Office 365</span><span class="sxs-lookup"><span data-stu-id="9e38f-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="9e38f-104">*Esse artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="9e38f-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="9e38f-105">O Office 365 usa um inquilino do Azure Active Directory (Azure AD) para armazenar e gerenciar identidades para autenticação e permissões para acessar recursos baseados em nuvem.</span><span class="sxs-lookup"><span data-stu-id="9e38f-105">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="9e38f-106">Se você tiver um Active Directory Domain Services (AD DS) local, poderá sincronizar suas contas de usuário, grupos e contatos do AD DS com o inquilino do Azure AD de sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e38f-106">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="9e38f-107">Esta é uma identidade híbrida do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e38f-107">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="9e38f-108">Estes são seus componentes.</span><span class="sxs-lookup"><span data-stu-id="9e38f-108">Here are its components.</span></span>

![Componentes da sincronização de diretórios para o Office 365](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="9e38f-110">O Azure AD Connect é executado em um servidor local e sincroniza seu AD DS com o locatário do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="9e38f-110">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="9e38f-111">Juntamente com a sincronização de diretórios, você também pode especificar estas opções de autenticação:</span><span class="sxs-lookup"><span data-stu-id="9e38f-111">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="9e38f-112">Sincronização de hash de senha (PHS)</span><span class="sxs-lookup"><span data-stu-id="9e38f-112">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="9e38f-113">O Azure AD realiza a própria autenticação.</span><span class="sxs-lookup"><span data-stu-id="9e38f-113">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="9e38f-114">Autenticação de passagem (PTA)</span><span class="sxs-lookup"><span data-stu-id="9e38f-114">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="9e38f-115">O Azure AD faz o AD DS executar a autenticação.</span><span class="sxs-lookup"><span data-stu-id="9e38f-115">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="9e38f-116">Autenticação federada</span><span class="sxs-lookup"><span data-stu-id="9e38f-116">Federated authentication</span></span>

  <span data-ttu-id="9e38f-117">O Azure AD redireciona o computador cliente que solicita autenticação para entrar em contato com outro provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="9e38f-117">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="9e38f-118">Confira [Identidades híbridas](plan-for-directory-synchronization.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9e38f-118">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="9e38f-119">1. Revisar os pré-requisitos para o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="9e38f-119">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="9e38f-120">Você recebe uma assinatura gratuita do Azure AD com a sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e38f-120">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="9e38f-121">Ao configurar a sincronização de diretórios, você instalará o Azure AD Connect em um dos servidores locais.</span><span class="sxs-lookup"><span data-stu-id="9e38f-121">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="9e38f-122">Para o Office 365, é necessário:</span><span class="sxs-lookup"><span data-stu-id="9e38f-122">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="9e38f-123">Verificar o seu domínio local.</span><span class="sxs-lookup"><span data-stu-id="9e38f-123">Verify your on-premises domain.</span></span> <span data-ttu-id="9e38f-124">O assistente do Azure AD Connect orientará você sobre isso.</span><span class="sxs-lookup"><span data-stu-id="9e38f-124">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="9e38f-125">Obtenha os nomes de usuário e senhas para as contas de administrador do seu locatário do Office 365 e do AD DS.</span><span class="sxs-lookup"><span data-stu-id="9e38f-125">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="9e38f-126">Para o servidor local no qual você instala o Azure AD Connect, será necessário:</span><span class="sxs-lookup"><span data-stu-id="9e38f-126">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="9e38f-127">**Sistema operacional do servidor**</span><span class="sxs-lookup"><span data-stu-id="9e38f-127">**Server OS**</span></span>|<span data-ttu-id="9e38f-128">**Outro software**</span><span class="sxs-lookup"><span data-stu-id="9e38f-128">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9e38f-129">Windows Server 2012 R2 e posterior</span><span class="sxs-lookup"><span data-stu-id="9e38f-129">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="9e38f-130">- O PowerShell é instalado por padrão, nenhuma ação é necessária.</span><span class="sxs-lookup"><span data-stu-id="9e38f-130">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="9e38f-131">- O Net 4.5.1 e as versões posteriores são oferecidos por meio do Windows Update.</span><span class="sxs-lookup"><span data-stu-id="9e38f-131">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="9e38f-132">Verifique se você instalou as atualizações mais recentes para o Windows Server no Painel de Controle.</span><span class="sxs-lookup"><span data-stu-id="9e38f-132">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="9e38f-133">Windows Server 2008 R2 com Service Pack 1 (SP1)\*\* ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="9e38f-133">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="9e38f-134">- A versão mais recente do PowerShell está disponível no Windows Management Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="9e38f-134">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="9e38f-135">Procure por ela no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="9e38f-135">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="9e38f-136">- O .NET 4.5.1 e as versões posteriores estão disponíveis no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="9e38f-136">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="9e38f-137">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="9e38f-137">Windows Server 2008</span></span> | <span data-ttu-id="9e38f-138">- A última versão do Windows PowerShell com suporte está disponível no Windows Management Framework 3.0, disponível no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="9e38f-138">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="9e38f-139">- O .NET 4.5.1 e as versões posteriores estão disponíveis no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="9e38f-139">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="9e38f-140">Confira [Pré-requisitos para o Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) para obter detalhes sobre requisitos de hardware, software, conta e permissões, requisitos de certificado SSL e limites de objetos para o Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="9e38f-140">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="9e38f-141">Também é possível examinar o [histórico de versões de lançamento](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) do Azure AD Connect para ver o que está incluído e o que foi corrigido em cada versão.</span><span class="sxs-lookup"><span data-stu-id="9e38f-141">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="9e38f-142">2. Instalar o Azure AD Connect e configurar a sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="9e38f-142">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="9e38f-143">Antes de começar, verifique se você tem:</span><span class="sxs-lookup"><span data-stu-id="9e38f-143">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="9e38f-144">O nome de usuário e senha de um administrador global do Office 365</span><span class="sxs-lookup"><span data-stu-id="9e38f-144">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="9e38f-145">O nome de usuário e senha de um administrador de domínio do AD DS</span><span class="sxs-lookup"><span data-stu-id="9e38f-145">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="9e38f-146">Qual método de autenticação (PHS, PTA, federado)</span><span class="sxs-lookup"><span data-stu-id="9e38f-146">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="9e38f-147">Se você deseja usar o [Logon Único Contínuo (SSO) do Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="9e38f-147">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="9e38f-148">Siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="9e38f-148">Follow these steps:</span></span>

1. <span data-ttu-id="9e38f-149">Entre no [centro de administração do Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) e escolha **Usuários** \> **Usuários Ativos** na navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="9e38f-149">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="9e38f-150">Na página **usuários ativos** , escolha **mais** (três pontos) \> **sincronização de diretório**.</span><span class="sxs-lookup"><span data-stu-id="9e38f-150">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="9e38f-151">Na página de **preparação do Azure Active Directory** , selecione a guia **vá para o centro de download para obter o link da ferramenta Azure ad Connect** para começar.</span><span class="sxs-lookup"><span data-stu-id="9e38f-151">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="9e38f-152">Siga as etapas no [roteiro de instalação do Azure AD Connect e do Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="9e38f-152">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="9e38f-153">3. Concluir a configuração dos domínios</span><span class="sxs-lookup"><span data-stu-id="9e38f-153">3. Finish setting up domains</span></span>

<span data-ttu-id="9e38f-154">Siga as etapas em [Criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) para concluir a configuração dos seus domínios.</span><span class="sxs-lookup"><span data-stu-id="9e38f-154">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="9e38f-155">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="9e38f-155">Next step</span></span>

[<span data-ttu-id="9e38f-156">Atribuir licenças às contas de usuário</span><span class="sxs-lookup"><span data-stu-id="9e38f-156">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
