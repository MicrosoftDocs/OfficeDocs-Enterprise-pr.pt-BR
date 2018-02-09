---
title: Projetar um site de equipe do SharePoint Online isolado
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: 'Resumo: Etapa durante o processo de design para sites de equipe do SharePoint Online isolados.'
ms.openlocfilehash: efd55ce780cf2951bfafd31215201459965c0e78
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a>Projetar um site de equipe do SharePoint Online isolado

 **Resumo:** Percorrer o processo de design para sites de equipe do SharePoint Online isolados.
  
Este artigo apresenta as decisões de design principal, que você deve fazer antes de criar um site de equipe do SharePoint Online isolado.
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a>Fase 1: Determinar seus grupos do SharePoint e níveis de permissão

Cada site de equipe do SharePoint Online, por padrão é criado com os seguintes grupos do SharePoint:
  
- \<nome do site > membros
    
- \<nome do site > visitantes
    
- \<nome do site > proprietários
    
Esses grupos são separados dos grupos do Office 365 e Windows Azure AD (Active Directory) e são a base para atribuir permissões para os recursos do site.
  
O conjunto de permissões específicas que determina o que um membro de um grupo do SharePoint pode fazer em um site é um nível de permissão. Existem três níveis de permissão por padrão para um site de equipe do SharePoint Online: controle total, leitura e editar. A tabela a seguir mostra a correlação de padrão de grupos do SharePoint e níveis de permissão atribuídos:
  
|**Grupo do SharePoint**|**Nível de permissão**|
|:-----|:-----|
|\<nome do site > membros  <br/> |Editar  <br/> |
|\<nome do site > visitantes  <br/> |Leitura  <br/> |
|\<nome do site > proprietários  <br/> |Controle total  <br/> |
   
 **Práticas recomendadas:** Você pode criar grupos adicionais do SharePoint e níveis de permissão. No entanto, é recomendável usar os grupos padrão do SharePoint e níveis de permissão para o seu site do SharePoint Online isolado.
  
Aqui estão os níveis de permissão e grupos padrão do SharePoint.
  
