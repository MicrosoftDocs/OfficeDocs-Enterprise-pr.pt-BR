---
title: Conectividade de cliente
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
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
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Resumo: Explica como os computadores clientes se conectam a locatários do Office 365, dependendo da localização do computador cliente e do datacenter do locatário do Office 365.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223033"
---
# <a name="client-connectivity"></a>Conectividade de cliente

 **Resumo:** Explica como os computadores clientes se conectam a locatários do Office 365, dependendo da localização do computador cliente e do datacenter do locatário do Office 365.
  
O Office 365 reside em datacenters da Microsoft em todo o mundo que ajudam a manter o serviço de backup e executando o mesmo quando há um grande problema em uma região, como um terremoto ou uma interrupção de energia. Quando você se conectar ao seu locatário do Office 365, a conexão do cliente será direcionado para o datacenter apropriado onde seu locatário está sendo hospedado. As regras que determinam onde seu locatário pode ser hospedado são definidas por seu contrato com a Microsoft. As regras que determinam como seu cliente adquire os dados a partir desta localização de datacenter dependem a arquitetura do serviço que você está usando.
  
Por exemplo, quando você fizer logon no portal do Office 365, você está geralmente conectado com o datacenter mais próximo ao cliente e direcionado dependendo do serviço que você use Avançar. Se você abrir o email, a conexão inicial para exibir a interface do usuário pode ainda ser provenientes do datacenter mais próximo, mas uma segunda conexão pode ser aberto entre o datacenter mais próximo e o datacenter onde seu locatário está localizado para mostrar que você está em emails ler. Microsoft opera uma das dez redes principais do mundo, resultando em um datacenter para datacenter extremamente fast conexões rápidas.
  
Após ler o artigo, você provavelmente compreenderá por que não fornecemos [intervalos de endereços IP e URLs do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) por datacenter, eles são simplesmente muito interconexão e dependentes de uns aos outros fazer com que viável.
  
Se você estiver usando o Windows Azure ExpressRoute para o Office 365, na maioria dos casos seu conectividade irão sobre uma conexão privada para Office 365 em vez da conexão pública descrito aqui. Os princípios sobre como os clientes se conectam ainda estão exatos. Saiba mais sobre [ExpressRoute do Windows Azure para o Office 365](azure-expressroute.md).
  
Para mais detalhes no Skype para solicitações de rede de negócios, leia o artigo de [qualidade de mídia e o desempenho da conectividade de rede em Skype para negócios Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).

||
|:-----|
| Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).|

