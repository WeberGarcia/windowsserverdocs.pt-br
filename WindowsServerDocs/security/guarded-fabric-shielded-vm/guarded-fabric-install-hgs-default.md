---
title: Instalar o HGS em uma nova floresta
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 84f88d96f1e16767dec3b21b34aa226e544afaac
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447398"
---
# <a name="install-hgs-in-a-new-forest"></a>Instalar o HGS em uma nova floresta 

>Aplica-se a: Windows Server 2019, Windows Server (canal semestral), Windows Server 2016

## <a name="add-the-hgs-server-role"></a>Adicionar a função de servidor HGS

Execute os seguintes comandos em uma sessão elevada do PowerShell para adicionar a função de servidor HGS e instalar o HGS.

[!INCLUDE [Install the HGS server role](../../../includes/guarded-fabric-install-hgs-server-role.md)] 

## <a name="install-hgs"></a>Instalar o HGS 

[!INCLUDE [Install HGS by default](../../../includes/install-hgs-default.md)] 

## <a name="next-steps"></a>Próximas etapas

- Para as próximas etapas para configurar o atestado de TPM, consulte [inicializar o cluster HGS usando o modo TPM em uma floresta nova dedicada (padrão)](guarded-fabric-initialize-hgs-tpm-mode-default.md).
- Para as próximas etapas para configurar o atestado de chaves do host, consulte [inicializar o cluster HGS usando o modo de chave em uma floresta nova dedicada (padrão)](guarded-fabric-initialize-hgs-key-mode-default.md).
- Para as próximas etapas para configurar o Atestado baseado em Admin (substituído no Windows Server 2019), consulte [inicializar o cluster HGS usando modo AD em uma floresta nova dedicada (padrão)](guarded-fabric-initialize-hgs-ad-mode-default.md).

## <a name="next-step"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Iniciar o HGS](guarded-fabric-initialize-hgs.md)


