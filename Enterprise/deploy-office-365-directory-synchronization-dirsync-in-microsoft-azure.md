---
title: Implantar a sincronização de diretórios do Microsoft 365 no Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Resumo: implante o Azure AD Connect em uma máquina virtual no Azure para sincronizar as contas entre o seu diretório local e o locatário do Azure AD da sua assinatura do Microsoft 365.'
ms.openlocfilehash: 6f2da528293de54d21bd88b31fcd347cfab9335c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998059"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>Implantar a sincronização de diretórios do Microsoft 365 no Microsoft Azure

O Azure Active Directory (Azure AD) Connect (anteriormente conhecido como a ferramenta de sincronização de diretório, a ferramenta de sincronização de diretório ou a ferramenta de DirSync.exe) é um aplicativo que você instala em um servidor associado a um domínio para sincronizar seus usuários do AD DS (serviços de domínio Active Directory) local para o locatário do Azure AD da sua assinatura do Microsoft 365. A Microsoft 365 usa o Azure AD para o serviço de diretório. Sua assinatura do Microsoft 365 inclui um locatário do Azure AD. Esse locatário também pode ser usado para o gerenciamento de identidades da sua organização com outras cargas de trabalho de nuvem, incluindo outros aplicativos SaaS e aplicativos no Azure.

Você pode instalar o Azure AD Connect em um servidor local, mas pode também instalá-lo em uma máquina virtual no Azure pelos seguintes motivos:
  
- Você pode provisionar e configurar servidores baseados na nuvem mais depressa, disponibilizando os serviços aos usuários com mais antecedência.
- O Azure oferece melhor disponibilidade de sites com menos esforço.
- Você pode reduzir o número de servidores locais em sua organização.

