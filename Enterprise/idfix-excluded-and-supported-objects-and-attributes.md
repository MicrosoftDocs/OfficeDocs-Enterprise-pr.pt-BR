---
title: Objetos e atributos excluídos e compatíveis com a IdFix
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
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085080"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="0f4c1-103">Objetos e atributos excluídos e compatíveis com a IdFix</span><span class="sxs-lookup"><span data-stu-id="0f4c1-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="0f4c1-p101">Há dois conjuntos de regras mantidos pelo IdFix: Multilocatário e Dedicado/ITAR. Neste momento, os dois conjuntos de regras excluem os mesmos objetos, atributos e valores de atributos de sua pesquisa. Isso pode mudar em futuras versões.</span><span class="sxs-lookup"><span data-stu-id="0f4c1-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="0f4c1-107">Exclusões de erros de Multilocatário e Dedicado usados pelo IdFix</span><span class="sxs-lookup"><span data-stu-id="0f4c1-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="0f4c1-p102">Esta seção lista os objetos, atributos e valores que o IdFix exclui da pesquisa do diretório. O asterisco (\*) é um curinga que pode ser substituído por outros caracteres.</span><span class="sxs-lookup"><span data-stu-id="0f4c1-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="0f4c1-110">Objetos, atributos e valores excluídos durante uma pesquisa do IdFix</span><span class="sxs-lookup"><span data-stu-id="0f4c1-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="0f4c1-111">**Exclusão**</span><span class="sxs-lookup"><span data-stu-id="0f4c1-111">**Exclusion**</span></span>|<span data-ttu-id="0f4c1-112">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="0f4c1-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0f4c1-113">Administrador\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-113">Admini\*</span></span> |<span data-ttu-id="0f4c1-114">Administrador</span><span class="sxs-lookup"><span data-stu-id="0f4c1-114">Administrator</span></span> |
|<span data-ttu-id="0f4c1-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-115">CAS_{\*</span></span>  |<span data-ttu-id="0f4c1-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="0f4c1-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="0f4c1-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="0f4c1-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="0f4c1-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="0f4c1-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-119">FederatedEmail\*</span></span> |<span data-ttu-id="0f4c1-p103">FederatedEmail. *GUID*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="0f4c1-122">Convidado\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-122">Guest\*</span></span> ||
|<span data-ttu-id="0f4c1-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-123">HTTPConnector\*</span></span>  |<span data-ttu-id="0f4c1-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="0f4c1-124">HTTPConnector</span></span> |
|<span data-ttu-id="0f4c1-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-125">krbtgt\*</span></span> |<span data-ttu-id="0f4c1-126">ms-DS-KrbTgt-link</span><span class="sxs-lookup"><span data-stu-id="0f4c1-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="0f4c1-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-127">iusr_\*</span></span> |<span data-ttu-id="0f4c1-128">IUSR _ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="0f4c1-129">Iwan\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-129">iwam\*</span></span>  |<span data-ttu-id="0f4c1-130">IWAM _ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="0f4c1-131">MSol\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-131">msol\*</span></span> |<span data-ttu-id="0f4c1-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="0f4c1-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="0f4c1-133">à\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-133">support_\*</span></span> ||
|<span data-ttu-id="0f4c1-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-134">SystemMailbox\*</span></span> |<span data-ttu-id="0f4c1-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="0f4c1-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="0f4c1-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="0f4c1-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="0f4c1-137">distinguishedName contém "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="0f4c1-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="0f4c1-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="0f4c1-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="0f4c1-139">O objeto contém o atributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="0f4c1-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="0f4c1-140">ConFira o [atributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="0f4c1-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="0f4c1-141">Atributos e objetos de Multilocatário e Dedicado verificados pelo IdFix</span><span class="sxs-lookup"><span data-stu-id="0f4c1-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="0f4c1-142">Os atributos que são verificados em busca de erros pelo IdFix são descritos na seção "objeto de diretório e preparação de atributo" em [preparar atributos de diretório para sincronização com o Office 365 usando a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="0f4c1-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

