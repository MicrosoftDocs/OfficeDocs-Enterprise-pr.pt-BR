---
title: Recursos de multi-Geo no OneDrive e SharePoint Online no Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda sua presença do Office 365 para várias regiões geográficas com os recursos de multi-geo no OneDrive e SharePoint Online.
ms.openlocfilehash: 2c5de533aaaace68e51b747cd62a53b9572bcaec
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="2b45b-103">Recursos de multi-Geo no OneDrive e SharePoint Online no Office 365</span><span class="sxs-lookup"><span data-stu-id="2b45b-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="2b45b-p101">Com os recursos de multi-geo no OneDrive e SharePoint Online, sua organização pode expandir sua presença do Office 365 para várias regiões geográficas e/ou países dentro de seu locatário existente. Este recurso está atualmente no modo de visualização. Chegar aos sua equipe de conta da Microsoft para sua empresa multinacionais para a avaliação do OneDrive Multi-Geo se inscrever.</span><span class="sxs-lookup"><span data-stu-id="2b45b-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. This feature is currently in preview. Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="2b45b-107">Com o OneDrive Multi-Geo, você pode provisionar e armazenar os dados em repouso nos locais geo escolhida para atender aos requisitos de residência de dados e ao mesmo tempo desbloquear seu rolo global sem experiências de produtividade moderno para sua força de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2b45b-107">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="2b45b-108">Aqui está como recursos de multi-geo podem beneficiar sua organização:</span><span class="sxs-lookup"><span data-stu-id="2b45b-108">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="2b45b-109">Opere como uma organização global de conectadas com um único locatário do Office 365 abrangência vários locais geo.</span><span class="sxs-lookup"><span data-stu-id="2b45b-109">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="2b45b-110">Atender aos requisitos de residência de dados criando e hospedando os dados em repouso dentro de um local de geo especificado.</span><span class="sxs-lookup"><span data-stu-id="2b45b-110">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="2b45b-111">Capacite os usuários de satélite com as mesmo experiências de produtividade moderno aproveitadas por seus usuários do local central.</span><span class="sxs-lookup"><span data-stu-id="2b45b-111">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="2b45b-112">Permitir que os usuários se mover entre localidades geo como suas alterações de função, enquanto o acesso ao seu conteúdo é mantido intacto.</span><span class="sxs-lookup"><span data-stu-id="2b45b-112">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="2b45b-113">Ajuste suas políticas de compartilhamento por geo local e políticas de prevenção de perda de dados por site.</span><span class="sxs-lookup"><span data-stu-id="2b45b-113">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="2b45b-114">Designar eDiscovery gerenciadores por local geo e permitir que regem casos adaptados ao seu local geo.</span><span class="sxs-lookup"><span data-stu-id="2b45b-114">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="2b45b-115">Escolha URL espaços para nome exclusivos (por exemplo, ContosoEUR.sharepoint.com) para seus locais geo adicionais.</span><span class="sxs-lookup"><span data-stu-id="2b45b-115">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="2b45b-116">Consolide seus dados de locais regionais em seu locatário do Office 365 multi-geo.</span><span class="sxs-lookup"><span data-stu-id="2b45b-116">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="2b45b-p102">Em uma configuração de multi-geo, seu locatário do Office 365 consiste em um local central (também conhecido como o local padrão) e um ou mais locais de geo satélite. O conceito de chave de multi-geo é que um único locatário ocupará entre um vários locais geo. Em um locatário multi-geo, as informações sobre locais geo, grupos e informações do usuário, são administradas no Windows Azure Active Directory (AAD). Como suas informações de Inquilino são administradas centralmente e sincronizadas em cada local geo, compartilhamento e experiências envolvendo qualquer pessoa da sua empresa contêm divulgação global.</span><span class="sxs-lookup"><span data-stu-id="2b45b-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="2b45b-121">Configuração do inquilino de multi-geo de amostra</span><span class="sxs-lookup"><span data-stu-id="2b45b-121">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="2b45b-122">Usando um locatário multi-geo, Contoso, com um local central da América do Norte, pode expandir para satélite geo locais na Europa e Austrália sob a proteção de única organização de Contoso.com. Usuários com o seu local de dados preferida definido como Europa terão sua OneDrive na Europa, enquanto os usuários com o seu local de dados preferida na América do Norte terão sua OneDrive nos EUA.</span><span class="sxs-lookup"><span data-stu-id="2b45b-122">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Mapa do mundo, mostrando geo locais para a Contoso e outros locais geo disponíveis](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="2b45b-124">Obter recursos de multi-geo em três etapas simples</span><span class="sxs-lookup"><span data-stu-id="2b45b-124">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="2b45b-125">Configurar o multi-geo é fácil:</span><span class="sxs-lookup"><span data-stu-id="2b45b-125">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="2b45b-p103">Trabalhar com sua equipe de conta para adicionar o plano de serviço _Multi-Geo recursos no Office 365_ . Eles vão orientá-lo para adicionar o número de licenças necessárias.</span><span class="sxs-lookup"><span data-stu-id="2b45b-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="2b45b-128">Adicione seus locais de satélite.</span><span class="sxs-lookup"><span data-stu-id="2b45b-128">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="2b45b-129">Configure suas contas de usuário para o local apropriado.</span><span class="sxs-lookup"><span data-stu-id="2b45b-129">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="2b45b-130">Disponibilidade e o status de Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="2b45b-130">Multi-Geo status and availability</span></span>

<span data-ttu-id="2b45b-131">OneDrive Multi-Geo no momento é oferecido nessas regiões e países:</span><span class="sxs-lookup"><span data-stu-id="2b45b-131">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="2b45b-132">Pacífico Asiático</span><span class="sxs-lookup"><span data-stu-id="2b45b-132">Asia-Pacific</span></span>
    
- <span data-ttu-id="2b45b-133">Austrália</span><span class="sxs-lookup"><span data-stu-id="2b45b-133">Australia</span></span>
    
- <span data-ttu-id="2b45b-134">Canadá</span><span class="sxs-lookup"><span data-stu-id="2b45b-134">Canada</span></span>
    
- <span data-ttu-id="2b45b-135">União Europeia (EMEA)</span><span class="sxs-lookup"><span data-stu-id="2b45b-135">European Union (EMEA)</span></span>
    
- <span data-ttu-id="2b45b-136">Japão</span><span class="sxs-lookup"><span data-stu-id="2b45b-136">Japan</span></span>
    
- <span data-ttu-id="2b45b-137">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="2b45b-137">United Kingdom</span></span>
    
- <span data-ttu-id="2b45b-138">Estados Unidos (América do Norte)</span><span class="sxs-lookup"><span data-stu-id="2b45b-138">United States (North America)</span></span>
    
- <span data-ttu-id="2b45b-139">Coreia</span><span class="sxs-lookup"><span data-stu-id="2b45b-139">Korea</span></span>
      
<span data-ttu-id="2b45b-140">Próximos geo locais:</span><span class="sxs-lookup"><span data-stu-id="2b45b-140">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="2b45b-141">França</span><span class="sxs-lookup"><span data-stu-id="2b45b-141">France</span></span>
- <span data-ttu-id="2b45b-142">Índia</span><span class="sxs-lookup"><span data-stu-id="2b45b-142">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="2b45b-143">Introdução</span><span class="sxs-lookup"><span data-stu-id="2b45b-143">Getting started</span></span>

<span data-ttu-id="2b45b-p104">Para começar com o OneDrive for Business Multi-Geo, a primeira etapa é [Planejar o OneDrive for Business Multi-Geo ambiente](plan-for-multi-geo.md). Avançar, [Saiba mais sobre como administrar um ambiente multi-geo](administering-a-multi-geo-environment.md) e [como os usuários observarão um ambiente multi-geo](multi-geo-user-experience.md). Quando você estiver pronto para configurar o OneDrive for Business Multi-Geo, [configure seu locatário do multi-geo](multi-geo-tenant-configuration.md), [mover todos os sites existentes OneDrive para as localizações de geo novos](move-onedrive-between-geo-locations.md) e [Configurar a pesquisa](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="2b45b-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
