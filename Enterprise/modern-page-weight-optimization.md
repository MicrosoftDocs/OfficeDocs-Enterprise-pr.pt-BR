---
title: Otimizar o peso da página nas páginas do site moderno do SharePoint Online.
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Aprenda a otimizar o peso da página nas páginas do site moderno do SharePoint Online.
ms.openlocfilehash: 96341402cb6f1ca89e7a1602d77adf70e4a69607
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814209"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="cf8d9-103">Otimizar o peso da página nas páginas do site moderno do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-103">Optimize page weight in SharePoint Online modern site pages</span></span>

<span data-ttu-id="cf8d9-104">As páginas do site moderno do SharePoint Online contêm o código serializado necessário para renderizar o conteúdo da página, incluindo imagens, texto, objetos na área de conteúdo embaixo das barras de navegação/comando e outro código HTML que forma a estrutura da página.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-104">SharePoint Online modern site pages contain serialized code that is required to render page content of the page, including images, text, objects in the content area underneath navigation/command bars and other HTML code that forms the framework of the page.</span></span> <span data-ttu-id="cf8d9-105">A gramatura da página é uma medida desse código HTML e deve ser limitado para garantir o tempo de carregamento ideal da página.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-105">Page weight is a measurement of this HTML code, and should be limited to ensure optimal page load times.</span></span>

<span data-ttu-id="cf8d9-106">Este artigo vai ajudá-lo a entender como reduzir o peso da página em suas páginas de site modernos.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-106">This article will help you understand how to reduce page weight in your modern site pages.</span></span>

