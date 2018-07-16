---
title: Che cos'è la registrazione dei dispositivi di Microsoft Intune
titlesuffix: Microsoft Intune
description: Informazioni sulla registrazione di dispositivi iOS, Android e Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7aabb010baa4a5e53ad5e4264edc43e3ca111c70
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909202"
---
# <a name="what-is-device-enrollment"></a>Che cos'è la registrazione dei dispositivi?
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune consente di gestire i dispositivi e le app del personale, nonché la modalità di accesso ai dati dell'organizzazione da parte del personale stesso. Per usare la gestione dei dispositivi mobili (MDM, Mobile Device Management), i dispositivi devono prima essere registrati nel servizio Intune. Quando un dispositivo viene registrato, viene rilasciato un certificato MDM, che viene usato per la comunicazione con il servizio Intune.

Come si può vedere nelle tabelle seguenti, sono disponibili diversi metodi per registrare i dispositivi del personale. La scelta del metodo dipende dalla proprietà del dispositivo (personale o aziendale), dal tipo di dispositivo (iOS, Windows, Android) e dai requisiti di gestione (reimpostazioni, affinità, blocco).

Per impostazione predefinita, i dispositivi di tutte le piattaforme sono autorizzati alla registrazione in Intune. Tuttavia, è possibile [limitare i dispositivi in base alla piattaforma](enrollment-restrictions-set.md#set-device-type-restrictions).

## <a name="ios-enrollment-methods"></a>Metodi di registrazione per iOS

| **Metodo** |  **Ripristino necessario** |    [**Affinità utente**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) |   **Bloccato** | **Informazioni dettagliate** |
|:---:|:---:|:---:|:---:|:---:|
| | Viene eseguito il ripristino delle impostazioni predefinite dei dispositivi durante la registrazione. |  Associa ogni dispositivo a un utente.| Gli utenti non possono annullare la registrazione di dispositivi.  | |
|**[BYOD](#bring-your-own-device)** | No|   Sì |   No | [Altre informazioni](./apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No  | [Altre informazioni](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**|   Sì |   Facoltativo |  Facoltativo|[Altre informazioni](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Sì |   Facoltativo |  No| [Altre informazioni](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[Altre informazioni](./apple-configurator-direct-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>Metodi di registrazione di macOS

| **Metodo** |  **Ripristino necessario** |  **Affinità utente** | **Bloccato** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | No| Sì | No | [Altre informazioni](./macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No  | [Altre informazioni](./device-enrollment-manager-enroll.md)|


## <a name="windows-enrollment-methods"></a>Metodi di registrazione per Windows

| **Metodo** |  **Ripristino necessario** |    **Affinità utente**   |   **Bloccato** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | No |  Sì |   No | [Altre informazioni](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No  |[Altre informazioni](device-enrollment-manager-enroll.md)|
|**Registrazione automatica** | No |Sì |No | [Altre informazioni](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Registrazione in blocco** |No |No |No | [Altre informazioni](./windows-bulk-enroll.md) |

## <a name="android-enrollment-methods"></a>Metodi di registrazione per Android

| **Metodo** |  **Ripristino necessario** |    **Affinità utente**   |   **Bloccato** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | No|   Sì |   No | [Altre informazioni](./android-enroll.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No  |[Altre informazioni](./device-enrollment-manager-enroll.md)|
|**Profili di lavoro Android**| No | Sì | No| [Altre informazioni](./android-work-profile-enroll.md) |


## <a name="bring-your-own-device"></a>Bring Your Own Device (BYOD)
Il metodo Bring Your Own Device (BYOD) è applicabile a telefoni, tablet e PC personali. Per registrare i dispositivi BYOD, gli utenti installano ed eseguono l'app Portale aziendale. Questo programma consente agli utenti di accedere a risorse aziendali come la posta elettronica.

## <a name="corporate-owned-device"></a>Dispositivo di proprietà dell'azienda
I [dispositivi di proprietà dell'azienda](corporate-identifiers-add.md) includono telefoni, tablet e PC di proprietà dell'organizzazione distribuiti al personale. La registrazione dei dispositivi di proprietà dell'azienda rende possibili scenari di gestione come la registrazione automatica, i dispositivi condivisi o i requisiti di registrazione pre-autorizzati. Un metodo comunemente usato dagli amministratori o dai manager per la registrazione dei dispositivi di proprietà dell'azienda è l'uso del manager di registrazione dispositivi. I dispositivi iOS possono essere registrati direttamente tramite gli strumenti DEP (Device Enrollment Program) offerti da Apple. È possibile identificare e contrassegnare come dispositivi di proprietà dell'azienda anche i dispositivi con numero IMEI.

### <a name="device-enrollment-manager"></a>Manager di registrazione dispositivi
Il manager di registrazione dispositivi (DEM, Device Enrollment Manager) è un account utente speciale usato per registrare e gestire più dispositivi di proprietà dell'azienda. I responsabili possono installare il portale aziendale e registrare molti dispositivi senza utente associato. Questi tipi di dispositivi sono ideali per app POS o di utilità, ad esempio, ma non sono adatti per gli utenti che devono accedere alla posta elettronica o alle risorse aziendali. Altre informazioni su [DEM](./device-enrollment-manager-enroll.md). 

### <a name="apple-device-enrollment-program"></a>Programma di registrazione del dispositivo mobile di Apple:
La gestione del programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple consente di creare e distribuire i criteri in modalità wireless ai dispositivi acquistati e gestiti tramite DEP. Il dispositivo viene registrato quando l'utente accende il dispositivo per la prima volta ed esegue l'Assistente configurazione di iOS. Questo metodo supporta la modalità con supervisione iOS, che abilita la configurazione del dispositivo con funzionalità specifiche.

Per altre informazioni sulla registrazione DEP iOS, vedere:

- [Scegliere come registrare i dispositivi iOS](ios-enroll.md)
- [Registrare dispositivi iOS con Device Enrollment Program](https://docs.microsoft.com/intune/device-restrictions-ios#device-enrollment-program)

### <a name="usb-sa"></a>USB-SA
Gli amministratori IT usano Apple Configurator, tramite USB, per preparare manualmente ogni dispositivo di proprietà dell'azienda per la registrazione con Assistente configurazione. L'amministratore IT crea un profilo di registrazione e lo esporta in Apple Configurator. Quando gli utenti ricevono i dispositivi, devono eseguire Assistente configurazione per registrarli. Questo metodo supporta la modalità **con supervisione iOS**, che a sua volta abilita le funzionalità seguenti:
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

Il certificato MDM viene rinnovato automaticamente quando i dispositivi mobili comunicano con il servizio Intune. In caso di cancellazione dei dispositivi mobili o se questi non riescono a comunicare con il servizio Intune per un determinato periodo di tempo, il certificato MDM non viene rinnovato. Il dispositivo viene rimosso dal portale di Azure 180 giorni dopo la scadenza del certificato MDM.
