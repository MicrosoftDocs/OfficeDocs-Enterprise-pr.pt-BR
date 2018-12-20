---
title: Como a autenticação moderna funciona para os aplicativos clientes do Office 2013 e do Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
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
description: Saiba como autenticação moderna do Office 365 funciona de modo diferente para aplicativos de cliente de 2016 e Office 2013.
ms.openlocfilehash: 2a5e218ca751f341e2a3a0ffd164f000ee503279
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378497"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Como a autenticação moderna funciona para os aplicativos clientes do Office 2013 e do Office 2016

Leia este artigo para saber como o Office 2013 e aplicativos de cliente do Office 2016 usam recursos modernos de autenticação com base na configuração de autenticação no locatário do Office 365 para Exchange Online, SharePoint Online e Skype para negócios Online.
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>Disponibilidade de autenticação moderna aos serviços do Office 365

Para os serviços do Office 365, o estado padrão de autenticação moderno é:
  
- **Ativado para o Exchange Online por padrão.** Consulte [Habilitar ou desabilitar a autenticação moderna no Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) para ativar ou desativar o ele. 
    
- **Ativado para o SharePoint Online por padrão.** 
    
- **Ativado para Skype para Business Online por padrão.** Consulte [Habilitar Skype para negócios Online para autenticação moderna ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)ativá-lo ou desativar.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportamento de entrada dos aplicativos de cliente do Office

Aplicativos de cliente do Office 2013 suportam a autenticação de legado por padrão. Herdado significa que tem suporte para qualquer um dos Microsoft Online entrar assistente ou básica autenticação. Em ordem para estes clientes usem os recursos de autenticação moderno, as janelas cliente tem possuem chaves do registro definido. Para obter instruções, consulte [Ativar autenticação moderna do Office 2013 em dispositivos do Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).
  
Leia [como usar moderno autenticação (ADAL) com Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=785431) para saber mais sobre como ele funciona com o Skype para negócios. 
  
Clientes do Office 2016 oferecem suporte à autenticação moderna por padrão e nenhuma ação é necessária para o cliente usar esses novos fluxos. No entanto, a ação explícita é necessária para usar a autenticação de legado.
  
Clique nos links abaixo para ver como a autenticação de cliente do Office 2013 e Office 2016 funciona com os serviços do Office 365 dependendo ou não autenticação moderna está ativada.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

A tabela a seguir descreve o comportamento de autenticação para aplicativos de cliente do Office 2013 ou Office 2016 ao se conectarem ao Exchange Online com ou sem autenticação moderna.
  
|Office cliente app versão * * *|Chave de registro presente? * * *|Autenticação moderna nos? * * *|Comportamento de autenticação com autenticação moderno ativado para o locatário (padrão) * * *|Comportamento de autenticação com autenticação moderno desativada por locatário * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Não, ou EnableADAL = 1  <br/> |Sim  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, autenticação básica é usada. Servidor recusará moderna autenticação quando o locatário não está habilitado.  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, autenticação básica é usada. Servidor recusará moderna autenticação quando o locatário não está habilitado.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, autenticação básica é usada. Servidor recusará moderna autenticação quando o locatário não está habilitado.  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, autenticação básica é usada. Servidor recusará moderna autenticação quando o locatário não está habilitado.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 0  <br/> |Não  <br/> |Autenticação básica  <br/> |Autenticação básica  <br/> |
|Office 2013  <br/> |Não  <br/> |Não  <br/> |Autenticação básica  <br/> |Autenticação básica  <br/> |
|Office 2013  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, autenticação básica é usada. Servidor recusará moderna autenticação quando o locatário não está habilitado.  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, autenticação básica é usada. Servidor recusará moderna autenticação quando o locatário não está habilitado.  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

A tabela a seguir descreve o comportamento de autenticação para aplicativos de cliente do Office 2013 ou Office 2016 ao se conectarem ao SharePoint Online com ou sem autenticação moderna.
  
|Office cliente app versão * * *|Chave de registro presente? * * *|Autenticação moderna nos? * * *|Comportamento de autenticação com autenticação moderno ativado para o locatário (padrão) * * *|Comportamento de autenticação com autenticação moderno desativada por locatário * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Não, ou EnableADAL = 1  <br/> |Sim  <br/> |Somente autenticação moderna.  <br/> |Falha ao se conectar.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |Somente autenticação moderna.  <br/> |Falha ao se conectar.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 0  <br/> |Não  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |
|Office 2013  <br/> |Não  <br/> |Não  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |
|Office 2013  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |Somente autenticação moderna.  <br/> |Falha ao se conectar.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business online
<a name="BK_SFBO"> </a>

A tabela a seguir descreve o comportamento de autenticação para o Office 2013 ou aplicativos de cliente do Office 2016 quando eles se conectam ao Skype para Business Online com ou sem autenticação moderna.
  
|Office cliente app versão * * *|Chave de registro presente? * * *|Autenticação moderna nos? * * *|Comportamento de autenticação com autenticação moderno ativado para o locatário * * *|Comportamento de autenticação com autenticação moderno desativado para o locatário (padrão) * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Não, ou EnableADAL = 1  <br/> |Sim  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, é usado o Assistente de entrada do Microsoft Online. Servidor recusará a autenticação moderna quando Skype para os locatários Business Online não estão habilitados.  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, é usado o Assistente de entrada do Microsoft Online. Servidor recusará a autenticação moderna quando Skype para os locatários Business Online não estão habilitados.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, é usado o Assistente de entrada do Microsoft Online. Servidor recusará a autenticação moderna quando Skype para os locatários Business Online não estão habilitados.  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, é usado o Assistente de entrada do Microsoft Online. Servidor recusará a autenticação moderna quando Skype para os locatários Business Online não estão habilitados.  <br/> |
|Office 2016  <br/> |Sim, EnableADAL = 0  <br/> |Não  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |
|Office 2013  <br/> |Não  <br/> |Não  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |
|Office 2013  <br/> |Sim, EnableADAL = 1  <br/> |Sim  <br/> |Autenticação moderna é tentada primeiro. Se o servidor recusará uma conexão de autenticação moderno, é usado o Assistente de entrada do Microsoft Online. Servidor recusará a autenticação moderna quando Skype para os locatários Business Online não estão habilitados.  <br/> |Microsoft Online Assistente de conexão apenas.  <br/> |
   
## <a name="see-also"></a>Confira também

[Habilitar a Autenticação Moderna do Office 2013 em dispositivos Windows.](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[Planejar a autenticação multifator para implantações do Office 365 (para administradores do Office 365)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[Faça logon no Office 365 com 2-etapa verificação (para usuários finais)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)