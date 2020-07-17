---
title: Controles de acesso corporativo do Microsoft 365 Yammer
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
description: 'Resumo: um breve resumo sobre os controles de acesso corporativo do Yammer no ambiente de produção.'
ms.openlocfilehash: 0da479eb36359ec6b795a8e4323441edc4678f1a
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44775110"
---
# <a name="yammer-enterprise-access-controls"></a><span data-ttu-id="0ff26-103">Controles de acesso corporativo do Yammer</span><span class="sxs-lookup"><span data-stu-id="0ff26-103">Yammer enterprise access controls</span></span> 

<span data-ttu-id="0ff26-104">O acesso físico e lógico ao ambiente de produção do Yammer é restrito a um pequeno conjunto de pessoas (infraestrutura e operações).</span><span class="sxs-lookup"><span data-stu-id="0ff26-104">Physical and logical access to the Yammer production environment is restricted to a small set of people (infrastructure and operations).</span></span> <span data-ttu-id="0ff26-105">Como em outros engenheiros da Microsoft 365, os engenheiros do Yammer têm zero acesso à dados dos clientes.</span><span class="sxs-lookup"><span data-stu-id="0ff26-105">As with other Microsoft 365 engineers, Yammer engineers have zero standing access to customer data.</span></span> <span data-ttu-id="0ff26-106">O acesso deve ser solicitado usando um sistema de controle de acesso just-in-time baseado em aprovação semelhante ao Lockbox com um número limitado de aprovadores.</span><span class="sxs-lookup"><span data-stu-id="0ff26-106">Access must be requested using an approval-based just-in-time access control system similar to Lockbox with a limited number of approvers.</span></span> <span data-ttu-id="0ff26-107">Os aprovadores verificam a solicitação (por exemplo, eles verificam se a solicitação é legítima com base em necessidade, caso de negócios, hora etc.) e, em seguida, aprovar ou negar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="0ff26-107">Approvers verify the request (for example, they verify whether the request is legitimate based on need, business case, time, etc.), and then approve or deny the request.</span></span> <span data-ttu-id="0ff26-108">Se a solicitação for aprovada, o acesso JIT será concedido para um tempo definido e limitado.</span><span class="sxs-lookup"><span data-stu-id="0ff26-108">If the request is approved, JIT access is granted for a defined and limited time.</span></span> <span data-ttu-id="0ff26-109">Após o tempo de acesso ser excedido, o acesso expira automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0ff26-109">After access time is exceeded, the access automatically expires.</span></span>

<span data-ttu-id="0ff26-110">Como em outros serviços do Microsoft 365, todo o acesso ao ambiente de produção do Yammer usa a autenticação multifator.</span><span class="sxs-lookup"><span data-stu-id="0ff26-110">As with other Microsoft 365 services, all access to the Yammer production environment uses multi-factor authentication.</span></span> <span data-ttu-id="0ff26-111">Todos os acessos e o histórico de comandos são atribuídos a um usuário e registrados e revisados regularmente pela equipe de segurança do Yammer.</span><span class="sxs-lookup"><span data-stu-id="0ff26-111">All access and command history is attributed to a user, and logged and reviewed regularly by the Yammer security team.</span></span>

<span data-ttu-id="0ff26-112">Para obter mais informações sobre administração e gerenciamento do Yammer, consulte [ajuda do administrador do Yammer](https://docs.microsoft.com/yammer/yammer-landing-page).</span><span class="sxs-lookup"><span data-stu-id="0ff26-112">For more information about Yammer administration and management, see [Yammer admin help](https://docs.microsoft.com/yammer/yammer-landing-page).</span></span>