>[!NOTE]
><span data-ttu-id="cf8d9-107">Para obter mais informações sobre o desempenho dos portais modernos do SharePoint Online, confira [Desempenho na experiência moderna do SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="cf8d9-107">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a><span data-ttu-id="cf8d9-108">Usar a ferramenta Diagnóstico de Página do SharePoint para analisar o peso da página</span><span class="sxs-lookup"><span data-stu-id="cf8d9-108">Use the Page Diagnostics for SharePoint tool to analyze page weight</span></span>

<span data-ttu-id="cf8d9-109">A **ferramenta Diagnóstico de Página do SharePoint** é uma extensão de navegador para o Chrome e o [Microsoft Edge versão 77 ou posterior](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8), que você pode usar para analisar as páginas do site de publicação moderna e clássica do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="cf8d9-110">A ferramenta fornece um relatório para cada página analisada que mostra o desempenho da página em relação a um conjunto definido de critérios de desempenho.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="cf8d9-111">Para instalar e saber mais sobre a ferramenta Diagnóstico de Página do SharePoint, acesse [Usar a ferramenta Diagnóstico de Página do SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="cf8d9-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="cf8d9-112">Ao analisar uma página de site do SharePoint com a ferramenta Diagnóstico de Página para SharePoint, você pode ver informações sobre a página **Peso da página em 500kB** resultado do painel dos _Testes de Diagnóstico _.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about page in the **Page weight under 500KB** result of the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="cf8d9-113">O resultado será exibido em verde se o peso da página estiver abaixo do valor da linha de base e vermelho se o peso da página exceder o valor da linha de base.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-113">The result will appear in green if the page weight is under the baseline value, and red if the page weight exceeds the baseline value.</span></span>

<span data-ttu-id="cf8d9-114">Os resultados possíveis incluem:</span><span class="sxs-lookup"><span data-stu-id="cf8d9-114">Possible results include:</span></span>

- <span data-ttu-id="cf8d9-115">**Atenção necessária** (vermelho): O peso da página ultrapassa 500kB</span><span class="sxs-lookup"><span data-stu-id="cf8d9-115">**Attention required** (red): Page weight exceeds 500KB</span></span>
- <span data-ttu-id="cf8d9-116">**Nenhuma ação necessário** (verde): O peso da página está abaixo de 500kB</span><span class="sxs-lookup"><span data-stu-id="cf8d9-116">**No action required** (green): Page weight is under 500KB</span></span>

<span data-ttu-id="cf8d9-117">Se o resultado **Peso da página abaixo de 500kB** aparecer na seção **Atenção necessária**, você pode clicar no resultado para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-117">If the **Page weight under 500KB** result appears in the **Attention required** section, you can click the result for details.</span></span>

![Solicitações para resultados do SharePoint](media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a><span data-ttu-id="cf8d9-119">Solucionar problemas com o peso da página</span><span class="sxs-lookup"><span data-stu-id="cf8d9-119">Remediate page weight issues</span></span>

<span data-ttu-id="cf8d9-120">Se o peso da página exceder 500KB, você pode aumentar o tempo geral de carregamento da página reduzindo o número de Web Parts e limitando o conteúdo da página a um grau apropriado.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-120">If page weight exceeds 500KB, you can improve overall page load time by reducing the number of web parts and limiting page content to an appropriate degree.</span></span>

<span data-ttu-id="cf8d9-121">As diretrizes gerais para reduzir o peso da página incluem:</span><span class="sxs-lookup"><span data-stu-id="cf8d9-121">General guidance for reducing page weight includes:</span></span>

- <span data-ttu-id="cf8d9-122">Limite o conteúdo da página a um valor razoável e use várias páginas para conteúdo relacionado.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-122">Limit the page content to a reasonable amount and use multiple pages for related content.</span></span>
- <span data-ttu-id="cf8d9-123">Minimize o uso de Web Parts com grandes bolsas de propriedades.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-123">Minimize the use of web parts that have large property bags.</span></span>
- <span data-ttu-id="cf8d9-124">Use modos de exibição cumulativos não interativos sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-124">Use non-interactive rollup views when possible.</span></span>
- <span data-ttu-id="cf8d9-125">Otimize os tamanhos das imagens dimensionando-as de forma adequada, usando formatos de imagem compactados e garantindo que eles sejam baixados de uma CDN.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-125">Optimize image sizes by sizing images appropriately, using compressed image formats and ensuring that they are downloaded from a CDN.</span></span>

<span data-ttu-id="cf8d9-126">Para saber mais, confira o artigo a seguir sobre como limitar o peso da página no seguinte artigo:</span><span class="sxs-lookup"><span data-stu-id="cf8d9-126">You can find additional guidance for limiting page weight in the following article:</span></span>

- [<span data-ttu-id="cf8d9-127">Otimizar o desempenho de página no SharePoint</span><span class="sxs-lookup"><span data-stu-id="cf8d9-127">Optimize page performance in SharePoint</span></span>](https://docs.microsoft.com/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

<span data-ttu-id="cf8d9-128">Antes de criar revisões de página para corrigir problemas de desempenho, anote o tempo de carregamento da página nos resultados da análise.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-128">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="cf8d9-129">Execute a ferramenta novamente após a revisão para ver se o novo resultado está dentro do padrão da linha de base e verifique o tempo de carregamento da nova página para ver se melhorou.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-129">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Resultados do tempo de carregamento da página](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="cf8d9-131">O tempo de carregamento da página pode variar de acordo com vários fatores, como a carga da rede, hora do dia e outras condições transitórias.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-131">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="cf8d9-132">Você deve testar o tempo de carregamento da página algumas vezes antes e depois de fazer as alterações para ajudá-lo a calcular uma média dos resultados.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-132">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="cf8d9-133">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="cf8d9-133">Related topics</span></span>

[<span data-ttu-id="cf8d9-134">Ajustar o desempenho do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cf8d9-134">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="cf8d9-135">Ajustar o desempenho do Office 365</span><span class="sxs-lookup"><span data-stu-id="cf8d9-135">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="cf8d9-136">Desempenho na experiência moderna do SharePoint</span><span class="sxs-lookup"><span data-stu-id="cf8d9-136">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="cf8d9-137">Redes de distribuição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="cf8d9-137">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="cf8d9-138">Usar a Rede de Distribuição de Conteúdo (CDN) do Office 365 com o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cf8d9-138">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
