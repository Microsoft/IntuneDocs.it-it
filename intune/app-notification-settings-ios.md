---
title: Impostazioni delle notifiche nelle app di Intune per dispositivi iOS
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune di Azure: informazioni sulle impostazioni da usare per controllare le notifiche delle app nei dispositivi iOS.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c64167275a2628c6a3a4e899e00c25df4c10b06b
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="intune-app-notifications-settings-for-ios-devices"></a>Impostazioni delle notifiche delle app di Intune per dispositivi iOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Consente di configurare la modalità in cui vengono inviate le notifiche delle app installate in un dispositivo. Questa impostazione supporta dispositivi supervisionati che eseguono iOS 9.3 e versioni successive.

## <a name="configure-settings"></a>Configurare le impostazioni

1. Nel pannello **Funzionalità del dispositivo** scegliere **Notifiche app (solo con supervisione)**.
2. Nel pannello **Notifiche app** scegliere **Aggiungi**e configurare i valori seguenti:
    - **ID bundle dell'app**: immettere l'**ID bundle** dell'app che si vuole configurare. Per assistenza, vedere **Guida di riferimento agli ID bundle per le app iOS predefinite** più avanti in questo argomento.
    - **Nome app**: immettere il nome dell'app che si vuole configurare. Questo nome non viene visualizzato nel dispositivo e viene usato per identificare l'app nell'elenco.
    - **Editore**: immettere l'ente di pubblicazione dell'app che si vuole configurare. Questo nome non viene visualizzato nel dispositivo e viene usato per identificare l'app nell'elenco.
    - **Notifiche**: abilitare o disabilitare l'invio di notifiche delle app al dispositivo. Se si disabilita questa impostazione, vengono disabilitate anche le impostazioni seguenti.
        - **Mostra nel centro notifiche**: abilitare questa opzione per consentire all'app di visualizzare notifiche nel centro modifiche del dispositivo.
        - **Mostra nella schermata di blocco**: abilitare questa opzione per visualizzare le notifiche dall'app nella schermata di blocco del dispositivo.
        - **Tipo avviso**: selezionare il tipo di notifica che si vuole ricevere quando il dispositivo è sbloccato:
            - **Nessuno**: non viene visualizzata alcuna notifica.
            - **Banner**: viene visualizzato brevemente un banner con la notifica.
            - **Modale**: la notifica viene visualizzata e l'utente deve chiuderla manualmente prima di continuare a usare il dispositivo.
        - **Badge sull'icona dell'pp**: abilitare questa opzione per aggiungere un badge all'icona dell'app che indica che l'app ha inviato una notifica.
        - **Suoni**: abilitare questa opzione per riprodurre un suono quando viene recapitata una notifica.
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
