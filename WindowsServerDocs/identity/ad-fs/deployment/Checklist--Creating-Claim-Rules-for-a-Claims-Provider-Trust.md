---
ms.assetid: 503733f8-be0c-429c-81f0-cd4205e8b118
title: Lista de verificação - criando regras de declaração para um provedor de declarações de confiança
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 708919691f88cc49d1f2bd74d8f4255e1a854353
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66192393"
---
# <a name="checklist-creating-claim-rules-for-a-claims-provider-trust"></a>Lista de verificação: Criando regras de declaração para um provedor de declarações de confiança


Esta lista de verificação inclui tarefas de planejamento, criação, e implantar regras de declaração que estão associadas um provedor de declarações de confiança nos serviços de Federação do Active Directory \(do AD FS\).  
  
> [!NOTE]  
> Execute as tarefas desta lista de verificação na ordem indicada. Quando um link de referência levar você a um procedimento, volte para este tópico depois de executar as etapas nesse procedimento para que você possa prosseguir com as tarefas restantes na lista de verificação.  
  
![Criando regras de declaração](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**lista de verificação: Criando um conjunto de regras de declaração para uma relação de confiança do provedor de declarações**  
  
||Tarefa|Referência|  
|-|--------|-------------|  
|![Criando regras de declaração](media/icon_checkboxo.gif)|Examine os conceitos sobre declarações, regras de declaração, conjuntos de regras de declaração e como eles são associados com relações de confiança federadas e modelos de regra de declaração.|![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Claims](../../ad-fs/technical-reference/The-Role-of-Claims.md)<br /><br />![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Claim Rules](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md)|  
|![Criando regras de declaração](media/icon_checkboxo.gif)|Examine os conceitos sobre como uma declaração flui em todos os estágios no pipeline de emissão de declarações e como as regras são processadas pelo mecanismo de emissão de declarações.|![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claims Pipeline](../../ad-fs/technical-reference/The-Role-of-the-Claims-Pipeline.md)<br /><br />![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claims Engine](../../ad-fs/technical-reference/The-Role-of-the-Claims-Engine.md)|  
|![Criando regras de declaração](media/icon_checkboxo.gif)|Para planejar e implementar as declarações de saída que serão emitidas por essa relação de confiança do provedor de declarações com eficiência, determine se uma ou mais regras de declaração são necessários e que você deve usar com essa relação de confiança do provedor de declarações de regras de declaração.|![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[determinar o tipo de declaração de modelo de regra para uso](../../ad-fs/technical-reference/Determine-the-Type-of-Claim-Rule-Template-to-Use.md)|  
|![Criando regras de declaração](media/icon_checkboxo.gif)|Examine os conceitos sobre quando criar uma declaração de regra em relação a outra e como você pode usar a linguagem de regra de declaração para fornecer uma lógica mais complexa que as regras padrão para fornecer um resultado desejado na saída ideal conjunto de declarações.|![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[quando usar uma passagem ou filtro de regra de declaração](../../ad-fs/technical-reference/When-to-Use-a-Pass-Through-or-Filter-Claim-Rule.md)<br /><br />![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[quando usar uma regra de transformação de declaração](../../ad-fs/technical-reference/When-to-Use-a-Transform-Claim-Rule.md)<br /><br />![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[quando usar a Send LDAP Attributes as Claims Rule](../../ad-fs/technical-reference/When-to-Use-a-Send-LDAP-Attributes-as-Claims-Rule.md)<br /><br />![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[quando usar uma associação de grupo Enviar como uma regra de declaração](../../ad-fs/technical-reference/When-to-Use-a-Send-Group-Membership-as-a-Claim-Rule.md)<br /><br />![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[quando usar uma regra de declaração personalizada](../../ad-fs/technical-reference/When-to-Use-a-Custom-Claim-Rule.md)<br /><br />![Criando regras de declaração](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of a linguagem da regra de declaração](../../ad-fs/technical-reference/The-Role-of-the-Claim-Rule-Language.md)|  
|![Criando regras de declaração](media/icon_checkboxo.gif)|Uma descrição de declaração deve ser criada se ainda não existir que atenderá as necessidades da sua organização. O AD FS é fornecido com um conjunto padrão de descrições de declarações que são expostos no snap do gerenciamento do AD FS\-no.|![Criando regras de declaração](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[adicionar uma descrição de declaração](../../ad-fs/operations/Add-a-Claim-Description.md)|  
|![Criando regras de declaração](media/icon_checkboxo.gif)|Dependendo das necessidades da sua organização, crie uma ou mais regras de declaração para o conjunto de regras de transformação de aceitação que está associado essa relação de confiança do provedor de declarações para que as declarações serão emitidas adequadamente.|![Criando regras de declaração](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[criar uma regra para passar ou filtrar uma declaração de entrada](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)<br /><br />![Criando regras de declaração](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[crie uma regra para enviar atributos LDAP como declarações](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)<br /><br />![Criando regras de declaração](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[criar uma regra enviar associação do grupo como uma declaração](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)<br /><br />![Criando regras de declaração](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[criar uma regra para transformar uma declaração de entrada](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)<br /><br />![Criando regras de declaração](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[criar uma regra para enviar uma declaração de método de autenticação](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)<br /><br />![Criando regras de declaração](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[criar uma regra para enviar um AD FS 1.x compatível de declaração](../../ad-fs/operations/Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)<br /><br />![Criando regras de declaração](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[crie uma regra para enviar declarações usando uma regra personalizada](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)|  
  

