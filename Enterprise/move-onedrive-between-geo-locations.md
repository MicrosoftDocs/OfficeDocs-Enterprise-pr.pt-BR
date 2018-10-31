---
title: Mover um site do OneDrive para um local geográfico diferente
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba como migrar um site do OneDrive para um local geográfico diferente.
ms.openlocfilehash: 258c562343875ff4ad115b81dba5338c79641dfc
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849847"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="273a9-103">Mover um site do OneDrive para um local geográfico diferente</span><span class="sxs-lookup"><span data-stu-id="273a9-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="273a9-p101">Com a movimentação geográfica do OneDrive, você pode mover o OneDrive de um usuário para um local geográfico diferente. A movimentação geográfica do OneDrive é executada pelo administrador do SharePoint Online ou pelo administrador global do Office 365. Antes de iniciar a movimentação geográfica do OneDrive, notifique o usuário cujo OneDrive está sendo movido e recomende que ele feche todos os arquivos durante a movimentação. (Se o usuário tiver um documento aberto usando o cliente do Office durante a movimentação, quando ela for concluída, o documento precisará ser salvo em um novo local). A movimentação poderá agendada para um momento futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="273a9-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="273a9-p102">O serviço do OneDrive usa o Armazenamento de Blobs do Azure para armazenar conteúdo. O blob de armazenamento associado ao OneDrive do usuário será movido da origem para a localização geográfica de destino dentro de 40 dias após o destino estar disponível para o usuário do OneDrive. O acesso ao OneDrive do usuário será restaurado assim que o OneDrive de destino estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="273a9-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="273a9-p103">Durante a janela de movimentação geográfica do OneDrive (cerca de duas a seis horas), o OneDrive do usuário é definido como somente leitura. O usuário ainda pode acessar os arquivos por meio do cliente de sincronização do OneDrive ou o site do OneDrive no SharePoint Online. Após a conclusão da movimentação geográfica do OneDrive, o usuário será automaticamente conectado ao OneDrive na localização geográfica destino quando navegar para o OneDrive no inicializador de aplicativos do Office 365. O cliente de sincronização começará automaticamente a sincronizar do novo local.</span><span class="sxs-lookup"><span data-stu-id="273a9-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="273a9-115">Os procedimentos deste artigo exigem o [Módulo PowerShell do Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="273a9-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="communicating-to-your-users"></a><span data-ttu-id="273a9-116">Comunicação com seus usuários</span><span class="sxs-lookup"><span data-stu-id="273a9-116">Communicating to your users</span></span>

<span data-ttu-id="273a9-p104">Ao mover os sites do OneDrive entre locais geográficos, é importante comunicar aos seus usuários o que esperar. Isso pode ajudar a reduzir a confusão do usuário e chamadas para o suporte técnico. Envie um email para seus usuários antes de fazer as movimentações com as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="273a9-p104">When moving OneDrive sites between geo-locations, it's important to communicate to your users what to expect. This can help reduce user confusion and calls to your help desk. Email your users before the move and let them know the following information:</span></span>

- <span data-ttu-id="273a9-120">Quando a mudança deve começar e quanto tempo deve demorar</span><span class="sxs-lookup"><span data-stu-id="273a9-120">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="273a9-121">Para qual localização geográfica o OneDrive mudará, e qual é a URL para acessar o novo local</span><span class="sxs-lookup"><span data-stu-id="273a9-121">What geo location their OneDrive is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="273a9-122">Eles devem fechar os arquivos e não fazer edições durante a mudança.</span><span class="sxs-lookup"><span data-stu-id="273a9-122">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="273a9-123">O compartilhamento e permissões de arquivo não mudarão devido a mudança.</span><span class="sxs-lookup"><span data-stu-id="273a9-123">File permissions and sharing will not change as a result of the move.</span></span>
- <span data-ttu-id="273a9-124">O que esperar da [experiência do usuário em um ambiente multigeográfico](multi-geo-user-experience.md)</span><span class="sxs-lookup"><span data-stu-id="273a9-124">What to expect from the [user experience in a multi-geo environment](multi-geo-user-experience.md)</span></span>

<span data-ttu-id="273a9-125">Após a conclusão da mudança, envie um email aos seus usuários informando que eles podem continuar a trabalhar com o OneDrive.</span><span class="sxs-lookup"><span data-stu-id="273a9-125">Be sure to send your users an email when the move has successfully completed informing them that they can resume working in OneDrive.</span></span>

