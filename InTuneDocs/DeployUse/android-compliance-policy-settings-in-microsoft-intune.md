---
title: "Impostazioni dei criteri di conformità per i dispositivi Android | Microsoft Intune"
description: "Questo argomento descrive le impostazioni dei criteri di conformità per i dispositivi Android."
keywords: 
author: karthikaraman
ms.author: karaman
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
ms.sourcegitcommit: e24de6814d9e01c64768f425e961a7822f4b27a1
ms.openlocfilehash: 5f02618da6fb3c538ad131fe8abaf35a6be6e177


---


# Impostazioni dei criteri di conformità per i dispositivi Android in Microsoft Intune

Le impostazioni dei criteri descritte in questo argomento si applicano ai dispositivi che eseguono Android 4.0 e versioni successive oppure Samsung KNOX 4.0 e versioni successive.

Per informazioni su altre piattaforme, selezionare una delle voci seguenti:
> [!div class="op_single_selector"]
- [Impostazioni dei criteri di conformità per i dispositivi iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Impostazioni dei criteri di conformità per i dispositivi Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Impostazioni di sicurezza del sistema
### Password
- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per richiedere agli utenti di immettere una password prima di poter accedere al dispositivo.

-  **Lunghezza minima password**: specifica il numero minimo di cifre o caratteri per la password dell'utente.

- **Qualità password:** questa impostazione rileva se i requisiti di password specificati sono configurati nel dispositivo. Abilitare questa impostazione per richiedere agli utenti di impostare determinati requisiti di password per i dispositivi Android. È possibile scegliere tra:

  -   **Protezione biometrica bassa**
  -   **Richiesto**
  -   **Almeno numerico**
  -   **Almeno alfabetico**
  -   **Almeno alfanumerico**
  -   **Alfanumerico con simboli**

- **Minuti di inattività prima che venga richiesta la password:** specifica il tempo di inattività prima che l'utente debba immettere di nuovo la password.

- **Scadenza password (giorni):** selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.

- **Ricorda cronologia password:** usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.

- **Impedisci riutilizzo delle password precedenti:** se l'opzione **Ricorda cronologia password** è selezionata, specifica il numero di password usate in precedenza che non è possibile usare di nuovo.

- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività:** questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.

### Crittografia
- **Richiedi crittografia sul dispositivo mobile:** impostare questa opzione su **Sì** per richiedere che i dispositivi vengano crittografati per la connessione alle risorse. I dispositivi vengono crittografati se si sceglie l'impostazione **Richiedi una password per sbloccare i dispositivi mobili**.

## Impostazioni di integrità e sicurezza dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted:** se si abilita questa impostazione, i dispositivi jailbroken vengono considerati come non conformi.
- **Richiedi che i dispositivi impediscano l'installazione di app da origini sconosciute (Android 4.0 o versione successiva)**: per bloccare i dispositivi che hanno le opzioni **Sicurezza** > **Origini sconosciute** abilitate sul dispositivo, selezionare questa impostazione e specificare **Sì**.  
>[!IMPORTANT]
>Le applicazioni di cui si esegue il sideload richiedono l'abilitazione dell'impostazione **Origini sconosciute**. Imporre questo criterio di conformità solo se non si esegue il sideload di app Android nei dispositivi.

- **Richiedi la disabilitazione del debug USB (Android 4.2 o versione successiva)**: questa impostazione indica se è necessario rilevare o meno l'abilitazione del debug USB nel dispositivo.
- **Richiedi l'abilitazione dell'opzione "Cerca minacce per la sicurezza nel dispositivo" nei dispositivi (Android 4.2-4.4)**: questa impostazione specifica che la funzionalità **Verifica app** è abilitata nel dispositivo.
- **Livello minimo di patch di protezione per Android (Android 6.0 o versione successiva)**: usare questa impostazione per specificare il livello minimo di patch per Android. I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere specificata nel formato: AAAA-MM-GG.
- **Richiedi l'abilitazione della protezione dalle minacce per il dispositivo**: usare questa impostazione per considerare la valutazione del rischio della soluzione Lookout MTP come condizione di conformità. Selezionare il livello di minaccia più alto consentito tra uno dei seguenti:

  - **Nessuno (protetto)**: questo è il livello più sicuro e indica che il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello per il dispositivo, questo sarà considerato come non conforme.
  - **Basso**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Medio**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene considerato come non conforme.
  - **Alta**: questo è il livello meno sicuro. Questa impostazione abilita tutti i livelli di rischio. Potrebbe essere utile usare questa soluzione solo per la creazione di report.

  Per altre informazioni dettagliate, vedere [Abilitare la regola di protezione dalle minacce per i dispositivi nei criteri di conformità](enable-device-threat-protection-rule-in-compliance-policy.md).

## Impostazioni delle proprietà dei dispositivi
- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme.
  Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo per poter accedere alle risorse aziendali.

- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali è bloccato e l'utente deve contattare l'amministratore IT. Fino a quando la regola non viene modificata per consentire la versione del sistema operativo, non è possibile usare il dispositivo per accedere alle risorse aziendali.



<!--HONumber=Oct16_HO3-->


