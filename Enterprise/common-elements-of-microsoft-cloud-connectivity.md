---
title: Elementos comuns de conectividade de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 'Resumo: Entenda os elementos comuns da infraestrutura de rede e como preparar sua rede.'
ms.openlocfilehash: 492d13a2a62425201c727c039e45db2750202da6
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915646"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Elementos comuns de conectividade de nuvem da Microsoft

 **Resumo:** Compreenda os elementos comuns da infraestrutura de rede e como preparar sua rede.
  
A integração da sua rede com a nuvem da Microsoft oferece um acesso excelente a uma ampla gama de serviços.
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>Etapas para preparar sua rede para serviços de nuvem da Microsoft
<a name="steps"> </a>

Para a sua rede local:
  
1. Analisar os computadores cliente e otimizar para drivers de software, hardware de rede, as configurações de protocolo e navegadores da Internet.
    
2. Analise sua rede local para latência de tráfego e roteamento ideal para o dispositivo de borda de Internet.
    
3. Analisar a capacidade e o desempenho do seu dispositivo de borda de Internet e otimizar para níveis mais altos de tráfego.
    
Para sua conexão de Internet:
  
1. Analise a latência entre seu dispositivo de borda da Internet (por exemplo, seu firewall externo) e os locais regionais do serviço de nuvem da Microsoft para o qual você está se conectando.
    
2. Analisar a capacidade e a utilização de sua conexão de Internet atual e adicionar capacidade, se necessário. Como alternativa, adicione uma conexão ExpressRoute.
    
## <a name="microsoft-cloud-connectivity-options"></a>Opções de conectividade do Microsoft cloud
<a name="steps"> </a>

Use seu pipe Internet existente ou uma conexão ExpressRoute ao Office 365, Windows Azure e Dynamics 365.
  
**Figura 1: Opções para conectividade de nuvem da Microsoft**

![Figura 1:  Opções para a conectividade de nuvem da Microsoft](media/Network-Poster/CommonElements.png)

  
A Figura 1 mostra como uma rede local pode ser conectada para ofertas de nuvem da Microsoft usando seus pipe de Internet existente ou ExpressRoute. O pipe Internet representa uma DMZ e pode ter os seguintes componentes:
  
- **Firewall interno:** Uma barreira entre sua rede confiável e um não confiável. Realiza a filtragem de tráfego (com base nas regras) e monitoramento.
    
- **a carga de trabalho externa:** Sites da Web ou outras cargas de trabalho disponibilizado para usuários externos na Internet.
    
- **Servidor proxy:** Serviços de solicitações de conteúdo da web em nome de usuários da intranet. Um proxy reverso permite que as solicitações de entrada não solicitadas.
    
- **Firewall externo:** Permite que o tráfego de saída e o tráfego de entrada especificado. Pode executar a conversão de endereço.
    
- **Conexão WAN para ISP:** Uma conexão para um ISP, quem peers com a Internet para conectividade e roteamento baseado em operadora.
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>Áreas de rede comuns a todos os serviços de nuvem da Microsoft
<a name="steps"> </a>

Você precisa considerar nessas áreas de rede quando a adoção de qualquer um dos serviços de nuvem da Microsoft.
  
- **Desempenho intranet:** Desempenho aos recursos baseados em Internet sofrerá se sua intranet, incluindo os computadores clientes, não está otimizado.
    
- **Dispositivos de borda:** Dispositivos na extremidade de sua rede são os pontos de saída e podem incluir conversores de endereço de rede (NATs), servidores de proxy (incluindo proxies reversos), firewalls, dispositivos de detecção de invasão ou uma combinação.
    
- **Conexão de Internet:** Sua conexão WAN para seu ISP e a Internet deve ter capacidade suficiente para lidar com cargas de pico. Você também pode usar uma conexão ExpressRoute.
    
- **Internet DNS:** A, AAAA, CNAME, MX, PTR e outros registros para localizar nuvem da Microsoft ou seus serviços hospedados na nuvem. Por exemplo, talvez seja necessário um registro CNAME para seu aplicativo hospedado no Windows Azure PaaS.
    

## <a name="next-step"></a>Próxima etapa

[ExpressRoute para conectividade de nuvem da Microsoft](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>Confira também

<a name="steps"> </a>

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)


