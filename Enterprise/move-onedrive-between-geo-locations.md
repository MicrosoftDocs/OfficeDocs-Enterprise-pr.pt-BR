---
title: Mover um site de OneDrive para um local diferente de geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Aprenda a mover um site de OneDrive para uma localização geográfica diferente.
ms.openlocfilehash: 7ce9106fa7d8d144f0f8935713b4df926a73fb6b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="a9b17-103">Mover um site de OneDrive para um local diferente de geo</span><span class="sxs-lookup"><span data-stu-id="a9b17-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="a9b17-p101">Com o OneDrive geo mover, você pode mover OneDrive um usuário para um local diferente geo. OneDrive geo movimentação é executada pelo administrador do SharePoint Online ou o administrador global do Office 365. Antes de iniciar um OneDrive geo mover, certifique-se de notificar o usuário que está sendo movido cujo OneDrive e recomendar que eles fecharem todos os arquivos para a duração da movimentação. (Se o usuário tem um documento aberto usando o cliente do Office durante a movimentação, então após mover o documento precisará ser salvo para o novo local de conclusão.) A movimentação pode ser agendada para um tempo futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="a9b17-p102">O serviço do OneDrive usa o armazenamento de Blob do Windows Azure para armazenar o conteúdo. O blob de armazenamento associado ao OneDrive do usuário será movido da origem de local geo de destino dentro de 40 dias do OneDrive sendo disponíveis para o usuário de destino. O acesso ao OneDrive do usuário será restaurado tão logo o destino OneDrive está disponível.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="a9b17-p103">Durante a janela de movimentação do OneDrive geo (cerca de 2 a 6 horas) OneDrive do usuário é definido como somente leitura. O usuário ainda pode acessar os arquivos por meio do seu site de OneDrive no SharePoint Online ou o cliente de sincronização do OneDrive. Quando OneDrive geo movimentação for concluída, o usuário será automaticamente conectado ao seu OneDrive no local geo destino quando navegarem para o OneDrive no iniciador de aplicativo do Office 365. O cliente de sincronização começará automaticamente a sincronização de um novo local.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="a9b17-115">Os procedimentos neste artigo exigem o [Módulo de PowerShell Online do Microsoft SharePoint](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="a9b17-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="a9b17-116">Mover um site de OneDrive</span><span class="sxs-lookup"><span data-stu-id="a9b17-116">Moving a OneDrive site</span></span>

<span data-ttu-id="a9b17-p104">Para executar um OneDrive geo mover, o administrador de locatário defina primeiro preferencial a localização de dados (PDL) do usuário para o local de geo apropriado. Depois que o PDL estiver definida, aguarde pelo menos 24 horas para a atualização PDL a sincronização entre os locais de geo antes de iniciar a movimentação de geo OneDrive.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="a9b17-119">Quando usando o geo mover cmdlets, conecte ao serviço do SPO no local de geo OneDrive atual do usuário, usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="a9b17-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="a9b17-120">Por exemplo: para mover OneDrive do usuário 'Matt@contosoenergy.onmicrosoft.com', conecte-se ao centro de administração do SharePoint EUR como OneDrive do usuário está no local de geo EUR:</span><span class="sxs-lookup"><span data-stu-id="a9b17-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="a9b17-121">Validando o ambiente</span><span class="sxs-lookup"><span data-stu-id="a9b17-121">Validating the environment</span></span>

<span data-ttu-id="a9b17-122">Antes de começar a mover um geo OneDrive, é recomendável que você valide o ambiente.</span><span class="sxs-lookup"><span data-stu-id="a9b17-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="a9b17-123">Para garantir que todos os locais de geo são compatíveis, execute:</span><span class="sxs-lookup"><span data-stu-id="a9b17-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="a9b17-p105">Se um OneDrive está em retenção legal ou se ele contiver um subsite, ele não pode ser movido. Você pode usar o cmdlet Start-SPOUserAndContentMove com o parâmetro - ValidationOnly para validar se o OneDrive for capaz de ser movida:</span><span class="sxs-lookup"><span data-stu-id="a9b17-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="a9b17-p106">Isso retornará o sucesso se OneDrive está pronta para ser movido ou falhar se houver uma retenção legal ou subsite que impediria a movimentação. Depois que você tenha validado que o OneDrive está pronto para migrar, você pode iniciar a movimentação.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="a9b17-128">Iniciar uma movimentação de geo OneDrive</span><span class="sxs-lookup"><span data-stu-id="a9b17-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="a9b17-129">Para iniciar a movimentação, execute:</span><span class="sxs-lookup"><span data-stu-id="a9b17-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="a9b17-130">Usando esses parâmetros:</span><span class="sxs-lookup"><span data-stu-id="a9b17-130">Using these parameters:</span></span>

