---
title: Exibir status de sincronização de diretório no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001564"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="a528e-104">Exibir status de sincronização de diretório no Office 365</span><span class="sxs-lookup"><span data-stu-id="a528e-104">View directory synchronization status in Office 365</span></span>

<span data-ttu-id="a528e-105">Se você integrou o Active Directory local ao Azure AD sincronizando seu ambiente local com o Office 365, você também pode verificar o status da sua sincronização.</span><span class="sxs-lookup"><span data-stu-id="a528e-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="a528e-106">Exibir status de sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="a528e-106">View directory synchronization status</span></span>

- <span data-ttu-id="a528e-107">Entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com) e escolha **status DirSync** na página inicial.</span><span class="sxs-lookup"><span data-stu-id="a528e-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="a528e-108">Como alternativa, você pode ir para \*\*\*\* \> **usuários ativos**do usuário e, na **página usuários ativos** , escolha **mais** \> **sincronização de diretórios**.</span><span class="sxs-lookup"><span data-stu-id="a528e-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="a528e-109">No painel de **sincronização de diretórios** , escolha **ir para gerenciamento DirSync**.</span><span class="sxs-lookup"><span data-stu-id="a528e-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="a528e-110">Informações na página Gerenciar sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="a528e-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="a528e-111">A tabela a seguir lista os recursos para os quais você pode obter informações na página.</span><span class="sxs-lookup"><span data-stu-id="a528e-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="a528e-112">Se houver um problema com a sincronização de diretório, os erros também serão listados nessa página.</span><span class="sxs-lookup"><span data-stu-id="a528e-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="a528e-113">Para obter mais informações sobre diferentes erros que você pode encontrar, consulte [identificar erros de sincronização de diretório no Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="a528e-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="a528e-114">**Item**</span><span class="sxs-lookup"><span data-stu-id="a528e-114">**Item**</span></span>|<span data-ttu-id="a528e-115">**Para que serve**</span><span class="sxs-lookup"><span data-stu-id="a528e-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a528e-116">**Domínios verificados**</span><span class="sxs-lookup"><span data-stu-id="a528e-116">**Domains verified**</span></span> | <span data-ttu-id="a528e-117">Número de domínios em seu locatário do Office 365 que você verificou você possui.</span><span class="sxs-lookup"><span data-stu-id="a528e-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="a528e-118">**Domínios não verificados**</span><span class="sxs-lookup"><span data-stu-id="a528e-118">**Domains not verified**</span></span> | <span data-ttu-id="a528e-119">Domínios que você adicionou, mas não verificados.</span><span class="sxs-lookup"><span data-stu-id="a528e-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="a528e-120">**Sincronização de diretório habilitada**</span><span class="sxs-lookup"><span data-stu-id="a528e-120">**Directory sync enabled**</span></span> |<span data-ttu-id="a528e-121">True ou false.</span><span class="sxs-lookup"><span data-stu-id="a528e-121">True or False.</span></span> <span data-ttu-id="a528e-122">Especifica se você habilitou a sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="a528e-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="a528e-123">**Sincronização de diretório mais recente**</span><span class="sxs-lookup"><span data-stu-id="a528e-123">**Latest directory sync**</span></span> | <span data-ttu-id="a528e-124">Última vez em que a sincronização de diretório foi executada.</span><span class="sxs-lookup"><span data-stu-id="a528e-124">Last time directory sync ran.</span></span> <span data-ttu-id="a528e-125">Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização tiver mais de três dias.</span><span class="sxs-lookup"><span data-stu-id="a528e-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="a528e-126">**Sincronização de senha habilitada**</span><span class="sxs-lookup"><span data-stu-id="a528e-126">**Password sync enabled**</span></span> | <span data-ttu-id="a528e-127">True ou false.</span><span class="sxs-lookup"><span data-stu-id="a528e-127">True or False.</span></span> <span data-ttu-id="a528e-128">Especifica se você tem sincronização de hash de senha entre o seu locatário do Office 365 e o local.</span><span class="sxs-lookup"><span data-stu-id="a528e-128">Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="a528e-129">**Última sincronização de senha**</span><span class="sxs-lookup"><span data-stu-id="a528e-129">**Last Password Sync**</span></span> | <span data-ttu-id="a528e-130">Última vez em que a sincronização de hash de senha foi executada.</span><span class="sxs-lookup"><span data-stu-id="a528e-130">Last time password hash sync ran.</span></span> <span data-ttu-id="a528e-131">Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização tiver mais de três dias.</span><span class="sxs-lookup"><span data-stu-id="a528e-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="a528e-132">**Versão do cliente de sincronização de diretório**</span><span class="sxs-lookup"><span data-stu-id="a528e-132">**Directory sync client version**</span></span> | <span data-ttu-id="a528e-133">Contém um link de download se uma nova versão do Azure AD Connect foi liberada.</span><span class="sxs-lookup"><span data-stu-id="a528e-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="a528e-134">**Ferramenta IDFix**</span><span class="sxs-lookup"><span data-stu-id="a528e-134">**IDFix Tool**</span></span> | <span data-ttu-id="a528e-135">Link de download para o [IDFix](install-and-run-idfix.md), uma ferramenta que você pode usar para verificar se você localIzou o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a528e-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="a528e-136">**Conta de serviço de sincronização de diretório**</span><span class="sxs-lookup"><span data-stu-id="a528e-136">**Directory sync service account**</span></span> | <span data-ttu-id="a528e-137">Exibe o nome da conta do serviço de sincronização de diretório do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a528e-137">Displays the name of you Office 365 directory sync service account.</span></span> |