This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> Este artigo descreve a sincronização de um único domínio em uma única floresta. O Azure AD Connect sincroniza todos os domínios do AD DS em sua floresta do Active Directory com o Microsoft 365. Se você tiver várias florestas do Active Directory para sincronizar com o Microsoft 365, confira [sincronização de diretórios com várias florestas com o cenário de logon único](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>Visão geral da implantação da sincronização de diretório do Microsoft 365 no Azure

O diagrama a seguir mostra o Azure AD Connect em execução em uma máquina virtual no Azure (o servidor de sincronização de diretório) que sincroniza uma floresta local do AD DS com uma assinatura do Microsoft 365.
  
![A ferramenta Azure AD Connect em uma máquina virtual no Azure sincronizando contas locais para o locatário do Azure AD de uma assinatura do Microsoft 365 com fluxo de tráfego](media/CP-DirSyncOverview.png)
  
In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:
  
-  O Azure AD Connect consulta um controlador de domínio na rede local para detectar alterações em contas e senhas.
-  O Azure AD Connect envia as alterações para contas e senhas para a instância do Azure AD da sua assinatura do Microsoft 365. Como o servidor de sincronização de diretório está em uma parte estendida da sua rede local, essas alterações são enviadas pelo servidor de proxy da rede local.
    
> [!NOTE]
> Esta solução descreve a sincronização de um único domínio do Active Directory, uma única floresta do Active Directory. O Azure AD Connect sincroniza todos os domínios do Active Directory em sua floresta do Active Directory com o Microsoft 365. Se você tiver várias florestas do Active Directory para sincronizar com o Microsoft 365, confira [sincronização de diretórios com várias florestas com o cenário de logon único](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
Há duas etapas principais quando você implanta essa solução:
  
1. Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Instale o [Azure ad Connect](https://www.microsoft.com/download/details.aspx?id=47594) em uma máquina virtual associada ao domínio no Azure e sincronize o AD DS local com o Microsoft 365. Isso envolve:
    
    Criar uma Máquina Virtual do Azure para executar o Azure AD Connect.
    
    Instalar e configurar o [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).
    
    Configurar o Azure AD Connect requer as credenciais (nome de usuário e senha) de uma conta de administrador do Azure AD e uma conta de administrador corporativo do AD DS. O Azure AD Connect é executado imediatamente e continuamente para sincronizar a floresta do AD DS local com o Microsoft 365.
    
Antes de implantar essa solução em produção, você pode usar as instruções da [configuração de base corporativa simulada](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) para definir essa configuração como prova de conceito, para demonstrações ou para experimentos.
  
> [!IMPORTANT]
> Quando a configuração do Azure AD Connect for concluída, ele não salvará as credenciais de conta de administrador corporativo do AD DS. 
  
> [!NOTE]
> Esta solução descreve a sincronização de uma única floresta do AD DS para o Microsoft 365. A topologia abordada neste artigo representa apenas uma das maneiras de implementar essa solução. A topologia de sua organização pode ser diferente, com base em requisitos de rede e considerações de segurança exclusivos. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>Planejar a hospedagem de um servidor de sincronização de diretório para o Microsoft 365 no Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Pré-requisitos

Antes de começar, examine os seguintes pré-requisitos para essa solução:
  
- Examine o conteúdo de planejamento relacionado em [Planejar sua rede virtual do Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).
    
- Verifique se você atende a todos os [pré-requisitos](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) para configurar a Rede Virtual do Azure.
    
- Ter uma assinatura do Microsoft 365 que inclua o recurso integração com o Active Directory. Para obter informações sobre assinaturas do Microsoft 365, vá para a [página de assinatura do microsoft 365](https://products.office.com/compare-all-microsoft-office-products?tab=2).
    
- Provisione uma máquina virtual do Azure que executa o Azure AD Connect para sincronizar sua floresta do AD DS local com o Microsoft 365.
    
    Você deve ter as credenciais (nomes e senhas) para a conta de administrador corporativo do AD DS e uma conta de Administrador do Azure AD.
    
### <a name="solution-architecture-design-assumptions"></a>Suposições de design de arquitetura da solução

A lista a seguir descreve as opções de design feitas para essa solução.
  
- This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect. 
    
- Na rede local, existem servidores DNS e um controlador de domínio.
    
- Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).
    
There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:
  
- Se houver servidores DNS em uma rede virtual existente do Azure, determine se você deseja que seu servidor de sincronização de diretório os use para resolução de nomes em vez dos servidores DNS da rede local.
    
- If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.
    
## <a name="deployment-roadmap"></a>Roteiro de implantação

A implantação do Azure AD Connect em uma máquina virtual no Azure tem três etapas:
  
- Fase 1: Criar e configurar a rede virtual do Azure
    
- Fase 2: Criar e configurar a máquina virtual do Azure
    
- Fase 3: Instalar e configurar o Azure AD Connect
    
Após a implantação, você também deve atribuir locais e licenças para as novas contas de usuário no Microsoft 365.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Fase 1: Criar e configurar a rede virtual do Azure

Para criar e configurar a rede virtual do Azure, conclua a [Fase 1: preparar sua rede local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) e a [Fase 2: criar a rede virtual entre locais no Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) no roteiro de implantação de [Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Esta é a configuração resultante.
  
![Fase 1 do servidor de sincronização de diretório para o Microsoft 365 hospedado no Azure](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Esta figura mostra uma rede local conectada a uma rede virtual do Azure por meio de uma conexão VPN ou ExpressRoute de site a site.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Fase 2: Criar e configurar a máquina virtual do Azure

Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:
  
- On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.
    
- No painel **Escolher um tamanho**, escolha o tamanho **A2 Padrão**.
    
- On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.
    
Para conferir se o servidor de sincronização de diretório está usando o DNS corretamente, verifique o DNS interno para garantir que um registro de endereço (A) foi adicionado à máquina virtual com o respectivo endereço IP. 
  
Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.
  
For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.
  
Esta é a configuração resultante.
  
![Fase 2 do servidor de sincronização de diretório para o Microsoft 365 hospedado no Azure](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Esta figura mostra a máquina virtual do servidor de sincronização de diretório na rede virtual entre locais do Azure.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Fase 3: Instalar e configurar o Azure AD Connect

Faça o procedimento a seguir:
  
1. Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).
    
2. No servidor de sincronização de diretório, abra o artigo [Configurar a sincronização de diretório para o Microsoft 365](set-up-directory-synchronization.md) e siga as instruções para a sincronização de diretório com a sincronização de hash de senha.
    
> [!CAUTION]
> Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.
  
Esta é a configuração resultante.
  
![Fase 3 do servidor de sincronização de diretório para o Microsoft 365 hospedado no Azure](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Esta figura mostra o servidor de sincronização de diretório com o Azure AD Connect na rede virtual entre locais do Azure.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>Atribuir locais e licenças aos usuários no Microsoft 365

O Azure AD Connect adiciona contas à sua assinatura do Microsoft 365 do AD DS local, mas, para que os usuários entrem no Microsoft 365 e usem seus serviços, as contas devem ser configuradas com um local e licenças. Use essas etapas para adicionar o local e as licenças ativas às devidas contas de usuário:
  
1. Entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com)e, em seguida, clique em **administrador**.
    
2. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
3. Na lista das contas de usuário, marque a caixa de seleção ao lado do usuário que você deseja ativar.
    
4. Na página do usuário, clique em **Editar** para **Licenças de produto**.
    
5. Na página **Licenças de produto**, selecione um local para o usuário em **Local** e habilite as licenças apropriadas para ele.
    
6. Ao concluir, clique em **Salvar** e, em seguida, clique em **Fechar** duas vezes.
    
7. Volte à etapa 3 para usuários adicionais.
    
## <a name="see-also"></a>Confira também

[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.yml)
  
[Conectar uma rede local a uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Baixar o Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Configurar a sincronização de diretórios para o Microsoft 365](set-up-directory-synchronization.md)
  
