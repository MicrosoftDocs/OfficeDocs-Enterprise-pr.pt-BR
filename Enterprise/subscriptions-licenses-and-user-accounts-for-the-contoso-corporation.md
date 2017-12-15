---
title: "Contas de usuário para a Contoso Corporation, licenças e assinaturas"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "Resumo: Compreenda a estrutura de locatários, contas de usuário, licenças e assinaturas de nuvem da Contoso."
ms.openlocfilehash: 6bc90d7b166d5e0983eac8ed47ba16bede57426d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="902b5-103">Contas de usuário para a Contoso Corporation, licenças e assinaturas</span><span class="sxs-lookup"><span data-stu-id="902b5-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="902b5-104">**Resumo:** Compreenda a estrutura de locatários, contas de usuário, licenças e assinaturas de nuvem da Contoso.</span><span class="sxs-lookup"><span data-stu-id="902b5-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="902b5-105">Para fornecer um uso consistente de identidades e cobrança para todas as ofertas de nuvem, a Microsoft fornece a que hierarquia de contas de um organização/assinaturas/licenças/usuário:</span><span class="sxs-lookup"><span data-stu-id="902b5-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="902b5-106">Organização</span><span class="sxs-lookup"><span data-stu-id="902b5-106">Organization</span></span>
    
    <span data-ttu-id="902b5-107">A entidade de negócios que está usando ofertas de nuvem da Microsoft, normalmente identificadas por um nome de domínio DNS público, por exemplo, contoso.com.</span><span class="sxs-lookup"><span data-stu-id="902b5-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="902b5-108">Assinaturas</span><span class="sxs-lookup"><span data-stu-id="902b5-108">Subscriptions</span></span>
    
    <span data-ttu-id="902b5-p101">Para Microsoft SaaS nuvem ofertas (Office 365, Intune/EMS e Dynamics 365), uma assinatura é um produto específico e um conjunto de aquisição de licenças de usuário. Para o Windows Azure, uma assinatura permite faturamento dos serviços de nuvem consumido para a organização.</span><span class="sxs-lookup"><span data-stu-id="902b5-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="902b5-111">Licenças</span><span class="sxs-lookup"><span data-stu-id="902b5-111">Licenses</span></span>
    
    <span data-ttu-id="902b5-p102">Para ofertas de nuvem da Microsoft SaaS, uma licença permite que uma conta de usuário específica usar os serviços de nuvem. Para o Windows Azure, licenças de software são criadas no preço de serviço, mas, em alguns casos, que você precisará adquirir licenças de software adicional.</span><span class="sxs-lookup"><span data-stu-id="902b5-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="902b5-114">Contas do usuário</span><span class="sxs-lookup"><span data-stu-id="902b5-114">User accounts</span></span>
    
    <span data-ttu-id="902b5-115">Contas de usuário são armazenadas em um locatário do Azure AD e possam ser sincronizadas a partir de um provedor de identidade, como o Windows Server AD local.</span><span class="sxs-lookup"><span data-stu-id="902b5-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="902b5-116">Estrutura da Contoso</span><span class="sxs-lookup"><span data-stu-id="902b5-116">Contoso's structure</span></span>

