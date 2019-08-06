---
title: Preparar atributos de diretório para sincronizarem com o Office 365 usando a ferramenta IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Fornece instruções sobre como usar o IdFix para preparar e limpar o diretório local antes de sincronizar com o Office 365.
ms.openlocfilehash: cba2889673d1ff50161cde77670f06ab40e233c0
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490784"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Preparar atributos de diretório para sincronizarem com o Office 365 usando a ferramenta IdFix
Este tópico contém instruções detalhadas sobre como executar a ferramenta IdFix, alguns erros comuns que você pode encontrar, sugestões de correção, exemplos e práticas recomendadas para o que fazer se você tiver um grande número de erros.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Correção de erros no seu diretório usando a GUI do IdFix

[Execute a ferramenta IdFix do Office 365](install-and-run-idfix.md) para procurar problemas no seu diretório e, em seguida, corrija os erros na GUI, conforme descrito neste tópico. Se uma tabela em branco for retornada pela ferramenta, nenhum erro foi descoberto. Se houver muitos problemas em seu diretório, pode ser difícil quando a ferramenta retornar os erros. Uma maneira de resolver isso é corrigir todos os erros de um tipo primeiro e, em seguida, passar para o próximo tipo. 
  
1. Antes de começar a fazer alterações, dê uma olhada nas recomendações apresentadas pelo IdFix.
    
2. Examine a lista de erros que IdFix retornou. Você pode classificar os erros por tipo de erro clicando em **erro** na parte superior da coluna que lista os tipos de erro. Se mais de um erro estiver associado a um único atributo, os erros serão combinados em uma linha. Onde for possível, IdFix apresentará uma recomendação para uma correção na coluna **atualização** . A correção é baseada em uma verificação de outros atributos associados a um objeto. Embora eles geralmente sejam melhor do que o que já está no diretório, somente você pode decidir o que é realmente preciso. 
    
3. Se o IdFix tiver uma sugestão para uma correção de um erro de duplicação, a correção será identificada por um dos três sinalizadores no início do valor na coluna **Atualizar** , por exemplo `[E]john.doe@contoso.com`,. Se você aceitar a sugestão, quando aplicar a alteração, o sinalizador não será inserido no diretório. Somente o valor após o sinalizador de sugestão será aplicado, por exemplo, `john.doe@contoso.com`. Se você quiser aceitar a sugestão, selecione a ação correspondente na coluna **ação** . Os sinalizadores indicam ações da seguinte maneira: 
    
 - **[C]** ação sugerida **concluída**. O valor não precisa ser editado.
    
 - **[E]** **edição**de ação sugerida. O valor deve ser alterado para evitar conflito com outro valor no diretório.
    
 - **[R]** ação sugerida **Remove**. O valor é um proxy SMTP em um objeto não habilitado para email e provavelmente pode ser removido com segurança.
    
4. Depois de ler e entender os erros, atualize a entrada na coluna **Atualizar** com suas alterações e, na coluna **ação** , selecione o que você deseja que o IdFix faça para implementar a alteração. Por exemplo, dois usuários podem ter um `proxyAddress` identificado como duplicado. Somente um usuário pode usar o `proxyAddress` para entrega de email. Para corrigir isso, marque a coluna **ação** como **concluída** para o usuário com o valor correto e marque a coluna **ação** **remover** para o outro usuário. Isso remove o `proxyAddress` atributo do usuário a quem isso `proxyAddress` não pertence e não faz nenhuma alteração no usuário para o qual isso `proxyAddress` está correto.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Erros comuns e correções detectadas pelo IdFix
A tabela a seguir descreve os erros detectados pelo IdFix, fornece as correções mais comumente sugeridas da ferramenta e, em alguns casos, fornece exemplos de como corrigi-los.

