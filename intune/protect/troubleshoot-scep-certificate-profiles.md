---
title: Risolvere i problemi dell'uso di profili certificato SCEP per il provisioning di certificati con Microsoft Intune | Microsoft Docs
description: Risolvere i problemi relativi all'uso di Simple Certificate Enrollment Protocol (SCEP) nei dispositivi per richiedere certificati da usare con Intune, inclusi i problemi di comunicazione dai dispositivi al servizio Registrazione dispositivi di rete (NDES), da NDES alle autorità di certificazione e dal Connettore di certificati di Intune al servizio Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4496a5bbc6d5ee5134dc4e6a795494710ea6865d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515221"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Panoramica della risoluzione dei problemi di distribuzione dei profili certificato SCEP con Microsoft Intune

La risoluzione dei problemi associati all'uso di profili certificato SCEP in Intune può risultare complicata. Questo articolo è una panoramica che può contribuire alla risoluzione dei problemi tramite:

- Spiegazione dell'architettura e del flusso di comunicazione del processo SCEP
- Delimitazione dell'ambito in cui si verifica un problema nel flusso di comunicazione
- Identificazione dei file di log delle chiavi a cui si fa riferimento negli articoli successivi per la risoluzione dei problemi con i profili certificato

Le informazioni contenute in questo articolo e negli articoli sulla risoluzione dei problemi con i certificati SCEP si applicano all'uso di profili certificato SCEP con dispositivi Android, iOS/iPad e Windows. Le informazioni analoghe per macOS non sono disponibili in questo momento.

Per la risoluzione dei problemi del servizio NDES, vedere i seguenti articoli in support.microsoft.com:

