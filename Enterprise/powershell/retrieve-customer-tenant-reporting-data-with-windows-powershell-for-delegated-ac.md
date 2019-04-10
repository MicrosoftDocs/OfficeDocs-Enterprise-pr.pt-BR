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
ms.openlocfilehash: 8df88e8b00cbd8e14558e423f41f45ea5f9bf26a
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001754"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="37c45-103">Recuperar dados de relatório do locatário do cliente com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="37c45-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="37c45-104">**Resumo:** use o Windows PowerShell remoto para Microsoft Exchange Online para recuperar os relatórios de locatários individuais do cliente.</span><span class="sxs-lookup"><span data-stu-id="37c45-104">**Summary:** Use remoteWindows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="37c45-p101">Os Parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). podem acessar os dados que compõem os relatórios de locatários do cliente diretamente por meio do Windows PowerShell remoto para o PowerShell do Exchange Online. Isso permite aos parceiros coletar e salvar os dados dos relatórios e, em seguida, realizar outras operações neles. Depois de abrir uma conexão remota, recuperar dados de relatório de uma locação é o mesmo que executar qualquer cmdlet em uma locação do cliente.</span><span class="sxs-lookup"><span data-stu-id="37c45-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="37c45-p102">Neste artigo, você vai aprender a usar o Windows PowerShell remoto para Exchange Online para se conectar a uma locação única do cliente e a recuperar um relatório. Por padrão, o Windows PowerShell não tem suporte para agregar dados de relatórios de várias locações do cliente. Os relatórios que você recuperar com esse procedimento são destinados apenas ao  _DelegatedOrg_ para o qual você se conectar.</span><span class="sxs-lookup"><span data-stu-id="37c45-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
<span data-ttu-id="37c45-111">Se deseja recuperar um único relatório para todas as locações do seu cliente, encontre um script de exemplo para fazer isso em [Agregar dados de relatório do cliente por meio do Windows PowerShell para parceiros com permissão de acesso delegado (DAP)](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md).</span><span class="sxs-lookup"><span data-stu-id="37c45-111">If you want to retrieve a single report for all your customer tenancies, a sample script to do this can be found in [Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="37c45-112">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="37c45-112">Before you begin</span></span>

- <span data-ttu-id="37c45-p103">Você deve se conectar ao seu locatário do Exchange Online usando o Windows PowerShell remoto. Para obter instruções, confira [Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="37c45-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="37c45-115">Executar a amostra do Get-StaleMailboxReport</span><span class="sxs-lookup"><span data-stu-id="37c45-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="37c45-116">Após abrir uma sessão remota do Exchange Online, execute este comando para recuperar o **Get-StaleMailboxReport** para o intervalo de datas de 25/03/2015 a 31/03/2015.</span><span class="sxs-lookup"><span data-stu-id="37c45-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="37c45-p104">Há vários outros cmdlets de relatório disponíveis para o Exchange Online, para o Lync Online e para o SharePoint Online, dentre outros, que você pode usar para rastreamento de mensagens. Para saber mais sobre os cmdlets de relatórios disponíveis e sobre o Serviço Web de Relatório do Office 365, confira os tópicos da seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="37c45-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="37c45-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="37c45-119">See also</span></span>

#### 

[<span data-ttu-id="37c45-120">Serviço Web de Relatório do Office 365</span><span class="sxs-lookup"><span data-stu-id="37c45-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="37c45-121">Cmdlets de criação de relatórios no Exchange Online</span><span class="sxs-lookup"><span data-stu-id="37c45-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="37c45-122">Ajuda para parceiros</span><span class="sxs-lookup"><span data-stu-id="37c45-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

