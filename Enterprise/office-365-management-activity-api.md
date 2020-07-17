---
title: API da Atividade de Gerenciamento do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-analytics
f1.keywords:
- NOCSH
description: Um breve resumo sobre a API da atividade de gerenciamento do Office 365.
ms.openlocfilehash: 8c7e4723ffb1792847c4b4eca0ec8285b8848c98
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998670"
---
# <a name="office-365-management-activity-api"></a><span data-ttu-id="e5aa5-103">API da Atividade de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="e5aa5-103">Office 365 Management Activity API</span></span>

<span data-ttu-id="e5aa5-104">A Microsoft fornece o Reporting Services que você pode usar para obter informações transacionais agregadas sobre o locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-104">Microsoft provides reporting services you can use to obtain aggregated transactional information about your Office 365 tenant.</span></span> <span data-ttu-id="e5aa5-105">A [API de atividade de gerenciamento do Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview#office-365-management-activity-api) usa um design RESTful padrão da indústria e o OAuth v2 para autenticação.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-105">The [Office 365 Management Activity API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview#office-365-management-activity-api) uses an industry-standard RESTful design and OAuth v2 for authentication.</span></span> <span data-ttu-id="e5aa5-106">Isso facilita a tarefa de começar a experimentar a recuperação de dados e a inclusão em ferramentas e aplicativos de visualização.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-106">This makes it easy to start experimenting with retrieving data and ingesting it into visualization tools and applications.</span></span> <span data-ttu-id="e5aa5-107">A API fornece um feed de dados com informações sobre o usuário, administrador, operações e atividade de segurança no Office 365.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-107">The API provides a data feed with information about user, administrator, operations, and security activity in Office 365.</span></span> <span data-ttu-id="e5aa5-108">Os dados podem ser mantidos por razões regulamentares ou combinados com os dados de log obtidos de uma infraestrutura local ou de outras fontes.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-108">The data can be kept for regulatory purposes, or combined with log data procured from an on-premises infrastructure or other sources.</span></span> <span data-ttu-id="e5aa5-109">Isso ajuda a criar uma solução de monitoramento para operações, segurança e conformidade em toda a empresa.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-109">This helps build a monitoring solution for operations, security, and compliance across the enterprise.</span></span>

<span data-ttu-id="e5aa5-110">A API da Atividade de Gerenciamento do Office 365 fornece informações sobre várias ações e eventos de usuário, administração, sistema e políticas dos logs de atividades do Office 365 e do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-110">The Office 365 Management Activity API provides information about various user, admin, system, and policy actions and events from Office 365 and Azure Active Directory activity logs.</span></span> <span data-ttu-id="e5aa5-111">A API fornece um esquema de auditoria consistente com mais de 10 campos comuns em todos os serviços.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-111">The API provides a consistent audit schema with over 10 fields common across all the services.</span></span> <span data-ttu-id="e5aa5-112">A API permite que as organizações façam conexões fáceis entre eventos e permite que as novas maneiras de fazer isso nos dados.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-112">The API allows organizations to make easy connections between events, and enables new ways to reason over the data.</span></span>

<span data-ttu-id="e5aa5-113">Dezenas de ISVs (fornecedores independentes de software) parceiros com a Microsoft e criaram soluções com base na API.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-113">Dozens of Independent Software Vendors (ISVs) partnered with Microsoft and have built solutions based on the API.</span></span> <span data-ttu-id="e5aa5-114">Algumas soluções se concentram exclusivamente nos dados do Office 365 e outros dados de origem de vários provedores de nuvem e sistemas locais para criar uma visão unificada das operações, segurança e atividade relacionada à conformidade.</span><span class="sxs-lookup"><span data-stu-id="e5aa5-114">Some solutions focus solely on Office 365 data and others source data from multiple cloud providers and on-premises systems to create a unified view of operations, security, and compliance-related activity.</span></span> 

<span data-ttu-id="e5aa5-115">Para obter mais informações, consulte a [referência da API da atividade de gerenciamento do Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference).</span><span class="sxs-lookup"><span data-stu-id="e5aa5-115">For more information, see the [Office 365 Management Activity API reference](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference).</span></span>
