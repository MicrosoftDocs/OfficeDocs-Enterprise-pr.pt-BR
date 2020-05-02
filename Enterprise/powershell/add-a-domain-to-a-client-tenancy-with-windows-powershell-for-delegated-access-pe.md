---
title: Adicionar um domínio a uma locação do cliente com o Windows PowerShell para parceiros com permissão de acesso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Resumo: Use o Windows PowerShell para o Office 365 para adicionar um nome de domínio alternativo a um locatário existente do cliente.'
ms.openlocfilehash: 693dbc22fea27c24fb6b578e22d0d2b150a8dfd5
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004744"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="86d09-103">Adicionar um domínio a uma locação do cliente com o Windows PowerShell para parceiros com permissão de acesso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="86d09-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="86d09-104">**Resumo:** use o Windows PowerShell para o Office 365 para adicionar um nome de domínio alternativo a um locatário existente do cliente.</span><span class="sxs-lookup"><span data-stu-id="86d09-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="86d09-105">Você pode criar e associar novos domínios à locação do cliente com o Windows PowerShell para o Office 365 mais rápido do que usar o Centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="86d09-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="86d09-106">Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP).</span><span class="sxs-lookup"><span data-stu-id="86d09-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="86d09-107">Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas.</span><span class="sxs-lookup"><span data-stu-id="86d09-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="86d09-108">Eles reúnem assinaturas do Office 365 em suas ofertas de serviço aos seus clientes.</span><span class="sxs-lookup"><span data-stu-id="86d09-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="86d09-109">Quando eles vendem uma assinatura do Office 365, recebem automaticamente permissões de Administrar Em Nome de (AOBO) para as locações de cliente para que possam administrar e relatar todas as suas locações de cliente.</span><span class="sxs-lookup"><span data-stu-id="86d09-109">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="86d09-110">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="86d09-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="86d09-p102">Os procedimentos neste tópico exigem que você se conecte ao Windows PowerShell para Office 365. Para obter instruções, veja [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="86d09-p102">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="86d09-113">Você também precisa ter as credenciais de administrador de locatários do parceiro.</span><span class="sxs-lookup"><span data-stu-id="86d09-113">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="86d09-114">Você também precisará das seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="86d09-114">You also need the following information:</span></span>
  
- <span data-ttu-id="86d09-115">É necessário o nome de domínio totalmente qualificado (FQDN) escolhido pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="86d09-115">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="86d09-116">É necessária a **TenantId** do cliente.</span><span class="sxs-lookup"><span data-stu-id="86d09-116">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="86d09-p103">O FQDN deve ser registrado com um registrador de Serviço de Nomes de Domínio da Internet (DNS), como o GoDaddy. Para saber mais sobre como registrar publicamente um nome de domínio, confira [Como comprar um nome de domínio](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="86d09-p103">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="86d09-p104">Você precisa saber como adicionar um registro TXT à zona DNS registrada do seu registrador de DNS. Para saber mais sobre como adicionar um registro TXT, confira [Criar registros DNS em qualquer provedor de host DNS para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se esses procedimentos não funcionarem, localize os procedimentos do seu registrador de DNS.</span><span class="sxs-lookup"><span data-stu-id="86d09-p104">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="86d09-122">Criar domínios</span><span class="sxs-lookup"><span data-stu-id="86d09-122">Create domains</span></span>

 <span data-ttu-id="86d09-p105">Os clientes provavelmente vão solicitar a criação de domínios adicionais para associar às suas locações, uma vez que não pretendem ter o<domínio>.onmicrosoft.compadrão como o domínio principal que representa sua identidade corporativa mundialmente. Este procedimento lhe orienta na criação de um novo domínio associado à locação do cliente.</span><span class="sxs-lookup"><span data-stu-id="86d09-p105">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="86d09-125">Para realizar algumas dessas operações, a conta de administrador de parceiros que você faz logon deve ser definida como **Administração completa** para a configuração **atribuir acesso administrativo às empresas às quais você dá suporte,** localizada nos detalhes da conta de administrador no centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="86d09-125">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="86d09-126">Para obter mais informações sobre o gerenciamento de funções de administrador de parceiros, consulte[parceiros: oferecer administração delegada](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="86d09-126">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="86d09-127">Criar o domínio no Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="86d09-127">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="86d09-128">Esse comando cria o domínio no Azure Active Directory, mas não o associa ao domínio registrado publicamente.</span><span class="sxs-lookup"><span data-stu-id="86d09-128">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="86d09-129">Isso ocorre quando você prova que possui o domínio registrado publicamente ao Microsoft Office 365 para empresas.</span><span class="sxs-lookup"><span data-stu-id="86d09-129">That comes when you prove that you own the publicly registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="86d09-130">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="86d09-130">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="86d09-131">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86d09-131">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="86d09-132">Obter os dados do registro de verificação TXT de DNS</span><span class="sxs-lookup"><span data-stu-id="86d09-132">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="86d09-p109">O Office 365 gerará os dados específicos necessários para você colocar no registro de verificação TXT de DNS. Para obter os dados, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="86d09-p109">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="86d09-135">Isso lhe dará saída como:</span><span class="sxs-lookup"><span data-stu-id="86d09-135">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="86d09-136">Você vai precisar desse texto para criar o registro TXT na zona DNS registrada publicamente.</span><span class="sxs-lookup"><span data-stu-id="86d09-136">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="86d09-137">Não deixe de copiá-lo e salvá-lo.</span><span class="sxs-lookup"><span data-stu-id="86d09-137">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="86d09-138">Adicionar um registro TXT à zona DNS registrada publicamente</span><span class="sxs-lookup"><span data-stu-id="86d09-138">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="86d09-139">Para que o Office 365 comece a aceitar o tráfego direcionado ao nome de domínio registrado publicamente, você deve provar que possui e tem permissões de administrador para o domínio.</span><span class="sxs-lookup"><span data-stu-id="86d09-139">Before Office 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="86d09-140">Para provar que você é o proprietário do domínio, crie um registro TXT nele.</span><span class="sxs-lookup"><span data-stu-id="86d09-140">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="86d09-141">Um registro TXT não altera nada em seu domínio e pode ser excluído depois que for provado que você possui o domínio.</span><span class="sxs-lookup"><span data-stu-id="86d09-141">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="86d09-142">Para criar registros TXT, siga os procedimentos de [Criar registros DNS em qualquer provedor de hospedagem de DNS do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="86d09-142">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="86d09-143">Caso esses procedimentos não funcionem, localize os procedimentos do seu registrador de DNS.</span><span class="sxs-lookup"><span data-stu-id="86d09-143">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="86d09-p112">Confirme a criação bem-sucedida do registro TXT por meio do nslookup. Execute a seguinte sintaxe.</span><span class="sxs-lookup"><span data-stu-id="86d09-p112">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="86d09-146">Isso lhe dará saída como:</span><span class="sxs-lookup"><span data-stu-id="86d09-146">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="86d09-147">Validar a propriedade do domínio no Office 365</span><span class="sxs-lookup"><span data-stu-id="86d09-147">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="86d09-p113">Nesta última etapa, você comprovou ao Office 365 que é proprietário do domínio registrado publicamente. Após essa etapa, o Office 365 começará a aceitar tráfego roteado para o novo nome de domínio. Para concluir a criação do domínio e o processo de registro, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="86d09-p113">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="86d09-151">Este comando não retornará nenhuma saída; portanto, para confirmar se ele funcionou, execute-o.</span><span class="sxs-lookup"><span data-stu-id="86d09-151">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="86d09-152">Isso retornará algo parecido com o seguinte</span><span class="sxs-lookup"><span data-stu-id="86d09-152">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="86d09-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="86d09-153">See also</span></span>

#### 

[<span data-ttu-id="86d09-154">Ajuda para parceiros</span><span class="sxs-lookup"><span data-stu-id="86d09-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

