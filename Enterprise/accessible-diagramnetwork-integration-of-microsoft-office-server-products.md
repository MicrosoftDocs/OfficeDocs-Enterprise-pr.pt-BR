---
title: Diagrama acessível - rede integração dos produtos Microsoft Office Server
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: Este artigo é uma versão de texto acessível do diagrama denominado rede integração dos produtos Microsoft Office Server.
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504424"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>Diagrama acessível - rede integração dos produtos Microsoft Office Server

**Resumo:** Este artigo é uma versão de texto acessível do diagrama denominado rede integração dos produtos Microsoft Office Server.
  
Este cartaz fornece uma ilustração geral de um ambiente de rede que inclua o Lync Server 2013, SharePoint 2013 e Exchange Server 2013. Ele também ilustra os seguintes elementos de redes que são comuns entre esses produtos: acesso remoto e interno, autenticação, o tráfego do cliente e rotear o tráfego por meio de dispositivos compartilhados. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Conceitos de alto nível do Lync, Exchange, SharePoint Server e Office Web Apps

### <a name="about-the-design"></a>Sobre o design

#### <a name="streamlined-network-design"></a>Design de rede simplificadas

Essa topologia ilustra uma implantação de rede local do SharePoint 2013, Exchange Server 2013 e Lync Server 2013. Ele também mostra o uso do serviço de nuvem do Microsoft, Exchange Online Protection, que oferece proteção contra spam e malware Simple Mail Transfer Protocol (SMTP) para tráfego de entrada da Internet. 
  
Esse projeto de rede é simplificado a fim de um conjunto mínimo de recursos de rede. O design não leva em conta infraestrutura ou segurança recursos adicionais que algumas organizações podem exigir. 
  
Este diagrama: 
  
- Fornece uma topologia de rede de exemplo que ilustram o tráfego de entrada e saído por meio de um roteador de gateway e o balanceamento de carga de sessão tráfego do cliente (interno e externo) para as camadas de servidor do SharePoint, Exchange e Lync apropriados. 
    
- Mostra o uso de servidores de acesso remoto opcional, um gateway VPN de terceiros ou o servidor DirectAccess, para fornecer comunicações seguras para os funcionários móveis ou remotos. 
    
- Fornece detalhes sobre o SharePoint, Exchange e Lync fluxo de tráfego do cliente para cada camada do servidor de plataforma. 
    
- Identifica o tipo de conexão de acesso remoto ou interno com base no cliente (por exemplo, parceiros ou funcionários) e o método de autenticação usado. 
    
- Rompe as plataformas do SharePoint, Exchange e Lync pelas funções de servidor necessárias, que identifica o front-end, aplicativo, banco de dados e outros níveis. 
    
A arquitetura aqui usado para o SharePoint, Lync e Exchange não sugere uma maneira preferencial de implementar essas plataformas. Ele fornece um exemplo meramente conforme topologias diferem com base nos requisitos de rede exclusivo e considerações de segurança. 
  
#### <a name="gateway-router"></a>Roteador de gateway

Essa topologia, o roteador de gateway estiver disposta da borda da rede e roteia todo o tráfego de entrada e saído para e da intranet. Como alternativa, também pode haver outros componentes que fechar a lacuna entre o roteador de gateway e o balanceador de carga mostrado, como várias camadas de firewalls. Essa topologia representa apenas uma maneira de implantar sua rede entre vários. Nesta configuração, o gateway é configurado com listas de controle de acesso (ACLs) para permitir muito entrada e saída com base em IP tráfego específico nas interfaces do roteador. ACLs, inspeção avançada ou conversão de endereço de rede (NAT) também pode ser executada em outros dispositivos, como firewalls, em toda a sua rede. 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>Dispositivos de proxy reverso e o balanceador de carga

