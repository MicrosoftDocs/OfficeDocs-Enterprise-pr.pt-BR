---
title: Resposta de incidentes de segurança do Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/27/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: Essa solução informa a você que o mais comuns segurança na Internet ataques podem ter aparência no Office 365 e como responder a eles
ms.openlocfilehash: b9800070bde662603c731e2b8d64609b4f821cce
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="office-365-security-incident-response"></a><span data-ttu-id="4f55d-103">Resposta de incidentes de segurança do Office 365</span><span class="sxs-lookup"><span data-stu-id="4f55d-103">Office 365 Security Incident Response</span></span>

 <span data-ttu-id="4f55d-104">**Resumo:** Essa solução informa Cite os indicadores para os ataques de segurança na Internet mais comuns no Office 365, como confirmar positiva qualquer dado ataque e como responder a ele.</span><span class="sxs-lookup"><span data-stu-id="4f55d-104">**Summary:** This solution tells you what the indicators are for the most common cyber-security attacks in Office 365, how to positively confirm any given attack, and how to respond to it.</span></span>
  
## <a name="overview"></a><span data-ttu-id="4f55d-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="4f55d-105">Overview</span></span>
<span data-ttu-id="4f55d-p101">Nem todos os ataques virtuais podem ser impedidos. Os invasores estão sempre buscando novos pontos fracos em sua estratégia defensiva ou eles estão explorando as antigas. Sabendo como reconhecer um ataque permite que você responder com mais rapidez a ela, que diminuirá a duração de um incidente de segurança.</span><span class="sxs-lookup"><span data-stu-id="4f55d-p101">Not all cyber attacks can be thwarted. Attackers are constantly looking for new weaknesses in your defensive strategy or they are exploiting old ones. Knowing how to recognize an attack allows you to respond to it faster, which shortens the duration of the security incident.</span></span>

<span data-ttu-id="4f55d-p102">Esta série de artigo ajuda a entender o que um determinado tipo de ataque pode parecer com no Office 365 e fornece etapas a que seguir para responder. Eles são os pontos de entrada rápida Noções básicas sobre:</span><span class="sxs-lookup"><span data-stu-id="4f55d-p102">This series of article helps you understand what a particular type of attack might look like in Office 365 and gives you steps you can take to respond. They are quick entry points to understanding:</span></span>
 
- <span data-ttu-id="4f55d-111">O ataque que é e como ele funciona.</span><span class="sxs-lookup"><span data-stu-id="4f55d-111">What the attack is and how it works.</span></span>
- <span data-ttu-id="4f55d-112">O que entra, chamado indicadores de comprometimento (IOC), procurar e como procurá-los.</span><span class="sxs-lookup"><span data-stu-id="4f55d-112">What signs, called indicators of compromise (IOC), to look for and how to look for them.</span></span>
- <span data-ttu-id="4f55d-113">Como confirmar positiva o ataque.</span><span class="sxs-lookup"><span data-stu-id="4f55d-113">How to positively confirm the attack.</span></span>
- <span data-ttu-id="4f55d-114">Etapas a serem executadas para abreviada ataque e melhor protegem sua organização no futuro.</span><span class="sxs-lookup"><span data-stu-id="4f55d-114">Steps to take to cut off the attack and better protect your organization in the future.</span></span>
- <span data-ttu-id="4f55d-115">Links para informações detalhadas sobre cada tipo de ataque.</span><span class="sxs-lookup"><span data-stu-id="4f55d-115">Links to in-depth information on each attack type.</span></span>

<span data-ttu-id="4f55d-116">Volte mais tarde mensalmente mais artigos serão adicionados ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="4f55d-116">Check back here monthly as more articles will be added over time.</span></span>

## <a name="detect-and-remediate-articles"></a><span data-ttu-id="4f55d-117">Detectar e remediar artigos</span><span class="sxs-lookup"><span data-stu-id="4f55d-117">Detect and Remediate Articles</span></span>
- [<span data-ttu-id="4f55d-118">Detectar e remediar concede consentimento ilícito no Office 365</span><span class="sxs-lookup"><span data-stu-id="4f55d-118">Detect and Remediate Illicit Consent Grants in Office 365</span></span>](detect-and-remediate-illicit-consent-grants.md)
- [<span data-ttu-id="4f55d-119">Detectar e corrigir as regras do Outlook e ataques de inclusões de formulários personalizados no Office 365</span><span class="sxs-lookup"><span data-stu-id="4f55d-119">Detect and Remediate Outlook Rules and Custom Forms Injections Attacks in Office 365</span></span>](detect-and-remediate-outlook-rules-forms-attack.md)
 
## <a name="secure-office-365-like-a-cybersecurity-pro"></a><span data-ttu-id="4f55d-120">Proteger o Office 365 como um cybersecurity pro</span><span class="sxs-lookup"><span data-stu-id="4f55d-120">Secure Office 365 like a cybersecurity pro</span></span>
<span data-ttu-id="4f55d-p103">Sua assinatura do Office 365 é fornecido com um conjunto avançado de recursos de segurança que você pode usar para proteger seus dados e seus usuários.  Use o [mapa de segurança do Office 365: principais prioridades para os primeiros 30 dias, 90 dias e além](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) para implementar as práticas recomendadas para proteger seu locatário do Office 365 do Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4f55d-p103">Your Office 365 subscription comes with a powerful set of security capabilities that you can use to protect your data and your users.  Use the [Office 365 security roadmap: Top priorities for the first 30 days, 90 days, and beyond](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) to implement Microsoft recommended best practices for securing your Office 365 tenant.</span></span>
- <span data-ttu-id="4f55d-p104">Tarefas para realizar nos primeiros 30 dias.  Elas têm efeito imediato e são baixo impacto para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="4f55d-p104">Tasks to accomplish in the first 30 days.  These have immediate affect and are low-impact to your users.</span></span>
- <span data-ttu-id="4f55d-p105">Tarefas para realizar em 90 dias. Essas levar um pouco mais tempo para planejar e implementar mas melhorar consideravelmente sua situação de segurança</span><span class="sxs-lookup"><span data-stu-id="4f55d-p105">Tasks to accomplish in 90 days. These take a bit more time to plan and implement but greatly improve your security posture</span></span>
- <span data-ttu-id="4f55d-p106">Além de 90 dias. Esses aperfeiçoamentos se baseiam em seu primeiro trabalho de 90 dias.</span><span class="sxs-lookup"><span data-stu-id="4f55d-p106">Beyond 90 days. These enhancements build in your first 90 days work.</span></span>






