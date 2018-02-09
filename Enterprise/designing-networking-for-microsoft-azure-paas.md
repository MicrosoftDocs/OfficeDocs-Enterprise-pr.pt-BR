---
title: Projetando a rede para o Microsoft Azure PaaS
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
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Resumo: Entenda como otimizar sua rede para o acesso ao Microsoft Azure PaaS.'
ms.openlocfilehash: 151701223c6cf21890fcd961c5dc3acda8de4915
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>Projetando a rede para o Microsoft Azure PaaS

 **Resumo:** Compreenda como otimizar sua rede para o acesso ao Microsoft Azure PaaS.
  
Otimizar a rede para os aplicativos PaaS do Azure exige uma largura de banda de Internet adequada e pode ainda exigir a distribuição de tráfego de rede em diversos sites ou aplicativos.
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>Etapas de planejamento para hospedar aplicativos PaaS de organização no Windows Azure

1. Percorra a seção de **etapas para preparar sua rede para serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Otimize sua largura de banda da Internet usando as etapas 2 a 4 da seção **etapas para preparar a sua rede de serviços Microsoft SaaS** em [projetar a rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md).
    
3. Determine se você precisa de uma conexão ExpressRoute no Azure.
    
4. Para cargas de trabalho baseados na web, determine se é necessário que o Gateway de aplicativo do Windows Azure.
    
5. Para distribuição de tráfego para os pontos de extremidade diferentes em datacenters diferentes, determine se é necessário que o Gerenciador de tráfego do Azure.
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>Largura de banda de Internet para aplicativos de PaaS da organização

Aplicativos de organização hospedados no Azure PaaS exigem largura de banda da Internet para os usuários da intranet. Há duas opções:
  
- **Opção 1:** Use seu pipe existente, otimizado para o tráfego da Internet com a capacidade de lidar com cargas de pico. Consulte[Projetando a rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md) para borda de Internet, uso do cliente e considerações de operações de IT.
    
- **Opção 2:** Para alta largura de banda ou baixa latência necessidades, use uma conexão ExpressRoute no Azure.
    
**Figura 1: Opções de Conexão para conectar-se os serviços do Azure PaaS**

![Figura 1: Opções de conexão para os serviços de PaaS do Azure](images/Network_Poster/PaaS1.png)
  
A Figura 1 mostra uma rede local conectando-se aos serviços do Azure PaaS através de uma conexão de Internet ou ExpressRoute.
  
## <a name="azure-application-gateway"></a>Gateway de aplicativo do Azure

Roteamento de nível de aplicativo e balanceamento de serviços que permitem que você construir um escalonável e altamente disponível web front-end no Windows Azure para aplicativos web, serviços em nuvem e máquinas virtuais. 
  
**Figura 2: Gateway de aplicativo do Azure**

![Figura 2: Serviço de gateway do aplicativo do Azure](images/Network_Poster/PaaS2.png)
  
A Figura 2 mostra o Gateway de aplicativo do Windows Azure e como o usuário solicita da Internet pode ser roteada para os aplicativos web do Azure, serviços de nuvem ou máquinas virtuais.
  
Application Gateway suporta atualmente o fornecimento de 7 de aplicativos de camada para o seguinte:
  
- Balanceamento de carga HTTP
    
- Afinidade baseada em cookie de sessão
    
- Descarregamento SSL
    
Para obter mais informações, consulte [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).
  
## <a name="azure-traffic-manager"></a>Gerenciador de tráfego do Azure

Distribuição de tráfego para os pontos de extremidade diferentes, que podem incluir serviços em nuvem ou aplicativos web Azure localizados em datacenters diferentes ou pontos de extremidade externos.
  
Gerenciador de tráfego usa os seguintes métodos de roteamento:
  
- **Failover:** Os pontos de extremidade estão em data centers Azure o mesmo ou diferente e você deseja usar um ponto de extremidade principal para todo o tráfego, mas fornecer backups em caso do principal ou os pontos de extremidade de backup não estão disponíveis.
    
- **Rodízio:** Você deseja distribuir a carga em um conjunto de pontos de extremidade no mesmo datacenter ou em datacenters diferentes.
    
- **Desempenho:** Você tem pontos de extremidade em diferentes locais geográficos e quiser que o solicitante aos clientes utilizarem o ponto de extremidade "mais próximo" em termos a mais baixa latência.
    
Aqui está um exemplo para três aplicativos da web distribuídos geograficamente.
  
**Figura 3: Gerenciador de tráfego do Azure**

![Figura 3: Gerenciador de tráfego do Azure](images/Network_Poster/PaaS3.png)
  
A Figura 3 mostra o processo básico que o Gerenciador de tráfego usa para rotear solicitações para três aplicativos web Azure diferente nos Estados Unidos, Europa e Ásia. No exemplo:
  
1. Uma consulta DNS do usuário para um site da web que URL obtém direcionados para Azure Gerenciador de tráfego, que retorna o nome de um aplicativo web regionais, com base no método de roteamento de desempenho.
    
2. O usuário inicia o tráfego com o aplicativo web regionais na Europa.
    
Para obter mais informações, consulte [Gerenciador de tráfego](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="next-step"></a>Próxima etapa

[Projetando a rede para o Microsoft Azure IaaS](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a>Confira também

[Microsoft Cloud Networking para arquitetos corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



