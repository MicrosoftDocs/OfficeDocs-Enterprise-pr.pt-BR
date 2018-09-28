---
title: Gerenciar o Skype for Business Online com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumo: Use o Office 365 PowerShell para gerenciar as políticas do Skype for Business online, políticas por usuário e configurações da reunião.'
ms.openlocfilehash: a91803316972337aa31e2b979f841ac1cfbe8566
ms.sourcegitcommit: 053db5479f93478a65d4c36ffe44c6a7bcb60e3c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "23965188"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Gerenciar o Skype for Business Online com o Office 365 PowerShell

 **Resumo:** use o Office 365 PowerShell para gerenciar as políticas do Skype for Business Online, políticas por usuário e configurações de reunião.
  
Uma das tarefas de qualquer Skype para Business Online administrador primárias está gerenciando políticas. Embora você possa realizar algumas dessas tarefas no Centro de administração do Office 365, outras tarefas são muito mais rápido e fácil no Office 365 PowerShell. 

## <a name="before-you-start"></a>Antes de começar

Baixar e instalar o [Skype para módulo Business Connector Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366)e reinicie o computador se solicitado.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Conectar usando um Skype para senha e nome da conta de administrador Business Online

1. Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Na caixa de diálogo **Solicitação de credencial do Windows PowerShell** , digite sua Skype Business Online nome da conta de administrador e senha e clique em **Okey**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Conectar usando um Skype para conta de administrador Business Online com a autenticação multifator

1. Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Quando solicitado pelo comando **New-CsOnlineSession** , insira seu Skype do nome da conta de administrador Business Online.

3. Na caixa de diálogo **entrar em sua conta** , digite sua Skype Business Online senha de administrador e clique em **entrar**.

4. Siga as instruções na caixa de diálogo **entrar em sua conta** para fornecer informações de autenticação adicionais, como um código de verificação e clique em **Verificar**.

Para saber mais, confira os seguintes tópicos:
  
- [Gerenciar as políticas do Skype for Business Online com o Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>See also

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

[Skype para referências de cmdlet do PowerShell de negócios](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

