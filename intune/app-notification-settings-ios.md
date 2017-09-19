---
title: Impostazioni delle notifiche nelle app di Intune per dispositivi iOS
titlesuffix: Azure portal
description: Informazioni sulle impostazioni da usare per controllare le notifiche delle app nei dispositivi iOS."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 46b31be3cd05c0a5252589d2b25eb92b86a42733
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
---
# <a name="intune-app-notifications-settings-for-ios-devices"></a>Impostazioni delle notifiche delle app di Intune per i dispositivi iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Consente di configurare la modalità in cui vengono inviate le notifiche delle app installate in un dispositivo. Queste impostazioni supportano dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

## <a name="configure-settings"></a>Configurare le impostazioni

1. Nel pannello delle funzionalità del dispositivo scegliere **Notifiche app (solo con supervisione)**.
2. Nel pannello **Notifiche app** scegliere **Aggiungi**e configurare i valori seguenti:
    - **ID bundle dell'app**: immettere l'**ID bundle** dell'app che si vuole configurare. Per assistenza, vedere **Guida di riferimento agli ID bundle per le app iOS predefinite** più avanti in questo argomento.
    - **Nome app**: immettere il nome dell'app che si vuole configurare. Questo nome non viene visualizzato nel dispositivo e viene usato per identificare l'app nell'elenco.
    - **Editore**: immettere l'ente di pubblicazione dell'app che si vuole configurare. Il nome dell'editore non viene visualizzato nel dispositivo e viene usato per identificare l'app nell'elenco.
    - **Notifiche**: abilitare o disabilitare l'invio di notifiche delle app al dispositivo. Se si disabilita questa impostazione, vengono disabilitate anche le impostazioni seguenti.
        - **Mostra nel centro notifiche**: abilitare questa impostazione per consentire all'app di visualizzare notifiche nel centro notifiche del dispositivo.
        - **Mostra nella schermata di blocco**: abilitare questa impostazione per visualizzare le notifiche dall'app nella schermata di blocco del dispositivo.
        - **Tipo avviso**: selezionare il tipo di notifica che si vuole ricevere quando il dispositivo è sbloccato:
            - **Nessuno**: non viene visualizzata alcuna notifica.
            - **Banner**: viene visualizzato brevemente un banner con la notifica.
            - **Modale**: la notifica viene visualizzata e l'utente deve chiuderla manualmente prima di continuare a usare il dispositivo.
        - **Badge sull'icona dell'pp**: abilitare questa impostazione per aggiungere un badge all'icona dell'app che indica l'invio di una notifica.
        - **Suoni**: abilitare questa impostazione per riprodurre un suono quando viene recapitata una notifica.
3. Continuare ad aggiungere tutte le app necessarie. Al termine, scegliere **OK**.
4. Fare clic più volte su **OK** fino a quando non viene visualizzato il pannello **Crea profilo** e scegliere **Crea**. 


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Guida di riferimento agli ID bundle per le app iOS predefinite

Questo elenco include l'ID bundle di alcune app comuni iOS predefinite. Per l'ID bundle di altre app rivolgersi al fornitore del software. 

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

È ora possibile assegnare il profilo del dispositivo ai gruppi selezionati. Per informazioni dettagliate, vedere [How to assign device profiles](device-profile-assign.md) (Come assegnare profili di dispositivo).
