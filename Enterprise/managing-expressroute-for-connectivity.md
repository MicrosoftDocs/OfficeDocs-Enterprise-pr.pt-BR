---
title: Como gerenciar o ExpressRoute para a conectividade do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: ExpressRoute para o Office 365 oferece um caminho alternativo de roteamento para acessar muitos serviços do Office 365 sem a necessidade de todo o tráfego de saída para a internet. Embora a conexão de internet para o Office 365 ainda for necessário, as rotas específicas que Microsoft anuncia por meio de BGP à sua rede Verifique circuito ExpressRoute direto preferencial, a menos que existem outras configurações em sua rede. As três áreas comuns, que convém configurá-la para gerenciar este roteamento incluem prefixo a filtragem, segurança e conformidade.
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539196"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Como gerenciar o ExpressRoute para a conectividade do Office 365

ExpressRoute para o Office 365 oferece um caminho alternativo de roteamento para acessar muitos serviços do Office 365 sem a necessidade de todo o tráfego de saída para a internet. Embora a conexão de internet para o Office 365 ainda for necessário, as rotas específicas que Microsoft anuncia por meio de BGP à sua rede Verifique circuito ExpressRoute direto preferencial, a menos que existem outras configurações em sua rede. As três áreas comuns, que convém configurá-la para gerenciar este roteamento incluem prefixo a filtragem, segurança e conformidade.
  
