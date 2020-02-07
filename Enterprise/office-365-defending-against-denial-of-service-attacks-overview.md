---
title: Defesa contra ataques de negação de serviço no Office 365
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
description: Uma visão geral dos ataques de negação de serviço (DoS).
ms.openlocfilehash: 16378800fc7bb61b8f78e2c4c51eb7940cb45d17
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843583"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a><span data-ttu-id="a94fb-103">Defesa contra ataques de negação de serviço no Office 365</span><span class="sxs-lookup"><span data-stu-id="a94fb-103">Defend Against Denial-of-Service Attacks in Office 365</span></span>

## <a name="introduction"></a><span data-ttu-id="a94fb-104">Introdução</span><span class="sxs-lookup"><span data-stu-id="a94fb-104">Introduction</span></span>

<span data-ttu-id="a94fb-105">A Microsoft fornece uma infraestrutura confiável para mais de 200 serviços em nuvem hospedados em uma infraestrutura de nuvem global de mais de 100 datacenters.</span><span class="sxs-lookup"><span data-stu-id="a94fb-105">Microsoft delivers a trustworthy infrastructure for more than 200 cloud services hosted in a global cloud infrastructure of more than 100 datacenters.</span></span> <span data-ttu-id="a94fb-106">Entre eles:</span><span class="sxs-lookup"><span data-stu-id="a94fb-106">These include:</span></span>

- <span data-ttu-id="a94fb-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a94fb-107">Microsoft Azure</span></span>
- <span data-ttu-id="a94fb-108">Microsoft Bing</span><span class="sxs-lookup"><span data-stu-id="a94fb-108">Microsoft Bing</span></span>
- <span data-ttu-id="a94fb-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a94fb-109">Microsoft Dynamics 365</span></span>
- <span data-ttu-id="a94fb-110">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="a94fb-110">Microsoft Office 365</span></span>
- <span data-ttu-id="a94fb-111">Microsoft OneDrive</span><span class="sxs-lookup"><span data-stu-id="a94fb-111">Microsoft OneDrive</span></span>
- <span data-ttu-id="a94fb-112">Skype</span><span class="sxs-lookup"><span data-stu-id="a94fb-112">Skype</span></span>
- <span data-ttu-id="a94fb-113">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="a94fb-113">Xbox Live</span></span>

<span data-ttu-id="a94fb-114">Como uma organização global com uma presença de Internet significativa e muitas propriedades proeminentes da Internet que oferecem serviços em nuvem, a Microsoft é um grande alvo comum para hackers e outras pessoas mal-intencionadas.</span><span class="sxs-lookup"><span data-stu-id="a94fb-114">As a global organization with a significant Internet presence and many prominent Internet properties that provide cloud services, Microsoft is a large, common target for hackers and other malicious individuals.</span></span> <span data-ttu-id="a94fb-115">A camada de comunicação de rede entre clientes e a nuvem da Microsoft é um dos maiores alvos de ataques mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="a94fb-115">The network communication layer between clients and the Microsoft Cloud is one of the biggest targets of malicious attacks.</span></span> <span data-ttu-id="a94fb-116">Na verdade, a Microsoft está continuamente e persistentemente sob alguma forma de cyberattack baseados em rede.</span><span class="sxs-lookup"><span data-stu-id="a94fb-116">In fact, Microsoft is continuously and persistently under some form of network-based cyberattack.</span></span> <span data-ttu-id="a94fb-117">Com isso, a Microsoft usa princípios de segurança de defesa profunda para proteger seus serviços de nuvem e redes.</span><span class="sxs-lookup"><span data-stu-id="a94fb-117">In line with this, Microsoft uses defense-in-depth security principles to protect its cloud services and networks.</span></span> <span data-ttu-id="a94fb-118">Sem sistemas de mitigação confiáveis e persistentes que defendem contra esses ataques, os serviços em nuvem da Microsoft ficarão offline e indisponíveis para os clientes.</span><span class="sxs-lookup"><span data-stu-id="a94fb-118">Without reliable and persistent mitigation systems that defend against these attacks, Microsoft's cloud services would be offline and unavailable to customers.</span></span>

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a><span data-ttu-id="a94fb-119">Definição e sintomas de ataques de negação de serviço</span><span class="sxs-lookup"><span data-stu-id="a94fb-119">Definition and Symptoms of Denial-of-Service Attacks</span></span>

