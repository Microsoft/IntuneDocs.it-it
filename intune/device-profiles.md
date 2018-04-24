---
title: Profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Panoramica dei diversi profili di dispositivo di Microsoft Intune, che include funzionalità, restrizioni, posta elettronica, Wi-Fi, VPN, Education, certificati, aggiornamento a Windows 10, BitLocker e Windows Defender, Windows Information Protection e impostazioni di configurazione del dispositivo personalizzate nel portale di Azure. Usare questi profili per proteggere i dati e i dispositivi aziendali.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b942f794136ce1a1d7851b0b04d6df70ea7174c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Informazioni sui profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune include impostazioni e funzionalità che è possibile abilitare o disabilitare in dispositivi diversi all'interno dell'organizzazione. Queste impostazioni e funzionalità vengono gestite usando i profili. Di seguito sono riportati alcuni esempi di profili: 

- Un profilo Wi-Fi che consente a dispositivi diversi l'accesso alla rete Wi-Fi aziendale
- Un profilo VPN che consente a dispositivi diversi l'accesso al server VPN nella rete aziendale

In questo argomento viene offerta una panoramica dei diversi profili che è possibile creare per i dispositivi. Usare questi profili per autorizzare o bloccare determinate funzionalità nei dispositivi.

## <a name="before-you-begin"></a>Prima di iniziare
Per visualizzare le funzionalità disponibili, aprire il [portale di Azure](https://portal.azure.com) e quindi aprire la risorsa di Intune. 

**Configurazione del dispositivo** include le opzioni seguenti:

- **Panoramica**: elenca lo stato dei profili e offre dettagli aggiuntivi sui profili assegnati a utenti e dispositivi
- **Gestisci**: consente di creare profili di dispositivo e caricare [script PowerShell](intune-management-extension.md) personalizzati da eseguire all'interno del profilo
- **Monitoraggio**: consente di verificare lo stato di un profilo e le operazioni riuscite e non riuscite, nonché di visualizzare i log per i profili
- **Installazione**: consente di aggiungere un'autorità di certificazione (SCEP o PFX) o di attivare Gestione delle spese per telecomunicazioni per il profilo

## <a name="create-the-profile"></a>Creare il profilo

[Creare un profilo del dispositivo](device-profile-create.md) visualizza istruzioni dettagliate per creare un profilo. 

## <a name="device-features-profile"></a>Profilo Funzionalità del dispositivo

[Funzionalità del dispositivo](device-features-configure.md) consente di gestire le funzionalità dei dispositivi iOS e macOS, come AirPrint, le notifiche e le configurazioni dei dispositivi condivisi.

Questa funzionalità supporta:  
- iOS 
- macOS

## <a name="device-restrictions-profile"></a>Profilo Limitazioni del dispositivo
[Limitazioni del dispositivo](device-restrictions-configure.md) consente di gestire la protezione, l'hardware, la condivisione dei dati e altre impostazioni nei dispositivi. Ad esempio è possibile creare un profilo di limitazioni del dispositivo che impedisce agli utenti di dispositivi iOS di usare la fotocamera. 

Questa funzionalità supporta: 

- Android
- iOS
- macOS
- Windows 10
- Windows 10 Team

## <a name="email-profile"></a>Profilo di posta elettronica
Il profilo [Impostazioni di posta elettronica](email-settings-configure.md) consente di creare, assegnare e gestire le impostazioni di posta elettronica Exchange ActiveSync nei dispositivi. I profili di posta elettronica garantiscono coerenza e consentono di ridurre le chiamate al supporto. Grazie ad essi gli utenti finali possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione manuale. 

Questa funzionalità supporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="wi-fi-profile"></a>Profilo Wi-Fi
[Impostazioni Wi-Fi](wi-fi-settings-configure.md) assegna le impostazioni di rete wireless a utenti e dispositivi. Quando si assegna un profilo Wi-Fi, gli utenti dispongono dell'accesso alla rete Wi-Fi aziendale senza doverlo configurare. 

Questa funzionalità supporta: 

- Android
- iOS
- macOS
- Windows 8.1 (solo importazione)

## <a name="vpn-profile"></a>Profilo VPN
[Impostazioni VPN](vpn-settings-configure.md) assegna le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete. 

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per stabilire una connessione con il server VPN. 

Questa funzionalità supporta: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="education-profile"></a>Profilo Education
Le [impostazioni Education](education-settings-configure.md) consentono di configurare le opzioni per l'[app Test ed esami di Windows](https://education.microsoft.com/gettrained/win10takeatest). Quando si configurano queste opzioni, nessun'altra app può essere eseguita sul dispositivo finché il test non è completato.

## <a name="certificates-profile"></a>Profilo Certificati
Il profilo [Certificati](certificates-configure.md) consente di configurare certificati attendibili, SCEP e PKCS, da assegnare ai dispositivi e da usare per autenticare i profili Wi-Fi, VPN e di posta elettronica.

Questa funzionalità supporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="edition-upgrade-profile"></a>Profilo Aggiornamento edizione
[Aggiornamento edizione di Windows 10](edition-upgrade-configure-windows-10.md) consente di aggiornare automaticamente i dispositivi che eseguono determinate versioni di Windows 10 a un'edizione più recente.

Questa funzionalità supporta: solo Windows 10

## <a name="endpoint-protection-profile"></a>Profilo Endpoint Protection
[Endpoint protection settings for Windows 10](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10) configura le impostazioni di BitLocker e Windows Defender per i dispositivi Windows 10.

Per l'onboarding di Windows Defender Advanced Threat Protection (WDATP) in Microsoft Intune, vedere [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection) (Configurare endpoint con gli strumenti di gestione dei dispositivi mobili).

Questa funzionalità supporta: solo Windows 10

## <a name="windows-information-protection-profile"></a>Profilo Windows Information Protection
[Windows Information Protection](windows-information-protection-configure.md) offre la protezione dalla perdita di dati senza interferire con l'esperienza del dipendente. Consente anche di proteggere le app e i dati aziendali da perdite di dati accidentali su dispositivi di proprietà dell'azienda e dispositivi personali che i dipendenti usano al lavoro. Questa funzionalità non richiede modifiche all'ambiente o ad altre app.

Questa funzionalità supporta: solo Windows 10

## <a name="custom-profile"></a>Profilo personalizzato
Le [impostazioni personalizzate](custom-settings-configure.md) consentono di assegnare ai dispositivi impostazioni non integrate in Intune. Ad esempio, nei dispositivi Android è possibile immettere valori OMA-URI. Per i dispositivi iOS è possibile importare un file di configurazione creato in Apple Configurator. 

Questa funzionalità supporta:

- Android
- iOS
- macOS
- Windows Phone 8.1