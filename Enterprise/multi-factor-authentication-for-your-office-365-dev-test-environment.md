---
title: "A autenticação multifator para seu ambiente de desenvolvimento e teste do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "Resumo: Configure a autenticação multifator usando mensagens de texto enviadas a um telefone inteligente em um ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: 23c5aa4e205937899cac813b3b39780c989a1073
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>A autenticação multifator para seu ambiente de desenvolvimento e teste do Office 365

 **Resumo:** Configure a autenticação multifator usando mensagens de texto enviadas a um telefone inteligente em um ambiente de desenvolvimento e teste do Office 365.
  
Para um nível adicional de segurança para entrar em sua assinatura do Office 365, você pode habilitar a autenticação multifator Azure, que requer mais do que apenas um nome de usuário e uma senha para verificar uma conta. Com a autenticação multifator para o Office 365, os usuários são necessários para reconhecer uma chamada telefônica, digite um código de verificação enviado em uma mensagem de texto ou especificar uma senha de app em seus telefones inteligentes após inserir corretamente suas senhas. Eles podem entrar somente depois que esse segundo fator de autenticação foram atendido. 
  
Este artigo descreve como habilitar e testar a autenticação baseada em mensagens de texto de uma conta específica do Office 365.
  
Há duas fases para configurar a autenticação multifator para o Office 365 em um ambiente de desenvolvimento e teste:
  
1. Crie o ambiente de desenvolvimento e teste do Office 365.
    
2. Habilitar e testar a autenticação multifator para a conta de usuário 2.
    
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada

Se você deseja testar a autenticação multifator de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você deseja testar a autenticação multifator em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testar a autenticação multifator não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa testar a autenticação multifator e experimentar em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Fase 2: Habilitar e testar a autenticação multifator para a conta de usuário 2

Habilite a autenticação multifator para a conta de usuário 2 com estas etapas:
  
1. Abra uma instância separada do navegador, vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e então entrar com sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
2. Na página principal do portal, clique em **Admin**.
    
3. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
4. No painel de usuários ativos, clique em **mais > instalação Azure multi-factor auth**.
    
5. Na lista, clique na conta de **usuário 2** .
    
6. Na seção **2 do usuário** , em **etapas rápidas**, clique em **Habilitar**.
    
7. Na caixa de diálogo **sobre como habilitar a autenticação multifator** , clique em **Habilitar a autenticação multifator**.
    
8. Na caixa de diálogo **atualizar com êxito** , clique em **Fechar**.
    
9. Na guia **Página inicial do Microsoft Office** , clique no ícone de conta de usuário no canto superior direito e clique em **Sair**.
    
10. Feche sua instância do navegador.
    
Conclua a configuração da conta do usuário 2 a usar uma mensagem de texto para validação e testá-lo com estas etapas:
  
1. Abra uma nova instância do navegador.
    
2. Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e o logon com a conta de usuário 2 (Usuário2 @\<nome da organização >. onmicrosoft.com) e a senha.
    
3. Depois de entrar, você precisará configurar a conta para a validação de segurança adicionais. Clique em **montá-lo agora**.
    
4. Na página **verificação de segurança adicionais** :
    
  - Selecione seu país ou região.
    
  - Digite o número de telefone do telefone inteligente que receberá mensagens de texto.
    
  - Selecione **Enviar-me um código de mensagem de texto**.
    
5. Clique em **contato me**.
    
6. Insira o código de verificação da mensagem de texto recebida no seu telefone inteligente e clique em **Verificar**.
    
7. Sobre o **etapa 3: mantenha seus aplicativos existentes** página, registre a senha do aplicativo exibido para a conta de usuário 2 em um local seguro e clique em **concluído**.
    
8. Volta na página de entrada, digite a senha para a conta de usuário 2 e clique em **entrar**.
    
9. Insira o código de verificação da mensagem de texto recebida no seu telefone inteligente e, em seguida, clique em **entrar**.
    
10. Se essa for a primeira vez você entrou com a conta de usuário 2, você será solicitado alterar a senha. Digite a senha original e uma nova senha duas vezes e, em seguida, clique em **Atualizar senha e entrar**. Registre a nova senha em um local seguro.
    
    Você deverá ver o portal do Office 365 para o usuário 2.
    
## <a name="see-also"></a>Veja também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento e teste de configuração de base](base-configuration-dev-test-environment.md)
  
[Ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Planejar a autenticação multifator para implantações do Office 365](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

