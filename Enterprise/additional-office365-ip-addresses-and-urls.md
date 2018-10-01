---
title: Endereços IP e URLs adicionais do Office 365 não incluídos nos serviços web
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 9/13/2018
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
description: 'Resumo: os novos serviços Web de ponto de extremidade não incluem uma quantidade pequena de pontos de extremidade para cenários específicos.'
hideEdit: true
ms.openlocfilehash: 4711f9b9560b0fab6d18700fcf3e933150861946
ms.sourcegitcommit: 0f98c342f80ffa21ec35bbf4ae5619b5e3271da5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23977346"
---
# <a name="additional-office-365-ip-addresses-and-urls-not-included-in-the-web-services"></a>Endereços IP e URLs adicionais do Office 365 não incluídos nos serviços web

Alguns pontos de extremidade de rede foram publicados anteriormente e não foram incluídos nos serviços da web. O escopo de serviços da web é de pontos de extremidade de rede que são necessários para conectividade de um usuário final do Office 365 em uma rede de perímetro empresarial. Atualmente, isso não inclui:

1. Conectividade de rede que pode ser requerida de um datacenter da Microsoft para uma rede do cliente (tráfego de rede de servidor de entrada híbrido)
2. Conectividade de rede de servidores em uma rede do cliente no perímetro empresarial (tráfego de rede de servidor de saída)
3. Cenários excepcionais para requisitos de conectividade de rede de um usuário
4. Requisitos de conectividade de resolução DNS (não listados abaixo)
5. Sites confiáveis do Internet Explorer ou Microsoft Edge

Exceto pelo DNS, todos estes são opcionais para a maioria dos clientes, a menos que você precise do cenário específico descrito.

|||||
|:-----|:-----|:-----|:-----|
| **Linha** | **Objetivo** | **Destino** | **Tipo** |
| 1  | [Serviço de importação](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) para PST e ingestão de arquivos | Confira o [Serviço de Importação](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) para requisitos adicionais. | Cenários excepcionais de saída |
| 2  | [Assistente de suporte e recuperação da Microsoft para o Office 365](https://diagnostics.office.com/#/) – validar as credenciais do usuário de logon único. Fonte: <br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | Serviço de token de segurança local | Tráfego do servidor de entrada |
| 3  | Azure AD Connect (com opção de SSO) – WinRM e PowerShell remoto | Ambiente de STS do cliente (servidor do AD FS e Proxy do AD FS) \| portas TCP 80 e 443 | Tráfego do servidor de entrada |
| 4  | STS, como servidor (es) Proxy do AD FS (somente para clientes federados) | STS do cliente (como Proxy do AD FS) \| portas TCP 443 ou TCP 49443 com ClientTLS | Tráfego do servidor de entrada |
| 5  | [Mensagens unificadas no Exchange Online/Integração de SBC](https://technet.microsoft.com/library/jj673565.aspx) | Bidirecional entre controlador de borda de sessão local e *. um.outlook.com | Somente o tráfego de servidor de saída |
| 6  | A coexistência do [Exchange Híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) funciona como um compartilhamento de disponibilidade. | Servidor Exchange local do cliente | Tráfego do servidor de entrada |
| 7  | Autenticação de proxy do [Exchange híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) | STS local do cliente | Tráfego do servidor de entrada |
| 8  | Usado para configurar o [Exchange Híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant), usando o Assistente de Configuração do Exchange Híbrido. <br> Observação: esses pontos de extremidade só são necessários para configurar o Exchange híbrido  | ```domains.live.com``` em portas TCP 80 e 443, exigido apenas para o Assistente de Configuração do Exchange 2010 SP3 Híbrido. | Somente o tráfego de servidor de saída |
| 9  | O serviço de detecção automática é usado em cenários do [Exchange Híbrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) com [Autenticação Híbrida Moderna com Outlook para iOS e Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <BR> <BR> ```*.acompli.net``` <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | Servidor Exchange local do cliente em TCP 443 | Tráfego do servidor de entrada |
| 10  | **FQDNs de autenticação e identidade** <br> O FDQN ```secure.aadcdn.microsoftonline-p.com```precisa estar no Internet Explorer (IE) ou na Zona de Sites Confiáveis de Borda para funcionar. |  | Sites confiáveis |
| 11  |  **FDQNs do Microsoft Teams** <br> Se estiver usando o Internet Explorer ou o Microsoft Edge, você precisa habilitar os cookies de primeiros e terceiros e adicionar os FQDNs do Teams aos seus Sites Confiáveis. Isso além de todo o pacote de FQDNs, CDNs e telemetria listados acima. Confira [Problemas conhecidos do Microsoft Teams](https://docs.microsoft.com/microsoftteams/known-issues) para saber mais. |  | Sites confiáveis |
| 12  |  **FDQNs do SharePoint Online e do OneDrive for Business** <br> Todas as FDQNs '. sharepoint.com' com '\<locatário >' na FQDN precisam estar no IE ou na Zona de Sites Confiáveis de Borda de seu cliente para funcionar. Além de todo o pacote de FDQNs, CDNs e telemetria listados acima, você precisará adicionar também esses pontos de extremidade. |  | Sites confiáveis |
| 13  | **Yammer**  <br> O Yammer só está disponível no navegador e exige que o usuário esteja autenticado através de um proxy. Todos os FQDNs do Yammer devem estar no IE ou Zona de Sites confiáveis de Borda do cliente para funcionar. |  | Sites confiáveis |

## <a name="related-topics"></a>Tópicos relacionados

[Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md)
  
[Solucionar problemas de conectividade do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Conectividade de cliente](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Redes de distribuição de conteúdo](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Intervalos de IP do Datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Grupos de notícias públicos da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

