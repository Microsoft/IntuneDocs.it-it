---
# required metadata

title: Criteri firewall per PC Windows | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteggere i PC Windows con criteri di Windows Firewall in Microsoft Intune
Microsoft Intune consente di proteggere i PC Windows gestiti usando il client Intune in diversi modi, ad esempio usando criteri che consentono di configurare Windows Firewall sui PC.

Se il client Intune per PC Windows non è ancora stato installato sui computer, vedere [Install the Windows PC client with Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md) (Installare il client PC Windows con Microsoft Intune).

Usare le informazioni delle sezioni seguenti per configurare, distribuire e monitorare i criteri di Windows Firewall sui PC Windows.

## Usare i criteri Intune per gestire Windows Firewall
I criteri di Windows Firewall consentono di creare e distribuire le impostazioni che controllano Windows Firewall nei PC gestiti. Non è possibile gestire le eccezioni personalizzate per Windows Firewall e queste impostazioni non influenzano i firewall di terze parti.

> [!NOTE]
> Se i criteri di Microsoft Intune e Criteri di gruppo sono configurati per gestire le stesse impostazioni nel PC, le impostazioni di Criteri di gruppo sostituiscono i criteri di Microsoft Intune. Per informazioni su come evitare i conflitti tra criteri di Intune e Criteri di gruppo, vedere [Resolve GPO and Microsoft Intune policy conflicts](resolve-gpo-and-microsoft-intune-policy-conflicts.md) (Risolvere i conflitti tra i criteri di oggetto Criteri di gruppo e Microsoft Intune).
>
> Se si vogliono distribuire le impostazioni di Windows Firewall nei computer che eseguono Windows Vista, è necessario innanzitutto installare l' [hotfix KB971800](http://support2.microsoft.com/kb/971800) in tali computer.

> [!IMPORTANT]
> Per gestire Windows Firewall con Intune, è necessario verificare che i due servizi seguenti siano abilitati nei computer gestiti:
>
> -   Windows Firewall
> -   Agente criteri IPsec

## Configurare un criterio di Windows Firewall

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Criteri** &gt; **Aggiungi criterio**.

2.  Configurare e distribuire un criterio delle **Impostazioni di Windows Firewall** . È possibile usare le impostazioni consigliate o personalizzare le impostazioni. Per altre informazioni su come creare e distribuire i criteri, vedere [Common Windows PC management tasks with the Microsoft Intune computer client](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) (Attività comuni di gestione di PC Windows con il client di Microsoft Intune).

    La sezione seguente illustra i valori che possono essere configurati nei criteri e i valori predefiniti che vengono usati se i criteri non vengono personalizzati.

Dopo aver distribuito il criterio di Windows Firewall, nella pagina **Tutti i criteri** dell'area di lavoro **Criteri** è possibile visualizzarne lo stato.

## Impostazioni dei criteri per Windows Firewall

### Attiva Windows Firewall

