---
title: Configurare le impostazioni VPN per i dispositivi Windows Phone 8.1 in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di configurazione VPN usando le impostazioni di configurazione della rete privata virtuale (VPN), inclusi i dettagli della connessione e le impostazioni proxy per includere l'indirizzo IP o FQDN e la porta TCP in Microsoft Intune nei dispositivi che eseguono Windows Phone 8,1.
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
ms.openlocfilehash: 70f33fe132eb6c3dbf91c5dc313369d75f4f3e24
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207027"
---
# <a name="add-vpn-settings-on-windows-phone-81-devices-in-microsoft-intune"></a>Aggiungere impostazioni VPN per i dispositivi Windows Phone 8.1 in Microsoft Intune



Questo articolo illustra le impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi che eseguono Windows Phone 8.1. 

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.

>[!IMPORTANT]
>I profili VPN Windows Phone 8,1 vengono applicati anche ai dispositivi Windows 10.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

- **Applica tutte le impostazioni solo a Windows Phone 8,1**: configurare questa impostazione nel portale classico di Intune. Nel centro di amministrazione di Microsoft Endpoint Manager questa impostazione non può essere modificata. Con l'impostazione **Configurato**, tutte le impostazioni vengono applicate solo ai dispositivi Windows Phone 8.1. Con l'impostazione **Non configurato**, queste impostazioni vengono applicate anche ai dispositivi Windows 10 Mobile.
- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Metodo di autenticazione**: scegliere uno dei metodi seguenti di autenticazione dei dispositivi al server VPN:
  - **Certificati**: in **Certificato di autenticazione** scegliere un profilo di certificato SCEP o PKCS creato in precedenza per autenticare la connessione. Per altre informazioni sui profili di certificato, vedere [Come configurare i certificati](../protect/certificates-configure.md).
  - **Nome utente e password**: gli utenti finali devono specificare un nome utente e una password per accedere al server VPN.
- **Server**: aggiungere uno o più server VPN a cui si connettono i dispositivi.
  - **Aggiungi**: apre il pannello **Aggiungi riga** in cui è possibile specificare le informazioni seguenti:
    - **Descrizione**: specificare un nome descrittivo per il server come **Server VPN Contoso**.
    - **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connettono i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
    - **Server predefinito**: abilita il server come server predefinito usato dai dispositivi per stabilire la connessione. Assicurarsi di impostare un solo server come predefinito.
  - **Importa**: selezionare un file con valori delimitati da virgole con un elenco di server nel formato: descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i server nell'elenco **Server**.
  - **Esporta**: esporta l'elenco dei server in un file con valori delimitati da virgole (CSV).

- **Ignora la VPN nella rete Wi-Fi aziendale**: abilitare questa opzione per specificare che le connessioni VPN non vengono usate quando il dispositivo è connesso alla rete Wi-Fi aziendale.
- **Ignora la VPN nella rete Wi-Fi domestica**: abilita questa opzione per specificare che la connessione VPN non viene usata quando il dispositivo è connesso a una rete Wi-Fi domestica.

- **Tipo di connessione**: Selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **Gruppo o dominio di accesso** (solo SonicWall Mobile Connect): Specificare il nome del gruppo di accesso o di dominio a cui connettersi.
- **Ruolo** (solo Pulse Secure): Specificare il nome del ruolo utente che ha accesso a questa connessione. Un ruolo utente consente di definire le opzioni e le impostazioni personali, oltre ad abilitare o disabilitare alcune funzionalità di accesso.
- **Area di autenticazione** (solo Pulse Secure): Specificare il nome dell'area di autenticazione da usare. Un'area di autenticazione è un raggruppamento di risorse di autenticazione usate dal tipo di connessione Pulse Secure.

- **Elenco di ricerca dei suffissi DNS**: selezionare **Aggiungi** per aggiungere uno o più suffissi DNS. Ogni suffisso DNS specificato viene cercato al momento della connessione a un sito Web mediante un nome breve. Ad esempio, specificare i suffissi DNS **domain1.contoso.com** e **domain2.contoso.com**, visitare l'URL `http://mywebsite` per eseguire la ricerca degli URL `http://mywebsite.domain1.contoso.com` e `http://mywebsite.domain2.contoso.com`.

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

- **Split tunneling**: **Abilitare** o **disabilitare** questa opzione che consente ai dispositivi di stabilire la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.

## <a name="proxy-settings"></a>Impostazioni proxy

- **Rileva automaticamente impostazioni proxy**: Se il server VPN richiede un server proxy per la connessione, specificare se si desidera che i dispositivi rilevino automaticamente le impostazioni di connessione.
- **Script di configurazione automatica**: consente di usare un file per configurare il server proxy. Immettere l'**URL server proxy**, ad esempio `http://proxy.contoso.com`, contenente il file di configurazione.
- **Usa server proxy**: abilitare questa opzione se si vogliono immettere manualmente le impostazioni del server proxy.
  - **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
  - **Numero porta**: immettere il numero di porta associato al server proxy.
- **Ignora proxy per indirizzi locali**: selezionare questa opzione se il server VPN richiede un server proxy per la connessione e non si vuole usare il server proxy per gli indirizzi locali immessi.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Configurare le impostazioni VPN nei dispositivi [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)e [Windows 10](vpn-settings-windows-10.md) .
