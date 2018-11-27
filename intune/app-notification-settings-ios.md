---
title: Creare notifiche app per dispositivi iOS - Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare notifiche app per dispositivi iOS in Microsoft Intune. Scegliere le app a cui inviare notifiche, configurare le impostazioni delle notifiche nella schermata di blocco, abilitare il suono, scegliere il tipo di avviso e aggiungere una notifica.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2bf4919fecbba8ad4c0f3b8535adf8b97a35342e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182194"
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>Configurare le impostazioni delle notifiche app per i dispositivi iOS in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configurare la modalità in cui le app installate in un dispositivo iOS devono inviare notifiche. Queste impostazioni supportano dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

## <a name="add-the-app-notification"></a>Aggiungere la notifica app

1. Accedere al [portale di Azure](https://portal.azure.com).
2. All'interno del profilo iOS o macOS selezionare **Funzionalità del dispositivo**. [Funzionalità dei dispositivi iOS o macOS](device-features-configure.md) elenca i passaggi per creare un profilo.
3. Selezionare **Notifiche app (solo con supervisione)** e quindi selezionare **Aggiungi**: ![Aggiungere una notifica app in un profilo iOS o macOS in Intune](./media/ios-macos-app-notifications.png)
4. Immettere le seguenti proprietà:

   - **ID bundle dell'app**: immettere l'**ID bundle** dell'app che si vuole configurare. Per informazioni, vedere **Guida di riferimento agli ID bundle per le app iOS predefinite** in questo articolo.
   - **Nome app**: immettere il nome dell'app che si vuole configurare. Questo nome non viene visualizzato nel dispositivo e viene usato per identificare l'app nell'elenco.
   - **Editore**: immettere l'editore dell'app che si vuole configurare. Il nome dell'editore non viene visualizzato nel dispositivo e viene usato per identificare l'app nell'elenco.
   - **Notifiche**: abilitare o disabilitare l'invio di notifiche al dispositivo da parte dell'app. Se si disabilita questa impostazione, vengono disabilitate anche le impostazioni seguenti.
     - **Mostra nel centro notifiche**: abilitare questa impostazione per consentire all'app di visualizzare notifiche nel centro notifiche del dispositivo.
     - **Mostra nella schermata di blocco**: abilitare questa impostazione per visualizzare le notifiche dall'app nella schermata di blocco del dispositivo.
     - **Tipo avviso**: selezionare il tipo di notifica che si vuole ricevere quando il dispositivo è sbloccato:
       - **Nessuno**: non viene visualizzata alcuna notifica.
       - **Banner**: viene visualizzato brevemente un banner con la notifica.
       - **Modale**: la notifica viene visualizzata e l'utente deve chiuderla manualmente prima di continuare a usare il dispositivo.
     - **Badge sull'icona dell'pp**: abilitare questa impostazione per aggiungere un badge all'icona dell'app che indica l'invio di una notifica.
     - **Suoni**: abilitare questa impostazione per riprodurre un suono quando viene recapitata una notifica.

5. Continuare ad aggiungere tutte le app necessarie. Al termine dell'aggiunta delle app, selezionare **OK**.
6. Selezionare **Crea** per salvare il profilo.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Guida di riferimento agli ID bundle per le app iOS predefinite

L'elenco seguente include l'ID bundle di alcune app comuni iOS predefinite. Per l'ID bundle di altre app, è consigliabile rivolgersi al fornitore del software.

|||
|-|-|
|Nome app|ID bundle|
|App Store|com.apple.AppStore|
|Calcolatrice|com.apple.calculator|
|Calendario|com.apple.mobilecal|
|Fotocamera|com.apple.camera|
|Orologio|com.apple.mobiletimer|
|Bussola|com.apple.compass|
|Contatti|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Trova amici|com.apple.mobileme.fmf1|
|Trova il mio iPhone|com.apple.mobileme.fmip1|
|Area giochi|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Integrità|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|Maps|com.apple.Maps|
|Messaggi|com.apple.MobileSMS|
|Musica|com.apple.Music|
|News|com.apple.news|
|Note|com.apple.mobilenotes|
|Numeri|com.apple.Numbers|
|.NET|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Foto|com.apple.mobileslideshow|
|Podcast|com.apple.podcasts|
|Reminders|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Impostazioni|com.apple.Preferences|
|Stocks|com.apple.stocks|
|Suggerimenti|com.apple.tips|
|Video|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|Video|com.apple.Bridge|
|Weather|com.apple.weather|

## <a name="next-steps"></a>Passaggi successivi

Assegnare il profilo del dispositivo ai gruppi selezionati. I passaggi sono elencati in [Come assegnare i profili di dispositivo con Intune](device-profile-assign.md).