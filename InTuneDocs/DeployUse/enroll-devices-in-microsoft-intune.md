---
title: Registrare i dispositivi | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69cf07aa0747448e0ef3384b5b5132e0e76aed45
ms.openlocfilehash: 930cbc806d8fd1185cf33fd64d866b88ec9a6a04


---

# Registrare i dispositivi per la gestione in Intune
La Gestione dei dispositivi mobili di Microsoft Intune (MDM) usa la registrazione per gestire i dispositivi e consentire l'accesso alle risorse. Il modo di registrazione dei dispositivi varia a seconda del tipo di dispositivo in uso, della proprietà e del livello di gestione necessario. Per i dispositivi BYOD e di proprietà dell'azienda è necessario un processo di registrazione. Le aziende che usano Exchange ActiveSync, locale oppure ospitato nel cloud, possono abilitare una gestione semplificata senza necessità di registrazione. I PC Windows possono essere gestiti tramite il software client di Intune.

###  Piattaforme per dispositivi supportate

Intune può gestire le piattaforme dei dispositivi seguenti:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Panoramica dei metodi di registrazione dei dispositivi

La tabella seguente illustra i metodi di registrazione per i dispositivi di proprietà dell'azienda con i relativi vantaggi.

**Metodi di registrazione per iOS**

