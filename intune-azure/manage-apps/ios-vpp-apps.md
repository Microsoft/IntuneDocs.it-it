---
title: Manage iOS apps you purchased through a volume-purchase program with Microsoft Intune (Gestire le app iOS acquistate tramite Volume Purchase Program con Microsoft Intune)
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: Informazioni su come sincronizzare le app acquistate con Volume Purchase Program dallo Store di iOS in Intune e su come gestirle e tenere traccia del relativo uso.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: ff43a0be6ebc124bb7e52e5be31e89985ce32166
ms.contentlocale: it-it
ms.lasthandoff: 04/24/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Come gestire le app iOS acquistate tramite Volume Purchase Program con Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

L'App Store iOS consente di acquistare più licenze per un'app da eseguire nell'azienda. In questo modo, è possibile ridurre il carico amministrativo associato al monitoraggio di più copie delle app acquistate.

Microsoft Intune semplifica la gestione delle app acquistate con questo programma importando le informazioni di licenza dall'App Store, verificando il numero di licenze usate e impedendo l'installazione di più copie dell'app rispetto a quelle possedute.

È anche possibile usare Intune per sincronizzare, gestire e assegnare agli utenti i libri acquistati nello store Apple Volume Purchase Program. Per la gestione dei libri, usare il carico di lavoro **Libri** del portale di Intune. Le procedure per la gestione dei libri sono uguali a quelle usate per la gestione delle app.
Per eseguire questa operazione è necessario avere un token Apple Volume Purchase Program. Attualmente, è possibile assegnare libri solo con la modalità di installazione **Richiesto**.
Quando si assegna un libro a un dispositivo, nel dispositivo deve essere installata l'app predefinita iBooks. In caso contrario l'utente dovrà reinstallare l'app per leggere il libro. Attualmente non è possibile usare Intune per ripristinare le app predefinite rimosse.


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gestione delle app acquistate tramite Volume Purchase Program per dispositivi iOS
Acquistare più licenze per le app iOS tramite [Apple Volume Purchase Program per le aziende](http://www.apple.com/business/vpp/) o [Apple Volume Purchase Program per l'istruzione](http://volume.itunes.apple.com/us/store). A questo scopo, configurare un account VPP di Apple dal sito Web Apple e caricare il token VPP di Apple in Intune.  È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso delle app acquistate con VPP.

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare, è necessario ottenere un token VPP da Apple e caricarlo nell'account di Intune. Tenere anche presente quanto segue:

* È possibile associare più token Volume Purchase Program con l'account di Intune.
* Se in passato è stato usato un token VPP con un prodotto diverso, è necessario generare un nuovo token da usare con Intune.
* Ogni token è valido per un anno.
* Per impostazione predefinita, Intune esegue la sincronizzazione con il servizio VPP di Apple due volte al giorno. È possibile avviare una sincronizzazione manuale in qualsiasi momento.
* Dopo avere importato il token VPP in Intune, non importare lo stesso token in un'altra soluzione di gestione dei dispositivi. Questo potrebbe infatti causare la perdita di record relativi agli utenti e alle assegnazioni di licenze.
* Prima di iniziare a usare VPP iOS con Intune, rimuovere tutti gli account utente VPP esistenti creati con altri fornitori di soluzioni di gestione dei dispositivi mobili (MDM). Intune non sincronizzerà tali account utente in Intune come misura di protezione. Intune sincronizza solo i dati dal servizio VPP di Apple creati da Intune stesso.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Per ottenere e caricare un token VPP di Apple

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
1.  Nel carico di lavoro di **App per dispositivi mobili** scegliere **Installazione** > **Token VPP iOS**.
2.  Nel pannello di elenco dei token VPP fare clic su **Aggiungi**.
3.  Nel pannello Nuovo token VPP specificare le informazioni seguenti:
    - **File del token VPP**: procedere all'iscrizione per Volume Purchase Program per le aziende o Volume Purchase Program per l'istruzione, se questa operazione non è stata ancora eseguita. Dopo avere completato l'iscrizione, scaricare il token VPP di Apple per l'account e selezionarlo qui.
    - **ID Apple**: immettere l'ID Apple dell'account associato al Volume Purchase Program.
    - **Tipo di account VPP**: scegliere **Azienda** o **Istruzione**.
4. Al termine, fare clic su **Carica**.

Il token viene visualizzato nel pannello di elenco dei token.


È possibile sincronizzare i dati archiviati da Apple con Intune in qualsiasi momento scegliendo **Sincronizza**.

## <a name="to-assign-a-volume-purchased-app"></a>Per assegnare un'app acquistata tramite Volume Purchase Program

1. Nel carico di lavoro di **App per dispositivi mobili** scegliere **Gestisci** > **App con licenza**.
2. Nel pannello di elenco delle app scegliere l'app da assegnare e quindi scegliere "**...** " > **Assegna gruppi**.
3. Nel pannello <*Nome app*> - **Gruppi assegnati** scegliere **Gestisci** > **Gruppi assegnati**.
4. Scegliere **Assegna gruppi** e quindi nel pannello **Seleziona gruppi** scegliere i gruppi di utenti o di dispositivi Azure AD a cui assegnare l'app.
È necessario scegliere un'azione di assegnazione **obbligatoria**. Inoltre, le assegnazioni ai gruppi di dispositivi sono disponibili per i nuovi tenant creati dopo il mese di gennaio 2017. Se il tenant è stato creato prima di questa data e non è possibile assegnare le app VPP ai gruppi di dispositivi, contattare il supporto tecnico di Intune.
5. Al termine, scegliere **Salva**.

Vedere [How to monitor apps](monitor-apps.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni di app.

## <a name="further-information"></a>Altre informazioni

Quando si assegna l'app indicando l'installazione come **Obbligatoria**, ogni utente che installa l'app usa una licenza.

Per revocare una licenza, è necessario modificare l'azione di assegnazione specificando **Disinstalla**. La licenza verrà revocata una volta disinstallata l'app.

La prima volta che un utente con un dispositivo idoneo tenta di installare un'app VPP gli viene richiesto di partecipare al programma Volume Purchase Program di Apple. È necessario completare questo passaggio per poter proseguire l'installazione dell'app.

Quando si distribuisce un'app VPP come Disponibile, il contenuto e la licenza dell'app vengono distribuiti direttamente dall'App Store.

