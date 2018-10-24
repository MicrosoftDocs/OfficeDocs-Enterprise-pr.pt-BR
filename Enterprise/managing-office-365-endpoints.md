---
title: Gerenciar pontos de extremidade do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Algumas redes corporativas restringem o acesso a locais de internet genérico ou incluem backhaul substancial ou processamento de tráfego de rede. Para garantir que os computadores em redes como essas podem acessar o Office 365, os administradores de rede e proxy precisam gerenciar a lista de FQDNs, URLs, e endereços IP que compõem a lista de pontos de extremidade do Office 365. Esses necessidade a ser adicionado à rota direta, proxy bypass, e/ou regras de firewall e arquivos de PAC para garantir que as solicitações de rede são capazes de alcançar o Office 365.
ms.openlocfilehash: 480d2fa1b55507187f9150d02907849178a451b5
ms.sourcegitcommit: d93f7a51e8cdefdfc9933cdf1f9e413b013bb367
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "25719015"
---
# <a name="managing-office-365-endpoints"></a>Gerenciar pontos de extremidade do Office 365

A maioria das organizações de empresa que possuem vários escritórios e uma conexão WAN precisará precisa de configuração para conectividade de rede do Office 365. Você pode otimizar sua rede enviando a que todos os confiáveis solicitações diretamente através do firewall da rede do Office 365, ignorando todos inspeção de nível de pacotes adicionais ou processamento. Isso reduz a latência e seus requisitos de capacidade de perímetro. Identificar o tráfego de rede do Office 365 é a primeira etapa no fornecimento de desempenho ideal para seus usuários. Para obter mais informações sobre conectividade de rede do Office 365, consulte [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md)

A Microsoft recomenda que você acessar o Office 365 pontos de extremidade de rede e altera a eles usando o [endereço de IP do Office 365 e a URL do serviço Web](office-365-ip-web-service.md)

Independentemente de como gerenciar o tráfego de rede do Office 365 vital, o Office 365 requer conectividade à Internet. Outros pontos de extremidade de rede onde é necessária a conectividade estão listados nos [pontos de extremidade adicionais não incluídos no serviço Web de URL e endereço de IP do Office 365](additional-office365-ip-addresses-and-urls.md)

Como você pode usar os pontos de extremidade de rede do Office 365 dependerá sua arquitetura de rede da organização de empresa. Este artigo descreve as arquiteturas de rede empresarial podem se integrar com endereços IP do Office 365 e URLs de várias maneiras. A maneira mais fácil para escolher qual rede solicitações a confiança é usar dispositivos SDWAN que oferecem suporte a configuração automatizada do Office 365 em cada um dos diversos escritórios. 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN para saída local de filial do tráfego de rede vital do Office 365

Em cada escritório de filial, você pode fornecer um dispositivo SDWAN que está configurado para rotear o tráfego para otimizar o Office 365 categoria de pontos de extremidade ou otimizar e permitir categorias, diretamente para a rede da Microsoft. Outros tráfegos de rede, incluindo o tráfego de datacenter local, o tráfego de sites da web do Internet gerais e tráfego aos pontos de extremidade de categoria padrão do Office 365 é enviado para outro local em que você tenha um perímetro de rede mais substancial.

