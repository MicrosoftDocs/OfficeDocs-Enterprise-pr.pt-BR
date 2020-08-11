---
title: Exibir o status de sincronização do diretório no Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Neste artigo, saiba como você pode verificar o status da sua sincronização de diretórios no Office 365.
ms.openlocfilehash: 9aaad085854326ebb6542f03256ae851b27f0980
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605857"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="df59f-103">Exibir o status de sincronização do diretório no Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="df59f-103">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="df59f-104">Se você integrou o Active Directory local ao Azure AD sincronizando seu ambiente local com o Microsoft 365, você também pode verificar o status da sua sincronização.</span><span class="sxs-lookup"><span data-stu-id="df59f-104">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="df59f-105">Exibir o status da sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="df59f-105">View directory synchronization status</span></span>

- <span data-ttu-id="df59f-106">Entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com) e escolha **status DirSync** na página inicial.</span><span class="sxs-lookup"><span data-stu-id="df59f-106">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="df59f-107">Como alternativa, você pode ir para **Users** \> **usuários ativos**do usuário e, na página **usuários ativos** , escolha **mais** \> **sincronização de diretórios**.</span><span class="sxs-lookup"><span data-stu-id="df59f-107">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="df59f-108">No painel de **sincronização de diretórios** , escolha **ir para gerenciamento DirSync**.</span><span class="sxs-lookup"><span data-stu-id="df59f-108">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="df59f-109">Informações na página Gerenciar sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="df59f-109">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="df59f-110">A tabela a seguir lista os recursos para os quais você pode obter informações na página.</span><span class="sxs-lookup"><span data-stu-id="df59f-110">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="df59f-111">Se houver um problema com a sincronização de diretório, os erros também serão listados nessa página.</span><span class="sxs-lookup"><span data-stu-id="df59f-111">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="df59f-112">Para obter mais informações sobre diferentes erros que você pode encontrar, consulte [identificar erros de sincronização de diretório no Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="df59f-112">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="df59f-113">**Item**</span><span class="sxs-lookup"><span data-stu-id="df59f-113">**Item**</span></span>|<span data-ttu-id="df59f-114">**Para que serve**</span><span class="sxs-lookup"><span data-stu-id="df59f-114">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="df59f-115">**Domínios verificados**</span><span class="sxs-lookup"><span data-stu-id="df59f-115">**Domains verified**</span></span> | <span data-ttu-id="df59f-116">Número de domínios em seu locatário do Microsoft 365 que você verificou você possui.</span><span class="sxs-lookup"><span data-stu-id="df59f-116">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="df59f-117">**Domínios não verificados**</span><span class="sxs-lookup"><span data-stu-id="df59f-117">**Domains not verified**</span></span> | <span data-ttu-id="df59f-118">Domínios que você adicionou, mas não verificados.</span><span class="sxs-lookup"><span data-stu-id="df59f-118">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="df59f-119">**Sincronização de diretório habilitada**</span><span class="sxs-lookup"><span data-stu-id="df59f-119">**Directory sync enabled**</span></span> |<span data-ttu-id="df59f-120">True ou false.</span><span class="sxs-lookup"><span data-stu-id="df59f-120">True or False.</span></span> <span data-ttu-id="df59f-121">Especifica se você habilitou a sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="df59f-121">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="df59f-122">**Sincronização de diretório mais recente**</span><span class="sxs-lookup"><span data-stu-id="df59f-122">**Latest directory sync**</span></span> | <span data-ttu-id="df59f-123">Última vez em que a sincronização de diretório foi executada.</span><span class="sxs-lookup"><span data-stu-id="df59f-123">Last time directory sync ran.</span></span> <span data-ttu-id="df59f-124">Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização tiver mais de três dias.</span><span class="sxs-lookup"><span data-stu-id="df59f-124">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="df59f-125">**Sincronização de senha habilitada**</span><span class="sxs-lookup"><span data-stu-id="df59f-125">**Password sync enabled**</span></span> | <span data-ttu-id="df59f-126">True ou false.</span><span class="sxs-lookup"><span data-stu-id="df59f-126">True or False.</span></span> <span data-ttu-id="df59f-127">Especifica se a sincronização de hash de senha deve ser sincronizada entre o seu locatário do Microsoft 365 e no local.</span><span class="sxs-lookup"><span data-stu-id="df59f-127">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="df59f-128">**Última sincronização de senha**</span><span class="sxs-lookup"><span data-stu-id="df59f-128">**Last Password Sync**</span></span> | <span data-ttu-id="df59f-129">Última vez em que a sincronização de hash de senha foi executada.</span><span class="sxs-lookup"><span data-stu-id="df59f-129">Last time password hash sync ran.</span></span> <span data-ttu-id="df59f-130">Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização tiver mais de três dias.</span><span class="sxs-lookup"><span data-stu-id="df59f-130">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="df59f-131">**Versão do cliente de sincronização de diretório**</span><span class="sxs-lookup"><span data-stu-id="df59f-131">**Directory sync client version**</span></span> | <span data-ttu-id="df59f-132">Contém um link de download se uma nova versão do Azure AD Connect foi liberada.</span><span class="sxs-lookup"><span data-stu-id="df59f-132">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="df59f-133">**Conta de serviço de sincronização de diretório**</span><span class="sxs-lookup"><span data-stu-id="df59f-133">**Directory sync service account**</span></span> | <span data-ttu-id="df59f-134">Exibe o nome da sua conta de serviço de sincronização de diretório do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="df59f-134">Displays the name of your Microsoft 365 directory sync service account.</span></span> |