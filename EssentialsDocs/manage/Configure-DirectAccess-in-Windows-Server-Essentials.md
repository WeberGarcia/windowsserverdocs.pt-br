---
title: Configurar o DirectAccess no Windows Server Essentials
description: Descreve como usar o Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c959b6fc-c67e-46cd-a9cb-cee71a42fa4c
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2081473500a08776a1dc81a4fa443696b6fde0d6
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433459"
---
# <a name="configure-directaccess-in-windows-server-essentials"></a>Configurar o DirectAccess no Windows Server Essentials

>Aplica-se a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Este tópico fornece instruções passo a passo para configurar o DirectAccess no Windows Server Essentials para habilitar sua força de trabalho móvel a conectar diretamente à rede da sua organização de qualquer local remoto equipado com Internet sem estabelecer uma conexão de rede virtual privada (VPN). O DirectAccess pode oferecer aos trabalhadores móveis a mesma experiência de conectividade dentro e fora do escritório de seus computadores Windows 8.1, Windows 8 e Windows 7.  
  
 No Windows Server Essentials, se o domínio tiver mais de um servidor Windows Server Essentials, o DirectAccess deve ser configurado no controlador de domínio.  
  
> [!NOTE]
>  Este tópico fornece instruções para configurar o DirectAccess quando seu servidor Windows Server Essentials é o controlador de domínio. Se o servidor do Windows Server Essentials é um membro do domínio, siga as instruções para configurar o DirectAccess em um membro do domínio em [adicionar DirectAccess a uma implantação de acesso remoto existente (VPN)](https://technet.microsoft.com/library/jj574220.aspx) em vez disso.  
  
## <a name="process-overview"></a>Visão geral do processo  
 Para configurar o DirectAccess no Windows Server Essentials, conclua as etapas a seguir.  
  
> [!IMPORTANT]
>  Antes de usar os procedimentos neste guia para configurar o DirectAccess no Windows Server Essentials, você deve habilitar o VPN no servidor. Para obter instruções, consulte [gerenciar VPN](Manage-VPN-in-Windows-Server-Essentials.md).  
  
-   [Etapa 1: Adicionar ferramentas de gerenciamento de acesso remoto ao seu servidor](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_AddRAM)  
  
-   [Etapa 2: Altere o endereço do adaptador de rede do servidor para um endereço IP estático](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_AddStaticIP)  
  
-   [Etapa 3: Preparar um certificado e o registro de DNS para o servidor de local de rede](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)  
  
    -   [Etapa 3a: Conceder permissões completas para usuários autenticados para o modelo de certificado do servidor Web](#BKMK_GrantFullPermissions)  
  
    -   [Etapa 3b: Inscrever um certificado para o servidor de local de rede com um nome comum, que não pode ser resolvido a partir da rede externa](#BKMK_EnrollaCertificate)  
  
    -   [Etapa 3c: Adicionar um novo host ao servidor DNS e mapeá-lo para o endereço do servidor Windows Server Essentials](#BKMK_MapNewHosttoServerAddress)  
  
-   [Etapa 4: Criar um grupo de segurança para computadores cliente do DirectAccess](#BKMK_AddSecurityGroup)  
  
-   [Etapa 5: Habilitar e configurar o DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableConfigureDA)  
  
    -   [Etapa 5a: Habilitar o DirectAccess usando o Console de gerenciamento de acesso remoto](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableDA)  
  
    -   [Etapa 5b: Remover o IPv6Prefix inválido em GPO RRAS (Windows Server Essentials apenas)](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_RemoveIPv6)  
  
    -   [Etapa 5c: Habilitar os computadores cliente que executam o Windows 7 Enterprise para que usem o DirectAccess](#BKMK_Step4cWindows7Setup)  
  
    -   [Etapa 5D: Configurar o servidor de local de rede](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NLS)  
  
    -   [Etapa 5e: Adicionar uma chave do registro para ignorar a autoridade de certificação ao estabelecer um canal IPsec](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_CA)  
  
-   [Etapa 6: Definir as configurações de tabela de diretivas de resolução de nome para o servidor DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NRPT)  
  
-   [Etapa 7: Configurar regras de firewall TCP e UDP para os GPOs do servidor DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_TCPUDP)  
  
-   [Etapa 8: Alterar a configuração de DNS64 para escutar a interface IP-HTTPS](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS64)  
  
-   [Etapa 9: Reservar portas para o serviço WinNat](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_ExemptPort)  
  
-   [Etapa 10: Reiniciar o serviço WinNat](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_WinNAT)  
  
> [!NOTE]
>  [Apêndice: Configurar o DirectAccess usando o Windows PowerShell](#BKMK_AppendixBPowerShellScript) fornece um script do Windows PowerShell que você pode usar para executar a instalação do DirectAccess.  
  
##  <a name="BKMK_AddRAM"></a> Etapa 1: Adicionar Ferramentas de Gerenciamento de Acesso Remoto ao servidor  
  
#### <a name="to-add-remote-access-management-tools"></a>Para adicionar as Ferramentas de Gerenciamento de Acesso Remoto  
  
1.  No servidor, no canto inferior esquerdo da tela Inicial, clique no ícone do **Gerenciador do Servidor**.  
  
     No Windows Server Essentials, você precisará pesquisar o Gerenciador do servidor para abri-lo. Na página Inicial, digite **Server Manager**e clique em **Gerenciador do Servidor** nos resultados da pesquisa. Para fixar o Gerenciador do Servidor para a página Inicial, clique com o botão direito do mouse em Gerenciador do Servidor nos resultados da pesquisa e clique em **Fixar na tela inicial**.  
  
2.  Caso a mensagem de aviso de **Controle de Conta do Usuário** seja exibida, clique em **Sim**.  
  
3.  No painel do Gerenciador do Servidor, clique em **Gerenciar** e depois em **Adicionar Funções e Recursos**.  
  
4.  No Assistente de Adição de Funções e Recursos, faça o seguinte:  
  
    1.  Na página **Tipo de Instalação**, clique em **Instalação baseada em função ou recurso**.  
  
    2.  Sobre o **página seleção de servidor** (ou o **Selecionar servidor de destino** página no Windows Server Essentials), clique em **selecione um servidor no pool de servidores**.  
  
    3.  Na página **Recursos** , expanda **Ferramentas de Administração de Servidor Remoto (instalado)** , expanda **Ferramentas de gerenciamento de acesso remoto (instalado)** , expanda **Ferramentas de administração de função (instalado)** , expanda **Ferramentas de gerenciamento de acesso remoto**e, em seguida, selecione **GUI de acesso remoto e ferramentas de linha de comando**.  
  
    4.  Siga as instruções para concluir o assistente.  
  
##  <a name="BKMK_AddStaticIP"></a> Etapa 2: Alterar o endereço do adaptador de rede do servidor para um endereço IP estático  
 O DirectAccess requer um adaptador com endereço IP estático. Você deve alterar o endereço IP do adaptador de rede local no servidor.  
  
#### <a name="to-add-a-static-ip-address"></a>Para adicionar um endereço IP estático  
  
1.  Na página Inicial, abra **Painel de controle**.  
  
2.  Clique em **Rede e Internet**e em **Exibir o status e as tarefas da rede**.  
  
3.  No painel de tarefas da **Central de Rede e Compartilhamento**, clique em **Alterar as configurações do adaptador**.  
  
4.  Clique com o botão direito no adaptador de rede local e clique em **Propriedades**.  
  
5.  Na guia **Rede** , clique em **Protocolo IP Versão 4 (TCP/IPv4)** e em **Propriedades**.  
  
6.  Na guia **Geral** , clique em **Usar o seguinte endereço IP**e digite o endereço IP que deseja usar.  
  
     Um valor padrão para a máscara de sub-rede aparece automaticamente na caixa **Máscara de sub-rede**. Aceite o valor padrão ou digite o valor da máscara de sub-rede que deseja usar.  
  
7.  Na caixa **Gateway padrão**, digite o endereço IP do seu gateway padrão.  
  
8.  Na caixa **Servidor DNS preferencial**, digite o endereço IP do seu servidor DNS.  
  
    > [!NOTE]
    >  Use o endereço IP atribuído ao seu adaptador por DHCP (por exemplo, 192.168.X.X) em vez de uma rede de loopback (por exemplo, 127.0.0.1). Para descobrir o endereço IP atribuído, execute **ipconfig** no prompt de comando.  
  
9. Na caixa **Servidor DNS alternativo**, digite o endereço IP do seu servidor DNS alternativo, se houver.  
  
10. Clique em **OK** e em **Fechar**.  
  
> [!IMPORTANT]
>  Certifique-se de configurar o roteador de modo a encaminhar as portas 80 e 443 para o novo endereço IP estático do servidor.  
  
##  <a name="BKMK_DNS"></a> Etapa 3: Preparar um certificado e um registro de DNS para o servidor de local de rede  
 Para preparar um certificado e um registro de DNS para o servidor de local de rede, execute as tarefas a seguir:  
  
-   [Etapa 3a: Conceder permissões completas para usuários autenticados para o modelo de certificado do servidor Web](#BKMK_GrantFullPermissions)  
  
-   [Etapa 3b: Inscrever um certificado para o servidor de local de rede com um nome comum, que não pode ser resolvido a partir da rede externa](#BKMK_EnrollaCertificate)  
  
-   [Etapa 3c: Adicionar um novo host ao servidor DNS e mapeá-lo para o endereço do servidor Windows Server Essentials.](#BKMK_MapNewHosttoServerAddress)  
  
###  <a name="BKMK_GrantFullPermissions"></a> Etapa 3a: Conceder permissões completas para usuários autenticados para o modelo de certificado do servidor Web  
 A primeira tarefa é conceder permissões completas para autenticar usuários para o modelo de certificado do servidor Web na autoridade de certificação.  
  
####  <a name="BKMK_ToGrantFullPermissions"></a> Para conceder permissões completas para usuários autenticados para o modelo de certificado do servidor Web  
  
1.  Na página **Iniciar** , abra **Autoridade de Certificação**.  
  
2.  Na árvore de console, sob **autoridade de certificação (Local)** , expanda **< servername\>-CA**, clique com botão direito **modelos de certificado**e, em seguida, clique em **Gerenciar**.  
  
3.  Em **Autoridade de certificação (Local)** , clique com botão direito do mouse em **Servidor Web**e clique em **Propriedades**.  
  
4.  Nas propriedades do servidor Web, na guia **Segurança** , clique em **Usuários autenticados**, selecione **Controle Total**e clique em **OK**.  
  
5.  Reinicie **Serviços de certificados do Active Directory**. No painel de controle, abra **Exibir serviços locais**. Na lista de serviços, clique com botão direito do mouse em **Serviços de certificados do Active Directory**e, em seguida, clique em **Reiniciar**.  
  
###  <a name="BKMK_EnrollaCertificate"></a> Etapa 3b: Inscrever um certificado para o servidor de local de rede com um nome comum, que não pode ser resolvido a partir da rede externa.  
 A seguir, inscrever um certificado para o servidor de local de rede com um nome comum, que não pode ser resolvido a partir da rede externa.  
  
####  <a name="BKMK_ToEnrollaCertificate"></a> Para inscrever um certificado para o servidor de local de rede  
  
1.  Na página **Iniciar**, abra **mmc** (Console de Gerenciamento Microsoft).  
  
2.  Caso a mensagem de aviso de **Controle de Conta do Usuário** seja exibida, clique em **Sim**.  
  
     O Console de Gerenciamento Microsoft (MMC) é aberto.  
  
3.  No menu **Arquivo**, clique em **Adicionar/Remover Snap-ins**.  
  
4.  Na caixa **Adicionar ou remover snap-ins** , clique em **Certificados**e clique em **Adicionar**.  
  
5.  Na página **Snap-in de certificados**, clique em **Conta de computador** e em **Avançar**.  
  
6.  Na página **Selecionar Computador** , clique em **Computador local**, em **Concluir**e em **OK**.  
  
7.  Na árvore de console, expanda **Certificados (Computador Local)** , expanda **Pessoal**, clique com botão direito do mouse em **Certificados**e, em seguida, em **Todas as tarefas**, clique em **Solicitar novo certificado**.  
  
8.  Quando o Assistente de registro de certificado for exibido, clique em **Avançar**.  
  
9. Na página **Selecionar política de registro de certificado**, clique em **Avançar**.  
  
10. Na página **Solicitar certificados**, marque a caixa de seleção **Servidor Web** e clique em **Mais informações são necessárias para inscrever esse certificado**.  
  
11. Na caixa **Propriedades do certificado**, digite as seguintes configurações para **Nome de assunto**:  
  
    1.  Para o **Tipo**, selecione **Nome comum**.  
  
    2.  Em **Valor**, digite o nome do servidor de local de rede (por exemplo, DirectAccess-NLS.contoso.local) e clique em **Adicionar**.  
  
    3.  Clique em **OK** e, em seguida, clique em **Registrar**.  
  
12. Quando terminar de registrar o certificado, clique em **Concluir**.  
  
###  <a name="BKMK_MapNewHosttoServerAddress"></a> Etapa 3c: Adicionar um novo host ao servidor DNS e mapeá-o para o endereço do servidor Windows Server Essentials.  
 Para concluir a configuração do DNS, adicione um novo host no servidor DNS e mapeá-lo para o endereço do servidor Windows Server Essentials.  
  
####  <a name="BKMK_ToMapNewHosttoServerAddress"></a> Para mapear um novo host para o endereço do servidor Windows Server Essentials  
  
1.  Na página Inicial, abra o Gerenciador de DNS. Para abrir o Gerenciador de DNS, pesquise **dnsmgmt.msc**e clique em **dnsmgmt.msc** nos resultados.  
  
2.  Na árvore de console Gerenciador DNS, expanda o servidor local, expanda **zonas de pesquisa direta**, clique com botão direito na zona com o sufixo do domínio do servidor e, em seguida, clique em **novo Host (A ou AAAA)** .  
  
3.  Digite o nome e o endereço IP do servidor (por exemplo, DirectAccess-NLS.contoso.local) e o endereço do servidor correspondente (por exemplo, 192.168.x.x).  
  
4.  Clique em **Adicionar Host**, clique em **OK** e, em seguida, clique em **Concluído**.  
  
##  <a name="BKMK_AddSecurityGroup"></a> Etapa 4: Criar um grupo de segurança para os computadores cliente DirectAccess  
 Em seguida, criar um grupo de segurança a ser usado para os computadores cliente DirectAccess e, em seguida, adicionar as contas de computador ao grupo.  
  
#### <a name="to-add-a-security-group-for-client-computers-that-use-directaccess"></a>Para adicionar um grupo de segurança para computadores cliente que usam o DirectAccess  
  
1. No painel do Gerenciador do Servidor, clique em **Ferramentas** e clique em **Computadores e Usuários do Active Directory**.  
  
   > [!NOTE]
   >  Se você não vir **Computadores e Usuários do Active Directory** no menu **Ferramentas**, você precisa instalar o recurso. Para instalar os Grupos e Usuários do Active Directory, execute o seguinte cmdlet do Windows PowerShell como um administrador: `Install-WindowsFeature RSAT-ADDS-Tools`. Para obter mais informações, consulte [Instalando ou removendo o Pacote de Ferramentas de Administração de Servidor Remoto](https://technet.microsoft.com/library/cc730825.aspx).  
  
2. Na árvore de console, expanda o servidor, clique com o botão direito do mouse em **Usuários**, clique em **Novo**e, em seguida, clique em **Grupo**.  
  
3. Digite um nome de grupo, escopo de grupo e o tipo de grupo (criar um grupo de segurança) e, em seguida, clique em **OK**.  
  
   O novo grupo de segurança é adicionado para a pasta **Usuários**.  
  
#### <a name="to-add-computer-accounts-to-the-security-group"></a>Para adicionar contas de computador ao grupo de segurança  
  
1.  No painel do Gerenciador do Servidor, clique em **Ferramentas** e clique em **Computadores e Usuários do Active Directory**.  
  
2.  Na árvore de console, expanda o servidor e, em seguida, clique em **Usuários**.  
  
3.  Na lista de contas de usuário e grupos de segurança no servidor, clique com o botão direito do mouse no grupo de segurança que você criou para o DirectAccess e, em seguida, clique em **Propriedades**.  
  
4.  Na guia **Membros** , clique em **Adicionar**.  
  
5.  Na caixa de diálogo, digite os nomes das contas de computador que você deseja adicionar ao grupo, separando os nomes com um ponto e vírgula (;). Em seguida, clique em **Verificar nomes**.  
  
6.  Depois que as contas de computador forem validadas, clique em **OK**. Em seguida, clique em **OK**.  
  
> [!NOTE]
>  Você também pode usar a guia **Membro de** nas propriedades de conta de computador para adicionar a conta ao grupo de segurança.  
  
##  <a name="BKMK_EnableConfigureDA"></a> Etapa 5: Habilitar e configurar o DirectAccess  
 Para habilitar e configurar o DirectAccess no Windows Server Essentials, você deve concluir as etapas a seguir:  
  
-   [Etapa 5a: Habilitar o DirectAccess usando o Console de gerenciamento de acesso remoto](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableDA)  
  
-   [Etapa 5b: Remover o IPv6Prefix inválido em GPO RRAS (Windows Server Essentials apenas)](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_RemoveIPv6)  
  
-   [Etapa 5c: Habilitar os computadores cliente que executam o Windows 7 Enterprise para que usem o DirectAccess](#BKMK_Step4cWindows7Setup)  
  
-   [Etapa 5D: Configurar o servidor de local de rede](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NLS)  
  
-   [Etapa 5e: Adicionar uma chave do registro para ignorar a autoridade de certificação ao estabelecer um canal IPsec](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_CA)  
  
###  <a name="BKMK_EnableDA"></a> Etapa 5a: Habilitar o DirectAccess usando o console de Gerenciamento de Acesso Remoto  
 Esta seção fornece instruções passo a passo para habilitar o DirectAccess no Windows Server Essentials. Se você ainda não tiver configurado o VPN no servidor, você deverá fazer isso antes de iniciar este procedimento. Para obter instruções, consulte [gerenciar VPN](Manage-VPN-in-Windows-Server-Essentials.md).  
  
##### <a name="to-enable-directaccess-by-using-the-remote-access-management-console"></a>Para habilitar o DirectAccess usando o console de Gerenciamento de Acesso Remoto  
  
1.  Na página Inicial, abra **Gerenciamento de acesso remoto**.  
  
2.  No assistente para habilitar o DirectAccess, faça o seguinte:  
  
    1.  Revise os **Pré-requisitos do DirectAccess** e clique em **Avançar**.  
  
    2.  Na guia **Selecionar Grupos** , adicione o grupo de segurança que você criou anteriormente para clientes do DirectAccess. (Se você não tiver criado o grupo de segurança, consulte [etapa 4: Criar um grupo de segurança para o cliente DirectAccess computadores](#BKMK_AddSecurityGroup) para obter instruções.)  
  
    3.  Na guia **Selecionar Grupos**, clique em **Habilitar o DirectAccess apenas para computadores móveis** caso deseje permitir que computadores móveis usem o DirectAccess para acessar o servidor remotamente e clique em **Avançar**.  
  
    4.  Em **Topologia de Rede**, selecione a topologia do servidor e clique em **Avançar**.  
  
    5.  Em **Lista de Pesquisa de Sufixos DNS**, adicione outro sufixo DNS para computadores clientes, se necessário, e clique em **Avançar**.  
  
        > [!NOTE]
        >  Por padrão, o assistente Habilitar DirectAccess adiciona automaticamente o sufixo DNS para o domínio atual. Porém, você pode adicionar mais se necessário.  
  
    6.  Examine os GPOs (objetos de política de grupo) que serão aplicados e modifique-os se necessário.  
  
    7.  Clique em **Avançar**e em **Concluir**.  
  
    8.  Reinicie o serviço de Gerenciamento de acesso remoto executando o seguinte comando do Windows PowerShell no modo elevado:  
  
        ```powershell  
        Restart-Service RaMgmtSvc   
        ```  
  
###  <a name="BKMK_RemoveIPv6"></a> Etapa 5b: Remover o IPv6Prefix inválido em GPO RRAS (Windows Server Essentials apenas)  
  Esta seção se aplica a um servidor que executa o Windows Server Essentials.  
  
 Abra o Windows PowerShell como administrador e execute os seguintes comandos:  
  
```powershell  
gpupdate  
$key = Get-ChildItem -Path HKLM:\SOFTWARE\Policies\Microsoft\Windows\RemoteAccess\config\MachineSIDs | Where-Object{$_.GetValue("IPv6RrasPrefix") -ne $null}  
Remove-GPRegistryValue -Name "DirectAccess Server Settings" -Key $key.Name -ValueName IPv6RrasPrefix  
gpupdate  
```  
  
###  <a name="BKMK_Step4cWindows7Setup"></a> Etapa 5c: Habilitar os computadores cliente que executam o Windows 7 Enterprise para que usem o DirectAccess  
 Se você tiver computadores cliente que executam o Windows 7 Enterprise, conclua o procedimento a seguir para habilitar o DirectAccess nesses computadores.  
  
##### <a name="to-enable--windows-7-enterprise-computers-to-use-directaccess"></a>Para habilitar os computadores Windows 7 Enterprise usar o DirectAccess  
  
1.  Na página de início do servidor, abra **gerenciamento de acesso remoto**.  
  
2.  No Console de gerenciamento de acesso remoto, clique em **Configuração**. Em seguida, no painel **Detalhes da configuração**, na **Etapa 2**, clique em **Editar**.  
  
     O Assistente de instalação de servidor de acesso remoto é aberto.  
  
3.  Sobre o **autenticação** guia, escolha o certificado de autoridade de certificação que será o certificado raiz confiável (você pode escolher o certificado de autoridade de certificação do servidor do Windows Server Essentials). Clique em **Habilitar que os computadores cliente do Windows 7 se conectem via DirectAccess** e clique em **Avançar**.  
  
4.  Siga as instruções para concluir o assistente.  
  
> [!IMPORTANT]
>  Há um problema conhecido para computadores Windows 7 Enterprise que se conectam por meio do DirectAccess, quando o servidor do Windows Server Essentials não veio com UR1 pré-instalado. Para habilitar conexões do DirectAccess nesse ambiente, você deve executar estas etapas adicionais:  
> 
> 1. Instale o hotfix descrito em [artigo 2796394 da Base de Conhecimento Microsoft (KB)](https://support.microsoft.com/kb/2796394) no servidor do Windows Server Essentials. Em seguida, reinicie o servidor.  
>    2. Em seguida, instale o hotfix descrito em [artigo 2615847 da Base de Conhecimento Microsoft (KB)](https://support.microsoft.com/kb/2615847) em cada computador do Windows 7.  
> 
>    Esse problema foi resolvido no Windows Server Essentials.  
  
###  <a name="BKMK_NLS"></a> Etapa 5D: Configurar o servidor de local de rede  
 Esta seção fornece instruções passo a passo para definir as configurações do servidor de local de rede.  
  
> [!NOTE]
>  Antes de começar, copie o conteúdo da < SystemDrive\>pasta \inetpub\wwwroot para a < SystemDrive\>pasta Files\Windows server\bin\webapps\site\insideoutside. Copie também o arquivo default. aspx da < SystemDrive\>\Program Files\Windows Server\Bin\WebApps\Site pasta para o < SystemDrive\>pasta Files\Windows server\bin\webapps\site\insideoutside.  
  
##### <a name="to-configure-the-network-location-server"></a>Para configurar o servidor de local de rede  
  
1.  Na página Inicial, abra **Gerenciamento de acesso remoto**.  
  
2.  No console Gerenciamento de Acesso Remoto, clique em **Configuração** e, no painel de detalhes **Configuração de Acesso Remoto**, na **Etapa 3**, clique em **Editar**.  
  
3.  Em que o Assistente de instalação de servidor de acesso remoto, sobre o **servidor de local de rede** guia, selecione **o servidor de local de rede é implantado no servidor de acesso remoto**e, em seguida, selecione o certificado que foi emitido anteriormente (na [etapa 3: Preparar um certificado e o registro de DNS para o servidor de local de rede](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)).  
  
4.  Siga as instruções para concluir o assistente e clique em **Concluir**.  
  
###  <a name="BKMK_CA"></a> Etapa 5e: Adicione uma chave do Registro para ignorar a certificação de autoridade de certificação ao estabelecer um canal IPsec  
 A próxima etapa é configurar o servidor para ignorar a certificação de autoridade de certificação quando um canal IPsec é estabelecido.  
  
##### <a name="to-add-a-registry-key-to-bypass-the-ca-certification"></a>Para adicionar uma chave do Registro para ignorar a autoridade de certificação  
  
1.  Na página Inicial, abra **regedit** (o Editor do Registro).  
  
2.  No Editor do Registro, expanda **HKEY_LOCAL_MACHINE**, expanda **Sistema**, expanda **CurrentControlSet**, expanda **Serviços** e expanda **IKEEXT**.  
  
3.  Em **IKEEXT**, clique com botão direito do mouse em **Parâmetros**, clique em **Novo** e, em seguida, clique em **Valor DWORD (32 bits)** .  
  
4.  Renomeie o valor recém-adicionado como **ikeflags**.  
  
5.  Clique duas vezes em **ikeflags**, configure o **Tipo** como **Hexadecimal**, configure o valor como **8000**e clique em **OK**.  
  
> [!NOTE]
>  Você pode usar o seguinte comando do Windows PowerShell no modo elevado para adicionar essa chave do Registro:  
>   
>  `Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\IKEEXT\Parameters -Name ikeflags -Type DWORD -Value 0x8000`  
  
##  <a name="BKMK_NRPT"></a> Etapa 6: Configurar as definições da Tabela de Políticas de Resolução de Nomes para o servidor DirectAccess  
 Esta seção fornece instruções para edição de entradas da Tabela de Políticas de Resolução de Nomes (NPRT) para endereços internos (por exemplo, aqueles com um sufixo contoso.local) para GPOs de cliente do DirectAccess e definição do endereço da interface IPHTTPS.  
  
#### <a name="to-configure-name-resolution-policy-table-entries"></a>Para configurar as entradas da Tabela de Políticas de Resolução de Nomes  
  
1.  Na página Inicial, abra **Gerenciamento de Política de Grupo**.  
  
2.  No console Gerenciamento de Política de Grupo, clique na floresta e domínio padrão, clique com o botão direito em **Configurações do Cliente do DirectAccess** e clique em **Editar**.  
  
3.  Clique em **Configurações do Computador**, em **Políticas**, em **Configurações do Windows** e, em seguida, clique em **Política de Resolução de Nome**. Selecione a entrada cujo namespace é idêntico ao sufixo DNS e clique em **Editar Regra**.  
  
4.  Clique na guia **Configurações de DNS para DirectAccess** e selecione **Habilitar configurações de DNS para DirectAccess nesta regra**. Adicione o endereço IPv6 para a interface IP-HTTPS na lista de servidores DNS.  
  
    > [!NOTE]
    >  Você pode usar o seguinte comando do Windows PowerShell para obter o endereço IPv6:  
    >   
    >  `(Get-NetIPInterface -InterfaceAlias IPHTTPSInterface | Get-NetIPAddress -PrefixLength 128)[1].IPAddress`  
  
##  <a name="BKMK_TCPUDP"></a> Etapa 7: Configurar regras de firewall TCP e UDP para os GPOs do servidor do DirectAccess  
 Esta seção inclui instruções passo a passo para configurar regras de firewall TCP e UDP para os GPOs do servidor do DirectAccess  
  
#### <a name="to-configure-firewall-rules"></a>Para configurar regras de firewall  
  
1.  Na página Inicial, abra **Gerenciamento de Política de Grupo**.  
  
2.  No console Gerenciamento de Política de Grupo, clique na floresta e domínio padrão, clique com o botão direito em **Configurações do Servidor do DirectAccess**e clique em **Editar**.  
  
3.  Clique em **Configuração do computador**, em **Políticas**, em **Configurações do Windows**, em **Configurações de segurança**, em **Firewall do Windows com segurança avançada**, clique próximo nível **Firewall do Windows com segurança avançada** e, em seguida, clique em **Regras de entrada**. Clique com o botão direito do mouse em **Servidor de Nomes de Domínio (TCP-Entrada)** e clique em **Propriedades**.  
  
4.  Clique na guia **Escopo** e, na lista **Endereço IP Local**, adicione o endereço IPv6 da interface IP-HTTPS.  
  
5.  Repita o mesmo procedimento para **Servidor de Nomes de Domínio (UDP-Entrada)** .  
  
##  <a name="BKMK_DNS64"></a> Etapa 8: Alterar a configuração de DNS64 para escutar a interface IP-HTTPS  
 Você deve alterar a configuração DNS64 para escutar a interface IP-HTTPS usando o comando de Windows PowerShell a seguir.  
  
```powershell  
Set-NetDnsTransitionConfiguration -AcceptInterface IPHTTPSInterface  
```  
  
##  <a name="BKMK_ExemptPort"></a> Etapa 9: Reservar portas para o serviço WinNat  
 Usar o seguinte comando do Windows PowerShell para reservar portas para o serviço WinNat. Substitua "192.168.1.100" pelo endereço IPv4 do seu servidor Windows Server Essentials.  
  
```powershell  
Set-NetNatTransitionConfiguration -IPv4AddressPortPool @("192.168.1.100, 10000-47000")  
```  
  
> [!IMPORTANT]
>  Para evitar conflitos de porta com aplicativos, certifique-se de que o intervalo de portas reservado para o serviço WinNat não inclui a porta 6602.  
  
##  <a name="BKMK_WinNAT"></a> Etapa 10: Reiniciar o serviço WinNat  
 Reinicie o serviço Driver NAT do Windows (WinNat) executando o seguinte comando do Windows PowerShell.  
  
```powershell  
Restart-Service winnat  
```  
  
##  <a name="BKMK_AppendixBPowerShellScript"></a> Apêndice: Configurar o DirectAccess usando o Windows PowerShell  
 Esta seção descreve como instalar e configurar o DirectAccess usando o Windows PowerShell.  
  
### <a name="preparation"></a>Preparação  
 Antes de começar a configuração do servidor para o DirectAccess, você deve:  
  
1.  Siga o procedimento [etapa 3: Preparar um certificado e o registro de DNS para o servidor de local de rede](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS) para inscrever um certificado chamado **DirectAccess-NLS.contoso.com** (onde **contoso.com** é substituído pelo seu real nome de domínio interno) e para adicionar um registro DNS para o servidor de local de rede (NLS).  
  
2.  Adicionar um grupo de segurança chamado **DirectAccessClients** ao Active Directory e adicionar os computadores clientes para os quais deseja fornecer a funcionalidade do DirectAccess. Para obter mais informações, consulte [etapa 4: Criar um grupo de segurança para o cliente DirectAccess computadores](#BKMK_AddSecurityGroup).  
  
### <a name="commands"></a>Comandos  
  
> [!IMPORTANT]
>  No Windows Server Essentials, você precisa remover o GPO de prefixo IPv6 desnecessário. Exclua a seção de código com o seguinte rótulo: `# [WINDOWS SERVER 2012 ESSENTIALS ONLY] Remove the unnecessary IPv6 prefix GPO`.  
  
```powershell  
# Add Remote Access role if not installed yet  
$ra = Get-WindowsFeature RemoteAccess  
If ($ra.Installed -eq $FALSE) { Add-WindowsFeature RemoteAccess }  
  
# Server may need to restart if you installed RemoteAccess role in the above step  
  
# Set the internet domain name to access server, replace contoso.com below with your own domain name  
$InternetDomain = "www.contoso.com"  
#Set the SG name which you create for DA clients  
$DaSecurityGroup = "DirectAccessClients"  
#Set the internal domain name  
$InternalDomain = [System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain().Name  
  
# Set static IP and DNS settings  
$NetConfig = Get-WmiObject Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true"  
$CurrentIP = $NetConfig.IPAddress[0]  
$SubnetMask = $NetConfig.IPSubnet | Where-Object{$_ -like "*.*.*.*"}  
$NetConfig.EnableStatic($CurrentIP, $SubnetMask)  
$NetConfig.SetGateways($NetConfig.DefaultIPGateway)  
$NetConfig.SetDNSServerSearchOrder($CurrentIP)  
  
# Get physical adapter name and the certificate for NLS server  
$Adapter = (Get-WmiObject -Class Win32_NetworkAdapter -Filter "NetEnabled=$true").NetConnectionId  
$Certs = dir cert:\LocalMachine\My  
$nlscert = $certs | Where-Object{$_.Subject -like "*CN=DirectAccess-NLS*"}  
  
# Add regkey to bypass CA cert for IPsec authentication  
Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\IKEEXT\Parameters -Name ikeflags -Type DWORD -Value 0x8000  
  
# Install DirectAccess.   
Install-RemoteAccess -NoPrerequisite -DAInstallType FullInstall -InternetInterface $Adapter -InternalInterface $Adapter -ConnectToAddress $InternetDomain -nlscertificate $nlscert -force  
  
#Restart Remote Access Management service  
Restart-Service RaMgmtSvc  
  
# [WINDOWS SERVER 2012 ESSENTIALS ONLY] Remove the unnecessary IPv6 prefix GPO   
  
gpupdate  
$key = Get-ChildItem -Path HKLM:\SOFTWARE\Policies\Microsoft\Windows\RemoteAccess\config\MachineSIDs | Where-Object{$_.GetValue("IPv6RrasPrefix") -ne $null}  
Remove-GPRegistryValue -Name "DirectAccess Server Settings" -Key $key.Name -ValueName IPv6RrasPrefix  
gpupdate  
  
# Enable client computers running Windows 7 to use DirectAccess  
$allcertsinroot = dir cert:\LocalMachine\root  
$rootcert = $allcertsinroot | Where-Object{$_.Subject -like "*-CAA*"}  
Set-DAServer -IPSecRootCertificate $rootcert[0]  
Set -DAClient -OnlyRemoteComputers Disabled -Downlevel Enabled  
  
#Set the appropriate security group used for DA client computers. Replace the group name below with the one you created for DA clients  
Add-DAClient -SecurityGroupNameList $DaSecurityGroup   
Remove-DAClient -SecurityGroupNameList "Domain Computers"  
  
# Gather DNS64 IP address information  
$Remoteaccess = get-remoteaccess  
$IPinterface = get-netipinterface -InterfaceAlias IPHTTPSInterface | get-netipaddress -PrefixLength 128  
$DNS64IP=$IPInterface[1].IPaddress  
$Natconfig = Get-NetNatTransitionConfiguration  
  
# Configure TCP and UDP firewall rules for the DirectAccess server GPO  
$GpoName = 'GPO:'+$InternalDomain+'\DirectAccess Server Settings'  
Get-NetFirewallRule -PolicyStore $GpoName -Displayname "Domain Name Server (TCP-IN)"|Get-NetFirewallAddressFilter | Set-NetFirewallAddressFilter -LocalAddress $DNS64IP  
Get-NetFirewallrule -PolicyStore $GpoName -Displayname "Domain Name Server (UDP-IN)"|Get-NetFirewallAddressFilter | Set-NetFirewallAddressFilter -LocalAddress $DNS64IP  
  
# Configure the name resolution policy settings for the DirectAccess server, replace the DNS suffix below with the one in your domain  
$Suffix = '.' + $InternalDomain  
set-daclientdnsconfiguration -DNSsuffix $Suffix -DNSIPAddress $DNS64IP  
  
# Change the DNS64 configuration to listen to IP-HTTPS interface  
Set-NetDnsTransitionConfiguration -AcceptInterface IPHTTPSInterface  
  
# Copy the necessary files to NLS site folder  
XCOPY 'C:\inetpub\wwwroot' 'C:\Program Files\Windows Server\Bin\WebApps\Site\insideoutside' /E /Y  
XCOPY 'C:\Program Files\Windows Server\Bin\WebApps\Site\Default.aspx' 'C:\Program Files\Windows Server\Bin\WebApps\Site\insideoutside' /Y  
  
# Reserve ports for the WinNat service  
Set-NetNatTransitionConfiguration -IPv4AddressPortPool @("192.168.1.100, 10000-47000")  
  
# Restart the WinNat service  
Restart-Service winnat  
```  
  
## <a name="see-also"></a>Consulte também  
  
-   [Gerenciar o acesso em qualquer lugar](Manage-Anywhere-Access-in-Windows-Server-Essentials.md)  
  
-   [Gerenciar o Windows Server Essentials](Manage-Windows-Server-Essentials.md)
