---
title: Como configurar o Skype for Business no local para usar a autenticação moderna híbrida
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: A autenticação moderna é um método de gerenciamento de identidades que oferece autenticação e autorização de usuário mais seguras, está disponível para o Skype for Business Server local e o Exchange Server local, bem como para o Split-Domain híbridas do Skype for Business.
ms.openlocfilehash: 4a49885fc6276f180872facb777bfe5a5adb61ee
ms.sourcegitcommit: f9b5e029ed427b7c15cbfb6231a9259b34c9436f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "36759679"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="36e81-103">Como configurar o Skype for Business no local para usar a autenticação moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="36e81-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="36e81-104">A autenticação moderna é um método de gerenciamento de identidades que oferece autenticação e autorização de usuário mais seguras, está disponível para o Skype for Business Server local e o Exchange Server local, bem como para o Split-Domain híbridas do Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="36e81-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="36e81-105">**Importante** Gostaria de saber mais sobre a autenticação moderna (MA) e por que você pode preferir usá-la em sua empresa ou organização?</span><span class="sxs-lookup"><span data-stu-id="36e81-105">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="36e81-106">Consulte [este documento](hybrid-modern-auth-overview.md) para obter uma visão geral.</span><span class="sxs-lookup"><span data-stu-id="36e81-106">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="36e81-107">Se você precisa saber quais topologias do Skype for Business são compatíveis com o MA, está documentado aqui!</span><span class="sxs-lookup"><span data-stu-id="36e81-107">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="36e81-108">**Antes de começar**, chamo:</span><span class="sxs-lookup"><span data-stu-id="36e81-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="36e81-109">MA de \> autenticação moderna</span><span class="sxs-lookup"><span data-stu-id="36e81-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="36e81-110">HMA de autenticação \> moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="36e81-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="36e81-111">Exchange local \></span><span class="sxs-lookup"><span data-stu-id="36e81-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="36e81-112">EXO do \> Exchange Online</span><span class="sxs-lookup"><span data-stu-id="36e81-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="36e81-113">SFB local \> do Skype for Business</span><span class="sxs-lookup"><span data-stu-id="36e81-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="36e81-114">e Skype for Business Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="36e81-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="36e81-115">Além disso, \* se um gráfico neste artigo tiver um objeto que é ' esmaecido ' ou ' esmaecido ', isso significa que o elemento mostrado em cinza **não está** incluído na configuração específica de ma.</span><span class="sxs-lookup"><span data-stu-id="36e81-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="36e81-116">Leia o resumo</span><span class="sxs-lookup"><span data-stu-id="36e81-116">Read the summary</span></span>

