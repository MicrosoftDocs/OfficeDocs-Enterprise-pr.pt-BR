---
title: Gerenciar pontos de extremidade do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Algumas redes corporativas restringem o acesso a locais genéricos da Internet ou incluem backhaul substanciais ou processamento de tráfego de rede. Para garantir que os computadores em redes como esses possam acessar o Office 365, os administradores de rede e de proxy precisam gerenciar a lista de FQDNs, URLs e endereços IP que compõem a lista de pontos de extremidade do Office 365. Eles precisam ser adicionados a rotas diretas, bypass de proxy e/ou regras de firewall e arquivos de PAC para garantir que as solicitações de rede possam acessar o Office 365.
ms.openlocfilehash: 1a694d516a81fec7d6c619c17414e2245dd6b0ef
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2019
ms.locfileid: "38030605"
---
# <a name="managing-office-365-endpoints"></a>Gerenciar pontos de extremidade do Office 365

A maioria das organizações corporativas que têm vários locais do Office e uma WAN de conexão precisará precisar de configuração para a conectividade de rede do Office 365. Você pode otimizar sua rede enviando todas as solicitações de rede do Office 365 confiáveis diretamente através do firewall, ignorando a inspeção ou o processamento de qualquer nível de pacote adicional. Isso reduz a latência e seus requisitos de capacidade de perímetro. A identificação do tráfego de rede do Office 365 é a primeira etapa para fornecer o melhor desempenho para seus usuários. Para obter mais informações sobre a conectividade de rede do Office 365, consulte [office 365 princípios de conectividade de rede](office-365-network-connectivity-principles.md).

A Microsoft recomenda que você acesse os pontos de extremidade de rede do Office 365 e altere-os usando o [endereço IP 365 do Office e o serviço Web de URL](office-365-ip-web-service.md).

Independentemente de como você gerencia o tráfego de rede vital do Office 365, o Office 365 requer conectividade com a Internet. Outros pontos de extremidade de rede onde a conectividade é necessária são listados em [pontos de extremidade adicionais não incluídos no endereço IP do Office 365 e no serviço Web de URL](additional-office365-ip-addresses-and-urls.md).

O modo de uso dos pontos de extremidade de rede do Office 365 dependerá da arquitetura de rede da organização de sua empresa. Este artigo descreve várias maneiras pelas quais as arquiteturas de rede corporativas podem se integrar com os endereços IP e URLs do Office 365. A maneira mais fácil de escolher quais solicitações de rede confiar é usar dispositivos SDWAN que suportam a configuração automatizada do Office 365 em cada um dos seus locais do Office.

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN para saída de filial local de tráfego de rede vital do Office 365

Em cada local de filial, você pode fornecer um dispositivo SDWAN que esteja configurado para rotear o tráfego para o Office 365 otimizar categoria de pontos de extremidade, ou otimizar e permitir categorias, diretamente à rede da Microsoft. Outro tráfego de rede, incluindo o tráfego do datacenter local, tráfego geral de sites da Web da Internet e tráfego para os pontos de extremidade de categoria padrão do Office 365 é enviado para outro local onde você tem um perímetro de rede mais significativo.

