---
title: Gestire i contratti di licenza software per PC che eseguono il client software di Intune
description: Intune consente di gestire i contratti di licenza del software acquistati tramite Contratti multilicenza Microsoft e del software acquistato tramite altri canali.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: afaeb5b1af35008e6aa778e4391cafeda979bdc0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="manage-license-agreements-for-windows-pc-software-in-microsoft-intune"></a>Gestire i contratti di licenza del software per PC Windows in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune consente di aggiungere e gestire le informazioni sui contratti di licenza del software acquistato con i contratti multilicenza Microsoft. Queste operazioni possono essere eseguite anche per software Microsoft o non Microsoft acquistato in altri modi. È possibile organizzare le informazioni in gruppi logici.

> [!IMPORTANT]
> Questa funzionalità viene fornita solo per comodità e non ne è garantita l'accuratezza. Si sconsiglia di fare affidamento su di essa per verificare la conformità ai contratti multilicenza di Microsoft. Microsoft non userà i dati raccolti per indagare sulle potenziali violazioni o sulla conformità dei contratti di licenza dell'utente eventualmente in atto con Microsoft.
>
> Le licenze aggiunte a Intune non influiscono sui contratti di licenza o sui diritti di licenza per l'uso del software. Ad esempio, l'eliminazione di una coppia di contratti/licenze da Intune non comporta l'eliminazione né l'annullamento della validità di alcun contratto di licenza stipulato con Microsoft.

Nell'area di lavoro **Licenze** della console di amministrazione di Intune è possibile:

-   Aggiungere e modificare i contratti multilicenza Microsoft.

-   Aggiungere e modificare altri contratti di licenza software.

-   Gestire licenze e gruppi.

-   Confrontare le informazioni sui diritti recuperate tramite Intune dal Centro servizi per contratti multilicenza (VLSC) con l'inventario del software Microsoft rilevato da Intune nei PC Windows gestiti.

È anche possibile creare report con i dati relativi al numero di installazioni e di licenze dei titoli software. I report licenze sono utili per valutare la situazione complessiva delle licenze relative al software Microsoft e non Microsoft.

> [!TIP]
> L'area di lavoro **Licenze** non viene visualizzata nella console di amministrazione finché non si gestisce almeno un PC Windows con il client per PC Windows di Intune.

## <a name="add-microsoft-volume-licensing-agreements"></a>Aggiungere contratti multilicenza Microsoft
I contratti multilicenza per Intune offrono informazioni sulle licenze per il software acquistato tramite contratti multilicenza Microsoft. È possibile aggiungere contratti multilicenza Microsoft a Intune specificando coppie di numeri di contratto. I numeri di contratto o di autorizzazione devono corrispondere ai numeri di licenza o di registrazione corretti. Le coppie dei numeri di contratto si ottengono da [Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842)al momento dell'acquisto dei contratti di licenza.

1.  Nella [console di amministrazione di Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx) scegliere **Licenze**.

2.  Nella pagina **Aggiungi contratti** selezionare **Contratto multilicenza**in **Scegli tipo di contratto**.

