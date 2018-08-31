---
title: Fim do Exchange 2010 do mapa de suporte
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 está se aproximando fim do suporte. Use este mapa de planejamento como um guia para preparar a atualização para o Exchange Online ou uma versão mais recente do Exchange Server local.
ms.openlocfilehash: e655edcc38723acd622fc6abc62a00d3f3e36738
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915186"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Fim do Exchange 2010 do mapa de suporte

Em **14 de janeiro de 2020**, o Exchange Server 2010 alcançará o fim do suporte. Se você ainda não já começou a migração do Exchange 2010 para o Office 365 ou Exchange 2016, agora é a hora de início do seu planejamento. 
  
## <a name="what-does-end-of-support-mean"></a>Qual end faz da média de suporte?

Exchange Server, como quase todos os produtos da Microsoft, tem um ciclo de vida de suporte durante o qual fornecemos novos recursos, correções de erros, correções de segurança e assim por diante. Esse ciclo de vida geralmente dura por 10 anos a partir da data de lançamento inicial do produto e final desse ciclo de vida é conhecido como o fim do produto do suporte. Quando o Exchange 2010 atinge o final do suporte em 14 de janeiro de 2020, Microsoft não fornecerá mais:
  
- Suporte técnico para problemas que podem ocorrer;
    
- Correções de erros para problemas que são descobertos e que pode afetar a estabilidade e a usabilidade do servidor;
    
- Correções de segurança para vulnerabilidades que são descobertas e pode fazer com que o servidor vulnerável a falhas de segurança;
    
- Atualizações de fuso horário.
    
Sua instalação do Exchange 2010 continuará a executar após essa data. No entanto, devido às alterações listadas acima, é altamente recomendável que você migre do Exchange 2010 assim que possível.
  