|**ERROS**|**Descrição do tipo de erro**|**Correção sugerida**|**Exemplo**|
|:-----|:-----|:-----|:-----|
|**caractere** | Caracteres ilegais. O valor contém um caractere que é inválido. | A correção sugerida para o erro mostrado na coluna **atualização** mostra o valor com o caractere inválido removido.  <br/> | Um espaço à direita no final de um endereço de email válido é um caractere inválido, por exemplo:  <br/> " `user@contoso.com` "  <br/> Um espaço à esquerda no início de um endereço de email válido é um caractere inválido, por exemplo:  <br/> " ` user@contoso.com `"  <br/>  O `ú` caractere é um caractere inválido. |
|**cópias** | Entrada duplicada. O valor tem uma duplicata dentro do escopo da consulta. Todos os valores duplicados serão exibidos como erros. | Editar ou remover valores para eliminar a duplicação. A ferramenta não fornecerá uma correção sugerida para duplicatas. Em vez disso, você deve escolher qual das duas ou mais duplicatas é a correta e excluir as entradas duplicadas. ||
|**format** | Erro de formatação. O valor viola os requisitos de formato para o uso de atributo. | A atualização sugerida mostrará o valor com caracteres inválidos removidos. Se não houver caracteres inválidos, a atualização e o valor aparecerão da mesma. Você precisa determinar o que você realmente deseja na atualização. A ferramenta não fornecerá uma correção sugerida para todos os erros de formatação. | Por exemplo, os endereços SMTP devem estar em conformidade com o RFC 2822 e o mailNickName não pode começar ou terminar com um ponto. Para obter mais informações sobre os requisitos de formato para atributos de diretório, consulte "objeto de diretório e preparação de atributo" em [preparar para provisionar usuários por meio da sincronização de diretório com o Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Domínio de nível superior. Isso se aplica a valores sujeitos à formatação [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) . Se o domínio de nível superior não for roteável pela Internet, ele será identificado como um erro. Por exemplo, um endereço SMTP termina em. local não é roteável pela Internet e poderia causar esse erro. |Altere o valor para um domínio de Internet roteável `.com` como `.net`ou. | Mude `myaddress@fourthcoffee.local` para `fourthcoffee.com` ou para outro domínio roteável pela Internet.  <br/> Para obter instruções, consulte [como preparar um domínio não roteável (como o domínio. local) para a sincronização de diretórios](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Erro na parte do domínio. Isso se aplica a valores sujeitos à formatação RFC 2822. Se a parte de domínio do valor for inválida e não estiver em conformidade com a RFC 2822, ela será gerada. | Altere o valor para um que esteja de acordo com a RFC 2822. Por exemplo, certifique-se de que ele não contenha espaços ou caracteres ilegais. | Alterar `myaddress@fourth coffee.com` para `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Erro de parte local. Isso se aplica a valores sujeitos à formatação RFC 2822. Se a parte local do valor for inválida e não estiver em conformidade com a RFC 2822, ela será gerada. |Altere o valor para um que esteja de acordo com a RFC 2822. Por exemplo, certifique-se de que ele não contenha espaços ou caracteres ilegais. |Alterar `my"work"address@fourthcoffee.com` para `myworkaddress@fourthcoffee.com`. |
|**comprimento** | Erro de comprimento. O valor viola o limite de tamanho para o atributo. Isso geralmente é encontrado quando o esquema de diretório é alterado.  | A atualização sugerida pelo IdFix truncará o valor para o comprimento aceitável.  <br/> Lembre-se de que isso pode produzir resultados indesejados. Você deve revisar a correção sugerida e alterá-la, se necessário, antes de clicar em **aplicar**. ||
|**brancos**  | Erro em branco ou nulo. O valor viola a restrição NULL para os atributos a serem sincronizados. Somente alguns atributos devem conter um valor. | Se possível, a atualização sugerida usará outros valores de atributo para gerar um substituto provável. ||
|**mailmatch** | Isso se aplica somente ao Office 365 dedicado. O valor não corresponde ao atributo de email. | A atualização sugerida será o valor do atributo de email prefixado por "SMTP:". ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Operações que você pode executar usando o IdFix
Para corrigir um erro, selecione uma opção na lista suspensa **ação** . A tabela a seguir descreve as operações de **ação** que você pode executar em atributos usando a ferramenta IdFix. Se você deixar a coluna de **ação** vazia, a ferramenta IdFix não executará nenhuma ação nesse erro específico no diretório. 

|**AÇÃO**|**Descrição da ação**|**Exemplo**|
|:-----|:-----|:-----|
|**COMPLETAMENTE** | O valor original é aceitável e não deve ser alterado apesar de ser identificado como um erro. | Dois usuários têm um proxyAddress identificado como duplicado. Somente um pode usar o valor para entrega de email. Marque o usuário com o valor correto como **concluído**. |
|**REMOVER** | O valor do atributo será excluído do objeto de origem. No caso de um atributo com vários valores, por exemplo `proxyAddresses`, apenas o valor individual mostrado será excluído. | Dois usuários têm um proxyAddress identificado como duplicado. Somente um pode usar o valor para entrega de email. Marcar o usuário com o valor duplicado como **Remove**. |
|**EDITAR** | As informações na coluna **Atualizar** serão usadas para modificar o valor do atributo. Se um valor de **atualização** válido tiver sido sugerido por IdFix, na coluna **ação** , selecione **Editar** e vá para o próximo erro. Se você não gostar da sugestão, digite uma nova na coluna **Atualizar** e, em seguida, na coluna **ação** , selecione **Editar**. ||
|**COMANDO** | Essa opção só estará disponível se você tiver restaurado de um log de transações. Se você selecionar **desfazer**, o valor do atributo será restaurado para o valor original. ||
|**FAIL** | Esse valor só será retornado se um valor de **atualização** tiver um conflito desconhecido com as regras do AD DS. Nesse caso, você pode editar o valor na coluna **atualização** novamente se souber o que é a falha. Pode ser necessário analisar os valores no objeto usando o ADSI Edit. Para obter mais informações, consulte [ADSI Edit (Adsiedit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Após escolher uma **ação** para um erro ou lote de erros, clique em **aplicar**. Quando você clica em **aplicar**, a ferramenta faz as alterações no diretório. Você pode fornecer correções para vários erros antes de clicar em **aplicar** e o IdFix todos serão alterados ao mesmo tempo.

Execute o IdFix novamente para garantir que as correções que você fez não introduziu novos erros. Você pode repetir essas etapas quantas vezes for necessário. É uma boa ideia passar pelo processo algumas vezes antes de sincronizar.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Alterar o conjunto de regras usado pelo IdFix
Por padrão, o IdFix usa o conjunto de regras multilocatário para testar as entradas no seu diretório. Este é o conjunto de regras correto para a maioria dos clientes do Office 365 =. No entanto, se você for um cliente do Office 365 dedicado ou ITAR (leis internacionais de tráfego de braços), poderá configurar o IdFix para usar o conjunto de regras dedicado. Se você não tiver certeza sobre o tipo de cliente que você está, pode ignorar esta etapa com segurança. Para definir o conjunto de regras como dedicado, clique no ícone de engrenagem na barra de menus e, em seguida, clique em **dedicado**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Alterar o escopo da pesquisa usada pelo IdFix
Por padrão, o IdFix pesquisa todo o diretório. Se quiser, você pode configurar a ferramenta para pesquisar em uma subárvore específica. Para fazer isso, na barra de menus, clique no ícone de filtro e insira uma subárvore válida.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Reverter suas alterações usando a GUI do IdFix
Cada vez que você clica em **aplicar** para aplicar alterações, a ferramenta IdFix cria um arquivo separado chamado log de transações que lista as alterações que você acabou de fazer. Você pode usar o log de transações para reverter apenas as alterações que estão no log mais recente caso você cometa um erro. Se você cometer um erro enquanto estiver atualizando, poderá desfazer as alterações aplicadas mais recentemente clicando em **desfazer**. Quando você clica em **desfazer**, o IdFix usa o log de transações para reverter apenas as alterações que estão no log de transações mais recente. Para obter mais informações sobre como usar o log de transações, consulte [Reference: Office 365 IdFix Transaction log](idfix-transaction-log.md).

## <a name="next-step"></a>Próxima etapa

[Configurar a sincronização de diretórios](set-up-directory-synchronization.md)