Você pode usar soluções de balanceamento de carga de hardware ou software para redirecionar o tráfego para segmentos, incluindo servidores web front-end do SharePoint e servidores de acesso para cliente do Exchange (classes). Em alguns casos, é melhor usar um balanceador de carga baseado no hardware de camada 7 para requisitos de persistência conforme ele pode executar melhor usando informações na solicitação, cookies ou cabeçalhos. No entanto, a fatores como custo e aumento da utilização e carga de trabalho de tal solução não pode ser desejável para suas necessidades específicas. Considere os seguintes pontos balanceamento de carga em SharePoint, Exchange e Lync: 
  
- SharePoint - para o SharePoint 2013, você não precisará habilitar afinidade para os servidores web front-end. Normalmente, isso seria usado para criar sessões auto-adesivas e evitar a várias solicitações de autenticação de clientes para cada servidor web front-end. O novo serviço de Cache distribuído no SharePoint 2013 armazena e distribui tokens de logon entre os servidores web do farm do SharePoint. 
    
- Exchange - In Exchange 2013, a função CAS foi projetado para usar o balanceamento de carga de camada 4, distribuir solicitações na camada de transporte. Isso pode diminuir significativamente a utilização do balanceador de carga e a carga de trabalho. 
    
- Lync - balanceamento de carga de sistema de nome de domínio (DNS) é recomendada para tráfego de protocolo de iniciação de sessão (SIP) para os pools do Lync. (HLB) de balanceamento de carga de hardware é necessária para o tráfego da Web do Lync (HTTPS). 
    
### <a name="remote-access-options"></a>Opções de acesso remoto

Há várias opções que podem publicar recursos da intranet para parceiros na Internet ou fornecer acesso remoto seguro para funcionários remotos ou móveis. Esses exemplos incluem proxies reversos, DirectAccess e gateways VPN de terceiros. As soluções de acesso remoto discutidas posteriormente nesta seção são possibilidades para SharePoint, Exchange e o Lync, ou qualquer combinação desses servidores em uma implantação no local. No entanto, algumas opções remotas podem não funcionar com uma solução específica. 
  
Proxy reverso - um proxy reverso oferece suporte à criptografia de tráfego, como o Secure Sockets Layer (SSL) e com ele, para que você pode publicar aplicativos de intranet e os recursos da web autenticados usuários e parceiros na Internet. Um exemplo é o Microsoft Forefront Unified Access Gateway (UAG). Muitos balanceadores de carga de hardware também suportam a funcionalidade de proxy reverso. No entanto, há ainda válidos cenários para uso de uma solução de autônomo com base em suas necessidades e requisitos, como isolamento de tráfego, compartimentalização de segurança e a otimização do desempenho. 
  
Benefícios de proxy reverso e considerações: 
  
- Fornece acesso autenticado e protegido para parceiros ou usuários que acessam recursos da intranet (usa SSL (TCP 443) entre o cliente e o servidor proxy reverso). 
    
- Para o Exchange, uma vantagem do uso de um proxy reverso como o Forefront UAG é pré-autenticação antes de acessar o servidor acesso para cliente do Exchange. Os usuários de acesso remoto que usam aplicativos publicados, como o Outlook Web Access (OWA) pode autenticar com o básico, NTLM ou Kerberos métodos antes que eles cheguem a rede interna. 
    
- Para o Exchange e SharePoint, soluções, como o Forefront UAG podem encerrar conexões SSL e diminuir a carga do servidor de recursos de intranet fornecendo um único ponto de gerenciamento de certificados. 
    
- Para o Lync, o tráfego de Web (HTTPS) passa pelo proxy reverso (TCP 443) para comunicação do cliente. Os proxies de proxy reverso o HTTPS conexão a serviços Web do Lync, CAS do Exchange e Office Web Apps. Lync Server 2013 não suporta UAG. 
    
DirectAccess - uma tecnologia de acesso remoto que depende do protocolo IPSec (IPsec) para autenticação e para criptografar o tráfego entre o cliente DirectAccess e o servidor. DirectAccess fornece acesso simultâneo aos recursos de Internet e intranet para funcionários móveis e remotos, sem precisar iniciar uma conexão. 
  
