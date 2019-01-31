---
title: Preparar sua organização para o Office 365 Enterprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Se você tiver decidido sem FastTrack implantação e não está encontrando o que precisa em nossas etapas de implantação básica, este é o ponto de partida.
ms.openlocfilehash: bb522890880ec77969abe6e2559c3d0293aca372
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651195"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Preparar sua organização para o Office 365 Enterprise

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>O que você precisa fazer para se preparar para o Office 365?

A maioria das organizações não precisa fazer nada para se preparar para o Office 365. Ele é um aplicativo na web e pessoas são capazes de usá-lo assim que eles têm uma conta. Outras organizações têm mais locais, práticas recomendadas de segurança ou outros requisitos que criam a necessidade de mais planejamento. Para organizações de nível empresarial, siga os itens de lista de verificação abaixo para começar com o Office 365.
  
Se quiser ajuda para configurar o Office 365, o [FastTrack](https://fasttrack.microsoft.com/office) é a maneira mais fácil de implantar o Office 365, e você também pode entrar e usar os [Consultores de implantação para serviços do Office 365](deployment-advisors-for-office-365.md).
  
|**Escolha uma ou mais para começar:**||
|:-----|:-----|
| [Requisitos do sistema para Office](https://products.office.com/office-system-requirements) |-Microsoft Office Professional, Office 365, Office 365 ProPlus e cada aplicativo do Office para Windows, Mac, iOS e Android têm requisitos de sistema específico. Verifique se a sua reunião de hardware e software requisitos mínimos do sistema.|
|**A maioria dos** clientes conectar seu diretório local ao Office 365. Obtenha um ponto de partida na preparação de diretório, [Instalando e executando o IdFix em sua rede](https://www.microsoft.com/download/details.aspx?id=36832).<br> Use o [advisor AAD conectar](https://aka.ms/aadconnectpwsync) e o [que Windows Azure AD Premium configurar guia](https://aka.ms/aadpguidance) para obter orientações de configurar personalizada. <br> |-Automatizados verificações em seu diretório para [Validar pessoas contas sincronizará adequadamente](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> -Recomenda alterações para objetos de diretório e oferece para automatizar as alterações para você. <br> - [Para obter mais detalhes sobre como usar a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md). |
|Nosso [orientações de desempenho de rede](https://aka.ms/tune) e o uso nossas ferramentas para garantir que você tem a configuração de desempenho e a conectividade necessária fornecer as pessoas com a melhor experiência de **leitura** .  <br> | -Verifique se é possível conectar ao Office 365, se você filtra ou examinar saída tráfego, você vai querer entender quais [Gerenciando pontos de extremidade do Office 365](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) significa para sua organização.  <br>  - [Modelo e testar sua capacidade de rede](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) ou mover para um circuito [ExpressRoute do Windows Azure para o Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) para uma experiência mais previsível.   |
|**Use** nosso [planejamento de lista de verificação](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) como um ponto de partida para criar seu próprio plano de implantação.  <br> | -Visão geral aprofundada das áreas possíveis você precisará planejar com links para informações de referência ou instruções para ajudá-lo a planejar. |
|**Use** o [Script de Item grande do Exchange Server](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) para localizar os itens de email que podem ser muito grandes para migrar.  <br> | -Usa serviços Web do Exchange para representar, acessar, verificar a caixa de correio para tamanhos de arquivo que você especificar e despejos os resultados em um arquivo CSV. Leia as [instruções detalhadas sobre como usar o script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**Tirar** vantagem dos [especialistas de implantação da Microsoft](https://go.microsoft.com/fwlink/?LinkId=517115) que possa ajudar você a partir do planejamento de ajudar todos começar a usar os novos serviços e aplicativos.  <br> Use os [assistentes de implantação de serviços do Office 365](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) para obter orientações de configurar personalizada.  <br> | -O Centro de inclusão funciona diretamente com os clientes e com organizações parceiras. Fornecer-lhes uma chamada hoje. |
|**Use** os [modelos e recursos no Centro de sucesso do Office 365](https://www.microsoft.com/fasttrack/resources) para compartilhar sua implantação e a inclusão planos com as pessoas na sua organização.  <br> | -A comunicação com todos antes, durante e após a transição para o Office 365 é essencial.  <br> -Use nosso modelos, guias e folhetos para melhorar sua comunicação. |
|**Leia** o artigo [Princípios de conectividade de rede do Office 365](https://aka.ms/o365networkingprinciples) para entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível.  <br> | -Este artigo ajudará você a entender as orientações mais recentes para otimizar com segurança de conectividade de rede do Office 365. |
   
Deseja mais recursos para ajudá-lo a integrar o Office 365 com sua estratégia de nuvem ampla? Estes são os [recursos de arquitetura de TI de nuvem da Microsoft](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>Queira falar com suporte?

Estamos aqui para ajudar, [contate o suporte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para produtos de negócios.
