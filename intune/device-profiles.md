---
title: Funzionalità e impostazioni dei dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Panoramica dei diversi profili di dispositivo di Microsoft Intune, che include funzionalità, restrizioni, posta elettronica, Wi-Fi, VPN, Education, certificati, aggiornamento a Windows 10, BitLocker e Windows Defender, Windows Information Protection, modelli amministrativi e impostazioni di configurazione del dispositivo personalizzate nel portale di Azure. Usare questi profili per proteggere i dati e i dispositivi aziendali.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b9bd8aaca9aaf6e39c7a120518eeca1cef31511
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845092"
---
# <a name="apply-features-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Applicare le impostazioni delle funzionalità nei dispositivi usando i profili dei dispositivi in Microsoft Intune

Microsoft Intune include impostazioni e funzionalità che è possibile abilitare o disabilitare in dispositivi diversi all'interno dell'organizzazione. Queste impostazioni e funzionalità vengono aggiunte ai "profili di configurazione". È possibile creare profili per dispositivi diversi e piattaforme diverse, tra cui iOS, Android e Windows, e quindi usare Intune per applicare il profilo ai dispositivi nell'organizzazione.

Di seguito sono riportati alcuni esempi di profili:

- Nei dispositivi Windows 10 usare un modello di profilo che blocca i controlli ActiveX in Internet Explorer.
- Nei dispositivi iOS e macOS consentire agli utenti di usare stampanti AirPrint nell'organizzazione.
- Consentire o impedire l'accesso al Bluetooth nel dispositivo.
- Creare un profilo Wi-Fi o VPN che consente a dispositivi diversi l'accesso alla rete aziendale.
- Gestire gli aggiornamenti software, incluso quando installarli.
- Eseguire un dispositivo Android come dispositivo in modalità tutto schermo dedicato che può eseguire una o più app.

Questo articolo elenca i passaggi per creare un profilo e offre una panoramica dei diversi tipi di profili che è possibile creare. Usare questi profili per autorizzare o bloccare determinate funzionalità nei dispositivi.

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.

2. Selezionare **Configurazione del dispositivo**. Sono disponibili le seguenti opzioni:

    - **Panoramica**: elenca lo stato dei profili e offre dettagli aggiuntivi sui profili assegnati a utenti e dispositivi.
    - **Gestione**: consente di creare profili di dispositivo, caricare [script di PowerShell](intune-management-extension.md) personalizzati da eseguire all'interno del profilo e di aggiungere piani dati ai dispositivi che usano [eSIM](esim-device-configuration.md).
    - **Monitoraggio**: consente di verificare lo stato di un profilo e le operazioni riuscite e non riuscite, nonché di visualizzare i log per i profili.
    - **Configurazione**: aggiungere un'autorità di certificazione SCEP o PFX o abilitare [Gestione delle spese per telecomunicazioni](telecom-expenses-monitor.md) nel profilo.