-   <span data-ttu-id="a9b17-131">_UserPrincipalName_ – UPN do usuário cujo OneDrive está sendo movido.</span><span class="sxs-lookup"><span data-stu-id="a9b17-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="a9b17-p107">_DestinationDataLocation_ – localização geográfica onde o OneDrive precisa ser movido. Este deve ser igual ao local dos dados preferencial do usuário.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="a9b17-134">É recomendável executar `Get-SPOGeoMoveStateCompatibility` com `ValidationOnly` antes de iniciar o OneDrive geo mover.</span><span class="sxs-lookup"><span data-stu-id="a9b17-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="a9b17-135">Por exemplo, para mover o OneDrive de matt@contosoenergy.onmicrosoft.com de EUR para Austrália, execute:</span><span class="sxs-lookup"><span data-stu-id="a9b17-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="a9b17-136">Para agendar uma movimentação geo por um tempo posterior, use um dos parâmetros a seguir:</span><span class="sxs-lookup"><span data-stu-id="a9b17-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="a9b17-p108">_PreferredMoveBeginDate_ – a movimentação provavelmente começar neste momento especificado. Tempo deve ser especificado no tempo Universal Coordenado (UTC).</span><span class="sxs-lookup"><span data-stu-id="a9b17-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="a9b17-p109">_PreferredMoveEndDate_ – a movimentação provavelmente ser concluídas por neste momento especificado, em uma base de esforço recomendada. Tempo deve ser especificado no tempo Universal Coordenado (UTC).</span><span class="sxs-lookup"><span data-stu-id="a9b17-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="a9b17-141">Cancelar uma movimentação de geo OneDrive</span><span class="sxs-lookup"><span data-stu-id="a9b17-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="a9b17-142">Você pode interromper a movimentação geo do OneDrive de um usuário, desde que a movimentação não está em andamento ou concluído usando o cmdlet:</span><span class="sxs-lookup"><span data-stu-id="a9b17-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="a9b17-143">Onde o _UserPrincipalName_ é o UPN do usuário cujo OneDrive mover que você deseja parar.</span><span class="sxs-lookup"><span data-stu-id="a9b17-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="a9b17-144">Determinando o status atual</span><span class="sxs-lookup"><span data-stu-id="a9b17-144">Determining current status</span></span>

<span data-ttu-id="a9b17-145">Você pode verificar o status de um OneDrive geo mover ou sair do geo que você está conectado usando o cmdlet Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="a9b17-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="a9b17-146">Os status de movimentação são descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a9b17-146">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a9b17-147"><strong>Status</strong></span><span class="sxs-lookup"><span data-stu-id="a9b17-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="a9b17-148"><strong>Descrição</strong></span><span class="sxs-lookup"><span data-stu-id="a9b17-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a9b17-149">NotStarted</span><span class="sxs-lookup"><span data-stu-id="a9b17-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="a9b17-150">A movimentação não foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="a9b17-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9b17-151">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="a9b17-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="a9b17-152">A movimentação está em andamento em um dos seguintes estados: validação (1/4) (2/4) de Backup, restaurar (3 4), limpeza (4/4).</span><span class="sxs-lookup"><span data-stu-id="a9b17-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a9b17-153">Sucesso</span><span class="sxs-lookup"><span data-stu-id="a9b17-153">Success</span></span></td>
<td align="left"><span data-ttu-id="a9b17-154">A movimentação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="a9b17-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a9b17-155">Com falha</span><span class="sxs-lookup"><span data-stu-id="a9b17-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="a9b17-156">A movimentação falhou.</span><span class="sxs-lookup"><span data-stu-id="a9b17-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a9b17-157">Para localizar o status de movimentação de um usuário específico, use o parâmetro UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="a9b17-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="a9b17-158">Para localizar o status de todas as movimentações ou sair geo local que você está conectado, use o parâmetro MoveState com um dos seguintes valores: NotStarted, InProgress, êxito, falha, todos os.</span><span class="sxs-lookup"><span data-stu-id="a9b17-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="a9b17-159">Você também pode adicionar o `-Verbose` parâmetro para obter descrições mais detalhadas do estado de movimentação.</span><span class="sxs-lookup"><span data-stu-id="a9b17-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="a9b17-160">Experiência do Usuário</span><span class="sxs-lookup"><span data-stu-id="a9b17-160">User Experience</span></span>

