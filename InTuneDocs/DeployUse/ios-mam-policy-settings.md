---
title: Impostazioni dei criteri MAM per iOS | Microsoft Intune
description: Questo argomento descrive le impostazioni dei criteri di gestione delle app mobili per i dispositivi iOS.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: be1ebcdf2514e45d383dd49890e0e21acf6ede44
ms.openlocfilehash: ba258bfb3140ffc79aa38ef2f46497346cdc6bfa


---

#  Impostazioni dei criteri di gestione delle app per dispositivi mobili per iOS
Le impostazioni dei criteri descritte di seguito possono essere [configurate](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) per i criteri MAM nel pannello **Impostazioni** del portale di Azure.

Esistono due categorie di impostazioni dei criteri: impostazioni di rilocazione dei dati e impostazioni di accesso.

##  Impostazioni di rilocazione dei dati
Il termine **App gestite da criteri** viene usato per indicare le app che sono configurate con criteri MAM.

- **Impedisci backup in iTunes e iCloud**: scegliere **Sì** per disabilitare o **No** per consentire il backup delle informazioni aziendali dalle app gestite da criteri.

  **Valore predefinito = Sì**

- **Consenti all'app di trasferire i dati ad altre app:** scegliere una delle opzioni per indicare le app che possono ricevere dati dalle app gestite da criteri:
  - **App gestite da criteri**: consente il trasferimento solo ad app con i criteri MAM.
  - **Tutte le app**: consente il trasferimento a qualsiasi app.
  - **Nessuna**: non consente il trasferimento a nessuna app, incluse le altre app gestite da criteri.

  Inoltre, se si imposta l'opzione su **App gestite da criteri** o **Nessuna**, la funzionalità di iOS 9 che consente a Ricerca Spotlight di cercare i dati nelle app verrà bloccata.

  **Questa impostazione non controlla l'uso della funzionalità Apri in nei dispositivi mobili. Per gestire Apri in, vedere [qui](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)**.

  **Valore predefinito = App gestite da criteri**

- **Consenti all'app di ricevere i dati da altre app:** specificare le app autorizzate a trasferire dati alle app gestite da criteri:
  -  **App gestite da criteri**: consente il trasferimento di dati solo da altre app gestite da criteri.
  -  **Tutte le app**: consente il trasferimento dei dati da qualsiasi app.
  -  **Nessuna**: non consente il trasferimento dei dati da nessuna app.

  **Valore predefinito = Tutte le app**

- **Impedisci Salva con nome**: scegliere **Sì** per disabilitare l'uso dell'opzione Salva con nome in qualsiasi app che usa questo criterio. Scegliere **No** per consentire l'uso di Salva con nome.

  **Valore predefinito = Sì**

- **Limita le operazioni taglia, copia e incolla con le altre app**: specificare quando limitare le operazioni taglia, copia e incolla. È possibile scegliere tra:
  -   **Bloccato**: non consente le operazioni taglia, copia e incolla tra le app gestite da criteri.
  -   **App gestite da criteri**: consente le operazioni taglia, copia e incolla solo tra le app gestite da criteri.
  -   **App gestite da criteri con Incolla in**: consente le operazioni taglia o copia tra le app gestite da criteri. I dati tagliati o copiati da qualsiasi app possono essere incollati in questa app.
  - **Qualsiasi app**: nessuna restrizione per le operazioni taglia, copia e incolla tra qualsiasi app.

  **Valore predefinito = App gestite da criteri con Incolla in**

