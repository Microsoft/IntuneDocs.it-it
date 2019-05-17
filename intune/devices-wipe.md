---
title: Disattivare o cancellare i dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Disattivare o cancellare un dispositivo in un dispositivo Android, profilo di lavoro Android, dispositivo iOS, macOS o Windows usando Microsoft Intune. È anche possibile eliminare un dispositivo da Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 896008594e17c3773831edede263c8c47cde3c48
ms.sourcegitcommit: 601327125ac8ae912d8159422de8aac7dbdc25f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570546"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>Rimuovere i dispositivi con la cancellazione, la disattivazione o l'annullamento manuale della registrazione

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usando le azioni **Disattiva** o **Cancella**, è possibile rimuovere da Intune i dispositivi non più necessari, da reimpiegare o mancanti. Gli utenti possono anche inviare un comando remoto dall'app Portale aziendale Intune ai dispositivi registrati in Intune.

> [!NOTE]
> Prima di rimuovere un utente da Azure Active Directory (Azure AD) usare l'azione **Cancella** o **Disattiva** per tutti i dispositivi associati all'utente. Se si rimuovono utenti con dispositivi gestiti da Azure AD, Intune non potrà più disattivare o cancellare tali dispositivi.

## <a name="wipe"></a>Cancellazione

L'azione **Cancella** riporta un dispositivo alle impostazioni predefinite di fabbrica. I dati degli utenti vengono mantenuti se si seleziona la casella di controllo **Mantieni lo stato della registrazione e l'account utente**. In caso contrario, l'unità viene cancellata in modo sicuro.

|Azione di cancellazione|**Mantieni lo stato della registrazione e l'account utente**|Rimosso dalla gestione di Intune|Descrizione|
|:-------------:|:------------:|:------------:|------------|
|**Cancellazione**| Non selezionata | Sì | Cancella tutti gli account utente, i dati, i criteri MDM e le impostazioni. Reimposta le impostazioni e lo stato predefiniti del sistema operativo.|
|**Cancellazione**| Selezionata | No | Cancella tutti i criteri MDM. Conserva gli account utente e i dati. Reimposta le impostazioni utente predefinite. Reimposta le impostazioni e lo stato predefiniti del sistema operativo.|

L'opzione **Mantieni lo stato della registrazione e l'account utente** è disponibile solo per Windows 10 versione 1709 o successiva.

I criteri MDM verranno riapplicati alla successiva connessione del dispositivo a Intune.

La cancellazione è utile per reimpostare un dispositivo prima di assegnarlo a un nuovo utente o nel caso in cui il dispositivo sia stato smarrito o rubato. Scegliere l'azione **Cancella** con cautela. Non sarà possibile recuperare i dati nel dispositivo.

### <a name="wiping-a-device"></a>Cancellazione di un dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** > **Tutti i dispositivi**.
4. Selezionare il nome del dispositivo di cui si vuole eseguire la cancellazione.
5. Nel riquadro in cui appare il nome del dispositivo selezionare **Cancella**.
6. Per Windows 10 versione 1709 o successiva è inoltre disponibile l'opzione **Mantieni lo stato della registrazione e l'account utente**. 
    
    |Mantenuti durante una cancellazione |Non mantenuti|
    | -------------|------------|
    |Account utente associati al dispositivo|File dell'utente|
    |Stato del computer \(aggiunto a un dominio, aggiunto ad AD)| App installate dall'utente \(app dello Store e Win32)|
    |Registrazione del software MDM|Impostazioni del dispositivo non predefinite|
    |App installate da OEM \(app dello Store e Win32)||
    |Profilo utente||
    |Dati utente esterni al profilo utente||
    |Accesso automatico dell'utente|| 
    
         
7. Per confermare la cancellazione, selezionare **Sì**.

Se il dispositivo è acceso e connesso, l'azione **Cancella** si propaga a tutti i tipi di dispositivo in meno di 15 minuti.

## <a name="retire"></a>Ritiro

L'azione **Disattiva** consente di rimuovere i dati delle app gestite, se presenti, le impostazioni e i profili di posta elettronica assegnati usando Intune. Il dispositivo viene rimosso dalla gestione di Intune. Questa operazione viene eseguita solo dopo che il dispositivo si è collegato e ha ricevuto l'azione **Disattiva** remota.

**Disattiva** lascia i dati personali dell'utente nel dispositivo.  

Le tabelle seguenti descrivono i dati che vengono rimossi e l'effetto dell'azione **Disattiva** sui dati che rimangono nel dispositivo dopo la rimozione dei dati aziendali.

