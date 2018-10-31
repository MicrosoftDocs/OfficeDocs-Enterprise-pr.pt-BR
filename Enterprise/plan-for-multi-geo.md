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
ms.openlocfilehash: d40f84ea3636b4eca2711a48bd9d70c73a242cfd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849857"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Planejar o OneDrive for Business com a funcionalidade multigeográfica

Este guia foi projetado para os administradores de empresas multinacionais (MNCs) que estão preparando o locatário do SharePoint Online para ser expandido para outras regiões de acordo com a presença da empresa para atender aos requisitos de residência de dados.

Em uma configuração multigeográfica do OneDrive, o seu locatário do Office 365 consiste em um local central e uma ou mais localizações geográficas satélites. Este é um único locatário que se distribui em várias localizações geográficas. No OneDrive com a funcionalidade multigeográfica, as suas informações de locatário, incluindo as localizações geográficas, são controladas no Azure Active Directory (AAD). 

Vejamos alguns termos da multigeografia que o ajudarão a entender os conceitos básicos da configuração:

-   **Locatário** – A representação de uma organização na nuvem do Office 365 que geralmente tem um ou mais domínios associados (por exemplo, http://contoso.sharepoint.com). 

-   **Localizações geográficas** – locais geográficos disponíveis para hospedar os dados em um locatário do Office 365.

-   **Localizações geográficas** – As localizações geográficas que você configurou para hospedarem os dados de seu locatário do Office 365. Os locatários multigeográficos abrangem mais de uma localização geográfica, por exemplo, América do Norte e Europa.

-   **Local de dados preferencial (PDL)** – A localização geográfica onde são armazenados os dados do OneDrive de um usuário individual. Isso pode ser definido pelo administrador como qualquer um dos locais de dados permitidos que foram configurados para o locatário. Se você alterar o PDL para um usuário que já tenha um site do OneDrive, os dados do OneDrive não serão movidos para a nova localização geográfica automaticamente. Veja mais informações em [Mover uma biblioteca do OneDrive para uma localização geográfica diferente](move-onedrive-between-geo-locations.md).

Habilitar a multigeografia requer quatro etapas principais:

1.  Trabalhe com a sua equipe de conta para adicionar o plano de serviço _Funcionalidades multigeográficas no Office 365_.

2.  Escolha a(s) localização(ões) geográfica(s) satélite(s) desejada(s) e adicione-a(s) ao seu locatário.

3.  Defina seu local de dados preferencial dos usuários na localização satélite desejada. Quando um novo site do OneDrive é provisionado para um usuário, ele é provisionado para o PDL dele.

4.  Migre os seus sites existentes do OneDrive dos usuários do local central para o local de dados preferencial conforme necessário.

Veja em [Configurar o OneDrive for Business com a funcionalidade multigeográfica](multi-geo-tenant-configuration.md) detalhes sobre cada uma dessas etapas.

> [!IMPORTANT]
> Observe que as funcionalidades multigeográficas do Office 365 não foram criadas para casos de otimização de desempenho, mas sim para atender aos requisitos de residência de dados. Para saber mais sobre a otimização de desempenho do Office 365, confira [Planejamento de rede e ajuste de desempenho para o Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou fale com o grupo de suporte.

Você pode configurar qualquer um dos seguintes locais como localizações geográficas satélites onde você pode hospedar arquivos do OneDrive. Ao planejar a multigeografia, crie uma lista das localizações que você deseja adicionar ao seu locatário do Office 365. Recomendamos começar com uma ou duas localizações satélites e, depois, ir expandindo gradualmente para mais localizações, se necessário.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Localização</strong></th>
<th align="left"><strong>Código</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Ásia – Pacífico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Austrália</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Canadá</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">Europa/Oriente Médio/África</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">França</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">Japão</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Coreia</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">América do Norte</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">Reino Unido</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Localizações geográficas futuras:
  
- Índia

Ao configurar a multigeografia, considere aproveitar a oportunidade de consolidar a sua infraestrutura local ao migrar para o Office 365. Por exemplo, se você tiver farms locais em Cingapura e na Malásia, poderá consolidá-los para a localização satélite de APC, desde que os requisitos de residência de dados permitam isso.

## <a name="best-practices"></a>Práticas recomendadas

Recomendamos que você crie um usuário de teste no Office 365 para executar alguns testes iniciais. Você passará por algumas etapas de teste e verificação com esse usuário antes de prosseguir para a integração de usuários de produção no recurso de multigeografia do OneDrive.

Depois de concluir os testes com o usuário de teste, selecione um grupo piloto, talvez do departamento de TI, como o primeiro a usar o OneDrive em uma nova localização geográfica. Para este primeiro grupo, selecione os usuários que ainda não têm o OneDrive. Recomendamos no máximo cinco pessoas nesse grupo inicial e, depois, que se expanda gradualmente seguindo uma abordagem de implantação em lote.

Cada usuário deve ter um *local de dados preferencial* (PDL) definido para que o Office 365 possa determinar em qual localização geográfica provisionar o OneDrive. O local de dados preferencial do usuário deve coincidir com um dos seus locais satélites escolhidos ou com o local central. Embora o campo PDL não seja obrigatório, é recomendável que um PDL seja definido para todos os usuários. As cargas de trabalho de um usuário sem um PDL serão provisionadas no local central.   

Crie uma lista dos seus usuários e inclua o nome de usuário principal (UPN) e o código de local para o local de dados preferencial adequado. Inclua o seu usuário de teste e o seu grupo piloto inicial para começar. Você precisará dessa lista para os procedimentos de configuração.

Se os usuários forem sincronizados de um sistema local do Active Directory (AD) para o Azure Active Directory (AAD), você deverá definir o local de dados preferencial para os usuários sincronizados usando o Azure Active Directory Connect. Diretamente, você não poderá configurar o local de dados preferencial para os usuários sincronizados usando o PowerShell do Azure AD. As etapas para se configurar o PDL no AD e sincronizá-lo estão descritas em [Sincronização do Azure Active Directory Connect: Configurar o local de dados preferencial para os recursos do Office 365](https://docs.microsoft.com/pt-BR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

A administração de um locatário multigeográfico pode variar de um locatário que não seja de multigeografia, pois muitos dos serviços e configurações do SharePoint e do OneDrive detectam a multigeografia. Recomendamos que leia [Administrar um ambiente multigeográfico](administering-a-multi-geo-environment.md) antes de prosseguir com a configuração.

Leia em [Experiência do usuário em um ambiente multigeográfico](multi-geo-user-experience.md) detalhes sobre a experiência dos usuários finais em um ambiente multigeográfico.

Para começar a configurar o OneDrive for Business com a funcionalidade multigeográfica, confira [Configurar o OneDrive for Business com a funcionalidade multigeográfica](multi-geo-tenant-configuration.md).

Depois de concluir a configuração, lembre-se de [migrar as bibliotecas do OneDrive dos seus usuários](move-onedrive-between-geo-locations.md) conforme necessário para que os usuários possam trabalhar dos locais de dados preferenciais.
