---
title: Impostazioni dei criteri MAM per iOS | Microsoft Intune
description: Questo argomento descrive le impostazioni dei criteri di gestione delle app mobili per i dispositivi iOS.
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 913008568226621de4824c5bac287e8a65dc6533


---

#  <a name="ios-mobile-app-management-policy-settings"></a>Impostazioni dei criteri di gestione delle app per dispositivi mobili per iOS
Le impostazioni dei criteri descritte in questo argomento possono essere [configurate](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) per i criteri MAM (Mobile App Management, Gestione delle app per dispositivi mobili) nel pannello **Impostazioni** del portale di Azure.

Ci sono due categorie di impostazioni dei criteri: impostazioni di rilocazione dei dati e impostazioni di accesso. In questo argomento, il termine *app gestite da criteri* si riferisce alle app configurate con criteri MAM.

##  <a name="data-relocation-settings"></a>Impostazioni di rilocazione dei dati

- **Impedisci backup in iTunes e iCloud**: scegliere **Sì** per disabilitare o **No** per consentire il backup dei dati aziendali da app gestite da criteri.

  Valore predefinito = **Sì**.

- **Consenti all'app di trasferire i dati ad altre app**: scegliere una delle opzioni per indicare le app che possono ricevere dati da app gestite da criteri:
  - **App gestite da criteri**: consente il trasferimento solo ad app con i criteri MAM.
  - **Tutte le app**: consente il trasferimento a qualsiasi app.
  - **Nessuna**: non consente il trasferimento a nessuna app, incluse le altre app gestite da criteri.

  Inoltre, se si imposta l'opzione su **App gestite da criteri** o **Nessuna**, la funzionalità di iOS 9 che consente alla ricerca Spotlight di cercare i dati nelle app verrà bloccata.

  >[!NOTE]
  >Questa impostazione non controlla l'uso della funzionalità Apri in nei dispositivi mobili. Per gestire la funzionalità Apri in, vedere [Gestire il trasferimento di dati tra app iOS con Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

  Valore predefinito = **App gestite da criteri**.

- **Consenti all'app di ricevere i dati da altre app:** specificare le app autorizzate a trasferire dati alle app gestite da criteri:
  -  **App gestite da criteri**: consente il trasferimento di dati solo da altre app gestite da criteri.
  -  **Tutte le app**: consente il trasferimento dei dati da qualsiasi app.
  -  **Nessuna**: non consente il trasferimento dei dati da nessuna app.

  Valore predefinito = **Tutte le app**.

- **Impedisci Salva con nome**: scegliere **Sì** per disabilitare l'uso dell'opzione Salva con nome in qualsiasi app che usa questo criterio. Scegliere **No** per consentire l'uso di Salva con nome.

  Valore predefinito = **Sì**.

- **Limita le operazioni taglia, copia e incolla con le altre app**: specificare se le operazioni taglia, copia e incolla devono essere limitate. È possibile scegliere tra:
  -   **Bloccato**: non consente le operazioni taglia, copia e incolla tra le app gestite da criteri.
  -   **App gestite da criteri**: consente le operazioni taglia, copia e incolla solo tra le app gestite da criteri.
  -   **App gestite da criteri con Incolla in**: consente le operazioni taglia o copia tra le app gestite da criteri. I dati tagliati o copiati da qualsiasi app possono essere incollati in questa app.
  - **Qualsiasi app**: non ci sono restrizioni per le operazioni taglia, copia e incolla tra nessuna app.

  Valore predefinito = **App gestite da criteri con Incolla in**.