Para obter mais informações sobre os servidores do Office 2010 próximo do fim do suporte, consulte [recursos para ajudar a atualizar do Office 2010 de servidores e clientes](upgrade-from-office-2010-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Quais são as opções de minha?

Com o Exchange 2010 está atingindo o seu fim do suporte, este é um ótimo momento para explorar suas opções e preparar um plano de migração. É possível:
  
- Migrar para o Office 365 usando a transferência, expressas ou migração híbrida; 
    
- Migre seus servidores Exchange 2010 para uma versão mais recente do Exchange em seus servidores no local.
    
As seções a seguir exploram cada opção mais detalhadamente.
  
### <a name="migrate-to-office-365"></a>Migrar para o Office 365

Migrar seu email para o Office 365 é sua opção de melhor e mais simples para ajudá-lo a desativar a sua implantação do Exchange 2010. Com uma migração para o Office 365, você pode fazer um único salto da tecnologia antigo aos recursos de última geração, como:
  
- Recursos de conformidade, como políticas de retenção In-loco e retenção de litígio, in-loco eDiscovery e muito mais;
    
- Equipes da Microsoft;
    
- Power BI;
    
- Caixa de entrada focada;
    
- Me aprofundar Analytics;
    
- APIs REST de acesso programático aos emails, calendários, contatos e assim por diante.
    
O Office 365 também obtém experiências e nos novos recursos primeiro e você e seus usuários geralmente podem começar a usá-los imediatamente. Além dos novos recursos, você não precisará se preocupar com:
  
- Aquisição e manutenção de hardware;
    
- Pagar por aquecimento e o resfriamento dos seus servidores;
    
- Mantendo atualizado em correções de segurança, produto e fuso horário;
    
- Manutenção de armazenamento e software para dar suporte a requisitos de conformidade;
    
- Atualizando para uma nova versão do Exchange - estiver sempre a versão mais recente do Exchange no Office 365.
    
#### <a name="how-should-i-migrate-to-office-365"></a>Como posso migrar para o Office 365?

Dependendo da sua organização, você tem algumas opções que vai ajudá-lo a chegar ao Office 365. Ao escolher uma opção de migração, você precisa considerar algumas coisas como o número de estações ou você precisa mover as caixas de correio, quanto tempo você deseja que a migração para o último e se é necessário que uma integração perfeita entre sua instalação local e o Office 365 durante a migração. Esta tabela mostra as opções de migração e fatores mais importantes que vai determinar qual método você usará.
  
|**Opção de migração**|**Tamanho da organização**|**Duração**|
|:-----|:-----|:-----|
|Migração de substituição  <br/> |Menos de 150 estações  <br/> |Uma semana ou menos  <br/> |
|Migração Express  <br/> |Menos de 150 estações  <br/> |Algumas semanas ou menos  <br/> |
|Migração híbrida completo  <br/> |Mais de 150 estações  <br/> |Algumas semanas ou mais  <br/> |
   
As próximas seções fornecem uma visão geral dos métodos a seguir. Confira [Decida em um caminho de migração](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) para aprender os detalhes de cada método. 
  
#### <a name="cutover-migration"></a>Migração de substituição

Uma migração de substituição é uma onde, em pré-selecionada data e hora, você migrará todas as suas caixas de correio, grupos de distribuição, contatos e assim por diante, para o Office 365; Quando tiver terminado, você vai desligar seus servidores do Exchange no local e começar a usar o Office 365 exclusivamente.
  
O método de migração é ótimo para pequenas organizações que não possuem muitos muito caixas de correio, deseja ir para o Office 365 rapidamente e não deseja lidar com algumas da complexidade dos outros métodos. Mas ele também um pouco limitado porque ele deve ser concluído em uma semana ou menos e porque ele requer que os usuários reconfigurar os seus perfis do Outlook. Durante a migração pode lidar com até 2.000 caixas de correio, é altamente recomendável que você migra um máximo de 150 caixas de correio com este método. Se você tentar migrar mais de 150 caixas de correio, você poderia ficar esgotado o tempo necessário para transferir todas as caixas de correio antes seu prazo e sua equipe pode obter o suporte de TI sobrecarregado ajudando os usuários reconfigure o Outlook.
  
Se você estiver pensando sobre fazendo uma migração gradual, aqui estão algumas coisas a considerar considerar:
  
- O Office 365 precisará conectar-se a seus servidores Exchange 2010 usando o Outlook em qualquer lugar através da porta TCP 443;
    
- Todas as caixas de correio local serão movidas para o Office 365;
    
- Você precisará de uma conta de administrador local que tenha acesso ao ler o conteúdo de caixas de correio dos usuários;
    
- O Exchange 2010 aceitou os domínios que você deseja usar no Office 365 necessidade para ser adicionado como domínios verificados no serviço;
    
- Entre o momento em que você inicia a migração e quando você começar a fase de conclusão, Office 365 periodicamente será sincronizado com o Office 365 e caixas de correio local. Isso permite que você concluir a migração sem se preocupar eletrônico sejam deixado para trás em suas caixas de correio local;
    
- Os usuários receberão novas senhas temporárias para sua conta do Office 365 precisará alterar quando eles fazem logon suas caixas de correio pela primeira vez;
    
- Você precisará de uma licença do Office 365 que inclui o Exchange Online para cada caixa de correio de usuário que você migrar;
    
- Os usuários precisarão configurar um novo perfil do Outlook em cada um dos seus dispositivos e baixar seus emails novamente. A quantidade de email que o Outlook baixará pode variar. Para obter mais informações, dê uma olhada em [alterar quanto mail para manter offline](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Para saber mais sobre a migração de transferência, dê uma olhada:
  
- [O que você precisa saber sobre uma migração de substituição de email para o Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Executar uma migração de substituição de email para o Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="express-migration"></a>Migração Express

Uma migração express é um onde você tinha a algumas centenas caixas de correio que você deseja migrar para o Office 365, pode concluir a migração em algumas semanas e não é necessário qualquer um dos recursos de migração do híbrida avançadas, como informações de calendário livre/ocupado compartilhados.
  
Migração Express é ótima para organizações que precisam levar mais tempo para migrar suas caixas de correio para o Office 365, mas ainda planejar concluir a migração em algumas semanas. Você obter alguns benefícios da migração híbrida completo mais avançado sem muitos da complexidade. Você pode controlar quantos e quais, caixas de correio são migrados em um determinado momento; Caixas de correio do Office 365 serão criadas com o nome de usuário e senhas de suas contas de local; e, ao contrário de migrações de transferência, os usuários não será necessário recriar seus perfis do Outlook.
  
Se você estiver pensando sobre fazendo uma migração em estágios, aqui estão algumas coisas a considerar:
  
- O Office 365 precisará conectar-se a seus servidores Exchange 2010 usando o Outlook em qualquer lugar através da porta TCP 443;
    
- Você precisará executar uma sincronização de diretório ocasional entre seus servidores locais do Active Directory e o Office 365;
    
- Os usuários poderão fazer logon suas caixas de correio do Office 365 usando o mesmo nome de usuário e senha que eles estavam usando quando suas caixas de correio foi migrada;
    
- Você precisará de uma licença do Office 365 que inclui o Exchange Online para cada caixa de correio de usuário que você migrar;
    
- Os usuários não precisam configurar um novo perfil do Outlook na maioria dos seus dispositivos (alguns telefones Android mais antigos talvez seja necessário um novo perfil) e não será necessário fazer o download novamente a seus emails.
    
Para saber mais sobre a migração em estágios, dê uma olhada na [Híbrida mínima de uso rapidamente migrar caixas de correio do Exchange para o Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)
  
#### <a name="full-hybrid"></a>Híbrido completo

Uma migração híbrida completo é aquele onde sua organização tem várias centenas, até dezenas de milhares, de caixas de correio e você deseja mover alguns ou todos eles para o Office 365. Como essas migrações são geralmente longo prazo, migrações híbridas tornam possível:
  
- Mostrar as informações do calendário livre/ocupado para usuários de usuários locais no Office 365 e vice-versa;
    
- Ver uma lista de endereços global unificada que contém os destinatários no local e o Office 365;
    
- Exibir cartões de destinatário de Outlook completos para todos os usuários, independentemente se eles estão no local ou no Office 365;
    
- Email comunicação segura entre os servidores Exchange locais e Office 365 usando o TLS e certificados;
    
- Trate as mensagens enviadas entre os servidores do Exchange no local e o Office 365 como internos, permitindo-lhes:
    
  - Ser avaliado corretamente e processados pelos agentes de transporte e conformidade direcionamento de mensagens internas;
    
  - Desvio pelos filtros antispam.
    
Migrações híbridas completo são recomendadas para as organizações que esperam permaneçam em uma configuração híbrida para muitos meses ou mais. Você obterá os recursos listados anteriormente nesta seção, além de sincronização de diretórios, melhores recursos de conformidade integrada e a capacidade de mover caixas de correio de e para o Office 365 usando movimentações de caixa de correio online. O Office 365 se torna uma extensão da sua organização local.
  
Se você estiver pensando sobre fazendo uma migração completa híbrida, aqui estão algumas coisas a considerar:
  
- Migrações híbridas completo não são adequadas para todos os tipos de organizações. Devido à complexidade das migrações híbridas completo, as organizações com menos de algumas centenas de caixas de correio normalmente não vejo benefícios que justificam o esforço e o custo necessário para configurar um. Se isso SOA como a sua organização, é altamente recomendável que você considere as migrações em estágios ou de Cutover em vez disso;
    
- O Office 365 precisará conectar-se a um servidor Exchange 2010 usando o Outlook em qualquer lugar através da porta TCP 443;
    
- Você precisará configurar a sincronização de diretório usando o Windows Azure Active Directory se conectar (AADConnect) entre seus servidores locais do Active Directory e o Office 365;
    
- Os usuários poderão fazer logon suas caixas de correio do Office 365 usando o mesmo nome de usuário e senha que usam quando fazem logon na rede local (requer o Azure Active Directory Connect com sincronização de senha e/ou serviços de Federação do Active Directory);
    
- Você precisará de uma licença do Office 365 que inclui o Exchange Online para cada caixa de correio de usuário que você migrar;
    
- Os usuários não precisam configurar um novo perfil do Outlook na maioria dos seus dispositivos (alguns telefones Android mais antigos talvez seja necessário um novo perfil) e não será necessário fazer o download novamente a seus emails.
    
Se um sons de migração completa híbrida certa para você, dê uma olhada nos seguintes recursos para ajudá-lo no processo de migração:
  
- [Assistente de implantação do Exchange](https://aka.ms/exdeploy)
    
- [Implantações híbridas do Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [Assistente de Configuração Híbrida](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [Perguntas frequentes do Assistente de Configuração Híbrida](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [Pré-requisitos de implantação híbrida](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrar para uma versão mais recente do Exchange Server

Enquanto estamos altamente acredita que você pode obter a melhor experiência de usuário e o valor por meio da migração para o Office 365, também sabemos que algumas organizações precisam manter seu email no local. Isso poderia ser devido a requisitos normativos garantir que os dados não é armazenados em um data center localizado em outro país e assim por diante. Se você optar por manter o seu email local, você pode migrar seu ambiente do Exchange 2010 para Exchange 2013 ou 2016 do Exchange.
  
É recomendável que você migre para Exchange 2016 se você não pode migrar para o Office 365. Exchange 2016 inclui todos os recursos e os aperfeiçoamentos incluídos com versões anteriores do Exchange e mais parecido com a experiência disponível com o Office 365 (embora alguns recursos estão disponíveis somente no Office 365). Confira apenas algumas das coisas que você tiver sido ausentes abrindo diante:
  
|**Versão do Exchange**|**Recursos**|
|:-----|:-----|
|Exchange 2013  <br/> | Arquitetura simplificada, reduzindo o número de funções de servidor para três (caixa de correio, acesso para cliente, transporte de borda)  <br/>  Políticas de prevenção de perda dados (DLP) que ajudam a manter o vazamento de informações confidenciais  <br/>  Significativamente Outlook Web App experiência aprimorada  <br/> |
|Exchange 2016  <br/> | *Recursos do Exchange 2013 e …*  <br/>  Ainda mais as funções de servidor simplificado para acabou de caixa de correio e transporte de borda  <br/>  DLP aprimorada, juntamente com a integração com o SharePoint  <br/>  Resiliência de banco de dados aprimorado  <br/>  Colaboração de documentos online  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>Qual versão deve migrar para?

Recomendamos que você inicialmente pressupõe que você migrará para 2016 do Exchange. Em seguida, use as informações a seguir para confirmar sua pressuposição ou eliminar os 2016 do Exchange. Se você não pode migrar para o Exchange 2016 para um ou outro motivo, o mesmo processo com o Exchange 2013 e assim por diante.
  
|**Consideração**|**Mais informações**|
|:-----|:-----|
|Datas finais de suporte  <br/> | Como o Exchange 2010, cada versão do Exchange tem seu próprio final da data de suporte:  <br/> **Exchange 2013** - de 2023 abril  <br/> **Exchange 2016** - de 2025 de outubro  <br/>  Quanto mais cedo final da data de suporte, o antes você precisará realizar a migração de outra. Abril de 2023 é muito mais próximo do que você pensa!<br/> |
|Caminho de migração para o Exchange 2013 ou 2016  <br/> |Aqui estão as fases gerais para migrar para o Exchange 2013:  <br/> Instalar o Exchange 2013 ou 2016 em seus serviços de movimentação de organização existentes do Exchange 2010 e outra infra-estrutura para o Exchange 2013 ou 2016 mover as caixas de correio e pastas públicas para o Exchange 2013 ou descomissionamento 2016 restantes servidores Exchange 2010 |
|Coexistência de versão  <br/> |Ao migrar para o Exchange 2013 ou Exchange 2016, você pode instalar tanto a versão em uma organização existente do Exchange 2010. Isso permite que você instale um ou mais servidores Exchange 2013 ou Exchange 2016 e realizar a migração.  <br/> |
|Hardware de servidor  <br/> | Requisitos de hardware de servidor foram alterados do Exchange 2010. Você precisará certificar-se de que o hardware que você vai usar é compatível. Você pode encontrar mais informações sobre requisitos de hardware para cada versão aqui:<br/> [Requisitos do sistema do Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Requisitos do sistema do Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/>  Você encontrará com as melhorias significativas no desempenho do Exchange e a maior capacidade de computação e a capacidade de armazenamento em servidores mais recentes, você provavelmente precisará de menos servidores para suportar o mesmo número de caixas de correio.  <br/> |
|Versão do sistema operacional  <br/> | As versões de mínimos do sistema operacional com suporte para cada versão são:  <br/> **Exchange 2016** Windows Server 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/>  Você pode encontrar mais informações sobre o suporte ao sistema operacional na [Matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Nível funcional do Active Directory floresta  <br/> | Os mínimo com suporte do Active Directory níveis funcionais de floresta de cada versão são:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/>  Você pode encontrar mais informações sobre o suporte de nível funcional de floresta na [Matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Versões de cliente do Office  <br/> | As versões mínimas do cliente Office com suporte para cada versão são:  <br/> **Exchange 2016** Office 2010 (com as atualizações mais recentes)  <br/> **Exchange 2013** Office 2007 SP3  <br/>  Você pode encontrar mais informações sobre o suporte de cliente do Office na [Matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Como migrar?

Se você tiver decidido que você deseja manter seu email local, você pode usar os seguintes recursos para ajudá-lo no processo de migração:
  
- [Assistente de implantação do Exchange](https://aka.ms/exdeploy)
    
- Alterações de esquema Active Directory para Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)
    
- Requisitos do sistema para Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)
    
- Pré-requisitos para o Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)
    
## <a name="what-if-i-need-help"></a>E se eu precisar de ajuda?

Se você estiver migrando para o Office 365, você pode ser qualificado para usar o nosso serviço de Microsoft FastTrack. FastTrack fornece práticas recomendadas, ferramentas e recursos para tornar sua migração para o Office 365 é tão uniforme como possíveis. Melhor de tudo, você terá um engenheiro de suporte real que irá orientá-lo na sua migração, desde o planejamento e projetar até migrando sua caixa de correio do última. Se você deseja saber mais sobre FastTrack, dê uma olhada no [Microsoft FastTrack](https://fasttrack.microsoft.com/).
  
Se você executar em quaisquer problemas durante a migração para o Office 365 e você não estiver usando FastTrack ou a migração para uma versão mais recente do Exchange Server, estamos aqui para ajudar. Aqui estão alguns recursos que você pode usar:
  
- [Comunidade técnica](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [Suporte ao cliente](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>Tópicos relacionados

[Recursos para ajudá-lo a atualizar do Office 2010 de servidores e clientes](upgrade-from-office-2010-servers-and-products.md)
  
[Grupo de aposentadoria do Office (Microsoft Tech comunidade)](https://go.microsoft.com/fwlink/?linkid=842065)
  