DirectAccess pontos a considerar: 
  
- DirectAccess usa tráfego IPsec protegido (protocolo UDP 500 e 50 e 51) entre o cliente DirectAccess e o servidor. 
    
- DirectAccess para o Windows Server 2012 e Windows 8 não precisa de uma implantação da infraestrutura de chave pública (PKI) para autenticação de cliente e servidor. 
    
- Não é recomendável usar o DirectAccess com o Lync Server 2013 devido a problemas de latência de áudio e vídeo associados IPsec criptografia e descriptografia. 
    
    Gateway VPN - gateways VPN típica fornecem uma conexão de acesso remoto no qual um computador cliente de acesso remoto é logicamente projetado intranet através de uma conexão encapsulada e iniciadas pelo usuário. Você pode usar a Unificação de acesso remoto no Windows Server 2012 ou várias soluções de terceiros para fornecer acesso seguro à intranet para funcionários móveis ou remotos. VPN não é recomendado para o Lync. O tráfego remoto do Lync deve usar os servidores de borda e dividida encapsulamento. 
    
### <a name="domain-name-system-dns-considerations"></a>Considerações de nome DNS (sistema) do domínio

Você precisa planejar para o conjunto de registros DNS que permitem que os usuários de Internet e intranet resolver nomes DNS para os endereços IP apropriados. 
  
- Para parceiros baseado na Internet e os funcionários móveis ou remotos, registros DNS registrados com servidores DNS da Internet fornecem resolução ao conjunto de endereços IP públicos, correspondente para o roteador de gateway, o servidor de borda do Lync, o conjunto de endereços IP virtuais (VIPs) em o balanceador de carga e o gateway DirectAccess ou VPN, conforme necessário. 
    
- Para usuários baseados na intranet, registros DNS registrados com servidores DNS da intranet fornecem resolução ao conjunto de endereços IP virtuais (VIPs) no balanceador de carga para acessar recursos do SharePoint, Lync e Exchange. 
    
- Os clientes DirectAccess usam servidores DNS da intranet para nomes correspondente para o espaço para nome DNS da intranet e os servidores DNS da Internet para nomes que não. Para simplificar a operação do DirectAccess, considere o uso de uma implementação de DNS dividido que usa diferentes namespaces DNS para nomes baseado na Internet e intranet. Por exemplo, use contoso.com para o namespace de Internet e corp.contoso.com para o namespace da intranet. 
    
- O Exchange usa um modelo DNS dividido onde o host de resolução de IP difere no tráfego roteado publicamente do que na rede corporativa. No mínimo, você precisa ter um registro MX para emails de entrada e registros DNS para o OWA, descoberta automática, ActiveSync URLs para o tráfego do cliente. 
    
- Se você estiver usando o Exchange Online Protection (EOP), o seu registro MX aponta para esse serviço em vez de seu farm do Exchange. 
    
- Para o Exchange, você precisa de uma prova de propriedade registro TXT em seu DNS público e uma ID da organização de federação para configurar o compartilhamento federado. 
    
- Clientes de VPN de acesso remoto podem ser configurados para usar apenas os servidores DNS da intranet quando a conexão VPN de acesso remoto está ativo. 
    
### <a name="diagram-description"></a>Descrição do diagrama

Este diagrama fornece uma topologia de rede de exemplo que ilustram o tráfego de entrada e saído por meio de um roteador de gateway e o balanceamento de carga de sessão tráfego do cliente (interno e externo) para as camadas de servidor do SharePoint, Exchange e Lync apropriados. A descrição deste diagrama é dividida em duas partes: 
  
- Descrição dos componentes mostrados no diagrama 
    
- Descrição de como o tráfego é movido por todos os componentes para as camadas de servidor do SharePoint, Exchange, Lync e Office Web Apps. 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>Descrição dos componentes mostrados no diagrama

#### <a name="user-types"></a>Tipos de usuário

Há quatro tipos diferentes de usuários, três fora os serviços de rede e em nuvem e outro interna, que incluem: 
  
