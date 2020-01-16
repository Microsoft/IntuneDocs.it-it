---
title: Configurare impostazioni VPN per dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di configurazione di rete privata virtuale (VPN), inclusi i dettagli della connessione, il tunneling suddiviso, le impostazioni VPN personalizzate con l'identificatore, le coppie chiave-valore, le impostazioni proxy con uno script di configurazione, l'indirizzo IP o FQDN e la porta TCP in Microsoft Intune nei dispositivi che eseguono macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0bb2cb757e944369642807f117683dad3a9805a
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206262"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>Aggiungere impostazioni VPN in dispositivi macOS in Microsoft Intune



Questo articolo illustra le impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono macOS.

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](vpn-settings-configure.md).

> [!NOTE]
> Queste impostazioni sono disponibili per tutti i tipi di registrazione. Per ulteriori informazioni sui tipi di registrazione, vedere la pagina relativa alla [registrazione MacOS](../enrollment/macos-enroll.md).

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

**Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connettono i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
- **Metodo di autenticazione**: scegliere uno dei metodi seguenti di autenticazione dei dispositivi al server VPN:
  - **Certificati**: in **Certificato di autenticazione** scegliere un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [Come configurare i certificati](../protect/certificates-configure.md).
  - **Nome utente e password**: gli utenti finali devono specificare un nome utente e una password per accedere al server VPN.
- **Tipo di connessione**: Selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **VPN personalizzata**
- **Split tunneling**: **Abilitare** o **disabilitare** questa opzione che consente ai dispositivi di stabilire la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Impostazioni VPN personalizzate

Se si seleziona **VPN personalizzata**, configurare queste altre impostazioni:

- **Identificatore VPN**: immettere un identificatore per l'app VPN in uso. Questo identificatore viene fornito dal provider VPN.
- **Immettere le coppie chiave-valore per gli attributi della VPN personalizzata**: Aggiungere o importare **chiavi** e **valori** per la personalizzazione della connessione VPN. Questi valori vengono in genere forniti dal provider VPN.

## <a name="proxy-settings"></a>Impostazioni proxy

- **Script di configurazione automatica**: consente di usare un file per configurare il server proxy. Immettere l'**URL server proxy** che contiene il file di configurazione. Immettere ad esempio `http://proxy.contoso.com`.
- **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
- **Numero porta**: immettere il numero di porta associato al server proxy.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Configurare le impostazioni VPN nei dispositivi [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [iOS](vpn-settings-ios.md)e [Windows 10](vpn-settings-windows-10.md) .
