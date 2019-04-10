---
title: Cenários de nuvem híbrida para a PaaS do Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Resumo: entenda a arquitetura híbrida e os cenários para ofertas de nuvem com base na PaaS (plataforma como serviço) da Microsoft no Azure.'
ms.openlocfilehash: f4d90d51a7627063fae6fd168681bdf96cb4d6bc
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741367"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Cenários de nuvem híbrida para a PaaS do Azure

 **Resumo:** Compreenda a arquitetura híbrida e os cenários para as ofertas de nuvem baseadas na PaaS (plataforma como serviço) da Microsoft no Azure.
  
Combine dados locais ou recursos de computação com aplicativos novos ou convertidos em execução na PaaS do Azure, o que pode aproveitar o desempenho, a confiabilidade e a escala da nuvem e oferecer um melhor suporte aos usuários móveis. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Arquitetura de cenário híbrido do Azure PaaS

A Figura 1 mostra a arquitetura dos cenários híbridos baseados em PaaS da Microsoft no Azure.
  
**Figura 1: cenários híbridos baseados no Microsoft PaaS no Azure**

![Cenários híbridos baseados no Microsoft PaaS no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
Para cada camada da arquitetura:
  
- Aplicativos e cenários
    
    Um aplicativo de PaaS híbrido é executado no Azure e usa recursos de computação ou armazenamento no local.
    
- Identidade
    
    O consiste em uma sincronização de diretório ou Federação com um provedor de identidade de terceiros.
    
- Rede
    
    O consiste no seu pipe existente na Internet ou em uma conexão ExpressRoute com emparelhamento público para a PaaS do Azure. Você deve incluir uma maneira de o aplicativo de PaaS do Azure acessar o recurso de armazenamento ou de computação local.
    
- Local
    
    O consiste em uma infraestrutura de identidade e segurança e em servidores de banco de dados ou aplicativos LOB (linha de negócios) existentes, que um aplicativo de PaaS do Azure pode acessar com segurança.
    
## <a name="azure-paas-hybrid-application"></a>Aplicativo híbrido do Azure PaaS

A Figura 2 mostra a configuração de um aplicativo híbrido executado no Azure.
  
**Figura 2: aplicativo híbrido baseado em PaaS do Azure**

![Aplicativo híbrido baseado em PaaS do Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
Na Figura 2, uma rede local hospeda o armazenamento ou aplicativos nos servidores e um DMZ contendo um servidor proxy. Ele está conectado aos serviços de PaaS do Azure pela Internet ou com uma conexão ExpressRoute.
  
Uma organização pode tornar seus recursos de computação ou de armazenamento disponíveis para o aplicativo híbrido do Azure PaaS por:
  
- Hospedar o recurso em servidores no DMZ.
    
- Hospedagem de um servidor proxy reverso no DMZ, que permite solicitações autenticadas, de entrada, baseadas em HTTPS para o recurso localizado no local.
    
O aplicativo do Azure pode usar credenciais de:
  
- O Azure AD, que pode ser sincronizado com seu provedor de identidade local, como os serviços de domínio do Active Directory (AD DS).
    
- Um provedor de identidade de terceiros.
    
### <a name="example-azure-paas-hybrid-application"></a>Exemplo de aplicativo híbrido do Azure PaaS

A Figura 3 mostra um exemplo de aplicativo híbrido executado no Azure.
  
**Figura 3: um aplicativo híbrido baseado em PaaS de exemplo do Azure**

![Um exemplo de aplicativo híbrido baseado em PaaS do Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
Na Figura 3, uma rede local hospeda um aplicativo LOB. O Azure PaaS hospeda um aplicativo móvel personalizado. Um smartphone na Internet acessa o aplicativo móvel personalizado no Azure, que envia solicitações de dados para o aplicativo LOB local.
  
Este exemplo de aplicativo híbrido do Azure PaaS é um aplicativo móvel personalizado que fornece informações de contato atualizadas sobre funcionários. O cenário híbrido de ponta a ponta consiste em:
  
- Um aplicativo do smartphone que requer credenciais locais e validadas para executar.
    
- Um aplicativo móvel personalizado em execução na PaaS do Azure, que solicita informações sobre funcionários específicos com base nas consultas do aplicativo smartphone de um usuário.
    
- Um servidor de proxy reverso na DMZ que valida o aplicativo móvel personalizado e encaminha a solicitação.
    
- Um farm de servidor de aplicativos LOB que faz a solicitação de contato, sujeita às permissões da conta do usuário.
    
Como o provedor de identidade local foi sincronizado com o Azure AD, o aplicativo móvel personalizado e o aplicativo LOB podem validar o nome da conta do usuário solicitante.
  
## <a name="see-also"></a>Confira também


[Nuvem híbrida da Microsoft para arquitetos corporativos](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

