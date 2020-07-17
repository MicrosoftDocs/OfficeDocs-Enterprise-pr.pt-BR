---
title: Correção de problemas com a sincronização de diretórios para o Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
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
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Descreve causas comuns de problemas com a sincronização de diretórios no Office 365 e fornece alguns métodos para ajudar a solucionar problemas.
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998029"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="bf394-103">Correção de problemas com a sincronização de diretórios para o Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bf394-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="bf394-104">Com a sincronização de diretórios, você pode continuar a gerenciar os usuários e grupos locais, e sincronizar acréscimos, eliminações e alterações com a nuvem.</span><span class="sxs-lookup"><span data-stu-id="bf394-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="bf394-105">Mas a configuração é um pouco complicada e algumas vezes pode ser difícil identificar a origem dos problemas.</span><span class="sxs-lookup"><span data-stu-id="bf394-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="bf394-106">Temos recursos para ajudá-lo a identificar os possíveis problemas e corrigi-los.</span><span class="sxs-lookup"><span data-stu-id="bf394-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="bf394-107">Como saber se algo está errado?</span><span class="sxs-lookup"><span data-stu-id="bf394-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="bf394-108">A primeira indicação de que algo está errado é quando o bloco de status DirSync no centro de administração do Microsoft 365 indica que há um problema.</span><span class="sxs-lookup"><span data-stu-id="bf394-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="bf394-109">Você também receberá um email (para o email alternativo e para o email do administrador) da Microsoft 365 que indica que seu locatário encontrou erros de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="bf394-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="bf394-110">Para obter detalhes, consulte [identificar erros de sincronização de diretório no Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="bf394-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="bf394-111">Como usar a ferramenta Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="bf394-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="bf394-112">No [centro de administração do Microsoft 365](https://admin.microsoft.com), navegue até usuários ativos do **usuário** \> **Active users**.</span><span class="sxs-lookup"><span data-stu-id="bf394-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="bf394-113">Clique no menu **mais** (três pontos) e selecione **sincronização de diretório**.</span><span class="sxs-lookup"><span data-stu-id="bf394-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="bf394-114">Siga as [instruções no assistente](set-up-directory-synchronization.md) para baixar o Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="bf394-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="bf394-115">Se você ainda estiver usando a sincronização do Azure Active Directory (Azure AD), confira [como solucionar problemas de mensagens de erro do assistente de instalação e configuração da ferramenta de sincronização do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396717) (DirSync) no Microsoft 365 para obter informações sobre os requisitos do sistema para instalar o DirSync, as permissões necessárias e como solucionar erros comuns.</span><span class="sxs-lookup"><span data-stu-id="bf394-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="bf394-116">Para atualizar do Azure AD Sync para o Azure AD Connect, consulte [as instruções de atualização](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="bf394-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="bf394-117">Resolver causas comuns de problemas com a sincronização de diretórios no Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bf394-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="bf394-118">**Os objetos sincronizados não são exibidos ou atualizados online, ou estou recebendo relatórios de erros de sincronização do serviço.**</span><span class="sxs-lookup"><span data-stu-id="bf394-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="bf394-119">Sincronização de identidades e resiliência do atributo duplicada</span><span class="sxs-lookup"><span data-stu-id="bf394-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="bf394-120">**Tenho um alerta no centro de administração ou estou recebendo emails automáticos informando que não houve eventos de sincronização recentes**</span><span class="sxs-lookup"><span data-stu-id="bf394-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="bf394-121">Solucionar problemas de conectividade com o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="bf394-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="bf394-122">Contas e permissões do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="bf394-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="bf394-123">Sincronização do Azure AD Connect: como gerenciar a conta de serviço do Azure AD</span><span class="sxs-lookup"><span data-stu-id="bf394-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="bf394-124">A sincronização do diretório com o Azure Active Directory para ou você é alertado de que a sincronização não aconteceu há mais de um dia</span><span class="sxs-lookup"><span data-stu-id="bf394-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="bf394-125">**As senhas não estão sincronizando ou estou vendo um alerta no centro de administração de que não houve sincronização de hash de senhas recentes**</span><span class="sxs-lookup"><span data-stu-id="bf394-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="bf394-126">Implementação de sincronização de hash de senha com a sincronização do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="bf394-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="bf394-127">**Estou vendo um alerta de cota de objeto excedida**</span><span class="sxs-lookup"><span data-stu-id="bf394-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="bf394-128">Temos uma cota interna de objetos para ajudar a proteger o serviço.</span><span class="sxs-lookup"><span data-stu-id="bf394-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="bf394-129">Se você tiver muitos objetos em seu diretório que precisam ser sincronizados com o Microsoft 365, será necessário [entrar em contato com o suporte para produtos de negócios](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar sua cota.</span><span class="sxs-lookup"><span data-stu-id="bf394-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="bf394-130">**Preciso saber quais são os atributos sincronizados**</span><span class="sxs-lookup"><span data-stu-id="bf394-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="bf394-131">É possível encontrar uma lista de todos os atributos que estão sincronizados entre o local e a nuvem [aqui](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="bf394-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="bf394-132">**Não consigo gerenciar ou remover os objetos que foram sincronizados na nuvem**</span><span class="sxs-lookup"><span data-stu-id="bf394-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="bf394-133">Você está pronto para gerenciar objetos somente na nuvem?</span><span class="sxs-lookup"><span data-stu-id="bf394-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="bf394-134">Ou existe um objeto que foi excluído localmente, mas está preso na nuvem?</span><span class="sxs-lookup"><span data-stu-id="bf394-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="bf394-135">Confira [Como solucionar erros durante a sincronização](https://go.microsoft.com/fwlink/p/?linkid=842044) e este [artigo sobre suporte](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obter orientação sobre como resolver esses problemas.</span><span class="sxs-lookup"><span data-stu-id="bf394-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="bf394-136">**Recebi uma mensagem de erro informando que minha empresa excedeu o número de objetos que podem ser sincronizados**</span><span class="sxs-lookup"><span data-stu-id="bf394-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="bf394-137">Leia mais sobre o problema [aqui](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="bf394-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="bf394-138">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="bf394-138">Other resources</span></span>

