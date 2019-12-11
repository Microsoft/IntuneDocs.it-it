---
title: Aggiungere impostazioni VPN per dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Per i dispositivi Android, Android Enterprise, iOS, macOS e Windows, usare le impostazioni predefinite per creare connessioni VPN (Virtual Private Network) in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9fab50e0aefd926b4dc7a2b3559576642d5d6b79
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059301"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>Creare profili VPN per la connessione ai server VPN in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete della propria organizzazione. I dispositivi usano un profilo di connessione VPN per avviare una connessione con il server VPN. I **profili VPN** in Microsoft Intune assegnano le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete dell'organizzazione.

Si supponga, ad esempio, di voler configurare i dispositivi iOS con le impostazioni necessarie per connettersi a una condivisione file nella rete dell'organizzazione. Si crea un profilo VPN che include queste impostazioni e si assegna questo profilo a tutti gli utenti che hanno un dispositivo iOS. Gli utenti visualizzeranno la connessione VPN nell'elenco delle reti disponibili e potranno connettersi con la massima facilità.

> [!NOTE]
> È possibile usare [i criteri di configurazione personalizzati di Intune](custom-settings-configure.md) per creare profili VPN per le piattaforme seguenti:
>
> * Android 4 e versioni successive
> * Dispositivi registrati che eseguono Windows 8.1 e versioni successive
> * Windows Phone 8.1 e versioni successive
> * Dispositivi registrati che eseguono Windows 10 Desktop
> * Windows 10 Mobile
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>Tipi di connessione VPN

È possibile creare i profili VPN tramite i tipi di connessione seguenti:

|Tipo di connessione|Piattaforma|
|-|-|
|Automatico|Windows 10|
|Check Point Capsule VPN|- Android<br/>- Profili di lavoro Android Enterprise<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Cisco AnyConnect|- Android<br/>- Profili di lavoro Android Enterprise<br/>- Proprietario del dispositivo Android Enterprise (completamente gestito)<br/>- iOS<br/>- macOS|
|Cisco (IPSec)|iOS|
|Citrix SSO|- Android<br/>- Profili di lavoro Android Enterprise: Usare i [criteri di configurazione delle app](../apps/app-configuration-policies-use-android.md)<br/>- Proprietario del dispositivo Android Enterprise (completamente gestito): Usare i [criteri di configurazione delle app](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|VPN personalizzata|- iOS<br/>- macOS|
|F5 Access|- Android<br/>- Profili di lavoro Android Enterprise<br/>- Proprietario del dispositivo Android Enterprise (completamente gestito)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|IKEv2| - iOS<br/>- Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|- Profili di lavoro Android Enterprise: Usare i [criteri di configurazione delle app](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|PPTP|Windows 10|
|Pulse Secure|- Android<br/>- Profili di lavoro Android Enterprise<br/>- Proprietario del dispositivo Android Enterprise (completamente gestito)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|SonicWall Mobile Connect|- Android<br/>- Profili di lavoro Android Enterprise<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Zscaler|- Profili di lavoro Android Enterprise: Usare i [criteri di configurazione delle app](../apps/app-configuration-policies-use-android.md)<br/>- iOS|

> [!IMPORTANT]
> Prima di usare i profili VPN assegnati a un dispositivo, è necessario installare l'app VPN applicabile per il profilo. È possibile usare le informazioni disponibili nell'articolo [Informazioni sulla gestione delle app in Microsoft Intune](../apps/app-management.md) per assegnare l'app usando Intune.  

Per informazioni su come creare profili VPN personalizzati usando le impostazioni URI, vedere [Creare un profilo con impostazioni personalizzate](custom-settings-configure.md).

## <a name="create-a-device-profile"></a>Creare un profilo del dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un buon nome di profilo è **Profilo VPN per l'intera azienda**.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:

      - **Android**
      - **Android Enterprise** > **Solo proprietario del dispositivo**
      - **Android Enterprise** > **Solo profilo di lavoro**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 e versioni successive**
      - **Windows 10 e versioni successive**

    - **Tipo di profilo**: selezionare **VPN**.

4. Le impostazioni configurabili variano in base alla piattaforma scelta. Vedere gli articoli seguenti per informazioni dettagliate sulle impostazioni per ogni piattaforma:

    - [Impostazioni Android](vpn-settings-android.md)
    - [Impostazioni Android Enterprise](vpn-settings-android-enterprise.md)
    - [Impostazioni di iOS/iPadOS](vpn-settings-ios.md)
    - [Impostazioni macOS](vpn-settings-macos.md)
    - [Impostazioni Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Impostazioni Windows 8.1](vpn-settings-windows-8-1.md)
    - [Impostazioni di Windows 10](vpn-settings-windows-10.md) (incluso Windows Holographic for Business)

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco dei profili. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).

## <a name="secure-your-vpn-profiles"></a>Proteggere i profili VPN

I profili VPN possono usare numerosi tipi di connessione e protocolli diversi di produttori diversi. Queste connessioni vengono in genere protette mediante i metodi seguenti.

### <a name="certificates"></a>Certificati

Quando si crea il profilo VPN, è possibile scegliere un profilo certificato SCEP o PKCS creato precedentemente in Intune. Questo profilo è noto come certificato di identità. Viene usato per eseguire l'autenticazione in base a un profilo certificato attendibile (o *certificato radice*) creato per consentire all'utente del dispositivo di connettersi. Il certificato attendibile viene assegnato al computer che esegue l'autenticazione della connessione VPN, in genere il server VPN.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Microsoft Intune](../protect/certificates-configure.md).

### <a name="user-name-and-password"></a>Nome utente e password

Per eseguire l'autenticazione al server VPN, l'utente deve specificare nome utente e password.

## <a name="next-steps"></a>Passaggi successivi

Dopo che il profilo è stato creato, non è ancora operativo. Ora [assegnare il profilo](device-profile-assign.md) ad alcuni dispositivi.

È inoltre possibile creare e usare VPN per-app sui dispositivi [Android](android-pulse-secure-per-app-vpn.md) e [iOS](vpn-setting-configure-per-app.md).
