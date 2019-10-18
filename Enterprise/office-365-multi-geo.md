---
title: Office 365 multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Expanda a sua presença do Office 365 para várias regiões geográficas com o Office 365 multigeográfico.
ms.openlocfilehash: 7aa1933725617bcc1f84bbe6d0f31a6ddd91815d
ms.sourcegitcommit: a7b2adf4b55df5fc35a617a145e8177caefce28b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2019
ms.locfileid: "35078505"
---
# <a name="office-365-multi-geo"></a><span data-ttu-id="902e8-103">Office 365 multigeográfico</span><span class="sxs-lookup"><span data-stu-id="902e8-103">Office 365 Multi-Geo</span></span>

<span data-ttu-id="902e8-104">Com o Office 365 multigeográfico, sua organização poderá expandir sua presença do Office 365 para várias regiões geográficas e/ou os países em seu locatário existente.</span><span class="sxs-lookup"><span data-stu-id="902e8-104">With Office 365 Multi-Geo, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="902e8-105">Entre em contato com sua equipe de conta da Microsoft para inscrever sua empresa multinacional para o Office 365 multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="902e8-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Office 365 Multi-Geo.</span></span>
  
<span data-ttu-id="902e8-106">Com o Office 365 multigeográfico, você pode provisionar e armazenar dados em repouso nas localizações geográficas escolhidas para atender aos requisitos de residência de dados e, ao mesmo tempo, dar vazão à sua implantação global a partir de experiências de produtividade modernas para a sua força de trabalho.</span><span class="sxs-lookup"><span data-stu-id="902e8-106">With Office 365 Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="902e8-107">Vídeo: Apresentando o Office 365 multigeográfico</span><span class="sxs-lookup"><span data-stu-id="902e8-107">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="902e8-108">Em um ambiente multigeográfico, seu locatário do Office 365 consiste em um local central (onde a assinatura do Office 365 originalmente foi provisionada) e um ou mais locais do satélite.</span><span class="sxs-lookup"><span data-stu-id="902e8-108">In a Multi-Geo environment, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="902e8-109">Em um locatário multigeográfico, as informações sobre localizações geográficas, grupos e informações do usuário são dominadas no Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="902e8-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="902e8-110">Como as informações de locatário são dominadas centralmente e sincronizadas em cada localização geográfica, compartilhamento e experiências envolvendo qualquer pessoa da sua empresa contêm percepção global.</span><span class="sxs-lookup"><span data-stu-id="902e8-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![Captura de tela do menu do centro de administração do SharePoint](media/multi-geo-world-map.png)

