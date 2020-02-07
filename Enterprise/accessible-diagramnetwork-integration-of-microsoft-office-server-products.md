---
title: Diagrama acessível-integração de rede de produtos do Microsoft Office Server
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
f1.keywords:
- NOCSH
description: Este artigo é uma versão de texto acessível do diagrama chamado integração de rede dos produtos do Microsoft Office Server.
ms.openlocfilehash: def94a4523ad78676d6a9532a60dcba78032f23b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843862"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>Diagrama acessível-integração de rede de produtos do Microsoft Office Server

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado integração de rede dos produtos do Microsoft Office Server.
  
Este cartaz fornece uma ilustração geral de um ambiente de rede que inclui o Lync Server 2013, o SharePoint 2013 e o Exchange Server 2013. Ele também ilustra os seguintes elementos de rede que são comuns em todos os produtos: acesso remoto e interno, autenticação, tráfego de cliente e tráfego de roteamento por meio de dispositivos compartilhados. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Conceitos de alto nível para Lync, Exchange, SharePoint Server e Office Web Apps

### <a name="about-the-design"></a>Sobre o design

#### <a name="streamlined-network-design"></a>Design de rede simplificado

Esta topologia ilustra uma implantação de rede local do SharePoint 2013, do Exchange Server 2013 e do Lync Server 2013. Ele também mostra o uso do serviço baseado em nuvem da Microsoft, o Exchange Online Protection, que fornece proteção contra spam e malware para tráfego SMTP de entrada da Internet. 
  
Esse design de rede é simplificado para um conjunto mínimo de recursos de rede. O design não leva em conta os recursos de segurança ou de infraestrutura adicionais que algumas organizações podem exigir. 
  
Este diagrama: 
  
- Fornece um exemplo de topologia de rede que ilustra o tráfego de entrada e saída por meio de um roteador de gateway e balanceamento de carga do tráfego de sessão de cliente (externo e interno) para as camadas apropriadas do SharePoint, do Exchange e do Lync Server. 
    
- Mostra o uso de servidores de acesso remoto opcionais, como um gateway VPN de terceiros ou servidor DirectAccess, para fornecer comunicação segura para funcionários móveis ou remotos. 
    
- Detalha o fluxo de tráfego do SharePoint, do Exchange e do Lync do cliente para cada camada de servidor de plataforma. 
    
- Identifica o tipo de conexão de acesso remoto ou interno com base no cliente (como parceiro ou funcionário) e o método de autenticação usado. 
    
- Divide as plataformas do SharePoint, do Exchange e do Lync por funções de servidor necessárias, identificando o front-end, o aplicativo, o banco de dados e outros níveis. 
    
A arquitetura usada aqui para SharePoint, Lync e Exchange não sugere uma forma preferida de implementar essas plataformas. Ele simplesmente fornece um exemplo de topologias diferentes com base em requisitos de rede exclusivos e considerações de segurança. 
  
#### <a name="gateway-router"></a>Roteador de gateway

Para essa topologia, o roteador de gateway fica na borda da rede e roteia todo o tráfego de entrada e saída para e da intranet. Como alternativa, também pode haver outros componentes que desligam a lacuna entre o roteador de gateway e o balanceador de carga mostrado, como várias camadas de firewalls. Essa topologia representa apenas uma maneira de implantar sua rede de várias. Nessa configuração, o gateway é configurado com ACLs (listas de controle de acesso) para permitir tráfego muito específico de entrada e saída baseado em IP nas interfaces do roteador. ACLs, inspeção avançada ou NAT (conversão de endereço de rede) também podem ser realizadas em outros dispositivos, como firewalls, por toda a rede. 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>Balanceador de carga e dispositivos de proxy reverso

