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
f1.keywords:
- CSH
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
description: Saiba como a autenticação moderna da 365 Microsoft funciona de forma diferente para os aplicativos cliente do Office 2013 e 2016.
ms.openlocfilehash: a7c3a9a8aaa4705ff81607718813060be3455ccd
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997838"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Como funciona a autenticação moderna para aplicativos cliente do Office 2013 e do Office 2016

*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*

Leia este artigo para saber como os aplicativos clientes do Office 2013 e do Office 2016 usam recursos de autenticação modernos com base na configuração de autenticação no Microsoft 365 locatário para Exchange Online, SharePoint Online e Skype for Business online.

> [!NOTE]
> Aplicativos clientes herdados, como o Office 2010 e o Office para Mac 2011, não oferecem suporte à autenticação moderna e só podem ser usados com a autenticação básica.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Disponibilidade da autenticação moderna para os serviços do Microsoft 365

Para os serviços do Microsoft 365, o estado padrão da autenticação moderna é:
  
- Ativado **para o** Exchange Online por padrão. Confira [habilitar ou desabilitar a autenticação moderna no Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) para desativá-la ou fazê-la. 
    
- Ativado **para o** SharePoint Online por padrão. 
    
- Ativado **para o** Skype for Business online por padrão. Consulte [habilitar o Skype for Business online para obter autenticação moderna ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)para desativá-la ou para.

> [!NOTE]
> Para locatários criados **antes** 1º de agosto de 2017, a autenticação moderna é **desativada** por padrão para o Exchange Online e o Skype for Business Online.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportamento de entrada dos aplicativos cliente do Office

Os aplicativos cliente do Office 2013 dão suporte à autenticação herdada por padrão. Herdado significa que eles suportam o assistente de conexão do Microsoft Online ou a autenticação básica. Para que esses clientes usem recursos de autenticação modernos, o cliente do Windows deve ter chaves de registro definidas. Para obter instruções, consulte [habilitar a autenticação moderna do Office 2013 em dispositivos Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

To enable modern authentication for any devices running Windows (for example on laptops and tablets), that have Microsoft Office 2013 installed, you need to set the following registry keys. The keys have to be set on each device that you want to enable for modern authentication:
  
|**Chave do Registro**|**Tipo**|**Valor** |
|:-------|:------:|--------:|
|Hkcu\software\microsoft\office\15.0 \common\identity\enableadal com  |REG_DWORD  |1   |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1  |
  
Leia [como usar a Adal (autenticação moderna) com o Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=785431) para saber como ela funciona com o Skype for Business. 
  
Os clientes do Office 2016 dão suporte à autenticação moderna por padrão, e nenhuma ação é necessária para que o cliente use esses novos fluxos. No entanto, é necessária uma ação explícita para usar a autenticação herdada.
  
Clique nos links abaixo para ver como a autenticação de cliente do Office 2013 e Office 2016 funciona com os serviços do Microsoft 365, dependendo se a autenticação moderna está ativada ou não.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

A tabela a seguir descreve o comportamento de autenticação para os aplicativos cliente do Office 2013 ou do Office 2016 quando eles se conectam ao Exchange Online com ou sem a autenticação moderna.
  
|Versão do aplicativo cliente do Office * * * *|Chave do registro presente? * * * *|Autenticação moderna em? * * * *|Comportamento de autenticação com autenticação moderna ativada para o locatário (padrão) * * * *|Comportamento de autenticação com autenticação moderna desativada para o locatário * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Não <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Sim  <br/> |Força a autenticação moderna no Outlook 2010, 2013 ou 2016 <br/> [Mais informações](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Força a autenticação moderna no cliente do Outlook.<br/> |
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
   
## <a name="see-also"></a>Também consulte

[Habilitar a Autenticação Moderna do Office 2013 em dispositivos Windows.](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/enable-modern-authentication)

[Autenticação multifator para Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365)

[Entrar no Microsoft 365 com a autenticação multifator](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Visão geral do Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
