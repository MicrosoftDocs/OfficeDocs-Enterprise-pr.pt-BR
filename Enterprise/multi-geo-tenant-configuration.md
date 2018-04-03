---
title: OneDrive para configuração do inquilino de negócios Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba como configurar o OneDrive for Business Multi-Geo.
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="ed508-103">OneDrive para configuração do inquilino de negócios Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="ed508-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="ed508-p101">Antes de configurar seu locatário do OneDrive for Business Multi-Geo, certifique-se de que você leu a [Planejar o OneDrive for Business Multi-Geo](plan-for-multi-geo.md). Para executar as etapas neste artigo, você precisará de uma lista de locais de que você deseja habilitar e os usuários de teste que você deseja provisionar para esses locais.</span><span class="sxs-lookup"><span data-stu-id="ed508-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="ed508-106">Adicionar as capacidades de Multi-Geo no plano do Office 365 para seu locatário</span><span class="sxs-lookup"><span data-stu-id="ed508-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="ed508-p102">Para usar o OneDrive for Business Multi-Geo, você precisa ter o plano de _Recursos de Multi-Geo no Office 365_ . Trabalhar com sua equipe de conta para adicionar a este plano de seu locatário. Sua equipe de conta será conectá-lo com a especialista em licenciamento apropriada e obtenha seu locatário configurado.</span><span class="sxs-lookup"><span data-stu-id="ed508-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="ed508-p103">Observe que o plano de _Recursos de Multi-Geo no Office 365_ é um plano de serviço de nível do usuário. Você precisa de uma licença para cada usuário que você deseja hospedar em um local de setellite. Você pode adicionar mais licenças ao longo do tempo à medida que você adiciona usuários nos locais de satélite.</span><span class="sxs-lookup"><span data-stu-id="ed508-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a setellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="ed508-113">Quando seu locatário tenha sido provisionado com o plano de _Recursos de Multi-Geo no Office 365_ , na guia **locais Geo** estará disponível no [Centro de administração do OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="ed508-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="ed508-114">Definir os locais de dados permitido (ADL) ao seu locatário</span><span class="sxs-lookup"><span data-stu-id="ed508-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="ed508-p104">Você deve definir o local dos dados uma permissão do SharePoint para cada localização geográfica onde você deseja usar o OneDrive for Business. Locais de geo disponíveis são mostradas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="ed508-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ed508-117"><strong>Local</strong></span><span class="sxs-lookup"><span data-stu-id="ed508-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="ed508-118"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="ed508-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ed508-119">América do Norte</span><span class="sxs-lookup"><span data-stu-id="ed508-119">North America</span></span></td>
<td align="left"><span data-ttu-id="ed508-120">NOME</span><span class="sxs-lookup"><span data-stu-id="ed508-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ed508-121">Europa / Oriente Médio / África</span><span class="sxs-lookup"><span data-stu-id="ed508-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="ed508-122">EUR</span><span class="sxs-lookup"><span data-stu-id="ed508-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ed508-123">Pacífico Asiático</span><span class="sxs-lookup"><span data-stu-id="ed508-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="ed508-124">APC</span><span class="sxs-lookup"><span data-stu-id="ed508-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ed508-125">Austrália</span><span class="sxs-lookup"><span data-stu-id="ed508-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="ed508-126">AUSTRÁLIA</span><span class="sxs-lookup"><span data-stu-id="ed508-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ed508-127">Japão</span><span class="sxs-lookup"><span data-stu-id="ed508-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="ed508-128">JAPONÊS</span><span class="sxs-lookup"><span data-stu-id="ed508-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ed508-129">Canadá</span><span class="sxs-lookup"><span data-stu-id="ed508-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="ed508-130">PODE</span><span class="sxs-lookup"><span data-stu-id="ed508-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ed508-131">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="ed508-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="ed508-132">GBR</span><span class="sxs-lookup"><span data-stu-id="ed508-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ed508-133">Coreia</span><span class="sxs-lookup"><span data-stu-id="ed508-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="ed508-134">KOR</span><span class="sxs-lookup"><span data-stu-id="ed508-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="ed508-135">Para adicionar um local de geo satélite</span><span class="sxs-lookup"><span data-stu-id="ed508-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="ed508-136">Abra o [Centro de administração do OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="ed508-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="ed508-137">Navegue até a guia **Geo locais** .</span><span class="sxs-lookup"><span data-stu-id="ed508-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="ed508-138">Clique em **Adicionar local**.</span><span class="sxs-lookup"><span data-stu-id="ed508-138">Click **Add location**.</span></span>

4. <span data-ttu-id="ed508-139">Selecione o local que você deseja adicionar e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="ed508-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="ed508-140">Digite o domínio que você deseja usar com o local de geo e, em seguida, clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ed508-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="ed508-141">Clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="ed508-141">Click **Close**.</span></span>

