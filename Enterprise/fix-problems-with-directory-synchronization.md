---
title: Corrigindo problemas de sincronização de diretório no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Descreve causas comuns de problemas com a sincronização de diretórios no Office 365 e fornece alguns métodos para ajudar a solucionar problemas.
ms.openlocfilehash: cc0fe15d0d49542489ac1e586efbe99d0846b3ab
ms.sourcegitcommit: fbd2f3fb297c508212baed3ee9d1ce51765cc8bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39254520"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="3bc98-103">Corrigindo problemas de sincronização de diretório no Office 365</span><span class="sxs-lookup"><span data-stu-id="3bc98-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="3bc98-104">Com a sincronização de diretórios, você pode continuar a gerenciar os usuários e grupos locais, e sincronizar acréscimos, eliminações e alterações com a nuvem.</span><span class="sxs-lookup"><span data-stu-id="3bc98-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="3bc98-105">Mas a configuração é um pouco complicada e algumas vezes pode ser difícil identificar a origem dos problemas.</span><span class="sxs-lookup"><span data-stu-id="3bc98-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="3bc98-106">Temos recursos para ajudá-lo a identificar os possíveis problemas e corrigi-los.</span><span class="sxs-lookup"><span data-stu-id="3bc98-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="3bc98-107">Como saber se algo está errado?</span><span class="sxs-lookup"><span data-stu-id="3bc98-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="3bc98-108">A primeira indicação de que algo está errado é quando o bloco de status DirSync no centro de administração do Microsoft 365 indica que há um problema.</span><span class="sxs-lookup"><span data-stu-id="3bc98-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="3bc98-109">Você também receberá um email (no email alternativo e no seu email de administrador) do Office 365 que indica que seu locatário encontrou erros de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="3bc98-109">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="3bc98-110">Confira os detalhes em [Identificar erros de sincronização de diretório no Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="3bc98-110">For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="3bc98-111">Como usar a ferramenta Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="3bc98-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="3bc98-112">No [centro de administração do Microsoft 365](https://admin.microsoft.com), navegue até usuários **ativos**do **usuário** \> .</span><span class="sxs-lookup"><span data-stu-id="3bc98-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="3bc98-113">Clique no menu **mais** (três pontos) e selecione **sincronização de diretório**.</span><span class="sxs-lookup"><span data-stu-id="3bc98-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="3bc98-114">Siga as [instruções no assistente](set-up-directory-synchronization.md) para baixar o Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="3bc98-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="3bc98-115">Se você ainda estiver usando a Sincronização do Azure Active Directory (DirSync), confira o tópico [Como solucionar problemas de instalação da Ferramenta de Sincronização do Azure Active Directory e mensagens de erro do Assistente de Configuração no Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para saber mais sobre os requisitos do sistema para instalar o DirSync, as permissões necessárias e como solucionar erros comuns.</span><span class="sxs-lookup"><span data-stu-id="3bc98-115">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="3bc98-116">Para atualizar da Sincronização do Azure Active Directory para o Azure AD Connect, confira as [instruções de atualização](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="3bc98-116">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="3bc98-117">Resolvendo causas comuns de problemas com a sincronização de diretórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="3bc98-117">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="3bc98-118">**Os objetos sincronizados não são exibidos ou atualizados online, ou estou recebendo relatórios de erros de sincronização do serviço.**</span><span class="sxs-lookup"><span data-stu-id="3bc98-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="3bc98-119">Sincronização de identidades e resiliência do atributo duplicada</span><span class="sxs-lookup"><span data-stu-id="3bc98-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="3bc98-120">**Tenho um alerta no centro de administração ou estou recebendo emails automáticos informando que não houve eventos de sincronização recentes**</span><span class="sxs-lookup"><span data-stu-id="3bc98-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="3bc98-121">Solucionar problemas de conectividade com o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3bc98-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="3bc98-122">Contas e permissões do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3bc98-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="3bc98-123">Sincronização do Azure AD Connect: como gerenciar a conta de serviço do Azure AD</span><span class="sxs-lookup"><span data-stu-id="3bc98-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="3bc98-124">A sincronização do diretório com o Azure Active Directory para ou você é alertado de que a sincronização não aconteceu há mais de um dia</span><span class="sxs-lookup"><span data-stu-id="3bc98-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="3bc98-125">**As senhas não estão sincronizando ou estou vendo um alerta no centro de administração de que não houve sincronização de hash de senhas recentes**</span><span class="sxs-lookup"><span data-stu-id="3bc98-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="3bc98-126">Implementação de sincronização de hash de senha com a sincronização do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3bc98-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="3bc98-127">**Estou vendo um alerta de cota de objeto excedida**</span><span class="sxs-lookup"><span data-stu-id="3bc98-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="3bc98-128">Temos uma cota interna de objetos para ajudar a proteger o serviço.</span><span class="sxs-lookup"><span data-stu-id="3bc98-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="3bc98-129">Se você tiver objetos demais em seu diretório e precisar sincronizar com o Office 365, terá que [Entrar em contato com o suporte de produtos empresariais](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar sua cota.</span><span class="sxs-lookup"><span data-stu-id="3bc98-129">If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="3bc98-130">**Preciso saber quais são os atributos sincronizados**</span><span class="sxs-lookup"><span data-stu-id="3bc98-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="3bc98-131">É possível encontrar uma lista de todos os atributos que estão sincronizados entre o local e a nuvem [aqui](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="3bc98-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="3bc98-132">**Não consigo gerenciar ou remover os objetos que foram sincronizados na nuvem**</span><span class="sxs-lookup"><span data-stu-id="3bc98-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="3bc98-133">Você está pronto para gerenciar objetos somente na nuvem?</span><span class="sxs-lookup"><span data-stu-id="3bc98-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="3bc98-134">Ou existe um objeto que foi excluído localmente, mas está preso na nuvem?</span><span class="sxs-lookup"><span data-stu-id="3bc98-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="3bc98-135">Confira [Como solucionar erros durante a sincronização](https://go.microsoft.com/fwlink/p/?linkid=842044) e este [artigo sobre suporte](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obter orientação sobre como resolver esses problemas.</span><span class="sxs-lookup"><span data-stu-id="3bc98-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="3bc98-136">**Recebi uma mensagem de erro informando que minha empresa excedeu o número de objetos que podem ser sincronizados**</span><span class="sxs-lookup"><span data-stu-id="3bc98-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="3bc98-137">Leia mais sobre o problema [aqui](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="3bc98-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="3bc98-138">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="3bc98-138">Other resources</span></span>

- [<span data-ttu-id="3bc98-139">Script para corrigir UPNs duplicados</span><span class="sxs-lookup"><span data-stu-id="3bc98-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="3bc98-140">Como preparar um domínio não roteável (por exemplo, domínio .local) para a sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="3bc98-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="3bc98-141">Script para contar o total de objetos sincronizados</span><span class="sxs-lookup"><span data-stu-id="3bc98-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="3bc98-142">Solucionar problemas do AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="3bc98-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="3bc98-143">Usar o PowerShell para corrigir os atributos DisplayName vazios para grupos habilitados para email</span><span class="sxs-lookup"><span data-stu-id="3bc98-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="3bc98-144">Usar o PowerShell para corrigir UPN duplicado</span><span class="sxs-lookup"><span data-stu-id="3bc98-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="3bc98-145">Usar o PowerShell para corrigir endereços de email duplicados</span><span class="sxs-lookup"><span data-stu-id="3bc98-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="3bc98-146">Ferramentas de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="3bc98-146">Diagnostic tools</span></span>

<span data-ttu-id="3bc98-147">A [ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) é usada para realizar a descoberta e a reparação de objetos de identidade e seus atributos em um ambiente do Active Directory local que está em preparação para migrar para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="3bc98-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365.</span></span> <span data-ttu-id="3bc98-148">O IDFix destina-se aos administradores do Active Directory responsáveis pela sincronização de diretórios com o serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="3bc98-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Office 365 service.</span></span> 

<span data-ttu-id="3bc98-149">[Baixar a ferramenta IdFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3bc98-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>