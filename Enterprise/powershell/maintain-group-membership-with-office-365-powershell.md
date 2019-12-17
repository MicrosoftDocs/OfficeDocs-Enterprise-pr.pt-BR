---
title: Manter Associação de grupo com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Saiba como usar o Office 365 PowerShell para manter a associação em grupos do Office 365.
ms.openlocfilehash: e7cd4cb76f28bfbe2e1bc538df6727ac403c29df
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072493"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a>Manter Associação de grupo com o Office 365 PowerShell

Você pode usar o Office 365 PowerShell como uma alternativa para o centro de administração do Microsoft 365 para manter a associação de grupo no Office 365. 

> [!TIP]
> Para gerar comandos do PowerShell prontos para execução especificando os nomes de conta e de grupo do usuário, use esta [pasta de trabalho de manutenção de grupo do Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx). 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico
Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Adicionar ou remover contas de usuário como membros de um grupo

**Para adicionar uma conta de usuário por seu UPN**, preencha o nome principal do usuário (UPN) da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo, removendo os caracteres "<" e ">" e execute esses comandos na janela do PowerShell ou no ISE (ambiente de script integrado) do PowerShell.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para adicionar uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para remover uma conta de usuário por seu UPN**, preencha o UPN da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para remover uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Adicionar ou remover grupos como membros de um grupo

Os grupos de segurança podem conter outros grupos como membros. No entanto, os grupos do Office 365 não podem. Esta seção contém comandos do PowerShell para adicionar ou remover grupos apenas de um grupo de segurança.

**Para adicionar um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você adicionará e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para remover um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você vai remover e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Adicionar ou remover contas de usuário como membros de um grupo

**Para adicionar uma conta de usuário por seu UPN**, preencha o nome principal do usuário (UPN) da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo, removendo os caracteres "<" e ">" e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para adicionar uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para remover uma conta de usuário por seu UPN**, preencha o UPN da conta de usuário (exemplo: belindan@contoso.com) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para remover uma conta de usuário pelo seu nome de exibição**, preencha o nome de exibição da conta de usuário (exemplo: Belinda Newman) e o nome de exibição do grupo e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Adicionar ou remover grupos como membros de um grupo

Os grupos de segurança podem conter outros grupos como membros. No entanto, os grupos do Office 365 não podem. Esta seção contém comandos do PowerShell para adicionar ou remover grupos apenas de um grupo de segurança.

**Para adicionar um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você adicionará e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**Para remover um grupo por seu nome de exibição**, preencha o nome de exibição do grupo que você vai remover e o nome de exibição do grupo que conterá o grupo de membros e execute esses comandos na janela do PowerShell ou no ISE do PowerShell.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Confira também

[Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

