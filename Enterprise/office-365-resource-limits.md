---
title: Limites de recursos do Office 365
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
description: 'Resumo: informações sobre os limites de recursos para os vários aplicativos no Office 365.'
ms.openlocfilehash: 7ccbf2bdfe359dd44a0b03dcf6e2aed8d5daedbe
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035481"
---
# <a name="resource-limits"></a>Limites de recurso

Os limites de recursos são impostos usando cotas (limites) e limitação. O Azure Active Directory e os serviços individuais do Office 365 usam ambos. Os limites são específicos de serviço e mudam com o tempo à medida que novos recursos são adicionados. Para obter detalhes sobre os limites atuais para os vários serviços, consulte os seguintes tópicos:

- [Limites e restrições de serviços do Active Directory do Azure](https://msdn.microsoft.com/library/azure/dn764971.aspx)
- [Limites do Exchange Online](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Limites do Exchange Online Protection](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [Limites e limites de software do SharePoint Online](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Limites do Skype for Business](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [API REST do Yammer e limites de taxa](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Limites de tamanho de arquivo no Sway](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

Além desses limites, vários mecanismos de limitação são usados no Azure Active Directory e no Office 365. A limitação do serviço é especialmente importante, Considerando que os recursos de rede nos datacenters da Microsoft são otimizados para o amplo conjunto de clientes que usam os serviços. Os mecanismos de limitação incluem:

- O Azure Active Directory e o Office 365 recurso de limitação de nível de usuário, que limitam o número de transações ou chamadas simultâneas (por script ou código) que podem ser realizadas por um único usuário.
- Uma política padrão de limitação do PowerShell é atribuída a cada locatário na criação de locatário. Essas configurações afetam outros itens, como o número máximo de sessões simultâneas do PowerShell que podem ser abertas por um único administrador.
- Cada cliente do Exchange Online tem uma política de serviços Web do Exchange (EWS) padrão ajustada para operações do cliente EWS e limitação que se aplica a todos os clientes do Outlook.
