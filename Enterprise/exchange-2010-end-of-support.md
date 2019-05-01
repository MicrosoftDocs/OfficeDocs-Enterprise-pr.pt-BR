---
title: Roteiro de fim do suporte do Exchange 2010
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
description: O Exchange 2010 está se aproximando do fim do suporte. Use este mapa de planejamento como um guia para preparar a atualização para o Exchange Online ou uma versão mais recente do Exchange Server no local.
ms.openlocfilehash: d9dcc2120f549c55fedc78483689dbded0a4464f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487217"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Roteiro de fim do suporte do Exchange 2010

Em **14 de janeiro de 2020**, o Exchange Server 2010 alcançará o fim do suporte. Se você ainda não começou sua migração do Exchange 2010 para o Office 365 ou o Exchange 2016, agora é hora de iniciar o planejamento.

## <a name="what-does-end-of-support-mean"></a>O que significa o fim do suporte?

O Exchange Server, como quase todos os produtos da Microsoft, tem um ciclo de vida de suporte durante o qual fornecemos novos recursos, correções de erros, correções de segurança e assim por diante. Esse ciclo de vida normalmente dura 10 anos a partir da data da versão inicial do produto, e o final desse ciclo de vida é conhecido como o fim do suporte do produto.
Quando o Exchange 2010 atingir o fim do suporte em 14 de janeiro de 2020, a Microsoft não fornecerá mais:

- Suporte técnico para problemas que podem ocorrer;
- Correções de erros descobertas e que podem afetar a estabilidade e a usabilidade do servidor;
- Correções de segurança para vulnerabilidades descobertas e que podem tornar o servidor vulnerável a falhas de segurança;
- Atualizações de fuso horário.

A instalação do Exchange 2010 continuará a ser executada após essa data. No enTanto, devido às alterações listadas acima, é altamente recomendável migrar do Exchange 2010 o mais rápido possível.