- [Verificare la configurazione del servizio Registrazione dispositivi di rete in locale per i certificati SCEP in Intune](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [Risoluzione dei problemi di configurazione del servizio Registrazione dispositivi di rete per l'uso con i profili certificato di Microsoft Intune]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)

Prima di procedere, verificare di aver soddisfatto i [prerequisiti per l'uso dei profili certificato SCEP](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates), inclusa la distribuzione di un certificato radice tramite un profilo certificato attendibile.

## <a name="scep-communication-flow-overview"></a>Panoramica del flusso di comunicazione SCEP

Il grafico seguente illustra una panoramica di base del processo di comunicazione SCEP in Intune.

![Flusso del profilo certificato SCEP](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [Distribuire un profilo certificato SCEP](troubleshoot-scep-certificate-profile-deployment.md). Intune genera una stringa di richiesta di verifica, che richiede un utente, uno scopo del certificato e un tipo di certificato specifici.

2. [Comunicazioni dal dispositivo al server NDES](troubleshoot-scep-certificate-device-to-ndes.md). Il dispositivo usa l'URI del servizio Registrazione dispositivi di rete (NDES) per contattare il server di registrazione dispositivi e presentare una richiesta di verifica.

3. [Comunicazioni da NDES al modulo criteri](troubleshoot-scep-certificate-ndes-policy-module.md). Il servizio Registrazione dispositivi di rete (NDES) trasmette la richiesta di verifica al modulo criteri del Connettore di certificati di Intune sul server, che convalida la richiesta.

4. [Da NDES all'autorità di certificazione](troubleshoot-scep-certificate-ndes-policy-module.md). NDES passa le richieste di emissione certificato valide all'autorità di certificazione (CA).

5. [Consegna del certificato ai dispositivo](troubleshoot-scep-certificate-delivery.md). Il certificato viene consegnato al dispositivo.

6. [Segnalazione della distribuzione a Intune](troubleshoot-scep-certificate-reporting.md). Il Connettore di certificati di Intune segnala l'evento di emissione del certificato a Intune.

## <a name="log-files"></a>File di registro

Per identificare problemi con il flusso di lavoro di comunicazione e provisioning dei certificati, esaminare i file di log dell'infrastruttura server e dei dispositivi. Le sezioni successive per la risoluzione dei problemi con i profili certificato SCEP esaminano i file di log a cui si fa riferimento in questa sezione.

- [Log dell'infrastruttura e del server](#logs-for-on-premises-infrastructure)

I log del dispositivo dipendono dalla piattaforma del dispositivo:  

- [iOS e iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>Log per l'infrastruttura locale
  
L'infrastruttura locale che supporta l’uso dei profili certificato SCEP per le distribuzioni di certificati include il Connettore di certificati di Microsoft Intune, il servizio Registrazione dispositivi di rete eseguito in un server Windows e l'autorità di certificazione.

I file di log per questi ruoli includono il Visualizzatore eventi di Windows, le console di certificazione e vari file di log specifici per il Connettore di certificati di Intune, il servizio Registrazione dispositivi di rete o altri ruoli e operazioni che fanno parte dell'infrastruttura locale.

L'elenco seguente include i log o le console a cui si fa riferimento nei successivi articoli sulla risoluzione dei problemi di SCEP. 

- **NDESConnector_date_time.svclog**:

  questo log visualizza le comunicazioni dal Connettore di certificati di Microsoft Intune al servizio cloud di Intune. Per visualizzare questo log è possibile usare lo strumento [Visualizzatore di tracce dei servizi](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe).

  Chiave del Registro di sistema associata: *HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  Percorso: Nel server che ospita il servizio Registrazione dispositivi di rete: *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **CertificateRegistrationPoint_date_time.svclog**:

  Questo log visualizza il modulo criteri del servizio Registrazione dispositivi di rete che riceve e verifica le richieste di certificati. Per visualizzare questo log è possibile usare lo strumento [Visualizzatore di tracce dei servizi](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe).

  Percorso: Nel server che ospita il servizio Registrazione dispositivi di rete: *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **NDESPlugin.log**:

  Questo log visualizza il passaggio delle richieste di certificati al punto di registrazione certificati e la verifica di tali richieste.

  Percorso: Nel server che ospita il servizio Registrazione dispositivi di rete: *%program_files%\Microsoft Intune\NDESPolicyModule\logs*

- **Log di IIS**:

  I log di IIS visualizzano le richieste di certificati dei dispositivi mobili che accedono al servizio Registrazione dispositivi di rete.

  Percorso: Nel server che ospita il servizio Registrazione dispositivi di rete: *c:\inetpub\logs\LogFiles\W3SVC1*

- **Registro applicazioni di Windows**:

  questo log è utile quando si esaminano i problemi di IIS, ad esempio il pool di applicazioni SCEP.

  Percorso: Nel server che ospita il servizio Registrazione dispositivi di rete: Eseguire **eventvwr.msc** per aprire il Visualizzatore eventi di Windows




### <a name="logs-for-android-devices"></a>Log per dispositivi Android

Per i dispositivi che eseguono Android, usare il file di log dell’app **Portale aziendale Android** con nome **OMADM.log**. Prima di raccogliere ed esaminare i log, abilitare la [registrazione dettagliata](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android), quindi riprodurre il problema.

Per raccogliere il file OMADM.log da un dispositivo, vedere [Caricare e inviare per posta elettronica i log tramite un cavo USB](/intune-user-help/send-logs-to-your-it-admin-using-cable-android).

È anche possibile [caricare e inviare i log tramite posta elettronica](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app) al supporto.

### <a name="logs-for-ios-and-ipados-devices"></a>Log per i dispositivi iOS e iPadOS

Per i dispositivi che eseguono iOS/iPadOS si usano i log di debug e **Xcode** eseguito in un computer Mac:

1. Connettere il dispositivo iOS/iPadOS al Mac, quindi passare ad **Applicazioni** > **Utility** per aprire l'app Console. 

2. In **Azione** selezionare **Includi messaggi di informazioni** e **Includi messaggi di debug**.

   ![Selezionare le opzioni del log](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. Riprodurre il problema e salvare i log in un file di testo:
   1. Selezionare **Modifica** > **Seleziona tutto** per selezionare tutti i messaggi nella schermata corrente, quindi selezionare **Modifica** > **Copia** per copiare i messaggi negli Appunti. 
   2. Aprire l'applicazione TextEdit, incollare i log copiati in un nuovo file di testo e quindi salvare il file.


Il log Portale aziendale per i dispositivi iOS e iPadOS non contiene informazioni sui profili certificato SCEP.

### <a name="logs-for-windows-devices"></a>Log per dispositivi Windows

Per i dispositivi che eseguono Windows, usare i Registri eventi di Windows per diagnosticare i problemi di registrazione o di gestione per i dispositivi gestiti con Intune.

Nel dispositivo aprire **Visualizzatore eventi** > **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider**

![Registri eventi di Windows](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>Passaggi successivi

Esaminare la [distribuzione dei profili certificato SCEP](troubleshoot-scep-certificate-profile-deployment.md) 
