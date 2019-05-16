---
title: URL do serviço Web e endereço IP do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/7/2019
audience: ITPro
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
ms.openlocfilehash: fcef7a6a175b043639275fedc77faaa689f0e7d5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069727"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="a4535-104">URL do serviço Web e endereço IP do Office 365</span><span class="sxs-lookup"><span data-stu-id="a4535-104">Office 365 IP Address and URL Web service</span></span>

<span data-ttu-id="a4535-p102">Para você identificar e diferenciar melhor o tráfego de rede do Office 365, um novo serviço Web publica pontos de extremidade do Office 365, permitindo avaliar, configurar e se manter atualizado em relação às alterações com mais facilidade. Esse novo serviço Web substitui os arquivos XML para download que estão disponíveis atualmente. A descontinuação do formato XML está prevista para 2 de outubro de 2018.</span><span class="sxs-lookup"><span data-stu-id="a4535-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="a4535-p103">Como cliente ou fornecedor de dispositivos de perímetro de rede, você pode criar com o novo serviço Web baseado em REST para as entradas FQDN e os endereços IP do Office 365. É possível acessar os dados diretamente de um navegador da Web usando essas URLs.</span><span class="sxs-lookup"><span data-stu-id="a4535-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="a4535-110">Para ter a última versão dos intervalos de endereços IP e URLs do Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a4535-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="a4535-111">Para os dados na página de intervalos de endereços IP e URLs do Office 365 para firewalls e servidores proxy, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a4535-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="a4535-112">Para obter as últimas alterações desde o fim de julho de 2018, quando os serviço Web foi disponibilizado, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a4535-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="a4535-113">Como cliente, você pode usar esse serviço Web para:</span><span class="sxs-lookup"><span data-stu-id="a4535-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="a4535-114">Atualize os seus scripts do Windows PowerShell para obter dados de ponto de extremidade do Office 365 e modificar qualquer formatação dos dispositivos de rede.</span><span class="sxs-lookup"><span data-stu-id="a4535-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="a4535-115">Use essas informações para atualizar os arquivos PAC implantados nos computadores clientes.</span><span class="sxs-lookup"><span data-stu-id="a4535-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="a4535-116">Como fornecedor de dispositivos de perímetro de rede, é possível usar esse serviço Web para:</span><span class="sxs-lookup"><span data-stu-id="a4535-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="a4535-117">Criar e testar o software do dispositivo para baixar a lista de configuração automatizada.</span><span class="sxs-lookup"><span data-stu-id="a4535-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="a4535-118">Verificar a versão atual.</span><span class="sxs-lookup"><span data-stu-id="a4535-118">Check for the current version.</span></span>
- <span data-ttu-id="a4535-119">Obter as alterações atuais.</span><span class="sxs-lookup"><span data-stu-id="a4535-119">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="a4535-120">Se você estiver usando o Azure ExpressRoute para se conectar ao Office 365, confira [Azure ExpressRoute para Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) para se familiarizar com os serviços do Office 365 com suporte no Azure ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="a4535-120">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="a4535-121">Além disso, veja o artigo [URLs e intervalos de endereços IP do Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) para entender quais solicitações de rede para aplicativos do Office 365 exigem conectividade com a Internet.</span><span class="sxs-lookup"><span data-stu-id="a4535-121">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="a4535-122">Isso ajudará a configurar melhor seus dispositivos de segurança de perímetro.</span><span class="sxs-lookup"><span data-stu-id="a4535-122">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="a4535-123">Confira mais informações em:</span><span class="sxs-lookup"><span data-stu-id="a4535-123">For additional information, see:</span></span>

