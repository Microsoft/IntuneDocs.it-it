---
title: Guida al testing di Microsoft Intune App SDK per sviluppatori di Android
description: La Guida al testing di Microsoft Intune App SDK per Android è utile per testare le app Android gestite da Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa6b07c77b0d92ceb7bdc960d8c2fd754c277499
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713241"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Guida al testing di Microsoft Intune App SDK per sviluppatori di Android

La Guida al testing di Microsoft Intune App SDK per Android è progettata per agevolare le operazioni di test per le app Android gestite da Intune.  

## <a name="prerequisite-test-accounts"></a>Account di test prerequisiti
È possibile creare nuovi account con e senza dati pre-generati. Per creare un nuovo account:
1. Passare al sito [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant). 
2. [Configurare Intune](https://docs.microsoft.com/intune/setup-steps) per abilitare la gestione di dispositivi mobili (MDM).
3. [Creare gli utenti](https://docs.microsoft.com/intune/users-add).
4. [Creare i gruppi](https://docs.microsoft.com/intune/groups-add).
5. [Assegnare le licenze](https://docs.microsoft.com/intune/licenses-assign) appropriate per i test.


## <a name="azure-portal-policy-configuration"></a>Configurazione dei criteri del portale di Azure
[Creare e assegnare criteri di protezione delle app](https://docs.microsoft.com/intune/app-protection-policies) nel [pannello Intune del portale di Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). I [criteri di configurazione delle app](https://docs.microsoft.com/intune/app-configuration-policies-overview) possono anche essere creati e assegnati nel pannello Intune.

> [!NOTE]
> Se l'app non è elencata nel portale di Azure, è possibile impostarla come destinazione con un criterio selezionando l'opzione **Altre app** e specificando il nome del pacchetto nella casella di testo.

> [!IMPORTANT]
> Per poter applicare i criteri di configurazione delle app, l'utente da registrare deve essere impostato come destinazione per i [criteri di protezione delle app di Intune](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Test case

I test case seguenti illustrano le procedure di configurazione e conferma. Usare queste linee guida per risolvere i problemi relativi alle app Android gestite da Intune.

### <a name="required-pin-and-corporate-credentials"></a>PIN obbligatorio e credenziali aziendali

È possibile richiedere un PIN per accedere alle risorse aziendali. È anche possibile imporre l'autenticazione aziendale prima che gli utenti possano usare le app gestite. Seguire questa procedura per impostare questi requisiti:

1. Impostare **Richiedi PIN per l'accesso** e **Richiedi credenziali aziendali per l'accesso** su **Sì**. Per altre informazioni, vedere [Impostazioni dei criteri di protezione delle app di Android in Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Confermare le condizioni seguenti:
    - All'avvio dell'app deve essere visualizzato un prompt per l'input o la configurazione del PIN e/o l'utente di produzione che è stato usato durante la registrazione nel portale aziendale.
    - Se non viene visualizzato un prompt di accesso valido, è possibile che il manifesto Android non sia configurato correttamente, in modo specifico i valori per l'integrazione di ADAL (SkipBroker ClientID e Authority).
    - Se non viene visualizzato alcun prompt la causa potrebbe essere un valore `MAMActivity` integrato in modo non corretto. Per altre informazioni su `MAMActivity`, vedere [Manuale dello sviluppatore di Microsoft Intune App SDK per Android](app-sdk-android.md).

> [!NOTE] 
> Se il test precedente non funziona, è probabile che abbiano esito negativo anche i test seguenti. Controllare l'integrazione di [SDK](app-sdk-android.md##sdk-integration) e [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Limitare il trasferimento e la ricezione di dati con altre app
È possibile controllare il trasferimento dei dati tra le applicazioni gestite aziendali come indicato di seguito:

1. Impostare **Consenti all'app di trasferire i dati ad altre app** su **App gestite da criteri**.
2. Impostare **Consenti all'app di ricevere i dati da altre app** su **Tutte le app**. Questi criteri avranno effetto sull'uso di finalità e provider di contenuti.
3. Confermare le condizioni seguenti:
    - L'apertura da un'app non gestita nell'app funziona correttamente.
    - È consentita la condivisione del contenuto tra app gestite.
    - La condivisione da app gestite ad app non gestite (ad esempio Chrome) è bloccata.

### <a name="restrict-cut-copy-and-paste"></a>Limitare le operazioni taglia, copia e incolla
È possibile limitare gli Appunti di sistema per le applicazioni gestite nel modo seguente:

1. Impostare **Limita le operazioni taglia, copia e incolla con le altre app** su **App gestite da criteri con Incolla in**.
2. Confermare le condizioni seguenti:
    - La copia di testo dalla propria app in un'app gestita o non gestita (ad esempio, Messaggi) ha esito negativo.

### <a name="prevent-save-as"></a>Impedire **Salva con nome**
È possibile controllare la funzionalità **Salva con nome** come indicato di seguito:

1. Se l'app richiede [controlli 'Salva con nome' integrati](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), impostare **Impedisci 'Salva con nome'** su **Sì**.
2. Confermare le condizioni seguenti:
    - Il comando Salva è limitato solo alle posizioni gestite appropriate.

### <a name="file-encryption"></a>Crittografia file
È possibile crittografare i dati nel dispositivo come indicato di seguito:

1. Impostare **Crittografa dati app** su **Sì**.
2. Confermare le condizioni seguenti:
    - Nessun effetto sul comportamento normale dell'applicazione.

### <a name="prevent-android-backups"></a>Impedire backup in Android
È possibile controllare i backup dell'app come indicato di seguito:

1. Se sono state impostate [limitazioni per il backup integrato](app-sdk-android.md#protecting-backup-data), impostare **Impedisci backup in Android** su **Sì**.
2. Confermare le condizioni seguenti:
    - I backup sono limitati.

### <a name="unenrollment"></a>Annullamento della registrazione
È possibile cancellare posta elettronica e documenti aziendali dalle app gestite e i dati personali vengono decrittografati quando non sono più amministrati, come indicato di seguito:

1. Dal portale di Azure [eseguire una cancellazione](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Se l'app non è registrata per qualsiasi gestore di cancellazione verificare le condizioni seguenti:
    - Si verifica una cancellazione completa dell'app.
3. Se l'app è registrata per `WIPE_USER_DATA` o `WIPE_USER_AUXILARY_DATA`, verificare le condizioni seguenti:
    - Il contenuto gestito viene rimosso dall'app. Per altre informazioni, vedere [Manuale dello sviluppatore di Intune App SDK per Android - Cancellazione selettiva](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Identità multiple
L'integrazione del [supporto di più identità](app-sdk-android.md#multi-identity-optional) è una modifica ad alto rischio che deve essere testata accuratamente. I problemi più comuni saranno causati dall'impostazione non corretta dell'identità (a livello di contesto o di minaccia) e anche dei file di rilevamento (`MAMFileProtectionManager`).

Come minimo, devono essere riconvalidati gli scenari seguenti per le identità multiple:

- I criteri per **Salva con nome** funzionano correttamente per le identità gestite.
- Le limitazioni per Copia/Incolla vengono applicate correttamente nel passaggio dal contesto gestito a quello personale.
- Vengono crittografati solo i dati appartenenti all'identità gestita e i file personali non vengono modificati.
- La cancellazione selettiva in fase di l'annullamento della registrazione rimuove solo i dati dell'identità gestita.
- All'utente finale viene richiesto di eseguire l'avvio condizionale quando passa da un account non gestito a un account gestito (solo la prima volta).

### <a name="app-configuration-optional"></a>Configurazione delle app (facoltativa)
È possibile configurare il comportamento delle app gestite nel modo seguente:

1. Se l'app utilizza eventuali impostazioni di configurazione delle app, è necessario verificare che l'app gestisca correttamente tutti i valori che possono essere impostati dall'amministratore. I [criteri di configurazione delle app](https://docs.microsoft.com/intune/app-configuration-policies-overview) possono essere creati e assegnati tramite Intune.

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere un'app line-of-business per Android a Microsoft Intune](lob-apps-android.md).
