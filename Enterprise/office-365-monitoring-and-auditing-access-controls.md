---
title: Controles de acesso de monitoramento e auditoria do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 'Resumo: um resumo dos vários controles de acesso de monitoramento e auditoria disponíveis no Office 365.'
ms.openlocfilehash: 300d5efa2b448e8e5219eb88f3d736eeba66f2d6
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41842598"
---
# <a name="monitoring-and-auditing-access-controls-in-office-365"></a><span data-ttu-id="1c7d3-103">Monitoramento e auditoria de controles de acesso no Office 365</span><span class="sxs-lookup"><span data-stu-id="1c7d3-103">Monitoring and Auditing Access Controls in Office 365</span></span>

<span data-ttu-id="1c7d3-104">A Microsoft executa monitoramento e auditoria abrangentes de todos os privilégios, delegação e operações que ocorrem no Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-104">Microsoft performs extensive monitoring and auditing of all delegation, privileges, and operations that occur within Office 365.</span></span> <span data-ttu-id="1c7d3-105">O controle de acesso do Office 365 é um processo automatizado desenvolvido com base no princípio de privilégio mínimo e para incorporar auditorias e controles de acesso a dados:</span><span class="sxs-lookup"><span data-stu-id="1c7d3-105">Office 365 access control is an automated process built on the principle of least privilege and incorporate data access controls and audits:</span></span>

- <span data-ttu-id="1c7d3-106">Todo o acesso permitido é rastreável para um usuário exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-106">All permitted access is traceable to a unique user.</span></span> <span data-ttu-id="1c7d3-107">Os administradores são responsáveis por lidar com o conteúdo do cliente.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-107">Administrators are accountable for their handling of customer content.</span></span>
- <span data-ttu-id="1c7d3-108">Solicitações de controle de acesso, aprovações e logs de operações administrativas são capturadas para análise de segurança e eventos mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-108">Access control requests, approvals, and administrative operations logs are captured for analysis of security and malicious events.</span></span>
- <span data-ttu-id="1c7d3-109">Os níveis de acesso são analisados quase em tempo real com base na associação de grupo de segurança para garantir que apenas usuários com justificativas de negócios autorizadas e atendam aos requisitos de qualificação tenham acesso aos sistemas.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-109">Access levels are reviewed in near real-time based on security group membership to ensure that only users who have authorized business justifications and meet the eligibility requirements have access to the systems.</span></span>
- <span data-ttu-id="1c7d3-110">O Office 365, seus controles de acesso e serviços de suporte, incluindo o Azure Active Directory e datacenters físicos, são auditados regularmente por terceiros independentes para conformidade com [ISO/iec 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [ISO/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)e outros [padrões](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span><span class="sxs-lookup"><span data-stu-id="1c7d3-110">Office 365, its access controls, and supporting services, including Azure Active Directory and physical datacenters, are regularly audited by independent third-parties for compliance with [ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [ISO/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP), and other [standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span></span>
- <span data-ttu-id="1c7d3-111">Os engenheiros do Office 365 devem fazer um treinamento de segurança anual, examinar os melhores procedimentos de acesso elevado e reconhecer as políticas de segurança e privacidade da Microsoft para manter os direitos para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-111">Office 365 engineers must take yearly security training, review elevated access best procedures, and acknowledge Microsoft's security and privacy policies to maintain entitlements to the service.</span></span>

<span data-ttu-id="1c7d3-112">O gatilho automatizado avisa quando é detectada atividade suspeita, como vários logons com falha dentro de um curto período de tempo.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-112">Automated alerts trigger when suspicious activity is detected, such as multiple failed logins within a short period.</span></span> <span data-ttu-id="1c7d3-113">A equipe de resposta de segurança do Office 365 usa o Machine Learning e a grande análise de dados para analisar e analisar a atividade, procurar padrões de acesso irregular e responder proativamente a atividades anômalas e ilícitas.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-113">The Office 365 Security Response team uses machine learning and big data analysis to review and analyze activity, look for irregular access patterns, and proactively respond to anomalous and illicit activities.</span></span> <span data-ttu-id="1c7d3-114">A Microsoft também emprega uma equipe dedicada de testadores de penetração e participa da equipe vermelha periódica e de exercícios de equipe azuis para encontrar problemas de segurança e controle de acesso no serviço.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-114">Microsoft also employs a dedicated team of penetration testers and engages in periodic Red Team and Blue Team exercises to find security and access control issues in the service.</span></span> <span data-ttu-id="1c7d3-115">Os clientes podem verificar a eficácia dos sistemas de controle de acesso usando os relatórios de auditoria e a API de atividade de gerenciamento fornecida pelo Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c7d3-115">Customers can verify the effectiveness of access control systems by using audit reports and the management activity API provided by Office 365.</span></span>

<span data-ttu-id="1c7d3-116">Para obter mais informações, consulte referência e auditoria da [API de atividade de gerenciamento do office 365](https://msdn.microsoft.com/library/office/mt227394.aspx) e [relatórios no Office 365](office-365-auditing-and-reporting-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c7d3-116">For more information, see [Office 365 Management Activity API reference](https://msdn.microsoft.com/library/office/mt227394.aspx) and [Auditing and Reporting in Office 365](office-365-auditing-and-reporting-overview.md).</span></span>
