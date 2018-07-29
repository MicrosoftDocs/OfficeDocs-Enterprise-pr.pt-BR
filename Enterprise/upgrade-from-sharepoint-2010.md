---
title: Atualizando do SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 e o SharePoint Server 2010 estão se aproximando do fim do suporte. Use este artigo como guia para atualizar para o SharePoint Online ou uma versão mais recente do SharePoint Server no local.
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169863"
---
# <a name="upgrading-from-sharepoint-2010"></a>Atualizando do SharePoint 2010

Em 13 de outubro de 2020, Microsoft Office SharePoint Server 2010 atinge o fim do suporte. Este artigo fornece detalhes sobre os recursos para ajudar as pessoas a migrar seus dados existentes do SharePoint Server 2010 para o SharePoint Online, ou atualizar o seu servidor do SharePoint local.
  
## <a name="what-is-end-of-support"></a>Qual é o fim do suporte?

Quando o seu software do SharePoint Server 2010 e o SharePoint Foundation 2010 chega ao fim do seu ciclo de vida do suporte (o tempo durante o qual a Microsoft fornece novos recursos, correções de erros, correções de segurança e assim por diante) é chamado 'fim do software do suporte ', ou, às vezes, seu 'aposentadoria'. Ao final do suporte (ou EOS) de um produto, nada realmente encerra ou interrompe funcionando; No entanto, ao final do suporte de software, a Microsoft não são mais fornece:
  
- Suporte técnico para problemas que podem ocorrer;
    
- Correções de erros para problemas que são descobertos e que pode afetar a estabilidade e a usabilidade do servidor;
    
- Correções de segurança para vulnerabilidades que são descobertas e pode fazer com que o servidor vulnerável a falhas de segurança;
    
- Atualizações de fuso horário.
    
Isso significa, haverá nenhuma outra atualizações, patches, ou correções serão enviadas para o produto (incluindo patches/correções de segurança) e Microsoft Support será totalmente alteraram os esforços de suporte a versões mais recentes. À medida que se aproxima o fim do suporte do SharePoint Server 2010, você deve tirar proveito das oportunidades para reduzir os dados que não são mais necessários antes da atualização do produto e/ou migrando seus dados importantes.
  
> [!NOTE]
> Um ciclo de vida do software geralmente dura por 10 anos a partir da data de lançamento inicial do produto. Você pode procurar por [Parceiros da Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) que possa ajudar com a atualização para a próxima versão do software ou com migração do Office 365 (ou ambos). Certifique-se de que ter ciência de datas finais de suporte em críticas também das tecnologias subjacentes particularmente da versão do SQL server que você estiver usando com o SharePoint. 
  
## <a name="what-are-my-options"></a>Quais são as opções de minha?

Primeiro, verifique a data em que o suporte termina no [site do ciclo de vida do produto](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010). Em seguida, certifique-se de planejar seu horário de atualização ou migração conhecendo a essa data. Lembre-se de que seu produto *não parar de funcionar* em uma data listados, e você pode continuar a usá-las, mas que, desde que a sua instalação do patch será não mais aplicada após essa data, você vai querer uma estratégia que ajudarão você a mais suavemente transição para a próxima versão do produto. 
  
Essa matriz ajuda plotar um curso quando se trata de recursos do produto Migrando e dados do usuário:
  
|**fim do suporte ao produto**|**Bom**|**Melhor**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Implantação Híbrida do SharePoint  <br/> |SharePoint Server 2016 (no local)  <br/> |
|||Pesquisa do SharePoint nuvem híbrida  <br/> |
   
