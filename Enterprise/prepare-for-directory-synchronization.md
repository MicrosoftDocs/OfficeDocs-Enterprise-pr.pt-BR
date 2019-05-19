---
title: Preparar a sincronização de diretórios para o Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Descreve como se preparar para provisionar usuários para o Office 365 usando a sincronização de diretórios e os benefícios de longo prazo de usar esse método.
ms.openlocfilehash: 2361f4484f00d61fda90fed407bf3c287bbc2bc1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162464"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a><span data-ttu-id="84e3e-103">Preparar a sincronização de diretórios para o Office 365</span><span class="sxs-lookup"><span data-stu-id="84e3e-103">Prepare for directory synchronization to Office 365</span></span>

<span data-ttu-id="84e3e-104">Os benefícios para a identidade híbrida e a sincronização de diretórios que a organização incluem:</span><span class="sxs-lookup"><span data-stu-id="84e3e-104">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="84e3e-105">Reduzindo os programas administrativos em sua organização</span><span class="sxs-lookup"><span data-stu-id="84e3e-105">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="84e3e-106">Opcionalmente, habilitando o cenário de logon único</span><span class="sxs-lookup"><span data-stu-id="84e3e-106">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="84e3e-107">Automatizar alterações de contas no Office 365</span><span class="sxs-lookup"><span data-stu-id="84e3e-107">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="84e3e-108">Para obter mais informações sobre as vantagens de usar a sincronização de diretório, consulte [mapa de sincronização de diretório]( https://go.microsoft.com/fwlink/p/?LinkId=525398) e [identidade híbrida do Office 365](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="84e3e-108">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Office 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="84e3e-109">No entanto, a sincronização de diretórios requer planejamento e preparação para garantir que os serviços de domínio do Active Directory (AD DS) sincronizem com o locatário do Azure Active Directory (Azure AD) da sua assinatura do Office 365 com um mínimo de erros.</span><span class="sxs-lookup"><span data-stu-id="84e3e-109">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="84e3e-110">Siga estas etapas para obter os melhores resultados.</span><span class="sxs-lookup"><span data-stu-id="84e3e-110">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="84e3e-111">1. tarefas de limpeza de diretório</span><span class="sxs-lookup"><span data-stu-id="84e3e-111">1. Directory cleanup tasks</span></span>

<span data-ttu-id="84e3e-112">Antes de sincronizar o AD DS com seu locatário do Azure AD, você precisa limpar o AD DS.</span><span class="sxs-lookup"><span data-stu-id="84e3e-112">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84e3e-113">Se você não executar a limpeza do AD DS antes de sincronizar, pode haver um efeito negativo significativo no processo de implantação.</span><span class="sxs-lookup"><span data-stu-id="84e3e-113">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="84e3e-114">Pode levar dias ou até mesmo semanas para passar pelo ciclo de sincronização de diretórios, identificar erros e ressincronizar.</span><span class="sxs-lookup"><span data-stu-id="84e3e-114">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="84e3e-115">No AD DS, conclua as seguintes tarefas de limpeza para cada conta de usuário à qual a licença do Office 365 será atribuída:</span><span class="sxs-lookup"><span data-stu-id="84e3e-115">In your AD DS, complete the following clean-up tasks for each user account that will be assigned an Office 365 license:</span></span>
  
1. <span data-ttu-id="84e3e-116">Verifique se um endereço de email válido e exclusivo no atributo **proxyAddresses** .</span><span class="sxs-lookup"><span data-stu-id="84e3e-116">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="84e3e-117">Remova os valores duplicados no atributo **proxyAddresses** .</span><span class="sxs-lookup"><span data-stu-id="84e3e-117">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="84e3e-118">Se possível, assegure um valor válido e exclusivo para o atributo **userPrincipalName** no objeto **User** do usuário.</span><span class="sxs-lookup"><span data-stu-id="84e3e-118">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="84e3e-119">Para obter a melhor experiência de sincronização, verifique se o UPN do AD DS corresponde ao UPN do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="84e3e-119">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="84e3e-120">Se um usuário não tiver um valor para o atributo **userPrincipalName** , o objeto de **usuário** deverá conter um valor válido e exclusivo para o atributo **sAMAccountName** .</span><span class="sxs-lookup"><span data-stu-id="84e3e-120">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="84e3e-121">Remova os valores duplicados no atributo **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="84e3e-121">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="84e3e-122">Para o uso ideal da GAL (lista de endereços global), verifique se as informações nos seguintes atributos da conta de usuário do AD DS estão corretas:</span><span class="sxs-lookup"><span data-stu-id="84e3e-122">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="84e3e-123">givenName</span><span class="sxs-lookup"><span data-stu-id="84e3e-123">givenName</span></span>
  - <span data-ttu-id="84e3e-124">surname</span><span class="sxs-lookup"><span data-stu-id="84e3e-124">surname</span></span>
  - <span data-ttu-id="84e3e-125">displayName</span><span class="sxs-lookup"><span data-stu-id="84e3e-125">displayName</span></span>
  - <span data-ttu-id="84e3e-126">Cargo</span><span class="sxs-lookup"><span data-stu-id="84e3e-126">Job Title</span></span>
  - <span data-ttu-id="84e3e-127">Departamento</span><span class="sxs-lookup"><span data-stu-id="84e3e-127">Department</span></span>
  - <span data-ttu-id="84e3e-128">Escritório</span><span class="sxs-lookup"><span data-stu-id="84e3e-128">Office</span></span>
  - <span data-ttu-id="84e3e-129">Telefone comercial</span><span class="sxs-lookup"><span data-stu-id="84e3e-129">Office Phone</span></span>
  - <span data-ttu-id="84e3e-130">Telefone celular</span><span class="sxs-lookup"><span data-stu-id="84e3e-130">Mobile Phone</span></span>
  - <span data-ttu-id="84e3e-131">Número do fax</span><span class="sxs-lookup"><span data-stu-id="84e3e-131">Fax Number</span></span>
  - <span data-ttu-id="84e3e-132">Endereço</span><span class="sxs-lookup"><span data-stu-id="84e3e-132">Street Address</span></span>
  - <span data-ttu-id="84e3e-133">Cidade</span><span class="sxs-lookup"><span data-stu-id="84e3e-133">City</span></span>
  - <span data-ttu-id="84e3e-134">Estado</span><span class="sxs-lookup"><span data-stu-id="84e3e-134">State or Province</span></span>
  - <span data-ttu-id="84e3e-135">CEP</span><span class="sxs-lookup"><span data-stu-id="84e3e-135">Zip or Postal Code</span></span>
  - <span data-ttu-id="84e3e-136">País</span><span class="sxs-lookup"><span data-stu-id="84e3e-136">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="84e3e-137">2. preparação de objeto e atributo de diretório</span><span class="sxs-lookup"><span data-stu-id="84e3e-137">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="84e3e-138">A sincronização de diretório com êxito entre o AD DS e o Office 365 requer que seus atributos do AD DS sejam preparados corretamente.</span><span class="sxs-lookup"><span data-stu-id="84e3e-138">Successful directory synchronization between your AD DS and Office 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="84e3e-139">Por exemplo, você precisa garantir que caracteres específicos não sejam usados em determinados atributos que são sincronizados com o ambiente do Office 365.</span><span class="sxs-lookup"><span data-stu-id="84e3e-139">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="84e3e-140">Caracteres inesperados não causam a sincronização de diretório, mas podem retornar um aviso.</span><span class="sxs-lookup"><span data-stu-id="84e3e-140">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="84e3e-141">Caracteres inválidos causarão falha na sincronização do diretório.</span><span class="sxs-lookup"><span data-stu-id="84e3e-141">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="84e3e-142">A sincronização de diretórios também falhará se alguns dos seus usuários do AD DS tiverem um ou mais atributos duplicados.</span><span class="sxs-lookup"><span data-stu-id="84e3e-142">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="84e3e-143">Cada usuário deve ter atributos exclusivos.</span><span class="sxs-lookup"><span data-stu-id="84e3e-143">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="84e3e-144">Os atributos que você precisa preparar estão listados aqui:</span><span class="sxs-lookup"><span data-stu-id="84e3e-144">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="84e3e-145">**displayName**</span><span class="sxs-lookup"><span data-stu-id="84e3e-145">**displayName**</span></span>
    
  - <span data-ttu-id="84e3e-146">Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="84e3e-146">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="84e3e-147">Se esse atributo existir no objeto user, deverá haver um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="84e3e-147">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="84e3e-148">Ou seja, o atributo não deve estar em branco.</span><span class="sxs-lookup"><span data-stu-id="84e3e-148">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="84e3e-149">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="84e3e-149">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="84e3e-150">**givenName**</span><span class="sxs-lookup"><span data-stu-id="84e3e-150">**givenName**</span></span>
    
  - <span data-ttu-id="84e3e-151">Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não o exigirá ou o usará.</span><span class="sxs-lookup"><span data-stu-id="84e3e-151">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="84e3e-152">Número máximo de caracteres: 64</span><span class="sxs-lookup"><span data-stu-id="84e3e-152">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="84e3e-153">**mala**</span><span class="sxs-lookup"><span data-stu-id="84e3e-153">**mail**</span></span>
    
  - <span data-ttu-id="84e3e-154">O valor do atributo deve ser exclusivo no diretório.</span><span class="sxs-lookup"><span data-stu-id="84e3e-154">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="84e3e-155">Se houver valores duplicados, o primeiro usuário com o valor será sincronizado.</span><span class="sxs-lookup"><span data-stu-id="84e3e-155">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="84e3e-156">Os usuários subsequentes não aparecerão no Office 365.</span><span class="sxs-lookup"><span data-stu-id="84e3e-156">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="84e3e-157">Você deve modificar o valor no Office 365 ou modificar os dois valores no AD DS para que ambos os usuários apareçam no Office 365.</span><span class="sxs-lookup"><span data-stu-id="84e3e-157">You must modify either the value in Office 365 or modify both of the values in AD DS in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="84e3e-158">**mailNickname** (Alias do Exchange)</span><span class="sxs-lookup"><span data-stu-id="84e3e-158">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="84e3e-159">O valor do atributo não pode começar com um ponto (.).</span><span class="sxs-lookup"><span data-stu-id="84e3e-159">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="84e3e-160">O valor do atributo deve ser exclusivo no diretório.</span><span class="sxs-lookup"><span data-stu-id="84e3e-160">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="84e3e-161">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="84e3e-161">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="84e3e-162">Atributo de vários valores</span><span class="sxs-lookup"><span data-stu-id="84e3e-162">Multiple-value attribute</span></span>
  - <span data-ttu-id="84e3e-163">Número máximo de caracteres por valor: 256</span><span class="sxs-lookup"><span data-stu-id="84e3e-163">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="84e3e-164">O valor do atributo não deve conter um espaço.</span><span class="sxs-lookup"><span data-stu-id="84e3e-164">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="84e3e-165">O valor do atributo deve ser exclusivo no diretório.</span><span class="sxs-lookup"><span data-stu-id="84e3e-165">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="84e3e-166">Caracteres inválidos: \< \> (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="84e3e-166">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="84e3e-167">Observe que os caracteres inválidos se aplicam aos caracteres após o delimitador de tipo e ":", de modo que SMTP:User@contso.com seja permitido, mas SMTP:user:M@contoso.com não.</span><span class="sxs-lookup"><span data-stu-id="84e3e-167">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="84e3e-168">Todos os endereços SMTP (Simple Mail Transport Protocol) devem estar em conformidade com os padrões de mensagens de email.</span><span class="sxs-lookup"><span data-stu-id="84e3e-168">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="84e3e-169">Se houver endereços indesejados ou duplicados, consulte o tópico de ajuda [removendo endereços de proxy duplicados e indesejados no Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="84e3e-169">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="84e3e-170">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="84e3e-170">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="84e3e-171">Número máximo de caracteres: 20</span><span class="sxs-lookup"><span data-stu-id="84e3e-171">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="84e3e-172">O valor do atributo deve ser exclusivo no diretório.</span><span class="sxs-lookup"><span data-stu-id="84e3e-172">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="84e3e-173">Caracteres inválidos: [\ "|, \< \> /: + =;?</span><span class="sxs-lookup"><span data-stu-id="84e3e-173">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="84e3e-174">\* ]</span><span class="sxs-lookup"><span data-stu-id="84e3e-174"></span></span>
  - <span data-ttu-id="84e3e-175">Se um usuário tiver um atributo **sAMAccountName** inválido, mas tiver um atributo **userPrincipalName** válido, a conta do usuário será criada no Office 365.</span><span class="sxs-lookup"><span data-stu-id="84e3e-175">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="84e3e-176">Se **sAMAccountName** e **userPrincipalName** forem inválidos, o atributo **userPrincipalName** do AD DS deverá ser atualizado.</span><span class="sxs-lookup"><span data-stu-id="84e3e-176">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="84e3e-177">**SN** sobrenome</span><span class="sxs-lookup"><span data-stu-id="84e3e-177">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="84e3e-178">Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não o exigirá ou o usará.</span><span class="sxs-lookup"><span data-stu-id="84e3e-178">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="84e3e-179">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="84e3e-179">**targetAddress**</span></span>
    
    <span data-ttu-id="84e3e-180">É necessário que o atributo **targetAddress** (por exemplo, SMTP:Tom@contoso.com) preenchido para o usuário deve aparecer na GAL do Office 365.</span><span class="sxs-lookup"><span data-stu-id="84e3e-180">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="84e3e-181">Em cenários de migração de mensagens de terceiros, isso exigiria a extensão de esquema do Office 365 para o AD DS.</span><span class="sxs-lookup"><span data-stu-id="84e3e-181">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the AD DS.</span></span> <span data-ttu-id="84e3e-182">A extensão de esquema do Office 365 também adicionaria outros atributos úteis para gerenciar objetos do Office 365 que são preenchidos usando uma ferramenta de sincronização de diretório do AD DS.</span><span class="sxs-lookup"><span data-stu-id="84e3e-182">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="84e3e-183">Por exemplo, o atributo **msExchHideFromAddressLists** para gerenciar caixas de correio ou grupos de distribuição ocultos seria adicionado.</span><span class="sxs-lookup"><span data-stu-id="84e3e-183">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="84e3e-184">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="84e3e-184">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="84e3e-185">O valor do atributo não deve conter um espaço.</span><span class="sxs-lookup"><span data-stu-id="84e3e-185">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="84e3e-186">O valor do atributo deve ser exclusivo no diretório.</span><span class="sxs-lookup"><span data-stu-id="84e3e-186">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="84e3e-187">Caracteres inválidos \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="84e3e-187">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="84e3e-188">Todos os endereços SMTP (Simple Mail Transport Protocol) devem estar em conformidade com os padrões de mensagens de email.</span><span class="sxs-lookup"><span data-stu-id="84e3e-188">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="84e3e-189">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="84e3e-189">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="84e3e-190">O atributo **userPrincipalName** deve estar no formato de entrada no estilo da Internet, onde o nome do usuário é seguido pelo sinal de arroba (@) e um nome de domínio: por exemplo, User@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="84e3e-190">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="84e3e-191">Todos os endereços SMTP (Simple Mail Transport Protocol) devem estar em conformidade com os padrões de mensagens de email.</span><span class="sxs-lookup"><span data-stu-id="84e3e-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="84e3e-192">O número máximo de caracteres para o atributo **userPrincipalName** é 113.</span><span class="sxs-lookup"><span data-stu-id="84e3e-192">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="84e3e-193">Um número específico de caracteres é permitido antes e depois do sinal de arroba (@), da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="84e3e-193">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="84e3e-194">Número máximo de caracteres para o nome de usuário que está na frente do sinal de arroba (@): 64</span><span class="sxs-lookup"><span data-stu-id="84e3e-194">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="84e3e-195">Número máximo de caracteres para o nome de domínio após o sinal de arroba (@): 48</span><span class="sxs-lookup"><span data-stu-id="84e3e-195">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="84e3e-196">Caracteres inválidos: &amp; \* \% +/=?</span><span class="sxs-lookup"><span data-stu-id="84e3e-196">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="84e3e-197">{ } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="84e3e-197"></span></span>
  - <span data-ttu-id="84e3e-198">Um trema também é um caractere inválido.</span><span class="sxs-lookup"><span data-stu-id="84e3e-198">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="84e3e-199">O caractere @ é necessário em cada valor **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="84e3e-199">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="84e3e-200">O caractere @ não pode ser o primeiro caractere em cada valor **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="84e3e-200">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="84e3e-201">O nome de usuário não pode terminar com um ponto (.),&amp;um e comercial (), um espaço ou um sinal de arroba (@).</span><span class="sxs-lookup"><span data-stu-id="84e3e-201">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="84e3e-202">O nome de usuário não pode conter espaços.</span><span class="sxs-lookup"><span data-stu-id="84e3e-202">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="84e3e-203">Domínios roteáveis devem ser usados; por exemplo, domínios locais ou internos não podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="84e3e-203">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="84e3e-204">Unicode é convertido em caracteres de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="84e3e-204">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="84e3e-205">**userPrincipalName** não pode conter valores duplicados no diretório.</span><span class="sxs-lookup"><span data-stu-id="84e3e-205">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 

<span data-ttu-id="84e3e-206">Consulte [preparar atributos de diretório com a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) para usar a ferramenta IdFix para identificar erros nos atributos do AD DS.</span><span class="sxs-lookup"><span data-stu-id="84e3e-206">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFIx tool to identify errors in the attributes of your AD DS.</span></span>
    
## <a name="2-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="84e3e-207">2. Prepare o atributo userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="84e3e-207">2. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="84e3e-208">O Active Directory é projetado para permitir que os usuários finais em sua organização entrem em seu diretório usando **sAMAccountName** ou **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="84e3e-208">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="84e3e-209">Da mesma forma, os usuários finais podem entrar no Office 365 usando o nome principal do usuário (UPN) de sua conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="84e3e-209">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="84e3e-210">A sincronização de diretório tenta criar novos usuários no Azure Active Directory usando o mesmo UPN que está no seu SD do AD.</span><span class="sxs-lookup"><span data-stu-id="84e3e-210">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD SD.</span></span> <span data-ttu-id="84e3e-211">O UPN é formatado como um endereço de email.</span><span class="sxs-lookup"><span data-stu-id="84e3e-211">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="84e3e-212">No Office 365, o UPN é o atributo padrão usado para gerar o endereço de email.</span><span class="sxs-lookup"><span data-stu-id="84e3e-212">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="84e3e-213">É fácil obter **userPrincipalName** (no AD DS e no Azure AD) e o endereço de email principal no **proxyAddresses** definido como valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="84e3e-213">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="84e3e-214">Quando estão definidas como valores diferentes, pode haver confusão para administradores e usuários finais.</span><span class="sxs-lookup"><span data-stu-id="84e3e-214">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="84e3e-215">É melhor alinhar esses atributos para reduzir a confusão.</span><span class="sxs-lookup"><span data-stu-id="84e3e-215">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="84e3e-216">Para atender aos requisitos de logon único com os serviços de Federação do Active Directory (AD FS) 2,0, você precisa garantir que os UPNs no Active Directory do Azure e o AD DS coincidam e estejam usando um namespace de domínio válido.</span><span class="sxs-lookup"><span data-stu-id="84e3e-216">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="84e3e-217">4. adicionar um sufixo UPN alternativo ao AD DS</span><span class="sxs-lookup"><span data-stu-id="84e3e-217">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="84e3e-218">Talvez seja necessário adicionar um sufixo UPN alternativo para associar as credenciais corporativas do usuário ao ambiente do Office 365.</span><span class="sxs-lookup"><span data-stu-id="84e3e-218">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="84e3e-219">Um sufixo UPN é a parte do UPN à direita do caractere @.</span><span class="sxs-lookup"><span data-stu-id="84e3e-219">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="84e3e-220">UPNs usados para logon único podem conter letras, números, pontos, traços e sublinhados, mas nenhum outro tipo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="84e3e-220">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="84e3e-221">Para obter mais informações sobre como adicionar um sufixo UPN alternativo ao Active Directory, consulte [preparar para a sincronização de diretórios]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="84e3e-221">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a><span data-ttu-id="84e3e-222">5. corresponder ao UPN do AD DS com o UPN do Office 365</span><span class="sxs-lookup"><span data-stu-id="84e3e-222">5. Match the AD DS UPN with the Office 365 UPN</span></span>

<span data-ttu-id="84e3e-223">Se você já configurou a sincronização de diretórios, o UPN do usuário para Office 365 pode não corresponder ao UPN do AD DS do usuário definido no AD DS.</span><span class="sxs-lookup"><span data-stu-id="84e3e-223">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="84e3e-224">Isso pode ocorrer quando uma licença foi atribuída ao usuário antes da verificação do domínio.</span><span class="sxs-lookup"><span data-stu-id="84e3e-224">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="84e3e-225">Para corrigir isso, use o [PowerShell para corrigir](https://go.microsoft.com/fwlink/p/?LinkId=396730) o UPN duplicado para atualizar o UPN do usuário para garantir que o UPN do Office 365 corresponda ao nome de usuário e ao domínio da empresa.</span><span class="sxs-lookup"><span data-stu-id="84e3e-225">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="84e3e-226">Se você estiver atualizando o UPN no AD DS e quiser que ele seja sincronizado com a identidade do Azure Active Directory, será necessário remover a licença do usuário no Office 365 antes de realizar as alterações no AD DS.</span><span class="sxs-lookup"><span data-stu-id="84e3e-226">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="84e3e-227">Consulte também [como preparar um domínio não roteável (como o domínio. local) para a sincronização de diretórios](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="84e3e-227">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>


## <a name="next-steps"></a><span data-ttu-id="84e3e-228">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="84e3e-228">Next steps</span></span>

<span data-ttu-id="84e3e-229">Consulte [preparar atributos de diretório com a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) para ajudá-lo a corrigir erros nos atributos do AD DS antes da sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="84e3e-229">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to help you correct errors in the attributes of your AD DS prior to directory synchronization.</span></span>

<span data-ttu-id="84e3e-230">Se você corrigiu todos os erros de atributo identificados com a ferramenta IdFix e tiver concluído as etapas 1 a 5 acima, consulte [set up Directory Synchronization](set-up-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="84e3e-230">If you have corrected all the attribute errors identified with the IdFix tool and have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>