<span data-ttu-id="a9b17-p110">Os usuários do OneDrive devem observar um mínimo de interrupção se seus OneDrive for movido para um local diferente geo. Além de um estado somente leitura breve durante a movimentação, permissões e os vínculos existentes continuarão funcionando como esperado depois que a movimentação é concluída.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="a9b17-163">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="a9b17-163">OneDrive for Business</span></span>

<span data-ttu-id="a9b17-p111">Enquanto a movimentação está em andamento OneDrive do usuário é definido como somente leitura. Depois que a movimentação é concluída, o usuário seja direcionado para seu OneDrive no novo local geo quando navegarem para o OneDrive o iniciador de aplicativo do Office 365 ou um navegador da web.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="a9b17-166">Permissões de conteúdo do OneDrive</span><span class="sxs-lookup"><span data-stu-id="a9b17-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="a9b17-167">Usuários com permissões para o conteúdo de OneDrive continuará a ter acesso ao conteúdo durante a movimentação, e depois que ela for concluída.</span><span class="sxs-lookup"><span data-stu-id="a9b17-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="a9b17-168">Cliente de sincronização do OneDrive</span><span class="sxs-lookup"><span data-stu-id="a9b17-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="a9b17-p112">O cliente de sincronização do OneDrive detectará automaticamente e transferir uniformemente está sincronizando para o novo local de OneDrive depois que a movimentação de geo OneDrive for concluída. O usuário não precisa entrar novamente ou executar qualquer outra ação.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="a9b17-171">Se um usuário atualiza um arquivo enquanto a movimentação de geo OneDrive está em andamento, o cliente de sincronização notificará-los que carregamentos de arquivo estão pendentes enquanto a movimentação está em andamento.</span><span class="sxs-lookup"><span data-stu-id="a9b17-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="a9b17-172">Compartilhamento de links</span><span class="sxs-lookup"><span data-stu-id="a9b17-172">Sharing links</span></span> 

<span data-ttu-id="a9b17-173">Após a OneDrive geo mover conclusão, os vínculos existentes de compartilhado para os arquivos que foram movidos automaticamente redirecionará para o novo local de geo.</span><span class="sxs-lookup"><span data-stu-id="a9b17-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="a9b17-174">Experiência do OneNote</span><span class="sxs-lookup"><span data-stu-id="a9b17-174">OneNote Experience</span></span> 

<span data-ttu-id="a9b17-p113">Cliente do OneNote win32 e UWP (Universal) App detectará automaticamente e perfeitamente sincronizar blocos de anotações para o novo local de OneDrive depois que o OneDrive geo movimentação está concluída. O usuário não precisa entrar novamente ou executar qualquer outra ação. O indicador visível somente para o usuário é sincronização de notebook falhará quando OneDrive geo movimentação está em andamento. Esta experiência está disponível nas seguintes versões de cliente do OneNote:</span><span class="sxs-lookup"><span data-stu-id="a9b17-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="a9b17-179">OneNote win32 – versão 16.0.8326.2096 (e posterior)</span><span class="sxs-lookup"><span data-stu-id="a9b17-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="a9b17-180">OneNote UWP – versão 16.0.8431.1006 (e posterior)</span><span class="sxs-lookup"><span data-stu-id="a9b17-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="a9b17-181">OneNote Mobile App – versão 16.0.8431.1011 (e posterior)</span><span class="sxs-lookup"><span data-stu-id="a9b17-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="a9b17-182">Aplicativo de equipes</span><span class="sxs-lookup"><span data-stu-id="a9b17-182">Teams app</span></span>

<span data-ttu-id="a9b17-p114">Após OneDrive geo mover conclusão, os usuários terão acesso aos seus arquivos OneDrive no App. equipes Além disso, os arquivos compartilhados via bate-papo de equipes do seu OneDrive antes da movimentação geo continuará inserido após a movimentação está concluída.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="a9b17-185">OneDrive para negócios Mobile App (iOS)</span><span class="sxs-lookup"><span data-stu-id="a9b17-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="a9b17-186">Após a OneDrive geo mover conclusão, o usuário precisa sair e entrar novamente em iOS Mobile App para sincronizar com o novo local de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="a9b17-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="a9b17-187">Existente seguido de grupos e sites</span><span class="sxs-lookup"><span data-stu-id="a9b17-187">Existing followed groups and sites</span></span>

<span data-ttu-id="a9b17-p115">Grupos e sites seguidos serão mostrada do OneDrive do usuário for business independente da sua localização geográfica. Sites e grupos hospedados em outro local geo serão aberto em uma guia separada.</span><span class="sxs-lookup"><span data-stu-id="a9b17-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
