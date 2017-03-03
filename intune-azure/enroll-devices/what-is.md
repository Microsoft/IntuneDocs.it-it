---
title: Informazioni sulla registrazione dei dispositivi in Microsoft Intune | Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: informazioni sulla registrazione di dispositivi iOS, Android e Windows.'
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: a92daf02c6fb2405c1255ff4ff8988f669dd76ce
ms.lasthandoff: 02/15/2017


---

# <a name="what-is-device-enrollment"></a>Che cos'è la registrazione dei dispositivi?
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Questo argomento descrive la registrazione e illustra i diversi modi per registrare i dispositivi mobili per la gestione con Intune.

Registrare i dispositivi, inclusi i PC Windows, in Intune in modo da poterli gestire. Nella documentazione di Intune questa funzionalità viene definita Gestione di dispositivi mobili (MDM). Quando i dispositivi vengono registrati come dispositivi mobili (non come PC), viene emesso un certificato MDM che attesta che da quel momento il dispositivo comunica con il servizio Intune. 

Il modo di registrazione dei dispositivi varia a seconda del tipo di dispositivo in uso, della proprietà e del livello di gestione necessario. La registrazione BYOD (Bring Your Own Device) consente agli utenti di registrare i propri telefoni, tablet o PC personali. La registrazione dei dispositivi di proprietà dell'azienda rende possibili scenari di gestione come la registrazione automatica, i dispositivi condivisi o i requisiti di registrazione pre-autorizzati.

