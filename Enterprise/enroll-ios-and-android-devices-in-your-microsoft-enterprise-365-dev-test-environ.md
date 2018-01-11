---
title: Registrar o iOS e Android dispositivos em seu ambiente de desenvolvimento e teste do Microsoft Enterprise 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Resumo: Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente."
ms.openlocfilehash: 71d04b0d2a59683ff09ad4256ed8fc82e89e876a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>Registrar o iOS e Android dispositivos em seu ambiente de desenvolvimento e teste do Microsoft Enterprise 365

 **Resumo:** Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.
  
O pacote de mobilidade do Microsoft Enterprise (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Se você precisar aplicar segurança em nível de dispositivo, deverá registrar dispositivos no Microsoft Intune. A inscrição de dispositivos não só ajuda você a gerenciar dispositivos de propriedade da empresa, como também dispositivos pessoais (BYOD) e compartilhados, dependendo das políticas legais da sua organização.
  
Seguindo as instruções fornecidas neste artigo, você poderá registrar e testar recursos de gerenciamento de dispositivo móvel básica para dispositivos com Android e iOS em seu ambiente de desenvolvimento e teste da Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Fase 1: Crie seu ambiente de desenvolvimento e teste da Microsoft 365

Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a>Fase 2: Personalizar o aplicativo de Portal da Empresa do Microsoft Intune

Use essas etapas para personalizar o aplicativo de Portal da Empresa do Microsoft Intune para sua empresa fictícia:
  
1. Em uma nova guia, abra o console de administração do Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).
    
2. Clique em **Admin** , no painel de navegação e, em seguida, clique em **Gerenciamento de dispositivos móveis** do painel de **Administração** .
    
3. Na lista de **tarefas** , selecione **Definir autoridade de gerenciamento de dispositivo móvel**. Certifique-se de que ele está definido como **Microsoft Intune**.
    
4. No painel **Administração** , clique em **Portal da empresa**.
    
5. No painel de **Portal da empresa** , defina as seguintes configurações:
    
  - Nome da empresa: \<seu nome de empresa fictícia >
    
  - O nome do contato de departamento IT: **User5**
    
  - Número de telefone do departamento de IT: **555-1234**
    
  - Endereço de email do departamento de IT: **User5 @**\<nome da empresa fictícia de organização > **. onmicrosoft.com** (o endereço de email da conta User5)
    
6. Em **personalização**, selecione **verde** na **cor do tema**.
    
7. Clique em **Salvar**.
    
Em seguida, você instalará o aplicativo de Portal da Empresa do Microsoft Intune e registrará um dispositivo iOS ou Android e depois testará a funcionalidade básica de gerenciamento do console de administração do Microsoft Intune.
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a>Fase 3 (apenas para dispositivos iOS): Inscrever e gerenciar um dispositivo iOS

Para inscrever um dispositivo iOS para gerenciamento pelo Intune, você precisará do seguinte:
  
- Um dispositivo iOS, como um Apple iPad ou um iPhone.
    
- Conhecimento da senha do dispositivo iOS.
    
