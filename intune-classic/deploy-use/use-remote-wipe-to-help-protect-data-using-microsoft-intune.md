---
title: Usare la cancellazione remota per proteggere i dati
description: "Intune offre funzionalità di cancellazione selettiva e completa per rimuovere i dati aziendali riservati e impedire l'accesso a numerose risorse aziendali."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8519e411-3d48-44eb-9b41-3e4fd6a93112
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 85907167305e822ddf6a29475f032b2eb5f97a74
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="help-protect-your-data-with-full-or-selective-wipe-using-microsoft-intune"></a>Proteggere i dati con la cancellazione selettiva o completa tramite Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

È possibile cancellare app e dati non più necessari dai dispositivi gestiti da Intune che vengono reimpiegati o sono andati persi. A tale scopo, Intune offre funzionalità di cancellazione completa e selettiva. Gli utenti possono anche inviare un comando di cancellazione remota dei dati del dispositivo dall'app Portale aziendale di Intune nei dispositivi privati registrati in Intune.

  > [!NOTE]
  > Questo argomento riguarda solo la cancellazione dei dispositivi gestiti con la gestione dei dispositivi mobili di Intune. Anche il [portale di Azure](https://portal.azure.com) può essere usato per [cancellare i dati aziendali dalle app](wipe-managed-company-app-data-with-microsoft-intune.md). È anche possibile [ritirare i computer gestiti con il software client di Intune](retire-a-windows-pc-with-microsoft-intune.md).

## <a name="full-wipe"></a>Cancellazione completa

La **cancellazione completa** ripristina le impostazioni predefinite di un dispositivo rimuovendo tutti i dati e le impostazioni dell'azienda e dell'utente. Il dispositivo verrà rimosso da Intune. La cancellazione completa è utile per la reimpostazione di un dispositivo prima di consegnarlo a un nuovo utente o nei casi in cui il dispositivo è stato smarrito o rubato.  **Prestare attenzione alla selezione della cancellazione completa. Non sarà possibile recuperare i dati nel dispositivo**.


> [!Warning]
> I dispositivi Windows 10 RTM (ossia precedenti a Windows 10 versione 1511) con meno di 4 GB di RAM possono diventare inaccessibili se cancellati. Per accedere a un dispositivo Windows 10 che non risponde più, è possibile avviare il dispositivo da un'unità USB.

### <a name="remotely-wipe-a-device-from-the-intune-administrator-console"></a>Cancellare un dispositivo in modalità remota dalla console di amministrazione di Intune

1.  Selezionare i dispositivi da cancellare. Possono essere cercati per utente o per dispositivo.

    -   **Utente:**

        1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi**&gt;**Tutti gli utenti**

        2.  Scegliere il nome dell'utente il cui dispositivo mobile deve essere cancellato. Scegliere **Visualizza proprietà**

        3.  Nella pagina **Proprietà** relativa all'utente scegliere **Dispositivi**, quindi il nome del dispositivo mobile di cui cancellare i dati. Per selezionare più dispositivi, usare CTRL+clic.

    -   **Dispositivo:**

        1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi**&gt;**Tutti i dispositivi mobili**

         ![Avvio di un'operazione di ritiro o di cancellazione](../media/dev-sa-wipe.png)

        2.  Scegliere **Dispositivi**, quindi il nome del dispositivo mobile di cui cancellare i dati. Per selezionare più dispositivi, usare CTRL+clic.

2.  Scegliere **Disattiva/Cancella**.

3.  Verrà visualizzato un messaggio di conforma che richiede se si vuole ritirare il dispositivo.

    -   Per eseguire una **cancellazione selettiva** che rimuove solo le app e i dati aziendali, scegliere **Sì**.

    -   Per eseguire una **cancellazione completa** che cancella tutte le app e i dati e ripristina le impostazioni predefinite del dispositivo, scegliere **Cancellazione del dispositivo prima della disattivazione**. Questa azione si applica a tutte le piattaforme tranne Windows 8.1. **Non è possibile ripristinare i dati rimossi con una cancellazione completa**.

Se il dispositivo è acceso e connesso, un comando di cancellazione non richiede più di 15 minuti per propagarsi a tutti i tipi di dispositivo.

#### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Per eliminare i dispositivi nel portale di Azure Active Directory

1.  Accedere a [http://aka.ms/accessaad](http://aka.ms/accessaad) oppure fare clic su **Amministrazione** &gt; **Azure AD** da [https://portal.office.com](https://portal.office.com).

2.  Accedere con l'ID organizzazione usando il collegamento sul lato sinistro della pagina.

3.  Creare una sottoscrizione di Azure, se non se ne possiede una. Se si dispone di un account a pagamento, questa operazione non richiede l'uso di una carta di credito né un pagamento. Fare clic sul collegamento per l'abbonamento relativo alla **registrazione gratuita di Azure Active Directory**.

4.  Selezionare **Active Directory** e quindi l'organizzazione.

5.  Selezionare la scheda **Utenti** .

6.  Selezionare l'utente di cui si desidera eliminare i dispositivi.

7.  Scegliere **Dispositivi**.

8.  Rimuovere i dispositivi nel modo opportuno, ad esempio quelli che non sono più in uso o quelli con definizioni errate.


## <a name="selective-wipe"></a>Cancellazione selettiva

La **cancellazione selettiva** rimuove i dati aziendali, compresi i dati sulla gestione delle app mobili (MAM), ove applicabile, le impostazioni e i profili di posta elettronica da un dispositivo. La cancellazione selettiva lascia i dati personali dell'utente sul dispositivo. Il dispositivo verrà rimosso da Intune. Le tabelle seguenti descrivono i dati che vengono rimossi e l'effetto sui dati che rimangono nel dispositivo dopo una cancellazione selettiva. (Le tabelle sono organizzate in base alla piattaforma.)

**iOS**

|Tipo di dati|iOS|
|-------------|-------|
|App aziendali e dati associati installati da Intune|Le app vengono disinstallate e vengono rimossi i dati dell'app aziendale.<br /><br />I dati delle app Microsoft che usano la gestione delle app mobili vengono rimossi. L'app non viene rimossa.|
|Impostazioni|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|
|Agente di gestione|Il profilo di gestione viene rimosso.|
|Posta elettronica|I profili di posta elettronica di cui viene eseguito il provisioning tramite Intune vengono rimossi e il messaggio di posta elettronica memorizzato nella cache del dispositivo viene eliminato.|
|Outlook|I messaggi di posta elettronica ricevuti dall'app Microsoft Outlook per iOS vengono rimossi.|
|Separazione di Azure Active Directory (AAD)|Il record AAD viene rimosso.|
|Contatti | I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. <br /> <br />Attualmente è supportata solo l'app Outlook.

**Android**

|Tipo di dati|Android|Android Samsung KNOX Standard|
|-------------|-----------|------------------------|
|Collegamenti Web|Rimosso.|Rimosso.|
|App Google Play non gestite|Le app e i dati rimangono installati.|Le app e i dati rimangono installati.|
|App line-of-business non gestite|Le app e i dati rimangono installati.|Le app vengono disinstallate e, di conseguenza, i dati locali delle app vengono rimossi. Non vengono rimossi dati esterni all'app, ad esempio quelli in una scheda SD.|
|App Google Play gestite|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e sono inutilizzabili, ma non vengono rimossi.|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati, ma non vengono rimossi.|
|App line-of-business gestite|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e sono inutilizzabili, ma non vengono rimossi.|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e sono inutilizzabili, ma non vengono rimossi.|
|Impostazioni|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|
|Impostazioni del profilo certificato|Certificati revocati, ma non rimossi.|Certificati rimossi e revocati.|
|Agente di gestione|Il privilegio di amministratore del dispositivo viene revocato.|Il privilegio di amministratore del dispositivo viene revocato.|
|Posta elettronica|N/D. Vedere l'elemento di Outlook.|I profili di posta elettronica di cui viene eseguito il provisioning tramite Intune vengono rimossi e il messaggio di posta elettronica memorizzato nella cache del dispositivo viene eliminato.|
|Outlook|Il messaggio di posta elettronica ricevuto dall'app di Microsoft Outlook per Android viene rimosso, ma solo se Outlook è protetto tramite i criteri MAM. In caso contrario, Outlook non è viene cancellato durante l'annullamento della registrazione.|Il messaggio di posta elettronica ricevuto dall'app di Microsoft Outlook per Android viene rimosso, ma solo se Outlook è protetto tramite i criteri MAM. In caso contrario, Outlook non è viene cancellato durante l'annullamento della registrazione.|
|Separazione di Azure Active Directory (AAD)|Il record AAD viene rimosso.|Il record AAD viene rimosso.|
|Contatti | I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. <br /> <br />Attualmente è supportata solo l'app Outlook.|I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. <br /> <br />Attualmente è supportata solo l'app Outlook.

**Android for Work**

L'esecuzione di una cancellazione selettiva in un dispositivo Android for Work consente di rimuovere tutti i dati, le app e le impostazioni nel profilo di lavoro in tale dispositivo. Il dispositivo viene così ritirato dalla gestione con Intune. La cancellazione completa non è supportata per Android for Work.

**Windows**

|Tipo di dati|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|App aziendali e dati associati installati da Intune|Ai file protetti da EFS verrà revocata la chiave e l'utente non sarà in grado di aprire i file.|Le app aziendali non verranno rimosse.|Vengono disinstallate le app installate inizialmente tramite il portale aziendale e vengono rimossi i dati dell'app aziendale.|Le app vengono disinstallate e le chiavi di trasferimento locale vengono rimosse.|
|Impostazioni|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|Non supportata.|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|Certificati rimossi e revocati.|Non supportata.|Certificati rimossi e revocati.|
|Posta elettronica|Rimuove le applicazioni di posta elettronica abilitate per EFS, tra cui i messaggi e gli allegati dell'applicazione Posta di Windows.|Non supportata.|I profili di posta elettronica di cui viene eseguito il provisioning tramite Intune vengono rimossi e il messaggio di posta elettronica memorizzato nella cache del dispositivo viene eliminato.|Rimuove le applicazioni di posta elettronica abilitate per EFS, tra cui i messaggi e gli allegati dell'applicazione Posta di Windows. Rimuove gli account di posta elettronica di cui Intune ha effettuato il provisioning.|
|Separazione di Azure Active Directory (AAD)|No.|No.|Il record AAD viene rimosso.|Non applicabile. Windows 10 non supporta la cancellazione selettiva per dispositivi appartenenti ad Azure Active Directory.|

## <a name="wipe-encryption-file-system-efs-enabled-content"></a>Cancellare contenuti abilitati per Encryption File System (EFS)
La cancellazione selettiva dei contenuti crittografati con EFS è supportata da Windows 8.1 e Windows RT 8.1. I punti seguenti sono validi per una cancellazione selettiva di contenuti abilitati per EFS:

-   Solo le app e i dati protetti da EFS che usano lo stesso dominio Internet come account di Intune vengono cancellati in modo selettivo. Per altre informazioni, vedere l'argomento relativo alla [cancellazione selettiva di Windows per la gestione dei dati dei dispositivi](http://technet.microsoft.com/library/dn486874.aspx).

-   In caso di modifiche al dominio associato con EFS, potranno essere necessarie fino a 48 ore prima che le app e i dati che usano il nuovo dominio siano cancellati in modo selettivo.

-   Ogni dominio registrato con Intune verrà cancellato.

I dati e le app che sono attualmente supportati dalla cancellazione selettiva EFS sono:

-   App di posta elettronica per Windows

-   Cartelle di lavoro

-   File e cartelle crittografate con EFS. Per altre informazioni, vedere le [procedure consigliate per la crittografia del file system](http://support.microsoft.com/kb/223316).

-   Se gestisce la propria identità in Active Directory, l'organizzazione deve usare lo strumento di sincronizzazione directory (DirSync) per sincronizzare le informazioni in AAD garantendo il corretto funzionamento della cancellazione selettiva EFS.  Per altre informazioni, vedere [Scenario di sincronizzazione della directory](http://technet.microsoft.com/library/dn441212.aspx) nella documentazione di Azure Active Directory.

## <a name="monitor-retire-wipe-and-delete-actions"></a>Monitorare le azioni di disattivazione, cancellazione ed eliminazione
Per ottenere un report dei dispositivi che sono stati ritirati, cancellati o eliminati:

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Report**&gt;**Report cronologia dispositivo**

2.  Specificare una data di inizio e una data di fine per il report, quindi scegliere **Visualizza report**.

Questo report mostra anche chi ha eseguito l'azione.

### <a name="see-also"></a>Vedere anche
[Ritirare i dispositivi](retire-devices-from-microsoft-intune-management.md)

[Cancellazione selettiva di Windows per la gestione di dati del dispositivo](http://technet.microsoft.com/library/dn486874.aspx)
