---
title: Opções de seleção de sub-rede DHCP
description: This topic provides information about DHCP subnet selection options for Dynamic Host Configuration Protocol (DHCP) in Windows Server 2016.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dhcp
ms.topic: get-started-article
ms.assetid: ca19e7d1-e445-48fc-8cf5-e4c45f561607
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 43bc3d165f895767ded921b41118ecaccf9734e8
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="dhcp-subnet-selection-options"></a>Opções de seleção de sub-rede DHCP

>Aplica-se a: Windows Server (anual por canal), Windows Server 2016

You can use this topic for information about new DHCP subnet selection options.

DHCP agora dá suporte a opções 118 e 82 \(sub-option 5\). Você pode usar essas opções para permitir que os clientes de proxy DHCP e agentes de retransmissão solicitar um endereço IP para uma sub-rede específica e de um intervalo de endereços IP específico e escopo.

If you are using a DHCP proxy client that is configured with DHCP option 118, such as a virtual private network (VPN) server that is running Windows Server 2016 and the Remote Access server role, the VPN server can request IP address leases for VPN clients from a specific IP address range.

If you are using a DHCP relay agent that is configured with DHCP option 82, sub-option 5, the relay agent can request an IP address lease for DHCP clients from a specific IP address range.

Following are links to Request for Comments topics for these options.

- **Option 118**: [RFC 3011 IPv4 Subnet Selection Option for DHCP](http://www.rfc-base.org/rfc-3011.html)
- **Option 82 Sub Option 5**: [RFC 3527 Link Selection sub-option for the Relay Agent Information Option for DHCPv4](https://tools.ietf.org/html/rfc3527)


## <a name="dhcp-option-118-client-subnet-and-relay-agent-link-selection"></a>DHCP Option 118: Client Subnet and Relay Agent Link-Selection

The DHCP subnet selection option provides a mechanism for DHCP proxies to specify an IP subnet from which the DHCP server should assign IP addresses and options.

### <a name="use-case-scenario"></a>Use case scenario

In this scenario, a virtual private network \(VPN\) server allocates IP addresses to VPN clients. 

In this circumstance, the VPN server is connected to both the intranet where the DHCP server is installed and to the Internet, so that VPN clients can connect to the VPN server from remote locations.

Before the VPN server can provide IP address leases to VPN clients, the server contacts the DHCP server on an internal subnet and reserves a block of IP addresses. The VPN server then manages the IP addresses it obtained from the DHCP server. If the VPN server provides all of the reserved IP addresses in leases to VPN clients, the VPN server then obtains additional IP addresses from the DHCP server.

By configuring the VPN server with DHCP option 118, you can specify the IP address range and scope that you want to use for VPN clients. After you configure option 118, the VPN server requests IP addresses from a specific IP address range and scope from the DHCP server.

### <a name="the-dhcp-subnet-selection-option-field"></a>The DHCP subnet selection option field

The DHCP subnet selection option field contains a single IPv4 address used to represent the originating subnet address for a DHCP lease request.  A DHCP server that is configured to respond to this option allocates the address from either:

1. The subnet that is specified in the subnet selection option.
2. A subnet that is on the same network segment as the subnet that is specified in the subnet selection option.

## <a name="option-82-sub-option-5-link-selection-sub-option"></a>Option 82 Sub Option 5: Link Selection Sub Option

The Relay Agent Link Selection sub-option allows a DHCP Relay Agent to specify an IP subnet from which the DHCP server should assign IP addresses and options.

Typically, DHCP relay agents rely on the Gateway IP Address \(GIADDR\) field to communicate with DHCP servers. However, GIADDR is limited by its two operational functions:

1. To inform the DHCP server about the subnet upon which the DHCP client that is requesting the IP address lease resides.
2. To inform the DHCP server of the IP address to use to communicate with the relay agent.

In some cases, the IP address that the relay agent uses to communicate with the DHCP server might be different than the IP address range from which the DHCP client IP address needs to be allocated. 

DHCP relay agents cannot make use of option 118, as their functionality is limited and can only write to the GIADDR field or the Relay Agent Information Option \(option 82\). 

The Link Selection Sub option of option 82 is useful in this situation, allowing the relay agent to explicitly state the subnet from which it wants the IP address allocated in the form of DHCP v4 option 82 sub option 5.

### <a name="use-case-scenario"></a>Use case scenario

In this scenario, an organization network includes both a DHCP server and a Wireless Access Point \(AP\) for the guest users. Guests client IP addresses are assigned from the organization DHCP server - however, due to firewall policy restrictions, the DHCP server cannot access the guest wireless network or wireless clients with broadcase messages.

To resolve this restriction, the AP is configured with the Link Selection Sub Option 5 to specify the subnet from which it wants the IP address allocated for guest clients, while in the GIADDR also specifying the IP address of the internal interface that leads to the corporate network.