<span data-ttu-id="36e81-117">Este resumo resume o processo em etapas que podem ser perdidas durante a execução e é bom para uma lista de verificação geral para acompanhar onde você está no processo.</span><span class="sxs-lookup"><span data-stu-id="36e81-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="36e81-118">Primeiro, verifique se você atende a todos os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="36e81-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="36e81-119">Como muitos **pré-requisitos** são comuns para o Skype for Business e o Exchange, [consulte o artigo de visão geral de sua lista de verificação de pré-](hybrid-modern-auth-overview.md)requisito.</span><span class="sxs-lookup"><span data-stu-id="36e81-119">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="36e81-120">Faça isso *antes* de começar qualquer uma das etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="36e81-120">Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="36e81-121">Colete as informações específicas da HMA necessárias em um arquivo ou no OneNote.</span><span class="sxs-lookup"><span data-stu-id="36e81-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="36e81-122">Ative a autenticação moderna para o EXO (se ainda não estiver ativada).</span><span class="sxs-lookup"><span data-stu-id="36e81-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="36e81-123">Ative a autenticação moderna para o SFBO (se ainda não estiver ativada).</span><span class="sxs-lookup"><span data-stu-id="36e81-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="36e81-124">Ative a autenticação moderna híbrida para o Exchange local.</span><span class="sxs-lookup"><span data-stu-id="36e81-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="36e81-125">Ative a autenticação moderna híbrida para o Skype for Business no local.</span><span class="sxs-lookup"><span data-stu-id="36e81-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="36e81-126">Observe que essas etapas ativam MA para SFB, SFBO, EXCH e EXO--ou seja, todos os produtos que podem participar de uma configuração de HMA de SFB e SFBO (incluindo dependências em EXCH/EXO).</span><span class="sxs-lookup"><span data-stu-id="36e81-126">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="36e81-127">Em outras palavras, se seus usuários estiverem hospedados em/têm caixas de correio criadas em qualquer parte do híbrido (EXO + SFBO, EXO + SFB, EXCH + SFBO ou EXCH + SFB), o produto final terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="36e81-127">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Uma topologia de HMA 6 do Skype for Business mista tem MA em todos os quatro locais possíveis.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="36e81-129">Como você pode ver, há quatro lugares diferentes para ativar MA!</span><span class="sxs-lookup"><span data-stu-id="36e81-129">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="36e81-130">Para obter a melhor experiência do usuário, recomendamos que você ative o MA nos quatro desses locais.</span><span class="sxs-lookup"><span data-stu-id="36e81-130">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="36e81-131">Se você não conseguir ativar o MA em todos esses locais, ajuste as etapas para ativar o MA somente nos locais necessários para o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="36e81-131">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="36e81-132">Consulte o [tópico sobre capacidade de suporte para o Skype for Business com ma](https://technet.microsoft.com/en-us/library/mt803262.aspx) para topologias suportadas.</span><span class="sxs-lookup"><span data-stu-id="36e81-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="36e81-133">**Importante** Verifique se você atendeu a todos os pré-requisitos antes de começar.</span><span class="sxs-lookup"><span data-stu-id="36e81-133">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="36e81-134">Você encontrará essas informações [aqui](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36e81-134">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="36e81-135">Coletar todas as informações específicas da HMA necessárias</span><span class="sxs-lookup"><span data-stu-id="36e81-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="36e81-136">Depois de verificar novamente se você atende aos [pré-requisitos](hybrid-modern-auth-overview.md) para usar a autenticação moderna (consulte a observação acima), você deve criar um arquivo para armazenar as informações necessárias para configurar a HMA nas etapas adiante.</span><span class="sxs-lookup"><span data-stu-id="36e81-136">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="36e81-137">Exemplos usados neste artigo:</span><span class="sxs-lookup"><span data-stu-id="36e81-137">Examples used in this article:</span></span> 
  
- <span data-ttu-id="36e81-138">**SIP/domínio SMTP**</span><span class="sxs-lookup"><span data-stu-id="36e81-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="36e81-139">Ex.</span><span class="sxs-lookup"><span data-stu-id="36e81-139">Ex.</span></span> <span data-ttu-id="36e81-140">contoso.com (é federado com o Office 365)</span><span class="sxs-lookup"><span data-stu-id="36e81-140">contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="36e81-141">**ID do locatário**</span><span class="sxs-lookup"><span data-stu-id="36e81-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="36e81-142">O GUID que representa o locatário do Office 365 (no logon de contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="36e81-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="36e81-143">**SFB 2015 CU5 Web Service URLs**</span><span class="sxs-lookup"><span data-stu-id="36e81-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="36e81-144">Você precisará de URL de serviço Web interno e externo para todos os pools do SfB 2015 implantados.</span><span class="sxs-lookup"><span data-stu-id="36e81-144">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="36e81-145">Para obtê-los, execute o seguinte no Shell de gerenciamento do Skype for Business:</span><span class="sxs-lookup"><span data-stu-id="36e81-145">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="36e81-146">Ex.</span><span class="sxs-lookup"><span data-stu-id="36e81-146">Ex.</span></span> <span data-ttu-id="36e81-147">Internamentehttps://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="36e81-147">Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="36e81-148">Ex.</span><span class="sxs-lookup"><span data-stu-id="36e81-148">Ex.</span></span> <span data-ttu-id="36e81-149">Externohttps://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="36e81-149">External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="36e81-150">Se você estiver usando um servidor Standard Edition, a URL interna ficará em branco.</span><span class="sxs-lookup"><span data-stu-id="36e81-150">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="36e81-151">Nesse caso, use o FQDN do pool para a URL interna.</span><span class="sxs-lookup"><span data-stu-id="36e81-151">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="36e81-152">Ativar a autenticação moderna para o EXO</span><span class="sxs-lookup"><span data-stu-id="36e81-152">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="36e81-153">Siga as instruções aqui: [Exchange Online: como habilitar seu locatário para autenticação moderna.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="36e81-153">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="36e81-154">Ativar a autenticação moderna para o SFBO</span><span class="sxs-lookup"><span data-stu-id="36e81-154">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="36e81-155">Siga as instruções aqui: [Skype for Business Online: habilitar seu locatário para autenticação moderna](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="36e81-155">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="36e81-156">Ativar a autenticação moderna híbrida para o Exchange local</span><span class="sxs-lookup"><span data-stu-id="36e81-156">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="36e81-157">Siga as instruções aqui: [como configurar o Exchange Server no local para usar a autenticação moderna híbrida](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="36e81-157">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="36e81-158">Ativar a autenticação moderna híbrida para o Skype for Business no local</span><span class="sxs-lookup"><span data-stu-id="36e81-158">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="36e81-159">Adicionar URLs do serviço Web local como SPNs no Azure AD</span><span class="sxs-lookup"><span data-stu-id="36e81-159">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="36e81-160">Agora, você precisará executar comandos para adicionar as URLs (coletadas anteriormente) como entidades de serviço no SFBO.</span><span class="sxs-lookup"><span data-stu-id="36e81-160">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="36e81-161">**Observação** Os SPNs (nomes de entidade de serviço) identificam os serviços Web e os associam a um objeto de segurança (como um nome de conta ou grupo) para que o serviço possa atuar em nome de um usuário autorizado.</span><span class="sxs-lookup"><span data-stu-id="36e81-161">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="36e81-162">Os clientes que se autenticam em um servidor fazem uso de informações contidas em SPNs.</span><span class="sxs-lookup"><span data-stu-id="36e81-162">Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="36e81-163">Primeiro, conecte-se ao AAD com [estas instruções](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span><span class="sxs-lookup"><span data-stu-id="36e81-163">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>
    
2. <span data-ttu-id="36e81-164">Execute este comando, no local, para obter uma lista de URLs de serviços Web do SFB.</span><span class="sxs-lookup"><span data-stu-id="36e81-164">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="36e81-165">Observe que o AppPrincipalId começa com `00000004`.</span><span class="sxs-lookup"><span data-stu-id="36e81-165">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="36e81-166">Isso corresponde ao Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="36e81-166">This corresponds to Skype for Business Online.</span></span>
    
   <span data-ttu-id="36e81-167">Anote (e captura de tela para comparação posterior) a saída desse comando, que incluirá uma URL SE e um WS, mas que basicamente consiste em SPNs que começam `00000004-0000-0ff1-ce00-000000000000/`com.</span><span class="sxs-lookup"><span data-stu-id="36e81-167">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. <span data-ttu-id="36e81-168">Se as URLs de SFB internas **ou** externas do local estiverem ausentes (por exemplo, https://lyncwebint01.contoso.com e https://lyncwebext01.contoso.com) precisaremos adicionar esses registros específicos a essa lista.</span><span class="sxs-lookup"><span data-stu-id="36e81-168">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="36e81-169">Certifique-se de substituir *as URLs de exemplo* abaixo por suas URLs reais na adição de comandos!</span><span class="sxs-lookup"><span data-stu-id="36e81-169">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="36e81-170">Verifique se os novos registros foram adicionados executando o comando Get-MsolServicePrincipal da etapa 2 novamente e examinando a saída.</span><span class="sxs-lookup"><span data-stu-id="36e81-170">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="36e81-171">Compare a lista/captura de tela antes da nova lista de SPNs (você também pode capturar a nova lista para seus registros).</span><span class="sxs-lookup"><span data-stu-id="36e81-171">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="36e81-172">Se você tiver êxito, verá as duas novas URLs na lista.</span><span class="sxs-lookup"><span data-stu-id="36e81-172">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="36e81-173">Indo em nosso exemplo, a lista de SPNs agora incluirá as URLs https://lyncwebint01.contoso.com específicas e https://lyncwebext01.contoso.com/.</span><span class="sxs-lookup"><span data-stu-id="36e81-173">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="36e81-174">Criar o objeto de servidor de autenticação EvoSTS</span><span class="sxs-lookup"><span data-stu-id="36e81-174">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="36e81-175">Execute o seguinte comando no Shell de gerenciamento do Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="36e81-175">Run the following command in the Skype for Business Management Shell.</span></span>
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="36e81-176">Habilitar a autenticação moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="36e81-176">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="36e81-177">Esta é a etapa que realmente ativa o MA.</span><span class="sxs-lookup"><span data-stu-id="36e81-177">This is the step that actually turns MA on.</span></span> <span data-ttu-id="36e81-178">Todas as etapas anteriores podem ser executadas antecipadamente sem alterar o fluxo de autenticação do cliente.</span><span class="sxs-lookup"><span data-stu-id="36e81-178">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="36e81-179">Quando estiver pronto para alterar o fluxo de autenticação, execute este comando no Shell de gerenciamento do Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="36e81-179">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a><span data-ttu-id="36e81-180">Verify</span><span class="sxs-lookup"><span data-stu-id="36e81-180">Verify</span></span>

<span data-ttu-id="36e81-181">Depois de habilitar a HMA, o próximo login de um cliente usará o novo fluxo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="36e81-181">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="36e81-182">Observe que apenas a ativação da HMA não acionará uma nova autenticação para qualquer cliente.</span><span class="sxs-lookup"><span data-stu-id="36e81-182">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="36e81-183">Os clientes são autenticados novamente com base no tempo de vida dos tokens de autenticação e/ou certs que possuem.</span><span class="sxs-lookup"><span data-stu-id="36e81-183">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="36e81-184">Para testar se a HMA está funcionando depois de tê-la habilitado, saia do SFB de teste do cliente Windows e certifique-se de clicar em excluir minhas credenciais.</span><span class="sxs-lookup"><span data-stu-id="36e81-184">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="36e81-185">Entre novamente.</span><span class="sxs-lookup"><span data-stu-id="36e81-185">Sign in again.</span></span> <span data-ttu-id="36e81-186">Agora, o cliente deve usar o fluxo de autenticação moderna e seu logon incluirá um prompt do **Office 365** para uma conta de ' trabalho ou escola ', visto imediatamente antes de o cliente entrar em contato com o servidor e fizer o login.</span><span class="sxs-lookup"><span data-stu-id="36e81-186">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="36e81-187">Você também deve verificar as ' informações de configuração ' para clientes do Skype for Business para uma ' autoridade OAuth '.</span><span class="sxs-lookup"><span data-stu-id="36e81-187">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="36e81-188">Para fazer isso no computador cliente, pressione a tecla CTRL ao mesmo tempo em que você clica com o botão direito do mouse no ícone do Skype for Business na bandeja de notificação do Windows.</span><span class="sxs-lookup"><span data-stu-id="36e81-188">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="36e81-189">Clique em informações de configuração no menu exibido.</span><span class="sxs-lookup"><span data-stu-id="36e81-189">Click Configuration Information in the menu that appears.</span></span> <span data-ttu-id="36e81-190">Na janela ' informações de configuração do Skype for Business ' que aparecerá na área de trabalho, procure o seguinte:</span><span class="sxs-lookup"><span data-stu-id="36e81-190">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![As informações de configuração de um cliente Skype for Business usando a autenticação moderna mostra uma URL de autoridade OAUTH do https://login.windows.net/common/oauth2/authorizeLYNC e EWS de.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="36e81-192">Você também deve manter pressionada a tecla CTRL enquanto clica com o botão direito do mouse no ícone do cliente Outlook (também na bandeja de notificações do Windows) e clique em "status da conexão".</span><span class="sxs-lookup"><span data-stu-id="36e81-192">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="36e81-193">Procure o endereço SMTP do cliente em relação a um tipo Authn de ' portador\*', que representa o token de portador usado no OAuth.</span><span class="sxs-lookup"><span data-stu-id="36e81-193">Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="36e81-194">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="36e81-194">Related articles</span></span>

<span data-ttu-id="36e81-195">[Link de volta para a visão geral da autenticação moderna](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="36e81-195">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="36e81-196">Você precisa saber como usar a ADAL (autenticação moderna) para os clientes do Skype for Business?</span><span class="sxs-lookup"><span data-stu-id="36e81-196">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="36e81-197">Temos as etapas [aqui](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="36e81-197">We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="36e81-198">Você gostaria de ler essas etapas à medida que elas aparecem para o Exchange Server, no local, executando sem o SFB?</span><span class="sxs-lookup"><span data-stu-id="36e81-198">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB?</span></span> <span data-ttu-id="36e81-199">Essas etapas estão disponíveis aqui.</span><span class="sxs-lookup"><span data-stu-id="36e81-199">Those steps are available here.</span></span>
  