- **Limita il contenuto Web per la visualizzazione in Managed Browser:** quando questa impostazione è abilitata, tutti i collegamenti nell'app vengono aperti in Managed Browser.

  Per i dispositivi non registrati in Intune, i collegamenti Web delle app gestite da criteri possono essere aperti nell'app Managed Browser solo usando i criteri di gestione delle app mobili.

  Se si usa Intune per gestire i dispositivi, vedere [Gestire l'accesso a Internet usando i criteri di Managed Browser con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

    **Valore predefinito = Sì**

- **Crittografa dati app:** per le app associate ai criteri di gestione delle app mobili di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], i dati vengono crittografati a riposo usando la crittografia a livello di dispositivo offerta dal sistema operativo. Quando viene richiesto un PIN, i dati vengono crittografati in base alle impostazioni nei criteri di gestione delle app mobili. Come indicato nella documentazione di Apple [i moduli utilizzati dal iOS 7 sono FIPS 140-2 certified](http://support.apple.com/en-us/HT202739).

  Nelle impostazioni dei criteri, è possibile specificare valori per la crittografia del PIN.  Questi valori determinano quando vengono crittografati i dati. Le opzioni disponibili sono:
  - **Quando il dispositivo è bloccato:** tutti i dati delle app associati a questo criterio vengono crittografati quando il dispositivo è bloccato.
  -   **Quando il dispositivo è bloccato (tranne file aperti):** tutti i dati delle app associati a questo criterio vengono crittografati quando il dispositivo è bloccato, tranne i dati nei file attualmente aperti nell'app.
  -   **Dopo il riavvio del dispositivo:** tutti i dati delle app associati a questo criterio vengono crittografati al riavvio del dispositivo e restano crittografati fino a quando il dispositivo non viene sbloccato per la prima volta.
  -   **Usa impostazioni dispositivo:** i dati delle app vengono crittografati in base alle impostazioni predefinite del dispositivo.
  Quando si abilita questa impostazione, l'utente finale deve configurare e usare un PIN per accedere al dispositivo.  Se non è presente il PIN le app non vengono avviate e all'utente finale viene richiesto di impostare un PIN con il messaggio "L'azienda ha richiesto l'abilitazione di un PIN del dispositivo per poter accedere a questa applicazione".

  **Valore predefinito = l'opzione Crittografia non è selezionata.**
- **Disable contact sync (Disabilita sincronizzazione contatti):** scegliere **Sì** per impedire la sincronizzazione delle informazioni di contatto nell'app Rubrica nativa nel dispositivo. Se si sceglie **No**, l'app salverà le informazioni di contatto nell'app Rubrica nativa sul dispositivo.

  Quando si esegue una cancellazione selettiva per rimuovere dati aziendali, i contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app **Microsoft Outlook**.

  **Valore predefinito = Sì**
##  Impostazioni dei criteri di accesso di iOS
Il termine **App gestite da criteri** viene usato per indicare le app che sono configurate con criteri MAM.
- **Richiedi PIN per l'accesso:** scegliere **Sì** per richiedere un PIN per l'uso di app gestite da criteri. All'utente viene richiesto di impostare questo numero alla prima esecuzione dell'app in un contesto aziendale.

  **Valore predefinito = Sì**
    -  **Consenti PIN semplice:** specificare se consentire agli utenti di usare sequenze PIN semplici, come 1234 o 1111. **Valore predefinito = Sì**.
    - **Lunghezza PIN**: specificare il numero minimo di cifre in un PIN. **Valore predefinito = 4**
    - **Numero di tentativi prima della reimpostazione del PIN:** specificare il numero di tentativi di immissione del PIN che è possibile effettuare prima che all'utente venga richiesto di reimpostare il PIN.
  **Non c'è un valore predefinito per questa impostazione**.

  - **Consenti impronta digitale anziché PIN (iOS 8+)**: scegliere **Sì** per richiedere l'identificazione con impronta digitale invece di un codice PIN per accedere all'app.
Nei dispositivi iOS è possibile consentire all'utente di identificarsi con l'impronta digitale anziché con un codice PIN. Quando l'utente finale prova ad accedere all'app usando il proprio account aziendale, gli viene richiesto di identificarsi con l'impronta digitale invece che con un codice PIN.

    **Valore predefinito = Sì**
- **Richiedi credenziali aziendali per l'accesso:** scegliere **Sì** per richiedere l'identificazione con credenziali aziendali invece di un codice PIN per accedere all'app. **Se questa opzione è impostata su Sì, ha la priorità sulle richieste di PIN o ID tocco.** All'utente verrà richiesto di fornire le credenziali aziendali.

  **Valore predefinito = No**
- **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**: scegliere **Sì** per bloccare l'esecuzione delle app nei dispositivi jailbroken o rooted. L'utente potrà comunque usare le app per le attività personali, ma dovrà usare un dispositivo diverso per l'attività aziendale.

  **Valore predefinito = Sì**
- **Controlla di nuovo i requisiti di accesso dopo (minuti)**|-   **Timeout:** periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.
  -   **Periodo di prova offline:** se il dispositivo è offline, specificare il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.

  **Valori predefiniti = timeout di 30 minuti e periodo di prova offline di 720 minuti**
  - **Intervallo offline (giorni) prima della cancellazione dei dati dell'app:** è possibile scegliere di cancellare i dati aziendali se un dispositivo è stato offline per un determinato periodo.  Specificare il numero di giorni per cui un dispositivo può rimanere offline prima che i dati aziendali vengano rimossi dal dispositivo. **Immettere il valore 0 per disattivare questa impostazione**.

  **Valore predefinito = 90 giorni**



<!--HONumber=Jul16_HO5-->