- [<span data-ttu-id="bf394-139">Script para corrigir UPNs duplicados</span><span class="sxs-lookup"><span data-stu-id="bf394-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="bf394-140">Como preparar um domínio não roteável (por exemplo, domínio .local) para a sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="bf394-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="bf394-141">Script para contar o total de objetos sincronizados</span><span class="sxs-lookup"><span data-stu-id="bf394-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="bf394-142">Solucionar problemas do AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="bf394-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="bf394-143">Usar o PowerShell para corrigir os atributos DisplayName vazios para grupos habilitados para email</span><span class="sxs-lookup"><span data-stu-id="bf394-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="bf394-144">Usar o PowerShell para corrigir UPN duplicado</span><span class="sxs-lookup"><span data-stu-id="bf394-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="bf394-145">Usar o PowerShell para corrigir endereços de email duplicados</span><span class="sxs-lookup"><span data-stu-id="bf394-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="bf394-146">Ferramentas de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="bf394-146">Diagnostic tools</span></span>

<span data-ttu-id="bf394-147">[IDFix ferramenta](prepare-directory-attributes-for-synch-with-idfix.md) é usada para executar a descoberta e a correção de objetos Identity e seus atributos em um ambiente do Active Directory local em preparação para a migração para o Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="bf394-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft 365.</span></span> <span data-ttu-id="bf394-148">O IDFix destina-se aos administradores do Active Directory responsáveis pela sincronização de diretórios com o serviço do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="bf394-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Microsoft 365 service.</span></span> 

<span data-ttu-id="bf394-149">[Baixar a ferramenta IdFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bf394-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>