- **Limita il contenuto Web per la visualizzazione in Managed Browser:** quando questa impostazione è abilitata, tutti i collegamenti nell'app vengono aperti in Managed Browser.

  Per i dispositivi non registrati in Intune, i collegamenti Web nelle app gestite da criteri possono essere aperti solo nell'app Managed Browser.

  Se si usa Intune per gestire i dispositivi, vedere [Gestire l'accesso a Internet usando criteri di browser gestiti con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

  Valore predefinito = **Sì**.

- **Crittografa dati app:** per le app associate ai criteri MAM di Intune, i dati inattivi vengono crittografati usando la crittografia a livello di dispositivo offerta dal sistema operativo. Quando viene richiesto un PIN, i dati vengono crittografati in base alle impostazioni nei criteri MAM. Come indicato nella documentazione di Apple, [i moduli usati da iOS 7 sono dotati di certificazione FIPS 140-2](http://support.apple.com/en-us/HT202739).

  Nelle impostazioni dei criteri, è possibile specificare valori per la crittografia del PIN. Questi valori determinano quando vengono crittografati i dati. Le opzioni disponibili sono:
  -   **Quando il dispositivo è bloccato**: tutti i dati delle app associati a questo criterio vengono crittografati quando il dispositivo è bloccato.
  -   **Quando il dispositivo è bloccato (tranne file aperti)**: tutti i dati delle app associati a questo criterio vengono crittografati quando il dispositivo è bloccato, tranne i dati nei file attualmente aperti nell'app.
  -   **Dopo il riavvio del dispositivo**: tutti i dati delle app associati a questo criterio vengono crittografati al riavvio del dispositivo e restano crittografati fino a quando il dispositivo non viene sbloccato per la prima volta.
  -   **Usa impostazioni dispositivo**: i dati delle app vengono crittografati in base alle impostazioni predefinite del dispositivo.
  Quando si abilita questa impostazione, l'utente deve configurare e usare un PIN per accedere al dispositivo.  Se non è presente il PIN, le app non vengono aperte e all'utente viene richiesto di impostare un PIN con il messaggio "L'azienda ha richiesto l'abilitazione di un PIN del dispositivo per poter accedere a questa applicazione".

  Valore predefinito = l'opzione Crittografia non è selezionata.
- **Disabilita sincronizzazione contatti:** scegliere **Sì** per impedire la sincronizzazione delle informazioni di contatto nell'app Rubrica nativa nel dispositivo. Se si sceglie **No**, l'app salverà le informazioni di contatto nell'app Rubrica nativa nel dispositivo.

  Quando si esegue una cancellazione selettiva per rimuovere dati aziendali, i contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook.

  Valore predefinito = **Sì**.

- **Disabilita stampa:** scegliere **Sì** per impedire la stampa dei dati aziendali dalle app associate a criteri MAM.

    Valore predefinito = **Sì**.

##  <a name="access-settings"></a>Impostazioni di accesso

- **Richiedi PIN per l'accesso:** scegliere **Sì** per richiedere un PIN per l'uso di app gestite da criteri. All'utente viene richiesto di impostare questo numero alla prima esecuzione dell'app in un contesto aziendale.

  Valore predefinito = **Sì**.
    -  **Consenti PIN semplice:** consente agli utenti di usare sequenze PIN semplici, come 1234 o 1111. Valore predefinito = **Sì**.
    - **Lunghezza PIN**: specifica il numero minimo di cifre in un PIN. Valore predefinito = **4**.
    - **Numero di tentativi prima della reimpostazione del PIN:** specifica il numero di tentativi di immissione del PIN che è possibile eseguire prima che all'utente venga richiesto di reimpostare il PIN. Non esiste alcun valore predefinito per questa impostazione.

- **Consenti impronta digitale anziché PIN (iOS 8.0+)**: scegliere **Sì** per richiedere l'identificazione con impronta digitale invece di un PIN per accedere all'app.
Nei dispositivi iOS è possibile consentire all'utente di identificarsi con l'impronta digitale anziché con un PIN. Quando l'utente prova ad aprire l'app usando il proprio account aziendale, gli viene richiesto di identificarsi con l'impronta digitale invece che con un PIN.

  Valore predefinito = **Sì**.
- **Richiedi credenziali aziendali per l'accesso**: scegliere **Sì** per richiedere l'identificazione con credenziali aziendali invece di un codice PIN per accedere all'app. Se questa opzione è impostata su **Sì**, ha la priorità sulle richieste di PIN o ID tocco. All'utente verrà richiesto di fornire le credenziali aziendali.

  Valore predefinito = **No**.
- **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**: scegliere **Sì** per bloccare l'esecuzione delle app nei dispositivi jailbroken o rooted. L'utente potrà comunque usare le app per le attività personali, ma dovrà usare un dispositivo diverso per l'attività aziendale.

  Valore predefinito = **Sì**.
- **Controlla di nuovo i requisiti di accesso dopo (minuti)**
  -   **Timeout**: specifica il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.
  -   **Periodo di prova offline:** se il dispositivo è offline, specifica il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.

  Valori predefiniti = timeout di **30** minuti e periodo di prova offline di **720** minuti.
- **Intervallo offline (giorni) prima della cancellazione dei dati dell'app:** è possibile scegliere di cancellare i dati aziendali se un dispositivo è stato offline per un determinato periodo. Specificare il numero di giorni per cui un dispositivo può rimanere offline prima che i dati aziendali vengano rimossi dal dispositivo.

  >[!TIP]
  >L'immissione del valore **0** disattiva questa impostazione.

  Valore predefinito = **90** giorni.



<!--HONumber=Oct16_HO5-->


