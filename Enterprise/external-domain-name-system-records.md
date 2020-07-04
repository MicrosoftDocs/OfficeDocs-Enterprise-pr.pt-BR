---
title: Registros de Sistema de Nomes de Domínio Externos para o Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: 'Resumo: lista de referências de registros DNS a serem usados ao planejar uma implantação do Office 365.'
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996535"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Registros de Sistema de Nomes de Domínio Externos para o Office 365

|||
|:-----|:-----|
|![Domínio](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> **Volte para o** [Planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Registros DNS externos exigidos para o Office 365 (serviços essenciais)
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Objetivo** <br/> |**Valor a ser usado** <br/> |
|**CNAME** <br/> **(Suite)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **Observação:** Este CNAME só se aplica ao Office 365 operado pela 21Vianet.   |**Alias:** msoid  <br/> **Destino:** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Verificação de domínio)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**Host:** @ (ou, para alguns provedores de hospedagem DNS, o nome do seu domínio)  <br/> **Valor do TXT:** _uma cadeia de texto fornecida pelo_ Office 365  <br/> O **assistente de configuração de domínio** do Office 365 fornece os valores usados para criar esse recurso.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Registros DNS externos exigidos para email no Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **O registro de Descoberta Automática** permite que os computadores clientes encontrem o Exchange automaticamente e configurem o cliente corretamente.

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
Você só quer migrar alguns endereços de email para o Office 365? Você pode [Coordenar o Office 365 com alguns endereços de email em seu domínio personalizado](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **O registro TXT para SPF** é usado por sistemas de email do destinatário para validar se o servidor que envia seu email é aquele que você aprova. Isso ajuda a evitar problemas como a falsificação e o phishing de emails. Consulte os [Registros DNS externos necessários para SPF](external-domain-name-system-records.md#BKMK_SPFrecords) neste artigo para ajudá-lo a entender o que incluir em seu registro.

Os clientes de email que estão usando a Federação do Exchange também terão um registro CNAME e TXT adicional listado no final da tabela.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Objetivo** <br/> |**Valor a ser usado** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**Alias:** descoberta automática  <br/> **Destino:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Envia emails de entrada de seu domínio para o serviço Exchange Online no Office 365.  <br/> [!NOTE] Quando os emails estão sendo enviados para o Exchange Online, você deve remover os registros MX que apontam para o sistema antigo.   |**Domínio:** por exemplo, contoso.com  <br/> **Servidor de email de destino:** \<MX token\> . mail.protection.outlook.com  <br/> **Preferência/Prioridade:** menor do que outros registros MX (isso garante que o email seja entregue ao Exchange Online), por exemplo, 1 ou “baixa”  <br/>  Encontre seu seguindo \<MX token\> estas etapas:  <br/>  Entre no Office 365, vá para o administrador do Office 365 \>Domínios.  <br/>  Na coluna Ação de seu domínio, escolha Corrigir problemas.  <br/>  Na seção de registros MX, escolha O que corrigir?  <br/>  Siga as instruções nesta página para atualizar seu registro MX.  <br/> [O que é prioridade MX?](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[Registros DNS externos necessários para SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Federação do Exchange)** <br/> |Usado na federação do Exchange para implantação híbrida.  <br/> |**Registro TXT 1:** por exemplo, contoso.com e um texto de hash associado, gerado de forma personalizada e à prova de domínio (por exemplo, Y96nu89138789315669824)  <br/> **Registro TXT 2:** por exemplo, exchangedelegation.contoso.com e um texto de hash associado gerado de forma personalizada e à prova de domínio (por exemplo, Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Federação do Exchange)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**Alias:** por exemplo, Autodiscover.service.contoso.com  <br/> **Destino:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Registros DNS externos necessários para o Skype for Business Online
<a name="BKMK_ReqdCore"> </a>

Há etapas específicas a serem seguidas quando você usa [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) para garantir que sua rede esteja configurada corretamente.

> [!NOTE]
> Esses registros DNS também se aplicam ao Teams, especialmente em um cenário híbrido do Teams e do Skype for Business Online, onde podem surgir certos problemas de federação.
  
||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Objetivo** <br/> |**Valor a ser usado** <br/> |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Serviço:** sipfederationtls  <br/> **Protocolo:** TCP  <br/> **Priority:** 100  <br/> **Peso:** 1  <br/> **Porta:** 5061  <br/> **Destino:** sipfed.online.lync.com  <br/> **Observação:** Se o firewall ou o servidor proxy bloquearem pesquisas SRV em um DNS externo, você deverá adicionar esse registro ao registro DNS interno.   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Usado pelo Skype for Business para coordenar o fluxo de informações entre clientes do Lync.  <br/> |**Serviço:** sip  <br/> **Protocolo:** TLS  <br/> **Priority:** 100  <br/> **Peso:** 1  <br/> **Porta:** 443  <br/> **Destino:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Usado pelo cliente do Lync para ajudar a localizar o serviço do Skype for Business Online e entrar.  <br/> |**Alias:** sip  <br/> **Destino:** sipdir.online.lync.com  <br/> Para obter mais informações, confira [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Usado pelo cliente móvel do Lync para ajudar a localizar o serviço do Skype for Business Online e entrar.  <br/> |**Alias:** lyncdiscover  <br/> **Destino:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Registros DNS externos exigidos para Acesso por Logon Único ao Office 365
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**Registro DNS** <br/> |**Objetivo** <br/> |**Valor a ser usado** <br/> |
|**Host (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**Destino:** por exemplo, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Registros DNS externos necessários para SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>Estrutura de um registro SPF

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Um sistema de emails que recebe um email do seu domínio analisa o registro SPF. Se o servidor de email que enviou a mensagem era um servidor do Office 365, a mensagem é aceita. Se o servidor que enviou a mensagem era o seu antigo sistema de emails ou um sistema mal-intencionado na Internet, por exemplo, a verificação de SPF pode falhar, e a mensagem não ser enviada. Verificações como esta ajudam a evitar mensagens de falsificação e phishing.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Escolha a estrutura de registro de SPF que precisar

Para cenários em que você não está usando apenas o email do Exchange Online no Office 365 (por exemplo, quando você também usa o email proveniente do SharePoint Online), use a tabela a seguir para determinar o que incluir no valor do registro.
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||Se você estiver usando...  <br/> |Finalidade  <br/> |Adicionar isso inclui  <br/> |
|1   <br/> |Todos os sistemas de email (obrigatório)  <br/> |Todos os registros SPF começam com esse valor  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online (comum)  <br/> |Usar apenas com o Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |Sistema de email de terceiros (menos comum)  <br/> ||include:\<email system like mail.contoso.com\>  <br/> |
|4   <br/> |Sistema de email local (menos comum)  <br/> |Usar se você estiver usando o Exchange Online Protection ou o Exchange Online e outro sistema de email  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> include:\<mail.contoso.com\>  <br/> O valor entre colchetes (\<\>) deve ser outros sistemas de email que enviarão emails para seu domínio.  <br/> |
|5   <br/> |Todos os sistemas de email (obrigatório)  <br/> ||-tudo  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Exemplo: adicionar a um registro SPF existente
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Agora, você está atualizando o registro SPF do Office 365. Você editará o registro atual para ter um registro SPF que inclua os valores necessários. Para o Office 365, "spf.protection.outlook.com".
  
Correto:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Incorreto:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Mais exemplos de valores de SPF comuns
<a name="bkmk_addtospf"> </a>

Se você estiver usando o pacote completo do Office 365 e estiver usando o MailChimp para enviar emails de marketing em seu nome, seu registro SPF em contoso.com poderá ser semelhante ao seguinte, que usa as linhas 1, 3 e 5 da tabela acima. Lembre-se de que as linhas 1 e 5 são obrigatórias.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Como alternativa, se você tiver uma configuração híbrida do Exchange na qual o email é enviado do Office 365 e também do seu sistema de email local, seu registro SPF em contoso.com pode ser assim:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
Aqui está um link curto que você pode usar para voltar: [https://aka.ms/o365edns](https://aka.ms/o365edns)
