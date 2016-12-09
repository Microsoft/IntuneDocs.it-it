---
title: Impostazioni dei criteri MAM per Android | Microsoft Intune
description: Questo argomento descrive le impostazioni dei criteri di gestione di app mobili per i dispositivi Android.
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d0a1a2b3f4e5dbac8b333db3a5cc4bb32c0d61ef


---

# <a name="android-mobile-app-management-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di gestione delle app per dispositivi mobili Android in Microsoft Intune
Le impostazioni dei criteri descritte in questo argomento possono essere [configurate](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) per i criteri MAM (Mobile App Management, Gestione delle app per dispositivi mobili) nel pannello **Impostazioni** del portale di Azure.
Ci sono due categorie di impostazioni dei criteri: impostazioni di rilocazione dei dati e impostazioni di accesso. In questo argomento, il termine *app gestite da criteri* si riferisce alle app configurate con criteri MAM.

##  <a name="data-relocation-settings"></a>Impostazioni di rilocazione dei dati

- **Impedisci backup in Android**: scegliere **Sì** per disabilitare o **No** per abilitare il backup delle informazioni aziendali dalle app gestite da criteri.

  Valore predefinito = **Sì**
- **Consenti all'app di trasferire i dati ad altre app**: scegliere una delle opzioni per indicare quale tipo di app può ricevere dati aziendali dalle app gestite da criteri:
  -   **App gestite da criteri**: abilita il trasferimento ad app con i soli criteri MAM.
  -   **Tutte le app**: abilita il trasferimento a qualsiasi app.
  -   **Nessuna**: non consente il trasferimento dei dati a nessuna app.

 Valore predefinito = **App gestite da criteri**.
- **Consenti all'app di ricevere i dati da altre app**: specificare quali app possono trasferire dati alle app gestite da criteri:
  -   **App gestite da criteri**: abilita il trasferimento di dati solo da altre app gestite da criteri.
  -   **Tutte le app**: abilita il trasferimento dei dati da qualsiasi app.
  -   **Nessuna**: non consente il trasferimento dei dati da nessuna app.

  Valore predefinito = **Tutte le app**

-   **Impedisci Salva con nome**: scegliere **Sì** per disabilitare l'uso dell'opzione Salva con nome in qualsiasi app che usa questo criterio. Scegliere **No** per abilitare l'uso di Salva con nome.

  Valore predefinito = **Sì**
- **Limita le operazioni taglia, copia e incolla con le altre app**: specificare se le operazioni taglia, copia e incolla devono essere limitate. È possibile scegliere tra:
  -   **Bloccato**: non consente le operazioni taglia, copia e incolla tra le app gestite da criteri.
  -   **App gestite da criteri**: abilita le operazioni taglia, copia e incolla solo tra le app gestite da criteri.
  -   **App gestite da criteri con Incolla in**: abilita le operazioni taglia o copia tra le app gestite da criteri. I dati tagliati o copiati da qualsiasi app possono essere incollati in questa app.
  -   **Qualsiasi app**: non ci sono restrizioni per le operazioni taglia, copia e incolla tra nessuna app.

  Valore predefinito = **App gestite da criteri con Incolla in**