Queste impostazioni dei criteri abilitano Windows Firewall nei computer gestiti connessi a un dominio (ad esempio, all'area di lavoro), a una rete privata attendibile (ad esempio una rete domestica) o una rete non attendibile, pubblica (ad esempio quella di un bar). Il valore predefinito per tutte queste impostazioni è **Sì**, ovvero il valore più sicuro. 



### Blocca tutte le connessioni in ingresso, comprese quelle nell'elenco dei programmi consentiti

Queste impostazioni dei criteri configurano Windows Firewall in modo che blocchi il traffico in ingresso quando il computer gestito è connesso a un dominio (ad esempio, l'area di lavoro), a una rete privata attendibile (ad esempio una rete domestica) o a una rete non attendibile, pubblica (ad esempio quella di un bar). Il valore predefinito per tutte queste impostazioni è **Sì**, ovvero il valore più sicuro. 

> [!IMPORTANT]
> Se nel proprio ambiente sono presenti computer gestiti in cui viene eseguito Windows Vista senza Service Pack, è necessario installare l'aggiornamento associato all' [articolo 971800](http://go.microsoft.com/fwlink/?LinkId=188405) della Microsoft Knowledge Base oppure disattivare le impostazioni del criterio **Blocca tutte le connessioni in ingresso** nei criteri distribuiti a tali computer.

### Notifica all'utente quando Windows Firewall blocca un nuovo programma

Queste impostazioni dei criteri stabiliscono se Windows Firewall debba informare l'utente del PC quando blocca il traffico in ingresso quando il computer gestito è connesso a un dominio (ad esempio, l'area di lavoro), a una rete privata attendibile (ad esempio una rete domestica) o a una rete non attendibile, pubblica (ad esempio quella di un bar). Per tutte queste impostazioni, il valore predefinito è **Sì**.


### Eccezioni predefinite

Dopo aver configurato i valori di base precedenti, è possibile configurare le eccezioni che consentono a una parte del traffico di rete di attraversare il firewall indipendentemente dai valori configurati in precedenza. Per impostazione predefinita, nessuna di queste impostazioni è configurata.

|Nome impostazione|Dettagli|
|------------------|--------------------|
|**BranchCache - recupero contenuto**<br>(Windows 7 o versioni successive)|Consente ai client BranchCache di usare il protocollo HTTP per recuperare il contenuto l'uno dall'altro in modalità distribuita e dalla cache ospitata in modalità cache ospitata. Questa impostazione usa il protocollo HTTP.|
|**BranchCache - client cache ospitata**<br>(Windows 7 o versioni successive)|Consente ai client BranchCache di usare una cache ospitata. Viene usato il protocollo HTTPS.|
|**BranchCache - server cache ospitata**|Consente ai client BranchCache di usare una cache ospitata per comunicare con altri client. Viene usato il protocollo HTTPS.|
|**BranchCache - individuazione peer**<br>(Windows 7 o versioni successive)|Consente ai client BranchCache di usare il protocollo WS-Discovery per cercare la disponibilità dei contenuti nella subnet locale.|
|**Peer caching BITS**|Consente ai client di usare BITS (Background Intelligent Transfer Service, Servizio trasferimento intelligente in background) per individuare e condividere i file archiviati nella cache BITS nei client della stessa subnet. Vengono usati WSDAPI e RPC.|
|**Connessione a un proiettore di rete**|Consente agli utenti di connettersi a proiettori in reti cablate o wireless per proiettare presentazioni. Viene usato WSDAPI.|
|**Funzionalità di base rete**|Consente ai client di usare i protocolli IPv4 e IPv6 per connettersi alle risorse di rete.|
|**Distributed Transaction Coordinator**|Consente ai computer gestiti di coordinare le transazioni che aggiornano le risorse protette tramite transazioni, quali database, code di messaggi e file system.|
|**Condivisione file e stampanti**|Consente agli utenti di condividere i file e le stampanti locali con altri utenti della rete. Vengono usati NetBIOS, LLMNR, SMB e RPC.|
|**Gruppo Home**<br>(Windows 7 o versioni successive)|Consente ai computer gestiti di partecipare a una rete di Gruppo Home.|
|**Servizio iSCSI**|Consente ai computer gestiti di connettersi ai dispositivi e ai server iSCSI.|
|**Servizio di gestione delle chiavi**|Consente ai computer di essere conteggiati per la verifica delle licenze in ambienti aziendali.|
|**Media Center Extender**|Consente a Media Center Extender di comunicare con i computer che eseguono Windows Media Center. Vengono usati SSDP e qWave.|
|**Servizio Accesso rete**|Configura un canale di protezione tra i client di dominio e un controller di dominio per l'autenticazione di utenti e servizi. Viene usato RPC.|
|**Individuazione rete**|Consente ai computer di individuare altri dispositivi e di essere individuati da altri dispositivi nella rete. Vengono usati l'individuazione funzione, nonché i protocolli di rete SSDP, NetBIOS, LLMNR e UPnP.|
|**Avvisi e registri di prestazioni**|Consente di gestire da remoto il servizio Avvisi e registri di prestazioni. Viene usato RPC.|
|**Amministrazione remota**|Consente l'amministrazione remota del computer.|
|**Assistenza remota**|Consente agli utenti dei computer gestiti di richiedere assistenza remota da altri utenti della rete. Vengono usati i protocolli di rete SSDP, PNRP, Teredo e UPnP.|
|**Desktop remoto**|Consente al computer di usare Desktop remoto per accedere ad altri computer.|
|**Gestione remota registro eventi**|Consente di visualizzare e gestire da remoto i registri eventi del client. Vengono usati Named Pipe e RPC.|
|**Gestione remota attività pianificate**|Consente la gestione remota del servizio di pianificazione delle attività. Viene usato RPC.|
|**Gestione remota servizi**|Consente la gestione remota dei servizi locali nei client. Vengono usati Named Pipe e RPC.|
|**Gestione volumi remota**|Consente la gestione remota dei volumi dei dischi hardware e software. Viene usato RPC.|
|**Routing e Accesso remoto**|Consente di stabilire connessioni VPN e di accesso remoto in ingresso ai computer.|
|**SSTP (Secure Socket Tunneling Protocol)**|Consente di stabilire connessioni VPN in ingresso ai computer gestiti usando il protocollo SSTP (Secure Socket Tunneling Protocol). Viene usato il protocollo HTTPS.|
|**Trap SNMP**|Consente ai computer gestiti di ricevere il traffico del servizio Trap SNMP.|
|**Framework UPnP**|Configura il servizio Framework UPnP nei computer per consentire di individuare e usare i dispositivi certificati UPnP.|
|**Servizio di registrazione nome computer per Funzioni di collaborazione Windows**|Consente ai computer di individuare e comunicare con altri computer usando il protocollo Peer Name Resolution Protocol. Vengono usati SSDP e PNRP.|
|**Windows Media Player**|Consente agli utenti di ricevere flussi multimediali via UDP.|
|**Servizio di condivisione in rete Windows Media Player**|Consente agli utenti di condividere file multimediali in rete. Vengono usati i protocolli di rete SSDP, qWave e UPnP.|
|**Servizio di condivisione in rete Windows Media Player (Internet)**<br>(Windows 7 o versioni successive)|Consente agli utenti di condividere file multimediali via Internet.|
|**Area riunioni virtuali Windows**|Consente agli utenti di collaborare in rete per condividere documenti, programmi o il desktop. Vengono usati DFSR e P2P.|
|**Windows Peer to Peer Collaboration Foundation**|Configura connessioni tramite programmi e tecnologie peer-to-peer. Vengono usati SSDP e PNRP.|
|**Gestione remota Windows (Compatibilità)**|Consente di configurare la gestione remota dei computer gestiti mediante WS-Management, un protocollo basato su servizi Web per la gestione remota di sistemi operativi e dispositivi.|
|**Gestione remota Windows**<br>(Windows 8 o versioni successive)|Consente di configurare la gestione remota dei computer gestiti mediante WS-Management, un protocollo basato su servizi Web per la gestione remota di sistemi operativi e dispositivi.|
|**Windows Virtual PC**<br>(Windows 7 o versioni successive)|Consente la comunicazione tra macchine virtuali e altri computer.|
|**Dispositivi portatili wireless**|Consente di trasferire file multimediali nei computer gestiti da fotocamere, videocamere o dispositivi multimediali che supportano la rete mediante il protocollo MTP (Media Transfer Protocol). Vengono usati i protocolli di rete SSDP e UPnP.|

### Vedere anche
[Policies to protect Windows PCs (Criteri per la protezione dei PC Windows)](policies-to-protect-windows-pcs-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


