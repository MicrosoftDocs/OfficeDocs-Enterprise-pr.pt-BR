---
title: Recuperar dados de relatório do locatário do cliente com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Resumo: Use o Windows PowerShell remoto para Microsoft Exchange Online para recuperar os relatórios de locatários individuais do cliente.'
ms.openlocfilehash: 478cd8736a837dae571e20f38187be087b48231a
ms.sourcegitcommit: 509bcf92580d7a0bcebbf6f1d10311d6b0014984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "31992821"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Recuperar dados de relatório do locatário do cliente com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)

 **Resumo:** use o Windows PowerShell remoto para Microsoft Exchange Online para recuperar os relatórios de locatários individuais do cliente.
  
Os Parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). podem acessar os dados que compõem os relatórios de locatários do cliente diretamente por meio do Windows PowerShell remoto para o PowerShell do Exchange Online. Isso permite aos parceiros coletar e salvar os dados dos relatórios e, em seguida, realizar outras operações neles. Depois de abrir uma conexão remota, recuperar dados de relatório de uma locação é o mesmo que executar qualquer cmdlet em uma locação do cliente.
  
Neste artigo, você vai aprender a usar o Windows PowerShell remoto para Exchange Online para se conectar a uma locação única do cliente e a recuperar um relatório. Por padrão, o Windows PowerShell não tem suporte para agregar dados de relatórios de várias locações do cliente. Os relatórios que você recuperar com esse procedimento são destinados apenas ao  _DelegatedOrg_ para o qual você se conectar.
  
 
## <a name="before-you-begin"></a>Antes de começar

- Você deve se conectar ao seu locatário do Exchange Online usando o Windows PowerShell remoto. Para obter instruções, confira [Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Executar a amostra do Get-StaleMailboxReport

Após abrir uma sessão remota do Exchange Online, execute este comando para recuperar o **Get-StaleMailboxReport** para o intervalo de datas de 25/03/2015 a 31/03/2015.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Há vários outros cmdlets de relatório disponíveis para o Exchange Online, para o Lync Online e para o SharePoint Online, dentre outros, que você pode usar para rastreamento de mensagens. Para saber mais sobre os cmdlets de relatórios disponíveis e sobre o Serviço Web de Relatório do Office 365, confira os tópicos da seção a seguir.
  
## <a name="see-also"></a>Confira também

#### 

[Serviço Web de Relatório do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlets de criação de relatórios no Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[Ajuda para parceiros](https://go.microsoft.com/fwlink/p/?LinkID=533477)

