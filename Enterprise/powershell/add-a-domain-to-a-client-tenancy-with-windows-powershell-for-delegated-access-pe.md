---
title: Adicionar um domínio a uma locação do cliente com o Windows PowerShell para parceiros com permissão de acesso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Resumo: Use o Windows PowerShell para o Office 365 para adicionar um nome de domínio alternativo a um locatário existente do cliente.'
ms.openlocfilehash: 5f22e21e1eafc7c2d3fb9bc7286e860ad468445b
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257460"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Adicionar um domínio a uma locação do cliente com o Windows PowerShell para parceiros com permissão de acesso delegado (DAP)

 **Resumo:** use o Windows PowerShell para o Office 365 para adicionar um nome de domínio alternativo a um locatário existente do cliente.
  
Você pode criar e associar novos domínios à locação do cliente com o Windows PowerShell para o Office 365 mais rápido do que usar o Centro de administração do Microsoft 365.
  
Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas do Office 365 em suas ofertas de serviço aos seus clientes. Quando eles vendem uma assinatura do Office 365, recebem automaticamente permissões de Administrar Em Nome de (AOBO) para as locações de cliente para que possam administrar e relatar todas as suas locações de cliente.
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

Os procedimentos neste tópico exigem que você se conecte ao Windows PowerShell para Office 365. Para obter instruções, veja [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
  
Você também precisa ter as credenciais de administrador de locatários do parceiro.
  
Você também precisará das seguintes informações:
  
- É necessário o nome de domínio totalmente qualificado (FQDN) escolhido pelo cliente.
    
- É necessária a **TenantId** do cliente.
    
- O FQDN deve ser registrado com um registrador de Serviço de Nomes de Domínio da Internet (DNS), como o GoDaddy. Para saber mais sobre como registrar publicamente um nome de domínio, confira [Como comprar um nome de domínio](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- Você precisa saber como adicionar um registro TXT à zona DNS registrada do seu registrador de DNS. Para saber mais sobre como adicionar um registro TXT, confira [Criar registros DNS em qualquer provedor de host DNS para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se esses procedimentos não funcionarem, localize os procedimentos do seu registrador de DNS.
    
## <a name="create-domains"></a>Criar domínios

 Os clientes provavelmente vão solicitar a criação de domínios adicionais para associar às suas locações, uma vez que não pretendem ter o<domínio>.onmicrosoft.compadrão como o domínio principal que representa sua identidade corporativa mundialmente. Este procedimento lhe orienta na criação de um novo domínio associado à locação do cliente.
  
> [!NOTE]
> Para realizar algumas dessas operações, a conta de administrador de parceiros que você faz logon deve ser definida como **Administração completa** para a configuração **atribuir acesso administrativo às empresas às quais você dá suporte,** localizada nos detalhes da conta de administrador no centro de administração do Microsoft 365. Para obter mais informações sobre o gerenciamento de funções de administrador de parceiros, consulte[parceiros: oferecer administração delegada](https://go.microsoft.com/fwlink/p/?LinkId=532435). 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Criar o domínio no Azure Active Directory

Esse comando cria o domínio no Azure Active Directory, mas não o associa ao domínio registrado publicamente. Isso ocorre quando você prova que possui o domínio registrado publicamente ao Microsoft Office 365 para empresas.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
>O PowerShell Core não é compatível com o módulo Microsoft Azure Active Directory para o módulo e cmdlets do Windows PowerShell com o **MSol** em seu nome. Para continuar usando esses cmdlets, você deve executá-los do Windows PowerShell.
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Obter os dados do registro de verificação TXT de DNS

 O Office 365 gerará os dados específicos necessários para você colocar no registro de verificação TXT de DNS. Para obter os dados, execute o seguinte comando.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Isso lhe dará saída como:
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> Você vai precisar desse texto para criar o registro TXT na zona DNS registrada publicamente. Não deixe de copiá-lo e salvá-lo. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Adicionar um registro TXT à zona DNS registrada publicamente

Para que o Office 365 comece a aceitar o tráfego direcionado ao nome de domínio registrado publicamente, você deve provar que possui e tem permissões de administrador para o domínio. Para provar que você é o proprietário do domínio, crie um registro TXT nele. Um registro TXT não altera nada em seu domínio e pode ser excluído depois que for provado que você possui o domínio. Para criar registros TXT, siga os procedimentos de [Criar registros DNS em qualquer provedor de hospedagem de DNS do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Caso esses procedimentos não funcionem, localize os procedimentos do seu registrador de DNS.
  
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
   
## <a name="see-also"></a>Confira também

#### 

[Ajuda para parceiros](https://go.microsoft.com/fwlink/p/?LinkID=533477)