Para obter mais informações sobre os servidores do Office 2010 próximos ao fim do suporte, confira [recursos para ajudá-lo a atualizar de clientes e servidores do office 2010](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## <a name="what-are-my-options"></a>Quais são as minhas opções?

Com o Exchange 2010 alcançando o fim do suporte, esse é um excelente momento para explorar suas opções e preparar um plano de migração. Você pode:

- Migre totalmente para o Office 365. Migrar caixas de correio usando substituição, uma migração híbrida mínima ou completa e, em seguida, remover os servidores do Exchange locais e o Active Directory.
- Migre seus servidores Exchange 2010 para o Exchange 2016 em seus servidores locais.

> [!IMPORTANT]
> Se sua organização optar por migrar caixas de correio para o Office 365, mas pretende manter o dirSync ou o Azure AD Connect in-loco para continuar Gerenciando contas de usuário do Active Directory local, você precisará manter pelo menos um servidor Exchange local. Se o último servidor do Exchange for removido, você não poderá fazer alterações nos destinatários do Exchange no Exchange Online. Isso ocorre porque a fonte de autoridade permanece no Active Directory local e as alterações precisam ser feitas ali. Neste cenário, você tem as seguintes opções:

- (**Recomendado**) Se você puder migrar suas caixas de correio para o Office 365 e atualizar seus servidores em 14 de janeiro de 2020, use o Exchange 2010 para se conectar ao Office 365 e migrar caixas de correio. Em seguida, migre o Exchange 2010 para o Exchange 2016 e encerre os servidores do Exchange 2010 restantes.
- Se você não conseguir concluir a migração de caixa de correio e a atualização do servidor local em 14 de janeiro de 2020, atualize seus servidores locais do Exchange 2010 para o Exchange 2016 primeiro e, em seguida, use o Exchange 2016 para se conectar ao Office 365 e migrar caixas de correio.

> [!NOTE]
> Embora um pouco mais complicado, você também pode migrar caixas de correio para o Office 365 enquanto migra seus servidores locais do Exchange 2010 para o Exchange 2016.

As seções a seguir exploram cada opção em mais detalhes.

## <a name="migrate-to-office-365"></a>Migrar para o Office 365

Migrar seu email para o Office 365 é a opção mais simples e fácil de ajudá-lo a retirar sua implantação do Exchange 2010. Com uma migração para o Office 365, você pode fazer um único salto da tecnologia antiga para os recursos de ponta, como:

- Recursos de conformidade, como políticas de retenção, bloqueio in-loco e de litígio, descoberta eletrônica in-loco e mais;
- Microsoft Teams;
- Power BI;
- Caixa de entrada destaques;
- Análise do Delve;

O Office 365 também obtém novos recursos e experiências primeiro, e você e seus usuários normalmente podem começar a usá-los imediatamente. Além de novos recursos, você não precisa se preocupar com:

- Compra e manutenção de hardware;
- Pagar a calefação e refrigeração de seus servidores;
- Manter-se atualizado sobre correções de segurança, produtos e fuso horário;
- Manutenção de armazenamento e software para atender aos requisitos de conformidade;
- Atualizando para uma nova versão do Exchange-você está sempre na versão mais recente do Exchange no Office 365.

### <a name="how-should-i-migrate-to-office-365"></a>Como devo migrar para o Office 365?

Dependendo da sua organização, você tem algumas opções que o ajudarão a acessar o Office 365. Ao escolher uma opção de migração, você precisa considerar algumas coisas como o número de assentos ou caixas de correio que precisa mover, quanto tempo deseja que a migração seja a última e se precisa de uma integração perfeita entre a sua instalação local e o Office 365 durante a migração. Esta tabela mostra as opções de migração e os fatores mais importantes que determinarão o método que você usará.

| **Opção de migração**     | **Tamanho da organização** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| Migração de substituição        | Menos de 150 estações  | Uma semana ou menos      |
| Migração híbrida mínima | Menos de 150 estações  | Algumas semanas ou menos |
| Migração híbrida completa    | Mais de 150 assentos   | Algumas semanas ou mais |

As seções a seguir fornecem uma visão geral desses métodos. ConFira [decida em um caminho de migração](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) para aprender os detalhes de cada método.

### <a name="cutover-migration"></a>Migração de substituição

Uma migração de substituição é aquela em que, em uma data e hora previamente selecionadas, você migrará todas as suas caixas de correio, grupos de distribuição, contatos e assim por diante, para o Office 365; Quando tiver terminado, você desligará seus servidores locais do Exchange e começará a usar o Office 365 exclusivamente.

O método de migração de substituição é ótimo para pequenas organizações que não têm muitas caixas de correio, que desejam acessar o Office 365 rapidamente e não querem lidar com algumas das complexidades dos outros métodos. Mas também é um tanto limitado porque deve ser concluída em uma semana ou menos, pois requer que os usuários reconfigurem seus perfis do Outlook. Embora a migração de substituição possa lidar com até 2.000 caixas de correio, é altamente recomendável migrar um máximo de 150 caixas de correio com esse método. Se você tentar migrar mais de 150 caixas de correio, você pode ficar sem tempo para transferir todas as caixas de correio antes do seu prazo, e sua equipe de suporte de ti pode se tornar sobrecarregado para ajudar os usuários a reconfigurar o Outlook.

Se você estiver pensando em fazer uma migração de substituição, aqui estão alguns pontos a considerar:

- O Office 365 precisará se conectar aos seus servidores do Exchange 2010 usando o Outlook Anywhere pela porta TCP 443;
- Todas as caixas de correio locais serão movidas para o Office 365;
- Você precisará de uma conta de administrador local que tenha acesso para ler o conteúdo das caixas de correio dos usuários;
- Os domínios aceitos do Exchange 2010 que você deseja usar no Office 365 precisam ser adicionados como domínios verificados no serviço;
- Entre o momento em que você iniciar a migração e quando começar a fase de conclusão, o Office 365 sincronizará periodicamente as caixas de correio locais e do Office 365. Isso permite que você conclua a migração sem se preocupar com emails que estão sendo deixados em suas caixas de correio locais;
- Os usuários receberão novas senhas temporárias para sua conta do Office 365 que eles precisarão alterar quando fizerem logon em suas caixas de correio pela primeira vez;
- Você precisará de uma licença do Office 365 que inclua o Exchange Online para cada caixa de correio de usuário que você migrar;
- Os usuários precisarão configurar um novo perfil do Outlook em cada um dos seus dispositivos e baixar seus emails novamente. A quantidade de email que o Outlook fará download pode variar. Para obter mais informações, confira [alterar a quantidade de emails que serão mantidas offline](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

Para saber mais sobre a migração de substituição, confira:

- [O que você precisa saber sobre uma migração de substituição de email para o Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Executar uma migração de substituição de email para o Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>Migração híbrida mínima

Uma migração mínima híbrida ou expressa é aquela em que você tem algumas centenas de caixas de correio que você deseja migrar para o Office 365, pode concluir a migração dentro de algumas semanas e não precisa de nenhum dos recursos de migração híbrida avançados, como o calendário de disponibilidade compartilhado Information.

A migração híbrida mínima é excelente para as organizações que precisam levar mais tempo para migrar suas caixas de correio para o Office 365, mas ainda planeja concluir a migração dentro de algumas semanas. Você obtém alguns benefícios da migração híbrida completa mais avançada sem muitas das complexidades. Você pode controlar quantas e quais caixas de correio são migradas em um determinado momento; As caixas de correio do Office 365 serão criadas com o nome de usuário e as senhas de suas contas locais; e, diferentemente das migrações de substituição, seus usuários não precisarão recriar os perfis do Outlook.

Se você estiver pensando em realizar uma migração híbrida mínima, aqui estão alguns pontos a considerar:

- Você precisará executar uma sincronização de diretório única entre seus servidores do Active Directory local e o Office 365;
- Os usuários poderão fazer logon na caixa de correio do Office 365 usando o mesmo nome de usuário e senha que estavam usando quando a caixa de correio foi migrada;
- Você precisará de uma licença do Office 365 que inclua o Exchange Online para cada caixa de correio de usuário que você migrar;
- Os usuários não precisam configurar um novo perfil do Outlook na maioria de seus dispositivos (alguns telefones Android antigos podem precisar de um novo perfil) e não precisam baixar novamente seus emails.

Para saber mais sobre a migração híbrida mínima, dê uma olhada em [usar o mínimo híbrido para migrar rapidamente as caixas de correio do Exchange para o Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>Híbrido completo

Uma migração híbrida completa é aquela em que sua organização tem muitas centenas, até dezenas de milhares, de caixas de correio e você deseja mover algumas ou todas elas para o Office 365. Como essas migrações são geralmente de longo prazo, as migrações híbridas tornam possível:

- Mostrar usuários locais as informações de calendário de disponibilidade para usuários no Office 365 e vice-versa;
- Veja uma lista de endereços global unificada que contém destinatários no local e no Office 365;
- Exibir cartões de destinatários completos do Outlook para todos os usuários, independentemente se eles estão no local ou no Office 365;
- Comunicação segura de email entre servidores locais do Exchange e o Office 365 usando TLS e certificados;
- Tratar mensagens enviadas entre os servidores locais do Exchange e o Office 365 como internas, permitindo que eles:
- Ser avaliado e processado corretamente por agentes de conformidade e de conformidade direcionados a mensagens internas;
- Ignorar filtros antispam.

As migrações híbridas completas são melhores para as organizações que esperam permanecer em uma configuração híbrida por muitos meses ou mais. Você receberá os recursos listados anteriormente nesta seção, além de sincronização de diretório, melhores recursos de conformidade integrado e a capacidade de mover caixas de correio para e do Office 365 usando movimentações de caixa de correio online. O Office 365 se torna uma extensão de sua organização local.

Se você estiver pensando em realizar uma migração híbrida completa, aqui estão alguns pontos a considerar:

- As migrações híbridas completas não são adequadas a todos os tipos de organizações. Devido à complexidade de migrações híbridas completas, as organizações com menos de algumas cem caixas de correio não costumam ver benefícios que justificam o esforço e o custo necessário para definir um. Se isso soa como sua organização, recomendamos enfaticamente que você considere a substituição ou as migrações híbridas mínimas;
- Você precisará configurar a sincronização de diretório usando o Azure Active Directory Connect (AADConnect) entre seus servidores do Active Directory local e o Office 365;
- Os usuários poderão fazer logon em sua caixa de correio do Office 365 usando o mesmo nome de usuário e senha que eles usam ao fazer logon na rede local (requer o Azure Active Directory Connect com sincronização de senha e/ou serviços de Federação do Active Directory);
- Você precisará de uma licença do Office 365 que inclua o Exchange Online para cada caixa de correio de usuário que você migrar;
- Os usuários não precisam configurar um novo perfil do Outlook na maioria de seus dispositivos (alguns telefones Android antigos podem precisar de um novo perfil) e não precisam baixar novamente seus emails.

> [!IMPORTANT]
> Se sua organização optar por migrar caixas de correio para o Office 365, mas pretende manter o dirSync ou o Azure AD Connect in-loco para continuar Gerenciando contas de usuário do Active Directory local, você precisará manter pelo menos um servidor Exchange local. Se o último servidor do Exchange for removido, você não poderá fazer alterações nos destinatários do Exchange no Exchange Online. Isso ocorre porque a fonte de autoridade permanece no Active Directory local e as alterações precisam ser feitas ali.

Se uma migração híbrida completa for adequada para você, dê uma olhada nos seguintes recursos para ajudá-lo com a migração:

- [Assistente de implantação do Exchange](https://aka.ms/exdeploy)
- [Implantações híbridas do Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [Assistente de Configuração Híbrida](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [Perguntas frequentes do Assistente de Configuração Híbrida](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [Pré-requisitos de implantação híbrida](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Atualizar para uma versão mais recente do Exchange Server local

Embora acreditemos que você possa obter o melhor valor e a experiência do usuário migrando totalmente para o Office 365, também entendemos que algumas organizações precisam manter alguns servidores do Exchange locais. Isso pode ter ocorrido por causa dos requisitos normativos, para garantir que os dados não sejam armazenados em um Datacenter localizado em outro país ou que você tenha configurações ou requisitos exclusivos que não podem ser atendidos na nuvem ou pode simplesmente ser que você precise do Exchange para gerenciar caixas de correio em nuvem porque você ainda usa o Active Directory local. Em qualquer caso em que você escolher ou precisar manter o Exchange local, você deve garantir que seu ambiente do Exchange 2010 seja atualizado para pelo menos o Exchange 2013 ou Exchange 2016 e o Exchange 2010 seja removido antes da data de término do suporte.

Para obter a melhor experiência, recomendamos que você atualize seu ambiente local restante para o Exchange 2016. Você não precisa instalar o Exchange Server 2013 se quiser ir diretamente do Exchange Server 2010 para o Exchange Server 2016.

O Exchange 2016 inclui todos os recursos e avanços incluídos nas versões anteriores do Exchange e mais uma delas correspondem à experiência disponível com o Office 365 (embora alguns recursos estão disponíveis apenas no Office 365). ConFira apenas algumas das coisas que você esteve perdendo:

| **Versão do Exchange**                     | **Recursos**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | Arquitetura simplificada reduzindo o número de funções de servidor para três (caixa de correio, acesso para cliente, transporte de borda)                                                                                                                                        |
|                                          | Políticas de prevenção contra perda de dados (DLP) que ajudam a manter informações confidenciais contra vazamento                                                                                                                                                                |
|                                          | Experiência do Outlook Web App significativamente aprimorada                                                                                                                                                                                                    |
| Exchange 2016                            | *Recursos do Exchange 2013 e...*                                                                                                                                                                                                                   |
|                                          | Funções de servidor simplificadas para apenas o transporte de borda e caixa de correio                                                                                                                                                                                   |
|                                          | DLP aprimorado junto com a integração com o SharePoint                                                                                                                                                                                                  |
|                                          | Resiliência de banco de dados aprimorada                                                                                                                                                                                                                         |
|                                          | Colaboração de documentos online                                                                                                                                                                                                                        |

| **Relação**                        | **Mais informações**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Datas de fim de suporte                     | Como o Exchange 2010, cada versão do Exchange tem seu próprio fim de data de suporte:                                                                                                                                                                        |
|                                          | **Exchange 2013** -abril de 2023                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** -outubro de 2025                                                                                                                                                                                                                     |
|                                          | Antes do fim da data de suporte, mais cedo você precisará executar outra migração. Abril de 2023 é muito mais próximo do que você imagina!                                                                                                                 |
| Caminho de migração para o Exchange 2013 ou 2016  | O caminho de migração do Exchange 2010 para uma versão mais recente é o mesmo se você escolher o Exchange 2013 ou o Exchange 2016:                                                                                                                              |
|                                          | Instalar o Exchange 2013 ou 2016 em seus serviços de movimentação de organização do Exchange 2010 existente e outra infraestrutura para o Exchange 2013 ou 2016 mover caixas de correio e pastas públicas para o Exchange 2013 ou 2016 encerrar servidores Exchange 2010 restantes  |
| Coexistência de versões                      | Ao migrar para o Exchange 2013 ou o Exchange 2016, você pode instalar a versão em uma organização existente do Exchange 2010. Isso permite que você instale um ou mais servidores do Exchange 2013 ou do Exchange 2016 e realize sua migração.             |
| Hardware de servidor                          | Os requisitos de hardware do servidor foram alterados do Exchange 2010. Você precisará certificar-se de que o hardware que você vai usar é compatível. Você pode saber mais sobre os requisitos de hardware para cada versão aqui:                                      |
|                                          | [Requisitos de sistema do Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Requisitos de sistema do Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Você descobrirá que com os aprimoramentos significativos no desempenho do Exchange e com a capacidade de armazenamento e o aumento de energia em servidores mais recentes, provavelmente precisará de menos servidores para suportar o mesmo número de caixas de correio.                       |
| Versão do sistema operacional                 | As versões mínimas de sistema operacional com suporte para cada versão são:                                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | Você pode encontrar mais informações sobre o suporte do sistema operacional na [matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Nível funcional da floresta do Active Directory | Os níveis mínimos funcionais de floresta do Active Directory com suporte para cada versão são:                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** Windows Server 2003                                                                                                                                                                                                                |
|                                          | Você pode encontrar mais informações sobre o suporte de nível funcional da floresta na [matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Versões de cliente do Office                   | As versões mínimas compatíveis do cliente do Office para cada versão são:                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (com as atualizações mais recentes)                                                                                                                                                                                              |
|                                          | **Exchange 2013** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | Você pode encontrar mais informações sobre o suporte do cliente do Office na [matriz de suporte do Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

Você pode usar os seguintes recursos para ajudá-lo com a migração:

- [Assistente de implantação do Exchange](https://aka.ms/exdeploy)
- Alterações de esquema do Active Directory para o Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)
- Requisitos do sistema para o Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)
- Pré-requisitos para o Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)

## <a name="what-if-i-need-help"></a>E se eu precisar de ajuda?

Se você estiver migrando para o Office 365, poderá estar qualificado para usar nosso serviço Microsoft FastTrack. O FastTrack oferece práticas recomendadas, ferramentas e recursos para tornar sua migração para o Office 365 o mais simples possível. O melhor de tudo é que você terá um engenheiro de suporte real que orientará você durante a migração, do planejamento e do design de toda a forma de migração da última caixa de correio. Se você quiser saber mais sobre o FastTrack, dê uma olhada no [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Se você tiver problemas durante a migração para o Office 365 e não estiver usando o FastTrack ou sua migração para uma versão mais recente do Exchange Server, estamos aqui para ajudar. Veja alguns recursos que você pode usar:

- [Comunidade técnica](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [Suporte ao cliente](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>Tópicos relacionados

[Recursos para ajudá-lo a atualizar de clientes e servidores do Office 2010](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Grupo de aposentadoria do Office (comunidade de tecnologia da Microsoft)](https://go.microsoft.com/fwlink/?linkid=842065)
