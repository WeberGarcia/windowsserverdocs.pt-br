---
title: Controle de acesso baseado em função
description: Este tópico faz parte do guia de gerenciamento do gerenciamento de endereço IP (IPAM) no Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ecdfc589-fa14-4bb3-ab7e-456ebc719385
ms.author: pashort
author: shortpatti
ms.openlocfilehash: bb4c1a6a5f2ea708863be3cbf0abe436e12608de
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67282141"
---
# <a name="role-based-access-control"></a>Controle de acesso baseado em função

>Aplica-se a: Windows Server (canal semestral), Windows Server 2016

Este tópico fornece informações sobre como usar o controle de acesso baseado em função no IPAM.  
  
> [!NOTE]  
> Além deste tópico, a seguinte documentação de controle de acesso do IPAM está disponível nesta seção.  
>   
> -   [Gerenciar baseado em função com o Gerenciador do servidor de controle de acesso](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Server-Manager.md)  
> -   [Gerenciar função com base em controle com o Windows PowerShell de acesso](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Windows-PowerShell.md)  
  
Controle de acesso baseado em função permite que você especifique os privilégios de acesso em vários níveis, incluindo o servidor DNS, zona DNS e níveis de registro de recursos DNS.  
Usando o controle de acesso baseado em função, você pode especificar quem tem um controle granular sobre operações para criar, editar e excluir diferentes tipos de registros de recursos DNS.  
  
Você pode configurar o controle de acesso para que os usuários são restritos para as seguintes permissões.  
  
-   Os usuários podem editar apenas registros de recurso DNS específicos  
  
-   Os usuários podem editar os registros de recursos DNS de um tipo específico, como PTR ou MX  
  
-   Os usuários podem editar os registros de recurso DNS para regiões específicas  
  
## <a name="see-also"></a>Consulte também  
[Gerenciar baseado em função com o Gerenciador do servidor de controle de acesso](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Server-Manager.md)  
[Gerenciar função com base em controle com o Windows PowerShell de acesso](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Windows-PowerShell.md)  
[Gerenciar IPAM](Manage-IPAM.md)  
  


