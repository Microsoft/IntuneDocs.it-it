---
title: Rimuovere i dati aziendali nei dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: È possibile rimuovere i dati aziendali in un dispositivo o eseguire un ripristino delle impostazioni di fabbrica in un dispositivo Android, profilo di lavoro Android, iOS, macOS o Windows usando Microsoft Intune. È anche possibile eliminare un dispositivo da Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 41d8f70dd72e845663f39e151c393f5edc0ad394
ms.sourcegitcommit: 391755a4c8a38e3a22744516fd27d75e40438899
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028746"
---
# <a name="remove-devices-by-using-factory-reset-removing-company-data-or-manually-unenrolling-the-device"></a>Rimuovere i dispositivi tramite il ripristino delle impostazioni predefinite, la rimozione dei dati aziendali o l'annullamento manuale della registrazione del dispositivo

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usando le azioni **Rimuovi i dati aziendali** o **Ripristino delle impostazioni predefinite**, è possibile rimuovere da Intune i dispositivi non più necessari, da reimpiegare o mancanti. Gli utenti possono anche inviare un comando remoto dall'app Portale aziendale Intune ai dispositivi privati registrati in Intune.

> [!NOTE]
> Prima di rimuovere un utente da Azure Active Directory (Azure AD) usare l'azione **Ripristino delle impostazioni di fabbrica** o **Rimuovi i dati aziendali** per tutti i dispositivi associati all'utente. Se si rimuovono utenti con dispositivi gestiti da Azure AD, Intune non è più in grado di generare un comando di ripristino delle impostazioni di fabbrica o di rimozione dei dati aziendali per tali dispositivi.

## <a name="factory-reset"></a>Ripristino delle impostazioni di fabbrica

L'azione **Ripristino delle impostazioni di fabbrica** riporta un dispositivo alle impostazioni predefinite di fabbrica. I dati degli utenti vengono mantenuti se si seleziona la casella di controllo **Mantieni lo stato della registrazione e l'account utente**. In caso contrario, l'unità viene cancellata in modo sicuro.

|Azione Ripristino delle impostazioni predefinite|**Mantieni lo stato della registrazione e l'account utente**|Rimosso dalla gestione di Intune|Descrizione|
|:-------------:|:------------:|:------------:|------------|
|**Ripristino impostazioni predefinite**| Non selezionata | Sì | Cancella tutti gli account utente, i dati, i criteri MDM e le impostazioni. Reimposta le impostazioni e lo stato predefiniti del sistema operativo.|
|**Ripristino impostazioni predefinite**| Selezionato | No | Cancella tutti i criteri MDM. Conserva gli account utente e i dati. Reimposta le impostazioni utente predefinite. Reimposta le impostazioni e lo stato predefiniti del sistema operativo.|

L'opzione **Mantieni lo stato della registrazione e l'account utente** è disponibile solo per Windows 10 versione 1709 o successiva.

I criteri MDM verranno riapplicati alla successiva connessione del dispositivo a Intune.

Il ripristino delle impostazioni di fabbrica è utile per reimpostare un dispositivo prima di assegnarlo a un nuovo utente o nel caso in cui il dispositivo sia stato smarrito o rubato. Prestare attenzione quando si seleziona **Ripristino delle impostazioni di fabbrica**. Non sarà possibile recuperare i dati nel dispositivo.

### <a name="factory-reset-a-device"></a>Ripristinare le impostazioni di fabbrica di un dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** > **Tutti i dispositivi**.
4. Selezionare il nome del dispositivo di cui si vuole eseguire il ripristino delle impostazioni di fabbrica.
5. Nel riquadro in cui appare il nome del dispositivo selezionare **Ripristino delle impostazioni di fabbrica**.
6. Per Windows 10 versione 1709 o successiva è inoltre disponibile l'opzione **Mantieni lo stato della registrazione e l'account utente**. 
    
    |Mantenuti durante un ripristino delle impostazioni di fabbrica|Non mantenuti|
    | -------------|------------|
    |Account utente associati al dispositivo|File dell'utente|
    |Stato del computer \(aggiunto a un dominio, aggiunto ad AD)| App installate dall'utente \(app dello Store e Win32)|
    |Registrazione del software MDM|Impostazioni del dispositivo non predefinite|
    |App installate da OEM \(app dello Store e Win32)||
    |Profilo utente||
    |Dati utente esterni al profilo utente||
    |Accesso automatico dell'utente|| 
    
         
