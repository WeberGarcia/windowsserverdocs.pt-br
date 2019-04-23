---
title: rpcping
description: 'Tópico de comandos do Windows para * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7382aa0d-90fc-47c0-84b3-15f52dd656d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cfa1d08c81f8b26507a5cae5f688923a7b226e1d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59829987"
---
# <a name="rpcping"></a>rpcping

>Aplica-se a: Windows Server (canal semestral), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Confirma a conectividade RPC entre o computador que esteja executando o Microsoft Exchange Server e qualquer uma das estações de trabalho do cliente do Microsoft Exchange com suporte na rede. Esse utilitário pode ser usado para verificar se os serviços do Microsoft Exchange Server estão respondendo às solicitações RPC de estações de trabalho cliente por meio da rede. 

## <a name="syntax"></a>Sintaxe
```
rpcping [/t <protseq>] [/s <server_addr>] [/e <endpoint>
        |/f <interface UUID>[,Majorver]] [/O <Interface Object UUID]
        [/i <#_iterations>] [/u <security_package_id>] [/a <authn_level>]
        [/N <server_princ_name>] [/I <auth_identity>] [/C <capabilities>]
        [/T <identity_tracking>] [/M <impersonation_type>]
        [/S <server_sid>] [/P <proxy_auth_identity>] [/F <RPCHTTP_flags>]
        [/H <RPC/HTTP_authn_schemes>] [/o <binding_options>]
        [/B <server_certificate_subject>] [/b] [/E] [/q] [/c]
        [/A <http_proxy_auth_identity>] [/U <HTTP_proxy_authn_schemes>]
        [/r <report_results_interval>] [/v <verbose_level>] [/d]
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|-------|--------|
|/t \<protseq>|Especifica a sequência de protocolo para usar. Pode ser um do padrão de protocolo RPC, por exemplo: ncacn_ip_tcp, ncacn_np, ou ncacn_http.<br /><br />Se não for especificado, o padrão é ncacn_ip_tcp.|
|/s \<server_addr>|Especifica o endereço do servidor. Se não for especificado, o computador local será ping.|
|/e \<endpoint>|Especifica o ponto de extremidade para executar o ping. Se nenhum for especificado, o mapeador de ponto de extremidade no computador de destino será ping.<br /><br />Essa opção é mutuamente exclusiva com a interface (**/f**) opção.|
|/o \<binding_options>|Especifica as opções de associação para o ping RPC.|
|/f \<UUID de interface > [, Majorver]|Especifica a interface para executar o ping. Essa opção é mutuamente exclusiva com a opção de ponto de extremidade. A interface é especificada como um UUID.<br /><br />Se o *Majorver* não for especificado, a versão 1 da interface será procurado.<br /><br />Quando a interface for especificado, **rpcping** consultará o mapeador de ponto de extremidade no computador de destino para recuperar o ponto de extremidade para a interface especificada. O mapeador de ponto de extremidade será consultado usando as opções especificadas na linha de comando.|
|/O \<UUID do objeto >|Especifica o UUID do objeto se a interface registrada uma.|
|/i \<#_iterations>|Especifica o número de chamadas para fazer. O padrão é 1. Essa opção é útil para medir a latência de conexão se várias iterações forem especificadas.|
|/u \<security_package_id>|Especifica o pacote de segurança (provedor de segurança) RPC usará para fazer a chamada. O pacote de segurança é identificado como um número ou um nome. Se um número é usado é o mesmo número de API do RpcBindingSetAuthInfoEx. A lista a seguir mostra os nomes e números. Nomes não diferenciam maiusculas de minúsculas:<br /><br />-Negotiate / 9 ou um de nego, snego ou negocie<br />-NTLM / 10 ou NTLM<br />-SChannel / 14 ou SChannel<br />-Kerberos / 16 ou Kerberos<br />-Kernel / 20 ou Kernel<br />    Se você especificar essa opção, você deve especificar o nível de autenticação diferente de none. Não há nenhum padrão para essa opção. Se não for especificado, o RPC não usará segurança para o ping.|
|/a \<authn_level>|Especifica o nível de autenticação a ser usado. Os valores possíveis são:<br /><br />-conectar-se<br />-chamar<br />-pkt<br />-integridade<br />-privacidade<br /><br />Se essa opção for especificada, a ID de pacote de segurança (/ u) também deve ser especificado. Não há nenhum padrão para essa opção.<br /><br />Se essa opção não for especificada, o RPC não usará segurança para o ping.|
|/N \<server_princ_name>|Especifica um nome de entidade de segurança do servidor.<br /><br />Este campo pode ser usado apenas quando o pacote de segurança e nível de autenticação são selecionados.|
|/I \<auth_identity>|Permite que você especificar uma identidade alternativa para se conectar ao servidor. A identidade está no formulário usuário, domínio, senha. Se o nome de usuário, o domínio ou a senha tem caracteres especiais que podem ser interpretados pelo shell, coloque a identidade entre aspas duplas. Você pode especificar **\*** em vez da senha e o RPC solicitará que você insira a senha sem mostrá-la na tela. Se esse campo não for especificado, a identidade do usuário conectado será usada.<br /><br />Este campo pode ser usado apenas quando o pacote de segurança e nível de autenticação são selecionados.|
|/C \<capabilities>|Especifica uma máscara de bits hexadecimal dos sinalizadores. Este campo pode ser usado apenas quando o pacote de segurança e nível de autenticação são selecionados.|
|/T \<identity_tracking>|Especifica a estática ou dinâmica. Se não for especificado, dinâmico é o padrão.<br /><br />Este campo pode ser usado apenas quando o pacote de segurança e nível de autenticação são selecionados.|
|/M \<impersonation_type>|Especifica se anônimo, identificar, representam ou delegam. O padrão é impersonate.<br /><br />Este campo pode ser usado apenas quando o pacote de segurança e nível de autenticação são selecionados.|
|/S \<server_sid>|Especifica o SID esperado do servidor.<br /><br />Este campo pode ser usado apenas quando o pacote de segurança e nível de autenticação são selecionados.|
|/P \<proxy_auth_identity>|Especifica a identidade para autenticar com o proxy RPC/HTTP. Tem o mesmo formato de opção /I. Você deve especificar o pacote de segurança (/ u), nível de autenticação (/a) e esquemas de autenticação (/ H) para usar essa opção.|
|/F \<RPCHTTP_flags>|Especifica os sinalizadores a serem passados para a autenticação de front-end do RPC/HTTP. Os sinalizadores podem ser especificados como números ou nomes, que os sinalizadores reconhecidos no momento são:<br /><br />-Use SSL / 1 ou ssl ou use_ssl<br />-O esquema de autenticação primeiro uso / 2 ou o primeiro ou o use_first<br /><br />Você deve especificar o pacote de segurança (/ u) e o nível de autenticação (/) para usar essa opção.|
|/H \<RPC/HTTP_authn_schemes>|Especifica os esquemas de autenticação a ser usado para autenticação de front-end do RPC/HTTP. Essa opção é uma lista de nomes separados por vírgula ou valores numéricos. Exemplo: Basic, NTLM. Valores reconhecidos são (os nomes não diferenciam maiusculas de minúsculas):<br /><br />-Básica / 1 ou básico<br />-NTLM / 2 ou NTLM<br />-Certificado / 65536 ou certificado<br /><br />Você deve especificar o pacote de segurança (/ u) e o nível de autenticação (/) para usar essa opção.|
|/B \<server_certificate_subject>|Especifica a entidade do certificado de servidor. Você deve usar SSL para essa opção funcione.<br /><br />Você deve especificar o pacote de segurança (/ u) e o nível de autenticação (/) para usar essa opção.|
|/b|Recupera a entidade do certificado de servidor de certificado enviado pelo servidor e a imprime uma tela ou um arquivo de log. Válido somente quando o Proxy somente a opção de eco (/ E) e as opções de SSL de uso são especificadas.<br /><br />Você deve especificar o pacote de segurança (/ u) e o nível de autenticação (/) para usar essa opção.|
|/R|Especifica o proxy HTTP. Se *none*, o proxy RPC é usado. O valor *padrão* significa usar as configurações do IE no computador cliente. Qualquer outro valor será tratado como o proxy HTTP explícito. Se você não especificar esse sinalizador, presume-se o valor padrão, ou seja, as configurações do IE são verificadas. Esse sinalizador é válido somente quando o **/E** sinalizador (eco) está habilitado.|
|/E|Restringe o ping para o proxy RPC/HTTP apenas. O ping não alcançará o servidor. É útil ao tentar estabelecer se o proxy RPC/HTTP está acessível. Para especificar um proxy HTTP, use o sinalizador /R. Se um proxy HTTP é especificado no sinalizador de /o, essa opção será ignorada.<br /><br />Você deve especificar o pacote de segurança (/ u) e o nível de autenticação (/) para usar essa opção.|
|/q|Especifica o modo silencioso. Não emite avisos com exceção das senhas. Pressupõe *Y* resposta para todas as consultas. Use essa opção com cuidado.|
|/c|Use certificado de cartão inteligente. RPCPing solicitará que o usuário escolher o cartão inteligente.|
|/A|Especifica a identidade com o qual autenticar para o proxy HTTP. Tem o mesmo formato de opção /I.<br /><br />Você deve especificar os esquemas de autenticação (/ U), o pacote de segurança (/ u) e o nível de autenticação (/) para usar essa opção.|
|/U|Especifica os esquemas de autenticação a ser usado para autenticação de proxy HTTP. Essa opção é uma lista de nomes separados por vírgula ou valores numéricos. Exemplo: Basic, NTLM. Valores reconhecidos são (os nomes não diferenciam maiusculas de minúsculas):<br /><br />-Básica / 1 ou básico<br />-NTLM / 2 ou NTLM<br /><br />Você deve especificar o pacote de segurança (/ u) e o nível de autenticação (/) para usar essa opção.|
|/r|Se forem especificadas várias iterações, essa opção fará **rpcping** exibir estatísticas de execução atual periodicamente em vez disso, após a última chamada. O intervalo de relatório é fornecido em segundos. O padrão é 15.|
|/v|Informa **rpcping** como detalhado para fazer a saída. Valor padrão é 1. 2 e 3 fornecem mais saída de **rpcping**.|
|/d|Lançamentos de RPC de diagnóstico da interface do usuário de rede.|
|/p|Especifica para solicitar credenciais se a autenticação falhar.|
|/?|Exibe a ajuda no prompt de comando.|

## <a name="BKMK_Examples"></a>Exemplos
Para descobrir se seu servidor Exchange que você se conectar por meio de RPC/HTTP está acessível, digite:
```
rpcping /t ncacn_http /s exchange_server /o RpcProxy=front_end_proxy /P "username,domain,*" /H Basic /u NTLM /a connect /F 3
```

## <a name="additional-references"></a>Referências adicionais
-   [Chave de sintaxe de linha de comando](command-line-syntax-key.md)