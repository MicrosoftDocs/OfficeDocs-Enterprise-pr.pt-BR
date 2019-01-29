---
title: Roteiro de fim do suporte do SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
ms.audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: Em 10 de outubro de 2017, o suporte foi encerrado para o SharePoint Server 2007. Leia este artigo para saber mais sobre as opções de atualização, solução de problemas, práticas recomendadas, requisitos do sistema, as etapas de atualização e como obter ajuda da Microsoft Partners.
ms.openlocfilehash: b0d3eda690733b45ee82054e145642a5c76125d5
ms.sourcegitcommit: 792fe2ccc860517fe3dcbc9c668bae97f39ae7c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2019
ms.locfileid: "29604512"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Roteiro de fim do suporte do SharePoint Server 2007

Em **10 de outubro de 2017**, Microsoft Office SharePoint Server 2007 atingido o fim do suporte. Se você ainda não tiver começado a migração do SharePoint Server 2007 para o Office 365 ou uma versão mais recente do SharePoint Server local, este é o momento para começar a planejar. Este artigo fornece detalhes sobre os recursos para ajudar as pessoas a migrar dados para o SharePoint Online, ou atualizar o seu servidor do SharePoint local. 
  
## <a name="what-does-end-of-support-mean"></a>Qual end faz da média de suporte?

SharePoint Server, como quase todos os produtos da Microsoft, tem um ciclo de vida de suporte durante os quais a Microsoft fornece novos recursos, correções de erros, correções de segurança e assim por diante. Esse ciclo de vida geralmente dura por 10 anos a partir da data de lançamento inicial do produto e final desse ciclo de vida é conhecido como o fim do produto do suporte. No fim do suporte, a Microsoft não são mais fornece:
  
- Suporte técnico para problemas que podem ocorrer;
    
- Correções de erros para problemas que são descobertos e que pode afetar a estabilidade e a usabilidade do servidor;
    
- Correções de segurança para vulnerabilidades que são descobertas e pode fazer com que o servidor vulnerável a falhas de segurança; e 
    
- Atualizações de fuso horário.
    
No entanto seu farm do SharePoint Server 2007 ainda será operacional após 10 de outubro de 2017, a nenhum ainda mais atualizações, patches, ou correções serão enviadas para o produto (incluindo patches/correções de segurança) e Microsoft Support será totalmente deslocadas seus esforços de suporte para versões mais recentes do produto. Porque sua instalação será não tem mais suporte ou corrigidos, como a fim de abordagens de suporte você deve atualizar o produto ou migrar dados importantes.
  
> [!TIP]
> Se você já não tiver planejado para atualização ou migração, consulte: [Opções de migração do SharePoint 2007 a serem considerados](sharepoint-2007-migration-options.md), para alguns exemplos de onde começar. Você também pode pesquisar para [Parceiros da Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) que possa ajudar com atualização ou migração do Office 365 (ou ambos). 
  
