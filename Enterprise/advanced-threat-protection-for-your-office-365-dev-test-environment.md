---
title: Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Resumo: Configure e demonstre a Proteção Avançada contra Ameaças do Office 365 no seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: e3efe339550992fba85509cd07a791d916d5d6e7
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030555"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Proteção Avançada contra Ameaças para o ambiente de desenvolvimento/teste do Office 365

 **Resumo:** Configure e demonstre a Proteção Avançada contra Ameaças do Office 365 no seu ambiente de desenvolvimento e teste do Office 365.
  
A Proteção Avançada contra Ameaças (ATP) do Office 365 é um recurso da Proteção do Exchange Online (EOP) que ajuda a evitar malware em emails. Com ATP, você cria políticas no centro de administração do Exchange (Eat) ou no &amp; centro de conformidade de segurança que ajuda a garantir que seus usuários acessem apenas links ou anexos em emails identificados como não mal-intencionados. Para obter mais informações, consulte [proteção avançada contra ameaças para anexos seguros e links seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Com as instruções neste artigo, você configurará e testará a ATP na sua assinatura de avaliação do Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Desenvolver seu ambiente de desenvolvimento e teste do Office 365 leve ou em uma empresa simulada

Se você só quiser testar a ATP de uma maneira leve com os requisitos mínimos, siga as instruções nas fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar a ATP em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> O teste de ATP não exige o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta dos serviços de domínio Active Directory (AD DS). Ele é fornecido aqui como uma opção para que você possa testar a ATP e fazer testes com ele em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Fase 2: demonstrar o comportamento padrão de entrega de email do Office 365

Nesta fase, você demonstrará que, antes de configurar políticas de ATP, emails mal-intencionados são entregues às caixas de correio do Office 365 sem triagem ou mitigação.
  
1. Abra o Internet Explorer e entre na conta do Outlook que você criou na fase 2 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
    
  - Se estiver usando o ambiente de desenvolvimento e teste leve do Office 365, abra uma sessão particular do Internet Explorer e entre com o seu computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, use o [portal do Azure](https://portal.azure.com) para se conectar à máquina virtual do CLIENT1 e, em seguida, entre no CLIENT1.
    
2. Execute o Bloco de Notas e insira algum texto.
    
3. Salve o arquivo na pasta Documentos como **getKeys.js**.
    
4. Na guia Email do Outlook do Internet Explorer, clique em **Novo**.
    
5. Em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste.
    
6. Para o assunto, digite **Suas novas chaves**.
    
7. No corpo, digite **Aqui está o arquivo**.
    
8. Clique em **Anexar**, clique duas vezes em **getKeys.js** na pasta Documentos, clique em **Anexar como cópia** e depois clique em **Enviar**.
    
9. Clique em **Novo**.
    
10. Em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste.
    
11. Para o assunto, digite **Novo site de viagem**.
    
12. No corpo, digite **Alguém me encaminhou este site**.
    
13. No corpo, selecione o texto **este site** e clique no ícone de hiperlink na barra de ferramentas.
    
14. Em **URL**, digite **https://www.spamlink.contoso.com/**, clique em **OK**e, em seguida, clique em **Enviar**.
    
15. Abra uma instância separada do Internet Explorer no modo de navegação privada, vá para o centro de administração do[https://admin.microsoft.com](https://admin.microsoft.com)Microsoft 365 () e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
16. Na página principal do portal, clique no bloco Aplicativos e depois em **Email**.
    
17. Em Caixa de Entrada, clique na mensagem com o assunto **Suas novas chaves**.
    
18. Na pasta lixo eletrônico, clique na mensagem com o assunto **novo site da Web da viagem**. Na mensagem, clique no link **este site** . Você verá um "Opa! O Internet Explorer não pôde encontrar spamlink.contoso.com. " da. Este é o resultado correto porque não há nenhuma página da Web nesse local.
    
Observe que ambos os emails potencialmente mal-intencionados foram entregues com êxito. O email **Suas novas chaves** poderia conter malware não detectado, e o usuário poderia clicar no link possivelmente mal-intencionado no email **Novo site de viagem**.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Fase 3: Configurar políticas de anexo seguro e links seguros para a ATP

Nesta fase, você criará e configurará uma política de anexo seguro para impedir a entrega de emails com anexos possivelmente mal-intencionados e uma política de links seguros para impedir que os usuários acessem URLs possivelmente não seguras.
  
1. Na guia **Microsoft Office Home** do Internet Explorer, clique no bloco **administrador** .
    
2. Na navegação à esquerda, clique em **Centros de administração** e depois em **Exchange**.
    
3. Na navegação à esquerda da guia Centro de administração do Exchange, clique em **ameaças avançadas**.
    
4. Clique na guia **anexos seguros** e depois clique no sinal de adição.
    
5. Na **nova janela política de anexos confiáveis** , em **nome**, digite **política de anexo seguro-Bloquear**.
    
6. Para uma **resposta desconhecida de malware de anexos seguros**, clique em **Bloquear**.
    
7. Para **Redirecionar o anexo na detecção**, clique em **Habilitar redirecionamento** e digite o endereço de email da sua conta de administrador global do Office 365.
    
8. Para **Aplicado a**, clique na seta para baixo e depois em **O domínio do destinatário é**. Na janela, clique no nome da sua organização (como contoso.onmicrosoft.com) e, em seguida, clique em **OK**.
    
9. Clique em **Salvar**. Após a atualização, você deve ver o **bloco de política de anexo seguro**novo e habilitado.
    
10. Clique na guia **links seguros** e depois clique no sinal de adição.
    
11. Na janela **nova política de segurança de links**, em **Nome**, digite **Política de Link Seguro**.
    
12. Para **Selecionar a ação a ser tomada em relação a URLs potencialmente mal intencionadas e desconhecidas em mensagens.**, clique em **Ativado** e depois selecione **Não permitir que os usuários cliquem até a URL original**.
    
13. Para **Aplicado a**, clique na seta para baixo e depois em **O domínio do destinatário é**. Na janela, clique no nome da sua organização (como contoso.onmicrosoft.com) e, em seguida, clique em **OK**.
    
14. Clique em **Salvar**. Você verá o novo item habilitado **Política de Link Seguro**.
    
## <a name="phase-4-show-atp-in-action"></a>Fase 4: Mostrar a ATP em ação

Nesta fase, você demonstrará como a ATP lida com emails potencialmente mal-intencionados.
  
1. Na instância do Internet Explorer que você usou para enviar o email na fase 2, na navegação à esquerda, clique em **itens enviados.**
    
2. Clique no email intitulado **suas novas chaves**, clique no ícone de seta para baixo e, em seguida, clique em **encaminhar**.
    
3. Para a nova mensagem, em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste e clique em **Enviar**.
    
4. Clique no email intitulado **novo site de viagem**, clique no ícone de seta para baixo, clique em **responder a todos**e, em seguida, clique em **Enviar**.
    
5. Na instância do Internet Explorer que você usou para configurar as políticas de ATP na Fase 3, clique na guia Centro de administração do Exchange, clique no bloco Aplicativos e depois clique em **Email**. Você verá duas novas mensagens de email na caixa de entrada:
    
  - Uma delas como o título **Enc: Suas novas chaves**
    
  - Uma delas como o título **Enc: Novo site de viagem**
    
6. Abra a mensagem de email chamada **FW: novo site de viagem** e clique no link **este site** . Você verá um "este site foi classificado como mal-intencionado". da. Isso demonstra que a ATP impede que você acesse o site potencialmente mal-intencionado.
    
7. Na guia Centro de administração do Exchange do Internet Explorer, na navegação à esquerda, clique em **fluxo de emails**.
    
8. Clique na guia **rastreamento de mensagens** e depois clique em **pesquisar**.
    
9. Na janela **Resultados do Rastreamento de Mensagens**, clique duas vezes na mensagem com o assunto **Suas novas chaves**. Esta mensagem foi entregue com êxito para a caixa de entrada. Feche esta janela.
    
10. Clique duas vezes na mensagem com o assunto **Novo site de viagem**. Esta mensagem foi entregue com êxito para a caixa de entrada. Feche esta janela.
    
11. Clique duas vezes na mensagem com o assunto **Enc: Suas novas chaves**. Observe como essa mensagem foi processada pela ATP e entregue à caixa de entrada. Feche esta janela.
    
    > [!NOTE]
    > O objetivo da política de anexos seguros era começar a examinar anexos por código mal-intencionado. O anexo getkeys. js era permitido porque não foi determinado como mal-intencionado. Esta etapa mostra que a ATP executou uma verificação do anexo. 
  
12. Clique duas vezes na mensagem com o assunto **Enc: Novo site de viagem**. Observe que essa mensagem foi entregue com êxito para a caixa de entrada.
    
Agora, você pode usar esse ambiente para criar novas políticas e fazer testes com a ATP.
  
> [!TIP]
> Clique [aqui](https://aka.ms/catlgstack) para exibir um mapa visual de todos os artigos da pilha da Guia do Laboratório de Teste do Office 365.
  
## <a name="see-also"></a>Confira também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para o ambiente de desenvolvimento/ teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md) 

[Proteção avançada para anexos seguros e links seguros](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


