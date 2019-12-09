---
title: Profili di provisioning di app iOS in Microsoft Intune
titleSuffix: ''
description: Intune offre strumenti per assegnare in modo proattivo un nuovo profilo di provisioning ai dispositivi con app prossime alla scadenza.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31bad59c33a34d0b92d93979b20b58f70fd042ef
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564087"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Usare i profili di provisioning per le app iOS per impedire la scadenza delle app

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Introduzione

Nelle app line-of-business Apple iOS assegnate a dispositivi iPhone e iPad sono inclusi sia un profilo di provisioning che codice firmato con un certificato. Quando si esegue l'app, iOS conferma l'integrità dell'app iOS e impone i criteri definiti dal profilo di provisioning. Si verificano le convalide seguenti:

- **Integrità del file di installazione**: iOS confronta i dettagli dell'app con la chiave pubblica del certificato di firma aziendale. Se non vi è corrispondenza, il contenuto dell'app potrebbe essere stato modificato e non sarà consentita l'esecuzione dell'app.
- **Imposizione delle funzionalità**: iOS prova a imporre le funzionalità dell'app dal profilo di provisioning aziendale (non da profili singoli di provisioning dello sviluppatore) contenuto nel file di installazione dell'app (con estensione ipa).


La durata del certificato di firma aziendale usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Mentre il certificato è ancora valido, Intune offre gli strumenti per assegnare in modo proattivo un nuovo profilo di provisioning ai dispositivi con app prossime alla scadenza.
Dopo la scadenza del certificato, è necessario firmare nuovamente l'app con un nuovo certificato e incorporare un nuovo profilo di provisioning con la chiave del nuovo certificato.

L'amministratore può includere ed escludere gruppi di sicurezza per assegnare la configurazione di provisioning delle app iOS. Ad esempio, è possibile assegnare una configurazione di provisioning delle app iOS a Tutti gli utenti, ma escludere un gruppo di manager.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Come creare un profilo di provisioning per dispositivi mobili iOS

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Profili di provisioning delle app iOS** > **Crea profilo**.
3. Nella pagina **Informazioni di base** aggiungere i valori seguenti:
    - **Nome**: specificare un nome per il profilo di provisioning per dispositivi mobili.
    - **Descrizione**: (facoltativo) specificare una descrizione per il criterio.
    - **Carica il file del profilo**: scegliere l'icona **Apri** e quindi scegliere un file del profilo di configurazione per dispositivi mobili Apple, con estensione `.mobileprovision`, scaricato dal [sito Web Apple Developer](https://developer.apple.com/).

   Il campo **Data di scadenza** verrà compilato da un valore nel file del profilo di configurazione per dispositivi mobili Apple aggiunto in precedenza.<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. Fare clic su **Avanti: Tag di ambito**.<br>
   Nella pagina **Tag di ambito** è possibile configurare facoltativamente i tag di ambito per determinare chi può visualizzare il profilo di provisioning delle app iOS in Intune. Per altre informazioni sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).
5. Fare clic su **Avanti: Assegnazioni**.<br>
   La pagina **Assegnazioni** consente di assegnare il profilo a utenti e dispositivi. Si noti che è possibile assegnare un profilo a un dispositivo indipendentemente dal fatto che il dispositivo sia gestito da Intune o meno.
6. Fare clic su **Avanti: Rivedi e crea** per verificare i valori immessi per il profilo.
7. Al termine, fare clic su **Crea** per creare il profilo di provisioning delle app iOS in Intune. 

## <a name="next-steps"></a>Passaggi successivi

Assegnare il profilo ai dispositivi iOS richiesti. Per altre informazioni, vedere la procedura in [Come assegnare i profili di dispositivo](../device-profile-assign.md).
