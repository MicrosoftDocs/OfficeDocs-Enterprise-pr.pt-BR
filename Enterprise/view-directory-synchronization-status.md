---
title: Exibir o status da sincronização de diretório no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Saiba como desativar a sincronização de diretório. Também é possível exibir seu status.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539445"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Exibir o status da sincronização de diretório no Office 365
Se você tiver integrado seu Active Directory no local com o Azure AD por meio da sincronização seu ambiente local com o Office 365, você também pode verificar o status da sua sincronização.
  
## <a name="view-directory-synchronization-status"></a>Exibir status de sincronização de diretório
- Entrar no Centro de administração do Office 365 e escolha **DirSync Status** na home page. 
- Como alternativa, você pode ir para **usuários** \> **usuários ativos**e na página **usuários ativos** , escolha **mais** \> **sincronização de diretórios**. No painel de **Sincronização de diretórios** , escolha **vá para gerenciamento de DirSync**.
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>Informações sobre a página de sincronização de diretório de gerenciar

A tabela a seguir lista os recursos que você pode obter informações sobre na página.
  
Se houver um problema com a sincronização de diretórios, os erros são listados nesta página também. Para obter mais informações sobre erros diferentes que podem ser encontrados, consulte [identificar erros de sincronização de diretórios no Office 365](identify-directory-synchronization-errors.md).
  
|**Item**|**What's for**|
|:-----|:-----|
|**Domínios verificados** | Número de domínios no seu locatário do Office 365 que você verificou você é proprietário. |
|**Domínios não verificados** | Domínios você tenha adicionado, mas não verificada. |
|**Sincronização de diretório ativada** |True ou False. Especifica se você habilitou a sincronização de diretório. |
|**Sincronização de diretório mais recente** | Hora da última sincronização de diretório foi executada. Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização foram há mais de três dias. |
|**Sincronização de senha habilitada** | True ou False. Especifica se você tiver a sincronização de hash de senha entre nosso local e seu locatário do Office 365. |
|**Última sincronização de senha** | Hora da última sincronização de hash de senha foi executada. Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização foram há mais de três dias. |
|**Versão do cliente de sincronização de diretório** | Contém um link de download, se uma nova versão do Azure Connect do AD foi liberada. |
|**Ferramenta IDFix** | Baixe o link para o [IDFix](install-and-run-idfix.md), uma ferramenta que você pode usar para verificar a você o Active Directory local. |
|**Conta de serviço de sincronização de diretório** | Exibe o nome do que a conta de serviço de sincronização de diretório do Office 365. |