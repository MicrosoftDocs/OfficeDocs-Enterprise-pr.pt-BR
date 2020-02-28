---
title: Plano para o Office 365 multigeográfico
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Saiba mais sobre o Office 365 multigeográfico, como a funcionalidade multigeográfica funciona e quais localizações geográficas estão disponíveis para o armazenamento de dados.
ms.openlocfilehash: 2875f820b0ce1437a09289e3c5e660287b64dc40
ms.sourcegitcommit: 6ad59ab24a5dc8d27f448ca7fe4f6bdf7ab28066
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "42316000"
---
# <a name="plan-for-office-365-multi-geo"></a>Plano para o Office 365 multigeográfico

Este guia foi projetado para os administradores de empresas multinacionais (MNCs) que estão preparando o locatário do Office 365 para ser expandido para outras regiões de acordo com a presença da empresa para atender aos requisitos de residência dos dados.

Em uma configuração multigeográfica, o locatário do Office 365 consiste em uma localização central e uma ou mais localizações geográficas de satélite. Este é um locatário único que se estende em várias localizações geográficas. Suas informações de locatário, incluindo localizações geográficas, são armazenadas no Azure Active Directory (AAD).

Vejamos alguns termos chave da multigeografia que o ajudarão a entender os conceitos básicos da configuração:

-   **Locatário** – A representação de uma organização no Office 365 que geralmente tem um ou mais domínios associados (por exemplo, https://contoso.sharepoint.com). 

-   **Localizações geográficas** – Localizações geográficas disponíveis para hospedar os dados em um locatário do Office 365.

-   **Locais de satélite** – Localizações geográficas adicionais configuradas para hospedar dados em seu locatário do Office 365. Locatários multigeográficos abrangem mais do que uma localização geográfica, por exemplo, América do Norte e Europa.

-   **Local de Dados Preferencial (PDL)** – A localização geográfica onde os dados do OneDrive e do usuário individual do Exchange são armazenados. Isso pode ser definido pelo administrador, m qualquer localização geográfica configurada para o locatário. Observe que se você alterar a PDL para um usuário que já tenha um site do OneDrive, seus dados do OneDrive não serão movidos para a nova localização geográfica automaticamente. Confira [Mover uma biblioteca do OneDrive para uma localização geográfica diferente](move-onedrive-between-geo-locations.md) para saber mais. Se houver uma caixa de correio do Exchange, a caixa de correio é movida para o novo local de dados preferencial automaticamente.

Habilitar a multigeografia requer quatro etapas principais:

1.  Trabalhe com a sua equipe de conta para adicionar o plano de serviço _Funcionalidades multigeográficas no Office 365_.

2.  Escolha a(s) localização(ões) geográfica(s) satélite(s) desejada(s) e adicione-a(s) ao seu locatário.

3.  Defina o local preferencial dos dados dos usuários para a localização de satélite desejada. Quando um novo site do OneDrive ou caixa de correio do Exchange está provisionada para um usuário, está provisionado para sua PDL.

4.  Migre os seus sites existentes do OneDrive dos usuários do local central para o local de dados preferencial conforme necessário. (As caixas de correio do Exchange são migradas automaticamente quando você define o PDL do usuário.)

Ver [Configurar o Office 365 multigeográfico](multi-geo-tenant-configuration.md) para obter detalhes sobre cada uma dessas etapas.

> [!IMPORTANT]
> Observe que o Office 365 multigeográfico não foi desenvolvido para otimizar o desempenho, foi projetado para atender aos requisitos de residência de dados. Para saber mais sobre a otimização do desempenho do Office 365, confira [Planejamento de rede e ajuste de desempenho do Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou fale com o suporte.

Você pode configurar qualquer uma das seguintes localizações para ser de satélite onde você pode hospedar o OneDrive, sites do SharePoint e caixas de correio do Exchange. Ao planejar multigeográfico, crie uma lista de locais que você deseja adicionar ao seu locatário do Office 365. Recomendamos começar com um ou dois locais de satélite e expandir gradualmente para mais localizações geográficas, se necessário.

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

Ao configurar a multigeografia, considere aproveitar a oportunidade de consolidar a sua infraestrutura local ao migrar para o Office 365. Por exemplo, se você tiver farms locais em Cingapura e na Malásia, poderá consolidá-los para a localização satélite de APC, desde que os requisitos de residência de dados permitam isso.

## <a name="best-practices"></a>Práticas recomendadas

Recomendamos que você criie um usuário de teste no Office 365 para executar alguns testes iniciais. Vamos executar algumas etapas de teste e verificação com esse usuário antes de prosseguir para os usuários de produção no Office 365 multigeográfico.

Depois de concluir os testes com o usuário de teste, selecione um grupo piloto – talvez do departamento de TI – para ser o primeiro a usar o OneDrive e o Exchange em uma nova localização geográfica. Para esse primeiro grupo, selecione os usuários que ainda não tem do OneDrive. É recomendável não mais do que cinco pessoas neste grupo inicial e expanda-o gradualmente seguindo uma abordagem de implantação em lote.

Cada usuário deve ter um *local de dados preferencial* (PDL) definido para que o Office 365 possa determinar em qual localização geográfica provisionar o OneDrive. O local de dados preferencial do usuário deve corresponder a um de seus locais satélites escolhidos ou ao local central. Embora o campo PDL não seja obrigatório, é recomendável que um PDL seja definido para todos os usuários. As cargas de trabalho de um usuário sem um PDL serão provisionadas no local central.

Crie uma lista dos seus usuários e inclua o nome UPN e o código de local para o local de dados preferencial adequado. Inclua o seu usuário de teste e o seu grupo piloto inicial para começar. Você precisará dessa lista para os procedimentos de configuração.

Se os usuários serão sincronizados com um sistema do Active Directory local ao Azure Active Directory, você deve definir o local de dados preferencial como um atributo Active Directory e sincronizá-lo usando o Azure Active Directory Connect. Você não pode configurar o local de dados preferencial diretamente para os usuários sincronizados usando o Azure AD PowerShell. As etapas para configurar o PDL no Active Directory e sincronizá-lo são descritas em [Sincronização do Azure Active Directory Connect: Configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

A administração de um locatário multigeográfico pode variar de um locatário que não seja de multigeografia, pois muitos dos serviços e configurações do SharePoint e do OneDrive detectam a multigeografia. Recomendamos que leia [Administrar um ambiente multigeográfico](administering-a-multi-geo-environment.md) antes de prosseguir com a configuração.

Leia em [Experiência do usuário em um ambiente multigeográfico](multi-geo-user-experience.md) detalhes sobre a experiência dos usuários finais em um ambiente multigeográfico.

Para obter detalhes sobre a experiência do Teams em uma locação multigeográfica do Office 365, consulte [Experiência do Teams em uma locação multigeográfica do Office 365, OneDrive e SharePoint Online](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo).

Para começar a configurar o Office 365 Multigeográfico, confira [Configurar o Office 365 Multigeográfico](multi-geo-tenant-configuration.md).

Depois de concluir a configuração, lembre-se de [migrar as bibliotecas do OneDrive dos seus usuários](move-onedrive-between-geo-locations.md) conforme necessário para que os usuários possam trabalhar dos locais de dados preferenciais.
