---
title: Gerenciar o Skype for Business Online com o Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumo: use o Windows PowerShell para Microsoft 365 para gerenciar as políticas do Skype for Business Online, políticas por usuário e configurações de reunião.'
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592205"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="a6faa-103">Gerenciar o Skype for Business Online com o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6faa-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="a6faa-104">*Este artigo se aplica tanto ao Microsoft 365 Enterprise quanto ao Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="a6faa-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="a6faa-105">Uma das principais tarefas de um administrador do Skype for Business Online é gerenciar políticas.</span><span class="sxs-lookup"><span data-stu-id="a6faa-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="a6faa-106">Embora você possa executar algumas dessas tarefas no Centro de administração do Microsoft 365, outras tarefas são muito mais rápidas e fáceis no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6faa-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="a6faa-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="a6faa-107">Before you start</span></span>

<span data-ttu-id="a6faa-108">Baixe e instale o [módulo Conector do Skype for Business Online](https://www.microsoft.com/download/details.aspx?id=39366) e, então, reinicie o computador.</span><span class="sxs-lookup"><span data-stu-id="a6faa-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="a6faa-109">Conectar usando um nome e uma senha da conta de administrador do Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a6faa-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="a6faa-110">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="a6faa-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="a6faa-111">Na caixa de diálogo **Solicitação de Credenciais do Windows PowerShell**, digite o nome e a senha da sua conta de administrador do Skype for Business Online e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6faa-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="a6faa-112">Conectar usando uma conta de administrador do Skype for Business Online com a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="a6faa-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="a6faa-113">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="a6faa-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="a6faa-114">Quando solicitado pelo comando **New-CsOnlineSession**, insira o nome da sua conta de administrador do Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="a6faa-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="a6faa-115">Na caixa de diálogo **Entre em sua conta**, digite sua senha de administrador do Skype for Business Online e clique em **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="a6faa-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="a6faa-116">Siga as instruções na caixa de diálogo **Entre em sua conta** para fornecer informações adicionais de autenticação, como um código de verificação, e clique em **Verificar**.</span><span class="sxs-lookup"><span data-stu-id="a6faa-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="a6faa-117">Para mais informações, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="a6faa-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="a6faa-118">Gerenciar as políticas do Skype for Business Online com o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6faa-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="a6faa-119">Atribuir políticas do Skype for Business online por usuário com o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6faa-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="a6faa-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="a6faa-120">See also</span></span>

[<span data-ttu-id="a6faa-121">Gerenciar o Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6faa-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a6faa-122">Introdução ao PowerShell para o Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a6faa-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="a6faa-123">Referências de cmdlet do Windows PowerShell do Skype for Business</span><span class="sxs-lookup"><span data-stu-id="a6faa-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

