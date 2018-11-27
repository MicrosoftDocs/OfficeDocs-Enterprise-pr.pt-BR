---
title: Preparar um domínio não roteáveis para sincronização de diretórios
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Saiba o que fazer se você tiver um domínio não-routale associado com os usuários no local antes de sincronizar com o Office 365.
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674435"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Preparar um domínio não roteáveis para sincronização de diretórios
Quando você sincronizar seu diretório local com o Office 365, você precisa ter um domínio verificado no Azure Active Directory. Somente o usuário Principal nomes (UPN) que estão associados ao domínio local são sincronizados. No entanto, qualquer UPN que contém um domínio não roteáveis, por exemplo. local (como billa@contoso.local), será sincronizada com uma. domínio onmicrosoft.com (como billa@contoso.onmicrosoft.com). 

Se você usar atualmente um domínio. local para suas contas de usuário no Active Directory, é recomendável que você alterá-las para usar um domínio verificado (como billa@contoso.com) para sincronizar corretamente no seu domínio do Office 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>E se eu tiver apenas um domínio de local. local?

A ferramenta mais recente, que você pode usar para sincronizar seu Active Directory para o Windows Azure Active Directory é nomeada Connect do Azure AD. Para obter mais informações, consulte [integrando suas identidades no local com o Windows Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Conectar do Azure AD sincroniza UPN e a senha dos usuários para que os usuários podem assinar com as mesmas credenciais que usam o local. No entanto, Connect do Azure AD sincroniza somente os usuários a domínios que são verificados pelo Office 365. Isso significa que o domínio também sejam verificado pelo Windows Azure Active Directory porque identidades do Office 365 são gerenciadas pelo Windows Azure Active Directory. Em outras palavras, o domínio deve ser um domínio da Internet válido (por exemplo, .com,. org, .net,. us, etc.). Se o seu Active Directory interna usa apenas um domínio não roteáveis (por exemplo,. local), isso possivelmente não pode corresponder ao domínio verificado que você tiver no Office 365. Para resolver esse problema alterando seu domínio primário no seu Active Directory local ou adicionando um ou mais sufixos de nome UPN.
  
### <a name="change-your-primary-domain"></a>**Alterar seu domínio primário**

Altere seu domínio primário para um domínio que você tiver verificado no Office 365, por exemplo, contoso.com. Cada usuário que possui a Contoso do domínio é atualizado para contoso.com. Para obter instruções, consulte [Como o domínio renomear funciona](https://go.microsoft.com/fwlink/p/?LinkId=624174). No entanto, esse é um processo muito envolvido, e uma solução mais fácil é [sufixos de UPN adicionar e atualizar seus usuários a eles](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), conforme mostrado na seção a seguir.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Adicionar sufixos UPN e atualizar seus usuários a eles**

Você pode resolver o problema. local registrando novo sufixo UPN ou sufixos no Active Directory para corresponder ao domínio (ou domínios) verificado no Office 365. Após registrar o novo sufixo, você pode atualizar o usuário UPNs substituir. o local com o novo nome de domínio, por exemplo, para que uma conta de usuário se parece com billa@contoso.com.
  
Depois de ter atualizado os UPNs para usar ao domínio verificado, você estará pronto para sincronizar seu Active Directory no local com o Office 365.
  
 **Etapa 1: Adicionar o novo sufixo UPN**
  
1. No servidor que executa o serviços de domínio Active Directory (AD DS), no Gerenciador de servidores escolher **Ferramentas** \> **domínios do Active Directory e relações de confiança**.
    
    **Ou, se você não tiver o Windows Server 2012**
    
    Pressione a **tecla do Windows + R** para abrir a caixa de diálogo **Executar** e digite msc e escolha **Okey**.
    
    ![Escolha domínios do Active Directory e relações de confiança.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Na janela de **domínios do Active Directory e relações de confiança** , do mouse em **domínios do Active Directory e relações de confiança**e escolha **Propriedades**.
    
    ![Clique com o botão ActiveDirectory domínios e relações de confiança e escolha Propriedades](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Na guia **Sufixos UPN** , na caixa **Sufixos de nome UPN alternativo** , digite seu novo sufixo UPN ou sufixos e escolha **Adicionar** \> **Aplicar**.
    
    ![Adicionar um novo sufixo UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Escolha **Okey** quando você terminar de adicionar sufixos. 
    
 **Etapa 2: Alterar o sufixo UPN para usuários existentes**
  
1. No servidor que executa o serviços de domínio Active Directory (AD DS), no Gerenciador de servidores escolher **Ferramentas** \> **e computadores do Active Directory Active Directory Users**.
    
    **Ou, se você não tiver o Windows Server 2012**
    
    Pressione a **tecla do Windows + R** para abrir a caixa de diálogo **Executar** e digite DSA. msc e clique em **Okey**
    
2. Selecione um usuário, com o botão direito e escolha **Propriedades**.
    
3. Na guia **conta** , na lista suspensa sufixo UPN, escolha Novo sufixo UPN e escolha **Okey**.
    
    ![Adicionar um novo sufixo UPN de um usuário](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Conclua estas etapas para cada usuário.
    
    Como alternativa você pode atualizar em massa sufixos de UPN [você também pode usar o Windows PowerShell para alterar o sufixo UPN para todos os usuários](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Você também pode usar o Windows PowerShell para alterar o sufixo UPN para todos os usuários**

Se você tiver muitos usuários para atualizar, é mais fácil usar o Windows PowerShell. O exemplo a seguir usa os cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) e [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) para alterar todos os sufixos de Contoso para contoso.com. 

Execute os seguintes comandos do Windows PowerShell para atualizar todos os sufixos de Contoso para contoso.com:
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
Consulte o [módulo do Active Directory Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=624314) para saber mais sobre como usar o Windows PowerShell no Active Directory. 

