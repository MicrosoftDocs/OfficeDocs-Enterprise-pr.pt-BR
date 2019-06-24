---
title: Roteiro de fim do suporte do Project Server 2010
ms.author: efrene
author: efrene
manager: pamg
ms.date: 06/03/2019
audience: ITPro
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
description: O suporte para ends para o Project Server 2010 termina em 13 de outubro de 2020. Use este artigo como um guia para atualizar para o Project online ou uma versão mais recente do Project Server no local.
ms.openlocfilehash: 86ab1534058d49094327c326d8367a08c14d725b
ms.sourcegitcommit: c763b0f28e1ce498aef5d5deb3b6324288da85ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2019
ms.locfileid: "35128698"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Roteiro de fim do suporte do Project Server 2010

O Project Server 2010 atingirá o fim do suporte em **13 de outubro de 2020**. Se você estiver usando o Project Server 2010 no momento, observe que esses outros produtos relacionados têm as seguintes datas de suporte:
  
|**Product**|**data do fim da suporte**|
|:-----|:-----|
|Project Portfolio Server 2010  <br/> |13 de outubro de 2020  <br/> |
|Padrão do Project 2010  <br/> |13 de outubro de 2020  <br/> |
|Project 2010 Professional  <br/> |13 de outubro de 2020  <br/> |
   
