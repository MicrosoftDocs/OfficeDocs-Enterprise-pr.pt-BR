---
title: Prepare-se para provisionar usuários por meio da sincronização de diretório para o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Descreve como preparar para provisionar usuários para o Office 365 usando a sincronização de diretórios e os benefícios de longo prazo do uso deste método.
ms.openlocfilehash: 78636fd3ec7aaaac8fa06ba8a0f2c37d76d1b045
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539402"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="13da9-103">Prepare-se para provisionar usuários por meio da sincronização de diretório para o Office 365</span><span class="sxs-lookup"><span data-stu-id="13da9-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="13da9-p101">Provisionamento de usuários com a sincronização de diretório exige mais planejamento e preparação que simplesmente gerenciar sua conta do trabalho ou da escola diretamente no Office 365. As tarefas de planejamento e preparação adicionais são necessárias para garantir que o seu local Active Directory sincroniza adequadamente no Windows Azure Active Directory. Os benefícios adicionais à sua organização incluem:</span><span class="sxs-lookup"><span data-stu-id="13da9-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="13da9-107">Reduzir os programas administrativos em sua organização</span><span class="sxs-lookup"><span data-stu-id="13da9-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="13da9-108">Opcionalmente, habilitando o cenário de logon único</span><span class="sxs-lookup"><span data-stu-id="13da9-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="13da9-109">Automatizar as alterações de conta no Office 365</span><span class="sxs-lookup"><span data-stu-id="13da9-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="13da9-110">Para obter mais informações sobre as vantagens do uso de sincronização de diretórios, consulte o [roteiro de sincronização de diretório]( https://go.microsoft.com/fwlink/p/?LinkId=525398) e [Noções básicas sobre Office 365 Identity e o Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="13da9-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="13da9-111">Para determinar qual cenário é a melhor para a sua organização, examine a [comparação de ferramentas de integração de diretório](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span><span class="sxs-lookup"><span data-stu-id="13da9-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="13da9-112">Tarefas de limpeza do diretório</span><span class="sxs-lookup"><span data-stu-id="13da9-112">Directory cleanup tasks</span></span>

<span data-ttu-id="13da9-113">Antes de começar a sincronizar seu diretório, você precisa limpar seu diretório.</span><span class="sxs-lookup"><span data-stu-id="13da9-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="13da9-114">Analise também o [atributos são sincronizados com o Windows Azure Active Directory por Connect do Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=746480).</span><span class="sxs-lookup"><span data-stu-id="13da9-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=746480).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="13da9-p102">Se você não executar a limpeza do diretório antes de sincronizar, pode haver um efeito de negativo significativo sobre o processo de implantação. Ele pode levar dias ou até mesmo semanas, para passar o ciclo de sincronização de diretórios, identificando erros e ressincronização.</span><span class="sxs-lookup"><span data-stu-id="13da9-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="13da9-117">No seu diretório local, conclua as seguintes tarefas de limpeza:</span><span class="sxs-lookup"><span data-stu-id="13da9-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="13da9-118">Verifique se cada usuário ao qual serão atribuídas ofertas de serviços do Office 365 tem um endereço de email válido e exclusivo no atributo **proxyAddresses**.</span><span class="sxs-lookup"><span data-stu-id="13da9-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="13da9-119">Remover valores duplicados no atributo **proxyAddresses**.</span><span class="sxs-lookup"><span data-stu-id="13da9-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="13da9-p103">Se possível, certifique-se de que cada usuário ao qual será atribuído ofertas de serviço do Office 365 tem um valor válido e exclusivo para o atributo **userPrincipalName** no objeto de **usuário** do usuário. Para melhor experiência de sincronização, certifique-se de UPN Active Directory local corresponde a nuvem UPN. Se um usuário não tiver um valor para o atributo **userPrincipalName** , o objeto de **usuário** deve conter um valor válido e exclusivo para o atributo **sAMAccountName** . Remova valores duplicados no atributo **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="13da9-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="13da9-124">Para garantir o melhor uso da lista de endereços global (GAL), verifique se as informações nos seguintes atributos estão corretas:</span><span class="sxs-lookup"><span data-stu-id="13da9-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="13da9-125">givenName </span><span class="sxs-lookup"><span data-stu-id="13da9-125">givenName</span></span>
  - <span data-ttu-id="13da9-126">surname</span><span class="sxs-lookup"><span data-stu-id="13da9-126">surname</span></span>
  - <span data-ttu-id="13da9-127">displayName</span><span class="sxs-lookup"><span data-stu-id="13da9-127">displayName</span></span>
  - <span data-ttu-id="13da9-128">Cargo</span><span class="sxs-lookup"><span data-stu-id="13da9-128">Job Title</span></span>
  - <span data-ttu-id="13da9-129">Departamento</span><span class="sxs-lookup"><span data-stu-id="13da9-129">Department</span></span>
  - <span data-ttu-id="13da9-130">Escritório</span><span class="sxs-lookup"><span data-stu-id="13da9-130">Office</span></span>
  - <span data-ttu-id="13da9-131">Telefone Comercial</span><span class="sxs-lookup"><span data-stu-id="13da9-131">Office Phone</span></span>
  - <span data-ttu-id="13da9-132">Celular</span><span class="sxs-lookup"><span data-stu-id="13da9-132">Mobile Phone</span></span>
  - <span data-ttu-id="13da9-133">Número de Fax</span><span class="sxs-lookup"><span data-stu-id="13da9-133">Fax Number</span></span>
  - <span data-ttu-id="13da9-134">Endereço</span><span class="sxs-lookup"><span data-stu-id="13da9-134">Street Address</span></span>
  - <span data-ttu-id="13da9-135">Cidade</span><span class="sxs-lookup"><span data-stu-id="13da9-135">City</span></span>
  - <span data-ttu-id="13da9-136">Estado ou Província</span><span class="sxs-lookup"><span data-stu-id="13da9-136">State or Province</span></span>
  - <span data-ttu-id="13da9-137">CEP ou Código Postal</span><span class="sxs-lookup"><span data-stu-id="13da9-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="13da9-138">País ou Região</span><span class="sxs-lookup"><span data-stu-id="13da9-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="13da9-139">Preparação de objetos e atributos de diretório</span><span class="sxs-lookup"><span data-stu-id="13da9-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="13da9-p104">Sincronização de diretórios bem-sucedida entre seu diretório local e o Office 365 exige que seu atributos de diretório local estejam adequadamente preparados. Por exemplo, você precisará garantir que os caracteres específicos não são usados em determinados atributos que são sincronizados com o ambiente do Office 365. Caracteres inesperados não farão com que a sincronização de diretório falhar, mas podem retornar um aviso. Caracteres inválidos fará com que a sincronização de diretório falhar.</span><span class="sxs-lookup"><span data-stu-id="13da9-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="13da9-p105">Sincronização de diretórios também falhará se alguns dos usuários do Active Directory possuem um ou mais atributos duplicados. Cada usuário deve ter atributos exclusivos.</span><span class="sxs-lookup"><span data-stu-id="13da9-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="13da9-146">Os atributos que você precisa para preparar são listados aqui:</span><span class="sxs-lookup"><span data-stu-id="13da9-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="13da9-147">**Observação:** Você também pode usar a [ferramenta IdFix](install-and-run-idfix.md) para tornar esse processo muito mais fácil.</span><span class="sxs-lookup"><span data-stu-id="13da9-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="13da9-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="13da9-148">**displayName**</span></span>
    
  - <span data-ttu-id="13da9-149">Se o atributo existe no objeto do usuário, ele será sincronizado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="13da9-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="13da9-p106">Se esse atributo existir no objeto de usuário, deve haver um valor para ela. Ou seja, o atributo não deve estar em branco.</span><span class="sxs-lookup"><span data-stu-id="13da9-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="13da9-152">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="13da9-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="13da9-153">**givenName **</span><span class="sxs-lookup"><span data-stu-id="13da9-153">**givenName**</span></span>
    
  - <span data-ttu-id="13da9-154">Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não necessitará dele ou irá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="13da9-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="13da9-155">Número máximo de caracteres: 64</span><span class="sxs-lookup"><span data-stu-id="13da9-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="13da9-156">**email**</span><span class="sxs-lookup"><span data-stu-id="13da9-156">**mail**</span></span>
    
  - <span data-ttu-id="13da9-157">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="13da9-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="13da9-p107">Se houver valores duplicados, o primeiro usuário com o valor é sincronizado. Usuários subsequentes não aparecerá no Office 365. Você deve modificar o valor no Office 365 ou modificar ambos dos valores no diretório local na ordem de ambos os usuários apareça no Office 365.</span><span class="sxs-lookup"><span data-stu-id="13da9-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="13da9-161">**mailNickname** (alias do Exchange)</span><span class="sxs-lookup"><span data-stu-id="13da9-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="13da9-162">O valor do atributo não pode começar com um ponto (.).</span><span class="sxs-lookup"><span data-stu-id="13da9-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="13da9-163">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="13da9-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="13da9-164">**proxyAddresses **</span><span class="sxs-lookup"><span data-stu-id="13da9-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="13da9-165">Atributo de valores múltiplos</span><span class="sxs-lookup"><span data-stu-id="13da9-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="13da9-166">A quantidade máxima de caracteres por valor: 256</span><span class="sxs-lookup"><span data-stu-id="13da9-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="13da9-167">O valor do atributo não deve conter um espaço.</span><span class="sxs-lookup"><span data-stu-id="13da9-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="13da9-168">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="13da9-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="13da9-169">Caracteres inválidos: \< \> (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="13da9-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="13da9-170">Observe que os caracteres inválidos se aplicam aos caracteres seguindo o delimitador do tipo e ":", de forma que SMTP:User@contso.com é permitida, mas SMTP:user:M@contoso.com não está.</span><span class="sxs-lookup"><span data-stu-id="13da9-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="13da9-p108">Todos os endereços de protocolo de transporte de email simples (SMTP) devem ser compatíveis com os padrões de mensagens de email. Se os endereços duplicados ou indesejados existirem, consulte o tópico de Ajuda, [Remover proxy duplicado e indesejado endereços no Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="13da9-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="13da9-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="13da9-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="13da9-174">Número máximo de caracteres: 20</span><span class="sxs-lookup"><span data-stu-id="13da9-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="13da9-175">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="13da9-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="13da9-p109">Caracteres inválidos: [\ "|, /: \< \> + =;? \* ]</span><span class="sxs-lookup"><span data-stu-id="13da9-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="13da9-178">Se um usuário tiver um atributo **sAMAccountName** inválido, mas tiver um atributo **userPrincipalName** válido, a conta de usuário será criada no Office 365.</span><span class="sxs-lookup"><span data-stu-id="13da9-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="13da9-179">Se **sAMAccountName** e **userPrincipalName** forem inválidos, o atributo de **userPrincipalName** local do Active Directory deve ser atualizado.</span><span class="sxs-lookup"><span data-stu-id="13da9-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="13da9-180">**sn** (sobrenome)</span><span class="sxs-lookup"><span data-stu-id="13da9-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="13da9-181">Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não necessitará dele ou irá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="13da9-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="13da9-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="13da9-182">**targetAddress**</span></span>
    
    <span data-ttu-id="13da9-p110">É obrigatório se o atributo **targetAddress** (por exemplo, SMTP:tom@contoso.com) que é preenchido para o usuário deverá aparecer no Office 365 GAL. Cenários de migração de mensagens de terceiros, isso exigiria a extensão de esquema do Office 365 para o diretório local. A extensão de esquema do Office 365 também seria adicionar outros atributos úteis para gerenciar o Office 365 objetos que são preenchidos usando uma ferramenta de sincronização de diretórios do diretório local. Por exemplo, o atributo **msExchHideFromAddressLists** para gerenciar caixas de correio ocultas ou grupos de distribuição seria adicionado.</span><span class="sxs-lookup"><span data-stu-id="13da9-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="13da9-187">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="13da9-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="13da9-188">O valor do atributo não deve conter um espaço.</span><span class="sxs-lookup"><span data-stu-id="13da9-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="13da9-189">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="13da9-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="13da9-190">Caracteres inválidos: \ \< \> (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="13da9-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="13da9-191">Todos os endereços no Protocolo SMTP devem estar em conformidade com os padrões de emails.</span><span class="sxs-lookup"><span data-stu-id="13da9-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="13da9-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="13da9-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="13da9-p111">O atributo **userPrincipalName** deve estar no estilo Internet entrar formato onde o nome de usuário é seguido do sinal de arroba (@) e um nome de domínio: por exemplo, user@contoso.com. Todos os endereços de protocolo de transporte de email simples (SMTP) devem ser compatíveis com os padrões de mensagens de email.</span><span class="sxs-lookup"><span data-stu-id="13da9-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="13da9-p112">A quantidade máxima de caracteres para o atributo **userPrincipalName** é 113. Permite-se uma quantidade específica de caracteres antes e depois do sinal (@), como a seguir:</span><span class="sxs-lookup"><span data-stu-id="13da9-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="13da9-197">Número máximo de caracteres para o nome de usuário antes do sinal de arroba (@): 64</span><span class="sxs-lookup"><span data-stu-id="13da9-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="13da9-198">Número máximo de caracteres para o nome de domínio após o sinal de arroba (@): 48</span><span class="sxs-lookup"><span data-stu-id="13da9-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="13da9-p113">Caracteres inválidos: \ % &amp; \* + / =? { } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="13da9-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="13da9-201">Tem trema também é um caractere inválido.</span><span class="sxs-lookup"><span data-stu-id="13da9-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="13da9-202">O caractere @ é necessário em cada valor **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="13da9-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="13da9-203">O caractere @ não pode ser o primeiro caractere em cada valor **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="13da9-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="13da9-204">O nome de usuário não pode terminar com um ponto (.), um e comercial (&amp;), um espaço ou um sinal de arroba (@).</span><span class="sxs-lookup"><span data-stu-id="13da9-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="13da9-205">O nome de usuário não pode conter espaços.</span><span class="sxs-lookup"><span data-stu-id="13da9-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="13da9-206">Domínios roteáveis devem ser usados; Por exemplo, domínios locais ou internos não podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="13da9-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="13da9-207">Unicode é convertido para caracteres sublinhados.</span><span class="sxs-lookup"><span data-stu-id="13da9-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="13da9-208">**userPrincipalName** não pode conter valores duplicados no diretório.</span><span class="sxs-lookup"><span data-stu-id="13da9-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="13da9-209">Preparar o atributo userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="13da9-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="13da9-p114">Active Directory é projetado para permitir que os usuários finais na sua organização para entrar no seu diretório usando o **sAMAccountName** ou **userPrincipalName**. Da mesma forma, os usuários finais podem entrar no Office 365 usando o nome principal do usuário (UPN) dos seus trabalhos ou escola conta. Sincronização de diretórios tenta criar novos usuários no Windows Azure Active Directory usando o UPN mesmo que esteja no seu diretório local. O UPN é formatado como um endereço de email.</span><span class="sxs-lookup"><span data-stu-id="13da9-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="13da9-p115">No Office 365, o UPN é o atributo padrão que é usado para gerar o endereço de email. É fácil obter **userPrincipalName** (no local e no Windows Azure Active Directory) e o endereço de email primário no **proxyAddresses** definidos como valores diferentes. Quando eles estiverem definidos como valores diferentes, pode haver confusão para os administradores e usuários finais.</span><span class="sxs-lookup"><span data-stu-id="13da9-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="13da9-p116">É melhor alinhar esses atributos para reduzir a confusão. Para atender a requisitos de single sign-on com os serviços de Federação do Active Directory (AD FS) 2.0, você precisará garantir que o UPNs no Windows Azure Active Directory e seu local Active Directory correspondem e estiver usando um namespace de domínio válidos.</span><span class="sxs-lookup"><span data-stu-id="13da9-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="13da9-219">Adicionar um sufixo UPN alternativo ao AD DS</span><span class="sxs-lookup"><span data-stu-id="13da9-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="13da9-p117">Você pode precisar adicionar um sufixo UPN alternativo para associar as credenciais do usuário corporativo ao ambiente do Office 365. Um sufixo UPN é a parte de um UPN à direita do caractere @. UPNs que são usados para o serviço single sign-on podem conter letras, números, períodos, traços e sublinhados, mas não há outros tipos de caracteres.</span><span class="sxs-lookup"><span data-stu-id="13da9-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="13da9-223">Para obter mais informações sobre como adicionar um sufixo UPN alternativo ao Active Directory, consulte [Prepare para sincronização de diretórios]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="13da9-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="13da9-224">Corresponder o UPN local com o Office 365 UPN</span><span class="sxs-lookup"><span data-stu-id="13da9-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="13da9-p118">Se você já tiver configurado a sincronização de diretórios, UPN do usuário para o Office 365 pode não corresponder o UPN do local do usuário que está definido no seu serviço de diretório local. Isso pode ocorrer quando um usuário foi atribuído uma licença antes do domínio foi verificado. Para corrigir esse problema, use o [PowerShell para corrigir o UPN duplicado](https://go.microsoft.com/fwlink/p/?LinkId=396730) para atualizar o UPN do usuário para garantir que o UPN do Office 365 coincide com o nome de usuário corporativo e o domínio. Se você estiver atualizando o UPN no serviço de diretório local e gostaria que ele para sincronizar com a identidade do Windows Azure Active Directory, você precisa remover a licença do usuário no Office 365 antes de fazer o alterações no local.</span><span class="sxs-lookup"><span data-stu-id="13da9-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="13da9-229">Consulte também [como preparar um domínio não roteáveis (por exemplo, o domínio. local) para sincronização de diretórios](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="13da9-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="13da9-230">Ferramentas de integração de diretório</span><span class="sxs-lookup"><span data-stu-id="13da9-230">Directory integration tools</span></span>

<span data-ttu-id="13da9-p119">Sincronização de diretórios é a sincronização de objetos de diretório (usuários, grupos e contatos) do seu ambiente do Active Directory local a infraestrutura de diretório do Office 365, o Azure Active Directory. Consulte [As ferramentas de integração de diretório](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obter uma lista das ferramentas disponíveis e suas funcionalidades. A ferramenta recomendada é o [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Para obter mais informações sobre como conectar do Azure Active Directory, consulte [integrando suas identidades no local com o Windows Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span><span class="sxs-lookup"><span data-stu-id="13da9-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="13da9-p120">Quando as contas de usuário são sincronizadas com o diretório do Office 365 pela primeira vez, eles são marcados como não ativado. Não podem enviar ou receber emails, e não consomem licenças de assinatura. Quando você estiver pronto para atribuir assinaturas do Office 365 para usuários específicos, você deve selecionar e ativá-los por [Atribuir licenças aos usuários no Office 365 para empresas](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span><span class="sxs-lookup"><span data-stu-id="13da9-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="13da9-p121">Você também pode usar o [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) para atribuir licenças. Consulte [como usar o PowerShell para atribuir licenças automaticamente para os usuários do seu Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) para uma solução automatizada.</span><span class="sxs-lookup"><span data-stu-id="13da9-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>