---
title: Gestire il trasferimento di dati tra app iOS | Microsoft Intune
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 002ebec14a089754849024916590b787431c7efe
ms.openlocfilehash: fce0081fc1ecb92acf539a2d69f0493fb30ee418


---

# Gestire il trasferimento di dati tra app iOS con Microsoft Intune
## Gestire le app iOS
La protezione dei dati aziendali prevede anche che ci si assicuri che i trasferimenti di file siano limitati alle app gestite dall'utente.  È possibile gestire le app iOS nei modi seguenti:

-   Evitare perdite di dati aziendali tramite la configurazione di criteri MAM per le app, a cui si farà riferimento con il termine app **gestite da criteri**.

-   È anche possibile distribuire e gestire le app tramite il **canale MDM**.  Ciò richiede che i dispositivi vengono registrati nella soluzione MDM. Possono essere app **gestite da criteri** o altre app gestite.

La funzionalità di **gestione Open In** per i dispositivi iOS consente i trasferimenti di file solo tra le app distribuite tramite il **canale MDM**. Le restrizioni della gestione Open In sono definite nelle impostazioni di configurazione e distribuite tramite la soluzione MDM.  Quando l'utente installa l'app distribuita, vengono applicate le restrizioni impostate.
##  Uso di software MAM con le app iOS
I criteri di gestione di applicazioni mobili (MAM) possono essere usati con la funzionalità di **gestione Open In** di iOS per proteggere i dati aziendali nei modi seguenti:

-   **Dispositivi di proprietà dei dipendenti non gestiti da soluzioni MDM:** è possibile impostare i criteri MAM su **Allow app to transfer data to only managed apps** (Consenti all'app di trasferire i dati solo alle app gestite). Quando l'utente finale apre un file protetto in un'app non gestita da criteri, il file è illeggibile.

-   **Dispositivi gestiti da Intune:** per i dispositivi registrati in Intune, il trasferimento dei dati tra app con criteri MAM e altre app iOS gestite distribuite tramite Intune è consentito automaticamente. Per consentire il trasferimento dei dati tra app con criteri MAM, abilitare l'impostazione **Allow app to transfer data to only managed apps** (Consenti all'app di trasferire i dati solo alle app gestite). È possibile usare la funzionalità di **gestione Open In** per controllare il trasferimento dei dati tra le app distribuite tramite Intune.   

-   **Dispositivi gestiti da una soluzione MDM di terze parti:** è possibile limitare il trasferimento dei dati solo alle app gestite usando la funzionalità di **gestione Open In** di iOS.
Per assicurarsi che le app distribuite mediante la soluzione MDM di terze parti siano associate anche ai criteri MAM configurati in Intune, è necessario configurare l'impostazione UPN dell'utente come descritto nella procedura dettagliata [Configurare l'impostazione UPN dell'utente](#configure-user-upn-setting).  Quando le app vengono distribuite con l'impostazione UPN dell'utente, all'app verranno applicati i criteri MAM nel momento in cui l'utente finale esegue l'accesso con il proprio account aziendale.

> [!IMPORTANT]
> L'impostazione UPN dell'utente è obbligatoria solo per le app distribuite nei dispositivi gestiti da una soluzione MDM di terze parti.  Per i dispositivi gestiti da Intune questa impostazione non è obbligatoria.

## Configurare l'impostazione UPN dell'utente
Questa configurazione è necessaria per i dispositivi gestiti da una soluzione MDM di terze parti. La procedura descritta di seguito illustra il flusso generale di implementazione dell'impostazione UPN e l'esperienza dell'utente finale risultante:


1.  Nel portale di Azure [configurare i criteri di gestione delle app mobili](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) per la piattaforma iOS. Configurare le impostazioni dei criteri secondo i requisiti aziendali e selezionare le app che devono rispettare questi criteri.

2.  Distribuire le app e il profilo di posta elettronica che si vuole gestire **tramite la soluzione MDM di terze parti** usando l'impostazione descritta nei passaggi 3 e 4.

3.  Distribuire l'app con le impostazioni di configurazione seguenti: key=IntuneMAMUPN, Value=<nomeutente@azienda.com> [esempio: 'IntuneMAMUPN', 'jondoe@microsoft.com']

4.  Distribuire i criteri di gestione Open In nei dispositivi registrati.

### Esempio di esperienza utente finale

1.  L'utente finale installa l'app di Microsoft Word nel dispositivo.

2.  L'utente finale avvia l'app di posta elettronica nativa gestita per accedere alla posta elettronica.

3.  L'utente finale prova ad aprire un documento dalla posta nativa in Microsoft Word.

4.  Quando viene avviata l'app di Word, all'utente finale viene richiesto di eseguire l'accesso con l'account aziendale.  L'account aziendale immesso dall'utente finale, quando richiesto, deve corrispondere all'account specificato nelle impostazioni di configurazione dell'app di Microsoft Word.

    > [!NOTE]
    > L'utente finale può aggiungere altri account personali a Word per svolgere lavoro personale senza essere interessato dai criteri MAM quando usa l'app di Word in un contesto personale.

5.  Se l'accesso riesce, le impostazioni dei criteri per le app vengono applicate all'app Word.

6.  A questo punto il trasferimento dei dati avrà esito positivo e il documento viene contrassegnato come identità aziendale nell'app. I dati, poi, vengono trattati in un contesto aziendale e le impostazioni dei criteri vengono applicate di conseguenza.

### Vedere anche
[Proteggere i dati delle app usando i criteri di gestione delle app mobili con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


