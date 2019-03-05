---
title: Impostazioni VPN di Microsoft Intune per i dispositivi macOS
titlesuffix: ''
description: Informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ead7b89d9d8117e7b850be99a4f51188a2efb01c
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238388"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-macos"></a>Configurare le impostazioni VPN in Microsoft Intune per i dispositivi che eseguono macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono macOS.

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

**Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
- **Metodo di autenticazione**: scegliere tra le seguenti modalità di autenticazione dei dispositivi per il server VPN:
    - **Certificati**: in **Certificato di autenticazione** scegliere un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [How to configure certificates](certificates-configure.md)(Come configurare i certificati).
    - **Nome utente e password**: gli utenti finali devono fornire un nome utente e una password per accedere al server VPN.
- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **VPN personalizzata**
- **Split tunneling** - **Abilitare** o **disabilitare** questa opzione che consente ai dispositivi di stabilire la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Impostazioni VPN personalizzate

Se si seleziona **VPN personalizzata**, configurare queste altre impostazioni:

- **Identificatore VPN** È un identificatore per l'app VPN in uso e viene fornito dal provider VPN.
- **Immettere le coppie chiave-valore per gli attributi della VPN personalizzata** Aggiungere o importare **chiavi** e **valori** che consentono di personalizzare la connessione VPN. Anche questi valori vengono in genere forniti dal provider VPN.


## <a name="proxy-settings"></a>Impostazioni proxy

- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL server proxy** che contiene il file di configurazione. Immettere ad esempio `http://proxy.contoso.com`.
- **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
- **Numero di porta**: immettere il numero di porta associato al server proxy.
