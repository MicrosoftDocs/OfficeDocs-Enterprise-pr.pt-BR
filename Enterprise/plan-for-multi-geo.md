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
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Planejar o OneDrive for Business Multi-Geo

Este guia foi criado para administradores de empresas multinacionais (MNCs) que estão Preparando seu locatário SharePoint Online para ser expandida para áreas geográficas adicionais de acordo com a presença da empresa para atender aos requisitos de residência de dados.

Em uma configuração de OneDrive Multi-Geo, seu locatário do Office 365 consiste em um local central (também conhecido como o local padrão) e um ou mais locais de geo satélite. Este é um único locatário que abrange através de vários locais geo. No OneDrive Multi-Geo, suas informações de locatário, incluindo geo locais, são administradas no Windows Azure Active Directory (AAD). 

Aqui estão alguns termos multi-geo principais para ajudá-lo a entender os conceitos básicos da configuração:

-   **Locatário** – representação de uma organização na nuvem Office 365 que geralmente tem um ou mais domínios associados a ele (por exemplo, http://contoso.sharepoint.com). 

-   **Locais de Geo** – os locais geográficos onde os dados do seu locatário estão hospedados. Multi-geo inquilinos abrangem mais de um local de geo, por exemplo, América do Norte e Europa.

-   **Locais de dados permitido (ADL)** – os locais de geo para o qual seu locatário foi configurado para hospedar dados OneDrive e o SharePoint.

-   **Localização de dados preferencial (PDL)** – o local de geo onde os dados de OneDrive de um usuário individual estão armazenados. Isso pode ser definido pelo administrador para qualquer um dos locais permitidos dados que tiverem sido configuradas para o inquilino. Observe que se você alterar o PDL para um usuário que já tem um site OneDrive, seus dados OneDrive não serão movidos para o novo local de geo automaticamente. Para obter mais informações, consulte [Mover uma biblioteca do OneDrive para uma localização geográfica diferente](move-onedrive-between-geo-locations.md) .

Habilitar Multi-Geo exige quatro etapas principais:

1.  Trabalhar com sua equipe de conta para adicionar o plano de serviço _Multi-Geo recursos no Office 365_ .

2.  Escolha seu desejada satélite geo local (is) e adicioná-los ao seu locatário.

3.  Defina o local dos dados preferencial dos usuários para o local de geo de satélite desejada. Quando um novo site de OneDrive é provisionado para um usuário, ele é provisionado para seu PDL.

4.  Migre sites de OneDrive existentes dos usuários do local da página inicial para seu local de preferência dados conforme necessário.

Consulte [Configurar o OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) para obter detalhes sobre cada uma dessas etapas.

> [!IMPORTANT]
> Observe que os recursos de Multi-Geo do Office 365 não são projetados para casos de otimização de desempenho, eles são criados para atender aos requisitos de residência de dados. Para obter informações sobre a otimização do desempenho para o Office 365, consulte [planejamento da rede e ajuste de desempenho para o Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou entre em contato com seu grupo de suporte.

Você pode configurar qualquer um dos seguintes locais para ser locais de geo satélite onde você pode hospedar arquivos OneDrive. Ao planejar para multi-geo, faça uma lista dos locais que você deseja adicionar ao seu locatário do Office 365. É recomendável iniciando com um ou dois locais de satélite e, em seguida, gradualmente expandindo para obter mais geo locais, se necessário.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Local</strong></th>
<th align="left"><strong>Código</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Pacífico Asiático</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Europa / Oriente Médio / África</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">América do Norte</td>
<td align="left">NOME</td>
</tr>
<tr class="even">
<td align="left">Austrália</td>
<td align="left">AUSTRÁLIA</td>
</tr>
<tr class="odd">
<td align="left">Canadá</td>
<td align="left">PODE</td>
</tr>
<tr class="odd">
<td align="left">Japão</td>
<td align="left">JAPONÊS</td>
</tr>
<tr class="even">
<td align="left">Coreia</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">Reino Unido</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Próximos geo locais:
  
- França
- Índia

Quando você configura multi-geo, considere aproveitando a oportunidade para consolidar sua infraestrutura local durante a migração para o Office 365. Por exemplo, se você tiver farms local em Cingapura e Malásia, em seguida, você pode consolidá-los para o local de satélite APC, desde que os requisitos de residência dados permitem que você fazê-lo.

## <a name="best-practices"></a>Práticas recomendadas

Recomendamos que você crie um usuário de teste no Office 365 para fazer algumas teste inicial. Vamos examinar algumas etapas de testes e verificações com esse usuário antes de prosseguir para o recurso de OneDrive Multi-Geo aos usuários de produção onboard.

Depois de ter concluído o teste com o usuário de teste, selecione um grupo piloto – talvez do departamento de TI – como o primeiro usar OneDrive em uma nova localização geográfica. Para esse grupo primeiro, selecione os usuários que ainda não têm um OneDrive. Recomendamos não mais de cinco pessoas neste grupo inicial e expanda gradualmente seguindo um método de distribuição em lote.

Cada usuário deve ter um *local de dados preferida* (PDL) definida para que o Office 365 pode determinar em qual local geo para provisionar seu OneDrive. Local dos dados preferencial do usuário deve corresponder a um dos seus locais de satélite escolhida ou seu local central. Enquanto o campo PDL não seja obrigatório, é recomendável que uma PDL seja definido para todos os usuários. Cargas de trabalho de um usuário sem uma PDL serão provisionadas no local central com base na lógica Multi-Geo.   

Criar uma lista de seus usuários e inclua o seu nome de usuário principal (UPN) e o código de local para o local apropriado aos dados preferencial. Inclua começar com o usuário de teste e para seu grupo piloto inicial. Você precisará desta lista para os procedimentos de configuração.

Se os usuários são sincronizados em um sistema do AD (Active Directory) no local para Windows Azure Active Directory (AAD), você deve definir a localização de dados preferida para usuários sincronizados usando o Azure Active Directory Connect. Diretamente, você não pode configurar o local de dados preferida para usuários sincronizados usando o PowerShell do Windows Azure AD. As etapas para configurar o PDL em AD e sincronizá-lo são abordadas em [sincronização do Azure Active Directory Connect: configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

A administração de um inquilino multi-geo pode diferir um locatário de não-multi-geo, como muitas das configurações do SharePoint e OneDrive e serviços são multi-geo ciente. Recomendamos que você examine [administrar um ambiente multi-geo](administering-a-multi-geo-environment.md) antes de prosseguir com sua configuração.

Leia a [experiência do usuário em um ambiente de multgeo](multi-geo-user-experience.md) para obter detalhes sobre a experiência dos usuários finais em um ambiente multi-geo.

Para começar a configuração OneDrive for Business Multi-Geo, consulte [Configurar o OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).

Depois de ter concluído a configuração, lembre-se para [migrar bibliotecas de OneDrive dos usuários](move-onedrive-between-geo-locations.md) conforme necessário para obter seus usuários trabalhando dos seus locais de dados preferida.
