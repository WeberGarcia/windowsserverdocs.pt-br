---
ms.assetid: 5fd4063d-34dc-4b15-9a88-cc6c1fff455a
title: Guia passo a passo – gerencie riscos com autenticação multifator adicional para aplicativos confidenciais
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: bd21f2d6e8dcb167aa2c614d096807305a7728d6
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66188891"
---
# <a name="walkthrough-guide-manage-risk-with-additional-multi-factor-authentication-for-sensitive-applications"></a>Guia Passo a passo: gerencie riscos com Multi-Factor Authentication adicional para aplicativos confidenciais




## <a name="about-this-guide"></a>Sobre este guia
Este passo a passo fornece instruções para configurar a autenticação multifator (MFA) no Active Directory Federation Services (AD FS) no Windows Server 2012 R2 com base nos dados de associação de grupo do usuário.

Para obter mais informações sobre mecanismos de autenticação e MFA no AD FS, consulte [gerenciar riscos com autenticação multifator adicional para aplicativos confidenciais](../../ad-fs/operations/Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md).

Este passo a passo consiste nas seguintes seções:

-   [Etapa 1: Configurando o ambiente de laboratório](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Conditional-Access-Control.md#BKMK_1)

-   [Etapa 2: Verifique se o mecanismo de autenticação do AD FS padrão](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_2)

-   [Etapa 3: Configurar a MFA no servidor de Federação](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_3)

-   [Etapa 4: Verifique se o mecanismo da MFA](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_4)

## <a name="BKMK_1"></a>Etapa 1: Configuração do ambiente de laboratório
Para concluir este passo a passo, é necessário um ambiente que consiste nos seguintes componentes:

-   Um domínio do Active Directory com um usuário de teste e contas de grupo, em execução no Windows Server 2012 R2 ou um domínio do Active Directory em execução no Windows Server 2008, Windows Server 2008 R2 ou Windows Server 2012 com seu esquema atualizado para o Windows Server 2012 R2

-   Um servidor de Federação em execução no Windows Server 2012 R2

-   Um servidor Web que hospede o aplicativo de exemplo

-   Um computador cliente do qual é possível acessar o aplicativo de exemplo

> [!WARNING]
> É altamente recomendável (em ambientes de produção ou de teste) que você não use o mesmo computador para ser o servidor de federação e o servidor Web.

Nesse ambiente, o servidor de federação emite as declarações que são necessárias para que os usuários possam acessar o aplicativo de exemplo. O servidor Web hospeda um aplicativo de exemplo que confiará nos usuários que apresentarem as declarações que o servidor de federação emitir.

Para obter instruções sobre como configurar esse ambiente, consulte [configurar o ambiente de laboratório para o AD FS no Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

## <a name="BKMK_2"></a>Etapa 2: Verificar mecanismo de autenticação AD FS padrão
Nesta etapa, você verificará o mecanismo de controle de acesso do AD FS padrão (**Autenticação de Formulários** para extranet e **Autenticação do Windows** para intranet), no qual o usuário é redirecionado para a página de entrada do AD FS, fornece credenciais válidas e recebe o acesso ao aplicativo. Você pode usar o **Robert Hatley** conta do AD e o **claimapp** que você configurou no aplicativo de exemplo [configurar o ambiente de laboratório para o AD FS no Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

1.  No computador cliente, abra uma janela do navegador e navegue até o aplicativo de exemplo: **https://webserv1.contoso.com/claimapp**.

    Essa ação automaticamente redireciona a solicitação ao servidor de federação, e você será solicitado a entrar com um nome de usuário e uma senha.

2.  Digite as credenciais do **Robert Hatley** que você criou na conta do AD [configurar o ambiente de laboratório para o AD FS no Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

    Você receberá acesso ao aplicativo.

## <a name="BKMK_3"></a>Etapa 3: Configure o MFA no seu servidor de federação
Há duas partes para configurar a MFA no AD FS no Windows Server 2012 R2:

-   [Selecione um método de autenticação adicionais](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_5)

-   [Configurar a política de MFA](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_6)

### <a name="BKMK_5"></a>Selecione um método de autenticação adicionais
Para configurar a MFA, é preciso selecionar um método de autenticação adicional. Neste passo a passo, para o método de autenticação adicional, é possível escolher entre as seguintes opções:

-   Selecione [autenticação de certificado](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_7) método que está disponível no AD FS no Windows Server 2012 R2, por padrão

-   Configure e selecione [Windows Azure Multi-Factor Authentication](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_8)

#### <a name="BKMK_7"></a>Autenticação de certificado
Complete qualquer um dos procedimentos a seguir para selecionar a autenticação de certificado como um método de autenticação adicional:

###### <a name="to-configure-certificate-authentication-as-an-additional-authentication-method-via-the-ad-fs-management-console"></a>Para configurar a autenticação de certificado como um método de autenticação adicional através do Console de Gerenciamento do AD FS

1.  No servidor de federação, no Console de Gerenciamento do AD FS, navegue até o nó **Políticas de autenticação** e, na seção **Autenticação Multifator** , clique no link **Editar** ao lado da sub-seção **Configurações Globais** .

2.  Na janela **Editar Política de Autenticação Global**, selecione **Autenticação de Certificado** como um método de autenticação adicional e clique em **OK**.

###### <a name="to-configure-certificate-authentication-as-an-additional-authentication-method-via-windows-powershell"></a>Para configurar a autenticação de certificado como um método de autenticação adicional através do Windows PowerShell

1.  No servidor de federação, abra a janela de comando do Windows PowerShell e execute o seguinte comando:

    ```
    Set-AdfsGlobalAuthenticationPolicy -AdditionalAuthenticationProvider CertificateAuthentication

    ```

    > [!WARNING]
    > Para verificar se esse comando foi executado com êxito, é possível executar o comando `Get-AdfsGlobalAuthenticationPolicy` .

#### <a name="BKMK_8"></a>Windows autenticação multifator do Azure
Conclua os procedimentos a seguir para baixar, configurar e selecionar a **autenticação multifator do Windows Azure** como autenticação adicional em seu servidor de federação:

1.  [Criar um provedor de autenticação multifator através do Windows Azure Portal](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_a)

2.  [Baixar o servidor de autenticação multifator do Azure da Microsoft](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_b)

3.  [Instale o servidor de autenticação multifator do Azure no servidor de Federação](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_c)

4.  [Configurar a autenticação multifator do Microsoft Azure como um método de autenticação adicional](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md#BKMK_d)

##### <a name="BKMK_a"></a>Criar um provedor de autenticação multifator através do Windows Azure Portal

1.  Faça logon no portal do Windows Azure como administrador.

2.  À esquerda, selecione Active Directory.

3.  Na página do Active Directory, na parte superior, selecione **Provedores de Autenticação Multifator**.  Na parte inferior, clique em **Novo**.

4.  Em **Serviços de Aplicativos->Active Directory**, selecione **Provedor de Autenticação Multifator** e depois **Criação Rápida**.

5.  Em **Serviços de Aplicativos**, selecione **Provedores de Autenticação Ativos**e depois **Criação Rápida**.

6.  Preencha os campos a seguir e selecione **Criar**.

    1.  **Nome** -o nome do provedor de autenticação multifator.

    2.  **Modelo de uso** -o modelo de uso do provedor de autenticação multifator.

        -   **Por autenticação** -modelo de compra que cobra por autenticação. Normalmente usado para cenários que usam a autenticação multifator do Windows Azure em um aplicativo de voltado ao consumidor.

        -   **Por usuário habilitado** -modelo de compra que cobra por usuário habilitado.  Normalmente usado para cenários voltados ao funcionário, como o Office 365.

        Para obter informações adicionais sobre modelos de uso, consulte [Detalhes de preços do Microsoft Azure](http://www.windowsazure.com/pricing/details/active-directory/).

    3.  **Diretório** -locatário o Windows Azure Active Directory que o provedor de autenticação multifator está associado. Isso é opcional, já que o provedor não precisa estar ligado ao Active Directory do Windows Azure durante a proteção de aplicativos no local.

7.  Depois de clicar em criar, o provedor de autenticação multifator será criado e você verá uma mensagem dizendo:  Provedor da Autenticação Multifator criado com êxito.  Clique em **Ok**.

Em seguida, é preciso baixar o servidor de autenticação multifator do Windows Azure. É possível fazer isso inicializando o portal de autenticação multifator do Windows Azure através do portal do Windows Azure.

##### <a name="BKMK_b"></a>Baixar o servidor de autenticação multifator do Azure da Microsoft

1.  Faça logon no portal do Windows Azure como administrador e clique no provedor de autenticação multifator que você criou no procedimento acima. Em seguida, clique no botão **Gerenciar** .

    Isso inicializa o portal de **Autenticação Multifator do Windows Azure** .

2.  No portal de **Autenticação Multifator do Windows Azure** , clique em **Downloads**, e em **Download** para baixar uma cópia do servidor de autenticação multifator do Windows Azure.

Depois de ter baixado o arquivo executável para o servidor de autenticação multifator do Windows Azure, é preciso instalá-lo no servidor de federação.

##### <a name="BKMK_c"></a>Instale o servidor de autenticação multifator do Azure no servidor de Federação

1.  Faça o download e clique duas vezes no arquivo executável para o servidor de autenticação multifator do Windows Azure.  Isso iniciará a instalação.

2.  Na tela Contrato de Licença, leia o contrato, selecione **Concordo** e clique em **Avançar**.

3.  Verifique se a pasta de destino está correta e clique em **Avançar**.

4.  Quando a instalação estiver concluída, clique em **Concluir**.

Agora você está pronto para iniciar o servidor de autenticação multifator do Windows Azure que você instalou no servidor de federação e configurá-lo como um método de autenticação adicional.

##### <a name="BKMK_d"></a>Configurar a autenticação multifator do Microsoft Azure como um método de autenticação adicional

1.  Inicie a **Autenticação Multifator do Windows Azure** de onde você a instalou no servidor de federação e, na página de Boas-vindas, marque a caixa de seleção **Pular o uso do Assistente de Configuração de Autenticação** e clique em **Avançar**.

2.  Para ativar o Servidor de Autenticação Multifator, volte para a página no portal de gerenciamento de Autenticação Multifator, onde você baixou o Servidor de Autenticação Multifator, e clique no botão **Gerar Credenciais de Ativação** . Na interface de usuário do Servidor de Autenticação Multifator, insira as credenciais que foram geradas e clique em **Ativar**.

3.  Em seguida, a interface de usuário do **Servidor de Autenticação Multifator** solicita que você execute o **Assistente de Configuração Multifator**.  Selecione **Não**.

    > [!IMPORTANT]
    > Você pode pular a conclusão do **Assistente de Configuração Multifator** por causa do ambiente de laboratório com apenas um servidor de federação que é usado para concluir este passo a passo. No entanto, se seu ambiente contiver vários servidores de federação, é preciso instalar o Servidor de Autenticação Multifator e concluir o **Assistente de Configuração Multifator** em cada servidor de federação para habilitar a replicação entre os servidores multifator em execução nos servidores de federação.

4.  Na interface de usuário do **Servidor Multi-Factor Authentication** , selecione o ícone **Usuários** , clique em **Importar do Active Directory**, selecione a conta de **Eduardo Gomes** para provisioná-la no Microsoft Azure Multi-Factor Authentication e clique em **Importar**.

5.  Na lista **Usuários** , selecione a conta de **Eduardo Gomes** , clique em **Editar**e, na janela **Editar Usuário** , forneça um número de telefone celular dessa conta, verifique se a caixa de seleção **Habilitado** está marcada e clique em **Aplicar**.

6.  Na lista **Usuários** , selecione a conta de **Eduardo Gomes** e clique em **Testar**. Na janela **Testar Usuário** , forneça as credenciais para a conta de **Eduardo Gomes** . Quando o celular tocar, pressione '#' para concluir a verificação de conta.

7.  Na interface de usuário do **Servidor de Autenticação Multifator** , selecione o ícone **AD FS** , verifique se as caixas de seleção **Permitir registro de usuário**, **Permitir que usuários selecionem método** (incluindo **Ligação** e **Mensagem de texto**), **Usar perguntas de segurança para fallback** e **Habilitar log** estão marcadas, clique em **Instalar Adaptador do AD FS**e conclua o assistente de instalação do **Adaptador do AD FS de Autenticação Multifator** .

    > [!NOTE]
    > O assistente de instalação do **Adaptador do AD FS de Autenticação Multifator** cria um grupo de segurança chamado **PhoneFactor Admins** no Active Directory e adiciona a conta de serviço do AD FS do serviço de federação a esse grupo.
    > 
    > É recomendável que você verifique no controlador de domínio se o grupo **PhoneFactor Admins** realmente foi criado e se a conta de serviço do AD FS é um membro desse grupo.
    > 
    > Se necessário, adicione manualmente a conta de serviço do AD FS ao grupo **PhoneFactor Admins** no controlador de domínio.

    Para obter detalhes adicionais sobre como instalar o Adaptador do AD FS, clique no link de ajuda no canto superior direito do Servidor de Autenticação Multifator.

8.  Para registrar o adaptador no serviço de federação, no servidor de federação, inicie a janela de comando do Windows PowerShell e execute o seguinte comando: `\Program Files\Multi-Factor Authentication Server\Register-MultiFactorAuthenticationAdfsAdapter.ps1`. O adaptador está agora registrado como **WindowsAzureMultiFactorAuthentication**.  É preciso reiniciar o serviço do AD FS para que o registro tenha efeito.

9. Para configurar a Autenticação Multifator do Windows Azure como método de autenticação adicional, no Console de Gerenciamento do AD FS, navegue até o nó **Políticas de autenticação** e, na seção **Autenticação Multifator**, clique no link **Editar** ao lado da sub-seção **Configurações Globais**. Na janela **Editar Política de Autenticação Global** , selecione **Autenticação Multifator** como um método de autenticação adicional e clique em **OK**.

    > [!NOTE]
    > É possível personalizar o nome e a descrição do método de Autenticação Multifator do Windows Azure, bem como qualquer método de autenticação configurado de terceiros, como aparece na interface de usuário do AD FS, executando o cmdlet **Set-AdfsAuthenticationProviderWebContent** . Para obter mais informações, consulte [https://technet.microsoft.com/library/dn479401.aspx](https://technet.microsoft.com/library/dn479401.aspx)

### <a name="BKMK_6"></a>Configurar a política de MFA
Para habilitar a MFA, é preciso configurar a política da MFA no servidor de federação. Para este passo a passo, conforme nossa política de MFA **Robert Hatley** conta é necessária para passar por MFA porque ele pertence à **Finanças** grupo que você configurou no [configurar o ambiente de laboratório para AD FS no Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

É possível configurar a política da MFA através do Console de Gerenciamento do AD FS ou usando o Windows PowerShell.

##### <a name="to-configure-the-mfa-policy-based-on-users-group-membership-data-for-claimapp--via-the-ad-fs-management-console"></a>Para configurar a política MFA com base em dados de associação de grupo do usuário para "claimapp" através do Console de gerenciamento do AD FS

1.  No servidor de federação, no Console de Gerenciamento do AD FS, navegue até o nó **Políticas de autenticação**\\**Por Objeto de Confiança da Terceira Parte Confiável** e selecione o objeto de confiança da terceira parte confiável que representa o aplicativo de exemplo (**claimapp**).

2.  Na página **Ações** ou clicando com o botão direito do mouse em **claimapp**, selecione **Editar Autenticação de Multifator Personalizada**.

3.  Na janela **Editar Objeto de Confiança da Terceira Parte Confiável para claimapp** , clique no botão **Adicionar** , ao lado da lista **Usuários/Grupos** . Digite **Finance** para o nome do grupo do AD que você criou na [configurar o ambiente de laboratório para o AD FS no Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md)e clique em **verificar nomes**, e quando é o nome resolvido, clique em **Okey**.

4.  Clique em **OK** na janela **Editar Objeto de Confiança da Terceira Parte Confiável para claimapp** .

##### <a name="to-configure-the-mfa-policy-based-on-users-group-membership-data-for-claimapp--via-windows-powershell"></a>Para configurar a política MFA com base em dados de associação de grupo do usuário para "claimapp" através do Windows PowerShell

1.  No servidor de federação, abra a janela de comando do Windows PowerShell e execute o seguinte comando:

    ```
    $rp = Get-AdfsRelyingPartyTrust -Name claimapp
    ```

2.  Na mesma janela de comando do Windows PowerShell, execute o seguinte comando:

    ```
    $GroupMfaClaimTriggerRule = 'c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid", Value =~ "^(?i) <group_SID>$"] => issue(Type = "https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod", Value = "https://schemas.microsoft.com/claims/multipleauthn");'
    Set-AdfsRelyingPartyTrust -TargetRelyingParty $rp -AdditionalAuthenticationRules $GroupMfaClaimTriggerRule

    ```

    > [!NOTE]
    > Substitua <group_SID> pelo valor do SID de seu grupo **Finanças** do AD.

## <a name="BKMK_4"></a>Etapa 4: verificar o mecanismo da MFA
Nesta etapa, você verificará a funcionalidade da MFA que configurou na etapa anterior. É possível usar o procedimento a seguir para verificar se o usuário do AD **Eduardo Gomes** pode acessar seu aplicativo de exemplo e, dessa vez, é necessário passar por MFA porque ele pertence ao grupo **Finanças**.

1.  No computador cliente, abra uma janela do navegador e navegue até o aplicativo de exemplo: **https://webserv1.contoso.com/claimapp**.

    Essa ação automaticamente redireciona a solicitação ao servidor de federação, e você será solicitado a entrar com um nome de usuário e uma senha.

2.  Digite as credenciais da conta do AD de **Eduardo Gomes** .

    Neste ponto, por causa da política do MFA que você configurou, o usuário será solicitado a passar por uma autenticação adicional. O texto de mensagem padrão é **por motivos de segurança, exigimos informações adicionais para verificar a sua conta.** No entanto, esse texto é totalmente personalizável. Para obter mais informações sobre como personalizar a experiência de entrada, consulte [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/library/dn280950.aspx).

    Se você configurou a autenticação de certificado como método de autenticação adicional, o texto da mensagem padrão é **selecionar um certificado que você deseja usar para autenticação. Se você cancelar a operação, feche seu navegador e tente novamente.**

    Se você configurou o Microsoft Azure Multi-Factor Authentication como o método de autenticação adicional, o texto de mensagem padrão é **Uma chamada será enviada para seu telefone para concluir sua autenticação.** Para obter mais informações sobre como entrar com o Microsoft Azure Multi-Factor Authentication e usando várias opções para o método preferencial de verificação, consulte [Visão geral do Microsoft Azure Multi-Factor Authentication](https://technet.microsoft.com/library/dn249479.aspx).

## <a name="see-also"></a>Consulte também
[Gerencie riscos com autenticação multifator adicional para aplicativos confidenciais](../../ad-fs/operations/Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)
[configurar o ambiente de laboratório para o AD FS no Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md)



