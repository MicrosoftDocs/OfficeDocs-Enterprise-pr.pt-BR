---
title: Usar a rede de fornecimento de conteúdo do Office 365 com o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Descreve como usar a rede de entrega de conteúdo (CDN) interno do Office 365 para acelerar a entrega dos ativos do SharePoint Online para todos os usuários, não importa onde eles estão localizados ou como eles acessam o seu conteúdo.
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539168"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a><span data-ttu-id="02d01-103">Usar a rede de fornecimento de conteúdo do Office 365 com o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="02d01-103">Use the Office 365 content delivery network with SharePoint Online</span></span>

<span data-ttu-id="02d01-p101">Você pode hospedar estáticos ativos na rede de fornecimento de conteúdo de Office 365 (CDN) para oferecer melhor desempenho para as páginas do SharePoint Online. Estáticos ativos são arquivos que não são alterados com frequência, como imagens, vídeo e áudio, folhas de estilo, fontes e arquivos JavaScript. A CDN funciona como um proxy de cache distribuído geograficamente, obtendo quase ativos estáticos para os navegadores pedi-las.</span><span class="sxs-lookup"><span data-stu-id="02d01-p101">You can host static assets in the Office 365 content delivery network (CDN) to provide better performance for your SharePoint Online pages. Static assets are files that don't change very often, like images, video and audio, style sheets, fonts, and JavaScript files. The CDN works as a geographically distributed caching proxy, by caching static assets closer to the browsers requesting them.</span></span> 
  
