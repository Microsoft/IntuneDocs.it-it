---
title: Impostazioni dei criteri MAM per Android | Documentazione Microsoft
description: Questo argomento descrive le impostazioni dei criteri di gestione di app mobili per i dispositivi Android.
keywords: 
author: andredm7
ms.author: andredm
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
ms.sourcegitcommit: 28a1bf4c7c2200901761a53394064d920b56dad6
ms.openlocfilehash: 058527911594614865ae44ba9de7ab0887fa60b2


---

# <a name="android-mobile-app-management-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di gestione delle app per dispositivi mobili Android in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Le impostazioni dei criteri descritte in questo argomento possono essere [configurate](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) per i criteri MAM (Mobile App Management, Gestione delle app per dispositivi mobili) nel pannello **Impostazioni** del portale di Azure.
Ci sono due categorie di impostazioni dei criteri: impostazioni di rilocazione dei dati e impostazioni di accesso. In questo argomento, il termine _**app gestite da criteri**_ si riferisce alle app configurate con criteri MAM.


##  <a name="data-relocation-settings"></a>Impostazioni di rilocazione dei dati

| Impostazioni | Uso | Valori predefiniti |
|------|------|------|
| **Impedisci backup in Android** | Scegliere **Sì** per impedire all'app di eseguire il backup di dati aziendali o dell'istituto di istruzione nel [servizio di backup Android](https://developer.android.com/google/backup/index.html). Scegliere **No** per consentire all'app di eseguire il backup di dati aziendali o dell'istituto di istruzione.| sì |
| **Consenti all'app di trasferire i dati ad altre app** | Specificare le app da cui questa app può ricevere dati: <ul><li> **App gestite da criteri**: consente il trasferimento solo ad altre app gestite da criteri.</li> <li>**Tutte le app**: consente il trasferimento a qualsiasi app. </li> <li>**Nessuna**: non consente il trasferimento a nessuna app, incluse le altre app gestite da criteri.</li></ul> | Tutte le app |
| **Consenti all'app di ricevere i dati da altre app** | Specificare le app che possono trasferire dati a questa app: <ul><li>**App gestite da criteri**: consente il trasferimento solo da altre app gestite da criteri.</li><li>**Tutte le app**: consente il trasferimento dei dati da qualsiasi app.</li><li>**Nessuna**: non consente il trasferimento da alcuna app, incluse le altre app gestite da criteri. | Tutte le app |
| **Impedisci "Salva con nome"** | Scegliere **Sì** per disabilitare l'uso dell'opzione Salva con nome in questa app. Scegliere **No** per consentire l'uso di Salva con nome. | No |
| **Limita le operazioni taglia, copia e incolla con le altre app** | Specificare quando è possibile usare le azioni taglia, copia e incolla con questa app. È possibile scegliere tra: <ul><li>**Bloccato**: non consente le azioni taglia, copia e incolla tra questa app e altre app.</li><li>**App gestite da criteri**: consente le azioni taglia, copia e incolla tra questa app e altre app gestite da criteri.</li><li>**App gestite da criteri con Incolla in**: consente le azioni taglia o copia tra questa app e altre app gestite da criteri. I dati da qualsiasi app possono essere incollati in questa app.</li><li>**Qualsiasi app**: nessuna restrizione per le azioni taglia, copia e incolla in e da questa app. | Qualsiasi app |
|**Limita il contenuto Web per la visualizzazione in Managed Browser** | Scegliere **Sì** per imporre l'apertura dei collegamenti Web nell'app con l'app Managed Browser. <br><br> Per i dispositivi non registrati in Intune, i collegamenti Web nelle app gestite da criteri possono essere aperti solo nell'app Managed Browser. <br><br> Se si usa Intune per gestire i dispositivi, vedere [Gestire l'accesso a Internet usando criteri di browser gestiti con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md). | No |
| **Crittografa dati app** | Scegliere **Sì** per abilitare la crittografia dei dati aziendali o dell'istituto di istruzione in questa app. Intune usa uno schema di crittografia OpenSSL insieme al sistema di archivio chiavi Android per crittografare i dati dell'applicazione in modo sicuro. I dati vengono crittografati in modo sincrono durante le operazioni di I/O dei file. Il contenuto nella memoria del dispositivo è sempre crittografato. <br><br> Il metodo di crittografia **non** è certificato FIPS 140-2.  | sì |
| **Disabilita sincronizzazione contatti** | Scegliere **Sì** per impedire all'app di salvare dati nell'app Contatti nativa nel dispositivo. Se si sceglie **No**, l'app può salvare dati nell'app Contatti nativa nel dispositivo. <br><br>Quando si esegue una cancellazione selettiva per rimuovere dati aziendali o dell'istituto di istruzione dall'app, i contatti sincronizzati direttamente dall'app nell'app Contatti nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook. | No |
| **Disabilita stampa** | Scegliere **Sì** per impedire all'app di stampare dati aziendali o dell'istituto di istruzione. | No |


  >[!NOTE]
  >Il metodo di crittografia per l'impostazione **Crittografa dati app** **non** è certificato FIPS 140-2.




##  <a name="access-settings"></a>Impostazioni di accesso

| Impostazioni | Uso | Valori predefiniti |
|------|------|------|
| **Richiedi PIN per l'accesso** | Scegliere **Sì** per richiedere un PIN per usare questa app. All'utente viene richiesto di impostare questo PIN alla prima esecuzione dell'app in un contesto aziendale o dell'istituto di istruzione. Valore predefinito = **Sì**.<br><br> Configurare le impostazioni seguenti per la complessità del PIN: <ul><li>**Numero di tentativi prima della reimpostazione del PIN**: specifica il numero di tentativi di immissione del PIN che è possibile eseguire prima che all'utente venga richiesto di reimpostare il PIN. Valore predefinito = **5**.</li><li> **Consenti PIN semplice**: scegliere **Sì** per consentire agli utenti di usare sequenze PIN semplici, come 1234 o 1111. Scegliere **No** per impedire l'uso di sequenze semplici. Valore predefinito = **Sì**. </li><li> **Lunghezza PIN**: specificare il numero minimo di cifre in una sequenza di PIN. Valore predefinito = **4**. </li><li> **Consenti impronta digitale anziché PIN (Android 6.0+)**: scegliere **Sì** per consentire all'utente di usare l'[autenticazione con impronta digitale](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) invece di un PIN per accedere all'app. Valore predefinito = **Sì**.<br><br> Nei dispositivi Android è possibile consentire all'utente di confermare l'identità usando l'[autenticazione con impronta digitale Android](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) invece di un PIN. Quando l'utente prova a usare l'app usando il proprio account aziendale o dell'istituto di istruzione, gli viene richiesto di identificarsi con l'impronta digitale invece che immettendo un PIN. </li></ul>| Richiedi PIN: sì <br><br> Tentativi prima della reimpostazione del PIN: 5 <br><br> Consenti PIN semplice: sì <br><br> Lunghezza PIN: 4 <br><br> Consenti impronta digitale: sì |
| **Richiedi credenziali aziendali per l'accesso** | Scegliere **Sì** per richiedere all'utente di accedere con il proprio account aziendale o dell'istituto di istruzione anziché immettere un PIN per accedere all'app. Se questa opzione è impostata su **Sì**, ha la priorità sulle richieste di PIN o ID tocco.  | No |
| **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted** |  Scegliere **Sì** per impedire l'esecuzione dell'app nei dispositivi jailbroken o rooted. L'utente potrà comunque usare le app per le attività personali, ma dovrà usare un dispositivo diverso per accedere ai dati aziendali o dell'istituto di istruzione nell'app. | sì |
| **Controlla di nuovo i requisiti di accesso dopo (minuti)** | Configurare le seguenti impostazioni: <ul><li>**Timeout**: specifica il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app. Valore predefinito: **30** minuti.</li><li>**Periodo di prova offline:** se il dispositivo è offline, specifica il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app. Valore predefinito: **720** minuti (12 ore).</li></ul>| Timeout: 30 <br><br> Offline: 720 |
| **Intervallo offline (giorni) prima della cancellazione dei dati dell'app** | I dati aziendali o dell'istituto di istruzione in questa app possono essere cancellati se un dispositivo è rimasto offline per un periodo più lungo di un determinato intervallo. Specificare il numero di giorni per cui un dispositivo può rimanere offline prima che i dati aziendali o dell'istituto di istruzione vengano rimossi dal dispositivo. <br><br> | 90 giorni |
| **Blocca acquisizione schermo e Assistente per Android (Android 6.0+)** | Scegliere **Sì** per bloccare le funzionalità di acquisizione schermo e **Assistente per Android** del dispositivo quando si usa questa app. Se si sceglie **Sì** verrà anche sfocata l'immagine di anteprima della funzione Switch quando si usa questa app con un account aziendale o dell'istituto di istruzione. | No |



<!--HONumber=Dec16_HO3-->


