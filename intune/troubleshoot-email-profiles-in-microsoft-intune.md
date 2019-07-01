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
ms.openlocfilehash: 2246e3f6faa853f620327558a7faf4dc9d6a6e85
ms.sourcegitcommit: 43ba5a05b2e1dc1997126d3574884f65cde449c7
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2019
ms.locfileid: "67197501"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problemi comuni e soluzioni per i profili di posta elettronica in Microsoft Intune

Esaminare alcuni problemi comuni relativi ai profili di posta elettronica e le relative procedure di risoluzione.

## <a name="what-you-need-to-know"></a>Informazioni importanti

- Profili di posta elettronica vengono distribuiti per l'utente che ha registrato il dispositivo. Per configurare il profilo di posta elettronica, Intune Usa le proprietà di Azure Active Directory (AD) nel profilo di posta elettronica dell'utente durante la registrazione. [Aggiungere impostazioni di posta elettronica ai dispositivi](email-settings-configure.md) potrebbe essere un'ottima risorsa.
- Dopo la migrazione dalla soluzione ibrida di Configuration Manager a Intune autonomo, il profilo di posta elettronica dalla soluzione ibrida di Configuration Manager rimane sul dispositivo per 7 giorni. Si tratta di un comportamento previsto. Se è necessario rimosso prima il profilo di posta elettronica, contattare [supporto tecnico di Intune](get-support.md).
- Per Android Enterprise, distribuire Gmail o Nine for Work usando la Store di Play Google gestito. [Aggiungere App Google Play gestito](apps-add-android-for-work.md) Elenca i passaggi.
- Microsoft Outlook per iOS e Android non supporta i profili di posta elettronica. In alternativa, distribuire i criteri di configurazione. Per altre informazioni, vedere [impostazione di configurazione di Outlook](app-configuration-policies-outlook.md).
- Profili di posta elettronica destinati ai gruppi di dispositivi (non i gruppi di utenti) potrebbero non essere recapitati al dispositivo. Quando il dispositivo dispone di un utente primario, quindi destinate a dispositivi dovrebbe funzionare. Se il profilo di posta elettronica sono inclusi i certificati utente, assicurarsi di gruppi di utenti di destinazione.
- Gli utenti possono ripetutamente richiesto di immettere la password per il profilo di posta elettronica. In questo scenario, verificare che tutti i certificati a cui fa riferimento il profilo di posta elettronica. Se uno dei certificati non è destinato a un utente, quindi Ritenta Intune per distribuire il profilo di posta elettronica.

## <a name="device-already-has-an-email-profile-installed"></a>Nel dispositivo è già installato un profilo di posta elettronica

Se gli utenti creano un profilo di posta elettronica prima di registrarsi in Intune o Office 365 MDM, il profilo di posta elettronica distribuito da Intune potrebbe non funzionare come previsto:

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
3. Selezionare il profilo di posta elettronica > **delle proprietà** > **impostazioni**.
4. Impostare il **consentire messaggi di posta elettronica dalle applicazioni di terze parti** se si imposta su **abilitare**.

### <a name="configuration-manager-hybrid"></a>Distribuzione ibrida di Configuration Manager

1. Aprire la console di Configuration Manager > **Asset e conformità**.

2. Espandere **Panoramica** > **Impostazioni di conformità** > **Accesso risorse aziendali** e selezionare **Profili di posta elettronica**.

3. Fare clic con il tasto destro del mouse sul profilo di posta elettronica e aprire **Proprietà**.

4. Nella scheda **Impostazioni di sincronizzazione** selezionare **Consenti di inviare messaggi di posta elettronica da applicazioni di terze parti**.

## <a name="next-steps"></a>Passaggi successivi

Ottenere [supporto da Microsoft](get-support.md) o usare i [forum della community](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
