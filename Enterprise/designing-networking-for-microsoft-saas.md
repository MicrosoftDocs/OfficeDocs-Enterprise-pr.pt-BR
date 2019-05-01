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
description: 'Resumo: entenda como otimizar sua rede para acessar os serviços SaaS da Microsoft, incluindo o Office 365, o Microsoft Intune e o Dynamics 365.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487288"
---
# <a name="designing-networking-for-microsoft-saas"></a>Criação de rede para o Microsoft SaaS

 **Resumo:** Entenda como otimizar sua rede para acessar os serviços SaaS da Microsoft, incluindo o Office 365, o Microsoft Intune e o Dynamics 365.
  
A otimização da sua rede para os serviços de SaaS da Microsoft exige a configuração de dispositivos de borda e interno para direcionar as diferentes categorias de tráfego para os serviços de SaaS da Microsoft.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Etapas para preparar sua rede para os serviços Microsoft SaaS

Siga estas etapas para otimizar a rede para os serviços Microsoft SaaS:
  
1. Siga as **etapas para preparar sua rede para o serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Adicione uma conexão à Internet para cada um dos seus escritórios.
    
3. Certifique-se de que os ISPs de todas as conexões com a Internet usem um servidor DNS com um endereço IP local.
    
4. Examine seus hairpins de rede, destinos intermediários, como serviços de segurança baseados em nuvem, e elimine-os se possível.
    
5. Configure seus dispositivos de borda para ignorar o processamento para as categorias otimizar e permitir do tráfego Microsoft SaaS.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Otimizando o tráfego para os serviços SaaS da Microsoft    

Há três categorias de tráfego de SaaS da Microsoft:

- Otimização

  Necessário para conectividade a cada serviço Microsoft SaaS e representa mais de 75% de largura de banda, conexões e volume de dados do SaaS da Microsoft.

- Permitir

  Necessário para conectividade com serviços e recursos Microsoft SaaS específicos, mas não são tão sensíveis ao desempenho da rede e à latência que na categoria otimizar.

- Padrão

  Representa serviços e dependências Microsoft SaaS que não exigem nenhuma otimização. Você pode tratar o tráfego de categoria padrão, como o tráfego de Internet normal.


**Figura 1: configuração recomendada para o tráfego de SaaS da Microsoft para todos os escritórios**

![Figura 1: configuração recomendada para o tráfego de SaaS da Microsoft para todos os escritórios](media/Network-Poster/SaaS1.png)

A Figura 1 mostra a configuração recomendada de todos os escritórios, incluindo filiais e escritórios regionais ou centrais, nos quais:

- A categoria **padrão** e o tráfego geral da Internet são roteados para escritórios que têm servidores proxy e outros dispositivos de borda para oferecer proteção contra riscos de segurança baseados na Internet.
- **Otimizar** e **permitir** tráfego de categoria é encaminhado diretamente para a borda do front-end de rede da Microsoft mais próximo do escritório que contém o usuário de conexão, ignorando servidores proxy e outros dispositivos de borda.

Os dispositivos de rede de longa distância (SD-WAN) definidos por software em filiais separam tráfego para: 

- A categoria **padrão** e o tráfego geral da Internet vão para um escritório central ou regional no backbone Wan. 
- **Otimizar** e **permitir que** o tráfego de categoria vá para o ISP que fornece a conexão local com a Internet.
  
Para obter mais informações, consulte:
  
- [Princípios de conectividade de rede](https://aka.ms/expressrouteoffice365)

- [Planejamento de migração e rede para Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Próxima etapa

[Criação de rede para o Microsoft Azure PaaS](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Confira também

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

