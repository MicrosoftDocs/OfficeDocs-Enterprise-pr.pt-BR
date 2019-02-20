---
title: Preparar um domínio não roteável para sincronização de diretório
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
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
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Saiba o que fazer se você tiver um domínio não routale associado aos seus usuários locais antes de sincronizar com o Office 365.
ms.openlocfilehash: 150e670e58419cda0f8ba08a5fb1e375478a27b1
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085310"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="2b71b-103">Preparar um domínio não roteável para sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="2b71b-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="2b71b-p101">Ao sincronizar seu diretório local com o Office 365, você precisa ter um domínio verificado no Azure Active Directory. Somente os nomes principais de usuário (UPN) associados ao domínio local são sincronizados. No enTanto, qualquer UPN que contenha um domínio não roteável, por exemplo. local (como Billa @ contoso. local), será sincronizado com um domínio. onmicrosoft.com (como billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="2b71b-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="2b71b-107">Se você usa atualmente um domínio. local para suas contas de usuário no Active Directory, é recomendável alterá-lo para usar um domínio verificado (como o billa@contoso.com) a fim de sincronizar corretamente com seu domínio do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b71b-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="2b71b-108">E se eu só tiver um domínio. local local?</span><span class="sxs-lookup"><span data-stu-id="2b71b-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="2b71b-p102">A ferramenta mais recente que você pode usar para sincronizar seu Active Directory com o Azure Active Directory é chamada Azure AD Connect. Para obter mais informações, consulte [integrando suas identidades locais com o Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span><span class="sxs-lookup"><span data-stu-id="2b71b-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="2b71b-p103">O Azure AD Connect sincroniza o UPN e a senha dos usuários para que os usuários possam entrar com as mesmas credenciais que usam no local. No enTanto, o Azure AD Connect sincroniza apenas os usuários em domínios verificados pelo Office 365. Isso significa que o domínio também é verificado pelo Azure Active Directory porque as identidades do Office 365 são gerenciadas pelo Azure Active Directory. Em outras palavras, o domínio deve ser um domínio válido da Internet (por exemplo,. com,. org, .net,. us, etc.). Se o Active Directory interno usar apenas um domínio não roteável (por exemplo,. local), isso não poderá corresponder ao domínio verificado que você tem no Office 365. Você pode corrigir esse problema alterando seu domínio primário no Active Directory local ou adicionando um ou mais sufixos UPN.</span><span class="sxs-lookup"><span data-stu-id="2b71b-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="2b71b-117">**Alterar seu domínio primário**</span><span class="sxs-lookup"><span data-stu-id="2b71b-117">**Change your primary domain**</span></span>

<span data-ttu-id="2b71b-p104">Altere o domínio primário para um domínio verificado no Office 365, por exemplo, contoso.com. Todos os usuários que têm o domínio contoso. local é atualizado para o contoso.com. Para obter instruções, consulte [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). Esse é um processo muito envolvido, no entanto, e uma solução mais fácil é [Adicionar sufixos UPN e atualizar seus usuários](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), conforme mostrado na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b71b-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="2b71b-122">**Adicionar sufixos UPN e atualizar seus usuários para eles**</span><span class="sxs-lookup"><span data-stu-id="2b71b-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="2b71b-p105">Você pode resolver o problema. local registrando novos sufixos de UPN ou sufixos no Active Directory para corresponder ao domínio (ou domínios) que você verificou no Office 365. Depois de registrar o novo sufixo, você atualizará os UPNs do usuário para substituir o. local pelo novo nome de domínio, por exemplo, para que uma conta de usuário se pareça com billa@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="2b71b-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="2b71b-125">Depois de atualizar os UPNs para usar o domínio verificado, você está pronto para sincronizar seu Active Directory local com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b71b-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="2b71b-126">**Etapa 1: Adicionar o novo sufixo UPN**</span><span class="sxs-lookup"><span data-stu-id="2b71b-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="2b71b-127">No servidor em que o AD DS (serviços de domínio Active Directory) é executado, no Gerenciador de servidores, escolha **ferramentas** \> **domínios e relações de confiança do Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="2b71b-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="2b71b-128">**Ou, se você não tiver o Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="2b71b-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="2b71b-129">Pressione a **tecla Windows + R** para abrir a caixa de diálogo **executar** e digite domain. msc e, em seguida, escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="2b71b-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Escolha domínios e relações de confiança do Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="2b71b-131">Na janela **domínios e relações de confiança do Active Directory** , clique com o botão direito em **domínios e relações de confiança do Active Directory**e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="2b71b-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![Clique com o botão direito em domínios e relações de confiança do ActiveDirectory e escolha Propriedades](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="2b71b-133">Na guia **sufixos UPN** , na caixa sufixos **UPN alternativos** , digite seu novo sufixo UPN ou sufixos e, em seguida, escolha **Adicionar** \> **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="2b71b-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Adicionar um novo sufixo UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="2b71b-135">Escolha **OK** quando terminar de adicionar os sufixos.</span><span class="sxs-lookup"><span data-stu-id="2b71b-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="2b71b-136">**Etapa 2: alterar o sufixo UPN para usuários existentes**</span><span class="sxs-lookup"><span data-stu-id="2b71b-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="2b71b-137">No servidor em que o AD DS (serviços de domínio Active Directory) é executado, no Gerenciador de servidores, escolha **ferramentas** \> **usuários e computadores do Active Directory**do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2b71b-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="2b71b-138">**Ou, se você não tiver o Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="2b71b-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="2b71b-139">Pressione a **tecla Windows + R** para abrir a caixa de diálogo **executar** e digite dsa. msc e clique em **OK**</span><span class="sxs-lookup"><span data-stu-id="2b71b-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="2b71b-140">Selecione um usuário, clique com o botão direito do mouse e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="2b71b-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="2b71b-141">Na guia **conta** , na lista suspensa sufixo de UPN, escolha o novo sufixo UPN e, em seguida, escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="2b71b-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Adicionar novo sufixo UPN para um usuário](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="2b71b-143">Conclua estas etapas para cada usuário.</span><span class="sxs-lookup"><span data-stu-id="2b71b-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="2b71b-144">Como alternativa, você pode atualizar os sufixos de UPN em massa [também pode usar o Windows PowerShell para alterar o sufixo UPN para todos os usuários](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span><span class="sxs-lookup"><span data-stu-id="2b71b-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="2b71b-145">**Você também pode usar o Windows PowerShell para alterar o sufixo UPN de todos os usuários**</span><span class="sxs-lookup"><span data-stu-id="2b71b-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="2b71b-p106">Se você tiver muitos usuários para atualizar, é mais fácil usar o Windows PowerShell. O exemplo a seguir usa os cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) e [set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) para alterar todos os sufixos contoso. local para contoso.com.</span><span class="sxs-lookup"><span data-stu-id="2b71b-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="2b71b-148">Execute os seguintes comandos do Windows PowerShell para atualizar todos os sufixos contoso. local para contoso.com:</span><span class="sxs-lookup"><span data-stu-id="2b71b-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="2b71b-149">Consulte [Active Directory Windows PowerShell Module](https://go.microsoft.com/fwlink/p/?LinkId=624314) para saber mais sobre como usar o Windows PowerShell no Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2b71b-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