- [<span data-ttu-id="a4535-124">Comunicado de postagem no blog do Fórum da Comunidade de Tecnologia do Office 365</span><span class="sxs-lookup"><span data-stu-id="a4535-124">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="a4535-125">Fórum da Comunidade de Tecnologia do Office 365 para perguntas sobre o uso dos serviços Web</span><span class="sxs-lookup"><span data-stu-id="a4535-125">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="a4535-126">Parâmetros comuns</span><span class="sxs-lookup"><span data-stu-id="a4535-126">Common parameters</span></span>

<span data-ttu-id="a4535-127">Estes parâmetros são comuns a todos os métodos de serviço Web:</span><span class="sxs-lookup"><span data-stu-id="a4535-127">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="a4535-128">**format=<JSON | CSV>** - Por padrão, o formato de dados retornado é JSON.</span><span class="sxs-lookup"><span data-stu-id="a4535-128">**format=<JSON | CSV>** - By default, the returned data format is JSON.</span></span> <span data-ttu-id="a4535-129">Use este parâmetro opcional para retornar os dados no formato de valores separados por vírgula (CSV).</span><span class="sxs-lookup"><span data-stu-id="a4535-129">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="a4535-130">**ClientRequestId=\<guid>** - Um GUID necessário que você gera para associação de clientes.</span><span class="sxs-lookup"><span data-stu-id="a4535-130">**ClientRequestId=\<guid>** - A required GUID that you generate for client association.</span></span> <span data-ttu-id="a4535-131">Você deve gerar um GUID para cada computador que chama o serviço da web.</span><span class="sxs-lookup"><span data-stu-id="a4535-131">You should generate a GUID for each machine that calls the web service.</span></span> <span data-ttu-id="a4535-132">Não use os GUIDs mostrados nos exemplos a seguir porque eles podem ser bloqueados pelo serviço da Web no futuro.</span><span class="sxs-lookup"><span data-stu-id="a4535-132">Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future.</span></span> <span data-ttu-id="a4535-133">O formato GUID é_ xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, em que x representa um número hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a4535-133">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span> <span data-ttu-id="a4535-134">Para gerar um GUID, use o comando [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4535-134">To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="a4535-135">Método da web de versão</span><span class="sxs-lookup"><span data-stu-id="a4535-135">Version web method</span></span>

<span data-ttu-id="a4535-p107">As Microsoft atualiza as entradas de FQDN e o endereço IP do Office 365 ao final de cada mês e, eventualmente, fora do ciclo para atender a requisitos de suporte ou operacionais. Os dados de cada instância publicada recebem um número de versão. O método Web de versão permite pesquisar a última versão de cada instância de serviço do Office 365. Recomendamos verificar a versão diariamente, ou no máximo, a cada hora. As novas versões devem ser disponibilizadas no início de cada mês. Às vezes, devido a incidentes de suporte, segurança ou outros requisitos operacionais, novas versões são disponibilizadas ao longo do mês.</span><span class="sxs-lookup"><span data-stu-id="a4535-p107">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="a4535-142">Os parâmetros para o método da web de versão são:</span><span class="sxs-lookup"><span data-stu-id="a4535-142">Parameters for the version web method are:</span></span>

- <span data-ttu-id="a4535-143">**AllVersions=<true | false>** - Por padrão, a versão retornada é a mais recente.</span><span class="sxs-lookup"><span data-stu-id="a4535-143">**AllVersions=<true | false>** - By default, the version returned is the latest.</span></span> <span data-ttu-id="a4535-144">Inclua este parâmetro opcional para solicitar todas as versões publicadas desde que o serviço da Web foi lançado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="a4535-144">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="a4535-145">**Format=<JSON | CSV | RSS>** – Além dos formatos JSON e CSV, o método da web de versão também é compatível com RSS.</span><span class="sxs-lookup"><span data-stu-id="a4535-145">**Format=<JSON | CSV | RSS>** – In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="a4535-146">Você pode usar esse parâmetro opcional junto com o parâmetro _AllVersions=true_ para solicitar um feed RSS que possa ser usado com o Outlook ou outros leitores de RSS.</span><span class="sxs-lookup"><span data-stu-id="a4535-146">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="a4535-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - Este parâmetro opcional especifica a instância para o retorno da versão.</span><span class="sxs-lookup"><span data-stu-id="a4535-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="a4535-148">Se omitido, todas as instâncias serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="a4535-148">If omitted, all instances are returned.</span></span> <span data-ttu-id="a4535-149">As instâncias válidas são: em todo o mundo, China, Alemanha, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="a4535-149">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="a4535-p111">A versão do método Web não é limitado por taxa e nunca retornará o código de resposta HTTP 429. A resposta à versão do método Web inclui um cabeçalho de controle de cache que recomenda o armazenamento em cache dos dados por 1 hora. O resultado do método de versão Web pode ser um único registro ou uma matriz de registros. Os elementos de cada registro são:</span><span class="sxs-lookup"><span data-stu-id="a4535-p111">The version web method is not rate limited and does not ever return 429 HTTP Response Codes. The response to the version web method does include a cache-control header recommending caching of the data for 1 hour. The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="a4535-154">instance – um nome curto da instância de serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a4535-154">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="a4535-155">latest – a versão mais recente dos pontos de extremidade da instância especificada.</span><span class="sxs-lookup"><span data-stu-id="a4535-155">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="a4535-p112">versions – uma lista com todas as versões anteriores da instância especificada. Este elemento só será incluído se o parâmetro AllVersions for verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="a4535-p112">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="a4535-p113">Você pode usar o Microsoft Flow para receber notificações de email das alterações nos endereços IP e URLs. Confira [Usar o Microsoft Flow para receber um email das alterações em URLs e endereços IP do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="a4535-p113">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="a4535-160">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="a4535-160">Examples:</span></span>

<span data-ttu-id="a4535-161">Exemplo 1 de URI de solicitação: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a4535-161">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a4535-p114">Esse URI retorna a última versão de cada instância de serviço do Office 365. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="a4535-p114">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="a4535-p115">O GUID para o parâmetro ClientRequestID nesses URIs são apenas um exemplo. Para experimentar os URIs do serviço Web, gere o seu próprio GUID. O GUIDs exibido nesses exemplos pode ser bloqueado pelo serviço Web no futuro.</span><span class="sxs-lookup"><span data-stu-id="a4535-p115">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="a4535-167">Exemplo 2 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a4535-167">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a4535-p116">Esse URI retorna a última versão da instância de serviço especificada do Office 365. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="a4535-p116">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="a4535-170">Exemplo 3 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a4535-170">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a4535-p117">Este URI mostra os resultados no formato CSV. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="a4535-p117">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="a4535-173">Exemplo 4 de URI de solicitação: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a4535-173">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a4535-p118">Este URI mostra todas as versões anteriores que foram publicadas para a instância de serviço do Office 365 em todo o mundo. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="a4535-p118">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="a4535-176">Exemplo 5 de URI de RSS feed: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="a4535-176">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="a4535-p119">Este URI mostra um RSS feed das versões publicadas que contêm links para a lista de alterações de cada versão. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="a4535-p119">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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
```

## <a name="endpoints-web-method"></a><span data-ttu-id="a4535-179">Método da Web de pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="a4535-179">Endpoints web method</span></span>

<span data-ttu-id="a4535-180">O método da Web de pontos de extremidade retorna todos os registros para intervalos de endereços IP e URLs que compõem o serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a4535-180">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="a4535-181">Enquanto os dados mais recentes do método da Web de pontos de extremidade devem ser usados para a configuração de dispositivos de rede, os dados podem ser armazenados em cache por até 30 dias após sua publicação devido ao aviso antecipado fornecido para adições.</span><span class="sxs-lookup"><span data-stu-id="a4535-181">While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions.</span></span> <span data-ttu-id="a4535-182">Recomendamos que você chame o método da Web de pontos de extremidade somente quando o método da web da versão indicar que uma nova versão dos dados está disponível.</span><span class="sxs-lookup"><span data-stu-id="a4535-182">We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available.</span></span>

<span data-ttu-id="a4535-183">Os parâmetros para o método da Web de pontos de extremidade são:</span><span class="sxs-lookup"><span data-stu-id="a4535-183">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="a4535-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - Uma lista de áreas de serviço separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="a4535-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - A comma-separated list of service areas.</span></span> <span data-ttu-id="a4535-185">Os itens válidos são _Common_, _Exchange_, _SharePoint_ e _Skype_.</span><span class="sxs-lookup"><span data-stu-id="a4535-185">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="a4535-186">Como os itens da área de serviço comum são um pré-requisito para todas as outras áreas de serviço, o serviço da Web sempre os incluirá.</span><span class="sxs-lookup"><span data-stu-id="a4535-186">Because Common service area items are a prerequisite for all other service areas, the web service will always include them.</span></span> <span data-ttu-id="a4535-187">Se você não incluir esse parâmetro, todas as áreas de serviço serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="a4535-187">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="a4535-188">**TenantName=<tenant_name>** - Seu nome de locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a4535-188">**TenantName=<tenant_name>** - Your Office 365 tenant name.</span></span> <span data-ttu-id="a4535-189">O serviço da web insere o seu nome fornecido em partes de URLs que incluem o nome do locatário.</span><span class="sxs-lookup"><span data-stu-id="a4535-189">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="a4535-190">Se você não fornecer um nome de locatário, essas partes das URLs terão o caractere curinga (\*).</span><span class="sxs-lookup"><span data-stu-id="a4535-190">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="a4535-191">**NoIPv6=<true | false>** - Defina como true para excluir endereços IPv6 dos resultados; por exemplo, se você não usar o IPv6 em sua rede.</span><span class="sxs-lookup"><span data-stu-id="a4535-191">**NoIPv6=<true | false>** - Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="a4535-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - Este parâmetro obrigatório especifica a instância para a qual retornar os terminais.</span><span class="sxs-lookup"><span data-stu-id="a4535-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This required parameter specifies the instance to return the endpoints for.</span></span> <span data-ttu-id="a4535-193">As instâncias válidas são: _Mundialmente_, _China_, _Alemanha_, _USGovDoD_ e _USGovGCCHigh_.</span><span class="sxs-lookup"><span data-stu-id="a4535-193">Valid instances are: _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.</span></span>

<span data-ttu-id="a4535-194">Se você chamar o método da Web de pontos de extremidade um grande número de vezes a partir do mesmo endereço IP do cliente, poderá receber o código de resposta HTTP 429 (Excesso de solicitações).</span><span class="sxs-lookup"><span data-stu-id="a4535-194">If you call the endpoints web method a large number of times from the same client IP address, you may receive HTTP response code 429 (Too Many Requests).</span></span> <span data-ttu-id="a4535-195">A maioria das pessoas nunca verá isso.</span><span class="sxs-lookup"><span data-stu-id="a4535-195">Most people will never see this.</span></span> <span data-ttu-id="a4535-196">Se você receber esse código de resposta, aguarde uma hora antes de repetir sua solicitação.</span><span class="sxs-lookup"><span data-stu-id="a4535-196">If you get this response code, wait 1 hour before repeating your request.</span></span> <span data-ttu-id="a4535-197">Planeje chamar apenas o método da Web de pontos de extremidade quando o método da web de versão indicar que há uma nova versão disponível.</span><span class="sxs-lookup"><span data-stu-id="a4535-197">Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span>

<span data-ttu-id="a4535-p125">O resultado do método Web de pontos de extremidade é uma matriz de registros com cada registro representando um conjunto de pontos de extremidade. Os elementos de cada registro são:</span><span class="sxs-lookup"><span data-stu-id="a4535-p125">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="a4535-200">id – o número de ID imutável do conjunto de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a4535-200">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="a4535-201">serviceArea – a área de serviço que faz parte do: Common, Exchange, SharePoint ou Skype.</span><span class="sxs-lookup"><span data-stu-id="a4535-201">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="a4535-p126">urls – as URLs do conjunto de pontos de extremidade. Uma matriz JSON de registros DNS. Omitidas caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="a4535-p126">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="a4535-p127">tcpPorts – as portas TCP para o conjunto de pontos de extremidade. Os elementos de todas as portas são formatados como uma lista separada por vírgulas ou intervalos de portas separados por um hífen (-). As portas se aplicam a todos os endereços IP e todas as URLs do conjunto de pontos de extremidade para essa categoria. Omitidas caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="a4535-p127">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="a4535-p128">udpPorts – as portas UDP para os intervalos de endereço IP deste conjunto de pontos de extremidade. Omitidas caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="a4535-p128">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="a4535-p129">ips – os intervalos de endereço IP associados a esse conjunto de pontos de extremidade conforme associação com as portas TCP ou UDP listadas. Uma matriz JSON de intervalos de Endereço IP. Omitidos caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="a4535-p129">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="a4535-p130">categoria - A categoria conectividade para a configuração de ponto de extremidade. Os valores válidos são Otimizar, Permitir e Padrão. Se você estiver usando os dados do ponto de extremidade para pesquisar a categoria de um endereço IP ou URL, é possível que sua consulta possa retornar diversas categorias. Há alguns motivos para isso acontecer. Nesses casos, você deve seguir as recomendações para a categoria de maior prioridade. Por exemplo, se o ponto de extremidade aparecer tanto em Otimizar quanto em Permitir, você deve seguir os requisitos de Otimizar. Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a4535-p130">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span>
- <span data-ttu-id="a4535-221">expressRoute – Verdadeiro ou Falso se esse conjunto de pontos de extremidade for roteado pelo ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="a4535-221">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="a4535-p131">required – Verdadeiro se esse conjunto de pontos de extremidade precisar de conectividade com o Office 365 para ter suporte. Falso se o conjunto de pontos de extremidade for opcional.</span><span class="sxs-lookup"><span data-stu-id="a4535-p131">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="a4535-p132">notes – para pontos de extremidade opcionais, este texto descreve a funcionalidade do Office 365 que não estará disponível se os endereços IP ou URLs deste conjunto de pontos de extremidade não puderem ser acessados na camada de rede. Omitidos caso estejam em branco.</span><span class="sxs-lookup"><span data-stu-id="a4535-p132">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="a4535-226">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="a4535-226">Examples:</span></span>

<span data-ttu-id="a4535-227">Exemplo 1 de URI de solicitação: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a4535-227">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a4535-p133">Esse URI obtém todos os pontos de extremidade da instância do Office 365 em todo o mundo para todas as cargas de trabalho. Exemplo de resultado mostrando um trecho da saída:</span><span class="sxs-lookup"><span data-stu-id="a4535-p133">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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

<span data-ttu-id="a4535-230">Os conjuntos de ponto de extremidade adicionais não são incluídos neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="a4535-230">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="a4535-231">Exemplo 2 de URI de solicitação: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a4535-231">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a4535-232">Esse exemplo obtém pontos de extremidade da instância do Office 365 em todo o mundo apenas para o Exchange Online e dependências.</span><span class="sxs-lookup"><span data-stu-id="a4535-232">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="a4535-233">O resultado do exemplo 2 é semelhante ao do exemplo 1, exceto que os resultados não incluirão pontos de extremidade do SharePoint Online ou do Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="a4535-233">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="a4535-234">Método Web de alterações</span><span class="sxs-lookup"><span data-stu-id="a4535-234">Changes web method</span></span>

<span data-ttu-id="a4535-p134">O método Web de alterações retorna as atualizações mais recentes publicadas. Normalmente, são as alterações do mês anterior de URLs e dos intervalos de endereços IP. As alterações mais importantes a serem processadas ocorrem quando novas URLs ou endereços IP são adicionados, uma vez que a falha ao adicionar um endereço IP à lista de controle de acesso do firewall ou a uma URL a uma lista de bypass de servidores proxy pode causar uma interrupção para usuários do Office 365 por trás desse dispositivo de rede. Apesar dos requisitos operacionais, as operações _Adicionar_ são adicionadas com uma notificação 30 dias antes da interrupção.</span><span class="sxs-lookup"><span data-stu-id="a4535-p134">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="a4535-239">O parâmetro necessário para o método da web de alterações é:</span><span class="sxs-lookup"><span data-stu-id="a4535-239">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="a4535-240">**Version=\<YYYYMMDDNN>** - Parâmetro de rota de URL obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a4535-240">**Version=\<YYYYMMDDNN>** - Required URL route parameter.</span></span> <span data-ttu-id="a4535-241">Este valor deve ser a versão que você tem implementada atualmente.</span><span class="sxs-lookup"><span data-stu-id="a4535-241">This value should be the version that you have currently implemented.</span></span> <span data-ttu-id="a4535-242">O serviço da Web retornará as alterações desde essa versão.</span><span class="sxs-lookup"><span data-stu-id="a4535-242">The web service will return the changes since that version.</span></span> <span data-ttu-id="a4535-243">O formato é _YYYYMMDDNN_, em que _NN_ é um número natural incrementado, se houver várias versões que precisem ser publicadas em um único dia, com _00_ representando a primeira atualização de um determinado dia.</span><span class="sxs-lookup"><span data-stu-id="a4535-243">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="a4535-244">O serviço da web requer que o parâmetro de _versão_ contenha exatamente 10 dígitos.</span><span class="sxs-lookup"><span data-stu-id="a4535-244">The web service requires the _version_ parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="a4535-245">O método da Web de alterações é limitado por taxa da mesma forma que o método da web de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a4535-245">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="a4535-246">Se você receber um código de resposta HTTP 429, espere 1 hora antes de repetir sua solicitação.</span><span class="sxs-lookup"><span data-stu-id="a4535-246">If you receive a 429 HTTP response code, wait 1 hour before repeating your request.</span></span>

<span data-ttu-id="a4535-p137">O resultado do método Web de alterações é uma matriz de registros com cada registro representando uma alteração em uma versão específica dos pontos de extremidade. Os elementos de cada registro são:</span><span class="sxs-lookup"><span data-stu-id="a4535-p137">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="a4535-249">id – a ID imutável do registro de alterações.</span><span class="sxs-lookup"><span data-stu-id="a4535-249">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="a4535-250">endpointSetId - O ID do registro do conjunto de pontos de extremidade que é alterado.</span><span class="sxs-lookup"><span data-stu-id="a4535-250">endpointSetId - The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="a4535-251">disposição - Pode ser de alteração, adição ou remoção e descreve o que a alteração fez no registro do conjunto de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a4535-251">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
- <span data-ttu-id="a4535-p138">impacto - Nem todas as alterações serão igualmente importantes para todos os ambientes. Isso descreve o impacto esperado para um ambiente de perímetro de rede corporativa como resultado dessa alteração. Este atributo está incluído apenas nos registros de alterações da versão **2018112800** e posterior. As opções para o impacto são:</span><span class="sxs-lookup"><span data-stu-id="a4535-p138">impact - Not all changes will be equally important to every environment. This describes the expected impact to an enterprise network perimeter environment as a result of this change. This attribute is included only in change records of version **2018112800** and later. Options for the impact are:</span></span>
  - <span data-ttu-id="a4535-p139">AddedIp – um endereço de IP foi adicionado ao Office 365 e estará ativo no serviço em breve. Isso representa uma alteração que você precisa realizar em um firewall ou em outro dispositivo de perímetro de rede de camada 3. Se você não adicionar isso antes de começar a usá-lo, você pode observar uma interrupção.</span><span class="sxs-lookup"><span data-stu-id="a4535-p139">AddedIp – An IP Address was added to Office 365 and will be live on the service soon. This represents a change you need to take on a firewall or other layer 3 network perimeter device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a4535-259">AddedUrl - Uma URL foi adicionada ao Office 365 e será exibida no serviço em breve.</span><span class="sxs-lookup"><span data-stu-id="a4535-259">AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="a4535-260">Isso representa uma mudança que você precisa fazer em um servidor de proxy ou dispositivo de perímetro de rede de análise de URL.</span><span class="sxs-lookup"><span data-stu-id="a4535-260">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="a4535-261">Se você não adicionar isso antes de começar a usá-lo, talvez haja uma interrupção.</span><span class="sxs-lookup"><span data-stu-id="a4535-261">If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a4535-p141">AddedIpAndUrl - um endereço de IP e URL foram adicionados. Isso representa uma alteração que você precisa realizar em um dispositivo de camada 3 firewall ou em um servidor proxy ou dispositivo de análise da URL. Se você não adicionar isso antes de começar a usá-lo, você pode observar uma interrupção.</span><span class="sxs-lookup"><span data-stu-id="a4535-p141">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a4535-p142">RemovedIpOrUrl, pelo menos um endereço IP ou URL foi removido do Office 365. Você deve remover os pontos de extremidade de rede nos seus dispositivos de perímetro, mas não há nenhuma data limite para você fazer isso.</span><span class="sxs-lookup"><span data-stu-id="a4535-p142">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  - <span data-ttu-id="a4535-p143">ChangedIsExpressRoute – o atributo de suporte do ExpressRoute foi modificado. Se você usar o ExpressRoute será necessário tomar medidas dependendo da configuração.</span><span class="sxs-lookup"><span data-stu-id="a4535-p143">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  - <span data-ttu-id="a4535-p144">MovedIpOrUrl – Movemos um endereço IP ou uma Url entre esse conjunto de ponto de extremidade e outro. Geralmente, nenhuma ação é necessária.</span><span class="sxs-lookup"><span data-stu-id="a4535-p144">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span>
  - <span data-ttu-id="a4535-p145">RemovedDuplicateIpOrUrl – Removemos um endereço IP ou uma Url duplicados, mas ele ainda é publicado para o Office 365. Geralmente, nenhuma ação é necessária.</span><span class="sxs-lookup"><span data-stu-id="a4535-p145">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span>
  - <span data-ttu-id="a4535-273">OtherNonPriorityChanges – alteramos algo menos crítico que todas as opções como um campo de anotações</span><span class="sxs-lookup"><span data-stu-id="a4535-273">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="a4535-p146">version – a versão do conjunto de pontos de extremidade em que a alteração foi introduzida. Os números de versões estão no formato _AAAAMMDDNN_, em que NN é um número natural incrementado caso existam várias versões a serem publicadas em um único dia.</span><span class="sxs-lookup"><span data-stu-id="a4535-p146">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="a4535-276">previous - Uma subestrutura detalhando os valores anteriores de elementos alterados no conjunto de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a4535-276">previous - A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="a4535-277">Isso não será incluído para conjuntos de pontos de extremidade recém-adicionados.</span><span class="sxs-lookup"><span data-stu-id="a4535-277">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="a4535-278">Inclui _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ e _notes_.</span><span class="sxs-lookup"><span data-stu-id="a4535-278">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="a4535-279">current - Uma subestrutura detalhando valores atualizados de elementos de alterações no conjunto de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a4535-279">current - A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="a4535-280">Inclui _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ e _notes_.</span><span class="sxs-lookup"><span data-stu-id="a4535-280">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="a4535-p149">add – uma subestrutura que detalha os itens a serem adicionados às coleções do conjunto de pontos de extremidade. Omitida caso não haja nenhuma adição.</span><span class="sxs-lookup"><span data-stu-id="a4535-p149">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="a4535-283">effectiveDate – define os dados de quando as adições estarão disponíveis no serviço.</span><span class="sxs-lookup"><span data-stu-id="a4535-283">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="a4535-284">ips - Itens a serem adicionados à matriz _ips_.</span><span class="sxs-lookup"><span data-stu-id="a4535-284">ips - Items to be added to the _ips_ array.</span></span>
  - <span data-ttu-id="a4535-285">URLs - Itens a serem adicionados à matriz _urls_.</span><span class="sxs-lookup"><span data-stu-id="a4535-285">urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="a4535-286">remover - Uma subestrutura detalhando itens a serem removidos do conjunto de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a4535-286">remove - A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="a4535-287">Omitido se não houver remoções.</span><span class="sxs-lookup"><span data-stu-id="a4535-287">Omitted if there are no removals.</span></span>
  - <span data-ttu-id="a4535-288">ips - itens a serem removidos da matriz _ips_.</span><span class="sxs-lookup"><span data-stu-id="a4535-288">ips - Items to be removed from the _ips_ array.</span></span>
  - <span data-ttu-id="a4535-289">urls- Itens a serem removidos da matriz _urls_.</span><span class="sxs-lookup"><span data-stu-id="a4535-289">urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="a4535-290">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="a4535-290">Examples:</span></span>

<span data-ttu-id="a4535-291">Exemplo 1 de URI de solicitação: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a4535-291">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a4535-p151">Solicita todas as alterações anteriores da instância do serviço do Office 365 em todo o mundo. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="a4535-p151">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="a4535-294">Exemplo 2 de URI de solicitação: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a4535-294">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a4535-p152">Solicita as alterações desde a versão especificada da instância do Office 365 em todo o mundo. Nesse caso, a versão especificada é a mais recente. Exemplo de resultado:</span><span class="sxs-lookup"><span data-stu-id="a4535-p152">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="a4535-298">Exemplo de script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4535-298">Example PowerShell Script</span></span>

<span data-ttu-id="a4535-299">Aqui está um script do PowerShell que você pode executar para ver se há ações que você precisa tomar para os dados atualizados.</span><span class="sxs-lookup"><span data-stu-id="a4535-299">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="a4535-300">Esse script verifica o número da versão dos pontos de extremidade da instância do Office 365 Worldwide.</span><span class="sxs-lookup"><span data-stu-id="a4535-300">This script checks the version number for the Office 365 Worldwide instance endpoints.</span></span> <span data-ttu-id="a4535-301">Quando há uma alteração, ele faz o download dos pontos de extremidade e filtros para os pontos de extremidade das categorias "Permitir" e "Otimizar".</span><span class="sxs-lookup"><span data-stu-id="a4535-301">When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints.</span></span> <span data-ttu-id="a4535-302">Ele também usa um _ClientRequestId_ exclusivo em várias chamadas e salva a versão mais recente encontrada em um arquivo temporário.</span><span class="sxs-lookup"><span data-stu-id="a4535-302">It also uses a unique _ClientRequestId_ across multiple calls and saves the latest version found in a temporary file.</span></span> <span data-ttu-id="a4535-303">Você deve chamar esse script uma vez por hora para verificar se há uma atualização de versão.</span><span class="sxs-lookup"><span data-stu-id="a4535-303">You should call this script once an hour to check for a version update.</span></span>

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
    $flatIp6s = $endpointSets | ForEach-Object {
    $endpointSet = $_
    $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
    # IPv6 strings have colons while IPv6 strings have dots
    $ip6s = $ips | Where-Object { $_ -like '*:*' }
    $ipCustomObjects = @()
    if ($endpointSet.category -in ("Optimize")) {
        $ipCustomObjects = $ip6s | ForEach-Object {
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
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a><span data-ttu-id="a4535-304">Exemplo de script do Python</span><span class="sxs-lookup"><span data-stu-id="a4535-304">Example Python Script</span></span>

<span data-ttu-id="a4535-p154">Esse é um script do Python, testado com o Python 3.6.3 no Windows 10, que você pode executar para ver se há ações que você precisa realizar em relação aos dados atualizados. Esse script verifica o número da versão dos pontos de extremidade de instâncias do Office 365 em todo o mundo. Quando houver uma alteração, ele baixará os pontos de extremidade e os filtros dos pontos de extremidade das categorias _Permitir_ e _Otimizar_. Ele também usa um ClientRequestId exclusivo em várias chamadas e salva a última versão encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se há alguma atualização da versão.</span><span class="sxs-lookup"><span data-stu-id="a4535-p154">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="a4535-310">Controle de versão de interface do serviço da Web</span><span class="sxs-lookup"><span data-stu-id="a4535-310">Web Service interface versioning</span></span>

<span data-ttu-id="a4535-p155">No futuro, podem ser necessárias atualizações de parâmetros ou de resultados desses métodos de serviço Web. Após a publicação da versão de disponibilidade geral desses serviços Web, a Microsoft fará os esforços cabíveis para enviar previamente notificações sobre atualizações do material para o serviço Web. Quando acreditar que uma atualização exigirá alterações dos clientes usando o serviço Web, a Microsoft manterá a versão anterior (uma versão antes) do serviço Web disponível por pelo menos doze (12) meses após o lançamento da nova versão. Os clientes que não fizerem a atualização durante esse período, perderão o acesso ao serviço Web e aos seus métodos. É preciso garantir que os clientes do serviço Web continuem trabalhando sem erros se as seguintes alterações forem feitas à assinatura da interface da Web:</span><span class="sxs-lookup"><span data-stu-id="a4535-p155">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="a4535-316">Adição de um novo parâmetro opcional a um método Web existente que não precise ser fornecido por clientes mais antigos e que não afete os resultados recebidos por um cliente mais antigo.</span><span class="sxs-lookup"><span data-stu-id="a4535-316">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="a4535-317">Adição de um novo atributo nomeado em um dos itens do REST de resposta ou em colunas adicionais para o CSV de resposta.</span><span class="sxs-lookup"><span data-stu-id="a4535-317">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="a4535-318">Adição de um novo método Web com um novo nome que não é chamado pelos clientes mais antigos.</span><span class="sxs-lookup"><span data-stu-id="a4535-318">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="office-365-endpoint-functions-module"></a><span data-ttu-id="a4535-319">Módulo de funções do ponto de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="a4535-319">Office 365 Endpoint Functions Module</span></span>

<span data-ttu-id="a4535-320">A Microsoft está hospedando um Serviço REST para obter o URI mais recente dos serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a4535-320">Microsoft is hosting a REST Service to get the newest and latest URI for the Office 365 services.</span></span>  <span data-ttu-id="a4535-321">Para poder usar o URI como uma coleção, você pode usar este módulo com alguns cmdlets úteis.</span><span class="sxs-lookup"><span data-stu-id="a4535-321">To be able to use the URI as a collection, you can use this module with a few helpful cmdlets.</span></span>

### <a name="calling-the-rest-service"></a><span data-ttu-id="a4535-322">Chamando o serviço REST</span><span class="sxs-lookup"><span data-stu-id="a4535-322">Calling the REST service</span></span>

<span data-ttu-id="a4535-323">Para usar este módulo, simplesmente copie o arquivo de módulo [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) em algum lugar no seu disco rígido e importe-o diretamente com este comando:</span><span class="sxs-lookup"><span data-stu-id="a4535-323">To use this module, simply copy the module file [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) somewhere on your hard disk and import it directly with this command:</span></span>

```powershell
    Import-Module O365EndpointFunctions.psm1
```

<span data-ttu-id="a4535-324">Depois de importar o módulo, você poderá chamar o serviço REST.</span><span class="sxs-lookup"><span data-stu-id="a4535-324">After you have imported the module, you will be able to call the REST service.</span></span> <span data-ttu-id="a4535-325">Isso retornará o URI como uma coleção que você pode processar diretamente no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4535-325">This will return the URI as a collection that you can now process in PowerShell directly.</span></span> <span data-ttu-id="a4535-326">Você deve inserir o nome do seu locatário do Office 365, conforme descrito no seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a4535-326">You must enter the name of your Office 365 tenant, as described in the following command:</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant]
```

#### <a name="parameters"></a><span data-ttu-id="a4535-327">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4535-327">Parameters</span></span>

- <span data-ttu-id="a4535-328">**tenantName** - o nome do seu locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a4535-328">**tenantName** - The name of your Office 365 tenant.</span></span> <span data-ttu-id="a4535-329">Este parâmetro é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a4535-329">This parameter is mandatory.</span></span>
- <span data-ttu-id="a4535-330">**ForceLatest** - Esse parâmetro forçará a API REST a sempre retornar toda a lista do URI mais recente.</span><span class="sxs-lookup"><span data-stu-id="a4535-330">**ForceLatest** -This switch will force the REST API to always return the entire list of the latest URI.</span></span>
- <span data-ttu-id="a4535-331">**IPv6** - Esta opção retornará os endereços IPv6 também.</span><span class="sxs-lookup"><span data-stu-id="a4535-331">**IPv6** -This switch will return the IPv6 addresses as well.</span></span> <span data-ttu-id="a4535-332">Por padrão, somente o IPv4 será retornado.</span><span class="sxs-lookup"><span data-stu-id="a4535-332">As default only IPv4 will be returned.</span></span>

### <a name="examples"></a><span data-ttu-id="a4535-333">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a4535-333">Examples</span></span>

<span data-ttu-id="a4535-334">Retornar a lista completa de todos os URIs, incluindo os endereços IPv6</span><span class="sxs-lookup"><span data-stu-id="a4535-334">Return the complete list of all URIs including the IPv6 addresses</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

<span data-ttu-id="a4535-335">Retornar somente os endereços IP para o serviço do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a4535-335">Return only the IP addresses for Exchange Online Service</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="a4535-336">Exportando um arquivo Proxy PAC</span><span class="sxs-lookup"><span data-stu-id="a4535-336">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="a4535-337">Você pode usar este módulo para criar um arquivo Proxy PAC.</span><span class="sxs-lookup"><span data-stu-id="a4535-337">You can use this module to create a Proxy PAC file.</span></span> <span data-ttu-id="a4535-338">Neste exemplo, você primeiro obtém os pontos de extremidade e filtra o resultado para selecionar as URLs.</span><span class="sxs-lookup"><span data-stu-id="a4535-338">In this example you first get the endpoints and filter the result to select the URLs.</span></span> <span data-ttu-id="a4535-339">Estas URLs são direcionadas para serem exportadas.</span><span class="sxs-lookup"><span data-stu-id="a4535-339">These URLs are piped to be exported.</span></span>  

```powershell
 Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a><span data-ttu-id="a4535-340">Tópicos Relacionados</span><span class="sxs-lookup"><span data-stu-id="a4535-340">Related Topics</span></span>
  
[<span data-ttu-id="a4535-341">URLs e intervalos de endereços IP do Office 365</span><span class="sxs-lookup"><span data-stu-id="a4535-341">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="a4535-342">Perguntas frequentes sobre pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="a4535-342">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="a4535-343">Princípios de conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="a4535-343">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="a4535-344">Rede do Office 365 e ajuste de desempenho</span><span class="sxs-lookup"><span data-stu-id="a4535-344">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="a4535-345">Conectividade de rede para Office 365</span><span class="sxs-lookup"><span data-stu-id="a4535-345">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="a4535-346">Qualidade da mídia e desempenho de conectividade de rede no Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a4535-346">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="a4535-347">Como otimizar a sua rede para o Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a4535-347">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="a4535-348">Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho</span><span class="sxs-lookup"><span data-stu-id="a4535-348">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="a4535-349">Plano de solução de problemas de desempenho do Office 365</span><span class="sxs-lookup"><span data-stu-id="a4535-349">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
