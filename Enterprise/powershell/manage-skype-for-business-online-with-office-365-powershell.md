---
title: Gerenciar o Skype for Business Online com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumo: Use o Office 365 PowerShell para gerenciar as políticas do Skype for Business online, políticas por usuário e configurações da reunião.'
ms.openlocfilehash: 80d8308a1c9b32fcafd47d1df2f699141e41accd
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782131"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="9ea66-103">Gerenciar o Skype for Business Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ea66-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="9ea66-104">**Resumo:** use o Office 365 PowerShell para gerenciar as políticas do Skype for Business Online, políticas por usuário e configurações de reunião.</span><span class="sxs-lookup"><span data-stu-id="9ea66-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="9ea66-105">Uma das principais tarefas de qualquer administrador do Skype for Business online é gerenciar políticas.</span><span class="sxs-lookup"><span data-stu-id="9ea66-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="9ea66-106">Embora você possa executar algumas dessas tarefas no centro de administração do Microsoft 365, outras tarefas são muito mais rápidas e fáceis no Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ea66-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="9ea66-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="9ea66-107">Before you start</span></span>

<span data-ttu-id="9ea66-108">Baixe e instale o [módulo do conector do Skype for Business online](https://www.microsoft.com/en-us/download/details.aspx?id=39366)e reinicie o computador, se solicitado.</span><span class="sxs-lookup"><span data-stu-id="9ea66-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="9ea66-109">Conectar-se usando um nome e senha da conta de administrador do Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="9ea66-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="9ea66-110">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="9ea66-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="9ea66-111">Na caixa de diálogo solicitação de credencial do **Windows PowerShell** , digite seu nome e senha da conta de administrador do Skype for Business Online e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9ea66-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="9ea66-112">Conectar-se usando uma conta de administrador do Skype for Business online com a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="9ea66-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="9ea66-113">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="9ea66-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="9ea66-114">Quando solicitado pelo comando **New-CsOnlineSession** , insira seu nome de conta de administrador do Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="9ea66-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="9ea66-115">Na caixa de diálogo **entrar na conta** , digite sua senha de administrador do Skype for Business Online e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="9ea66-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="9ea66-116">Siga as instruções na caixa de diálogo **entrar na conta** para fornecer informações de autenticação adicionais, como um código de verificação, e clique em **verificar**.</span><span class="sxs-lookup"><span data-stu-id="9ea66-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="9ea66-117">Para saber mais, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="9ea66-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="9ea66-118">Gerenciar Skype para políticas Business Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ea66-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="9ea66-119">Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ea66-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="9ea66-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="9ea66-120">See also</span></span>

[<span data-ttu-id="9ea66-121">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ea66-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9ea66-122">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ea66-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="9ea66-123">Referências do cmdlet do PowerShell do Skype for Business</span><span class="sxs-lookup"><span data-stu-id="9ea66-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

