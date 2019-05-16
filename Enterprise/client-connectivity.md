---
title: Conectividade de cliente
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
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
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Resumo: explica como os computadores cliente se conectam aos locatários do Office 365, dependendo do local do computador cliente e do datacenter de locatário do Office 365.'
ms.openlocfilehash: d101af5a0fdd4e29e366b34ad1ab682489f6b3ca
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068197"
---
# <a name="client-connectivity"></a>Conectividade de cliente

 **Resumo:** Explica como os computadores cliente se conectam aos locatários do Office 365, dependendo do local do computador cliente e do datacenter de locatário do Office 365.
  
O Office 365 reside nos datacenters da Microsoft em todo o mundo, o que ajuda a manter o serviço em execução, mesmo quando há um problema significativo em uma região, como um terremoto ou uma queda de energia. Quando você se conectar ao seu locatário do Office 365, a conexão do cliente será direcionada para o datacenter apropriado onde o locatário está sendo hospedado. As regras que determinam onde seu locatário podem ser hospedados são definidas por seu contrato com a Microsoft. As regras que determinam como o cliente adquire os dados desse local de datacenter dependem da arquitetura do serviço que você está usando.
  
Por exemplo, quando você faz logon no portal do Office 365, geralmente está conectado ao datacenter mais próximo ao cliente e, em seguida, direcionado, dependendo do serviço que você usa em seguida. Se você iniciar o email, a conexão inicial para exibir a interface do usuário ainda pode ser proveniente do datacenter mais próximo, mas uma segunda conexão pode ser aberta entre o datacenter mais próximo e o datacenter onde o locatário está localizado para mostrar o que há nos emails que você lê. A Microsoft opera uma das dez principais redes do mundo, resultando em conexões de datacenter incrivelmente rápidas.
  
Depois de ler o artigo, é provável que você entenda por que não fornecemos as [URLs e os intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) por datacenter, eles são simplesmente interconectados e dependentes uns dos outros para torná-lo viável.
  
Se você estiver usando o Azure ExpressRoute para Office 365, na maioria dos casos, sua conectividade passará por uma conexão privada para o Office 365 em vez da conexão pública descrita aqui. Os princípios sobre como os clientes se conectam ainda são precisos. Saiba mais sobre o [Azure ExpressRoute para Office 365](azure-expressroute.md).
  
Para obter mais detalhes sobre as solicitações de rede do Skype for Business, leia o artigo [qualidade de mídia e desempenho de conectividade de rede no Skype for Business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).

