---
title: Configurar auditoria da triagem de arquivo
description: Este artigo descreve como configurar a auditoria de triagem de arquivo para gerar o relatório de auditoria de triagem de arquivo
ms.date: 7/7/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 89592a9e1f61374d2d909678a91dc4a06e0b1972
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824467"
---
# <a name="configure-file-screen-audit"></a>Configurar auditoria da triagem de arquivo

> Aplica-se a: Windows Server (canal semestral), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Usando o Gerenciador de recursos do servidor de arquivos, você pode gravar atividade de triagem de arquivo em um banco de dados de auditoria. As informações salvas neste banco de dados são usadas para gerar o relatório de auditoria de triagem de arquivo.

> [!Important]
> Se a caixa de seleção **Registrar atividade de triagem de arquivo no banco de dados de auditoria** estiver desmarcada, os relatórios de auditoria de triagem de arquivos não conterão informações.

## <a name="to-configure-file-screen-audit"></a>Para configurar auditoria de triagem de arquivo

1.  Na árvore de console, clique com o botão direito do mouse em **Gerenciador de Recursos de Servidor de Arquivos** e em **Configurar Opções**. A caixa de diálogo **Opções do Gerenciador de Recursos de Servidor de Arquivos** é aberta.

2.  Na guia **Auditoria de triagem de arquivo**, selecione a caixa de seleção **Registrar atividade no banco de dados de auditoria de triagem de arquivo**.

3.  Clique em **OK**. Todos os arquivos de atividade de triagem agora serão armazenados no banco de dados de auditoria e podem ser exibidos executando um relatório de auditoria de triagem de arquivo.

## <a name="see-also"></a>Consulte também

-   [Opções do Gerenciador de recursos de servidor de arquivos de configuração](setting-file-server-resource-manager-options.md)
-   [Gerenciamento de relatórios de armazenamento](storage-reports-management.md)