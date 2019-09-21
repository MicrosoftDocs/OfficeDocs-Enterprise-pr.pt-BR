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
description: 'Resumo: um resumo dos vários controles de acesso de monitoramento e auditoria disponíveis no Office 365.'
ms.openlocfilehash: 00f0032afa85905ed5b1e0c4e016ea218207fc34
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067126"
---
# <a name="monitoring-and-auditing-access-controls-in-office-365"></a>Monitoramento e auditoria de controles de acesso no Office 365

A Microsoft executa monitoramento e auditoria abrangentes de todos os privilégios, delegação e operações que ocorrem no Office 365. O controle de acesso do Office 365 é um processo automatizado desenvolvido com base no princípio de privilégio mínimo e para incorporar auditorias e controles de acesso a dados:

- Todo o acesso permitido é rastreável para um usuário exclusivo. Os administradores são responsáveis por lidar com o conteúdo do cliente.
- Solicitações de controle de acesso, aprovações e logs de operações administrativas são capturadas para análise de segurança e eventos mal-intencionados.
- Os níveis de acesso são analisados quase em tempo real com base na associação de grupo de segurança para garantir que apenas usuários com justificativas de negócios autorizadas e atendam aos requisitos de qualificação tenham acesso aos sistemas.
- O Office 365, seus controles de acesso e serviços de suporte, incluindo o Azure Active Directory e datacenters físicos, são auditados regularmente por terceiros independentes para conformidade com [ISO/iec 27001](https://www.microsoft.com/en-us/TrustCenter/Compliance/iso-iec-27001), [ISO/IEC 27018](https://www.microsoft.com/en-us/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/en-us/TrustCenter/Compliance/SOC), [ FedRAMP](https://www.microsoft.com/en-us/TrustCenter/Compliance/FedRAMP)e outros [padrões](https://www.microsoft.com/en-us/TrustCenter/Compliance?service=Office#Icons).
- Os engenheiros do Office 365 devem fazer um treinamento de segurança anual, examinar os melhores procedimentos de acesso elevado e reconhecer as políticas de segurança e privacidade da Microsoft para manter os direitos para o serviço.

O gatilho automatizado avisa quando é detectada atividade suspeita, como vários logons com falha dentro de um curto período de tempo. A equipe de resposta de segurança do Office 365 usa o Machine Learning e a grande análise de dados para analisar e analisar a atividade, procurar padrões de acesso irregular e responder proativamente a atividades anômalas e ilícitas. A Microsoft também emprega uma equipe dedicada de testadores de penetração e participa da equipe vermelha periódica e de exercícios de equipe azuis para encontrar problemas de segurança e controle de acesso no serviço. Os clientes podem verificar a eficácia dos sistemas de controle de acesso usando os relatórios de auditoria e a API de atividade de gerenciamento fornecida pelo Office 365.

Para obter mais informações, consulte referência e auditoria da [API de atividade de gerenciamento do office 365](https://msdn.microsoft.com/en-us/library/office/mt227394.aspx) e [relatórios no Office 365](office-365-auditing-and-reporting-overview.md).
