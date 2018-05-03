---
title: Detectar e personalizados e regras do Outlook remediar inclusões de formulários attacks no Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: Saiba como reconhecer e remediar as regras do Outlook e os ataques de inclusões de formulários personalizados no Office 365
ms.openlocfilehash: d0f54a0dc47d7a3602a7b4ce57a04c83d15d9301
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks-in-office-365"></a>Detectar e corrigir as regras do Outlook e ataques de inclusões de formulários personalizados no Office 365

**Resumo** Saiba como reconhecer e remediar as regras do Outlook e os ataques de inclusões de formulários personalizados no Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Qual é o ataque de injeção de regras do Outlook e formulários personalizados?
Depois que um invasor tenha violado uma conta em sua locação e obtém no, haverá para tentar estabelecer uma maneira de ficar no ou uma maneira de obter em depois que eles são descobertos e removidos. Isso é chamado estabelecendo um mecanismo de persistência. Duas maneiras que eles podem fazer isso são Explorando as regras do Outlook ou pela injeção de formulários personalizados para o Outlook. Em ambos os casos, a regra ou o formulário é sincronizado do serviço de nuvem para baixo até o cliente de desktop, para um formato completo e reinstale-o do software cliente não eliminar o mecanismo de injeção. Isso ocorre porque quando o software de cliente do Outlook reconecta à caixa de correio na nuvem-lo novamente baixará as regras e formulários da nuvem. Depois que as regras e formulários estão no lugar, o invasor os usa para executar código personalizado ou remoto, geralmente para instalar malware na máquina local. Em seguida, o malware roube novamente as credenciais ou executa outras atividades ilícitas. A boa notícia é que caso você mantenha seus clientes o patch para a versão mais recente, você não está vulnerável a ameaça como os dois mecanismos de bloquear atuais padrões de cliente do Outlook. 

Os ataques geralmente seguem a esses padrões:

