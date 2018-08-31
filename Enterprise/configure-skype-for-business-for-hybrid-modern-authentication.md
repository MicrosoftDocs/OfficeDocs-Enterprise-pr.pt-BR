---
title: Como configurar o Skype for Business no local para usar a autenticação moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Autenticação moderna, é um método de gerenciamento de identidade que oferece a autorização e autenticação de usuário mais segura, está disponível para Skype para Business server local e Exchange server local, bem como a divisão de domínios Skype para híbridas de negócios.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539487"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="ccfd3-103">Como configurar o Skype for Business no local para usar a autenticação moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="ccfd3-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="ccfd3-104">Autenticação moderna, é um método de gerenciamento de identidade que oferece a autorização e autenticação de usuário mais segura, está disponível para Skype para Business server local e Exchange server local, bem como a divisão de domínios Skype para híbridas de negócios.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="ccfd3-p101">**Importante** Gostaria de saber mais sobre autenticação moderno (MA) e por que você talvez prefira usá-lo em sua empresa ou organização? Verifique se [Este documento](hybrid-modern-auth-overview.md) para obter uma visão geral. Se você precisar saber qual Skype para topologias de negócios são compatíveis com o MA, que está documentado aqui!</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="ccfd3-108">**Antes de começar**, posso chamar:</span><span class="sxs-lookup"><span data-stu-id="ccfd3-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="ccfd3-109">Autenticação moderna \> MA</span><span class="sxs-lookup"><span data-stu-id="ccfd3-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="ccfd3-110">Autenticação de moderno híbrida \> HMA</span><span class="sxs-lookup"><span data-stu-id="ccfd3-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="ccfd3-111">Local do Exchange \> EXCH</span><span class="sxs-lookup"><span data-stu-id="ccfd3-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="ccfd3-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="ccfd3-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="ccfd3-113">Skype para negócios local \> SFB</span><span class="sxs-lookup"><span data-stu-id="ccfd3-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="ccfd3-114">e Skype para negócios Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="ccfd3-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="ccfd3-115">Além disso, \* se um elemento gráfico neste artigo tem um objeto que tenha 'acinzentado' ou 'esmaecida' que significa que o elemento mostrado em cinza **não está** incluído na configuração MA específico.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="ccfd3-116">Leia o resumo</span><span class="sxs-lookup"><span data-stu-id="ccfd3-116">Read the summary</span></span>

