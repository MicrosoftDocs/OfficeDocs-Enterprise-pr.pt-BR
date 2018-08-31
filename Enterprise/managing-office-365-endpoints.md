---
title: Gerenciando pontos de extremidade do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Algumas redes são projetados para restringir o acesso à internet, para garantir que os computadores nas redes como essas podem acessar o Office 365, os administradores de rede e o proxy precisam gerenciar a lista de FQDNs, URLs, e endereços IP que compõem a lista de pontos de extremidade do Office 365. Esses necessidade a ser adicionado às regras de firewall ou proxy e PAC arquivos para garantir que as solicitações de rede são capazes de alcançar o Office 365.
ms.openlocfilehash: 0396174719adc7794a1d6bb4b1f950bfe4603996
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539268"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="06755-104">Gerenciando pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="06755-104">Managing Office 365 endpoints</span></span>

## <a name="office-365-network-connectivity"></a><span data-ttu-id="06755-105">Conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="06755-105">Office 365 network connectivity</span></span>

 <span data-ttu-id="06755-p102">Conexões para o Office 365 consistem em alto volume, solicitações de rede de perímetro que executar melhor quando eles estiver feitos ao longo de uma saída de baixa latência está perto do usuário. Algumas conexões do Office 365 podem se beneficiar de otimizar a conexão.</span><span class="sxs-lookup"><span data-stu-id="06755-p102">Connections to Office 365 consist of high volume, trusted network requests that perform best when they're made over a low-latency egress that is near the user. Some Office 365 connections can benefit from optimizing the connection.</span></span> 
  
1. <span data-ttu-id="06755-108">Certifique-se de seu firewall permitir listas permitem conectividade aos pontos de extremidade do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06755-108">Ensure your firewall allow lists allow for connectivity to Office 365 endpoints.</span></span>
    
2. <span data-ttu-id="06755-109">Use sua infraestrutura de proxy para permitir a conectividade à Internet para o caractere curinga e destinos de publicação cancelados.</span><span class="sxs-lookup"><span data-stu-id="06755-109">Use your proxy infrastructure to allow Internet connectivity to wildcard and unpublished destinations.</span></span>
    
3. <span data-ttu-id="06755-110">Manter uma configuração de rede de perímetro ideal.</span><span class="sxs-lookup"><span data-stu-id="06755-110">Maintain an optimal perimeter network configuration.</span></span>
    