> [!NOTE]
> Microsoft alterado como o domínio de roteamento do Microsoft Peering seja analisado para ExpressRoute do Windows Azure. Iniciando 31 de julho de 2017, todos os clientes do Windows Azure ExpressRoute podem habilitar Microsoft Peering diretamente no console administrativo do Windows Azure ou por meio do PowerShell. Após a habilitação do Microsoft Peering, qualquer cliente pode criar filtros de roteamento para receber os anúncios de rota BGP para aplicativos do contrato de cliente do Dynamics 365 (anteriormente conhecidos como CRM Online). Clientes que precisam de ExpressRoute do Windows Azure para o Office 365 devem obter a revisão da Microsoft antes que possam criar filtros de roteamento para o Office 365. Entre em contato com sua equipe de Account da Microsoft para saber mais sobre como solicitar uma revisão para habilitar ExpressRoute do Office 365. As assinaturas não autorizadas tentar criar filtros de roteamento para o Office 365 receberá uma [mensagem de erro](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Prefixo de filtragem

A Microsoft recomenda que os clientes aceitam todas as rotas BGP como anunciado da Microsoft, as rotas fornecidas passar por um processo de revisão e validação rigoroso, removendo qualquer benefícios para exames detalhados adicionado. ExpressRoute nativamente oferece os controles recomendados, como a propriedade de prefixo IP, a integridade e escala - com nenhuma rota de entrada de filtragem do lado do cliente.
  
Se você precisar outras validações de propriedade de rota entre ExpressRoute pública correspondência, você pode verificar as rotas anunciadas em relação à lista de todos os prefixos de IPv4 e IPv6 IP que representam os [intervalos IP públicos da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Esses intervalos abordam o espaço de endereço completo do Microsoft e alterar raramente, fornecendo um conjunto confiável de intervalos para filtrar contra que também fornece proteção adicional aos clientes que se preocupam não-Microsoft pertencente rotas vazamento em seus ambiente. No caso haja uma alteração, ela será feita no 1st do mês e o número da versão na seção **detalhes** da página será alterada sempre que o arquivo é atualizado.
  
Há vários motivos para evitar o uso dos [intervalos de endereços IP e URLs do Office 365](https://aka.ms/o365endpoints) para gerar as listas de filtro de prefixo. Incluindo o seguinte:
  
- Os prefixos de IP do Office 365 passar por muitas das alterações com frequência.

- As URLs do Office 365 e o endereço IP intervalos projetados para gerenciar o firewall permitem listas e infraestrutura de Proxy, não o roteamento.

- Os intervalos de endereços IP e URLs do Office 365 não abordam outros serviços da Microsoft que podem estar em um escopo para suas conexões de ExpressRoute.

| |
|**Opção**|**Complexidade**|**Controle de alterações**|
|:-----|:-----|:-----|
|Aceitar todas as rotas da Microsoft  <br/> |**Baixa:** Cliente depende de controles da Microsoft para garantir que todas as rotas são de propriedade adequadamente.  <br/> |None  <br/> |
|Microsoft Filter pertencente super-redes  <br/> |**Médio:** Cliente implementa as listas de filtro de prefixo resumidos para permitir que somente Microsoft pertencente rotas.  <br/> |Os clientes devem assegurar que as atualizações esporádicos são refletidas nos filtros de rota.  <br/> |
|Filtrar intervalos de IP do Office 365  <br/> [!CAUTION] Não é recomendável
|**Alta:** Cliente filtra rotas com base em prefixos de IP do Office 365 definidos.  <br/> |Os clientes devem implementar um processo de gerenciamento de alterações robusta para obter as atualizações mensais.  <br/> [!CAUTION]Essa solução requer alterações significativas de contínuas. Alterações não implementadas no tempo provavelmente resultará em uma interrupção de serviço.   |

Conectar-se ao Office 365 usar o Windows Azure ExpressRoute se baseia em anúncios BGP de subredes de IP específicas que representam redes onde os pontos de extremidade do Office 365 estão implantados. Devido à natureza global do Office 365 e o número de serviços que compõem o Office 365, os clientes frequentemente têm necessidade de gerenciar os anúncios que eles aceitarem em sua rede. Se você estiver preocupado com o número de prefixos divulgado em seu ambiente, o recurso de [comunidade BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) permite filtrar os anúncios para um conjunto específico de serviços do Office 365. Esse recurso agora está no modo de visualização.
  
Independentemente de como você gerencia os anúncios de rota BGP provenientes da Microsoft, você não obtém qualquer exposição especial para serviços do Office 365, quando comparada com a conexão para o Office 365 em um circuito de internet sozinho. A Microsoft mantém a mesma segurança, conformidade e níveis de desempenho, independentemente do tipo de circuito de que um cliente usa para se conectar ao Office 365.
  
### <a name="security"></a>Segurança

A Microsoft recomenda que você mantenha seus próprios controles de perímetro de rede e segurança para conexões indo de e ExpressRoute pública e a correspondência da Microsoft, que inclui conexões de serviços do Office 365. Controles de segurança devem estar prontas para solicitações de rede que viajar saída da sua rede para a rede da Microsoft, bem como de entrada da rede da Microsoft em sua rede.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Saída do cliente para a Microsoft
  
Quando os computadores se conectam ao Office 365, eles se conectam ao mesmo conjunto de pontos de extremidade independentemente se a conexão é feita por um circuito ExpressRoute ou internet. Independentemente do circuito que está sendo usado, a Microsoft recomenda que você trata serviços do Office 365, como mais confiável que genérico destinos da internet. Os controles de segurança de saída devem focalizar as portas e protocolos para reduzir a exposição e minimizar a manutenção contínuas. As informações de porta necessários estão disponíveis no artigo de referência de [pontos de extremidade do Office 365](https://aka.ms/o365endpoints) .
  
Para controles adicionados, você pode usar o nível FQDN filtragem dentro de sua infra-estrutura de proxy para restringir ou inspecionar algumas ou todas as solicitações de rede destinadas a internet ou Office 365. Mantém a lista dos FQDNs como recursos são lançados e as ofertas de Office 365 evoluem requer o gerenciamento de alteração mais robusto e controle de alterações para o publicado [pontos de extremidade do Office 365](https://aka.ms/o365endpoints).
  
> [!CAUTION]
> A Microsoft recomenda que você não confie exclusivamente em prefixos IP para gerenciar a segurança de saída para o Office 365.

|**Opção**|**Complexidade**|**Controle de alterações**|
|:-----|:-----|:-----|
|Sem restrições  <br/> |**Baixa:** Cliente permite acesso irrestrito de saída para a Microsoft.  <br/> |None  <br/> |
|Restrições de porta  <br/> |**Baixa:** Cliente restringe o acesso de saída para a Microsoft pelas portas esperadas.  <br/> |Não frequentes.  <br/> |
|Restrições de FQDN  <br/> |**Alta:** Cliente restringe o acesso de saída para o Office 365 com base nos FQDNs publicados.  <br/> |Alterações mensais.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Entrada da Microsoft no cliente
  
Há vários cenários opcionais que exigem o Microsoft iniciar as conexões à sua rede.
  
- ADFS durante a validação de senha para a entrada.

- [Implantações híbridas do Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- Email de um locatário do Exchange Online para um host local.

- Caixas de correio Online do SharePoint enviar do SharePoint Online para um host local.

- [SharePoint federados pesquisa híbrida](https://technet.microsoft.com/library/dn197174.aspx).

- [SharePoint híbrido BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype para o híbrido de negócios](https://technet.microsoft.com/en-us/library/jj205403.aspx) e/ou [Skype para federação de negócios](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype para o Business Connector de nuvem](https://technet.microsoft.com/library/mt605227.aspx ).

A Microsoft recomenda que você aceita essas conexões via seu circuito de internet, em vez de seu circuito ExpressRoute para reduzir a complexidade. Se o seu desempenho ou conformidade precisa dita que essas conexões de entrada devem ser aceitas via um circuito ExpressRoute, recomenda-se o usando um firewall ou proxy reverso para as conexões aceitas de escopo. Você pode usar os [pontos de extremidade do Office 365](https://aka.ms/o365endpoints) para descobrir o direito FQDNs e os prefixos IP.
  
### <a name="compliance"></a>Conformidade

Nós não confie no caminho de roteamento, que você pode usar para qualquer um dos nossos controles de conformidade. Independentemente de se conectar aos serviços do Office 365 sobre um circuito ExpressRoute ou internet, não alterará a nossos controles de conformidade. Você deve consultar a conformidade diferente e os níveis de certificação de segurança para o Office 365 descobrir a melhor escolha para atender às necessidades da sua organização.
  
Aqui está um link curto que você pode usar para voltar:[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>Tópicos relacionados

[Redes de distribuição de conteúdo](content-delivery-networks.md)
  
[URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Gerenciando pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute treinamento do Office 365](https://channel9.msdn.com/series/aer)
