---
title: Mapa de fim do suporte do servidor 2010 do Project
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: Em 13 de outubro de 2020, o suporte termina do Project Server 2010. Use este artigo para planejar uma atualização agora.
ms.openlocfilehash: bdfc4dd81dca7fe137be5780e54252eba961910f
ms.sourcegitcommit: e89b5306338ecdb40ad88efcf9cae3b8d5692924
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2018
ms.locfileid: "25549775"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Final do Project Server 2010 do mapa de suporte

Suporte está terminando para servidores do Office 2010 e aplicativos em 2010, e você precisa considerar planos para migração. Se você está usando o Project Server 2010, observe que ele e esses outros produtos relacionados terá as seguintes datas finais de suporte:
  
|**Produto**|**fim do suporte de data**|
|:-----|:-----|
|Project Server 2010  <br/> |13 de outubro de 2020  <br/> |
|Project Portfolio Server 2010  <br/> |13 de outubro de 2020  <br/> |
|Project 2010 Standard  <br/> |13 de outubro de 2020  <br/> |
|Project 2010 Professional  <br/> |13 de outubro de 2020  <br/> |
   
Para obter mais informações sobre os servidores do Office 2010 está atingindo aposentadoria, consulte [atualização do produtos de cliente e servidores do Office 2010](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>Qual end faz da média de suporte?

Project Server, como quase todos os produtos da Microsoft, tem um ciclo de vida de suporte durante o qual fornecemos novos recursos, correções de erros, correções de segurança e assim por diante. Esse ciclo de vida geralmente dura por 10 anos a partir da data de lançamento inicial do produto e final desse ciclo de vida é conhecido como o fim do produto do suporte. Porque o Project Server 2010 atingido seu fim do suporte em 10 de outubro de 2020, a Microsoft não fornecerá mais:
  
- Suporte técnico para problemas que podem ocorrer.
    
- Bug correções para os problemas que são descobertos e que pode afetar a estabilidade e a usabilidade do servidor.
    
- Correções de segurança para vulnerabilidades que são descobertas e pode fazer com que o servidor vulnerável a falhas de segurança.
    
- Atualizações de fuso horário.
    
Sua instalação do Project Server 2010 continuará a executar após essa data. No entanto, devido às alterações listadas acima, é altamente recomendável que você migre do Project Server 2010 assim que possível.
  
## <a name="what-are-my-options"></a>Quais são as opções de minha?

Se você estiver usando o Project Server 2010, você precisará explore as opções de migração, que são:
  
- Migrar para o Project Online
    
- Migre para uma versão mais recente do local do Project Server (preferencialmente 2019 do Project Server).
    
|**Por que eu prefere migrar para o Project Online**|**Por que eu prefere migrar para o Project Server 2019**|
|:-----|:-----|
| Tenho que os usuários móveis.  <br/>  Os custos para migrar são uma preocupação ganhar (hardware, software, horas e esforço para implementar, etc.).  <br/>  Após a migração, os custos para manter o meu ambiente são uma preocupação ganhar (por exemplo, atualizações automáticas, há uma garantia de tempo de atividade, etc.).  <br/> | Regras de negócios restringem me opere minha empresa na nuvem.  <br/>  Necessário controle das atualizações do meu ambiente.  <br/> |
   
> [!NOTE]
> Para obter mais informações sobre as opções para mover de seus servidores do Office 2010, consulte [recursos para ajudar a atualizar do Office 2010 de servidores e clientes](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Observe que o Project Server não dá suporte a uma configuração híbrida desde o Project Server e Project Online não podem compartilhar o mesmo pool de recursos. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Considerações importantes que você precisa tomar ao planejar migrar do Project Server 2010

Você precisa considerar o seguinte ao planejar migrar do Project Server 2010:
  
- **Obtenha ajuda de um parceiro da Microsoft** - atualização do Project Server 2010 pode ser um desafio e requer muita preparação e planejamento. Ele pode ser desafiador, especialmente se você não eram aquele para instalar e configurar o Project Server 2010 originalmente. Felizmente, há Microsoft Partners você pode transformar para que isso para uma sala, se você planeja migrar para o Project Server 2019 ou Project Online. Você pode pesquisar um Microsoft Partner para ajudá-lo no processo de migração no [Centro de parceiros da Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Você pode retirar uma lista de todos os Microsoft Partner com experiência em projeto pesquisando no termo *Gold Project e do gerenciamento de portfólio* . 
    
- **Planejar as personalizações** - Lembre-se de que muitas das personalizações você tiver trabalhando em seu ambiente do Project Server 2010 podem não funcionar durante a migração para o Project Server 2019 ou Project Online. Há algumas diferenças ganhar na arquitetura do Project Server entre versões, bem como os sistemas operacionais necessários, servidores de banco de dados e navegadores da web de cliente suportadas para trabalhar com a versão mais recente. Ter um plano sobre como testar ou reconstruir suas personalizações conforme necessário no novo ambiente. Planejando a atualização também será uma boa oportunidade para verificar se uma personalização específica seja realmente necessário ao se mover para frente. [Criar um plano para personalizações atuais durante a atualização para o SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) tem algumas ótimas informações gerais sobre a avaliação e planejamento para personalizações atuais durante a atualização. 
    
- **Tempo e compreensão** - planejamento, execução e teste de atualização levará muito tempo e esforço, especialmente se você estiver atualizando para o Project Server 2019. Por exemplo, se você estiver migrando do Project Server 2010 para o Project Server 2019, você será primeiro precisa migrar do Project Server 2010 para o Project Server 2013 e verifique se os dados e, em seguida, fazer a mesma coisa quando você migra para cada versão sucessiva (projeto Server 2016 e, em seguida, Project Server 2019). Talvez você queira Verifique com um Microsoft Partner para comparar os custos estimados com suas estimativas de quanto tempo levará para que eles possam fazê-la e a que custo. 
    
## <a name="migrate-to-project-online"></a>Migrar para o Project Online

Se você optar por migrar do Project Server 2010 para o Project Online, você pode fazer o seguinte procedimento para migrar manualmente os dados do plano de projeto:
  
1. Salve seus planos de projeto do Project Server 2010 para. Formato MPP.
    
2. Usando o Project Professional 2016, Project Professional 2019 ou o cliente de Desktop Project Online, abrir cada arquivo. mpp e, em seguida, salve e publicá-lo com o Project Online.
    
Você pode criar manualmente a configuração do PWA no Project Online (por exemplo, recrie quaisquer campos personalizados necessários ou calendários da empresa). Microsoft Partners também pode ajudá-lo com isso.
  
Principais recursos:
  
|**Recurso**|**Descrição**|
|:-----|:-----|
|[Introdução ao Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Como configurar e usar o Project Online.  <br/> |
|[Descrições de serviço on-line do projeto](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informações sobre os planos de projeto Online diferentes que estão disponíveis para você.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrar para uma versão mais recente do local do Project Server

Enquanto estamos altamente acredita que você pode obter a melhor experiência de usuário e o valor, migrando para o Project Online, também sabemos que algumas organizações precisam manter dados de projeto em um ambiente local. Se você optar por manter o seu projeto dados local, você pode migrar seu ambiente do Project Server 2010 para o Project Server 2013, Project Server 2016 ou 2019 do Project Server.
  
É recomendável que você migre para o Project Server 2019 se você não pode migrar para o Project Online. Project Server 2019 inclui a maior parte da chave os recursos e os aperfeiçoamentos incluídos com versões anteriores do Project Server e mais parecido com a experiência disponível com o Project Online (embora alguns recursos estão disponíveis somente no Project Online).
  
Após concluir cada migração, você deve verificar seus dados para certificar-se de que foram migrados com êxito.
  
> [!NOTE]
> Se você estiver considerando apenas migrando para o Project Server 2013, se você está limitado a uma solução local, é importante observar que ele tem apenas alguns anos mais de suporte à esquerda. Project Server 2013 com Service Pack 2, o fim do suporte data é 10/13/2023. Para obter mais informações sobre datas finais de suporte, consulte a [Política de ciclo de vida de produtos do Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Como migrar para o Project Server 2019?

As diferenças arquitetônicas entre o Project Server 2010 e Project Server 2019 impede que um caminho de migração direta. Isso significa que você precisará migrar os dados do Project Server 2010 para a próxima versão sucessiva do Project Server até que você atualizar para o Project Server 2019.
  
Você precisará fazer o seguinte para atualizar para o Project Server 2019:
  
1. Etapa 1: Migre seus dados do Project Server 2010 para o Project Server 2013.
    
2. Etapa 2: Migre seus dados do Project 2013 servem para 2016 do Project Server.
    
3. Etapa 3: Migre seus dados do Project Server 2016 para 2019 do Project Server.
    
Após concluir cada migração, você deve verificar seus dados para certificar-se de que foram migrados com êxito.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Etapa 1: Migrar para o Project Server 2013

A primeira etapa na migrar os dados do Project Server 2010 para o Project Server 2019 é primeiro migrar para o Project Server 2013. 
  
Para ter uma compreensão abrangente do que você precisa fazer para atualizar do Project Server 2010 para o Project Server 2013, consulte o conjunto de conteúdo de [atualizar para o Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) no TechNet. 
  
Principais recursos:
  
|**Recurso**|**Descrição**|
|:-----|:-----|
|[Processo de atualização de visão geral do Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Obtenha uma compreensão de alto nível do que você precisa fazer para atualizar do Project Server 2010 para o Project Server 2013.  <br/> |
|[Planejar a atualização para o Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Examinar considerações que precisam ser tomadas durante a atualização do Project Server 2010 para o Project Server 2013, incluindo os requisitos de sistema de planejamento.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Informações importantes sobre como atualizar para esta versão

[O que há de novo na atualização do Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) informa algumas alterações importantes para a atualização para esta versão, o que está sendo mais notáveis: 
  
- Não há nenhuma atualização in-loco para o Project Server 2013. A anexação de banco de dados é o único método com suporte para a atualização do Project Server 2010 para o Project Server 2013.
    
- O processo de atualização não serão convertidos apenas os dados do Project Server 2010 para o formato do Project Server 2013, mas também serão consolidados os quatro bancos de dados do Project Server 2010 para um único banco de dados do Project Web App.
    
- SharePoint Server 2013 e Project Server 2013 alterado para autenticação baseada em declarações da versão anterior. Você precisará fazer considerações ao atualizar se você estiver usando a autenticação clássica. Para obter mais informações, consulte [Migrate de modo clássico para a autenticação baseada em declarações no SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Recursos adicionais:
  
- [Visão geral do processo de atualização para o Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Atualizar seus bancos de dados e conjuntos de sites do Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagrama de processo de atualização do Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [A consolidação de banco de dados grande, migração do Project Server 2010 para 2013 nas etapas fácil 8](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Etapa 2 migrar para o Project Server 2016

Após a migração para o Project Server 2013 e verificando se os dados foram migrados com êxito, a próxima etapa é migrar os dados para o Project Server 2016.
  
Para ter uma compreensão abrangente do que você precisa fazer para a atualização do Project Server 2013 para o Project Server 2016, consulte o conjunto de conteúdo de [atualizar para o Project Server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Principais recursos:
  
|**Recurso**|**Descrição**|
|:-----|:-----|
|[Visão geral do processo de upgrade para o Project Server 2016](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Obtenha uma compreensão de alto nível do que você precisa fazer para a atualização do Project Server 2013 para o Project Server 2016.  <br/> |
|[Plano para upgrade para o Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Examinar as considerações de planejamento, que você precisa tomar ao atualizar do Project Server 2013 para 2016 do Project Server.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Informações importantes sobre como atualizar para esta versão

[Coisas que você precisa saber sobre o Project Server 2016 atualizar](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) informa algumas alterações importantes para a atualização para esta versão, que incluem: 
  
- Quando você cria o seu ambiente do Project Server 2016 ao qual você irá migrar os dados do Project Server 2013, observe que os arquivos de instalação do Project Server 2016 serão incluídos no SharePoint Server 2016. Para obter mais informações, consulte [implantar o Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Planos de recursos são reduzidos no Project Server 2016. Seus planos de recursos do Project Server 2013 serão migrados para contratos de recursos no Project Server 2016 e no Project Online. Consulte [Visão geral: compromissos com o recurso](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) para obter mais informações. 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Etapa 3 migrar para o Project Server 2019

Após a migração para o Project Server 2016 e verificando se os dados foram migrados com êxito, a próxima etapa é migrar os dados para o Project Server 2019.
  
Para ter uma compreensão abrangente do que você precisa fazer para a atualização do Project Server 2016 para 2019 do Project Server, consulte o conjunto de conteúdo de [atualizar para o Project Server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Principais recursos:
  
|**Recurso**|**Descrição**|
|:-----|:-----|
|[Visão geral do que o Project Server 2019 o processo de atualização](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Obtenha uma compreensão de alto nível do que você precisa fazer para a atualização do Project Server 2013 para o Project Server 2016.  <br/> |
|[Planejar a atualização para o Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Examinar as considerações de planejamento, que você precisa tomar ao atualizar do Project Server 2016 para 2019 do Project Server.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Informações importantes sobre como atualizar para esta versão

[Coisas que você precisa saber sobre o Project Server 2019 atualizar](https://go.microsoft.com/fwlink/p/?linkid=841827) informa algumas alterações importantes para a atualização para esta versão, que incluem: 
  
- O processo de atualização será migre seus dados do seu banco de dados do Project Server 2016 no banco de dados de conteúdo do SharePoint Server 2019.  Project Server 2019 não tempo irá criá-la é o proprietário de banco de dados do Project Server no farm do SharePoint Server.

- Após a atualização, esteja ciente das várias alterações no Project Web App.  Para obter uma descrição dessas, consulte [o que há de novo no Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).


## <a name="migrate-from-portfolio-server-2010"></a>Migrar do Portfolio Server 2010

Project Portfolio Server 2010 foi usado com o Project Server 2010 para otimização, priorização e estratégia de portfólio. Sem adicionais versões do Project Portfolio Server foram criadas após essa versão. No entanto, os recursos de gerenciamento de portfólio estão disponíveis em versões posteriores do Project Server e a versão Premium do Project Online. Dados do Project Portfolio Server 2010 não podem ser migrados para o. Dados como impulsionadores de negócios precisará ser recriadas.
  
Outros recursos:
  
- [Descrições do serviço do Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): consulte os recursos de gerenciamento de portfólio que estão inclusos no Project Server 2016 e Premium on-line do projeto.
    
- [Guia de migração do Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Tópicos relacionados

[Atualizando do SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Recursos para ajudá-lo a atualizar do Office 2010 de servidores e clientes](upgrade-from-office-2010-servers-and-products.md)
  

