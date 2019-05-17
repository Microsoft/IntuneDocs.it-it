---
title: Come configurare l'app Portale aziendale
titleSuffix: Microsoft Intune
description: Informazioni su come applicare specifiche personalizzazioni aziendali all'app Portale aziendale.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 33f24a3d7b30973855bb303bb97bf703cd4dc5fa
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567270"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Come configurare l'app Portale aziendale di Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Il portale aziendale di Microsoft Intune è il punto in cui gli utenti possono accedere ai dati aziendali ed eseguire attività comuni quali la registrazione dei dispositivi, l'installazione di app e la ricerca delle informazioni di assistenza del reparto IT.        

> [!Tip]        
> Quando si personalizza il portale aziendale, le configurazioni vengono applicate sia al sito Web che alle app Portale aziendale. Si noti che gli utenti devono avere una licenza di Intune assegnata per accedere al sito Web del portale aziendale.

Con la personalizzazione del Portale aziendale si offrirà agli utenti finali un'esperienza familiare e utile. A questo scopo, nel portale di Intune selezionare **App client** > **Personalizzazione** e quindi configurare le impostazioni necessarie. 

> [!Note]       
> Se si usa Azure per enti pubblici, l'utente finale riceve i log delle app per prendere decisioni in merito alla condivisione quando avvia il processo per visualizzare la Guida per un problema. Se tuttavia non si usa Azure per enti pubblici, il portale aziendale per Windows 10 invierà i log delle app direttamente a Microsoft quando l'utente avvia il processo per visualizzare la Guida per un problema. Inviando i log delle app a Microsoft sarà più semplice risolvere i problemi. 

## <a name="company-information-and-privacy-statement"></a>Informazioni e informativa sulla privacy della società        
Il nome dell'azienda viene visualizzato come titolo del portale aziendale. L'informativa sulla privacy viene visualizzata quando un utente fa clic sul relativo collegamento.

I campi contrassegnati con un asterisco (*) sono obbligatori.       


| Nome del campo | Lunghezza massima | Altre informazioni |
|---|---|---|
|**Nome società**| 40 | Questo nome viene visualizzato come titolo del portale aziendale e appare come testo nell'intera esperienza utente Intune. |
| **URL dell'informativa sulla privacy** |     79     | È possibile indicare l'informativa sulla privacy della propria azienda che verrà visualizzata quando gli utenti fanno clic sui collegamenti relativi alla privacy dal portale aziendale. Immettere un URL valido nel formato `<https://www.contoso.com>`. |

## <a name="support-information"></a>Informazioni di supporto      
Immettere le informazioni di supporto della società, in modo da garantire al dipendente un contatto per le domande relative a Intune.          

|Nome del campo|Lunghezza massima|Altre informazioni|
|---|---|---|
|**Nome di contatto** | 40 | Questo nome viene visualizzato nella pagina **Contatta l'IT**. |
|**Numero di telefono** | 20 | Questo numero di contatto viene visualizzato nella pagina **Contatta l'IT** che consente ai dipendenti di contattare l'organizzazione per ottenere supporto. |
|**Indirizzo di posta elettronica**| 40 | Questo indirizzo di contatto viene visualizzato nella pagina **Contatta l'IT**. È necessario immettere un indirizzo di posta elettronica valido nel formato `alias@domainname.com`. |
|**Nome del sito Web**| 40 | Questo è il nome descrittivo visualizzato per l'URL del sito Web del supporto tecnico. Se si specifica solo un URL del sito Web e nessun nome descrittivo, nella pagina **Contatta l'IT** del portale aziendale verrà visualizzato Vai al sito Web IT. |
|**URL del sito Web**| 150 | Se si dispone di un sito Web di supporto che si desidera venga usato dagli utenti, è necessario specificare qui l'URL. Il formato dell'URL deve essere `https://www.contoso.com`. Se non si specifica un URL, non verrà visualizzato alcun valore nella pagina **Contatta l'IT** del portale aziendale. |
| **Informazioni aggiuntive**| 120 | Visualizzato nella pagina **Contatta l'IT** |


## <a name="company-identity-branding-customization"></a>Personalizzazione del branding dell'identità aziendale      
È possibile personalizzare il portale aziendale con logo, nome dell'azienda, colore del tema e sfondo.     

### <a name="theme-color-and-logo-in-the-company-portal"></a>Colore del tema e logo nel portale aziendale
È possibile applicare un colore del tema al portale aziendale. Selezionare un colore standard o immettere un codice esadecimale a sei cifre corrispondente a un colore personalizzato.

|Nome del campo|Altre informazioni|
|---|---|
|**Select a standard color or enter a six-digit hex code** (Selezionare un colore standard o immettere un codice esadecimale a sei cifre)| Scegliere **Standard** per selezionare visivamente un colore. Scegliere **Personalizzato** per selezionare un colore specifico in base a un valore in formato esadecimale.|
|**Choose theme color** (Scegliere il colore del tema)| Selezionare un colore del tema da applicare al portale aziendale. È possibile scegliere un colore standard o immettere un codice esadecimale specifico. |
|**Display** (Schermo)| Specificare se visualizzare il **logo e il nome della società**, **solo il logo della società** o solo il **nome della società**. |
|**Upload your company logo** (Carica il logo della società)|È possibile caricare il logo della società da visualizzare nel portale aziendale. Si noti che il colore del testo viene selezionato automaticamente per offrire il massimo livello di contrasto. Per assicurare un aspetto ottimale, caricare un logo con uno sfondo trasparente.<p><ul><li>Dimensioni massime dell'immagine: 400x400 px</li><li>Dimensioni massime del file: 750 kB</li><li>Tipo di file: PNG, JPG o JPEG</li></ul>|

