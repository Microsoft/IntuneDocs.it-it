---
title: Configurare l'app Microsoft Managed Home Screen
titleSuffix: Microsoft Intune
description: Informazioni su come configurare l'app Microsoft Managed Home Screen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e97e88ad78e1b914543b7fa283f47863dce185fc
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813466"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Configurare l'app Microsoft Managed Home Screen per Android Enterprise

Managed Home Screen è l'applicazione usata per i dispositivi Android Enterprise dedicati di proprietà dell'azienda, registrati tramite Intune ed eseguiti in modalità Più app in modalità tutto schermo. Per questi dispositivi l'app Managed Home Screen funge da programma di avvio per altre app approvate da eseguire in aggiunta. Managed Home Screen offre agli amministratori IT la possibilità di personalizzare i loro dispositivi e di limitare le funzionalità a cui l'utente finale potrà accedere. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Quando configurare l'app Microsoft Managed Home Screen

In generale, configurare le impostazioni tramite Configurazione dispositivo, se sono disponibili. In questo modo si risparmia tempo, si riducono gli errori e si ottiene un'esperienza di supporto di Intune più efficace. Tuttavia, alcune impostazioni di Managed Home Screen sono attualmente disponibili solo tramite il pannello **Criteri di configurazione dell'app** nella console di Intune. Leggere questo documento per informazioni su come configurare le diverse impostazioni usando Progettazione configurazione o uno script JSON. 

