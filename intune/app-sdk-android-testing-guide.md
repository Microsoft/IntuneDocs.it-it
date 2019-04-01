---
title: Guida al testing di Microsoft Intune App SDK per sviluppatori di Android
description: Microsoft Intune App SDK per Android Guida test consente di testare l'app Android gestiti da Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072471"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Guida al testing di Microsoft Intune App SDK per sviluppatori di Android

Microsoft Intune App SDK per Android Guida test è progettato per consentire di testare l'app Android gestiti da Intune.  

## <a name="prerequisite-test-accounts"></a>Account di test dei prerequisiti
È possibile creare nuovi account con e senza dati pre-generati. Per creare un nuovo account:
1. Passare il [Demos Microsoft](https://demos.microsoft.com/environments/create/tenant) sito. 
2. [Configurare Intune](https://docs.microsoft.com/intune/setup-steps) per abilitare la gestione dei dispositivi mobili (MDM).
3. [Creare utenti](https://docs.microsoft.com/intune/users-add).
4. [Creare i gruppi](https://docs.microsoft.com/intune/groups-add).
5. [Assegnare le licenze](https://docs.microsoft.com/intune/licenses-assign) come appropriato per il test.


## <a name="azure-portal-policy-configuration"></a>Configurazione dei criteri del portale Azure
[Creare e assegnare criteri di protezione delle app](https://docs.microsoft.com/intune/app-protection-policies) nella [pannello Intune del portale di Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). I [criteri di configurazione app](https://docs.microsoft.com/intune/app-configuration-policies-overview) può anche essere creato e assegnato nel Pannello di Intune.

> [!NOTE]
> Se l'app non è elencato nel portale di Azure, è possibile definire la destinazione con un criterio selezionando il **altre app** opzione e fornendo il nome del pacchetto nella casella di testo.

> [!IMPORTANT]
> Per i criteri di configurazione da applicare, l'utente della registrazione deve essere impostata come destinazione un' [criteri di protezione delle app Intune](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Test case

I test case seguenti illustrano le procedure di configurazione e la conferma. Utilizzare questo materiale sussidiario per risolvere i problemi di app Android gestita da Intune.

### <a name="required-pin-and-corporate-credentials"></a>PIN obbligatorio e le credenziali aziendali

È possibile richiedere un pin per accedere alle risorse aziendali. Inoltre, è possibile imporre l'autenticazione azienda prima che gli utenti possono usare le app gestite. Utilizzare la procedura seguente per impostare questi requisiti:

1. Configurare **Richiedi PIN per l'accesso** e **Richiedi credenziali aziendali per l'accesso** al **Sì**. Per altre informazioni, vedere [Impostazioni dei criteri di protezione delle app di Android in Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Confermare le condizioni seguenti:
    - Avvio dell'app deve presentare una richiesta di input/configurazione del PIN e/o l'utente di produzione che è stato usato durante la registrazione con l'App portale aziendale.
    - Errore di presentare una richiesta di accesso valida potrebbe essere a causa di un manifesto di android non configurato correttamente, in modo specifico i valori per l'integrazione di ADAL (SkipBroker ClientID e Authority).
    - Errore nella presentazione alcuna richiesta potrebbe essere dovuto a un prodotto in modo non corretto `MAMActivity` valore. Per altre informazioni sulle `MAMActivity`, vedere [Microsoft Intune App SDK per la Guida per sviluppatori Android](app-sdk-android.md).

> [!NOTE] 
> Se il test precedente non funziona, il test seguente probabilmente avrà inoltre esito negativo. Revisione [SDK](app-sdk-android.md##sdk-integration) e [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) integrazione.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Limitare il trasferimento e la ricezione di dati con altre App
È possibile controllare il trasferimento dati tra le applicazioni gestite aziendali come indicato di seguito:

1. Impostare **Consenti all'app di trasferire dati ad altre app** al **le app gestite da criteri**.
2. Impostare **Consenti all'app di ricevere i dati da altre app** su **Tutte le app**. Utilizzo di tipi e i provider di contenuti sarà interessata da questi criteri.
3. Confermare le condizioni seguenti:
    - Apertura da un'app non gestita nelle funzioni app correttamente.
    - È consentita la condivisione del contenuto tra App gestite.
    - La condivisione dalle App gestite per le app non gestite (ad esempio Chrome) è bloccata.

### <a name="restrict-cut-copy-and-paste"></a>Limitare le operazioni taglia, copia e incolla
È possibile limitare gli Appunti di sistema per le applicazioni gestite nel modo seguente:

1. Impostare **limita le operazioni Taglia, copia e Incolla con le altre app** al **gestite da criteri con Incolla in**.
2. Confermare le condizioni seguenti:
    - Copiare il testo dalla propria app in un oggetto gestito viene bloccata un'app non gestita (ad esempio, i messaggi).

### <a name="prevent-save-as"></a>Impedire **Salva con nome**
È possibile controllare **Salva con nome** funzionalità come indicato di seguito:

1. Se l'app richiede [integrata 'Salva con nome' controlli](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), impostare **Impedisci 'Salva con nome'** al **Sì**.
2. Confermare le condizioni seguenti:
    - Salva è limitato solo nelle posizioni gestito appropriate.

### <a name="file-encryption"></a>Crittografia file
È possibile crittografare i dati sul dispositivo come indicato di seguito:

1. Impostare **Crittografa dati app** al **Yes**.
2. Confermare le condizioni seguenti:
    - Il comportamento normale dell'applicazione non è compromessa.

### <a name="prevent-android-backups"></a>Impedire backup in Android
È possibile controllare i backup dell'app come indicato di seguito:

1. Se è stata impostata [restrizioni sul backup integrato](app-sdk-android.md#protecting-backup-data), configurare **Impedisci backup in Android** al **Sì**.
2. Confermare le condizioni seguenti:
    - I backup sono limitati.

### <a name="unenrollment"></a>Annullamento della registrazione
È possibile cancellare le app gestite da contenente i documenti e posta elettronica aziendale e i dati personali viene decrittografati quando il servizio non è non è più gestito come indicato di seguito:

1. Dal portale di Azure [eseguire una cancellazione](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Se l'app non effettuare la registrazione per qualsiasi gestore di cancellazione verificare le condizioni seguenti:
    - Si verifica una cancellazione completa dell'app.
3. Se l'app è registrata per `WIPE_USER_DATA` o `WIPE_USER_AUXILARY_DATA`, verificare le condizioni seguenti:
    - Il contenuto gestito viene rimosso dall'app. Per altre informazioni, vedere [Intune App SDK per la Guida per sviluppatori Android - cancellazione selettiva](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Identità multiple
L'integrazione [supporto di più identità](app-sdk-android.md#multi-identity-optional) è una modifica ad alto rischio che deve essere verificato. I problemi più comuni saranno pronti per l'impostazione non corretta dell'identità (contesto rispetto al livello di minaccia) e anche i file di rilevamento (`MAMFileProtectionManager`).

Minima devono essere riconvalidati gli scenari seguenti per identità multiple:

- **Salva con nome** criteri funzionano correttamente per identità gestita.
- Copiare e incollare le restrizioni vengono applicate correttamente dal codice gestito a personale.
- Vengono crittografati solo i dati appartenenti all'identità gestita e i file personali non vengono modificati.
- Durante l'annullamento della registrazione la cancellazione selettiva rimuove solo i dati di identità gestita.
- L'utente finale viene richiesto per il lancio condizionale quando si passa da non gestiti a managed account (solo la prima volta).

### <a name="app-configuration-optional"></a>Configurazione delle App (facoltativa)
È possibile configurare il comportamento di App gestite nel modo seguente:

1. Se l'app utilizza le impostazioni di configurazione di app, è necessario verificare che l'app gestisce correttamente tutti i valori (come amministratore) possono essere impostati. [I criteri di configurazione App](https://docs.microsoft.com/intune/app-configuration-policies-overview) possono essere creati e assegnati usando Intune.

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere un'app line-of-business per Android a Microsoft Intune](lob-apps-android.md).
