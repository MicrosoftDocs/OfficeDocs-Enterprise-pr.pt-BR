---
title: Como configurar o Exchange Server no local para usar a autenticação moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: A protocolo de autenticação moderna (HMA) híbrida é um método de gerenciamento de identidades que oferece autenticação e autorização de usuário mais seguras e está disponível para implantações híbridas locais do Exchange Server.
ms.openlocfilehash: c86d794d0952faf59a724976fa2a180084646baa
ms.sourcegitcommit: ffa5c7a2d0e1eaa40b84ea1e9fb6992d1f05aa86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "34332618"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="a3f3e-103">Como configurar o Exchange Server no local para usar a autenticação moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="a3f3e-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="a3f3e-104">A protocolo de autenticação moderna (HMA) híbrida é um método de gerenciamento de identidades que oferece autenticação e autorização de usuário mais seguras e está disponível para implantações híbridas locais do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="a3f3e-105">CONHECIMENTO</span><span class="sxs-lookup"><span data-stu-id="a3f3e-105">FYI</span></span>

<span data-ttu-id="a3f3e-106">Antes de começar, chamo:</span><span class="sxs-lookup"><span data-stu-id="a3f3e-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="a3f3e-107">HMA de autenticação \> moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="a3f3e-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="a3f3e-108">Exchange local \></span><span class="sxs-lookup"><span data-stu-id="a3f3e-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="a3f3e-109">EXO do \> Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a3f3e-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="a3f3e-110">Além disso, *se um gráfico neste artigo tiver um objeto que é ' esmaecido ' ou ' esmaecido ' que significa que o elemento mostrado em cinza não está incluído na configuração específica da HMA* .</span><span class="sxs-lookup"><span data-stu-id="a3f3e-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="a3f3e-111">Habilitar a autenticação moderna híbrida</span><span class="sxs-lookup"><span data-stu-id="a3f3e-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="a3f3e-112">Virar a HMA em significa:</span><span class="sxs-lookup"><span data-stu-id="a3f3e-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="a3f3e-113">Ter certeza de que você atende ao pré antes de começar.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="a3f3e-114">Como muitos **pré-requisitos** são comuns para o Skype for Business e o Exchange, a [visão geral da autenticação moderna híbrida e os pré-requisitos para usá-lo com o Skype for Business e servidores do Exchange locais](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a3f3e-114">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="a3f3e-115">Faça isso antes de começar qualquer uma das etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-115">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="a3f3e-116">Adicionar URLs do serviço Web local como nomes de entidade de serviço (SPNs) no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="a3f3e-117">Garantir que todos os diretórios virtuais estejam habilitados para a HMA</span><span class="sxs-lookup"><span data-stu-id="a3f3e-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="a3f3e-118">Verificando o objeto do servidor de autenticação EvoSTS</span><span class="sxs-lookup"><span data-stu-id="a3f3e-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="a3f3e-119">Habilitando HMA no EXCH.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="a3f3e-120">**Observação** Sua versão do Office oferece suporte ao MA?</span><span class="sxs-lookup"><span data-stu-id="a3f3e-120">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="a3f3e-121">Veja [como a autenticação moderna funciona para aplicativos cliente do office 2013 e office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="a3f3e-121">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="a3f3e-122">Certifique-se de que você atende a todos os reqs</span><span class="sxs-lookup"><span data-stu-id="a3f3e-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="a3f3e-123">Como muitos pré-requisitos são comuns para o Skype for Business e o Exchange, revise a [visão geral da autenticação moderna híbrida e os pré-requisitos para usá-lo com o Skype for Business e os servidores do Exchange locais](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a3f3e-123">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="a3f3e-124">Faça isso *antes* de começar qualquer uma das etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-124">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="a3f3e-125">Adicionar URLs do serviço Web local como SPNs no Azure AD</span><span class="sxs-lookup"><span data-stu-id="a3f3e-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="a3f3e-126">Execute os comandos que atribuem as URLs do serviço Web local como SPNs do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-126">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="a3f3e-127">Os SPNs são usados por máquinas clientes e dispositivos durante a autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-127">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="a3f3e-128">Todas as URLs que podem ser usadas para conectar-se ao Azure Active Directory (AAD) devem ser registradas no AAD (isso inclui namespaces internos e externos).</span><span class="sxs-lookup"><span data-stu-id="a3f3e-128">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="a3f3e-129">Primeiro, reúna todas as URLs que você precisa adicionar no AAD.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-129">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="a3f3e-130">Execute estes comandos no local:</span><span class="sxs-lookup"><span data-stu-id="a3f3e-130">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="a3f3e-131">Verifique se os clientes URLs que podem se conectar estão listados como nomes de entidade de serviço HTTPS no AAD.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="a3f3e-132">Primeiro, conecte-se ao AAD com [estas instruções](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="a3f3e-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="a3f3e-133">**Observação** Você precisa usar a opção Connect-MsolService desta página para poder usar o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-133">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="a3f3e-134">Para suas URLs relacionadas ao Exchange, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a3f3e-134">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="a3f3e-135">Anote (e captura de tela para comparação posterior) a saída desse comando, que deve incluir uma URL https:// *autodiscover.yourdomain.com* e https:// *mail.yourdomain.com* , mas que basicamente consiste em SPNs que começam com 00000002-0000-0ff1-ce00-000000000000/.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-135">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="a3f3e-136">Se houver https://URLs de seu local que estão ausentes, precisaremos adicionar esses registros específicos a essa lista.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-136">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="a3f3e-137">Se você não vir seus registros internos e externos de MAPI/HTTP, EWS, ActiveSync, OAB e descoberta automática nesta lista, você deve adicioná-los usando o comando a seguir (as URLs de`mail.corp.contoso.com`exemplo são '`owa.contoso.com`' e ' ', mas você **substituirá os URLs de exemplo por seu próprio** ) :</span><span class="sxs-lookup"><span data-stu-id="a3f3e-137">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="a3f3e-138">Verifique se os novos registros foram adicionados executando o comando Get-MsolServicePrincipal da etapa 2 novamente e examinando a saída.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-138">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="a3f3e-139">Compare a lista/captura de tela antes da nova lista de SPNs (você também pode capturar a nova lista para seus registros).</span><span class="sxs-lookup"><span data-stu-id="a3f3e-139">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="a3f3e-140">Se você tiver êxito, verá as duas novas URLs na lista.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-140">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="a3f3e-141">Indo em nosso exemplo, a lista de SPNs agora incluirá as URLs `https://mail.corp.contoso.com` específicas e `https://owa.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-141">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="a3f3e-142">Verificar se os diretórios virtuais estão configurados corretamente</span><span class="sxs-lookup"><span data-stu-id="a3f3e-142">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="a3f3e-143">Agora, verifique se o OAuth está habilitado corretamente no Exchange em todos os diretórios virtuais que o Outlook pode usar executando os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="a3f3e-143">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="a3f3e-144">Verifique a saída para certificar-se de que o **OAuth** está habilitado em cada um desses VDirs, ele terá uma aparência semelhante a esta (e a principal coisa a ser verificada é "OAuth");</span><span class="sxs-lookup"><span data-stu-id="a3f3e-144">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

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
  
<span data-ttu-id="a3f3e-145">Se o OAuth estiver ausente de qualquer servidor e de qualquer um dos quatro diretórios virtuais, você precisará adicioná-lo usando os comandos relevantes antes de prosseguir.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-145">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="a3f3e-146">Confirmar se o objeto de servidor de autenticação EvoSTS está presente</span><span class="sxs-lookup"><span data-stu-id="a3f3e-146">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="a3f3e-147">Retorne ao Shell de gerenciamento do Exchange local para este último comando.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-147">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="a3f3e-148">Agora você pode validar que seu local tem uma entrada para o provedor de autenticação do evoSTS:</span><span class="sxs-lookup"><span data-stu-id="a3f3e-148">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="a3f3e-149">A saída deve mostrar um AuthServer do nome EvoSts e o estado ' Enabled ' deve ser true.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-149">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="a3f3e-150">Se você não vir isso, baixe e execute a versão mais recente do assistente de configuração híbrida.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-150">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="a3f3e-151">**Importante** Se você estiver executando o Exchange 2010 em seu ambiente, o provedor de autenticação do EvoSTS não será criado.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-151">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="a3f3e-152">Habilitar HMA</span><span class="sxs-lookup"><span data-stu-id="a3f3e-152">Enable HMA</span></span>

<span data-ttu-id="a3f3e-153">Execute o seguinte comando no Shell de gerenciamento do Exchange, no local:</span><span class="sxs-lookup"><span data-stu-id="a3f3e-153">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="a3f3e-154">Verify</span><span class="sxs-lookup"><span data-stu-id="a3f3e-154">Verify</span></span>

<span data-ttu-id="a3f3e-155">Depois de habilitar a HMA, o próximo login de um cliente usará o novo fluxo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-155">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="a3f3e-156">Observe que apenas a ativação da HMA não acionará uma nova autenticação para qualquer cliente.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-156">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="a3f3e-157">Os clientes são autenticados novamente com base no tempo de vida dos tokens de autenticação e/ou certs que possuem.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-157">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="a3f3e-158">Você também deve manter pressionada a tecla CTRL enquanto clica com o botão direito do mouse no ícone do cliente Outlook (também na bandeja de notificações do Windows) e clique em "status da conexão".</span><span class="sxs-lookup"><span data-stu-id="a3f3e-158">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="a3f3e-159">Procure o endereço SMTP do cliente em relação a um tipo "Authn" de "portador\*", que representa o token de portador usado no OAuth.</span><span class="sxs-lookup"><span data-stu-id="a3f3e-159">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="a3f3e-160">**Observação** Precisa configurar o Skype for Business com a HMA?</span><span class="sxs-lookup"><span data-stu-id="a3f3e-160">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="a3f3e-161">Você precisará de dois artigos: um que [](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)lista as topologias suportadas e uma que mostra [como fazer a configuração](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a3f3e-161">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="a3f3e-162">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="a3f3e-162">Related topics</span></span>

[<span data-ttu-id="a3f3e-163">Visão geral da autenticação moderna híbrida e pré-requisitos para usá-lo com o Skype for Business e servidores do Exchange locais</span><span class="sxs-lookup"><span data-stu-id="a3f3e-163">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

