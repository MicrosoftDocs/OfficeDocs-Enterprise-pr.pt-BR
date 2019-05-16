---
title: Visualizar o status de sincronização de diretório no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Saiba como desativar a sincronização de diretórios. Você também pode exibir seu status.
ms.openlocfilehash: 4204d72719e928982b2b6222fb971d62c0f1f8d6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070407"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Visualizar o status de sincronização de diretório no Office 365

Se você integrou o Active Directory local ao Azure AD sincronizando seu ambiente local com o Office 365, você também pode verificar o status da sua sincronização.
  
## <a name="view-directory-synchronization-status"></a>Exibir status de sincronização de diretório

- Entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com) e escolha **status DirSync** na página inicial.
- Como alternativa, você pode ir para **** \> **usuários ativos**do usuário e, na **página usuários ativos** , escolha **mais** \> **sincronização de diretórios**. No painel de **sincronização de diretórios** , escolha **ir para gerenciamento DirSync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informações na página Gerenciar sincronização de diretório

A tabela a seguir lista os recursos para os quais você pode obter informações na página.
  
Se houver um problema com a sincronização de diretório, os erros também serão listados nessa página. Para obter mais informações sobre diferentes erros que você pode encontrar, consulte [identificar erros de sincronização de diretório no Office 365](identify-directory-synchronization-errors.md).
  
|**Item**|**Para que serve**|
|:-----|:-----|
|**Domínios verificados** | Número de domínios em seu locatário do Office 365 que você verificou você possui. |
|**Domínios não verificados** | Domínios que você adicionou, mas não verificados. |
|**Sincronização de diretório habilitada** |True ou false. Especifica se você habilitou a sincronização de diretório. |
|**Sincronização de diretório mais recente** | Última vez em que a sincronização de diretório foi executada. Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização tiver mais de três dias. |
|**Sincronização de senha habilitada** | True ou false. Especifica se você tem sincronização de hash de senha entre o seu locatário do Office 365 e o local. |
|**Última sincronização de senha** | Última vez em que a sincronização de hash de senha foi executada. Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização tiver mais de três dias. |
|**Versão do cliente de sincronização de diretório** | Contém um link de download se uma nova versão do Azure AD Connect foi liberada. |
|**Ferramenta IDFix** | Link de download para o [IDFix](install-and-run-idfix.md), uma ferramenta que você pode usar para verificar se você localizou o Active Directory. |
|**Conta de serviço de sincronização de diretório** | Exibe o nome da conta do serviço de sincronização de diretório do Office 365. |