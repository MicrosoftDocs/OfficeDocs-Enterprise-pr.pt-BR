---
title: Proteja arquivos e sites do SharePoint Online
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
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "Resumo: Configuração as recomendações para proteger arquivos no SharePoint Online e Office 365."
ms.openlocfilehash: 035c3e69a430269b382ab032387a44cc3cbbbfd6
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>Proteja arquivos e sites do SharePoint Online

 **Resumo:** Recomendações de configuração de proteção de arquivos no SharePoint Online e Office 365.
  
Este artigo fornece recomendações para configuração de sites de equipe do SharePoint Online e proteção de arquivo que equilibra a segurança com a facilidade de colaboração. Este artigo define quatro configurações diferentes, começando com um site público dentro da sua organização com as políticas de compartilhamento abertas mais. Cada configuração adicional representa uma etapa significativa para cima em proteção, mas a capacidade de acessar e colaborar com os recursos é reduzida ao conjunto relevante de usuários. Use estas recomendações como ponto de partida e ajustar as configurações para atender às necessidades da sua organização. 
  
As configurações neste artigo se alinhem à recomendadas pela Microsoft para três camadas de proteção de dados, as identidades e dispositivos:
  
- Proteção de linha de base
    
- Proteção confidencial
    
- Proteção altamente confidencial
    
Para obter mais informações sobre esses recursos recomendados para cada camada e as camadas, consulte os recursos a seguir. 
  