- Uma ID da Apple (um nome de conta e senha). Se você não tiver um, vá para o [website da ID da Apple](https://appleid.apple.com/#!&amp;page=signin) e clique em **criar sua ID da Apple**. Crie uma ID da Apple correspondente à conta de administrador global de sua assinatura do Office 365. Registre seu novo nome de conta do Apple ID e a senha em um local seguro.
    
Um certificado do Apple Push Notification Service (APNs) é necessário para o Intune gerenciar dispositivos iOS e Mac. Quando o certificado for adicionado ao Intune, os usuários poderão instalar o aplicativo de Portal da Empresa do Microsoft Intune para registrarem seus dispositivos, ou o administrador poderá configurar o gerenciamento de dispositivos iOS de propriedade da empresa.
  
Você precisa de um arquivo de solicitação de assinatura de certificado para solicitar um certificado de relação de confiança do Apple Push Certificates Portal. Para obter um arquivo de solicitação de assinatura de certificado:
  
1. No console de administração do Microsoft Intune, clique em **Admin** , no painel de navegação.
    
    No painel **Administração** , abra **gerenciamento de dispositivos móveis > iOS e Mac OS X**e clique em **carregar um certificado APNs** em **tarefas**. 
    
2. No painel de **carregar um certificado APNs** , clique em **Baixar a solicitação de certificado APNs**. Salve o arquivo de solicitação (.csr) localmente com o nome do **teste de desenvolvimento**de assinatura de certificado.
    
Para obter um certificado do Apple Push Notification Service:
  
1. Abrir uma nova guia, vá para o [Portal do Apple Push certificados](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)e entrar com sua ID de Apple.
    
2. Na página **Introdução** , clique em **criar um certificado**.
    
3. Na página **Termos de uso** , selecione **eu leu e concorda com estes termos e condições**e, em seguida, clique em **Aceitar**.
    
4. Na página **criar um novo certificado de Push** , clique em **Procurar** e selecione o arquivo de **dev-test.csr** salvo no procedimento anterior e, em seguida, clique em **carregar**. Quando solicitado para abrir um arquivo json, salve-o na mesma pasta onde o arquivo dev-test.csr está armazenado.
    
5. Abra o [Portal do Apple Push certificados](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) em uma guia diferente e para **os certificados para servidores de terceiros**, clique em **Baixar**.
    
6. Quando solicitado para abrir um arquivo de .pem, salve-o com o nome **dev-test.pem** na mesma pasta onde o arquivo dev-test.csr está armazenado. Esse é o seu certificado APNs.
    
Para carregar o certificado APNs no Intune:
  
1. Na guia de console de administração do Microsoft Intune, na página **carregar um certificado APNs** , clique em **carregar o certificado APNs**.
    
2. Clique em **Procurar** e especifique o arquivo **dev-test.pem** .
    
3. Clique em **Abrir**, digite seu nome de conta da ID da Apple e, em seguida, clique em **carregar**. Você verá uma mensagem **pronto para inscrição** na página **iOS e configuração do gerenciamento de dispositivo do MaxOS X Mobile** .
    
Com o certificado APNs instalado, agora o Intune pode registrar e gerenciar dispositivos iOS, enviando a política por push para os dispositivos móveis inscritos.
  
Para baixar o aplicativo de Portal da Empresa do Microsoft Intune e registrar o dispositivo iOS:
  
1. No seu dispositivo iOS, entre com seu ID Apple.
    
2. Abra o aplicativo de **Repositório da Apple** .
    
3. Digite **intune** na caixa Pesquisar e toque em **Microsoft Intune Portal da empresa**, e em seguida, **obter**e **instalar**.
    
4. Depois que ele instala, toque em **Abrir**.
    
5. Na tela do **Portal da empresa Intune** , entre com sua conta de administrador global do Office 365.
    
6. Na tela **Configuração de acesso empresa** , toque em **Iniciar**e, em seguida, toque duas vezes em **continuar** .
    
7. Sobre o **o que vem em seguida?** tela, toque em **registrar**.
    
8. Sobre o **Ativar o administrador do dispositivo?** tela, toque em **Ativar**.
    
9. Na tela de **Gerenciamento de perfil** , toque em **instalar**.
    
10. Em **Inserir senha**, digite sua senha de dispositivo iOS.
    
11. Na tela **o que vem em seguida** , toque em **registrar**.
    
12. **Instalar o perfil**, toque em **instalar**.
    
13. Na página **Aviso** , toque em **instalar**.
    
14. No **Gerenciamento remoto**, toque em **Confiar**.
    
15. Toque em **concluído** para concluir o processo de inscrição.
    
16. Quando solicitado a **abri-la no "Composição de Portal"?**, toque em **Abrir**.
    
17. Na tela **Configuração de acesso empresa** , toque em **Iniciar**e, em seguida, toque em **concluído**.
    
18. Na tela principal do aplicativo de Portal da Empresa do Microsoft Intune, você verá:
    
  - Uma faixa verde.
    
  - O nome da empresa fictícia no canto superior esquerdo.
    
  - O nome do dispositivo iOS listado em **Meus dispositivos**.
    
  - Na seção de **assistência técnica** , o **Nome do contato** do **User5** com o número de telefone de **555-1234** e um botão de **contato por email** .
    
O Microsoft Intune fornece recursos de bloqueio e redefinição de senha remotos. Se alguém perder um dispositivo, você poderá bloqueá-lo remotamente. Se alguém se esquecer da senha, você poderá removê-la remotamente.
  
Para bloquear um dispositivo iOS remotamente:
  
1. Do seu computador de administração, na guia de console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.
    
2. No painel **grupos** , abra **todos os dispositivos > dispositivos móveis todos > todos os dispositivos gerenciados direto**.
    
3. No painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .
    
4. Na lista de dispositivos, clique no seu dispositivo iOS.  
    
5. No seu dispositivo iOS, certifique-se de que ele esteja na tela principal.  
    
6. No seu computador de administração, na barra de tarefas, clique em **tarefas remotas > bloqueio remoto**. Assista seu dispositivo iOS conforme ele alterna para a tela de bloqueio.
    
Para remover a senha:
  
1. Do seu computador de administração, no painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .
    
2. Na lista, clique em seu dispositivo iOS. Na barra de tarefas, clique em **tarefas remotas > redefinição de senha**. Aguarde um minuto.
    
3. No seu dispositivo iOS, desbloqueá-lo e observe que não há uma senha. Para alterar a senha novamente, vá para **configurações**e, em seguida, a **senha**.
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a>Fase 3 (apenas para dispositivos Android): Inscrever e gerenciar um dispositivo Android

Você precisará do seguinte para registrar um dispositivo Android para gerenciamento pelo Intune:
  
- Um dispositivo Android.
    
- Conhecimento da senha do dispositivo.
    
Para baixar o aplicativo de Portal da Empresa do Intune e registrar o dispositivo:
  
1. Usando seu dispositivo Android, vá para o **Repositório do Google tocar**e, em seguida, toque em **Guia de Introdução**.
    
2. Digite **intune** na caixa Pesquisar e toque em **intune portal da empresa** nos resultados da pesquisa.
    
3. Toque no item **Intune Portal da empresa** e, em seguida, toque em **instalar**.
    
4. Na tela **para concluir a configuração de conta** , toque em **continuar**e, em seguida, **Ignore**.
    
5. No **Portal de empresa Intune**, toque em **Aceitar**. O aplicativo é instalado.
    
6. Toque em **Abrir**e, em seguida, toque em **entrar**.
    
7. Na tela do **Portal da empresa Intune** , entre com sua conta de administrador global do Office 365.
    
8. Na tela **Configuração de acesso empresa** , toque em **Iniciar**e, em seguida, **continuar** duas vezes.
    
9. Sobre o **o que vem em seguida?** tela, toque em **registrar**.
    
10. Sobre o **Ativar o administrador do dispositivo?** tela, toque em **Activate.**
    
11. Na tela de **Diretiva de privacidade** , selecione **eu confirmar** e, em seguida, toque em **Confirmar**. Aguarde o conclusão do processo de inscrição.
    
12. Na tela de **Configuração de acesso empresa** , toque **continuar**e, em seguida, toque em **concluído**.
    
13. Na tela principal do aplicativo de Portal da Empresa do Microsoft Intune, você verá uma faixa verde e o nome da empresa fictícia no canto superior esquerdo.
    
14. Toque em **Meus dispositivos**. Você deve ver seu nome de dispositivo Android na lista.
    
15. Toque em **contato IT**. Você deverá ver o número de telefone de **555-1234**, um botão de **contatos por email** , e entre em contato com o IT de **User5**.
    
O Microsoft Intune fornece recursos de bloqueio e redefinição de senha remotos. Se alguém perder um dispositivo, você poderá bloqueá-lo remotamente. Se alguém se esquecer da senha, você poderá redefini-la remotamente.
  
Para bloquear um dispositivo Android remotamente:
  
1. Do seu computador de administração, na guia de console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.
    
2. No painel **grupos** , abra **todos os dispositivos > dispositivos móveis todos > todos os dispositivos gerenciados direto**.
    
3. No painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .
    
4. Na lista de dispositivos, clique no seu dispositivo Android.  
    
5. No seu dispositivo Android, certifique-se de que ele esteja na tela principal.  
    
6. No seu computador de administração, na barra de tarefas, clique em **tarefas remotas > bloqueio remoto**. Quando solicitado, clique em **Sim**.
    
7. Observe seu dispositivo Android entrando na tela de bloqueio.
    
Quando você redefinir a senha para dispositivos com Android, o portal de administração Intune gera e configura uma senha forte.
  
Para redefinir a senha remotamente:
  
1. Do seu computador de administração, na guia de console de administração do Microsoft Intune do navegador, no painel de **Todos os dispositivos gerenciados direta** , clique em seu dispositivo Android.
    
2. Na barra de tarefas, clique em **tarefas remotas > redefinição de senha**.
    
3. Sobre o **tarefa remota: redefinição de senha** solicitar, clique em **Sim**. Aguarde um minuto.
    
4. No painel de **Todos os dispositivos gerenciados direta** , clique em **Exibir propriedades**.
    
5. Em **Redefinição de senha**, observe a nova senha.
    
6. No seu dispositivo Android, insira a nova senha na tela de bloqueio.  
    
7. Para alterar a senha novamente, entram em **configurações**, toque em **dispositivo**, toque em **tela de bloqueio**, insira a nova senha novamente, toque em **bloqueio de tela**e sua escolha para a senha.
    
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="see-also"></a>Veja também

[O ambiente de desenvolvimento e teste da Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Políticas MAM para seu ambiente de desenvolvimento e teste da Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilidade corporativos + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