<span data-ttu-id="a94fb-120">Uma maneira de atacar os serviços de rede é criar muitas solicitações em relação aos hosts de serviço para sobrecarregar a rede e os servidores para negar o serviço a usuários legítimos.</span><span class="sxs-lookup"><span data-stu-id="a94fb-120">One way to attack network services is to create many requests against service hosts to overwhelm the network and servers to deny service to legitimate users.</span></span> <span data-ttu-id="a94fb-121">Isso é conhecido como um ataque de negação de serviço (DoS).</span><span class="sxs-lookup"><span data-stu-id="a94fb-121">This is referred to as a denial-of-service (DoS) attack.</span></span> <span data-ttu-id="a94fb-122">Quando o ataque é executado por vários atores, pontos de extremidade e/ou vetores, ele é conhecido como um ataque de negação de serviço distribuído (DDoS).</span><span class="sxs-lookup"><span data-stu-id="a94fb-122">When the attack is performed by multiple actors, endpoints, and/or vectors, it is referred to as a distributed denial-of-service (DDoS) attack.</span></span> <span data-ttu-id="a94fb-123">Embora os meios, motivos e metas variem, os ataques DoS e DDoS geralmente consistem em esforços para impedir que um serviço ou site da Internet funcione corretamente ou, de forma temporária ou indefinida.</span><span class="sxs-lookup"><span data-stu-id="a94fb-123">Although the means, motives, and targets vary, DoS and DDoS attacks generally consist of efforts to prevent an Internet site or service from functioning correctly or at all, either temporarily or indefinitely.</span></span>

<span data-ttu-id="a94fb-124">A [equipe de preparação para emergências dos Estados Unidos](https://www.us-cert.gov/) (US-CERT) define sintomas de ataques de dos para incluir:</span><span class="sxs-lookup"><span data-stu-id="a94fb-124">The [United States Computer Emergency Readiness Team](https://www.us-cert.gov/) (US-CERT) defines symptoms of DoS attacks to include:</span></span>

- <span data-ttu-id="a94fb-125">Desempenho de rede excepcionalmente lento (ao abrir arquivos ou acessar sites da Internet)</span><span class="sxs-lookup"><span data-stu-id="a94fb-125">Unusually slow network performance (when opening files or accessing Internet sites)</span></span>
- <span data-ttu-id="a94fb-126">Indisponibilidade de um site da Web</span><span class="sxs-lookup"><span data-stu-id="a94fb-126">Unavailability of a Web site</span></span>
- <span data-ttu-id="a94fb-127">Incapacidade de acessar um site da Web</span><span class="sxs-lookup"><span data-stu-id="a94fb-127">Inability to access a Web site</span></span>
- <span data-ttu-id="a94fb-128">Aumento considerável no spam recebido</span><span class="sxs-lookup"><span data-stu-id="a94fb-128">Dramatic increase in received spam</span></span>
- <span data-ttu-id="a94fb-129">Desconexão de uma conexão com a Internet sem fio ou com fio</span><span class="sxs-lookup"><span data-stu-id="a94fb-129">Disconnection of a wireless or wired Internet connection</span></span>
- <span data-ttu-id="a94fb-130">Perda de longo prazo do acesso à Web ou a qualquer serviço de Internet</span><span class="sxs-lookup"><span data-stu-id="a94fb-130">Long-term loss of access to the Web or any Internet services</span></span>

## <a name="related-topics"></a><span data-ttu-id="a94fb-131">Tópicos Relacionados</span><span class="sxs-lookup"><span data-stu-id="a94fb-131">Related Topics</span></span>

- [<span data-ttu-id="a94fb-132">Princípios básicos de defesa contra ataques de negação de serviço</span><span class="sxs-lookup"><span data-stu-id="a94fb-132">Core Principles of Defense Against Denial-of-Service Attacks</span></span>](office-365-core-principles-of-defense-against-dos-attacks.md)
- [<span data-ttu-id="a94fb-133">Estratégia de defesa de negação de serviço da Microsoft</span><span class="sxs-lookup"><span data-stu-id="a94fb-133">Microsoft's Denial-of-Service Defense Strategy</span></span>](office-365-microsoft-dos-defense-strategy.md)
- [<span data-ttu-id="a94fb-134">Defendendo os serviços de nuvem da Microsoft contra ataques de negação de serviço</span><span class="sxs-lookup"><span data-stu-id="a94fb-134">Defending Microsoft Cloud Services Against Denial-of-Service Attacks</span></span>](office-365-defending-cloud-services-against-dos-attacks.md)
