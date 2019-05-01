---
title: Visão geral de nuvem híbrida
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
description: 'Resumo: entender a definição e os elementos da nuvem híbrida da Microsoft.'
ms.openlocfilehash: c048cfeb840bbb03b1886c7053603cfdc84f37ab
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491148"
---
# <a name="hybrid-cloud-overview"></a>Visão geral de nuvem híbrida

 **Resumo:** Entender a definição e os elementos da nuvem híbrida da Microsoft.
  
A nuvem híbrida usa recursos de computação ou armazenamento em sua rede local e na nuvem. Você pode usar a nuvem híbrida como um caminho para migrar sua empresa e suas necessidades de ti para a nuvem ou integrar plataformas de nuvem e serviços com sua infraestrutura local existente como parte da sua estratégia geral de ti.
  
## <a name="microsoft-hybrid-cloud"></a>Nuvem híbrida da Microsoft

A nuvem híbrida da Microsoft é um conjunto de cenários comerciais que combinam uma plataforma de nuvem da Microsoft com um componente local, como: 
  
- Obter resultados de pesquisa do conteúdo em um farm local do SharePoint e no SharePoint Online no Office 365.
    
- Um aplicativo móvel em execução no Azure que consulta um repositório de dados local.
    
- Uma carga de trabalho de ti de intranet em execução nas máquinas virtuais do Azure.
    
**Figura 1: componentes da nuvem híbrida da Microsoft**

![Componentes da nuvem híbrida da Microsoft](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
A Figura 1 mostra os componentes da nuvem híbrida da Microsoft, de uma rede local para o conjunto de serviços do Office 365, da plataforma do Azure como um serviço (PaaS) e do Azure infraestrutura como serviço (IaaS) disponíveis através da Internet ou de uma conexão ExpressRoute.
  
Como a Microsoft tem a solução de nuvem mais completa do mercado, incluindo software como um serviço (SaaS), PaaS e IaaS, você pode:
  
- Aproveite seus investimentos locais existentes ao migrar cargas de trabalho e aplicativos para a nuvem.
    
- Incorpore cenários de nuvem híbridas em seus planos de ti de longo prazo, por exemplo, quando regulamentos ou políticas não permitem a movimentação de dados ou cargas de trabalho específicos para a nuvem.
    
- Crie outros cenários híbridos que incluem vários serviços e plataformas do Microsoft Cloud.
    
Cenários para nuvem híbrida com os serviços de nuvem da Microsoft variam com a plataforma.
  
- SaaS
    
    Os serviços Microsoft SaaS incluem o Office 365, o Microsoft Intune e o Microsoft Dynamics 365. Cenários de nuvem híbrida com o Microsoft SaaS combina esses serviços com aplicativos ou serviços locais. Por exemplo, o Exchange Online em execução no Office 365 pode ser integrado ao Skype for Business 2019 implantado no local.
    
- PaaS do Azure
    
    Os serviços de PaaS do Microsoft Azure permitem que você crie aplicativos baseados em nuvem. Cenários de nuvem híbrida com os serviços de PaaS do Azure combinam um aplicativo de PaaS do Azure com recursos ou aplicativos locais. Por exemplo, um aplicativo de PaaS do Azure pode consultar com segurança um repositório de dados local para obter informações necessárias para exibir os usuários do aplicativo móvel.
    
- Azure IaaS
    
    Os serviços do Azure IaaS permitem que você crie e execute cargas de trabalho de ti baseadas em servidor na nuvem, em vez de no datacenter local. Cenários de nuvem híbrida com serviços do Azure IaaS geralmente consistem em uma carga de trabalho de ti que é executada em máquinas virtuais conectadas de forma transparente à sua rede local. Os usuários locais não perceberão a diferença.
    
## <a name="elements-of-hybrid-cloud"></a>Elementos da nuvem híbrida

Você deve considerar os seguintes elementos ao planejar e implementar cenários de nuvem híbrida com plataformas e serviços de nuvem da Microsoft.
  
- Rede
    
    O sistema de rede para cenários de nuvem híbrida inclui a conectividade para plataformas e serviços da nuvem da Microsoft e largura de banda suficiente para ser um desempenho em picos de carga. Para obter mais informações, consulte [rede do Microsoft Cloud para arquitetos corporativos](microsoft-cloud-networking-for-enterprise-architects.md).
    
- Identidade
    
    A identidade para o SaaS e cenários híbridos de PaaS do Azure podem incluir o Azure AD como um provedor de identidade comum, que pode ser sincronizado com os serviços de domínio do Active Directory (AD DS) local ou federado com o AD DS ou outros provedores de identidade. Você também pode estender sua infraestrutura de identidade local para o Azure IaaS. Para obter mais informações, consulte [identidade de nuvem da Microsoft para arquitetos corporativos](microsoft-cloud-it-architecture-resources.md#identity).
    
- Segurança
    
    A segurança para cenários de nuvem híbrida inclui proteção e gerenciamento de identidades, proteção de dados, gerenciamento de privilégios administrativos, reconhecimento de ameaças e implementação de políticas de governança e segurança. Para obter mais informações, consulte [segurança de nuvem da Microsoft para arquitetos corporativos](microsoft-cloud-it-architecture-resources.md#security).
    
- Gerenciamento
    
    O gerenciamento de cenários de nuvem híbrida inclui a capacidade de manter configurações, dados, contas, políticas e permissões e para monitorar a integridade contínua dos elementos do cenário e seu desempenho. Você também pode usar o mesmo conjunto de ferramentas, como o Systems Management Server, para gerenciar máquinas virtuais no Azure IaaS.
    
## <a name="see-also"></a>Confira também

[Nuvem híbrida da Microsoft para Arquitetos Corporativos](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

