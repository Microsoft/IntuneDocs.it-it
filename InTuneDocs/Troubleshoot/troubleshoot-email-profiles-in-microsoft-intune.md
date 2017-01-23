---
title: Risolvere i problemi relativi ai profili di posta elettronica | Documentazione Microsoft
description: Problemi relativi ai profili di posta elettronica e procedure di risoluzione.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: 017a7912cb991f00916373acc18f4ab2b97ce8ed


---

# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Risolvere i problemi relativi ai profili di posta elettronica in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Di seguito vengono elencati alcuni problemi relativi ai profili di posta elettronica e le relative procedure di risoluzione.

Se queste informazioni non consentono di risolvere il problema, vedere [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md) per trovare altri modi per ottenere assistenza.


## <a name="unable-to-send-images-from--email-account"></a>Impossibile inviare immagini dall'account di posta elettronica
Gli utenti con account di posta elettronica configurati automaticamente non riescono a inviare le immagini dai propri dispositivi.
Questo errore si verifica quando l'opzione **Consenti l'invio di messaggi di posta elettronica da applicazioni di terze parti** non è abilitata.

### <a name="intune-solution"></a>Soluzione Intune

1.  Aprire la console di amministrazione di Microsoft Intune, selezionare il carico di lavoro **Criterio** &gt; **Criteri di configurazione**.

2.  Selezionare il profilo di posta elettronica e scegliere **Modifica**.

3.  Selezionare **Consenti l'invio di messaggi di posta elettronica da applicazioni di terze parti**.

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integrato con la soluzione Intune

1.  Nella console di Configuration Manager fare clic su &gt;**Asset e conformità**.

2.  Espandere **Panoramica** -&gt; **Impostazioni di conformità** -&gt; **Accesso risorse aziendali** e selezionare **Profili di posta elettronica**.

3.  Fare clic con il tasto destro del mouse sul profilo di posta elettronica e aprire **Proprietà**.

4.  Nella scheda **Impostazioni di sincronizzazione** selezionare **Consenti di inviare messaggi di posta elettronica da applicazioni di terze parti**.


## <a name="device-already-has-an-email-profile-installed"></a>Nel dispositivo è già installato un profilo di posta elettronica

Se l'utente ha installato un profilo di posta elettronica prima di eseguire il provisioning di un profilo con Intune, il risultato della distribuzione del profilo di posta elettronica di Intune dipende dalla piattaforma del dispositivo:

-**iOS**: Intune rileva un profilo di posta elettronica esistente duplicato in base all'indirizzo di posta elettronica e al nome host. Il profilo di posta elettronica duplicato creato dall'utente bloccherà la distribuzione di un profilo creato dall'amministratore di Intune. Si tratta di un problema comune poiché gli utenti di iOS in genere creano un profilo di posta elettronica e poi eseguono la registrazione. Il portale aziendale informerà l'utente che non è conforme perché il profilo di posta elettronica è stato configurato manualmente e richiederà la rimozione del profilo. L'utente deve rimuovere il proprio profilo di posta elettronica per consentire la distribuzione del profilo di Intune. Per evitare il problema, indicare agli utenti di eseguire la registrazione prima di installare un profilo di posta elettronica e di consentire a Intune di distribuirlo.

-**Windows**: Intune rileva un profilo di posta elettronica esistente duplicato in base all'indirizzo di posta elettronica e al nome host. Intune sovrascriverà il profilo di posta elettronica esistente creato dall'utente.

-**Samsung KNOX Standard**: Intune identifica un account di posta elettronica duplicato in base all'indirizzo di posta elettronica e lo sovrascrive con il profilo di Intune. Se l'utente configura questo account, verrà sovrascritto nuovamente dal profilo di Intune. Questa operazione potrebbe confondere l'utente la cui configurazione dell'account viene sovrascritta.

Samsung KNOX non usa il nome host per identificare il profilo, quindi si consiglia di creare più profili di posta elettronica da distribuire nello stesso indirizzo di posta elettronica di host diversi perché questi verranno sovrascritti.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Errore 0x87D1FDE8 per il dispositivo KNOX Standard
**Problema**: dopo la creazione e la distribuzione di un profilo di posta elettronica di Exchange Active Sync per Samsung KNOX Standard per vari dispositivi Android, viene restituito l'errore **0x87D1FDE8** o **correzione non riuscita** nelle proprietà del dispositivo &gt; scheda Criteri.

Verificare la configurazione del profilo EAS per Samsung KNOX e i criteri di origine. L'opzione di sincronizzazione Samsung Notes non è più supportata e non dovrebbe essere selezionata nel profilo. Assicurarsi che i dispositivi abbiano avuto un tempo sufficiente per elaborare i criteri, fino a 24 ore.

## <a name="next-steps"></a>Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Dec16_HO5-->


