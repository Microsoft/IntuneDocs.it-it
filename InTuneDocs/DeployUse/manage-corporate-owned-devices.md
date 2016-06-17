---
# required metadata

title: Gestire i dispositivi di proprietà dell'azienda | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrare i dispositivi di proprietà dell'azienda con Microsoft Intune
I dispositivi di proprietà dell'organizzazione o dell'azienda possono essere inclusi nella gestione di Intune in diversi modi a seconda del dispositivo, di come è stato acquistato e delle esigenze dell'organizzazione.

## Dispositivi iOS di proprietà dell'azienda
Questi metodi di registrazione sono adatti per gli scenari CYOD (Choose Your Own Device) in cui l'organizzazione acquista i dispositivi per gli utenti ma vuole mantenere la gestione dei dispositivi. Se l'organizzazione ha acquistato dispositivi iOS, è possibile preconfigurare la registrazione in modo che la gestione dei dispositivi sia possibile fin dalla prima volta che questi ultimi vengono accesi dai rispettivi utenti. Intune supporta la registrazione tramite il [programma di registrazione dispositivi di Apple (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) o tramite lo strumento Apple Configurator in esecuzione in un computer Mac per la registrazione [diretta](ios-direct-enrollment-in-microsoft-intune.md) o con [Assistente configurazione](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Registrare i dispositivi iOS di proprietà dell'azienda](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Manager di registrazione dispositivi
Le organizzazioni possono usare Intune per gestire un numero elevato di dispositivi mobili con un unico account utente, detto manager di registrazione dispositivi. Dopo la creazione, un account manager di registrazione dispositivi può essere usato da un gestore per registrare più dei cinque dispositivi standard consentiti per impostazione predefinita agli utenti normali. La registrazione di dispositivi con un manager di registrazione dispositivi funziona solo per i dispositivi non usati da un utente specifico. Questi dispositivi sono ideali per app POS o utilità, ad esempio, ma non sono adatti per gli utenti che devono accedere alla posta elettronica o alle risorse della società.

[Registrare i dispositivi di proprietà dell'azienda con il manager di registrazione dispositivi](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## International Mobile Equipment Identity (IMEI)
I numeri IMEI (International Mobile Equipment Identity) univoci costituiscono una proprietà di dispositivo diffusa per molti produttori di dispositivi mobili. Gli amministratori Intune possono importare numeri IMEI per i dispositivi di proprietà della società. Quando il dispositivo passa alla gestione con Intune, può essere contrassegnato come dispositivo di proprietà dell'azienda ed essere soggetto a criteri appropriati.

[Specificare i dispositivi aziendali con i numeri IMEI (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

## Panoramica dei metodi di registrazione dei dispositivi di proprietà dell'azienda

La tabella seguente illustra i metodi di registrazione per i dispositivi di proprietà dell'azienda con i relativi vantaggi.

**Metodi di registrazione per iOS**

| **Metodo** |  **[Reimposta](#Reset)** |   **[Affinità](#Affinity)**   |   **[Bloccato](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | No|    Sì |   No |
|**[DEM](#DEM)**|   No |No |No  |
|**[DEP](#DEP)**|   sì |   Opt |   Opt|
|**[USB-SA](#USB-SA)**| sì |   Opt |   No|
|**[USB-Direct](#USB-Direct)**| No |    No  | No|

**Metodi di registrazione per Windows e Android**

| **Metodo** |  **[Cancellazione](#Wipe)** | **[User](#User)**   |   **[Bloccato](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | No|    Sì |   No |
|**[DEM](#DEM)**|   No |No |No  |

**Metodi di registrazione per i dispositivi di proprietà dell'azienda**

### BYOD
Bring Your Own Device (uso del dispositivo personale). Gli utenti installano l'app Portale aziendale e registrano il dispositivo di loro proprietà. Quando un dispositivo viene registrato nel Portale aziendale viene anche aggiunto all'area di lavoro. La registrazione di dispositivi iOS nel Portale aziendale richiede un ID Apple. La modalità BYOD non richiede operazioni di configurazione aggiuntive per i dispositivi di proprietà dell'azienda. Vedere la procedura [Impostare la gestione dei dispositivi](get-ready-to-enroll-devices-in-microsoft-intune#set-up-device-management.md). ([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods))

### DEM
Manager di registrazione dispositivi (Device Enrollment Manager). Gli account DEM vengono creati dall'amministratore. I manager possono quindi installare il Portale aziendale e registrare molti dispositivi senza utente associato. Altre informazioni su [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods))

### DEP
Programma di registrazione dispositivi Apple (Device Enrollment Program). L'amministratore crea e distribuisce i criteri a distanza ai dispositivi acquistati e gestiti tramite DEP. Il dispositivo viene registrato quando l'utente esegue l'Impostazione assistita iOS. Questo metodo supporta la modalità **supervisionato** di iOS, che a sua volta attiva:
  - Registrazione bloccata
  - Accesso condizionale
  - Rilevamento jailbreak
  - Gestione per applicazioni mobili

Altre informazioni su [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods))

### USB-SA
Connessione USB, registrazione con Assistente configurazione. L'amministratore crea criteri di Intune e li esporta in Apple Configurator. I dispositivi connessi tramite USB vengono preparati con i criteri di Intune. L'amministratore deve registrare manualmente ogni dispositivo. Gli utenti ricevono i propri dispositivi ed eseguono Assistente configurazione per registrare il dispositivo. Questo metodo supporta la modalità **supervisionato** di iOS, che a sua volta attiva:
  - Accesso condizionale
  - Rilevamento jailbreak
  - Gestione per applicazioni mobili

Altre informazioni sulla [registrazione Assistente configurazione con Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods))

### USB-Direct
Registrazione diretta. L'amministratore crea criteri di Intune e li esporta in Apple Configurator. I dispositivi connessi tramite USB vengono registrati direttamente senza richiedere il ripristino delle impostazioni predefinite. L'amministratore deve registrare manualmente ogni dispositivo. I dispositivi vengono gestiti come dispositivi senza utente associato. Non vengono bloccati né supervisionati e non supportano l'accesso condizionale, il rilevamento jailbreak e la gestione di applicazioni mobili. Altre informazioni sulla [registrazione diretta con Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods))

**Comportamento per i dispositivi mobili di proprietà dell'azienda**

### Reimposta
Specifica se per la registrazione è necessario il ripristino delle impostazioni predefinite del dispositivo, con la rimozione di tutti i dati e il ripristino allo stato originale.
([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods))

### Affinità
Specifica se il metodo di registrazione supporta "Affinità utente", che connette un dispositivo a un utente specifico. I dispositivi "Opt" possono essere registrati con o senza affinità utente. L'affinità utente è necessaria per supportare quanto segue:
  - App per la gestione di applicazioni mobili (MAM)
  - Accesso condizionale ai dati aziendali e della posta elettronica
  - App Portale aziendale

([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods))

### Blocco
Specifica se il dispositivo può essere bloccato per impedire all'utente di rimuovere i criteri di Intune, scollegando il dispositivo dalla gestione. Per i dispositivi iOS, il blocco del dispositivo può essere eseguito solo in modalità Supervisionato.
([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods)) ([Torna alla tabella](#overview-of corporate-owned-device-enrollment-methods))


<!--HONumber=Jun16_HO3-->


