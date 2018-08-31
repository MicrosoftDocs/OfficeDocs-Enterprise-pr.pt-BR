---
title: Exibir o status da sincronização de diretório no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Saiba como desativar a sincronização de diretório. Também é possível exibir seu status.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539445"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="be9e9-104">Exibir o status da sincronização de diretório no Office 365</span><span class="sxs-lookup"><span data-stu-id="be9e9-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="be9e9-105">Se você tiver integrado seu Active Directory no local com o Azure AD por meio da sincronização seu ambiente local com o Office 365, você também pode verificar o status da sua sincronização.</span><span class="sxs-lookup"><span data-stu-id="be9e9-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="be9e9-106">Exibir status de sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="be9e9-106">View directory synchronization status</span></span>
- <span data-ttu-id="be9e9-107">Entrar no Centro de administração do Office 365 e escolha **DirSync Status** na home page.</span><span class="sxs-lookup"><span data-stu-id="be9e9-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="be9e9-p102">Como alternativa, você pode ir para **usuários** \> **usuários ativos**e na página **usuários ativos** , escolha **mais** \> **sincronização de diretórios**. No painel de **Sincronização de diretórios** , escolha **vá para gerenciamento de DirSync**.</span><span class="sxs-lookup"><span data-stu-id="be9e9-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="be9e9-110">Informações sobre a página de sincronização de diretório de gerenciar</span><span class="sxs-lookup"><span data-stu-id="be9e9-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="be9e9-111">A tabela a seguir lista os recursos que você pode obter informações sobre na página.</span><span class="sxs-lookup"><span data-stu-id="be9e9-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="be9e9-p103">Se houver um problema com a sincronização de diretórios, os erros são listados nesta página também. Para obter mais informações sobre erros diferentes que podem ser encontrados, consulte [identificar erros de sincronização de diretórios no Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="be9e9-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="be9e9-114">**Item**</span><span class="sxs-lookup"><span data-stu-id="be9e9-114">**Item**</span></span>|<span data-ttu-id="be9e9-115">**What's for**</span><span class="sxs-lookup"><span data-stu-id="be9e9-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="be9e9-116">**Domínios verificados**</span><span class="sxs-lookup"><span data-stu-id="be9e9-116">**Domains verified**</span></span> | <span data-ttu-id="be9e9-117">Número de domínios no seu locatário do Office 365 que você verificou você é proprietário.</span><span class="sxs-lookup"><span data-stu-id="be9e9-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="be9e9-118">**Domínios não verificados**</span><span class="sxs-lookup"><span data-stu-id="be9e9-118">**Domains not verified**</span></span> | <span data-ttu-id="be9e9-119">Domínios você tenha adicionado, mas não verificada.</span><span class="sxs-lookup"><span data-stu-id="be9e9-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="be9e9-120">**Sincronização de diretório ativada**</span><span class="sxs-lookup"><span data-stu-id="be9e9-120">**Directory sync enabled**</span></span> |<span data-ttu-id="be9e9-p104">True ou False. Especifica se você habilitou a sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="be9e9-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="be9e9-123">**Sincronização de diretório mais recente**</span><span class="sxs-lookup"><span data-stu-id="be9e9-123">**Latest directory sync**</span></span> | <span data-ttu-id="be9e9-p105">Hora da última sincronização de diretório foi executada. Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização foram há mais de três dias.</span><span class="sxs-lookup"><span data-stu-id="be9e9-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="be9e9-126">**Sincronização de senha habilitada**</span><span class="sxs-lookup"><span data-stu-id="be9e9-126">**Password sync enabled**</span></span> | <span data-ttu-id="be9e9-p106">True ou False. Especifica se você tiver a sincronização de hash de senha entre nosso local e seu locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="be9e9-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="be9e9-129">**Última sincronização de senha**</span><span class="sxs-lookup"><span data-stu-id="be9e9-129">**Last Password Sync**</span></span> | <span data-ttu-id="be9e9-p107">Hora da última sincronização de hash de senha foi executada. Exibirá um aviso e um link para uma ferramenta de solução de problemas se a última sincronização foram há mais de três dias.</span><span class="sxs-lookup"><span data-stu-id="be9e9-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="be9e9-132">**Versão do cliente de sincronização de diretório**</span><span class="sxs-lookup"><span data-stu-id="be9e9-132">**Directory sync client version**</span></span> | <span data-ttu-id="be9e9-133">Contém um link de download, se uma nova versão do Azure Connect do AD foi liberada.</span><span class="sxs-lookup"><span data-stu-id="be9e9-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="be9e9-134">**Ferramenta IDFix**</span><span class="sxs-lookup"><span data-stu-id="be9e9-134">**IDFix Tool**</span></span> | <span data-ttu-id="be9e9-135">Baixe o link para o [IDFix](install-and-run-idfix.md), uma ferramenta que você pode usar para verificar a você o Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="be9e9-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="be9e9-136">**Conta de serviço de sincronização de diretório**</span><span class="sxs-lookup"><span data-stu-id="be9e9-136">**Directory sync service account**</span></span> | <span data-ttu-id="be9e9-137">Exibe o nome do que a conta de serviço de sincronização de diretório do Office 365.</span><span class="sxs-lookup"><span data-stu-id="be9e9-137">Displays the name of you Office 365 directory sync service account.</span></span> |