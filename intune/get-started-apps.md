---
title: Introduzione alle app di Microsoft Intune
titlesuffix: ''
description: Trovare le app e aggiungerle ai dispositivi per consentire ai propri collaboratori di svolgere il proprio lavoro.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e206683575b60a5194d83dc829af4fbccfb9d32e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189289"
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Introduzione all'aggiunta di app in Microsoft Intune

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. Intune supporta diversi tipi di app. Inoltre, le opzioni disponibili variano per ogni tipo di app.

Intune consente di aggiungere e assegnare ai dispositivi aziendali i tipi di app seguenti:
- **App dello Store**: per i dispositivi in cui è necessario implementare modalità aggiuntive di gestione applicazioni mobili alle app disponibili nell'App Store.
- **App scritte internamente (line-of-business)**: programmi in cui si carica un file scaricato nei dispositivi degli utenti.
- **App predefinite**: per l'assegnazione di app gestite dedicate, ad esempio le app di Office 365, ai dispositivi iOS e Android.
- **App sul Web**: Intune crea un collegamento all'app Web nella schermata iniziale del dispositivo.

> [!NOTE]
> La propagazione a tutti i dispositivi inclusi nel gruppo dei nuovi criteri applicati a un gruppo di dispositivi dinamico può richiedere fino a otto ore.

## <a name="how-do-i-assign-a-public-store-app"></a>Come si assegna un'app di uno store pubblico?

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Selezionare **App client** e quindi selezionare **App**.
4. Selezionare **Aggiungi** e quindi selezionare **iOS** come **Tipo di app**.
5. Scegliere **Seleziona app** per visualizzare il riquadro **Cerca in App Store**.
6. Nella casella di testo, cercare l'app da assegnare al dispositivo. Scegliere l'app e quindi fare clic su **Seleziona**.
7. Nel riquadro **Aggiungi app** selezionare **Informazioni sull'app** e verificare che tutte le informazioni sull'app siano compilate. È possibile aggiungere altri dettagli facoltativi per definire l'app, ad esempio **Proprietario**, **Note**, **Sviluppatore** e un **URL privacy** per l'informativa sulla privacy dell'azienda.
8. Verificare di avere selezionato **Sì** per **Visualizza come app in primo piano nel portale aziendale** e quindi selezionare **OK**.
9. Selezionare **Aggiungi** nel riquadro **Aggiungi app** per aggiungere l'app. Questa azione consente di visualizzare la **Panoramica** dell'app. Scegliere **Assegnazioni** e quindi fare clic su **Aggiungi gruppo** per assegnare l'app al gruppo di test. Impostare l'app come **Disponibile** per il download. L'app viene visualizzata come **App in primo piano** nel dispositivo di test.


- [Come assegnare app ai gruppi](apps-deploy.md)

## <a name="learn-more"></a>Altre informazioni

* [Che cos'è la gestione delle app con Intune?](app-management.md)
* [Panoramica del ciclo di vita dell'app](app-lifecycle.md)
* [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md)
