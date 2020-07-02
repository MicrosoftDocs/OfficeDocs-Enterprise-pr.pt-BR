---
title: Exclusão de dados do Skype for Business do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Uma explicação da exclusão de dados no Skype for Business.
ms.openlocfilehash: 7c94c5d1ddfb5a8056e139d664627dd1e7bed0de
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997791"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a><span data-ttu-id="b03f7-103">Exclusão de dados do Skype for Business no Office 365</span><span class="sxs-lookup"><span data-stu-id="b03f7-103">Skype for Business Data Deletion in Office 365</span></span>

<span data-ttu-id="b03f7-104">Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings.</span><span class="sxs-lookup"><span data-stu-id="b03f7-104">Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings.</span></span> <span data-ttu-id="b03f7-105">The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.</span><span class="sxs-lookup"><span data-stu-id="b03f7-105">The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.</span></span>

<span data-ttu-id="b03f7-106">All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users.</span><span class="sxs-lookup"><span data-stu-id="b03f7-106">All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users.</span></span> <span data-ttu-id="b03f7-107">There is no direct control of archiving settings from within the Skype for Business admin center.</span><span class="sxs-lookup"><span data-stu-id="b03f7-107">There is no direct control of archiving settings from within the Skype for Business admin center.</span></span>

<span data-ttu-id="b03f7-108">Os seguintes tipos de conteúdo não são arquivados no Skype for Business:</span><span class="sxs-lookup"><span data-stu-id="b03f7-108">The following types of content are not archived in Skype for Business:</span></span>

- <span data-ttu-id="b03f7-109">Transferências de arquivo ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="b03f7-109">Peer-to-peer file transfers</span></span>
- <span data-ttu-id="b03f7-110">Áudio/vídeo para mensagens instantâneas ponto a ponto e conferências</span><span class="sxs-lookup"><span data-stu-id="b03f7-110">Audio/video for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="b03f7-111">Compartilhamento de aplicativo para mensagens instantâneas ponto a ponto e conferências</span><span class="sxs-lookup"><span data-stu-id="b03f7-111">Application sharing for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="b03f7-112">Anotações de conferência</span><span class="sxs-lookup"><span data-stu-id="b03f7-112">Conferencing annotations</span></span> 

## <a name="meeting-content-retention"></a><span data-ttu-id="b03f7-113">Retenção de conteúdo de reunião</span><span class="sxs-lookup"><span data-stu-id="b03f7-113">Meeting Content Retention</span></span>

<span data-ttu-id="b03f7-114">Os clientes que usam o Skype for Business podem carregar conteúdo para uma reunião do Skype for Business como anexos, como apresentações do PowerPoint, arquivos do OneNote e outros arquivos.</span><span class="sxs-lookup"><span data-stu-id="b03f7-114">Customers using Skype for Business can upload content to a Skype for Business meeting as attachments, such as PowerPoint presentations, OneNote files, and other files.</span></span> <span data-ttu-id="b03f7-115">O período de retenção para o conteúdo que foi carregado para uma reunião é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b03f7-115">The retention period for content that has been uploaded to a meeting is as follows:</span></span>

