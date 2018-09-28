---
title: Visão geral de conectividade de rede do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Discute por que a otimização de rede é importante para os serviços SaaS, o objetivo de rede do Office 365, e como SaaS requer uma rede diferente de outras cargas de trabalho.
ms.openlocfilehash: ebd7410ec5fe421561543f1223e455377e99e625
ms.sourcegitcommit: 09985cb7894725289ef1fc8ddd90b569c285c09e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "25002350"
---
# <a name="office-365-network-connectivity-overview"></a>Visão geral de conectividade de rede do Office 365

O Office 365 é distribuída nuvem Software-como um serviço (SaaS) que fornece cenários de produtividade e colaboração por meio de uma gama de microserviços e aplicativos. Componentes de cliente do Office 365, como o Outlook, Word e PowerPoint execute nos computadores dos usuários e se conectar a outros componentes do Office 365 que são executados em centros de dados da Microsoft. O fator mais significativo que determina a qualidade da experiência do usuário final do Office 365 é baixa latência entre clientes do Office 365 e portas de frente de serviço do Office 365 e confiabilidade de rede.

Neste artigo, você aprenderá sobre as metas da rede do Office 365 e por que o sistema de rede do Office 365 exige uma abordagem diferente para otimização de tráfego genérico da Internet.

## <a name="office-365-networking-goals"></a>Metas de rede do Office 365

O principal objetivo de rede do Office 365 é otimizar a experiência do usuário final, permitindo o acesso menos restritivo entre clientes e os pontos de extremidade mais próximos do Office 365. A qualidade da experiência do usuário final está diretamente relacionada ao desempenho e capacidade de resposta do aplicativo que o usuário está usando. Por exemplo, Microsoft Teams depende de baixa latência para que as chamadas de telefone do usuário, conferências e colaboração de tela compartilhado é livre de problemas e Outlook depende da conectividade de rede excelente para os recursos de pesquisa instantânea que otimizam o lado do servidor de indexação e AI recursos.