> [!NOTE]
> Podemos tomar muito cuidado para gerenciar dados de cliente, por isso é seguro e privadas em nossos centros de dados. Detalhes sobre as etapas tomada para gerenciar a privacidade estão incluídos na [Central de confiabilidade](https://go.microsoft.com/fwlink/?LinkID=397383).
  
## <a name="connecting-to-the-nearest-datacenter"></a>Conexão com o datacenter mais próximo

Este é o tipo de conexão mais comum, e é usado pelo portal do Office 365 e Exchange Online. Nessa situação, quando os clientes tentam se conectar ao Office 365, consulta DNS do seu computador determina as regiões do mundo que vem de seu computador e Office 365 redireciona a solicitação para o datacenter mais próximo.
  
Conexões ao portal interrompida ao datacenter mais próximo, e o computador cliente é apresentado com informações sobre o locatário do cliente do mesmo local.
  
O Exchange Online vai uma etapa adicional. Depois que o computador cliente estiver conectado com o datacenter mais próximo, um servidor do Exchange em que datacenter se conecta com o datacenter onde o inquilino é realmente localizado, conforme ilustrado no *como faz isso trabalhar seção* abaixo. Os servidores do Exchange Online no datacenter mais próximo e proxy as solicitações do computador cliente para o servidor de caixa de correio. Isso acelera a experiência para o computador cliente, movendo o trabalho pesado de recuperação de emails e itens de calendário para Microsoft network.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>Como isso funciona para ofertas de nuvem padrão?

Esse processo de conexão é o padrão para tráfego intenso, aplicativos da web de alto valor, como o Office 365. Nesta seção, nós de estrutura de tópicos e ilustram as etapas no processo. Quando o computador cliente não estiver na mesma região como o locatário, a conexão se parece muito diferente, dependendo do serviço que o cliente está se conectando.
  
 Este diagrama ilustra um cliente usando uma oferta padrão do Office 365 com um locatário na América do Norte. Neste cenário, a pessoa que está fazendo a solicitação tiver percorrida para Europa e está usando o Office 365 desse local.
  
1. O computador cliente solicita aos servidores DNS locais o endereço IP associado com o Office 365.

2. Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado com o Office 365.

3. Os servidores DNS da Microsoft retornam o nome de servidor regional (com base na localização dos servidores DNS do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter regional do Office 365.

4. O computador cliente se conecta ao endereço IP do datacenter regional.

5. Os servidores do Exchange Online estabelecem uma conexão com o datacenter ativo onde o locatário do cliente reside.

![Datacenter regional mais próximo](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>Como esse trabalho para sovereign nuvem ofertas?

Essa conexão é ligeiramente diferente para ofertas de nuvem soberana como o Office 365 operado pela Vianet 21. Com o locatário em uma instância de soberana do Office 365, os servidores do Office 365 mais próximo que aceitarão conexões de portal são os servidores com a região soberana cujo locatário reside. Da mesma forma, os clientes acessando SharePoint Online em nosso soberana nuvem ou ofertas padrão serão direcionados para servidores front-end cujo locatário reside. Consulte a conexão com o datacenter ativo abaixo.
  
1. O computador cliente solicita aos servidores DNS locais o endereço IP associado com o Office 365.

2. Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado com o Office 365.

3. Os servidores DNS da Microsoft retornam o nome de servidor regional (com base na localização dos servidores DNS do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter regional do Office 365.

4. O computador cliente se conecta ao endereço IP do datacenter regional.

5. Os servidores do Exchange Online estabelecem uma conexão com o datacenter ativo onde o locatário do cliente reside.

![Datacenter regional dos EUA mais próximo](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>Conexão com o datacenter ativo

Conexão com o datacenter ativo foi projetado para cargas de trabalho de transferência de dados mais pesadas e está sendo usado pelo SharePoint Online. Nessa situação, quando os clientes que tentam se conectar ao Office 365, seu navegador é redirecionado para o datacenter ativo para seu locatário do SharePoint Online.
  
## <a name="how-does-this-work"></a>Como isso funciona?

Quando o computador cliente está se conectando ao SharePoint Online a partir de uma região diferente, a conexão é redirecionada para o datacenter ativo de SharePoint Online. Neste cenário, o cliente está usando um padrão que oferece, resultando nas conexões de portal remanescente local e as conexões do SharePoint Online, sendo direcionadas para o datacenter ativo.
  
1. O computador cliente solicita aos servidores DNS locais o endereço IP associado com o Office 365.

2. Os servidores DNS locais do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado com o Office 365.

3. Os servidores DNS da Microsoft retornam o nome do servidor do SharePoint Online datacenter ativo (com base na localização do locatário do Office 365 do cliente) e o computador cliente repete as etapas 1 e 2 para obter o endereço IP do datacenter ativo do Office 365.

4. O computador cliente se conecta ao endereço IP do datacenter ativo.

![Datacenter dos EUA ativo](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>Conexão em Redes Virtuais Privadas (VPN)

Esse tipo de conexão se aplica somente quando uma rede virtual privada (VPN) é usada pelos computadores cliente. Na realidade, comportamento do Office 365 não será alterado simplesmente como uma VPN é usada, mas VPNs são comumente usadas para controlar como os computadores cliente estabelecem conexões com o Office 365 e, normalmente, os resultados em uma experiência de degradação, portanto é importante cobrir.
  
## <a name="how-does-this-work"></a>Como isso funciona?

Quando o computador cliente estabelece uma conexão VPN para um escritório corporativo em uma região diferente, os servidores DNS no que office são usados no lugar de servidores DNS do local do computador cliente. Na maioria dos casos, essa conexão extra através da VPN prejudicará a experiência do Office 365. Os serviços do Office 365 otimizados para conexões de cliente do serviço como e está perto do usuário final possível. Muitos serviços aproveitam a rede de borda do Azure, redes de fornecimento de conteúdo e a capacidade de rede confiável na rede Microsoft para oferecer a melhor experiência de usuário possíveis quando são feitas solicitações de rede para serviços do Office 365 mais próximo do computador cliente possível.
  
1. O computador cliente solicita o DNS VPN servidores para o endereço IP associado com o Office 365.

2. Servidores de DNS VPN do computador cliente solicitam aos servidores DNS da Microsoft o endereço IP associado com o Office 365.

3. Os servidores DNS da Microsoft retornam o nome de servidor regional (com base na localização dos servidores DNS da VPN) e o computador cliente repete as etapas 1 e 2 para obter as informações de endereço IP do datacenter regional do Office 365.

4. O computador cliente se conecta com o datacenter endereço IP que mais se aproxima ao escritório corporativo com que eles estabelecerem uma conexão VPN.

![Conectividade do datacenter de VPN](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
Aqui está um link curto que você pode usar para voltar:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>Confira também

[Gerenciando pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Conectividade de rede para Office 365](network-connectivity.md)