<span data-ttu-id="02d01-p102">Se você já estiver familiarizado com o modo como as CDNs funcionem, você precisará concluir algumas etapas para configurá-lo. Este tópico descreve como. Leia informações sobre o Office 365 CDN e como começar a hospedagem seus ativos estáticos.</span><span class="sxs-lookup"><span data-stu-id="02d01-p102">If you are already familiar with the way that CDNs work, you only need to complete a few steps to set it up. This topic describes how. Read on for information about the Office 365 CDN and how to get started hosting your static assets.</span></span>
  
 <span data-ttu-id="02d01-110">**Cabeça de volta para o [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="02d01-110">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>
  
## <a name="office-365-cdn-basics"></a><span data-ttu-id="02d01-111">Noções básicas CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-111">Office 365 CDN basics</span></span>

<span data-ttu-id="02d01-p103">O Office 365 CDN é incluído como parte da sua assinatura do SharePoint Online. Você não precisa pagar extra para ele. O Office 365 fornece suporte para ambas privadas e acesso público e permite aos ativos estática em vários locais ou origens de host. O Office 365 CDN não é igual a CDN do Windows Azure. Se precisar de mais informações sobre por que usar uma CDN ou sobre conceitos gerais de CDN, consulte [redes de fornecimento de conteúdo](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="02d01-p103">The Office 365 CDN is included as part of your SharePoint Online subscription. You don't have to pay extra for it. Office 365 provides support for both private and public access and allows you to host static assets in multiple locations, or origins. The Office 365 CDN is not the same as the Azure CDN. If you need more information about why to use a CDN or about general CDN concepts, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="how-the-cdn-grants-access-to-end-users"></a><span data-ttu-id="02d01-117">Como a CDN concede acesso aos usuários finais</span><span class="sxs-lookup"><span data-stu-id="02d01-117">How the CDN grants access to end users</span></span>

<span data-ttu-id="02d01-p104">Privada acessem estáticos ativos do Office 365 CDN recebe por tokens gerados pelo SharePoint Online. Usuários que já têm permissão para acessar até a pasta ou biblioteca designados por origem serão concedidos automaticamente tokens. SharePoint Online não suporta as permissões de nível de item para a CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-p104">Private access to static assets in the Office 365 CDN is granted by tokens generated by SharePoint Online. Users who already have permission to access to the folder or library designated by the origin will automatically be granted tokens. SharePoint Online does not support item-level permissions for the CDN.</span></span>
  
<span data-ttu-id="02d01-121">Por exemplo, para um arquivo localizado em `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, dado o seguinte:</span><span class="sxs-lookup"><span data-stu-id="02d01-121">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, given the following:</span></span>
  
- <span data-ttu-id="02d01-122">O usuário 1 tem acesso para folder1 e image1.jpg</span><span class="sxs-lookup"><span data-stu-id="02d01-122">User 1 has access to folder1 and to image1.jpg</span></span>
    
- <span data-ttu-id="02d01-123">O usuário 2 não tem acesso para folder1</span><span class="sxs-lookup"><span data-stu-id="02d01-123">User 2 does not have access to folder1</span></span>
    
- <span data-ttu-id="02d01-124">3 de usuário não tem acesso para folder1, mas é concedida permissão explícita para acessar image1.jpg através do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="02d01-124">User 3 does not have access to folder1 but is granted explicit permission to access image1.jpg through SharePoint Online</span></span>
    
- <span data-ttu-id="02d01-125">4 de usuário tem acesso ao folder1, mas foi negado explicitamente acesso ao image1.jpg</span><span class="sxs-lookup"><span data-stu-id="02d01-125">User 4 has access to folder1 but has been explicitly denied access to image1.jpg</span></span>
    
<span data-ttu-id="02d01-126">Em seguida, as seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="02d01-126">Then the following are true:</span></span>
  
- <span data-ttu-id="02d01-127">O usuário 1 e 4 de usuário poderão acessar image1.jpg através do CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-127">User 1 and User 4 will be able to access image1.jpg through the CDN.</span></span>
    
- <span data-ttu-id="02d01-128">O usuário 2 e 3 do usuário não será capaz de acessar image1.jpg através do CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-128">User 2 and User 3 will not be able to access image1.jpg through the CDN.</span></span>
    
    <span data-ttu-id="02d01-129">No entanto, User 3 ainda pode acessar o image1.jpg ativos diretamente através do SharePoint Online enquanto o usuário 4 não pode acessar o ativo através do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="02d01-129">However, User 3 can still access the asset image1.jpg directly through SharePoint Online while User 4 cannot access the asset through SharePoint Online.</span></span>
    
## <a name="overview-of-working-with-the-office-365-cdn"></a><span data-ttu-id="02d01-130">Visão geral de como trabalhar com o Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="02d01-130">Overview of working with the Office 365 CDN</span></span>

<span data-ttu-id="02d01-131">Para configurar o Office 365 CDN, você deve seguir estas etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="02d01-131">To set up the Office 365 CDN, you follow these basic steps:</span></span>
  
- <span data-ttu-id="02d01-132">Planejar a implantação de CDN:</span><span class="sxs-lookup"><span data-stu-id="02d01-132">Plan for CDN deployment:</span></span>
    
  - <span data-ttu-id="02d01-p105">Determine quais ativos estáticos que você deseja hospedar na CDN do Office 365. Para obter informações detalhadas sobre como fazer essas opções, consulte [redes de fornecimento de conteúdo](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="02d01-p105">Determine which static assets you want to host on the Office 365 CDN. For detailed information about how to make these choices, refer to [Content delivery networks](content-delivery-networks.md).</span></span>
    
  - <span data-ttu-id="02d01-p106">[Determine onde deseja armazenar os ativos](use-office-365-cdn-with-spo.md#CDNStoreAssets). Este local é uma pasta ou uma biblioteca do SharePoint e é chamado de uma origem.</span><span class="sxs-lookup"><span data-stu-id="02d01-p106">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets). This location is a folder or SharePoint library and is called an origin.</span></span>
    
  - <span data-ttu-id="02d01-p107">Determine se os ativos devem ser feitos públicos ou mantidos privados. Você fazer isso quando você [escolher se cada origem deve ser pública ou privada](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Se desejar, você pode ter várias origens nas quais alguns são públicos e alguns estão privadas.</span><span class="sxs-lookup"><span data-stu-id="02d01-p107">Determine whether the assets should be made public or kept private. You do this when you [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). If you want, you can have multiple origins in which some are public, and some are private.</span></span>
    
- <span data-ttu-id="02d01-p108">[Definido para cima e para configurar o Office 365 CDN usando o Shell de gerenciamento do SharePoint Online](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Quando você concluir esta etapa, você terá:</span><span class="sxs-lookup"><span data-stu-id="02d01-p108">[Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). When you complete this step, you will have:</span></span>
    
  - <span data-ttu-id="02d01-142">Habilitado a CDN para sua organização.</span><span class="sxs-lookup"><span data-stu-id="02d01-142">Enabled the CDN for your organization.</span></span>
    
  - <span data-ttu-id="02d01-p109">Adicionado o seus origens. Você identificar cada origem como pública ou privada.</span><span class="sxs-lookup"><span data-stu-id="02d01-p109">Added your origins. You identify each origin as public or private.</span></span>
    
<span data-ttu-id="02d01-145">Uma vez terminar com a instalação, [Gerenciar o Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) ao longo do tempo por:</span><span class="sxs-lookup"><span data-stu-id="02d01-145">Once you're done with setup, [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span> 
  
- <span data-ttu-id="02d01-146">Adicionar, atualizar e remover ativos</span><span class="sxs-lookup"><span data-stu-id="02d01-146">Adding, updating, and removing assets</span></span>
    
- <span data-ttu-id="02d01-147">Adicionando e removendo origens</span><span class="sxs-lookup"><span data-stu-id="02d01-147">Adding and removing origins</span></span>
    
- <span data-ttu-id="02d01-148">Configurando políticas CDN</span><span class="sxs-lookup"><span data-stu-id="02d01-148">Configuring CDN policies</span></span>
    
- <span data-ttu-id="02d01-149">Se necessário, desabilitando a CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-149">If necessary, disabling the Office 365 CDN</span></span>
    
## <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="02d01-150">Determinar onde deseja armazenar os ativos</span><span class="sxs-lookup"><span data-stu-id="02d01-150">Determine where you want to store your assets</span></span>

<span data-ttu-id="02d01-p110">A CDN busca seus ativos de um local chamado uma origem. Para o Office 365, uma origem é uma biblioteca do SharePoint ou a pasta que seja acessível por uma URL. Você tem grande flexibilidade quando você especificar origens para sua organização. Por exemplo, você pode especificar várias origens ou, uma única origem onde você deseja colocar todos os seus ativos CDN. Você pode optar por ter origens públicas ou privadas para a sua organização. A maioria das organizações optará por implementar uma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="02d01-p110">The CDN fetches your assets from a location called an origin. For Office 365, an origin is a SharePoint library or folder that is accessible by a URL. You have great flexibility when you specify origins for your organization. For example, you can specify multiple origins, or, a single origin where you want to put all your CDN assets. You can choose to have both public or private origins for your organization. Most organizations will choose to implement a combination of the two.</span></span>
  
<span data-ttu-id="02d01-p111">Se você definir centenas de origens, ele provavelmente terá um impacto negativo sobre o tempo que leva para processar solicitações. É recomendável que se você tiver mais de cerca de 100 origens você talvez queira pensar novamente sua arquitetura.</span><span class="sxs-lookup"><span data-stu-id="02d01-p111">If you define hundreds of origins, it will likely have a negative impact on the time it takes to process requests. We recommend that if you have more than about 100 origins you might want to rethink your architecture.</span></span>
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="02d01-159">Escolha se cada origem deve ser pública ou privada</span><span class="sxs-lookup"><span data-stu-id="02d01-159">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="02d01-p112">Quando você identifica uma origem, especifique se ela deve ser feita pública ou privada. Independentemente de qual opção escolher, Microsoft faz todo o trabalho pesado para você quando se trata de administração da CDN em si. Além disso, você pode alterar mente mais tarde, depois de configurar o CDN e identificado suas origens.</span><span class="sxs-lookup"><span data-stu-id="02d01-p112">When you identify an origin, you specify whether it should be made public or private. Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself. Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>
  
<span data-ttu-id="02d01-163">Opções de públicas e particulares fornecem melhorias de desempenho, mas cada uma tem vantagens e atributos exclusivos.</span><span class="sxs-lookup"><span data-stu-id="02d01-163">Both public and private options provide performance improvements, but each has unique attributes and advantages.</span></span>
  
 <span data-ttu-id="02d01-164">**Atributos e as vantagens de hospedagem ativos em uma origem de público**</span><span class="sxs-lookup"><span data-stu-id="02d01-164">**Attributes and advantages of hosting assets in a public origin**</span></span>
  
- <span data-ttu-id="02d01-165">Ativos expostos em uma origem pública anonimamente são acessíveis por todos.</span><span class="sxs-lookup"><span data-stu-id="02d01-165">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="02d01-166">Se você identificar uma origem pública na sua CDN, você nunca deve colocar os recursos que são considerados confidenciais à sua organização em uma origem pública ou a biblioteca do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="02d01-166">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in a public origin or SharePoint Online library.</span></span> 
  
- <span data-ttu-id="02d01-167">Se você remover um ativo de uma origem de pública, o ativo pode continuar a estejam disponíveis por até 30 dias a partir do cache; No entanto, podemos invalidará links para os ativos na CDN dentro de 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="02d01-167">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="02d01-p113">Quando você hospeda folhas de estilo (arquivos CSS) em uma origem de pública, você pode usar caminhos relativos e URIs dentro do código. Isso significa que é possível fazer referência a localização das imagens de plano de fundo e outros objetos em relação a localização do ativo que está chamando-lo.</span><span class="sxs-lookup"><span data-stu-id="02d01-p113">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code. This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
    
- <span data-ttu-id="02d01-p114">Enquanto você pode codificar o URL de uma origem público, fazer isso não é recomendado. O motivo para isso é que, se acessem a CDN ficar indisponível, a URL não resolverá automaticamente à sua organização no SharePoint Online e pode resultar em links desfeitos e outros erros.</span><span class="sxs-lookup"><span data-stu-id="02d01-p114">While you can hard code a public origin's URL, doing so is not recommended. The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
    
- <span data-ttu-id="02d01-p115">Os tipos de arquivo padrão que estão incluídos para origens públicas são. CSS, .eot,. gif,. ico,. JPEG,. jpg,. js,. map,. png,. SVG,. ttf e .woff. Você pode especificar os tipos de arquivo adicional.</span><span class="sxs-lookup"><span data-stu-id="02d01-p115">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff. You can specify additional file types.</span></span>
    
- <span data-ttu-id="02d01-p116">Se desejar, você pode configurar uma política para excluir os ativos que foram identificados por classificações de site que você especificar. Por exemplo, você pode optar por excluir todos os ativos que são marcados como "confidencial" ou "restritas", mesmo que elas são um tipo de arquivo permitidos e estão localizadas em uma origem de pública.</span><span class="sxs-lookup"><span data-stu-id="02d01-p116">If you want, you can configure a policy to exclude assets that have been identified by site classifications that you specify. For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>
    
 <span data-ttu-id="02d01-176">**Atributos e as vantagens de hospedagem ativos em uma origem privada**</span><span class="sxs-lookup"><span data-stu-id="02d01-176">**Attributes and advantages of hosting assets in a private origin**</span></span>
  
- <span data-ttu-id="02d01-p117">Os usuários podem acessar apenas os ativos de uma origem privada se eles estão autorizados a fazê-lo. Acesso anônimo para esses ativos é impedido.</span><span class="sxs-lookup"><span data-stu-id="02d01-p117">Users can only access the assets from a private origin if they are authorized to do so. Anonymous access to these assets is prevented.</span></span>
    
- <span data-ttu-id="02d01-179">Se você remover um ativo em relação à origem particular, o ativo pode continuar esteja disponível para até uma hora do cache; No entanto, podemos invalidará links para os ativos na CDN dentro de 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="02d01-179">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="02d01-p118">Os tipos de arquivo padrão que estão incluídos para origens privadas são. ico,. gif,. jpg,. JPEG,. js e. PNG. Você pode especificar os tipos de arquivo adicional.</span><span class="sxs-lookup"><span data-stu-id="02d01-p118">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png. You can specify additional file types.</span></span>
    
- <span data-ttu-id="02d01-182">Assim como as origens de públicas, você pode configurar uma política para excluir os ativos que foram identificados por classificações de site que você especificar, mesmo se você usar caracteres curinga para incluir todos os ativos dentro de uma pasta ou biblioteca do Site.</span><span class="sxs-lookup"><span data-stu-id="02d01-182">Just like public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or Site Library.</span></span>
    
## <a name="default-office-365-cdn-origins"></a><span data-ttu-id="02d01-183">Origens de Office 365 CDN padrão</span><span class="sxs-lookup"><span data-stu-id="02d01-183">Default Office 365 CDN origins</span></span>

<span data-ttu-id="02d01-p119">A menos que você especifique o contrário, Office 365 configura algumas origens de padrão para você quando você habilita a CDN do Office 365. Se você inicialmente excluí-los, você pode adicionar esses origens após concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="02d01-p119">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN. If you initially exclude them, you can add these origins after you complete setup.</span></span>
  
<span data-ttu-id="02d01-186">Origens de privada padrão:</span><span class="sxs-lookup"><span data-stu-id="02d01-186">Default private origins:</span></span>
  
- <span data-ttu-id="02d01-187">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="02d01-187">\*/userphoto.aspx</span></span>
    
- <span data-ttu-id="02d01-188">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="02d01-188">\*/siteassets</span></span>
    
<span data-ttu-id="02d01-189">Origens de pública padrão:</span><span class="sxs-lookup"><span data-stu-id="02d01-189">Default public origins:</span></span>
  
- <span data-ttu-id="02d01-190">\*/MasterPage</span><span class="sxs-lookup"><span data-stu-id="02d01-190">\*/masterpage</span></span>
    
- <span data-ttu-id="02d01-191">\*/biblioteca</span><span class="sxs-lookup"><span data-stu-id="02d01-191">\*/style library</span></span>
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="02d01-192">Instalar e configurar o Office 365 CDN usando o Shell de gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="02d01-192">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="02d01-p120">Os procedimentos neste tópico exigem que você pode usar o Shell de gerenciamento do SharePoint Online para se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="02d01-p120">The procedures in this topic require you to use the SharePoint Online Management Shell to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="02d01-195">Conclua estas etapas para instalar e configurar o CDN do Office 365 para hospedar seus estáticos ativos no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="02d01-195">Complete these steps to set up and configure the Office 365 CDN to host your static assets in SharePoint Online.</span></span>
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="02d01-196">Para habilitar a sua organização para usar o Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="02d01-196">To enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="02d01-p121">Use o cmdlet **Set-SPOTenantCdnEnabled** para habilitar a sua organização para usar o Office 365 CDN. Você pode habilitar a sua organização usar origens públicas, origens privadas ou ambos com a CDN. Você também pode configurar o CDN do Office 365 para ignorar a configuração de origens padrão quando você ativá-la. Você sempre pode adicionar esses origens posteriormente, conforme descrito neste tópico.</span><span class="sxs-lookup"><span data-stu-id="02d01-p121">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN. You can enable your organization to use either public origins, private origins, or both with the CDN. You can also configure the Office 365 CDN to skip the setup of default origins when you enable it. You can always add these origins later as described in this topic.</span></span> 
  
<span data-ttu-id="02d01-201">No Windows Powershell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="02d01-201">In Windows Powershell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="02d01-202">Por exemplo, para permitir que sua organização use origens de públicas e particulares com a CDN, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02d01-202">For example, to enable your organization to use both public and private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="02d01-203">Para permitir que sua organização use origens de públicas e particulares com a CDN mas ignorar a configuração as origens padrão, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02d01-203">To enable your organization to use both public and private origins with the CDN but skip setting up the default origins, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="02d01-204">Para permitir que sua organização use origens públicas com a CDN, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02d01-204">To enable your organization to use public origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="02d01-205">Para permitir que sua organização use origens privadas com a CDN, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02d01-205">To enable your organization to use private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="02d01-206">Para obter mais informações sobre esse cmdlet, consulte [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-206">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a><span data-ttu-id="02d01-207">(Opcional) Para alterar a lista de tipos de arquivo para incluir na CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-207">(Optional) To change the list of file types to include in the Office 365 CDN</span></span>
<span data-ttu-id="02d01-208"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-208"></span></span>

> [!TIP]
> <span data-ttu-id="02d01-p122">Quando você definir tipos de arquivo usando o cmdlet **Set-SPOTenantCdnPolicy** , substituirá a lista definida no momento. Se você deseja adicionar tipos de arquivo à lista, use o cmdlet primeiro para descobrir quais tipos de arquivo que já têm permissão e incluem-los na lista, juntamente com as novas.</span><span class="sxs-lookup"><span data-stu-id="02d01-p122">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span> 
  
<span data-ttu-id="02d01-p123">Use o cmdlet **Set-SPOTenantCdnPolicy** para definir tipos de arquivos estáticos que podem ser hospedados por origens de públicas e particulares na CDN. Por padrão, os tipos de ativos comuns são permitidos para. js,. gif,. jpg e. CSS de exemplo.</span><span class="sxs-lookup"><span data-stu-id="02d01-p123">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN. By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span> 
  
<span data-ttu-id="02d01-213">No Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="02d01-213">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="02d01-214">Para ver quais tipos de arquivo são permitidos atualmente pela CDN, use o cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="02d01-214">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="02d01-215">Para obter mais informações sobre esses cmdlets, consulte [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-215">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="02d01-216">(Opcional) Para alterar a lista de classificações de site que você deseja excluir da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-216">(Optional) To change the list of site classifications you want to exclude from the Office 365 CDN</span></span>
<span data-ttu-id="02d01-217"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-217"></span></span>

> [!TIP]
> <span data-ttu-id="02d01-p124">Quando você excluir classificações de sites usando o cmdlet **Set-SPOTenantCdnPolicy** , substituirá a lista definida no momento. Se você deseja excluir classificações de sites adicionais, use o cmdlet primeiro para saber quais classificações já são excluídas e adicioná-lo, juntamente com as novas.</span><span class="sxs-lookup"><span data-stu-id="02d01-p124">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span> 
  
<span data-ttu-id="02d01-p125">Use o cmdlet **Set-SPOTenantCdnPolicy** para excluir as classificações de site que você não deseja disponibilizar sobre a CDN. Por padrão, nenhuma classificações de site são excluídas.</span><span class="sxs-lookup"><span data-stu-id="02d01-p125">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN. By default, no site classifications are excluded.</span></span> 
  
<span data-ttu-id="02d01-222">No Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="02d01-222">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="02d01-223">Para ver quais classificações de site são restritas atualmente, use o cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="02d01-223">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="02d01-224">Para obter mais informações sobre esses cmdlets, consulte [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-224">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="to-add-an-origin-for-your-assets"></a><span data-ttu-id="02d01-225">Para adicionar uma origem para os ativos</span><span class="sxs-lookup"><span data-stu-id="02d01-225">To add an origin for your assets</span></span>
<span data-ttu-id="02d01-226"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-226"></span></span>

<span data-ttu-id="02d01-p126">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir uma origem. Você pode definir várias origens. A origem é uma URL que aponta para uma biblioteca do SharePoint ou a pasta que contém os ativos que você deseja ser hospedada pela CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-p126">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin. You can define multiple origins. The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="02d01-230">Se você identificar uma origem pública na sua CDN, você nunca deve colocar os recursos que são considerados confidenciais à sua organização na origem pública ou biblioteca do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="02d01-230">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in the public origin or SharePoint Online library.</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

<span data-ttu-id="02d01-p127">Onde caminho é o caminho para a pasta que contém os ativos. Você pode usar caracteres curinga, além dos caminhos relativos. Por exemplo, para incluir todos os ativos na pasta masterpages para todos os sites como uma origem pública dentro a CDN, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02d01-p127">Where path is the path to the folder that contains the assets. You can use wildcards in addition to relative paths. For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

<span data-ttu-id="02d01-234">Para obter mais informações sobre esse comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-234">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="02d01-p128">Após executar o comando, o sistema sincroniza todas a configuração no datacenter. Isso leva a 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="02d01-p128">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="02d01-237">Exemplo: Configurar uma origem pública para suas páginas mestras e para sua biblioteca de estilos para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="02d01-237">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="02d01-238"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-238"></span></span>

<span data-ttu-id="02d01-p129">Normalmente, essas origens estiver configuradas para você por padrão quando você habilita origens públicas para o Office 365 CDN. No entanto, se você quiser habilitá-los manualmente, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="02d01-p129">Normally, these origins are set up for you by default when you enable public origins for the Office 365 CDN. However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="02d01-241">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a biblioteca de estilos como uma origem pública dentro do Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-241">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="02d01-242">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir as páginas mestras como uma origem pública dentro do Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-242">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- <span data-ttu-id="02d01-243">Para obter mais informações sobre esse comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-243">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="02d01-p130">Após executar o comando, o sistema sincroniza todas a configuração no datacenter. Isso leva a 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="02d01-p130">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="02d01-246">Exemplo: Configurar uma origem privada para seus ativos do site, páginas do site e publicação de imagens para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="02d01-246">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="02d01-247"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-247"></span></span>

- <span data-ttu-id="02d01-248">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de ativos do site como uma origem privada dentro do Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-248">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="02d01-249">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de páginas do site como uma origem privada dentro do Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-249">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="02d01-250">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de imagens de publicação como uma origem privada dentro do Office 365 CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-250">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    <span data-ttu-id="02d01-251">Para obter mais informações sobre esse comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-251">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="02d01-p131">Após executar o comando, o sistema sincroniza todas a configuração no datacenter. Isso leva a 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="02d01-p131">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="02d01-254">Exemplo: Configurar uma origem privada para um conjunto de sites para o SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="02d01-254">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="02d01-255"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-255"></span></span>

<span data-ttu-id="02d01-p132">Use o cmdlet **Add-SPOTenantCdnOrigin** para definir um conjunto de sites como uma origem privada dentro do Office 365 CDN. Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="02d01-p132">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin within the Office 365 CDN. For example,</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="02d01-258">Para obter mais informações sobre esse comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-258">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="02d01-p133">Após executar o comando, o sistema sincroniza todas a configuração no datacenter. Isso leva a 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="02d01-p133">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
## <a name="manage-the-office-365-cdn"></a><span data-ttu-id="02d01-261">Gerenciar o Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="02d01-261">Manage the Office 365 CDN</span></span>
<span data-ttu-id="02d01-262"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-262"></span></span>

<span data-ttu-id="02d01-263">Depois que você tiver configurado a CDN, você pode fazer alterações à sua configuração como atualizar o conteúdo ou conforme suas necessidades mudam, conforme descrito nesta seção.</span><span class="sxs-lookup"><span data-stu-id="02d01-263">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="02d01-264">Para adicionar, atualizar, ou remova ativos a CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-264">To add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="02d01-265"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-265"></span></span>

<span data-ttu-id="02d01-p134">Depois de ter concluído as etapas de instalação, você pode adicionar novos ativos e atualizar ou remover ativos existentes, sempre que desejar. Apenas faça as alterações dos ativos na pasta ou biblioteca do SharePoint que você identificou como uma origem. Se você adicionar um novo ativo, ele está disponível por meio do CDN imediatamente. No entanto, se você atualizar o ativo, levará até 15 minutos para a nova cópia propagar e se tornam disponíveis na CDN.</span><span class="sxs-lookup"><span data-stu-id="02d01-p134">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want. Just make your changes to the assets in the folder or SharePoint library that you identified as an origin. If you add a new asset, it is available through the CDN immediately. However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="02d01-p135">Se você precisar recuperar o local da origem, você pode usar o cmdlet **Get-SPOTenantCdnOrigins** . Para obter informações sobre como usar esse cmdlet, consulte [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-p135">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet. For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="02d01-272">Para remover uma origem da CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-272">To remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="02d01-273"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-273"></span></span>

<span data-ttu-id="02d01-p136">Se for necessário, você pode remover o acesso a uma pasta ou uma biblioteca do SharePoint que você identificou como uma origem. Para fazer isso, use o cmdlet **Remove-SPOTenantCdnOrigin** . Para obter informações sobre como usar esse cmdlet, consulte [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-p136">If you need to, you can remove access to a folder or SharePoint library that you identified as an origin. To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet. For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="02d01-277">Para modificar uma origem na CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-277">To modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="02d01-278"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-278"></span></span>

<span data-ttu-id="02d01-p137">Você não pode modificar uma origem que você criou. Em vez disso, remova a origem e, em seguida, adicionar um novo. Para obter mais informações, consulte [para remover uma origem a partir do Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) e [Adicionar uma origem para os ativos](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="02d01-p137">You can't modify an origin you've created. Instead, remove the origin and then add a new one. For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
### <a name="to-disable-the-office-365-cdn"></a><span data-ttu-id="02d01-282">Para desabilitar a CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-282">To disable the Office 365 CDN</span></span>
<span data-ttu-id="02d01-283"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-283"></span></span>

<span data-ttu-id="02d01-p138">Use o cmdlet **Set-SPOTenantCdnEnabled** para desabilitar a CDN para sua organização. Se você tiver ambas as públicas e particulares origens habilitadas para a CDN, você precisará executar o cmdlet duas vezes conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="02d01-p138">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization. If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span> 
  
<span data-ttu-id="02d01-286">Para desabilitar o uso de origens públicos no CDN, no Windows Powershell para SharePoint Online, insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02d01-286">To disable use of public origins in the CDN, in Windows Powershell for SharePoint Online, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="02d01-287">Para desabilitar o uso das origens privadas na CDN, insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02d01-287">To disable use of the private origins in the CDN, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="02d01-288">Para obter mais informações sobre esse cmdlet, consulte [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="02d01-288">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a><span data-ttu-id="02d01-289">Solucionando problemas de configuração CDN do Office 365</span><span class="sxs-lookup"><span data-stu-id="02d01-289">Troubleshooting your Office 365 CDN configuration</span></span>
<span data-ttu-id="02d01-290"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="02d01-290"></span></span>

<span data-ttu-id="02d01-p139">O ponto de extremidade não imediatamente estará disponível para uso, como leva tempo para que o registro para se propagar a CDN. Configuração leva 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="02d01-p139">The endpoint will not immediately be available for use, as it takes time for the registration to propagate through the CDN. Configuration takes 15 minutes.</span></span>
  

