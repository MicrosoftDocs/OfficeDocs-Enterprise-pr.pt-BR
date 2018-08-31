---
title: Recursos de multi-Geo no Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Expanda sua presença do Office 365 para várias regiões geográficas com os recursos de multi-geo no Exchange Online.
ms.openlocfilehash: 9834b102365f11623a1decc00460f85f36552ccb
ms.sourcegitcommit: d88307a32fd3439a09a87b260e0c0cf9074ebeb0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2018
ms.locfileid: "22914776"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="f1f78-103">Recursos de multi-Geo no Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f1f78-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="f1f78-p101">Recursos de multi-Geo no Office 365 habilitar um único locatário englobe vários locais geográficos (Geos). Quando Multi-Geo estiver habilitada, os clientes podem selecionar o local do conteúdo de caixa de correio Exchange Online (dados em repouso) em uma base por usuário.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="f1f78-p102">Seu local de locatário inicial (conhecido como seus "padrão" ou "central" local) é determinada com base em seu endereço de cobrança. Quando Multi-Geo estiver habilitada, você pode colocar a caixas de correio em locais adicionais "satélite" por:</span><span class="sxs-lookup"><span data-stu-id="f1f78-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="f1f78-108">Criando uma nova caixa de correio Exchange Online diretamente em um satélite.</span><span class="sxs-lookup"><span data-stu-id="f1f78-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="f1f78-109">Mover uma caixa de correio do Exchange Online existente para um satélite.</span><span class="sxs-lookup"><span data-stu-id="f1f78-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="f1f78-110">Inclusão de uma caixa de correio de uma organização do Exchange local diretamente em um satélite.</span><span class="sxs-lookup"><span data-stu-id="f1f78-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="f1f78-111">Os Geos a seguintes estão disponíveis para uso em uma configuração de Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="f1f78-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="f1f78-112">Ásia Pacífico</span><span class="sxs-lookup"><span data-stu-id="f1f78-112">Asia Pacific</span></span>

- <span data-ttu-id="f1f78-113">Austrália</span><span class="sxs-lookup"><span data-stu-id="f1f78-113">Australia</span></span>

- <span data-ttu-id="f1f78-114">Canadá</span><span class="sxs-lookup"><span data-stu-id="f1f78-114">Canada</span></span>

- <span data-ttu-id="f1f78-115">União Europeia</span><span class="sxs-lookup"><span data-stu-id="f1f78-115">European Union</span></span>

- <span data-ttu-id="f1f78-116">França</span><span class="sxs-lookup"><span data-stu-id="f1f78-116">France</span></span>

- <span data-ttu-id="f1f78-117">Índia (atualmente disponível apenas a clientes com os endereços de cobrança na Índia)</span><span class="sxs-lookup"><span data-stu-id="f1f78-117">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="f1f78-118">Japão</span><span class="sxs-lookup"><span data-stu-id="f1f78-118">Japan</span></span>

- <span data-ttu-id="f1f78-119">Coreia</span><span class="sxs-lookup"><span data-stu-id="f1f78-119">Korea</span></span>

- <span data-ttu-id="f1f78-120">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="f1f78-120">United Kingdom</span></span>

