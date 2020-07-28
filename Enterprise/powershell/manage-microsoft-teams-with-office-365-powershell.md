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
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429184"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="36e73-103">Gerenciar o Microsoft Teams com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="36e73-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="36e73-104">*Esse artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="36e73-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="36e73-105">Você pode gerenciar o Microsoft Teams com o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36e73-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="36e73-106">Primeiro, instale o [módulo do Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="36e73-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="36e73-107">Entrar com um nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="36e73-107">Sign in with a user name and password</span></span>

<span data-ttu-id="36e73-108">Para a nuvem do Office 365 Worldwide (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="36e73-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="36e73-109">Para a nuvem DoD do Office 365 do governo dos EUA:</span><span class="sxs-lookup"><span data-stu-id="36e73-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="36e73-110">Para a nuvem superior do Office 365 governo dos EUA, GCC:</span><span class="sxs-lookup"><span data-stu-id="36e73-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="36e73-111">Entrar com a autenticação multifator (MFA)</span><span class="sxs-lookup"><span data-stu-id="36e73-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="36e73-112">Para a nuvem do Office 365 Worldwide (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="36e73-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="36e73-113">Para a nuvem DoD do Office 365 do governo dos EUA:</span><span class="sxs-lookup"><span data-stu-id="36e73-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="36e73-114">Para a nuvem superior do Office 365 governo dos EUA, GCC:</span><span class="sxs-lookup"><span data-stu-id="36e73-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="36e73-115">Desconectar do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="36e73-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="36e73-116">Use este comando:</span><span class="sxs-lookup"><span data-stu-id="36e73-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="36e73-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="36e73-117">See also</span></span>

[<span data-ttu-id="36e73-118">Visão geral do teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="36e73-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="36e73-119">Gerenciar o Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="36e73-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="36e73-120">Introdução ao PowerShell para o Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="36e73-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

