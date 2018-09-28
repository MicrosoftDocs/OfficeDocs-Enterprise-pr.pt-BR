---
title: Durante e após a migração dos dados
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Movimentações de dados são uma operação de back-end com um impacto mínimo para os usuários finais. Nenhuma ação é necessária, enquanto o Microsoft move cada serviço e os dados associados para seu locatário para um novo geo de datacenter. Transferência de dados e validação ocorrerem em segundo plano com antecedência com um impacto mínimo para os usuários.
ms.openlocfilehash: 0c715e80acbac126626c73a75fac1bbc809367e2
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975169"
---
# <a name="during-and-after-your-data-move"></a>Durante e após a migração dos dados

Movimentações de dados são uma operação de back-end com um impacto mínimo para os usuários finais. Nenhuma ação é necessária, enquanto o Microsoft move cada serviço e os dados associados para seu locatário para um novo geo de datacenter. Transferência de dados e validação ocorrerem em segundo plano com antecedência com um impacto mínimo para os usuários.
  
> [!NOTE]
> Movimentações ocorrerem em momentos diferentes para cada serviço. Como resultado, você verá a funcionalidade reduzida descrita para cada serviço em um horário diferente. 
  
Assista o Centro de mensagem do Office 365 confirmação quando movimentações para cada um do Exchange Online, SharePoint Online e Skype para negócios forem concluídas. Conforme mostrado na tabela a seguir, pode demorar até 24 meses, após o término do período de inscrição, para concluir os dados solicitados move para todos os clientes em um geo específico. Se você vir quaisquer problemas com seu locatário após a movimentação, contate o [Suporte do Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) para obter assistência. 
  

|**Clientes com o endereço de cobrança**|**Todas as movimentações concluídas por**|
|:-----|:-----|
|Austrália, Nova Zelândia, Fiji  <br/> |31 de outubro de 2017  <br/> |
|Japão  <br/> |31 de outubro de 2018  <br/> |
|Índia  <br/> |31 de outubro de 2018  <br/> |
|Canadá  <br/> |31 de outubro de 2018  <br/> |
|Coreia do Sul  <br/> |31 de outubro de 2018  <br/> |
|Reino Unido  <br/> |15 de setembro de 2019  <br/> |
|França  <br/> |15 de setembro de 2020  <br/> |
   
## <a name="moves-that-involve-a-third-party-audio-conferencing-provider"></a>Movimentações que envolvem um provedor de conferência de áudio de terceiros

- Serviços de complemento de provedor de conferência de áudio de terceiros para Skype para negócios não estão disponíveis para usuários hospedados nos novos centros de dados específicos geo. 
    
- Os clientes existentes usando um serviço de provedor de conferência de áudio de terceiros não devem solicitar uma movimentação para um novo centro de dados geo específicos. 
    
- Novos clientes implantados para os centros de dados específicos geo novo precisará solicitar uma movimentação para um centro de dados regionais para usar um provedor de conferência de áudio de terceiros. 
    
## <a name="exchange-online"></a>Exchange Online

Porque leva tempo para mover cada usuário para o novo geo datacenter para um único locatário, alguns usuários ainda estará no antigo geo datacenter durante a movimentação, enquanto outros farão parte do novo geo datacenter. Isso significa que alguns recursos que envolvem acessando várias caixas de correio totalmente não funcionarão durante um período do processo de movimentação, que pode últimas semanas. Esses recursos são descritos nas seções a seguir.
  
### <a name="mailbox-move"></a>Movimentação de caixa de correio

Quando geos de datacenter uma caixa de correio individual movimentações crosses, o conteúdo de caixa de correio é primeiramente esses transferidos para que os dados existentes são copiados para a localização geográfica de destino sem afetar a caixa de correio. No momento da transferência para o geo de destino, a caixa de correio geo a fonte estiver bloqueada por alguns minutos. Durante esse tempo, os clientes de email não podem conectar temporariamente. Alterações adicionais são copiadas para a localização geográfica de destino e a caixa de correio conclui a mudança para o geo de destino. Não há sem interromper o fluxo de email durante a movimentação.
  
