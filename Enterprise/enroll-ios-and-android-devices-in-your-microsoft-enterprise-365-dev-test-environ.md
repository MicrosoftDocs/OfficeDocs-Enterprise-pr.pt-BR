---
title: Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumo: Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.'
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188099"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise

 **Resumo:** Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.
  
O pacote de mobilidade do Microsoft Enterprise (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Se você precisar aplicar segurança no nível do dispositivo, você deve registrar os dispositivos em Microsoft Intune. Registro do dispositivo não apenas ajuda a gerenciar os dispositivos de propriedade da organização, mas também pessoal (BYOD) e dispositivos compartilhados, dependendo da sua organização do legal políticas.
  
Seguindo as instruções fornecidas neste artigo, você poderá registrar e testar recursos de gerenciamento de dispositivo móvel básica para dispositivos com Android e iOS em seu ambiente de desenvolvimento e teste da Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Fase 1: Crie seu ambiente de desenvolvimento e teste da Microsoft 365

Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Fase 2: Registrar seus dispositivos com Android e iOS

Primeiro, use as instruções em [instalar e acesse o aplicativo de Portal da empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar o aplicativo do Portal do Microsoft Intune empresa para seu locatário de desenvolvimento e teste.

Em seguida, use as instruções em [Configurar o acesso aos seus recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para registrar um dispositivo iOS.

Em seguida, use as instruções em [registrar seu dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para registrar um dispositivo Android.

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>Fase 2: Gerenciar seus dispositivos com Android e iOS remotamente

O Microsoft Intune fornece recursos de bloqueio e redefinição de senha remotos. Se alguém perder um dispositivo, você poderá bloqueá-lo remotamente. Se alguém se esquecer da senha, você poderá removê-la remotamente.
  
Para bloquear um dispositivo iOS remotamente:
  
1.  Abra uma nova guia e vá para http://manage.microsoft.com (se necessário). 

2.  No console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.

3. No painel **Grupos**, abra **Todos os dispositivos > Todos os dispositivos móveis > Todos os Dispositivos Gerenciados Diretamente**.
    
4. No painel **Todos os Dispositivos Gerenciados Diretamente**, clique na guia **Dispositivos**.
    
5. Na lista de dispositivos, clique no seu dispositivo iOS.  
    
6. No seu dispositivo iOS, certifique-se de que ele esteja na tela principal.  
    
7. No computador de administração, na barra de tarefas, clique em **Tarefas Remotas > Bloqueio Remoto**. Observe seu dispositivo iOS entrando na tela de bloqueio.
    
Para remover a senha:
  
1. No computador de administração, no painel **Todos os Dispositivos Gerenciados Diretamente**, clique na guia **Dispositivos**.
    
2. Na lista, clique no seu dispositivo iOS. Na barra de tarefas, clique em **Tarefas Remotas > Reconfiguração de Senha**. Aguarde um minuto.
    
3. No seu dispositivo iOS, desbloqueie-o e observe que uma senha não existe mais. Para alterar novamente a senha, vá para **Configurações** e depois para **Senha**.
    
Para bloquear um dispositivo Android remotamente:
  
1. No console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.
    
2. No painel **Grupos**, abra **Todos os dispositivos > Todos os dispositivos móveis > Todos os Dispositivos Gerenciados Diretamente**.
    
3. No painel **Todos os Dispositivos Gerenciados Diretamente**, clique na guia **Dispositivos**.
    
4. Na lista de dispositivos, clique no seu dispositivo Android.  
    
5. No seu dispositivo Android, certifique-se de que ele esteja na tela principal.  
    
6. No computador de administração, na barra de tarefas, clique em **Tarefas Remotas > Bloqueio Remoto**. Quando solicitado, clique em **Sim**.
    
7. Observe seu dispositivo Android entrando na tela de bloqueio.
    
Quando você redefinir a senha para dispositivos com Android, o portal de administração Intune gera e configura uma senha forte.
  
Para redefinir a senha remotamente:
  
1. No computador de administração, na guia do console de administração do Microsoft Intune do navegador, no painel **Todos os Dispositivos Gerenciados Diretamente**, clique no seu dispositivo Android.
    
2. Na barra de tarefas, clique em **Tarefas Remotas > Reconfiguração de Senha**.
    
3. No prompt **Tarefa Remota: Reconfiguração de Senha**, clique em **Sim**. Aguarde um minuto.
    
4. No painel **Todos os Dispositivos Gerenciados Diretamente**, clique em **Exibir Propriedades**.
    
5. Em **Reconfiguração de Senha**, anote a nova senha.
    
6. No seu dispositivo Android, insira a nova senha na tela de bloqueio.  
    
7. Para alterar novamente a senha, vá para **Configurações**, toque em **Dispositivo**, toque em **Tela de bloqueio**, insira novamente a nova senha, toque em **Bloqueio da tela** e depois na sua opção de senha.
    

> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="see-also"></a>Confira também

[Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilidade corporativos + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


