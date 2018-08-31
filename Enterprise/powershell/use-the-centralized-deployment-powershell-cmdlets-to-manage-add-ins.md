---
title: Use os cmdlets do PowerShell centralizados de implantação para gerenciar suplementos
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Use os cmdlets do PowerShell centralizados de implantação para ajudá-lo a implantar e gerenciar suplementos do Office para sua organização do Office 365.
ms.openlocfilehash: f15bd1048d9240a125a1ae8245c773d83c6c935d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539163"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Use os cmdlets do PowerShell centralizados de implantação para gerenciar suplementos

Como um administrador do Office 365, você pode implantar os suplementos do Office para usuários por meio da implantação do centralizados recurso (consulte [Gerenciar a implantação de suplementos do Office 365 no Centro de administração do Office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). Além de implantação de suplementos do Office por meio do Centro de administração do Office 365, você também pode usar o Microsoft PowerShell. [Baixe](https://go.microsoft.com/fwlink/p/?linkid=850850) os cmdlets do PowerShell centralizados de implantação do Microsoft Download Center. 
  
## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

[Conectar usando suas credenciais de administrador](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[Carregar um suplemento manifesto](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Carregar um suplemento da Office Store](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[Obtenha detalhes de um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[Ativar ou desativar um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[Adicionar ou remover usuários de um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[Atualizar um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[Excluir um suplemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[Obtenha ajuda detalhada para cada cmdlet](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>Conectar usando suas credenciais de administrador
<a name="BKMK_Connect"> </a>

Antes de poder usar os cmdlets centralizados de implantação, você precisa entrar.
  
1. Inicie o PowerShell.
    
2. Conecte-se ao PowerShell usando suas credenciais de administrador da empresa. Execute o seguinte cmdlet.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Na página **Inserir credenciais** , insira suas credenciais de administrador global do Office 365. Como alternativa, você pode inserir suas credenciais diretamente para o cmdlet. 
    
    Execute o seguinte cmdlet especificando a sua empresa credenciais de administrador, como um objeto PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Para obter mais informações sobre como usar o PowerShell, consulte [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Carregar um suplemento manifesto
<a name="BKMK_UploadManifest"> </a>

Execute o cmdlet New-OrganizationAdd-In para carregar um suplemento de manifesto de um caminho, que pode ser um local de arquivo ou uma URL. O exemplo a seguir mostra um local de arquivo para o valor do parâmetro _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Você também pode executar o cmdlet New-OrganizationAdd-In para carregar um add-in e atribuí-lo a usuários ou grupos usando o parâmetro _Members_ , conforme mostrado no exemplo a seguir. Separe os endereços de email dos membros com uma vírgula. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Carregar um suplemento da Office Store
<a name="BKMK_UploadAddin"> </a>

Execute o cmdlet New-OrganizationAddIn para carregar um manifesto da Office Store.
  
No exemplo a seguir, o cmdlet New-OrganizationAddIn Especifica o AssetId para um suplemento para um mercado local e o conteúdo de Estados Unidos.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Para determinar o valor do parâmetro _AssetId_ , você pode copiar da URL do repositório do Office webpage para AssetIds o suplemento sempre começam com "WA" seguido por um número. Por exemplo, no exemplo anterior, a fonte para o valor de AssetId do WA104099688 é a URL de página da Web do Office Store para o suplemento: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Os valores para o parâmetro _Locale_ e o parâmetro _ContentMarket_ são idênticos e indicam o país/região que você está tentando instalar o suplemento de. O formato é en-US, fr-FR. e assim por diante. 
  
> [!NOTE]
> Suplementos carregados da Office Store atualizará automaticamente dentro de alguns dias após a atualização mais recente que está sendo disponíveis no Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Obtenha detalhes de um suplemento
<a name="BKMK_GetDetails"> </a>

Execute o cmdlet Get-OrganizationAddIn, conforme mostrado a seguir obter detalhes de todos os suplementos carregados para o inquilino, incluído ID do produto. de um suplemento
  
```
Get-OrganizationAddIn
```

Execute o cmdlet Get-OrganizationAddIn com um valor para o parâmetro _ProductId_ especificar qual suplemento se deseja recuperar os detalhes de. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Para obter detalhes completos de todos os suplementos plus a usuários e grupos atribuídos, canalize a saída do cmdlet Get-OrganizationAddIn para o cmdlet Format-List, conforme mostrado no exemplo a seguir.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Ativar ou desativar um suplemento
<a name="BKMK_TurnOnOff"> </a>

Para desativar um suplemento para usuários e grupos que são atribuídos a ela não terá mais acesso, execute o cmdlet Set-OrganizationAddIn com o parâmetro _ProductId_ e o parâmetro _Enabled_ definido como `$false`, conforme mostrado no exemplo a seguir.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Para ativar um add-in novamente, execute o cmdlet a mesmo com o parâmetro _Enabled_ definido como `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Adicionar ou remover usuários de um suplemento
<a name="BKMK_AddRemove"> </a>

Para adicionar usuários e grupos para um suplemento específico, execute o cmdlet Set-OrganizationAddInAssignments com os parâmetros _ProductId_, _Adicionar_e _membros_ . Separe os endereços de email dos membros com uma vírgula. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para remover usuários e grupos, execute o cmdlet mesmo usando o parâmetro _Remover_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para atribuir um suplemento para todos os usuários no locatário do, execute o cmdlet mesmo usando o parâmetro _AssignToEveryone_ com o valor definido como `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Para não atribuir um suplemento para todos e reverter para os usuários atribuídos anteriormente e grupos, você pode executar o cmdlet mesmo e desativar o parâmetro _AssignToEveryone_ definindo seu valor como `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Atualizar um suplemento
<a name="BKMK_UpdateAddin"> </a>

Para atualizar um add-in de um manifesto, execute o cmdlet Set-OrganizationAddIn com o _ProductId_, _ManifestPath_e parâmetros de _localidade_ , conforme mostrado no exemplo a seguir. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Suplementos carregados da Office Store atualizará automaticamente dentro de alguns dias após a atualização mais recente que está sendo disponíveis no Office Store. 
  
## <a name="delete-an-add-in"></a>Excluir um suplemento
<a name="BKMK_Delete"> </a>

Para excluir um add-in, execute o cmdlet Remove-OrganizationAddIn com o parâmetro _ProductId_ , conforme mostrado no exemplo a seguir. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Obtenha ajuda detalhada para cada cmdlet
<a name="BKMK_GetHelp"> </a>

Você pode consultar a ajuda detalhada para cada cmdlet usando o cmdlet Get-help. Por exemplo, o cmdlet a seguir fornece informações detalhadas sobre o cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