- <span data-ttu-id="b03f7-116">**Reunião de uso único** -o conteúdo é mantido por 15 dias a partir de quando a última pessoa deixa a reunião.</span><span class="sxs-lookup"><span data-stu-id="b03f7-116">**One-time meeting** - Content is retained for 15 days starting from when the last person leaves the meeting.</span></span>
- <span data-ttu-id="b03f7-117">**Reunião recorrente** -o conteúdo é mantido por 15 dias após a última pessoa sair da última sessão da reunião.</span><span class="sxs-lookup"><span data-stu-id="b03f7-117">**Recurring meeting** - Content is retained for 15 days after the last person leaves the last session of the meeting.</span></span> <span data-ttu-id="b03f7-118">O temporizador de retenção reinicia se alguém ingressar na mesma sessão de reunião em 15 dias.</span><span class="sxs-lookup"><span data-stu-id="b03f7-118">The retention timer resets if someone joins the same meeting session within 15 days.</span></span> <span data-ttu-id="b03f7-119">Por exemplo, suponha que uma reunião do Skype for Business está agendada para ocorrer semanal por um ano, e um arquivo é carregado para a reunião durante a primeira instância.</span><span class="sxs-lookup"><span data-stu-id="b03f7-119">For example, assume a Skype for Business meeting is scheduled to occur on a weekly basis for one year, and a file is uploaded to the meeting during the first instance.</span></span> <span data-ttu-id="b03f7-120">Se pelo menos uma pessoa ingressar na sessão de reunião toda semana, o arquivo será mantido nos servidores do Skype for Business online por todo o ano mais 15 dias após a última pessoa sair da última reunião da série.</span><span class="sxs-lookup"><span data-stu-id="b03f7-120">If at least one person joins the meeting session every week, the file is retained in Skype for Business Online servers for the entire year plus 15 days after the last person leaves the last meeting of the series.</span></span>
- <span data-ttu-id="b03f7-121">**Reunião agora** -o conteúdo é retido por 8 horas após a hora de término da reunião.</span><span class="sxs-lookup"><span data-stu-id="b03f7-121">**Meet Now meeting** - Content is retained for 8 hours after the meeting end time.</span></span>

> [!NOTE]
> <span data-ttu-id="b03f7-122">Se um usuário não estiver licenciado ou estiver desabilitado (por exemplo, se **msRTCSIP-userhabilitado** for definido como *false*) e, em seguida, for novamente licenciado ou reabilitado, o conteúdo da reunião não será mantido.</span><span class="sxs-lookup"><span data-stu-id="b03f7-122">If a user is unlicensed or disabled (e.g., if **msRTCSIP-userenabled** is set to *False*), and is then re-licensed or reenabled, meeting content is not retained.</span></span>

## <a name="meeting-expiration"></a><span data-ttu-id="b03f7-123">Expiração de reunião</span><span class="sxs-lookup"><span data-stu-id="b03f7-123">Meeting Expiration</span></span>

<span data-ttu-id="b03f7-124">Os usuários podem acessar uma reunião específica, após a reunião ter terminado, sujeitos aos seguinte períodos de expiração:</span><span class="sxs-lookup"><span data-stu-id="b03f7-124">Users can access a specific meeting after the meeting has ended, subject to the following expiration time periods:</span></span>

- <span data-ttu-id="b03f7-125">**Reunião de uso único** – a reunião expira 14 dias após a hora de término da reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="b03f7-125">**One-time meeting** - Meeting expires 14 days after the scheduled meeting end time.</span></span>
- <span data-ttu-id="b03f7-126">**Reunião recorrente com data de término** – a reunião expira 14 dias após a hora de término agendada da última ocorrência da reunião.</span><span class="sxs-lookup"><span data-stu-id="b03f7-126">**Recurring meeting with end date** - Meeting expires 14 days after the scheduled end time of the last meeting occurrence.</span></span>
- <span data-ttu-id="b03f7-127">**Reunião agora** – a reunião expira após 8 horas.</span><span class="sxs-lookup"><span data-stu-id="b03f7-127">**Meet Now meeting** - Meeting expires after 8 hours.</span></span>

## <a name="whiteboard-collaboration"></a><span data-ttu-id="b03f7-128">Colaboração de quadro de comunicações</span><span class="sxs-lookup"><span data-stu-id="b03f7-128">Whiteboard Collaboration</span></span>

<span data-ttu-id="b03f7-129">As anotações feitas em quadros de comunicação serão vistas por todos os participantes.</span><span class="sxs-lookup"><span data-stu-id="b03f7-129">Annotations made on whiteboards will be seen by all participants.</span></span> <span data-ttu-id="b03f7-130">Ao salvar um quadro de comunicações, o quadro de comunicações e todas as anotações serão armazenados em um Skype for Business Server e serão retidos no servidor de acordo com as políticas de expiração de conteúdo da reunião definidas pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="b03f7-130">When saving a whiteboard, the whiteboard and all annotations will be stored on a Skype for Business server, and it will be retained on the server according to meeting content expiration policies set by the administrator.</span></span>