## <a name="scheduling-onedrive-site-moves"></a><span data-ttu-id="273a9-126">Agendar movimentações do site do OneDrive</span><span class="sxs-lookup"><span data-stu-id="273a9-126">Scheduling OneDrive site moves</span></span>

<span data-ttu-id="273a9-p105">Você pode agendar as movimentações de site do OneDrive com antecedência (conforme descrito posteriormente neste artigo). Recomendamos começar com um pequeno número de usuários para validar seus fluxos de trabalho e estratégias de comunicação. Quando você estiver familiarizado com o processo, poderá agendar as movimentações da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="273a9-p105">You can schedule OneDrive site moves in advance (described later in this article). We recommend that you start with a small number of users to validate your workflows and communication strategies. Once you are comfortable with the process, you can schedule moves as follows:</span></span>

- <span data-ttu-id="273a9-130">Você pode agendar até 4.000 movimentações por vez.</span><span class="sxs-lookup"><span data-stu-id="273a9-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="273a9-131">Conforme a movimentação se inicia, você pode agendar mais, com no máximo 4.000 movimentações pendentes na fila e a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="273a9-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
- <span data-ttu-id="273a9-132">É recomendável não agendar mais de 4.000 movimentações por mês.</span><span class="sxs-lookup"><span data-stu-id="273a9-132">We recommend not scheduling more than 4,000 moves per month.</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="273a9-133">Mover um site do OneDrive</span><span class="sxs-lookup"><span data-stu-id="273a9-133">Moving a OneDrive site</span></span>

<span data-ttu-id="273a9-p106">Para executar uma movimentação geográfica do OneDrive, primeiro o administrador do locatário precisa definir o local de dados preferencial (PDL) do usuário como a localização geográfica apropriada. Quando o PDL for definido, aguarde pelo menos 24 horas para que a atualização do PDL seja sincronizada entre os vários locais geográficos antes de iniciar a movimentação geográfica do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="273a9-p106">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="273a9-136">Ao usar cmdlets de movimentação geográfica, conecte-se ao Serviço de SPO na localização geográfica atual do OneDrive do usuário, usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="273a9-136">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="273a9-137">Por exemplo: para mover o OneDrive do usuário 'Carlos@contosoenergy.onmicrosoft.com', conecte-se ao Centro de administração do SharePoint EUR, pois o OneDrive do usuário está na localização geográfica EUR:</span><span class="sxs-lookup"><span data-stu-id="273a9-137">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="273a9-138">Validar o ambiente</span><span class="sxs-lookup"><span data-stu-id="273a9-138">Validating the environment</span></span>

<span data-ttu-id="273a9-139">Antes de começar uma movimentação geográfica do OneDrive, recomendamos validar o ambiente.</span><span class="sxs-lookup"><span data-stu-id="273a9-139">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="273a9-140">Para garantir que todos os locais geográficos são compatíveis, execute:</span><span class="sxs-lookup"><span data-stu-id="273a9-140">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="273a9-p107">Se o OneDrive estiver com retenção legal ou se contiver um subsite, não poderá ser movido. Você pode usar o cmdlet Start-SPOUserAndContentMove com o parâmetro –ValidationOnly para validar se o OneDrive pode ser movido:</span><span class="sxs-lookup"><span data-stu-id="273a9-p107">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="273a9-p108">Isso retornará Sucesso se o OneDrive estiver pronto para ser movido ou Falha se houver um bloqueio legal ou um subsite que impeça a movimentação. Após validar se o OneDrive está pronto para a movimentação, você pode iniciá-la.</span><span class="sxs-lookup"><span data-stu-id="273a9-p108">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="273a9-145">Iniciar uma movimentação geográfica do OneDrive</span><span class="sxs-lookup"><span data-stu-id="273a9-145">Start a OneDrive geo move</span></span>

<span data-ttu-id="273a9-146">Para iniciar a movimentação, execute:</span><span class="sxs-lookup"><span data-stu-id="273a9-146">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="273a9-147">Usando estes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="273a9-147">Using these parameters:</span></span>

-   <span data-ttu-id="273a9-148">_UserPrincipalName_ – UPN do usuário cujo OneDrive está sendo movido.</span><span class="sxs-lookup"><span data-stu-id="273a9-148">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="273a9-p109">_DestinationDataLocation_ – localização geográfica para onde o OneDrive deve ser movido. Deve ser igual à localização de dados preferencial do usuário.</span><span class="sxs-lookup"><span data-stu-id="273a9-p109">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="273a9-151">Recomendamos a execução do `Get-SPOGeoMoveStateCompatibility` com `ValidationOnly` antes de iniciar a movimentação geográfica do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="273a9-151">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="273a9-152">Por exemplo, para mover o OneDrive de carlos@contosoenergy.onmicrosoft.com de EUR para AUS, execute:</span><span class="sxs-lookup"><span data-stu-id="273a9-152">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations-image2.png)

