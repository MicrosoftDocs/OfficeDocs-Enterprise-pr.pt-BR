---
title: Mover um site de OneDrive para um local diferente de geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Aprenda a mover um site de OneDrive para uma localização geográfica diferente.
ms.openlocfilehash: a31f683170fdb83dac90e9d09884c3020d1a47b1
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Mover um site de OneDrive para um local diferente de geo 

Com o OneDrive geo mover, você pode mover OneDrive um usuário para um local diferente geo. OneDrive geo movimentação é executada pelo administrador do SharePoint Online ou o administrador global do Office 365. Antes de iniciar um OneDrive geo mover, certifique-se de notificar o usuário que está sendo movido cujo OneDrive e recomendar que eles fecharem todos os arquivos para a duração da movimentação. (Se o usuário tem um documento aberto usando o cliente do Office durante a movimentação, então após mover o documento precisará ser salvo para o novo local de conclusão.) A movimentação pode ser agendada para um tempo futuro, se desejado.

O serviço do OneDrive usa o armazenamento de Blob do Windows Azure para armazenar o conteúdo. O blob de armazenamento associado ao OneDrive do usuário será movido da origem de local geo de destino dentro de 40 dias do OneDrive sendo disponíveis para o usuário de destino. O acesso ao OneDrive do usuário será restaurado tão logo o destino OneDrive está disponível.

Durante a janela de movimentação do OneDrive geo (cerca de 2 a 6 horas) OneDrive do usuário é definido como somente leitura. O usuário ainda pode acessar os arquivos por meio do seu site de OneDrive no SharePoint Online ou o cliente de sincronização do OneDrive. Quando OneDrive geo movimentação for concluída, o usuário será automaticamente conectado ao seu OneDrive no local geo destino quando navegarem para o OneDrive no iniciador de aplicativo do Office 365. O cliente de sincronização começará automaticamente a sincronização de um novo local.

