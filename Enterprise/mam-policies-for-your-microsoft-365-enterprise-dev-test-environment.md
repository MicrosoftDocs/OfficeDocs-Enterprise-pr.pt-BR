---
title: "Políticas MAM para seu ambiente de desenvolvimento e teste da Microsoft 365 Enterprise"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "Resumo: Use este guia de laboratório de teste para adicionar políticas de gerenciamento (MAM) de aplicativo móvel do EMS ao seu ambiente de desenvolvimento e teste da Microsoft 365."
ms.openlocfilehash: d088970dca1ec55212642f16d0519e89bd9591e5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Políticas MAM para seu ambiente de desenvolvimento e teste da Microsoft 365 Enterprise

 **Resumo:** Use este guia de laboratório de teste para adicionar políticas de gerenciamento (MAM) de aplicativo móvel do EMS ao seu ambiente de desenvolvimento e teste da Microsoft 365.
  
O Microsoft Enterprise mobilidade + segurança (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Com as instruções deste artigo, você pode adicionar políticas de gerenciamento (MAM) do aplicativo móvel ao seu ambiente de desenvolvimento e teste da Microsoft 365.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Fase 1: Criar o seu ambiente de desenvolvimento e teste da Microsoft 365

Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Fase 2: Criar e implantar políticas de MAM para dispositivos iOS e Android

Nesta fase, você criará e implantará duas políticas de MAM diferentes: uma para dispositivos iOS e outra para dispositivos Android.
  
1. Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
2. Em uma nova guia do navegador, abra o portal do Windows Azure ([https://azure.portal.com](https://azure.portal.com)) e entrar usando sua conta de administrador global do Office 365.
    
3. Na guia Azure portal no Internet Explorer, no painel de navegação, clique em **mais serviços** (ou na seta à direita), digite **Intune**e clique em **Intune**.
    
4. No painel de navegação à esquerda, clique em **Grupos**.
    
5. No blade **usuários e grupos-All grupos** , clique em **Adicionar**.
    
6. No **grupo** blade, digite **gerenciados iOS usuários de dispositivo** em **nome**, selecione **atribuído** no **tipo de associação**, selecione **Sim** para **recursos do Office habilitar?**e clique em **criar**. 
    
7. Feche o blade de **grupo** .
    
8. No blade **usuários e grupos-All grupos** , clique em **Adicionar**.
    
9. No **grupo** blade, digite **os usuários de dispositivos Android gerenciados** em **nome**, selecione **atribuído** no **tipo de associação**, selecione **Sim** para **recursos do Office habilitar?**e clique em **criar**.
    
10. Feche o blade de **usuários e grupos-All grupos** .
    
11. No blade **Intune** , na lista de **Tarefas rápidas** , clique em **criar uma política de conformidade**.
    
12. No blade **Perfis de política de conformidade** , clique em **Criar diretiva**.
    
13. No blade **Criar política** , em **nome**, digite **iOS**. Na **plataforma**, selecione **iOS**, clique **Okey** no blade **iOS política de conformidade** e, em seguida, clique em **criar**.
    
14. No blade **Perfis de política de conformidade** , clique em **Criar diretiva**.
    
15. No blade **Criar política** , em **nome**, digite **Android**. Na **plataforma**, selecione **Android**, clique **Okey** no blade **política de conformidade Android** e, em seguida, clique em **criar**.
    
16. No blade **Perfis de política de conformidade** , clique no nome de política **Android** .
    
17. No painel de navegação à esquerda do blade **Android - propriedades** , clique em **atribuições**e, em seguida, clique em **Selecionar grupos**.
    
18. No blade **Selecionar grupos** , clique no grupo de **usuários de dispositivos Android gerenciada** e, em seguida, clique em **Selecionar**.
    
19. Clique em **Salvar**e feche o blade **Android - atribuições** .
    
20. No blade **Perfis de política de conformidade** , clique no nome de política de **iOS** .
    
21. No painel de navegação à esquerda do blade **iOS - propriedades** , clique em **atribuições**e, em seguida, clique em **Selecionar grupos**.
    
22. No blade **Selecionar grupos** , clique no grupo de **usuários de dispositivos iOS Managed** e, em seguida, clique em **Selecionar**.
    
23. Clique em **Salvar**e feche o blade **iOS - atribuições** .
    
24. Feche o blade **Perfis de política de conformidade** .
    
25. No blade **Intune** , clique em **Gerenciar aplicativos** no painel de navegação à esquerda.
    
26. No blade **Apps Mobile** , clique em **aplicativos**.
    
27. Na lista de aplicativos, clique em **PowerPoint**, 
    
28. No blade **Visão geral do PowerPoint** , clique em **atribuições > Selecione grupos > gerenciados dispositivos iOS > selecione**. Em **tipo**, selecione **disponível**e, em seguida, clique em **Salvar**.
    
29. Repita a etapa 28 para os seguintes aplicativos:
    
  - Outlook para Android
    
  - Word para iOS
    
  - Excel para iOS
    
  - Outlook para iOS
    
  - Microsoft Dynamics CRM no iPad para iOS
    
  - Microsoft Dynamics CRM no iPhone para iOS
    
  - Dynamics CRM para Telefones para Android
    
  - Dynamics CRM para Tablets para Android
    
  - Excel para Android
    
  - Word para Android
    
  - OneNote para iOS
    
30. Feche o blade **Mobile Apps - Apps** .
    
31. No blade **Apps Mobile** , clique em **Políticas de proteção de aplicativos**.
    
32. No blade **Políticas de proteção de aplicativos** , clique em **Adicionar uma política**.
    
33. No blade **Adicionar uma política** , digite **iOS**e clique em **Selecionar aplicativos necessários**.
    
34. No blade **Apps** , clique o **PowerPoint**, **O Microsoft Dynamics CRM no iPhone**, **Excel**, **O Microsoft Dynamics CRM no iPhone**, **Word**, **OneNote**e **Outlook**e clique em **Selecionar**.
    
35. No blade **Adicionar uma política** , clique em **criar**.
    
36. No blade **Políticas de proteção de aplicativos** , clique em **Adicionar uma política**.
    
37. No blade **Adicionar uma política** , digite **Android**, selecione **Android** na **plataforma**e clique em **Selecionar aplicativos necessários**.
    
38. No blade **Apps** , clique **Dynamics CRM para tablets**, **PowerPoint**, **Word**, **Excel**, **Outlook**e **Dynamics CRM para telefones**e, em seguida, clique em **Selecionar**.
    
39. No blade **Adicionar uma política** , clique em **criar**.
    
Agora, você tem duas políticas de MAM, uma para dispositivos iOS e outra para dispositivos Android, e está pronto para trabalhar com configurações de teste para os aplicativos selecionados.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="see-also"></a>See Also

[O ambiente de desenvolvimento e teste da Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Registrar o iOS e Android dispositivos em seu ambiente de desenvolvimento e teste do Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Adoção de nuvem Test Lab Guides (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilidade corporativos + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