<span data-ttu-id="ed508-p105">Depois de concluído o provisionamento de um local de satélite, você receberá um email de confirmação. Quando o novo local de geo aparece em azul no mapa na guia **locais Geo** no Centro de administração do OneDrive, você poderá prosseguir para definir o local dos dados preferencial dos usuários ao geo-local.</span><span class="sxs-lookup"><span data-stu-id="ed508-p105">Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ed508-p106">Irá configurar seu novo local geo satélite com as configurações padrão. Isso permitirá que você configure esse local geo conforme apropriado para suas necessidades de conformidade de local.</span><span class="sxs-lookup"><span data-stu-id="ed508-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="ed508-146">A definição de local dos dados preferencial dos usuários</span><span class="sxs-lookup"><span data-stu-id="ed508-146">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="ed508-p107">Depois que você ativar os locais de dados necessários, você pode atualizar suas contas de usuário para usar o local apropriado aos dados. Recomendamos que você defina um local de dados preferida para cada usuário, mesmo se esse usuário permanecer no local de dados padrão.</span><span class="sxs-lookup"><span data-stu-id="ed508-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="ed508-149">Recomendamos que você comece validações com um usuário de teste ou de um pequeno grupo de usuários antes de implantá Multi-Geo recursos em sua organização ampla.</span><span class="sxs-lookup"><span data-stu-id="ed508-149">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="ed508-p108">AAD existem dois tipos de objetos de usuário: nuvem apenas usuários e sincronizados. Siga as instruções apropriadas para seu tipo de usuário.</span><span class="sxs-lookup"><span data-stu-id="ed508-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="ed508-152">Sincronizar o local do usuário preferencial dados usando o AD Connect</span><span class="sxs-lookup"><span data-stu-id="ed508-152">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="ed508-p109">Se os usuários da sua empresa são sincronizados a partir de um sistema do AD (Active Directory) no local para Windows Azure Active Directory (AAD), seu PreferredDataLocation deve ser preenchido no AD e sincronizada com AAD. Siga o processo em [sincronização do Azure Connect da AD: faça uma alteração na configuração padrão](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) configurar preferencial da sincronização local dos dados AD local para AAD.</span><span class="sxs-lookup"><span data-stu-id="ed508-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="ed508-155">Recomendamos que você inclua a definição de local dos dados preferencial do usuário como parte do seu fluxo de trabalho de criação de usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="ed508-155">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed508-p110">Para novos usuários com nenhum OneDrive provisionado, aguarde pelo menos 24 horas depois que PDL um usuário é sincronizado com o AAD para que as alterações sejam propagadas antes que o usuário fizer logon ao OneDrive for Business. (Os dados preferenciais a definição local antes que o usuário fizer logon para provisionar sua OneDrive for Business garante que OneDrive de novo do usuário será provisionado no local correto).</span><span class="sxs-lookup"><span data-stu-id="ed508-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="ed508-158">Configurando o local dos dados preferencial para nuvem somente os usuários</span><span class="sxs-lookup"><span data-stu-id="ed508-158">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="ed508-159">Se os usuários da sua empresa não serão sincronizados com um sistema de AD (Active Directory) no local para Windows Azure Active Directory (AAD), que significa que eles são criados no Office 365 ou AAD, em seguida, PDL deve ser definida usando o PowerShell AAD.</span><span class="sxs-lookup"><span data-stu-id="ed508-159">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="ed508-p111">Os procedimentos nesta seção exigem o [Microsoft Azure módulo Active Directory módulo para Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se você já tiver PowerShell AAD instalado, verifique se que você atualizar para a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="ed508-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="ed508-162">Abra o módulo do Microsoft Azure Active Directory para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed508-162">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="ed508-163">Execute `Connect-MsolService` e insira as credenciais de administrador global para seu locatário.</span><span class="sxs-lookup"><span data-stu-id="ed508-163">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="ed508-p112">Use o cmdlet [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) para definir o local de dados preferida para cada um dos seus usuários. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ed508-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="ed508-p113">Você pode verificar para confirmar que o local preferido de dados foi atualizado corretamente usando o cmdlet Get-MsolUser. Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ed508-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="ed508-168">Recomendamos que você inclua a definição de local dos dados preferencial do usuário como parte do seu fluxo de trabalho de criação de usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="ed508-168">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed508-p114">Para novos usuários com nenhum OneDrive provisionado, aguarde pelo menos 24 horas depois que PDL um usuário é definido para que as alterações sejam propagadas antes que o usuário fizer logon SharePoint OneDrive. (Os dados preferenciais a definição local antes que o usuário fizer logon para provisionar sua OneDrive for Business garante que OneDrive de novo do usuário será provisionado no local correto).</span><span class="sxs-lookup"><span data-stu-id="ed508-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="ed508-171">Provisionamento de OneDrive e o efeito da PDL</span><span class="sxs-lookup"><span data-stu-id="ed508-171">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="ed508-p115">Se o usuário já tem um site de OneDrive criado no locatário, definir sua PDL não moverá automaticamente sua OneDrive existente. Para mover OneDrive um usuário, consulte o [OneDrive for Business mover de Geo](move-onedrive-between-geo-locations.md) , siga as instruções no OneDrive movendo entre geo locais.</span><span class="sxs-lookup"><span data-stu-id="ed508-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="ed508-174">Se o usuário não tem um site de OneDrive dentro de locatário, OneDrive será provisionado para-los de acordo com o seu valor PDL, supondo que corresponde a um dos locais de dados permitidos da empresa (ADLs) PDL para o usuário.</span><span class="sxs-lookup"><span data-stu-id="ed508-174">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="ed508-175">Configurando a pesquisa de Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="ed508-175">Configuring Multi-Geo search</span></span>

