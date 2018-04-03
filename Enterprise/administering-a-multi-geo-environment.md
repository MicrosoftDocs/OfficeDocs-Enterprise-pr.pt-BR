---
title: Administrando um ambiente multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba mais sobre a administração dos serviços do SharePoint e OneDrive em um ambiente multi-geo.
ms.openlocfilehash: f49cf35503ee6495b5982dc7d72f9b1936f564c6
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="f745a-103">Administrando um ambiente multi-geo</span><span class="sxs-lookup"><span data-stu-id="f745a-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="f745a-104">Aqui está uma olhada em como os serviços de OneDrive e o SharePoint funcionam em um ambiente multi-geo.</span><span class="sxs-lookup"><span data-stu-id="f745a-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="f745a-105">Experiência do administrador do OneDrive</span><span class="sxs-lookup"><span data-stu-id="f745a-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="f745a-p101">O [Centro de administração do OneDrive](https://admin.onedrive.com) tem uma guia **Geo locais** na navegação esquerda, quais recursos um geo-locais mapeiam onde você pode exibir e gerenciar seus locais geo. Use esta página para adicionar ou excluir locais geo para seu locatário.</span><span class="sxs-lookup"><span data-stu-id="f745a-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="f745a-108">Taxonomia</span><span class="sxs-lookup"><span data-stu-id="f745a-108">Taxonomy</span></span>

<span data-ttu-id="f745a-p102">Oferecemos suporte uma unificada [taxonomia](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) para metadados corporativos gerenciados entre localidades geo, com o mestre que está sendo hospedado no local central para sua empresa. Recomendamos que você gerenciar seu taxonomia global do local central e apenas Adicione termos específicos do local para taxonomia do local geo de satélite. Termos de taxonomia global serão sincronizadas com os locais de geo satélite.</span><span class="sxs-lookup"><span data-stu-id="f745a-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="f745a-112">Compartilhando</span><span class="sxs-lookup"><span data-stu-id="f745a-112">Sharing</span></span>

<span data-ttu-id="f745a-p103">Os administradores podem definir e gerenciar políticas de compartilhamento para cada um dos seus locais. Os sites de OneDrive em cada local geo aceita somente as correspondente geo compartilhamento configurações específicas. Por exemplo, você pode permitir o [compartilhamento externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) de seu local central, mas não para sua satélite local ou vice-versa. Para o OneDrive Multi-Geo, você deve gerenciar suas configurações de compartilhamento em cada local geo como essas não são sincronizadas entre o inquilino.</span><span class="sxs-lookup"><span data-stu-id="f745a-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="f745a-p104">Para gerenciar o compartilhamento visitar a página do [Centro de administração do OneDrive configurações de compartilhamento](https://admin.onedrive.com/?v=SharingSettings) . Compartilhamento externo está habilitado por padrão com qualquer pessoa em cada local de satélite.</span><span class="sxs-lookup"><span data-stu-id="f745a-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="f745a-119">Aplicativo de perfil de usuário</span><span class="sxs-lookup"><span data-stu-id="f745a-119">User Profile Application</span></span>

<span data-ttu-id="f745a-p105">Existe um [aplicativo de perfil de usuário](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) em cada local geo. Informações de perfil de cada usuário são hospedadas em sua localização geográfica e disponíveis para o administrador para esse local geo.</span><span class="sxs-lookup"><span data-stu-id="f745a-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="f745a-122">Se você tiver propriedades de perfil personalizadas, depois, é recomendável que você use o mesmo esquema de perfil entre regiões geográficas e preenche suas propriedades de perfil personalizadas tanto em todos os locais de geo ou onde for necessário.</span><span class="sxs-lookup"><span data-stu-id="f745a-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="f745a-123">Aplicativos do BCS, repositório seguro,</span><span class="sxs-lookup"><span data-stu-id="f745a-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="f745a-124">BCS, repositório seguro e aplicativos tiverem instâncias de geo separado, portanto, o administrador do SharePoint Online deve gerenciar e configurar esses serviços de cada instância geo onde eles desejam estar presentes.</span><span class="sxs-lookup"><span data-stu-id="f745a-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="f745a-125">Segurança e conformidade Centro de administração</span><span class="sxs-lookup"><span data-stu-id="f745a-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="f745a-126">Não há um centro de conformidade central para o locatário Multi-Geo: [Centro de conformidade e segurança do Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="f745a-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="f745a-127">Diretiva Prevention (DLP) de perda de dados do informações proteção (IP)</span><span class="sxs-lookup"><span data-stu-id="f745a-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="f745a-p106">Você pode definir seu DLP IP políticas do OneDrive for Business na Central de segurança e conformidade, políticas de escopo, conforme necessário para o inquilino todo ou usuários aplicáveis. Por exemplo: se você deseja selecionar uma política para um usuário OneDrive em um local de satélite, selecione esta opção para aplicar a política a um OneDrive específico e insira o usuário do OneDrive url. Consulte [Visão geral das políticas de prevenção de perda de dados](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para orientação geral na criação de políticas de DLP.</span><span class="sxs-lookup"><span data-stu-id="f745a-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="f745a-131">As políticas DLP são automaticamente sincronizadas com base na sua capacidade de aplicação para cada local geo.</span><span class="sxs-lookup"><span data-stu-id="f745a-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="f745a-132">A implementação de políticas de prevenção de perda de dados e de proteção de informações para todos os usuários em um local de geo não é uma opção disponível na interface de usuário, em vez disso, você deve selecionar as contas de OneDrive aplicáveis para a política ou aplicar a política globalmente a todas as contas do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f745a-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="f745a-133">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="f745a-133">eDiscovery</span></span> 

