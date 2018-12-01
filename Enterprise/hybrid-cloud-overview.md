---
title: Visão geral da nuvem híbrida
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: 'Resumo: Entenda a definição e elementos de nuvem da Microsoft híbrida.'
ms.openlocfilehash: 04c1a80009b1136ae4575ea4d454cebdb26bed3c
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123308"
---
# <a name="hybrid-cloud-overview"></a>Visão geral da nuvem híbrida

 **Resumo:** Compreenda a definição e elementos de nuvem da Microsoft híbrida.
  
Nuvem híbrida usa os recursos de computação ou armazenamento em sua rede local e na nuvem. Você pode usar a nuvem híbrida como um caminho para migrar seus negócios e suas necessidades de TI para a nuvem ou integre plataformas de nuvem e serviços com as existentes no local infraestrutura como parte de sua estratégia geral de TI.
  
## <a name="microsoft-hybrid-cloud"></a>Nuvem híbrida da Microsoft

Nuvem híbrida da Microsoft é um conjunto de cenários de negócios que combinam uma plataforma de nuvem da Microsoft com um componente de local, como: 
  
- Obtenção de resultados da pesquisa do conteúdo em um farm do SharePoint no local e no SharePoint Online no Office 365.
    
- Um aplicativo móvel em execução no Azure que consulta a um armazenamento de dados local.
    
- Uma intranet IT carga de trabalho em execução em máquinas virtuais do Azure.
    
**Figura 1: Componentes da nuvem híbrida Microsoft**

![Componentes da nuvem híbrida da Microsoft](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
A Figura 1 mostra os componentes de nuvem da Microsoft híbrido, a partir de uma rede local para o conjunto do Office 365, a plataforma do Azure como um serviço (PaaS) e a infra-estrutura do Azure como um serviço (IaaS) de serviços disponível pela Internet ou por uma conexão ExpressRoute.
  
Como a Microsoft tem a solução de nuvem mais completa no mercado — incluindo Software como um serviço (SaaS), PaaS e IaaS — você pode:
  
- Aproveite os investimentos existentes do local conforme você migra cargas de trabalho e aplicativos para a nuvem.
    
- Incorpore cenários de nuvem híbrida aos seus planos IT a longo prazo, por exemplo, quando as normas ou políticas não permitir a movimentação de dados específicos ou cargas de trabalho para a nuvem.
    
- Crie cenários híbridos adicionais que incluem vários serviços de nuvem da Microsoft e plataformas.
    
Cenários para a nuvem híbrida com os serviços de nuvem da Microsoft variam de acordo com a plataforma.
  
- SaaS
    
    Serviços Microsoft SaaS incluem o Office 365, Microsoft Intune e Microsoft Dynamics 365. Cenários de nuvem híbrida com o Microsoft SaaS combinam esses serviços com aplicativos ou serviços no local. Por exemplo, o Exchange Online em execução no Office 365 pode ser integrado ao Skype para 2019 Business que esteja implantados no local.
    
- PaaS Azure
    
    Serviços do Microsoft Azure PaaS permitem que você crie aplicativos baseados em nuvem. Cenários de nuvem híbrida com os serviços do Azure PaaS combinam um aplicativo do Windows Azure PaaS com recursos locais ou aplicativos. Por exemplo, um aplicativo do Windows Azure PaaS com segurança pôde consultar um armazenamento de dados no local para informações necessárias para exibir aos usuários de aplicativos móveis.
    
- Azure IaaS
    
    Serviços do Azure IaaS permitem que você criar e executar cargas de trabalho baseado em servidor IT na nuvem, em vez de seu centro de dados local. Cenários de nuvem híbrida com os serviços do Azure IaaS geralmente consistem em uma carga de trabalho TI que é executado em máquinas virtuais transparente conectado à sua rede local. Os usuários no local não perceberá a diferença.
    
## <a name="elements-of-hybrid-cloud"></a>Elementos de nuvem híbrida

Você deve considerar os seguintes elementos ao planejamento e implementação de cenários de nuvem híbrida com o Microsoft cloud plataformas e serviços.
  
- Rede
    
    A rede para cenários de nuvem híbrida inclui a conectividade com plataformas de nuvem da Microsoft e serviços de largura de banda suficiente para ter um bom desempenho sob cargas de pico. Para obter mais informações, consulte [Microsoft Cloud Networking para arquitetos da empresa](microsoft-cloud-networking-for-enterprise-architects.md).
    
- Identidade
    
    Identidade para os cenários híbridos SaaS e o Azure PaaS pode incluir o Azure AD como um provedor de identidade comuns, que pode ser sincronizado com o seu local Windows Server AD ou federado com o Windows Server AD ou outros provedores de identidade. Você também pode estender sua infraestrutura de identidade no local para o Windows Azure IaaS. Para obter mais informações, consulte [Identidade de nuvem da Microsoft para arquitetos da empresa](microsoft-cloud-it-architecture-resources.md#identity).
    
- Segurança
    
    Segurança para cenários de nuvem híbrida inclui o gerenciamento para sua identidades, proteção de dados, gerenciamento de privilégio administrativo, reconhecimento de ameaça e a implementação da governança e diretivas de segurança e proteção. Para obter mais informações, consulte [Segurança de nuvem da Microsoft para arquitetos da empresa](https://technet.microsoft.com/library/dn919927.aspx#security).
    
- Gerenciamento
    
    Gerenciamento para cenários de nuvem híbrida inclui a capacidade de manter configurações, dados, contas, políticas e permissões e para monitorar a integridade em andamento dos elementos do cenário e seu desempenho. Você também pode usar o mesmo conjunto de ferramentas, como o Systems Management Server, para o gerenciamento de máquinas virtuais no Windows Azure IaaS.
    
## <a name="see-also"></a>Confira também

[Nuvem híbrida da Microsoft para Arquitetos Corporativos](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

