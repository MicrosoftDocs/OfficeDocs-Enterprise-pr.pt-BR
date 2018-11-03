---
title: Plano para dispositivos de rede que se conectam aos serviços do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Resumo: Descreve as considerações para a capacidade da rede, aceleradores de WAN e balanceamento de dispositivos que são usados para conectar para o Office 365.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933118"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Plano para dispositivos de rede que se conectam aos serviços do Office 365

 **Resumo**: Descreve as considerações para a capacidade da rede, aceleradores de WAN e balanceamento de dispositivos que são usados para conectar para o Office 365.
  
Alguns dispositivos de hardware de rede podem ter limitações no número de sessões simultâneas que são suportados. Para ter mais de 2.000 usuários de empresas, recomendamos que eles monitoram seus dispositivos de rede para garantir que eles sejam capazes de lidar com o tráfego de serviço adicional do Office 365. Simple Network Management Protocol (SNMP) software de monitoramento pode ajudá-lo a fazer isso.

||
|:-----|
| Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).|

Local saídas configurações de proxy de Internet também afetam a conectividade com os serviços do Office 365 para seus aplicativos de cliente. Você também deve configurar os dispositivos de proxy de rede para permitir conexões para aplicativos e URLs de serviços de nuvem do Microsoft. Cada organização é diferente. Para obter uma ideia de como o Microsoft gerencia esse processo e a largura de banda, vamos provisionar, [Leia o estudo de caso](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
A seguir Skype para artigos de Ajuda do Business ter mais informações sobre Skype para configurações de negócios:
  
- [Skype para solução de problemas para erros de entrada no Business Online para administradores](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Você não pode se conectar ao Skype para negócios ou determinados recursos não funcionam porque um firewall local bloqueia a conexão](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Embora muitas dessas configurações sejam Skype para negócios específicos, a orientação geral sobre configuração de rede é útil para todos os serviços do Office 365.
  
## <a name="determining-network-capacity"></a>Determinando a capacidade da rede

Cada dispositivo de rede que existe em uma conexão tem seu limite de capacidade. Esses dispositivos incluem os adaptadores de rede do cliente e do servidor, roteadores, chaves e hubs que se interconectam. Capacidade de rede adequada significa que nenhum deles está saturado. O monitoramento da atividade da rede é essencial para ajudar a assegurar que os carregamentos reais em todos os dispositivos de rede estejam abaixo de sua capacidade máxima. A capacidade da rede afeta o desempenho do dispositivo proxy.
  
Na maioria das situações, a largura de banda de conexão de Internet define o limite para a quantidade de tráfego. Desempenho fraco durante as horas de pico tráfego provavelmente é causado por uso excessivo do link da Internet. Essa situação também se aplica a um cenário de filiais, onde os computadores de servidores de proxy de escritório de filial estão conectados ao dispositivo proxy nas matrizes da ramificação em um link de rede de longa distância (WAN) lento.
  
Para testar a capacidade da rede, monitore a atividade de rede na interface da rede de proxy. Se for mais de 75% da largura de banda máxima de qualquer interface de rede, considere a aumentar a largura de banda da infraestrutura de rede que for inadequada. Ou então, considere o uso de recursos avançados, como compactação HTTP.
  
## <a name="wan-accelerators"></a>Aceleradores de WAN

Se sua organização usa os dispositivos de proxy de aceleração de rede (WAN) de longa distância, você poderá encontrar problemas ao acessar os serviços do Office 365. Você pode precisar otimizar seu dispositivo de rede ou dispositivos para garantir que os usuários tenham uma experiência consistente ao acessar o Office 365. Por exemplo, serviços do Office 365 criptografar algum conteúdo do Office 365 e o cabeçalho TCP. O dispositivo não estejam aptos a lidar com esse tipo de tráfego.
  
Leia nossa declaração de suporte sobre [usando o controlador de otimização de WAN ou dispositivos de inspeção do tráfego com o Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Dispositivos de balanceamento de carga de hardware e software

Sua organização precisa usar um balanceador de carga de hardware (HLB) ou uma solução de balanceamento de carga da rede (NLB) para distribuir as solicitações para seus servidores Active Directory Federation Services (AD FS) e/ou servidores híbridos do Exchange. Os dispositivos de balanceamento de carga controlam o tráfego da rede para os servidores locais. Esses servidores são cruciais para ajudar a assegurar a disponibilidade do logon único e da implantação híbrida do Exchange.
  
Fornecemos uma solução NLB baseada em software integrada ao Windows Server. Office 365 oferece suporte a essa solução para atingir o balanceamento de carga.
  
## <a name="firewalls-and-proxies"></a>Firewalls e proxies

Para obter mais detalhes sobre como configurar firewalls e proxies para se conectar ao Office 365, leia os [pontos de extremidade de gerenciar o Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [conectividade de rede para o Office 365](network-connectivity.md)e [pontos de extremidade do Office 365 perguntas Frequentes](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) para saber mais sobre os dispositivos e seleção de circuito.
  
## <a name="see-also"></a>Confira também

[Supervisores de implantação para serviços do Office 365](deployment-advisors-for-office-365.md)
