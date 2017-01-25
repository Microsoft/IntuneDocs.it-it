---
title: Gestire il Blocco attivazione di iOS nei dispositivi | Documentazione Microsoft
description: "Microsoft Intune consente di gestire il Blocco attivazione di iOS, una funzionalità dell&quot;app Trova il mio iPhone per dispositivi iOS 7.1 e versioni successive."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: a6fa910c0a8ec1a9542e03a276dbb8d0757d75b4


---

# <a name="help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune"></a>Proteggere i dispositivi iOS con il bypass di Blocco attivazione per Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune consente di gestire il Blocco attivazione di iOS, una funzionalità dell'app Trova il mio iPhone per dispositivi iOS 8.0 e versioni successive. Blocco attivazione viene abilitato automaticamente quando un utente apre l'app Trova il mio iPhone in un dispositivo. Una volta abilitato, richiede l'immissione di un ID Apple e una password dell'utente prima di poter: 

-   Disattivare Trova il mio iPhone

-   Cancellare il dispositivo

-   Riattivare il dispositivo

## <a name="how-activation-lock-affects-you"></a>Impatto di Blocco attivazione sull'amministratore
Anche se Blocco attivazione consente di proteggere i dispositivi iOS e di aumentare le possibilità di ripristino in caso di smarrimento o furto del dispositivo, questa funzionalità può presentare una serie di difficoltà per gli amministratori IT. Ad esempio:

-   Un utente configura Blocco attivazione in un dispositivo. L'utente lascia la società e restituisce il dispositivo. Senza l'ID Apple e la password dell'utente il dispositivo non può essere riattivato in alcun modo.

-   È necessario creare un report di tutti i dispositivi in cui è abilitato il blocco attivazione.

-   Durante un aggiornamento dei dispositivi nell'organizzazione si vogliono riassegnare alcuni dispositivi a un reparto diverso. È possibile riassegnare solo i dispositivi per cui non è abilitato il blocco attivazione.

Per facilitare la soluzione di questi problemi, Apple ha introdotto il bypass di Blocco attivazione in iOS 7.1 che consente di rimuovere Blocco attivazione dai dispositivi supervisionati senza richiedere Apple ID e password dell'utente. I dispositivi supervisionati possono generare un codice bypass di Blocco attivazione specifico, che viene archiviato nel server di attivazione di Apple.

> [!TIP]
> La modalità di supervisione per i dispositivi iOS consente di usare Apple Configurator per bloccare un dispositivo e limitarne la funzionalità per specifici scopi aziendali. Questa modalità è in genere usata solo per dispositivi di proprietà dell'azienda.

## <a name="how-intune-helps-you-manage-activation-lock"></a>Come gestire Blocco attivazione in Intune
Intune può richiedere lo stato di Blocco attivazione per dispositivi con supervisione che eseguono iOS 8.0 e versioni successive. Solo per i dispositivi con supervisione, Intune può recuperare il codice del bypass del blocco attivazione e inviarlo direttamente al dispositivo. Se il dispositivo è stato cancellato, è possibile accedervi direttamente usando un nome utente vuoto e il codice come password.

**I vantaggi aziendali di questo approccio sono i seguenti**:

-   L'utente può usufruire dei vantaggi dell'app Trova il mio iPhone in termini di sicurezza.

-   L'amministratore può consentire agli utenti di continuare a lavorare sapendo che, in caso di ridestinazione del dispositivo, potrà ritirarlo o sbloccarlo.

## <a name="how-to-use-activation-lock-bypass-from-the-intune-admin-console"></a>Come usare il bypass di Blocco attivazione dalla console di amministrazione di Intune
> [!IMPORTANT]
> Dopo aver eseguito il bypass di Blocco attivazione in un dispositivo, un nuovo Blocco attivazione verrà applicato automaticamente all'apertura dell'app Trova il mio iPhone. Di conseguenza, **è necessario essere fisicamente in possesso del dispositivo prima di eseguire questa procedura**.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Gruppi** &gt; **Tutti i dispositivi** &gt; **Tutti i dispositivi di proprietà dell'azienda**.

2.  Selezionare il dispositivo per cui eseguire il bypass di Blocco attivazione. Scegliere **Bypass del blocco attivazione**.

3.  Leggere il messaggio di avviso. Scegliere **Sì** per continuare.

È possibile esaminare lo stato della richiesta di sblocco nella pagina dei dettagli relativa al dispositivo.

## <a name="how-to-see-which-devices-are-using-activation-lock"></a>Come visualizzare i dispositivi che usano Blocco attivazione
È possibile visualizzare i dispositivi che usano Blocco attivazione in due diversi modi:

-   Eseguire il **Report inventario dispositivi mobili**. Questo report visualizza le colonne **Stato blocco attivazione** e **Supervisione eseguita** che indicano lo stato dei dispositivi. I valori per **Supervisione eseguita** sono **Sì** e **No**, mentre quelli per **Stato di blocco attivazione** sono:

    -   Abilitato con codice bypass

    -   Abilitato senza codice bypass (dispositivo senza supervisione)

    -   Abilitato senza codice bypass (dispositivo non raggiungibile)

    -   Non abilitato

    La casella **Stato blocco attivazione** è vuoto per i dispositivi che non eseguono iOS 8.0 o versioni successive.

-   Selezionare un dispositivo in una visualizzazione gruppi per visualizzare lo stato di Blocco attivazione nel riquadro dei dettagli del dispositivo.

    Se si seleziona un dispositivo nel nodo **Tutti i dispositivi di proprietà dell'azienda** e Blocco attivazione è abilitato per il dispositivo, verrà visualizzato anche il codice bypass. Questo codice può essere usato per inviare manualmente un bypass di Blocco attivazione.

    > [!IMPORTANT]
    >Intune riceve l'inventario dai dispositivi per Blocco attivazione ogni sette giorni. Per questo motivo, è possibile che i dispositivi non vengano visualizzati immediatamente con il relativo stato di Blocco attivazione nella console di Intune.


### <a name="see-also"></a>Vedere anche
[Retire devices (Ritirare i dispositivi)](retire-devices-from-microsoft-intune-management.md)
[Help protect your devices with remote lock and passcode reset (Proteggere i dispositivi con blocco remoto e reimpostazione del passcode)](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)



<!--HONumber=Jan17_HO2-->


