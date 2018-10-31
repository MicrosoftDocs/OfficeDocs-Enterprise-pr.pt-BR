---
title: Funcionalidades multigeográficas no OneDrive e SharePoint Online no Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda a sua presença do Office 365 para várias regiões geográficas com funcionalidades multigeográficas do OneDrive e do SharePoint Online.
ms.openlocfilehash: 725a7a88e3459f73ff00554b14afc740db1244b3
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849817"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="1d047-103">Funcionalidades multigeográficas no OneDrive e SharePoint Online no Office 365</span><span class="sxs-lookup"><span data-stu-id="1d047-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="1d047-p101">Com as funcionalidades multigeográficas do OneDrive e do SharePoint Online, sua organização pode expandir a presença do Office 365 para várias regiões geográficas e/ou países em seu locatário existente. Fale com a equipe da sua conta da Microsoft para inscrever a sua empresa multinacional no OneDrive for Business com Funcionalidades Multigeográficas.</span><span class="sxs-lookup"><span data-stu-id="1d047-p101">With Multi-Geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="1d047-106">Com o OneDrive for Business com Funcionalidades Multigeográficas, você pode provisionar e armazenar dados em repouso nas localizações geográficas escolhidas para atender aos requisitos de residência de dados e, ao mesmo tempo, dar vazão à sua implantação global a partir de experiências de produtividade modernas para a sua força de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1d047-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="1d047-107">Vejamos a seguir como os recursos multigeográficos podem beneficiar a sua organização:</span><span class="sxs-lookup"><span data-stu-id="1d047-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="1d047-108">Opere como uma organização conectada globalmente com um único locatário do Office 365 em várias localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="1d047-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="1d047-109">Atenda aos requisitos de residência de dados criando e hospedando dados em repouso em um localização geográfica especificada.</span><span class="sxs-lookup"><span data-stu-id="1d047-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="1d047-110">Capacite os seus usuários-satélites com as mesmas experiências de produtividade modernas que os seus usuários do local central desfrutam.</span><span class="sxs-lookup"><span data-stu-id="1d047-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="1d047-111">Permita que os seus usuários transitem por localizações geográficas à medida que mudarem de função, mantendo intacto o acesso ao conteúdo deles.</span><span class="sxs-lookup"><span data-stu-id="1d047-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="1d047-112">Adapte as suas políticas de compartilhamento por localização geográfica e as políticas de prevenção contra perda de dados por local.</span><span class="sxs-lookup"><span data-stu-id="1d047-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="1d047-113">Designe gerentes de descoberta eletrônica por localização geográfica e permita a administração de casos de acordo com a sua localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="1d047-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="1d047-114">Escolha namespaces de URL exclusivos (por exemplo, ContosoEUR.sharepoint.com) para as suas localizações geográficas adicionais.</span><span class="sxs-lookup"><span data-stu-id="1d047-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="1d047-115">Consolide os seus dados locais regionais em seu locatário multigeográfico do Office 365.</span><span class="sxs-lookup"><span data-stu-id="1d047-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="1d047-p102">Em uma configuração multigeográfica, o seu locatário do Office 365 consiste em um local central (onde sua assinatura do Office 365 foi provisionada originalmente) e uma ou mais localizações geográficas satélites. O conceito principal de multigeografia é que um único locatário pode atuar em várias localizações geográficas. Em um locatário multigeográfico, as informações sobre localizações geográficas, grupos e informações do usuário são dominadas no Azure Active Directory (AAD). Como as informações de locatário são controladas centralmente e sincronizadas em cada localização geográfica, o compartilhamento e as experiências envolvendo qualquer pessoa da sua empresa conterão uma abrangência global.</span><span class="sxs-lookup"><span data-stu-id="1d047-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="1d047-120">Vídeo: Apresentando a multigeografia do Office 365</span><span class="sxs-lookup"><span data-stu-id="1d047-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="1d047-121">Obter recursos multigeográficos em três etapas simples</span><span class="sxs-lookup"><span data-stu-id="1d047-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="1d047-122">A configuração multigeográfica é fácil:</span><span class="sxs-lookup"><span data-stu-id="1d047-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="1d047-p103">Trabalhe com a sua equipe de contas para adicionar o plano de serviço _Funcionalidades multigeográficos no Office 365_. Ela dará instruções sobre a adição do número de licenças necessárias.</span><span class="sxs-lookup"><span data-stu-id="1d047-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="1d047-125">Adicione seus locais de satélite.</span><span class="sxs-lookup"><span data-stu-id="1d047-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="1d047-126">Configure as suas de conta de usuário para o local apropriado.</span><span class="sxs-lookup"><span data-stu-id="1d047-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="1d047-127">Disponibilidade e status multigeográficos</span><span class="sxs-lookup"><span data-stu-id="1d047-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="1d047-128">A multigeografia do OneDrive atualmente é oferecida nas regiões e países seguintes:</span><span class="sxs-lookup"><span data-stu-id="1d047-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="1d047-129">Ásia – Pacífico</span><span class="sxs-lookup"><span data-stu-id="1d047-129">Asia-Pacific</span></span>
    
- <span data-ttu-id="1d047-130">Austrália</span><span class="sxs-lookup"><span data-stu-id="1d047-130">Australia</span></span>
    
- <span data-ttu-id="1d047-131">Canadá</span><span class="sxs-lookup"><span data-stu-id="1d047-131">Canada</span></span>
    
- <span data-ttu-id="1d047-132">União Europeia (EMEA)</span><span class="sxs-lookup"><span data-stu-id="1d047-132">European Union (EMEA)</span></span>

- <span data-ttu-id="1d047-133">França</span><span class="sxs-lookup"><span data-stu-id="1d047-133">France</span></span>
    
- <span data-ttu-id="1d047-134">Japão</span><span class="sxs-lookup"><span data-stu-id="1d047-134">Japan</span></span>
    
- <span data-ttu-id="1d047-135">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="1d047-135">United Kingdom</span></span>
    
- <span data-ttu-id="1d047-136">Estados Unidos (América do Norte)</span><span class="sxs-lookup"><span data-stu-id="1d047-136">United States (North America)</span></span>
    
- <span data-ttu-id="1d047-137">Coreia</span><span class="sxs-lookup"><span data-stu-id="1d047-137">Korea</span></span>
      
<span data-ttu-id="1d047-138">Localizações geográficas futuras:</span><span class="sxs-lookup"><span data-stu-id="1d047-138">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="1d047-139">Índia</span><span class="sxs-lookup"><span data-stu-id="1d047-139">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="1d047-140">Introdução</span><span class="sxs-lookup"><span data-stu-id="1d047-140">Getting started</span></span>

<span data-ttu-id="1d047-p104">Para começar a usar o OneDrive for Business com Funcionalidades Multigeográficas, a primeira etapa é [planejar o seu ambiente do OneDrive for Business com Funcionalidades Multigeográficas](plan-for-multi-geo.md). Em seguida, [aprenda como administrar um ambiente multigeográfico](administering-a-multi-geo-environment.md) e [como será a experiência dos seus usuários em um ambiente multigeográfico](multi-geo-user-experience.md). Quando estiver pronto para configurar o OneDrive for Business com Funcionalidades Multigeográficas, [configure o seu locatário para a multigeografia](multi-geo-tenant-configuration.md) e, em seguida, [mova todos os sites do OneDrive existentes para as suas novas localizações geográficas](move-onedrive-between-geo-locations.md) e [configure a pesquisa](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="1d047-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
