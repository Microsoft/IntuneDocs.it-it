---
title: Impostazioni VPN per dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare le impostazioni di configurazione della rete privata virtuale (VPN) disponibili, inclusi i dettagli della connessione, i metodi di autenticazione e lo split tunneling nelle impostazioni di base; le impostazioni VPN personalizzate con l'identificatore e le coppie chiave-valore; le impostazioni VPN per app che includono gli URL Safari e VPN su richiesta con SSID o domini di ricerca DNS; le impostazioni del proxy per includere un script di configurazione, un indirizzo IP o FQDN e una porta TCP nei dispositivi che eseguono iOS in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eb87d75512d9f04abac9db256d0d968bb85116ef
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Configurare le impostazioni VPN in Microsoft Intune per i dispositivi che eseguono iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono iOS.

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali quando cercano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo (FQDN) del server VPN a cui si connetteranno i dispositivi. Ad esempio, immettere **192.168.1.1** o **vpn.contoso.com**.
- **Metodo di autenticazione**: scegliere il metodo di autenticazione dei dispositivi al server VPN:
  - **Certificati**: in **Certificato di autenticazione** selezionare un profilo di certificato SCEP o PKCS esistente per autenticare la connessione. In [Configurare i certificati](certificates-configure.md) sono disponibili alcune indicazioni sui profili di certificato.
  - **Nome utente e password**: gli utenti finali devono immettere un nome utente e una password per accedere al server VPN.

    > [!NOTE]
    > Se nome utente e password vengono usati come metodo di autenticazione per la VPN IPSec Cisco, devono fornire SharedSecret tramite un profilo personalizzato di Apple Configurator.
  
- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **Cisco Legacy AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix**
  - **VPN personalizzata**

    > [!NOTE]
    > - I profili **VPN Cisco Legacy AnyConnect** sono destinati all'app [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 4.0.5x e versioni precedenti
    > - I profili **VPN Cisco AnyConnect** sono destinati all'app [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 4.0.7x e versioni successive

- **Split tunneling**: scegliere **Abilita** o **Disabilita** per consentire ai dispositivi di scegliere la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.

## <a name="custom-vpn-settings"></a>Impostazioni VPN personalizzate

Se si seleziona **VPN personalizzata** come tipo di connessione, configurare queste impostazioni aggiuntive:

- **Identificatore VPN**: identificatore per l'app VPN in uso, specificato dal provider VPN.
- **Immettere le coppie chiave-valore per gli attributi della VPN personalizzata**: aggiungere o importare **chiavi** e **valori** che consentono di personalizzare la connessione VPN. Anche questi valori vengono in genere forniti dal provider VPN.

## <a name="apps-per-app-vpn-settings"></a>Impostazioni delle app (VPN per app)

- **VPN per app**: abilitare questa opzione per consentire agli URL di abilitare la connessione VPN quando sono visitati dal browser Safari. Per configurare questa impostazione, è necessario avere selezionato **Certificati** come metodo di autenticazione nelle impostazioni VPN di base.
  - **URL Safari che attiveranno questa connessione VPN**: selezionare questa opzione per aggiungere uno o più URL del sito Web. Quando questi URL vengono visitati, la connessione VPN viene abilitata.

- **VPN su richiesta**: configurare le regole condizionali che controllano l'avvio della connessione VPN. Ad esempio, creare una condizione per cui la connessione VPN viene usata solo quando un dispositivo non è connesso a una rete Wi-Fi aziendale. Oppure, creare una condizione per cui, se un dispositivo non può accedere a un dominio di ricerca DNS specificato, la connessione VPN non viene avviata.

  - **SSID o domini di ricerca DNS**: selezionare se la condizione usa o meno **SSID** della rete wireless o **Domini di ricerca DNS**. Scegliere **Aggiungi** per configurare uno o più SSID o domini di ricerca.
  - **Probe della stringa dell'URL**: facoltativo. Immettere un URL che viene usato dalla regola come test. Se il dispositivo in cui è installato il profilo può accedere a questo URL senza il reindirizzamento, la connessione VPN viene avviata e il dispositivo si connette all'URL di destinazione. L'utente non visualizza il sito del probe della stringa dell'URL. Un esempio di probe della stringa dell'URL è l'indirizzo di un server Web di controllo che verifica la conformità del dispositivo prima della connessione VPN. Un'altra possibilità è che l'URL verifichi che la rete VPN possa connettersi a un sito prima di connettere il dispositivo all'URL di destinazione tramite VPN.
  - **Azione del dominio**: scegliere una delle opzioni seguenti:
    - Connetti se necessario
    - Non connettere mai
  - **Azione**: scegliere una delle opzioni seguenti:
    - Connessione
    - Valuta la connessione
    - Ignora
    - Disconnessione

## <a name="proxy-settings"></a>Impostazioni proxy

- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL del server proxy**, ad esempio **http://proxy.contoso.com**, contenente il file di configurazione.
- **Indirizzo**: immettere l'indirizzo IP del nome host completo del server proxy.
- **Numero di porta**: immettere il numero di porta associato al server proxy.

## <a name="next-step"></a>Passaggio successivo
[Creare profili VPN in Intune](vpn-settings-configure.md)
