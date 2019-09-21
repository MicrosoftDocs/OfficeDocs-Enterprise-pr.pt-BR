---
title: Controles de acesso administrativo no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Resumo: uma visão geral dos controles de acesso administrativo e categorização de dados do Office 365.'
ms.openlocfilehash: e8cc470c617deea7435841f276b772b0a8ef17a3
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067184"
---
# <a name="administrative-access-controls-in-office-365"></a><span data-ttu-id="fbeed-103">Controles de acesso administrativo no Office 365</span><span class="sxs-lookup"><span data-stu-id="fbeed-103">Administrative Access Controls in Office 365</span></span> 

<span data-ttu-id="fbeed-104">A Microsoft investiu pesadamente em sistemas e controles que automatizam a maioria das operações do Office 365 enquanto limitava intencionalmente o acesso ao conteúdo do cliente pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fbeed-104">Microsoft has invested heavily in systems and controls that automate most Office 365 operations while intentionally limiting access to customer content by Microsoft.</span></span> <span data-ttu-id="fbeed-105">Os seres humanos governam o serviço e o software opera o serviço.</span><span class="sxs-lookup"><span data-stu-id="fbeed-105">Humans govern the service, and software operates the service.</span></span> <span data-ttu-id="fbeed-106">Isso permite que a Microsoft gerencie o Office 365 em escala e gerencie os riscos de ameaças internas ao conteúdo do cliente.</span><span class="sxs-lookup"><span data-stu-id="fbeed-106">This enables Microsoft to manage Office 365 at scale and manage the risks of internal threats to customer content.</span></span>

<span data-ttu-id="fbeed-107">Por padrão, os engenheiros da Microsoft têm nenhum privilégio administrativo de pé e zero acesso de pé ao conteúdo do cliente no Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbeed-107">By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Office 365.</span></span> <span data-ttu-id="fbeed-108">Um engenheiro da Microsoft pode ter acesso limitado, auditado e protegido ao conteúdo de um cliente por um período limitado de tempo.</span><span class="sxs-lookup"><span data-stu-id="fbeed-108">A Microsoft engineer can have limited, audited, and secured access to a customer's content for a limited amount of time.</span></span> <span data-ttu-id="fbeed-109">O acesso é apenas quando necessário para operações de serviço e somente quando aprovado por um membro do gerenciamento sênior da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fbeed-109">Access is only when necessary for service operations and only when approved by a member of Microsoft senior management.</span></span> <span data-ttu-id="fbeed-110">Para clientes licenciados de lockbox de clientes, o cliente fornece aprovação de acesso para seu conteúdo hospedado no Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbeed-110">For Customer Lockbox licensed customers, the customer provides access approval to their content hosted on Office 365.</span></span>

<span data-ttu-id="fbeed-111">A Microsoft fornece serviços online usando várias formas de entrega na nuvem:</span><span class="sxs-lookup"><span data-stu-id="fbeed-111">Microsoft provides online services using multiple forms of cloud delivery:</span></span>

