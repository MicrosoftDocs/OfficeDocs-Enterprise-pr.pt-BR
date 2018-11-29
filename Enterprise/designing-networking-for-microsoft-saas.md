---
title: Criação de rede para o Microsoft SaaS
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Resumo: Entenda como otimizar sua rede para o acesso aos serviços de SaaS da Microsoft, incluindo o Office 365 e Microsoft Intune Dynamics 365.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872262"
---
# <a name="designing-networking-for-microsoft-saas"></a>Criação de rede para o Microsoft SaaS

 **Resumo:** Compreenda como otimizar sua rede para o acesso aos serviços de SaaS da Microsoft, incluindo o Office 365 e Microsoft Intune Dynamics 365.
  
Otimizando a sua rede de serviços Microsoft SaaS requer a configuração de internos e os dispositivos de borda para rotear as diferentes categorias de tráfego para os serviços Microsoft SaaS.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Etapas para preparar sua rede para serviços SaaS da Microsoft

Siga estas etapas para otimizar a sua rede de serviços SaaS da Microsoft:
  
1. Percorra a seção de **etapas para preparar sua rede para serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Adicione uma conexão de Internet a cada um dos seus escritórios.
    
3. Certifique-se de que os provedores para todas as conexões de Internet usam um servidor DNS com um endereço IP local.
    
4. Examinar seu hairpins de rede, os destinos intermediários como serviços de segurança baseado em nuvem e eliminá-los a se possível.
    
5. Configure os dispositivos de borda para ignorar o processamento da otimizar e permitir a categorias de tráfego do Microsoft SaaS.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Otimizando o tráfego para os serviços da Microsoft SaaS    

Existem três categorias de tráfego SaaS Microsoft:

- Otimização

  Necessário para conectividade com cada serviço Microsoft SaaS e representam mais de 75% da largura de banda do Microsoft SaaS, conexões e volume de dados.

- Permitir

  Necessário para conectividade para específica Microsoft SaaS serviços e recursos mas não são sensível aos desempenho da rede e latência como aqueles na categoria Optimize.

- Padrão

  Representam os serviços Microsoft SaaS e dependências que não exigem qualquer otimização. Você pode tratar tráfego, categoria padrão como normal tráfego da Internet.


**Figura 1: Configuração recomendada para o tráfego de Microsoft SaaS para todos os escritórios**

![Figura 1: Configuração recomendada para o tráfego de Microsoft SaaS para todos os escritórios](media/Network-Poster/SaaS1.png)

A Figura 1 mostra a configuração recomendada de todos os escritórios, incluindo filiais e aquelas regionais ou central, na qual:

- Categoria **padrão** e gerais do tráfego da Internet é encaminhado para escritórios com servidores proxy e outros dispositivos de borda para oferecer proteção contra riscos de segurança baseado na Internet.
- **Otimizar** e **Permitir** tráfego de categoria é encaminhado diretamente até a borda do Microsoft rede front-end mais próxima do office que contém o usuário se conectando, ignorando servidores proxy e outros dispositivos de borda.

Dispositivos de rede (SD-WAN) de área ampla definida pelo software nas filiais separam o tráfego para que: 

- Categoria **padrão** e gerais de tráfego de Internet vai para um escritório central ou regional sobre o backbone de rede de longa distância. 
- **Otimizar** e **Permitir** o tráfego categoria vai para o ISP fornecendo a conexão de Internet local.
  
Para saber mais, confira:
  
- [Princípios de conectividade de rede](https://aka.ms/expressrouteoffice365)

- [Planejamento de migração e rede para Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Próxima etapa

[Criação de rede para o Microsoft Azure PaaS](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Confira também

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

