---
title: Mover um site do OneDrive para um local geográfico diferente
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Saiba como migrar um site do OneDrive para um local geográfico diferente.
ms.openlocfilehash: e093eab04a5ef19fcd6759d66cb65e9ee264c388
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974013"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Mover um site do OneDrive para um local geográfico diferente 

Com a movimentação geográfica do OneDrive, você pode mover o OneDrive de um usuário para um local geográfico diferente. A movimentação geográfica do OneDrive é executada pelo administrador do SharePoint Online ou pelo administrador global do Office 365. Antes de iniciar a movimentação geográfica do OneDrive, notifique o usuário cujo OneDrive está sendo movido e recomende que ele feche todos os arquivos durante a movimentação. (Se o usuário tiver um documento aberto usando o cliente do Office durante a movimentação, quando ela for concluída, o documento precisará ser salvo em um novo local). A movimentação poderá agendada para um momento futuro, se desejado.

O serviço do OneDrive usa o Armazenamento de Blobs do Azure para armazenar conteúdo. O blob de armazenamento associado ao OneDrive do usuário será movido da origem para a localização geográfica de destino dentro de 40 dias após o destino estar disponível para o usuário do OneDrive. O acesso ao OneDrive do usuário será restaurado assim que o OneDrive de destino estiver disponível.

Durante a janela de movimentação geográfica do OneDrive (cerca de duas a seis horas), o OneDrive do usuário é definido como somente leitura. O usuário ainda pode acessar os arquivos por meio do cliente de sincronização do OneDrive ou o site do OneDrive no SharePoint Online. Após a conclusão da movimentação geográfica do OneDrive, o usuário será automaticamente conectado ao OneDrive na localização geográfica destino quando navegar para o OneDrive no inicializador de aplicativos do Office 365. O cliente de sincronização começará automaticamente a sincronizar do novo local.

