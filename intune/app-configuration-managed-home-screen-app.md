---
title: Configurare l'app Microsoft Managed Home Screen
titleSuffix: Microsoft Intune
description: Informazioni su come configurare l'app Microsoft Managed Home Screen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d28ac5f7964fa7b2ddb5ec9be1878ccdd3dadbd
ms.sourcegitcommit: 5fec35341d83b16023a92fc4b2b3e9237fc6c9ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65853946"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Configurare l'app Microsoft Managed Home Screen per Android Enterprise

Managed Home Screen è l'applicazione usata per i dispositivi Android Enterprise dedicati di proprietà dell'azienda, registrati tramite Intune ed eseguiti in modalità Più app in modalità tutto schermo. Per questi dispositivi l'app Managed Home Screen funge da programma di avvio per altre app approvate da eseguire in aggiunta. Managed Home Screen offre agli amministratori IT la possibilità di personalizzare i loro dispositivi e di limitare le funzionalità a cui l'utente finale potrà accedere. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Quando configurare l'app Microsoft Managed Home Screen

In generale, configurare le impostazioni tramite Configurazione dispositivo, se sono disponibili. In questo modo si risparmia tempo, si riducono gli errori e si ottiene un'esperienza di supporto di Intune più efficace. Tuttavia, alcune impostazioni di Managed Home Screen sono attualmente disponibili solo tramite il pannello **Criteri di configurazione dell'app** nella console di Intune. Leggere questo documento per informazioni su come configurare le diverse impostazioni usando Progettazione configurazione o uno script JSON. 