## <a name="audio-test-service"></a><span data-ttu-id="b03f7-131">Serviço de teste de áudio</span><span class="sxs-lookup"><span data-stu-id="b03f7-131">Audio Test Service</span></span>

<span data-ttu-id="b03f7-132">Um curto (aproximadamente 5 segundos) amostra de sua voz é registrado durante a chamada do serviço de teste de áudio.</span><span class="sxs-lookup"><span data-stu-id="b03f7-132">A short (approximately 5 seconds) sample of your voice is recorded during the Audio Test Service call.</span></span> <span data-ttu-id="b03f7-133">O exemplo de voz é usado para verificar e/ou verificar a qualidade de som da chamada do Skype for Business com base na qualidade da gravação.</span><span class="sxs-lookup"><span data-stu-id="b03f7-133">The voice sample is used by you to check and/or verify the sound quality of your Skype for Business call based on the quality of the recording.</span></span> <span data-ttu-id="b03f7-134">Quando a chamada de serviço de teste de áudio termina, a amostra de voz é excluída.</span><span class="sxs-lookup"><span data-stu-id="b03f7-134">When the Audio Test Service call ends, the voice sample is deleted.</span></span>

## <a name="persistent-group-chat"></a><span data-ttu-id="b03f7-135">Chat de grupo persistente</span><span class="sxs-lookup"><span data-stu-id="b03f7-135">Persistent Group Chat</span></span>

<span data-ttu-id="b03f7-136">O chat de grupo persistente armazena o conteúdo de conversas de chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="b03f7-136">Persistent Group Chat stores the content of group chat conversations.</span></span> <span data-ttu-id="b03f7-137">Se for habilitada, o administrador poderá controlar o período de retenção, o servidor em que essas informações estão armazenadas, se o histórico de chat de grupo for arquivado para fins de conformidade ou outras finalidades, e gerenciar/modificar quaisquer propriedades em uma sala.</span><span class="sxs-lookup"><span data-stu-id="b03f7-137">If enabled, the administrator can control the retention period, the server on which this information is stored, if Group Chat history is archived for compliance or other purposes, and manage/modify any properties on a room.</span></span> <span data-ttu-id="b03f7-138">Os usuários com funções diferentes têm acesso diferente aos dados persistentes da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b03f7-138">Users with different roles have different access to the persisted data, as follows:</span></span>

- <span data-ttu-id="b03f7-139">Os administradores podem excluir conteúdo mais antigo (por exemplo, o conteúdo postado antes de uma determinada data) de qualquer sala de chat para manter o tamanho do banco de dados crescendo muito.</span><span class="sxs-lookup"><span data-stu-id="b03f7-139">Administrators can delete older content (for example, content posted before a certain date) from any chat room to keep the size of the database from growing greatly.</span></span> <span data-ttu-id="b03f7-140">Ou podem remover ou substituir mensagens consideradas inadequadas para uma determinada sala de chat (ou consideradas inadequadas).</span><span class="sxs-lookup"><span data-stu-id="b03f7-140">Or, they can remove or replace messages considered inappropriate for a given chat room (or considered unsuitable).</span></span>
- <span data-ttu-id="b03f7-141">Os usuários finais, incluindo autores de mensagens, não podem excluir conteúdo de qualquer sala de chat.</span><span class="sxs-lookup"><span data-stu-id="b03f7-141">End-users, including message authors, cannot delete content from any chat room.</span></span>
- <span data-ttu-id="b03f7-142">Os gerentes de salas de chat podem desabilitar salas, mas não podem excluir salas.</span><span class="sxs-lookup"><span data-stu-id="b03f7-142">Chat room managers can disable rooms but cannot delete rooms.</span></span> <span data-ttu-id="b03f7-143">Somente os administradores podem excluir uma sala de chat após sua criação.</span><span class="sxs-lookup"><span data-stu-id="b03f7-143">Only administrators can delete a chat room after it is created.</span></span>