---
title: Identidade para a Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "Resumo: Entenda como Contoso aproveita IDaaS e fornece geograficamente distribuída e autenticação redundante para seus usuários."
ms.openlocfilehash: a0de29ac7e73216e04fe02c680f2557e9f402883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="identity-for-the-contoso-corporation"></a>Identidade para a Contoso Corporation

 **Resumo:** Compreenda como a Contoso aproveita IDaaS e fornece geograficamente distribuída e autenticação redundante para seus usuários.
  
A Microsoft fornece uma identidade como um serviço (IDaaS) entre suas ofertas de nuvem. Para adotar uma infra-estrutura inclusive de nuvem, solução de IDaaS da Contoso deve aproveitar o seu provedor de identidade no local e incluir autenticação federada com seus provedores de identidade confiável, de terceiros existente.
  
## <a name="contosos-windows-server-ad-forest"></a>Floresta do Windows Server AD da Contoso

A Contoso usa uma única floresta do Windows Server Active Directory (AD) para contoso.com com sete domínios, um para cada região do mundo. As matrizes, escritórios regionais hub e escritórios satélite contêm controladores de domínio para autenticação e autorização.
  
**Figura 1: Da Contoso floresta e domínios em todo o mundo**

![Floresta e domínios do AD do Windows Server da Contoso em todo o mundo](images/Contoso_Poster/Contoso_WW_ID.png)
  
A Figura 1 mostra a floresta Contoso com domínios regionais para as diferentes partes do mundo que contêm os hubs regionais.
  
A Contoso deseja usar as contas e grupos na floresta contoso.com para autenticação e autorização para seus aplicativos baseados em nuvem e cargas de trabalho.
  
## <a name="contosos-federated-authentication-infrastructure"></a>Infraestrutura de autenticação federada da Contoso

Permite que a Contoso:
  
- Clientes usem suas contas do Microsoft, Facebook ou Google Mail para entrar no seu site público.
    
- Parceiros e fornecedores usem suas contas LinkedIn, a equipe de vendas ou Google Mail para entrar no parceiro de extranet.
    
**Figura 2: Suporte da Contoso autenticação federada para clientes e parceiros**

![Infraestrutura da Contoso para dar suporte à autenticação federada para clientes e parceiros](images/Contoso_Poster/Federated_ID.png)
  
A Figura 2 mostra DMZ Contoso contendo um site público, um parceiro extranet e um conjunto de servidores do AD FS. DMZ está conectado à Internet que contém a clientes e parceiros e serviços de Internet.
  
Servidores de Active Directory Federation Services (AD FS) na DMZ autenticam credenciais de clientes para acessar o site público e credenciais de parceiro para acesso a extranet de parceiros.
  
Quando seu site público um Azure Web App e o parceiro extranet do Dynamics 365 transições de Contoso, eles querem continuar a usar esses provedores de identidade de terceiros para seus clientes e parceiros. Isso será realizado configurando federação entre locatários Contoso Azure AD e esses provedores de identidade de terceiros.
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a>Sincronização de diretórios para a floresta do Windows Server AD da Contoso

A Contoso implantou a ferramenta conectar do Azure AD em um cluster de servidores no seu datacenter Paris. Connect do Azure AD sincroniza as alterações para a floresta do Windows Server AD contoso.com com o locatário do Azure AD compartilhado pelo Office 365 da Contoso, EMS, Dynamics 365 e assinaturas do Azure. Para obter mais informações sobre inquilinos, contas de usuário, licenças e assinaturas, consulte [assinaturas, licenças e contas de usuário para a Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).
  
**Figura 3: Infra-estrutura de sincronização de diretório da Contoso**

![Infraestrutura de sincronização de diretórios da Contoso](images/Contoso_Poster/DirSync.png)
  
A Figura 3 mostra um cluster de servidores que executam o Azure AD conectar-se a floresta Contoso Windows Server AD como sincronizar com o locatário do Azure AD.
  
Contoso tiver configurado a autenticação federada, que fornece o serviço single sign-on para trabalhadores da Contoso. Quando um usuário que já tiver entrado para a floresta do Windows Server AD contoso.com acessa um recurso de nuvem Microsoft SaaS ou PaaS, eles não serão solicitados por uma senha.
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a>Distribuição geográfica de tráfego de autenticação da Contoso

