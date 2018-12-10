---
title: Administrar um ambiente multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba como administrar o SharePoint e os serviços do OneDrive em um ambiente multigeográfico.
ms.openlocfilehash: 09f8816fc0ba748ced5bd104710677829d893198
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200694"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="d6851-103">Administrar um ambiente multigeográfico</span><span class="sxs-lookup"><span data-stu-id="d6851-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="d6851-104">Veja aqui um resumo de como funcionam os serviços do OneDrive e do SharePoint em um ambiente multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="d6851-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="d6851-105">Experiência de Administrador do OneDrive</span><span class="sxs-lookup"><span data-stu-id="d6851-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="d6851-p101">O [Centro de Administração do OneDrive](https://admin.onedrive.com) tem uma guia de **localizações geográficas** na navegação à esquerda, que apresenta um mapa com os locais onde é possível exibir e gerenciar suas localizações geográficas. Use essa página para adicionar ou excluir as localizações geográficas de seu locatário.</span><span class="sxs-lookup"><span data-stu-id="d6851-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="d6851-108">Taxonomia</span><span class="sxs-lookup"><span data-stu-id="d6851-108">Taxonomy</span></span>

<span data-ttu-id="d6851-p102">Oferecemos suporte para uma [taxonomia](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificada para os metadados gerenciados da empresa em diferentes localizações geográficas, mantendo os dados-mestres hospedados na localização central de sua empresa. Recomendamos que você gerencie sua taxonomia global a partir do local central e adicione apenas termos específicos para cada localização à Taxonomia das localização geográficas satélites. Os termos da taxonomia global serão sincronizados nas localizações geográficas satélites.</span><span class="sxs-lookup"><span data-stu-id="d6851-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite location’s Taxonomy. Global taxonomy terms will synchronize to the satellite locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="d6851-112">Compartilhamento</span><span class="sxs-lookup"><span data-stu-id="d6851-112">Sharing</span></span>

<span data-ttu-id="d6851-p103">Os administradores podem definir e gerenciar as políticas de compartilhamento para cada uma das localizações. Os sites do OneDrive em cada localização geográfica respeitarão apenas as configurações de compartilhamento específicas para aquela localização. (Por exemplo, você pode permitir o [compartilhamento externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) na localização central, mas não na localização satélite, ou vice-versa). As configurações de compartilhamento, no entanto, não permitem configurar limitações de compartilhamento entre localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="d6851-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo locations.</span></span>

<span data-ttu-id="d6851-p104">Para a OneDrive com Funcionalidades Multigeográficas, você deve gerenciar as configurações de compartilhamento em cada localização geográfica, pois essas não são sincronizadas no locatário. Para gerenciar o compartilhamento, acesse a página de [configurações de compartilhamento no Centro de Administração do OneDrive](https://admin.onedrive.com/?v=SharingSettings). Por padrão, o compartilhamento externo é habilitado para Qualquer Pessoa em todas as localizações no satélite.</span><span class="sxs-lookup"><span data-stu-id="d6851-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="d6851-119">Aplicativo de Perfil de Usuário</span><span class="sxs-lookup"><span data-stu-id="d6851-119">User Profile Application</span></span>

<span data-ttu-id="d6851-p105">Há um [aplicativo de perfil de usuário](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) em cada localização geográfica. As informações de perfil de cada usuário estão hospedadas na localização geográfica dele e ficam disponíveis para o administrador daquela localização.</span><span class="sxs-lookup"><span data-stu-id="d6851-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="d6851-p106">Se houver propriedades de perfil personalizadas, recomendamos que você use o mesmo esquema de perfil nas localizações e popule as propriedades personalizadas em cada uma delas ou nas que forem necessárias. Para obter mais orientações sobre como popular de forma programática os dados de perfil de usuário, consultes as informações sobre a [API de Atualização de Perfil de Usuário em Massa](https://docs.microsoft.com/pt-BR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).</span><span class="sxs-lookup"><span data-stu-id="d6851-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/pt-BR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="d6851-124">BCS, Repositório Seguro, Aplicativos</span><span class="sxs-lookup"><span data-stu-id="d6851-124">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="d6851-125">A BCS, o Repositório Seguro e os Aplicativos têm instâncias geográficas em cada localização satélite e portanto, o administrador do SharePoint Online deve gerenciar e configurar esses serviços separadamente para cada localização satélite.</span><span class="sxs-lookup"><span data-stu-id="d6851-125">BCS, Secure Store, and Apps all have separate instances in each satellite location, therefore the SharePoint Online administrator should manage and configure these services separately from each satellite location.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="d6851-126">Centro de Administração de Conformidade e Segurança</span><span class="sxs-lookup"><span data-stu-id="d6851-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="d6851-127">Há um centro de conformidade central para o locatário multigeográfico: [Centro de Conformidade e Segurança do Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="d6851-127">There is one central compliance center for a multi-geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="d6851-128">Política de Prevenção contra Perda de Dados (DLP) e Proteção da Informação (IP). </span><span class="sxs-lookup"><span data-stu-id="d6851-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="d6851-p107">Você pode configurar as políticas de DLP e IP para o OneDrive for Business no Centro de Segurança e Conformidade, examinando com cuidado as políticas conforme necessário para o locatário inteiro ou para os usuários que precisarem. Por exemplo: se desejar selecionar uma política para um usuário do OneDrive em uma localização no satélite, selecione-a para aplicar a política em um OneDrive específico e insira a url do OneDrive do usuário. Consulte a [visão geral das políticas de prevenção contra perda de dados](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para obter instruções gerais para a criação de políticas de DLP.</span><span class="sxs-lookup"><span data-stu-id="d6851-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="d6851-132">As políticas de DLP são sincronizadas automaticamente de acordo com a aplicabilidade delas a cada localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="d6851-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="d6851-133">A implementação de políticas de Prevenção contra Perda de Dados e Proteção da Informação para todos os usuários em uma localização geográfica não é uma opção disponível na IU. Em vez disso, é preciso selecionar as contas do OneDrive em que deseja aplicar a política ou aplicá-la de modo global a todas as contas do OneDrive. </span><span class="sxs-lookup"><span data-stu-id="d6851-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="d6851-134">Descoberta Eletrônica</span><span class="sxs-lookup"><span data-stu-id="d6851-134">eDiscovery</span></span> 

<span data-ttu-id="d6851-p108">Por padrão, o gerente ou administrador de Descoberta Eletrônica de um locatário multigeográfico poderá realizar a Descoberta Eletrônica apenas na localização central desse locatário. Para poder realizar a descoberta eletrônica nas localizações no satélite, está disponível, no PowerShell, um novo parâmetro de Filtro de Segurança de Conformidade, chamado "Região".</span><span class="sxs-lookup"><span data-stu-id="d6851-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="d6851-137">O administrador global do Office 365 deve atribuir permissões de gerente de Descoberta Eletrônica para permitir que outras pessoas possam realizá-la e atribuir o parâmetro "Região" no Filtro de Segurança e Conformidade deles, para especificar a região como uma localização no satélite para a realização da Descoberta. Caso contrário, a Descoberta Eletrônica não será realizada para nenhuma localização no satélite.</span><span class="sxs-lookup"><span data-stu-id="d6851-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="d6851-p109">Quando a função de gerente ou administrador de Descoberta Eletrônica é definida para uma determinada localização satélite, o gerente ou o administrador só poderá realizar ações de pesquisa de Descoberta Eletrônica em sites do SharePoint e do OneDrive naquela localização satélite. Se ele tentar pesquisar sites do SharePoint ou do OneDrive fora da localização satélite especificada, nenhum resultado será apresentado. Além disso, quando o gerente ou administrador de Descoberta Eletrônica de uma localização satélite aciona uma exportação, os dados são exportados para a instância do Azure daquela região. Isso ajuda as organizações a permanecerem em conformidade, não permitindo que o conteúdo seja exportado para além de fronteiras controladas.</span><span class="sxs-lookup"><span data-stu-id="d6851-p109">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="d6851-142">Caso seja necessário que o gerente de Descoberta Eletrônica pesquise diversas localizações satélites no SharePoint, será necessário criar outra conta de usuário para ele, a qual especifique a localização satélite alternativa onde se encontram os sites do OneDrive ou do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d6851-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d6851-143"><strong>Localizações geográficas em que a Multigeografia é suportada</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="d6851-144"><strong>A Descoberta eletrônica para os dados exportados do SharePoint estará nesta localização de dados do Blob do Azure...</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d6851-145"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-145"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-146">Datacenters no sudeste ou leste da Ásia</span><span class="sxs-lookup"><span data-stu-id="d6851-146">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d6851-147"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-147"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-148">Datacenters no sudeste ou leste da Ásia</span><span class="sxs-lookup"><span data-stu-id="d6851-148">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d6851-149"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-149"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-150">Datacenters nos Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="d6851-150">US datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d6851-151"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-151"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-152">Datacenters na Europa</span><span class="sxs-lookup"><span data-stu-id="d6851-152">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d6851-153"><strong>FRA</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-153"><strong>FRA</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-154">Datacenters na Europa</span><span class="sxs-lookup"><span data-stu-id="d6851-154">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d6851-155"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-155"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-156">Datacenters na Europa</span><span class="sxs-lookup"><span data-stu-id="d6851-156">Europe datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d6851-157"><strong>IND</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-157"><strong>IND</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-158">Datacenters no sudeste ou leste da Ásia</span><span class="sxs-lookup"><span data-stu-id="d6851-158">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d6851-159"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-159"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-160">Datacenters no sudeste ou leste da Ásia</span><span class="sxs-lookup"><span data-stu-id="d6851-160">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d6851-161"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="d6851-161"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-162">Datacenters no sudeste ou leste da Ásia</span><span class="sxs-lookup"><span data-stu-id="d6851-162">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d6851-163"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="d6851-163"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="d6851-164">Datacenters nos Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="d6851-164">US datacenters</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="d6851-165">Para configurar o Filtro de Segurança de Conformidade para uma região:</span><span class="sxs-lookup"><span data-stu-id="d6851-165">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="d6851-166">Abra o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6851-166">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="d6851-167">Digite</span><span class="sxs-lookup"><span data-stu-id="d6851-167">Enter</span></span>  
    <span data-ttu-id="d6851-168">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="d6851-168">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="d6851-169">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="d6851-169">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="d6851-170">**New-ComplianceSecurityFilter** **-Action** TODOS **-FilterName** InsiraONomeParaOQualDesejaAtribuir **-Region** InsiraOParâmetroDeRegiao **-Users** InsiraONomePrincipalDoUsuario</span><span class="sxs-lookup"><span data-stu-id="d6851-170">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="d6851-171">Por exemplo: **New-ComplianceSecurityFilter -Action** TODOS **-FilterName** NomeDosGerentesDeDescobertaEletronica **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d6851-171">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="d6851-172">Confira o artigo sobre o cmdlet [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para ver os parâmetros adicionais e a sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6851-172">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="d6851-173">Pesquisa de log de auditoria</span><span class="sxs-lookup"><span data-stu-id="d6851-173">Audit log search</span></span>

<span data-ttu-id="d6851-p110">Está disponível um [log de auditoria](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unificado para todas as localizações satélites na página de pesquisa de log de auditoria do Office 365. É possível ver todas as entradas do log de auditoria em diferentes localizações, por exemplo, atividades dos usuários das localizações NAM e EUR serão exibidos em um modo de exibição de organograma e você poderá aplicar os filtros existentes para ver atividades de usuários específicos.</span><span class="sxs-lookup"><span data-stu-id="d6851-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your satellite locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
