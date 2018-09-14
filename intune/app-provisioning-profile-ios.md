---
title: Profili di provisioning di app iOS in Microsoft Intune
titlesuffix: ''
description: Intune offre strumenti per assegnare in modo proattivo un nuovo profilo di provisioning ai dispositivi con app prossime alla scadenza.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8fdfa89654df1f62979240f364c2e28b5a15e78f
ms.sourcegitcommit: d047a692c798e1fb61ee43a487d6332bce344610
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44058915"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Usare i profili di provisioning per le app iOS per impedire la scadenza delle app

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>Introduzione

Nelle app line-of-business Apple iOS assegnate a dispositivi iPhone e iPad sono inclusi sia un profilo di provisioning che codice firmato con un certificato. Quando si esegue l'app, iOS conferma l'integrità dell'app iOS e impone i criteri definiti dal profilo di provisioning. Si verificano le convalide seguenti:

- **Integrità del file di installazione**: iOS confronta i dettagli dell'app con la chiave pubblica del certificato di firma aziendale. Se non vi è corrispondenza, il contenuto dell'app potrebbe essere stato modificato e non sarà consentita l'esecuzione dell'app.
- **Imposizione delle funzionalità**: iOS prova a imporre le funzionalità dell'app dal profilo di provisioning aziendale (non da profili singoli di provisioning dello sviluppatore) contenuto nel file di installazione dell'app (con estensione ipa).


La durata del certificato di firma aziendale usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Mentre il certificato è ancora valido, Intune offre gli strumenti per assegnare in modo proattivo un nuovo profilo di provisioning ai dispositivi con app prossime alla scadenza.
Dopo la scadenza del certificato, è necessario firmare nuovamente l'app con un nuovo certificato e incorporare un nuovo profilo di provisioning con la chiave del nuovo certificato.

L'amministratore può includere ed escludere gruppi di sicurezza per assegnare la configurazione di provisioning delle app iOS. Ad esempio, è possibile assegnare una configurazione di provisioning delle app iOS a Tutti gli utenti, ma escludere un gruppo di manager.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Come creare un profilo di provisioning per dispositivi mobili iOS

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App client**.
1.  Nel carico di lavoro **App client** scegliere **Gestisci** > **Profili di provisioning delle app iOS**.
2.  Nell'elenco del riquadro dei profili scegliere **Crea profilo**.
3. Nel riquadro **Crea profilo** configurare i valori seguenti:
    - **Nome**: specificare un nome per il profilo di provisioning per dispositivi mobili.
    - **Descrizione**: (facoltativo) specificare una descrizione per il criterio.
    - **Carica il file del profilo**: fare clic su **Importa** e quindi scegliere un file del profilo di configurazione per dispositivi mobili Apple, con estensione **mobileprovision**, scaricato dal sito Web Apple Developer.
4. Al termine, scegliere **Crea**.

## <a name="next-steps"></a>Passaggi successivi

Assegnare il profilo ai dispositivi iOS richiesti. Per altre informazioni, vedere la procedura in [Come assegnare i profili di dispositivo](device-profile-assign.md).