<span data-ttu-id="902e8-112">Observe que o Office 365 multigeográfico não foi desenvolvido para otimizar o desempenho, foi projetado para atender aos requisitos de residência de dados.</span><span class="sxs-lookup"><span data-stu-id="902e8-112">Note that Office 365 Multi-Geo is not primarily designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="902e8-113">Para saber mais sobre a otimização do desempenho do Office 365, confira [planejamento de rede e ajuste de desempenho do Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou Fale com o suporte.</span><span class="sxs-lookup"><span data-stu-id="902e8-113">For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="902e8-114">Terminologia</span><span class="sxs-lookup"><span data-stu-id="902e8-114">Terminology</span></span>

<span data-ttu-id="902e8-115">Aqui estão os principais termos usados para descrever o Office 365 multigeográfico:</span><span class="sxs-lookup"><span data-stu-id="902e8-115">Here are the key terms used in describing Office 365 Multi-Geo:</span></span>

- <span data-ttu-id="902e8-116">**Uma localização central** -a localização geográfica onde seu locatário foi originalmente provisionado.</span><span class="sxs-lookup"><span data-stu-id="902e8-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="902e8-117">**Administrador geográfico**, um administrador que pode administrar um ou mais locais do satélite especificado.</span><span class="sxs-lookup"><span data-stu-id="902e8-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="902e8-118">**Geocódigo** -um código de três letras de uma localização geográfica determinada.</span><span class="sxs-lookup"><span data-stu-id="902e8-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="902e8-119">**Localização geográfica** – uma localização geográfica pode ser usada em um locatário multigeográfico para hospedar dados, incluindo caixas de correio do Exchange e o OneDrive e sites do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="902e8-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="902e8-120">**Preferenciais de dados local (PDL)** a propriedade do usuário definido pelo administrador que indica onde a localização geográfica onde a caixa de correio do Exchange usuários e do OneDrive devem ser provisionadas.</span><span class="sxs-lookup"><span data-stu-id="902e8-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="902e8-121">A PDL determina também onde os sites do SharePoint criados pelo usuário estão provisionados.</span><span class="sxs-lookup"><span data-stu-id="902e8-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="902e8-122">**Localização de satélite** – As localizações geográficas em que as cargas de trabalho geográficas do Office 365 (SharePoint, OneDrive e Exchange) estão habilitadas em um locatário multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="902e8-122">**Satellite location** – The geo locations where the geo-aware Office 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="902e8-123">**Locatário** – – a representação de uma organização no Office 365 que geralmente tem um ou mais domínios associados (por exemplo, contoso.com).</span><span class="sxs-lookup"><span data-stu-id="902e8-123">**Tenant** – An organization's representation in Office 365 which typically has one or more domains associated with it (for example, contoso.com).</span></span>

## <a name="office-365-multi-geo-availability"></a><span data-ttu-id="902e8-124">Disponibilidade do Office 365 multigeográfico</span><span class="sxs-lookup"><span data-stu-id="902e8-124">Office 365 Multi-Geo availability</span></span>

<span data-ttu-id="902e8-125">A multigeografia do Office 365 atualmente é oferecida nos países e regiões seguintes:</span><span class="sxs-lookup"><span data-stu-id="902e8-125">Office 365 Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="902e8-126">Introdução</span><span class="sxs-lookup"><span data-stu-id="902e8-126">Getting started</span></span>

<span data-ttu-id="902e8-127">Siga estas etapas para iniciar com o multigeográfico:</span><span class="sxs-lookup"><span data-stu-id="902e8-127">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="902e8-128">Trabalhe com a sua equipe de conta para adicionar o plano de serviço _Funcionalidades multigeográficas do Office 365_.</span><span class="sxs-lookup"><span data-stu-id="902e8-128">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span> <span data-ttu-id="902e8-129">Elas orientarão você ra adicionar o número de licenças necessárias.</span><span class="sxs-lookup"><span data-stu-id="902e8-129">They will guide you to add the number of licenses needed.</span></span> <span data-ttu-id="902e8-130">O recurso multigeográfico está disponível para clientes com um mínimo de 500 assinaturas do Office 365.</span><span class="sxs-lookup"><span data-stu-id="902e8-130">Multi-Geo feature is available to customers with a minimum of 2,500 Office 365 subscriptions.</span></span>

   <span data-ttu-id="902e8-131">Antes de começar a usar o Office 365 multigeográfico, a Microsoft precisa configurar seu locatário do Exchange Online para suporte multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="902e8-131">Before you can start using Office 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="902e8-132">Esse processo de configuração único é disparado após você solicitar o plano de serviço *Funcionalidades Multigeográficas no Office 365* e as licenças aparecem em seu locatário.</span><span class="sxs-lookup"><span data-stu-id="902e8-132">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Office 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="902e8-133">Você receberá notificações no [Centro de mensagens do Office 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) depois que as licenças multigeográficas são aplicadas e você pode começar configurar e usar recursos do Office 365 multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="902e8-133">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Office 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="902e8-134">Leia [planejar o ambiente multigeográfico](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="902e8-134">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="902e8-135">Saiba mais sobre [administrar um ambiente multigeográfico](administering-a-multi-geo-environment.md) e [como seus usuários terão o ambiente](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="902e8-135">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="902e8-136">Quando estiver pronto para configurar o Office 365 Multigeográfico, [configurar seu locatário multigeográfico](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="902e8-136">When you are ready to set up Office 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="902e8-137">[Configurar pesquisa](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="902e8-137">[Set up search](configure-search-for-multi-geo.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="902e8-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="902e8-138">See also</span></span>

[<span data-ttu-id="902e8-139">Multigeográfico no Exchange Online e no OneDrive</span><span class="sxs-lookup"><span data-stu-id="902e8-139">Multi-Geo in Exchange Online and OneDrive</span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="902e8-140">Recursos multigeográficos no OneDrive e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="902e8-140">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[<span data-ttu-id="902e8-141">Recursos multigeográficos no Exchange Online</span><span class="sxs-lookup"><span data-stu-id="902e8-141">Multi-Geo Capabilities in Exchange Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)
