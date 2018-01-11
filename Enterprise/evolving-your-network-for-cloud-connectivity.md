---
title: "Evolução da sua rede para conectividade de nuvem"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: "Resumo: Entenda como a adoção de nuvem requer uma nova abordagem sobre investimentos em infraestrutura de rede."
ms.openlocfilehash: 18b4e5e10094a43f0d2b10cd0f01684f2352a0a8
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>Evolução da sua rede para conectividade de nuvem

 **Resumo:** Compreenda como a adoção de nuvem requer uma nova abordagem sobre investimentos em infraestrutura de rede.
  
A migração para a nuvem altera o volume e a natureza dos fluxos de tráfego dentro e fora de uma rede corporativa. Ela também afeta as abordagens para atenuar os riscos de segurança.
  
- Antes de nuvem
    
    A maioria dos investimentos de infraestrutura de rede foram gastas em garantindo disponível, confiável e conectividade de alto desempenho em centros de dados de local. Para muitas organizações, a conectividade com a Internet não foi crítica para operações de negócios internos. Limites da rede eram principais defesas contra violações de segurança.
    
- Após a nuvem
    
    Com nova e migrada de produtividade e cargas de trabalho IT em execução na nuvem, infraestrutura investimentos deslocar do local data centers para conectividade de Internet, que agora é fundamental para operações de negócios internos. Conectividade federada desloca a estratégia de segurança para proteger identidades e dados, conforme elas fluem através da rede e pontos de conectividade com serviços de nuvem da Microsoft.
    
Investimentos em infraestrutura de rede começam com conectividade. Investimentos adicionais dependem da categoria do serviço na nuvem.
  
- **Software como serviço (SaaS)** Serviços Microsoft SaaS incluem o Office 365, Microsoft Intune e Microsoft Dynamics 365. Adoção bem-sucedida dos serviços de SaaS pelos usuários depende altamente disponível e de alto desempenho conectividade à Internet ou diretamente aos serviços de nuvem da Microsoft.
    
    Arquitetura de rede se concentra em conectividade confiável e redundante e ampla largura de banda. Investimentos em andamento incluem monitoramento e ajuste de desempenho.
    
- **Plataforma Windows Azure como um serviço (PaaS)** Além dos investimentos para serviços SaaS da Microsoft, aplicativos de PaaS multi-site ou geograficamente distribuídos podem exigir a arquitetura do Gerenciador de tráfego do Windows Azure para distribuir o tráfego do cliente. Investimentos em andamento incluem testes de desempenho e monitoramento de distribuição de tráfego e failover.
    
- **Azure infraestrutura como um serviço (IaaS)** Além dos investimentos para os serviços Microsoft SaaS e PaaS, a execução de cargas de trabalho IT no IaaS requer o design e configuração do Azure virtual redes que hospedar máquinas virtuais, conectividade segura para os aplicativos executados neles, roteamento, IP Lidando com, DNS e balanceamento de carga. Investimentos em andamento incluem o desempenho e monitoramento e solução de problemas de segurança.
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>Áreas de investimento para obter êxito na nuvem de rede

Empresas se beneficiam adotar uma abordagem metódica para otimizar a taxa de transferência de rede entre sua intranet e à Internet. Você também pode beneficiar uma conexão ExpressRoute.
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>Otimizar a conectividade de intranet à sua rede de borda

Ao longo dos anos, muitas organizações têm otimizada de conectividade de intranet e desempenho para aplicativos executados em centros de dados de local. Com a produtividade e cargas de trabalho do IT executando em nuvem da Microsoft, investimento adicional deve assegurar a conectividade de alta disponibilidade e desempenho que o tráfego entre a rede de borda e os usuários da intranet é ideal.
  
### <a name="optimize-throughput-at-your-edge-network"></a>Otimizar a taxa de transferência na sua rede de borda

Mais suas viagens de tráfego diárias de produtividade para a nuvem, como examine atentamente o conjunto de sistemas em sua rede de borda para garantir que elas sejam atuais, fornecer alta disponibilidade e tem capacidade suficiente para atender às cargas de pico.
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>Para um SLA alto Azure, Office 365 e Dynamics 365, use ExpressRoute

Embora você pode utilizar sua conexão de Internet atual da sua rede de borda, o tráfego de entrada e dos serviços de nuvem da Microsoft deve compartilhar pipe com outros tráfegos de intranet indo para a Internet. Além disso, o tráfego para os serviços de nuvem da Microsoft está sujeito a congestionamento de tráfego de Internet.
  
Para obter o melhor desempenho e um SLA alto, use ExpressRoute, uma conexão WAN dedicada entre sua rede e Windows Azure, Office 365, Dynamics 365 ou todos os três. 
  
ExpressRoute podem aproveitar o seu provedor de rede existente para uma conexão dedicado. Recursos conectados por ExpressRoute aparecem como se estiverem em sua WAN, mesmo para organizações distribuídos geograficamente.
  
Para obter mais informações, consulte [ExpressRoute para conectividade de nuvem da Microsoft](expressroute-for-microsoft-cloud-connectivity.md).
  
## <a name="scope-of-network-investments"></a>Escopo de investimentos de rede

O escopo de investimentos de rede dependem da categoria do serviço na nuvem. Investindo em nuvem da Microsoft maximiza os investimentos das equipes de rede. Por exemplo, investimentos para serviços IaaS se aplicam a todas as áreas de investimento.
  
|||||
|:-----|:-----|:-----|:-----|
|Área de investimento  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|Conectividade de Internet confiável, redundante de arquiteto com ampla largura de banda  <br/> |Aplica-se  <br/> |Aplica-se  <br/> |Aplica-se  <br/> |
|Monitorar e ajustar a taxa de transferência de Internet para o desempenho  <br/> |Aplica-se  <br/> |Aplica-se  <br/> |Aplica-se  <br/> |
|Solucionar problemas de conectividade e taxa de transferência da Internet  <br/> |Aplica-se  <br/> |Aplica-se  <br/> |Aplica-se  <br/> |
|Projetar o Gerenciador de tráfego do Windows Azure para balancear o tráfego para pontos de extremidade diferentes de carga  <br/> ||Aplica-se  <br/> |Aplica-se  <br/> |
|Arquiteto confiável, redundante e alto desempenho conectividade com redes virtuais do Azure  <br/> |||Aplica-se  <br/> |
|Design de conectividade segura para máquinas virtuais do Azure  <br/> |||Aplica-se  <br/> |
|Projetar e implementar o roteamento entre locais de local e redes virtuais  <br/> |||Aplica-se  <br/> |
|Projetar e implementar o balanceamento de carga para cargas de trabalho IT internas e voltados para a Internet  <br/> |||Aplica-se  <br/> |
|Solucionar problemas de conectividade e taxa de transferência da máquina virtual  <br/> |||Aplica-se  <br/> |
   
## <a name="see-also"></a>Veja também

[Microsoft Cloud Networking para arquitetos corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[ExpressRoute para conectividade de nuvem da Microsoft](expressroute-for-microsoft-cloud-connectivity.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



