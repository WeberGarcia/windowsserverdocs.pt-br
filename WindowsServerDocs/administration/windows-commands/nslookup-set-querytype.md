---
title: nslookup set querytype
description: 'Tópico de comandos do Windows para * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5af54ac5-fc1a-4af6-977b-f8e97c8eba90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f0015db716bd8c74bc4366063009bda41d338d19
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436734"
---
# <a name="nslookup-set-querytype"></a>nslookup set querytype

>Aplica-se a: Windows Server (canal semestral), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Altera o tipo de registro de recurso para a consulta.
## <a name="syntax"></a>Sintaxe
```
set querytype=<ResourceRecordtype>
```
## <a name="parameters"></a>Parâmetros
<ResourceRecordtype> Especifica um tipo de registro de recurso DNS. O tipo de registro de recurso padrão é A. A tabela a seguir lista os valores válidos para esse comando.

| Valor |                                                   Descrição                                                   |
|-------|-----------------------------------------------------------------------------------------------------------------|
|   A   |                                      Especifica um computador&#39;endereço IP                                      |
|  QUALQUER  |                                     Especifica um computador&#39;endereço IP.                                      |
| CNAME |                                    Especifica um nome canônico para um alias.                                     |
|  GID  |                                  Especifica um identificador de grupo de um nome de grupo.                                  |
| HINFO |                          Especifica um computador&#39;s da CPU e o tipo de sistema operacional.                           |
|  MB   |                                        Especifica um nome de domínio da caixa de correio.                                         |
|  MG   |                                         Especifica um membro do grupo de email.                                          |
| MINFO |                                   Especifica as informações da lista de caixa de correio ou email.                                   |
|  MR   |                                     Especifica o nome de domínio.                                      |
|  MX   |                                          Especifica o servidor de mensagens.                                          |
|  NS   |                                 Especifica um servidor de nomes DNS para a zona nomeada.                                 |
|  PTR  | Especifica um computador nome se a consulta é um endereço IP; Caso contrário, especifica o ponteiro para outras informações. |
|  SOA  |                                Especifica a início de autoridade para uma zona DNS.                                 |
|  TXT  |                                         Especifica as informações de texto.                                         |
|  UID  |                                         Especifica o identificador de usuário.                                          |
| UINFO |                                         Especifica as informações do usuário.                                         |
|  WKS  |                                         Descreve um serviço conhecido.                                         |
| {Ajuda |                                                       ?}                                                        |

Exibe um resumo breve dos <strong>nslookup</strong> subcomandos
## <a name="remarks"></a>Comentários
- O <strong>definir o tipo</strong> comando executa a mesma função que o <strong>definir querytype</strong> comando.
- Para obter mais informações sobre tipos de registro de recurso, consulte a solicitação de comentários (Rfc) 1035.
  ## <a name="additional-references"></a>Referências adicionais
  <a href="command-line-syntax-key.md" data-raw-source="[Command-Line Syntax Key](command-line-syntax-key.md)">Chave de sintaxe de linha de comando</a>
  <a href="nslookup-set-type.md" data-raw-source="[nslookup set type](nslookup-set-type.md)">nslookup defina tipo</a>
