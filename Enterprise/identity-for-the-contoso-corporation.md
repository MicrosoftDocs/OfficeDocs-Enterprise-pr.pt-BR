---
title: Identidade para a Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "Resumo: Entenda como Contoso aproveita IDaaS e fornece geograficamente distribuída e autenticação redundante para seus usuários."
ms.openlocfilehash: 7a6448969a90f1f646f70fee4c67a6da992dd2bc
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="identity-for-the-contoso-corporation"></a><span data-ttu-id="29c2f-103">Identidade para a Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="29c2f-103">Identity for the Contoso Corporation</span></span>

 <span data-ttu-id="29c2f-104">**Resumo:** Compreenda como a Contoso aproveita IDaaS e fornece geograficamente distribuída e autenticação redundante para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="29c2f-104">**Summary:** Understand how Contoso takes advantage of IDaaS and provides geographically distributed and redundant authentication for its users.</span></span>
  
<span data-ttu-id="29c2f-p101">A Microsoft fornece uma identidade como um serviço (IDaaS) entre suas ofertas de nuvem. Para adotar uma infra-estrutura inclusive de nuvem, solução de IDaaS da Contoso deve aproveitar o seu provedor de identidade no local e incluir autenticação federada com seus provedores de identidade confiável, de terceiros existente.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p101">Microsoft provides an Identity as a Service (IDaaS) across its cloud offerings. To adopt a cloud-inclusive infrastructure, Contoso's IDaaS solution must leverage their on-premises identity provider and include federated authentication with their existing trusted, third-party identity providers.</span></span>
  
## <a name="contosos-windows-server-ad-forest"></a><span data-ttu-id="29c2f-107">Floresta do Windows Server AD da Contoso</span><span class="sxs-lookup"><span data-stu-id="29c2f-107">Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="29c2f-p102">A Contoso usa uma única floresta do Windows Server Active Directory (AD) para contoso.com com sete domínios, um para cada região do mundo. As matrizes, escritórios regionais hub e escritórios satélite contêm controladores de domínio para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p102">Contoso uses a single Windows Server Active Directory (AD) forest for contoso.com with seven domains, one for each region of the world. The headquarters, regional hub offices, and satellite offices contain domain controllers for local authentication and authorization.</span></span>
  
<span data-ttu-id="29c2f-110">**Figura 1: Da Contoso floresta e domínios em todo o mundo**</span><span class="sxs-lookup"><span data-stu-id="29c2f-110">**Figure 1: Contoso's forest and domains worldwide**</span></span>

![Floresta e domínios do AD do Windows Server da Contoso em todo o mundo](images/Contoso_Poster/Contoso_WW_ID.png)
  
<span data-ttu-id="29c2f-112">A Figura 1 mostra a floresta Contoso com domínios regionais para as diferentes partes do mundo que contêm os hubs regionais.</span><span class="sxs-lookup"><span data-stu-id="29c2f-112">Figure 1 shows the Contoso forest with regional domains for the different parts of the world that contain regional hubs.</span></span>
  
<span data-ttu-id="29c2f-113">A Contoso deseja usar as contas e grupos na floresta contoso.com para autenticação e autorização para seus aplicativos baseados em nuvem e cargas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="29c2f-113">Contoso wants to use the accounts and groups in the contoso.com forest for authentication and authorization for its cloud-based apps and workloads.</span></span>
  
## <a name="contosos-federated-authentication-infrastructure"></a><span data-ttu-id="29c2f-114">Infraestrutura de autenticação federada da Contoso</span><span class="sxs-lookup"><span data-stu-id="29c2f-114">Contoso's federated authentication infrastructure</span></span>

<span data-ttu-id="29c2f-115">Permite que a Contoso:</span><span class="sxs-lookup"><span data-stu-id="29c2f-115">Contoso allows:</span></span>
  
- <span data-ttu-id="29c2f-116">Clientes usem suas contas do Microsoft, Facebook ou Google Mail para entrar no seu site público.</span><span class="sxs-lookup"><span data-stu-id="29c2f-116">Customers to use their Microsoft, Facebook, or Google Mail accounts to sign in to their public web site.</span></span>
    
- <span data-ttu-id="29c2f-117">Parceiros e fornecedores usem suas contas LinkedIn, a equipe de vendas ou Google Mail para entrar no parceiro de extranet.</span><span class="sxs-lookup"><span data-stu-id="29c2f-117">Vendors and partners to use their LinkedIn, Salesforce, or Google Mail accounts to sign in to the partner extranet.</span></span>
    