Você pode usar soluções de balanceamento de carga de software ou hardware para redirecionar o tráfego de segmentos, incluindo servidores Web front-end do SharePoint e servidores de acesso para cliente do Exchange (CASs). Em alguns casos, é ideal usar um balanceador de carga baseado em hardware de camada 7 para obter os requisitos de persistência, pois ele pode funcionar melhor usando informações na solicitação, como cookies ou cabeçalhos. No entanto, fatores como custo e maior utilização e carga de trabalho de tal solução podem não ser desejáveis para suas necessidades específicas. Considere os seguintes pontos para balanceamento de carga no SharePoint, no Exchange e no Lync: 
  
- SharePoint – para o SharePoint 2013, não é necessário habilitar a afinidade para seus servidores Web front-end. Normalmente, isso seria usado para criar sessões adesivas e evitar várias solicitações de autenticação de clientes para cada servidor Web front-end. O novo serviço de cache distribuído no SharePoint 2013 armazena e distribui tokens de logon nos servidores Web do farm do SharePoint. 
    
- Exchange-no Exchange 2013, a função CAS é projetada para usar o balanceamento de carga de camada 4, distribuindo solicitações na camada de transporte. Isso pode diminuir significativamente a utilização e a carga de um balanceador de carga. 
    
- Lync-o balanceamento de carga do DNS (sistema de nomes de domínio) é recomendado para o tráfego do protocolo SIP para pools do Lync. O balanceamento de carga de hardware (HLB) é necessário para o tráfego do Lync Web (HTTPS). 
    
### <a name="remote-access-options"></a>Opções de acesso remoto

Há várias opções que podem publicar recursos de intranet para parceiros na Internet ou fornecer acesso remoto seguro para funcionários remotos ou móveis. Esses exemplos incluem proxies reversos, DirectAccess e gateways VPN de terceiros. As soluções de acesso remoto discutidas mais adiante nesta seção são possibilidades para o SharePoint, Lync e Exchange, ou qualquer combinação desses servidores em uma implantação local. No entanto, algumas opções remotas podem não funcionar com uma solução específica. 
  
Proxy reverso-um proxy reverso oferece suporte à criptografia de tráfego, como SSL (Secure Sockets Layer) e com ele você pode publicar aplicativos de intranet e recursos da Web para usuários e parceiros autenticados na Internet. Um exemplo é o Microsoft Forefront Unified Access Gateway (UAG). Muitos balanceadores de carga de hardware também oferecem suporte à funcionalidade de proxy reverso. No entanto, ainda há cenários válidos para usar uma solução autônoma com base em suas necessidades e requisitos, como isolamento de tráfego, compartimentalização de segurança e otimização de desempenho. 
  
Considerações e benefícios do proxy reverso: 
  
- Fornece acesso autenticado e protegido para parceiros ou usuários que acessam recursos de intranet (usa SSL (TCP 443) entre o cliente e o servidor de proxy reverso). 
    
- Para o Exchange, um benefício de usar um proxy reverso como o Forefront UAG é a pré-autenticação antes de acessar o servidor de acesso para cliente do Exchange. Os usuários de acesso remoto que usam aplicativos publicados como o Outlook Web Access (OWA) podem autenticar com os métodos Basic, NTLM ou Kerberos antes que eles cheguem à rede interna. 
    
- Para o Exchange e o SharePoint, soluções como o Forefront UAG podem encerrar conexões SSL e diminuir a carga do servidor de recursos de intranet enquanto fornecem um único ponto de gerenciamento para certificados. 
    
- Para o tráfego do Lync, Web (HTTPS) passa pelo proxy reverso (TCP 443) para comunicação de cliente. Os proxies de proxy reverso da conexão HTTPS para os serviços Web do Lync, Exchange CAS e Office Web Apps. O Lync Server 2013 não dá suporte a UAG. 
    
DirectAccess-uma tecnologia de acesso remoto que se baseia no protocolo IPsec (Internet Protocol Security) para autenticação e criptografia de tráfego entre o cliente e o servidor do DirectAccess. O DirectAccess fornece acesso simultâneo à Internet e recursos de intranet para funcionários móveis e remotos sem ter que iniciar uma conexão. 
  
Pontos do DirectAccess a considerar: 
  
- O DirectAccess usa o tráfego protegido IPsec (protocolo 50 e 51 e UDP 500) entre o cliente e o servidor do DirectAccess. 
    
