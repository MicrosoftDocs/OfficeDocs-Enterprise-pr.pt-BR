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
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>Administrar um ambiente multigeográfico

Veja aqui um resumo de como funcionam os serviços do OneDrive e do SharePoint em um ambiente multigeográfico.

#### <a name="onedrive-administrator-experience"></a>Experiência de Administrador do OneDrive

O [Centro de Administração do OneDrive](https://admin.onedrive.com) tem uma guia de **localizações geográficas** na navegação à esquerda, que apresenta um mapa com os locais onde é possível exibir e gerenciar suas localizações geográficas. Use essa página para adicionar ou excluir as localizações geográficas de seu locatário.

#### <a name="taxonomy"></a>Taxonomia

Oferecemos suporte para uma [taxonomia](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificada para os metadados gerenciados da empresa em diferentes locais, mantendo os dados-mestre hospedados na localização central de sua empresa. Recomendamos que você gerencie sua taxonomia global do local central e adicione apenas termos específicos para cada localização à Taxonomia das localização geográficas no satélite. Os termos da taxonomia global serão sincronizadas nas localizações geográficas no satélite.

#### <a name="sharing"></a>Compartilhamento

Os administradores podem definir e gerenciar as políticas de compartilhamento para cada uma das localizações. Os sites do OneDrive em cada localização geográfica respeitará apenas as configurações de compartilhamento específicas para aquela localização. (Por exemplo, você pode permitir o [compartilhamento externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) na localização central, mas não na localização por satélite ou vice-versa). As configurações de compartilhamento, no entanto, não permitem configurar limitações de compartilhamento entre localizações geográficas.

Para a OneDrive com Funcionalidades Multigeográficas, você deve gerenciar as configurações de compartilhamento em cada localização geográfica, pois essas não são sincronizadas no locatário. Para gerenciar o compartilhamento, acesse a página de [configurações de compartilhamento no Centro de Administração do OneDrive](https://admin.onedrive.com/?v=SharingSettings). Por padrão, o compartilhamento externo é habilitado para Qualquer Pessoa em todas as localizações no satélite.

#### <a name="user-profile-application"></a>Aplicativo de Perfil de Usuário

Há um [aplicativo de perfil de usuário](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) em cada localização geográfica. As informações de perfil de cada usuário estão hospedadas na localização geográfica dele e ficam disponíveis para o administrador daquela localização.

Se houver propriedades de perfil personalizadas, recomendamos que você use o mesmo esquema de perfil nas localizações e popule as propriedades personalizadas em cada uma delas ou nas que forem necessárias. Para obter mais orientações sobre como popular de forma programática os dados de perfil de usuário, consultes as informações sobre a [API de Atualização de Perfil de Usuário em Massa](https://docs.microsoft.com/pt-BR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

#### <a name="bcs-secure-store-apps"></a>BCS, Repositório Seguro, Aplicativos

A BCS, o Repositório Seguro e os Aplicativos têm instâncias geográficas separadas, portanto, o administrador do SharePoint Online deve gerenciar e configurar esses serviços em cada instância geográfica onde ele quer que esses recursos apareçam.

#### <a name="security-and-compliance-admin-center"></a>Centro de Administração de Conformidade e Segurança

Há um centro de conformidade central para o locatário multigeográfico: [Centro de conformidade e segurança do Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Política de Prevenção contra Perda de Dados (DLP) e Proteção da Informação (IP). 

Você pode configurar as políticas de DLP e IP para o OneDrive for Business no Centro de Segurança e Conformidade, examinando com cuidado as políticas conforme necessário para o locatário inteiro ou para os usuários que precisarem. Por exemplo: se desejar selecionar uma política para um usuário do OneDrive em uma localização no satélite, selecione-a para aplicar a política em um OneDrive específico e insira a url do OneDrive do usuário. Consulte a [visão geral das políticas de prevenção contra perda de dados](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para obter instruções gerais para a criação de políticas de DLP.

As políticas de DLP são sincronizadas automaticamente de acordo com a aplicabilidade delas a cada localização geográfica.

A implementação de políticas de Prevenção contra Perda de Dados e Proteção da Informação para todos os usuários em uma localização geográfica não é uma opção disponível na IU. Em vez disso, é preciso selecionar as contas do OneDrive em que deseja aplicar a política ou aplicá-la de modo global a todas as contas do OneDrive. 

#### <a name="ediscovery"></a>Descoberta Eletrônica 

Por padrão, o gerente ou administrador de Descoberta Eletrônica de um locatário multigeográfico poderá realizar a Descoberta Eletrônica apenas na localização central desse locatário. Para poder realizar a descoberta eletrônica nas localizações no satélite, está disponível, no PowerShell, um novo parâmetro de Filtro de Segurança de Conformidade, chamado "Região".

O administrador global do Office 365 deve atribuir permissões de gerente de Descoberta Eletrônica para permitir que outras pessoas possam realizá-la e atribuir o parâmetro "Região" no Filtro de Segurança e Conformidade deles, para especificar a região como uma localização no satélite para a realização da Descoberta. Caso contrário, a Descoberta Eletrônica não será realizada para nenhuma localização no satélite.

Quando a função de gerente ou administrador de Descoberta Eletrônica é definida para uma determinada localização geográfica, o gerente ou o administrador só poderá realizar ações de pesquisa em sites do SharePoint e do OneDrive naquela localização geográfica. Se ele tentar pesquisar sites do SharePoint ou do OneDrive fora da região especificada, nenhum resultado será apresentado. Além disso, quando o gerente ou administrador da Descoberta de uma região aciona uma exportação, os dados são exportados para a instância do Azure daquela região. Isso ajuda as organizações a permanecerem em conformidade, não permitindo que o conteúdo seja exportado para além de fronteiras controladas.

> [!NOTE]
> Caso seja necessário que o gerente de Descoberta Eletrônica pesquise diversas regiões no SharePoint, será necessário criar outra conta de usuário para ele, a qual especifique a região alternativa em que os sites do OneDrive ou do SharePoint estão localizados.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Localizações geográficas em que a Multigeografia é suportada</strong></th>
<th align="left"><strong>A Descoberta eletrônica para os dados exportados do SharePoint estará nesta localização de dados do Blob do Azure...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">Data centers nos EUA</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">Data centers na Europa</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Data centers no Sudeste ou Leste da Ásia</td>
</tr>
<tr class="even">
<td align="left"><strong>CAN</strong></td>
<td align="left">Data centers nos EUA</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">Data centers no Sudeste ou Leste da Ásia</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">Local de dados-padrão do locatário</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Data centers na Europa</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN </strong></td>
<td align="left">Data centers no Sudeste ou Leste da Ásia</td>
</tr>
</tbody>
</table>

Para configurar o Filtro de Segurança de Conformidade para uma região:

1.  Abra o Windows PowerShell

2.  Digite  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** TODOS **-FilterName** InsiraONomeParaOQualDesejaAtribuir **-Region** InsiraOParâmetroDeRegiao **-Users** InsiraONomePrincipalDoUsuario

    Por exemplo: **New-ComplianceSecurityFilter -Action** TODOS **-FilterName** NomeDosGerentesDeDescobertaEletronica **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

Confira o artigo sobre o cmdlet [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para ver os parâmetros adicionais e a sintaxe

#### <a name="audit-log-search"></a>Pesquisa de log de auditoria

Está disponível um [log de auditoria](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unificado para todas as localizações geográficas na página de pesquisa de log de auditoria do Office 365. É possível ver todas as entradas do log de auditoria em diferentes localizações, por exemplo, atividades dos usuários das localizações NAM e EUR serão exibidos em um modo de exibição de organograma e você poderá aplicar os filtros existentes para ver atividades de usuários específicos.
