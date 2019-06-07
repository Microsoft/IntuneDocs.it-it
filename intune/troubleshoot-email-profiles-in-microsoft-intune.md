---
title: Risolvere i problemi dei profili di posta elettronica in Microsoft Intune - Azure | Microsoft Docs
description: Descrizioni dei problemi comuni relativi ai profili di posta elettronica di Microsoft Intune, tra cui i profili duplicati e gli errori nei dispositivi Android Samsung KNOX Standard, e delle relative soluzioni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0fe37deb63457fef869df0f7263970a4e53cb29
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402716"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problemi comuni e soluzioni per i profili di posta elettronica in Microsoft Intune

Esaminare alcuni problemi comuni relativi ai profili di posta elettronica e le relative procedure di risoluzione.

## <a name="device-already-has-an-email-profile-installed"></a>Nel dispositivo è già installato un profilo di posta elettronica

Se un utente crea un profilo di posta elettronica prima di registrarsi in Intune, il profilo di posta elettronica di Intune potrebbe non funzionare nel modo previsto:

- **iOS**: Intune rileva un profilo di posta elettronica esistente duplicato in base all'indirizzo di posta elettronica e al nome host. Il profilo di posta elettronica creato dall'utente blocca la distribuzione del profilo creato da Intune. Si tratta di un problema comune, poiché gli utenti di iOS in genere creano un profilo di posta elettronica e poi eseguono la registrazione. L'app Portale aziendale indica che l'utente non è conforme e potrebbe richiedergli di rimuovere il profilo di posta elettronica.

  L'utente deve rimuovere il proprio profilo di posta elettronica in modo che il profilo di Intune possa essere distribuito. Per evitare questo problema, richiedere agli utenti di registrarsi e consentire a Intune di distribuire il profilo di posta elettronica. Gli utenti possono quindi creare il proprio profilo di posta elettronica.

- **Windows**: Intune rileva un profilo di posta elettronica esistente duplicato in base all'indirizzo di posta elettronica e al nome host. Intune sovrascrive il profilo di posta elettronica esistente creato dall'utente.

- **Samsung KNOX Standard**: Intune identifica un account di posta elettronica duplicato in base all'indirizzo di posta elettronica e lo sovrascrive con il profilo di Intune. Se questo account viene configurato dall'utente, viene sovrascritto nuovamente dal profilo di Intune. Questo potrebbe confondere l'utente di cui viene sovrascritta la configurazione dell'account.

Samsung KNOX non usa il nome host per identificare il profilo. È consigliabile evitare di creare più profili di posta elettronica da distribuire allo stesso indirizzo di posta elettronica in host diversi, perché si sovrascrivono tra loro.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Errore 0x87D1FDE8 per il dispositivo KNOX Standard

**Problema**: dopo la creazione e la distribuzione di un profilo di posta elettronica di Exchange Active Sync per Samsung KNOX Standard per diversi dispositivi Android, l'errore **0x87D1FDE8** o **Correzione non riuscita** viene visualizzato nella scheda Criteri delle proprietà del dispositivo.

Verificare la configurazione del profilo EAS per Samsung KNOX e i criteri di origine. L'opzione di sincronizzazione Samsung Notes non è più supportata e non deve essere selezionata nel profilo. Assicurarsi che i dispositivi abbiano tempo sufficiente per elaborare i criteri, fino a 24 ore.

## <a name="unable-to-send-images-from--email-account"></a>Impossibile inviare immagini dall'account di posta elettronica

Si applica a Intune nel portale di Azure classico.

Gli utenti con account di posta elettronica configurati automaticamente non possono inviare immagini o foto dai propri dispositivi. Questo scenario può verificarsi se l'opzione **Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti** non è abilitata.

### <a name="intune-solution"></a>Soluzione Intune

1. Aprire la console di amministrazione di Microsoft Intune, selezionare il carico di lavoro **Criteri** > **Criteri di configurazione**.

2. Selezionare il profilo di posta elettronica e scegliere **Modifica**.

3. Selezionare **Consenti l'invio di messaggi di posta elettronica da applicazioni di terze parti**.

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integrato con la soluzione Intune

1. Aprire la console di Configuration Manager > **Asset e conformità**.

2. Espandere **Panoramica** > **Impostazioni di conformità** > **Accesso risorse aziendali** e selezionare **Profili di posta elettronica**.

3. Fare clic con il tasto destro del mouse sul profilo di posta elettronica e aprire **Proprietà**.

4. Nella scheda **Impostazioni di sincronizzazione** selezionare **Consenti di inviare messaggi di posta elettronica da applicazioni di terze parti**.

## <a name="next-steps"></a>Passaggi successivi

Ottenere [supporto da Microsoft](get-support.md) o usare i [forum della community](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).