A exploração de regras
1. O invasor roube o nome de usuário e a senha de um dos seus usuários.
2. O invasor entra para essa caixa de correio do Exchange de usuários. A caixa de correio pode ser no Exchange online ou no Exchange local.
3. O invasor, em seguida, cria uma regra de encaminhamento na caixa de correio que é disparada quando a caixa de correio recebe um email que corresponde aos critérios da regra. Os critérios da regra e o conteúdo do email gatilho é personalizado para cada um dos outros.
4. O invasor envia o email de gatilho ao usuário que está usando suas caixas de correio normalmente.
5. Quando o email é recebido, a regra for acionada. Geralmente, a ação da regra é iniciar um aplicativo em um servidor remoto de (WebDAV).
6. O aplicativo normalmente instala o malware, como [Powershell Empire](https://www.powershellempire.com/), localmente no computador do usuário.
7. O malware permite que o invasor roubar novamente o nome do usuário e senha ou outras credenciais da máquina local e realizar outras atividades mal-intencionadas.

A exploração de formulários
1. O invasor roube o nome de usuário e a senha de um dos seus usuários.
2. O invasor entrar para essa caixa de correio do Exchange de usuários. A caixa de correio pode ser no Exchange online ou no Exchange local.
3. O invasor cria um modelo de formulário de email personalizado e insere em caixa de correio do usuário.  O formulário personalizado é disparado quando a caixa de correio recebe um email que exige a caixa de correio para carregar o formulário personalizado. O formulário personalizado e o formato de email são personalizadas para cada um dos outros.
4. O invasor envia o email de gatilho ao usuário, que está usando suas caixas de correio normalmente.
5. Quando o email é recebido, o formulário é carregado. O formulário inicia um aplicativo em um servidor remoto de (WebDAV).
6. O aplicativo normalmente instala o malware, como [Powershell Empire](https://www.powershellempire.com/), localmente no computador do usuário.
7. O malware permite que o invasor roubar novamente o nome do usuário e senha ou outras credenciais da máquina local e realizar outras atividades mal-intencionadas.


## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Quais regras de um e ataque de injeção de formulários personalizado pode parecer com o Office 365?

Esses mecanismos de persistência improvável de ser observado por seus usuários e talvez em alguns casos pares estejam invisíveis a eles.  Este artigo explica como procurar por qualquer um dos sinais de sete (indicadores de comprometimento) listadas abaixo. Se você encontrar qualquer uma dessas, você precisará executar etapas de remediação.

- Indicadores do comprometimento regras
    - Ação de regra é para iniciar um aplicativo.
    - Regra faz referência a um EXE, ZIP ou URL.
    - Na máquina local, procure o início do processo de nova originados PID o Outlook.
- Indicadores do comprometimento de formulários personalizados 
    - Formulário personalizado presente salvo como sua própria classe de mensagem.
    - Classe de mensagem contém código executável.
    - Geralmente, armazenados em pastas de caixa de entrada ou biblioteca de formulários particulares.
    - Formulário é denominado IPM. Nota. [nome personalizado].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Etapas para localizar os sinais desse ataque e confirmá-la
Você pode usar qualquer um desses dois métodos para confirmar o ataque.
- Examine manualmente as regras e formulários para cada caixa de correio usando o cliente do Outlook.  Esse método é completo, mas só é possível verificar correio do usuário cada vez que pode ser muito demorado se você tiver muitos usuários para verificar.  Ele também pode resultar em uma violação do computador que você está executando a verificação de.
- Use o script do PowerShell [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) para todos os emails de encaminhamento de regras e formulários personalizados para todos os usuários em sua locação de despejo automaticamente. Este é o método mais rápido e mais seguro com o mínimo de sobrecarga.


### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Confirme que as regras de ataque usando o cliente do Outlook
1. Abra o cliente do Outlook de usuários como o usuário.  O usuário talvez precise de ajuda para examinando as regras de sua caixa de correio.
2. Consulte o artigo de [Gerenciar mensagens usando regras de e-mail](https://support.office.com/en-us/article/manage-email-messages-by-using-rules-c24f5dea-9465-4df4-ad17-a50704d66c59#ID0EAABAAA=2010) para obter os procedimentos sobre como abrir a interface de regras nas versões 2007, 2010 ou 2013 do Outlook.
3. Procure regras que o usuário não criou, ou qualquer inesperadas regras ou regras com nomes suspeitos.
4. Examinar a descrição da regra para ações de regra que iniciar e o aplicativo ou se referir a um. EXE. Arquivo ZIP ou para lançar uma URL.
5. Procurar por novos processos que começar a usar a ID de processo do Outlook.  Consulte [localizar a identificação do processo](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/finding-the-process-id).

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Etapas para confirmar o ataque de formulários usando o cliente do Outlook
1. Abra o cliente do Outlook do usuário como o usuário.
2. Siga as etapas em, [Mostrar a guia Desenvolvedor](https://support.office.com/en-us/article/show-the-developer-tab-e1192344-5e56-4d45-931b-e5fd9bea2d45) para a versão de usuários do Outlook.
3. Abra a guia Desenvolvedor agora está visível no Outlook e clique em **criar um formulário**.
4. Selecione a **caixa de entrada** , **Procure na** lista. Procure por quaisquer formulários personalizados.  Formulários personalizados são raros o suficiente para que se você tiver quaisquer formulários personalizados nisso, ele vale uma Visão aprofundada.
5. Investigue quaisquer formulários personalizados, especialmente aquelas marcados como ocultos.
6. Abra quaisquer formulários personalizados e no grupo **formulário** , clique em **Exibir código** para ver o que é executado quando o formulário é carregado.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Etapas para confirmar o ataque de regras e formulários usando o PowerShell
A maneira mais simples de verificar um regras ou ataque de formulários personalizados é executar o script do PowerShell [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) .  Esse script conecta-se para cada caixa de correio no seu locatário e descarta todas as regras e formulários em dois arquivos. csv.

#### <a name="pre-requisites"></a>Pré-requisitos
Você precisará ter um direitos de administrador global para executar o script, porque o script conecta-se para cada caixa de correio no aluguel para ler as regras e formulários.

1. Inscreva-se para a máquina que você executará o script de com direitos de administrador local.
2. Faça download ou copie o script de Get-AllTenantRulesAndForms.ps1 da GitHub para uma pasta da qual você vai executá-lo.  O script irá criar dois arquivos com carimbo de data para esta pasta, MailboxFormsExport-aaaa-mm-dd.csv e MailboxRulesExport-aaaa-mm-dd.csv.
3. Abra uma instância do PowerShell como administrador e abra a pasta que você salvou o script.
4. Execute esta linha de comando do PowerShell da seguinte maneira `.\Get-AllTenantRulesAndForms.ps1`.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Interpretando a saída

MailboxRulesExport -*aaaa-mm-dd*. csv – examinar as regras (um por linha) para as condições de ação que incluem arquivos executáveis ou aplicativos.
- ActionType (coluna A) – se você vir o valor "ID_ACTION_CUSTOM", a regra é provável mal-intencionado.
- IsPotentiallyMalicious (coluna D) – se esse valor for "TRUE", a regra é provável mal-intencionado.
- ActionCommand (coluna G) – se esta lista um aplicativo ou qualquer arquivo com um .exe, extensão. zip ou uma entrada que se refere a uma URL, que não deveriam estar lá, a regra é provável mal-intencionado.

MailboxFormsExport -*aaaa-mm-dd*. csv – em geral, o uso de formulários personalizados é muito raro.  Se você encontrar qualquer nesta pasta de trabalho, você pode abre a caixa de correio desse usuário e examinar o próprio formulário.  Se sua organização não colocou ele intencionalmente, é provável mal-intencionado.



## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Como parar e remediar o ataque de formulários e regras do Outlook
Se você encontrar qualquer evidência de qualquer um desses ataques, correção é simple, basta excluir a regra ou o formulário da caixa de correio. Você pode fazer isso com o cliente Outlook ou usando o PowerShell remoto para remover regras.

### <a name="using-outlook"></a>Usando o Outlook
1. Identificar todos os dispositivos que o usuário tiver usado com o Outlook.  Eles todos precisará ser limpo de malware possível.  Não permitir que o usuário logon e usar email, até que todos os dispositivos são limpos.
2. Siga as etapas em [Excluir uma regra](https://support.office.com/en-us/article/Delete-a-rule-2F0E7139-F696-4422-8498-44846DB9067F) de cada dispositivo.
3. Se você não tiver certeza sobre a presença de outros tipos de malware, você pode formatar e reinstale todos os softwares no dispositivo.  Para dispositivos móveis, você pode seguir as etapas de fabricantes para redefinir o dispositivo para a imagem de fábrica.
4. Instale as versões mais recentes do Outlook.  Lembre-se de que a versão atual do Outlook bloqueia, por padrão, os dois tipos desse ataque.
5. Depois que todas as cópias offline da caixa de correio foram removidas, redefinir a senha do usuário (use uma alta qualidade uma) e siga as etapas em [Configurar a autenticação multifator para usuários do Office 365](https://support.office.com/en-us/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6) se MFA já não tiver sido habilitado. Isso garante que as credenciais do usuário não estão expostas por outros meios (por exemplo, senha ou phishing reutilizar).

### <a name="using-powershell"></a>Usando o PowerShell
Existem dois cmdlets do PowerShell remotos que você pode usar para remover ou desabilitar regras perigosas. Basta seguir as etapas.
 
Etapas para caixas de correio que estão em um servidor do Exchange

1. Conecte-se ao servidor do Exchange usando o PowerShell remoto. Siga as etapas em [conectar-se aos servidores do Exchange usando o PowerShell remoto](https://docs.microsoft.com/en-us/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell?view=exchange-ps).
2. Se desejar remover completamente uma única regra, todas as regras ou várias regras de um uso de caixa de correio o [cmdlet Remove-caixa de entrada regra ](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)- use essa opção para completamente remove uma, várias ou todas as regras da caixa de correio.
3. Se você deseja manter a regra e seu conteúdo para uma investigação detalhada use o [cmdlet Disable-InboxRule](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx). 

Etapas para caixas de correio no Exchange Online
1. Siga as etapas em [conectar-se ao Exchange Online usando o PowerShell](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).
2.  Se desejar remover completamente uma única regra, várias regras ou todas as regras de uma caixa de correio, use o [cmdlet Remove-caixa de entrada de regra](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps).
3.  Se você deseja manter a regra e seu conteúdo para uma investigação detalhada use o [cmdlet Disable-InboxRule](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx). 

## <a name="how-to-minimize-future-attacks"></a>Como minimizar os ataques futuros

### <a name="first-protect-your-accounts"></a>Primeira: proteger suas contas

As regras e formulários explorações são usadas somente por um invasor após terem roubado ou violado uma das contas do usuário. Portanto, a primeira etapa para evitar o uso dessas explorações contra a sua organização é agressivamente proteger suas contas de usuário.  Algumas das formas mais comuns que contas são violadas são por meio de phishing ou [senha pulverizando](http://www.dabcc.com/microsoft-defending-against-password-spray-attacks/) ataques.



A melhor maneira de proteger suas contas de usuário e especialmente suas contas de administrador deve [Configurar a autenticação multifator para usuários do Office 365](https://support.office.com/en-us/article/set-up-multi-factor-authentication-for-office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).  Você também deve:
<ol>
    <li>Monitore como suas contas de usuário são <a href="https://docs.microsoft.com/en-us/azure/active-directory/active-directory-view-access-usage-reports">acessados e usados</a>. Você não pode impedir a violação inicial, mas você reduzirá a duração e o impacto da violação detectando mais cedo. Você pode usá-los: <a href="https://support.office.com/en-us/article/overview-of-office-365-cloud-app-security-81f0ee9a-9645-45ab-ba56-de9cbccab475">políticas de segurança de aplicativo de nuvem do Office 365</a> para monitorar a contas e alerta no atividade incomum.<ol type="a">
            <li><b>Várias tentativas de login com falha</b> Essa diretiva profiles seu ambiente e gatilhos alertas quando os usuários realizam várias atividades de login com falha em uma única sessão com relação a linha de base aprendida, que possa indicar uma violação tentada.</li>
            <li><b>Impossible viagem</b> - Esta diretiva perfis de seu ambiente e dispara alertas quando atividades são detectadas do mesmo usuário em diferentes locais dentro de um período de tempo que seja menor que o tempo de viagem esperada entre os dois locais. Isso pode indicar que um usuário diferente está usando as mesmas credenciais. Detectar esse comportamento anômalos necessita de um período de aprendizado inicial de sete dias durante os quais ele aprende padrão da atividade de um novo usuário.</li>
            <li><b>Incomum representada atividade (por usuário)</b> - Esta diretiva perfis de seu ambiente e dispara alertas quando os usuários realizam várias atividades representadas em uma única sessão com relação a linha de base aprendida, que possa indicar uma violação tentada.</li>
        </ol>
    </li>
    <li>Aproveite uma ferramenta como a <a href="https://securescore.office.com/">Pontuação de seguro do Office 365</a> para gerenciar configurações de segurança de conta e comportamentos. 
    </li>
</ol> 

### <a name="second-keep-your-outlook-clients-current"></a>Segunda: Mantenha seus clientes Outlook atual
Versões corrigidas e completamente atualizados do Outlook 2013 e 2016 desabilitar a ação de regra/formulário "Iniciar aplicativo" por padrão.  Isso garantirá que, mesmo que um invasor violar a conta, as ações de regra e formulário serão bloqueadas.  Você pode instalar as últimas atualizações e patches de segurança seguindo as etapas em [instalar Office updates](https://support.office.com/en-us/article/Install-Office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5).

Aqui estão as versões de patch do seu Outlook 2013 e clientes de 2016:
- Outlook 2013: 15.0.4937.1000 ou posterior
- Outlook 2016: 16.0.4534.1001 ou posterior

Para obter mais informações sobre os patches de segurança individuais, consulte:

- [Patch de segurança do Outlook 2013](https://support.microsoft.com/en-us/help/3191938) 
- [Patch de segurança do Outlook 2016](https://support.microsoft.com/en-us/help/3191883)

### <a name="third-monitor-your-outlook-clients"></a>Terceiro: Monitorar seus clientes do Outlook
Observe que mesmo com as correções e atualizações instaladas, é possível que um invasor alterar a configuração da máquina local para reabilitar o comportamento de "Iniciar aplicativo". Você pode usar o [Gerenciamento avançado de diretiva de grupo](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/agpm/) para monitorar e impor diretivas de máquina local em seus clientes.  
Você pode para ver se "Iniciar aplicativo" novamente habilitado, através de uma substituição no registro, usando as informações em [como exibir o registro do sistema usando as versões de 64 bits do Windows](https://support.microsoft.com/en-us/help/305097/how-to-view-the-system-registry-by-using-64-bit-versions-of-windows).  Verifique essas subchaves: 

- Outlook 2016: HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\
- Outlook 2013: HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\

Procure a chave EnableUnsafeClientMailRules. Se ele existe e está definido como 1, o patch de segurança do Outlook foi substituído e o computador está vulnerável a ataques de formulário/regras. Se o valor for 0, a ação de "Iniciar aplicativo" está desabilitada.  Se a versão atualizada e corrigida do Outlook está instalada e essa chave do registro não estiver presente, um sistema não é vulnerável a esses ataques.

Clientes com instalações do Exchange local devem considerar o bloqueio versões mais antigas do Outlook que não possuem patches disponíveis. Detalhes sobre esse processo podem ser encontrados no artigo [bloqueio do cliente de configurar o Outlook](https://technet.microsoft.com/en-us/library/dd335207(v=exchg.150).aspx).

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Proteger o Office 365 como um cybersecurity pro
Sua assinatura do Office 365 é fornecido com um conjunto avançado de recursos de segurança que você pode usar para proteger seus dados e seus usuários.  Use o [mapa de segurança do Office 365: principais prioridades para os primeiros 30 dias, 90 dias e além](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) para implementar as práticas recomendadas para proteger seu locatário do Office 365 do Microsoft.
- Tarefas para realizar nos primeiros 30 dias.  Elas têm efeito imediato e são baixo impacto para seus usuários.
- Tarefas para realizar em 90 dias. Essas demoram um pouco mais para planejar e implementar mas melhorar consideravelmente sua situação de segurança.
- Além de 90 dias. Esses aperfeiçoamentos se baseiam em seu primeiro trabalho de 90 dias.

## <a name="see-also"></a>Consulte também:
- [As regras do Outlook mal-intencionado](https://silentbreaksecurity.com/malicious-outlook-rules/) por SilentBreak Post de segurança sobre regras de vetor fornece uma análise detalhada de como as regras do Outlook. 
- [MAPI sobre HTTP e Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) no blog do Sensepost sobre Mailrule Pwnage discute uma ferramenta chamada régua que lhe permite explorar caixas de correio por meio de regras do Outlook.
- [Shells e formulários do outlook](https://sensepost.com/blog/2017/outlook-forms-and-shells/) no blog do Sensepost sobre formulários vetor de ameaça. 
- [Codebase da régua](https://github.com/sensepost/ruler)
- [Indicadores de régua de comprometimento](https://github.com/sensepost/notruler/blob/master/iocs.md)