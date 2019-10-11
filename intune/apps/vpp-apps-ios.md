---
title: Gestire app acquistate con Volume Purchase Program di Apple
titleSuffix: Microsoft Intune
description: Informazioni su come sincronizzare le app acquistate con Volume Purchase Program da App Store iOS e macOS in Microsoft Intune e su come gestirle e tenere traccia dell'utilizzo.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dac7069e30c173d80f15977ba2f06fcabcb7179b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724438"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Procedura per la gestione delle app iOS e macOS acquistate tramite Volume Purchase Program di Apple con Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple consente di acquistare più licenze per le app da eseguire nell'azienda in dispositivi iOS e macOS. L'acquisto di più copie favorisce una gestione più efficiente delle app presenti in azienda.

Microsoft Intune consente di gestire più copie delle app acquistate con questo programma mediante:

- Segnalazione delle informazioni di licenza dall'App Store.
- Verifica del numero di licenze usate.
- Blocco dell'installazione di un numero di copie dell'app superiore al numero di copie acquistate.

È possibile usare due metodi per assegnare app acquistate con Volume Purchase Program:

## <a name="device-licensing"></a>Licenze per dispositivo

Quando si assegna un'app a un dispositivo, viene usata una licenza dell'app che rimane associata al dispositivo a cui è stata assegnata.

Quando si assegnano app acquistate con Volume Purchase Program a un dispositivo, l'utente finale del dispositivo non deve fornire un ID Apple per accedere allo store.

## <a name="user-licensing"></a>Licenze per utenti

Quando si assegna un'app a un utente, viene usata una licenza app che rimane associata all'utente. È possibile eseguire l'app in un massimo di cinque dispositivi di proprietà dell'utente. Il limite del numero di dispositivi è controllato da Apple.

Quando si assegna agli utenti un'app acquistata con Volume Purchase Program, ogni utente finale deve avere un ID Apple valido e univoco per accedere all'App Store.