7. Selezionare **Sì** per confermare il ripristino delle impostazioni di fabbrica.

Se il dispositivo è acceso e connesso, l'azione **Ripristino delle impostazioni di fabbrica** si propaga a tutti i tipi di dispositivo in meno di 15 minuti.

## <a name="remove-company-data"></a>Rimuovere i dati aziendali

L'azione **Rimuovi i dati aziendali** consente di rimuovere i dati delle app (se applicabile), le impostazioni e i profili di posta elettronica assegnati usando Intune. Il dispositivo viene rimosso dalla gestione di Intune. Questa operazione viene eseguita solo dopo che il dispositivo si è collegato e ha ricevuto l'azione **Rimuovi i dati aziendali** remota.

**Rimuovi i dati aziendali** lascia i dati personali dell'utente nel dispositivo.  

Le tabelle seguenti descrivono i dati che vengono rimossi e l'effetto dell'azione **Rimuovi i dati aziendali** sui dati che rimangono nel dispositivo dopo la rimozione dei dati aziendali.

### <a name="ios"></a>iOS

|Tipo di dati|iOS|
|-------------|-------|
|App aziendali e dati associati installati da Intune|Le app vengono disinstallate e vengono rimossi i dati dell'app aziendale.<br /><br />I dati delle app Microsoft che usano la gestione delle app mobili vengono rimossi. L'app non viene rimossa.|
|Impostazioni|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|
|Agente di gestione|Il profilo di gestione viene rimosso.|
|Posta elettronica|I profili di posta elettronica di cui viene eseguito il provisioning con Intune vengono rimossi. I messaggi di posta elettronica memorizzati nella cache del dispositivo vengono eliminati.|
|Outlook|I messaggi di posta elettronica ricevuti dall'app Microsoft Outlook per iOS vengono rimossi. È necessario che l'app Outlook per dispositivi mobili sia prima distribuita come app obbligatoria per gli utenti iOS.|
|Separazione di Azure AD|Il record di Azure AD viene rimosso.|
|Contatti |I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Eventuali contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere rimossi. <br /> <br />Attualmente è supportata solo l'app Outlook.

### <a name="android"></a>Android

|Tipo di dati|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Collegamenti Web|Rimosso.|Rimosso.|
|App Google Play non gestite|Le app e i dati rimangono installati.|Le app e i dati rimangono installati.|
|App line-of-business non gestite|Le app e i dati rimangono installati.|Le app vengono disinstallate e i dati locali delle app vengono rimossi. Non vengono rimossi dati esterni all'app, ad esempio quelli in una scheda SD.|
|App Google Play gestite|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM (Mobile Application Management, Gestione di applicazioni mobili) all'esterno dell'app, ad esempio in una scheda SD, restano crittografati e sono inutilizzabili, ma non vengono rimossi.|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati, ma non vengono rimossi.|
|App line-of-business gestite|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e inutilizzabili, ma non vengono rimossi.|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e inutilizzabili, ma non vengono rimossi.|
|Impostazioni|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|
|Impostazioni del profilo certificato|I certificati vengono revocati, ma non rimossi.|Certificati rimossi e revocati.|
|Agente di gestione|Il privilegio di amministratore del dispositivo viene revocato.|Il privilegio di amministratore del dispositivo viene revocato.|
|Posta elettronica|N/D (i profili di posta elettronica non sono supportati dai dispositivi Android)|I profili di posta elettronica di cui viene eseguito il provisioning con Intune vengono rimossi. I messaggi di posta elettronica memorizzati nella cache del dispositivo vengono eliminati.|
|Outlook|I messaggi di posta elettronica ricevuti dall'app Outlook per Android vengono rimossi, ma solo se Outlook è protetto dai criteri MAM. In caso contrario, Outlook non viene cancellato quando si annulla la registrazione del dispositivo.|I messaggi di posta elettronica ricevuti dall'app Outlook per Android vengono rimossi, ma solo se Outlook è protetto dai criteri MAM. In caso contrario, Outlook non viene cancellato quando si annulla la registrazione del dispositivo.|
|Separazione di Azure AD|Il record di Azure AD viene rimosso.|Il record di Azure AD viene rimosso.|
|Contatti |I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Eventuali contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere rimossi. <br /> <br />Attualmente è supportata solo l'app Outlook.|I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Eventuali contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere rimossi. <br /> <br />Attualmente è supportata solo l'app Outlook.

