---
title: Gerenciar o Microsoft Teams com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Resumo: Use o Office 365 PowerShell para gerenciar o Microsoft Teams.'
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209114"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a>Gerenciar o Microsoft Teams com o Office 365 PowerShell

Você pode gerenciar o Microsoft Teams com o Office 365 PowerShell.
  
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


## <a name="see-also"></a>Também consulte

[Visão geral do teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