È anche possibile usare Intune per sincronizzare, gestire e assegnare i libri acquistati dallo Store Volume Purchase Program (VPP) di Apple in dispositivi iOS. Per altre informazioni, vedere [Come gestire gli eBook iOS acquistati tramite Volume Purchase Program](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-and-macos-devices"></a>Gestire le app acquistate tramite Volume Purchase Program per dispositivi iOS e macOS

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps"></a>Supporta le app acquistate con Volume Purchase Program di Apple

È possibile acquistare più licenze per le app iOS e macOS tramite [Volume Purchase Program di Apple per le aziende](https://www.apple.com/business/vpp/) o [Volume Purchase Program di Apple per l'istruzione](https://volume.itunes.apple.com/us/store). Questo processo comporta la configurazione di un account VPP di Apple dal sito Web Apple e il caricamento del token VPP di Apple in Intune.  È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso delle app acquistate con VPP.

### <a name="supports-business-to-business-volume-purchased-apps"></a>Supporta le app acquistate con Volume Purchase Program Business-to-Business

Anche gli sviluppatori di terze parti possono distribuire privatamente le app ai membri autorizzati di Volume Purchase Program per le aziende, indicati in App Store Connect. I membri VPP per le aziende possono accedere a Volume Purchase Program App Store e acquistare le app. Le app VPP per le aziende acquistate dall'utente finale verranno sincronizzate con il proprio tenant Intune.

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare è necessario ottenere un token VPP da Apple e caricarlo nell'account di Intune. Tenere presenti anche i criteri che seguono:

* È possibile associare token VPP multipli all'account di Intune.
* Se in passato è stato usato un token VPP con un prodotto diverso, è necessario generare un nuovo token da usare con Intune.
* Ogni token è valido per un anno.
* Per impostazione predefinita, Intune esegue la sincronizzazione con il servizio VPP di Apple due volte al giorno. È possibile avviare una sincronizzazione manuale in qualsiasi momento.
* Prima di iniziare a usare VPP di Apple con Intune, rimuovere tutti gli account utente VPP esistenti creati con altri fornitori di soluzioni di gestione di dispositivi mobili (MDM). Intune non sincronizzerà tali account utente in Intune come misura di sicurezza. Intune sincronizza solo i dati del servizio VPP di Apple creati da Intune stesso.
* Intune supporta l'aggiunta di un numero massimo di 256 token VPP.
* Il programma DEP di Apple automatizza la registrazione per la gestione di dispositivi mobili (MDM). Con DEP è possibile configurare i dispositivi aziendali senza nemmeno toccarli. È possibile registrarsi al programma DEP con lo stesso account dell'agente del programma usato per VPP di Apple. L'ID del programma di distribuzione di Apple è univoco per i programmi elencati nel sito Web [Deployment Program di Apple](https://deploy.apple.com) e non può essere usato per accedere a servizi Apple quali iTunes store.
* Quando si assegnano le app VPP usando il modello di licenze utente a utenti o dispositivi (con l'affinità utente), ogni utente di Intune deve essere associato a un ID Apple univoco o a un indirizzo di posta elettronica quando accetta i Termini e condizioni Apple sul proprio dispositivo.
* Quando si configura un dispositivo per un nuovo utente di Intune, verificare di configurarlo con l'ID Apple univoco o l'indirizzo posta elettronica dell'utente. L'ID Apple o l'indirizzo di posta elettronica e l'utente di Intune formano una coppia di credenziali unica che può essere usata su un massimo di 5 dispositivi.
* Un token VPP è supportato per l'uso su un solo account Intune alla volta. Evitare di riusare lo stesso token VPP per più tenant Intune.

>[!IMPORTANT]
>Dopo avere importato il token VPP in Intune, non importare lo stesso token in un'altra soluzione di gestione dei dispositivi. Questo potrebbe infatti causare la perdita di record relativi agli utenti e alle assegnazioni di licenze.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Per ottenere e caricare un token VPP di Apple

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **App client** > **Token VPP Apple** in **Installazione**.
4. Nel riquadro di elenco dei token VPP selezionare **Crea**.
5. Nel riquadro **Creazione token VPP** specificare le informazioni seguenti:
    - **File del token VPP**: se l'operazione non è ancora stata eseguita, procedere all'iscrizione a Volume Purchase Program per le aziende o per l'istruzione. Dopo avere completato l'iscrizione, scaricare il token VPP di Apple per l'account e selezionarlo qui.
    - **ID Apple**: immettere l'ID Apple dell'account associato al Volume Purchase Program.
    - **Paese o area geografica**: selezionare lo Store del paese o dell'area geografica VPP.  Intune sincronizza le app VPP per tutte le impostazioni locali dello Store VPP del paese/dell'area specificato.
        > [!WARNING]  
        > Se si modifica il paese o l'area geografica, i metadati delle app e l'URL dello Store verranno aggiornati durante la sincronizzazione successiva usando il servizio Apple per le app create con questo token. L'app non verrà aggiornata se non è presente nel nuovo Store del paese o dell'area geografica.

    - **Tipo di account VPP**: scegliere **Azienda** o **Istruzione**.
    - **Aggiornamenti automatici delle app**: scegliere da **On** o **Off** per abilitare gli aggiornamenti automatici. Quando è abilitato, Intune rileva gli aggiornamenti delle app VPP nell'App Store e li invia automaticamente al dispositivo quando questo si connette. Gli aggiornamenti automatici delle app per le app VPP di Apple aggiorneranno automaticamente solo le app distribuite con la finalità di installazione **Richiesto**. Per le app distribuite con la finalità di installazione **Disponibile**, l'aggiornamento automatico genera una notifica per l'amministratore e lo informa che è disponibile una nuova versione dell'app. L'utente vedrà inoltre l'app come non installata nel portale aziendale, anche se è installata una versione precedente dell'app. In questo caso, l'utente può installare la versione più recente dell'app facendo clic su **Installa** nella schermata dei dettagli dell'app nell'app Portale aziendale.

        > [!NOTE]
        > Gli aggiornamenti automatici delle app funzionano per le app sia con licenza per dispositivo che con licenza per utente per iOS 11.0 e versioni successive o macOS 10.12 e versioni successive.
6. Al termine, selezionare **Crea**.

Il token viene visualizzato nel riquadro di elenco dei token.

È possibile sincronizzare i dati archiviati da Apple con Intune in qualsiasi momento scegliendo **Sincronizza**.

## <a name="to-assign-a-volume-purchased-app"></a>Per assegnare un'app acquistata tramite Volume Purchase Program

1. Nel riquadro **Intune** scegliere **App client** > **App** in **Gestisci**.
2. Nel riquadro dell'elenco delle app scegliere l'app da assegnare e quindi scegliere **Assegnazioni**.
3. Nel riquadro ***nome app*** - **Assegnazioni** scegliere **Aggiungi gruppo**, quindi nel riquadro **Aggiungi gruppo** scegliere un **Tipo di assegnazione** e scegliere i gruppi di utenti o di dispositivi Azure AD a cui assegnare l'app.
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

## <a name="revoking-app-licenses"></a>Revoca delle licenze delle app

È possibile revocare tutte le licenze di app iOS o macOS associate al Volume Purchase Program in base a un determinato dispositivo, utente o app.  Esistono tuttavia alcune differenze tra le piattaforme iOS e macOS. 

### <a name="revoking-app-licenses-on-ios"></a>Revoca di licenze di app in iOS
È possibile informare gli utenti quando un'app non è più assegnata a loro. La revoca della licenza di un'app, tuttavia, non comporterà la disinstallazione dell'app VPP correlata dal dispositivo. Per disinstallare un'app VPP e recuperare una licenza app assegnata a un utente o dispositivo, è necessario modificare l'azione di assegnazione specificando **Disinstalla**. Quando si rimuove un'app assegnata a un utente, Intune recupera la licenza per l'utente o il dispositivo e disinstalla l'app dal dispositivo. Il conteggio delle licenze recuperate è indicato nel nodo **App con licenza** nel carico di lavoro **App** di Intune. Dopo che un'app VPP è stata disinstallata e la licenza dell'app è stata recuperata, è possibile scegliere di assegnare la licenza dell'app a un altro utente o dispositivo.


### <a name="revoking-app-licenses-on-macos"></a>Revoca di licenze di app in macOS
La revoca della licenza di un'app non comporta la disinstallazione dell'app VPP dal dispositivo. Quando si revoca la licenza di un'app assegnata a un utente, Intune recupera la licenza utente o dispositivo. Un'app macOS con licenza revocata rimane utilizzabile nel dispositivo, ma può essere aggiornata solo quando viene riassegnata una licenza all'utente o al dispositivo. Secondo Apple, un'app che si trova in questa condizione viene rimossa dopo un periodo di tolleranza di 30 giorni. Apple, tuttavia, non offre a Intune il modo di rimuovere l'app usando l'azione di assegnazione **Disinstalla**. È però possibile scegliere di assegnare la licenza recuperata a un altro utente o dispositivo.

>[!NOTE]
>Intune recupera le licenze delle app VPP per iOS e macOS concesse a un utente quando un dipendente lascia l'azienda e non fa più parte dei gruppi di AAD.

## <a name="deleting-vpp-tokens"></a>Eliminazione di token VPP
<!-- 820879 -->  
È possibile eliminare un token Volume Purchasing Program (VPP) di Apple tramite la console. Ciò potrebbe risultare necessario in presenza di istanze duplicate di un token VPP. L'eliminazione di un token eliminerà anche le eventuali app associate e l'assegnazione. Tuttavia, l'eliminazione di un token non comporta la revoca delle licenze per le app o la disinstallazione di app. 

>[!NOTE]
>Intune non può revocare le licenze delle app dopo l'eliminazione di un token. 

<!-- 820870 -->  
Per revocare la licenza di tutte le app VPP per un token VPP specificato, è prima di tutto necessario revocare tutte le licenze di app associate al token e quindi eliminare il token.

## <a name="renewing-app-licenses"></a>Rinnovo delle licenze delle app

È possibile rinnovare un token VPP Apple scaricando un nuovo token dal portale di Volume Purchase Program di Apple e aggiornando il token esistente in Intune.

## <a name="deleting-a-vpp-app"></a>Eliminazione di un'app VPP

Attualmente, non è possibile eliminare un'app VPP per iOS da Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Assegnazione di autorizzazioni a ruoli personalizzati per VPP

È possibile controllare l'accesso ai token VPP e alle app VPP di Apple in modo indipendente usando le autorizzazioni assegnate ai ruoli di amministratore personalizzati in Intune.

* Per consentire a un ruolo personalizzato di Intune di gestire i token VPP di Apple, in **App client** > **Token VPP Apple** assegnare le autorizzazioni per **App gestite**.
* Per consentire a un ruolo personalizzato di Intune di gestire le app acquistate tramite token VPP iOS, in **App client** > **App** assegnare le autorizzazioni per **App per dispositivi mobili**. 

## <a name="additional-information"></a>Informazioni aggiuntive

Quando un utente con un dispositivo idoneo prova a installare per la prima volta un'app VPP riceve una richiesta di partecipazione al programma Volume Purchase Program di Apple. Per procedere con l'installazione dell'app l'utente deve confermare la partecipazione. L'invito a partecipare al Volume Purchase Program di Apple richiede che l'utente possa usare l'app App Store nel dispositivo iOS o macOS. Se sono stati impostati criteri per disabilitare l'app App Store, le licenze basate sugli utenti per le app VPP non funzionano. La soluzione consiste nel consentire l'app App Store rimuovendo i criteri oppure nell'usare licenze basate su dispositivo.

Apple offre assistenza diretta per creare e rinnovare i token VPP. Per altre informazioni, vedere [Distribuire contenuti agli utenti con il Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661). 

Se nel portale di Intune è indicato **Assegnata a MDM esterno** l'amministratore deve rimuovere il token VPP dall'MDM di terze parti prima di usare il token VPP in Intune.

## <a name="frequently-asked-questions"></a>Domande frequenti

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Quanto tempo è necessario per aggiornare il conteggio delle licenze nel portale dopo che un'app è stata installata o rimossa dal dispositivo?
La licenza viene aggiornata entro poche ore dall'installazione o dalla disinstallazione di un'app. Si noti che se l'utente finale rimuove l'app dal dispositivo, la licenza rimane assegnata all'utente o al dispositivo.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>È possibile sottoscrivere più della disponibilità effettiva di licenze per un'app e, in caso affermativo, in quali casi?
Sì. L'amministratore di Intune può sottoscrivere più della disponibilità effettiva di licenze per un'app. Ad esempio, nel caso in cui l'amministratore acquisti 100 licenze per l'app XYZ e quindi decida di destinare l'app a un gruppo di 500 membri. I primi 100 membri (utenti o dispositivi) otterranno la licenza a essi assegnata mentre per il resto dei membri l'assegnazione della licenza non riuscirà.

### <a name="how-frequently-does-intune-sync-vpp-tokens-with-apple"></a>Con quale frequenza Intune sincronizza i token VPP con Apple?
Intune sincronizza le licenze delle app con Apple due volte al giorno. L'amministratore di Intune può avviare una sincronizzazione manuale in **App client** > **Token VPP Apple**.

## <a name="next-steps"></a>Passaggi successivi

Vedere [How to monitor apps](apps-monitor.md) (Come monitorare le app) per informazioni sul monitoraggio delle assegnazioni di app.