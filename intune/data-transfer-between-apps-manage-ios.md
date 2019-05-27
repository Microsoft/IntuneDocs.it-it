---
title: Gestire il trasferimento di dati tra app iOS
titleSuffix: Microsoft Intune
description: Informazioni su come usare i criteri di gestione delle app per dispositivi mobili in Microsoft Intune per gestire i trasferimenti di dati tra app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dffdf67597ccb7a1719b2b769a79a6a5f365198c
ms.sourcegitcommit: 5fec35341d83b16023a92fc4b2b3e9237fc6c9ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65853898"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Come gestire il trasferimento di dati tra app iOS in Microsoft Intune

Per facilitare la protezione dei dati aziendali, limitare i trasferimenti di file alle sole app gestite personalmente. È possibile gestire le app iOS nei modi seguenti:

-   Evitare perdite di dati aziendali tramite la configurazione di criteri di protezione delle app, dette app **gestite da criteri**. Vedere [tutte le app gestite da Intune che è possibile gestire con i criteri di protezione delle app](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   Distribuire e gestire le app tramite il **canale MDM**, che richiede che i dispositivi vengano registrati in una soluzione di gestione dei dispositivi mobili (MDM, Mobile Device Management). Le app distribuite possono essere app **gestite da criteri** o altre app gestite.

La funzionalità di **gestione Open In** per i dispositivi iOS consente i trasferimenti di file solo tra le app distribuite tramite il **canale MDM**. Impostare restrizioni per la *gestione Apri in* nelle impostazioni di configurazione e quindi distribuirle tramite la soluzione MDM.  Le restrizioni impostate vengono applicate quando l'utente installa l'app distribuita.

##  <a name="use-app-protection-with-ios-apps"></a>Usare la protezione delle app con app iOS
Usare i criteri di protezione delle app con la funzionalità di **gestione Apri in** di iOS per proteggere i dati aziendali nei modi seguenti:

-   **Dispositivi di proprietà dei dipendenti non gestiti da soluzioni MDM:** è possibile impostare i criteri di protezione delle app su **Consenti all'app di trasferire i dati ad altre app: App gestite da criteri**. Il comportamento *Apri in* di un'app gestita da criteri propone come opzioni per la condivisione solo altre app gestite da criteri. Se un utente tenta di inviare un file protetto da criteri come allegato da OneDrive nell'app di posta nativa, il file risulta illeggibile.

-   **Dispositivi gestiti da Intune:** per i dispositivi registrati in Intune, il trasferimento dei dati tra app con criteri di protezione delle app e altre app iOS gestite distribuite con Intune è consentito automaticamente. Per specificare come consentire il trasferimento di dati ad altre app, abilitare l'impostazione **Consenti all'app di trasferire i dati ad altre app** e quindi scegliere un livello di condivisione. Per specificare come consentire a un'app di ricevere dati da altre app, abilitare l'impostazione **Consenti all'app di ricevere i dati da altre app** e quindi scegliere un livello di ricezione. È possibile usare la funzionalità di **gestione Open In** per controllare il trasferimento dei dati tra le app distribuite tramite Intune. Per altre informazioni su ricezione e condivisione dei dati delle app, vedere [Impostazioni di rilocazione dei dati](app-protection-policy-settings-ios.md#data-protection).   

-   **Dispositivi gestiti da una soluzione MDM di terze parti:** è possibile limitare il trasferimento dei dati solo alle app gestite con la funzionalità di **gestione Open In** di iOS.
Per assicurarsi che le app distribuite tramite la soluzione MDM di terze parti siano anche associate ai criteri di protezione delle app di Intune, configurare l'impostazione UPN dell'utente come descritto nella sezione seguente, [Configurare l'impostazione UPN dell'utente](#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Quando le app vengono distribuite con l'impostazione UPN dell'utente, all'app si applicano i criteri di protezione delle app nel momento in cui l'utente esegue l'accesso con il proprio account aziendale.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurare l'impostazione UPN dell'utente per Microsoft Intune o soluzioni EMM di terze parti
La configurazione dell'impostazione UPN dell'utente è **obbligatoria** per i dispositivi gestiti da Intune o da una soluzione EMM di terze parti. La configurazione UPN funziona con i criteri di protezione delle app distribuiti da Intune. La procedura seguente illustra il flusso generale per la configurazione dell'impostazione UPN, nonché l'esperienza utente risultante:

1.  Nel [portale di Azure](https://portal.azure.com) [creare e assegnare un criterio di protezione delle app](app-protection-policies.md) per iOS. Configurare le impostazioni dei criteri secondo i requisiti aziendali e selezionare le app iOS che devono rispettare questi criteri.

2.  Distribuire le app e il profilo di posta elettronica che si vuole gestire tramite Intune o la soluzione MDM di terze parti usando la procedura generalizzata descritta di seguito. Questa esperienza è illustrata anche dall'*esempio 1*.

3.  Distribuire l'app con le impostazioni di configurazione seguenti nel dispositivo gestito:

      **key** = IntuneMAMUPN, **value** = <username@company.com>

      Esempio: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]
      
       > [!NOTE]
       > In Intune i criteri di configurazione dell'app devono essere per il tipo di registrazione "Dispositivi gestiti".
       > L'app deve inoltre essere installata dal Portale aziendale Intune se è impostata come disponibile oppure deve essere eseguito il push come richiesto nel dispositivo. 

4.  Distribuire i criteri di **gestione Apri in** tramite Intune o il provider MDM di terze parti in uso nei dispositivi registrati.


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


### <a name="example-2-end-user-experience"></a>Esempio 2: Esperienza dell'utente finale

1.  Un utente installa l'app Microsoft Word in un dispositivo.

2.  L'utente avvia l'app di posta elettronica nativa gestita per accedere alla posta elettronica.

3.  L'utente prova ad aprire un documento dalla posta nativa in Microsoft Word.

4.  Quando viene avviata l'app Word, all'utente viene richiesto di eseguire l'accesso con l'account aziendale. L'account immesso dall'utente deve corrispondere all'account specificato nelle impostazioni di configurazione dell'app Microsoft Word.

    > [!NOTE]
    > L'utente può aggiungere e usare con Word gli account personali. I criteri di protezione delle app non si applicano quando l'utente usa Word al di fuori di un contesto aziendale. 

5.  Dopo l'accesso, all'app Word si applicano le impostazioni dei criteri di protezione delle app.

6.  Il trasferimento dei dati ha esito positivo e il documento viene contrassegnato con un'identità aziendale nell'app.  I dati vengono trattati all'interno di un contesto aziendale e le impostazioni dei criteri vengono applicate. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Convalidare l'impostazione UPN dell'utente per soluzioni EMM di terze parti

Dopo aver configurato l'impostazione UPN dell'utente, verificare se l'app iOS può ricevere i criteri di protezione delle app di Intune e conformarsi a tali criteri.

È facile testare, ad esempio, l'impostazione del criterio **Require app PIN** (Richiedi PIN app). Se l'impostazione del criterio corrisponde a **Sì**, per accedere ai dati aziendali l'utente deve impostare o immettere un PIN quando richiesto.

Prima di tutto, [creare e assegnare criteri di protezione delle app](app-protection-policies.md) all'app iOS. Per altre informazioni su come testare i criteri di protezione delle app, vedere [Convalidare i criteri di protezione delle app](app-protection-policies-validate.md).


### <a name="see-also"></a>Vedere anche
[Che cos'è un criterio di protezione delle app di Intune?](app-protection-policy.md)