<span data-ttu-id="ed508-176">Seu locatário Multi-Geo terão os recursos de pesquisa agregadas permitindo que uma consulta de pesquisa, para retornar resultados de qualquer lugar dentro do inquilino.</span><span class="sxs-lookup"><span data-stu-id="ed508-176">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="ed508-177">Por padrão, as pesquisas desses pontos de entrada retornará resultados agregados, embora cada índice de pesquisa está localizada dentro de sua localização geo relevantes:</span><span class="sxs-lookup"><span data-stu-id="ed508-177">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="ed508-178">OneDrive para business</span><span class="sxs-lookup"><span data-stu-id="ed508-178">OneDrive for business</span></span>

- <span data-ttu-id="ed508-179">Delve</span><span class="sxs-lookup"><span data-stu-id="ed508-179">Delve</span></span>

- <span data-ttu-id="ed508-180">Página inicial do SharePoint</span><span class="sxs-lookup"><span data-stu-id="ed508-180">SharePoint Home</span></span>

- <span data-ttu-id="ed508-181">Centro de Pesquisa</span><span class="sxs-lookup"><span data-stu-id="ed508-181">Search Center</span></span>

<span data-ttu-id="ed508-182">Além disso, os recursos de pesquisa de Multi-Geo podem ser configurados para seus aplicativos de pesquisa personalizadas que usam a API de pesquisa do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ed508-182">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="ed508-183">Analise a [Configurar a pesquisa do OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) para obter instruções, incluindo quaisquer limitações e diferenças.</span><span class="sxs-lookup"><span data-stu-id="ed508-183">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="ed508-184">Validando o OneDrive for Business Multi-Geo configuração</span><span class="sxs-lookup"><span data-stu-id="ed508-184">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="ed508-p116">Abaixo estão alguns casos de uso básico, que talvez você queira incluir em seu plano de validação antes amplamente aplicação do OneDrive for Business Multi-Geo à sua empresa. Depois que você concluir estes testes e qualquer casso adicionais que são relevantes para a sua empresa, você pode escolher passar para a adição de usuários no seu grupo piloto inicial.</span><span class="sxs-lookup"><span data-stu-id="ed508-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="ed508-187">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="ed508-187">**OneDrive for Business**</span></span>

<span data-ttu-id="ed508-p117">Selecione OneDrive o iniciador de aplicativo do Office 365 e confirme que você será direcionado automaticamente para o local geo apropriado para o usuário, com base em PDL do usuário. OneDrive for Business agora deve começar com o provisionamento nesse local. Uma vez provisionado, tente upload e download de alguns documentos.</span><span class="sxs-lookup"><span data-stu-id="ed508-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="ed508-191">**App móvel do OneDrive**</span><span class="sxs-lookup"><span data-stu-id="ed508-191">**OneDrive Mobile App**</span></span>

<span data-ttu-id="ed508-p118">Faça logon em seu aplicativo móvel do OneDrive com suas credenciais de conta de teste. Confirme que você pode ver seu OneDrive para arquivos de negócios e pode interagir com eles a partir do seu dispositivo móvel.</span><span class="sxs-lookup"><span data-stu-id="ed508-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="ed508-194">**Cliente de sincronização do OneDrive**</span><span class="sxs-lookup"><span data-stu-id="ed508-194">**OneDrive sync client**</span></span>

<span data-ttu-id="ed508-p119">Confirme que o cliente de sincronização do OneDrive detecta automaticamente seu OneDrive for Business geo-local durante o logon no. Se você precisar baixar o cliente de sincronização, você pode clicar **Sync** na biblioteca do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="ed508-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="ed508-197">**Aplicativos do Office**</span><span class="sxs-lookup"><span data-stu-id="ed508-197">**Office applications**</span></span>

<span data-ttu-id="ed508-p120">Confirme que você pode acessar o OneDrive for Business fazendo logon um aplicativo do Office, como o Word. Abra o Office de aplicativos e selecione "OneDrive – <TenantName>". Office detectará seu local de OneDrive e mostram os arquivos que pode ser aberto.</span><span class="sxs-lookup"><span data-stu-id="ed508-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="ed508-201">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="ed508-201">**Sharing**</span></span>

<span data-ttu-id="ed508-p121">Tente compartilhar arquivos OneDrive. Confirme que o people picker mostra todos os seus usuários online de SharePoint onde quer que estejam geo.</span><span class="sxs-lookup"><span data-stu-id="ed508-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
