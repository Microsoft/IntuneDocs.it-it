---
title: Impostazioni di layout della schermata iniziale di Intune per i dispositivi iOS
titlesuffix: Azure portal
description: Informazioni sulle impostazioni per personalizzare la schermata iniziale e il dock nei dispositivi iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6aba4491-afb9-43cd-9ccc-14e6a2a5a3b1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4a3f175337d521c92c909db9972d844ac6997cb0
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="intune-home-screen-layout-settings-for-ios-devices"></a>Impostazioni di layout della schermata iniziale di Intune per i dispositivi iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare queste impostazioni per configurare il layout di app, cartelle e clip web nel dock e nella schermata iniziale dei dispositivi iOS.

I dispositivi iOS ai quali si assegna il profilo devono essere in modalità di supervisione ed eseguire iOS 9.3 o versione successiva.

1. Nei pannelli delle **funzionalità dei dispositivi** scegliere **Layout della schermata iniziale (solo con supervisione)**.
2. Nel pannello **Layout della schermata iniziale (solo supervisione)** scegliere se configurare il layout **Dock** o **Pagine**.

## <a name="add-items-to-the-dock"></a>Aggiungere elementi al dock

Nel pannello **Dock** è possibile aggiungere fino a sei elementi o cartelle al dock della schermata iOS. Tuttavia, molti dispositivi supportano un numero inferiore di elementi. Ad esempio, i dispositivi iPhone supportano massimo quattro elementi. In questo caso, nel dispositivo verranno visualizzati solo i primi quattro elementi configurati.

1. Scegliere **Aggiungi** per aggiungere un elemento al dock.
2. Nel pannello **Aggiungi riga** scegliere se aggiungere un'**App** o una **Cartella**.
3. Usando le informazioni in questo argomento, configurare le app e le cartelle che si vuole visualizzare nel dock.
4. Aggiungere tutti gli elementi desiderati. Al termine, fare clic su **OK** in ogni pannello fino a tornare al pannello **Crea profilo**. Scegliere **Crea**.

>[!TIP]
> È possibile selezionare e trascinare gli elementi di qualsiasi schermata iniziale e qualsiasi elenco di pagine per riordinarli. 

### <a name="example"></a>Esempio

In questo esempio la schermata del dock è stata configurata in modo che visualizzi solo le app Safari, Mail e Borsa. Nella figura seguente, l'app Mail è selezionata per illustrarne le proprietà:

![Impostazioni di esempio del dock iOS](http://i.imgur.com/FfFiUcP.png)

Quando si assegnano i criteri a un iPhone, il risultato è un dock con un aspetto simile al seguente:

![Esempio di layout del dock su iPhone](http://i.imgur.com/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>Aggiungere pagine alla schermata iniziale

Aggiungere le pagine che verranno visualizzate nella schermata iniziale e le app che verranno visualizzate in ogni pagina. Le app aggiunte a una pagina vengono disposte da sinistra a destra, nell'ordine in cui sono specificate nell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate nella pagina successiva.


1. Nel pannello **Pagine**, scegliere **Aggiungi**.
2. Nel pannello **Aggiungi riga**, immettere un **Nome pagina**. Questo nome viene usato come riferimento nel portale di Azure e *non viene visualizzato* nel dispositivo iOS.
3. Scegliere **Aggiungi**, quindi scegliere se aggiungere alla pagina un'**App** o una **Cartella**.
4. Usando le informazioni in questo argomento, configurare le app e le cartelle che si vuole visualizzare nella pagina.

### <a name="example"></a>Esempio

In questo esempio è stata configurata una nuova pagina con il nome **Contoso**. La pagina visualizza solo le app Trova amici e Impostazioni. Nell'immagine seguente l'app Impostazioni è selezionata per illustrarne le proprietà:

![Esempio di impostazioni della schermata iniziale iOS](http://i.imgur.com/Jc2OxyX.png)

Quando si assegnano i criteri a un iPhone, il risultato è una pagina con un aspetto simile al seguente:

![Dispositivo iOS con schermata iniziale modificata](http://i.imgur.com/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>Come aggiungere un'app all'elenco

1. Immettere il **Nome app**. Questo nome viene usato come riferimento nel portale di Azure e *non viene visualizzato* nel dispositivo iOS.
2. Immettere l'**ID bundle** dell'app che si vuole visualizzare. Per assistenza, vedere **Guida di riferimento degli ID bundle delle app incorporate di iOS** più avanti in questo argomento.
3. Fare clic su **OK** e continuare ad aggiungere elementi, fino a un massimo di **6** per il dock del dispositivo e di **60** per una pagina del dispositivo.
4. Al termine, fare clic su **OK**.

## <a name="how-to-add-a-folder-to-the-list"></a>Come aggiungere una cartella all'elenco

Le app aggiunte a una pagina in una cartella vengono disposte da sinistra a destra, nell'ordine in cui sono specificate nell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate nella pagina successiva.

1. Immettere il **Nome cartella**. Questo nome viene visualizzato nel dispositivo degli utenti.
2. Scegliere **Aggiungi** per creare una pagina nella cartella. È possibile aggiungere fino a 20 pagine.
3. Nel pannello **Aggiungi riga**, immettere un nome per la pagina. Questo nome viene usato come riferimento nel portale di Azure e *non viene visualizzato* nel dispositivo iOS.
3. Immettere il **Nome app**. Questo nome viene usato come riferimento nel portale di Azure e *non viene visualizzato* nel dispositivo iOS.
2. Immettere l'**ID bundle** dell'app che si vuole visualizzare. Per assistenza, vedere **Come aggiungere un'app all'elenco**.
3. Scegliere **Aggiungi**. È possibile aggiungere fino a 60 elementi.
4. Al termine, fare clic su **OK**.


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Guida di riferimento degli ID bundle per le app predefinite di iOS

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