---
title: Come configurare le impostazioni VPN di Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come usare Intune per configurare le connessioni VPN nei dispositivi gestiti.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: 96756c4aa5afa52821614d5f7fbc6d0bca15895b
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Come configurare le impostazioni VPN in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per stabilire una connessione con il server VPN. Usare i **profili VPN** in Microsoft Intune per distribuire le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete.

Si supponga, ad esempio, di voler effettuare il provisioning di tutti i dispositivi iOS con le impostazioni necessarie per connettersi a una condivisione file nella rete aziendale. Viene creato un profilo VPN contenente le impostazioni necessarie per connettersi alla rete aziendale, profilo che viene assegnato a tutti gli utenti che usano dispositivi iOS. Gli utenti visualizzano la connessione VPN nell'elenco delle reti disponibili e possono connettersi con la massima facilità.

## <a name="vpn-connection-types"></a>Tipi di connessione VPN

È possibile creare i profili VPN tramite i tipi di connessione seguenti:

||||||||
|-|-|-|-|-|-|-|
|Tipo di connessione|Android|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|Pulse Secure|Sì|Sì|Sì|Sì|Sì|sì|
|Cisco (IPSec)|No|Sì|No|No|No|No|
|Citrix|sì|Sì|No|No|No|No|
|F5 Edge Client|Sì|Sì|Sì|Sì|Sì|Sì|
|Dell SonicWALL Mobile Connect|Sì|Sì|Sì|Sì|Sì|sì|
|Check Point Capsule VPN|sì|Sì|Sì|Sì|Sì|sì|
|Cisco AnyConnect|Sì|Sì|Sì|No|No|No|
|Automatico|No|No|No|No|No|sì|
|IKEv2|No|No|No|No|No|Sì|
|L2TP|No|No|No|No|No|sì|
|PPTP|No|No|No|No|No|sì|
|Custom|No|Sì|Sì|No|No|No|


> [!IMPORTANT]
> Prima di usare i profili VPN distribuiti in un dispositivo, è necessario installare l'app VPN applicabile per il profilo È possibile usare le informazioni fornite nell'argomento [What is app management in Microsoft Intune?](/intune-azure/manage-apps/what-is-app-management) (Informazioni sulla gestione delle app in Microsoft Intune) per distribuire l'app usando Intune.  

Per informazioni su come creare profili VPN personalizzati usando le impostazioni URI, vedere [Create custom VPN profiles](create-custom-vpn-profiles.md) (Creare profili VPN personalizzati).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Creare un profilo dispositivo contenente le impostazioni VPN

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo VPN.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni VPN. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni del dispositivo VPN:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **VPN**.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [Impostazioni Android](vpn-for-android.md)
    - [Impostazioni iOS](vpn-for-ios.md)
    - [Impostazioni macOS](vpn-for-macos.md)
    - [Impostazioni Windows Phone 8.1](vpn-for-windows-phone-8-1.md)
    - [Impostazioni Windows 8.1](vpn-for-windows-8-1.md)
    - [Impostazioni Windows 10](vpn-for-windows-10.md)
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md).


## <a name="methods-of-securing-vpn-profiles"></a>Metodi per la protezione dei profili VPN

I profili VPN possono usare numerosi tipi di connessione e protocolli diversi di produttori diversi. Queste connessioni vengono in genere protette mediante uno dei due metodi seguenti.

### <a name="certificates"></a>Certificati

Quando si crea il profilo VPN, è possibile scegliere un profilo certificato SCEP o PKCS creato precedentemente in Intune. Questo metodo è noto come certificato di identità. Viene usato per eseguire l'autenticazione in base a un profilo certificato attendibile (o *certificato radice*) creato per stabilire che il dispositivo dell'utente è autorizzato a connettersi. Il certificato attendibile viene distribuito nel computer che esegue l'autenticazione della connessione VPN, in genere il server VPN.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Microsoft Intune](how-to-configure-certificates.md).

### <a name="user-name-and-password"></a>Nome utente e password

Per eseguire l'autenticazione al server VPN, l'utente deve specificare nome utente e password.

