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
ms.openlocfilehash: 48b10038e396953469f4b0732103671cbc6b0d75
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030936"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Gerenciar o Skype for Business Online com o Office 365 PowerShell

 **Resumo:** use o Office 365 PowerShell para gerenciar as políticas do Skype for Business Online, políticas por usuário e configurações de reunião.
  
Uma das principais tarefas de qualquer administrador do Skype for Business online é gerenciar políticas. Embora você possa executar algumas dessas tarefas no centro de administração do Microsoft 365, outras tarefas são muito mais rápidas e fáceis no Office 365 PowerShell. 

## <a name="before-you-start"></a>Antes de começar

Baixe e instale o [módulo do conector do Skype for Business online](https://www.microsoft.com/download/details.aspx?id=39366)e reinicie o computador, se solicitado.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Conectar-se usando um nome e senha da conta de administrador do Skype for Business Online

1. Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Na caixa de diálogo **solicitação de credencial do Windows PowerShell** , digite seu nome e senha da conta de administrador do Skype for Business Online e clique em **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Conectar-se usando uma conta de administrador do Skype for Business online com a autenticação multifator

1. Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Quando solicitado pelo comando **New-CsOnlineSession** , insira seu nome de conta de administrador do Skype for Business online.

3. Na caixa de diálogo **entrar na conta** , digite sua senha de administrador do Skype for Business Online e clique em **entrar**.

4. Siga as instruções na caixa de diálogo **entrar na conta** para fornecer informações de autenticação adicionais, como um código de verificação, e clique em **verificar**.

Para saber mais, consulte os tópicos a seguir:
  
- [Gerenciar Skype para políticas Business Online com o Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Confira também

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

[Referências do cmdlet do PowerShell do Skype for Business](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