3.  Nella sezione **Aggiungi dettagli contratto** scegliere se caricare un file o aggiungere i dettagli manualmente.

    -   **Carica un file CSV che contiene i dettagli del contratto**. Scegliere **Sfoglia** e selezionare il file CSV da caricare.

        -   Il file può comprendere due o tre colonne: due per le sole coppie di numeri di contratto o tre se si desidera aggiungere un nome descrittivo che ne agevoli l'individuazione.

        -   Il numero totale dei caratteri di una coppia di numeri di contratto non può superare i 16 caratteri ASCII.

        -   Sono supportati solo i caratteri ASCII.

        -   I caratteri seguenti non sono consentiti nel nome del contratto: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Sono invece consentiti gli spazi.

        -   Il nome del file non può superare i 128 caratteri.

        -   Il file deve contenere almeno una coppia di contratti e non può includere più di 5.000 coppie di contratti.

        **Formato del file**

        È possibile creare il file aggiungendo le coppie di numeri di contratto a un documento di solo testo in uno dei formati riportati di seguito, in base al tipo di organizzazione registrato in VLSC. Specificare una coppia di numeri di contratto per riga.

        -   **Clienti Open Value:** *Numero di contratto*, *ripetere il numero di contratto*, *nome contratto*

        -   **Clienti Open:** *Numero autorizzazione*, *relativo numero di licenza*, *nome contratto*

        -   **Clienti Select ed Enterprise:** *Numero di contratto*, *relativo numero di registrazione*, *nome contratto*

        Quando si aggiungono nuovi contratti, il modulo **Aggiungi contratti** richiede di selezionare questo file.

        Di seguito viene riportato un esempio del contenuto di un file CSV per un cliente Open Value.

        `01-07001, 01-07001, Office agreements`

    -   **Aggiungi manualmente i dettagli del contratto**. Specificare le informazioni seguenti e quindi digitare le coppie di numeri di contratto nelle caselle **Numero autorizzazione/contratto** e **Numero licenza/registrazione/cliente**. Dopo aver digitato entrambi i numeri, fare clic su **Aggiungi coppia** per salvare i numeri e, se si vuole, aggiungere una nuova coppia.

        -   **Nome contratto**: specificare un nome univoco per il contratto.

            Il nome del contratto può avere un massimo di 256 caratteri e non può contenere i caratteri seguenti: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Sono invece consentiti gli spazi.

        -   **Numero autorizzazione/contratto**: immettere il numero di autorizzazione/contratto della coppia di licenze.

        -   **Numero licenza/registrazione/cliente**: immettere il numero di licenza/registrazione/cliente della coppia di licenze.

        > [!NOTE]
        > Se si aggiungono diverse coppie di numeri di contratto, Intune crea un contratto con il nome specificato in cui rientreranno tutte le coppie aggiunte in precedenza.

    Scegliere **+** per aggiungere un'altra coppia di numeri di contratto o **-** per rimuovere una coppia di numeri di contratto già immessa.

4.  Nell'area **Seleziona gruppo di licenze** , effettuare una delle seguenti operazioni:

    -   **Aggiungi i contratti a un gruppo di contratti non assegnato**. Selezionare questa opzione se non si vogliono aggiungere i nuovi contratti a un gruppo di licenze.

    -   **Aggiungi contratti a un nuovo gruppo di licenze**. Specificare un nome per il nuovo gruppo di licenze.

    -   **Aggiungi contratti a un gruppo di licenze esistente**. Nell'elenco **Nome gruppo** selezionare il gruppo di licenze a cui si desidera aggiungere i contratti.

5.  Scegliere **OK**.

Viene aperta la visualizzazione **Tutti i contratti** e Intune si connette al Centro servizi per contratti multilicenza per convalidare le coppie di numeri di contratto specificate.

Per aggiornare le informazioni sui contratti multilicenza dopo aver aggiunto i contratti di licenza in Intune, scegliere **Aggiorna** nella pagina **Panoramica licenze**. Questa azione recupera le informazioni sulle licenze correnti da [Microsoft Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT]
> Finché non vengono aggiornate le informazioni sui contratti multilicenza, è possibile che le informazioni dell'elenco di contratti siano diverse da quelle della pagina **Panoramica contratti** .

Dopo aver aggiornato le informazioni sui contratti multilicenza, è possibile confrontare le informazioni sulle licenze con il software Microsoft rilevato nell'area di lavoro **App** . È anche possibile eseguire i report sulle licenze seguenti:

-   **Report acquisto licenza**: consente di visualizzare il software concesso in licenza per i gruppi di licenze selezionati per facilitare l'individuazione di lacune nella copertura.

-   **Report installazione licenza**: consente di determinare se la copertura del contratto di licenza è sufficiente.

> [!NOTE]
> Il **Titolo prodotto** visualizzato per tutti i contratti multilicenza Microsoft è **Non disponibile**.

## <a name="add-and-edit-other-software-licensing-agreements"></a>Aggiungere e modificare altri contratti di licenza software
È anche possibile aggiungere altri tipi di contratti di licenza a Intune oltre ai contratti multilicenza Microsoft. Questi contratti possono essere relativi a software non Microsoft oppure a software Microsoft acquistato presso un rivenditore.

> [!IMPORTANT]
> Prima di poter aggiungere un contratto, è necessario avere almeno un PC Windows registrato in Intune.  Inoltre, in almeno un computer registrato deve essere caricato un pacchetto software soggetto a licenza da usare per aggiungere un contratto di licenza.

### <a name="to-add-other-software-agreements"></a>Per aggiungere altri contratti software

1.  Nella [console di amministrazione di Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx) scegliere **Licenze**.

2.  Scegliere **Aggiungi contratti** nella sezione **Altri contratti di licenza software**.

3.  Nella sezione **Scelta del tipo di contratto** della pagina **Aggiungi contratti** selezionare **Altri contratti di licenza software** .

