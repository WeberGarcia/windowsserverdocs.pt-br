---
title: Atualizações de Componentes do Active Directory Domain Services
description: Este documento aborda as atualizações de componentes do AD DS do Windows Server 2012 R2
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 09/08/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: a3a91034-a4da-4ad7-93f8-0cd2ec3e7824
ms.technology: identity-adds
ms.openlocfilehash: b0bd021863e1e25bd222baf9a633438153fe820b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66442763"
---
# <a name="active-directory-domain-services-component-updates"></a>Atualizações de Componentes do Active Directory Domain Services

>Aplica-se a: Windows Server 2016, Windows Server 2012 R2

Este módulo apresenta os componentes que receberam atualizações secundárias nos Serviços de Diretório e Espaços de Identidade.  


| Sobre o autor |
|------------------|
|   **Autor:**    |
|     **Biografia:**     |
| **Colaboradores** |
|  **Revisores**   |

> [!NOTE]  
> Este documento foi criado por um engenheiro de atendimento ao cliente da Microsoft e é destinado a administradores e arquitetos de sistemas experientes que procuram explicações técnicas mais profundas para recursos e soluções no Windows Server 2012 R2 do que aquelas geralmente oferecidas em tópicos do TechNet. No entanto, ele não passou pelas mesmas etapas de edição que eles, por isso a linguagem pode parecer que menos refinada do que a geralmente encontrada no TechNet.  

### <a name="what-you-will-learn"></a>O que você aprenderá  
Depois de concluir este módulo, você será capaz de:  

-   Explicar as atualizações de componente feitas nas áreas dos Serviços de Diretório e Tecnologia de Identidade no Windows Server 2012 R2  

    -   [Exclusividade de SPN e UPN](../../../ad-ds/manage/component-updates/SPN-and-UPN-uniqueness.md)  

    -   [Winlogon Automatic Restart Sign-On &#40;ARSO&#41;](../../../ad-ds/manage/component-updates/Winlogon-Automatic-Restart-Sign-On--ARSO-.md)  

    -   [Atestado de chave de TPM](../../../ad-ds/manage/component-updates/TPM-Key-Attestation.md)  

    -   [Cmdlets do Windows PowerShell de backup e restauração de AC](../../../ad-ds/manage/component-updates/CA-Backup-and-Restore-Windows-PowerShell-cmdlets.md)  

    -   [Auditoria de processo de linha de comando](../../../ad-ds/manage/component-updates/Command-line-process-auditing.md)  

    -   [Proteção e gerenciamento de credenciais](https://technet.microsoft.com/library/dn408190.aspx)  

    -   [Atualizações de componentes dos Serviços de Diretório](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md)  

        -   [Níveis funcionais de domínio e de floresta](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_FL)  

        -   [NTFRS preterido](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_NTFRS)  

        -   [Alterações do otimizador de consultas LDAP](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_LDAPQuery)  

        -   [Melhorias no evento 1644](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_1644)  

        -   [Melhoria da taxa de transferência de replicação do Active Directory](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_ADRepl)  