Para obter mais informações sobre os servidores do Office 2007 está atingindo o fim do suporte, consulte [recursos para ajudar a atualizar do Office 2007 servidores e clientes](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Quais são as opções de minha?

Sua primeira parada deve ser o [site do ciclo de vida do produto](https://go.microsoft.com/fwlink/?linkid=843148). Se você tiver um produto da Microsoft no local que é a duração, você deve verificar seu lado da data de suporte assim que um ano ou isso check-out - ou seus migrações geralmente exigem - desde que você pode agendar atualização ou migrações. Ao escolher a próxima etapa, talvez seja útil pensar em termos do que seria ser tão bom, melhor e práticas quando se trata de recursos do produto. Aqui está um exemplo:
  
|**Bom**|**Melhor**|**Melhor**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Implantação Híbrida do SharePoint  <br/> |SharePoint Server 2016  <br/> |
|||Implantação Híbrida do SharePoint  <br/> |
   
Se você escolher opções de low-end da escala (BOM o suficiente), lembre-se você precisará começar a planejar a atualização muito breve após a migração do SharePoint Server 2007 é concluída. (o fim do suporte para o SharePoint Server 2007 é de 10 de outubro de 2017. Observe que essas datas estão sujeitos a alterações e verificar o [site do ciclo de vida do produto](https://support.microsoft.com/en-us/lifecycle).)
  
## <a name="where-can-i-go-next"></a>Onde posso próximo?

SharePoint Server pode ser instalado no local em seus próprios servidores, ou você pode usar o SharePoint Online, que é um serviço online que faz parte do Microsoft Office 365. Você pode optar por:
  
- Migrar para o SharePoint Online
    
- Atualização do SharePoint Server no local
    
- Faça ambas as condições acima
    
- Implementar uma solução [híbrida do SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Lembre-se de que oculto custos associados à manutenção de um farm de servidores no futuro, manutenção ou migrando personalizações e atualizar o hardware dos quais depende o SharePoint Server. Ter um farm do SharePoint Server no local é gratificante se ele é uma necessidade; Caso contrário, se você executar o seu farm em servidores herdados do SharePoint, sem personalização pesada, você pode beneficiar uma migração planejada para o SharePoint Online.
  
> [!IMPORTANT]
> Há outra opção se o conteúdo no SharePoint 2007 raramente é usado. Alguns administradores do SharePoint pode optar por [criar uma assinatura do Office 365](https://go.microsoft.com/fwlink/?linkid=843152), configure um novo site do SharePoint Online e cortar para longe do SharePoint 2007, clareza, levando somente os documentos mais essenciais para os sites do SharePoint Online atualizados. A partir daí, dados podem ser esvaziados do site do SharePoint 2007 em arquivos mortos. Dê ideia de como os usuários trabalham com dados sua instalação do SharePoint 2007. Pode haver criativas maneiras de resolver este problema! 
  
|**SharePoint Online (SPO)**|**SharePoint Server no local**|
|:-----|:-----|
|Alto custo em tempo (plano / execução / verificação)  <br/> |Alto custo em tempo (plano / execução / verificação)  <br/> |
|Menor custo em fundos (aquisições de hardware)  <br/> |Custo mais alto na fundos (hardware + desenvolvedores / administradores)  <br/> |
|Custo único na migração  <br/> |Custo único repetida por migração futura  <br/> |
|Custo total de propriedade de baixa / manutenção  <br/> |Alto custo total de propriedade / manutenção  <br/> |
   
Quando você migra para o Office 365, a movimentação de uma única vez terá um custo mais pesado antecipado, enquanto você estiver organizando dados e decidir o que leve para a nuvem e o que deve ser deixar para trás. No entanto, upgrades estarão automáticos a partir desse momento, não há mais você precisará gerenciar atualizações de hardware e software e o tempo de atividade do seu farm será feito por um contrato de nível de serviço ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrar para o SharePoint Online

Certifique-se de que o SharePoint Online tem todos os recursos que você precisa examinando a descrição de serviço associado. Aqui está o link para todas as descrições do serviço Office 365:
  
[Descrições do Serviço do Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
Há um meio direto para migrar do SharePoint 2007 para o SharePoint Online; sua mudança para o SharePoint Online seria feita manualmente. Se você atualizar para o SharePoint Server 2013 ou SharePoint Server 2016, sua movimentação também pode envolver usando a API de migração do SharePoint (para migrar informações para o OneDrive for Business, por exemplo).
  
|**Pro online**|**Con online**|
|:-----|:-----|
|A Microsoft fornece o hardware SPO e toda a administração de hardware.  <br/> |Recursos disponíveis podem ser diferentes entre o SharePoint Server no local e o SPO.  <br/> |
|Você é o administrador global de sua assinatura e pode atribuir administradores a sites SPO.  <br/> |Algumas ações disponíveis para um administrador de Farm no SharePoint Server no local não existirem (ou não é necessárias) incluído à função de administrador do SharePoint no Office 365.  <br/> |
|Microsoft aplica correções, corrige e atualiza a base de hardware e software.  <br/> |Como não há nenhum acesso para o sistema de arquivos subjacente no serviço, algumas personalizações são limitadas.  <br/> |
|A Microsoft publica [Contratos de nível de serviço](https://go.microsoft.com/fwlink/?linkid=843153) e move rapidamente para resolver incidentes de nível de serviço.  <br/> |Backup e restauração e outras opções de recuperação são automatizadas pelo serviço no SharePoint Online - backups são sobrescritos se não for usados.  <br/> |
|Testes de segurança e ajuste de desempenho do servidor são executadas continuamente no serviço pela Microsoft.  <br/> |As alterações da interface do usuário e outro SharePoint recursos são instalados pelo serviço e talvez precisem ser ativados ou desativados.  <br/> |
|O Office 365 atende aos padrões do setor de muitos: [Conformidade do Office 365](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |Assistência de [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) para migração é limitada.  <br/> Grande parte da atualização vai ser manual ou por meio da API de migração de SPO descrito no [SharePoint Online e o mapa de conteúdo de migração do OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Nem engenheiros de suporte da Microsoft nem funcionários no datacenter têm admin acesso irrestrito à sua assinatura.  <br/> |Pode haver custos adicionais se a infraestrutura de hardware precisa ser atualizado para oferecer suporte a versão mais recente do SharePoint, ou se um farm secundário é necessário para a atualização.  <br/> |
|Parceiros podem auxiliar com o trabalho único de migrar os dados para o SharePoint Online.  <br/> ||
|Produtos online são atualizados automaticamente entre o que significa que, embora talvez preterir recursos, não há nenhuma true fim do suporte de serviço.  <br/> ||
   
Se você decidiu criar um novo site do Office 365 e manualmente será migrada dados-lo conforme necessário, você pode ver seu direito de opções do Office 365 aqui:
  
[Opções de planos do Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Atualização do SharePoint Server no local

Não há historicamente para ignorar versões em atualizações do SharePoint, pelo menos não desde a versão do SharePoint Server 2016. Isso significa upgrades vá em série:
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
Entrem em todo o caminho do SharePoint 2007 para SharePoint Server 2016 significará um investimento significativo de tempo e envolverá a um custo em termos de hardware atualizado (Lembre-se de que os servidores SQL também devem ser atualizados), software e administração. Personalizações precisará ser atualizada ou abandonados, de acordo com o nível de importância do recurso.
  
> [!NOTE]
> É possível manter seu farm do SharePoint 2007 fim da vida útil, instale um farm do SharePoint Server 2016 em novo hardware (de modo que os farms separados executado lado a lado) e, em seguida, planejar e executar uma migração manual de conteúdo (para download e carregamento novamente o conteúdo, para exemplo). Lembre-se de alguns das armadilhas de movimentações manuais (por exemplo, se move de substituição de última modificação conta com o alias da conta fazendo a movimentação manual de documentos) e o trabalho que precisa ser feito antes do tempo (por exemplo, a recriação de sites, subsites, permissões e lista estruturas). Novamente, este é um tempo para considerar os quais você pode mover para armazenamento, ou não há mais necessidade, uma ação que pode reduzir o impacto da migração de dados.
  
De qualquer forma, limpe anteriormente seu ambiente para atualização. Certifique-se o farm existente for funcional antes da atualização e (com certeza) antes de encerrar! 
  
Lembre-se de examinar os **caminhos de atualização compatíveis e sem suportados**: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Se você tiver **personalizações**, é essencial para que ter um plano de sua atualização para cada etapa no caminho de migração: 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro local**|**Con local**|
|:-----|:-----|
|Controle total de todos os aspectos do seu Farm do SharePoint, de hardware do servidor de backup.  <br/> |Todas as quebras e correções são de responsabilidade da sua empresa (possam interagir paga Microsoft Support se seu produto não estiver no fim do suporte):  <br/> |
|O conjunto completo de recursos do SharePoint Server no local com a opção de conectar seu farm local em uma assinatura do SharePoint Online via híbrida.  <br/> |Atualização, patches, correções de segurança e manutenção de todos os do SharePoint Server gerenciado no local.  <br/> |
|Acesso total para maior personalização.  <br/> |[Padrões de conformidade suportados pelo Office 365](https://go.microsoft.com/fwlink/?linkid=843165) deve ser configurado manualmente no local.  <br/> |
|Testes de segurança e ajuste de desempenho do servidor, realizados em seu local (está sob o controle de suas).  <br/> |O Office 365 pode disponibilizar recursos no SharePoint Online que não interoperam com o SharePoint Server no local  <br/> |
|Parceiros podem ajudar a migrar dados para a próxima versão do SharePoint Server (e depois).  <br/> |Os sites do SharePoint Server não usará automaticamente certificados [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) como é visto no SharePoint Online.  <br/> |
|Controle total das convenções de nomenclatura, backup e restauração e outras opções de recuperação no SharePoint Server local.  <br/> |SharePoint Server local é sensível ciclos de vida do produto.  <br/> |
   
### <a name="upgrade-resources"></a>Recursos de atualização

Comece sabendo que você atende os requisitos de hardware e software, então follow suporte para métodos de atualização.
  
- **Requisitos de hardware e software para**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [do SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [2016 do SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Limites de software e limites para**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [do SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [2016 do SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Visão geral do processo de atualização do**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [do SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [2016 do SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Criar uma solução híbrida do SharePoint entre o SharePoint Online e no local

Caso a resposta às suas necessidades de migração em algum lugar entre o autocontrole oferecido pelo local e o menor custo de propriedade oferecido pelo SharePoint Online, você pode conectar SharePoint Server 2013 ou 2016 farms no SharePoint Online, por meio de híbridas. [Saiba mais sobre soluções híbridas SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Se você decidir que um farm de servidores do SharePoint híbrido beneficiarão seu negócio, familiarize-se com os tipos existentes de híbrido e como configurar a conexão entre o seu farm do SharePoint no local e a sua assinatura do Office 365.
  
Uma boa maneira de ver como isso funciona é criando um [ambiente de desenvolvimento e teste do Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Depois que você tiver uma versão de avaliação ou adquirido de assinatura do Office 365, você estará no seu caminho até a criação de conjuntos de sites, webs e bibliotecas de documentos no SharePoint Online para o qual você pode migrar dados (manualmente, por use da API de migração, ou - se você quiser migrar meu Conteúdo do site ao OneDrive for Business - por meio do Assistente de híbrido).
  
> [!NOTE]
> Lembre-se de que o seu farm do SharePoint 2007 precisará ser atualizado, no local, para o SharePoint Server 2013 ou SharePoint Server 2016 para usar a opção híbrida 
  
## <a name="related-topics"></a>Tópicos relacionados

[Solucionar problemas e continuar a atualização (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[Solucionar problemas de atualização (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[Resolver problemas de atualização do banco de dados no SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Procurar Microsoft Partners para ajudá-lo a atualização](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Recursos para ajudá-lo a atualizar do Office 2007 servidores e clientes](upgrade-from-office-2007-servers-and-products.md)
  

