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
ms.openlocfilehash: 93e872098b31326de67fb0557354e9f4fc1de9ed
ms.sourcegitcommit: a337ac253054f571a8304e18e426f74bcd385857
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2018
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="f6174-103">Alta disponibilidade federado autenticação fase 5: configurar a autenticação federada para o Office 365</span><span class="sxs-lookup"><span data-stu-id="f6174-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

 <span data-ttu-id="f6174-104">**Resumo:** Configure o Azure AD conectar-se para sua autenticação federada de alta disponibilidade para o Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="f6174-104">**Summary:** Configure Azure AD Connect for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
 
<span data-ttu-id="f6174-p101">Nesta fase final da implantação de autenticação federada de alta disponibilidade para o Office 365 nos serviços de infraestrutura do Windows Azure, você obter e instala um certificado emitido por uma autoridade de certificação pública, verifique se a sua configuração e, em seguida, instale e execute Azure AD. Conecte-se no servidor de sincronização de diretório. Conectar do Azure AD configura sua assinatura do Office 365 e seus serviços de Federação do Active Directory (AD FS) e servidores de proxy de aplicativo da web para autenticação federada.</span><span class="sxs-lookup"><span data-stu-id="f6174-p101">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the directory synchronization server. Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="f6174-107">Consulte [autenticação federada de alta disponibilidade de implantação para o Office 365 no Windows Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas as fases.</span><span class="sxs-lookup"><span data-stu-id="f6174-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a><span data-ttu-id="f6174-108">Obtenha um certificado público e copiá-lo para o servidor de sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="f6174-108">Get a public certificate and copy it to the directory synchronization server</span></span>

<span data-ttu-id="f6174-109">Obtenha um certificado digital de uma autoridade de certificação pública com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="f6174-109">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="f6174-110">Um certificado x. 509 adequado para criar conexões SSL.</span><span class="sxs-lookup"><span data-stu-id="f6174-110">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="f6174-111">O nome de alternativo da entidade (SAN) estendido a propriedade for definida como seu FQDN do serviço de Federação (exemplo: fs.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="f6174-111">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="f6174-112">O certificado deve ter a chave privada e ser armazenado no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="f6174-112">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="f6174-p102">Além disso, seus computadores da organização e dispositivos devem confiar a autoridade de certificação pública que está emitindo o certificado digital. Esta confiança é estabelecida estabelecendo um certificado raiz da autoridade de certificação pública instalado no armazenamento de autoridades de certificação raiz confiáveis em seus computadores e dispositivos. Computadores que executam o Microsoft Windows geralmente têm um conjunto desses tipos de certificados instalados em autoridades de certificação usadas regularmente. Se o certificado raiz da sua autoridade de certificação pública já não estiver instalado, você deverá implantar esta aos computadores e dispositivos de sua organização.</span><span class="sxs-lookup"><span data-stu-id="f6174-p102">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="f6174-117">Para obter mais informações sobre os requisitos de certificado para autenticação federada, consulte [pré-requisitos para instalação de Federação e configuração](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span><span class="sxs-lookup"><span data-stu-id="f6174-117">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="f6174-p103">Quando você recebe o certificado, copie-o para uma pasta na unidade c: do servidor de sincronização de diretório. Por exemplo, nomeie o arquivo SSL.pfx e armazene-a em c:\\pasta certificados no servidor de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="f6174-p103">When you receive the certificate, copy it to a folder on the C: drive of the directory synchronization server. For example, name the file SSL.pfx and store it in the C:\\Certs folder on the directory synchronization server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="f6174-120">Verifique se a sua configuração</span><span class="sxs-lookup"><span data-stu-id="f6174-120">Verify your configuration</span></span>

<span data-ttu-id="f6174-p104">Agora você deve estar pronto para configurar o Azure Connect de AD e autenticação federada para o Office 365. Para garantir que você está, aqui está uma lista de verificação:</span><span class="sxs-lookup"><span data-stu-id="f6174-p104">You should now be ready to configure Azure AD Connect and federated authentication for Office 365. To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="f6174-123">Domínio de público da sua organização é adicionado à sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="f6174-123">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="f6174-124">Contas de usuário do Office 365 da sua organização estiverem configuradas para o nome de domínio público da sua organização e podem entrar com êxito.</span><span class="sxs-lookup"><span data-stu-id="f6174-124">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="f6174-125">Você determinou que um FQDN do serviço de federação com base em seu nome de domínio público.</span><span class="sxs-lookup"><span data-stu-id="f6174-125">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="f6174-126">Um registro DNS A público para seus pontos FQDN de serviço de federação para o endereço IP público do Azure voltado à Internet balanceador de carga para os servidores de proxy de aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="f6174-126">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="f6174-127">Um registro DNS A privada para seus pontos FQDN de serviço de federação para o endereço IP privado do balanceador de carga Azure interno para os servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="f6174-127">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="f6174-128">Um certificação pública autoridade-isssued certificado digital adequado para conexões SSL com SAN definida como seu serviço de federação que FQDN é um arquivo PFX armazenado no seu servidor de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="f6174-128">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your directory synchronization server.</span></span>
    
- <span data-ttu-id="f6174-129">O certificado raiz da autoridade de certificação pública está instalado em autoridades de certificação raiz confiáveis armazene em seus computadores e dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f6174-129">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="f6174-130">Aqui está um exemplo de organização Contoso:</span><span class="sxs-lookup"><span data-stu-id="f6174-130">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="f6174-131">**Um exemplo de configuração para uma alta disponibilidade federado a infraestrutura de autenticação no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="f6174-131">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Um exemplo de configuração da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure](images/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="f6174-133">Execute o Azure AD conectar-se para configurar a autenticação federada</span><span class="sxs-lookup"><span data-stu-id="f6174-133">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="f6174-134">A ferramenta conectar do Azure AD configura o Office 365, os servidores de proxy de aplicativo da web e servidores do AD FS para autenticação federada com estas etapas:</span><span class="sxs-lookup"><span data-stu-id="f6174-134">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="f6174-135">Crie uma conexão de área de trabalho remota ao seu servidor de sincronização de diretório com uma conta de domínio que tenha privilégios de administrador local.</span><span class="sxs-lookup"><span data-stu-id="f6174-135">Create a remote desktop connection to your directory synchronization server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="f6174-136">Área de trabalho do servidor de sincronização de diretório, abra o Internet Explorer e vá para [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="f6174-136">From the desktop of the directory synchronization server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="f6174-137">Na página **Microsoft Azure Active Directory Connect** , clique em **Download**e, em seguida, clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-137">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="f6174-138">Na página **Bem-vindo ao conectar do Azure AD** , clique em **Concordo**e clique em **continuar.**</span><span class="sxs-lookup"><span data-stu-id="f6174-138">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="f6174-139">Na página **Configurações Express** , clique em **Personalizar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-139">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="f6174-140">Na página **instalar componentes necessários** , clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-140">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="f6174-141">Na página de **logon do usuário** , clique em **federação com o AD FS**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-141">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="f6174-142">Na página **conectar ao AD do Windows Azure** , digite o nome e senha de uma conta de administrador global para a sua assinatura do Office 365 e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-142">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="f6174-143">Na página **conectar seus diretórios** , certifique-se de que sua floresta do Windows Server AD local está selecionada na **floresta**, digite o nome e a senha de uma conta de administrador de domínio, clique em **Adicionar diretório**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-143">On the **Connect your directories** page, ensure that your on-premises Windows Server AD forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="f6174-144">Na página **configuração de entrada do Azure AD** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-144">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="f6174-145">Na página de **filtragem de unidade Organizacional e o domínio** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-145">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="f6174-146">Na página **que identifica unicamente a seus usuários** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-146">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="f6174-147">Na página **usuários e dispositivos de filtro** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-147">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="f6174-148">Na página **recursos opcionais** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-148">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="f6174-149">Na página **farm AD FS** , clique em **Configurar um novo farm do AD FS**.</span><span class="sxs-lookup"><span data-stu-id="f6174-149">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="f6174-150">Clique em **Procurar** e especifique o local e o nome do certificado SSL da autoridade de certificação pública.</span><span class="sxs-lookup"><span data-stu-id="f6174-150">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="f6174-151">Quando solicitado, digite a senha do certificado e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="f6174-151">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="f6174-152">Verifique se o **Nome da entidade** e o **Nome do serviço de Federação** estão definidos para seu serviço de Federação FQDN e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-152">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="f6174-153">Na página **servidores AD FS** , digite o nome do primeiro servidor do AD FS (tabela M - Item 4 - coluna de nome de máquina Virtual) e, em seguida, clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-153">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="f6174-154">Digite o nome do seu servidor de AD FS segundo (tabela M - Item 5 - coluna de nome de máquina Virtual), clique em **Adicionar**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-154">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="f6174-155">Na página **servidores de Proxy de aplicativo Web** , digite o nome do seu primeiro aplicativo proxy do servidor web (tabela M - Item 6 - coluna de nome de máquina Virtual) e, em seguida, clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-155">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="f6174-156">Digite o nome do segundo aplicativo proxy do servidor web (tabela M - Item 7 - coluna de nome de máquina Virtual), clique em **Adicionar**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-156">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="f6174-157">Na página **credenciais de administrador de domínio** , digite o nome de usuário e senha de uma conta de administrador de domínio e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-157">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="f6174-158">Na página **conta de serviço do AD FS** , digite o nome de usuário e a senha de uma conta de administrador da empresa e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-158">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="f6174-159">Na página **Domínio do Windows Azure AD** , no **domínio**, selecione o nome de domínio DNS da sua organização e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-159">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="f6174-160">Na página **pronto para configurar** , clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="f6174-160">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="f6174-p105">Na página **instalação concluída** , clique em **Verificar**. Você deverá ver duas mensagens indicando que a intranet e a Internet configuração foram verificada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f6174-p105">On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="f6174-163">A mensagem de intranet deve listar o endereço IP privado sua Azure interno do balanceador de carga para os seus servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="f6174-163">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="f6174-164">A mensagem de Internet deve listar o endereço IP público do seu balanceador de carga voltados para a Internet do Windows Azure para seus servidores de proxy de aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="f6174-164">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="f6174-165">Na página **instalação concluída** , clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="f6174-165">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="f6174-166">Aqui está a configuração final, com nomes de espaço reservado para os servidores.</span><span class="sxs-lookup"><span data-stu-id="f6174-166">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="f6174-167">**Fase 5: A configuração final de uma alta disponibilidade federado infraestrutura de autenticação no Windows Azure**</span><span class="sxs-lookup"><span data-stu-id="f6174-167">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![A configuração final da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="f6174-169">Sua infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Windows Azure é concluída.</span><span class="sxs-lookup"><span data-stu-id="f6174-169">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f6174-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="f6174-170">See Also</span></span>

[<span data-ttu-id="f6174-171">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="f6174-171">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="f6174-172">Identidade federada para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="f6174-172">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="f6174-173">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="f6174-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="f6174-174">Identidade federada para o Office 365</span><span class="sxs-lookup"><span data-stu-id="f6174-174">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