4.  Nell'area **Aggiungi dettagli contratto** specificare quanto segue:

    -   **Agreement name** (obbligatorio). Il nome del contratto può avere un massimo di 256 caratteri e non può contenere i caratteri seguenti: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Sono invece consentiti gli spazi.

    -   **Autore** (obbligatorio). Quando si inizia a digitare il nome dell'autore, il servizio recupera tutti i nomi degli autori che contengono i caratteri digitati. Ad esempio, se si digita "soft", il servizio recupera tutti i nomi degli autori che contengono "soft" come parte del nome, come "Microsoft" e "Microsoft Research". I nomi degli autori vengono recuperati dal Software Asset Catalog. È necessario selezionare l'autore prima di immettere il titolo del prodotto.

        > [!IMPORTANT]
        > La società che si vuole aggiungere potrebbe non essere visualizzata nell'elenco. È possibile aggiungere contratti software solo per le aziende già presenti in Software Asset Catalog. Tuttavia, Microsoft si impegna continuamente ad aggiungere i titoli software più diffusi. Se si vuole inviare una richiesta per aggiungere una società a questo elenco, usare il [sito Intune UserVoice](https://microsoftintune.uservoice.com/).

    -   **Titolo prodotto** (obbligatorio). Quando si digita il titolo del prodotto, il servizio recupera tutti i titoli dei prodotti che contengono i caratteri digitati. È necessario specificare prima l' **Autore** e dopo il **Titolo prodotto**.

    -   **Conteggio licenze** (obbligatorio). Immettere il numero delle licenze acquistate.

    -   **Data di inizio licenza**. Immettere la data di inizio della licenza.

    -   **Data di scadenza licenza**. Immettere la data di scadenza della licenza.

    -   **Dettagli contratto**. È facoltativo specificare le informazioni di contatto, i codici di registrazione e altre informazioni.

5.  Nell'area **Seleziona gruppo di licenze** , effettuare una delle seguenti operazioni:

    -   Se non si desidera aggiungere nuovi contratti a un gruppo di licenze nuovo o esistente, selezionare **Aggiungi i contratti a un gruppo di contratti non assegnato** . In qualsiasi momento, è possibile aggiungere i contratti a gruppi di licenze definiti dall'utente.

    -   Per aggiungere i nuovi contratti a un nuovo gruppo di licenze, selezionare **Aggiungi contratti a un nuovo gruppo di licenze** . Viene richiesto di indicare il nome del nuovo gruppo di licenze.

    -   Per aggiungere i nuovi contratti a un gruppo di licenze esistente, selezionare **Aggiungi contratti a un gruppo di licenze esistente** . Nell'elenco **Nome gruppo** selezionare il gruppo di licenze a cui si desidera aggiungere i contratti.

6.  Scegliere **OK**.

Viene visualizzato l'elenco **Tutti i contratti** .

## <a name="manage-license-agreements"></a>Gestire i contratti di licenza
È possibile aggiungere contratti di licenza software a gruppi di licenze. È possibile usare i gruppi di licenze per organizzare i contratti di licenza in unità adeguate alle esigenze dell'organizzazione. È anche possibile eliminare i contratti di licenza creati in precedenza.

|||
|-|-|
|Attività|Dettagli|
|Creare un gruppo di licenze|Nella pagina **Panoramica** dell'area di lavoro **Licenze** scegliere **Crea gruppo di licenze** dal menu **Attività**. **Nota:** è possibile creare un massimo di 500 gruppi di licenze.|
|Rinominare un gruppo di licenze|Nell'area di lavoro **Licenze** scegliere un gruppo di licenze e quindi scegliere **Modifica gruppo di licenze** dal menu **Attività**.|
|Eliminare un gruppo di licenze|Nell'area di lavoro **Licenze** scegliere un gruppo di licenze e quindi scegliere **Elimina gruppo di licenze** dal menu **Attività**. **Suggerimento:** tutte le licenze nel gruppo eliminato verranno spostate nel gruppo di licenze **Contratti non assegnati**.|
|Eliminare un contratto di licenza|Nell'area di lavoro **Licenze** scegliere un contratto e quindi fare clic su **Elimina**. **Suggerimento:** dopo aver eliminato i contratti multilicenza, per aggiornare le informazioni sulle licenze fare clic su **Aggiorna** nella pagina **Panoramica licenze** o della scheda **Generale** di un gruppo di licenze specifico.|
