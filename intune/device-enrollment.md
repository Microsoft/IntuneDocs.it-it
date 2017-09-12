---
title: "Che cos'è la registrazione dei dispositivi di Microsoft Intune"
titlesuffix: Azure portal
description: Informazioni sulla registrazione di dispositivi iOS, Android e Windows."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dda7108aedcc4d3878fe3743ee0b88b26fabbe6f
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="what-is-device-enrollment"></a>Che cos'è la registrazione dei dispositivi?
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo argomento descrive la registrazione e illustra i diversi modi per registrare i dispositivi mobili per la gestione con Intune.

La registrazione dei dispositivi in Intune consente di gestirli. Nella documentazione di Intune questa funzionalità viene definita Gestione di dispositivi mobili (MDM). Quando i dispositivi vengono registrati in Intune, viene emesso un certificato MDM che attesta che da quel momento il dispositivo comunica con il servizio Intune.

Il modo di registrazione dei dispositivi varia a seconda del tipo di dispositivo in uso, della proprietà e del livello di gestione necessario. La registrazione BYOD (Bring Your Own Device) consente agli utenti di registrare i propri telefoni, tablet o PC personali. La registrazione dei dispositivi di proprietà dell'azienda rende possibili scenari di gestione come la registrazione automatica, i dispositivi condivisi o i requisiti di registrazione pre-autorizzati.

Se si usa Exchange ActiveSync, sia in locale che ospitato nel cloud, è possibile abilitare la gestione semplice con Intune, senza registrazione (maggiori informazioni saranno disponibili a breve). È possibile gestire i PC Windows come dispositivi mobili, tramite il metodo consigliato descritto di seguito.


## <a name="overview-of-device-enrollment-methods"></a>Panoramica dei metodi di registrazione dei dispositivi

La tabella seguente offre una panoramica dei metodi di registrazione di Intune, con una descrizione delle relative funzionalità e dei requisiti.
**Legenda**

- **Ripristino necessario** - Viene eseguito il ripristino delle impostazioni predefinite del dispositivo durante la registrazione.
- **Affinità utente** - Associa i dispositivi agli utenti. Per altre informazioni, vedere [Affinità utente](device-enrollment-program-enroll-ios.md).
- **Bloccato** - Impedisce agli utenti di annullare la registrazione dei dispositivi.

**Metodi di registrazione per iOS**

