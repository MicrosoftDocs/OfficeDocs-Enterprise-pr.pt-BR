---
title: Office 365 multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Expanda a sua presença do Office 365 para várias regiões geográficas com o Office 365 multigeográfico.
ms.openlocfilehash: e216f61806ea5d648519ac7217acf7dbaddd1419
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933930"
---
# <a name="office-365-multi-geo"></a>Office 365 multigeográfico

Com o Office 365 multigeográfico, sua organização poderá expandir sua presença do Office 365 para várias regiões geográficas e/ou os países em seu locatário existente. Entre em contato com sua equipe de conta da Microsoft para inscrever sua empresa multinacional para o Office 365 multigeográfico.
  
Com o Office 365 multigeográfico, você pode provisionar e armazenar dados em repouso nas localizações geográficas escolhidas para atender aos requisitos de residência de dados e, ao mesmo tempo, dar vazão à sua implantação global a partir de experiências de produtividade modernas para a sua força de trabalho.

#### <a name="video-introducing-office-365-multi-geo"></a>Vídeo: Apresentando o Office 365 multigeográfico

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

Em um ambiente multigeográfico, seu locatário do Office 365 consiste em um local central (onde a assinatura do Office 365 originalmente foi provisionada) e um ou mais locais do satélite. Em um locatário multigeográfico, as informações sobre localizações geográficas, grupos e informações do usuário são dominadas no Azure Active Directory (AAD). Como as informações de locatário são dominadas centralmente e sincronizadas em cada localização geográfica, compartilhamento e experiências envolvendo qualquer pessoa da sua empresa contêm percepção global.

![Captura de tela do menu do centro de administração do SharePoint](media/multi-geo-world-map.png)

Observe que o Office 365 multigeográfico não foi desenvolvido para otimizar o desempenho, foi projetado para atender aos requisitos de residência de dados. Para saber mais sobre a otimização do desempenho do Office 365, confira [planejamento de rede e ajuste de desempenho do Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou Fale com o suporte.

## <a name="terminology"></a>Terminologia

Aqui estão os principais termos usados para descrever o Office 365 multigeográfico:

- **Uma localização central** -a localização geográfica onde seu locatário foi originalmente provisionado.
- **Administrador geográfico**, um administrador que pode administrar um ou mais locais do satélite especificado.
- **Geocódigo** -um código de três letras de uma localização geográfica determinada.
- **Localização geográfica** – uma localização geográfica pode ser usada em um locatário multigeográfico para hospedar dados, incluindo caixas de correio do Exchange e o OneDrive e sites do SharePoint.
- **Preferenciais de dados local (PDL)** a propriedade do usuário definido pelo administrador que indica onde a localização geográfica onde a caixa de correio do Exchange usuários e do OneDrive devem ser provisionadas. A PDL determina também onde os sites do SharePoint criados pelo usuário estão provisionados.
- **Localização de satélite** – As localizações geográficas em que as cargas de trabalho geográficas do Office 365 (SharePoint, OneDrive e Exchange) estão habilitadas em um locatário multigeográfico.
- **Locatário** – – a representação de uma organização no Office 365 que geralmente tem um ou mais domínios associados (por exemplo, contoso.com).

## <a name="office-365-multi-geo-availability"></a>Disponibilidade do Office 365 multigeográfico

A multigeografia do Office 365 atualmente é oferecida nos países e regiões seguintes:

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Introdução

Siga estas etapas para iniciar com o multigeográfico:

1. Trabalhe com a sua equipe de contas para adicionar o plano de serviço _Funcionalidades multigeográficos no Office 365_. Ela dará instruções sobre a adição do número de licenças necessárias.

   Antes de começar a usar o Office 365 multigeográfico, a Microsoft precisa configurar seu locatário do Exchange Online para suporte multigeográfico. Esse processo de configuração único é disparado após você solicitar o plano de serviço *Funcionalidades Multigeográficas no Office 365* e as licenças aparecem em seu locatário. Você receberá notificações no [Centro de mensagens do Office 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) depois que as licenças multigeográficas são aplicadas e você pode começar configurar e usar recursos do Office 365 multigeográfico.

2. Leia [planejar o ambiente multigeográfico](plan-for-multi-geo.md).

3. Saiba mais sobre [administrar um ambiente multigeográfico](administering-a-multi-geo-environment.md) e [como seus usuários terão o ambiente](multi-geo-user-experience.md).

4. Quando estiver pronto para configurar o Office 365 Multigeográfico, [configurar seu locatário multigeográfico](multi-geo-tenant-configuration.md).

5. [Configurar pesquisa](configure-search-for-multi-geo.md).

## <a name="see-also"></a>Confira também

[Aka.ms/GoMultiGeo ](https://Aka.ms/GoMultiGeo)

[Recursos multigeográficos no OneDrive e SharePoint Online](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365.md)

[Recursos multigeográficos no Exchange Online](multi-geo-capabilities-in-exchange-online.md)
