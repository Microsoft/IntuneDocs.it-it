---
# required metadata

title: Proteggere i dispositivi iOS con il bypass del blocco attivazione | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteggere i dispositivi iOS con il bypass di Blocco attivazione per Microsoft Intune
Microsoft Intune consente di gestire il Blocco attivazione di iOS, una funzionalità dell'app Trova il mio iPhone per dispositivi iOS 7.1 e versioni successive. Blocco attivazione viene abilitato automaticamente quando si usa l'app Trova il mio iPhone in un dispositivo. Una volta abilitato, richiede l'immissione di un ID Apple e una password dell'utente prima di poter:

-   Disattivare Trova il mio iPhone

-   Cancellare il dispositivo

-   Riattivare il dispositivo

## Impatto di Blocco attivazione sull'amministratore
Anche se il blocco attivazione consente di proteggere i dispositivi iOS e di aumentare le possibilità di ripristino in caso di smarrimento o furto del dispositivo, questa funzionalità può presentare una serie di difficoltà per gli amministratori IT. Ad esempio:

-   Uno degli utenti configura Blocco attivazione in un dispositivo. L'utente lascia la società e restituisce il dispositivo. Senza l'ID Apple e la password dell'utente il dispositivo non può essere riattivato in alcun modo.

-   È necessario creare un report di tutti i dispositivi in cui è abilitato il blocco attivazione.

-   Durante un aggiornamento dei dispositivi nell'organizzazione si vuole riassegnare alcuni dispositivi a un reparto diverso. È possibile riassegnare solo i dispositivi per cui non è abilitato il blocco attivazione.

Per facilitare la soluzione di questi problemi, Apple ha introdotto il bypass di Blocco attivazione in iOS 7.1 che consente di rimuovere Blocco attivazione dai dispositivi supervisionati senza richiedere Apple ID e password dell'utente. I dispositivi supervisionati possono generare un codice bypass di Blocco attivazione specifico, che viene archiviato nel server di attivazione di Apple.

> [!TIP]
> Nella modalità supervisionata per i dispositivi iOS è possibile usare lo strumento Apple Configurator per bloccare un dispositivo e limitarne la funzionalità per specifici scopi aziendali. Questa modalità è in genere usata solo per dispositivi di proprietà dell'azienda.

## Come gestire Blocco attivazione in Intune
Intune può richiedere lo stato di Blocco attivazione per dispositivi supervisionati e non supervisionati che eseguono iOS 7.1 e versioni successive. Solo per i dispositivi con supervisione, Intune può recuperare il codice del bypass del blocco attivazione e inviarlo direttamente al dispositivo. Se il dispositivo è stato cancellato, è possibile accedervi direttamente usando il codice come nome utente e immettendo una password vuota.

**I vantaggi aziendali di questo approccio sono i seguenti**:

-   L'utente può usufruire dei vantaggi dell'app Trova il mio iPhone in termini di sicurezza.

-   È possibile consentire all'utente di continuare a lavorare sapendo che, in caso di ridestinazione del dispositivo, potrà disattivarlo o sbloccarlo.

## Come usare il bypass di Blocco attivazione dalla console di amministrazione di Intune
> [!IMPORTANT]
> Dopo aver eseguito il bypass di Blocco attivazione in un dispositivo, Blocco attivazione verrà applicato automaticamente all'apertura dell'app Trova il mio iPhone. Di conseguenza, **è necessario essere fisicamente in possesso del dispositivo prima di eseguire questa procedura**.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i dispositivi di proprietà dell'azienda**.

2.  Selezionare il dispositivo per cui eseguire il bypass di Blocco attivazione. Scegliere **Bypass del blocco attivazione**.

3.  Leggere il messaggio di avviso. Scegliere **Sì** per continuare.

È possibile esaminare lo stato della richiesta di sblocco nella pagina dei dettagli relativa al dispositivo.

## Come visualizzare i dispositivi che usano Blocco attivazione
È possibile visualizzare i dispositivi che usano Blocco attivazione in due diversi modi:

-   Eseguire il **Report inventario dispositivi mobili**. Questo report visualizza le colonne **Stato di blocco attivazione** e **Supervisione eseguita** che indicano lo stato dei dispositivi. I valori per **Supervisione eseguita** sono **Sì** e **No**, mentre quelli per **Stato di blocco attivazione** sono:

    -   Abilitato con codice bypass

    -   Abilitato senza codice bypass (dispositivo senza supervisione)

    -   Abilitato senza codice bypass (dispositivo non raggiungibile)

    -   Non abilitato

    Il campo **Stato di blocco attivazione** è vuoto per i dispositivi che non eseguono iOS 7.1 o versioni successive.

-   Selezionare un dispositivo in una visualizzazione gruppi per visualizzare lo stato di Blocco attivazione nel riquadro dei dettagli del dispositivo.

    Se si seleziona un dispositivo nel nodo **Tutti i dispositivi di proprietà dell'azienda** e Blocco attivazione è abilitato per il dispositivo, verrà visualizzato anche il codice bypass. Questo codice può essere usato per inviare manualmente un bypass di Blocco attivazione.

### Vedere anche
[Retire devices (Ritirare i dispositivi)](retire-devices-from-microsoft-intune-management.md)
[Help protect your devices with remote lock and passcode reset (Proteggere i dispositivi con blocco remoto e reimpostazione del passcode)](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)


<!--HONumber=May16_HO3-->


