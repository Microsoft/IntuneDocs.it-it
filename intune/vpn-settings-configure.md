---
title: Come configurare le impostazioni VPN di Intune
titleSuffix: Azure portal
description: Informazioni su come usare Intune per configurare le connessioni VPN nei dispositivi gestiti."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 699fa64bc0f720b18c1376e39b85eccd9018bbaf
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Come configurare le impostazioni VPN in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. I dispositivi usano un profilo di connessione VPN per stabilire una connessione con il server VPN. Usare i **profili VPN** in Microsoft Intune per assegnare le impostazioni VPN agli utenti e ai dispositivi dell'organizzazione in modo che possano connettersi in modo facile e sicuro alla rete.

Si supponga, ad esempio, di voler effettuare il provisioning di tutti i dispositivi iOS con le impostazioni necessarie per connettersi a una condivisione file nella rete aziendale. Viene creato un profilo VPN contenente le impostazioni necessarie per connettersi alla rete aziendale, profilo che viene assegnato a tutti gli utenti che usano dispositivi iOS. Gli utenti visualizzano la connessione VPN nell'elenco delle reti disponibili e possono connettersi con la massima facilità.

## <a name="vpn-connection-types"></a>Tipi di connessione VPN

È possibile creare i profili VPN tramite i tipi di connessione seguenti:

|Tipo di connessione|Android<br>Android for Work|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Pulse Secure|Sì|Sì|Sì|Sì|Sì|sì|
|Cisco (IPSec)|No|Sì|No|No|No|No|
|Citrix|sì|Sì|No|No|No|Sì|
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
> Prima di usare i profili VPN assegnati a un dispositivo, è necessario installare l'app VPN applicabile per il profilo. È possibile usare le informazioni fornite nell'argomento [Informazioni sulla gestione delle app in Microsoft Intune](app-management.md) per assegnare l'app usando Intune.  

Per informazioni su come creare profili VPN personalizzati usando le impostazioni URI, vedere [Create custom VPN profiles](custom-vpn-profiles-create.md) (Creare profili VPN personalizzati).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Creare un profilo dispositivo contenente le impostazioni VPN

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo VPN.
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
    - [Impostazioni Windows 10](vpn-settings-windows-10.md)
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).


## <a name="methods-of-securing-vpn-profiles"></a>Metodi per la protezione dei profili VPN

I profili VPN possono usare numerosi tipi di connessione e protocolli diversi di produttori diversi. Queste connessioni vengono in genere protette mediante uno dei due metodi seguenti.

### <a name="certificates"></a>Certificati

Quando si crea il profilo VPN, è possibile scegliere un profilo certificato SCEP o PKCS creato precedentemente in Intune. Questo metodo è noto come certificato di identità. Viene usato per eseguire l'autenticazione in base a un profilo certificato attendibile (o *certificato radice*) creato per stabilire che il dispositivo dell'utente è autorizzato a connettersi. Il certificato attendibile viene assegnato al computer che esegue l'autenticazione della connessione VPN, in genere il server VPN.

Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Nome utente e password

Per eseguire l'autenticazione al server VPN, l'utente deve specificare nome utente e password.
