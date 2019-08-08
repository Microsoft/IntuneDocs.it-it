---
title: Risolvere i problemi delle azioni dei dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Ottenere assistenza per la risoluzione dei problemi di azione del dispositivo.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 159e236a079adcd55ba73e8fea6f786c09d08bbd
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2019
ms.locfileid: "68772360"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Risolvere i problemi relativi alle azioni del dispositivo in Intune

Microsoft Intune dispone di molte azioni che consentono di gestire i dispositivi. Questo articolo fornisce le risposte ad alcune domande comuni che consentono di risolvere i problemi relativi alle azioni del dispositivo.

## <a name="bypass-activation-lock-action"></a>Azione Bypass del blocco attivazione

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>È stato fatto clic sull'azione "Ignora Blocco attivazione" nel portale, ma non si è verificato alcun problema sul dispositivo.
Si tratta di un comportamento previsto. Dopo l'avvio dell'azione bypass Blocco attivazione, a Intune viene richiesto un codice aggiornato da Apple. Il codice verrà immesso manualmente nel campo del codice di accesso quando il dispositivo si trova nella schermata Blocco attivazione. Questo codice è valido solo per 15 giorni, quindi assicurarsi di fare clic sull'azione e copiare il codice prima di eseguire la cancellazione.

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>Perché non viene visualizzato il bypass Blocco attivazione codice nel pannello panoramica hardware del dispositivo iOS?
I motivi più probabili includono:
- Il codice è scaduto ed è stato cancellato dal servizio.
- Il dispositivo non è supervisionato con i criteri di restrizione del dispositivo per consentire Blocco attivazione.

È possibile controllare il codice in Graph Explorer con la query seguente:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>Perché il bypass Blocco attivazione azione in grigio per il dispositivo iOS?
I motivi più probabili includono: 
- Il codice è scaduto ed è stato cancellato dal servizio.
- Il dispositivo non è supervisionato con i criteri di restrizione del dispositivo per consentire Blocco attivazione.

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>Il bypass Blocco attivazione distinzione tra maiuscole e minuscole?
No. E non è necessario immettere i trattini.

## <a name="remove-devices-action"></a>Azione Rimuovi dispositivi

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Ricerca per categorie indicare chi ha avviato un ritiro/cancellazione?
Passare a **dispositivi** > **Intuneazionidispositivo** > **controllare la colonna** **avviato da.**
Se non viene visualizzata alcuna voce, la persona più probabile che abbia avviato l'azione è l'utente del dispositivo. Probabilmente hanno usato l'app Portale aziendale o portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Perché l'applicazione non è stata disinstallata dopo l'uso del ritiro?
Poiché non era considerata un'applicazione gestita. In questo contesto, un'applicazione gestita è un'applicazione installata con il servizio Intune. Sono inclusi:
- L'app è stata distribuita come richiesto
- L'app è stata distribuita come disponibile e quindi installata dall'utente finale dall'app Portale aziendale.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Perché la cancellazione è disabilitata per i dispositivi di profilo di lavoro Android Enterprise?
Si tratta di un comportamento previsto. Google non consente la reimpostazione delle impostazioni predefinite dei dispositivi del profilo di lavoro dal provider MDM.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Perché è possibile accedere nuovamente alle app di Office dopo il ritiro del dispositivo?
Poiché il ritiro di un dispositivo non revoca i token di accesso. È possibile usare i criteri di accesso condizionale per attenuare questa condizione.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Come è possibile monitorare un'azione di ritiro/cancellazione dopo l'emissione?
Passare a **dispositivi** > **Intuneazioni** > **dispositivo**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Perché le cancellazioni vengono talvolta visualizzate come in sospeso per un periodo illimitato?
I dispositivi non sempre segnalano il proprio stato al servizio Intune prima dell'avvio della reimpostazione. Quindi, l'azione viene visualizzata come in sospeso. Se è stata confermata l'azione riuscita, eliminare il dispositivo dal servizio.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Cosa accade se si avvia un ritiro/cancellazione su un dispositivo offline o un dispositivo che non ha comunicato con il servizio in un periodo di tempo?
Il dispositivo rimarrà in stato di **ritiro/cancellazione in sospeso** fino alla scadenza del certificato MDM. Il certificato MDM dura per un anno dalla registrazione e rinnova automaticamente ogni anno. Se il dispositivo archivia prima della scadenza del certificato MDM, verrà ritirato/cancellato. Se il dispositivo non archivia prima della scadenza del certificato MDM, non sarà in grado di archiviare il servizio. 180 giorni dopo la scadenza del certificato MDM, il dispositivo verrà rimosso automaticamente dal portale di Azure.


## <a name="reset-passcode-action"></a>Reimposta azione di codice

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Perché l'azione Reimposta il codice di ripristino è disattivata nel dispositivo di amministrazione del dispositivo Android registrato?
Per combattere il riscatto, Google ha rimosso la funzionalità di reimpostazione del codice nell'API di amministrazione del dispositivo (si applica a dispositivi Android versione 7,0 o successiva).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Perché viene ricevuto un messaggio "non supportato" quando si rilascia una reimpostazione del codice a un dispositivo registrato Android 8,0 o versione successiva?
Poiché il token di reimpostazione non è stato attivato nel dispositivo. Per attivare il token di reimpostazione:
1. È necessario disporre di un codice di accesso del profilo di lavoro nei criteri di configurazione.
2. L'utente finale deve impostare un codice di accesso del profilo di lavoro appropriato.
3. Per consentire la reimpostazione del codice, l'utente finale deve accettare la richiesta secondaria.
Una volta completati questi passaggi, non è più necessario ricevere questa risposta.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>Perché viene richiesto di impostare un nuovo codice di accesso nel dispositivo iOS quando si rilascia l'azione Rimuovi codice?
Poiché uno dei criteri di conformità richiede un codice di accesso.

## <a name="next-steps"></a>Passaggi successivi

Ottenere [supporto da Microsoft](get-support.md) o usare i [forum della community](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