### <a name="ios"></a>iOS

|Tipo di dati|iOS|
|-------------|-------|
|App aziendali e dati associati installati da Intune|**App installate tramite il Portale aziendale:** Per le app aggiunte al profilo di gestione, vengono rimossi tutti i dati, oltre alle app stesse. Queste app includono le app inizialmente installate dall'App Store e successivamente gestite come app aziendali. <br /><br /> **App Microsoft che usano Gestione delle app mobili e sono state installate dall'App Store:** Per le app non gestite dal Portale aziendale, vengono rimossi i dati delle app aziendali protette da crittografia MAM (Mobile Application Management, gestione di applicazioni mobili) all'interno delle risorse di archiviazione locale delle app. I dati protetti da crittografia MAM all'esterno dell'app restano crittografati e inutilizzabili, ma non vengono rimossi. Le app personali e i relativi dati non vengono rimossi.|
|Impostazioni|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|
|Agente di gestione|Il profilo di gestione viene rimosso.|
|Posta elettronica|I profili di posta elettronica di cui viene eseguito il provisioning con Intune vengono rimossi. I messaggi di posta elettronica memorizzati nella cache del dispositivo vengono eliminati.|
|Separazione di Azure AD|Il record di Azure AD viene rimosso.|

### <a name="android"></a>Android

|Tipo di dati|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Collegamenti Web|Rimosso.|Rimosso.|
|App Google Play non gestite|Le app e i dati rimangono installati. <br /> <br />Vengono rimossi i dati delle app aziendali protette da crittografia MAM (Mobile Application Management, gestione di applicazioni mobili) all'interno delle risorse di archiviazione locale delle app. I dati protetti da crittografia MAM all'esterno dell'app restano crittografati e inutilizzabili, ma non vengono rimossi. |Le app e i dati rimangono installati. <br /> <br />Vengono rimossi i dati delle app aziendali protette da crittografia MAM (Mobile Application Management, gestione di applicazioni mobili) all'interno delle risorse di archiviazione locale delle app. I dati protetti da crittografia MAM all'esterno dell'app restano crittografati e inutilizzabili, ma non vengono rimossi.|
|App line-of-business non gestite|Le app e i dati rimangono installati.|Le app vengono disinstallate e i dati locali delle app vengono rimossi. Non vengono rimossi dati esterni all'app, ad esempio quelli in una scheda SD.|
|App Google Play gestite|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM (Mobile Application Management, Gestione di applicazioni mobili) all'esterno dell'app, ad esempio in una scheda SD, restano crittografati e sono inutilizzabili, ma non vengono rimossi.|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati, ma non vengono rimossi.|
|App line-of-business gestite|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e inutilizzabili, ma non vengono rimossi.|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e inutilizzabili, ma non vengono rimossi.|
|Impostazioni|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|
|Impostazioni del profilo certificato|I certificati vengono revocati, ma non rimossi.|Certificati rimossi e revocati.|
|Agente di gestione|Il privilegio di amministratore del dispositivo viene revocato.|Il privilegio di amministratore del dispositivo viene revocato.|
|Posta elettronica|N/D (i profili di posta elettronica non sono supportati dai dispositivi Android)|I profili di posta elettronica di cui viene eseguito il provisioning con Intune vengono rimossi. I messaggi di posta elettronica memorizzati nella cache del dispositivo vengono eliminati.|
|Separazione di Azure AD|Il record di Azure AD viene rimosso.|Il record di Azure AD viene rimosso.|

### <a name="android-work-profile"></a>Profilo di lavoro Android

La rimozione dei dati aziendali da un dispositivo con profilo di lavoro Android consente di rimuovere tutti i dati, le app e le impostazioni nel profilo di lavoro in tale dispositivo. Il dispositivo viene ritirato dalla gestione con Intune. La cancellazione non è supportata per i profili di lavoro Android.

### <a name="android-enterprise-kiosk-devices"></a>Dispositivi in modalità tutto schermo di Android Enterprise

I dispositivi in modalità tutto schermo possono solo essere cancellati. Non è possibile disattivare i dispositivi Android in modalità tutto schermo.


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