<span data-ttu-id="f745a-p107">Por padrão, uma descoberta eletrônica gerente ou administrador de um inquilino multi-geo será capaz de realizar o eDiscovery apenas no local central desse inquilino. Para oferecer suporte a capacidade de realizar o eDiscovery para locais de satélite, um novo parâmetro de filtro de segurança de conformidade chamado "Region" está disponível por meio do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f745a-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="f745a-136">O administrador global do Office 365 deve atribuir permissões de gerente de descoberta eletrônica para permitir que outras pessoas executar a descoberta eletrônica e atribuir um parâmetro "Region" em seu filtro de segurança de conformidade aplicável para especificar a região para a realização de descoberta eletrônica como satélite local, caso contrário que nenhum eDiscovery será realizada para o local de satélite.</span><span class="sxs-lookup"><span data-stu-id="f745a-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="f745a-p108">Quando a função de gerente ou administrador de descoberta eletrônica é definida para um local específico-geo, o eDiscovery, gerente ou administrador só poderá executar ações de pesquisa de descoberta eletrônica contra os sites do SharePoint e sites de OneDrive localizados naquele geo-local. Se um administrador ou um gerente de descoberta eletrônica tenta pesquisar sites SharePoint ou OneDrive fora da região especificada, nenhum resultado será retornado. Além disso, quando o eDiscovery gerente ou administrador para uma região dispara uma exportação, os dados são exportados para a instância Azure da região. Isso ajuda as organizações a manter a conformidade não permitindo que o conteúdo a ser exportado entre as fronteiras controladas.</span><span class="sxs-lookup"><span data-stu-id="f745a-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="f745a-141">Se for necessário para um gerente para pesquisar em várias regiões SharePoint eDiscovery, outra conta de usuário precisará ser criado para o eDiscovery Manager que especifica a região alternativa onde os sites OneDrive ou do SharePoint estão localizados.</span><span class="sxs-lookup"><span data-stu-id="f745a-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f745a-142"><strong>Multi-Geo suportado Geo locais</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="f745a-143"><strong>eDiscovery para SharePoint exportados dados será neste local de dados Blob Azure …</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f745a-144"><strong>NOME</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="f745a-145">Centros de dados dos EUA</span><span class="sxs-lookup"><span data-stu-id="f745a-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f745a-146"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="f745a-147">Centros de dados Europa</span><span class="sxs-lookup"><span data-stu-id="f745a-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f745a-148"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="f745a-149">Sul Leste ou centros de dados do Leste Asiático</span><span class="sxs-lookup"><span data-stu-id="f745a-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f745a-150"><strong>PODE</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="f745a-151">Centros de dados dos EUA</span><span class="sxs-lookup"><span data-stu-id="f745a-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f745a-152"><strong>AUSTRÁLIA</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="f745a-153">Sul Leste ou centros de dados do Leste Asiático</span><span class="sxs-lookup"><span data-stu-id="f745a-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f745a-154"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="f745a-155">Localização de dados padrão de locatário</span><span class="sxs-lookup"><span data-stu-id="f745a-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f745a-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="f745a-157">Centros de dados Europa</span><span class="sxs-lookup"><span data-stu-id="f745a-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f745a-158"><strong>JAPONÊS</strong></span><span class="sxs-lookup"><span data-stu-id="f745a-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="f745a-159">Sul Leste ou centros de dados do Leste Asiático</span><span class="sxs-lookup"><span data-stu-id="f745a-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f745a-160">Para definir o filtro de segurança de conformidade para uma região:</span><span class="sxs-lookup"><span data-stu-id="f745a-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="f745a-161">Abrir o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f745a-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="f745a-162">Insira </span><span class="sxs-lookup"><span data-stu-id="f745a-162">Enter</span></span>  
    <span data-ttu-id="f745a-163">$s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred-autenticação básica - AllowRedirection - SessionOption (New-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="f745a-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="f745a-164">$um = Import-PSSession $s - AllowClobber</span><span class="sxs-lookup"><span data-stu-id="f745a-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="f745a-165">**New-ComplianceSecurityFilter** **-Ação** Todos os EnterTheNameYouWantToAssign de **-FilterName** **-região** EnterTheRegionParameter **-usuários** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="f745a-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="f745a-166">Por exemplo: **New-ComplianceSecurityFilter-ação** NAMEDISCOVERYMANAGERS de todos os **- FilterName** **-região** NAM **-usuários** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="f745a-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="f745a-167">Consulte o artigo de [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para sintaxe e parâmetros adicionais</span><span class="sxs-lookup"><span data-stu-id="f745a-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="f745a-168">Pesquisa de log de auditoria</span><span class="sxs-lookup"><span data-stu-id="f745a-168">Audit log search</span></span>

<span data-ttu-id="f745a-p109">Um unificada de [log de auditoria](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) para todos os seus locais geo está disponível de página de pesquisa de log de auditoria do Office 365. Você pode ver todas as entradas de log de auditoria de entre geos, por exemplo, EUR & me geo as atividades dos usuários serão exibidas em um modo de exibição de organização e, em seguida, você pode aplicar filtros existentes para ver as atividades do usuário específico.</span><span class="sxs-lookup"><span data-stu-id="f745a-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
