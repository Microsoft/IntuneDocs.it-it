---
title: Configurare le impostazioni VPN per i dispositivi Windows 8.1 in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di configurazione VPN usando le impostazioni di configurazione della rete privata virtuale (VPN), inclusi i dettagli della connessione e le impostazioni proxy per includere l'indirizzo IP o FQDN e la porta TCP in Microsoft Intune nei dispositivi che eseguono Windows 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f9a1399d5474d79ac8fd48a8aa3a844f20eb640
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207044"
---
# <a name="add-vpn-settings-on-windows-81-devices-in-microsoft-intune"></a>Aggiungere impostazioni VPN per i dispositivi Windows 8.1 in Microsoft Intune



Questo articolo illustra le impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono Windows 8.1.

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

- **Applica tutte le impostazioni solo a Windows 8.1**: configurare questa impostazione nel portale classico di Intune. Nel centro di amministrazione di Microsoft Endpoint Manager questa impostazione non può essere modificata. Con l'impostazione **Configurato**, tutte le impostazioni vengono applicate solo ai dispositivi Phone 8.1. Con l'impostazione **Non configurato**, queste impostazioni vengono applicate anche ai dispositivi Windows 10.
- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Server**: aggiungere uno o più server VPN a cui si connettono i dispositivi.
  - **Aggiungi**: apre la pagina **Aggiungi riga** in cui è possibile specificare le informazioni seguenti:
    - **Descrizione**: specificare un nome descrittivo per il server come **Server VPN Contoso**.
    - **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connettono i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
    - **Server predefinito**: abilita il server come server predefinito usato dai dispositivi per stabilire la connessione. Assicurarsi di impostare un solo server come predefinito.
  - **Importa**: selezionare un file con valori delimitati da virgole con l'elenco di server nel formato: descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i server nell'elenco **Server**.
  - **Esporta**: esporta l'elenco dei server in un file con valori delimitati da virgole (CSV).

- **Tipo di connessione**: Selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only): Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Gruppo o dominio di accesso** (solo SonicWall Mobile Connect): Specificare il nome del gruppo di accesso o di dominio a cui connettersi.

- **Ruolo** (solo Pulse Secure): Specificare il nome del ruolo utente che ha accesso a questa connessione. Un ruolo utente consente di definire le opzioni e le impostazioni personali, oltre ad abilitare o disabilitare alcune funzionalità di accesso.

- **Area di autenticazione** (solo Pulse Secure): Specificare il nome dell'area di autenticazione da usare. Un'area di autenticazione è un raggruppamento di risorse di autenticazione usate dal tipo di connessione Pulse Secure.

- **XML personalizzato**: specificare i comandi XML personalizzati per la configurazione della connessione VPN.

  **Esempio di Pulse Secure**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **Esempio di VPN CheckPoint Mobile**:

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **Esempio di SonicWall Mobile Connect**:

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **Esempio di F5 Edge Client**:

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  Per altre informazioni su come scrivere comandi XML personalizzati, vedere la documentazione della VPN del produttore.

## <a name="proxy-settings"></a>Impostazioni proxy

- **Rileva automaticamente impostazioni proxy**: Se il server VPN richiede un server proxy per la connessione, specificare se si desidera che i dispositivi rilevino automaticamente le impostazioni di connessione.
- **Script di configurazione automatica**: consente di usare un file per configurare il server proxy. Immettere l'**URL server proxy** che contiene il file di configurazione. Immettere ad esempio `http://proxy.contoso.com`.
- **Usa server proxy**: abilitare questa opzione se si vogliono immettere manualmente le impostazioni del server proxy.
  - **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
  - **Numero porta**: immettere il numero di porta associato al server proxy.
- **Ignora proxy per indirizzi locali**: selezionare questa opzione se il server VPN richiede un server proxy per la connessione e non si vuole usare il server proxy per gli indirizzi locali immessi.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Configurare le impostazioni VPN nei dispositivi [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)e [Windows 10](vpn-settings-windows-10.md) .
