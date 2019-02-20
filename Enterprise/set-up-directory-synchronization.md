---
title: Configurar a sincronização de diretórios com o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
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
description: Saiba como configurar a sincronização de diretórios entre o Office 365 e o Active Directory local.
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085260"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="93898-103">Configurar a sincronização de diretórios com o Office 365</span><span class="sxs-lookup"><span data-stu-id="93898-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="93898-p101">O Office 365 usa o serviço de gerenciamento de identidade de usuário baseado em nuvem do Azure Active Directory para gerenciar usuários. Você também pode integrar seu Active Directory local com o Azure AD sincronizando seu ambiente local com o Office 365. Depois de configurar a sincronização, você pode optar por fazer com que a autenticação do usuário ocorra no AD do Azure ou no diretório local.</span><span class="sxs-lookup"><span data-stu-id="93898-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="93898-107">Sincronização de diretórios do Office 365</span><span class="sxs-lookup"><span data-stu-id="93898-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="93898-p102">Você pode usar identidade sincronizada ou identidade federada entre sua organização local e o Office 365. Com a identidade sincronizada, você gerencia os usuários locais e eles são autenticados pelo Azure AD quando eles usam a mesma senha na nuvem como local. Este é o cenário mais comum de sincronização de diretórios. A autenticação de passagem ou a identidade federada permite que você gerencie os usuários no local e eles são autenticados por seu diretório local. A identidade federada requer configuração adicional e permite que os usuários entrem apenas uma vez. Para obter detalhes, leia underStanding [Office 365 Identity e Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="93898-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="93898-114">Deseja atualizar da sincronização do Windows Azure Active Directory (dirSync) para o Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="93898-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="93898-115">Se você está usando o dirSync e deseja atualizar, vá para [Azure.com](https://azure.com) para obter [instruções de atualização](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="93898-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="93898-116">Pré-requisitos para o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="93898-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="93898-p103">Você recebe uma assinatura gratuita do Azure AD com sua assinatura do Office 365. Ao configurar a sincronização de diretórios, você instalará o Azure Active Directory Connect em um dos servidores locais.</span><span class="sxs-lookup"><span data-stu-id="93898-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="93898-119">Para o Office 365, você precisará:</span><span class="sxs-lookup"><span data-stu-id="93898-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="93898-120">Verifique seu domínio local (o procedimento o guiará por isso).</span><span class="sxs-lookup"><span data-stu-id="93898-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="93898-121">[Atribuir funções de administrador no office 365 para](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissões de negócios para o locatário do Office 365 e o Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="93898-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="93898-122">Para o servidor local no qual você instala o Azure AD Connect, você precisará do seguinte software:</span><span class="sxs-lookup"><span data-stu-id="93898-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="93898-123">**SISTEMA operacional do servidor**</span><span class="sxs-lookup"><span data-stu-id="93898-123">**Server OS**</span></span>|<span data-ttu-id="93898-124">**Outro software**</span><span class="sxs-lookup"><span data-stu-id="93898-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="93898-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="93898-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="93898-126">-O PowerShell é instalado por padrão, nenhuma ação é necessária.</span><span class="sxs-lookup"><span data-stu-id="93898-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="93898-p104">-NET 4.5.1 e versões posteriores são oferecidos por meio do Windows Update. Verifique se você instalou as atualizações mais recentes do Windows Server no painel de controle.</span><span class="sxs-lookup"><span data-stu-id="93898-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="93898-129">**Windows server 2008 R2 com Service Pack 1 (SP1)** ou **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="93898-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="93898-p105">– A versão mais recente do PowerShell está disponível no Windows Management Framework 4,0. Procure por ele no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="93898-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br> <span data-ttu-id="93898-132">– As versões do .NET 4.5.1 e posteriores estão disponíveis no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="93898-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="93898-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="93898-133">**Windows Server 2008**</span></span> | <span data-ttu-id="93898-134">– A versão com suporte mais recente do PowerShell está disponível no Windows Management Framework 3,0, disponível no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="93898-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="93898-135">– As versões do .NET 4.5.1 e posteriores estão disponíveis no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="93898-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="93898-p106">Se você estiver usando o dirSync do Azure Active Directory, o número máximo de membros do grupo de distribuição que você pode sincronizar de seu Active Directory local para o Azure Active Directory é 15.000. Para o Azure AD Connect, esse número é 50.000.</span><span class="sxs-lookup"><span data-stu-id="93898-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="93898-138">Para rever cuidadosamente os requisitos de hardware, software, conta e permissões, requisitos de certificado SSL e limites de objeto para o Azure AD Connect, leia os [pré-requisitos para o Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span><span class="sxs-lookup"><span data-stu-id="93898-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="93898-139">Você também pode analisar o histórico de versões da [versão](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) do Azure ad Connect para ver o que está incluído e corrigido em cada versão.</span><span class="sxs-lookup"><span data-stu-id="93898-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="93898-140">Para configurar a sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="93898-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="93898-141">entre no centro de administração do Office 365 e escolha usuários **ativos** do **usuário** \> no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="93898-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="93898-142">no centro de administração do Office 365, na página **usuários ativos** , escolha **mais** \> **sincronização de diretório**.</span><span class="sxs-lookup"><span data-stu-id="93898-142">In the Office 365 admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![No menu mais, escolha sincronização de diretório](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="93898-p107">Na página de **preparação do Active Directory** , selecione o link **baixar a ferramenta de conexão do Active Directory do Microsoft Azure** para começar. Para obter mais informações sobre o processo de instalação do Azure Active Directory Connect, consulte [Azure ad Connect e Azure ad Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="93898-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="93898-146">Atribuir licenças a usuários sincronizados</span><span class="sxs-lookup"><span data-stu-id="93898-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="93898-p108">Depois de sincronizar seus usuários com o Office 365, eles são criados, mas você precisa atribuir licenças a eles para que eles possam usar os recursos do Office 365, como email. Para obter instruções, consulte [assign licenses to Users in Office 365 for Business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span><span class="sxs-lookup"><span data-stu-id="93898-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="93898-149">Concluir a configuração dos domínios</span><span class="sxs-lookup"><span data-stu-id="93898-149">Finish setting up domains</span></span>

<span data-ttu-id="93898-150">Siga as etapas em [criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) para concluir a configuração dos seus domínios.</span><span class="sxs-lookup"><span data-stu-id="93898-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>