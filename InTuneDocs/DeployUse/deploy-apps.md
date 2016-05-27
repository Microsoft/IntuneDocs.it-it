---
# required metadata

title: Distribuire le app | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Distribuire le app con Microsoft Intune

Questo argomento illustra alcuni dei concetti che è necessario comprendere prima di iniziare a distribuire le app con Microsoft Intune.

## Autore del software Intune
**Autore del software Microsoft Intune** viene avviato quando si aggiungono o si modificano le app dalla console di amministrazione di Microsoft Intune. In Autore del software selezionare e configurare un tipo di installazione software che caricherà le app (programmi per computer o app per dispositivi mobili) da archiviare nell'archiviazione cloud di Intune oppure specificare un collegamento a uno store online o a un'applicazione Web.

### Requisiti
Prima di iniziare a usare Autore del software Microsoft Intune, è necessario installare la versione completa di [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Dopo l'installazione, potrebbe essere necessario riavviare il computer per consentire la corretta apertura di Autore del software.

## Spazio di archiviazione nel cloud
Tutte le app distribuite con il tipo di installazione del programma di installazione software devono essere compresse e caricate nell'archiviazione cloud di Microsoft Intune. Una sottoscrizione di valutazione di Intune comprende 2 gigabyte (GB) di archiviazione nel cloud per l'archiviazione delle app gestite e degli aggiornamenti. Una sottoscrizione a pagamento comprende 20 GB, con l'opzione per l'acquisto di altro spazio di archiviazione.

È possibile visualizzare la quantità di spazio usato e acquistare altro spazio di archiviazione nel nodo **Uso memoria** dell'area di lavoro **Amministratore**.

Le regole seguenti si applicano all'acquisto di altro spazio di archiviazione nel cloud per Intune:

-   È necessario un abbonamento a pagamento attivo per acquistare ulteriore memoria.

-   Solo gli amministratori della fatturazione o gli amministratori globali di Microsoft Online Services possono acquistare spazio di archiviazione aggiuntivo tramite il portale per gli account di Intune. Per aggiungere, eliminare o gestire gli amministratori, è necessario essere un amministratore globale e accedere al portale per gli account di Intune.

-   Per i clienti dei contratti multilicenza che hanno acquistato Intune o il componente aggiuntivo di Microsoft Intune attraverso il contratto aziendale, contattare il Microsoft Account Manager o il Microsoft Partner per informazioni sui prezzi e per acquistare memoria aggiuntiva.

#### Requisiti di spazio di archiviazione nel cloud

-   Tutti i file associati a un'app devono essere nella stessa posizione ed essere accessibili da Intune.

-   Le dimensioni massime dei file caricati sono di 2GB.

-   Per caricare i file è necessario avere una connessione Internet la cui velocità minima è pari a 768 kbps.

## Azioni di distribuzione dell'app
Quando si distribuiscono le app, è possibile scegliere una delle seguenti azioni di distribuzione:

-   **Installazione richiesta**: l'app viene installata nel dispositivo senza alcun intervento da parte dell'utente finale.

    > [!TIP]
    > Per i dispositivi iOS non in modalità di supervisione e per tutti i dispositivi Android, l'utente deve accettare l'offerta per l'app prima di installarla.
    >
    > Non è più possibile creare nuove distribuzioni di app nei dispositivi iOS che eseguono sistemi operativi precedenti a iOS 7.1. Tutte le distribuzioni di app esistenti nei dispositivi che eseguono un sistema operativo precedente a iOS 7.1 continueranno a funzionare e ad essere gestite da Intune.

-   **Installazione disponibile**: l'app viene visualizzata nel Portale aziendale e gli utenti finali possono eseguirne l'installazione su richiesta.

-   **Disinstalla** : l'app viene disinstallata dal dispositivo.

-   **Non applicabile** : l'app non viene visualizzata nel Portale aziendale e non viene installata in nessun dispositivo.

#### Comprendere quali sono le azioni di distribuzione disponibili per ogni tipo di programma di installazione

|Tipo di programma di installazione|Installazione richiesta|Installazione disponibile|Disinstalla|Non applicabile|
|------------------|--------------------|---------------------|-------------|------------------|
|Pacchetto app Windows (distribuito in un gruppo di utenti)|Sì|Sì|Sì|sì|
|Pacchetto app Windows (distribuito in un gruppo di dispositivi)|sì|No|Sì|Sì|
|Pacchetto app per dispositivi mobili (distribuito in un gruppo di utenti)|Sì|Sì|Sì|Sì|
|Pacchetto app per dispositivi mobili (distribuito in un gruppo di dispositivi)|Sì|No|Sì|Sì|
|Windows Installer (distribuito in un gruppo di utenti)|No|Sì|No|Sì|
|Windows Installer (distribuito in un gruppo di dispositivi)|Sì|No|Sì|Sì|
|Collegamento esterno (distribuito in un gruppo di utenti)|No|Sì|No|Sì|
|Collegamento esterno (distribuito in un gruppo di dispositivi)|No|No|No|No|
|App iOS gestita dall'App Store (distribuita in un gruppo di utenti)|Sì|Sì|Sì|Sì|
|App iOS gestita dall'App Store (distribuita in un gruppo di dispositivi)|Sì|No|Sì|sì|
> [!TIP]
> Quando si distribuiscono le app, se si selezionano gruppi sia di utenti che di dispositivi, è possibile distribuire l'app soltanto come **Installazione disponibile**.

## Conflitti di distribuzione
Quando un dispositivo riceve due distribuzioni con la stessa azione di distribuzione, si applicano le regole seguenti:

-   Le distribuzioni eseguite in un gruppo di dispositivi hanno la precedenza rispetto a quelle eseguite in un gruppo di utenti. Tuttavia, se un'applicazione viene distribuita in un gruppo di utenti con un'azione di distribuzione di **disponibile** e la stessa applicazione viene distribuita in un gruppo di dispositivi con un'azione di distribuzione di **non applicabile**, l'applicazione verrà reso disponibile nel portale aziendale agli utenti di installare.

-   Lo scopo dell'amministratore IT ha priorità rispetto a quello dell'utente.

-   Un'azione di installazione ha la precedenza rispetto a un'azione di disinstallazione.

-   Se un dispositivo riceve sia un'installazione richiesta che un'installazione disponibile, le azioni vengono combinate (l'app è sia richiesta che disponibile).


## Passaggi successivi

Informazioni su come [Distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).

<!--HONumber=May16_HO1-->


