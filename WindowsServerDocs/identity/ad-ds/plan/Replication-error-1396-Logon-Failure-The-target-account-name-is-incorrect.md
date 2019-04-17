---
ms.assetid: 399a8bbe-3375-4bb0-b55b-5f46e7050028
title: "Erro de replicação 1396 Logon falha no nome da conta de destino está incorreta"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 84799de26e1260f914d9b959357d5eed6fef62f6
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="replication-error-1396-logon-failure-the-target-account-name-is-incorrect"></a>Erro de replicação 1396 Logon falha no nome da conta de destino está incorreta

>Aplica-se a: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012


<developerConceptualDocument xmlns="https://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="https://www.w3.org/1999/xlink" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Este artigo descreve os sintomas, causa e como resolver replicação do Active Directory falha com erro Win32 1396: "Falha de Logon: O nome da conta de destino está incorreto." </para><list class="bullet"><listItem><para><link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Symptoms">Sintomas</link></para></listItem><listItem><para><link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Causes">faz com que</link></para></listItem><listItem><para><link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Resolutions">resoluções</link></para></listItem></list>
  </introduction>
  <section address="BKMK_Symptoms">
              
    <title>Symptoms</title>
    <content>
      <para />
      <list class="ordered">
<listItem><para>DCDIAG reports that the Active Directory Replications test has failed with error 1396: Logon failure: The target account name is incorrect."</para><code>Testing server: &lt;Site name&gt;&lt;DC Name&gt;
Starting test: Replications
[Replications Check,&lt;DC Name&gt;] A recent replication attempt failed:
From &lt;source DC&gt; to &lt;destination DC&gt;
Naming Context: CN=&lt;DN path of naming context&gt;
<codeFeaturedElement>The replication generated an error (1396):
Logon Failure: The target account name is incorrect.</codeFeaturedElement>
The failure occurred at &lt;date&gt; &lt;time&gt;.
The last success occurred at &lt;date&gt; &lt;time&gt;.
XX failures have occurred since the last success</code></listItem><listItem><para>REPADMIN.EXE reports that the last replication attempt has failed with status 1396.</para><para>REPADMIN commands that commonly cite the 1396 status include but are not limited to:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><tbody><tr><TD><list class="bullet"><listItem><para>/ADD REPADMIN</para></listItem><listItem><para>REPADMIN /REPLSUM</para></listItem><listItem><para>REPADMIN /REHOST</para></listItem><listItem><para>REPADMIN /SHOWVECTOR /LATENCY</para></listItem></list></TD><TD><list class="bullet"><listItem><para>REPADMIN /SHOWREPS</para></listItem><listItem><para>REPADMIN /SHOWREPL</para></listItem><listItem><para>REPADMIN /SYNCALL</para></listItem></list></TD></tr></tbody></table><para>Sample output from "REPADMIN /SHOWREPS" depicting inbound replication from CONTOSO-DC2 to CONTOSO-DC1 failing with the "Logon Failure: The target account name is incorrect." error is shown below::</para><code>Default-First-Site-NameCONTOSO-DC1
DSA Options: IS_GC 
Site Options: (none)
DSA object GUID: b6dc8589-7e00-4a5d-b688-045aef63ec01
DSA invocationID: b6dc8589-7e00-4a5d-b688-045aef63ec01
==== INBOUND NEIGHBORS ======================================
DC=contoso,DC=com
Default-First-Site-NameCONTOSO-DC2 via RPC
DSA object GUID: 74fbe06c-932c-46b5-831b-af9e31f496b2
Last attempt @ &lt;date&gt; &lt;time&gt; failed, <codeFeaturedElement>result 1396 (0x574):
Logon Failure: The target account name is incorrect.</codeFeaturedElement>
&lt;#&gt; consecutive failure(s).
Last success @ &lt;date&gt; &lt;time&gt;.
</code></listItem><listItem><para>The <ui>Replicate now</ui> command in Active Directory Sites and Services returns "Logon Failure: The target account name is incorrect."</para><para>Right-clicking on the connection object from a source DC and choosing <ui>Replicate now</ui> fails with "Logon Failure: The target account name is incorrect." The on-screen error message is shown below:</para><para>Dialog title text:</para><para>Replicate Now</para><para>Dialog message text: </para><para>The following error occurred during the attempt to synchronize naming context &lt;partition DNS path&gt; from domain controller &lt;source DC&gt; to domain controller &lt;destination DC&gt;: Logon Failure: The target account name is incorrect. This operation will not continue. </para></listItem><listItem><para>NTDS KCC, NTDS General or Microsoft-Windows-ActiveDirectory_DomainService events with the 1396 status are logged in the Directory Services log in Event Viewer.</para><para>Active Directory events that commonly cite the 1396 status include but are not limited to:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><thead><tr><TD><para>ID de evento</para></TD><TD><para>Origem do evento</para></TD><TD><para>Cadeia de caracteres de evento</para></TD></tr></thead><tbody><tr><TD><para>1125</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>O assistente domínio Active Directory serviços de instalação (Dcpromo) não conseguiu estabelecer conexão com o controlador de domínio a seguir.</para></TD></tr><tr><TD><para>1645</para><para>esse evento lista o SPN de três partes.</para></TD><TD><para>Replicação NTDS</para></TD><TD><para>No Active Directory não executou uma chamada de procedimento remoto autenticado (RPC) para outro controlador de domínio porque o controlador de domínio do Centro de distribuição de chaves (KDC) que resolve o SPN não é registrado o nome principal do serviço desejado (SPN) para o controlador de domínio de destino.</para></TD></tr><tr><TD><para>1655</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>Serviços de domínio do Active Directory tentou se comunicar com o seguinte catálogo global e as tentativas de foram malsucedidas.</para></TD></tr><tr><TD><para>2847</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>O verificador de consistência de dados de Conhecimento localizado uma conexão de replicação do serviço de diretório local somente leitura e tentou atualizá-lo remotamente na instância do serviço de diretório seguinte. Falha na operação. Ele será repetido.</para></TD></tr><tr><TD><para>1925</para></TD><TD><para>NTDS KCC</para></TD><TD><para>Falha ao tentar estabelecer um link de replicação para a partição de diretório gravável a seguir.</para></TD></tr><tr><TD><para>1926</para></TD><TD><para>NTDS KCC</para></TD><TD><para>A tentativa de estabelecer um link de replicação para uma partição de diretório somente leitura com os seguintes parâmetros falhou.</para></TD></tr><tr><TD><para>5781</para></TD><TD><para>LOGON DE REDE</para></TD><TD><para> O servidor não pode registrar seu nome no DNS.</para></TD></tr></tbody></table></listItem><listItem><para>DCPROMO fails with an onscreen error</para><para>Dialog Title Text:</para><para>Active Directory Installation Failed</para><para>Dialog Message text:</para><para>The operation failed because: The Directory Service failed to create the server object for CN=NTDS Settings,CN=ServerBeingPromoted,CN=Servers,CN=Site,CN=Sites,CN=Configuration,DC=contoso,DC=com on server ReplicationSourceDC.contoso.com. </para><para>Please ensure the network credentials provided have sufficient access to add a replica. </para><para> "Logon Failure: The target account name is incorrect. "</para><para>In this case, Event ID 1645, 1168, and 1125 are logged on the server that is being promoted.</para></listItem><listItem><para>Map a drive using <embeddedLabel>net use</embeddedLabel>:</para><code>C:&gt;net use z: &lt;server_name&gt;c$
System error 1396 has occurred.
Logon Failure: The target account name is incorrect.</code><para>In this case, the server can also logging Event ID 333 in the system event log and use a high amount of virtual memory for an application such as SQL Server.</para></listItem><listItem><para>The DC time is incorrect.</para></listItem><listItem><para>The KDC will not start on an RODC after a restore of the krbtgt account for the RODC, which had been deleted. For example, after a restore, error 1396 appears. </para><para> Event ID 1645 is logged on the RODC. </para><para> Dcdiag also reports an error that it cannot update the RODC krbtgt account. </para></listItem>
</list>
    </content>
  </section>
  <section address="BKMK_Causes">
    <title>faz com que</title>
    <content>
      <para />
      <list class="ordered">
        <listItem>
          <para>o SPN não existir no catálogo global pesquisado pelo KDC em nome do cliente tentando autenticar usando Kerberos.</para>
          <para>no contexto da replicação do Active Directory, o cliente Kerberos é o controlador de domínio, o KDC executa a pesquisa SPN de destino é provavelmente o controlador de domínio em si destino mas pode ser um controlador de domínio remoto.</para>
        </listItem>
        <listItem>
          <para>a conta de usuário ou serviço que deve conter o nome da entidade sendo pesquisado de serviço não existe no catálogo global pesquisado pelo KDC em nome de destino DC tentando replicar.</para>
          <para>no contexto da replicação do Active Directory, a conta de computador do controlador de domínio de origem não existe no catálogo global pesquisado pelo DC em nome a duplicação de entrada de desempenho de destino DC.</para>
        </listItem>
        <listItem>
          <para>o controlador de domínio de destino não tem um segredo LSA para o domínio de controladores de domínio de origem.</para>
        </listItem>
        <listItem>
          <para>o SPN sendo pesquisado existe em uma conta de computador diferente do que o controlador de domínio de origem.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMK_Resolutions">
    <title>Resoluções</title>
    <content>
      <list class="ordered">
        <listItem>
          <para>Verifique o log de eventos do serviço de diretório em que o controlador de domínio de destino para o evento de replicação NTDS 1645 e observe o seguinte:</para>
          <para>o nome do destino DC</para>
          <para>o SPN está sendo pesquisado (E3514235-4B06-11D1-AB04-00C04FC2DCD2 /&lt;guid para o objeto de configurações de NTDS de controladores de domínio de origem de objeto&gt;/&lt;domínio de destino&gt;.&lt; TLD&gt;@&lt;domínio de destino&gt;. &lt;tld&gt;</para>
          <para>o KDC está sendo usado pelo destino DC</para>
        </listItem>
        <listItem>
          <para>no console do KDC identificado na etapa 1, digite: </para>
          <code>nltest /dsgetdc &lt;forest root DNS domain name &gt; /gc</code>
          <para>execute o teste de localizador NLTEST imediatamente após uma tentativa de replicação falha com o erro 1396 sobre o controlador de domínio de destino. </para>
          <para>Isso deve identificar esse GC KDC está realizando pesquisas SPN contra. </para>
          <para>O GC está sendo pesquisado pelo KDC também pode ser captado no evento Microsoft-Windows-ActiveDirectory_DomainService 1655. </para>
        </listItem>
        <listItem>
          <para>Procure o SPN descoberto na etapa 1 no catálogo global descoberto na etapa 2. </para>
          <code>C:&gt;repadmin /showattr Server_Name DC=corp,DC=contoso,dc=com &lt;GC used by KDC&gt; &lt;DN path of forest root domain&gt; /filter:"(serviceprincipalname=&lt;SPN cited in the NTDS Replication event 1645&gt;)" /gc /subtree /atts:cn,serviceprincipalname</code>
          <para>Ou</para>
          <code>C:&gt;dsquery * forestroot -scope subtree -filter "(serviceprincipalname=E3514235-4B06-11D1-AB04-00C04FC2DCD2/65cead9f-4949-46a3-a49a-f1fbfe13d2b3*)" -attr * -s Server_Name.europe.corp.contoso.com</code>
          <para>Verifique se o objeto de host para o SPN existe. </para>
          <para>Verifique se o caminho DN para o objeto de host incluindo se o objeto é CNF / conflito desconfigurados ou reside no contêiner perdido e perdidos. </para>
          <para>Verificar se a fonte de controladores de domínio Active Directory replicação SPN está registrada somente na fonte de conta de computador de controladores de domínio. </para>
          <para>Se a replicação SPN estiver ausente, determinar se o controlador de domínio de origem registrou seu SPN com em si, e se o SPN está ausente no GC usado pelo KDC devido à latência da replicação simples ou uma falha na replicação. </para>
        </listItem>
        <listItem>
          <para>Verificar a integridade do canal seguro e confiável de integridade.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
    <externalLink>
      <linkText>operações do Active Directory de solução de problemas que uma falha com erro 1396: falha no Logon: O nome da conta de destino está incorreto.</linkText>
      <linkUri>https://support.microsoft.com/kb/2183411/en-gb</linkUri>
    </externalLink>
  </relatedTopics>
</developerConceptualDocument>


