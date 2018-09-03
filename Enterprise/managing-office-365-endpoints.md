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
# <a name="managing-office-365-endpoints"></a>Gerenciando pontos de extremidade do Office 365

## <a name="office-365-network-connectivity"></a>Conectividade de rede do Office 365

 Conexões para o Office 365 consistem em alto volume, solicitações de rede de perímetro que executar melhor quando eles estiver feitos ao longo de uma saída de baixa latência está perto do usuário. Algumas conexões do Office 365 podem se beneficiar de otimizar a conexão. 
  
1. Certifique-se de seu firewall permitir listas permitem conectividade aos pontos de extremidade do Office 365.
    
2. Use sua infraestrutura de proxy para permitir a conectividade à Internet para o caractere curinga e destinos de publicação cancelados.
    
3. Manter uma configuração de rede de perímetro ideal.
    
4. [Verifique se você estiver recebendo a melhor conectividade](https://aka.ms/o365perfprinciples).
    
5. Leia os [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md) para entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível. 
    
![Conectando-se ao Office 365 através de firewalls e proxies.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>Atualização do seu firewall da saída listas de permissões

Você pode otimizar sua rede enviando a que todos os confiáveis solicitações diretamente através do firewall da rede do Office 365, ignorando todos inspeção de nível de pacotes adicionais ou processamento. Isso reduz o desempenho lento de latência e reduz seus requisitos de capacidade de perímetro. A maneira mais fácil para escolher qual rede solicitações a confiança é usar nossos arquivos PAC pré-criados na guia **Proxies** acima. 
  
Se o tráfego de saída de blocos de firewall, você vai querer garantir que todos o IP e FQDNs listado como **necessários** neste [arquivo XML](https://go.microsoft.com/fwlink/?LinkId=533185) estão na lista de permissões. Reconhece que todos os serviços exigem o uso de alguns 3º serviços de terceiros. Nós não forneça endereços IP para esses serviços de terceiros 3º como provedores DNS do certificado provedores, redes de fornecimento de conteúdo e assim por diante. Para obter a funcionalidade completa do Office 365, você deve ser capaz de acessar todos os destinos solicitados pelo Office 365 independentemente quanta informação publicamos sobre o destino. 
  
Muitos destinos não têm um endereço IP publicado ou são listados como um domínio de curinga com nenhum nome de domínio totalmente qualificado específico, para usar essa funcionalidade, você deve ser capaz de resolver esses pedidos de rede como o IP atual está sendo solicitado de endereços e enviar o solicitação de rede pela Internet.
  
Automatize o processo usando um firewall que analisa o arquivo XML em seu nome e atualiza suas regras automaticamente com base em serviços ou recursos que você pretende encaminhar diretamente através do firewall. Você também pode usar a ferramenta de [Intervalo do Azure](https://azurerange.azurewebsites.net/) que foi criada pela comunidade e analisa o XML para você com opções de exportação para configuração da lista de ACL ou Cisco XE rota, CSV ou texto sem formatação. 
  
Uma explicação mais os destinos de rede está disponível em nosso [site de referência](urls-and-ip-address-ranges.md) também por meio de [log de alteração de RSS com base em](https://go.microsoft.com/fwlink/p/?linkid=236301) nosso, portanto você pode inscrever-se às alterações. 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>Configurar caminhos de saída com os arquivos de PAC

Use arquivos PAC ou WPAD para gerenciar solicitações de rede que estão associadas com o Office 365, mas não têm um endereço IP fornecido. Solicitações de rede comuns que são enviadas por meio de um dispositivo de proxy ou perímetro acarretar uma latência adicional. Enquanto a autenticação de proxy provoca a maior imposto, outros serviços, como pesquisa de reputação e tentativas para inspecionar pacotes podem causar uma experiência de usuário ruim. Além disso, esses dispositivos de rede de perímetro precisam capacidade suficiente para processar todas as solicitações de rede. É recomendável ignorando a infra-estrutura de inspeção ou proxy para solicitações de rede diretas do Office 365.
  
Use um dos arquivos nosso PAC como um ponto de partida para determinar qual o tráfego de rede será enviado a um proxy e qual será enviada a um firewall. Se estiver familiarizado com arquivos de PAC ou WPAD, leia esta postagem de [arquivos de PAC Implantando](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) um de nossos consultores do Office 365. Você vai querer Revise-as como um ponto de partida e editar de acordo com seu ambiente. 
  
 **Arquivos de PAC atualizados 10/7/2018**. 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1 - arquivo PAC: separa necessário FQDNs de Internet do FQDN de 365 Office conhecidos.

O primeiro exemplo é uma demonstração de nossa abordagem recomendada para gerenciar pontos de extremidade pela Internet apenas. Ignora o proxy para o Office 365 destinos onde o endereço IP é publicado e envia solicitações de rede restantes para o proxy.
  
Trecho de código:
  
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

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2 – arquivo PAC: conectar ao Office 365 pela Internet e ExpressRoute
<a name="bkmk_inet-aer"> </a>

O segundo exemplo é uma demonstração de nossa abordagem recomendada para gerenciar as conexões quando circuitos ExpressRoute e Internet estão disponíveis. Envia ExpressRoute divulgado destinos ao circuito ExpressRoute e Internet apenas divulgado destinos ao proxy.
  
Trecho de código:
  
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

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3 – arquivo PAC: gerenciar todos os destinos de Office 365 coletivamente
<a name="bkmk_inet-direct"> </a>

O terceiro exemplo demonstra o envio de todas as solicitações de rede associadas com o Office 365 para um único destino. Isso geralmente é usado para ignorar todos os inspeção de solicitações de rede do Office 365 e oferece a você um formato onde todos publicado pontos de extremidade está na lista no formato a ser usado para sua personalização PAC.
  
Trecho de código:
  
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

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>Usam scripts personalizados ou criar manualmente seus próprios arquivos PAC
<a name="pacfiles_manual"> </a>

Eis algumas ferramentas mais da comunidade, se você tiver criado algo que você gostaria de compartilhar deixe uma nota nos comentários. None da comunidade ferramentas mencionadas neste artigo são oficialmente suportado ou mantida pela Microsoft e são oferecidos para sua conveniência.
  
- Esta é a ferramenta de comunidade gerada mais antiga para ajudar a gerenciar o processo, uma ferramenta criada por um membro da comunidade do Office 365. Aqui está o link para [Baixar](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).
    
- Verificação de conceito com regras de firewall exportável: [API do Microsoft Cloud IP](https://mscloudips.azurewebsites.net/).
    
- No IT Praktyk: [Conversão de RSS](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) e [conversão de XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).
    
- De Peter Abele: [Baixar](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).
    
- Use sua análise de rede para determinar qual rede solicita deve ignorar sua infraestrutura de proxy. Os FQDNs mais comuns usados para ignorar os proxies de cliente incluem devido ao volume de tráfego de rede enviados e recebidos desses pontos de extremidade.
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- Certifique-se de que quaisquer solicitações de rede sendo enviadas diretamente à seu firewall tem uma entrada correspondente no firewall lista para permitir que a solicitação para passar de permissões.
    
## <a name="perimeter-network-integration"></a>Integração de rede de perímetro
<a name="BKMK_Perimeter"> </a>

Você sabia da Microsoft WAN é uma dos backbones maiores no mundo?
  
É definido como true, que esta rede enorme é o que torna o Office 365 e nossos serviços de nuvem que trabalhar independentemente where do mundo que você está. Nossa rede consiste de largura de banda alta, baixa latência, links capaz de failover com milhares de quilômetros de rota de fibra escura pertencente em particular e multi-Terabit conexões entre data centers e borda nós, para facilitar a usar nossos serviços de nuvem.
  
Com uma rede assim, você deseja que os dispositivos da sua organização para se conectar à nossa rede assim que possível. Com mais de 2.500 relacionamentos de correspondência ISP globalmente e 70 pontos de presença, obtendo da sua rede para nosso deve ser contínuo. Ele não pode prejudicar o gastar alguns minutos, certificando-se que o relacionamento de correspondência do seu ISP é o ideal, [Eis alguns exemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de uma boa e não tão boas aos transferências à nossa rede. 
  
Você pode manualmente ou configurar automaticamente os dispositivos na sua rede para tratem de solicitações de rede de aplicativos do Office 365, dependendo de seu equipamento. Quais alterações de configuração que você precisa fazer em tratem de tráfego de rede do Office 365 dependerá de seu ambiente. Office 365 rede solicitações poderão se beneficiar configurações de rede que permitem o seguinte:
  
- Prioridade sobre o tráfego de rede menos crítico.
    
- O roteamento para uma saída local para evitar backhauling em uma WAN lenta link, beneficiando a latência baixa disponível no Microsoft network. [Aqui está uma boa discussão](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) com base em contratos com clientes. 
    
- Usando o DNS perto de uma saída local para garantir que a solicitação de rede que deixa a saída local chega no local aos Microsoft mais próximo.
    
- Exclusão de profunda inspeção de pacotes ou outros para atender aos requisitos de latência na escala de processamento de pacotes de rede intensiva.
    
Os dispositivos de rede moderno incluem recursos para gerenciar solicitações de rede para aplicativos confiáveis, como o Office 365 diferente genérico, não confiável tráfego da Internet. Com o cenário emergente das soluções SD-WAN, tal diferenciação de tráfego e o caminho de seleção também pode ser executada com o reconhecimento de ao estado em mudança da rede, como o ponto na disponibilidade de tempo, latência ou desempenho dos diversos caminhos de conectividade entre o usuário e a nuvem.
  
Consulte [rede e planejamento de migração para o Office 365](network-and-migration-planning.md), [plano para o Office 365 de solução de problemas de desempenho](performance-troubleshooting-plan.md)e [processo de planejamento de implantação para Office 365](deployment-planning-checklist.md) para obter orientação adicional sobre como planejar sua configuração de rede. 
  
### <a name="to-implement-this-scenario"></a>Para implementar esse cenário:

Verifique com seu provedor de solução ou serviço de rede, se eles podem usar a URL do Office 365 e definições de IP de XML para facilitar o local (para o usuário), pouca sobrecarga de saída para o Office 365 tráfego de rede, gerenciar sua prioridade em relação a outros aplicativos e ajustar a caminho de rede para conexões do Office 365 em rede Microsoft dependendo alterando as condições de rede. Algumas soluções Baixe e automatizam a definição de URL do Office 365 e IP XMLs em suas pilhas.
  
Sempre certifique-se de que a solução implementada tem necessário grau de resiliência, redundância geo apropriada do caminho da rede para tráfego do Office 365 e acomoda mudanças URLs do Office 365 e IPs conforme eles se tornam publicados.
  
## <a name="web-service"></a>Serviço Web
<a name="webservice"> </a>

Para ajudá-lo a identificar e diferenciar o tráfego de rede do Office 365 melhor, um novo web service publica pontos de extremidade do Office 365, tornando mais fácil a avaliar, configurar e manter-se atualizado com as alterações. Esse novo serviço da web (agora na visualização), eventualmente substituirão as listas de pontos de extremidade no artigo [URLs do Office 365 e intervalos de endereços IP](urls-and-ip-address-ranges.md) , juntamente com as versões de RSS e XML desses dados. Esses formato dos dados de ponto de extremidade estão planejados para ser substituídos gradualmente em 2 de outubro de 2018. 
  
Como um cliente ou um fornecedor de dispositivo de perímetro de rede, você pode construir contra o novo serviço da web baseado em REST para as entradas FQDN e o endereço IP do Office 365.
  
- Para obter a versão mais recente dos intervalos de endereço IP e URLs do Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
- Para os dados na página de intervalos de endereço IP para firewalls e servidores proxy e URLs do Office 365, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
- Para obter as últimas alterações, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
Como um cliente, você pode usar esse serviço web para: 
  
- Atualize os scripts do PowerShell para obter dados de ponto de extremidade do Office 365 e modificar qualquer formatação para os dispositivos de redes.
    
- Use essas informações para atualizar os arquivos de PAC implantados nos computadores clientes.
    
Como um fornecedor de dispositivo de perímetro de rede, você pode usar esse serviço web para: 
  
- Criar e testar o software de dispositivo para baixar a lista de configuração automatizada. 
    
- Verificar a versão atual.
    
- Obtenha as alterações atuais.
    
As seções a seguir descrevem a visualização desse serviço web, que pode ser alterado ao longo do tempo até que o serviço está disponível no mercado. 
  
Os dados no serviço da web estão atualizados e nós não estiver planejando fazer alterações adicionais para as URLs de serviço web ou retornados esquema de dados antes do lançamento de disponibilidade geral deste serviço da web.
  
Para obter informações adicionais, consulte:
  
- [Postagem do blog de anúncio no Fórum da comunidade do Office 365 Tech](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [Fórum da comunidade do Office 365 Tech para fazer perguntas sobre o uso dos serviços da web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a>Parâmetros comuns

Esses parâmetros são comuns entre todos os métodos de serviço web:
  
- formato de **= CSV | JSON** -parâmetro de cadeia de caracteres de consulta. Por padrão, o formato de dados retornados é JSON. Inclua este parâmetro opcional para retornar os dados no formato de valores separados por vírgula (CSV). 
    
- **ClientRequestId** - parâmetro de cadeia de caracteres de consulta. Um GUID necessário que você gerar para associação de sessão de cliente. Você deve gerar um GUID para cada máquina cliente que chama o serviço web. Não use os GUIDs mostrados nos exemplos a seguir, porque eles podem ser bloqueados pelo serviço web no futuro. O formato GUID é xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, onde x representa um número hexadecimal. Para gerar um GUID, use o comando [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) do PowerShell. 
    
### <a name="version-web-method"></a>Método da web de versão

A Microsoft atualiza o endereço IP do Office 365 e as entradas de FQDN no final de cada mês e ocasionalmente sair ciclo para operacionais ou requisitos de suporte. Os dados para cada instância publicado são atribuídos a um número de versão. O método de web versão permite sondar para a versão mais recente para cada instância de serviço do Office 365. Recomendamos que você verificar a versão diariamente, ou no máximo, por hora.
  
Há um parâmetro para o método de web de versão:
  
- **AllVersions = true** -parâmetro de cadeia de caracteres de consulta. Por padrão, a versão retornada é o mais recente. Inclua este parâmetro opcional para solicitar que todas as versões publicadas. 
    
- **Instância** - parâmetro Route. Esse parâmetro opcional especifica a instância para retornar a versão para. Se for omitido, todas as instâncias serão retornadas. Instâncias válidas são: mundial, China, Alemanha, USGovDoD, USGovGCCHigh 
    
O resultado do método da web versão pode ser um único registro ou uma matriz de registros. Os elementos de cada registro são:
  
- instância - o nome curto da instância do serviço do Office 365.
    
- informações mais recentes - a versão mais recente para pontos de extremidade da instância especificada.
    
- versões - uma lista de todas as versões anteriores para a instância especificada. Esse elemento só está incluído se o parâmetro AllVersions for true.
   
#### <a name="examples"></a>Exemplos:
  
URI de solicitação do exemplo 1: ** <span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Esse URI retorna a versão mais recente de cada instância de serviço do Office 365. Resultado de exemplo:
  
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
> O GUID para o parâmetro ClientRequestID nesses URIs são apenas um exemplo. Para testar o web URIs check-out de serviço, gerar seu próprios GUID. Os GUIDs mostrados nestes exemplos podem ser bloqueados pelo serviço web no futuro. 
  
URI de solicitação do exemplo 2: ** <span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Esse URI retorna a versão mais recente da instância de serviço especificada do Office 365. Resultado de exemplo:
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

URI de solicitação de exemplo 3: ** <span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
Esse URI mostra a saída no formato CSV. Resultado de exemplo:
  
```
instance,latest
Worldwide,2018063000
```

URI de solicitação de exemplo 4: ** <span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
Esse URI mostra todas as versões anteriores que foram publicadas para a instância de serviço em todo o mundo do Office 365. Resultado de exemplo:
  
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

### <a name="endpoints-web-method"></a>Método da web de pontos de extremidade

O método de web de pontos de extremidade retorna todos os registros para intervalos de endereços IP e URLs que compõem o serviço Office 365. Parâmetros para o método de web de pontos de extremidade são:
  
- **ServiceAreas** - parâmetro de cadeia de caracteres de consulta. Uma lista separada por vírgulas das áreas de serviço. Itens válidos são comum, Exchange, SharePoint, Skype. Como itens de área comuns do serviço são um pré-requisito para todas as outras áreas de serviço, o serviço web sempre incluirá-los. Se você não incluir esse parâmetro, todas as áreas de serviço serão retornadas. 
    
- **TenantName** - parâmetro de cadeia de caracteres de consulta. Seu nome de Inquilino do Office 365. O serviço web leva seu nome fornecido e o insere em partes do URLs que incluem o nome do locatário. Se você não fornecer um nome de locatário, as partes de URLs têm o caractere curinga (\*). 
    
- **NoIPv6** - parâmetro de cadeia de caracteres de consulta. Defina essa opção para True para endereços IPv6 de exclusão de saída, por exemplo, se você não usar o IPv6 em sua rede. 
    
- **Instância** - parâmetro Route. Este parâmetro obrigatório especifica a instância para retornar os pontos de extremidade. Instâncias válidas são: mundial, China, Alemanha, USGovDoD, USGovGCCHigh. 
    
O resultado do método da web de pontos de extremidade é uma matriz de registros com cada registro que representa um conjunto de pontos de extremidade. Os elementos para cada registro são:
  
- ID - o número de identificação imutável do ponto de extremidade definida.
    
- serviceArea - área de serviço que isso faz parte do: comum, Exchange, SharePoint ou Skype.
    
- URLs - definido de URLs para o ponto de extremidade. Uma matriz de JSON dos registros DNS. Omitidos se deixado em branco.
    
- tcpPorts - definido de portas TCP para o ponto de extremidade. Todos os elementos de portas são formatados como uma lista separada por vírgulas dos ou intervalos de portas separados por um caractere de travessão (-). Portas se aplicam a todos os endereços IP e todas as URLs nesse conjunto de ponto de extremidade para essa categoria. Omitidos se deixado em branco.
    
- udpPorts - portas UDP para o IP endereços intervalos nesse conjunto de ponto de extremidade. Omitidos se deixado em branco.
    
- IPS - intervalos de endereço IP associados a esse ponto de extremidade definido como associados com as portas TCP ou UDP listadas. Omitidos se deixado em branco.
    
- a categoria de conectividade para o ponto de extremidade de categoria - definida. Valores válidos são Optimize, permitir e padrão. Necessário.
    
- expressRoute - True ou False se este conjunto de ponto de extremidade é roteado pela ExpressRoute.
    
- obrigatório - True se este conjunto de ponto de extremidade é necessário ter conectividade para o Office 365 ser suportados. Omitidos se for false.
    
- Notas de-de pontos de extremidade opcionais, este texto descreve URLs ou funcionalidades do Office 365 que serão ausentes se endereços IP neste ponto final set não pode ser acessado na camada de rede. Omitidos se deixado em branco.
    
#### <a name="examples"></a>Exemplos:
  
URI de solicitação do exemplo 1: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Esse URI obtém todos os pontos de extremidade para a instância em todo o mundo do Office 365 para todas as cargas de trabalho. Resultados de exemplo mostrando um trecho da saída:
  
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

Conjuntos de ponto de extremidade adicionais não são incluídos neste exemplo.
  
URI de solicitação do exemplo 2: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
Este exemplo obtém os pontos de extremidade para a instância do Office 365 internacional para Exchange Online e dependências apenas.
  
A saída, por exemplo 2 é semelhante ao exemplo 1, exceto que os resultados não incluirá pontos de extremidade para o SharePoint Online ou Skype para negócios Online.
  
### <a name="changes-web-method"></a>Método alterações de web

O método de web alterações retorna as atualizações mais recentes que foram publicadas. Esse é normalmente alterações do mês anterior URLs e intervalos de endereços IP.
  
> [!NOTE]
> Dados das alterações API são precisos na visualização e devem ser usado para o desenvolvimento e teste somente. 
  
O parâmetro para o método de web de alterações é:
  
- **Versão** - parâmetro de rota de URL necessária. A versão que você tenha implementado no momento, e você deseja ver as alterações, desde que a versão. O formato é YYYYMMDDNN. 
    
O resultado do método da web de alterações é uma matriz de registros com cada registro que representa uma alteração em uma versão específica dos pontos de extremidade. Os elementos para cada registro são:
  
- ID - a identificação imutável do registro alteração.
    
- endpointSetId - o ID do ponto de extremidade definido registro é alterado. Necessário.
    
- disposição - isso pode ser de alteração, adicione ou remova e descreve o que fez a alteração para o registro do conjunto de ponto de extremidade.
    
- versão - a versão do ponto de extremidade publicado definida no qual a alteração foi introduzida. Números de versão estão do formato YYYYMMDDNN, onde NN é um número de natural incrementado se houver várias versões deverão ser publicadas em um único dia.
    
- Defina um estruturados detalhando os valores anteriores de elementos alterados no ponto de extremidade anterior. Isso não serão incluído para conjuntos de ponto de extremidade recém-adicionado. Inclui tcpPorts, udpPorts, ExpressRoute, categoria, obrigatória, anotações.
    
- Current - um estruturados detalhando valores atualizados de elementos de alterações no endpoinset. Inclui tcpPorts, udpPorts, ExpressRoute, categoria, obrigatória, anotações.
    
- Add - conjuntos de definir uma estrutura de sub detalhando itens a serem adicionados ao ponto de extremidade. Omitidos se não há nenhuma adições.
    
  - effectiveDate - define os dados quando as adições estará live no serviço.
    
  - IPS - itens a serem adicionados à matriz ips.
    
  - URLs-itens a serem adicionados à matriz urls.
    
- Remova - um estruturados detalhando itens a serem removidos do conjunto de ponto de extremidade. Omitidos se não houver nenhuma remoções.
    
  - IPS - itens a serem removidos da matriz ips.
    
  - Itens de URLs a ser removido da matriz urls.
    
 **Exemplos:**
  
URI de solicitação do exemplo 1: ** <span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Isso solicita todas as alterações anteriores para a instância de serviço em todo o mundo do Office 365. Resultado de exemplo:
  
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

URI de solicitação do exemplo 2: ** <span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Isso solicita alterações desde a versão especificada para a instância do Office 365 internacional. Nesse caso, a versão especificada é o mais recente. Resultado de exemplo:
  
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

### <a name="example-powershell-script"></a>Script do PowerShell de exemplo

Aqui está um script do PowerShell que podem ser executadas para ver se existem ações que você precisa tomar para dados atualizados. Esse script verifica o número de versão para os Office 365 internacional pontos de extremidade de instância. Quando houver uma alteração, baixa os pontos de extremidade e filtros para os pontos de extremidade de categoria "Permitir" e "Otimizar". Ele também usa um ClientRequestId exclusivo entre várias chamadas e salva a versão mais recente encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se uma atualização de versão.
  
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

### <a name="example-python-script"></a>Exemplo de Script Python

Aqui está um script de Python, testado com Python 3.6.3 no Windows 10, que pode ser executado para ver se existem ações que você precisa tomar para dados atualizados. Esse script verifica o número de versão para os Office 365 internacional pontos de extremidade de instância. Quando houver uma alteração, baixa os pontos de extremidade e filtros para os pontos de extremidade de categoria "Permitir" e "Otimizar". Ele também usa um ClientRequestId exclusivo entre várias chamadas e salva a versão mais recente encontrada em um arquivo temporário. Você deve chamar esse script uma vez por hora para verificar se uma atualização de versão.
  
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

### <a name="web-service-interface-versioning"></a>Controle de versão de interface de serviço Web

Atualizações para os parâmetros ou resultados para esses métodos de serviço da web podem ser necessárias no futuro. Depois que a versão de disponibilidade geral desses serviços da web é publicada, a Microsoft fará esforços razoáveis para fornecer prévio de materiais atualizações para o serviço web. Quando a Microsoft acredita que uma atualização exigirá mudanças para os clientes usando o serviço web, o Microsoft manterá a versão anterior (versão anterior) do serviço web disponível para pelo menos doze (12) meses após o lançamento da nova versão. Os clientes que não atualize durante esse tempo podem ser capaz de acessar o serviço web e seus métodos. Os clientes devem garantir que os clientes do serviço web continuam trabalhando sem erro, se as seguintes alterações são feitas na assinatura de interface de serviço web:
  
- Adicionando um novo parâmetro opcional para um método web existente que não tem a serem fornecidos por clientes mais antigos e não afeta o resultado recebe um cliente mais antigo.
    
- Adicionando um novo atributo nomeado em um dos itens do restante de resposta ou colunas adicionais à resposta CSV.
    
- Adicionando um novo método de web com um novo nome não é chamado pelos clientes mais antigos.
    
## <a name="faq"></a>Perguntas frequentes

Perguntas sobre o administrador de perguntas frequentes sobre conectividade:
  
### <a name="how-do-i-submit-a-question"></a>Como faço para enviar uma pergunta?

Clique no link na parte inferior para indicar se o artigo foi útil ou não e enviar perguntas adicionais. Podemos monitorar o feedback e atualizar as perguntas aqui com perguntas frequentes.
  
### <a name="when-is-the-xml-file-updated"></a>Quando o arquivo XML é atualizado?

Quando novos pontos de extremidade são anunciados, normalmente há um buffer de 30 + dia antes que eles são eficazes e solicitações da rede começam a passando a eles. Esse buffer é para garantir que os clientes e parceiros terá a oportunidade de atualizar seus sistemas. FQDN e IP prefix adições e remoções são processadas no arquivo XML, ao mesmo tempo como o comunicado, que significa que um novo FQDN será no arquivo XML de 30 dias antes do uso. Como podemos parar de enviar solicitações da rede aos pontos de extremidade que podemos está removendo antes da anunciando sua remoção, quando removemos o ponto de extremidade do XML ao mesmo tempo que o comunicado já é não utilizado.
  
### <a name="how-can-i-be-notified-of-changes"></a>Como posso ser notificado das alterações?
<a name="bkmk_changes"> </a>

Pontos de extremidade do Office 365 são publicados no final de cada mês com o aviso de 30 dias. Ocasionalmente, a alteração ocorrerá mais de uma vez por mês ou com mais curtos períodos de aviso. Quando é adicionado a um ponto de extremidade, a data efetiva listada no [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) é a data após o qual as solicitações de rede serão enviadas ao ponto de extremidade. Se estiver familiarizado com RSS, aqui está como [Inscreva-se via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) ou você pode [ter o RSS feed atualizações enviadas para você](https://go.microsoft.com/fwlink/p/?LinkId=532417).
  
### <a name="how-do-i-read-the-rss-change-log"></a>Como ler que o RSS de log de alteração?
<a name="bkmk_changes"> </a>

Depois que você se inscrever no RSS feed, você pode analisar as informações sozinho ou com um script. A tabela a seguir descreve o formato do RSS feed o tornam mais fácil.
  
|**Seção**|**Parte 1**|**Parte 2**|**Parte 3**|**Parte 4**|**Parte 5**|**Parte 6**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**Descrição** <br/> |Contagem  <br/> |Data após o qual você pode esperar solicitações sejam enviadas para o ponto de extremidade de rede.  <br/> |Descrição básica do recurso ou serviço que exija o ponto de extremidade.  <br/> |Você pode se conectar a esse ponto de extremidade em um circuito ExpressRoute além da internet?  <br/> |**Sim** — você pode se conectar a esse ponto de extremidade na internet e ExpressRoute.  <br/> **Não** — você só pode se conectar a este ponto de extremidade na internet.  <br/> |O intervalo IP ou FQDN que está sendo adicionado ou removido de destino.  <br/> |
|**Exemplo** <br/> |1 /  <br/> |[Efetivo xx/xx/xxx.  <br/> |Obrigatório: \<descrição\>.  <br/> |ExpressRoute:  <br/> |\<Sim/não\>.  <br/> |\<FQDN/IP\>],  <br/> |
   
Algumas outras coisas observar, cada entrada tem um conjunto comum de delimitadores:
  
- **/**-Após a contagem 
    
- **[-** para indicar a entrada para a contagem 
    
- **.** -usados entre cada seção distinta da entrada 
    
- **],** - para indicar o final de uma única entrada 
    
- **].** -Para indicar o final de todas as entradas 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Como faço para determinar o local do meu locatário?

 **Local de Inquilino** é melhor determinado usando nosso [Mapear datacenter](https://o365datacentermap.azurewebsites.net/).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Sou eu correspondência apropriadamente com Microsoft?

 **Peering locais** são descritos em mais detalhes na [correspondência com a Microsoft](https://www.microsoft.com/peering).
  
Com mais de 2.500 relacionamentos de correspondência ISP globalmente e 70 pontos de presença, obtendo da sua rede para nosso deve ser contínuo. Ele não pode prejudicar o gastar alguns minutos, certificando-se que o relacionamento de correspondência do seu ISP é o ideal, [Eis alguns exemplos](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de uma boa e não tão boas aos transferências à nossa rede. 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>Como determinar quais endereços IP para aceitar o ExpressRoute?

 **Rotas ExpressRoute aceitos** são definidos por [intervalos IP da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602) e o Office 365 [comunidades BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)específico.
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>Como faço para determinar quais pontos de extremidade que eu preciso?

Regularmente adicionamos novos recursos e serviços para o Office 365 suite, expandindo o cenário de conectividade. Se você estiver inscrito ao E3 ou SKU E5, de maneira simples de pensar a lista de pontos de extremidade é que você precisa todos eles para obter a funcionalidade total para o pacote. Se você não se inscreveu para qualquer um desses SKUs a diferença é mínima em termos de número de pontos de extremidade.
  
Leia os [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md) para obter mais informações sobre categorias de ponto de extremidade do Office 365 e entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível. 
  
A imagem abaixo, você pode ver um exemplo de uma parte da tabela FQDN na seção Office Online. As linhas são organizadas por recurso e diferenças na conectividade. As duas primeiras linhas indicam Office Online depende os pontos de extremidade marcados necessário na autenticação do Office 365 e a identidade e portal e seções compartilhadas. Isso é típico de um serviço no Office 365 depender esses serviços compartilhados. A terceira linha indica os computadores cliente devem ser capazes de alcançar \*. officeapps.live.com para usar o Office Online e a quarta linha indica computadores também devem ser capazes de alcançar \*. cdn.office.net para usar o Office Online.
  
Embora ambos linha três e quatro são necessários para usar o Office Online, tiver sido separadas para indicar que o destino é diferente:
  
1. \*. officeapps.live.com não representa uma CDN, solicitações de significado para esse namespace serão levado diretamente para um datacenter da Microsoft.
    
2. \*. officeapps.live.com pode ser acessada em circuitos ExpressRoute usando o Microsoft Peering.
    
3. Os endereços IP associados com o Office Online e \*. officeapps.live.com podem ser encontradas seguindo este link.
    
4. \*. cdn.office.net representa uma CDN hospedada pelo Akamai, solicitações de significado para esse namespace serão encaminhadas para um datacenter Akamai.
    
5. \*. cdn.office.net não está acessível em circuitos ExpressRoute.
    
6. Os endereços IP associados com o Office Online e \*. cdn.office.net não estão disponíveis.
    
![Captura de tela da página pontos de extremidade](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Posso ver as solicitações de rede para os endereços IP não está na lista publicada, preciso para fornecer acesso a eles?
<a name="bkmk_MissingIP"> </a>

Fornecemos apenas endereços IP para os servidores do Office 365 que você deve rotear diretamente pela Internet ou ExpressRoute. Isso não é uma lista abrangente de todos os endereços IP, para que você verá as solicitações de rede. Você verá as solicitações de rede à Microsoft e endereços IP pertencentes, não publicados, softwares de terceiros. Esses endereços IP dinamicamente são gerados ou gerenciados de forma que impede que o aviso em tempo hábil quando eles são alterados. Se seu firewall não pode permitir o acesso com base nos FQDNs para essas solicitações da rede, use um arquivo PAC ou WPAD para gerenciar as solicitações.
  
Ver que um IP associado ao que você deseja obter mais informações no Office 365?
  
1. Verifique se o endereço IP está incluído em um intervalo de publicado maior usando uma [Calculadora CIDR](http://jodies.de/ipcalc).
    
2. Consulte se um parceiro possui o IP com uma [consulta whois](https://dnsquery.org/). Se for Microsoft pertencente, talvez seja um parceiro interno.
    
3. Verifique o certificado, em um navegador conectar ao endereço IP usando *HTTPS://\<IP_ADDRESS\> * , verifique os domínios listados no certificado para entender quais domínios associados com o endereço IP. Se for um endereço IP de propriedade da Microsoft e não está na lista de endereços IP do Office 365, provavelmente é o endereço IP é associado um Microsoft CDN como *MSOCDN.NET* ou outro domínio Microsoft sem informações publicadas de IP. Se você encontrar que o domínio no certificado é uma onde podemos declaração listar o endereço IP, informe-nos. 
    
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Por que vejo nomes como nsatc.net ou akadns.net em nomes de domínio Microsoft?
<a name="bkmk_akamai"> </a>

Office 365 e outros serviços da Microsoft usam vários serviços de terceiros, como Akamai e MarkMonitor para melhorar a experiência do Office 365. Para manter oferecendo a melhor experiência possível, podemos alterar esses serviços no futuro. Ao fazer isso, muitas vezes Publicamos o registro CNAME que aponta para um terceiro domínio pertencente, um registro ou endereço IP. Domínios de terceiros podem hospedar o conteúdo, como uma CDN, ou eles podem hospedar um serviço, como um serviço de gerenciamento de tráfego geográficas. Quando você vir conexões com esses terceiros, eles estão no formato de um redirecionamento ou referência, não uma solicitação inicial do cliente. Alguns clientes precisam garantir a essa forma de referência e passar sem adicionar explicitamente que longa lista de serviços de terceiros FQDNs potenciais pode usar o redirecionamento será permitido.
  
Lista de serviços está sujeita a alterações a qualquer momento. Alguns dos serviços atualmente em uso incluem:
  
[MarkMonitor](https://www.markmonitor.com/) está em uso quando você vir solicitações que incluem * \*. nsatc.net* . Este serviço oferece proteção de nome de domínio e monitoramento para proteger contra comportamentos mal-intencionados. 
  
[ExactTarget](https://www.marketingcloud.com/) está em uso quando você vir solicitações para * \*. exacttarget.com* . Esse serviço fornece contra comportamento mal intencionado de monitoramento e gerenciamento do link de email. 
  
[Akamai](https://www.akamai.com/) está em uso quando você vir solicitações que incluem um dos seguintes FQDNs. Este serviço oferece geo-DNS e serviços de rede de fornecimento de conteúdo. 
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>Quais são os três tipos de pontos de extremidade do Office 365?
<a name="bkmk_akamai"> </a>

- Você pode se conectar aos serviços de terceiros para recuperar serviços básicos da internet, como pesquisas de DNS e recuperação de conteúdo CDN. Você também pode conectar aos serviços de terceiros para integrações como incorporação de vídeos do YouTube em seus blocos de anotações do OneNote.
    
- Conecte-se aos serviços secundários hospedado e execute pela Microsoft, como nós da borda que permitem que sua solicitação de rede inserir a rede global da Microsoft no local mais próximo da internet para seu computador. Como a rede terceira maior do planeta, isso melhora a sua experiência de conectividade. Você também pode conectar aos serviços do Microsoft Azure como Azure Media Services, que são usados por uma variedade de serviços do Office 365.
    
- A conexão com serviços do Office 365 principais, como o servidor de caixa de correio Exchange Online ou o Skype para servidor Business Online onde os seus dados exclusivos e proprietários residem. Você pode se conectar aos serviços do Office 365 principais por endereço IP ou FQDN e usar ExpressRoute circuitos ou internet. Você só pode se conectar ao terceiro e serviços secundários usando FQDNs em um circuito de internet.
    
O diagrama a seguir mostra as diferenças entre essas áreas de serviço. Neste diagrama, a rede de local do cliente na parte inferior esquerda tem vários dispositivos de rede para auxiliar no gerenciamento de conectividade de rede. Configurações como esse são comuns para clientes empresariais. Se sua rede tem somente um firewall entre os computadores cliente e a internet, que é suportado, bem, e você vai querer Certifique-se de que seu firewall pode suportar FQDNs e curingas nas regras de lista Permitir.
  
Leia os [Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md) para obter mais informações sobre categorias de ponto de extremidade do Office 365 e entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível. 
  
![Mostra os três tipos diferentes de pontos de extremidade de rede ao usar o Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>Não consigo ou não desejar usar qualquer serviço de terceiros
<a name="bkmk_thirdparty"> </a>

Office 365 é um conjunto de serviços incluído funcione pela internet, confiabilidade e disponibilidade promessas baseiam-se no muitos serviços de internet padrão que está sendo disponíveis. Por exemplo, os serviços de internet padrão como DNS, CRL e CDNs devem ser acessíveis para usar o Office 365 assim como eles devem ser alcançados para usar os serviços de internet mais modernos.
  
Além desses serviços básicos da internet, existem serviços de terceiros que são usados somente para integrar funcionalidade. Por exemplo, usar Giphy.com dentro Teams Microsoft permite que os clientes incluem perfeitamente Gifs dentro de equipes. Da mesma forma, YouTube e Flickr são os serviços de terceiros que são usados para integrar perfeitamente vídeo e imagens em clientes do Office da internet. Enquanto elas são necessárias para integração, eles estão marcados como opcionais no artigo Office 365 pontos de extremidade que significa que a funcionalidade principal do serviço continuarão a funcionar se o ponto de extremidade não está acessível.
  
Se você estiver tentando usar o Office 365 e está descobrindo serviços de terceiros não estão acessíveis você desejará [Certifique-se de que todos os FQDNs marcados obrigatório ou opcional neste artigo são permitidos por meio do proxy e firewall](urls-and-ip-address-ranges.md).
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>Não consigo ou não deseja usar todos os serviços secundários
<a name="bkmk_secondary"> </a>

Secundário são serviços da Microsoft que não estão dentro do controle do Office 365. Estas são as coisas como a rede de borda, Azure Media Services e redes de distribuição de conteúdo do Windows Azure. Estes são necessários para usar o Office 365 e devem ser alcançados.
  
Se você estiver tentando usar o Office 365 e está descobrindo serviços de terceiros não estão acessíveis você desejará [Certifique-se de que todos os FQDNs marcados obrigatório ou opcional neste artigo são permitidos por meio do proxy e firewall](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Como bloquear o acesso aos serviços de consumidor da Microsoft?
<a name="bkmk_consumer"> </a>

Restringir o acesso aos nossos serviços de consumidor deve ser feita por seu próprio risco, a maneira confiável apenas aos serviços do consumidor de bloqueio é para restringir o acesso a *login.live.com* FQDN. Esse FQDN é utilizado por um amplo conjunto de serviços, incluindo serviços de não-consumidor como MSDN, TechNet e outros. Restringindo o acesso a esse FQDN pode resultar na necessidade de também incluem exceções à regra para solicitações de rede associados a esses serviços. 
  
Tenha em mente que bloqueando o acesso aos serviços do consumidor do Microsoft sozinhos não impedir a capacidade para alguém em sua rede às informações de exfiltrate usando um locatário do Office 365 ou outro serviço.
  
## <a name="related-topics"></a>Tópicos relacionados

[Intervalos de IP de Datacenter Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espaço IP público da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisitos de infraestrutura de rede da Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute e no power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URLs e intervalos de endereços IP do Office 365](urls-and-ip-address-ranges.md)
  
[Como gerenciar o ExpressRoute para a conectividade do Office 365](managing-expressroute-for-connectivity.md)
  
[Princípios de conectividade de rede do Office 365](office-365-network-connectivity-principles.md)
  
