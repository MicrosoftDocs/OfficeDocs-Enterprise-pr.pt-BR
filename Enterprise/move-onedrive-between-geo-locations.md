---
title: Mover um site do OneDrive para um local geográfico diferente
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba como migrar um site do OneDrive para um local geográfico diferente.
ms.openlocfilehash: 6bac98cc0707f977b7b585e8ae0a570f4b9662ee
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="f38cf-103">Mover um site do OneDrive para um local geográfico diferente</span><span class="sxs-lookup"><span data-stu-id="f38cf-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="f38cf-p101">Com a movimentação geográfica do OneDrive, você pode mover o OneDrive de um usuário para um local geográfico diferente. A movimentação geográfica do OneDrive é executada pelo administrador do SharePoint Online ou pelo administrador global do Office 365. Antes de iniciar a movimentação geográfica do OneDrive, notifique o usuário cujo OneDrive está sendo movido e recomende que ele feche todos os arquivos durante a movimentação. (Se o usuário tiver um documento aberto usando o cliente do Office durante a movimentação, quando ela for concluída, o documento precisará ser salvo em um novo local). A movimentação poderá agendada para um momento futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="f38cf-p102">O serviço do OneDrive usa o Armazenamento de Blobs do Azure para armazenar conteúdo. O blob de armazenamento associado ao OneDrive do usuário será movido da origem para a localização geográfica de destino dentro de 40 dias após o destino estar disponível para o usuário do OneDrive. O acesso ao OneDrive do usuário será restaurado assim que o OneDrive de destino estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="f38cf-p103">Durante a janela de movimentação geográfica do OneDrive (cerca de duas a seis horas), o OneDrive do usuário é definido como somente leitura. O usuário ainda pode acessar os arquivos por meio do cliente de sincronização do OneDrive ou o site do OneDrive no SharePoint Online. Após a conclusão da movimentação geográfica do OneDrive, o usuário será automaticamente conectado ao OneDrive na localização geográfica destino quando navegar para o OneDrive no inicializador de aplicativos do Office 365. O cliente de sincronização começará automaticamente a sincronizar do novo local.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="f38cf-115">Os procedimentos deste artigo exigem o [Módulo PowerShell do Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="f38cf-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="f38cf-116">Mover um site do OneDrive</span><span class="sxs-lookup"><span data-stu-id="f38cf-116">Moving a OneDrive site</span></span>

<span data-ttu-id="f38cf-p104">Para executar uma movimentação geográfica do OneDrive, primeiro o administrador do locatário precisa definir o local de dados preferencial (PDL) do usuário como a localização geográfica apropriada. Quando o PDL for definido, aguarde pelo menos 24 horas para que a atualização do PDL seja sincronizada entre os vários locais geográficos antes de iniciar a movimentação geográfica do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="f38cf-119">Ao usar cmdlets de movimentação geográfica, conecte-se ao Serviço de SPO na localização geográfica atual do OneDrive do usuário, usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="f38cf-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="f38cf-120">Por exemplo: para mover o OneDrive do usuário 'Carlos@contosoenergy.onmicrosoft.com', conecte-se ao Centro de administração do SharePoint EUR, pois o OneDrive do usuário está na localização geográfica EUR:</span><span class="sxs-lookup"><span data-stu-id="f38cf-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="f38cf-121">Validar o ambiente</span><span class="sxs-lookup"><span data-stu-id="f38cf-121">Validating the environment</span></span>

<span data-ttu-id="f38cf-122">Antes de começar uma movimentação geográfica do OneDrive, recomendamos validar o ambiente.</span><span class="sxs-lookup"><span data-stu-id="f38cf-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="f38cf-123">Para garantir que todos os locais geográficos são compatíveis, execute:</span><span class="sxs-lookup"><span data-stu-id="f38cf-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="f38cf-p105">Se o OneDrive estiver com retenção legal ou se contiver um subsite, não poderá ser movido. Você pode usar o cmdlet Start-SPOUserAndContentMove com o parâmetro –ValidationOnly para validar se o OneDrive pode ser movido:</span><span class="sxs-lookup"><span data-stu-id="f38cf-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="f38cf-p106">Isso retornará Sucesso se o OneDrive estiver pronto para ser movido ou Falha se houver um bloqueio legal ou um subsite que impeça a movimentação. Após validar se o OneDrive está pronto para a movimentação, você pode iniciá-la.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="f38cf-128">Iniciar uma movimentação geográfica do OneDrive</span><span class="sxs-lookup"><span data-stu-id="f38cf-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="f38cf-129">Para iniciar a movimentação, execute:</span><span class="sxs-lookup"><span data-stu-id="f38cf-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="f38cf-130">Usando estes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="f38cf-130">Using these parameters:</span></span>

