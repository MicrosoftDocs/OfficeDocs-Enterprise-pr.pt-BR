---
title: Log de alteração de pontos de extremidade do Office 365 Alemanha
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid: MOE150
ms.assetid: 980041c9-7984-44b2-95f0-af66743543a1
ms.openlocfilehash: e77d6fc3b8136f39ed75ef21b0ff417a4ad6465a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539374"
---
# <a name="office-365-germany-endpoints-change-log"></a>Log de alteração de pontos de extremidade do Office 365 Alemanha

*Aplicável à: Administração do Office 365*

## <a name="list-of-changes-to-the-endpoints-required-for-office-365-germany"></a>Lista de alterações para os pontos de extremidade necessários para o Office 365 Alemanha

A tabela a seguir lista as alterações aos [pontos de extremidade do Office 365 Alemanha](office-365-germany-endpoints.md).
  
|**Date**|**Alteração**|
|:-----|:-----|
|1/24/2017  <br/> |Publicação inicial do artigo.  <br/> |
|2/28/2017  <br/> |Adicionando 3 FQDNs; 1 / [efetivo 4/1/2017. Obrigatório: Portal do Office 365 e compartilhado. ExpressRoute: não. www.Office.de], 2 / [efetivo 4/1/2017. Obrigatório: Portal do Office 365 e compartilhado. ExpressRoute: não. Office.de], 3 / [efetivo 4/1/2017. Obrigatório: Portal do Office 365 e compartilhado. ExpressRoute: não. officehome.msocdn.de]. Notes: adicionando adicionais Portal FQDNs. adicionando 2 IP_Sets; 1 / [efetivo 4/1/2017. Obrigatório: Portal do Office 365 e compartilhado. ExpressRoute: n º 51.5.245.67/32], 2 / [efetivo 4/1/2017. Obrigatório: Portal do Office 365 e compartilhado. ExpressRoute: n º 51.4.227.178/32]. Observações: Adicionando pontos de extremidade de Portal adicionais. Adicionando 2 IP_Sets; 1 / [efetivo 4/1/2017. Obrigatório: Portal do Office 365 e compartilhado. ExpressRoute: n º 2a01:4180:2001::92], 2 / [efetivo 4/1/2017. Obrigatório: Portal do Office 365 e compartilhado. ExpressRoute: n º 2a01:4180:2401::11f]. Observações: Adicionando pontos de extremidade de Portal adicionais.  <br/> |
|3/8/2017  <br/> |Adicionando FQDNs 1; 1 / [efetivo 3/8/2017. Obrigatório: OneDrive for Business. ExpressRoute: não. spoprod-a.akamaihd.net]. Observações: Adicionando pontos de extremidade CDN adicionais.  <br/> |
|3/31/2017  <br/> |Adicionando 3 FQDNs; 1 / [efetivo 5/1/2017. Obrigatório: SharePoint Online híbrido. \*. search.production.de.azuretrafficmanager.de], 2 / [efetivo 5/1/2017. Obrigatório: SharePoint Online híbrido. login.microsoftonline.de], 3 / [efetivo 5/1/2017. Obrigatório: SharePoint Online híbrido. provisioningapi.microsoftonline.de]. Notes: adicionando Sharepoint híbrido FQDNs.  <br/> |
|6/1/2017  <br/> |Adicionando 2 FQDNs efetiva em 1/7/2017  <br/> shellprod.msocdn.de  <br/> R1.res.office365.com  <br/> |
|6/26/2017  <br/> |Substituído Autodiscover\*. outlook.de com Autodiscover.outlook.de e outlook.office.de de descoberta automática.  <br/> |
|9/29/2017  <br/> |Adicionando 3 FQDNs; 1 / [efetivo 11/1/2017.  <br/> cegsignup.microsoft.de  <br/> negsignup.microsoft.de  <br/> \*. svc.ms  <br/> |
|1/16/2018  <br/> |Adicionando FQDNs 1; 1 / [efetivo 2/1/2018. Obrigatório: Portal do Office 365. ExpressRoute: não. webshell.Suite.Office.de]. Notes: adicionando FQDN adicional do shell de pacote do Office 365. Adicionando 4 IP_Sets; 1 / [efetivo 2/1/2018. Obrigatório: Portal do Office 365. ExpressRoute: n º 51.5.242.163/32], 2 / [efetivo 2/1/2018. Obrigatório: Portal do Office 365. ExpressRoute: n º 51.4.226.115/32], 3 / [efetivo 2/1/2018. Obrigatório: Portal do Office 365. ExpressRoute: N º 2a01:4180:2401::33b / 4 / [efetivo 2/1/2018. Obrigatório: Portal do Office 365. ExpressRoute: N º 2a01:4180:2001::234 / Notes: adicionando endereços IP adicionais para o shell de pacote do Office 365.  <br/> |
|2/5/2018  <br/> |Adicionar 1 FQDN; 1 / [efetivo 3/1/2018. Obrigatório: Portal e compartilhado. ExpressRoute: Sim. webshell.Suite.Office.de]. Notes: adicionar uma URL de Portal e compartilhado FQDNs. adicionando 2 IP_Sets; 1 / [efetivo 3/1/2018. Obrigatório: Portal e compartilhado. ExpressRoute: Sim. 51.5.242.163/32]., 2 / [efetivo 3/1/2018. Obrigatório: Portal e compartilhado. ExpressRoute: Sim. 51.4.226.115/32]. Observações: Adicionando novos prefixos de Portal e compartilhado. Adicionando 2 IP_Sets; 1 / [efetivo 3/1/2018. Obrigatório: Portal e compartilhado. ExpressRoute: Sim. 2a01:4180:2401::33b / 128]., 2 / [efetivo 3/1/2018. Obrigatório: Portal e compartilhado. ExpressRoute: Sim. 2a01:4180:2001::234 / 128]. Observações: Adicionando novos prefixos de Portal e compartilhado. Adicionando 1 IP_Sets; 1 / [efetivo 3/1/2018. Obrigatório: Office Online. ExpressRoute: Sim. 51.18.16.0/23]. Observações: Adicionando um novo prefixo para o Office Online.  <br/> |
|15/3/2018  <br/> |Adicionando 1 IP_Set; 1 / [efetivo 4/15/2018. Obrigatório: Office 365 ProPlus. ExpressRoute: n º 51.18.0.0/21]. Observações: Adicionando um ponto de extremidade do Office 365 ProPlus.  <br/> |
|2/7/2018  <br/> |Removendo 1 FQDN; 1 / [efetivo 8/1/2018. Obrigatório: OneDrive for Business. ExpressRoute: não. login.microsoftonline.de]. Notes: Removendo OneDrive para o ponto de extremidade de negócios. Removendo 11 FQDNs; 1 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://excelps.osi.office.de/exlps/excelprint.svc/exlPrint], 2 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://wordps.osi.office.de/wrdps/wordprint.svc/wrdprint], 3 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://wordcs.osi.office.de/wordauto/wordautomation.svc/wordautomation], 4 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://wordcs.osi.office.de/wordauto/wordautomation.svc/rest], 5 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://pptps.osi.office.de/pptps/powerpointprint.svc/PptPrint], 6 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/PptAutomation], 7 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/rest], 8 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://ols.osi.office.de/], 9 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://ols.osi.office.de/olsc/OlsClient.svc/OlsClient], 10 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://excelcs.osi.office.de/xlauto/excelautomation.svc/XlAutomation], 11 / [efetivo 8/1/2018. Obrigatório: Office Mobile. ExpressRoute: n º https://excelcs.osi.office.de/xlauto/excelautomation.svc/rest]. Observações: Removendo pontos de extremidade do Office Mobile.  <br/> |
   