- Empresas parceiras (business-to-business)-externo 
    
- Parceiros individuais (SharePoint e anônimo (Lync))-externo 
    
- Externo funcionários móvel e remoto 
    
- Funcionários internos 
    
#### <a name="cloud-based-email-traffic"></a>Tráfego de email baseada em nuvem

Não há um componente baseado em nuvem para o tráfego de email baseados em SMTP, Hosts de email da Internet ou Exchange Online Protection. 
  
#### <a name="authentication-for-external-access"></a>Autenticação para acesso externo

Há um conjunto específico de procedimentos de autenticação para o Lync, SharePoint e Exchange para cada um dos tipos de usuário. Eles são descritos em mais detalhes posteriormente neste documento. 
  
#### <a name="gateway-router-with-acls"></a>Roteador de gateway com ACLs

O roteador de gateway fica na borda da rede e encaminha o todo o tráfego de entrada e saído para e da intranet. 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Servidores de acesso remoto do Lync e SharePoint

Essa topologia inclui um servidor de borda do Lync e um gateway de SharePoint VPN ou servidor DirectAccess. 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>Balanceador de carga e o dispositivo de proxy reverso

Você pode usar soluções de balanceamento de carga de hardware ou software para redirecionar o tráfego para segmentos, incluindo servidores web front-end do SharePoint e servidores de acesso para cliente do Exchange (classes). Essa topologia mostra componentes Lync VIP, VIP do SharePoint e Exchange VIP no balanceador de carga. 
  
#### <a name="servers"></a>Servidores

Há quatro servidores: Office Web Apps Server, SharePoint, Exchange e Lync. Cada servidor pode ter três camadas: um front-end, o nível de acesso para cliente, uma camada de aplicativo e uma camada de armazenamento/banco de dados.
  
#### <a name="front-end-client-access-tier"></a>Front-end, camada de acesso para cliente

Essa camada tem componentes em todos os quatro servidores: 
  
- Pool do Lync (front-end). O diagrama mostra os dois bancos de dados do Lync. 
    
- Front-end do SharePoint e o cache distribuído. O diagrama mostra três bancos de dados do SharePoint. 
    
- CAS do Exchange. O diagrama mostra os dois bancos de dados do Exchange. 
    
- Office Web Apps Server. O diagrama mostra os dois bancos de dados do Office Web Apps. 
    
#### <a name="application-tier"></a>Camada de aplicativo

Essa camada tem componentes somente no servidor do SharePoint: 
  
- Pesquisa (consulta, index, admin). O diagrama mostra três bancos de dados do SharePoint. 
    
- Processamento em lotes. O diagrama mostra três bancos de dados do SharePoint. 
    
#### <a name="databasestorage-tier"></a>Camada de armazenamento/banco de dados

Essa camada tem componentes nos servidores do SharePoint, Lync e Exchange: 
  
- Banco de dados do Lync (back-end). O diagrama mostra três bancos de dados do Lync. 
    
- Banco de dados do SharePoint. O diagrama mostra três bancos de dados do SharePoint. 
    
- Servidor de caixa de correio do Exchange. O diagrama mostra dois servidores de caixa de correio do Exchange. 
    