-   <span data-ttu-id="f38cf-131">_UserPrincipalName_ – UPN do usuário cujo OneDrive está sendo movido.</span><span class="sxs-lookup"><span data-stu-id="f38cf-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="f38cf-p107">_DestinationDataLocation_ – localização geográfica para onde o OneDrive deve ser movido. Deve ser igual à localização de dados preferencial do usuário.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="f38cf-134">Recomendamos a execução do `Get-SPOGeoMoveStateCompatibility` com `ValidationOnly` antes de iniciar a movimentação geográfica do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f38cf-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="f38cf-135">Por exemplo, para mover o OneDrive de carlos@contosoenergy.onmicrosoft.com de EUR para AUS, execute:</span><span class="sxs-lookup"><span data-stu-id="f38cf-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="f38cf-136">Para agendar uma movimentação geográfica posteriormente, use um dos seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="f38cf-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="f38cf-p108">_PreferredMoveBeginDate_ – a movimentação provavelmente começará no horário especificado. A hora deve ser especificada como UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="f38cf-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="f38cf-p109">_PreferredMoveEndDate_ – a movimentação provavelmente será concluída no horário especificado, conforme o melhor esforço. A hora deve ser especificada como UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="f38cf-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="f38cf-141">Cancelar uma movimentação geográfica do OneDrive</span><span class="sxs-lookup"><span data-stu-id="f38cf-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="f38cf-142">Você pode parar a movimentação geográfica do OneDrive de um usuário, desde que a movimentação não esteja em andamento ou tenha sido concluída, usando o cmdlet:</span><span class="sxs-lookup"><span data-stu-id="f38cf-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="f38cf-143">Em que _UserPrincipalName_ é o UPN do usuário cuja movimentação do OneDrive você deseja parar.</span><span class="sxs-lookup"><span data-stu-id="f38cf-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="f38cf-144">Determinar o status atual</span><span class="sxs-lookup"><span data-stu-id="f38cf-144">Determining current status</span></span>

<span data-ttu-id="f38cf-145">Você pode verificar o status de uma movimentação geográfica do OneDrive dentro ou fora do local geográfico ao qual está conectado usando o cmdlet Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="f38cf-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="f38cf-146">Os status de movimentação estão descritas na seguinte tabela:</span><span class="sxs-lookup"><span data-stu-id="f38cf-146">The fields in alerts are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f38cf-147"><strong>Status</strong></span><span class="sxs-lookup"><span data-stu-id="f38cf-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="f38cf-148"><strong>Descrição</strong></span><span class="sxs-lookup"><span data-stu-id="f38cf-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f38cf-149">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f38cf-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="f38cf-150">Movimentação não iniciadas.</span><span class="sxs-lookup"><span data-stu-id="f38cf-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f38cf-151">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="f38cf-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="f38cf-152">A movimentação está em andamento em um dos seguintes estados: Validação (1/4), Backup (2/4), Restauração (3 4), Limpeza (4/4).</span><span class="sxs-lookup"><span data-stu-id="f38cf-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f38cf-153">Êxito</span><span class="sxs-lookup"><span data-stu-id="f38cf-153">Success</span></span></td>
<td align="left"><span data-ttu-id="f38cf-154">A movimentação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="f38cf-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f38cf-155">Falhou</span><span class="sxs-lookup"><span data-stu-id="f38cf-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="f38cf-156">Falha na movimentação.</span><span class="sxs-lookup"><span data-stu-id="f38cf-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f38cf-157">Para localizar o status da movimentação de um usuário específico, use o parâmetro UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="f38cf-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="f38cf-158">Para localizar o status de todas as movimentações dentro ou fora da localização geográfica à qual você está conectado, use o parâmetro MoveState com um dos seguintes valores: NotStarted, InProgress, Success, Failed, All.</span><span class="sxs-lookup"><span data-stu-id="f38cf-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="f38cf-159">Você também pode adicionar o parâmetro `-Verbose` para obter descrições mais detalhadas do estado de movimentação.</span><span class="sxs-lookup"><span data-stu-id="f38cf-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="f38cf-160">Experiência do Usuário</span><span class="sxs-lookup"><span data-stu-id="f38cf-160">User Experience</span></span>

