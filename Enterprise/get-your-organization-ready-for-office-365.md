---
title: Preparar sua organização para o Office 365 Enterprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Se você optou pela implantação do FastTrack e não está encontrando o que precisa em nossas etapas de implantação básica, este é o local para começar.
ms.openlocfilehash: a15bd73efe2fd2e2dfd13b3a444f77b9d0bfc764
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487737"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Preparar sua organização para o Office 365 Enterprise

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>O que você precisa fazer para se preparar para o Office 365?

A maioria das organizações não precisa fazer nada para se preparar para o Office 365. É um aplicativo na Web e as pessoas podem usá-lo assim que eles tiverem uma conta. Outras organizações têm mais locais, práticas de segurança ou outros requisitos que criam a necessidade de mais planejamento. Para organizações de nível empresarial, siga os itens de lista de verificação abaixo para começar a usar o Office 365.
  
Se quiser ajuda para configurar o Office 365, o [FastTrack](https://fasttrack.microsoft.com/office) é a maneira mais fácil de implantar o Office 365, e você também pode entrar e usar os [Consultores de implantação para serviços do Office 365](deployment-advisors-for-office-365.md).
  
|**Escolha uma ou mais para começar:**||
|:-----|:-----|
| [Requisitos do sistema para o Office](https://products.office.com/office-system-requirements) |– O Microsoft Office Professional, o Office 365, o Office 365 proPlus e cada aplicativo do Office para Windows, Mac, iOS e Android têm requisitos de sistema específicos. Verifique se o hardware e o software atendem aos requisitos mínimos do sistema.|
|**A maioria dos** clientes conecta o diretório local ao Office 365. Obtenha uma ponta na preparação do diretório [Instalando e executando o IdFix em sua rede](https://www.microsoft.com/download/details.aspx?id=36832). <br> Use o [AAD Connect Advisor](https://aka.ms/aadconnectpwsync) e o [Guia de configuração do Azure ad Premium](https://aka.ms/aadpguidance) para obter orientações personalizadas de configuração. <br> |– As verificações automáticas em relação ao seu diretório para [validar as contas de pessoas serão sincronizadas corretamente](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> – Recomenda alterações nos objetos de diretório e oferece para automatizar as alterações para você. <br> - [Mais detalhes sobre como usar a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Leia** nossa [orientação de desempenho de rede](https://aka.ms/tune) e use nossas ferramentas para garantir que você tenha a configuração de conectividade e desempenho necessárias para fornecer às pessoas a melhor experiência.  <br> | – Verifique se você pode se conectar ao Office 365, se filtrar ou examinar o tráfego de saída, convém entender o que [gerencia pontos de extremidade do Office 365](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) significa para sua organização.  <br>  - [Modele e teste sua capacidade de rede](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) ou mude para um circuito do [Azure ExpressRoute para Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) para uma experiência mais previsível.   |
|**Use** nossa [lista de verificação de planejamento](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) como um local inicial para criar seu próprio plano de implantação.  <br> | Visão geral detalhada das possíveis áreas que você precisará planejar com links para informações de referência ou instruções para ajudá-lo a planejar. |
|**Use** o [script de item grande do Exchange Server](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) para localizar itens de email que podem ser muito grandes para migrar.  <br> | – Usa os serviços Web do Exchange para representar, acessar, examinar a caixa de correio em busca de tamanhos de arquivo que você especificar e despeja os resultados em um arquivo CSV. Leia as [instruções detalhadas sobre como usar o script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**** Aproveite os [especialistas de implantação da Microsoft](https://go.microsoft.com/fwlink/?LinkId=517115) que podem ajudá-lo a planejar o planejamento para ajudar todos a começar a usar os novos serviços e aplicativos.  <br> Use os [assistentes de implantação para os serviços do Office 365](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) para obter orientações personalizadas de configuração.  <br> | – O centro de integração funciona diretamente com clientes e organizações parceiras. Dê a eles uma chamada hoje. |
|**Use** os [modelos e recursos do centro de sucesso do Office 365](https://www.microsoft.com/fasttrack/resources) para compartilhar seus planos de implantação e integração com as pessoas da sua organização.  <br> | – A comunicação com todos antes, durante e após a transição para o Office 365 é crítica.  <br> – Use nossos modelos, guias e folhetos para melhorar suas comunicações. |
|**Leia** o artigo sobre os [princípios de conectividade de rede do Office 365](https://aka.ms/o365networkingprinciples) para entender os princípios de conectividade para o gerenciamento seguro do tráfego do Office 365 e obter o melhor desempenho possível.  <br> | Este artigo o ajudará a entender as orientações mais recentes para otimizar com segurança a conectividade de rede do Office 365. |
   
Quer mais recursos para ajudá-lo a integrar o Office 365 à sua estratégia de nuvem mais ampla? Estes são os [recursos de arquitetura de ti do Microsoft Cloud](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>Quer falar com o suporte?

Estamos aqui para ajudar, [entre em contato com o suporte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para produtos de negócios.
