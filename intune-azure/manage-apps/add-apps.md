---
title: Come aggiungere app in Microsoft Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: queste procedure consentono di ottenere in Intune app pronte per l&quot;assegnazione a utenti e dispositivi. '
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: d85544bdfaa3a369e1d2d03e5454ff7aa2d75467
ms.lasthandoff: 04/19/2017

---

# <a name="how-to-add-an-app-to-microsoft-intune"></a>Come aggiungere un'app a Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Prima di poter gestire e assegnare le app per gli utenti, è necessario aggiungerle in Intune. Intune supporta un'ampia gamma di tipi diversi di app e le opzioni possono essere diverse per ogni tipo.

Intune consente di aggiungere e assegnare i tipi di app seguenti:

![Tipi di app supportati da Intune](./media/app-types.png)

Sono supportate le piattaforme seguenti. Fare clic su uno degli argomenti per altre informazioni sulle modalità di aggiunta di tutti i tipi di app.

- [App di Android Store](/intune-azure/manage-apps/android-store-app)
- [App di Android LOB](/intune-azure/manage-apps/android-lob-app)
- [App di iOS Store](/intune-azure/manage-apps/ios-store-app)
- [App di iOS LOB](/intune-azure/manage-apps/ios-lob-app)
- [App Web (per tutte le piattaforme)](/intune-azure/manage-apps/web-app)
- [App di Windows Phone 8.1 Store](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [App di Windows Store](/intune-azure/manage-apps/windows-store-app)

Alcune app Microsoft vengono aggiunte automaticamente da Intune quando viene configurato il tenant. Queste app verranno elencate più avanti in questo argomento.

## <a name="before-you-start"></a>Prima di iniziare

Tenere presente quanto segue prima di iniziare ad aggiungere e assegnare le app.

- Quando si aggiunge e si distribuisce un'app da un archivio, gli utenti finali devono avere un account dell'archivio per poter installare l'app.
- Alcune app o elementi distribuiti potrebbero dipendere da app iOS predefinite. Ad esempio, se si distribuisce un libro dallo Store iOS, è necessario che l'app iBooks sia disponibile nel dispositivo. Se l'app iBooks predefinita è stata rimossa, non è possibile usare Intune per ripristinarla.

## <a name="cloud-storage-space"></a>Spazio di archiviazione nel cloud
Tutte le app create con il tipo di installazione del programma di installazione software, ad esempio un'app line-of-business, vengono compresse e caricate nello spazio di archiviazione cloud di Microsoft Intune. Una sottoscrizione di valutazione di Intune comprende 2 gigabyte (GB) di archiviazione nel cloud per l'archiviazione delle app gestite e degli aggiornamenti. Una sottoscrizione completa include 20 GB di spazio di archiviazione.

È possibile acquistare spazio di archiviazione aggiuntivo per Intune usando il metodo di acquisto originale.  Se il pagamento è stato effettuato con fattura o carta di credito, visitare il [portale di gestione delle sottoscrizioni](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Negli altri casi, contattare il partner o l'assistente alle vendite di riferimento.

I requisiti dello spazio di archiviazione nel cloud sono i seguenti:

-   Tutti i file di installazione delle app devono trovarsi nella stessa cartella.
-   La dimensione massima dei file caricati è di 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Come creare e modificare le categorie di app

Le categorie di app possono essere usate per ordinare le app in modo da consentire agli utenti finali di trovarle più facilmente nel portale aziendale. È possibile assegnare una o più categorie a un'app, ad esempio **App per sviluppatori** o **App di comunicazione**.
Quando si aggiunge un'app in Intune, è possibile selezionare la categoria desiderata. Usare gli argomenti specifici della piattaforma per aggiungere un'app e assegnare le categorie. Per creare e modificare le categorie, usare la procedura seguente:

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Installazione** > **Categorie di app**.
5. Nel pannello **Categorie di app** viene visualizzato un elenco delle categorie correnti. Scegliere una delle azioni seguenti:
    - **Creare una categoria**: nel pannello **Create category**(Crea categoria) immettere un nome per la nuova categoria. I nomi possono essere immessi in una sola lingua e non vengono tradotti da Intune. Al termine, fare clic su **Crea**.
    - **Modificare una categoria**: per qualsiasi categoria nell'elenco, scegliere "**...**". Nel pannello **Proprietà** è possibile immettere un nuovo nome per la categoria o eliminare la categoria.


## <a name="apps-added-automatically-by-intune"></a>App aggiunte automaticamente da Intune

Le app seguenti pubblicate da Microsoft vengono compilate in Intune e possono essere assegnate:

|||
|-|-|
|Nome|Piattaforma|Tipo di App|
|Azure Information Protection|Android|App di Android Store gestita|
|Dynamics CRM per telefoni|Android|App di Android Store gestita|
|Dynamics CRM per tablet|Android|App di Android Store gestita|
|Excel|iOS|App dello Store iOS gestita|
|Excel|Android|App di Android Store gestita|
|Managed Browser|Android|App di Android Store gestita|
|Managed Browser|iOS|App dello Store iOS gestita|
|Microsoft Dynamics CRM per telefoni|iOS|App dello Store iOS gestita|
|Microsoft Dynamics CRM per tablet|iOS|App dello Store iOS gestita|
|Microsoft Power BI|iOS|App dello Store iOS gestita|
|Microsoft Power BI|Android|App di Android Store gestita|
|Microsoft SharePoint|iOS|App dello Store iOS gestita|
|Microsoft SharePoint|Android|App di Android Store gestita|
|Microsoft Teams|Android|App di Android Store gestita|
|Microsoft Teams|iOS|App dello Store iOS gestita|
|OneDrive|iOS|App dello Store iOS gestita|
|OneDrive|Android|App di Android Store gestita|
|OneNote|iOS|App dello Store iOS gestita|
|Outlook|Android|App di Android Store gestita|
|Outlook|iOS|App dello Store iOS gestita|
|Outlook Groups|Android|App di Android Store gestita|
|Outlook Groups|iOS|App dello Store iOS gestita|
|PowerPoint|iOS|App dello Store iOS gestita|

