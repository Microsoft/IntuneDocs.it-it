---
title: Profili di provisioning delle app
description: Intune offre gli strumenti per distribuire in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6e975aa7ee22f826c7a0a60d637d651fd347bc54
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="use-ios-mobile-provisioning-profile-policies-to-prevent-your-apps-from-expiring"></a>Usare i criteri del profilo di provisioning per dispositivi mobili iOS per impedire la scadenza delle app

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Nelle app line-of-business Apple iOS distribuite in dispositivi iPhone e iPad sono inclusi un profilo di provisioning e un codice firmato con un certificato. Quando si esegue l'app, iOS conferma l'integrità dell'app iOS e impone i criteri definiti dal profilo di provisioning. Si verificano le convalide seguenti:

- **Integrità del file di installazione**: iOS confronta i dettagli dell'app con la chiave pubblica del certificato di firma aziendale. Se non vi è corrispondenza, il contenuto dell'app potrebbe essere stato modificato e non sarà consentita l'esecuzione dell'app.
- **Imposizione delle funzionalità**: iOS prova a imporre le funzionalità dell'app dal profilo di provisioning aziendale (non da profili singoli di provisioning dello sviluppatore) contenuto nel file di installazione dell'app (con estensione ipa).


La durata del certificato di firma aziendale usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Mentre il certificato è ancora valido, Intune offre gli strumenti per distribuire in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza.
Dopo la scadenza del certificato, è necessario firmare nuovamente l'app con un nuovo certificato e incorporare un nuovo profilo di provisioning con la chiave del nuovo certificato.



## <a name="how-to-find-out-when-a-line-of-business-app-will-expire"></a>Come individuare la scadenza di un'app line-of-business

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **App** > **App**.
2. Nell'elenco delle app esaminare la colonna **Data di scadenza** per visualizzare la data di scadenza dell'app. È inoltre possibile impostare l'elenco a discesa **Filtri** su **Scaduto/prossimo alla scadenza** per visualizzare solo le app per cui è necessario eseguire l'azione.

## <a name="how-to-create-an-ios-mobile-provisioning-profile-policy"></a>Come creare un criterio del profilo di provisioning per dispositivi mobili iOS


1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** > **Panoramica** > **Aggiungi criterio**.
2. Nella finestra di dialogo **Crea un nuovo criterio** scegliere **iOS** > **Criteri del profilo di provisioning per dispositivi mobili** e quindi scegliere **Crea criterio**.
3. Nella pagina **Generale** configurare i valori seguenti:
    - **Nome**: specificare un nome per il criterio del profilo di provisioning per dispositivi mobili.
    - **Descrizione**: (facoltativo) specificare una descrizione per il criterio.
    - **File del profilo di configurazione**: fare clic su **Importa**, quindi scegliere un file del profilo di configurazione per dispositivi mobili Apple, con estensione **mobileprovision**, scaricato dal sito Web Apple Developer.
4. Al termine, scegliere **Salva criterio**.
5. Distribuire ora i criteri ai dispositivi iOS richiesti. Per altre informazioni, vedere [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).