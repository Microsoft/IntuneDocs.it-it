---
title: Che cosa sono i profili di dispositivo in Microsoft Intune?
titlesuffix: Azure portal
description: "Informazioni sui profili di dispositivo Intune e sulle modalità di gestione e protezione dei dispositivi nell'azienda.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0c745f9f745802e0de7a58e3dd7570c0e363ab5d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Informazioni sui profili di dispositivo in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare il carico di lavoro **Configurazione del dispositivo** di Microsoft Intune per gestire impostazioni e funzionalità in tutti i dispositivi gestiti. Questo carico di lavoro viene usato principalmente per creare profili di dispositivo, che consentono di gestire e controllare una vasta gamma di funzionalità dei dispositivi.

Quando si apre questo carico di lavoro, vengono visualizzate le opzioni seguenti:

- **Overview** (Panoramica): questa pagina offre stato e report che consentono di monitorare le configurazioni del dispositivo assegnate a utenti e dispositivi.
- **Manage Profiles** (Gestione profili): questa sezione consente di creare profili di configurazione per i dispositivi. Più avanti in questo argomento è presente un elenco di tutti i tipi di profilo che è possibile creare.
- **Setup Certificate Authority** (Configurazione autorità di certificazione): questo flusso di lavoro guida l'utente nella procedura necessaria per configurare i profili certificato di Intune.

## <a name="getting-started"></a>Guida introduttiva

Il flusso di lavoro per la creazione di profili di dispositivo è simile per tutti i profili. Per informazioni, leggere [Come creare profili di configurazione del dispositivo in Microsoft Intune](device-profile-create.md). Continuare a leggere per informazioni specifiche sulla creazione delle impostazioni per ogni tipo di profilo.

Nei dispositivi è possibile gestire le funzionalità seguenti:

## <a name="device-features"></a>Funzionalità del dispositivo

Funzionalità del dispositivo consente di controllare le funzionalità dei dispositivi iOS e macOS come AirPrint, le notifiche e le configurazioni dei dispositivi condivisi.
Per altre informazioni, vedere [Come configurare le impostazioni relative alle funzionalità dei dispositivi](device-features-configure.md). Supporta: iOS e macOS.

## <a name="device-restrictions"></a>Limitazioni del dispositivo
Le restrizioni dei dispositivi consentono di controllare numerose impostazioni dei dispositivi gestiti per numerose categorie, ad esempio le impostazioni relative alla sicurezza, all'hardware e alla condivisione dei dati. Ad esempio, è possibile creare un profilo di restrizione dei dispositivi che impedisce agli utenti di dispositivi iOS di accedere alla fotocamera.
Per altre informazioni, vedere [Come configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune](device-restrictions-configure.md). Sistemi operativi supportati: Android, iOS, Mac OS, Windows 10 e Windows 10 Team.

## <a name="email"></a>Posta elettronica
I profili di posta elettronica consentono di creare, assegnare e monitorare le impostazioni di posta elettronica di Exchange ActiveSync nei dispositivi gestiti. I profili di posta elettronica garantiscono coerenza e consentono di ridurre le chiamate al supporto. Grazie ad essi, poi, gli utenti finali possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione manuale.
Per altre informazioni, vedere [Come configurare le impostazioni di posta elettronica in Microsoft Intune](email-settings-configure.md). Sistemi operativi supportati: Android, iOS, Windows Phone 8.1 e Windows 10.

## <a name="wi-fi"></a>Wi-Fi
Usare i profili Wi-Fi per assegnare le impostazioni di rete wireless agli utenti e ai dispositivi dell'organizzazione. Quando si assegna un profilo Wi-Fi, gli utenti hanno accesso alla rete Wi-Fi aziendale senza doverla configurare.
Per altre informazioni, vedere [Come configurare le impostazioni Wi-Fi](wi-fi-settings-configure.md). Sistemi operativi supportati: Android, iOS, macOS e Windows 8.1 (solo importazione).

## <a name="vpn"></a>Connessione
Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per stabilire una connessione con il server VPN. Assegnare profili VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete.
Per altre informazioni, vedere [How to configure VPN settings](vpn-settings-configure.md) (Come configurare le impostazioni VPN).
Sistemi operativi supportati: Android, iOS, Mac OS, Windows Phone 8.1, Windows 8.1 e Windows 10.

## <a name="education"></a>Istruzione
Consente di configurare le opzioni per l'app Test ed esami di Windows. Quando si configurano queste opzioni, nessun'altra app può essere eseguita sul dispositivo finché il test non è completato.
Per altre informazioni, vedere [Come configurare le impostazioni relative alla formazione](education-settings-configure.md).

## <a name="certificates"></a>Certificati
Questo tipo di profilo consente di configurare certificati attendibili SCEP e PKCS, da assegnare ai dispositivi e usati per autenticare i profili Wi-Fi, VPN e di posta elettronica.
Per altre informazioni, vedere [Come configurare i certificati](certificates-configure.md). Sistemi operativi supportati: Android, iOS, Windows Phone 8.1, Windows 8.1 e Windows 10.

## <a name="edition-upgrade"></a>Aggiornamento dell'edizione
Questo tipo di profilo consente di aggiornare automaticamente i dispositivi che eseguono alcune versioni di Windows 10 a un'edizione più recente.
Per altre informazioni, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md). Sistemi operativi supportati: solo Windows 10.

## <a name="endpoint-protection"></a>Endpoint Protection
Questo tipo di profilo consente di configurare le impostazioni di BitLocker e Windows Defender per i dispositivi Windows 10.
Per altre informazioni, vedere [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10 e versioni successive). Sistemi operativi supportati: solo Windows 10.

## <a name="windows-information-protection"></a>Windows Information Protection
Windows Information Protection offre protezione dalla perdita di dati senza interferire con l'esperienza del dipendente. Consente inoltre di proteggere le app e i dati aziendali da perdite di dati accidentali su dispositivi di proprietà dell'azienda e dispositivi personali che i dipendenti portano a lavoro senza richiedere modifiche per l'ambiente o altre app.
Per altre informazioni, vedere [How to configure Windows Information Protection](windows-information-protection-configure.md) (Come configurare Windows Information Protection). Supporta: solo Windows 10.

## <a name="custom"></a>Custom
Le impostazioni personalizzate consentono di assegnare ai dispositivi impostazioni non integrate in Intune. Ad esempio, sui dispositivi Android è possibile specificare valori URI OMA che consentono di configurare il dispositivo. Per i dispositivi iOS è possibile importare un file di configurazione creato in Apple Configurator.
Per altre informazioni, vedere [How to configure custom settings](custom-settings-configure.md) (Come configurare impostazioni personalizzate). Sistemi operativi supportati: Android, iOS, macOS e Windows 8.1 (solo importazione).

## <a name="next-steps"></a>Passaggi successivi
Scegliere uno dei tipi di profilo dall'elenco per iniziare la configurazione dei dispositivi.
