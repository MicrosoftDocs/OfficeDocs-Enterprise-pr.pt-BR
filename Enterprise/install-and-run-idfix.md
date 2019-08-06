---
title: Baixar e executar a ferramenta IdFix do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Como baixar e executar a ferramenta IdFix do Office 365 para ajudar a limpar os serviços de domínio do Active Directory (AD DS) antes de sincronizá-lo com o Office 365.
ms.openlocfilehash: 4a402cf245ebd20fbc5846908d521469ebfb90c1
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490744"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a>Baixar e executar a ferramenta IdFix do Office 365


IdFix identifica erros como duplicatas e problemas de formatação no domínio dos serviços de domínio do Active Directory (AD DS) antes de sincronizar com o Office 365. 
  
Para concluir essa tarefa com êxito, você deve estar seguro para trabalhar com objetos de usuário, de grupo e de contato no AD DS.
  
Se você não puder concluir esta tarefa, há algumas outras coisas que você pode fazer. Esses métodos podem ser mais fáceis, mas também podem demorar mais ou ter outras desvantagens. São eles:
  
- **Executar a sincronização de diretórios sem executar o IdFix** 

  Você pode sincronizar seu diretório sem usar a ferramenta IdFix, mas não é recomendável. A correção de erros antes da sincronização leva menos tempo e geralmente fornece uma transição mais suave para a nuvem. 

- **Contratar um consultor** 

  Obter ajuda especializada pode colocar seus usuários em funcionamento rapidamente e seu diretório sincronizado. 
    
## <a name="what-you-need-to-run-idfix"></a>O que você precisa para executar o IdFix

A maneira mais fácil de obter IdFix em funcionamento é baixá-lo em um computador que ingressou no seu domínio do AD DS. Você pode executá-lo no controlador de domínio, se desejar, mas isso não é necessário.
  
### <a name="idfix-hardware-requirements"></a>Requisitos de hardware do IdFix

O computador onde você baixa o IdFix precisa atender a estes requisitos mínimos de hardware:
  
- 4 GB de RAM
- 2 GB de espaço em disco rígido
   
### <a name="idfix-software-requirements"></a>Requisitos de software do IdFix

O computador onde você baixa o IdFix precisa ser associado ao mesmo domínio do AD DS do qual você deseja sincronizar os usuários com o Office 365. 

O computador também precisa ter o .NET Framework 4,0 instalado. Se você estiver executando o Windows Server 2008 ou posterior, o .NET Framework provavelmente já está instalado. Caso contrário, você pode [baixar o .net 4,0 do centro de download](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou com o Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisitos de permissões do IdFix

A conta de usuário que você usa para executar o IdFix deve ter acesso de leitura e gravação ao domínio do AD DS.
  
Se você não tiver certeza se sua conta de usuário atende a esses requisitos e se não tem certeza de como verificar, ainda pode baixar e executar o IdFix. Se sua conta de usuário não tiver as permissões corretas, o IdFix simplesmente exibirá um erro quando você tentar executá-la.
  
## <a name="download-and-extract-idfix"></a>Baixar e extrair IdFix

Siga estas instruções. 
  
1. Entre no computador em que você deseja executar a ferramenta IdFix.
    
2. Vá para o site de download da Microsoft para a [ferramenta de correção de erros do IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Baixe e abra o arquivo zip.
    
3. Na janela **IdFix** , escolha **extrair**e **extrair tudo**. Por padrão, o IdFix é extraído para `C:\Users\<your user name>\Documents\IdFix`. 
    
6. Escolha **extrair**.

Essas instruções foram feitas com o Internet Explorer em um servidor executando o Windows Server 2016. Se você estiver usando uma versão diferente do Windows ou um navegador diferente, suas etapas podem variar.
    
## <a name="run-the-idfix-tool"></a>Executar a ferramenta IdFix

Depois de baixar e extrair o IdFix, execute-o para procurar problemas no domínio do AD DS.
  
1. Usando uma conta com acesso de leitura/gravação ao seu domínio do AD DS, entre no computador onde você baixou o IdFix.
    
2. No explorador de arquivos, vá para o local onde você extraiu IdFix. Se você escolher a pasta padrão durante a extração, `C:\Users\<your user name>\Documents\IdFix`vá para. 
    
3. Clique duas vezes em **IdFix. exe**. 
  
4. Por padrão, o IdFix usa o conjunto de regras multilocatário para testar as entradas no seu diretório. Este é o conjunto de regras correto para a maioria dos clientes do Office 365. No entanto, se você for um cliente do Office 365 dedicado ou internacional de tráfego de leis de braços (ITAR)), poderá configurar o IdFix para usar o conjunto de regras dedicado. Se você não tiver certeza sobre o tipo de cliente que você está, pode ignorar esta etapa com segurança. Para definir o conjunto de regras como dedicado, clique no ícone de engrenagem na barra de menus e, em seguida, escolha **dedicado**.
    
5. Escolha **consulta**.
    
    ![Escolha consulta no IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Por padrão, o IdFix procura erros em todo o diretório.
    
    Dependendo do tamanho do seu diretório, a execução da consulta pode demorar um pouco. Você pode assistir ao progresso na parte inferior da janela principal da ferramenta. Se você clicar em **Cancelar**, precisará reiniciar desde o início.
  
7. Depois que o IdFix concluir a consulta, você poderá sincronizar seu diretório se não houver erros. Se houver erros no diretório, é recomendável corrigi-los antes de sincronizar. Consulte [preparar atributos de diretório para sincronização com o Office 365](prepare-directory-attributes-for-synch-with-idfix.md) para obter mais informações.
    
    Embora não seja obrigatório corrigir os erros antes de sincronizar, é altamente recomendável que você pelo menos revise todos os erros retornados pelo IdFix.
    
    Cada erro é exibido em uma linha separada na janela principal da ferramenta. 
    
8. Se você concordar com a alteração sugerida na coluna **Atualizar** , na coluna **ação** , selecione o que você deseja que o IdFix faça para implementar a alteração e clique em **aplicar**. Quando você clica em **aplicar**, a ferramenta faz as alterações no diretório.
    
    Você não precisa clicar em **aplicar** após cada atualização. Em vez disso, você pode corrigir vários erros antes de clicar em **aplicar** e o IdFix todos serão alterados ao mesmo tempo. Você pode classificar os erros por tipo de erro clicando em **erro** na parte superior da coluna que lista os tipos de erro. 
    
    Uma estratégia é corrigir todos os erros do mesmo tipo; por exemplo, corrija primeiro todas as duplicatas e aplique-as. Em seguida, corrija os erros de formato de caractere e assim por diante. Cada vez que você aplica as alterações, a ferramenta IdFix cria um arquivo de log separado que você pode usar para desfazer suas alterações caso você cometa um erro. O [log de transações](idfix-transaction-log.md) é armazenado na pasta onde você extraiu o IdFix, que é _C:\Users\<seu nome de usuário> \documents\idfix_ por padrão. 
    
    ![Correção de erros no IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Depois que todas as suas alterações forem feitas no diretório, execute IdFix novamente para garantir que as correções que você fez não introduziu novos erros. Você pode repetir essas etapas quantas vezes for necessário. É uma boa ideia passar pelo processo algumas vezes antes de sincronizar.
    
## <a name="additional-resources-on-idfix"></a>Recursos adicionais no IdFix 

- [Objetos e atributos excluídos e compatíveis com a IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Log de transações do IdFix do Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Treinamento em vídeo

Para obter mais informações, consulte a lição [instalar e usar a ferramenta IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), trazida para você pelo LinkedIn Learning.
  

