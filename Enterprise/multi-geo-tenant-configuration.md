---
title: Configuração de um locatário do Office 365 multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
ms.custom: ''
localization_priority: Priority
description: Saiba como configurar o Office 365 multigeográfico.
ms.openlocfilehash: 8e845a7d1c3a8d83189a77c5fc7a6e8d3358a425
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076385"
---
# <a name="office-365-multi-geo-tenant-configuration"></a><span data-ttu-id="5fecb-103">Configuração de um locatário do Office 365 multigeográfico</span><span class="sxs-lookup"><span data-stu-id="5fecb-103">Office 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="5fecb-104">Antes de configurar seu locatário do Office 365 multigeográfico, certifique-se de que você leu o [Plano para o Office 365 multigeográfico](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="5fecb-104">Before you configure your tenant for Office 365 Multi-Geo, be sure you have read [Plan for Office 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="5fecb-105">Para seguir as etapas neste artigo, você precisará de uma lista de localizações geográficas que você deseja habilitar como locais de satélite e os usuários de teste que você deseja provisionar para esses locais.</span><span class="sxs-lookup"><span data-stu-id="5fecb-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="5fecb-106">Adicionar recursos multigeográficos no plano do Office 365 para seu locatário</span><span class="sxs-lookup"><span data-stu-id="5fecb-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="5fecb-107">Para usar o Office 365 multigeográfico, é necessário o plano _Funcionalidades Multigeográficas no Office 365_.</span><span class="sxs-lookup"><span data-stu-id="5fecb-107">To use Office 365 Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan.</span></span> <span data-ttu-id="5fecb-108">Trabalhar com sua equipe de conta para adicionar este plano para seu locatário.</span><span class="sxs-lookup"><span data-stu-id="5fecb-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="5fecb-109">Sua equipe de conectará você com o especialista de licenciamento apropriado e fará a configuração do seu locatário.</span><span class="sxs-lookup"><span data-stu-id="5fecb-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="5fecb-p103">Observe que o plano de _Funcionalidades Multigeográficas no Office 365_ é um plano de serviços de nível de usuário. Você precisa de uma licença para cada usuário que deseja hospedar em um local de satélite. Você pode adicionar mais licenças ao longo do tempo ao adicionar usuários em locais de satélite.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="5fecb-113">Depois que o locatário for provisionado com o plano  _Funcionalidades Multigeográficas no Office 365_, a guia **Localizaões geográficas** será disponibilizada no OneDrive e no Centro de administração do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5fecb-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="5fecb-114">Adicionar locais de satélites ao seu locatário</span><span class="sxs-lookup"><span data-stu-id="5fecb-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="5fecb-115">Você deve adicionar um local de satélite para cada localização geográfica onde você deseja armazenar dados.</span><span class="sxs-lookup"><span data-stu-id="5fecb-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="5fecb-116">As localizações geográficas disponíveis são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="5fecb-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Captura de tela da página de localizações geográficas do centro de administração do SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="5fecb-118">Para adicionar um local de satélite</span><span class="sxs-lookup"><span data-stu-id="5fecb-118">To add a satellite location</span></span>

1. <span data-ttu-id="5fecb-119">Abra o Centro de Administração do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5fecb-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="5fecb-120">Navegue até a guia **Localizações geográficas**.</span><span class="sxs-lookup"><span data-stu-id="5fecb-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="5fecb-121">Clique em **Adicionar local**.</span><span class="sxs-lookup"><span data-stu-id="5fecb-121">Click **Add location**.</span></span>

4. <span data-ttu-id="5fecb-122">Selecione o local que você deseja adicionar e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5fecb-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="5fecb-123">Digite o domínio que você deseja usar com a localização geográfica e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="5fecb-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="5fecb-124">Clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="5fecb-124">Click **Close**.</span></span>

<span data-ttu-id="5fecb-p105">O provisionamento pode levar desde algumas horas até 72 horas, dependendo do tamanho de seu locatário. Depois que o provisionamento de uma localização satélite for concluído, você receberá um email de confirmação. Quando o novo local geográfico for exibido em azul no mapa na guia **Localizações geográficas** no Centro de administração do OneDrive, você poderá definir o local preferencial de dados dos usuários como essa localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="5fecb-p106">A nova localização satélite será definida com configurações padrão. Isso permitirá configurar a localização satélite de acordo com suas necessidades locais de conformidade.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="5fecb-130">Defina o local de dados preferencial dos usuários</span><span class="sxs-lookup"><span data-stu-id="5fecb-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="5fecb-p107">Depois de habilitar as localizações satélites necessárias, você pode atualizar as contas de usuários para usar o local de dados de sua preferência. É recomendável definir um local preferencial de dados para todos os usuários, mesmo que o usuário permaneça no local de dados central.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fecb-133">Se o local de dados preferencial do usuário for definido em um local que não foi configurado como um local de satélite ou um local central, o sistema adotará como padrão o local central ao provisionar sites do OneDrive e do SharePoint e caixas de correio de Grupo.</span><span class="sxs-lookup"><span data-stu-id="5fecb-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="5fecb-134">É recomendável começar validações com um usuário de teste ou um pequeno grupo de usuários antes de implantar Funcionalidades Multigeográficas em sua organização de forma mais ampla.</span><span class="sxs-lookup"><span data-stu-id="5fecb-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="5fecb-135">Há dois tipos de objetos de usuário no Azure Active Directory: usuários somente nuvem e usuários sincronizados.</span><span class="sxs-lookup"><span data-stu-id="5fecb-135">In Azure Active Directory there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="5fecb-136">Siga as instruções apropriadas para o seu tipo de usuário.</span><span class="sxs-lookup"><span data-stu-id="5fecb-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a><span data-ttu-id="5fecb-137">Sincronizar o local de dados preferencial do usuário usando o Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="5fecb-137">Synchronize user's Preferred Data Location using Azure Active Directory Connect</span></span> 