Para obter mais informações sobre os servidores do Office 2010 que atinjam o fim do suporte, consulte [Upgrade from Office 2010 Servers and Client Products](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>O que significa o fim do suporte?

O Project Server, como quase todos os produtos da Microsoft, tem um ciclo de vida de suporte durante o qual fornecemos novos recursos, correções de erros e atualizações de segurança. Esse ciclo de vida normalmente dura 10 anos a partir da data da versão inicial do produto, e o final desse ciclo de vida é conhecido como o fim do suporte do produto. Quando o Project Server 2010 atingir o fim do suporte em 13 de outubro de 2020, a Microsoft não fornecerá mais:
  
- Suporte técnico para problemas que podem ocorrer.
    
- Correções de erros descobertas e que podem afetar a estabilidade e a usabilidade do servidor.
    
- Correções de segurança para vulnerabilidades descobertas e que podem tornar o servidor vulnerável a brechas de segurança.
    
- Atualizações de fuso horário.
    
Sua instalação do Project Server 2010 continuará a ser executada após essa data. No entanto, devido às alterações listadas acima, é altamente recomendável migrar do Project Server 2010 o mais rápido possível.
  
## <a name="what-are-my-options"></a>Quais são as minhas opções?

Se você estiver usando o Project Server 2010, precisará explorar as opções de migração, que são:
  
- Migrar para o Project online
    
- Migre para uma versão local mais recente do Project Server (preferivelmente o Project Server 2019).
    
|**Por que eu prefiro migrar para o Project online?**|**Por que eu prefiro migrar para o Project Server 2019?**|
|:-----|:-----|
| Tenho usuários móveis ou remotos.  <br/>  Os custos para migrar servidores locais são uma grande preocupação (hardware, software, horas e esforço para implementar, etc.).  <br/>  Após a migração, os custos de manutenção do meu ambiente são uma grande preocupação (por exemplo, atualizações automáticas, tempo de atividade garantido, etc.).  <br/> | Regras de negócios restringe a operar minha empresa na nuvem.  <br/>  Preciso de controle das atualizações no meu ambiente.  <br/> |
   
> [!NOTE]
> Para obter mais informações sobre as opções de migração de seus servidores do Office 2010, consulte [recursos para ajudá-lo a atualizar de clientes e servidores do office 2010](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Observe que o Project Server não oferece suporte a uma configuração híbrida, já que o Project Server e o Project online não podem compartilhar o mesmo pool de recursos. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Considerações importantes que você precisa tomar ao planejar a migração do Project Server 2010

Você precisa considerar o seguinte ao planejar a migração do Project Server 2010:
  
- **Obter ajuda de um provedor de solução da Microsoft** – a atualização do Project Server 2010 pode ser um desafio e requer muito planejamento e preparação. Pode ser especialmente desafiador se você não fosse o para instalar e configurar o Project Server 2010 originalmente. 2019 no @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ @ Você pode pesquisar por um provedor de soluções da Microsoft para ajudá-lo com sua migração no [centro de provedores de soluções da Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). 
    
- **Planejar suas personalizações** – esteja ciente de que muitas das personalizações que você está trabalhando no seu ambiente do Project Server 2010 podem não funcionar ao migrar para o project Server 2019 ou para o Project online. Há grandes diferenças na arquitetura do Project Server entre as versões, bem como os sistemas operacionais necessários, os servidores de banco de dados e os navegadores da Web do cliente com suporte para trabalhar com a versão mais recente. Tenha um plano em vigor para testar ou reconstruir suas personalizações conforme necessário em seu novo ambiente. O planejamento da atualização também será uma boa oportunidade para verificar se uma personalização específica é realmente necessária à medida que você avança. [Criar um plano para personalizações atuais durante a atualização para o SharePoint 2013]( https://docs.microsoft.com/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013) tem algumas informações gerais excelentes sobre a avaliação e o planejamento de suas personalizações atuais durante a atualização. 
    
- O planejamento, a execução e o teste da atualização de **tempo e paciência** levarão muito tempo e esforço, especialmente se você estiver atualizando para o Project Server 2019. Por exemplo, se você estiver migrando do Project Server 2010 para o Project Server 2019, primeiro será necessário migrar do Project Server 2010 para o Project Server 2013 e, em seguida, verificar seus dados e, em seguida, fazer o mesmo quando migrar para cada versão sucessiva (para o Project Server 2016 e, em seguida, para o Project Server 2019). Você pode querer verificar com um provedor de soluções da Microsoft para comparar seus custos estimados com suas estimativas de quanto tempo levará para eles e em qual custo. 
    
## <a name="migrate-to-project-online"></a>Migrar para o Project online

Se você optar por migrar do Project Server 2010 para o Project online, poderá fazer o seguinte para migrar manualmente os dados do plano de projeto:
  
1. Salve seus planos de projeto do Project Server 2010 para o. Formato MPP.
    
2. Usando o Project Professional 2016, o Project Professional 2019 ou o cliente da área de trabalho do Project online, abra cada arquivo. mpp e salve e publique-o no Project online.
    
Você pode criar manualmente a configuração do PWA no Project online (por exemplo, recrie os campos personalizados ou calendários da empresa necessários). Os Microsoft Solution Providers também podem ajudá-lo com isso.
  
Principais recursos:
  
|**Recurso**|**Descrição**|
|:-----|:-----|
|[Introdução ao Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Como configurar e usar o Project online.  <br/> |
|[Descrição do Serviço do Project Online](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informações sobre os diferentes planos do Project online que estão disponíveis para você.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrar para uma versão local mais recente do Project Server

Embora acreditemos que você possa obter o melhor valor e a experiência do usuário migrando para o Project online, também entendemos que algumas organizações precisam manter os dados do projeto em um ambiente local. Se você optar por manter seus dados de projeto no local, poderá migrar seu ambiente do Project Server 2010 para o Project Server 2013, o Project Server 2016 ou o Project Server 2019.
  
Recomendamos migrar para o Project Server 2019 se não for possível migrar para o Project online. O Project Server 2019 inclui a maior parte da chave dos recursos e avanços incluídos nas versões anteriores do Project Server e mais se compara à experiência disponível com o Project online (embora alguns recursos estejam disponíveis somente no Project online).
  
Após concluir cada migração, você deve verificar seus dados para certificar-se de que foram migrados com êxito.
  
> [!NOTE]
> Se você estiver pensando em migrar somente para o Project Server 2013 se estiver limitado a uma solução local, é importante observar que ela tem apenas mais alguns anos de suporte à esquerda. O Project Server 2013 com Service Pack 2 data de término de suporte é 10/13/2023. Para obter mais informações sobre o fim das datas de suporte, consulte [política de ciclo de vida do produto da Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Como faço para migrar para o Project Server 2019?

As diferenças arquitetônicas entre o Project Server 2010 e o Project Server 2019 evitam um caminho de migração direta. Isso significa que você precisará migrar os dados do Project Server 2010 para a próxima versão sucessiva do Project Server até atualizar para o Project Server 2019.
  
Será necessário executar as seguintes etapas para atualizar o Project Server 2010 para o Project Server 2019:
  
1. Migrar para o Project Server 2013.
    
2. Migrar do Project serve 2013 para o Project Server 2016.
    
3. Migre do Project Server 2016 para o Project Server 2019.
    
Após concluir cada migração, você deve verificar seus dados para certificar-se de que foram migrados com êxito.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Etapa 1: migrar para o Project Server 2013

Sua primeira etapa na migração dos dados do Project Server 2010 para o Project Server 2019 é primeiro migrar para o Project Server 2013. 
  
Para obter uma compreensão abrangente do que você precisa fazer para atualizar do Project Server 2010 para o Project Server 2013, consulte [upgrade to project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822). 
  
Principais recursos:
  
|||
|:-----|:-----|
|[Visão geral do processo de atualização do Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Obtenha uma compreensão de alto nível do que você precisa fazer para atualizar do Project Server 2010 para o Project Server 2013.  <br/> |
|[Planejar a atualização para o Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Observe as considerações de planejamento que você precisa fazer ao atualizar do Project Server 2010 para o Project Server 2013, incluindo os requisitos do sistema.  <br/> |
   
[O que há de novo na atualização do Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) mostra algumas alterações importantes para a atualização desta versão, o mais notável: 
  
- Não há nenhuma atualização no local para o Project Server 2013. O método Database-Attach é o único método com suporte para atualização do Project Server 2010 para o Project Server 2013.
    
- O processo de atualização não só converterá os dados do Project Server 2010 no formato do Project Server 2013, mas também consolidará os quatro bancos de dados do Project Server 2010 em um único banco de dados do Project Web App.
    
- O SharePoint Server 2013 e o Project Server 2013 foram alterados para a autenticação baseada em declarações da versão anterior. Você precisará fazer considerações ao atualizar se estiver usando a autenticação clássica. Para saber mais, confira [Migrar da autenticação de modo clássico para a autenticação baseada em declarações SharePoint 2013]( https://docs.microsoft.com/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).
    
Principais recursos:
  
- [Visão geral do processo de atualização para o Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Atualizar seus bancos de dados e conjuntos de sites do Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagrama de processo de atualização do Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [A excelente consolidação do banco de dados, o Project Server 2010 para a migração 2013 em 8 etapas simples](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Etapa 2: migrar para o Project Server 2016

Após a migração para o Project Server 2013 e a verificação de que seus dados foram migrados com êxito, a próxima etapa é migrar seus dados para o Project Server 2016.
  
Para obter uma compreensão abrangente do que você precisa fazer para atualizar do Project Server 2013 para o Project Server 2016, consulte [upgrade to project server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016).
  
Principais recursos:
  
|||
|:-----|:-----|
|[Visão geral do processo de atualização do Project Server 2016](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Obtenha uma compreensão de alto nível do que você precisa fazer para atualizar do Project Server 2013 para o Project Server 2016.  <br/> |
|[Planejar a atualização para o Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Observe as considerações de planejamento que você precisa fazer ao atualizar do Project Server 2013 para o Project Server 2016.  <br/> |
   
As [coisas que você precisa saber sobre a atualização do Project Server 2016](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) lhe dizem algumas alterações importantes para atualizar para esta versão, que incluem: 
  
- Ao criar seu ambiente do Project Server 2016 para o qual você migrará os dados do Project Server 2013, observe que os arquivos de instalação do Project Server 2016 estão incluídos no SharePoint Server 2016. Para obter mais informações, consulte [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Os planos de recursos são preteridos no Project Server 2016. Seus planos de recursos do Project Server 2013 serão migrados para os compromissos de recursos no Project Server 2016 e no Project online. Consulte [visão geral: compromissos de recursos](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) para obter mais informações. 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Etapa 3: migrar para o Project Server 2019

Após a migração para o Project Server 2016 e a verificação de que seus dados foram migrados com êxito, a próxima etapa é migrar seus dados para o Project Server 2019.
  
Para obter uma compreensão abrangente do que você precisa fazer para atualizar do Project Server 2016 para o Project Server 2019, consulte [upgrade to project server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016).
  
Principais recursos:
  
|||
|:-----|:-----|
|[Visão geral do processo de atualização do Project Server 2019](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Obtenha uma compreensão de alto nível do que você precisa fazer para atualizar do Project Server 2013 para o Project Server 2016.  <br/> |
|[Planejar a atualização para o Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Observe as considerações de planejamento que você precisa fazer ao atualizar do Project Server 2016 para o Project Server 2019.  <br/> |
   
As [coisas que você precisa saber sobre a atualização do Project Server 2019](https://go.microsoft.com/fwlink/p/?linkid=841827) lhe dizem algumas alterações importantes para atualizar para esta versão, que incluem: 
  
- O processo de atualização migrará seus dados do banco de dados do Project Server 2016 para o banco de dados de conteúdo do SharePoint Server 2019.  O Project Server 2019 não criará mais seu próprio banco de dados do Project Server no farm do SharePoint Server.

- Após a atualização, esteja ciente de várias alterações no Project Web App.  Para obter uma descrição dessas, consulte [What ' s New in Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

  
Outros recursos:
  
- [Descrições do serviço do Project online](https://go.microsoft.com/fwlink/p/?linkid=841280): consulte os recursos de gerenciamento de portfólio incluídos no project Server 2016 e no Project Online Premium.
    
- [Guia de migração do Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Tópicos relacionados

[Atualizando do SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Atualização de clientes e servidores do Office 2010](upgrade-from-office-2010-servers-and-products.md)
  