Se você escolher opções de low-end da escala (boa opções), você precisará iniciar o planejamento para atualização de outra logo após a conclusão da migração do SharePoint Server 2010. (fim do suporte para o SharePoint Server 2010 e o SharePoint Foundation 2010 são agendados para 13 de outubro de 2020, mas *esteja ciente* , você sempre deve verificar o [site do ciclo de vida do produto](https://support.microsoft.com/en-us/lifecycle) suas datas mais precisos!) 
  
## <a name="where-should-i-go-next"></a>Onde posso ir próximo?

SharePoint Server 2013 e SharePoint Foundation 2013 podem ser instalado no local em seus próprios servidores. Caso contrário, você pode usar o SharePoint Online, que é um serviço online que faz parte do Microsoft Office 365. Você pode optar por:
  
- Migrar para o SharePoint Online
    
- Atualização do SharePoint Server ou SharePoint Foundation no local
    
- Faça ambas as condições acima
    
- Implementar uma solução [híbrida do SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Lembre-se de que oculto custos associados à manutenção de um farm de servidores no futuro, manutenção ou migrando personalizações e atualizar o hardware dos quais depende o SharePoint Server. Se você ter ciência e atendeu a todos esses, ele será mais fácil continuar a atualização no local. Caso contrário, se você executar o seu farm em servidores herdados do SharePoint sem personalização pesada, você poderia se beneficiar uma migração planejada para o SharePoint Online. Também é possível que local nos produtos do SharePoint Server podem optar por colocar alguns dados no SharePoint Online para reduzir a quantidade de gerenciamento de hardware, mantendo todos os seus dados locais envolve. Talvez seja mais econômico mover alguns dos seus dados para o SharePoint Online.
  
> [!NOTE]
> Os administradores do SharePoint podem [criar uma assinatura do Office 365](https://go.microsoft.com/fwlink/?linkid=843152), configure um novo site do SharePoint Online e cortar para longe do SharePoint Server 2010, clareza, levando somente os documentos mais essenciais para os sites do SharePoint Online atualizados. A partir daí, todos os dados restantes podem ser esvaziados do site do SharePoint Server 2010 em arquivos mortos do local. 
  
|**SharePoint Online (SPO)**|**SharePoint Server no local**|
|:-----|:-----|
|Alto custo em tempo (plano / execução / verificação)  <br/> |Alto custo em tempo (plano / execução / verificação)  <br/> |
|Menor custo em fundos (aquisições de hardware)  <br/> |Custo mais alto na fundos (aquisições de hardware)  <br/> |
|Custo único na migração  <br/> |Custo único repetida por migração futura  <br/> |
|Custo total de propriedade de baixa / manutenção  <br/> |Alto custo total de propriedade / manutenção  <br/> |
   
Quando migrar para o Office 365, a única é movido vai ter um custo mais pesado em tempo gasto planejamento antecipado (enquanto você estiver organizando dados e decidir o que leve para a nuvem e o que deve ser deixar para trás). No entanto, depois que os dados são migrados, upgrades estarão automáticos a partir desse momento, ver enquanto você precisará não são mais gerenciar atualizações de hardware e software e o tempo de atividade do seu farm será feito por um contrato de nível de serviço ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrar para o SharePoint Online

Certifique-se de que o SharePoint Online oferece todos os recursos que você precisa examinando a descrição de serviço associado. Aqui está o link para todas as descrições do serviço Office 365:
  
[Descrições do serviço Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
No momento não um meio pelo qual você pode diretamente migrar do SharePoint Server 2010 (ou SharePoint Foundation 2010) para o SharePoint Online, portanto o volume de trabalho é manual. Isso dará a oportunidade para arquivar e remova a dados e os sites que não são mais necessários, antes da movimentação. Você pode arquivar outros dados em armazenamento. Também Lembre-se de que nem o SharePoint Server 2010 nem o SharePoint Foundation 2010 irá parar de funcionar no fim do suporte, para que os administradores possam ter um período durante o qual SharePoint ainda está em execução se esquecem de seus clientes mover alguns dos seus dados.
  
Se você atualizar para o SharePoint Server 2013 ou SharePoint Server 2016 e decide colocar dados no SharePoint Online, sua movimentação também pode envolver usando a [API de migração do SharePoint](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (para migrar informações para o OneDrive for Business). 
  
|**Pro online**|**Con online**|
|:-----|:-----|
|A Microsoft fornece o hardware SPO e toda a administração de hardware.  <br/> |Recursos disponíveis podem ser diferentes entre o SharePoint Server no local e o SPO.  <br/> |
|Você é o administrador global de sua assinatura e pode atribuir administradores a sites SPO.  <br/> |Algumas ações disponíveis para um administrador de Farm no SharePoint Server local não existirem (ou não são necessárias) à função de administrador do SharePoint no Office 365, mas a administração do SharePoint, são locais para administração do conjunto de sites e a propriedade do Site sua org.  <br/> |
|Microsoft aplica correções, corrige e atualiza a subjacente hardware e software (inclusive servidores SQL em que executa o SharePoint Online).  <br/> |Como não há nenhum acesso para o sistema de arquivos subjacente no serviço, algumas personalizações são limitadas.  <br/> |
|A Microsoft publica [Contratos de nível de serviço](https://go.microsoft.com/fwlink/?linkid=843153) e move rapidamente para resolver incidentes de nível de serviço.  <br/> |Backup e restauração e outras opções de recuperação são automatizadas pelo serviço no SharePoint Online - backups são sobrescritos se não for usados.  <br/> |
|Testes de segurança e ajuste de desempenho do servidor são executadas continuamente no serviço pela Microsoft.  <br/> |As alterações da interface do usuário e outro SharePoint recursos são instalados pelo serviço e talvez precisem ser ativados ou desativados.  <br/> |
|O Office 365 atende aos padrões do setor de muitos: [Conformidade do Office 365](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |Assistência de [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) para migração é limitada.  <br/> Grande parte da atualização vai ser manual ou por meio da API de migração de SPO descrito no [SharePoint Online e o mapa de conteúdo de migração do OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Nem engenheiros de suporte da Microsoft nem funcionários no datacenter têm admin acesso irrestrito à sua assinatura.  <br/> |Pode haver custos adicionais se a infraestrutura de hardware precisa ser atualizado para oferecer suporte a versão mais recente do SharePoint, ou se um farm secundário é necessário para a atualização.  <br/> |
|Parceiros podem auxiliar com o trabalho único de migrar os dados para o SharePoint Online.  <br/> |Nem todas as alterações para o SharePoint Online estão dentro de seu controle. Após a migração, o design diferenças em menus, bibliotecas e outros recursos temporariamente podem afetar a usabilidade.  <br/> |
|Produtos online são atualizados automaticamente entre o que significa que, embora talvez preterir recursos, não há nenhuma true fim do suporte do ciclo de vida de serviço.  <br/> |Não há um fim do ciclo de vida de suporte para o SharePoint Server (ou SharePoint Foundation), bem como servidores SQL subjacentes.  <br/> |
   
Se você decidiu criar um novo site do Office 365 e manualmente será migrada dados-lo conforme necessário, você pode ver seu direito de opções do Office 365 aqui:
  
[Opções de planos do Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Atualização do SharePoint Server no local

À medida que a versão mais recente do produto SharePoint local (SharePoint Server 2016), atualizações do SharePoint Server devem passar *em série* , isso significa que não é possível atualizar diretamente do SharePoint Server 2010 para o SharePoint 2016 do servidor. 
  
|||
|:-----|:-----|
||Serial atualização caminho * * *: SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** 2016 do SharePoint Server |
   
Se você optar por siga todo o caminho do SharePoint 2010 para SharePoint Server 2016, isso levará tempo e planejamento. Atualizações envolvem um custo em termos de administração, software e hardware atualizado (Lembre-se de que os servidores SQL também devem ser atualizados). Além disso, as personalizações podem precisar ser atualizado ou até mesmo abandonados. Certifique-se de que você colete anotações em todas as suas personalizações críticas antes de atualizar seu farm do SharePoint Server.
  
> [!NOTE]
> É possível manter seu final do farm do SharePoint 2010 de suporte, instalar um farm do SharePoint Server 2016 em um hardware novo (de modo que os farms separados executado lado a lado) e, em seguida, planejar e executar uma migração manual de conteúdo (para download e carregamento novamente o conteúdo, para exemplo). Há possíveis armadilhas a serem essas movimentações manuais (por exemplo, documentos provenientes da 2010 ter uma conta de modificação última atual com o alias da conta fazendo a movimentação manual) e algum trabalho deve ser feito antes do tempo (recriando sites, subsites, permissões e estruturas de lista). É uma boa hora para considerar o que você pode mover para armazenamento, ou não há mais de dados precisam. Isso pode reduzir o impacto da migração. De qualquer forma, limpe anteriormente seu ambiente para atualização. Certifique-se o farm existente for funcional antes da atualização e (com certeza) antes de encerrar! 
  
Lembre-se de examinar os **caminhos de atualização compatíveis e sem suportados**: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Se você tiver **personalizações**, é essencial para que ter um plano de sua atualização para cada etapa no caminho de migração: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro local**|**Con local**|
|:-----|:-----|
|Controle de todos os aspectos do seu Farm do SharePoint (e seu SQL) total do hardware do servidor para cima.  <br/> |Todas as quebras e correções são de responsabilidade da sua empresa (mas você pode envolver paga Microsoft Support se seu produto não estiver no fim do suporte):  <br/> |
|O conjunto completo de recursos do SharePoint Server no local com a opção de conectar seu farm local em uma assinatura do SharePoint Online via híbrida.  <br/> |Atualização, patches, correções de segurança, atualizações de hardware e todos os de manutenção do SharePoint Server e do farm do SQL são gerenciados no local.  <br/> |
|Acesso total para opções de personalização maiores do que com o SharePoint Online.  <br/> |[Padrões de conformidade suportados pelo Office 365](https://go.microsoft.com/fwlink/?linkid=843165) deve ser configurado manualmente no local.  <br/> |
|Testes de segurança e ajuste de desempenho do servidor, realizados em seu local (sob seu controle).  <br/> |O Office 365 pode disponibilizar recursos no SharePoint Online que não interoperam com o SharePoint Server no local  <br/> |
|Parceiros podem ajudar a migrar dados para a próxima versão do SharePoint Server (e depois).  <br/> |Os sites do SharePoint Server não usará automaticamente certificados [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) como é visto no SharePoint Online.  <br/> |
|Controle total das convenções de nomenclatura, backup e restauração e outras opções de recuperação no SharePoint Server local.  <br/> |SharePoint Server local é sensível ciclos de vida do produto.  <br/> |
   
### <a name="upgrade-resources"></a>Recursos de atualização

Começar, comparando os requisitos de hardware e software. Se você não atender aos requisitos básicos para a atualização no hardware atual, que pode significar que você precisa atualizar o hardware no farm ou servidores SQL pela primeira vez, ou se você decidir mover alguns porcentagem dos seus locais para o hardware 'verde' do SharePoint Online. Depois que você fizer sua avaliação, siga os caminhos de atualização com suporte e métodos.
  
- **Requisitos de hardware e software para**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [2016 do SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Limites de software e limites para**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [2016 do SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Visão geral do processo de atualização do**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [2016 do SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Criar uma solução híbrida do SharePoint entre o SharePoint Online e o SharePoint Server no local

Outra opção (que pode ser o melhor dos locais e online mundos para alguns migração precisa) é um híbrido, você pode conectar o SharePoint Server 2013 ou 2016 farms no SharePoint Online para criar um SharePoint híbrido: [Saiba mais sobre soluções híbridas SharePoint ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Se você decidir que um farm de servidores do SharePoint híbrido é o objetivo de migração, certifique-se de que para planejar quais sites e usuários, você deve mover para online, e que devem permanecer no local. Uma revisão e classificação de conteúdo do seu farm do SharePoint Server (determinar quais dados serão baixa, média ou alta impacto para a sua empresa) podem ser útil ao tomar essa decisão. Pode ser que a única coisa que você precisa compartilhar com o SharePoint Online é contas de usuário do (a) para login e (b) o índice de pesquisa do SharePoint Server — não pode ser criptografado até que você observar como os sites são usados. Se a sua empresa posteriormente decidir migrar todo o conteúdo para o SharePoint Online, você pode mover todos os demais contas e dados on-line e encerre o farm local e gerenciamento/administração do farm do SharePoint será feita por meio do Office 365 consoles a partir desse ponto em diante.
  
Certifique-se de estar familiarizado com os tipos existentes de híbrido e como configurar a conexão entre o seu farm do SharePoint no local e a sua assinatura do Office 365.
  
Uma boa maneira de ver como funciona a um farm do SharePoint híbrido é criando um [ambiente de desenvolvimento e teste do Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Depois que você tiver uma versão de avaliação ou adquirido de assinatura do Office 365, você estará no seu caminho até a criação de conjuntos de sites, webs e bibliotecas de documentos no SharePoint Online para o qual você pode migrar dados (manualmente, por use da API de migração, ou - se você quiser migrar meu Conteúdo do site ao OneDrive for Business - por meio do Assistente de híbrido).
  
> [!NOTE]
> Lembre-se de que seu farm do SharePoint Server 2010 primeiro precisará ser atualizado, no local, para o SharePoint Server 2013 ou SharePoint Server 2016 para usar a opção híbrida. SharePoint Foundation 2010 e o SharePoint Foundation 2013 não podem criar conexões híbrida com o SharePoint Online. 
  
## <a name="related-topics"></a>Tópicos relacionados

[Recursos para ajudar você a atualização do Office 2007 ou 2010 servidores e clientes](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[Práticas recomendadas para atualização do SharePoint 2010 para o SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[Resolver problemas de atualização do banco de dados no SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Procurar Microsoft Partners para ajudá-lo a atualização](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Política atualizada de manutenção do produto para SharePoint Server 2013](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[Política atualizada de manutenção do produto para SharePoint Server 2016](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

