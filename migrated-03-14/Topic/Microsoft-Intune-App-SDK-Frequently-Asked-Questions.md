---
title: Domande frequenti per Microsoft Intune App SDK
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 133d81c4-e550-404a-980e-64f6e843c649
author: Msmbaldwin
---
# Domande frequenti per Microsoft Intune App SDK
Di seguito sono riportate alcune domande frequenti relative a Intune App SDK.

## Si è verificato un problema con la documentazione o con Intune App SDK. Come si inviano i commenti e suggerimenti o come si segnala un problema?

I commenti e i suggerimenti su Intune App SDK possono essere inviati tramite il sito Microsoft Connect, in cui è visualizzata un'opzione che consente di inviare i commenti o di segnalare un problema. Specificare una priorità per i problemi segnalati e il team di Microsoft Intune li risolverà appena possibile.

![Modulo dei commenti e dei suggerimenti relativi alle app](/Image/App-Feedback-Form.png)

## Come vengono gestiti gli aggiornamenti e la compatibilità del sistema operativo in Intune App SDK?

Microsoft continuerà a impegnarsi per garantire il funzionamento delle funzionalità SDK esistenti nella nuova versione del sistema operativo il prima possibile. Inoltre, assicurerà che l'SDK non causi arresti anomali delle applicazioni o altri effetti gravi per l'utente finale a causa delle nuove funzionalità del sistema operativo accessibili agli utenti finali all'interno delle applicazioni esistenti.

Se i fornitori del sistema operativo forniranno tempestivamente le informazioni richieste, Intune offrirà il supporto per le versioni beta del sistema operativo per consentire i test sulle versioni non definitive dell'applicazione. I fornitori di software indipendenti devono segnalare tempestivamente gli eventuali problemi di compatibilità rilevati o i piani di rilascio di versioni dell'applicazione destinate alle versioni di anteprima del sistema operativo.

Le nuove funzionalità aggiunte all'SDK non interromperanno la compatibilità con il sistema operativo esistente senza preavviso e senza l'approvazione da parte di Microsoft. I problemi di compatibilità non intenzionali verranno gestiti come bug.

## In che modo Intune App SDK influisce sull'app per dispositivi mobili?

L'SDK può influire sull'applicazione in tre modi principali.
* **Prestazioni**: i metodi usati per applicare i criteri possono avere effetti sulle prestazioni dell'applicazione. Testare le prestazioni e segnalare eventuali problemi sotto forma di bug, quindi includere i risultati delle prestazioni con e senza criteri per lo scenario specificato.
* **Funzionalità facoltative**: l'SDK supporta le funzionalità facoltative tramite l'area dell'API (ad esempio, save-as). Il supporto di queste funzionalità richiede modifiche all'applicazione.

  > [AZURE.NOTE] La telemetria è una funzionalità di consenso esplicito. iOS MAM SDK registra i dati della telemetria SDK negli eventi di utilizzo **per impostazione predefinita**. Questi dati vengono inviati a Microsoft Intune. Se si sceglie di non inviare i dati della telemetria SDK a Microsoft Intune dall'applicazione, è necessario disabilitare l'acquisizione della telemetria SDK impostando la proprietà `MAMTelemetryDisabled` su "YES" in `IntuneMAMSettings`.
  
* **Imposizione dei criteri**: quando vengono applicati i criteri MAM alle applicazioni SDK, le funzionalità dell'applicazione e l'esperienza dell'utente potrebbero essere modificate. I team delle applicazioni devono collaborare con il team di Intune per testare le applicazioni e comprendere l'impatto di tali modifiche.


<!--HONumber=Apr16_HO4-->


