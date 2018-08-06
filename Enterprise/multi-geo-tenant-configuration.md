---
title: Configuração de locatário multigeográfico do Onedrive for Business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Saiba como configurar o OneDrive for Business com a funcionalidade multigeográfica.
ms.openlocfilehash: 561025efc38199f3a92e228d5414a28df6eb12f0
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2018
ms.locfileid: "21549962"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="5403d-103">Configuração de locatário multigeográfico do Onedrive for Business</span><span class="sxs-lookup"><span data-stu-id="5403d-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="5403d-p101">Antes de configurar o locatário para o OneDrive for Business com a funcionalidade multigeográfica, leia [Plano do OneDrive for Business com a funcionalidade multigeográfica](plan-for-multi-geo.md). Para seguir as etapas deste artigo, você precisará de uma lista de locais que deseja habilitar e os usuários de teste que deseja provisionar para esses locais.</span><span class="sxs-lookup"><span data-stu-id="5403d-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="5403d-106">Adicionar recursos multigeográficos no plano do Office 365 para seu locatário</span><span class="sxs-lookup"><span data-stu-id="5403d-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="5403d-p102">Para usar o OneDrive for Business com Funcionalidades Multigeográficas, é necessário o plano _Funcionalidades Multigeográficas no Office 365_. Trabalhe com sua equipe de conta para adicionar esse plano ao locatário. A equipe de conta conectará você ao especialista em licenciamento apropriado e configurará o locatário.</span><span class="sxs-lookup"><span data-stu-id="5403d-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="5403d-p103">Observe que o plano de _Funcionalidades Multigeográficas no Office 365_ é um plano de serviços de nível de usuário. Você precisa de uma licença para cada usuário que deseja hospedar em um local de satélite. Você pode adicionar mais licenças ao longo do tempo ao adicionar usuários em locais de satélite.</span><span class="sxs-lookup"><span data-stu-id="5403d-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="5403d-113">Depois que o locatário for provisionado com o plano _Funcionalidades Multigeográficas no Office 365_, a guia **Locais geográficos** será disponibilizada na [Centro de administração do OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="5403d-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="5403d-114">Defina Locais de Dados Permitidos (ADL) para seu locatário</span><span class="sxs-lookup"><span data-stu-id="5403d-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="5403d-p104">Você deve definir um Local de Dados Permitido para o SharePoint para cada localização geográfica onde deseja usar o OneDrive for Business. As localizações geográficas disponíveis são mostradas na seguinte tabela:</span><span class="sxs-lookup"><span data-stu-id="5403d-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5403d-117"><strong>Localização</strong></span><span class="sxs-lookup"><span data-stu-id="5403d-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="5403d-118"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="5403d-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5403d-119">Ásia – Pacífico</span><span class="sxs-lookup"><span data-stu-id="5403d-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="5403d-120">APC</span><span class="sxs-lookup"><span data-stu-id="5403d-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5403d-121">Austrália</span><span class="sxs-lookup"><span data-stu-id="5403d-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="5403d-122">AUS</span><span class="sxs-lookup"><span data-stu-id="5403d-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5403d-123">Canadá</span><span class="sxs-lookup"><span data-stu-id="5403d-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="5403d-124">CAN</span><span class="sxs-lookup"><span data-stu-id="5403d-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5403d-125">Europa/Oriente Médio/África</span><span class="sxs-lookup"><span data-stu-id="5403d-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="5403d-126">EUR</span><span class="sxs-lookup"><span data-stu-id="5403d-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5403d-127">França</span><span class="sxs-lookup"><span data-stu-id="5403d-127">France</span></span></td>
<td align="left"><span data-ttu-id="5403d-128">FRA</span><span class="sxs-lookup"><span data-stu-id="5403d-128">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5403d-129">Japão</span><span class="sxs-lookup"><span data-stu-id="5403d-129">Japan</span></span></td>
<td align="left"><span data-ttu-id="5403d-130">JPN</span><span class="sxs-lookup"><span data-stu-id="5403d-130">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5403d-131">Coreia</span><span class="sxs-lookup"><span data-stu-id="5403d-131">Korea</span></span></td>
<td align="left"><span data-ttu-id="5403d-132">KOR</span><span class="sxs-lookup"><span data-stu-id="5403d-132">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5403d-133">América do Norte</span><span class="sxs-lookup"><span data-stu-id="5403d-133">North America</span></span></td>
<td align="left"><span data-ttu-id="5403d-134">NAM</span><span class="sxs-lookup"><span data-stu-id="5403d-134">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5403d-135">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="5403d-135">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="5403d-136">GBR</span><span class="sxs-lookup"><span data-stu-id="5403d-136">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="5403d-137">Para adicionar um local geográfico de satélite</span><span class="sxs-lookup"><span data-stu-id="5403d-137">To add a satellite geo location</span></span>