- <span data-ttu-id="f1f78-121">Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="f1f78-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="f1f78-122">Configuração de pré-requisito</span><span class="sxs-lookup"><span data-stu-id="f1f78-122">Prerequisite configuration</span></span>
<span data-ttu-id="f1f78-p103">Antes de começar a usar o Multi-Geo recursos no Exchange Online, o Microsoft precisa configurar seu locatário do Exchange Online para suporte Multi-Geo. Esse processo de configuração de uma única vez é disparado depois que você encomendar que multi-Geo e as licenças mostram no nosso inquilino. Esse processo de configuração de uma única vez normalmente deve levar menos de 30 dias para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered after you order Multi-Geo and the licenses show up in our tenant. This one-time configuration process should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="f1f78-p104">Você receberá notificações no [Centro de mensagem do Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) , quando a configuração foi concluída. Configuração automaticamente é acionada depois de suas licenças Multi-Geo mostram no seu locatário.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your Multi-Geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="f1f78-128">Movimentações e posicionamento de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f1f78-128">Mailbox placement and moves</span></span>
<span data-ttu-id="f1f78-129">Após a conclusão da Microsoft as etapas de configuração de Multi-Geo pré-requisito, o Exchange Online aceita o atributo **PreferredDataLocation** em objetos de usuário no Windows Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f1f78-129">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="f1f78-p105">O Exchange Online sincroniza a propriedade **PreferredDataLocation** do Azure AD para a propriedade **MailboxRegion** no serviço de diretório Exchange Online. O valor **MailboxRegion** determina o Geo onde caixas de correio de usuário e qualquer caixa de correio de arquivo morto associada será colocada. Não é possível configurar da caixa de correio e arquivamento caixas de correio primárias um usuário para residir em Geos diferentes. Apenas um Geo pode ser configurado por um objeto de usuário.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="f1f78-134">Quando **PreferredDataLocation** estiver configurada em um usuário com uma caixa de correio existente, a caixa de correio será colocado em uma fila de realocação e movidas automaticamente para o Geo especificado.</span><span class="sxs-lookup"><span data-stu-id="f1f78-134">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="f1f78-135">Quando **PreferredDataLocation** estiver configurada em um usuário sem uma caixa de correio existente, a caixa de correio será provisionada para o Geo especificado.</span><span class="sxs-lookup"><span data-stu-id="f1f78-135">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="f1f78-136">Quando **PreferredDataLocation** não for especificado em um usuário, a caixa de correio será colocada no Geo padrão.</span><span class="sxs-lookup"><span data-stu-id="f1f78-136">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the default Geo.</span></span>

