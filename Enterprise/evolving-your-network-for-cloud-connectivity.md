---
title: Desenvolver sua rede para conectividade de nuvem
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: 'Resumo: entenda como a adoção da nuvem requer uma nova abordagem para os investimentos em infra-estrutura de rede.'
ms.openlocfilehash: c8fba120292b89894850312a84fd6067d925a07f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487237"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>Desenvolver sua rede para conectividade de nuvem

 **Resumo:** Entenda como a adoção em nuvem requer uma nova abordagem para os investimentos em infra-estrutura de rede.
  
A migração para a nuvem altera o volume e a natureza dos fluxos de tráfego dentro e fora de uma rede corporativa. Ela também afeta as abordagens para atenuar os riscos de segurança.
  
- Antes da nuvem
    
    A maioria dos investimentos em infra-estrutura de rede foi gasta para garantir conectividade disponível, confiável e com desempenho a datacenters locais. Para muitas organizações, a conectividade com a Internet não era crítica para operações comerciais internas. Os limites de rede foram defesas primárias contra violações de segurança.
    
- Após a nuvem
    
    Com a produtividade nova e migrada e as cargas de trabalho de ti em execução na nuvem, os investimentos em infra-estrutura mudarão de datacenters locais para a conectividade com a Internet, que agora é essencial para operações comerciais internas. A conectividade federada desloca a estratégia de segurança para proteger identidades e dados à medida que eles fluem pela rede e pontos de conectividade para os serviços de nuvem da Microsoft.
    
Os investimentos em infra-estrutura de rede começam com a conectividade. Investimentos adicionais dependem da categoria de serviço de nuvem.
  
- **Software como serviço (SaaS)** Os serviços Microsoft SaaS incluem o Office 365, o Microsoft Intune e o Microsoft Dynamics 365. A adoção bem-sucedida de serviços SaaS por usuários depende da conectividade de alta disponibilidade e desempenho à Internet ou diretamente aos serviços de nuvem da Microsoft.
    
    A arquitetura de rede concentra-se em uma conectividade confiável e redundante e uma ampla largura de banda. Os investimentos contínuos incluem monitoramento e ajuste de desempenho.
    
- **Plataforma do Azure como um serviço (PaaS)** Além dos investimentos em serviços Microsoft SaaS, os aplicativos de vários locais ou de PaaS geograficamente distribuídos podem exigir a arquitetura do Azure Traffic Manager para distribuir o tráfego do cliente. Os investimentos contínuos incluem monitoramento de distribuição de tráfego e de desempenho e teste de failover.
    
- **Infraestrutura do Azure como um serviço (IaaS)** Além dos investimentos para os serviços SaaS e PaaS da Microsoft, executar cargas de trabalho de ti no IaaS requer o design e a configuração de redes virtuais do Azure que hospedam máquinas virtuais, conectividade segura para aplicativos executados neles, roteamento, IP endereçamento, DNS e balanceamento de carga. Os investimentos contínuos incluem monitoramento e solução de problemas de desempenho e segurança.

A [Microsoft 365](https://www.microsoft.com/microsoft-365) é uma combinação entre o Office 365, o Enterprise Management + Security (EMS) e o Windows 10. A Microsoft 365 combina vários serviços SaaS e Azure para uma solução completa e inteligente que permite que todas as pessoas sejam criativas e trabalhem em conjunto com segurança.
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>Áreas de investimento em rede para o sucesso na nuvem

As organizações empresariais se beneficiam de tomar uma abordagem unificada para otimizar a taxa de transferência de rede em sua intranet e na Internet. Você também pode se beneficiar de uma conexão ExpressRoute.
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>Otimizar a conectividade da intranet para sua rede de borda

Com o passar dos anos, muitas organizações têm conectividade e desempenho de intranet otimizados para aplicativos executados em datacenters locais. Com a produtividade e as cargas de trabalho de ti em execução na nuvem da Microsoft, o investimento adicional deve garantir uma alta disponibilidade de conectividade e que o desempenho do tráfego entre a rede de borda e seus usuários de intranet é ideal.
  
### <a name="optimize-throughput-at-your-edge-network"></a>Otimizar a taxa de transferência em sua rede de borda

À medida que mais de seu tráfego de produtividade diária é transmitido para a nuvem, você deve examinar atentamente o conjunto de sistemas em sua rede de borda para garantir que eles sejam atuais, fornecer alta disponibilidade e ter capacidade suficiente para atender às cargas de pico.
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>Para um alto SLA para o Azure, Office 365 e Dynamics 365, use o ExpressRoute

Embora você possa usar sua conexão de Internet atual de sua rede de borda, o tráfego de e para os serviços de nuvem da Microsoft deve compartilhar o pipe com outro tráfego de intranet indo para a Internet. Além disso, seu tráfego para os serviços do Microsoft Cloud está sujeito ao congestionamento de tráfego da Internet.
  
Para um alto SLA e o melhor desempenho, use o ExpressRoute, uma conexão WAN dedicada entre sua rede e o Azure, Office 365, Dynamics 365 ou todos os três. 
  
O ExpressRoute pode aproveitar o provedor de rede existente para uma conexão dedicada. Os recursos conectados pelo ExpressRoute aparecem como se estivessem na sua WAN, mesmo para organizações geograficamente distribuídas.
  
Para obter mais informações, consulte [ExpressRoute for Microsoft Cloud Connectivity](expressroute-for-microsoft-cloud-connectivity.md).
  
## <a name="scope-of-network-investments"></a>Escopo dos investimentos em rede

O escopo dos investimentos em rede depende da categoria do serviço de nuvem. O investimento na nuvem da Microsoft maximiza os investimentos de equipes de rede. Por exemplo, os investimentos para serviços IaaS se aplicam a todas as áreas de investimento.
  
|||||
|:-----|:-----|:-----|:-----|
|Área de investimento  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|Arquiteta confiável e conectividade de Internet redundante com muita largura de banda  <br/> |Aplique  <br/> |Aplique  <br/> |Aplique  <br/> |
|Monitorar e ajustar a taxa de transferência de desempenho da Internet  <br/> |Aplique  <br/> |Aplique  <br/> |Aplique  <br/> |
|Solucionar problemas de taxa de transferência e conectividade com a Internet  <br/> |Aplique  <br/> |Aplique  <br/> |Aplique  <br/> |
|Projetar o Gerenciador de tráfego do Azure para balancear o tráfego de carga para diferentes pontos de extremidade  <br/> ||Aplique  <br/> |Aplique  <br/> |
|Arquiteta conectividade confiável, redundante e de desempenho para redes virtuais do Azure  <br/> |||Aplique  <br/> |
|Projetar conectividade segura para máquinas virtuais do Azure  <br/> |||Aplique  <br/> |
|Projetar e implementar o roteamento entre locais no local e redes virtuais  <br/> |||Aplique  <br/> |
|Arquitetar e implementar o balanceamento de carga para cargas de trabalho de ti internas e voltadas para a Internet  <br/> |||Aplique  <br/> |
|Solucionar problemas de taxa de transferência e conectividade de máquina virtual  <br/> |||Aplique  <br/> |
   
## <a name="next-step"></a>Próxima etapa

[Elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>Confira também

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)



