---
title: Implantar a sincronização de diretórios do Microsoft 365 no Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Resumo: implante o Azure AD Connect em uma máquina virtual no Azure para sincronizar as contas entre o seu diretório local e o locatário do Azure AD da sua assinatura do Microsoft 365.'
ms.openlocfilehash: 6f2da528293de54d21bd88b31fcd347cfab9335c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998059"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="faf9d-103">Implantar a sincronização de diretórios do Microsoft 365 no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="faf9d-103">Deploy Microsoft 365 Directory Synchronization in Microsoft Azure</span></span>

<span data-ttu-id="faf9d-104">O Azure Active Directory (Azure AD) Connect (anteriormente conhecido como a ferramenta de sincronização de diretório, a ferramenta de sincronização de diretório ou a ferramenta de DirSync.exe) é um aplicativo que você instala em um servidor associado a um domínio para sincronizar seus usuários do AD DS (serviços de domínio Active Directory) local para o locatário do Azure AD da sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-104">Azure Active Directory (Azure AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Active Directory Domain Services (AD DS) users to the Azure AD tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="faf9d-105">A Microsoft 365 usa o Azure AD para o serviço de diretório.</span><span class="sxs-lookup"><span data-stu-id="faf9d-105">Microsoft 365 uses Azure AD for its directory service.</span></span> <span data-ttu-id="faf9d-106">Sua assinatura do Microsoft 365 inclui um locatário do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="faf9d-106">Your Microsoft 365 subscription includes an Azure AD tenant.</span></span> <span data-ttu-id="faf9d-107">Esse locatário também pode ser usado para o gerenciamento de identidades da sua organização com outras cargas de trabalho de nuvem, incluindo outros aplicativos SaaS e aplicativos no Azure.</span><span class="sxs-lookup"><span data-stu-id="faf9d-107">This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="faf9d-108">Você pode instalar o Azure AD Connect em um servidor local, mas pode também instalá-lo em uma máquina virtual no Azure pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="faf9d-108">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="faf9d-109">Você pode provisionar e configurar servidores baseados na nuvem mais depressa, disponibilizando os serviços aos usuários com mais antecedência.</span><span class="sxs-lookup"><span data-stu-id="faf9d-109">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="faf9d-110">O Azure oferece melhor disponibilidade de sites com menos esforço.</span><span class="sxs-lookup"><span data-stu-id="faf9d-110">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="faf9d-111">Você pode reduzir o número de servidores locais em sua organização.</span><span class="sxs-lookup"><span data-stu-id="faf9d-111">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="faf9d-112">This solution requires connectivity between your on-premises network and your Azure virtual network.</span><span class="sxs-lookup"><span data-stu-id="faf9d-112">This solution requires connectivity between your on-premises network and your Azure virtual network.</span></span> <span data-ttu-id="faf9d-113">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="faf9d-113">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="faf9d-114">Este artigo descreve a sincronização de um único domínio em uma única floresta.</span><span class="sxs-lookup"><span data-stu-id="faf9d-114">This article describes synchronization of a single domain in a single forest.</span></span> <span data-ttu-id="faf9d-115">O Azure AD Connect sincroniza todos os domínios do AD DS em sua floresta do Active Directory com o Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-115">Azure AD Connect synchronizes all AD DS domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="faf9d-116">Se você tiver várias florestas do Active Directory para sincronizar com o Microsoft 365, confira [sincronização de diretórios com várias florestas com o cenário de logon único](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="faf9d-116">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a><span data-ttu-id="faf9d-117">Visão geral da implantação da sincronização de diretório do Microsoft 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="faf9d-117">Overview of deploying Microsoft 365 directory synchronization in Azure</span></span>

<span data-ttu-id="faf9d-118">O diagrama a seguir mostra o Azure AD Connect em execução em uma máquina virtual no Azure (o servidor de sincronização de diretório) que sincroniza uma floresta local do AD DS com uma assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-118">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises AD DS forest to a Microsoft 365 subscription.</span></span>
  
![A ferramenta Azure AD Connect em uma máquina virtual no Azure sincronizando contas locais para o locatário do Azure AD de uma assinatura do Microsoft 365 com fluxo de tráfego](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="faf9d-120">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection.</span><span class="sxs-lookup"><span data-stu-id="faf9d-120">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="faf9d-121">There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="faf9d-121">There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span> <span data-ttu-id="faf9d-122">There are two main traffic flows originating from the directory sync server:</span><span class="sxs-lookup"><span data-stu-id="faf9d-122">There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="faf9d-123">O Azure AD Connect consulta um controlador de domínio na rede local para detectar alterações em contas e senhas.</span><span class="sxs-lookup"><span data-stu-id="faf9d-123">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="faf9d-124">O Azure AD Connect envia as alterações para contas e senhas para a instância do Azure AD da sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-124">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Microsoft 365 subscription.</span></span> <span data-ttu-id="faf9d-125">Como o servidor de sincronização de diretório está em uma parte estendida da sua rede local, essas alterações são enviadas pelo servidor de proxy da rede local.</span><span class="sxs-lookup"><span data-stu-id="faf9d-125">Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="faf9d-126">Esta solução descreve a sincronização de um único domínio do Active Directory, uma única floresta do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="faf9d-126">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest.</span></span> <span data-ttu-id="faf9d-127">O Azure AD Connect sincroniza todos os domínios do Active Directory em sua floresta do Active Directory com o Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-127">Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="faf9d-128">Se você tiver várias florestas do Active Directory para sincronizar com o Microsoft 365, confira [sincronização de diretórios com várias florestas com o cenário de logon único](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="faf9d-128">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="faf9d-129">Há duas etapas principais quando você implanta essa solução:</span><span class="sxs-lookup"><span data-stu-id="faf9d-129">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="faf9d-130">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network.</span><span class="sxs-lookup"><span data-stu-id="faf9d-130">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network.</span></span> <span data-ttu-id="faf9d-131">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="faf9d-131">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="faf9d-132">Instale o [Azure ad Connect](https://www.microsoft.com/download/details.aspx?id=47594) em uma máquina virtual associada ao domínio no Azure e sincronize o AD DS local com o Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-132">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises AD DS to Microsoft 365.</span></span> <span data-ttu-id="faf9d-133">Isso envolve:</span><span class="sxs-lookup"><span data-stu-id="faf9d-133">This involves:</span></span>
    
    <span data-ttu-id="faf9d-134">Criar uma Máquina Virtual do Azure para executar o Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="faf9d-134">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="faf9d-135">Instalar e configurar o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="faf9d-135">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="faf9d-136">Configurar o Azure AD Connect requer as credenciais (nome de usuário e senha) de uma conta de administrador do Azure AD e uma conta de administrador corporativo do AD DS.</span><span class="sxs-lookup"><span data-stu-id="faf9d-136">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a AD DS enterprise administrator account.</span></span> <span data-ttu-id="faf9d-137">O Azure AD Connect é executado imediatamente e continuamente para sincronizar a floresta do AD DS local com o Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-137">Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises AD DS forest to Microsoft 365.</span></span>
    
<span data-ttu-id="faf9d-138">Antes de implantar essa solução em produção, você pode usar as instruções da [configuração de base corporativa simulada](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) para definir essa configuração como prova de conceito, para demonstrações ou para experimentos.</span><span class="sxs-lookup"><span data-stu-id="faf9d-138">Before you deploy this solution in production, you can use the instructions in [The simulated enterprise base configuration](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="faf9d-139">Quando a configuração do Azure AD Connect for concluída, ele não salvará as credenciais de conta de administrador corporativo do AD DS.</span><span class="sxs-lookup"><span data-stu-id="faf9d-139">When Azure AD Connect configuration completes, it does not save the AD DS enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="faf9d-140">Esta solução descreve a sincronização de uma única floresta do AD DS para o Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-140">This solution describes synchronizing a single AD DS forest to Microsoft 365.</span></span> <span data-ttu-id="faf9d-141">A topologia abordada neste artigo representa apenas uma das maneiras de implementar essa solução.</span><span class="sxs-lookup"><span data-stu-id="faf9d-141">The topology discussed in this article represents only one way to implement this solution.</span></span> <span data-ttu-id="faf9d-142">A topologia de sua organização pode ser diferente, com base em requisitos de rede e considerações de segurança exclusivos.</span><span class="sxs-lookup"><span data-stu-id="faf9d-142">Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a><span data-ttu-id="faf9d-143">Planejar a hospedagem de um servidor de sincronização de diretório para o Microsoft 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="faf9d-143">Plan for hosting a directory sync server for Microsoft 365 in Azure</span></span>
<span data-ttu-id="faf9d-144"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="faf9d-144"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="faf9d-145">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="faf9d-145">Prerequisites</span></span>

<span data-ttu-id="faf9d-146">Antes de começar, examine os seguintes pré-requisitos para essa solução:</span><span class="sxs-lookup"><span data-stu-id="faf9d-146">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="faf9d-147">Examine o conteúdo de planejamento relacionado em [Planejar sua rede virtual do Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span><span class="sxs-lookup"><span data-stu-id="faf9d-147">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="faf9d-148">Verifique se você atende a todos os [pré-requisitos](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) para configurar a Rede Virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="faf9d-148">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="faf9d-149">Ter uma assinatura do Microsoft 365 que inclua o recurso integração com o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="faf9d-149">Have a Microsoft 365 subscription that includes the Active Directory integration feature.</span></span> <span data-ttu-id="faf9d-150">Para obter informações sobre assinaturas do Microsoft 365, vá para a [página de assinatura do microsoft 365](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span><span class="sxs-lookup"><span data-stu-id="faf9d-150">For information about Microsoft 365 subscriptions, go to the [Microsoft 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="faf9d-151">Provisione uma máquina virtual do Azure que executa o Azure AD Connect para sincronizar sua floresta do AD DS local com o Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-151">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises AD DS forest with Microsoft 365.</span></span>
    
    <span data-ttu-id="faf9d-152">Você deve ter as credenciais (nomes e senhas) para a conta de administrador corporativo do AD DS e uma conta de Administrador do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="faf9d-152">You must have the credentials (names and passwords) for a AD DS enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="faf9d-153">Suposições de design de arquitetura da solução</span><span class="sxs-lookup"><span data-stu-id="faf9d-153">Solution architecture design assumptions</span></span>

<span data-ttu-id="faf9d-154">A lista a seguir descreve as opções de design feitas para essa solução.</span><span class="sxs-lookup"><span data-stu-id="faf9d-154">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="faf9d-155">This solution uses a single Azure virtual network with a site-to-site VPN connection.</span><span class="sxs-lookup"><span data-stu-id="faf9d-155">This solution uses a single Azure virtual network with a site-to-site VPN connection.</span></span> <span data-ttu-id="faf9d-156">The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="faf9d-156">The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="faf9d-157">Na rede local, existem servidores DNS e um controlador de domínio.</span><span class="sxs-lookup"><span data-stu-id="faf9d-157">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="faf9d-158">Azure AD Connect performs password hash synchronization instead of single sign-on.</span><span class="sxs-lookup"><span data-stu-id="faf9d-158">Azure AD Connect performs password hash synchronization instead of single sign-on.</span></span> <span data-ttu-id="faf9d-159">You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure.</span><span class="sxs-lookup"><span data-stu-id="faf9d-159">You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure.</span></span> <span data-ttu-id="faf9d-160">To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).</span><span class="sxs-lookup"><span data-stu-id="faf9d-160">To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="faf9d-161">There are additional design choices that you might consider when you deploy this solution in your environment.</span><span class="sxs-lookup"><span data-stu-id="faf9d-161">There are additional design choices that you might consider when you deploy this solution in your environment.</span></span> <span data-ttu-id="faf9d-162">These include the following:</span><span class="sxs-lookup"><span data-stu-id="faf9d-162">These include the following:</span></span>
  
- <span data-ttu-id="faf9d-163">Se houver servidores DNS em uma rede virtual existente do Azure, determine se você deseja que seu servidor de sincronização de diretório os use para resolução de nomes em vez dos servidores DNS da rede local.</span><span class="sxs-lookup"><span data-stu-id="faf9d-163">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="faf9d-164">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you.</span><span class="sxs-lookup"><span data-stu-id="faf9d-164">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you.</span></span> <span data-ttu-id="faf9d-165">The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span><span class="sxs-lookup"><span data-stu-id="faf9d-165">The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="faf9d-166">Roteiro de implantação</span><span class="sxs-lookup"><span data-stu-id="faf9d-166">Deployment roadmap</span></span>

<span data-ttu-id="faf9d-167">A implantação do Azure AD Connect em uma máquina virtual no Azure tem três etapas:</span><span class="sxs-lookup"><span data-stu-id="faf9d-167">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="faf9d-168">Fase 1: Criar e configurar a rede virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="faf9d-168">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="faf9d-169">Fase 2: Criar e configurar a máquina virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="faf9d-169">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="faf9d-170">Fase 3: Instalar e configurar o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="faf9d-170">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="faf9d-171">Após a implantação, você também deve atribuir locais e licenças para as novas contas de usuário no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="faf9d-171">After deployment, you must also assign locations and licenses for the new user accounts in Microsoft 365.</span></span>


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="faf9d-172">Fase 1: Criar e configurar a rede virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="faf9d-172">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="faf9d-173">Para criar e configurar a rede virtual do Azure, conclua a [Fase 1: preparar sua rede local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) e a [Fase 2: criar a rede virtual entre locais no Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) no roteiro de implantação de [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="faf9d-173">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="faf9d-174">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="faf9d-174">This is your resulting configuration.</span></span>
  
![Fase 1 do servidor de sincronização de diretório para o Microsoft 365 hospedado no Azure](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="faf9d-176">Esta figura mostra uma rede local conectada a uma rede virtual do Azure por meio de uma conexão VPN ou ExpressRoute de site a site.</span><span class="sxs-lookup"><span data-stu-id="faf9d-176">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="faf9d-177">Fase 2: Criar e configurar a máquina virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="faf9d-177">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="faf9d-178">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span><span class="sxs-lookup"><span data-stu-id="faf9d-178">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span></span> <span data-ttu-id="faf9d-179">Use the following settings:</span><span class="sxs-lookup"><span data-stu-id="faf9d-179">Use the following settings:</span></span>
  
- <span data-ttu-id="faf9d-180">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network.</span><span class="sxs-lookup"><span data-stu-id="faf9d-180">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network.</span></span> <span data-ttu-id="faf9d-181">Record the user name and password in a secure location.</span><span class="sxs-lookup"><span data-stu-id="faf9d-181">Record the user name and password in a secure location.</span></span> <span data-ttu-id="faf9d-182">You will need these later to connect to the virtual machine.</span><span class="sxs-lookup"><span data-stu-id="faf9d-182">You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="faf9d-183">No painel **Escolher um tamanho**, escolha o tamanho **A2 Padrão**.</span><span class="sxs-lookup"><span data-stu-id="faf9d-183">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="faf9d-184">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type.</span><span class="sxs-lookup"><span data-stu-id="faf9d-184">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type.</span></span> <span data-ttu-id="faf9d-185">In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet).</span><span class="sxs-lookup"><span data-stu-id="faf9d-185">In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet).</span></span> <span data-ttu-id="faf9d-186">Leave all other settings at their default values.</span><span class="sxs-lookup"><span data-stu-id="faf9d-186">Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="faf9d-187">Para conferir se o servidor de sincronização de diretório está usando o DNS corretamente, verifique o DNS interno para garantir que um registro de endereço (A) foi adicionado à máquina virtual com o respectivo endereço IP.</span><span class="sxs-lookup"><span data-stu-id="faf9d-187">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="faf9d-188">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection.</span><span class="sxs-lookup"><span data-stu-id="faf9d-188">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection.</span></span> <span data-ttu-id="faf9d-189">After signing in, join the virtual machine to the on-premises AD DS domain.</span><span class="sxs-lookup"><span data-stu-id="faf9d-189">After signing in, join the virtual machine to the on-premises AD DS domain.</span></span>
  
<span data-ttu-id="faf9d-190">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server.</span><span class="sxs-lookup"><span data-stu-id="faf9d-190">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server.</span></span> <span data-ttu-id="faf9d-191">You should contact your network administrator for any additional configuration steps to perform.</span><span class="sxs-lookup"><span data-stu-id="faf9d-191">You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="faf9d-192">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="faf9d-192">This is your resulting configuration.</span></span>
  
![Fase 2 do servidor de sincronização de diretório para o Microsoft 365 hospedado no Azure](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="faf9d-194">Esta figura mostra a máquina virtual do servidor de sincronização de diretório na rede virtual entre locais do Azure.</span><span class="sxs-lookup"><span data-stu-id="faf9d-194">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="faf9d-195">Fase 3: Instalar e configurar o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="faf9d-195">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="faf9d-196">Faça o procedimento a seguir:</span><span class="sxs-lookup"><span data-stu-id="faf9d-196">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="faf9d-197">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges.</span><span class="sxs-lookup"><span data-stu-id="faf9d-197">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges.</span></span> <span data-ttu-id="faf9d-198">See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).</span><span class="sxs-lookup"><span data-stu-id="faf9d-198">See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).</span></span>
    
2. <span data-ttu-id="faf9d-199">No servidor de sincronização de diretório, abra o artigo [Configurar a sincronização de diretório para o Microsoft 365](set-up-directory-synchronization.md) e siga as instruções para a sincronização de diretório com a sincronização de hash de senha.</span><span class="sxs-lookup"><span data-stu-id="faf9d-199">From the directory sync server, open the [Set up directory synchronization for Microsoft 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="faf9d-200">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU).</span><span class="sxs-lookup"><span data-stu-id="faf9d-200">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU).</span></span> <span data-ttu-id="faf9d-201">Do not move or remove this account or synchronization will fail.</span><span class="sxs-lookup"><span data-stu-id="faf9d-201">Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="faf9d-202">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="faf9d-202">This is your resulting configuration.</span></span>
  
![Fase 3 do servidor de sincronização de diretório para o Microsoft 365 hospedado no Azure](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="faf9d-204">Esta figura mostra o servidor de sincronização de diretório com o Azure AD Connect na rede virtual entre locais do Azure.</span><span class="sxs-lookup"><span data-stu-id="faf9d-204">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a><span data-ttu-id="faf9d-205">Atribuir locais e licenças aos usuários no Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="faf9d-205">Assign locations and licenses to users in Microsoft 365</span></span>

<span data-ttu-id="faf9d-206">O Azure AD Connect adiciona contas à sua assinatura do Microsoft 365 do AD DS local, mas, para que os usuários entrem no Microsoft 365 e usem seus serviços, as contas devem ser configuradas com um local e licenças.</span><span class="sxs-lookup"><span data-stu-id="faf9d-206">Azure AD Connect adds accounts to your Microsoft 365 subscription from the on-premises AD DS, but in order for users to sign in to Microsoft 365 and use its services, the accounts must be configured with a location and licenses.</span></span> <span data-ttu-id="faf9d-207">Use essas etapas para adicionar o local e as licenças ativas às devidas contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="faf9d-207">Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="faf9d-208">Entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com)e, em seguida, clique em **administrador**.</span><span class="sxs-lookup"><span data-stu-id="faf9d-208">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="faf9d-209">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="faf9d-209">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="faf9d-210">Na lista das contas de usuário, marque a caixa de seleção ao lado do usuário que você deseja ativar.</span><span class="sxs-lookup"><span data-stu-id="faf9d-210">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="faf9d-211">Na página do usuário, clique em **Editar** para **Licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="faf9d-211">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="faf9d-212">Na página **Licenças de produto**, selecione um local para o usuário em **Local** e habilite as licenças apropriadas para ele.</span><span class="sxs-lookup"><span data-stu-id="faf9d-212">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="faf9d-213">Ao concluir, clique em **Salvar** e, em seguida, clique em **Fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="faf9d-213">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="faf9d-214">Volte à etapa 3 para usuários adicionais.</span><span class="sxs-lookup"><span data-stu-id="faf9d-214">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="faf9d-215">Confira também</span><span class="sxs-lookup"><span data-stu-id="faf9d-215">See also</span></span>

[<span data-ttu-id="faf9d-216">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="faf9d-216">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)
  
[<span data-ttu-id="faf9d-217">Conectar uma rede local a uma rede virtual do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="faf9d-217">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="faf9d-218">Baixar o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="faf9d-218">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="faf9d-219">Configurar a sincronização de diretórios para o Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="faf9d-219">Set up directory synchronization for Microsoft 365</span></span>](set-up-directory-synchronization.md)
  
