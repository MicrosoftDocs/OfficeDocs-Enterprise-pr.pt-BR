---
title: Objetos e atributos excluídos e suportados pelo IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
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
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487177"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="d25fe-103">Objetos e atributos excluídos e suportados pelo IdFix</span><span class="sxs-lookup"><span data-stu-id="d25fe-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="d25fe-104">Há dois conjuntos de regras mantidas pelo IdFix; Multilocatário e dedicado/ITAR.</span><span class="sxs-lookup"><span data-stu-id="d25fe-104">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="d25fe-105">No momento, os dois conjuntos de regras excluem os mesmos objetos, atributos e valores de atributo de sua pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d25fe-105">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="d25fe-106">Isso pode ser alterado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="d25fe-106">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="d25fe-107">Exclusões de erro de vários locatários e dedicados usadas pelo IdFix</span><span class="sxs-lookup"><span data-stu-id="d25fe-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="d25fe-108">Esta seção lista os objetos, atributos e valores que o IdFix exclui da pesquisa do diretório.</span><span class="sxs-lookup"><span data-stu-id="d25fe-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="d25fe-109">O asterisco (\*) é um curinga que pode ser substituído por outros caracteres.</span><span class="sxs-lookup"><span data-stu-id="d25fe-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="d25fe-110">Objetos, atributos e valores excluídos durante uma pesquisa do IdFix</span><span class="sxs-lookup"><span data-stu-id="d25fe-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="d25fe-111">**Exclusão**</span><span class="sxs-lookup"><span data-stu-id="d25fe-111">**Exclusion**</span></span>|<span data-ttu-id="d25fe-112">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="d25fe-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d25fe-113">Administrador\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-113">Admini\*</span></span> |<span data-ttu-id="d25fe-114">Administrador</span><span class="sxs-lookup"><span data-stu-id="d25fe-114">Administrator</span></span> |
|<span data-ttu-id="d25fe-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-115">CAS_{\*</span></span>  |<span data-ttu-id="d25fe-116">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="d25fe-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="d25fe-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="d25fe-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="d25fe-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="d25fe-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-119">FederatedEmail\*</span></span> |<span data-ttu-id="d25fe-120">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="d25fe-120">FederatedEmail.</span></span> <span data-ttu-id="d25fe-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="d25fe-121">*GUID*</span></span> |
|<span data-ttu-id="d25fe-122">Guest\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-122">Guest\*</span></span> ||
|<span data-ttu-id="d25fe-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-123">HTTPConnector\*</span></span>  |<span data-ttu-id="d25fe-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="d25fe-124">HTTPConnector</span></span> |
|<span data-ttu-id="d25fe-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-125">krbtgt\*</span></span> |<span data-ttu-id="d25fe-126">ms-DS-KrbTgt-link</span><span class="sxs-lookup"><span data-stu-id="d25fe-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="d25fe-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-127">iusr_\*</span></span> |<span data-ttu-id="d25fe-128">IUSR _ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="d25fe-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="d25fe-129">Iwan\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-129">iwam\*</span></span>  |<span data-ttu-id="d25fe-130">IWAM _ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="d25fe-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="d25fe-131">MSol\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-131">msol\*</span></span> |<span data-ttu-id="d25fe-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="d25fe-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="d25fe-133">à\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-133">support_\*</span></span> ||
|<span data-ttu-id="d25fe-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-134">SystemMailbox\*</span></span> |<span data-ttu-id="d25fe-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="d25fe-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="d25fe-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="d25fe-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="d25fe-137">distinguishedName contém "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="d25fe-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="d25fe-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="d25fe-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="d25fe-139">Objeto contém o atributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="d25fe-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="d25fe-140">ConFira o [atributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="d25fe-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="d25fe-141">Objetos e atributos de vários locatários e dedicados verificados por IdFix</span><span class="sxs-lookup"><span data-stu-id="d25fe-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="d25fe-142">Os atributos que são verificados em busca de erros pelo IdFix são descritos na seção "objeto de diretório e preparação de atributo" em [preparar atributos de diretório para sincronização com o Office 365 usando a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="d25fe-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