Dopo aver caricato il logo, l'area di anteprima visualizza il logo con il colore del tema. Se si sceglie di visualizzare il nome della società, il nome verrà visualizzato in nero o in bianco nel portale aziendale in modo da offrire il massimo livello di contrasto in base al colore del tema. L'area di anteprima nella schermata non visualizzerà il nome della società. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logo da usare su sfondi bianchi o chiari
Scegliere un logo adatto a sfondi bianchi o chiari.

|Nome del campo|Altre informazioni|
|---|---|
|**Upload your logo** (Carica il logo)| Questa opzione è disponibile se si è scelto di visualizzare il logo della società. Per assicurare un aspetto ottimale, caricare un logo con uno sfondo trasparente.<p><ul><li>Dimensioni massime dell'immagine: 400x400 px</li><li>Dimensioni massime del file: 750 kB</li><li>Tipo di file: PNG, JPG o JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Immagine del marchio per il portale aziendale

Visualizzare un'immagine del marchio che rifletta il marchio della società. Dopo aver salvato le modifiche è possibile scegliere **Visualizzare l'anteprima delle impostazioni nel portale Web di Intune** nella parte superiore del pannello per visualizzare come appaiono le configurazioni. Si noti che l'immagine del marchio può essere visualizzata in anteprima solo in un dispositivo iOS e non nel portale Web di Intune. 

|Nome del campo|Altre informazioni|
|---|---|
|**Upload your brand image** (Caricare immagine del marchio)| Questa opzione consente di visualizzare un'immagine del marchio. Nell'app Portale aziendale iOS viene visualizzata come immagine di sfondo nella pagina del profilo dell'utente.<p><ul><li>Larghezza dell'immagine consigliata: Meno di 1125 px ma non meno di 640 px</li><li>Dimensioni massime dell'immagine: 1,3 MB</li><li>Tipo di file: PNG, JPG o JPEG</li></ul>|

L'immagine del marchio può migliorare la fiducia dell'utente nel portale aziendale presentando un forte senso di marchio della società. Di seguito sono riportati alcuni suggerimenti che è possibile prendere in considerazione per l'acquisizione, la scelta e l'ottimizzazione dell'immagine per il portale aziendale. 

- Rivolgersi al reparto marketing o pubblicità. È possibile che il reparto abbia già a disposizione un set di immagini del marchio approvate. Il reparto può anche aiutare l'utente ad adattare le immagini alle esigenze specifiche. 

- Prendere in considerazione sia la composizione verticale che quella orizzontale. L'immagine deve avere uno sfondo sufficiente che circonda il punto focale. L'immagine può essere ritagliata in diversi modi in base alle dimensioni del dispositivo, all'orientamento e alla piattaforma. 

- Evitare di usare un'immagine generica. L'immagine deve riflettere il marchio della società ed essere familiare agli utenti. Se non è disponibile alcuna immagine, è preferibile non usare un'immagine generica che non ha alcun significato per l'utente. 

- Rimuovere i metadati non necessari. Il file di immagine può includere i metadati, ad esempio il profilo della fotocamera, la posizione geografica, il titolo, il sottotitolo e così via. Usare uno strumento di ottimizzazione delle immagini per rimuovere queste informazioni per mantenere la qualità e rispettare il limite di dimensione del file. 

Dopo l'aggiunta o la modifica di un'immagine del marchio in Intune, l'utente finale potrebbe non vedere la modifica nei dispositivi iOS fino a quando il portale aziendale non riconosce la modifica all'avvio e viene quindi riavviato per visualizzare l'immagine del marchio. 

### <a name="brand-image-examples"></a>Esempi di immagini di marchio

L'immagine seguente mostra un esempio di immagine del marchio per iPad:

![Screenshot dell'immagine del marchio per iPad di esempio](media/company-portal-app/company-portal-app-03.png)

L'immagine seguente mostra un esempio di immagine del marchio iPhone:

![Screenshot dell'immagine del marchio per iPhone di esempio](media/company-portal-app/company-portal-app-02.png)

## <a name="windows-company-portal-keyboard-shortcuts"></a>Tasti di scelta rapida del portale aziendale di Windows

Gli utenti finali possono usare tasti di scelta rapida per eseguire azioni di spostamento, sulle app e sui dispositivi nel portale aziendale di Windows.

I tasti di scelta rapida seguenti sono disponibili nell'app Portale aziendale di Windows.

| Area | Descrizione | Tasti di scelta rapida |
|:------------------:|:--------------:|:-----------------:|
| Menu di spostamento | Spostamento | ALT+M |
|  | Home | ALT+H |
|  | Tutte le app | ALT+A |
|  | App installate | ALT+I |
|  | Inviare un feedback | ALT+F |
|  | Profilo personale | ALT+U |
|  | Impostazioni | ALT+T |
| Home - Riquadro dispositivo | Rinomina | F2 |
|  | Remove | CTRL+D o CANC |
|  | Verifica l'accesso | CTRL+M o F9 |
| Dettagli dispositivo | Rinomina | F2 |
|  | Remove | CTRL+D o CANC |
|  | Verifica l'accesso | CTRL+M o F9 |
| Dettagli dell'app | Installare | CTRL+I |

Gli utenti finali potranno anche visualizzare i tasti di scelta rapida disponibili nell'app Portale aziendale di Windows.

![Screenshot dei tasti di scelta rapida disponibili nell'app Portale aziendale di Windows](media/company-portal-app/company-portal-app-01.png)

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere manualmente l'app Portale aziendale di Windows 10 usando Microsoft Intune](store-apps-company-portal-app.md)
