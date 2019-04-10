---
title: Autenticação multifator para o ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Resumo: Configure a autenticação multifator usando mensagens de texto enviadas a um telefone inteligente em um ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: 091b82132b407cfd25b18c3ba8e424e29df58910
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741217"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Autenticação multifator para o ambiente de desenvolvimento/teste do Office 365

 **Resumo:** Configurar a autenticação multifator usando mensagens de texto enviadas a um telefone inteligente em um ambiente de desenvolvimento/teste do Office 365.
  
Para obter um nível adicional de segurança para entrar em sua assinatura do Office 365, você pode habilitar a autenticação multifator do Azure, que requer mais do que apenas um nome de usuário e senha para autenticar uma conta. Com a autenticação multifator para o Office 365, os usuários precisam confirmar uma chamada telefônica, digitar um código de verificação enviado em uma mensagem de texto ou especificar uma senha de aplicativo em telefones inteligentes depois de inserir corretamente suas senhas. O acesso só será possível depois que esse segundo fator de autenticação for atendido. 
  
Este artigo descreve como habilitar e testar a autenticação baseada em mensagem de texto para uma conta específica do Office 365.
  
Há duas fases para configurar a autenticação multifator para o Office 365 em um ambiente de desenvolvimento/teste:
  
1. Criação do ambiente de desenvolvimento/teste do Office 365.
    
2. Habilite e teste a autenticação multifator para a conta do usuário 2.
    
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa Visual para todos os artigos da pilha do guia do laboratório de teste do Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada

Se você só quiser testar a autenticação multifator de forma leve com os requisitos mínimos, siga as instruções nas fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar a autenticação multifator em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testar a autenticação multifator não requer o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta dos serviços de domínio Active Directory (AD DS). É fornecida aqui como uma opção para que você possa testar a autenticação multifator e experimentá-la em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Fase 2: habilitar e testar a autenticação multifator para a conta do usuário 2

Habilite a autenticação multifator para a conta do usuário 2 com estas etapas:
  
1. Abra uma instância separada do navegador, vá para o portal do Office 365 ([https://www.office.com](https://www.office.com)) e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
2. Na página principal do portal, clique em **Admin**.
    
3. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
4. No painel usuários ativos, clique em **mais > configuração de autenticação**multifator.
    
5. Na lista, selecione a conta do **usuário 2** .
    
6. Na seção **usuário 2** , em **etapas rápidas**, clique em **habilitar**.
    
7. Na caixa de diálogo **sobre como habilitar a autenticação** multifator, clique em **habilitar autenticação**multifator.
    
8. Na caixa de diálogo **atualizações com êxito** , clique em **fechar**.
    
9. Na guia **Microsoft Office Home** , clique no ícone da conta de usuário no canto superior direito e clique em **** sair.
    
10. Feche a instância do navegador.
    
Conclua a configuração da conta do usuário 2 para usar uma mensagem de texto para validação e testá-la com estas etapas:
  
1. Abra uma nova instância do navegador.
    
2. Vá para o portal do Office 365[https://www.office.com](https://www.office.com)() e entre com a conta do usuário 2 (Usuário2\<@ Organization name>. onmicrosoft. com) e a senha.
    
3. Após entrar, você será solicitado a configurar a conta para a validação de segurança adicional. Clique em **Configurar agora**.
    
4. Na página **verificação de segurança adicional** :
    
  - Selecione seu país ou região.
    
  - Digite o número de telefone do telefone inteligente que receberá mensagens de texto.
    
  - em **método**, clique em **enviar um código por mensagem de texto**.
    
5. Clique em **Avançar**.
    
6. Insira o código de verificação da mensagem de texto recebida no telefone inteligente e clique em **verificar**.
    
7. Na página **etapa 3: manter seus aplicativos existentes** , registre a senha do aplicativo exibida para a conta do usuário 2 em um local seguro e clique em **concluído**.
    
8. Se esta é a primeira vez que você entrou com a conta de usuário 2, você é solicitado a alterar a senha. Digite a senha original e uma nova senha duas vezes e clique em **Atualizar senha e entrar**. Registre a nova senha em um local seguro.
    
    Você deve ver o portal do Office 365 para o usuário 2 na guia **Microsoft Office Home** do navegador.
    
## <a name="see-also"></a>Confira também


[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento/teste para a Configuração Base](base-configuration-dev-test-environment.md)
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Plano para a autenticação multifator para Implantações do Office 365](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