![Os grupos do SharePoint e níveis de permissão padrão de um site do SharePoint Online.](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a>Fase 2: Atribuir permissões aos usuários com grupos de acesso

Você pode atribuir permissões aos usuários adicionando sua conta de usuário ou um grupo do Office 365 ou no Windows Azure AD do qual a conta de usuário é um membro, aos grupos do SharePoint. Uma vez adicionados, as contas de usuário do Office 365, seja diretamente ou indiretamente por meio de associação em um grupo do Office 365 ou no Windows Azure AD, recebem o nível de permissão associado ao grupo do SharePoint.
  
Usando os grupos padrão do SharePoint como exemplo:
  
- Membros do ** \<nome do site > membros** grupo do SharePoint, que pode incluir contas de usuário e grupos, recebem o nível de permissão **Editar**
    
- Membros do ** \<nome do site > visitantes** grupo do SharePoint, que pode incluir contas de usuário e grupos, recebem o nível de permissão de **leitura**
    
- Membros do ** \<nome do site > proprietários** grupo do SharePoint, que pode incluir contas de usuário e grupos, recebem o nível de permissão **controle total**
    
 **Práticas recomendadas:** Embora seja possível gerenciar permissões por meio de contas de usuário individuais, recomendamos que você use um único grupo Azure AD, conhecido como um grupo de acesso, em vez disso. Isso simplifica o gerenciamento de permissões por meio da participação no grupo de acesso, em vez de contas de gerenciamento da lista de usuário para cada grupo do SharePoint.
  
Grupos do Azure AD para o Office 365 são diferentes grupos do Office 365. Grupos do Azure AD aparecem no Centro de administração do Office com seu conjunto de **tipo** para **segurança** e não têm um endereço de email. Grupos do Azure AD podem ser gerenciados em:
  
- Windows Server Active Directory (AD)
    
    Esses são grupos que foram criados na infraestrutura do Windows Server AD local e sincronizados à sua assinatura do Office 365. No Centro de administração do Office, esses grupos têm um **Status** de **Synched com o active directory**.
    
- Office 365
    
    Estes são os grupos que foram criados usando o Centro de administração do Office, o portal do Azure ou Microsoft PowerShell. No Centro de administração do Office, esses grupos têm um **Status** de **nuvem**.
    
 **Práticas recomendadas:** Se você estiver usando o Windows Server AD local e sincronizar com sua assinatura do Office 365, execute o usuário e o gerenciamento de grupo com o Windows Server AD.
  
Para sites de equipe do SharePoint Online isolados, a estrutura do grupo recomendado tem esta aparência:
  
|**Grupo do SharePoint**|**Grupo Azure de acesso baseada em AD**|**Nível de permissão**|
|:-----|:-----|:-----|
|\<nome do site > membros  <br/> |\<nome do site > membros  <br/> |Editar  <br/> |
|\<nome do site > visitantes  <br/> |\<nome do site > visualizadores  <br/> |Leitura  <br/> |
|\<nome do site > proprietários  <br/> |\<nome do site > Admins  <br/> |Controle total  <br/> |
   
 **Práticas recomendadas:** Embora você possa usar o Office 365 ou Azure AD grupos como membros de grupos do SharePoint, é recomendável que você use grupos do Azure AD. Grupos do AD Azure, gerenciados através do Windows Server AD ou Office 365, proporcionam mais flexibilidade para usar grupos aninhados para atribuir permissões.
  
Aqui está configurados para usar grupos do Azure acesso baseado em AD de grupos do SharePoint padrão.
  
![Usando os grupos de acesso como membros de grupos de sites do SharePoint Online padrão.](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
Quando estiver criando os grupos de três do access, lembre-se do seguinte:
  
- Deve haver apenas alguns membros no ** \<nome do site > Admins** grupo de acesso, correspondente a um pequeno número de administradores do SharePoint Online, que estão gerenciando o site de equipe.
    
- A maioria dos seus membros do site está no ** \<nome do site > membros** ou ** \<nome do site > visualizadores** acessar grupos. Porque sites membros no ** \<nome do site > membros** grupo acesso têm a capacidade de excluir ou modificar os recursos do site, considere cuidadosamente sua associação. Quando estiver em dúvida, adicione o membro de site para o ** \<nome do site > visualizadores** grupo de acesso.
    
Aqui está um exemplo dos grupos do SharePoint e grupos de acesso para um site isolado chamado ProjectX.
  
![Um exemplo de como usar os grupos de acesso em um site do SharePoint Online chamado ProjectX.](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a>Fase 3: Usar aninhadas grupos do Azure AD.

Para um projeto confinado a um pequeno número de pessoas, um único nível de grupos de Azure acesso baseado em AD adicionados aos grupos do SharePoint do site mais adequado para a maioria dos cenários. No entanto, se você tiver um grande número de pessoas e as pessoas já estejam membros de estabelecidos grupos do AD do Windows Azure, você pode mais facilmente atribuir permissões do SharePoint usando grupos aninhados ou grupos que contêm outros grupos como membros.
  
Por exemplo, você deseja criar um site de equipe online isolado do SharePoint para colaboração entre os executivos de vendas, marketing, engenharia, legais e suporte departamentos e os departamentos já seus próprios grupos com a conta de usuário executivo associação. Em vez de criar um novo grupo para os novos membros do site e colocar todas as contas de usuário individual de executivos nela, coloque os grupos de executivos existentes para cada departamento no novo grupo.
  
 Se você estiver compartilhando uma assinatura do Office 365 entre várias organizações, um único nível de associação de grupo para um site isolada para uma organização pode se tornar difícil de gerenciar devido ao grande número de contas de usuário. Nesse caso, você pode usar grupos do Azure AD para cada organização que contenham os grupos em suas organizações para gerenciar as permissões aninhados.
  
Para usar grupos de Azure AD aninhados:
  
1. Identificar ou criar os grupos do Azure AD que conterá a contas de usuário e adicione as contas de usuário apropriados como membros.
    
2. Crie o grupo do Azure acesso baseado em AD contêiner que conterá os outros grupos do Azure AD e adicionar esses grupos como membros.
    
3.  Para o nível apropriado de acesso para o grupo de acesso do contêiner, identifique o grupo do SharePoint e o nível de permissão correspondente.
    
> [!NOTE]
> É possível usar grupos aninhados do Office 365. 
  
Aqui está um exemplo do Azure AD aninhado grupos para o grupo de acesso do membro ProjectX.
  
![Um exemplo de como usar grupos de acesso aninhados para o grupo de acesso de membros do site do ProjectX.](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
Como todas as contas de usuário na Research, engenharia e Project leads equipes destinam-se a ser membros do site, é mais fácil adicionar seus grupos do Azure AD ao grupo acesso ProjectX membros.
  
## <a name="next-step"></a>Próxima etapa

Quando você estiver pronto para criar e configurar um site isolado em produção, consulte [Deploy um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Veja também

[Isolado sites de equipe do SharePoint Online](isolated-sharepoint-online-team-sites.md)
  
[Gerenciar um site de equipe do SharePoint Online isolado](manage-an-isolated-sharepoint-online-team-site.md)
  
[Soluções de segurança](security-solutions.md)

[Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md)



