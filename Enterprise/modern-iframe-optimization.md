---
title: Otimizar os iFrames em páginas do site de publicação clássico e moderno do SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/17/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Saiba como otimizar o desempenho de iFrames em páginas do site de publicação clássico e moderno do SharePoint Online.
ms.openlocfilehash: 676407108db1669240df76438ff2b8739c4eaac1
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028218"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="3b953-103">Otimizar os iFrames em páginas do site de publicação clássico e moderno do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3b953-103">Optimize iFrames in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="3b953-104">Os iFrames podem ser útil para a visualização de conteúdo avançado, como vídeos ou outras mídias.</span><span class="sxs-lookup"><span data-stu-id="3b953-104">iFrames can be useful for previewing rich content such as videos or other media.</span></span> <span data-ttu-id="3b953-105">No entanto, como os iFrames carregam uma página separada na página do site do SharePoint, o conteúdo carregado no iFrame pode conter imagens grandes, vídeos ou outros elementos que podem contribuir para o tempo total de carregamento da página e que você não pode controlar na página.</span><span class="sxs-lookup"><span data-stu-id="3b953-105">However, because iFrames load a separate page within the SharePoint site page, content loaded in the iFrame could contain large images, videos or other elements that can contribute to overall page load times and that you cannot control on the page.</span></span> <span data-ttu-id="3b953-106">Este artigo ajudará você a entender como determinar de que modo os iFrames nas suas páginas afetam a latência percebida pelo usuário e como corrigir problemas comuns.</span><span class="sxs-lookup"><span data-stu-id="3b953-106">This article will help you understand how to determine how iFrames in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="3b953-107">Para obter mais informações sobre o desempenho dos sites modernos do SharePoint Online, confira [Desempenho na experiência moderna do SharePoint](https://docs.microsoft.com/pt-BR/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="3b953-107">For more information about performance in SharePoint Online modern sites, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/pt-BR/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a><span data-ttu-id="3b953-108">Usar a ferramenta Diagnóstico de Página para SharePoint para analisar Web Parts usando os iFrames</span><span class="sxs-lookup"><span data-stu-id="3b953-108">Use the Page Diagnostics for SharePoint tool to analyze web parts using iFrames</span></span>

<span data-ttu-id="3b953-109">A **ferramenta Diagnóstico de Página para SharePoint** é uma extensão de navegador para o Chrome e o [Microsoft Edge versão 77 ou posterior](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) que você pode usar para analisar as páginas do site de publicação moderno e clássico do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3b953-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="3b953-110">A ferramenta fornece um relatório para cada página analisada que mostra o desempenho da página em relação a um conjunto definido de critérios de desempenho.</span><span class="sxs-lookup"><span data-stu-id="3b953-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="3b953-111">Para instalar e saber mais sobre a ferramenta Diagnóstico de Página para SharePoint, acesse [Usar a ferramenta Diagnóstico de Página para SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="3b953-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="3b953-112">Ao analisar uma página do site do SharePoint com a ferramenta Diagnóstico de página do SharePoint, você pode ver as informações sobre as Web Parts que contêm os iFrames no painel _Testes de diagnóstico_.</span><span class="sxs-lookup"><span data-stu-id="3b953-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts containing iFrames in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="3b953-113">A métrica da linha de base é a mesma para as páginas clássicas e modernas.</span><span class="sxs-lookup"><span data-stu-id="3b953-113">The baseline metric is the same for modern and classic pages.</span></span>

<span data-ttu-id="3b953-114">Os resultados possíveis incluem:</span><span class="sxs-lookup"><span data-stu-id="3b953-114">Possible results include:</span></span>

- <span data-ttu-id="3b953-115">**Atenção necessária** (vermelho): a página contém **três ou mais** Web Parts usando iFrames</span><span class="sxs-lookup"><span data-stu-id="3b953-115">**Attention required** (red): The page contains **three or more** web parts using iFrames</span></span>
- <span data-ttu-id="3b953-116">**Oportunidades de melhoria** (amarelo): a página contém **uma ou duas** Web Parts usando iFrames</span><span class="sxs-lookup"><span data-stu-id="3b953-116">**Improvement opportunities** (yellow): The page contains **one or two** web parts using iFrames</span></span>
- <span data-ttu-id="3b953-117">**Nenhuma ação necessária** (verde): a página não contém Web Parts usando iFrames</span><span class="sxs-lookup"><span data-stu-id="3b953-117">**No action required** (green): The page contains no web parts using iFrames</span></span>

<span data-ttu-id="3b953-118">Se o resultado **Web Parts usando iFrames detectados** aparecer na seção **Oportunidades de melhoria** ou **Atenção necessária)**, você poderá clicar no resultado para ver a Web Parts que contêm iFrames.</span><span class="sxs-lookup"><span data-stu-id="3b953-118">If the **Web parts using iFrames detected** result appears in either the **Improvement opportunities** or **Attention required)** section of the results, you can click the result to see the web parts that contain iFrames.</span></span>

