---
title: Isolado sites de equipe do SharePoint Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: 'Resumo: Saiba mais sobre os usos para sites de equipe do SharePoint Online isolados.'
ms.openlocfilehash: 0ce446860becb7a9dced91e26b6da55ed5fab1c9
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a>Isolado sites de equipe do SharePoint Online

 **Resumo:** Saiba mais sobre os usos para sites de equipe do SharePoint Online isolados.
  
Sites de equipe do SharePoint Online são uma maneira fácil para criar rapidamente um espaço para colaboração de notas, documentos, artigos, um calendário e outros recursos no Microsoft Office 365. Sites de equipe do SharePoint Online baseiam-se em um grupo do Office 365 e tem um modelo de administração simplificada para permitir a colaboração aberta com um conjunto particular de membros de grupo ou de toda a organização. Um site de equipe do SharePoint Online padrão permite que os membros do grupo do Office 365 convidar outros usuários e controlar as configurações de permissões.
  
No entanto, em alguns casos, você deseja criar um site de equipe do SharePoint Online para colaboração onde as permissões do site são mais controladas por meio de associação de grupo e níveis de permissão do SharePoint Online, que só são gerenciados pelo SharePoint Administradores. Chamamos isso um site isolado, o que é isolado para o conjunto de usuários que estão colaborando, exibindo seu conteúdo ou administrando o site. Talvez você precise um site isolado para o seguinte:
  
- Um projeto secreto dentro da sua organização.
    
- O local para a propriedade intelectual de altamente confidenciais ou valioso para sua organização.
    
- Os recursos de uma ação judicial tomadas por sua organização ou que ao qual ele está sujeito.
    
- Para compartilhar uma assinatura do Office 365 entre várias organizações que têm algumas overlap, mas existir na maioria das vezes como entidades empresariais separadas.
    
Aqui estão os requisitos de um site isolado:
  
- Somente os administradores do SharePoint Online podem executar a administração do site, que inclui a associação de grupo para acessar o site e como configurar permissões personalizadas.
    
- Membros do site não podem convidar outros membros para o site de equipe.
    
- Usuários que não são membros do site isolado não podem solicitar acesso ao site. Eles receberão um acesso negado a página da web quando eles tentam acessar qualquer URL associada ao site.
    
A desvantagem da exigência de controle de acesso centralizado e permissões personalizadas pelos administradores do SharePoint Online é que o site permanece isolado ao longo do tempo. Por exemplo, atuais membros não é possível, intencionalmente ou acidentalmente, convidar ou configurar permissões personalizadas para outros usuários dentro da assinatura do Office 365, que não devem ser membros do site.
  
Um site isolado pode ser usado com outros recursos, tais como:
  
- Information Rights Management para garantir que os recursos no site permaneçam criptografados, mesmo se eles são baixados localmente e carregado para outro site que está disponível para toda a organização.
    
- Prevenção de perda de dados para impedir que os usuários enviem os recursos do site, como arquivos, em email.
    
## <a name="next-steps"></a>Próximas etapas

Para testar um site de equipe do SharePoint Online isolado em uma assinatura de avaliação, consulte as instruções passo a passo no [ambiente de desenvolvimento e teste de site de equipe isolado SharePoint Online](isolated-sharepoint-online-team-site-dev-test-environment.md).
  
Quando estiver pronto para implantar um site de equipe do SharePoint Online isolado em produção, consulte as considerações de design passo a passo em [um site de equipe do SharePoint Online isolado de Design](design-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Veja também

[Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md)
  
[Gerenciar um site de equipe do SharePoint Online isolado](manage-an-isolated-sharepoint-online-team-site.md)
  
[Soluções de segurança](security-solutions.md)

[Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md)


