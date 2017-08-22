---
title: Come aggiungere app in Microsoft Intune
titleSuffix: Intune on Azure
description: Queste procedure consentono di ottenere in Intune app pronte per l'assegnazione a utenti e dispositivi. "
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 14f2ac5b25cfe3e688363a21775872baaa9ff89a
ms.sourcegitcommit: 4034ac474bfed358270a32459a2cf2fe02f44e45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2017
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>Come aggiungere un'app a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Prima di poter gestire e assegnare le app per gli utenti, è necessario aggiungerle in Intune. Intune supporta un'ampia gamma di tipi diversi di app e le opzioni possono essere diverse per ogni tipo.

Intune consente di aggiungere e assegnare i tipi di app seguenti:

![Tipi di app supportati da Intune](./media/app-types.png)

Sono supportate le piattaforme seguenti.

- App di Android Store
- App line-of-business Android
- App di iOS Store
- App line-of-business iOS
- App Web
- App di Windows Phone 8.1 Store
- App line-of-business di Windows Phone (file con estensione xap)
- App di Windows Store
- App line-of-business di Windows (solo file con estensione msi)

>[!TIP]
> Un'app line-of-business è un'app che non viene installata da un App Store, ma dal file di installazione dell'app stessa. Ad esempio, per installare un'app line-of-business iOS, aggiungere il file di archivio dell'applicazione (con estensione ipa). Tali app vengono in genere create internamente.

## <a name="before-you-start"></a>Prima di iniziare

Tenere presente quanto segue prima di iniziare ad aggiungere e assegnare le app.

- Quando si aggiunge e si assegna un'app da uno Store, gli utenti finali devono avere un account in tale Store per poter installare l'app.
- Alcune app o elementi assegnati potrebbero dipendere da app iOS predefinite. Ad esempio, se si assegna un libro dallo Store iOS, è necessario che l'app iBooks sia disponibile nel dispositivo. Se l'app iBooks predefinita è stata rimossa, non è possibile usare Intune per ripristinarla.

## <a name="cloud-storage-space"></a>Spazio di archiviazione nel cloud
Tutte le app create con il tipo di installazione del programma di installazione software, ad esempio un'app line-of-business, vengono compresse e caricate nello spazio di archiviazione cloud di Intune. Una sottoscrizione di valutazione di Intune comprende 2 gigabyte (GB) di archiviazione nel cloud per l'archiviazione delle app gestite e degli aggiornamenti. Una sottoscrizione completa include 20 GB di spazio di archiviazione.

È possibile acquistare spazio di archiviazione aggiuntivo per Intune usando il metodo di acquisto originale.  Se il pagamento è stato effettuato con fattura o carta di credito, visitare il [portale di gestione delle sottoscrizioni](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Negli altri casi, contattare il partner o l'assistente alle vendite di riferimento.

I requisiti dello spazio di archiviazione nel cloud sono i seguenti:

-   Tutti i file di installazione delle app devono trovarsi nella stessa cartella.
-   La dimensione massima dei file caricati è di 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Come creare e modificare le categorie di app

Le categorie di app consentono di ordinare le app in modo da consentire agli utenti di trovarle più facilmente nel portale aziendale. È possibile assegnare una o più categorie a un'app, ad esempio **App per sviluppatori** o **App di comunicazione**.
Quando si aggiunge un'app in Intune, è possibile selezionare la categoria desiderata. Usare gli argomenti specifici della piattaforma per aggiungere un'app e assegnare le categorie. Per creare e modificare le categorie, usare la procedura seguente:

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Installazione** > **Categorie di app**.
5. Nel pannello **Categorie di app** viene visualizzato un elenco delle categorie correnti. Scegliere una delle azioni seguenti:
    - **Creare una categoria**: nel pannello **Create category**(Crea categoria) immettere un nome per la nuova categoria. I nomi possono essere immessi in una sola lingua e non vengono tradotti da Intune. Al termine, fare clic su **Crea**.
    - **Modificare una categoria**: per qualsiasi categoria nell'elenco, scegliere "**...**". Nel pannello **Proprietà** è possibile immettere un nuovo nome per la categoria o eliminare la categoria.


## <a name="apps-added-automatically-by-intune"></a>App aggiunte automaticamente da Intune

Intune conteneva in precedenza un numero di app predefinite che era possibile assegnare rapidamente. In base ai commenti e suggerimenti ricevuti, abbiamo rimosso l'elenco e le app predefinite non verranno più visualizzate.
Tuttavia, se sono già state assegnate app predefinite, le app assegnate saranno ancora visibili nell'elenco delle app. È possibile continuare ad assegnare queste app in base alle proprie esigenze.
In una versione successiva si prevede di aggiungere un metodo più semplice per la selezione e l'assegnazione delle app predefinite dal portale di Intune.

## <a name="next-steps"></a>Passaggi successivi

Per informazioni su come aggiungere a Intune app per ciascuna piattaforma, scegliere uno degli argomenti seguenti:

- [App di Android Store](store-apps-android.md)
- [App di Android LOB](lob-apps-android.md)
- [App di iOS Store](store-apps-ios.md)
- [App di iOS LOB](lob-apps-ios.md)
- [App Web (per tutte le piattaforme)](web-app.md)
- [App di Windows Phone 8.1 Store](store-apps-windows-phone-8-1.md)
- [Applicazioni line-of-business di Windows Phone](lob-apps-windows-phone.md)
- [App di Windows Store](store-apps-windows.md)
- [App line-of-business di Windows](lob-apps-windows.md)
- [Applicazioni di Office 365 per Windows 10](apps-add-office365.md)

