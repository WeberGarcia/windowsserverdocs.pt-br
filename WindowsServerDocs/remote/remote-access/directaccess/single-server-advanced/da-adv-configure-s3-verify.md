---
title: Etapa 3 verificar a implantação do DirectAccess avançado
description: Este tópico faz parte do guia de implantar um único servidor DirectAccess com avançadas configurações para o Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae8bbff0-c981-4bc6-8df1-861621d0627f
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 386d10dda9f61724a012801840e6471e48c0905a
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67283545"
---
# <a name="step-3-verify-the-advanced-directaccess-deployment"></a>Etapa 3 verificar a implantação do DirectAccess avançado

>Aplica-se a: Windows Server (canal semestral), Windows Server 2016

Este tópico descreve como verificar se você configurou corretamente a implantação do DirectAccess.  
  
### <a name="to-verify-access-to-internal-resources-through-directaccess"></a>Para verificar o acesso aos recursos internos por meio do DirectAccess  
  
1.  Conectar um computador cliente DirectAccess à rede corporativa e obter o objeto de diretiva de grupo.  
  
2.  Clique o **conexões de rede** ícone na área de notificação para acessar o Gerenciador de mídia do DirectAccess.  
  
3.  Clique em **Conexão do DirectAccess**, e você verá que o status é **conectado localmente**.  
  
4.  Conecte o computador cliente à rede externa e tentar acessar os recursos internos.  
  
    Você deve conseguir acessar todos os recursos corporativos.  
  
## <a name="BKMK_Links"></a>Etapa anterior  
  
-   [Etapa 2: Configurar o servidor DirectAccess](Step-2-Configuring-DirectAccess-Servers.md)  
  


