---
title: "Impostazioni dei criteri di conformità per i dispositivi Android | Microsoft Intune"
description: "Questo argomento descrive le impostazioni dei criteri di conformità per i dispositivi Android."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: af4c84d0e317f5903d22cdfead9ce0ab4fbddc8f
ms.openlocfilehash: ed8f280de4582863f77e5b0e9cb5dfb2f20159c4


---


# Impostazioni dei criteri di conformità per i dispositivi Android in Microsoft Intune

Le impostazioni dei criteri descritte in questo argomento si applicano ai dispositivi che eseguono Android 4.0 e versioni successive oppure Samsung KNOX 4.0 e versioni successive.

Per informazioni su altre piattaforme, selezionare una delle voci seguenti:
> [!div class="op_single_selector"]
- [Impostazioni dei criteri di conformità per i dispositivi iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Impostazioni dei criteri di conformità per i dispositivi Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Impostazioni di sicurezza del sistema
### Password
- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per richiedere agli utenti di immettere una password per poter accedere al dispositivo.

-  **Lunghezza minima password**: specificare il numero minimo di cifre o caratteri che la password dell'utente deve contenere.

- **Qualità password:** questa impostazione rileva se i requisiti di password specificati sono configurati nel dispositivo. Abilitare questa impostazione per richiedere agli utenti la configurazione di determinati requisiti di password per i dispositivi Android. È possibile scegliere tra:
  -   **Protezione biometrica bassa**
  - **Richiesto**
  -   **Almeno numerico**
  -   **Almeno alfabetico**
  -   **Almeno alfanumerico**
  -   **Alfanumerico con simboli**

- **Minuti di inattività prima che venga richiesta la password:** specifica il tempo di inattività prima che l'utente debba immettere nuovamente la password.

- **Scadenza password (giorni):** selezionare il numero di giorni che mancano alla scadenza della password attuale, quando l'utente deve creare una nuova password.

- **Ricorda cronologia password:** usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.

- **Impedisci riutilizzo delle password precedenti:** se l'opzione **Ricorda cronologia password** è selezionata, specificare il numero di password usate in precedenza che non è possibile riutilizzare.

- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività:** questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti finali viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.

### Crittografia
- **Richiedi crittografia sul dispositivo mobile:** impostare questa opzione su **Sì** per richiedere che i dispositivi vengano crittografati per la connessione alle risorse. I dispositivi vengono crittografati quando si configura l'impostazione **Richiedi una password per sbloccare i dispositivi mobili**.

## Impostazioni di integrità e sicurezza dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted:** se si abilita questa impostazione, i dispositivi jailbroken verranno valutati come non conformi.
- **Richiedi che i dispositivi impediscano l'installazione di app da origini sconosciute (Android 4.0 o versione successiva)**: per bloccare i dispositivi con le opzioni **Sicurezza > Origini sconosciute** selezionate, abilitare questa impostazione e specificare **Sì**.  
>[!IMPORTANT]
>Le applicazioni di cui si esegue il sideload richiedono l'abilitazione dell'impostazione **Origini sconosciute**.  È necessario applicare questo criterio di conformità solo se non si esegue il sideload di app Android nei dispositivi.

- **Richiedi la disabilitazione del debug USB (Android 4.2 o versione successiva)**: questa impostazione indica se è necessario rilevare o meno l'abilitazione del debug USB nel dispositivo.
- **Richiedi l'abilitazione dell'opzione "Cerca minacce per la sicurezza nel dispositivo" nei dispositivi (Android 4.2-4.4)**: questa impostazione specifica che la funzionalità **Verifica app** è abilitata nel dispositivo.
- **Livello minimo di patch di protezione per Android (Android 6.0 o versione successiva)**: usare questa impostazione per specificare il livello minimo di patch per Android.  I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere specificata nel formato: AAAA-MM-GG.
- **Richiedi l'abilitazione della protezione dalle minacce per il dispositivo**: usare questa impostazione per considerare la valutazione del rischio della soluzione Lookout MTP come condizione di conformità. Selezionare il livello di minaccia massimo consentito tra uno dei seguenti:

  - **Nessuno (protetto)**: questo è il livello più sicuro e indica che il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello per il dispositivo, questo sarà valutato come non conforme.
  - **Bassa**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.
  - **Media**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sonio di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.
  - **Alta**: questo è il livello meno sicuro. Fondamentalmente consente tutti i livelli di minaccia ed è utile solo se si usa questa soluzione esclusivamente per la creazione di report.

  Per altre informazioni dettagliate, vedere [Abilitare la regola di protezione dalle minacce per i dispositivi nei criteri di conformità](enable-device-threat-protection-rule-in-compliance-policy.md).

## Impostazioni delle proprietà dei dispositivi
- **Minimum OS required** (Versione minima richiesta del sistema operativo): quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme.
  Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.

- **Maximum OS version allowed** (Versione massima consentita del sistema operativo): quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali risulterà bloccato e l'utente dovrà contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.



<!--HONumber=Oct16_HO2-->