||
|:-----|
| Este artigo faz parte do [planejamento de rede e do ajuste de desempenho do Office 365](https://aka.ms/tune).|

> [!NOTE]
> Temos muito cuidado para gerenciar os dados do cliente, de modo que eles sejam seguros e privados em nossos data centers. Os detalhes sobre as etapas tomadas para gerenciar a privacidade estão incluídos na [central de confiabilidade](https://go.microsoft.com/fwlink/?LinkID=397383).
  
## <a name="connecting-to-the-nearest-datacenter"></a>Conectando-se ao datacenter mais próximo

Este é o tipo mais comum de conexão e é usado pelo portal do Office 365 e pelo Exchange Online. Nessa situação, quando os clientes tentam se conectar ao Office 365, a consulta DNS do computador determina a região do mundo da qual o computador está vindo e o Office 365 redireciona a solicitação para o datacenter mais próximo.
  
As conexões com o portal param no datacenter mais próximo e o computador cliente é apresentado com informações sobre o locatário do cliente desse local.
  
O Exchange Online vai um passo adiante. Depois que o computador cliente está conectado ao datacenter mais próximo, um servidor Exchange no datacenter conecta-se ao datacenter onde o locatário está realmente localizado, conforme ilustrado na *seção como funciona* . Os servidores do Exchange Online no datacenter mais próximo então proxy as solicitações do computador cliente para o servidor de caixa de correio. Isso aumenta a experiência do computador cliente, movendo o trabalho pesado da recuperação de emails e itens de calendário para a rede da Microsoft.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>Como isso funciona para ofertas de nuvem padrão?

Esse processo de conexão é padrão para grandes tráfegos, aplicativos Web de alto valor como o Office 365. Nesta seção, descrevemos e ilustramos as etapas no processo. Quando o computador cliente não está na mesma região que o locatário, a conexão parece muito diferente dependendo do serviço ao qual o cliente está se conectando.
  
 Este diagrama ilustra um cliente usando uma oferta padrão do Office 365 com um locatário na América do Norte. Neste cenário, a pessoa que está fazendo a solicitação viajau para a Europa e está usando o Office 365 desse local.
  
1. O computador cliente solicita os servidores DNS locais para o endereço IP associado ao Office 365.

2. Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado ao Office 365.

3. Os servidores DNS da Microsoft retornam o nome do servidor regional (com base no local dos servidores DNS do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter regional do Office 365.

4. O computador cliente se conecta ao endereço IP do datacenter regional.

5. Os servidores do Exchange Online estabelecem uma conexão com o datacenter ativo onde reside o locatário do cliente.

![Datacenter regional mais próximo](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>Como isso funciona para as ofertas de nuvem do soberana?

Essa conexão é um pouco diferente para ofertas de nuvem do soberana, como o Office 365 operado por 21 vianet. Com o locatário em uma instância do soberana do Office 365, os servidores do Office 365 mais próximos que aceitarão conexões do portal são os servidores dentro da região do soberana onde o locatário reside. Da mesma forma, os clientes que acessam o SharePoint Online em nossa nuvem soberana ou ofertas padrão serão direcionados para servidores front-end nos quais o locatário reside. Consulte conectar-se ao datacenter ativo abaixo.
  
1. O computador cliente solicita os servidores DNS locais para o endereço IP associado ao Office 365.

2. Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado ao Office 365.

3. Os servidores DNS da Microsoft retornam o nome do servidor regional (com base no local dos servidores DNS do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter regional do Office 365.

4. O computador cliente se conecta ao endereço IP do datacenter regional.

5. Os servidores do Exchange Online estabelecem uma conexão com o datacenter ativo onde reside o locatário do cliente.

![Datacenter regional dos EUA mais próximo](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>Conexão com o datacenter ativo

A conexão com o datacenter ativo foi projetada para cargas de trabalho de transferência de dados mais pesadas e é usada no momento pelo SharePoint Online. Nessa situação, quando os clientes tentam se conectar ao Office 365, seu navegador é redirecionado para o datacenter ativo para seu locatário do SharePoint Online.
  
## <a name="how-does-this-work"></a>Como isso funciona?

Quando o computador cliente está se conectando ao SharePoint Online a partir de uma região diferente, a conexão é redirecionada para o datacenter ativo do SharePoint Online. Neste cenário, o cliente está usando uma oferta padrão, resultando nas conexões de portal restantes locais e nas conexões do SharePoint Online direcionadas para o datacenter ativo.
  
1. O computador cliente solicita os servidores DNS locais para o endereço IP associado ao Office 365.

2. Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado ao Office 365.

3. Os servidores DNS da Microsoft retornam o nome do servidor do datacenter do SharePoint Online ativo (com base no local do locatário do Office 365 do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter do Office 365 ativo.

4. O computador cliente se conecta ao endereço IP do datacenter ativo.

![Datacenter dos EUA ativo](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>Conectando-se por redes privadas virtuais (VPNs)

Esse tipo de conexão só se aplica quando uma rede virtual privada (VPN) é usada por computadores cliente. Na realidade, o comportamento do Office 365 não é alterado simplesmente porque uma VPN é usada, mas as VPNs são comumente usadas para controlar como os computadores cliente estabelecem conexões com o Office 365 e normalmente resultam em uma experiência degradada, portanto, é importante cobrir.
  
## <a name="how-does-this-work"></a>Como isso funciona?

Quando o computador cliente estabelece uma conexão VPN com um escritório corporativo em uma região diferente, os servidores DNS no Office são usados em vez dos servidores DNS no local do computador cliente. Na maioria dos casos, essa conexão adicional sobre a VPN degradará a experiência do Office 365. Os serviços do Office 365 são otimizados para conexões do cliente de serviço o mais próximo possível do usuário final. Muitos serviços aproveitam a rede de borda do Azure, redes de distribuição de conteúdo e a capacidade de rede confiável na rede da Microsoft para oferecer a melhor experiência de usuário possível quando as solicitações de rede para os serviços do Office 365 são feitas como próximas ao computador cliente possível.
  
1. O computador cliente solicita aos servidores DNS VPN o endereço IP associado ao Office 365.

2. Os servidores DNS VPN do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado ao Office 365.

3. Os servidores DNS da Microsoft retornam o nome do servidor regional (com base no local dos servidores DNS VPN) e o computador cliente repete as etapas 1 e 2 para obter as informações de endereço IP do datacenter regional do Office 365.

4. O computador cliente se conecta ao endereço IP do datacenter que está mais próximo do escritório corporativo que estabeleceu uma conexão VPN com o.

![Conectividade do datacenter de VPN](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
Aqui está um link curto que você pode usar para voltar: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>Confira também

[Gerenciar pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Conectividade de rede para Office 365](network-connectivity.md)