<span data-ttu-id="ccfd3-117">Esse resumo concentra-se o processo em etapas que talvez caso contrário, obtenha perdidos durante a execução e é bom para uma lista de verificação geral rastrear onde você está no processo.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="ccfd3-118">Primeiro, verifique se que você atende a todos os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="ccfd3-p102">Desde muitos **pré-requisitos** são comuns para ambos os Skype para Exchange, [consulte o artigo de visão geral para a sua lista de verificação de pré-req](hybrid-modern-auth-overview.md)e de negócios. Fazer esta *antes de* começar qualquer uma das etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="ccfd3-121">Colete as informações de HMA específicos, que você precisará de um arquivo ou o OneNote.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="ccfd3-122">Ativar Diante moderno autenticação para EXO (se ela não ainda esteja ativada).</span><span class="sxs-lookup"><span data-stu-id="ccfd3-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="ccfd3-123">Ativar Diante moderno autenticação para SFBO (se ela não ainda esteja ativada).</span><span class="sxs-lookup"><span data-stu-id="ccfd3-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="ccfd3-124">Ative a autenticação moderno híbrido para Exchange local.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="ccfd3-125">Ative a autenticação moderno híbrido para Skype para negócios local.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="ccfd3-p103">Observe que essas etapas ativem MA para SFB, SFBO, EXCH e EXO – ou seja, todos os produtos que podem participar de uma configuração de HMA do SFB e SFBO (incluindo dependências em EXCH/EXO). Em outras palavras, se os usuários estejam hospedados em / criou caixas de correio em qualquer parte do híbrido (EXO + SFBO, EXO + SFB, EXCH + SFBO, ou EXCH + SFB), seu produto acabado terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Um misto Skype de 6 de topologia do business HMA tem MA em todos os locais de possíveis quatro.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="ccfd3-p104">Como você pode ver, existem quatro diferentes locais para ativar o MA! Para uma melhor experiência do usuário é recomendável que você ativar MA em todos os quatro desses locais. Se você não pode ativar MA todos nesses locais, ajuste as etapas para que você ativar MA apenas nos locais que são necessárias para o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="ccfd3-132">Consulte o [tópico de suporte para Skype for Business com o MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) para topologias com suporte.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="ccfd3-p105">**Importante** Verifique novamente cumprir todos os pré-requisitos antes de começar. Você encontrará essas informações [aqui](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="ccfd3-135">Coletar todas as informações de HMA específicos, que você precisará</span><span class="sxs-lookup"><span data-stu-id="ccfd3-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="ccfd3-p106">Depois que você tiver com verificação dupla que você cumpre os [pré-requisitos](hybrid-modern-auth-overview.md) para usar a autenticação moderno (consulte a observação acima), você deve criar um arquivo para armazenar as informações que você precisará para configurar HMA nas etapas com antecedência. Exemplos usados neste artigo:</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="ccfd3-138">**Domínio SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="ccfd3-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="ccfd3-p107">Contoso.com ex. (é federado com o Office 365)</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="ccfd3-141">**ID do inquilino**</span><span class="sxs-lookup"><span data-stu-id="ccfd3-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="ccfd3-142">O GUID que representa seu locatário do Office 365 (no login do contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="ccfd3-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="ccfd3-143">**SFB 2015 CU5 URLs do Web Service**</span><span class="sxs-lookup"><span data-stu-id="ccfd3-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="ccfd3-p108">Você precisará do URL do serviço de web internos e externos para todos os pools de SfB 2015 implantados. Para obtê-los, execute o seguinte do Skype do Shell de gerenciamento de negócios:</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="ccfd3-146">Get-CsService - WebServer | Select-Object PoolFqdn, InternalFqdn, Fqdnexterno | FL</span><span class="sxs-lookup"><span data-stu-id="ccfd3-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="ccfd3-p109">Interna ex.:https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="ccfd3-p110">External ex.:https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="ccfd3-p111">Se você estiver usando um servidor Standard Edition, a URL interna ficará em branco. Nesse caso, use o fqdn do pool para a URL interna.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="ccfd3-153">Ativar a autenticação moderna para EXO</span><span class="sxs-lookup"><span data-stu-id="ccfd3-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="ccfd3-154">Siga as instruções aqui: [Exchange Online: como habilitar o seu locatário para autenticação moderno.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="ccfd3-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="ccfd3-155">Ativar a autenticação moderna para SFBO</span><span class="sxs-lookup"><span data-stu-id="ccfd3-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="ccfd3-156">Siga as instruções aqui: [Skype para Business Online: habilitar o seu locatário para autenticação moderno](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="ccfd3-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="ccfd3-157">Ativar a autenticação moderno híbrida do Exchange local</span><span class="sxs-lookup"><span data-stu-id="ccfd3-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="ccfd3-158">Siga as instruções aqui: [como configurar o Exchange Server local para usar a autenticação híbrida moderno](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ccfd3-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="ccfd3-159">Ativar a autenticação moderno híbrido para Skype para negócios no local</span><span class="sxs-lookup"><span data-stu-id="ccfd3-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="ccfd3-160">Adicionar local de URLs de serviço web como SPNs no Azure AD</span><span class="sxs-lookup"><span data-stu-id="ccfd3-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="ccfd3-161">Agora, você precisará executar comandos para adicionar as URLs (anteriormente coletados) como entidades de serviço no SFBO.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="ccfd3-p112">**Observação** Nomes de entidade de serviço (SPNs) identificam os serviços da web e associá-los a uma entidade de segurança (por exemplo, um nome de conta ou grupo), para que o serviço possa atuar em nome de um usuário autorizado. Clientes de autenticação a um servidor verifique o uso das informações que SPNs contidas em.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="ccfd3-164">Primeiro, se conecte ao AAD com [estas instruções](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="ccfd3-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="ccfd3-165">Execute este comando no local, para obter uma lista das URLs do web service SFB.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="ccfd3-166">Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Selecione ServicePrincipalNames - ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="ccfd3-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="ccfd3-p113">Observe que o AppPrincipalId começa com '00000004'. Isso corresponde ao Skype para negócios Online.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="ccfd3-169">Tomar nota das (e captura de tela para comparação posterior) a saída deste comando, que incluem um SE e a URL do WS, mas consistem principalmente SPNs que começam com 00000004-0000-0ff1-ce00-000000000000 /.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="ccfd3-170">Se os internos **ou** externos SFB URLs no local estão ausentes (por exemplo, https://lyncwebint01.contoso.com e https://lyncwebext01.contoso.com) precisamos adicionar esses registros específicos a essa lista.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="ccfd3-171">Certifique-se de substituir *as URLs de exemplo* , abaixo, aos URLs reais nos comandos Add!</span><span class="sxs-lookup"><span data-stu-id="ccfd3-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="ccfd3-172">$x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="ccfd3-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="ccfd3-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="ccfd3-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="ccfd3-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="ccfd3-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="ccfd3-175">Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="ccfd3-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="ccfd3-p114">Verifique se que seus novos registros foram adicionados executando o comando Get-MsolServicePrincipal da etapa 2 novamente e, em seguida, procurando por meio de saída. Compare a lista / captura de tela de antes da nova lista de SPNs (você pode também a nova lista de captura de tela para seus registros). Se você tiver sido bem-sucedida, você verá duas novas URLs na lista. Vai pelo nosso exemplo, a lista de SPNs agora inclui as URLs específicas https://lyncweb01.contoso.com e https://autodiscover.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="ccfd3-180">Criar o objeto de servidor de autenticação EvoSTS</span><span class="sxs-lookup"><span data-stu-id="ccfd3-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="ccfd3-181">Execute o seguinte comando no Skype do Shell de gerenciamento de negócios.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="ccfd3-182">New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-AzureAD de tipo</span><span class="sxs-lookup"><span data-stu-id="ccfd3-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="ccfd3-183">Habilitar a autenticação híbrida moderno</span><span class="sxs-lookup"><span data-stu-id="ccfd3-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="ccfd3-p115">Esta é a etapa que realmente ativa MA. Todas as etapas anteriores podem ser executadas antes do tempo, sem alterar o fluxo de autenticação de cliente. Quando você estiver pronto para alterar o fluxo de autenticação, execute este comando no Skype do Shell de gerenciamento de negócios.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="ccfd3-187">Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="ccfd3-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="ccfd3-188">Verificar</span><span class="sxs-lookup"><span data-stu-id="ccfd3-188">Verify</span></span>

<span data-ttu-id="ccfd3-p116">Depois que você ativar HMA, próximo de login do cliente usarão o novo fluxo de autenticação. Observe que apenas ativem HMA não aciona um re-autenticação para qualquer cliente. O clientes sua reconexão com base no tempo de vida de e/ou os tokens de autenticação têm os certificados.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="ccfd3-p117">Para testar se HMA está funcionando depois que tiver habilitado, saia de um cliente Windows SFB de teste e não se esqueça de clicar em 'Excluir minhas credenciais'. Entre novamente. O cliente agora deve usar o fluxo de autenticação moderno e seu login agora incluirá um prompt do **Office 365** para um 'trabalho ou escola' conta, Vista direita antes que o cliente contata o servidor e registra você.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="ccfd3-p118">Você deve também verificar as informações de configuração' ' Skype para clientes corporativos para uma autoridade de OAuth' '. Para fazer isso no computador cliente, mantenha pressionada a tecla CTRL ao mesmo tempo em que você clique com botão direito do Skype para o ícone de negócios na bandeja de notificação do Windows. No menu exibido, clique em informações de configuração. Na janela 'Skype para obter informações de configuração de negócios' que aparecerá na área de trabalho, procure o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![As informações de configuração de um Skype Business Client usando a autenticação moderno mostram uma Lync e a URL de autoridade do EWS OAUTH do https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="ccfd3-p119">Você também deve mantenha pressionada a tecla CTRL ao mesmo tempo que Right clicar no ícone para o cliente do Outlook (também na bandeja do Windows notificações) e clique em Status do Conexão. Procure o endereço de SMTP do cliente em relação a um tipo de Authn de ' portador\*', que representa o token do transportador usado em OAuth.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="ccfd3-202">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="ccfd3-202">Related articles</span></span>

<span data-ttu-id="ccfd3-203">[Vínculo inverso para a visão geral de autenticação moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="ccfd3-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="ccfd3-p120">É preciso saber como usar a autenticação moderno (ADAL) para sua Skype para clientes de negócios? Temos etapas [aqui](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="ccfd3-p121">Deseja para ler estas etapas que eles aparecem para o Exchange Server, local, executando sem SFB? Essas etapas estão disponíveis aqui.</span><span class="sxs-lookup"><span data-stu-id="ccfd3-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

