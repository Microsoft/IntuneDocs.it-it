---
title: Risolvere i problemi dei profili di posta elettronica in Microsoft Intune - Azure | Microsoft Docs
description: Problemi relativi ai profili di posta elettronica e procedure di risoluzione.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 480b453aa4f08f8d2a2460e26bfdb5f05466df6e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190099"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Risolvere i problemi relativi ai profili di posta elettronica in Microsoft Intune

Esaminare alcuni problemi comuni relativi ai profili di posta elettronica e le relative procedure di risoluzione.

Se queste informazioni non risultano utili, è anche possibile [richiedere supporto per Microsoft Intune](get-support.md).

## <a name="unable-to-send-images-from--email-account"></a>Impossibile inviare immagini dall'account di posta elettronica
Si applica a Intune nel portale di Azure classico.

Gli utenti con account di posta elettronica configurati automaticamente non riescono a inviare le immagini dai propri dispositivi. Questo scenario può verificarsi se l'opzione **Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti** non è abilitata.

### <a name="intune-solution"></a>Soluzione Intune

1. Aprire la console di amministrazione di Microsoft Intune, selezionare il carico di lavoro **Criteri** > **Criteri di configurazione**.

2. Selezionare il profilo di posta elettronica e scegliere **Modifica**.

3. Selezionare **Consenti l'invio di messaggi di posta elettronica da applicazioni di terze parti**.

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integrato con la soluzione Intune

1. Aprire la console di Configuration Manager > **Asset e conformità**.

2. Espandere **Panoramica** > **Impostazioni di conformità** > **Accesso risorse aziendali** e selezionare **Profili di posta elettronica**.

3. Fare clic con il tasto destro del mouse sul profilo di posta elettronica e aprire **Proprietà**.

4. Nella scheda **Impostazioni di sincronizzazione** selezionare **Consenti di inviare messaggi di posta elettronica da applicazioni di terze parti**.

## <a name="device-already-has-an-email-profile-installed"></a>Nel dispositivo è già installato un profilo di posta elettronica

Se l'utente ha installato un profilo di posta elettronica prima di effettuare il provisioning di un profilo di Intune, il risultato della distribuzione del profilo di posta elettronica di Intune dipende dalla piattaforma del dispositivo:

- **iOS**: Intune rileva un profilo di posta elettronica esistente duplicato in base all'indirizzo di posta elettronica e al nome host. Il profilo di posta elettronica duplicato creato dall'utente blocca la distribuzione di un profilo creato dall'amministratore di Intune. Si tratta di un problema comune, poiché gli utenti di iOS in genere creano un profilo di posta elettronica e poi eseguono la registrazione. Il portale aziendale comunica all'utente che esiste un problema di conformità perché il profilo di posta elettronica è stato configurato manualmente. All'utente viene quindi richiesto di rimuovere il profilo. L'utente deve rimuovere il proprio profilo di posta elettronica in modo da poter distribuire il profilo di Intune. Per evitare questo problema, richiedere agli utenti di registrarsi e di consentire a Intune di distribuire il profilo. Installare quindi il profilo di posta elettronica creato dall'utente.

- **Windows**: Intune rileva un profilo di posta elettronica esistente duplicato in base all'indirizzo di posta elettronica e al nome host. Intune sovrascrive il profilo di posta elettronica esistente creato dall'utente.

- **Samsung KNOX Standard**: Intune identifica un account di posta elettronica duplicato in base all'indirizzo di posta elettronica e lo sovrascrive con il profilo di Intune. Se questo account viene configurato dall'utente, viene sovrascritto nuovamente dal profilo di Intune. Questo potrebbe confondere l'utente di cui viene sovrascritta la configurazione dell'account.

Samsung KNOX non usa il nome host per identificare il profilo. È consigliabile non creare profili di posta elettronica multipli da distribuire allo stesso indirizzo di posta elettronica in host diversi, perché si sovrascrivono tra loro.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Errore 0x87D1FDE8 per il dispositivo KNOX Standard
**Problema**: dopo la creazione e la distribuzione di un profilo di posta elettronica di Exchange Active Sync per Samsung KNOX Standard per vari dispositivi Android, viene restituito l'errore **0x87D1FDE8** o **Correzione non riuscita** nelle proprietà del dispositivo > scheda Criteri.

Verificare la configurazione del profilo EAS per Samsung KNOX e i criteri di origine. L'opzione di sincronizzazione Samsung Notes non è più supportata e non dovrebbe essere selezionata nel profilo. Assicurarsi che i dispositivi abbiano tempo sufficiente per elaborare i criteri, fino a 24 ore.

## <a name="next-steps"></a>Passaggi successivi
Se queste informazioni non risultano utili, è anche possibile [richiedere supporto per Microsoft Intune](get-support.md).