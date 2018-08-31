---
title: Rota Expressa do Azure para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Saiba como o Windows Azure ExpressRoute é usado com o Office 365 e como planejar o projeto de implementação de rede que será necessário se você estiver implantando o Windows Azure ExpressRoute para uso com o Office 365.
ms.openlocfilehash: 5a82576b541e27c70bca490ff8dfe887ee879c83
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539174"
---
# <a name="azure-expressroute-for-office-365"></a>Rota Expressa do Azure para Office 365

Saiba como o Windows Azure ExpressRoute é usado com o Office 365 e como planejar o projeto de implementação de rede que será necessário se você estiver implantando o Windows Azure ExpressRoute para uso com o Office 365. Serviços de infraestrutura e plataforma executados no Windows Azure frequentemente se beneficiarão abordando as considerações de desempenho e a arquitetura de rede. É recomendável ExpressRoute para Azure nesses casos. Software como um ofertas de serviço, como o Office 365 e Dynamics 365 foram criados para ser acessado forma segura e confiável através da Internet. Da mesma forma, é recomendável ExpressRoute somente para esses aplicativos em cenários específicos. Você pode ler sobre segurança e o desempenho da Internet e quando você pode considerar ExpressRoute do Windows Azure para o Office 365 no artigo [conectividade de rede para o Office 365](network-connectivity.md).

