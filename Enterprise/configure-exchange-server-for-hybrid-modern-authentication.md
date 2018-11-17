---
title: Como configurar o Exchange Server no local para usar a autenticação moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Híbrido moderno autenticação (HMA), é um método de gerenciamento de identidade que oferece mais seguro de autenticação e autorização e está disponível para implantações híbridas do Exchange server local.
ms.openlocfilehash: df5ea03b06ee1c101b03e19c7acb445c9543586b
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547153"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="35324-103">Como configurar o Exchange Server no local para usar a autenticação moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="35324-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="35324-104">Híbrido moderno autenticação (HMA), é um método de gerenciamento de identidade que oferece mais seguro de autenticação e autorização e está disponível para implantações híbridas do Exchange server local.</span><span class="sxs-lookup"><span data-stu-id="35324-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="35324-105">FYI</span><span class="sxs-lookup"><span data-stu-id="35324-105">FYI</span></span>

<span data-ttu-id="35324-106">Antes de começar, posso chamar:</span><span class="sxs-lookup"><span data-stu-id="35324-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="35324-107">Autenticação de moderno híbrida \> HMA</span><span class="sxs-lookup"><span data-stu-id="35324-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="35324-108">Local do Exchange \> EXCH</span><span class="sxs-lookup"><span data-stu-id="35324-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="35324-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="35324-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="35324-110">Além disso, *que se um elemento gráfico neste artigo tem um objeto que tem ' acinzentado ' ou 'esmaecida' isso significa que o elemento mostrado em cinza não está incluído na configuração HMA específica* .</span><span class="sxs-lookup"><span data-stu-id="35324-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="35324-111">Habilitar a autenticação híbrida moderno</span><span class="sxs-lookup"><span data-stu-id="35324-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="35324-112">Ativando HMA meios:</span><span class="sxs-lookup"><span data-stu-id="35324-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="35324-113">Sendo Verifique se que você está cumprindo os pré-requisitos antes de começar.</span><span class="sxs-lookup"><span data-stu-id="35324-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="35324-p101">Desde muitos **pré-requisitos** são comuns para ambos os Skype para Exchange, [Visão geral da autenticação de moderno híbrida e pré-requisitos para utilizá-lo com local Skype para servidores Exchange e de negócios](hybrid-modern-auth-overview.md)e de negócios. Faça isso antes de começar qualquer uma das etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="35324-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="35324-116">Adicionando local URLs do web service como nomes de entidade de serviço (SPNs) no Windows Azure AD.</span><span class="sxs-lookup"><span data-stu-id="35324-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="35324-117">Garantindo que todos os diretórios virtuais estão habilitados para HMA</span><span class="sxs-lookup"><span data-stu-id="35324-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="35324-118">Verificando o objeto de servidor de autenticação EvoSTS</span><span class="sxs-lookup"><span data-stu-id="35324-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="35324-119">Habilitando HMA no ajuste</span><span class="sxs-lookup"><span data-stu-id="35324-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="35324-p102">**Observação** Sua versão do Office oferecem suporte a MA? Consulte [moderno como funciona a autenticação para aplicativos de cliente do Office 2013 e Office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="35324-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="35324-122">Verifique se que você atende a todos os pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="35324-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="35324-p103">Como muitos pré-requisitos são comuns para ambos os Skype para Exchange e de negócios, examine o [Visão geral da autenticação de moderno híbrida e pré-requisitos para utilizá-lo com Skype local para os servidores de negócios e do Exchange](hybrid-modern-auth-overview.md). Fazer esta *antes de* começar qualquer uma das etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="35324-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="35324-125">Adicionar local de URLs de serviço web como SPNs no Azure AD</span><span class="sxs-lookup"><span data-stu-id="35324-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="35324-p104">Execute os comandos que atribuir sua web local URLs de serviço, como o Windows Azure AD SPNs. SPNs são usados por computadores clientes e dispositivos durante a autenticação e autorização. Todas as URLs que poderiam ser usadas para conectar-se no local para Windows Azure Active Directory (AAD) devem ser registradas no AAD (Isso inclui namespaces internos e externos).</span><span class="sxs-lookup"><span data-stu-id="35324-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="35324-p105">Primeiro, reúna todas as URLs que você precisa adicionar no AAD. Execute estes comandos no local:</span><span class="sxs-lookup"><span data-stu-id="35324-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="35324-131">Verifique se as URLs que os clientes podem se conectar a são listados como nomes de entidade de serviço HTTPS no AAD.</span><span class="sxs-lookup"><span data-stu-id="35324-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="35324-132">Primeiro, se conecte ao AAD com [estas instruções](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="35324-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="35324-133">**Observação** Você precisa usar a opção de Connect-MsolService a partir desta página para poder usar o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="35324-133">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="35324-134">Para o Exchange URLs relacionados, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="35324-134">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="35324-p106">Tomar nota das (e captura de tela para comparação posterior) a saída deste comando, que deve incluir um https:// *autodiscover.yourdomain.com* e a URL de *e-mailseudominio.com* https://, mas consistem principalmente SPNs que começam com 00000002-0000-0ff1-CE00-000000000000 /. Se houver https:// URLs a partir de seu local que está ausente precisamos adicionar esses registros específicos a essa lista.</span><span class="sxs-lookup"><span data-stu-id="35324-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="35324-137">Se você não vir os registros MAPI/HTTP, EWS, ActiveSync, OAB e descoberta automática internos e externos nessa lista, você deve adicioná-los usando o comando a seguir (o exemplo URLs são '`mail.corp.contoso.com`'e'`owa.contoso.com`', mas você tinha a **Substituir as URLs de exemplo com seu próprio** ) :</span><span class="sxs-lookup"><span data-stu-id="35324-137">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="35324-p107">Verifique se que seus novos registros foram adicionados executando o comando Get-MsolServicePrincipal da etapa 2 novamente e, em seguida, procurando por meio de saída. Compare a lista / captura de tela de antes da nova lista de SPNs (você pode também a nova lista de captura de tela para seus registros). Se você tiver sido bem-sucedida, você verá duas novas URLs na lista. Vai pelo nosso exemplo, a lista de SPNs agora inclui as URLs específicas `https://mail.corp.contoso.com` e `https://owa.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="35324-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="35324-142">Verifique se que diretórios virtuais estão configuradas corretamente</span><span class="sxs-lookup"><span data-stu-id="35324-142">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="35324-143">Verificar agora OAuth adequadamente está habilitado no Exchange em todos os do Outlook diretórios virtuais pode usar, executando os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="35324-143">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="35324-144">Seleção a saída para certificar-se de **OAuth** está habilitada em cada um desses VDirs, você verá algo semelhante a esta (e o mais importante a ser analisado é 'OAuth');</span><span class="sxs-lookup"><span data-stu-id="35324-144">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="35324-145">Se o OAuth está faltando qualquer servidor e qualquer um dos quatro diretórios virtuais, você precisará adicioná-lo usando os comandos relevantes antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="35324-145">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="35324-146">Confirmar que o objeto do servidor de autenticação EvoSTS está presente</span><span class="sxs-lookup"><span data-stu-id="35324-146">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="35324-p108">Volte para o Shell de gerenciamento do Exchange local para esse último comando. Agora você pode validar que o seu local tem uma entrada para o provedor de autenticação evoSTS:</span><span class="sxs-lookup"><span data-stu-id="35324-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="35324-p109">A saída deve mostrar um AuthServer do EvoSts nome e o estado 'Enabled' deve ser True. Se você não vir isso, você deve baixar e executar a versão mais recente do Assistente de configuração híbrida.</span><span class="sxs-lookup"><span data-stu-id="35324-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="35324-151">**Importante** Se você estiver executando o Exchange 2010 em seu ambiente, o provedor de autenticação EvoSTS não será criado.</span><span class="sxs-lookup"><span data-stu-id="35324-151">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="35324-152">Habilitar HMA</span><span class="sxs-lookup"><span data-stu-id="35324-152">Enable HMA</span></span>

<span data-ttu-id="35324-153">Execute o seguinte comando no Shell de gerenciamento do Exchange, no local:</span><span class="sxs-lookup"><span data-stu-id="35324-153">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="35324-154">Verificar</span><span class="sxs-lookup"><span data-stu-id="35324-154">Verify</span></span>

<span data-ttu-id="35324-p110">Depois que você ativar HMA, próximo de login do cliente usarão o novo fluxo de autenticação. Observe que apenas ativem HMA não aciona um re-autenticação para qualquer cliente. O clientes sua reconexão com base no tempo de vida de e/ou os tokens de autenticação têm os certificados.</span><span class="sxs-lookup"><span data-stu-id="35324-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="35324-p111">Você também deve mantenha pressionada a tecla CTRL ao mesmo tempo que Right clicar no ícone para o cliente do Outlook (também na bandeja do Windows notificações) e clique em Status do Conexão. Procure o endereço de SMTP do cliente em relação a um tipo de 'Authn' de ' portador\*', que representa o token do transportador usado em OAuth.</span><span class="sxs-lookup"><span data-stu-id="35324-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="35324-p112">**Observação** Precisa configurar Skype for Business com HMA? Você precisará de dois artigos: um que lista [topologias com suporte](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)e outro que mostra [como fazer a configuração](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="35324-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="35324-162">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="35324-162">Related topics</span></span>

[<span data-ttu-id="35324-163">Visão geral do híbrido autenticação moderno e pré-requisitos para usá-lo com Skype local para os servidores de negócios e do Exchange</span><span class="sxs-lookup"><span data-stu-id="35324-163">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