<span data-ttu-id="273a9-153">Para agendar uma movimentação geográfica posteriormente, use um dos seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="273a9-153">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="273a9-p110">_PreferredMoveBeginDate_ – a movimentação provavelmente começará no horário especificado. A hora deve ser especificada como UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="273a9-p110">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="273a9-p111">_PreferredMoveEndDate_ – a movimentação provavelmente será concluída no horário especificado, conforme o melhor esforço. A hora deve ser especificada como UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="273a9-p111">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="273a9-158">Cancelar uma movimentação geográfica do OneDrive</span><span class="sxs-lookup"><span data-stu-id="273a9-158">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="273a9-159">Você pode parar a movimentação geográfica do OneDrive de um usuário, desde que a movimentação não esteja em andamento ou tenha sido concluída, usando o cmdlet:</span><span class="sxs-lookup"><span data-stu-id="273a9-159">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="273a9-160">Em que _UserPrincipalName_ é o UPN do usuário cuja movimentação do OneDrive você deseja parar.</span><span class="sxs-lookup"><span data-stu-id="273a9-160">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="273a9-161">Determinar o status atual</span><span class="sxs-lookup"><span data-stu-id="273a9-161">Determining current status</span></span>

<span data-ttu-id="273a9-162">Você pode verificar o status de uma movimentação geográfica do OneDrive dentro ou fora do local geográfico ao qual está conectado usando o cmdlet Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="273a9-162">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="273a9-163">Os status de movimentação estão descritas na seguinte tabela:</span><span class="sxs-lookup"><span data-stu-id="273a9-163">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="273a9-164"><strong>Status</strong></span><span class="sxs-lookup"><span data-stu-id="273a9-164"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="273a9-165"><strong>Descrição</strong></span><span class="sxs-lookup"><span data-stu-id="273a9-165"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="273a9-166">NotStarted</span><span class="sxs-lookup"><span data-stu-id="273a9-166">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="273a9-167">Movimentação não iniciadas.</span><span class="sxs-lookup"><span data-stu-id="273a9-167">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="273a9-168">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="273a9-168">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="273a9-169">A movimentação está em andamento em um dos seguintes estados: Validação (1/4), Backup (2/4), Restauração (3 4), Limpeza (4/4).</span><span class="sxs-lookup"><span data-stu-id="273a9-169">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="273a9-170">Êxito</span><span class="sxs-lookup"><span data-stu-id="273a9-170">Success</span></span></td>
<td align="left"><span data-ttu-id="273a9-171">A movimentação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="273a9-171">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="273a9-172">Falhou</span><span class="sxs-lookup"><span data-stu-id="273a9-172">Failed</span></span></td>
<td align="left"><span data-ttu-id="273a9-173">Falha na movimentação.</span><span class="sxs-lookup"><span data-stu-id="273a9-173">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="273a9-174">Para localizar o status da movimentação de um usuário específico, use o parâmetro UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="273a9-174">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="273a9-175">Para localizar o status de todas as movimentações dentro ou fora da localização geográfica à qual você está conectado, use o parâmetro MoveState com um dos seguintes valores: NotStarted, InProgress, Success, Failed, All.</span><span class="sxs-lookup"><span data-stu-id="273a9-175">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="273a9-176">Você também pode adicionar o parâmetro `-Verbose` para obter descrições mais detalhadas do estado de movimentação.</span><span class="sxs-lookup"><span data-stu-id="273a9-176">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="273a9-177">Experiência do Usuário</span><span class="sxs-lookup"><span data-stu-id="273a9-177">User Experience</span></span>

<span data-ttu-id="273a9-p112">Os usuários do OneDrive deverão enfrentar um mínimo de interrupção se o OneDrive for movido para uma localização geográfica diferente. Além de um breve estado somente leitura durante a movimentação, as permissões e os links existentes continuarão a funcionar como esperado quando a movimentação for concluída.</span><span class="sxs-lookup"><span data-stu-id="273a9-p112">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="273a9-180">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="273a9-180">OneDrive for Business</span></span>

