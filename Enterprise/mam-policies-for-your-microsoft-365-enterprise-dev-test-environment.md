---
title: Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 'Resumo: Use este guia de laboratório de teste para adicionar políticas de gerenciamento (MAM) de aplicativo móvel do EMS ao seu ambiente de desenvolvimento e teste da Microsoft 365.'
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188149"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise

 **Resumo:** Use este guia de laboratório de teste para adicionar políticas de gerenciamento (MAM) de aplicativo móvel do EMS ao seu ambiente de desenvolvimento e teste da Microsoft 365.
  
O Microsoft Enterprise mobilidade + segurança (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Com as instruções deste artigo, você pode adicionar políticas de gerenciamento (MAM) do aplicativo móvel ao seu ambiente de desenvolvimento e teste da Microsoft 365.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Fase 1: Criar o seu ambiente de desenvolvimento e teste da Microsoft 365

Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Fase 2: Criar e implantar políticas de MAM para dispositivos iOS e Android

Nesta fase, você criará e implantará duas políticas de MAM diferentes: uma para dispositivos iOS e outra para dispositivos Android.
  
1. Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e se conectar à sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
2. Em uma nova guia do navegador, abra o portal do Windows Azure ([https://azure.portal.com](https://azure.portal.com)) e entrar usando sua conta de administrador global do Office 365.
    
3. Na guia Azure portal no Internet Explorer, no painel de navegação, clique em **todos os serviços**, digite **Intune**e, em seguida, clique em **Intune**.
    
4. No painel de navegação à esquerda, clique em **Grupos**.
    
5. No blade **grupos-All grupos** , clique em **+ novo grupo**.
    
6. No **grupo** blade, selecione **Office 365** para **tipo de grupo?**, digite **gerenciados iOS usuários de dispositivo** em **nome**, selecione **atribuído** no **tipo de associação**e, em seguida, clique em **criar**. 
    
7. Feche a folha **Grupo**.
    
8. No blade **grupos-All grupos** , clique em **Adicionar**.
    
9. No **grupo** blade, selecione **Office 365** para **tipo de grupo?**, digite **gerenciados Android usuário de dispositivo** em **nome**, selecione **atribuído** no **tipo de associação**e, em seguida, clique em **criar**.
    
10. Feche o blade **grupos grupos a todos** .
    
11. Na folha **Intune**, na lista **Tarefas rápidas**, clique em **Crie uma política de conformidade**.
    
12. Na folha **Perfis de Políticas de Conformidade**, clique em **Criar Política**.
    
13. Na folha **Criar Política**, em **Nome**, digite **iOS**. Em **Plataforma**, selecione **iOS**, clique em **OK** na folha **Política de conformidade do iOS** e depois clique em **Criar**.
    
14. Na folha **Perfis de Políticas de Conformidade**, clique em **Criar Política**.
    
15. Na folha **Criar Política**, em **Nome**, digite **Android**. Em **Plataforma**, selecione **Android**, clique em **OK** na folha **Política de conformidade do Android** e depois clique em **Criar**.
    
16. Na folha **Perfis de Políticas de Conformidade**, clique no nome da política **Android**.
    
17. Na navegação à esquerda da folha **Android - Propriedades**, clique em **Atribuições** e depois em **Grupos selecionados**.
    
18. Na folha **Grupos selecionados**, clique no grupo **Usuários de dispositivos Android gerenciados** e depois clique em **Selecionar**.
    
19. Clique em **Salvar**e feche o blade **Android - atribuições** .
    
20. Na folha **Perfis de Políticas de Conformidade**, clique no nome da política **iOS**.
    
21. Na navegação à esquerda da folha **iOS - Propriedades**, clique em **Atribuições** e depois em **Grupos selecionados**.
    
22. Na folha **Grupos selecionados**, clique no grupo **Usuários de dispositivos iOS gerenciados** e depois clique em **Selecionar**.
    
23. Clique em **Salvar**e feche o blade **iOS - atribuições** .
    
24. Feche a folha **Perfis de Políticas de Conformidade**.
    
25. Na folha **Intune**, clique em **Gerenciar aplicativos** na navegação à esquerda.
    
26. Na folha **Aplicativos Móveis**, clique em **Aplicativos**.
    
27. Na lista de aplicativos, clique em **PowerPoint**,  
    
28. Na folha **Visão Geral do PowerPoint**, clique em **Atribuições > Selecionar grupos > Dispositivos iOS gerenciados > Selecionar**. Em **Tipo**, selecione **Disponível** e clique em **Salvar**.
    
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
    
30. Feche a folha **Aplicativos Móveis - Aplicativos**.
    
31. Na folha **Aplicativos Móveis**, clique em **Políticas de Proteção de Aplicativo**.
    
32. Na folha **Políticas de Proteção de Aplicativo**, clique em **Adicionar uma política**.
    
33. Na folha **Adicionar uma política**, digite **iOS** e clique em **Selecionar aplicativos necessários**.
    
34. Na folha **Aplicativos**, clique em **PowerPoint**, **Microsoft Dynamics CRM no iPhone**, **Excel**, **Microsoft Dynamics CRM no iPhone**, **Word**, **OneNote** e **Outlook** e depois clique em **Selecionar**.
    
35. Na folha **Adicionar uma política**, clique em **Criar**.
    
36. Na folha **Políticas de Proteção de Aplicativo**, clique em **Adicionar uma política**.
    
37. Na folha **Adicionar uma política**, digite **Android**, selecione **Android** em **Plataforma** e clique em **Selecionar aplicativos necessários**.
    
38. Na folha **Aplicativos**, clique em **PowerPoint**, **Dynamics CRM para tablets**, **Excel**, **Word**, **Outlook** e **Dynamics CRM para telefones**. Em seguida, clique em **Selecionar**.
    
39. Na folha **Adicionar uma política**, clique em **Criar**.
    
Agora, você tem duas políticas de MAM, uma para dispositivos iOS e outra para dispositivos Android, e está pronto para trabalhar com configurações de teste para os aplicativos selecionados.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="see-also"></a>Confira também

[Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilidade corporativos + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


