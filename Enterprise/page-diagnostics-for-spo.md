---
title: Usar a ferramenta diagnóstico de página para o SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
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
description: Use a ferramenta diagnóstico de página para SharePoint para analisar suas páginas clássicas em relação às práticas recomendadas para o SharePoint Online.
ms.openlocfilehash: f61d680ab4470429436cd0bb88925c2f1fc63323
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616794"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Usar a ferramenta diagnóstico de página para o SharePoint Online

Este artigo descreve como você pode usar a ferramenta de diagnóstico de página para analisar suas páginas de publicação clássicas e páginas em sites de equipe clássicos, em um subconjunto de práticas recomendadas no **SharePoint Online**. 
  
Os sites de equipe que não têm publicação habilitado não podem usar o CDNs, mas todas as regras restantes são aplicáveis. A publicação adiciona sobrecarga adicional, portanto, não ative a publicação apenas para obter a funcionalidade da CDN, já que afetará negativamente o tempo de carregamento da página.

**Observe que v 1.05 foi lançado, portanto, atualize sua extensão, caso já tenha sido instalada**. Se você não tiver certeza sobre qual versão você tem, clique no link "sobre" para verificá-la.
  
> [!IMPORTANT]
> A ferramenta diagnóstico de página não será executada em bibliotecas de documentos ou páginas do sistema, pois a ferramenta foi projetada para examinar as páginas do site do SharePoint. Uma página *AllItems. aspx* é uma página de sistema. Se você tentar executar a ferramenta em uma página do sistema, receberá uma mensagem que diz "este aplicativo deve ser executado somente em páginas do SharePoint." <br/> ![Deve ser executado em uma página do SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>Isso não é um erro na ferramenta, já que não há nenhum valor em avaliar bibliotecas ou páginas do sistema. Navegue até uma página que não seja do sistema do SharePoint para usar a ferramenta. Se isso ocorrer em uma página do SharePoint, verifique a MasterPage, já que já vimos os clientes removerem as marcas meta do SharePoint e a página não é mais uma página do SharePoint. Se você quiser fazer comentários sobre a ferramenta, clique na guia sobre e siga o [link enviar comentários](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Instalar a ferramenta de diagnóstico de página

> [!IMPORTANT]
> A Microsoft não lê os dados ou sites que você visita e não capturamos informações pessoais, sites ou informações de download com essa ferramenta. A única informação registrada pela ferramenta é o nome do locatário, a contagem de regra e se a opção de registro em log de suporte foi utilizada quando a ferramenta é executada. Estas informações são para a Microsoft analisar quais desafios estão sendo enfrentados por nossos clientes e para garantir que o recurso de registro de suporte não esteja sendo usado de forma inválida.

1. Usando um navegador Chrome, abra o [link para a ferramenta](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) diretamente ou abra a pesquisa no webstore do [navegador Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e instale a extensão do navegador. Revise a política de privacidade do usuário fornecida na página de descrição da loja. Ao adicionar a ferramenta ao navegador, você verá o aviso de permissões a seguir.<br/>![Permissões do repositório Chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Este aviso está no local porque uma página pode conter conteúdo de locais fora do SharePoint, dependendo das Web Parts e personalizações na página. Isso significa que a ferramenta lerá as solicitações e respostas quando o botão iniciar for clicado e apenas para a guia ativa do SharePoint, onde a ferramenta está em execução. Essas informações são capturadas localmente pelo navegador da Web e estão disponíveis por meio do link exportar para JSON na ferramenta. **As informações não são enviadas ou capturadas pela Microsoft.** (A ferramenta respeita a política de privacidade da Microsoft acessível [aqui](https://go.microsoft.com/fwlink/p/?linkid=857875)).<br/><br/>A funcionalidade "exportar para JSON" na ferramenta é também por que a permissão "gerenciar seus downloads" é necessária. Siga as diretrizes de privacidade da sua empresa antes de compartilhar o arquivo JSON fora da sua organização, já que os resultados contêm URLs e que podem ser classificados como PII (informações de identificação pessoal).
    
2. (Isso é opcional) Se você quiser usar a ferramenta no modo incógnito do Chrome, navegue até a extensão e clique em **permitir no incógnito**.
    
3. Navegue até a página de publicação clássica do SharePoint no SharePoint Online que você gostaria de revisar. Nós permitimos o "carregamento de atraso" dos itens nas páginas; Portanto, a **ferramenta não será interrompida automaticamente**. Se você deseja interromper a coleta, clique em **parar**. (Isso é design para atender a todos os cenários de carregamento de página.) Antes de clicar em **parar**, verifique se os dados de rastreamento de rede estão concluídos. Caso contrário, você terá um rastreamento parcial. Além disso, a ferramenta é uma extensão do navegador e abrir várias guias ou o Windows permitirá que apenas uma instância ativa da ferramenta seja executada de uma só vez. Essa é uma limitação das extensões no navegador. 
  
4. Clique no logotipo de extensão ![Diagnóstico de página para o logotipo do SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) para carregar a ferramenta e será exibida a seguinte janela pop-up de extensão:<br/> ![Pop-up de ferramentas de diagnóstico de página](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Operações de início e parada seguem o conceito básico de quando você clica em iniciar a página será recarregada e a coleta começará.

Leia as seções a seguir para saber mais sobre as informações fornecidas na ferramenta.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>O que você verá na ferramenta diagnóstico de página
    
1. O link **about** fornecerá orientações gerais e detalhes sobre a ferramenta, incluindo um link de volta para este artigo. Ele também inclui um link direto para as recomendações de desempenho do SharePoint, um aviso de terceiros e uma opção para fornecer comentários sobre a ferramenta. 
    
2. A **ID de correlação, SPRequestDuration, SPIISLatency**, **tempo de carregamento de página**e detalhes de **URL** são informativas e podem ser usadas para alguns fins. 
    
  - **** O CorrelationId é um elemento importante quando se trabalha com as equipes de suporte da Microsoft, pois permite que eles recebam dados de diagnóstico adicionais. 
    
  - **SPRequestDuration** é o tempo decorrido do servidor para processar a página. Se esse tempo for longo, isso não significa necessariamente que o servidor estava funcionando incorretamente, mas também pode refletir o número de chamadas e a carga enviada pela página para o servidor, por exemplo, navegação estrutural, imagens grandes, muitas chamadas de API podem contribuir para o tempo de servidor mais longo . 
    
  - **SPIISLatency** é o tempo, em milissegundos, obtido no servidor Web front-end quando recebe a solicitação para carregar a página. Este é um indicador de latência para iniciar o processamento da página e não inclui o tempo gasto pelo aplicativo Web para responder. 
    
  - O **tempo de carregamento da página** é o tempo registrado pela página a partir da hora da solicitação até o momento em que a resposta foi recebida e lida pelo navegador. Qualquer tempo adicional é afetado pelo desempenho do computador e o tempo que ele leva para o navegador ser carregado. 
    
  - A **URL** (Uniform Resource Locator) é o endereço da Web da página atual. 
    
3. A [guia **diagnóstico** ](#how-to-use-the-diagnostic-tab) listará as regras e, se qualquer uma delas estiver marcada com uma ![Cruz](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)vermelha, haverá problemas identificados na página.<br/>Cada regra tem seu próprio link "mais informações" que você clica se um item está vermelho. Isso o levará para os detalhes por trás dessa regra e como corrigir o problema.<br/>![Diagnóstico vermelho-regra aberta](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Uma [guia **rastreamento de rede** ](#how-to-use-the-network-trace-tab) fornece detalhes sobre solicitações e respostas de compilação de página.

## <a name="how-to-use-the-diagnostic-tab"></a>Como usar a guia diagnóstico

1. **Verificar executando como usuário padrão**  Verificar o desempenho da página não deve ser executado quando estiver conectado como uma conta de serviço, administrador ou administrador de conjunto de sites ou qualquer conta com privilégios elevados. Scripts e funcionalidades adicionais são carregados especificamente para esses tipos de contas, portanto, os resultados não serão uma representação real do desempenho da página.
    
2. **Verificar solicitações para o SharePoint**  A quantidade de dados e solicitações feitas no servidor deve ser limitada à medida que uma página sobrecarregada sofrerá um desempenho ruim. Essa verificação verifica o número de solicitações que estão sendo feitas no SharePoint e aconselha quando as solicitações excedem 6 solicitações. A maioria das solicitações deve ser armazenada em cache e, portanto, não é chamada para cada carregamento de página. O cache deve ser configurado e utilizado por pelo menos 15 minutos para reduzir a quantidade de chamadas para uma página por cada usuário. Esse é um problema comum e, na maioria dos casos, os dados só são alterados diariamente, mas a página verifica e busca dados cada vez para cada página para cada usuário que geralmente é desnecessário.
    
3. **Verificar usando CDNs**  As redes de distribuição de conteúdo (CDNs) foram fornecidas pela Microsoft e as que mencionamos aqui são as redes de distribuição de conteúdo do SharePoint Online. Há vários tipos disponíveis, bem como diferentes serviços de CDN, como o SharePoint CDNs e, em seguida, CDNs no Azure. [Use as orientações a seguir](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Verificar tamanhos de imagem grandes**  As imagens devem ser otimizadas para Web por meio da utilização de tipos de Web melhores como PNG. As representações de imagem também devem ser utilizadas e estão disponíveis diretamente no SharePoint. Imagens/renderizações de imagem maiores do que 100kb serão realçadas como não otimizadas para Web. [Use as orientações a seguir para otimizar imagens](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Verificar a navegação estrutural**  A navegação estrutural foi originalmente projetada para uso no SharePoint local onde o cache de objetos pode ser utilizado. A navegação estrutural não é recomendada para uso no SharePoint Online e deve ser alterada para navegação gerenciada ou um provedor personalizado. [Use as orientações a seguir para otimizar a navegação.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Verificar Web part CBQ** (CBQ-conteúdo pela Web Part de consulta)  O conteúdo da Web Part de consulta gera uma alta carga de SQL à medida que atravessa todos os itens na consulta para cada e qualquer carga de página, para cada usuário. Ao contrário de uma instalação local, não há cache disponível para limitar o número de consultas necessárias para preencher esta Web Part. Como tal, CBQ é executado lentamente e impacta o desempenho geral da página, por isso ele não deve ser utilizado. Use a Web Part de pesquisa de conteúdo (CSWP) como substituição para a Web Part de consulta de conteúdo. [Use as orientações a seguir relacionadas à Web Part de pesquisa de conteúdo](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>Como usar a guia rastreamento de rede
    
A guia **rastreamento de rede** fornece informações detalhadas sobre as solicitações para criar a página, bem como as respostas recebidas. 

1. **Procure tempos de carregamento de item sinalizados como vermelho**. O desempenho de cada solicitação e resposta são codificados em cores, com base em seu impacto no desempenho geral da página da seguinte maneira:
- Verde: \< 500 milhões
- Amarelo: 500-1000ms
- Vermelho: \> 1000ms
<br/>![Rastreamento de rede](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/> Na imagem mostrada acima, o item vermelho pertence à página padrão. Ele sempre mostrará vermelho, a menos que a \< página seja carregada no 1000ms (menos de 1 segundo).

2. **Teste os tempos de carregamento do item**. Em alguns casos, não haverá nenhum indicador de tempo ou de cor porque os itens já foram armazenados em cache pelo navegador. Para testar corretamente, abra a página, limpe o cache do navegador e, em seguida, clique em **Iniciar** como isso forçará uma carga de página "Cold" e será uma reflexão verdadeira da carga inicial da página. Isso deve ser comparado com a carga de página "quente" como isso também ajudará a determinar quais itens estão sendo armazenados em cache na página. 
    
3. **Compartilhar detalhes relevantes com outras pessoas que podem ajudar a investigar problemas**. Para compartilhar os detalhes ou as informações fornecidas na ferramenta com seus desenvolvedores ou um profissional de suporte técnico, clique em **exportar para JSON** (conforme mostrado na imagem acima). Isso permitirá que você baixe os resultados, exibíveis com um visualizador de arquivos JSON.

> [!IMPORTANT]
> Esses resultados contêm URLs e que podem ser classificados como PII (informações de identificação pessoal). Certifique-se de seguir as diretrizes da sua organização antes de distribuir essas informações. 

## <a name="engaging-with-microsoft-support"></a>Contratando o suporte da Microsoft
   
Incluímos um **recurso de nível de suporte da Microsoft** que só deve ser utilizado ao trabalhar diretamente em um caso de suporte para desempenho. A utilização desse recurso não fornecerá nenhum benefício quando for usada sem nossa equipe de suporte. Na verdade, a página é executada significativamente mais lentamente e o uso contínuo do recurso pode ser considerado "mau uso" do serviço. Não há informações adicionais ao usar esse recurso na ferramenta, pois as informações adicionais são adicionadas ao registro em log no serviço. 

Nenhuma alteração é visível, exceto que você será notificado de que a habilitou e que o desempenho da página será significativamente reduzido por 2-3 vezes o desempenho mais lento enquanto isso estiver habilitado. Ele só será relevante para a página específica e essa sessão ativa. Por esse motivo, isso deve ser usado com moderação e apenas quando ativamente envolvido com nossa equipe de suporte.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Para habilitar o recurso de nível de suporte da Microsoft

1. Abra a ferramenta diagnóstico de página.
2. No teclado, pressione ALT-SHIFT-L. Isso exibirá a habilitação do **log de nível de suporte**. 
3. Marque a caixa de seleção e clique em **Iniciar** para recarregar a página e gerar registro detalhado para obter suporte para análise.<br/>![Opção de suporte habilitada](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Um elemento importante para esse é o CorrelationId como a equipe de suporte utilizará esse número para extrair as informações necessárias. Copie o CorrelationId (na parte superior da ferramenta de diagnóstico de página) e forneça a eles suporte, pois eles não podem executar o trabalho necessário sem a ID completa.
    
## <a name="related-topics"></a>Tópicos relacionados

[Ajustar o desempenho do SharePoint Online](tune-sharepoint-online-performance.md)

[Ajustar o desempenho do Office 365](tune-office-365-performance.md)

[Redes de distribuição de conteúdo](content-delivery-networks.md)
