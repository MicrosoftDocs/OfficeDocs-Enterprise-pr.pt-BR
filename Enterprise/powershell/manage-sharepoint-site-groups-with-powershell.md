---
title: Manage SharePoint Online site groups with Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Resumo: Usar o PowerShell do Office 365 para gerenciar grupos de sites do SharePoint Online.'
ms.openlocfilehash: c68e0905c0abcbea279829be7c841c31409db6cf
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975139"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Manage SharePoint Online site groups with Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para gerenciar grupos de sites do SharePoint Online.
  
Embora você possa usar o Centro de administração do Office 365, você também pode usar o Office 365 PowerShell para gerenciar os grupos de sites do SharePoint Online.

## <a name="before-you-begin"></a>Antes de começar

Os procedimentos neste artigo exigem que você se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Modo de exibição SharePoint Online com o Office 365 PowerShell

Centro de administração do SharePoint Online tem alguns métodos fácil de usar para gerenciar grupos de sites. Por exemplo, suponha que você deseja examinar os grupos e os membros do grupo, o `https://litwareinc.sharepoint.com/sites/finance` site. Aqui está o que você deve fazer para:

1. No Centro de administração do Office 365, clique em **recursos** > **Sites**e, em seguida, clique na URL do site.
2. Na caixa de diálogo do conjunto de sites, clique em **Ir para este site**.
3. Na página do site, clique no ícone **configurações** (localizado no canto superior direito da página) e clique em **configurações do Site**:<br/>
![Configurações de site do SharePoint Online](media/spo-site-settings.png)<br/>
4. Na página Configurações do Site, clique em **permissões de Sites** em **usuários e permissões**.

E, em seguida, repita o processo para o próximo site que você deseja examinar.

Para obter uma lista dos grupos com o Office 365 PowerShell, você usaria o seguinte conjunto de comando:

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Há duas maneiras de executar este comando definir no prompt de comando do Shell de gerenciamento do SharePoint Online:

- Copie os comandos no bloco de notas (ou outro editor de texto), modifique o valor da variável **$siteURL** , selecione os comandos e cole-os no prompt de comando do Shell de gerenciamento do SharePoint Online. Quando você fizer isso, o PowerShell será interrompida a um **>>** prompt. Pressione Enter para executar o comando **foreach** .<br/>
- Copie os comandos no bloco de notas (ou outro editor de texto), modifique o valor da variável **$siteURL** e, em seguida, salve o arquivo de texto com um nome e a extensão. ps1 em uma pasta adequada. Em seguida, execute o script no prompt de comando do Shell de gerenciamento do SharePoint Online especificando seu nome de arquivo e caminho. Aqui está um exemplo de comando:

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

Em ambos os casos, você verá algo semelhante a esta:

![Grupos de sites do SharePoint Online](media/SPO-site-groups.png)

Esses são todos os grupos que foram criados para o site `https://litwareinc.sharepoint.com/sites/finance`, assim como todos os usuários atribuídos a esses grupos. Os nomes de grupo são em amarelo para ajudá-lo nomes de grupo separado de seus membros.

Como outro exemplo, aqui está um conjunto de comandos que lista os grupos e todas as associações de grupo, para todos os sites do SharePoint Online.

```
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a>Confira também

[Conectar ao PowerShell do SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Criar sites do SharePoint Online e adicionar usuários com o Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