<span data-ttu-id="29c2f-118">**Figura 2: Suporte da Contoso autenticação federada para clientes e parceiros**</span><span class="sxs-lookup"><span data-stu-id="29c2f-118">**Figure 2: Contoso's support for federated authentication for customers and partners**</span></span>

![Infraestrutura da Contoso para dar suporte à autenticação federada para clientes e parceiros](images/Contoso_Poster/Federated_ID.png)
  
<span data-ttu-id="29c2f-p103">A Figura 2 mostra DMZ Contoso contendo um site público, um parceiro extranet e um conjunto de servidores do AD FS. DMZ está conectado à Internet que contém a clientes e parceiros e serviços de Internet.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p103">Figure 2 shows the Contoso DMZ containing a public web site, a partner extranet, and a set of AD FS servers. The DMZ is connected to the Internet that contains customers and partners and Internet services.</span></span>
  
<span data-ttu-id="29c2f-122">Servidores de Active Directory Federation Services (AD FS) na DMZ autenticam credenciais de clientes para acessar o site público e credenciais de parceiro para acesso a extranet de parceiros.</span><span class="sxs-lookup"><span data-stu-id="29c2f-122">Active Directory Federation Services (AD FS) servers in the DMZ authenticate customer credentials for access to the public web site and partner credentials for access to the partner extranet.</span></span>
  
