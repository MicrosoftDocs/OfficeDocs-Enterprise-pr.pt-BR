---
title: Autenticação federada de alta disponibilidade fase 5 configurar autenticação federada para o Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: 'Resumo: Configure o Azure AD conectar-se para sua autenticação federada de alta disponibilidade para o Office 365 in Microsoft Azure.'
ms.openlocfilehash: 797429e508a0a0c2b91d837e5475e840ca26b3d8
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915356"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a>Autenticação federada de alta disponibilidade Fase 5: configurar a autenticação federada para o Office 365

 **Resumo:** Configure o Azure AD conectar-se para sua autenticação federada de alta disponibilidade para o Office 365 in Microsoft Azure.
 
Nesta fase final da implantação de autenticação federada de alta disponibilidade para o Office 365 nos serviços de infraestrutura do Windows Azure, você obter e instala um certificado emitido por uma autoridade de certificação pública, verifique se a sua configuração e, em seguida, instale e execute Azure AD. Conecte-se no servidor de sincronização de diretório. Conectar do Azure AD configura sua assinatura do Office 365 e seus serviços de Federação do Active Directory (AD FS) e servidores de proxy de aplicativo da web para autenticação federada.
  
Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>Obtenha um certificado público e copiá-lo para o servidor de sincronização de diretório

Obtenha um certificado digital de uma autoridade de certificação pública com as seguintes propriedades:
  
- Um certificado x. 509 adequado para criar conexões SSL.
    
- O nome de alternativo da entidade (SAN) estendido a propriedade for definida como seu FQDN do serviço de Federação (exemplo: fs.contoso.com).
    
- O certificado deve ter a chave privada e ser armazenado no formato PFX.
    
Além disso, seus computadores da organização e dispositivos devem confiar a autoridade de certificação pública que está emitindo o certificado digital. Esta confiança é estabelecida estabelecendo um certificado raiz da autoridade de certificação pública instalado no armazenamento de autoridades de certificação raiz confiáveis em seus computadores e dispositivos. Computadores que executam o Microsoft Windows geralmente têm um conjunto desses tipos de certificados instalados em autoridades de certificação usadas regularmente. Se o certificado raiz da sua autoridade de certificação pública já não estiver instalado, você deverá implantar esta aos computadores e dispositivos de sua organização.
  
Para obter mais informações sobre os requisitos de certificado para autenticação federada, consulte [pré-requisitos para instalação de Federação e configuração](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).
  
Quando você recebe o certificado, copie-o para uma pasta na unidade c: do servidor de sincronização de diretório. Por exemplo, nomeie o arquivo SSL.pfx e armazene-a em c:\\pasta certificados no servidor de sincronização de diretório.
  
## <a name="verify-your-configuration"></a>Verifique se a sua configuração

Agora você deve estar pronto para configurar o Azure Connect de AD e autenticação federada para o Office 365. Para garantir que você está, aqui está uma lista de verificação:
  
- Domínio de público da sua organização é adicionado à sua assinatura do Office 365.
    
- Contas de usuário do Office 365 da sua organização estiverem configuradas para o nome de domínio público da sua organização e podem entrar com êxito.
    
- Você determinou que um FQDN do serviço de federação com base em seu nome de domínio público.
    
- Um registro DNS A público para seus pontos FQDN de serviço de federação para o endereço IP público do Azure voltado à Internet balanceador de carga para os servidores de proxy de aplicativo web.
    
- Um registro DNS A privada para seus pontos FQDN de serviço de federação para o endereço IP privado do balanceador de carga Azure interno para os servidores do AD FS.
    
- Um certificação pública autoridade-isssued certificado digital adequado para conexões SSL com SAN definida como seu serviço de federação que FQDN é um arquivo PFX armazenado no seu servidor de sincronização de diretório.
    
- O certificado raiz da autoridade de certificação pública está instalado em autoridades de certificação raiz confiáveis armazene em seus computadores e dispositivos.
    
Aqui está um exemplo de organização Contoso:
  
**Um exemplo de configuração para uma alta disponibilidade federado a infraestrutura de autenticação no Windows Azure**

