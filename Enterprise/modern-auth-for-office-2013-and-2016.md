---
title: Como funciona a autenticação moderna para aplicativos cliente do Office 2013 e do Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: Saiba como a autenticação moderna do Office 365 funciona de forma diferente para os aplicativos cliente do Office 2013 e 2016.
ms.openlocfilehash: 17a6713fe12e7cdb1fe0355dd38b44b4cb93be54
ms.sourcegitcommit: 756f1713cab2e46be948f91f6dd87fd60197c4a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "36491290"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Como funciona a autenticação moderna para aplicativos cliente do Office 2013 e do Office 2016

Leia este artigo para saber como os aplicativos clientes do Office 2013 e do Office 2016 usam recursos de autenticação modernos com base na configuração de autenticação no locatário do Office 365 para o Exchange Online, o SharePoint Online e o Skype for Business online.

> [!NOTE]
> Aplicativos clientes herdados, como o Office 2010 e o Office para Mac 2011, não oferecem suporte à autenticação moderna e só podem ser usados com a autenticação básica.

## <a name="availability-of-modern-authentication-for-office-365-services"></a>Disponibilidade da autenticação moderna para os serviços do Office 365

Para os serviços do Office 365, o estado padrão da autenticação moderna é:
  
- Ativado **** para o Exchange Online por padrão. Confira [habilitar ou desabilitar a autenticação moderna no Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) para desativá-la ou fazê-la. 
    
- Ativado **** para o SharePoint Online por padrão. 
    
- Ativado **** para o Skype for Business online por padrão. Consulte [habilitar o Skype for Business online para obter autenticação moderna ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)para desativá-la ou para.

> [!NOTE]
> Para locatários criados **antes** de 1º de agosto de 2017, a autenticação **** moderna é desativada por padrão para o Exchange Online e para o Skype for Business online.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportamento de entrada dos aplicativos cliente do Office

Os aplicativos cliente do Office 2013 dão suporte à autenticação herdada por padrão. Herdado significa que eles suportam o assistente de conexão do Microsoft Online ou a autenticação básica. Para que esses clientes usem recursos de autenticação modernos, o cliente do Windows tem chaves do registro definidas. Para obter instruções, consulte [habilitar a autenticação moderna do Office 2013 em dispositivos Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).
  
Leia [como usar a Adal (autenticação moderna) com o Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=785431) para saber como ela funciona com o Skype for Business. 
  
Os clientes do Office 2016 dão suporte à autenticação moderna por padrão, e nenhuma ação é necessária para que o cliente use esses novos fluxos. No entanto, é necessária uma ação explícita para usar a autenticação herdada.
  
Clique nos links abaixo para ver como a autenticação de cliente do Office 2013 e Office 2016 funciona com os serviços do Office 365, dependendo se a autenticação moderna está ativada ou não.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

A tabela a seguir descreve o comportamento de autenticação para os aplicativos cliente do Office 2013 ou do Office 2016 quando eles se conectam ao Exchange Online com ou sem a autenticação moderna.
  
|Versão do aplicativo cliente do Office * * * *|Chave do registro presente? * * * *|Autenticação moderna em? * * * *|Comportamento de autenticação com autenticação moderna ativada para o locatário (padrão) * * * *|Comportamento de autenticação com autenticação moderna desativada para o locatário * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Não, ou EnableADAL = 1  <br/> |Sim  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, a autenticação básica será usada. O servidor recusa a autenticação moderna quando o locatário não está habilitado.  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, a autenticação básica será usada. O servidor recusa a autenticação moderna quando o locatário não está habilitado.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, a autenticação básica será usada. O servidor recusa a autenticação moderna quando o locatário não está habilitado.  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, a autenticação básica será usada. O servidor recusa a autenticação moderna quando o locatário não está habilitado.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 0  <br/> |Não  <br/> |Autenticação básica  <br/> |Autenticação básica  <br/> |
|Office 2013  <br/> |Não  <br/> |Não  <br/> |Autenticação básica  <br/> |Autenticação básica  <br/> |
|Office 2013  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, a autenticação básica será usada. O servidor recusa a autenticação moderna quando o locatário não está habilitado.  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, a autenticação básica será usada. O servidor recusa a autenticação moderna quando o locatário não está habilitado.  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

A tabela a seguir descreve o comportamento de autenticação para os aplicativos cliente do Office 2013 ou do Office 2016 quando eles se conectam ao SharePoint Online com ou sem a autenticação moderna.
  
|Versão do aplicativo cliente do Office * * * *|Chave do registro presente? * * * *|Autenticação moderna em? * * * *|Comportamento de autenticação com autenticação moderna ativada para o locatário (padrão) * * * *|Comportamento de autenticação com autenticação moderna desativada para o locatário * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Não, ou EnableADAL = 1  <br/> |Sim  <br/> |Somente autenticação moderna.  <br/> |Falha ao se conectar.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |Somente autenticação moderna.  <br/> |Falha ao se conectar.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 0  <br/> |Não  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |
|Office 2013  <br/> |Não  <br/> |Não  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |
|Office 2013  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |Somente autenticação moderna.  <br/> |Falha ao se conectar.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

A tabela a seguir descreve o comportamento de autenticação para os aplicativos cliente do Office 2013 ou do Office 2016 quando eles se conectam ao Skype for Business online com ou sem a autenticação moderna.
  
|Versão do aplicativo cliente do Office * * * *|Chave do registro presente? * * * *|Autenticação moderna em? * * * *|Comportamento de autenticação com autenticação moderna ativada para o locatário * * * *|Comportamento de autenticação com autenticação moderna desativada para o locatário (padrão) * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Não, ou EnableADAL = 1  <br/> |Sim  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, o assistente de conexão do Microsoft Online será usado. O servidor recusa a autenticação moderna quando os locatários do Skype for Business online não estão habilitados.  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, o assistente de conexão do Microsoft Online será usado. O servidor recusa a autenticação moderna quando os locatários do Skype for Business online não estão habilitados.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, o assistente de conexão do Microsoft Online será usado. O servidor recusa a autenticação moderna quando os locatários do Skype for Business online não estão habilitados.  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, o assistente de conexão do Microsoft Online será usado. O servidor recusa a autenticação moderna quando os locatários do Skype for Business online não estão habilitados.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 0  <br/> |Não  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |
|Office 2013  <br/> |Não  <br/> |Não  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |
|Office 2013  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |A autenticação moderna é tentada primeiro. Se o servidor recusar uma conexão de autenticação moderna, o assistente de conexão do Microsoft Online será usado. O servidor recusa a autenticação moderna quando os locatários do Skype for Business online não estão habilitados.  <br/> |Assistente de conexão do Microsoft Online apenas.  <br/> |
   
## <a name="see-also"></a>Confira também

[Habilitar a autenticação moderna do Office 2013 em dispositivos Windows](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[Planejar a autenticação multifator para implantações do Office 365 (para administradores do Office 365)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[Entrar no Office 365 com verificação em duas etapas (para usuários finais)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)
