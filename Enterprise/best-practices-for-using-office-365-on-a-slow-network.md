---
title: Práticas recomendadas para usar o Office 365 em uma rede lenta
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: End User
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
description: Não seria legal se sua conexão de Internet sempre foi fast e nunca para baixo? Talvez daquele dia virão. Mas enquanto isso, há práticas coisas que você pode fazer para contornar a uma rede balky e ainda obter seu trabalho diário.
ms.openlocfilehash: 2287de562672f5ceb1ab32949168e8dfdeb31585
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933138"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Práticas recomendadas para usar o Office 365 em uma rede lenta

Não seria legal se sua conexão de Internet sempre foi fast e nunca para baixo? Talvez daquele dia virão. Mas enquanto isso, há práticas coisas que você pode fazer para contornar a uma rede balky e ainda obter seu trabalho diário. Embora o Office 365 é um serviço baseado em nuvem, ele também fornece várias maneiras para trabalhar com o conteúdo offline e suavemente manter as alterações sincronizadas. Além disso, às vezes é mais eficiente para trabalhar com conteúdo offline só porque os aplicativos executados com mais rapidez e a interface do usuário é mais responsiva. Esse é o ponto: Office 365 oferece o melhor dos dois mundos. Aqui está como tirar vantagem dos que. 
  