<span data-ttu-id="273a9-p113">Enquanto a movimentação está em andamento, o OneDrive do usuário é definido como somente leitura. Após a movimentação ser concluída, o usuário é direcionado para o OneDrive na nova localização geográfica quando ele navega para o OneDrive, o inicializador de aplicativos do Office 365 ou um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="273a9-p113">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="273a9-183">Permissões sobre o conteúdo do OneDrive</span><span class="sxs-lookup"><span data-stu-id="273a9-183">Permissions on OneDrive content</span></span>

<span data-ttu-id="273a9-184">Os usuários com permissões para o conteúdo do OneDrive continuarão a ter acesso ao conteúdo durante a movimentação e após sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="273a9-184">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="273a9-185">Cliente de sincronização do OneDrive</span><span class="sxs-lookup"><span data-stu-id="273a9-185">OneDrive Sync Client</span></span> 

<span data-ttu-id="273a9-p114">O cliente de sincronização do OneDrive detectará automaticamente e transferirá perfeitamente a sincronização para o novo local do OneDrive após a conclusão da movimentação geográfica do OneDrive. O usuário não precisa entrar novamente nem realizar outras ações. (Precisa da versão 17.3.6943.0625 ou posterior do cliente de sincronização.)</span><span class="sxs-lookup"><span data-stu-id="273a9-p114">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.  (Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="273a9-189">Se um usuário atualizar um arquivo enquanto a movimentação geográfica do OneDrive estiver em andamento, o cliente de sincronização o notificará de que uploads de arquivo estão pendentes enquanto a movimentação estiver em andamento.</span><span class="sxs-lookup"><span data-stu-id="273a9-189">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="273a9-190">Links de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="273a9-190">Sharing links</span></span> 

<span data-ttu-id="273a9-191">Após a conclusão da movimentação geográfica do OneDrive, os links compartilhados existentes para os arquivos que foram movidos serão redirecionados automaticamente para a nova localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="273a9-191">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="273a9-192">Experiência do OneNote</span><span class="sxs-lookup"><span data-stu-id="273a9-192">OneNote Experience</span></span> 

<span data-ttu-id="273a9-p115">O cliente do OneNote para win32 e o aplicativo UWP (Universal) detectarão automaticamente e sincronizarão perfeitamente os blocos de anotações com o novo local no OneDrive após a conclusão da movimentação geográfica do OneDrive. O usuário não precisa entrar novamente nem realizar outras ações. O único indicador visível para o usuário é que a sincronização de bloco de anotações falha quando a movimentação geográfica do OneDrive está em andamento. Essa experiência está disponível nas seguintes versões do cliente do OneNote:</span><span class="sxs-lookup"><span data-stu-id="273a9-p115">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="273a9-197">OneNote win32 – versão 16.0.8326.2096 (e posteriores)</span><span class="sxs-lookup"><span data-stu-id="273a9-197">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="273a9-198">OneNote UWP – versão 16.0.8431.1006 (e posteriores)</span><span class="sxs-lookup"><span data-stu-id="273a9-198">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="273a9-199">Aplicativo móvel do OneNote – versão 16.0.8431.1011 (e posteriores)</span><span class="sxs-lookup"><span data-stu-id="273a9-199">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="273a9-200">Aplicativo de equipes</span><span class="sxs-lookup"><span data-stu-id="273a9-200">Teams app</span></span>

<span data-ttu-id="273a9-p116">Após a conclusão da movimentação geográfica do OneDrive, os usuários terão acesso aos arquivos do OneDrive no aplicativo do Teams. Além disso, arquivos compartilhados por chat do Teams no OneDrive antes da movimentação geográfica continuarão funcionando após a movimentação ser concluída.</span><span class="sxs-lookup"><span data-stu-id="273a9-p116">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="273a9-203">Aplicativo móvel do OneDrive for Business (iOS)</span><span class="sxs-lookup"><span data-stu-id="273a9-203">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="273a9-204">Após a conclusão da movimentação geográfica do OneDrive, o usuário precisa sair e entrar novamente no aplicativo móvel do iOS para fazer a sincronização com o novo local do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="273a9-204">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="273a9-205">Grupos e sites seguidos existentes</span><span class="sxs-lookup"><span data-stu-id="273a9-205">Existing followed groups and sites</span></span>

<span data-ttu-id="273a9-p117">Os grupos e sites seguidos serão mostrados no OneDrive for Business do usuário, independentemente da localização geográfica. Sites e grupos hospedados em outra localização geográfica serão abertos em uma guia separada.</span><span class="sxs-lookup"><span data-stu-id="273a9-p117">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
