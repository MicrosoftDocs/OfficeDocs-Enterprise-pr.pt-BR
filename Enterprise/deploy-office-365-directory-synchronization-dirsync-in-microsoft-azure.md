---
title: "Implantar a DirSync (sincronização de diretórios) do Office 365 no Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: "Resumo: implante o Azure AD Connect (DirSync) em uma máquina virtual no Azure para sincronizar as contas entre o diretório local e o locatário do Azure AD da sua assinatura do Office 365."
ms.openlocfilehash: 3bfcf11ed59ca355f661434fcb171835aae2c80b
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure"></a><span data-ttu-id="a8ff7-103">Implantar a DirSync (sincronização de diretórios) do Office 365 no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-103">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>

 <span data-ttu-id="a8ff7-104">**Resumo:** implante o Azure AD Connect (DirSync) em uma máquina virtual no Azure para sincronizar as contas entre o diretório local e o locatário do Azure AD da sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-104">**Summary:** Deploy Azure AD Connect (DirSync) on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="a8ff7-p101">O Azure Active Directory (AD) Connect (também conhecido como Ferramenta de Sincronização de Diretório ou ferramenta DirSync.exe) é um aplicativo baseado em servidor que você instala em um servidor associado ao domínio para sincronizar os usuários locais do Windows Server Active Directory com o locatário do Azure Active Directory da sua assinatura do Office 365. Você pode instalar o Azure AD Connect em um servidor local, mas pode também instalá-lo em uma máquina virtual no Azure pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="a8ff7-107">Você pode provisionar e configurar servidores baseados na nuvem mais depressa, disponibilizando os serviços aos usuários com mais antecedência.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="a8ff7-108">O Azure oferece melhor disponibilidade de sites com menos esforço.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="a8ff7-109">Você pode reduzir o número de servidores locais em sua organização.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="a8ff7-p102">Essa solução requer conectividade entre sua rede local e sua Rede Virtual do Azure. Saiba mais em [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="a8ff7-p103">Este artigo descreve a sincronização de um único domínio em uma única floresta. O Azure AD Connect sincroniza todos os domínios do AD do Windows Server na sua floresta do Active Directory com o Office 365. Se você tiver várias florestas do Active Directory para sincronizar com o Office 365, confira [Cenário de Sincronização de Diretório de Várias Florestas com Logon Único](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="a8ff7-p104">O Office 365 usa o Azure Active Directory (AD do Azure) para o serviço de diretório. Sua assinatura do Office 365 inclui um locatário do AD do Azure. Esse locatário também pode ser usado para o gerenciamento de identidades da sua organização com outras cargas de trabalho de nuvem, inclusive outros aplicativos SaaS e aplicativos no Azure.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="a8ff7-118">Visão geral da implantação da sincronização de diretório do Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="a8ff7-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="a8ff7-119"><a name="Overview"> </a></span></span>

<span data-ttu-id="a8ff7-120">O diagrama a seguir mostra o Azure AD Connect Health em execução em uma máquina virtual do Azure (o servidor DirSync) que sincroniza uma floresta local do AD do Windows Server com uma assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-120">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the DirSync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Ferramenta Azure AD Connect em uma máquina virtual no Azure sincronizando contas locais para o locatário do Azure AD de uma assinatura do Office 365 com o fluxo de tráfego local](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="a8ff7-p105">No diagrama, há duas redes conectadas por meio de uma conexão VPN site a site ou ExpressRoute. Há uma rede local em que os controladores de domínio do AD do Windows Server estão localizados e há uma rede virtual do Azure com um servidor DirSync, uma máquina virtual que executa o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Existem dois fluxos de tráfego principais provenientes do servidor DirSync:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a DirSync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the DirSync server:</span></span>
  