> [!NOTE]
> È attualmente possibile (e consigliabile) impostare le applicazioni incluse nell'elenco elementi consentiti e i collegamenti Web aggiunti tramite **App client** e **Configurazione del dispositivo**. Per l'elenco completo di impostazioni disponibili in **Configurazione dispositivo** che influiscono su Managed Home Screen, vedere [Impostazioni di un dispositivo dedicato](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).  

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
| Enable notifications badge (Abilita notifiche) | bool | FALSE | Abilita le notifiche per le icone delle app che mostrano il numero delle nuove notifiche ricevute. Se si abilita questa impostazione, gli utenti finali vedranno il numero di notifiche da leggere per le app. Se si mantiene disabilitata questa chiave di configurazione, gli utenti finali non vedranno le eventuali notifiche da leggere per le app. |
| Lock Home Screen (Blocca schermata iniziale) | bool | TRUE | Impedisce all'utente finale di spostare le icone delle app nella schermata iniziale. Se si abilita questa chiave di configurazione, le icone delle app saranno bloccate nella schermata iniziale e l'utente finale non potrà trascinarle in posizioni diverse della griglia. Se impostata su `false`, gli utenti finali potranno spostare le icone di applicazioni e collegamenti Web nella schermata iniziale gestita.  |
| Set device wall paper (Imposta sfondo del dispositivo) | string | Predefinito | Consente di impostare uno sfondo a scelta immettendo l'URL dell'immagine da usare. |
| Set app icon size (Imposta dimensioni delle icone delle app) | integer | 2 | Consente di impostare le dimensioni delle icone per le app visualizzate nella schermata inziale. È possibile scegliere i valori seguenti in questa configurazione per le diverse dimensioni: 0 (minime), 1 (piccole), 2 (regolari), 3 (grandi) e 4 (massime). |
| Set app folder icon (Imposta icona delle cartelle di app) | integer | 0 | Consente di definire l'aspetto delle cartelle delle app nella schermata iniziale. È possibile scegliere l'aspetto dai valori seguenti: 0 (quadrato scuro), 1 (cerchio scuro), 2 (quadrato chiaro), 3 (cerchio chiaro). |
| Set screen orientation (Imposta orientamento schermo) | integer | 1 | Consente di impostare l'orientamento della schermata iniziale sulla modalità verticale, orizzontale o con rotazione automatica. Per impostare l'orientamento, immettere il valore 1 (modalità verticale), 2 (modalità orizzontale) o 3 (rotazione automatica). |
| Enable device telemetry (Abilita telemetria del dispositivo) | bool | FALSE | Abilita tutti i dati di telemetria acquisiti per la schermata iniziale gestita. Se si abilita questa impostazione, Microsoft potrà acquisire i dati di telemetria sull'utilizzo del dispositivo, ad esempio il numero di volte in cui è stata avviata una specifica app. |
| Set allow-listed applications (Imposta applicazioni nell'elenco elementi consentiti) | bundleArray | FALSE | Consente di definire il set di app visibili nella schermata iniziale tra le app installate nel dispositivo. Per definire le app, immettere il nome del pacchetto delle app da rendere visibili, ad esempio com.microsoft.emmx per rendere le impostazioni accessibili nella schermata iniziale. Le app da aggiungere nell'elenco elementi consentiti in questa sezione devono essere già installate nel dispositivo per renderle visibili nella schermata iniziale. |
| Set pinned web links (Imposta collegamenti Web aggiunti) | bundleArray | FALSE | Consente di aggiungere i siti Web come icone di avvio rapido nella schermata iniziale. Con questa configurazione è possibile definire l'URL e aggiungerlo nella schermata iniziale per consentire all'utente finale di avviarlo nel browser con un singolo tocco. |
| Enable screen saver (Abilita screen saver) | bool | FALSE | Per abilitare o non abilitare la modalità screen saver. Se impostata su True, è possibile configurare **screen_saver_image**, **screen_saver_show_time**, **inactive_time_to_show_screen_saver** e **media_detect_screen_saver**. |
| Screen saver image (Immagine screen saver) | string |   | Consente di impostare l'URL dell'immagine dello screen saver. Se non viene impostato un URL, nei dispositivi verrà visualizzata l'immagine dello screen saver predefinita quando è attivato lo screen saver. L'immagine predefinita visualizza l'icona dell'app Managed Home Screen.  |
| Screen saver show time (Durata dello screen saver) | integer | 0 | Offre la possibilità di impostare la durata, in secondi, dello screen saver visualizzato nel dispositivo in modalità screen saver. Se impostata su 0, lo screen saver verrà visualizzato per un tempo indefinito in modalità screen saver finché il dispositivo non diventa attivo.  |
| Inactive time to enable screen saver (Tempo di inattività per abilitare lo screen saver) | integer | 30 | Il numero di secondi durante il quale il dispositivo è inattivo prima che venga attivato lo screen saver. Se impostata su 0, il dispositivo non passerà mai in modalità screen saver. |
| Media detect before showing screen saver (Rilevamento di contenuti multimediali prima dello screen saver) | bool | TRUE | Scegliere se nel dispositivo dovrà essere visualizzato lo screen saver durante la riproduzione di audio o video. Se impostata su True, il dispositivo non riprodurrà audio o video, indipendentemente dal valore di **inactive_time_to_show_scree_saver**. Se impostata su False, nel dispositivo verrà visualizzato lo screen saver in base al valore impostato in **inactive_time_to_show_screen_saver**.   |
| Enable virtual home button (Abilita il pulsante di schermata iniziale virtuale) | bool | FALSE | Se impostata su `True`, l'utente finale avrà accesso a un pulsante della schermata iniziale di Managed Home Screen che consentirà di tornare in Managed Home Screen dall'attività corrente.  |
| Type of virtual home button (Tipo di pulsante di schermata iniziale virtuale) | string | swipe_up | Usare **swipe_up** per accedere al pulsante della pagina iniziale con un gesto di scorrimento in alto. Usare **float** per accedere a un pulsante della schermata iniziale persistente e permanente che l'utente finale può spostare nella schermata. |
| Battery and Signal Strength indicator bar (Barra indicatore potenza segnale e batteria) | bool | True  | Se impostata su `True`, visualizza la barra indicatore della potenza del segnale e della batteria. |
| Exit lock task mode password (Password di uscita dalla modalità blocco attività) | string |   | Immettere un codice di 4-6 cifre da usare per uscire temporaneamente dalla modalità blocco attività per la risoluzione dei problemi. |
| Show Wi-Fi setting (Mostra impostazioni Wi-Fi) | bool | FALSE | Se impostata su `True`, l'utente finale può attivare o disattivare il Wi-Fi oppure connettersi a reti Wi-Fi diverse.  |
| Show Bluetooth setting (Mostra impostazione Bluetooth) | bool | FALSE | Se impostata su `True`, l'utente finale può attivare o disattivare il Bluetooth oppure connettersi ad altri dispositivi abilitati per Bluetooth.   |
| Applications in folder are ordered by name (Le applicazioni nella cartella sono ordinate per nome) | bool | TRUE | Se impostata su `False`, gli elementi in una cartella vengono visualizzati nell'ordine in cui sono specificati. In caso contrario vengono visualizzati in ordine alfabetico nella cartella.   |
| Application order enabled (Ordine delle applicazioni abilitato) | bool | FALSE | Se impostata su `True` è possibile impostare l'ordine di applicazioni, collegamenti Web e cartelle in Managed Home Screen. Dopo l'abilitazione, impostare l'ordinamento con **app_order**. L'utente finale può attivare o disattivare il Bluetooth e connettersi ad altri dispositivi abilitati per Bluetooth.   |
| Application order (Ordine delle applicazioni) | bundleArray | FALSE | Consente di specificare l'ordine di applicazioni, collegamenti Web e cartelle in Managed Home Screen. Per usare questa impostazione, l'impostazione **Lock Home Screen** (Blocca schermata iniziale) deve essere abilitata, l'opzione **Set Grid Size** (Imposta dimensioni griglia) deve essere definita e l'opzione **Application order enabled** (Ordine delle applicazioni abilitato) deve essere impostata su `True`.   |

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
            "key": "screen_orientation",
            "valueInteger": 1
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
            "key": "grid_size",
            "valueString": "4;5"
        },
        {
            "key": "app_order_enabled",
            "valueBool": true
        },
        {
            "key": "apps_in_folder_ordered_by_name",
            "valueBool": true
        },
        {
            "key": "app_orders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.Microsoft.emmx"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 1
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Work"
                        },
                        {
                            "key": "type",
                            "valueString": "managed_folder"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 2
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.launcher.enterprise"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "class",
                            "valueString": "com.microsoft.launcher.launcher"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 3
                        }
                    ]
                }
            ]
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

