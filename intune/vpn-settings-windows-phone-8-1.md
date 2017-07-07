---
title: Impostazioni VPN di Intune per dispositivi Windows Phone 8.1
titleSuffix: Intune on Azure
description: "Informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi Windows Phone 8.1.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1a9053f-02a7-4735-bc0d-fe4573b31ed4
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a009a16c7c475864f665f6ad0ab8fe1853c801b4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="vpn-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Impostazioni VPN per i dispositivi Windows Phone 8.1 in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

- **Apply all settings to Windows Phone 8.1 only**(Applica tutte le impostazioni solo a Windows Phone 8.1): si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni verranno applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni verranno applicate anche ai dispositivi Windows 10 Mobile.
- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui sfogliano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Metodo di autenticazione**: scegliere tra le seguenti modalità di autenticazione dei dispositivi per il server VPN:
    - **Certificati**: in **Certificato di autenticazione** scegliere un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [How to configure certificates](certificates-configure.md)(Come configurare i certificati).
    - **Nome utente e password**: gli utenti finali devono fornire un nome utente e una password per accedere al server VPN.
- **Server**: aggiungere uno o più server VPN a cui si connetteranno i dispositivi.
    - **Aggiungi**: apre il pannello **Aggiungi riga** in cui è possibile specificare le informazioni seguenti:
        - **Descrizione**: specificare un nome descrittivo per il server come **server VPN di Contoso**.
        - **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
        - **Server predefinito**: abilita questo server come server predefinito che i dispositivi useranno per stabilire la connessione. Assicurarsi di impostare un solo server come predefinito.
    - **Importa**: selezionare un file contenente un elenco delimitato da virgole di server nel formato descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i dati nell'elenco **Server**.
    - **Esporta**: esporta l'elenco dei server in un file di valori separati da virgole (CSV).

- **Ignora la VPN nella rete Wi-Fi aziendale**: abilitare questa opzione per specificare che la connessione VPN non verrà usata quando il dispositivo è connesso alla rete Wi-Fi aziendale.
- **Ignora la VPN nella rete Wi-Fi domestica**: abilitare questa opzione per specificare che la connessione VPN non verrà usata quando il dispositivo è connesso alla rete Wi-Fi domestica.

- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
    - **Check Point Capsule VPN**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **Gruppo o dominio di accesso** (solo Dell SonicWALL Mobile Connect): specificare il nome del gruppo o dominio di accesso a cui si desidera connettersi.
- **Ruolo** (solo Pulse Secure): specificare il nome del ruolo utente che ha accesso a questa connessione. Un ruolo utente consente di definire le opzioni e le impostazioni personali, oltre ad abilitare o disabilitare alcune funzionalità di accesso.
- **Area di autenticazione** (solo Pulse Secure): specificare il nome dell'area di autenticazione da usare. Un'area di autenticazione è un raggruppamento di risorse di autenticazione usate dal tipo di connessione Pulse Secure.

- **Elenco di ricerca suffisso DNS** - **aggiungere** uno o più suffissi DNS. Ogni suffisso DNS specificato verrà cercato al momento della connessione a un sito Web mediante un nome breve. Ad esempio, specificare i suffissi DNS **domain1.contoso.com** e **domain2.contoso.com** e visitare l'URL **http://mywebsite**: verranno cercati gli URL **http://mywebsite.domain1.contoso.com** e **http://mywebsite.domain2.contoso.com**.

- **XML personalizzato**: specificare i comandi XML personalizzati per la configurazione della connessione VPN.

    **Esempio per Pulse Secure:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>

```

**Esempio per CheckPoint Mobile VPN:**

```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Esempio per Dell SonicWALL Mobile Connect:**
```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>

```

**Esempio per F5 Edge Client:**
```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```

Per altre informazioni su come scrivere comandi XML personalizzati, fare riferimento alla documentazione della VPN fornita dai diversi produttori.

- **Split tunneling** - **abilitare** o **disabilitare** questa opzione che consente ai dispositivi di stabilire la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.




## <a name="proxy-settings"></a>Impostazioni proxy

- **Rileva automaticamente impostazioni proxy**: se il server VPN richiede un server proxy per la connessione, specificare se si desidera che i dispositivi rilevino automaticamente le impostazioni di connessione. Per altre informazioni, vedere la documentazione di Windows Server.
- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL del server proxy** (ad esempio **http://proxy.contoso.com**) che contiene il file di configurazione.
- **Usa server proxy**: abilitare questa opzione se si desidera immettere manualmente le impostazioni del server proxy.
    - **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
    - **Numero di porta**: immettere il numero di porta associato al server proxy.
- **Ignora proxy per indirizzi locali**: se il server VPN richiede un server proxy per la connessione, selezionare questa opzione se non si vuole usare il server proxy per gli indirizzi locali specificati. Per altre informazioni, vedere la documentazione di Windows Server.
