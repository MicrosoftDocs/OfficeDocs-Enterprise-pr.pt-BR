---
title: Roteiro de fim do suporte do Project Server 2007
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: Em 10 de outubro de 2017, o suporte foi encerrado para Project Server 2007, Project Portfolio Server e Project 2007. Use este artigo para planejar uma atualização agora.
ms.openlocfilehash: 5b2fb194d4819b5427cb2844a5189b2b03753800
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169893"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Roteiro de fim do suporte do Project Server 2007

O suporte está terminando para aplicativos e servidores do Office 2007 em 2017 e você precisa considerar planos para migração. Se você estiver usando o Project Server 2007, observe que ele e esses outros produtos relacionados terá as datas de fim do suporte a seguintes:
  
|**Produto**|**fim do suporte de data**|
|:-----|:-----|
|Project Server 2007  <br/> |10 de outubro de 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 de outubro de 2017  <br/> |
|Project 2007 Standard  <br/> |10 de outubro de 2017  <br/> |
|Project 2007 Professional  <br/> |10 de outubro de 2017  <br/> |
   
Para obter mais informações sobre os servidores do Office 2007 está atingindo aposentadoria, consulte [atualização do produtos de cliente e servidores do Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Qual end faz da média de suporte?

Project Server, como quase todos os produtos da Microsoft, tem um ciclo de vida de suporte durante o qual fornecemos novos recursos, correções de erros, correções de segurança e assim por diante. Esse ciclo de vida geralmente dura por 10 anos a partir da data de lançamento inicial do produto e final desse ciclo de vida é conhecido como o fim do produto do suporte. Porque o Project Server 2007 atingido seu fim do suporte em 10 de outubro de 2017, a Microsoft não fornecerá mais:
  
- Suporte técnico para problemas que podem ocorrer.
    
- Bug correções para os problemas que são descobertos e que pode afetar a estabilidade e a usabilidade do servidor.
    
- Correções de segurança para vulnerabilidades que são descobertas e pode fazer com que o servidor vulnerável a falhas de segurança.
    
- Atualizações de fuso horário.
    
Sua instalação do Project Server 2007 continuará a executar após essa data. No entanto, devido às alterações listadas acima, é altamente recomendável que você migre do Project Server 2007 assim que possível.
  
## <a name="what-are-my-options"></a>Quais são as opções de minha?

Se você estiver usando o Project Server 2007, você precisará explore as opções de migração, que são:
  
- Migrar para o Project Online
    
- Migre para uma versão mais recente do local do Project Server (preferencialmente 2016 do Project Server).
    
|**Por que eu prefere migrar para o Project Online**|**Por que eu prefere migrar para o Project Server 2016**|
|:-----|:-----|
| Tenho que os usuários móveis.  <br/>  Os custos para migrar são uma preocupação ganhar (hardware, software, horas e esforço para implementar, etc.).  <br/>  Após a migração, os custos para manter o meu ambiente são uma preocupação ganhar (por exemplo, atualizações automáticas, há uma garantia de tempo de atividade, etc.).  <br/> | Regras de negócios restringem me opere minha empresa na nuvem.  <br/>  Necessário controle das atualizações do meu ambiente.  <br/> |
   
> [!NOTE]
> Para obter mais informações sobre as opções para mover de seus servidores do Office 2007, consulte [recursos para ajudar a atualizar do Office 2007 servidores e clientes](upgrade-from-office-2007-servers-and-products.md). Observe que o Project Server não dá suporte a uma configuração híbrida desde o Project Server e Project Online não podem compartilhar o mesmo pool de recursos. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>Considerações importantes que você precisa tomar ao planejar migrar do Project Server 2007

Você precisa considerar o seguinte ao planejar migrar do Project Server 2007:
  
- **Obtenha ajuda de um parceiro da Microsoft** - atualização do Project Server 2007 pode ser um desafio e exige muito planejamento e preparação. Ele pode ser desafiador, especialmente se você não eram aquele para instalar e configurar o Project Server 2007 originalmente. Felizmente, há Microsoft Partners você pode transformar para que isso para uma sala, se você planeja migrar para o Project Server 2016 ou Project Online. Você pode pesquisar um Microsoft Partner para ajudá-lo no processo de migração no [Centro de parceiros da Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Você pode retirar uma lista de todos os Microsoft Partner com experiência em projeto pesquisando no termo *Gold Project e do gerenciamento de portfólio* . 
    
- **Planejar as personalizações** - Lembre-se de que muitas das personalizações você tiver trabalhando em seu ambiente do Project Server 2007 podem não funcionar durante a migração para o Project Server 2016 ou Project Online. Há algumas diferenças ganhar na arquitetura do Project Server entre versões, bem como os sistemas operacionais necessários, servidores de banco de dados e navegadores da web de cliente suportadas para trabalhar com a versão mais recente. Ter um plano sobre como testar ou reconstruir suas personalizações conforme necessário no novo ambiente. Planejando a atualização também será uma boa oportunidade para verificar se uma personalização específica seja realmente necessário ao se mover para frente. [Criar um plano para personalizações atuais durante a atualização para o SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) tem algumas ótimas informações gerais sobre a avaliação e planejamento para personalizações atuais durante a atualização. 
    
- **Tempo e compreensão** - planejamento, execução e teste de atualização levará muito tempo e esforço, especialmente se você estiver atualizando para o Project Server 2016. Por exemplo, se você estiver migrando do Project Server 2007 para o Project Server 2016, você será primeiro precisa migrar do Project Server 2007 para o Project Server 2010 e verifique se seus dados e faça a mesma coisa quando você migra para cada versão sucessiva. Talvez você queira Verifique com um Microsoft Partner para comparar os custos com suas estimativas de quanto tempo levará para que eles possam fazê-la e a que custo. 
    
## <a name="migrate-to-project-online"></a>Migrar para o Project Online

Se você optar por migrar do Project Server 2007 para o Project Online, você pode fazer o seguinte procedimento para migrar manualmente os dados do plano de projeto:
  
1. Salve seus planos de projeto do Project Server 2003 para. Formato MPP.
    
2. Usando o Project Professional 2013, Project Professional 2016 ou o cliente de Desktop Project Online, abra cada arquivo. mpp e, em seguida, salve e publicá-lo com o Project Online.
    
Você pode criar manualmente a configuração do PWA no Project Online (por exemplo, recrie quaisquer campos personalizados necessários ou calendários da empresa). Microsoft Partners também pode ajudá-lo com isso.
  
Principais recursos:
  
|**Recurso**|**Descrição**|
|:-----|:-----|
|[Introdução ao Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Como configurar e usar o Project Online.  <br/> |
|[Descrições de serviço on-line do projeto](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informações sobre os planos de projeto Online diferentes que estão disponíveis para você.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrar para uma versão mais recente do local do Project Server

Enquanto estamos altamente acredita que você pode obter a melhor experiência de usuário e o valor, migrando para o Project Online, também sabemos que algumas organizações precisam manter dados de projeto em um ambiente local. Se você optar por manter o seu projeto dados local, você pode migrar seu ambiente do Project Server 2007 para o Project Server 2010, Project Server 2013 ou 2016 do Project Server.
  
É recomendável que você migre para o Project Server 2016 se você não pode migrar para o Project Online. Project Server 2016 inclui todos os recursos e os aperfeiçoamentos incluídos com versões anteriores do Project Server e mais parecido com a experiência disponível com o Project Online (embora alguns recursos estão disponíveis somente no Project Online).
  
Após concluir cada migração, você deve verificar seus dados para certificar-se de que foram migrados com êxito.
  
> [!NOTE]
> Se você estiver considerando apenas migrando para o Project Server 2010, se você está limitado a uma solução local, é importante observar que ele tem apenas alguns anos mais de suporte à esquerda. Project Server 2010 com Service Pack 2, o fim do suporte data é 10/13/2020. Para obter mais informações sobre datas finais de suporte, consulte a [Política de ciclo de vida de produtos do Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Como migrar para o Project Server 2016?

As diferenças arquitetônicas entre o Project Server 2007 e Project Server 2016 impede que um caminho de migração direta. Isso significa que você precisará migrar os dados do Project Server 2007 para a próxima versão sucessiva do Project Server até que você atualizar para o Project Server 2016.
  
Você precisará fazer o seguinte para atualizar para o Project Server 2016:
  
1. Etapa 1: Migre do Project Server 2007 para o Project Server 2010.
    
2. Etapa 2: Migre do servidor do Project 2010 para o Project Server 2013.
    
3. Etapa 3: Migre do Project Server 2013 para o Project Server 2016.
    
Após concluir cada migração, você deve verificar seus dados para certificar-se de que foram migrados com êxito.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Etapa 1: Migrar do Project Server 2007 para o Project Server 2010

Para ter uma compreensão abrangente do que você precisa fazer para atualizar do Project Server 2007 para o Project Server 2010, consulte o conjunto de conteúdo de [atualizar para o Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) no TechNet. 
  
Principais recursos:
  
|**Recurso**|**Descrição**|
|:-----|:-----|
|[Visão geral da atualização do Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |Obtenha uma compreensão de alto nível do que você precisa fazer para atualizar do Project Server 2007 para o Project Server 2010.  <br/> |
|[Planejar a atualização do Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |Examinar considerações que precisam ser tomadas durante a atualização do Project Server 2007 para o Project Server 2010, incluindo os requisitos de sistema de planejamento.  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Como atualizar?

Enquanto os detalhes sobre como atualizar podem ser encontrados no conjunto de conteúdo de [atualização para o Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) , é importante entender que existem dois métodos distintos, que você pode usar a atualização: 
  
- **a atualização com anexação de banco de dados:** Esse método somente atualiza o conteúdo para seu ambiente e não as definições de configuração. Ela é necessária se você estiver atualizando do Office Project Server 2007 implantado em um hardware que suporta apenas um sistema operacional de servidor de 32 bits. Existem dois tipos de métodos de atualização de anexação de banco de dados: 
    
  - **Atualização completa de anexação de banco de dados** - migra os dados de projeto armazenados nos bancos de dados do Office Project Server 2007, mais os dados de site do Microsoft Project Web App (PWA) armazenados em um banco de dados de conteúdo do SharePoint. 
    
  - **Atualização do núcleo de anexação de banco de dados** - migra somente os dados de projeto armazenados nos bancos de dados do Project Server. 
    
- **Atualização in-loco**: os dados de configuração para o farm e todo o conteúdo no farm estão atualizados no hardware existente, em uma ordem fixa. Quando você inicia o processo de atualização in-loco, instalação leva todo o farm offline e os sites e sites do Microsoft Project Web App não estarão disponíveis até que a atualização é concluída e, em seguida, o programa de instalação reinicia o servidor. Depois que começar uma atualização in-loco, você não pode pausar a atualização ou reverter para a versão anterior. É altamente recomendável fazer uma imagem espelhada do seu ambiente de produção e fazer a atualização in-loco nesse ambiente e não seu ambiente de produção. 
    
Recursos adicionais:
  
- [SuperFlow para atualização do Microsoft Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Migração do Project Server 2007 para o Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Considerações sobre atualização das Web parts do Project Web App](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [Project Software Development Kit (SDK)](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>Etapa 2: Migrar para o Project Server 2013

Após a migração para o Project Server 2010 e verificando se os dados foram migrados com êxito, a próxima etapa é migrar os dados para o Project Server 2013.
  
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
    
### <a name="step-3-migrate-to-project-server-2016"></a>Etapa 3: Migrar para o Project Server 2016

Após a migração para o Project Server 2013 e verificando se os dados foram migrados com êxito, a próxima etapa é migrar os dados para o Project Server 2016.
  
Para ter uma compreensão abrangente do que você precisa fazer para a atualização do Project Server 2013 para o Project Server 2016, consulte a atualização para o conteúdo do Project Server 2016 definido no TechNet.
  
Principais recursos:
  
|**Recurso**|**Descrição**|
|:-----|:-----|
|[Visão geral do processo de upgrade para o Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |Obtenha uma compreensão de alto nível do que você precisa fazer para a atualização do Project Server 2013 para o Project Server 2016.  <br/> |
|[Plano para upgrade para o Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |Examinar considerações que precisam ser tomadas durante a atualização do Project Server 2013 para o Project Server 2016, incluindo de planejamento.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Informações importantes sobre como atualizar para esta versão

[Coisas que você precisa saber sobre o Project Server 2016 atualizar](https://go.microsoft.com/fwlink/p/?linkid=841827) informa algumas alterações importantes para a atualização para esta versão, que incluem: 
  
- Quando você cria o seu ambiente do Project Server 2016 ao qual você irá migrar os dados do Project Server 2013, observe que os arquivos de instalação do Project Server 2016 serão incluídos no SharePoint Server 2016. Para obter mais informações, consulte [implantar o Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Planos de recursos são reduzidos no Project Server 2016. Seus planos de recursos do Project Server 2013 serão migrados para contratos de recursos no Project Server 2016 e no Project Online. Consulte [Visão geral: compromissos com o recurso](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) para obter mais informações. 
    
## <a name="migrate-from-portfolio-server-2007"></a>Migrar do Portfolio Server 2007

Project Portfolio Server 2007 foi usado com o Project Server 2007 para otimização, priorização e estratégia de portfólio. Sem adicionais versões do Project Portfolio Server foram criadas após essa versão. No entanto, os recursos de gerenciamento de portfólio estão disponíveis no Project Server 2016 e a versão Premium do Project Online. Dados do Project Portfolio Server 2007 não podem ser migrados para qualquer um. Dados como impulsionadores de negócios precisará ser recriadas.
  
Outros recursos:
  
- [Descrições do serviço do Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): consulte os recursos de gerenciamento de portfólio que estão inclusos no Project Server 2016 e Premium on-line do projeto.
    
- [Guia de migração do Microsoft Office Project Portfolio Server 2007](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Tópicos relacionados

[Fim do SharePoint Server 2007 do mapa de suporte](sharepoint-2007-end-of-support.md)
  
[Recursos para ajudá-lo a atualizar do Office 2007 servidores e clientes](upgrade-from-office-2007-servers-and-products.md)
  

