---
title: Redes de distribuição de conteúdo
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
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
description: Use essas informações para saber mais sobre redes de fornecimento de conteúdo (CDNs) e como Office 365 se beneficia delas. CDNs ajudam a manter o Office 365 rápida e confiável para os usuários finais. Com as CDNs, serviços de nuvem, como o Office 365 rapidamente baixem conteúdo genérico, como ícones, ao navegador dos usuários quando eles estão usando o serviço por meio de um cliente web.
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539397"
---
# <a name="content-delivery-networks"></a>Redes de distribuição de conteúdo

Use essas informações para saber mais sobre redes de fornecimento de conteúdo (CDNs) e como Office 365 se beneficia delas. CDNs ajudam a manter o Office 365 rápida e confiável para os usuários finais. Com as CDNs, serviços de nuvem, como o Office 365 rapidamente baixem conteúdo genérico, como ícones, ao navegador dos usuários quando eles estão usando o serviço por meio de um cliente web.
  
 **Cabeça de volta ao** [Planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Como deve configurar o minha rede para que as CDNs funcionem melhor com o Office 365?

Se você estiver planejando a [conectividade de rede para o Office 365](network-connectivity.md), é útil compreender como as CDNs funcionem. Também é importante entender que não é possível filtrar conectividade com as CDNs por endereço IP. Fornecemos uma lista de esforço práticas de IPs para os serviços no Office 365, como o Exchange Online. Saiba mais sobre nossas recomendações para [Gerenciar o Office 365 pontos de extremidade](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="how-do-cdns-make-services-work-faster"></a>Como as CDNs agilizam o funcionamento dos serviços?

Baixar itens comuns, como ícones repetidamente pode demorar até a largura de banda de rede que pode ser usada melhor para download de conteúdo pessoal importante, como email ou documentos. Como o Office 365 usa uma arquitetura que inclui CDNs, os ícones, scripts e outros conteúdos genérico podem ser baixado em servidores mais próximo para computadores clientes, tornando os downloads mais rápidos. Isso significa acesso mais rápido a seu conteúdo pessoal, que é armazenado com segurança em centros de dados do Office 365.
  
## <a name="what-exactly-is-a-cdn"></a>O que é uma CDN exatamente?

CDNs são usados pela maioria dos serviços de nuvem da empresa. Serviços de nuvem, como o Office 365 tem milhões de clientes, baixando uma mistura de conteúdo proprietário (como emails) e conteúdo genérico (por exemplo, ícones) ao mesmo tempo. É mais eficiente para colocar imagens que todos usam, como ícones, conforme perto do computador do usuário quanto possível. Ainda assim, não é prático para cada serviço na nuvem construir CDN data centers que armazenam esse conteúdo genérico em cada área metropolitana ou até mesmo em cada hub de Internet principal no mundo todo, portanto alguns desses CDNs são compartilhados.
  
CDNs podem ser privada ou pública. CDNs privadas são pertencentes operados por uma única empresa e somente essa empresa aplicativos e serviços podem usá-lo. As CDNs públicas são executadas pelas empresas que arrendar uso para várias empresas. Dependendo de onde você está localizado, talvez seja mais eficiente para o Office 365 baixar imagens genéricas para você de uma CDN proprietária do Office 365 e é executado, uma CDN pública ou uma combinação dos dois. Independentemente de qual tipo de CDN for usado, as etapas para recuperar os dados são os mesmos.
  
1. Seu cliente solicita dados do Office 365.

2. O Office 365 retorna os dados diretamente para o seu cliente ou direciona o seu cliente para uma CDN.

3. Se os dados já é armazenado em cache na CDN, seu cliente baixa os dados diretamente do local de CDN mais próximo ao seu cliente na internet.

4. Se os dados não não armazenado em cache na CDN, o nó CDN solicita os dados do Office 365 e, em seguida, o cache dos dados por um período de tempo depois que o seu cliente baixa os dados.

As CDNs extrair os arquivos e imagens do datacenter mais próximo do Office 365 e, por sua vez, o seu cliente recebe os arquivos e imagens da CDN mais próxima. Quando os usuários acessam um serviço em nuvem, como ao ler um email no Outlook Web App, o navegador do usuário tenta recuperar os arquivos e imagens do datacenter do Office 365. Em vez de gastar o tempo e a largura de banda como entregar os arquivos, o Office 365 redireciona o navegador para a CDN. A CDN descobre o datacenter mais próximo ao navegador do usuário e, usando o redirecionamento, downloads as imagens genéricas a partir daí. Usando o redirecionamento de CDN é rápido e salvará usuários muito tempo de download.
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Há uma lista de todos os FQDNs que otimizam as CDNs?

Lista de FQDNs e como eles utilizam CDNs alteração ao longo do tempo, consulte nosso publicada [página de pontos de extremidade do Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744) para obter os FQDNs mais recentes que otimizam as CDNs atualizado.
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Há uma lista de todas as CDNs que usa Office 365?

As CDNs em uso pelo Office 365 são sempre está sujeita a alterações e em muitos casos, há vários parceiros CDN configurados no caso de um estiver indisponível. Os dois CDNs mais comuns em uso são [Akamai](https://www.akamai.com/us/en/cdn.jsp) e [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/). Ambos dessas soluções CDN têm um alcance global aprimorando o alcance do serviço para os cantos mais do mundo. O conteúdo armazenado lá inclui gerais scripts, arquivos e imagens do Office 365. Por exemplo, quando você efetua logon portal.office.com, as imagens são retiradas da CDN mais próxima para acelerar os tempos de carregamento de página. Outros exemplos incluem o Office 365 ProPlus armazenando os bits de instalação em uma CDN para acelerar a quantidade de tempo que leva para baixar a versão mais recente do Office. Também há algum conteúdo proprietário que está armazenado no CDNs como os arquivos de vídeo para vídeo do Office 365. Depois que você carregar os vídeos, os arquivos são criptografados e, em seguida, armazenados em seu formato criptografado com o Windows Azure Media Services. Quando o player de vídeo do Office 365 recupera o vídeo a ele está pela primeira vez em cache para o mais próximo CDN antes que está sendo baixado para acelerar a quantidade de tempo que leva para baixar o vídeo.
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a>Office 365 oferece uma CDN que eu posso usar meus próprios arquivos?

Sim! Sua assinatura do Office 365 agora inclui uma CDN separado do Azure que você pode usar especificamente para os ativos do SharePoint Online. Para obter informações sobre como usar o Office 365 CDN, consulte [usar a rede de fornecimento de conteúdo do Office 365 com o SharePoint Online](use-office-365-cdn-with-spo.md).
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Pode usar meu próprios CDN e cache de conteúdo na minha rede local?

Nós queremos continuamente novas maneiras dar suporte a nossas necessidades de clientes e atualmente estão explorando o uso de soluções de proxy e outras soluções CDN do local de cache.
  
## <a name="is-my-data-safe"></a>Meus dados estão seguros?

Podemos tomar muito cuidado para ajudar a garantir que podemos proteger os dados que executa o seu negócio. Os itens armazenados em nossos parceiros de rede de fornecimento de conteúdo são criptografados; como com [Vídeo do Office 365](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)ou não específico; do cliente como os arquivos de instalação do Office 365 ProPlus. Vá diretamente para a [Central de confiabilidade do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=397383) para saber mais sobre nossos esforços aprofundados para proteger sua privacidade e seus dados.
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Como posso proteger meu rede com todos esses serviços de terceiros 3º?

A utilização de um amplo conjunto de serviços de parceiros permite o Office 365 dimensionar e atender aos requisitos de disponibilidade, bem como aprimorar a experiência do usuário ao usar o Office 365. Os serviços de terceiros 3º que Office 365 se beneficia incluem duas listas de revogação de certificado; como crl.microsoft.com ou sa.symcb.com e CDNs; como r3.res.outlook.com. Cada CDN FQDN Office 365 usa é um FQDN personalizado para o Office 365, se você estiver enviado a um FQDN por solicitação do Office 365 você pode ter certeza que podemos controlar o FQDN e subjacente conteúdo nesse local.
  
Para clientes que ainda quiser segregar solicitações destinadas a um datacenter da Microsoft ou Office 365 de solicitações destinadas a uma parte confiável 3º, escreveu backup orientação em [pontos de extremidade de gerenciamento do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Estou usando o Windows Azure ExpressRoute para o Office 365, que alteram as coisas?

[ExpressRoute do Windows Azure para o Office 365](azure-expressroute.md) fornece uma conexão dedicado à infraestrutura do Office 365 que é segregar da internet pública. Isso significa que os clientes ainda precisará se conectam via conexões não-ExpressRoute para se conectar ao CDNs e outra infraestrutura da Microsoft que não está incluída na lista de serviços suportados pelo ExpressRoute explicitamente. Para obter mais informações sobre como rotear tráfego específico, como solicitações destinadas a CDNs, consulte [gerenciamento de tráfego de rede do Office 365](routing-with-expressroute.md).
  
Aqui está um link curto que você pode usar para voltar:[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Confira também

[Pontos de extremidade perguntas Frequentes do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
