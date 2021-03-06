---
title: Gerenciar áreas de trabalho virtuais
description: Saiba como gerenciar áreas de trabalho virtuais (VDI) no MultiPoint Services
ms.custom: na
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa9ac0ed-47cb-4811-91ff-4fcb62d7858b
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 7afc6d2a65cd5cd3b116db5d65fd97e4cc770690
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861437"
---
# <a name="manage-virtual-desktops"></a>Gerenciar áreas de trabalho virtuais
VDI de computador único permite que você configure cada *local* estação do MultiPoint Services para se conectar a um sistema de operacional de convidado do Windows 10 Enterprise em execução em uma máquina virtual do Hyper-V (VM) no mesmo computador do MultiPoint Services como o estação. Essas estações de área de trabalho virtual podem ser personalizadas com o aplicativo que não pode ser instalado em uma versão de servidor Windows.  
  
## <a name="enable-the-virtual-desktop-feature"></a>Habilitar o recurso de área de trabalho virtual  
  
1.  Abra o MultiPoint Manager e clique na guia **Áreas de Trabalho Virtuais**.  
  
2.  Em **VDI Tasks (Tarefas da VDI)**, clique em **criar área de trabalho virtual** e procure o .iso ou VHD do Windows 10 Enterprise.  
  
O sistema é reiniciado, o que pode levar vários minutos.  
  
## <a name="create-a-virtual-desktop-template"></a>Criar um modelo de área de trabalho virtual  
  
1.  Abra o MultiPoint Manager e clique na guia **Áreas de Trabalho Virtuais**.  
  
2.  Em **VDI Tasks (Tarefas da VDI)**, clique em **Create virtual desktop (Criar área de trabalho virtual)** e procure o .iso ou VHD do Windows 10 Enterprise.  
  
    Se estiver usando o DVD, o programa localizará automaticamente o arquivo .wim do Windows 10 Enterprise. Caso contrário, clique em **Procurar** e, em seguida, navegue até o .iso ou VHD do Windows 10 Enterprise.  
  
    Se desejar, modifique o prefixo. O prefixo padrão é o nome do computador host.  
  
    > [!NOTE]  
    > O prefixo é usado para nomear o modelo e as estações da área de trabalho virtual. O modelo é denominado com o prefixo \-t. As estações de área de trabalho virtual serão denominadas com o prefixo \-*n*, em que *n* é a ID da estação.  
  
4.  Insira um nome e uma senha para a conta de administrador local que será usada para fazer logon em todas as áreas de trabalho da estação virtual criadas por meio do modelo e, em seguida, clique em **OK**.  
  
    A criação do modelo leva vários minutos para ser concluída.  
      
    Em seguida, saiba como personalizar o modelo de suporte virtual.  
      
    > [!NOTE]  
    > Se o MultiPoint Server estiver adicionado a um domínio, a caixa de diálogo popula um campo adicional que permite que você indique se as máquinas virtuais que foram criadas do modelo devem ser adicionadas a um domínio.   
  
## <a name="import-a-virtual-desktop-template"></a>Importar um modelo de área de trabalho virtual  
No caso em que você criou um modelo de área de trabalho virtual em outro MultiPoint Server, você pode importar o modelo usando as seguintes etapas.  

1.  Abra o MultiPoint Manager e clique na guia **Áreas de Trabalho Virtuais**.  
  
2.  Nas tarefas de VDI, clique em **Import Virtual desktop template (Importar modelo de área de trabalho virtual)**.  
  
3.  Localize o modelo e defina o caminho e o prefixo para o modelo importado.  
  
## <a name="customize-the-virtual-desktop-template"></a>Personalizar o modelo de área de trabalho virtual  
Depois que você criou o modelo de área de trabalho virtual, você pode personalizá-lo com aplicativos, atualizações de software e definir configurações do sistema.   

1. Abra o MultiPoint Manager e clique na guia **Áreas de Trabalho Virtuais**.  
2. Escolha o modelo de área de trabalho virtual e clique em **Customize virtual desktop template (Personalizar o modelo de área de trabalho virtual)**.  
O modelo é aberto em uma janela separada e são fornecidas instruções adicionais que realçam as etapas mais importantes para personalizar o modelo virtual. Examine essas instruções cuidadosamente.  
  
## <a name="create-virtual-desktop-stations"></a>Criar estações de área de trabalho virtual  
  
1.  Abra o MultiPoint Manager no modo de estação e clique na guia **Áreas de Trabalho Virtuais**.  
  
    > [!NOTE]  
    > Se o sistema MultiPoint Services não estiver em execução no modo de estação, reinicie-o antes de concluir este procedimento.  
  
2.  Selecione o modelo de área de trabalho virtual na esquerda\-painel. Ele é chamado <prefix –t >.  
  
3.  Nas tarefas do modelo, clique em **Create virtual desktop stations (Criar estações de área de trabalho virtual)** e clique em **OK**.  
  
    O processo de criação da estação de área de trabalho virtual leva vários minutos.  
  
    > [!NOTE]  
    > Se qualquer uma das estações locais atualmente conectado a uma sessão\-virtual baseada em área de trabalho, você deverá fazer logoff dessas estações para que eles possam se conectar a uma das estações da área de trabalho virtual recém-criada.  
  
### <a name="validate-the-newly-created-customized-virtual-station-desktops"></a>Validar as áreas de trabalho da estação virtual personalizada recém-criadas  
  
Você pode validar suas áreas de trabalho da estação virtual personalizadas efetuando logon uma ou mais das estações da área de trabalho virtual usando uma conta de administrador local ou uma conta de domínio e, em seguida, verifique se que a nova VM\-trabalham com áreas de trabalho virtuais corretamente.  
  
## <a name="disable-virtual-desktops"></a>Desabilitar áreas de trabalho virtuais  
  
Ao desabilitar as áreas de trabalho virtuais o recurso Hyper-V será desativado. Todos os usuários serão desconectados e o sistema será reiniciado. Todas as estações virtuais são atribuídas a sessões locais do MultiPoint após a reinicialização do sistema.  

1. Abra o MultiPoint Manager no modo de estação e clique na guia **Áreas de Trabalho Virtuais**.  
  
2. Nas tarefas de VDI, clique em **Disable virtual desktops (Desabilitar áreas de trabalho virtuais)**. 