---
title: Proteger os arquivos do SharePoint Online com proteção de informações do Windows Azure
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
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Resumo: Aplica proteção de informações do Windows Azure para proteger os arquivos em um site de equipe do SharePoint Online altamente confidencial.'
ms.openlocfilehash: 84bd1f48c7051f945e7b851f829421364de2a557
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Proteger os arquivos do SharePoint Online com proteção de informações do Windows Azure

 **Resumo:** Aplica proteção de informações do Windows Azure para proteger os arquivos em um site de equipe do SharePoint Online altamente confidencial.
  
Use as etapas neste artigo para configurar a proteção de informações do Windows Azure para fornecer criptografia e permissões para os arquivos em um site de equipe do SharePoint Online altamente confidencial. A proteção de criptografia e permissões viaja com um arquivo, mesmo quando ele é baixado do site. Para obter mais informações sobre altamente confidenciais sites de equipe do SharePoint Online, consulte [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md).
  
> [!NOTE]
> Quando a criptografia da Proteção de Informações do Azure é aplicada aos arquivos armazenados no Office 365, o serviço não pode processar o conteúdo desses arquivos. Coautoria, descoberta eletrônica, pesquisa, Delve e outros recursos de colaboração não funcionam. Políticas DLP só funcionam com metadados (incluindo rótulos do Office 365), mas não com o conteúdo desses arquivos (como números de cartão de crédito em arquivos). 
  
Primeiro, use as instruções em [Ativar o Azure RMS com o Centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) para sua assinatura do Office 365.
  
Em seguida, configure a proteção de informações do Windows Azure com uma nova política de escopo e sub-recurso rótulo para proteção e permissões do seu site de equipe do SharePoint Online altamente confidencial.
  
1. Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Em uma guia separada do navegador, vá para o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se essa for a primeira vez que você está configurando a proteção de informações do Windows Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. No painel de lista, clique em **mais de serviços**, digite as **informações**e clique em **Proteção de informações do Windows Azure**.
    
5. No blade **proteção das informações do Azure** , clique em **escopo políticas > + Adicionar uma nova diretiva**.
    
6. Digite um nome para a nova política no **Nome da política** e uma descrição em **Descrição**.
    
7. Clique em **Selecionar quais usuários ou grupos obtêm esta política > Usuário/ Grupos**, e selecione o grupo de acesso dos membros do site para o site da equipe do SharePoint Online altamente confidencial. 
    
8. Clique em **Selecionar > OK**.
    
9. Para o rótulo **Altamente Confidencial**, clique nas reticências (...) e, em seguida, clique em **Adicionar um sub-rótulo**.
    
10. Digite um nome para o subrótulo em **Nome** e uma descrição do rótulo em **Descrição**.
    
11. Em **Definir permissões para documentos e emails que contenham este rótulo**, clique em **Proteger**.
    
12. Na seção **Proteção**, clique em **Azure (chave de nuvem)**.
    
13. Na folha **Proteção**, em **Configurações de proteção**, clique em **+ Adicionar permissões**.
    
14. Na folha **Adicionar permissões**, em **Especificar usuários e grupos**, clique em **+ Procurar no diretório**.
    
15. No painel **AAD usuários e grupos** , selecione o grupo de acesso de membros do site do seu site de equipe do SharePoint Online altamente confidencial e clique em **Selecionar**.
    
16. Em **Escolha as permissões a predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo**e **Encaminhar** .
    
17. Clique duas vezes em **Okey** .
    
18. Na folha **Rótulo**, clique em **Salvar**.
    
19. Feche a nova folha de política em escopo.
    
20. No blade **proteção de informações do Windows Azure - políticas com escopo** , clique em **Publicar**.
    
Isso é sua configuração resultante para seu site de equipe do SharePoint Online altamente confidencial.
  
![Rótulo da Proteção de Informações do Azure de um site de equipe isolado do SharePoint Online.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Agora você está pronto para começar a criar documentos e protegê-los com a Proteção de Informações do Azure e seu novo rótulo.
  
Você deve [instalar o cliente de proteção de informações do Windows Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) no seu dispositivo ou computador baseado no Windows. Você pode criar script e automatizar a instalação ou os usuários podem instalar manualmente o cliente. Consulte os seguintes recursos:
  
- [O lado do cliente da Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Instalando o cliente da Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Página de download para a instalação manual](https://www.microsoft.com/download/details.aspx?id=53018)
    
Depois de instalado, seus usuários execute e, em seguida, login em um aplicativo do Office (por exemplo, o Microsoft Word) com sua conta do Office 365. Uma nova barra de **Proteção de informações** permite que os usuários selecionem o novo rótulo. Certifique-se de que os usuários saibam o site da equipe do SharePoint Online e que identificam os usar para proteger seus arquivos altamente confidenciais.
  
> [!NOTE]
> Se houver vários sites de equipe do SharePoint Online altamente confidenciais, crie várias políticas de escopo de Proteção de Informações do Azure com sub-rótulos com as configurações acima, com as permissões para cada sub-rótulo definidas para o grupo de acesso de membros do site, de um site específico de equipe do SharePoint Online. 
  
## <a name="see-also"></a>Confira também

[Proteger sites e arquivos do SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




