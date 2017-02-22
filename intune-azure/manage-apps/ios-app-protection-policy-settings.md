---
title: Impostazioni dei criteri di protezione delle app per iOS| Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: Questo argomento descrive le impostazioni dei criteri di protezione delle app per i dispositivi iOS.'
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 291c380b861d3ad7df2fc1af4274d9e8bb014846
ms.openlocfilehash: 55faaa918e309616c9b84eeb429f42d52796c1d9


---

#  <a name="ios-app-protection-policy-settings"></a>Impostazioni dei criteri di protezione delle app per iOS 
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Le impostazioni dei criteri descritte in questo argomento possono essere [configurate](app-protection-policies.md) per un criterio di protezione delle app nel pannello **Impostazioni** del portale di Azure.

Ci sono due categorie di impostazioni dei criteri: impostazioni di rilocazione dei dati e impostazioni di accesso. In questo argomento il termine ***app gestite da criteri*** si riferisce alle app configurate con criteri di protezione delle app.

##  <a name="data-relocation-settings"></a>Impostazioni di rilocazione dei dati

| Impostazioni | Uso | Valori predefiniti |
|------|------|------|
| **Impedisci backup in iTunes e iCloud** | Scegliere **Sì** per impedire all'app di eseguire il backup dei dati aziendali o dell'istituto di istruzione in iTunes e iCloud. Scegliere **No** per consentire all'app di eseguire il backup dei dati aziendali o dell'istituto di istruzione in iTunes e iCloud.| sì |
| **Consenti all'app di trasferire i dati ad altre app** | Specificare le app da cui questa app può ricevere dati: <ul><li> **App gestite da criteri**: consente il trasferimento solo ad altre app gestite da criteri.</li> <li>**Tutte le app**: consente il trasferimento a qualsiasi app. </li> <li>**Nessuna**: non consente il trasferimento a nessuna app, incluse le altre app gestite da criteri.</li></ul> Inoltre, se si imposta l'opzione su **App gestite da criteri** o **Nessuna**, la funzionalità di iOS 9 che consente alla ricerca Spotlight di cercare i dati nelle app verrà bloccata. <br><br> | Tutte le app |
| **Consenti all'app di ricevere i dati da altre app** | Specificare le app che possono trasferire dati a questa app: <ul><li>**App gestite da criteri**: consente il trasferimento solo da altre app gestite da criteri.</li><li>**Tutte le app**: consente il trasferimento dei dati da qualsiasi app.</li><li>**Nessuna**: non consente il trasferimento da alcuna app, incluse le altre app gestite da criteri. | Tutte le app |
| **Impedisci "Salva con nome"** | Scegliere **Sì** per disabilitare l'uso dell'opzione Salva con nome in questa app. Scegliere **No** per consentire l'uso di Salva con nome. | No |
| **Limita le operazioni taglia, copia e incolla con le altre app** | Specificare quando è possibile usare le azioni taglia, copia e incolla con questa app. È possibile scegliere tra: <ul><li>**Bloccato**: non consente le azioni taglia, copia e incolla tra questa app e altre app.</li><li>**App gestite da criteri**: consente le azioni taglia, copia e incolla tra questa app e altre app gestite da criteri.</li><li>**App gestite da criteri con Incolla in**: consente le azioni taglia o copia tra questa app e altre app gestite da criteri. I dati da qualsiasi app possono essere incollati in questa app.</li><li>**Qualsiasi app**: nessuna restrizione per le azioni taglia, copia e incolla in e da questa app. | Qualsiasi app |
|**Limita il contenuto Web per la visualizzazione in Managed Browser** | Scegliere **Sì** per imporre l'apertura dei collegamenti Web nell'app con l'app Managed Browser. <br><br> Per i dispositivi non registrati in Intune, i collegamenti Web nelle app gestite da criteri possono essere aperti solo nell'app Managed Browser. <br><br> Se si usa Intune per gestire i dispositivi, vedere [Gestire l'accesso a Internet usando criteri di browser gestiti con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/manage-internet-access-using-managed-browser-policies). | No |
| **Crittografa dati app** | Per le applicazioni gestite da criteri, i dati inattivi vengono crittografati usando lo schema di crittografia a livello di dispositivo fornito da iOS. Quando viene richiesto un PIN, i dati vengono crittografati in base alle impostazioni nei criteri di protezione delle app. <br><br> Passare alla documentazione di Apple ufficiale [qui](https://support.apple.com/HT202739) per vedere quali moduli di crittografia iOS sono certificati FIPS 140-2 o in attesa della certificazione FIPS 140-2. <br><br> Specificare quando vengono crittografati i dati aziendali o dell'istituto di istruzione nell'app. È possibile scegliere tra: <ul><li>**Quando il dispositivo è bloccato**: tutti i dati delle app associati a questo criterio vengono crittografati quando il dispositivo è bloccato.</li><li>**Quando il dispositivo è bloccato e sono presenti file aperti**: tutti i dati delle app associati a questo criterio vengono crittografati quando il dispositivo è bloccato, tranne i dati nei file attualmente aperti nell'app.</li><li>**Dopo il riavvio del dispositivo**: tutti i dati delle app associati a questo criterio vengono crittografati al riavvio del dispositivo e restano crittografati fino a quando il dispositivo non viene sbloccato per la prima volta.</li><li>**Usa impostazioni dispositivo**: i dati delle app vengono crittografati in base alle impostazioni predefinite del dispositivo. <br><br> Quando si abilita questa impostazione, l'utente deve configurare e usare un PIN per accedere al dispositivo.  Se non è presente il PIN, le app non vengono aperte e all'utente viene richiesto di impostare un PIN con il messaggio "L'azienda ha richiesto l'abilitazione di un PIN del dispositivo per poter accedere a questa applicazione". </li></ul> | Quando il dispositivo è bloccato |
| **Disabilita sincronizzazione contatti** | Scegliere **Sì** per impedire all'app di salvare dati nell'app Contatti nativa nel dispositivo. Se si sceglie **No**, l'app può salvare dati nell'app Contatti nativa nel dispositivo. <br><br>Quando si esegue una cancellazione selettiva per rimuovere dati aziendali o dell'istituto di istruzione dall'app, i contatti sincronizzati direttamente dall'app nell'app Contatti nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook. | No |
| **Disabilita stampa** | Scegliere **Sì** per impedire all'app di stampare dati aziendali o dell'istituto di istruzione. | No |


> [!NOTE]
> Nessuna delle impostazioni di rilocazione dei dati controlla la funzionalità "Apri in" gestita di Apple nei dispositivi iOS. Per gestire la funzionalità "Apri in" gestita di Apple, vedere [Gestire il trasferimento di dati tra app iOS con Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).


## <a name="access-settings"></a>Impostazioni di accesso

| Impostazioni | Uso | Valori predefiniti |
|------|------|------|
| **Richiedi PIN per l'accesso** | Scegliere **Sì** per richiedere un PIN per usare questa app. All'utente viene richiesto di impostare questo PIN alla prima esecuzione dell'app in un contesto aziendale o dell'istituto di istruzione. Valore predefinito = **Sì**.<br><br> Configurare le impostazioni seguenti per la complessità del PIN: <ul><li>**Numero di tentativi prima della reimpostazione del PIN**: specifica il numero di tentativi di immissione del PIN che è possibile eseguire prima che all'utente venga richiesto di reimpostare il PIN. Valore predefinito = **5**.</li><li> **Consenti PIN semplice**: scegliere **Sì** per consentire agli utenti di usare sequenze PIN semplici, come 1234 o 1111. Scegliere **No** per impedire l'uso di sequenze semplici. Valore predefinito = **Sì**. </li><li> **Lunghezza PIN**: specificare il numero minimo di cifre in una sequenza di PIN. Valore predefinito = **4**. </li><li> **Consenti impronta digitale anziché PIN (iOS 8.0+)**: scegliere **Sì** per consentire all'utente di usare l'[ID tocco](https://support.apple.com/en-us/HT201371) invece di un PIN per accedere all'app. Valore predefinito = **Sì**.<br><br> Nei dispositivi iOS è possibile consentire all'utente di confermare l'identità usando l'[ID tocco](https://support.apple.com/en-us/HT201371) invece di un PIN. Quando l'utente prova a usare l'app usando il proprio account aziendale o dell'istituto di istruzione, gli viene richiesto di identificarsi con l'impronta digitale invece che immettendo un PIN. </li></ul>| Richiedi PIN: sì <br><br> Tentativi prima della reimpostazione del PIN: 5 <br><br> Consenti PIN semplice: sì <br><br> Lunghezza PIN: 4 <br><br> Consenti impronta digitale: sì |
| **Richiedi credenziali aziendali per l'accesso** | Scegliere **Sì** per richiedere all'utente di accedere con il proprio account aziendale o dell'istituto di istruzione anziché immettere un PIN per accedere all'app. Se questa opzione è impostata su **Sì**, ha la priorità sulle richieste di PIN o ID tocco.  | No |
| **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted** |  Scegliere **Sì** per impedire l'esecuzione dell'app nei dispositivi jailbroken o rooted. L'utente potrà comunque usare le app per le attività personali, ma dovrà usare un dispositivo diverso per accedere ai dati aziendali o dell'istituto di istruzione nell'app. | sì |
| **Controlla di nuovo i requisiti di accesso dopo (minuti)** | Configurare le seguenti impostazioni: <ul><li>**Timeout**: specifica il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app. Valore predefinito: **30** minuti.</li><li>**Periodo di prova offline:** se il dispositivo è offline, specifica il periodo di tempo (in minuti) che deve trascorrere prima che vengano controllati di nuovo i requisiti di accesso per l'app. Valore predefinito: **720** minuti (12 ore).</li></ul>| Timeout: 30 <br><br> Offline: 720 |
| **Intervallo offline (giorni) prima della cancellazione dei dati dell'app** | I dati aziendali o dell'istituto di istruzione in questa app possono essere cancellati se un dispositivo è rimasto offline per un periodo più lungo di un determinato intervallo. Specificare il numero di giorni per cui un dispositivo può rimanere offline prima che i dati aziendali o dell'istituto di istruzione vengano rimossi dal dispositivo. <br><br> | 90 giorni |

##  <a name="add-ins-for-outlook-app"></a>Componenti aggiuntivi per l'app Outlook

Outlook ha introdotto recentemente componenti aggiuntivi in Outlook per iOS che consentono di integrare app comuni con il client di posta elettronica. I componenti aggiuntivi per Outlook sono disponibili per Outlook per iOS, sul Web e per Windows e Mac. Poiché i componenti aggiuntivi vengono gestiti tramite Microsoft Exchange, gli utenti saranno in grado di condividere i dati e i messaggi in Outlook e le applicazioni aggiuntive non gestite a meno che i componenti aggiuntivi non vengano disattivati per l'utente dall'istanza di Exchange.

Per impedire agli utenti finali di accedere e installare componenti aggiuntivi di Outlook con effetto su tutti i client Outlook, assicurarsi di applicare le seguenti modifiche ai ruoli nell'interfaccia di amministrazione di Exchange:

- Per impedire agli utenti di installare componenti aggiuntivi di Office Store, rimuovere il ruolo di Marketplace personale.
- Per impedire agli utenti il sideload di componenti aggiuntivi, rimuovere il ruolo di app personalizzate.
- Per impedire agli utenti di installare tutti i componenti aggiuntivi, rimuovere i ruoli di app personalizzate e di Marketplace personale.

Queste istruzioni si applicano a Office 365, Exchange 2016, Exchange 2013 in Outlook sul Web, per dispositivi mobili, Windows e Mac.

- Altre informazioni sui [componenti aggiuntivi per Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Altre informazioni su [come specificare gli amministratori e gli utenti che possono installare e gestire i componenti aggiuntivi per l'app Outlook](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).



<!--HONumber=Feb17_HO2-->