## <a name="googles-android-device-policy-app"></a>App Google Apps Device Policy per Android
L'app di schermata iniziale gestita ora consente l'accesso a Google Apps Device Policy per Android. L'app di schermata iniziale gestita è un'utilità di avvio personalizzata usata per i dispositivi registrati in Intune come dispositivi dedicati Android Enterprise (AE) che usano la modalità tutto schermo per più app. È possibile accedere all'app Android Device Policy o guidare gli utenti all'app Android Device Policy per fini di supporto e debug. Questa funzionalità di avvio è disponibile nel momento in cui il dispositivo viene registrato e bloccato nella schermata iniziale gestita. Per usare questa funzionalità non è necessaria alcuna installazione aggiuntiva.

## <a name="managed-home-screen-debug-screen"></a>Schermata di debug della schermata iniziale gestita
È possibile accedere alla schermata di debug della schermata iniziale gestita facendo clic sul pulsante **Indietro** fino a quando non viene visualizzata la schermata di debug (fare clic sul pulsante **Indietro** 15 volte o più). Da questa schermata di debug è possibile avviare l'applicazione Android Device Policy, visualizzare e caricare i log o sospendere temporaneamente la modalità tutto schermo per aggiornare il dispositivo. Per altre informazioni su come sospendere la modalità tutto schermo, vedere l'elemento **Esci dalla modalità tutto schermo** nelle [impostazioni dei dispositivi dedicati](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings) Android Enterprise.

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sui dispositivi Android Enterprise dedicati, vedere [Configurare la registrazione in Intune di dispositivi Android Enterprise dedicati](../enrollment/android-kiosk-enroll.md).
