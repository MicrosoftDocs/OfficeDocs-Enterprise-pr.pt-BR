---
title: Privacidade e termos de uso do Office 365 Network insights (visualização)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Privacidade e termos de uso do Office 365 Network insights (visualização)
ms.openlocfilehash: 9c47149ebef1e8b1614b26ad90fb60335783cfd0
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42891480"
---
# <a name="office-365-network-insights-privacy-and-terms-of-use-preview"></a>Privacidade e termos de uso do Office 365 Network insights (visualização)

O centro de administração do Microsoft 365 agora mostra as **recomendações de rede e o desempenho**, que são métricas de desempenho ao vivo coletadas do seu locatário do Office 365 e disponíveis para visualização apenas por usuários administrativos em seu locatário. A conectividade de rede organizacional é projetada por local do escritório por meio de um local de egresso de rede para a Internet. A conectividade de cliente do Office 365 usa essa rota e, em seguida, através da Internet para os servidores de porta frontal do serviço Microsoft. Identificar os locais do Office é a chave para poder mostrar esses insights de rede.

## <a name="location-in-network-measurements"></a>Local em medições de rede

O administrador de uma organização pode aceitar o local a ser incluído nas medições de rede usadas por esse recurso. Isso permite a descoberta automática da cidade onde cada escritório está localizado. As informações de local não são precisas e são ofuscadas para 300m e categorizadas por cidade. No momento em que o local é capturado em um dispositivo do Windows, ele mostrará um ícone **de local em uso** na bandeja de ferramentas e os administradores podem querer notificar os usuários sobre isso. Com esse processamento, o local é tratado como o local da organização do escritório e não o local de uma pessoa ou de um dispositivo. Os insights de rede podem ser mostrados nessas cidades de localização descoberta do Office. Se for desejado mais precisão das recomendações, um administrador poderá inserir endereços específicos do local do escritório, e os insights da rede serão agregados a eles. Os locais do Office não podem ser agregados mais de 300 metros.

## <a name="location-in-the-microsoft-365-admin-center"></a>Local no centro de administração do Microsoft 365

No centro de administração do Microsoft 365, os controles do Bing MAP são usados para mostrar onde as localizações de escritórios da organização são e para mostrar a topologia de perímetro de rede para um local do escritório selecionado. Quando um administrador adiciona detalhes de endereço específicos para locais do Office, o Bing Maps também é usado para sugerir endereços para facilitar a entrada de dados.

## <a name="terms-of-use"></a>Termos de Uso

Qualquer conteúdo fornecido por meio do Bing Maps, incluindo geocodes, só pode ser usado dentro do produto através do qual o conteúdo é fornecido. O uso do recurso de serviços de local do centro de administração do M365 para o cliente, fornecido pelo Bing Maps, é regido pelos _termos de uso do Bing Maps End User_ disponível em <https://go.microsoft.com/?linkid=9710837> e pela _declaração de privacidade da Microsoft_ disponível em<https://go.microsoft.com/fwlink/?LinkID=248686.>

Esse recurso, fornecido por meio do Bing Maps, também é suportado por **estas tecnologias**. O modo como aproveitamos os serviços de localização fornecidos por estas tecnologias é regido pelos termos de serviço de <https://legal.here.com/en-gb/terms> _tecnologias aqui_ disponíveis em.
