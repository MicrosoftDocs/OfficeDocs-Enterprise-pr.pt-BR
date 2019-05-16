---
title: Usar a Rede de Distribuição de Conteúdo (CDN) do Office 365 com o SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Descreve como usar a CDN (rede de distribuição de conteúdo) do Office 365 para acelerar a entrega de seus ativos do SharePoint Online para todos os seus usuários, independentemente de onde eles estão localizados ou como eles acessam o conteúdo.
ms.openlocfilehash: de8c02b44405260aa7379ab0a881ba72f73c7a6b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070627"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="06dac-103">Usar a Rede de Distribuição de Conteúdo (CDN) do Office 365 com o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="06dac-104">Você pode usar a Rede de Distribuição de Conteúdo (CDN) do Office 365 integrado para proporcionar melhor desempenho a suas páginas do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="06dac-105">A CDN do Office 365 melhora o desempenho ao armazenar em cache ativos estáticos mais próximos aos navegadores que os solicitaram, o que ajuda a acelerar downloads e reduzir a latência.</span><span class="sxs-lookup"><span data-stu-id="06dac-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="06dac-106">Além disso, a CDN do Office 365 usa o [protocolo http/2](https://en.wikipedia.org/wiki/HTTP/2) para maior compactação e canalização http.</span><span class="sxs-lookup"><span data-stu-id="06dac-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="06dac-107">O serviço de CDN do Office 365 faz parte da assinatura do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="06dac-108">A CDN do Office 365 é composta por várias CDNs que permitem que você hospede ativos estáticos em vários locais ou _origens_e sirva-os de redes globais de alta velocidade.</span><span class="sxs-lookup"><span data-stu-id="06dac-108">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="06dac-109">Dependendo do tipo de conteúdo você quiser hospedar na CDN do Office 365, você pode adicionar origens **públicas**, origens **privadas** ou ambas.</span><span class="sxs-lookup"><span data-stu-id="06dac-109">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="06dac-110">Veja [escolher se cada origem deve ser pública ou privada](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) para obter mais informações sobre a diferença entre origens públicas e privadas.</span><span class="sxs-lookup"><span data-stu-id="06dac-110">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="06dac-111">![Diagrama conceitual da CDN do Office 365] (media/O365-CDN/o365-cdn-flow-transparent.svg "Diagrama conceitual da CDN do Office 365")</span><span class="sxs-lookup"><span data-stu-id="06dac-111">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="06dac-112">Se você já estiver familiarizado com o modo como o CDNs funciona, só precisará concluir algumas etapas para habilitar a CDN do Office 365 para o seu locatário.</span><span class="sxs-lookup"><span data-stu-id="06dac-112">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="06dac-113">Este tópico descreve como.</span><span class="sxs-lookup"><span data-stu-id="06dac-113">This topic describes how.</span></span> <span data-ttu-id="06dac-114">Continue lendo para saber mais sobre como começar a hospedar seus ativos estáticos.</span><span class="sxs-lookup"><span data-stu-id="06dac-114">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="06dac-115">Há outros CDNs hospedados pela Microsoft que podem ser usados com o Office 365 para cenários de uso especializado, mas não são discutidos neste tópico porque estão fora do escopo da CDN do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06dac-115">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="06dac-116">Para obter mais informações, consulte [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span><span class="sxs-lookup"><span data-stu-id="06dac-116">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 <span data-ttu-id="06dac-117">**Volta para o [planejamento de rede e ajuste de desempenho do Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="06dac-117">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="06dac-118">Visão geral do trabalho com a CDN do Office 365 no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-118">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="06dac-119">Para configurar a CDN do Office 365 para sua organização, siga estas etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="06dac-119">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

- [<span data-ttu-id="06dac-120">Planejar a implantação da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-120">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - <span data-ttu-id="06dac-121">[Determine quais ativos estáticos você deseja hospedar na CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span><span class="sxs-lookup"><span data-stu-id="06dac-121">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  - <span data-ttu-id="06dac-122">[Determine onde você deseja armazenar seus ativos](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span><span class="sxs-lookup"><span data-stu-id="06dac-122">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="06dac-123">Este local pode ser um site do SharePoint, uma biblioteca ou uma pasta e é chamado de _origem_.</span><span class="sxs-lookup"><span data-stu-id="06dac-123">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  - <span data-ttu-id="06dac-124">[Escolha se cada origem deve ser pública ou privada](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span><span class="sxs-lookup"><span data-stu-id="06dac-124">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="06dac-125">Você pode adicionar várias origens de tipos públicos e privados.</span><span class="sxs-lookup"><span data-stu-id="06dac-125">You can add multiple origins of both public and private types.</span></span>

- <span data-ttu-id="06dac-126">Configurar e configurar a CDN usando o PowerShell ou a CLI do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-126">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  - [<span data-ttu-id="06dac-127">Configurar e configurar a CDN usando o Shell de gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-127">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [<span data-ttu-id="06dac-128">Configurar e configurar a CDN usando a CLI do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-128">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="06dac-129">Ao concluir esta etapa, você terá:</span><span class="sxs-lookup"><span data-stu-id="06dac-129">When you complete this step, you will have:</span></span>

  - <span data-ttu-id="06dac-130">Habilitou a CDN para sua organização.</span><span class="sxs-lookup"><span data-stu-id="06dac-130">Enabled the CDN for your organization.</span></span>
  - <span data-ttu-id="06dac-131">Adicionadas suas origens, identificando cada origem como pública ou privada.</span><span class="sxs-lookup"><span data-stu-id="06dac-131">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="06dac-132">Após concluir a instalação, você poderá [gerenciar a CDN do Office 365](use-office-365-cdn-with-spo.md#CDNManage) ao longo do tempo:</span><span class="sxs-lookup"><span data-stu-id="06dac-132">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
- <span data-ttu-id="06dac-133">Adicionando, atualizando e removendo ativos</span><span class="sxs-lookup"><span data-stu-id="06dac-133">Adding, updating, and removing assets</span></span>
- <span data-ttu-id="06dac-134">Adição e remoção de origens</span><span class="sxs-lookup"><span data-stu-id="06dac-134">Adding and removing origins</span></span>
- <span data-ttu-id="06dac-135">Configurando políticas de CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-135">Configuring CDN policies</span></span>
- <span data-ttu-id="06dac-136">Se necessário, desabilitando a CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-136">If necessary, disabling the CDN</span></span>

<span data-ttu-id="06dac-137">Por fim, consulte [usando seus ativos de CDN](use-office-365-cdn-with-spo.md#using-your-cdn-assets) para saber mais sobre como acessar seus ativos de CDN de origens públicas e privadas.</span><span class="sxs-lookup"><span data-stu-id="06dac-137">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="06dac-138">Consulte [Troubleshooting The Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) para obter orientação sobre a resolução de problemas comuns.</span><span class="sxs-lookup"><span data-stu-id="06dac-138">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="06dac-139">Planejar a implantação da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-139">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="06dac-140">Antes de implantar a CDN do Office 365 para seu locatário do Office 365, considere os seguintes fatores como parte do processo de planejamento.</span><span class="sxs-lookup"><span data-stu-id="06dac-140">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  - [<span data-ttu-id="06dac-141">Determinar quais ativos estáticos você deseja hospedar na CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-141">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  - [<span data-ttu-id="06dac-142">Determinar onde você deseja armazenar seus ativos</span><span class="sxs-lookup"><span data-stu-id="06dac-142">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [<span data-ttu-id="06dac-143">Escolha se cada origem deve ser pública ou privada</span><span class="sxs-lookup"><span data-stu-id="06dac-143">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="06dac-144">Determinar quais ativos estáticos você deseja hospedar na CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-144">Determine which static assets you want to host on the CDN</span></span>
<span data-ttu-id="06dac-145"><a name="CDNAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-145"></span></span>

<span data-ttu-id="06dac-146">Em geral, o CDNs é mais eficaz para hospedar _ativos estáticos_ou ativos que não mudam muito frequentemente.</span><span class="sxs-lookup"><span data-stu-id="06dac-146">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="06dac-147">Uma boa regra prática é identificar arquivos que atendam a algumas ou todas as condições a seguir:</span><span class="sxs-lookup"><span data-stu-id="06dac-147">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

- <span data-ttu-id="06dac-148">Arquivos estáticos incorporados em uma página (como scripts e imagens) que podem ter um impacto incremental significativo nos tempos de carregamento da página</span><span class="sxs-lookup"><span data-stu-id="06dac-148">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
- <span data-ttu-id="06dac-149">Arquivos grandes, como executáveis e arquivos de instalação</span><span class="sxs-lookup"><span data-stu-id="06dac-149">Large files like executables and installation files</span></span>
- <span data-ttu-id="06dac-150">Arquivos de mídia de fluxo contínuo</span><span class="sxs-lookup"><span data-stu-id="06dac-150">Streaming media files</span></span>
- <span data-ttu-id="06dac-151">Bibliotecas de recursos que dão suporte ao código do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="06dac-151">Resource libraries that support client-side code</span></span>

<span data-ttu-id="06dac-152">Por exemplo, arquivos pequenos que são solicitados repetidamente como imagens de site e scripts podem melhorar significativamente o desempenho da renderização de site e reduzir incrementalmente a carga em seus sites do SharePoint Online quando você os adiciona a uma origem de CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-152">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="06dac-153">Arquivos maiores, como executáveis de instalação ou arquivos de vídeo, podem ser baixados ou transmitidos da CDN, fornecendo um impacto de desempenho positivo e a redução subsequente da carga no seu site do SharePoint Online, mesmo que eles não sejam acessados com a frequência.</span><span class="sxs-lookup"><span data-stu-id="06dac-153">Larger files such as installation executables or video files can be downloaded or streamed from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="06dac-154">A melhoria de desempenho por arquivo depende de vários fatores, incluindo a proximidade do cliente para o ponto de extremidade da CDN mais próxima, condições transitórias na rede local e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="06dac-154">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="06dac-155">Muitos arquivos estáticos são bem pequenos e podem ser baixados do Office 365 em menos de um segundo.</span><span class="sxs-lookup"><span data-stu-id="06dac-155">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="06dac-156">No entanto, uma página da Web pode conter vários arquivos incorporados com um tempo de download cumulativo de vários segundos.</span><span class="sxs-lookup"><span data-stu-id="06dac-156">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="06dac-157">Servir esses arquivos da CDN pode reduzir significativamente o tempo de carregamento geral da página.</span><span class="sxs-lookup"><span data-stu-id="06dac-157">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="06dac-158">Veja [quais ganhos de desempenho uma CDN oferece?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) por exemplo.</span><span class="sxs-lookup"><span data-stu-id="06dac-158">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="06dac-159">Determinar onde você deseja armazenar seus ativos</span><span class="sxs-lookup"><span data-stu-id="06dac-159">Determine where you want to store your assets</span></span>
<span data-ttu-id="06dac-160"><a name="CDNStoreAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-160"></span></span>

<span data-ttu-id="06dac-161">A CDN busca seus ativos de um local chamado _origem_.</span><span class="sxs-lookup"><span data-stu-id="06dac-161">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="06dac-162">Uma origem pode ser um site do SharePoint, uma biblioteca de documentos ou uma pasta que possa ser acessada por uma URL.</span><span class="sxs-lookup"><span data-stu-id="06dac-162">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="06dac-163">Você tem grande flexibilidade ao especificar origens para sua organização.</span><span class="sxs-lookup"><span data-stu-id="06dac-163">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="06dac-164">Por exemplo, você pode especificar várias origens ou uma única origem em que você deseja colocar todos os seus ativos de CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-164">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="06dac-165">Você pode optar por ter origens públicas ou privadas para sua organização.</span><span class="sxs-lookup"><span data-stu-id="06dac-165">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="06dac-166">A maioria das organizações optará por implementar uma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="06dac-166">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="06dac-167">Você pode criar um novo contêiner para suas origens, como pastas ou bibliotecas de documentos, e adicionar arquivos que você deseja disponibilizar na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-167">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="06dac-168">Essa é uma boa abordagem se você tiver um conjunto específico de ativos que você deseja que esteja disponível na CDN e deseja restringir o conjunto de ativos da CDN a apenas esses arquivos no contêiner.</span><span class="sxs-lookup"><span data-stu-id="06dac-168">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="06dac-169">Você também pode configurar um conjunto de sites, um site, uma biblioteca ou uma pasta existente como origem, o que tornará todos os ativos qualificados no contêiner disponíveis na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-169">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="06dac-170">Antes de adicionar um contêiner existente como origem, é importante certificar-se de que você está ciente de seu conteúdo e permissões para não expor inadvertidamente ativos para acesso anônimo ou usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="06dac-170">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="06dac-171">Você pode definir _as políticas de CDN_ para excluir o conteúdo de suas origens da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-171">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="06dac-172">As políticas de CDN excluem ativos em origens públicas ou privadas por atributos como _tipo de arquivo_ e _classificação de site_e são aplicadas a todas as origens do CdnType (privado ou público) especificado na política.</span><span class="sxs-lookup"><span data-stu-id="06dac-172">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="06dac-173">Por exemplo, se você adicionar uma origem privada que consiste em um site que contém vários subsites, é possível definir uma política para excluir sites marcados como **confidenciais** , de modo que o conteúdo de sites com essa classificação aplicada não será atendido da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-173">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="06dac-174">A política será aplicada ao conteúdo de _todas as_ origens privadas que você adicionou à CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-174">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="06dac-175">Tenha em mente que quanto maior o número de origens, maior o impacto no tempo em que o serviço de CDN leva para processar as solicitações.</span><span class="sxs-lookup"><span data-stu-id="06dac-175">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="06dac-176">Recomendamos que você limite o número de origens o máximo possível.</span><span class="sxs-lookup"><span data-stu-id="06dac-176">We recommend that you limit the number of origins as much as possible.</span></span>
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="06dac-177">Escolha se cada origem deve ser pública ou privada</span><span class="sxs-lookup"><span data-stu-id="06dac-177">Choose whether each origin should be public or private</span></span>
<span data-ttu-id="06dac-178"><a name="CDNOriginChoosePublicPrivate"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-178"></span></span>

<span data-ttu-id="06dac-179">Quando você identifica uma origem, especifica se ela deve ser publicada ou __ _privada_.</span><span class="sxs-lookup"><span data-stu-id="06dac-179">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="06dac-180">O acesso aos ativos da CDN em origens públicas é anônimo, e o conteúdo da CDN em origens privadas é protegido por tokens gerados dinamicamente para maior segurança.</span><span class="sxs-lookup"><span data-stu-id="06dac-180">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="06dac-181">Independentemente da opção que você escolher, a Microsoft faz todo o trabalho pesado quando se trata da administração da CDN propriamente dita.</span><span class="sxs-lookup"><span data-stu-id="06dac-181">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="06dac-182">Além disso, você pode mudar de ideia depois, depois de configurar a CDN e identificar suas origens.</span><span class="sxs-lookup"><span data-stu-id="06dac-182">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="06dac-183">As opções pública e privada fornecem ganhos de desempenho semelhantes, mas cada um tem atributos e vantagens exclusivos.</span><span class="sxs-lookup"><span data-stu-id="06dac-183">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="06dac-184">Origens **públicas** dentro da CDN do Office 365 são acessíveis anonimamente, e ativos hospedados podem ser acessados por qualquer pessoa que tenha a URL para o ativo.</span><span class="sxs-lookup"><span data-stu-id="06dac-184">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="06dac-185">Como o acesso ao conteúdo de origens públicas é anônimo, você só deve usá-lo para o armazenamento em cache de conteúdo genérico e não sensível como arquivos javascript, scripts, ícones e imagens.</span><span class="sxs-lookup"><span data-stu-id="06dac-185">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="06dac-186">Origens**privadas** dentro da CDN do Office 365 oferecem acesso privado ao conteúdo do usuário, como as bibliotecas de documentos do SharePoint Online, sites e mídia, por exemplo, vídeos.</span><span class="sxs-lookup"><span data-stu-id="06dac-186">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and media such as videos.</span></span> <span data-ttu-id="06dac-187">O acesso ao conteúdo em origens privadas é protegido por tokens gerados dinamicamente, de forma que ele só possa ser acessado por usuários com permissões para a biblioteca de documentos original ou local de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="06dac-187">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="06dac-188">Origens privadas na CDN do Office 365 só podem ser usadas para conteúdo do SharePoint Online, e você só pode acessar ativos em origens privadas por meio de redirecionamento de seu locatário do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-188">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="06dac-189">Você pode ler mais sobre como a CDN o acesso aos ativos de uma origem privada funciona [com o uso de ativos em origens privadas](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span><span class="sxs-lookup"><span data-stu-id="06dac-189">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="06dac-190">Atributos e vantagens da Hospedagem de ativos em origens públicas</span><span class="sxs-lookup"><span data-stu-id="06dac-190">Attributes and advantages of hosting assets in public origins</span></span>
  
- <span data-ttu-id="06dac-191">Os ativos exibidos em uma origem pública são acessíveis por todos os usuários anonimamente.</span><span class="sxs-lookup"><span data-stu-id="06dac-191">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="06dac-192">Você nunca deve colocar recursos que contenham informações de usuário ou são considerados confidenciais para sua organização em uma origem pública.</span><span class="sxs-lookup"><span data-stu-id="06dac-192">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
- <span data-ttu-id="06dac-193">Se você remover um ativo de uma origem pública, ele pode seguir disponível em cache por até 30 dias; contudo, invalidaremos os links para o ativo na CDN em 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="06dac-193">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
- <span data-ttu-id="06dac-194">Quando você hospeda folhas de estilo (arquivos CSS) em uma origem pública, você pode usar os caminhos relativos e URIs dentro do código.</span><span class="sxs-lookup"><span data-stu-id="06dac-194">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="06dac-195">Isso significa que você pode referenciar o local das imagens de fundo e outros objetos em relação ao local do ativo que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="06dac-195">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
- <span data-ttu-id="06dac-196">Por mais que você possa codificar uma URL de origem pública, isto não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="06dac-196">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="06dac-197">O motivo é que se o acesso à CDN ficar indisponível, a URL não resolverá automaticamente para a sua organização no SharePoint Online e pode resultar em links quebrados e outros erros.</span><span class="sxs-lookup"><span data-stu-id="06dac-197">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
- <span data-ttu-id="06dac-198">Os tipos de arquivo padrão incluídos para origens públicas são .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf e .woff.</span><span class="sxs-lookup"><span data-stu-id="06dac-198">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="06dac-199">Você pode especificar tipos de arquivo adicionais.</span><span class="sxs-lookup"><span data-stu-id="06dac-199">You can specify additional file types.</span></span>
- <span data-ttu-id="06dac-200">Você pode configurar uma política para excluir ativos identificados por classificações de site que você especificar.</span><span class="sxs-lookup"><span data-stu-id="06dac-200">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="06dac-201">Por exemplo, você pode optar por excluir todos os ativos marcados como "restrito" ou "confidencial", mesmo que sejam um tipo de arquivo permitido e estejam localizados em uma origem pública.</span><span class="sxs-lookup"><span data-stu-id="06dac-201">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="06dac-202">Atributos e vantagens da Hospedagem de ativos em origens privadas</span><span class="sxs-lookup"><span data-stu-id="06dac-202">Attributes and advantages of hosting assets in private origins</span></span>

- <span data-ttu-id="06dac-203">Origens privadas só podem ser usadas para ativos do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-203">Private origins can only be used for SharePoint Online assets.</span></span>
- <span data-ttu-id="06dac-204">Os usuários só poderão acessar os ativos de uma origem privada se tiverem permissões para acessar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="06dac-204">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="06dac-205">O acesso anônimo a esses ativos é vetado.</span><span class="sxs-lookup"><span data-stu-id="06dac-205">Anonymous access to these assets is prevented.</span></span>
- <span data-ttu-id="06dac-206">Os ativos em origens privadas devem ser referenciados do locatário do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-206">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="06dac-207">O acesso direto aos ativos da CDN privada não funciona.</span><span class="sxs-lookup"><span data-stu-id="06dac-207">Direct access to private CDN assets does not work.</span></span>
- <span data-ttu-id="06dac-208">Se você remover um ativo da origem privada, o ativo poderá continuar disponível para até uma hora no cache; no entanto, iremos invalidar os links para o ativo na CDN dentro de 15 minutos da remoção do ativo.</span><span class="sxs-lookup"><span data-stu-id="06dac-208">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
- <span data-ttu-id="06dac-209">Os tipos de arquivo padrão incluídos para origens privadas são .gif, .ico, .jpeg, .jpg, .js e .png.</span><span class="sxs-lookup"><span data-stu-id="06dac-209">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="06dac-210">Você pode especificar tipos de arquivo adicionais.</span><span class="sxs-lookup"><span data-stu-id="06dac-210">You can specify additional file types.</span></span>
- <span data-ttu-id="06dac-211">Assim como acontece com as origens públicas, você pode configurar uma política para excluir ativos identificados por classificações de site que você especificar, mesmo se usar curingas para incluir todos os ativos de uma pasta ou biblioteca de documentos.</span><span class="sxs-lookup"><span data-stu-id="06dac-211">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="06dac-212">Para obter mais informações sobre por que usar a CDN do Office 365, conceitos gerais da CDN e outros CDNs da Microsoft que você pode usar com o seu locatário do Office 365, consulte [redes de distribuição de conteúdo](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="06dac-212">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="06dac-213">Origens de CDN padrão</span><span class="sxs-lookup"><span data-stu-id="06dac-213">Default CDN origins</span></span>

<span data-ttu-id="06dac-214">A menos que você especifique o contrário, o Office 365 configura algumas origens padrão quando você habilita a CDN do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06dac-214">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="06dac-215">Se você optar por não provisioná-los inicialmente, poderá adicionar essas origens após concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="06dac-215">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="06dac-216">A menos que você entenda as conseqüências de ignorar a configuração de origens padrão e tenha um motivo específico para fazer isso, você deve permitir que elas sejam criadas quando você habilitar a CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-216">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="06dac-217">Origens de CDN privadas padrão:</span><span class="sxs-lookup"><span data-stu-id="06dac-217">Default private CDN origins:</span></span>
  
- <span data-ttu-id="06dac-218">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="06dac-218">\*/userphoto.aspx</span></span>
- <span data-ttu-id="06dac-219">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="06dac-219">\*/siteassets</span></span>

<span data-ttu-id="06dac-220">Origens padrão da CDN pública:</span><span class="sxs-lookup"><span data-stu-id="06dac-220">Default public CDN origins:</span></span>
  
- <span data-ttu-id="06dac-221">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="06dac-221">\*/masterpage</span></span>
- <span data-ttu-id="06dac-222">\*biblioteca/Style</span><span class="sxs-lookup"><span data-stu-id="06dac-222">\*/style library</span></span>
- <span data-ttu-id="06dac-223">\*/clientsideassets</span><span class="sxs-lookup"><span data-stu-id="06dac-223">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="06dac-224">_clientsideassets_ é uma origem pública padrão que foi adicionada ao serviço de CDN do Office 365 em dezembro de 2017.</span><span class="sxs-lookup"><span data-stu-id="06dac-224">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="06dac-225">Essa origem deve estar presente para que as soluções da estrutura do SharePoint na CDN funcionem.</span><span class="sxs-lookup"><span data-stu-id="06dac-225">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="06dac-226">Se você habilitou a CDN do Office 365 antes de dezembro de 2017, ou se você ignorou a configuração de origens padrão ao habilitar a CDN, é possível adicionar manualmente essa origem.</span><span class="sxs-lookup"><span data-stu-id="06dac-226">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="06dac-227">Para obter mais informações, consulte [My client-side Web Part ou SharePoint Framework Solution não está funcionando](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span><span class="sxs-lookup"><span data-stu-id="06dac-227">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="06dac-228">Configurar e configurar a CDN do Office 365 usando o Shell de gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-228">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>
<span data-ttu-id="06dac-229"><a name="CDNSetupinPShell"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-229"></span></span>

<span data-ttu-id="06dac-230">Os procedimentos nesta seção exigem que você use o Shell de gerenciamento do SharePoint Online para se conectar ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-230">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="06dac-231">Para obter instruções, consulte [conectar-se ao PowerShell do SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="06dac-231">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="06dac-232">Conclua estas etapas para configurar e configurar a CDN para hospedar seus ativos no SharePoint online usando o Shell de gerenciamento do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-232">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="06dac-233">Habilitar sua organização para usar a CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-233">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="06dac-234">Antes de fazer alterações nas configurações de CDN do locatário, você deve recuperar o status atual da configuração de CDN privada em seu locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06dac-234">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="06dac-235">Conecte-se ao seu locatário usando o Shell de gerenciamento do SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="06dac-235">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="06dac-236">Agora use o cmdlet **Get-SPOTenantCdnEnabled** para recuperar as configurações de status de CDN do locatário:</span><span class="sxs-lookup"><span data-stu-id="06dac-236">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="06dac-237">O status da CDN para o CdnType especificado fará a saída para a tela.</span><span class="sxs-lookup"><span data-stu-id="06dac-237">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="06dac-238">Use o cmdlet **set-SPOTenantCdnEnabled** para permitir que sua organização Use a CDN do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06dac-238">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="06dac-239">Você pode habilitar sua organização para usar origens públicas, origens privadas ou ambas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="06dac-239">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="06dac-240">Você também pode configurar a CDN para ignorar a configuração de origens padrão ao ativá-la.</span><span class="sxs-lookup"><span data-stu-id="06dac-240">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="06dac-241">Você sempre pode adicionar essas origens mais tarde, conforme descrito neste tópico.</span><span class="sxs-lookup"><span data-stu-id="06dac-241">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="06dac-242">No Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="06dac-242">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="06dac-243">Por exemplo, para permitir que sua organização Use origens públicas e privadas, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="06dac-243">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="06dac-244">Para permitir que sua organização Use origens públicas e privadas, mas ignore a configuração das origens padrão, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="06dac-244">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="06dac-245">Consulte [origens de CDN padrão](use-office-365-cdn-with-spo.md#default-cdn-origins) para obter informações sobre as origens que são provisionadas por padrão quando você HABILITA a CDN do Office 365 e o impacto potencial de ignorar a configuração de origens padrão.</span><span class="sxs-lookup"><span data-stu-id="06dac-245">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="06dac-246">Para permitir que sua organização Use origens públicas, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="06dac-246">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="06dac-247">Para permitir que sua organização Use origens privadas, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="06dac-247">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="06dac-248">Para obter mais informações sobre esse cmdlet, consulte [set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-248">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="06dac-249">Alterar a lista de tipos de arquivo a serem incluídos na CDN do Office 365 (opcional)</span><span class="sxs-lookup"><span data-stu-id="06dac-249">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>
<span data-ttu-id="06dac-250"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-250"></span></span>

> [!TIP]
> <span data-ttu-id="06dac-251">Ao definir tipos de arquivo usando o cmdlet **set-SPOTenantCdnPolicy** , você substitui a lista definida no momento.</span><span class="sxs-lookup"><span data-stu-id="06dac-251">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="06dac-252">Se quiser adicionar outros tipos de arquivo à lista, use o cmdlet primeiro para descobrir quais tipos de arquivo já são permitidos e incluí-los na lista junto com os novos.</span><span class="sxs-lookup"><span data-stu-id="06dac-252">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="06dac-253">Use o cmdlet **set-SPOTenantCdnPolicy** para definir tipos de arquivos estáticos que podem ser hospedados por origens públicas e privadas na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-253">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="06dac-254">Por padrão, tipos de ativos comuns são permitidos, por exemplo. CSS,. gif,. jpg e. js.</span><span class="sxs-lookup"><span data-stu-id="06dac-254">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="06dac-255">No Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="06dac-255">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="06dac-256">Por exemplo, para habilitar a CDN para os arquivos host. css e. png, você deve inserir o comando:</span><span class="sxs-lookup"><span data-stu-id="06dac-256">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="06dac-257">Para ver quais tipos de arquivo são permitidos atualmente pela CDN, use o cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="06dac-257">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="06dac-258">Para obter mais informações sobre esses cmdlets, consulte [set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-258">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="06dac-259">Alterar a lista de classificações de site que você deseja excluir da CDN do Office 365 (opcional)</span><span class="sxs-lookup"><span data-stu-id="06dac-259">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>
<span data-ttu-id="06dac-260"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-260"></span></span>

> [!TIP]
> <span data-ttu-id="06dac-261">Quando você exclui as classificações de site usando o cmdlet **set-SPOTenantCdnPolicy** , você substitui a lista definida no momento.</span><span class="sxs-lookup"><span data-stu-id="06dac-261">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="06dac-262">Se você deseja excluir classificações de site adicionais, use o cmdlet primeiro para descobrir quais classificações já foram excluídas e, em seguida, adicione-as junto com as novas.</span><span class="sxs-lookup"><span data-stu-id="06dac-262">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="06dac-263">Use o cmdlet **Set-SPOTenantCdnPolicy** para excluir as classificações de site que não deseja disponibilizar na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-263">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="06dac-264">Por padrão, nenhuma classificação de sites é excluída.</span><span class="sxs-lookup"><span data-stu-id="06dac-264">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="06dac-265">No Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="06dac-265">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="06dac-266">Para ver quais classificações de site estão restritas no momento, use o cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="06dac-266">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="06dac-267">As propriedades que serão retornadas são _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ e _ExcludeIfNoScriptDisabled_.</span><span class="sxs-lookup"><span data-stu-id="06dac-267">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="06dac-268">A propriedade _IncludeFileExtensions_ contém a lista de extensões de arquivo que serão servidas da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-268">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="06dac-269">As extensões de arquivo padrão são diferentes entre Public e Private.</span><span class="sxs-lookup"><span data-stu-id="06dac-269">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="06dac-270">A propriedade _ExcludeRestrictedSiteClassifications_ contém as classificações de site que você deseja excluir da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-270">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="06dac-271">Por exemplo, você pode excluir sites marcados como **confidenciais** , de modo que o conteúdo de sites com essa classificação aplicada não será atendido da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-271">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="06dac-272">A propriedade _ExcludeIfNoScriptDisabled_ exclui o conteúdo da CDN com base nas configurações de atributo noscript no nível do site. __</span><span class="sxs-lookup"><span data-stu-id="06dac-272">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="06dac-273">Por padrão, o __ atributo noscript é definido como **habilitado** para sites _modernos_ e **desabilitado** para sites _clássicos_ .</span><span class="sxs-lookup"><span data-stu-id="06dac-273">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="06dac-274">Isso depende de suas configurações de locatário.</span><span class="sxs-lookup"><span data-stu-id="06dac-274">This depends on your tenant settings.</span></span>

<span data-ttu-id="06dac-275">Para obter mais informações sobre esses cmdlets, consulte [set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-275">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="06dac-276">Adicionar uma origem para seus ativos</span><span class="sxs-lookup"><span data-stu-id="06dac-276">Add an origin for your assets</span></span>
<span data-ttu-id="06dac-277"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-277"></span></span>

<span data-ttu-id="06dac-278">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir uma origem.</span><span class="sxs-lookup"><span data-stu-id="06dac-278">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="06dac-279">Você pode definir várias origens.</span><span class="sxs-lookup"><span data-stu-id="06dac-279">You can define multiple origins.</span></span> <span data-ttu-id="06dac-280">A origem é uma URL que aponta para uma biblioteca ou pasta do SharePoint contendo os ativos que você deseja hospedar na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-280">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="06dac-281">Você nunca deve colocar recursos que contenham informações de usuário ou são considerados confidenciais para sua organização em uma origem pública.</span><span class="sxs-lookup"><span data-stu-id="06dac-281">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="06dac-282">O valor de _path_ é o caminho relativo para a biblioteca ou pasta que contém os ativos.</span><span class="sxs-lookup"><span data-stu-id="06dac-282">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="06dac-283">Você pode usar caracteres curinga, além de caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="06dac-283">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="06dac-284">As origens dão suporte a curingas precedidas à URL.</span><span class="sxs-lookup"><span data-stu-id="06dac-284">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="06dac-285">Isso permite criar origens que abrangem vários sites.</span><span class="sxs-lookup"><span data-stu-id="06dac-285">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="06dac-286">Por exemplo, para incluir todos os ativos na pasta masterpages de todos os sites como uma origem pública dentro da CDN, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="06dac-286">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- <span data-ttu-id="06dac-287">O modificador curinga**/** \* só pode ser usado no início do caminho e corresponderá a todos os segmentos de URL na URL especificada.</span><span class="sxs-lookup"><span data-stu-id="06dac-287">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
- <span data-ttu-id="06dac-288">O caminho pode apontar para uma biblioteca de documentos, pasta ou site.</span><span class="sxs-lookup"><span data-stu-id="06dac-288">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="06dac-289">Por exemplo, o caminho _\*/site1_ corresponderá a todas as bibliotecas de documentos no site.</span><span class="sxs-lookup"><span data-stu-id="06dac-289">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="06dac-290">Você pode adicionar uma origem com um caminho relativo específico.</span><span class="sxs-lookup"><span data-stu-id="06dac-290">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="06dac-291">Não é possível adicionar uma origem usando o caminho completo.</span><span class="sxs-lookup"><span data-stu-id="06dac-291">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="06dac-292">Este exemplo adiciona uma origem privada da biblioteca siteassets em um site específico:</span><span class="sxs-lookup"><span data-stu-id="06dac-292">This example adds a private origin of the siteassets library on a specific site:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="06dac-293">Este exemplo adiciona uma origem privada da pasta _Pasta1_ na biblioteca de ativos do site do conjunto de sites:</span><span class="sxs-lookup"><span data-stu-id="06dac-293">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “/sites/test/siteassets/folder1”
```

<span data-ttu-id="06dac-294">Para obter mais informações sobre este comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-294">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="06dac-295">Em origens privadas, os ativos que estão sendo compartilhados a partir de uma origem devem ter uma versão principal publicada antes que possam ser acessadas da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-295">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="06dac-296">Depois de executar o comando, o sistema sincroniza a configuração no datacenter.</span><span class="sxs-lookup"><span data-stu-id="06dac-296">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="06dac-297">Isso pode levar até 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="06dac-297">This can take up to 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="06dac-298">Exemplo: Configure uma origem pública para suas páginas mestras e para sua biblioteca de estilos para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-298">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="06dac-299"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-299"></span></span>

<span data-ttu-id="06dac-300">Normalmente, essas origens são configuradas por padrão quando você habilita a CDN do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06dac-300">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="06dac-301">No entanto, se você quiser habilitá-los manualmente, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="06dac-301">However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="06dac-302">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a biblioteca de estilos como uma origem pública.</span><span class="sxs-lookup"><span data-stu-id="06dac-302">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="06dac-303">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir as páginas mestras como uma origem pública.</span><span class="sxs-lookup"><span data-stu-id="06dac-303">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="06dac-304">Para obter mais informações sobre este comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-304">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="06dac-305">Depois de executar o comando, o sistema sincroniza a configuração no datacenter.</span><span class="sxs-lookup"><span data-stu-id="06dac-305">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="06dac-306">Isso pode levar até 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="06dac-306">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="06dac-307">Exemplo: configurar uma origem privada para seus ativos de site, páginas de site e imagens de publicação para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-307">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="06dac-308"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-308"></span></span>

- <span data-ttu-id="06dac-309">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de ativos do site como uma origem privada.</span><span class="sxs-lookup"><span data-stu-id="06dac-309">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="06dac-310">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de páginas do site como uma origem privada.</span><span class="sxs-lookup"><span data-stu-id="06dac-310">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="06dac-311">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de imagens de publicação como uma origem privada.</span><span class="sxs-lookup"><span data-stu-id="06dac-311">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="06dac-312">Para obter mais informações sobre este comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-312">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="06dac-313">Depois de executar o comando, o sistema sincroniza a configuração no datacenter.</span><span class="sxs-lookup"><span data-stu-id="06dac-313">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="06dac-314">Isso pode levar até 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="06dac-314">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="06dac-315">Exemplo: configurar uma origem privada para um conjunto de sites para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-315">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="06dac-316"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-316"></span></span>

<span data-ttu-id="06dac-317">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir um conjunto de sites como uma origem privada.</span><span class="sxs-lookup"><span data-stu-id="06dac-317">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="06dac-318">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="06dac-318">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="06dac-319">Para obter mais informações sobre este comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-319">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="06dac-320">Depois de executar o comando, o sistema sincroniza a configuração no datacenter.</span><span class="sxs-lookup"><span data-stu-id="06dac-320">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="06dac-321">Você pode ver uma mensagem de _configuração pendente_ que é esperado, pois o locatário do SharePoint Online se conecta ao serviço de CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-321">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="06dac-322">Isso pode levar até 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="06dac-322">This can take up to 15 minutes.</span></span>

### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="06dac-323">Gerenciar a CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-323">Manage the Office 365 CDN</span></span>
<span data-ttu-id="06dac-324"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-324"></span></span>

<span data-ttu-id="06dac-325">Depois de configurar a CDN, você pode fazer alterações na configuração ao atualizar o conteúdo ou à medida que suas necessidades mudam, conforme descrito nesta seção.</span><span class="sxs-lookup"><span data-stu-id="06dac-325">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="06dac-326">Adicionar, atualizar ou remover ativos da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-326">Add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="06dac-327"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-327"></span></span>

<span data-ttu-id="06dac-328">Depois de concluir as etapas de configuração, você pode adicionar novos ativos e atualizar ou remover ativos existentes sempre que desejar.</span><span class="sxs-lookup"><span data-stu-id="06dac-328">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="06dac-329">Basta fazer suas alterações nos ativos na pasta ou na biblioteca do SharePoint que você identificou como origem.</span><span class="sxs-lookup"><span data-stu-id="06dac-329">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="06dac-330">Se você adicionar um novo ativo, ele estará disponível através da CDN imediatamente.</span><span class="sxs-lookup"><span data-stu-id="06dac-330">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="06dac-331">No entanto, se você atualizar o ativo, levará até 15 minutos para que a nova cópia se propague e fique disponível na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-331">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="06dac-332">Se for necessário recuperar o local da origem, você poderá usar o cmdlet **Get-SPOTenantCdnOrigins** .</span><span class="sxs-lookup"><span data-stu-id="06dac-332">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="06dac-333">Para obter informações sobre como usar esse cmdlet, consulte [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-333">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="06dac-334">Remover uma origem da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-334">Remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="06dac-335"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-335"></span></span>

<span data-ttu-id="06dac-336">Você pode remover o acesso a uma pasta ou biblioteca do SharePoint que você identificou como origem.</span><span class="sxs-lookup"><span data-stu-id="06dac-336">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="06dac-337">Para fazer isso, use o cmdlet **Remove-SPOTenantCdnOrigin** .</span><span class="sxs-lookup"><span data-stu-id="06dac-337">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="06dac-338">Para obter informações sobre como usar esse cmdlet, consulte [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-338">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="06dac-339">Modificar uma origem na CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-339">Modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="06dac-340"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-340"></span></span>

<span data-ttu-id="06dac-341">Não é possível modificar uma origem que você criou.</span><span class="sxs-lookup"><span data-stu-id="06dac-341">You cannot modify an origin you've created.</span></span> <span data-ttu-id="06dac-342">Em vez disso, remova a origem e adicione uma nova.</span><span class="sxs-lookup"><span data-stu-id="06dac-342">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="06dac-343">Para obter mais informações, consulte [para remover uma origem da CDN do Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) e [Adicionar uma origem para seus ativos](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="06dac-343">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="06dac-344">Desabilitar a CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-344">Disable the Office 365 CDN</span></span>
<span data-ttu-id="06dac-345"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-345"></span></span>

<span data-ttu-id="06dac-346">Use o cmdlet **set-SPOTenantCdnEnabled** para desabilitar a CDN para sua organização.</span><span class="sxs-lookup"><span data-stu-id="06dac-346">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="06dac-347">Se você tiver as origens pública e privada habilitadas para a CDN, será necessário executar o cmdlet duas vezes, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="06dac-347">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="06dac-348">Para desabilitar o uso de origens públicas na CDN, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="06dac-348">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="06dac-349">Para desabilitar o uso das origens privadas na CDN, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="06dac-349">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="06dac-350">Para obter mais informações sobre esse cmdlet, consulte [set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="06dac-350">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="06dac-351">Instalação e configuração da CDN do Office 365 usando a CLI do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-351">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>
<span data-ttu-id="06dac-352"><a name="CDNSetupinCLI"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-352"></span></span>

<span data-ttu-id="06dac-353">Os procedimentos nesta seção exigem que você tenha instalado a [CLI do Office 365](https://aka.ms/o365cli).</span><span class="sxs-lookup"><span data-stu-id="06dac-353">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="06dac-354">Em seguida, conecte-se ao locatário do SharePoint Online usando o comando [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/).</span><span class="sxs-lookup"><span data-stu-id="06dac-354">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="06dac-355">Conclua estas etapas para configurar e configurar a CDN para hospedar seus ativos no SharePoint online usando a CLI do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06dac-355">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="06dac-356">Habilitar a CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-356">Enable the Office 365 CDN</span></span>

<span data-ttu-id="06dac-357">Você pode gerenciar o estado da CDN do Office 365 no locatário usando o comando [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/).</span><span class="sxs-lookup"><span data-stu-id="06dac-357">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="06dac-358">Para habilitar a CDN pública do Office 365 no locatário:</span><span class="sxs-lookup"><span data-stu-id="06dac-358">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="06dac-359">Para habilitar a CDN do Office 365 SharePoint, execute:</span><span class="sxs-lookup"><span data-stu-id="06dac-359">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="06dac-360">Exiba o status atual da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-360">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="06dac-361">Para verificar se o tipo específico de CDN do Office 365 está habilitado ou desabilitado, use o comando [SPO CDN Get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) .</span><span class="sxs-lookup"><span data-stu-id="06dac-361">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="06dac-362">Para verificar se a CDN pública do Office 365 está habilitada:</span><span class="sxs-lookup"><span data-stu-id="06dac-362">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="06dac-363">Exibir as origens de CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-363">View the Office 365 CDN origins</span></span>

<span data-ttu-id="06dac-364">Para exibir as origens de CDN pública do Office 365 configuradas no momento:</span><span class="sxs-lookup"><span data-stu-id="06dac-364">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="06dac-365">Consulte [origens de CDN padrão](use-office-365-cdn-with-spo.md#default-cdn-origins) para obter informações sobre as origens que são provisionadas por padrão quando você HABILITA a CDN do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06dac-365">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="06dac-366">Adicionar uma origem de CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-366">Add an Office 365 CDN origin</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06dac-367">Você nunca deve colocar os recursos considerados confidenciais para sua organização em uma biblioteca de documentos do SharePoint configurada como uma origem pública.</span><span class="sxs-lookup"><span data-stu-id="06dac-367">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="06dac-368">Use o adicionar comando [spo cdn origem ](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) para definir uma origem de CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-368">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="06dac-369">Você pode definir várias origens.</span><span class="sxs-lookup"><span data-stu-id="06dac-369">You can define multiple origins.</span></span> <span data-ttu-id="06dac-370">A origem é uma URL que aponta para uma biblioteca ou pasta do SharePoint contendo os ativos que você deseja hospedar na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-370">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="06dac-371">Em `path` que é o caminho relativo para a pasta que contém os ativos.</span><span class="sxs-lookup"><span data-stu-id="06dac-371">Where `path` is the relative path to the folder that contains the assets.</span></span> <span data-ttu-id="06dac-372">Você pode usar caracteres curinga, além de caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="06dac-372">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="06dac-373">Para incluir todos os ativos da **Galeria de páginas mestras** de todos os sites como uma origem pública, execute:</span><span class="sxs-lookup"><span data-stu-id="06dac-373">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="06dac-374">Para configurar uma origem privada para um conjunto de sites específico:</span><span class="sxs-lookup"><span data-stu-id="06dac-374">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="06dac-375">Após adicionar uma origem de CDN, pode levar até 15 minutos para que você possa recuperar arquivos por meio do serviço de CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-375">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="06dac-376">Você pode verificar se a origem específica já foi ativada usando o comando [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/).</span><span class="sxs-lookup"><span data-stu-id="06dac-376">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="06dac-377">Remover uma origem de CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-377">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="06dac-378">Use o comando [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) para remover uma origem de CDN para o tipo de CDN especificado.</span><span class="sxs-lookup"><span data-stu-id="06dac-378">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="06dac-379">Para remover uma origem pública da configuração de CDN, execute:</span><span class="sxs-lookup"><span data-stu-id="06dac-379">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="06dac-380">Remover uma origem de CDN não afeta os arquivos armazenados em qualquer biblioteca de documentos que corresponde a essa origem.</span><span class="sxs-lookup"><span data-stu-id="06dac-380">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="06dac-381">Se esses ativos tiverem sido referenciados usando a URL do SharePoint, o SharePoint voltará automaticamente para a URL original apontando para a biblioteca de documentos.</span><span class="sxs-lookup"><span data-stu-id="06dac-381">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="06dac-382">No entanto, se os ativos tiverem sido referenciados usando uma URL de CDN pública, a remoção da origem quebrará o link e você precisará alterá-las manualmente.</span><span class="sxs-lookup"><span data-stu-id="06dac-382">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="06dac-383">Modificar uma origem de CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-383">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="06dac-384">Não é possível alterar uma origem de CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-384">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="06dac-385">Em vez disso, você deve remover a origem de CDN definida anteriormente usando o comando `spo cdn origin remove` e adicionar outro usando o comando `spo cdn origin add`.</span><span class="sxs-lookup"><span data-stu-id="06dac-385">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="06dac-386">Alterar os tipos de arquivos a serem incluídos na CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-386">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="06dac-387">Por padrão, os seguintes tipos de arquivo estão incluídos na CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, png, .svg, .ttf e .woff_.</span><span class="sxs-lookup"><span data-stu-id="06dac-387">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="06dac-388">Se precisar incluir outros tipos de arquivo na CDN, você pode alterar a configuração de CDN usando o comando [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).</span><span class="sxs-lookup"><span data-stu-id="06dac-388">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="06dac-389">Ao alterar a lista de tipos de arquivo, você substitui a lista definida no momento.</span><span class="sxs-lookup"><span data-stu-id="06dac-389">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="06dac-390">Se quiser incluir outros tipos de arquivo, primeiro use o comando [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) para descobrir quais tipos de arquivo estão configurados no momento.</span><span class="sxs-lookup"><span data-stu-id="06dac-390">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="06dac-391">Para adicionar o tipo de arquivo _JSON_ à lista padrão de tipos de arquivo incluídos na CDN pública, execute:</span><span class="sxs-lookup"><span data-stu-id="06dac-391">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="06dac-392">Altere a lista de classificações de site que você deseja excluir da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-392">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="06dac-393">Use o comando [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) para excluir as classificações de site que não deseja disponibilizar na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-393">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="06dac-394">Por padrão, nenhuma classificação de sites é excluída.</span><span class="sxs-lookup"><span data-stu-id="06dac-394">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="06dac-395">Ao alterar a lista de classificações de sites excluída, você substitui a lista definida no momento.</span><span class="sxs-lookup"><span data-stu-id="06dac-395">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="06dac-396">Se desejar excluir outras classificações, primeiro use o comando [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) para descobrir quais classificações estão configuradas no momento.</span><span class="sxs-lookup"><span data-stu-id="06dac-396">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="06dac-397">Para excluir sites classificados como _Ain_ da CDN pública, execute</span><span class="sxs-lookup"><span data-stu-id="06dac-397">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="06dac-398">Desabilitar a CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-398">Disable the Office 365 CDN</span></span>

<span data-ttu-id="06dac-399">Para desabilitar a CDN do Office 365, use o comando `spo cdn set`, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="06dac-399">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a><span data-ttu-id="06dac-400">Usando seus ativos de CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-400">Using your CDN assets</span></span>

<span data-ttu-id="06dac-401">Agora que você ativou a CDN e as origens e políticas configuradas, você pode começar a usar seus ativos da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-401">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="06dac-402">Esta seção o ajudará a entender como usar URLs de CDN em suas páginas e conteúdo do SharePoint para que o SharePoint redirecione solicitações de ativos em origens públicas e privadas para a CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-402">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

- [<span data-ttu-id="06dac-403">Atualizando links para ativos da CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-403">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [<span data-ttu-id="06dac-404">Usando ativos em origens públicas</span><span class="sxs-lookup"><span data-stu-id="06dac-404">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [<span data-ttu-id="06dac-405">Usando ativos em origens privadas</span><span class="sxs-lookup"><span data-stu-id="06dac-405">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="06dac-406">Para obter informações sobre como usar a CDN para hospedar Web Parts do lado do cliente, consulte o tópico [hospedar a Web Part do lado do cliente do Office 365 CDN (Hello World parte 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span><span class="sxs-lookup"><span data-stu-id="06dac-406">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="06dac-407">Atualizando links para ativos da CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-407">Updating links to CDN assets</span></span>

<span data-ttu-id="06dac-408">Para usar os ativos que você adicionou a uma origem, basta atualizar os links para o arquivo original com o caminho para o arquivo na origem.</span><span class="sxs-lookup"><span data-stu-id="06dac-408">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

- <span data-ttu-id="06dac-409">Edite a página ou o conteúdo que contém links para os ativos que você adicionou a uma origem.</span><span class="sxs-lookup"><span data-stu-id="06dac-409">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="06dac-410">Você também pode usar um dos vários métodos para pesquisar e substituir globalmente links em um determinado site ou conjunto de sites, se você quiser atualizar o link para um determinado ativo em qualquer lugar em que ele for exibido.</span><span class="sxs-lookup"><span data-stu-id="06dac-410">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
- <span data-ttu-id="06dac-411">Para cada link com um ativo em uma origem, substitua o caminho com o caminho para o arquivo na origem da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-411">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="06dac-412">Você pode usar caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="06dac-412">You can use relative paths.</span></span>
- <span data-ttu-id="06dac-413">Salve a página ou o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="06dac-413">Save the page or content.</span></span>

<span data-ttu-id="06dac-414">Por exemplo, considere a imagem _/site/SiteAssets/images/Image.png_, que você copiou para a pasta da biblioteca de documentos _/site/CDN_origins/Public/_.</span><span class="sxs-lookup"><span data-stu-id="06dac-414">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="06dac-415">Para usar o ativo da CDN, substitua o caminho original para o local do arquivo de imagem com o caminho para a origem para tornar a nova URL _/site/CDN_origins/Public/Image.png_.</span><span class="sxs-lookup"><span data-stu-id="06dac-415">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="06dac-416">Se você quiser usar a URL completa para o ativo em vez de um caminho relativo, construa o link da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="06dac-416">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="06dac-417">Em geral, você não deve codificar URLs diretamente para os ativos na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-417">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="06dac-418">No entanto, você pode criar manualmente URLs para ativos em origens públicas, se necessário.</span><span class="sxs-lookup"><span data-stu-id="06dac-418">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="06dac-419">Para obter mais informações, consulte [codificar URLs da CDN para ativos públicos](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span><span class="sxs-lookup"><span data-stu-id="06dac-419">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="06dac-420">Para saber mais sobre como verificar se os ativos estão sendo servidos da CDN, confira [como confirmar se os ativos estão sendo servidos pela CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) na seção [solução de problemas do Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="06dac-420">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="06dac-421">Usando ativos em origens públicas</span><span class="sxs-lookup"><span data-stu-id="06dac-421">Using assets in public origins</span></span>

<span data-ttu-id="06dac-422">O **recurso de publicação** no SharePoint Online reconfigura automaticamente as URLs de ativos armazenados em origens públicas para seus equivalentes de CDN, para que os ativos sejam servidos do serviço CDN, e não do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="06dac-422">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="06dac-423">Se sua origem estiver em um site com o recurso de publicação habilitado e os ativos que você deseja descarregar para a CDN estiverem em uma das seguintes categorias, o SharePoint reescreverá automaticamente as URLs dos ativos na origem, desde que o ativo não tenha sido excluído por uma CDN  política.</span><span class="sxs-lookup"><span data-stu-id="06dac-423">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="06dac-424">Mostramos a seguir uma visão geral dos links reescritos automaticamente pelo recurso de Publicação do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="06dac-424">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

- <span data-ttu-id="06dac-425">URLs IMG/LINK/CSS em respostas de HTML de página de publicação clássica</span><span class="sxs-lookup"><span data-stu-id="06dac-425">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  - <span data-ttu-id="06dac-426">Incluem-se imagens adicionadas por autores no conteúdo HTML de uma página</span><span class="sxs-lookup"><span data-stu-id="06dac-426">This includes images added by authors within the HTML content of a page</span></span>
- <span data-ttu-id="06dac-427">URLs de imagem da web part Apresentação de Slides da Biblioteca de Imagens</span><span class="sxs-lookup"><span data-stu-id="06dac-427">Picture Library SlideShow webpart image URLs</span></span>
- <span data-ttu-id="06dac-428">Campos de imagem nos resultados da API REST SPList (RenderListDataAsStream)</span><span class="sxs-lookup"><span data-stu-id="06dac-428">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  - <span data-ttu-id="06dac-429">Use a nova propriedade _ImageFieldsToTryRewriteToCdnUrls_ para fornecer uma lista separada por vírgulas de campos</span><span class="sxs-lookup"><span data-stu-id="06dac-429">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  - <span data-ttu-id="06dac-430">Suporta campos de hiperlink e campos PublishingImage</span><span class="sxs-lookup"><span data-stu-id="06dac-430">Supports hyperlink fields and PublishingImage fields</span></span>
- <span data-ttu-id="06dac-431">Renderizações de imagem do SharePoint</span><span class="sxs-lookup"><span data-stu-id="06dac-431">SharePoint image renditions</span></span>

<span data-ttu-id="06dac-432">O diagrama a seguir ilustra o fluxo de trabalho quando o SharePoint recebe uma solicitação para uma página contendo ativos de uma origem pública.</span><span class="sxs-lookup"><span data-stu-id="06dac-432">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="06dac-433">![Diagrama de fluxo de trabalho: recuperação de ativos de CDN do Office 365 de uma origem pública] (media/O365-CDN/o365-cdn-public-steps-transparent.svg "Fluxo de trabalho: recuperação de ativos de CDN do Office 365 de uma origem pública")</span><span class="sxs-lookup"><span data-stu-id="06dac-433">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="06dac-434">Se quiser desabilitar a reconfiguração automática para URLs específicas em uma página, você pode fazer o check-out da página e adicionar o parâmetro de cadeia de caracteres de consulta **?NoAutoReWrites = true** ao final de cada link que você deseja desabilitar.</span><span class="sxs-lookup"><span data-stu-id="06dac-434">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="06dac-435">Codificar URLs de CDN para ativos públicos</span><span class="sxs-lookup"><span data-stu-id="06dac-435">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="06dac-436">Se o recurso de _publicação_ não estiver habilitado para uma origem pública ou se o ativo não for um dos tipos de link suportados pelo recurso de regravação automática do serviço CDN, você poderá construir URLs manualmente para o local da CDN dos ativos e usar essas URLs em seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="06dac-436">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="06dac-437">Você não pode codificar URLs CDN para ativos em uma origem privada, pois o token de acesso necessário que forma a última seção da URL é gerado no momento em que o recurso é solicitado.</span><span class="sxs-lookup"><span data-stu-id="06dac-437">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="06dac-438">Para ativos da CDN pública, o formato da URL terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="06dac-438">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="06dac-439">Substitua **TenantHostName** pelo nome do seu locatário.</span><span class="sxs-lookup"><span data-stu-id="06dac-439">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="06dac-440">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="06dac-440">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="06dac-441">Usando ativos em origens privadas</span><span class="sxs-lookup"><span data-stu-id="06dac-441">Using assets in private origins</span></span>

<span data-ttu-id="06dac-442">Nenhuma configuração adicional é necessária para usar ativos em origens privadas.</span><span class="sxs-lookup"><span data-stu-id="06dac-442">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="06dac-443">O SharePoint Online reconfigura automaticamente as URLs de ativos em origens privadas para que as solicitações desses ativos sejam sempre servidas da CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-443">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="06dac-444">Você não pode criar URLs manualmente para ativos da CDN em origens privadas, pois essas URLs contêm tokens que devem ser gerados automaticamente pelo SharePoint Online no momento em que o ativo for solicitado.</span><span class="sxs-lookup"><span data-stu-id="06dac-444">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="06dac-445">O acesso a ativos em origens privadas é protegido por tokens gerados dinamicamente com base nas permissões do usuário para a origem, com as advertências descritas nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="06dac-445">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="06dac-446">Os usuários devem ter pelo menos acesso de **leitura** às origens da CDN para renderizar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="06dac-446">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="06dac-447">O diagrama a seguir ilustra o fluxo de trabalho quando o SharePoint recebe uma solicitação para uma página contendo ativos de uma origem privada.</span><span class="sxs-lookup"><span data-stu-id="06dac-447">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="06dac-448">![Diagrama de fluxo de trabalho: recuperação de ativos de CDN do Office 365 de uma origem privada] (media/O365-CDN/o365-cdn-private-steps-transparent.svg "Fluxo de trabalho: recuperação de ativos de CDN do Office 365 de uma origem privada")</span><span class="sxs-lookup"><span data-stu-id="06dac-448">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="06dac-449">Autorização baseada em token em origens privadas</span><span class="sxs-lookup"><span data-stu-id="06dac-449">Token-based authorization in private origins</span></span>

<span data-ttu-id="06dac-450">O acesso a ativos em origens privadas na CDN do Office 365 é concedido por tokens gerados pelo SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-450">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="06dac-451">Os usuários que já têm permissão para acessar a pasta ou a biblioteca designada pela origem recebem tokens automaticamente que permitem que o usuário acesse o arquivo com base em seu nível de permissão.</span><span class="sxs-lookup"><span data-stu-id="06dac-451">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="06dac-452">Esses tokens de acesso são válidos por 30 a 90 minutos após serem gerados para ajudar a evitar ataques de repetição de token.</span><span class="sxs-lookup"><span data-stu-id="06dac-452">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="06dac-453">Depois que o token de acesso é gerado, o SharePoint Online retorna um URI personalizado ao cliente contendo dois __ parâmetros de autorização (token de autorização de borda) e _OAT_ (token de autorização de origem).</span><span class="sxs-lookup"><span data-stu-id="06dac-453">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="06dac-454">A estrutura de cada token é _<'expiration tempo no tempo de época Format'>__<'secure signature'>_.</span><span class="sxs-lookup"><span data-stu-id="06dac-454">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="06dac-455">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="06dac-455">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="06dac-456">Qualquer pessoa em posse do token pode acessar o recurso na CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-456">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="06dac-457">No entanto, URLs contendo esses tokens de acesso são compartilhados somente por HTTPS, então, a menos que a URL seja explicitamente compartilhada por um usuário final antes que o token expire, o ativo não poderá ser acessado por usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="06dac-457">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="06dac-458">Permissões de nível de item não são suportadas para ativos em origens privadas</span><span class="sxs-lookup"><span data-stu-id="06dac-458">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="06dac-459">É importante observar que o SharePoint Online não suporta permissões no nível do item para ativos em origens privadas.</span><span class="sxs-lookup"><span data-stu-id="06dac-459">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="06dac-460">Por exemplo, para um arquivo localizado em `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, os usuários têm acesso efetivo ao arquivo de acordo com as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="06dac-460">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="06dac-461">Usuário</span><span class="sxs-lookup"><span data-stu-id="06dac-461">User</span></span>  |<span data-ttu-id="06dac-462">Permissões</span><span class="sxs-lookup"><span data-stu-id="06dac-462">Permissions</span></span>  |<span data-ttu-id="06dac-463">Acesso efetivo</span><span class="sxs-lookup"><span data-stu-id="06dac-463">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="06dac-464">Usuário 1</span><span class="sxs-lookup"><span data-stu-id="06dac-464">User 1</span></span>     |<span data-ttu-id="06dac-465">Tem acesso à Pasta1</span><span class="sxs-lookup"><span data-stu-id="06dac-465">Has access to folder1</span></span>         |<span data-ttu-id="06dac-466">Pode acessar o image1. jpg da CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-466">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="06dac-467">Usuário 2</span><span class="sxs-lookup"><span data-stu-id="06dac-467">User 2</span></span>     |<span data-ttu-id="06dac-468">Não tem acesso à Pasta1</span><span class="sxs-lookup"><span data-stu-id="06dac-468">Does not have access to folder1</span></span>         |<span data-ttu-id="06dac-469">Não é possível acessar image1. jpg da CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-469">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="06dac-470">Usuário 3</span><span class="sxs-lookup"><span data-stu-id="06dac-470">User 3</span></span>     |<span data-ttu-id="06dac-471">Não tem acesso à Pasta1, mas recebeu permissão explícita para acessar o image1. jpg no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-471">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="06dac-472">Pode acessar o Asset image1. jpg diretamente do SharePoint Online, mas não da CDN</span><span class="sxs-lookup"><span data-stu-id="06dac-472">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="06dac-473">Usuário 4</span><span class="sxs-lookup"><span data-stu-id="06dac-473">User 4</span></span>     |<span data-ttu-id="06dac-474">Tem acesso à Pasta1, mas teve o acesso explicitamente negado a image1. jpg no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-474">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="06dac-475">Não é possível acessar o ativo do SharePoint Online, mas pode acessar o ativo da CDN apesar de ter sido negado o acesso ao arquivo no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-475">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="06dac-476">Solucionando problemas da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-476">Troubleshooting the Office 365 CDN</span></span>
<span data-ttu-id="06dac-477"><a name="CDNTroubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-477"></span></span>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="06dac-478">Como posso confirmar se os ativos estão sendo servidos pela CDN?</span><span class="sxs-lookup"><span data-stu-id="06dac-478">How do I confirm that assets are being served by the CDN?</span></span>
<span data-ttu-id="06dac-479"><a name="CDNConfirm"> </a></span><span class="sxs-lookup"><span data-stu-id="06dac-479"></span></span>

<span data-ttu-id="06dac-480">Depois de adicionar links aos ativos da CDN a uma página, você pode confirmar se o ativo está sendo servido da CDN, navegando até a página, clicando com o botão direito do mouse na imagem depois de renderizar e revisar a URL da imagem.</span><span class="sxs-lookup"><span data-stu-id="06dac-480">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="06dac-481">Você também pode usar as ferramentas de desenvolvedor do navegador para exibir a URL de cada ativo em uma página ou usar uma ferramenta de rastreamento de rede de terceiros.</span><span class="sxs-lookup"><span data-stu-id="06dac-481">You can also use your browser's developer tools to view the URL for each asset on a page, or use a 3rd party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="06dac-482">Se você usar uma ferramenta de rede como o Fiddler para testar seus ativos fora do processamento do ativo de uma página do SharePoint, você deve adicionar manualmente o cabeçalho referenciado `https://yourdomain.sharepoint.com`"referenciador" à solicitação GET, onde a URL é a URL raiz do seu locatário do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-482">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="06dac-483">Você não pode testar URLs de CDN diretamente em um navegador da Web, pois deve ter um referenciador proveniente do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="06dac-483">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="06dac-484">No entanto, se você adicionar a URL de ativo da CDN a uma página do SharePoint e, em seguida, abrir a página em um navegador, verá o ativo da CDN renderizado na página.</span><span class="sxs-lookup"><span data-stu-id="06dac-484">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="06dac-485">Para obter mais informações sobre como usar as ferramentas de desenvolvedor no navegador do Microsoft Edge, consulte [ferramentas de desenvolvedor do Microsoft Edge](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span><span class="sxs-lookup"><span data-stu-id="06dac-485">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="06dac-486">Por que os ativos de uma nova origem não estão disponíveis?</span><span class="sxs-lookup"><span data-stu-id="06dac-486">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="06dac-487">Os ativos em novas origens não estarão disponíveis para uso imediatamente, pois levará tempo para o registro se propagar através da CDN e para que os ativos sejam carregados da origem para o armazenamento de CDN.</span><span class="sxs-lookup"><span data-stu-id="06dac-487">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="06dac-488">O tempo necessário para que os ativos estejam disponíveis na CDN depende do número de ativos e dos arquivos.</span><span class="sxs-lookup"><span data-stu-id="06dac-488">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="06dac-489">Minha solução de Web Part do lado do cliente ou do SharePoint Framework não está funcionando</span><span class="sxs-lookup"><span data-stu-id="06dac-489">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="06dac-490">Quando você habilita a CDN do Office 365 para origens públicas, o serviço CDN cria automaticamente essas origens padrão:</span><span class="sxs-lookup"><span data-stu-id="06dac-490">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

- <span data-ttu-id="06dac-491">\*/MASTERPAGE</span><span class="sxs-lookup"><span data-stu-id="06dac-491">\*/MASTERPAGE</span></span>
- <span data-ttu-id="06dac-492">\* BIBLIOTECA/STYLE</span><span class="sxs-lookup"><span data-stu-id="06dac-492">\*/STYLE LIBRARY</span></span>
- <span data-ttu-id="06dac-493">\*/CLIENTSIDEASSETS</span><span class="sxs-lookup"><span data-stu-id="06dac-493">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="06dac-494">Se a origem \*/clientsideassets estiver ausente, as soluções da estrutura do SharePoint falharão, e nenhuma mensagem de aviso ou de erro será gerada.</span><span class="sxs-lookup"><span data-stu-id="06dac-494">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="06dac-495">Essa origem pode estar faltando porque a CDN foi habilitada com o parâmetro _-NoDefaultOrigins_ definido como **$true**ou porque a origem foi excluída manualmente.</span><span class="sxs-lookup"><span data-stu-id="06dac-495">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="06dac-496">Você pode verificar se a origem de \*/CLIENTSIDEASSETS está presente com o seguinte comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="06dac-496">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="06dac-497">Ou você pode verificar com a CLI do Office 365:</span><span class="sxs-lookup"><span data-stu-id="06dac-497">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="06dac-498">Para adicionar a origem no PowerShell:</span><span class="sxs-lookup"><span data-stu-id="06dac-498">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="06dac-499">Para adicionar a origem na CLI do Office 365:</span><span class="sxs-lookup"><span data-stu-id="06dac-499">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="06dac-500">Quais são os módulos do PowerShell e os shells da CLI necessários para trabalhar com a CDN do Office 365?</span><span class="sxs-lookup"><span data-stu-id="06dac-500">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="06dac-501">Você pode optar por trabalhar com a CDN do Office 365 usando o módulo do PowerShell do **Shell de gerenciamento do SharePoint Online** ou a **CLI do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="06dac-501">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

- [<span data-ttu-id="06dac-502">Introdução ao Shell de gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="06dac-502">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [<span data-ttu-id="06dac-503">Instalar a CLI do Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-503">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="06dac-504">Confira também</span><span class="sxs-lookup"><span data-stu-id="06dac-504">See also</span></span>

[<span data-ttu-id="06dac-505">Redes de Distribuição de Conteúdo</span><span class="sxs-lookup"><span data-stu-id="06dac-505">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="06dac-506">Planejamento de rede e ajuste de desempenho para o Office 365</span><span class="sxs-lookup"><span data-stu-id="06dac-506">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

