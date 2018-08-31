---
title: Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Resumo: Configure e demonstre a Proteção Avançada contra Ameaças do Office 365 no seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: 07411600db11c8eea825c0ef5b82ea1206d20e11
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914956"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365

 **Resumo:** Configure e demonstre a Proteção Avançada contra Ameaças do Office 365 no seu ambiente de desenvolvimento e teste do Office 365.
  
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
    
14. Em **URL**, digite **http://www.spamlink.contoso.com/**, clique em **Okey**e, em seguida, clique em **Enviar**.
    
15. Abra uma instância separada do Internet Explorer no modo de navegação privada, vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e se conectar à sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
16. Na página principal do portal, clique no bloco Aplicativos e depois em **Email**.
    
17. Em Caixa de Entrada, clique na mensagem com o assunto **Suas novas chaves**.
    
18. Na pasta Lixo eletrônico, clique na mensagem com o assunto **New viajam o site da web**. Dentro da mensagem, clique no link de **neste site** . Você deverá ver "Oops! Página do Internet Explorer não pôde encontrar spamlink.contoso.com.". Este é o resultado correto porque não há nenhuma página da web nesse local.
    
Observe que ambos os emails potencialmente mal-intencionados foram entregues com êxito. O email **Suas novas chaves** poderia conter malware não detectado, e o usuário poderia clicar no link possivelmente mal-intencionado no email **Novo site de viagem**.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Fase 3: Configurar políticas de anexo seguro e links seguros para a ATP

Nesta fase, você criará e configurará uma política de anexo seguro para impedir a entrega de emails com anexos possivelmente mal-intencionados e uma política de links seguros para impedir que os usuários acessem URLs possivelmente não seguras.
  
1. Na guia **Página inicial do Microsoft Office** do Internet Explorer, clique no lado do **Admin** .
    
2. Na navegação à esquerda, clique em **Centros de administração** e depois em **Exchange**.
    
3. Na navegação à esquerda da guia Centro de administração do Exchange, clique em **ameaças avançadas**.
    
4. Clique na guia **anexos seguros** e depois clique no sinal de adição.
    
5. Na janela **nova diretiva de segurança de anexos** , em **nome**, digite **Seguros política de anexo - bloco**.
    
6. **Resposta de malware desconhecido anexos seguros**, clique em **Bloquear**.
    
7. Para **Redirecionar o anexo na detecção**, clique em **Habilitar redirecionamento** e digite o endereço de email da sua conta de administrador global do Office 365.
    
8. Para **aplicado a**, clique na seta e, em seguida, clique em **domínio do destinatário é**. Na janela, clique em nome de sua organização (por exemplo, contoso.onmicrosoft.com) e clique em **Okey**.
    
9. Clique em **Salvar**. Depois da atualização, você verá a nova e habilitado a **Política de anexo seguros - bloco**.
    
10. Clique na guia **links seguros** e depois clique no sinal de adição.
    
11. Na janela **nova política de segurança de links**, em **Nome**, digite **Política de Link Seguro**.
    
12. Para **Selecionar a ação a ser tomada em relação a URLs potencialmente mal intencionadas e desconhecidas em mensagens.**, clique em **Ativado** e depois selecione **Não permitir que os usuários cliquem até a URL original**.
    
13. Para **aplicado a**, clique na seta e, em seguida, clique em **domínio do destinatário é**. Na janela, clique em nome de sua organização (por exemplo, contoso.onmicrosoft.com) e clique em **Okey**.
    
14. Clique em **Salvar**. Você verá o novo item habilitado **Política de Link Seguro**.
    
## <a name="phase-4-show-atp-in-action"></a>Fase 4: Mostrar a ATP em ação

Nesta fase, você demonstrará como a ATP lida com emails potencialmente mal-intencionados.
  
1. Da instância do Internet Explorer que você usou para enviar o email na fase 2, no painel de navegação esquerdo, clique em **itens enviados.**
    
2. Clique em email intitulado **suas novas chaves**, clique no ícone de seta para baixo e clique em **Avançar**.
    
3. Para a nova mensagem, em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste e clique em **Enviar**.
    
4. Clique em email intitulado **New viajam o site da web**, clique no ícone de seta para baixo, clique em **responder a todos**e clique em **Enviar**.
    
5. Na instância do Internet Explorer que você usou para configurar as políticas de ATP na Fase 3, clique na guia Centro de administração do Exchange, clique no bloco Aplicativos e depois clique em **Email**. Você verá duas novas mensagens de email na caixa de entrada:
    
  - Uma delas como o título **Enc: Suas novas chaves**
    
  - Uma delas como o título **Enc: Novo site de viagem**
    
6. Abra a mensagem de email denominada **firmware: novo site de viagens** e clique no link **neste site** . Você deverá ver uma página "Este site tiver sido classificado como sendo maliciosas.". Isso demonstra que ATP está impedindo acessem o site da web potencialmente mal-intencionados.
    
7. Na guia Centro de administração do Exchange do Internet Explorer, na navegação à esquerda, clique em **fluxo de emails**.
    
8. Clique na guia **rastreamento de mensagens** e depois clique em **pesquisar**.
    
9. Na janela de **Resultados de rastreamento de mensagem** , clique duas vezes a mensagem com o assunto **suas novas chaves**. Essa mensagem foi entregue com êxito para a caixa de entrada. Feche essa janela.
    
10. Clique duas vezes a mensagem com o assunto **New viajam o site da web**. Essa mensagem foi entregue com êxito para a caixa de entrada. Feche essa janela.
    
11. Clique duas vezes a mensagem com o assunto **firmware: suas novas chaves**. Observe como esta mensagem foi processada pelo ATP e, em seguida, entregue à caixa de entrada. Feche essa janela.
    
    > [!NOTE]
    > A finalidade da diretiva de segurança de anexos era começar a verificação de anexos para código mal-intencionado. O anexo getKeys.js foi permitido porque não foi determinado mal-intencionados. Esta etapa mostra que ATP executa um exame do anexo. 
  
12. Clique duas vezes a mensagem com o assunto **firmware: novo site de viagens**. Observe que essa mensagem foi entregue com êxito para a caixa de entrada.
    
Agora, você pode usar esse ambiente para criar novas políticas e fazer testes com a ATP.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="see-also"></a>Confira também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para o ambiente de desenvolvimento/ teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md) 

[Proteção avançada para anexos seguros e links seguros](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


