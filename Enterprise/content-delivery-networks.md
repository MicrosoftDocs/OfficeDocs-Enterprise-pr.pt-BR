---
title: Redes de distribuição de conteúdo
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
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
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Use essas informações para saber mais sobre redes de distribuição de conteúdo (CDNs) e como o Office 365 as utiliza.
ms.openlocfilehash: 50f28e8311a501d9bc5b3f2c709fa84b1633e418
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "30636092"
---
# <a name="content-delivery-networks"></a>Redes de Distribuição de Conteúdo

As informações neste tópico vão ajudá-lo a aprender sobre redes de distribuição de conteúdo (CDNs) e como elas são usadas pelo Office 365.

CDNs ajudar a manter o Office 365 rápido e confiável para usuários finais. Os serviços de nuvem, como o Office 365, usam CDNs para armazenar em cache ativos estáticos mais próximos dos navegadores que os solicitam para acelerar os downloads e reduzir a latência. O Public CDNs permite downloads mais rápidos de conteúdo genérico, como arquivos JavaScript, ícones e imagens, enquanto o CDNs privado pode fornecer acesso rápido e seguro a conteúdo do usuário, como vídeos e bibliotecas de documentos do SharePoint Online.
  
 **Cabeçote de volta para** [Planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).
  
## <a name="what-exactly-is-a-cdn"></a>O que é exatamente uma CDN?

CDNs são usados pela maioria dos serviços de nuvem corporativos. Os serviços de nuvem, como o Office 365, têm milhões de clientes baixando uma mistura de conteúdo proprietário (como emails) e conteúdo genérico (como ícones) ao mesmo tempo. É mais eficiente colocar as imagens que todos usam, como ícones, o mais próximo possível do computador do usuário. No enTanto, não é prático que todos os serviços de nuvem criem datacenters CDN que armazenem esse conteúdo genérico em todas as áreas metropolitanas, ou mesmo em cada Hub de Internet principal em todo o mundo, de forma que alguns desses CDNs sejam compartilhados.
  
CDNs pode ser privado ou público. Os CDNs privados são proprietários e operados por uma única empresa e apenas os aplicativos e serviços da empresa podem usá-lo. Os CDNs públicos são executados por empresas que concedem uso a várias empresas. Dependendo de onde você estiver localizado, talvez seja mais eficiente para o Office 365 baixar imagens genéricas de uma CDN que o Office 365 possui e executa, uma CDN pública ou uma combinação das duas. Independentemente de qual tipo de CDN é usado, as etapas para recuperar os dados são as mesmas.
  
1. O cliente solicita dados do Office 365.

2. O Office 365 retorna os dados diretamente para o cliente ou direciona seu cliente para uma CDN.

3. Se os dados já estiverem armazenados em cache na CDN, seu cliente baixará os dados diretamente do local da CDN mais próximo para o cliente na Internet.

4. Se os dados não estiverem armazenados em cache na CDN, o nó CDN solicitará os dados do Office 365 e, em seguida, armazenará em cache os dados por um período de tempo após o cliente baixar os dados.

O CDNs extrair os arquivos e imagens do datacenter do Office 365 mais próximo e, por sua vez, o cliente recebe os arquivos e imagens da CDN mais próxima. Quando os usuários estão acessando um serviço de nuvem, como a leitura de email no Outlook Web App, o navegador do usuário tenta recuperar os arquivos e imagens do datacenter do Office 365. Em vez de gastar o tempo e a largura de banda fornecendo os arquivos, o Office 365 redireciona o navegador para a CDN. A CDN calcula o datacenter mais próximo ao navegador do usuário e, usando o redirecionamento, baixa as imagens genéricas. O uso desse redirecionamento de CDN é rápido e poupa muito tempo de download dos usuários.

## <a name="how-do-cdns-make-services-work-faster"></a>Como o CDNs faz os serviços funcionarem mais rapidamente?

Baixar itens comuns, como ícones repetidamente, pode ocupar a largura de banda da rede que pode ser usada melhor para baixar conteúdo pessoal importante, como emails ou documentos. Como o Office 365 usa uma arquitetura que inclui o CDNs, os ícones, scripts e outros conteúdos genéricos podem ser baixados de servidores mais próximos dos computadores cliente, tornando os downloads mais rápidos. Isso significa acesso mais rápido ao conteúdo pessoal, que é armazenado com segurança nos datacenters do Office 365.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Como configurar minha rede para que o CDNs funcione melhor com o Office 365?

Se você estiver planejando [a conectividade de rede para o Office 365](network-connectivity.md), é útil entender como o CDNs funciona em geral e como o tráfego de rede da CDN deve ser gerenciado.

Ao habilitar uma CDN para seu locatário do Office 365, você começa definindo políticas que regem as fontes de conteúdo (chamadas **origens** no contexto de CDNs), classificações de dados ou tipos de arquivo que você deseja que sejam distribuídos na CDN. Os usuários que acessarem o conteúdo especificado serão redirecionados para o local mais próximo do arquivo na CDN. Portanto, você deve usar as práticas recomendadas descritas no [Gerenciamento de pontos de extremidade do Office 365](managing-office-365-endpoints.md) para garantir que sua configuração de rede permita que navegadores de clientes acessem a CDN diretamente, em vez de rotear tráfego CDN por meio de proxies centrais para evitar Introdução à latência desnecessária.