<span data-ttu-id="902b5-117">Contoso determinados a estrutura para a organização e suas assinaturas, licenças, contas e inquilinos a seguir:</span><span class="sxs-lookup"><span data-stu-id="902b5-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="902b5-118">**Figura 1: Da Contoso organização, assinaturas, licenças, contas de usuário e locatários**</span><span class="sxs-lookup"><span data-stu-id="902b5-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Organização, assinaturas, licenças, contas de usuário e locatários da Contoso](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="902b5-120">A Figura 1 mostra como a organização Contoso inclui diversas assinaturas e está vinculada a um locatário comuns do Azure AD que contém as contas de usuário sincronizadas a partir do contoso.com floresta do Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="902b5-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="902b5-121">**Organização** A Contoso Corporation é identificada pela sua contoso.com de nome de domínio público.</span><span class="sxs-lookup"><span data-stu-id="902b5-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="902b5-122">**Assinaturas e licenças** A Contoso Corporation está usando o seguinte:</span><span class="sxs-lookup"><span data-stu-id="902b5-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="902b5-123">O produto do Office 365 Enterprise E3 com 5.000 licenças</span><span class="sxs-lookup"><span data-stu-id="902b5-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="902b5-124">O produto do Office 365 Enterprise E5 com 200 licenças</span><span class="sxs-lookup"><span data-stu-id="902b5-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="902b5-125">O produto EMS com 5.000 licenças</span><span class="sxs-lookup"><span data-stu-id="902b5-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="902b5-126">O produto Dynamics 365 com 100 licenças</span><span class="sxs-lookup"><span data-stu-id="902b5-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="902b5-127">Diversas assinaturas Azure com base em regiões</span><span class="sxs-lookup"><span data-stu-id="902b5-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="902b5-128">**Contas de usuário** Um locatário comuns do Windows Azure AD contém a lista de contas de usuário e os grupos usados por todas as assinaturas da Contoso, com exceção de desenvolvimento e teste assinaturas do Azure.</span><span class="sxs-lookup"><span data-stu-id="902b5-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="902b5-129">Para os locatários da Contoso:</span><span class="sxs-lookup"><span data-stu-id="902b5-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="902b5-p103">Para ofertas de nuvem SaaS, o inquilino é o local regional que hospeda os servidores fornecendo serviços de nuvem. A Contoso optou pela região europeu para hospedar seus locatários do Office 365, EMS e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="902b5-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="902b5-p104">Serviços do Azure PaaS e aplicativos e cargas de trabalho de TI IaaS podem ter locação em qualquer datacenter do Windows Azure no mundo inteiro. Um locatário do Azure AD é uma instância específica do Azure AD contendo as contas e grupos.</span><span class="sxs-lookup"><span data-stu-id="902b5-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="902b5-134">O inquilino comuns do Azure AD que contém as contas sincronizadas para a floresta Contoso Windows Server AD fornece IDaaS nas ofertas de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="902b5-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="902b5-135">Para obter mais informações, consulte [assinaturas, licenças, contas e inquilinos para as ofertas de nuvem da Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span><span class="sxs-lookup"><span data-stu-id="902b5-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="902b5-136">Assinaturas do Azure da Contoso</span><span class="sxs-lookup"><span data-stu-id="902b5-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="902b5-137">A Figura 2 mostra o design hierárquico de assinaturas do Azure da Contoso:</span><span class="sxs-lookup"><span data-stu-id="902b5-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="902b5-138">**Figura 2: Estrutura da Contoso para assinaturas do Azure**</span><span class="sxs-lookup"><span data-stu-id="902b5-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Estrutura da Contoso para assinaturas do Azure](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="902b5-140">A Contoso é na parte superior, com base em seu Enterprise Agreement com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="902b5-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="902b5-141">Há um conjunto de contas correspondente às diferentes regiões da Contoso Corporation em todo o mundo, com base nos domínios da floresta do Windows Server AD da Contoso.</span><span class="sxs-lookup"><span data-stu-id="902b5-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="902b5-142">Dentro de cada região, há um ou mais inscrições com base nas necessidades de implantação de desenvolvimento, teste e produção da região.</span><span class="sxs-lookup"><span data-stu-id="902b5-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="902b5-p105">Cada assinatura Azure pode ser associada um único locatário do Azure AD que contém as contas de usuário e grupos para autenticação e autorização aos serviços do Azure. Inscrições de produção usam locatário da Contoso Azure AD comuns.</span><span class="sxs-lookup"><span data-stu-id="902b5-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="902b5-145">See Also</span><span class="sxs-lookup"><span data-stu-id="902b5-145">See Also</span></span>

[<span data-ttu-id="902b5-146">Contoso em nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="902b5-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="902b5-147">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="902b5-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="902b5-148">Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="902b5-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




