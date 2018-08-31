---
title: Vídeo do Office 365 networking perguntas frequentes
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: O repositório de vídeo do Office 365 e serviços de fluxo de simplificam armazenando e streaming vídeos dentro da sua organização. Não há uma muitas informações sobre o vídeo do Office 365; Estas perguntas Frequentes de rede foi projetado para responder as perguntas mais comuns em torno de planejamento, criptografia e como o serviço aproveita redes de fornecimento de conteúdo (CDNs) de largura de banda.
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539207"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Vídeo do Office 365 networking perguntas frequentes

O repositório de vídeo do Office 365 e serviços de fluxo de simplificam armazenando e streaming vídeos dentro da sua organização. Não há uma muitas [informações sobre o Office 365 vídeo](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); Estas perguntas Frequentes de rede foi projetado para responder as perguntas mais comuns em torno de planejamento, criptografia e como o serviço aproveita [redes de fornecimento de conteúdo (CDNs)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)de largura de banda.
  
Se você já não tiver uma compreensão detalhada do que acontece quando um vídeo é carregado ou reproduzida, dê uma olhada neste vídeo, fazemos juntos, [o que acontece com um arquivo de vídeo quando carregados para o vídeo do Office 365](https://www.youtube.com/watch?v=HXSZ0jYBKlM).
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Quais são os requisitos de largura de banda de vídeo do Office 365?

Há um diversos [formatos de vídeos com suporte](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) que podem ser transferidos para o Office 365. Cada arquivo de vídeo é codificado, em seguida, para um formato padrão com várias qualidades diferentes de vídeos para reprodução. Vídeo do Office 365 usa uma taxa de bits adaptável streaming para selecionar a melhor qualidade de reprodução de vídeo com base na largura de banda de rede disponível e o tamanho do player de vídeo. Para fazer isso, o player inicialmente solicitações a mais baixa qualidade de reprodução. O serviço começa a enviar segmentos de vídeos de 2 segundos para o player de vídeo. O player, pode solicitar a qualidade de reprodução superior ou inferior com base em como rapidamente a cada segmento é entregue.
  
A taxa de bits adaptável streaming faz isso em segundo plano, enquanto o vídeo é reproduzido com o mínimo de interrupção ou armazenamento em buffer. Durante a reprodução de vídeo, o player de vídeo permite que o Visualizador de substituir manualmente a qualidade de reprodução automática, para selecionar uma qualidade de reprodução de vídeo específico.
  
Aqui está uma tabela rápida que descreve os requisitos de rede para cada um dos qualidades a reprodução de vídeo. A largura de banda por pessoa necessária para reproduzir um vídeo é 802Kbps.
  
|||
|:-----|:-----|
|**Qualidade de reprodução** <br/> |**Velocidade da rede** <br/> |
|288p  <br/> |802kbps  <br/> |
|360p  <br/> |1.2 Mbps  <br/> |
|576p  <br/> |2.5 Mbps  <br/> |
|720 pixels  <br/> |3,8 Mbps  <br/> |

([Voltar ao topo](office-365-video-networking-faq.md))
  
## <a name="how-do-cdns-help-video-playback"></a>Como CDNs ajudam a reprodução de vídeo?

Se várias pessoas da mesma organização dentro da mesma localidade geográfica são streaming de vídeo mesmo (s), CDNs irá armazenar uma cópia destes vídeos em um local mais próximo para essa região geográfica. Com o vídeo armazenados ou em cache no local mais próximo, cada pessoa transmite o vídeo do local mais próximo a eles, em vez de um local ainda mais ausente. Vídeo do Office 365 usa os serviços de mídia do Windows Azure para gerenciar o que é armazenado em cache as CDNs Azure e por quanto tempo. Serviços do Azure mídia pode usar qualquer um dos [locais de CDN do Windows Azure](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) para armazenar em cache fragmentos de vídeos e manifestos por alguns dias. Se as pessoas na sua organização continuam a Assista aos vídeos de cache, eles permanecerão no cache. Se nenhum acessa um vídeo por vários dias, o vídeo será eventualmente drop descartados do cache. Na próxima vez em que alguém tentar fazer Assista ao vídeo ele é mais uma vez armazenado em cache no local CDN mais próximo.
  
Todas as pessoas que tenta Assista ao vídeo enquanto o conteúdo é armazenado em cache em um benefícios CDN próximos do vídeo sendo mais próximo e na maioria dos casos menos saltos, ausente. Isso melhora a velocidade de reprodução de vídeo; No entanto, ele não altera o requisito de rede para reproduzir o vídeo.
  
> [!NOTE]
> Há algumas circunstâncias, como nosso limite de capacidade está sendo atingido, onde o vídeo pode ser removido antes dos três dias foi atingido.
  
([Voltar ao topo](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>Posso armazenar os vídeos localmente para reprodução mais rápido em cache?

Sim. Office 365 não impede que você use uma CDN local ou um proxy de cache para traga vídeo ou outro conteúdo do Office 365 para sua rede local para acesso mais rápido. Há várias maneiras para implementar uma solução local de cache em sua rede, o método mais comum é usar uma solução de proxy que armazena em cache o conteúdo localmente. Depois que um proxy ou CDN privada tiver armazenado em cache os fragmentos de vídeos e manifestos, as solicitações futuras para esses arquivos que rotear por meio do proxy ou CDN privada são extraídas de cache local e não extraídas de um local da internet. Considere a largura de banda de rede, a capacidade e simultaneidade de reprodução de vídeo durante o planejamento de uma solução semelhante a esta.
  
([Voltar ao topo](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>Como vídeos são criptografados e protegidos?

Vídeo do Office 365 sabe como é importante manter seus dados seguros e particulares. [O Centro de confiança do Office 365](https://products.office.com/business/office-365-trust-center-cloud-computing-security) descreve nosso compromisso com a privacidade e segurança de seu conteúdo. Com a reprodução de vídeo, a velocidade é importante para uma boa experiência; No entanto, podemos não comprometer a segurança ou privacidade, em troca de velocidade. Aqui está como podemos acomodar velocidade, segurança e privacidade.
  
Quando você ou alguém em sua organização carrega um novo vídeo, se o vídeo é transcodificados, criptografadas com criptografia AES-128 e armazenados no Azure Media Services. Isso significa que os vídeos são criptografados em trânsito e em repouso.
  
Quando alguém em sua organização tenta Assista a um novo vídeo, eles siga estas etapas:
  
1. Pergunte SharePoint Online se eles têm permissão para exibir o vídeo.

2. SharePoint Online usa as permissões de arquivo para determinar se a pessoa pode Assista ao vídeo.

3. Se eles têm permissão, SharePoint Online recupera um token do Windows Azure para passar para o player de vídeo.

4. O player de vídeo, em seguida, usa o token para solicitar a chave de descriptografia do Azure.

5. Com a chave de descriptografia prontas, o player de vídeo é capaz de fluxo de vídeo.

![O365 Reprodução de vídeo](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([Voltar ao topo](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Quais são os requisitos para reprodução de vídeo do Office 365?

Vídeo do Office 365 com suporte a sistemas operacionais e navegadores da web são os mesmos que os requisitos do SharePoint Online nos [requisitos de sistema do Office 365](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). Dependendo de qual sistema operacional e web, você tem a configuração do navegador determinará às necessidades específicas do player de vídeo. Eis aqui para obter mais informações sobre os [requisitos de reprodução de vídeo](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).
  
([Voltar ao topo](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Não é possível obter Office 365 vídeo funcione, onde posso começar?

Resolver problemas de conectividade para o Office 365 vídeo envolve a solução de problemas de rede, sua ISP(s) e sua configuração do Office 365. O primeiro ponto de partida é o painel de integridade do serviço. Isso informará que você de vídeo do Office 365 está tendo um problema ou não. Se tudo parece ótimo lá, eis alguns recursos adicionais para ajudá-lo.
  
- Verifique se que é possível conectar aos [pontos de extremidade de rede necessários para vídeo do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

- Verificar a conectividade da rede usando nosso [guia resolução de problemas de rede de Office 365](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).

- Consulte nossas [práticas recomendadas para usar o Office 365 em uma rede lenta](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).

- Encontre a [Ajuda sobre a configuração de vídeo do Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([Voltar ao topo](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Recursos de vídeo do Office 365

Classifique o tópico e deixe um comentário para nos informar se respondemos suas dúvidas ou se você ainda estiver procurando por respostas. Eis alguns de nossos outros recursos para ajudá-lo a implantar e usar o vídeo do Office 365 com êxito:
  
[Encontrar ajuda sobre configuração de vídeo do Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).
  
[Reunir vídeo do Office 365](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Criar e gerenciar um canal no vídeo do Office 365](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Gerenciar seu portal de vídeo do Office 365](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Formatos de vídeo que funcionam no vídeo do Office 365](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([Voltar ao topo](office-365-video-networking-faq.md))
  
Aqui está um link curto que você pode usar para voltar:[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
