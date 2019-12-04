---
title: Objetos e atributos excluídos e suportados pelo IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Lista os atributos que são excluídos e suportados pela ferramenta IdFix.
ms.openlocfilehash: e57507688fe1efd21bb629b4fad297129eff55d6
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813921"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="aa5c7-103">Objetos e atributos excluídos e suportados pelo IdFix</span><span class="sxs-lookup"><span data-stu-id="aa5c7-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="aa5c7-104">*Esse artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="aa5c7-105">Há dois conjuntos de regras mantidas pelo IdFix; Multilocatário e dedicado/ITAR.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="aa5c7-106">No momento, os dois conjuntos de regras excluem os mesmos objetos, atributos e valores de atributo de sua pesquisa.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="aa5c7-107">Isso pode ser alterado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="aa5c7-108">Exclusões de erro de vários locatários e dedicados usadas pelo IdFix</span><span class="sxs-lookup"><span data-stu-id="aa5c7-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="aa5c7-109">Esta seção lista os objetos, atributos e valores que o IdFix exclui da pesquisa do diretório.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="aa5c7-110">O asterisco (\*) é um curinga que pode ser substituído por outros caracteres.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="aa5c7-111">Objetos, atributos e valores excluídos durante uma pesquisa do IdFix</span><span class="sxs-lookup"><span data-stu-id="aa5c7-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="aa5c7-112">**Exclusão**</span><span class="sxs-lookup"><span data-stu-id="aa5c7-112">**Exclusion**</span></span>|<span data-ttu-id="aa5c7-113">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="aa5c7-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="aa5c7-114">Administrador\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-114">Admini\*</span></span> |<span data-ttu-id="aa5c7-115">Administrador</span><span class="sxs-lookup"><span data-stu-id="aa5c7-115">Administrator</span></span> |
|<span data-ttu-id="aa5c7-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-116">CAS_{\*</span></span>  |<span data-ttu-id="aa5c7-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="aa5c7-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="aa5c7-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="aa5c7-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="aa5c7-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="aa5c7-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-120">FederatedEmail\*</span></span> |<span data-ttu-id="aa5c7-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="aa5c7-121">FederatedEmail.</span></span> <span data-ttu-id="aa5c7-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-122">*GUID*</span></span> |
|<span data-ttu-id="aa5c7-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-123">Guest\*</span></span> ||
|<span data-ttu-id="aa5c7-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-124">HTTPConnector\*</span></span>  |<span data-ttu-id="aa5c7-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="aa5c7-125">HTTPConnector</span></span> |
|<span data-ttu-id="aa5c7-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-126">krbtgt\*</span></span> |<span data-ttu-id="aa5c7-127">ms-DS-KrbTgt-link</span><span class="sxs-lookup"><span data-stu-id="aa5c7-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="aa5c7-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-128">iusr_\*</span></span> |<span data-ttu-id="aa5c7-129">iusr_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="aa5c7-130">Iwan\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-130">iwam\*</span></span>  |<span data-ttu-id="aa5c7-131">IWAM_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="aa5c7-132">MSol\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-132">msol\*</span></span> |<span data-ttu-id="aa5c7-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="aa5c7-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="aa5c7-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-134">support_\*</span></span> ||
|<span data-ttu-id="aa5c7-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-135">SystemMailbox\*</span></span> |<span data-ttu-id="aa5c7-136">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="aa5c7-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="aa5c7-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="aa5c7-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="aa5c7-138">distinguishedName contém "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="aa5c7-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="aa5c7-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="aa5c7-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="aa5c7-140">Objeto contém o atributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="aa5c7-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="aa5c7-141">Confira o [atributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="aa5c7-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="aa5c7-142">Objetos e atributos de vários locatários e dedicados verificados por IdFix</span><span class="sxs-lookup"><span data-stu-id="aa5c7-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="aa5c7-143">Os atributos que são verificados em busca de erros pelo IdFix são descritos na seção "objeto de diretório e preparação de atributo" em [preparar atributos de diretório para sincronização com o Office 365 usando a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="aa5c7-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