| **Metodo** |  **Ripristino necessario** |    **Affinità utente**   |   **Bloccato** | **Informazioni dettagliate** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](./apple-mdm-push-certificate-get.md)|
|**[DEM](#dem)**|   No |No |No  | [Altre informazioni](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#dep)**|   sì |   Facoltativo |  Facoltativo|[Altre informazioni](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| sì |   Facoltativo |  No| [Altre informazioni](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[Altre informazioni](./apple-configurator-direct-enroll-ios.md)|

**Metodi di registrazione per Windows**

| **Metodo** |  **Ripristino necessario** |    **Affinità utente**   |   **Bloccato** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No |   Sì |   No | [Altre informazioni](windows-enroll.md)|
|**[DEM](#dem)**|   No |No |No  |[Altre informazioni](device-enrollment-manager-enroll.md)|
|**Registrazione automatica** | No |Sì |No | [Altre informazioni](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Registrazione in blocco** |No |No |No | [Altre informazioni](./windows-bulk-enroll.md) |

**Metodi di registrazione per Android**

| **Metodo** |  **Ripristino necessario** |    **Affinità utente**   |   **Bloccato** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |   No | [Altre informazioni](./android-enroll.md)|
|**[DEM](#dem)**|   No |No |No  |[Altre informazioni](./device-enrollment-program-enroll-ios.md)|
|**Android for Work**| No | Sì | No| [Altre informazioni](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="byod"></a>BYOD
Gli utenti BYOD (Bring Your Own Device) installano ed eseguono l'app Portale aziendale per registrare i dispositivi di loro proprietà. Questo programma consente agli utenti di accedere a risorse aziendali come la posta elettronica.

## <a name="corporate-owned-devices"></a>Dispositivi di proprietà dell'azienda
Di seguito sono indicati gli scenari di registrazione per i dispositivi di proprietà dell'azienda. I dispositivi iOS possono essere registrati direttamente tramite gli strumenti offerti da Apple. Tutti i tipi di dispositivo possono essere registrati da un amministratore o da un responsabile usando il manager di registrazione dispositivi. È anche possibile identificare e contrassegnare come dispositivo di proprietà dell'azienda i dispositivi con numero IMEI e abilitare questo tipo di registrazione.

### <a name="dem"></a>DEM
Il manager di registrazione dispositivi (DEM, Device Enrollment Manager) è un account utente speciale usato per registrare e gestire più dispositivi di proprietà dell'azienda. I manager possono installare il Portale aziendale e registrare molti dispositivi senza utente associato. Altre informazioni su [DEM](./device-enrollment-manager-enroll.md).

### <a name="dep"></a>DEP
La gestione del programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple consente di creare e distribuire i criteri in modalità wireless ai dispositivi acquistati e gestiti tramite DEP. Il dispositivo viene registrato quando l'utente accende il dispositivo per la prima volta ed esegue l'Assistente configurazione di iOS. Questo metodo supporta la modalità **supervisione iOS**, che a sua volta abilita le funzionalità seguenti:

  - Registrazione bloccata
  - Modalità tutto schermo e altre configurazioni avanzate e limitazioni

Per altre informazioni sulla registrazione DEP iOS, vedere:

- [Scegliere come registrare i dispositivi iOS](enrollment-method-choose-ios.md)
- [Registrare dispositivi iOS con Device Enrollment Program](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
Gli amministratori IT usano Apple Configurator, tramite USB, per preparare manualmente ogni dispositivo di proprietà dell'azienda per la registrazione con Assistente configurazione. L'amministratore IT crea un profilo di registrazione e lo esporta in Apple Configurator. Quando gli utenti ricevono i dispositivi, devono eseguire Assistente configurazione per registrarli. Questo metodo supporta la modalità **supervisione iOS**, che a sua volta abilita le funzionalità seguenti:
  - Registrazione bloccata
  - Modalità tutto schermo e altre configurazioni avanzate e limitazioni

Per altre informazioni sulla registrazione di iOS Apple Configurator con Assistente configurazione, vedere:

- [Stabilire come registrare i dispositivi iOS](enrollment-method-choose-ios.md)
- [Registrare dispositivi iOS con Configurator e Assistente configurazione](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
Per la registrazione diretta, l'amministratore deve registrare manualmente ogni dispositivo creando criteri di registrazione ed esportandoli in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono registrati direttamente e non richiedono il ripristino delle impostazioni predefinite. I dispositivi vengono gestiti come dispositivi senza utente associato. Non vengono bloccati né supervisionati e non possono supportare l'accesso condizionale, il rilevamento jailbreak o la gestione di applicazioni mobili.

Per altre informazioni sulla registrazione di iOS, vedere:

- [Stabilire come registrare i dispositivi iOS](enrollment-method-choose-ios.md)
- [Enroll iOS devices with Configurator and direct enrollment](apple-configurator-direct-enroll-ios.md) (Registrare dispositivi iOS con Configurator e registrazione diretta)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Gestione dei dispositivi mobili con Exchange ActiveSync e Intune
I dispositivi mobili che non sono registrati, ma che sono connessi a Exchange ActiveSync, possono essere gestiti da Intune mediante i criteri MDM di EAS. Intune usa Exchange Connector per comunicare con EAS (Exchange Active Sync), in locale oppure ospitato nel cloud. Maggiori informazioni saranno disponibili a breve.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Pulizia dei dispositivi mobili dopo la scadenza del certificato MDM

Il certificato MDM viene rinnovato automaticamente quando i dispositivi mobili comunicano con il servizio Intune. In caso di cancellazione dei dispositivi mobili o se questi non riescono a comunicare con il servizio Intune per un determinato periodo di tempo, il certificato MDM non verrà rinnovato. Il dispositivo viene rimosso dal portale di Azure 180 giorni dopo la scadenza del certificato MDM.
