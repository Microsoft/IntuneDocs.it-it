---
title: Gestire le app acquistate con Volume Purchase Program iOS in Microsoft Intune
titlesuffix: ''
description: Informazioni su come sincronizzare le app acquistate con Volume Purchase Program dallo Store iOS in Microsoft Intune e su come gestirle e tenere traccia dell'utilizzo.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 848f76f61ebf85201af18ab019d0546e48fcaa41
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'App Store iOS consente di acquistare più licenze per un'app da eseguire nell'azienda. L'acquisto di più copie favorisce una gestione più efficiente delle app presenti in azienda.

Microsoft Intune consente di gestire più copie delle app acquistate con questo programma mediante:

- Segnalazione delle informazioni di licenza dall'App Store.
- Verifica del numero di licenze usate.
- Blocco dell'installazione di un numero di copie dell'app superiore al numero di copie acquistate.

È possibile usare due metodi per assegnare app acquistate con Volume Purchase Program:

### <a name="device-licensing"></a>Licenze per dispositivo

Quando si assegna un'app a un dispositivo, viene usata una licenza dell'app che rimane associata al dispositivo a cui è stata assegnata.

Quando si assegnano app acquistate con Volume Purchase Program a un dispositivo, l'utente finale del dispositivo non deve fornire un ID Apple per accedere allo store.

### <a name="user-licensing"></a>Licenze per utenti

Quando si assegna un'app a un utente, viene usata una licenza app che rimane associata all'utente. È possibile eseguire l'app su più dispositivi di proprietà dell'utente con un limite controllato da Apple.

Quando si assegna agli utenti un'app acquistata con Volume Purchase Program, ogni utente finale deve avere un ID Apple valido e univoco per accedere all'App Store.

È anche possibile usare Intune per sincronizzare, gestire e assegnare i libri acquistati nello Store Volume Purchase Program (VPP) di Apple. Per altre informazioni, vedere [Come gestire gli eBook iOS acquistati tramite Volume Purchase Program](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gestione delle app acquistate tramite Volume Purchase Program per dispositivi iOS

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>Supporta le app acquistate con Volume Purchase Program di Apple per i dispositivi iOS

È possibile acquistare più licenze per le app iOS tramite [Volume Purchase Program di Apple per le aziende](http://www.apple.com/business/vpp/) o [Volume Purchase Program di Apple per l'istruzione](http://volume.itunes.apple.com/us/store). Questo processo comporta la configurazione di un account VPP di Apple dal sito Web Apple e il caricamento del token VPP di Apple in Intune.  È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso delle app acquistate con VPP.

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>Supporta le app acquistate con volume Business-to-Business per dispositivi iOS

Anche gli sviluppatori di terze parti possono distribuire privatamente le app ai membri, indicati in iTunes Connect, di Volume Purchase Program per le aziende. I membri VPP per le aziende possono accedere a Volume Purchase Program App Store e acquistare le app. Le app VPP per le aziende acquistate dall'utente finale verranno sincronizzate con il proprio tenant Intune.

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare è necessario ottenere un token VPP da Apple e caricarlo nell'account di Intune. Tenere presenti anche i criteri che seguono:

* È possibile associare token VPP multipli all'account di Intune.
* Se in passato è stato usato un token VPP con un prodotto diverso, è necessario generare un nuovo token da usare con Intune.
* Ogni token è valido per un anno.
* Per impostazione predefinita, Intune esegue la sincronizzazione con il servizio VPP di Apple due volte al giorno. È possibile avviare una sincronizzazione manuale in qualsiasi momento.
* Prima di iniziare a usare VPP di Apple con Intune, rimuovere tutti gli account utente VPP esistenti creati con altri fornitori di soluzioni di gestione di dispositivi mobili (MDM). Intune non sincronizzerà tali account utente in Intune come misura di sicurezza. Intune sincronizza solo i dati del servizio VPP di Apple creati da Intune stesso.
* Intune supporta l'aggiunta di un numero massimo di 256 token VPP.
* Il programma DEP di Apple automatizza la registrazione per la gestione di dispositivi mobili (MDM). Con DEP è possibile configurare i dispositivi aziendali senza nemmeno toccarli. È possibile registrarsi al programma DEP con lo stesso account dell'agente del programma usato per VPP di Apple. L'ID del programma di distribuzione di Apple è univoco per i programmi elencati nel sito Web [Deployment Program di Apple](https://deploy.apple.com) e non può essere usato per accedere a servizi Apple quali iTunes store.
* Quando si assegnano le app VPP usando il modello di licenze utente a utenti o dispositivi (con l'affinità utente), ogni utente di Intune deve essere associato a un ID Apple univoco o a un indirizzo di posta elettronica quando accetta i Termini e condizioni Apple sul proprio dispositivo. Quando si configura un dispositivo per un nuovo utente di Intune, verificare di configurarlo con l'ID Apple univoco o l'indirizzo posta elettronica dell'utente. L'ID Apple o l'indirizzo di posta elettronica e l'utente di Intune formano una coppia di credenziali unica che può essere usata su un massimo di 5 dispositivi.
* Un token VPP è supportato per l'uso su un solo account Intune alla volta. Evitare di riusare lo stesso token VPP per più tenant Intune.
* Quando si assegnano le app VPP usando il modello di licenze utente a utenti o dispositivi (con l'affinità utente), ogni utente di Intune deve essere associato a un ID Apple univoco o a un indirizzo di posta elettronica quando accetta i Termini e condizioni Apple sul proprio dispositivo.
Quando si configura un dispositivo per un nuovo utente di Intune, verificare di configurarlo con l'ID Apple univoco o l'indirizzo posta elettronica necessario. L'ID Apple o l'indirizzo di posta elettronica e l'utente di Intune formano una coppia univoca che può essere usata in un massimo di 5 dispositivi.

>[!IMPORTANT]
>Dopo avere importato il token VPP in Intune, non importare lo stesso token in un'altra soluzione di gestione dei dispositivi. Questo potrebbe infatti causare la perdita di record relativi agli utenti e alle assegnazioni di licenze.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Per ottenere e caricare un token VPP di Apple

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
1.  Nel riquadro **Intune** scegliere **App per dispositivi mobili** > **Token VPP iOS** in **Installazione**.
2.  Nel riquadro di elenco dei token VPP selezionare **Crea**.
4. Nel riquadro **Creazione token VPP** specificare le informazioni seguenti:
    - **File del token VPP**: se l'operazione non è ancora stata eseguita, procedere all'iscrizione a Volume Purchase Program per le aziende o per l'istruzione. Dopo avere completato l'iscrizione, scaricare il token VPP di Apple per l'account e selezionarlo qui.
    - **ID Apple**: immettere l'ID Apple dell'account associato al Volume Purchase Program.
    - **Paese/area**: selezionare lo Store del paese VPP.  Intune sincronizza le app VPP per tutte le impostazioni locali dello Store del paese VPP specificato.
        > [!WARNING]  
        > Se si modifica il paese, i metadati delle app e l'URL dello Store saranno aggiornati durante la sincronizzazione successiva usando il servizio Apple per le app create con questo token. L'app non sarà aggiornata se non esiste nel nuovo Store del paese.

    - **Tipo di account VPP**: scegliere **Azienda** o **Istruzione**.
    - **Aggiornamenti automatici delle app**: scegliere da **On** a **Off** per abilitare gli aggiornamenti automatici. Una volta abilitati, Intune aggiornerà le app acquistate per il token specifico, quando il dispositivo è connesso, attraverso il servizio Intune.
Identifica gli aggiornamenti per le app VPP all'interno dell'app store e li invia automaticamente al dispositivo quando questo si connette.
4. Al termine, selezionare **Crea**.

Il token viene visualizzato nel riquadro di elenco dei token.

È possibile sincronizzare i dati archiviati da Apple con Intune in qualsiasi momento scegliendo **Sincronizza**.

## <a name="to-assign-a-volume-purchased-app"></a>Per assegnare un'app acquistata tramite Volume Purchase Program

1.  Nel riquadro **Intune** scegliere **App per dispositivi mobili** > **App** in **Gestisci**.
2.  Nel riquadro dell'elenco delle app scegliere l'app da assegnare e quindi scegliere **Assegnazioni**.
3.  Nel riquadro ***nome app*** - **Assegnazioni** scegliere **Aggiungi gruppo**, quindi nel riquadro **Aggiungi gruppo** scegliere un **Tipo di assegnazione** e scegliere i gruppi di utenti o di dispositivi Azure AD a cui assegnare l'app.
5.  Per ogni gruppo selezionato scegliere le impostazioni seguenti:
    - **Tipo**: decidere se l'app sarà **Disponibile** (gli utenti finali possono installare l'app dal Portale aziendale) o **Obbligatoria** (l'app sarà installata automaticamente nei dispositivi degli utenti finali).
    - **Tipo di licenza**: scegliere **Licenze utente** o **Licenze dispositivo**.
6.  Al termine, scegliere **Salva**.


>[!NOTE]
>L'elenco di app visualizzato è associato a un token. Se è presente un'app associata a più token VPP la stessa app viene visualizzata più volte, una volta per ogni token.

## <a name="end-user-prompts-for-vpp"></a>Richieste agli utenti finali di VPP

Agli utenti finali verrà richiesto di installare app VPP in numerosi scenari. Nella tabella seguente sono illustrate tutte le condizioni:

| # | Scenario                                | Invito al programma VPP di Apple                              | Richiesta di installazione app | Richiesta di ID Apple |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD: utente con licenza                             | S                                                                                               | S                                           | S                                 |
| 2 | Aziendale: utente con licenza (dispositivo senza supervisione)     | S                                                                                               | S                                           | S                                 |
| 3 | Aziendale: utente con licenza (dispositivo con supervisione)         | S                                                                                               | N                                           | S                                 |
| 4 | BYOD: dispositivo con licenza                           | N                                                                                               | S                                           | N                                 |
| 5 | Aziendale: dispositivo con licenza (dispositivo senza supervisione)                           | N                                                                                               | S                                           | N                                 |
| 6 | Aziendale: dispositivo con licenza (dispositivo con supervisione)                           | N                                                                                               | N                                           | N                                 |
| 7 | Modalità tutto schermo (dispositivo con supervisione): dispositivo con licenza | N                                                                                               | N                                           | N                                 |
| 8 | Modalità tutto schermo (dispositivo con supervisione): utente con licenza   | --- | ---                                          | ---                                |

> [!Note]  
> Non è consigliabile assegnare app VPP a dispositivi in modalità tutto schermo usando la licenza utente VPP.

## <a name="revoking-app-licenses-and-deleting-tokens"></a>Revoca delle licenze delle app ed eliminazione dei token 

<!-- 820863 -->  
Per un dispositivo specifico con una o più app Volume Purchase Program (VPP) iOS, è necessario revocare tutte le licenze per app basate su dispositivo associate al dispositivo stesso. La revoca di una licenza per app non comporterà la disinstallazione dell'app VPP correlata dal dispositivo. Per disinstallare un'app VPP e revocare una licenza, è necessario modificare il tipo di assegnazione dell'app VPP in **Disinstalla**. Se si rimuove un'app assegnata a un utente, Intune recupera la licenza per l'utente o il dispositivo e disinstalla l'app dal dispositivo.

>[!NOTE]
>Intune recupererà tutte le licenze delle app VPP per iOS concesse agli utenti quando un dipendente lascia l'azienda e non fa più parte dei gruppi di AAD.

<!-- 820879 -->  
È possibile eliminare un token Volume Purchasing Program (VPP) iOS tramite la console. Ciò potrebbe risultare necessario in presenza di istanze duplicate di un token VPP. L'eliminazione di un token eliminerà anche le eventuali app associate e l'assegnazione. Tuttavia, l'eliminazione di un token non comporta la revoca delle licenze per le app o la disinstallazione di app. 

>[!NOTE]
>Intune non può revocare le licenze delle app dopo l'eliminazione di un token. 

<!-- 820870 -->  
Per revocare la licenza di tutte le app VPP per un token VPP specificato, è prima di tutto necessario revocare tutte le licenze di app associate al token e quindi eliminare il token.

## <a name="further-information"></a>Altre informazioni

Quando un utente con un dispositivo idoneo prova a installare per la prima volta un'app VPP riceve una richiesta di partecipazione al programma Volume Purchase Program di Apple. Per procedere con l'installazione dell'app l'utente deve confermare la partecipazione. L'invito a partecipare al Volume Purchase Program di Apple richiede che l'utente possa usare l'app iTunes nel dispositivo iOS. Se sono stati impostati criteri per disabilitare l'app iTunes Store, le licenze basate sugli utenti per le app VPP non funzionano. La soluzione consiste nel consentire l'app iTunes rimuovendo i criteri oppure nell'usare licenze basate sui dispositivi.

## <a name="frequently-asked-questions"></a>Domande frequenti

#### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Quanto tempo è necessario per aggiornare il conteggio delle licenze nel portale dopo che un'app è stata installata o rimossa dal dispositivo?
La licenza viene aggiornata entro poche ore dall'installazione o dalla disinstallazione di un'app. Si noti che se l'utente finale rimuove l'app dal dispositivo, la licenza rimane assegnata all'utente o al dispositivo.

#### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>È possibile sottoscrivere più della disponibilità effettiva di licenze per un'app e, in caso affermativo, in quali casi?
Sì. L'amministratore di Intune può sottoscrivere più della disponibilità effettiva di licenze per un'app. Ad esempio, nel caso in cui l'amministratore acquisti 100 licenze per l'app XYZ e quindi decida di destinare l'app a un gruppo di 500 membri. I primi 100 membri (utenti o dispositivi) otterranno la licenza a essi assegnata mentre per il resto dei membri l'assegnazione della licenza non riuscirà.

#### <a name="i-understand-intune-automatically-syncs-app-licenses-each-day-with-apple-is-that-correct"></a>Intune sincronizza automaticamente le licenze delle app con Apple ogni giorno. È corretto?
Intune sincronizza le licenze delle app con Apple ogni 15 ore.

## <a name="next-steps"></a>Passaggi successivi

Vedere [How to monitor apps](apps-monitor.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni di app.