3. Selezionare **Profili** > **Crea profilo**. Immettere le proprietà seguenti:

   - **Nome**: immettere un nome descrittivo per il profilo.
   - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
   - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e versioni successive**
       - **Windows 10 e versioni successive**

   - **Tipo di profilo**: selezionare il tipo di impostazioni da creare. L'elenco visualizzato dipende dalla **piattaforma** scelta:

       - [Modelli amministrativi](administrative-templates-windows.md)
       - [Personalizzato](custom-settings-configure.md)
       - [Ottimizzazione recapito](delivery-optimization-windows.md)
       - [Funzionalità dei dispositivi](device-features-configure.md)
       - [Restrizioni dei dispositivi](device-restrictions-configure.md)
       - [Aggiornamento dell'edizione e cambio di modalità](edition-upgrade-configure-windows-10.md)
       - [Istruzione](education-settings-configure.md)
       - [Posta elettronica](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [Protezione dell'identità](identity-protection-configure.md)  
       - [Modalità tutto schermo](kiosk-settings.md)
       - [Certificato PKCS](certficates-pfx-configure.md)
       - [Certificato SCEP](certificates-scep-configure.md)
       - [Certificato attendibile](certificates-configure.md)
       - [Criteri di aggiornamento](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows Information Protection](windows-information-protection-configure.md)

     Se ad esempio si seleziona **iOS** come piattaforma, le opzioni del tipo di profilo sono simili alle seguenti:

     ![Creare un profilo iOS in Intune](./media/create-device-profile.png)

4. Selezionare **Impostazioni**. Le impostazioni sono organizzate per categoria. Selezionare una categoria per visualizzare un elenco di tutte le impostazioni che è possibile configurare.

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Per altre informazioni sui diversi tipi di profilo, vedere le sezioni successive di questo articolo.

## <a name="administrative-templates-preview"></a>Modelli amministrativi (anteprima)

La funzionalità [Modelli amministrativi](administrative-templates-windows.md) include centinaia di impostazioni che è possibile configurare per Internet Explorer, OneDrive, Desktop remoto, Word, Excel e altri programmi Office e molto altro.

Questi modelli offrono agli amministratori una visualizzazione estremamente semplice delle impostazioni simile a quella dei criteri di gruppo, ma basata sul cloud al 100%. 

Questa funzionalità supporta:

- Windows 10 e versioni successive

## <a name="device-features"></a>Funzionalità del dispositivo

[Funzionalità del dispositivo](device-features-configure.md) consente di gestire le funzionalità dei dispositivi iOS e macOS, come AirPrint, le notifiche e i messaggi della schermata di blocco.

Questa funzionalità supporta:

- iOS 
- macOS

## <a name="device-restrictions"></a>Limitazioni del dispositivo

[Limitazioni del dispositivo](device-restrictions-configure.md) consente di gestire la protezione, l'hardware, la condivisione dei dati e altre impostazioni nei dispositivi. Ad esempio è possibile creare un profilo di limitazioni del dispositivo che impedisce agli utenti di dispositivi iOS di usare la fotocamera. 

Questa funzionalità supporta:

- Android
- Android Enterprise
- iOS
- macOS
- Windows 10 e versioni successive
- Windows 10 Team

## <a name="delivery-optimization"></a>Ottimizzazione recapito

[Ottimizzazione recapito](delivery-optimization-windows.md) offre un'esperienza migliore per il recapito degli aggiornamenti software. Queste impostazioni sostituiscono le impostazioni **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10**.

Usare queste impostazioni per controllare la modalità di download degli aggiornamenti software nei dispositivi nell'organizzazione. Ad esempio, è possibile consentire agli utenti di gestire in autonomia gli aggiornamenti oppure di ottenere gli aggiornamenti tramite i servizi cloud di ottimizzazione recapito in un profilo di dispositivo.

Questa funzionalità supporta:

- Windows 10 e versioni successive

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

Il profilo delle [impostazioni della modalità tutto schermo](kiosk-settings.md) consente di configurare un dispositivo per l'esecuzione di una singola app o di molte app. È anche possibile personalizzare altre funzionalità sulla modalità tutto schermo, inclusi un menu di avvio e un Web browser.

Questa funzionalità supporta:

- Windows 10 e versioni successive

Impostazioni per la modalità tutto schermo disponibili anche come restrizioni del dispositivo per [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings), e [iOS](device-restrictions-ios.md#kiosk-supervised-only).

## <a name="email"></a>Posta elettronica

Il profilo [Impostazioni di posta elettronica](email-settings-configure.md) consente di creare, assegnare e gestire le impostazioni di posta elettronica di Exchange ActiveSync nei dispositivi. I profili di posta elettronica garantiscono coerenza e consentono di ridurre le chiamate al supporto. Grazie ad essi gli utenti finali possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione manuale. 

Questa funzionalità supporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10 e versioni successive

## <a name="vpn"></a>Connessione

[Impostazioni VPN](vpn-settings-configure.md) assegna le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete. 

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per avviare una connessione con il server VPN. 

Questa funzionalità supporta: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 e versioni successive

## <a name="wi-fi"></a>Wi-Fi

[Impostazioni Wi-Fi](wi-fi-settings-configure.md) assegna le impostazioni di rete wireless a utenti e dispositivi. Quando si assegna un profilo Wi-Fi, gli utenti dispongono dell'accesso alla rete Wi-Fi aziendale senza doverlo configurare. 

Questa funzionalità supporta: 

- Android
- iOS
- macOS
- Windows 8.1 (solo importazione)
- Windows 10 e versioni successive

## <a name="esim-cellular---public-preview"></a>Cellulare eSIM - Anteprima pubblica

La funzionalità [Profili cellulare eSIM](esim-device-configuration.md) consente agli amministratori di configurare piani di rete dati nei dispositivi gestiti, per l'accesso a Internet e ai dati. Dopo aver ottenuto i codici di attivazione dall'operatore di telefonia mobile, usare Intune per importare questi codici di attivazione e quindi assegnarli ai dispositivi che supportano eSIM.

Questa funzionalità supporta:
- Windows 10 Fall Creators Update e versioni successive

## <a name="education"></a>Istruzione

Le [impostazioni di Education - Windows 10](education-settings-configure.md) consentono di configurare le opzioni per l'[app Test ed esami di Windows](https://education.microsoft.com/gettrained/win10takeatest). Quando si configurano queste opzioni, nessun'altra app può essere eseguita sul dispositivo finché il test non è completato.

Le [impostazioni di Education - iOS](education-settings-configure-ios-shared.md) usano l'app Classroom iOS, progettata per gestire l'insegnamento e controllare i dispositivi degli studenti in aula. È possibile configurare i dispositivi iPad in modo che molti studenti possano condividere un unico dispositivo.

## <a name="edition-upgrade"></a>Aggiornamento dell'edizione

[Aggiornamento edizione di Windows 10](edition-upgrade-configure-windows-10.md) consente di aggiornare automaticamente i dispositivi che eseguono determinate versioni di Windows 10 a un'edizione più recente.

Questa funzionalità supporta: 
- Windows 10 e versioni successive

## <a name="update-policies"></a>Criteri di aggiornamento

I [criteri di aggiornamento di iOS](software-updates-ios.md) spiegano come creare e assegnare i criteri di iOS per installare gli aggiornamenti software nei dispositivi iOS. È anche possibile rivedere lo stato dell'installazione.

Per i criteri di aggiornamento nei dispositivi Windows, vedere [Ottimizzazione recapito](delivery-optimization-windows.md). 

Questa funzionalità supporta:
- iOS

## <a name="certificates"></a>Certificati

Il profilo [Certificati](certificates-configure.md) consente di configurare certificati attendibili, SCEP e PKCS, assegnati ai dispositivi e usati per autenticare i profili Wi-Fi, VPN e di posta elettronica.

Questa funzionalità supporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 e versioni successive

## <a name="windows-information-protection-profile"></a>Profilo Windows Information Protection

[Windows Information Protection](windows-information-protection-configure.md) offre la protezione dalla perdita di dati senza interferire con l'esperienza del dipendente. Consente anche di proteggere le app e i dati aziendali da perdite di dati accidentali su dispositivi di proprietà dell'azienda e dispositivi personali che i dipendenti usano al lavoro. L'uso di Windows Information Protection non richiede modifiche all'ambiente o ad altre app.

Questa funzionalità supporta:

- Windows 10 e versioni successive

## <a name="shared-multi-user-device"></a>Dispositivo multiutente condiviso

[Windows 10](shared-user-device-settings-windows.md) e [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) includono le impostazioni per gestire i dispositivi con più utenti, noti anche come dispositivi condivisi o PC condivisi. Quando un utente accede al dispositivo, si sceglie se l'utente può modificare le opzioni di sospensione o salvare i file nel dispositivo. In un altro esempio è possibile creare un criterio che consente di eliminare le credenziali inattive dai dispositivi Windows HoloLens per risparmiare spazio.

Queste impostazioni del dispositivo multiutente condiviso consentono agli amministratori di controllare alcune delle funzionalità del dispositivo e di gestire questi dispositivi condivisi con Intune.

Questa funzionalità supporta:

- Windows 10 e versioni successive
- Windows Holographic for Business

## <a name="custom-profile"></a>Profilo personalizzato

[Impostazioni personalizzate](custom-settings-configure.md) consente agli amministratori di assegnare impostazioni dei dispositivi non incluse in Intune. Ad esempio, nei dispositivi Android è possibile immettere valori OMA-URI. Per i dispositivi iOS è possibile importare un file di configurazione creato in Apple Configurator. 

Questa funzionalità supporta:

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Monitorare e risolvere problemi

[Gestire i profili](device-profile-monitor.md) per controllare lo stato dei dispositivi e i profili assegnati. Ciò agevola anche la risoluzione dei conflitti grazie alla visualizzazione delle impostazioni che causano conflitto e dei profili che le contengono. La funzionalità relativa a [problemi comuni e soluzioni](device-profile-troubleshoot.md) offre un elenco di domande e risposte per aiutare a usare i profili, tra cui cosa accade quando viene eliminato un profilo, cosa fa sì che vengano inviate notifiche ai dispositivi e altro ancora.

## <a name="next-steps"></a>Passaggi successivi
Scegliere la piattaforma e iniziare a usare:

