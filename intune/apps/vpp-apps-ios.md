---
title: Gestire app acquistate con Volume Purchase Program di Apple
titleSuffix: Microsoft Intune
description: Informazioni su come sincronizzare le app acquistate con Volume Purchase Program da App Store iOS e macOS in Microsoft Intune e su come gestirle e tenere traccia dell'utilizzo.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0bc511669ec8a88523581b3afbcca161d5208934
ms.sourcegitcommit: de663ef5f3e82e0d983899082a7f5b62c63f24ef
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "75956214"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Procedura per la gestione delle app iOS e macOS acquistate tramite Volume Purchase Program di Apple con Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple consente di acquistare più licenze per un'app da usare nell'organizzazione nei dispositivi iOS e macOS con [Apple Business Manager](https://business.apple.com/) o [Apple School Manager](https://school.apple.com/). È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso delle app acquistate con VPP. L'acquisto di licenze per le app consente di gestire in modo efficiente le app nell'azienda e di mantenere la proprietà e il controllo delle app acquistate. 

Microsoft Intune consente di gestire le app acquistate con questo programma:

- Sincronizzando i token di percorso scaricati da Apple Business Manager.
- Verificando il numero di licenze disponibili e usate per le app acquistate.
- Supportando l'installazione di app fino al numero di licenze di cui si è proprietari.

È anche possibile sincronizzare, gestire e assegnare i libri acquistati da Apple Business Manager con Intune in dispositivi iOS. Per altre informazioni, vedere [Come gestire gli eBook iOS acquistati tramite Volume Purchase Program](vpp-ebooks-ios.md).

## <a name="what-are-location-tokens"></a>Che cosa sono i token di percorso?
I token di percorso sono noti anche come token VPP (Volume Purchase Program) e vengono usati per assegnare e gestire le licenze acquistate usando Apple Business Manager. I responsabili della gestione del contenuto possono acquistare e associare le licenze con i token di percorso per i quali hanno un'autorizzazione in Apple Business Manager. I token di percorso vengono quindi scaricati da Apple Business Manager e caricati in Microsoft Intune. Microsoft Intune supporta il caricamento di più token di percorso per ogni tenant. Ogni token è valido per un anno.

## <a name="how-are-purchased-apps-licensed"></a>Come vengono concesse in licenza le app acquistate?
Le app acquistate possono essere assegnate a gruppi usando due tipi di licenze offerte da Apple per i dispositivi iOS e macOS.

|   | Licenze dispositivo | Licenze utente |
|-----|------------------|----------------|
| **Accesso all'App Store** | Non obbligatorio. | Ogni utente finale deve usare un ID Apple univoco quando viene richiesto di accedere all'App Store. |
| **Configurazione del dispositivo che blocca l'accesso all'App Store** | Le app possono essere installate e aggiornate usando il Portale aziendale. | L'invito a partecipare ad Apple VPP richiede l'accesso all'App Store. Se sono stati impostati criteri per disabilitare l'App Store, le licenze utente per le app VPP non funzionano. |
| **Aggiornamento automatico delle app** | Configurato dall'amministratore di Intune nelle impostazioni del token VPP Apple in cui il **tipo di assegnazione** dell'app è **obbligatorio**. <br> <br> Se il **tipo di assegnazione** è **disponibile per i dispositivi registrati**, gli aggiornamenti delle app disponibili possono essere installati dal Portale aziendale. | Configurato dall'utente finale nelle impostazioni personali dell'App Store. Questa opzione non può essere gestita dall'amministratore di Intune. |
| **Registrazione utenti** | Non supportata. | Supportata se si usano ID Apple gestiti. |
| **Documentazione** | Non supportata. | Supportata. |
| **Licenze usate** | 1 licenza per dispositivo. La licenza è associata al dispositivo. | 1 licenza per un massimo di 5 dispositivi che usano lo stesso ID Apple personale. La licenza è associata all'utente. <br> <br> Un utente finale associato a un ID Apple personale e a un ID Apple gestito in Intune usa 2 licenze per le app.|
| **Migrazione delle licenze** | La migrazione delle app può essere eseguita automaticamente dalle licenze utente alle licenze dispositivo. | Non è possibile eseguire la migrazione delle app dalle licenze dispositivo alle licenze utente. |

> [!NOTE]  
> Nel Portale aziendale non sono visualizzate le app con licenza dispositivo per i dispositivi di registrazione utente perché solo le app con licenza utente possono essere installate nei dispositivi di registrazione utente.

## <a name="what-app-types-are-supported"></a>Quali tipi di app sono supportati?
È possibile acquistare e distribuire app pubbliche e private usando Apple Business Manager.
- **App Store:** Con Apple Business Manager, i responsabili della gestione del contenuto possono acquistare le app sia gratuite che a pagamento disponibili nell'App Store.
- **App personalizzate:** Con Apple Business Manager, i responsabili della gestione del contenuto possono acquistare anche le app personalizzate rese disponibili privatamente per l'organizzazione. Queste app sono personalizzate in base alle esigenze specifiche dell'organizzazione dagli sviluppatori che lavorano direttamente con l'utente. Altre informazioni su [come distribuire le app personalizzate](https://developer.apple.com/business/custom-apps/).

## <a name="prerequisites"></a>Prerequisiti
- Un account di [Apple Business Manager](https://business.apple.com/) o [Apple School Manager](https://school.apple.com/) per l'organizzazione. 
- Sono state acquistate le licenze delle app assegnate a uno o più token di percorso. 
- Sono stati scaricati i token di percorso. 

> [!IMPORTANT]
> - Un token di percorso può essere usato solo con una soluzione di gestione dei dispositivi alla volta. Prima di iniziare a usare le app acquistate con Intune, revocare e rimuovere tutti i token di percorso esistenti usati con altri fornitori di soluzioni di gestione dei dispositivi mobili (MDM). 
> - Un token di percorso è supportato solo per l'uso in un tenant Intune alla volta. Evitare di riusare lo stesso token per più tenant Intune.
> - Per impostazione predefinita, Intune sincronizza i token di percorso con Apple due volte al giorno. È possibile avviare una sincronizzazione manuale da Intune in qualsiasi momento.
> - Dopo avere importato il token di percorso in Intune, non importare lo stesso token in un'altra soluzione di gestione dei dispositivi. Questo potrebbe infatti causare la perdita di record relativi agli utenti e alle assegnazioni di licenze.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>Eseguire la migrazione da Volume Purchase Program (VPP) ad App e libri
Se non è ancora stata eseguita la migrazione dell'organizzazione ad Apple Business Manager o Apple School Manager, consultare le [indicazioni di Apple sulla migrazione ad App e libri](https://support.apple.com/HT208257) prima di procedere con la gestione delle app acquistate in Intune.

> [!IMPORTANT]
> - Per una migliore esperienza di migrazione, eseguire la migrazione di un solo acquirente VPP per percorso. Se tutti gli acquirenti eseguono la migrazione in un unico percorso, tutte le licenze, assegnate e non assegnate, passeranno ad App e libri.
> - Non eliminare il token VPP legacy esistente in Intune o le app e le assegnazioni associate al token VPP legacy esistente in Intune. Queste azioni richiedono che tutte le assegnazioni di app in Intune vengano ricreate.

Eseguire la migrazione del contenuto e dei token VPP acquistati ad App e libri in Apple Business Manager o Apple School Manager come indicato di seguito:

1. Invitare gli acquirenti VPP a partecipare all'organizzazione e invitare ogni utente a selezionare un percorso univoco. 
2. Verificare che tutti gli acquirenti VPP all'interno dell'organizzazione abbiano completato il passaggio 1 prima di continuare.
3. Verificare che sia stata eseguita la migrazione di tutte le app e le licenze acquistate ad App e libri in Apple Business Manager o Apple School Manager.
4. Per scaricare il nuovo token di percorso, passare a **Apple Business (o School) Manager** > **Impostazioni** > **App e libri** > **My Server Tokens** (Token server personali).
5. Per aggiornare il token di percorso nell'interfaccia di amministrazione di Microsoft Endpoint Manager, passare a **Amministrazione del tenant** > **Connettori e token** > **Token VPP Apple** e sincronizzare il token.

## <a name="upload-an-apple-vpp-or-location-token"></a>Caricare un token VPP o di percorso di Apple

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Token VPP Apple**.
4. Nel riquadro di elenco dei token VPP selezionare **Crea**.
5. Nel riquadro **Creazione token VPP** specificare le informazioni seguenti:
    - **File del token VPP**: se non è già stato fatto, iscriversi ad Apple Business Manager o Apple School Manager. Dopo avere completato l'iscrizione, scaricare il token VPP di Apple per l'account e selezionarlo qui.
    - **ID Apple**: immettere l'ID Apple gestito dell'account associato al token caricato.
    - **Ottenere il controllo del token da un altro software MDM**: se si imposta questa opzione su **Sì** il token può essere riassegnato a Intune da un'altra soluzione MDM.
    - **Nome del token**: campo per l'impostazione del nome del token.    
    - **Paese o area geografica**: selezionare lo Store del paese o dell'area geografica VPP.  Intune sincronizza le app VPP per tutte le impostazioni locali dello Store VPP del paese/dell'area specificato.
        > [!WARNING]  
        > Se si modifica il paese o l'area geografica, i metadati delle app e l'URL dell'App Store verranno aggiornati durante la sincronizzazione successiva usando il servizio Apple per le app create con questo token. L'app non verrà aggiornata se non è presente nel nuovo Store del paese o dell'area geografica.

    - **Tipo di account VPP**: scegliere **Azienda** o **Istruzione**.
    - **Aggiornamenti automatici delle app**: scegliere da **On** o **Off** per abilitare gli aggiornamenti automatici. Quando è abilitato, Intune rileva gli aggiornamenti delle app VPP nell'App Store e li invia automaticamente al dispositivo quando questo si connette. 
        
        > [!NOTE] 
        > Gli aggiornamenti automatici delle app per le app VPP di Apple aggiorneranno automaticamente solo le app distribuite con la finalità di installazione **Richiesto**. Per le app distribuite con la finalità di installazione **Disponibile**, l'aggiornamento automatico genera un messaggio di stato per l'amministratore IT e lo informa che è disponibile una nuova versione dell'app. Per visualizzare questo messaggio, selezionare l'app, selezionare Stato dell'installazione del dispositivo e controllare Dettagli stato.  

    - **Concedo a Microsoft l'autorizzazione a inviare informazioni su utente e dispositivo ad Apple.** - È necessario selezionare **Accetto** per continuare. Per esaminare i dati inviati da Microsoft ad Apple, vedere [Dati inviati da Intune ad Apple](~/protect/data-intune-sends-to-apple.md).

6. Al termine, selezionare **Crea**. Il token viene visualizzato nel riquadro di elenco dei token.

## <a name="synchronize-a-vpp-token"></a>Sincronizzare un token VPP
È possibile sincronizzare i nomi delle app, i metadati e le informazioni di licenza per le app acquistate in Intune scegliendo **Sincronizzazione** per un token selezionato.

## <a name="assign-a-volume-purchased-app"></a>Assegnare un'app acquistata con Volume Purchase Program

1. Selezionare **App** > **Tutte le app**.
2. Nel riquadro dell'elenco delle app scegliere l'app da assegnare e quindi scegliere **Assegnazioni**.
3. Nel riquadro **nome app** - **Assegnazioni** scegliere **Aggiungi gruppo**, quindi nel riquadro **Aggiungi gruppo** scegliere un **Tipo di assegnazione** e scegliere i gruppi di utenti o di dispositivi Azure AD a cui assegnare l'app.
5. Per ogni gruppo selezionato scegliere le impostazioni seguenti:
    - **Tipo**: decidere se l'app sarà **Disponibile** (gli utenti finali possono installare l'app dal Portale aziendale) o **Obbligatoria** (l'app sarà installata automaticamente nei dispositivi degli utenti finali).
    - **Tipo di licenza**: scegliere **Licenze utente** o **Licenze dispositivo**.
6. Al termine, scegliere **Salva**.


>[!NOTE]
>La finalità della distribuzione in base alla disponibilità non è supportata per i gruppi di dispositivi, ma solo per i gruppi di utenti. L'elenco di app visualizzato è associato a un token. Se è presente un'app associata a più token VPP la stessa app viene visualizzata più volte, una volta per ogni token.

## <a name="end-user-prompts-for-vpp"></a>Richieste agli utenti finali di VPP

Agli utenti finali verrà richiesto di installare app VPP in numerosi scenari. Nella tabella seguente sono illustrate tutte le condizioni:

| # | Scenario                                | Invito al programma VPP di Apple                              | Richiesta di installazione app | Richiesta di ID Apple |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD: utente con licenza (dispositivo senza registrazione utente)                             | S                                                                                               | S                                           | S                                 |
| 2 | Aziendale: utente con licenza (dispositivo senza supervisione)     | S                                                                                               | S                                           | S                                 |
| 3 | Aziendale: utente con licenza (dispositivo con supervisione)         | S                                                                                               | N                                           | S                                 |
| 4 | BYOD: dispositivo con licenza                           | N                                                                                               | S                                           | N                                 |
| 5 | Aziendale: dispositivo con licenza (dispositivo senza supervisione)                           | N                                                                                               | S                                           | N                                 |
| 6 | Aziendale: dispositivo con licenza (dispositivo con supervisione)                           | N                                                                                               | N                                           | N                                 |
| 7 | Modalità tutto schermo (dispositivo con supervisione): dispositivo con licenza | N                                                                                               | N                                           | N                                 |
| 8 | Modalità tutto schermo (dispositivo con supervisione): utente con licenza   | --- | ---                                          | ---                                |

> [!Note]  
> Non è consigliabile assegnare app VPP a dispositivi in modalità tutto schermo usando la licenza utente.

## <a name="revoking-app-licenses"></a>Revoca delle licenze delle app

È possibile revocare tutte le licenze di app iOS o macOS associate al Volume Purchase Program in base a un determinato dispositivo, utente o app.  Esistono tuttavia alcune differenze tra le piattaforme iOS e macOS. 

|   | iOS | macOS |
|-----|------------------|----------------|
| **Rimuovere l'assegnazione dell'app** | Quando si rimuove un'app assegnata a un utente, Intune recupera la licenza per l'utente o il dispositivo e disinstalla l'app dal dispositivo. | Quando si rimuove un'app assegnata a un utente, Intune recupera la licenza utente o dispositivo. L'app non viene disinstallata dal dispositivo. |
| **Revocare la licenza dell'app** | Se revocata, la licenza dell'app per l'utente o il dispositivo viene recuperata. Per rimuovere l'app dal dispositivo, è necessario modificare l'assegnazione in **Disinstalla**. | Se revocata, la licenza dell'app per l'utente o il dispositivo viene recuperata. Un'app macOS con licenza revocata rimane utilizzabile nel dispositivo, ma può essere aggiornata solo quando viene riassegnata una licenza all'utente o al dispositivo. Secondo Apple, un'app che si trova in questa condizione viene rimossa dopo un periodo di tolleranza di 30 giorni. Apple, tuttavia, non offre a Intune il modo di rimuovere l'app usando l'azione di assegnazione Disinstalla.

>[!NOTE]
> - Intune recupera le licenze delle app quando un dipendente lascia l'azienda e non fa più parte dei gruppi di AAD.
> - Quando si assegna un'app acquistata con finalità **Disinstalla**, Intune recupera la licenza e disinstalla l'app.
> - Le licenze dell'app non vengono recuperate se un dispositivo viene rimosso dalla gestione di Intune. 

## <a name="deleting-vpp-tokens"></a>Eliminazione di token VPP
<!-- 820879 -->  
È possibile eliminare un token Volume Purchasing Program (VPP) di Apple tramite la console. Ciò potrebbe risultare necessario in presenza di istanze duplicate di un token VPP. L'eliminazione di un token eliminerà anche le eventuali app associate e l'assegnazione. Tuttavia, l'eliminazione di un token non comporta la revoca delle licenze per le app o la disinstallazione di app. 

>[!NOTE]
>Intune non può revocare le licenze delle app dopo l'eliminazione di un token. 

<!-- 820870 -->  
Per revocare la licenza di tutte le app VPP per un token VPP specificato, è prima di tutto necessario revocare tutte le licenze di app associate al token e quindi eliminare il token.

## <a name="renewing-app-licenses"></a>Rinnovo delle licenze delle app

È possibile rinnovare un token VPP Apple scaricando un nuovo token da Apple Business Manager o Apple School Manager e aggiornando il token esistente in Intune.

## <a name="deleting-a-vpp-app"></a>Eliminazione di un'app VPP

Attualmente, non è possibile eliminare un'app VPP per iOS da Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Assegnazione di autorizzazioni a ruoli personalizzati per VPP

È possibile controllare l'accesso ai token VPP e alle app VPP di Apple in modo indipendente usando le autorizzazioni assegnate ai ruoli di amministratore personalizzati in Intune.

* Per consentire a un ruolo personalizzato di Intune di gestire i token VPP di Apple, in **App** > **Token VPP Apple** assegnare le autorizzazioni per **App gestite**.
* Per consentire a un ruolo personalizzato di Intune di gestire le app acquistate tramite token VPP iOS, in **App** > **Tutte le app** assegnare le autorizzazioni per **App per dispositivi mobili**. 

## <a name="additional-information"></a>Informazioni aggiuntive

Apple offre assistenza diretta per creare e rinnovare i token VPP. Per altre informazioni, vedere [Distribuire contenuti agli utenti con il Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661). 

Se nel portale di Intune è indicato **Assegnata a MDM esterno** l'amministratore deve rimuovere il token VPP dall'MDM di terze parti prima di usare il token VPP in Intune.

## <a name="frequently-asked-questions"></a>Domande frequenti

### <a name="how-many-tokens-can-i-upload"></a>Quanti token si possono caricare?
È possibile caricare fino a 3.000 token in Intune.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Quanto tempo è necessario per aggiornare il conteggio delle licenze nel portale dopo che un'app è stata installata o rimossa dal dispositivo?
La licenza viene aggiornata entro poche ore dall'installazione o dalla disinstallazione di un'app. Si noti che se l'utente finale rimuove l'app dal dispositivo, la licenza rimane assegnata all'utente o al dispositivo.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>È possibile sottoscrivere più della disponibilità effettiva di licenze per un'app e, in caso affermativo, in quali casi?
Sì. L'amministratore di Intune può sottoscrivere più della disponibilità effettiva di licenze per un'app. Ad esempio, nel caso in cui l'amministratore acquisti 100 licenze per l'app XYZ e quindi decida di destinare l'app a un gruppo di 500 membri. I primi 100 membri (utenti o dispositivi) otterranno la licenza a essi assegnata mentre per il resto dei membri l'assegnazione della licenza non riuscirà.


## <a name="next-steps"></a>Passaggi successivi

Vedere [How to monitor apps](apps-monitor.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni di app.

Vedere [How to troubleshoot apps](~/apps/troubleshoot-app-install.md) (Come risolvere i problemi delle app) per informazioni sulla risoluzione dei problemi relativi alle app.
