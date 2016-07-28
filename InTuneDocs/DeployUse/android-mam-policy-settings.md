---
title: Impostazioni dei criteri MAM per Android | Microsoft Intune
description: Questo argomento descrive le impostazioni dei criteri di gestione di app mobili per i dispositivi Android.
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 359f76daa35a14e4107a9e03c6a1b1f4d1215777
ms.openlocfilehash: bbb2d56753d47e68aeba1e5f17188f1f7a740c6e


---

# Impostazioni dei criteri di gestione delle app per dispositivi mobili Android in Microsoft Intune
Le impostazioni dei criteri descritte di seguito possono essere [configurate](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) per i criteri MAM nel pannello **Impostazioni** del portale di Azure.
Esistono due categorie di impostazioni dei criteri: impostazioni di rilocazione dei dati e impostazioni di accesso.

##  Impostazioni di rilocazione dei dati
Il termine **App gestite da criteri** viene usato per indicare le app che sono configurate con criteri MAM.
- **Impedisci backup in Android**: scegliere **Sì** per disabilitare o **No** per consentire il backup delle informazioni aziendali dalle app gestite da criteri.

  **Valore predefinito = Sì**
- **Consenti all'app di trasferire i dati ad altre app**: scegliere una delle opzioni per indicare le app che possono ricevere dati aziendali dalle app gestite da criteri:
  -   **App gestite da criteri**: consente il trasferimento solo ad app con i criteri MAM
  -   **Tutte le app**: consente il trasferimento a qualsiasi app
  -   **Nessuna**: non consente il trasferimento dei dati a nessuna app

  **Valore predefinito = App gestite da criteri**
- **Consenti all'app di ricevere i dati da altre app:** specificare le app autorizzate a trasferire dati alle app gestite da criteri:
  -   **App gestite da criteri**: consente il trasferimento di dati solo da altre app gestite da criteri
  -   **Tutte le app**: consente il trasferimento dei dati da qualsiasi app
  -   **Nessuna**: non consente il trasferimento dei dati da nessuna app

      **Valore predefinito = Tutte le app**

-   **Impedisci Salva con nome**: scegliere **Sì** per disabilitare l'uso dell'opzione Salva con nome in qualsiasi app che usa questo criterio. Scegliere **No** per consentire l'uso di Salva con nome.

  **Valore predefinito = Sì**
- **Limita le operazioni taglia, copia e incolla con le altre app**: specificare quando limitare le operazioni taglia, copia e incolla. È possibile scegliere tra:
  -   **Bloccato**: non consente le operazioni taglia, copia e incolla tra le app gestite da criteri.
  -   **App gestite da criteri**: consente le operazioni taglia, copia e incolla solo tra le app gestite da criteri.
  -   **App gestite da criteri con Incolla in**: consente le operazioni taglia o copia tra le app gestite da criteri. I dati tagliati o copiati da qualsiasi app possono essere incollati in questa app.
  -   **Qualsiasi app**: nessuna restrizione per le operazioni taglia, copia e incolla tra qualsiasi app.

    **Valore predefinito = App gestite da criteri con Incolla in**
-   **Limita il contenuto Web per la visualizzazione in Managed Browser:** quando questa impostazione è abilitata, tutti i collegamenti nell'app vengono aperti in Managed Browser.

  Per i dispositivi non registrati in Intune, i collegamenti Web delle app gestite da criteri vengono aperti nell'app Managed Browser solo usando i criteri di gestione delle app mobili.

  Se si usa Intune per gestire i dispositivi, vedere [Manage Internet access using managed browser policies with Microsoft Intune](manage-internet-access-using-managed-browser-policies.md) (Gestire l'accesso a Internet usando criteri di Managed Browser con Microsoft Intune).

    **Valore predefinito = Sì**
- **Crittografa dati app**: scegliere **Sì** per abilitare la crittografia. Quando quest'impostazione è abilitata, per le app associate ai criteri di gestione delle app mobili, la crittografia viene offerta da Microsoft. I dati vengono crittografati in modo sincrono durante le operazioni di I/O file. Il contenuto nell'archivio del dispositivo è sempre crittografato.
  >[!NOTE]
  >Il metodo di crittografia non è conforme agli standard FIPS 140-2

  **Valore predefinito = Sì**

- **Disable contact sync (Disabilita sincronizzazione contatti):** scegliere **Sì** per impedire la sincronizzazione delle informazioni di contatto nell'app Rubrica nativa nel dispositivo. Se si sceglie **No**, l'app salverà le informazioni di contatto nell'app Rubrica nativa sul dispositivo.<br/>Quando si esegue una cancellazione selettiva per rimuovere dati aziendali, i contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app **Microsoft Outlook**.

  **Valore predefinito = Sì**

##  Impostazioni dei criteri di accesso di Android
Il termine **App gestite da criteri** viene usato per indicare le app che sono configurate con criteri MAM

- **Richiedi PIN per l'accesso:** scegliere **Sì** per richiedere un PIN per l'uso di app gestite da criteri. All'utente viene richiesto di impostare questo numero alla prima esecuzione dell'app in un contesto aziendale.

 **Valore predefinito = Sì**

 -  **Consenti PIN semplice:** specificare se consentire agli utenti di usare sequenze PIN semplici, come 1234 o 1111. **Valore predefinito = Sì**.
 - **Lunghezza PIN**: specificare il numero minimo di cifre in un PIN. **Valore predefinito = 4**
 - **Numero di tentativi prima della reimpostazione del PIN:** specificare il numero di tentativi di immissione del PIN che è possibile effettuare prima che all'utente venga richiesto di reimpostare il PIN. **Non esiste alcun valore predefinito per questa impostazione.**
- **Richiedi credenziali aziendali per l'accesso**: scegliere **Sì** per richiedere l'identificazione con credenziali aziendali invece di un codice PIN per accedere all'app.  Se questa opzione è impostata su **Sì**, ha la priorità sulle richieste di PIN o ID tocco.  All'utente verrà richiesto di fornire le credenziali aziendali.

  **Valore predefinito = No**
- **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**: scegliere **Sì** per bloccare l'esecuzione delle app nei dispositivi jailbroken o rooted. L'utente potrà comunque usare le app per le attività personali, ma dovrà usare un dispositivo diverso per l'attività aziendale.

  **Valore predefinito = Sì**
- **Controlla di nuovo i requisiti di accesso dopo (minuti)**-   **Timeout:** periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.
  -   **Periodo di prova offline:** se il dispositivo è offline, specificare il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app.

    **Valori predefiniti = timeout di 30 minuti e periodo di prova offline di 720 minuti**

-   **Intervallo offline (giorni) prima della cancellazione dei dati dell'app:** è possibile scegliere di cancellare i dati aziendali se un dispositivo è stato offline per un determinato periodo.  Specificare il numero di giorni per cui un dispositivo può rimanere offline prima che i dati aziendali vengano rimossi dal dispositivo. **Suggerimento:** immettere un valore pari a 0 per disattivare questa impostazione.

  **Valore predefinito = 90 giorni**
- **Blocca acquisizione schermo e Assistente per Android (Android 6 Marshmallow o versione successiva):** scegliere **Sì** per bloccare le funzionalità di acquisizione schermo e dell'**Assistente per Android** del dispositivo quando si usa l'app.



<!--HONumber=Jul16_HO3-->


