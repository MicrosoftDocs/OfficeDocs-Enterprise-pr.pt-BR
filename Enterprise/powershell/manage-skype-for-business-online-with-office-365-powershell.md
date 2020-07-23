---
title: Gerenciar o Skype for Business online com o PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumo: Use o PowerShell para Microsoft 365 para gerenciar políticas do Skype for Business Online, políticas por usuário e configurações de reunião.'
ms.openlocfilehash: f66b3186a5b29bbf0756a629b85c626caf2c1e36
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230437"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Gerenciar o Skype for Business online com o PowerShell

*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*

Uma das principais tarefas de qualquer administrador do Skype for Business online é gerenciar políticas. Embora você possa realizar algumas dessas tarefas no centro de administração do Microsoft 365, outras tarefas são muito mais rápidas e fáceis no PowerShell. 

## <a name="before-you-start"></a>Antes de começar

Baixe e instale o [módulo do conector do Skype for Business online](https://www.microsoft.com/download/details.aspx?id=39366)e reinicie o computador.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Conectar-se usando um nome e senha da conta de administrador do Skype for Business Online

1. Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos: 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Na caixa de diálogo **solicitação de credencial do Windows PowerShell** , digite seu nome e senha da conta de administrador do Skype for Business Online e clique em **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>Conectar-se usando uma conta de administrador do Skype for Business online com a autenticação multifator

1. Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Quando solicitado pelo comando **New-CsOnlineSession** , insira seu nome de conta de administrador do Skype for Business online.

3. Na caixa de diálogo **entrar na conta** , digite sua senha de administrador do Skype for Business Online e clique em **entrar**.

4. Siga as instruções na caixa de diálogo **entrar na conta** para fornecer informações de autenticação adicionais, como um código de verificação, e clique em **verificar**.

Para mais informações, confira os seguintes tópicos:
  
- [Gerenciar as políticas do Skype for Business online com o PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Atribuir políticas do Skype for Business online por usuário com o PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Confira também

[Gerenciar o Microsoft 365 com o PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao PowerShell para o Microsoft 365](getting-started-with-office-365-powershell.md)

[Referências do cmdlet do PowerShell do Skype for Business](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

