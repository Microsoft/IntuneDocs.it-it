---
title: Gestire gli eBook iOS/iPadOS acquistati con Volume Purchase Program
titleSuffix: Microsoft Intune
description: Informazioni su come sincronizzare i libri acquistati con Volume Purchase Program dallo Store iOS in Intune e su come gestirli e tenere traccia dell'utilizzo.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7c2bd0603961b9d618b3f743ecb323fb7fc9823
ms.sourcegitcommit: ecaff388038fb800f2e646f8efcf8f3b1e2fd1b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/18/2020
ms.locfileid: "77437869"
---
# <a name="how-to-manage-iosipados-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Come gestire gli eBook iOS/iPadOS acquistati usando Volume Purchase Program con Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple Volume Purchase Program (VPP) consente di acquistare più licenze per un libro, da distribuire agli utenti aziendali. È possibile distribuire libri dagli store per le aziende o l'istruzione.

Microsoft Intune consente di sincronizzare, gestire e assegnare i libri acquistati tramite questo programma. È possibile importare le informazioni di licenza dallo store e tenere traccia del numero di licenze usate.

Le procedure per la gestione dei libri sono simili a quelle per la [gestione delle app VPP](../vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Gestire i libri acquistati tramite Volume Purchase Program per dispositivi iOS
È possibile acquistare più licenze per libri iOS/iPadOS con [Volume Purchase Program di Apple per le aziende](https://www.apple.com/business/vpp/) o [Volume Purchase Program di Apple per l'istruzione](https://volume.itunes.apple.com/us/store). Questo processo comporta la configurazione di un account VPP di Apple dal sito Web Apple e il caricamento del token VPP di Apple in Intune.  È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso dei libri acquistati con VPP.

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare, ottenere un token VPP da Apple e caricarlo nell'account di Intune. Inoltre:

* Se in passato è stato usato un token VPP con un prodotto diverso, è necessario generare un nuovo token da usare con Intune.
* Ogni token è valido per un anno.
* Per impostazione predefinita, Intune esegue la sincronizzazione con il servizio VPP di Apple due volte al giorno. È possibile avviare una sincronizzazione manuale in qualsiasi momento.
* Dopo avere importato il token VPP in Intune, non importare lo stesso token in un'altra soluzione di gestione dei dispositivi. Questo potrebbe infatti causare la perdita di record relativi agli utenti e alle assegnazioni di licenze.
* Prima di iniziare a usare i libri iOS/iPadOS con Intune, rimuovere tutti gli account utente VPP esistenti creati con altri fornitori di soluzioni di gestione dei dispositivi mobili (MDM). Intune non sincronizzerà tali account utente in Intune come misura di sicurezza. Intune sincronizza solo i dati dal servizio VPP di Apple creati da Intune stesso.
* Quando si assegna un libro a un dispositivo, nel dispositivo deve essere installata l'app predefinita iBooks. In caso contrario l'utente finale deve reinstallare l'app prima di poter leggere il libro. Attualmente non è possibile usare Intune per ripristinare le app predefinite rimosse.
* È possibile assegnare libri solo dal sito Volume Purchase Program di Apple. Non è possibile caricare e quindi assegnare libri creati internamente.
* Attualmente non è consentita l'assegnazione di libri a categorie di utenti finali, come per le app.
* Non è possibile recuperare una licenza dopo aver assegnato il libro.
* La prima volta che un utente con un dispositivo idoneo tenta di installare un libro VPP dovrà confermare la partecipazione al programma Volume Purchase Program di Apple prima di poter installare un libro. È anche possibile assegnare licenze a gruppi di sicurezza con ID Apple gestiti. In questo caso, agli utenti non viene richiesto l'ID Apple al momento dell'installazione di un libro.
* I dispositivi devono essere registrati con affinità utente, dato che i libri possono essere assegnati solo a gruppi di utenti.   


## <a name="to-get-and-upload-an-apple-vpp-token"></a>Per ottenere e caricare un token VPP di Apple

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Token VPP Apple**.
3. Nel riquadro di elenco dei token VPP fare clic su **Crea**.
5. Nella pagina **Nuovo token VPP** specificare le informazioni seguenti:
    - **File del token VPP**: assicurarsi di avere completato l'iscrizione a Volume Purchase Program per le aziende o Volume Purchase Program per l'istruzione. Scaricare poi il token VPP di Apple per l'account e selezionarlo qui.
    - **ID Apple**: immettere l'ID Apple dell'account associato al Volume Purchase Program.
    - **Tipo di account VPP**: scegliere **Azienda** o **Istruzione**.
5. Al termine, fare clic su **Crea**.

Il token viene visualizzato nel riquadro di elenco dei token.


È possibile sincronizzare i dati archiviati da Apple con Intune in qualsiasi momento scegliendo **Sincronizza**.

## <a name="to-assign-a-volume-purchased-app"></a>Per assegnare un'app acquistata tramite Volume Purchase Program

1. Selezionare **App** > **eBook** > **Tutti gli eBook**.
2. Nel riquadro di elenco dei libri scegliere il libro da assegnare e quindi scegliere ' **...** ' > **Assegna gruppi**.
3. Nel riquadro <*nome libro*> - **Gruppi assegnati** scegliere **Gestisci** > **Gruppi assegnati**.
4. Scegliere **Assegna gruppi** e quindi nel riquadro **Seleziona gruppi** scegliere i gruppi di utenti di Azure AD a cui assegnare il libro. I gruppi di dispositivi non sono attualmente supportati.
È necessario scegliere un'azione di assegnazione **Disponibile** o **Obbligatoria**. 
5. Al termine, scegliere **Salva**.

## <a name="next-steps"></a>Passaggi successivi

Vedere [How to monitor apps](apps-monitor.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni dei libri.






