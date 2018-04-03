---
title: Experiência do usuário em um ambiente de multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba mais sobre a experiência do usuário do SharePoint e OneDrive em um ambiente multi-geo.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Experiência do usuário em um ambiente multi-geo

Aqui está o que os usuários verão em uma configuração de OneDrive Multi-Geo:

#### <a name="users-onedrive-for-business-location"></a>OneDrive do usuário para o local da empresa

Os usuários terão sua OneDrive for Business provisionado no seu local de dados preferida. Se um usuário navega até um URL de OneDrive que contém uma localização geográfica incorreta (por exemplo, um indicador de um local de geo anterior), eles serão automaticamente redirecionados para o OneDrive no geo-local apropriado.

#### <a name="sharing"></a>Compartilhando

A experiência do People Picker mostra todos os usuários onde quer que estejam geo. Isso permite que um usuário compartilhar com outro usuário em seu geo mesmo ou em qualquer um dos outros locais de localização geográfica do seu locatário. Conteúdo de diferente geo locais serão exibidas no modo de exibição **compartilhou** no OneDrive do usuário for Business e podem ser acessados com experiência de Single-Sign-On independentemente de qual geo-local está hospedada no.

#### <a name="office-applications"></a>Aplicativos do Office

Aplicativos do Office como Word, Excel e PowerPoint detectará automaticamente o correto OneDrive for Business geo-local para cada usuário quando fazem logon. Os usuários não precisam digitar a URL de geo específica para sua OneDrive.

#### <a name="onedrive-for-business-sync-client"></a>OneDrive for Business cliente de sincronização

O OneDrive for Business cliente de sincronização (versão 17.3.6943.0625 e posterior) detectará automaticamente o OneDrive correto para o local da empresa geo para o usuário.

#### <a name="office-365-app-launcher"></a>Inicializador de aplicativos do Office 365

O iniciador app está ciente Multi-Geo e direcionará cada lado a lado para o local apropriado geo da carga de trabalho. Os pontos de blocos de OneDrive para o local correto geo onde a biblioteca do OneDrive do usuário está hospedada, enquanto a lado a lado SharePoint apontará todos os usuários para o local central, como sites de equipe ainda estejam hospedados lá.

#### <a name="delve-user-profiles"></a>Me aprofundar perfis de usuário

Informações de perfil de usuário são administradas no local de geo do usuário. Ao selecionar um usuário, você será direcionado para o local de geo apropriado para o usuário, onde você verá seus detalhes de perfil completo.

Se Delve estiver desativada, você verá o perfil clássico experiência no SharePoint, que não é multi-geo ciente.

#### <a name="delve"></a>Delve

Para usuários do Office 365 que estiverem nas instâncias de satélite, Multi-Geo me aprofundar é suportado, com a limitação que são Delve não vinculados a postagens de blog do SharePoint escritas por usuários de outras regiões, apenas aos seus sites de blog do SharePoint.

#### <a name="search"></a>Pesquisa

Cada local geo tem seus próprios índice de pesquisa e o Centro de pesquisa. Quando um usuário procura, a consulta é enviada para todos os locais de geo e resultados retornados são mesclados e, em seguida, classificados para que o usuário obtém resultados unificados. Os usuários obtém os resultados de todos os locais de geo onde quer que estejam suas próprias geo. Consulte [Configurar a pesquisa do OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) para obter informações específicas.

Há suporte para os seguintes clientes de pesquisa:

-   OneDrive for Business

-   Delve

-   Página inicial do SharePoint

-   Centro de pesquisa

-   Aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS e Android 

O iOS OneDrive e aplicativos móveis Android mostrará seus arquivos de OneDrive e os arquivos compartilhados com você, independente da sua localização geográfica. Pesquisa de aplicativos móveis OneDrive mostrará resultados relevantes de todos os locais de geo. Baixe a versão mais recente desses aplicativos.

Para obter mais informações, consulte Use [OneDrive em iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) e [Uso do OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .

#### <a name="teams-experience"></a>Experiência de equipes

As equipes é multi-geo ciente. Arquivos de OneDrive e visualizadas recentemente são mostrados, independentemente da localização do geo do usuário. @ menções o trabalho com usuários de todos os locais de geo.
