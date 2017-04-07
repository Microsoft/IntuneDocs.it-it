---
title: Impostazioni VPN di Intune per dispositivi Windows 8.1
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi Windows 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: f38526a3e60f2a6628e61ffca5f5d179a2718e9b
ms.lasthandoff: 02/18/2017


---

# <a name="vpn-settings-for-windows-81-devices-in-microsoft-intune"></a>Impostazioni VPN per i dispositivi Windows 8.1 in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base


- **Apply all settings to Windows 8.1 only** (Applica tutte le impostazioni solo a Windows 8.1): si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni verranno applicate solo ai dispositivi Windows 8.1. Se è impostata su **Non configurato**, queste impostazioni verranno applicate anche ai dispositivi Windows 10.
- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui sfogliano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Server**: aggiungere uno o più server VPN a cui si connetteranno i dispositivi.
    - **Aggiungi**: apre il pannello **Aggiungi riga** in cui è possibile specificare le informazioni seguenti:
        - **Descrizione**: specificare un nome descrittivo per il server come **server VPN di Contoso**.
        - **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
        - **Server predefinito**: abilita questo server come server predefinito che i dispositivi useranno per stabilire la connessione. Assicurarsi di impostare un solo server come predefinito.
    - **Importa**: selezionare un file contenente un elenco delimitato da virgole di server nel formato descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i dati nell'elenco **Server**.
    - **Esporta**: esporta l'elenco dei server in un file di valori separati da virgole (CSV).

- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
- **Check Point Capsule VPN**
- **Dell SonicWALL Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Gruppo o dominio di accesso** (solo Dell SonicWALL Mobile Connect): specificare il nome del gruppo o dominio di accesso a cui si desidera connettersi.

- **Ruolo** (solo Pulse Secure): specificare il nome del ruolo utente che ha accesso a questa connessione. Un ruolo utente consente di definire le opzioni e le impostazioni personali, oltre ad abilitare o disabilitare alcune funzionalità di accesso.

- **Area di autenticazione** (solo Pulse Secure): specificare il nome dell'area di autenticazione da usare. Un'area di autenticazione è un raggruppamento di risorse di autenticazione usate dal tipo di connessione Pulse Secure.


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


## <a name="proxy-settings"></a>Impostazioni proxy

- **Rileva automaticamente impostazioni proxy**: se il server VPN richiede un server proxy per la connessione, specificare se si desidera che i dispositivi rilevino automaticamente le impostazioni di connessione. Per altre informazioni, vedere la documentazione di Windows Server.
- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL del server proxy** (ad esempio **http://proxy.contoso.com**) che contiene il file di configurazione.
- **Usa server proxy**: abilitare questa opzione se si desidera immettere manualmente le impostazioni del server proxy.
    - **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
    - **Numero di porta**: immettere il numero di porta associato al server proxy.
- **Ignora proxy per indirizzi locali**: se il server VPN richiede un server proxy per la connessione, selezionare questa opzione se non si vuole usare il server proxy per gli indirizzi locali specificati. Per altre informazioni, vedere la documentazione di Windows Server.