Para oferecer um melhor suporte sua força de trabalho móvel e remota, a Contoso implantou os conjuntos de servidores de autenticação em seus escritórios regionais. Essa infra-estrutura distribui a carga e fornece um melhor desempenho e redundância ao autenticar credenciais de usuário para acesso a ofertas de nuvem da Microsoft que usam o locatário comuns do Azure AD.
  
Para distribuir a carga de solicitações de autenticação, a Contoso configurou o Gerenciador de tráfego do Windows Azure com um perfil que usa o método, que se refere a autenticação de clientes para o conjunto regional mais próximo de servidores de autenticação de roteamento de desempenho. 
  
**Figura 4: A distribuição geográfica de tráfego de autenticação para escritórios regionais**

![Distribuição geográfica do tráfego de autenticação da Contoso para escritórios regionais](images/Contoso_Poster/Auth_GeoDist.png)
  
Figura 4 mostra as camadas de computadores clientes, Gerenciador de tráfego do Windows Azure e servidores de autenticação em escritórios regionais. Cada escritório regional usa proxies de web e servidores do AD FS para autenticar credenciais de usuário com os controladores de domínio do Windows Server AD.
  
Exemplo do processo de autenticação:
  
1. O computador cliente inicia a comunicação com uma página da web no Office 365 aluguel na Europa (por exemplo, sharepoint.contoso.com).
    
2. O Office 365 volta envia uma solicitação para enviar uma prova de autenticação. A solicitação contém a URL para contatar para autenticação.
    
3. O computador cliente tenta resolver o nome DNS na URL para um endereço IP.
    
4. Gerenciador de tráfego do Azure recebe a consulta DNS e responde para o computador cliente com o endereço IP de um servidor de proxy de aplicativo web no escritório regional mais próximo ao computador cliente.
    
5.  O computador cliente envia uma solicitação de autenticação para um servidor de proxy de aplicativo web, que encaminha a solicitação para um servidor AD FS.
    
6. O servidor do AD FS solicita as credenciais do usuário do computador cliente.
    
7. O computador cliente envia as credenciais do usuário sem avisar o usuário.
    
8. O servidor do AD FS valida as credenciais com um controlador de domínio do Windows Server AD no escritório regional e retorna um token de segurança para o computador cliente.
    
9. O computador cliente envia o token de segurança para o Office 365.
    
10. Após uma validação bem-sucedida, o Office 365 armazena em cache o token de segurança e envia a página da web solicitada na etapa 1 para o computador cliente.
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a>Redundância para a infraestrutura de autenticação matrizes no Azure IaaS

Para fornecer redundância para os trabalhadores remotos e móveis da sede Paris que contém a 15.000 trabalhadores, a Contoso implantou um segundo conjunto de proxies de aplicativos e servidores do AD FS no Azure IaaS.
  
**Figura 5: Infraestrutura de autenticação redundantes no Azure IaaS**

![A infraestrutura de autenticação redundante no Azure IaaS para a sede de Paris](images/Contoso_Poster/Paris_Auth_Redun.png)
  
Figura 5 mostra servidores AD FS e proxies de web no DMZ e um conjunto adicional de cada uma no Azure locais cruzados rede virtual.
  
Quando os servidores de autenticação primária na sede da DMZ ficar indisponíveis, a equipe de TI alterna para o conjunto redundante implantado no Azure IaaS. Solicitações de autenticação subsequentes de computadores de escritório Paris usam o conjunto no Azure IaaS, até que o problema de disponibilidade for corrigido.
  
Para alternar e voltar, Contoso atualizações o perfil do Gerenciador de tráfego do Windows Azure para a região Paris usar um conjunto diferente de endereços IP para os proxies de aplicativo web:
  
- Quando os servidores de autenticação DMZ estão disponíveis, use os endereços IP dos servidores no DMZ.
    
- Quando os servidores de autenticação DMZ não estão disponíveis, use os endereços IP dos servidores no Azure IaaS.
    
## <a name="see-also"></a>See Also

[Contoso em nuvem da Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Identidade de nuvem da Microsoft para arquitetos da empresa](http://aka.ms/cloudarchidentity)
  
[Identidade e a proteção de dispositivo para o Office 365](http://aka.ms/o365protect_device)
  
[Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