-  <span data-ttu-id="a8ff7-125">O Azure AD Connect consulta um controlador de domínio na rede local para detectar alterações em contas e senhas.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="a8ff7-p106">O Azure AD Connect envia as alterações nas contas e senhas à instância do AD do Azure da sua assinatura do Office 365. Como o servidor DirSync está em uma parte estendida da sua rede local, essas alterações são enviadas pelo servidor proxy da rede local.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the DirSync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="a8ff7-p107">Esta solução descreve a sincronização de um único domínio do Active Directory, uma única floresta do Active Directory. O Azure AD Connect sincroniza todos os domínios do Active Directory na sua floresta do Active Directory com o Office 365. Se você tiver várias florestas do Active Directory para sincronizar com o Office 365, confira [Cenário de Sincronização de Diretório de Várias Florestas com Logon Único](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="a8ff7-p108">Em ambos os casos, o tráfego originado pelo Azure AD Connect em execução na máquina virtual do Azure é encaminhado para um gateway em uma rede virtual no Azure, que então encaminha o tráfego pela conexão VPN de site a site ou ExpressRoute para o dispositivo de gateway VPN na rede local. A infraestrutura de roteamento da rede local encaminha então o tráfego ao destino, como um controlador de domínio ou um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="a8ff7-133">Há duas etapas principais quando você implanta essa solução:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="a8ff7-p109">Criar uma rede virtual do Azure e estabelecer uma conexão VPN de site a site para a sua rede local. Saiba mais em [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="a8ff7-p110">Instalar o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) em uma máquina virtual associada ao domínio no Azure e depois sincronizar o AD do Windows Server com o Office 365. Isso envolve:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="a8ff7-138">Criar uma Máquina Virtual do Azure para executar o Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="a8ff7-139">Instalar e configurar o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="a8ff7-p111">A configuração do Azure AD Connect requer as credenciais (nome de usuário e senha) de uma conta de administrador do AD do Azure e uma conta de administrador corporativo do AD do Windows Server. O Azure AD Connect executa imediata e continuamente para sincronizar a floresta local do AD do Windows Server com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="a8ff7-142">Antes de implantar esta solução no ambiente de produção, use as instruções descritas no artigo [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md) para definir essa configuração como uma prova de conceito, para fins de demonstrações ou experiências.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-142">Before you deploy this solution in production, use the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="a8ff7-143">Quando a configuração do Azure AD Connect for concluída, ele não salvará as credenciais de conta de administrador corporativo do AD do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="a8ff7-p112">Essa solução descreve a sincronização de uma única floresta do AD do Windows Server com o Office 365. A topologia abordada neste artigo representa apenas uma das maneiras de implementar essa solução. A topologia da sua organização pode ser diferente, com base em requisitos de rede e considerações de segurança exclusivos.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-dirsync-server-for-office-365-in-azure"></a><span data-ttu-id="a8ff7-147">Planejar a hospedagem de um servidor DirSync do Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-147">Plan for hosting a DirSync server for Office 365 in Azure</span></span>
<span data-ttu-id="a8ff7-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="a8ff7-148"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="a8ff7-149">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a8ff7-149">Prerequisites</span></span>

<span data-ttu-id="a8ff7-150">Antes de começar, examine os seguintes pré-requisitos para essa solução:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="a8ff7-151">Examine o conteúdo de planejamento relacionado em [Planejar sua rede virtual do Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-151">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="a8ff7-152">Verifique se você atende a todos os [pré-requisitos](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) para configurar a Rede Virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="a8ff7-p113">Tenha uma assinatura do Office 365 que inclui o recurso de integração do Active Directory. Para saber mais sobre assinaturas do Office 365, acesse a [Página de Assinaturas do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span></span>
    
- <span data-ttu-id="a8ff7-155">Provisione uma Máquina Virtual do Azure que executa o Azure AD Connect para sincronizar sua floresta local do AD do Windows Server com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-155">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="a8ff7-156">Você deve ter as credenciais (nomes e senhas) para a conta de administrador corporativo do AD do Windows Server e uma conta de Administrador do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="a8ff7-157">Suposições de design de arquitetura da solução</span><span class="sxs-lookup"><span data-stu-id="a8ff7-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="a8ff7-158">A lista a seguir descreve as opções de design feitas para essa solução.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="a8ff7-p114">Essa solução usa uma única rede virtual do Azure com uma conexão VPN site a site. A rede virtual do Azure hospeda uma única sub-rede que contém um servidor, o servidor DirSync que está executando o Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the DirSync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="a8ff7-161">Na rede local, existem servidores DNS e um controlador de domínio.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="a8ff7-p115">O Azure AD Connect realiza a sincronização de senha, em vez de logon único. Você não precisa implantar uma infraestrutura de AD FS (Serviços de Federação do Active Directory). Saiba mais sobre as opções de sincronização de senha e logon único em [Determinar qual cenário de integração de diretório usar](https://go.microsoft.com/fwlink/p/?LinkId=393094).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p115">Azure AD Connect performs password synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password synchronization and single sign-on options, see [Determine which directory integration scenario to use](https://go.microsoft.com/fwlink/p/?LinkId=393094).</span></span>
    
<span data-ttu-id="a8ff7-p116">Há opções adicionais de design que você pode considerar ao implantar essa solução no seu ambiente. Elas incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="a8ff7-167">Se houver servidores DNS em uma rede virtual existente do Azure, determine se você deseja que seu servidor DirSync os use para resolução de nomes em vez dos servidores DNS da rede local.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-167">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your DirSync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="a8ff7-p117">Se houver controladores de domínio em uma rede virtual do Azure existente, determine se a configuração de Serviços e Sites do Active Directory pode ser uma opção melhor para você. O servidor DirSync pode consultar controladores de domínio na rede virtual do Azure para procurar alterações em contas e senhas em vez de controladores de domínio na rede local.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The DirSync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="a8ff7-170">Roteiro de implantação</span><span class="sxs-lookup"><span data-stu-id="a8ff7-170">Deployment roadmap</span></span>
<span data-ttu-id="a8ff7-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="a8ff7-171"><a name="DeploymentRoadmap"> </a></span></span>

<span data-ttu-id="a8ff7-172">A implantação do Azure AD Connect em uma máquina virtual no Azure tem três etapas:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-172">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="a8ff7-173">Fase 1: Criar e configurar a rede virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="a8ff7-174">Fase 2: Criar e configurar a máquina virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="a8ff7-175">Fase 3: Instalar e configurar o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="a8ff7-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="a8ff7-176">Após a implantação, você também deve atribuir locais e licenças para as novas contas de usuário no Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="a8ff7-177">O [Kit de implantação do Servidor DirSync no Microsoft Azure](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contém todos os blocos do Azure PowerShell para elaborar esta solução, os diagramas no formato do Microsoft PowerPoint e do Visio e a pasta de trabalho de configuração do Microsoft Excel que gera blocos de comandos personalizados do Azure PowerShell para suas configurações.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-177">The [DirSync Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="a8ff7-178">Fase 1: Criar e configurar a rede virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="a8ff7-179">Para criar e configurar a rede virtual do Azure, conclua a [Fase 1: preparar sua rede local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) e a [Fase 2: criar a rede virtual entre locais no Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) no roteiro de implantação de [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="a8ff7-180">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-180">This is your resulting configuration.</span></span>
  
![Fase 1 do servidor DirSync do Office 365 hospedado no Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="a8ff7-182">Esta figura mostra uma rede local conectada a uma rede virtual do Azure por meio de uma conexão VPN ou ExpressRoute de site a site.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="a8ff7-183">Fase 2: Criar e configurar a máquina virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="a8ff7-p118">Crie a máquina virtual no Azure usando as instruções em [Criar sua primeira máquina virtual do Windows no portal do Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="a8ff7-p119">No painel **Noções Básicas**, selecione a mesma assinatura, local e grupo de recursos da sua rede virtual. Armazene o nome de usuário e a senha em um local seguro. Você precisará dessas informações posteriormente para se conectar à máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="a8ff7-189">No painel **Escolher um tamanho**, escolha o tamanho **A2 Padrão**.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-189">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="a8ff7-p120">No painel **Configurações**, na seção **Armazenamento**, escolha o tipo de armazenamento **Padrão**. Na seção **Rede**, escolha o nome da rede virtual e a sub-rede para hospedar o servidor DirSync (não a GatewaySubnet). Deixe todas as outras configurações com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the DirSync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="a8ff7-193">Para conferir se o servidor DirSync está usando o DNS corretamente, verifique o DNS interno para garantir que um registro de endereço (A) foi adicionado à máquina virtual com o respectivo endereço IP.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-193">Verify that your DirSync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="a8ff7-p121">Use as instruções em [Conectar-se à máquina virtual e fazer login](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) para conectar-se ao servidor DirSync com uma Conexão de Área de Trabalho Remota. Depois de entrar, ingresse na máquina virtual do domínio local do AD do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the DirSync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="a8ff7-p122">Para que o Azure AD Connect acesse os recursos da Internet, você deve configurar o servidor DirSync para usar o servidor proxy da rede local. Entre em contato com o administrador da rede para etapas de configuração adicionais a executar.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p122">For Azure AD Connect to gain access to Internet resources, you must configure the DirSync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="a8ff7-198">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-198">This is your resulting configuration.</span></span>
  
![Fase 2 do servidor DirSync do Office 365 hospedado no Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="a8ff7-200">Esta figura mostra a máquina virtual do servidor DirSync na rede virtual entre locais do Azure.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-200">This figure shows the DirSync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="a8ff7-201">Fase 3: Instalar e configurar o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="a8ff7-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="a8ff7-202">Faça o procedimento a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="a8ff7-p123">Conecte-se ao servidor DirSync usando uma Conexão de Área de Trabalho Remota com uma conta de domínio do AD do Windows Server que tenha privilégios de administrador local. Confira [Conectar-se à máquina virtual e fazer login](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p123">Connect to the DirSync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="a8ff7-205">No servidor DirSync, abra o artigo [Configurar a sincronização de diretórios no Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) e siga as instruções para a sincronização de diretório com a sincronização de senha.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-205">From the DirSync server, open the [Set up directory synchronization in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="a8ff7-p124">A instalação cria a conta **AAD_xxxxxxxxxxxx** na unidade organizacional (UO) Usuários Locais. Não mova nem remova essa conta ou a sincronização falhará.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="a8ff7-208">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-208">This is your resulting configuration.</span></span>
  
![Fase 3 do servidor DirSync do Office 365 hospedado no Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="a8ff7-210">Esta figura mostra o servidor DirSync com o Azure AD Connect na rede virtual entre locais do Azure.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-210">This figure shows the DirSync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="a8ff7-211">Atribuir locais e licenças aos usuários no Office 365</span><span class="sxs-lookup"><span data-stu-id="a8ff7-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="a8ff7-p125">O Azure AD Connect adiciona contas à sua assinatura do Office 365 do AD local do Windows Server, mas para que os usuários entrem no Office 365 e usem seus serviços, as contas devem ser configuradas com um local e licenças. Use essas etapas para adicionar o local e as licenças ativas às devidas contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="a8ff7-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="a8ff7-214">Entre na [página do portal do Office 365](https://portal.office.com) e clique em **Administrador**.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="a8ff7-215">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="a8ff7-216">Na lista das contas de usuário, marque a caixa de seleção ao lado do usuário que você deseja ativar.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="a8ff7-217">Na página do usuário, clique em **Editar** para **Licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="a8ff7-218">Na página **Licenças de produto**, selecione um local para o usuário em **Local** e habilite as licenças apropriadas para ele.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="a8ff7-219">Ao concluir, clique em **Salvar** e, em seguida, clique em **Fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="a8ff7-220">Volte à etapa 3 para usuários adicionais.</span><span class="sxs-lookup"><span data-stu-id="a8ff7-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a8ff7-221">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8ff7-221">See Also</span></span>

<span data-ttu-id="a8ff7-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="a8ff7-222"><a name="DeploymentRoadmap"> </a></span></span>

[<span data-ttu-id="a8ff7-223">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="a8ff7-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="a8ff7-224">Conectar uma rede local a uma rede virtual do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="a8ff7-225">Baixar o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="a8ff7-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="a8ff7-226">Configurar a sincronização de diretório no Office 365</span><span class="sxs-lookup"><span data-stu-id="a8ff7-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="a8ff7-227">Kit de implantação do Servidor DirSync no Azure</span><span class="sxs-lookup"><span data-stu-id="a8ff7-227">DirSync Server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