- O DirectAccess para Windows Server 2012 e Windows 8 não precisa de uma implantação de infraestrutura de chave pública (PKI) para autenticação de servidor e cliente. 
    
- Recomendamos o uso do DirectAccess com o Lync Server 2013 devido a problemas de latência de áudio e vídeo associados à criptografia e descriptografia IPsec. 
    
    Gateway VPN-gateways VPN típicos fornecem uma conexão de acesso remoto na qual um computador cliente de acesso remoto é projetado logicamente para a intranet por meio de uma conexão encapsulada e iniciada pelo usuário. Você pode usar o acesso remoto unificado no Windows Server 2012 ou várias soluções de terceiros para fornecer acesso seguro à intranet para funcionários móveis ou remotos. A VPN não é recomendada para o Lync. O tráfego do Lync remoto deve usar os servidores de borda e o túnel de divisão. 
    
### <a name="domain-name-system-dns-considerations"></a>Considerações sobre DNS (sistema de nomes de domínio)

Você precisa planejar o conjunto de registros DNS que permitem que os usuários de Internet e intranet resolvam nomes DNS para os endereços IP apropriados. 
  
- Para parceiros baseados na Internet e para funcionários remotos ou móveis, os registros DNS registrados com servidores DNS da Internet fornecem resolução para o conjunto de endereços IP públicos correspondentes ao roteador de gateway, o servidor de borda do Lync, o conjunto de endereços IP virtuais (VIPs) no o balanceador de carga e o DirectAccess ou o gateway VPN, conforme o necessário. 
    
- Para usuários baseados na intranet, os registros DNS registrados em servidores DNS da intranet fornecem resolução para o conjunto de VIPs (endereços IP virtuais) no balanceador de carga para acesso aos recursos do SharePoint, Lync e Exchange. 
    
- Os clientes do DirectAccess usam servidores DNS da intranet para nomes que correspondem ao espaço de nome DNS da intranet e servidores DNS da Internet para nomes que não. Para simplificar a operação do DirectAccess, considere o uso de uma implementação de DNS dividido que usa namespaces DNS diferentes para nomes baseados na intranet e na Internet. Por exemplo, use contoso.com para namespace da Internet e corp.contoso.com para o namespace da intranet. 
    
- O Exchange usa um modelo de DNS dividido em que a resolução de host para IP difere no tráfego roteado publicamente do na rede corporativa. No mínimo, você precisa ter registros DNS para OWA, descoberta automática, URLs do ActiveSync para tráfego do cliente e um registro MX para email de entrada. 
    
- Se você estiver usando o Exchange Online Protection (EOP), seu registro MX apontará para esse serviço em vez do farm do Exchange. 
    
- Para o Exchange, você precisa de um registro TXT de verificação de propriedade no seu DNS público e uma ID da organização de Federação para configurar o compartilhamento federado. 
    
- Os clientes VPN de acesso remoto podem ser configurados para usar apenas os servidores DNS da intranet quando a conexão VPN de acesso remoto estiver ativa. 
    
### <a name="diagram-description"></a>Descrição do diagrama

Este diagrama fornece um exemplo de topologia de rede que ilustra o tráfego de entrada e saída por meio de um roteador de gateway e balanceamento de carga do tráfego de sessão de cliente (externo e interno) para as camadas apropriadas do SharePoint, do Exchange e do Lync Server. A descrição deste diagrama é dividida em duas partes: 
  
- Descrição dos componentes mostrados no diagrama 
    
- Descrição de como o tráfego se move pelos componentes para as camadas do servidor do SharePoint, do Exchange, do Lync e do Office Web Apps. 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>Descrição dos componentes mostrados no diagrama

#### <a name="user-types"></a>Tipos de usuários

Há quatro tipos diferentes de usuários, três fora dos serviços de rede e nuvem e um interno, que incluem: 
  
- Empresas parceiras (Business-to-Business)-externa 
    
- Parceiros individuais (SharePoint e anônimo (Lync))-externo 
    
