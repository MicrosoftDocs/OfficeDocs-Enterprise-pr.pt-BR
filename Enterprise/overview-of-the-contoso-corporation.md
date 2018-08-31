---
title: Visão geral da Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 1de16e29-ac2e-40b5-bf13-9301a51e16a8
description: 'Resumo: Entenda a Contoso Corporation como um negócio e a estrutura hierárquica dos seus escritórios em todo o mundo.'
ms.openlocfilehash: 66171ee872f9b526860ae1436b0e8cb51de119de
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915856"
---
# <a name="overview-of-the-contoso-corporation"></a>Visão geral da Contoso Corporation

 **Resumo:** Entenda a Contoso Corporation como um negócio e a estrutura hierárquica dos seus escritórios em todo o mundo.
  
A Contoso Corporation é uma empresa global, com sede em Paris, França. É uma conglomerado manufatura, vendas e organização de suporte com mais de 100.000 produtos. 
  
## <a name="the-contoso-corporation"></a>A Contoso Corporation

Organização mundial da Contoso tem escritórios nos seguintes locais:
  
**Figura 1: Escritórios da Contoso em todo o mundo**

![Os escritórios da Contoso Corporation em todo o mundo](media/Contoso-Poster/Contoso-WW-Org.png)

  
A Figura 1 mostra o escritório da matriz em regionais de hub e Paris e filiais em vários continentes.
  
Escritórios da Contoso em todo o mundo siga um design de três camadas.
  
- Matrizes
    
    Matriz da Contoso Corporation é um grande campus corporativo fora da Paris com dezenas de prédios para instalações administrativas, de engenharia e fabricação. Todos os centros de dados da Contoso e presença da Internet são armazenados nas matrizes de Paris.
    
    Os escritórios centrais tem 15.000 funcionários.
    
- Hubs regionais
    
    Servidor de escritórios regionais hub uma região específica do mundo com a equipe de suporte e de vendas de 60%. Cada hub regional está conectado à sede Paris com um link WAN de alta largura de banda. 
    
    Cada regional hub tem uma média de 2.000 funcionários.
    
- Filiais
    
    Filiais contêm 80% de vendas e equipe de suporte e fornecem uma presença física e locais para os clientes de Contoso em cidades principais ou regiões de subsites. Cada escritório satélite está conectado a um hub regional com um link WAN de alta largura de banda.
    
    Cada escritório satélite tem uma média de 250 funcionários.
    
25% da força de trabalho da Contoso é somente para celular, com uma porcentagem superior dos funcionários móveis somente nas filiais e hubs regionais. Oferecendo melhor suporte para trabalhadores somente mobile é um objetivo comercial importante para a Contoso.
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>Elementos de implementação da Contoso do Microsoft cloud

Da Contoso arquitetos de TI identificou os seguintes elementos durante o planejamento para a adoção das ofertas de nuvem da Microsoft.
  
- Rede
    
    A rede inclui a conectividade com as ofertas de nuvem da Microsoft e a largura de banda suficiente para ter um bom desempenho sob cargas de pico. Alguns conectividade será local conexões de Internet e algumas serão entre a infraestrutura de rede privada da Contoso.
    
    Para obter mais informações, consulte o cartaz de [Rede da nuvem com a Microsoft para arquitetos da empresa](microsoft-cloud-networking-for-enterprise-architects.md) .
   
- Identidade
    
    A Contoso utiliza uma floresta do Windows Server AD para seu provedor de identidade interno e também agrupa com provedores de terceiros para clientes e parceiros. Contoso deve aproveitar o conjunto interno de contas para as ofertas de nuvem da Microsoft. Provedores de identidade de terceiros também deve aproveitar o acesso aos aplicativos baseados em nuvem para clientes e parceiros.
    
    Para obter mais informações, consulte o cartaz de [Identidade de nuvem da Microsoft para arquitetos da empresa](microsoft-cloud-it-architecture-resources.md#identity) .
    
- Segurança
    
    Segurança de dados e de identidades baseadas em nuvem deve incluir a proteção de dados, gerenciamento de privilégio administrativo, reconhecimento de ameaça e a implementação de políticas de governança e segurança de dados.
    
    Para obter mais informações, consulte o cartaz de [Segurança de nuvem da Microsoft para arquitetos da empresa](http://aka.ms/cloudarchsecurity) .
    
- Gerenciamento
    
    Gerenciamento de aplicativos baseados em nuvem e cargas de trabalho SaaS precisará a capacidade de manter configurações, dados, contas, políticas e permissões e monitorar o desempenho e a integridade em andamento. Ferramentas de gerenciamento de servidor existente serão ser usadas para gerenciar as máquinas virtuais no Windows Azure IaaS.
    
## <a name="see-also"></a>Confira também

[Contoso no Microsoft Cloud](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

[Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)
 


