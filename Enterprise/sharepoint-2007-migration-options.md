---
title: Opções de migração do SharePoint 2007 a serem considerados
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007 atingiu o fim do suporte e é hora de atualização. Use este artigo para ajudá-lo a criar seu plano.
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169873"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Opções de migração do SharePoint 2007 a serem considerados

Microsoft SharePoint 2007 e o SharePoint Server 2007 alcançaram o fim do suporte. É hora de atualização! Este artigo fornece informações sobre as opções de migração.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Estratégias de atualização comuns para SharePoint

Há vários métodos para atualizar um ambiente do SharePoint Server. Se você tiver um farm do Microsoft Office SharePoint Server 2007, aqui estão alguns exemplos de como os métodos de atualização:
  
- Anexar banco de dados
    
- Atualização de lado a lado
    
- Atualização in-loco
    
- Atualização híbrida (in-loco com bancos de dados desanexados / separado com anexação de banco de dados)
    
- Híbridas do SharePoint (online conectar ao SharePoint local)
    
- Mova manualmente os dados entre conjuntos de sites ou bibliotecas
    
- Assistente de FastTrack atualizar para o Office 365 ([Supervisor de implantação do SharePoint Online](https://aka.ms/spoguidance))
    
- API de migração para o SharePoint Online (SPO) no Office 365
    
O que funciona melhor para você?
  
Seus conhecimentos sobre o que faz seu farm e é usado para é uma força tática quando se trata de atualizar. A maneira como as pessoas usam o Farm do SharePoint ajudarão você a escolha uma das suas opções.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 também tem uma atualização gradual não abordada aqui. Para ver uma lista de atualização específica de etapa artigos consulte o [final do SharePoint Server 2007 do mapa de suporte](sharepoint-2007-end-of-support.md). 
  
Lembre-se de verificar qualquer outra versão do SharePoint que você está atualizando para o [Ciclo de vida do produto](https://support.microsoft.com/en-us/lifecycle/search) e os requisitos do sistema. Isso é para que você vai estar ciente à próxima atualização será necessária (por exemplo, se você pausar em um produto herdado como o SharePoint Server 2010 para planejar mais atualizações, certifique-se de que você saiba seu lado da data de suporte) e ter certeza de que você tem o hardware que ofereça suporte a seu plano. 
  
Se você estiver planejando fazer a transição de alguns ou todos os sites do SharePoint para o Office 365 na nuvem, este é um horário para indicar um link para as [Descrições do serviço para o Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Você precisará as descrições de serviço para saber mais sobre os recursos do SharePoint Online e como eles podem diferir o SharePoint Server no local. Atualize farms funcionais do Microsoft Office SharePoint Server 2007. Se sua instalação tiver sites que não estão funcionando, corrigi-los antes da atualização.
  
## <a name="a-note-about-managing-risk"></a>Uma observação sobre o gerenciamento de riscos

Métodos como 'lado a lado' são importantes no esquema de lógica de atualização. Quando você atualiza o lado a lado, você manter seu farm do Microsoft Office SharePoint Server 2007, mas criar um farm a próxima versão dele (SharePoint Server 2010) em um hardware novo. Isso ajuda de três maneiras:
  
1. Você tem um lugar para fazer backups de seus bancos de dados do Microsoft Office SharePoint Server 2007 para atualizá-los separadamente, usando o banco de dados anexado.
    
2. Se você descobrir que apenas um pequeno número de bibliotecas de documentos críticos e outras informações estão em uso em seu farm do Microsoft Office SharePoint Server 2007, você pode optar por mover manualmente os dados do Microsoft Office SharePoint Server 2007 para o SharePoint Server 2010 , ou assumir somente sites específicos e webs para a próxima versão (que pode tornar seu trabalho mais fácil).
    
3. Quanto menos fizer ao Microsoft Office SharePoint Server 2007 farm de servidores, diretamente, mais seguro os dados do farm contém como você atualizar.
    
Métodos, como atualização in-loco atuará diretamente no seu farm do Microsoft Office SharePoint Server 2007, dando opções fácil menos abandonar um caminho e começar novamente com o seu ambiente intacta. Construa tanto quanto possível, em algumas medidas de segurança (como aproveitando e testar os backups do ambiente original). Por exemplo, se seu farm do Microsoft Office SharePoint Server 2007 é virtual e é duplicado para fins de backup e restauração, em seguida, fazer backup e restaurar os bancos de dados mais recentes antes da sua janela de serviço para a atualização. Sabendo que você tem a opção Restaurar banco de dados backups não serão somente proporcionam à prova de falha, ele pode fornecer tranquilo.
  
> [!TIP]
> Documentos de práticas recomendadas para atualização existirem para o [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)e [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx). Você também pode pesquisar para [Parceiros da Microsoft](https://partnercenter.microsoft.com/en-us/pcv/search) que têm experiência com upgrades ou migrações do Office 365. 
  
## <a name="make-your-plan"></a>Verifique seu plano

Se você precisar atualizar, você precisa de um plano e não se ajusta o tamanho de um todos nesses casos. Seu plano pode ser tão simple quanto 'Criar uma assinatura do Office 365 com o SharePoint Online, registrar um domínio e redirecionar as pessoas para salvar seus arquivos lá'. E talvez não seja. Essa decisão é sua, e é para baixo até o que você e seus usuários realmente precisam.
  
> [!NOTE]
> É executado no software cujo ciclo de vida encerrou riscado. Produtos que estão fora do suporte são o patch não é mais quando são encontrados problemas. Isso também significa que não se surgirem novas ameaças à segurança haverá nenhum patches de segurança ou correções porque os fim do ciclo de vida produtos não são mais suportados. Por favor, evite essa situação! 
  
### <a name="first-know-your-farm"></a>Primeiro, saber seu farm

Ao atualizar, sua tomada de decisão deve se basear o que significa a seu farm para sua organização. Qual necessidade ele satisfazer? Qual é sua função? Cada farm da sua empresa pode ter uma função diferente. Alguns dos seus farms do SharePoint podem estar *crítico* , alguns podem estar arquivos compactados – daí mantê. Ou, se seu farm preenche muitas funções ao mesmo tempo, em seguida, você pode precisar saber quais conjuntos de sites, webs ou até mesmo as bibliotecas de documentos fazer, nenhuma personalização, e como importantes são. A análise dos dados neste nível pode parecer como muito trabalho, mas ele economiza tempo e esforço para dominar seu domínio antes de atualizar ou migrar, ele. Quando você souber a todas as partes móveis e os bits mais importantes, você também saberá o que você tiver superado e pode deixar para trás. Esse conhecimento só beneficiarão você no futuro. 
  
Portanto, o que os usuários dizem mais importantes sobre o seu farm do SharePoint Server?
  
- Recursos internos do SharePoint
    
- O corpus de dados grandes (por exemplo, um arquivo morto de arquivos)
    
- Disponibilidade
    
- Apps críticos, web parts ou documentos no farm (farm de missão crítica)
    
- Os padrões de conformidade atendidos
    
- Personalizações
    
Se você executar algo essencial para seus negócios de seu farm do SharePoint, digamos que age como um grande catálogo de dados essenciais sobre requisitos de serviço do cliente, você pode colocar uma escala ao lado de 'Apps críticos', mas também seria 'Disponibilidade' – ou seja, seu negócio afetado se você não podia usar SharePoint por algum tempo. Da mesma forma, você pode verificar 'Personalizações' porque o crítico services seu farm ofertas baseiam-se no código personalizado, definições de site ou um número de personalizações que trabalham juntos.
  
Se o SharePoint atendidos essas necessidades sem precisar fazer nada fora usando o que é incorporado ao software e você geralmente atualizá-lo e realizar a manutenção e administração normal, talvez você tenha escolhido 'SharePoint internas' – isso também pode ser sua motivo da sentado em uma versão mais antiga do SharePoint. Em outras palavras, ele já faz o que você precisa e você ainda não necessários para atualizar até agora, ao Microsoft Office SharePoint Server 2007 fim do suporte.
  
Quando você-lista com marcadores essas coisas, você cria critérios para a atualização. Em outras palavras, qualquer atualização teria que cumprir esta barra a serem considerados. Isso oferece uma maneira de eliminar os métodos que atualmente não atendem às suas necessidades.
  
### <a name="a-simple-sample-plan"></a>Um exemplo simples de plano

Há talvez precise ser mais largo consenso com liderança e outros admins no caminho que levará a atualização do SharePoint. Administradores do SharePoint Server com frequência cooperam com os administradores do Microsoft SQL Server, trabalhar com as equipes de rede e segurança e muito mais. Onde há muitas das partes interessadas, você pode precisar criar contrato para, ou ajustar, seu plano de atualização e migração. Por exemplo, se você migrar dados para que a parte de sua empresa usa o SharePoint Online no Office 365, há provavelmente precisará ser ajuste de desempenho ou testes dentro da sua rede. Equipes afetadas devem ser informadas antes do tempo.
  
No meu exemplo simple, posso mostram proposta do administrador do SharePoint e, em seguida, liste o plano de todos os participantes acordados. Para manter a clareza, documente seus contratos e decisões.
  
O plano começa após uma análise detalhada de um farm e tenta identificar a função do farm, pontos problemáticos e outras informações importantes que levarão a limitar algumas opções de atualização. Depois disso, uma proposta de atualização é feita pelo administrador do SharePoint, e os participantes concordam um plano de ação.
  
Minha lista de marcador 'mais importante':
  
- Disponibilidade, recursos internos para o SharePoint e os padrões de conformidade.
    
- A maioria dos dados está em três conjuntos de sites, com um espaço de trabalho de reunião usado por uma equipe de desenvolvimento particularmente importante e em uso intenso em vários fusos em todo o mundo.
    
- Há dezessete outros sites que são amplamente usados.
    
- Duas bibliotecas de documentos (espaço de trabalho de reunião e documentos no conjunto de sites raiz) são maiores (mais de 8000 docs cada). Temos um grande número de lista com anexos de planilha e documentos arquivados.
    
- Não há quatorze lista das bibliotecas que tenham dados confidenciais que devem permanecer em conformidade.
    
- Podemos deve ter a capacidade de fazer pausas e descoberta eletrônica, onde podemos ir.
    
- Alguns desses dados devem permanecer no local, devido às regras de InfoSec.
    
 **Minhas opções de atualização e migração:**
  
|||
|:-----|:-----|
|**Sim** <br/> |**Não** <br/> |
|Anexagem bancos de dados de atualização com o banco de dados  <br/> |Atualização in-loco  <br/> |
|Atualizar com farms lado a lado  <br/> |Atualização híbrida  <br/> |
|API de migração para o SPO no Office 365 (para dados de site pessoal)  <br/> |SharePoint híbrido (não necessária ainda)  <br/> |
|Alguns migrações manual de dados para o SharePoint Online para dados críticos  <br/> |Atualização de assistente FastTrack para o Office 365  <br/> |
   
 **Meu plano proposto:**
  
Atualização no local, com as versões do SharePoint--lado a lado, alguns virtualizado, de modo que podemos possa atualizar os bancos de dados pela primeira vez. Vá do SharePoint 2007 para o SharePoint 2010. Os administradores e desenvolvedores de teste do farm resultante. Os usuários de teste do farm resultante. Corrija quaisquer problemas de parar de Mostrar durante esse período. Novamente, lado a lado, a atualização do SharePoint 2010 bancos de dados para o SharePoint 2013. Teste de usuário Test. / piloto. Corrija quaisquer problemas de parar de Mostrar durante esse período.
  
- Considere a possibilidade de se uma pesquisa federados híbrida com SPO atenda às suas necessidades.
    
- Se você gostaria de atualizar para o SharePoint Online a partir daqui, considere [FastTrack assistência](https://fasttrack.microsoft.com) . 
    
- Determine se quaisquer conjuntos de sites podem ser transferidos para uma assinatura do Office 365. (O office 365 atende muitos [padrões de conformidade](https://technet.microsoft.com/library/office-365-compliance.aspx). Office 365 tem [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) e pode fazer [retenções](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) por meio do Centro de conformidade.) 
    
Caso contrário, continue com uma atualização lado a lado para o SharePoint Server 2016.
  
> [!NOTE]
> Entre as recomendações feitas por administradores que planejam a atualização e o processo real são as conversas que ocorrem com os outros participantes no qual a atualização se baseia. Por exemplo, em alguns casos, a economia força administradores para alterar seus planos. Seja qual for a decisão final é, devem ser documentadas qual é o plano acordados, no futuro. Ele pode parecer semelhante a esta: 
  
 **Meu plano de ação:**
  
No local, usamos um ambiente virtual para criar padrão do SharePoint Server 2010 e 2013. SharePoint Server 2016 serão criados em um hardware novo que atenda aos requisitos do sistema para 2016. Faremos anexa atualizar bancos de dados do SharePoint 2007 por meio de todas as versões entre ele e o SharePoint Server 2016 de banco de dados. Personalizações de núcleo estão sendo recriadas para e testado no SharePoint Server 2016 ambiente neste momento, se os recursos nativos já não atenderem às nossas necessidades. Se estamos bem-sucedida, podemos terão um farm local em um hardware novo com bancos de dados atualizados e menos personalizações. Podemos vai anexar os bancos de dados de conteúdo atualizados aos novos conjuntos de sites no SharePoint Server 2013, teste, piloto da teste usuário, e, em seguida, faça um DNS substituição para o novo ambiente do SharePoint Server 2016 para uso ao vivo.
  
- Não podemos irá considerar federados híbrida entre o SharePoint Server 2016 e SharePoint Online agora.
    
- Um 35% estimado dos nossos sites podem ser transformado em novos sites SPO com domínios vanity, ou, por fim, se tornam OneDrive para armazenamento de negócios. Procurando outras oportunidades converter sites ou encaminhar novos sites para o SPO.
    
- Alguns nesta parte da migração será manual, arrastar e soltar ao OneDrive para sites pessoais de negócios e alguns pelo API de migração.
    
Etapas mais detalhadas, ou um número de links para instruções específicas de atualização deve seguir um plano. O computador do MOSS 2007 não deve ser encerrado e ambientes virtuais devem ser mantidas para fins de comparação; No entanto, a atualização estará concluída quando os usuários serão redirecionados para o SharePoint Server 2016.
  
Frequentemente principais fatores na escolha de um método são o custo total da atualização e o custo em tempo (você verá obter mais informações sobre isso no artigo roteiro de migração do SharePoint). Entretanto, planejar com antecedência se beneficiarão você significativamente na definição de expectativas, escolhendo comparecer, e o que é sucesso de enquadramento terá a seguinte aparência.
  
## <a name="related-links"></a>Links relacionados

[Recursos para ajudá-lo a atualizar do Office 2007 servidores e clientes](upgrade-from-office-2007-servers-and-products.md)
  
[Pesquisa Policy de Lifecycle do Microsoft and ciclo de vida](https://support.microsoft.com/en-us/lifecycle)
  
[Procurar Microsoft Partners que possa ajudar com atualização ou migração](https://partnercenter.microsoft.com/en-us/pcv/search)
  

