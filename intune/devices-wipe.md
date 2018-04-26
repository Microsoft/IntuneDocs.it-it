---
title: Rimuovere i dati aziendali nei dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: È possibile rimuovere i dati aziendali in un dispositivo o eseguire un ripristino delle impostazioni di fabbrica in un dispositivo Android, Android for Work, iOS, macOS o Windows usando Microsoft Intune. È anche possibile eliminare un dispositivo da Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 228198276643f1eb8dfcb0392e4902a7f56875c9
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Rimuovere i dispositivi con il ripristino delle impostazioni predefinite o rimuovere i dati aziendali

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile rimuovere da Intune i dispositivi non più necessari, da reimpiegare o mancanti. Questa operazione può essere eseguita usando l'azione **Rimuovi i dati aziendali** o **Ripristino delle impostazioni di fabbrica**. Gli utenti possono anche inviare un comando remoto dall'app Portale aziendale Intune ai dispositivi privati registrati in Intune.

> [!NOTE]
> Prima di rimuovere un utente da Azure Active Directory (Azure AD) usare l'azione **Ripristino delle impostazioni di fabbrica** o **Rimuovi i dati aziendali** per tutti i dispositivi associati all'utente. Se si rimuovono utenti con dispositivi gestiti da Azure AD, Intune non è più in grado di generare un comando di ripristino delle impostazioni di fabbrica o di rimozione dei dati aziendali per tali dispositivi.

## <a name="factory-reset"></a>Ripristino delle impostazioni di fabbrica

L'azione **Ripristino delle impostazioni di fabbrica** riporta un dispositivo alle impostazioni predefinite di fabbrica. Un ripristino delle impostazioni di fabbrica consente di ripristinare tutti i dati e le impostazioni aziendali e dell'utente. Il dispositivo viene rimosso dalla gestione di Intune. Il ripristino delle impostazioni di fabbrica è utile per reimpostare un dispositivo prima di assegnarlo a un nuovo utente o nel caso in cui il dispositivo sia stato smarrito o rubato. Prestare attenzione quando si seleziona **Ripristino delle impostazioni di fabbrica**. Non sarà possibile recuperare i dati nel dispositivo.

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

L'azione **Rimuovi i dati aziendali** consente di rimuovere i dati delle app (se applicabile), le impostazioni e i profili di posta elettronica assegnati usando Intune. **Rimuovi i dati aziendali** lascia i dati personali dell'utente nel dispositivo. Il dispositivo viene rimosso dalla gestione di Intune. 

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

### <a name="android-for-work"></a>Android for Work

La rimozione dei dati aziendali da un dispositivo Android for Work consente di rimuovere tutti i dati, le app e le impostazioni nel profilo di lavoro in tale dispositivo. Il dispositivo viene ritirato dalla gestione con Intune. Il ripristino delle impostazioni predefinite non è supportato per Android for Work.


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

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Dispositivi** selezionare **Tutti i dispositivi**.
4. Selezionare il nome del dispositivo da cui verranno rimossi i dati aziendali.
5. Nel riquadro in cui appare il nome del dispositivo selezionare **Rimuovi i dati aziendali**. Selezionare **Sì** per confermare.

Se il dispositivo è acceso e connesso, l'azione **Rimuovi i dati aziendali** si propaga a tutti i tipi di dispositivo in meno di 15 minuti.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminare dispositivi dal portale di Azure Active Directory

A causa di problemi di comunicazione o dispositivi mancanti può essere necessario eliminare dispositivi da Azure AD. È possibile usare l'azione **Elimina** per rimuovere dal portale di Azure i record dei dispositivi che sono sicuramente irraggiungibili e che molto probabilmente non comunicheranno più con Azure. L'azione **Elimina** non rimuove un dispositivo dalla gestione.

1.  Accedere ad [Azure Active Directory nel portale di Azure](http://aka.ms/accessaad) usando le proprie credenziali di amministratore. È anche possibile accedere al [portale di Office 365](https://portal.office.com). Nel menu selezionare **Interfacce di amministrazione** > **Azure AD**.
2.  Creare una sottoscrizione di Azure, se non se ne possiede una. Se si ha un account a pagamento, per questa operazione non è necessario usare una carta di credito o effettuare un pagamento. Selezionare il collegamento per la sottoscrizione relativo alla **registrazione gratuita di Azure Active Directory**.
3.  Selezionare **Azure Active Directory** e quindi l'organizzazione.
4.  Selezionare la scheda **Utenti**.
5. Selezionare l'utente associato al dispositivo che si vuole eliminare.
6.  Selezionare **Dispositivi**.
7.  Rimuovere i dispositivi nel modo appropriato. Ad esempio, si possono rimuovere i dispositivi che non sono più in uso o quelli con definizioni non accurate.