4. <span data-ttu-id="06755-111">[Verifique se você estiver recebendo a melhor conectividade](https://aka.ms/o365perfprinciples).</span><span class="sxs-lookup"><span data-stu-id="06755-111">[Ensure you're getting the best connectivity](https://aka.ms/o365perfprinciples).</span></span>
    
5. <span data-ttu-id="06755-112">Leia os [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md) para entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível.</span><span class="sxs-lookup"><span data-stu-id="06755-112">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
    
![Conectando-se ao Office 365 através de firewalls e proxies.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a><span data-ttu-id="06755-114">Atualização do seu firewall da saída listas de permissões</span><span class="sxs-lookup"><span data-stu-id="06755-114">Update your firewall's outbound allow lists</span></span>

<span data-ttu-id="06755-p103">Você pode otimizar sua rede enviando a que todos os confiáveis solicitações diretamente através do firewall da rede do Office 365, ignorando todos inspeção de nível de pacotes adicionais ou processamento. Isso reduz o desempenho lento de latência e reduz seus requisitos de capacidade de perímetro. A maneira mais fácil para escolher qual rede solicitações a confiança é usar nossos arquivos PAC pré-criados na guia **Proxies** acima.</span><span class="sxs-lookup"><span data-stu-id="06755-p103">You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces slow performance from latency and reduces your perimeter capacity requirements. The easiest way to choose which network requests to trust is to use our pre-built PAC files on the **Proxies** tab above.</span></span> 
  
<span data-ttu-id="06755-p104">Se o tráfego de saída de blocos de firewall, você vai querer garantir que todos o IP e FQDNs listado como **necessários** neste [arquivo XML](https://go.microsoft.com/fwlink/?LinkId=533185) estão na lista de permissões. Reconhece que todos os serviços exigem o uso de alguns 3º serviços de terceiros. Nós não forneça endereços IP para esses serviços de terceiros 3º como provedores DNS do certificado provedores, redes de fornecimento de conteúdo e assim por diante. Para obter a funcionalidade completa do Office 365, você deve ser capaz de acessar todos os destinos solicitados pelo Office 365 independentemente quanta informação publicamos sobre o destino.</span><span class="sxs-lookup"><span data-stu-id="06755-p104">If your firewall blocks outbound traffic, you'll want to ensure all of the IP and FQDNs listed as **Required** in this [XML file](https://go.microsoft.com/fwlink/?LinkId=533185) are on the allow list. Recognize all services require the use of some 3rd party services. We don't provide IP addresses for these 3rd party services such as certificate providers, Content Delivery Networks, DNS providers, and so on. For full Office 365 functionality, you must be able to reach all destinations requested by Office 365 regardless of how much information we publish about the destination.</span></span> 
  
<span data-ttu-id="06755-122">Muitos destinos não têm um endereço IP publicado ou são listados como um domínio de curinga com nenhum nome de domínio totalmente qualificado específico, para usar essa funcionalidade, você deve ser capaz de resolver esses pedidos de rede como o IP atual está sendo solicitado de endereços e enviar o solicitação de rede pela Internet.</span><span class="sxs-lookup"><span data-stu-id="06755-122">Many destinations do not have an IP address published or are listed as a wildcard domain with no specific fully qualified domain name, to use this functionality you must be able to resolve these network requests to the current IP address being requested and send the network request over the Internet.</span></span>
  
<span data-ttu-id="06755-p105">Automatize o processo usando um firewall que analisa o arquivo XML em seu nome e atualiza suas regras automaticamente com base em serviços ou recursos que você pretende encaminhar diretamente através do firewall. Você também pode usar a ferramenta de [Intervalo do Azure](https://azurerange.azurewebsites.net/) que foi criada pela comunidade e analisa o XML para você com opções de exportação para configuração da lista de ACL ou Cisco XE rota, CSV ou texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="06755-p105">Automate your process by using a firewall that parses the XML file on your behalf and updates your rules automatically based on the services or features you plan to route directly through your firewall. You can also use the [Azure Range](https://azurerange.azurewebsites.net/) tool that has been built by the community and parses the XML for you with export options for Cisco XE Route or ACL list configuration, plain text, or CSV.</span></span> 
  
<span data-ttu-id="06755-125">Uma explicação mais os destinos de rede está disponível em nosso [site de referência](urls-and-ip-address-ranges.md) também por meio de [log de alteração de RSS com base em](https://go.microsoft.com/fwlink/p/?linkid=236301) nosso, portanto você pode inscrever-se às alterações.</span><span class="sxs-lookup"><span data-stu-id="06755-125">A longer explanation of the network destinations is available on our [reference site](urls-and-ip-address-ranges.md) as well through our [RSS based change log](https://go.microsoft.com/fwlink/p/?linkid=236301) so you can subscribe to changes.</span></span> 
  
<span data-ttu-id="06755-126"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-126"></span></span>
## <a name="configure-outbound-paths-with-pac-files"></a><span data-ttu-id="06755-127">Configurar caminhos de saída com os arquivos de PAC</span><span class="sxs-lookup"><span data-stu-id="06755-127">Configure outbound paths with PAC files</span></span>

<span data-ttu-id="06755-p106">Use arquivos PAC ou WPAD para gerenciar solicitações de rede que estão associadas com o Office 365, mas não têm um endereço IP fornecido. Solicitações de rede comuns que são enviadas por meio de um dispositivo de proxy ou perímetro acarretar uma latência adicional. Enquanto a autenticação de proxy provoca a maior imposto, outros serviços, como pesquisa de reputação e tentativas para inspecionar pacotes podem causar uma experiência de usuário ruim. Além disso, esses dispositivos de rede de perímetro precisam capacidade suficiente para processar todas as solicitações de rede. É recomendável ignorando a infra-estrutura de inspeção ou proxy para solicitações de rede diretas do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06755-p106">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While proxy authentication incurs the largest tax, other services such as reputation lookup and attempts to inspect packets can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="06755-p107">Use um dos arquivos nosso PAC como um ponto de partida para determinar qual o tráfego de rede será enviado a um proxy e qual será enviada a um firewall. Se estiver familiarizado com arquivos de PAC ou WPAD, leia esta postagem de [arquivos de PAC Implantando](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) um de nossos consultores do Office 365. Você vai querer Revise-as como um ponto de partida e editar de acordo com seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="06755-p107">Use one of our PAC files as a starting place to determine what network traffic will be sent to a proxy and which will be sent to a firewall. If you're new to PAC or WPAD files, read this post about [deploying PAC files](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) from one of our Office 365 consultants. You'll want to review these as a starting place and edit to suit your environment.</span></span> 
  
 <span data-ttu-id="06755-136">**Arquivos de PAC atualizados 10/7/2018**.</span><span class="sxs-lookup"><span data-stu-id="06755-136">**PAC files updated 7/10/2018**.</span></span> 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a><span data-ttu-id="06755-137">#1 - arquivo PAC: separa necessário FQDNs de Internet do FQDN de 365 Office conhecidos.</span><span class="sxs-lookup"><span data-stu-id="06755-137">#1 - PAC file: Separates required Internet FQDNs from known Office 365 FQDN.</span></span>

<span data-ttu-id="06755-p108">O primeiro exemplo é uma demonstração de nossa abordagem recomendada para gerenciar pontos de extremidade pela Internet apenas. Ignora o proxy para o Office 365 destinos onde o endereço IP é publicado e envia solicitações de rede restantes para o proxy.</span><span class="sxs-lookup"><span data-stu-id="06755-p108">The first example is a demonstration of our recommended approach to managing endpoints over the Internet only. Bypasses the proxy for Office 365 destinations where the IP address is published and sends remaining network requests to the proxy.</span></span>
  
<span data-ttu-id="06755-140">Trecho de código:</span><span class="sxs-lookup"><span data-stu-id="06755-140">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))
      
    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))
        
    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a><span data-ttu-id="06755-141">#2 – arquivo PAC: conectar ao Office 365 pela Internet e ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="06755-141">#2 - PAC file: Connect to Office 365 over the Internet and ExpressRoute</span></span>
<span data-ttu-id="06755-142"><a name="bkmk_inet-aer"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-142"></span></span>

<span data-ttu-id="06755-p109">O segundo exemplo é uma demonstração de nossa abordagem recomendada para gerenciar as conexões quando circuitos ExpressRoute e Internet estão disponíveis. Envia ExpressRoute divulgado destinos ao circuito ExpressRoute e Internet apenas divulgado destinos ao proxy.</span><span class="sxs-lookup"><span data-stu-id="06755-p109">The second example is a demonstration of our recommended approach to managing connections when ExpressRoute and Internet circuits are available. Sends ExpressRoute advertised destinations to the ExpressRoute circuit and Internet only advertised destinations to the proxy.</span></span>
  
<span data-ttu-id="06755-145">Trecho de código:</span><span class="sxs-lookup"><span data-stu-id="06755-145">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a><span data-ttu-id="06755-146">#3 – arquivo PAC: gerenciar todos os destinos de Office 365 coletivamente</span><span class="sxs-lookup"><span data-stu-id="06755-146">#3 - PAC file: Manage all Office 365 destinations collectively</span></span>
<span data-ttu-id="06755-147"><a name="bkmk_inet-direct"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-147"></span></span>

<span data-ttu-id="06755-p110">O terceiro exemplo demonstra o envio de todas as solicitações de rede associadas com o Office 365 para um único destino. Isso geralmente é usado para ignorar todos os inspeção de solicitações de rede do Office 365 e oferece a você um formato onde todos publicado pontos de extremidade está na lista no formato a ser usado para sua personalização PAC.</span><span class="sxs-lookup"><span data-stu-id="06755-p110">The third example demonstrates sending all network requests associated with Office 365 to a single destination. This is commonly used to bypass all inspection of Office 365 network requests and offers you a format where all published endpoints are in list in the PAC format to use for your customization.</span></span>
  
<span data-ttu-id="06755-150">Trecho de código:</span><span class="sxs-lookup"><span data-stu-id="06755-150">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a><span data-ttu-id="06755-151">Usam scripts personalizados ou criar manualmente seus próprios arquivos PAC</span><span class="sxs-lookup"><span data-stu-id="06755-151">Use custom scripts or manually create your own PAC files</span></span>
<span data-ttu-id="06755-152"><a name="pacfiles_manual"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-152"></span></span>

<span data-ttu-id="06755-p111">Eis algumas ferramentas mais da comunidade, se você tiver criado algo que você gostaria de compartilhar deixe uma nota nos comentários. None da comunidade ferramentas mencionadas neste artigo são oficialmente suportado ou mantida pela Microsoft e são oferecidos para sua conveniência.</span><span class="sxs-lookup"><span data-stu-id="06755-p111">Here's a few more tools from the community, if you've built something you'd like to share leave a note in the comments. None of the community tools referenced in this article are officially supported or maintained by Microsoft and are provided here for your convenience.</span></span>
  
- <span data-ttu-id="06755-p112">Esta é a ferramenta de comunidade gerada mais antiga para ajudar a gerenciar o processo, uma ferramenta criada por um membro da comunidade do Office 365. Aqui está o link para [Baixar](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span><span class="sxs-lookup"><span data-stu-id="06755-p112">This is the oldest community generated tool to help manage the process, a tool built by a member of the Office 365 community. Here is link to [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span></span>
    
- <span data-ttu-id="06755-157">Verificação de conceito com regras de firewall exportável: [API do Microsoft Cloud IP](https://mscloudips.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="06755-157">Proof of Concept with exportable firewall rules: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span></span>
    
- <span data-ttu-id="06755-158">No IT Praktyk: [Conversão de RSS](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) e [conversão de XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span><span class="sxs-lookup"><span data-stu-id="06755-158">From IT Praktyk: [RSS conversion](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) and [XML conversion](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span></span>
    
- <span data-ttu-id="06755-159">De Peter Abele: [Baixar](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span><span class="sxs-lookup"><span data-stu-id="06755-159">From Peter Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span></span>
    
- <span data-ttu-id="06755-p113">Use sua análise de rede para determinar qual rede solicita deve ignorar sua infraestrutura de proxy. Os FQDNs mais comuns usados para ignorar os proxies de cliente incluem devido ao volume de tráfego de rede enviados e recebidos desses pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="06755-p113">Use your network analysis to determine which network requests should bypass your proxy infrastructure. The most common FQDNs used to bypass customer proxies include the following due to the volume of network traffic sent and received from these endpoints.</span></span>
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- <span data-ttu-id="06755-162">Certifique-se de que quaisquer solicitações de rede sendo enviadas diretamente à seu firewall tem uma entrada correspondente no firewall lista para permitir que a solicitação para passar de permissões.</span><span class="sxs-lookup"><span data-stu-id="06755-162">Ensure any network requests being sent to your firewall directly have a corresponding entry in the firewall allow list to allow the request to go through.</span></span>
    
## <a name="perimeter-network-integration"></a><span data-ttu-id="06755-163">Integração de rede de perímetro</span><span class="sxs-lookup"><span data-stu-id="06755-163">Perimeter network integration</span></span>
<span data-ttu-id="06755-164"><a name="BKMK_Perimeter"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-164"></span></span>

<span data-ttu-id="06755-165">Você sabia da Microsoft WAN é uma dos backbones maiores no mundo?</span><span class="sxs-lookup"><span data-stu-id="06755-165">Did you know Microsoft's WAN is one of the largest backbones in the world?</span></span>
  
<span data-ttu-id="06755-p114">É definido como true, que esta rede enorme é o que torna o Office 365 e nossos serviços de nuvem que trabalhar independentemente where do mundo que você está. Nossa rede consiste de largura de banda alta, baixa latência, links capaz de failover com milhares de quilômetros de rota de fibra escura pertencente em particular e multi-Terabit conexões entre data centers e borda nós, para facilitar a usar nossos serviços de nuvem.</span><span class="sxs-lookup"><span data-stu-id="06755-p114">It's true, this massive network is what makes Office 365 and our other cloud services work regardless of where in the world you are. Our network consists of high bandwidth, low latency, fail-over capable links with thousands of route miles of privately owned dark fiber, and multi-Terabit connections between datacenters and edge nodes, all to make it easier to use our cloud services.</span></span>
  
<span data-ttu-id="06755-p115">Com uma rede assim, você deseja que os dispositivos da sua organização para se conectar à nossa rede assim que possível. Com mais de 2.500 relacionamentos de correspondência ISP globalmente e 70 pontos de presença, obtendo da sua rede para nosso deve ser contínuo. Ele não pode prejudicar o gastar alguns minutos, certificando-se que o relacionamento de correspondência do seu ISP é o ideal, [Eis alguns exemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de uma boa e não tão boas aos transferências à nossa rede.</span><span class="sxs-lookup"><span data-stu-id="06755-p115">With a network like this, you want your organization's devices to connect to our network as soon as possible. With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
<span data-ttu-id="06755-p116">Você pode manualmente ou configurar automaticamente os dispositivos na sua rede para tratem de solicitações de rede de aplicativos do Office 365, dependendo de seu equipamento. Quais alterações de configuração que você precisa fazer em tratem de tráfego de rede do Office 365 dependerá de seu ambiente. Office 365 rede solicitações poderão se beneficiar configurações de rede que permitem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="06755-p116">You can manually or automatically configure the devices on your network to optimally handle Office 365 application network requests, depending on your equipment. What configuration changes you need to make to optimally handle Office 365 network traffic will depend on your environment. Office 365 network requests may benefit from network configurations that allow the following:</span></span>
  
- <span data-ttu-id="06755-174">Prioridade sobre o tráfego de rede menos crítico.</span><span class="sxs-lookup"><span data-stu-id="06755-174">Priority over less critical network traffic.</span></span>
    
- <span data-ttu-id="06755-p117">O roteamento para uma saída local para evitar backhauling em uma WAN lenta link, beneficiando a latência baixa disponível no Microsoft network. [Aqui está uma boa discussão](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) com base em contratos com clientes.</span><span class="sxs-lookup"><span data-stu-id="06755-p117">Routing to a local egress to avoid backhauling over a slow WAN link while taking advantage of the low latency available on the Microsoft network. [Here's a good discussion](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) based on customer engagements.</span></span> 
    
- <span data-ttu-id="06755-177">Usando o DNS perto de uma saída local para garantir que a solicitação de rede que deixa a saída local chega no local aos Microsoft mais próximo.</span><span class="sxs-lookup"><span data-stu-id="06755-177">Using DNS near a local egress to ensure the network request that leaves the local egress arrives at the nearest Microsoft peering location.</span></span>
    
- <span data-ttu-id="06755-178">Exclusão de profunda inspeção de pacotes ou outros para atender aos requisitos de latência na escala de processamento de pacotes de rede intensiva.</span><span class="sxs-lookup"><span data-stu-id="06755-178">Exclusion from deep packet inspection or other intensive network packet processing to meet latency requirements at scale.</span></span>
    
<span data-ttu-id="06755-p118">Os dispositivos de rede moderno incluem recursos para gerenciar solicitações de rede para aplicativos confiáveis, como o Office 365 diferente genérico, não confiável tráfego da Internet. Com o cenário emergente das soluções SD-WAN, tal diferenciação de tráfego e o caminho de seleção também pode ser executada com o reconhecimento de ao estado em mudança da rede, como o ponto na disponibilidade de tempo, latência ou desempenho dos diversos caminhos de conectividade entre o usuário e a nuvem.</span><span class="sxs-lookup"><span data-stu-id="06755-p118">Modern network devices include capabilities to manage network requests for trusted applications such as Office 365 differently than generic, untrusted Internet traffic. With the emerging landscape of SD-WAN solutions, such differentiation of traffic and path selection can also be performed with awareness of the changing state of the network, such as point in time availability, latency or performance of various connectivity paths between the user and the cloud.</span></span>
  
<span data-ttu-id="06755-181">Consulte [rede e planejamento de migração para o Office 365](network-and-migration-planning.md), [plano para o Office 365 de solução de problemas de desempenho](performance-troubleshooting-plan.md)e [processo de planejamento de implantação para Office 365](deployment-planning-checklist.md) para obter orientação adicional sobre como planejar sua configuração de rede.</span><span class="sxs-lookup"><span data-stu-id="06755-181">See [Network and migration planning for Office 365](network-and-migration-planning.md), [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), and [Deployment planning checklist for Office 365](deployment-planning-checklist.md) for additional guidance on planning your network configuration.</span></span> 
  
### <a name="to-implement-this-scenario"></a><span data-ttu-id="06755-182">Para implementar esse cenário:</span><span class="sxs-lookup"><span data-stu-id="06755-182">To implement this scenario:</span></span>

<span data-ttu-id="06755-p119">Verifique com seu provedor de solução ou serviço de rede, se eles podem usar a URL do Office 365 e definições de IP de XML para facilitar o local (para o usuário), pouca sobrecarga de saída para o Office 365 tráfego de rede, gerenciar sua prioridade em relação a outros aplicativos e ajustar a caminho de rede para conexões do Office 365 em rede Microsoft dependendo alterando as condições de rede. Algumas soluções Baixe e automatizam a definição de URL do Office 365 e IP XMLs em suas pilhas.</span><span class="sxs-lookup"><span data-stu-id="06755-p119">Check with your network solution or service provider if they can use Office 365 URL and IP definitions from XML to facilitate local (to the user), low overhead network egress for Office 365 traffic, manage its priority relative to other applications and adjust the network path for Office 365 connections into Microsoft network depending on changing network conditions. Some solutions download and automate Office 365 URL and IP XMLs definition in their stacks.</span></span>
  
<span data-ttu-id="06755-185">Sempre certifique-se de que a solução implementada tem necessário grau de resiliência, redundância geo apropriada do caminho da rede para tráfego do Office 365 e acomoda mudanças URLs do Office 365 e IPs conforme eles se tornam publicados.</span><span class="sxs-lookup"><span data-stu-id="06755-185">Always ensure that the implemented solution has necessary degree of resiliency, appropriate geo-redundancy of the network path for Office 365 traffic and accommodates changes to Office 365 URLs and IPs as they become published.</span></span>
  
## <a name="web-service"></a><span data-ttu-id="06755-186">Serviço Web</span><span class="sxs-lookup"><span data-stu-id="06755-186">Web service</span></span>
<span data-ttu-id="06755-187"><a name="webservice"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-187"></span></span>

<span data-ttu-id="06755-p120">Para ajudá-lo a identificar e diferenciar o tráfego de rede do Office 365 melhor, um novo web service publica pontos de extremidade do Office 365, tornando mais fácil a avaliar, configurar e manter-se atualizado com as alterações. Esse novo serviço da web (agora na visualização), eventualmente substituirão as listas de pontos de extremidade no artigo [URLs do Office 365 e intervalos de endereços IP](urls-and-ip-address-ranges.md) , juntamente com as versões de RSS e XML desses dados. Esses formato dos dados de ponto de extremidade estão planejados para ser substituídos gradualmente em 2 de outubro de 2018.</span><span class="sxs-lookup"><span data-stu-id="06755-p120">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service (now in preview), will eventually replace the lists of endpoints in the [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) article, along with the RSS and XML versions of that data. These format of endpoint data are planned to be phased out on October 2, 2018.</span></span> 
  
<span data-ttu-id="06755-191">Como um cliente ou um fornecedor de dispositivo de perímetro de rede, você pode construir contra o novo serviço da web baseado em REST para as entradas FQDN e o endereço IP do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06755-191">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries.</span></span>
  
- <span data-ttu-id="06755-192">Para obter a versão mais recente dos intervalos de endereço IP e URLs do Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="06755-192">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="06755-193">Para os dados na página de intervalos de endereço IP para firewalls e servidores proxy e URLs do Office 365, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="06755-193">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="06755-194">Para obter as últimas alterações, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="06755-194">To get the latest changes, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
<span data-ttu-id="06755-195">Como um cliente, você pode usar esse serviço web para:</span><span class="sxs-lookup"><span data-stu-id="06755-195">As a customer, you can use this web service to:</span></span> 
  
- <span data-ttu-id="06755-196">Atualize os scripts do PowerShell para obter dados de ponto de extremidade do Office 365 e modificar qualquer formatação para os dispositivos de redes.</span><span class="sxs-lookup"><span data-stu-id="06755-196">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
    
- <span data-ttu-id="06755-197">Use essas informações para atualizar os arquivos de PAC implantados nos computadores clientes.</span><span class="sxs-lookup"><span data-stu-id="06755-197">Use this information to update PAC files deployed to client computers.</span></span>
    
<span data-ttu-id="06755-198">Como um fornecedor de dispositivo de perímetro de rede, você pode usar esse serviço web para:</span><span class="sxs-lookup"><span data-stu-id="06755-198">As a network perimeter device vendor, you can use this web service to:</span></span> 
  
- <span data-ttu-id="06755-199">Criar e testar o software de dispositivo para baixar a lista de configuração automatizada.</span><span class="sxs-lookup"><span data-stu-id="06755-199">Create and test device software to download the list for automated configuration.</span></span> 
    
- <span data-ttu-id="06755-200">Verificar a versão atual.</span><span class="sxs-lookup"><span data-stu-id="06755-200">Check for the current version.</span></span>
    
- <span data-ttu-id="06755-201">Obtenha as alterações atuais.</span><span class="sxs-lookup"><span data-stu-id="06755-201">Get the current changes.</span></span>
    
<span data-ttu-id="06755-202">As seções a seguir descrevem a visualização desse serviço web, que pode ser alterado ao longo do tempo até que o serviço está disponível no mercado.</span><span class="sxs-lookup"><span data-stu-id="06755-202">The following sections describe the preview of this web service, which might change over time until the service is generally available.</span></span> 
  
<span data-ttu-id="06755-203">Os dados no serviço da web estão atualizados e nós não estiver planejando fazer alterações adicionais para as URLs de serviço web ou retornados esquema de dados antes do lançamento de disponibilidade geral deste serviço da web.</span><span class="sxs-lookup"><span data-stu-id="06755-203">The data on the web service is up to date and we are not planning to make further changes to the web service URLs or returned data schema before the general availability release of this web service.</span></span>
  
<span data-ttu-id="06755-204">Para obter informações adicionais, consulte:</span><span class="sxs-lookup"><span data-stu-id="06755-204">For additional information, see:</span></span>
  
- [<span data-ttu-id="06755-205">Postagem do blog de anúncio no Fórum da comunidade do Office 365 Tech</span><span class="sxs-lookup"><span data-stu-id="06755-205">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [<span data-ttu-id="06755-206">Fórum da comunidade do Office 365 Tech para fazer perguntas sobre o uso dos serviços da web</span><span class="sxs-lookup"><span data-stu-id="06755-206">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a><span data-ttu-id="06755-207">Parâmetros comuns</span><span class="sxs-lookup"><span data-stu-id="06755-207">Common parameters</span></span>

<span data-ttu-id="06755-208">Esses parâmetros são comuns entre todos os métodos de serviço web:</span><span class="sxs-lookup"><span data-stu-id="06755-208">These parameters are common across all the web service methods:</span></span>
  
- <span data-ttu-id="06755-p121">formato de **= CSV | JSON** -parâmetro de cadeia de caracteres de consulta. Por padrão, o formato de dados retornados é JSON. Inclua este parâmetro opcional para retornar os dados no formato de valores separados por vírgula (CSV).</span><span class="sxs-lookup"><span data-stu-id="06755-p121">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span> 
    
- <span data-ttu-id="06755-p122">**ClientRequestId** - parâmetro de cadeia de caracteres de consulta. Um GUID necessário que você gerar para associação de sessão de cliente. Você deve gerar um GUID para cada máquina cliente que chama o serviço web. Não use os GUIDs mostrados nos exemplos a seguir, porque eles podem ser bloqueados pelo serviço web no futuro. O formato GUID é xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, onde x representa um número hexadecimal. Para gerar um GUID, use o comando [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06755-p122">**ClientRequestId** - Query string parameter. A required GUID that you generate for client session association. You should generate a GUID for each client machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span> 
    
### <a name="version-web-method"></a><span data-ttu-id="06755-218">Método da web de versão</span><span class="sxs-lookup"><span data-stu-id="06755-218">Version web method</span></span>

<span data-ttu-id="06755-p123">A Microsoft atualiza o endereço IP do Office 365 e as entradas de FQDN no final de cada mês e ocasionalmente sair ciclo para operacionais ou requisitos de suporte. Os dados para cada instância publicado são atribuídos a um número de versão. O método de web versão permite sondar para a versão mais recente para cada instância de serviço do Office 365. Recomendamos que você verificar a versão diariamente, ou no máximo, por hora.</span><span class="sxs-lookup"><span data-stu-id="06755-p123">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly.</span></span>
  
<span data-ttu-id="06755-223">Há um parâmetro para o método de web de versão:</span><span class="sxs-lookup"><span data-stu-id="06755-223">There is one parameter for the version web method:</span></span>
  
- <span data-ttu-id="06755-p124">**AllVersions = true** -parâmetro de cadeia de caracteres de consulta. Por padrão, a versão retornada é o mais recente. Inclua este parâmetro opcional para solicitar que todas as versões publicadas.</span><span class="sxs-lookup"><span data-stu-id="06755-p124">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span> 
    
- <span data-ttu-id="06755-p125">**Instância** - parâmetro Route. Esse parâmetro opcional especifica a instância para retornar a versão para. Se for omitido, todas as instâncias serão retornadas. Instâncias válidas são: mundial, China, Alemanha, USGovDoD, USGovGCCHigh</span><span class="sxs-lookup"><span data-stu-id="06755-p125">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh</span></span> 
    
<span data-ttu-id="06755-p126">O resultado do método da web versão pode ser um único registro ou uma matriz de registros. Os elementos de cada registro são:</span><span class="sxs-lookup"><span data-stu-id="06755-p126">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>
  
- <span data-ttu-id="06755-233">instância - o nome curto da instância do serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06755-233">instance - The short name of the Office 365 service instance.</span></span>
    
- <span data-ttu-id="06755-234">informações mais recentes - a versão mais recente para pontos de extremidade da instância especificada.</span><span class="sxs-lookup"><span data-stu-id="06755-234">latest - The latest version for endpoints of the specified instance.</span></span>
    
- <span data-ttu-id="06755-p127">versões - uma lista de todas as versões anteriores para a instância especificada. Esse elemento só está incluído se o parâmetro AllVersions for true.</span><span class="sxs-lookup"><span data-stu-id="06755-p127">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>
   
#### <a name="examples"></a><span data-ttu-id="06755-237">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="06755-237">Examples:</span></span>
  
<span data-ttu-id="06755-238">URI de solicitação do exemplo 1: ** <span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="06755-238">Example 1 request URI: **<span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="06755-p128">Esse URI retorna a versão mais recente de cada instância de serviço do Office 365. Resultado de exemplo:</span><span class="sxs-lookup"><span data-stu-id="06755-p128">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>
  
```
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
> <span data-ttu-id="06755-p129">O GUID para o parâmetro ClientRequestID nesses URIs são apenas um exemplo. Para testar o web URIs check-out de serviço, gerar seu próprios GUID. Os GUIDs mostrados nestes exemplos podem ser bloqueados pelo serviço web no futuro.</span><span class="sxs-lookup"><span data-stu-id="06755-p129">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span> 
  
<span data-ttu-id="06755-244">URI de solicitação do exemplo 2: ** <span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="06755-244">Example 2 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="06755-p130">Esse URI retorna a versão mais recente da instância de serviço especificada do Office 365. Resultado de exemplo:</span><span class="sxs-lookup"><span data-stu-id="06755-p130">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="06755-247">URI de solicitação de exemplo 3: ** <span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="06755-247">Example 3 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="06755-p131">Esse URI mostra a saída no formato CSV. Resultado de exemplo:</span><span class="sxs-lookup"><span data-stu-id="06755-p131">This URI shows output in CSV format. Example result:</span></span>
  
```
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="06755-250">URI de solicitação de exemplo 4: ** <span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="06755-250">Example 4 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="06755-p132">Esse URI mostra todas as versões anteriores que foram publicadas para a instância de serviço em todo o mundo do Office 365. Resultado de exemplo:</span><span class="sxs-lookup"><span data-stu-id="06755-p132">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>
  
```
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

### <a name="endpoints-web-method"></a><span data-ttu-id="06755-253">Método da web de pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="06755-253">Endpoints web method</span></span>

<span data-ttu-id="06755-p133">O método de web de pontos de extremidade retorna todos os registros para intervalos de endereços IP e URLs que compõem o serviço Office 365. Parâmetros para o método de web de pontos de extremidade são:</span><span class="sxs-lookup"><span data-stu-id="06755-p133">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. Parameters for the endpoints web method are:</span></span>
  
- <span data-ttu-id="06755-p134">**ServiceAreas** - parâmetro de cadeia de caracteres de consulta. Uma lista separada por vírgulas das áreas de serviço. Itens válidos são comum, Exchange, SharePoint, Skype. Como itens de área comuns do serviço são um pré-requisito para todas as outras áreas de serviço, o serviço web sempre incluirá-los. Se você não incluir esse parâmetro, todas as áreas de serviço serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="06755-p134">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span> 
    
- <span data-ttu-id="06755-p135">**TenantName** - parâmetro de cadeia de caracteres de consulta. Seu nome de Inquilino do Office 365. O serviço web leva seu nome fornecido e o insere em partes do URLs que incluem o nome do locatário. Se você não fornecer um nome de locatário, as partes de URLs têm o caractere curinga (\*).</span><span class="sxs-lookup"><span data-stu-id="06755-p135">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span> 
    
- <span data-ttu-id="06755-p136">**NoIPv6** - parâmetro de cadeia de caracteres de consulta. Defina essa opção para True para endereços IPv6 de exclusão de saída, por exemplo, se você não usar o IPv6 em sua rede.</span><span class="sxs-lookup"><span data-stu-id="06755-p136">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span> 
    
- <span data-ttu-id="06755-p137">**Instância** - parâmetro Route. Este parâmetro obrigatório especifica a instância para retornar os pontos de extremidade. Instâncias válidas são: mundial, China, Alemanha, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="06755-p137">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span> 
    
<span data-ttu-id="06755-p138">O resultado do método da web de pontos de extremidade é uma matriz de registros com cada registro que representa um conjunto de pontos de extremidade. Os elementos para cada registro são:</span><span class="sxs-lookup"><span data-stu-id="06755-p138">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>
  
- <span data-ttu-id="06755-272">ID - o número de identificação imutável do ponto de extremidade definida.</span><span class="sxs-lookup"><span data-stu-id="06755-272">id - The immutable id number of the endpoint set.</span></span>
    
- <span data-ttu-id="06755-273">serviceArea - área de serviço que isso faz parte do: comum, Exchange, SharePoint ou Skype.</span><span class="sxs-lookup"><span data-stu-id="06755-273">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
    
- <span data-ttu-id="06755-p139">URLs - definido de URLs para o ponto de extremidade. Uma matriz de JSON dos registros DNS. Omitidos se deixado em branco.</span><span class="sxs-lookup"><span data-stu-id="06755-p139">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
    
- <span data-ttu-id="06755-p140">tcpPorts - definido de portas TCP para o ponto de extremidade. Todos os elementos de portas são formatados como uma lista separada por vírgulas dos ou intervalos de portas separados por um caractere de travessão (-). Portas se aplicam a todos os endereços IP e todas as URLs nesse conjunto de ponto de extremidade para essa categoria. Omitidos se deixado em branco.</span><span class="sxs-lookup"><span data-stu-id="06755-p140">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
    
- <span data-ttu-id="06755-p141">udpPorts - portas UDP para o IP endereços intervalos nesse conjunto de ponto de extremidade. Omitidos se deixado em branco.</span><span class="sxs-lookup"><span data-stu-id="06755-p141">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
    
- <span data-ttu-id="06755-p142">IPS - intervalos de endereço IP associados a esse ponto de extremidade definido como associados com as portas TCP ou UDP listadas. Omitidos se deixado em branco.</span><span class="sxs-lookup"><span data-stu-id="06755-p142">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. Omitted if blank.</span></span>
    
- <span data-ttu-id="06755-p143">a categoria de conectividade para o ponto de extremidade de categoria - definida. Valores válidos são Optimize, permitir e padrão. Necessário.</span><span class="sxs-lookup"><span data-stu-id="06755-p143">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. Required.</span></span>
    
- <span data-ttu-id="06755-288">expressRoute - True ou False se este conjunto de ponto de extremidade é roteado pela ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="06755-288">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
    
- <span data-ttu-id="06755-p144">obrigatório - True se este conjunto de ponto de extremidade é necessário ter conectividade para o Office 365 ser suportados. Omitidos se for false.</span><span class="sxs-lookup"><span data-stu-id="06755-p144">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. Omitted if false.</span></span>
    
- <span data-ttu-id="06755-p145">Notas de-de pontos de extremidade opcionais, este texto descreve URLs ou funcionalidades do Office 365 que serão ausentes se endereços IP neste ponto final set não pode ser acessado na camada de rede. Omitidos se deixado em branco.</span><span class="sxs-lookup"><span data-stu-id="06755-p145">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>
    
#### <a name="examples"></a><span data-ttu-id="06755-293">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="06755-293">Examples:</span></span>
  
<span data-ttu-id="06755-294">URI de solicitação do exemplo 1: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="06755-294">Example 1 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="06755-p146">Esse URI obtém todos os pontos de extremidade para a instância em todo o mundo do Office 365 para todas as cargas de trabalho. Resultados de exemplo mostrando um trecho da saída:</span><span class="sxs-lookup"><span data-stu-id="06755-p146">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>
  
```
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

<span data-ttu-id="06755-297">Conjuntos de ponto de extremidade adicionais não são incluídos neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="06755-297">Additional endpoint sets are not included in this example.</span></span>
  
<span data-ttu-id="06755-298">URI de solicitação do exemplo 2: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="06755-298">Example 2 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="06755-299">Este exemplo obtém os pontos de extremidade para a instância do Office 365 internacional para Exchange Online e dependências apenas.</span><span class="sxs-lookup"><span data-stu-id="06755-299">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>
  
<span data-ttu-id="06755-300">A saída, por exemplo 2 é semelhante ao exemplo 1, exceto que os resultados não incluirá pontos de extremidade para o SharePoint Online ou Skype para negócios Online.</span><span class="sxs-lookup"><span data-stu-id="06755-300">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>
  
### <a name="changes-web-method"></a><span data-ttu-id="06755-301">Método alterações de web</span><span class="sxs-lookup"><span data-stu-id="06755-301">Changes web method</span></span>

<span data-ttu-id="06755-p147">O método de web alterações retorna as atualizações mais recentes que foram publicadas. Esse é normalmente alterações do mês anterior URLs e intervalos de endereços IP.</span><span class="sxs-lookup"><span data-stu-id="06755-p147">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs.</span></span>
  
> [!NOTE]
> <span data-ttu-id="06755-304">Dados das alterações API são precisos na visualização e devem ser usado para o desenvolvimento e teste somente.</span><span class="sxs-lookup"><span data-stu-id="06755-304">Data from the changes API is accurate in the preview and should be used for development and testing only.</span></span> 
  
<span data-ttu-id="06755-305">O parâmetro para o método de web de alterações é:</span><span class="sxs-lookup"><span data-stu-id="06755-305">The parameter for the changes web method is:</span></span>
  
- <span data-ttu-id="06755-p148">**Versão** - parâmetro de rota de URL necessária. A versão que você tenha implementado no momento, e você deseja ver as alterações, desde que a versão. O formato é YYYYMMDDNN.</span><span class="sxs-lookup"><span data-stu-id="06755-p148">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is YYYYMMDDNN.</span></span> 
    
<span data-ttu-id="06755-p149">O resultado do método da web de alterações é uma matriz de registros com cada registro que representa uma alteração em uma versão específica dos pontos de extremidade. Os elementos para cada registro são:</span><span class="sxs-lookup"><span data-stu-id="06755-p149">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>
  
- <span data-ttu-id="06755-311">ID - a identificação imutável do registro alteração.</span><span class="sxs-lookup"><span data-stu-id="06755-311">id - The immutable id of the change record.</span></span>
    
- <span data-ttu-id="06755-p150">endpointSetId - o ID do ponto de extremidade definido registro é alterado. Necessário.</span><span class="sxs-lookup"><span data-stu-id="06755-p150">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
    
- <span data-ttu-id="06755-314">disposição - isso pode ser de alteração, adicione ou remova e descreve o que fez a alteração para o registro do conjunto de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="06755-314">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
    
- <span data-ttu-id="06755-p151">versão - a versão do ponto de extremidade publicado definida no qual a alteração foi introduzida. Números de versão estão do formato YYYYMMDDNN, onde NN é um número de natural incrementado se houver várias versões deverão ser publicadas em um único dia.</span><span class="sxs-lookup"><span data-stu-id="06755-p151">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format YYYYMMDDNN, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
    
- <span data-ttu-id="06755-p152">Defina um estruturados detalhando os valores anteriores de elementos alterados no ponto de extremidade anterior. Isso não serão incluído para conjuntos de ponto de extremidade recém-adicionado. Inclui tcpPorts, udpPorts, ExpressRoute, categoria, obrigatória, anotações.</span><span class="sxs-lookup"><span data-stu-id="06755-p152">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="06755-p153">Current - um estruturados detalhando valores atualizados de elementos de alterações no endpoinset. Inclui tcpPorts, udpPorts, ExpressRoute, categoria, obrigatória, anotações.</span><span class="sxs-lookup"><span data-stu-id="06755-p153">current - A substructure detailing updated values of changes elements on the endpoinset. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="06755-p154">Add - conjuntos de definir uma estrutura de sub detalhando itens a serem adicionados ao ponto de extremidade. Omitidos se não há nenhuma adições.</span><span class="sxs-lookup"><span data-stu-id="06755-p154">add - A sub structure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
    
  - <span data-ttu-id="06755-324">effectiveDate - define os dados quando as adições estará live no serviço.</span><span class="sxs-lookup"><span data-stu-id="06755-324">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
    
  - <span data-ttu-id="06755-325">IPS - itens a serem adicionados à matriz ips.</span><span class="sxs-lookup"><span data-stu-id="06755-325">ips - Items to be added to the ips array.</span></span>
    
  - <span data-ttu-id="06755-326">URLs-itens a serem adicionados à matriz urls.</span><span class="sxs-lookup"><span data-stu-id="06755-326">urls- Items to be added to the urls array.</span></span>
    
- <span data-ttu-id="06755-p155">Remova - um estruturados detalhando itens a serem removidos do conjunto de ponto de extremidade. Omitidos se não houver nenhuma remoções.</span><span class="sxs-lookup"><span data-stu-id="06755-p155">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
    
  - <span data-ttu-id="06755-329">IPS - itens a serem removidos da matriz ips.</span><span class="sxs-lookup"><span data-stu-id="06755-329">ips - Items to be removed from the ips array.</span></span>
    
  - <span data-ttu-id="06755-330">Itens de URLs a ser removido da matriz urls.</span><span class="sxs-lookup"><span data-stu-id="06755-330">urls- Items to be removed from the urls array.</span></span>
    
 <span data-ttu-id="06755-331">**Exemplos:**</span><span class="sxs-lookup"><span data-stu-id="06755-331">**Examples:**</span></span>
  
<span data-ttu-id="06755-332">URI de solicitação do exemplo 1: ** <span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="06755-332">Example 1 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="06755-p156">Isso solicita todas as alterações anteriores para a instância de serviço em todo o mundo do Office 365. Resultado de exemplo:</span><span class="sxs-lookup"><span data-stu-id="06755-p156">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>
  
```
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

<span data-ttu-id="06755-335">URI de solicitação do exemplo 2: ** <span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="06755-335">Example 2 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="06755-p157">Isso solicita alterações desde a versão especificada para a instância do Office 365 internacional. Nesse caso, a versão especificada é o mais recente. Resultado de exemplo:</span><span class="sxs-lookup"><span data-stu-id="06755-p157">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>
  
```
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

### <a name="example-powershell-script"></a><span data-ttu-id="06755-339">Script do PowerShell de exemplo</span><span class="sxs-lookup"><span data-stu-id="06755-339">Example PowerShell Script</span></span>

<span data-ttu-id="06755-p158">Aqui está um script do PowerShell que podem ser executadas para ver se existem ações que você precisa tomar para dados atualizados. Esse script verifica o número de versão para os Office 365 internacional pontos de extremidade de instância. Quando houver uma alteração, baixa os pontos de extremidade e filtros para os pontos de extremidade de categoria "Permitir" e "Otimizar". Ele também usa um ClientRequestId exclusivo entre várias chamadas e salva a versão mais recente encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se uma atualização de versão.</span><span class="sxs-lookup"><span data-stu-id="06755-p158">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
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

### <a name="example-python-script"></a><span data-ttu-id="06755-345">Exemplo de Script Python</span><span class="sxs-lookup"><span data-stu-id="06755-345">Example Python Script</span></span>

<span data-ttu-id="06755-p159">Aqui está um script de Python, testado com Python 3.6.3 no Windows 10, que pode ser executado para ver se existem ações que você precisa tomar para dados atualizados. Esse script verifica o número de versão para os Office 365 internacional pontos de extremidade de instância. Quando houver uma alteração, baixa os pontos de extremidade e filtros para os pontos de extremidade de categoria "Permitir" e "Otimizar". Ele também usa um ClientRequestId exclusivo entre várias chamadas e salva a versão mais recente encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se uma atualização de versão.</span><span class="sxs-lookup"><span data-stu-id="06755-p159">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
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

### <a name="web-service-interface-versioning"></a><span data-ttu-id="06755-351">Controle de versão de interface de serviço Web</span><span class="sxs-lookup"><span data-stu-id="06755-351">Web Service interface versioning</span></span>

<span data-ttu-id="06755-p160">Atualizações para os parâmetros ou resultados para esses métodos de serviço da web podem ser necessárias no futuro. Depois que a versão de disponibilidade geral desses serviços da web é publicada, a Microsoft fará esforços razoáveis para fornecer prévio de materiais atualizações para o serviço web. Quando a Microsoft acredita que uma atualização exigirá mudanças para os clientes usando o serviço web, o Microsoft manterá a versão anterior (versão anterior) do serviço web disponível para pelo menos doze (12) meses após o lançamento da nova versão. Os clientes que não atualize durante esse tempo podem ser capaz de acessar o serviço web e seus métodos. Os clientes devem garantir que os clientes do serviço web continuam trabalhando sem erro, se as seguintes alterações são feitas na assinatura de interface de serviço web:</span><span class="sxs-lookup"><span data-stu-id="06755-p160">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>
  
- <span data-ttu-id="06755-357">Adicionando um novo parâmetro opcional para um método web existente que não tem a serem fornecidos por clientes mais antigos e não afeta o resultado recebe um cliente mais antigo.</span><span class="sxs-lookup"><span data-stu-id="06755-357">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
    
- <span data-ttu-id="06755-358">Adicionando um novo atributo nomeado em um dos itens do restante de resposta ou colunas adicionais à resposta CSV.</span><span class="sxs-lookup"><span data-stu-id="06755-358">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
    
- <span data-ttu-id="06755-359">Adicionando um novo método de web com um novo nome não é chamado pelos clientes mais antigos.</span><span class="sxs-lookup"><span data-stu-id="06755-359">Adding a new web method with a new name that is not called by the older clients.</span></span>
    
## <a name="faq"></a><span data-ttu-id="06755-360">Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="06755-360">FAQ</span></span>

<span data-ttu-id="06755-361">Perguntas sobre o administrador de perguntas frequentes sobre conectividade:</span><span class="sxs-lookup"><span data-stu-id="06755-361">Frequently-asked administrator questions about connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="06755-362">Como faço para enviar uma pergunta?</span><span class="sxs-lookup"><span data-stu-id="06755-362">How do I submit a question?</span></span>

<span data-ttu-id="06755-p161">Clique no link na parte inferior para indicar se o artigo foi útil ou não e enviar perguntas adicionais. Podemos monitorar o feedback e atualizar as perguntas aqui com perguntas frequentes.</span><span class="sxs-lookup"><span data-stu-id="06755-p161">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="when-is-the-xml-file-updated"></a><span data-ttu-id="06755-365">Quando o arquivo XML é atualizado?</span><span class="sxs-lookup"><span data-stu-id="06755-365">When is the XML file updated?</span></span>

<span data-ttu-id="06755-p162">Quando novos pontos de extremidade são anunciados, normalmente há um buffer de 30 + dia antes que eles são eficazes e solicitações da rede começam a passando a eles. Esse buffer é para garantir que os clientes e parceiros terá a oportunidade de atualizar seus sistemas. FQDN e IP prefix adições e remoções são processadas no arquivo XML, ao mesmo tempo como o comunicado, que significa que um novo FQDN será no arquivo XML de 30 dias antes do uso. Como podemos parar de enviar solicitações da rede aos pontos de extremidade que podemos está removendo antes da anunciando sua remoção, quando removemos o ponto de extremidade do XML ao mesmo tempo que o comunicado já é não utilizado.</span><span class="sxs-lookup"><span data-stu-id="06755-p162">When new endpoints are announced, there is usually a 30+ day buffer before they are effective and network requests begin going to them. This buffer is to ensure customers and partners have an opportunity to update their systems. FQDN and IP prefix additions and removals are processed in the XML file at the same time as the announcement, meaning a new FQDN will be in the XML file 30 days before use. Since we stop sending network requests to endpoints we're removing prior to announcing their removal, when we remove the endpoint from the XML at the same time as the announcement it is already unused.</span></span>
  
### <a name="how-can-i-be-notified-of-changes"></a><span data-ttu-id="06755-370">Como posso ser notificado das alterações?</span><span class="sxs-lookup"><span data-stu-id="06755-370">How can I be notified of changes?</span></span>
<span data-ttu-id="06755-371"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-371"></span></span>

<span data-ttu-id="06755-p163">Pontos de extremidade do Office 365 são publicados no final de cada mês com o aviso de 30 dias. Ocasionalmente, a alteração ocorrerá mais de uma vez por mês ou com mais curtos períodos de aviso. Quando é adicionado a um ponto de extremidade, a data efetiva listada no [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) é a data após o qual as solicitações de rede serão enviadas ao ponto de extremidade. Se estiver familiarizado com RSS, aqui está como [Inscreva-se via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) ou você pode [ter o RSS feed atualizações enviadas para você](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span><span class="sxs-lookup"><span data-stu-id="06755-p163">Office 365 endpoints are published at the end of each month with 30 days notice. Occasionally changes will occur more than once a month or with shorter notice periods. When an endpoint is added, the effective date listed in the [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) is the date after which network requests will be sent to the endpoint. If you're new to RSS, here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>
  
### <a name="how-do-i-read-the-rss-change-log"></a><span data-ttu-id="06755-376">Como ler que o RSS de log de alteração?</span><span class="sxs-lookup"><span data-stu-id="06755-376">How do I read the RSS change log?</span></span>
<span data-ttu-id="06755-377"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-377"></span></span>

<span data-ttu-id="06755-p164">Depois que você se inscrever no RSS feed, você pode analisar as informações sozinho ou com um script. A tabela a seguir descreve o formato do RSS feed o tornam mais fácil.</span><span class="sxs-lookup"><span data-stu-id="06755-p164">After you subscribe to the RSS feed, you can parse the information yourself or with a script. The following table describes the format of the RSS feed o make it easier.</span></span>
  
|<span data-ttu-id="06755-380">**Seção**</span><span class="sxs-lookup"><span data-stu-id="06755-380">**Section**</span></span>|<span data-ttu-id="06755-381">**Parte 1**</span><span class="sxs-lookup"><span data-stu-id="06755-381">**Part 1**</span></span>|<span data-ttu-id="06755-382">**Parte 2**</span><span class="sxs-lookup"><span data-stu-id="06755-382">**Part 2**</span></span>|<span data-ttu-id="06755-383">**Parte 3**</span><span class="sxs-lookup"><span data-stu-id="06755-383">**Part 3**</span></span>|<span data-ttu-id="06755-384">**Parte 4**</span><span class="sxs-lookup"><span data-stu-id="06755-384">**Part 4**</span></span>|<span data-ttu-id="06755-385">**Parte 5**</span><span class="sxs-lookup"><span data-stu-id="06755-385">**Part 5**</span></span>|<span data-ttu-id="06755-386">**Parte 6**</span><span class="sxs-lookup"><span data-stu-id="06755-386">**Part 6**</span></span>|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="06755-387">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="06755-387">**Description**</span></span> <br/> |<span data-ttu-id="06755-388">Contagem</span><span class="sxs-lookup"><span data-stu-id="06755-388">Count</span></span>  <br/> |<span data-ttu-id="06755-389">Data após o qual você pode esperar solicitações sejam enviadas para o ponto de extremidade de rede.</span><span class="sxs-lookup"><span data-stu-id="06755-389">Date after which you can expect network requests to be sent to the endpoint.</span></span>  <br/> |<span data-ttu-id="06755-390">Descrição básica do recurso ou serviço que exija o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="06755-390">Basic description of the feature or service that requires the endpoint.</span></span>  <br/> |<span data-ttu-id="06755-391">Você pode se conectar a esse ponto de extremidade em um circuito ExpressRoute além da internet?</span><span class="sxs-lookup"><span data-stu-id="06755-391">Can you connect to this endpoint on an ExpressRoute Circuit in addition to the internet?</span></span>  <br/> |<span data-ttu-id="06755-392">**Sim** — você pode se conectar a esse ponto de extremidade na internet e ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="06755-392">**Yes** - you can connect to this endpoint on both the internet and ExpressRoute.</span></span>  <br/> <span data-ttu-id="06755-393">**Não** — você só pode se conectar a este ponto de extremidade na internet.</span><span class="sxs-lookup"><span data-stu-id="06755-393">**No** - you can only connect to this endpoint on the internet.</span></span>  <br/> |<span data-ttu-id="06755-394">O intervalo IP ou FQDN que está sendo adicionado ou removido de destino.</span><span class="sxs-lookup"><span data-stu-id="06755-394">The destination FQDN or IP range being added or removed.</span></span>  <br/> |
|<span data-ttu-id="06755-395">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="06755-395">**Example**</span></span> <br/> |<span data-ttu-id="06755-396">1 /</span><span class="sxs-lookup"><span data-stu-id="06755-396">1/</span></span>  <br/> |<span data-ttu-id="06755-397">[Efetivo xx/xx/xxx.</span><span class="sxs-lookup"><span data-stu-id="06755-397">[Effective xx/xx/xxx.</span></span>  <br/> |<span data-ttu-id="06755-398">Obrigatório: \<descrição\>.</span><span class="sxs-lookup"><span data-stu-id="06755-398">Required: \<description\>.</span></span>  <br/> |<span data-ttu-id="06755-399">ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="06755-399">ExpressRoute:</span></span>  <br/> |<span data-ttu-id="06755-400">\<Sim/não\>.</span><span class="sxs-lookup"><span data-stu-id="06755-400">\<Yes/No\>.</span></span>  <br/> |<span data-ttu-id="06755-401">\<FQDN/IP\>],</span><span class="sxs-lookup"><span data-stu-id="06755-401">\<FQDN/IP\>],</span></span>  <br/> |
   
<span data-ttu-id="06755-402">Algumas outras coisas observar, cada entrada tem um conjunto comum de delimitadores:</span><span class="sxs-lookup"><span data-stu-id="06755-402">A couple other things to note, every entry has a common set of delimiters:</span></span>
  
- <span data-ttu-id="06755-403">**/**-Após a contagem</span><span class="sxs-lookup"><span data-stu-id="06755-403">**/** - after the count</span></span> 
    
- <span data-ttu-id="06755-404">**[-** para indicar a entrada para a contagem</span><span class="sxs-lookup"><span data-stu-id="06755-404">**[** - to indicate the entry for the count</span></span> 
    
- <span data-ttu-id="06755-p165">**.** -usados entre cada seção distinta da entrada</span><span class="sxs-lookup"><span data-stu-id="06755-p165">**.** - used in between each distinct section of the entry</span></span> 
    
- <span data-ttu-id="06755-407">**],** - para indicar o final de uma única entrada</span><span class="sxs-lookup"><span data-stu-id="06755-407">**],** - to indicate the end of a single entry</span></span> 
    
- <span data-ttu-id="06755-p166">**].** -Para indicar o final de todas as entradas</span><span class="sxs-lookup"><span data-stu-id="06755-p166">**].** - To indicate the end of all the entries</span></span> 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="06755-410">Como faço para determinar o local do meu locatário?</span><span class="sxs-lookup"><span data-stu-id="06755-410">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="06755-411">**Local de Inquilino** é melhor determinado usando nosso [Mapear datacenter](https://o365datacentermap.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="06755-411">**Tenant location** is best determined using our [datacenter map](https://o365datacentermap.azurewebsites.net/).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="06755-412">Sou eu correspondência apropriadamente com Microsoft?</span><span class="sxs-lookup"><span data-stu-id="06755-412">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="06755-413">**Peering locais** são descritos em mais detalhes na [correspondência com a Microsoft](https://www.microsoft.com/peering).</span><span class="sxs-lookup"><span data-stu-id="06755-413">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="06755-p167">Com mais de 2.500 relacionamentos de correspondência ISP globalmente e 70 pontos de presença, obtendo da sua rede para nosso deve ser contínuo. Ele não pode prejudicar o gastar alguns minutos, certificando-se que o relacionamento de correspondência do seu ISP é o ideal, [Eis alguns exemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de uma boa e não tão boas aos transferências à nossa rede.</span><span class="sxs-lookup"><span data-stu-id="06755-p167">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a><span data-ttu-id="06755-416">Como determinar quais endereços IP para aceitar o ExpressRoute?</span><span class="sxs-lookup"><span data-stu-id="06755-416">How do I determine which IP addresses to accept over ExpressRoute?</span></span>

 <span data-ttu-id="06755-417">**Rotas ExpressRoute aceitos** são definidos por [intervalos IP da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602) e o Office 365 [comunidades BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)específico.</span><span class="sxs-lookup"><span data-stu-id="06755-417">**Accepted ExpressRoute routes** are defined by [Microsoft's IP ranges](https://www.microsoft.com/download/details.aspx?id=53602) and the specific Office 365 [BGP communities](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span></span>
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a><span data-ttu-id="06755-418">Como faço para determinar quais pontos de extremidade que eu preciso?</span><span class="sxs-lookup"><span data-stu-id="06755-418">How do I determine which endpoints I need?</span></span>

<span data-ttu-id="06755-p168">Regularmente adicionamos novos recursos e serviços para o Office 365 suite, expandindo o cenário de conectividade. Se você estiver inscrito ao E3 ou SKU E5, de maneira simples de pensar a lista de pontos de extremidade é que você precisa todos eles para obter a funcionalidade total para o pacote. Se você não se inscreveu para qualquer um desses SKUs a diferença é mínima em termos de número de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="06755-p168">We regularly add new features and services to the Office 365 suite, expanding the connectivity landscape. If you're subscribed to the E3 or E5 SKU, the simple way to think about the list of endpoints is that you need all of them to get full functionality for the suite. If you aren't subscribed to either of these SKUs the difference is minimal in terms of the number of endpoints.</span></span>
  
<span data-ttu-id="06755-422">Leia os [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md) para obter mais informações sobre categorias de ponto de extremidade do Office 365 e entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível.</span><span class="sxs-lookup"><span data-stu-id="06755-422">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
<span data-ttu-id="06755-p169">A imagem abaixo, você pode ver um exemplo de uma parte da tabela FQDN na seção Office Online. As linhas são organizadas por recurso e diferenças na conectividade. As duas primeiras linhas indicam Office Online depende os pontos de extremidade marcados necessário na autenticação do Office 365 e a identidade e portal e seções compartilhadas. Isso é típico de um serviço no Office 365 depender esses serviços compartilhados. A terceira linha indica os computadores cliente devem ser capazes de alcançar \*. officeapps.live.com para usar o Office Online e a quarta linha indica computadores também devem ser capazes de alcançar \*. cdn.office.net para usar o Office Online.</span><span class="sxs-lookup"><span data-stu-id="06755-p169">In the image below, you can see an example from a portion of the FQDN table in the Office Online section. The rows are organized by feature and differences in connectivity. The first two rows indicate Office Online relies on the endpoints marked Required in the Office 365 Authentication and Identity and portal and shared sections. This is typical for a service within Office 365 to rely on these shared services. The third row indicates client computers must be able to reach \*.officeapps.live.com to use Office Online and the fourth row indicates computers must also be able to reach \*.cdn.office.net to use Office Online.</span></span>
  
<span data-ttu-id="06755-428">Embora ambos linha três e quatro são necessários para usar o Office Online, tiver sido separadas para indicar que o destino é diferente:</span><span class="sxs-lookup"><span data-stu-id="06755-428">Even though both row three and four are required to use Office Online, they've been separated to indicate the destination is different:</span></span>
  
1. <span data-ttu-id="06755-429">\*. officeapps.live.com não representa uma CDN, solicitações de significado para esse namespace serão levado diretamente para um datacenter da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="06755-429">\*.officeapps.live.com does not represent a CDN, meaning requests to this namespace will go directly to a Microsoft datacenter.</span></span>
    
2. <span data-ttu-id="06755-430">\*. officeapps.live.com pode ser acessada em circuitos ExpressRoute usando o Microsoft Peering.</span><span class="sxs-lookup"><span data-stu-id="06755-430">\*.officeapps.live.com is accessible on ExpressRoute circuits using Microsoft Peering.</span></span>
    
3. <span data-ttu-id="06755-431">Os endereços IP associados com o Office Online e \*. officeapps.live.com podem ser encontradas seguindo este link.</span><span class="sxs-lookup"><span data-stu-id="06755-431">The IP addresses associated with Office Online and \*.officeapps.live.com can be found by following this link.</span></span>
    
4. <span data-ttu-id="06755-432">\*. cdn.office.net representa uma CDN hospedada pelo Akamai, solicitações de significado para esse namespace serão encaminhadas para um datacenter Akamai.</span><span class="sxs-lookup"><span data-stu-id="06755-432">\*.cdn.office.net represents a CDN hosted by Akamai, meaning requests to this namespace will go to an Akamai datacenter.</span></span>
    
5. <span data-ttu-id="06755-433">\*. cdn.office.net não está acessível em circuitos ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="06755-433">\*.cdn.office.net is not accessible on ExpressRoute circuits.</span></span>
    
6. <span data-ttu-id="06755-434">Os endereços IP associados com o Office Online e \*. cdn.office.net não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="06755-434">The IP addresses associated with Office Online and \*.cdn.office.net are not available.</span></span>
    
![Captura de tela da página pontos de extremidade](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="06755-436">Posso ver as solicitações de rede para os endereços IP não está na lista publicada, preciso para fornecer acesso a eles?</span><span class="sxs-lookup"><span data-stu-id="06755-436">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="06755-437"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-437"></span></span>

<span data-ttu-id="06755-p170">Fornecemos apenas endereços IP para os servidores do Office 365 que você deve rotear diretamente pela Internet ou ExpressRoute. Isso não é uma lista abrangente de todos os endereços IP, para que você verá as solicitações de rede. Você verá as solicitações de rede à Microsoft e endereços IP pertencentes, não publicados, softwares de terceiros. Esses endereços IP dinamicamente são gerados ou gerenciados de forma que impede que o aviso em tempo hábil quando eles são alterados. Se seu firewall não pode permitir o acesso com base nos FQDNs para essas solicitações da rede, use um arquivo PAC ou WPAD para gerenciar as solicitações.</span><span class="sxs-lookup"><span data-stu-id="06755-p170">We only provide IP addresses for the Office 365 servers you should route directly to over the Internet or ExpressRoute. This isn't a comprehensive list of all IP addresses you'll see network requests for. You'll see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="06755-443">Ver que um IP associado ao que você deseja obter mais informações no Office 365?</span><span class="sxs-lookup"><span data-stu-id="06755-443">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="06755-444">Verifique se o endereço IP está incluído em um intervalo de publicado maior usando uma [Calculadora CIDR](http://jodies.de/ipcalc).</span><span class="sxs-lookup"><span data-stu-id="06755-444">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
    
2. <span data-ttu-id="06755-p171">Consulte se um parceiro possui o IP com uma [consulta whois](https://dnsquery.org/). Se for Microsoft pertencente, talvez seja um parceiro interno.</span><span class="sxs-lookup"><span data-stu-id="06755-p171">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
    
3. <span data-ttu-id="06755-p172">Verifique o certificado, em um navegador conectar ao endereço IP usando *HTTPS://\<IP_ADDRESS\> * , verifique os domínios listados no certificado para entender quais domínios associados com o endereço IP. Se for um endereço IP de propriedade da Microsoft e não está na lista de endereços IP do Office 365, provavelmente é o endereço IP é associado um Microsoft CDN como *MSOCDN.NET* ou outro domínio Microsoft sem informações publicadas de IP. Se você encontrar que o domínio no certificado é uma onde podemos declaração listar o endereço IP, informe-nos.</span><span class="sxs-lookup"><span data-stu-id="06755-p172">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span> 
    
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="06755-450">Por que vejo nomes como nsatc.net ou akadns.net em nomes de domínio Microsoft?</span><span class="sxs-lookup"><span data-stu-id="06755-450">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="06755-451"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-451"></span></span>

<span data-ttu-id="06755-p173">Office 365 e outros serviços da Microsoft usam vários serviços de terceiros, como Akamai e MarkMonitor para melhorar a experiência do Office 365. Para manter oferecendo a melhor experiência possível, podemos alterar esses serviços no futuro. Ao fazer isso, muitas vezes Publicamos o registro CNAME que aponta para um terceiro domínio pertencente, um registro ou endereço IP. Domínios de terceiros podem hospedar o conteúdo, como uma CDN, ou eles podem hospedar um serviço, como um serviço de gerenciamento de tráfego geográficas. Quando você vir conexões com esses terceiros, eles estão no formato de um redirecionamento ou referência, não uma solicitação inicial do cliente. Alguns clientes precisam garantir a essa forma de referência e passar sem adicionar explicitamente que longa lista de serviços de terceiros FQDNs potenciais pode usar o redirecionamento será permitido.</span><span class="sxs-lookup"><span data-stu-id="06755-p173">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="06755-p174">Lista de serviços está sujeita a alterações a qualquer momento. Alguns dos serviços atualmente em uso incluem:</span><span class="sxs-lookup"><span data-stu-id="06755-p174">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="06755-p175">[MarkMonitor](https://www.markmonitor.com/) está em uso quando você vir solicitações que incluem \* \*. nsatc.net\* . Este serviço oferece proteção de nome de domínio e monitoramento para proteger contra comportamentos mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="06755-p175">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span> 
  
<span data-ttu-id="06755-p176">[ExactTarget](https://www.marketingcloud.com/) está em uso quando você vir solicitações para \* \*. exacttarget.com\* . Esse serviço fornece contra comportamento mal intencionado de monitoramento e gerenciamento do link de email.</span><span class="sxs-lookup"><span data-stu-id="06755-p176">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span> 
  
<span data-ttu-id="06755-p177">[Akamai](https://www.akamai.com/) está em uso quando você vir solicitações que incluem um dos seguintes FQDNs. Este serviço oferece geo-DNS e serviços de rede de fornecimento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="06755-p177">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span> 
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net

```

### <a name="what-are-the-three-types-of-office-365-endpoints"></a><span data-ttu-id="06755-466">Quais são os três tipos de pontos de extremidade do Office 365?</span><span class="sxs-lookup"><span data-stu-id="06755-466">What are the three types of Office 365 endpoints?</span></span>
<span data-ttu-id="06755-467"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-467"></span></span>

- <span data-ttu-id="06755-p178">Você pode se conectar aos serviços de terceiros para recuperar serviços básicos da internet, como pesquisas de DNS e recuperação de conteúdo CDN. Você também pode conectar aos serviços de terceiros para integrações como incorporação de vídeos do YouTube em seus blocos de anotações do OneNote.</span><span class="sxs-lookup"><span data-stu-id="06755-p178">You connect to third-party services to retrieve basic internet services such as DNS lookups and CDN content retrieval. You also connect to third-party services for integrations such as incorporating YouTube videos in your OneNote notebooks.</span></span>
    
- <span data-ttu-id="06755-p179">Conecte-se aos serviços secundários hospedado e execute pela Microsoft, como nós da borda que permitem que sua solicitação de rede inserir a rede global da Microsoft no local mais próximo da internet para seu computador. Como a rede terceira maior do planeta, isso melhora a sua experiência de conectividade. Você também pode conectar aos serviços do Microsoft Azure como Azure Media Services, que são usados por uma variedade de serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="06755-p179">You connect to secondary services hosted and run by Microsoft such as edge nodes that enable your network request to enter Microsoft's global network at the closest internet location to your computer. As the third largest network on the planet, this improves your connectivity experience. You also connect to Microsoft Azure services such as Azure Media Services which are used by a variety of Office 365 services.</span></span>
    
- <span data-ttu-id="06755-p180">A conexão com serviços do Office 365 principais, como o servidor de caixa de correio Exchange Online ou o Skype para servidor Business Online onde os seus dados exclusivos e proprietários residem. Você pode se conectar aos serviços do Office 365 principais por endereço IP ou FQDN e usar ExpressRoute circuitos ou internet. Você só pode se conectar ao terceiro e serviços secundários usando FQDNs em um circuito de internet.</span><span class="sxs-lookup"><span data-stu-id="06755-p180">You connect to primary Office 365 services such as the Exchange Online mailbox server or the Skype for Business Online server where your unique and proprietary data lives. You can connect to the primary Office 365 services by FQDN or IP address and use internet or ExpressRoute circuits. You can only connect to the third party and secondary services using FQDNs on an internet circuit.</span></span>
    
<span data-ttu-id="06755-p181">O diagrama a seguir mostra as diferenças entre essas áreas de serviço. Neste diagrama, a rede de local do cliente na parte inferior esquerda tem vários dispositivos de rede para auxiliar no gerenciamento de conectividade de rede. Configurações como esse são comuns para clientes empresariais. Se sua rede tem somente um firewall entre os computadores cliente e a internet, que é suportado, bem, e você vai querer Certifique-se de que seu firewall pode suportar FQDNs e curingas nas regras de lista Permitir.</span><span class="sxs-lookup"><span data-stu-id="06755-p181">The following diagram shows the differences between these service areas. In this diagram, the customer on-premises network in the lower left has multiple network devices to assist in managing network connectivity. Configurations like this one are common for enterprise customers. If your network only has a firewall between your client computers and the internet, that's supported as well, and you'll want to ensure your firewall can support FQDNs and wildcards in the allow list rules.</span></span>
  
<span data-ttu-id="06755-480">Leia os [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md) para obter mais informações sobre categorias de ponto de extremidade do Office 365 e entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível.</span><span class="sxs-lookup"><span data-stu-id="06755-480">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
![Mostra os três tipos diferentes de pontos de extremidade de rede ao usar o Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a><span data-ttu-id="06755-482">Não consigo ou não desejar usar qualquer serviço de terceiros</span><span class="sxs-lookup"><span data-stu-id="06755-482">I can't or don't want to use any third-party service</span></span>
<span data-ttu-id="06755-483"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-483"></span></span>

<span data-ttu-id="06755-p182">Office 365 é um conjunto de serviços incluído funcione pela internet, confiabilidade e disponibilidade promessas baseiam-se no muitos serviços de internet padrão que está sendo disponíveis. Por exemplo, os serviços de internet padrão como DNS, CRL e CDNs devem ser acessíveis para usar o Office 365 assim como eles devem ser alcançados para usar os serviços de internet mais modernos.</span><span class="sxs-lookup"><span data-stu-id="06755-p182">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>
  
<span data-ttu-id="06755-p183">Além desses serviços básicos da internet, existem serviços de terceiros que são usados somente para integrar funcionalidade. Por exemplo, usar Giphy.com dentro Teams Microsoft permite que os clientes incluem perfeitamente Gifs dentro de equipes. Da mesma forma, YouTube e Flickr são os serviços de terceiros que são usados para integrar perfeitamente vídeo e imagens em clientes do Office da internet. Enquanto elas são necessárias para integração, eles estão marcados como opcionais no artigo Office 365 pontos de extremidade que significa que a funcionalidade principal do serviço continuarão a funcionar se o ponto de extremidade não está acessível.</span><span class="sxs-lookup"><span data-stu-id="06755-p183">In addition to these basic internet services, there are third-party services that are only used to integrate functionality. For example, using Giphy.com within Microsoft Teams allows customers to seamlessly include Gifs within Teams. Similarly, YouTube and Flickr are third-party services that are used to seamlessly integrate video and images into Office clients from the internet. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible.</span></span>
  
<span data-ttu-id="06755-490">Se você estiver tentando usar o Office 365 e está descobrindo serviços de terceiros não estão acessíveis você desejará [Certifique-se de que todos os FQDNs marcados obrigatório ou opcional neste artigo são permitidos por meio do proxy e firewall](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="06755-490">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a><span data-ttu-id="06755-491">Não consigo ou não deseja usar todos os serviços secundários</span><span class="sxs-lookup"><span data-stu-id="06755-491">I can't or don't want to use any secondary services</span></span>
<span data-ttu-id="06755-492"><a name="bkmk_secondary"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-492"></span></span>

<span data-ttu-id="06755-p184">Secundário são serviços da Microsoft que não estão dentro do controle do Office 365. Estas são as coisas como a rede de borda, Azure Media Services e redes de distribuição de conteúdo do Windows Azure. Estes são necessários para usar o Office 365 e devem ser alcançados.</span><span class="sxs-lookup"><span data-stu-id="06755-p184">Secondary services are Microsoft services that don't fall within Office 365 control. These are things like the edge network, Azure Media Services, and Azure Content Delivery Networks. These are all required to use Office 365 and must be reachable.</span></span>
  
<span data-ttu-id="06755-496">Se você estiver tentando usar o Office 365 e está descobrindo serviços de terceiros não estão acessíveis você desejará [Certifique-se de que todos os FQDNs marcados obrigatório ou opcional neste artigo são permitidos por meio do proxy e firewall](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="06755-496">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="06755-497">Como bloquear o acesso aos serviços de consumidor da Microsoft?</span><span class="sxs-lookup"><span data-stu-id="06755-497">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="06755-498"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="06755-498"></span></span>

<span data-ttu-id="06755-p185">Restringir o acesso aos nossos serviços de consumidor deve ser feita por seu próprio risco, a maneira confiável apenas aos serviços do consumidor de bloqueio é para restringir o acesso a *login.live.com* FQDN. Esse FQDN é utilizado por um amplo conjunto de serviços, incluindo serviços de não-consumidor como MSDN, TechNet e outros. Restringindo o acesso a esse FQDN pode resultar na necessidade de também incluem exceções à regra para solicitações de rede associados a esses serviços.</span><span class="sxs-lookup"><span data-stu-id="06755-p185">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span> 
  
<span data-ttu-id="06755-502">Tenha em mente que bloqueando o acesso aos serviços do consumidor do Microsoft sozinhos não impedir a capacidade para alguém em sua rede às informações de exfiltrate usando um locatário do Office 365 ou outro serviço.</span><span class="sxs-lookup"><span data-stu-id="06755-502">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="06755-503">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="06755-503">Related Topics</span></span>

[<span data-ttu-id="06755-504">Intervalos de IP de Datacenter Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="06755-504">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="06755-505">Espaço IP público da Microsoft</span><span class="sxs-lookup"><span data-stu-id="06755-505">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="06755-506">Requisitos de infraestrutura de rede da Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="06755-506">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="06755-507">ExpressRoute e no power BI</span><span class="sxs-lookup"><span data-stu-id="06755-507">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="06755-508">URLs e intervalos de endereços IP do Office 365</span><span class="sxs-lookup"><span data-stu-id="06755-508">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="06755-509">Como gerenciar o ExpressRoute para a conectividade do Office 365</span><span class="sxs-lookup"><span data-stu-id="06755-509">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="06755-510">Princípios de conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="06755-510">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
  

