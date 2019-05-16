---
title: Elementos comuns de conectividade de nuvem da Microsoft
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 'Resumo: entenda os elementos comuns da infraestrutura de rede e como preparar sua rede.'
ms.openlocfilehash: f092e3fb0a2f009aa7c6bbb14229fe98b35700ea
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068107"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Elementos comuns de conectividade de nuvem da Microsoft

 **Resumo:** Compreenda os elementos comuns da infraestrutura de rede e como preparar sua rede.
  
A integração da sua rede com a nuvem da Microsoft oferece um acesso excelente a uma ampla gama de serviços.
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>Etapas para preparar sua rede para os serviços do Microsoft Cloud
<a name="steps"> </a>

Para sua rede local:
  
1. Analise seus computadores clientes e otimize para hardware de rede, drivers de software, configurações de protocolo e navegadores da Internet.
    
2. Analise sua rede local quanto à latência de tráfego e o roteamento ideal para o dispositivo de borda da Internet.
    
3. Analise a capacidade e o desempenho do seu dispositivo de borda da Internet e otimize para níveis mais altos de tráfego.
    
Para sua conexão com a Internet:
  
1. Analise a latência entre o dispositivo de borda da Internet (como o firewall externo) e os locais regionais do serviço de nuvem da Microsoft para os quais você está se conectando.
    
2. Analise a capacidade e a utilização da sua conexão atual com a Internet e adicione a capacidade, se necessário. Como alternativa, adicione uma conexão ExpressRoute.
    
## <a name="microsoft-cloud-connectivity-options"></a>Opções de conectividade do Microsoft Cloud
<a name="steps"> </a>

Use seu pipe de Internet existente ou uma conexão ExpressRoute para o Office 365, Azure e Dynamics 365.
  
**Figura 1: opções para a conectividade de nuvem da Microsoft**

![Figura 1: opções para a conectividade de nuvem da Microsoft](media/Network-Poster/CommonElements.png)

  
A Figura 1 mostra como uma rede local pode ser conectada às ofertas de nuvem da Microsoft usando seu pipe existente na Internet ou o ExpressRoute. O pipe da Internet representa uma DMZ e pode ter os seguintes componentes:
  
- **Firewall interno:** Uma barreira entre sua rede confiável e outra não confiável. Realiza filtragem de tráfego (com base em regras) e monitoramento.
    
- **Carga de trabalho externa:** Sites da Web ou outras cargas de trabalho disponibilizadas para usuários externos na Internet.
    
- **Servidor proxy:** Serviços solicitações de conteúdo da Web em nome de usuários da intranet. Um proxy reverso permite solicitações de entrada não solicitadas.
    
- **Firewall externo:** Permite o tráfego de saída e o tráfego de entrada especificado. Pode executar a conversão de endereços, a inspeção de pacotes, a interrupção e a inspeção de SSL ou a prevenção contra perda de dados.
    
- **Conexão WAN com o ISP:** Uma conexão baseada em uma operadora a um ISP, que os colegas com a Internet para conectividade e roteamento.
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>Áreas de rede comuns a todos os serviços de nuvem da Microsoft
<a name="steps"> </a>

Você precisa considerar essas áreas de rede ao adotar qualquer um dos serviços de nuvem da Microsoft.
  
- **Desempenho da intranet:** O desempenho para os recursos baseados na Internet será afetado se sua intranet, incluindo computadores cliente, não estiver otimizada.
    
- **Dispositivos de borda:** Os dispositivos na borda da sua rede são pontos de saída e podem incluir conversores de endereço de rede (NATs), servidores proxy (incluindo proxies inversos), firewalls, dispositivos de detecção de invasão ou uma combinação.
    
- **Conexão com a Internet:** Sua conexão WAN com seu ISP e com a Internet deve ter capacidade suficiente para lidar com as cargas de pico. Você também pode usar uma conexão ExpressRoute.
    
- **DNS da Internet:** A, AAAA, CNAME, MX, PTR e outros registros para localizar a nuvem da Microsoft ou seus serviços hospedados na nuvem. Por exemplo, você pode precisar de um registro CNAME para seu aplicativo hospedado na PaaS do Azure.
    

## <a name="next-step"></a>Próxima etapa

[ExpressRoute para conectividade de nuvem da Microsoft](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>Confira também

<a name="steps"> </a>

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI da Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)