## <a name="is-my-data-safe"></a>Meus dados estão seguros?

Temos muito cuidado para ajudar a garantir que protegemos os dados que executam sua empresa. Dados específicos do cliente armazenados no CDNs são criptografados em trânsito e em repouso.

> [!NOTE]
> Os provedores de CDN podem ter padrões de privacidade e conformidade diferentes dos compromissos indicados pela central de confiabilidade do Office 365. Os dados armazenados em cache através do serviço de CDN podem não estar em conformidade com os termos de processamento de dados da Microsoft (DPT) e podem estar fora dos limites de conformidade da central de confiabilidade do Office 365.

Para obter informações detalhadas sobre privacidade e proteção de dados para provedores de CDN do Office 365, visite o seguinte:  

+ Saiba mais sobre a proteção de dados e privacidade do Office 365 na [central de confiabilidade da Microsoft](https://www.microsoft.com/trustcenter)
+ Saiba mais sobre privacidade e proteção de dados do Azure na [central de confiabilidade do Azure](https://azure.microsoft.com/en-us/overview/trusted-cloud/)
+ Saiba mais sobre a privacidade e a proteção de dados da Akamai no [Akamai Privacy Trust Center](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Como posso proteger minha rede com todos esses serviços de terceiros?

O uso de um conjunto abrangente de serviços parceiros permite que o Office 365 dimensione e atenda aos requisitos de disponibilidade, bem como aprimore a experiência do usuário ao usar o Office 365. Os serviços de terceiros do Office 365 aproveitam as listas de certificados revogados; como crl.microsoft.com ou sa.symcb.com, e CDNs; como R3.res.Outlook.com. Cada FQDN de CDN do Office 365 usa é um FQDN personalizado para o Office 365. Se você for enviado para um FQDN na solicitação do Office 365, poderá ter certeza de que o provedor de CDN controla o FQDN e o conteúdo subjacente nesse local.
  
Para clientes que ainda querem segregar solicitações destinadas a um datacenter da Microsoft ou do Office 365 de solicitações destinadas a um terceiro, criamos orientações sobre como [gerenciar pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Há uma lista de todos os CDNs que o Office 365 usa?

O CDNs em uso pelo Office 365 está sempre sujeito a alterações e, em muitos casos, há vários parceiros CDN configurados no evento um não está disponível. O CDNs principal está em uso:

+ [Office 365 (especificamente para conteúdo do SharePoint Online)](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Akamai](https://www.akamai.com/us/en/cdn.jsp)

Essas soluções de CDN têm um alcance global que melhora o alcance do serviço para mais cantos do mundo. O conteúdo armazenado ali inclui scripts, arquivos e imagens gerais do Office 365. Por exemplo, quando você faz logon no portal.office.com, as imagens são extraídas da CDN mais próxima para acelerar o tempo de carregamento da página. Outros exemplos incluem o Office 365 proPlus que armazena os bits de instalação em uma CDN para acelerar a quantidade de tempo que leva para baixar a versão mais recente do Office.

Há também algum conteúdo proprietário armazenado no CDNs, como os arquivos de vídeo para o vídeo do Office 365. Depois que você carregar os vídeos, os arquivos serão criptografados e, em seguida, armazenados em seu formato criptografado com os serviços de mídia do Azure. Quando o player de vídeo do Office 365 recupera o vídeo, primeiro ele é armazenado em cache para a CDN mais próxima antes de ser baixado para acelerar a quantidade de tempo que leva para baixar o vídeo.

Para obter informações sobre como usar a CDN do Office 365, consulte [usar a rede de distribuição de conteúdo do office 365 com o SharePoint Online](use-office-365-cdn-with-spo.md).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Há uma lista de todos os FQDNs que utilizam o CDNs?

A lista de FQDNs e como eles aproveitam o CDNs mudam ao longo do tempo, consulte nossa URL publicada do [Office 365 e](https://go.microsoft.com/fwlink/p/?LinkID=293744) a página de intervalos de endereços IP para se familiarizar com os FQDNs mais recentes que aproveitam o CDNs.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Posso usar minha própria CDN e o conteúdo de cache na minha rede local?

Estamos continuamente procurando novas maneiras de dar suporte às necessidades dos clientes e estamos explorando atualmente o uso de soluções de proxy de cache e outras soluções de CDN no local.

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Estou usando o Azure ExpressRoute para Office 365, isso muda de coisa?

O [Azure ExpressRoute para Office 365](azure-expressroute.md) fornece uma conexão dedicada à infraestrutura 365 do Office que é segregada da Internet pública. Isso significa que os clientes ainda precisarão se conectar por conexões não-ExpressRoute para se conectarem ao CDNs e a outra infraestrutura da Microsoft que não esteja explicitamente incluída na lista de serviços com suporte do ExpressRoute. Para obter mais informações sobre como rotear tráfego específico, como solicitações destinadas a CDNs, consulte o [Gerenciamento de tráfego de rede do Office 365](routing-with-expressroute.md).
  
Aqui está um link curto que você pode usar para voltar: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Confira também

[Gerenciar pontos de extremidade do Office 365](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[URLs e intervalos de endereços IP do Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Usar a rede de distribuição de conteúdo do Office 365 com o SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Central de Confiabilidade da Microsoft](https://www.microsoft.com/trustcenter)