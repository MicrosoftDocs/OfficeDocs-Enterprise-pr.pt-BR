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
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Resumo: Descreve os certificados SSL necessários para o Exchange no local e híbrido, SSO usando o AD FS, serviços do Exchange Online e serviços Web do Exchange.'
ms.openlocfilehash: c9e968ef7ec9015be398b4eef9184451dd316bea
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546512"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Plano para certificados SSL de terceiros para o Office 365

 **Resumo:** Descreve os certificados SSL necessários para Exchange local e híbrido, SSO usando o AD FS, serviços do Exchange Online e serviços Web do Exchange. 
  
Para criptografar comunicações entre seus clientes e o ambiente do Office 365, os certificados de camada de soquete seguro (SSL) de terceiros devem ser instalados em seus servidores de infraestrutura.

||
|:-----|
| Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).|
   
Os certificados são obrigatórios para os seguintes componentes do Office 365:
  
- Exchange local
    
- Logon único (SSO) (para os servidores de federação dos Serviços de Federação do Active Directory (AD FS) e os proxies do servidor de federação do AD FS)
    
- Serviços do Exchange Online, como descoberta automática, Outlook em qualquer lugar e serviços Web do Exchange
    
- Servidor híbrido do Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>Certificados para o Exchange local

Para obter uma visão geral sobre como usar certificados digitais para tornar a comunicação entre a organização do Exchange no local e o Exchange Online seguro, consulte o artigo TechNet [Compreendendo requisitos de certificado](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Certificados para logon único

Para fornecer aos usuários uma simplificado single sign-on experiência que inclui segurança robusta, os certificados mostrados na tabela a seguir são necessárias nos servidores de Federação ou os proxies do servidor de Federação. A tabela a seguir se concentra em serviços de Federação do Active Directory (AD FS), também temos para obter mais informações sobre como [usar provedores de identidade de terceiros](https://go.microsoft.com/fwlink/?LinkId=532869).
  
||||
|:-----|:-----|:-----|
|**Tipo de Certificado** <br/> |**Descrição** <br/> |**O que você precisa saber antes de implantar** <br/> |
|**Certificado SSL (também chamado de certificado de autenticação de servidor)** <br/> |É um certificado SSL padrão usado para tornar as comunicações entre servidores de federação, clientes e computadores do proxy do servidor de federação seguros.  <br/> |O AD FS requer um certificado SSL. Por padrão, o AD FS usa o certificado SSL configurado para o site padrão no serviços de informações da Internet (IIS).<br/> O nome da entidade do certificado SSL é usado para determinar o nome do serviço de Federação (FS) para cada instância do AD FS que você implanta. Considere escolher um nome de entidade para qualquer nova autoridade de certificação (CA)-emitidos certificados que melhor representa o nome da sua empresa ou organização para o Office 365. Este nome deve ser roteáveis pela Internet.<br/>**Cuidado:** O AD FS requer que o certificado SSL não tenha nenhum nome de entidade de pontos (apelido).          <br/> **Recomendação:** Porque este certificado deve ser confiável pelos clientes do AD FS, recomendamos que você use um certificado SSL emitido por uma autoridade de certificação pública (terceiros) ou por uma autoridade de certificação subordinada a uma raiz confiada publicamente; Por exemplo, VeriSign ou Thawte.  <br/> |
|**Certificado de assinatura de token** <br/> |Este é um certificado x. 509 padrão usado para assinar com segurança todos os tokens que o servidor de Federação emite e que o Office 365 aceito e validado.  <br/> |O certificado de assinatura de token deve conter uma chave privada vinculado a uma raiz confiável no FS. Por padrão, o AD FS cria um certificado autoassinado. No entanto, dependendo das necessidades da sua organização, você pode alterar esse certificado para um certificado de autoridade de certificação emitida usando o snap-in de gerenciamento do AD FS.<br/>**Cuidado:** O certificado de assinatura de token é fundamental para a estabilidade do FS. Se o certificado for alterado, o Office 365 deve ser notificado sobre a alteração. Se a notificação não for fornecida, os usuários não podem entrar no suas ofertas de serviço do Office 365.<br/>**Recomendação:** Recomendamos que você use o certificado autoassinado assinatura de token que seja gerado pelo AD FS. Fazendo isso, ele gerencia esse certificado para você por padrão. Por exemplo, quando esse certificado está prestes a expirar, o AD FS irá gerar um novo certificado autoassinado.<br/> |
   
Os proxies do servidor de federação exigem o certificado descrito na tabela a seguir.
  
||||
|:-----|:-----|:-----|
|**Tipo de certificado** <br/> |**Descrição** <br/> |**O que você precisa saber antes de implantar** <br/> |
|Certificado SSL  <br/> |É um certificado SSL padrão usado para proteger comunicações entre um servidor de federação, um proxy de servidor de federação e computadores cliente da Internet.  <br/> |Esse certificado SSL deve ser vinculado ao site padrão no IIS antes de poder executar o Assistente de configuração de Proxy de servidor de Federação do AD FS com êxito.  <br/> Esse certificado deverá ter o mesmo nome de assunto do certificado SSL configurado no servidor de federação na rede corporativa.  <br/> **Recomendação:** Recomendamos que você use o mesmo certificado de autenticação de servidor configurado no servidor de federação ao qual esse proxy de servidor de federação se conecta.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificados para descoberta automática, o Outlook em qualquer lugar e a sincronização do Active Directory

Sua externo voltado para Exchange 2013, Exchange 2010, Exchange 2007 e Exchange 2003 Client Access servidores (classes) exigem um certificado SSL de terceiros para conexões seguras para os serviços de sincronização de descoberta automática, Outlook em qualquer lugar e do Active Directory. Talvez você já tenha esse certificado instalado no seu ambiente local.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificado para um Servidor Híbrido do Exchange

Seu servidor híbrido do Exchange ou servidores em externo voltado para exigem um certificado SSL de terceiros para conectividade segura com o serviço Exchange Online. Você precisará fazer esse certificado a partir de seu provedor SSL de terceiros.
  
## <a name="office-365-certificate-chains"></a>Cadeias de certificados do Office 365

Este artigo descreve os certificados que você talvez precise instalar na sua infra-estrutura. Para obter mais informações sobre os certificados instalados em nossos servidores do Office 365, consulte [Cadeias de certificados do Office 365](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  

