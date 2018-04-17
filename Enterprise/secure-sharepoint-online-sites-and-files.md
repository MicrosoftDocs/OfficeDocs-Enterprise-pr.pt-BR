---
title: Proteger sites e arquivos do SharePoint Online seguros
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: 'Resumo: Configuração as recomendações para proteger arquivos no SharePoint Online e Office 365.'
ms.openlocfilehash: 800d81d657164b2a936b95764d57fd092cfa21cc
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>Proteger sites e arquivos do SharePoint Online seguros

 **Resumo:** Recomendações de configuração de proteção de arquivos no SharePoint Online e Office 365.
  
Este artigo fornece recomendações para configuração de sites de equipe do SharePoint Online e proteção de arquivo que equilibra a segurança com a facilidade de colaboração. Este artigo define quatro configurações diferentes, começando com um site público dentro da sua organização com as políticas de compartilhamento abertas mais. Cada configuração adicional representa uma etapa significativa para cima em proteção, mas a capacidade de acessar e colaborar com os recursos é reduzida ao conjunto relevante de usuários. Use estas recomendações como ponto de partida e ajustar as configurações para atender às necessidades da sua organização. 
  
As configurações nesse artigo se alinham às recomendações da Microsoft para três níveis de proteção de dados, identidades e dispositivos:
  
- Proteção de linha de base
    
- Proteção confidencial
    
- Proteção altamente confidencial
    
Para obter mais informações sobre essas camadas e recursos recomendados para cada camada, consulte os recursos a seguir. 
  