<span data-ttu-id="f38cf-p110">Os usuários do OneDrive deverão enfrentar um mínimo de interrupção se o OneDrive for movido para uma localização geográfica diferente. Além de um breve estado somente leitura durante a movimentação, as permissões e os links existentes continuarão a funcionar como esperado quando a movimentação for concluída.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="f38cf-163">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="f38cf-163">OneDrive for Business</span></span>

<span data-ttu-id="f38cf-p111">Enquanto a movimentação está em andamento, o OneDrive do usuário é definido como somente leitura. Após a movimentação ser concluída, o usuário é direcionado para o OneDrive na nova localização geográfica quando ele navega para o OneDrive, o inicializador de aplicativos do Office 365 ou um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="f38cf-166">Permissões sobre o conteúdo do OneDrive</span><span class="sxs-lookup"><span data-stu-id="f38cf-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="f38cf-167">Os usuários com permissões para o conteúdo do OneDrive continuarão a ter acesso ao conteúdo durante a movimentação e após sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="f38cf-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="f38cf-168">Cliente de sincronização do OneDrive</span><span class="sxs-lookup"><span data-stu-id="f38cf-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="f38cf-p112">O cliente de sincronização do OneDrive detectará automaticamente e transferirá perfeitamente a sincronização para o novo local do OneDrive após a conclusão da movimentação geográfica do OneDrive. O usuário não precisa entrar novamente nem realizar outras ações.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="f38cf-171">Se um usuário atualizar um arquivo enquanto a movimentação geográfica do OneDrive estiver em andamento, o cliente de sincronização o notificará de que uploads de arquivo estão pendentes enquanto a movimentação estiver em andamento.</span><span class="sxs-lookup"><span data-stu-id="f38cf-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="f38cf-172">Links de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="f38cf-172">Sharing links</span></span> 

<span data-ttu-id="f38cf-173">Após a conclusão da movimentação geográfica do OneDrive, os links compartilhados existentes para os arquivos que foram movidos serão redirecionados automaticamente para a nova localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="f38cf-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="f38cf-174">Experiência do OneNote</span><span class="sxs-lookup"><span data-stu-id="f38cf-174">OneNote Experience</span></span> 

<span data-ttu-id="f38cf-p113">O cliente do OneNote para win32 e o aplicativo UWP (Universal) detectarão automaticamente e sincronizarão perfeitamente os blocos de anotações com o novo local no OneDrive após a conclusão da movimentação geográfica do OneDrive. O usuário não precisa entrar novamente nem realizar outras ações. O único indicador visível para o usuário é que a sincronização de bloco de anotações falha quando a movimentação geográfica do OneDrive está em andamento. Essa experiência está disponível nas seguintes versões do cliente do OneNote:</span><span class="sxs-lookup"><span data-stu-id="f38cf-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="f38cf-179">OneNote win32 – versão 16.0.8326.2096 (e posteriores)</span><span class="sxs-lookup"><span data-stu-id="f38cf-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="f38cf-180">OneNote UWP – versão 16.0.8431.1006 (e posteriores)</span><span class="sxs-lookup"><span data-stu-id="f38cf-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="f38cf-181">Aplicativo móvel do OneNote – versão 16.0.8431.1011 (e posteriores)</span><span class="sxs-lookup"><span data-stu-id="f38cf-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="f38cf-182">Aplicativo de equipes</span><span class="sxs-lookup"><span data-stu-id="f38cf-182">Teams app</span></span>

<span data-ttu-id="f38cf-p114">Após a conclusão da movimentação geográfica do OneDrive, os usuários terão acesso aos arquivos do OneDrive no aplicativo do Teams. Além disso, arquivos compartilhados por chat do Teams no OneDrive antes da movimentação geográfica continuarão funcionando após a movimentação ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="f38cf-185">Aplicativo móvel do OneDrive for Business (iOS)</span><span class="sxs-lookup"><span data-stu-id="f38cf-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="f38cf-186">Após a conclusão da movimentação geográfica do OneDrive, o usuário precisa sair e entrar novamente no aplicativo móvel do iOS para fazer a sincronização com o novo local do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f38cf-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="f38cf-187">Grupos e sites seguidos existentes</span><span class="sxs-lookup"><span data-stu-id="f38cf-187">Existing followed groups and sites</span></span>

<span data-ttu-id="f38cf-p115">Os grupos e sites seguidos serão mostrados no OneDrive for Business do usuário, independentemente da localização geográfica. Sites e grupos hospedados em outra localização geográfica serão abertos em uma guia separada.</span><span class="sxs-lookup"><span data-stu-id="f38cf-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
