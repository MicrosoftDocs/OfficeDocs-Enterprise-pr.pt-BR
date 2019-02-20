---
title: Corrigir problemas de sincronização de diretório do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
description: Descreve causas comuns de problemas com a sincronização de diretórios no Office 365 e fornece alguns métodos para ajudar a solucioná-los e solucioná-los.
ms.openlocfilehash: e83ca495ca96ac41fb2f79775c3d5970a6b538fb
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085390"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="33b90-103">Corrigir problemas de sincronização de diretório do Office 365</span><span class="sxs-lookup"><span data-stu-id="33b90-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="33b90-p101">Com a sincronização de diretórios, você pode continuar a gerenciar usuários e grupos locais e sincronizar adições, exclusões e alterações na nuvem. Mas a configuração é um pouco complicada e, às vezes, pode ser difícil identificar a origem dos problemas. Temos recursos para ajudá-lo a identificar possíveis problemas e corrigi-los.</span><span class="sxs-lookup"><span data-stu-id="33b90-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="33b90-107">Como saber se algo está errado?</span><span class="sxs-lookup"><span data-stu-id="33b90-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="33b90-108">A primeira indicação de que algo está errado é quando o bloco de status dirSync no centro de administração do Office 365 indica que há um problema:</span><span class="sxs-lookup"><span data-stu-id="33b90-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![O bloco de status dirSync na visualização do centro de administração](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="33b90-p102">Você também receberá um email (para o email alternativo e para o email do administrador) do Office 365 que indica que seu locatário encontrou erros de sincronização de diretório. Para obter detalhes, consulte [identificar erros de sincronização de diretório no Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="33b90-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="33b90-112">Como obter a ferramenta Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="33b90-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="33b90-p103">no centro de administração do Office 365, navegue até \* \* usuários \* \> \* **usuários ativos**. Clique no menu **mais** e selecione **sincronização de diretório**.</span><span class="sxs-lookup"><span data-stu-id="33b90-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![No menu mais, escolha sincronização de diretório](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="33b90-116">no antigo centro de administração do Office 365, navegue até **usuários ativos**do **usuário** \> e selecione **configurar** ao lado de **sincronização do Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="33b90-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Escolha Configurar ao lado da sincronização do Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="33b90-118">Siga as [instruções no assistente](set-up-directory-synchronization.md) para baixar o Azure ad Connect.</span><span class="sxs-lookup"><span data-stu-id="33b90-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="33b90-119">Se você ainda estiver usando a sincronização do Azure Active Directory (dirSync), confira [como solucionar problemas de mensagens de erro do assistente de instalação e configuração da ferramenta de sincronização do Azure Active Directory no Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para obter informações sobre os requisitos do sistema para instalar DirSync, as permissões necessárias e como solucionar erros comuns.</span><span class="sxs-lookup"><span data-stu-id="33b90-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="33b90-120">Para atualizar da sincronização do Azure Active Directory para o Azure AD Connect, consulte [as instruções de atualização](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="33b90-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="33b90-121">Resolver causas comuns de problemas com a sincronização de diretórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="33b90-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="33b90-122">**Objetos sincronizados não aparecem ou estão sendo atualizados online, ou estou obtendo relatórios de erro de sincronização do serviço.**</span><span class="sxs-lookup"><span data-stu-id="33b90-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="33b90-123">Sincronização de identidade e resiliência de atributo duplicada</span><span class="sxs-lookup"><span data-stu-id="33b90-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="33b90-124">**Tenho um alerta no centro de administração do Office 365 ou estou recebendo emails automatizados que não foram mais recentes eventos de sincronização**</span><span class="sxs-lookup"><span data-stu-id="33b90-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="33b90-125">Solucionar problemas de conectividade com o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="33b90-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="33b90-126">Contas e permissões do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="33b90-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="33b90-127">Sincronização do Azure AD Connect: como gerenciar a conta de serviço do Azure AD</span><span class="sxs-lookup"><span data-stu-id="33b90-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="33b90-128">A sincronização de diretórios com o Azure Active Directory é interrompida ou você é avisado de que a sincronização não foi registrada em mais de um dia</span><span class="sxs-lookup"><span data-stu-id="33b90-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="33b90-129">**Os hashes de senha não estão sendo sincronizados ou estou vendo um alerta no centro de administração do Office 365 que não havia uma sincronização de hash de senha recente**</span><span class="sxs-lookup"><span data-stu-id="33b90-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="33b90-130">Implementar a sincronização de hash de senha com a sincronização do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="33b90-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="33b90-131">**Estou vendo um alerta que a cota de objeto excedeu**</span><span class="sxs-lookup"><span data-stu-id="33b90-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="33b90-p104">Temos uma cota de objeto interna para ajudar a proteger o serviço. Se você tiver muitos objetos em seu diretório que precisam ser sincronizados com o Office 365, será necessário [entrar em contato com o suporte para produtos de negócios](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar sua cota.</span><span class="sxs-lookup"><span data-stu-id="33b90-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="33b90-134">**Preciso saber quais atributos são sincronizados**</span><span class="sxs-lookup"><span data-stu-id="33b90-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="33b90-135">Você pode encontrar uma lista de todos os atributos sincronizados entre o local e a nuvem [imediatamente](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="33b90-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="33b90-136">**Não consigo gerenciar ou remover objetos que foram sincronizados com a nuvem**</span><span class="sxs-lookup"><span data-stu-id="33b90-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="33b90-p105">Você está pronto para gerenciar objetos somente na nuvem? Ou há um objeto que foi excluído no local, mas está preso na nuvem? Confira os erros de [solução de problemas durante a sincronização](https://go.microsoft.com/fwlink/p/?linkid=842044) e o [artigo de suporte](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obter orientação sobre como resolver esses problemas.</span><span class="sxs-lookup"><span data-stu-id="33b90-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="33b90-140">**Recebi uma mensagem de erro de que minha empresa excedeu a quantidade de objetos que podem ser sincronizada**</span><span class="sxs-lookup"><span data-stu-id="33b90-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="33b90-141">Você pode ler mais sobre esse problema [aqui](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="33b90-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="33b90-142">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="33b90-142">Other resources</span></span>

- [<span data-ttu-id="33b90-143">Script para corrigir UPNs duplicados</span><span class="sxs-lookup"><span data-stu-id="33b90-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="33b90-144">Como preparar um domínio não roteável (como o domínio. local) para a sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="33b90-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="33b90-145">Total de objetos sincronizados com o script para contagem</span><span class="sxs-lookup"><span data-stu-id="33b90-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="33b90-146">Solução de problemas do AD FS 2,0</span><span class="sxs-lookup"><span data-stu-id="33b90-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="33b90-147">Usar o PowerShell para corrigir atributos DisplayName vazios para grupos habilitados para email</span><span class="sxs-lookup"><span data-stu-id="33b90-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="33b90-148">Usar o PowerShell para corrigir o UPN duplicado</span><span class="sxs-lookup"><span data-stu-id="33b90-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="33b90-149">Usar o PowerShell para corrigir endereços de email duplicados</span><span class="sxs-lookup"><span data-stu-id="33b90-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="33b90-150">Ferramentas de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="33b90-150">Diagnostic tools</span></span>

<span data-ttu-id="33b90-p106">[IDFix ferramenta](prepare-directory-attributes-for-synch-with-idfix.md) é usada para executar a descoberta e a correção de objetos Identity e seus atributos em um ambiente do Active Directory local em preparação para a migração para o Office 365. O IDFix destina-se aos administradores do Active Directory responsáveis pelo dirSync com o serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="33b90-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="33b90-153">[Baixe a ferramenta IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) do centro de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="33b90-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>