> [!NOTE]
> È attualmente possibile (e consigliabile) impostare le applicazioni incluse nell'elenco elementi consentiti e i collegamenti Web aggiunti tramite **App client** e **Configurazione del dispositivo**. Per l'elenco completo di impostazioni disponibili in **Configurazione dispositivo** che influiscono su Managed Home Screen, vedere [Impostazioni di un dispositivo dedicato](device-restrictions-android-for-work.md#dedicated-device-settings).  

Passare prima di tutto alla console di Intune nel portale di Azure, quindi selezionare **App client** > **Criteri di configurazione dell'app**. Aggiungere un criterio di configurazione per i **Dispositivi gestiti** che eseguono **Android** e scegliere **Managed Home Screen** come app associata. Fare clic su **Impostazioni di configurazione** per configurare le varie impostazioni di Managed Home Screen disponibili. 

## <a name="choosing-a-configuration-settings-format"></a>Scelta di un formato delle impostazioni di configurazione

È possibile usare due metodi per definire le impostazioni di configurazione per Managed Home Screen:

- **Progettazione configurazione** consente di configurare le impostazioni con un'interfaccia utente intuitiva tramite la quale è possibile attivare o disattivare le funzionalità e impostare i valori. Con questo metodo, alcune chiavi di configurazione sono disabilitate con un tipo di valore `BundleArray`. Queste chiavi di configurazione possono essere configurate solo immettendo dati JSON. 
- **Dati JSON** consente di definire tutte le chiavi di configurazione possibili usando uno script JSON. 

Se si aggiungono proprietà con Progettazione configurazione, è possibile convertirle automaticamente in JSON scegliendo **Immettere i dati JSON** dal menu a discesa **Formato delle impostazioni di configurazione**.

![Screenshot delle opzioni di Formato delle impostazioni di configurazione](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Uso di Progettazione configurazione

Progettazione configurazione consente di selezionare impostazioni prepopolate e i rispettivi valori associati. 

![Screenshot delle impostazioni di configurazione aggiunte](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

La tabella seguente contiene un elenco delle chiavi di configurazione di Managed Home Screen disponibili, con i tipi di valore, i valori predefiniti e le descrizioni. La descrizione indica il comportamento previsto del dispositivo in base ai valori selezionati. Le chiavi di configurazione disabilitate in Progettazione configurazione non sono elencate nella tabella.

| Chiave di configurazione | Tipo valore | Valore predefinito | Descrizione |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Set Grid Size (Imposta dimensioni griglia) | string | Automatico | Consente di impostare le dimensioni della griglia per le app da posizionare nella schermata iniziale gestita. È possibile specificare il numero di righe e colonne di app per definire le dimensioni della griglia nel formato `columns;rows`. Se si definiscono le dimensioni della griglia, il numero di righe impostate corrisponde al numero massimo di app che verranno visualizzate in una riga e il numero di colonne impostate al numero massimo di app che verranno visualizzate in una colonna. |
| Enable Screen Header (Abilita intestazione schermo) | bool | TRUE | Abilita l'intestazione superiore per diverse visualizzazioni offerte dalla schermata iniziale gestita, ad esempio feed o schede di feed. Se si abilita questa impostazione, gli utenti del dispositivo vedranno l'intestazione. |
| Enable device status bar (Abilita barra di stato del dispositivo) | bool | TRUE | Abilita la barra di stato nella schermata iniziale, ossia la barra superiore che visualizza le connessioni correnti, come il Wi-Fi e così via. Se si abilita questa impostazione, l'utente finale potrà vedere sulla barra di stato le icone che rappresentano le connessioni e le app attive. |
| Enable notifications badge (Abilita notifiche) | bool | FALSE | Abilita le notifiche per le icone delle app che mostrano il numero delle nuove notifiche ricevute. Se si abilita questa impostazione, gli utenti finali vedranno il numero di notifiche da leggere per le app. Se si mantiene disabilitata questa chiave di configurazione, gli utenti finali non vedranno le eventuali notifiche da leggere per le app. |
| Lock Home Screen (Blocca schermata iniziale) | bool | TRUE | Impedisce all'utente finale di spostare le icone delle app nella schermata iniziale. Se si abilita questa chiave di configurazione, le icone delle app saranno bloccate nella schermata iniziale e l'utente finale non potrà trascinarle in posizioni diverse della griglia. Se impostata su `false`, gli utenti finali potranno spostare le icone di applicazioni e collegamenti Web nella schermata iniziale gestita.  |
| Set device wall paper (Imposta sfondo del dispositivo) | string | Predefinito | Consente di impostare uno sfondo a scelta immettendo l'URL dell'immagine da usare. |
| Set app icon size (Imposta dimensioni delle icone delle app) | integer | 2 | Consente di impostare le dimensioni delle icone per le app visualizzate nella schermata inziale. È possibile scegliere i valori seguenti in questa configurazione per le diverse dimensioni: 0 (minime), 1 (piccole), 2 (regolari), 3 (grandi) e 4 (massime). |
| Set app folder icon (Imposta icona delle cartelle di app) | integer | 0 | Consente di definire l'aspetto delle cartelle delle app nella schermata iniziale. È possibile scegliere l'aspetto dai valori seguenti: 0 (quadrato scuro), 1 (cerchio scuro), 2 (quadrato chiaro), 3 (cerchio chiaro). |
| Enable gestures (Abilita gesti) | bool | FALSE | Consente all'utente finale di assegnare azioni a diversi gesti, come lo scorrimento rapido in alto o in basso. Se si disabilita questa chiave di configurazione, gli utenti finali potranno scorrere rapidamente solo a destra, se è disponibile una seconda pagina, e a sinistra per tornare nella schermata iniziale. |
| Enable vertical scrolling (Abilita scorrimento verticale) | bool | FALSE | Abilita lo scorrimento verticale nella schermata iniziale gestita. Se si abilita questa chiave di configurazione, l'utente finale potrà passare ad altre pagine solo scorrendo in verticale e non in orizzontale. |
| Set home screen theme (Imposta tema della schermata iniziale) | string | Theme.Light.Blue | Consente di scegliere il tema per la schermata iniziale da un set predefinito con colori diversi. È possibile scegliere i temi seguenti immettendo il valore di stringa nel formato seguente.   Theme.Light.Green. Dove Light (chiaro) può essere sostituito con Dark per un tema scuro e Green (verde) può essere sostituito con Blue (blu), Yellow (giallo), Pink (rosa), Red (rosso), Orange (arancione) e Purple (viola). |
| Enable dock (Abilita ancoraggio) | bool | FALSE | Abilita la sezione di ancoraggio delle app nella parte inferiore della schermata iniziale, con le app persistenti visualizzate e il punto di ingresso per tutte le app installate. Se si abilita questa chiave di configurazione, l'utente finale potrà accedere alle app nella sezione di ancoraggio e potrà anche passare all'elenco di tutte le app installate nei dispositivi, indipendentemente dal fatto che siano o meno inserite nell'elenco elementi consentiti. |
| Set screen orientation (Imposta orientamento schermo) | integer | 1 | Consente di impostare l'orientamento della schermata iniziale sulla modalità verticale, orizzontale o con rotazione automatica. Per impostare l'orientamento, immettere il valore 1 (modalità verticale), 2 (modalità orizzontale) o 3 (rotazione automatica). |
| Enable home screen feed (Abilita feed della schermata iniziale) | bool | FALSE | Abilita il feed della schermata iniziale, che è possibile vedere con lo scorrimento rapido a sinistra. Questo feed visualizza diversi tipi di contenuto, come il calendario, le app usate di frequente, la scheda dell'assistente vocale Cortana e così via. Se si abilita questa impostazione, l'utente finale potrà passare al feed scorrendo rapidamente a sinistra nella schermata iniziale. |
| Enable overview mode (Abilita modalità panoramica) | bool | FALSE | Consente agli utenti finali di aggiungere o rimuovere diverse pagine della schermata iniziale accessibili con lo scorrimento rapido a destra dalla schermata predefinita. Se si abilita questa impostazione, l'utente finale potrà aggiungere pagine a destra della pagina predefinita della schermata iniziale, potrà cambiare la pagina predefinita e potrà accedere alle impostazioni di Managed Home Screen. |
| Enable device telemetry (Abilita telemetria del dispositivo) | bool | FALSE | Abilita tutti i dati di telemetria acquisiti per la schermata iniziale gestita. Se si abilita questa impostazione, Microsoft potrà acquisire i dati di telemetria sull'utilizzo del dispositivo, ad esempio il numero di volte in cui è stata avviata una specifica app. |
| Set whitelisted applications (Imposta applicazioni nell'elenco elementi consentiti) | bundleArray | FALSE | Consente di definire il set di app visibili nella schermata iniziale tra le app installate nel dispositivo. Per definire le app, immettere il nome del pacchetto delle app da rendere visibili, ad esempio com.android.settings per rendere le impostazioni accessibili nella schermata iniziale. Le app da aggiungere nell'elenco elementi consentiti in questa sezione devono essere già installate nel dispositivo per renderle visibili nella schermata iniziale. |
| Set pinned web links (Imposta collegamenti Web aggiunti) | bundleArray | FALSE | Consente di aggiungere i siti Web come icone di avvio rapido nella schermata iniziale. Con questa configurazione è possibile definire l'URL e aggiungerlo nella schermata iniziale per consentire all'utente finale di avviarlo nel browser con un singolo tocco. |
| Enable search bar (Abilita barra di ricerca) | bool | FALSE | Abilita la barra di ricerca nella schermata iniziale. Se si abilita questa impostazione, gli utenti del dispositivo vedranno la barra di ricerca nella schermata iniziale e potranno immettere qualsiasi contenuto da cercare nel Web. |
| Disable settings app (Disabilita app di impostazioni) | bool | FALSE | Disabilita la pagina di impostazioni per Managed Home Screen. Se si disabilita questa impostazione, l'utente finale del dispositivo non potrà accedere alle impostazioni di Managed Home Screen. |
| Enable screen saver (Abilita screen saver) | bool | FALSE | Abilita o disabilita la modalità screen saver. Se impostata su True, è possibile configurare **screen_saver_image**, **screen_saver_show_time**, **inactive_time_to_show_screen_saver** e **media_detect_screen_saver**. |
| Screen saver image (Immagine screen saver) | string |   | Consente di impostare l'URL dell'immagine dello screen saver. Se non viene impostato un URL, nei dispositivi verrà visualizzata la schermata predefinita quando è attivato lo screen saver.  |
| Screen saver show time (Durata dello screen saver) | integer | 0 | Offre la possibilità di impostare la durata, in secondi, dello screen saver visualizzato nel dispositivo in modalità screen saver. Se impostata su 0, lo screen saver verrà visualizzato per un tempo indefinito in modalità screen saver finché il dispositivo non diventa attivo.  |
| Inactive time to enable screen saver (Tempo di inattività per abilitare lo screen saver) | integer | 30 | Il numero di secondi durante il quale il dispositivo è inattivo prima che venga attivato lo screen saver. Se impostata su 0, il dispositivo non passerà mai in modalità screen saver. |
| Media detect before showing screen saver (Rilevamento di contenuti multimediali prima dello screen saver) | bool | TRUE | Scegliere se nel dispositivo dovrà essere visualizzato lo screen saver durante la riproduzione di audio o video. Se impostata su True, il dispositivo non riprodurrà audio o video, indipendentemente dal valore di **inactive_time_to_show_scree_saver**. Se impostata su False, nel dispositivo verrà visualizzato lo screen saver in base al valore impostato in **inactive_time_to_show_screen_saver**.   |
| Enable virtual home button (Abilita il pulsante di schermata iniziale virtuale) | bool | FALSE | Se impostata su `True`, l'utente finale avrà accesso a un pulsante della schermata iniziale di Managed Home Screen che consentirà di tornare in Managed Home Screen dall'attività corrente.  |
| Type of virtual home button (Tipo di pulsante di schermata iniziale virtuale) | string | swipe_up | Usare **swipe_up** per accedere al pulsante della pagina iniziale con un gesto di scorrimento in alto. Usare **float** per accedere a un pulsante della schermata iniziale persistente e permanente che l'utente finale può spostare nella schermata. |
| Battery and Signal Strength indicator bar (Barra indicatore potenza segnale e batteria) | bool | True  | Se impostata su `True`, visualizza la barra indicatore della potenza del segnale e della batteria. |
| Exit lock task mode password (Password di uscita dalla modalità blocco attività) | string |   | Immettere un codice di 4-6 cifre da usare per uscire temporaneamente dalla modalità blocco attività per la risoluzione dei problemi. |
| Show Wi-Fi setting (Mostra impostazioni Wi-Fi) | bool | FALSE | Se impostata su `True`, l'utente finale può attivare o disattivare il Wi-Fi oppure connettersi a reti Wi-Fi diverse.  |
| Show Bluetooth setting (Mostra impostazione Bluetooth) | bool | FALSE | Se impostata su `True`, l'utente finale può attivare o disattivare il Bluetooth oppure connettersi ad altri dispositivi abilitati per Bluetooth.   |

## <a name="enter-json-data"></a>Immettere dati JSON

Immettere dati JSON per configurare tutte le impostazioni disponibili per Managed Home Screen, oltre alle impostazioni disabilitate in **Progettazione configurazione**.

![Screenshot dei dati JSON aggiunti](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

In aggiunta all'elenco di impostazioni configurabili riportato nella tabella **Progettazione configurazione** precedente, la tabella seguente include le chiavi di configurazione che è possibile configurare solo tramite dati JSON.

|    Chiave di configurazione    |    Tipo di valore    |    Valore predefinito    |    Descrizione    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Set allow-listed applications (Imposta applicazioni nell'elenco elementi consentiti)    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    Consente di definire il set di app visibili nella schermata iniziale tra le app installate nel dispositivo. Per definire le app, immettere il nome del pacchetto delle app da rendere visibili, ad esempio com.android.settings per rendere le impostazioni accessibili nella schermata iniziale. Le app da aggiungere nell'elenco elementi consentiti in questa sezione devono essere già installate nel dispositivo per renderle visibili nella schermata iniziale.    |
|    Set pinned web links (Imposta collegamenti Web aggiunti)    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    Consente di aggiungere i siti Web come icone di avvio rapido nella schermata iniziale. Con questa configurazione è possibile definire l'URL e aggiungerlo nella schermata iniziale per consentire all'utente finale di avviarlo nel browser con un singolo tocco.    |
|    Create Managed Folder for grouping apps (Crea cartella gestita per il raggruppamento di app)    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    Consente di creare e denominare cartelle e gruppi di app al loro interno. Gli utenti finali non potranno spostare o rinominare le cartelle, né spostare le app al loro interno.   Le cartelle verranno visualizzate nell'ordine in cui vengono create, mentre le app al loro interno saranno disposte in ordine alfabetico.         Nota: tutte le app da raggruppare in cartelle devono essere assegnate come obbligatorie al dispositivo e devono essere aggiunte a Managed Home Screen.     |

Di seguito è riportato un esempio di script JSON con tutte le chiavi di configurazione disponibili incluse:

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "grid_size",
            "valueString": "Auto"
        },
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}

```
## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sui dispositivi Android Enterprise dedicati, vedere [Configurare la registrazione in Intune di dispositivi Android Enterprise dedicati](android-kiosk-enroll.md).
