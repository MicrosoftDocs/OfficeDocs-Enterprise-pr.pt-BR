---
title: Planejar o OneDrive for Business com a funcionalidade multigeográfica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba mais sobre o OneDrive for Business com a funcionalidade multigeográfica, como ela funciona e quais localizações geográficas estão disponíveis para o armazenamento de dados.
ms.openlocfilehash: 26dc9d1b0f0f78e1740088036be4b77bea3ce176
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2018
ms.locfileid: "21549982"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="8e2f7-103">Planejar o OneDrive for Business com a funcionalidade multigeográfica</span><span class="sxs-lookup"><span data-stu-id="8e2f7-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="8e2f7-104">Este guia foi projetado para os administradores de empresas multinacionais (MNCs) que estão preparando o locatário do SharePoint Online para ser expandido para outras regiões de acordo com a presença da empresa para atender aos requisitos de residência de dados.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="8e2f7-p101">Em uma configuração multigeográfica do OneDrive, o seu locatário do Office 365 consiste em um local central (também conhecido como local padrão) e uma ou mais localizações geográficas satélites. Este é um único locatário que transita em várias localizações geográficas. No OneDrive com a funcionalidade multigeográfica, as suas informações de locatário, incluindo as localizações geográficas, são controladas no Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="8e2f7-108">Vejamos alguns termos da multigeografia que o ajudarão a entender os conceitos básicos da configuração:</span><span class="sxs-lookup"><span data-stu-id="8e2f7-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="8e2f7-109">**Locatário** – A representação de uma organização na nuvem do Office 365 que geralmente tem um ou mais domínios associados (por exemplo, http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="8e2f7-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="8e2f7-p102">**Localizações geográficas** – As localizações geográficas onde os dados do locatário estão hospedados. Os locatários multigeográficos abrangem mais de uma localização geográfica, por exemplo, América do Norte e Europa.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="8e2f7-112">**Locais de dados permitidos (ADL)** – As localizações geográficas para o seu locatário foram configuradas para hospedar dados do OneDrive e do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="8e2f7-p103">**Local de dados preferencial (PDL)** – A localização geográfica onde são armazenados os dados do OneDrive de um usuário individual. Isso pode ser definido pelo administrador como qualquer um dos locais de dados permitidos que foram configurados para o locatário. Se você alterar o PDL para um usuário que já tenha um site do OneDrive, os dados do OneDrive não serão movidos para a nova localização geográfica automaticamente. Veja mais informações em [Mover uma biblioteca do OneDrive para uma localização geográfica diferente](move-onedrive-between-geo-locations.md).</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="8e2f7-117">Habilitar a multigeografia requer quatro etapas principais:</span><span class="sxs-lookup"><span data-stu-id="8e2f7-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="8e2f7-118">Trabalhe com a sua equipe de conta para adicionar o plano de serviço _Funcionalidades multigeográficas no Office 365_.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="8e2f7-119">Escolha as localizações geográficas satélites desejadas e adicione-as ao seu locatário.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="8e2f7-p104">Defina local de dados preferencial dos usuários para a localização geográfica satélite desejada. Quando um novo site do OneDrive é provisionado para um usuário, ele é provisionado para o PDL dele.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="8e2f7-122">Migre os seus sites existentes do OneDrive dos usuários desde o local doméstico para o local de dados preferencial conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="8e2f7-123">Veja em [Configurar o OneDrive for Business com a funcionalidade multigeográfica](multi-geo-tenant-configuration.md) detalhes sobre cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e2f7-p105">Observe que as funcionalidades multigeográficas do Office 365 não foram criadas para casos de otimização de desempenho, mas sim para atender aos requisitos de residência de dados. Para saber mais sobre a otimização de desempenho do Office 365, confira [Planejamento de rede e ajuste de desempenho para o Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou fale com o grupo de suporte.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="8e2f7-p106">Você pode configurar qualquer um dos seguintes locais como localizações geográficas satélites onde você pode hospedar arquivos do OneDrive. Ao planejar a multigeografia, crie uma lista das localizações que você deseja adicionar ao seu locatário do Office 365. Recomendamos começar com uma ou duas localizações satélites e, depois, ir expandindo gradualmente para mais localizações, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="8e2f7-129"><strong>Localização</strong></span><span class="sxs-lookup"><span data-stu-id="8e2f7-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="8e2f7-130"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="8e2f7-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="8e2f7-131">Ásia – Pacífico</span><span class="sxs-lookup"><span data-stu-id="8e2f7-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-132">APC</span><span class="sxs-lookup"><span data-stu-id="8e2f7-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8e2f7-133">Austrália</span><span class="sxs-lookup"><span data-stu-id="8e2f7-133">Australia</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-134">AUS</span><span class="sxs-lookup"><span data-stu-id="8e2f7-134">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8e2f7-135">Canadá</span><span class="sxs-lookup"><span data-stu-id="8e2f7-135">Canada</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-136">CAN</span><span class="sxs-lookup"><span data-stu-id="8e2f7-136">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8e2f7-137">Europa/Oriente Médio/África</span><span class="sxs-lookup"><span data-stu-id="8e2f7-137">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-138">EUR</span><span class="sxs-lookup"><span data-stu-id="8e2f7-138">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8e2f7-139">França</span><span class="sxs-lookup"><span data-stu-id="8e2f7-139">France</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-140">FRA</span><span class="sxs-lookup"><span data-stu-id="8e2f7-140">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8e2f7-141">Japão</span><span class="sxs-lookup"><span data-stu-id="8e2f7-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-142">JPN</span><span class="sxs-lookup"><span data-stu-id="8e2f7-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8e2f7-143">Coreia</span><span class="sxs-lookup"><span data-stu-id="8e2f7-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-144">KOR</span><span class="sxs-lookup"><span data-stu-id="8e2f7-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8e2f7-145">América do Norte</span><span class="sxs-lookup"><span data-stu-id="8e2f7-145">North America</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-146">NAM</span><span class="sxs-lookup"><span data-stu-id="8e2f7-146">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8e2f7-147">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="8e2f7-147">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="8e2f7-148">GBR</span><span class="sxs-lookup"><span data-stu-id="8e2f7-148">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="8e2f7-149">Localizações geográficas futuras:</span><span class="sxs-lookup"><span data-stu-id="8e2f7-149">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="8e2f7-150">Índia</span><span class="sxs-lookup"><span data-stu-id="8e2f7-150">India</span></span>

<span data-ttu-id="8e2f7-p107">Ao configurar a multigeografia, considere aproveitar a oportunidade de consolidar a sua infraestrutura local ao migrar para o Office 365. Por exemplo, se você tiver farms locais em Cingapura e na Malásia, poderá consolidá-los para a localização satélite de APC, desde que os requisitos de residência de dados permitam isso.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="8e2f7-153">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="8e2f7-153">Best practices</span></span>

<span data-ttu-id="8e2f7-p108">Recomendamos que você crie um usuário de teste no Office 365 para executar alguns testes iniciais. Você passará por algumas etapas de teste e verificação com esse usuário antes de prosseguir para a integração de usuários de produção no recurso de multigeografia do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="8e2f7-p109">Depois de concluir os testes com o usuário de teste, selecione um grupo piloto, talvez do departamento de TI, como o primeiro a usar o OneDrive em uma nova localização geográfica. Para esse primeiro grupo, selecione os usuários que ainda não têm o OneDrive. Recomendamos no máximo cinco pessoas nesse grupo inicial e, depois, que se expanda gradualmente seguindo uma abordagem de implantação em lote.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="8e2f7-p110">Cada usuário deve ter um *local de dados preferencial* (PDL) definido para que o Office 365 possa determinar em qual localização geográfica provisionar o OneDrive. O local de dados preferencial do usuário deve coincidir com um dos seus locais satélites escolhidos ou com o local central. Embora o campo PDL não seja obrigatório, é recomendável que um PDL seja definido para todos os usuários. As cargas de trabalho de um usuário sem um PDL serão provisionadas no local central, com base na lógica multigeográfica.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="8e2f7-p111">Crie uma lista dos seus usuários e inclua o nome de usuário principal (UPN) e o código de local para o local de dados preferencial adequado. Inclua o seu usuário de teste e o seu grupo piloto inicial para começar. Você precisará dessa lista para os procedimentos de configuração.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="8e2f7-p112">Se os usuários forem sincronizados de um sistema local do Active Directory (AD) para o Azure Active Directory (AAD), você deverá definir o local de dados preferencial para os usuários sincronizados usando o Azure Active Directory Connect. Diretamente, você não poderá configurar o local de dados preferencial para os usuários sincronizados usando o PowerShell do Azure AD. As etapas para se configurar o PDL no AD e sincronizá-lo estão descritas em [Sincronização do Azure Active Directory Connect: Configurar o local de dados preferencial para os recursos do Office 365](https://docs.microsoft.com/pt-BR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/pt-BR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="8e2f7-p113">A administração de um locatário multigeográfico pode variar de um locatário que não seja de multigeografia, pois muitos dos serviços e configurações do SharePoint e do OneDrive detectam a multigeografia. Recomendamos que leia [Administrar um ambiente multigeográfico](administering-a-multi-geo-environment.md) antes de prosseguir com a configuração.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="8e2f7-171">Leia em [Experiência do usuário em um ambiente multigeográfico](multi-geo-user-experience.md) detalhes sobre a experiência dos usuários finais em um ambiente multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-171">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="8e2f7-172">Para começar a configurar o OneDrive for Business com a funcionalidade multigeográfica, confira [Configurar o OneDrive for Business com a funcionalidade multigeográfica](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8e2f7-172">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="8e2f7-173">Depois de concluir a configuração, lembre-se de [migrar as bibliotecas do OneDrive dos seus usuários](move-onedrive-between-geo-locations.md) conforme necessário para que os usuários possam trabalhar dos locais de dados preferenciais.</span><span class="sxs-lookup"><span data-stu-id="8e2f7-173">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
