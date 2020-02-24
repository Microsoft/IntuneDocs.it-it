---
title: Che cos'è la registrazione dei dispositivi di Microsoft Intune
titleSuffix: Microsoft Intune
description: Informazioni sulla registrazione di dispositivi iOS/iPadOS, Android e Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7955c91a33edef37b86f5bd8f29dfb681d28030e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415339"
---
# <a name="what-is-device-enrollment"></a>Che cos'è la registrazione dei dispositivi?
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune consente di gestire i dispositivi e le app del personale, nonché la modalità di accesso ai dati dell'organizzazione da parte del personale stesso. Per usare la gestione dei dispositivi mobili (MDM, Mobile Device Management), i dispositivi devono prima essere registrati nel servizio Intune. Quando un dispositivo viene registrato, viene rilasciato un certificato MDM, che viene usato per la comunicazione con il servizio Intune.

Come si può vedere nelle tabelle seguenti, sono disponibili diversi metodi per registrare i dispositivi del personale. La scelta del metodo dipende dalla proprietà del dispositivo (personale o aziendale), dal tipo di dispositivo (iOS, Windows, Android) e dai requisiti di gestione (reimpostazioni, affinità, blocco).

Per impostazione predefinita, i dispositivi di tutte le piattaforme sono autorizzati alla registrazione in Intune. Tuttavia, è possibile [limitare i dispositivi in base alla piattaforma](enrollment-restrictions-set.md#create-a-device-type-restriction).

## <a name="iosipados-enrollment-methods"></a>Metodi di registrazione iOS/iPadOS

| **Metodo** | **Ripristino necessario** | [**Affinità utente**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) | **Bloccato** | **Informazioni dettagliate** |
|:---:|:---:|:---:|:---:|:---:|
| | I dispositivi vengono cancellati durante la registrazione. | Associa ogni dispositivo a un utente.| In caso affermativo, gli utenti non possono annullare la registrazione di dispositivi. | |
|**[BYOD](#bring-your-own-device)** | No| Sì | No | [Altre informazioni](apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No | [Altre informazioni](device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**| Sì | Facoltativo | Facoltativo|[Altre informazioni](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Sì | Facoltativo | No| [Altre informazioni](apple-configurator-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| No | No | No|[Altre informazioni](apple-configurator-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>Metodi di registrazione di macOS
| **Metodo** |  **Ripristino necessario** |  **Affinità utente** | **Locked** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | No| Sì | No | [Altre informazioni](macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No  | [Altre informazioni](device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**| Sì | Facoltativo | Facoltativo|[Altre informazioni](device-enrollment-program-enroll-macos.md)|

## <a name="windows-enrollment-methods"></a>Metodi di registrazione per Windows

| **Metodo** | **Ripristino necessario** | **Affinità utente** | **Locked** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | No | Sì | No | [Altre informazioni](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No |[Altre informazioni](device-enrollment-manager-enroll.md)|
|**Registrazione automatica** | No |Sì |No | [Altre informazioni](windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |Sì |Sì |No | [Altre informazioni](enrollment-autopilot.md)
|**Registrazione in blocco** |No |No |No | [Altre informazioni](windows-bulk-enroll.md) |
|**Co-gestione** |No |Sì |No | [Altre informazioni](https://docs.microsoft.com/configmgr/core/clients/manage/co-management-overview)
|**Oggetto Criteri di gruppo** |No |Sì |No | [Altre informazioni](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)

## <a name="android-enrollment-methods"></a>Metodi di registrazione per Android

| **Personale** | **Metodi di registrazione** | **Ripristino necessario** | **Affinità utente** | **Locked** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android Device Admin**|**Avviato dall'utente tramite portale aziendale** | No | Sì | No | [Altre informazioni](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Profilo aziendale di Android Enterprise**|**Avviato dall'utente tramite portale aziendale**| No | Sì | No | [Altre informazioni](android-work-profile-enroll.md)|


| **Aziendale** | **Metodi di registrazione** | **Ripristino necessario** | **Affinità utente** | **Locked** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android Device Admin**|**[DEM](#device-enrollment-manager) avviato tramite portale aziendale**| No | No | No |[Altre informazioni](device-enrollment-manager-enroll.md)|
|**Android Device Admin**|**(IMEI o SN predichiarato) Avviato dall'utente tramite portale aziendale**| No | Sì | No | [Altre informazioni](./../corporate-identifiers-add.md)|
|**Android Device Admin con Zebra Mobility Extensions**|**Avviato dall'utente o da [DEM](#device-enrollment-manager) tramite portale aziendale**| No | Sì, se avviato dall'utente, No se avviato da [DEM](#device-enrollment-manager) | No | [Altre informazioni](../configuration/android-zebra-mx-overview.md)|
|**Android Enterprise dedicato**|**NFC, token, codice a matrice, Zero Touch**| Sì | No | Configurabile tramite criteri | [Altre informazioni](android-kiosk-enroll.md)|
|**Android Enterprise completamente gestito**|**NFC, token, codice a matrice, Zero Touch**| Sì | Sì | Configurabile tramite criteri | [Altre informazioni](android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>Bring Your Own Device (BYOD)
Il metodo Bring Your Own Device (BYOD) è applicabile a telefoni, tablet e PC di proprietà personale. Per registrare i dispositivi BYOD, gli utenti installano ed eseguono l'app Portale aziendale. Questo programma consente agli utenti di accedere a risorse aziendali come la posta elettronica.

## <a name="corporate-owned-device"></a>Dispositivo di proprietà dell'azienda
I [dispositivi di proprietà dell'azienda](corporate-identifiers-add.md) includono telefoni, tablet e PC di proprietà dell'organizzazione distribuiti al personale. La registrazione dei dispositivi di proprietà dell'azienda rende possibili scenari di gestione come la registrazione automatica, i dispositivi condivisi o i requisiti di registrazione pre-autorizzati. Un metodo comunemente usato dagli amministratori o dai manager per la registrazione dei dispositivi di proprietà dell'azienda è l'uso del manager di registrazione dispositivi. I dispositivi iOS/iPadOS possono essere registrati direttamente tramite gli strumenti DEP (Device Enrollment Program) offerti da Apple. È possibile identificare e contrassegnare come dispositivi di proprietà dell'azienda anche i dispositivi con numero IMEI.

### <a name="device-enrollment-manager"></a>Manager di registrazione dispositivi
Il manager di registrazione dispositivi (DEM, Device Enrollment Manager) è un account utente speciale usato per registrare e gestire più dispositivi di proprietà dell'azienda. I manager possono installare il Portale aziendale e registrare molti dispositivi senza utente associato. Questi tipi di dispositivi sono ideali per app POS o di utilità, ad esempio, ma non sono adatti per gli utenti che devono accedere alla posta elettronica o alle risorse aziendali. Altre informazioni su [DEM](device-enrollment-manager-enroll.md).

### <a name="apple-device-enrollment-program"></a>Programma di registrazione del dispositivo mobile di Apple
La gestione DEP di Apple (Device Enrollment Program) consente di creare e distribuire i criteri in modalità wireless ai dispositivi iOS/iPadOS e macOS acquistati e gestiti tramite DEP. Il dispositivo viene registrato quando l'utente accende il dispositivo per la prima volta ed esegue l'Assistente configurazione. Questo metodo supporta la modalità con supervisione iOS/iPadOS, che abilita la configurazione del dispositivo con funzionalità specifiche.

Altre informazioni sulla registrazione DEP iOS/iPadOS:

- [Scegliere come registrare i dispositivi iOS/iPadOS](ios-enroll.md)
- [Registrare i dispositivi iOS con Device Enrollment Program](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
Gli amministratori IT usano Apple Configurator, tramite USB, per preparare manualmente ogni dispositivo di proprietà dell'azienda per la registrazione con Assistente configurazione. L'amministratore IT crea un profilo di registrazione e lo esporta in Apple Configurator. Quando gli utenti ricevono i dispositivi, devono eseguire Assistente configurazione per registrarli. Questo metodo supporta la modalità **con supervisione iOS**, che a sua volta abilita le funzionalità seguenti:
- Registrazione bloccata
- Modalità tutto schermo e altre configurazioni avanzate e limitazioni

Altre informazioni sulla registrazione di iOS/iPadOS Apple Configurator con Assistente configurazione:

- [Decidere come registrare i dispositivi iOS/iPadOS](ios-enroll.md)
- [Registrare i dispositivi iOS/iPadOS con Configurator e Assistente configurazione](apple-configurator-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
Per la registrazione diretta, l'amministratore deve registrare manualmente ogni dispositivo creando criteri di registrazione ed esportandoli in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono registrati direttamente e non richiedono la cancellazione. I dispositivi vengono gestiti come dispositivi senza utente associato. Non vengono bloccati né supervisionati e non possono supportare l'accesso condizionale, il rilevamento jailbreak o la gestione di applicazioni mobili.

Per altre informazioni sulla registrazione iOS/iPadOS, vedere:

- [Decidere come registrare i dispositivi iOS/iPadOS](ios-enroll.md)
- [Registrare i dispositivi iOS/iPadOS con Configurator e la registrazione diretta](apple-configurator-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Pulizia dei dispositivi mobili dopo la scadenza del certificato MDM

Il certificato MDM viene rinnovato automaticamente quando i dispositivi mobili comunicano con il servizio Intune. In caso di cancellazione dei dispositivi mobili o se questi non riescono a comunicare con il servizio Intune per un determinato periodo di tempo, il certificato MDM non viene rinnovato. Il dispositivo viene rimosso dal portale di Azure 180 giorni dopo la scadenza del certificato MDM.
