---
title: Impostazioni della modalità tutto schermo Android in Microsoft Intune - Azure | Microsoft Docs
description: Configurare i dispositivi in modalità tutto schermo Android Enterprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 15ac6adbcf262fd14edf11107b032aeda106a15b
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039336"
---
# <a name="android-enterprise-kiosk-settings-in-intune"></a>Impostazioni della modalità tutto schermo Android Enterprise

I profili della modalità tutto schermo Android supportano le impostazioni di configurazione seguenti. Quando si crea un profilo, le impostazioni vengono visualizzate quando si sceglie **Tipo di profilo** > **Proprietario dispositivo** > **Limitazioni del dispositivo**. Per visualizzare queste impostazioni, scegliere **Proprietà** dal profilo di restrizione di un dispositivo Android Enterprise e quindi scegliere **Configura**.

## <a name="general-settings"></a>Impostazioni generali

- **Acquisizione schermo**: scegliere **Blocca** per impedire agli utenti di acquisire la schermata del dispositivo.
- **Fotocamera**: scegliere **Blocca** per disabilitare la fotocamera del dispositivo.
- **Criteri di autorizzazione predefiniti**: questa impostazione definisce i criteri di autorizzazione predefiniti delle richieste delle autorizzazioni di runtime. I valori possibili includono:
    - **Impostazione predefinita dispositivo**: usare l'impostazione predefinita del dispositivo.
    - **Messaggio di richiesta**: all'utente viene richiesto di approvare l'autorizzazione.
    - **Concedi automaticamente**: le autorizzazioni vengono concesse automaticamente.
    - **Nega automaticamente**: le autorizzazioni vengono negate automaticamente.
- **Modifiche al volume**: scegliere **Blocca** per impedire agli utenti di modificare il volume del dispositivo.
- **Ripristino delle impostazioni predefinite**: scegliere **Blocca** per impedire agli utenti di ripristinare le impostazioni predefinite del dispositivo.
- **Modalità provvisoria**: scegliere **Blocca** per impedire agli utenti di riavviare il dispositivo in modalità provvisoria.
- **Barra di stato**: scegliere **Blocca** per impedire agli utenti di accedere alla barra di stato, incluse le notifiche e le impostazioni rapide.
- **Modifiche alle impostazioni Wi-Fi**: scegliere **Blocca** per impedire agli utenti di modificare le configurazioni Wi-Fi create dal proprietario del dispositivo. Gli utenti possono creare configurazioni Wi-Fi personalizzate.
- **Configurazione del punto di accesso Wi-Fi**: scegliere **Blocca** per impedire agli utenti di creare o modificare le configurazioni Wi-Fi.
- **Funzionalità di debug**: scegliere **Consenti** per consentire agli utenti di usare le funzionalità di debug.
- **Regolazione del microfono**: scegliere **Blocca** per impedire agli utenti di regolare il volume o disattivare l'audio del microfono.
- **Indirizzi di posta elettronica per la protezione dal ripristino delle impostazioni predefinite**: scegliere **Indirizzi di posta elettronica dell'account Google** per definire gli indirizzi di posta elettronica, separati da punto e virgola, in grado di sbloccare il dispositivo dopo un ripristino delle impostazioni predefinite. Se non viene specificato alcun indirizzo di posta elettronica, chiunque può sbloccare il dispositivo dopo un ripristino delle impostazioni predefinite.
- **Rete di emergenza**: scegliere **Abilita** per consentire di attivare la funzione di rete di emergenza. Se non è possibile stabilire una connessione di rete all'avvio, la rete di emergenza richiede all'utente di connettersi temporaneamente a una rete per aggiornare i criteri del dispositivo. Dopo aver applicato i criteri, la rete temporanea viene dimenticata e viene ripreso l'avvio del dispositivo. Ciò consente di evitare il caso in cui non sia possibile connettersi a una rete in assenza di una rete idonea nei criteri più recenti e il dispositivo venga avviato in un'app in modalità di attività di blocco oppure l'utente non sia in grado di raggiungere le impostazioni del dispositivo.
- **Consenti l'installazione da origini sconosciute**: scegliere **Consenti** per consentire agli utenti di eseguire l'installazione da origini sconosciute.
- **Aggiornamento del sistema**: scegliere un'opzione per definire la modalità di gestione degli aggiornamenti da parte del dispositivo:
    - **Impostazione predefinita dispositivo**: usare l'impostazione predefinita del dispositivo.
    - **Automatico**: gli aggiornamenti vengono installati automaticamente.
    - **Posposto**: gli aggiornamenti vengono rimandati a una data successiva.
    - **Finestra di manutenzione**: in una finestra di manutenzione viene richiesto agli utenti di approvare l'aggiornamento.

## <a name="kiosk-settings"></a>Impostazioni della modalità tutto schermo

- **Modalità tutto schermo**: specifica se il dispositivo può eseguire un'app singola o più app. Per altre informazioni, vedere [Impostazioni della modalità tutto schermo per dispositivi Android](android-kiosk-settings.md).
    - **Single app kiosk** (App singola in modalità tutto schermo): gli utenti possono accedere a un'app singola.
    - **Più app in modalità tutto schermo**: gli utenti possono accedere a un set di app limitato.

## <a name="device-password-settings"></a>Impostazioni della password del dispositivo mobile

- **Protezione della tastiera**: scegliere **Disabilita** per impedire agli utenti di usare la protezione della tastiera nel dispositivo.
- **Tipo di password richiesto**: definire il tipo di password richiesta per il dispositivo.
- **Lunghezza minima password**: definire la lunghezza minima della password richiesta per il dispositivo.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: definire il numero di accessi non riusciti che devono verificarsi prima che i dati del dispositivo vengano cancellati.

## <a name="power-settings"></a>Impostazioni di risparmio energia

- **Time to lock screen** (Tempo per schermata di blocco): impostare la quantità di tempo di inattività necessaria affinché il dispositivo venga bloccato.
- **Screen on while device plugged in** (Schermata attiva con dispositivo alimentato): scegliere i tipi di alimentazione che mantengono attiva la schermata del dispositivo alimentato.

## <a name="users-and-accounts-settings"></a>Impostazioni di utenti e account

- **Aggiungi nuovi utenti**: scegliere **Blocca** per impedire agli utenti di aggiungere nuovi utenti.
- **Rimozione degli utenti**: scegliere **Blocca** per impedire agli utenti di rimuovere gli utenti.
- **Modifiche all'account**: scegliere **Blocca** per impedire agli utenti di modificare gli account.

## <a name="next-steps"></a>Passaggi successivi
[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).


