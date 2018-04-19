---
title: Implantar o Office 365 Directory Synchronization in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Resumo: Implante o Azure AD conectar-se em uma máquina virtual no Windows Azure para sincronizar contas entre seu diretório local e o locatário do Azure AD de sua assinatura do Office 365.'
ms.openlocfilehash: 31a72d027acd274c9908a7e63e83843bce9cec71
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a>Implantar o Office 365 Directory Synchronization in Microsoft Azure

 **Resumo:** Implante o Windows Azure AD conectar-se em uma máquina virtual no Windows Azure para sincronizar contas entre seu diretório local e o locatário do Azure AD de sua assinatura do Office 365.
  
O Azure Active Directory Connect (também conhecido como Ferramenta de Sincronização de Diretório ou ferramenta DirSync.exe) é um aplicativo baseado em servidor que você instala em um servidor associado ao domínio para sincronizar os usuários locais do Windows Server Active Directory com o locatário do Azure Active Directory da sua assinatura do Office 365. Você pode instalar o Azure AD Connect em um servidor local, mas pode também instalá-lo em uma máquina virtual no Azure pelos seguintes motivos:
  
- Você pode provisionar e configurar servidores baseados na nuvem mais depressa, disponibilizando os serviços aos usuários com mais antecedência.
    
- O Azure oferece melhor disponibilidade de sites com menos esforço.
    
- Você pode reduzir o número de servidores locais em sua organização.
    
