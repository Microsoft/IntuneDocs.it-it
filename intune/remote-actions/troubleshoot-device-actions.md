---
title: Risolvere i problemi delle azioni dei dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Ottenere assistenza per la risoluzione dei problemi relativi alle azioni dei dispositivi.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 545f287e8b7ee82e2008f239171b22e01714b8c7
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514745"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Risolvere i problemi delle azioni dei dispositivi in Intune

In Microsoft Intune sono disponibili molte azioni che consentono di gestire i dispositivi. Questo articolo contiene le risposte ad alcune domande comuni per facilitare la risoluzione dei problemi relativi alle azioni dei dispositivi.

## <a name="disable-activation-lock-action"></a>Azione Disabilita il blocco attivazione

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>È stato fatto clic sull'azione "Disabilita il blocco attivazione" nel portale, ma non è accaduto nulla sul dispositivo.
Si tratta di un comportamento previsto. Dopo l'avvio dell'azione Disabilita il blocco attivazione, Apple richiede a Intune un codice aggiornato. Il codice deve essere immesso manualmente nel campo del codice di accesso quando sul dispositivo è attivata la schermata Blocco attivazione. Il codice è valido solo per 15 giorni. È pertanto necessario assicurarsi di fare clic sull'azione e copiare il codice prima di eseguire l'azione di cancellazione dei dati.

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-iosipados-device"></a>Per quale motivo il codice Disabilita il blocco attivazione non viene visualizzato nel pannello di panoramica Hardware del dispositivo iOS/iPadOS?
I motivi più probabili includono:
- Il codice è scaduto ed è stato cancellato dal servizio.
- Il dispositivo non è supervisionato con i criteri di limitazione dei dispositivi in modo da consentire il blocco attivazione.

È possibile controllare il codice in Graph Explorer con la query seguente:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-iosipados-device"></a>Per quale motivo l'azione Disabilita il blocco attivazione è disattivata per il dispositivo iOS/iPadOS?
I motivi più probabili includono: 
- Il codice è scaduto ed è stato cancellato dal servizio.
- Il dispositivo non è supervisionato con i criteri di limitazione dei dispositivi in modo da consentire il blocco attivazione.

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>Nel codice dell'azione Disabilita il blocco attivazione viene fatta distinzione tra maiuscole e minuscole?
No. Non è nemmeno necessario immettere i trattini.

## <a name="remove-devices-action"></a>Azione Rimuovi i dispositivi

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Come si identifica l'utente che ha avviato un'azione di ritiro o cancellazione dei dati?
In [Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), passare ad **Amministrazione del tenant** > **Log di controllo** > controllare la colonna **Avviato da**.
Se non viene visualizzata alcuna voce, la persona che con maggiore probabilità ha avviato l'azione è l'utente del dispositivo. È probabile che abbia usato l'app Portale aziendale oppure il sito portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Per quale motivo l'applicazione non è stata disinstallata dopo l'uso della funzione di ritiro?
Perché non era considerata un'applicazione gestita. In questo contesto, un'applicazione gestita è un'applicazione installata tramite il servizio Intune. Sono inclusi:
- L'app è stata distribuita come Obbligatoria
- L'app è stata distribuita come Disponibile e quindi installata dall'utente finale tramite l'app Portale aziendale.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Per quale motivo la funzione di cancellazione dei dati è disabilitata per i dispositivi con Profilo di lavoro Android Enterprise?
Si tratta di un comportamento previsto. Google non consente il ripristino delle impostazioni predefinite dei dispositivi con Profilo di lavoro dal provider MDM.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Per quale motivo è possibile accedere nuovamente alle app di Office dopo il ritiro del dispositivo?
Perché il ritiro di un dispositivo non ha l'effetto di revocare i token di accesso. Per attenuare questa condizione è possibile usare i criteri di accesso condizionale.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>In che modo è possibile monitorare un'azione di ritiro o cancellazione dei dati dopo che è stata avviata?
In [Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), passare ad **Amministrazione del tenant** > **Log di controllo**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Per quale motivo le azioni di cancellazione dei dati vengono talvolta visualizzate come In sospeso per un periodo illimitato?
I dispositivi non sempre segnalano il proprio stato al servizio Intune prima dell'avvio della reimpostazione. L'azione viene quindi visualizzata come In sospeso. Se si è certi che l'azione è stata eseguita, eliminare il dispositivo dal servizio.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Cosa accade se si avvia un'azione di ritiro o cancellazione dei dati su un dispositivo offline o su un dispositivo che non ha comunicato con il servizio per un certo periodo di tempo?
Lo stato del dispositivo rimarrà **Ritiro/Cancellazione in sospeso** fino alla scadenza del certificato MDM. Il certificato MDM ha validità di un anno dalla registrazione e viene rinnovato automaticamente ogni anno. Se il dispositivo viene sincronizzato prima della scadenza del certificato MDM, l'azione di ritiro o cancellazione dei dati verrà eseguita. Se il dispositivo non viene sincronizzato prima della scadenza del certificato MDM, la sincronizzazione con il servizio non sarà possibile. 180 giorni dopo la scadenza del certificato MDM, il dispositivo verrà rimosso automaticamente dal portale di Azure.


