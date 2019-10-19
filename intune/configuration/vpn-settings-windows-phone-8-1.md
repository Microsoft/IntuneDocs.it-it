---
title: Impostazioni VPN di Microsoft Intune per i dispositivi Windows Phone 8.1
titleSuffix: ''
description: Informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono Windows Phone 8.1.
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
ms.openlocfilehash: 69de660e65ed2a0f3b6c9c7e4ce774a6fcde2676
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506510"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Configurare le impostazioni VPN in Microsoft Intune per i dispositivi che eseguono Windows Phone 8.1

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo illustra le impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono Windows Phone 8.1.


A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

- **Applica tutte le impostazioni solo a Windows Phone 8.1**: si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni vengono applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni vengono applicate anche ai dispositivi Windows 10 Mobile.
- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Metodo di autenticazione**: scegliere tra le seguenti modalità di autenticazione dei dispositivi per il server VPN:
  - **Certificati**: in **Certificato di autenticazione** scegliere un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [How to configure certificates](../protect/certificates-configure.md)(Come configurare i certificati).
  - **Nome utente e password**: gli utenti finali devono fornire un nome utente e una password per accedere al server VPN.
- **Server**: aggiungere uno o più server VPN a cui si connettono i dispositivi.
  - **Aggiungi**: apre il pannello **Aggiungi riga** in cui è possibile specificare le informazioni seguenti:
    - **Descrizione**: specificare un nome descrittivo per il server come **server VPN di Contoso**.
    - **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
    - **Server predefinito**: abilita questo server come server predefinito che i dispositivi usano per stabilire la connessione. Assicurarsi di impostare un solo server come predefinito.
  - **Importa**: selezionare un file contenente un elenco delimitato da virgole di server nel formato descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i dati nell'elenco **Server**.
  - **Esporta**: esporta l'elenco dei server in un file di valori separati da virgole (CSV).

- **Ignora la VPN nella rete Wi-Fi aziendale**: abilitare questa opzione per specificare che la connessione VPN non viene usata quando il dispositivo è connesso alla rete Wi-Fi aziendale.
- **Ignora la VPN nella rete Wi-Fi domestica**: abilitare questa opzione per specificare che la connessione VPN non viene usata quando il dispositivo è connesso alla rete Wi-Fi domestica.

- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **Gruppo o dominio di accesso** (solo SonicWall Mobile Connect): specificare il nome del gruppo o dominio di accesso a cui si vuole connettersi.
- **Ruolo** (solo Pulse Secure): specificare il nome del ruolo utente che ha accesso a questa connessione. Un ruolo utente consente di definire le opzioni e le impostazioni personali, oltre ad abilitare o disabilitare alcune funzionalità di accesso.
- **Area di autenticazione** (solo Pulse Secure): specificare il nome dell'area di autenticazione da usare. Un'area di autenticazione è un raggruppamento di risorse di autenticazione usate dal tipo di connessione Pulse Secure.

- **Elenco di ricerca suffisso DNS** - **aggiungere** uno o più suffissi DNS. Ogni suffisso DNS specificato viene cercato al momento della connessione a un sito Web mediante un nome breve. Ad esempio, specificare i suffissi DNS **domain1.contoso.com** e **domain2.contoso.com**, visitare l'URL `http://mywebsite` per eseguire la ricerca degli URL `http://mywebsite.domain1.contoso.com` e `http://mywebsite.domain2.contoso.com`.

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

Per altre informazioni su come scrivere comandi XML personalizzati, fare riferimento alla documentazione della VPN fornita dai diversi produttori.

- **Split tunneling** - **Abilitare** o **disabilitare** questa opzione che consente ai dispositivi di stabilire la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.




## <a name="proxy-settings"></a>Impostazioni proxy

- **Rileva automaticamente impostazioni proxy**: se il server VPN richiede un server proxy per la connessione, specificare se si desidera che i dispositivi rilevino automaticamente le impostazioni di connessione. Per altre informazioni, vedere la documentazione di Windows Server.
- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL server proxy**, ad esempio `http://proxy.contoso.com`, contenente il file di configurazione.
- **Usa server proxy**: abilitare questa opzione se si desidera immettere manualmente le impostazioni del server proxy.
  - **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
  - **Numero di porta**: immettere il numero di porta associato al server proxy.
- **Ignora proxy per indirizzi locali**: se il server VPN richiede un server proxy per la connessione, selezionare questa opzione se non si vuole usare il server proxy per gli indirizzi locali specificati. Per altre informazioni, vedere la documentazione di Windows Server.
