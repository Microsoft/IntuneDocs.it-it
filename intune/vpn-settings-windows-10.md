---
title: Configurare le impostazioni VPN di Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Informazioni sulle impostazioni VPN disponibili in Microsoft Intune, sulla loro funzione e sulle operazioni eseguite, incluse le regole di traffico, l'accesso condizionale e le impostazioni DNS e proxy per i dispositivi Windows 10 e i dispositivi Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: d41ec494672340a9f5751e6fc40edf1a7b06bb40
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="windows-10-vpn-settings-in-intune"></a>Impostazioni VPN di Windows 10 in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile configurare le connessioni VPN usando Intune. Questo articolo descrive queste impostazioni, le regole di traffico, l'accesso condizionale e le impostazioni DNS e proxy.

Queste impostazioni si applicano a:

- Dispositivi che eseguono Windows 10
- Dispositivi che eseguono Windows Holographic for Business

A seconda delle impostazioni selezionate, è possibile che non tutti i valori siano configurabili.

## <a name="base-vpn-settings"></a>Impostazioni VPN di base

- **Nome della connessione**: immettere un nome per la connessione. Questo nome viene visualizzato dagli utenti finali nel momento in cui esplorano l'elenco delle connessioni VPN disponibili nel dispositivo.
- **Server**: aggiungere uno o più server VPN a cui si connettono i dispositivi. Quando si aggiunge un server, si immettono le informazioni seguenti:
  - **Descrizione**: immettere un nome descrittivo per il server, ad esempio **Server VPN Contoso**
  - **Indirizzo IP o FQDN**: immettere l'indirizzo IP o il nome di dominio completo del server VPN a cui si connettono i dispositivi, ad esempio **192.168.1.1** o **vpn.contoso.com**
  - **Server predefinito**: abilita il server come server predefinito usato dai dispositivi per stabilire la connessione. Impostare un solo server come server predefinito.
  - **Importa**: selezionare un file contenente un elenco di server separati da virgole nel formato: descrizione, indirizzo IP o FQDN, server predefinito. Scegliere **OK** per importare i server nell'elenco **Server**.
  - **Esporta**: esporta l'elenco dei server in un file di valori separati da virgole (CSV).

- **Tipo di connessione**: selezionare il tipo di connessione VPN dall'elenco di fornitori seguente:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Automatico**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Quando si sceglie un tipo di connessione VPN, potrebbe essere richieste anche le impostazioni seguenti:  
    - **Always On**: abilitare automaticamente la connessione VPN quando si verificano le condizioni seguenti: 
      - Gli utenti accedono ai propri dispositivi
      - La rete del dispositivo cambia
      - Lo schermo del dispositivo si riattiva dopo essere stato disattivato 

    - **Metodo di autenticazione**: selezionare come si vuole eseguire l'autenticazione degli utenti nel server VPN. L'uso dei **certificati** offre funzionalità avanzate, ad esempio un'esperienza completamente automatica, VPN su richiesta e VPN per singole app.
    - **Ricorda le credenziali a ogni accesso**: scegliere di memorizzare nella cache le credenziali di autenticazione.
    - **XML personalizzato**: immettere i comandi XML personalizzati per la configurazione della connessione VPN.
    - **XML EAP**: immettere i comandi XML EAP per la configurazione della connessione VPN

#### <a name="pulse-secure-example"></a>Esempio di Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>Esempio di F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>Esempio di SonicWALL Mobile Connect
**Gruppo o dominio di accesso**: questa proprietà non può essere impostata nel profilo VPN. Mobile Connect analizza questo valore quando nome utente e dominio vengono immessi nel formato `username@domain` o `DOMAIN\username`.

Esempio:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>Esempio di VPN CheckPoint Mobile

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>Scrittura di XML personalizzato
Per altre informazioni su come scrivere comandi XML personalizzati, vedere la documentazione della VPN fornita dai diversi produttori.

Per altre informazioni sulla creazione di XML EAP personalizzato, vedere [EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration) (Configurazione EAP).

## <a name="apps-and-traffic-rules"></a>App e regole del traffico

