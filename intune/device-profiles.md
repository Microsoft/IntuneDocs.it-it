---
title: Profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Panoramica dei diversi profili di dispositivo di Microsoft Intune, che include funzionalità, restrizioni, posta elettronica, Wi-Fi, VPN, Education, certificati, aggiornamento a Windows 10, BitLocker e Windows Defender, Windows Information Protection e impostazioni di configurazione del dispositivo personalizzate nel portale di Azure. Usare questi profili per proteggere i dati e i dispositivi aziendali.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 590ce850b97502b357dec86932e1445718860af2
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253545"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Informazioni sui profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune include impostazioni e funzionalità che è possibile abilitare o disabilitare in dispositivi diversi all'interno dell'organizzazione. Queste impostazioni e funzionalità vengono gestite usando i profili. Di seguito sono riportati alcuni esempi di profili: 

- Un profilo Wi-Fi che consente a dispositivi diversi l'accesso alla rete Wi-Fi aziendale
- Un profilo VPN che consente a dispositivi diversi l'accesso al server VPN nella rete aziendale

In questo articolo viene offerta una panoramica dei diversi profili che è possibile creare per i dispositivi. Usare questi profili per autorizzare o bloccare determinate funzionalità nei dispositivi.

## <a name="before-you-begin"></a>Prima di iniziare
Per visualizzare le funzionalità disponibili, aprire il [portale di Azure](https://portal.azure.com) e quindi aprire la risorsa di Intune. 

**Configurazione del dispositivo** include le opzioni seguenti:

- **Panoramica**: elenca lo stato dei profili e offre dettagli aggiuntivi sui profili assegnati a utenti e dispositivi
- **Gestisci**: consente di creare profili di dispositivo e caricare [script PowerShell](intune-management-extension.md) personalizzati da eseguire all'interno del profilo
- **Monitoraggio**: consente di verificare lo stato di un profilo e le operazioni riuscite e non riuscite, nonché di visualizzare i log per i profili
- **Installazione**: consente di aggiungere un'autorità di certificazione (SCEP o PFX) o di attivare Gestione delle spese per telecomunicazioni per il profilo

## <a name="create-the-profile"></a>Creare il profilo

[Creare un profilo del dispositivo](device-profile-create.md) visualizza istruzioni dettagliate per creare un profilo. 

## <a name="device-features---ios-and-macos"></a>Funzionalità dei dispositivi - iOS e macOS

[Funzionalità del dispositivo](device-features-configure.md) consente di gestire le funzionalità dei dispositivi iOS e macOS, come AirPrint, le notifiche e le configurazioni dei dispositivi condivisi.

Questa funzionalità supporta:
- iOS 
- macOS


## <a name="device-restrictions"></a>Limitazioni del dispositivo
[Limitazioni del dispositivo](device-restrictions-configure.md) consente di gestire la protezione, l'hardware, la condivisione dei dati e altre impostazioni nei dispositivi. Ad esempio è possibile creare un profilo di limitazioni del dispositivo che impedisce agli utenti di dispositivi iOS di usare la fotocamera. 

Questa funzionalità supporta:

- Android
- iOS
- macOS
- Windows 10
- Windows 10 Team

## <a name="endpoint-protection"></a>Endpoint Protection
[Endpoint protection settings for Windows 10](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10) configura le impostazioni di BitLocker e Windows Defender per i dispositivi Windows 10.

Per l'onboarding di Windows Defender Advanced Threat Protection (WDATP) in Microsoft Intune, vedere [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection) (Configurare endpoint con gli strumenti di gestione dei dispositivi mobili).

Questa funzionalità supporta:
- Windows 10 e versioni successive

## <a name="identity-protection"></a>Protezione dell'identità
[La protezione dell'identità](identity-protection-configure.md) controlla l'esperienza Windows Hello for Business nei dispositivi Windows 10 e Windows 10 Mobile. Configurare queste impostazioni per rendere Windows Hello for Business disponibile per gli utenti e i dispositivi e per specificare i requisiti per i pin e i gesti dispositivo.  

Questa funzionalità supporta:  
- Windows 10 e versioni successive
- Windows Holographic for Business  

## <a name="kiosk"></a>Modalità tutto schermo

Il profilo delle [impostazioni della modalità tutto schermo](kiosk-settings.md) consente di configurare un dispositivo per l'esecuzione di una singola app o di più app. È anche possibile personalizzare altre funzionalità sulla modalità tutto schermo, inclusi un menu di avvio e un Web browser.

Questa funzionalità supporta:
- Windows 10 e versioni successive

## <a name="email"></a>Posta elettronica
Il profilo [Impostazioni di posta elettronica](email-settings-configure.md) consente di creare, assegnare e gestire le impostazioni di posta elettronica Exchange ActiveSync nei dispositivi. I profili di posta elettronica garantiscono coerenza e consentono di ridurre le chiamate al supporto. Grazie ad essi gli utenti finali possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione manuale. 

Questa funzionalità supporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="vpn"></a>Connessione
[Impostazioni VPN](vpn-settings-configure.md) assegna le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete. 

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per avviare una connessione con il server VPN. 

Questa funzionalità supporta: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi
[Impostazioni Wi-Fi](wi-fi-settings-configure.md) assegna le impostazioni di rete wireless a utenti e dispositivi. Quando si assegna un profilo Wi-Fi, gli utenti dispongono dell'accesso alla rete Wi-Fi aziendale senza doverlo configurare. 

Questa funzionalità supporta: 

- Android
- iOS
- macOS
- Windows 8.1 (solo importazione)

## <a name="esim-cellular---public-preview"></a>Cellulare eSIM - Anteprima pubblica

La funzionalità [Profili cellulare eSIM](esim-device-configuration.md) consente di configurare piani di rete dati nei dispositivi gestiti, per l'accesso a Internet e ai dati.  Dopo aver ottenuto i codici di attivazione dall'operatore di telefonia mobile, è possibile usare Intune per importare questi codici di attivazione e quindi assegnarli ai dispositivi che supportano eSIM.

Questa funzionalità supporta:
- Windows 10 Fall Creators Update e versioni successive

## <a name="education"></a>Istruzione
Le [impostazioni di Education - Windows 10](education-settings-configure.md) consentono di configurare le opzioni per l'[app Test ed esami di Windows](https://education.microsoft.com/gettrained/win10takeatest). Quando si configurano queste opzioni, nessun'altra app può essere eseguita sul dispositivo finché il test non è completato.

Le [impostazioni di Education - iOS](education-settings-configure-ios-shared.md) usano l'app Classroom iOS, progettata per gestire l'insegnamento e controllare i dispositivi degli studenti in aula. È possibile configurare i dispositivi iPad in modo che più studenti possono condividere un unico dispositivo.

## <a name="edition-upgrade"></a>Aggiornamento dell'edizione
[Aggiornamento edizione di Windows 10](edition-upgrade-configure-windows-10.md) consente di aggiornare automaticamente i dispositivi che eseguono determinate versioni di Windows 10 a un'edizione più recente.

Questa funzionalità supporta: 
- Windows 10 e versioni successive

## <a name="update-policies"></a>Criteri di aggiornamento
I [criteri di aggiornamento di iOS](software-updates-ios.md) spiegano come creare e assegnare i criteri di iOS per installare gli aggiornamenti software nei dispositivi iOS. È anche possibile rivedere lo stato dell'installazione.

Questa funzionalità supporta:
- iOS

## <a name="certificates"></a>Certificati
Il profilo [Certificati](certificates-configure.md) consente di configurare certificati attendibili, SCEP e PKCS, da assegnare ai dispositivi e da usare per autenticare i profili Wi-Fi, VPN e di posta elettronica.

Questa funzionalità supporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>Profilo Windows Information Protection
[Windows Information Protection](windows-information-protection-configure.md) offre la protezione dalla perdita di dati senza interferire con l'esperienza del dipendente. Consente anche di proteggere le app e i dati aziendali da perdite di dati accidentali su dispositivi di proprietà dell'azienda e dispositivi personali che i dipendenti usano al lavoro. Questa funzionalità non richiede modifiche all'ambiente o ad altre app.

Questa funzionalità supporta:
- Windows 10 e versioni successive

## <a name="custom-profile"></a>Profilo personalizzato
Le [impostazioni personalizzate](custom-settings-configure.md) consentono di assegnare ai dispositivi impostazioni non integrate in Intune. Ad esempio, nei dispositivi Android è possibile immettere valori OMA-URI. Per i dispositivi iOS è possibile importare un file di configurazione creato in Apple Configurator. 

Questa funzionalità supporta:

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Monitorare e risolvere problemi

[Gestire i profili](device-profile-monitor.md) per controllare lo stato dei dispositivi e i profili assegnati. Ciò agevola anche la risoluzione dei conflitti grazie alla visualizzazione delle impostazioni che causano conflitto e dei profili che le contengono. La funzionalità relativa a [problemi comuni e soluzioni](device-profile-troubleshoot.md) offre un elenco di domande e risposte per aiutare a usare i profili, tra cui cosa accade quando viene eliminato un profilo, cosa fa sì che vengano inviate notifiche ai dispositivi e altro ancora.