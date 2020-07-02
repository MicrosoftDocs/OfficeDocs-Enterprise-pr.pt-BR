---
title: Proteção contra ataques de negação de serviço no Microsoft 365
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
- M365-security-compliance
f1.keywords:
- NOCSH
description: Uma visão geral dos ataques de negação de serviço (DoS).
ms.openlocfilehash: 2cbe5eb86402fd7b7888f39440a58935604c90eb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998415"
---
# <a name="defend-against-denial-of-service-attacks-in-microsoft-365"></a>Proteção contra ataques de negação de serviço no Microsoft 365

## <a name="introduction"></a>Introdução

A Microsoft fornece uma infraestrutura confiável para mais de 200 serviços em nuvem hospedados em uma infraestrutura de nuvem global de mais de 100 datacenters. Entre eles:

- Microsoft Azure
- Microsoft Bing
- Microsoft Dynamics 365
- Microsoft 365 e Office 365
- Microsoft OneDrive
- Skype
- Xbox Live

Como uma organização global com uma presença de Internet significativa e muitas propriedades proeminentes da Internet que oferecem serviços em nuvem, a Microsoft é um grande alvo comum para hackers e outras pessoas mal-intencionadas. A camada de comunicação de rede entre clientes e a nuvem da Microsoft é um dos maiores alvos de ataques mal-intencionados. Na verdade, a Microsoft está continuamente e persistentemente sob alguma forma de cyberattack baseados em rede. Com isso, a Microsoft usa princípios de segurança de defesa profunda para proteger seus serviços de nuvem e redes. Sem sistemas de mitigação confiáveis e persistentes que defendem contra esses ataques, os serviços em nuvem da Microsoft ficarão offline e indisponíveis para os clientes.

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a>Definição e sintomas de ataques de negação de serviço

Uma maneira de atacar os serviços de rede é criar muitas solicitações em relação aos hosts de serviço para sobrecarregar a rede e os servidores para negar o serviço a usuários legítimos. Isso é conhecido como um ataque de negação de serviço (DoS). Quando o ataque é executado por vários atores, pontos de extremidade e/ou vetores, ele é conhecido como um ataque de negação de serviço distribuído (DDoS). Embora os meios, motivos e metas variem, os ataques DoS e DDoS geralmente consistem em esforços para impedir que um serviço ou site da Internet funcione corretamente ou, de forma temporária ou indefinida.

A [equipe de preparação para emergências dos Estados Unidos](https://www.us-cert.gov/) (US-CERT) define sintomas de ataques de dos para incluir:

- Desempenho de rede excepcionalmente lento (ao abrir arquivos ou acessar sites da Internet)
- Indisponibilidade de um site da Web
- Incapacidade de acessar um site da Web
- Aumento considerável no spam recebido
- Desconexão de uma conexão com a Internet sem fio ou com fio
- Perda de longo prazo do acesso à Web ou a qualquer serviço de Internet

## <a name="related-topics"></a>Tópicos Relacionados

- [Princípios básicos de defesa contra ataques de negação de serviço](office-365-core-principles-of-defense-against-dos-attacks.md)
- [Estratégia de defesa de negação de serviço da Microsoft](office-365-microsoft-dos-defense-strategy.md)
- [Defendendo os serviços de nuvem da Microsoft contra ataques de negação de serviço](office-365-defending-cloud-services-against-dos-attacks.md)
