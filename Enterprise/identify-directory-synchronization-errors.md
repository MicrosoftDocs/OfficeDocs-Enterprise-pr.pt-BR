---
title: Exibir erros de sincronização de diretórios no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Saiba como exibir erros de sincronização de diretório no Centro de administração do Office 365.
ms.openlocfilehash: 8beeeebbb24936abd7c93f4c04c0fa4e27c85c12
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327333"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Exibir erros de sincronização de diretórios no Office 365

Você pode exibir erros de sincronização de diretório no Centro de administração do Office 365. Somente os erros de objeto de usuário são exibidos. Para exibir erros usando o PowerShell, consulte [objetos de identidade com DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Depois de exibição, consulte [Corrigindo problemas com a sincronização de diretório para o Office 365](fix-problems-with-directory-synchronization.md) para corrigir os problemas identificados.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Exibir erros de sincronização de diretório no Centro de administração

Para exibir quaisquer erros no Centro de administração:
  
1. Entre no Office 365 com a sua conta corporativa ou de estudante. 
    
2. Vá para o [Centro de administração sobre o Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Na página **inicial** do, você verá a **Status do DirSync** lado a lado. 
    
    ![O Status de DirSync lado a lado no modo de visualização admin center](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Na organização lado o lado, escolha **DirSync Status** para ir para a página **Status da sincronização de diretório** . 
    
    Na parte inferior da página, você pode ver se há erros de DirSync.
    
    ![Na página Status da sincronização de diretório, você pode ver se há erros de objeto do DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Escolha **encontramos DirSync erros de objeto** para ir para uma exibição detalhada dos erros de sincronização de diretório. 
    
    > [!NOTE]
    > Você também pode ir à página **DirSync erros** se você escolher **encontramos DirSync erros de objetos** no lado a lado **status de DirSync** . 
  
![Página de erros de DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Na página **DirSync erros** , escolha qualquer um dos erros listados para exibir o painel de detalhes, com informações sobre o erro e dicas sobre como corrigi-lo. 
