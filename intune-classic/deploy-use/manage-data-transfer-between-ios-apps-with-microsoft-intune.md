---
title: Gestire il trasferimento di dati tra app iOS
description: "Usare questo argomento per comprendere come è possibile usare la funzionalità Apri in di iOS e i criteri di gestione delle app mobili per gestire i trasferimenti di dati tra le app."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 05975303bd45764d56f00986aea5aa30399893f9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="manage-data-transfer-between-ios-apps-with-microsoft-intune"></a>Gestire il trasferimento di dati tra app iOS con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="manage-ios-apps"></a>Gestire le app iOS
La protezione dei dati aziendali prevede anche che ci si assicuri che i trasferimenti di file siano limitati alle app gestite dall'utente.  È possibile gestire le app iOS nei modi seguenti:

-   Evitare perdite di dati aziendali tramite la configurazione di criteri di protezione delle app, a cui si farà riferimento con il termine app **gestite da criteri**.

-   È anche possibile distribuire e gestire le app tramite il **canale MDM**.  Ciò richiede che i dispositivi vengono registrati nella soluzione MDM. Possono essere app **gestite da criteri** o altre app gestite.

La funzionalità di **gestione Open-In** per i dispositivi iOS consente i trasferimenti di file solo tra le app distribuite tramite il **canale MDM**. Le restrizioni della gestione Open-In sono definite nelle impostazioni di configurazione e distribuite tramite la soluzione MDM.  Quando l'utente installa l'app distribuita, vengono applicate le restrizioni impostate.

##  <a name="manage-data-transfer-between-ios-apps"></a>Gestire il trasferimento di dati tra app iOS
I criteri di protezione delle app possono essere usati con la funzionalità di **gestione Apri in** di iOS per proteggere i dati aziendali nei modi seguenti:

-   **Dispositivi di proprietà dei dipendenti non gestiti da soluzioni MDM:** è possibile [impostare i criteri di protezione delle app](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) su **Allow app to transfer data to only managed apps** (Consenti all'app di trasferire i dati solo alle app gestite). Quando l'utente finale apre un file protetto in un'app non gestita da criteri, il file è illeggibile.

-   **Dispositivi gestiti da Intune:** per i dispositivi registrati in Intune, il trasferimento dei dati tra app con criteri di protezione delle app e altre app iOS gestite distribuite tramite Intune è consentito automaticamente. Per consentire il trasferimento dei dati tra app con criteri di protezione delle app, abilitare l'impostazione **Allow app to transfer data to only managed apps** (Consenti all'app di trasferire i dati solo alle app gestite). È possibile usare la funzionalità di **gestione Open In** per controllare il trasferimento dei dati tra le app distribuite tramite Intune.   

