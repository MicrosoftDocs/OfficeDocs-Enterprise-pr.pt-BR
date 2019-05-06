---
title: URL do serviço Web e endereço IP do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/1/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Para você identificar e diferenciar melhor o tráfego de rede do Office 365, um novo serviço Web publica pontos de extremidade do Office 365, permitindo avaliar, configurar e se manter atualizado em relação às alterações com mais facilidade. Esse novo serviço Web substitui os arquivos XML para download que estão disponíveis atualmente.
ms.openlocfilehash: af1ff6f222d4d9563116c4173ebeca9ca9f4470d
ms.sourcegitcommit: 3b5597cab55bc67890fd6c760102efce513be87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/01/2019
ms.locfileid: "33512677"
---
# <a name="office-365-ip-address-and-url-web-service"></a>URL do serviço Web e endereço IP do Office 365

Para você identificar e diferenciar melhor o tráfego de rede do Office 365, um novo serviço Web publica pontos de extremidade do Office 365, permitindo avaliar, configurar e se manter atualizado em relação às alterações com mais facilidade. Esse novo serviço Web substitui os arquivos XML para download que estão disponíveis atualmente. A descontinuação do formato XML está prevista para 2 de outubro de 2018.

Como cliente ou fornecedor de dispositivos de perímetro de rede, você pode criar com o novo serviço Web baseado em REST para as entradas FQDN e os endereços IP do Office 365. É possível acessar os dados diretamente de um navegador da Web usando essas URLs.

- Para ter a última versão dos intervalos de endereços IP e URLs do Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Para os dados na página de intervalos de endereços IP e URLs do Office 365 para firewalls e servidores proxy, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Para obter as últimas alterações desde o fim de julho de 2018, quando os serviço Web foi disponibilizado, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Como cliente, você pode usar esse serviço Web para:

- Atualize os seus scripts do Windows PowerShell para obter dados de ponto de extremidade do Office 365 e modificar qualquer formatação dos dispositivos de rede.
- Use essas informações para atualizar os arquivos PAC implantados nos computadores clientes.

Como fornecedor de dispositivos de perímetro de rede, é possível usar esse serviço Web para:

- Criar e testar o software do dispositivo para baixar a lista de configuração automatizada.
- Verificar a versão atual.
- Obter as alterações atuais.

> [!NOTE]
> Se você estiver usando o Azure ExpressRoute para se conectar ao Office 365, confira [Azure ExpressRoute para Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) para se familiarizar com os serviços do Office 365 com suporte no Azure ExpressRoute. Além disso, veja o artigo [URLs e intervalos de endereços IP do Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) para entender quais solicitações de rede para aplicativos do Office 365 exigem conectividade com a Internet. Isso ajudará a configurar melhor seus dispositivos de segurança de perímetro.

Confira mais informações em:

