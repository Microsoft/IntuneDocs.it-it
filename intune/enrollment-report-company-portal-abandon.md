---
title: Abbandono delle registrazioni nel portale aziendale in Intune
titlesuffix: Microsoft Intune
description: Informazioni sul report Abbandono del portale aziendale.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: ba1ee5a6811457b8c6e7343de7355261a2fcecdb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236755"
---
# <a name="company-portal-abandonment-report"></a>Report Abbandono del portale aziendale

Questo report indica in quale fase della registrazione nel portale aziendale gli utenti abbandonano il processo di registrazione.

Per visualizzare il report, scegliere **Intune** > **Registrazione del dispositivo** > **Abbandono del Portale aziendale**.

Mediante queste informazioni relative all'abbandono è possibile aggiornare i documenti di onboarding, per assistere gli utenti nel completamento della registrazione. Se ad esempio molti utenti abbandonano il processo quando visualizzano le Condizioni per l'utilizzo, è possibile investigare quest'area e renderla più intuitiva per gli utenti.

## <a name="what-is-abandonment"></a>Che cos'è l'abbandono?

L'abbandono si verifica quando un utente esegue una delle operazioni seguenti:

-   Sceglie in modo esplicito un'azione per interrompere la registrazione
-   Chiude il portale aziendale durante la registrazione
-   Impiega oltre 30 minuti per passare da una sezione della registrazione all'altra

Se un utente sceglie di arrestare e riavviare la registrazione più volte, queste azioni vengono conteggiate come più tentativi e più abbandoni. Se un utente attende 30 minuti tra diverse schermate di registrazione, questa azione viene considerata come più abbandoni.

## <a name="what-does-the-report-show"></a>Che cosa visualizza il report?

I report di registrazione includono i dati per i dispositivi iOS e Android.

I report visualizzano i dati delle ultime due settimane, ma è possibile filtrare il report in modo da visualizzare qualsiasi periodo entro gli ultimi 30 giorni.

È possibile applicare filtri all'intervallo di date, al sistema operativo e alla sezione di registrazione scegliendo **Filtra**.

### <a name="number-and-percentage-tiles"></a>Riquadri Numero e Percentuale

Nella parte superiore del report è possibile visualizzare il numero e la percentuale di report abbandonati rispetto al totale delle registrazioni.

-   Registrazioni avviate: numero di registrazioni avviate.
-   Registrazioni abbandonate: numero di registrazioni avviate ma che non hanno restituito come risultato un dispositivo registrato e conforme.
-   Abandonment rate (Frequenza di abbandono): percentuale di tentativi di registrazione abbandonati (Registrazioni abbandonate/Registrazioni iniziate).

### <a name="line-graph"></a>Grafico a linee

Il grafico a linee visualizza gli abbandoni giornalieri in corrispondenza delle quattro sezioni principali della registrazione:

-   Elenco di controllo per l'installazione
-   Schermate della piattaforma
-   Condizioni per l'utilizzo
-   Conformità/Attivazione

### <a name="user-abandonment-actions"></a>Azioni di abbandono degli utenti

Le tabelle seguenti illustrano l'elenco delle azioni degli che sono considerate come abbandono. Per esempi di schermate di registrazione, guardare i video relativi alla registrazione per [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) e [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Sezione Elenco di controllo per l'installazione

| Nome abbandono | Schermata o flusso | Piattaforma | Azione |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Richiesta di apertura di una pagina nel Portale aziendale | iOS/Android | **Annulla** |
| EnrollmentWrapUp | Schermata Registrazione del dispositivo in corso fino al completamento di **Caricamento delle risorse aziendali** | iOS/Android | Tempo richiesto > 30 minuti |
| DeviceCategory | Selezione di Categoria del dispositivo (se configurata dall'amministratore) fino al clic su **Fine** | iOS/Android | Tempo richiesto > 30 minuti |
| PreEnrollmentWizard | Schermata Set up access (Configurare l'accesso), quando dopo l'avvio della registrazione si torna a questa schermata | iOS/Android| **Rimanda** |
| PreEnrollmentWizard | Schermata Set up access (Configurare l'accesso) fino al clic su **Avanti** nella schermata **Passaggi successivi** | iOS/Android | Tempo richiesto > 30 minuti |

#### <a name="platform-screens-section"></a>Sezione Schermate della piattaforma

| Nome abbandono | Schermata o flusso | Piattaforma | Azione |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Richiesta di visualizzazione di un profilo di configurazione | iOS | **Ignora** |
| iOSProfileLaunch | Schermata Installa profilo | iOS | **Annulla** |
| iOSProfileLaunch | Richiesta per considerare attendibile l'origine del profilo e registrare il dispositivo | iOS | **Annulla** |
| iOSProfileLaunch | Schermata Installa profilo fino all'installazione del profilo | iOS | Tempo richiesto > 30 minuti |
| AndroidPermissions | Schermata di attivazione dell'amministratore del dispositivo | Android | **Annulla** |
| AndroidPermissions | Dalla richiesta di approvazione per effettuare e gestire chiamate telefoniche fino alla selezione di **Attiva** per l'amministratore del dispositivo | Android | Tempo richiesto > 30 minuti |
| KnoxActivation | Attivazione dell'agente KLMS (solo Samsung) | Android| **Annulla** |
| KnoxActivation | Attivazione dell'agente KLMS fino a **Conferma** | Android | Tempo richiesto > 30 minuti|

#### <a name="terms-of-use-section"></a>Sezione Condizioni per l'utilizzo

| Nome abbandono | Schermata o flusso | Piattaforma | Azione |
| ---- |---- |---- |---- |
| TermsofUse | Condizioni per l'utilizzo (se configurate dall'amministratore) | iOS/Android | **Rifiuta tutto** |
| TermsofUse | Condizioni per l'utilizzo fino a **Accetta tutto** | iOS/Android | Tempo richiesto > 30 minuti |

#### <a name="complianceactivation-section"></a>Sezione Conformità/Attivazione

| Nome abbandono | Schermata o flusso | Piattaforma | Azione |
| ---- |---- |---- |---- |
| Conformità | Conformità del dispositivo (se configurata dall'amministratore) appare con un colore diverso dal verde al momento della configurazione dell'accesso dopo la registrazione| iOS/Android | **Rimanda** |
| Conformità | Conformità del dispositivo appare con un colore diverso dal verde fino a quando non viene aggiornata e diventa verde | iOS/Android | Tempo richiesto > 30 minuti |
| Attivazione | Attivazione della registrazione (se configurata dall'amministratore) appare con un colore diverso dal verde al momento della configurazione dell'accesso | iOS/Android | **Rimanda** |
| Conformità | Attivazione del dispositivo appare con un colore diverso dal verde fino a quando non viene aggiornata e diventa verde | iOS/Android | Tempo richiesto > 30 minuti |

## <a name="next-steps"></a>Passaggi successivi

Dopo avere verificato le frequenze di abbandono, è possibile esaminare le [opzioni di registrazione](enrollment-options.md) per valutare se apportare eventuali modifiche per migliorare le percentuali di registrazione.