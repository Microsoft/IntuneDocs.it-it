---
title: Report Registrazioni utente incomplete in Intune
titleSuffix: Microsoft Intune
description: Informazioni sul report Registrazioni utente incomplete.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b7861d26650aaf74ea9c58608c33e72495244575
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414215"
---
# <a name="incomplete-user-enrollments-report"></a>Report Registrazioni utente incomplete

Questo report indica in quale fase del processo di registrazione nel portale aziendale gli utenti non completano il processo di registrazione.

Per visualizzare il report, scegliere **Intune** > **Registrazione del dispositivo** > **Registrazioni utente incomplete**.

Usando queste informazioni, è possibile aggiornare i documenti di onboarding per aiutare gli utenti a completare la registrazione. Se ad esempio molti utenti abbandonano il processo quando visualizzano le Condizioni per l'utilizzo, è possibile investigare quest'area e renderla più intuitiva per gli utenti.

## <a name="what-is-an-incomplete-enrollment"></a>Cos'è una registrazione incompleta?

Una registrazione incompleta si verifica quando un utente esegue una delle operazioni seguenti:

- Sceglie in modo esplicito un'azione per interrompere la registrazione
- Chiude il portale aziendale durante la registrazione
- Impiega oltre 30 minuti per passare da una sezione della registrazione all'altra

Se un utente sceglie di arrestare e riavviare la registrazione più volte, queste azioni vengono conteggiate come più tentativi e più registrazioni incomplete. Se un utente attende 30 minuti tra schermate di registrazione diverse, questa azione viene considerata come più registrazioni incomplete.

## <a name="what-does-the-report-show"></a>Che cosa visualizza il report?

Il report include i dati per i dispositivi iOS/iPadOS e Android.

I report visualizzano i dati delle ultime due settimane, ma è possibile filtrare il report in modo da visualizzare qualsiasi periodo entro gli ultimi 30 giorni.

È possibile applicare filtri all'intervallo di date, al sistema operativo e alla sezione di registrazione scegliendo **Filtra**.

### <a name="number-and-percentage-tiles"></a>Riquadri Numero e Percentuale

Nella parte superiore del report è possibile vedere il numero e la percentuale di registrazioni incomplete rispetto al totale delle registrazioni.

- Registrazioni avviate: numero di tentativi di registrazione.
- Registrazioni incomplete: numero di tentativi di registrazione che non hanno restituito come risultato un dispositivo registrato e conforme.
- Incomplete rate (Percentuale registrazioni incomplete): percentuale di tentativi di registrazione abbandonati (Registrazioni abbandonate/Registrazioni avviate).

### <a name="line-graph"></a>Grafico a linee

Il grafico a linee visualizza le registrazioni incomplete giornaliere per ognuna delle quattro sezioni principali della registrazione:

- Elenco di controllo per l'installazione
- Schermate della piattaforma
- Condizioni per l'utilizzo
- Conformità/Attivazione

### <a name="user-abandonment-actions"></a>Azioni di abbandono degli utenti

Le tabelle seguenti illustrano l'elenco delle azioni utente che vengono considerate come registrazione incompleta. Per esempi di schermate di registrazione, guardare i video relativi alla registrazione per [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) e [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Sezione Elenco di controllo per l'installazione

| Nome azione | Schermata o flusso | Piattaforma | Action |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Richiesta di apertura di una pagina nel Portale aziendale | iOS/Android | **Annulla** |
| EnrollmentWrapUp | Schermata Registrazione del dispositivo in corso fino al completamento di **Caricamento delle risorse aziendali** | iOS/Android | Tempo richiesto > 30 minuti |
| DeviceCategory | Selezione di Categoria del dispositivo (se configurata dall'amministratore) fino al clic su **Fine** | iOS/Android | Tempo richiesto > 30 minuti |
| PreEnrollmentWizard | Schermata Set up access (Configurare l'accesso), quando dopo l'avvio della registrazione si torna a questa schermata | iOS/Android| **Rimanda** |
| PreEnrollmentWizard | Schermata Set up access (Configurare l'accesso) fino al clic su **Avanti** nella schermata **Passaggi successivi** | iOS/Android | Tempo richiesto > 30 minuti |

#### <a name="platform-screens-section"></a>Sezione Schermate della piattaforma

| Nome azione | Schermata o flusso | Piattaforma | Action |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Richiesta di visualizzazione di un profilo di configurazione | iOS/iPadOS | **Ignora** |
| iOSProfileLaunch | Schermata Installa profilo | iOS/iPadOS | **Annulla** |
| iOSProfileLaunch | Richiesta per considerare attendibile l'origine del profilo e registrare il dispositivo | iOS/iPadOS | **Annulla** |
| iOSProfileLaunch | Schermata Installa profilo fino all'installazione del profilo | iOS/iPadOS | Tempo richiesto > 30 minuti |
| AndroidPermissions | Schermata di attivazione dell'amministratore del dispositivo | Android | **Annulla** |
| AndroidPermissions | Dalla richiesta di approvazione per effettuare e gestire chiamate telefoniche fino alla selezione di **Attiva** per l'amministratore del dispositivo | Android | Tempo richiesto > 30 minuti |
| KnoxActivation | Attivazione dell'agente KLMS (solo Samsung) | Android| **Annulla** |
| KnoxActivation | Attivazione dell'agente KLMS fino a **Conferma** | Android | Tempo richiesto > 30 minuti|

#### <a name="terms-of-use-section"></a>Sezione Condizioni per l'utilizzo

| Nome azione | Schermata o flusso | Piattaforma | Action |
| ---- |---- |---- |---- |
| TermsofUse | Condizioni per l'utilizzo (se configurate dall'amministratore) | iOS/Android | **Rifiuta tutto** |
| TermsofUse | Condizioni per l'utilizzo fino a **Accetta tutto** | iOS/Android | Tempo richiesto > 30 minuti |

#### <a name="complianceactivation-section"></a>Sezione Conformità/Attivazione

| Nome azione | Schermata o flusso | Piattaforma | Action |
| ---- |---- |---- |---- |
| Conformità | Conformità del dispositivo (se configurata dall'amministratore) appare con un colore diverso dal verde al momento della configurazione dell'accesso dopo la registrazione| iOS/Android | **Rimanda** |
| Conformità | Conformità del dispositivo appare con un colore diverso dal verde fino a quando non viene aggiornata e diventa verde | iOS/Android | Tempo richiesto > 30 minuti |
| Attivazione | Attivazione della registrazione (se configurata dall'amministratore) appare con un colore diverso dal verde al momento della configurazione dell'accesso | iOS/Android | **Rimanda** |
| Conformità | Attivazione del dispositivo appare con un colore diverso dal verde fino a quando non viene aggiornata e diventa verde | iOS/Android | Tempo richiesto > 30 minuti |

## <a name="next-steps"></a>Passaggi successivi

Dopo aver verificato le percentuali di registrazioni incomplete, è possibile esaminare le [opzioni di registrazione](enrollment-options.md) per valutare se apportare modifiche per migliorare la registrazione.
