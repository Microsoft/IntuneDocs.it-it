---
title: L'ottimizzazione alimentazione impedisce l'accesso alla posta elettronica | Microsoft Docs
description: Informazioni su come disattivare l'ottimizzazione alimentazione per Android per assicurarsi di ricevere la posta elettronica.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 663da92e11befeae1f65467e887870a52640cbeb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020572"
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Outlook non sincronizza la posta elettronica gestita quando è attivata l'ottimizzazione della batteria per Android

> [!IMPORTANT]
> Questo problema è documentato qui perché sono state ricevute numerose segnalazioni dei clienti a questo proposito. Se il problema continua a verificarsi dopo avere eseguito questi passaggi, contattare il [supporto tecnico dell'azienda](https://portal.manage.microsoft.com#HelpDeskDialog) per ulteriore assistenza.

La registrazione del dispositivo in Intune consente di ottenere l'accesso alle risorse aziendali. Una delle risorse più comuni è l'accesso alla posta elettronica. È stato rilevato un problema di accesso alla posta elettronica tramite Outlook per i dispositivi Android quando è attivata l'ottimizzazione della batteria. L'ottimizzazione della batteria può essere attivata automaticamente per tentare di mantenere acceso il dispositivo quanto più a lungo possibile. A tale scopo, l'ottimizzazione della batteria tenta di interrompere i download automatici della posta elettronica.

Il team di Microsoft Intune sta lavorando attivamente per trovare una soluzione per questo problema. Un modo per evitare che il dispositivo entri in modalità a basso consumo energetico è assicurarsi che la batteria mantenga un livello di carica superiore al 30%. Per evitare che si verifichi il problema quando viene attivata la modalità a basso consumo energetico, è necessario rimuovere il portale aziendale e Outlook dall'elenco delle app interessate dalle impostazioni di risparmio energetico e di ottimizzazione della batteria.

Esistono molti dispositivi Android realizzati da numerosi produttori. Non è possibile documentare la procedura esatta da eseguire per ogni dispositivo. Potrebbe essere necessario eseguire questa operazione solo nelle impostazioni di sistema o anche in alcune impostazioni specifiche del produttore. Sono disponibili alcuni esempi comuni delle procedure per la risoluzione del problema nei dispositivi Android.

## <a name="unmodified-android-devices"></a>Dispositivi Android non modificati

Numerosi produttori aggiungono modifiche ai propri dispositivi Android. Questo può cambiare alcune modalità di interazione con il dispositivo, ad esempio i temi e le notifiche. Google in genere non apporta modifiche di questo tipo ai propri telefoni. Ad esempio, in un dispositivo di Google Pixel con Android 7.0 o versione successiva, è necessario eseguire i seguenti passaggi per rimuovere queste app dall'ottimizzazione della batteria:

1. Aprire **Impostazioni**.
2. Toccare **Battery** (Batteria)  > **More** (Altro)  > **Battery optimization** (Ottimizzazione batteria).
3. Toccare la freccia verso il basso, quindi **Not optimized** (Non ottimizzato).
4. Selezionare le app Portale aziendale e Outlook, quindi disattivare l'ottimizzazione della batteria.

## <a name="samsung-devices"></a>Dispositivi Samsung

Per altri tipi di dispositivi Android, ad esempio i dispositivi Samsung con Android 7.0 o versione successiva, è necessario eseguire una procedura diversa per rimuovere le app Portale aziendale e Outlook dall'ottimizzazione della batteria.

1. Aprire **Impostazioni**.
2. Toccare **Menu (...)**   >  **Special access** (Accesso speciale)  > **Optimize battery usage** (Ottimizza l'utilizzo della batteria).
3. Selezionare **All apps** (Tutte le app) nell'elenco a discesa.
4. **Disattivare** l'interruttore accanto alle app Portale aziendale e Outlook per disattivare l'ottimizzazione della batteria.

Inoltre, se si usa un dispositivo Samsung con una versione precedente di Android, è necessario eseguire la seguente procedura per rimuovere queste app dalla modalità risparmio energia.

1. Aprire **Impostazioni**.
2. Toccare **Device maintenance** (Manutenzione dispositivo)  > **Battery** (Batteria)  > **Unmonitored apps** (App non monitorate).
3. Toccare **Add apps**  (Aggiungi app).
4. Selezionare le app Portale aziendale e Outlook, quindi toccare **Done** (Fine).

## <a name="oneplus-devices"></a>Dispositivi OnePlus

È anche possibile individuare queste impostazioni tramite una ricerca nelle impostazioni di sistema. Ad esempio, in un dispositivo OnePlus 3 con Android 7.1.1, è necessario eseguire la seguente procedura: 

1. Aprire **System Settings** (Impostazioni di sistema). 
2. Toccare il pulsante **Search** (Cerca). Questo pulsante, simile a una lente di ingrandimento, è disponibile nella parte superiore destra dello schermo. 
3. Digitare **battery optimization** (ottimizzazione batteria) nella casella di ricerca, quindi selezionare l'opzione **Battery Optimization** (Ottimizzazione batteria) nella schermata **Settings** (Impostazioni) visualizzata. 
4. Toccare **Battery** (Batteria)  > **Battery optimization** (Ottimizzazione batteria).
5. Selezionare le app Portale aziendale e Outlook, quindi selezionare **Don't optimize** (Non ottimizzare). Toccare **Fine**.

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
