---
title: Sincronização de diretório do ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Resumo: Configure a sincronização de diretórios do ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: 209b41e4d695a753867d989b8f27b96618a81303
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a>Sincronização de diretório do ambiente de desenvolvimento/teste do Office 365

 **Resumo:** Configure a sincronização de diretórios do ambiente de desenvolvimento/teste do Office 365.
  
Muitas organizações usam o Azure AD Connect e a sincronização de diretório para sincronizar o conjunto de contas em sua floresta local do Windows Server Active Directory (AD) com o conjunto de contas no Office 365. Este artigo descreve como você pode adicionar a sincronização de diretório com a sincronização de hash de senha para o ambiente de desenvolvimento/de teste do Office 365, resultando na seguinte configuração.
  
![Ambiente de desenvolvimento/de teste do Office 365 com a sincronização de diretório](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Esta configuração consiste em: 
  
- Uma assinatura de avaliação do Office 365 E5, que expira 30 dias depois de você criá-la.
- Uma intranet de organização simplificada conectada à Internet, que consiste em três máquinas virtuais em uma sub-rede de uma rede virtual do Azure (DC1 APP1 e CLIENT1). O Azure AD Connect é executado no APP1 para sincronizar o domínio do Windows Server AD com o Office 365.
    
Há duas fases para configurar esse ambiente de desenvolvimento/ de teste:
  
1. Crie um ambiente de desenvolvimento/de teste do Office 365 (as máquinas virtuais do DC1, APP1 e CLIENT1 em uma rede virtual do Azure com uma assinatura de avaliação do Office 365 E5).
2. Instale e configure o Azure AD Connect no APP1.
    
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>Fase 1: Criar um ambiente de desenvolvimento/de teste do Office 365

Siga as instruções nas fases 1, 2 e 3 do artigo [Ambiente de desenvolvimento/de teste do Office 365](office-365-dev-test-environment.md). Aqui está a configuração resultante.
  
![O ambiente de desenvolvimento/teste do Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Esta configuração consiste em: 
  
- Uma assinatura de avaliação do Office 365 E5.
- Uma intranet de organização simplificada conectado à Internet, que consiste em máquinas virtuais do DC1 APP1 e CLIENT1 em uma sub-rede de uma rede virtual do Azure.
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>Fase 2: Instalar o Azure AD Connect no APP1

Depois de instalado e configurado, o Azure AD Connect sincroniza o conjunto de contas no domínio CORP do Windows Server AD com o conjunto de contas de assinatura de avaliação do Office 365. O procedimento a seguir orientará a instalação do Azure AD Connect no APP1 e a confirmação de seu bom funcionamento.
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>Instalar e configurar o Azure AD Connect no APP1

1. Do [portal do Azure](https://portal.azure.com), conecte-se ao APP1 com a conta CORP\\Usuário1.
    
2. Do APP1, abra um prompt de comando do nível de administrador do Windows PowerShell e execute estes comandos:
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. Na barra de tarefas, clique em **Internet Explorer** e acesse [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. Na página do Microsoft Azure Active Directory Connect, clique em **Baixar** e, em seguida, clique em **Executar**.
    
5. Na página **Bem-vindo ao Azure AD Connect**, clique em **Concordo** e, em seguida, **Continuar**.
    
6. Na página **Configurações Expressas**, clique em **Usar configurações expressas**.
    
7. Na página **Conectar-se ao Azure AD**, digite o nome de sua conta de administrador global em **Nome de usuário**, digite a sua senha em **Senha** e clique em **Avançar**.
    
8. Na página **Conectar-se ao AD DS**, digite **CORP\\Usuárior1** em **Nome de usuário,** digita a senha em **Senha** e clique em **Avançar**.
    
9. Na página **Configuração de entrada do Azure AD**, clique em **Continuar sem domínio verificado** e depois em **Avançar**.
    
10. Na página **Pronto para configurar**, clique em **Instalar**.
    
11. Na página **Configuração concluída**, clique em **Sair**.
    
12. No Internet Explorer, vá ao portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entre na sua assinatura de avaliação do Office 365 com a sua conta de administrador global.
    
13. Na página principal do portal, clique em **Admin**.
    
14. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
    Observe a conta denominada **Usuário1**. Essa conta fica no domínio CORP do Windows Server AD e é prova que a sincronização de diretórios funcionou.
    
15. Clique na conta **Usuário1**. Para licenças de produto, clique em **Editar**.
    
16. Em **Licenças de produto**, selecione o seu país/região e, em seguida, clique no controle **Desativado** para **Office 365 Enterprise E5** (mudando-o para **Ativado**). Clique em **Salvar** na parte inferior da página e clique em **Fechar**.
    
Esta é a configuração resultante.
  
![Ambiente de desenvolvimento/de teste do Office 365 com a sincronização de diretório](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Esta configuração consiste em: 
  
- Uma assinatura de avaliação do Office 365 E5.
- Uma intranet de organização simplificada conectada à Internet, que consiste nas máquinas virtuais DC1, APP1 e CLIENT1 em uma sub-rede de uma rede virtual do Azure. O Azure AD Connect é executado no APP1 para sincronizar o domínio CORP do Windows Server AD com o Office 365 a cada 30 minutos.
    
## <a name="next-step"></a>Próxima etapa

Quando estiver pronto para implantar a sincronização de diretório da sua organização, confira [Implantar a sincronização de diretório do Office 365 no Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).

## <a name="see-also"></a>Veja também

[Guias de laboratório de teste (TLGs) da adoção da nuvem](cloud-adoption-test-lab-guides-tlgs.md)
[Ambiente de desenvolvimento/de teste de configuração base](base-configuration-dev-test-environment.md)
[Ambiente de desenvolvimento/de teste do Office 365](office-365-dev-test-environment.md)
[Cloud App Security para o seu ambiente de desenvolvimento/de teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
[Proteção avançada contra ameaças para o seu ambiente de desenvolvimento/de teste do Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Adoção da nuvem e as soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




