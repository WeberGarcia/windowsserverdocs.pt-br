---
title: Diretrizes de rede principal para o Windows Server
description: Este tópico fornece uma visão geral do guia da rede principal, que permite que você a planejar e implantar os componentes principais necessários para uma rede totalmente operacional e um novo domínio do Active Directory em uma nova floresta com o Windows Server 2016
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.date: ''
ms.assetid: 9b3ef3eb-4246-4e0e-8bf1-53224ca5f2f9
ms.author: pashort
author: shortpatti
ms.openlocfilehash: a905fd0c11237edd3a408998f8f71aa25a054328
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59847897"
---
# <a name="core-network-guidance-for-windows-server"></a>Diretrizes de rede principal para o Windows Server

>Aplica-se a: Windows Server, Windows Server 2016

Este tópico fornece uma visão geral das diretrizes de rede principal para o Windows Server&reg; 2016 e contém as seções a seguir.  
  
-   [Introdução à rede do Windows Server Core](#bkmk_intro)  
  
-   [Guia da rede principal para o Windows Server](#bkmk_core)  
  
## <a name="bkmk_intro"></a>Introdução à rede do Windows Server Core

Uma rede principal é um conjunto de hardware de rede, dispositivos e software que fornece os serviços fundamentais para as necessidades da TI (tecnologia da informação) de sua organização.

Uma rede principal do Windows Server fornece muitos benefícios, incluindo alguns a seguir.

- Os protocolos principais de conectividade da rede entre computadores e outros dispositivos compatíveis com os protocolos TCP/IP. TCP/IP é um conjunto de protocolos padrão para conexão de computadores e criação de redes. TCP/IP é software de protocolo de rede fornecido com o Microsoft&reg; Windows&reg; conjunto de protocolos de sistemas operacionais que implementa e oferece suporte a TCP/IP.

- Endereçamento IP automático do servidor DHCP A configuração manual dos endereços IP em todos os computadores na sua rede é demorado e menos flexível que fornecer dinamicamente computadores e outros dispositivos com concessões de endereço IP de um servidor DHCP.

- Serviços de resolução de nomes do DNS (Sistema de Nomes de Domínios) O DNS permite que os usuários, computadores, aplicativos e serviços encontrem os endereços IP dos computadores e dispositivos na rede usando o Nome de Domínio Totalmente Qualificado do computador ou dispositivo.

- Uma floresta, que é um ou mais domínios do Active Directory que compartilham as mesmas definições de classe e de atributo (esquema), informações de local e replicação (configuração) e capacidades de pesquisa da floresta (catálogo global).

- Um domínio raiz de floresta, que é o primeiro domínio criado em uma nova floresta. Os grupos Administradores de Empresa e Administradores de Esquema (que são grupos administrativos em toda a floresta) estão localizados no domínio raiz da floresta. Além disso, um domínio raiz da floresta, tal como acontece com outros domínios, é uma coleção de objetos de computador, de usuário e de grupo que são definidos pelo administrador no AD DS (Serviços de Domínio Active Directory). Esses objetos compartilham um banco de dados de diretório comum e políticas de segurança. Eles também poderão compartilhar relações de segurança com outros domínios se você adicionar domínios à medida que sua organização crescer. O serviço de diretório também armazena os dados de diretório e permite que computadores autorizados, aplicativos e usuários acessem os dados.

- Um banco de dados de contas de usuário e de computador. O serviço de diretório fornece um banco de dados de contas de usuário centralizado que permite que você crie contas de usuário e de computador para pessoas e computadores que estão autorizados a se conectar à sua rede e acessar os recursos da rede, como aplicativos, bancos de dados, arquivos e pastas compartilhados, e impressoras.

Uma rede principal também permite escalar sua rede à medida que sua organização cresce e os requisitos de TI mudam. Por exemplo, com uma rede principal, você pode adicionar domínios, sub-redes IP, serviços de acesso remoto, serviços sem fio e outros recursos e funções de servidor fornecidas pelo Windows Server 2016.

## <a name="bkmk_core"></a>Guia da rede principal para o Windows Server

Guia de rede do Windows Server 2016 Core fornece instruções sobre como planejar e implantar os componentes principais necessários para uma rede totalmente operacional e um novo Active Directory&reg; domínio em uma nova floresta. Usando este guia, você pode implantar os computadores configurados com os seguintes componentes de servidor do Windows:

- A função de servidor do AD DS (Serviços de Domínio Active Directory)

- A função de servidor DNS (Sistema de Nomes de Domínio)

- A função de servidor de protocolo de configuração de Host dinâmico (DHCP)

- O serviço de função do NPS (Servidor de Políticas de Rede) da função de servidor dos Serviços de Acesso e Política de Rede.

- A função de servidor Servidor Web (IIS)

- Conexões de protocolo TCP/IPv4 em servidores individuais

Este guia está disponível no seguinte local.

- O [guia da rede principal](../core-network-guide/Core-Network-Guide.md) na biblioteca técnica do Windows Server 2016.
  


