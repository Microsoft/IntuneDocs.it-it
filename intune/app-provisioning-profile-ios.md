---
title: Profili di provisioning delle app
titlesuffix: Azure portal
description: Intune offre gli strumenti per assegnare in modo proattivo un nuovo profilo di provisioning ai dispositivi con app prossime alla scadenza."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b58fb0d9b69e875736b5d2ea884ae9d3453b481
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="use-ios-mobile-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Usare i profili di provisioning per dispositivi mobili iOS per impedire la scadenza delle app

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>Introduzione

Nelle app line-of-business Apple iOS assegnate a dispositivi iPhone e iPad sono inclusi sia un profilo di provisioning che codice firmato con un certificato. Quando si esegue l'app, iOS conferma l'integrità dell'app iOS e impone i criteri definiti dal profilo di provisioning. Si verificano le convalide seguenti:

- **Integrità del file di installazione**: iOS confronta i dettagli dell'app con la chiave pubblica del certificato di firma aziendale. Se non vi è corrispondenza, il contenuto dell'app potrebbe essere stato modificato e non sarà consentita l'esecuzione dell'app.
- **Imposizione delle funzionalità**: iOS prova a imporre le funzionalità dell'app dal profilo di provisioning aziendale (non da profili singoli di provisioning dello sviluppatore) contenuto nel file di installazione dell'app (con estensione ipa).


La durata del certificato di firma aziendale usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Mentre il certificato è ancora valido, Intune offre gli strumenti per assegnare in modo proattivo un nuovo profilo di provisioning ai dispositivi con app prossime alla scadenza.
Dopo la scadenza del certificato, è necessario firmare nuovamente l'app con un nuovo certificato e incorporare un nuovo profilo di provisioning con la chiave del nuovo certificato.


## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Come creare un profilo di provisioning per dispositivi mobili iOS

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
1.  Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **Profili di provisioning di iOS**.
2.  Nell'elenco del pannello dei profili scegliere **Crea profilo**.
3. Nel pannello **Crea profilo** configurare i valori seguenti:
    - **Nome**: specificare un nome per il profilo di provisioning per dispositivi mobili.
    - **Descrizione**: (facoltativo) specificare una descrizione per il criterio.
    - **Carica il file del profilo**: fare clic su **Importa** e quindi scegliere un file del profilo di configurazione per dispositivi mobili Apple, con estensione **mobileprovision**, scaricato dal sito Web Apple Developer.
4. Al termine, scegliere **Crea**.

## <a name="next-steps"></a>Passaggi successivi

Assegnare il profilo ai dispositivi iOS richiesti. Per altre informazioni, vedere la procedura in [Come assegnare i profili di dispositivo](device-profile-assign.md).
