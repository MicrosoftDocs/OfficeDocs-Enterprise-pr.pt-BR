---
title: "Exibir usuários licenciados e não licenciados com o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: O365ITProTrain, Ent_Office_Other, PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: "Explica como usar o Office 365 PowerShell para exibir as contas de usuários licenciados e não licenciados."
ms.openlocfilehash: e691ba7db96b34166f03ccd90d87fee0d2ee09f8
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Exibir usuários licenciados e não licenciados com o Office 365 PowerShell

**Resumo:** explica como usar o Office 365 PowerShell para exibir as contas de usuários licenciados e não licenciados.
  
As contas de usuário em sua organização do Office 365 podem ter algumas, todas ou nenhuma das licenças disponíveis atribuídas a elas em planos de licenciamento que estão disponíveis em sua organização. Você pode usar o Office 365 PowerShell para localizar rapidamente os usuários licenciados e não licenciados em sua organização.
  
## <a name="before-you-begin"></a>Antes de começar

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Confira instruções em [Conectar-se ao Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.
    
## <a name="the-short-version-instructions-without-explanations"></a>A versão curta (instruções sem explicações)

Esta seção apresenta os procedimentos sem divulgação ou explicação supérflua. Se tiver dúvidas ou quiser mais informações, leia o restante do tópico.
  
Para visualizar a lista de todas as contas de usuários e os respectivos status de licenciamento em sua organização, execute o seguinte comando no Office 365 PowerShell:
  
```
Get-MsolUser -All
```

Para visualizar a lista de todas as contas de usuários não licenciados em sua organização, execute o seguinte comando:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Para visualizar a lista de todas as contas de usuários licenciados em sua organização, execute o seguinte comando:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>A versão longa (instruções com explicações detalhadas)

As contas de usuário do Office 365 e as licenças do Office 365 não precisam ter uma correspondência direta: é possível ter os usuários do Office 365 que não têm uma licença do Office 365 e é possível ter licenças do Office 365 que ainda não foram atribuídas a um usuário. Na verdade, uma única conta de usuário pode até ter *várias* licenças do Office 365. Quando você cria uma nova conta de usuário do Office 365 (confira mais informações no artigo [Licenciar usuários do Office 365 com o Windows PowerShell](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx)), não precisa atribuir uma licença ao usuário: o novo usuário terá uma conta válida, mas não poderá entrar no Office 365. Se tentar entrar, verá algo parecido com isto:
  
![Usuário sem uma licença válida do Office 365.](images/o365_powershell_no_license.png)
  
Da mesma forma, você pode ter um usuário que ficará de férias ou ausente por um longo período. Nesse caso, você poderia remover a licença do usuário, mas deixar a conta intacta (isto é, manter todos os valores de propriedades, como endereço e telefone, como estão). Ao fazer isso, você pode atribuir a licença a outra pessoa (por exemplo, um funcionário temporário que esteja substituindo a pessoa que está de férias). Quando o usuário voltar ao trabalho, você poderá emitir uma nova licença, e ele poderá retomar o trabalho como se nunca tivesse saído.
  
Isso tudo quer dizer que você pode ter, sim, usuários com contas, mas sem licenças. Ou vice-versa.
  
O artigo [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) explica como determinar o número de licenças do Office 365 que a sua organização comprou, além de quantas dessas licenças foram atribuídas a usuários. Essas são informações importantes. No entanto, é igualmente importante saber quais dos usuários receberam essas licenças e quais não receberam. Este artigo mostrará como fazer exatamente isso.
  
Como você já deve saber, o cmdlet **Get-MsolUser** retorna informações sobre todas as suas contas de usuário do Office 365. Precisa de informações rápidas sobre todos os usuários do Office 365? Então execute este comando no Office 365 PowerShell:
  
```
Get-MsolUser
```

Por sua vez, Get-MsolUser retorna dados parecidos com estes:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

Como você pode ver, um dos valores de propriedade retornados é para a propriedade **isLicensed**. Se **isLicensed** for igual a `False`, significará que o usuário não tem uma licença do Office 365. Ou seja, se quisesse, você poderia simplesmente percorrer a lista de usuários e escolher aqueles em que a propriedade **isLicensed** esteja definida como `False`.
  
De qualquer forma, rolar pela lista de usuários para tentar escolher os que não têm licenças funciona bem desde que você tenha uma quantidade relativamente pequena de usuários. Se houver um grande número de usuários, no entanto, rolar pela lista será, no melhor dos casos, extremamente tedioso. E, dependendo de como o Windows PowerShell foi configurado, provavelmente impossível, já que há um limite no número de linhas de resultados que podem ser exibidas no console do Windows PowerShell em um momento específico.
  
Com isto em mente, uma maneira muito melhor de listar os usuários não licenciados é executar o seguinte comando:
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Esse comando retorna apenas os usuários que não têm uma licença do Office 365. Em outras palavras:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

Como você pode ver, temos um usuário não licenciado. E se quiséssemos somente uma lista dos usuários *licenciados*? Isso é um pouco mais complicado, mas só um pouquinho:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

Esse comando, que procura todas as contas de usuário em que a propriedade **isLicensed** seja igual a `True`, retorna informações parecidas com esta:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

Como você pode ver, as informações não são retornadas para Brenda Fernandes. Por que não? Acertou: porque a propriedade **isLicensed** da conta de Brenda não está definida como `True`.
  
## <a name="see-also"></a>Confira também
<a name="SeeAlso"> </a>

Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