> [!NOTE]
> Iniciando 31 de julho de 2017, é possível habilitar o Microsoft Peering diretamente do console administrativo do Windows Azure ou usando o PowerShell. Após a habilitação do Microsoft Peering, você pode criar filtros de roteamento para receber anúncios de rota BGP específicos. Você precisará de autorização para criar filtros para o Office 365 e pode criar filtros de aplicativos (anteriormente conhecidos como CRM Online) do contrato de cliente do Dynamics 365 a qualquer momento. Converse com sua equipe de Account da Microsoft sobre o processo para obter a autorização para criar filtros de roteamento do Office 365. As assinaturas não autorizadas tentar criar filtros de roteamento para o Office 365 receberá uma [mensagem de erro](https://support.microsoft.com/kb/3181709)

Agora você pode adicionar uma conexão de rede direta para o Office 365 para o tráfego de rede do Office 365 selecionado. ExpressRoute Azure oferece uma conexão direta, desempenho previsível e vem com um tempo de atividade SLA de 99,95% para os componentes de rede da Microsoft. Você ainda vai exigir uma conexão de internet para serviços que não são suportados pela ExpressRoute do Windows Azure.

## <a name="planning-azure-expressroute-for-office-365"></a>Planejamento ExpressRoute Azure para o Office 365

Além de conectividade de internet, você pode escolher rotear um subconjunto de sua tráfego de rede do Office 365 através de uma conexão direta que oferece um tempo de atividade 99,95% SLA para os componentes de rede Microsoft e previsibilidade. ExpressRoute Azure fornece essa conexão de rede dedicada ao Office 365 e outros serviços de nuvem da Microsoft.

Se você tiver uma WAN MPLS existente, independentemente de ExpressRoute pode ser adicionado à sua arquitetura de rede em um dos três maneiras; por meio de um provedor de localização conjunta do exchange com suporte de nuvem, um provedor de conexão Ethernet ponto a ponto, ou em um provedor de conexão MPLS. Ver quais [provedores estão disponíveis em sua região](https://azure.microsoft.com/documentation/articles/expressroute-locations/). A conexão direta de ExpressRoute habilitará a conectividade com os aplicativos descritos em [serviços quais Office 365 estão incluídos?](azure-expressroute.md#BKMK_WhatDoIGet) abaixo. Tráfego de rede para todos os outros aplicativos e serviços continuará atravessam a internet.

Considere o seguinte diagrama de rede de nível alto que mostra um cliente do Office 365 típico conectando em centros de dados da Microsoft através da internet para acesso a todos os aplicativos Microsoft, como o Office 365, Windows Update e TechNet. Os clientes usam um caminho de rede semelhantes independentemente se que estão se conectando a partir de uma rede local ou uma conexão de internet independentes.

![Conectividade de rede do Office 365](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Agora, examine o atualizado diagrama que ilustra um cliente do Office 365 que usa a internet e o ExpressRoute para se conectar ao Office 365. Observe que algumas conexões como nós DNS público e a rede de fornecimento de conteúdo ainda exigem a conexão de internet pública. Observe também os usuários do cliente que não estão localizados em seu ExpressRoute construção conectada estiverem se conectando pela Internet.

![Conectividade do Office 365 com ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Deseja ainda mais informações? Saiba como [Gerenciar o tráfego de rede com ExpressRoute do Windows Azure para o Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) e saiba como [Configurar o Azure ExpressRoute para o Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). Também podemos ter gravadas uma série de [ExpressRoute do Windows Azure para treinamento do Office 365](https://channel9.msdn.com/series/aer) 10 parte no Channel 9 para ajudar a explicar os conceitos mais detalhadamente.

([ExpressRoute azure para o Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>Quais serviços do Office 365 estão incluídos?
<a name="BKMK_WhatDoIGet"> </a>

A tabela a seguir lista os serviços do Office 365 suportados pela ExpressRoute. Revise o [artigo de pontos de extremidade do Office 365](https://aka.ms/o365endpoints) para entender quais solicitações de rede para esses aplicativos exigem conectividade com a internet.

|**Aplicativos incluídos**|
|:-----|
|<sup>1</sup> do Exchange Online <br/> Exchange Online Protection<sup>1</sup> <br/> Me aprofundar<sup>1</sup> <br/> |
|Skype para negócios Online<sup>1</sup> <br/> |
|<sup>1</sup> do SharePoint Online <br/> OneDrive for Business<sup>1</sup> <br/> <sup>1</sup> do Project Online <br/> |
|Portal e compartilhado<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD conectar<sup>1</sup> <br/> O Office Online<sup>1</sup> <br/> |

<sup>1</sup> Cada um desses aplicativos têm requisitos de conectividade de internet sem suporte em ExpressRoute, consulte o [artigo de pontos de extremidade do Office 365](https://aka.ms/o365endpoints) para obter mais informações.

Os serviços que não estão inclusos no ExpressRoute para o Office 365 são downloads de cliente Office 365 ProPlus, Sign-In de provedor de identidade no local e serviço do Office 365 (operado pela Vianet 21) na China.

([ExpressRoute azure para o Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>Como implementar o ExpressRoute para Office 365

Implementando ExpressRoute requer o envolvimento dos proprietários de rede e de aplicativos e requer o cuidado de planejamento para determinar a nova [arquitetura de roteamento de rede](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), os requisitos de largura de banda, onde a segurança será implementado, alta disponibilidade, e assim por diante. Para implementar ExpressRoute, você precisará:

1. Entenda totalmente a necessidade de que expressroute atenda no seu planejamento de conectividade do Office 365. Entender quais aplicativos usará internet ou ExpressRoute e totalmente planejar sua capacidade de rede, segurança e alta disponibilidade precisa no contexto do usando a internet e o ExpressRoute para o Office 365 do tráfego.

2. Determine a saída e aos locais de internet e o tráfego de ExpressRoute<sup>1</sup>.

3. Determine a capacidade necessária na internet e ExpressRoute conexões.

4. Adotar um plano de implementação de segurança e outros controles do perímetro padrão<sup>1</sup>.

5. Ter uma conta válida do Microsoft Azure para assinar ExpressRoute.

6. Selecione um modelo de conectividade e um [aprovados pelo provedor](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Tenha em mente, os clientes podem selecionar vários modelos de conectividade ou parceiros e o parceiro não precisa ser o mesmo que o seu provedor de rede existente.

7. Valide implantação antes de direcionar o tráfego para ExpressRoute.

8. Opcionalmente, [implementar QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) e avaliar expansão regional.

<sup>1</sup> Considerações de desempenho importantes. Decisões aqui drasticamente podem afetar a latência que é essencial para aplicativos, como Skype para negócios.

Referências adicionais, use nosso [guia Roteamento](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) , além de [ExpressRoute documentação](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).

Para adquirir ExpressRoute para o Office 365, você precisará trabalhar com um ou mais [aprovada provedores](https://azure.microsoft.com/documentation/articles/expressroute-locations/) para provisionar o número desejado e circuitos de tamanho com uma assinatura ExpressRoute Premium. Não há nenhuma licenças adicionais a compra do Office 365.

Aqui está um link curto que você pode usar para voltar:[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

Pronto para inscrição para [ExpressRoute para o Office 365](https://aka.ms/ert)?

([ExpressRoute azure para o Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>Tópicos relacionados
<a name="BKMK_End"> </a>

[Conectividade de rede para Office 365](network-connectivity.md)

[Como gerenciar o ExpressRoute para a conectividade do Office 365](managing-expressroute-for-connectivity.md)

[Como rotear com o ExpressRoute para Office 365](routing-with-expressroute.md)

[Planejamento de rede com o ExpressRoute para Office 365](network-planning-with-expressroute.md)

[Como implementar o ExpressRoute para Office 365](implementing-expressroute.md)

[Usando o comunidades BGP em ExpressRoute para cenários do Office 365 (preview)](bgp-communities-in-expressroute.md)

[Qualidade de mídia e o desempenho de conectividade de rede no Skype para negócios on-line](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho](performance-tuning-using-baselines-and-history.md)

[Plano de solução de problemas de desempenho do Office 365](performance-troubleshooting-plan.md)

[URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Ajuste de desempenho e de rede do Office 365](network-planning-and-performance.md)
