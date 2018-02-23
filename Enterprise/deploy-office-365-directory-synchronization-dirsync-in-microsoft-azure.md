---
title: "Implantar a DirSync (sincronização de diretórios) do Office 365 no Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: "Resumo: implante o Azure AD Connect (DirSync) em uma máquina virtual no Azure para sincronizar as contas entre o diretório local e o locatário do Azure AD da sua assinatura do Office 365."
ms.openlocfilehash: 07ec310c50635afd70b0342d2e0547aab0e95d01
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure"></a>Implantar a DirSync (sincronização de diretórios) do Office 365 no Microsoft Azure

 **Resumo:** implante o Azure AD Connect (DirSync) em uma máquina virtual no Azure para sincronizar as contas entre o diretório local e o locatário do Azure AD da sua assinatura do Office 365.
  
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

O diagrama a seguir mostra o Azure AD Connect Health em execução em uma máquina virtual do Azure (o servidor DirSync) que sincroniza uma floresta local do AD do Windows Server com uma assinatura do Office 365.
  
![Ferramenta Azure AD Connect em uma máquina virtual no Azure sincronizando contas locais para o locatário do Azure AD de uma assinatura do Office 365 com o fluxo de tráfego local](images/CP_DirSyncOverview.png)
  
No diagrama, há duas redes conectadas por meio de uma conexão VPN site a site ou ExpressRoute. Há um rede local em que os controladores de domínio do AD do Windows Server estão localizados e há uma rede virtual do Azure com um servidor DirSync, uma máquina virtual que executa o [Azure AD Connect Health](https://www.microsoft.com/download/details.aspx?id=47594). Existem dois fluxos de tráfego principais provenientes do servidor DirSync:
  
-  O Azure AD Connect consulta um controlador de domínio na rede local para detectar alterações em contas e senhas.
    
-  O Azure AD Connect envia as alterações nas contas e senhas à instância do AD do Azure de sua assinatura do Office 365. Como o servidor DirSync está em uma parte estendida de sua rede local, essas alterações são enviadas pelo servidor proxy da rede local.
    
> [!NOTE]
> Esta solução descreve a sincronização de um único domínio do Active Directory, uma única floresta do Active Directory. O Azure AD Connect sincroniza todos os domínios do Active Directory em sua floresta do Active Directory com o Office 365. Se você tiver várias florestas do Active Directory para sincronizar com o Office 365, confira [Cenário de Sincronização de Diretório de Várias Florestas com Logon Único](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
Em ambos os casos, o tráfego originado pelo Azure AD Connect em execução na máquina virtual do Azure é encaminhado para um gateway em uma rede virtual no Azure, que então encaminha o tráfego pela conexão VPN de site a site ou ExpressRoute para o dispositivo de gateway VPN na rede local. A infraestrutura de roteamento da rede local encaminha então o tráfego ao seu destino, como um controlador de domínio ou um servidor proxy.
  
Há duas etapas principais quando você implanta essa solução:
  
1. Criar uma rede virtual do Azure e estabelecer uma conexão VPN de site a site para a sua rede local. Para saber mais, confira o artigo [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Instalar o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) em uma máquina virtual associada ao domínio no Azure e depois sincronizar AD do Windows Server com o Office 365. Isso envolve:
    
    Criar uma Máquina Virtual do Azure para executar o Azure AD Connect.
    
    Instalar e configurar o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).
    
    A configuração do Azure AD Connect requer as credenciais (nome de usuário e senha) de uma conta de administrador do AD do Azure e uma conta de administrador corporativo do AD do Windows Server. O Azure AD Connect executa imediatamente e continuamente para sincronizar a floresta local do AD DS com o Office 365.
    
Antes de implantar esta solução no ambiente de produção, use as instruções descritas no artigo [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md) para definir essa configuração como uma prova de conceito, para fins de demonstrações ou experiências.
  
> [!IMPORTANT]
> Quando a configuração do Azure AD Connect for concluída, ele não salvará as credenciais de conta de administrador corporativo do AD do Windows Server. 
  
> [!NOTE]
> Essa solução descreve a sincronização de uma única floresta do AD do Windows Server com o Office 365. A topologia abordada neste artigo representa apenas uma das maneiras de implementar essa solução. A topologia de sua organização pode ser diferente, com base em requisitos de rede e considerações de segurança exclusivos. 
  
## <a name="plan-for-hosting-a-dirsync-server-for-office-365-in-azure"></a>Planejar a hospedagem de um servidor DirSync do Office 365 no Azure
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
  
- Essa solução usa uma única rede virtual do Azure com uma conexão VPN de site a site. A rede virtual do Azure hospeda uma única sub-rede que contém um servidor, o servidor DirSync que está executando o Azure AD Connect. 
    
- Na rede local, existem servidores DNS e um controlador de domínio.
    
- O Azure AD Connect realiza a sincronização de senha, em vez de logon único. Você não precisa implantar uma infraestrutura de AD FS (Serviços de Federação do Active Directory). Para saber mais sobre as opções de sincronização de senha e logon único, confira [Determinar qual cenário de integração de diretório usar](https://go.microsoft.com/fwlink/p/?LinkId=393094).
    
Há opções adicionais de design que você pode considerar ao implantar essa solução em seu ambiente. Elas incluem o seguinte:
  
- Se houver servidores DNS em uma rede virtual existente do Azure, determine se você deseja que seu servidor DirSync os use para resolução de nomes em vez dos servidores DNS da rede local.
    
- Se houver controladores de domínio em uma rede virtual do Azure existente, determine se a configuração de Serviços e Sites do Active Directory pode ser uma opção melhor para você. O servidor DirSync pode consultar controladores de domínio na rede virtual do Azure para procurar alterações em contas e senhas em vez de controladores de domínio na rede local.
    
## <a name="deployment-roadmap"></a>Roteiro de implantação
<a name="DeploymentRoadmap"> </a>

A implantação do Azure AD Connect em uma máquina virtual no Azure tem três etapas:
  
- Fase 1: Criar e configurar a rede virtual do Azure
    
- Fase 2: Criar e configurar a máquina virtual do Azure
    
- Fase 3: Instalar e configurar o Azure AD Connect
    
Após a implantação, você também deve atribuir locais e licenças para as novas contas de usuário no Office 365.
  
> [!TIP]
> O [Kit de implantação do Servidor DirSync no Microsoft Azure](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contém todos os blocos do Azure PowerShell para elaborar esta solução, os diagramas no formato do Microsoft PowerPoint e do Visio e a pasta de trabalho de configuração do Microsoft Excel que gera blocos de comandos personalizados do Azure PowerShell para suas configurações.
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Fase 1: Criar e configurar a rede virtual do Azure

Para criar e configurar a rede virtual do Azure, conclua a [Fase 1: preparar sua rede local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) e a [Fase 2: criar a rede virtual entre locais no Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) no roteiro de implantação de [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Esta é a configuração resultante.
  
![Fase 1 do servidor DirSync do Office 365 hospedado no Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Esta figura mostra uma rede local conectada a uma rede virtual do Azure por meio de uma conexão VPN ou ExpressRoute de site a site.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Fase 2: Criar e configurar a máquina virtual do Azure

Criar a máquina virtual no Azure usando as instruções [Criar sua primeira máquina virtual do Windows no portal do Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use as seguintes configurações:
  
- No painel **Básico**, selecione a mesma assinatura, local e grupo de recursos que sua rede virtual. Armazene o nome de usuário e a senha em um local seguro. Você precisará dessas informações posteriormente para se conectar à máquina virtual.
    
- No painel **Escolher um tamanho**, escolha o tamanho **A2 Padrão**.
    
- No painel **Configurações**, na seção **Armazenamento**, escolha o tipo de armazenamento **Padrão**. Na seção **Rede**, escolha o nome da rede virtual e a sub-rede para hospedar o servidor DirSync (não a GatewaySubnet). Deixe todas as outras configurações com seus valores padrão.
    
Para conferir se o servidor DirSync está usando o DNS corretamente, verifique o DNS interno para garantir que um registro de endereço (A) foi adicionado à máquina virtual com o respectivo endereço IP. 
  
Use as instruções em [Conectar-se à máquina virtual e fazer login](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) para conectar-se ao servidor DirSync com uma Conexão de Área de Trabalho Remota. Depois de entrar, ingresse na máquina virtual do domínio local do AD do Windows Server.
  
Para que o Azure AD Connect acesse os recursos da Internet, você deve configurar o servidor DirSync para usar o servidor proxy da rede local. Entre em contato com o administrador da rede para etapas de configuração adicionais para executar.
  
Esta é a configuração resultante.
  
![Fase 2 do servidor DirSync do Office 365 hospedado no Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Esta figura mostra a máquina virtual do servidor DirSync na rede virtual entre locais do Azure.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Fase 3: Instalar e configurar o Azure AD Connect

Faça o procedimento a seguir:
  
1. Conecte-se ao servidor DirSync usando uma Conexão de Área de Trabalho Remota com uma conta de domínio do AD do Windows Server que tenha privilégios de administrador local. Confira [Conectar-se à máquina virtual e fazer login](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).
    
2. No servidor DirSync, abra o artigo [Configurar a sincronização de diretórios no Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) e siga as instruções para a sincronização de diretório com a sincronização de senha.
    
> [!CAUTION]
> A instalação cria a conta **AAD_xxxxxxxxxxxx** na unidade organizacional (UO) Usuários Locais. Não mova nem remova essa conta ou a sincronização falhará.
  
Esta é a configuração resultante.
  
![Fase 3 do servidor DirSync do Office 365 hospedado no Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Esta figura mostra o servidor DirSync com o Azure AD Connect na rede virtual entre locais do Azure.
  
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
  
[Kit de implantação do Servidor DirSync no Azure](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



