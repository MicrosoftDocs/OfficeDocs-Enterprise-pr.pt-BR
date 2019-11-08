---
title: Controles de isolamento do Office 365
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
description: 'Resumo: uma explicação dos controles de isolamento no Office 365.'
ms.openlocfilehash: a53826f7f11324986f3df59d9df806ea522cb7d6
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031196"
---
# <a name="office-365-isolation-controls"></a>Controles de isolamento do Office 365 

A Microsoft funciona continuamente para garantir que a arquitetura de vários locatários do Office 365 suporte a segurança de nível empresarial, confidencialidade, privacidade, integridade, local, internacional e [padrões](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)de disponibilidade. A escala e o escopo de serviços fornecidos pela Microsoft tornam difícil e não econômico gerenciar o Office 365 com uma interação humana significativa. Os serviços do Office 365 são fornecidos através de vários data centers distribuídos globalmente, cada um altamente automatizado com poucas operações que exigem um toque humano ou qualquer acesso ao conteúdo do cliente. Nossa equipe oferece suporte a esses serviços e data centers usando ferramentas automatizadas e acesso remoto altamente seguro. Para ver alguns dos detalhes sobre como os serviços em grande escala são operados no Office 365, confira [a bastidores, examine o Office 365 para profissionais de ti](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202).

O Office 365 é composto por vários serviços que fornecem funcionalidade comercial importante e contribuem para toda a experiência do Office 365. Cada um desses serviços é autônomo e projetado para integração entre si.

O Office 365 foi projetado com os seguintes princípios:

 - ** [Arquitetura orientada a serviços](https://msdn.microsoft.com/library/aa480021.aspx):** design e desenvolvimento de software na forma de serviços de interoperabilidade que fornecem funcionalidade comercial bem definida.
 - **[Garantia de segurança operacional](https://www.microsoft.com/download/details.aspx?id=40872):** uma estrutura que incorpora o conhecimento obtido por meio de vários recursos exclusivos da Microsoft, incluindo o ciclo de [vida do desenvolvimento da segurança](https://www.microsoft.com/sdl/default.aspx)da Microsoft, o [Microsoft Security Response Center](https://technet.microsoft.com/library/dn440717.aspx)e uma profunda percepção do panorama de ameaças do cybersecurity.

Os serviços do Office 365 interoperam entre si, mas foram projetados e implementados para que possam ser implantados e operados como serviços autônomos, independentemente uns dos outros. A Microsoft segregou as obrigações e áreas de responsabilidade do Office 365 para reduzir as oportunidades de modificação não autorizada ou incorreta ou uso indevido dos ativos da organização. O Office 365 Teams tem funções definidas como parte de um mecanismo abrangente de controle de acesso baseado em função.

## <a name="customer-content-isolation"></a>Isolamento de conteúdo do cliente

Todo o conteúdo do cliente em um locatário é isolado de outros locatários e de operações e dados de sistemas usados no gerenciamento do Office 365. Várias formas de proteção são implementadas em todo o Office 365 para minimizar o risco de comprometimento de qualquer serviço ou aplicativo do Office 365. Várias formas de proteção também impedem o acesso não autorizado às informações de locatários ou ao próprio sistema do Office 365.

Para obter informações sobre como a Microsoft implementa o isolamento lógico de dados de locatário no Office 365, consulte [isolamento de locatário no office 365](office-365-tenant-isolation-overview.md).
