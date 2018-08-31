---
title: Exibir erros de sincronização de diretórios no Office 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Saiba como exibir erros de sincronização de diretório no Centro de administração do Office 365.
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539287"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Exibir erros de sincronização de diretórios no Office 365

Você pode exibir erros de sincronização de diretório no Centro de administração do Office 365. Somente os erros de objeto de usuário são exibidos. Para exibir erros usando o PowerShell, consulte [objetos de identidade com DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).

Depois de exibição, consulte [Corrigindo problemas com a sincronização de diretório para o Office 365](fix-problems-with-directory-synchronization.md) para corrigir os problemas identificados.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Exibir erros de sincronização de diretório no Centro de administração

Para exibir quaisquer erros no Centro de administração:
  
1. Entre no Office 365 com sua conta corporativa ou de estudante. 
    
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
