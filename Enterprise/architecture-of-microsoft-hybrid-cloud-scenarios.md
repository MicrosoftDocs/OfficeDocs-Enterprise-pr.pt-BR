---
title: "Arquitetura dos cenários de nuvem Microsoft híbridos"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Resumo: Entenda a arquitetura das ofertas de nuvem da Microsoft híbrida."
ms.openlocfilehash: 0909964421cecec455ed3c45c965a330501d361c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Arquitetura dos cenários de nuvem Microsoft híbridos

 **Resumo:** Entenda a arquitetura de ofertas de nuvem da Microsoft híbrida.
  
Use uma abordagem de arquitetura para planejar e implementar os cenários de nuvem híbrida com os serviços de nuvem da Microsoft e plataformas.
  
**Figura 1: Microsoft híbrida pilha da nuvem**

![A pilha de nuvem híbrida da Microsoft](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
A Figura 1 mostra a pilha de nuvem híbrida Microsoft e sua camada, que incluem o local, rede, identidade, aplicativos e cenários e categoria do serviço na nuvem (SaaS Microsoft Azure PaaS e Azure PaaS).
  
A camada de aplicativos e cenários contém os cenários de nuvem híbrida específica que são detalhados nos artigos adicionais desse modelo. A identidade, rede e locais camadas podem ser comuns para as categorias de serviço na nuvem (SaaS, PaaS ou PaaS).
  
- Local
    
    Infraestrutura do local para cenários híbridos pode incluir servidores para SharePoint, Exchange, Skype para aplicativos linha de negócios e de negócios. Ele também pode incluir os repositórios de dados (bancos de dados, listas, arquivos). Sem conexões ExpressRoute, acesso para os repositórios de dados de locais deve ser permitido por meio de um proxy reverso ou tornando o servidor ou os dados acessíveis em sua DMZ ou extranet.
    
- Rede
    
    Há duas opções para conectividade com plataformas de nuvem da Microsoft e serviços: seu pipe existente da Internet e ExpressRoute. Use uma conexão ExpressRoute se desempenho previsível é importante. Você pode usar uma conexão de ExpressRoute para conectar-se diretamente para os serviços Microsoft SaaS (Office 365 e Dynamics 365), serviços do Azure PaaS e serviços do Azure PaaS.
    
- Identidade
    
    Para infraestrutura de identidade de nuvem, há duas maneiras de ir, dependendo da plataforma de nuvem da Microsoft. Para SaaS e PaaS do Azure, integrar sua infraestrutura de identidade no local com o Azure AD ou estabelecer uma federação com provedores de identidade seu local identidade infraestrutura ou de terceiros. Para VMs em execução no Windows Azure, você pode estender sua infraestrutura de identidade de local, como o Windows Server AD, para as redes virtuais (VNets) onde residem os suas VMs.
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>Cenários de nuvem híbrida para o processo de adoção de nuvem de três fases

Muitas empresas, incluindo Microsoft, usam uma abordagem de três fases para adotar a nuvem. Cenários de nuvem híbrida podem reproduzir uma função em cada fase.
  
1. Mover cargas de trabalho de produtividade para SaaS
    
    Para produtividade cargas de trabalho que atualmente estão ou devem permanecer no local, cenários híbridos permitir que eles sejam integrados com os representantes de nuvem.
    
2. Desenvolva aplicativos novos e modernos no Azure PaaS
    
    Aplicativos do Azure PaaS híbrida com segurança podem aproveitar os recursos de servidor ou armazenamento local.
    
3. Mover aplicativos existentes para o Windows Azure IaaS
    
    Para cenários de shift e levantar e compilação na nuvem, aplicativos de servidor em execução no Azure VMs fornecem fácil provisionamento e dimensionamento.
    
## <a name="see-also"></a>See Also

[Nuvem híbrida da Microsoft para arquitetos da empresa](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