| **Metodo** |  **[Cancellazione](#Wipe)** | **[Affinità](#Affinity)**   |   **[Bloccato](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | No|    Sì |   No |
|**[DEM](#DEM)**|   No |No |No  |
|**[DEP](#DEP)**|   sì |   Opt |   Opt|
|**[USB-SA](#USB-SA)**| sì |   Opt |   No|
|**[USB-Direct](#USB-Direct)**| No |    No  | No|

**Metodi di registrazione per Windows e Android**

| **Metodo** |  **[Cancellazione](#Wipe)** | **[Affinità](#Affinity)**   |   **[Bloccato](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | No|    Sì |   No |
|**[DEM](#DEM)**|   No |No |No  |

**Metodi di registrazione per i dispositivi di proprietà dell'azienda**

### BYOD
Bring Your Own Device (uso del dispositivo personale). Gli utenti installano l'app Portale aziendale e registrano il dispositivo di loro proprietà. Quando un dispositivo viene registrato nel Portale aziendale viene anche aggiunto all'area di lavoro. La registrazione di dispositivi iOS nel Portale aziendale richiede un ID Apple. La modalità BYOD non richiede operazioni di configurazione aggiuntive per i dispositivi di proprietà dell'azienda. Vedere la procedura di [configurazione della gestione dei dispositivi](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management). ([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods))

### DEM
Manager di registrazione dispositivi (Device Enrollment Manager). L'amministratore crea account DEM per gestire i dispositivi di proprietà dell'azienda. I manager possono quindi installare il Portale aziendale e registrare molti dispositivi senza utente associato. Altre informazioni su [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods))

### DEP
Programma di registrazione dispositivi Apple (Device Enrollment Program). L'amministratore crea e distribuisce i criteri a distanza ai dispositivi iOS di proprietà dell'azienda acquistati e gestiti tramite Protezione esecuzione programmi. Il dispositivo viene registrato quando l'utente esegue l'Impostazione assistita iOS. Questo metodo supporta la modalità **supervisionato** di iOS, che a sua volta attiva:
  - Registrazione bloccata
  - Accesso condizionale
  - Rilevamento jailbreak
  - Gestione per applicazioni mobili

Altre informazioni su [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods))

### USB-SA
Connessione USB, registrazione con Assistente configurazione. L'amministratore crea criteri di Intune e li esporta in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono preparati con i criteri di Intune. L'amministratore deve registrare manualmente ogni dispositivo. Gli utenti ricevono i propri dispositivi ed eseguono Assistente configurazione per registrare il dispositivo. Questo metodo supporta la modalità **supervisionato** di iOS, che a sua volta attiva:
  - Accesso condizionale
  - Rilevamento jailbreak
  - Gestione per applicazioni mobili

Altre informazioni sulla [registrazione Assistente configurazione con Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods))

### USB-Direct
Registrazione diretta. L'amministratore crea criteri di Intune e li esporta in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono registrati direttamente senza richiedere il ripristino delle impostazioni predefinite. L'amministratore deve registrare manualmente ogni dispositivo. I dispositivi vengono gestiti come dispositivi senza utente associato. Non vengono bloccati né supervisionati e non supportano l'accesso condizionale, il rilevamento jailbreak e la gestione di applicazioni mobili. Altre informazioni sulla [registrazione diretta con Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods))

**Comportamento per i dispositivi mobili di proprietà dell'azienda**

### Cancellazione
Specifica se per la registrazione è necessario il ripristino delle impostazioni predefinite del dispositivo, con la rimozione di tutti i dati e il ripristino allo stato originale.
([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods))

### Affinità
Specifica se il metodo di registrazione supporta "Affinità utente", che connette un dispositivo a un utente specifico. I dispositivi "Opt" possono essere registrati con o senza affinità utente. L'affinità utente è necessaria per supportare quanto segue:
  - App per la gestione di applicazioni mobili (MAM)
  - Accesso condizionale ai dati aziendali e della posta elettronica
  - App Portale aziendale

([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods))

### Blocco
Specifica se il dispositivo può essere bloccato per impedire all'utente di rimuovere i criteri di Intune, scollegando il dispositivo dalla gestione. Per i dispositivi iOS, il blocco del dispositivo può essere eseguito solo in modalità Supervisionato.
([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods)) ([Torna alla tabella](#overview-of-corporate-owned-device-enrollment-methods))

## Abilitare la registrazione dei dispositivi  
 La registrazione consente agli utenti di accedere a risorse aziendali dai dispositivi personali e all'amministratore di verificare che tali dispositivi siano conformi ai criteri di protezione delle risorse aziendali. È il modo migliore per abilitare gli scenari BYOD con Intune. L'amministratore deve abilitare la registrazione nella console di Intune. È possibile che sia necessario creare una relazione di trust con il dispositivo e assegnare licenze agli utenti. Il dispositivo viene registrato quindi registrato, generalmente dopo che gli utenti immettono le proprie credenziali aziendali o dell'istituto di istruzione. A questo punto il dispositivo riceve i criteri di Intune e può accedere alle risorse.

[Prepararsi alla registrazione dei dispositivi in Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)

## Registrare i dispositivi di proprietà dell'azienda
È possibile gestire i dispositivi di proprietà dell'azienda usando la console di Intune. I dispositivi iOS possono essere registrati direttamente mediante gli strumenti di Apple. Tutti i tipi di dispositivo possono essere registrati da un amministratore o da un responsabile usando il manager di registrazione dispositivi. È anche possibile identificare e contrassegnare come dispositivo di proprietà dell'azienda i dispositivi con numero IMEI e abilitare questo tipo di registrazione.

[Registrare i dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md)

## Gestione dei dispositivi mobili con Exchange ActiveSync e Intune
I dispositivi mobili che non sono registrati, ma che sono connessi a Exchange ActiveSync, possono essere gestiti da Intune mediante i criteri MDM di EAS. Intune usa Exchange Connector per comunicare con EAS, in locale oppure ospitato nel cloud.



[Gestione dei dispositivi mobili con Exchange ActiveSync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Gestire i PC Windows con Intune  
È anche possibile usare Microsoft Intune per gestire i PC Windows che implementano il software client di Intune per PC Windows. I PC gestiti con il client di Intune possono:

 - Compilare relazioni su inventari software e hardware
 - Installare applicazioni desktop, ad esempio file con estensione msi ed exe
 - Impostazioni del firewall

I computer gestiti con il software client di Intune non possono essere cancellati o ritirati in modo selettivo e non possono sfruttare le numerose funzionalità di gestione di Intune, ad esempio l'accesso condizionale, le impostazioni VPN e Wi-Fi o la distribuzione di certificati e le configurazioni di posta elettronica.

[Gestire i PC Windows con Intune](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Jun16_HO5-->


