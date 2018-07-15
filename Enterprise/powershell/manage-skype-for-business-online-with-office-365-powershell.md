---
title: Gerenciar o Skype for Business Online com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumo: Use o Office 365 PowerShell para gerenciar as políticas do Skype for Business online, políticas por usuário e configurações da reunião.'
ms.openlocfilehash: f490131491a026961b0a5db312df5780483eadd9
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319232"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="935a1-103">Gerenciar o Skype for Business Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="935a1-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="935a1-104">**Resumo:** use o Office 365 PowerShell para gerenciar as políticas do Skype for Business Online, políticas por usuário e configurações de reunião.</span><span class="sxs-lookup"><span data-stu-id="935a1-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="935a1-p101">Uma das tarefas de qualquer Skype para Business Online administrador primárias está gerenciando políticas. Embora você possa realizar algumas dessas tarefas no Centro de administração do Office 365, outras tarefas são muito mais rápido e fácil no Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="935a1-p101">One of the primary tasks of any Skype for Business Online administrator is managing policies. Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="935a1-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="935a1-107">Before you start</span></span>

<span data-ttu-id="935a1-108">Baixar e instalar o [Skype para módulo Business Connector Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366)e reinicie o computador se solicitado.</span><span class="sxs-lookup"><span data-stu-id="935a1-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="935a1-109">Conectar usando um Skype para senha e nome da conta de administrador Business Online</span><span class="sxs-lookup"><span data-stu-id="935a1-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="935a1-110">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="935a1-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="935a1-111">Na caixa de diálogo **Solicitação de credencial do Windows PowerShell** , digite sua Skype Business Online nome da conta de administrador e senha e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="935a1-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="935a1-112">Conectar usando um Skype para conta de administrador Business Online com a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="935a1-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="935a1-113">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="935a1-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="935a1-114">Quando solicitado pelo comando **New-CsOnlineSession** , insira seu Skype do nome da conta de administrador Business Online.</span><span class="sxs-lookup"><span data-stu-id="935a1-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="935a1-115">Na caixa de diálogo **entrar em sua conta** , digite sua Skype Business Online senha de administrador e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="935a1-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="935a1-116">Siga as instruções na caixa de diálogo **entrar em sua conta** para fornecer informações de autenticação adicionais, como um código de verificação e clique em **Verificar**.</span><span class="sxs-lookup"><span data-stu-id="935a1-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="935a1-117">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="935a1-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="935a1-118">Gerenciar Skype para políticas Business Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="935a1-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="935a1-119">Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="935a1-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="935a1-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="935a1-120">See also</span></span>

[<span data-ttu-id="935a1-121">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="935a1-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="935a1-122">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="935a1-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

