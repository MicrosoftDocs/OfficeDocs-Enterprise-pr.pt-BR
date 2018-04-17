---
title: Administrando um ambiente multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Saiba mais sobre a administração dos serviços do SharePoint e OneDrive em um ambiente multi-geo.
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a>Administrando um ambiente multi-geo

Aqui está uma olhada em como os serviços de OneDrive e o SharePoint funcionam em um ambiente multi-geo.

#### <a name="onedrive-administrator-experience"></a>Experiência do administrador do OneDrive

O [Centro de administração do OneDrive](https://admin.onedrive.com) tem uma guia **Geo locais** na navegação esquerda, quais recursos um geo-locais mapeiam onde você pode exibir e gerenciar seus locais geo. Use esta página para adicionar ou excluir locais geo para seu locatário.

#### <a name="taxonomy"></a>Taxonomia

Oferecemos suporte uma unificada [taxonomia](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) para metadados corporativos gerenciados entre localidades geo, com o mestre que está sendo hospedado no local central para sua empresa. Recomendamos que você gerenciar seu taxonomia global do local central e apenas Adicione termos específicos do local para taxonomia do local geo de satélite. Termos de taxonomia global serão sincronizadas com os locais de geo satélite.

#### <a name="sharing"></a>Compartilhamento

Os administradores podem definir e gerenciar políticas de compartilhamento para cada um dos seus locais. Os sites de OneDrive em cada local geo aceita somente as correspondente geo compartilhamento configurações específicas. Por exemplo, você pode permitir o [compartilhamento externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) de seu local central, mas não para sua satélite local ou vice-versa. Para o OneDrive Multi-Geo, você deve gerenciar suas configurações de compartilhamento em cada local geo como essas não são sincronizadas entre o inquilino.

Para gerenciar o compartilhamento visitar a página do [Centro de administração do OneDrive configurações de compartilhamento](https://admin.onedrive.com/?v=SharingSettings) . Compartilhamento externo está habilitado por padrão com qualquer pessoa em cada local de satélite.

#### <a name="user-profile-application"></a>Aplicativo de perfil de usuário

Existe um [aplicativo de perfil de usuário](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) em cada local geo. Informações de perfil de cada usuário são hospedadas em sua localização geográfica e disponíveis para o administrador para esse local geo.

Se você tiver propriedades de perfil personalizadas, depois, é recomendável que você use o mesmo esquema de perfil entre regiões geográficas e preenche suas propriedades de perfil personalizadas tanto em todos os locais de geo ou onde for necessário.

#### <a name="bcs-secure-store-apps"></a>Aplicativos do BCS, repositório seguro,

BCS, repositório seguro e aplicativos tiverem instâncias de geo separado, portanto, o administrador do SharePoint Online deve gerenciar e configurar esses serviços de cada instância geo onde eles desejam estar presentes.

#### <a name="security-and-compliance-admin-center"></a>Segurança e conformidade Centro de administração

Não há um centro de conformidade central para o locatário Multi-Geo: [Centro de conformidade e segurança do Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Diretiva Prevention (DLP) de perda de dados do informações proteção (IP)

Você pode definir seu DLP IP políticas do OneDrive for Business na Central de segurança e conformidade, políticas de escopo, conforme necessário para o inquilino todo ou usuários aplicáveis. Por exemplo: se você deseja selecionar uma política para um usuário OneDrive em um local de satélite, selecione esta opção para aplicar a política a um OneDrive específico e insira o usuário do OneDrive url. Consulte [Visão geral das políticas de prevenção de perda de dados](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para orientação geral na criação de políticas de DLP.

As políticas DLP são automaticamente sincronizadas com base na sua capacidade de aplicação para cada local geo.

A implementação de políticas de prevenção de perda de dados e de proteção de informações para todos os usuários em um local de geo não é uma opção disponível na interface de usuário, em vez disso, você deve selecionar as contas de OneDrive aplicáveis para a política ou aplicar a política globalmente a todas as contas do OneDrive.

#### <a name="ediscovery"></a>eDiscovery 

Por padrão, uma descoberta eletrônica gerente ou administrador de um inquilino multi-geo será capaz de realizar o eDiscovery apenas no local central desse inquilino. Para oferecer suporte a capacidade de realizar o eDiscovery para locais de satélite, um novo parâmetro de filtro de segurança de conformidade chamado "Region" está disponível por meio do PowerShell.

O administrador global do Office 365 deve atribuir permissões de gerente de descoberta eletrônica para permitir que outras pessoas executar a descoberta eletrônica e atribuir um parâmetro "Region" em seu filtro de segurança de conformidade aplicável para especificar a região para a realização de descoberta eletrônica como satélite local, caso contrário que nenhum eDiscovery será realizada para o local de satélite.

Quando a função de gerente ou administrador de descoberta eletrônica é definida para um local específico-geo, o eDiscovery, gerente ou administrador só poderá executar ações de pesquisa de descoberta eletrônica contra os sites do SharePoint e sites de OneDrive localizados naquele geo-local. Se um administrador ou um gerente de descoberta eletrônica tenta pesquisar sites SharePoint ou OneDrive fora da região especificada, nenhum resultado será retornado. Além disso, quando o eDiscovery gerente ou administrador para uma região dispara uma exportação, os dados são exportados para a instância Azure da região. Isso ajuda as organizações a manter a conformidade não permitindo que o conteúdo a ser exportado entre as fronteiras controladas.

> [!NOTE]
> Se for necessário para um gerente para pesquisar em várias regiões SharePoint eDiscovery, outra conta de usuário precisará ser criado para o eDiscovery Manager que especifica a região alternativa onde os sites OneDrive ou do SharePoint estão localizados.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Multi-Geo suportado Geo locais</strong></th>
<th align="left"><strong>eDiscovery para SharePoint exportados dados será neste local de dados Blob Azure …</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NOME</strong></td>
<td align="left">Centros de dados dos EUA</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">Centros de dados Europa</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Sul Leste ou centros de dados do Leste Asiático</td>
</tr>
<tr class="even">
<td align="left"><strong>PODE</strong></td>
<td align="left">Centros de dados dos EUA</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUSTRÁLIA</strong></td>
<td align="left">Sul Leste ou centros de dados do Leste Asiático</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">Localização de dados padrão de locatário</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Centros de dados Europa</td>
</tr>
<tr class="even">
<td align="left"><strong>JAPONÊS</strong></td>
<td align="left">Sul Leste ou centros de dados do Leste Asiático</td>
</tr>
</tbody>
</table>

Para definir o filtro de segurança de conformidade para uma região:

1.  Abrir o Windows PowerShell

2.  Insira   
    $s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred-autenticação básica - AllowRedirection - SessionOption (New-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)

    $um = Import-PSSession $s - AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Ação** Todos os EnterTheNameYouWantToAssign de **-FilterName** **-região** EnterTheRegionParameter **-usuários** EnterTheUserPrincipalName

    Por exemplo: **New-ComplianceSecurityFilter-ação** NAMEDISCOVERYMANAGERS de todos os **- FilterName** **-região** NAM **-usuários** adwood@contosodemosx.onmicrosoft.com

Consulte o artigo de [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para sintaxe e parâmetros adicionais

#### <a name="audit-log-search"></a>Pesquisa de log de auditoria

Um unificada de [log de auditoria](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) para todos os seus locais geo está disponível de página de pesquisa de log de auditoria do Office 365. Você pode ver todas as entradas de log de auditoria de entre geos, por exemplo, EUR & me geo as atividades dos usuários serão exibidas em um modo de exibição de organização e, em seguida, você pode aplicar filtros existentes para ver as atividades do usuário específico.
