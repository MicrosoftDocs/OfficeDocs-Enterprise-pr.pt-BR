---
title: Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumo: Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720407"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise

 **Resumo:** Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.
  
O pacote de mobilidade do Microsoft Enterprise (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Se você precisar aplicar segurança no nível do dispositivo, você deve registrar os dispositivos em Microsoft Intune. Registro do dispositivo não apenas ajuda a gerenciar os dispositivos de propriedade da organização, mas também pessoal (BYOD) e dispositivos compartilhados, dependendo da sua organização do legal políticas.
  
Seguindo as instruções fornecidas neste artigo, você poderá registrar e testar recursos de gerenciamento de dispositivo móvel básica para dispositivos com Android e iOS em seu ambiente de desenvolvimento e teste da Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Fase 1: Crie seu ambiente de desenvolvimento e teste da Microsoft 365

Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Fase 2: Registrar seus dispositivos com Android e iOS

Primeiro, use as instruções em [instalar e acesse o aplicativo de Portal da empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar o aplicativo Microsoft Intune Portal da empresa para o seu ambiente de teste.

Em seguida, use as instruções em [Configurar o acesso aos seus recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para registrar um dispositivo iOS.

Em seguida, use as instruções em [registrar seu dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para registrar um dispositivo Android.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Fase 3: Gerenciar seus dispositivos com Android e iOS remotamente

Microsoft Intune fornece recursos de redefinição de bloqueio remoto e uma senha. Se alguém perder seus dispositivos, você pode bloquear o dispositivo remotamente. Se alguém esquecer sua senha, é possível redefini-lo remotamente.
  
Para bloquear um dispositivo Android ou o iOS remotamente:

1. Entrar no portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com) com as credenciais da sua conta de administrador global.
2. Clique em **todos os serviços**, digite **Intune**e clique em **Intune**.
3. Clique em **dispositivos > todos os dispositivos**.
4. Na lista de dispositivos, clique em um iOS ou um dispositivo Android e, em seguida, clique na ação de **bloqueio remoto** .

    
Para redefinir a senha remotamente:

1. Se necessário, entrar no portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com) com as credenciais da sua conta de administrador global.
2. Clique em **todos os serviços**, digite **Intune**e clique em **Intune**.
3. Clique em **dispositivos > todos os dispositivos**.
4. Da lista de dispositivos você gerenciar, clique em um iOS ou um dispositivo Android e escolha **… Mais**. Escolha a ação remota dispositivo **Remover a senha** .

Experimentação adicionais, consulte [ações de dispositivo disponível](https://docs.microsoft.com/intune/device-management#available-device-actions).

    

> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="see-also"></a>Confira também

[Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilidade corporativos + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