- [Proteção de dispositivo e identidade para o Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Soluções de proteção de arquivo do Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>Visão geral da funcionalidade

As recomendações para sites de equipe do SharePoint Online traçam uma variedade de recursos do Office 365. Para sites altamente confidenciais, recomenda-se a Proteção de Informações do Azure. Ela está incluída no EMS (Enterprise Mobility + Security). 
  
A ilustração a seguir mostra as configurações recomendadas para quatro sites de equipe do SharePoint Online.
  
![Configuração recomendada para sites do SharePoint](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
Conforme ilustrado:
  
- A proteção de linha de base inclui duas opções para sites de equipe do SharePoint Online — um site público e um site privado. Os sites públicos podem ser descobertos e acessados por qualquer pessoa na organização. Os sites privados podem ser descobertos e acessados apenas por membros do site. Essas configurações de site permitem o compartilhamento fora do grupo. 
    
- Os sites para proteção confidencial e altamente confidencial são sites privados com acesso limitado apenas a membros de grupos específicos.
    
- Os rótulos do Office 365 fornecem uma maneira de classificar os dados com um nível de proteção necessário. Cada um dos sites de equipe do SharePoint Online é configurado para aplicar rótulos automaticamente aos arquivos nas bibliotecas de documentos com um rótulo padrão para o site. Correspondentes às quatro configurações de site, os rótulos nesse exemplo são Público Interno, Privado, Confidencial e Altamente Confidencial. Os usuários podem alterar os rótulos, mas essa configuração garante que todos os arquivos de recebem um rótulo padrão.
    
- As políticas DLP (prevenção de perda de dados) são configuradas para os rótulos Confidenciais e Altamente Confidenciais do Office 365 para avisar ou impedir os usuários quando tentam enviar esses tipos de arquivos para fora da organização.
    
- Para sites configurados com a proteção altamente confidencial, a Proteção de Informações do Azure criptografa e concede permissões aos arquivos.
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>Configurações para todo o locatário do SharePoint Online e OneDrive para Empresas

O SharePoint Online e OneDrive para Empresas incluem configurações para todo o locatário que afetam todos os sites e os usuários. Algumas dessas configurações também podem ser ajustadas no nível do site para serem mais restritivas (mas não menos). Esta seção discute as configurações para todo o locatário que afetam a segurança e a colaboração. 
  
### <a name="sharing"></a>Compartilhando

Para esta solução, recomendamos as seguintes configurações para todo o locatário:
  
- Mantenha a política de configuração padrão que permite todo o compartilhamento com todos os tipos de conta, incluindo o compartilhamento anônimo.
    
- Configure os links anônimos para expirar, se desejado.
    
- Altere o tipo de link padrão para o compartilhamento para Interno. Isso ajuda a impedir o vazamento acidental de dados fora da sua organização.
    
Embora possa parecer contraintuitivo permitir o compartilhamento externo, essa abordagem fornece mais controle sobre o compartilhamento de arquivo em comparação com enviar os arquivos por email. O SharePoint Online e o Outlook trabalham juntos para fornecer a colaboração segura nos arquivos. 
  
- Por padrão, o Outlook compartilha um link para um arquivo em vez de enviar o arquivo por email. 
    
- SharePoint Online e o OneDrive for Business facilitam a compartilhar links para arquivos com colaboradores que estão dentro e fora da sua organização
    
Você também tem controles para ajudar a controlar o compartilhamento externo. Por exemplo, você pode:
  
- Desabilitar um link de convidado anônimo.
    
- Revogar o acesso de usuário para um site.
    
- Ver quem tem acesso a um documento ou um site específico.
    
- Configurar os links de compartilhamento anônimos para expirarem (configuração de locatário).
    
- Limitar quem pode compartilhar fora da sua organização (configuração de locatário).
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>Usar o compartilhamento externo junto com a DLP (prevenção de perda de dados)

Se você não permitir o compartilhamento externo, os usuários com uma empresa precisam encontrará métodos e ferramentas alternativas. A Microsoft recomenda que você combinar compartilhamento externo com políticas de DLP para proteger arquivos confidenciais e altamente confidenciais.
  
### <a name="device-access-settings"></a>Configurações de acesso de dispositivo

Configurações de acesso de dispositivo para o SharePoint Online e o OneDrive for Business permitem determinar se o acesso é limitado ao navegador apenas (arquivos não podem ser baixados) ou se o acesso é bloqueado. Essas configurações são atualmente na primeira versão e se aplicam a todo o inquilino. Em breve é a capacidade de configurar as políticas de acesso de dispositivo no nível do site. Para essa solução, recomendamos que você não usar configurações de acesso de dispositivo que se aplicam a todo o locatário.
  
Para usar configurações de acesso de dispositivo enquanto estão na primeira versão: [Configurar as opções dos programas Padrão ou Primeiro Lançamento no Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).
  
### <a name="onedrive-for-business"></a>OneDrive for Business

Visite essas configurações para decidir se deseja alterar as configurações padrão para sites do OneDrive para Empresas. Atualmente, as configurações de acesso de compartilhamento e de dispositivo estão duplicadas do Centro de administração do SharePoint Online e se aplicam a ambos os ambientes.
  
## <a name="sharepoint-team-site-configuration"></a>Configuração de site de equipe do SharePoint

A tabela a seguir resume a configuração para cada um dos sites de equipe descritos anteriormente neste artigo. Use essas configurações como recomendações de ponto de partida e ajuste as configurações e os tipos de site para atender às necessidades da sua organização. Nem toda organização precisa de todos os tipos de site. Somente um pequeno número de organizações requer a proteção altamente confidencial.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**Proteção de linha de base nº 1** <br/> |**Proteção de linha de base nº 2** <br/> |**Proteção confidencial** <br/> |**Altamente confidencial** <br/> |
|Descrição  <br/> |Abra a descoberta e a colaboração dentro da organização.  <br/> |Grupo e site particulares com o compartilhamento permitido fora do grupo.  <br/> |Site isolado, no qual os níveis de acesso são definidos pela associação em grupos específicos. O compartilhamento é permitido apenas para membros do site. A DLP avisa os usuários quando tenta enviar arquivos fora da organização.  <br/> |Criptografia de arquivo + site isolado e permissões com a Proteção de Informações do Azure. A DLP impede que os usuários enviem arquivos fora da organização.  <br/> |
|Site de equipe público ou privado  <br/> |Público  <br/> |Private  <br/> |Private  <br/> |Private  <br/> |
|Quem tem acesso?  <br/> |Todas as pessoas na organização, incluindo usuários convidados e usuários de B2B.  <br/> |Membros do site somente. Outros usuários podem solicitar acesso.  <br/> |Membros do site somente. Outros usuários podem solicitar acesso.  <br/> |Somente membros. Outros usuários não podem solicitar acesso.  <br/> |
|Controles de compartilhamento de nível de site  <br/> |Compartilhamento permitido com qualquer pessoa. Configurações padrão.  <br/> |Compartilhamento permitido com qualquer pessoa. Configurações padrão.  <br/> |Os membros não podem compartilhar o acesso ao site.  <br/> Os não membros podem solicitar acesso ao site, mas essas solicitações precisam ser atendidas por um administrador de site.  <br/> |Os membros não podem compartilhar o acesso ao site.  <br/> Os não membros não podem solicitar acesso ao site ou conteúdo.  <br/> |
|Controles de acesso de dispositivo de nível de site  <br/> |Sem controles adicionais.  <br/> |Sem controles adicionais.  <br/> |Os controles de nível de site serão disponibilizados em breve, o que impede que os usuários baixem arquivos para dispositivos que não estão ingressados no domínio ou estão sem conformidade. Isso permite o acesso somente para navegador de todos os outros dispositivos.  <br/> |Os controles de nível de site serão disponibilizados em breve, o que impede o download dos arquivos para dispositivos não ingressados no domínio ou sem conformidade.  <br/> |
|Rótulos do Office 365  <br/> |Público Interno  <br/> |Private  <br/> |Confidencial  <br/> |Altamente Confidencial  <br/> |
|Políticas DLP  <br/> |||Avisar os usuários quando enviar arquivos que são rotulados como Confidencial para fora da organização.  <br/> Para bloquear o compartilhamento externo de tipos de dados confidenciais, como números de cartão de crédito ou outros dados pessoais, você pode configurar políticas DLP adicionais para esses tipos de dados (incluindo tipos de dados personalizados que você configurar).  <br/> |Impedir que os usuários enviem arquivos rotulados como altamente confidenciais para fora da organização. Permitir que os usuários substituam isso fornecendo justificativa, incluindo com quem eles estão compartilhando o arquivo.  <br/> |
|Azure Information Protection  <br/> ||||Use a proteção de informações do Windows Azure para criptografar automaticamente e conceder permissões para os arquivos. Essa proteção viaja com os arquivos caso eles são vazados.  <br/> O Office 365 não pode ler arquivos criptografados com proteção de informações do Windows Azure. Além disso, as políticas de DLP só podem trabalhar com os metadados (incluindo rótulos), mas não o conteúdo desses arquivos (por exemplo, números de cartão de crédito dentro de arquivos).  <br/> |
   
Para conhecer as etapas implantar os quatro tipos diferentes de sites de equipe do SharePoint Online nesta solução, consulte [sites implantar o SharePoint Online para três camadas de proteção](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). Para conhecer as etapas criar um ambiente de desenvolvimento e teste, consulte [sites seguro do SharePoint Online em um ambiente de desenvolvimento e teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md). 
  
## <a name="office-365-classification-and-labels"></a>Rótulos e classificação do Office 365

O uso de rótulos do Office 365 é recomendado para ambientes com dados confidenciais. Depois de configurar e publicar os rótulos do Office 365:
  
- Você pode aplicar um rótulo padrão para uma biblioteca de documentos em um site de equipe do SharePoint Online, de modo que todos os documentos nessa biblioteca obtém o rótulo padrão. 
    
- Você pode aplicar rótulos para conteúdo automaticamente se ele corresponder condições específicas.
    
- Você pode aplicar políticas de DLP que se baseiam em rótulos do Office 365.
    
- Pessoas da sua organização podem aplicar um rótulo manualmente ao conteúdo no Outlook na web, Outlook 2010 e posterior, OneDrive para grupos de negócios, SharePoint Online e Office 365. Os usuários geralmente saber melhor que tipo de conteúdo que eles está trabalhando, para que possam classificá-lo e têm a política DLP apropriada aplicada.
    
![Configuração recomendada para sites do SharePoint](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
Conforme ilustrado, essa solução inclui a criação dos seguintes rótulos:
  
- Altamente Confidencial
    
- Confidencial
    
- Private
    
- Público Interno
    
Esses rótulos são mapeados para os sites recomendados nas ilustrações e gráficos neste artigo. Esta solução recomenda configurando políticas de DLP para ajudar a impedir o vazamento de arquivos rotulados como confidenciais e altamente confidenciais.
  
Para as etapas de configuração de rótulos e políticas DLP do Office 365 nesta solução, consulte [Proteger os arquivos do SharePoint Online com rótulos e DLP do Office 365](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).
  
## <a name="azure-information-protection"></a>Azure Information Protection

Use a Proteção de Informações do Azure para aplicar rótulos e proteções que seguem os arquivos onde quer que eles estejam. Para esta solução, recomendamos que você use uma política de Proteção de Informações do Azure e um sub-rótulo altamente confidencial para criptografar e conceder permissões a arquivos que precisam ser protegidos com o mais alto nível de segurança. 
  
Lembre-se de que quando a criptografia da Proteção de Informações do Azure é aplicada aos arquivos armazenados no Office 365, o serviço não pode processar o conteúdo desses arquivos. Coautoria, descoberta eletrônica, pesquisa, Delve e outros recursos de colaboração não funcionam. Políticas de DLP só funcionam com metadados (incluindo rótulos do Office 365), mas não com o conteúdo desses arquivos (como números de cartão de crédito em arquivos).
  
![A Proteção de Informações do Azure é configurada no Azure e os rótulos são exibidos na barra de ferramentas do cliente.](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
Conforme ilustrado:
  
- Configurar políticas de proteção de informações do Windows Azure e rótulos no portal do Microsoft Azure. Configurar um rótulo sub-recurso de uma política de proteção de informações do Windows Azure com escopo é recomendado.
    
- Proteção de informações Azure etiquetas Mostrar backup como uma barra de **proteção de informações** nos aplicativos do Office.
    
### <a name="adding-permissions-for-external-users"></a>Adicionando permissões para usuários externos

Existem duas maneiras que você pode conceder a usuários externos acessem arquivos protegidos com proteção de informações do Windows Azure. Ambos nesses casos, os usuários externos devem ter uma conta do Windows Azure AD. Se os usuários externos não membros de uma organização que usa o Azure AD, eles podem obter uma conta do Windows Azure AD como um indivíduo usando esta página de inscrição: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).
  
- Adicionar usuários externos a um grupo de Azure AD que é usado para configurar a proteção de um controle label
    
     Você precisará primeiro adicione a conta como um usuário B2B em seu diretório. Pode demorar algumas horas para ser um [membro do grupo cache pelo gerenciamento de direitos do Windows Azure](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). Com este método, as permissões são concedidas a todos os arquivos existentes protegidos com o rótulo (até mesmo arquivos protegidos antes que um usuário é adicionado ao grupo Azure AD).
    
- Adicionar usuários externos diretamente para a proteção de rótulo
    
     Você pode adicionar todos os usuários de uma organização (por exemplo, Fabrikam.com), um usuário individual ou um grupo do Windows Azure AD (por exemplo, um grupo de finanças dentro de uma organização). Por exemplo, você pode adicionar uma equipe externa de reguladores para a proteção de um controle label. Com este método, as permissões são concedidas apenas para arquivos protegidos pelo rótulo depois que a entidade externa é adicionada para a proteção.
    
### <a name="deploying-and-using-azure-information-protection"></a>Implantando e usando a Proteção de Informações do Azure

Para as etapas de configuração de Proteção de Informações do Azure nesta solução, consulte [Proteger arquivos do SharePoint Online com a Proteção de Informações do Azure](protect-sharepoint-online-files-with-azure-information-protection.md).
  
## <a name="see-also"></a>Confira também

[Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Soluções de segurança](security-solutions.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



