---
title: Instalar servidores de conteúdo dos Serviços de Arquivo
description: Este tópico faz parte do BranchCache implantação guia para o Windows Server 2016, que demonstra como implantar o BranchCache nos modos de cache hospedado e distribuído para otimizar o uso de largura de banda WAN em filiais
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 74b0a5ed-dc20-4974-9d4b-2426987a01a1
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 496c0c1408c64216f29a31d5b22d3d9b48d4f44c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59855057"
---
# <a name="install-file-services-content-servers"></a>Instalar servidores de conteúdo dos Serviços de Arquivo

>Aplica-se a: Windows Server (canal semestral), Windows Server 2016

Para implantar servidores de conteúdo que executam a função de servidor de Serviços de Arquivo, instale o BranchCache para o serviço de função de arquivos de rede da função de servidor de Serviços de Arquivo. Além disso, você deve habilitar o BranchCache em compartilhamentos de arquivos de acordo com suas necessidades.  
  
Durante a configuração do servidor de conteúdo, você pode permitir a publicação do BranchCache de conteúdo para todos os compartilhamentos de arquivos ou pode selecionar um subconjunto de compartilhamentos de arquivos para publicar.  
  
> [!NOTE]  
> Quando você implanta um servidor de arquivos habilitados do BranchCache ou o servidor Web como um servidor de conteúdo, as informações de conteúdo agora são calculadas offline, bem antes de um cliente do BranchCache solicita um arquivo. Devido a essa melhoria, você não precisará configurar a publicação de hash para servidores de conteúdo, como fez na versão anterior do BranchCache.  
>   
> Essa geração automática de hash fornece um desempenho mais rápido e mais economia de largura de banda, porque as informações de conteúdo estão prontas para o primeiro cliente que solicita o conteúdo e cálculos já foram realizados.  
  
Consulte os tópicos a seguir para implantar servidores de conteúdo.  
  
-   [Configurar a função de servidor Serviços de arquivo](../../branchcache/deploy/Configure-the-File-Services-server-role.md)  
  
-   [Habilitar a publicação de Hash para servidores de arquivos](../../branchcache/deploy/Enable-Hash-Publication-for-File-Servers.md)  
  
-   [Habilitar o BranchCache em um compartilhamento de arquivos &#40;opcional&#41;](../../branchcache/deploy/enable-bc-on-file-share.md)  
  