Se si usa Exchange ActiveSync, sia in locale che ospitato nel cloud, è possibile abilitare la gestione semplice con Intune, senza registrazione (maggiori informazioni saranno disponibili a breve). È possibile gestire i PC Windows come dispositivi mobili, tramite il metodo consigliato descritto di seguito. È anche possibile gestirli come PC usando il [software client di Intune](https://docs.microsoft.com/intune/deploy-use/manage-windows-pcs-with-microsoft-intune).


## <a name="overview-of-device-enrollment-methods"></a>Panoramica dei metodi di registrazione dei dispositivi

La tabella seguente illustra i metodi di registrazione di Intune con le relative funzionalità supportate e i requisiti di ciascun metodo. Funzionalità e requisiti vengono descritti più avanti in questo articolo. Nella tabella vengono usati i termini seguenti:

- **Cancellazione** - Indica se il dispositivo deve essere cancellato prima che gli utenti possano registrarlo. Il termine "cancellazione" significa il ripristino delle impostazioni predefinite del dispositivo, con la rimozione di tutti i dati. Per altre informazioni, vedere [Use full or selective wipe on devices](/intune-azure/manage-devices/use-full-or-selective-wipe-on-devices-using-microsoft-intune) (Usare la cancellazione completa o selettiva sui dispositivi).
- **Affinità** - Associare i dispositivi agli utenti. Funzionalità richiesta per la gestione di applicazioni per dispositivi mobili (MAM) e l'accesso condizionale ai dati aziendali. Per altre informazioni, vedere [Affinità utente](enroll-ios-devices-using-device-enrollment-program.md).
- **Blocco**: indica se agli utenti non è consentito annullare la registrazione per la gestione dei dispositivi. Gli utenti possono annullare la registrazione dei dispositivi su tutte le piattaforme tramite l'app Portale aziendale. Per annullare la registrazione, non possono usare i menu nativi del sistema operativo.


**Metodi di registrazione per iOS**

| **Metodo** |    **Cancellazione dati richiesta?** |    **Affinità**    |    **Blocco** | **Informazioni dettagliate** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |    No | Maggiori informazioni saranno disponibili a breve|
|**[DEM](#dem)**|    No |No |No    | [Altre informazioni](enroll-ios-devices-using-device-enrollment-program.md)|
|**[DEP](#dep)**|    sì |    Facoltativo |    Facoltativo|[Altre informazioni](enroll-ios-devices-using-device-enrollment-program.md)|
|**[USB-SA](#usb-sa)**|    sì |    Facoltativo |    No| [Altre informazioni](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)|
|**[USB-Direct](#usb-direct)**|    No |    No    | No|[Altre informazioni](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)|



**Metodi di registrazione per Windows**

| **Metodo** |    **Cancellazione dati richiesta?** |    **Affinità**    |    **Blocco** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | sì|    Sì |    No | Maggiori informazioni saranno disponibili a breve|
|**[DEM](#dem)**|    No |No |No    |[Altre informazioni](enroll-devices-using-device-enrollment-manager.md)|

**Metodi di registrazione per Android**

| **Metodo** |    **Cancellazione dati richiesta?** |    **Affinità**    |    **Blocco** | **Informazioni dettagliate**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sì |    No | Maggiori informazioni saranno disponibili a breve|
|**[DEM](#dem)**|    No |No |No    |[Altre informazioni](enroll-ios-devices-using-device-enrollment-program.md)|


## <a name="byod"></a>BYOD
Gli utenti BYOD (Bring Your Own Device) installano l'app Portale aziendale e registrano il dispositivo di loro proprietà. Ciò consente agli utenti di connettersi alla rete aziendale e creare un join al domino o a Azure Active Directory. Per la maggior parte delle piattaforme, è necessario abilitare la registrazione di BYOD per molti scenari di COD (Corporate-Owned Devices, Dispositivi di proprietà dell'azienda). È possibile bloccare la registrazione di dispositivi iOS e Android di proprietà personale. Per istruzioni, vedere [Impostare le restrizioni sul tipo di dispositivi](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions).

## <a name="corporate-owned-devices"></a>Dispositivi di proprietà dell'azienda
È possibile gestire i dispositivi di proprietà dell'azienda (COD) tramite il portale di Azure. I dispositivi iOS possono essere registrati direttamente tramite gli strumenti offerti da Apple. Tutti i tipi di dispositivo possono essere registrati da un amministratore o da un responsabile usando il manager di registrazione dispositivi. È anche possibile identificare e contrassegnare come dispositivo di proprietà dell'azienda i dispositivi con numero IMEI e abilitare questo tipo di registrazione.

### <a name="dem"></a>DEM
Il Manager di registrazione dispositivi è un account utente speciale usato per registrare e gestire più dispositivi di proprietà dell'azienda. I manager possono installare il Portale aziendale e registrare molti dispositivi senza utente associato. Altre informazioni su [DEM](enroll-devices-using-device-enrollment-manager.md). ([Tornare alla tabella](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
La gestione del programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple consente di creare e distribuire i criteri in modalità wireless ai dispositivi acquistati e gestiti tramite DEP. Il dispositivo viene registrato quando l'utente accende il dispositivo per la prima volta ed esegue l'Assistente configurazione di iOS. Questo metodo supporta la modalità **supervisione iOS**, che a sua volta abilita:

  -    Registrazione bloccata
  -    Modalità tutto schermo e altre configurazioni avanzate e limitazioni

Per altre informazioni sulla registrazione di iOS, vedere:

- [Scegliere come registrare i dispositivi iOS](choose-ios-enrollment-method.md)
- [Registrare dispositivi iOS con Device Enrollment Program](enroll-ios-devices-using-device-enrollment-program.md). 
- [Tornare alla tabella in alto](#overview-of-device-enrollment-methods)

### <a name="usb-sa"></a>USB-SA
Gli amministratori IT usano Apple Configurator, via USB, per preparare manualmente ogni dispositivo di proprietà dell'azienda per la registrazione con Assistente configurazione. L'amministratore IT crea un profilo di registrazione e lo esporta in Apple Configurator. Quando gli utenti ricevono i dispositivi, devono eseguire Assistente configurazione per registrarli. Questo metodo supporta la modalità **supervisione iOS**, che a sua volta abilita:
  -    Registrazione bloccata
  -    Modalità tutto schermo e altre configurazioni avanzate e limitazioni

Per altre informazioni sulla registrazione di iOS, vedere:

- [Stabilire come registrare i dispositivi iOS](choose-ios-enrollment-method.md)
- [Registrare dispositivi iOS con Configurator e Assistente configurazione](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md). 

### <a name="usb-direct"></a>USB-Direct
Per la registrazione diretta, l'amministratore deve registrare manualmente ogni dispositivo creando criteri di registrazione ed esportandoli in Apple Configurator. I dispositivi di proprietà dell'azienda connessi tramite USB vengono registrati direttamente e non richiedono il ripristino delle impostazioni predefinite. I dispositivi vengono gestiti come dispositivi senza utente associato. Non vengono bloccati né supervisionati e non possono supportare l'accesso condizionale, il rilevamento jailbreak o la gestione di applicazioni mobili. 

Per altre informazioni sulla registrazione di iOS, vedere:

- [Stabilire come registrare i dispositivi iOS](choose-ios-enrollment-method.md)
- [Enroll iOS devices with Configurator and direct enrollment](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md) (Registrare dispositivi iOS con Configurator e registrazione diretta)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Gestione dei dispositivi mobili con Exchange ActiveSync e Intune
I dispositivi mobili che non sono registrati, ma che sono connessi a Exchange ActiveSync, possono essere gestiti da Intune mediante i criteri MDM di EAS. Intune usa Exchange Connector per comunicare con EAS (Exchange Active Sync), in locale oppure ospitato nel cloud. Maggiori informazioni saranno disponibili a breve.


## <a name="windows-pc-management-with-intune"></a>Gestione di PC Windows con Intune  
È anche possibile usare Microsoft Intune per gestire i PC Windows con il software del client di Intune. I PC gestiti con il client di Intune possono:

 - Compilare relazioni su inventari software e hardware
 - Installare applicazioni desktop, ad esempio file con estensione msi ed exe
 - Gestire le impostazioni del firewall

I PC gestiti con il software del client di Intune non possono essere completamente cancellati, anche se è disponibile la cancellazione selettiva. I PC gestiti con il software del client di Intune non possono sfruttare le numerose funzionalità di gestione di Intune, ad esempio l'accesso condizionale, le impostazioni VPN e Wi-Fi o la distribuzione di certificati e le configurazioni di posta elettronica. Maggiori informazioni saranno disponibili a breve.

## <a name="supported-device-platforms-and-browsers"></a>Piattaforme e browser per dispositivi supportati

Vedere [Dispositivi e browser supportati per Intune](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Pulizia dei dispositivi mobili dopo la scadenza del certificato MDM

Il certificato MDM viene rinnovato automaticamente quando i dispositivi mobili comunicano con il servizio Intune. Se si verifica la cancellazione dei dispositivi mobili (non PC) o se questi non riescono a comunicare con il servizio di Intune per un determinato periodo di tempo, il certificato MDM non viene rinnovato. Il dispositivo viene rimosso dal portale di Azure 180 giorni dopo la scadenza del certificato MDM.

