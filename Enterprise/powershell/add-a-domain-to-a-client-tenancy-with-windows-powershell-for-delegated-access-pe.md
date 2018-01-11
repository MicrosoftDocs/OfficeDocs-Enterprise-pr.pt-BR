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
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Adicionar um domínio a uma locação do cliente com o Windows PowerShell para parceiros com permissão de acesso delegado (DAP)

 **Resumo:** use o Windows PowerShell para o Office 365 para adicionar um nome de domínio alternativo a um locatário existente do cliente.
  
Você pode criar e associar novos domínios à locação do cliente com o Windows PowerShell para o Office 365 mais rápido do que usar o Centro de administração do Office 365.
  
Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas do Office 365 em suas ofertas de serviço aos seus clientes. Quando eles vendem uma assinatura do Office 365, recebem automaticamente permissões de Administrar Em Nome de (AOBO) para aslocações de cliente para que possam administrar e relatar todas as suas locações de cliente.
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)
  
Você também precisará das seguintes informações:
  
- É necessário o nome de domínio totalmente qualificado (FQDN) escolhido pelo cliente.
    
- É necessária a **TenantId** do cliente.
    
- O FQDN deve ser registrado com um registrador de Serviço de Nomes de Domínio da Internet (DNS), como o GoDaddy. Para saber mais sobre como registrar publicamente um nome de domínio, confira [Como comprar um nome de domínio](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- Você precisa saber como adicionar um registro TXT à zona DNS registrada do seu registrador de DNS. Para saber mais sobre como adicionar um registro TXT, confira [Criar registros DNS em qualquer provedor de host DNS para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se esses procedimentos não funcionarem, localize os procedimentos do seu registrador de DNS.
    
## <a name="create-domains"></a>Criar domínios

 Os clientes provavelmente vão solicitar a criação de domínios adicionais para associar às suas locações, uma vez que não pretendem ter o<domínio>.onmicrosoft.compadrão como o domínio principal que representa sua identidade corporativa mundialmente. Este procedimento lhe orienta na criação de um novo domínio associado à locação do cliente.
  
> [!NOTE]
> Para realizar algumas dessas operações, a conta de administrador do parceiro com a qual você entrar deve ser definida como **Administração total** para a configuração **Atribuir acesso administrativo a empresas às quais você oferece suporte** encontrada nos detalhes da conta do administrador no Centro de administração do Office 365. Para saber mais informações sobre como gerenciar funções de administrador de parceiro, confira[Parceiros: Oferecer administração delegada](https://go.microsoft.com/fwlink/p/?LinkId=532435). 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Criar o domínio no Azure Active Directory

Esse comando cria o domínio no Azure Active Directory, mas não o associa ao domínio registrado publicamente. Isso ocorre quando você comprova a propriedade do domínio registrado publicamente para o Microsoft Office 365 para empresas.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Obter os dados do registro de verificação TXT de DNS

 O Office 365 gerará os dados específicos necessários para você colocar no registro de verificação TXT de DNS. Para obter os dados, execute o seguinte comando.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Isso lhe dará saída como:
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> Você vai precisar desse texto para criar o registro TXT na zona DNS registrada publicamente. Não deixe de copiá-lo e salvá-lo. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Adicionar um registro TXT à zona DNS registrada publicamente

Antes que o Office 365 comece a aceitar tráfego direcionado para o nome de domínio registrado publicamente, você deve comprovar a propriedade e ter permissões de administrador do domínio. Para provar que é o proprietário, crie um registro TXT no domínio. O registro TXT não tem nenhuma utilidade no domínio. Você pode exclui-lo após comprovar sua propriedade. Para criar os registros TXT, siga os procedimentos do artigo [Criar registros DNS em qualquer provedor de host DNS para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se esses procedimentos não funcionarem, localize os procedimentos do seu registrador de DNS.
  
Confirme a criação bem-sucedida do registro TXT por meio do nslookup. Execute a seguinte sintaxe.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

Isso lhe dará saída como:
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a>Validar a propriedade do domínio no Office 365

Nesta última etapa, você comprovou ao Office 365 que é proprietário do domínio registrado publicamente. Após essa etapa, o Office 365 começará a aceitar tráfego roteado para o novo nome de domínio. Para concluir a criação do domínio e o processo de registro, execute o seguinte comando. 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Este comando não retornará nenhuma saída; portanto, para confirmar se ele funcionou, execute-o.
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Isso retornará algo parecido com o seguinte
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>Veja também

#### 

[Ajuda para parceiros](https://go.microsoft.com/fwlink/p/?LinkID=533477)

