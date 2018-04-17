---
title: Planejar o OneDrive for Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Saiba mais sobre OneDrive para Business Multi-Geo, como funciona a multi-geo e geo-locais que estão disponíveis para armazenamento de dados.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="b3507-103">Planejar o OneDrive for Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="b3507-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="b3507-104">Este guia foi criado para administradores de empresas multinacionais (MNCs) que estão Preparando seu locatário SharePoint Online para ser expandida para áreas geográficas adicionais de acordo com a presença da empresa para atender aos requisitos de residência de dados.</span><span class="sxs-lookup"><span data-stu-id="b3507-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="b3507-p101">Em uma configuração de OneDrive Multi-Geo, seu locatário do Office 365 consiste em um local central (também conhecido como o local padrão) e um ou mais locais de geo satélite. Este é um único locatário que abrange através de vários locais geo. No OneDrive Multi-Geo, suas informações de locatário, incluindo geo locais, são administradas no Windows Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="b3507-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="b3507-108">Aqui estão alguns termos multi-geo principais para ajudá-lo a entender os conceitos básicos da configuração:</span><span class="sxs-lookup"><span data-stu-id="b3507-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="b3507-109">**Locatário** – representação de uma organização na nuvem Office 365 que geralmente tem um ou mais domínios associados a ele (por exemplo, http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="b3507-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="b3507-p102">**Locais de Geo** – os locais geográficos onde os dados do seu locatário estão hospedados. Multi-geo inquilinos abrangem mais de um local de geo, por exemplo, América do Norte e Europa.</span><span class="sxs-lookup"><span data-stu-id="b3507-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="b3507-112">**Locais de dados permitido (ADL)** – os locais de geo para o qual seu locatário foi configurado para hospedar dados OneDrive e o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b3507-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="b3507-p103">**Localização de dados preferencial (PDL)** – o local de geo onde os dados de OneDrive de um usuário individual estão armazenados. Isso pode ser definido pelo administrador para qualquer um dos locais permitidos dados que tiverem sido configuradas para o inquilino. Observe que se você alterar o PDL para um usuário que já tem um site OneDrive, seus dados OneDrive não serão movidos para o novo local de geo automaticamente. Para obter mais informações, consulte [Mover uma biblioteca do OneDrive para uma localização geográfica diferente](move-onedrive-between-geo-locations.md) .</span><span class="sxs-lookup"><span data-stu-id="b3507-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="b3507-117">Habilitar Multi-Geo exige quatro etapas principais:</span><span class="sxs-lookup"><span data-stu-id="b3507-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="b3507-118">Trabalhar com sua equipe de conta para adicionar o plano de serviço _Multi-Geo recursos no Office 365_ .</span><span class="sxs-lookup"><span data-stu-id="b3507-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="b3507-119">Escolha seu desejada satélite geo local (is) e adicioná-los ao seu locatário.</span><span class="sxs-lookup"><span data-stu-id="b3507-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="b3507-p104">Defina o local dos dados preferencial dos usuários para o local de geo de satélite desejada. Quando um novo site de OneDrive é provisionado para um usuário, ele é provisionado para seu PDL.</span><span class="sxs-lookup"><span data-stu-id="b3507-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="b3507-122">Migre sites de OneDrive existentes dos usuários do local da página inicial para seu local de preferência dados conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b3507-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="b3507-123">Consulte [Configurar o OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) para obter detalhes sobre cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="b3507-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3507-p105">Observe que os recursos de Multi-Geo do Office 365 não são projetados para casos de otimização de desempenho, eles são criados para atender aos requisitos de residência de dados. Para obter informações sobre a otimização do desempenho para o Office 365, consulte [planejamento da rede e ajuste de desempenho para o Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou entre em contato com seu grupo de suporte.</span><span class="sxs-lookup"><span data-stu-id="b3507-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="b3507-p106">Você pode configurar qualquer um dos seguintes locais para ser locais de geo satélite onde você pode hospedar arquivos OneDrive. Ao planejar para multi-geo, faça uma lista dos locais que você deseja adicionar ao seu locatário do Office 365. É recomendável iniciando com um ou dois locais de satélite e, em seguida, gradualmente expandindo para obter mais geo locais, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b3507-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b3507-129"><strong>Local</strong></span><span class="sxs-lookup"><span data-stu-id="b3507-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="b3507-130"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="b3507-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b3507-131">Pacífico Asiático</span><span class="sxs-lookup"><span data-stu-id="b3507-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="b3507-132">APC</span><span class="sxs-lookup"><span data-stu-id="b3507-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b3507-133">Europa / Oriente Médio / África</span><span class="sxs-lookup"><span data-stu-id="b3507-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="b3507-134">EUR</span><span class="sxs-lookup"><span data-stu-id="b3507-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b3507-135">América do Norte</span><span class="sxs-lookup"><span data-stu-id="b3507-135">North America</span></span></td>
<td align="left"><span data-ttu-id="b3507-136">NOME</span><span class="sxs-lookup"><span data-stu-id="b3507-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b3507-137">Austrália</span><span class="sxs-lookup"><span data-stu-id="b3507-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="b3507-138">AUSTRÁLIA</span><span class="sxs-lookup"><span data-stu-id="b3507-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b3507-139">Canadá</span><span class="sxs-lookup"><span data-stu-id="b3507-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="b3507-140">PODE</span><span class="sxs-lookup"><span data-stu-id="b3507-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b3507-141">Japão</span><span class="sxs-lookup"><span data-stu-id="b3507-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="b3507-142">JAPONÊS</span><span class="sxs-lookup"><span data-stu-id="b3507-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b3507-143">Coreia</span><span class="sxs-lookup"><span data-stu-id="b3507-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="b3507-144">KOR</span><span class="sxs-lookup"><span data-stu-id="b3507-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b3507-145">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="b3507-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="b3507-146">GBR</span><span class="sxs-lookup"><span data-stu-id="b3507-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="b3507-147">Próximos geo locais:</span><span class="sxs-lookup"><span data-stu-id="b3507-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="b3507-148">França</span><span class="sxs-lookup"><span data-stu-id="b3507-148">France</span></span>
- <span data-ttu-id="b3507-149">Índia</span><span class="sxs-lookup"><span data-stu-id="b3507-149">India</span></span>

<span data-ttu-id="b3507-p107">Quando você configura multi-geo, considere aproveitando a oportunidade para consolidar sua infraestrutura local durante a migração para o Office 365. Por exemplo, se você tiver farms local em Cingapura e Malásia, em seguida, você pode consolidá-los para o local de satélite APC, desde que os requisitos de residência dados permitem que você fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="b3507-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="b3507-152">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b3507-152">Best practices</span></span>

<span data-ttu-id="b3507-p108">Recomendamos que você crie um usuário de teste no Office 365 para fazer algumas teste inicial. Vamos examinar algumas etapas de testes e verificações com esse usuário antes de prosseguir para o recurso de OneDrive Multi-Geo aos usuários de produção onboard.</span><span class="sxs-lookup"><span data-stu-id="b3507-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="b3507-p109">Depois de ter concluído o teste com o usuário de teste, selecione um grupo piloto – talvez do departamento de TI – como o primeiro usar OneDrive em uma nova localização geográfica. Para esse grupo primeiro, selecione os usuários que ainda não têm um OneDrive. Recomendamos não mais de cinco pessoas neste grupo inicial e expanda gradualmente seguindo um método de distribuição em lote.</span><span class="sxs-lookup"><span data-stu-id="b3507-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="b3507-p110">Cada usuário deve ter um *local de dados preferida* (PDL) definida para que o Office 365 pode determinar em qual local geo para provisionar seu OneDrive. Local dos dados preferencial do usuário deve corresponder a um dos seus locais de satélite escolhida ou seu local central. Enquanto o campo PDL não seja obrigatório, é recomendável que uma PDL seja definido para todos os usuários. Cargas de trabalho de um usuário sem uma PDL serão provisionadas no local central com base na lógica Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="b3507-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="b3507-p111">Criar uma lista de seus usuários e inclua o seu nome de usuário principal (UPN) e o código de local para o local apropriado aos dados preferencial. Inclua começar com o usuário de teste e para seu grupo piloto inicial. Você precisará desta lista para os procedimentos de configuração.</span><span class="sxs-lookup"><span data-stu-id="b3507-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="b3507-p112">Se os usuários são sincronizados em um sistema do AD (Active Directory) no local para Windows Azure Active Directory (AAD), você deve definir a localização de dados preferida para usuários sincronizados usando o Azure Active Directory Connect. Diretamente, você não pode configurar o local de dados preferida para usuários sincronizados usando o PowerShell do Windows Azure AD. As etapas para configurar o PDL em AD e sincronizá-lo são abordadas em [sincronização do Azure Active Directory Connect: configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="b3507-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="b3507-p113">A administração de um inquilino multi-geo pode diferir um locatário de não-multi-geo, como muitas das configurações do SharePoint e OneDrive e serviços são multi-geo ciente. Recomendamos que você examine [administrar um ambiente multi-geo](administering-a-multi-geo-environment.md) antes de prosseguir com sua configuração.</span><span class="sxs-lookup"><span data-stu-id="b3507-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="b3507-170">Leia a [experiência do usuário em um ambiente de multgeo](multi-geo-user-experience.md) para obter detalhes sobre a experiência dos usuários finais em um ambiente multi-geo.</span><span class="sxs-lookup"><span data-stu-id="b3507-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="b3507-171">Para começar a configuração OneDrive for Business Multi-Geo, consulte [Configurar o OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b3507-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="b3507-172">Depois de ter concluído a configuração, lembre-se para [migrar bibliotecas de OneDrive dos usuários](move-onedrive-between-geo-locations.md) conforme necessário para obter seus usuários trabalhando dos seus locais de dados preferida.</span><span class="sxs-lookup"><span data-stu-id="b3507-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