- [Proteção de identidade e dispositivo para o Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Soluções para proteção de arquivos do Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>Visão geral do recurso

Recomendações para sites de equipe do SharePoint Online desenhar em uma variedade de recursos do Office 365. Para sites altamente confidenciais, recomenda-se a proteção de informações do Azure. Isso é incluído no Enterprise mobilidade + segurança (EMS). 
  
A ilustração a seguir mostra as configurações recomendadas para quatro sites de equipe do SharePoint Online.
  
![Configuração recomendada para sites do SharePoint](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
Conforme ilustrado:
  
- Proteção de linha de base inclui duas opções para sites de equipe do SharePoint Online — um site público e sites particulares. Sites públicos podem ser descobertos e pode ser acessados por qualquer pessoa na organização. Sites privadas só podem ser descobertos e acessados pelos membros do site. Ambas essas configurações de site permitem o compartilhamento fora do grupo. 
    
- Sites para proteção altamente confidenciais são sites privados com acesso limitado somente aos membros de grupos específicos.
    
- Rótulos do Office 365 fornecem uma maneira de classificar os dados com um nível de proteção necessárias. Cada um dos sites de equipe do SharePoint Online são configurados automaticamente rótulo arquivos em bibliotecas de documentos com um rótulo padrão para o site. Correspondente para as configurações de site de quatro, os rótulos neste exemplo são internos de públicos, privados, confidenciais e altamente confidenciais. Os usuários podem alterar os rótulos, mas essa configuração garante que todos os arquivos de recebem um rótulo padrão.
    
- Políticas de (DLP) de prevenção de perda de dados são configuradas para os rótulos de confidenciais e altamente confidenciais Office 365 Avisar ou impedir que os usuários quando eles tentam enviar esses tipos de arquivos fora da organização.
    
- Para sites configurados com proteção altamente confidencial, a proteção de informações do Windows Azure criptografa e concede permissões para os arquivos.
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>Configurações de todo o locatário para o SharePoint Online e o OneDrive for Business

SharePoint Online e OneDrive for Business incluem configurações de todo o locatário que afetam todos os sites e usuários. Algumas dessas configurações também podem ser ajustadas no nível do site para ser mais restritivo (mas não menor). Esta seção discute as configurações de todo o locatário que afetam a segurança e colaboração. 
  
### <a name="sharing"></a>Compartilhamento

Para essa solução, recomendamos as seguintes configurações de todo o locatário:
  
- Mantenha a política que permite o compartilhamento de todas as com todos os tipos de conta, incluindo compartilhamento anônimo de compartilhamento padrão.
    
- Defina os links anônimo para expirar, se desejar.
    
- Altere o tipo de link de padrão para o compartilhamento como Internal. Isso ajuda a evitar vazamento acidental de dados fora da sua organização.
    
Enquanto se imagina contra-intuitivo para permitir o compartilhamento externo, essa abordagem oferece mais controle sobre o compartilhamento de arquivos em comparação com enviando arquivos em email. SharePoint Online e o Outlook trabalham juntos para fornecer a colaboração segura em arquivos. 
  
- Por padrão, o Outlook compartilha um link para um arquivo, em vez de enviar o arquivo no email. 
    
- SharePoint Online e o OneDrive for Business facilitam a compartilhar links para arquivos com colaboradores que estão dentro e fora da sua organização
    
Você também tem controles para ajudar a controlar compartilhamento externo. Por exemplo, você pode:
  
- Desabilite um link de convidado anônimo.
    
- Revogar o acesso de usuário a um site.
    
- Ver quem tem acesso a um site específico ou um documento.
    
- Definir vínculos de compartilhamento anônimos para vencer (inquilino configuração).
    
- Limitar quem pode compartilhar fora da sua organização (inquilino configuração).
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>Usar o compartilhamento externo em conjunto com a prevenção de perda de dados (DLP)

Se você não permitir o compartilhamento externo, os usuários com uma empresa precisam encontrará métodos e ferramentas alternativas. A Microsoft recomenda que você combinar compartilhamento externo com políticas de DLP para proteger arquivos confidenciais e altamente confidenciais.
  
### <a name="device-access-settings"></a>Configurações de acesso de dispositivo

Configurações de acesso de dispositivo para o SharePoint Online e o OneDrive for Business permitem determinar se o acesso é limitado ao navegador apenas (arquivos não podem ser baixados) ou se o acesso é bloqueado. Essas configurações são atualmente na primeira versão e se aplicam a todo o inquilino. Em breve é a capacidade de configurar as políticas de acesso de dispositivo no nível do site. Para essa solução, recomendamos que você não usar configurações de acesso de dispositivo que se aplicam a todo o locatário.
  
Usar as configurações de acesso de dispositivo enquanto eles estão na primeira versão: [Configurar a opção padrão ou primeira opções liberar no Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).
  
### <a name="onedrive-for-business"></a>OneDrive for Business

Visite essas configurações para decidir se deseja alterar as configurações padrão do OneDrive para sites corporativos. Atualmente, as configurações de acesso de compartilhamento e de dispositivo são duplicadas a partir do Centro de administração do SharePoint Online e aplicam a ambos os ambientes.
  
## <a name="sharepoint-team-site-configuration"></a>Configuração de site de equipe do SharePoint

A tabela a seguir resume a configuração para cada um dos sites de equipe descritos anteriormente neste artigo. Use essas configurações como recomendações do ponto de partida e ajustar os tipos de site e configurações para atender às necessidades da sua organização. Não, toda organização precisa de cada tipo de site. Somente um pequeno número de organizações exige proteção altamente confidencial.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**Proteção de linha de base #1** <br/> |**Proteção de linha de base #2** <br/> |**Proteção confidencial** <br/> |**Altamente confidenciais** <br/> |
|Descrição  <br/> |Abrir o discovery and colaboração dentro da organização.  <br/> |Site particular e grupo com compartilhamento permitido fora do grupo.  <br/> |Site isolado, no qual os níveis de acesso estão definidos pela associação em grupos específicos. Compartilhamento é permitido somente membros do site. DLP avisa aos usuários ao tentar enviar arquivos fora da organização.  <br/> |Site isolado + criptografia de arquivos e permissões de proteção de informações do Windows Azure. DLP impede que os usuários enviem arquivos fora da organização.  <br/> |
|Site de equipe privada ou pública  <br/> |Público  <br/> |Particular  <br/> |Particular  <br/> |Particular  <br/> |
|Quem tem acesso?  <br/> |Todas as pessoas na organização, incluindo usuários B2B e usuários convidados.  <br/> |Membros do site apenas. Outras pessoas podem solicitar acesso.  <br/> |Membros do site apenas. Outras pessoas podem solicitar acesso.  <br/> |Somente membros. Outros usuários não podem solicitar acesso.  <br/> |
|Controles de compartilhamento de nível de site  <br/> |Compartilhando permitidos com qualquer pessoa. Configurações padrão.  <br/> |Compartilhando permitidos com qualquer pessoa. Configurações padrão.  <br/> |Membros não podem compartilhar o acesso ao site.  <br/> Não membros podem solicitar acesso ao site, mas essas solicitações precisam ser atendidas por um administrador de site.  <br/> |Membros não podem compartilhar o acesso ao site.  <br/> Não membros não podem solicitar acesso ao conteúdo ou site.  <br/> |
|Controles de acesso de dispositivo de nível de site  <br/> |Não há controles adicionais.  <br/> |Não há controles adicionais.  <br/> |Controles de nível do site estão em breve, o que impede que os usuários baixem arquivos nos dispositivos Unidos incompatíveis ou não pertencentes ao domínio. Isso permite acesso somente de navegador de todos os outros dispositivos.  <br/> |Controles de nível do site estão disponíveis em breve, que bloqueia o download de arquivos nos dispositivos Unidos incompatíveis ou não pertencentes ao domínio.  <br/> |
|Rótulos do Office 365  <br/> |Público interno  <br/> |Particular  <br/> |Confidenciais  <br/> |Altamente confidenciais  <br/> |
|Políticas de DLP  <br/> |||Avise aos usuários durante o envio de arquivos que são rotulados como confidenciais fora da organização.  <br/> Para bloquear o compartilhamento externo dos tipos de dados confidenciais, como números de cartão de crédito ou outros dados pessoais, você pode configurar políticas de DLP adicionais para esses tipos de dados (incluindo os tipos de dados personalizados que você configurar).  <br/> |Impedir que os usuários enviem arquivos que são rotulados como altamente confidenciais fora da organização. Permitir que usuários substituí-lo, fornecendo justificativa, incluindo que eles estão compartilhando o arquivo com.  <br/> |
|Proteção de Informações do Azure  <br/> ||||Use a proteção de informações do Windows Azure para criptografar automaticamente e conceder permissões para os arquivos. Essa proteção viaja com os arquivos caso eles são vazados.  <br/> O Office 365 não pode ler arquivos criptografados com proteção de informações do Windows Azure. Além disso, as políticas de DLP só podem trabalhar com os metadados (incluindo rótulos), mas não o conteúdo desses arquivos (por exemplo, números de cartão de crédito dentro de arquivos).  <br/> |
   
Para conhecer as etapas implantar os quatro tipos diferentes de sites de equipe do SharePoint Online nesta solução, consulte [sites implantar o SharePoint Online para três camadas de proteção](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). Para conhecer as etapas criar um ambiente de desenvolvimento e teste, consulte [sites seguro do SharePoint Online em um ambiente de desenvolvimento e teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md). 
  
## <a name="office-365-classification-and-labels"></a>Etiquetas e classificação do office 365

O uso de rótulos do Office 365 é recomendado para ambientes com dados confidenciais. Depois de configurar e publicar os rótulos do Office 365:
  
- Você pode aplicar um rótulo padrão para uma biblioteca de documentos em um site de equipe do SharePoint Online, de modo que todos os documentos nessa biblioteca obtém o rótulo padrão. 
    
- Você pode aplicar rótulos para conteúdo automaticamente se ele corresponder condições específicas.
    
- Você pode aplicar políticas de DLP que se baseiam em rótulos do Office 365.
    
- Pessoas da sua organização podem aplicar um rótulo manualmente ao conteúdo no Outlook na web, Outlook 2010 e posterior, OneDrive para grupos de negócios, SharePoint Online e Office 365. Os usuários geralmente saber melhor que tipo de conteúdo que eles está trabalhando, para que possam classificá-lo e têm a política DLP apropriada aplicada.
    
![Configuração recomendada para sites do SharePoint](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
Conforme ilustrado, essa solução inclui criando os seguintes rótulos:
  
- Altamente confidenciais
    
- Confidenciais
    
- Particular
    
- Público interno
    
Esses rótulos são mapeados para os sites recomendados nas ilustrações e gráficos neste artigo. Esta solução recomenda configurando políticas de DLP para ajudar a impedir o vazamento de arquivos rotulados como confidenciais e altamente confidenciais.
  
Para conhecer as etapas configurar rótulos do Office 365 e políticas DLP nesta solução, consulte [arquivos de proteger o SharePoint Online com o Office 365 rótulos e DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).
  
## <a name="azure-information-protection"></a>Proteção de Informações do Azure

Use a proteção de informações do Windows Azure para aplicar a rótulos e proteções que seguem os arquivos onde quer que estejam. Para essa solução, recomendamos que você usa uma política de proteção de informações do Windows Azure com escopo e um rótulo de subsites do rótulo altamente confidenciais para criptografar e conceder permissões para os arquivos que precisam ser protegidas com o nível mais alto de segurança. 
  
Lembre-se de que, quando a criptografia de proteção de informações do Windows Azure é aplicada aos arquivos armazenados no Office 365, o serviço não conseguirá processar o conteúdo desses arquivos. Coautoria, eDiscovery, pesquisa, Delve e outros recursos colaborativos não funcionam. Políticas de DLP só podem trabalhar com os metadados (incluindo os rótulos do Office 365), mas não o conteúdo desses arquivos (por exemplo, números de cartão de crédito dentro de arquivos).
  
![A Proteção de Informações do Azure é configurada no Azure e os rótulos são exibidos na barra de ferramentas do cliente.](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
Conforme ilustrado:
  
- Configurar políticas de proteção de informações do Windows Azure e rótulos no portal do Microsoft Azure. Configurar um rótulo sub-recurso de uma política de proteção de informações do Windows Azure com escopo é recomendado.
    
- Proteção de informações Azure etiquetas Mostrar backup como uma barra de **proteção de informações** nos aplicativos do Office.
    
### <a name="adding-permissions-for-external-users"></a>Adicionar permissões para usuários externos

Existem duas maneiras que você pode conceder a usuários externos acessem arquivos protegidos com proteção de informações do Windows Azure. Ambos nesses casos, os usuários externos devem ter uma conta do Windows Azure AD. Se os usuários externos não membros de uma organização que usa o Azure AD, eles podem obter uma conta do Windows Azure AD como um indivíduo usando esta página de inscrição: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).
  
- Adicionar usuários externos a um grupo de Azure AD que é usado para configurar a proteção de um controle label
    
     Você precisará primeiro adicione a conta como um usuário B2B em seu diretório. Pode demorar algumas horas para ser um [membro do grupo cache pelo gerenciamento de direitos do Windows Azure](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). Com este método, as permissões são concedidas a todos os arquivos existentes protegidos com o rótulo (até mesmo arquivos protegidos antes que um usuário é adicionado ao grupo Azure AD).
    
- Adicionar usuários externos diretamente para a proteção de rótulo
    
     Você pode adicionar todos os usuários de uma organização (por exemplo, Fabrikam.com), um usuário individual ou um grupo do Windows Azure AD (por exemplo, um grupo de finanças dentro de uma organização). Por exemplo, você pode adicionar uma equipe externa de reguladores para a proteção de um controle label. Com este método, as permissões são concedidas apenas para arquivos protegidos pelo rótulo depois que a entidade externa é adicionada para a proteção.
    
### <a name="deploying-and-using-azure-information-protection"></a>Implantação e uso de proteção de informações do Windows Azure

Para conhecer as etapas configurar o Azure Information Protection nesta solução, consulte [proteger o SharePoint Online arquivos com proteção de informações do Windows Azure](protect-sharepoint-online-files-with-azure-information-protection.md).
  
## <a name="see-also"></a>Veja também

[Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Soluções de segurança](security-solutions.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Proteger sites do SharePoint Online em um ambiente de desenvolvimento e teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