## <a name="reset-passcode-action"></a>Azione Reimposta passcode

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Per quale motivo l'azione Reimposta passcode è disattivata nel dispositivo registrato con Android Device Admin?
Per prevenire il rischio di ransomware, Google ha rimosso la funzionalità di reimpostazione del passcode nell'API Device Admin (applicabile a dispositivi Android versione 7.0 o successiva).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Per quale motivo viene restituito un messaggio "Non supportato" quando si esegue la reimpostazione del passcode su un dispositivo registrato con Profilo di lavoro Android versione 8.0 o successiva?
Perché nel dispositivo non è stato attivato il token di reimpostazione. Per attivare il token di reimpostazione:
1. È necessario disporre di un passcode per Profilo di lavoro nei criteri di configurazione.
2. L'utente finale deve impostare un passcode per Profilo di lavoro appropriato.
3. Per consentire la reimpostazione del passcode, l'utente finale deve accettare la richiesta secondaria.
Una volta completati questi passaggi, il messaggio non dovrebbe essere più visualizzato.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-iosipados-device-when-i-issue-the-remove-passcode-action"></a>Per quale motivo viene chiesto di impostare un nuovo passcode nel dispositivo iOS/iPadOS quando si esegue l'azione Rimuovi il passcode?
Perché uno dei criteri di conformità richiede l'impostazione di un passcode.


## <a name="wipe-action"></a>Azione di cancellazione

### <a name="i-cant-restart-a-windows-10-device-after-using-the-wipe-action"></a>Non è possibile riavviare un dispositivo Windows 10 dopo aver usato l'azione di cancellazione
Questo problema può verificarsi se si usa l'opzione **Cancella i dati del dispositivo e continua a cancellare anche in caso di perdita di alimentazione del dispositivo. Se si seleziona questa opzione, occorre notare che potrebbe impedire il riavvio di alcuni dispositivi Windows 10** in un dispositivo Windows 10.

Questo problema può verificarsi quando l'installazione di Windows presenta un danneggiamento importante che impedisce la reinstallazione del sistema operativo. In tal caso, il processo ha esito negativo e lascia il sistema nell'[Ambiente ripristino Windows]( https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

### <a name="i-cant-restart-a-bitlocker-encrypted-device-after-using-the-wipe-action"></a>Non è possibile riavviare un dispositivo crittografato con BitLocker dopo aver usato l'azione di cancellazione
Questo problema può verificarsi se si usa l'opzione **Cancella i dati del dispositivo e continua a cancellare anche in caso di perdita di alimentazione del dispositivo. Se si seleziona questa opzione, occorre notare che potrebbe impedire il riavvio di alcuni dispositivi Windows 10** in dispositivo crittografato con BitLocker.

Per risolvere questo problema, usare i supporti di avvio per reinstallare Windows 10 nel dispositivo.


## <a name="next-steps"></a>Passaggi successivi

Ottenere [supporto da Microsoft](../fundamentals/get-support.md) o usare i [forum della community](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