-   **Limita il contenuto Web per la visualizzazione in Managed Browser**: scegliere **Sì** per specificare che tutti i collegamenti nell'app vengano aperti in Managed Browser.

  Per i dispositivi non registrati in Intune, i collegamenti delle app gestite da criteri possono essere aperti solo nell'app Managed Browser se si usano i criteri MAM.

  Se si usa Intune per gestire i dispositivi, vedere [Gestire l'accesso a Internet usando criteri di browser gestiti con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

  Valore predefinito = **Sì**
- **Crittografa dati app**: scegliere **Sì** per abilitare la crittografia. Quando questa impostazione è abilitata, Microsoft offre la crittografia per le app associate ai criteri MAM. I dati vengono crittografati in modo sincrono durante le operazioni di I/O dei file. Il contenuto nella memoria del dispositivo è sempre crittografato.
  >[!NOTE]
  >Il metodo di crittografia non è conforme agli standard FIPS 140-2.

  Valore predefinito = **Sì**

- **Disabilita sincronizzazione contatti**: scegliere **Sì** per impedire la sincronizzazione delle informazioni di contatto con l'app Rubrica nativa nel dispositivo. Se si sceglie **No**, l'app salva le informazioni di contatto nell'app Rubrica nativa nel dispositivo.

  Quando si esegue una cancellazione selettiva per rimuovere dati aziendali, i contatti sincronizzati direttamente tra l'app e la Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati tra la Rubrica nativa e un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook.

  Valore predefinito = **Sì**
- **Disabilita stampa**: scegliere **Sì** per impedire la stampa dei dati aziendali dalle app associate a criteri MAM.

  Valore predefinito = **Sì**

##  <a name="access-settings"></a>Impostazioni di accesso

- **Richiedi PIN per l'accesso:** scegliere **Sì** per richiedere un PIN per l'uso di app gestite da criteri. All'utente viene richiesto di impostare questo numero alla prima esecuzione dell'app in un contesto aziendale.

 Valore predefinito = **Sì**

 -  **Consenti PIN semplice:** consente agli utenti di usare sequenze PIN semplici, come 1234 o 1111. Valore predefinito = **Sì**.
 - **Lunghezza PIN**: specifica il numero minimo di cifre in un PIN. Valore predefinito = **4**.
 - **Numero di tentativi prima della reimpostazione del PIN:** specifica il numero di tentativi di immissione del PIN che è possibile eseguire prima che all'utente venga richiesto di reimpostare il PIN. Non esiste alcun valore predefinito per questa impostazione.
 - **Consenti impronta digitale anziché PIN (Android 6.0+)**: scegliere **Sì** per richiedere l'identificazione con impronta digitale invece di un codice PIN per accedere all'app.
 Nei dispositivi Android è possibile consentire agli utenti di identificarsi con l'impronta digitale anziché con un codice PIN. Quando provano ad accedere all'app usando il proprio account aziendale, verrà loro richiesto di identificarsi con l'impronta digitale invece che con un PIN.
 - **Richiedi credenziali aziendali per l'accesso**: scegliere **Sì** per richiedere l'identificazione con credenziali aziendali invece di un PIN o dell'impronta digitale per accedere all'app. Se è impostata su **Sì**, questa impostazione ha la priorità sulle richieste di un PIN o di un ID tocco. All'utente verrà richiesto di fornire le credenziali aziendali. Valore predefinito = **No**.


- **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**: scegliere **Sì** per bloccare l'esecuzione delle app nei dispositivi jailbroken o rooted. L'utente può continuare a usare le app per le attività personali, ma deve usare un dispositivo diverso per l'attività aziendale.

  Valore predefinito = **Sì**
- **Controlla di nuovo i requisiti di accesso dopo (minuti)**
  -   **Timeout**: specifica il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.
  -   **Periodo di prova offline:** se il dispositivo è offline, specifica il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.

  Valori predefiniti = timeout di **30** minuti e periodo di prova offline di **720** minuti

-   **Intervallo offline (giorni) prima della cancellazione dei dati dell'app**: scegliere se cancellare i dati aziendali se un dispositivo è stato offline per un determinato periodo.  Specificare il numero di giorni per cui un dispositivo può rimanere offline prima che i dati aziendali vengano rimossi dal dispositivo.

    >[!TIP]
    >L'immissione del valore **0** disattiva questa impostazione.

  Valore predefinito = **90** giorni
- **Blocca acquisizione schermo e Assistente per Android (Android 6 Marshmallow o versioni successive)**: scegliere **Sì** per bloccare le funzionalità di acquisizione schermo e dell'**Assistente per Android** del dispositivo quando si usa l'app.



<!--HONumber=Dec16_HO2-->