![Um exemplo de configuração da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure](media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Execute o Azure AD conectar-se para configurar a autenticação federada

A ferramenta conectar do Azure AD configura o Office 365, os servidores de proxy de aplicativo da web e servidores do AD FS para autenticação federada com estas etapas:
  
1. Crie uma conexão de área de trabalho remota ao seu servidor de sincronização de diretório com uma conta de domínio que tenha privilégios de administrador local.
    
2. Área de trabalho do servidor de sincronização de diretório, abra o Internet Explorer e vá para [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
3. Na página **Microsoft Azure Active Directory Connect** , clique em **Download**e, em seguida, clique em **Executar**.
    
4. Na página **Bem-vindo ao conectar do Azure AD** , clique em **Concordo**e clique em **continuar.**
    
5. Na página **Configurações Expressas**, clique em **Personalizar**.
    
6. Na página **Instalar componentes necessários**, clique em **Instalar**. 
    
7. Na página **Entrada do usuário**, clique em **Federação com AD FS** e em **Avançar**.
    
8. Na página **conectar ao AD do Windows Azure** , digite o nome e senha de uma conta de administrador global para a sua assinatura do Office 365 e clique em **Avançar**.
    
9. Na página **conectar seus diretórios** , certifique-se de que sua floresta do Windows Server AD local está selecionada na **floresta**, digite o nome e a senha de uma conta de administrador de domínio, clique em **Adicionar diretório**e, em seguida, clique em **Avançar**.
    
10. Na página **configuração de entrada do Azure AD** , clique em **Avançar**.
    
11. Na página de **filtragem de unidade Organizacional e o domínio** , clique em **Avançar**.
    
12. Na página **que identifica unicamente a seus usuários** , clique em **Avançar**.
    
13. Na página **usuários e dispositivos de filtro** , clique em **Avançar**.
    
14. Na página **recursos opcionais** , clique em **Avançar**.
    
15. Na página **farm AD FS** , clique em **Configurar um novo farm do AD FS**.
    
16. Clique em **Procurar** e especifique o local e o nome do certificado SSL da autoridade de certificação pública.
    
17. Quando solicitado, digite a senha do certificado e, em seguida, clique em **Okey**.
    
18. Verifique se o **Nome da entidade** e o **Nome do serviço de Federação** estão definidos para seu serviço de Federação FQDN e, em seguida, clique em **Avançar**.
    
19. Na página **servidores AD FS** , digite o nome do primeiro servidor do AD FS (tabela M - Item 4 - coluna de nome de máquina Virtual) e, em seguida, clique em **Adicionar**.
    
20. Digite o nome do seu servidor de AD FS segundo (tabela M - Item 5 - coluna de nome de máquina Virtual), clique em **Adicionar**e, em seguida, clique em **Avançar**.
    
21. Na página **servidores de Proxy de aplicativo Web** , digite o nome do seu primeiro aplicativo proxy do servidor web (tabela M - Item 6 - coluna de nome de máquina Virtual) e, em seguida, clique em **Adicionar**.
    
22. Digite o nome do segundo aplicativo proxy do servidor web (tabela M - Item 7 - coluna de nome de máquina Virtual), clique em **Adicionar**e, em seguida, clique em **Avançar**.
    
23. Na página **credenciais de administrador de domínio** , digite o nome de usuário e senha de uma conta de administrador de domínio e clique em **Avançar**.
    
24. Na página **conta de serviço do AD FS** , digite o nome de usuário e a senha de uma conta de administrador da empresa e clique em **Avançar**.
    
25. Na página **Domínio do Windows Azure AD** , no **domínio**, selecione o nome de domínio DNS da sua organização e clique em **Avançar**.
    
26. Na página **Pronto para configurar**, clique em **Instalar**.
    
27. Na página **instalação concluída** , clique em **Verificar**. Você deverá ver duas mensagens indicando que a intranet e a Internet configuração foram verificada com êxito.
    
  - A mensagem de intranet deve listar o endereço IP privado sua Azure interno do balanceador de carga para os seus servidores do AD FS.
    
  - A mensagem de Internet deve listar o endereço IP público do seu balanceador de carga voltados para a Internet do Windows Azure para seus servidores de proxy de aplicativo web.
    
28. Na página **Instalação Completa**, clique em **Fechar**.
    
Aqui está a configuração final, com nomes de espaço reservado para os servidores.
  
**Fase 5: A configuração final de uma alta disponibilidade federado infraestrutura de autenticação no Windows Azure**

![A configuração final da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Sua infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Windows Azure é concluída.
  
## <a name="see-also"></a>Confira também

[Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Identidade federada para seu ambiente de desenvolvimento e teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Identidade federada para o Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