Para obter mais informações sobre componentes instalados em cada uma das funções de servidor do SharePoint, consulte [Topologias otimizadas do SharePoint 2013](https://aka.ms/Ma5cgk). 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>Descrição de como o tráfego é movido por todos os componentes para as camadas de servidor diferente

Esta seção descreve como as solicitações de usuário para percorrer a topologia de rede. 
  
#### <a name="authentication-and-routing-for-external-access"></a>Autenticação e o roteamento para acesso externo

Há três tipos diferentes de clientes fora do serviços de rede e em nuvem, que incluem: 
  
- Empresas parceiras (business-to-business)-externo 
    
- Parceiros individuais (SharePoint e anônimo (Lync))-externo 
    
- Externo funcionários móvel e remoto 
    
A autenticação e o processo de roteamento para cada tipo de usuário externo é descrito individualmente. 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>Empresas parceiras (business-to-business) (https://partnerweb.contoso.com)

- Lync: a confiança de federação com outras organizações, Skype e conectividade de IM pública (PIC) com o AOL. O tráfego de Federação do Lync passa pelo roteador gateway para o servidor de borda do Lync, como o VIP do Lync (servidor de proxy / reverso do balanceador de carga) e, em seguida, o Lync Server. 
    
- SharePoint: Confiáveis provedor de identidade de parceiro com autenticação SAML. O tráfego de cliente do SharePoint passa pelo roteador Gateway para o VIP do SharePoint (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o SharePoint Server. 
    
- Exchange: TLS Auth mútuo para tráfego de email, a autenticação SAML para Federated Sharing. O tráfego do cliente Exchange passa pelo roteador Gateway para o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) e depois para o Exchange Server. 
    
- O tráfego de SMTP passa por meio do roteador de Gateway e o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) para o Exchange server. 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>Parceiros individuais (SharePoint) e anônimo (Lync) (https://partnerweb.contoso.com e https://meet.contoso.com)

- Lync: usuários anônimos só podem ingressar em reuniões do Lync organizados pelos funcionários. O tráfego de Federação do Lync passa pelo roteador Gateway para o servidor de borda do Lync, como o VIP do Lync (servidor de proxy / reverso do balanceador de carga) e, em seguida, o Lync Server. 
    
- Do SharePoint: Provedor de identidade parceiro confiável com autenticação SAML ou a autenticação baseada em formulários. O tráfego de cliente do SharePoint passa pelo roteador Gateway para o VIP do SharePoint (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o SharePoint Server. 
    
- Exchange: Não se aplica. 
    
- Tráfego da Web do Lync passa pelo roteador Gateway para o servidor de borda do Lync, como o VIP do Lync (servidor de proxy / reverso do balanceador de carga,) para um balanceador de carga de hardware, que é necessário para tráfego HTTPS, e depois para o Lync Server. 
    
#### <a name="roaming-and-remote-employees"></a>Funcionários móveis e remotos

1. https://intranet.contoso.com 
    
2. https://Teams.contoso.com 
    
3. https://My.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com * 
    
6. https://dial.contoso.com *
    
7. https://meet.contoso.com *
    
* A URL do Exchange tem os seguintes diretórios virtuais: descoberta automática, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell 
  
- Lync: Autenticação TLS-DSK ou NTLM. O tráfego do cliente Lync passa pelo roteador Gateway para o servidor de borda do Lync, como o VIP do Lync (servidor de proxy / reverso do balanceador de carga) e, em seguida, o Lync Server. 
    
- SharePoint: Os serviços de domínio Active Directory (AD DS), a autenticação baseada em formulários ou autenticação SAML. O tráfego de cliente do SharePoint passa pelo gateway VPN ou o servidor DirectAccess para o VIP do SharePoint (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o SharePoint server. 
    
- Exchange: A autenticação básica sobre SSL (ActiveSync, descoberta automática), a autenticação baseada em formulários (OWA). O tráfego do cliente Exchange passa pelo roteador Gateway para o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) e depois para o Exchange Server. 
    
- O tráfego de cliente do Lync passa pelo roteador Gateway para o VIP Lync (servidor de proxy / reverso do balanceador de carga) para um balanceador de carga de hardware, que é necessário para tráfego HTTPS, e depois para o Lync Server. 
    
#### <a name="authentication-for-internal-access"></a>Autenticação para acesso interno

#### <a name="internal-employees"></a>Funcionários internos

> https://intranet.contoso.com 
    
> https://Teams.contoso.com 
    
> https://My.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com * 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://Admin.contoso.com
    
- Lync: Autenticação Kerberos, NTLM ou DSK de TLS. O tráfego do cliente Lync vai para o VIP do Lync (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o Lync Server. 
    
- SharePoint: Os serviços de domínio Active Directory (AD DS), a autenticação baseada em formulários ou autenticação SAML. O tráfego de cliente do SharePoint vai para o VIP do SharePoint (servidor de proxy / reverso do balanceador de carga) e, em seguida, para o SharePoint Server. 
    
- Exchange: AD DS, a autenticação baseada em formulários. O tráfego do cliente Exchange vai para o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) e depois para o Exchange Server. 
    
- O tráfego de cliente do Lync vai para o VIP do Lync (servidor de proxy / reverso do balanceador de carga) para um balanceador de carga de hardware, que é necessário para tráfego HTTPS, e depois para o Lync Server. 
    
#### <a name="cloud-based-email-traffic"></a>Tráfego de email baseada em nuvem

O componente baseado em nuvem para o tráfego de email baseados em SMTP consiste em Hosts de email da Internet ou Exchange Online Protection.
  
Esses componentes movem o tráfego de email através da rede usando o SMTP. O tráfego passa pelo roteador Gateway para o VIP do Exchange (servidor de proxy / reverso do balanceador de carga) e depois para o Exchange Server. 
  
### <a name="network-traffic-legend"></a>Legenda de tráfego de rede

Na caixa legenda graficamente mostra os diferentes tipos de tráfego ilustrado no gráfico nas linhas coloridos diferentes da seguinte maneira: 
  
- Verde linha: Lync SIP tráfego 
    
- Azul linha: tráfego da Web do Lync 
    
- Roxo linha: o tráfego de cliente do SharePoint 
    
- Linha laranja: tráfego do cliente do Exchange 
    
- Linha de cinza: tráfego do servidor de email do Exchange entre o Exchange local e o Exchange Online Protection. 
    
Os diferentes tipos de tráfego e as portas que eles usam também são descritos na caixa legenda. 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Tráfego SIP do Lync e o tráfego de web do Lync

O servidor de borda do Lync usa as seguintes portas para comunicação de usuário externo: 
  
- Tráfego de sinalização/IM (SIP/simples): porta TCP 443 (abertas para tráfego de entrada) 
    
- Tráfego de webconferência (PSOM) da Web: TCP 443 (aberta para o tráfego de entrada) 
    
- A / V (SRTP) do tráfego: TCP 443, UDP 3478 e TCP 50000-59999 (opcional) (aberta para o tráfego de entrada e saída) 
    
Servidor de borda do Lync usa as seguintes portas para comunicação de Federação: 
  
- Portas TCP 5061 (SIP), 5269 (XMPP), 443 e UDP 3478 (SRTP) (aberta para o tráfego de entrada e saída) 
    
#### <a name="sharepoint-client-traffic"></a>Tráfego de cliente do SharePoint

SharePoint pode usar a porta TCP 443 (SSL) para comunicação criptografada entre o cliente e o balanceador de carga. Para obter acesso externo da Internet, essa porta precisa ser aberto para o tráfego de entrada e saído no roteador de gateway (ou firewall externo). 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Tráfego de cliente do Exchange e o tráfego do servidor de email do Exchange

Para comunicações de servidor-para-servidor, o Exchange usa a porta TCP 25 (SMTP). A maioria dos tráfego de cliente (OWA, ActiveSync, descoberta automática, Outlook Anywhere) é tratado na porta 443 (HTTPS). Se você tiver clientes POP ou IMAP, portas 110 (POP3), 995 (criptografadas POP3), 143 (IMAP4), 993 (criptografadas IMAP4) e 587 (SMTP) também são usadas para oferecer suporte a esses clientes. 
  
#### <a name="more-on-lync-network-traffic"></a>Mais tráfego diante de rede do Lync?

Saiba como o Lync Server pode ajudar sua organização a fornecer mensagens instantâneas, Webconferência, compartilhamento de aplicativos e comunicação por voz. Para obter mais informações, consulte o [Cartaz de cargas de trabalho de protocolo do Microsoft Lync Server 2013](https://aka.ms/G5jzjo). 
  
O cartaz também inclui um código QR para acessar essa informação. 
  

