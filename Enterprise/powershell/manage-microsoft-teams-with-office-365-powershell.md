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
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="3571d-103">Gerenciar o Microsoft Teams com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3571d-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="3571d-104">Você pode gerenciar o Microsoft Teams com o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3571d-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="3571d-105">Primeiro, instale o [módulo do Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="3571d-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="3571d-106">Entrar com um nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="3571d-106">Sign in with a user name and password</span></span>

<span data-ttu-id="3571d-107">Para a nuvem do Office 365 Worldwide (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="3571d-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="3571d-108">Para a nuvem DoD do Office 365 do governo dos EUA:</span><span class="sxs-lookup"><span data-stu-id="3571d-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="3571d-109">Para a nuvem superior do Office 365 governo dos EUA, GCC:</span><span class="sxs-lookup"><span data-stu-id="3571d-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="3571d-110">Entrar com a autenticação multifator (MFA)</span><span class="sxs-lookup"><span data-stu-id="3571d-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="3571d-111">Para a nuvem do Office 365 Worldwide (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="3571d-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="3571d-112">Para a nuvem DoD do Office 365 do governo dos EUA:</span><span class="sxs-lookup"><span data-stu-id="3571d-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="3571d-113">Para a nuvem superior do Office 365 governo dos EUA, GCC:</span><span class="sxs-lookup"><span data-stu-id="3571d-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="3571d-114">Desconectar do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3571d-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="3571d-115">Use este comando:</span><span class="sxs-lookup"><span data-stu-id="3571d-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="3571d-116">Também consulte</span><span class="sxs-lookup"><span data-stu-id="3571d-116">See also</span></span>

[<span data-ttu-id="3571d-117">Visão geral do teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="3571d-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="3571d-118">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3571d-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3571d-119">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3571d-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

