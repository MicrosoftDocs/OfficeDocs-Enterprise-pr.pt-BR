---
title: Experiência do usuário em um ambiente multigeográfico
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
description: Saiba mais sobre a experiência do usuário do SharePoint e do OneDrive em um ambiente multigeográfico.
ms.openlocfilehash: 951efb636ce00f59393f624687d44a406fcf3fc0
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849827"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Experiência do usuário em um ambiente multigeográfico

Vejamos a seguir o que os usuários verão em uma configuração multigeográfica do OneDrive:

#### <a name="users-onedrive-for-business-location"></a>Local do OneDrive for Business do usuário

Os usuários terão o OneDrive for Business provisionado em sua localização dados preferida. Se um usuário navegar para uma URL do OneDrive com uma localização geográfica incorreta (por exemplo, um indicador de uma localização geográfica anterior), eles serão redirecionados automaticamente para o OneDrive na localização geográfica adequada.

#### <a name="sharing"></a>Compartilhamento

A experiência do Seletor de Pessoas mostra todos os usuários independentemente da localização geográfica. Isso permite que um usuário compartilhe com outro usuário, em sua mesma localização geográfica ou em qualquer outra localização do seu locatário. O conteúdo de localizações geográficas diferentes será exibido na visualização **Compartilhado comigo** no OneDrive for Business do usuário, e poderá ser acessado com a experiência de logon único, independentemente de em qual localização geográfica estiver hospedado.

#### <a name="office-applications"></a>Aplicativos do Office

Os aplicativos do Office como o Word, o Excel e o PowerPoint detectarão automaticamente a localização geográfica correta do OneDrive for Business para todos os usuários ao entrarem. Os usuários não precisam inserir a URL do OneDrive específica do local.

#### <a name="onedrive-for-business-sync-client"></a>Cliente de sincronização do OneDrive for Business

O cliente de sincronização do OneDrive for Business (versão 17.3.6943.0625 e posteriores) detectará automaticamente a localização geográfica correta do OneDrive for Business para o usuário.

#### <a name="office-365-app-launcher"></a>Inicializador de aplicativos do Office 365

O inicializador de aplicativos reconhece localizações geográficas diferentes e direcionará cada bloco para a localização geográfica adequada da carga de trabalho. O bloco do OneDrive aponta para a localização geográfica correta na qual a biblioteca do OneDrive do usuário está hospedada, ao passo que o bloco do SharePoint apontará todos os usuários para o local central, pois os sites de equipe ainda estão hospedados lá.

#### <a name="delve-user-profiles"></a>Perfis do usuário Delve

As informações de perfil de usuário são controladas na localização geográfica do usuário. Ao selecionar um usuário, você será direcionado para a localização geográfica adequada do usuário, onde você verá os detalhes do perfil completos dele.

Se o Delve estiver desativado, você verá a experiência de perfil clássica no SharePoint, que não reconhece diferentes localizações geográficas.

#### <a name="delve"></a>Delve

Para os usuários do Office 365 que estão nas instâncias-satélites, a multigeografia do Delve tem suporte, com a limitação de que o Delve não contém ligação para postagens de blog do SharePoint escritas por usuários em outras regiões, apenas para os sites de blog do SharePoint.

#### <a name="search"></a>Pesquisar

Cada localização geográfica tem o seu próprio índice de pesquisa e Centro de pesquisa. Quando um usuário faz uma pesquisa, a consulta é enviada a todas as localizações geográficas e os resultados retornados são mesclados e, depois, classificados de modo que o usuário obtenha resultados unificados. Os usuários obtêm resultados de todas as localizações geográfica independentemente da sua própria localização. Leia informações específicas em [Configurar a pesquisa do OneDrive for Business com Funcionalidade Multigeográfica](configure-search-for-multi-geo.md).

Há suporte para os seguintes clientes de pesquisa:

-   OneDrive for Business

-   Delve

-   Página inicial do SharePoint

-   O Centro de Pesquisa

-   Aplicativos de pesquisa personalizada que usam a API de pesquisa do SharePoint

#### <a name="onedrive-ios-and-android"></a>OneDrive para iOS e Android 

Os aplicativos móveis do OneDrive para iOS e Android mostrarão os seus arquivos do OneDrive e arquivos compartilhados com você, independentemente da localização geográfica deles. A pesquisa dos aplicativos móveis do OneDrive mostrará resultados relevantes de todas as localizações geográficas. Baixe a versão mais recente desses aplicativos.

Confira mais informações em [Usar o OneDrive para iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) e [Usar o OneDrive para Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36).

#### <a name="teams-experience"></a>Experiência do Teams

O Teams reconhece localizações geográficas diferentes. Os arquivos do OneDrive e os arquivos visualizados recentemente são mostrados independentemente da localização geográfica do usuário. As menções com @ funcionam com usuários de todas as localizações.
