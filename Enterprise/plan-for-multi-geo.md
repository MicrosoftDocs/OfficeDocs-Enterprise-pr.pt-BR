---
title: Planejar o OneDrive for Business com a funcionalidade multigeográfica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba mais sobre o OneDrive for Business com a funcionalidade multigeográfica, como ela funciona e quais localizações geográficas estão disponíveis para o armazenamento de dados.
ms.openlocfilehash: de856bdeb0c0f1ca8e718439ddb98d738843bc5a
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200714"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="c695a-103">Planejar o OneDrive for Business com a funcionalidade multigeográfica</span><span class="sxs-lookup"><span data-stu-id="c695a-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="c695a-104">Este guia foi projetado para os administradores de empresas multinacionais (MNCs) que estão preparando o locatário do SharePoint Online para ser expandido para outras regiões de acordo com a presença da empresa para atender aos requisitos de residência de dados.</span><span class="sxs-lookup"><span data-stu-id="c695a-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="c695a-p101">Em uma configuração multigeográfica do OneDrive, o seu locatário do Office 365 consiste em um local central e uma ou mais localizações geográficas satélites. Este é um único locatário que se distribui em várias localizações geográficas. No OneDrive com a funcionalidade multigeográfica, as suas informações de locatário, incluindo as localizações geográficas, são controladas no Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="c695a-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="c695a-108">Vejamos alguns termos da multigeografia que o ajudarão a entender os conceitos básicos da configuração:</span><span class="sxs-lookup"><span data-stu-id="c695a-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="c695a-109">**Locatário** – a representação de uma organização na nuvem do Office 365 que geralmente tem um ou mais domínios associados (por exemplo, http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="c695a-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="c695a-110">**Localizações geográficas** – locais geográficos disponíveis para hospedar os dados em um locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="c695a-110">**Geo locations** – The geographic locations available to host data in an Office 365 tenant.</span></span>

-   <span data-ttu-id="c695a-p102">**Localizações geográficas** – As localizações geográficas que você configurou para hospedarem os dados de seu locatário do Office 365. Os locatários multigeográficos abrangem mais de uma localização geográfica, por exemplo, América do Norte e Europa.</span><span class="sxs-lookup"><span data-stu-id="c695a-p102">**Satellite locations** – The geo locations that you have configured to host data in your Office 365 tenant. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="c695a-p103">**Local de dados preferencial (PDL)** – a localização geográfica em que são armazenados os dados do OneDrive de um usuário individual. Isso pode ser definido pelo administrador como qualquer um dos locais de dados permitidos que foram configurados para o locatário. Se você alterar o PDL para um usuário que já tenha um site do OneDrive, os dados do OneDrive não serão movidos para a nova localização geográfica automaticamente. Veja mais informações em [Mover uma biblioteca do OneDrive para uma localização geográfica diferente](move-onedrive-between-geo-locations.md).</span><span class="sxs-lookup"><span data-stu-id="c695a-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="c695a-117">Habilitar a multigeografia requer quatro etapas principais:</span><span class="sxs-lookup"><span data-stu-id="c695a-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="c695a-118">Trabalhe com a sua equipe de conta para adicionar o plano de serviço _Funcionalidades multigeográficas no Office 365_.</span><span class="sxs-lookup"><span data-stu-id="c695a-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="c695a-119">Escolha a(s) localização(ões) geográfica(s) satélite(s) desejada(s) e adicione-a(s) ao seu locatário.</span><span class="sxs-lookup"><span data-stu-id="c695a-119">Choose your desired satellite location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="c695a-p104">Defina seu local de dados preferencial dos usuários na localização satélite desejada. Quando um novo site do OneDrive é provisionado para um usuário, ele é provisionado para o PDL dele.</span><span class="sxs-lookup"><span data-stu-id="c695a-p104">Set your users’ preferred data location to the desired satellite location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="c695a-122">Migre os seus sites existentes do OneDrive dos usuários do local central para o local de dados preferencial conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="c695a-122">Migrate your users’ existing OneDrive sites from the central location to their preferred data location as needed.</span></span>

