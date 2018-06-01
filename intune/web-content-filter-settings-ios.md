---
title: Impostazioni dei filtri del contenuto Web di Microsoft Intune per i dispositivi iOS
titlesuffix: ''
description: Informazioni sulle impostazioni di Microsoft Intune che possono essere usate per consentire e bloccare l'accesso ai siti Web dai dispositivi con iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1c8eb121b3db52f0fdfc30d7d8dff7ef0f7bf97b
ms.sourcegitcommit: f21287c66dd5559688f08bd98b6c976a0dea055d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2018
ms.locfileid: "34456351"
---
# <a name="web-content-filter-settings-for-ios-devices"></a>Impostazioni di filtraggio del contenuto Web per i dispositivi iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni di Microsoft Intune che consentono di controllare l'accesso con URL del browser dai dispositivi che eseguono iOS.

È possibile usare due metodi per configurare gli URL:

- **Configurare gli URL**: usare il filtro Web predefinito di Apple che cerca termini per adulti, ad esempio un linguaggio volgare o sessualmente esplicito. Questa funzione valuta ogni pagina Web non appena viene caricata e tenta di identificare e bloccare il contenuto non appropriato. È anche possibile configurare URL che non vengono verificati dal filtro o URL che vengono bloccati, indipendentemente dalle impostazioni del filtro.

- **Specificare solo i siti Web** (solo per il Web browser Safari): questi URL vengono aggiunti ai segnalibri del browser Safari. Viene consentito all'utente di visitare **solo** questi siti, non è possibile accedere ad altri siti. Usare questa opzione solo se si conosce l'elenco esatto degli URL a cui gli utenti possono accedere.
Se non si specifica alcun URL, gli utenti finali non saranno in grado di accedere ad alcun sito Web, ad eccezione di microsoft.com, microsoft.net e apple.com.

## <a name="get-started"></a>Operazioni preliminari

1. Nella pagina Funzionalità del dispositivo scegliere **Filtro contenuto Web (solo con supervisione)**.
2. Nella pagina **Filtro contenuto Web** scegliere il **tipo di filtro** che si vuole configurare da:
    - **Non configurato**: non viene applicato alcun filtro.
    - **Configura gli URL**
    - **Solo siti Web specifici**
3. Successivamente, seguire una delle procedure seguenti in base al tipo di filtro in uso:


## <a name="configure-urls"></a>Configurare gli URL

1. Nella pagina **Filtro contenuto Web** scegliere una delle seguenti impostazioni come necessario:
   - **URL autorizzati**: immettere nella pagina **URL autorizzati** gli URL che si vuole autorizzare (ignorando il filtro Web di Apple) e premere INVIO dopo avere scelto ogni opzione.
     > [!NOTE]
     > Gli URL specificati qui sono quelli che non devono essere sottoposti al filtro Web di Apple. Questi URL non rappresentano un elenco dei soli siti Web consentiti. Per indicare un elenco dei soli siti Web consentiti, usare **Solo siti Web specifici**.

   - **URL bloccati**: immettere nella pagina **URL bloccati** gli URL che si vuole bloccare (indipendentemente dalle impostazioni del filtro Web di Apple) e premere INVIO dopo avere scelto ogni opzione.
2. Al termine, fare clic su **OK**.


## <a name="specific-websites-only"></a>Solo siti Web specifici

1. Nella pagina **Filtro contenuto Web** configurare le impostazioni seguenti per ogni sito Web che si vuole autorizzare:
    - **URL**: immettere l'URL del sito Web che si vuole autorizzare, ad esempio **http://www.contoso.com**.
    - **Percorso del segnalibro**: immettere il percorso in cui verrà archiviato il segnalibro, ad esempio **/Contoso/Business Apps**. Se non si aggiunge un percorso, il segnalibro verrà aggiunto alla cartella dei segnalibri predefiniti nel dispositivo.
    - **Titolo**: immettere un titolo descrittivo per il segnalibro.
2. Fare clic su **Aggiungi** dopo avere immesso le informazioni per ogni sito Web.
3. Al termine, fare clic su **OK**.

> [!IMPORTANT]
> Gli URL seguenti vengono automaticamente autorizzati da Intune.
> - <www.microsoft.com>
> - <www.microsoft.net>
> - <www.apple.com>

## <a name="finish-up"></a>Terminare

Scegliere **OK** per tornare al riquadro **Crea profilo** e quindi scegliere **Crea**.

## <a name="next-steps"></a>Passaggi successivi

È ora possibile assegnare il profilo del dispositivo ai gruppi selezionati. Per informazioni dettagliate, vedere [How to assign device profiles](device-profile-assign.md) (Come assegnare profili di dispositivo).
