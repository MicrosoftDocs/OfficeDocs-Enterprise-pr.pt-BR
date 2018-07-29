---
title: Roteiro de fim do suporte do Exchange 2007
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
description: Em 11 de abril de 2017, Exchange Server 2007 atingido o fim do suporte. Se você ainda não já começou a migração do Exchange 2007 para o Office 365 ou Exchange 2016, agora é a hora de início do seu planejamento.
ms.openlocfilehash: 4bb8933977c280b4bfaa686e858fc818a1dc4ace
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169803"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Roteiro de fim do suporte do Exchange 2007

Em **11 de abril de 2017**, Exchange Server 2007 atingido o fim do suporte. Se você ainda não já começou a migração do Exchange 2007 para o Office 365 ou Exchange 2016, agora é a hora de início do seu planejamento. 
  
## <a name="what-does-end-of-support-mean"></a>Qual end faz da média de suporte?

Exchange Server, como quase todos os produtos da Microsoft, tem um ciclo de vida de suporte durante o qual fornecemos novos recursos, correções de erros, correções de segurança e assim por diante. Esse ciclo de vida geralmente dura por 10 anos a partir da data de lançamento inicial do produto e final desse ciclo de vida é conhecido como o fim do produto do suporte. Desde que o Exchange 2007 alcançado seu fim do suporte em 11 de abril de 2017, a Microsoft não oferece mais:
  
- Suporte técnico para problemas que podem ocorrer;
    
- Correções de erros para problemas que são descobertos e que pode afetar a estabilidade e a usabilidade do servidor;
    
- Correções de segurança para vulnerabilidades que são descobertas e pode fazer com que o servidor vulnerável a falhas de segurança;
    
- Atualizações de fuso horário.
    
Sua instalação do Exchange 2007 continuará a executar após essa data. No entanto, devido às alterações listadas acima, é altamente recomendável que você migre do Exchange 2007 assim que possível.
  