- <span data-ttu-id="f1f78-137">Se o código de **PreferredDataLocation** está incorreto (por exemplo, um tipo de NAN em vez do nome), a caixa de correio será colocada no Geo padrão.</span><span class="sxs-lookup"><span data-stu-id="f1f78-137">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="f1f78-p106">**Observação**: capacidades de Multi-Geo e Skype para Business Online regional hospedada reuniões usam a propriedade **PreferredDataLocation** nos objetos de usuário para localizar serviços. Se você configurar valores **PreferredDataLocation** em objetos de usuário para reuniões regional hospedadas, a caixa de correio dos usuários serão automaticamente movida para o Geo especificado depois Multi-Geo está habilitado no inquilino do Office 365.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="f1f78-140">Limitações do recurso para Multi-Geo no Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f1f78-140">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="f1f78-p107">Apenas caixas de correio do usuário, caixas de correio de recurso (caixas de correio de sala e equipamento) e caixas de correio compartilhadas suportam recursos de Multi-Geo. Caixas de correio de pasta de públicos e grupos do Office 365 permanecem em Geo de página inicial do cliente.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. Public Folder Mailboxes and Office 365 Groups remain in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="f1f78-p108">Segurança e conformidade recursos (por exemplo, auditoria e descoberta eletrônica) que estão disponíveis no Centro de administração do Exchange (EAC) não estão disponíveis nas organizações Multi-Geo. Em vez disso, você precisará usar o [Centro de conformidade e segurança do Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar recursos de segurança e conformidade.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="f1f78-p109">Outlook para Mac usuários perceba uma perda temporária de acesso a sua pasta de arquivo morto Online enquanto você move suas caixas de correio para um novo Geo. Esta condição ocorre quando o principal do usuário e caixas de correio de arquivo morto estejam em Geos diferentes, porque cross-Geo movimentações de caixa de correio podem ser concluído em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="f1f78-p110">Os usuários não podem compartilhar *pastas de caixa de correio* entre Geos no Outlook na web (anteriormente conhecido como o Outlook Web App ou no OWA). Por exemplo, um usuário na União Europeia não pode usar o Outlook na web para abrir uma pasta compartilhada em uma caixa de correio que está localizada nos Estados Unidos. No entanto, o Outlook em que os usuários da Web pode abrir *outras caixas de correio* em diferentes Geos usando uma janela separada do navegador, conforme descrito em [Abrir a caixa de correio de outra pessoa em uma janela separada do navegador no Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="f1f78-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="f1f78-150">**Observação**: o compartilhamento de pasta de caixa de correio entre-Geo é suportado no Outlook no Windows.</span><span class="sxs-lookup"><span data-stu-id="f1f78-150">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="f1f78-151">Administração</span><span class="sxs-lookup"><span data-stu-id="f1f78-151">Administration</span></span> 
<span data-ttu-id="f1f78-p111">PowerShell remoto é necessária para exibir e configurar propriedades relacionadas ao Geo no seu ambiente do Office 365. Para obter informações sobre vários módulos do PowerShell usados para administrar o Office 365, consulte [Gerenciando o Office 365 e o Exchange Online com o Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="f1f78-p111">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="f1f78-p112">É necessário o [Módulo Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou posterior em v1. x para ver a propriedade **PreferredDataLocation** em objetos de usuário. Objetos de usuário sincronizados via AAD conectar no AAD não podem ter seu valor **PreferredDataLocation** modificada diretamente por meio do PowerShell AAD. Objetos de usuário somente na nuvem podem ser modificados por meio do PowerShell AAD. Para se conectar ao AD do Windows Azure PowerShell, consulte [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="f1f78-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="f1f78-158">Para conectar ao Exchange Online PowerShell, consulte [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="f1f78-158">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="f1f78-159">Conectar-se diretamente a um Geo específico usando o PowerShell do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f1f78-159">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="f1f78-p113">Normalmente, o Exchange Online PowerShell se conectará ao Geo padrão. Porém, você também pode conectar diretamente à Geos não-padrão. Devido aos aprimoramentos de desempenho, recomendamos que você se conectando diretamente ao Geo não-padrão, quando você gerencia somente usuários em que Geo.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p113">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="f1f78-p114">Para conectar a um Geo específico, o parâmetro *ConnectionUri* é diferente das instruções de conexão regular. O restante dos comandos e valores são os mesmos. As etapas são:</span><span class="sxs-lookup"><span data-stu-id="f1f78-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="f1f78-166">No computador local, abra o Windows PowerShell e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1f78-166">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="f1f78-167">Na caixa de diálogo **Solicitação de credencial do Windows PowerShell** , digite seu trabalho escola conta e senha e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="f1f78-167">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="f1f78-p115">Substituir `<emailaddress>` com o endereço de email de **qualquer** caixa de correio de destino Geo e execute o comando a seguir. Suas permissões na caixa de correio e a relação com suas credenciais na etapa 1 não são um fator; o endereço de email simplesmente informa o Exchange Online onde para se conectar.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="f1f78-170">Por exemplo, se olga@contoso.onmicrosoft.com é o endereço de email de uma caixa de correio válida do Geo que você deseja se conectar, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1f78-170">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="f1f78-171">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1f78-171">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="f1f78-172">Requisitos de versão do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="f1f78-172">Azure AD Connect version requirements</span></span>
<span data-ttu-id="f1f78-p116">Conectar AAD versão 1.1.524.0 ou posterior é o único método suportado para definir a propriedade **PreferredDataLocation** nos objetos de usuário que são sincronizados do Active Directory no local. Objetos de usuário sincronizados via AAD conectar no AAD não podem ter seu valor **PreferredDataLocation** modificada diretamente por meio do PowerShell AAD. Objetos de usuário somente na nuvem podem ser modificados por meio do PowerShell AAD. Para obter instruções detalhadas, consulte [sincronização do Azure Active Directory Connect: configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="f1f78-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="f1f78-177">Códigos de geo</span><span class="sxs-lookup"><span data-stu-id="f1f78-177">Geo Codes</span></span>
<span data-ttu-id="f1f78-p117">Você pode usar os códigos de três letras para especificar o Geo na propriedade **PreferredDataLocation** . A tabela a seguir lista os códigos para o Geos disponíveis:</span><span class="sxs-lookup"><span data-stu-id="f1f78-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="f1f78-180">Geo</span><span class="sxs-lookup"><span data-stu-id="f1f78-180">Geo</span></span> |<span data-ttu-id="f1f78-181">Código</span><span class="sxs-lookup"><span data-stu-id="f1f78-181">Code</span></span> |
|---------|---------|
|<span data-ttu-id="f1f78-182">Ásia/Pacífico</span><span class="sxs-lookup"><span data-stu-id="f1f78-182">Asia/Pacific</span></span> |<span data-ttu-id="f1f78-183">APC</span><span class="sxs-lookup"><span data-stu-id="f1f78-183">APC</span></span> |
|<span data-ttu-id="f1f78-184">Austrália</span><span class="sxs-lookup"><span data-stu-id="f1f78-184">Australia</span></span> |<span data-ttu-id="f1f78-185">AUS</span><span class="sxs-lookup"><span data-stu-id="f1f78-185">AUS</span></span> |
|<span data-ttu-id="f1f78-186">Canadá</span><span class="sxs-lookup"><span data-stu-id="f1f78-186">Canada</span></span> |<span data-ttu-id="f1f78-187">CAN</span><span class="sxs-lookup"><span data-stu-id="f1f78-187">CAN</span></span> |
|<span data-ttu-id="f1f78-188">União Europeia</span><span class="sxs-lookup"><span data-stu-id="f1f78-188">European Union</span></span> |<span data-ttu-id="f1f78-189">EUR</span><span class="sxs-lookup"><span data-stu-id="f1f78-189">EUR</span></span> |
|<span data-ttu-id="f1f78-190">França</span><span class="sxs-lookup"><span data-stu-id="f1f78-190">France</span></span> |<span data-ttu-id="f1f78-191">FRA</span><span class="sxs-lookup"><span data-stu-id="f1f78-191">FRA</span></span>|
|<span data-ttu-id="f1f78-192">Índia</span><span class="sxs-lookup"><span data-stu-id="f1f78-192">India</span></span> |<span data-ttu-id="f1f78-193">IND</span><span class="sxs-lookup"><span data-stu-id="f1f78-193">IND</span></span> |
|<span data-ttu-id="f1f78-194">Japão</span><span class="sxs-lookup"><span data-stu-id="f1f78-194">Japan</span></span> |<span data-ttu-id="f1f78-195">JPN</span><span class="sxs-lookup"><span data-stu-id="f1f78-195">JPN</span></span> |
|<span data-ttu-id="f1f78-196">Coreia</span><span class="sxs-lookup"><span data-stu-id="f1f78-196">Korea</span></span> |<span data-ttu-id="f1f78-197">KOR</span><span class="sxs-lookup"><span data-stu-id="f1f78-197">KOR</span></span> |
|<span data-ttu-id="f1f78-198">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="f1f78-198">United Kingdom</span></span> |<span data-ttu-id="f1f78-199">GBR</span><span class="sxs-lookup"><span data-stu-id="f1f78-199">GBR</span></span> |
|<span data-ttu-id="f1f78-200">Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="f1f78-200">United States</span></span> |<span data-ttu-id="f1f78-201">NAM</span><span class="sxs-lookup"><span data-stu-id="f1f78-201">NAM</span></span> |

<span data-ttu-id="f1f78-p118">**Observação**: as propriedades **PreferredDataLocation** e **MailboxRegion** são cadeias de caracteres com nenhuma verificação de erro. Se você inserir um valor inválido (por exemplo, NAN) a caixa de correio será colocada no Geo padrão.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="f1f78-204">Exibir o Geos disponíveis que estão configurados em sua organização do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f1f78-204">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="f1f78-205">Para ver a lista de Geos configurado em sua organização do Exchange Online, execute o seguinte comando no Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f1f78-205">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="f1f78-206">A saída do comando será parecida com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f1f78-206">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="f1f78-207">Modo de exibição padrão Geo para sua organização do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f1f78-207">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="f1f78-208">Para exibir o geo padrão da sua organização do Exchange Online, execute o seguinte comando no Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f1f78-208">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="f1f78-209">A saída do comando será parecida com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f1f78-209">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="f1f78-210">Encontrar o local de Geo de uma caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f1f78-210">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="f1f78-211">O cmdlet **Get-Mailbox** no Exchange Online PowerShell exibirá as seguintes propriedades relacionadas ao Geo em caixas de correio:</span><span class="sxs-lookup"><span data-stu-id="f1f78-211">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="f1f78-p119">**Banco de dados**: as primeiro 3 letras do nome do banco de dados correspondem ao código de Geo, que informa onde a caixa de correio está localizada no momento. Caixas de correio de arquivo morto Online o **ArchiveDatabase** propriedade deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="f1f78-214">**MailboxRegion**: Especifica o código de Geo que foi definido para o administrador (sincronizado a partir **PreferredDataLocation** no Azure AD).</span><span class="sxs-lookup"><span data-stu-id="f1f78-214">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="f1f78-215">**MailboxRegionLastUpdateTime**: indica quando MailboxRegion última atualização (automática ou manualmente).</span><span class="sxs-lookup"><span data-stu-id="f1f78-215">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="f1f78-216">Para ver essas propriedades para uma caixa de correio, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="f1f78-216">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="f1f78-217">Por exemplo, para ver as informações de localização geográfica para chris@contoso.onmicrosoft.com a caixa de correio, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1f78-217">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="f1f78-218">A saída do comando será parecida com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f1f78-218">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="f1f78-219">**Observação:** Se o código Geo no nome do banco de dados não coincidir com o valor de **MailboxRegion** , a caixa de correio será automaticamente ser colocado em uma fila de realocação e movidos para o Geo especificado pelo valor **MailboxRegion** (Exchange Online parecidas uma incompatibilidade entre essas valores de propriedade).</span><span class="sxs-lookup"><span data-stu-id="f1f78-219">**Note:** If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="f1f78-220">Mover uma caixa de correio somente em nuvem existente para um Geo específico</span><span class="sxs-lookup"><span data-stu-id="f1f78-220">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="f1f78-p120">Um usuário somente na nuvem é um usuário não sincronizadas para o inquilino via AAD se conectar. Este usuário foi criado diretamente no Azure AD. Use os cmdlets **Get-MsolUser** e **Set-MsolUser** no módulo Azure AD para Windows PowerShell para exibir ou especificar o Geo onde será armazenada caixa de correio do usuário somente na nuvem.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="f1f78-224">Para exibir o valor de **PreferredDataLocation** para um usuário, use esta sintaxe no Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f1f78-224">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="f1f78-225">Por exemplo, para ver o valor de **PreferredDataLocation** para michelle@contoso.onmicrosoft.com o usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1f78-225">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="f1f78-226">A saída do comando será parecida com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f1f78-226">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="f1f78-227">Para modificar o valor de **PreferredDataLocation** para um objeto de usuário somente na nuvem, use a seguinte sintaxe no Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f1f78-227">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="f1f78-228">Por exemplo, para definir o valor de **PreferredDataLocation** como geo a União Europeia (EUR) para michelle@contoso.onmicrosoft.com o usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1f78-228">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="f1f78-229">**Observações**:</span><span class="sxs-lookup"><span data-stu-id="f1f78-229">**Notes**:</span></span>

- <span data-ttu-id="f1f78-p121">Como mencionado anteriormente você não pode usar este procedimento para objetos de usuário sincronizado do Active Directory no local. Você precisa alterar o valor de **PreferredDataLocation** usando AAD se conectar. Para obter mais informações, consulte [sincronização do Azure Active Directory Connect: configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="f1f78-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="f1f78-233">Quanto tempo levará para realocar um mailboxfrom que seu geo atual para o novo geo desejada depende de vários fatores:</span><span class="sxs-lookup"><span data-stu-id="f1f78-233">How long it takes to relocate a mailboxfrom its current geo to the new desired geo depends on several factors:</span></span>
 
  - <span data-ttu-id="f1f78-234">O tamanho e o tipo de caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="f1f78-234">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="f1f78-235">O número de caixas de correio sendo movido.</span><span class="sxs-lookup"><span data-stu-id="f1f78-235">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="f1f78-236">A disponibilidade dos recursos de movimentação.</span><span class="sxs-lookup"><span data-stu-id="f1f78-236">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="f1f78-237">Move desabilitado caixas de correio que estão na retenção de litígio</span><span class="sxs-lookup"><span data-stu-id="f1f78-237">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="f1f78-p122">Desabilitado caixas de correio em retenção de litígio que são preservadas para eDiscovery fins não podem ser movidos, alterando seu valor **PreferredDataLocation** em seu estado desabilitado. Para mover uma caixa de correio desabilitada em suspensão de litígio:</span><span class="sxs-lookup"><span data-stu-id="f1f78-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="f1f78-240">Atribua temporariamente uma licença à caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="f1f78-240">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="f1f78-241">Altere o **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="f1f78-241">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="f1f78-242">Remova a licença da caixa de correio depois que ela foi movida para a localização geográfica selecionada para colocá-lo novamente em estado desativado.</span><span class="sxs-lookup"><span data-stu-id="f1f78-242">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="f1f78-243">Criar novas caixas de correio da nuvem em um Geo específico</span><span class="sxs-lookup"><span data-stu-id="f1f78-243">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="f1f78-244">Para criar uma nova caixa de correio em um Geo específico, você precisará fazer qualquer uma dessas etapas:</span><span class="sxs-lookup"><span data-stu-id="f1f78-244">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="f1f78-p123">Configure o valor de **PreferredDataLocation** , conforme descrito no anterior seção *antes da* que caixa de correio é criada no Exchange Online. Por exemplo, configure o valor de **PreferredDataLocation** em um usuário antes de atribuir uma licença.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="f1f78-247">Atribua uma licença ao mesmo tempo em que você definir o valor de **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="f1f78-247">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="f1f78-248">Para criar um novo somente em nuvem licenciado usuário (não AAD conectar sincronizados) em um Geo específico, use a seguinte sintaxe no Windows Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f1f78-248">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="f1f78-249">Este exemplo cria uma nova conta de usuário para Elizabeth Brunner com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="f1f78-249">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="f1f78-250">Nome principal do usuário: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="f1f78-250">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="f1f78-251">Nome: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="f1f78-251">First name: Elizabeth</span></span>

- <span data-ttu-id="f1f78-252">Sobrenome: Brunner</span><span class="sxs-lookup"><span data-stu-id="f1f78-252">Last name: Brunner</span></span>

- <span data-ttu-id="f1f78-253">Nome para exibição Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="f1f78-253">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="f1f78-254">Senha: gerada aleatoriamente e mostra os resultados do comando (porque não estamos usando o parâmetro *Password* )</span><span class="sxs-lookup"><span data-stu-id="f1f78-254">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="f1f78-255">Licença: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="f1f78-255">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="f1f78-256">Local: Austrália (Austrália)</span><span class="sxs-lookup"><span data-stu-id="f1f78-256">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="f1f78-257">Para obter mais informações sobre como criar novas contas de usuário e Localizando LicenseAssignment valores no PowerShell do Windows Azure AD, consulte [criar contas de usuário com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [Exibir as licenças e serviços com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="f1f78-257">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="f1f78-p124">**Observação:** Se você estiver usando o PowerShell do Exchange Online para habilitar uma caixa de correio e precisam ser criados diretamente a Geo especificado em **PreferredDataLocation**a caixa de correio, você precisará usar um cmdlet do Exchange Online como **Enable-Mailbox** ou **New-Mailbox **diretamente em relação ao serviço de nuvem. Se você usar o cmdlet **Enable-RemoteMailbox** local Exchange, a caixa de correio será criada no Geo padrão.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="f1f78-260">Existente onboard local caixas de correio de um específico Geo</span><span class="sxs-lookup"><span data-stu-id="f1f78-260">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="f1f78-261">Você pode usar as ferramentas de inclusão standard e processos para migrar uma caixa de correio de uma organização do Exchange no local para o Exchange Online, incluindo o [Painel de migração no EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e o cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) no Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1f78-261">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="f1f78-p125">A primeira etapa é verificar se que existe um objeto de usuário para cada caixa de correio a ser onboarded e verifique se que o valor de **PreferredDataLocation** correto está configurado no Azure AD. As ferramentas de inclusão respeitam o valor de **PreferredDataLocation** e irá migrar as caixas de correio diretamente para o Geo especificado.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="f1f78-264">Ou então, você pode usar as seguintes etapas para caixas de correio onboard diretamente em um Geo específico usando o cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) no PowerShell do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f1f78-264">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="f1f78-p126">Verifique se que o objeto de usuário existe para cada caixa de correio a ser onboarded e que o **PreferredDataLocation** está definido como o valor desejado no Azure AD. O valor de **PreferredDataLocation** será sincronizado com o atributo **MailboxRegion** do objeto de usuário de email correspondente no Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="f1f78-267">Conecte-se diretamente para o satélite específico Geo usando as instruções de conexão do anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="f1f78-267">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="f1f78-268">No PowerShell do Exchange Online, armazene as credenciais de administrador local que é usada para executar uma migração de caixa de correio em uma variável executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1f78-268">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="f1f78-269">No PowerShell do Exchange Online, crie um novo **New-MoveRequest** semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f1f78-269">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="f1f78-270">Repita a etapa #4 para cada caixa de correio que você precisa para migrar do Exchange local para o satélite Geo que você está conectado atualmente.</span><span class="sxs-lookup"><span data-stu-id="f1f78-270">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="f1f78-271">Se você precisar migrar caixas de correio adicionais para um satélite diferente Geo, repita as etapas 2 a 4 para cada Geo de satélite específico.</span><span class="sxs-lookup"><span data-stu-id="f1f78-271">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="f1f78-272">Relatórios de multi-Geo</span><span class="sxs-lookup"><span data-stu-id="f1f78-272">Multi-Geo Reporting</span></span>
<span data-ttu-id="f1f78-p127">**Relatórios de uso de Multi-Geo** no Centro de administração do Office 365 exibe a contagem de usuários por Geo. O relatório exibe a distribuição dos usuários para o mês atual e fornece dados históricos para os últimos seis meses.</span><span class="sxs-lookup"><span data-stu-id="f1f78-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
