---
title: Risolvere i problemi dei profili di posta elettronica in Microsoft Intune - Azure | Microsoft Docs
description: Descrizioni dei problemi comuni relativi ai profili di posta elettronica di Microsoft Intune, tra cui i profili duplicati e gli errori nei dispositivi Android Samsung KNOX Standard, e delle relative soluzioni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/17/2019
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
ms.openlocfilehash: ec3a5a5aa4d30dcac0f954057f0cc51ffde6a950
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734297"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problemi comuni e soluzioni per i profili di posta elettronica in Microsoft Intune

Esaminare alcuni problemi comuni relativi ai profili di posta elettronica e le relative procedure di risoluzione.

## <a name="what-you-need-to-know"></a>Informazioni importanti

- I profili di posta elettronica vengono distribuiti per l'utente che ha registrato il dispositivo. Per configurare il profilo di posta elettronica, Intune usa le proprietà Azure Active Directory (AD) nel profilo di posta elettronica dell'utente durante la registrazione. L' [aggiunta delle impostazioni di posta elettronica ai dispositivi](email-settings-configure.md) può essere una risorsa efficace.
- Dopo aver eseguito la migrazione da Configuration Manager ibrido a Intune autonomo, il profilo di posta elettronica da Configuration Manager Hybrid rimane sul dispositivo per 7 giorni. Si tratta di un comportamento previsto. Se è necessario rimuovere prima il profilo di posta elettronica, contattare il [supporto di Intune](../fundamentals/get-support.md).
- Per Android Enterprise, distribuire Gmail o Nine for Work usando il Google Play Store gestito. [Aggiungi app Google Play gestite](../apps/apps-add-android-for-work.md) elenca i passaggi.
- Microsoft Outlook per iOS e Android non supporta i profili di posta elettronica. Distribuire invece un criterio di configurazione delle app. Per altre informazioni, vedere [impostazione di configurazione di Outlook](../apps/app-configuration-policies-outlook.md).
- I profili di posta elettronica assegnati ai gruppi di dispositivi (non gruppi di utenti) non possono essere recapitati al dispositivo. Quando il dispositivo ha un utente primario, la destinazione del dispositivo dovrebbe funzionare. Se il profilo di posta elettronica include certificati utente, assicurarsi di fare riferimento ai gruppi di utenti.
- È possibile che agli utenti venga ripetutamente richiesto di immettere la password per il profilo di posta elettronica. In questo scenario, controllare tutti i certificati a cui viene fatto riferimento nel profilo di posta elettronica. Se uno dei certificati non è destinato a un utente, Intune tenta di distribuire il profilo di posta elettronica.

## <a name="device-already-has-an-email-profile-installed"></a>Nel dispositivo è già installato un profilo di posta elettronica

Se gli utenti creano un profilo di posta elettronica prima della registrazione in Intune o in Office 365 MDM, il profilo di posta elettronica distribuito da Intune potrebbe non funzionare come previsto:

- **iOS**: Intune rileva un profilo di posta elettronica esistente duplicato in base all'indirizzo di posta elettronica e al nome host. Il profilo di posta elettronica creato dall'utente blocca la distribuzione del profilo creato da Intune. Si tratta di un problema comune, poiché gli utenti di iOS in genere creano un profilo di posta elettronica e poi eseguono la registrazione. L'app Portale aziendale indica che l'utente non è conforme e potrebbe richiedergli di rimuovere il profilo di posta elettronica.

  L'utente deve rimuovere il proprio profilo di posta elettronica in modo che il profilo di Intune possa essere distribuito. Per evitare questo problema, richiedere agli utenti di registrarsi e consentire a Intune di distribuire il profilo di posta elettronica. Gli utenti possono quindi creare il proprio profilo di posta elettronica.

- **Windows**: Intune rileva un profilo di posta elettronica esistente duplicato in base all'indirizzo di posta elettronica e al nome host. Intune sovrascrive il profilo di posta elettronica esistente creato dall'utente.

- **Samsung KNOX Standard**: Intune identifica un account di posta elettronica duplicato in base all'indirizzo di posta elettronica e lo sovrascrive con il profilo di Intune. Se questo account viene configurato dall'utente, viene sovrascritto nuovamente dal profilo di Intune. Questo potrebbe confondere l'utente di cui viene sovrascritta la configurazione dell'account.

Samsung KNOX non usa il nome host per identificare il profilo. È consigliabile evitare di creare più profili di posta elettronica da distribuire allo stesso indirizzo di posta elettronica in host diversi, perché si sovrascrivono tra loro.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Errore 0x87D1FDE8 per il dispositivo KNOX Standard

**Problema**: dopo la creazione e la distribuzione di un profilo di posta elettronica di Exchange Active Sync per Samsung KNOX Standard per diversi dispositivi Android, l'errore **0x87D1FDE8** o **Correzione non riuscita** viene visualizzato nella scheda Criteri delle proprietà del dispositivo.

Verificare la configurazione del profilo EAS per Samsung KNOX e i criteri di origine. L'opzione di sincronizzazione Samsung Notes non è più supportata e non deve essere selezionata nel profilo. Assicurarsi che i dispositivi abbiano tempo sufficiente per elaborare i criteri, fino a 24 ore.

## <a name="unable-to-send-images-from--email-account"></a>Impossibile inviare immagini dall'account di posta elettronica

Gli utenti con account di posta elettronica configurati automaticamente non possono inviare immagini o foto dai propri dispositivi. Questo scenario può verificarsi se l'opzione **Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti** non è abilitata.

### <a name="intune-solution"></a>Soluzione Intune

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili**.
3. Selezionare il profilo di posta elettronica >**le** **Proprietà** > .
4. Impostare l'opzione **Consenti l'invio di messaggi di posta elettronica da applicazioni di terze parti** per **abilitare**.

### <a name="configuration-manager-hybrid"></a>Distribuzione ibrida di Configuration Manager

1. Aprire la console di Configuration Manager > **Asset e conformità**.

2. Espandere **Panoramica** > **Impostazioni di conformità** > **Accesso risorse aziendali** e selezionare **Profili di posta elettronica**.

3. Fare clic con il tasto destro del mouse sul profilo di posta elettronica e aprire **Proprietà**.

4. Nella scheda **Impostazioni di sincronizzazione** selezionare **Consenti di inviare messaggi di posta elettronica da applicazioni di terze parti**.

## <a name="next-steps"></a>Passaggi successivi

Ottenere [supporto da Microsoft](../fundamentals/get-support.md) o usare i [forum della community](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