<span data-ttu-id="5fecb-p109">Se os usuários da empresa são sincronizados de um sistema local do AD (Active Directory) ao AAD (Azure Active Directory), o PreferredDataLocation deve ser preenchido no AD e sincronizado com o AAD. Siga o processo em [Sincronização do Azure AD Connect: configurar o local preferencial de dados para recursos do Office 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) para configurar a sincronização do local preferencial de dados do Active Directory local com o Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="5fecb-140">Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="5fecb-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fecb-141">Para novos usuários sem o OneDrive provisionado, aguarde pelo menos de 24 horas após o PDL do usuário ser sincronizado com o Azure Active Directory para que as alterações se propaguem antes de fazer logon no OneDrive for Business.</span><span class="sxs-lookup"><span data-stu-id="5fecb-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="5fecb-142">(Configurar o Local de Dados Preferencial antes do usuário fazer o logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)</span><span class="sxs-lookup"><span data-stu-id="5fecb-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="5fecb-143">Configurar Local de Dados Preferencial para usuários somente na nuvem</span><span class="sxs-lookup"><span data-stu-id="5fecb-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="5fecb-144">Se os usuários da empresa não estiverem sincronizados a partir de um sistema do Active Directory local para o Azure Active Directory, o que significa que são criados no Office 365 ou no Azure Active Directory, o PDL deverá ser definido usando o PowerShell do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5fecb-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Office 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="5fecb-p111">Os procedimentos desta seção exigem o [Módulo do Microsoft Azure Active Directory para o Módulo do Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se você já tiver instalado o PowerShell do Azure Active Directory, não se esqueça de atualizar para a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="5fecb-147">Abra o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fecb-147">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="5fecb-148">Execute o `Connect-MsolService` e insira as credenciais de administrador global do locatário.</span><span class="sxs-lookup"><span data-stu-id="5fecb-148">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="5fecb-p112">Use o cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) para definir o local preferencial de dados para cada um dos usuários. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5fecb-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="5fecb-p113">Você pode confirmar se o local preferencial de dados foi atualizado corretamente usando o cmdlet Get-MsolUser. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5fecb-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Captura de tela de uma janela do PowerShell mostrando o conjunto-msoluser](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="5fecb-154">Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="5fecb-154">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fecb-155">Para novos usuários sem o OneDrive provisionado, aguarde pelo menos de 24 horas após o PDL ser feito para que as alterações se propaguem antes de fazer logon no OneDrive.</span><span class="sxs-lookup"><span data-stu-id="5fecb-155">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="5fecb-156">(Configurar o Local de Dados Preferencial antes do usuário fazer o logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)</span><span class="sxs-lookup"><span data-stu-id="5fecb-156">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="5fecb-157">Provisionamento do OneNote e efeito de PDL</span><span class="sxs-lookup"><span data-stu-id="5fecb-157">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="5fecb-158">Se o usuário já tiver um site do OneDrive criado no locatário, configurar o PDL não moverá automaticamente o OneDrive existente.</span><span class="sxs-lookup"><span data-stu-id="5fecb-158">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="5fecb-159">Para mover o OneDrive de um usuário, confira [Movimentação Geográfica do OneDrive for Business](move-onedrive-between-geo-locations.md) siga as instruções em Mover o OneDrive entre localizações geográfica.</span><span class="sxs-lookup"><span data-stu-id="5fecb-159">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="5fecb-160">(Observe que a caixa de correio do Exchange do usuário não move automaticamente quando ao definir o PDL do usuário.)</span><span class="sxs-lookup"><span data-stu-id="5fecb-160">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="5fecb-161">Se o usuário não tiver um site do OneDrive no locatário, o OneDrive será provisionado para ele de acordo com o valor do PDL, supondo que o PDL do usuário corresponda a um dos locais de satélites da empresa.</span><span class="sxs-lookup"><span data-stu-id="5fecb-161">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="5fecb-162">Configurar pesquisa multigeográfica</span><span class="sxs-lookup"><span data-stu-id="5fecb-162">Configuring Multi-Geo search</span></span>

<span data-ttu-id="5fecb-163">O locatário com Funcionalidades Multigeográficas terá recursos de pesquisa agregados, permitindo que uma consulta de pesquisa retorne resultados de praticamente qualquer lugar no locatário.</span><span class="sxs-lookup"><span data-stu-id="5fecb-163">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="5fecb-164">Por padrão, pesquisas desses pontos de entrada retornam resultados agregados, mesmo que cada índice de pesquisa esteja em sua localização geográfica relevante:</span><span class="sxs-lookup"><span data-stu-id="5fecb-164">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="5fecb-165">OneDrive for business</span><span class="sxs-lookup"><span data-stu-id="5fecb-165">OneDrive for business</span></span>

- <span data-ttu-id="5fecb-166">Delve</span><span class="sxs-lookup"><span data-stu-id="5fecb-166">Delve</span></span>

- <span data-ttu-id="5fecb-167">Página inicial do SharePoint</span><span class="sxs-lookup"><span data-stu-id="5fecb-167">SharePoint Home</span></span>

- <span data-ttu-id="5fecb-168">Centro de Pesquisa</span><span class="sxs-lookup"><span data-stu-id="5fecb-168">Search Center</span></span>

<span data-ttu-id="5fecb-169">Além disso, recursos de pesquisa multigeográfica podem ser configurados para os aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5fecb-169">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="5fecb-170">Examine [Configurar a pesquisa para o OneDrive for Business com a funcionalidade multigeográfica](configure-search-for-multi-geo.md) para obter instruções, incluindo limitações e diferenças.</span><span class="sxs-lookup"><span data-stu-id="5fecb-170">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-office-365-multi-geo-configuration"></a><span data-ttu-id="5fecb-171">Validar a configuração do Office 365 multigeográfico</span><span class="sxs-lookup"><span data-stu-id="5fecb-171">Validating the Office 365 Multi-Geo configuration</span></span>

<span data-ttu-id="5fecb-172">Veja a seguir alguns casos de uso básico que você pode incluir em seu plano de validação antes de implementar o Office 365 multigeográficolargamente em sua empresa.</span><span class="sxs-lookup"><span data-stu-id="5fecb-172">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Office 365 Multi-Geo to your company.</span></span> <span data-ttu-id="5fecb-173">Depois de concluir esses testes e os casos de uso mais relevantes para sua empresa, você pode optar por prosseguir e adicionar os usuários em seu grupo piloto inicial.</span><span class="sxs-lookup"><span data-stu-id="5fecb-173">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="5fecb-174">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="5fecb-174">**OneDrive for Business**</span></span>

<span data-ttu-id="5fecb-175">Selecione o OneDrive no inicializador de aplicativos do Office 365 e confirme que você será direcionado automaticamente para a localização geográfica apropriada do usuário com base no PDL do usuário.</span><span class="sxs-lookup"><span data-stu-id="5fecb-175">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="5fecb-176">OneDrive for Business agora vai começar a provisionar nesse local.</span><span class="sxs-lookup"><span data-stu-id="5fecb-176">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="5fecb-177">Uma vez provisionado, tente carregar e baixar alguns documentos.</span><span class="sxs-lookup"><span data-stu-id="5fecb-177">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="5fecb-178">**Aplicativo móvel do OneDrive**</span><span class="sxs-lookup"><span data-stu-id="5fecb-178">**OneDrive Mobile App**</span></span>

<span data-ttu-id="5fecb-p118">Faça logon no aplicativo móvel do OneDrive com suas credenciais de conta de teste. Confirme se você pode ver os arquivos do OneDrive for Business e se pode interagir com eles no dispositivo móvel.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="5fecb-181">**Cliente de sincronização do OneDrive**</span><span class="sxs-lookup"><span data-stu-id="5fecb-181">**OneDrive sync client**</span></span>

<span data-ttu-id="5fecb-p119">Confirme que o cliente de sincronização do OneDrive detecta automaticamente a localização geográfica do OneDrive for Business após o logon. Se você precisar baixar o cliente de sincronização, clique em **Sincronização** na biblioteca do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="5fecb-184">**Aplicativos do Office**</span><span class="sxs-lookup"><span data-stu-id="5fecb-184">**Office applications**</span></span>

<span data-ttu-id="5fecb-p120">Confirme que você pode acessar o OneDrive for Business fazendo logon de um aplicativo do Office, como o Word. Abra o aplicativo do Office e selecione "OneDrive – <TenantName>". O Office detectará o local do OneDrive e mostrará os arquivos que você pode abrir.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="5fecb-188">**Compartilhamento**</span><span class="sxs-lookup"><span data-stu-id="5fecb-188">**Sharing**</span></span>

<span data-ttu-id="5fecb-p121">Tente compartilhar arquivos do OneDrive. Confirme se o seletor de pessoas mostra todos os usuários online do SharePoint, independentemente da localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="5fecb-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