- **Associa WIP o app a questa VPN**: abilitare questa opzione se si vuole che la connessione VPN venga usata solo da alcune app. Le opzioni disponibili sono:

  - **Associa WIP a questa connessione**: immettere un **dominio WIP per questa connessione**
  - **Associa le app a questa connessione**: è possibile **limitare la connessione VPN a queste app** e quindi aggiungere le **app associate**. Le app immesse usano automaticamente la connessione VPN. Il tipo di app determina l'identificatore dell'app. Per un'app universale, immettere il nome della famiglia di pacchetti. Per un'app desktop, immettere il percorso del file dell'app.
  >[!IMPORTANT]
  >È consigliabile proteggere tutti gli elenchi di app creati per le reti VPN per singole app. Se un utente non autorizzato modifica l'elenco e l'elenco viene importato nell'elenco delle app della VPN per singole app, si autorizzano potenzialmente le app che non dovrebbero essere autorizzate ad accedere alla VPN. Un modo per proteggere gli elenchi delle app consiste nell'usare un elenco di controllo di accesso (ACL).

- **Regole del traffico di rete per questa connessione VPN**: selezionare i protocolli, le porte e gli intervalli di indirizzi locali e remoti che vengono abilitati per la connessione VPN. Se non si crea una regola di traffico di rete, vengono abilitati tutti i protocolli, le porte e gli intervalli di indirizzi. Dopo la creazione di una regola, la connessione VPN usa soltanto i protocolli, le porte e gli intervalli di indirizzi immessi nella regola.

## <a name="conditional-access"></a>Accesso condizionale

- **Accesso condizionale per questa connessione VPN**: abilita il flusso di conformità del dispositivo dal client. Se questa impostazione è abilitata, il client VPN proverà a comunicare con Azure Active Directory (AD) per ottenere un certificato da usare per l'autenticazione. La rete VPN deve essere impostata per usare l'autenticazione basata su certificato e il server VPN deve considerare attendibile il server restituito da Azure AD.

- **Accesso Single Sign-On (SSO) con il certificato alternativo**: per la conformità del dispositivo, usare un certificato diverso dal certificato di autenticazione VPN per l'autenticazione Kerberos. Immettere il certificato con le impostazioni seguenti:

  - **Nome**: nome per l'utilizzo chiave avanzato
  - **Identificatore di oggetto**: identificatore di oggetto per l'utilizzo chiavi avanzato.
  - **Hash dell'emittente**: identificazione personale per il certificato SSO.

## <a name="dns-settings"></a>Impostazioni DNS

**Domini e server per questa connessione VPN**: aggiungere il dominio e il server DNS da usare per la VPN. È possibile scegliere i server DNS usati dalla connessione VPN dopo che è stata stabilita la connessione. Per ogni server, immettere:
- **Dominio**
- **Server DNS**
- **Proxy**

## <a name="proxy-settings"></a>Impostazioni proxy

- **Script di configurazione automatica**: consente di usare un file per la configurazione del server proxy. Immettere l'**URL server proxy**, ad esempio `http://proxy.contoso.com`, che contiene il file di configurazione.
- **Indirizzo**: immettere l'indirizzo del server proxy, ad esempio un indirizzo IP o `vpn.contoso.com`
- **Numero porta**: immettere il numero della porta TCP usato dal server proxy
- **Ignora proxy per indirizzi locali**: se non si vuole usare un server proxy per gli indirizzi locali, scegliere Abilita. Questa impostazione si applica se il server VPN richiede un server proxy per la connessione.

## <a name="split-tunneling"></a>Split tunneling

- **Split tunneling**: scegliere **Abilita** o **Disabilita** per consentire ai dispositivi di scegliere la connessione da usare in base al traffico. Ad esempio, un utente in un hotel userà la connessione VPN per accedere ai file di lavoro, ma userà la rete standard dell'hotel per la normale esplorazione sul Web.
- **Route di split tunneling per questa connessione VPN**: aggiungere route facoltative per i provider VPN di terze parti. Immettere un prefisso di destinazione e una dimensione per ogni connessione.
