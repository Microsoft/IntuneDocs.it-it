---
title: Creare profili di dispositivo VPN in Microsoft Intune - Azure | Microsoft Docs
description: Per i dispositivi iOS, visualizzare i tipi di connessione di rete privata virtuale (VPN), creare un profilo del dispositivo VPN nel portale di Azure e visualizzare le opzioni per proteggere il profilo VPN con certificati, o nome utente e password in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cd605542a0711e27f87d68af51662fd318f3250e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184880"
---
# <a name="create-vpn-profiles-in-intune"></a>Creare profili VPN in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per stabilire una connessione con il server VPN. Usare i **profili VPN** in Microsoft Intune per assegnare le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete.

Si supponga, ad esempio, di voler effettuare il provisioning di tutti i dispositivi iOS con le impostazioni necessarie per connettersi a una condivisione file nella rete aziendale. Si crea un profilo VPN contenente le impostazioni per connettersi alla rete aziendale. e si assegna questo profilo a tutti gli utenti che hanno un dispositivo iOS. Gli utenti visualizzeranno la connessione VPN nell'elenco delle reti disponibili e potranno connettersi con la massima facilità.

È possibile usare i criteri di configurazione personalizzati di Intune per creare profili VPN per le piattaforme seguenti:

* Android 4 e versioni successive
* Dispositivi registrati che eseguono Windows 8.1 e versioni successive
* Windows Phone 8.1 e versioni successive
* Dispositivi registrati che eseguono Windows 10 Desktop
* Windows 10 Mobile
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>Tipi di connessione VPN

È possibile creare i profili VPN tramite i tipi di connessione seguenti:

|Tipo di connessione|Android<br>Profili di lavoro Android|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Automatico|No|No|No|No|No|Sì|
|Check Point Capsule VPN|Sì|Sì|Sì|Sì|Sì|Sì|
|Cisco AnyConnect|Sì|Sì|Sì|No|No|No|
|SonicWall Mobile Connect|Sì|Sì|Sì|Sì|Sì|Sì|
|F5 Edge Client|Sì|Sì|Sì|Sì|Sì|Sì|
|Palo Alto Networks GlobalProtect|No|Sì|No|No|No|Sì|
|Pulse Secure|Sì|Sì|Sì|Sì|Sì|Sì|
|Cisco (IPSec)|No|Sì|No|No|No|No|
|Citrix|Sì (solo Android)|Sì|No|No|No|Sì|
|IKEv2|No|No|No|No|No|Sì|
|L2TP|No|No|No|No|No|Sì|
|PPTP|No|No|No|No|No|Sì|
|Zscaler|No|Sì|No|No|No|No|
|VPN personalizzata|No|Sì|Sì|No|No|No|

> [!IMPORTANT]
> Prima di usare i profili VPN assegnati a un dispositivo, è necessario installare l'app VPN applicabile per il profilo. È possibile usare le informazioni disponibili nell'articolo [Informazioni sulla gestione delle app in Microsoft Intune](app-management.md) per assegnare l'app usando Intune.  

Per informazioni su come creare profili VPN personalizzati usando le impostazioni URI, vedere [Creare un profilo con impostazioni personalizzate](custom-settings-configure.md).

## <a name="create-a-device-profile-containing-vpn-settings"></a>Creare un profilo dispositivo contenente le impostazioni VPN

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
4. Immettere un **Nome** e una **Descrizione** per il profilo VPN.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni VPN. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni del dispositivo VPN:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 e versioni successive**
   - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **VPN**.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
   - [Impostazioni di Android e del profilo di lavoro Android](vpn-settings-android.md)
   - [Impostazioni iOS](vpn-settings-ios.md)
   - [Impostazioni macOS](vpn-settings-macos.md)
   - [Impostazioni Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
   - [Impostazioni Windows 8.1](vpn-settings-windows-8-1.md)
   - [Impostazioni di Windows 10](vpn-settings-windows-10.md) (incluso Windows Holographic for Business)
8. Al termine, **creare** il profilo

Il profilo viene creato e visualizzato nell'elenco dei profili. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).

## <a name="methods-of-securing-vpn-profiles"></a>Metodi per la protezione dei profili VPN

I profili VPN possono usare numerosi tipi di connessione e protocolli diversi di produttori diversi. Queste connessioni vengono in genere protette mediante uno dei due metodi seguenti.

### <a name="certificates"></a>Certificati

Quando si crea il profilo VPN, è possibile scegliere un profilo certificato SCEP o PKCS creato precedentemente in Intune. Questo profilo è noto come certificato di identità. Viene usato per eseguire l'autenticazione in base a un profilo certificato attendibile (o *certificato radice*) creato per consentire all'utente del dispositivo di connettersi. Il certificato attendibile viene assegnato al computer che esegue l'autenticazione della connessione VPN, in genere il server VPN.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Nome utente e password

Per eseguire l'autenticazione al server VPN, l'utente deve specificare nome utente e password.
