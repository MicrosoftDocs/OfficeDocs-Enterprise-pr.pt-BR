---
title: Use a ferramenta de diagnóstico de página para o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: Use o diagnóstico de página para a ferramenta SharePoint para analisar suas páginas clássicas contra as práticas recomendadas para o SharePoint Online.
ms.openlocfilehash: 6bfe26900426b30b9f0ad0746b0c1840e122dc82
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539378"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Use a ferramenta de diagnóstico de página para o SharePoint Online

Este artigo descreve como você pode usar a ferramenta de diagnóstico de página para analisar o clássicas páginas de publicação e páginas em sites de equipe clássico, em relação a um subconjunto das práticas recomendadas no **SharePoint Online**. 
  
Sites de equipe que não têm a publicação ativada não podem fazer com o uso das CDNs mas todas as demais regras são aplicáveis. Publicação adiciona sobrecarga adicional, portanto, não ative publicação apenas para obter a funcionalidade CDN conforme impactará negativamente tempos de carregamento de página.
  
> [!IMPORTANT]
> A ferramenta de diagnóstico de página não será executado em bibliotecas de documentos ou páginas de sistema, como a ferramenta foi projetada para examinar páginas do site do SharePoint. Uma página *AllItems* é uma página do sistema. Se você tentar executar a ferramenta em uma página do sistema, você receberá uma mensagem que lê, "Este aplicativo deve ser executado somente em páginas do SharePoint." > ![deve ser executado em uma página do SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)
  
