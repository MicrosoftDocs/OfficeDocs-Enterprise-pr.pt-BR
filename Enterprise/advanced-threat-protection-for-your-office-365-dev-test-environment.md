---
title: "Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365"
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
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "Resumo: Configurar e demonstrar a proteção de ameaça avançadas do Office 365 em seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: 00b1fc8fea930346f082d3d2302a14dea7ad4309
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365

 **Resumo:** Configurar e demonstrar a proteção de ameaça avançadas do Office 365 em seu ambiente de desenvolvimento e teste do Office 365.
  
O Office 365 avançadas ameaça proteção (ATP) é um recurso do Exchange Online Protection (EOP) que ajuda a manter o malware fora do seu email. Com ATP, você deve criar diretivas no Centro de administração do Exchange (EAC) ou a segurança &amp; Centro de conformidade que ajudam a garantir que seus usuários acessam apenas links ou anexos em emails que são identificadas como não mal-intencionado. Para obter mais informações, consulte [proteção contra ameaças avançadas para anexos seguros e links de seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Com as instruções neste artigo, você configurará e testará a ATP na sua assinatura de avaliação do Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Desenvolver seu ambiente de desenvolvimento e teste do Office 365 leve ou em uma empresa simulada

Se você quiser testar ATP de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar ATP em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> O teste da ATP não requer o ambiente de desenvolvimento e teste em uma empresa simulada, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do AD no Windows Server. Ele é fornecido aqui como uma opção para que você possa testar a ATP e fazer testes com ele em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Fase 2: Demonstrar o comportamento de entrega de email padrão do Office 365

Nesta fase, você demonstrará que, antes de configurar políticas de ATP, emails mal-intencionados são entregues às caixas de correio do Office 365 sem triagem ou mitigação.
  
1. Abra o Internet Explorer e entrar com a conta do Outlook que você criou na fase 2 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
    
  - Se estiver usando o ambiente de desenvolvimento e teste leve do Office 365, abra uma sessão particular do Internet Explorer e entre com o seu computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, use o [portal Azure](https://portal.azure.com) para conectar a máquina virtual CLIENT1 e entrar em CLIENT1.
    
2. Execute o Bloco de Notas e insira algum texto.
    
3. Salve o arquivo para a pasta de documentos como **getKeys.js**.
    
4. Na guia email do Outlook do Internet Explorer, clique em **novo**.
    
5. Na caixa **para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de avaliação.
    
6. Para o assunto, digite **suas novas chaves**.
    
7. No corpo, digite **que aqui está o arquivo**.
    
8. Clique em **Anexar**, clique duas vezes em **getKeys.js** na pasta documentos, clique em **Anexar como uma cópia**e, em seguida, clique em **Enviar**.
    
9. Clique em **novo**.
    
10. Na caixa **para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de avaliação.
    
11. Para o assunto, digite **New viajam o site da web**.
    
12. No corpo, digite **que alguém me encaminhadas neste site**.
    
13. No corpo, selecione o texto **deste site** e clique no ícone de hiperlink na barra de ferramentas.
    
14. Em **URL**, digite **http://www.spamlink.contoso.com/**, clique em **Okey**e, em seguida, clique em **Enviar**.
    
15. Abra uma instância separada do Internet Explorer no modo de navegação particular, vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
16. Na página principal do portal, clique no lado de aplicativos e, em seguida, clique em **email**.
    
17. Na caixa de entrada, clique na mensagem com o assunto **suas novas chaves**.
    
18. Na pasta Lixo eletrônico, clique na mensagem com o assunto **New viajam o site da web**. Dentro da mensagem, clique no link de **neste site** . Você deverá ver "Oops! Página do Internet Explorer não pôde encontrar spamlink.contoso.com.". Este é o resultado correto porque não há nenhuma página da web nesse local.
    
Observe que ambos esses emails potencialmente mal-intencionados foram entregue com êxito. O email de **suas novas chaves** pode conter malware não detectado e o usuário foi permitido a clicar no link potencialmente mal-intencionados no email **novo site da web de viagens** .
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Fase 3: Configurar políticas de anexo seguro e links seguros para a ATP

Nesta fase, você criará e configurará uma política de anexo seguro para impedir a entrega de emails com anexos possivelmente mal-intencionados e uma política de links seguros para impedir que os usuários acessem URLs possivelmente não seguras.
  
1. Na guia **Página inicial do Microsoft Office** do Internet Explorer, clique no lado do **Admin** .
    
2. No painel de navegação esquerdo, clique em **Admin centrais**e **Exchange**.
    
3. No painel de navegação à esquerda da guia Exchange admin center, clique em **Avançado de ameaças**.
    
4. Clique na guia **anexos seguros** e, em seguida, clique no sinal de adição.
    
5. Na janela **nova diretiva de segurança de anexos** , em **nome**, digite **Seguros política de anexo - bloco**.
    
6. **Resposta de malware desconhecido anexos seguros**, clique em **Bloquear**.
    
7. Para **redirecionar o anexo na detecção**, clique em **Habilitar redirecionamento** e digite o endereço de email da sua conta de administrador global do Office 365.
    
8. Para **aplicado a**, clique na seta e, em seguida, clique em **domínio do destinatário é**. Na janela, clique em nome de sua organização (por exemplo, contoso.onmicrosoft.com) e clique em **Okey**.
    
9. Clique em **Salvar**. Depois da atualização, você verá a nova e habilitado a **Política de anexo seguros - bloco**.
    
10. Clique na guia **links seguros** e, em seguida, clique no sinal de adição.
    
11. Na janela **nova política de links de seguros** , em **nome**, digite **Diretiva de Link seguros**.
    
12. Para **Selecionar a ação para URLs potencialmente mal-intencionados desconhecidos em mensagens**, clique **em**e selecione **não permitir aos usuários clicarem por meio de URL original**.
    
13. Para **aplicado a**, clique na seta e, em seguida, clique em **domínio do destinatário é**. Na janela, clique em nome de sua organização (por exemplo, contoso.onmicrosoft.com) e clique em **Okey**.
    
14. Clique em **Salvar**. Você verá a nova e habilitado para a **Política de Link seguros**.
    
## <a name="phase-4-show-atp-in-action"></a>Fase 4: Mostrar a ATP em ação

Nesta fase, você demonstrará como a ATP lida com emails potencialmente mal-intencionados.
  
1. Da instância do Internet Explorer que você usou para enviar o email na fase 2, no painel de navegação esquerdo, clique em **itens enviados.**
    
2. Clique em email intitulado **suas novas chaves**, clique no ícone de seta para baixo e clique em **Avançar**.
    
3. Da nova mensagem, na **para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de avaliação e, em seguida, clique em **Enviar**.
    
4. Clique em email intitulado **New viajam o site da web**, clique no ícone de seta para baixo, clique em **responder a todos**e clique em **Enviar**.
    
5. Da instância do Internet Explorer que você usou para configurar políticas de ATP na fase 3, clique na guia de Central de administração do Exchange, clique no lado de aplicativos e, em seguida, clique em **email**. Você deverá ver duas novas mensagens de email na caixa de entrada:
    
  - Um intitulado **firmware: suas novas chaves**
    
  - Um intitulado **firmware: novo site de viagens**
    
6. Abra a mensagem de email denominada **firmware: novo site de viagens** e clique no link **neste site** . Você deverá ver uma página "Este site tiver sido classificado como sendo maliciosas.". Isso demonstra que ATP está impedindo acessem o site da web potencialmente mal-intencionados.
    
7. No Exchange admin center guia do Internet Explorer, no painel de navegação esquerdo, clique em **fluxo de emails**.
    
8. Clique na guia **rastreamento de mensagem** e clique em **Pesquisar**.
    
9. Na janela de **Resultados de rastreamento de mensagem** , clique duas vezes a mensagem com o assunto **suas novas chaves**. Essa mensagem foi entregue com êxito para a caixa de entrada. Feche essa janela.
    
10. Clique duas vezes a mensagem com o assunto **New viajam o site da web**. Essa mensagem foi entregue com êxito para a caixa de entrada. Feche essa janela.
    
11. Clique duas vezes a mensagem com o assunto **firmware: suas novas chaves**. Observe como esta mensagem foi processada pelo ATP e, em seguida, entregue à caixa de entrada. Feche essa janela.
    
    > [!NOTE]
    > A finalidade da diretiva de segurança de anexos era começar a verificação de anexos para código mal-intencionado. O anexo getKeys.js foi permitido porque não foi determinado mal-intencionados. Esta etapa mostra que ATP executa um exame do anexo. 
  
12. Clique duas vezes a mensagem com o assunto **firmware: novo site de viagens**. Observe que essa mensagem foi entregue com êxito para a caixa de entrada.
    
Agora, você pode usar esse ambiente para criar novas políticas e fazer testes com a ATP.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="see-also"></a>See Also

[Adoção de nuvem Test Lab Guides (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento e teste de configuração de base](base-configuration-dev-test-environment.md)
  
[Ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md) 

[Proteção contra ameaças avançadas para anexos seguros e links de seguros](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


