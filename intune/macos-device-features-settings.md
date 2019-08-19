---
title: Impostazioni delle funzionalità dei dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare le impostazioni per configurare i dispositivi macOS per AirPrint e personalizzare la finestra di accesso per visualizzare o nascondere pulsanti di alimentazione in Microsoft Intune. Vedere i passaggi per ottenere l'indirizzo IP, il percorso e le impostazioni della porta di un server AirPrint nella rete. Usare queste impostazioni in un profilo di configurazione del dispositivo per configurare le funzionalità dei dispositivi macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63f2832dd321425efe8092f1bb12dd0d479ef71b
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69549926"
---
# <a name="macos-device-feature-settings-in-intune"></a>Impostazioni relative alle funzionalità dei dispositivi macOS in Intune

Intune include alcune impostazioni integrate per personalizzare le funzionalità nei dispositivi macOS. L'articolo elenca queste impostazioni e descrive la funzione di ogni impostazione. Vengono inoltre elencati i passaggi per ottenere l'indirizzo IP, il percorso e la porta delle stampanti AirPrint tramite l'app Terminale (emulatore).

Questa funzionalità si applica a:

- macOS

Come parte della soluzione MDM, usare queste impostazioni per creare un banner, scegliere la modalità di accesso degli utenti, aggiungere un server AirPrint e altro ancora.

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo in Intune e quindi assegnate o distribuite ai dispositivi macOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione dei dispositivi macOS](device-features-configure.md).

## <a name="airprint"></a>AirPrint