> [!IMPORTANT]
> Essa solução requer conectividade entre sua rede local e sua Rede Virtual do Azure. Para saber mais, confira o artigo [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!IMPORTANT]
> Este artigo descreve a sincronização de um único domínio em uma única floresta. O Azure AD Connect sincroniza todos os domínios do AD do Windows Server em sua floresta do Active Directory com o Office 365. Se você tiver várias florestas do Active Directory para sincronizar com o Office 365, confira [Cenário de Sincronização de Diretório de Várias Florestas com Logon Único](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
> [!NOTE]
> O Office 365 usa o Azure Active Directory (AD do Azure) para seu serviço de diretório. A sua assinatura do Office 365 inclui um locatário do AD do Azure. Esse locatário também pode ser usado para o gerenciamento de identidades da sua organização com outras cargas de trabalho de nuvem, incluindo outros aplicativos SaaS e aplicativos no Azure. 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a>Visão geral da implantação da sincronização de diretório do Office 365 no Azure
<a name="Overview"> </a>

O diagrama a seguir mostra o Azure Connect da AD em execução em uma máquina virtual no Windows Azure (o servidor de sincronização de diretório) que sincroniza uma floresta do Windows Server AD local à assinatura anOffice 365.
  
![Ferramenta Azure AD Connect em uma máquina virtual no Azure sincronizando contas locais para o locatário do Azure AD de uma assinatura do Office 365 com o fluxo de tráfego local](images/CP_DirSyncOverview.png)
  
No diagrama, há duas redes conectadas por uma conexão de VPN ou ExpressRoute-to-site. Há um local de rede onde os controladores de domínio do Windows Server AD estão localizados e não há uma rede virtual do Azure com um servidor de sincronização de diretório, que é uma máquina virtual em execução [Connect do Azure AD](https://www.microsoft.com/download/details.aspx?id=47594). Existem dois fluxos de tráfego principal provenientes do servidor de sincronização do diretório:
  
-  O Azure AD Connect consulta um controlador de domínio na rede local para detectar alterações em contas e senhas.
    
-  Conectar do Azure AD envia as alterações para contas e senhas para a instância do Azure AD de sua assinatura do Office 365. Como o servidor de sincronização de diretório está em uma parte estendida de sua rede local, essas alterações são enviadas por meio do servidor de proxy da rede local.
    
> [!NOTE]
> Esta solução descreve a sincronização de um único domínio do Active Directory, uma única floresta do Active Directory. O Azure AD Connect sincroniza todos os domínios do Active Directory em sua floresta do Active Directory com o Office 365. Se você tiver várias florestas do Active Directory para sincronizar com o Office 365, confira [Cenário de Sincronização de Diretório de Várias Florestas com Logon Único](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
Em ambos os casos, o tráfego originado pelo Azure AD Connect em execução na máquina virtual do Azure é encaminhado para um gateway em uma rede virtual no Azure, que então encaminha o tráfego pela conexão VPN de site a site ou ExpressRoute para o dispositivo de gateway VPN na rede local. A infraestrutura de roteamento da rede local encaminha então o tráfego ao seu destino, como um controlador de domínio ou um servidor proxy.
  
Há duas etapas principais quando você implanta essa solução:
  
1. Criar uma rede virtual do Azure e estabelecer uma conexão VPN de site a site para a sua rede local. Para saber mais, confira o artigo [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Instalar o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) em uma máquina virtual associada ao domínio no Azure e depois sincronizar AD do Windows Server com o Office 365. Isso envolve:
    
    Criar uma Máquina Virtual do Azure para executar o Azure AD Connect.
    
    Instalar e configurar o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).
    
    A configuração do Azure AD Connect requer as credenciais (nome de usuário e senha) de uma conta de administrador do AD do Azure e uma conta de administrador corporativo do AD do Windows Server. O Azure AD Connect executa imediatamente e continuamente para sincronizar a floresta local do AD DS com o Office 365.
    
Antes de implantar essa solução na produção, use as instruções na [sincronização de diretório para o seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md) para configurar essa configuração como uma prova de conceito, para demonstrações ou experimentação.
  
> [!IMPORTANT]
> Quando a configuração do Azure AD Connect for concluída, ele não salvará as credenciais de conta de administrador corporativo do AD do Windows Server. 
  
> [!NOTE]
> Essa solução descreve a sincronização de uma única floresta do AD do Windows Server com o Office 365. A topologia abordada neste artigo representa apenas uma das maneiras de implementar essa solução. A topologia de sua organização pode ser diferente, com base em requisitos de rede e considerações de segurança exclusivos. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a>Planejar para hospedar um servidor de sincronização de diretório para o Office 365 no Windows Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Pré-requisitos

Antes de começar, examine os seguintes pré-requisitos para essa solução:
  
- Examine o conteúdo de planejamento relacionado em [Planejar sua rede virtual do Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).
    
- Verifique se você atende a todos os [pré-requisitos](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) para configurar a Rede Virtual do Azure.
    
- Tenha uma assinatura do Office 365 que inclui o recurso de integração do Active Directory. Para saber mais sobre assinaturas do Office 365, acesse a [Página de Assinaturas do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=394278).
    
- Provisione uma Máquina Virtual do Azure que executa o Azure AD Connect para sincronizar sua floresta local do AD do Windows Server com o Office 365.
    
    Você deve ter as credenciais (nomes e senhas) para a conta de administrador corporativo do AD do Windows Server e uma conta de Administrador do Azure Active Directory.
    
### <a name="solution-architecture-design-assumptions"></a>Suposições de design de arquitetura da solução

A lista a seguir descreve as opções de design feitas para essa solução.
  
- Esta solução usa uma única rede virtual Azure com uma conexão de VPN-to-site. A rede virtual do Azure hospeda uma única sub-rede que contém um servidor, o servidor de sincronização de diretório que está executando o Connect do Azure AD. 
    
- Na rede local, existem servidores DNS e um controlador de domínio.
    
- Conectar do Azure AD executa a sincronização de hash de senha em vez do serviço single sign-on. Você não precisará implantar uma infraestrutura de serviços de Federação do Active Directory (AD FS). Para saber mais sobre as opções de logon única e sincronização de hash de senha, consulte como [Escolher o método de autenticação correto para sua solução de identidade híbrida Azure Active Directory](http://aka.ms/auth-options).
    
Há opções adicionais de design que você pode considerar ao implantar essa solução em seu ambiente. Elas incluem o seguinte:
  
- Se houver servidores DNS em uma rede virtual de Azure existente existentes, determine se deseja que seu servidor de sincronização de diretório usá-las para resolução de nome, em vez de servidores DNS na rede local.
    
- Se houver controladores de domínio em uma rede virtual de Azure existente, determine se a configuração de serviços e Sites do Active Directory pode ser a melhor opção para você. O servidor de sincronização de diretório pode consultar os controladores de domínio na rede virtual Azure alterações em contas e senhas, em vez de controladores de domínio na rede local.
    
## <a name="deployment-roadmap"></a>Roteiro de implantação
<a name="DeploymentRoadmap"> </a>

A implantação do Azure AD Connect em uma máquina virtual no Azure tem três etapas:
  
- Fase 1: Criar e configurar a rede virtual do Azure
    
- Fase 2: Criar e configurar a máquina virtual do Azure
    
- Fase 3: Instalar e configurar o Azure AD Connect
    
Após a implantação, você também deve atribuir locais e licenças para as novas contas de usuário no Office 365.
  
> [!TIP]
> O [Servidor de sincronização de diretório no Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contém todos os blocos de Azure PowerShell para criar o essa solução, os diagramas no formato do Microsoft PowerPoint e Visio e uma pasta de trabalho de configuração de Microsoft Excel gerará Blocos de comando do Windows Azure PowerShell personalizados para suas configurações.
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Fase 1: Criar e configurar a rede virtual do Azure

Para criar e configurar a rede virtual do Azure, conclua a [Fase 1: preparar sua rede local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) e a [Fase 2: criar a rede virtual entre locais no Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) no roteiro de implantação de [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Esta é a configuração resultante.
  
![Fase 1 do servidor de sincronização de diretório para o Office 365 hospedados no Windows Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Esta figura mostra uma rede local conectada a uma rede virtual do Azure por meio de uma conexão VPN ou ExpressRoute de site a site.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Fase 2: Criar e configurar a máquina virtual do Azure

Criar a máquina virtual no Azure usando as instruções [Criar sua primeira máquina virtual do Windows no portal do Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use as seguintes configurações:
  
- No painel **Básico**, selecione a mesma assinatura, local e grupo de recursos que sua rede virtual. Armazene o nome de usuário e a senha em um local seguro. Você precisará dessas informações posteriormente para se conectar à máquina virtual.
    
- No painel **Escolher um tamanho**, escolha o tamanho **A2 Padrão**.
    
- No painel **configurações** , na seção de **armazenamento** , selecione o tipo de armazenamento **padrão** . Na seção de **rede** , selecione o nome da sua rede virtual e da sub-rede para hospedar o servidor de sincronização de diretório (não o GatewaySubnet). Deixe todas as outras configurações com seus valores padrão.
    
Verifique se seu servidor de sincronização de diretório está usando DNS corretamente, verificando o DNS interno para certificar-se de que um registro de endereço (A) foi adicionado para a máquina virtual com o respectivo endereço IP. 
  
Use as instruções em [conectar-se para a máquina virtual e entrada](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) para se conectar ao servidor de sincronização de diretório com uma Conexão de área de trabalho remota. Depois de entrar, ingresse a máquina virtual ao domínio Windows Server AD local.
  
Para conectar de Azure AD acessar os recursos da Internet, você deve configurar o servidor de sincronização de diretório para usar o servidor de proxy da rede local. Contate o administrador da rede para as etapas de configuração adicional para executar.
  
Esta é a configuração resultante.
  
![Fase 2 do servidor de sincronização de diretório para o Office 365 hospedados no Windows Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Esta figura mostra a máquina virtual de servidor de sincronização de diretório nos locais cruzados rede virtual do Azure.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Fase 3: Instalar e configurar o Azure AD Connect

Faça o procedimento a seguir:
  
1. Conecte-se ao servidor de sincronização de diretório usando uma Conexão de área de trabalho remota com uma conta de domínio do Windows Server AD que tenha privilégios de administrador local. Consulte [Connect to a máquina virtual e o logon](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).
    
2. Do servidor de sincronização do diretório, abra o artigo [Configure a sincronização de diretórios no Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) e siga as instruções para sincronização de diretórios com a sincronização de hash de senha.
    
> [!CAUTION]
> A instalação cria a conta **AAD_xxxxxxxxxxxx** na unidade organizacional (UO) Usuários Locais. Não mova nem remova essa conta ou a sincronização falhará.
  
Esta é a configuração resultante.
  
![Fase 3 do servidor de sincronização de diretório para o Office 365 hospedados no Windows Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Esta figura mostra o servidor de sincronização de diretório com o Azure Connect do AD nos locais cruzados rede virtual do Azure.
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a>Atribuir locais e licenças aos usuários no Office 365

O Azure AD Connect adiciona contas à sua assinatura do Office 365 do AD local do Windows Server, mas para que os usuários entrem no Office 365 e usem seus serviços, as contas devem ser configuradas com um local e licenças. Use essas etapas para adicionar o local e as licenças ativas às devidas contas de usuário:
  
1. Entre na [página do portal do Office 365](https://portal.office.com) e clique em **Administrador**.
    
2. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
3. Na lista das contas de usuário, marque a caixa de seleção ao lado do usuário que você deseja ativar.
    
4. Na página do usuário, clique em **Editar** para **Licenças de produto**.
    
5. Na página **Licenças de produto**, selecione um local para o usuário em **Local** e habilite as licenças apropriadas para ele.
    
6. Ao concluir, clique em **Salvar** e, em seguida, clique em **Fechar** duas vezes.
    
7. Volte à etapa 3 para usuários adicionais.
    
## <a name="see-also"></a>Confira também

<a name="DeploymentRoadmap"> </a>

[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Baixar o Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Configurar a sincronização de diretório no Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[Servidor de sincronização de diretório no Kit de implantação do Windows Azure](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