![Resultados da ferramenta Diagnóstico de Página](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a><span data-ttu-id="3b953-120">Solucionar problemas de desempenho de iFrame</span><span class="sxs-lookup"><span data-stu-id="3b953-120">Remediate iFrame performance issues</span></span>

<span data-ttu-id="3b953-121">Use o resultado **Web Parts usando iFrames detectados** na ferramenta Página de diagnóstico para determinar quais Web Parts contêm iFrames e podem estar contribuindo no tempo de carregamento lento da página.</span><span class="sxs-lookup"><span data-stu-id="3b953-121">Use the **Web parts using iFrames detected** result in the Page Diagnostic tool to determine which web parts contain iFrames and may be contributing to slow page load times.</span></span>

<span data-ttu-id="3b953-122">Os iFrames são inerentemente lentos porque carregam uma página externa separada, incluindo todo o conteúdo associado, como elementos JavaScript, CSS e Framework, potencialmente aumentando a sobrecarga da página do site em um fator de dois ou mais.</span><span class="sxs-lookup"><span data-stu-id="3b953-122">iFrames are inherently slow because they load a separate external page including all associated content such as javascript, CSS and framework elements, potentially increasing the overhead of the site page by a factor of two or more.</span></span>

<span data-ttu-id="3b953-123">Siga as orientações abaixo para garantir o uso ideal dos iFrames.</span><span class="sxs-lookup"><span data-stu-id="3b953-123">Follow the guidance below to ensure optimal use of iFrames.</span></span>

- <span data-ttu-id="3b953-124">Quando possível, use imagens em vez de iFrames se a visualização for não interativa ou pequena para começar.</span><span class="sxs-lookup"><span data-stu-id="3b953-124">When possible, use images instead of iFrames if the preview is small to begin with or non-interactive.</span></span>
- <span data-ttu-id="3b953-125">Se precisar usar os iFrames, minimize o número e/ou remova-os do visor.</span><span class="sxs-lookup"><span data-stu-id="3b953-125">If iFrames must be used, minimize the number and/or move them out of the viewport.</span></span>
- <span data-ttu-id="3b953-126">Os arquivos inseridos do Office, como o Word, Excel e PowerPoint são interativos, mas são lentos para carregar.</span><span class="sxs-lookup"><span data-stu-id="3b953-126">Embedded Office files like Word, Excel and PowerPoint are interactive, but are slow to load.</span></span> <span data-ttu-id="3b953-127">As miniaturas de imagem com um link para o documento inteiro geralmente terão melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="3b953-127">Image thumbnails with a link to the full document will often perform better.</span></span>
- <span data-ttu-id="3b953-128">Os vídeos inseridos do YouTube e os feeds do Twitter tendem a funcionar melhor nos iFrames, mas você deve usar esses tipos de incorporações de forma criteriosa.</span><span class="sxs-lookup"><span data-stu-id="3b953-128">Embedded YouTube videos and Twitter feeds tend to perform better in iFrames, but use these kinds of embeds judiciously.</span></span>
- <span data-ttu-id="3b953-129">As Web Parts isoladas são uma exceção razoável, mas minimize seu número e posicionamento no visor.</span><span class="sxs-lookup"><span data-stu-id="3b953-129">Isolated web parts are a reasonable exception, but minimize their number and placement in the viewport.</span></span>
- <span data-ttu-id="3b953-130">Se um iFrame estiver fora do visor, considere o uso de um IntersectionObserver para atrasar a renderização do iFrame até que ele seja exibido.</span><span class="sxs-lookup"><span data-stu-id="3b953-130">If an iFrame is located out of the viewport, consider using an _IntersectionObserver_ to delay rendering the iFrame until it comes into view.</span></span>

<span data-ttu-id="3b953-131">Antes de fazer as revisões das páginas para corrigir problemas de desempenho, anote o tempo de carregamento da página nos resultados da análise.</span><span class="sxs-lookup"><span data-stu-id="3b953-131">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="3b953-132">Execute a ferramenta novamente após a revisão para ver se o novo resultado está dentro do padrão da linha de base e verifique o tempo de carregamento da nova página para ver se melhorou.</span><span class="sxs-lookup"><span data-stu-id="3b953-132">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Resultados do tempo de carregamento da página](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="3b953-134">O tempo de carregamento da página pode variar de acordo com vários fatores, como a carga da rede, hora do dia e outras condições transitórias.</span><span class="sxs-lookup"><span data-stu-id="3b953-134">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="3b953-135">Você deve testar o tempo de carregamento da página algumas vezes antes e depois de fazer as alterações para ajudá-lo a calcular uma média dos resultados.</span><span class="sxs-lookup"><span data-stu-id="3b953-135">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="3b953-136">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="3b953-136">Related topics</span></span>

[<span data-ttu-id="3b953-137">Ajustar o desempenho do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3b953-137">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="3b953-138">Ajustar o desempenho do Office 365</span><span class="sxs-lookup"><span data-stu-id="3b953-138">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="3b953-139">Desempenho na experiência moderna do SharePoint</span><span class="sxs-lookup"><span data-stu-id="3b953-139">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/pt-BR/sharepoint/modern-experience-performance.md)