- **Indirizzo IP**: immettere l'indirizzo IPv4 o IPv6 della stampante. Se si usano i nomi host per identificare le stampanti, è possibile ottenere l'indirizzo IP effettuando il ping della stampante nell'app Terminale. Per informazioni più dettagliate, vedere [Ottenere l'indirizzo IP e il percorso](#get-the-ip-address-and-path) (in questo articolo).
- **Percorso**: immettere il percorso della stampante. il percorso è in genere `ipp/print` per le stampanti di rete. Per informazioni più dettagliate, vedere [Ottenere l'indirizzo IP e il percorso](#get-the-ip-address-and-path) (in questo articolo).
- **Porta** (iOS 11.0 eversioni successive): immettere la porta di ascolto della destinazione AirPrint. Se si omette questa proprietà, AirPrint usa la porta predefinita.
- **TLS** (iOS 11.0 e versioni successive): selezionare **Abilita** per proteggere le connessioni AirPrint con Transport Layer Security (TLS).

**Aggiungere** il server AirPrint. È possibile aggiungere più server AirPrint.

- **Importa** (facoltativa): è anche possibile **importare** un file delimitato da virgole (.csv) che include un elenco di stampanti AirPrint. Dopo aver aggiunto le stampanti AirPrint in Intune, è anche possibile **esportare** questo elenco.

Selezionare **OK** per salvare le impostazioni.

### <a name="get-the-ip-address-and-path"></a>Ottenere l'indirizzo IP e il percorso

Per aggiungere i server AirPrinter, sono necessari l'indirizzo IP della stampante, il percorso della risorsa e la porta. La procedura seguente mostra come ottenere queste informazioni.

1. In un dispositivo Mac connesso alla stessa rete locale (subnet) delle stampanti AirPrint aprire **Terminale** (da **/Applicazioni/Utilità**).
2. Nell'app Terminale digitare `ippfind` e premere INVIO.

    Prendere nota delle informazioni della stampante. Ad esempio, potrebbe restituire un valore simile a `ipp://myprinter.local.:631/ipp/port1`. La prima parte è il nome della stampante. L'ultima parte (`ipp/port1`) è il percorso della risorsa.

3. Nel Terminale digitare `ping myprinter.local` e premere INVIO.

   Prendere nota dell'indirizzo IP. Ad esempio, potrebbe restituire un valore simile a `PING myprinter.local (10.50.25.21)`.

4. Usare i valori del percorso della risorsa e dell'indirizzo IP. In questo esempio l'indirizzo IP è `10.50.25.21` e il percorso della risorsa è `/ipp/port1`.

## <a name="login-items"></a>Elementi di accesso

- **File, cartelle e app personalizzate**: **aggiungere** il percorso di un file, una cartella, un'app personalizzata o un'app di sistema che si vuole aprire quando un utente accede al dispositivo. Le app di sistema o le `Applications` app compilate o personalizzate per l'organizzazione si trovano in genere nella cartella con un percorso simile a. `/Applications/AppName.app` 

  È possibile aggiungere molti file, cartelle e app. Ad esempio, immettere:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Quando si aggiunge un'app, una cartella o un file, assicurarsi di immettere il percorso corretto. Non tutti gli elementi si trovano `Applications` nella cartella. Se un utente sposta un elemento da una posizione a un'altra, il percorso viene modificato. Questo elemento spostato non verrà aperto quando l'utente accede.

## <a name="login-window"></a>Finestra di accesso

### <a name="window-layout"></a>Layout della finestra

- **Mostra informazioni aggiuntive sulla barra dei menu**: quando viene selezionata l'area del tempo nella barra dei menu, **Consenti** mostra il nome host e la versione di macOS. **Non configurato** (impostazione predefinita) non visualizza queste informazioni nella barra dei menu.
- **Banner**: immettere un messaggio che viene visualizzato nella schermata di accesso del dispositivo. Ad esempio, immettere le informazioni sull'organizzazione, un messaggio di benvenuto, le informazioni perse e trovate e così via.
- **Scegliere il formato di accesso**: scegliere la modalità di accesso degli utenti al dispositivo. Le opzioni disponibili sono:
  - **Richiedi nome utente e password** (impostazione predefinita): richiede agli utenti di immettere un nome utente e una password.
  - **Elenca tutti gli utenti e richiedi la password**: richiede agli utenti di selezionare il nome utente da un elenco di utenti e quindi immettere la password. Configurare inoltre:

    - **Utenti locali**: **Nascondi** non mostra gli account utente locali nell'elenco degli utenti, che può includere gli account standard e amministratore. Vengono visualizzati solo gli account utente di rete e del sistema. **Non configurato** (impostazione predefinita) mostra gli account utente locali nell'elenco degli utenti.
    - **Account per dispositivi mobili**: **Nascondi** non mostra gli account per dispositivi mobili nell'elenco degli utenti. **Non configurato** (impostazione predefinita) mostra gli account utente per dispositivi mobili nell'elenco degli utenti. Alcuni account per dispositivi mobili possono essere visualizzati come utenti della rete.
    - **Utenti di rete**: selezionare **Mostra** per elencare gli utenti di rete nell'elenco degli utenti. **Non configurato** (impostazione predefinita) non mostra gli account degli utenti di rete nell'elenco degli utenti.
    - **Utenti amministratori**: **Nascondi** non mostra gli account utente amministratori nell'elenco degli utenti. **Non configurato** (impostazione predefinita) mostra gli account utente amministratori nell'elenco degli utenti.
    - **Altri utenti**: selezionare **Mostra** per elencare **Altri...** utenti nell’elenco degli utenti. **Non configurato** (impostazione predefinita) non mostra gli altri account utente nell'elenco degli utenti.

### <a name="login-screen-power-settings"></a>Impostazioni di risparmio energia della schermata di accesso

- **Pulsante Arresta**: **Nascondi** non mostra il pulsante di arresto nella schermata di accesso. **Non configurata** (impostazione predefinita) mostra il pulsane di arresto.
- **Pulsante Riavvia**: **Nascondi** non mostra il pulsante di riavvio nella schermata di accesso. **Non configurata** (impostazione predefinita) mostra il pulsane di riavvio.
- **Pulsante Sospendi**: **Nascondi** non mostra il pulsante di sospensione nella schermata di accesso. **Non configurata** (impostazione predefinita) mostra il pulsante di sospensione.

### <a name="other"></a>Altro

- **Disabilita l'accesso utente dalla console**: **Disabilita** nasconde la riga di comando di macOS usata per l'accesso. Per gli utenti tipici **disabilitare** questa impostazione. **Non configurata** (impostazione predefinita) consente agli utenti esperti di accedere usando la riga di comando di macOS. Per passare alla modalità console, gli utenti immettono `>console` nel campo Nome utente e devono autenticarsi nella finestra della console.

### <a name="apple-menu"></a>Apple Menu

Dopo che gli utenti hanno effettuato l'accesso ai dispositivi, le impostazioni seguenti influiscono cosa possono fare.

- **Disabilita Arresta**: **Disabilita** impedisce agli utenti di selezionare l’opzione **Arresta** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Arresta** sul dispositivo.
- **Disabilita Riavvia**: **Disabilita** impedisce agli utenti di selezionare l’opzione **Riavvia** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Riavvia** sul dispositivo.
- **Disabilita Spegni**: **Disabilita** impedisce agli utenti di selezionare l’opzione **Spegni** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Spegni** sul dispositivo.
- **Disabilita Disconnetti** (macOS 10.13 e versioni successive): **Disabilita** impedisce agli utenti di selezionare l’opzione **Disconnetti** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Disconnetti** sul dispositivo.
- **Disabilita la schermata di blocco** (macOS 10.13 e versioni successive): **Disabilita** impedisce agli utenti di selezionare l’opzione **Schermata di blocco** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Schermata di blocco** sul dispositivo.

Selezionare **OK** per salvare le impostazioni.

## <a name="next-steps"></a>Passaggi successivi

- Visualizzare tutte le impostazioni per i dispositivi [iOS](ios-device-features-settings.md).
- [Assegnare il profilo](device-profile-assign.md) al gruppo e [monitorarne lo stato](device-profile-monitor.md).
