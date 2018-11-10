---
title: Gestire il trasferimento di dati tra app iOS
titlesuffix: Microsoft Intune
description: Informazioni su come usare i criteri di gestione delle app per dispositivi mobili in Microsoft Intune per gestire i trasferimenti di dati tra app.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 491d2884f73d9178f54b6b2861bfe6f248c41c63
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236561"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Come gestire il trasferimento di dati tra app iOS in Microsoft Intune
## <a name="manage-ios-apps"></a>Gestire le app iOS
La protezione dei dati aziendali prevede anche che ci si assicuri che i trasferimenti di file siano limitati alle app gestite dall'utente.  È possibile gestire le app iOS nei modi seguenti:

-   Evitare perdite di dati aziendali tramite la configurazione di criteri di protezione delle app, a cui si farà riferimento con il termine app **gestite da criteri**. Vedere [tutte le app gestite da Intune che è possibile gestire con i criteri di protezione delle app](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   È anche possibile distribuire e gestire le app tramite il **canale MDM**.  Ciò richiede che i dispositivi vengono registrati nella soluzione MDM. Possono essere app **gestite da criteri** o altre app gestite.

La funzionalità di **gestione Open In** per i dispositivi iOS consente i trasferimenti di file solo tra le app distribuite tramite il **canale MDM**. Le restrizioni della gestione Open In sono definite nelle impostazioni di configurazione e distribuite tramite la soluzione MDM.  Quando l'utente installa l'app distribuita, vengono applicate le restrizioni impostate.

##  <a name="using-app-protection-with-ios-apps"></a>Uso della protezione delle app con app per iOS
I criteri di protezione delle app possono essere usati con la funzionalità di **gestione Apri in** di iOS per proteggere i dati aziendali nei modi seguenti:

-   **Dispositivi di proprietà dei dipendenti non gestiti da soluzioni MDM:** è possibile impostare i criteri di protezione delle app su **Consenti all'app di trasferire i dati ad altre app: App gestite da criteri**. Il comportamento Apri in un'app gestita da criteri presenterà solo altre app gestite da criteri come opzione per la condivisione. Se un utente tenta di inviare un file protetto da criteri come allegato dalla posta nativa di OneDrive, il file risulterà illeggibile.

-   **Dispositivi gestiti da Intune:** per i dispositivi registrati in Intune, il trasferimento dei dati tra app con criteri di protezione delle app e altre app iOS gestite distribuite tramite Intune è consentito automaticamente. Per specificare come consentire il trasferimento di dati ad altre app, abilitare l'impostazione **Consenti all'app di trasferire dati ad altre app** e scegliere un livello di condivisione. Per specificare come consentire a un'app di ricevere dati da altre app, abilitare l'impostazione **Consenti all'app di ricevere i dati da altre app** e scegliere un livello di ricezione. È possibile usare la funzionalità di **gestione Open In** per controllare il trasferimento dei dati tra le app distribuite tramite Intune. Per altre informazioni su ricezione e condivisione dei dati delle app, vedere [Impostazioni di rilocazione dei dati](app-protection-policy-settings-ios.md#data-relocation-settings).   

-   **Dispositivi gestiti da una soluzione MDM di terze parti:** è possibile limitare il trasferimento dei dati solo alle app gestite usando la funzionalità di **gestione Open In** di iOS.
Per assicurarsi che le app distribuite mediante la soluzione MDM di terze parti siano associate anche ai criteri di protezione delle app configurati in Intune, è necessario configurare l'impostazione UPN dell'utente come descritto nella procedura dettagliata [Configurare l'impostazione UPN dell'utente](#configure-user-upn-setting-for-third-party-emm).  Quando le app vengono distribuite con l'impostazione UPN dell'utente, all'app verranno applicati i criteri di protezione delle app nel momento in cui l'utente finale esegue l'accesso con il proprio account aziendale.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurare l'impostazione UPN dell'utente per Microsoft Intune o soluzioni EMM di terze parti
La configurazione dell'impostazione UPN dell'utente è **obbligatoria** per i dispositivi gestiti da Intune o da una soluzione EMM di terze parti. La procedura descritta di seguito illustra il flusso generale per configurare l'impostazione UPN e l'esperienza dell'utente finale risultante:

1.  Nel [portale di Azure](https://portal.azure.com) [creare e assegnare un criterio di protezione delle app](app-protection-policies.md) per iOS. Configurare le impostazioni dei criteri secondo i requisiti aziendali e selezionare le app iOS che devono rispettare questi criteri.

2.  Distribuire le app e il profilo di posta elettronica che si vuole gestire tramite Intune o la soluzione MDM di terze parti usando la procedura generalizzata descritta di seguito. Questa esperienza è illustrata anche dall'esempio 1.

3.  Distribuire l'app con le impostazioni di configurazione seguenti:

      **key** = IntuneMAMUPN, **value** = <username@company.com>

      Esempio: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  Distribuire i criteri di **gestione Apri in** tramite Intune o il provider MDM di terze parti in uso nei dispositivi registrati.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Esempio 1: esperienza di amministrazione in Intune o nella console MDM di terze parti

1. Passare alla console di amministrazione di Intune o del provider MDM di terze parti. Passare alla sezione della console in cui si distribuiscono le impostazioni di configurazione dell'applicazione ai dispositivi iOS registrati.

2. Immettere l'impostazione seguente nella sezione Configurazione dell'applicazione:

   **key** = IntuneMAMUPN, **value** = <username@company.com>

   La sintassi esatta della coppia chiave/valore può variare a seconda del provider MDM di terze parti. La tabella seguente visualizza alcuni esempi di provider MDM di terze parti e i valori esatti che devono essere immessi per la coppia chiave/valore.

|Provider MDM di terze parti| Chiave Configuration | Tipo valore | Valore di configurazione|
| ------- | ---- | ---- | ---- |
|Microsoft Intune| IntuneMAMUPN | Stringa | {{UserPrincipalName}}|
|VMware AirWatch| IntuneMAMUPN | Stringa | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | Stringa | ${userUPN} **o** ${userEmailAddress} |
|ManageEngine Mobile Device Manager | IntuneMAMUPN | Stringa | %upn% |


### <a name="example-2-end-user-experience"></a>Esempio 2: Esperienza dell'utente finale

1.  L'utente finale installa l'app di Microsoft Word nel dispositivo.

2.  L'utente finale avvia l'app di posta elettronica nativa gestita per accedere alla posta elettronica.

3.  L'utente finale prova ad aprire un documento dalla posta nativa in Microsoft Word.

4.  Quando viene avviata l'app di Word, all'utente finale viene richiesto di eseguire l'accesso con l'account aziendale.  L'account aziendale immesso dall'utente finale, quando richiesto, deve corrispondere all'account specificato nelle impostazioni di configurazione dell'app di Microsoft Word.

    > [!NOTE]
    > L'utente finale può aggiungere altri account personali a Word per svolgere lavoro personale senza essere interessato dai criteri di protezione delle app quando usa l'app di Word in un contesto personale.

5.  Se l'accesso riesce, le impostazioni dei criteri di protezione delle app vengono applicate all'app Word.

6.  Il trasferimento dei dati ha esito positivo e il documento viene contrassegnato con un'identità aziendale nell'app. I dati, poi, vengono trattati in un contesto aziendale e le impostazioni dei criteri vengono applicate di conseguenza.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Convalidare l'impostazione UPN dell'utente per soluzioni EMM di terze parti

Dopo aver configurato l'impostazione UPN dell'utente, è necessario verificare se l'app iOS può ricevere i criteri di protezione delle app di Intune e conformarsi a tali criteri.

Ad esempio, è facile verificare visivamente l'impostazione del criterio **Richiedi PIN semplice per l'accesso** in un dispositivo. Se il criterio è impostato su **Sì**, quando l'utente cerca di accedere ai dati aziendali un prompt richiede di impostare o immettere un PIN.

Prima di tutto, [creare e assegnare criteri di protezione delle app](app-protection-policies.md) all'app iOS. Per altre informazioni su come testare i criteri di protezione delle app, vedere [Convalidare i criteri di protezione delle app](app-protection-policies-validate.md).


### <a name="see-also"></a>Vedere anche
[Che cos'è un criterio di protezione delle app di Intune?](app-protection-policy.md)