> Isso não é um erro na ferramenta de forma que não há nenhum valor na avaliação bibliotecas ou páginas do sistema. Navegue até uma página do SharePoint não seja do sistema para usar a ferramenta. Se desejar fornecer comentários sobre a ferramenta por favor, clique na guia sobre e siga a [oferecer o link de comentários](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a>Como usar a ferramenta de diagnóstico de página
<a name="useit"> </a>

1. Usando um navegador Chrome, abra o [link para a ferramenta](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) diretamente ou abra a pesquisa no [Chrome navegador WebStore](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e instalar a extensão do navegador. 
    
    Revise a política de privacidade do usuário fornecidas na página descrição no repositório.
    
    Ao adicionar a ferramenta ao seu navegador, você verá o seguinte aviso de permissões.
    
    ![Permissões do repositório de cromo](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    Este aviso é in-loco, porque uma página pode conter o conteúdo de locais fora do SharePoint, dependendo da Web Parts e personalizações na página. Isso significa que a ferramenta lerá as solicitações e respostas quando clicar no botão Iniciar e apenas para a guia ativa do SharePoint onde a ferramenta está sendo executado. Essas informações são capturadas localmente pelo navegador da web e estará disponíveis por meio de exportação para o link JSON na ferramenta. **As informações não são enviadas a ou capturadas pela Microsoft.**
    
    > [!IMPORTANT]
    > Microsoft não lê os dados ou sites que você visita e não podemos capturar quaisquer informações pessoais, site ou fazer download de informações com esta ferramenta. A única informação registrada pela ferramenta é o nome do locatário, contagem e se a opção de registro em log de suporte é utilizada quando a ferramenta for executada da regra. Essas informações são para a Microsoft para analisar que desafios estão sendo apresentados pelos nossos clientes e garantir que a capacidade de registro em log de suporte não está sendo uso inadequada.
  
A ferramenta respeita o Microsoft Privacy política acessível [aqui](https://go.microsoft.com/fwlink/p/?linkid=857875). 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. (Opcional) Se desejar usar a ferramenta no modo de incognito Chrome, navegue até a extensão e clique em "permitir no incognito".
    
3. Navegue até a página de publicação clássica do SharePoint no SharePoint Online que você gostaria de revisar.
    
    > [!IMPORTANT]
    > Podemos ter permitido para "carregamento com atraso" de itens nas páginas; Portanto, a **ferramenta não será interrompida automaticamente**. Você deseja interromper a coleção, você pode clicar em **Parar**. (Isso é por design para atender em todos os cenários de carga de página) 
  
Antes de clicar em **Parar**, certifique-se de que os dados de rastreamento de rede estão concluídos. Caso contrário, você terá um rastreamento parcial. 
  
Além disso, a ferramenta é uma extensão de navegador e abrir várias guias ou windows permitirá que apenas uma instância ativa da ferramenta a ser executada ao mesmo tempo. Esta é uma limitação das extensões no navegador. 
  
4. Clique em sobre o logotipo de extensão ![Página de diagnósticos para logotipo do SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) para carregar a ferramenta e você serão apresentados com a seguinte janela pop-up extensão: 
    
    ![Ferramenta de diagnóstico de página Popup](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    Iniciar e parar follow operações o conceito básico de quando você clica em coleta e iniciar que a página será recarregado começará.
    
5. O primeiro link é o link **sobre** e fornecerá orientações gerais e detalhes sobre a ferramenta, incluindo um link de volta neste artigo. Ele também inclui um link direto para recomendações de desempenho do SharePoint, um aviso de terceiros e uma opção para fornecer comentários sobre a ferramenta. 
    
6. Revise as informações **ID de correlação, SPRequestDuration, SPIISLatency** **, hora e a URL de carga de página** . (Esta seção é informativa e pode ser usada para fins de alguns.) 
    
  - **CorrelationID** é um elemento importante ao trabalhar com as equipes de suporte da Microsoft, pois permite-los extrair dados de diagnósticos adicionais. 
    
  - **SPRequestDuration** é o tempo necessário para processar a página do servidor. Se esse tempo for longo, não necessariamente significa que o servidor estava executando mal, mas pode também refletem o número de chamadas e carregar enviados pela página para o servidor ex.: navegação estrutural, imagens grandes, muitas das chamadas de API poderiam contribuem para o tempo menor de servidor . 
    
  - **SPIISLatency** é o tempo em milissegundos gasto no servidor Web Front End quando ela recebe a solicitação para carregar a página. Este é um indicador da latência para iniciar o processamento de página e não inclui o tempo gasto para o aplicativo web responder. 
    
  - **Tempo de carregamento de página** é a hora registrada pela página desde o momento da solicitação até o momento em que a resposta foi recebida e lido pelo navegador. Nenhum tempo adicional é afetado pelo desempenho do computador e o tempo que leva para o navegador carregar. 
    
  - A **URL** (Uniform Resource Locator) é o endereço da web da página atual. 
    
7. Na **guia Diagnóstico** listará as regras e se alguma deles estão marcados com um vermelho ![cruze](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), e em seguida, existem problemas identificados na página.
    
    Cada regra tem seu próprio link "mais informações", se você clicar nele quando ele é vermelho. Isso levará você para os detalhes por trás essa regra e como corrigir o problema.
    
    ![Diagnósticos Red - regra open](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. Verificar o usuário executando como padrão
  
Verificar o desempenho da página não deve ser realizada quando conectado como uma conta de serviço, o administrador ou o administrador do conjunto de sites, ou seja, uma conta com privilégios elevados. Funcionalidade e scripts adicionais é carregadas especificamente para esses tipos de contas e não fornecerá uma representação verdadeira do desempenho da página.
    
2. Solicitações de seleção para SharePoint
  
A quantidade de dados e solicitações feitas ao servidor deve ser limitada como uma página sobrecarregada observarão desempenho ruim. Essa verificação verifica o número de solicitações sendo feita para SharePoint e informará quando as solicitações excedem 6 solicitações. A maioria das solicitações devem ser armazenados em cache e, portanto, não chamadas para cada carregamento de página. Cache deve ser configurado e utilizada pelo menos 15 minutos reduzir a quantidade de chamadas para uma página por cada usuário. Este é um problema comum e na maioria dos casos dados só muda diariamente mas a página verifica e busca dados de cada vez para cada página para cada usuário que geralmente é desnecessário.
    
3. Verificar usando CDNs
  
Redes de fornecimento de conteúdo foram fornecidas pela Microsoft e aqueles conhecido que aqui estão as redes conteúdo Online entrega do SharePoint. Há vários tipos disponíveis, bem como os diferentes serviços CDN como CDNs do SharePoint e, em seguida, CDNs no Windows Azure. [Use as orientações a seguir](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. Seleção de tamanhos de imagem grande
  
Imagens devem ser otimizadas para web utilizando o melhor tipos de web, como o PNG. Reprodução de imagens também deve ser utilizada e está disponível no SharePoint diretamente. Imagens / renderizações de imagem maiores do que 100kb será realçada como não otimizado para web. [Use as diretrizes a seguir para otimizar imagens](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. Seleção para a navegação estrutural
  
Navegação estrutural originalmente foi projetada para uso no SharePoint on-Premises onde o cache de objetos poderia ser utilizada. Navegação estrutural não é recomendada para uso no SharePoint Online e deve ser alterada para navegação gerenciada ou um provedor personalizado. [Use a seguinte orientação para otimizar a navegação.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. Procurar CBQ WebPart (CBQ - conteúdo por Web Part de consulta)
  
Web Part de consulta de conteúdo gera uma carga elevada de SQL que atravessam todos os itens na consulta para cada carregamento de página, para cada usuário. Ao contrário de uma instalação local, não há nenhum cache disponível para limitar o número de consultas necessárias para preencher esta Web Part. Como tal, CBQ executa lentamente e afeta o desempenho geral da página é por isso que ele não deve ser utilizado. Use a Web Part de pesquisa de conteúdo (CSWP) como a substituição para a Web Part de consulta de conteúdo. [Use a seguinte orientação relacionada à Web Part de pesquisa de conteúdo](https://go.microsoft.com/fwlink/?linkid=873245).
    
8. A **guia de rastreamento de rede** fornece * * * informações detalhadas sobre as solicitações para criar a página, bem como as respostas recebidas. O desempenho de cada solicitação e resposta são codificados por cores com base em seu impacto sobre o desempenho geral de página, ou seja, verde \< 500 ms, amarelado 500-1000 msegs e vermelha \> 1000 msegs. 
    
    Nessa guia, há uma exportação à opção JSON deve deseja baixar e compartilhar os detalhes da solicitação e a resposta.
    
    > [!IMPORTANT]
    > Passe o mouse sobre a URL abreviada para exibir a URL completa. 
  
    ![Rastreamento de rede](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    Nesta imagem o vermelho é a própria página e que sempre aparecerá vermelho, a menos que a página for carregada no \< 1000 msegs (isto é, de 1 segundo).
    
    Em alguns casos, *não haverá nenhum indicador de cor ou tempo porque os itens já tiverem sido armazenados em cache pelo navegador* . Para testar isso corretamente, abra a página, limpe o cache do navegador e, em seguida, clique em **Iniciar** se encontram que forçará uma carga de página "frio" e ser um reflexo true da carga de página inicial. Isso, em seguida, deve ser comparado à carga de página "passiva" conforme que também ajudarão a determinar quais itens estão sendo armazenado em cache na página. 
    
9. Se você desejar compartilhar esses detalhes ou informações com seus desenvolvedores ou com uma pessoa de suporte, em seguida, você pode clicar em "Exportar para JSON" conforme a imagem acima e que irão descarregar os resultados. Observe que o arquivo pode então ser aberto usando um visualizador de arquivo JSON.
    
    > [!IMPORTANT]
    > Esses resultados irá conter a URL e, portanto, contém PII (informações de identificação pessoal) e você deve seguir as diretrizes da sua empresa antes de distribuir essas informações. 
  
10. Incluímos um **recurso de nível de suporte da Microsoft** que só deve ser utilizado quando estiver trabalhando diretamente em um caso de suporte para o desempenho. Utilizando a esse recurso não fornecerá nenhum benefício para você quando usado sem nossa equipe de suporte. Na verdade fará a página executar significativamente mais lento e uso continuado do recurso poderá ser considerado "uso indevido" do serviço. Não há nenhuma informação adicional ao usar esse recurso na ferramenta conforme as informações adicionais são adicionadas para o registro no serviço. 
    
    Nenhuma alteração é visível, exceto que você será notificado de que você habilitou e o desempenho da sua página será degradado significativamente por 2 - 3 vezes ao mesmo tempo, que é habilitado para um desempenho mais lento. Ele só será relevante para a página específica e dessa sessão ativa. Por esse motivo, isso deve ser usado com moderação e participando somente quando ativamente com nossa equipe de suporte.
    
    Para ativar o recurso por favor, abra a ferramenta e uso ALT-Shift-L que, em seguida, exibirá "habilitar o log de nível de suporte". Clique em que a caixa de seleção e depois clique em iniciam para recarregar a página e gerar o registro extenso para suporte analisar.
    
    ![Habilitado a opção de suporte](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    Um elemento importante para que isso é a CorrelationID conforme a equipe de suporte serão então, utilizar esse número para extrair as informações necessárias. Copie a CorrelationID e fornecer que para oferecer suporte à medida que eles não é possível executar o trabalho necessário sem o ID de completo.
    

