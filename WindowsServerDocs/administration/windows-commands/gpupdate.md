---
title: gpupdate
description: 'Tópico de comandos do Windows para * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fd4e567-2ce1-4637-b611-c2f0895e5708
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 61131d2bf253c66d93408bc66b78d1dca2502087
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59840587"
---
# <a name="gpupdate"></a>gpupdate



Atualiza as configurações de diretiva de grupo. Para obter exemplos de como esse comando pode ser usado, consulte [exemplos](#BKMK_Examples).

## <a name="syntax"></a>Sintaxe

```
gpupdate [/target:{Computer | User}] [/force] [/wait:<VALUE>] [/logoff] [/boot] [/sync] [/?]
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------|-----------|
|/target:{Computer | Usuário}|Atualiza apenas o usuário ou apenas as configurações de política de computador.|
|/force|Reaplica todas as configurações de política. Por padrão, somente as configurações de política que foram alteradas são aplicadas.|
|/wait:\<VALUE>|Define o número de segundos a aguardar para concluir antes de retornar ao prompt de comando de processamento de política. Quando o limite de tempo for excedido, o prompt de comando aparece, mas continua o processamento de diretiva. O valor padrão é 600 segundos. O valor **0** significa que não haverá espera. O valor **-1** significa aguardar indefinidamente.</br>Em um script, usando este comando com um limite de tempo especificado, você pode executar **gpupdate** e continue com os comandos que não dependem após a conclusão das **gpupdate**. Como alternativa, você pode usar esse comando sem limite de tempo especificado para permitir que o **gpupdate** concluir a execução antes da execução de outros comandos que dependem dele.|
|/logoff|Faz logoff depois que as configurações de diretiva de grupo foram atualizadas. Isso é necessário para extensões do lado do cliente de diretiva de grupo que não processam diretivas em um ciclo de atualização em segundo plano, mas processam quando um usuário faz logon. Exemplos incluem instalação de Software e redirecionamento de pasta direcionada ao usuário. Essa opção não tem efeito se não houver nenhum extensões chamadas que exijam um logoff.|
|/boot|Faz com que uma reinicialização do computador depois que as configurações de diretiva de grupo são aplicadas. Isso é necessário para extensões do lado do cliente de diretiva de grupo que não processam diretivas em um ciclo de atualização em segundo plano, mas processam uma diretiva na inicialização do computador. Os exemplos incluem a instalação do Software de computador-alvo. Essa opção não tem efeito se não houver nenhum extensões chamadas que exigem uma reinicialização.|
|/sync|Faz com que o próximo aplicativo de política de primeiro plano a ser feito de forma síncrona. Política de primeiro plano é aplicada no logon de usuário e de inicialização do computador. Você pode especificar isso para o usuário, computador ou ambos, usando o **/destino** parâmetro. O **/Force** e **/Wait** parâmetros serão ignorados se você especificá-los.|
|/?|Exibe a ajuda no prompt de comando.|

## <a name="remarks"></a>Comentários

-   O **gpupdate** comando está disponível no Windows Server 2008 R2, Windows Server 2008, Windows 7 Ultimate, Windows 7 Professional, Windows Vista Ultimate, Windows Vista Enterprise e Windows Vista Business.

## <a name="BKMK_Examples"></a>Exemplos

Força uma atualização do plano de fundo de todas as configurações de diretiva de grupo, independentemente se eles foram alterados.
```
gpupdate /force
```

#### <a name="additional-references"></a>Referências adicionais

-   [Group Policy TechCenter](https://go.microsoft.com/fwlink/?LinkID=145531)
-   [Chave de sintaxe de linha de comando](command-line-syntax-key.md)