Para obter mais informações sobre os servidores do Office 2007 próximo do fim do suporte, consulte [Planejar a atualização do 2007 Office servers e produtos](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Quais são as opções de minha?

Agora que o Exchange 2007 alcançou o fim do suporte, é altamente recomendável que você explore as opções e preparar um plano de migração. É possível:
  
- Migrar para o Office 365 usando a transferência, em etapas ou migração híbrida;
    
- Migre seus servidores Exchange 2007 para uma versão mais recente do Exchange em seus servidores no local.
    
As seções a seguir exploram cada opção mais detalhadamente.
  
### <a name="migrate-to-office-365"></a>Migrar para o Office 365

Migrar seu email para o Office 365 é sua opção de melhor e mais simples para ajudá-lo a desativar a implantação do Exchange 2007. Com uma migração para o Office 365, você pode fazer um único salto da tecnologia de 10 anos aos recursos de última geração, como:
  
- Recursos de conformidade, como políticas de retenção In-loco e retenção de litígio, in-loco eDiscovery e muito mais;
    
- O Office 365 grupos;
    
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
  
| |
|**Opção de migração**|**Tamanho da organização**|**Duração**|
|:-----|:-----|:-----|
|Migração de substituição  <br/> |Menos de 150 estações  <br/> |Uma semana ou menos  <br/> |
|Migração em estágios  <br/> |Mais de 150 estações  <br/> |Algumas semanas  <br/> |
|Migração híbrida completo  <br/> |Centenas ou milhares de estações  <br/> |Alguns meses ou mais  <br/> |
   
As próximas seções fornecem uma visão geral dos métodos a seguir. Confira [Decida em um caminho de migração](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) para aprender os detalhes de cada método. 
  
#### <a name="cutover-migration"></a>Migração de substituição

Uma migração de substituição é uma onde, em pré-selecionada data e hora, você migrará todas as suas caixas de correio, grupos de distribuição, contatos e assim por diante, para o Office 365; Quando tiver terminado, você vai desligar seus servidores do Exchange no local e começar a usar o Office 365 exclusivamente.
  
O método de migração é ótimo para pequenas organizações que não possuem muitos muito caixas de correio, deseja ir para o Office 365 rapidamente e não deseja lidar com algumas da complexidade dos outros métodos. Mas ele também um pouco limitado porque ele deve ser concluído em uma semana ou menos e porque ele requer que os usuários reconfigurar os seus perfis do Outlook. Durante a migração pode lidar com até 2.000 caixas de correio, é altamente recomendável que você migra um máximo de 150 caixas de correio com este método. Se você tentar migrar mais de 150 caixas de correio, você poderia ficar esgotado o tempo necessário para transferir todas as caixas de correio antes seu prazo e sua equipe pode obter o suporte de TI sobrecarregado ajudando os usuários reconfigure o Outlook.
  
Se você estiver pensando sobre fazendo uma migração gradual, aqui estão algumas coisas a considerar considerar:
  
- O Office 365 precisará conectar-se a seus servidores Exchange 2007 usando o Outlook em qualquer lugar através da porta TCP 443;
    
- Todas as caixas de correio local serão movidas para o Office 365;
    
- Você precisará de uma conta de administrador local que tenha acesso ao ler o conteúdo de caixas de correio dos usuários;
    
- O Exchange 2007 aceitou os domínios que você deseja usar no Office 365 necessidade para ser adicionado como domínios verificados no serviço;
    
- Entre o momento em que você inicia a migração e quando você começar a fase de conclusão, Office 365 periodicamente será sincronizado com o Office 365 e caixas de correio local. Isso permite que você concluir a migração sem se preocupar eletrônico sejam deixado para trás em suas caixas de correio local;
    
- Os usuários receberão novas senhas temporárias para sua conta do Office 365 precisará alterar quando eles fazem logon suas caixas de correio pela primeira vez;
    
- Você precisará de uma licença do Office 365 que inclui o Exchange Online para cada caixa de correio de usuário que você migrar;
    
- Os usuários precisarão configurar um novo perfil do Outlook em cada um dos seus dispositivos e baixar seus emails novamente. A quantidade de email que o Outlook baixará pode variar. Para obter mais informações, dê uma olhada em [alterar quanto mail para manter offline](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Para saber mais sobre a migração de transferência, dê uma olhada:
  
- [O que você precisa saber sobre uma migração de substituição de email para o Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Executar uma migração de substituição de email para o Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Migração em estágios

Uma migração em estágios é um onde você tiver algumas centenas ou alguns mil caixas de correio que você deseja migrar para o Office 365, precisará tomar uma semana ou mais para concluir a migração, e não precisa de qualquer um dos recursos de migração híbrida avançado gostar informações de calendário disponível/ocupado compartilhada inform.
  
Migração em estágios é ótima para organizações que precisam levar mais tempo para migrar suas caixas de correio para o Office 365, mas ainda planejar concluir a migração em algumas semanas. Você pode migrar caixas de correio em lotes"" que permitem que você controle quantos e qual, caixas de correio são migradas em um determinado momento. Você pode lote de caixas de correio dos usuários do mesmo departamento, por exemplo, para garantir que eles estiver todos movidos ao mesmo tempo. Ou então, você pode deixar as caixas de correio executivas até o último lote. Conforme com migrações de transferência, serão necessário recriar seus perfis do Outlook seus usuários.
  
Se você estiver pensando sobre fazendo uma migração em estágios, aqui estão algumas coisas a considerar:
  
- O Office 365 precisará conectar-se a seus servidores Exchange 2007 usando o Outlook em qualquer lugar através da porta TCP 443;
    
- Você precisará de uma conta de administrador local que tenha acesso ao ler o conteúdo de caixas de correio dos usuários;
    
- O Exchange 2007 aceitou os domínios que você deseja usar no Office 365 necessidade para ser adicionado como domínios verificados no serviço;
    
- Você precisará criar um arquivo CSV com o nome completo e endereço de email do cada caixa de correio que você deseja migrar em um lote. Você precisará também incluem uma nova senha para cada caixa de correio que você está migrando e envie sua senha a cada usuário. O usuário será solicitado a alterar a senha na primeira vez que fazem logon sua caixa de correio do novo Office 365;
    
- Entre o momento em que você iniciar o lote de migração e quando você começar a fase de conclusão, o Office 365 periodicamente sincronizará as caixas de correio do Office 365 e no local incluídas no lote. Isso permite que você concluir a migração sem se preocupar eletrônico sejam deixado para trás em suas caixas de correio local;
    
- Os usuários receberão novas senhas temporárias para sua conta do Office 365 precisará alterar quando fazem logon em suas caixas de correio pela primeira vez;
    
- Você precisará de uma licença do Office 365 que inclui o Exchange Online para cada caixa de correio de usuário que você migrar;
    
- Os usuários precisarão configurar um novo perfil do Outlook em cada um dos seus dispositivos e baixar seus emails novamente. A quantidade de email que o Outlook baixará pode variar. Para obter mais informações, dê uma olhada em [alterar quanto mail para manter offline](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Para saber mais sobre a migração em estágios, dê uma olhada:
  
- [O que você precisa saber sobre uma migração em estágios de email para o Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Realizar uma migração em estágios do email para o Office 365](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
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
    
- Você precisará implantar pelo menos um servidor Exchange 2013 em sua organização do Exchange 2007 para agir como um "servidor de híbrido". Esse servidor se comunicar com o Office 365 em nome de seus servidores Exchange 2007;
    
- O Office 365 precisará conectar-se ao "servidor híbrido" usando o Outlook em qualquer lugar através da porta TCP 443;
    
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

Enquanto estamos altamente acredita que você pode obter a melhor experiência de usuário e o valor por meio da migração para o Office 365, também sabemos que algumas organizações precisam manter seu email no local. Isso poderia ser devido a requisitos normativos garantir que os dados não é armazenados em um data center localizado em outro país e assim por diante. Se você optar por manter o seu email local, você pode migrar seu ambiente do Exchange 2007 para Exchange 2010, Exchange 2013 ou 2016 do Exchange.
  
É recomendável que você migre para Exchange 2016 se você não pode migrar para o Office 365. Exchange 2016 inclui todos os recursos e os aperfeiçoamentos incluídos com versões anteriores do Exchange e mais parecido com a experiência disponível com o Office 365 (embora alguns recursos estão disponíveis somente no Office 365). Confira apenas algumas das coisas que você tiver sido ausentes abrindo diante:
  
|**Versão do Exchange**|**Recursos**|
|:-----|:-----|
|Exchange 2010  <br/> | Role Based Access Control (permissões sem ACLs)  <br/>  Diretivas de caixa de correio do Outlook Web Access  <br/>  Capacidade de compartilhar informações de disponibilidade e delegar calendários entre organizações  <br/> |
|Exchange 2013  <br/> | *Recursos do Exchange 2010 e …*  <br/>  Arquitetura simplificada, reduzindo o número de funções de servidor para três (caixa de correio, acesso para cliente, transporte de borda)  <br/>  Políticas de prevenção de perda dados (DLP) que ajudam a manter o vazamento de informações confidenciais  <br/>  Significativamente Outlook Web App experiência aprimorada  <br/> |
|Exchange 2016  <br/> | *Recursos do Exchange 2013 e …*  <br/>  Ainda mais as funções de servidor simplificado para acabou de caixa de correio e transporte de borda  <br/>  DLP aprimorada, juntamente com a integração com o SharePoint  <br/>  Resiliência de banco de dados aprimorado  <br/>  Colaboração de documentos online  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>Qual versão deve migrar para?

Recomendamos que você inicialmente pressupõe que você migrará para 2016 do Exchange. Em seguida, use as informações a seguir para confirmar sua pressuposição ou eliminar os 2016 do Exchange. Se você não pode migrar para o Exchange 2016 para um ou outro motivo, o mesmo processo com o Exchange 2013 e assim por diante.
  
|**Consideração**|**Mais informações**|
|:-----|:-----|
|Datas finais de suporte  <br/> | Como o Exchange 2007, cada versão do Exchange tem seu próprio final da data de suporte:  <br/> **O Exchange 2010** - janeiro de 2020  <br/> **Exchange 2013** - de 2023 abril  <br/> **Exchange 2016** - de 2025 de outubro  <br/>  Quanto mais cedo final da data de suporte, o antes você precisará realizar a migração de outra. Janeiro de 2020 é muito mais próximo do que você pensa!<br/> |
|Caminho de migração para o Exchange 2010 e 2013  <br/> |Aqui estão as fases gerais para migrar para o Exchange 2010 ou Exchange 2013:  <br/> Instalar o Exchange 2010 ou 2013 em seus serviços de movimentação de organização existentes do Exchange 2007 e outra infraestrutura para o Exchange 2010 ou 2013 mover as caixas de correio e pastas públicas para o Exchange 2010 ou o descomissionamento 2013 restantes servidores Exchange 2007 |
|Caminho de migração para Exchange 2016  <br/> |Aqui estão as fases gerais para migrar para o Exchange 2016:  <br/> Instalar o Exchange 2013 em seus serviços de movimentação de organização existentes do Exchange 2007 e outra infraestrutura para caixas de correio do Exchange 2013 Move e pastas públicas para o Descomissionamento do Exchange 2013 restantes servidores Exchange 2007 instalar 2016 do Exchange em sua existente Organização do Exchange 2013. Mova caixas de correio, pastas públicas, serviços e outra infraestrutura para 2016 do Exchange (ordem não importa). Encerrar os servidores restantes do Exchange 2013 > [!NOTE]> Migrando a partir do Exchange 2013 para Exchange 2016 é simple. As duas versões apresentam quase os mesmos requisitos de hardware. Isso e o fato destas que versões são portanto compatível, significa que você pode recriar um servidor que você comprou para o Exchange 2013 e instalar o Exchange 2016 nele. Além disso, com movimentações de caixa de correio online, a maioria dos usuários nunca perceberá suas caixas de correio sendo movida desativar o servidor e, em seguida, novamente depois que você o tiver recriados com Exchange 2016.           |
|Coexistência de versão  <br/> | Durante a migração para:  <br/> **Exchange 2016** Exchange 2016 não pode ser instalado em uma organização que inclui um servidor Exchange 2007. Você precisará primeiro migrar para o Exchange 2010 ou 2013 (é altamente recomendável o Exchange 2013), remover todos os servidores Exchange 2007 e migre para 2016 do Exchange.<br/> **Exchange 2010 ou Exchange 2013** Você pode instalar o Exchange 2010 ou Exchange 2013 em uma organização existente do Exchange 2007. Isso permite que você instale um ou mais o Exchange 2010 ou 2013 servidores e realizar a migração.<br/> |
|Hardware de servidor  <br/> | Requisitos de hardware de servidor foram alterados do Exchange 2007. Você precisará certificar-se de que o hardware que você vai usar é compatível. Você pode encontrar mais informações sobre requisitos de hardware para cada versão aqui:<br/> [Requisitos do sistema do Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Requisitos do sistema do Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [Requisitos do sistema do Exchange 2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  Você encontrará com as melhorias significativas no desempenho do Exchange e a maior capacidade de computação e a capacidade de armazenamento em servidores mais recentes, você provavelmente precisará de menos servidores para suportar o mesmo número de caixas de correio.  <br/> |
|Versão do sistema operacional  <br/> | As versões de mínimos do sistema operacional com suporte para cada versão são:  <br/> **Exchange 2016** Windows Server 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/> **O Exchange 2010** Windows Server 2008 SP2  <br/>  Você pode encontrar mais informações sobre o suporte ao sistema operacional na [Matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Nível funcional do Active Directory floresta  <br/> | Os mínimo com suporte do Active Directory níveis funcionais de floresta de cada versão são:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **O Exchange 2010** Windows Server 2003  <br/>  Você pode encontrar mais informações sobre o suporte de nível funcional de floresta na [Matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Versões de cliente do Office  <br/> | As versões mínimas do cliente Office com suporte para cada versão são:  <br/> **Exchange 2016** Office 2010 (com as atualizações mais recentes)  <br/> **Exchange 2013** Office 2007 SP3  <br/> **O Exchange 2010** Office 2003  <br/>  Você pode encontrar mais informações sobre o suporte de cliente do Office na [Matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Como migrar?

Se você tiver decidido que você deseja manter seu email local, você pode usar os seguintes recursos para ajudá-lo no processo de migração:
  
- [Assistente de implantação do Exchange](https://aka.ms/exdeploy)
    
- Alterações de esquema Active Directory para o Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Requisitos do sistema para Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)
    
- Pré-requisitos para o Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)
    
## <a name="what-if-i-need-help"></a>E se eu precisar de ajuda?

Se você estiver migrando para o Office 365, você pode ser qualificado para usar o nosso serviço de Microsoft FastTrack. FastTrack fornece práticas recomendadas, ferramentas e recursos para tornar sua migração para o Office 365 é tão uniforme como possíveis. Melhor de tudo, você terá um engenheiro de suporte real que irá orientá-lo na sua migração, desde o planejamento e projetar até migrando sua caixa de correio do última. Se você deseja saber mais sobre FastTrack, dê uma olhada no [Microsoft FastTrack](https://fasttrack.microsoft.com/).
  
Se você executar em quaisquer problemas durante a migração para o Office 365 e você não estiver usando FastTrack ou a migração para uma versão mais recente do Exchange Server, estamos aqui para ajudar. Aqui estão alguns recursos que você pode usar:
  
- [Comunidade técnica](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [Suporte ao cliente](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>Tópicos relacionados

[Recursos para ajudá-lo a atualizar seus servidores do Office 2007 e clientes](upgrade-from-office-2007-servers-and-products.md)
  
[Grupo de aposentadoria do Office (Microsoft Tech comunidade)](https://go.microsoft.com/fwlink/?linkid=842065)
  

