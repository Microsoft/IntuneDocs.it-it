---
title: Impostazioni VPN di Intune per dispositivi iOS
titlesuffix: Azure portal
description: "Informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi iOS.\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1447c123-ea33-4ea0-aab4-69577cdb8d00
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 27b29c7e7dd256484763b9a0cbe9e76f32fe74d8
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="vpn-settings-for-ios-devices-in-microsoft-intune"></a>Impostazioni VPN per dispositivi iOS in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base


**Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
- **Metodo di autenticazione**: scegliere tra le seguenti modalità di autenticazione dei dispositivi per il server VPN:
    - **Certificati**: in **Certificato di autenticazione** scegliere un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [Come configurare i certificati](certificates-configure.md).
    - **Nome utente e password**: gli utenti finali devono fornire un nome utente e una password per accedere al server VPN.
- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Cisco (IPSec)**
    - **Citrix**
    - **VPN personalizzata**
- **Split tunneling** - **Abilitare** o **disabilitare** questa opzione che consente ai dispositivi di stabilire la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.


## <a name="custom-vpn-settings"></a>Impostazioni VPN personalizzate

Se si seleziona **VPN personalizzata** come tipo di connessione, configurare queste impostazioni aggiuntive:

- **Identificatore VPN** È un identificatore per l'app VPN in uso e viene fornito dal provider VPN.
- **Immettere le coppie chiave-valore per gli attributi della VPN personalizzata** Aggiungere o importare **chiavi** e **valori** che consentono di personalizzare la connessione VPN. Anche questi valori vengono in genere forniti dal provider VPN.

## <a name="apps-per-app-vpn-settings"></a>Impostazioni delle app (VPN per app)

- **VPN per app**: abilitare questa opzione per consentire agli URL di abilitare la connessione VPN quando sono visitati dal browser Safari. Per configurare questa impostazione, è necessario avere selezionato **Certificati** come metodo di autenticazione nelle impostazioni VPN di base.
- **Specifica URL che abiliteranno la connessione VPN durante l'uso del browser Safari**: fare clic su Aggiungi per aggiungere uno o più URL di siti Web. Quando questi URL vengono visitati, la connessione VPN viene abilitata.

- **On-demand rules** (Regole su richiesta): consente di configurare le regole condizionali che controllano l'avvio della connessione VPN. Ad esempio, è possibile creare una condizione per cui la connessione VPN viene usata solo quando un dispositivo non è connesso a una delle reti Wi-Fi dell'azienda. In alternativa, è possibile creare una condizione per cui, se un dispositivo non può accedere a un dominio di ricerca DNS specificato, la connessione VPN non viene avviata.

    - **SSID o domini di ricerca DNS**: specificare se la condizione userà o meno **SSID** della rete wireless o **Domini di ricerca DNS**. Scegliere Aggiungi per configurare uno o più SSID o domini di ricerca.
    - **Probe della stringa dell'URL**: facoltativo, specificare un URL che la regola usa come test. Se il dispositivo in cui è installato il profilo è in grado di accedere a questo URL senza il reindirizzamento, la connessione VPN viene avviata e il dispositivo si connette all'URL di destinazione. L'utente non visualizzerà il sito del probe della stringa dell'URL. Un esempio di probe della stringa dell'URL è l'indirizzo di un server Web di controllo che verifica la conformità del dispositivo prima della connessione VPN. Un'altra possibilità è che l'URL verifichi che la rete VPN possa connettersi a un sito prima di connettere il dispositivo all'URL di destinazione tramite VPN.
    - **Azione del dominio**: scegliere una delle voci seguenti:
        - Connetti se necessario 
        - Non connettere mai 
    - **Azione**: scegliere una delle voci seguenti:
        - Connetti 
        - Valuta la connessione 
        - Ignora 
        - Disconnetti 


## <a name="proxy-settings"></a>Impostazioni proxy

- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL del server proxy** (ad esempio **http://proxy.contoso.com**) che contiene il file di configurazione.
- **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
- **Numero di porta**: immettere il numero di porta associato al server proxy.