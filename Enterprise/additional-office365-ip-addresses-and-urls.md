---
title: Pontos de extremidade adicionais não incluídos no endereço IP do Office 365 e no serviço Web de URL
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/04/2019
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'Resumo: o novo serviço Web de ponto de extremidade não inclui uma quantidade pequena de pontos de extremidade para cenários específicos.'
hideEdit: true
ms.openlocfilehash: f226e48fa6512e32e505d7ca1a35ab1fec390488
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490892"
---
# <a name="additional-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Pontos de extremidade adicionais não incluídos no endereço IP do Office 365 e no serviço Web de URL

Alguns pontos de extremidade de rede foram publicados anteriormente e não foram incluídos no [endereço IP do Office 365 e no serviço Web de URL](office-365-ip-web-service.md). O escopo de serviços Web é de pontos de extremidade de rede que são necessários para conectividade de um usuário final do Office 365 em uma rede de perímetro empresarial. Atualmente, isso não inclui:

1. Conectividade de rede que pode ser requerida de um datacenter da Microsoft para uma rede do cliente (tráfego de rede de servidor de entrada híbrido).
2. Conectividade de rede de servidores em uma rede do cliente no perímetro empresarial (tráfego de rede de servidor de saída).
3. Cenários excepcionais para requisitos de conectividade de rede de um usuário.
4. Requisitos de conectividade de resolução DNS (não listados abaixo).
5. Sites confiáveis do Internet Explorer ou Microsoft Edge.

Exceto pelo DNS, todos estes são opcionais para a maioria dos clientes, a menos que você precise do cenário específico descrito.