-   **Dispositivi gestiti da una soluzione MDM di terze parti:** è possibile limitare il trasferimento dei dati solo alle app gestite usando la funzionalità di **gestione Open In** di iOS.
Per assicurarsi che le app distribuite mediante la soluzione MDM di terze parti siano associate anche ai criteri di protezione delle app configurati in Intune, è necessario configurare l'impostazione UPN dell'utente come descritto nella procedura dettagliata [Configurare l'impostazione UPN dell'utente](#configure-user-upn-setting-for-third-party-emm).  Quando le app vengono distribuite con l'impostazione UPN dell'utente, all'app verranno applicati i criteri di protezione delle app nel momento in cui l'utente finale esegue l'accesso con il proprio account aziendale.

> [!IMPORTANT]
> L'impostazione UPN dell'utente è obbligatoria solo per le app distribuite nei dispositivi gestiti da una soluzione MDM di terze parti.  Per i dispositivi gestiti da Intune questa impostazione non è obbligatoria.

## <a name="configure-user-upn-setting-for-third-party-emm"></a>Configurare l'impostazione UPN dell'utente per soluzioni EMM di terze parti
La configurazione dell'impostazione UPN dell'utente è **obbligatoria** per i dispositivi gestiti da una soluzione EMM di terze parti. La procedura descritta di seguito illustra il flusso generale per configurare l'impostazione UPN e l'esperienza dell'utente finale risultante:


1.  Nel portale di Azure [configurare un criterio di protezione delle app](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) per la piattaforma iOS. Configurare le impostazioni dei criteri secondo i requisiti aziendali e selezionare le app che devono rispettare questi criteri.

2.  Distribuire le app e il profilo di posta elettronica che si vuole gestire **tramite la soluzione MDM di terze parti** usando la procedura generalizzata descritta di seguito. Questa esperienza è illustrata anche dall'esempio 1.

  1.  Distribuire l'app con le impostazioni di configurazione seguenti:

      **key** = IntuneMAMUPN, **value** = <username@company.com>

      Esempio: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

  2.  Distribuire i criteri di gestione Apri in con il provider MDM di terze parti in uso nei dispositivi registrati.


### <a name="example-1-admin-experience-in-third-party-mdm-console"></a>Esempio 1: Esperienza di amministrazione nella console MDM di terze parti

1. Passare alla console di amministrazione del provider MDM di terze parti. Passare alla sezione della console in cui si distribuiscono le impostazioni di configurazione dell'applicazione ai dispositivi iOS registrati.

2. Immettere l'impostazione seguente nella sezione Configurazione dell'applicazione:

  **key** = IntuneMAMUPN, **value** = <username@company.com>

  La sintassi esatta della coppia chiave/valore può variare a seconda del provider MDM di terze parti. La tabella seguente visualizza alcuni esempi di provider MDM di terze parti e i valori esatti che devono essere immessi per la coppia chiave/valore.

|Provider MDM di terze parti| Chiave Configuration | Tipo valore | Valore di configurazione|
| ------- | ---- | ---- | ---- |
| VMware AirWatch | IntuneMAMUPN | String | {UserPrincipalName}|
| MobileIron Core | IntuneMAMUPN | String | $EMAIL$ **o** $USER_UPN$ |
| MobileIron Cloud | IntuneMAMUPN | String | ${userUPN} **o** ${userEmailAddress} |

### <a name="example-2-end-user-experience"></a>Esempio 2: Esperienza dell'utente finale

1.  L'utente finale installa l'app di Microsoft Word nel dispositivo.

2.  L'utente finale avvia l'app di posta elettronica nativa gestita per accedere alla posta elettronica.

3.  L'utente finale prova ad aprire un documento dalla posta nativa in Microsoft Word.

4.  Quando viene avviata l'app di Word, all'utente finale viene richiesto di eseguire l'accesso con l'account aziendale.  L'account aziendale immesso dall'utente finale, quando richiesto, deve corrispondere all'account specificato nelle impostazioni di configurazione dell'app di Microsoft Word.

    > [!NOTE]
    > L'utente finale può aggiungere altri account personali a Word per svolgere lavoro personale senza essere interessato dai criteri di protezione delle app quando usa l'app di Word in un contesto personale.

5.  Se l'accesso riesce, le impostazioni dei criteri di protezione delle app vengono applicate all'app Word.

6.  A questo punto il trasferimento del file è stato completato e il documento viene contrassegnato come identità aziendale nell'app. Il file viene inoltre gestito in un contesto aziendale e le impostazioni dei criteri vengono applicate di conseguenza.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Convalidare l'impostazione UPN dell'utente per soluzioni EMM di terze parti

Dopo aver configurato l'impostazione UPN dell'utente, è necessario verificare se l'app iOS può ricevere i criteri di protezione delle app di Intune e conformarsi a tali criteri.

Ad esempio, è facile verificare visivamente l'impostazione del criterio **Richiedi PIN semplice per l'accesso** in un dispositivo. Se il criterio viene impostato su **Sì**, all'utente finale deve essere visualizzato un prompt per impostare o immettere un PIN quando tenta di accedere ai dati aziendali.

Prima di tutto, [creare e distribuire i criteri di protezione delle app](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)  nell'app iOS. Per altre informazioni su come testare i criteri di protezione delle app, vedere [Convalidare i criteri di protezione delle app](validate-mobile-application-management.md).



### <a name="see-also"></a>Vedere anche
[Proteggere i dati delle app usando i criteri di protezione delle app con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
