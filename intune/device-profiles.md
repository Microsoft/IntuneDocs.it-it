---
title: Che cosa sono i profili di dispositivo in Microsoft Intune? | Microsoft Docs
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sui profili di dispositivo Intune e sulle modalità di gestione e protezione dei dispositivi nell&quot;azienda."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 54b20d405613a67e54e9d22df45a3055f093fafa
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="what-are-microsoft-intune-device-profiles"></a>Informazioni sui profili di dispositivo in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Usare il carico di lavoro **Configurazione del dispositivo** di Microsoft Intune per gestire impostazioni e funzionalità in tutti i dispositivi gestiti. Questo carico di lavoro verrà usato principalmente per creare profili di dispositivo, che consentono di gestire e controllare una vasta gamma di funzionalità sui dispositivi gestiti.

All'apertura di questo carico di lavoro, verranno visualizzate le opzioni seguenti:

- **Overview** (Panoramica): questa pagina offre stato e report che consentono di monitorare le configurazioni del dispositivo assegnate a utenti e dispositivi.
- **Manage Profiles** (Gestione dei profili): questa sezione consente di creare profili di configurazione per i dispositivi. Di seguito riportiamo un elenco di tutti i tipi di profilo che è possibile creare.
- **Setup Certificate Authority** (Configurare l'autorità di certificazione): questo flusso di lavoro guida l'utente nella procedura necessaria per configurare i certificati. È necessario eseguire questa operazione se si desidera lavorare con i profili di certificato di Intune.

## <a name="getting-started"></a>Guida introduttiva

Il flusso di lavoro per la creazione di profili di dispositivo è simile per tutti i profili. Per informazioni su come creare i profili, leggere [How to create Microsoft Intune device configuration profiles](device-profile-create.md) (Come creare profili di configurazione del dispositivo Microsoft Intune). Continuare a leggere per informazioni specifiche sulla creazione delle impostazioni per ogni tipo di profilo.

Nei dispositivi è possibile gestire le funzionalità seguenti:

## <a name="device-features"></a>Funzionalità del dispositivo

Funzionalità del dispositivo consente di controllare le funzionalità dei dispositivi iOS e macOS come AirPrint, le notifiche e le configurazioni dei dispositivi condivisi.
Per altre informazioni, vedere [Come configurare le impostazioni relative alle funzionalità dei dispositivi](device-features-configure.md). Supporta: iOS e macOS.

## <a name="device-restrictions"></a>Limitazioni del dispositivo
Limitazioni del dispositivo consente di controllare una vasta gamma di impostazioni dei dispositivi gestiti relative a numerose categorie tra cui sicurezza, browser, hardware e condivisione dei dati. Ad esempio, è possibile creare un profilo di restrizione dei dispositivi che impedisce agli utenti di dispositivi iOS di accedere alla fotocamera.
Per altre informazioni, vedere [How to configure device restriction settings](device-restrictions-configure.md) (Come configurare le impostazioni di restrizione dei dispositivi). Supporta: Android, iOS, Mac OS, Windows 10 e Windows 10 Team.

## <a name="email"></a>Posta elettronica
I profili di posta elettronica consentono di creare, assegnare e monitorare le impostazioni di posta elettronica di Exchange ActiveSync nei dispositivi gestiti. Assegnando queste impostazioni, si garantisce coerenza, si riducono le chiamate al supporto e si consente agli utenti finali di accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione da parte loro.
Per altre informazioni, vedere [How to configure email settings](email-settings-configure.md) (Come configurare le impostazioni della posta elettronica). Supporta: Android, iOS, Windows Phone 8.1 e Windows 10.

## <a name="wi-fi"></a>Wi-Fi
Usare i profili Wi-Fi per assegnare le impostazioni di rete wireless agli utenti e ai dispositivi dell'organizzazione. Quando si assegna un profilo Wi-Fi, gli utenti hanno accesso alla rete Wi-Fi aziendale senza doverla configurare.
Per altre informazioni, vedere [How to configure Wi-Fi settings](wi-fi-settings-configure.md) (Come configurare le impostazioni Wi-Fi). Supporta: Android, iOS, macOS e Windows 8.1 (solo importazione).

## <a name="vpn"></a>Connessione
Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per stabilire una connessione con il server VPN. Usare i profili VPN per assegnare le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete.
Per altre informazioni, vedere [How to configure VPN settings](vpn-settings-configure.md) (Come configurare le impostazioni VPN).
Supporto: Android, iOS, Mac OS, Windows Phone 8.1, Windows 8.1 e Windows 10.

## <a name="education"></a>Istruzione
Consente di configurare le opzioni per l'app Test ed esami di Windows. Quando si configurano queste opzioni, nessun'altra app può essere eseguita sul dispositivo finché il test non è completato.
Per altre informazioni, vedere [Come configurare le impostazioni relative alla formazione](education-settings-configure.md).

## <a name="certificates"></a>Certificati
Questo tipo di profilo consente di configurare certificati attendibili SCEP e PKCS, da assegnare ai dispositivi e usati per autenticare i profili Wi-Fi, VPN e di posta elettronica.
Per altre informazioni, vedere [How to configure certificates](certificates-configure.md) (Come configurare i certificati). Supporta: Android, iOS, Windows Phone 8.1, Windows 8.1 e Windows 10.

## <a name="edition-upgrade"></a>Aggiornamento dell'edizione
Questo tipo di profilo consente di aggiornare automaticamente i dispositivi che eseguono alcune versioni di Windows 10 a una versione più recente. Per altre informazioni, vedere [How to configure Windows 10 edition upgrades](edition-upgrade-configure-windows-10.md) (Come configurare gli aggiornamenti dell'edizione di Windows 10). Supporta: solo Windows 10.

## <a name="windows-information-protection"></a>Windows Information Protection
Windows Information Protection offre protezione dalla perdita di dati senza interferire con l'esperienza del dipendente. Consente inoltre di proteggere le app e i dati aziendali da perdite di dati accidentali su dispositivi di proprietà dell'azienda e dispositivi personali che i dipendenti portano a lavoro senza richiedere modifiche per l'ambiente o altre app.
Per altre informazioni, vedere [How to configure Windows Information Protection](windows-information-protection-configure.md) (Come configurare Windows Information Protection). Supporta: solo Windows 10.

## <a name="custom"></a>Custom
Le impostazioni personalizzate consentono di assegnare ai dispositivi impostazioni non integrate in Intune. Ad esempio, sui dispositivi Android è possibile specificare valori URI OMA che consentono di configurare il dispositivo. Per i dispositivi iOS è possibile importare un file di configurazione creato in Apple Configurator.
Per altre informazioni, vedere [How to configure custom settings](custom-settings-configure.md) (Come configurare le impostazioni personalizzate). Supporta: Android, iOS, macOS e Windows 8.1 (solo importazione).

