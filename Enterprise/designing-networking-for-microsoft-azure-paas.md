---
title: Criação de rede para o Microsoft Azure PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Resumo: entenda como otimizar sua rede para acesso à PaaS do Microsoft Azure.'
ms.openlocfilehash: fafc3de1c5f755e891da6c07ae8993fb869bc5e1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067817"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>Criação de rede para o Microsoft Azure PaaS

 **Resumo:** Entenda como otimizar sua rede para acessar o Microsoft Azure PaaS.
  
Otimizar a rede para os aplicativos PaaS do Azure exige uma largura de banda de Internet adequada e pode ainda exigir a distribuição de tráfego de rede em diversos sites ou aplicativos.
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>Planejamento de etapas de Hospedagem de aplicativos de PaaS da organização no Azure

1. Siga as **etapas para preparar sua rede para o serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Otimize a largura de banda da Internet usando as etapas 2-4 das **etapas para preparar sua rede para os serviços Microsoft SaaS** no [projeto de rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md).
    
3. Determine se você precisa de uma conexão expressa para o Azure.
    
4. Para cargas de trabalho baseadas na Web, determine se você precisa do gateway de aplicativo do Azure.
    
5. Para distribuição de tráfego para diferentes pontos de extremidade em diferentes data centers, determine se você precisa do Azure Traffic Manager.
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>Largura de banda da Internet para aplicativos de PaaS da organização

Os aplicativos de organização hospedados na PaaS do Azure exigem largura de banda de Internet para usuários de intranet. Há duas opções:
  
- **Opção 1:** Use seu pipe existente, otimizado para o tráfego de Internet com a capacidade de lidar com as cargas de pico. Consulte[projetando a rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md) para borda da Internet, uso do cliente e considerações sobre operações de ti.
    
- **Opção 2:** Para necessidades de alta largura de banda ou baixa latência, use uma conexão ExpressRoute para o Azure.
    
**Figura 1: opções de conexão para conectar os serviços do Azure PaaS**

![Figura 1: opções de conexão para os serviços do Azure PaaS](media/Network-Poster/PaaS1.png)
  
A Figura 1 mostra uma rede local conectando-se aos serviços de PaaS do Azure em um pipe da Internet ou no ExpressRoute.
  
## <a name="azure-application-gateway"></a>Gateway de aplicativo do Azure

Roteamento de nível de aplicativo e serviços de balanceamento de carga que permitem criar um front-end da Web escalonável e altamente disponível no Azure para aplicativos Web, serviços em nuvem e máquinas virtuais. 
  
**Figura 2: gateway de aplicativo do Azure**

![Figura 2: serviço do Azure Application Gateway](media/Network-Poster/PaaS2.png)
  
A Figura 2 mostra o gateway de aplicativo do Azure e como as solicitações de usuário da Internet podem ser roteadas para aplicativos Web do Azure, serviços em nuvem ou máquinas virtuais.
  
O Application Gateway atualmente oferece suporte à entrega de aplicativos Layer 7 para o seguinte:
  
- Balanceamento de carga HTTP
    
- Afinidade de sessão baseada em cookies
    
- Descarregamento SSL
    
Para obter mais informações, consulte [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).
  
## <a name="azure-traffic-manager"></a>Gerenciador de tráfego do Azure

Distribuição de tráfego para diferentes pontos de extremidade, que podem incluir serviços em nuvem ou aplicativos Web do Azure localizados em diferentes centros de dados ou pontos de extremidade externos.
  
O Gerenciador de tráfego usa os seguintes métodos de roteamento:
  
- **Failover:** Os pontos de extremidade estão no mesmo ou em diferentes data centers do Azure e você deseja usar um ponto de extremidade principal para todo o tráfego, mas fornecer backups caso os pontos de extremidade principal ou de backup não estejam disponíveis.
    
- **Round Robin:** Você deseja distribuir o carregamento em um conjunto de pontos de extremidade no mesmo datacenter ou em diferentes data centers.
    
- **Desempenho:** Você tem pontos de extremidade em diferentes locais geográficos e deseja solicitar que os clientes usem o ponto de extremidade "mais próximo" em termos da menor latência.
    
Veja a seguir um exemplo de três aplicativos Web distribuídos geograficamente.
  
**Figura 3: Gerenciador de tráfego do Azure**

![Figura 3: Gerenciador de tráfego do Azure](media/Network-Poster/PaaS3.png)
  
A Figura 3 mostra o processo básico que o Gerenciador de tráfego usa para encaminhar solicitações para três aplicativos Web do Azure diferentes nos Estados Unidos, na Europa e na Ásia. No exemplo:
  
1. Uma consulta DNS de usuário para uma URL de site é direcionada para o Azure Traffic Manager, que retorna o nome de um aplicativo Web regional, com base no método de roteamento de desempenho.
    
2. O usuário inicia o tráfego com o aplicativo Web regional na Europa.
    
Para obter mais informações, consulte [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="next-step"></a>Próxima etapa

[Criação de rede para o Microsoft Azure IaaS](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a>Confira também

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI da Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

