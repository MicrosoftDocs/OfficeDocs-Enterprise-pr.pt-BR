---
title: Preparar atributos de diretório para sincronizarem com o Office 365 usando a ferramenta IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Fornece instruções sobre como usar o IdFix para preparar e limpar o seu diretório local antes de sincronizar com o Office 365.
ms.openlocfilehash: a4fc8af476ec8ffdd7d762796abe1ec210a1bacb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539392"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Preparar atributos de diretório para sincronizarem com o Office 365 usando a ferramenta IdFix
Este tópico contém instruções detalhadas sobre como executar a ferramenta IdFix, sugerido de alguns erros comuns que você pode encontrar, correções, exemplos e práticas recomendadas para o que fazer se você tiver um grande número de erros.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Corrigindo erros no diretório usando a GUI do IdFix
[Executar a ferramenta IdFix do Office 365](install-and-run-idfix.md) para procurar problemas no diretório e, em seguida, corrija os erros na GUI, conforme descrito neste tópico. Se uma tabela em branco é retornada pela ferramenta, nenhum erro foram descoberto. Se houver muitos problemas em seu diretório, ele pode ser cansativo quando a ferramenta retorna os erros. Uma maneira de lidar com isso é corrija todos os erros de um tipo primeiro e, em seguida, passar para o próximo tipo. 
  
1. Antes de começar a fazer alterações, observe as recomendações apresentadas pelo IdFix.
    
2. Verifique a lista de erros que o IdFix retornou. Você pode classificar os erros por tipo de erro clicando em **ERROR** na parte superior da coluna que lista os tipos de erro. Se mais de um erro estiver associado a um único atributo, os erros são combinados em uma fila. Sempre que possível, o IdFix apresenta uma recomendação para uma correção na coluna **UPDATE**. A correção é baseada em uma seleção de outros atributos associados a um objeto. Embora esses atributos sejam geralmente melhores do que os que já estão no diretório, só você pode decidir qual é realmente preciso. 
    
