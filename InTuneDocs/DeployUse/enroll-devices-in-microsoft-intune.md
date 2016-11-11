---
title: Registrare i dispositivi | Microsoft Intune
description: Gestione dei dispositivi mobili (MDM) usa la registrazione per gestire i dispositivi e consentire l&quot;accesso alle risorse.
keywords: 
author: staciebarker
ms.author: stabar
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
ms.sourcegitcommit: 289e6019aa1a17deb91b38ed32f0432af0902a9d
ms.openlocfilehash: 3422d47a5759e22a512cf6de8578d774ad3bb8cd


---

# <a name="enroll-devices-for-management-in-intune"></a>Registrare i dispositivi per la gestione in Intune
È possibile registrare i dispositivi, inclusi i PC Windows, per abilitare la gestione di dispositivi mobili (MDM, Mobile Device Management) con Microsoft Intune. Questo argomento descrive i diversi modi per registrare i dispositivi mobili per la gestione con Intune. Il modo di registrazione dei dispositivi varia a seconda del tipo di dispositivo in uso, della proprietà e del livello di gestione necessario. La registrazione BYOD (Bring Your Own Device) consente agli utenti di registrare i propri telefoni, tablet o PC personali. La registrazione dei dispositivi di proprietà dell'azienda (COD) rende possibili scenari di gestione come la cancellazione remota, i dispositivi condivisi o l'affinità utente per un dispositivo.

