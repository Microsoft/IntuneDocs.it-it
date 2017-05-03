---
title: Impostazioni di layout della schermata iniziale di Intune per i dispositivi iOS
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni sulle impostazioni per personalizzare la schermata iniziale e ancorare i dispositivi iOS.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 4/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6aba4491-afb9-43cd-9ccc-14e6a2a5a3b1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 72bfde93389a060ed52062be0f2692b8bc35543a
ms.lasthandoff: 04/19/2017


---

# <a name="intune-home-screen-layout-settings-for-ios-devices"></a>Impostazioni di layout della schermata iniziale di Intune per i dispositivi iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Usare queste impostazioni per configurare il layout di app, cartelle e clip web nel dock e nella schermata iniziale di tutti i dispositivi iOS ai quali si assegnano i criteri.

I dispositivi iOS ai quali si assegna il profilo devono essere in modalità di supervisione ed eseguire iOS 9.3 o versione successiva.

1. Nel pannello **Funzionalità del dispositivo** scegliere **Layout della schermata iniziale (solo supervisione)**.
2. Nel pannello **Layout della schermata iniziale (solo supervisione)** scegliere se configurare il layout **Dock** o **Pagine**.

## <a name="add-items-to-the-dock"></a>Aggiungere elementi al dock

Nel pannello **Dock** è possibile aggiungere fino a 6 elementi o cartelle al dock nella parte inferiore della schermata iOS. Tuttavia molti dispositivi supportano un numero di elementi inferiore. Ad esempio i dispositivi iPhone supportano un massimo di 4 elementi. In questo caso nel dispositivo verranno visualizzati solo i primi quattro elementi configurati.

1. Scegliere **Aggiungi** per aggiungere un elemento al dock.
2. Nel pannello **Aggiungi riga** scegliere se aggiungere un'**App** o una **Cartella**.
3. Configurare le app e le cartelle da visualizzare nel dock, usando le informazioni delle sezioni **Come aggiungere un'app all'elenco** e **Come aggiungere una cartella all'elenco** di questo argomento.
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
2. Nel pannello **Aggiungi riga**, immettere un **Nome pagina**. Il nome viene usato per riferimento nel portale di Intune e *non viene visualizzato* nel dispositivo iOS.
3. Scegliere **Aggiungi**, quindi scegliere se aggiungere alla pagina un'**App** o una **Cartella**.
4. Configurare le app e le cartelle da visualizzare nella pagina usando le informazioni delle sezioni **Come aggiungere un'app all'elenco** e **Come aggiungere una cartella all'elenco** di questo argomento.

### <a name="example"></a>Esempio

In questo esempio è stata configurata una nuova pagina con il nome **Contoso**. La pagina visualizza solo le app Trova amici e Impostazioni. Nell'immagine seguente l'app Impostazioni è selezionata per illustrarne le proprietà:

![Esempio di impostazioni della schermata iniziale iOS](http://i.imgur.com/Jc2OxyX.png)

Quando si assegnano i criteri a un iPhone, il risultato è una pagina con un aspetto simile al seguente:

![Dispositivo iOS con schermata iniziale modificata](http://i.imgur.com/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>Come aggiungere un'app all'elenco

1. Immettere il **Nome app**. Il nome viene usato per riferimento nel portale di Intune e *non viene visualizzato* nel dispositivo iOS.
2. Immettere l'**ID bundle** dell'app che si vuole visualizzare. Per assistenza, vedere **Guida di riferimento degli ID bundle delle app incorporate di iOS** più avanti in questo argomento.
3. Fare clic su **OK** e continuare ad aggiungere elementi, fino a un massimo di **6** per il dock del dispositivo e di **60** per una pagina del dispositivo.
4. Al termine, fare clic su **OK**.

## <a name="how-to-add-a-folder-to-the-list"></a>Come aggiungere una cartella all'elenco

Le app aggiunte a una pagina in una cartella vengono disposte da sinistra a destra, nell'ordine in cui sono specificate nell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate nella pagina successiva.

1. Immettere il **Nome cartella**. Questo nome viene visualizzato nel dispositivo degli utenti.
2. Scegliere **Aggiungi** per creare una pagina nella cartella. È possibile aggiungere fino a 20 pagine.
3. Nel pannello **Aggiungi riga**, immettere un nome per la pagina. Il nome viene usato per riferimento nel portale di Intune e *non viene visualizzato* nel dispositivo iOS.
3. Immettere il **Nome app**. Il nome viene usato per riferimento nel portale di Intune e *non viene visualizzato* nel dispositivo iOS.
2. Immettere l'**ID bundle** dell'app che si vuole visualizzare. Per assistenza, vedere **Come aggiungere un'app all'elenco**.
3. Scegliere **Aggiungi**. È possibile aggiungere fino a 60 elementi.
4. Al termine, fare clic su **OK**.


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Guida di riferimento degli ID bundle per le app predefinite di iOS

Questo elenco visualizza l'ID bundle di alcune app predefinite comuni di iOS. Per l'ID bundle di altre app rivolgersi al fornitore del software. 

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
|Salute|com.apple.Health|
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
|Numbers|com.apple.Numbers|
|Pages|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Foto|com.apple.mobileslideshow|
|Podcast|com.apple.podcasts|
|Promemoria|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Impostazioni|com.apple.Preferences|
|Borsa|com.apple.stocks|
|Suggerimenti|com.apple.tips|
|Video|com.apple.videos|
|Memo vocali|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|Video|com.apple.Bridge|
|Meteo|com.apple.weather|


