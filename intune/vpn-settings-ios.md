---
title: Impostazioni VPN di Intune per dispositivi iOS
titleSuffix: Intune on Azure
description: "Informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi iOS.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
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
ms.openlocfilehash: a6cc079b05037cc18b7d27dd0d2674e87e1d54d0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="vpn-settings-for-ios-devices-in-microsoft-intune"></a>Impostazioni VPN per dispositivi iOS in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base


**Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui sfogliano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
- **Metodo di autenticazione**: scegliere tra le seguenti modalità di autenticazione dei dispositivi per il server VPN:
    - **Certificati**: in **Certificato di autenticazione** scegliere un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [How to configure certificates](certificates-configure.md)(Come configurare i certificati).
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
- **Split tunneling** - **abilitare** o **disabilitare** questa opzione che consente ai dispositivi di stabilire la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.


## <a name="custom-vpn-settings"></a>Impostazioni VPN personalizzate

Se si seleziona **VPN personalizzata** come tipo di connessione, configurare queste impostazioni aggiuntive:

- **Identificatore VPN** È un identificatore per l'app VPN in uso e viene fornito dal provider VPN.
- **Immettere le coppie chiave-valore per gli attributi della VPN personalizzata** Aggiungere o importare **chiavi** e **valori** che consentono di personalizzare la connessione VPN. Anche questi valori vengono in genere forniti dal provider VPN.

## <a name="apps-per-app-vpn-settings"></a>Impostazioni delle app (VPN per app)

- **VPN per app**: abilitare questa opzione se si desidera che gli URL abilitino la connessione VPN quando visitati dal browser Safari. Per configurare questa impostazione, è necessario avere selezionato **Certificati** come metodo di autenticazione nelle impostazioni VPN di base.
- **URLs that will enable the VPN connection while using the Safari browser** (URL che abiliteranno la connessione VPN durante l'uso del browser Safari): fare clic su Aggiungi per aggiungere uno o più URL di sito Web. Quando vengono visitati questi URL, verrà attivata la connessione VPN.

- **On-demand rules** (Regole su richiesta): consente di configurare le regole condizionali che controllano l'avvio della connessione VPN. Ad esempio, è possibile creare una condizione per cui la connessione VPN viene usata solo quando un dispositivo non è connesso a una delle reti Wi-Fi dell'azienda. In alternativa, è possibile creare una condizione per cui, se un dispositivo non può accedere a un dominio di ricerca DNS specificato, la connessione VPN non viene avviata.

    - **SSIDs or DNS search domains** (SSID o domini di ricerca DNS): selezionare questa opzione se la condizione userà **SSIDs** (SSID) della rete wireless o **DNS search domains** (Domini di ricerca DNS). Scegliere Aggiungi per configurare uno o più SSID o domini di ricerca.
    - **Probe della stringa dell'URL**: facoltativo, specificare un URL che la regola usa come test. Se il dispositivo in cui è installato il profilo è in grado di accedere a tale URL senza il reindirizzamento, la connessione VPN verrà avviata e il dispositivo si connetterà all'URL di destinazione. L'utente non visualizzerà il sito del probe della stringa dell'URL. Un esempio di probe della stringa dell'URL è l'indirizzo di un server Web di controllo che verifica la conformità del dispositivo prima della connessione VPN. Un'altra possibilità è che l'URL verifichi la capacità della rete VPN di connettersi a un sito, prima di connettere il dispositivo all'URL di destinazione tramite VPN.
    - **Azione del dominio**: scegliere una delle azioni seguenti:
        - Connetti se necessario 
        - Non connettere mai 
    - **Azione**: scegliere una delle azioni seguenti:
        - Connetti 
        - Valuta la connessione 
        - Ignora 
        - Disconnetti 


## <a name="proxy-settings"></a>Impostazioni proxy

- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL del server proxy** (ad esempio **http://proxy.contoso.com**) che contiene il file di configurazione.
- **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
- **Numero di porta**: immettere il numero di porta associato al server proxy.
