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
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Saiba como desativar a sincronização de diretórios. Você também pode exibir seu status.
ms.openlocfilehash: 4c2f0baf6d3657e3eb9974ff7d4f8109e52e603b
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571034"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="f1c99-104">Exibir o status de sincronização do diretório no Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f1c99-104">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="f1c99-105">Se você integrou o Active Directory local ao Azure AD sincronizando seu ambiente local com o Microsoft 365, você também pode verificar o status da sua sincronização.</span><span class="sxs-lookup"><span data-stu-id="f1c99-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="f1c99-106">Exibir o status da sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="f1c99-106">View directory synchronization status</span></span>

- <span data-ttu-id="f1c99-107">Entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com) e escolha **status DirSync** na página inicial.</span><span class="sxs-lookup"><span data-stu-id="f1c99-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="f1c99-108">Como alternativa, você pode ir para **Users** \> **usuários ativos**do usuário e, na página **usuários ativos** , escolha **mais** \> **sincronização de diretórios**.</span><span class="sxs-lookup"><span data-stu-id="f1c99-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="f1c99-109">No painel de **sincronização de diretórios** , escolha **ir para gerenciamento DirSync**.</span><span class="sxs-lookup"><span data-stu-id="f1c99-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="f1c99-110">Informações na página Gerenciar sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="f1c99-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="f1c99-111">A tabela a seguir lista os recursos para os quais você pode obter informações na página.</span><span class="sxs-lookup"><span data-stu-id="f1c99-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="f1c99-112">Se houver um problema com a sincronização de diretório, os erros também serão listados nessa página.</span><span class="sxs-lookup"><span data-stu-id="f1c99-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="f1c99-113">Para obter mais informações sobre diferentes erros que você pode encontrar, consulte [identificar erros de sincronização de diretório no Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="f1c99-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="f1c99-114">**Item**</span><span class="sxs-lookup"><span data-stu-id="f1c99-114">**Item**</span></span>|<span data-ttu-id="f1c99-115">**Para que serve**</span><span class="sxs-lookup"><span data-stu-id="f1c99-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f1c99-116">**Domínios verificados**</span><span class="sxs-lookup"><span data-stu-id="f1c99-116">**Domains verified**</span></span> | <span data-ttu-id="f1c99-117">Número de domínios em seu locatário do Microsoft 365 que você verificou você possui.</span><span class="sxs-lookup"><span data-stu-id="f1c99-117">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="f1c99-118">**Domínios não verificados**</span><span class="sxs-lookup"><span data-stu-id="f1c99-118">**Domains not verified**</span></span> | <span data-ttu-id="f1c99-119">Domínios que você adicionou, mas não verificados.</span><span class="sxs-lookup"><span data-stu-id="f1c99-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="f1c99-120">**Sincronização de diretório habilitada**</span><span class="sxs-lookup"><span data-stu-id="f1c99-120">**Directory sync enabled**</span></span> |<span data-ttu-id="f1c99-121">True ou false.</span><span class="sxs-lookup"><span data-stu-id="f1c99-121">True or False.</span></span> <span data-ttu-id="f1c99-122">Especifica se você habilitou a sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="f1c99-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="f1c99-123">**Sincronização de diretório mais recente**</span><span class="sxs-lookup"><span data-stu-id="f1c99-123">**Latest directory sync**</span></span> | <span data-ttu-id="f1c99-124">Última vez em que a sincronização de diretório foi executada.</span><span class="sxs-lookup"><span data-stu-id="f1c99-124">Last time directory sync ran.</span></span> <span data-ttu-id="f1c99-125">Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização tiver mais de três dias.</span><span class="sxs-lookup"><span data-stu-id="f1c99-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="f1c99-126">**Sincronização de senha habilitada**</span><span class="sxs-lookup"><span data-stu-id="f1c99-126">**Password sync enabled**</span></span> | <span data-ttu-id="f1c99-127">True ou false.</span><span class="sxs-lookup"><span data-stu-id="f1c99-127">True or False.</span></span> <span data-ttu-id="f1c99-128">Especifica se a sincronização de hash de senha deve ser sincronizada entre o seu locatário do Microsoft 365 e no local.</span><span class="sxs-lookup"><span data-stu-id="f1c99-128">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="f1c99-129">**Última sincronização de senha**</span><span class="sxs-lookup"><span data-stu-id="f1c99-129">**Last Password Sync**</span></span> | <span data-ttu-id="f1c99-130">Última vez em que a sincronização de hash de senha foi executada.</span><span class="sxs-lookup"><span data-stu-id="f1c99-130">Last time password hash sync ran.</span></span> <span data-ttu-id="f1c99-131">Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização tiver mais de três dias.</span><span class="sxs-lookup"><span data-stu-id="f1c99-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="f1c99-132">**Versão do cliente de sincronização de diretório**</span><span class="sxs-lookup"><span data-stu-id="f1c99-132">**Directory sync client version**</span></span> | <span data-ttu-id="f1c99-133">Contém um link de download se uma nova versão do Azure AD Connect foi liberada.</span><span class="sxs-lookup"><span data-stu-id="f1c99-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="f1c99-134">**Conta de serviço de sincronização de diretório**</span><span class="sxs-lookup"><span data-stu-id="f1c99-134">**Directory sync service account**</span></span> | <span data-ttu-id="f1c99-135">Exibe o nome da sua conta de serviço de sincronização de diretório do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f1c99-135">Displays the name of your Microsoft 365 directory sync service account.</span></span> |