Os procedimentos neste artigo exigem o [Módulo de PowerShell Online do Microsoft SharePoint](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

## <a name="moving-a-onedrive-site"></a>Mover um site de OneDrive

Para executar um OneDrive geo mover, o administrador de locatário defina primeiro preferencial a localização de dados (PDL) do usuário para o local de geo apropriado. Depois que o PDL estiver definida, aguarde pelo menos 24 horas para a atualização PDL a sincronização entre os locais de geo antes de iniciar a movimentação de geo OneDrive.

Quando usando o geo mover cmdlets, conecte ao serviço do SPO no local de geo OneDrive atual do usuário, usando a seguinte sintaxe:

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Por exemplo: para mover OneDrive do usuário 'Matt@contosoenergy.onmicrosoft.com', conecte-se ao centro de administração do SharePoint EUR como OneDrive do usuário está no local de geo EUR:

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>Validando o ambiente

Antes de começar a mover um geo OneDrive, é recomendável que você valide o ambiente.

Para garantir que todos os locais de geo são compatíveis, execute:

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

Se um OneDrive está em retenção legal ou se ele contiver um subsite, ele não pode ser movido. Você pode usar o cmdlet Start-SPOUserAndContentMove com o parâmetro - ValidationOnly para validar se o OneDrive for capaz de ser movida:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Isso retornará o sucesso se OneDrive está pronta para ser movido ou falhar se houver uma retenção legal ou subsite que impediria a movimentação. Depois que você tenha validado que o OneDrive está pronto para migrar, você pode iniciar a movimentação.

## <a name="start-a-onedrive-geo-move"></a>Iniciar uma movimentação de geo OneDrive

Para iniciar a movimentação, execute:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Usando esses parâmetros:

-   _UserPrincipalName_ – UPN do usuário cujo OneDrive está sendo movido.

-   _DestinationDataLocation_ – localização geográfica onde o OneDrive precisa ser movido. Este deve ser igual ao local dos dados preferencial do usuário.

> [!NOTE]
> É recomendável executar `Get-SPOGeoMoveStateCompatibility` com `ValidationOnly` antes de iniciar o OneDrive geo mover.

Por exemplo, para mover o OneDrive de matt@contosoenergy.onmicrosoft.com de EUR para Austrália, execute:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

Para agendar uma movimentação geo por um tempo posterior, use um dos parâmetros a seguir:

-   _PreferredMoveBeginDate_ – a movimentação provavelmente começar neste momento especificado.

-   _PreferredMoveEndDate_ – a movimentação provavelmente ser concluídas por neste momento especificado, em uma base de esforço recomendada.

## <a name="cancel-a-onedrive-geo-move"></a>Cancelar uma movimentação de geo OneDrive 

Você pode interromper a movimentação geo do OneDrive de um usuário, desde que a movimentação não está em andamento ou concluído usando o cmdlet:

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

Onde o _UserPrincipalName_ é o UPN do usuário cujo OneDrive mover que você deseja parar.

## <a name="determining-current-status"></a>Determinando o status atual

Você pode verificar o status de um OneDrive geo mover ou sair do geo que você está conectado usando o cmdlet Get-SPOUserAndContentMoveState.

Os status de movimentação são descritos na tabela a seguir.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Status</strong></th>
<th align="left"><strong>Descrição</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">A movimentação não foi iniciada.</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">A movimentação está em andamento em um dos seguintes estados: validação (1/4) (2/4) de Backup, restaurar (3 4), limpeza (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Sucesso</td>
<td align="left">A movimentação foi concluída com êxito.</td>
</tr>
<tr class="even">
<td align="left">Com falha</td>
<td align="left">A movimentação falhou.</td>
</tr>
</tbody>
</table>

Para localizar o status de movimentação de um usuário específico, use o parâmetro UserPrincipalName:

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Para localizar o status de todas as movimentações ou sair geo local que você está conectado, use o parâmetro MoveState com um dos seguintes valores: NotStarted, InProgress, êxito, falha, todos os.

`Get-SPOUserAndContentMoveState -MoveState <value>`

Você também pode adicionar o `-Verbose` parâmetro para obter descrições mais detalhadas do estado de movimentação.

## <a name="user-experience"></a>Experiência do Usuário

Os usuários do OneDrive devem observar um mínimo de interrupção se seus OneDrive for movido para um local diferente geo. Além de um estado somente leitura breve durante a movimentação, permissões e os vínculos existentes continuarão funcionando como esperado depois que a movimentação é concluída.

### <a name="onedrive-for-business"></a>OneDrive for Business

Enquanto a movimentação está em andamento OneDrive do usuário é definido como somente leitura. Depois que a movimentação é concluída, o usuário seja direcionado para seu OneDrive no novo local geo quando navegarem para o OneDrive o iniciador de aplicativo do Office 365 ou um navegador da web.

### <a name="permissions-on-onedrive-content"></a>Permissões de conteúdo do OneDrive

Usuários com permissões para o conteúdo de OneDrive continuará a ter acesso ao conteúdo durante a movimentação, e depois que ela for concluída.

### <a name="onedrive-sync-client"></a>Cliente de sincronização do OneDrive 

O cliente de sincronização do OneDrive detectará automaticamente e transferir uniformemente está sincronizando para o novo local de OneDrive depois que a movimentação de geo OneDrive for concluída. O usuário não precisa entrar novamente ou executar qualquer outra ação.

Se um usuário atualiza um arquivo enquanto a movimentação de geo OneDrive está em andamento, o cliente de sincronização notificará-los que carregamentos de arquivo estão pendentes enquanto a movimentação está em andamento.

### <a name="sharing-links"></a>Compartilhamento de links 

Após a OneDrive geo mover conclusão, os vínculos existentes de compartilhado para os arquivos que foram movidos automaticamente redirecionará para o novo local de geo.

### <a name="onenote-experience"></a>Experiência do OneNote 

Cliente do OneNote win32 e UWP (Universal) App detectará automaticamente e perfeitamente sincronizar blocos de anotações para o novo local de OneDrive depois que o OneDrive geo movimentação está concluída. O usuário não precisa entrar novamente ou executar qualquer outra ação. O indicador visível somente para o usuário é sincronização de notebook falhará quando OneDrive geo movimentação está em andamento. Esta experiência está disponível nas seguintes versões de cliente do OneNote:

-   OneNote win32 – versão 16.0.8326.2096 (e posterior)

-   OneNote UWP – versão 16.0.8431.1006 (e posterior)

-   OneNote Mobile App – versão 16.0.8431.1011 (e posterior)

### <a name="teams-app"></a>Aplicativo de equipes

Após OneDrive geo mover conclusão, os usuários terão acesso aos seus arquivos OneDrive no App. equipes Além disso, os arquivos compartilhados via bate-papo de equipes do seu OneDrive antes da movimentação geo continuará inserido após a movimentação está concluída.

### <a name="onedrive-for-business-mobile-app-ios"></a>OneDrive para negócios Mobile App (iOS) 

Após a OneDrive geo mover conclusão, o usuário precisa sair e entrar novamente em iOS Mobile App para sincronizar com o novo local de OneDrive.

### <a name="existing-followed-groups-and-sites"></a>Existente seguido de grupos e sites

Grupos e sites seguidos serão mostrada do OneDrive do usuário for business independente da sua localização geográfica. Sites e grupos hospedados em outro local geo serão aberto em uma guia separada.