O principal objetivo do design de rede deve ser minimizar a latência, reduzindo o tempo de ida e volta (RTT) de máquinas clientes à rede Global Microsoft, backbone de rede pública da Microsoft que interconexão todos os centros de dados da Microsoft com baixa latência , pontos de entrada de aplicativo de nuvem de alta disponibilidade espalham pelo mundo. Você pode aprender mais sobre a rede Global da Microsoft em [como a Microsoft amplia sua rede global rápida e confiável](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Otimizando o desempenho de rede do Office 365 não precisa ser complicado. Você pode obter o melhor desempenho possível seguindo alguns princípios-chave:

- Identificar o tráfego de rede do Office 365
- Permitir saída local de filial do tráfego de rede do Office 365 para a internet de cada local em que os usuários se conectam ao Office 365
- Permitir o tráfego ignorar proxies e dispositivos de inspeção de pacotes do Office 365

Para obter mais informações sobre os princípios de conectividade de rede do Office 365, consulte [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Arquiteturas de rede tradicionais e SaaS

Princípios de arquitetura de rede tradicional de cargas de trabalho do cliente/servidor destinam-se ao redor do pressuposto de que o tráfego entre clientes e pontos de extremidade não se estende fora do perímetro da rede corporativa. Além disso, em redes corporativas muitos, todas as conexões de Internet de saída atravessam a rede corporativa em a saída de um local central.

Em arquiteturas de rede tradicional, o maior latência para tráfego da Internet genérico é uma compensação necessária para manter a segurança de rede de perímetro e otimização do desempenho para o tráfego de Internet normalmente envolve atualizar ou expansão o equipamento nos pontos de saída de rede. No entanto, essa abordagem não aborda os requisitos de desempenho de rede ideal de serviços SaaS como o Office 365.

## <a name="identifying-office-365-network-traffic"></a>Identificando o tráfego de rede do Office 365

Estamos tornando mais fácil identificar o tráfego de rede do Office 365 e tornando-o mais simples de gerenciar a identificação de rede.

- Novas categorias de pontos de extremidade de rede para diferenciar o tráfego de rede altamente críticos de tráfego de rede que não é afetado por latências de Internet. Há apenas um número limitado de URLs e dos endereços de IP de suporte na categoria "Otimizar" mais importante.
- Identificação de rede de serviços da Web para o uso de script ou de gerenciamento de alterações e configuração de dispositivo direto do Office 365. As alterações são disponíveis do serviço da web, no formato RSS ou no email usando um modelo do Microsoft Flow.
- [Programa de parceria de rede do office 365](http://aka.ms/Office365NPP) com parceiros da Microsoft que fornecem dispositivos ou serviços que seguem princípios de conectividade de rede do Office 365 e tem a configuração simples.

## <a name="securing-office-365-connections"></a>Protegendo conexões do Office 365

O objetivo de segurança de rede tradicional é proteger o perímetro de rede corporativa contra invasão e explorações mal-intencionado. A maioria das redes de enterprise impor a segurança de rede para o tráfego de Internet usando tecnologias, como servidores proxy, firewalls, quebra SSL e inspecione, profunda inspeção de pacotes e os sistemas de prevenção de perda de dados. Essas tecnologias fornecem mitigação de riscos importantes para solicitações de Internet genéricas, mas podem reduzir drasticamente o desempenho, a escalabilidade e a qualidade da experiência do usuário final quando aplicada aos pontos de extremidade do Office 365.

O Office 365 ajuda a atender às necessidades da sua organização para fins de conformidade conteúda de uso de dados e segurança com recursos internos de segurança e governança projetado especificamente para cargas de trabalho e recursos do Office 365. Para obter mais informações sobre conformidade e segurança do Office 365, consulte o [mapa de segurança do Office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). Para obter mais informações sobre as recomendações e a posição de suporte da Microsoft em soluções de rede avançado que executar o processamento de nível avançadas no tráfego do Office 365, consulte [usando dispositivos de rede de terceiros ou soluções de tráfego do Office 365](https://support.microsoft.com/en-us/help/2690045).

## <a name="why-is-office-365-networking-different"></a>Por que Office 365 é uma rede diferente?

O Office 365 foi projetado para um desempenho ideal usando conexões de rede criptografada, reduzindo a necessidade de imposição de segurança de perímetro e segurança do ponto de extremidade. Centros de dados do Office 365 estão espalhados pelo mundo e o serviço destina-se usar vários métodos para conectar clientes aos pontos de extremidade de serviço disponível recomendados. Desde que o processamento e dados do usuário é distribuído entre muitos centros de dados do Microsoft, não há nenhum ponto de extremidade de rede único ao qual cliente máquinas podem se conectar. Na verdade, dados e serviços no seu locatário do Office 365 dinamicamente otimizados pela rede Microsoft Global para se adaptar os locais geográficos do qual são acessados pelos usuários finais.

Certos problemas comuns de desempenho são criados quando o tráfego do Office 365 está sujeito a inspeção de pacotes e de saída centralizada:

- Latência alta pode causar extremamente baixo desempenho dos fluxos de áudio e vídeos e resposta lento de recuperação de dados, pesquisas, colaboração em tempo real, informações de disponibilidade de calendário, conteúdo do produto e outros serviços
- Egressing conexões de um local central de derrotas as capacidades de roteamento dinâmicas da rede global do Office 365, adicionando a latência e o tempo de ida e volta
- Descriptografia SSL protegido o tráfego de rede do Office 365 e criptografando-o novamente pode causar erros de protocolo e possui os riscos de segurança

Diminuir o caminho de rede para os pontos de entrada do Office 365, permitindo o tráfego de cliente para saída mais próximo possível para a sua localização geográfica, conectividade pode melhorar experiência de desempenho e o usuário final no Office 365. Ele também pode ajudar a reduzir o impacto das alterações futuras para a arquitetura de rede no Office 365 desempenho e confiabilidade. O modelo de conectividade ideal é sempre fornecer a saída de rede no local do usuário, independentemente se isso está na rede corporativa ou locais remotos, como home, hotéis, cafeterias e aeroportos. Tráfego de rede corporativo com base em genérico tráfego da Internet e WAN seriam roteados separadamente e não usar o modelo de saída direto local. Este modelo de saída direto local é representado no diagrama a seguir.

![Arquitetura de rede de saída local](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

A arquitetura de saída local tem os seguintes benefícios para tráfego de rede do Office 365 sobre o modelo tradicional:
  
- Fornece o melhor desempenho do Office 365 otimizando o comprimento de rota. Conexões de usuário final dinamicamente são roteadas para o ponto de entrada do Office 365 mais próximo pela infraestrutura de _distribuído porta do serviço frontal_ da rede Global Microsoft e tráfego será encaminhado internamente aos pontos de extremidade de serviço e dados através da Microsoft fibra escura do extremamente baixa latência alta disponibilidade.
- Reduz a carga em infraestrutura de rede corporativa, permitindo a saída local para o tráfego do Office 365, ignorando proxies e dispositivos de inspeção de tráfego.
- Protege as conexões em ambas as extremidades utilizando o cliente ponto de extremidade nuvem e segurança recursos de segurança, evitando aplicativo das tecnologias de segurança de rede redundantes.

> [!NOTE]
> A infra-estrutura de _distribuído porta frontal de serviço_ é a borda de rede altamente disponível e escalonável da rede Global Microsoft com locais geograficamente distribuídos. Ela termina conexões de usuário final e eficiente roteia-los dentro da rede Global da Microsoft. Você pode aprender mais sobre a rede Global da Microsoft em [como a Microsoft amplia sua rede global rápida e confiável](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Para obter mais informações sobre a compreensão e a aplicação de princípios de conectividade de rede do Office 365, consulte [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles#office-365-connectivity-principles).

## <a name="conclusion"></a>Conclusão

Otimizando o desempenho de rede do Office 365 realmente resume-se à remoção impedimentos desnecessários. Tratando conexões do Office 365 como o tráfego confiável, você pode impedir que a latência que estão sendo apresentados pela inspeção de pacotes e a concorrência por largura de banda de proxy. Permitindo locais conexões entre computadores clientes e pontos de extremidade do Office 365 permite que o tráfego dinamicamente ser roteadas através da rede Global da Microsoft.

## <a name="related-topics"></a>Tópicos relacionados

[Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md)

[URL do serviço Web e endereço IP do Office 365](office-365-ip-web-service.md)

[Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md)

[URL do serviço Web e endereço IP do Office 365](office-365-ip-web-service.md)

[Conectividade de rede para Office 365](network-connectivity.md)

[Rede do Office 365 e ajuste de desempenho](network-planning-and-performance.md)

[Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho](performance-tuning-using-baselines-and-history.md)

[Plano de solução de problemas de desempenho do Office 365](performance-troubleshooting-plan.md)

[Como o Microsoft amplia sua rede global rápida e confiável](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
