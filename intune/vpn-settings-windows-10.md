---
title: Impostazioni VPN di Intune per dispositivi Windows 10
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni di Intune che è possibile usare per configurare le connessioni VPN nei dispositivi Windows 10."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 495e4ed6-b2ef-47cc-a110-13fa9b5f85a6
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6dd98b176c76e19d6ff261a4dafbabfb9698f787
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>Impostazioni VPN per i dispositivi Windows 10 in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

A seconda delle impostazioni selezionate, non tutti i valori nell'elenco seguente sono configurabili.


## <a name="base-vpn-settings"></a>Impostazioni VPN di base


- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui sfogliano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Server**: aggiungere uno o più server VPN a cui si connetteranno i dispositivi.
    - **Aggiungi**: apre il pannello **Aggiungi riga** in cui è possibile specificare le informazioni seguenti:
        - **Descrizione**: specificare un nome descrittivo per il server come **server VPN di Contoso**.
        - **Indirizzo IP o FQDN**: specificare l'indirizzo IP o il nome di dominio completo del server VPN a cui si connetteranno i dispositivi. Esempi: **192.168.1.1**, **vpn.contoso.com**.
        - **Server predefinito**: abilita questo server come server predefinito che i dispositivi useranno per stabilire la connessione. Assicurarsi di impostare un solo server come predefinito.
    - **Importa**: selezionare un file contenente un elenco delimitato da virgole di server nel formato descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i dati nell'elenco **Server**.
    - **Esporta**: esporta l'elenco dei server in un file di valori separati da virgole (CSV).

**Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:
- **Pulse Secure**
- **F5 Edge Client**
- **Dell SonicWALL Mobile Connect**
- **Check Point Capsule VPN**
- **Automatico**
- **IKEv2**
- **L2TP**
- **PPTP**

**Gruppo o dominio di accesso** (solo Dell SonicWALL Mobile Connect): specificare il nome del gruppo o dominio di accesso a cui si desidera connettersi.

**XML personalizzato**/**EAP XML**: specificare i comandi XML personalizzati per la configurazione della connessione VPN.

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

**Split tunneling** - **abilitare** o **disabilitare** questa opzione che consente ai dispositivi di stabilire la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.
- **Route di split tunneling per questa connessione VPN**: aggiungere route facoltative per i provider VPN di terze parti. Specificare un prefisso di destinazione e la dimensione del prefisso per ognuno.

## <a name="apps-and-traffic-rules"></a>App e regole del traffico

**Limita la connessione VPN a queste app**: abilitare questa opzione se si desiderano solo le app specificate per usare la connessione VPN.
**App associate**: fornire un elenco di app che useranno automaticamente la connessione VPN. Il tipo di app determinerà l'identificatore dell'app. Per un'app universale, specificare il nome della famiglia di pacchetti. Per un'app desktop, specificare il percorso file dell'app.

>[!IMPORTANT]
>È consigliabile proteggere tutti gli elenchi delle app compilate da usare per la configurazione della VPN per app. Se un utente non autorizzato modifica l'elenco e l'elenco viene importato nell'elenco della VPN per app, si autorizzano potenzialmente le app che non dovrebbero essere autorizzate ad accedere alla VPN. Un modo per proteggere gli elenchi delle app consiste nell'usare un elenco di controllo di accesso (ACL).

**Regole del traffico di rete per questa connessione VPN**: selezionare i protocolli, le porte e gli intervalli di indirizzi locali e remoti che verranno abilitati per la connessione VPN. Se non si crea una regola del traffico di rete, verranno abilitati tutti i protocolli, le porte e gli intervalli di indirizzi. Dopo la creazione di una regola, la connessione VPN userà soltanto i protocolli, le porte e gli intervalli di indirizzi specificati in tale regola.


## <a name="conditional-access"></a>Accesso condizionale

**Accesso condizionale per questa connessione VPN** -
**Single Sign-On (SSO) con certificato alternativo** -
**Utilizzo chiavi avanzato** -
**Hash dell'emittente** -

## <a name="dns-settings"></a>Impostazioni DNS

**Nomi e server DNS per questa connessione VPN**: selezionare i server DNS che verranno usati dalla connessione VPN una volta stabilita la connessione.
Per ogni server. specificare:
- **Nome DNS**
- **Server DNS**
- **Proxy**

## <a name="proxy-settings"></a>Impostazioni proxy

- **Rileva automaticamente impostazioni proxy**: se il server VPN richiede un server proxy per la connessione, specificare se si desidera che i dispositivi rilevino automaticamente le impostazioni di connessione. Per altre informazioni, vedere la documentazione di Windows Server.
- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL del server proxy** (ad esempio **http://proxy.contoso.com**) che contiene il file di configurazione.
- **Usa server proxy**: abilitare questa opzione se si desidera immettere manualmente le impostazioni del server proxy.
    - **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP).
    - **Numero di porta**: immettere il numero di porta associato al server proxy.
- **Ignora proxy per indirizzi locali**: se il server VPN richiede un server proxy per la connessione, selezionare questa opzione se non si vuole usare il server proxy per gli indirizzi locali specificati. Per altre informazioni, vedere la documentazione di Windows Server.