A Microsoft está trabalhando com provedores do SDWAN para habilitar a configuração automatizada. Para obter mais informações, consulte [programa de parceria de rede do Office 365](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Usar um arquivo PAC para o roteamento direto de tráfego vital do Office 365

Use os arquivos PAC ou WPAD para gerenciar solicitações de rede associadas ao Office 365, mas que não têm um endereço IP. As solicitações de rede típicas enviadas por meio de um proxy ou dispositivo de perímetro aumentam a latência. Embora a interrupção e a inspeção do SSL criem a maior latência, outros serviços, como a autenticação de proxy e a pesquisa de reputação podem causar um desempenho ruim e uma experiência de usuário ruim. Além disso, esses dispositivos de rede de perímetro precisam de capacidade suficiente para processar todas as solicitações de conexão de rede. Recomendamos ignorar seus dispositivos de proxy ou de inspeção para solicitações de rede diretas do Office 365.
  
A [Galeria do PowerShell Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) é um script do PowerShell que lê os pontos de extremidade de rede mais recentes do endereço IP e URL do serviço Web do Office 365 e cria um arquivo de PAC de exemplo. Você pode modificar o script para que ele se integre com o gerenciamento de arquivo de PAC existente.

![Conexão com o Office 365 por meio de firewalls e proxies.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Figura 1: perímetro da rede corporativa simples**

O arquivo de PAC é implantado em navegadores da Web, no ponto 1, na Figura 1. Ao usar um arquivo PAC para egresso direta de tráfego de rede vital do Office 365, você também precisará permitir a conectividade para os endereços IP por trás dessas URLs em seu firewall de perímetro de rede. Isso é feito buscando os endereços IP para as mesmas categorias de pontos de extremidade do Office 365, conforme especificado no arquivo PAC e criando ACLs de firewall com base nesses endereços. O firewall é o ponto 3 na Figura 1.

Separadamente se você optar por apenas o roteamento direto para os pontos de extremidade da categoria otimizar, qualquer ponto de extremidade de permissão de categoria necessário enviado para o servidor proxy precisará ser listado no servidor proxy para ignorar o processamento. Por exemplo, as interrupções SSL e a inspeção e a autenticação de proxy são incompatíveis com os pontos de extremidade de categoria optimize e Allow. O servidor proxy é o ponto 2 na Figura 1.

A configuração comum é permitir sem o processamento de todo o tráfego de saída do servidor proxy para os endereços IP de destino do tráfego de rede do Office 365 que atinge o servidor proxy. Para obter informações sobre problemas com o SSL Break e inspecionar, consulte [usando dispositivos de rede de terceiros ou soluções no tráfego do Office 365](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Há dois tipos de arquivos de PAC que o script Get-PacFile gerará.

|**Tipo**|**Descrição**|
|:-----|:-----|
|**1** <br/> |Send otimiza o tráfego de ponto de extremidade direto e tudo o mais para o servidor proxy. <br/> |
|**duas** <br/> |Enviar otimizar e permitir tráfego de ponto de extremidade direto e tudo o mais para o servidor proxy. Este tipo também pode ser usado para enviar todos os tráfegos do ExpressRoute suportados para o Office 365 para os segmentos de rede ExpressRoute e tudo o mais para o servidor proxy. <br/> |

Veja um exemplo simples de chamar o script do PowerShell:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Há vários parâmetros que podem ser passados para o script:

|**Parâmetro**|**Description**|
|:-----|:-----|
|**ClientRequestId** <br/> |Isso é obrigatório e é um GUID passado para o serviço Web que representa a máquina cliente que está fazendo a chamada. <br/> |
|**Instância** <br/> |A instância de serviço do Office 365 que assume como padrão em todo o mundo. Também passado para o serviço Web. <br/> |
|**TenantName** <br/> |O nome do locatário do Office 365. Passado para o serviço Web e usado como um parâmetro substituível em algumas URLs do Office 365. <br/> |
|**Tipo** <br/> |O tipo de arquivo de PAC de proxy que você deseja gerar. <br/> |

Este é outro exemplo de chamada do script do PowerShell com parâmetros adicionais:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Servidor proxy ignora o processamento do tráfego de rede do Office 365

Onde os arquivos de PAC não são usados para tráfego de saída direta, você ainda deseja ignorar o processamento no seu perímetro de rede configurando seu servidor proxy. Alguns fornecedores de servidor proxy habilitaram a configuração automatizada, conforme descrito no [programa de parceria de rede do Office 365](office-365-networking-partner-program.md).

Se você estiver fazendo isso manualmente, precisará obter os dados de categoria otimizar e permitir ponto de extremidade do endereço IP do Office 365 e do serviço Web URL e configurar seu servidor proxy para ignorar o processamento para eles. É importante evitar interrupção de SSL e autenticação de inspecionar e proxy para os pontos de extremidade de categoria otimizar e permitir.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Gerenciamento de alterações para endereços IP e URLs do Office 365

Além de selecionar a configuração apropriada para o seu perímetro de rede, é fundamental que você adote um processo de gerenciamento de alterações para os pontos de extremidade do Office 365. Esses pontos de extremidade mudam regularmente e, se você não gerencia as alterações, você pode terminar com usuários bloqueados ou com baixo desempenho após um novo endereço IP ou URL ser adicionado.

Alterações nos endereços IP e URLs do Office 365 geralmente são publicadas próximo ao último dia de cada mês. Às vezes, uma alteração será publicada fora desse cronograma devido aos requisitos operacionais, de suporte ou de segurança.

Quando uma alteração é publicada que requer que você atue porque um endereço IP ou uma URL foi adicionada, você deve receber um aviso de 30 dias da hora que publicamos a alteração até que haja um serviço do Office 365 nesse ponto de extremidade. Embora o objetivo desse período de notificação, nem sempre é possível ser possível devido aos requisitos de segurança, de suporte ou operacionais. Alterações que não exigem ação imediata para manter a conectividade, como endereços IP removidos ou URLs ou alterações menos significativas, não incluem notificações antecipadas. Independentemente de qual notificação é fornecida, listamos a data de ativação do serviço esperada para cada alteração.

### <a name="change-notification-using-the-web-service"></a>Notificação de alteração usando o serviço Web

Você pode usar o endereço IP do Office 365 e o serviço Web de URL para obter a notificação de alteração. Recomendamos chamar o método Web **/version** uma vez por hora para verificar a versão dos pontos de extremidade que você está usando para se conectar ao Office 365. Se essa versão mudar em comparação com a versão que você está usando, você deve obter os dados mais recentes do ponto de extremidade do método Web do **/Endpoints** e, opcionalmente, obter as diferenças do método Web **/Changes** . Não é necessário chamar os métodos Web **/Endpoints** ou **/Changes** se não houve nenhuma alteração na versão encontrada.

Para obter mais informações, consulte o [endereço IP do Office 365 e o serviço Web de URL](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Alterar notificação usando RSS feeds

O serviço Web de URL e endereço IP do Office 365 fornece um RSS feed que você pode assinar no Outlook. Há links para as URLs RSS em cada uma das páginas específicas da instância do serviço do Office 365 para os endereços IP e URLs. Para obter mais informações, consulte o [endereço IP do Office 365 e o serviço Web de URL](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Alteração de notificação e análise de aprovação usando o Microsoft Flow

Entendemos que você ainda pode exigir o processamento manual para alterações de ponto de extremidade de rede que aparecem em cada mês. Você pode usar o Microsoft Flow para criar um fluxo que o notifique por email e, opcionalmente, execute um processo de aprovação para alterações quando os pontos de extremidade de rede do Office 365 tiverem alterações. Após a conclusão da revisão, você pode fazer com que o fluxo envie as alterações automaticamente para o firewall e a equipe de gerenciamento do servidor proxy.

Para obter informações sobre um modelo e exemplo de fluxo da Microsoft, consulte [use Microsoft Flow para receber um email para alterações nos endereços IP e URLs do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Perguntas frequentes sobre pontos de extremidade de rede do Office 365

Perguntas frequentes sobre o administrador sobre a conectividade do Office 365:
  
### <a name="how-do-i-submit-a-question"></a>Como eu envio uma pergunta?

Clique no link na parte inferior para indicar se o artigo foi útil ou não e envie nenhuma pergunta adicional. Monitoramos os comentários e atualizamos as perguntas aqui com a maioria das perguntas frequentes.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Como determinar o local do meu locatário?

 O **local do locatário** é melhor determinado usando nosso mapa de [datacenter](https://aka.ms/datamaps).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Estou trocando apropriadamente à Microsoft?

 Os **locais de emparelhamento** são descritos mais detalhadamente em [emparelhamento com a Microsoft](https://www.microsoft.com/peering).
  
Com mais de 2500 relações de emparelhamento de ISP globalmente e 70 pontos de presença, obter de sua rede para a nossa deve ser uniforme. Não é possível que isso gaste alguns minutos para garantir que a relação de emparelhamento do seu ISP seja a mais adequada, [Veja alguns exemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) de boas e não boas mãos de ponto de partida para nossa rede.
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Vejo solicitações de rede para endereços IP que não estão na lista publicada, preciso fornecer acesso a elas?
<a name="bkmk_MissingIP"> </a>

Só fornecemos endereços IP para os servidores do Office 365 que você deve rotear diretamente para o. Esta não é uma lista abrangente de todos os endereços IP para os quais você verá as solicitações de rede. Você verá as solicitações de rede para endereços IP de terceiros, não publicados, da Microsoft e de terceiros. Esses endereços IP são gerados dinamicamente ou gerenciados de forma que evitam o aviso em tempo hábil quando mudam. Se o firewall não puder permitir acesso com base nos FQDNs dessas solicitações de rede, use um arquivo de PAC ou de WPAD para gerenciar as solicitações.
  
Confira um IP associado ao Office 365 no qual você deseja obter mais informações?
  
1. Verifique se o endereço IP está incluído em um intervalo de publicação maior usando uma [calculadora de CIDR](https://jodies.de/ipcalc).
2. Veja se um parceiro é proprietário do IP com uma [consulta whois](https://dnsquery.org/). Se ele for proprietário da Microsoft, poderá ser um parceiro interno.
3. Verifique o certificado, em um navegador, conecte-se ao endereço IP usando o *https://\<ip_address\> * , verifique os domínios listados no certificado para entender quais domínios estão associados ao endereço IP. Se for um endereço IP de propriedade da Microsoft e não na lista de endereços IP do Office 365, é provável que o endereço IP esteja associado a uma CDN da Microsoft, como o *MSOCDN.net* ou outro domínio da Microsoft, sem informações de IP publicadas. Se você encontrar o domínio no certificado, um onde afirmamos listar o endereço IP, informe-nos.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Algumas URLs do Office 365 apontam para registros CNAME em vez de registros no DNS. O que preciso fazer com os registros CNAME?

Computadores clientes precisam de um registro DNS A ou AAAA que inclua um ou mais endereços IP para se conectar a um serviço de nuvem. Algumas URLs incluídas no Office 365 mostram registros CNAME em vez de registros A ou AAAA. Esses registros CNAME são intermediários e pode haver vários em uma cadeia. Eles sempre serão eventualmente resolvidos para um registro A ou AAAA de um endereço IP. Por exemplo, considere a seguinte série de registros DNS, que, por fim, é resolvida para o endereço IP _IP_1_:

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Esses redirecionamentos CNAME são uma parte normal do DNS e são transparentes para o computador cliente e transparentes para servidores proxy. Eles são usados para balanceamento de carga, redes de distribuição de conteúdo, alta disponibilidade e mitigação de incidentes de serviço. A Microsoft não publica os registros CNAME intermediários, eles estão sujeitos a alterações a qualquer momento e não é necessário configurá-los conforme permitido no servidor de proxy.

Um servidor proxy valida a URL inicial que, no exemplo acima, é serviceA.office.com e essa URL seria incluída na publicação do Office 365. O servidor proxy solicita a resolução de DNS dessa URL para um endereço IP e receberá IP_1 de volta. Ele não valida os registros de redirecionamento de CNAME intermediário.

Não é recomendável que as configurações de código ou a lista de brancas do Office 365 indiretas não sejam suportadas pela Microsoft, e é conhecido por causar problemas de conectividade do cliente. As soluções DNS que bloqueiam o redirecionamento de CNAME ou que, de outra forma, resolvem incorretamente as entradas DNS do Office 365, podem ser resolvidas por meio do encaminhamento DNS condicional (com escopo para os FQDNs do Office 365 usados diretamente) com a recursão de DNS habilitada. Vários produtos de perímetro de rede de terceiros integram nativamente a lista de pontos de extremidade recomendados do Office 365 em suas configurações usando o [endereço IP 365 do Office e o serviço Web de URL](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Por que vejo nomes como nsatc.net ou akadns.net nos nomes de domínio da Microsoft?
<a name="bkmk_akamai"> </a>

O Office 365 e outros serviços da Microsoft usam vários serviços de terceiros, como Akamai e MarkMonitor, para melhorar a experiência do Office 365. Para manter a melhor experiência possível, podemos alterar esses serviços no futuro. Domínios de terceiros podem hospedar conteúdo, como uma CDN, ou podem hospedar um serviço, como um serviço de gerenciamento de tráfego geográfico. Alguns dos serviços em uso no momento incluem:
  
[MarkMonitor](https://www.markmonitor.com/) está em uso quando você vê as solicitações que incluem * \*. nsatc.net* . Este serviço fornece proteção e monitoramento de nomes de domínio para proteção contra comportamentos mal-intencionados.
  
[ExactTarget](https://www.marketingcloud.com/) está em uso quando você vê as solicitações para * \*. exacttarget.com* . Este serviço oferece gerenciamento e monitoramento de links de email contra comportamentos mal-intencionados.
  
O [Akamai](https://www.akamai.com/) está em uso quando você vê solicitações que incluem um dos FQDNs a seguir. Este serviço oferece serviços de rede de distribuição de conteúdo e DNS geográfico.
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Preciso ter a conectividade mínima possível para o Office 365
<a name="bkmk_thirdparty"> </a>

Como o Office 365 é um pacote de serviços criados para funcionar pela Internet, as promessas de confiabilidade e disponibilidade são baseadas em muitos serviços padrão da Internet que estão disponíveis. Por exemplo, os serviços padrão da Internet, como DNS, CRL e CDNs devem ser acessíveis para usar o Office 365 da mesma forma que devem ser acessados para usar os serviços de Internet mais modernos.

O pacote do Office 365 é dividido nas principais áreas de serviço. Eles podem ser habilitados seletivamente para conectividade e há uma área comum que é uma dependência para todos e é sempre necessário.

|**Área de serviço**|**Descrição**|
|:-----|:-----|
|**Exchange** <br/> |Proteção do Exchange Online e do Exchange Online <br/> |
|**SharePoint** <br/> |SharePoint Online e OneDrive for Business <br/> |
|**Skype for Business Online e Microsoft Teams** <br/> |Skype for Business e Microsoft Teams <br/> |
|**Comum** <br/> |Office 365 Pro Plus, Office em um navegador, Azure AD e outros pontos de extremidade de rede comuns <br/> |

Além dos serviços básicos da Internet, há serviços de terceiros que são usados apenas para integrar a funcionalidade. Embora sejam necessários para integração, eles são marcados como opcionais no artigo de pontos de extremidade do Office 365, o que significa que a funcionalidade principal do serviço continuará funcionando se o ponto de extremidade não estiver acessível. Qualquer ponto de extremidade de rede necessário terá o atributo Required definido como true. Qualquer ponto de extremidade de rede opcional terá o atributo Required definido como false e o atributo Notes detalhará a funcionalidade ausente que você deverá esperar se a conectividade for bloqueada.
  
Se você estiver tentando usar o Office 365 e localizar serviços de terceiros não estiverem acessíveis, convém [garantir que todos os FQDNs marcados ou opcionais neste artigo sejam permitidos através do proxy e firewall](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Como faço para bloquear o acesso aos serviços de consumidor da Microsoft?
<a name="bkmk_consumer"> </a>

Restringir o acesso aos nossos serviços de consumidor deve ser feito por sua conta e risco. A única maneira confiável de bloquear serviços de consumidor é restringir o acesso ao FQDN do *login.Live.com* . Esse FQDN é usado por um amplo conjunto de serviços, incluindo serviços não-consumidor como o MSDN, o TechNet e outros. Esse FQDN também é usado pelo programa de troca segura de arquivos do suporte da Microsoft e é necessário para transferir arquivos para facilitar a solução de problemas para produtos da Microsoft.  Restringir o acesso a esse FQDN pode resultar na necessidade de também incluir exceções à regra para solicitações de rede associadas a esses serviços.
  
Tenha em mente que bloquear o acesso aos serviços de cliente da Microsoft sozinhos não impedirá a capacidade de alguém de sua rede Exfiltrate informações usando um locatário do Office 365 ou outro serviço.
  
## <a name="related-topics"></a>Tópicos Relacionados

[URL do serviço Web e endereço IP do Office 365](office-365-ip-web-service.md)

[Intervalos de IP do Datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Grupos de notícias públicos da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisitos de infraestrutura de rede para o Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute e Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URLs e intervalos de endereços IP do Office 365](urls-and-ip-address-ranges.md)
  
[Como gerenciar o ExpressRoute para a conectividade do Office 365](managing-expressroute-for-connectivity.md)
  
[Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md)
