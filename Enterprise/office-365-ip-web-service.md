---
title: URL do serviço Web e endereço IP do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
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
ms.openlocfilehash: 1765a35e961d6aa3da42c36e5a04333e57ae010b
ms.sourcegitcommit: 7f1e19fb2d7a448a2dec73d8b2b4b82f851fb5f7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2018
ms.locfileid: "25697977"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="51fd0-104">**URL do serviço Web e endereço IP do Office 365**</span><span class="sxs-lookup"><span data-stu-id="51fd0-104">**Office 365 IP Address and URL Web service**</span></span>

<span data-ttu-id="51fd0-p102">Para você identificar e diferenciar melhor o tráfego de rede do Office 365, um novo serviço Web publica pontos de extremidade do Office 365, permitindo avaliar, configurar e se manter atualizado em relação às alterações com mais facilidade. Esse novo serviço Web substitui os arquivos XML para download que estão disponíveis atualmente. A descontinuação do formato XML está prevista para 2 de outubro de 2018.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="51fd0-p103">Como cliente ou fornecedor de dispositivos de perímetro de rede, você pode criar com o novo serviço Web baseado em REST para as entradas FQDN e os endereços IP do Office 365. É possível acessar os dados diretamente de um navegador da Web usando essas URLs.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="51fd0-110">Para ter a última versão dos intervalos de endereços IP e URLs do Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="51fd0-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="51fd0-111">Para os dados na página de intervalos de endereços IP e URLs do Office 365 para firewalls e servidores proxy, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="51fd0-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="51fd0-112">Para obter as últimas alterações desde o fim de julho de 2018, quando os serviço Web foi disponibilizado, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="51fd0-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="51fd0-113">Como cliente, você pode usar esse serviço Web para:</span><span class="sxs-lookup"><span data-stu-id="51fd0-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="51fd0-114">Atualize os seus scripts do Windows PowerShell para obter dados de ponto de extremidade do Office 365 e modificar qualquer formatação dos dispositivos de rede.</span><span class="sxs-lookup"><span data-stu-id="51fd0-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="51fd0-115">Use essas informações para atualizar os arquivos PAC implantados nos computadores clientes.</span><span class="sxs-lookup"><span data-stu-id="51fd0-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="51fd0-116">Como fornecedor de dispositivos de perímetro de rede, é possível usar esse serviço Web para:</span><span class="sxs-lookup"><span data-stu-id="51fd0-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="51fd0-117">Criar e testar o software do dispositivo para baixar a lista de configuração automatizada.</span><span class="sxs-lookup"><span data-stu-id="51fd0-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="51fd0-118">Verificar a versão atual.</span><span class="sxs-lookup"><span data-stu-id="51fd0-118">Check for the current version.</span></span>
- <span data-ttu-id="51fd0-119">Obter as alterações atuais.</span><span class="sxs-lookup"><span data-stu-id="51fd0-119">Get the current changes.</span></span>

<span data-ttu-id="51fd0-120">Confira mais informações em:</span><span class="sxs-lookup"><span data-stu-id="51fd0-120">For additional information, see:</span></span>

