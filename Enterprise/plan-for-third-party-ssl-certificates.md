---
title: Plano para certificados SSL de terceiros para o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Resumo: descreve os certificados SSL necessários para o Exchange local e híbrido, SSO usando AD FS, serviços do Exchange Online e serviços Web do Exchange.'
ms.openlocfilehash: 3c22daa2315e36c45b5b5dd6271842168c90726d
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491407"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Plano para certificados SSL de terceiros para o Office 365

 **Resumo:** Descreve os certificados SSL necessários para o Exchange local e híbrido, SSO usando AD FS, serviços do Exchange Online e serviços Web do Exchange. 
  
Para criptografar comunicações entre seus clientes e o ambiente do Office 365, os certificados SSL (Secure Socket Layer) de terceiros devem ser instalados nos seus servidores de infraestrutura.

||
|:-----|
| Este artigo faz parte do [planejamento de rede e do ajuste de desempenho do Office 365](https://aka.ms/tune).|
   
Os certificados são necessários para os seguintes componentes do Office 365:
  
- Exchange local
    
- Logon único (SSO) (para os servidores de Federação dos serviços de Federação do Active Directory (AD FS) e proxies do servidor de Federação do AD FS)
    
- Serviços do Exchange Online, como descoberta automática, Outlook Anywhere e serviços Web do Exchange
    
- Servidor híbrido do Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>Certificados para o Exchange local

Para obter uma visão geral sobre como usar certificados digitais para fazer a comunicação entre a organização local do Exchange e o Exchange Online protegido, consulte o artigo da TechNet underStanding [Certificate requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Certificados para logon único

Para fornecer aos usuários uma experiência de logon único simplificada que inclua segurança robusta, os certificados mostrados na tabela a seguir são necessários nos servidores de Federação ou nos proxies do servidor de Federação. A tabela abaixo se concentra nos serviços de Federação do Active Directory (AD FS), também temos mais informações sobre o [uso de provedores de identidade de terceiros](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
||||
|:-----|:-----|:-----|
|**Tipo de certificado** <br/> |**Descrição** <br/> |**O que você precisa saber antes de implantar o** <br/> |
|**Certificado SSL (também chamado de certificado de autenticação de servidor)** <br/> |Este é um certificado SSL padrão usado para tornar as comunicações entre servidores de Federação, clientes e computadores de proxy do servidor de Federação seguros.  <br/> |O AD FS requer um certificado SSL. Por padrão, o AD FS usa o certificado SSL que é configurado para o site padrão nos serviços de informações da Internet (IIS).  <br/> O nome do assunto desse certificado SSL é usado para determinar o nome do serviço de Federação (FS) para cada instância do AD FS que você implantar. Considere a escolha de um nome de entidade para qualquer nova autoridade de certificação (CA) emitida certificados que melhor representam o nome de sua empresa ou organização para o Office 365. Esse nome deve ser roteável pela Internet.  <br/>**Cuidado:** O AD FS requer que esse certificado SSL não tenha nome de entidade sem ponto (nome abreviado).          <br/> **Recomendação:** Como esse certificado deve ser confiável para os clientes do AD FS, recomendamos que você use um certificado SSL emitido por uma CA pública (terceiros) ou por uma CA subordinada a uma raiz confiável publicamente; por exemplo, VeriSign ou Thawte.  <br/> |
|**Certificado de autenticação de token** <br/> |Este é um certificado X. 509 padrão usado para assinar com segurança todos os tokens emitidos pelo servidor de Federação e que o Office 365 aceita e valida.  <br/> |O certificado de autenticação de token deve conter uma chave privada que encadeia para uma raiz confiável no FS. Por padrão, o AD FS cria um certificado autoassinado. No enTanto, dependendo das necessidades da sua organização, você pode alterar esse certificado para um certificado emitido por AC usando o snap-in de gerenciamento do AD FS.  <br/>**Cuidado:** O certificado de autenticação de token é crítico para a estabilidade do FS. Se o certificado for alterado, o Office 365 deve ser notificado sobre a alteração. Se a notificação não for fornecida, os usuários não poderão entrar em suas ofertas de serviço do Office 365.<br/>**Recomendação:** Recomendamos que você use o certificado de autenticação de token auto-assinado gerado pelo AD FS. Ao fazer isso, ele gerencia esse certificado por padrão. Por exemplo, quando esse certificado estiver prestes a expirar, o AD FS irá gerar um novo certificado autoassinado.  <br/> |
   
Os proxies do servidor de Federação exigem o certificado descrito na tabela a seguir.
  
||||
|:-----|:-----|:-----|
|**Tipo de certificado** <br/> |**Descrição** <br/> |**O que você precisa saber antes de implantar o** <br/> |
|Certificado SSL  <br/> |Este é um certificado SSL padrão usado para proteger as comunicações entre um servidor de Federação, um proxy do servidor de Federação e computadores cliente da Internet.  <br/> |Esse certificado SSL deve estar associado ao site padrão no IIS antes que você possa executar o assistente de configuração de proxy do servidor de Federação do AD FS com êxito.  <br/> Esse certificado deve ter o mesmo nome de entidade que o certificado SSL configurado no servidor de Federação na rede corporativa.  <br/> **Recomendação:** Recomendamos que você use o mesmo certificado de autenticação de servidor configurado no servidor de Federação ao qual esse proxy de servidor de Federação se conecta.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificados para descoberta automática, Outlook Anywhere e sincronização do Active Directory

Seus servidores de acesso para cliente (CASs) do Exchange 2013, Exchange 2010, Exchange 2007 e Exchange 2003 exigem um certificado SSL de terceiros para conexões seguras para descoberta automática, Outlook Anywhere e serviços de sincronização do Active Directory. Talvez você já tenha esse certificado instalado no seu ambiente local.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificado para um servidor híbrido do Exchange

Seu servidor ou servidores híbridos do Exchange de face externa exigem um certificado SSL de terceiros para conectividade segura com o serviço do Exchange Online. Você precisa obter esse certificado do provedor de SSL de terceiros.
  
## <a name="office-365-certificate-chains"></a>Cadeias de certificados do Office 365

Este artigo descreve os certificados que você pode precisar instalar em sua infraestrutura. Para obter mais informações sobre os certificados instalados em nossos servidores do Office 365, confira cadeias de [certificados do office 365](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  

