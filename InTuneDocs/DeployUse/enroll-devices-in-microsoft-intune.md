---
title: Registrare i dispositivi | Microsoft Intune
description: Gestione dei dispositivi mobili (MDM) usa la registrazione per gestire i dispositivi e consentire l'accesso alle risorse.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6b182ebab1691c62e69cabaf4689ac7395ab31a
ms.openlocfilehash: 0995d3ced978f5213fdb0e9905f508b64a1e5c09


---

# Registrare i dispositivi per la gestione in Intune
È possibile registrare i dispositivi, inclusi i PC Windows, per abilitare la gestione di dispositivi mobili (MDM, Mobile Device Management) con Microsoft Intune. Questo argomento descrive i diversi modi per registrare i dispositivi mobili per la gestione con Intune. La modalità di registrazione dei dispositivi varia a seconda del tipo di dispositivo in uso, della proprietà e del livello di gestione necessario. La registrazione BYOD (Bring Your Own Device) consente agli utenti di registrare i propri telefoni, tablet o PC personali. La registrazione dei dispositivi di proprietà dell'azienda (COD) rende possibili scenari di gestione come la cancellazione remota, i dispositivi condivisi o l'affinità utente per un dispositivo.

Se si usa [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), sia in locale che ospitato nel cloud, è possibile abilitare la gestione semplice con Intune, senza registrazione. I PC Windows possono essere anche gestiti tramite il [software client di Intune](#manage-windows-pcs-with-intune).

## Panoramica dei metodi di registrazione dei dispositivi

La tabella seguente illustra i metodi di registrazione di Intune con le relative funzionalità supportate. Queste funzionalità includono:
- **Cancellazione** - Ripristino delle impostazioni predefinite del dispositivo, con rimozione di tutti i dati. [Retire devices (Ritirare i dispositivi)](retire-devices-from-microsoft-intune-management.md)
- **Affinità** - Associare i dispositivi agli utenti. Funzionalità richiesta per la gestione di applicazioni per dispositivi mobili (MAM) e l'accesso condizionale ai dati aziendali. [Affinità utente](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **Blocco** - Impedire agli utenti di rimuovere il dispositivo dal sistema di gestione. Per il blocco dei dispositivi iOS è richiesta la modalità con supervisione. [Blocco remoto](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**Metodi di registrazione per iOS**

| **Metodo** |  **Cancellazione** |  **Affinità**    |   **Blocco** | **Dettagli** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [informazioni](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   No |No |No  | [informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   sì |   Facoltativo |  Facoltativo|[informazioni](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| sì |   Facoltativo |  No| [informazioni](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[informazioni](ios-direct-enrollment-in-microsoft-intune.md)|

**Metodi di registrazione per Windows e Android**

| **Metodo** |  **Cancellazione** |  **Affinità**    |   **Blocco** | **Dettagli**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [informazioni](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   No |No |No  |[informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Per una serie di domande utili per individuare il metodo corretto, vedere [Scegliere come registrare i dispositivi mobili](/intune/get-started/choose-how-to-enroll-devices1).

## BYOD
Gli utenti BYOD (Bring Your Own Device) installano l'app Portale aziendale e registrano il dispositivo di loro proprietà. Questo può consentire agli utenti di connettersi alla rete aziendale, aggiungersi al dominio o ad Azure Active Directory. L'abilitazione della registrazione BYOD costituisce un prerequisito per molti scenari COD per la maggior parte delle piattaforme. Vedere [Prerequisiti per la registrazione del dispositivo](prerequisites-for-enrollment.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

## Dispositivi di proprietà dell'azienda
È possibile gestire i dispositivi di proprietà dell'azienda usando la console di Intune. I dispositivi iOS possono essere registrati direttamente mediante gli strumenti di Apple. Tutti i tipi di dispositivo possono essere registrati da un amministratore o da un responsabile usando il manager di registrazione dispositivi. È anche possibile identificare e contrassegnare come dispositivo di proprietà dell'azienda i dispositivi con numero IMEI e abilitare questo tipo di registrazione.

[Registrare i dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md)

### DEM
Il manager di registrazione dispositivi è un account speciale di Intune usato per registrare e gestire più dispositivi di proprietà dell'azienda. I manager possono installare il Portale aziendale e registrare molti dispositivi senza utente associato. Altre informazioni su [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### DEP
La gestione del programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple consente di creare e distribuire i criteri a distanza ai dispositivi acquistati e gestiti tramite DEP. Il dispositivo viene registrato quando l'utente accende il dispositivo per la prima volta ed esegue l'Assistente configurazione di iOS. Questo metodo supporta la modalità **supervisionato** di iOS, che a sua volta attiva:
  - Registrazione bloccata
  - Accesso condizionale
  - Rilevamento jailbreak
  - Gestione per applicazioni mobili

Altre informazioni su [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### USB-SA
Connessione USB, registrazione con Assistente configurazione. L'amministratore crea criteri di Intune e li esporta in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono preparati con i criteri di Intune. L'amministratore deve registrare manualmente ogni dispositivo. Gli utenti ricevono i propri dispositivi ed eseguono Assistente configurazione per registrare il dispositivo. Questo metodo supporta la modalità **supervisionato** di iOS, che a sua volta attiva:
  - Accesso condizionale
  - Rilevamento jailbreak
  - Gestione per applicazioni mobili

Altre informazioni sulla [registrazione Assistente configurazione con Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### USB-Direct
Registrazione diretta. L'amministratore crea criteri di Intune e li esporta in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono registrati direttamente senza richiedere il ripristino delle impostazioni predefinite. L'amministratore deve registrare manualmente ogni dispositivo. I dispositivi vengono gestiti come dispositivi senza utente associato. Non vengono bloccati né supervisionati e non supportano l'accesso condizionale, il rilevamento jailbreak e la gestione di applicazioni mobili. Altre informazioni sulla [registrazione diretta con Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

## Gestione dei dispositivi mobili con Exchange ActiveSync e Intune
I dispositivi mobili che non sono registrati, ma che sono connessi a Exchange ActiveSync, possono essere gestiti da Intune mediante i criteri MDM di EAS. Intune usa Exchange Connector per comunicare con EAS, in locale oppure ospitato nel cloud.

[Gestione dei dispositivi mobili con Exchange ActiveSync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Gestire i PC Windows con Intune  
È anche possibile usare Microsoft Intune per gestire i PC Windows che implementano il software client di Intune. I PC gestiti con il client di Intune possono:

 - Compilare relazioni su inventari software e hardware
 - Installare applicazioni desktop, ad esempio file con estensione msi ed exe
 - Impostazioni del firewall

I PC gestiti con il software client di Intune non possono essere cancellati e non possono sfruttare le numerose funzionalità di gestione di Intune, ad esempio l'accesso condizionale, le impostazioni VPN e Wi-Fi o la distribuzione di certificati e le configurazioni di posta elettronica.

[Gestire i PC Windows con Intune](manage-windows-pcs-with-microsoft-intune.md)

##  Piattaforme per dispositivi supportate

Intune può gestire le piattaforme dei dispositivi seguenti:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Passaggi successivi
- [Prerequisiti per la registrazione del dispositivo](prerequisites-for-enrollment.md)
- [Gestire i dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md)
- [Dispositivi mobili e computer supportati](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Sep16_HO3-->