- Funcionários remotos e móveis-externos 
    
- Funcionários internos 
    
#### <a name="cloud-based-email-traffic"></a>Tráfego de email baseado na nuvem

Há um componente baseado em nuvem para tráfego de email baseado em SMTP, hosts de email da Internet ou proteção do Exchange Online. 
  
#### <a name="authentication-for-external-access"></a>Autenticação para acesso externo

Há um conjunto específico de procedimentos de autenticação para Lync, SharePoint e Exchange para cada um dos tipos de usuário. Eles são descritos mais detalhadamente mais adiante neste documento. 
  
#### <a name="gateway-router-with-acls"></a>Roteador de gateway com ACLs

O roteador de gateway fica na borda da rede e roteia todo o tráfego de entrada e saída para e da intranet. 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Servidores de acesso remoto para Lync e SharePoint

Essa topologia inclui um servidor de borda do Lync e um gateway VPN do SharePoint ou um servidor DirectAccess. 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>Balanceador de carga e dispositivo de proxy reverso

Você pode usar soluções de balanceamento de carga de software ou hardware para redirecionar o tráfego de segmentos, incluindo servidores Web front-end do SharePoint e servidores de acesso para cliente do Exchange (CASs). Essa topologia mostra os componentes do Lync VIP, do SharePoint VIP e do Exchange VIP no balanceador de carga. 
  
#### <a name="servers"></a>Servidores

Há quatro servidores: Lync, SharePoint, Exchange e Office Web Apps Server. Cada servidor pode ter três camadas: um front-end, uma camada de acesso para cliente, uma camada de aplicativo e uma camada de banco de dados/armazenamento.
  
#### <a name="front-end-client-access-tier"></a>Front-end, camada de acesso para cliente

Esta camada tem componentes em todos os quatro servidores: 
  
- Pool do Lync (front-end). O diagrama mostra dois bancos de dados do Lync. 
    
- Front-end do SharePoint e cache distribuído. O diagrama mostra três bancos de dados do SharePoint. 
    
- CAS do Exchange. O diagrama mostra dois bancos de dados do Exchange. 
    
- Servidor do Office Web Apps. O diagrama mostra dois bancos de dados do Office Web Apps. 
    
#### <a name="application-tier"></a>Camada de aplicativo

Esta camada tem componentes somente no servidor do SharePoint: 
  
- Pesquisa (consulta, índice, administrador). O diagrama mostra três bancos de dados do SharePoint. 
    
- Processamento em lotes. O diagrama mostra três bancos de dados do SharePoint. 
    
#### <a name="databasestorage-tier"></a>Banco de dados/camada de armazenamento

Esta camada tem componentes nos servidores Lync, SharePoint e Exchange: 
  
- Banco de dados do Lync (backend). O diagrama mostra três bancos de dados do Lync. 
    
- Banco de dados do SharePoint. O diagrama mostra três bancos de dados do SharePoint. 
    
- Servidor de caixa de correio do Exchange. O diagrama mostra dois servidores de caixa de correio do Exchange. 
    