- <span data-ttu-id="fbeed-112">**Nuvens públicas:** Inclui versões de vários locatários do Office 365, Azure e outros serviços hospedados na América do Norte, América do Sul, Europa, Ásia, Austrália, etc.</span><span class="sxs-lookup"><span data-stu-id="fbeed-112">**Public Clouds:** Includes multi-tenant versions of Office 365, Azure, and other services hosted in North America, South America, Europe, Asia, Australia, etc.</span></span>
- <span data-ttu-id="fbeed-113">**Nuvens nacionais:** Inclui todas as nuvens soberana e operadas por terceiros fora dos Estados Unidos (exceto aqueles observados anteriormente), como o Office 365 na China (operado pela 21Vianet) e o Office 365 na Alemanha (operado pela Microsoft, mas em um modelo no qual um data de confiança em alemão, O alemão Telekom, controla e monitora o acesso da Microsoft aos dados e sistemas de clientes que contêm dados do cliente).</span><span class="sxs-lookup"><span data-stu-id="fbeed-113">**National Clouds:** Includes all sovereign and third party-operated clouds outside of the United States (except ones noted previously), such as Office 365 in China (operated by 21Vianet), and Office 365 in Germany (operated by Microsoft, but under a model in which a German data trustee, Deutsche Telekom, controls and monitors Microsoft's access to Customer Data and systems that contain Customer Data).</span></span>
- <span data-ttu-id="fbeed-114">**Nuvens governamentais:** Inclui os serviços do Office 365 e do Azure que estão disponíveis para os clientes do governo dos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="fbeed-114">**Government Clouds:** Includes Office 365 and Azure services that are available to United States government customers.</span></span>

<span data-ttu-id="fbeed-115">Para os fins deste artigo, os serviços do Office 365 incluem:</span><span class="sxs-lookup"><span data-stu-id="fbeed-115">For purposes of this article, Office 365 services include:</span></span>

- [<span data-ttu-id="fbeed-116">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="fbeed-116">Exchange Online</span></span>](https://docs.microsoft.com/Exchange/exchange-online)
- [<span data-ttu-id="fbeed-117">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="fbeed-117">Exchange Online Protection</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [<span data-ttu-id="fbeed-118">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fbeed-118">SharePoint Online</span></span>](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [<span data-ttu-id="fbeed-119">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="fbeed-119">OneDrive for Business</span></span>](https://docs.microsoft.com/OneDrive/onedrive)
- [<span data-ttu-id="fbeed-120">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="fbeed-120">Skype for Business</span></span>](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [<span data-ttu-id="fbeed-121">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="fbeed-121">Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [<span data-ttu-id="fbeed-122">Yammer</span><span class="sxs-lookup"><span data-stu-id="fbeed-122">Yammer</span></span>](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a><span data-ttu-id="fbeed-123">Controles de acesso do Office 365</span><span class="sxs-lookup"><span data-stu-id="fbeed-123">Office 365 Access Controls</span></span>

<span data-ttu-id="fbeed-124">Para fins de controle de acesso, a Microsoft categoriza os dados do Office 365 como dados do cliente ou outros tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="fbeed-124">For access control purposes, Microsoft categorizes Office 365 data as Customer data or other types of data.</span></span>

### <a name="customer-data"></a><span data-ttu-id="fbeed-125">Dados do cliente</span><span class="sxs-lookup"><span data-stu-id="fbeed-125">Customer data</span></span>

<span data-ttu-id="fbeed-126">Os dados do cliente são todos os dados fornecidos por ou em nome de um cliente ao usar os serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbeed-126">Customer data is all data provided by or on behalf of a customer when using Office 365 services.</span></span> <span data-ttu-id="fbeed-127">Este é o conteúdo do cliente criado diretamente ou carregado por usuários do Office 365, incluindo:</span><span class="sxs-lookup"><span data-stu-id="fbeed-127">This is customer content directly created or uploaded by Office 365 users, including:</span></span>

- <span data-ttu-id="fbeed-128">Emails</span><span class="sxs-lookup"><span data-stu-id="fbeed-128">Emails</span></span>
- <span data-ttu-id="fbeed-129">Conteúdo do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fbeed-129">SharePoint Online content</span></span>
- <span data-ttu-id="fbeed-130">Mensagens instantâneas</span><span class="sxs-lookup"><span data-stu-id="fbeed-130">Instant messages</span></span>
- <span data-ttu-id="fbeed-131">Itens de calendário</span><span class="sxs-lookup"><span data-stu-id="fbeed-131">Calendar items</span></span>
- <span data-ttu-id="fbeed-132">Documentos</span><span class="sxs-lookup"><span data-stu-id="fbeed-132">Documents</span></span>
- <span data-ttu-id="fbeed-133">Contatos</span><span class="sxs-lookup"><span data-stu-id="fbeed-133">Contacts</span></span>
- <span data-ttu-id="fbeed-134">Informações de identificação do usuário final (EUII) (dados exclusivos de um usuário ou que são vinculados a um usuário individual, mas não inclui conteúdo do cliente).</span><span class="sxs-lookup"><span data-stu-id="fbeed-134">End-user identifiable information (EUII) (data that is unique to a user or that is linkable to an individual user but does not include customer content).</span></span>

### <a name="other-types-of-data"></a><span data-ttu-id="fbeed-135">Outros tipos de dados</span><span class="sxs-lookup"><span data-stu-id="fbeed-135">Other types of data</span></span>

<span data-ttu-id="fbeed-136">Outros tipos de dados incluem:</span><span class="sxs-lookup"><span data-stu-id="fbeed-136">Other types of data include:</span></span>

- <span data-ttu-id="fbeed-137">**Dados da conta:** Inclui dados administrativos (informações fornecidas por administradores ao inscrever-se ou comprar serviços) e dados de pagamento (informações sobre instrumentos de pagamento, como detalhes do cartão de crédito).</span><span class="sxs-lookup"><span data-stu-id="fbeed-137">**Account data:** Includes administrative data (information provided by administrators when they sign-up or purchase services), and payment data (information about payment instruments, such as credit card details).</span></span>
- <span data-ttu-id="fbeed-138">**Informações de identificação corporativa:** Inclui dados usados para identificar um locatário, dados de uso e não vinculáveis a um usuário individual ou incluído no conteúdo do cliente.</span><span class="sxs-lookup"><span data-stu-id="fbeed-138">**Organizationally identifiable information:** Includes data used to identify a tenant, usage data, and not linkable to an individual user or included in customer content.</span></span>
- <span data-ttu-id="fbeed-139">**Metadados do sistema:** Inclui logs de serviço que contêm definições de configuração, status do sistema, endereços IP da Microsoft e informações técnicas sobre inscrições e locatários.</span><span class="sxs-lookup"><span data-stu-id="fbeed-139">**System metadata:** Includes service logs that contain configuration settings, system status, Microsoft IP addresses, and technical information about subscriptions and tenants.</span></span>

<span data-ttu-id="fbeed-140">A Microsoft estabeleceu mecanismos de controle de acesso para garantir que ninguém tenha acesso não aprovado aos dados do cliente ou aos dados de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="fbeed-140">Microsoft has established access control mechanisms to ensure that no one has unapproved access to Customer Data or access control data.</span></span> <span data-ttu-id="fbeed-141">Os dados de controle de acesso gerenciam o acesso a outros tipos de dados ou funções dentro do ambiente, incluindo acesso ao conteúdo do cliente ou EUII, senhas da Microsoft, certificados de segurança e outros dados relacionados à autenticação.</span><span class="sxs-lookup"><span data-stu-id="fbeed-141">Access control data manages access to other types of data or functions within the environment, including access to customer content or EUII, Microsoft passwords, security certificates, and other authentication-related data.</span></span> <span data-ttu-id="fbeed-142">Os mecanismos de controle de acesso também protegem contra acesso físico, lógico ou remoto não aprovado ao ambiente de produção do Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbeed-142">Access control mechanisms also guard against unapproved physical, logical, or remote access to the Office 365 production environment.</span></span>

<span data-ttu-id="fbeed-143">Há três categorias de controles de acesso usados pela Microsoft para a operação do Office 365:</span><span class="sxs-lookup"><span data-stu-id="fbeed-143">There are three categories of access controls used by Microsoft for operating Office 365:</span></span>

- <span data-ttu-id="fbeed-144">Controles de isolamento</span><span class="sxs-lookup"><span data-stu-id="fbeed-144">Isolation Controls</span></span>
- <span data-ttu-id="fbeed-145">Controles de pessoal</span><span class="sxs-lookup"><span data-stu-id="fbeed-145">Personnel Controls</span></span>
- <span data-ttu-id="fbeed-146">Controles de tecnologia</span><span class="sxs-lookup"><span data-stu-id="fbeed-146">Technology Controls</span></span>

<span data-ttu-id="fbeed-147">Quando combinadas, esses controles ajudam a evitar e detectar ações mal-intencionadas no Office 365.</span><span class="sxs-lookup"><span data-stu-id="fbeed-147">When combined, these controls help prevent and detect malicious actions in Office 365.</span></span> <span data-ttu-id="fbeed-148">Além dos controles de isolamento, pessoal e tecnologia usados pela Microsoft, há uma quarta categoria de controles: as implementadas por clientes.</span><span class="sxs-lookup"><span data-stu-id="fbeed-148">In addition to the isolation, personnel, and technology controls used by Microsoft, there is a fourth category of controls: those implemented by customers.</span></span>

<span data-ttu-id="fbeed-149">O Office 365 permite que você gerencie dados da mesma forma que os dados são gerenciados em ambientes locais.</span><span class="sxs-lookup"><span data-stu-id="fbeed-149">Office 365 allows you to manage data the same way data is managed in on-premises environments.</span></span> <span data-ttu-id="fbeed-150">A pessoa que assina uma organização para o Office 365 se torna automaticamente um administrador global.</span><span class="sxs-lookup"><span data-stu-id="fbeed-150">The person who signs up an organization for Office 365 automatically becomes a global administrator.</span></span> <span data-ttu-id="fbeed-151">O administrador global tem acesso a todos os recursos nos portais de gerenciamento e pode:</span><span class="sxs-lookup"><span data-stu-id="fbeed-151">The global admin has access to all features in Management Portals and can:</span></span>

- <span data-ttu-id="fbeed-152">Criar ou editar usuários</span><span class="sxs-lookup"><span data-stu-id="fbeed-152">Create or edit users</span></span>
- <span data-ttu-id="fbeed-153">Atribuir funções de administrador a outras pessoas</span><span class="sxs-lookup"><span data-stu-id="fbeed-153">Assign admin roles to others</span></span>
- <span data-ttu-id="fbeed-154">Redefinir senhas de usuário</span><span class="sxs-lookup"><span data-stu-id="fbeed-154">Reset user passwords</span></span>
- <span data-ttu-id="fbeed-155">Gerenciar licenças de usuário</span><span class="sxs-lookup"><span data-stu-id="fbeed-155">Manage user licenses</span></span>
- <span data-ttu-id="fbeed-156">Gerenciar domínios</span><span class="sxs-lookup"><span data-stu-id="fbeed-156">Manage domains</span></span>
- <span data-ttu-id="fbeed-157">Aprovar solicitações de lockbox do cliente</span><span class="sxs-lookup"><span data-stu-id="fbeed-157">Approve Customer Lockbox requests</span></span>

<span data-ttu-id="fbeed-158">Recomendamos que cada organização configure pelo menos duas contas de administrador.</span><span class="sxs-lookup"><span data-stu-id="fbeed-158">We recommend that each organization configure at least two admin accounts.</span></span> <span data-ttu-id="fbeed-159">Para organizações de grande porte, recomendamos contas de administração especializadas que atendam a diferentes funções.</span><span class="sxs-lookup"><span data-stu-id="fbeed-159">For large enterprise organizations, we recommend specialized admin accounts that serve different functions.</span></span>

<span data-ttu-id="fbeed-160">Para obter informações sobre como atribuir permissões e funções de administrador, consulte [atribuindo funções de administrador no office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) e [sobre as funções de administrador do Office 365](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span><span class="sxs-lookup"><span data-stu-id="fbeed-160">For information about assigning admin roles and permissions, see [Assigning admin roles in Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) and [About Office 365 admin roles](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span></span>

## <a name="related-links"></a><span data-ttu-id="fbeed-161">Links relacionados</span><span class="sxs-lookup"><span data-stu-id="fbeed-161">Related Links</span></span>

- [<span data-ttu-id="fbeed-162">Controles de isolamento</span><span class="sxs-lookup"><span data-stu-id="fbeed-162">Isolation Controls</span></span>](office-365-isolation-controls.md)
- [<span data-ttu-id="fbeed-163">Controles de pessoal</span><span class="sxs-lookup"><span data-stu-id="fbeed-163">Personnel Controls</span></span>](office-365-personnel-controls.md)
- [<span data-ttu-id="fbeed-164">Controles de tecnologia</span><span class="sxs-lookup"><span data-stu-id="fbeed-164">Technology Controls</span></span>](office-365-technology-controls.md)
- [<span data-ttu-id="fbeed-165">Monitorando e auditando controles de acesso </span><span class="sxs-lookup"><span data-stu-id="fbeed-165">Monitoring and Auditing Access Controls</span></span>](office-365-monitoring-and-auditing-access-controls.md)
- [<span data-ttu-id="fbeed-166">Controles de acesso do Yammer Enterprise</span><span class="sxs-lookup"><span data-stu-id="fbeed-166">Yammer Enterprise Access Controls</span></span>](office-365-yammer-enterprise-access-controls.md)