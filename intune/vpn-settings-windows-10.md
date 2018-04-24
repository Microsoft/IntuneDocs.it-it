---
title: Visualizzare le impostazioni VPN in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni sulle impostazioni VPN disponibili in Microsoft Intune, sulla loro funzione e sulle operazioni eseguite, incluse le regole di traffico, l'accesso condizionale e le impostazioni DNS e proxy per i dispositivi Windows 10 e i dispositivi Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/8/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 9464b73acc43b9625560156617359c374d7100fb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="read-about-the-vpn-settings-in-intune"></a>Informazioni sulle impostazioni VPN in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile configurare le connessioni VPN usando Intune. Questo articolo descrive queste impostazioni, le regole di traffico, l'accesso condizionale e le impostazioni DNS e proxy.

Queste impostazioni si applicano a:

- Dispositivi che eseguono Windows 10
- Dispositivi che eseguono Windows Holographic for Business

A seconda delle impostazioni selezionate, è possibile che non tutti i valori siano configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Server**: aggiungere uno o più server VPN a cui si connettono i dispositivi.
  - **Aggiungi**: apre **Aggiungi riga** in cui vengono immesse le informazioni seguenti:
    - **Descrizione**: immettere un nome descrittivo per il server, ad esempio **Server VPN Contoso**
    - **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo del server VPN a cui si connettono i dispositivi, ad esempio **192.168.1.1** o **vpn.contoso.com**
    - **Server predefinito**: abilita il server come server predefinito usato dai dispositivi per stabilire la connessione. Impostare un solo server come server predefinito.
  - **Importa**: selezionare un file contenente un elenco di server separati da virgole nel formato: descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i server nell'elenco **Server**.
  - **Esporta**: esporta l'elenco dei server in un file di valori separati da virgole (CSV).

**Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:

- **Automatico**
- **Check Point Capsule VPN**
- **VPN Citrix**
- **SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**

**Gruppo o dominio di accesso** (solo SonicWALL Mobile Connect): questa proprietà non può essere impostata nel profilo VPN. Mobile Connect analizza questo valore quando nome utente e dominio vengono immessi nel formato `username@domain` o `DOMAIN\username`.

**XML personalizzato**/**EAP XML**: immettere i comandi XML personalizzati per la configurazione della connessione VPN.

**Esempio per Pulse Secure:**

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Esempio per CheckPoint Mobile VPN:**

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Esempio per SonicWALL Mobile Connect:**

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Esempio per F5 Edge Client:**

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Per altre informazioni su come scrivere comandi XML personalizzati, vedere la documentazione della VPN fornita dai diversi produttori.

Per altre informazioni sulla creazione di XML EAP personalizzato, vedere [EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration) (Configurazione EAP).

**Split tunneling**: scegliere **Abilita** o **Disabilita** per consentire ai dispositivi di scegliere la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.
- **Route di split tunneling per questa connessione VPN**: aggiungere route facoltative per i provider VPN di terze parti. Immettere un prefisso di destinazione e una dimensione per ogni prefisso.

## <a name="apps-and-traffic-rules"></a>App e regole del traffico

**Limita la connessione VPN a queste app**: abilitare questa opzione se si vuole che la connessione VPN venga usata solo da alcune app.
**App associate**: immettere un elenco delle app che usano automaticamente la connessione VPN. Il tipo di app determina l'identificatore dell'app. Per un'app universale, immettere il nome della famiglia di pacchetti. Per un'app desktop, immettere il percorso del file dell'app.

>[!IMPORTANT]
>È consigliabile proteggere tutti gli elenchi di app creati per le reti VPN per singole app. Se un utente non autorizzato modifica l'elenco e l'elenco viene importato nell'elenco delle app della VPN per singole app, si autorizzano potenzialmente le app che non dovrebbero essere autorizzate ad accedere alla VPN. Un modo per proteggere gli elenchi delle app consiste nell'usare un elenco di controllo di accesso (ACL).

**Regole del traffico di rete per questa connessione VPN**: selezionare i protocolli, le porte e gli intervalli di indirizzi locali e remoti che vengono abilitati per la connessione VPN. Se non si crea una regola di traffico di rete, vengono abilitati tutti i protocolli, le porte e gli intervalli di indirizzi. Dopo la creazione di una regola, la connessione VPN usa soltanto i protocolli, le porte e gli intervalli di indirizzi immessi nella regola.

## <a name="conditional-access"></a>Accesso condizionale

**Accesso condizionale per questa connessione VPN**: abilita il flusso di conformità del dispositivo dal client. Se questa impostazione è abilitata, il client VPN proverà a comunicare con Azure Active Directory per ottenere un certificato da usare per l'autenticazione. La rete VPN deve essere impostata per usare l'autenticazione basata su certificato e il server VPN deve considerare attendibile il server restituito da Azure Active Directory.

**Accesso Single Sign-On (SSO) con il certificato alternativo**: per la conformità del dispositivo, usare un certificato diverso dal certificato di autenticazione VPN per l'autenticazione Kerberos. Immettere il certificato con le impostazioni seguenti:

- **Utilizzo chiavi avanzato**: nome per l'utilizzo chiavi avanzato.
- **Identificatore di oggetto**: identificatore di oggetto per l'utilizzo chiavi avanzato.
- **Hash dell'emittente**: identificazione personale per il certificato SSO.

## <a name="dns-settings"></a>Impostazioni DNS

**Nomi e server DNS per questa connessione VPN**: selezionare i server DNS che vengono usati dalla connessione VPN una volta stabilita la connessione.
Per ogni server, immettere:
- **Nome DNS**
- **Server DNS**
- **Proxy**

## <a name="proxy-settings"></a>Impostazioni proxy

- **Rileva automaticamente impostazioni proxy**: se il server VPN richiede un server proxy per la connessione, scegliere se si vuole che i dispositivi rilevino automaticamente le impostazioni di connessione.
- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL server proxy**, ad esempio `http://proxy.contoso.com`, che contiene il file di configurazione.
- **Usa server proxy**: abilitare questa opzione per immettere manualmente le impostazioni del server proxy.
  - **Indirizzo**: immettere l'indirizzo del server proxy (ad esempio un indirizzo IP)
  - **Numero di porta**: immettere il numero di porta associato al server proxy
- **Ignora proxy per indirizzi locali**: se il server VPN richiede un server proxy per la connessione, selezionare questa impostazione se non si vuole usare il server proxy per gli indirizzi locali immessi.