3. Se IdFix tiver uma sugestão para uma correção para um erro de duplicação, a correção é identificada por um dos três sinalizadores no início do valor na coluna **UPDATE** , por exemplo, `[E]john.doe@contoso.com`. Se você aceitar a sugestão, quando você aplica a alteração o sinalizador não será inserido no diretório. Somente o valor seguindo a sugestão sinalizador serão aplicadas, por exemplo, `john.doe@contoso.com`. Se você quiser aceitar a sugestão, selecione a ação correspondente na coluna **ação** . Os sinalizadores indicam ações da seguinte maneira: 
    
 - **[C]** Ação sugerida **COMPLETE**. O valor não precisa ser editado.
    
 - **[[E]** Ação sugerida **EDIT**. O valor deve ser alterado para evitar conflito com outro valor no diretório.
    
 - **[R]** Ação sugerida **REMOVE**. O valor é um proxy de SMTP em um objeto não ativado por email e pode, provavelmente, ser removido com segurança.
    
4. Depois de ter ler e compreendidos os erros, atualize a entrada na coluna **Atualizar** com suas alterações e na **ação** coluna selecione o que você deseja que o IdFix, fazer para implementar a alteração. Por exemplo, os dois usuários podem ter um `proxyAddress` identificado como duplicado. Somente um usuário pode usar o `proxyAddress` para entrega de email. Para corrigir esse problema, marcar a coluna **ação** **completo** para o usuário com o valor correto e marcar a coluna **ação** **Remover** o outro usuário. Isso remove o `proxyAddress` atributo do usuário a quem isso `proxyAddress` não pertence e não faz nenhuma alteração ao usuário para quem isso `proxyAddress` está correto.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Erros comuns e as correções detectadas pelo IdFix
A tabela a seguir descreve os erros que são detectados pelo IdFix, fornece as correções mais comumente sugeridas a partir da ferramenta e, em alguns casos, fornece exemplos de como corrigi-los.

|**ERRO**|**Descrição do Tipo de Erro**|**Correção Sugerida**|**Exemplo**|
|:-----|:-----|:-----|:-----|
|**character** | caracteres ilegais. O valor contém um caractere que não é válido. | A correção sugerida para o erro apresentado na coluna **UPDATE** mostra o valor com o caractere inválido removido.  <br/> | Um espaço à direita do final de um endereço de email válido é um caractere inválido, por exemplo:  <br/> " `user@contoso.com` "  <br/> Um espaço à esquerda no início de um endereço de email válido é um caractere inválido, por exemplo:  <br/> " ` user@contoso.com `"  <br/>  O `ú` caractere é um caractere inválido. |
|**duplicate** | Entrada duplicada. O valor tem uma duplicata dentro do escopo da consulta. Todos os valores duplicados serão exibidos como erros. | Edite ou remova valores para eliminar a duplicação. A ferramenta não fornecerá uma correção sugerida para duplicatas. Em vez disso, você deve escolher qual das duas ou mais duplicatas é a correta e excluir a entrada ou as entradas duplicadas. ||
|**format** | Erro de formatação. O valor viola os requisitos de formato para o uso do atributo. | O Update sugerido mostrará o valor com todos os caracteres inválidos removidos. Se não houver nenhum caractere inválido, o Update e o Value serão iguais. Você precisa determinar o que realmente deseja em Update. A ferramenta não fornecerá uma correção sugerida para todos os erros de formatação. | Por exemplo endereços SMTP devem estar em conformidade com a RFC 2822, e o mailNickName não pode começar ou terminar com um ponto. Para obter mais informações sobre os requisitos de formato dos atributos de diretório, consulte "Preparação de objetos e atributos de diretório" em [Prepare to para provisionar usuários por meio da sincronização de diretório para o Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Domínio de nível superior. Isso se aplica aos valores sujeitos a [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) formatação. Se o domínio de nível superior não é roteável da internet, em seguida, isso será identificado como um erro. Por exemplo, um endereço SMTP terminando em. local não é roteável da internet e pode causar esse erro. |Altere o valor para um domínio roteável da internet como `.com` ou `.net`. | Alterar `myaddress@fourthcoffee.local` para `fourthcoffee.com` ou outro domínio roteável da internet.  <br/> Para obter instruções, consulte [como preparar um domínio não roteáveis (por exemplo, o domínio. local) para sincronização de diretórios](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Erro de parte do domínio. Aplica-se a valores sujeitos à formatação RFC 2822. Se a parte do domínio do valor for inválida e não cumprir com a RFC 2822, este erro será gerado. | Altere o valor para um que está em conformidade com a RFC 2822. Por exemplo, certifique-se de que não contenha espaços nem caracteres ilegais. | Alterar `myaddress@fourth coffee.com` para `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Erro da parte do local. Aplica-se a valores sujeitos à formatação RFC 2822. Se a parte do local do valor for inválida e não cumprir com a RFC 2822, este erro será gerado. |Altere o valor para um que está em conformidade com a RFC 2822. Por exemplo, certifique-se de que não contenha espaços nem caracteres ilegais. |Alterar `my"work"address@fourthcoffee.com` para `myworkaddress@fourthcoffee.com`. |
|**length** | Erro de comprimento. O valor excede o limite de comprimento do atributo. É o erro mais comumente encontrado quando o esquema de diretório foi alterado.  | A atualização sugerida pelo IdFix irá truncar o valor para o comprimento aceitável.  <br/> Lembre-se de que isso pode produzir resultados indesejados. Você deve rever a correção sugerida e fazer a alteração conforme necessária, antes de clicar em **Apply**. ||
|**blank**  | Erro nulo ou em branco. O valor viola a restrição nulo para os atributos a serem sincronizados. Somente alguns atributos devem conter um valor. | Se possível, a atualização sugerida irá alavancar outros valores de atributos, a fim de gerar um substituto provável. ||
|**mailmatch** | Isso se aplica apenas dedicados do Office 365. O valor não coincide com o atributo mail. | A atualização sugerida será o valor do atributo de email precedido por "SMTP:". ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Operações que podem ser realizadas por meio do IdFix
Para corrigir um erro, você pode selecionar uma opção na lista suspensa **ação** . A tabela a seguir descreve as operações de **ação** que pode ser executada em atributos usando a ferramenta IdFix. Se você deixar vazio coluna **ação** , a ferramenta IdFix não terão qualquer ação sobre esse erro específico no diretório. 

|**AÇÃO**|**Descrição da ação**|**Exemplo**|
|:-----|:-----|:-----|
|**COMPLETE** | O valor original é aceitável e não deve ser alterado, apesar de ser identificado como um erro. | Dois usuários têm um proxyAddress identificado como duplicado. Somente um poderá usar o valor para a entrega de emails. Marque o usuário com o valor correto como **COMPLETE**. |
|**REMOVER** | O valor do atributo será excluído do objeto de origem. No caso de um atributo de valores múltiplos, por exemplo, `proxyAddresses`, somente o valor individual mostrado será excluído. | Dois usuários têm um proxyAddress identificado como duplicado. Somente um poderá usar o valor para a entrega de emails. Marque o usuário com o valor duplicado como **REMOVE**. |
|**EDITAR** | As informações na coluna **UPDATE** serão usadas para modificar o valor do atributo. Se um valor válido de **atualização** tiver sido sugerido pelo IdFix, em seguida, na coluna **ação** , selecione **Editar** e vá para o próximo erro. Se não gostar a sugestão, digite um novo na coluna **UPDATE** e em seguida, na coluna **ação** , selecione **Editar**. ||
|**DESFAZER** | Esta opção só está disponível caso tenha restaurado de um log de transação. Caso selecione **DESFAZER**, o valor do atributo será restaurado para o valor original. ||
|**FAIL** | Este valor só será retornado se um valor de **atualização** tem um conflito desconhecido com as regras do AD DS. Nesse caso, você pode editar o valor na coluna **UPDATE** novamente se você sabe o que é a falha. Talvez seja necessário analisar os valores no objeto usando o ADSI Edit. Para obter mais informações, consulte o [ADSI Edit (ADSIEdit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Depois de escolher uma **ACTION** para um erro ou um lote de erros, clique em **Apply**. Quando você clica em **Apply**, a ferramenta faz as alterações no diretório. Você pode fornecer correções para vários erros antes de clicar em **Apply** e o IdFix fará todas as alterações ao mesmo tempo.

Execute o IdFix novamente para garantir que as correções feitas não introduzem novos erros. Você pode repetir essas etapas quantas vezes precisar. É uma boa ideia passar pelo processo algumas vezes, antes de sincronizar.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Alterar o conjunto de regras usado pelo IdFix
Por padrão, o IdFix usa a regra de multilocatário definida para testar as entradas em seu diretório. Essa é a certa regra definida para a maioria dos Office 365 = aos clientes. No entanto, se você for um cliente ITAR (International tráfego nos Regulamentos de alerta) ou a dedicados do Office 365, você pode configurar o IdFix para usar a regra dedicada definida em vez disso. Se você não tiver certeza sobre qual tipo de cliente que você está, você pode ignorar com segurança esta etapa. Para definir a conjunto de regras para exclusivas, clique no ícone de engrenagem na barra de menus e clique em **exclusivas**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Alterar o escopo de pesquisa usado pelo IdFix
Por padrão, o IdFix pesquisa todo o diretório. Se desejar, você pode configurar a ferramenta para pesquisar uma subárvore específica. Para isso, na barra de menu, clique no ícone Filtro e insira uma subárvore válida.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Revertendo as alterações usando a GUI do IdFix
Cada vez que você clicar em **Apply** para aplicar as alterações, a ferramenta IdFix cria um arquivo separado chamado um log de transações que lista as alterações que você acabou de criar. Você pode usar o log de transação para reverter apenas essas alterações que estão no log de mais recente, caso você cometer um erro. Se você cometer um erro enquanto você está atualizando, você pode desfazer as alterações aplicadas mais recentemente clicando em **Desfazer**. Quando você clica **Desfazer**, o IdFix usa o log de transação para reverter apenas essas alterações que estão no log de transações mais recente. Para obter mais informações sobre como usar o log de transações, consulte [referência: log de transações do IdFix do Office 365](idfix-transaction-log.md).