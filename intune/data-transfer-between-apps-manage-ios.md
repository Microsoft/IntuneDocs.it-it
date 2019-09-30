---
title: Gestire il trasferimento di dati tra app iOS
titleSuffix: Microsoft Intune
description: Informazioni su come usare i criteri di gestione delle app per dispositivi mobili in Microsoft Intune per gestire i trasferimenti di dati tra app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eaf381d6d7b6bf8e9508eac4ccfc5431aa008658
ms.sourcegitcommit: 89a973bbfa1702b2d275af6814874e4305bdcb77
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71140699"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Come gestire il trasferimento di dati tra app iOS in Microsoft Intune

Per facilitare la protezione dei dati aziendali, limitare i trasferimenti di file alle sole app gestite personalmente. È possibile gestire le app iOS nei modi seguenti:

- Proteggere i dati dell'organizzazione per gli account aziendali o dell'istituto di istruzione configurando un criterio di protezione delle app per le app che vengono denominate *app gestite da criteri*  Vedere [tutte le app gestite da Intune che è possibile gestire con i criteri di protezione delle app](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Distribuire e gestire le app tramite la gestione dei dispositivi iOS, per la quale è necessario che i dispositivi siano registrati in una soluzione di gestione dei dispositivi mobili. Le app distribuite possono essere *app gestite da criteri* o altre app iOS gestite.

La funzionalità di **gestione Apri in** per i dispositivi iOS registrati consente i trasferimenti di file solo tra app iOS gestite. Impostare restrizioni per la *gestione Apri in* nelle impostazioni di configurazione, quindi distribuirle tramite la soluzione MDM.  Le restrizioni impostate vengono applicate quando l'utente installa l'app distribuita.

## <a name="use-app-protection-with-ios-apps"></a>Usare la protezione delle app con app iOS
Usare i criteri di protezione delle app con la funzionalità di **gestione Apri in** di iOS per proteggere i dati aziendali nei modi seguenti:

- **Dispositivi non gestiti da soluzioni MDM:** è possibile impostare i criteri di protezione delle app per controllare la condivisione di dati con altre applicazioni tramite *Apri in* o *Condividi estensioni*.  A tale scopo, configurare l'impostazione **Invia i dati dell'organizzazione ad altre app** sul valore **App gestite da criteri con filtro basato su Apri in/Condividi**.  Il comportamento di *Apri in/Condividi* nell'*app gestita da criteri* propone come opzioni per la condivisione solo altre*app gestite da criteri*. 

- **Dispositivi gestiti da soluzioni MDM**: per i dispositivi registrati in Intune o soluzioni MDM di terze parti, la condivisione dei dati tra app con criteri di protezione delle app e altre app iOS gestite distribuite tramite MDM è controllata dai criteri di protezione delle app di Intune e dalla funzionalità iOS di **gestione Open In**. Per assicurarsi che le app distribuite tramite una soluzione MDM siano anche associate ai criteri di protezione delle app di Intune, configurare l'impostazione UPN dell'utente come descritto nella sezione seguente, [Configurare l'impostazione UPN dell'utente](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Per specificare come consentire il trasferimento di dati ad altre app, abilitare **Invia i dati dell'organizzazione ad altre app** e quindi scegliere il livello di condivisione preferito. Per specificare come consentire a un'app di ricevere dati da altre app, abilitare **Ricevi dati da altre app** e quindi scegliere il livello di ricezione dei dati preferito. Per altre informazioni su ricezione e condivisione dei dati delle app, vedere [Impostazioni di rilocazione dei dati](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurare l'impostazione UPN dell'utente per Microsoft Intune o soluzioni EMM di terze parti
La configurazione dell'impostazione UPN dell'utente è **obbligatoria** per i dispositivi gestiti da Intune o da una soluzione EMM di terze parti per identificare un account utente registrato. La configurazione UPN funziona con i criteri di protezione delle app distribuiti da Intune. La procedura seguente illustra il flusso generale per la configurazione dell'impostazione UPN, nonché l'esperienza utente risultante:

1. Nel [portale di Azure](https://portal.azure.com) [creare e assegnare un criterio di protezione delle app](app-protection-policies.md) per iOS. Configurare le impostazioni dei criteri secondo i requisiti aziendali e selezionare le app iOS che devono rispettare questi criteri.

2. Distribuire le app e il profilo di posta elettronica che si vuole gestire tramite Intune o la soluzione MDM di terze parti usando la procedura generalizzata descritta di seguito. Questa esperienza è illustrata anche dall'*esempio 1*.

3. Distribuire l'app con le impostazioni di configurazione seguenti nel dispositivo gestito:

      **key** = IntuneMAMUPN, **value** = <username@company.com>

      Esempio: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > In Intune il tipo di registrazione dei criteri di Configurazione app deve essere impostato su **Dispositivi gestiti**.
     > L'app deve anche essere installata dal Portale aziendale Intune se è impostata come disponibile oppure è necessario eseguirne il push come richiesto nel dispositivo. 

4. Distribuire i criteri di **gestione Apri in** tramite Intune o il provider MDM di terze parti in uso nei dispositivi registrati.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Esempio 1: Esperienza di amministrazione in Intune o nella console MDM di terze parti

1. Passare alla console di amministrazione di Intune o del provider MDM di terze parti. Passare alla sezione della console in cui si distribuiscono le impostazioni di configurazione dell'applicazione ai dispositivi iOS registrati.

2. Immettere l'impostazione seguente nella sezione Configurazione dell'applicazione:

   **key** = IntuneMAMUPN, **value** = <username@company.com>

   La sintassi esatta della coppia chiave/valore può variare a seconda del provider MDM di terze parti. La tabella seguente visualizza alcuni esempi di provider MDM di terze parti e i valori esatti da immettere per la coppia chiave/valore.

   |Provider MDM di terze parti| Chiave Configuration | Tipo valore | Valore di configurazione|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Stringa | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Stringa | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Stringa | ${userUPN} **o** ${userEmailAddress} |
   |Citrix Endpoint Management | IntuneMAMUPN | Stringa | ${user.userprincipalname} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Stringa | %upn% |

> [!NOTE]  
> Per l'app Outlook in iOS, se si distribuiscono criteri di Configurazione app con l'opzione "Usa progettazione configurazione", la chiave di configurazione IntuneMAMUPN viene configurata automaticamente in background per i criteri. Per altri dettagli, vedere la sezione delle domande frequenti in [New Outlook for iOS and Android App Configuration Policy Experience – General App Configuration](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481) (Nuova esperienza per i criteri di configurazione dell'app Outlook per iOS e Android). 


### <a name="example-2-end-user-experience"></a>Esempio 2: Esperienza dell'utente finale

*Condivisione da* un'*app gestita da criteri* in altre applicazioni con condivisione del sistema operativo

1. Un utente apre l'app Microsoft OneDrive in un dispositivo iOS registrato e accede all'account aziendale.  L'account immesso dall'utente deve corrispondere all'UPN dell'account specificato nelle impostazioni di configurazione dell'app per l'app Microsoft OneDrive.

2. Dopo l'accesso, le impostazioni dell'APP configurate dall'amministratore vengono applicate all'account utente in Microsoft OneDrive.  Viene anche configurata l'impostazione **Invia i dati dell'organizzazione ad altre app** sul valore **App gestita da criteri con condivisione del sistema operativo**.

3. L'utente visualizza in anteprima un file di lavoro e tenta di eseguire la condivisione in un'app iOS gestita usando Apri in.  

4. Il trasferimento dei dati ha esito positivo e i dati sono ora protetti dalla **gestione Apri in** nell'app iOS gestita.  L'APP Intune non viene applicata alle applicazioni che non sono *app gestite da criteri*.

*Condivisione da un'* app iOS gestita *in un'* app gestita da criteri *con dati dell'organizzazione in ingresso*

1. Un utente apre la posta elettronica nativa in un dispositivo iOS registrato usando un profilo di posta elettronica gestito.  

1. L'utente apre un documento di lavoro allegato proveniente dalla posta elettronica nativa in Microsoft Word.

1. Quando viene avviata l'app Word, si verifica una delle due esperienze seguenti:
   1. I dati vengono protetti dall'APP Intune nei casi seguenti:
      - L'utente ha eseguito l'accesso usando l'account aziendale che corrisponde all'UPN dell'account specificato nelle impostazioni di configurazione per l'app Microsoft Word. 
      - Le impostazioni dell'APP configurate dall'amministratore vengono applicate all'account utente in Microsoft Word.  Viene anche configurata l'impostazione **Ricevi dati da altre app** sul valore **Tutte le app con dati dell'organizzazione in ingresso**.
      - Il trasferimento dei dati ha esito positivo e il documento viene contrassegnato con l'identità aziendale nell'app.  L'APP Intune protegge le azioni dell'utente per il documento.
   1. I dati **non** vengono protetti dall'APP Intune nei casi seguenti:
      - L'utente **non** ha eseguito l'accesso all'account aziendale.
      - Le impostazioni configurate dall'amministratore **non** vengono applicate a Microsoft Word perché l'utente non ha eseguito l'accesso.
      - Il trasferimento dei dati ha esito positivo e il documento **non** viene contrassegnato con l'identità aziendale nell'app.  L'APP Intune **non** protegge le azioni dell'utente per il documento perché la protezione non è attiva.

    > [!NOTE]
    > L'utente può aggiungere e usare con Word gli account personali. I criteri di protezione delle app non si applicano quando l'utente usa Word al di fuori di un contesto aziendale. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Convalidare l'impostazione UPN dell'utente per soluzioni EMM di terze parti

Dopo aver configurato l'impostazione UPN dell'utente, verificare se l'app iOS può ricevere i criteri di protezione delle app di Intune e conformarsi a tali criteri.

È facile testare, ad esempio, l'impostazione del criterio **Require app PIN** (Richiedi PIN app). Se l'impostazione del criterio corrisponde a **Rendi obbligatorio**, per accedere ai dati aziendali l'utente deve prima impostare o immettere un PIN quando richiesto.

Prima di tutto, [creare e assegnare criteri di protezione delle app](app-protection-policies.md) all'app iOS. Per altre informazioni su come testare i criteri di protezione delle app, vedere [Convalidare i criteri di protezione delle app](app-protection-policies-validate.md).


## <a name="see-also"></a>Vedere anche
[Che cos'è un criterio di protezione delle app di Intune?](app-protection-policy.md)
