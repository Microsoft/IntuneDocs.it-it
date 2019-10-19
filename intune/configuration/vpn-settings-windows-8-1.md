---
title: Impostazioni VPN di Microsoft Intune per i dispositivi Windows 8.1
titleSuffix: ''
description: Informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono Windows 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 12267ce4e29fe2d53d01aa8115cafbf2196d50ed
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490848"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>Configurare le impostazioni VPN in Microsoft Intune per i dispositivi che eseguono Windows 8.1

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo illustra le impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono Windows 8.1.

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base


- **Applica tutte le impostazioni solo a Windows 8.1**: si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni vengono applicate solo ai dispositivi Windows 8.1. Se è impostata su **Non configurato**, queste impostazioni vengono applicate anche ai dispositivi Windows 10.
- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Server**: aggiungere uno o più server VPN a cui si connettono i dispositivi.
  - **Aggiungi**: apre la pagina **Aggiungi riga** in cui è possibile specificare le informazioni seguenti:
    - **Descrizione**: specificare un nome descrittivo per il server come **server VPN di Contoso**.
    - **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
    - **Server predefinito**: abilita questo server come server predefinito che i dispositivi usano per stabilire la connessione. Assicurarsi di impostare un solo server come predefinito.
  - **Importa**: selezionare un file contenente un elenco delimitato da virgole di server nel formato descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i dati nell'elenco **Server**.
  - **Esporta**: esporta l'elenco dei server in un file di valori separati da virgole (CSV).

- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Gruppo o dominio di accesso** (solo SonicWall Mobile Connect): specificare il nome del gruppo o dominio di accesso a cui si vuole connettersi.

- **Ruolo** (solo Pulse Secure): specificare il nome del ruolo utente che ha accesso a questa connessione. Un ruolo utente consente di definire le opzioni e le impostazioni personali, oltre ad abilitare o disabilitare alcune funzionalità di accesso.

- **Area di autenticazione** (solo Pulse Secure): specificare il nome dell'area di autenticazione da usare. Un'area di autenticazione è un raggruppamento di risorse di autenticazione usate dal tipo di connessione Pulse Secure.


- **XML personalizzato**: specificare i comandi XML personalizzati per la configurazione della connessione VPN.

**Esempio per Pulse Secure:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Esempio per CheckPoint Mobile VPN:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Esempio per SonicWall Mobile Connect:**

```xml
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Esempio per F5 Edge Client:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Per altre informazioni, fare riferimento alla documentazione della VPN del produttore relativa alla scrittura di comandi XML personalizzati.


## <a name="proxy-settings"></a>Impostazioni proxy

- **Rileva automaticamente impostazioni proxy**: se il server VPN richiede un server proxy per la connessione, specificare se si desidera che i dispositivi rilevino automaticamente le impostazioni di connessione. Per altre informazioni, vedere la documentazione di Windows Server.
- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL server proxy** che contiene il file di configurazione. Immettere ad esempio `http://proxy.contoso.com`.
- **Usa server proxy**: abilitare questa opzione se si desidera immettere manualmente le impostazioni del server proxy.
  - **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
  - **Numero di porta**: immettere il numero di porta associato al server proxy.
- **Ignora proxy per indirizzi locali**: se il server VPN richiede un server proxy per la connessione, selezionare questa opzione se non si vuole usare il server proxy per gli indirizzi locali specificati. Per altre informazioni, vedere la documentazione di Windows Server.
