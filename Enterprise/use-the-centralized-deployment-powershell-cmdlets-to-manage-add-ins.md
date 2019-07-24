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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Use os cmdlets do PowerShell de implantação centralizada para ajudá-lo a implantar e gerenciar suplementos do Office para sua organização do Office 365.
ms.openlocfilehash: 301e44da4c663fa54c4e2b753552b0b345e2a6e5
ms.sourcegitcommit: 9cd3dcf1e90b21c7651d367dcd3306d6fe0bcbcb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "35834231"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Usar os cmdlets do PowerShell de Implantação Centralizada para gerenciar suplementos

Como um administrador global da Microsoft 365 ou do Exchange, você pode implantar suplementos do Office para usuários por meio do recurso de implantação centralizada (Confira [implantar suplementos do Office no centro de administração](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Além de implantar os suplementos do Office por meio do centro de administração do Microsoft 365, você também pode usar o Microsoft PowerShell. Instale o [módulo de implantação de suplemento centralizado do O365 para o Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

Depois de baixar o módulo, abra uma janela do Windows PowerShell regular e execute o seguinte cmdlet:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>Conectar-se usando suas credenciais de administrador

Antes de poder usar os cmdlets de implantação centralizada, você precisa entrar.
  
1. Inicie o PowerShell.
    
2. Conecte-se ao PowerShell usando as credenciais de administrador da sua empresa. Execute o cmdlet a seguir.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. Na página **Inserir credenciais** , digite suas credenciais de administrador global do Office 365. Como alternativa, você pode inserir suas credenciais diretamente no cmdlet. 
    
    Execute o cmdlet a seguir especificando suas credenciais de administrador de empresa como um objeto PSCredential.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Para obter mais informações sobre como usar o PowerShell, confira [conectar-se ao Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Carregar um manifesto de suplemento

Execute o cmdlet **New-OrganizationAdd-in** para carregar um manifesto de suplemento a partir de um caminho, que pode ser um local de arquivo ou uma URL. O exemplo a seguir mostra um local de arquivo para o valor do parâmetro _ManifestPath_ . 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Você também pode executar o cmdlet **New-OrganizationAdd-in** para carregar um suplemento e atribuí-lo a usuários ou grupos diretamente usando o parâmetro _Members_ , conforme mostrado no exemplo a seguir. Separe os endereços de email dos membros com uma vírgula. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Carregar um suplemento da Office Store

Execute o cmdlet **New-OrganizationAddIn** para carregar um manifesto da Office Store.
  
No exemplo a seguir, o cmdlet **New-OrganizationAddIn** especifica o AssetID de um suplemento para um local dos Estados Unidos e o mercado de conteúdo.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Para determinar o valor para o __ parâmetro AssetID, você pode copiá-lo da URL da página da Web da Office Store para o suplemento. AssetIds sempre começa com "WA" seguido por um número. Por exemplo, no exemplo anterior, a origem para o valor AssetID de WA104099688 é a URL da página da Web da Office Store para o suplemento: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Os valores para o parâmetro _locale_ e o parâmetro _ContentMarket_ são idênticos e indicam o país/região para o qual você está tentando instalar o suplemento. O formato é en-US, fr-FR. e assim por diante. 
  
> [!NOTE]
> Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Obter detalhes de um suplemento

Execute o cmdlet **Get-OrganizationAddIn** conforme mostrado abaixo para obter detalhes de todos os suplementos carregados no locatário, incluindo a ID de produto de um suplemento.
  
```powershell
Get-OrganizationAddIn
```

Execute o cmdlet **Get-OrganizationAddIn** com um valor para o parâmetro _ProductID_ para especificar o suplemento para o qual você deseja recuperar detalhes. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Para obter detalhes completos de todos os suplementos, além dos usuários e grupos atribuídos, canalize a saída do cmdlet **Get-OrganizationAddIn** para o cmdlet Format-List, conforme mostrado no exemplo a seguir.
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Ativar ou desativar um suplemento

Para desativar um suplemento para que os usuários e grupos atribuídos a ele não tenham mais acesso, execute o cmdlet **set-OrganizationAddIn** com o parâmetro _ProductID_ e o parâmetro _Enabled_ definido como `$false`, conforme mostrado no exemplo a seguir .
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Para ativar um suplemento novamente, execute o mesmo cmdlet com o parâmetro _Enabled_ definido como `$true`.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Adicionar ou remover usuários de um suplemento

Para adicionar usuários e grupos a um suplemento específico, execute o cmdlet **set-OrganizationAddInAssignments** com os parâmetros _ProductID_, _Add_e Members __ . Separe os endereços de email dos membros com uma vírgula. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para remover usuários e grupos, execute o mesmo cmdlet usando o parâmetro _Remove_ . 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para atribuir um suplemento a todos os usuários no locatário, execute o mesmo cmdlet usando o parâmetro _AssignToEveryone_ com o valor definido como `$true`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Para não atribuir um suplemento a todos e reverter para os usuários e grupos atribuídos anteriormente, você pode executar o mesmo cmdlet e desativar o parâmetro _AssignToEveryone_ definindo seu valor como `$false`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Atualizar um suplemento

Para atualizar um suplemento de um manifesto, execute o cmdlet **set-OrganizationAddIn** com os parâmetros _ProductID_, _ManifestPath_e _locale_ , conforme mostrado no exemplo a seguir. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Os suplementos carregados da Office Store serão atualizados automaticamente em alguns dias da última atualização disponível na Office Store. 
  
## <a name="delete-an-add-in"></a>Excluir um suplemento

Para excluir um suplemento, execute o cmdlet **Remove-OrganizationAddIn** com o parâmetro _ProductID_ , conforme mostrado no exemplo a seguir. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a>Personalizar suplementos da Microsoft Store para sua organização

Você deve personalizar o suplemento antes de implantá-lo em sua organização. Os suplementos mais antigos do que a versão 1,1 não são suportados por este recurso. 

Recomendamos que você implante primeiro um suplemento personalizado para se certificar de que ele funcione conforme o esperado antes de implantá-lo em toda a organização.

Observe também as seguintes restrições:
- Todas as URLs devem ser absolutas (incluir http ou HTTPS) e válidas.
- *DisplayName* não deve exceder 125 caracteres 
- *DisplayName*, ** Resources e *AppDomains* não devem incluir os seguintes caracteres: 
 
    - \<
    -  \>
    -  ;
    -  =   

Se você quiser personalizar um suplemento implantado, será necessário desinstalá-lo no centro de administração e, em seguida, consulte [remover um suplemento do cache local](#remove-an-add-in-from-local-cache) para obter etapas para removê-lo de cada computador no qual foi implantado.

Para personalizar um suplemento, execute o cmdlet **set – OrganizationAddInOverrides** com o *ProductID* como um parâmetro, seguido da marca que você deseja substituir e o novo valor. Para saber como obter o *ProductID* , confira [obter detalhes de um suplemento](#get-details-of-an-add-in) neste artigo. Por exemplo:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
Para personalizar várias marcas de um suplemento, adicione essas marcas à linha de comando:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> Você deve aplicar várias marcas personalizadas a um suplemento como um comando. Se você personalizar as marcas um por um, somente a última personalização será aplicada. Além disso, se você personalizar uma marca por engano, você deve remover todas as personalizações e começar novamente.

### <a name="tags-you-can-customize"></a>Marcas que você pode personalizar

| Tag                  | Descrição          |
| :------------------- | :------------------- |
| \<> IconURL   </br>| A URL da imagem usada como o ícone do suplemento (no centro de administração). </br> |
| \<> DisplayName| O título do suplemento (no centro de administração).|
| \<Hospeda>| Lista de aplicativos que oferecerão suporte ao suplemento.|
| \<> SourceLocation | A URL de origem à qual o suplemento será conectado.| 
| \<> AppDomains | Uma lista de domínios com os quais o suplemento pode se conectar. | 
| \<> SupportURL| A URL que os usuários podem usar para acessar a ajuda e suporte. | 
| \<Recursos>  | Essa marca contém vários elementos, incluindo títulos, dicas de ferramentas e ícones de tamanhos diferentes.| 
|
### <a name="customize-resources-tag"></a>Marca personalizar recursos

Qualquer elemento na <Resources> marca do manifesto pode ser personalizado dinamicamente. Primeiro, você precisa verificar o manifesto para localizar a ID do elemento ao qual você deseja atribuir um novo valor. A <Resources> marca tem a seguinte aparência:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
Nesse caso, a ID do elemento para a imagem é "img16icon" e o valor associado a ela é "http:<i></i>//site. <i> </i>com/img. jpg. "

Depois de identificar os elementos que você deseja personalizar, use o seguinte comando no PowerShell para atribuir novos valores aos elementos:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

Você pode personalizar tantos elementos com o comando quanto necessário.

### <a name="remove-customization-from-an-add-in"></a>Remover a personalização de um suplemento

A única opção disponível atualmente para excluir personalizações é excluir todas elas de uma só vez:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a>Exibir personalizações de suplementos

Para exibir uma lista de personalizações aplicadas, execute o cmdlet **Get-OrganizationAddInOverrides** . Se **Get-OrganizationAddInOverrides** for executado sem um *ProductID* , uma lista de todos os suplementos com substituições aplicadas será retornada.  

```powershell
Get-OrganizationAddInOverrides 
```
Se ProductId for especificado, uma lista de substituições aplicada a esse suplemento será retornada. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a>Remover um suplemento do cache local

Se um suplemento tiver sido implantado, ele deve ser removido do cache em cada computador antes que ele possa ser personalizado. Para remive um suplemento do cache:

1. Navegue até a pasta "usuários" em C:\ 
1. Vá para a pasta do usuário
1. Navegue até AppData\Local\Microsoft\Office e selecione a pasta associada à sua versão do Office
1. Na pasta *WEF* , exclua ** a pasta manifestos.

## <a name="get-detailed-help-for-each-cmdlet"></a>Obter ajuda detalhada para cada cmdlet

Você pode examinar a ajuda detalhada para cada cmdlet usando o cmdlet Get-Help. Por exemplo, o cmdlet a seguir fornece informações detalhadas sobre o cmdlet Remove-OrganizationAddIn.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