### <a name="android-work-profile"></a>Profilo di lavoro Android

La rimozione dei dati aziendali da un dispositivo con profilo di lavoro Android consente di rimuovere tutti i dati, le app e le impostazioni nel profilo di lavoro in tale dispositivo. Il dispositivo viene ritirato dalla gestione con Intune. Il ripristino delle impostazioni predefinite non è supportato per i profili di lavoro Android.

### <a name="android-enterprise-kiosk-devices"></a>Dispositivi in modalità tutto schermo di Android Enterprise

Per i dispositivi in modalità tutto schermo di Android è possibile eseguire solo il ripristino delle impostazioni di fabbrica. Non è possibile rimuovere i dati aziendali dai dispositivi in modalità tutto schermo di Android.


### <a name="macos"></a>macOS

|Tipo di dati|macOS|
|-------------|-------|
|Impostazioni|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|
|Impostazioni del profilo certificato|I certificati distribuiti tramite MDM vengono rimossi e revocati.|
|Agente di gestione|Il profilo di gestione viene rimosso.|
|Outlook|Se l'accesso condizionale è abilitato, il dispositivo non riceve nuovi messaggi.|
|Separazione di Azure AD|Il record di Azure AD viene rimosso.|

### <a name="windows"></a>Windows

|Tipo di dati|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8.1 e Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|App aziendali e dati associati installati da Intune|Le chiavi vengono revocate per i file protetti da EFS. L'utente non può aprire i file.|Le app aziendali non vengono rimosse.|Vengono disinstallate le app installate inizialmente attraverso il portale aziendale e vengono rimossi i dati dell'app aziendale.|Le app vengono disinstallate Le chiavi di trasferimento locale vengono rimosse.<br>Per Windows 10 versione 1703 (Creators Update) e versioni successive, le app di Office 365 ProPlus non vengono rimosse.|
|Impostazioni|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|Non supportata.|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|Certificati rimossi e revocati.|Non supportata.|Certificati rimossi e revocati.|
|Posta elettronica|Rimuove i messaggi di posta elettronica abilitati per EFS. Sono inclusi i messaggi e gli allegati di posta elettronica nell'app Mail per Windows.|Non supportata.|I profili di posta elettronica di cui viene eseguito il provisioning con Intune vengono rimossi. I messaggi di posta elettronica memorizzati nella cache del dispositivo vengono eliminati.|Rimuove i messaggi di posta elettronica abilitati per EFS. Sono inclusi i messaggi e gli allegati di posta elettronica nell'app Mail per Windows. Rimuove gli account di posta elettronica di cui Intune ha effettuato il provisioning.|
|Separazione di Azure AD|No.|No.|Il record di Azure AD viene rimosso.|Non applicabile. In Windows 10 non è possibile rimuovere i dati aziendali per i dispositivi aggiunti ad Azure AD.|

### <a name="remove-company-data"></a>Rimuovere i dati aziendali

