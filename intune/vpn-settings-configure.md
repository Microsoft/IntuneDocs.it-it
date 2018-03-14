---
title: Come configurare le impostazioni VPN in Microsoft Intune
titleSuffix: 
description: Informazioni su come usare Microsoft Intune per configurare le connessioni a reti virtuali private (VPN) nei dispositivi gestiti.
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9480f19a8cd71e001d196674d3e285c8f2a8bb09
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Come configurare le impostazioni VPN in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per stabilire una connessione con il server VPN. Usare i **profili VPN** in Microsoft Intune per assegnare le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete.

Si supponga, ad esempio, di voler effettuare il provisioning di tutti i dispositivi iOS con le impostazioni necessarie per connettersi a una condivisione file nella rete aziendale. Viene creato un profilo VPN contenente le impostazioni necessarie per connettersi alla rete aziendale, profilo che viene assegnato a tutti gli utenti che usano dispositivi iOS. Gli utenti visualizzano la connessione VPN nell'elenco delle reti disponibili e possono connettersi con la massima facilità.

## <a name="vpn-connection-types"></a>Tipi di connessione VPN

È possibile creare i profili VPN tramite i tipi di connessione seguenti:

|Tipo di connessione|Android<br>Android for Work|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Pulse Secure|Sì|Sì|Sì|Sì|Sì|Sì|
|Cisco (IPSec)|No|Sì|No|No|No|No|
|Citrix|Sì|Sì|No|No|No|Sì|
|F5 Edge Client|Sì|Sì|Sì|Sì|Sì|Sì|
|SonicWall Mobile Connect|Sì|Sì|Sì|Sì|Sì|Sì|
|Check Point Capsule VPN|Sì|Sì|Sì|Sì|Sì|Sì|
|Cisco AnyConnect|Sì|Sì|Sì|No|No|No|
|Automatico|No|No|No|No|No|Sì|
|IKEv2|No|No|No|No|No|Sì|
|L2TP|No|No|No|No|No|Sì|
|PPTP|No|No|No|No|No|Sì|
|Personalizzato|No|Sì|Sì|No|No|No|


> [!IMPORTANT]
> Prima di usare i profili VPN assegnati a un dispositivo, è necessario installare l'app VPN applicabile per il profilo. È possibile usare le informazioni disponibili nell'articolo [Informazioni sulla gestione delle app in Microsoft Intune](app-management.md) per assegnare l'app usando Intune.  

Per informazioni su come creare profili VPN personalizzati usando le impostazioni URI, vedere [Create custom VPN profiles](custom-vpn-profiles-create.md) (Creare profili VPN personalizzati).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Creare un profilo dispositivo contenente le impostazioni VPN

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel riquadro dei profili scegliere **Crea profilo**.
4. Nel riquadro **Crea profilo** immettere un **nome** e una **descrizione** per il profilo VPN.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni VPN. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni del dispositivo VPN:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **VPN**.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [Impostazioni Android e Android for Work](vpn-settings-android.md)
    - [Impostazioni iOS](vpn-settings-ios.md)
    - [Impostazioni macOS](vpn-settings-macos.md)
    - [Impostazioni Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Impostazioni Windows 8.1](vpn-settings-windows-8-1.md)
    - [Impostazioni di Windows 10](vpn-settings-windows-10.md) (incluso Windows Holographic for Business)
8. Al termine tornare al riquadro **Crea profilo** e selezionare **Crea**.

Il profilo viene creato e visualizzato nel riquadro dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).


## <a name="methods-of-securing-vpn-profiles"></a>Metodi per la protezione dei profili VPN

I profili VPN possono usare numerosi tipi di connessione e protocolli diversi di produttori diversi. Queste connessioni vengono in genere protette mediante uno dei due metodi seguenti.

### <a name="certificates"></a>Certificati

Quando si crea il profilo VPN, è possibile scegliere un profilo certificato SCEP o PKCS creato precedentemente in Intune. Questo profilo è noto come certificato di identità. Viene usato per eseguire l'autenticazione in base a un profilo certificato attendibile (o *certificato radice*) creato per stabilire che il dispositivo dell'utente è autorizzato a connettersi. Il certificato attendibile viene assegnato al computer che esegue l'autenticazione della connessione VPN, in genere il server VPN.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Nome utente e password

Per eseguire l'autenticazione al server VPN, l'utente deve specificare nome utente e password.