<span data-ttu-id="29c2f-p104">Quando seu site público um Azure Web App e o parceiro extranet do Dynamics 365 transições de Contoso, eles querem continuar a usar esses provedores de identidade de terceiros para seus clientes e parceiros. Isso será realizado configurando federação entre locatários Contoso Azure AD e esses provedores de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p104">When Contoso transitions its public web site to an Azure Web App and partner extranet to Dynamics 365, they want to continue to use these third-party identity providers for their customers and partners. This will be accomplished by configuring federation between Contoso Azure AD tenants and these third-party identity providers.</span></span>
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a><span data-ttu-id="29c2f-125">Sincronização de diretórios para a floresta do Windows Server AD da Contoso</span><span class="sxs-lookup"><span data-stu-id="29c2f-125">Directory synchronization for Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="29c2f-p105">A Contoso implantou a ferramenta conectar do Azure AD em um cluster de servidores no seu datacenter Paris. Connect do Azure AD sincroniza as alterações para a floresta do Windows Server AD contoso.com com o locatário do Azure AD compartilhado pelo Office 365 da Contoso, EMS, Dynamics 365 e assinaturas do Azure. Para obter mais informações sobre inquilinos, contas de usuário, licenças e assinaturas, consulte [assinaturas, licenças e contas de usuário para a Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span><span class="sxs-lookup"><span data-stu-id="29c2f-p105">Contoso has deployed the Azure AD Connect tool on a cluster of servers in its Paris datacenter. Azure AD Connect synchronizes changes to the contoso.com Windows Server AD forest with the Azure AD tenant shared by Contoso's Office 365, EMS, Dynamics 365, and Azure subscriptions. For more information about subscriptions, licenses, user accounts, and tenants, see [Subscriptions, licenses, and user accounts for the Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span></span>
  
<span data-ttu-id="29c2f-129">**Figura 3: Infra-estrutura de sincronização de diretório da Contoso**</span><span class="sxs-lookup"><span data-stu-id="29c2f-129">**Figure 3: Contoso's directory synchronization infrastructure**</span></span>

![Infraestrutura de sincronização de diretórios da Contoso](images/Contoso_Poster/DirSync.png)
  
<span data-ttu-id="29c2f-131">A Figura 3 mostra um cluster de servidores que executam o Azure AD conectar-se a floresta Contoso Windows Server AD como sincronizar com o locatário do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="29c2f-131">Figure 3 shows a cluster of servers running Azure AD Connect synchronizing the Contoso Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="29c2f-p106">Contoso tiver configurado a autenticação federada, que fornece o serviço single sign-on para trabalhadores da Contoso. Quando um usuário que já tiver entrado para a floresta do Windows Server AD contoso.com acessa um recurso de nuvem Microsoft SaaS ou PaaS, eles não serão solicitados por uma senha.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p106">Contoso has configured federated authentication, which provides single sign-on for Contoso's workers. When a user that has already signed in to the contoso.com Windows Server AD forest accesses a Microsoft SaaS or PaaS cloud resource, they will not be prompted for a password.</span></span>
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a><span data-ttu-id="29c2f-134">Distribuição geográfica de tráfego de autenticação da Contoso</span><span class="sxs-lookup"><span data-stu-id="29c2f-134">Geographical distribution of Contoso authentication traffic</span></span>

<span data-ttu-id="29c2f-p107">Para oferecer um melhor suporte sua força de trabalho móvel e remota, a Contoso implantou os conjuntos de servidores de autenticação em seus escritórios regionais. Essa infra-estrutura distribui a carga e fornece um melhor desempenho e redundância ao autenticar credenciais de usuário para acesso a ofertas de nuvem da Microsoft que usam o locatário comuns do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p107">To better support its mobile and remote workforce, Contoso has deployed sets of authentication servers in its regional offices. This infrastructure distributes the load and provides redundancy and higher performance when authenticating user credentials for access to Microsoft cloud offerings that use the common Azure AD tenant.</span></span>
  
<span data-ttu-id="29c2f-137">Para distribuir a carga de solicitações de autenticação, a Contoso configurou o Gerenciador de tráfego do Windows Azure com um perfil que usa o método, que se refere a autenticação de clientes para o conjunto regional mais próximo de servidores de autenticação de roteamento de desempenho.</span><span class="sxs-lookup"><span data-stu-id="29c2f-137">To distribute the load of authentication requests, Contoso has configured Azure Traffic Manager with a profile that uses the performance routing method, which refers authenticating clients to the regionally closest set of authentication servers.</span></span> 
  
<span data-ttu-id="29c2f-138">**Figura 4: A distribuição geográfica de tráfego de autenticação para escritórios regionais**</span><span class="sxs-lookup"><span data-stu-id="29c2f-138">**Figure 4: Geographical distribution of authentication traffic for regional offices**</span></span>

![Distribuição geográfica do tráfego de autenticação da Contoso para escritórios regionais](images/Contoso_Poster/Auth_GeoDist.png)
  
<span data-ttu-id="29c2f-p108">Figura 4 mostra as camadas de computadores clientes, Gerenciador de tráfego do Windows Azure e servidores de autenticação em escritórios regionais. Cada escritório regional usa proxies de web e servidores do AD FS para autenticar credenciais de usuário com os controladores de domínio do Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p108">Figure 4 shows the layers of client computers, Azure Traffic Manager, and authentication servers in regional offices. Each regional office uses web proxies and AD FS servers to authenticate user credentials with Windows Server AD domain controllers.</span></span>
  
<span data-ttu-id="29c2f-142">Exemplo do processo de autenticação:</span><span class="sxs-lookup"><span data-stu-id="29c2f-142">Authentication process example:</span></span>
  
1. <span data-ttu-id="29c2f-143">O computador cliente inicia a comunicação com uma página da web no Office 365 aluguel na Europa (por exemplo, sharepoint.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="29c2f-143">The client computer initiates communication with a web page in the Office 365 tenancy in Europe (such as sharepoint.contoso.com).</span></span>
    
2. <span data-ttu-id="29c2f-p109">O Office 365 volta envia uma solicitação para enviar uma prova de autenticação. A solicitação contém a URL para contatar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p109">Office 365 sends back a request to send proof of authentication. The request contains the URL to contact for authentication.</span></span>
    
3. <span data-ttu-id="29c2f-146">O computador cliente tenta resolver o nome DNS na URL para um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="29c2f-146">The client computer attempts to resolve the DNS name in the URL to an IP address.</span></span>
    
4. <span data-ttu-id="29c2f-147">Gerenciador de tráfego do Azure recebe a consulta DNS e responde para o computador cliente com o endereço IP de um servidor de proxy de aplicativo web no escritório regional mais próximo ao computador cliente.</span><span class="sxs-lookup"><span data-stu-id="29c2f-147">Azure Traffic Manager receives the DNS query and responds to the client computer with the IP address of a web application proxy server in the regional office that is closest to the client computer.</span></span>
    
5.  <span data-ttu-id="29c2f-148">O computador cliente envia uma solicitação de autenticação para um servidor de proxy de aplicativo web, que encaminha a solicitação para um servidor AD FS.</span><span class="sxs-lookup"><span data-stu-id="29c2f-148">The client computer sends an authentication request to a web application proxy server, which forwards the request to an AD FS server.</span></span>
    
6. <span data-ttu-id="29c2f-149">O servidor do AD FS solicita as credenciais do usuário do computador cliente.</span><span class="sxs-lookup"><span data-stu-id="29c2f-149">The AD FS server requests the user credentials from the client computer.</span></span>
    
7. <span data-ttu-id="29c2f-150">O computador cliente envia as credenciais do usuário sem avisar o usuário.</span><span class="sxs-lookup"><span data-stu-id="29c2f-150">The client computer sends the user credentials without prompting the user.</span></span>
    
8. <span data-ttu-id="29c2f-151">O servidor do AD FS valida as credenciais com um controlador de domínio do Windows Server AD no escritório regional e retorna um token de segurança para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="29c2f-151">The AD FS server validates the credentials with a Windows Server AD domain controller in the regional office and returns a security token to the client computer.</span></span>
    
9. <span data-ttu-id="29c2f-152">O computador cliente envia o token de segurança para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="29c2f-152">The client computer sends the security token to Office 365.</span></span>
    
10. <span data-ttu-id="29c2f-153">Após uma validação bem-sucedida, o Office 365 armazena em cache o token de segurança e envia a página da web solicitada na etapa 1 para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="29c2f-153">After successful validation, Office 365 caches the security token and sends the web page requested in step 1 to the client computer.</span></span>
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a><span data-ttu-id="29c2f-154">Redundância para a infraestrutura de autenticação matrizes no Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="29c2f-154">Redundancy for the headquarters authentication infrastructure in Azure IaaS</span></span>

<span data-ttu-id="29c2f-155">Para fornecer redundância para os trabalhadores remotos e móveis da sede Paris que contém a 15.000 trabalhadores, a Contoso implantou um segundo conjunto de proxies de aplicativos e servidores do AD FS no Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="29c2f-155">To provide redundancy for the remote and mobile workers of the Paris headquarters that contains 15,000 workers, Contoso has deployed a second set of application proxies and AD FS servers in Azure IaaS.</span></span>
  
<span data-ttu-id="29c2f-156">**Figura 5: Infraestrutura de autenticação redundantes no Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="29c2f-156">**Figure 5: Redundant authentication infrastructure in Azure IaaS**</span></span>

![A infraestrutura de autenticação redundante no Azure IaaS para a sede de Paris](images/Contoso_Poster/Paris_Auth_Redun.png)
  
<span data-ttu-id="29c2f-158">Figura 5 mostra servidores AD FS e proxies de web no DMZ e um conjunto adicional de cada uma no Azure locais cruzados rede virtual.</span><span class="sxs-lookup"><span data-stu-id="29c2f-158">Figure 5 shows web proxies and AD FS servers in the DMZ and an additional set of each in a cross-premises Azure virtual network.</span></span>
  
<span data-ttu-id="29c2f-p110">Quando os servidores de autenticação primária na sede da DMZ ficar indisponíveis, a equipe de TI alterna para o conjunto redundante implantado no Azure IaaS. Solicitações de autenticação subsequentes de computadores de escritório Paris usam o conjunto no Azure IaaS, até que o problema de disponibilidade for corrigido.</span><span class="sxs-lookup"><span data-stu-id="29c2f-p110">When the primary authentication servers in the headquarters DMZ become unavailable, IT staff switch over to the redundant set deployed in Azure IaaS. Subsequent authentication requests from Paris office computers use the set in Azure IaaS until the availability problem is corrected.</span></span>
  
<span data-ttu-id="29c2f-161">Para alternar e voltar, Contoso atualizações o perfil do Gerenciador de tráfego do Windows Azure para a região Paris usar um conjunto diferente de endereços IP para os proxies de aplicativo web:</span><span class="sxs-lookup"><span data-stu-id="29c2f-161">To switch over and switch back, Contoso updates the Azure Traffic Manager profile for the Paris region to use a different set of IP addresses for the web application proxies:</span></span>
  
- <span data-ttu-id="29c2f-162">Quando os servidores de autenticação DMZ estão disponíveis, use os endereços IP dos servidores no DMZ.</span><span class="sxs-lookup"><span data-stu-id="29c2f-162">When the DMZ authentication servers are available, use the IP addresses of the servers in the DMZ.</span></span>
    
- <span data-ttu-id="29c2f-163">Quando os servidores de autenticação DMZ não estão disponíveis, use os endereços IP dos servidores no Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="29c2f-163">When the DMZ authentication servers are not available, use the IP addresses of the servers in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="29c2f-164">Veja também</span><span class="sxs-lookup"><span data-stu-id="29c2f-164">See Also</span></span>

[<span data-ttu-id="29c2f-165">Contoso na Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="29c2f-165">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="29c2f-166">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="29c2f-166">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="29c2f-167">Identidade da Microsoft Cloud para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="29c2f-167">Microsoft Cloud Identity for Enterprise Architects</span></span>](http://aka.ms/cloudarchidentity)
  
[<span data-ttu-id="29c2f-168">Proteção de identidade e dispositivo para o Office 365</span><span class="sxs-lookup"><span data-stu-id="29c2f-168">Identity and Device Protection for Office 365</span></span>](http://aka.ms/o365protect_device)
  
[<span data-ttu-id="29c2f-169">Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="29c2f-169">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