<span data-ttu-id="c695a-123">Veja em [Configurar o OneDrive for Business com a funcionalidade multigeográfica](multi-geo-tenant-configuration.md) detalhes sobre cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="c695a-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c695a-p105">Observe que as funcionalidades multigeográficas do Office 365 não foram criadas para casos de otimização de desempenho, mas sim para atender aos requisitos de residência de dados. Para saber mais sobre a otimização de desempenho do Office 365, confira [Planejamento de rede e ajuste de desempenho para o Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou fale com o grupo de suporte.</span><span class="sxs-lookup"><span data-stu-id="c695a-p105">Note that Office 365 Multi-Geo is not designed for performance optimization cases, it is designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="c695a-p106">Você pode configurar qualquer um dos seguintes locais como localizações geográficas satélites onde você pode hospedar arquivos do OneDrive. Ao planejar a multigeografia, crie uma lista das localizações que você deseja adicionar ao seu locatário do Office 365. Recomendamos começar com uma ou duas localizações satélites e, depois, ir expandindo gradualmente para mais localizações, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c695a-p106">You can configure any of the following locations to be satellite locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="c695a-129"><strong>Localização</strong></span><span class="sxs-lookup"><span data-stu-id="c695a-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="c695a-130"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="c695a-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="c695a-131">Ásia – Pacífico</span><span class="sxs-lookup"><span data-stu-id="c695a-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="c695a-132">APC</span><span class="sxs-lookup"><span data-stu-id="c695a-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c695a-133">Austrália</span><span class="sxs-lookup"><span data-stu-id="c695a-133">Australia</span></span></td>
<td align="left"><span data-ttu-id="c695a-134">AUS</span><span class="sxs-lookup"><span data-stu-id="c695a-134">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c695a-135">Canadá</span><span class="sxs-lookup"><span data-stu-id="c695a-135">Canada</span></span></td>
<td align="left"><span data-ttu-id="c695a-136">CAN</span><span class="sxs-lookup"><span data-stu-id="c695a-136">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c695a-137">Europa/Oriente Médio/África</span><span class="sxs-lookup"><span data-stu-id="c695a-137">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="c695a-138">EUR</span><span class="sxs-lookup"><span data-stu-id="c695a-138">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c695a-139">França</span><span class="sxs-lookup"><span data-stu-id="c695a-139">France</span></span></td>
<td align="left"><span data-ttu-id="c695a-140">FRA</span><span class="sxs-lookup"><span data-stu-id="c695a-140">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c695a-141">Índia</span><span class="sxs-lookup"><span data-stu-id="c695a-141">India</span></span></td>
<td align="left"><span data-ttu-id="c695a-142">IND</span><span class="sxs-lookup"><span data-stu-id="c695a-142">IND</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c695a-143">Japão</span><span class="sxs-lookup"><span data-stu-id="c695a-143">Japan</span></span></td>
<td align="left"><span data-ttu-id="c695a-144">JPN</span><span class="sxs-lookup"><span data-stu-id="c695a-144">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c695a-145">Coreia</span><span class="sxs-lookup"><span data-stu-id="c695a-145">Korea</span></span></td>
<td align="left"><span data-ttu-id="c695a-146">KOR</span><span class="sxs-lookup"><span data-stu-id="c695a-146">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c695a-147">América do Norte</span><span class="sxs-lookup"><span data-stu-id="c695a-147">North America</span></span></td>
<td align="left"><span data-ttu-id="c695a-148">NAM</span><span class="sxs-lookup"><span data-stu-id="c695a-148">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c695a-149">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="c695a-149">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="c695a-150">GBR</span><span class="sxs-lookup"><span data-stu-id="c695a-150">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="c695a-p107">Ao configurar a multigeografia, considere aproveitar a oportunidade de consolidar a sua infraestrutura local ao migrar para o Office 365. Por exemplo, se você tiver farms locais em Cingapura e na Malásia, poderá consolidá-los para a localização satélite de APC, desde que os requisitos de residência de dados permitam isso.</span><span class="sxs-lookup"><span data-stu-id="c695a-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="c695a-153">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="c695a-153">Best practices</span></span>

<span data-ttu-id="c695a-p108">Recomendamos que você crie um usuário de teste no Office 365 para executar alguns testes iniciais. Você passará por algumas etapas de teste e verificação com esse usuário antes de prosseguir para a integração de usuários de produção no recurso de multigeografia do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="c695a-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into OneDrive Multi-Geo.</span></span>

<span data-ttu-id="c695a-p109">Depois de concluir os testes com o usuário de teste, selecione um grupo piloto, talvez do departamento de TI, como o primeiro a usar o OneDrive em uma nova localização geográfica. Para este primeiro grupo, selecione os usuários que ainda não têm o OneDrive. Recomendamos no máximo cinco pessoas nesse grupo inicial e, depois, que se expanda gradualmente seguindo uma abordagem de implantação em lote.</span><span class="sxs-lookup"><span data-stu-id="c695a-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="c695a-p110">Cada usuário deve ter um *local de dados preferencial* (PDL) definido para que o Office 365 possa determinar em qual localização geográfica provisionar o OneDrive. O local de dados preferencial do usuário deve corresponder a um de seus locais satélites escolhidos ou ao local central. Embora o campo PDL não seja obrigatório, é recomendável que um PDL seja definido para todos os usuários. As cargas de trabalho de um usuário sem um PDL serão provisionadas no local central.</span><span class="sxs-lookup"><span data-stu-id="c695a-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.</span></span>   

<span data-ttu-id="c695a-p111">Crie uma lista dos seus usuários e inclua o nome UPN e o código de local para o local de dados preferencial adequado. Inclua o seu usuário de teste e o seu grupo piloto inicial para começar. Você precisará dessa lista para os procedimentos de configuração.</span><span class="sxs-lookup"><span data-stu-id="c695a-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="c695a-p112">Se os usuários forem sincronizados de um sistema local do Active Directory (AD) para o Azure Active Directory (AAD), você deverá definir o local de dados preferencial para os usuários sincronizados usando o Azure Active Directory Connect. Diretamente, você não poderá configurar o local de dados preferencial para os usuários sincronizados usando o PowerShell do Azure AD. As etapas para se configurar o PDL no AD e sincronizá-lo estão descritas em [Sincronização do Azure Active Directory Connect: Configurar o local de dados preferencial para os recursos do Office 365](https://docs.microsoft.com/pt-BR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="c695a-p112">If your users are synchronized from an on-premises Active Directory system to Azure Active Directory, you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/pt-BR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="c695a-p113">A administração de um locatário multigeográfico pode variar de um locatário que não seja de multigeografia, pois muitos dos serviços e configurações do SharePoint e do OneDrive detectam a multigeografia. Recomendamos que leia [Administrar um ambiente multigeográfico](administering-a-multi-geo-environment.md) antes de prosseguir com a configuração.</span><span class="sxs-lookup"><span data-stu-id="c695a-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="c695a-171">Leia em [Experiência do usuário em um ambiente multigeográfico](multi-geo-user-experience.md) detalhes sobre a experiência dos usuários finais em um ambiente multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="c695a-171">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="c695a-172">Para começar a configurar o OneDrive for Business com a funcionalidade multigeográfica, confira [Configurar o OneDrive for Business com a funcionalidade multigeográfica](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c695a-172">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="c695a-173">Depois de concluir a configuração, lembre-se de [migrar as bibliotecas do OneDrive dos seus usuários](move-onedrive-between-geo-locations.md) conforme necessário para que os usuários possam trabalhar dos locais de dados preferenciais.</span><span class="sxs-lookup"><span data-stu-id="c695a-173">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
