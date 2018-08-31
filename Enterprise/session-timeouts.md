---
title: Tempos limite de sessão para o Office 365
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
description: Tempos limite de sessão é usado para balancear a segurança e facilidade de acesso nos aplicativos de cliente do Office 365.
ms.openlocfilehash: dda13f280149c969354ae1f0eac336f1d8ed23e7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539261"
---
# <a name="session-timeouts-for-office-365"></a>Tempos limite de sessão para o Office 365

Tempo de vida de sessão é uma parte importante de autenticação para o Office 365 e um componente importante no balanceamento de segurança e o número de vezes que os usuários são solicitados para suas credenciais.
  
## <a name="session-times-for-office-365-services"></a>Tempos de sessão para serviços do Office 365

Quando os usuários são autenticados em qualquer um dos aplicativos do Office 365 web ou aplicativos móveis, uma sessão é estabelecida. Para a duração da sessão, os usuários não precisam autenticar novamente. Sessões podem expirar quando os usuários estão inativos, quando eles fecharem o navegador ou o guia, ou quando seu token de autenticação expira por outros motivos, como quando sua senha for redefinida. Os serviços do Office 365 têm tempos limite de sessão diferente para se corresponder com o uso normal de cada serviço.
  
A tabela a seguir lista os tempos de vida de sessão para os serviços do Office 365:
  
|**Serviço do Office 365**|**Tempo limite de sessão**|
|:-----|:-----|
|Centro de administração do Office 365  <br/> |Será solicitado que você forneça credenciais para o admin center a cada 8 horas.  <br/> |
|SharePoint Online  <br/> |5 dias de inatividade, desde que os usuários escolhe **Mantenha-me conectado**. Se o usuário acessa o SharePoint Online novamente após 24 ou mais horas do sign-in anterior, o valor de tempo limite é redefinido para 5 dias.<br/> |
|Outlook Web App  <br/> |seis horas.  <br/> Você pode alterar esse valor usando o _ActivityBasedAuthenticationTimeoutInterval_ parâmetro no cmdlet [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) .  <br/> |
|Azure Active Directory  <br/> (Usado pelos clientes do Office 2013 Windows com autenticação moderna habilitada)  <br/> | Autenticação moderna usa tokens de acesso e tokens de atualização para conceder acesso aos recursos do Office 365 usando o Windows Azure Active Directory do usuário. Um token de acesso é um JSON Web Token fornecido após uma autenticação bem-sucedida e é válido para 1 hora. Também é fornecido um token de atualização com um tempo de vida de mais tempo. Quando terminar de tokens de acesso, os clientes do Office usam um token de atualização válido para obter um novo token de acesso. Troca for bem-sucedido, se a autenticação inicial do usuário é voltado e ainda válida.  <br/>  Tokens de atualização são válidas por 90 dias e com o uso contínuo, eles podem ser válidos até revogado.  <br/>  Atualizar tokens podem ser invalidados por vários eventos, como:  <br/>  Senha do usuário foi alterado desde que o token de atualização foi emitido.  <br/>  Um administrador pode aplicar políticas de acesso condicional que restringem o acesso ao recurso que o usuário está tentando acessar.  <br/> |
|SharePoint e OneDrive aplicativos móveis para Android, iOS e Windows 10  <br/> |O tempo de vida padrão para o token de acesso é 1 hora. O tempo inativo máximo de padrão do token refresh é 90 dias.<br/> [Saiba mais sobre como configurar a vida útil do token e de tokens](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Para revogar a atualização de token, você pode redefinir a senha do usuário Office 365  <br/> |
|Com o Office 365 entrar no Yammer  <br/> |Tempo de vida do navegador. Se os usuários feche o navegador e acessar o Yammer em um novo navegador, o Yammer vai autenticá-los novamente com o Office 365. Se os usuários usarem navegadores de terceiros que cookies de cache, eles não precisará sua reconexão quando eles reabra o navegador.<br/> > [!NOTE]> Isso é válido apenas para redes que usam o Office 365 entrar no Yammer.           |
   