|Tipo di dati|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8.1 e Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|App aziendali e dati associati installati da Intune|Le chiavi vengono revocate per i file protetti da EFS. L'utente non può aprire i file.|Le app aziendali non vengono rimosse.|Vengono disinstallate le app installate inizialmente attraverso il portale aziendale e vengono rimossi i dati dell'app aziendale.|Le app vengono disinstallate Le chiavi di trasferimento locale vengono rimosse.<br>Per Windows 10 versione 1703 (Creators Update) e versioni successive, le app di Office 365 ProPlus non vengono rimosse. Le app Win32 installate dall'estensione di gestione di Intune non verranno disinstallate nei dispositivi di cui è stata annullata la registrazione. Gli amministratori possono sfruttare l'esclusione di assegnazione per non offrire l'app Win32 ai dispositivi BYOD.|
|Impostazioni|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|Le configurazioni impostate dai criteri di Intune non vengono più applicate. Gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|Non supportata.|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|Certificati rimossi e revocati.|Non supportata.|Certificati rimossi e revocati.|
|Posta elettronica|Rimuove i messaggi di posta elettronica abilitati per EFS. Sono inclusi i messaggi e gli allegati di posta elettronica nell'app Mail per Windows.|Non supportata.|I profili di posta elettronica di cui viene eseguito il provisioning con Intune vengono rimossi. I messaggi di posta elettronica memorizzati nella cache del dispositivo vengono eliminati.|Rimuove i messaggi di posta elettronica abilitati per EFS. Sono inclusi i messaggi e gli allegati di posta elettronica nell'app Mail per Windows. Rimuove gli account di posta elettronica di cui Intune ha effettuato il provisioning.|
|Separazione di Azure AD|No.|No.|Il record di Azure AD viene rimosso.|Non applicabile. In Windows 10 non è possibile disattivare i dispositivi aggiunti ad Azure AD.|

### <a name="retire"></a>Ritiro

1. Accedere a [Intune nel portale di Azure](https://aka.ms/intuneportal).
2. Nel riquadro **Dispositivi** selezionare **Tutti i dispositivi**.
3. Selezionare il nome del dispositivo da disattivare.
4. Nel riquadro in cui appare il nome del dispositivo selezionare **Disattiva**. Selezionare **Sì** per confermare.

Se il dispositivo è acceso e connesso, l'azione **Disattiva** si propaga a tutti i tipi di dispositivo in meno di 15 minuti.

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

1.  Accedere ad [Azure Active Directory nel portale di Azure](http://aka.ms/accessaad) usando le proprie credenziali di amministratore. È anche possibile accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com). Nel menu selezionare **Interfacce di amministrazione** > **Azure AD**.
2.  Creare una sottoscrizione di Azure, se non se ne possiede una. Se si ha un account a pagamento, per questa operazione non è necessario usare una carta di credito o effettuare un pagamento. Selezionare il collegamento per la sottoscrizione relativo alla **registrazione gratuita di Azure Active Directory**.
3.  Selezionare **Azure Active Directory** e quindi l'organizzazione.
4.  Selezionare la scheda **Utenti**.
5. Selezionare l'utente associato al dispositivo che si vuole eliminare.
6.  Selezionare **Dispositivi**.
7.  Rimuovere i dispositivi nel modo appropriato. Ad esempio, si possono rimuovere i dispositivi che non sono più in uso o quelli con definizioni non accurate.

## <a name="retire-an-apple-dep-device-from-intune"></a>Ritirare un dispositivo DEP Apple da Intune

Se si vuole rimuovere completamente un dispositivo DEP Apple dalla gestione con Intune, seguire questa procedura:

1. Accedere a [Intune nel portale di Azure](https://aka.ms/intuneportal).
2. Scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo > **Disattiva**.
![Screenshot della disattivazione](./media/devices-wipe/retire.png)
3. Scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP** > scegliere il token > **Dispositivi** > selezionare la casella di controllo corrispondente al dispositivo > **Elimina** > **Sì**.
![Screenshot per l'eliminazione di un dispositivo](./media/devices-wipe/delete-device.png)
4. Visitare il sito Web all'indirizzo [deploy.apple.com](http://deploy.apple.com) e cercare il dispositivo in base al numero di serie.
5. Nel menu **Assigned to** (Assegnato a) scegliere **Unassigned** (Non assegnato).

6. Scegliere **Reassign** (Riassegna).

    ![Schermata per la riassegnazione di un dispositivo Apple](./media/devices-wipe/apple-reassign.png)

## <a name="fresh-start"></a>Fresh Start

Applicabile per i dispositivi Windows 10. Altre informazioni su [Fresh Start](https://docs.microsoft.com/intune/device-fresh-start).

## <a name="next-steps"></a>Passaggi successivi

Se si vuole registrare di nuovo un dispositivo eliminato, vedere [Opzioni di registrazione](enrollment-options.md).