1. Accedere a [Intune nel portale di Azure](https://aka.ms/intuneportal).
2. Nel riquadro **Dispositivi** selezionare **Tutti i dispositivi**.
3. Selezionare il nome del dispositivo da cui verranno rimossi i dati aziendali.
4. Nel riquadro in cui appare il nome del dispositivo selezionare **Rimuovi i dati aziendali**. Selezionare **Sì** per confermare.

Se il dispositivo è acceso e connesso, l'azione **Rimuovi i dati aziendali** si propaga a tutti i tipi di dispositivo in meno di 15 minuti.

## <a name="delete-devices-from-the-intune-portal"></a>Eliminare i dispositivi dal portale di Intune

Per rimuovere i dispositivi dal portale di Intune, è possibile eliminarli dal riquadro del dispositivo specifico. Alla successivo collegamento del dispositivo, tutti i dati aziendali verranno rimossi.

1. Accedere a [Intune nel portale di Azure](https://aka.ms/intuneportal).
2. Scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere i dispositivi che si vuole eliminare > **Elimina**.

### <a name="automatically-delete-devices-with-cleanup-rules"></a>Eliminare automaticamente i dispositivi con le regole di pulizia
È possibile configurare Intune per eliminare automaticamente i dispositivi che sembrano essere inattivi, non aggiornati o non rispondere. Queste regole di pulizia monitorano continuamente l'inventario dei dispositivi in modo che i record di dispositivo rimangano aggiornati. I dispositivi eliminati in questo modo vengono rimossi dalla gestione di Intune.
1. Accedere a [Intune nel portale di Azure](https://aka.ms/intuneportal).
2. Scegliere **Dispositivi** > **Regole di pulizia del dispositivo** > **Sì**.
3. Nella casella **Elimina i dispositivi non archiviati per il numero di giorni specificato** immettere un numero compreso tra 90 e 270.
4. Scegliere **Salva**.



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminare dispositivi dal portale di Azure Active Directory

A causa di problemi di comunicazione o dispositivi mancanti può essere necessario eliminare dispositivi da Azure AD. È possibile usare l'azione **Elimina** per rimuovere dal portale di Azure i record dei dispositivi che sono sicuramente irraggiungibili e che molto probabilmente non comunicheranno più con Azure. L'azione **Elimina** non rimuove un dispositivo dalla gestione.

1.  Accedere ad [Azure Active Directory nel portale di Azure](http://aka.ms/accessaad) usando le proprie credenziali di amministratore. È anche possibile accedere al [portale di Office 365](https://portal.office.com). Nel menu selezionare **Interfacce di amministrazione** > **Azure AD**.
2.  Creare una sottoscrizione di Azure, se non se ne possiede una. Se si ha un account a pagamento, per questa operazione non è necessario usare una carta di credito o effettuare un pagamento. Selezionare il collegamento per la sottoscrizione relativo alla **registrazione gratuita di Azure Active Directory**.
3.  Selezionare **Azure Active Directory** e quindi l'organizzazione.
4.  Selezionare la scheda **Utenti**.
5. Selezionare l'utente associato al dispositivo che si vuole eliminare.
6.  Selezionare **Dispositivi**.
7.  Rimuovere i dispositivi nel modo appropriato. Ad esempio, si possono rimuovere i dispositivi che non sono più in uso o quelli con definizioni non accurate.

## <a name="retire-an-apple-dep-device-from-intune"></a>Ritirare un dispositivo DEP Apple da Intune

Se si vuole rimuovere completamente un dispositivo DEP Apple dalla gestione con Intune, seguire questa procedura:

1. Accedere a [Intune nel portale di Azure](https://aka.ms/intuneportal).
2. Scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo > **Rimuovi i dati aziendali**.
![Screenshot di Rimuovi i dati aziendali](./media/devices-wipe/remove-company-data.png)
3. Scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP** > scegliere il token > **Dispositivi** > selezionare la casella di controllo corrispondente al dispositivo > **Elimina** > **Sì**.
![Screenshot per l'eliminazione di un dispositivo](./media/devices-wipe/delete-device.png)
4. Visitare il sito Web all'indirizzo [deploy.apple.com](http://deploy.apple.com) e cercare il dispositivo in base al numero di serie.
5. Nel menu **Assigned to** (Assegnato a) scegliere **Unassigned** (Non assegnato).

6. Scegliere **Reassign** (Riassegna).

    ![Schermata per la riassegnazione di un dispositivo Apple](./media/devices-wipe/apple-reassign.png)

## <a name="next-steps"></a>Passaggi successivi

Se si vuole registrare di nuovo un dispositivo eliminato, vedere [Opzioni di registrazione](enrollment-options.md).

