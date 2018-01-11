---
title: "Adicionar um domínio a uma locação do cliente com o Windows PowerShell para parceiros com permissão de acesso delegado (DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "Resumo: Use o Windows PowerShell para o Office 365 para adicionar um nome de domínio alternativo a um locatário existente do cliente."
ms.openlocfilehash: f99039ffa9f921b33829767a08f33db500a5d2ed
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="05022-103">Adicionar um domínio a uma locação do cliente com o Windows PowerShell para parceiros com permissão de acesso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="05022-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="05022-104">**Resumo:** use o Windows PowerShell para o Office 365 para adicionar um nome de domínio alternativo a um locatário existente do cliente.</span><span class="sxs-lookup"><span data-stu-id="05022-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="05022-105">Você pode criar e associar novos domínios à locação do cliente com o Windows PowerShell para o Office 365 mais rápido do que usar o Centro de administração do Office 365.</span><span class="sxs-lookup"><span data-stu-id="05022-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Office 365 admin center.</span></span>
  
<span data-ttu-id="05022-p101">Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas do Office 365 em suas ofertas de serviço aos seus clientes. Quando eles vendem uma assinatura do Office 365, recebem automaticamente permissões de Administrar Em Nome de (AOBO) para aslocações de cliente para que possam administrar e relatar todas as suas locações de cliente.</span><span class="sxs-lookup"><span data-stu-id="05022-p101">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="05022-110">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="05022-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="05022-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span><span class="sxs-lookup"><span data-stu-id="05022-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span></span>
  
<span data-ttu-id="05022-112">Você também precisará das seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="05022-112">You also need the following information:</span></span>
  
- <span data-ttu-id="05022-113">É necessário o nome de domínio totalmente qualificado (FQDN) escolhido pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="05022-113">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="05022-114">É necessária a **TenantId** do cliente.</span><span class="sxs-lookup"><span data-stu-id="05022-114">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="05022-p102">O FQDN deve ser registrado com um registrador de Serviço de Nomes de Domínio da Internet (DNS), como o GoDaddy. Para saber mais sobre como registrar publicamente um nome de domínio, confira [Como comprar um nome de domínio](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="05022-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="05022-p103">Você precisa saber como adicionar um registro TXT à zona DNS registrada do seu registrador de DNS. Para saber mais sobre como adicionar um registro TXT, confira [Criar registros DNS em qualquer provedor de host DNS para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se esses procedimentos não funcionarem, localize os procedimentos do seu registrador de DNS.</span><span class="sxs-lookup"><span data-stu-id="05022-p103">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="05022-120">Criar domínios</span><span class="sxs-lookup"><span data-stu-id="05022-120">Create domains</span></span>

 <span data-ttu-id="05022-p104">Os clientes provavelmente vão solicitar a criação de domínios adicionais para associar às suas locações, uma vez que não pretendem ter o<domínio>.onmicrosoft.compadrão como o domínio principal que representa sua identidade corporativa mundialmente. Este procedimento lhe orienta na criação de um novo domínio associado à locação do cliente.</span><span class="sxs-lookup"><span data-stu-id="05022-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="05022-p105">Para realizar algumas dessas operações, a conta de administrador do parceiro com a qual você entrar deve ser definida como **Administração total** para a configuração **Atribuir acesso administrativo a empresas às quais você oferece suporte** encontrada nos detalhes da conta do administrador no Centro de administração do Office 365. Para saber mais informações sobre como gerenciar funções de administrador de parceiro, confira[Parceiros: Oferecer administração delegada](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="05022-p105">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Office 365 admin center. For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="05022-125">Criar o domínio no Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="05022-125">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="05022-p106">Esse comando cria o domínio no Azure Active Directory, mas não o associa ao domínio registrado publicamente. Isso ocorre quando você comprova a propriedade do domínio registrado publicamente para o Microsoft Office 365 para empresas.</span><span class="sxs-lookup"><span data-stu-id="05022-p106">This command creates the domain in Azure Active Directory but does not associate it with the publically registered domain. That comes when you prove that you own the publically registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="05022-128">Obter os dados do registro de verificação TXT de DNS</span><span class="sxs-lookup"><span data-stu-id="05022-128">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="05022-p107">O Office 365 gerará os dados específicos necessários para você colocar no registro de verificação TXT de DNS. Para obter os dados, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="05022-p107">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="05022-131">Isso lhe dará saída como:</span><span class="sxs-lookup"><span data-stu-id="05022-131">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="05022-p108">Você vai precisar desse texto para criar o registro TXT na zona DNS registrada publicamente. Não deixe de copiá-lo e salvá-lo.</span><span class="sxs-lookup"><span data-stu-id="05022-p108">You will need this text to create the TXT record in the publically registered DNS zone. Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="05022-134">Adicionar um registro TXT à zona DNS registrada publicamente</span><span class="sxs-lookup"><span data-stu-id="05022-134">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="05022-p109">Antes que o Office 365 comece a aceitar tráfego direcionado para o nome de domínio registrado publicamente, você deve comprovar a propriedade e ter permissões de administrador do domínio. Para provar que é o proprietário, crie um registro TXT no domínio. O registro TXT não tem nenhuma utilidade no domínio. Você pode exclui-lo após comprovar sua propriedade. Para criar os registros TXT, siga os procedimentos do artigo [Criar registros DNS em qualquer provedor de host DNS para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se esses procedimentos não funcionarem, localize os procedimentos do seu registrador de DNS.</span><span class="sxs-lookup"><span data-stu-id="05022-p109">Before Office 365 will start accepting traffic that is directed to the publically registered domain name, you must prove that you own and have administrator permissions to the domain. You prove you own the domain by creating a TXT record in the domain. A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established. To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="05022-p110">Confirme a criação bem-sucedida do registro TXT por meio do nslookup. Execute a seguinte sintaxe.</span><span class="sxs-lookup"><span data-stu-id="05022-p110">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="05022-142">Isso lhe dará saída como:</span><span class="sxs-lookup"><span data-stu-id="05022-142">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="05022-143">Validar a propriedade do domínio no Office 365</span><span class="sxs-lookup"><span data-stu-id="05022-143">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="05022-p111">Nesta última etapa, você comprovou ao Office 365 que é proprietário do domínio registrado publicamente. Após essa etapa, o Office 365 começará a aceitar tráfego roteado para o novo nome de domínio. Para concluir a criação do domínio e o processo de registro, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="05022-p111">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="05022-147">Este comando não retornará nenhuma saída; portanto, para confirmar se ele funcionou, execute-o.</span><span class="sxs-lookup"><span data-stu-id="05022-147">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="05022-148">Isso retornará algo parecido com o seguinte</span><span class="sxs-lookup"><span data-stu-id="05022-148">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="05022-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="05022-149">See also</span></span>

#### 

[<span data-ttu-id="05022-150">Ajuda para parceiros</span><span class="sxs-lookup"><span data-stu-id="05022-150">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

