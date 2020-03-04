---
title: Bypass della funzionalità Blocco attivazione di iOS/iPadOS con Intune
titleSuffix: Microsoft Intune
description: Informazioni su come usare Intune per il bypass della funzionalità Blocco attivazione di iOS/iPadOS per accedere ai dispositivi bloccati.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af5bb1c95a15a5c52585278605e2f7a86307cb76
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782225"
---
# <a name="disable-activation-lock-on-supervised-iosipados-devices-with-intune"></a>Disabilitare Blocco attivazione in dispositivi iOS/iPadOS con supervisione con Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune consente di gestire Blocco attivazione di iOS/iPadOS, una funzionalità dell'app Trova il mio iPhone per dispositivi iOS/iPadOS 8.0 e versioni successive. Blocco attivazione viene abilitato automaticamente quando un utente apre l'app Trova il mio iPhone in un dispositivo. Una volta abilitato, richiede l'immissione di un ID Apple e una password dell'utente prima di poter:

- Disattivare Trova il mio iPhone
- Cancellare il dispositivo
- Riattivare il dispositivo

## <a name="how-activation-lock-affects-you"></a>Impatto di Blocco attivazione sull'amministratore

Blocco attivazione consente di proteggere i dispositivi iOS/iPadOS e di aumentare le possibilità di recuperare un dispositivo rubato o perso, ma al tempo stesso questa funzionalità può essere la causa di vari problemi per gli amministratori IT. Ad esempio:

- Un utente configura Blocco attivazione in un dispositivo. L'utente lascia la società e restituisce il dispositivo. Senza l'ID Apple e la password dell'utente il dispositivo non può essere riattivato in alcun modo.
- È necessario creare un report di tutti i dispositivi in cui è abilitato il blocco attivazione.
- Durante un aggiornamento dei dispositivi nell'organizzazione si vogliono riassegnare alcuni dispositivi a un reparto diverso. È possibile riassegnare solo i dispositivi per cui non è abilitato il blocco attivazione.

Per risolvere facilmente questi problemi, Apple ha introdotto la disabilitazione di Blocco attivazione in iOS/iPadOS 7.1. che consente di rimuovere Blocco attivazione dai dispositivi con supervisione senza richiedere ID Apple e password dell'utente. I dispositivi supervisionati possono generare un codice bypass di Blocco attivazione specifico, che viene archiviato nel server di attivazione di Apple.

>[!TIP]
>La modalità di supervisione per i dispositivi iOS/iPadOS consente di usare Apple Configurator per bloccare un dispositivo e limitarne il funzionamento per scopi aziendali specifici. Questa modalità viene in genere usata solo per dispositivi di proprietà dell'azienda.

Altre informazioni sul blocco attivazione sono disponibili nel [sito Web di Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>Come gestire Blocco attivazione in Intune
Intune può richiedere lo stato di Blocco attivazione per i dispositivi con supervisione che eseguono iOS/iPadOS 8.0 e versioni successive. Solo per i dispositivi con supervisione, Intune può recuperare il codice di disabilitazione del blocco attivazione e inviarlo direttamente al dispositivo. Se il dispositivo è stato cancellato, è possibile accedervi direttamente usando un nome utente vuoto e il codice come password.

**I vantaggi aziendali dell'uso di Intune per gestire il blocco di attivazione sono:**

- L'utente può usufruire dei vantaggi dell'app Trova il mio iPhone in termini di sicurezza.
- L'amministratore può consentire agli utenti di continuare a lavorare sapendo che, in caso di ridestinazione del dispositivo, potrà ritirarlo o sbloccarlo.

## <a name="before-you-start"></a>Prima di iniziare
Per poter disabilitare il blocco attivazione nei dispositivi, è necessario abilitarlo seguendo queste istruzioni:

1. Configurare un profilo di restrizione del dispositivo di Intune per iOS/iPadOS seguendo le informazioni disponibili in [Come configurare le impostazioni relative alle restrizioni dei dispositivi](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Nelle [impostazioni relative alle restrizioni dei dispositivi iOS/iPadOS](../configuration/device-restrictions-ios.md), in **Generale** abilitare l'opzione **Blocco attivazione**.
3. Salvare il profilo e quindi [assegnarlo](../configuration/device-profile-assign.md) ai dispositivi in cui si vuole gestire Disabilita il blocco attivazione.


## <a name="how-to-use-disable-activation-lock"></a>Come usare Disabilita il blocco attivazione

>[!IMPORTANT]
>Dopo aver disabilitato il blocco attivazione in un dispositivo, all'avvio dell'app Trova il mio iPhone viene applicato automaticamente un nuovo blocco attivazione. Di conseguenza, **è necessario essere fisicamente in possesso del dispositivo prima di eseguire questa procedura**.

L'azione remota del dispositivo di Intune **Disabilita il blocco attivazione** rimuove Blocco attivazione da un dispositivo iOS/iPadOS senza richiedere l'ID Apple e la password dell'utente. Quando il blocco attivazione è disabilitato, il dispositivo attiva nuovamente il blocco attivazione quando si avvia l'app Trova il mio iPhone. Disabilitare il blocco attivazione solo se si ha accesso fisico al dispositivo.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Nel pannello **Intune** selezionare **Dispositivi**.
4. Nel pannello **Dispositivi** selezionare **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti selezionare l'azione remota del dispositivo **Disabilita il blocco attivazione**.
6. Passare alla sezione "Hardware" del dispositivo e quindi copiare il valore di **Codice di bypass del blocco attivazione** sotto **Accesso condizionale**.

    >[!NOTE]
    >Copiare il codice di bypass prima di cancellare il dispositivo. Se si esegue il ripristino delle impostazioni predefinite del dispositivo prima di copiare il codice, il codice viene rimosso da Azure.

7. Accedere al pannello **Panoramica** del dispositivo e selezionare **Cancella**.
8. Dopo il ripristino del dispositivo vengono richiesti l'*ID Apple* e la *password*. Lasciare vuoto il campo *ID* e immettere il **codice di bypass** come *password*. L'account viene rimosso dal dispositivo. 


## <a name="next-steps"></a>Passaggi successivi

È possibile esaminare lo stato della richiesta di sblocco nella pagina dei dettagli relativa al dispositivo nel carico di lavoro **Gestisci dispositivi**.