|||||
|:-----|:-----|:-----|:-----|
| **Linha** | **Objetivo** | **Destino** | **Tipo** |
| 1  | [Serviço de importação](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) para PST e ingestão de arquivos | Confira o [Serviço de Importação](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) para requisitos adicionais. | Cenários excepcionais de saída |
| 2  | [Assistente de suporte e recuperação da Microsoft para o Office 365](https://diagnostics.office.com/#/) – validar as credenciais do usuário de logon único. Fonte: <br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | Serviço de token de segurança local | Tráfego do servidor de entrada |
| 3  | Azure AD Connect (com opção de SSO) – WinRM e PowerShell remoto | Ambiente de STS do cliente (servidor do AD FS e Proxy do AD FS) \| portas TCP 80 e 443 | Tráfego do servidor de entrada |
| 4  | STS, como servidor (es) Proxy do AD FS (somente para clientes federados) | STS do cliente (como Proxy do AD FS) \| portas TCP 443 ou TCP 49443 com ClientTLS | Tráfego do servidor de entrada |
| 5  | [Mensagens unificadas no Exchange Online/Integração de SBC](https://technet.microsoft.com/library/jj673565.aspx) | Bidirecional entre controlador de borda de sessão local e *. um.outlook.com | Somente o tráfego de servidor de saída |
| 6  | Migração de caixa de correio. Quando a migração de caixa de correio é iniciada a partir do [Exchange Híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) para o Office 365, o Office 365 se conectará a seu servidor publicado de Serviços Web do Exchange (EWS)/Serviços de Replicação da Caixa de Correio (MRS). Se você precisar que os endereços IP NAT usados pelos servidores Exchange Online restrinjam conexões de entrada de intervalos IP de fontes específicas, eles se encontram listados em [Intervalos IP e de URL do Office 365](urls-and-ip-address-ranges.md) na área do serviço “Exchange Online”. Tome cuidado para garantir que o acesso a pontos de extremidade EWS publicados como OWA não seja impactado, certificando-se de que o proxy de MRS seja resolvido em um FQDN separado e em um endereço IP público antes de restringir as conexões TCP 443 de intervalos IP de fontes específicas. | Proxy de EWS/MRS local do cliente<br> Porta TCP 443 | Tráfego do servidor de entrada |
| 7  | A coexistência do [Exchange Híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) funciona como um compartilhamento de disponibilidade. | Servidor Exchange local do cliente | Tráfego do servidor de entrada |
| 8  | Autenticação de proxy do [Exchange Híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) | STS local do cliente | Tráfego do servidor de entrada |
| 9  | Usado para configurar o [Exchange Híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant), usando o [Assistente de Configuração do Exchange Híbrido](https://docs.microsoft.com/exchange/hybrid-configuration-wizard) <br> Observação: esses pontos de extremidade só são necessários para configurar o Exchange híbrido  | domains.live.com em portas TCP 80 e 443, exigido apenas para o Assistente de Configuração do Exchange 2010 SP3 Híbrido.<BR> <BR> Endereços de IP DoD GCC High: 40.118.209.192/32; 168.62.190.41/32 <BR> <BR> Comercial em todo o mundo e GCC: *. *.store.core.windows.net; asl.configure.office.com; mshrcstorageprod.blob.core.windows.net; tds.configure.office.com; mshybridservice.trafficmanager.net <BR>  | Somente o tráfego de servidor de saída |
| 10  | O serviço de detecção automática é usado em cenários do [Exchange Híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) com [Autenticação Híbrida Moderna com Outlook para iOS e Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <BR> <BR> ```*.acompli.net``` <BR> <BR> ```*.outlookmobile.com``` <BR> <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | Servidor Exchange local do cliente em TCP 443 | Tráfego do servidor de entrada |
| 11  | O Skype for Business no Office 2016 inclui o compartilhamento de tela baseado em vídeo que usa portas UDP. Os clientes mais antigos do Skype for Business no Office 2013 e em versões anteriores usavam a porta 443 RDP em vez da TCP. | Porta 443 TCP aberta para 52.112.0.0/14 | Versões de cliente mais antigas do Skype for Business no Office 2013 e em versões anteriores |
| 12  | Conectividade entre o servidor híbrido local do Skype for Business e o Skype for Business Online | 13.107.64.0/18, 52.112.0.0/14 portas UDP: 50.000 a 59.999 <BR>  Portas TCP: 50.000 a 59.999 | Conectividade de saída de servidor local no Skype for Business |
| 13  | O PSTN na nuvem sem conectividade híbrida local requer conectividade aberta ao host local. Para saber mais sobre as configurações híbridas do Skype for Business Online  | Confira [Planejar conectividade híbrida entre o Skype for Business Server e o Office 365](https://docs.microsoft.com/skypeforbusiness/hybrid/plan-hybrid-connectivity). | Entrada híbrida local do Skype for Business |
| 14  | **FQDNs de autenticação e identidade** <br> O FDQN ```secure.aadcdn.microsoftonline-p.com```precisa estar no Internet Explorer (IE) ou na Zona de Sites Confiáveis de Borda para funcionar. |  | Sites confiáveis |
| 15  |  **FDQNs do Microsoft Teams** <br> Se estiver usando o Internet Explorer ou o Microsoft Edge, é necessário habilitar os cookies primários e de terceiros, adicionar os FQDNs do Teams aos Sites Confiáveis, além de todo o pacote de FQDNs, CDNs e telemetria relacionados na linha 14. Para saber mais, confira o artigo [Problemas conhecidos do Microsoft Teams](https://docs.microsoft.com/microsoftteams/known-issues). |  | Sites confiáveis |
| 16  |  **FDQNs do SharePoint Online e do OneDrive for Business** <br> Todos os FDQNs ".sharepoint.com" com "\<locatário>" devem estar na zona de Sites Confiáveis do Internet Explorer ou do Microsoft Edge do cliente para funcionar. Além de todo o pacote de FDQNs, CDNs e telemetria relacionados na linha 14, é necessário também adicionar esses pontos de extremidade. |  | Sites confiáveis |
| 17  | **Yammer**  <br> O Yammer só está disponível no navegador e exige que o usuário esteja autenticado através de um proxy. Todos os FQDNs do Yammer devem estar no IE ou Zona de Sites confiáveis de Borda do cliente para funcionar. |  | Sites confiáveis |

## <a name="related-topics"></a>Tópicos relacionados

[Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md)
  
[Solucionar problemas de conectividade do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Conectividade de cliente](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Redes de distribuição de conteúdo](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Intervalos de IP do Datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Grupos de notícias públicos da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

