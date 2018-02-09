---
title: "Contas de usuário para a Contoso Corporation, licenças e assinaturas"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "Resumo: Compreenda a estrutura de locatários, contas de usuário, licenças e assinaturas de nuvem da Contoso."
ms.openlocfilehash: 6e62fbbc0f52019e5d233fc73992b000952344f5
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>Contas de usuário para a Contoso Corporation, licenças e assinaturas

 **Resumo:** Compreenda a estrutura de locatários, contas de usuário, licenças e assinaturas de nuvem da Contoso.
  
Para fornecer um uso consistente de identidades e cobrança para todas as ofertas de nuvem, a Microsoft fornece a que hierarquia de contas de um organização/assinaturas/licenças/usuário:
  
- Organização
    
    A entidade de negócios que está usando ofertas de nuvem da Microsoft, normalmente identificadas por um nome de domínio DNS público, por exemplo, contoso.com.
    
- Assinaturas
    
    Para Microsoft SaaS nuvem ofertas (Office 365, Intune/EMS e Dynamics 365), uma assinatura é um produto específico e um conjunto de aquisição de licenças de usuário. Para o Windows Azure, uma assinatura permite faturamento dos serviços de nuvem consumido para a organização.
    
- Licenças
    
    Para ofertas de nuvem da Microsoft SaaS, uma licença permite que uma conta de usuário específica usar os serviços de nuvem. Para o Windows Azure, licenças de software são criadas no preço de serviço, mas, em alguns casos, que você precisará adquirir licenças de software adicional.
    
- Contas do usuário
    
    Contas de usuário são armazenadas em um locatário do Azure AD e possam ser sincronizadas a partir de um provedor de identidade, como o Windows Server AD local.
    
## <a name="contosos-structure"></a>Estrutura da Contoso

Contoso determinados a estrutura para a organização e suas assinaturas, licenças, contas e inquilinos a seguir:
  
**Figura 1: Da Contoso organização, assinaturas, licenças, contas de usuário e locatários**

![Organização, assinaturas, licenças, contas de usuário e locatários da Contoso](images/Contoso_Poster/Subscriptions.png)
  
A Figura 1 mostra como a organização Contoso inclui diversas assinaturas e está vinculada a um locatário comuns do Azure AD que contém as contas de usuário sincronizadas a partir do contoso.com floresta do Windows Server AD.
  
- **Organização** A Contoso Corporation é identificada pela sua contoso.com de nome de domínio público.
    
  - **Assinaturas e licenças** A Contoso Corporation está usando o seguinte:
    
  - O produto do Office 365 Enterprise E3 com 5.000 licenças
    
  - O produto do Office 365 Enterprise E5 com 200 licenças
    
  - O produto EMS com 5.000 licenças
    
  - O produto Dynamics 365 com 100 licenças
    
  - Diversas assinaturas Azure com base em regiões
    
  - **Contas de usuário** Um locatário comuns do Windows Azure AD contém a lista de contas de usuário e os grupos usados por todas as assinaturas da Contoso, com exceção de desenvolvimento e teste assinaturas do Azure.
    
Para os locatários da Contoso:
  
- Para ofertas de nuvem SaaS, o inquilino é o local regional que hospeda os servidores fornecendo serviços de nuvem. A Contoso optou pela região europeu para hospedar seus locatários do Office 365, EMS e Dynamics 365. 
    
- Serviços do Azure PaaS e aplicativos e cargas de trabalho de TI IaaS podem ter locação em qualquer datacenter do Windows Azure no mundo inteiro. Um locatário do Azure AD é uma instância específica do Azure AD contendo as contas e grupos.
    
- O inquilino comuns do Azure AD que contém as contas sincronizadas para a floresta Contoso Windows Server AD fornece IDaaS nas ofertas de nuvem da Microsoft.
    
Para obter mais informações, consulte [assinaturas, licenças, contas e inquilinos para as ofertas de nuvem da Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).
  
## <a name="contosos-azure-subscriptions"></a>Assinaturas do Azure da Contoso

A Figura 2 mostra o design hierárquico de assinaturas do Azure da Contoso:
  
**Figura 2: Estrutura da Contoso para assinaturas do Azure**

![Estrutura da Contoso para assinaturas do Azure](images/Contoso_Poster/Subscriptions_Nested.png)
  
- A Contoso é na parte superior, com base em seu Enterprise Agreement com a Microsoft.
    
- Há um conjunto de contas correspondente às diferentes regiões da Contoso Corporation em todo o mundo, com base nos domínios da floresta do Windows Server AD da Contoso.
    
- Dentro de cada região, há um ou mais inscrições com base nas necessidades de implantação de desenvolvimento, teste e produção da região.
    
Cada assinatura Azure pode ser associada um único locatário do Azure AD que contém as contas de usuário e grupos para autenticação e autorização aos serviços do Azure. Inscrições de produção usam locatário da Contoso Azure AD comuns.
  
## <a name="see-also"></a>Veja também

[Contoso na Microsoft Cloud](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)




