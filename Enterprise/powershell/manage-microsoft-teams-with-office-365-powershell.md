---
title: Gerenciar o Microsoft Teams com o PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Resumo: Use o PowerShell para gerenciar o Microsoft Teams.'
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230607"
---
# <a name="manage-microsoft-teams-with-powershell"></a>Gerenciar o Microsoft Teams com o PowerShell

*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*

Você pode gerenciar o Microsoft Teams com o PowerShell.
  
Primeiro, instale o [módulo do Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).
    
## <a name="sign-in-with-a-user-name-and-password"></a>Entrar com um nome de usuário e senha

Para a nuvem do Office 365 Worldwide (+ GCC):

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

Para a nuvem DoD do Office 365 do governo dos EUA: 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

Para a nuvem superior do Office 365 governo dos EUA, GCC:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>Entrar com a autenticação multifator (MFA)

Para a nuvem do Office 365 Worldwide (+ GCC):

```powershell
Connect-MicrosoftTeams
```

Para a nuvem DoD do Office 365 do governo dos EUA: 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

Para a nuvem superior do Office 365 governo dos EUA, GCC:

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>Desconectar do Microsoft Teams

Use este comando:

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>Confira também

[Visão geral do teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Gerenciar o Microsoft 365 com o PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao PowerShell para o Microsoft 365](getting-started-with-office-365-powershell.md)

