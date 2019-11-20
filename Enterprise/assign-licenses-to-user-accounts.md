---
title: Atribuir licenças do Office 365 a contas de usuário
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
description: Descreve como atribuir licenças do Office 365 a contas de usuário, individualmente ou com base na associação de grupo.
ms.openlocfilehash: bc736236f9371ee1372fd36af4a707aca2ee1408
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745704"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="49863-103">Atribuir licenças do Office 365 a contas de usuário</span><span class="sxs-lookup"><span data-stu-id="49863-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="49863-104">*Este artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="49863-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="49863-105">Para o modelo de identidade somente na nuvem, você pode atribuir licenças do Office 365 a contas de usuário à medida que elas são criadas, dependendo de como você as cria.</span><span class="sxs-lookup"><span data-stu-id="49863-105">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="49863-106">Para o modelo de identidade híbrida, quando as contas de usuário dos serviços de domínio Active Directory (AD DS) são sincronizadas pela primeira vez, elas não recebem automaticamente uma licença do Office 365.</span><span class="sxs-lookup"><span data-stu-id="49863-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="49863-107">Em ambos os casos, você deve atribuir uma licença às contas de usuário para que seus usuários possam acessar os serviços do Office 365, como email e Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="49863-107">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="49863-108">Você pode atribuir licenças a contas de usuário individualmente ou automaticamente através da Associação de grupo.</span><span class="sxs-lookup"><span data-stu-id="49863-108">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="49863-109">Para atribuir licenças do Office 365 a contas de usuário individuais, você pode usar:</span><span class="sxs-lookup"><span data-stu-id="49863-109">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="49863-110">O Centro de administração do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="49863-110">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="49863-111">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="49863-111">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="49863-112">Para atribuição de licença automática, confira [Licenciamento baseado em grupo no Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="49863-112">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="49863-113">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="49863-113">Next steps</span></span>

<span data-ttu-id="49863-114">Com o conjunto completo de contas de usuário às quais foram atribuídas licenças, agora você está pronto para:</span><span class="sxs-lookup"><span data-stu-id="49863-114">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="49863-115">Implementar a segurança</span><span class="sxs-lookup"><span data-stu-id="49863-115">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="49863-116">Implantar software cliente, como o Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="49863-116">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="49863-117">Configurar o gerenciamento de dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="49863-117">Configure mobile device management</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="49863-118">Configurar serviços e aplicativos</span><span class="sxs-lookup"><span data-stu-id="49863-118">Configure services and applications</span></span>](configure-services-and-applications.md)