Para obter mais informações sobre os componentes instalados em cada uma das funções do SharePoint Server, consulte [topologias otimizadas para o SharePoint 2013](https://aka.ms/Ma5cgk). 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>Descrição de como o tráfego se move pelos componentes para diferentes níveis de servidor

Esta seção descreve como as solicitações de usuário são movidas pela topologia de rede. 
  
#### <a name="authentication-and-routing-for-external-access"></a>Autenticação e roteamento para acesso externo

Há três tipos diferentes de clientes fora da rede e dos serviços de nuvem, que incluem: 
  
- Empresas parceiras (Business-to-Business)-externa 
    
- Parceiros individuais (SharePoint e anônimo (Lync))-externo 
    
- Funcionários remotos e móveis-externos 
    
O processo de autenticação e roteamento para cada tipo de usuário externo é descrito individualmente. 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>Empresas parceiras (Business-to-Business) (https://partnerweb.contoso.com)

- Lync: confiança de Federação com outras organizações, Skype e conectividade pública de IM (PIC) com AOL. O tráfego de Federação do Lync passa pelo roteador de gateway para o servidor de borda do Lync, para o VIP do Lync (balanceador de carga/servidor de proxy reverso) e, em seguida, para o Lync Server. 
    
- SharePoint: provedor de identidade de parceiro confiável com autenticação SAML. O tráfego do cliente do SharePoint passa pelo roteador de gateway para o VIP do SharePoint (balanceador de carga/servidor de proxy reverso) e, em seguida, para o SharePoint Server. 
    
- Exchange: TLS de autenticação mútua para tráfego de email, autenticação SAML para compartilhamento federado. O tráfego de cliente do Exchange passa pelo roteador de gateway para o VIP do Exchange (balanceador de carga/servidor de proxy reverso) e, em seguida, para o servidor Exchange. 
    
- O tráfego SMTP passa pelo roteador de gateway e por meio do VIP do Exchange (balanceador de carga/servidor de proxy reverso) para o Exchange Server. 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>Parceiros individuais (SharePoint) e anônimo (Lync) (https://partnerweb.contoso.com ehttps://meet.contoso.com)

- Lync: usuários anônimos podem apenas ingressar em reuniões do Lync organizadas por funcionários. O tráfego de Federação do Lync passa pelo roteador de gateway para o servidor de borda do Lync, para o VIP do Lync (balanceador de carga/servidor de proxy reverso) e, em seguida, para o Lync Server. 
    
- SharePoint: provedor de identidade de parceiro confiável com autenticação SAML ou autenticação baseada em formulários. O tráfego do cliente do SharePoint passa pelo roteador de gateway para o VIP do SharePoint (balanceador de carga/servidor de proxy reverso) e, em seguida, para o SharePoint Server. 
    
- Exchange: não se aplica. 
    
- O tráfego da Web do Lync passa pelo roteador de gateway para o servidor de borda do Lync, para o VIP do Lync (balanceador de carga/servidor de proxy reverso) para um balanceador de carga de hardware, que é necessário para o tráfego HTTPS e, em seguida, para o Lync Server. 
    
#### <a name="roaming-and-remote-employees"></a>Funcionários remotos e móveis

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* A URL do Exchange tem os seguintes diretórios virtuais: descoberta automática, ECP, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell 
  
- Lync: TLS-DSK ou autenticação NTLM. O tráfego de cliente do Lync passa pelo roteador de gateway para o servidor de borda do Lync, para o VIP do Lync (balanceador de carga/servidor de proxy reverso) e, em seguida, para o Lync Server. 
    
- SharePoint: AD DS (serviços de domínio Active Directory), autenticação baseada em formulários ou autenticação SAML. O tráfego do cliente do SharePoint passa pelo gateway VPN ou pelo servidor DirectAccess para o VIP do SharePoint (balanceador de carga/servidor de proxy reverso) e, em seguida, para o SharePoint Server. 
    
- Exchange: autenticação básica sobre SSL (ActiveSync, descoberta automática), autenticação baseada em formulários (OWA). O tráfego de cliente do Exchange passa pelo roteador de gateway para o VIP do Exchange (balanceador de carga/servidor de proxy reverso) e, em seguida, para o servidor Exchange. 
    
- O tráfego de cliente do Lync passa pelo roteador de gateway para o servidor VIP do Lync (balanceador de carga/servidor de proxy reverso) para um balanceador de carga de hardware, que é necessário para o tráfego HTTPS e, em seguida, para o Lync Server. 
    
#### <a name="authentication-for-internal-access"></a>Autenticação para acesso interno

#### <a name="internal-employees"></a>Funcionários internos

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- Lync: Kerberos, TLS-DSK ou autenticação NTLM. O tráfego de cliente do Lync vai para o servidor VIP do Lync (balanceador de carga/servidor de proxy reverso) e, em seguida, para o Lync Server. 
    
- SharePoint: AD DS (serviços de domínio Active Directory), autenticação baseada em formulários ou autenticação SAML. O tráfego do cliente do SharePoint vai para o VIP do SharePoint (balanceador de carga/servidor de proxy reverso) e, em seguida, para o SharePoint Server. 
    
- Exchange: AD DS, autenticação baseada em formulários. O tráfego de cliente do Exchange vai para o VIP do Exchange (servidor de balanceador de carga/servidor de proxy reverso) e, em seguida, para o servidor do Exchange. 
    
- O tráfego de cliente do Lync vai para o VIP do Lync (balanceador de carga/servidor de proxy reverso) para um balanceador de carga de hardware, que é necessário para o tráfego HTTPS e, em seguida, para o Lync Server. 
    
#### <a name="cloud-based-email-traffic"></a>Tráfego de email baseado na nuvem

O componente baseado em nuvem para tráfego de email com base em SMTP consiste em hosts de email da Internet ou proteção do Exchange Online.
  
Esses componentes movem o tráfego de email pela rede usando SMTP. O tráfego passa pelo roteador de gateway para o VIP do Exchange (balanceador de carga/servidor de proxy reverso) e, em seguida, para o servidor do Exchange. 
  
### <a name="network-traffic-legend"></a>Legenda de tráfego de rede

A caixa de legenda mostra graficamente os diferentes tipos de tráfego descritos no gráfico em diferentes linhas coloridas da seguinte maneira: 
  
- Linha verde: tráfego SIP do Lync 
    
- Linha azul: tráfego da Web do Lync 
    
- Linha roxa: tráfego de cliente do SharePoint 
    
- Linha laranja: tráfego de cliente do Exchange 
    
- Linha cinza: tráfego de servidor de email do Exchange entre o Exchange local e o Exchange Online Protection. 
    
Os diferentes tipos de tráfego e as portas que eles usam também são descritos na caixa legenda. 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Tráfego SIP do Lync e tráfego da Web do Lync

O servidor de borda do Lync usa as seguintes portas para comunicação externa do usuário: 
  
- Tráfego de mensagens instantâneas/sinalização (SIP/simples): porta TCP 443 (aberta para tráfego de entrada) 
    
- Tráfego de Webconferência (PSOM): TCP 443 (abrir para tráfego de entrada) 
    
- Tráfego A/V (SRTP): TCP 443, UDP 3478 e TCP 50000-59999 (opcional) (abrir para tráfego de entrada e saída) 
    
O Lync Edge Server usa as seguintes portas para comunicação de Federação: 
  
- TCP portas 5061 (SIP), 5269 (XMPP), 443 e UDP 3478 (SRTP) (abrir para tráfego de entrada e saída) 
    
#### <a name="sharepoint-client-traffic"></a>Tráfego de cliente do SharePoint

O SharePoint pode usar a porta TCP 443 (SSL) para comunicação criptografada entre o cliente e o balanceador de carga. Para acesso externo a partir da Internet, esta porta precisa ser aberta para tráfego de entrada e saída no roteador do gateway (ou firewall externo). 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Tráfego de cliente do Exchange e de servidor de email do Exchange

O Exchange usa a porta TCP 25 (SMTP) para comunicações de servidor para servidor. A maior parte do tráfego de cliente (OWA, ActiveSync, autodiscover, Outlook Anywhere) é manipulada pela porta 443 (HTTPS). Se você tiver clientes POP ou IMAP, as portas 110 (POP3), 995 (POP3 criptografado), 143 (IMAP4), 993 (Encrypted IMAP4) e 587 (SMTP) também serão usados para dar suporte a esses clientes. 
  
#### <a name="more-on-lync-network-traffic"></a>Mais sobre o tráfego de rede do Lync?

Saiba como o Lync Server pode ajudar sua organização a fornecer mensagens instantâneas, webconferência, compartilhamento de aplicativos e comunicação de voz. Para obter mais informações, consulte [pôster de cargas de trabalho de protocolo do Microsoft Lync Server 2013](https://aka.ms/G5jzjo). 
  
O cartaz também inclui um código QR para acessar essas informações. 
  