- [Comunicado de postagem no blog do Fórum da Comunidade de Tecnologia do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Fórum da Comunidade de Tecnologia do Office 365 para perguntas sobre o uso dos serviços Web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Parâmetros comuns

Estes parâmetros são comuns a todos os métodos de serviço Web:

- **format=<JSON | CSV>** - Por padrão, o formato de dados retornado é JSON. Use este parâmetro opcional para retornar os dados no formato de valores separados por vírgula (CSV).
- **ClientRequestId=\<guid>** - Um GUID necessário que você gera para associação de clientes. Você deve gerar um GUID para cada computador que chama o serviço da web. Não use os GUIDs mostrados nos exemplos a seguir porque eles podem ser bloqueados pelo serviço da Web no futuro. O formato GUID é_ xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, em que x representa um número hexadecimal. Para gerar um GUID, use o comando [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) do PowerShell.

## <a name="version-web-method"></a>Método da web de versão

As Microsoft atualiza as entradas de FQDN e o endereço IP do Office 365 ao final de cada mês e, eventualmente, fora do ciclo para atender a requisitos de suporte ou operacionais. Os dados de cada instância publicada recebem um número de versão. O método Web de versão permite pesquisar a última versão de cada instância de serviço do Office 365. Recomendamos verificar a versão diariamente, ou no máximo, a cada hora. As novas versões devem ser disponibilizadas no início de cada mês. Às vezes, devido a incidentes de suporte, segurança ou outros requisitos operacionais, novas versões são disponibilizadas ao longo do mês.

Os parâmetros para o método da web de versão são:

- **AllVersions=<true | false>** - Por padrão, a versão retornada é a mais recente. Inclua este parâmetro opcional para solicitar todas as versões publicadas desde que o serviço da Web foi lançado pela primeira vez.
- **Format=<JSON | CSV | RSS>** – Além dos formatos JSON e CSV, o método da web de versão também é compatível com RSS. Você pode usar esse parâmetro opcional junto com o parâmetro _AllVersions=true_ para solicitar um feed RSS que possa ser usado com o Outlook ou outros leitores de RSS.
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - Este parâmetro opcional especifica a instância para o retorno da versão. Se omitido, todas as instâncias serão retornadas. As instâncias válidas são: em todo o mundo, China, Alemanha, USGovDoD, USGovGCCHigh.

A versão do método Web não é limitado por taxa e nunca retornará o código de resposta HTTP 429. A resposta à versão do método Web inclui um cabeçalho de controle de cache que recomenda o armazenamento em cache dos dados por 1 hora. O resultado do método de versão Web pode ser um único registro ou uma matriz de registros. Os elementos de cada registro são:

- instance – um nome curto da instância de serviço do Office 365.
- latest – a versão mais recente dos pontos de extremidade da instância especificada.
- versions – uma lista com todas as versões anteriores da instância especificada. Este elemento só será incluído se o parâmetro AllVersions for verdadeiro.

Você pode usar o Microsoft Flow para receber notificações de email das alterações nos endereços IP e URLs. Confira [Usar o Microsoft Flow para receber um email das alterações em URLs e endereços IP do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).

### <a name="examples"></a>Exemplos:

Exemplo 1 de URI de solicitação: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Esse URI retorna a última versão de cada instância de serviço do Office 365. Exemplo de resultado:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> O GUID para o parâmetro ClientRequestID nesses URIs são apenas um exemplo. Para experimentar os URIs do serviço Web, gere o seu próprio GUID. O GUIDs exibido nesses exemplos pode ser bloqueado pelo serviço Web no futuro.

Exemplo 2 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Esse URI retorna a última versão da instância de serviço especificada do Office 365. Exemplo de resultado:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

Exemplo 3 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este URI mostra os resultados no formato CSV. Exemplo de resultado:

```csv
instance,latest
Worldwide,2018063000
```

Exemplo 4 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este URI mostra todas as versões anteriores que foram publicadas para a instância de serviço do Office 365 em todo o mundo. Exemplo de resultado:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

Exemplo 5 de URI de RSS feed: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

Este URI mostra um RSS feed das versões publicadas que contêm links para a lista de alterações de cada versão. Exemplo de resultado:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
...
```

## <a name="endpoints-web-method"></a>Método da Web de pontos de extremidade

O método da Web de pontos de extremidade retorna todos os registros para intervalos de endereços IP e URLs que compõem o serviço do Office 365. Enquanto os dados mais recentes do método da Web de pontos de extremidade devem ser usados para a configuração de dispositivos de rede, os dados podem ser armazenados em cache por até 30 dias após sua publicação devido ao aviso antecipado fornecido para adições. Recomendamos que você chame o método da Web de pontos de extremidade somente quando o método da web da versão indicar que uma nova versão dos dados está disponível.

Os parâmetros para o método da Web de pontos de extremidade são:

- **ServiceAreas=<Common | Exchange | SharePoint | Skype>** - Uma lista de áreas de serviço separadas por vírgulas. Os itens válidos são _Common_, _Exchange_, _SharePoint_ e _Skype_. Como os itens da área de serviço comum são um pré-requisito para todas as outras áreas de serviço, o serviço da Web sempre os incluirá. Se você não incluir esse parâmetro, todas as áreas de serviço serão retornadas.
- **TenantName=<tenant_name>** - Seu nome de locatário do Office 365. O serviço da web insere o seu nome fornecido em partes de URLs que incluem o nome do locatário. Se você não fornecer um nome de locatário, essas partes das URLs terão o caractere curinga (\*).
- **NoIPv6=<true | false>** - Defina como true para excluir endereços IPv6 dos resultados; por exemplo, se você não usar o IPv6 em sua rede.
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - Este parâmetro obrigatório especifica a instância para a qual retornar os terminais. As instâncias válidas são: em todo o mundo, China, Alemanha, USGovDoD, USGovGCCHigh.

Se você chamar o método da Web de pontos de extremidade um grande número de vezes a partir do mesmo endereço IP do cliente, poderá receber o código de resposta HTTP 429 (Excesso de solicitações). A maioria das pessoas nunca verá isso. Se você receber esse código de resposta, aguarde uma hora antes de repetir sua solicitação. Planeje chamar apenas o método da Web de pontos de extremidade quando o método da web de versão indicar que há uma nova versão disponível.

O resultado do método Web de pontos de extremidade é uma matriz de registros com cada registro representando um conjunto de pontos de extremidade. Os elementos de cada registro são:

- id – o número de ID imutável do conjunto de pontos de extremidade.
- serviceArea – a área de serviço que faz parte do: Common, Exchange, SharePoint ou Skype.
- urls – as URLs do conjunto de pontos de extremidade. Uma matriz JSON de registros DNS. Omitidas caso estejam em branco.
- tcpPorts – as portas TCP para o conjunto de pontos de extremidade. Os elementos de todas as portas são formatados como uma lista separada por vírgulas ou intervalos de portas separados por um hífen (-). As portas se aplicam a todos os endereços IP e todas as URLs do conjunto de pontos de extremidade para essa categoria. Omitidas caso estejam em branco.
- udpPorts – as portas UDP para os intervalos de endereço IP deste conjunto de pontos de extremidade. Omitidas caso estejam em branco.
- ips – os intervalos de endereço IP associados a esse conjunto de pontos de extremidade conforme associação com as portas TCP ou UDP listadas. Uma matriz JSON de intervalos de Endereço IP. Omitidos caso estejam em branco.
- categoria - A categoria conectividade para a configuração de ponto de extremidade. Os valores válidos são Otimizar, Permitir e Padrão. Se você estiver usando os dados do ponto de extremidade para pesquisar a categoria de um endereço IP ou URL, é possível que sua consulta possa retornar diversas categorias. Há alguns motivos para isso acontecer. Nesses casos, você deve seguir as recomendações para a categoria de maior prioridade. Por exemplo, se o ponto de extremidade aparecer tanto em Otimizar quanto em Permitir, você deve seguir os requisitos de Otimizar. Obrigatório.
- expressRoute – Verdadeiro ou Falso se esse conjunto de pontos de extremidade for roteado pelo ExpressRoute.
- required – Verdadeiro se esse conjunto de pontos de extremidade precisar de conectividade com o Office 365 para ter suporte. Falso se o conjunto de pontos de extremidade for opcional.
- notes – para pontos de extremidade opcionais, este texto descreve a funcionalidade do Office 365 que não estará disponível se os endereços IP ou URLs deste conjunto de pontos de extremidade não puderem ser acessados na camada de rede. Omitidos caso estejam em branco.

### <a name="examples"></a>Exemplos:

Exemplo 1 de URI de solicitação: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Esse URI obtém todos os pontos de extremidade da instância do Office 365 em todo o mundo para todas as cargas de trabalho. Exemplo de resultado mostrando um trecho da saída:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

Os conjuntos de ponto de extremidade adicionais não são incluídos neste exemplo.

Exemplo 2 de URI de solicitação: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Esse exemplo obtém pontos de extremidade da instância do Office 365 em todo o mundo apenas para o Exchange Online e dependências.

O resultado do exemplo 2 é semelhante ao do exemplo 1, exceto que os resultados não incluirão pontos de extremidade do SharePoint Online ou do Skype for Business Online.

## <a name="changes-web-method"></a>Método Web de alterações

O método Web de alterações retorna as atualizações mais recentes publicadas. Normalmente, são as alterações do mês anterior de URLs e dos intervalos de endereços IP. As alterações mais importantes a serem processadas ocorrem quando novas URLs ou endereços IP são adicionados, uma vez que a falha ao adicionar um endereço IP à lista de controle de acesso do firewall ou a uma URL a uma lista de bypass de servidores proxy pode causar uma interrupção para usuários do Office 365 por trás desse dispositivo de rede. Apesar dos requisitos operacionais, as operações _Adicionar_ são adicionadas com uma notificação 30 dias antes da interrupção.

O parâmetro necessário para o método da web de alterações é:

- **Version=\<YYYYMMDDNN>** - Parâmetro de rota de URL obrigatório. Este valor deve ser a versão que você tem implementada atualmente. O serviço da Web retornará as alterações desde essa versão. O formato é _YYYYMMDDNN_, onde _NN_ são zeros. O serviço da web requer que este parâmetro contenha exatamente 10 dígitos.

O método da Web de alterações é limitado por taxa da mesma forma que o método da web de pontos de extremidade. Se você receber um código de resposta HTTP 429, espere 1 hora antes de repetir sua solicitação.

O resultado do método Web de alterações é uma matriz de registros com cada registro representando uma alteração em uma versão específica dos pontos de extremidade. Os elementos de cada registro são:

- id – a ID imutável do registro de alterações.
- endpointSetId - O ID do registro do conjunto de pontos de extremidade que é alterado.
- disposição - Pode ser de alteração, adição ou remoção e descreve o que a alteração fez no registro do conjunto de pontos de extremidade.
- impacto – nem todas as alterações serão igualmente importantes para todo ambiente. Isso descreve o impacto esperado em um ambiente de perímetro de rede corporativa como resultado dessa alteração. Esse atributo está incluído somente nos registros de alteração da versão 2018112800 e versões posteriores. As opções para o impacto são:
  - AddedIp – um endereço de IP foi adicionado ao Office 365 e estará ativo no serviço em breve. Isso representa uma alteração que você precisa realizar em um firewall ou em outro dispositivo de perímetro de rede de camada 3. Se você não adicionar isso antes de começar a usá-lo, você pode observar uma interrupção.
  - AddedUrl - Uma URL foi adicionada ao Office 365 e será exibida no serviço em breve. Isso representa uma mudança que você precisa fazer em um servidor de proxy ou dispositivo de perímetro de rede de análise de URL. Se você não adicionar isso antes de começar a usá-lo, talvez haja uma interrupção.
  - AddedIpAndUrl - um endereço de IP e URL foram adicionados. Isso representa uma alteração que você precisa realizar em um dispositivo de camada 3 firewall ou em um servidor proxy ou dispositivo de análise da URL. Se você não adicionar isso antes de começar a usá-lo, você pode observar uma interrupção.
  - RemovedIpOrUrl, pelo menos um endereço IP ou URL foi removido do Office 365. Você deve remover os pontos de extremidade de rede nos seus dispositivos de perímetro, mas não há nenhuma data limite para você fazer isso.
  - ChangedIsExpressRoute – o atributo de suporte do ExpressRoute foi modificado. Se você usar o ExpressRoute será necessário tomar medidas dependendo da configuração.
  - MovedIpOrUrl – Movemos um endereço IP ou uma Url entre esse conjunto de ponto de extremidade e outro. Geralmente, nenhuma ação é necessária.
  - RemovedDuplicateIpOrUrl – Removemos um endereço IP ou uma Url duplicados, mas ele ainda é publicado para o Office 365. Geralmente, nenhuma ação é necessária.
  - OtherNonPriorityChanges – alteramos algo menos crítico que todas as opções como um campo de anotações
- version – a versão do conjunto de pontos de extremidade em que a alteração foi introduzida. Os números de versões estão no formato _AAAAMMDDNN_, em que NN é um número natural incrementado caso existam várias versões a serem publicadas em um único dia.
- previous - Uma subestrutura detalhando os valores anteriores de elementos alterados no conjunto de pontos de extremidade. Isso não será incluído para conjuntos de pontos de extremidade recém-adicionados. Inclui _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ e _notes_.
- current - Uma subestrutura detalhando valores atualizados de elementos de alterações no conjunto de pontos de extremidade. Inclui _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ e _notes_.
- add – uma subestrutura que detalha os itens a serem adicionados às coleções do conjunto de pontos de extremidade. Omitida caso não haja nenhuma adição.
  - effectiveDate – define os dados de quando as adições estarão disponíveis no serviço.
  - ips - Itens a serem adicionados à matriz _ips_.
  - URLs - Itens a serem adicionados à matriz _urls_.
- remover - Uma subestrutura detalhando itens a serem removidos do conjunto de pontos de extremidade. Omitido se não houver remoções.
  - ips - itens a serem removidos da matriz _ips_.
  - urls- Itens a serem removidos da matriz _urls_.

### <a name="examples"></a>Exemplos:

Exemplo 1 de URI de solicitação: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Solicita todas as alterações anteriores da instância do serviço do Office 365 em todo o mundo. Exemplo de resultado:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

Exemplo 2 de URI de solicitação: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Solicita as alterações desde a versão especificada da instância do Office 365 em todo o mundo. Nesse caso, a versão especificada é a mais recente. Exemplo de resultado:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>Exemplo de script do PowerShell

Aqui está um script do PowerShell que você pode executar para ver se há ações que você precisa tomar para os dados atualizados. Esse script verifica o número da versão dos pontos de extremidade da instância do Office 365 Worldwide. Quando há uma alteração, ele faz o download dos pontos de extremidade e filtros para os pontos de extremidade das categorias "Permitir" e "Otimizar". Ele também usa um _ClientRequestId_ exclusivo em várias chamadas e salva a versão mais recente encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se há uma atualização de versão.

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>Exemplo de script do Python

Esse é um script do Python, testado com o Python 3.6.3 no Windows 10, que você pode executar para ver se há ações que você precisa realizar em relação aos dados atualizados. Esse script verifica o número da versão dos pontos de extremidade de instâncias do Office 365 em todo o mundo. Quando houver uma alteração, ele baixará os pontos de extremidade e os filtros dos pontos de extremidade das categorias _Permitir_ e _Otimizar_. Ele também usa um ClientRequestId exclusivo em várias chamadas e salva a última versão encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se há alguma atualização da versão.

```python
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>Controle de versão de interface do serviço da Web

No futuro, podem ser necessárias atualizações de parâmetros ou de resultados desses métodos de serviço Web. Após a publicação da versão de disponibilidade geral desses serviços Web, a Microsoft fará os esforços cabíveis para enviar previamente notificações sobre atualizações do material para o serviço Web. Quando acreditar que uma atualização exigirá alterações dos clientes usando o serviço Web, a Microsoft manterá a versão anterior (uma versão antes) do serviço Web disponível por pelo menos doze (12) meses após o lançamento da nova versão. Os clientes que não fizerem a atualização durante esse período, perderão o acesso ao serviço Web e aos seus métodos. É preciso garantir que os clientes do serviço Web continuem trabalhando sem erros se as seguintes alterações forem feitas à assinatura da interface da Web:

- Adição de um novo parâmetro opcional a um método Web existente que não precise ser fornecido por clientes mais antigos e que não afete os resultados recebidos por um cliente mais antigo.
- Adição de um novo atributo nomeado em um dos itens do REST de resposta ou em colunas adicionais para o CSV de resposta.
- Adição de um novo método Web com um novo nome que não é chamado pelos clientes mais antigos.

## <a name="office-365-endpoint-functions-module"></a>Módulo de funções do ponto de extremidade do Office 365

A Microsoft está hospedando um Serviço REST para obter o URI mais recente dos serviços do Office 365.  Para poder usar o URI como uma coleção, você pode usar este módulo com alguns cmdlets úteis.

### <a name="calling-the-rest-service"></a>Chamando o serviço REST

Para usar este módulo, simplesmente copie o arquivo de módulo [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) em algum lugar no seu disco rígido e importe-o diretamente com este comando:

```powershell
    Import-Module O365EndpointFunctions.psm1
```

Depois de importar o módulo, você poderá chamar o serviço REST. Isso retornará o URI como uma coleção que você pode processar diretamente no PowerShell. Você deve inserir o nome do seu locatário do Office 365, conforme descrito no seguinte comando:

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant]
```

> [!NOTE]
> A escrita correta do cmdlet é **Invoke-O365EnpointService**, sem a letra _d_. Este não é um erro tipográfico.

#### <a name="parameters"></a>Parâmetros

- **tenantName** - o nome do seu locatário do Office 365. Este parâmetro é obrigatório.
- **ForceLatest** - Esse parâmetro forçará a API REST a sempre retornar toda a lista do URI mais recente.
- **IPv6** - Esta opção retornará os endereços IPv6 também. Por padrão, somente o IPv4 será retornado.

### <a name="examples"></a>Exemplos

Retornar a lista completa de todos os URIs, incluindo os endereços IPv6

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

Retornar somente os endereços IP para o serviço do Exchange Online

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a>Exportando um arquivo Proxy PAC

Você pode usar este módulo para criar um arquivo Proxy PAC. Neste exemplo, você primeiro obtém os pontos de extremidade e filtra o resultado para selecionar as URLs. Estas URLs são direcionadas para serem exportadas.  

```powershell
 Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a>Tópicos Relacionados
  
[URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Perguntas frequentes sobre pontos de extremidade do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md)

[Rede do Office 365 e ajuste de desempenho](network-planning-and-performance.md)

[Conectividade de rede para Office 365](network-connectivity.md)
  
[Qualidade da mídia e desempenho de conectividade de rede no Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Como otimizar a sua rede para o Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho](performance-tuning-using-baselines-and-history.md)
  
[Plano de solução de problemas de desempenho do Office 365](performance-troubleshooting-plan.md)