Se si usa [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), sia in locale che ospitato nel cloud, è possibile abilitare la gestione semplice con Intune, senza registrazione. I PC Windows possono essere anche gestiti tramite il [software client di Intune](#manage-windows-pcs-with-intune).

## <a name="overview-of-device-enrollment-methods"></a>Panoramica dei metodi di registrazione dei dispositivi

La tabella seguente illustra i metodi di registrazione di Intune con le relative funzionalità supportate. Queste funzionalità includono:
- **Cancellazione** - Ripristino delle impostazioni predefinite del dispositivo, con rimozione di tutti i dati. Per altre informazioni, vedere [Disattivare i dispositivi](retire-devices-from-microsoft-intune-management.md).
- **Affinità** - Associare i dispositivi agli utenti. Funzionalità richiesta per la gestione di applicazioni per dispositivi mobili (MAM) e l'accesso condizionale ai dati aziendali. Per altre informazioni, vedere [Affinità utente](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices).
- **Blocco**: impedisce agli utenti di rimuovere il dispositivo dal sistema di gestione. Per il blocco dei dispositivi iOS è richiesta la modalità con supervisione. Per altre informazioni, vedere [Blocco remoto](retire-devices-from-microsoft-intune-management.md#block-access-a-device).

**Metodi di registrazione per iOS**

| **Metodo** |  **Cancellazione** |  **Affinità**    |   **Blocco** | **Informazioni dettagliate** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   No |No |No  | [Altre informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   sì |   Facoltativo |  Facoltativo|[Altre informazioni](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| sì |   Facoltativo |  No| [Altre informazioni](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[Altre informazioni](ios-direct-enrollment-in-microsoft-intune.md)|

**Metodi di registrazione per Windows**

| **Metodo** |  **Cancellazione** |  **Affinità**    |   **Blocco** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | sì|   Sì |   No | [Altre informazioni](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   No |No |No  |[Altre informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Metodi di registrazione per Android**

| **Metodo** |  **Cancellazione** |  **Affinità**    |   **Blocco** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   No |No |No  |[Altre informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Per una serie di domande e risposte utili per individuare il metodo corretto, vedere [Scegliere come registrare i dispositivi mobili](/intune/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
Gli utenti BYOD (Bring Your Own Device) installano l'app Portale aziendale e registrano il dispositivo di loro proprietà. Ciò consente agli utenti di connettersi alla rete aziendale e creare un join al domino o a Azure Active Directory. Per la maggior parte delle piattaforme, è necessario abilitare la registrazione di BYOD per molti scenari di COD (Corporate-Owned Devices, Dispositivi di proprietà dell'azienda). Per altre informazioni, vedere [Prerequisiti per la registrazione del dispositivo](prerequisites-for-enrollment.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

## <a name="corporateowned-devices"></a>Dispositivi di proprietà dell'azienda
È possibile gestire i dispositivi di proprietà dell'azienda (COD) tramite la console di Intune. I dispositivi iOS possono essere registrati direttamente tramite gli strumenti offerti da Apple. Tutti i tipi di dispositivo possono essere registrati da un amministratore o da un responsabile usando il manager di registrazione dispositivi. È anche possibile identificare e contrassegnare come dispositivo di proprietà dell'azienda i dispositivi con numero IMEI e abilitare questo tipo di registrazione.

Per altre informazioni, vedere [Registrare i dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md).

### <a name="dem"></a>DEM
Il Manager di registrazione dispositivi è un account speciale di Intune usato per registrare e gestire più dispositivi di proprietà dell'azienda. I manager possono installare il Portale aziendale e registrare molti dispositivi senza utente associato. Altre informazioni su [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
La gestione del programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple consente di creare e distribuire i criteri in modalità wireless ai dispositivi acquistati e gestiti tramite DEP. Il dispositivo viene registrato quando l'utente accende il dispositivo per la prima volta ed esegue l'Assistente configurazione di iOS. Questo metodo supporta la modalità **supervisione iOS**, che a sua volta abilita:
  - Registrazione bloccata
  - Accesso condizionale
  - Rilevamento jailbreak
  - Gestione per applicazioni mobili

Altre informazioni su [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### <a name="usbsa"></a>USB-SA
I dispositivi di proprietà dell'azienda connessi tramite USB vengono preparati con i criteri di Intune. Per la registrazione tramite l'Assistente configurazione, l'amministratore crea criteri di Intune e li esporta in Apple Configurator. L'amministratore deve registrare ogni dispositivo manualmente. Gli utenti ricevono i propri dispositivi ed eseguono Assistente configurazione per registrare il dispositivo. Questo metodo supporta la modalità **supervisione iOS**, che a sua volta abilita:
  - Accesso condizionale
  - Rilevamento jailbreak
  - Gestione per applicazioni mobili

Altre informazioni sulla [registrazione Assistente configurazione con Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### <a name="usbdirect"></a>USB-Direct
Per una registrazione diretta, l'amministratore crea criteri di Intune e li esporta in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono registrati direttamente e non richiedono il ripristino delle impostazioni predefinite. L'amministratore deve registrare ogni dispositivo manualmente. I dispositivi vengono gestiti come dispositivi senza utente associato. Non vengono bloccati né supervisionati e non possono supportare l'accesso condizionale, il rilevamento jailbreak o la gestione di applicazioni mobili. Altre informazioni sulla [registrazione diretta con Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Gestione dei dispositivi mobili con Exchange ActiveSync e Intune
I dispositivi mobili che non sono registrati, ma che sono connessi a Exchange ActiveSync, possono essere gestiti da Intune mediante i criteri MDM di EAS. Intune usa Exchange Connector per comunicare con EAS (Exchange Active Sync), in locale oppure ospitato nel cloud.

Per altre informazioni, vedere [Gestione dei dispositivi mobili con Exchange Active Sync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).


## <a name="windows-pc-management-with-intune"></a>Gestione di PC Windows con Intune  
È anche possibile usare Microsoft Intune per gestire i PC Windows con il software del client di Intune. I PC gestiti con il client di Intune possono:

 - Compilare relazioni su inventari software e hardware
 - Installare applicazioni desktop, ad esempio file con estensione msi ed exe
 - Impostazioni del firewall

I PC gestiti con il software del client di Intune non possono essere completamente cancellati, anche se è disponibile la cancellazione selettiva. I PC gestiti con il software del client di Intune non possono sfruttare le numerose funzionalità di gestione di Intune, ad esempio l'accesso condizionale, le impostazioni VPN e Wi-Fi o la distribuzione di certificati e le configurazioni di posta elettronica.

Per altre informazioni, vedere [Gestire PC Windows con Intune](manage-windows-pcs-with-microsoft-intune.md).

## <a name="supported-device-platforms"></a>Piattaforme per dispositivi supportate

Intune può gestire le piattaforme dei dispositivi seguenti:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## <a name="next-steps"></a>Passaggi successivi
- [Prerequisiti per la registrazione del dispositivo](prerequisites-for-enrollment.md)
- [Gestire i dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md)
- [Dispositivi mobili e computer supportati](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Nov16_HO1-->


