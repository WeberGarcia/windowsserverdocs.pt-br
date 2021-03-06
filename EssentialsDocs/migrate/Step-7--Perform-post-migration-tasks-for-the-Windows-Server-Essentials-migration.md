---
title: 'Etapa 7: Realizar tarefas pós-migração para a migração do Windows Server Essentials'
description: Descreve como usar o Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d382e3fd-d393-4bd0-883f-db50104a969f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 6a61d28f29097bcb6993a471587f4cc1ae0bcc3f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819157"
---
# <a name="step-7-perform-post-migration-tasks-for-the-windows-server-essentials-migration"></a>Etapa 7: Realizar tarefas pós-migração para a migração do Windows Server Essentials

>Aplica-se a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

As tarefas a seguir ajudaram a concluir a configuração do servidor de destino com algumas das mesmas configurações que estavam no servidor de origem. Você pode ter desabilitado algumas dessas configurações no servidor de origem durante o processo de migração para que elas não fossem migradas para o servidor de destino.  
  
1.  [Excluir entradas DNS para o servidor de origem](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md#BKMK_DeleteDNSEntries)  
  
2.  [Compartilhar a linha de negócios e outras pastas de dados de aplicativo](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md#BKMK_ShareLineOfBusinessAndOtherApplications)  
  
##  <a name="BKMK_DeleteDNSEntries"></a> Excluir entradas DNS para o servidor de origem  
 Depois de desativar o servidor de origem, o servidor do serviço de nomes de domínio (DNS) ainda pode conter entradas que apontem para o servidor de origem. Exclua essas entradas DNS.  
  
#### <a name="to-delete-dns-entries-that-point-to-the-source-server"></a>Para excluir as entradas DNS que apontam para o Servidor de Origem  
  
1.  No servidor de destino, abra o **Gerenciador de DNS**.  
  
2.  No Gerenciador DNS, clique com o botão direito no nome do servidor, clique em **Propriedades**e clique na guia **Encaminhadores** .  
  
3.  Determine se há uma entrada na lista de encaminhadores que aponte para o servidor de origem. Se houver, clique em **Editar** e exclua essa entrada na janela **Editar Encaminhadores**.  
  
4.  No **Gerenciador DNS**, expanda o nome do servidor e expanda **Zonas de Pesquisa Direta**.  
  
5.  Para cada zona de pesquisa direta, clique com o botão direito na zona, clique em **Propriedades** e clique na guia **Servidores de Nome**.  
  
6.  Selecione uma entrada na caixa de texto **Servidores de Nome** que aponte para o servidor de origem, clique em **Remover** e clique em **OK**.  
  
7.  Repita as etapas 5 e 6 até que todos os ponteiros para o servidor de origem sejam removidos.  
  
8.  Clique em **OK** para fechar a janela **Propriedades**.  
  
9. No **Gerenciador DNS**, expanda **Zonas de Pesquisa Inversa**.  
  
10. Repita as etapas de 6 a 9 para remover todas as Zonas de pesquisa inversa que apontam para o Servidor de origem.  
  
##  <a name="BKMK_ShareLineOfBusinessAndOtherApplications"></a> Compartilhar a linha de negócios e outras pastas de dados de aplicativo  
 Você deve definir as permissões da pasta compartilhada e as permissões NTFS para as pastas de dados de linha de negócios e de outros aplicativos que você copiou para o Servidor de Destino. Depois de definir as permissões, as pastas compartilhadas são exibidas no Painel na guia **Armazenamento** .  
  
 Se você estiver usando um script de logon para mapear unidades para as pastas compartilhadas, deverá atualizar o script para mapear para as unidades no Servidor de Destino.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você realizou as tarefas de pós-migração para a migração do Windows Server Essentials. Agora vá para [etapa 8 – executar o analisador de práticas recomendadas do Windows Server Essentials](Step-8--Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  
  

Para exibir todas as etapas, consulte [migrar para o Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