Microsoft está trabalhando com provedores SDWAN para habilitar a configuração automatizada. Para obter mais informações, consulte o [Programa de parceria de rede do Office 365](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Usar um arquivo de PAC direto de roteamento de tráfego vital do Office 365

Use arquivos PAC ou WPAD para gerenciar solicitações de rede que estão associadas com o Office 365, mas não têm um endereço IP. Solicitações de rede comuns que são enviadas por meio de um dispositivo de proxy ou perímetro aumentam a latência. Enquanto se quebram SSL e inspecionar cria a maior latência, outros serviços, como a pesquisa de reputação e autenticação de proxy pode causar um desempenho fraco e uma experiência de usuário incorretos. Além disso, esses dispositivos de rede de perímetro precisam capacidade suficiente para processar todas as solicitações de conexão de rede. É recomendável, ignorando os dispositivos de proxy ou inspeção para solicitações de rede diretas do Office 365.
  
[Galeria de PowerShell Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) é um script do PowerShell que lê os pontos de extremidade de rede mais recentes do serviço Web de URL e o endereço de IP do Office 365 e cria um arquivo de PAC da amostra. Você pode modificar o script para que ele se integra o gerenciamento de arquivos PAC existente. 

![Conectando-se ao Office 365 através de firewalls e proxies.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Figura 1 - perímetro da rede corporativa simples**

O arquivo PAC é implantado para os navegadores da web no ponto 1 na Figura 1. Ao usar um arquivo PAC para saída direta do tráfego de rede vital do Office 365, você também precisa permitir a conectividade com os endereços IP por trás dessas URLs em seu firewall de rede de perímetro. Isto é feito buscar os endereços IP para as mesmas categorias de ponto de extremidade de Office 365 conforme especificado no arquivo PAC e criação de firewall ACLs baseadas nesses endereços. O firewall é ponto 3 na Figura 1. 

Separadamente, se você optar por apenas diretos roteamento para os pontos de extremidade de categoria de otimizar, qualquer necessário permitir que os pontos de extremidade de categoria que você enviar para o servidor proxy precisará ser listados no servidor proxy para ignorar o processamento adicional. Por exemplo, quebra SSL e inspecionar e autenticação de Proxy são incompatíveis com o Optimize e permitir pontos de extremidade de categoria. O servidor proxy é ponto 2 na Figura 1.

A configuração comum é permitir sem processamento todo o tráfego de saída do servidor proxy para os endereços IP de destino para o tráfego de rede do Office 365 que acessa o servidor proxy. Para obter informações sobre problemas com SSL se quebram e inspecionar, consulte [usando dispositivos de rede de terceiros ou soluções de tráfego do Office 365](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Existem dois tipos de arquivos de PAC que o script Get-PacFile irá gerar.

|**Tipo**|**Descrição**|
|:-----|:-----|
|**1** <br/> |Envie o tráfego de ponto de extremidade de otimizar direto e todos os outros ao servidor proxy. <br/> |
|**2** <br/> |Envie Optimize e permitir tráfego de ponto de extremidade direto e todos os outros para o servidor proxy. Esse tipo de também pode ser usado para enviar que todas as ExpressRoute com suporte para o tráfego do Office 365 para os segmentos de rede ExpressRoute e todo o resto do servidor proxy. <br/> |

Aqui está um exemplo simples de chamar o script do PowerShell:

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Há vários parâmetros que você pode passar para o script:

|**Parameter**|**Descrição**|
|:-----|:-----|
|**ClientRequestId** <br/> |Isso é necessário e um GUID que é passado para o serviço web que representa a máquina cliente fazendo a chamada. <br/> |
|**Instance** <br/> |A instância de serviço do Office 365 que usa como padrão Worldwide. Também é passado para o serviço web. <br/> |
|**TenantName** <br/> |Seu nome de Inquilino do Office 365. Passadas para o serviço da web e usado como um parâmetro substituível em algumas URLs do Office 365. <br/> |
|**Tipo** <br/> |O tipo do arquivo PAC de proxy que você deseja gerar. <br/> |

Aqui está outro exemplo de chamar o script do PowerShell com parâmetros adicionais.

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Processamento de tráfego de rede do Office 365 de desvio do servidor proxy 

Onde os arquivos de PAC não são usados para tráfego de saída direto, ainda quiser ignorar processamento no seu perímetro de rede, configurando o servidor proxy. Alguns fornecedores de servidor proxy tem habilitado a configuração automatizada disso, conforme descrito no [Programa de parceria de rede do Office 365](office-365-networking-partner-program.md). 

Se você estiver fazendo isso manualmente você precisará obter a otimizar e permitir que os dados de categoria do ponto de extremidade do endereço de IP do Office 365 e URL do serviço Web e configure o servidor proxy para ignorar o processamento para esses. É importante evitar quebrar SSL e inspecionar e autenticação de Proxy para a otimizar e permitir que os pontos de extremidade de categoria. 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Gerenciamento de alteração para endereços IP do Office 365 e URLs

Além de selecionar a configuração apropriada para seu perímetro de rede, é muito importante que você adotar um processo de gerenciamento de alterações para pontos de extremidade do Office 365. Esses pontos de extremidade alterar regularmente e se você não gerencia as alterações, você pode acabar tendo usuários bloqueados ou com desempenho ruim após um novo IP endereço ou URL é adicionado. 

Alterações nos endereços IP do Office 365 e URLs são geralmente publicadas perto o último dia de cada mês. Em alguns casos, uma alteração será publicada fora que agenda devido à operacionais, suporte ou requisitos de segurança.

Quando uma alteração é publicada que exige a atuar como um endereço IP ou a URL foi adicionado, você deve esperar receber o aviso de 30 dias desde o momento em que publicamos a alteração até que haja um serviço do Office 365 no ponto de extremidade. Embora o nosso objetivo para esse período de notificação, não sempre pode ser possível devido à operacionais, suporte ou requisitos de segurança. As alterações que não exigem ação imediata para manter a conectividade, tais como removido endereços IP ou URLs ou menos alterações significativas, não incluir notificação prévia. Independentemente de qual notificação for fornecida, listamos da data de ativação de serviço esperados para cada alteração.

### <a name="change-notification-using-the-web-service"></a>Usando o serviço Web de notificação de alteração

Você pode usar o endereço de IP do Office 365 e a URL do serviço Web para obter a notificação de alteração. Recomendamos que você chama o método de web de **/version** uma vez por hora para verificar a versão dos pontos de extremidade que você está usando para se conectar ao Office 365. Se esta versão for alterado, quando comparada com a versão que você tem em uso, obter os dados mais recentes do ponto de extremidade do método **/endpoints** web e, opcionalmente, obtenha as diferenças pelo método **/changes** web. Não é necessário chamar o **/endpoints** ou **/changes** métodos web se não houve nenhuma alteração para a versão encontrada. 

Para obter mais informações, consulte o [endereço de IP do Office 365 e a URL do serviço Web](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Notificação de alteração usando RSS feeds

O endereço de IP do Office 365 e a URL do serviço Web oferece um RSS feed que você pode se inscrever no Outlook. Há links para as URLs RSS em cada um das páginas de específicas da instância de serviço do Office 365 para os endereços IP e URLs. Para obter mais informações, consulte o [endereço de IP do Office 365 e a URL do serviço Web](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Usando o Microsoft Flow de revisão de notificação de alteração e aprovação

Sabemos que você ainda pode exigir processamento manual para que as alterações de ponto de extremidade de rede que vêm por meio de cada mês. Você pode usar o Microsoft Flow para criar um fluxo que notifica você por email e, opcionalmente, executa um processo de aprovação para que as alterações ao Office 365 pontos de extremidade de rede foram alteradas. Após a conclusão da revisão, você pode ter o fluxo de email automaticamente as alterações para a equipe de gerenciamento de servidor de firewall e proxy. 

Para obter informações sobre uma amostra da Microsoft Flow e um modelo, consulte [Uso Microsoft fluxo para receber um email para alterações URLs e endereços IP do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Pontos de extremidade do Office 365 rede perguntas Frequentes

Perguntas sobre o administrador de perguntas frequentes sobre a conectividade do Office 365:
  
### <a name="how-do-i-submit-a-question"></a>Como faço para enviar uma pergunta?

Clique no link na parte inferior para indicar se o artigo foi útil ou não e enviar perguntas adicionais. Podemos monitorar o feedback e atualizar as perguntas aqui com perguntas frequentes.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Como faço para determinar o local do meu locatário?

 **Local de Inquilino** é melhor determinado usando nosso [Mapear datacenter](http://aka.ms/datamaps).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Sou eu correspondência apropriadamente com Microsoft?

 **Peering locais** são descritos em mais detalhes na [correspondência com a Microsoft](https://www.microsoft.com/peering).
  
Com mais de 2.500 relacionamentos de correspondência ISP globalmente e 70 pontos de presença, obtendo da sua rede para nosso deve ser contínuo. Ele não pode prejudicar o gastar alguns minutos, certificando-se que o relacionamento de correspondência do seu ISP é o ideal, [Eis alguns exemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) de uma boa e não tão boas aos transferências à nossa rede. 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Posso ver as solicitações de rede para os endereços IP não está na lista publicada, preciso para fornecer acesso a eles?
<a name="bkmk_MissingIP"> </a>

Fornecemos apenas endereços IP para os servidores do Office 365 que você deve rotear diretamente para. Isso não é uma lista abrangente de todos os endereços IP, para que você verá as solicitações de rede. Você verá as solicitações de rede à Microsoft e endereços IP pertencentes, não publicados, softwares de terceiros. Esses endereços IP dinamicamente são gerados ou gerenciados de forma que impede que o aviso em tempo hábil quando eles são alterados. Se seu firewall não pode permitir o acesso com base nos FQDNs para essas solicitações da rede, use um arquivo PAC ou WPAD para gerenciar as solicitações.
  
Ver que um IP associado ao que você deseja obter mais informações no Office 365?
  
1. Verifique se o endereço IP está incluído em um intervalo de publicado maior usando uma [Calculadora CIDR](http://jodies.de/ipcalc).
2. Consulte se um parceiro possui o IP com uma [consulta whois](https://dnsquery.org/). Se for Microsoft pertencente, talvez seja um parceiro interno.
3. Verifique o certificado, em um navegador conectar ao endereço IP usando *HTTPS://\<IP_ADDRESS\> * , verifique os domínios listados no certificado para entender quais domínios associados com o endereço IP. Se for um endereço IP de propriedade da Microsoft e não está na lista de endereços IP do Office 365, provavelmente é o endereço IP é associado um Microsoft CDN como *MSOCDN.NET* ou outro domínio Microsoft sem informações publicadas de IP. Se você encontrar que o domínio no certificado é uma onde podemos declaração listar o endereço IP, informe-nos.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Por que vejo nomes como nsatc.net ou akadns.net em nomes de domínio Microsoft?
<a name="bkmk_akamai"> </a>

Office 365 e outros serviços da Microsoft usam vários serviços de terceiros, como Akamai e MarkMonitor para melhorar a experiência do Office 365. Para manter oferecendo a melhor experiência possível, podemos alterar esses serviços no futuro. Ao fazer isso, muitas vezes Publicamos o registro CNAME que aponta para um terceiro domínio pertencente, um registro ou endereço IP. Domínios de terceiros podem hospedar o conteúdo, como uma CDN, ou eles podem hospedar um serviço, como um serviço de gerenciamento de tráfego geográficas. Quando você vir conexões com esses terceiros, eles estão no formato de um redirecionamento ou referência, não uma solicitação inicial do cliente. Alguns clientes precisam garantir a essa forma de referência e passar sem adicionar explicitamente que longa lista de serviços de terceiros FQDNs potenciais pode usar o redirecionamento será permitido.
  
Lista de serviços está sujeita a alterações a qualquer momento. Alguns dos serviços atualmente em uso incluem:
  
[MarkMonitor](https://www.markmonitor.com/) está em uso quando você vir solicitações que incluem * \*. nsatc.net* . Este serviço oferece proteção de nome de domínio e monitoramento para proteger contra comportamentos mal-intencionados.
  
[ExactTarget](https://www.marketingcloud.com/) está em uso quando você vir solicitações para * \*. exacttarget.com* . Esse serviço fornece contra comportamento mal intencionado de monitoramento e gerenciamento do link de email.
  
[Akamai](https://www.akamai.com/) está em uso quando você vir solicitações que incluem um dos seguintes FQDNs. Este serviço oferece geo-DNS e serviços de rede de fornecimento de conteúdo.
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Tenho que têm a conectividade mínima possível para o Office 365
<a name="bkmk_thirdparty"> </a>

Office 365 é um conjunto de serviços incluído funcione pela internet, confiabilidade e disponibilidade promessas baseiam-se no muitos serviços de internet padrão que está sendo disponíveis. Por exemplo, os serviços de internet padrão como DNS, CRL e CDNs devem ser acessíveis para usar o Office 365 assim como eles devem ser alcançados para usar os serviços de internet mais modernos.

Pacote Office 365 é dividido em áreas principais de serviço. Eles podem ser habilitados seletivamente para conectividade e houver uma área comum que é uma dependência para todos e é sempre necessário.

|**Área de serviço**|**Descrição**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online e o Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online e OneDrive for Business <br/> |
|**Skype** <br/> |Skype para equipes da Microsoft e de negócios <br/> |
|**Comuns** <br/> |O Office 365 Pro Plus, Office Online, Azure AD e outros pontos de extremidade de rede comuns <br/> |

Além dos serviços básicos da internet, há serviços de terceiros que são usados somente para integrar funcionalidade. Enquanto elas são necessárias para integração, eles estão marcados como opcionais no artigo Office 365 pontos de extremidade que significa que a funcionalidade principal do serviço continuarão a funcionar se o ponto de extremidade não está acessível. Qualquer ponto de extremidade de rede que é exigido terá required atributo definido como verdadeiro. Qualquer ponto de extremidade de rede que é opcional terá o atributo required definido como false e o atributo de notas em detalhes a funcionalidade ausente, você deve esperar que se conectividade será bloqueada.
  
Se você estiver tentando usar o Office 365 e está descobrindo serviços de terceiros não estão acessíveis você desejará [Certifique-se de que todos os FQDNs marcados obrigatório ou opcional neste artigo são permitidos por meio do proxy e firewall](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Como bloquear o acesso aos serviços de consumidor da Microsoft?
<a name="bkmk_consumer"> </a>

Restringir o acesso aos nossos serviços de consumidor deve ser feita por seu próprio risco, a maneira confiável apenas aos serviços do consumidor de bloqueio é para restringir o acesso a *login.live.com* FQDN. Esse FQDN é utilizado por um amplo conjunto de serviços, incluindo serviços de não-consumidor como MSDN, TechNet e outros. Restringindo o acesso a esse FQDN pode resultar na necessidade de também incluem exceções à regra para solicitações de rede associados a esses serviços.
  
Tenha em mente que bloqueando o acesso aos serviços do consumidor do Microsoft sozinhos não impedir a capacidade para alguém em sua rede às informações de exfiltrate usando um locatário do Office 365 ou outro serviço.
  
## <a name="related-topics"></a>Tópicos relacionados

[URL do serviço Web e endereço IP do Office 365](office-365-ip-web-service.md)

[Intervalos de IP do Datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Grupos de notícias públicos da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisitos de infraestrutura de rede da Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute e no power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URLs e intervalos de endereços IP do Office 365](urls-and-ip-address-ranges.md)
  
[Como gerenciar o ExpressRoute para a conectividade do Office 365](managing-expressroute-for-connectivity.md)
  
[Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md)