> [!TIP]
> Deseja ver como lento (ou fast) é sua conexão de rede? Experimente o [teste de velocidade de OOKLA](https://www.speedtest.net/) ou o [Aplicativo de teste de velocidade de rede](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70). 
     
## <a name="why-is-my-network-so-slow"></a>Por que é minha rede tão lenta?

Embora você não tiver controle sobre o desempenho da rede em si, ele o ajuda a entender o que está acontecendo nos bastidores. Internet é enormemente complexa, mas há alguns conceitos que podem ajudá-lo a entender a situação muito melhor. Seguir as práticas recomendadas neste artigo pode ajudar a problemas de desempenho da solução alternativa e reduzir aborrecimento.
  
**Principais fatores que afetam o desempenho da rede**

![Fatores de desempenho de rede](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **Largura de banda e latência** As duas medidas mais importantes do desempenho da rede são latência e largura de banda: 
  
- Largura de banda é a taxa de medida em bits por segundo de taxa de transferência. Maior é melhor. Largura de banda é semelhante a um pipe água. Quanto maior o pipe, a água mais que você pode "sinta por meio de"-lo.
    
- Latência é o tempo que leva para conteúdo para fazer a partir de um servidor ou serviço para seu dispositivo e é medido em milissegundos. É mais rápido melhor. Latência pode ser causada por um número de fatores, incluindo o tempo de transmissão, uma conexão esparso ou baixa largura de banda.
    
 **Problemas comuns** Além de largura de banda e latência, outros problemas têm um impacto no desempenho da rede e, geralmente, são imprevisíveis. Desempenho da rede pode flutuar com base na hora do dia ou seu local físico. A rede pode ficar sobrecarregada quando determinados eventos ocorrem que o uso da Internet, como um desastre natural ou um evento público principal chegar a pico. O tamanho e complexidade da página que está sendo carregada e o número e tamanho dos arquivos que estão sendo transferidos tem decisivo direto no desempenho. Uma conexão WiFi pode prejudicar o temporariamente: por exemplo, sondagem de uma reunião de conferência grande de milhares solicitando todos tweet ao mesmo tempo. 
  
 **Considerações para uma rede de satélite** Uma rede de satélite é útil quando uma rede terrestre não é viável, como o inverso país, um ship cruzeiro ou uma área científica remota. Essas redes dependem satélites posicionadas em uma órbita geosynchronous milhas 22.000 acima o equador. Entretanto, uma transmissão percorre realmente aproximadamente 90.000 milhas e, portanto, uma rede de satélite tem uma latência mais lenta (500 ms ou mais) que uma rede terrestre (20 a 50 ms). Sob a melhor das condições, talvez você não perceba essa latência, mas para baixar arquivos grandes, vídeos de streaming e jogar, você provavelmente Sim. Outro problema é "chuva esmaecer" na qual clima pesada, como Trovoadas e blizzards, temporariamente pode interromper a transmissão de satélite.
  
## <a name="are-you-sure-its-the-network"></a>Tem certeza de que seja a rede?

Sempre que você tiver problemas de desempenho, primeiro certifique-se de que seu dispositivo não é a causa do problema. Há duas coisas que você pode fazer que pode tornar um grande avanço:
  
- Verifique se o dispositivo estiver executando bem e não há nenhum malware no seu computador.
    
- Se possível, compre mais memória. Adicionar memória é o mais simples e mais frequentemente maneira eficaz para melhorar o desempenho no seu dispositivo. É especialmente útil quando estiver trabalhando com arquivos grandes e vídeos.
    
Para obter mais informações, consulte o [desempenho do Windows e a manutenção](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help) e [Windows corrigir problemas de desempenho do sistema](https://support.microsoft.com/mats/slow_windows_performance/).
   
## <a name="best-practices-for-using-your-browser"></a>Práticas recomendadas para usar seu navegador

Seu navegador é seu gateway para Office 365, portanto, ela pode ter um impacto no desempenho, especialmente com o tempo que leva para carregar uma página e com que frequência você arredondar trip ao Office 365 service. 
  
 **Navegadores em geral**
  
Em geral, aqui estão algumas sugestões para navegadores:
  
- Desabilite complementos do navegador que podem afetar o desempenho ou que você não precisa realmente.
    
- Aumente o tamanho do cache de arquivos temporários de internet.
    
-  Depois que você entrar em sua conta do trabalho ou da escola, mantenha a janela do navegador aberto durante todo o dia. Você pode abrir outras guias e windows sem entrar novamente. Se você precisar entrar com outra conta, use a navegação privada. 
    
- Depois que cada página é baixado e aberto, mantê-los o open usando guias. É fácil navegar entre as guias e use a página posteriormente no dia. Atualize uma página somente se você precisar os dados mais recentes na página.
    
- Se uma página está demorando muito para abrir, pare o download de página (pressione ESC) e, em seguida, atualize a página (pressione F5). 
    
-  Quando possível, reduza viagens de ida e para o Office 365. Por exemplo, em vez de paginação por meio de listas ou bibliotecas, use a pesquisa para localizar arquivos em uma biblioteca grande e a filtragem em uma lista para ir diretamente para os resultados desejados. Ou então, crie modos de exibição que minimizar o tempo de carregamento de página. Para obter mais informações, consulte [gerenciar grandes listas e bibliotecas no Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).
    
- Se o desempenho do vídeo é ruim, você poderá baixar o vídeo e assista a ele no seu dispositivo. Um link de download pode estar disponível, ou você pode conseguir clique com botão direito no link de vídeo e selecione **Salvar destino como**. 
    
 **Específica do navegador**
  
Aqui estão algumas sugestões para seu navegador específico:
  
- **Internet Explorer** Atualizar para o Internet Explorer versão 11 ou posterior para melhorias de desempenho substancial em relação às versões anteriores. Para obter mais informações, consulte [problemas de corrigir o Internet Explorer ](https://support.microsoft.com/mats/ie_performance_and_safety).
    
- **FireFox** Para obter mais informações, consulte [Firefox está lento ou para de funcionar](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging).
    
- **Safari** Para obter mais informações, consulte [Apple - Safari](https://www.apple.com/safari/).
    
- **Chrome** Para obter mais informações, consulte a [Ajuda do Chrome](https://support.google.com/chrome/?hl=en).
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Práticas recomendadas para usar o Outlook e Outlook Web App

Leitura, gravação e organização de email é uma grande parte do dia de todos os participantes. Outlook e Outlook Web App (OWA) oferecem suporte offline. Usando um aplicativo de email no seu telefone inteligente é outra alternativa útil. Use as seguintes opções que melhor atendem às suas necessidades:
  
- Atualizar para o Outlook 2013 SP1 ou posterior para melhorias de desempenho substancial em relação às versões anteriores. 
    
-  Outlook Web App permite criar mensagens offline, contatos e eventos de calendário que são carregados quando o OWA é a próxima capazes de se conectar ao Office 365. Para obter mais informações sobre como configurar e usar o OWA no modo offline, consulte [Usando o Outlook Web App offline](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).
    
- Outlook permite trabalhar no modo de cache, no qual se conecte automaticamente sempre que possível. Você pode fazer com que o Outlook Baixe sua caixa de correio toda ou parte dele. Para obter mais informações, consulte [Ativar o modo cache do Exchange](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) e [trabalhar offline no Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633). 
    
- O Outlook também oferece um modo offline. Para usá-la, você deve primeiro configurar o modo em cache para que as informações da sua conta são copiadas para seu computador. No modo offline, o Outlook tentará se conectar usando a enviar e receber configurações, ou quando você defini-lo manualmente para trabalhar online. Para obter mais informações, consulte [trabalhar offline para evitar tarifas de conexão de dados](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [altere a enviar e receber configurações quando você trabalha offline](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)e [Alternar de um trabalhando offline para online](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9). 
    
- Se você tiver um telefone inteligente, pode ser usada para a triagem de seu email e calendário pela rede da operadora de seu telefone. 
    
> [!NOTE]
> Eis algumas orientações sobre quando usar o Outlook ou no OWA. Se o espaço em disco não for um problema no seu dispositivo, o Outlook tem um conjunto completo de recursos e pode funcionar melhor para você. Se o espaço em disco é um problema no seu dispositivo, considere usar o OWA que tem um subconjunto dos recursos, mas também funciona melhor em uma situação online. Obviamente, você pode usar um porque eles funcionam bem juntos. 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>Práticas recomendadas para usar o OneDrive for Business

OneDrive for Business foi projetado desde o início para trabalhar com seus arquivos online e offline. Depois de configurá-lo, a sincronização das alterações ocorre automaticamente e confiável sempre e você torná-los. Se a rede está lenta, você poderá trabalhar com a versão offline dos arquivos.
  
O OneDrive for Business sync app está disponível com o Office 2013 (Professional Plus ou edições Standard) ou uma assinatura do Office 365 que inclui os aplicativos do Office 2013. Se você não possui o Office 2013, você pode [Baixar](https://support.microsoft.com/kb/2903984) o OneDrive for Business sync app gratuitamente. Esse aplicativo também é mais rápido do que usando os comandos **Abrir no Explorer** ou **carregar** . Para obter mais informações, consulte [Configurar o computador para sincronizar seu OneDrive para arquivos de negócios no Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).
  
Eis algumas orientações adicionais para usar o o OneDrive for Business sync app:
  
- Se você está sincronizando uma grande biblioteca pela primeira vez, inicie a sincronização durante fora do horário comercial, por exemplo, durante a noite. 
    
- Você pode usar o recurso de [interromper a sincronização de uma biblioteca com o OneDrive for Business app](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) para interromper temporariamente a sincronização de atualizações. No entanto, usar esse recurso para breves períodos, como algumas horas, ao mesmo tempo, para evitar o enfileiramento de mensagens grandes números de atualizações e minimizar o risco de conflitos de mesclagem se várias pessoas funcionam no mesmo documento. 
  
## <a name="best-practices-for-using-onenote"></a>Práticas recomendadas para uso do OneNote

Todos os sites de equipe do SharePoint tem um bloco de anotações do OneNote interno, e você poderá criar facilmente seus próprios. O OneNote é uma ótima maneira de coletar informações em tempo hábil que você precisa obter tarefas feitas todos os dias. Por exemplo, muitas equipes de usam o OneNote como um ponto de coleta para reuniões semanais, notas do projeto, ideias, planos e relatórios de status. Claramente, você pode organizar essas informações diferentes usando as páginas de seções e tabulações.
  
Mas a vantagem do OneNote é que você pode acessar o conteúdo de praticamente qualquer dispositivo, se uma área de trabalho, um laptop, um tablet ou um telefone inteligente. E você não precisa se preocupar sobre como salvar ou sincronizando porque o OneNote faz isso para você. 
  
Para obter mais informações, consulte [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/).
  
## <a name="best-practices-for-using-lync-online"></a>Práticas recomendadas para usar o Lync Online

A seguir estão as diretrizes gerais para usando o Lync Online quando sua rede está lenta:
  
- Use mensagens instantâneas, sempre que você pode porque ele funciona bem em uma rede lenta.
    
- Evite fazer chamadas telefônicas através de uma rede virtual privada (VPN) ou conexões de serviço (RAS) de acesso remoto.
    
- Certificar-se de que seu dispositivo de áudio em particular for aprovado. Para obter mais informações, consulte [telefones e dispositivos qualificados do Microsoft Lync](https://technet.microsoft.com/en-us/office/dn788944).
    
-  Ao usar o PowerPoint em uma apresentação online, reduza o tamanho e a complexidade dos slides. Para obter mais informações, consulte [dicas para melhorar o desempenho da sua apresentação](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).
    
- Sempre que possível, compartilhe um monitor, em vez de um programa ou uma área de trabalho. Para obter mais informações, consulte [compartilhar sua área de trabalho ou de um programa no Lync](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842).
    
- Em vez de compartilhamento, enviar os slides do PowerPoint antes do tempo como reunião anexo de solicitação para que os participantes visualizarem os slides em seu dispositivo de cliente. Para obter mais informações, consulte [Configure uma reunião do Lync](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d).
    
-  Desempenho do vídeo depende muito o desempenho da rede. Evite usar vídeo se a sua rede está lenta. 
    
Para obter mais informações, consulte [qualidade de vídeo no Lync Online ou de áudio ruim](https://support.microsoft.com/kb/2386655) e [tela lenta atualizar no Lync 2013](https://support.microsoft.com/kb/2958375).
  
## <a name="best-practices-for-using-sharepoint-lists"></a>Práticas recomendadas para usar as listas do SharePoint

Trabalhando com dados de lista offline para "eliminar", analisar ou relatar dados são uma ótima maneira de minimizar o impacto de uma rede lenta. Você pode ler e gravar a maioria das listas do Microsoft Access 2013 vinculando a eles. Você também pode exportar uma lista para uma tabela do Excel, que cria uma conexão de dados unidirecional entre a tabela do Excel e a lista.
  
Além disso, se o recurso de serviços do Access está ativado, você poderá trabalhar com consideravelmente mais dados do que o limite de exibição de lista, até 50.000 itens por padrão. Tanto Access 2013 and Excel 2013 processam automaticamente os dados da lista em lotes pequenos e, em seguida, monte os dados, uma técnica que permite trabalhar com dados substancialmente mais que o limite do modo de exibição de lista e sem afetar adversamente o desempenho do serviço do outros usuários. 
  
Para obter mais informações, consulte a seção "mais informações sobre o gerenciamento de grandes listas" em [gerenciar grandes listas e bibliotecas no Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).
  
## <a name="best-practices-for-customizing-web-pages"></a>Práticas recomendadas para personalizar as páginas da web

Quando você personaliza a uma página da web, você pode causar inadvertidamente desempenho ruim com a página. Vários fatores podem ter um impacto, como a complexidade e o tamanho da página, quantos web parts são adicionados, quantos itens de lista ou biblioteca é exibido inicialmente e a maneira como você a página de código.
  
Para obter mais informações, consulte [performance ajustar o SharePoint Online](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance).
  
## <a name="best-practices-for-using-project-online"></a>Práticas recomendadas para usar o Project Online

As diretrizes a seguir podem ajudar a melhorar o desempenho da rede.
  
- Project Online e SharePoint Online exigem sincronização, que pode ser demorada. Se suas equipes de projeto tem rotatividade baixa, desabilite a sincronização de Site de projeto para melhorar o desempenho de publicação do projeto e páginas de detalhes do projeto. Limite de sincronização do Active Directory para grupos de recursos que realmente precisam usar o sistema e monitorar há potenciais problemas de permissão após a sincronização de grupos maiores. 
    
- Se sua organização usa sites do projeto, criá-los sob demanda em vez de automaticamente. Isso acelera a primeira experiência de publicação e evita a criação de conteúdo e sites desnecessárias.
    
- Páginas de detalhes do projeto (PDP) pode acionar um recálculo do todo o projeto e disparar ações de fluxo de trabalho, ambos os quais podem ser operações de alto desempenho. Para evitar o disparo dois processos de atualização ao mesmo tempo em que o mesmo PDP, evite atualizando os campos de calendário (data de início, data de término, data de Status e a data atual) e os campos não programada (nome do projeto, descrição e proprietário). 
    
- Reduza o número de Web Parts e campos personalizados exibidos em cada PDP. Crie um PDP dedicado com os únicos campos que requeiram a atualização para melhorar a carga e economize tempo. 
    
- Quando você usa o OData para relatórios, limite a quantidade de dados que você consultar em tempo de execução usando o recurso de filtragem do lado do servidor.
    
Para obter mais informações, consulte [performance ajustar o Project Online](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).
  
## <a name="whats-the-best-way-to-report-problems"></a>Qual é a melhor maneira de relatar problemas?

Microsoft continuamente melhora o desempenho geral do Office 365 por meio do monitoramento da rede, medir a largura de banda e latência, melhorando o tempo, reduzindo e/s em disco, de carga de página reprojetando páginas para usar mínimo estratégia baixar, adicionar hardware para data centers e adicionando mais centros de dados. Para obter mais informações sobre a verificação de seu status atual e relatar problemas, consulte [Exibir o status de seus serviços](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx).
  
## <a name="see-also"></a>Confira também

[Planejamento de rede e ajuste de desempenho para o Office 365](network-planning-and-performance.md)
  
[Curso Microsoft Virtual Academy — gerenciamento de desempenho do Office 365](https://blogs.office.com/2014/12/03/microsoft-virtual-academy-course-office-365-performance-management/)
  
[Gerenciar pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Perguntas frequentes sobre pontos de extremidade do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