- [<span data-ttu-id="51fd0-121">Comunicado de postagem no blog do Fórum da Comunidade de Tecnologia do Office 365</span><span class="sxs-lookup"><span data-stu-id="51fd0-121">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="51fd0-122">Fórum da Comunidade de Tecnologia do Office 365 para perguntas sobre o uso dos serviços Web</span><span class="sxs-lookup"><span data-stu-id="51fd0-122">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="51fd0-123">**Parâmetros comuns**</span><span class="sxs-lookup"><span data-stu-id="51fd0-123">**Common parameters**</span></span>

<span data-ttu-id="51fd0-124">Estes parâmetros são comuns a todos os métodos de serviço Web:</span><span class="sxs-lookup"><span data-stu-id="51fd0-124">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="51fd0-p104">**format=CSV | JSON** – parâmetro de cadeia de caracteres de consulta. Por padrão, o formato de dados retornado é JSON. Inclua este parâmetro opcional para retornar os dados no formato de valores separados por vírgula (CSV).</span><span class="sxs-lookup"><span data-stu-id="51fd0-p104">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="51fd0-p105">**ClientRequestId** – parâmetro de cadeia de caracteres de consulta. Um GUID necessário gerado por você para associação de cliente. Você deve gere um GUID para cada computador que chama um serviço Web. Não use os GUIDs mostrados nos exemplos a seguir, porque eles podem ser bloqueados pelo serviço Web no futuro. O formato GUID é _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, em que x representa um número hexadecimal. Para gerar um GUID, use o comando do Windows PowerShell[New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="51fd0-p105">**ClientRequestId** - Query string parameter. A required GUID that you generate for client association. You should generate a GUID for each machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="51fd0-134">**Método de versão da Web**</span><span class="sxs-lookup"><span data-stu-id="51fd0-134">**Version web method**</span></span>

<span data-ttu-id="51fd0-p106">As Microsoft atualiza as entradas de FQDN e o endereço IP do Office 365 ao final de cada mês e, eventualmente, fora do ciclo para atender a requisitos de suporte ou operacionais. Os dados de cada instância publicada recebem um número de versão. O método Web de versão permite pesquisar a última versão de cada instância de serviço do Office 365. Recomendamos verificar a versão diariamente, ou no máximo, a cada hora. As novas versões devem ser disponibilizadas no início de cada mês. Às vezes, devido a incidentes de suporte, segurança ou outros requisitos operacionais, novas versões são disponibilizadas ao longo do mês.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p106">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="51fd0-141">Há um parâmetro para o método de versão Web:</span><span class="sxs-lookup"><span data-stu-id="51fd0-141">There is one parameter for the version web method:</span></span>

- <span data-ttu-id="51fd0-p107">**AllVersions=true** – parâmetro de cadeia de caracteres de consulta. Por padrão, a versão retornada é a mais recente. Inclua esse parâmetro opcional para solicitar todas as versões publicadas.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p107">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span>
- <span data-ttu-id="51fd0-p108">**Format=JSON** | **CSV** | **RSS** – além dos formatos JSON e CSV, o método de versão Web também é compatível com RSS. Use-o com o parâmetro allVersions=true para solicitar um RSS feed que pode ser usado com o Outlook ou outros leitores de RSS.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p108">**Format=JSON** | **CSV** | **RSS** – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="51fd0-p109">**Instance** – parâmetro de roteamento. Este parâmetro opcional especifica a instância para a qual a versão deve ser retornada. Caso seja omitido, todas as instâncias serão retornadas. As instâncias válidas são: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p109">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="51fd0-p110">O resultado do método de versão Web pode ser um único registro ou uma matriz de registros. Os elementos de cada registro são:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p110">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="51fd0-153">instance – um nome curto da instância de serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="51fd0-153">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="51fd0-154">latest – a versão mais recente dos pontos de extremidade da instância especificada.</span><span class="sxs-lookup"><span data-stu-id="51fd0-154">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="51fd0-p111">versions – uma lista com todas as versões anteriores da instância especificada. Este elemento só será incluído se o parâmetro AllVersions for verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p111">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="51fd0-p112">Você pode usar o Microsoft Flow para receber notificações de email das alterações nos endereços IP e URLs. Confira [Usar o Microsoft Flow para receber um email das alterações em URLs e endereços IP do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="51fd0-p112">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="51fd0-159">**Exemplos:**</span><span class="sxs-lookup"><span data-stu-id="51fd0-159">**Examples:**</span></span>

<span data-ttu-id="51fd0-160">Exemplo 1 de URI de solicitação: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="51fd0-160">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="51fd0-p113">Esse URI retorna a última versão de cada instância de serviço do Office 365. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="51fd0-p114">O GUID para o parâmetro ClientRequestID nesses URIs são apenas um exemplo. Para experimentar os URIs do serviço Web, gere o seu próprio GUID. O GUIDs exibido nesses exemplos pode ser bloqueado pelo serviço Web no futuro.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="51fd0-166">Exemplo 2 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="51fd0-166">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="51fd0-p115">Esse URI retorna a última versão da instância de serviço especificada do Office 365. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="51fd0-169">Exemplo 3 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="51fd0-169">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="51fd0-p116">Este URI mostra os resultados no formato CSV. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="51fd0-172">Exemplo 4 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="51fd0-172">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="51fd0-p117">Este URI mostra todas as versões anteriores que foram publicadas para a instância de serviço do Office 365 em todo o mundo. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="51fd0-175">Exemplo 5 de URI de RSS feed: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="51fd0-175">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="51fd0-p118">Este URI mostra um RSS feed das versões publicadas que contêm links para a lista de alterações de cada versão. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="51fd0-178">**Método Web de pontos de extremidade**</span><span class="sxs-lookup"><span data-stu-id="51fd0-178">**Endpoints web method**</span></span>

<span data-ttu-id="51fd0-p119">O método Web de pontos de extremidade retorna todos os registros de intervalos de endereço IP e as URLs que compõem o serviço do Office 365. Embora os dados mais recentes do método Web de pontos de extremidade devam ser usados para a configuração de dispositivos de rede, os dados podem ser armazenados em cache por até 30 dias após a publicação, devido à notificação prévia fornecida para adições. Os parâmetros para o método Web de pontos de extremidade são:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p119">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="51fd0-p120">**ServiceAreas** – parâmetro de cadeia de caracteres de consulta. Uma lista separada por vírgulas de áreas de serviço. Os itens válidos são Common, Exchange, SharePoint, Skype. Como os itens de área de serviço do Common são um pré-requisito para todas as demais áreas de serviço, o serviço Web sempre os incluirá. Caso você não inclua esse parâmetro, todas as áreas de serviço serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p120">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="51fd0-p121">**TenantName** – parâmetro de cadeia de caracteres de consulta. O nome do locatário do Office 365. O serviço Web busca o nome fornecido e o insere em partes das URLs que incluem o nome do locatário. Se você não fornecer o nome do locatário, essas partes das URLs terão o caractere curinga (\*).</span><span class="sxs-lookup"><span data-stu-id="51fd0-p121">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="51fd0-p122">**NoIPv6** – parâmetro de cadeia de caracteres de consulta. Defina como verdadeiro para excluir os endereços IPv6 dos resultados, por exemplo, se você não usar o IPv6 na sua rede.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p122">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="51fd0-p123">**Instance** – parâmetro de roteamento. Esse parâmetro obrigatório especifica a instância para a qual os pontos de extremidade devem ser retornados. As instâncias válidas são: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p123">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="51fd0-p124">O resultado do método Web de pontos de extremidade é uma matriz de registros com cada registro representando um conjunto de pontos de extremidade. Os elementos de cada registro são:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p124">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="51fd0-198">id – o número de ID imutável do conjunto de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="51fd0-198">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="51fd0-199">serviceArea – a área de serviço que faz parte do: Common, Exchange, SharePoint ou Skype.</span><span class="sxs-lookup"><span data-stu-id="51fd0-199">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="51fd0-p125">urls – as URLs do conjunto de pontos de extremidade. Uma matriz JSON de registros DNS. Omitidas caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p125">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="51fd0-p126">tcpPorts – as portas TCP para o conjunto de pontos de extremidade. Os elementos de todas as portas são formatados como uma lista separada por vírgulas ou intervalos de portas separados por um hífen (-). As portas se aplicam a todos os endereços IP e todas as URLs do conjunto de pontos de extremidade para essa categoria. Omitidas caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p126">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="51fd0-p127">udpPorts – as portas UDP para os intervalos de endereço IP deste conjunto de pontos de extremidade. Omitidas caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p127">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="51fd0-p128">ips – os intervalos de endereço IP associados a esse conjunto de pontos de extremidade conforme associação com as portas TCP ou UDP listadas. Uma matriz JSON de intervalos de Endereço IP. Omitidos caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p128">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="51fd0-p129">categoria - A categoria conectividade para a configuração de ponto de extremidade. Os valores válidos são Otimizar, Permitir e Padrão. Se você estiver usando os dados do ponto de extremidade para pesquisar a categoria de um endereço IP ou URL, é possível que sua consulta possa retornar diversas categorias. Há alguns motivos para isso acontecer. Nesses casos, você deve seguir as recomendações para a categoria de maior prioridade. Por exemplo, se o ponto de extremidade aparecer tanto em Otimizar quanto em Permitir, você deve seguir os requisitos de Otimizar. Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p129">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span> 
- <span data-ttu-id="51fd0-219">expressRoute – Verdadeiro ou Falso se esse conjunto de pontos de extremidade for roteado pelo ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="51fd0-219">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="51fd0-p130">required – Verdadeiro se esse conjunto de pontos de extremidade precisar de conectividade com o Office 365 para ter suporte. Falso se o conjunto de pontos de extremidade for opcional.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p130">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="51fd0-p131">notes – para pontos de extremidade opcionais, este texto descreve a funcionalidade do Office 365 que não estará disponível se os endereços IP ou URLs deste conjunto de pontos de extremidade não puderem ser acessados na camada de rede. Omitidos caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p131">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="51fd0-224">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="51fd0-224">Examples:</span></span>

<span data-ttu-id="51fd0-225">Exemplo 1 de URI de solicitação: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="51fd0-225">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="51fd0-p132">Esse URI obtém todos os pontos de extremidade da instância do Office 365 em todo o mundo para todas as cargas de trabalho. Exemplo de resultado mostrando um trecho da saída:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p132">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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
...
```

<span data-ttu-id="51fd0-228">Os conjuntos de ponto de extremidade adicionais não são incluídos neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="51fd0-228">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="51fd0-229">Exemplo 2 de URI de solicitação: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="51fd0-229">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="51fd0-230">Esse exemplo obtém pontos de extremidade da instância do Office 365 em todo o mundo apenas para o Exchange Online e dependências.</span><span class="sxs-lookup"><span data-stu-id="51fd0-230">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="51fd0-231">O resultado do exemplo 2 é semelhante ao do exemplo 1, exceto que os resultados não incluirão pontos de extremidade do SharePoint Online ou do Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="51fd0-231">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="51fd0-232">Método Web de alterações</span><span class="sxs-lookup"><span data-stu-id="51fd0-232">Changes web method</span></span>

<span data-ttu-id="51fd0-p133">O método Web de alterações retorna as atualizações mais recentes publicadas. Normalmente, são as alterações do mês anterior de URLs e dos intervalos de endereços IP. As alterações mais importantes a serem processadas ocorrem quando novas URLs ou endereços IP são adicionados, uma vez que a falha ao adicionar um endereço IP à lista de controle de acesso do firewall ou a uma URL a uma lista de bypass de servidores proxy pode causar uma interrupção para usuários do Office 365 por trás desse dispositivo de rede. Apesar dos requisitos operacionais, as operações _Adicionar_ são adicionadas com uma notificação 30 dias antes da interrupção.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p133">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="51fd0-237">O parâmetro para o método Web de alterações é:</span><span class="sxs-lookup"><span data-stu-id="51fd0-237">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="51fd0-p134">**Version** – parâmetro obrigatório de roteamento de URL. A versão implementada atualmente e aquela a partir da qual você deseja ver as alterações. O formato é _AAAAMMDDNN_.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p134">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is _YYYYMMDDNN_.</span></span>

<span data-ttu-id="51fd0-p135">O resultado do método Web de alterações é uma matriz de registros com cada registro representando uma alteração em uma versão específica dos pontos de extremidade. Os elementos de cada registro são:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p135">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="51fd0-243">id – a ID imutável do registro de alterações.</span><span class="sxs-lookup"><span data-stu-id="51fd0-243">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="51fd0-p136">endpointSetId – a ID do registro do conjunto de pontos de extremidade que é alterado. Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p136">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="51fd0-p137">disposition – pode ser de alteração, adição ou remoção e descreve o que a alteração fez com o registro de conjunto de pontos de extremidade. Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p137">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="51fd0-p138">version – a versão do conjunto de pontos de extremidade em que a alteração foi introduzida. Os números de versões estão no formato _AAAAMMDDNN_, em que NN é um número natural incrementado caso existam várias versões a serem publicadas em um único dia.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p138">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="51fd0-p139">previous – uma estrutura que detalha valores anteriores de elementos alterados no conjunto de pontos de extremidade. Isso não será incluído em novos conjuntos de pontos de extremidade adicionados. Inclui tcpPorts, udpPorts, ExpressRoute, categoria, obrigatório, observações.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p139">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="51fd0-p140">current – uma estrutura que detalha valores atualizados de elementos de alteração no conjunto de pontos de extremidade. Inclui tcpPorts, udpPorts, ExpressRoute, categoria, obrigatório, observações.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p140">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="51fd0-p141">add – uma subestrutura que detalha os itens a serem adicionados às coleções do conjunto de pontos de extremidade. Omitida caso não haja nenhuma adição.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p141">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="51fd0-257">effectiveDate – define os dados de quando as adições estarão disponíveis no serviço.</span><span class="sxs-lookup"><span data-stu-id="51fd0-257">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="51fd0-258">ips – os itens a serem adicionados à matriz ips.</span><span class="sxs-lookup"><span data-stu-id="51fd0-258">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="51fd0-259">urls – os itens a serem adicionados à matriz urls.</span><span class="sxs-lookup"><span data-stu-id="51fd0-259">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="51fd0-p142">remove – uma subestrutura que detalha os itens a serem removidos do conjunto de pontos de extremidade. Omitida se não houver nenhuma remoção.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p142">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
  - <span data-ttu-id="51fd0-262">ips – os itens a serem removidos da matriz ips.</span><span class="sxs-lookup"><span data-stu-id="51fd0-262">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="51fd0-263">urls – os itens a serem removidos da matriz urls.</span><span class="sxs-lookup"><span data-stu-id="51fd0-263">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="51fd0-264">**Exemplos:**</span><span class="sxs-lookup"><span data-stu-id="51fd0-264">**Examples:**</span></span>

<span data-ttu-id="51fd0-265">Exemplo 1 de URI de solicitação: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="51fd0-265">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="51fd0-p143">Solicita todas as alterações anteriores da instância do serviço do Office 365 em todo o mundo. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p143">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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
...
```

<span data-ttu-id="51fd0-268">Exemplo 2 de URI de solicitação: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="51fd0-268">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="51fd0-p144">Solicita as alterações desde a versão especificada da instância do Office 365 em todo o mundo. Nesse caso, a versão especificada é a mais recente. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p144">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="51fd0-272">**Exemplo de Script do Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="51fd0-272">**Example PowerShell Script**</span></span>

<span data-ttu-id="51fd0-p145">Esse é um script do Windows PowerShell que você pode executar para ver se há ações que você precisa realizar em relação aos dados atualizados. Esse script verifica o número da versão dos pontos de extremidade de instâncias do Office 365 em todo o mundo. Quando houver uma alteração, ele baixará os pontos de extremidade e os filtros dos pontos de extremidade das categorias &quot;Permitir&quot; e &quot;Otimizar&quot;. Ele também usa um ClientRequestId exclusivo em várias chamadas e salva a última versão encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se há alguma atualização da versão.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p145">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the &quot;Allow&quot; and &quot;Optimize&quot; category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="51fd0-278">**Exemplo de Script do Python**</span><span class="sxs-lookup"><span data-stu-id="51fd0-278">**Example Python Script**</span></span>

<span data-ttu-id="51fd0-p146">Esse é um script do Python, testado com o Python 3.6.3 no Windows 10, que você pode executar para ver se há ações que você precisa realizar em relação aos dados atualizados. Esse script verifica o número da versão dos pontos de extremidade de instâncias do Office 365 em todo o mundo. Quando houver uma alteração, ele baixará os pontos de extremidade e os filtros dos pontos de extremidade das categorias _Permitir_ e _Otimizar_. Ele também usa um ClientRequestId exclusivo em várias chamadas e salva a última versão encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se há alguma atualização da versão.</span><span class="sxs-lookup"><span data-stu-id="51fd0-p146">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="51fd0-284">**Controle de versão da interface de serviços Web**</span><span class="sxs-lookup"><span data-stu-id="51fd0-284">**Web Service interface versioning**</span></span>

<span data-ttu-id="51fd0-p147">No futuro, podem ser necessárias atualizações de parâmetros ou de resultados desses métodos de serviço Web. Após a publicação da versão de disponibilidade geral desses serviços Web, a Microsoft fará os esforços cabíveis para enviar previamente notificações sobre atualizações do material para o serviço Web. Quando acreditar que uma atualização exigirá alterações dos clientes usando o serviço Web, a Microsoft manterá a versão anterior (uma versão antes) do serviço Web disponível por pelo menos doze (12) meses após o lançamento da nova versão. Os clientes que não fizerem a atualização durante esse período, perderão o acesso ao serviço Web e aos seus métodos. É preciso garantir que os clientes do serviço Web continuem trabalhando sem erros se as seguintes alterações forem feitas à assinatura da interface da Web:</span><span class="sxs-lookup"><span data-stu-id="51fd0-p147">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="51fd0-290">Adição de um novo parâmetro opcional a um método Web existente que não precise ser fornecido por clientes mais antigos e que não afete os resultados recebidos por um cliente mais antigo.</span><span class="sxs-lookup"><span data-stu-id="51fd0-290">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="51fd0-291">Adição de um novo atributo nomeado em um dos itens do REST de resposta ou em colunas adicionais para o CSV de resposta.</span><span class="sxs-lookup"><span data-stu-id="51fd0-291">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="51fd0-292">Adição de um novo método Web com um novo nome que não é chamado pelos clientes mais antigos.</span><span class="sxs-lookup"><span data-stu-id="51fd0-292">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="related-topics"></a><span data-ttu-id="51fd0-293">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="51fd0-293">Related Topics</span></span>
  
[<span data-ttu-id="51fd0-294">URLs e intervalos de endereços IP do Office 365</span><span class="sxs-lookup"><span data-stu-id="51fd0-294">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="51fd0-295">Perguntas frequentes sobre pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="51fd0-295">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="51fd0-296">Princípios de conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="51fd0-296">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="51fd0-297">Rede do Office 365 e ajuste de desempenho</span><span class="sxs-lookup"><span data-stu-id="51fd0-297">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="51fd0-298">Conectividade de rede para Office 365</span><span class="sxs-lookup"><span data-stu-id="51fd0-298">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="51fd0-299">Qualidade da mídia e desempenho de conectividade de rede no Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="51fd0-299">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="51fd0-300">Como otimizar a sua rede para o Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="51fd0-300">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="51fd0-301">Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho</span><span class="sxs-lookup"><span data-stu-id="51fd0-301">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="51fd0-302">Plano de solução de problemas de desempenho do Office 365</span><span class="sxs-lookup"><span data-stu-id="51fd0-302">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
