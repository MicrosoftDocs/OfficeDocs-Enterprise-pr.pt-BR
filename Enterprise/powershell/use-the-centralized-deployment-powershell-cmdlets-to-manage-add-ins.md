---
title: Usar os cmdlets do PowerShell de Implantação Centralizada para gerenciar suplementos
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Use os cmdlets do PowerShell de implantação centralizada para ajudá-lo a implantar e gerenciar suplementos do Office para sua organização do Office 365.
ms.openlocfilehash: 3d6495646c6ce0a1d15f2d911f1fa8af92e3c2c6
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782581"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Usar os cmdlets do PowerShell de Implantação Centralizada para gerenciar suplementos

Como um administrador do Office 365, você pode implantar suplementos do Office para usuários por meio do recurso de implantação centralizada (consulte [Manage Deployment of Office 365 Add-ins no centro de administração](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). Além de implantar os suplementos do Office por meio do centro de administração, você também pode usar o Microsoft PowerShell. [Baixe](https://go.microsoft.com/fwlink/p/?linkid=850850) os cmdlets do PowerShell de implantação centralizada no centro de download da Microsoft. 
  
## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

[Conectar-se usando suas credenciais de administrador](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[Carregar um manifesto de suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Carregar um suplemento da Office Store](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[Obter detalhes de um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[Ativar ou desativar um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[Adicionar ou remover usuários de um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[Atualizar um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[Excluir um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[Obter ajuda detalhada para cada cmdlet](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>Conectar-se usando suas credenciais de administrador
<a name="BKMK_Connect"> </a>

Antes de poder usar os cmdlets de implantação centralizada, você precisa entrar.
  
1. Inicie o PowerShell.
    
2. Conecte-se ao PowerShell usando as credenciais de administrador da sua empresa. Execute o cmdlet a seguir.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Na página **Inserir credenciais** , digite suas credenciais de administrador global do Office 365. Como alternativa, você pode inserir suas credenciais diretamente no cmdlet. 
    
    Execute o cmdlet a seguir especificando suas credenciais de administrador de empresa como um objeto PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Para obter mais informações sobre como usar o PowerShell, confira [conectar-se ao Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Carregar um manifesto de suplemento
<a name="BKMK_UploadManifest"> </a>

Execute o cmdlet New-OrganizationAdd-in para carregar um manifesto de suplemento a partir de um caminho, que pode ser um local de arquivo ou uma URL. O exemplo a seguir mostra um local de arquivo para o valor do parâmetro _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Você também pode executar o cmdlet New-OrganizationAdd-in para carregar um suplemento e atribuí-lo a usuários ou grupos diretamente usando o parâmetro _Members_ , conforme mostrado no exemplo a seguir. Separe os endereços de email dos membros com uma vírgula. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Carregar um suplemento da Office Store
<a name="BKMK_UploadAddin"> </a>

Execute o cmdlet New-OrganizationAddIn para carregar um manifesto da Office Store.
  
No exemplo a seguir, o cmdlet New-OrganizationAddIn especifica o AssetID de um suplemento para um local dos Estados Unidos e o mercado de conteúdo.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Para determinar o valor para o __ parâmetro AssetID, você pode copiá-lo da URL da página da Web da Office Store para o suplemento. AssetIds sempre começa com "WA" seguido por um número. Por exemplo, no exemplo anterior, a origem para o valor AssetID de WA104099688 é a URL da página da Web da Office Store para o suplemento: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Os valores para o parâmetro _locale_ e o parâmetro _ContentMarket_ são idênticos e indicam o país/região para o qual você está tentando instalar o suplemento. O formato é en-US, fr-FR. e assim por diante. 
  
> [!NOTE]
> Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Obter detalhes de um suplemento
<a name="BKMK_GetDetails"> </a>

Execute o cmdlet Get-OrganizationAddIn conforme mostrado abaixo para obter detalhes de todos os suplementos carregados no locatário, incluindo a ID de produto de um suplemento.
  
```
Get-OrganizationAddIn
```

Execute o cmdlet Get-OrganizationAddIn com um valor para o parâmetro _ProductID_ para especificar o suplemento para o qual você deseja recuperar detalhes. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Para obter detalhes completos de todos os suplementos, além dos usuários e grupos atribuídos, canalize a saída do cmdlet Get-OrganizationAddIn para o cmdlet Format-List, conforme mostrado no exemplo a seguir.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Ativar ou desativar um suplemento
<a name="BKMK_TurnOnOff"> </a>

Para desativar um suplemento para que os usuários e grupos atribuídos a ele não tenham mais acesso, execute o cmdlet Set-OrganizationAddIn com o parâmetro _ProductID_ e o parâmetro _Enabled_ definido como `$false`, conforme mostrado no exemplo a seguir.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Para ativar um suplemento novamente, execute o mesmo cmdlet com o parâmetro _Enabled_ definido como `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Adicionar ou remover usuários de um suplemento
<a name="BKMK_AddRemove"> </a>

Para adicionar usuários e grupos a um suplemento específico, execute o cmdlet Set-OrganizationAddInAssignments com os parâmetros _ProductID_, _Add_e Members __ . Separe os endereços de email dos membros com uma vírgula. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para remover usuários e grupos, execute o mesmo cmdlet usando o parâmetro _Remove_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para atribuir um suplemento a todos os usuários no locatário, execute o mesmo cmdlet usando o parâmetro _AssignToEveryone_ com o valor definido como `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Para não atribuir um suplemento a todos e reverter para os usuários e grupos atribuídos anteriormente, você pode executar o mesmo cmdlet e desativar o parâmetro _AssignToEveryone_ definindo seu valor como `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Atualizar um suplemento
<a name="BKMK_UpdateAddin"> </a>

Para atualizar um suplemento de um manifesto, execute o cmdlet Set-OrganizationAddIn com os parâmetros _ProductID_, _ManifestPath_e _locale_ , conforme mostrado no exemplo a seguir. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store. 
  
## <a name="delete-an-add-in"></a>Excluir um suplemento
<a name="BKMK_Delete"> </a>

Para excluir um suplemento, execute o cmdlet Remove-OrganizationAddIn com o parâmetro _ProductID_ , conforme mostrado no exemplo a seguir. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Obter ajuda detalhada para cada cmdlet
<a name="BKMK_GetHelp"> </a>

Você pode examinar a ajuda detalhada para cada cmdlet usando o cmdlet Get-Help. Por exemplo, o cmdlet a seguir fornece informações detalhadas sobre o cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


