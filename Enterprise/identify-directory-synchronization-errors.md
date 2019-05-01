---
title: Exibir erros de sincronização de diretório no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Saiba como exibir os erros de sincronização de diretório no centro de administração do Microsoft 365.
ms.openlocfilehash: 8450c2e26c9c9ae194be46d81018a20c91e35f29
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491249"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Exibir erros de sincronização de diretório no Office 365

Você pode exibir os erros de sincronização de diretório no [centro de administração do Microsoft 365](https://admin.microsoft.com). Somente os erros de objeto do usuário são exibidos. Para exibir erros usando o PowerShell, consulte [identificar objetos com DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Após a exibição, confira [corrigir problemas de sincronização de diretório para o Office 365](fix-problems-with-directory-synchronization.md) para corrigir quaisquer problemas identificados.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Exibir erros de sincronização de diretório no centro de administração

Para exibir qualquer erro no centro de administração:
  
1. Entre no Office 365 com uma conta corporativa ou de estudante. 
    
2. Vá até o [centro de administração](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Na **Home** Page, você verá o bloco **status DirSync** . 
    
    ![O bloco de status dirSync na visualização do centro de administração](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. No bloco, escolha **status DirSync** para ir para a página **status de sincronização de diretório** . 
    
    Na parte inferior da página, você pode ver se há erros dirSync.
    
    ![Na página status de sincronização de diretório, você pode ver se há erros de objeto dirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Escolha encontramos **erros de objeto DirSync** para ir para um modo de exibição detalhado dos erros de sincronização de diretório. 
    
    > [!NOTE]
    > Você também pode acessar a página **erros DirSync** se escolher erros de **objeto DirSync** no bloco de **status DirSync** . 
  
![Página de erros dirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Na página **erros DirSync** , escolha qualquer um dos erros listados para exibir o painel de detalhes com informações sobre o erro e dicas sobre como corrigi-lo. 
