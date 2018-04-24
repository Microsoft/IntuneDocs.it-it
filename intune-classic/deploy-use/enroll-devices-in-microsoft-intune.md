---
title: Registrare i dispositivi
description: Gestione dei dispositivi mobili (MDM) usa la registrazione per gestire i dispositivi e consentire l'accesso alle risorse.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 09/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3cae9bc1b76dba3b896957f60ca08cca53423267
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-devices-for-management-in-intune"></a>Registrare i dispositivi per la gestione in Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

È possibile registrare i dispositivi, inclusi i PC Windows, per abilitare la gestione di dispositivi mobili (MDM, Mobile Device Management) con Microsoft Intune. Questo argomento descrive i diversi modi per registrare i dispositivi mobili per la gestione con Intune. Il modo di registrazione dei dispositivi varia a seconda del tipo di dispositivo in uso, della proprietà e del livello di gestione necessario. La registrazione BYOD (Bring Your Own Device) consente agli utenti di registrare i propri telefoni, tablet o PC personali. La registrazione dei dispositivi di proprietà dell'azienda rende possibili scenari di gestione come la registrazione automatica, i dispositivi condivisi o i requisiti di registrazione pre-autorizzati.

Se si usa [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), sia in locale che ospitato nel cloud, è possibile abilitare la gestione semplice con Intune, senza registrazione. I PC Windows possono essere anche gestiti tramite il [software client di Intune](#windows-pc-management-with-intune).

Per impostazione predefinita, i dispositivi di tutte le piattaforme sono autorizzati alla registrazione in Intune. Per impedire la registrazione dei dispositivi, accedere al [portale di amministrazione di Microsoft Intune](https://manage.microsoft.com) con le credenziali di amministratore. Scegliere **Amministrazione** > **Gestione dei dispositivi mobili** > **Regole di registrazione** e deselezionare le caselle di controllo applicabili per le piattaforme da bloccare.

## <a name="overview-of-device-enrollment-methods"></a>Panoramica dei metodi di registrazione dei dispositivi

La tabella seguente illustra i metodi di registrazione di Intune con le relative funzionalità supportate e i requisiti di ciascun metodo. Funzionalità e requisiti vengono descritti più avanti in questo articolo.

- **Cancellazione** - Indica se il dispositivo deve essere cancellato prima che gli utenti possano registrarlo. Il termine "cancellazione" significa il ripristino delle impostazioni predefinite del dispositivo, con la rimozione di tutti i dati. Per altre informazioni, vedere [Disattivare i dispositivi](retire-devices-from-microsoft-intune-management.md).
- **Affinità** - Associare i dispositivi agli utenti. Funzionalità richiesta per la gestione di applicazioni per dispositivi mobili (MAM) e l'accesso condizionale ai dati aziendali. Per altre informazioni, vedere [Affinità utente](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices).
- **Blocco**: indica se agli utenti non è consentito annullare la registrazione dei dispositivi personali tramite i menu del sistema operativo nativo. Gli utenti possono annullare la registrazione dei dispositivi su tutte le piattaforme tramite l'app Portale aziendale.

**Metodi di registrazione per iOS**

| **Metodo** |  **Cancellazione dati richiesta?** |    **Affinità**    |   **Blocco** | **Informazioni dettagliate** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   No |No |No  | [Altre informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Sì |   Facoltativo |  Facoltativo|[Altre informazioni](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Sì |   Facoltativo |  No| [Altre informazioni](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[Altre informazioni](ios-direct-enrollment-in-microsoft-intune.md)|

**Metodi di registrazione per Windows**

| **Metodo** |  **Cancellazione dati richiesta?** |    **Affinità**    |   **Blocco** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   No |No |No  |[Altre informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Metodi di registrazione per Android**

| **Metodo** |  **Cancellazione dati richiesta?** |    **Affinità**    |   **Blocco** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   No |No |No  |[Altre informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Metodi di registrazione di Android for Work**

| **Metodo** |  **Cancellazione dati richiesta?** |    **Affinità**    |   **Blocco** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   No |No |No  |[Altre informazioni](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Metodi di registrazione di macOS**

| **Metodo** |  **Cancellazione dati richiesta?** |    **Affinità**    |   **Blocco** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](prerequisites-for-enrollment.md)|


Per una serie di domande e risposte utili per individuare il metodo corretto, vedere [Scegliere come registrare i dispositivi mobili](/intune-classic/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
Gli utenti BYOD (Bring Your Own Device) installano l'app Portale aziendale e registrano il dispositivo di loro proprietà. Ciò consente agli utenti di connettersi alla rete aziendale e creare un join al domino o a Azure Active Directory. Per la maggior parte delle piattaforme, è necessario abilitare la registrazione di BYOD per molti scenari di COD (Corporate-Owned Devices, Dispositivi di proprietà dell'azienda). Per altre informazioni, vedere [Prerequisiti per la registrazione del dispositivo](prerequisites-for-enrollment.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Dispositivi di proprietà dell'azienda
È possibile gestire i dispositivi di proprietà dell'azienda (COD) tramite la console di Intune. I dispositivi iOS possono essere registrati direttamente tramite gli strumenti offerti da Apple. Tutti i tipi di dispositivo possono essere registrati da un amministratore o da un responsabile usando il manager di registrazione dispositivi. È anche possibile identificare e contrassegnare come dispositivo di proprietà dell'azienda i dispositivi con numero IMEI e abilitare questo tipo di registrazione.

Per altre informazioni, vedere [Registrare i dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md).

### <a name="dem"></a>DEM
Il Manager di registrazione dispositivi è un account speciale di Intune usato per registrare e gestire più dispositivi di proprietà dell'azienda. I manager possono installare il Portale aziendale e registrare molti dispositivi senza utente associato. Altre informazioni su [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
La gestione del programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple consente di creare e distribuire i criteri in modalità wireless ai dispositivi acquistati e gestiti tramite DEP. Il dispositivo viene registrato quando l'utente accende il dispositivo per la prima volta ed esegue l'Assistente configurazione di iOS. Questo metodo supporta la modalità **supervisione iOS**, che a sua volta abilita:
  - Registrazione bloccata
  - Modalità tutto schermo e altre configurazioni avanzate e limitazioni

Altre informazioni su [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
Gli amministratori IT usano Apple Configurator, via USB, per preparare manualmente ogni dispositivo di proprietà dell'azienda per la registrazione con Assistente configurazione. L'amministratore IT crea un profilo di registrazione e lo esporta in Apple Configurator. Quando gli utenti ricevono i dispositivi, devono eseguire Assistente configurazione per registrarli. Questo metodo supporta la modalità **supervisione iOS**, che a sua volta abilita:
  - Registrazione bloccata
  - Modalità tutto schermo e altre configurazioni avanzate e limitazioni

Altre informazioni sulla [registrazione Assistente configurazione con Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### <a name="usb-direct"></a>USB-Direct
Per la registrazione diretta, l'amministratore deve registrare manualmente ogni dispositivo creando criteri di registrazione ed esportandoli in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono registrati direttamente e non richiedono il ripristino delle impostazioni predefinite. I dispositivi vengono gestiti come dispositivi senza utente associato. Non vengono bloccati né supervisionati e non possono supportare l'accesso condizionale, il rilevamento jailbreak o la gestione di applicazioni mobili.  Altre informazioni sulla [registrazione diretta con Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Gestione dei dispositivi mobili con Exchange ActiveSync e Intune
I dispositivi mobili che non sono registrati, ma che sono connessi a Exchange ActiveSync, possono essere gestiti da Intune mediante i criteri MDM di EAS. Intune usa Exchange Connector per comunicare con EAS (Exchange Active Sync), in locale oppure ospitato nel cloud. Per altre informazioni, vedere [Gestione dei dispositivi mobili con Exchange Active Sync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).


## <a name="windows-pc-management-with-intune"></a>Gestione di PC Windows con Intune  
È anche possibile usare Microsoft Intune per gestire i PC Windows con il software del client di Intune. I PC gestiti con il client di Intune possono:

 - Compilare relazioni su inventari software e hardware
 - Installare applicazioni desktop, ad esempio file con estensione msi ed exe
 - Gestire le impostazioni del firewall

I PC gestiti con il software del client di Intune non possono essere completamente cancellati, anche se è disponibile la cancellazione selettiva. I PC gestiti con il software del client di Intune non possono sfruttare le numerose funzionalità di gestione di Intune, ad esempio l'accesso condizionale, le impostazioni VPN e Wi-Fi o la distribuzione di certificati e le configurazioni di posta elettronica. Per altre informazioni, vedere [Gestire PC Windows con Intune](manage-windows-pcs-with-microsoft-intune.md).

## <a name="supported-device-platforms"></a>Piattaforme per dispositivi supportate

Intune può gestire le piattaforme dei dispositivi seguenti:

[!INCLUDE [mdm-supported-devices](../includes/mdm-supported-devices.md)]

## <a name="next-steps"></a>Passaggi successivi
- [Prerequisiti per la registrazione del dispositivo](prerequisites-for-enrollment.md)
- [Gestire i dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md)
- [Dispositivi mobili e computer supportati](/intune/supported-devices-browsers#intune-supported-devices)