1. <span data-ttu-id="5403d-138">Abra o [Centro de administração do OneDrive](https://admin.onedrive.com)</span><span class="sxs-lookup"><span data-stu-id="5403d-138">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="5403d-139">Navegue até a guia **Localizações geográficas**.</span><span class="sxs-lookup"><span data-stu-id="5403d-139">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="5403d-140">Clique em **Adicionar local**.</span><span class="sxs-lookup"><span data-stu-id="5403d-140">Click **Add location**.</span></span>

4. <span data-ttu-id="5403d-141">Selecione o local que você deseja adicionar e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5403d-141">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="5403d-142">Digite o domínio que você deseja usar com a localização geográfica e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="5403d-142">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="5403d-143">Clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="5403d-143">Click **Close**.</span></span>

<span data-ttu-id="5403d-p105">O provisionamento pode levar desde algumas horas até 72 horas, dependendo do tamanho do locatário. Depois que o provisionamento de um local de satélite for concluído, você receberá um email de confirmação. Quando o novo local geográfico for exibido em azul no mapa na guia **Localizações geográficas** no Centro de administração do OneDrive, você poderá definir o local preferencial de dados dos usuários como essa localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="5403d-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="5403d-p106">A nova localização geográfica de satélite será definida com configurações padrão. Isso permitirá configurar a localização geográfica de acordo com suas necessidades de conformidade local.</span><span class="sxs-lookup"><span data-stu-id="5403d-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="5403d-149">Definir o local der dados preferencial dos usuários</span><span class="sxs-lookup"><span data-stu-id="5403d-149">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="5403d-p107">Depois de habilitar as localizações de dados necessárias, você pode atualizar as contas de usuário para usar o local de dados apropriado. É recomendável definir um local preferencial de dados para todos os usuários, mesmo que o usuário permaneça no local de dados padrão.</span><span class="sxs-lookup"><span data-stu-id="5403d-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="5403d-152">É recomendável começar validações com um usuário de teste ou um pequeno grupo de usuários antes de implantar Funcionalidades Multigeográficas em sua organização mais ampla.</span><span class="sxs-lookup"><span data-stu-id="5403d-152">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="5403d-p108">Há dois tipos de objetos de usuário no AAD: usuários somente de nuvem e usuários sincronizados. Siga as instruções apropriadas para o tipo de usuário.</span><span class="sxs-lookup"><span data-stu-id="5403d-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="5403d-155">Sincronizar o local de dados preferencial do usuário usando o AD Connect</span><span class="sxs-lookup"><span data-stu-id="5403d-155">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="5403d-p109">Se os usuários da empresa são sincronizados com um sistema do AD (Active Directory) no local ao AAD (Azure Active Directory), PreferredDataLocation deve ser populado no AD e sincronizado com o AAD. Siga o processo em [Sincronização do Azure AD Connect: fazer uma alteração na configuração padrão](https://docs.microsoft.com/pt-BR/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) para configurar a sincronização de local preferencial de dados do AD local para o AAD.</span><span class="sxs-lookup"><span data-stu-id="5403d-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/pt-BR/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="5403d-158">Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="5403d-158">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5403d-p110">Para novos usuários sem o OneDrive provisionado, aguarde pelo menos 24 horas após o PDL do usuário ser sincronizado com o AAD para que as alterações se propaguem antes que o usuário faça logon no OneDrive for Business. (Configurar o local preferencial de dados antes que o usuário faça logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)</span><span class="sxs-lookup"><span data-stu-id="5403d-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="5403d-161">Configurar local de dados preferencial para usuários somente na nuvem</span><span class="sxs-lookup"><span data-stu-id="5403d-161">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="5403d-162">Se os usuários da empresa não estiverem sincronizados de um sistema do AD (Active Directory) local para o AAD (Azure Active Directory), ou seja, são criados no Office 365 ou no AAD, o PDL deverá ser definido usando o PowerShell do AAD.</span><span class="sxs-lookup"><span data-stu-id="5403d-162">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="5403d-p111">Os procedimentos desta seção exigem o [Módulo do Microsoft Azure Active Directory para o Módulo do Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se você já tiver instalado o PowerShell do AAD, atualize para a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="5403d-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="5403d-165">Abra o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5403d-165">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="5403d-166">Execute o `Connect-MsolService` e insira as credenciais de administrador global do locatário.</span><span class="sxs-lookup"><span data-stu-id="5403d-166">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="5403d-p112">Use o cmdlet [Set-MsolUser](https://docs.microsoft.com/pt-BR/powershell/msonline/v1/set-msoluser) para definir o local preferencial de dados para cada um dos usuários. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5403d-p112">Use the [Set-MsolUser](https://docs.microsoft.com/pt-BR/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="5403d-p113">Você pode confirmar se o local preferencial de dados foi atualizado corretamente usando o cmdlet Get-MsolUser. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5403d-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="5403d-171">Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="5403d-171">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5403d-p114">Para novos usuários sem o OneDrive provisionado, aguarde pelo menos 24 horas após o PDL do usuário ser definido para que as alterações se propaguem antes que o usuário faça logon no OneDrive do SharePoint. (Configurar o local preferencial de dados antes que o usuário faça logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)</span><span class="sxs-lookup"><span data-stu-id="5403d-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="5403d-174">Provisionamento do OneNote e efeito de PDL</span><span class="sxs-lookup"><span data-stu-id="5403d-174">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="5403d-p115">Se o usuário já tiver um site do OneDrive criado no locatário, configurar o PDL não moverá automaticamente o OneDrive existente. Para mover o OneDrive de um usuário, confira [Movimentação geográfica do OneDrive for Business](move-onedrive-between-geo-locations.md). Siga as instruções em Mover o OneDrive entre locais geográficos.</span><span class="sxs-lookup"><span data-stu-id="5403d-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="5403d-177">Se o usuário não tiver um site do OneDrive no locatário, o OneDrive será provisionado para ele de acordo com o valor de PDL, supondo que o PDL do usuário corresponda a um dos locais de dados permitidos (ADLs) da empresa.</span><span class="sxs-lookup"><span data-stu-id="5403d-177">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="5403d-178">Configurar pesquisa multigeográfica</span><span class="sxs-lookup"><span data-stu-id="5403d-178">Configuring Multi-Geo search</span></span>

<span data-ttu-id="5403d-179">O locatário com Funcionalidades Multigeográficas terá recursos de pesquisa agregados, permitindo que uma consulta de pesquisa retorne resultados de praticamente qualquer lugar no locatário.</span><span class="sxs-lookup"><span data-stu-id="5403d-179">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="5403d-180">Por padrão, pesquisas desses pontos de entrada retornam resultados agregados, mesmo que cada índice de pesquisa esteja em sua localização geográfica relevante:</span><span class="sxs-lookup"><span data-stu-id="5403d-180">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="5403d-181">OneDrive for business</span><span class="sxs-lookup"><span data-stu-id="5403d-181">OneDrive for business</span></span>

- <span data-ttu-id="5403d-182">Delve</span><span class="sxs-lookup"><span data-stu-id="5403d-182">Delve</span></span>

- <span data-ttu-id="5403d-183">Página inicial do SharePoint</span><span class="sxs-lookup"><span data-stu-id="5403d-183">SharePoint Home</span></span>

- <span data-ttu-id="5403d-184">Centro de Pesquisa</span><span class="sxs-lookup"><span data-stu-id="5403d-184">Search Center</span></span>

<span data-ttu-id="5403d-185">Além disso, recursos de pesquisa multigeográfica podem ser configurados para os aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5403d-185">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="5403d-186">Examine [Configurar a pesquisa para o OneDrive for Business com a funcionalidade multigeográfica](configure-search-for-multi-geo.md) para obter instruções, incluindo limitações e diferenças.</span><span class="sxs-lookup"><span data-stu-id="5403d-186">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="5403d-187">Validar a configuração multigeográfica do OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="5403d-187">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="5403d-p116">Veja a seguir alguns casos de uso básicos que convém incluir em seu plano de validação antes de implantar amplamente o OneDrive for Business com Funcionalidades Multigeográficas em sua empresa. Depois de concluir essas testes e os casos de uso mais relevantes para sua empresa, você pode optar por adicionar os usuários em seu grupo piloto inicial.</span><span class="sxs-lookup"><span data-stu-id="5403d-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="5403d-190">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="5403d-190">**OneDrive for Business**</span></span>

<span data-ttu-id="5403d-p117">Selecione o OneDrive por meio do inicializador de aplicativos do Office 365 e confirme se você será direcionado automaticamente para a localização geográfica apropriada do usuário, com base no PDL do usuário. O OneDrive for Business agora deve iniciar o provisionamento nesse local. Após o provisionamento, tente carregar e baixar alguns documentos.</span><span class="sxs-lookup"><span data-stu-id="5403d-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="5403d-194">**Aplicativo móvel do OneDrive**</span><span class="sxs-lookup"><span data-stu-id="5403d-194">**OneDrive Mobile App**</span></span>

<span data-ttu-id="5403d-p118">Faça logon no aplicativo móvel do OneDrive com suas credenciais de conta de teste. Confirme se você pode ver os arquivos do OneDrive for Business e se pode interagir com eles no dispositivo móvel.</span><span class="sxs-lookup"><span data-stu-id="5403d-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="5403d-197">**Cliente de sincronização do OneDrive**</span><span class="sxs-lookup"><span data-stu-id="5403d-197">**OneDrive sync client**</span></span>

<span data-ttu-id="5403d-p119">Confirme que o cliente de sincronização do OneDrive detecta automaticamente a localização geográfica do OneDrive for Business após o logon. Se você precisar baixar o cliente de sincronização, clique em **Sincronização** na biblioteca do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="5403d-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="5403d-200">**Aplicativos do Office**</span><span class="sxs-lookup"><span data-stu-id="5403d-200">**Office applications**</span></span>

<span data-ttu-id="5403d-p120">Confirme que você pode acessar o OneDrive for Business fazendo logon de um aplicativo do Office, como o Word. Abra o aplicativo do Office e selecione "OneDrive – <TenantName>". O Office detectará o local do OneDrive e mostrará os arquivos que você pode abrir.</span><span class="sxs-lookup"><span data-stu-id="5403d-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="5403d-204">**Compartilhamento**</span><span class="sxs-lookup"><span data-stu-id="5403d-204">**Sharing**</span></span>

<span data-ttu-id="5403d-p121">Tente compartilhar arquivos do OneDrive. Confirme se o seletor de pessoas mostra todos os usuários online do SharePoint, independentemente da localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="5403d-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