Os procedimentos deste artigo exigem o [Módulo PowerShell do Microsoft SharePoint Online](https://www.microsoft.com/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>Comunicação com seus usuários

Ao mover os sites do OneDrive entre locais geográficos, é importante comunicar aos seus usuários o que esperar. Isso pode ajudar a reduzir a confusão do usuário e chamadas para o suporte técnico. Envie um email para seus usuários antes de fazer as movimentações com as seguintes informações:

- Quando a mudança deve começar e quanto tempo deve demorar
- Para qual localização geográfica o OneDrive mudará, e qual é a URL para acessar o novo local
- Eles devem fechar os arquivos e não fazer edições durante a mudança.
- O compartilhamento e permissões de arquivo não mudarão devido a mudança.
- O que esperar da [experiência do usuário em um ambiente multigeográfico](multi-geo-user-experience.md)

Após a conclusão da mudança, envie um email aos seus usuários informando que eles podem continuar a trabalhar com o OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>Agendar movimentações do site do OneDrive

Você pode agendar as movimentações de site do OneDrive com antecedência (conforme descrito posteriormente neste artigo). Recomendamos começar com um pequeno número de usuários para validar seus fluxos de trabalho e estratégias de comunicação. Quando você estiver familiarizado com o processo, poderá agendar as movimentações da seguinte maneira:

- Você pode agendar até 4.000 movimentações por vez.
- Conforme a movimentação se inicia, você pode agendar mais, com no máximo 4.000 movimentações pendentes na fila e a qualquer momento.
- O tamanho máximo de um OneDrive que pode ser movido é de 1 terabyte (1 TB)

## <a name="moving-a-onedrive-site"></a>Mover um site do OneDrive

Para executar uma movimentação geográfica do OneDrive, primeiro o administrador do locatário precisa definir o local de dados preferencial (PDL) do usuário como a localização geográfica apropriada. Quando o PDL for definido, aguarde pelo menos 24 horas para que a atualização do PDL seja sincronizada entre os vários locais geográficos antes de iniciar a movimentação geográfica do OneDrive.

Ao usar cmdlets de movimentação geográfica, conecte-se ao Serviço de SPO na localização geográfica atual do OneDrive do usuário, usando a seguinte sintaxe:

`Connect-SPOService -url https://<tenantName>-admin.sharepoint.com`

Por exemplo: para mover o OneDrive do usuário 'Carlos@contosoenergy.onmicrosoft.com', conecte-se ao Centro de administração do SharePoint EUR, pois o OneDrive do usuário está na localização geográfica EUR:

`Connect-SPOSservice -url https://contosoenergyeur-admin.sharepoint.com`

![Captura de tela da janela do PowerShell mostrando o cmdlet connect-sposervice](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Validar o ambiente

Antes de começar uma movimentação geográfica do OneDrive, recomendamos validar o ambiente.

Para garantir que todos os locais geográficos são compatíveis, execute:

`Get-SPOGeoMoveCrossCompatibilityStatus`

Você verá uma lista da localização geográfica e se o conteúdo poder ser movido, será indicado como "Compatível". Se o comando retornar "Incompatível", repita a validação do status em uma data posterior.

Se OneDrive contiver um subsite, por exemplo, não pode ser movido. Você pode usar o cmdlet Start-SPOUserAndContentMove com o parâmetro -ValidationOnly para validar se o OneDrive pode ser movido:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Isso retornará Sucesso se o OneDrive estiver pronto para ser movido ou Falha se houver um bloqueio legal ou um subsite que impeça a movimentação. Após validar se o OneDrive está pronto para a movimentação, você pode iniciá-la.

## <a name="start-a-onedrive-geo-move"></a>Iniciar uma movimentação geográfica do OneDrive

Para iniciar a movimentação, execute:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Usando estes parâmetros:

-   _UserPrincipalName_ – UPN do usuário cujo OneDrive está sendo movido.

-   _DestinationDataLocation_ – localização geográfica para onde o OneDrive deve ser movido. Deve ser igual à localização de dados preferencial do usuário.

Por exemplo, para mover o OneDrive de carlos@contosoenergy.onmicrosoft.com de EUR para AUS, execute:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![Captura de tela da janela do PowerShell mostrando o cmdlet Start-SPOUserAndContentMove](media/move-onedrive-between-geo-locations-image2.png)

Para agendar uma movimentação geográfica posteriormente, use um dos seguintes parâmetros:

-   _PreferredMoveBeginDate_ – a movimentação provavelmente começará no horário especificado. A hora deve ser especificada como UTC (Tempo Universal Coordenado).

-   _PreferredMoveEndDate_ – a movimentação provavelmente será concluída no horário especificado, conforme o melhor esforço. A hora deve ser especificada como UTC (Tempo Universal Coordenado). 

## <a name="cancel-a-onedrive-geo-move"></a>Cancelar uma movimentação geográfica do OneDrive 

Você pode parar a movimentação geográfica do OneDrive de um usuário, desde que a movimentação não esteja em andamento ou tenha sido concluída, usando o cmdlet:

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

Em que _UserPrincipalName_ é o UPN do usuário cuja movimentação do OneDrive você deseja parar.

## <a name="determining-current-status"></a>Determinar o status atual

Você pode verificar o status de uma movimentação geográfica do OneDrive dentro ou fora do local geográfico ao qual está conectado usando o cmdlet Get-SPOUserAndContentMoveState.

Os status de movimentação estão descritas na seguinte tabela:

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
<td align="left">Movimentação não iniciadas.</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">A movimentação está em andamento em um dos seguintes estados: Validação (1/4), Backup (2/4), Restauração (3 4), Limpeza (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Êxito</td>
<td align="left">A movimentação foi concluída com êxito.</td>
</tr>
<tr class="even">
<td align="left">Falhou</td>
<td align="left">Falha na movimentação.</td>
</tr>
</tbody>
</table>

Para localizar o status da movimentação de um usuário específico, use o parâmetro UserPrincipalName:

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Para localizar o status de todas as movimentações dentro ou fora da localização geográfica à qual você está conectado, use o parâmetro MoveState com um dos seguintes valores: NotStarted, InProgress, Success, Failed, All.

`Get-SPOUserAndContentMoveState -MoveState <value>`

Você também pode adicionar o parâmetro `-Verbose` para obter descrições mais detalhadas do estado de movimentação.

## <a name="user-experience"></a>Experiência do Usuário

Os usuários do OneDrive deverão enfrentar um mínimo de interrupção se o OneDrive for movido para uma localização geográfica diferente. Além de um breve estado somente leitura durante a movimentação, as permissões e os links existentes continuarão a funcionar como esperado quando a movimentação for concluída.

### <a name="onedrive-for-business"></a>OneDrive for Business

Enquanto a movimentação está em andamento, o OneDrive do usuário é definido como somente leitura. Após a movimentação ser concluída, o usuário é direcionado para o OneDrive na nova localização geográfica quando ele navega para o OneDrive, o inicializador de aplicativos do Office 365 ou um navegador da Web.

### <a name="permissions-on-onedrive-content"></a>Permissões sobre o conteúdo do OneDrive

Os usuários com permissões para o conteúdo do OneDrive continuarão a ter acesso ao conteúdo durante a movimentação e após sua conclusão.

### <a name="onedrive-sync-client"></a>Cliente de sincronização do OneDrive 

O cliente de sincronização do OneDrive detectará automaticamente e transferirá perfeitamente a sincronização para o novo local do OneDrive após a conclusão da movimentação geográfica do OneDrive. O usuário não precisa entrar novamente nem realizar outras ações. (Precisa da versão 17.3.6943.0625 ou posterior do cliente de sincronização.)

Se um usuário atualizar um arquivo enquanto a movimentação geográfica do OneDrive estiver em andamento, o cliente de sincronização o notificará de que uploads de arquivo estão pendentes enquanto a movimentação estiver em andamento.

### <a name="sharing-links"></a>Links de compartilhamento 

Após a conclusão da movimentação geográfica do OneDrive, os links compartilhados existentes para os arquivos que foram movidos serão redirecionados automaticamente para a nova localização geográfica.

### <a name="onenote-experience"></a>Experiência do OneNote 

O cliente do OneNote para win32 e o aplicativo UWP (Universal) detectarão automaticamente e sincronizarão perfeitamente os blocos de anotações com o novo local no OneDrive após a conclusão da movimentação geográfica do OneDrive. O usuário não precisa entrar novamente nem realizar outras ações. O único indicador visível para o usuário é que a sincronização de bloco de anotações falha quando a movimentação geográfica do OneDrive está em andamento. Essa experiência está disponível nas seguintes versões do cliente do OneNote:

-   OneNote win32 – versão 16.0.8326.2096 (e posteriores)

-   OneNote UWP – versão 16.0.8431.1006 (e posteriores)

-   Aplicativo móvel do OneNote – versão 16.0.8431.1011 (e posteriores)

### <a name="teams-app"></a>Aplicativo de equipes

Após a conclusão da movimentação geográfica do OneDrive, os usuários terão acesso aos arquivos do OneDrive no aplicativo do Teams. Além disso, arquivos compartilhados por chat do Teams no OneDrive antes da movimentação geográfica continuarão funcionando após a movimentação ser concluída.

### <a name="onedrive-for-business-mobile-app-ios"></a>Aplicativo móvel do OneDrive for Business (iOS) 

Após a conclusão da movimentação geográfica do OneDrive, o usuário precisa sair e entrar novamente no aplicativo móvel do iOS para fazer a sincronização com o novo local do OneDrive.

### <a name="existing-followed-groups-and-sites"></a>Grupos e sites seguidos existentes

Os grupos e sites seguidos serão mostrados no OneDrive for Business do usuário, independentemente da localização geográfica. Sites e grupos hospedados em outra localização geográfica serão abertos em uma guia separada.
