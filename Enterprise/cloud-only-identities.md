---
title: Identidades somente na nuvem do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Descreve como criar usuários e grupos quando sua assinatura do Office 365 está usando identidades somente na nuvem.
ms.openlocfilehash: 5991ec838321187b58f913e1707efb2ede9912fb
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072273"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="2fe6c-103">Identidades somente na nuvem do Office 365</span><span class="sxs-lookup"><span data-stu-id="2fe6c-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="2fe6c-104">*Esse artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="2fe6c-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="2fe6c-105">Com a identidade somente na nuvem, todos os usuários, grupos e contatos são armazenados no locatário do Azure Active Directory (Azure AD) da sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="2fe6c-106">Estes são os componentes básicos da identidade somente na nuvem.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-106">Here are the basic components of cloud-only identity.</span></span>
 
![Os componentes básicos da identidade somente na nuvem](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="2fe6c-108">Os usuários e suas contas de usuário nas organizações podem ser categorizados de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="2fe6c-109">Por exemplo, alguns são funcionários e têm um status permanente.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="2fe6c-110">Alguns são fornecedores, contratadores ou parceiros que têm um status temporário.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="2fe6c-111">Alguns são usuários externos que não têm contas de usuário, mas ainda precisam ter acesso a serviços e recursos específicos para oferecer suporte à interação e à colaboração.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="2fe6c-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2fe6c-112">For example:</span></span>

- <span data-ttu-id="2fe6c-113">As contas do locatário representam os usuários em sua organização para os quais você atribui uma licença para os serviços de nuvem</span><span class="sxs-lookup"><span data-stu-id="2fe6c-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="2fe6c-114">As contas B2B (Business to Business) representam os usuários de fora da sua organização que você convida para participar da colaboração, fazem o estoque dos tipos de usuários para sua organização.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="2fe6c-115">Quais são os agrupamentos?</span><span class="sxs-lookup"><span data-stu-id="2fe6c-115">What are the groupings?</span></span> <span data-ttu-id="2fe6c-116">Por exemplo, você pode agrupar usuários por função ou finalidade de alto nível em sua organização.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-116">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="2fe6c-p104">Além disso, alguns serviços de nuvem podem ser compartilhados com usuários de fora de sua organização que não tenham contas de usuário. Você também precisará identificar esses grupos de usuários.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="2fe6c-119">Você pode usar grupos no Azure AD para várias finalidades que simplificam o gerenciamento de seu ambiente de nuvem.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-119">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="2fe6c-120">Por exemplo, com grupos do Azure AD, você pode:</span><span class="sxs-lookup"><span data-stu-id="2fe6c-120">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="2fe6c-121">Use o licenciamento baseado em grupo para atribuir licenças do Office 365 às contas de usuário automaticamente assim que elas forem adicionadas.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-121">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="2fe6c-122">Adicionar contas de usuário para grupos específicos de forma dinâmica com base em atributos das contas de usuário, como o departamento.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-122">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="2fe6c-123">Provisionar usuários automaticamente para aplicativos de Software como um Serviço (SaaS) e para proteger o acesso a esses aplicativos com a autenticação multifator e outras regras de acesso condicional.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-123">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="2fe6c-124">Provisione permissões e níveis de acesso para sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="2fe6c-124">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="2fe6c-125">Você pode criar novos ***usuários*** com:</span><span class="sxs-lookup"><span data-stu-id="2fe6c-125">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="2fe6c-126">O Centro de administração do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="2fe6c-126">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="2fe6c-127">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fe6c-127">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="2fe6c-128">Você pode criar novos ***grupos*** com:</span><span class="sxs-lookup"><span data-stu-id="2fe6c-128">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="2fe6c-129">O Centro de administração do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="2fe6c-129">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="2fe6c-130">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fe6c-130">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="2fe6c-131">Próxima etapa para identidades somente na nuvem</span><span class="sxs-lookup"><span data-stu-id="2fe6c-131">Next step for cloud-only identities</span></span>

[<span data-ttu-id="2fe6c-132">Atribuir licenças às contas de usuário</span><span class="sxs-lookup"><span data-stu-id="2fe6c-132">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
