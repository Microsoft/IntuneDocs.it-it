---
title: Bypass del blocco attivazione iOS con Intune
titlesuffix: Azure portal
description: Informazioni su come usare Intune per il bypass del blocco attivazione iOS per accedere ai dispositivi bloccati."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/22/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e3cd1c7d68cba09c3483cd346772e9791d66c490
ms.sourcegitcommit: 001577b700f634da2fec0b44af2a378150d1f7ac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2017
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Bypass del blocco attivazione su dispositivi iOS con supervisione con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune consente di gestire il Blocco attivazione di iOS, una funzionalità dell'app Trova il mio iPhone per dispositivi iOS 8.0 e versioni successive. Blocco attivazione viene abilitato automaticamente quando un utente apre l'app Trova il mio iPhone in un dispositivo. Una volta abilitato, richiede l'immissione di un ID Apple e una password dell'utente prima di poter:

- Disattivare Trova il mio iPhone
- Cancellare il dispositivo
- Riattivare il dispositivo

## <a name="how-activation-lock-affects-you"></a>Impatto di Blocco attivazione sull'amministratore

Anche se Blocco attivazione consente di proteggere i dispositivi iOS e di aumentare le possibilità di ripristino in caso di smarrimento o furto del dispositivo, questa funzionalità può presentare una serie di difficoltà per gli amministratori IT. Ad esempio:

- Un utente configura Blocco attivazione in un dispositivo. L'utente lascia la società e restituisce il dispositivo. Senza l'ID Apple e la password dell'utente il dispositivo non può essere riattivato in alcun modo.
- È necessario creare un report di tutti i dispositivi in cui è abilitato il blocco attivazione.
- Durante un aggiornamento dei dispositivi nell'organizzazione si vogliono riassegnare alcuni dispositivi a un reparto diverso. È possibile riassegnare solo i dispositivi per cui non è abilitato il blocco attivazione.

Per facilitare la soluzione di questi problemi, Apple ha introdotto il bypass di Blocco attivazione in iOS 7.1 che consente di rimuovere Blocco attivazione dai dispositivi con supervisione senza richiedere ID Apple e password dell'utente. I dispositivi supervisionati possono generare un codice bypass di Blocco attivazione specifico, che viene archiviato nel server di attivazione di Apple.

>[!TIP]
>La modalità di supervisione per i dispositivi iOS consente di usare Apple Configurator per bloccare un dispositivo e limitarne la funzionalità per specifici scopi aziendali. Questa modalità viene in genere usata solo per dispositivi di proprietà dell'azienda.

Altre informazioni sul blocco attivazione sono disponibili nel [sito Web di Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>Come gestire Blocco attivazione in Intune
Intune può richiedere lo stato di Blocco attivazione per dispositivi con supervisione che eseguono iOS 8.0 e versioni successive. Solo per i dispositivi con supervisione, Intune può recuperare il codice del bypass del blocco attivazione e inviarlo direttamente al dispositivo. Se il dispositivo è stato cancellato, è possibile accedervi direttamente usando un nome utente vuoto e il codice come password.

**I vantaggi aziendali dell'uso di Intune per gestire il blocco di attivazione sono:**

- L'utente può usufruire dei vantaggi dell'app Trova il mio iPhone in termini di sicurezza.
- L'amministratore può consentire agli utenti di continuare a lavorare sapendo che, in caso di ridestinazione del dispositivo, potrà ritirarlo o sbloccarlo.

## <a name="before-you-start"></a>Prima di iniziare
Prima di poter eseguire il bypass del blocco attivazione nei dispositivi, è necessario abilitarlo seguendo queste istruzioni:

1. Configurare un profilo di restrizione del dispositivo per iOS in base alle informazioni in [Come configurare le impostazioni relative alle restrizioni dei dispositivi](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Nelle [impostazioni relative alle restrizioni dei dispositivi iOS](device-restrictions-ios.md), in **Generale**, abilitare l'opzione **Blocco attivazione**.
3. Salvare il profilo e quindi [assegnarlo](device-profile-assign.md) ai dispositivi in cui si vuole gestire il bypass del blocco attivazione.


## <a name="how-to-use-activation-lock-bypass"></a>Come usare il bypass del blocco attivazione

>[!IMPORTANT]
>Dopo aver eseguito il bypass del blocco attivazione in un dispositivo, all'apertura dell'app Trova il mio iPhone viene applicato automaticamente un nuovo blocco attivazione. Di conseguenza, **è necessario essere fisicamente in possesso del dispositivo prima di eseguire questa procedura**.

L'azione remota del dispositivo di Intune **Bypass del blocco attivazione** consente di rimuovere il blocco attivazione dai dispositivi iOS senza richiedere Apple ID e password dell'utente. Se è stato eseguito il bypass del blocco attivazione, il dispositivo attiva nuovamente il blocco attivazione quando si avvia l'app Trova il mio iPhone. Eseguire il bypass del blocco attivazione solo se si ha accesso fisico al dispositivo.

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti selezionare un dispositivo iOS con supervisione e quindi scegliere l'azione remota del dispositivo **Bypass del blocco attivazione**.

## <a name="next-steps"></a>Passaggi successivi

È possibile esaminare lo stato della richiesta di sblocco nella pagina dei dettagli relativa al dispositivo nel carico di lavoro **Gestisci dispositivi**.