Alguns usuários talvez seja necessário reiniciar a área de trabalho do Outlook depois que a caixa de correio for movida, conforme descrito no [artigo da Base de dados de Conhecimento 2591913](https://support.microsoft.com/kb/2591913).
  
### <a name="shared-mailbox"></a>Caixa de correio compartilhada

Um usuário com a permissão de "Acesso total" para caixas de correio compartilhadas não é afetado durante a movimentação.
  
### <a name="resource-mailbox"></a>Caixa de correio de recurso

Um usuário que precisa para gerenciar configurações de caixa de correio de recurso por meio da página de opções no Outlook Web Access pode continuar a fazê-lo durante a movimentação.
  
Se as caixas de correio de recurso são gerenciadas diretamente por meio de cmdlets do Exchange, os cmdlets Set-MailboxRegionalConfiguration e Set-MailboxCalendarConfiguration não funcionam se o usuário executando e a caixa de correio de recurso na geos diferentes.
  
### <a name="calendar-delegation"></a>Delegação de calendário

Livre/ocupado e o compartilhamento de calendário não são afetados durante a movimentação de locatário. O usuário A com permissão de gravação para a pasta de calendário da caixa de correio B ainda poderá gerenciar a pasta de calendário da caixa de correio B usando a área de trabalho do Outlook. No entanto, durante a movimentação, se o usuário A e B de caixa de correio não no mesmo geo, usuário não pode editar calendário da caixa de correio B no Outlook Web Access até que ambos são movidos para o geo de destino.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Abra o "Pasta compartilhada" no Outlook Web Access

Alguns usuários abrir uma pasta de email compartilhadas a partir de outra caixa de correio (que o usuário tem ler ou gravar permissões para) no Outlook Web Access usando o recurso de "Pasta compartilhada". A tabela a seguir descreve como mover o acesso a pastas compartilhadas works durante uma caixa de correio. Observe que os usuários com permissões de total para uma caixa de correio compartilhada podem abrir a caixa de correio usando o Outlook Web Access durante a movimentação. 
  
|**Configuração**|**Descrição**|
|:-----|:-----|
|Usuário tem permissão de pasta de caixa de correio para outra caixa de correio  <br/> |Possivelmente limitados.  <br/> Se o usuário A e B de caixa de correio não em geo o mesmo durante a movimentação de locatário, usuário não pode abrir a pasta de caixa de correio do B no Outlook Web Access se apenas o usuário tem permissão para uma pasta específica na b de caixa de correio.  <br/> Para adicionar uma pasta compartilhada, o nome de usuário no painel de navegação esquerdo do mouse em e selecione **Adicionar pasta compartilhada**.  <br/> |
|Usuário com permissão de caixa de correio completa para outra caixa de correio  <br/> |Totalmente suportado.  <br/> Se o usuário tem permissão de "Acesso total" b de caixa de correio, o usuário A pode clique a pasta compartilhada no painel de navegação à esquerda no Outlook Web Access para abrir uma janela mostrando b de caixa de correio.  <br/> > [!NOTE]> Um usuário pode abrir uma caixa de correio compartilhada usando o Outlook Web Access durante a movimentação sem qualquer impacto negativo. A limitação se aplica apenas a nível de pasta de compartilhamento em uma caixa de correio.           |
   
### <a name="public-folders"></a>Pastas públicas

Se a caixa de correio de pasta pública está temporariamente em geo um datacenter diferente do usuário tentar acessá-lo, o usuário não é possível acessá-lo. 
  
### <a name="online-archives"></a>Arquivos on-line

Enquanto a movimentação está em andamento, usuários que se conectam por meio do Outlook Web Access não poderão se conectar a suas caixas de correio de arquivo morto online. Acesso à caixa de correio de arquivamento para usuários conectando-se com o Outlook é suportado.
  
### <a name="ediscovery-amp-auditing"></a>descoberta eletrônica &amp; auditoria

O eDiscovery e recursos no Office 365 Security de auditoria &amp; move locatário de cross-geo de suporte do Centro de conformidade. ao contrário do Centro de administração do Exchange (EAC), que não tem suporte para consultar os usuários que ainda não foram movidos depois de mover o inquilino foi iniciado. Para obter mais informações sobre a segurança &amp; Centro de conformidade, consulte [a segurança do Office 365 &amp; Centro de conformidade](https://go.microsoft.com/fwlink/p/?linkid=841313). 
  
A tabela a seguir mostra como acessar o eDiscovery e auditoria via a segurança e a EAT &amp; Centro de conformidade.
  
||**Centro de administração do Exchange**|**Segurança &amp; Centro de conformidade**|
|:-----|:-----|:-----|
|Descoberta Eletrônica  <br/> | Vá para https://portal.office.come clique em blocos de **Admin** . <br/> Clique em **Admin centrais** \> **Exchange**. <br/> Selecione **gerenciamento de conformidade** \> **Descoberta eletrônica in-loco &amp; mantenha**. | Vá para https://portal.office.come clique em blocos de Admin. <br/> Clique em **Admin centrais** \> **segurança &amp; conformidade**. <br/> Selecione **pesquisa &amp; investigação** \> **eDiscovery**.|
|Auditoria  <br/> | Vá para https://portal.office.come clique em blocos de **Admin** . <br/> Clique em **Admin centrais** \> **Exchange**. Selecione **gerenciamento de conformidade** \> **auditoria**. | Vá para https://portal.office.come clique em blocos de Admin. <br/> Clique em **Admin centrais** \> **segurança &amp; conformidade**. <br/> Selecione **pesquisa &amp; investigação** \> **pesquisa de log de auditoria**. |
   
### <a name="mailbox-migration"></a>Migração de caixa de correio

Quando um locatário está movendo entre geos, um lote de migração pode relatar erros em alguns usuários no lote de migração que são deixados no geo a fonte. Nesse caso, remova o lote de migração existente para remover a solicitação de sincronização subjacente. Depois que o lote é totalmente limpos, crie o lote novamente, que iniciará a criação de solicitações de sincronização no geo destino.
  
## <a name="sharepoint-online"></a>SharePoint Online

Quando é movido do SharePoint Online, os dados para os seguintes serviços também serão movidos:
  
- One Drive for Business
    
- Project Online
    
- Project para Office 365
    
- Serviços de vídeo do Office 365
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro para Office 365
    
Depois que concluímos a mover os dados do SharePoint Online, talvez você veja o alguns dos seguintes efeitos.
  
### <a name="office-365-video-services"></a>Serviços de vídeo do Office 365

- Mover os dados para vídeo demora mais do que o é movido para o restante de seu conteúdo no SharePoint Online.
    
- Após o SharePoint Online conteúdo é movido, haverá um período de tempo em que os vídeos não conseguem a ser reproduzido.
    
- Podemos está removendo o codificados das transações copia do datacenter anterior e transcodificação-los novamente no novo datacenter.
    
### <a name="search"></a>Pesquisar

Durante a mover os dados do SharePoint Online, podemos migrar seu índice de pesquisa e configurações de pesquisa para um novo local. Até que podemos ter **concluído** a movimentação dos seus dados do SharePoint Online, podemos continuar atender a seus usuários a partir do índice no local original. No novo local, a pesquisa inicia automaticamente o rastreamento de seu conteúdo depois que concluímos a mover os dados do SharePoint Online. Partir dessa aponte e em diante que atendemos seus usuários do índice migrado. Alterações ao seu conteúdo que tenha ocorrido após a migração não são incluídas no índice migrado até que o rastreamento capte-los. A maioria dos clientes não Observe que os resultados são menos direita atualizada após concluímos a movimentação de seus dados do SharePoint Online, mas alguns clientes podem sofrer uma redução de atualização nas primeira 24-48 horas 
  
Os seguintes recursos de pesquisa são afetados:
  
- Web Parts de pesquisa e de resultados de pesquisa: resultados não incluem alterações que tenham ocorrido após a migração, até que o rastreamento capte-los. 
    
- Me aprofundar: Me aprofundar não inclui as alterações que tenham ocorrido após a migração, até que o rastreamento capte-los.
    
- Relatórios de pesquisa para o site e popularidade: contagens de relatórios do Excel no novo local incluem apenas contagens migradas e a conta de relatórios de uso tem executado uma vez concluída, movendo os dados do SharePoint Online. Qualquer contagens do período provisório são perdidas e não podem ser recuperadas. Normalmente, esse período é dois dias. Alguns clientes podem sofrer perdas ou mais curtos.
    
- Portal de vídeo: Contagens e estatísticas para o Portal de vídeo dependem as estatísticas para o Portal de vídeo e de estatísticas de relatórios do Excel, para que exibir as contagens de modo de exibição são perdidas no mesmo período de tempo para os relatórios do Excel.
    
- descoberta eletrônica: itens alterados durante a migração não são exibidos até rastreamento selecionará as alterações.
    
- Proteção de perda de dados (DLP): Políticas não são impostas itens alterados enquanto seleciona rastrear as alterações.
    
## <a name="skype-for-business"></a>Skype for Business

Todos os usuários serão desconectados do Skype para o software de cliente de negócios durante a migração. A entrada automática no serão reconectados usuários dentro de dois minutos.
  
|**Recursos que funcionam durante a movimentação inteira**|**Recursos que podem ser limitados durante uma parte da movimentação**|
|:-----|:-----|
| Chamadas de voz e de mensagens instantâneas  <br/>  Os usuários podem adicionar contatos, adicionar grupos de contatos, adicionar reuniões, defina seu local e alterar "Que está acontecendo hoje".  <br/>  Configurações do provedor de conferência (ACP) de áudio são copiadas para o destino datacenter geo. Se o provedor de ACP estiver presente no datacenter destino, que ela funcione. Caso contrário, ele não será.  <br/> | Locatário Admin TRPS (inquilino o PowerShell remoto) não estará disponível aos administradores criar sessões.  <br/>  Administrador de locatários LAC não estará disponível para os administradores entrar e alterar configurações do usuário.  <br/> |
   
|**Após a migração**|
|:-----|
| Dados da reunião (apresentações carregadas, etc.) não serão transferidos e deverá ser carregado novamente.  <br/>  Os clientes mais antigos do Lync, como o cliente do Lync 2010 e Lync para Mac 2011 cliente, são conhecidos como informações de DNS para o serviço causando problemas de login do cache. Limpeza do cache DNS pode ser necessário se o usuário não é o mais recente Skype para cliente Windows de negócios. Peça aos usuários para executar o [Assistente de solução de problemas](https://support.microsoft.com/en-us/kb/2541980) e siga as instruções sobre como limpar o cache do cliente. Lync para os usuários do Mac cliente deve seguir [estas instruções](https://support.microsoft.com/en-us/kb/2629861).<br/> |
   
## <a name="data-for-other-services-including-yammer-and-power-bi"></a>Dados de outros serviços, inclusive o Yammer e no Power BI

Podemos só mover dados do cliente para o Exchange Online, SharePoint Online e Skype para negócios. Nós não mover dados para outros serviços. Não há nenhuma alteração ou impacto para você, como um cliente ou usuário desses outros serviços. O processo de movimentação não influenciam-los e a localização dos seus dados de cliente permanecerá inalterada.
  
## <a name="related-topics"></a>Tópicos relacionados 
 
[Como solicitar a migração dos dados](request-your-data-move.md)
    
[Perguntas frequentes gerais sobre migração de dados](data-move-faq.md)
  
[Novo geos datacenter para o Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Serviços do Azure por região](https://azure.microsoft.com/en-us/regions/)

